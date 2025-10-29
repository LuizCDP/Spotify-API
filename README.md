# 🎵 Spotify PKCE Login & Profile Viewer

Uma aplicação web simples e segura para autenticar usuários do Spotify usando **OAuth 2.0 com PKCE** (Proof Key for Code Exchange) e exibir informações completas do perfil e a música atual do usuário.  
Feito por **CDP 💚**

---

## 🧠 O que o código faz

Este projeto:
- Permite login via conta Spotify (sem precisar de backend).
- Coleta **dados do perfil** (nome, email, ID, seguidores, tipo de conta, foto).
- Exibe a **música atualmente tocando**, com capa, título, artistas e player embutido.
- Usa PKCE (seguro e recomendado pela própria Spotify).
- Tudo acontece **no navegador**, sem armazenar senhas.

---

## 🚀 Como usar

1. **Acesse o arquivo HTML** no navegador (ou hospede no Netlify, GitHub Pages, etc).  
2. Clique no botão **“Login no Spotify”**.  
3. O Spotify abrirá uma tela pedindo permissão.  
4. Após o login, a página vai:
   - Trocar o botão por uma área de perfil.
   - Mostrar:
     - Nome
     - Email
     - ID
     - Número de seguidores
     - Tipo de conta (Free/Premium)
     - Foto do perfil
   - Se o usuário estiver ouvindo algo: exibe o player com a música atual.

---

## 🔐 Entendendo o PKCE

PKCE é um método que:
- Gera um **code verifier** (chave aleatória).
- Cria um **code challenge** derivado dela.
- Envia o challenge pro Spotify (no login).
- Depois usa o verifier pra pegar o token, garantindo segurança — sem risco de roubo do token em apps front-end.

---

## ⚙️ Estrutura simplificada

| Parte | O que faz |
|-------|------------|
| `generateRandomString()` | Cria um código aleatório pra autenticação. |
| `generateCodeChallenge()` | Converte o código pra formato seguro SHA-256. |
| `getAccessToken()` | Troca o código de autorização pelo token de acesso. |
| `getUserProfile()` | Busca os dados do perfil via API `/v1/me`. |
| `getCurrentPlayingTrack()` | Busca a música atual via API `/v1/me/player/currently-playing`. |
| `main()` | Controla o fluxo geral (login → pegar token → mostrar dados). |

---

## 🧩 Escopos usados

Esses são os **scopes** solicitados ao Spotify:

```js
user-read-private
user-read-email
user-read-playback-state
```

Eles permitem ler informações do perfil e o status do player (sem controlar a música).

---

## 💡 Dicas

- Para usar em produção, registre seu app no [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/).  
- Copie o **Client ID** e substitua na variável `clientId` no código.  
- Coloque o mesmo **Redirect URI** configurado no painel.  
- **Não é necessário Client Secret** (PKCE cuida disso!).

---

## ⚠️ Importante

> ⚠️ Tome cuidado com os ["Spotify Developer Terms"](https://developer.spotify.com/terms).

> O site/widget é funcional apenas **integrado com o site do Spotify**.
 
> Alterações ou redistribuições são completamente permitidas.

---

## ✨ Créditos

Desenvolvido por **CDP** — programador, compositor e criador de experiências únicas.  
Feito com ❤️, HTML puro e a API oficial do Spotify.
