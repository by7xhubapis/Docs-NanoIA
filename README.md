<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake.svg">
</picture>

## 1) Gerar imagem **(Metodo Get)**

**Exemplo de requisição python**
```python
import requests

def gerar_imagem_nano(prompt, auth, ref_url=None):
    """
    Gera uma imagem usando a API Nano7x via GET.
    
    Parâmetros:
    - prompt: Texto descrevendo a imagem desejada.
    - auth: Chave de autenticação da API.
    - ref_url: (Opcional) URL de imagem de referência.
    
    Retorna:
    - Resposta da API em JSON.
    """

    url = "https://7xhub-api.shardweb.app/api/ia/nano7x"
    
    # Monta os parâmetros da requisição
    params = {
        "prompt": prompt,
        "auth": auth
    }

    if ref_url:
        params["ref"] = ref_url

    try:
        response = requests.get(url, params=params, timeout=300)
        response.raise_for_status()  # Lança erro se status != 200
        return response.json()
    except requests.exceptions.RequestException as e:
        print("Erro na requisição:", e)
        return None

# ===============================
# Exemplo de uso
# ===============================
if __name__ == "__main__":
    prompt = "Deixa com cores vermelhas"
    auth = "7xHub-1DjX9NcR-qx82AUio-cQxz7ApO"
    ref_url = None  # Pode colocar uma URL de referência se quiser

    resultado = gerar_imagem_nano(prompt, auth, ref_url)
    print("Resposta da API:", resultado)
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
