<script>
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language, navcontext } from "@/lib/stores.js";
  import { slide } from "svelte/transition";
  import { quintOut } from "svelte/easing";
  import ListChild from "./list_child.svelte";
  loadTranslations($language, "/");
  export let NavContext; //ParentFunction
  export let value; //Google icon name
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
    <span class="material-symbols-outlined mr-1"> {value.symbol} </span>
    {value.name}

    <span class="material-symbols-outlined arrow" class:arrowDown
      >navigate_before</span
    >
  </div>
</button>

{#if arrowDown}
  <ul
    class="ml-6"
    transition:slide={{
      delay: 250,
      duration: 300,
      easing: quintOut,
      axis: "y", //方向
    }}
  >
    {#each value.lists as list}
      {#if list.sublist}
        <ListChild value={list.sublist} {NavContext} />
      {:else}
        <li>
          {#if list.url}
            <a href={list.url} class="">
              <span class="material-symbols-outlined label">
                {list.symbol}
              </span>
              {list.label}
            </a>
          {:else}
            <button on:click={() => NavContext(list.context)}>
              <span class="material-symbols-outlined label">
                {list.symbol}
              </span>
              {list.label}
            </button>
          {/if}
        </li>
      {/if}
    {/each}
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
    margin: 0.25rem;
  }
  ul {
    position: relative;
    color: #333;
  }
  ul li {
    position: relative;
    display: flex;
    align-items: center;
    line-height: 30px;
  }

  ul button {
    font-size: 0.8em;
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
