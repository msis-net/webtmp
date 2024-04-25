<script>
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language } from "@/lib/stores.js";
  export let label;
  let view = false;
  loadTranslations($language, "/");
</script>

<div class="m-2">{label}</div>
<div class="ml-2">
  <ul>
    <li>list1</li>
    <ol class="ml-2">
      <li>1-1</li>
      <li>1-2</li>
      <li>1-3</li>
    </ol>
    <li>list2</li>
    <ol class="ml-2">
      <li>2-1</li>
      <li>2-2</li>
      <li>2-3</li>
    </ol>
    <li>list3</li>
    <ol class="ml-2">
      <li>3-1</li>
      <li>3-2</li>
      <li>3-3</li>
    </ol>
  </ul>
</div>
