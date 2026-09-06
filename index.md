---
layout: default
title: "原発不明がん・中咽頭がん 闘病記 — 北きつねの治療記録"
description: "首のしこりの発見、原発不明がんの診断、頸部郭清術、中咽頭がんの判明、放射線治療、副作用、その後を患者本人が記録した闘病記です。"
schema_type: WebSite
permalink: /
---
<article class="home-page">
  <header class="record-header">
    <p class="eyebrow">患者本人の体験記</p>
    <h1>原発不明がん・中咽頭がん<br>北きつねの治療記録</h1>
    <p class="lead">首のしこりを見つけた日から、検査、診断、手術、放射線治療、副作用、治療後の経過までを時系列で残しています。</p>
  </header>

  {% include patient-notice.html %}

  <h2>治療全体の流れ</h2>
  <ol class="timeline">
    {% for event in site.data.timeline %}
      <li>
        <time>{{ event.date }}</time>
        <a href="{{ event.url | relative_url }}">{{ event.title }}</a>
      </li>
    {% endfor %}
  </ol>
  <p><a href="{{ '/timeline/' | relative_url }}">日付順の詳しい目次を見る</a></p>

  <h2>知りたい内容から読む</h2>
  <div class="card-grid">
    <a class="card" href="{{ '/diagnosis/' | relative_url }}"><strong>発見・検査・診断</strong><span>首の腫れ、細胞診、PET/CT、原発不明がん、中咽頭がんの判明</span></a>
    <a class="card" href="{{ '/surgery/' | relative_url }}"><strong>手術</strong><span>右頸部郭清術、両口蓋扁桃摘出術、入院、術後の経過</span></a>
    <a class="card" href="{{ '/radiotherapy/' | relative_url }}"><strong>放射線治療</strong><span>治療準備、33回の照射、途中の再入院、治療完了</span></a>
    <a class="card" href="{{ '/side-effects/' | relative_url }}"><strong>副作用・対策</strong><span>口内炎、半夏瀉心湯、皮膚、味覚障害、食事</span></a>
    <a class="card" href="{{ '/after-treatment/' | relative_url }}"><strong>治療後</strong><span>手術後の症状、味覚の回復、その後の生活</span></a>
  </div>

  <aside class="external-information">
    <h2>このサイトの文章について</h2>
    <p>2023年からBlogspotで公開していた本人の闘病記を、必要な記録へ直接たどり着けるよう治療段階ごとに分けたものです。本文は原文を可能な限り維持しています。</p>
    <p><a href="{{ '/source-and-update-history/' | relative_url }}">移行元と変更履歴を確認する</a></p>
  </aside>
</article>

