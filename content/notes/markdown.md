---
publish: true
title: Markdown and links
tags:
  - sample
---

# Markdown and links

Riebeckite keeps ordinary Markdown ordinary.

## Markdown links

- [Home](/)
- [日本語のページ](japanese.md)
- [Welcome](welcome.md)
- [External link](https://riebeckite.dev)

## A code block

```ts
export function greet(name: string): string {
  return `Hello, ${name}`;
}
```

## A table

| Input | Output |
| --- | --- |
| `[[welcome]]` | A link to the Welcome page |
| `[Welcome](welcome.md)` | The same page through Markdown |

## Blockquote

> Content belongs in Markdown. The site belongs in code. Keep them where your team can find them.

Back to [[welcome]].
