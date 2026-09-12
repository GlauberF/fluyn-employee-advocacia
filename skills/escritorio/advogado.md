# Dados do escritório

Arquivo de DADOS, sem método. A skill `escritorio` lê daqui quando precisa
qualificar uma peça, assinar um e-mail ou dizer quem está falando.

Está separado do `SKILL.md` de propósito: trocar de advogado, ou usar este mesmo
repositório em outro escritório, é editar só este arquivo.

Não é segredo. Nome, OAB e endereço profissional são públicos e vão impressos em
toda peça, por isso ficam aqui em texto e não no cofre. Credencial de verdade
(token, senha, chave de API) nunca entra neste arquivo: essa vai no cofre, e a
skill `fluyn-vault` explica como.

## Advogado responsável

- **Nome completo:** <!-- PREENCHER -->
- **OAB:** <!-- PREENCHER: número e seccional, ex. OAB/SP 123.456 -->
  A OAB não serve só para qualificar peça: é por ela que se vigia intimação no
  DJEN. Ver "Vigilância" no fim deste arquivo.
- **E-mail:** <!-- PREENCHER -->
- **Telefone:** <!-- PREENCHER -->

## Escritório

- **Razão social:** <!-- PREENCHER -->
- **CNPJ:** <!-- PREENCHER -->
- **Endereço completo:** <!-- PREENCHER -->

## Como usar

Enquanto um campo estiver com `<!-- PREENCHER -->`, ele **não foi informado**.
Nesse caso, pergunte ao usuário o dado que falta. Nunca preencha com um nome, um
número de OAB ou um CNPJ plausível: peça processual com qualificação inventada é
erro grave, e é o tipo de erro que ninguém revisa porque parece preenchido.

## Outras OABs do escritório

Só preencha se houver mais de um advogado cujas intimações o funcionário
acompanha. A vigilância no DJEN é **uma tarefa por OAB**, então cada linha aqui
vira uma tarefa separada, e não uma tarefa que olha todas.

<!-- PREENCHER, ou apague esta seção se só houver um advogado:
- Nome, OAB/UF 000.000
-->

## Vigilância

Quando o usuário pedir acompanhamento contínuo de intimação, a OAB que a
consulta usa **já está aqui**. Não pergunte o número de novo.

Isso dispensa a pergunta pelo NÚMERO, e só isso. Continue confirmando **o que**
vai ser vigiado antes de criar qualquer tarefa recorrente, porque tarefa
recorrente errada não avisa que está errada. A regra inteira, com as exigências
que não são óbvias, está na skill `dados-publicos-br`.
