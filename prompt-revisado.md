# Prompt Revisado — Landing Page FinApp
**Versão:** 2.0 — revisada pelos agentes Frontend e UX/Design
**Data:** 28/02/2026

> Alterações em relação ao prompt original estão marcadas com `[ALTERADO]` ou `[NOVO]`.

---

Crie uma Landing Page completa em HTML + CSS + JavaScript puro (um único arquivo index.html autocontido), visualmente inspirada no site da DolarApp. O objetivo é reproduzir a estrutura, o estilo visual e os componentes com fidelidade — sem depender de frameworks de JS ou build tools.

---

## IDENTIDADE VISUAL

**Paleta de cores:**
- Fundo primário escuro: #1F1F1F
- Fundo secundário (cards, seções alternativas escuras): #111111 `[ALTERADO: removido #1A1A1A e #2A2A2A como tons independentes — usar apenas estes 2]`
- Cards em fundo escuro: background #1E1E1E, border: 1px solid rgba(255,255,255,0.06) `[ALTERADO: unificado]`
- Cor de destaque / brand: #00E676 (verde vibrante) — usar apenas em fundos escuros ou fundos verdes
- Cor de destaque em fundo branco: #00A854 (verde mais escuro, contraste adequado) `[NOVO: #00E676 em #FFFFFF tem contraste 1.8:1, falha WCAG. Usar #00A854 para CTAs textuais em seções brancas]`
- Texto primário: #FFFFFF
- Texto secundário / muted: #B5B5B5 `[ALTERADO: era #A0A0A0 — ratio 4.0:1 falha WCAG AA. #B5B5B5 garante 4.6:1]`
- Fundo branco (seções de features): #FFFFFF com texto #111111
- Fundo cinza claro (Feature 2): #F7F7F7 `[NOVO: quebra monotonia de 3 seções brancas consecutivas]`

**Tipografia:**
- Fonte: Inter (Google Fonts). Carregar via `<link rel="preconnect">` + `<link>` com `&display=swap`. `[ALTERADO: adicionar display=swap]`
- Headline hero: 64px desktop / 38px mobile, font-weight: 800, line-height: 1.1
- Subtítulos de seção: 42px desktop / 28px mobile, font-weight: 700 `[ALTERADO: adicionado 28px mobile — 42px era grande demais]`
- Corpo: 16-18px, font-weight: 400, line-height: 1.6
- Labels/botões: 15px, font-weight: 600, letter-spacing: 0.01em

**Bordas e raios:**
- Cards: border-radius: 20px
- Botões principais: border-radius: 50px (pill)
- Botões secundários textuais sem borda

**Sombras:**
- Cards em fundos claros: box-shadow: 0 4px 24px rgba(0,0,0,0.08)
- Cards em fundos escuros: sem sombra, usar border: 1px solid rgba(255,255,255,0.06)

**Sistema de espaçamento:** `[NOVO]`
- Padding vertical entre seções: 96px desktop / 64px mobile
- Container principal: max-width: 1200px, margin: 0 auto, padding: 0 24px
- Grid interno: gap padrão de 24px entre cards, 48px entre colunas

**Regra de uso dos CTAs:** `[NOVO]`
- Botão pill verde = ação primária (cadastro, download, conversão)
- CTA textual com seta = ação secundária (saiba mais, ver detalhes)

---

## ESTRUTURA DE SEÇÕES

`[ALTERADO: ordem das seções reorganizada para melhorar narrativa — "O quê" antes do "Por quê", calculadora antes do social proof]`

### 1. NAVBAR (fixa no topo)
- Altura: 72px desktop / 60px mobile
- Fundo: #1F1F1F com leve blur: `backdrop-filter: blur(12px); -webkit-backdrop-filter: blur(12px);`
- Conteúdo: [Logo "FinApp" à esquerda] — [Links centrais: "Blog" e "FAQ"] — [Seletor de idioma: botão com emoji de bandeira 🇧🇷 e texto "PT", sem dropdown funcional] — [Botão pill "Cadastre-se" em verde]
- Comportamento: `position: fixed; z-index: 100`. Ao rolar mais de 50px, adicionar classe `.scrolled` com `border-bottom: 1px solid rgba(255,255,255,0.08)`
- Mobile: esconder links centrais e seletor de idioma. Mostrar logo + botão CTA + botão hamburger (☰) `[ALTERADO: adicionado botão hamburger]`
- Hamburger mobile: ao clicar, exibir menu vertical com links Blog, FAQ e seletor de idioma em overlay sobre a página `[NOVO]`

### 2. HERO SECTION
- Fundo: #1F1F1F, tela cheia (min-height: 100vh)
- Layout: centralizado verticalmente e horizontalmente, `display: flex; flex-direction: column; align-items: center; justify-content: center`
- Headline principal (H1): 2 linhas, bold, branco. Ex: "Os países têm fronteiras. Suas finanças, não mais."
- Subtítulo: parágrafo centralizado, cor #B5B5B5, max-width: 600px. Ex: "Diga tchau às tarifas abusivas. Diga tchau às fronteiras financeiras. Diga oi para a FinApp."
- CTA no hero: botão pill verde "Comece grátis" + CTA textual secundário "Ver como funciona ↓" abaixo `[NOVO: hero precisava de CTA]`
- Abaixo dos CTAs: 3 mockups de celular sobrepostos, com o central maior. Usar `position: relative` no container e `position: absolute` nos laterais.
  - Phone central: width: 280px, height: 560px, border-radius: 36px, background: #0D0D0D, border: 2px solid rgba(255,255,255,0.12)
  - Phones laterais: width: 240px, height: 480px, mesmas propriedades, opacity: 0.7, deslocados ±120px horizontalmente e 40px para baixo
  - Tela interna de cada phone: div com margin: 12px, border-radius: 24px, background: linear-gradient(160deg, #00E676, #00A854)
  - Mobile (< 768px): esconder phones laterais, mostrar apenas o central `[ALTERADO: especificado dimensões e comportamento mobile]`

### 3. FEATURE 1 — PAGAMENTO GLOBAL (fundo branco)
- `[ALTERADO: movida para posição 3 — "O quê" antes do "Por quê"]`
- Layout: grid de 2 colunas (50/50), gap: 48px, align-items: center
- Coluna esquerda — Ilustração do cartão:
  - Div retangular: width: 340px, height: 210px, border-radius: 16px
  - Background: linear-gradient(135deg, #e8e8e8, #f8f8f8)
  - Texto "FinApp" em bold no canto superior esquerdo, cor #333
  - Dois círculos sobrepostos simulando Mastercard: círculo esquerdo background #EB001B, círculo direito background #F79E1B, overlap de 50%, posicionados no canto inferior direito
  - Número do cartão: "•••• •••• •••• 4242" em fonte mono, cor #666, parte inferior
- Coluna direita — Texto:
  - H2: "Pague em qualquer lugar do mundo com tarifas justas e transparentes."
  - Parágrafo descritivo, cor #555
  - CTA textual: `color: #00A854` + seta "→" `[ALTERADO: usar #00A854 em fundo branco]`
- Mobile: colunas viram 1 coluna, ilustração acima do texto

### 4. FEATURE 2 — TRANSFERÊNCIAS (fundo #F7F7F7) `[ALTERADO: fundo cinza claro para quebrar monotonia]`
- Layout: grid de 2 colunas (50/50), gap: 48px, colunas invertidas (texto esquerda, ilustração direita)
- Coluna esquerda — Texto:
  - H2: "Envie e receba transferências em dólares e euros."
  - Parágrafo descritivo
  - Disclaimer em font-size: 12px, color: #999: "* Sujeito a limites e disponibilidade por região."
  - CTA textual: `color: #00A854` + seta "→"
- Coluna direita — Ilustração de transferências: `[ALTERADO: substituídas linhas tracejadas por cards — mais simples e mais limpo]`
  - 3 cards empilhados verticalmente, cada um com fundo #FFFFFF, border-radius: 12px, padding: 16px, box-shadow: 0 2px 12px rgba(0,0,0,0.06)
  - Cada card: avatar circular (inicial em fundo verde) + nome + valor transferido + bandeira. Ex: "M — Maria enviou R$ 800,00 🇧🇷→🇺🇸"
  - Animação sutil: cards aparecem com fade-in escalonado (stagger de 0.15s cada)
- Mobile: colunas viram 1 coluna, ilustração abaixo do texto

### 5. FEATURE 3 — CONVERSÃO (fundo branco)
- Layout: grid de 2 colunas (50/50), imagem à esquerda, texto à direita
- Coluna esquerda — Phone frame com lista de moedas:
  - Div phone frame: width: 260px, height: 480px, border-radius: 36px, background: #0D0D0D, border: 2px solid rgba(255,255,255,0.1), margin: 0 auto
  - Conteúdo interno (margin: 16px): lista com 4 itens separados por border-bottom: 1px solid rgba(255,255,255,0.06)
  - Cada item: emoji de bandeira + nome da moeda + chevron "›" à direita. Ex: "🇧🇷 Reais", "🇺🇸 Dólares", "🇪🇺 Euros", "🔵 Cripto"
  - Texto dos itens: color: #FFFFFF, font-size: 15px
- Coluna direita — Texto:
  - H2: "Compre dólares digitais com reais, em segundos."
  - Parágrafo descritivo
  - CTA textual: `color: #00A854` + seta "→"
- Mobile: colunas viram 1 coluna, phone frame acima do texto

### 6. SEÇÃO "POR QUÊ FINAPP?" (fundo verde)
- `[ALTERADO: movida para posição 6, depois das features — narrativa "O quê" antes do "Por quê"]`
- Fundo: #00E676, padding: 96px 24px
- Título: H2, color: #111111, font-weight: 800, text-align: center. Ex: "Por que a FinApp?"
- Subtítulo: parágrafo centralizado, color: #1A1A1A, max-width: 560px, margin: 0 auto 40px
- Área central — Ilustração de preview (não simular player de vídeo): `[ALTERADO: "player falso" substituído por ilustração — não enganar o usuário]`
  - Div retangular: max-width: 720px, height: 400px, border-radius: 24px, background: #1A1A1A, margin: 0 auto
  - Conteúdo: ícone de celular (📱) centralizado + texto "FinApp — suas finanças, sem fronteiras" abaixo, color: #FFFFFF
  - Badge no canto inferior esquerdo: div pequeno com logo "FA" em verde + texto "FinApp"
  - Sem ícone de play — é uma ilustração, não um player `[ALTERADO]`
- Mobile: altura do retângulo reduz para 240px

### 7. CALCULADORA INTERATIVA (fundo branco)
- `[ALTERADO: movida para posição 7, antes do social proof — usuário experimenta antes de ver depoimentos]`
- Padding: 96px 24px
- Título: H2, text-align: center, color: #111111. Ex: "Ninguém faz isso melhor. Experimente você mesmo."
- Layout: grid de 2 colunas (50/50), gap: 48px, align-items: center
- Coluna esquerda — Calculadora:
  - Container: background: #F7F7F7, border-radius: 20px, padding: 32px
  - Campo BRL: label "Você envia (BRL)", input numérico com id="brl-input", font-size: 24px, border: none, background: transparent. Adicionar `aria-label="Valor em reais"` `[NOVO: acessibilidade]`
  - Separador: botão circular verde (40px) com ícone "↕", `aria-hidden="true"`
  - Campo USD: label "Você recebe (USD)", div com id="usd-output", font-size: 24px, color: #111, `aria-live="polite"` `[NOVO: aria-live para leitores de tela]`
  - Taxa de câmbio: texto pequeno color: #00A854 "↗ $1 = 5.15 BRL" (valor hardcoded em variável JS `const RATE = 5.15`)
  - Botão pill verde "Converter agora" (largura total do container)
- Coluna direita — Gráfico simulado:
  - Div phone frame: width: 260px, height: 420px, border-radius: 36px, background: #0D0D0D, border: 2px solid rgba(255,255,255,0.1), margin: 0 auto
  - Conteúdo interno: SVG inline com path de linha verde simulando variação de câmbio (path hardcoded, sem dados reais). Ex: `<path d="M0,120 C60,90 120,140 180,80 C240,20 300,70 360,40" stroke="#00E676" fill="none" stroke-width="2"/>` `[ALTERADO: SVG path hardcoded em vez de canvas]`
  - Texto acima do gráfico: "BRL/USD — últimos 30 dias", color: #B5B5B5, font-size: 12px
- CTA após calculadora: botão pill verde "Criar conta grátis" centralizado abaixo das colunas `[NOVO: CTA após momento de maior engajamento]`
- Mobile: colunas viram 1 coluna, gráfico escondido

### 8. SOCIAL PROOF (fundo escuro #111111)
- Padding: 96px 24px
- Título H2 centralizado: "Para quem está <span style='color:#00E676'>sempre</span> em movimento."
- Ratings das app stores em linha, centralizados, margin-top: 24px:
  - "🍎 App Store — 4.5 ★★★★½"
  - "▶ Google Play — 4.7 ★★★★¾"
  - Fonte: 14px, color: #B5B5B5; estrelas: color: #00E676
- Grid de 3 cards, gap: 24px:
  - Cada card: background: #1E1E1E, border: 1px solid rgba(255,255,255,0.06), border-radius: 20px, padding: 28px
  - Avatar: div circular 48px, background: #00E676, color: #111, font-weight: 700 (inicial do nome)
  - Nome + cidade: font-size: 15px, color: #FFFFFF + font-size: 13px, color: #B5B5B5
  - 5 estrelas: "★★★★★" color: #00E676
  - Depoimento: font-size: 15px, color: #B5B5B5, line-height: 1.6, entre aspas
- Mobile: cards em scroll horizontal com `overflow-x: auto; scroll-snap-type: x mandatory` — cada card `scroll-snap-align: start; min-width: 85vw` `[ALTERADO: adicionado scroll-snap]`
- CTA após social proof: botão pill verde "Abrir minha conta" centralizado, margin-top: 48px `[NOVO: CTA no momento de maior confiança]`

### 9. MÍDIA (fundo branco)
- Padding: 80px 24px
- Título H3 centralizado: "O que os especialistas dizem sobre nós.", color: #111
- 4 logos de veículos em linha, centralizados, gap: 48px, margin-top: 48px:
  - Cada logo: texto estilizado, font-weight: 700, font-size: 22px, color: #BBBBBB, opacity: 0.5
  - Hover: `opacity: 1; color: #333; transition: all 0.2s`
  - Exemplos: "Bloomberg", "Yahoo Finance", "TechCrunch", "Forbes"
- Mobile: logos em grid 2x2

### 10. MOVIMENTO GLOBAL (fundo escuro #111111)
- Padding: 96px 24px
- Título H2 centralizado: "Participe do movimento <span style='color:#00E676'>global</span>."
- Ratings repetidos (igual seção 8), margin-top: 24px
- Grid de 8 cards de destino, grid-template-columns: repeat(4, 1fr), gap: 16px:
  - Cada card: height: 200px, border-radius: 16px, position: relative, overflow: hidden
  - Background: gradiente distinto por cidade. Exemplos:
    - Barcelona: linear-gradient(135deg, #f093fb, #f5576c)
    - Cairo: linear-gradient(135deg, #4facfe, #00f2fe)
    - Tóquio: linear-gradient(135deg, #43e97b, #38f9d7)
    - Lisboa: linear-gradient(135deg, #fa709a, #fee140)
    - Miami: linear-gradient(135deg, #a18cd1, #fbc2eb)
    - Dubai: linear-gradient(135deg, #fccb90, #d57eeb)
    - Londres: linear-gradient(135deg, #667eea, #764ba2)
    - Nova York: linear-gradient(135deg, #f7971e, #ffd200)
  - Badge de localização: div no canto inferior esquerdo, background: rgba(0,0,0,0.5), border-radius: 8px, padding: 4px 10px, font-size: 12px, color: #FFF. Ex: "📍 Barcelona"
- Botão pill verde grande "Baixar FinApp" centralizado, margin-top: 48px, padding: 18px 48px, font-size: 17px
- Mobile: grid vira 2 colunas

### 11. FOOTER (fundo #111111)
- Border-top: 1px solid rgba(255,255,255,0.08)
- Padding: 64px 24px 32px
- Layout: grid com logo à esquerda + 3 colunas de links à direita
- Logo "FinApp" em #00E676, font-weight: 800
- Colunas de links:
  - "Empresa": FAQ, Termos e políticas, Trabalhe conosco, Contato, Ouvidoria, Privacidade (DPO)
  - "Comunidade": Telegram
  - "Siga-nos": Instagram, X (Twitter), LinkedIn, Facebook
- Cada link: color: #B5B5B5, font-size: 14px; hover: color: #FFFFFF
- Separador: border-top: 1px solid rgba(255,255,255,0.06), margin: 32px 0
- Disclaimer legal: font-size: 12px, color: #666, line-height: 1.6. Texto: "A FinApp é uma empresa de tecnologia financeira, não um banco. Os serviços bancários são fornecidos pelo Banco Parceiro, membro do FDIC. Produtos de investimento não são garantidos pelo FDIC, podem perder valor e não são depósitos bancários."
- Copyright: "© 2025 FinApp. Todos os direitos reservados.", color: #666, font-size: 13px, text-align: center
- Mobile: logo + colunas em coluna única, colunas de links colapsadas por padrão com accordion simples

---

## COMPONENTES E COMPORTAMENTOS GLOBAIS

**Botão CTA primário (pill verde):**
```css
background: #00E676;
color: #111111;
border-radius: 50px;
padding: 14px 28px;
font-weight: 700;
font-size: 15px;
border: none;
cursor: pointer;
transition: transform 0.2s, background 0.2s;
```
Hover: `transform: scale(1.03); background: #00FF88;`

**Focus state (acessibilidade):** `[NOVO]`
```css
:focus-visible {
  outline: 2px solid #00E676;
  outline-offset: 2px;
}
```

**CTA textual em fundo escuro:**
```css
color: #00E676;
font-weight: 600;
text-decoration: none;
display: inline-flex;
align-items: center;
gap: 6px;
```

**CTA textual em fundo branco:** `[NOVO]`
```css
color: #00A854;
font-weight: 600;
text-decoration: none;
display: inline-flex;
align-items: center;
gap: 6px;
```

Hover (ambos): `gap: 10px; transition: gap 0.2s;`

**Scroll suave:**
```css
html { scroll-behavior: smooth; }
```

**Animação de entrada:**
```css
.fade-in { opacity: 0; transform: translateY(30px); transition: opacity 0.6s ease, transform 0.6s ease; }
.fade-in.visible { opacity: 1; transform: translateY(0); }
```
IntersectionObserver com `threshold: 0.15` para ativar antes do elemento estar totalmente visível. `[ALTERADO: adicionado threshold]`

**Navbar scroll behavior:**
Ao rolar mais de 50px, adicionar classe `.scrolled` com `border-bottom: 1px solid rgba(255,255,255,0.08)`.

**Calculadora JS:**
```js
const RATE = 5.15; // Taxa fixa BRL/USD
document.getElementById('brl-input').addEventListener('input', function() {
  const brl = parseFloat(this.value) || 0;
  document.getElementById('usd-output').textContent = (brl / RATE).toFixed(2);
});
```

**Responsividade:**
- Breakpoint principal: 768px — grids de 2 colunas viram 1 coluna
- Breakpoint mobile small: 480px — ajustes finos (padding reduzido, font-size dos cards, grid de destinos) `[NOVO]`
- Hero: 64px → 38px
- Subtítulos de seção: 42px → 28px `[NOVO]`
- Navbar: hamburger menu aparece, links e seletor de idioma somem
- Cards de review: scroll horizontal com scroll-snap `[NOVO]`

**CTA sticky no mobile:** `[NOVO]`
```css
@media (max-width: 768px) {
  .sticky-cta {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 12px 24px;
    background: #1F1F1F;
    border-top: 1px solid rgba(255,255,255,0.08);
    z-index: 99;
  }
  .sticky-cta .btn-pill {
    width: 100%;
    text-align: center;
  }
}
```
Adicionar `<div class="sticky-cta"><button class="btn-pill">Cadastre-se grátis</button></div>` antes do `</body>`.

---

## INSTRUÇÕES FINAIS
- Tudo em um único arquivo `index.html`
- CSS dentro de `<style>` no `<head>`
- JavaScript dentro de `<script>` antes do `</body>`
- Não usar nenhuma biblioteca externa (nem jQuery, nem Bootstrap) — apenas Google Fonts via `<link>`
- Nome da marca: "FinApp" — usar consistentemente em todo o arquivo `[ALTERADO: padronizado, remover qualquer referência a "DolarApp"]`
- Usar emojis de bandeiras e ícones Unicode onde necessário
- Usar HTML semântico: `<nav>`, `<main>`, `<section>`, `<footer>`, `<h1>`-`<h3>` na hierarquia correta `[NOVO]`
- Todos os inputs de formulário devem ter `<label>` associado `[NOVO]`
- O resultado final deve parecer um site profissional de fintech real, pronto para apresentação
