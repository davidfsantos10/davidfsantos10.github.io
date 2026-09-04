# Site do Gerador de Release

Site institucional para divulgar e disponibilizar o download do app **Gerador de Release** (Android e iPhone), com passo a passo de uso, instruções de instalação e espaços preparados para anúncios (monetização).

Este guia foi escrito para quem **nunca publicou um site antes** — siga na ordem.

---

## 1. O que tem em cada arquivo

```
projeto-release/
├── index.html          → Página principal (site inteiro)
├── privacidade.html     → Política de Privacidade (obrigatória para anúncios)
├── assets/
│   ├── css/style.css    → Todo o visual do site
│   ├── js/main.js       → Menu mobile, abas Android/iPhone, FAQ
│   └── img/             → (vazio) coloque aqui screenshots/ícone reais do app
└── README.md            → Este guia
```

Não existe "banco de dados" nem servidor: é um site **estático** (só HTML/CSS/JS). Isso significa que ele é grátis e simples de hospedar.

---

## 2. Ver o site no seu computador (antes de publicar)

1. Baixe/atualize os arquivos deste repositório no seu computador.
2. Dê **duplo clique** no arquivo `index.html`. Ele abre no seu navegador normalmente.
3. Navegue pelo site, teste o menu, as abas de instalação e o FAQ.

Isso é só para conferir visualmente — ainda não está "no ar" para outras pessoas acessarem.

---

## 3. Publicar de graça com GitHub Pages (recomendado)

Como o projeto já está no GitHub, a forma mais simples e **100% gratuita** de publicar é o **GitHub Pages**.

### Passo a passo

1. Acesse o repositório no site do GitHub (`davidfsantos10/projeto-release`).
2. Garanta que os arquivos deste site estejam na branch principal (`main`). Se você estiver revisando numa outra branch (ex.: `claude/release-generator-website-1jbiqe`), primeiro abra um Pull Request e faça o merge para a `main`.
3. No repositório, clique em **Settings** (Configurações).
4. No menu lateral, clique em **Pages**.
5. Em **Source**, selecione a branch `main` e a pasta `/ (root)`.
6. Clique em **Save**.
7. Aguarde 1–2 minutos. O GitHub vai mostrar o endereço do seu site, algo como:
   `https://davidfsantos10.github.io/projeto-release/`
8. Pronto! Esse é o link que você pode compartilhar.

Sempre que você (ou o Claude) fizer uma alteração e enviar (`push`) para a branch `main`, o site atualiza sozinho em 1–2 minutos.

### Quero um domínio próprio (ex: geradorderelease.com.br)

1. Compre um domínio em um registrador, por exemplo:
   - [registro.br](https://registro.br) — para domínios `.com.br` (mais barato para brasileiros);
   - Namecheap, GoDaddy, Google Domains — para domínios `.com`, `.app`, etc.
2. No painel do domínio, procure por **DNS** e crie os registros que o GitHub Pages pede (documentação oficial: *GitHub Pages → Managing a custom domain*). Em resumo:
   - Um registro **CNAME** apontando `www` para `davidfsantos10.github.io`;
   - Registros **A** apontando o domínio raiz para os IPs do GitHub Pages (185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153).
3. No repositório, em **Settings → Pages → Custom domain**, digite seu domínio e salve.
4. Aguarde a propagação (pode levar de alguns minutos a 24h).

*Isso é totalmente opcional — o link gratuito do GitHub Pages já funciona perfeitamente para divulgar o app.*

---

## 4. Como monetizar com anúncios (Google AdSense)

O jeito mais comum e confiável de colocar anúncios em um site é o **Google AdSense**. Passo a passo:

### 4.1 Antes de se cadastrar

- O site **precisa estar no ar** (publicado, com um link acessível — veja o passo 3).
- É **obrigatório** ter uma Política de Privacidade publicada — já deixei pronta em `privacidade.html`, mas **revise o conteúdo** (está marcado como "[MODELO]") antes de divulgar, principalmente as seções sobre quais dados o app realmente coleta.
- E-mail de contato já configurado: `davidpmfsantos@gmail.com` (rodapé, FAQ e política de privacidade).

### 4.2 Cadastro

1. Acesse [adsense.google.com](https://adsense.google.com) e clique em **Comecar**.
2. Informe o link do seu site (o do GitHub Pages ou seu domínio próprio) e seu e-mail.
3. O Google vai te dar um trecho de código parecido com este:
   ```html
   <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXX" crossorigin="anonymous"></script>
   ```
4. Cole esse código dentro da tag `<head>` do arquivo `index.html` (já deixei um comentário `GOOGLE ADSENSE` marcando exatamente onde) e de `privacidade.html`.
5. Envie o site para análise. A aprovação pode levar de alguns dias a algumas semanas. O Google vai revisar se o conteúdo está de acordo com as políticas deles (conteúdo original, política de privacidade, navegação funcionando, etc.).

### 4.3 Depois de aprovado: colocar os blocos de anúncio

No site já existem **3 espaços reservados** para anúncios, marcados assim no `index.html`:

```html
<div class="ad-slot ad-slot--section">
  <div class="ad-inner">
    <!-- ESPAÇO DE ANÚNCIO — troque este bloco pelo <ins class="adsbygoogle">...</ins> do AdSense. -->
    Espaço reservado para anúncio (banner responsivo)
  </div>
</div>
```

Para cada um desses blocos:

1. No painel do AdSense, crie um **novo bloco de anúncios** ("Anúncios de display", responsivo).
2. O Google vai te dar um código parecido com:
   ```html
   <ins class="adsbygoogle"
        style="display:block"
        data-ad-client="ca-pub-XXXXXXXXXXXXXXX"
        data-ad-slot="XXXXXXXXXX"
        data-ad-format="auto"
        data-full-width-responsive="true"></ins>
   <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
   ```
3. Substitua o `<div class="ad-inner">...</div>` inteiro por esse código.
4. Repita para os outros dois espaços de anúncio.
5. Publique a alteração (commit + push) e aguarde os anúncios começarem a aparecer (pode levar algumas horas).

> **Dica:** não clique nos próprios anúncios para "testar" — o Google pode banir sua conta por cliques inválidos. Use a ferramenta de pré-visualização do próprio AdSense.

---

## 5. Links de download

Todos os botões "Baixar para Android" / "Baixar para iPhone" do site (no topo, na seção de instalação e na seção final) já apontam para as páginas de instalação reais:

- **Android:** `https://gerador-de-release.netlify.app/android.html`
- **iPhone:** `https://gerador-de-release.netlify.app/ios.html`

Os botões abrem essas páginas em uma nova aba (`target="_blank"`), já que elas ficam em outro domínio (Netlify).

Se um dia o app for publicado também na Google Play ou na App Store, procure por `href="https://gerador-de-release.netlify.app/..."` no `index.html` (aparece 6 vezes) e troque pelo link da loja, no formato:

- **Google Play:** `https://play.google.com/store/apps/details?id=com.seudominio.geradorderelease`
- **App Store:** `https://apps.apple.com/br/app/nome-do-app/idXXXXXXXXXX`
- **TestFlight (beta):** `https://testflight.apple.com/join/XXXXXXXX`

Também existem 3 outros lugares com botões "Baixar" (no menu, no topo/hero e na seção de instalação) — todos apontam para `#download`, que rola até a seção final. Você só precisa atualizar os 2 links reais dentro da `download-cta` (seção "Pronto para agilizar seus releases?").

### Sobre os QR Codes

Os quadrados com texto "QR Code de download" em `#instalacao` são só placeholders visuais. Quando tiver os links reais, gere os QR Codes de graça em [qrcode-monkey.com](https://www.qr-code-generator.com/) ou similar, baixe a imagem e substitua o `<div class="qr-box">...</div>` por uma tag `<img src="assets/img/qr-android.png" alt="QR Code Android">` (o mesmo para o iPhone).

### Sobre as imagens/ícone

A pasta `assets/img/` está vazia — o site usa um "mockup" de telefone feito só em HTML/CSS (sem imagem real) e um ícone simples com a letra "R". Quando tiver o ícone e screenshots reais do app, é só:
1. Colocar os arquivos em `assets/img/`;
2. Trocar o favicon (procure `<link rel="icon"` nos dois arquivos HTML) e a `brand-mark` pelo ícone real, se quiser;
3. Opcionalmente, trocar o `.phone-mock` do topo por um `<img>` com um screenshot real do app.

---

## 6. Checklist antes de divulgar o site de verdade

- [ ] Revisar o texto da `privacidade.html` (está marcado como "[MODELO]") com atenção especial à seção "Quais dados coletamos" — descreva exatamente o que o app faz com os dados preenchidos.
- [x] E-mail de contato atualizado (`davidpmfsantos@gmail.com`) em `index.html` e `privacidade.html`.
- [x] Links de download apontando para as páginas de instalação (Netlify) — trocar pelas lojas oficiais quando/se publicar lá.
- [ ] Publicar o site (GitHub Pages — passo 3).
- [ ] Cadastrar no Google AdSense e aguardar aprovação (passo 4).
- [ ] Colar os blocos de anúncio depois da aprovação.
- [ ] (Opcional) Configurar domínio próprio.
- [ ] (Opcional) Gerar e colocar os QR Codes reais.

---

## 7. Manutenção do dia a dia

- Qualquer alteração de texto é feita direto nos arquivos `.html` (procure o texto que quer mudar e edite).
- Cores, fontes e espaçamentos ficam todos em `assets/css/style.css`, no topo, dentro de `:root { ... }`.
- Depois de qualquer alteração: salve, faça `git add`, `git commit` e `git push` para a branch `main` — o GitHub Pages atualiza sozinho.

Se tiver dúvida em qualquer passo, pode pedir para o Claude te ajudar de novo — é só descrever o que está tentando fazer (ex.: "não sei como configurar o DNS do meu domínio" ou "quero trocar a cor do botão verde").
