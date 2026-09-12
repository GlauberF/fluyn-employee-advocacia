---
name: ditado-para-roteiro
description: Transformar ditado, áudio ou transcrição de reunião em roteiro de trabalho organizado, separando os assuntos quando houver mais de um, e abrindo as tarefas do plano de ação no quadro. Use quando chegar um áudio ou um bloco longo de texto falado com instruções, quando o usuário disser que ditou alguma coisa, quando mandar transcrição de reunião, ou quando pedir para organizar as ideias dele.
---

# Ditado para roteiro

Advogado dita muito, e ditado é fora de ordem por natureza: a mesma ideia volta
três vezes, o assunto muda no meio da frase e a conclusão aparece antes do fato.

Seu trabalho aqui é **organizar, não executar**. O roteiro é o insumo da tarefa
seguinte, não a tarefa.

## Entrada

Se veio áudio e não texto, a skill `fluyn-audio` transcreve.

## Primeiro, quantos assuntos

Leia tudo antes de decidir. Procure ponto de ruptura: mudança de partes ou de
número de processo, frase de transição ("mudando de assunto", "agora sobre aquele
outro caso"), conjunto de fatos que não conversa com o parágrafo anterior.

**Um assunto** vira um roteiro. **Vários assuntos** viram um roteiro para cada,
separados por `---`, cada um com os seus próprios metadados. Não force dois casos
num roteiro só para parecer mais enxuto: eles vão virar tarefas diferentes.

## Se for reunião, e não ditado

Reunião tem mais de uma voz e ideia que evolui. Dois cuidados a mais:

- **Descarte o que não é trabalho:** cordialidade, piada, assunto pessoal.
- **Prevaleça a versão final.** Se uma ideia foi proposta e depois superada, só a
  conclusão vale. Registrar as duas faz o leitor achar que ainda há decisão em
  aberto.

E separe ideia **principal** de ideia **acessória**, numerando de forma
hierárquica (1., 1.1., 1.2.). Detalhe promovido a decisão é o jeito mais fácil de
distorcer o que a reunião decidiu.

## A saída

Para cada assunto, duas seções.

**Metadados:** título curto, data de referência e descrição de uma ou duas
frases. A data sai, nesta ordem de prioridade: data dita na transcrição; data no
nome do arquivo de origem; data de hoje.

**Roteiro:** objetivo central primeiro, em uma frase. Depois os tópicos
agrupados, em ordem lógica, sem as repetições. Frase solta vira comando ou ponto
de verificação.

Corrija erro óbvio de transcrição em jargão jurídico (o transcritor erra
"agravo", "exordial", nome de parte). Mas onde o ditado estiver genuinamente
ambíguo, **marque** `[PONTO A ESCLARECER: ...]` em vez de escolher por conta
própria. O ditado é a fonte, e adivinhar a intenção dele é onde se perde o caso.

## O plano de ação vira tarefa

Esta é a parte que costuma se perder. Toda tarefa, responsável e prazo que
saírem da transcrição você abre no quadro com a ferramenta `manage_tasks`, uma
por item.

Plano de ação que fica só como texto na conversa some no dia seguinte. Tarefa no
quadro volta a aparecer sozinha.

Antes de abrir, mostre ao usuário a lista do que você vai criar e espere ele
confirmar. Tarefa aberta errada dá mais trabalho para fechar do que para criar.

Prazo dito no áudio entra na tarefa como **informação do ditado**, nunca como
prazo processual conferido. Quem confere prazo é o advogado.
