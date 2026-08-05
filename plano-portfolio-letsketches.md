# Plano de ação — portfólio Letícia Garcia (web + mobile)

Objetivo duplo: cliente de ilustração **e** recrutador de design.
Cases com página própria no seu site. Stack do curso: HTML + Tailwind.

---

## Parte 1 — Diagnóstico

### O que você já tem (e é mais do que parece)

**No Behance:** 12+ projetos publicados, 14.7k views, 1.123 appreciations, 357 seguidores. Clientes de peso — Melissa/Fini, Puket, Netflix (Almanaque Tudum via time), MASP, ILUMAC, dr.consulta, Sanavita, Monks. Formação UNESP. Experiência: Tractian (Junior Designer III), Raccoon, Vnew. Uma fonte autoral publicada (Block Font). Um projeto de app (Transurb).

Isso é um portfólio forte. O problema nunca foi o conteúdo — é que ele está numa plataforma que apaga sua marca.

**No Figma:** e aqui está seu maior ativo. Você já tem um **sistema visual pronto**:

- Logo "Let Design" em 5 versões de cor (magenta, laranja, amarelo, navy, roxo)
- Um set de ~9 elementos gráficos (brilhos, rabiscos, smileys, estrelas, explosões, flores, olhos, pincéis, nuvens) × 6 cores
- Gradiente magenta → laranja → roxo
- Paleta creme + navy escuro como base

Repare: as quatro referências que você mandou usam exatamente esse recurso. A Mathi usa ✶ como separador de menu. A Paula usa 👩 💌 🪁 na navegação. Você tem uma versão **autoral** disso, desenhada por você. Isso é o que vai diferenciar seu site dos três feitos em Wix/Adobe Portfolio.

### O que as referências fazem (e o que copiar)

| Site | Plataforma | O que roubar |
|---|---|---|
| **Mathi Müller** | Wix | Menu como tipografia gigante (`WORK ✶ ABOUT ✶ LET'S CHAT ✶`), não como pílulas. GIFs animados no hero. Legenda de projeto = `NOME • CLIENTE` |
| **Paula Cruz** | Adobe Portfolio | **Separação DESIGN / ILLUSTRATION no menu** — exatamente seu problema dos dois públicos. Cada item do grid traz título + ano + tags |
| **Gabriela Sakata** | Adobe Portfolio | Separa "Works / Trabalhos" de "Personal / Pessoal". Bilíngue PT/EN no próprio label |
| **Dany Caetano** | Wix | Frase-manifesto gigante como elemento gráfico. Bilíngue empilhado (EN em cima, PT embaixo) |

**Três das quatro são feitas em plataforma.** Você vai codar — e é aí que está sua vantagem: hover animado nos seus stickers, cursor customizado, transições entre projetos. Coisas que Wix e Adobe Portfolio limitam.

**Padrão comum às quatro:** 4 a 6 seções na home, tipografia grande usada como elemento gráfico, grid propositalmente irregular, contato explícito e fácil, categorias declaradas como texto.

### Por que seu hero não funcionou

Você disse que é layout/composição. Concordo — e dá pra nomear o que está acontecendo:

**1. Tudo tem o mesmo peso.** Foto, "Olá!", parágrafo, ícones sociais e as 3 miniaturas ocupam áreas parecidas. Sem um elemento dominante, o olho não sabe onde pousar. Nas quatro referências sempre há **um** elemento que grita — a tipografia da Mathi, o manifesto da Dany.

**2. O trabalho aparece pequeno e tarde.** Suas 3 miniaturas estão embaixo, em tamanho igual, depois de um bloco de texto. Você é ilustradora: a ilustração tem que ser a primeira coisa, grande.

**3. O nav em pílulas centralizadas é o padrão-template.** É a decisão que mais faz um site parecer feito em construtor. A Mathi resolve isso com tipografia de 60px+.

**4. Falta assimetria.** Seu layout é um retângulo dividido ao meio, com um strip de 3 embaixo. Muito arrumado. Todas as referências quebram o grid de propósito.

**5. Um alerta com carinho:** a versão mobile diz *"Being Creative since 2001"*. O site da Dany Caetano diz *"BEING CREATIVE SINCE 99"*. Trocar o ano não descola o suficiente — e as duas circulam no mesmo meio. Vale achar uma frase que só você poderia dizer.

---

## Parte 2 — Arquitetura do site

```
/                       Home (página longa, 6 seções)
/projetos.html          Grid completo, com filtro Design / Ilustração
/projetos/[slug].html   Uma página por case
/sobre.html             Bio, clientes, experiência, CV
```

**Home — as 6 seções:**

1. **Hero** — nome, o que você faz, uma ilustração grande, CTA
2. **Seletor Design ↔ Ilustração** — a solução para os dois públicos. Duas portas visíveis logo de cara, em vez de um grid misturado que não serve bem para nenhum dos dois
3. **Projetos em destaque** — 6 cases, cada card com `TÍTULO · CLIENTE · ANO · TAGS` (padrão Paula Cruz)
4. **Sobre curto** — 3–4 linhas + foto + logos de clientes
5. **Serviços** — ilustração infantil, identidade visual, editorial, design de produto. Ajuda o cliente a se reconhecer
6. **Contato** — e-mail grande e clicável + redes

**Case (página de projeto):** capa → contexto em 2–3 linhas → cliente/ano/papel/entregas → processo (3–5 imagens) → resultado → próximo projeto.

Para recrutador, o bloco de **papel + processo** é o que importa. Para cliente de ilustração, é a capa. A mesma página serve os dois se a ordem estiver certa.

---

## Parte 3 — Design system

Extraia os hex exatos do seu Figma e preencha:

```css
@theme {
  /* base */
  --color-creme:   #FDF6E8;  /* confirmar */
  --color-navy:    #1E1B3A;  /* confirmar */

  /* marca */
  --color-magenta: #E91E7B;
  --color-laranja: #F26522;
  --color-amarelo: #FFC107;
  --color-roxo:    #6B4FBB;

  /* tipografia */
  --font-display: /* sua fonte de título */;
  --font-sans:    /* sua fonte de corpo */;

  /* escala */
  --text-hero:    120px;
  --text-title:    72px;
  --text-section:  48px;
}
```

**Regra de cor:** creme é o fundo, navy é o texto, as 4 cores da marca são acento e rotativas — cada categoria de projeto ganha uma. Nunca as quatro juntas na mesma tela em peso igual.

**Seus stickers** viram um componente reutilizável: `<span class="sticker">`. Use com moderação — 2 ou 3 por seção. Eles são tempero, não o prato.

---

## Parte 4 — Fases

### Fase 0 · Decisões (antes de desenhar) — ~3 dias

- [ ] **Curadoria.** Escolher 6 projetos para a home e 10–12 para o grid completo. Critério: melhor trabalho + variedade de tipo + clientes reconhecíveis. Almanaque Vampírico, Chico Quitandas, Puket, Melissa/Fini e ILUMAC são candidatos óbvios
- [ ] **Classificar** cada projeto: Design, Ilustração, ou os dois
- [ ] **Extrair os hex** das cores e definir as duas fontes
- [ ] **Escrever a copy do hero** — uma frase que resuma você. Sua bio do Behance já tem a matéria-prima: *"apaixonada por projetos para crianças — livros, padronagens, jogos"* + *"identidades visuais autênticas combinadas com ilustração vibrante"*
- [ ] **PT ou bilíngue?** Suas referências são bilíngues e você atende cliente internacional. Se for bilíngue, decida agora — muda o layout

### Fase 1 · Refazer o hero no Figma — ~4 dias

Três exercícios. Faça os três, escolha depois:

**A · Tipografia dominante (Mathi).** Seu nome ou uma frase ocupando 60% da tela em display gigante. Ilustração entra por trás ou por cima, sangrando. Nav em tipografia grande no topo, com um sticker seu como separador.

**B · Ilustração dominante.** Uma ilustração sua em tela cheia. Nome e nav pequenos, cantos opostos. Só isso. Funciona bem quando você tem uma peça muito forte.

**C · Grid quebrado (Paula).** Sem hero clássico — o site já abre no grid de projetos, com nome e nav fixos no topo. Cards de tamanhos diferentes.

**Teste dos 3 segundos:** mostre para alguém por 3 segundos e pergunte o que ela faz. Se a resposta não for "ilustração e design", o hero não passou.

### Fase 2 · Desenhar o resto (desktop 1440px) — ~1 semana

Home completa + template de case + template de listagem. Reaproveite o grid do projeto Jazz Is Dead: 1440 total, margem 80px, conteúdo 1280px, colunas de 413px com gap 21px. Você já sabe codar esse grid — economiza dias.

### Fase 3 · Mobile (390px) — ~4 dias

Não é o desktop espremido. Decisões a tomar em cada seção:

| Seção | Desktop | Mobile |
|---|---|---|
| Hero | tipografia gigante + ilustração lateral | tipografia menor, ilustração acima ou de fundo |
| Nav | horizontal, tipografia grande | menu hambúrguer ou 3 links + "menu" |
| Grid de projetos | 2–3 colunas | 1 coluna, cards mais altos |
| Case | imagem + texto lado a lado | empilhado, imagem primeiro |
| Contato | e-mail em texto grande | botão que abre o app de e-mail |

Cheque: nenhum texto abaixo de 14px, área de toque mínima de 44×44px, tipografia display não pode estourar a largura.

### Fase 4 · Código — ~2 semanas

Mesmo fluxo do projeto do curso: `CLAUDE.md` → seção por seção → salvar → conferir contra o Figma → commit.

**Ordem:** header/footer → hero → grid de projetos → seletor Design/Ilustração → sobre → contato → template de case → 1º case completo → replicar → responsivo.

**Uma decisão de stack que vale pensar agora:** com 12 páginas de case em HTML puro, você vai copiar e colar o mesmo header e footer 12 vezes. Muda uma coisa no menu, tem que mudar em 12 arquivos.

Duas saídas:

1. **Aceitar a repetição** e pedir ao Claude Code *"atualize o header em todos os arquivos de `/projetos/`"* quando precisar. Funciona bem, e é o que você acabou de aprender. **Recomendo começar assim.**
2. **Migrar para Astro** depois. Mesmo HTML e mesmo Tailwind, mas com componentes reutilizáveis. Vale quando a repetição começar a doer de verdade — e aí você já vai ter repertório.

Não trave essa decisão agora. Comece simples, migre se precisar.

### Fase 5 · Conteúdo — ~1 semana

Exportar imagens do Behance ou dos arquivos originais, otimizar (`.webp`, máx 1600px de largura, imagem de case abaixo de 300kb), escrever os textos de cada case, `alt` descritivo em tudo.

Aproveite o Claude Code: *"leia @cases/almanaque-vampirico.md e gere a página seguindo @projetos/_template.html"*.

### Fase 6 · Publicar — ~2 dias

GitHub → **Vercel** ou **Netlify** (grátis, deploy automático a cada push). Domínio próprio (`letsketches.com.br` ou `leticiagarcia.design`) por volta de R$40/ano. Depois: `<meta>` de SEO, imagem de Open Graph com sua marca, favicon com o logo Let, Google Analytics.

**O Behance continua vivo.** Ele te dá alcance e descoberta que site novo não tem. O site vira o endereço oficial; o Behance, um canal de distribuição. Linke um no outro.

---

## Parte 5 — CLAUDE.md do portfólio

```markdown
# Portfólio Letícia Garcia (Let Design)

Site estático. HTML + Tailwind CSS v4 via CDN. Sem React, sem build, sem NPM.
Ilustradora e designer gráfica. Dois públicos: cliente de ilustração e recrutador de design.

## Estrutura
index.html · projetos.html · sobre.html · projetos/[slug].html

## Regras
- Uma seção por vez. Não alterar seções prontas.
- Comentário HTML separando cada seção.
- Desktop (1440px) primeiro, mobile (390px) depois.
- Container: max-w-[1280px] mx-auto px-20 (px-5 no mobile).
- Tokens só no @theme. Nunca cor ou tamanho hardcoded fora dele.
- Toda imagem precisa de alt descritivo.
- Páginas de case seguem projetos/_template.html.

## Marca
- Fundo creme, texto navy. Magenta/laranja/amarelo/roxo são acento.
- Uma cor de acento por categoria de projeto. Nunca as quatro juntas.
- Stickers (brilho, estrela, flor, olhos, nuvem) em assets/stickers/ — máx 3 por seção.
- Tipografia display é elemento gráfico: grande, com personalidade.

## Não fazer
- Nav em pílulas centralizadas.
- Grid perfeitamente simétrico em todas as seções.
- Animação que atrapalhe a leitura do trabalho.
```

---

## Parte 6 — Cronograma

| Semana | Foco |
|---|---|
| 1 | Fase 0 + Fase 1 (curadoria, tokens, copy, 3 heros) |
| 2 | Fase 2 (design desktop completo) |
| 3 | Fase 3 (mobile) + começar código |
| 4–5 | Fase 4 (código) |
| 6 | Fase 5 (conteúdo dos cases) |
| 7 | Fase 6 (publicar) + ajustes |

**Se o tempo apertar, corte o escopo, não a qualidade:** lance com 6 cases em vez de 12. Site no ar com 6 projetos bons vale mais que site perfeito que nunca sai.

---

## Os três riscos reais

**1. Travar no design e nunca chegar no código.** É o mais provável. Marque uma data de "congelamento do Figma" — depois dela, só codar. Ajuste fino depois, no navegador.

**2. Perfeccionismo nos cases.** 12 cases bem escritos é muito texto. Escreva 3 com carinho, veja o padrão que funciona, replique.

**3. O site nunca ficar "pronto".** Nenhum fica. Publique na semana 7 mesmo incompleto e vá melhorando no ar.

---

## Primeiro passo, hoje

Abra o Figma e liste os 6 projetos da home. Só isso. Toda decisão de layout depende de saber o que você vai mostrar — e essa é a única etapa que nem eu nem a IA podemos fazer por você.
