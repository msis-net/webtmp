<script>
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language } from "@/lib/stores.js";
  export let label;
  let view = false;
  loadTranslations($language, "/");
</script>

<main class="">{label}</main>
<div>s</div>
