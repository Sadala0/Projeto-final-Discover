# DevLinks

Página de links pessoal ("link na bio") feita com **HTML, CSS e JavaScript puros**, sem frameworks e sem dependências. Reúne em um só lugar os principais links de desenvolvedor: GitHub e LinkedIn.

## Funcionalidades

- Página simples e responsiva, que funciona bem no celular e no computador
- Botões de links com efeito ao passar o mouse
- Ícones de redes sociais em SVG, no rodapé
- Tema **claro e escuro** com switch
  - Na primeira visita segue o tema do sistema
  - A escolha fica salva no navegador (`localStorage`)
- Acessível: navegação por teclado, foco visível e `aria-label` nos ícones

## Tecnologias

- HTML5
- CSS3 (variáveis CSS para os temas)
- JavaScript (ES6+)

## Estrutura do projeto

```
devlinks/
├── index.html   # estrutura da página, links e ícones
├── style.css    # estilos e temas claro/escuro
└── script.js    # alternância e persistência do tema
```

## Como rodar

Não precisa instalar nada.

1. Baixe ou clone o projeto
2. Deixe os três arquivos na mesma pasta
3. Abra o `index.html` no navegador

Se preferir um servidor local, na pasta do projeto rode `npx serve` ou use a extensão **Live Server** do VS Code.

## Como personalizar

Edite o `index.html`:

- **Nome, usuário e bio:** dentro de `<main>`, nas tags `<h1>`, `.handle` e `.bio`
- **Links:** na lista `<ul class="links">`, altere o `href` e o texto de cada item ou adicione novos `<li>`
- **Ícones do rodapé:** dentro de `<footer>`

Edite o `style.css` para mudar as cores. Elas ficam nas variáveis dos blocos `:root[data-theme="dark"]` e `:root[data-theme="light"]`, e a cor de destaque está em `--accent`.

## Publicar online

Dá para publicar de graça no **GitHub Pages**:

1. Suba os arquivos para um repositório no GitHub
2. Vá em **Settings → Pages**
3. Em **Source**, escolha a branch `main` e a pasta `/ (root)`
4. Salve e acesse o link gerado

Também funciona na Vercel e na Netlify, arrastando a pasta do projeto.

## Autor

**Lucas Sadala**

- GitHub: [@Sadala0](https://github.com/Sadala0)
- LinkedIn: [Lucas Sadala](https://www.linkedin.com/in/lucas-sadala-7a55773b3)
