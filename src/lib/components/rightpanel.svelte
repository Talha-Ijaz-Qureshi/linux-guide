<script lang="ts">
  import { Select, SelectItem, Theme } from "carbon-components-svelte";
  import Icon from "@iconify/svelte";

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
      <Icon icon="carbon:settings-adjust" width="32" height="32"  style="color: #78a9ff" />
      {:else}
      <Icon icon="carbon:close-filled" width="32" height="32"  style="color: #78a9ff" />      
      {/if}
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