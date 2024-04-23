<script>
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language, CodeSystem, Tabname, OpenTab } from "@/lib/stores.js";
  import { fade } from "svelte/transition";
  loadTranslations($language, "/");
  export let label;
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
  <button class="nav-icon flex space-x-2" on:click={toggleArrow}>
    <span class="material-symbols-outlined"> account_circle </span>
    <div class="hidden">{label}</div>
    <span class="material-symbols-outlined arrow hidden" class:arrowDown
      >navigate_before</span
    >
  </button>
  {#if arrowDown}
    <ul class="dropdown-item" transition:fade>
      <li><a href="/">ABOUT</a></li>
      <li><a href="/">SERVICE</a></li>
      <li><a href="/">COMPANY</a></li>
      <li><a href="/">CONTACT</a></li>
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
    @apply relative p-2;
    cursor: pointer;
  }

  .dropdown:hover {
    background-color: none;
  }
  .dropdown:hover > .dropdown-item {
    display: block;
  }

  .arrow {
    transition: 0.2s;
  }
  .arrowDown {
    transform: rotate(-90deg);
    transition: 0.2s;
  }

  .dropdown-item {
    @apply absolute w-72 bg-white border rounded-md;
  }

  ul li {
    display: block;
    height: 100%;
    line-height: 30px;
    border-top: 1px solid #ddd;
  }
  ul li a {
    margin: 4px;
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
  }
</style>
