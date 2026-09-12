---
name: defesa-processual
description: Construir contestação ou defesa a partir da petição inicial, cruzando causa de pedir com pedido e com liminar, e conferindo se a minuta existente impugnou cada ponto. Use quando o usuário mandar uma petição inicial e pedir contestação, defesa, impugnação ou resposta, ou quando pedir para conferir se a defesa que ele já escreveu cobre tudo que a outra parte alegou.
---

# Defesa processual

O erro que esta skill existe para evitar é um só: **ponto da inicial que
ninguém impugnou**. Ele não dá erro, não aparece na leitura, e só cobra o preço
na sentença.

Por isso o trabalho começa por uma matriz, e não pela redação.

## Fase 1, varredura da inicial

Peça a petição inicial e, se houver, a decisão liminar ou de tutela. Antes de
pedir, veja se os arquivos já foram anexados na conversa: se já vieram, diga
quais você identificou e siga.

Monte a matriz:

| Causa de pedir | Fundamento | Pedido de mérito | Pedido liminar |
|---|---|---|---|

Depois responda duas perguntas sobre ela:

1. **Cada causa de pedir tem pedido correspondente?** Causa sem pedido é
   narrativa, e não precisa de defesa de mérito.
2. **Cada pedido liminar tem correspondente no mérito?** Liminar sem pedido de
   mérito correspondente é inépcia, e é argumento de defesa, não um detalhe.

Apresente a matriz e pergunte se ela cobre a inicial inteira. Só siga com a
confirmação do advogado: matriz errada contamina tudo que vem depois.

## Fase 2, cobertura da minuta

Se existe minuta de contestação, e se existe minuta ou decisão de agravo, peça as
duas.

Para **cada linha** da matriz, marque uma das três: impugnada, impugnada de
forma frágil, ou não impugnada. Entregue a lista das não impugnadas primeiro, que
é o achado que justifica o trabalho.

Confira também a **congruência entre o agravo e a contestação**. Argumento que o
agravo sustenta e a contestação contradiz é munição entregue à outra parte.

## Fase 3, estrutura

Proponha a estrutura de tópicos da peça. Se a minuta original está boa, mantenha
a estrutura dela: reorganizar o que já funciona gasta o tempo do advogado sem
ganho. Se precisa mudar, diga o que muda e por quê.

## Fase 4, argumento a argumento

Para cada item de mérito e cada preliminar, apresente:

- **Ataque:** o que a inicial alega, em uma ou duas linhas.
- **Defesa atual:** o que a minuta responde hoje, se responde.
- **Pergunta:** manter, alterar ou acrescentar?

Quando o advogado propuser um argumento novo, seu trabalho não é aceitar: é
conferir se ele contradiz outra parte da defesa. Tese que salva a preliminar e
afunda o mérito é o risco real aqui.

## Fase 5, veredito sobre a minuta

Diga qual dos três, com o motivo:

- **Manter**, só ajuste fino.
- **Ajustar**, mudança pontual de conteúdo.
- **Refazer**, estrutura ou argumentos insuficientes.

## Fase 6, redação

Só agora se escreve. Vá **por seção**, como a skill `escritorio` descreve na
seção "Entrega de documento longo": uma seção, aprovação, próxima. Cada seção
segue o que foi decidido na Fase 4 para aquele item.

## Guardrails

**Nunca cite artigo, súmula ou precedente de memória.** Ou você leu a fonte
nesta conversa, ou você diz que não conferiu. Em defesa isso é ainda mais sério,
porque a peça vai assinada.

**Prazo é do advogado.** Você pode achar e organizar a informação de prazo, mas
a contagem e a conferência são dele. Nunca diga a um cliente qual é o prazo como
se fosse fato confirmado por você.

Se precisar buscar andamento ou peça no portal do tribunal, quem ensina isso é a
skill `portais-tribunal-br`. Não improvise endereço de tribunal.
