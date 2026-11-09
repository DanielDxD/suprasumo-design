# SupraSumo Design

Skills de Cursor para design de interfaces e assets visuais.

1. **Referências** — consulta SceneAI, Land-book, 60fps e Recent para spec ou refactor de landings, web e mobile.
2. **Assets** — cria ícones, logos, banners e imagens no Canva (MCP) e busca fotos gratuitas livre de direitos (Pexels / Unsplash / Pixabay).

## Skills

| Skill | Gatilho | O que faz |
|---|---|---|
| `suprasumo-design-start` | Comando `/suprasumo-design-start` | Pesquisa referências e grava `spec.md` + `plan.md`. Não implementa. |
| `suprasumo-design-refact` | Comando `/suprasumo-design-refact` | Refatora UI existente a partir da melhor referência. |
| `canva-visual-assets` | **Automático** | Ícones, logos, banners e imagens via Canva MCP + fotos stock via imagebank-mcp. |

A skill de assets **não** usa `disable-model-invocation`: o agente carrega sozinho quando o pedido menciona ícone, logo, banner, hero, foto, ilustração, OG image, etc.

### Comandos de referência

```text
/suprasumo-design-start Landing para um app de finanças pessoais, público jovem, visual limpo

/suprasumo-design-refact Melhorar a home do site atual: hierarquia fraca e tipografia genérica
```

### Exemplos de gatilho automático (Canva / stock)

```text
Cria um ícone de app para um banco digital, fundo escuro, marca em dourado
Gera um logo tipográfico para a padaria Sourdough Lab
Preciso de um banner YouTube 2560×1440 para o lançamento
Busca uma foto de hero de café artesanal e salva em public/images
```

## Instalar skills

### Opção rápida (recomendado)

```bash
npx skills add DanielDxD/suprasumo-design -a cursor
```

Global (todos os projetos neste Mac):

```bash
npx skills add DanielDxD/suprasumo-design -a cursor -g
```

### Cópia manual

```bash
git clone https://github.com/DanielDxD/suprasumo-design.git
mkdir -p .cursor/skills
cp -R suprasumo-design/skills/* .cursor/skills/
```

Para todos os projetos: copie para `~/.cursor/skills/` em vez de `.cursor/skills/`.

## MCP necessários (assets)

### 1. Canva

Use o plugin / MCP oficial do Canva no Cursor (`plugin-canva-canva`). Autentique quando o agente pedir (`mcp_auth`). Sem Canva autenticado, a skill de assets não consegue gerar ícones/logos/banners.

### 2. Fotos free — [imagebank-mcp](https://github.com/romuloquintanilha/imagebank-mcp)

Busca Pexels, Unsplash e Pixabay, baixa e converte para WebP no projeto.

Chaves gratuitas (pelo menos uma):

- [Pexels API](https://www.pexels.com/api/)
- [Unsplash Developers](https://unsplash.com/developers) (Access Key)
- [Pixabay API](https://pixabay.com/api/docs/)

Em `~/.cursor/mcp.json` ou `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "image-banks": {
      "command": "npx",
      "args": ["-y", "imagebank-mcp"],
      "env": {
        "PEXELS_API_KEY": "your_key",
        "UNSPLASH_ACCESS_KEY": "your_key",
        "PIXABAY_API_KEY": "your_key"
      }
    }
  }
}
```

Reinicie o Cursor / MCP depois de salvar. Detalhes e alternativa (stocky): [`skills/canva-visual-assets/references/stock-images-mcp.md`](skills/canva-visual-assets/references/stock-images-mcp.md).

## Estrutura

```text
skills/
  suprasumo-design-start/
    SKILL.md
    references/sources.md
  suprasumo-design-refact/
    SKILL.md
  canva-visual-assets/
    SKILL.md
    references/stock-images-mcp.md
```

## Como funciona

### Referências (`start` / `refact`)

1. Classifica a superfície (landing, web ou mobile).
2. Abre as fontes certas (Land-book, SceneAI, 60fps, Recent).
3. Escolhe 1 referência e grava spec / aplica refactor.

| Superfície | Fontes principais |
|---|---|
| Landing | Land-book + SceneAI |
| Interface web | Recent + seções do Land-book |
| Mobile | 60fps + Interface do Recent |

### Assets (`canva-visual-assets`)

| Pedido | Ferramenta |
|---|---|
| Ícone, logo mark, ilustração, graphic | Canva `generate-image` |
| Banner / layout editável | Canva `create-design` (on-brand → `generate-design`) |
| Foto real para hero/seção | imagebank-mcp `search_images` → `download_image` |

## Regras

- Conteúdo e marca são do pedido; referências emprestam ofício, não copy/assets de terceiros.
- Fotos stock vão para disco do projeto (WebP) — sem hotlink no código final.
- Respeite termos do Canva e das galerias / providers de stock.

## Licença

Uso livre neste repositório. Respeite as licenças de SceneAI, Land-book, 60fps, Recent, Canva, Pexels, Unsplash e Pixabay.
