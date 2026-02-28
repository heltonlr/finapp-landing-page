# Relatório de Revisão UX/Design — Prompt da Landing Page
**Autor:** UX/Design Agent — oConselho
**Data:** 28/02/2026

---

## 1. Fluxo Narrativo

**Avaliação: Bom, com ajustes necessários**

A estrutura geral segue um padrão sólido de landing page: captura atenção (Hero) → gera curiosidade (Por que?) → demonstra valor (Features) → prova social → ferramenta interativa → mídia → CTA final.

**Problemas identificados:**

- **Hero sem CTA é uma falha crítica.** O usuário chega, lê a headline, vê os mockups... e não tem nenhuma ação para tomar. Isso viola a heurística de Nielsen #7 (Flexibilidade e eficiência de uso). Usuários motivados que já querem converter não têm como agir imediatamente. **Sugestão:** Adicionar pelo menos um CTA secundário no hero (ex: "Baixe grátis" ou "Comece agora").

- **Seção "Por que [PRODUTO]?" com vídeo simulado na posição 3 é prematura.** O usuário ainda não entendeu O QUE o produto faz (as features vêm depois), então perguntar "por que?" antes de mostrar "o que" quebra a lógica narrativa. **Sugestão:** Mover esta seção para depois das 3 features, ou transformar as features em subseções dentro dela.

- **Calculadora (seção 8) está deslocada.** Aparece depois do social proof, quebrando o momentum de conversão. Se o usuário já viu depoimentos positivos, o próximo passo deveria ser um CTA forte, não uma calculadora. **Sugestão:** Mover a calculadora para antes do social proof, ou colocá-la entre as features como ferramenta de demonstração de valor.

- **"Movimento Global" (seção 10) é genérica.** Grid de fotos de destinos com "Baixar DolarApp" não conecta bem com o resto do fluxo. Parece um bloco visual sem propósito narrativo claro.

---

## 2. Hierarquia Visual

**Avaliação: Consistente, com ressalvas**

- **Tipografia bem definida.** 64px hero → 42px subtítulos → 16-18px corpo. Escala clara.
- **Problema no mobile:** Hero de 64px reduzindo para 38px está bom, mas não há menção de como os 42px dos subtítulos de seção se comportam no mobile. Vai ficar grande demais.
- **Alternância de fundos** (escuro → verde → branco → branco → branco → escuro → branco → branco → escuro) tem 3 seções brancas consecutivas (Features 1, 2, 3). Isso cria monotonia visual. **Sugestão:** Alternar pelo menos uma feature com fundo claro diferente (#F5F5F5) ou inserir um separador visual.

---

## 3. Problemas de UX

**Heurística #1 (Visibilidade do estado do sistema):**
- O seletor de idioma na navbar não tem indicação de qual idioma está ativo.
- A calculadora interativa não menciona feedback visual durante a conversão (loading, animação de resultado).

**Heurística #2 (Correspondência com o mundo real):**
- "Player de vídeo simulado" — um div escuro com ícone de play que não reproduz nada é enganoso. O usuário vai clicar esperando um vídeo. **Sugestão:** Ou colocar um vídeo real, ou deixar claro que é uma imagem/ilustração, não um player.

**Heurística #3 (Controle e liberdade do usuário):**
- Navbar mobile reduzida a "logo + botão CTA" remove acesso a Blog e FAQ. Usuários mobile perdem navegação. **Sugestão:** Adicionar menu hamburger.

**Heurística #4 (Consistência):**
- Existem 2 tipos de CTA: botão pill verde e CTA textual com seta. Não está claro quando usar qual. Precisa de regra: botão pill = ação primária, textual = ação secundária.

**Heurística #8 (Design minimalista):**
- 11 seções é bastante para uma landing page. O usuário pode desistir antes de chegar ao final. Considerar se "Mídia" e "Movimento Global" são realmente necessárias ou se podem ser condensadas.

---

## 4. Consistência do Design System

**Avaliação: Razoável**

- **Cores:** A paleta está coerente, mas há inconsistência nos fundos escuros: #1F1F1F, #2A2A2A, #111111, #1A1A1A — são 4 tons de cinza escuro diferentes. **Sugestão:** Reduzir para 2 (um primário e um secundário).
- **Componentes:** O prompt define botão pill e CTA textual, mas não define outros componentes reutilizáveis (cards de depoimento, badges, phone frames). Isso pode gerar inconsistências na implementação.
- **Espaçamento:** Não há menção de sistema de spacing (8px grid, padding entre seções, margens internas). Isso vai causar inconsistência visual.

---

## 5. Pontos de Conversão

**CTAs identificados:**
1. Navbar — botão CTA verde (bom, sempre visível)
2. Feature 1 — CTA textual verde (fraco, pode passar despercebido)
3. Movimento Global — "Baixar DolarApp" (posição ruim, seção 10 de 11)

**Problemas:**
- **Apenas 3 CTAs em 11 seções é muito pouco.** A regra geral é ter um CTA visível a cada 2-3 scrolls.
- **Nenhum CTA no Hero** (já mencionado).
- **Nenhum CTA após o Social Proof** — momento de maior confiança do usuário, desperdiçado.
- **Nenhum CTA após a Calculadora** — o usuário acabou de ver quanto economiza e não tem como agir.

**Sugestão:** Adicionar CTAs após as seções 2 (Hero), 7 (Social Proof) e 8 (Calculadora). Não precisa ser intrusivo — pode ser um botão inline.

---

## 6. O que está Faltando

1. **Menu hamburger mobile** — já mencionado.
2. **Sistema de spacing** — definir padding entre seções (ex: 80px desktop, 48px mobile).
3. **Estados de hover/focus para acessibilidade** — o prompt só menciona hover em logos de mídia.
4. **Skip to content / acessibilidade básica** — sem menção de ARIA labels, alt texts, contraste.
5. **CTA sticky ou floating no mobile** — em páginas longas como essa, um botão fixo no rodapé mobile é essencial.
6. **Seção de FAQ** — o navbar linka para FAQ mas não existe uma seção de FAQ na página.
7. **Microinterações na calculadora** — como o usuário interage? Input numérico? Slider? Precisa definir.
8. **Loading/performance** — 3 mockups de celular + fotos de destinos + avatares. Sem menção de lazy loading.

---

## 7. Sugestões Concretas (Priorizadas)

| Prioridade | Sugestão | Impacto |
|---|---|---|
| ALTA | Adicionar CTA no Hero | Conversão |
| ALTA | Adicionar CTA após Social Proof e Calculadora | Conversão |
| ALTA | Adicionar menu hamburger no mobile | Navegação |
| ALTA | Resolver o "vídeo simulado" — ou é vídeo real ou não finja ser | Confiança |
| MÉDIA | Mover "Por que [PRODUTO]?" para depois das features | Narrativa |
| MÉDIA | Reduzir tons de cinza escuro de 4 para 2 | Consistência |
| MÉDIA | Definir sistema de spacing (8px grid) | Consistência |
| MÉDIA | Adicionar CTA sticky no mobile | Conversão mobile |
| BAIXA | Definir tipografia mobile para subtítulos de seção | Responsividade |
| BAIXA | Considerar condensar seções Mídia + Movimento Global | Simplificação |
| BAIXA | Adicionar lazy loading para imagens | Performance |

---

## Resumo Executivo

O prompt é **sólido na estrutura geral** e no design system básico. Os principais problemas são:

1. **Falta de CTAs em momentos críticos** — especialmente no Hero e após Social Proof
2. **Fluxo narrativo com "Por que?" antes de "O que"** — inverte a lógica de convencimento
3. **Vídeo simulado falso** — gera frustração e quebra confiança
4. **Mobile subestimado** — sem hamburger, sem CTA sticky, sem definição de tipografia responsiva para subtítulos

Nenhum desses problemas exige reescrever o prompt do zero. São ajustes cirúrgicos que melhorariam significativamente a experiência e a taxa de conversão.
