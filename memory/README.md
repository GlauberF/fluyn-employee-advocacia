# Blocos de memória

> **Esta pasta ainda NÃO é carregada automaticamente.** Hoje você precisa copiar
> o conteúdo destes arquivos para a tela de edição do funcionário, à mão.

## Por que ela existe assim

O carregador de template do fluyn-server valida uma lista fechada de pastas
(`manifest.py`, `_KNOWN_PATH_KEYS = ("skills", "agents", "harness")`). Chave
desconhecida em `manifest.json` não dá erro: é **ignorada em silêncio**. Ou seja,
declarar `"memory": "memory"` hoje daria a impressão de que subiu, sem subir
nada.

Por isso o `manifest.json` **não** declara esta pasta. Quando a plataforma
passar a suportar, o passo é acrescentar `"memory": "memory"` em `paths` e
apagar este aviso.

Enquanto isso, o conteúdo fica aqui versionado, revisável em pull request, e a
configuração no painel é cópia fiel do arquivo.

## Por que isto não é uma skill

Skill é carregada **sob demanda**, por casamento da `description`. Bloco de
memória fica **sempre** no contexto.

O que está aqui é o que precisa valer quando **nenhuma** skill carrega. O caso
concreto: o advogado pergunta no chat "qual o prazo do agravo?". Isso não dispara
skill nenhuma, e sem o guardrail no contexto o modelo responde de memória com um
artigo que parece certo.

Tudo que tem gatilho claro (honorários, título para o sistema, auditoria de
contrato) mora em skill, e não aqui. Bloco custa contexto em todo turno, então
só entra o que não cabe em outro lugar.

## Formato

Igual ao dos blocos que o fluyn já traz de fábrica
(`fluyn/lib/agents/fluynbotDefaults/memories/`). Três campos no frontmatter,
mais o corpo:

```
---
label: escritorio/guardrails
description: uma frase natural dizendo QUANDO ele deve trazer isto para a conversa
limit: 20000
---

corpo
```

Os três campos são exatamente os do formulário "Adicionar memória" no painel:
`label` é o **Nome**, `description` é a **Orientação (quando usar esta
memória)**, e o corpo é **O que ele vai guardando**.

Nome de arquivo com `_` no lugar da `/` do label, extensão `.mdx`, como nos
arquivos de fábrica (`human_family.mdx` para `human/family`).

**O frontmatter passa por YAML estrito.** Um `: ` sem aspas dentro da
`description` quebra o parse e derruba o boot. Não use dois-pontos seguido de
espaço ali.

### Escreva em primeira pessoa

Bloco é a memória do funcionário, e os de fábrica são escritos como ele falando
de si ("Eu não afirmo...", "My failure mode is..."), não como ordem dada a ele.
Regra em segunda pessoa imperativa destoa do resto do contexto e lê como corpo
estranho.

### Ele pode reescrever o que está aqui

O funcionário edita os próprios blocos com `memory_insert` e `memory_replace`.
Isso é o ponto do bloco (ele aprende), mas significa que guardrail em bloco é
mais frágil que guardrail em skill, que ele não edita. Por isso as mesmas regras
estão **repetidas** dentro de cada skill de método: lá elas não mudam. O bloco
existe para o caso em que nenhuma skill carrega.

## Namespace

O `label` de cada arquivo **não** pode começar com `human/`. Blocos no namespace
`human` são isolados por conversa quando o funcionário está em modo per-channel
ou per-chat: cada conversa ganha a sua cópia, e uma regra do escritório passaria
a divergir entre conversas. Regra da casa vai em `escritorio/`.

## O que tem aqui

| Arquivo | `label` | Para quê |
|---|---|---|
| `escritorio_advogado.mdx` | `escritorio/advogado` | Nome, OAB, contato e dados do escritório, que entram na qualificação de toda peça. |
| `escritorio_honorarios.mdx` | `escritorio/honorarios` | A tabela por faixa e como aplicá-la. |
| `escritorio_padroes.mdx` | `escritorio/padroes` | Título e descrição para o sistema de controle, e entrega de documento longo por seção. |
| `escritorio_guardrails.mdx` | `escritorio/guardrails` | Não citar lei de memória, prazo é do advogado, qualificação sai do bloco do advogado. |

## A linha entre repositório e painel

**Repositório é método. Painel é constante deste escritório.**

As quatro skills ensinam a auditar um contrato, montar uma defesa, organizar um
ditado e triar uma publicação. Isso não muda quando o escritório muda de tabela
de honorários, e é revisável em pull request.

Os quatro blocos guardam o que **este** escritório decidiu e pode redecidir a
qualquer momento: quem assina, quanto cobra, em que formato cadastra, o que
nunca faz. O advogado altera no painel, sem tocar em Git e sem esperar deploy.

Existiu uma skill `escritorio` que misturava as duas coisas. Ela foi dissolvida
nestes blocos, porque toda seção dela era constante e não método, e constante em
arquivo de skill tem dois defeitos: é sobrescrita na sincronização, e obriga uma
chamada de ferramenta para ser lida.

## Por que a identidade do advogado é bloco, e não arquivo de skill

Ela já foi um `advogado.md` dentro de uma skill, e um teste na instância
mostrou por que aquilo não servia. Pedimos ao funcionário que gravasse uma OAB
de teste, ele editou o arquivo corretamente, e o dado **morreria na próxima
sincronização do repositório**, porque arquivo de skill é sobrescrito.

Três razões, na ordem em que pesam:

1. **Bloco sobrevive à sync**, arquivo de skill não.
2. **Bloco já está no contexto.** Com o arquivo, cada pergunta sobre a OAB
   gastava uma chamada de `Read`, e nós vimos isso acontecer.
3. **Este repositório pode ser apontado para outro funcionário ou outro
   escritório.** A OAB de um advogado específico não tem por que viajar junto
   com o método.

### `read_only` ficou desligado, de propósito

Bloco aceita `read_only`, e ele é aplicado de verdade (o `core_tool_executor` do
fluyn-server recusa toda mutação de memória sobre bloco marcado, e o
`ensure_read_only_block_not_modified` é um segundo portão).

Deixamos **desligado** por enquanto, para o funcionário poder corrigir um dado
quando o advogado avisar. O risco aceito é que ele reescreva a própria OAB num
turno confuso, e a peça saia assinada com número errado. Se isso preocupar, o
conserto é ligar o `read_only` no bloco `escritorio/advogado`, e aí só humano
edita.
