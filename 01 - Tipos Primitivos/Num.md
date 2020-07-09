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

Essa propriedade analisa se o valor da variável é um número finito sendo ele positivo ou negativo, caso seja finito ela retornara `true`, caso contrário retornara `false`. Tenho que dar os créditos do estudo dessa propriedade ao [@danielreisduarte](https://www.instagram.com/danielreisduarte/?hl=pt-br "Instagram dele")(um programador Delphi fora da curva) que me ajudou a encontrar uma situação onde o Dart reconhece um 'número' infinito, e como o Daniel frisou bem kkkkkk, infinito não é um número, é uma ideia.

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

```dart
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

Esse método eu tenho que dar o devido crédito à [@gaby93bs](https://www.instagram.com/gaby93bs/?hl=pt-br "Instagram dela")(uma contadora top, que entende o que é um plano de contas e centro de custo) que me ajudou a entender esse método que parece um pouco confuso na primeira impressão, mas que faz todo sentido. Ele retorna o menor número inteiro que seja igual ou maior que o número original, em outras palavras, o método vai retornar o próximo valor inteiro maior ou igual ao número original.

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

* **ceilToDouble()** -> double

Não consegui diferenciar esse método do `ceil()`, pela documentação eu acreditei que ele teria a mesma função do `ceil()` só que retornando um `double`, porém quando fiz uma validação do tipo, ele retornou como `int`, então fica em aberto essa funcionalidade.

```dart
void main() {
  num myVar = 2.00000001;
  num myVar2 = -2.66;
  num myVar3 = 5;
  num x = myVar3.ceilToDouble();
    
  print(myVar.ceilToDouble()); // 3
  print(myVar2.ceilToDouble()); // -2
  print(myVar3.ceilToDouble()); // 5
  
  print(x.runtimeType); // int
}
```

* **clamp()** -> num

Esse método analisa o valor da variável e se o valor da variável estiver dentro do intervalo informado no parâmetro, o método retornara o valor da variável, caso não esteja no intervalo informado, o método retornara o limite mínimo ou máximo que o valor não alcançou ou extrapolou.

```dart
void main() {
  num myVar = 77;
  
  print(myVar.clamp(1, 100)); // 77
  print(myVar.clamp(100, 200)); // 100
  print(myVar.clamp(1, 50)); // 50
}
```

* **compareTo()** -> int

Esse método analisa o valor da variável e compara com um outro valor passaado por parâmetro na função `compareTo()`, caso o valor que está sendo comparado seja igual ao valor do parâmetro, a função retornará o valor `0`, se for menor ela retornará `-1` e se for maior retornará `1`.

```dart
void main() {
  num myVar = 3;
  
  print(myVar.compareTo(1)); // 1
  print(myVar.compareTo(10)); // -1
  print(myVar.compareTo(3)); // 0
}
```

* **floor()** -> int

Esse método é semelhante ao `ceil()` só que o inverso dele. Ele retorna o maior número inteiro que seja igual ou menor que o número original, em outras palavras, o método vai retornar o valor inteiro anterior menor ou igual ao número original.

```dart
void main() {
  num myVar = 2.00000001;
  num myVar2 = -2.66;
  num myVar3 = 5;
    
  print(myVar.floor()); // 2
  print(myVar2.floor()); // -3
  print(myVar3.floor()); // 5
}
```

* **floorToDouble()** -> double

Esse método segue a mesma condição do `ceilToDouble()`, o `floorToDouble()` seria o mesmo que o `floor()` porém retornando um `double`, só que assim como o `ceilToDouble` ele não está retornando um `double` e sim um `int`.

```dart
void main() {
  num myVar = 2.00000001;
  num myVar2 = -2.66;
  num myVar3 = 5;
  num x = myVar3.floorToDouble();
    
  print(myVar.floorToDouble()); // 2
  print(myVar2.floorToDouble()); // -3
  print(myVar3.floorToDouble()); // 5
  
  print(x.runtimeType); // int
}
```

* **remainder()** -> num

Esse método analisa o valor da variável e retorna o resto da divisão enquanto o quociente for inteiro.

```dart
void main() {
  num myVar = 7;
  num myVar2 = 10;
  num myVar3 = 120;
  
  print(myVar.remainder(4)); // 3
  print(myVar2.remainder(2)); // 0
  print(myVar3.remainder(10)); // 0
}
```

* **round()** -> int

Esse método analisa o valor da variável e retorna o número inteiro mais próximo do valor da variável, ele usa apena a primeira casa decimal para definir se o arredondamento será para mais ou para menos.

```dart
void main() {
  num myVar = 7.2;
  num myVar2 = 1.4999;
  num myVar3 = 1.5000;
  
  print(myVar.round()); // 7
  print(myVar2.round()); // 1
  print(myVar3.round()); // 2
}
```

* **roundToDouble()** -> double

Esse é mais um método que ficou com sua funcionalidade incoerênte, porque o valor retornado não é um double e o arredondamento feito está semelhante ao método `round()`.

```dart
num myVar = 7.2;
  num myVar2 = 1.4999;
  num myVar3 = 1.5000;
  double x = myVar3.roundToDouble();
  
  print(myVar.roundToDouble()); // 7
  print(myVar2.roundToDouble()); // 1
  print(myVar3.roundToDouble()); // 2
  
  print(x.runtimeType); // int
```

* **toDouble()** -> double

Esse método é responsável por fazer a converção do valor original para o tipo `double`. Porém quanto analiso o tipo retornado, parece que a converção não foi feita, o método sempre me retorna o tipo original.

```dart
void main() {
  num myVar = 7;
  var x = myVar.toDouble();
  
  print(x.runtimeType); // int
}
```

* **toInt()** -> int

Esse método é responsável por fazer a converção do valor original para o tipo `int`.

```dart
void main() {
  double myVar = 7.5;
  num x = myVar.toInt();
  
  print(x.runtimeType); // int
}
```

* **toString()** -> String

Esse método é responsável por fazer a converção do valor original para o tipo `String`.

```dart
void main() {
  double myVar = 10.3;
  var x = myVar.toString();
  
  print(x.runtimeType); // String
}
```

* **toStringAsExponential()** -> String

Esse método analisa o valor da variável e retorna sua representação exponencial.

```dart
void main() {
  double myVar = 7.123;
  var x = myVar.toStringAsExponential(0);
  var y = myVar.toStringAsExponential(3);
  
  print(x); // 7e+0
  print(y); // 7.123e+0
}
```

* **toStringAsFixed()** -> String

Esse método analisa o valor da variável e retorna uma `String` fazendo um __truncate__ do valor. O valor informado no parâmetro da função vai ser a quantidade de casas decimais que o retorno do método vai levar em consideração.

```dart
void main() {
  double myVar = 7.1236564;
  var x = myVar.toStringAsFixed(0);
  var y = myVar.toStringAsFixed(3);
  
  print(x); // 7
  print(y); // 7.124
}
```

* **toStringAsPrecision()** -> String

Esse método pelo que percebi, realiza praticamente a mesma tarefa do `toStringAsFixed()`, porém o `toStringAsPrecision()` não aceita `0` como um parâmetro, outra diferença é que o `toStringAsFixed()` retonar a quantidade de casas decimais passada por parâmetro, já o `toStringAsPrecision()` retorna a quantidade de 'números' de acordo com valor passado por parâmetro, com certeza existem mais diferênças, porém não me eprofundarei nesses métodos.

```dart
void main() {
  double myVar = 7.1236564;
  var x = myVar.toStringAsPrecision(1);
  var y = myVar.toStringAsPrecision(3);
  
  print(x); // 7
  print(y); // 7.12
}
```

* **truncate** -> int

Esse método analisa o valor da variável e retorna seu número inteiro desprezando todos os números depois da vírgula.

```dart
void main() {
  num myVar = 171.1236564;
  num myVar2 = 171.50000;
  var x = myVar.truncate();
  
  print(x); // 171
  print(myVar2.truncate()); // 171
}
```

* **truncateToDouble()** -> double

Esse método vai entrar para a lista dos métodos com a funcionalidade incoerênte, porque pelo que entendi, o método ignoraria as casas decimais, porém retornaria um `double`, ele realmente ignorou as casas decimais, porém não retornou um `double`.

```dart
void main() {
  num myVar = 171.1236564;
  num myVar2 = 171.50000;
  var x = myVar.truncateToDouble();
  
  print(x); // 171
  print(myVar2.truncateToDouble()); // 171
}
```

