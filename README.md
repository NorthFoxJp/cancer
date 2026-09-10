# 原発不明がん・中咽頭がん 闘病記 — 北きつねの治療記録

Blogspotで公開していた患者本人の闘病記を、治療段階や症状から読めるよう再構成したJekyllサイトです。

公開予定URL：<https://northfoxjp.github.io/cancer/>

## 重要

このリポジトリは公開前確認中です。公開前に次の資料を確認してください。

- [`review/要確認事項.md`](review/要確認事項.md)
- [`review/原文から変更した箇所.md`](review/原文から変更した箇所.md)
- [`review/移行しなかった画像・外部資料.md`](review/移行しなかった画像・外部資料.md)

移行前の原文は[`source/`](source/)に保存しています。`source`と`review`はJekyllの生成サイトには出力されません。ただし、リポジトリをGitHubで公開すると、これらのファイル自体はGitHub上で閲覧できます。GitHub上でも非公開にしたい場合は、公開用リポジトリとは別の非公開リポジトリへ移してください。

## 構成

- `_records/`：各治療段階・症状の本文（Markdown）
- `_layouts/`：ページレイアウト
- `_includes/`：注意書き、SEO、パンくず、関連記事
- `_data/`：ナビゲーションと時系列
- `assets/`：CSSと移行した画像
- `source/`：Blogspot原文の保存データ（非公開）
- `review/`：公開前の確認資料（非公開）

## ローカル確認

Ruby 3.3とBundlerを用意し、リポジトリ直下で実行します。GitHub Pages 232の依存関係はRuby 4ではビルドできないため、このリポジトリではRuby 3.3を使用してください。

macOSでHomebrewを使う場合の例です。

```sh
brew install ruby@3.3
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"
```

続いてJekyllをインストールし、ローカルサーバーを起動します。

```sh
bundle config set --local path vendor/bundle
bundle install
bundle exec jekyll serve
```

ブラウザーで`http://127.0.0.1:4000/cancer/`を開きます。

GitHub Pagesがサポートするバージョンに合わせ、`github-pages` 232、Jekyll 3.10、`jekyll-sitemap` 1.4系を使用します。

## GitHub Pagesで公開

1. GitHubユーザー`northfoxjp`の下に`cancer`リポジトリを作成します。
2. このディレクトリの内容を`main`ブランチへpushします。
3. GitHubの **Settings → Pages** を開きます。
4. **Build and deployment** のSourceで **Deploy from a branch** を選びます。
5. Branchを`main`、フォルダーを`/(root)`にして保存します。
6. `https://northfoxjp.github.io/cancer/`を開き、HTTPSで表示できることを確認します。

## 新しい記録を追加

1. `_records/`にMarkdownファイルを追加します。
2. 既存ファイルを参考に、`title`、`description`、`permalink`、日付、パンくず、前後リンクをfront matterへ記載します。
3. 分類ページと必要に応じて`_data/timeline.yml`へリンクを追加します。
4. 本文では体験したことだけを記載し、薬を扱うページでは`medication_content: true`を指定します。
5. ローカルビルドでcanonical、OGP、構造化データ、内部リンクを確認します。

## SEO実装

各ページについて以下を出力します。

- ページ固有のtitleとmeta description
- `https://northfoxjp.github.io/cancer/`を基準とするself-canonical
- OGPとTwitter/X Card
- `BlogPosting`、`WebSite`、`CollectionPage`等のJSON-LD
- `BreadcrumbList`のJSON-LDと画面上のパンくず
- 前後ページ・関連ページへの内部リンク
- `jekyll-sitemap`による`sitemap.xml`
- `robots.txt`

Google Search ConsoleのHTMLタグで所有権を確認する場合は、`_config.yml`の次の値へ確認トークンだけを設定します。

```yaml
google_site_verification: "Search Consoleから発行された値"
```

公開後、Search ConsoleのURLプレフィックスプロパティへ`https://northfoxjp.github.io/cancer/`を登録し、`https://northfoxjp.github.io/cancer/sitemap.xml`を送信します。

## Cloudflare Web Analytics

GitHub Pagesのまま、Cloudflare Web Analyticsでアクセスを計測できます。

1. Cloudflare管理画面の **Web Analytics → Add a site** で、ホスト名 `northfoxjp.github.io` を登録します（`https://` や `/cancer/` は含めません）。すでに同じホスト名を登録している場合は、その設定を使用します。
2. **Manage site** に表示される計測コードの `token` の値を、`_config.yml` に設定します。

   ```yaml
   cloudflare_web_analytics_token: "発行された計測トークン"
   ```

   これはページに公開される計測用トークンです。Cloudflare APIトークンは設定しません。
3. GitHub Pagesへ公開すると、共通レイアウトを使う全ページの `</body>` 直前に計測コードが出力されます。
4. 公開サイトを閲覧し、数分後にCloudflare Web Analyticsでデータを確認します。同じホスト名に別サイトがある場合は、Pathで `/cancer/` 配下を絞り込みます。

トークンが空の場合と、通常のローカルプレビューでは計測コードを出力しません。本番と同じ出力をローカルで確認する場合は `JEKYLL_ENV=production bundle exec jekyll build` を実行します。GitHub Pagesのビルド環境は `production` です。

公式手順: [Cloudflare Web Analyticsの設定](https://developers.cloudflare.com/web-analytics/get-started/)

## Blogspot側の移行

新サイトの全ページが表示できることを確認するまでは、Blogspot記事を変更しません。

公開確認後、元記事`https://northfoxjp.blogspot.com/2023/01/blog-post.html`を次のような案内へ変更します。

```html
<h2>闘病記を新しいサイトへ移しました</h2>
<p>原発不明がん・中咽頭がんの治療記録は、治療段階や症状ごとに読みやすく整理した新サイトで公開しています。</p>
<ul>
  <li><a href="https://northfoxjp.github.io/cancer/">闘病記トップ</a></li>
  <li><a href="https://northfoxjp.github.io/cancer/timeline/">発見から現在までの時系列</a></li>
  <li><a href="https://northfoxjp.github.io/cancer/surgery/">手術の記録</a></li>
  <li><a href="https://northfoxjp.github.io/cancer/radiotherapy/">放射線治療の記録</a></li>
  <li><a href="https://northfoxjp.github.io/cancer/side-effects/oral-mucositis-and-hangeshashinto/">口内炎対策と半夏瀉心湯の記録</a></li>
  <li><a href="https://northfoxjp.github.io/cancer/side-effects/taste-and-eating/">味覚障害と食事の記録</a></li>
</ul>
<p>このページのURLは、以前のリンクやブックマークから来た方のために残しています。</p>
```

旧記事の全文は削除前にBloggerのバックアップ機能でも保存してください。旧URLは削除せず、移転案内として維持します。

## 更新時の注意

- `url`と`baseurl`を変更した場合はcanonical、OGP、サイトマップ、内部リンクを再確認する
- `source/`内の原文を上書きしない
- 医療上の一般論を本文へ追加する場合は、患者記録と明確に分け、出典を示す
- 薬や商品について「効く」「おすすめ」などへ一般化しない
- 画像を追加する前に個人情報と利用権を確認する
