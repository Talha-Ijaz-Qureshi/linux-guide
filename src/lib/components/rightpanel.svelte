<script lang="ts">
  import { Select, SelectItem, Theme } from "carbon-components-svelte";

  let selected = "g100";

  let isPreferencesOpen: boolean = false;
  let buttonAnimateClass = "";

  function togglePreferences() {
    isPreferencesOpen = !isPreferencesOpen;
    buttonAnimateClass = isPreferencesOpen ? "btn-animate" : "";
  }
</script>

<Theme theme={selected} />



<div class="preferences-panel" class:open={isPreferencesOpen}>
  <h1 style="opacity: 0.8;">Preferences</h1>
  <Select labelText="Carbon theme" bind:selected>
    <SelectItem value="white" text="White" />
    <SelectItem value="g10" text="Gray 10" />
    <SelectItem value="g80" text="Gray 80" />
    <SelectItem value="g90" text="Gray 90" />
    <SelectItem value="g100" text="Dark" />
  </Select>
</div>
  <button class="preferences-toggle {buttonAnimateClass}" on:click={togglePreferences} aria-label="Toggle preferences">
    {#if !isPreferencesOpen}
    <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 32 32"><path fill="#78a9ff" d="M27 16.76v-1.53l1.92-1.68A2 2 0 0 0 29.3 11l-2.36-4a2 2 0 0 0-1.73-1a2 2 0 0 0-.64.1l-2.43.82a11 11 0 0 0-1.31-.75l-.51-2.52a2 2 0 0 0-2-1.61h-4.68a2 2 0 0 0-2 1.61l-.51 2.52a11.5 11.5 0 0 0-1.32.75l-2.38-.86A2 2 0 0 0 6.79 6a2 2 0 0 0-1.73 1L2.7 11a2 2 0 0 0 .41 2.51L5 15.24v1.53l-1.89 1.68A2 2 0 0 0 2.7 21l2.36 4a2 2 0 0 0 1.73 1a2 2 0 0 0 .64-.1l2.43-.82a11 11 0 0 0 1.31.75l.51 2.52a2 2 0 0 0 2 1.61h4.72a2 2 0 0 0 2-1.61l.51-2.52a11.5 11.5 0 0 0 1.32-.75l2.42.82a2 2 0 0 0 .64.1a2 2 0 0 0 1.73-1l2.28-4a2 2 0 0 0-.41-2.51ZM25.21 24l-3.43-1.16a8.9 8.9 0 0 1-2.71 1.57L18.36 28h-4.72l-.71-3.55a9.4 9.4 0 0 1-2.7-1.57L6.79 24l-2.36-4l2.72-2.4a8.9 8.9 0 0 1 0-3.13L4.43 12l2.36-4l3.43 1.16a8.9 8.9 0 0 1 2.71-1.57L13.64 4h4.72l.71 3.55a9.4 9.4 0 0 1 2.7 1.57L25.21 8l2.36 4l-2.72 2.4a8.9 8.9 0 0 1 0 3.13L27.57 20Z"/><path fill="#78a9ff" d="M16 22a6 6 0 1 1 6-6a5.94 5.94 0 0 1-6 6m0-10a3.91 3.91 0 0 0-4 4a3.91 3.91 0 0 0 4 4a3.91 3.91 0 0 0 4-4a3.91 3.91 0 0 0-4-4"/></svg>
      {:else}
      <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 32 32"><path fill="#78a9ff" d="M16 2C8.2 2 2 8.2 2 16s6.2 14 14 14s14-6.2 14-14S23.8 2 16 2m5.4 21L16 17.6L10.6 23L9 21.4l5.4-5.4L9 10.6L10.6 9l5.4 5.4L21.4 9l1.6 1.6l-5.4 5.4l5.4 5.4z"/></svg>  {/if}
  </button>
<style>


  .preferences-toggle {
    display: none; 
    position: fixed;
    top: 4rem;
    left: .5rem;
    z-index: -100;
    font-size: 1.5rem;
    background: none;
    border: none;
    cursor: pointer;
    color: #78a9ff;
    z-index: 100;
    transform: translateX(0);
    transition: transform 200ms cubic-bezier(1, 0, 0.01, 1);
  }

  .btn-animate {
    transform: translateX(85vw);
    transition: transform 200ms cubic-bezier(1, 0, 0.01, 1);
  }

  .preferences-panel {
    position: fixed;
    top: 0em;
    right: 5em;
    height: 100%;
    width: 250px;
    padding: 1rem;
    box-shadow: -2px 0 5px rgba(0, 0, 0, 0.1);
    transition: transform 200ms cubic-bezier(1, 0, 0.01, 1);
    z-index: 1000;
    backdrop-filter: blur(1em);
  -webkit-backdrop-filter: blur(1em);
  }
    .preferences-toggle {
      display: none;
    }

  @media (min-width: 768px) and (max-width: 1199px) {
    .preferences-panel {
      position: fixed;
      left: 0;
      transform: translateX(-100%); 
      border-right: 1px solid var(--cds-border-subtle, #e0e0e0);
      box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);

      width: 250px;

    }
    .preferences-panel.open {
      transform: translateX(0);
    }
    .preferences-toggle {
      display: block; 
    }

}

    @media (max-width: 767px) {
    .preferences-panel {
      transform: translateX(-100%); 
      width: 300px;
      position: fixed;
      left: 0;
      border-right: 1px solid var(--cds-border-subtle, #e0e0e0);
      
      box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
    }
    .preferences-panel.open {
      transform: translateX(0);
    }
    .preferences-toggle {
      display: block; 
    }
  }
</style>