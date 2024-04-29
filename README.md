# WATe(Web App Template)

### JavaScript

私は開発案件をこなす為、役に立ちそうなフレームワークを探していました。
このテンプレートではナビゲーションを実装した基本レイアウトをベースにマニュアル等のアプリが構築できます。新たに構築したアプリをアップロードするにはブランチを作成してください。

最初 AdminLTE という素晴らしい CSS フレームワークに出会いました。この出会いは感動的なもので私が抱える全ての問題を解決できるかと思いました。
しかし結果的には問題解決には至りませんでした。
なぜなら、このプレームワークは元々は jQuery を使っていましたが、現在は jQuery を利用しないバージョンへと切替ていました。

実際 AdminLTE4 では Astro ベースで改良がおこなわれています。

そこで React や Vue を初め様々な JS フレームワークを試して、これらとどの様な融合化可能か探り始めました。
結果的にたどり着いたのが、この組み合わせになります。

- 第一階層では、Docker 展開用の関連ファイルが存在します。
- 各種フレームワークは app/以下で操作してください。
  <lo class="border-t-2">
  <ul>
  <div class="font-bold">開発環境</div>
  <li class="font-bold">アウトラインフレームワーク</li>
  <div class="ml-3 font-bold text-blue-700"><a href="https://astro.build/" class="href" target="_blank">ASTRO(アストロ)</a></div>
  <div class="ml-3">理由:HTMLの静的ジェネレータ。レイアウト構成全体の管理効率が上がる。多種のインテグレーションにも対応。</div>
  <li class="font-bold">インラインフレームワーク</li>
  <div class="ml-3 font-bold text-blue-700"><a href="https://svelte.jp/" target="_blank" class="href">SVELTE(スベルテ)</a></div>
  <div class="ml-3">理由:JavaScriptライブラリ。React/Vueが人気だがこれらと比べて新しく効率的なコーディング開発が可能。</div>
  <div class="ml-3 font-bold text-blue-700"><a href="https://tailwindcss.com/" target="_blank" class="href">TailWindCss(テイルウィンドCSS)</a></div>
  <div class="ml-3">理由:CSSフレームワーク。他フレームワークに比べて全体レイアウトの決まりは無く、個々のオブジェクトに対するデザインが簡単。</div>
  </ul>
  <div class="text-right">
  ※2024/02/29:過去の経験と現在のトレンド（今後の動向）を踏まえて厳選。

      </div>

    </lo>
