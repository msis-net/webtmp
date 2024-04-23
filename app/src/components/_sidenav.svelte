<script>
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
    <a href="/"><i class="fas fa-qrcode"></i>Dashbord</a>
  </li>
  <li>
    <a href="/"><i class="fas fa-link"></i>コミュニティ</a>
  </li>
  <li>
    <a href="/"><i class="fas fa-coffee"></i>コーヒ一</a>
  </li>
  <li>
    <a href="/"><i class="fas fa-calendar-week"></i>イベント</a>
  </li>
  <li>
    <a href="/"><i class="fas fa-sliders-h"></i>サービス</a>
  </li>
  <li>
    <a href="/"><i class="far fa-question-circle"></i>詳細情報</a>
  </li>
  <li>
    <a href="/"><i class="fas fa-envelope"></i>お問い合わせ</a>
  </li>
</ul>

<style>
  ul li {
    display: block;
    height: 100%;
    line-height: 30px;
    border-top: 1px solid #999;
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
  ul li i {
    margin-right: 5px;
  }
</style>
