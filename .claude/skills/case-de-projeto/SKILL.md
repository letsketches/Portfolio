---
name: case-de-projeto
description: Cria uma página de case novo em projetos/[slug].html no portfólio da Let, seguindo o padrão de luna-monstrinho, almanaque-vampirico e chico-quitandas. Use quando pedirem para montar, criar ou desenvolver a página de um projeto/case, converter um projeto do Figma ou do Behance em página, ou quando mandarem textos e imagens de um projeto para virar case. Também cobre revisar um case existente contra o padrão.
---

# Página de case do portfólio

Monta `projetos/[slug].html` reaproveitando o "chrome" que é idêntico em todos os cases e
escolhendo, entre blocos prontos, só os que o projeto pede.

## Arquivos desta skill

- `referencias/pagina-base.html` — página completa com o chrome pronto e marcadores `{{ }}`.
  É o ponto de partida: copie e preencha.
- `referencias/blocos.html` — catálogo dos blocos de conteúdo. Copie os que servirem
  para dentro da área marcada na página base.

## Fluxo

1. **Copiar a base.** `cp .claude/skills/case-de-projeto/referencias/pagina-base.html projetos/[slug].html`
2. **Preencher os `{{ }}`** do cabeçalho, título e ficha (lista abaixo).
3. **Montar o miolo** escolhendo blocos de `referencias/blocos.html`. Ordem livre — cada
   projeto conta a história do seu jeito. Apague a linha `<!-- MIOLO -->`.
4. **Criar a pasta de imagens**: `assets/img/[slug]/`.
5. **Encadear a navegação**: apontar o "Próximo projeto" deste case para o próximo, e
   conferir se algum case existente deveria apontar para este.
6. **Ligar na home**: `index.html` já tem um card por projeto. Se este case for novo,
   acrescente o card lá seguindo os que já existem.
7. **Verificar** com o bloco de checagem no fim deste arquivo.

## Marcadores da página base

| Marcador | O que é |
|---|---|
| `{{TITULO_PAGINA}}` | Nome do projeto. O `<title>` vira `Nome — Letícia Garcia` |
| `{{SLUG}}` | O slug do arquivo, sem `.html`. Usado nas meta tags de compartilhamento (`og:url` e `og:image`) |
| `{{META_DESCRICAO}}` | 1–2 frases para busca e compartilhamento, até ~155 caracteres |
| `{{CATEGORIA_PT}}` / `{{CATEGORIA_EN}}` | Tag de disciplina no topo: `Design`, `Ilustração` ou `Design + Ilustração` |
| `{{COR_ACENTO}}` | `roxo`, `magenta` ou `laranja` — ver tabela abaixo |
| `{{NOME_PROJETO}}` | Título em display. Sem `data-pt`: nome próprio é igual nos dois idiomas |
| `{{RESUMO_PT}}` / `{{RESUMO_EN}}` | Texto de abertura. Pode ter parágrafos separados por quebra de linha real |
| `{{ANO}}` | Ex.: `2025`. Sem `data-pt` |
| `{{FICHA_CATEGORIA_PT}}` / `{{FICHA_CATEGORIA_EN}}` | O que foi feito por ela, de fato. Aparece na ficha sob o rótulo **Categoria** |
| `{{FERRAMENTAS}}` | Ex.: `Illustrator, Photoshop`. Sem `data-pt` |
| `{{PROXIMO_SLUG}}` / `{{PROXIMO_NOME}}` | Case seguinte na navegação |

Atenção a dois campos parecidos: a **tag do topo** diz a disciplina do projeto
(`Design + Ilustração`), enquanto o campo **Categoria da ficha** diz o que ela fez no
projeto (`Autoria, ilustração, projeto gráfico e pesquisa`). São coisas diferentes com
rótulos parecidos — não troque um pelo outro.

## Cor de acento

Uma por case, usada na tag de categoria e nas barras do carrossel:

| Categoria | Cor |
|---|---|
| Design | `roxo` |
| Ilustração | `magenta` |
| Design + Ilustração | `laranja` |

O amarelo é destaque pontual, nunca a cor do case.

## Imagens que ainda não chegaram

É comum montar a página antes de receber os arquivos. Nesse caso:

- Mantenha o `src` apontando para o caminho final: `../assets/img/[slug]/nome-descritivo.jpg`
- Escreva o `alt` do jeito que ele vai ficar, descrevendo o que a imagem **vai** mostrar
- Marque com o comentário `<!-- IMG PENDENTE: descrição do que falta -->` logo acima

Assim a página fica pronta e dá para achar tudo que falta com um comando:

```bash
grep -rn "IMG PENDENTE" projetos/
```

Quando os arquivos chegarem, é só salvá-los com o nome certo e apagar os comentários.

## Regras que valem em qualquer case

- Container: `max-w-[1280px] mx-auto px-5 lg:px-20`.
- Todo texto visível precisa de `data-pt` **e** `data-en`. Nunca deixe texto solto dentro
  de um elemento que tenha `data-pt` — o script de idioma sobrescreve o conteúdo.
  Exceção: nomes próprios, anos e nomes de ferramentas, que ficam como texto normal.
- Toda imagem precisa de `alt` descritivo — o que aparece nela, não "imagem do projeto".
  Imagem decorativa leva `alt=""` e `aria-hidden="true"`.
- Cantos de imagem: `rounded-lg`. Nada mais arredondado que isso.
- Espaçamento na escala do Tailwind (múltiplos de 4).
- Desktop (1440px) primeiro, mobile (390px) depois.

## Não editar na página base

Estes trechos são iguais em todas as páginas do site; mexer neles quebra a consistência:

bloco `@theme` · faixa de gradiente do topo · header · faixa `@letsketches` · lightbox ·
script de troca de idioma · script do carrossel

As meta tags de compartilhamento (`og:` / `twitter:`) do `<head>` também são padrão: só troque
os marcadores. A `og:image` aponta para `assets/img/[slug]/capa.jpg` — se a capa do case for
`.webp` ou `.png`, corrija a extensão. Enquanto o site não estiver no ar, a URL fica como
`https://SEU-DOMINIO`; depois do deploy é um find-and-replace único em todos os arquivos.

**A faixa `@letsketches` tem duas cópias com exatamente 10 itens cada.** A animação anda
`-50%`, então as duas metades precisam ser idênticas — com número diferente de itens o
loop dá um salto visível a cada volta. (O `almanaque-vampirico.html` está com 9 na
primeira e 10 na segunda; se for mexer nele, corrija.)

## Rodapé dos cases

Uma linha só: Behance · Instagram · LinkedIn à esquerda, copyright à direita.
**Sem e-mail e sem bloco de contato** — isso fica na home e na página Sobre, e o menu do
topo já leva para lá. Todos os links externos levam `rel="noopener noreferrer"`.

Os quatro cases e os dois templates já estão nesse padrão; se encontrar um fora dele,
alinhe.

## Checagem antes de fechar

Troque `[slug]` e rode da raiz do projeto:

```bash
python3 - projetos/[slug].html <<'FIM'
import re, os, sys
f = sys.argv[1]
s = open(f, encoding='utf-8').read()
base = os.path.dirname(f)
# tira os <script> antes de contar: eles citam os mesmos data-attributes do markup
corpo = re.sub(r'<script\b.*?</script>', '', s, flags=re.S)

srcs = [x for x in re.findall(r'src="([^"]+)"', corpo) if not x.startswith('http')]
falta = [x for x in dict.fromkeys(srcs) if not os.path.exists(os.path.normpath(os.path.join(base, x)))]
print('marcadores nao preenchidos:', re.findall(r'\{\{[A-Z_]+\}\}', corpo) or 'nenhum')
print('imagens sem arquivo:', falta or 'nenhuma')
print('IMG PENDENTE:', corpo.count('IMG PENDENTE'))
og = re.search(r'og:image" content="[^"]*/assets/img/(.+?)"', s)
print('og:image existe:', os.path.exists(os.path.join(base, '..', 'assets/img', og.group(1))) if og else 'SEM OG')
print('data-pt/data-en:', len(re.findall(r'data-pt=', corpo)), '/', len(re.findall(r'data-en=', corpo)))
print('img sem alt:', len(re.findall(r'<img(?![^>]*alt=)', corpo)))
print('target=_blank sem rel:', len(re.findall(r'target="_blank"(?![^>]*rel=)', corpo)))

copias = [c.count('@letsketches') for c in re.split(r'(?=<span class="flex items-center shrink-0">)', corpo) if 'shrink-0">' in c]
print('itens por copia da faixa (as duas devem ser 10):', copias[1:])

for i, car in enumerate(re.findall(r'<div data-carousel\b.*?</section>', corpo, re.S), 1):
    b, sl = car.count('data-carousel-segment'), car.count('data-carousel-slide')
    print(f'carrossel {i}: {b} barras / {sl} slides', 'OK' if b == sl else '<<< DESCASADO')
FIM
```

O painel de preview desta máquina carrega páginas dentro de `projetos/` como `data:` URL,
onde caminho relativo não resolve — então **não dá para conferir esses arquivos pelo
navegador aqui**. A checagem acima é a verificação confiável. Diga isso ao usuário em vez
de afirmar que viu a página funcionando.
