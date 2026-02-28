# Prompt Original — Landing Page (estilo DolarApp)

Crie uma Landing Page completa em HTML + CSS + JavaScript puro (um único arquivo index.html autocontido), visualmente inspirada no site da DolarApp. O objetivo é reproduzir a estrutura, o estilo visual e os componentes com fidelidade — sem depender de frameworks de JS ou build tools.

---

## IDENTIDADE VISUAL

**Paleta de cores:**
- Fundo primário escuro: #1F1F1F
- Fundo secundário (cards, seções alternativas): #2A2A2A ou #111111
- Cor de destaque / brand: #00E676 (verde vibrante)
- Texto primário: #FFFFFF
- Texto secundário / muted: #A0A0A0
- Fundo branco (seções de features): #FFFFFF com texto #111111

**Tipografia:**
- Fonte: Inter (Google Fonts). Carregar via `<link>` do Google Fonts.
- Headline hero: 64px, font-weight: 800, line-height: 1.1
- Subtítulos de seção: 42px, font-weight: 700
- Corpo: 16-18px, font-weight: 400, line-height: 1.6
- Labels/botões: 15px, font-weight: 600, letter-spacing: 0.01em

**Bordas e raios:**
- Cards: border-radius: 20px
- Botões principais: border-radius: 50px (pill)
- Botões secundários textuais sem borda

**Sombras:**
- Cards em fundos claros: box-shadow: 0 4px 24px rgba(0,0,0,0.08)
- Cards em fundos escuros: sem sombra, usar borda sutil rgba(255,255,255,0.06)

---

## ESTRUTURA DE SEÇÕES (em ordem, de cima para baixo)

### 1. NAVBAR (fixa no topo)
- Altura: 72px desktop / 60px mobile
- Fundo: #1F1F1F com leve blur backdrop-filter
- Conteúdo: [Logo à esquerda] — [Links centrais: "Blog" e "FAQ"] — [Seletor de idioma com emoji de bandeira] — [Botão pill "Cadastre-se" em verde]
- Comportamento: position: fixed, z-index: 100. Ao rolar a página, adicionar sutil borda inferior rgba(255,255,255,0.1)
- Mobile: esconder links centrais, mostrar apenas logo + botão CTA

### 2. HERO SECTION
- Fundo: #1F1F1F, tela cheia (min-height: 100vh)
- Layout: centralizado verticalmente e horizontalmente
- Headline principal (H1): 2 linhas, bold, branco, ex: "Os países têm fronteiras. / Suas finanças, não mais."
- Subtítulo: parágrafo centralizado, cor muted, máx. 600px de largura. Usar repetição anafórica tipo "Diga tchau a X. Diga tchau a Y. Diga oi para [Produto]."
- Abaixo do texto: 3 mockups de celular sobrepostos ligeiramente, com o central maior. Simular com divs estilizados de cor escura com tela interna verde (#00E676), tipo "phone frame" em CSS puro. Os phones devem ter border-radius: 36px, fundo #111, bordas laterais finas, e uma "tela" interna com gradiente verde.
- Sem botão de CTA direto no hero — a conversão vem depois do storytelling

### 3. SEÇÃO "POR QUÊ [PRODUTO]?" (verde)
- Fundo: #00E676 (verde vibrante, seção inteira)
- Texto do título: #111111, bold, centralizado
- Subtítulo curto abaixo do título em preto
- Área central: um retângulo escuro (#1A1A1A) com border-radius: 24px simulando um player de vídeo. Incluir ícone de play (▶) centralizado em branco, e um texto "01:22" no canto inferior esquerdo simulando a duração.
- Logo/ícone da marca no canto inferior esquerdo do player

### 4. SEÇÃO FEATURE 1 — PAGAMENTO GLOBAL (fundo branco)
- Layout: duas colunas (50/50), imagem à esquerda, texto à direita
- Imagem: simulação de cartão de crédito físico (div retangular com border-radius: 16px, fundo em gradiente cinza claro a branco, logo Mastercard simulado com dois círculos sobrepostos vermelho/laranja, e texto "DolarApp" em bold)
- Texto: título H2 bold escuro, parágrafo descritivo, CTA textual verde com seta ">"
- Ex de título: "Pague em qualquer lugar do mundo com tarifas justas e transparentes."

### 5. SEÇÃO FEATURE 2 — TRANSFERÊNCIAS (fundo branco, alternado)
- Layout: texto à esquerda, ilustração à direita
- Ilustração: 3 avatares circulares (usar initials ou emojis) conectados por linhas tracejadas verdes, simulando transferências entre pessoas. Cada avatar tem um balão de texto mostrando "Maria enviou 800 USD 🇺🇸"
- Título: "Envie e receba transferências em dólares e euros"
- Disclaimer em fonte pequena com asterisco
- CTA textual verde

### 6. SEÇÃO FEATURE 3 — CONVERSÃO (fundo branco)
- Layout: imagem à esquerda (mockup de app), texto à direita
- Mockup: div phone frame escuro com uma lista interna simulando opções (Reais 🇧🇷, Dólares 🇺🇸, Euros 🇪🇺, Cripto 🔵), cada item com linha separadora e ícone de chevron à direita
- Texto: "Compre dólares digitais com reais, em segundos."
- CTA textual verde

### 7. SEÇÃO DE AVALIAÇÕES / SOCIAL PROOF (fundo escuro #1A1A1A)
- Título centralizado com palavra-chave em verde: ex. "Para quem está **sempre** em movimento." (a palavra em verde)
- Abaixo do título: ratings das app stores — ícone Apple (🍎 ou SVG) + "4.5 ★" e ícone Play Store + "4.7 ★", em linha, centralizados
- 3 cards lado a lado (grid 3 colunas): cada card tem fundo #2A2A2A, border-radius: 20px, padding: 28px. Conteúdo do card: avatar circular (foto simulada com inicial em fundo verde), nome + cidade abaixo, 5 estrelas verdes, depoimento em texto longo entre aspas.
- Mobile: cards em coluna única com scroll

### 8. SEÇÃO CALCULADORA INTERATIVA (fundo branco)
- Título: "Ninguém faz isso melhor. Experimente você mesmo."
- Layout: duas colunas — calculadora à esquerda, mockup de app à direita
- Calculadora: dois campos de input/display — "BRL" com campo editável e "Dólares digitais" com resultado calculado automaticamente. Entre eles, botão circular verde com ícone de seta ↓. Abaixo, taxa de câmbio em verde tipo "↗ $1 = 5.15 BRL". Botão pill verde "Converter agora".
- Interatividade: ao digitar no campo BRL, o valor em USD atualiza em tempo real (JS simples com taxa fixa definida em variável)
- Mockup à direita: phone frame com gráfico de linha simulado (canvas ou SVG path verde em fundo escuro), mostrando variação de câmbio

### 9. SEÇÃO DE MÍDIA (fundo branco)
- Título centralizado: "O que os especialistas dizem sobre nós."
- 4 logos de veículos de mídia em linha, centralizados, em tom cinza (#BBBBBB), ex.: "Bloomberg", "Yahoo Finance", "TechCrunch", "Forbes" — usar apenas texto estilizado com font-weight: 700 e font-family diferenciada simulando os logos tipográficos
- Hover state: opacidade 100% (os logos ficam com opacity: 0.4 por padrão)

### 10. SEÇÃO MOVIMENTO GLOBAL (fundo escuro #111)
- Título: "Participe do movimento **global**." (palavra global em verde)
- Ratings repetidos (Apple + Play Store) abaixo do título
- Grid de fotos: 6-8 cards de imagem (divs com fundo de gradiente colorido simulando fotos de destinos), com um badge de localização no canto inferior esquerdo (ex: "📍 Barcelona", "📍 Cairo"). As imagens podem ser divs com gradientes distintos para cada cidade.
- Botão pill verde grande: "Baixar DolarApp" centralizado ao final

### 11. FOOTER (fundo #111111)
- Logo à esquerda (topo da coluna)
- 3 colunas de links à direita:
  - "Sobre nós": FAQ, Termos e políticas, Trabalhe conosco, Contato, Ouvidoria, Dados Pessoais (DPO)
  - "Comunidade": Telegram
  - "Siga-nos": Instagram, X (Twitter), LinkedIn, Facebook
- Separador horizontal sutil (rgba branco)
- Texto de disclaimer legal no rodapé: "A [Marca] é uma empresa de tecnologia financeira, não um banco. Os serviços bancários são fornecidos pelo [Banco Parceiro], membro do FDIC..."
- Copyright: "© 2025 [Marca]. Todos os direitos reservados."

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

**CTA textual (links de feature):**
```css
color: #00E676;
font-weight: 600;
text-decoration: none;
display: inline-flex;
align-items: center;
gap: 6px;
```
Hover: `gap: 10px` (a seta se afasta levemente)

**Scroll suave:**
```css
html { scroll-behavior: smooth; }
```

**Animação de entrada (fade + translateY):**
Usar IntersectionObserver para adicionar classe `.visible` em elementos com classe `.fade-in`. CSS:
```css
.fade-in { opacity: 0; transform: translateY(30px); transition: opacity 0.6s ease, transform 0.6s ease; }
.fade-in.visible { opacity: 1; transform: translateY(0); }
```

**Navbar scroll behavior:**
Ao rolar mais de 50px, adicionar classe `.scrolled` ao nav com `border-bottom: 1px solid rgba(255,255,255,0.08)`.

**Responsividade:**
- Breakpoint principal: 768px
- Grids de 2 colunas viram 1 coluna
- Grid de 3 cards de review vira scroll horizontal (overflow-x: auto, white-space: nowrap em mobile)
- Fonte do hero reduz para 38px em mobile
- Navbar colapsa links secundários

---

## INSTRUÇÕES FINAIS
- Tudo em um único arquivo `index.html`
- CSS dentro de `<style>` no `<head>`
- JavaScript dentro de `<script>` antes do `</body>`
- Não usar nenhuma biblioteca externa (nem jQuery, nem Bootstrap) — apenas Google Fonts via `<link>`
- O conteúdo pode ser genérico/placeholder (ex: "FinApp" como nome da marca, "Suas finanças sem fronteiras" como slogan)
- Usar emojis de bandeiras e ícones Unicode onde necessário para simular os elementos visuais sem SVGs externos
- O resultado final deve parecer um site profissional de fintech real, pronto para apresentação
