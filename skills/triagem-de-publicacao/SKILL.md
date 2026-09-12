---
name: triagem-de-publicacao
description: Ler o extrato de uma publicação judicial ou intimação e extrair partes, dados do processo, ato processual exigido e prazo, entregando uma triagem estruturada com os pontos de atenção. Use quando o usuário colar o texto de uma publicação, de uma intimação ou de um andamento e pedir para entender o que é, o que precisa ser feito ou qual o prazo.
---

# Triagem de publicação

Aqui você recebe o **texto** de uma publicação e o organiza. Buscar publicação
nova é outro trabalho: quem faz isso é a skill `dados-publicos-br`, pelo DJEN, e
ela já traz a regra de quando o zero vale e quando não vale. Não refaça esse
caminho por aqui.

## Identifique o cliente antes

Se ainda não estiver claro de quem é o escritório nessa publicação, pergunte. O
usuário pode responder por nome ("Luiz Pereira", mesmo que o nome completo seja
outro), por sobrenome comum ("os Silva") ou por posição ("os réus", "os
locatários"). Sem isso você não sabe de que lado está o prazo, e a triagem inteira
sai invertida.

## O que extrair

Nesta ordem, e o que não estiver no texto fica como "não consta na publicação":

1. **Partes**, e qual delas é o cliente.
2. **Dados do processo:** número, órgão, vara ou câmara.
3. **Tipo de ação**, se der para dizer pelo texto. Até 600 caracteres, para o
   usuário entender o objeto sem abrir os autos.
4. **Data da publicação.**
5. **Ato processual exigido:** recorrer, esclarecer, arrolar testemunha,
   manifestar-se, cumprir.
6. **Prazo, como está publicado.** Literal, entre aspas, quando houver.
7. **Prazo legal aplicável**, quando a publicação não disser. Diga qual
   dispositivo e **diga que não conferiu a fonte**, se não conferiu.
8. **Pontos de atenção:** o que pode dar errado, o que precisa ser decidido.

## A regra do prazo

**Quem conta e confere prazo é o advogado. Sempre.**

Você organiza a informação e aponta o que reparou. Você não afirma prazo como
fato, não diz "vence dia X" com segurança e não deixa o usuário concluir que a
contagem está conferida porque você a escreveu.

Publicação tem contagem em dias úteis, suspensão, prerrogativa de prazo em dobro
e feriado local que não está no texto que você recebeu. Você não tem como saber
disso pelo extrato.

Feche toda triagem com prazo dizendo que a contagem precisa ser conferida nos
autos.

## O que NÃO fazer

**Não invente texto de lei.** Se for citar o artigo que dá o prazo, ou você leu a
fonte nesta conversa, ou você escreve que está citando de memória e precisa ser
conferido. Artigo com número trocado atravessa a revisão porque parece certo.

**Não prometa verificação que você não fez.** Não escreva que consultou várias
fontes oficiais, nem invente data de última atualização de um dispositivo. Isso
veio do fluxo antigo do escritório (arquivo `rotinas.txt`, rotina `#publicacao`,
que pedia quatro fontes oficiais com data de atualização de cada uma) e é
exatamente o tipo de instrução que faz um modelo preencher o vazio com invenção
convincente.

**Não invente endereço de tribunal.** Se precisar abrir o portal para conferir o
andamento, quem ensina isso é a skill `portais-tribunal-br`.

## Depois da triagem

Se a publicação gerar trabalho com data, ofereça abrir a tarefa no quadro com
`manage_tasks`, com o prazo **marcado como informação da publicação, ainda não
conferida**. Ofereça, não abra sozinho.

## Se ele quiser acompanhamento contínuo

Triagem é de UMA publicação que já chegou. "Me avisa sempre que sair algo desse
processo" é outra coisa: é vigilância recorrente, e é a skill
`dados-publicos-br` que manda nela, nas seções "Antes de agendar, confirme com o
usuário o que você vai vigiar" e "Agendar rotina de vigilância".

Vá para lá, e não monte a tarefa recorrente daqui. Aquela skill carrega
exigências que não são óbvias, como criar a tarefa dentro da conversa de quem
vai receber o alerta e usar janela de consulta desde a última execução. Tarefa
recorrente errada não avisa que está errada: ela roda por semanas vigiando a
coisa errada, e o usuário só descobre quando perde um prazo.
