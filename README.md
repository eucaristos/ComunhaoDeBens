# Comunhão de Bens Eucaristós

Formulário web para registro de contribuições mensais da Comunidade Eucaristós. Os dados são enviados automaticamente para uma planilha do Google Sheets via webhook.

---

## 🗂 Estrutura do projeto
```
comunhao-bens/
├── index.html       # Página principal com formulário
├── images/
│   ├── lg.jpg       # Favicon / logotipo
│   └── tutorial.gif # GIF de tutorial (exibido ao clicar em play)
└── README.md
```
---

## ⚙️ Configuração

### 1. Webhook

No arquivo `index.html`, localize a variável:

```js
var WEBHOOK_URL = '**';
```

Substitua pelo endpoint do seu webhook (ex: Make, Zapier, Google Apps Script Web App).

### 2. Google Sheets — Formatação de moeda

Para exibir os valores recebidos no formato `R$ #.##0,00`, acesse **Extensões → Apps Script** na planilha e cole:

```js
function formatarMoeda() {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  sheet.getRange("C2:F1000").setNumberFormat('R$ #.##0,00');
}
```

Execute uma vez. As colunas C–F passarão a exibir os valores como moeda brasileira.

---

## 📋 Campos do formulário

| Campo | Descrição |
|---|---|
| Nome completo | Identificação do contribuinte |
| Comunhão de Bens | Valor do fundo principal |
| Feliz Terceiro | Valor do fundo Feliz Terceiro |
| Fundo da Providência | Valor do Fundo da Providência |
| Monte Santo | Valor do Monte Santo |

---

## 📦 Payload enviado ao webhook

```json
{
  "data": "31/03/2026",
  "nome": "Nome do contribuinte",
  "comunhao": 150.00,
  "feliz": 50.00,
  "fundo": 30.00,
  "monte": 20.00
}
```

---

## 🌐 Compatibilidade

Testado e compatível com Chrome, Firefox, Safari, Edge e navegadores móveis (iOS Safari, Chrome Android).

---

## 📁 Dependências externas

- [Work Sans](https://fonts.google.com/specimen/Work+Sans) — Google Fonts
- Sem frameworks JS ou CSS externos

---

## ✝️ Sobre

Projeto desenvolvido para o setor do Economato da Comunidade Eucaristós.  
Dúvidas: procure o setor do Economato.