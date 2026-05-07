# 📋 Tarefas do Otávio — Guia de Configuração

Sistema de acompanhamento de tarefas com remuneração.  
App mobile para o Otávio + Painel web para o pai.

---

## 📁 Arquivos do projeto

| Arquivo | Descrição |
|---|---|
| `index.html` | App do Otávio (mobile) |
| `painel.html` | Painel do pai (desktop) |
| `config.js` | URL do Apps Script (você vai preencher) |
| `codigo-apps-script.gs` | Código do servidor Google |

---

## PASSO 1 — Configurar o Google Drive

1. Acesse o [Google Drive](https://drive.google.com)
2. Crie uma pasta chamada **"Tarefas Otávio"**
3. Dentro dela, crie outra pasta chamada **"Fotos"**
4. Crie uma **planilha do Google Sheets** dentro de "Tarefas Otávio" — pode chamar de **"Dados"**

**Copie os IDs:**
- Abra a pasta "Fotos" → copie o ID da URL: `drive.google.com/drive/folders/**SEU_ID_AQUI**`
- Abra a planilha "Dados" → copie o ID da URL: `docs.google.com/spreadsheets/d/**SEU_ID_AQUI**/edit`

---

## PASSO 2 — Configurar o Apps Script

1. Na planilha "Dados", clique em **Extensões > Apps Script**
2. Apague o código que estiver lá
3. Cole todo o conteúdo do arquivo `codigo-apps-script.gs`
4. No topo do código, substitua:
   - `COLE_AQUI_O_ID_DA_PLANILHA` → pelo ID da planilha "Dados"
   - `COLE_AQUI_O_ID_DA_PASTA_FOTOS` → pelo ID da pasta "Fotos"
5. Salve (Ctrl+S)
6. **Teste:** selecione a função `testar` e clique em ▶ Executar
   - Se aparecer "Tudo OK!" no log, funcionou!
   - Se pedir permissão, clique em "Autorizar acesso" e confirme

---

## PASSO 3 — Publicar o Apps Script como Web App

1. Ainda no editor do Apps Script, clique em **Implantar > Nova implantação**
2. Clique no ⚙️ ao lado de "Tipo" e selecione **"App da Web"**
3. Configure assim:
   - **Descrição:** Tarefas Otávio
   - **Executar como:** Eu (seu e-mail)
   - **Quem tem acesso:** Qualquer pessoa
4. Clique em **Implantar**
5. Autorize quando pedir
6. **Copie a URL** que aparecer — parece com: `https://script.google.com/macros/s/AKfycb.../exec`

---

## PASSO 4 — Configurar o arquivo config.js

Abra o arquivo `config.js` e cole a URL copiada:

```javascript
const APPS_SCRIPT_URL = 'https://script.google.com/macros/s/SUA_URL_AQUI/exec';
```

---

## PASSO 5 — Publicar no GitHub Pages

1. Crie um repositório no GitHub (pode ser privado ou público)
   - Sugestão de nome: `tarefas-octavio`
2. Faça upload de todos os 4 arquivos:
   - `index.html`
   - `painel.html`
   - `config.js`
   - (o `.gs` não precisa, é só pra referência)
3. Vá em **Settings > Pages**
4. Em "Source", selecione **main branch / root**
5. Salve — o GitHub vai gerar o link em alguns minutos

**Links finais:**
- App do Otávio: `https://SEU_USUARIO.github.io/tarefas-octavio/`
- Painel do pai: `https://SEU_USUARIO.github.io/tarefas-octavio/painel.html`

---

## 📱 Como o Otávio usa

1. Abre o link no celular
2. Vê as tarefas do dia
3. Para tarefas com 📷: toca em "Enviar foto" e tira a foto na hora
4. Para tarefas sem foto: toca em "Marcar como feito"
5. Se estiver no vô: toca em "✈️ Fora" para pular a tarefa sem penalidade

---

## 💡 Manutenção

**Limpar fotos antigas (a cada 2 meses):**
- Acesse Google Drive > Tarefas Otávio > Fotos
- As fotos ficam organizadas em subpastas por mês (ex: `2025-05`)
- Apague as pastas antigas que quiser

**Alterar valores ou tarefas:**
- Edite o arquivo `index.html` e `painel.html`
- Busque por `TAREFAS_DEF` e edite a lista
- Faça upload dos arquivos atualizados no GitHub

---

## 🆘 Problemas comuns

| Problema | Solução |
|---|---|
| Foto não sobe | Verifique se a URL do Apps Script está correta no `config.js` |
| Apps Script pede permissão | Autorize normalmente — é seu próprio código |
| Dados não aparecem no painel | O painel usa `localStorage` do navegador — abra no mesmo dispositivo que o Otávio usa |
| GitHub Pages não abre | Aguarde alguns minutos após ativar |
