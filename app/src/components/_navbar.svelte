<script>
  import NavChild from "./conrtol/nav_child.svelte";
  import Dropdown2 from "./conrtol/dropdown2.svelte";
  export let title;
</script>

<!--headerの全体枠-->
<div class="relative m-2 w-lvw">
  <div class="hidden">{title}</div>
  <ul class="absolute left-12 flex text-gray-600 space-x-5 top-3 mainmanu">
    <li><span class="material-symbols-outlined"> home </span></li>
    <li><span class="material-symbols-outlined"> logout </span></li>
  </ul>

  <div class="navbar-child ms-auto space-x-2">
    <NavChild label="Dropdown2" />
    <NavChild label="Dropdown3" />
  </div>
</div>

<style>
  /*.navbar-nav 
  右下寄せ、要素内：横並び、左右中央、16px間隔　
  */
  .navbar-child {
    @apply absolute flex right-8 bottom-0 align-middle justify-center space-x-4 text-gray-600;
  }
</style>
