Metodo de teste de estrutural, busca cobrir todos os caminhos de uma branch, encontrando os caminhos equivalentes a outros dessa forma reduzindo a quantidade de testes
DE N para n/2.

veja um exemplo, você tem que desenvolver casos de testes para validar se uma pessoa pode entrar no vestibular de uma universidade privada, para que ele possa
deve ter mais de 18 anos e ter pago ou não a matricula. Caso seja menor de 18 anos o responsavel deve assinar e pagar a matricula por ele.
 
 public boolean inscricaoAprovada(Pessoa pessoa){
	if(pessoa.getIdade()>=18 || (pessoa.paiAssina() && pessoa.matriculaPaga()){
		return true;
	}
	return false;
  }



EXPRESSAO ->  A || (B && C)

NR CONDIÇÕES: 3 

NR DE VALORES =2 ->{V,F}

quantidade de CAMINHOS->  NRVALORES ^ NRCODICAO ->2^3=8


TABELA VERDADE - Para montar a tabela pegamos a quantidade de caminhos E didimos por 2, encontramos 4 então a primeira coluna tera 4 verdadeiros  alterandos de 4 falsos.
Para segunda coluna pegamos a quantidade de caminhos e dividimos por 4 então teremos 2 verdadeiros alternados de 2 falsos.
Na terceira coluna pegamos a quantidade de caminhos e dividimos por ela mesma e teremos  1 verdadeiro alternado de 1 falso. 

A- B- C -> R
v- v- v -> ?
v- v- f -> ?
v- f- v -> ?
v- f- f -> ?
f- v- v -> ?
f- v- f -> ?
f- f- v -> ?
f- f- f -> ?

resolvemos as sub condições 

resolvendo  B E C
B- C -> (b && c)
v- v ->    v
v- f ->    v
f- v ->    v
f- f ->    f

resolvemos a condição final

   A || (B && C) -> R
1) v	v 	 -> v
2) v	f 	 -> v	
3) v	f        -> v
4) v    f        -> v
5) f	v        -> v
6) f    f        -> f
7) f	f        -> f
8) f   	f        -> f

econtramos a tabela final 
TABELA VERDADE - final

A- B- C -> R
v- v- v -> v
v- v- f -> v
v- f- v -> v
v- f- f -> v
f- v- v -> v
f- v- f -> f
f- f- v -> f
f- f- f -> f


MC/DC = modify conditional decision coverage

PASSO 1 -  encontra a lista de pares de condições para expressão A.
PASSO 2 -  encontra a lista de pares de condições para expressão B.
PASSO 3 -  encontra a lista de pares de condições para expressão C.
PASSO 4 -  encontrar a lista de condições que vamos implementar os nossos testes.

1)LEVAR EM CONSIDERACAO A CONDICAÇÃO: A -- LISTA DE PARES PARA A {VAZIO}
 
 A ||(B && C) 	-> r
1) v- v- v  	-> v     
2) v- v- f 	-> v
3) v- f- v	-> v
4) v- f- f 	-> v
5) f- v- v 	-> v
6) f- v- f 	-> f
7) f- f- v 	-> f
8) f- f- f 	-> f

A -> V mudamos o seu valor para falso -> a=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 1) 
então procuramos ->  (f v v) = f - nao encontrado L{}

A -> V mudamos o seu valor para falso -> a=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 2) 
então procuramos -> (f v f) = f -encontramos 6 =l{(2,6)}

A -> V mudamos o seu valor para falso -> a=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 3) 
então procuramos -> (f f v) = f  - encontramos 7 l={(2,6),(3,7)}

A -> V mudamos o seu valor para falso -> a=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 4) 
então procuramos -> (f f f) = f  - encontramos 8 l={(2,6),(3,7),(4,8)}

A -> F mudamos o seu valor para verdadeiro-> a=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 5) 
então procuramos -> (v v v ) = f  - nao encontramos l={(2,6),(3,7),(4,8)}

A -> F mudamos o seu valor para verdadeiro-> a=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 6) 
então procuramos -> (v v f ) = v  - encontramos  2, porém (2,6) já existe não precisamos colocar novamente. l={(2,6),(3,7),(4,8)}

A -> F mudamos o seu valor para verdadeiro-> a=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 7) 
então procuramos -> (v f v ) = v  - encontramos  3, porém (3,7) já existe não precisamos colocar novamente. l={(2,6),(3,7),(4,8)}

A -> F mudamos o seu valor para verdadeiro-> a=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 8) 
então procuramos -> (v f f ) = v  - encontramos  4, porém (4,8) já existe não precisamos colocar novamente. l={(2,6),(3,7),(4,8)}

ENTÃO A LISTA DE PARES PARA CONDICAO A É l={(2,6),(3,7),(4,8)}

2)LEVAR EM CONSIDERACAO A CONDICAÇÃO: B - LISTA DE PARES PARA B{VAZIO}

  A ||(B && C) 	-> r
1) v- v- v  	-> v     
2) v- v- f 	-> v
3) v- f- v	-> v
4) v- f- f 	-> v
5) f- v- v 	-> v
6) f- v- f 	-> f
7) f- f- v 	-> f
8) f- f- f 	-> f

B -> V mudamos o seu valor para falso -> b=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 1) 
então procuramos ->  (v f v) = f - nao encontrado L{}

B -> V mudamos o seu valor para falso -> b=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 2) 
então procuramos ->  (v f f) = f - nao encontrado L{}

B -> F mudamos o seu valor para verdadeiro-> b=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 3) 
então procuramos ->  (v V f) = f - nao encontrado L{}

B -> F mudamos o seu valor para verdadeiro -> b=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 4) 
então procuramos ->  (v v f) = f - nao encontrado L{}

B -> V mudamos o seu valor para falso -> b=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 5) 
então procuramos ->  (f f v) = f - encontramos 7, L{(5,7)}

B -> V mudamos o seu valor para falso -> b=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 6) 
então procuramos ->  (f f f) = v -  nao encontramos 7, L{(5,7)}

B -> F mudamos o seu valor para verdadeiro -> b=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 7) 
então procuramos ->  (f v v) = v -  encontramos 7, porém (5,7) já existe não precisamos colocar novamente L{(5,7)}

B -> F mudamos o seu valor para verdadeiro -> b=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 8) 
então procuramos ->  (f v f) = v -  nao encontramos, L{(5,7)}

ENTÃO A LISTA DE PARES PARA CONDICAO B É l={(5,7)}

3)LEVAR EM CONSIDERACAO A CONDICAÇÃO: C - LISTA DE PARES PARA C{VAZIO}
  A ||(B && C) 	-> r
1) v- v- v  	-> v     
2) v- v- f 	-> v
3) v- f- v	-> v
4) v- f- f 	-> v
5) f- v- v 	-> v
6) f- v- f 	-> f
7) f- f- v 	-> f
8) f- f- f 	-> f

C -> V mudamos o seu valor para falso -> C=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 1) 
então procuramos ->  (v v f) = f - nao encontrado L{}

C -> F mudamos o seu valor para verdadeiro-> C=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 2) 
então procuramos ->  (v v v) = f - nao encontrado L{}

C -> V mudamos o seu valor para falso -> C=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 3) 
então procuramos ->  (v f f) = f - nao encontrado L{}

C -> F mudamos o seu valor para verdadeiro-> C=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 4) 
então procuramos ->  (v f v) = f - nao encontrado L{}

C -> V mudamos o seu valor para falso> C=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 5) 
então procuramos ->  (f v f) = f - encontramos 6, L{(5,6)}

C -> F mudamos o seu valor para verdadeiro -> C=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 6) 
então procuramos ->  (f v v) = v - encontramos 5,  porém (5,6) já existe não precisamos colocar novamente L{(5,6)}

C -> V mudamos o seu valor para falso -> C=f, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 7) 
então procuramos ->  (f f f) = v - nao encontrado  L{(5,6)}

C -> F mudamos o seu valor para verdeiro-> C=v, buscamos encontrar uma condição que tenha valor de R oposto ao da expressão: 8) 
então procuramos ->  (f f v) = v - nao encontrado  L{(5,6)}

ENTÃO A LISTA DE PARES PARA CONDICAO C É l={(5,6)}

4 - ENCONTRAR A LISTA DE EXPRESSOES QUE VAMOS IMPLEMNTAR OS TESTES
	1) começo da lista que tem o menor tamanho e vou incluindo as outras de forma a encontrar N+1 expressoes, no caso 4.
	2) priorizo caminho que me levem a ter N resultados falsos e 1 verdadeiro.

ENTÃO A LISTA DE PARES PARA CONDICAO A É l={(2,6),(3,7),(4,8)}
ENTÃO A LISTA DE PARES PARA CONDICAO B É l={(5,7)}
ENTÃO A LISTA DE PARES PARA CONDICAO C É l={(5,6)}

POSSIVÉIS CAMINHOS

1 - TESTES->{5,6,7,2}
2 - TESTES->{5,6,7,3}
3 - TESTES->{5,6,7,4,8}


MATRICULA DE VESTIBULAR



caminho 1 - valores para as expressões ->{5,6,7,2}


2) v- v- f 	-> v -> entrada pessoa com { idade 18 anos, pai assina, matricula nao paga} -> inscrição aprovada
5) f- v- v 	-> v -> entrada pessoa com { idade 17 anos, pai assina, matricula paga} -> inscrição aprovada
6) f- v- f 	-> f -> entrada pessoa com { idade 17 anos, pai assina, matricula nao  paga} -> inscrição reprovada
7) f- f- v 	-> f -> entrada pessoa com { idade 17 anos, pai nao  assina, matricula paga} -> inscrição reprovada







