# transcri-lex

Repositório de [transcrições digitais](https://pt.wikiversity.org/wiki/Transcrição_digital) de documentos oficiais para [HTML5 de conteúdo](https://github.com/okfn-brasil/HTML5-onlyContent).

Amostragem de documentos públicos passíveis de serem identificados por sua URN LEX, tais como os documentos do [acervo LexML](http://lexml.gov.br/desc_acervo.html).

## Organização das pastas

Nomes na raiz do repositório iniciados por maiúsculas são jurisdições, nomes iniciados por `_` são reservados ao controle:

* [_docs](_docs): documentação geral.
* [_src](_src): códigos-fonte de material de apoio e algorítmos de referência.

As pastas de jurisdições seguem seu *path* conforme algoritmo da conversão de URN-LEX.  Exemplos:

* Na pasta [SP-SaoPaulo](SP-SaoPaulo) encontram-se as autoridades da jurisdição `br;sp;sao.paulo`. Por exemplo o estatuto da Associação OKBR, sediada em São Paulo, é identificado pela URN LEX  `br;sp;sao.paulo:assoc;okbr:estatuto:2013-09-10` e se encontra no na pasta   [SP-SaoPaulo/Assoc-Okbr](SP-SaoPaulo/Assoc-Okbr), ou seja, no path `SP-SaoPaulo/Assoc-Okbr/estatuto2013-09-10.htm`.

* na pasta  [BR-SP](BR-SP) encontram-se as autoridades da jurisdição `br;sp`.

* na pasta  [BR](BR), no path `BR/Federal/Leis` encontram-se os documentos do tipo *lei* da autoridade `br:federal`. Por exemplo a Lei nº 10.406 de 10/01/2002, da URN LEX `br:federal:lei:2002-01-10;10406` encontra-se na referida pasta. A versão compilada é o arquivo
[BR/Federal/Lei/2002-01-10-10406~compilada.htm](BR/Federal/Lei/2002-01-10-10406~compilada.htm).

## Lembretes
Conceitos e metodologia de transcrição em https://pt.wikiversity.org/wiki/Transcrição_digital

Adaptando e resgatando algoritmos de http://www.teses.usp.br/teses/disponiveis/76/76132/tde-15092010-164303/publico/AlessandraDoranteM.pdf

Ver [procedimentos em desenvolvimento aqui](BR/Federal/Lei/_originais/lote2018-03-13~planalto).


Nota: a versão inicial do repositório foi [transferida com todos os seus *commits*](https://stackoverflow.com/a/17373088/287948) de *ppkrauss/transcri-lex*. Os procedimentos de transferência ou [duplicação](https://help.github.com/articles/duplicating-a-repository/) são mais indicados do que o *fork* quando, como neste caso, não se deseja preservar vínculos com o repositório original, apenas garantir a autoria  (prova de trabalho neste caso) das contribuições.
