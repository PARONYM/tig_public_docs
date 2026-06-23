---
title: 画面から探す（CMS）
nav_order: 1.8
---

# 画面から探す（CMS）

CMSの画面・メニュー導線から機能ドキュメントを辿れます。リンク名はCMSの実画面に準拠しています。
（言葉で探したい場合は、左メニューの「検索」をご利用ください）

{% assign cms_pages = site.pages | where_exp: "p", "p.cms_path" %}
{% if cms_pages.size == 0 %}
> まだ索引対象のページがありません。各機能ページの frontmatter に `cms_section` / `cms_path` を付けると、ここに自動で並びます。
{% else %}
{% assign sections = cms_pages | group_by: "cms_section" %}
{% for sec in sections %}
## {{ sec.name }}

{% for p in sec.items %}- [{{ p.cms_link_label | default: p.title }}]({{ p.url | relative_url }}) — {{ p.cms_path }}
{% endfor %}
{% endfor %}
{% endif %}
