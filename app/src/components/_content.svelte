<script>
  import { loadTranslations, t, locale, locales } from "@/lib/i18n/i18n";
  import { language, navcontext } from "@/lib/stores.js";

  export let label;
  let view = false;
  loadTranslations($language, "/");

  //Compornetnt items
  import Comp1 from "./comp1.svelte";
  import Comp2 from "./comp2.svelte";
  import Comp3 from "./comp3.svelte";

  const options = [
    { name: "", component: null },
    { name: "Dashbord", component: Comp1 },
    { name: "Menu1", component: Comp2 },
    { name: "Menu2", component: Comp3 },
  ];

  let selected = options[0];

  $: {
    if ($navcontext.length > 0) {
      if (options.find((v) => v.name == $navcontext)) {
        selected = options.find((v) => v.name == $navcontext);
      } else {
        selected = options[0];
      }
    } else {
      selected = options[0];
    }
  }
</script>

<div>
  ありがとうございました。ありがとうございました。ありがとうございました。ありがとうございました。ありがとうございました。ありがとうございました。
</div>
<div>{label}:location[{$navcontext}]</div>
<div class="bg-slate-50">
  {#if selected.component === null}
    <div>[{$navcontext}] is Nothing</div>
  {:else}
    <svelte:component this={selected.component} label={$navcontext} />
  {/if}
</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
<div>Text</div>
