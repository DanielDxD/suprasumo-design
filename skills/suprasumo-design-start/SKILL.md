---
name: suprasumo-design-start
description: >-
  Pesquisa referências em SceneAI, Land-book, 60fps e Recent, escolhe a melhor
  e grava spec e plano para landing, interface web ou mobile. Use quando o
  usuário chamar /suprasumo-design-start, /suprasumo-design start, pedir spec
  de UI, moodboard, plano de landing, ou começar um design a partir de
  referências. Não implementa código de interface.
disable-model-invocation: true
---

# /suprasumo-design-start

Pesquisa referências públicas, escolhe uma e grava `spec.md` + `plan.md`. Não implementa UI.

## Entrada

O texto depois do comando traz produto, público e superfície (web, mobile ou landing).

- Se a superfície não vier no texto, inferir pelo pedido.
- Se o produto não der para nomear, perguntar antes de buscar.

## Fluxo

1. Classificar a superfície: **landing**, **interface web** ou **mobile**.
2. Ler [references/sources.md](references/sources.md) e abrir só as fontes daquela superfície, com o termo do assunto.
3. Comparar 3 candidatos públicos. Pontuar 1–5 pelos critérios do mapa e ficar com 1 referência.
4. Criar `specs/<slug>/` no projeto atual. `<slug>` sai do nome do produto em hífens. Se a pasta já existir, usar `-2`, `-3` — nunca sobrescrever.
5. Gravar os dois arquivos abaixo.
6. Entregar os caminhos e a URL da referência. **Parar.** Não escrever código de interface.

## Arquivos

### `specs/<slug>/spec.md`

```markdown
# Spec — <produto>

## Superfície
landing | interface web | mobile

## Referência escolhida
- URL:
- Por quê:

## Alternativas descartadas
- URL — motivo
- URL — motivo

## Estrutura
Seções ou telas, na ordem de leitura.

## Tipografia
Papéis: display, body, utility. Famílias e escala.

## Cor
Paleta nova para este assunto (4–6 hex nomeados). Relação claro/escuro e acento.

## Densidade
Respiro, grid, ritmo de seções.

## Movimento
Gatilho e sensação. Não clonar timing proprietário.

## Conteúdo
Copy, marca e dados do pedido.

## Assinatura visual
O único gesto memorável da interface.

## Não copiar
Headlines, screenshots, logos e assets da referência.

## Fora de escopo
O que esta spec não cobre.
```

### `specs/<slug>/plan.md`

```markdown
# Plano — <produto>

## Stack
Stack do projeto, ou HTML/CSS se não houver stack.

## Arquivos a criar
Lista de paths.

## Ordem
Passos de implementação.

## Verificação
Como confirmar no browser ou no alvo.
```

## Regras

- Conteúdo, nome e marca são do pedido. A referência empresta ritmo, escala, contraste, respiro e um gesto de movimento.
- Não colar headline, screenshot, logo ou asset de terceiro.
- Uma assinatura visual. O resto fica quieto.
- Usar só conteúdo público das galerias. Não furar paywall.
- Se `frontend-design`, `cinematographic-websites` ou `ui-ux-pro-max` se aplicarem ao projeto, refletir isso no plano sem misturar motores de animação que essas skills proíbem.
