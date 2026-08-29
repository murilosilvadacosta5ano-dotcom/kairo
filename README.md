# Kairo — by Sakaruke

Assistente de IA com interface completa inspirada em Claude / Grok / ChatGPT.

## Como usar

1. Abra `index.html` no navegador (ou sirva com qualquer servidor estático).
2. Clique em qualquer botão de login → entra no app (demo).
3. Converse, mude configurações, tema, modelo, etc.

## Integração real

### 1. Google Auth (e outros)
No arquivo `js/app.js`, função `login(provider)`:

```js
function login(provider) {
  // Substitua por sua lógica real (Firebase Auth, NextAuth, etc.)
  // Exemplo Firebase:
  // const provider = new GoogleAuthProvider();
  // signInWithPopup(auth, provider).then(...)
}
```

### 2. API da IA
Substitua a função `generateReply(userText)` pela chamada à sua API:

```js
async function generateReply(userText) {
  const res = await fetch('https://sua-api.com/chat', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer SEU_TOKEN'
    },
    body: JSON.stringify({
      model: state.model,
      messages: currentMessages(),
      mode: state.mode
    })
  });
  const data = await res.json();
  return data.reply;
}
```

Lembre de tornar `sendMessage` async e usar `await generateReply(...)`.

### 3. Conectores
Na tela de Conectores (já existe a UI). Adicione seus handlers de OAuth / API keys nos botões correspondentes.

### 4. Anexos (câmera / fotos / arquivos)
Os botões no modal de anexos já disparam eventos. Conecte `input[type=file]` ou MediaDevices conforme necessário.

## Estrutura

```
kairo/
├── index.html
├── css/styles.css
├── js/app.js
└── README.md
```

## Recursos já funcionais no frontend

- Login (demo)
- Histórico de conversas (localStorage)
- Busca de chats
- Tema claro / escuro / sistema
- Seletor de modelo
- Modo Rápido / Raciocínio / Criativo
- Configurações completas (voz, idioma, modo infantil, conteúdo adulto, etc.)
- Modal de anexos
- Exportar / limpar conversas
- Design responsivo (mobile + desktop)
- Interface 100% em português

Feito com ❤️ pelo estúdio **Sakaruke**.
