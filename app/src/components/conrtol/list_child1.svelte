<script>
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language, CodeSystem, Tabname, OpenTab } from "@/lib/stores.js";
  import { slide } from "svelte/transition";
  import { quintOut } from "svelte/easing";
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
    console.log("arrowDown", arrowDown);
  };
</script>

<button on:click={toggleArrow}>
  <div class="wrap">
    <!--span class="material-symbols-outlined"> unfold_more </span-->
    <span class="material-symbols-outlined"> fiber_smart_record </span>

    {label}
    <span class="material-symbols-outlined arrow" class:arrowDown
      >navigate_before</span
    >
  </div>
</button>

{#if arrowDown}
  <ul
    class="text-gray-000"
    transition:slide={{
      delay: 250,
      duration: 300,
      easing: quintOut,
      axis: "y", //方向
    }}
  >
    <li>
      <a href="/">
        <span class="material-symbols-outlined"> fiber_manual_record </span>
        label
      </a>
    </li>
    <li>
      <a href="/">
        <span class="material-symbols-outlined"> fiber_manual_record </span>
        label
      </a>
    </li>
    <li>
      <a href="/">
        <span class="material-symbols-outlined"> fiber_manual_record </span>
        label
      </a>
    </li>
  </ul>
{/if}

<style>
  .arrow {
    margin-left: 4px;
    transition: 0.2s;
  }

  .arrowDown {
    transform: rotate(-90deg);
  }

  button {
    display: flex;
    align-items: center;
    line-height: 30px;
    width: 100%;
    border-bottom: 1px solid #999;
  }

  button div {
    margin-left: 24px;
    font-size: 0.8em;
  }

  ul li {
    display: flex;
    align-items: center;
    line-height: 30px;
    border-bottom: 1px solid #999;
  }

  ul a {
    font-size: 0.8em;
    margin-left: 48px;
    display: block;
    width: 100%;
    list-style: 56px;
    transition: 0.3s;
  }

  ul li:hover a {
    padding-left: 10px;
  }
  ul li span {
    margin-right: 5px;
  }
</style>
