<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/0xme/0xme/output/github-contribution-grid-snake.svg">
</picture>

## 1) Gerar imagem **(Sem referência)**

**Exemplo de requisição python**
```python
import requests
import base64
import os

def gerar_imagem_nano(prompt, auth, ref_url=None, salvar_como="resultado.png"):
    """
    Função para gerar imagem usando a API Nano7x via método GET.
    
    Parâmetros:
    - prompt: Texto descrevendo a imagem desejada.
    - auth: Chave de autenticação fornecida pela API.
    - ref_url: (Opcional) URL de uma imagem de referência.
    - salvar_como: Nome do arquivo para salvar a imagem gerada.
    
    Retorna:
    - Dicionário com resposta da API.
    """

    url = "https://7xhub-api.shardweb.app/api/ia/nano7x"
    
    # Monta os parâmetros da requisição
    params = {
        "prompt": prompt,
        "auth": auth
    }

    # Se houver URL de referência, adiciona
    if ref_url:
        params["ref"] = ref_url

    try:
        # Requisição GET
        response = requests.get(url, params=params, timeout=300)
        response.raise_for_status()  # Garante que erros HTTP sejam lançados
        data = response.json()

        # Se a API retornar base64 da imagem
        if "image_base64" in data:
            imagem_bytes = base64.b64decode(data["image_base64"])
            with open(salvar_como, "wb") as f:
                f.write(imagem_bytes)
            print(f"Imagem salva como {salvar_como}")
        
        # Se a API retornar URL da imagem
        elif "image_url" in data:
            img_response = requests.get(data["image_url"], timeout=300)
            img_response.raise_for_status()
            with open(salvar_como, "wb") as f:
                f.write(img_response.content)
            print(f"Imagem baixada da URL e salva como {salvar_como}")
        
        else:
            print("Resposta da API não contém imagem para salvar.")

        return data

    except requests.exceptions.RequestException as e:
        print("Erro na requisição:", e)
        return None

# ===============================
# Exemplo de uso
# ===============================
if __name__ == "__main__":
    prompt = "Gere um avião. ✈️"
    auth = "auth_key"
    ref_url = None  # Ou uma URL de imagem de referência, ex: "https://site.com/logo.png"

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
