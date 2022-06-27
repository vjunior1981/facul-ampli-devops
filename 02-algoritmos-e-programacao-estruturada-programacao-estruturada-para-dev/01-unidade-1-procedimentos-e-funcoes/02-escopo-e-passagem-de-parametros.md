# Escopo e passagem de parâmetros



## Introdução da aula

- Você precisa criar funções que facilitem alguns dos cálculos mais comuns usados por estatísticos: a média e a mediana. Com base nessas funções tão importantes, podemos, por exemplo, calcular a média e a mediana dos IMCs de uma determinada população.
- A ideia é que, a partir de um conjunto de números reais (vetor), seu programa calcule a média e a mediana desses conjuntos.
- A média é o resultado da soma de todos os números do conjunto dividida pela quantidade de números que foram somados. Já a mediana será o número que ocupa a posição central do conjunto, considerando que o conjunto esteja crescentemente ordenado.
- Para o cálculo da mediana, há uma particularidade que deve ser observada. Se a quantidade de números do conjunto for ímpar, a mediana será o elemento do meio do vetor.
- Por exemplo, para o vetor [21, 24, 31, 32, 32, **32**, 33, 44, 65], a mediana será o número 32, que está bem no meio do vetor. Porém, se a quantidade de número do conjunto for par, então a mediana será a média aritmética dos dois valores centrais.
- Por exemplo, para o vetor [18, 19, 19, 22, **44**, **45**, 46, 46, 47, 48], a mediana será (44 + 45) / 2 → 89 /2, que é igual a 44,5. Além do cálculo, seu programa deverá exibir os resultados na tela.

---



## Escopo de variáveis, variáveis local e global

- Variáveis são usadas para armazenar dados temporariamente na memória, porém o local em que esse recurso é definido no código de um programa determina seu escopo e sua visibilidade.
- Observe o código Exemplo de variáveis em funções:

```c
#include <stdio.h>

int testar() {
  int x = 10;
  return x;
}

int main() {
  int x = 20;
  printf("\n Valor de x na função main() = %d", x);
  printf("\n Valor de x na função testar() = %d", testar());
  printf("\n");
  return 0;
}
```

- ***<u>Output:</u>***

```
 Valor de x na função main() = 20
 Valor de x na função testar() = 10
```

- Na implementação do código – Exemplo de variáveis em funções –, temos duas variáveis chamadas “x”. Isso acarretará algum erro?  A resposta, nesse caso, é não, pois mesmo as variáveis tendo o mesmo nome, elas são definidas em lugares diferentes: uma está dentro da função *main()* e outra dentro da *testar()*, e cada função terá seu espaço na memória de forma independente.

- A partir desse exemplo, pode-se definir o escopo de uma variável como:

  > a relação de alcance que se tem com o local onde certo recurso se encontra definido, de modo que possa ser ‘enxergado’ pelas várias partes do código de um programa (MANZANO, 2015, p. 288).

- O escopo é dividido em duas categorias:

![image-20220616132419723](./02-escopo-e-passagem-de-parametros.assets/image-20220616132419723.png)

- Veja a seguir que na função principal não foi definida qualquer variável com o nome de “x” e mesmo assim seu valor pode ser impresso na linha 10, pois é acessado o valor da variável global. Já na linha 12 é impresso o valor da variável global modificado pela função *testar()*, que retorna o dobro do valor.

```c
#include <stdio.h>

int x = 10;

void testar() { x = 2 * x; }

int main() {
  printf("\nValor de x global = %d", x);
  testar();
  printf("\nValor de x global alterado em testar() = %d", x);
  printf("\n");

  return 0;
}
```

- ***<u>Output:</u>***

```
Valor de x global = 10
Valor de x global alterado em testar() = 20
```

- No exemplo a seguir, fica clara a utilidade dessa técnica de programação, pois as variáveis são usadas em diferentes funções, otimizando o uso da memória, pois não foi preciso criar mais variáveis locais.

```c
#include <stdio.h>

float t1, t2;

float calcularMedia() { return (t1 + t2) / 2; }
int main() {
  printf("\nDigite as duas temperaturas: ");
  scanf("%f %f", &t1, &t2);
  printf("\nA temperatura média é %.2f ºC", calcularMedia());
  printf("\n");
  return 0;
}
```

- ***<u>Output:</u>***

```
Digite as duas temperaturas: 52 47

A temperatura média é 49.50 ºC
```

- Na linguagem *C*, para conseguirmos acessar o valor de uma variável global, dentro de uma função que apresenta uma variável local com mesmo nome, devemos usar a instrução ***extern\*** (MANZANO, 2015).
- No código – Variável global e local com mesmo nome –, veja como utilizar variáveis globais e locais com mesmo nome na linguagem C.

```c
#include <stdio.h>

int x = 10;

int main() {
  int x = -1;
  int b;
  {
    extern int x;
    b = x;
  }
  printf("\n Valor de x = %d", x);
  printf("\n Valor de b (x global) = %d", b);
  printf("\n");
  return 0;
}
```

- ***<u>Output:</u>***

```
 Valor de x = -1
 Valor de b (x global) = 10
```

- Observe que foi necessário criar uma variável chamada “b”, com um bloco de instruções (linhas 8 – 11), que atribui à nova variável o valor “externo” de *x*.

---



## Passagem de parâmetros para funções e passagem por valor

- Para criar funções usamos a seguinte sintaxe:

```c
    <tipo de retorno> <nome> (<parâmetros>) {
       <Comandos da função>
       <Retorno> (não obrigatório)
    }
```

- Na sintaxe, para criar uma função que  recebe parâmetros é preciso especificar qual o tipo de valor que será  recebido. Uma função pode receber parâmetros na forma de valor ou de  referência (SOFFNER, 2013).
- Na passagem de parâmetros por  valores, a função cria variáveis locais automaticamente para armazenar  esses valores e, após a execução da função, essas variáveis são  liberadas. Veja, no código – Chamada de função com passagem de valores –, um exemplo de definição e chamada de função com passagem de valores.

```c
#include <stdio.h>

int somar(int a, int b) { return a + b; }

int main() {
  int result;
  result = somar(10, 15);
  printf("\nResultado da soma = %d", result);
  printf("\n");

  return 0;
}
```

- ***<u>Output:</u>***

```
Resultado da soma = 25
```

- Ao utilizar variáveis como argumentos na passagem de parâmetros por valores, essas variáveis não são  alteradas, pois é fornecida uma cópia dos valores armazenados para a  função (SOFFNER, 2013). Para ficar clara essa importante definição, veja no código – Variáveis em chamada de função com passagem de valores.
- A execução do programa começa na  linha 10, pela função principal, na qual são criadas duas variáveis “n1” e “n2”. Na linha 13, o comando determina a impressão dos valores das  variáveis, na linha 16, a função *testar()* é invocada passando como parâmetro as duas variáveis.
- Nesse momento, é criada uma cópia de  cada variável na memória para utilização da função. Veja que dentro da  função o valor das variáveis é alterado e impresso, mas essa alteração é local, ou seja, é feita na cópia dos valores e não afetará o valor  inicial das variáveis criadas na função principal.

```c
#include <stdio.h>

void testar(int n1, int n2) {
  n1 = -1;
  n2 = -2;
  printf("\n\nValores dentro da função testar(): ");
  printf("\nn1 = %d e n2 = %d", n1, n2);
}

int main() {
  int n1 = 10;
  int n2 = 20;
  printf("\nValores antes de chamar a função testar(): ");
  printf("\nn1 = %d e n2 = %d", n1, n2);

  testar(n1, n2);

  printf("\n\nValores depois de chamar a função testar(): ");
  printf("\nn1 = %d e n2 = %d", n1, n2);
  printf("\n");

  return 0;
}
```

- ***<u>Output:</u>***

```
Valores antes de chamar a função testar():
n1 = 10 e n2 = 20

Valores dentro da função testar():
n1 = -1 e n2 = -2

Valores depois de chamar a função testar():
n1 = 10 e n2 = 20
```

---



## Passagem por referência

- A utilização de passagem de parâmetros por referência está diretamente ligada aos conceitos de ponteiro e endereço de memória. A ideia da técnica é análoga à  passagem por valores, ou seja, a função será definida de modo a receber  certos parâmetros e “quem” faz a chamada do método deve informar esses  argumentos. Entretanto, o comportamento e o resultado são diferentes.
- Na passagem por referência não será  criada uma cópia dos argumentos passados; na verdade, será passado o  endereço da variável e a função trabalhará diretamente com os valores  ali armazenados (SOFFNER, 2013).
- Veja no código – Variáveis em chamada de função com passagem de referência –, um exemplo de uma função que passa variáveis como referência. Observe que a única diferença desse código para o do código – Variáveis em chamada de função com passagem de valores –, é a utilização dos operadores * e &, porém, o resultado é completamente diferente (figura – Resultado do código – Variáveis em chamada de função com passagem de referência).

```c
#include <stdio.h>

void testar(int *n1, int *n2) {
  *n1 = -1; // o operador * permite acessar o valor da variável
  *n2 = -2;
  printf("\n\nValores dentro da função testar(): ");
  printf("\nn1 = %d e n2 = %d", *n1, *n2);
}

int main() {
  int n1 = 10;
  int n2 = 20;
  printf("\nValores antes de chamar a função testar(): ");
  printf("\nn1 = %d e n2 = %d", n1, n2);

  testar(&n1, &n2);

  printf("\n\nValores depois de chamar a função testar(): ");
  printf("\nn1 = %d e n2 = %d", n1, n2);
  printf("\n");

  return 0;
}
```

- ***<u>Output:</u>***

```
Valores antes de chamar a função testar():
n1 = 10 e n2 = 20

Valores dentro da função testar():
n1 = -1 e n2 = -2

Valores depois de chamar a função testar():
n1 = -1 e n2 = -2
```

---



## Passagem de vetor

- Para finalizar esta aula, vamos ver como passar um vetor para uma função. Esse recurso pode ser utilizado para  criar funções que preenchem e imprimem o conteúdo armazenado em um  vetor, evitando a repetição de trechos de código.
- Na definição da função, os parâmetros a serem recebidos devem ser declarados com colchetes sem especificar o  tamanho, por exemplo: *int testar(int v1[], int v2[])*. Na chamada da função, os parâmetros devem ser passados como se fossem variáveis simples, por exemplo: *resultado = testar(n1,n2).*
- Na linguagem C, a passagem de um  vetor é feita implicitamente por referência. Isso significa que mesmo  não utilizando os operadores “*” e “&”, quando uma função que recebe um vetor é invocada, o que é realmente passado é o endereço da primeira posição do vetor.
- Para entender esse conceito, vamos criar um programa que, por meio de uma função, preencha um vetor de três  posições e em outra função percorra o vetor imprimindo o dobro de cada  valor do vetor.
- Propositalmente criamos a função na  linha 2, recebendo como argumento um vetor de nome “a”, para que você  entenda que o nome da variável que a função recebe não precisa ser o  mesmo nome usado na chamada.
- Na maioria das vezes, utilizamos o mesmo nome como boa prática de programação. Na função *inserir()*, será solicitado ao usuário digitar os valores que serão armazenados no vetor “*numeros*”, pois foi passado como referência implicitamente.

```c
#include <stdio.h>

void inserir(int a[]) {
  int i = 0;
  for (i = 0; i < 3; i++) {
    printf("\nDigite o valor %d: ", i);
    scanf("%d", &a[i]);
  }
}

void imprimir(int b[]) {
  int i = 0;
  for (i = 0; i < 3; i++) {
    printf("\nNúmero[%d] = %d", i, 2 * b[i]);
  }
}
int main() {
  int numeros[3];
  printf("\nPreenchendo o vetor... \n ");
  inserir(numeros);
  printf("\n\nDobro dos valores informados:");
  imprimir(numeros);
  printf("\n");

  return 0;
}
```

- ***<u>Output:</u>***

```
Preenchendo o vetor...

Digite o valor 0: 2

Digite o valor 1: 5

Digite o valor 2: 8


Dobro dos valores informados:
Número[0] = 4
Número[1] = 10
Número[2] = 16
```

---



## Vídeoaula: Escopo e Passagem de Parâmetros

---



## Conclusão

- Você foi contratado por um  laboratório de pesquisa que presta serviço para diversas empresas, e  agora precisa fazer um programa para a equipe de estatísticos.
- Foi solicitado a você automatizar o  cálculo da média e da mediana e de um conjunto de números reais. Seu  programa, além de calcular os resultados, deverá imprimi-los na tela.
- Para implementar essa solução você pode  criar duas funções que recebem como parâmetro um vetor de números reais, juntamente com seu tamanho (quantidade de elementos).

```c
#include <stdio.h>
#define VET_TAM 6

float calcularMedia(float conjunto[], int tam) {
  float soma = 0.0, resultado = 0.0;
  for (int i = 0; i < tam; i++) {
    soma += conjunto[i];
  }
  resultado = soma / (float)tam;
  return resultado;
}

float calcularMediana(float conjunto[], int tam) {
  float resultado = 0.0;
  if (tam % 2 != 0) { // tam é impar
    resultado = conjunto[tam / 2];
  } else {
    resultado = (conjunto[tam / 2] + conjunto[(tam / 2) - 1]) / 2;
  }
  return resultado;
}

int main(void) {
  float vet[VET_TAM] = {1, 2, 3, 4, 5, 6};
  float media = calcularMedia(vet, VET_TAM);
  float mediana = calcularMediana(vet, VET_TAM);
  printf("\nMédia = %.2f", media);
  printf("\nMediana = %.2f", mediana);
  printf("\n");

  return 0;
}
```

- ***<u>Output:</u>***

```
Média = 3.50
Mediana = 3.50
```

