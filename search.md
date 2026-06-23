---
title: 検索
nav_order: 1.5
---

<link href="{{ '/pagefind/pagefind-ui.css' | relative_url }}" rel="stylesheet">

<div id="search" data-pagefind-ignore></div>

<script src="{{ '/pagefind/pagefind-ui.js' | relative_url }}"></script>
<script>
  window.addEventListener('DOMContentLoaded', function () {
    new PagefindUI({
      element: "#search",
      bundlePath: "{{ '/pagefind/' | relative_url }}",
      showSubResults: true,
      showImages: false,
      translations: {
        placeholder: "ドキュメントを検索",
        clear_search: "クリア",
        load_more: "さらに表示",
        search_label: "ドキュメント内を検索",
        filters_label: "絞り込み",
        zero_results: "[SEARCH_TERM] に一致する結果がありません",
        many_results: "[SEARCH_TERM] の検索結果: [COUNT] 件",
        one_result: "[SEARCH_TERM] の検索結果: [COUNT] 件",
        alt_search: "[SEARCH_TERM] の結果なし。[DIFFERENT_TERM] の結果を表示しています",
        search_suggestion: "[SEARCH_TERM] に一致する結果がありません。次の語をお試しください:",
        searching: "[SEARCH_TERM] を検索中..."
      }
    });
  });
</script>
