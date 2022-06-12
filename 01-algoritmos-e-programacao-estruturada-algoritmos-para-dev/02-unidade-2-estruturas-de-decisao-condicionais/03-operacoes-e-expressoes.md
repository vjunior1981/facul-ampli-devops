# Operações e expressões



## Introdução da aula

- Nesta aula, você terá a oportunidade de estudar a estrutura de repetição usando “*for*” (para), o histórico e as aplicações da repetição determinística, assim como o comparativo com estruturas condicionais.
- **Situação-problema**: Você, novamente, recebeu uma missão da instituição de ensino na qual se formou.
- Foi solicitado um programa em linguagem *C* para transformar o nome digitado dos alunos em letras maiúsculas, assim, caso uma pessoa digite o nome do aluno em letras minúsculas, o programa transformará automaticamente em maiúsculas. Essa é uma prática muito comum no dia a dia do desenvolvimento de software.
- Por exemplo, ao fazer a busca por um aluno da instituição usando seu nome, antes, é necessário transformar o nome informado, bem como os nomes dos alunos cadastrados no software para caixa alta (maiúsculas) ou baixa (minúsculas).
- Isso evitará que o fato de uma letra ser informada maiúscula ou minúscula prejudique a busca, ou seja, tanto faz se o usuário informou “josé” ou “José” ou “JOSÉ”; o resultado da busca deve ser sempre o mesmo.
- Outra aplicação prática desse exercício é quando se quer gerar uma lista de presença dos alunos de determinada turma. É comum sempre imprimir os nomes em caixa alta (maiúsculas), mantendo um padrão entre os nomes e facilitando a leitura do professor. Após a criação do programa, entregue o código no formato TXT para documentação.
- Qual função em linguagem *C* devemos usar para converter maiúsculas em minúsculas e vice-versa? São tantas as possibilidades de aplicação de estrutura de repetição que não podemos deixar passar esse novo desafio.

---



## Estrutura de repetição com variáveis de controle - *for*

- Esse comando – que em português significa “para”, segundo Mizrahi (2008), é geralmente usado para repetir um comando ou uma sequência de comandos um determinado número de vezes, isto é, podemos determinar quantas vezes acontecerá a repetição.
- Veja na figura a seguir como é representada a estrutura de repetição usando o comando *for*.

![image-20220611201346499](./03-operacoes-e-expressoes.assets/image-20220611201346499.png)

- A sintaxe usando a linguagem de programação em *C* fica da seguinte forma:

```c
for(inicialização; condição de parada; incremento) {
  comando ou sequência de comandos;
}
```

- Na aplicação do comando *for* você encontra três expressões separadas por ponto e vírgula. O significado de cada uma delas é apresentado a seguir:

![image-20220611201514234](./03-operacoes-e-expressoes.assets/image-20220611201514234.png)

- Para facilitar ainda mais, veja a seguinte representação:

```c
for (y = 0; y <= 10; y++)
```

![image-20220611201551241](./03-operacoes-e-expressoes.assets/image-20220611201551241.png)

- Agora, vamos aplicar essa representação em um programa que mostra uma sequência de números, em que y vai de 0 a 10. Observe a saída do código:

```c
#include <stdio.h>

int main() {
  int x, y;
  for (y = 0; y <= 10; y++) {
    printf("\ny=%d", y);
  }
  printf("\n");
  return 0;
}
```

- Output

```
y=0
y=1
y=2
y=3
y=4
y=5
y=6
y=7
y=8
y=9
y=10
```

- O incremento em um comando *for* não precisar ser unitário (de um em um). Você pode utilizar incrementos maiores para, por exemplo, imprimir todos os números pares de 0 a 10:

```c
#include <stdio.h>

int main() {
  int x, y;
  for (y = 0; y <= 10; y += 2) {
    printf("\ny=%d", y);
  }
  printf("\n");
  return 0;
}
```

- ***<u>Output:</u>***

```
y=0
y=2
y=4
y=6
y=8
y=10
```

- No código a seguir, vamos criar uma contagem regressiva de um número qualquer, digitado pelo usuário:

```c
#include <stdio.h>

int main() {
  int contador;
  printf("\nDigite um número para contagem regressiva: ");
  scanf("%d", &contador);
  for (contador; contador >= 1; contador--) {
    printf("%d ", contador);
  }
  return 0;
}
```

- ***<u>Output:</u>***

```
Digite um número para contagem regressiva: 8
8 7 6 5 4 3 2 1
```

- Você pode usar o comando *break* dentro de um laço for para uma determinada condição, forçando, assim, o término do laço. Veja o exemplo a seguir:

```c
#include <stdio.h>

int main() {
  int parar_em = 30;
  for (int i = 0; i < 100; i++) {
    if (i == parar_em) {
      break;
    }
    printf("%d ", i);
  }
}
```

- ***<u>Output:</u>***

```
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29
```

---



## Vetores e comando continue

- Segundo Manzano (2013; 2015), vetor (*array*) é um tipo especial de variável, capaz de armazenar diversos valores “ao mesmo tempo”, usando um mesmo nome de variável.
- Vamos a outro exemplo em que armazenamos valores em um vetor. Lembre-se de que os elementos de um vetor são acessados por meio de índices, que vão de 0 à *n* – 1, em que *n* é a quantidade de elementos.

```c
#include <stdio.h>

#define VET_TAM 5

int main() {
  int num[VET_TAM];

  for (int i = 0; i < VET_TAM; i++) {
    printf("\nEntre com o número: ");
    scanf("%d", &num[i]);
    printf("\nO valor digitado foi: %d", num[i]);
  }
  return 0;
}
```

- ***<u>Output:</u>***

```
Entre com o número: 10

O valor digitado foi: 10
Entre com o número: 3

O valor digitado foi: 3
Entre com o número:
```

- Que tal usarmos o comando *for* e *while* no mesmo código? O programa a seguir encontra a primeira posição para um determinado número inserido pelo usuário. Vejamos, então, como fica a programação:

```c
#include <stdio.h>

#define VET_TAM 5

int main() {
  int vetor[VET_TAM];
  int num, i = 0, achou = 0;

  // Preenche vetor
  for (int i = 0; i < VET_TAM; i++) {
    printf("\nEntre com um número: ");
    scanf("%d", &vetor[i]);
  }

  printf("\n\nInforme o número a ser encontrado: ");
  scanf("%d", &num);

  while (i < VET_TAM) {
    if (vetor[i] == num) {
      achou = 1;
      break;
    }
    i++;
  }

  if (achou == 1) {
    printf("\nO número %d foi encontrado na posição %d do vetor", num, i);
  } else {
    printf("\nO número %d não foi encontrado no vetor", num);
  }

  return 0;
}
```

- ***<u>Output:</u>***

```
Entre com um número: 2

Entre com um número: 5

Entre com um número: 3

Entre com um número: 6

Entre com um número: 7


Informe o número a ser encontrado: 6

O número 6 foi encontrado na posição 3 do vetor
```

- Dando prosseguimento aos nossos estudos, vamos conhecer o comando *continue*. Segundo Damas (2016), um comando *continue*, dentro de um laço, possibilita que a execução de comandos corrente seja terminada, passando à próxima iteração do laço, ou seja, quando usamos o *continue* dentro de um laço, este é passado para a próxima iteração.
- Vejamos, agora, um programa que percorrerá os números de 1 a 30, imprimindo na tela apenas os números ímpares.
- Nas iterações com números pares, o comando *continue* é usado para levar o programa para a próxima iteração. As linhas 3 a 8 declaram um comando for para iterar (percorrer) entre os números 1 a 30, imprimindo seu valor da tela, conforme mostra a linha 7.
- Contudo, na linha 4 é feito um teste condicional para verificar se o número da iteração corrente, representado pela variável i, é par.
- Caso seja, então o comando continue é executado, fazendo com que o laço for vá para a próxima iteração, sem executar as linhas que estão abaixo do comando *continue*. Nesse sentido, pode-se afirmar que o programa não imprime o valor dos números pares na tela.

```c
#include <stdio.h>

int main() {
  for (int i = 1; i <= 30; i++) {
    if (i % 2 == 0) {
      continue;
    }
    printf("%d ", i);
  }
}
```

- ***<u>Output:</u>***

```
1 3 5 7 9 11 13 15 17 19 21 23 25 27 29
```

- Segundo Damas (2016), o comando *continue* poderá apenas ser utilizado dentro de laços. No entanto, o comando *break* pode ser utilizado em laços ou nas instruções *switch*. Existem outras formas de continuar uma instrução dentro do laço?

---



## Vídeoaula: Estruturas de repetição determinísticas

- encerrando pelo dia 11/06/2022
