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
<div class="title nav-height flex">
  <img src="/images/adlogo.png" class="image" alt="adlogo" />
  {$t("common.header.title")}
</div>

<ul class="overflow-y-auto">
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
  .title {
    align-items: center; /*↕*/
    justify-content: left; /*↔*/
    font-size: 1.25em;
    padding: 4px;
  }
  .image {
    width: 48px; /* image width*/
    height: 48px; /* image height */
    object-fit: contain; /*contain / cover*/
    /*border: dashed 1px gray; */ /* for check of image outline  */
  }
  ul {
    color: #333;
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
