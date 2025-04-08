<script lang="ts">
	import { Content, InlineNotification, CodeSnippet, ToastNotification } from 'carbon-components-svelte';
	import content from '$lib/data/content';
	import "carbon-components-svelte/css/all.css";
	import { parseContent } from '$lib/utils/parse';
	
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
  function parseUrls(text: string): string {
    const urlRegex = /(https?:\/\/[^\s]+)/g;
    return text.replace(urlRegex, '<a href="$1" target="_blank" rel="noopener noreferrer">$1</a>');
  }

  function formatText(text: string): string {
    let formatted = parseUrls(text);
    return formatted;
  }

  </script>
  <h1 class="hide">Linux Migration<br>Compass  
  </h1>


  <Content>
  
	{#each content.sections as section}
	  <section id={section.id}>
		<h2>{section.title}</h2>
		<p>{section.intro}</p>
		{#each section.subtopics as subtopic}
		  {@const subtopicSlug: string = slugify(subtopic.title)}
		  {@const subtopicId: string = `${section.id}-${subtopicSlug}`}
		  <h3 id={subtopicId}>{subtopic.title}</h3>
		  {#each subtopic.blocks as block}
			{#if block.type === 'text'}
			  <p style="margin: 1em 0 .2em 0;">{@html formatText(block.value)}</p>
			{:else if block.type === 'code'}
			  <CodeSnippet code={block.value} />
			{:else if block.type === 'note'}
			  <InlineNotification
				kind={block.kind}
				title={block.message}
				subtitle={block.value}
				hideCloseButton
				lowContrast
			  />
			{/if}
		  {/each}
		{/each}
		<hr />
	  </section>
	{/each}
  </Content>

  <style>
	@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@300;400;600&family=IBM+Plex+Serif:wght@300;400;600&display=swap');

	:global(ol) {
		margin: .1em;
		margin-left: 2em;
		line-height: 2;
	}
	.hide {
		display: none;
	}
	h1 {
	  font-size: 1.5rem;
	  margin-left: 2rem;
	  margin-bottom: 0rem;
	  font-family: 'IBM Plex Serif', serif;
		font-weight: 600;
		color: #78a9ff;
		font-stretch: 100%;
		position: relative;
	}
	h2 {
	  font-size: 2.5rem;
	  /* color: #c6c6c6; */
	  margin: 2rem 0 1rem;
	  font-family: 'IBM Plex Serif', serif;
	  opacity: .9;
	}
	h3 {
	  font-size: 1.5rem;
	  margin: 1.5rem 0 0.5rem;
	  opacity: .9;
	}
	/* pre {
	  background-color: #2e3b44;
	  padding: 1rem;
	  border-radius: 4px;
	} */
	hr {
	  border: 0;
	  border-top: 1px solid #393939;
	  margin: 2rem 0;
	}	
	p {
		line-height: 2;
	}

	@media (max-width: 1199px) {
		h1 {
			font-size: 1.2rem;
			margin-left: 2rem;
		}
		h2 {
			font-size: 1.9rem;
		}
		h3 {
			font-size: 1.5rem;
		}
		p {
			font-size: 0.95rem;
			line-height: 1.7;
		}
		.hide {
			display: block;
		}
	}

</style>