# Assistente de gestão da empresa — guia de instalação e uso

Este kit prepara o **Claude Code** (aba **Code** do aplicativo Claude para Mac) para atuar como
administrador e analista da sua empresa, com base nos seus documentos.

**O que este kit é:** uma pasta de projeto com instruções (`CLAUDE.md`), procedimentos prontos
(skills) e um registro de decisões versionado com Git.

**O que este kit não é:** não treina o Claude e não é um MCP. O Claude lê seus documentos quando
precisa e segue as regras escritas aqui. MCP só entra numa fase futura, se for preciso conectar
sistemas externos (Google Drive, planilhas online, CRM).

---

## O que tem dentro

| Pasta / arquivo | Para que serve |
|---|---|
| `CLAUDE.md` | Papel do Claude e regras de resposta. Lido em toda conversa. |
| `empresa/mapa-da-empresa.md` | Resumo do negócio. Você preenche uma vez e atualiza quando mudar. |
| `documentos/` | Seus arquivos originais. **Fica fora do Git** e o Claude não pode editá-los. |
| `conhecimento/` | Fichas-resumo que o Claude cria de cada documento, mais o índice. |
| `decisoes/` | Uma ficha por decisão tomada, com histórico no Git. |
| `estrategia/` | Bússola do negócio e ciclos de 13 semanas do Método Rumo. |
| `testes/` | Perguntas para conferir se as respostas estão corretas. |
| `.claude/skills/` | Procedimentos prontos (ver abaixo). |
| `.claude/settings.json` | Instala os plugins oficiais da Anthropic e bloqueia a edição de `documentos/` e o `git push`. |

### Skills incluídas

| Skill | Como usar | O que faz |
|---|---|---|
| `catalogar-documentos` | Digite `/catalogar-documentos financeiro` | Lê até 10 documentos da pasta, cria fichas e atualiza o índice |
| `analisar-documento` | Peça "analise o arquivo X" | Modo guiado: perguntas uma a uma, depois números, implicações, riscos e próximo passo |
| `apoio-decisao` | Pergunte "devo fazer X?" | Modo guiado: perguntas uma a uma, depois opções, riscos, recomendação e contraponto |

### Plugins oficiais da Anthropic (instalação automática)

| Plugin | O que faz |
|---|---|
| `document-skills` | Lê e cria planilhas (xlsx), apresentações (pptx), PDFs e documentos Word (docx) |
| `marketing` | Planejamento de campanhas, criação de conteúdo, relatórios de desempenho e análise de concorrentes |
| `small-business` | Assistente para pequenas empresas: saúde do negócio (`business-pulse`), briefing semanal (`monday-brief`), caixa, vendas, relatórios, contratação. Basta pedir em linguagem comum |

**Atenção:** as skills de impostos, folha e fechamento contábil do `small-business` seguem regras dos Estados Unidos. O Claude está instruído a não usá-las para obrigações no Brasil; nesses assuntos, confirme sempre com o contador.

Os três estão declarados em `.claude/settings.json`. Ao abrir a pasta e confirmar que confia nela, o Claude Code baixa e ativa os plugins sozinho.
| `registrar-decisao` | Digite `/registrar-decisao título` | Salva a decisão em `decisoes/` e faz o commit no Git |
| `metodo-rumo` | Digite `/metodo-rumo` (ou peça "quero planejar o trimestre") | Planejamento estratégico em ciclos de 13 semanas, em modo guiado |

---

## Instalação (Mac)

Cada passo traz: objetivo, o que fazer, onde, resultado esperado, como verificar e erros comuns.

### Passo 0 — Privacidade da conta

- **Objetivo:** evitar que os documentos da empresa sejam usados para treinar modelos.
- **O que fazer:** nas configurações de privacidade da conta Claude, desative a opção de ajudar a melhorar o Claude ("Help improve Claude").
- **Onde:** claude.ai ou aplicativo Claude, em Configurações → Privacidade.
- **Resultado esperado:** opção desligada. Com ela desligada, a retenção de dados é de 30 dias; ligada, até 5 anos.
- **Verificar:** reabra a tela e confirme que continua desligada.
- **Atenção:** a mudança vale para conversas novas ou retomadas.

### Passo 1 — Conferir o Git

- **Objetivo:** ter o Git, que guarda o histórico das decisões e instruções.
- **O que fazer:** abra o app **Terminal** e digite `git --version`, depois Enter.
- **Resultado esperado:** algo como `git version 2.x.x`.
- **Erro comum:** se o Mac oferecer instalar as "ferramentas de linha de comando", aceite, aguarde terminar e rode `git --version` de novo.

### Passo 2 — Colocar a pasta no lugar

- **Objetivo:** ter o projeto numa pasta fixa.
- **O que fazer:** descompacte o kit e mova a pasta `assistente-empresa` para `Documentos`.
- **Verificar:** a pasta contém `CLAUDE.md` e `README.md`. As pastas e arquivos que começam com ponto (`.claude`, `.gitignore`) ficam ocultos no Finder; para vê-los, pressione `Cmd + Shift + .` (ponto).

### Passo 3 — Abrir o projeto no Claude

- **Objetivo:** iniciar o Claude Code dentro da pasta do projeto.
- **O que fazer:** abra o aplicativo Claude, clique na aba **Code** e escolha a pasta `assistente-empresa`.
- **Atenção:** se aparecer uma pergunta sobre confiar na pasta (workspace trust), **aceite**. Sem isso, os plugins oficiais não são instalados.
- **Verificar:** pergunte "Quais são as suas regras neste projeto?". A resposta deve mencionar fontes, Fato/Inferência/Premissa e a pasta `documentos/` como somente leitura.
- **Erro comum:** se ele não citar essas regras, a pasta escolhida não é a certa (precisa ser a que contém o `CLAUDE.md`).

### Passo 4 — Iniciar o histórico (Git)

- **O que fazer:** peça ao Claude: *"Inicialize um repositório Git nesta pasta e faça o primeiro commit com a mensagem 'ajuste: estrutura inicial'."*
- **Resultado esperado:** o Claude roda `git init` e `git commit` e mostra o resultado.
- **Verificar:** peça *"Mostre o git log"*. Deve aparecer um commit.
- **Atenção:** confira na lista do commit que **nenhum** arquivo de `documentos/` foi incluído (só `LEIA-ME.md`).

### Passo 5 — Conferir skills e plugins

- **Objetivo:** confirmar que as skills do projeto e os plugins oficiais estão ativos.
- **O que fazer:** feche a conversa, abra uma nova na mesma pasta (os plugins são baixados em segundo plano na primeira vez) e pergunte *"Quais skills estão disponíveis?"*
- **Resultado esperado:** as 5 skills do projeto, as skills `xlsx`, `pptx`, `pdf` e `docx` e as skills dos plugins `marketing` e `small-business`.
- **Como verificar de outro jeito:** clique no **+** ao lado da caixa de mensagem → **Plugins** → **Manage plugins**. Devem aparecer `document-skills`, `marketing` e `small-business`.
- **Se os plugins não aparecerem (plano B):**
  1. Clique no **+** → **Plugins** → **Add plugin** (ou **Browse plugins**), procure `document-skills` e `marketing` e instale com o escopo **deste projeto**.
  2. Se a busca não encontrar, digite na caixa de mensagem, um por vez:
     ```
     /plugin marketplace add anthropics/skills
     /plugin install document-skills@anthropic-agent-skills
     /plugin marketplace add anthropics/knowledge-work-plugins
     /plugin install marketing@knowledge-work-plugins
     /plugin install small-business@knowledge-work-plugins
     ```
  3. Se nada disso funcionar no app, fale com o consultor antes de seguir.
- **Observação:** as skills `pdf` e `xlsx` também podem aparecer uma segunda vez, vindas da conta claude.ai. Isso é normal e não atrapalha.

### Passo 6 — Preencher o mapa da empresa

- **O que fazer:** peça *"Me entreviste para preencher empresa/mapa-da-empresa.md, uma pergunta por vez."*
- **Verificar:** abra o arquivo e confira se está correto e curto. Depois peça o commit: *"Faça commit do mapa."*

### Passo 7 — Primeiro lote de documentos

- **O que fazer:** copie **de 20 a 50 documentos importantes** para as subpastas de `documentos/` (ver `documentos/LEIA-ME.md`). Depois digite `/catalogar-documentos financeiro` (troque pela pasta desejada).
- **Resultado esperado:** fichas em `conhecimento/financeiro/` e o índice atualizado.
- **Verificar:** abra duas fichas e confira os números com os originais.
- **Erro comum:** apresentações muito pesadas podem demorar ou falhar. O arquivo aparece em "Não lidos" no índice. Exportar a apresentação para PDF costuma resolver.

### Passo 8 — Validar

- Preencha `testes/perguntas-de-validacao.md` com 5 a 10 perguntas cujas respostas você já conhece.
- Faça cada pergunta em uma conversa nova e marque o resultado.
- **Só amplie para o restante dos documentos quando a maioria das respostas estiver certa e com a fonte correta.**

---

## Uso no dia a dia

### Modo guiado: aprender analisando

Em pedidos de **análise** ou de **decisão**, o Claude não entrega a resposta de imediato. Ele:

1. lê os documentos;
2. faz **uma pergunta por vez** (o que você espera encontrar, qual número olharia primeiro, o que explica a mudança, quais opções você vê);
3. comenta cada resposta em poucas linhas, explicando o conceito de gestão envolvido;
4. depois de 3 a 5 perguntas, entrega a análise completa e mostra onde a sua leitura coincidiu com os dados e onde vale olhar de outro jeito.

Perguntas rápidas ("qual foi o faturamento de agosto?") recebem resposta direta.
Com pressa? Diga **"resposta direta"** e ele pula as perguntas naquele pedido.

### Método Rumo: o ritmo da gestão

O planejamento segue ciclos de 13 semanas: 12 de execução e 1 de revisão.

1. **Bússola** (uma vez): propósito, visão em 3 anos, cliente ideal, indicadores vitais e o que a empresa não faz.
2. **Plano do trimestre** (início do ciclo): até 3 objetivos, de 2 a 4 resultados-chave com número, táticas semanais e pré-mortem.
3. **Revisão semanal** (sexta ou segunda): placar de execução (meta de 85%), vitórias, travas e as 3 entregas da próxima semana.
4. **Revisão mensal** (semanas 4, 8 e 12): painel de números e a decisão de manter, ajustar ou abandonar cada objetivo.
5. **Semana 13**: nota de 0 a 1 em cada resultado-chave; parar, começar, continuar; rascunho do próximo ciclo.

Digite `/metodo-rumo` e o Claude identifica em que ponto você está e conduz o ritual certo, uma pergunta por vez, usando os números dos seus documentos.

### Exemplos

- **Pergunta rápida:** "Qual foi o faturamento de setembro comparado a agosto?"
- **Analisar algo novo:** coloque o arquivo em `documentos/<area>/` e peça "analise documentos/marketing/relatorio-outubro.pdf".
- **Decidir:** "Devo aumentar o orçamento de anúncios no próximo trimestre?" e, no fim, `/registrar-decisao aumento-orcamento-anuncios`.
- **Documentos novos:** rode `/catalogar-documentos <pasta>` de tempos em tempos.
- **Como está o negócio:** "Me dê um panorama do negócio esta semana" (usa o `small-business`).
- **Planejar:** `/metodo-rumo plano` no início do trimestre; `/metodo-rumo semana` toda sexta.
- **Trocar de assunto:** digite `/clear` para começar uma conversa limpa. Isso economiza o limite de uso.

## Boas práticas

- Mantenha o `CLAUDE.md` e o mapa curtos. Instrução longa é seguida com menos fidelidade.
- Se o Claude errar a mesma coisa duas vezes, acrescente uma regra curta ao `CLAUDE.md`.
- Analisar muitos documentos consome o limite do plano. Catalogue aos poucos.
- Faça cópia de segurança de `documentos/` fora deste projeto.

## Fase 2 (somente depois da validação)

- **Conectores (MCP):** Google Drive, planilhas online ou CRM, se os documentos passarem a viver nesses sistemas.
- **Repositório remoto privado** (GitHub privado), se for preciso acessar o histórico de outro computador.

Cada item desses aumenta o contexto carregado e o consumo. Instale um de cada vez e só se houver necessidade comprovada.

## Solução de problemas

| Sintoma | Causa provável | O que fazer |
|---|---|---|
| Responde sem citar fonte | Regra perdida em conversa longa | `/clear` e pergunte de novo |
| Diz que não achou um número que existe | Documento ainda sem ficha | `/catalogar-documentos <pasta>` |
| Skill não aparece | Pasta errada aberta no app | Reabra a pasta que contém o `CLAUDE.md` |
| Plugins oficiais não aparecem | Confiança na pasta não aceita, ou download ainda em andamento | Abra uma conversa nova; se persistir, use o plano B do passo 5 |
| Perguntas demais para algo simples | Modo guiado ativado | Diga "resposta direta" |
| Commit inclui documentos | `.gitignore` ausente ou alterado | Peça ao Claude para conferir o `.gitignore` e refazer o commit |
| Limite de uso acaba rápido | Lotes grandes ou conversas longas | Lotes menores e `/clear` entre assuntos |

## Referências oficiais (consultadas em 27/10/2026)

- Visão geral do Claude Code: https://code.claude.com/docs/en/overview
- Memória e CLAUDE.md: https://code.claude.com/docs/en/memory
- Skills: https://code.claude.com/docs/en/skills
- Plugins: https://code.claude.com/docs/en/plugins/install
- Plugins declarados no repositório: https://code.claude.com/docs/en/plugins/org
- Skills oficiais da Anthropic: https://github.com/anthropics/skills
- Plugins de trabalho da Anthropic: https://github.com/anthropics/knowledge-work-plugins
- Boas práticas: https://code.claude.com/docs/en/best-practices
- Uso de dados: https://docs.claude.com/en/docs/claude-code/data-usage
