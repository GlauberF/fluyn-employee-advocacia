# Funcionário assistente jurídico

Repositório de configuração de um funcionário digital Fluyn, no formato do
[fluyn-employee-template](https://github.com/GlauberF/fluyn-employee-template).
Aponte este repositório na tela de edição do funcionário e o Fluyn carrega as
skills daqui para dentro da instância.

## Antes de usar, preencha

Os dados do escritório **não ficam no Git**, ficam em blocos de memória do
funcionário. O repositório versiona o **esqueleto** de cada bloco, em `memory/`,
e os valores você digita na tela de edição do funcionário.

Dois blocos para criar, copiando o conteúdo dos arquivos:

| Arquivo | Nome do bloco | O que preencher |
|---|---|---|
| `memory/escritorio_advogado.mdx` | `escritorio/advogado` | Os sete campos `PREENCHER`, mais outras OABs se houver. |
| `memory/escritorio_honorarios.mdx` | `escritorio/honorarios` | Nada, se a tabela 5/4/2 for a sua. Ajuste os percentuais se não for. |
| `memory/escritorio_padroes.mdx` | `escritorio/padroes` | Nada, se os limites 100 e 550 forem os do seu sistema. |
| `memory/escritorio_guardrails.mdx` | `escritorio/guardrails` | Nada, o conteúdo já vai pronto. |

Enquanto um campo estiver como `PREENCHER`, o funcionário foi instruído a
**perguntar** o dado, e nunca a inventar um nome ou um número de OAB plausível.

## O que tem aqui

| Skill | Para quê |
|---|---|
| `auditoria-de-contrato` | Revisar contrato pronto atrás de erro mecânico: numeração, referência cruzada, valor por extenso, placeholder, termo definido. |
| `defesa-processual` | Montar contestação a partir da inicial, cruzando causa de pedir com pedido e com liminar. |
| `ditado-para-roteiro` | Ditado ou reunião vira roteiro organizado, e o plano de ação vira tarefa no quadro. |
| `triagem-de-publicacao` | Extrato de publicação vira triagem estruturada com partes, ato e prazo. |

As skills são **método**. Tudo que é **constante deste escritório** (quem é o
advogado, a tabela de honorários, os formatos do sistema de controle, os
guardrails) vive em bloco de memória, em `memory/`, porque o advogado muda isso
ao longo do tempo e arquivo de skill é sobrescrito a cada sincronização.

## O que NÃO tem, e por quê

**Sem `harness/`.** O `harness/settings.json` de um repositório **substitui** o
padrão do Fluyn, inclusive a interceptação de credenciais e a negação de leitura
do cofre. Para um escritório de advocacia isso seria perder proteção sem ganhar
nada. Se um dia precisar de um hook específico, saiba que assume o harness
inteiro junto.

**Sem `agents/`.** Nenhuma das cinco skills delega para estagiário hoje.
Subagente sem uma skill dizendo quando acioná-lo fica no disco sem uso.

**Sem `vault.json`.** Nenhuma skill daqui chama API externa, então não há chave
a declarar. E os dados do advogado **não** são segredo: nome, OAB e endereço são
públicos e vão impressos em toda peça, por isso ficam no bloco de memória
`escritorio/advogado` e não no cofre. O cofre também não serviria: o agente
nunca lê o valor de um placeholder,
ele só escreve `{{CHAVE}}` e o proxy troca na saída HTTP. Numa petição, o
`{{CHAVE}}` sairia literal.

## O que o funcionário já tem de fábrica

Não recriamos nada disso aqui. As skills acima apontam para elas quando o
trabalho chega nesse ponto:

- **`dados-publicos-br`** para DJEN, intimação e publicação em diário.
- **`portais-tribunal-br`** para buscar processo por OAB, nome ou CPF/CNPJ nos
  portais de tribunal.
- **`doc`**, **`pdf`**, **`spreadsheet`** e **`slides`** para os formatos.
- **`fluyn-audio`** para transcrever áudio.
- **`himalaya`** e **`google-workspace`** para e-mail.
- **`whatsapp-styler`** para formatação de mensagem no WhatsApp.
- O quadro de tarefas nativo, pela ferramenta `manage_tasks`.

## Origem

O conteúdo destas skills foi destilado de um conjunto de rotinas que o escritório
usava num assistente anterior (`motor.txt`, `rotinas.txt`, `indice.txt`, 25
rotinas acionadas por `#comando`). A maior parte daquele material era andaime de
roteamento, que aqui já existe nativamente, e foi descartada. Sobrou o método
jurídico, que é o que está nas cinco skills.

Três coisas foram deliberadamente **não** trazidas:

1. A verificação em quatro fontes oficiais da rotina `#publicacao`, que convida o
   modelo a inventar fonte e data de atualização.
2. A proibição de blocos de código da rotina `#apresentacao#`, que fazia sentido
   no assistente anterior e aqui quebraria saída legítima.
3. Os códigos numéricos de aprovação ("digite 0"), que obrigam quem responde por
   WhatsApp a decorar um teclado que não existe.
