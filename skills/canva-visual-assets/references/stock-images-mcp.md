# MCP de imagens gratuitas (livre de direitos)

Recomendado para fotos de site/app: **[imagebank-mcp](https://github.com/romuloquintanilha/imagebank-mcp)**.

Busca em **Pexels**, **Unsplash** e **Pixabay**, baixa a imagem, converte para **WebP** e grava no projeto. Adequado a agentes que implementam UI (evita hotlink).

## Por que este MCP

| MCP | Prós | Contras |
|---|---|---|
| **imagebank-mcp** | `npx`, download + WebP no projeto, 3 providers, tracking Unsplash | Precisa de API key |
| [stocky](https://github.com/joelio/stocky) | Pexels + Unsplash, atribuição, `uvx stocky-mcp` | Menos focado em WebP no repo |
| [@ahmaddioxide/mcp-image-resolver](https://www.npmjs.com/package/@ahmaddioxide/mcp-image-resolver) | `npx`, search / best image | Menos pipeline de download no projeto |

## Chaves (gratuitas)

Configure pelo menos uma:

- Pexels: https://www.pexels.com/api/
- Unsplash Access Key: https://unsplash.com/developers
- Pixabay: https://pixabay.com/api/docs/

Nunca commitar chaves no repositório.

## Cursor — `~/.cursor/mcp.json` ou `.cursor/mcp.json`

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

Reinicie o MCP / Cursor depois de salvar. Só as chaves preenchidas são usadas.

## Alternativa — stocky

```json
{
  "mcpServers": {
    "stocky": {
      "command": "uvx",
      "args": ["stocky-mcp"],
      "env": {
        "PEXELS_API_KEY": "your_key",
        "UNSPLASH_ACCESS_KEY": "your_key"
      }
    }
  }
}
```

## Ferramentas esperadas (imagebank-mcp)

1. `search_images` — query em inglês; filtros de orientation / cor.
2. `download_image` — salva WebP no working directory; dispara tracking Unsplash quando aplicável.
3. `optimize_local_image` — otimiza foto já local do cliente.

## Licença (resumo)

Os três providers permitem uso comercial gratuito na maioria dos casos. Atribuição no site final costuma ser opcional (apreciada). Unsplash exige notificar download via API ao usar a foto — o MCP faz isso no download. Pixabay proíbe hotlink permanente — baixar resolve. Evite rostos reconhecíveis em anúncios pagos. Confirme os termos atuais de cada provider para o seu caso; isto não é aconselhamento jurídico.
