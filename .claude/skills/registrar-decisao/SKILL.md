---
name: registrar-decisao
description: Salva uma decisão tomada em decisoes/ usando o modelo do projeto e faz o commit no Git, criando um histórico das decisões da empresa.
argument-hint: "[título curto da decisão]"
disable-model-invocation: true
allowed-tools: Bash(git add decisoes/*) Bash(git commit *) Bash(git status *)
---

# Registrar decisão

Título informado: $ARGUMENTS

1. Use o que foi discutido nesta conversa. Se faltar algum campo do modelo, pergunte ao usuário. Não invente.
2. Crie `decisoes/AAAA-MM-DD-<titulo-em-minusculas-com-hifens>.md` a partir de `decisoes/_modelo.md`, com a data de hoje.
3. Mostre o texto ao usuário e peça confirmação antes de salvar.
4. Depois de confirmado, acrescente uma linha em `decisoes/README.md`, na seção "Registro":
   `- AAAA-MM-DD — [Título](arquivo.md) — situação`
5. Faça o commit:
   `git add decisoes/ && git commit -m "decisão: <título>"`
6. Confirme ao usuário o nome do arquivo salvo e o resultado do commit.

Para revisar uma decisão antiga, não apague o arquivo: atualize o campo "Situação" e acrescente a seção "Revisão em AAAA-MM-DD".
