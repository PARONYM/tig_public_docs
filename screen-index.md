---
title: 画面から探す
nav_order: 1.8
---

# 画面から探す

CMS・プレーヤーの画面/メニュー導線から機能ドキュメントを辿れます。リンク名は実画面に準拠しています。
（言葉で探したい場合は、左メニューの「検索」をご利用ください）

{% assign nav_pages = site.pages | where_exp: "p", "p.nav_path" %}
{% if nav_pages.size == 0 %}
> まだ索引対象のページがありません。各ページの frontmatter に `surface`（CMS / プレーヤー）・`nav_section`・`nav_path` を付けると、ここに自動で並びます。
{% else %}
{% assign surfaces = nav_pages | group_by: "surface" %}
{% for s in surfaces %}
## {{ s.name }}
{% assign sections = s.items | group_by: "nav_section" %}
{% for sec in sections %}
### {{ sec.name }}

{% for p in sec.items %}- [{{ p.nav_label | default: p.title }}]({{ p.url | relative_url }}) — {{ p.nav_path }}
{% endfor %}
{% endfor %}
{% endfor %}
{% endif %}
