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
