---
name: suprasumo-design-refact
description: >-
  Refatora um site, app ou landing já pronto a partir da melhor referência
  pública em SceneAI, Land-book, 60fps e Recent. Use quando o usuário chamar
  /suprasumo-design-refact, /suprasumo-design refact, pedir redesign, polish,
  restyle ou melhorar a UI existente sem recriar o produto.
disable-model-invocation: true
---

# /suprasumo-design-refact

Lê a interface existente, escolhe uma referência e aplica a refatoração no código atual. Não troca de stack e não recria o produto do zero.

## Entrada

O texto depois do comando aponta o site, app ou landing a melhorar e o que deve mudar.

- Se o alvo não estiver claro, usar a interface aberta ou a rota principal e dizer qual foi.
- Se a superfície não vier no texto, inferir pela UI existente.

## Fluxo

1. Ler a UI atual: rotas, componentes, estilos, conteúdo e o que já funciona.
2. Classificar a superfície: **landing**, **interface web** ou **mobile**.
3. Ler o mapa compartilhado em [../suprasumo-design-start/references/sources.md](../suprasumo-design-start/references/sources.md). Abrir só as fontes da superfície, com o termo do assunto e o que a UI atual faz mal (hierarquia, tipografia, respiro, movimento).
4. Comparar 3 candidatos públicos. Pontuar 1–5 pelos critérios do mapa e ficar com 1 referência.
5. Criar `specs/<slug>/` se ainda não existir. `<slug>` sai do nome do produto ou da rota em hífens. Se a pasta já existir, reutilizar. Gravar `refactor.md`.
6. Aplicar a refatoração no código existente. Manter rotas, dados, copy e comportamento, salvo quando o pedido pedir troca explícita.
7. Abrir no browser e exercer o fluxo principal, mais estados vazios ou de erro que a mudança tocar.

## `specs/<slug>/refactor.md`

```markdown
# Refactor — <alvo>

## Superfície
landing | interface web | mobile

## Alvo atual
Rotas, componentes e arquivos tocados.

## Referência escolhida
- URL:
- Por quê (ligado ao que a UI atual faz mal):

## Alternativas descartadas
- URL — motivo
- URL — motivo

## O que muda
Hierarquia, tipografia, cor, densidade, movimento, assinatura.

## O que permanece
Rotas, dados, copy, comportamento, stack.

## Não copiar
Headlines, screenshots, logos e assets da referência.

## Verificação
Fluxos e estados a exercitar no browser.
```

## Regras

- Conteúdo, nome e marca do produto permanecem. A referência empresta ritmo, escala, contraste, respiro e um gesto de movimento.
- Não colar headline, screenshot, logo ou asset de terceiro.
- Não trocar de stack. Não recriar o app, site ou landing do zero.
- Uma assinatura visual. O resto fica quieto.
- Manter responsivo, foco visível e `prefers-reduced-motion`.
- Usar só conteúdo público das galerias. Não furar paywall.
- Se `frontend-design`, `cinematographic-websites` ou `ui-ux-pro-max` se aplicarem ao código, segui-las. Não misturar motores de animação que essas skills proíbem.
