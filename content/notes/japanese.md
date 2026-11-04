---
publish: true
title: 日本語のページ
created: 2026-11-04
tags:
  - sample
  - japanese
---

# 日本語のページ

Riebeckite は日本語の Markdown をそのまま扱えます。見出し、段落、箇条書き、コード、表、WikiLink がすべて表示されます。

## コンテンツの配置

このサンプルでは、Markdown は `content/`（リポジトリ分離型では Vault リポジトリ）に置かれています。

- WikiLink: [[welcome]]
- Markdown リンク: [Markdown の例](markdown.md)
- タグ: `sample` と `japanese`

## コード

```ts
const message = "こんにちは、Riebeckite";
console.log(message);
```

## 表

| 項目 | 値 |
| --- | --- |
| 言語 | 日本語 |
| 静的サイト | はい |
| 配置方式 | 一体型 |

> [!note]
> Obsidian のコールアウト記法もそのまま使えます。

トップページは[こちら](/)です。
