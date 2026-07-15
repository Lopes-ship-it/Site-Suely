# Suely da Guarda Spazio — Site (Vite)

Site institucional do salão **Suely da Guarda Spazio**, agora estruturado como projeto **Vite** (HTML/CSS/JS puro, sem framework de UI).

## Estrutura

```
suely-da-guarda-vite-project/
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
cd suely-da-guarda-vite-project
npm install
npm run dev
```

Isso abre o site em `http://localhost:5173` com hot-reload — qualquer alteração no `index.html` atualiza o navegador automaticamente.

## Gerando o build de produção

```bash
npm run build
```

Isso cria a pasta `dist/` com o site otimizado, pronto para hospedar em qualquer lugar. Para conferir o resultado localmente antes de publicar:

```bash
npm run preview
```

## Como subir no GitHub

```bash
cd suely-da-guarda-vite-project
git init
git add .
git commit -m "Site Suely da Guarda Spazio (Vite)"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/NOME-DO-REPO.git
git push -u origin main
```

> `node_modules/` e `dist/` já estão no `.gitignore` — não sobem para o repositório, o Vercel gera o build dele automaticamente.

## Como publicar no Vercel

**Opção A — pelo site do Vercel (recomendado):**
1. Acesse [vercel.com](https://vercel.com) e faça login (pode usar sua conta do GitHub).
2. Clique em **Add New → Project**.
3. Selecione o repositório que você criou no GitHub.
4. O Vercel detecta automaticamente o framework **Vite** (graças ao `vercel.json` e ao `package.json`) e já preenche build command (`npm run build`) e output directory (`dist`) sozinho.
5. Clique em **Deploy**.

Em cerca de 1 minuto o Vercel gera uma URL pública (algo como `suely-da-guarda-spazio.vercel.app`). Depois é possível conectar um domínio próprio nas configurações do projeto.

**Opção B — pelo terminal (Vercel CLI):**
```bash
npm i -g vercel
cd suely-da-guarda-vite-project
vercel
```
Siga as instruções no terminal (login, nome do projeto, confirmar diretório). Depois, para colocar em produção:
```bash
vercel --prod
```

## Atualizações futuras

Qualquer alteração no `index.html` ou nas imagens em `public/images/`: basta commitar e dar `git push` — o Vercel builda e publica automaticamente uma nova versão a cada push na branch `main`.

## Observação

Este projeto foi validado localmente: `npm install` + `npm run build` rodaram sem erros e o `dist/index.html` gerado carrega todas as imagens corretamente a partir de `/images/`.
