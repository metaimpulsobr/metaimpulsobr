# 🛠️ Como Configurar o Seu Perfil Premium do GitHub

Este arquivo contém todas as instruções necessárias para você personalizar os componentes do seu novo `README.md` no GitHub.

---

## 1. Criar o Repositório do Perfil do GitHub
Se você ainda não criou o seu repositório de perfil:
1. Vá para o [GitHub](https://github.com) e clique em **New Repository** (Novo Repositório).
2. O nome do repositório **deve ser exatamente o seu nome de usuário** do GitHub (ex: se seu usuário for `lucasdev`, o repositório deve se chamar `lucasdev`).
3. Defina o repositório como **Public** (Público).
4. Marque a opção **Initialize this repository with a README** (Inicializar com um README).
5. Copie o arquivo `README.md` e a pasta `assets` que criamos aqui para dentro desse repositório.

---

## 2. Substituir os Placeholders no `README.md`
Abra o arquivo `README.md` no seu editor ou diretamente no GitHub e faça as seguintes substituições de texto:

- `SEU_USUARIO_GITHUB` ➔ Substitua pelo seu nome de usuário exato no GitHub (usado nas estatísticas e contador de visitas).
- `SEU_LINKEDIN` ➔ Substitua pelo seu link ou ID do LinkedIn.
- `SEU_EMAIL@gmail.com` ➔ Substitua pelo seu endereço de e-mail de contato.
- `SEU_DEVTO` ➔ Substitua pelo seu usuário da plataforma Dev.to.
- `SEU_INSTAGRAM` ➔ Substitua pelo seu usuário do Instagram.
- `SEU_PORTFOLIO.com` ➔ Substitua pela URL do seu portfólio pessoal.
- `Seu Nome Aqui` ➔ Substitua pelo seu nome real ou apelido no bloco JSON.

---

## 3. Configurar a Integração de Artigos do dev.to
Para atualizar seus posts do dev.to de forma 100% automática no seu perfil, siga estas instruções:

1. No repositório do seu perfil no GitHub, crie uma pasta chamada `.github` e, dentro dela, uma pasta chamada `workflows` (caminho: `.github/workflows/`).
2. Crie um arquivo chamado `blog-posts.yml` dentro de `.github/workflows/`.
3. Cole o seguinte código de GitHub Action dentro dele:

```yaml
name: Latest dev.to blog posts
on:
  schedule:
    # Roda a cada 1 hora para buscar novos artigos
    - cron: '0 * * * *'
  workflow_dispatch: # Permite rodar manualmente

jobs:
  update-readme-with-blog:
    name: Update this readme with latest blog posts
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: gautamkrishnar/blog-post-workflow@master
        with:
          comment_tag_name: "devto"
          feed_list: "https://dev.to/feed/SEU_USUARIO_DEVTO"
```
*Lembre-se de substituir `SEU_USUARIO_DEVTO` pelo seu usuário do dev.to na última linha.*

4. Salve e comente as alterações. A partir de agora, a Action irá rodar a cada hora (ou quando você iniciar manualmente na aba **Actions** do GitHub) e atualizará a seção `<!-- START_SECTION:devto -->` no seu `README.md`.

---

## 4. Configurar o Widget do Spotify (Opcional)
O widget exibe em tempo real o que você está ouvindo no Spotify. Para configurá-lo:

1. Acesse o site oficial do gerador: [spotify-github-profile](https://spotify-github-profile.vercel.app/).
2. Faça login com a sua conta do Spotify para obter o seu ID exclusivo (`uid`).
3. No seu `README.md`, procure pela linha:
   `https://spotify-github-profile.vercel.app/api/view?uid=SEU_ID_DO_SPOTIFY&cover_image=true&theme=novatorem`
4. Substitua `SEU_ID_DO_SPOTIFY` (nos dois lugares que aparece nessa seção) pelo seu ID numérico obtido no login.

---

## 5. Salvar e Publicar
Depois de fazer todas as alterações, faça o commit do seu `README.md`, do arquivo `INSTRUCOES.md` (opcional) e da pasta `assets` contendo a imagem do banner.

Seu perfil do GitHub estará online com um visual cyberpunk premium e dinâmico! 🚀
