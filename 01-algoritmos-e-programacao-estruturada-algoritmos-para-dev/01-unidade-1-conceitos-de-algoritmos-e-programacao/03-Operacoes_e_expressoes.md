# Operações e expressões



## Introdução da aula

- Nesta aula, você verá nesta aula como utilizar os operadores aritméticos, relacionais e lógicos, além de conhecer algumas funções predefinidas.
- A fim de colocarmos em prática os conhecimentos a serem aprendidos, vamos analisar a seguinte situação-problema: Seu chefe está muito contente, pois ele sabe que agora você será capaz de resolver problemas mais desafiadores na empresa. Sua última atividade foi escrever um programa na linguagem *C* que fosse capaz de ler a idade e o nome do cliente, bem como a classificação do filme que ele deseja locar. Posteriormente, seu programa deveria imprimir todas essas informações na tela, conforme o padrão a seguir:

```
Cliente: José das Couves

Idade: 18 anos

Classificação do filme: 12 anos
```

- Agora, seu chefe pediu para você melhorar esse programa, de forma que ele seja capaz de mostrar ao cliente:
  1. se o filme desejado está disponível ou não.
  2. se o filme desejado pode ser locado pelo cliente, levando em consideração se o filme está disponível e se ele é indicado para sua faixa etária.
  3. quantos anos faltam para que a classificação do filme seja adequada à faixa etária do cliente.

---



## Operadores aritiméticos na linguagem C

- Vamos começar a aprimorar nossos algoritmos com as operações aritméticas. Observe o quadro - Operações aritméticas básicas em linguagens de programação -, que demonstra algumas operações disponíveis na linguagem *C* e seus respectivos exemplos.

![image-20220611165941208](./03-Operacoes_e_expressoes.assets/image-20220611165941208.png)

- Vamos criar um programa em *C* que some a idade de duas pessoas e imprima na tela o resultado. No código – Soma da idade de duas pessoas –, está o código que realiza tal processo.

```c
#include <stdio.h>

int main() {
  int idade1 = 0;
  int idade2 = 0;
  int resultado = 0;
  printf("\n Digite a primeira idade: ");
  scanf("%d", &idade1);
  printf("\n Digite a segunda idade: ");
  scanf("%d", &idade2);
  resultado = idade1 + idade2;
  printf("\n Resultado = %d\n", resultado);
}
```

- ***<u>Output:</u>***

```
 Digite a primeira idade: 40

 Digite a segunda idade: 33

 Resultado = 73
```

- Quando trabalhamos com operadores, a **ordem de precedência** é muito importante. Segundo Soffner (2013), os operadores aritméticos apresentam a seguinte ordem de execução:

![image-20220611170535134](./03-Operacoes_e_expressoes.assets/image-20220611170535134.png)

- Das operações aritméticas apresentadas no quadro – Operações aritméticas básicas em linguagens de programação –, a operação módulo (%) talvez seja a que você ainda não tenha familiaridade. Essa operação faz a divisão de um número considerando somente a parte inteira do quociente e retorna o resto da divisão. Como exemplo, vamos aplicar o operador módulo para efetuar o processamento de 43 % 3.

```c
#include <stdio.h>

int main() {
  int resultado = 43 % 3;
  printf("Operacao modulo 43 % 3 = %d\n", resultado);
}
```

- ***<u>Output:</u>***

```
Operacao modulo 43 % 3 = 1
```

- Veja na figura – Operação aritmética módulo –, o cálculo matemático que é efetuado e como o resultado é obtido, você terá o resultado correto? Se for um cálculo para o setor financeiro de uma empresa, seu cálculo mostraria lucro ou prejuízo?

![image-20220611171031616](./03-Operacoes_e_expressoes.assets/image-20220611171031616.png)

- O quadro a seguir apresenta um resumo dos operadores unários.

![image-20220611171128986](./03-Operacoes_e_expressoes.assets/image-20220611171128986.png)

- Esses operadores acrescentam ou diminuem “um” ao valor de uma variável e podem ser usados de duas formas:

  - **Após a variável:**

    - pós-incremento: *x*++; nesse caso, é adicionado 1 (um) após a primeira execução.

    - pós-decremento: *x*- -; nesse caso, é decrementado 1 (um) após a primeira execução.

  - **Antes da variável:**

    - pré-incremento ++*x*; nesse caso, é adicionado 1 (um) antes da primeira execução.

    - pré-decremento --*x*; nesse caso, é decrementado 1 (um) antes da primeira execução.

- Exemplo de código com implemento pré e pós variável. Repare nas linhas "Resultado" o valor do output:

```c
#include <stdio.h>

int main(void) {
  int x = 0;
  int resultado_x = x++;
  printf("\n Resultado = %d", resultado_x);
  printf("\n X = %d", x);

  int y = 0;
  int resultado_y = ++y;
  printf("\n Resultado = %d", resultado_y);
  printf("\n Y = %d\n", y);
}
```

- ***<u>Output:</u>***

```
 Resultado = 0
 X = 1
 Resultado = 1
 Y = 1
```

---



## Operadores relacionais na linguagem C

- Em programação, para compararmos valores, usamos operadores relacionais. O quadro - Operadores relacionais em linguagens de programação -, apresenta os operadores usados na linguagem de programação *C* (DEITEL; DEITEL, 2011).

![image-20220611172122252](./03-Operacoes_e_expressoes.assets/image-20220611172122252.png)

- Os operadores relacionais são usados para construir expressões booleanas, ou seja, expressões que terão como resultado verdadeiro (valor 1) ou falso (valor 0).
- Vamos criar um programa que solicita ao usuário dois números inteiros e faz algumas comparações com esses valores. Veja, no código - Comparações entre dois números -, que na linha 9 comparamos se os números são iguais; na linha 10, se o primeiro (n1) é maior que o segundo (n2) e, na linha 11, se o primeiro é menor ou igual ao segundo.

```c
#include <stdio.h>

int main() {
  int n1 = 0;
  int n2 = 0;
  printf("\n Digite o primeiro numero: ");
  scanf("%d", &n1);
  printf("\n Digite o segundo numero: ");
  scanf("%d", &n2);
  printf("\n n1 e n2 sao iguais? %d", n1 == n2);
  printf("\n n1 e maior que n2? %d", n1 > n2);
  printf("\n n1 e menor ou igual a n2? %d\n", n1 <= n2);
}
```

- ***<u>Output:</u>***

```
 Digite o primeiro numero: 10

 Digite o segundo numero: 25

 n1 e n2 sao iguais? 0
 n1 e maior que n2? 0
 n1 e menor ou igual a n2? 1
```

---



## Operadores lógicos na linguagem C

- O quadro a seguir apresenta os operadores lógicos que podem ser usados na linguagem *C*.

![image-20220611172705734](./03-Operacoes_e_expressoes.assets/image-20220611172705734.png)

- Veja, no código – Operadores relacionais e lógicos –, o uso dos operadores relacionais e lógicos aplicados à comparação dos valores de três variáveis.

```c
#include <stdio.h>

int main() {
  int a = 5, b = 149, c = 15;
  printf("\n (a == b) && (a == c) = %d", ((a == b) && (a == c)));
  printf("\n (a == b) || (a == ¢) = %d", ((a == b) || (a == c)));
  printf("\n !(a == b) || (a == c) = %d\n", !((a == b) || (a == c)));
}
```

- ***<u>Output:</u>***

```
 (a == b) && (a == c) = 0
 (a == b) || (a == ¢) = 0
 !(a == b) || (a == c) = 1

```

---



## Funções predefinidas para a linguagem C

- Entende-se por função: um conjunto de instruções que efetuam uma tarefa específica (MANZANO, 2015, p. 153).
- Existe uma série de bibliotecas e funções disponíveis na linguagem *C* que podem facilitar o desenvolvimento de soluções. Em **C Standard Library Reference Tutorial**, você encontra uma vasta referência a esses elementos.
- Vamos apresentar algumas funções que costumam aparecer com frequência nos programas implementados na linguagem *C* (quadro - Algumas bibliotecas e funções na linguagem C).

![image-20220611173442157](./03-Operacoes_e_expressoes.assets/image-20220611173442157.png)

- A função *strcmp*(*string*1, *string*2) compara o conteúdo de duas *strings* e pode retornar três resultados, o valor nulo (zero), positivo ou negativo, conforme as seguintes regras:
  - quando as *strings* forem iguais, a função retorna 0.
  - quando as *strings* forem diferentes e o primeiro caractere não coincidir entre elas, sendo “maior” na primeira, a função retorna um valor positivo. Entende-se por “maior” o caractere com maior código ASCII, que é atribuído em ordem alfabética, ou seja, o caractere b é maior que a.
  - quando as *strings* forem diferentes e a primeira apresentar o caractere, não coincidente e “menor” que a segunda, então o valor resultante é negativo. Por exemplo, o caractere d é menor que h.
  - caso o primeiro caractere de ambas as *strings* seja igual, as duas regras anteriores são aplicadas para o próximo caractere, e assim sucessivamente.
- Observe o uso da função *strcmp* no código a seguir.

```c
#include <stdio.h>
#include <string.h>

int main(void) {
  printf("\n ARARA == ARARA? %d", strcmp("ARARA", "ARARA"));
  printf("\n ARARA == BANANA? %d", strcmp("ARARA", "BANANA"));
  printf("\n BANANA == ARARA? %d\n", strcmp("BANANA", "ARARA"));
}
```

- ***<u>Output:</u>***

```
 ARARA == ARARA? 0
 ARARA == BANANA? -1
 BANANA == ARARA? 1
```

---



## Conclusão

- Para ampliar sua visão acerca das possibilidades de aplicação dos conhecimentos obtidos até o momento, vamos retomar a situação-problema: Seu chefe solicitou que você aprimore um programa que vem sendo desenvolvido na empresa onde trabalha. Vamos então recordar o que já sabemos?

```c
#include <stdio.h>

#define TAM_NOME_CLIENTE 100

struct cliente {
  char nome[TAM_NOME_CLIENTE];
  int idade;
};

int main(void) {
  struct cliente cli;
  int classificacao_filme;

  printf("\n Informe o nome do cliente: ");
  fflush(stdin);
  fgets(cli.nome, TAM_NOME_CLIENTE, stdin);

  printf("\n Informe a idade do cliente: ");
  scanf("%d", &cli.idade);

  printf("\n Informe a classificação do filme: ");
  scanf("%d", &classificacao_filme);

  printf("\n Cliente: %s", cli.nome);
  printf("\n Idade: %d anos\n", cli.idade);
  printf("\n Classificação do filme: %d anos\n", classificacao_filme);
}
```

- ***<u>Output:</u>***

```
 Informe o nome do cliente: Vitor

 Informe a idade do cliente: 40

 Informe a classificação do filme: 21

 Cliente: Vitor

 Idade: 40 anos

 Classificação do filme: 21 anos
```

- Uma das novas funcionalidades propostas por seu chefe é que o programa informe ao cliente se o filme desejado está disponível para ser locado ou não. Nós já temos uma informação a respeito do filme, que é sua classificação. Então, para que nosso código fique organizado, vamos criar uma *struct* denominada Filme, assim como fizemos com o cliente.

```c
struct filme {
  int classificacao_filme;
  int esta_disponivel;
};
```

- Você também precisa de um trecho de código capaz de ler a informação se o filme está disponível ou não do teclado e imprimi-la na tela. Com os conhecimentos aprendidos, você consegue realizar essa etapa.
- A próxima melhoria a ser feita no programa é informar se o filme desejado pode ser locado pelo cliente, levando em consideração se o filme está disponível e se é indicado para a sua faixa etária.
- Nós já temos as informações necessárias para efetuar esse processamento. Então, vamos criar uma expressão lógica que resultará em 0 (falso) ou 1 (verdadeiro), dependendo dos valores das variáveis de entrada.
- Para que o resultado seja 1 (verdadeiro), a idade do cliente deve ser maior ou igual à classificação do filme **e** o filme deve estar disponível. Com base na versão atual do código do programa, a expressão lógica a ser utilizada é:

```c
(fi.esta_disponivel) && (cli.idade >= fi.classificacao_filme))
```

- Por fim, o programa deve informar quantos anos faltam para que a classificação do filme seja adequada à faixa etária do cliente. Nesse caso, precisamos pensar um pouco mais para resolver esse problema com os recursos que aprendemos até o momento.
- Você se lembra de que o resultado de uma expressão lógica é 0 ou 1. Então, se pensarmos na expressão (cli.idade < fi.classificacao_filme), seu resultado será 0 quando a idade do cliente for maior ou igual à classificação do filme ou 1, quando a idade do cliente for menor do que a classificação do filme.

```c
(cli.idade < fi.classificacao_filme) * (fi.classificacao_filme - cli.idade))
```

- O resultado dessa expressão será um número inteiro, que responde à seguinte pergunta: “quantos anos faltam para que a classificação do filme seja adequada à faixa etária do cliente?”.

```c
#include <stdio.h>

#define TAM_NOME_CLIENTE 100

struct cliente {
  char nome[TAM_NOME_CLIENTE];
  int idade;
};

struct filme {
  int classificacao_filme;
  int esta_disponivel;
};

int main(void) {
  struct cliente cli;
  struct filme fi;

  printf("\n Informe o nome do cliente: ");
  fflush(stdin);
  fgets(cli.nome, TAM_NOME_CLIENTE, stdin);

  printf("\n Informe a idade do cliente: ");
  scanf("%d", &cli.idade);

  printf("\n Informe a classificação do filme: ");
  scanf("%d", &fi.classificacao_filme);

  printf(
      "\n Informe (0) se o filme não está disponível e (1) caso contrário: ");
  scanf("%d", &fi.esta_disponivel);

  printf("\n Cliente: %s", cli.nome);
  printf("\n Idade: %d anos", cli.idade);
  printf("\n Classificação do filme: %d anos", fi.classificacao_filme);
  printf("\n Está disponível: %d", fi.esta_disponivel);
  printf("\n Filme pode ser locado pelo cliente: %d",
         (fi.esta_disponivel) && (cli.idade >= fi.classificacao_filme));
  printf("\n Anos restantes: %d\n", (cli.idade < fi.classificacao_filme) *
                                      (fi.classificacao_filme - cli.idade));
}
```

- ***<u>Output:</u>***

```
 Informe o nome do cliente: Vitor

 Informe a idade do cliente: 40

 Informe a classificação do filme: 21

 Informe (0) se o filme não está disponível e (1) caso contrário: 1

 Cliente: Vitor

 Idade: 40 anos
 Classificação do filme: 21 anos
 Está disponível: 1
 Filme pode ser locado pelo cliente: 1
 Anos restantes: 0
```

