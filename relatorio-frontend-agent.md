# Revisão Técnica — Prompt de Landing Page (estilo DolarApp)
**Autor:** Frontend Agent — oConselho
**Data:** 28/02/2026

---

## 1. VIABILIDADE TÉCNICA

### Viável sem problemas (complexidade baixa):
- Navbar fixa com backdrop-filter e scroll behavior
- Hero section com texto centralizado
- Seções de features com layout 2 colunas (flexbox/grid)
- Footer com colunas de links
- Scroll suave, IntersectionObserver para fade-in
- Seção de mídia com logos em texto
- Botões pill, CTAs textuais, paleta de cores
- Google Fonts (Inter)

### Viável com cuidado (complexidade média):
- **Mockups de celular em CSS puro (Seções 2, 6, 8):** Funciona, mas exige bastante CSS. O prompt pede 3 phones sobrepostos no hero — isso são ~100-150 linhas de CSS só para essa parte. Resultado tende a ficar "genérico" sem imagens reais.
- **Calculadora interativa (Seção 8):** JS simples com taxa fixa é trivial. O risco é o layout — dois campos + botão circular + mockup com gráfico ao lado é muita coisa para ficar bonito em single-file.
- **Gráfico de linha simulado (Seção 8):** O prompt sugere "canvas ou SVG path". SVG inline com um path hardcoded é a melhor opção. Canvas exigiria mais JS.
- **Cards de avaliação com scroll horizontal mobile (Seção 7):** Funciona com `overflow-x: auto` e `scroll-snap`, mas o prompt não menciona scroll-snap — vale adicionar.

### Potencialmente problemático (complexidade alta):
- **3 phones sobrepostos no hero com "tela interna verde":** A especificação é vaga. "Ligeiramente sobrepostos com o central maior" precisa de posicionamento absoluto cuidadoso e não vai ser responsivo de forma trivial. Em mobile, 3 phones sobrepostos ficam ilegíveis.
- **Avatares conectados por linhas tracejadas (Seção 5):** Linhas tracejadas entre elementos posicionados é complexo em CSS puro. Opções: SVG inline, border com dashes em divs posicionados, ou pseudo-elements. Nenhuma é trivial para ficar bonito e responsivo.
- **Grid de fotos com badges de localização (Seção 10):** Funciona, mas são 6-8 cards com gradientes distintos + badges posicionados. Volume de CSS alto.

---

## 2. RISCOS DE IMPLEMENTAÇÃO

### Vagueza na especificação:
- **"Simular com divs estilizados"** aparece várias vezes sem dimensões exatas. Sem width/height definidos para os phone frames, o LLM vai chutar valores que podem não harmonizar.
- **"Mockup de app"** na seção 6 e 8 — são dois mockups diferentes mas a descrição é similar. Risco de output repetitivo.
- **"Gradientes coloridos simulando fotos de destinos"** — sem especificar quais gradientes, o resultado será aleatório e possivelmente feio.
- **Conteúdo placeholder genérico** — o prompt diz "FinApp" mas usa "DolarApp" em vários exemplos. Inconsistência que pode confundir o modelo.

### Tamanho do arquivo:
- Estimativa: 1500-2500 linhas de HTML+CSS+JS em um único arquivo. Isso está no limite do que modelos geram bem em uma única resposta. **Risco alto de truncamento ou seções finais com qualidade inferior.**

### Responsividade:
- O prompt define apenas 1 breakpoint (768px). Para um site desse porte, seria melhor ter pelo menos 2 (768px e 480px). Os phone mockups e grids vão quebrar em telas muito pequenas.

### Performance:
- `backdrop-filter: blur()` na navbar pode causar repaint issues em scroll, especialmente mobile.
- IntersectionObserver em muitos elementos simultaneamente pode ser pesado se não configurado com threshold adequado.

---

## 3. PROBLEMAS DE ACESSIBILIDADE

### Contraste:
- **#A0A0A0 em #1F1F1F** — ratio ~4.0:1. **Falha em WCAG AA para texto normal (precisa 4.5:1).** Sugestão: usar #B5B5B5.
- **#00E676 em #FFFFFF (seções brancas)** — ratio ~1.8:1. **Falha crítica.** O verde vibrante em fundo branco é praticamente ilegível. Os CTAs textuais verdes em seções brancas vão ter contraste péssimo.
- **#111111 em #00E676 (seção verde)** — ratio ~8.5:1. OK.
- **#FFFFFF em #1F1F1F** — ratio ~13:1. OK.

### Semântica:
- O prompt não menciona landmarks (`main`, `section`, `nav`, `footer` semânticos). Deveria explicitar.
- Não menciona `alt` text para elementos visuais simulados.
- Não menciona `aria-label` para o player de vídeo falso (seção 3) — um div que parece player mas não é precisa de `role="img"` com `aria-label`.
- Calculadora (seção 8) precisa de `label` nos inputs e `aria-live` para o resultado dinâmico.

### Navegação por teclado:
- Não mencionada. Os CTAs textuais e botões precisam de focus states visíveis.
- O seletor de idioma na navbar não tem especificação de como funciona (dropdown? links?) — pode ser inacessível.

---

## 4. SUGESTÕES CONCRETAS DE AJUSTE NO PROMPT

### Críticas (devem ser feitas):

1. **Corrigir o contraste do verde em fundo branco.** Adicionar ao prompt: "Para CTAs verdes em fundo branco, usar #00C853 (verde mais escuro) ou adicionar underline para não depender apenas de cor."

2. **Definir dimensões dos phone mockups.** Adicionar: "Phone frame: width 280px, height 560px para o central, 240x480 para os laterais. Em mobile (< 768px), mostrar apenas 1 phone centralizado."

3. **Limitar a complexidade da Seção 5.** A seção 5 (avatares com linhas tracejadas) é a mais arriscada. Sugestão: substituir por 3 cards simples lado a lado mostrando transferências, sem linhas conectoras.

4. **Adicionar breakpoint mobile small.** Adicionar: "Breakpoint adicional em 480px para ajustes finos em telas pequenas."

5. **Padronizar o nome.** Substituir todas as referências a "DolarApp" por "FinApp" ou escolher um nome e usar consistentemente.

### Recomendadas (melhoram a qualidade):

6. **Especificar scroll-snap para cards mobile:** `scroll-snap-type: x mandatory` nos containers de cards.

7. **Adicionar focus states:** "Todos os elementos interativos devem ter `outline: 2px solid #00E676` com `outline-offset: 2px` no estado :focus-visible."

8. **Simplificar o gráfico da seção 8:** "Usar um SVG path hardcoded simples em vez de canvas."

9. **Definir max-width do container:** O prompt não especifica. Adicionar: "Container principal: max-width: 1200px, margin: 0 auto, padding: 0 24px."

10. **Especificar carregamento de fontes:** "Google Fonts com `display=swap`."

---

## 5. ESTIMATIVA DE COMPLEXIDADE POR SEÇÃO

| Seção | Complexidade | Linhas estimadas | Notas |
|-------|-------------|------------------|-------|
| 1. Navbar | Baixa | ~80 | Scroll behavior é simples |
| 2. Hero | **Alta** | ~200 | 3 phone mockups CSS puro |
| 3. Por quê (verde) | Baixa | ~60 | Player falso é simples |
| 4. Feature 1 (cartão) | Média | ~120 | Cartão CSS com gradiente |
| 5. Feature 2 (transferências) | **Alta** | ~150 | Linhas tracejadas entre avatares |
| 6. Feature 3 (conversão) | Média | ~120 | Phone frame + lista interna |
| 7. Social proof | Média | ~130 | 3 cards + scroll mobile |
| 8. Calculadora | **Alta** | ~200 | JS interativo + gráfico SVG |
| 9. Mídia | Baixa | ~50 | Logos em texto |
| 10. Movimento global | Média | ~120 | Grid de cards com badges |
| 11. Footer | Baixa | ~80 | Layout padrão |
| Global (reset, animações, responsivo) | Média | ~150 | |
| **TOTAL** | | **~1460** | Mínimo realista |

---

## RESUMO EXECUTIVO

O prompt é **bem estruturado e detalhado**, o que é bom para geração por LLM. Os principais riscos são:

1. **Contraste de acessibilidade** do verde (#00E676) em fundo branco — precisa de correção antes de implementar
2. **Tamanho do output** — está no limite do que se gera bem em uma única resposta. Considerar dividir em 2 prompts (seções 1-6 e 7-11) se o resultado vier truncado
3. **Phone mockups e linhas tracejadas** — as seções mais complexas que podem ficar visualmente ruins sem referência visual concreta
4. **Falta de max-width container** — sem isso, o layout vai esticar em telas largas

Com os ajustes sugeridos acima, o prompt tem boa chance de gerar um resultado profissional em uma única iteração.
