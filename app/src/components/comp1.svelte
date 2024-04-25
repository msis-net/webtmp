<script>
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language, navcontext } from "@/lib/stores.js";
  export let label;
  let view = false;
  loadTranslations($language, "/");
</script>

<main class="">{label}</main>

<div
  class="grid grid-cols-4 max-lg:grid-cols-2 max-sm:grid-cols-1 gap-x-2 gap-y-1"
>
  <div>01</div>
  <div>02</div>
  <div>03</div>
  <div>04</div>
  <div>05</div>
  <div>06</div>
  <div>07</div>
  <div>08</div>
  <div>09</div>
  <div>10</div>
  <div>11</div>
  <div>12</div>
</div>

<style>
  div.grid div {
    background-color: green;
    opacity: 0.2;
    height: 102px;
  }
</style>
