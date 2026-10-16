# 🎬 MovieCity — Landing Page

Landing page responsiva de um serviço de streaming fictício, construída com **React + Vite** e estilizada com **CSS puro**.

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)
![CSS](https://img.shields.io/badge/CSS-puro-1572B6?logo=css3&logoColor=white)

---

## 📖 Sobre o projeto

O **MovieCity** é um exercício prático de:

- **componentização** com React;
- **estilização com CSS puro**, sem bibliotecas de UI (Bootstrap, Tailwind, styled-components);
- **adaptação de layout** para diferentes tamanhos de tela (design responsivo).

A página é dividida em duas áreas principais:

- **Header (cabeçalho):** logo "MovieCity", menu de navegação (Filmes, Categoria, Sobre, Contato) e botão de **Login**.
- **Main (conteúdo principal):** uma coluna com o texto de chamada ("Seus Filmes") e o botão **Mais**, e outra coluna com um **grid de 6 cards** de filmes (Afterlife, Transformers, Mowgli, Shift, Round 6 e Harry Potter).

Em telas pequenas, as colunas se empilham, o grid de cards passa a ter 2 colunas e o menu de navegação vira um **menu hambúrguer** que abre e fecha.

---

## 🎓 Contexto das aulas

Este projeto faz parte do nosso aprendizado. **Também utilizamos React em nossas aulas**, e o MovieCity serve para colocar em prática os conceitos vistos em sala, como:

- criação e organização de **componentes** (`Home`, `Header`, `Main`);
- uso de **estado** com o hook `useState` (abrir/fechar o menu);
- renderização de listas com `.map()`;
- uso de `className` e importação de CSS global;
- ambiente de desenvolvimento com **Vite** (HMR, build e preview).

---

## 🧰 Tecnologias

| Tecnologia       | Para que serve                                         |
| ---------------- | ------------------------------------------------------ |
| React 19         | Biblioteca de UI baseada em componentes                |
| Vite 7           | Servidor de desenvolvimento com HMR e bundler          |
| JavaScript (ESM) | Linguagem e sistema de módulos                         |
| CSS puro         | Estilização global e responsividade (media queries)    |
| ESLint           | Padronização e análise estática do código              |

---

## ✅ Pré-requisitos

- [Node.js](https://nodejs.org/) **20.19+** ou **22.12+** (exigido pelo Vite 7)
- npm (já vem com o Node.js) — ou yarn/pnpm
- Um editor de código, como o VS Code

Confira as versões instaladas:

```bash
node -v
npm -v
```

---

## 🚀 Como executar

```bash
# 1. Clone o repositório
git clone <url-do-repositorio>

# 2. Entre na pasta do projeto
cd 01_landinpage

# 3. Instale as dependências
npm install

# 4. Inicie o servidor de desenvolvimento
npm run dev
```

O Vite abrirá em **http://localhost:5173**. A cada alteração salva, a página atualiza sozinha (HMR).

### Scripts disponíveis

| Comando           | Descrição                                              |
| ----------------- | ------------------------------------------------------ |
| `npm run dev`     | Inicia o servidor de desenvolvimento em `localhost:5173` |
| `npm run build`   | Gera a versão otimizada de produção em `dist/`         |
| `npm run preview` | Serve localmente o build de `dist/` para conferência   |
| `npm run lint`    | Roda o ESLint em todo o projeto                        |

---

## 📁 Estrutura de pastas

```
01_landinpage/
├── public/
│   └── vite.svg            # favicon
├── src/
│   ├── assets/             # imagens dos pôsteres
│   ├── components/
│   │   ├── Header.jsx      # cabeçalho + menu hambúrguer
│   │   ├── Main.jsx        # texto de chamada + grid de filmes
│   │   └── Home.jsx        # container da página
│   ├── App.jsx             # renderiza <Home />
│   ├── index.css           # estilos globais + responsividade
│   └── main.jsx            # ponto de entrada do React
├── index.html              # HTML raiz
├── eslint.config.js
├── package.json
└── vite.config.js
```

### Como as partes se conectam

```
index.html → main.jsx → App.jsx → Home.jsx ─┬─→ Header.jsx
                                            └─→ Main.jsx
```

1. `index.html` contém apenas a `<div id="root">` e o script de entrada.
2. `main.jsx` usa `createRoot()` para renderizar o `<App />`.
3. `App.jsx` importa o CSS global e renderiza `<Home />`.
4. `Home.jsx` monta `<Header />` e `<Main />`.
5. Os componentes usam `className`, e todo o visual vem de `src/index.css`.

---

## 📱 Responsividade

O layout usa quatro breakpoints:

| Breakpoint          | Alvo                          | O que muda                                                    |
| ------------------- | ----------------------------- | ------------------------------------------------------------- |
| `max-width: 1100px` | Tablets em paisagem           | Espaçamentos, gaps e tipografia menores                       |
| `max-width: 900px`  | Tablets retrato / celulares grandes | Colunas empilham, texto centralizado, menu hambúrguer aparece |
| `max-width: 600px`  | Celulares                     | Grid de cards com 2 colunas, fontes e paddings reduzidos      |
| `max-width: 380px`  | Celulares pequenos            | Ajustes finos de fonte e altura dos cards                     |

**Técnicas utilizadas:**

- Unidades relativas (`%`, `minmax(0, 1fr)`, `max-height`) em vez de larguras fixas;
- **Flexbox** para as colunas do `main` e o alinhamento do `header`;
- **CSS Grid** com `minmax(0, 1fr)` para os cards;
- Menu hambúrguer feito só com CSS, animado via `max-height`;
- `min-height: 100vh` no `.home`, para o conteúdo crescer sem ser cortado;
- **Acessibilidade:** o botão do menu tem `aria-label` e `aria-expanded`, e o menu fecha ao clicar em qualquer link.

Para testar: `F12` → `Ctrl + Shift + M` → teste em 1440px, 1024px, 768px, 600px e 375px.

---

## 💡 Próximos passos

- [ ] Trocar os `div` dos cards por `<button>` (acessibilidade e teclado);
- [ ] Adicionar título e nota a cada filme;
- [ ] Buscar a lista de filmes em uma API (ex.: [TMDB](https://www.themoviedb.org/)) e renderizar com `.map()`;
- [ ] Transformar os cards em carrossel horizontal no mobile;
- [ ] Adicionar `prefers-reduced-motion` para reduzir animações;
- [ ] Migrar o CSS para CSS Modules conforme o projeto crescer.

---

## 👥 Autoria

Projeto desenvolvido para fins educacionais, como parte das nossas aulas de React.

<!-- Feito no Senai Jacob Lafer / Sala 2IGDS / Professor Denis -->
