# Portfólio Letícia Garcia — Let Design

Site estático bilíngue (PT/EN). HTML + Tailwind CSS v4 via CDN.
**Sem React, sem build, sem NPM, sem instalar dependências.**

Letícia é designer gráfica e ilustradora, formada em Design pela UNESP.
Dois públicos: cliente de ilustração/identidade visual **e** recrutador de design.

## Estrutura de arquivos

```
index.html              home
projetos.html           grid completo com filtro
sobre.html              bio, experiência, clientes
projetos/_template.html template de case
projetos/[slug].html    um por projeto
assets/img/             imagens dos projetos
assets/stickers/        elementos gráficos da marca
```

## Regras

- Uma seção por vez. Não alterar seções já prontas.
- Comentário HTML separando cada seção: `<!-- ====== NOME ====== -->`
- Construir de fora para dentro (container → filhos).
- Um grid por módulo/seção, nunca um grid único para a página.
- Desktop (1440px) primeiro. Mobile (390px) depois, quando eu pedir.
- Container: `max-w-[1280px] mx-auto px-20` — no mobile, `px-5`.
- Tokens só no `@theme`. Nunca cor ou tamanho hardcoded fora dele.
- Espaçamento na escala do Tailwind (múltiplos de 4).
- Toda imagem precisa de `alt` descritivo.
- Páginas de case seguem `projetos/_template.html`.

## Bilíngue

Todo texto visível carrega os dois idiomas em atributos `data-pt` e `data-en`.
Um botão PT/EN no header troca via JS e salva a escolha. Nunca duplicar arquivo por idioma.

```html
<h2 data-pt="Trabalhos selecionados" data-en="Selected work"></h2>
```

## Marca

**Cores** (hex definitivos):

| token | hex | uso |
|---|---|---|
| `bg-creme` | `#FFF9EB` | fundo padrão |
| `text-navy` | `#1B1435` | texto e fundo escuro |
| `magenta` | `#E62070` | acento — Ilustração |
| `laranja` | `#E9571B` | acento — Design + Ilustração |
| `amarelo` | `#FBBC12` | destaque, hover, stickers |
| `roxo` | `#5E4A97` | acento — Design |

- Fundo creme, texto navy. Uma cor de acento por categoria de projeto.
- **Nunca as quatro cores de acento juntas com peso igual na mesma tela.**
- Stickers em `assets/stickers/` — no máximo 3 por seção. São tempero, não o prato.

**Tipografia:** Inter em todos os pesos.
Display = Inter Black (900) com `tracking-tighter` e `leading-none`.
Corpo = Inter Regular (400), `leading-relaxed`.

## Não fazer

- Nav em pílulas centralizadas (padrão-template).
- Grid perfeitamente simétrico em todas as seções.
- Animação que atrapalhe a leitura do trabalho.
- Duplicar arquivos por idioma.
