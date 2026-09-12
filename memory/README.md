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

## Namespace

O `label` de cada arquivo **não** pode começar com `human/`. Blocos no namespace
`human` são isolados por conversa quando o funcionário está em modo per-channel
ou per-chat: cada conversa ganha a sua cópia, e uma regra do escritório passaria
a divergir entre conversas. Regra da casa vai em `escritorio/`.

## O que tem aqui

| Arquivo | `label` | Para quê |
|---|---|---|
| `escritorio-guardrails.md` | `escritorio/guardrails` | Não citar lei de memória, prazo é do advogado, qualificação sai de `advogado.md`. |
