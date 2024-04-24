<script>
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language, navcontext } from "@/lib/stores.js";
  import { slide } from "svelte/transition";
  import { quintOut } from "svelte/easing";
  import ListChild_1 from "./list_child_1.svelte";
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
</script>

<button on:click={toggleArrow}>
  <div>
    <!--span class="material-symbols-outlined"> unfold_more </span-->
    <span class="material-symbols-outlined mr-1"> segment </span>
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
      <button on:click={() => NavContext("label")}>
        <span class="material-symbols-outlined"> label </span>
        label
      </button>
    </li>
    <li>
      <button on:click={() => NavContext("label_important")}>
        <span class="material-symbols-outlined"> label_important </span>
        label_important
      </button>
    </li>
    <li>
      <button on:click={() => NavContext("adjust")}>
        <span class="material-symbols-outlined"> adjust </span>
        adjust
      </button>
    </li>
    <ListChild_1 label="Child list" {NavContext} />
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
    line-height: 40px;
    width: 100%;
    border-top: 1px solid #999;
  }

  button div {
    margin: 4px;
  }

  ul li {
    display: flex;
    align-items: center;
    line-height: 30px;
  }

  ul button {
    font-size: 0.8em;
    margin-left: 24px;
    display: block;
    width: 100%;
    text-align: left;
    list-style: 56px;
    transition: 0.3s;
  }

  ul li:hover button {
    padding-left: 10px;
  }
  ul li span {
    margin-right: 5px;
  }
</style>
