# Fontes de referência

Mapa compartilhado por `/suprasumo-design-start` e `/suprasumo-design-refact`. Abrir só as fontes da superfície do pedido. Usar conteúdo público. Não furar paywall, não baixar assets premium, não redistribuir prompts.

## Roteamento por superfície

| Superfície | Fontes principais | Apoio |
|---|---|---|
| Landing | Land-book (página + hero, pricing, CTA), SceneAI | Recent `/websites` para desempate de gosto; 60fps só se o pedido pedir movimento de produto |
| Interface web | Recent (Web/Interface no browser), seções do Land-book | SceneAI quando o alvo for hero ou página de marketing |
| Mobile | 60fps, peças Interface do Recent | Land-book só para a página de marketing do app |

## Land-book

Galeria curada de websites, seções e motion.

- Galeria: https://land-book.com/
- Busca: `https://land-book.com/?search={termo}`
- Landing pages: https://land-book.com/design/landing-page
- Portfolios: https://land-book.com/design/portfolio
- Ecommerce: https://land-book.com/design/ecommerce
- Motion: https://land-book.com/motion
- Seções: https://land-book.com/sections
- Hero: https://land-book.com/sections/hero
- Value proposition: https://land-book.com/sections/value-proposition
- Features: https://land-book.com/sections/features
- How it works: https://land-book.com/sections/how-it-works
- Pricing: https://land-book.com/sections/pricing
- CTA: https://land-book.com/sections/call-to-action
- Footer: https://land-book.com/sections/footer
- Entrada individual: `https://land-book.com/websites/{slug}`
- Mapa máquina: https://land-book.com/llms.txt

Limites: filtros e resultados amplos podem exigir Pro. Usar o que a página pública mostrar. `/mobile` retorna 404 — não usar essa URL para UI de app.

## SceneAI

Biblioteca pública de direção visual para heroes e landings.

- Home / galeria: https://sceneai.art/
- Gradientes: https://sceneai.art/gradients
- Gradientes animados: https://sceneai.art/gradients/animated-gradients

Usar só o que a galeria pública mostra: composição, tipografia, atmosfera, gradiente, densidade. Não copiar prompts premium, não baixar assets, não furar paywall. A licença proíbe redistribuir prompts e assets.

## 60fps

Referência de interação, motion e craft de app.

- Galeria (shots): https://60fps.design/
- Filtros: https://60fps.design/shots/filter
- Filtro por slug: `https://60fps.design/shots/filter/{slug}`
- Shot individual: `https://60fps.design/shots/{slug}`
- Busca: https://60fps.design/search
- Apps: https://60fps.design/apps
- App sites: https://60fps.design/appsites
- Motion: https://60fps.design/motion
- Storyboards: https://60fps.design/storyboards
- Glossário: https://60fps.design/glossary
- Mapa máquina: https://60fps.design/llms.txt
- MCP (se já conectado): https://mcp.60fps.design/mcp

Filtros úteis públicos: `onboarding`, `get-started`, `splash`, `loading`, `empty-state`, `bottom-sheet`, `carousel`, `tabs`, `success-state`, `pricing`, `intro`.

Limites: parte dos filtros e storyboards é Pro. Usar o que a página pública mostrar. Se o MCP já estiver autenticado no ambiente, preferir a busca dele. Não instalar plano pago.

## Recent

Curadoria diária de websites, interfaces e motion.

- Home: https://recent.design/
- Websites: https://recent.design/websites
- Categorias em `/websites`: All, AI, Agency, Portfolio, SaaS, Ecommerce, Startup, Product, Technology, Finance, Food & Drink, Music, Art, Photography, Architecture, Health, Education, Entertainment, Web3, Crypto, Editorial, Personal
- Peça individual: `https://recent.design/i/{id}-{slug}`

Filtros Web, Interface, Branding, Motion, Illustration, Posters e Print na home são client-side: abrir no browser e clicar. Metadados úteis na peça: Category, Style, Color, Interaction.

## Como escolher

Pontuar 1–5 e ficar com a maior soma:

1. Encaixa no assunto e na superfície
2. Hierarquia, tipografia, espaçamento e movimento estão resolvidos
3. Dá para reconstruir com o conteúdo e o stack deste pedido
4. Não é só a marca de um produto famoso

Em empate, preferir a estrutura que ensina a página, não o efeito mais chamativo. Citar a URL escolhida.
