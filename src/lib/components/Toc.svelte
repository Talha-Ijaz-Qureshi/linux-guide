<script lang="ts">
  import { onMount } from 'svelte';
  import { Accordion, AccordionItem } from 'carbon-components-svelte';
  import "carbon-components-svelte/css/all.css";
  import contentData from '$lib/data/content';
  import type { Section, Subtopic } from '$lib/data/content';

  const sections: Section[] = contentData.sections;
  let activeSection: string = '';
  let activeSubtopicId: string = '';
  let observer: IntersectionObserver | null = null;
  let isMenuOpen: boolean = false;
  let buttonAnimateClass = "";

  function slugify(text: string): string {
    if (!text) return '';
    return text
      .toLowerCase()
      .trim()
      .replace(/\s+/g, '-')
      .replace(/[^\w-]+/g, '')
      .replace(/--+/g, '-')
      .replace(/^-+/, '')
      .replace(/-+$/, '');
  }

  function handleLinkClick(event: Event, href: string) {
    event.preventDefault();
    const targetId = href.slice(1);
    const targetElement = document.getElementById(targetId);

    if (targetElement) {
      const viewportHeight = window.innerHeight;
      const offset = viewportHeight * 0.1;
      const elementTop = targetElement.getBoundingClientRect().top + window.scrollY;
      const adjustedTop = elementTop - offset;

      window.scrollTo({
        top: adjustedTop,
        behavior: 'smooth'
      });
      isMenuOpen = false; 
    }
  }

  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
    buttonAnimateClass = isMenuOpen ? "btn-animate" : "";

  }

  onMount(() => {
    const subtopicIds: string[] = [];
    sections.forEach(section => {
      section.subtopics.forEach(subtopic => {
        const subtopicSlug = slugify(subtopic.title);
        const subtopicId = `${section.id}-${subtopicSlug}`;
        subtopicIds.push(subtopicId);
      });
    });

    const handleIntersection: IntersectionObserverCallback = (entries) => {
      const intersectingEntries = entries.filter(entry => entry.isIntersecting);
      if (intersectingEntries.length === 0) return;

      let topmostEntry = intersectingEntries[0];
      for (let i = 1; i < intersectingEntries.length; i++) {
        if (intersectingEntries[i].boundingClientRect.top < topmostEntry.boundingClientRect.top) {
          topmostEntry = intersectingEntries[i];
        }
      }

      if (topmostEntry.target instanceof HTMLElement) {
        const id = topmostEntry.target.id;
        activeSubtopicId = id; 
        const sectionId = id.split('-')[0];
        activeSection = sectionId; 
      }
    };

    const observerOptions: IntersectionObserverInit = {
      rootMargin: "0px 0px -80% 0px", 
      threshold: 0.0 
    };

    observer = new IntersectionObserver(handleIntersection, observerOptions);

    subtopicIds.forEach(id => {
      const el = document.getElementById(id);
      if (el) {
        if (observer) {
          observer.observe(el);
        }
      } else {
        console.warn(`Element with ID '${id}' not found.`);
      }
    });

    return () => {
      subtopicIds.forEach(id => {
        const el = document.getElementById(id);
        if (el && observer) observer.unobserve(el);
      });
      observer?.disconnect();
    };
  });
</script>


<nav class:open={isMenuOpen} aria-label="Table of contents">

  <h1>Linux Migration Compass</h1>
  <Accordion>
    {#each sections as section (section.id)}
      <AccordionItem open={activeSection === section.id}>
        <span slot="title">{section.title}</span>
        <ul>
          {#each section.subtopics as subtopic (subtopic.title)}
            {@const subtopicSlug: string = slugify(subtopic.title)}
            {@const subtopicHref: string = `#${section.id}-${subtopicSlug}`}
            <li>
              <a href={subtopicHref} on:click={(event) => handleLinkClick(event, subtopicHref)}>
                {activeSubtopicId === `${section.id}-${subtopicSlug}` ? '> ' : ''}{subtopic.title}
              </a>
            </li>
          {/each}
        </ul>
      </AccordionItem>
    {/each}
  </Accordion>

</nav>
<button class="menu-toggle {buttonAnimateClass}" on:click={toggleMenu} aria-label="Toggle menu">
  {#if !isMenuOpen}
  <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 32 32"><path fill="#78a9ff" d="M28 4H4c-1.1 0-2 .9-2 2v20c0 1.1.9 2 2 2h24c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2M10 26H4V6h6zm18 0H12v-9h10.2l-3.6 3.6L20 22l6-6l-6-6l-1.4 1.4l3.6 3.6H12V6h16z"/></svg>    
  {:else}
  <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 32 32"><path fill="#78a9ff" d="M28 4H4c-1.1 0-2 .9-2 2v20c0 1.1.9 2 2 2h24c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2m0 11H17.8l3.6-3.6L20 10l-6 6l6 6l1.4-1.4l-3.6-3.6H28v9H12V6h16z"/></svg>
      {/if}
</button>


<style>
  @import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@300;400;600&family=IBM+Plex+Serif:wght@300;400;600&display=swap');

  h1 {
    font-size: 1.5rem;
    margin-bottom: .5em;
    margin-top: 0;
    margin-right: auto;
    margin-left: auto;
    font-family: 'IBM Plex Serif', serif;
    font-weight: 600;
    color: #78a9ff;
    font-stretch: 100%;
  }

  nav {
    padding: 1rem 0;
    border-right: 1px solid var(--cds-border-subtle, #e0e0e0);
    width: fit-content; 
    position: fixed;
    top: 0;
    left: 0;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    flex-direction: column;
    transition: transform 200ms cubic-bezier(1, 0, 0.01, 1);
    z-index: 1001;
    backdrop-filter: blur(1em);
    -webkit-backdrop-filter: blur(1em); 
    transition: transform 200ms cubic-bezier(1, 0, 0.01, 1);
    box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);


  }


  .btn-animate {
    transform: translateX(85vw);
    transition: transform 200ms cubic-bezier(1, 0, 0.01, 1);
  }

  .menu-toggle {
    display: none;
    position: fixed;
    top: 1rem;
    left: .5rem;
    font-size: 1.5rem;
    background: none;
    border: none;
    cursor: pointer;
    color: #78a9ff;
    z-index: 100;
  }
  
  @media (min-width: 1200px) {
    nav {
      transform: translateX(0);
    }
    .menu-toggle {
      display: none;
    }
  }

  @media (max-width: 1199px) {
    nav {
      transform: translateX(-100%);
      border-right: 1px solid var(--cds-border-subtle, #e0e0e0);

    }
    nav.open {
      transform: translateX(0);
    }
  }

  ul {
    list-style: none;
    padding-left: 1rem;
    margin-top: 0.5rem;
  }

  li {
    margin: 0.5rem 0;
  }

  a {
    color: var(--cds-link-primary, #0f62fe);
    text-decoration: none;
    font-size: var(--cds-body-compact-01-font-size, 0.875rem);
  }

  a:hover {
    text-decoration: underline;
    color: var(--cds-link-primary-hover, #0043ce);
  }

  @media (max-width: 1199px) {
    .menu-toggle {
      display: block; 
    }
  }
</style>