# Plano do trimestre

Tempo: 2 a 3 horas, uma vez por ciclo. Pode ser dividido em duas conversas: objetivos e resultados-chave numa, táticas e pré-mortem na outra.
Antes de começar, leia `estrategia/bussola.md`, a revisão do ciclo anterior (se houver) e os números recentes em `conhecimento/`.

## Etapa 1 — Objetivos (no máximo 3)

1. "Olhando a bússola, aonde o negócio precisa chegar nestas 13 semanas?"
2. Para cada objetivo: "Por que agora, e não no próximo trimestre?"
3. Se surgirem mais de 3, pergunte: "Se só pudesse fazer 3, quais ficariam?" Explique: se tudo é prioridade, o trimestre já decidiu por você.

Objetivo é qualitativo e inspirador, por exemplo: "Tornar a operação de entregas confiável".

## Etapa 2 — Resultados-chave (2 a 4 por objetivo)

Para cada objetivo:

1. "Como vamos saber, com números, que chegamos lá?"
2. Para cada resultado: busque o **ponto de partida** nos documentos e mostre com fonte; pergunte a **meta**.
3. "Quem é o responsável por este objetivo?" (cargo)

Regra: o objetivo diz aonde ir; o resultado-chave diz se você chegou. Se não tem número, ainda não é resultado-chave.

## Etapa 3 — Táticas semanais (3 a 5 por objetivo)

1. "Que ações, repetidas ou pontuais, fazem cada resultado-chave andar?"
2. Cada tática começa com verbo e diz em quais semanas acontece (1 a 12).
3. Questione táticas vagas: "Ligar para clientes" vira "Ligar para 10 clientes inativos por semana".

## Etapa 4 — Pré-mortem

1. "Imagine que o ciclo terminou e falhou. O que aconteceu?"
2. "Quais desses riscos dependem de você?"
3. "O que você faz já para evitar isso?"

Explique: antecipar o fracasso é a forma mais barata de evitá-lo (pré-mortem, Gary Klein).

## Etapa 5 — Compromisso

1. "Ao final destas 13 semanas, o negócio estará…"
2. "Para isso, você vai abrir mão de…"
3. "Quem vai cobrar você?"

## Modelo do arquivo `estrategia/ciclo-AAAA-NN/plano.md`

```markdown
# Plano do ciclo AAAA-NN

Início: AAAA-MM-DD · Semana 13 (revisão): AAAA-MM-DD

## Objetivo 1: <frase>
- **Por que agora:** ...
- **Responsável:** (cargo)

| Resultado-chave | Ponto de partida | Fonte | Meta | Nota final (0–1) |
|---|---|---|---|---|

## Objetivo 2 ...
## Objetivo 3 ...

## Táticas semanais
| Objetivo | Tática | Semanas |
|---|---|---|
| 1 | Ligar para 10 clientes inativos | 1–12 |

## Pré-mortem
- **Se falhar, terá sido porque:** ...
- **Riscos que dependem de mim:** ...
- **O que faço já:** ...

## Compromisso
- Ao final destas 13 semanas, o negócio estará: ...
- Para isso, vou abrir mão de: ...
- Quem vai me cobrar: ...
```

Depois de salvar, crie `semana-01.md` a partir das táticas marcadas para a semana 1 (ver [semana.md](semana.md)).
