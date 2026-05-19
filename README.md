# Contas a Pagar — PWA

App de controle de contas a pagar com lembretes push. Funciona como app nativo no iPhone e Mac (Progressive Web App).

## Estrutura

- `index.html` — o app
- `manifest.json` — metadados para instalação
- `service-worker.js` — cache offline + push
- `icons/` — ícones para iOS, Android e Mac

## Como instalar no iPhone

1. Abra a URL do app no **Safari** (não funciona em outros navegadores no iPhone)
2. Toque no botão **Compartilhar** (□ com seta pra cima)
3. Role e toque em **"Adicionar à Tela de Início"**
4. Confirme o nome e toque em **Adicionar**
5. O ícone aparece na tela de início como um app nativo
6. Abra o app, vá em 🔔 → **Solicitar permissão** e autorize as notificações

## Como instalar no Mac

1. Abra a URL no **Safari**
2. Menu **Arquivo → Adicionar ao Dock...**
3. Confirme o nome e clique em **Adicionar**
4. O app aparece no Dock e pode ser aberto como um app nativo

(No Chrome no Mac: ícone de instalação aparece na barra de endereço, ou Menu → Transmitir, salvar e compartilhar → Instalar como app)

## Como hospedar (GitHub Pages — grátis)

1. Crie conta em [github.com](https://github.com)
2. Clique em **+ → New repository** (nome qualquer, ex: `contas-a-pagar`)
3. Marque **Public**
4. Faça upload dos arquivos desta pasta (`index.html`, `manifest.json`, `service-worker.js`, pasta `icons/`)
5. Vá em **Settings → Pages**
6. Em **Source**, escolha **Deploy from branch → main → / (root)** → Save
7. Aguarde 1-2 minutos. Acesse `https://SEU_USUARIO.github.io/contas-a-pagar/`
8. Abra essa URL no Safari do iPhone e siga os passos de instalação acima

## Sobre as notificações push

Como esta é uma PWA (não um app nativo de App Store), as notificações funcionam assim:

- **App aberto/em primeiro plano**: notificações disparam normalmente no horário configurado
- **App recém-fechado (alguns minutos)**: iOS pode ainda manter o service worker rodando
- **App fechado por muito tempo**: iOS suspende. Quando você abrir o app de novo, ele mostra um aviso "catch-up" com contas vencidas/do dia

Para pushes 100% confiáveis com app fechado por dias, seria necessário um servidor backend usando APNs — fora do escopo desta versão.

## Privacidade

Todos os dados ficam armazenados localmente no seu dispositivo (localStorage). Nada é enviado para servidores externos.
