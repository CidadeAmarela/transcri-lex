## Documentação

Sumário:

* Metodologias em https://pt.wikiversity.org/wiki/Transcri%C3%A7%C3%A3o_digital
* Procedimentos experimentais: a cada README de pasta `_originais` onde for declarado novo procedimento.
* Convenções: abaixo
* Preços e demais acordos: entre as partes com referência nas convenções

## Convenções adotadas

As subseções a seguir estabelecem tópicos e recomendações ou padrões adotados nos procedimentos de transcrição e na elaboração dos contratos de serviço.

### Entregáveis

O extrato da gestão dos entregáveis fica arquivado em `_proc-entregaveis.csv` a cada pasta `_originais`, global para todos os lotes. 

Arquivo|Status|Papel|Contexto|SHA3-b58btc
-------|------|-----|--------|-----------
*Nome do arquivo*|*Status* com valores <br/>1=em uso, 2=usado, -1=sem uso, -2=revisado, -3=falhou|"Papel" do arquivo no serviço ou na disposição final.|*Nome do lote ou sublote*<br/>(nome da pasta `loteData~User`)|Resultado da aplicação do [*hash* criptográfico](https://en.wikipedia.org/wiki/Cryptographic_hash_function) tipo [*SHA3-b58btc*](https://github.com/CidadeAmarela/transcri-lex/blob/master/_src/sha3-base58.pl) ao arquivo.

Quando o preço não é fechado por lote, podem ser adicionadas colunas de quantificação do mesmo.

### Lotes de material entregue ou processado

Quando for solicitada rastreabilidade (definitiva ou dentro de um "período de homologação serviço") os lotes com arquivos-fonte e arquivos resultantes de cada etapa do trabalho devem ser mantidos no repositório.

As pastas de lote devem estar sempre no interior de uma pasta de `_originais`  e recebem o prefixo `lote` ou `proc` seguido da data ISO:

* Prefixo `lote` refere-se a "lote  de simples remessa". A data indica o momento da entrega e o sufixo `~nome` o *username* do fornecedor.<br/>Precisa estar sempre dentro de uma pasta `_originais`. Exemplo: `lote2018-02-06~investcondo`.

* Prefixo `proc` refere-se a "lote em processamento". A data indica o momento em que o trabalho foi iniciado e o sufixo `~nome` o *username* do responsável (empresa) pelo trabalho. <br/>Pode estar dentro de uma pasta `_originais` ou uma pasta de lote &mdash; neste caso com o *path* `loteData1~user1/procData2~user2` restrito a `Data2≥Data1` e `user1≠user2`). <br/>Exemplos: `proc2018-02-03~spclstrn` (em `_original`) ou `lote2018-02-06~investcondo/proc2018-02-12~spclstrn`.


