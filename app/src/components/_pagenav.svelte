<script>
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import {
    language,
    CodeSystem,
    Tabname,
    OpenTab,
    dockLeft,
  } from "@/lib/stores.js";
  export let title;
  let view = false;
  loadTranslations($language, "/");
  console.log(title);
  $: {
    view = $dockLeft;
  }
</script>

<div></div>
<div class="main transition-all">
  a
  <div class="" class:view>
    {view}sss
  </div>
</div>

<style>
  .main {
    position: relative;
    transition: 1.5s;
  }

  .view {
    display: block;
    transition: all 1.2s;
    @apply w-72;
  }
</style>
