# Post LinkedIn — Workflow Claude Browser + Claude Code Agent Teams

---

Hoje testei um fluxo de trabalho que mudou minha percepção sobre o que dá pra fazer com AI antes de escrever uma linha de código.

**O ponto de partida:** encontrei uma landing page de fintech que achei incrível. Rodei o plugin Claude Browser nela. Em segundos, tinha uma análise completa da estrutura, identidade visual, seções, componentes e comportamentos — tudo documentado.

**O que fiz a seguir:** transformei essa análise em um prompt detalhado para gerar uma landing page equivalente em HTML + CSS + JS puro, num único arquivo. 11 seções. Design system completo. Animações. Calculadora interativa. Responsividade.

Um prompt longo, bem estruturado. Achei que estava pronto pra gerar.

**Mas antes de rodar**, decidi testar algo diferente.

Abri o Claude Code, usei o Agent Teams — uma feature experimental que permite spawnar múltiplos agentes trabalhando em paralelo — e mandei o prompt para dois agentes simultâneos:

→ **Frontend Agent** — revisar viabilidade técnica, complexidade, riscos de implementação e acessibilidade

→ **UX/Design Agent** — revisar fluxo narrativo, hierarquia visual, pontos de conversão e consistência do design system

Em minutos, os dois entregaram relatórios independentes.

**O que eles encontraram antes de eu gerar qualquer coisa:**

🔴 O verde vibrante (#00E676) em fundo branco tinha contraste de 1.8:1 — longe do mínimo WCAG de 4.5:1. O site inteiro seria ilegível nas seções de features.

🔴 O texto muted (#A0A0A0) também falhava em contraste — 4.0:1 quando precisava de 4.5:1.

🔴 O hero não tinha nenhum CTA. O usuário chegava, lia, e... nada para fazer.

🔴 A seção "Por que [Produto]?" aparecia antes das features — o usuário ainda não sabia *o que* era o produto.

🔴 O "player de vídeo simulado" era uma div escura com ícone de play que não reproduzia nada. Um clique de frustração garantido.

🔴 Apenas 3 CTAs em 11 seções. A calculadora ficava *depois* do social proof, quebrando o momentum de conversão.

🔴 4 tons de cinza escuro diferentes no design system. Sem max-width de container. Sem sistema de espaçamento.

Resultado: o prompt original teria gerado uma página visualmente bonita, mas com problemas sérios de acessibilidade, conversão e consistência.

Com os relatórios em mãos, revisei o prompt cirurgicamente. Corrigi os contrastes, adicionei CTAs nos momentos certos, reordenei as seções para uma narrativa que faz sentido, simplifiquei os elementos mais arriscados.

**Agora sim:** o prompt está pronto pra gerar.

O que me impressionou não foi a capacidade individual de cada agente — foi o fluxo completo. Um plugin que lê o mundo real → um prompt que captura o que foi lido → agentes especializados que revisam antes de executar → um output com muito mais chance de estar certo na primeira tentativa.

Isso não é só automação. É um processo de revisão que normalmente levaria horas de trabalho manual, comprimido em minutos.

Estamos só começando.

---

#ClaudeCode #AgentTeams #AI #InteligenciaArtificial #VibeCoding #PromptEngineering #LandingPage #UXDesign #Frontend #Acessibilidade #WCAG #Fintech #ProductDesign #Automacao #AIAgents #ClaudeBrowser #DesignSystem #WebDevelopment #NoCode #FutureOfWork
