<script>
  import NavChild from "./conrtol/nav_child.svelte";
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language, navcontext } from "@/lib/stores.js";
  export let label;
  loadTranslations($language, "/");
  const NavContext = (context) => {
    $navcontext = context;
    console.log("navcontext", $navcontext);
  };
</script>

<!--headerの全体枠-->
<div class="relative m-2 w-lvw">
  <div class="hidden">{label}</div>
  <ul class="navbar-main">
    <li>
      <button on:click={() => NavContext("home")}>
        <span class="material-symbols-outlined"> home </span>
      </button>
    </li>
    <li>
      <button on:click={() => NavContext("logout")}>
        <span class="material-symbols-outlined"> logout </span>
      </button>
    </li>
  </ul>

  <div class="navbar-child ms-auto space-x-2">
    <NavChild label="Dropdown2" {NavContext} />
    <NavChild label="Dropdown3" {NavContext} />
  </div>
</div>

<style>
  * {
    user-select: none;
  }
  .navbar-main {
    @apply absolute left-12 flex space-x-5;
    line-height: 42px;
    color: #666;
  }
  /*.navbar-nav 
  右下寄せ、要素内：横並び、左右中央、16px間隔　
  */
  .navbar-child {
    @apply absolute flex right-8 bottom-0 align-middle justify-center space-x-4 text-gray-600;
  }

  ul li {
    cursor: pointer;
  }
</style>
