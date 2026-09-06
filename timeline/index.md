---
layout: hub
title: "発見から現在までの時系列"
description: "2022年1月の首のしこり発見から、原発不明がんの診断、手術、中咽頭がんの判明、放射線治療、治療後までの患者記録を時系列で案内します。"
schema_type: CollectionPage
permalink: /timeline/
stage: 全体の経過
lead: 各日付から、その時期の本人の詳しい記録へ移動できます。
patient_notice: true
---
<ol class="timeline">
  {% for event in site.data.timeline %}
    <li>
      <time>{{ event.date }}</time>
      <a href="{{ event.url | relative_url }}">{{ event.title }}</a>
    </li>
  {% endfor %}
</ol>

## 記録の読み方

各ページはBlogspotの一つの長文記事を、治療段階と話題ごとに分けたものです。日付、当時の言葉、感じたことは原文を可能な限り維持しています。

