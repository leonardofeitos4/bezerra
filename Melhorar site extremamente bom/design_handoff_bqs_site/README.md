# Handoff: Site Institucional — Bezerra, Queiroz & Santos Advocacia (BQS)

## Overview
Redesign completo do site institucional de um escritório de advocacia em Recife-PE. One-page com navegação por âncoras: Hero, Áreas de Atuação, Citação, Equipe, O Escritório, Estatísticas, Localização, Contato e Footer. Direção visual: elegância orgânica — paleta navy + dourado, tipografia serifada clássica, e formas **arredondadas em tudo** (arcos, pílulas, círculos) no lugar de caixas retas.

## About the Design Files
Os arquivos deste pacote são **referências de design criadas em HTML** — protótipos que mostram o visual e o comportamento pretendidos, **não código de produção para copiar diretamente**. A tarefa é **recriar este design no ambiente do projeto de destino** (React, Next.js, Vue, HTML/CSS puro, etc.) usando os padrões e bibliotecas já estabelecidos — ou, se ainda não existe um projeto, escolher o framework mais adequado (para um site institucional estático, HTML/CSS/JS puro ou Astro/Next.js estático são boas escolhas) e implementar lá.

Nota técnica: `BQS v2.dc.html` usa um runtime proprietário de preview (`support.js`, tags `<x-dc>`, `<sc-for>`, `<sc-if>`, atributos `{{ }}`). **Ignore o runtime** — leia o arquivo como especificação: todo o markup, estilos inline, conteúdo e a classe `Component` (lógica JS) estão lá. Os loops `<sc-for>` iteram sobre os arrays de dados definidos em `renderVals()` no `<script data-dc-script>` do mesmo arquivo (areas, teamGroups, reasons, stats).

## Fidelity
**High-fidelity (hifi).** Cores, tipografia, espaçamentos, raios e microinterações são finais. Recriar fielmente.

## Design Tokens
Cores:
- Navy principal (fundo): `#0A1A2F`
- Navy alternado (seções): `#08182B`
- Navy quase-preto (header rolado / footer): `#050D18` (header rolado: `rgba(5,13,24,.94)`)
- Card interno: `#0C2038`
- Dourado principal: `#C8A55C` · Dourado claro (hover/itálico): `#E4C883` / `#D9BD7E`
- Faixa dourada: gradiente 140° `#C6A05A → #B08D48`
- Título/creme: `#F4F1E9` · Corpo: `#93A6BA` / `#A9BACB` · Secundário: `#8DA0B4` / `#7E92A6` · Apagado: `#6F8093` / `#54677B`
- Verde WhatsApp: `#1F9D68`
- Bordas douradas translúcidas: `rgba(200,165,92,.14–.5)` conforme ênfase

Tipografia:
- Display/títulos: **Cormorant Garamond** (Google Fonts), pesos 400–700 + itálico. H1: `clamp(50px,5.6vw,86px)`, line-height 1, peso 500. H2: `clamp(38px,4.6vw,64px)`. Palavras de ênfase em itálico dourado (`#D9BD7E`).
- UI/corpo: **Jost**, pesos 300–600. Corpo 14.5–16.5px, line-height 1.7–1.85. Labels/eyebrows: 10.5–12.5px, letter-spacing `.2em–.3em`, caixa alta.

Raios (assinatura do design):
- Botões, tags, badges: `border-radius:999px` (pílula)
- Cards: `24–36px` · Faixa de stats: `48px`
- Foto hero: `300px 300px 0 0` (arco) · Fotos da equipe: `150px 150px 0 0` (card `150px 150px 28px 28px`)
- Ícones e números: círculos perfeitos (`50%`)

Sombras: hover de cards `0 26px 60px -30px rgba(0,0,0,.7)`; CTA dourado hover `0 16px 40px -14px rgba(200,165,92,.6)`; faixa dourada `0 40px 90px -40px rgba(200,165,92,.4)`.

Espaçamento: seções `padding:120px 40px`; container `max-width:1320px`; gaps de grid 26–80px.

## Screens / Views (one-page, seções em ordem)

### 1. Header (fixo)
- Transparente no topo; após 40px de scroll ganha fundo `rgba(5,13,24,.94)`, borda inferior dourada `.16` e sombra (transição .4s).
- Esquerda: emblema circular 52px (borda dourada 1.5px, "BQS" serifado) + "BEZERRA, QUEIROZ & SANTOS" (serif 20px, nowrap) / "ADVOCACIA" (10px, tracking `.42em`, dourado).
- Direita (≥1180px): links ATUAÇÃO · EQUIPE · O ESCRITÓRIO · LOCALIZAÇÃO (12.5px, tracking .2em, `#C9D3DE`) + pílula "CONSULTA" (borda dourada; hover: fundo dourado, texto navy).
- <1180px: hambúrguer circular → overlay fullscreen `rgba(5,13,24,.97)` + blur, links serifados 30px centralizados.

### 2. Hero (min-height 100vh)
- Fundo navy com 2 glows radiais dourados (círculos ~600px, `rgba(200,165,92,.07–.13)`, cantos opostos) e um anel decorativo fino.
- Grid 2 colunas `minmax(0,1.05fr) minmax(0,.95fr)`, gap 60px; <1180px empilha (foto centralizada abaixo).
- Esquerda: pílula-eyebrow "RECIFE · PERNAMBUCO" (com ponto dourado 6px) → H1 "Seus direitos merecem uma defesa *sem concessões.*" → parágrafo (16.5px, max-width 480px) → CTAs: pílula dourada "FALE COM UM ESPECIALISTA →" (hover: sobe 3px + sombra + `#E4C883`) + círculo 58px com "↓" + link "CONHEÇA A EQUIPE".
- Direita (width `min(460px,100%)`): foto em **arco** 560px de altura (`border-radius:300px 300px 0 0`, borda dourada .35) com segundo arco fantasma deslocado -20px; selo circular dourado 132px sobreposto embaixo-esquerda ("+8 / ANOS DE / ATUAÇÃO", texto navy); pílula flutuante topo-direita com ponto verde + "+1.200 CLIENTES ATENDIDOS" (fundo navy .85 + blur).
- Placeholder de imagem: usar foto real da equipe (cliente fornece).

### 3. Áreas de Atuação (`#atuacao`)
- Cabeçalho 2 colunas: pílula-eyebrow + H2 "Expertise jurídica nas *frentes que importam.*" | parágrafo de apoio à direita.
- Grid `repeat(auto-fit,minmax(340px,1fr))`, gap 26px — 4 cards:
  - Card: radius 32px, fundo gradiente `rgba(255,255,255,.035)→.012`, borda dourada .16; hover: borda .5, sobe 5px, sombra.
  - Numeral itálico gigante (150px serif, `rgba(200,165,92,.07)`) vazando o canto sup-direito.
  - Ícone em círculo 60px (borda dourada .45, fundo .07): relógio / casa / maleta / cifrão (SVG stroke 1.4).
  - Título serif 27px; descrição 14.5px; tags-pílula (10.5px uppercase, borda .32, fundo dourado .06); link "CONSULTAR AGORA" + seta em círculo 34px (hover aumenta o gap).
- Conteúdo dos 4 cards (títulos, descrições e tags) está no array `areas` do arquivo.

### 4. Faixa de Citação
- Fundo `#08182B`, glow central. Aspas serifadas 90px douradas; citação itálica serif `clamp(24px,3vw,34px)` dourada: "Defender seus direitos não é apenas nossa profissão. É o nosso compromisso com cada pessoa que confia em nós." Assinatura "— EQUIPE BQS —" com traços.

### 5. Equipe (`#equipe`)
- Cabeçalho: eyebrow + H2 "Os profissionais por trás *da sua defesa.*" + parágrafo.
- 3 grupos, cada um com linha-título: nome serif 26px + pílula contadora ("04 PROFISSIONAIS") + hairline dourada preenchendo.
- Cards `repeat(auto-fill,minmax(258px,1fr))`, gap 28px: **topo arqueado** (`150px 150px 28px 28px`), foto aspect-ratio 4/4.6 com arco `150px 150px 0 0`, texto centralizado: nome serif 19px, pílula OAB (10px dourada), bio 13px. Hover igual aos cards de área.
- Membros (nome / OAB / bio) nos arrays `teamGroups`: Previdenciário (Joel de Oliveira Bezerra Filho 28.846; Christiane Laís A. Santos Morais 33.860; Letícia Cunha Ximenes 65.357; Júlia Queiroz de Freitas 54.363), Cível & Trabalhista (Aloizio Bernardino dos Santos 36.343; Camila Jerônimo de Araújo Cajui 42.045), Comercial & Atendimento (Simone Maria da Silva 30.039; Jéssica Maria da C. T. Nunes — "SETOR COMERCIAL").

### 6. O Escritório (`#escritorio`)
- Fundo `#08182B`, glow inferior-direito. 2 colunas: texto institucional à esquerda (3 parágrafos — ver arquivo); à direita 5 cards-razão (radius 24px): círculo dourado 48px com numeral serif + título serif 20px + descrição 13.5px; hover desliza 6px à direita.

### 7. Faixa de Estatísticas
- Cartão dourado flutuante (radius 48px, gradiente, sombra dourada) dentro da seção navy: 4 stats centrados — números serif `clamp(46px,4.6vw,60px)` navy + labels 11.5px tracking .22em.
- Valores: +1.200 CLIENTES ATENDIDOS · +8 ANOS DE ATUAÇÃO · 4 ÁREAS DE ATUAÇÃO · 8 PROFISSIONAIS NA EQUIPE.
- Animação count-up (1.5s, ease-out cúbico, formato pt-BR) ao entrar na viewport (IntersectionObserver, threshold .5, uma vez).

### 8. Localização (`#localizacao`)
- 2 colunas (1fr / 1.15fr): esquerda eyebrow + H2 "Venha nos *conhecer.*" + parágrafo + 3 linhas de contato (ícone em círculo 46px + label dourada 10.5px + valor 14.5px): Endereço (Rua Alfredo de Castro, 2175, Sala 07 / Espinheiro, Galeria Center Norte / Recife-PE, CEP 52021-000), WhatsApp (81) 98388-2001 → `https://wa.me/5581983882001`, Instagram @bezerraesantosadv.
- Direita: Google Maps embed em container radius 36px, borda dourada, min-height 460px, `filter:grayscale(.4) contrast(1.05)`.

### 9. Contato (`#contato`)
- Fundo `#08182B`. Esquerda: eyebrow + H2 "O primeiro passo é *uma conversa.*" + parágrafo + botão-pílula verde WhatsApp (`#1F9D68`, ícone + "INICIAR ATENDIMENTO VIA WHATSAPP", hover sobe 3px) + microcopy "Respondemos em até 2 horas em dias úteis".
- Direita: card de formulário (navy `#0A1A2F`, radius 36px, borda dourada .2, padding 48px): campos NOME COMPLETO, TELEFONE/WHATSAPP, ÁREA DE INTERESSE (select com as 4 áreas), DESCREVA BREVEMENTE O SEU CASO (textarea). Inputs: fundo `#08182B`, radius 14px, borda dourada .2 (focus: borda `#C8A55C`), placeholder `#54677B`. Botão-pílula dourado "SOLICITAR CONSULTA".
- Ao enviar (preventDefault): substituir formulário por estado de sucesso — círculo com check dourado + "Mensagem enviada" + texto. Em produção, integrar com backend/e-mail/WhatsApp conforme o projeto.

### 10. Footer
- Fundo `#050D18`. Grid `1.5fr 1fr 1fr 1.2fr`: marca + descrição + CNPJ 24.351.096/0001-09 + sociais em círculos; colunas ATUAÇÃO, INSTITUCIONAL, CONTATO (links âncora / dados).
- Barra final: © 2026 · disclaimer "Este site tem caráter exclusivamente informativo e não constitui consultoria jurídica." · pílula "OAB/PE INSCRITO" com ícone escudo.

### Flutuante
- Botão WhatsApp fixo (bottom/right 28px): círculo 58px verde com pulso keyframes (`box-shadow` verde expandindo, 2.6s infinite), hover scale 1.08.

## Interactions & Behavior
- Scroll suave por âncoras (`scroll-behavior:smooth` + `scroll-margin-top:90px` nas seções).
- Header muda de transparente → sólido em `scrollY > 40` (listener passive).
- Reveal on scroll: elementos começam `opacity:0; translateY(26px)` e animam para visível (transição .8s `cubic-bezier(.22,.61,.36,1)`; IntersectionObserver threshold .12, rootMargin `0px 0px -8% 0px`, uma vez). Fallback: visível se IO indisponível.
- Count-up das estatísticas (descrito acima).
- Hovers: descritos por componente (style-hover no arquivo = `:hover`).
- Responsivo: breakpoint 1180px (nav→hambúrguer, hero empilha); 920px (grids 2-col→1-col, H1 menor, padding lateral 24px). Grids de cards já são fluidos via auto-fit/auto-fill.

## State Management
- `scrolled: boolean` (header), `menuOpen: boolean` (overlay mobile), `sent: boolean` (formulário). Sem fetch de dados; conteúdo estático.

## Assets
- Fontes: Google Fonts — Cormorant Garamond, Jost.
- Fotos: placeholders (`<image-slot>`) — o cliente fornecerá as fotos reais da equipe (hero panorâmica + 8 retratos 4:5). Substituir por `<img>`/`background-image` reais.
- Ícones: SVGs inline no próprio arquivo (stroke 1.4–1.8) — copiar dali.
- Mapa: Google Maps embed (`https://www.google.com/maps?q=Rua%20Alfredo%20de%20Castro%202175%20Espinheiro%20Recife%20PE&output=embed`).

## Files
- `BQS v2.dc.html` — o design completo (markup + estilos inline + lógica na classe `Component` + arrays de conteúdo). **Fonte da verdade.**
- `image-slot.js` — componente de placeholder de imagem do ambiente de preview; apenas referência, não portar.
- `support.js` — runtime do ambiente de preview; ignorar no port.
