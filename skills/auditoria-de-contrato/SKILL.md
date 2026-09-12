---
name: auditoria-de-contrato
description: Auditar um contrato já escrito à procura de erro mecânico e risco de redação, como numeração fora de sequência, referência cruzada quebrada, valor em algarismo que não bate com o por extenso, placeholder esquecido e termo definido usado sem definição. Use quando o usuário mandar um contrato e pedir para revisar, conferir, auditar, checar antes de assinar ou antes de enviar para a outra parte.
---

# Auditoria de contrato

Você **não reescreve** o contrato aqui. Você aponta o que está errado e entrega
um relatório que o advogado usa para decidir. Reescrever sem ser pedido esconde
o defeito em vez de mostrá-lo.

Esta é uma leitura mecânica, item por item. O valor dela está na exaustão, não na
interpretação: são os erros que passam pela revisão humana justamente porque a
pessoa lê o que quis escrever, e não o que está escrito.

## Antes de começar

Se o contrato veio em `.docx`, a skill `doc` abre. Se veio em `.pdf`, a skill
`pdf`. Não tente adivinhar o conteúdo pelo nome do arquivo.

Leia o documento inteiro antes de apontar o primeiro erro. Metade das
inconsistências só aparece quando a cláusula 40 contradiz a cláusula 3.

## Os sete exames

### 1. Estrutura e numeração

Cláusulas, parágrafos, incisos, alíneas e listas estão em sequência? Aponte todo
salto (da Cláusula 3 para a 5) e toda repetição (duas Cláusulas 7).

### 2. Referências cruzadas

Para cada "conforme a Cláusula 4.1", "nos termos do item 2.3", "previsto no
Anexo II": a cláusula citada **existe**? E trata do assunto que a frase diz que
ela trata? Referência que aponta para o lugar errado é pior que referência
quebrada, porque não dá erro em lugar nenhum.

### 3. Clareza, gramática e semântica

Erro de ortografia, concordância e digitação. Trecho ambíguo, que permita duas
leituras.

**Ignore quebra de linha e artefato de conversão de PDF.** Aponte cláusula
incompleta somente quando a **ideia** estiver inacabada, faltando palavra ou
contexto. Confundir defeito de conversão com defeito de redação enche o
relatório de ruído e faz o advogado parar de ler.

### 4. Coerência lógica

Obrigações que se contradizem (uma cláusula diz que o contrato é irrevogável,
outra prevê rescisão imotivada). Prazos que não fecham (prazo total que não bate
com as datas de início e fim).

### 5. Informação faltante

Placeholder, espaço em branco, colchete, chave, destaque: `[ ]`, `XXXX`, `...`,
`[Inserir Razão Social]`, `[Data]`. A qualificação das partes está completa,
nome, documento e endereço?

### 6. Valores

Confronte cada valor em algarismo com o seu por extenso. "R$ 1.500,00 (um mil e
quinhentos reais)" bate; "R$ 15.000,00 (um mil e quinhentos reais)" não bate, e
é uma das divergências mais caras que existem num contrato.

Aponte também valor ou percentual que apareça **só** em algarismo, sem o por
extenso, e recomende incluir. Não vale para número de cláusula, item, subitem
nem lista.

### 7. Termos definidos

Palavra com inicial maiúscula que designa um conceito no contrato. Aponte:

- termo definido que nunca é usado depois;
- palavra com inicial maiúscula usada como termo definido que **não foi definida
  em lugar nenhum**;
- o mesmo conceito chamado de dois jeitos diferentes ao longo do texto.

## O relatório

Três seções, nesta ordem, da maior para a menor criticidade:

**Alertas críticos.** Contradição, valor divergente, referência cruzada quebrada,
informação faltante que impede assinar.

**Avisos de estrutura.** Numeração e uso incorreto de termo definido.

**Sugestões de correção de texto.** Gramática, ortografia e cláusula confusa.

Em cada item diga **onde** está (cláusula e, quando ajudar, o trecho), o que está
errado e por que importa. Achado sem localização obriga o advogado a procurar, e
aí a auditoria não economizou tempo nenhum.

Se algum dos sete exames não encontrou nada, escreva isso explicitamente:
"Nenhuma inconsistência encontrada neste item." Silêncio se confunde com exame
que não foi feito.

## Guardrail

Se você for citar lei para sustentar um apontamento, ou leu a fonte nesta
conversa, ou diz que não conferiu. Nunca cite dispositivo de memória.
