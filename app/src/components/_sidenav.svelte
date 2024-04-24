<script>
  import ListChild from "./conrtol/list_child.svelte";
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language, navcontext } from "@/lib/stores.js";

  export let title;
  loadTranslations($language, "/");

  const NavContext = (context) => {
    $navcontext = context;
  };
</script>

<div class="hidden">{title}</div>
<div class="text-xl bg-yellow-200 select-none p-5">
  {$t("common.header.title")}
</div>
<ul class="text-white bg-slate-600 overflow-y-auto">
  <li>
    <button on:click={() => NavContext("Dashbord")}>
      <span class="material-symbols-outlined"> speed </span>
      Dashbord
    </button>
  </li>

  <ListChild label="DropdownList" {NavContext} />

  <li>
    <button on:click={() => NavContext("Menu1")}>
      <span class="material-symbols-outlined"> format_indent_increase </span>
      Menu1
    </button>
  </li>
  <li>
    <button on:click={() => NavContext("Menu2")}>
      <span class="material-symbols-outlined"> unfold_more </span>
      Menu2
    </button>
  </li>
  <li>
    <button on:click={() => NavContext("Menu3")}>
      <span class="material-symbols-outlined"> list </span>
      Menu3
    </button>
  </li>
</ul>

<style>
  * {
    user-select: none;
  }
  ul li {
    display: flex;
    align-items: center;
    line-height: 40px;
    border-top: 1px solid #999;
  }
  ul button {
    margin: 4px;
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
