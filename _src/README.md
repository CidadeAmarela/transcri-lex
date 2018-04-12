## Códigos-fonte e especificações do processo

Nesta pasta são mantidos algoritmos de uso geral, que podem ser reaproveitados em qualquer ferramenta, e um primeiro esboço da docucumentação para o controle dos arquivos do repositório. Cada arquivo de transcrição, com seu *path* dentro do repositório, precisa ter uma tradução direta e não-ambígua para a URN LEX correspondente do seu conteúdo principal. Por exemplo o documento [`BR/Federal/Lei/2002-01-10-10406~compilada.htm`](../BR/Federal/Lei/2002-01-10-10406~compilada.htm) é identificado pela URN LEX `urn:lex:br:federal:lei:2002-01-10;10406@compilado`, e esse mapeamento pode ser realizado via software.

## Especificações gerais do processos

[Processos de transcrição digital](https://pt.wikiversity.org/wiki/Transcri%C3%A7%C3%A3o_digital) conforme disponibilidade dos arquivos originais (fontes em TXT, HTML, PDF, imagem, etc.) e sua destivação final (formatos HTML-lex1, HTML-lex2, HTML-lex3  ou XML-LexML).

A metodologia proposta garante a compatibilide entre as diversas opções de transcrição.

###  Formatos de entrada e saída do processo

O alvo principal são os formatos padronizados de XML, tais como [LexML](http://projeto.lexml.gov.br/documentacao/Parte-3-XML-Schema.pdf) e [ISO-STS](https://www.iso.org/schema/isosts/v1.1/doc), ainda carentes de uso no Brasil, e as variantes padronizadas de [HTML5-onlyContent](https://github.com/okfn-brasil/HTML5-onlyContent), descritas na seção "Formatos HTML-lex para intercâmbio e convervação".

Documentos oficiais no Brasil ainda encontram-se, em sua maior parte, em formato PDF ou indisponíveis no meio digigital, requerendo digitalização e OCR. O processo para se chegar no HTML é  similar ao adotado pelo [Transcritores Distribuídos](https://en.wikipedia.org/wiki/Distributed_Proofreaders).

### Formatos HTML-lex para intercâmbio e convervação
... relação entre a maturidade institucional e a adoção de um formato ...

## Semântica

* [Organizações](http://schema.org/Organization): empresas e organizaçoes não-governamentais. Associações, condomínios, empresas, etc.

* [Governo](http://schema.org/GovernmentOrganization): organizaçoes governamentais dos poderes executivo, legislativo e jurídico.

* **Jurisdiçao** de uma organização:
  - Se governamenal, jurisdição do poder associado.
  - Senão sede da organização: jurisdição sob a qual está vinculada a sede da organização. Determina competência jurídica em contratos ou serviços de cartórios. 

* **Autoridade** emitente documento: é a própria organizaçao, ou, no caso governamental, nova da autoridade relativa ao emissor.

* **Autoridade** emitente documento: é a própria organizaçao, ou, no caso governamental, nova da autoridade relativa ao emissor.


## Sintaxe

Sintaxe da URN LEX geral de um documento de associação ou condomínio:

&nbsp; `urn:lex:`


## Algoritmos para a conversão de identificadores

Documentos do repositório são identificados pelo seu *path* relativo à raiz do repositório (raiz do [git](https://en.wikipedia.org/wiki/Git) ou [zip](https://en.wikipedia.org/wiki/Archive_file)). Documentos finais (entregáveis) devem apresentar internamente, como metadado a sua [URN LEX](https://en.wikipedia.org/wiki/Lex_(URN)), e esta URN deve ser consistente com o *path*.

Tabela 1 da norma [Parte-2-LexML-URN](http://projeto.lexml.gov.br/documentacao/Parte-2-LexML-URN.pdf) - Caracteres Reservados.

separador|descrição
----|----
`:` |separador dos elementos principais do nome.
`;` |marcador da introdução de uma especificidade ou de um nível hierarquicamente inferior do elemento.
`@` |separador de versão.
`~` |separador para indicar a forma da expressão do conteúdo (ex: texto, imagem etc.) e língua.
`!` |separador de fragmento.
`[` , `]` |delimitadores utilizados para especificar intervalo de valores, em particular fragmentos.
`,` |É utilizado principalmente na designação de autoridade multipla (ex. autoridade interministerial) e documentos mistos (ex. ata e estatuto)

Regras de conversão de URN LEX para *path* de arquivos e pastas:

...conversão exata das URNs mais frequentes para a sua representação em pastas e arquivos.

1. troca `:` por `/`
2. troca `foo.bar` por `fooBar`
3. troca `;` por `.`
4. troca o `!` de fragmento e o `@` de versão por `~`  e a convenção de iniciar por "v" a versão. <br/>O segundo `~` o fragmento no caso de arquivos versionados. Compilações devem ser expressas com relação à data da norma da última alteração, ex. `v2012-02-30compilado`.

As autoridades múltiplas (ex. normas interministeriais) não serão tratadas com `,` mas uma tabela de cobvnversão de nomes.

Um repositório git não precisa conter todas as transcrições, a finalidade é servir de transporte ou distribuir em vários gits.

Convenção da representação de jurisdições:
* `BR` representa a União, `BR-AM`, `BR-SP`, etc. (2 letras) unidades da federação, `BR-STJ`, `BR-JusticaTrabalho-Regiao16`, etc. demais jurisdições da esfera federal conforme tabela de abreviações com 3 ou mais letras.

* `AM-Manaus`, `SP-Campinas`, etc. representam cidades e demais jurisdições da esfera estadual.

* Quando a pasta contém apenas sub-jurisdições (não pode conter autoridades) usar `_` no final, por exemplo `BR-SP_`

Exemplos:
* ...
* Com fragmento "lex:br:federal:lei:2000-12-06;126!sec2" vira "BR/Federal/Lei/2000-12-06.126~sec2"

Funções de conversão em Javascript, [PHP](lib_transcrilex.php) e PLpg/SQL.

* `transcrilex_urn2path(urnlex)`
* `transcrilex_path2urn(filename)`

## originais

Arquivos orgiginais requerem autenticação SHA3 (em arquivo `_sha3-256sum.b58btc.txt`) e entrada
no arquivo `_fonte.csv` &mdash; no futuro o perl gerador poderia incluir a coluna SHA3 no CSV automaticamente.

O arquivo CSV tem sempre a mesma estrutura de 3 colunas, `arquivo,autoridade,url`, com, respectivamente o nome de arquivo praticado na pasta, a URN LEX da autoridade que forneceu o original, e a URL do arquivo... Falta a data de acesso ou de ultima confirmação da SHA3.

Exemplos:

* `BR/Federal/Lei/_originais/2002-01-10-num10406.fonte0-camara.htm` representa a URN LEX `br:federal:lei:2002-01-10;10406` e tem como extensão completa `fonte0-camara.htm`, que indica que o arquivo é fonte primária (nível zero), formato HTML, fornecida pela autoridade "camara". O indicador de autoridade é apenas uma chave para resolver eventuais ambiguidades no CSV, onde a coluna "autoridade" descreve com mais precisão pelo prefixo URN LEX da autoridade.

* `BR/Federal/Lei/_originais/2002-01-10-num10406.fonte0-senado.htm` representa a URN LEX `br:federal:lei:2002-01-10;10406` e tem como extensão completa `fonte0-senado.htm`. Como no caso anterior o diferenciador "senado" estabelece a entrada no CSV com a URN LEX da autoridade.

* `BR/Federal/Lei/_originais/2002-01-10-num10406~compilada.fonte0-planalto.htm` representa a URN LEX `br:federal:lei:2002-01-10;10406~compilada` e tem como extensão completa `fonte0-planalto.htm`. Como no caso anterior o diferenciador "planalto" estabelece a entrada no CSV com a URN LEX da autoridade.
