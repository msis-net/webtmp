<script>
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language } from "@/lib/stores.js";
  import { fade } from "svelte/transition";
  loadTranslations($language, "/");
  export let label;
  export let NavContext; //ParentFunction
  const onChange = () => {
    locale.set($language);
  };

  let arrowDown = false;
  const toggleArrow = () => {
    if (arrowDown) {
      arrowDown = false;
    } else {
      arrowDown = true;
    }
  };

  //dropdown以外のクリックで閉じる
  import { onMount, onDestroy } from "svelte";

  const handleClickOutside = (event) => {
    if (!event.target.closest(".dropdown") && arrowDown) {
      arrowDown = false;
    }
  };

  onMount(() => {
    document.addEventListener("click", handleClickOutside);
  });

  onDestroy(() => {
    document.removeEventListener("click", handleClickOutside);
  });
</script>

<!--headerの全体枠-->
<div class="dropdown">
  <button class="nav-icon flex space-x-1" on:click={toggleArrow}>
    <span class="material-symbols-outlined"> account_circle </span>
    <div class="label">{label}</div>
    <span class="material-symbols-outlined arrow" class:arrowDown
      >navigate_before</span
    >
  </button>
  {#if arrowDown}
    <ul class="dropdown-item hidden" transition:fade>
      <li>
        <button on:click={() => NavContext("ABOUT")}> ABOUT </button>
      </li>
      <li>
        <button on:click={() => NavContext("SERVICE")}> SERVICE </button>
      </li>
      <li>
        <button on:click={() => NavContext("CONTACT")}> CONTACT </button>
      </li>
      <li>
        <select bind:value={$language} on:change={onChange}>
          <option value="en" selected>en</option>
          <option value="ja">ja</option>
        </select>
      </li>
    </ul>
  {/if}
</div>

<style>
  .dropdown {
    @apply relative;
    cursor: pointer;
    font-size: 0.9em;
  }

  .dropdown:hover {
    @apply shadow-md rounded-md;
  }

  .dropdown:hover > .dropdown-item {
    display: block;
  }

  .arrow {
    transition: 0.2s;
  }
  .arrowDown {
    transform: rotate(-90deg);
  }

  .dropdown-item {
    @apply absolute w-48 -left-12 bg-white border rounded-md shadow-md;
    z-index: 20;
  }

  ul li {
    display: block;
    height: 100%;
    line-height: 30px;
    border-top: 1px solid #ddd;
  }
  ul li button {
    margin: 4px;
    width: 98%;
    text-align: left;
    font-size: 0.8em;
  }
  ul li:hover {
    background-color: #eee;
  }

  select {
    margin: 4px;
    font-size: 0.8em;
  }
  @media (max-width: 768px) {
    .label {
      display: none;
    }
    .dropdown-item {
      @apply -left-48;
    }
  }
</style>
