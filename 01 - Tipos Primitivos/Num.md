# Num

Existem três tipos primitivos que herdam da classe **Num** e que podemos usar para trabalharmos com números, são eles:

### num
O `num` recebe qualquer tipo de número, sendo ele inteiro(300) ou de ponto flutuante(1.99), negativo ou positivo. Números de ponto flutuante devem ser representados sempre com `.`(ponto) e nunca com `,`(vírgula).

```dart
void main() {
  num idade = -25;
  num altura = 1.75;
  
  print(idade); // -25
  print(altura); // 1.75
}
```

### int
O `int` recebe qualquer número inteiro positivo ou negativo, qualquer valor diferente de um número inteiro vai fazer com que o compilador te retorne um erro.

```dart
void main() {
  int id = 17;
  
  print(id); // 17
}
```

### double
O `int` recebe qualquer número inteiro positivo ou negativo, qualquer valor diferente de um número inteiro vai fazer com que o compilador te retorne um erro.

```dart
void main() {
  double pi = 3.14159;
  
  print(pi); // 3.14159
}
```

A classe Num possui algumas propriedades e métodos que que nos auxiliam no desenvolvimento, essas propriedades se estendem aos nossos tipos também(num, int e double) abaixo segue a lista dessas propriedades e métodos.


## Propriedades de Num
> [propriedade] -> [tipo retornado]


* **hasCode** -> int
		
Retorna um código de hash que é uma identificação da classe, é útil quando se precisa fazer validações e você deseja fazer sua própria validação, essa é uma funcionalidade difícil de entender, não consegui ter clareza nela, mas consegui absorver um pouco do conceito de `hasCode` através desse [post do Ayush P Gupta na medium.com](https://medium.com/@ayushpguptaapg/demystifying-and-hashcode-in-dart-2f328d1ab1bc) foi a explicação mais clara que eu consegui, mas a aplicação da propriedade é como descrito abaixo.
			
```dart
void main() {
  var eu = new Pessoa('Anakin Skywalker');
  var meuFilho = new Pessoa('Luke Skywalker');
  
  print(eu.hashCode); // 43954095
  print(meuFilho.hashCode); // 255244877
}

class Pessoa{
  String nome;
  Pessoa(this.nome);
}
```
		
* **isFinit** -> bool

Essa propriedade analisa se o valor da variável é um número finito sendo ele positivo ou negativo, caso seja finito ela retornara `true`, caso contrário retornara `false`.

```dart
void main() {
  double infinito = 1 / 0;
  double finito = 7;
  
  print(infinito); // Infinity
  print(infinito.isFinite); // false
  
  print(finito); // 7
  print(finito.isFinite); // true
}
```

* **isInfinit** -> bool

Essa propriedade analisa se o valor da variável é um número infinito sendo ele positivo ou negativo, caso seja infinito ela retornara `true`, caso contrário retornara `false`.

```dart
void main() {
  double infinito = 1 / 0;
  double finito = 30;
  
  print(infinito); // Infinity
  print(infinito.isInfinite); // true
  
  print(finito); // 30
  print(finito.isInfinite); // false
}
```

* **isNaN** -> bool

Caramba, eu até tentei, só que não consegui validar essa função, se você conseguiu me ensina por favor. O mais próximo que cheguei foi o código abaixo que me retorna o erro **Uncaught TypeError: C.JSString_methods.get$isNaN is not a functionError: TypeError: C.JSString_methods.get$isNaN is not a function**.

```dart
void main() {
  dynamic myVar = 'NaN';

  print(myVar.isNaN); // Uncaught TypeError: C.JSString_methods.get$isNaN is not a functionError: TypeError: C.JSString_methods.get$isNaN is not a function
}
```

* **isNegative** -> bool

Essa propriedade analisa se o valor da variável é um número negativo ou não, caso seja ela retorna `true`, caso não seja ela retorna `false`.

```dart
void main() {
  int negativo = -10;
  int positivo = 10;

  print(negativo.isNegative); // true
  print(positivo.isNegative); // false
}
```

* **sign** -> num

Essa propriedade analisa se o valor da variável é menor, igual ou maior que zero, retornando `-1` caso o número seja negativo, `0` caso o número seja 0 e `1` caso o número seja positivo.

```dart
void main() {
  int negativo = -10;
  int zero = 0;
  int positivo = 10;

  print(negativo.sign); // -1
  print(zero.sign); // 0
  print(positivo.sign); // 1
}
```

* **rutimeType** -> type

Essa propriedade analisa o valor da variável e retorna o seu tipo de dado da variável **em tempo de execução**, o Dart vai retornar o tipo da variável naquele momento.

```dark
void main() {
  var myVar = new Pessoa();
  num n = 35.6;
  bool ligado = true;
  dynamic myVar = -3.58;

  print(myVar.runtimeType); // Pessoa
  print(n.runtimeType); // double
  print(ligado.runtimeType); // bool
  
  print(myVar.runtimeType); // double
  myVar = "Agora eu sou uma 'String'";
  print(myVar.runtimeType); // String
  
  
}

class Pessoa{
  String nome;
}
```

## Métodos de Num
> [metodo] -> [tipo retornado]

* **abs()** -> num

Esse método analisa o valor da variável e retorna o seu valor absoluto.

```dart
void main() {
  num myVar = -3.58;

  print(myVar.abs()); // 3.58
}
```

* **ceil()** -> int

Esse método eu tenho que dar o devido crédito à `@gaby93bs` que me ajudou a entender esse método que parece um pouco confuso na primeira impressão, mas que faz todo sentido. Ele retorna o menor número inteiro que seja igual ou maior que o número original, em outras palavras, o método vai retornar o próximo valor inteiro maior ou igual ao número original.

```dart
void main() {
  num myVar = 2.00000001;
  num myVar2 = -2.66;
  num myVar3 = 5;
    
  print(myVar.ceil()); // 3
  print(myVar2.ceil()); // -2
  print(myVar3.ceil()); // 5
}
```