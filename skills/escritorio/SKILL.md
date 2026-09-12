---
name: escritorio
description: Constantes deste escritório de advocacia, como calcular honorários advocatícios por faixa, como montar o título e a descrição para cadastro no sistema de controle, a qualificação do advogado e do escritório, e como entregar documento longo. Use quando o usuário perguntar quanto cobrar de honorário sobre um crédito recebido, pedir o título ou a descrição de um serviço para cadastrar, precisar qualificar uma peça ou assinar uma comunicação, ou quando você for entregar um documento extenso.
---

# Constantes do escritório

Esta skill guarda o que se **consulta**, e não método jurídico. Método está nas
skills de trabalho (`auditoria-de-contrato`, `defesa-processual`,
`triagem-de-publicacao`, `ditado-para-roteiro`).

## Quem é o advogado

Está no seu bloco de memória `escritorio/advogado`, que já está no contexto. Não
existe arquivo para ler, e você não precisa gastar uma chamada de ferramenta
para saber quem assina.

Ele fica no bloco, e não num arquivo desta skill, por dois motivos práticos.
Arquivo de skill é **sobrescrito a cada sincronização do repositório**, então o
que fosse anotado ali se perderia sem aviso. E este repositório pode ser
apontado para outro funcionário ou outro escritório, e a OAB de um advogado
específico não tem por que viajar junto.

Campo com `PREENCHER` é campo que ninguém informou ainda. Pergunte ao usuário,
nunca invente.

**A OAB é dado de trabalho, e não só de qualificação.** É por ela que se vigia
intimação no DJEN. Quando o usuário pedir acompanhamento contínuo ("me avisa
quando sair intimação minha"), o número já está no bloco: não pergunte de novo,
e não peça que ele digite.

Isso dispensa a pergunta pelo número, e nada mais. **Confirmar o que vai ser
vigiado continua obrigatório**, e quem manda nessa parte é a skill
`dados-publicos-br`, na seção "Antes de agendar, confirme com o usuário o que
você vai vigiar". Tarefa recorrente errada roda por semanas sem avisar que está
errada.

## Honorários

Sobre o valor do crédito **efetivamente recebido**, em faixas cumulativas:

| Faixa do crédito | Percentual |
|---|---|
| Até R$ 1.000.000,00 | 5% |
| O que exceder R$ 1.000.000,00 até R$ 5.000.000,00 | 4% |
| O que exceder R$ 5.000.000,00 | 2% |

As faixas são cumulativas, e não excludentes: um crédito de R$ 6.000.000,00 paga
5% sobre o primeiro milhão, 4% sobre os quatro milhões seguintes e 2% sobre o
último milhão, e não 2% sobre os seis milhões. É o erro que aparece quando
alguém lê a tabela rápido demais.

Confira: R$ 50.000,00 + R$ 160.000,00 + R$ 20.000,00 = R$ 230.000,00.

Sempre mostre o valor apurado em cada faixa antes do total. O advogado precisa
conseguir conferir a conta sem refazer.

**Base de cálculo é o recebido, não o ganho.** Se o usuário der o valor da
condenação, da causa ou do acordo, pergunte quanto entrou de fato antes de
calcular. Sentença favorável que não virou dinheiro não gera honorário nesta
tabela.

## Título e descrição para o sistema de controle

Ao concluir um trabalho, o escritório cadastra dois campos.

**Título, no máximo 100 caracteres.** Formato:

```
[Cliente] vs. [Parte Contrária] - [Objeto específico]
```

Sem parte contrária (parecer, contrato, consulta), use só `[Cliente] - [Objeto]`.
Se os nomes estourarem os 100 caracteres, abrevie a parte, nunca o objeto:
primeiro nome e último sobrenome, ou só a razão social principal. O objeto é o
que faz alguém achar o registro depois.

Exemplo: `José Ricardo vs. Topoflora - Contrato de manutenção florestal.`

**Descrição, no máximo 550 caracteres.** Resume o **resultado**, não o processo
de criação. Três partes: contexto da relação jurídica, objeto do que foi
entregue, e conclusão (cláusulas ajustadas, riscos apontados, recomendações).

Não escreva nada sobre a interação com o usuário. Fora: "documento gerado",
"conforme solicitado", "após seus ajustes", "análise feita em conjunto". Quem lê
esse campo daqui a um ano quer saber do caso, não de como ele foi produzido.

Conte os caracteres antes de entregar. Os dois limites são do sistema de
controle, e texto cortado no meio chega truncado lá.

## Entrega de documento longo

Documento extenso (contrato, peça, parecer) vai **por seção**, e não inteiro de
uma vez. Escreva uma seção, mostre, espere o advogado aprovar ou pedir ajuste, e
só então siga para a próxima. No fim, se ele quiser, compile tudo num texto só.

O motivo é prático: erro de premissa na cláusula 2 contamina as cláusulas 3 a 40,
e achar isso num texto pronto custa muito mais do que na hora.

Não use código numérico para aprovação. Aqui a pessoa responde em português, por
WhatsApp ou Telegram, e pedir "digite 0" a obriga a decorar um teclado que não
existe.

## Guardrail que vale em tudo que este escritório produz

**Nunca afirme o texto de uma lei, de uma súmula ou de um precedente de
memória.** Se você vai citar um dispositivo, ou você leu a fonte nesta conversa,
ou você diz que não conferiu. Artigo citado com número trocado atravessa a
revisão inteira porque parece certo.

O mesmo vale para prazo: quem confere prazo é o advogado, sempre. Você ajuda a
achar e a organizar, não assume a contagem.
