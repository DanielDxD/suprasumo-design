# SupraSumo Design

Skills de Cursor para desenhar landings, interfaces web e telas mobile a partir de referências reais.

As skills consultam quatro galerias públicas:

- [SceneAI](https://sceneai.art/)
- [Land-book](https://land-book.com/)
- [60fps](https://60fps.design/)
- [Recent](https://recent.design/)

Escolhem a melhor referência e geram specs consistentes — ou refatoram uma UI que já existe.

## Comandos

| Comando | O que faz |
|---|---|
| `/suprasumo-design-start` | Pesquisa referências, escolhe uma e grava `specs/<slug>/spec.md` + `plan.md`. **Não implementa código.** |
| `/suprasumo-design-refact` | Lê um site, app ou landing já pronto, escolhe referência e aplica a refatoração no código existente. |

No chat do Cursor, digite `/` e selecione o comando. Em seguida descreva o produto, o público e a superfície (`landing`, `web` ou `mobile`).

Exemplos:

```text
/suprasumo-design-start Landing para um app de finanças pessoais, público jovem, visual limpo

/suprasumo-design-refact Melhorar a home do site atual: hierarquia fraca e tipografia genérica
```

## Instalar

### Opção rápida (recomendado)

No projeto onde você quer usar as skills:

```bash
npx skills add DanielDxD/suprasumo-design -a cursor
```

Para instalar de forma global (todos os projetos neste Mac):

```bash
npx skills add DanielDxD/suprasumo-design -a cursor -g
```

### Cópia manual

1. Clone o repositório:

```bash
git clone https://github.com/DanielDxD/suprasumo-design.git
```

2. Copie as pastas das skills para o projeto:

```bash
mkdir -p .cursor/skills
cp -R suprasumo-design/skills/suprasumo-design-start .cursor/skills/
cp -R suprasumo-design/skills/suprasumo-design-refact .cursor/skills/
```

Ou, para valer em todos os projetos:

```bash
mkdir -p ~/.cursor/skills
cp -R suprasumo-design/skills/suprasumo-design-start ~/.cursor/skills/
cp -R suprasumo-design/skills/suprasumo-design-refact ~/.cursor/skills/
```

3. Reinicie o agente / abra um novo chat no Cursor para o menu `/` listar os comandos.

## Estrutura

```text
skills/
  suprasumo-design-start/
    SKILL.md
    references/
      sources.md          # mapa de URLs e filtros das quatro galerias
  suprasumo-design-refact/
    SKILL.md              # lê o mapa compartilhado acima
```

## Como funciona

### `/suprasumo-design-start`

1. Classifica a superfície (landing, web ou mobile).
2. Abre só as fontes certas, com o termo do assunto.
3. Compara 3 candidatos públicos e fica com 1 referência.
4. Grava em `specs/<slug>/`:
   - `spec.md` — estrutura, tipografia, cor, movimento, assinatura, o que não copiar
   - `plan.md` — stack, arquivos, ordem e verificação
5. Para. A implementação fica para um passo seguinte.

### `/suprasumo-design-refact`

1. Lê a UI atual (rotas, componentes, estilos, conteúdo).
2. Busca referência pelo que a interface faz mal.
3. Grava `specs/<slug>/refactor.md`.
4. Aplica a mudança no código existente — sem trocar de stack e sem recriar o produto.
5. Verifica no browser o fluxo principal.

## Fontes por superfície

| Superfície | Fontes principais |
|---|---|
| Landing | Land-book + SceneAI (Recent desempata gosto) |
| Interface web | Recent + seções do Land-book |
| Mobile | 60fps + Interface do Recent |

Detalhes de URL e filtros: [`skills/suprasumo-design-start/references/sources.md`](skills/suprasumo-design-start/references/sources.md).

## Regras

- Conteúdo, nome e marca são do pedido. A referência empresta ritmo, escala, contraste, respiro e um gesto de movimento.
- Não cola headline, screenshot, logo ou asset de terceiro.
- Usa só o que as galerias mostram em público. Não fura paywall.
- Uma assinatura visual. O resto fica quieto.

## Licença

Uso livre neste repositório. Respeite as licenças e termos de SceneAI, Land-book, 60fps e Recent ao consultar as galerias.
