<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake.svg">
</picture>


```
https://7xhub-api.shardweb.app/api/ia/nano?prompt={prompt}&ref={files/link}&auth={auth_key}
```

---
## 1) Gerar imagens **(Metodo Get)**

**Resposta (200)**
```json
{
  "developer": "7XHUB APIS",
  "status": "success",
  "type": "without_reference", // Sem referência
  "image": {
    "image_id": "802eba30bded44299414830ad85e9a84",
    "prompt": "Gere um avião vermelho! ✈️",
    "reference_used": false,
    "reference_size": false,
    "generated_image_size": {
      "bytes": 1495163,
      "kb": 1460.12
    },
    "time": 9646.74,
    "url": "<domínio>/api/generate/nano?imagem=802eba30bded44299414830ad85e9a84"
  }
}
```

## 2) Gerar imagens **(Metodo Post)**

**Resposta (200)**
```json
{
  "developer": "7XHUB APIS",
  "status": "success",
  "type": "with_reference", // Usando referência
  "image": {
    "image_id": "7c945398925c41b0a182ee95d1a341e5",
    "prompt": "Altere para cores vermelhas.",
    "reference_used": true,
    "reference_size": {
      "bytes": 1029456,
      "kb": 1005.33
    },
    "generated_image_size": {
      "bytes": 1970461,
      "kb": 1924.28
    },
    "time": 14872.94,
    "url": "<domínio>/api/generate/nano?imagem=7c945398925c41b0a182ee95d1a341e5"
  }
}
```

**Erros**
- 400 `{ "type": "invalid_request" }`
- 404 `{ "type": "player_not_found" }`
- 500 `{ "type": "erro_interno" }`
---
