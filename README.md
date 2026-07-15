# Suely da Guarda Spazio — Site (Vite)

Site institucional do salão **Suely da Guarda Spazio**, estruturado como projeto **Vite** (HTML/CSS/JS puro, sem framework de UI).

## Estrutura

```
suely-da-guarda-vite-v2/
├── index.html          → página do site (entrada do Vite)
├── public/
│   └── images/          → fotos e logo (copiadas como estão para o build)
├── package.json
├── package-lock.json
├── vite.config.js
├── vercel.json          → configuração de deploy (framework: vite)
└── README.md
```

## Antes de publicar

Abra o `index.html` e procure por `COLE_AQUI_O_LINK_DO_WHATSAPP` (aparece 2 vezes: botão flutuante e seção de contato) e substitua pelo link real, por exemplo:

```
https://wa.me/5538999999999
```

## Rodando localmente

Pré-requisito: [Node.js](https://nodejs.org) instalado (versão 18 ou superior).

```bash
cd suely-da-guarda-vite-v2
npm install
npm run dev
```

Isso abre o site em `http://localhost:5173` com hot-reload.

Se quiser só visualizar rápido sem instalar nada, também dá pra abrir o `index.html` direto no navegador (duplo clique) — as imagens usam caminhos relativos, então funcionam mesmo sem servidor.

## Gerando o build de produção

```bash
npm run build
```

Isso cria a pasta `dist/` com o site otimizado. Para conferir antes de publicar:

```bash
npm run preview
```

## Como subir no GitHub

```bash
cd suely-da-guarda-vite-v2
git init
git add .
git commit -m "Site Suely da Guarda Spazio (Vite)"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/NOME-DO-REPO.git
git push -u origin main
```

> `node_modules/` e `dist/` estão no `.gitignore` — o Vercel gera o build sozinho.

## Como publicar no Vercel

1. Acesse [vercel.com](https://vercel.com) e faça login.
2. **Add New → Project** e selecione o repositório do GitHub.
3. O Vercel detecta o framework **Vite** automaticamente (via `vercel.json`) e preenche build command e output directory sozinho.
4. Clique em **Deploy**.

**Pelo terminal (Vercel CLI):**
```bash
npm i -g vercel
cd suely-da-guarda-vite-v2
vercel        # preview
vercel --prod # produção
```

## O que foi corrigido nesta versão

As imagens estavam com caminho absoluto (`/images/...`), o que funciona no Vercel mas quebra se alguém tentar abrir o `index.html` direto no navegador (sem servidor) — o navegador procura a pasta `images` na raiz do computador, não na pasta do projeto. Agora os caminhos são relativos (`images/...`), então funcionam em qualquer cenário: abrindo o arquivo direto, rodando `npm run dev`, ou publicado no Vercel. Testado localmente com `npm install` + `npm run build` — build gera `dist/index.html` e `dist/images/` lado a lado, sem imagem quebrada.
