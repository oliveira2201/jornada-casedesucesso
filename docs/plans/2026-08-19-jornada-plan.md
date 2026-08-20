# Jornada Case de Sucesso: Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Colocar no ar `jornada.vexvendas.com.br`: a página do produto "Jornada Case de Sucesso" (funil done-for-you da Agência Case de Sucesso, rodando sobre a Orby).

**Architecture:** Site estático de um HTML único autossuficiente (CSS e JS inline, imagens locais), na identidade do casedesucesso.com. Repo próprio em `/root/projetos/sites/jornada-casedesucesso`, deploy como app estático no Coolify do 91, DNS via API da Cloudflare.

**Tech Stack:** HTML/CSS/JS vanilla (motor de animação portado de `apps/vex/landing/public/home-v1.html`), Google Fonts (Bebas Neue, DM Sans, Inter), Coolify (static build pack), Cloudflare DNS.

**Spec:** `/root/projetos/sites/jornada-casedesucesso/docs/2026-08-19-jornada-case-de-sucesso-design.md`.

## Global Constraints

- Copy PT-BR acentuada; PROIBIDO travessão (—); sem emoji; sem número absoluto de operação de cliente; sem depoimento inventado; clichês banidos: "enquanto você dorme", "máquina de vendas", percentuais sem base, "aceleradora" sem mecanismo.
- Identidade: Bebas Neue (títulos, uppercase), DM Sans (corpo), Inter (rótulos caixa alta); laranja #E8612A (marca/CTA); hero escuro #0a0907/#141210; seções alternando #FFFFFF e #FDF8F5; cores das fases: C=#E8612A, A=#7C3AED, S=#16A34A, E=#2563EB; verde #16A34A pra números de resultado.
- Toda animação respeita `prefers-reduced-motion`; mobile first (390px sem scroll lateral).
- Produto: assinatura contínua, permanência mínima de 3 meses, rampa de 90 dias (Método CASE); sem preço na página.
- Commits em inglês no repo novo; push e deploy fazem parte do pedido do Felipe ("faça aí"); nada de deploy em outros apps.

---

### Task 1: Repo, assets e esqueleto

**Files:**
- Create: `index.html` (esqueleto), `assets/` (logo, favicon), `.gitignore`, `README.md` (3 linhas: o que é, como deployar)

**Interfaces:**
- Produces: repo git inicializado; `assets/logo.png` e `assets/favicon.png` reais da agência; `index.html` com `<head>` completo (title `Jornada Case de Sucesso | do anúncio ao cliente fechado`, description, OG/Twitter apontando `assets/og.png` que a Task 4 gera, GTM da agência, fontes).

- [ ] **Step 1:** `git init` em `/root/projetos/sites/jornada-casedesucesso`; criar `.gitignore` (`node_modules`, `.DS_Store`).
- [ ] **Step 2:** Baixar os assets do site atual: `curl -sL https://casedesucesso.com/favicon.png -o assets/favicon.png` e o og `https://casedesucesso.com/og-image.png -o assets/og-agencia.png` (referência). A logo: inspecionar `https://casedesucesso.com/assets/index-D1_rqhg1.js` com grep por `logo|.png|.svg|.webp` e baixar o asset da wordmark; se o bundle não expuser, recortar a logo do og-image (topo esquerdo) com PIL. Validar com `python3 -c "from PIL import Image; Image.open('assets/logo.png').show..."` (só size/mode).
- [ ] **Step 3:** `index.html` com head: charset/viewport; title/description; canonical `https://jornada.vexvendas.com.br/` (trocar quando o domínio definitivo apontar); OG/Twitter (imagem `/assets/og.png`, 1200x630); GTM `GTM-P5T8W4LR` (snippet head + noscript body, igual ao do site institucional); `<link>` Google Fonts `Bebas+Neue`, `DM+Sans:wght@400;500;700`, `Inter:wght@600;700`; favicon.
- [ ] **Step 4:** Commit `chore: repo skeleton with agency assets and head`.

### Task 2: A página completa (copy + CSS identidade)

**Files:**
- Modify: `index.html` (corpo inteiro + `<style>`)

**Interfaces:**
- Consumes: head/assets da Task 1. Referência visual do design system a herdar: screenshot e CSS do site atual (paleta na Global Constraints; NÃO copiar CSS da Orby, só a MECÂNICA das seções).
- Produces: ids `#hero #confianca #dor #jornada #continuidade #tecnologia #relatorio #cases #comeco #faq`; classes de animação `.reveal`, `.fio-path`, `.chat-play` com `.msg.in/.msg.out` e `.typing` (contrato do motor da Task 3).

- [ ] **Step 1: Hero (`#hero`, fundo escuro).** Kicker Inter caixa alta laranja: `JORNADA CASE DE SUCESSO`. H1 Bebas Neue: `SEU NEGÓCIO É O PRÓXIMO <span class="acc">CASE DE SUCESSO.</span>` (acc = laranja). Sub DM Sans: `A gente faz o anúncio, a página, o atendimento por IA e a qualificação, e te entrega o lead pronto e o relatório de tudo. Você só fecha.` CTA primário (wa.me puro, id `#hero-wa`): `Falar com a nossa IA agora` → `https://wa.me/551127700941?text=` + encode de `Olá! Quero conhecer a Jornada Case de Sucesso.` CTA secundário: `Quero meu diagnóstico gratuito` → âncora `#comeco`.
- [ ] **Step 2: Confiança (`#confianca`).** Linha de números institucionais (os MESMOS do site da agência, que já os publica): `+15 anos de mercado`, `225+ clientes atendidos`, `+500 campanhas gerenciadas`, mais `tecnologia própria` como quarto selo (texto, não número). Nota: `Números da Agência Case de Sucesso. Os resultados lá embaixo são medidos pela nossa plataforma.`
- [ ] **Step 3: A dor (`#dor`, fundo bege #FDF8F5).** H2: `VOCÊ JÁ PAGOU AGÊNCIA PRA FAZER POST. AGORA COMPARE.` Corpo: três frustrações em linhas editoriais (sem cards de ícone): `Relatório bonito no fim do mês, resultado que não aparece.` / `Ferramenta nova pra sua equipe operar, que ninguém opera.` / `Lead do anúncio esperando horas por resposta, esfriando de graça.` Fecho serif/itálico DM Sans: `O problema não é o seu anúncio. É tudo que deveria acontecer depois do clique, e não acontece.`
- [ ] **Step 4: A Jornada (`#jornada`, fundo branco).** Kicker: `O MÉTODO CASE, EM 90 DIAS`. H2: `A RAMPA QUE MONTA E ACELERA O SEU FUNIL.` Lead: `As quatro fases do nosso método, aplicadas nos primeiros 90 dias da assinatura. Cada fase com entregável definido e a cor dela.` Timeline vertical de 4 fases (letra gigante Bebas na cor da fase + título + entregáveis + etiqueta "Você recebe"), com o fio SVG ao lado:
  - `C · Conhecimento` (#E8612A): `Raio-x do seu funil: de onde vem o lead, onde ele morre, quanto custa. Meta definida por escrito.` Você recebe: `o diagnóstico documentado e a meta.`
  - `A · Análise estratégica` (#7C3AED): `Posicionamento, oferta e plano: o que anunciar, pra quem, com qual página e qual conversa.` Você recebe: `o plano da campanha, antes de gastar 1 real de mídia.`
  - `S · Sistema e execução` (#16A34A): `Montamos a página, os anúncios, a IA treinada no seu negócio e o funil com réguas de follow-up e remarketing, tudo na nossa plataforma.` Você recebe: `o funil inteiro no ar, com lead qualificado caindo na agenda.`
  - `E · Evolução` (#2563EB): `Otimização semanal guiada pelo relatório: verba realocada pro anúncio que traz quem fecha, régua ajustada, base reaquecida.` Você recebe: `no dia 90, o seu case documentado, com números.`
- [ ] **Step 5: Dia 91 (`#continuidade`, fundo escuro).** H2: `E DEPOIS DOS 90 DIAS? É AÍ QUE FICA BOM.` Corpo: funil não é projeto com fim, é operação: mercado muda, produto muda, a IA e as campanhas precisam de quem ajuste toda semana. A assinatura continua com a gente operando e o relatório provando. Linha de honestidade: `Permanência mínima de 3 meses: é o tempo da rampa. Depois, fica quem está vendo resultado.`
- [ ] **Step 6: Tecnologia (`#tecnologia`).** Kicker: `TECNOLOGIA PRÓPRIA`. H2: `A JORNADA RODA NA ORBY. PLATAFORMA NOSSA, NÃO ALUGADA.` Corpo: agência comum monta seu funil em ferramenta alugada de terceiro; quando a plataforma muda o preço ou o recurso, o funil é refém. A Orby é nossa: rastreio do clique à venda, IA que atende em segundos e qualifica, funil, remarketing na base e relatório integrado, evoluindo na velocidade dos nossos clientes. Link discreto `orbyhub.com.br` (nova aba).
- [ ] **Step 7: Relatório (`#relatorio`, bege).** H2: `VOCÊ ENXERGA CADA REAL TRABALHANDO.` Lista prose: de onde veio cada lead e qual anúncio o trouxe; o que a IA conversou; custo por lead qualificado, anúncio por anúncio; o funil em reais, etapa por etapa. 2 shots reais da plataforma (copiar `analytics-c-1200.png` e `fluxo-c-1200.png` de `/root/projetos/monorepo/apps/vex/landing/public/shots/` pra `assets/`, com srcset/lazy).
- [ ] **Step 8: IA + transcript (`#tecnologia` ganha ao lado, OU seção própria dentro de `#tecnologia`: manter no MESMO bloco pra página não ficar longa: o `.chat-play` entra como coluna direita da seção Tecnologia).** Transcript encenado (mesma estrutura de bolhas da home Orby, conteúdo novo): cliente 22:41 `Boa noite! Vocês atendem minha região?`; IA 22:41 `Boa noite! Atendemos sim. Me conta rapidinho: qual é o seu negócio?`; cliente 22:42 `Tenho uma clínica odontológica.`; IA 22:42 `Perfeito. Hoje vocês atendem quantos pacientes por semana, em média?`; cliente 22:43 `Umas 60 consultas.`; IA 22:43 `Ótimo. Consigo te mostrar o funil funcionando amanhã às 10h ou às 15h. Qual prefere?` Selo: `22:41 de uma quarta. Lead qualificado e reunião marcada, sem ninguém do time acordado.`
- [ ] **Step 9: Cases (`#cases`, branco).** Mesma estrutura e MESMO conteúdo dos 4 cards validados da home Orby (Lux Residence @luxresidencesenior, Vox Embalagens @voxembalagens, Tenda Gospel @tenda_gospel, Espaço Fit @espacofitacademia1): copiar copy verbatim de `apps/vex/landing/public/home-v1.html` seção `#cases`, re-estilizada na identidade CDS (metric em Bebas na cor verde, cards com borda bege). Intro: `Resultados medidos pela nossa plataforma, na operação real de quem já roda com a gente.`
- [ ] **Step 10: Como começa (`#comeco`, escuro).** 3 passos: `Diagnóstico gratuito: a gente olha seu funil e te mostra onde vaza, com número.` / `Proposta com meta por escrito: o que vamos montar, o que você recebe por fase, e o investimento.` / `Kickoff da rampa: em dias o sistema está no ar; em 90, seu case está documentado.` CTA duplo repetido.
- [ ] **Step 11: FAQ (`#faq`) + CTA final.** `<details>`: `A conta de anúncio e o número de WhatsApp são de quem?` → `Seus, sempre. A campanha roda na SUA conta e o número é SEU. Se um dia sair, leva tudo.` / `O que acontece depois dos 90 dias?` → continuidade da operação (resumo do bloco 5). / `A verba de mídia está inclusa?` → `Não; mensalidade é a operação. O mínimo de verba recomendado pro seu caso sai por escrito no diagnóstico.` / `Funciona no meu segmento?` → qualquer negócio que fecha por conversa; cases de casa de repouso a indústria. / `Minha base atual de contatos entra?` → sim, remarketing na base desde a rampa. CTA final H2: `SEU CONCORRENTE JÁ ESTÁ RESPONDENDO EM SEGUNDOS.` + botões.
- [ ] **Step 12:** Conferir `grep -c "—"` = 0; abrir com server local; commit `feat: full page content and CDS identity`.

### Task 3: Motor de animação

**Files:**
- Modify: `index.html` (CSS de animação + `<script>` antes de `</body>`)

**Interfaces:**
- Consumes: classes `.reveal .fio-path .chat-play .msg.in/.out .typing` da Task 2.

- [ ] **Step 1:** Portar o CSS de animação e o `<script>` INTEIROS de `/root/projetos/monorepo/apps/vex/landing/public/home-v1.html` (blocos `.reveal/.fio-path/.fio-drip/.chat-play` + a media query de `prefers-reduced-motion` + o script de IntersectionObserver/parallax/chat). Adaptar SÓ cores do fio (laranja #E8612A → verde #16A34A no fim) e os seletores de parallax (glow se houver, shots com `[data-parallax]`).
- [ ] **Step 2:** Marcar `.reveal` nas 10 seções com `transition-delay` escalonado; fio na seção `#jornada` acompanhando as 4 fases.
- [ ] **Step 3:** Testar reduced-motion (DevTools) e 390px. Commit `feat: scroll engine ported (reveals, journey line, staged chat)`.

### Task 4: orby.js, OG e SEO

**Files:**
- Modify: `index.html`; Create: `assets/og.png`

**Interfaces:**
- Consumes: página completa.

- [ ] **Step 1:** Gerar pub key de tracking pro site: seguir a skill `orby-tracker` (projeto de tracking no tenant certo do vex_db; se o tenant da agência não existir, usar o tenant Orby/Felipe Pessoal e anotar). Inserir `<script src="https://api.orbyhub.com.br/track/orby.js?key=orby_pub_..."` no head. O CTA wa.me fica SEM classe de cta (o orby.js intercepta wa.me pra ponte site→conversa; não duplicar cta_click).
- [ ] **Step 2:** OG 1200x630 na identidade CDS (fundo escuro, logo, headline `SEU NEGÓCIO É O PRÓXIMO CASE DE SUCESSO.` com o acc laranja, sub curto), gerada com HTML + chromium do playwright (`/root/.cache/ms-playwright/chromium-1223/chrome-linux64/chrome --headless --no-sandbox --screenshot`), salva em `assets/og.png` e referenciada no head.
- [ ] **Step 3:** JSON-LD `Service` (provider Agência Case de Sucesso, areaServed BR). Commit `feat: tracking, OG art and structured data`.

### Task 5: Infra e deploy

**Files:**
- Create: repo no GitHub `oliveira2201/jornada-casedesucesso` (público); app no Coolify 91; registro DNS.

- [ ] **Step 1:** `gh repo create oliveira2201/jornada-casedesucesso --public --source . --push` (gh já autenticado na máquina; se não, `git remote add` + push com credencial existente).
- [ ] **Step 2:** DNS: criar `jornada.vexvendas.com.br` A → `91.107.218.63` via API Cloudflare (token/zona em `~/.claude/projects/-root-projetos-monorepo/memory/cloudflare-api.md`), `proxied: false` (deixa o Traefik do Coolify emitir o certificado; liga proxy depois se quiser).
- [ ] **Step 3:** Coolify 91 (token em CLAUDE.md do monorepo, seção Deploy produção): `GET /api/v1/projects` e `GET /api/v1/servers` pra achar uuids; `POST /api/v1/applications/public` com `{project_uuid, server_uuid, environment_name: "production", git_repository: "https://github.com/oliveira2201/jornada-casedesucesso", git_branch: "main", build_pack: "static", domains: "https://jornada.vexvendas.com.br"}`. Se o build_pack static exigir `publish_directory`, usar `/` (index.html na raiz).
- [ ] **Step 4:** Disparar deploy (`POST /api/v1/deploy?uuid=<app>`), acompanhar `GET /api/v1/deployments/<uuid>`; ao terminar, `curl -sI https://jornada.vexvendas.com.br` = 200 e o H1 presente no HTML.
- [ ] **Step 5:** Commit de eventuais ajustes de infra (`chore: deploy config`).

### Task 6: Verificação final

- [ ] **Step 1:** Checklist: `grep -c "—"` = 0; sem emoji; sem número absoluto de cliente; sem depoimento inventado; FAQ com posse da conta/número e pós-90; fases com nomes/cores do Método CASE.
- [ ] **Step 2:** Screenshots (hero, jornada, cases) pro Felipe; reduced-motion e 390px conferidos.
- [ ] **Step 3:** Lighthouse mobile ≥ 0.85 contra a URL viva.
- [ ] **Step 4:** Verificar GTM (requisição gtm.js no HTML) e orby.js (script no head; `curl` na URL do script = 200).
