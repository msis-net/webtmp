<script>
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language, navcontext } from "@/lib/stores.js";
  import { slide } from "svelte/transition";
  import { quintOut } from "svelte/easing";
  loadTranslations($language, "/");
  export let label;
  export let NavContext; //ParentFunction
  export let lists;
  export let symbol; //Google icon name

  const onChange = () => {
    locale.set($language);
  };

  if (!symbol) {
    symbol = "fiber_smart_record"; // is lile burger
  }

  if (!lists) {
    lists = []; // is lile burger
  }

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
    <span class="material-symbols-outlined"> {symbol} </span>

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
    {#each lists as list}
      <li>
        <button on:click={() => NavContext({ list })}>
          <span class="material-symbols-outlined"> fiber_manual_record </span>
          {list}
        </button>
      </li>
    {/each}
    <li>
      <button on:click={() => NavContext("Child label-1")}>
        <span class="material-symbols-outlined"> fiber_manual_record </span>
        Child label-1
      </button>
    </li>
    <li>
      <button on:click={() => NavContext("Child label-2")}>
        <span class="material-symbols-outlined"> fiber_manual_record </span>
        Child label-2
      </button>
    </li>
    <li>
      <button on:click={() => NavContext("Child label-3")}>
        <span class="material-symbols-outlined"> fiber_manual_record </span>
        Child label-3
      </button>
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
    line-height: 40px;
    width: 100%;
  }

  button div {
    margin-left: 24px;
    width: 100%;
    text-align: left;
    font-size: 0.8em;
    border-top: 1px solid #999;
  }

  ul li {
    display: flex;
    align-items: center;
    line-height: 30px;
  }

  ul button {
    font-size: 0.8em;
    margin-left: 48px;
    display: block;
    width: 100%;
    text-align: left;
    list-style: 56px;
    transition: 0.3s;
    /*border-bottom: 1px solid #999;*/
  }

  ul li:hover button {
    padding-left: 10px;
  }
  ul li span {
    margin-right: 5px;
  }
</style>
