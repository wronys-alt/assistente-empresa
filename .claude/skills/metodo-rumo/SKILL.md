---
name: metodo-rumo
description: Conduz o planejamento estratégico e de gestão pelo Método Rumo (ciclo de 13 semanas) — bússola do negócio, plano do trimestre com objetivos e resultados-chave, táticas, pré-mortem e as revisões semanal, mensal e do ciclo. Use quando o usuário quiser planejar o trimestre, definir metas ou objetivos, montar estratégia, fazer a revisão da semana, do mês ou do ciclo, ou perguntar o que priorizar.
argument-hint: "[bussola | plano | semana | mes | ciclo | dia]"
---

# Método Rumo

O Método Rumo transforma estratégia em rotina. O dono define poucos objetivos para 13 semanas, quebra cada um em táticas semanais e mede a execução. Toda semana mede se executou o que planejou. Todo mês confere se os números confirmam o caminho. Na semana 13, avalia o ciclo e desenha o próximo.

## Os quatro horizontes

| Horizonte | Ritual | Pergunta central | Arquivo de instruções |
|---|---|---|---|
| Rumo (3 anos + trimestre) | Bússola e plano do trimestre | Aonde o negócio precisa chegar e como vou medir? | [bussola.md](bussola.md), [plano.md](plano.md) |
| Mês | Painel e revisão mensal | Os números confirmam o rumo? | [mes.md](mes.md) |
| Semana | Revisão e plano semanal | Executei o que planejei? O que muda agora? | [semana.md](semana.md) |
| Ciclo | Semana 13 | O que o ciclo ensinou e qual é o próximo rumo? | [ciclo.md](ciclo.md) |
| Dia | Registro diário | Qual é a única coisa que move o negócio hoje? | seção "Dia" abaixo |

## Três regras do método

1. **Poucos objetivos.** No máximo 3 por ciclo.
2. **Meça a execução, não o esforço.** O placar semanal é a verdade. Referência: 85% das táticas planejadas.
3. **Revise sempre.** Um sistema sem revisão perde a confiança em semanas.

## Como escolher o ritual

- Argumento informado (`$ARGUMENTS`): siga o arquivo correspondente.
- Sem argumento: leia `estrategia/` e decida:
  - não existe `estrategia/bussola.md` → comece pela bússola;
  - não existe plano do ciclo atual → plano do trimestre;
  - existe ciclo em andamento → pergunte qual ritual o dono quer fazer agora.
- Antes de começar, diga em uma linha qual ritual vai conduzir e quanto tempo costuma levar.

## Regras de condução (todos os rituais)

- **Uma pergunta por vez.** Espere a resposta antes da próxima. Depois de cada resposta, comente em 2 ou 3 linhas e explique o conceito de gestão envolvido, em linguagem simples.
- **Use os dados da empresa.** Antes de perguntar sobre números, procure em `conhecimento/` e nos documentos. Mostre o dado com fonte e pergunte se ele confere ("Pelas planilhas, a margem de setembro foi X% — esse é o ponto de partida certo?").
- **Desafie com respeito.** Se um objetivo não tiver número, se houver mais de 3 objetivos ou se uma tática não começar com verbo, aponte e ajude a reescrever.
- **O dono decide.** Você propõe, questiona e mostra dados; a escolha final é dele.
- **Salve só com confirmação.** Mostre o texto final e peça "posso salvar?" antes de gravar.
- **Faça o commit depois de salvar:** `git add estrategia/ && git commit -m "rumo: <ritual> <ciclo/semana/mês>"`.
- Pule o modo guiado apenas se o dono pedir "resposta direta".

## Onde salvar

```
estrategia/
├── bussola.md                    (revista a cada ciclo)
└── ciclo-AAAA-NN/                (ex.: ciclo-2026-04)
    ├── plano.md                  (objetivos, resultados-chave, táticas, pré-mortem, compromisso)
    ├── semana-01.md … semana-12.md
    ├── mes-1.md, mes-2.md, mes-3.md
    └── revisao-do-ciclo.md       (semana 13)
```

## Dia (registro rápido, opcional)

Use quando o dono pedir ajuda para organizar o dia. Três perguntas, uma por vez:

1. "Qual é a **única coisa** que, se feita hoje, torna o resto mais fácil ou desnecessário?"
2. "Quais são as 3 prioridades do dia ligadas às táticas desta semana?" (mostre as táticas de `semana-NN.md`)
3. "O que está travado ou aguardando alguém?"

Não salve o dia em arquivo. Se surgir algo relevante, anote na semana.

## Ligação com as outras skills

- Decisões de manter, ajustar ou abandonar podem ser registradas com `/registrar-decisao`.
- Para analisar um documento durante o ritual, use `analisar-documento`.
