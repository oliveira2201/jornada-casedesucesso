# Jornada Case de Sucesso: página do produto (design)

Data: 2026-08-19. Status: aprovado em brainstorm com o Felipe.

## Contexto e decisão

A Agência Case de Sucesso (casedesucesso.com, dark + laranja #E8612A, "Marketing que gera case de sucesso") vai vender um produto novo: o funil completo done-for-you que foi deliberadamente RETIRADO da home do orbyhub.com.br (que agora vende a plataforma do lead pra frente). Aqui a promessa inverte: a agência faz o anúncio, a página, o atendimento por IA, a qualificação e o relatório, rodando sobre a Orby, tecnologia própria. O cliente só fecha.

Decisões tomadas:

- **Escopo:** página NOVA do produto; a home institucional da agência continua como está. Publicação inicial em `jornada.vexvendas.com.br` (Coolify 91 + Cloudflare, tudo na mão do Felipe); quando houver acesso ao DNS do casedesucesso.com (host atual: 162.241.203.50, fora da nossa infra), aponta pra rota/subdomínio definitivo.
- **Produto:** "Jornada Case de Sucesso". Assinatura CONTÍNUA com permanência mínima de 3 meses; os primeiros 90 dias são a RAMPA nomeada (o Método CASE monta e acelera o funil), do dia 91 em diante a operação continua com a agência tocando. NÃO é programa que termina: montar o funil é o custo pesado e só se paga na permanência (validado: nenhum dos 5 concorrentes analisados vende programa com fim; todos são mensalidade contínua).
- **Preço:** não aparece na página (padrão do estrato das micro aceleradoras, R$ 800 a R$ 3.000/mês). O diagnóstico gratuito é a porta.
- **Marco dos 90 dias:** o "case documentado" do cliente, com números do relatório. É o gancho natural pra autorização de publicação de case.

## O mercado (síntese do estudo + pesquisa de referências)

- Estrato alvo: micro aceleradoras SwaS (Promeusite, Vértice Escala, SetupIA, M4), R$ 800 a R$ 3.000/mês, funil completo. Fraqueza estrutural delas: tecnologia ALUGADA (GoHighLevel, ZapGPT, white-label). Nossa vantagem: a Orby é nossa.
- Espaços vagos que NENHUM concorrente ocupa e a página ocupa: (1) nomear a tecnologia por trás; (2) o funil de ponta a ponta numa peça visual só; (3) responder "e depois que montar, quem cuida?"; (4) FAQ com objeção real de fundo de funil ("a conta de anúncio e o número são de quem quando eu sair?"; resposta: SEUS, sempre).
- Clichês banidos: "enquanto você dorme" (3 de 5 usam), percentuais sem base, depoimento com foto de banco, "aceleradora" sem mecanismo, gradiente SaaS genérico, travessão, emoji.
- Réguas herdadas do trabalho da home Orby: métrica de cliente só RELATIVA (nunca volume absoluto), contada por contato, com causa da plataforma; cases com @ do Instagram verificável; nada de depoimento inventado.

## Estrutura da página (blocos)

1. **Hero.** Kicker: "JORNADA CASE DE SUCESSO". Headline na linha de "Seu negócio é o próximo case de sucesso." com acento na palavra da marca. Sub: "A gente faz o anúncio, a página, o atendimento por IA e a qualificação, e te entrega o lead pronto e o relatório de tudo. Você só fecha." CTA duplo: WhatsApp (conversa com a IA) + "Quero meu diagnóstico gratuito".
2. **Faixa de confiança.** Números institucionais que o site da agência JÁ publica (+15 anos, 225+ clientes, +500 campanhas) + agregados da plataforma Orby.
3. **A dor.** O funil que vaza + a dor específica do público done-for-you: o dono não tem tempo de operar ferramenta, e agência comum entrega relatório bonito sem resultado (eco da seção "desta vez" do site institucional).
4. **A Jornada = Método CASE em 90 dias.** A seção assinatura: timeline das 4 fases do método que a agência já anuncia, com entregáveis e artefatos visuais por fase (mesmo motor do Circuito da home Orby): **C**onhecimento (diagnóstico, raio-x do funil, meta), **A**nálise estratégica (posicionamento e plano), **S**istema & execução (página, anúncio, IA treinada, funil e réguas montados na Orby), **E**volução (tração, remarketing na base, otimização semanal e o case documentado no dia 90). Cores por fase do site institucional (laranja/roxo/verde/azul).
5. **Dia 91 em diante.** A continuidade como argumento: funil não é projeto com fim, é operação; quem ajusta a IA quando o produto muda somos nós. (Ocupa o vazio "e depois?" que nenhum concorrente responde.)
6. **Tecnologia própria.** "A Jornada roda na Orby, plataforma nossa, não alugada": rastreio do clique à venda, IA que atende e qualifica, funil, remarketing, relatório integrado. Sem citar concorrente ou white-label pelo nome.
7. **Relatório de tudo.** Transparência: de onde veio o lead, o que a IA falou, custo por lead qualificado por anúncio, funil em reais. Shots reais da plataforma.
8. **Cases.** Os 4 cards já validados (Lux Residence, Vox Embalagens, Tenda Gospel, Espaço Fit) com métrica relativa e @ do Instagram clicável em nova aba.
9. **Como começa.** Diagnóstico gratuito → proposta com meta escrita → kickoff da rampa de 90 dias. Permanência mínima de 3 meses dita com todas as letras (honestidade de expectativa, padrão Vértice/Nagase).
10. **FAQ + CTA final.** Perguntas de fundo de funil: de quem é a conta de anúncio e o número quando eu sair (seus, sempre); o que acontece depois dos 90 dias; a verba de mídia é à parte da mensalidade (sim, e dizemos o mínimo recomendado na proposta); funciona no meu segmento; e minha base atual (entra no remarketing desde a rampa).

## Direção visual

Identidade do casedesucesso.com atual, não da Orby: display condensado **Bebas Neue** nos títulos, **DM Sans** no corpo, Inter nos rótulos em caixa alta; laranja #E8612A como marca e CTA; hero escuro (#0a0907/#141210) e seções alternando branco #FFFFFF e bege #FDF8F5; as 4 cores das fases do método (laranja #E8612A, roxo #7C3AED, verde #16A34A, azul #2563EB); verde para números de resultado. Motor de animação portado da home Orby: fio da jornada desenhado no scroll (laranja fechando em verde), reveals, parallax discreto, transcript de WhatsApp encenado, tudo com `prefers-reduced-motion`. A página deve parecer FILHA do site institucional (mesma família tipográfica e de cor), não um template SaaS.

## Técnica

- Site estático: um HTML único autossuficiente (padrão dos nossos drafts: CSS e JS inline, imagens em pasta), sem framework: é uma página só.
- Repo novo `sites/jornada-casedesucesso` (este diretório), deploy como app no Coolify do 91 (nginx estático ou serve), domínio `jornada.vexvendas.com.br` criado via API da Cloudflare.
- GTM da agência (GTM-P5T8W4LR, o mesmo do site institucional) + orby.js com pub key própria: a página come a própria ração.
- CTA WhatsApp: número institucional da agência (55 11 2770-0941, o mesmo do site atual), link wa.me puro com texto pré-preenchido; o bot Orby por trás é tarefa separada. OG image própria na identidade da página.
- Assets a obter do site atual: logo (SVG/PNG do alvo) e favicon; extraível do bundle público do casedesucesso.com.

## Fora de escopo

Mexer no casedesucesso.com atual, preço na página, área de membros, o bot qualificador do WhatsApp (motor pronto, plugagem é outra tarefa), migração de DNS do domínio definitivo.

## Critérios de aceite

- Página no ar em jornada.vexvendas.com.br com os 10 blocos, identidade Case de Sucesso e o fio da jornada animado.
- Zero itens da lista "cara de IA"; zero travessão; zero emoji; zero número absoluto de operação de cliente; zero depoimento inventado.
- As 4 fases da seção Jornada usam os nomes e cores do Método CASE do site institucional.
- FAQ responde a posse da conta de anúncio/número e o pós-90 dias.
- `prefers-reduced-motion` desliga as animações; mobile 390px sem scroll lateral; Lighthouse mobile ≥ 0.85.
- GTM e orby.js disparando (conferível no preview do GTM e no tracking da Orby).
