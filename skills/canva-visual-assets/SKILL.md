---
name: canva-visual-assets
description: >-
  Cria e exporta assets visuais no Canva via MCP (ícones de app, logos, banners,
  ilustrações, OG images, stickers, gráficos) e busca fotos gratuitas livre de
  direitos via MCP de stock (Pexels, Unsplash, Pixabay). Use sempre que o usuário
  pedir ícone, logo, banner, favicon, app icon, imagem de hero, foto de produto,
  ilustração, artwork, sticker, thumbnail, capa, OG image, social post, ou
  qualquer imagem para site ou app — mesmo sem citar Canva, stock ou esta skill.
  Também use ao implementar UI que precise de mídia e o projeto não tiver assets.
---

# Canva Visual Assets

Produz assets no Canva e fotos stock livres de direitos para sites e apps. Carrega por gatilho automático — não espere o usuário nomear a skill.

## Pré-requisitos

1. **Canva MCP** (`plugin-canva-canva` / ferramentas `Canva:*`). Se faltar auth, autentique com `mcp_auth` nesse namespace e continue.
2. **Stock MCP** recomendado: [imagebank-mcp](https://github.com/romuloquintanilha/imagebank-mcp) (`search_images`, `download_image`). Setup em [references/stock-images-mcp.md](references/stock-images-mcp.md). Se o MCP não estiver conectado, diga como instalar e peça as chaves; não invente URLs de foto.

Descubra schemas com `GetDynamicTools` antes de chamar ferramentas.

## Quando usar o quê

| Pedido | Ferramenta |
|---|---|
| Ícone de app, favicon, sticker, ilustração, graphic, “imagem de…”, artwork | `generate-image` |
| Logo como arte standalone (mark, wordmark ilustrado) | `generate-image` com `SQUARE_1_1` (ou ratio pedido) |
| Logo editável no Canva / brand kit | `generate-design` com `design_type: "logo"` (+ `brand_kit_id` se o usuário pedir marca) |
| Banner, flyer, poster, social post, YouTube banner, capa editável | `create-design` (brief + format). On-brand → `generate-design` / brand kit |
| Foto real de cena, ambiente, produto genérico, gente, natureza | Stock MCP: `search_images` → `download_image` |
| Exportar design Canva para o projeto | `get-export-formats` → `export-design` (png/jpg) |

Regra Canva: se o usuário pediu **image / picture / photo / illustration / artwork / sticker / icon / graphic / 2d vector**, use `generate-image`. Se pediu **página editável** (poster, flyer, infographic, presentation), use `create-design`.

## Fluxo — Canva `generate-image`

1. Confirme assunto, uso (app icon, logo, hero art…) e ratio. Se faltar, assuma o ratio da tabela abaixo e diga o que assumiu.
2. Chame `generate-image` com:
   - `prompt`: palavras do usuário, sem reescrever (salvo se pedirem refinar)
   - `user_intent`: resumo curto do objetivo
   - `aspectRatio`: enum Canva (`SQUARE_1_1`, `LANDSCAPE_16_9`, …) — nunca `1:1` cru
3. Se houver widget de UI, **não** faça poll. Sem widget, poll `get-generate-image-job` até SUCCESS/FAILURE.
4. Mostre o resultado e o link “Open generated image”. Ofereça exportar ou ajustar.

### Ratios padrão

| Uso | `aspectRatio` |
|---|---|
| App icon / favicon / logo mark | `SQUARE_1_1` |
| Banner web / hero wide | `LANDSCAPE_16_9` |
| Banner ultrawide | `LANDSCAPE_2_1` |
| Story / mobile tall | `PORTRAIT_9_16` |
| Social feed (4:5) | `PORTRAIT_4_5` |
| Thumb YouTube-ish | `LANDSCAPE_16_9` |

### Prompt de ícone / logo (quando o usuário for vago)

Complete só em `user_intent` e, se precisar refinar o prompt com o usuário, peça confirmação. Para ícones: forma simples, silhueta legível em 32px, fundo sólido ou transparente pedido, sem texto miúdo. Para logos: 1–2 cores, contraste alto, sem mockup de mockup.

## Fluxo — Canva `create-design` / banners

1. `brief` com sujeito, propósito, texto, tom e cores pedidas.
2. `format` quando o tamanho importa (ex.: `"YouTube Banner"`, `"Instagram Post"`, `"Facebook Cover"`). Sem orientação o Canva pode sair quadrado.
3. Poll `get-create-design-async-job` só se não houver widget.
4. Entregue o link do design. Para arquivo no disco: `export-design`.

On-brand (brand kit / template da marca): não use `create-design`. Use `list-brand-kits`, confirme o kit, depois `generate-design` (ex. `design_type: "logo"` ou `"youtube_banner"`).

## Fluxo — fotos stock (sites/apps)

1. Query em **inglês**, específica (`"sourdough loaf on wooden board morning light"`, não `"nice food"`).
2. `orientation` alinhada ao layout (`landscape` hero, `portrait` mobile, `square` cards).
3. Escolha 1 resultado (evite rostos reconhecíveis em ads pagos).
4. `download_image` para pasta do projeto (`public/images/` ou `assets/` — siga o repo). Nunca hotlink URL de stock no código final.
5. Use o path local no HTML/JSX. Credite autor/provider no commit ou README se o provider exigir; Unsplash: respeite tracking de download que o MCP já dispara.

Se o stock MCP estiver ausente, diga para instalar [imagebank-mcp](references/stock-images-mcp.md) com pelo menos uma chave (Pexels ou Unsplash). Alternativa: [stocky](https://github.com/joelio/stocky) via `uvx stocky-mcp`.

## Integração com UI

Ao construir ou refatorar site/app e faltar mídia:

1. Assets de marca (ícone, logo, ilustração) → Canva.
2. Fotografia de atmosfera → stock MCP.
3. Salve em paths estáveis e referencie no código.
4. Não invente `https://picsum...` ou placeholders genéricos se o MCP estiver disponível.

## Regras

- Não afirme que o arquivo foi salvo no Canva sem commit/export bem-sucedido.
- Não furar paywall Canva Pro: se a ferramenta falhar por plano, explique e ofereça alternativa (stock ou prompt mais simples).
- Não redistribua assets Canva fora dos termos da conta do usuário.
- Uma intenção por chamada: ícone ≠ banner ≠ foto stock.
- Preferir assets do cliente quando já existirem no repo; otimize em vez de regenerar.
