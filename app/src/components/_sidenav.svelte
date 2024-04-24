<script>
  import ListChild from "./conrtol/list_child.svelte";
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language, CodeSystem, Tabname, OpenTab } from "@/lib/stores.js";

  export let title;
  loadTranslations($language, "/");
  console.log(title);
</script>

<div class="text-xl bg-yellow-200 select-none p-5">
  {$t("common.header.title")}
</div>
<ul class="text-white bg-slate-600">
  <li>
    <a href="/">
      <span class="material-symbols-outlined"> speed </span>
      Dashbord
    </a>
  </li>

  <ListChild label="Dropdown2" />

  <li>
    <a href="/">
      <span class="material-symbols-outlined"> format_indent_increase </span>
      Menu1
      <span class="material-symbols-outlined arrow">navigate_before</span>
    </a>
  </li>
  <li>
    <a href="/">
      <span class="material-symbols-outlined"> unfold_more </span>
      Menu2
      <span class="material-symbols-outlined arrow">navigate_before</span>
    </a>
  </li>
  <li>
    <a href="/">
      <span class="material-symbols-outlined"> list </span>
      Menu3
      <span class="material-symbols-outlined arrow">navigate_before</span>
    </a>
  </li>
  <li>
    <a href="/">
      <span class="material-symbols-outlined"> segment </span>
      Menu4
      <span class="material-symbols-outlined arrow">navigate_before</span>
    </a>
  </li>
  <li>
    <a href="/">
      <span class="material-symbols-outlined"> line_weight </span>
      Menu5
      <span class="material-symbols-outlined arrow">navigate_before</span>
    </a>
  </li>
</ul>

<style>
  ul li {
    display: flex;
    align-items: center;
    line-height: 40px;
    border-bottom: 1px solid #999;
    transition: 1.3s;
  }
  ul a {
    margin: 4px;
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
