---
name: catalogar-documentos
description: Lê documentos da pasta documentos/ ainda não catalogados e cria uma ficha-resumo para cada um em conhecimento/, atualizando o índice. Use quando o usuário pedir para catalogar, indexar ou processar documentos novos.
argument-hint: "[pasta dentro de documentos/, ex.: financeiro]"
disable-model-invocation: true
---

# Catalogar documentos

Pasta a processar: `documentos/$ARGUMENTS` (se vazio, pergunte qual pasta).

## Regras

- Trabalhe em **lotes de no máximo 10 documentos** por execução. No fim, diga quantos faltam.
- Nunca altere, mova ou apague nada em `documentos/`.
- Pule documentos que já têm ficha em `conhecimento/indice.md`, a menos que o arquivo tenha data de modificação mais recente que a ficha.
- Para planilhas, apresentações e PDFs, use as skills de documentos disponíveis (xlsx, pptx, pdf) quando existirem.
- Em apresentações, extraia o texto dos slides. Descreva imagens e gráficos só quando trouxerem números ou informação relevante.
- Em planilhas, liste as abas e o que cada uma contém; registre só os números principais, com aba e célula ou linha.
- Se não conseguir ler um arquivo, registre-o na seção "Não lidos" do índice com o motivo e siga para o próximo.

## Ficha (um arquivo por documento)

Caminho: `conhecimento/<area>/<nome-do-arquivo-sem-extensao>.md`

```markdown
---
origem: documentos/<area>/<arquivo>
tipo: planilha | apresentação | pdf | texto
periodo: <período a que o conteúdo se refere, ou "não informado">
catalogado_em: <AAAA-MM-DD>
---
# <Título claro do documento>

**Resumo:** 3 a 5 linhas sobre o que é e para que serve.

**Números-chave:** (cada um com local: página, slide ou aba)
- ...

**Temas:** palavras-chave separadas por vírgula

**Atenção:** dados incompletos, contradições ou pontos que pedem confirmação.
```

## Índice

Atualize `conhecimento/indice.md`, uma linha por ficha, agrupada por área:
`- [Título](<area>/<ficha>.md) — período — uma frase de resumo`

## Ao terminar

1. Mostre a lista de fichas criadas e os arquivos não lidos.
2. Faça commit: `git add conhecimento/ && git commit -m "fichas: <area> (<n> documentos)"`.
