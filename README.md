<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake.svg">
</picture>

## 1) Gerar imagem **(Sem referência)**

**Exemplo de requisição python**
```
GET https://7xhub-api.shardweb.app/api/ff/search-nickname?nickname={nome}&region={region}&auth={auth_key}
```

**Resposta (200)**
```json
{
  "developer": "7XHUB APIS",
  "status": "success",
  "quantidadeContas": 2,
  "contas": [
    {
      "id": "13454812921",
      "nivel": 2,
      "experiencia": 48,
      "nickname": "7xHub-#727",
      "regiao": "br"
    },
    {
      "id": "13429214319",
      "nivel": 2,
      "experiencia": 48,
      "curtidas": 98,
      "nickname": "7xhub-#828",
      "regiao": "br"
    }
  ]
}
```

**Erros**
- 400 `{ "type": "invalid_request" }`
- 404 `{ "type": "player_not_found" }`
- 500 `{ "type": "erro_interno" }`
---
