# FinApp Landing Page

Landing page de fintech gerada com um workflow de AI end-to-end, usando **Claude Browser** + **Claude Code Agent Teams**.

## Demo

Abra o arquivo `index.html` diretamente no browser — sem dependências, sem build, sem servidor.

## O workflow

### 1. Análise com Claude Browser
O plugin Claude Browser analisou uma landing page de fintech real e extraiu toda a estrutura: identidade visual, seções, componentes, comportamentos e design system.

### 2. Prompt Engineering
A análise virou um prompt detalhado descrevendo 11 seções completas, paleta de cores, tipografia, responsividade e interatividade em JS puro.

### 3. Revisão por Agent Teams (Claude Code)
Antes de gerar qualquer código, dois agentes especializados rodaram em paralelo para revisar o prompt:

**Frontend Agent** — revisão técnica:
- Viabilidade de implementação por seção
- Problemas de acessibilidade (contraste WCAG)
- Riscos de output (vagueza, tamanho, responsividade)
- Sugestões concretas de especificação

**UX/Design Agent** — revisão de UX:
- Fluxo narrativo e lógica de conversão
- Hierarquia visual e consistência do design system
- Pontos de conversão (CTAs) e momentos críticos
- Heurísticas de Nielsen aplicadas

### 4. Prompt revisado e geração
Com os relatórios dos agentes, o prompt foi revisado cirurgicamente. Principais correções:
- Contraste de texto corrigido para passar WCAG AA
- CTA adicionado no hero e após momentos de alta conversão
- Ordem das seções reorganizada (O quê → Por quê → Experimente → Prova)
- Seção verde com ilustração honesta (sem fake video player)
- Hamburger menu mobile, sticky CTA, scroll-snap nos cards
- Sistema de espaçamento e max-width de container definidos

## Estrutura do projeto

```
index.html                  # Landing page completa (HTML + CSS + JS)
prompt-original.md          # Prompt gerado a partir da análise do Claude Browser
prompt-revisado.md          # Prompt após revisão dos agentes
relatorio-frontend-agent.md # Análise técnica do Frontend Agent
relatorio-ux-design-agent.md # Análise de UX/Design do UX Agent
```

## Tecnologias

- HTML5 semântico
- CSS3 (Grid, Flexbox, Custom Properties, IntersectionObserver)
- JavaScript vanilla (sem frameworks)
- Google Fonts — Inter

## Seções da landing page

1. Navbar fixa com blur e menu mobile
2. Hero com 3 phone mockups e CTAs
3. Feature — Pagamento global
4. Feature — Transferências internacionais
5. Feature — Conversão de moedas
6. Por que FinApp? (seção verde)
7. Calculadora interativa BRL → USD
8. Social proof com depoimentos
9. Menções na mídia
10. Movimento global com destinos
11. Footer completo

## Sobre

Projeto demonstrativo de um workflow AI-first para criação de interfaces: análise → prompt → revisão por agentes → geração. Construído com [Claude Code](https://claude.ai/claude-code) e o sistema experimental de Agent Teams.
