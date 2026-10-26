# VectrClean Studio — Pacote Pronto para Deploy no Railway

Este pacote já está 100% configurado para deploy imediato no [Railway](https://railway.com/) (via **Railway CLI** ou **GitHub**), incluindo:
- `public/index.html`: Aplicação completa do **VectrClean Studio** (Editor Vetorial Clean-Room, Painel `?target=myDesigns` e Especificação REA).
- `server.js`: Servidor HTTP Node.js zero-dependências otimizado com compressão Gzip, bind em `0.0.0.0:${PORT}` e endpoint `/health` para o healthcheck do Railway.
- `Dockerfile`: Imagem `node:20-alpine` enxuta para build automático e determinístico no Railway.
- `railway.json` e `.railway/railway.ts`: Configuração de build, start command e healthcheck (`/health`).
- `src/`: Módulos TypeScript da arquitetura (`SceneGraph.ts`, `Matrix2D.ts`, `PenTool.ts`, `BooleanEngine.ts`, `SnapEngine.ts`, `CommandHistory.ts`, `SVGSerializer.ts`).

---

## Opção 1: Deploy Direto pelo Terminal (Mais Rápido — Sem precisar criar repositório)

1. Extraia este arquivo `vectr-railway-deploy.zip` em uma pasta no seu computador e abra o terminal nela.
2. Instale a CLI oficial do Railway (caso ainda não tenha):
   ```bash
   npm install -g @railway/cli
   ```
3. Faça login na sua conta Railway:
   ```bash
   railway login
   ```
4. Crie/vincule o projeto e envie os arquivos direto para produção:
   ```bash
   railway init
   railway up
   ```
5. Gere o domínio público HTTPS (`*.up.railway.app`):
   ```bash
   railway domain
   ```

---

## Opção 2: Deploy via GitHub no Painel Web do Railway

1. Suba os arquivos desta pasta para um repositório no seu GitHub:
   ```bash
   git init
   git add .
   git commit -m "feat: VectrClean Studio ready for Railway"
   git branch -M main
   git remote add origin https://github.com/SEU_USUARIO/vectr-cleanroom-studio.git
   git push -u origin main
   ```
2. Acesse [railway.com/new](https://railway.com/new) e clique em **Deploy from GitHub repo**.
3. Selecione o repositório `vectr-cleanroom-studio` — o Railway detectará automaticamente o `Dockerfile` e o `railway.json`, fará o build e deixará o app online com certificado SSL automático.
