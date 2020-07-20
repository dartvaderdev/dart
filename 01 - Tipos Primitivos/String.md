# String

As `Strings` são representadas por `''`(aspas simples) ou `""`(aspas duplas), não há diferença entre elas.

### Concatenação e Interpretação

O operador que é utilizado para concatenar Strings é o `+`:

```dart
void main() {
  print('My name is Vader ' + 'Dart Vader');
}
```

O Dart consegue interpretar variáveis dentro de uma `String`, semelhante ao que o PHP faz. Para que o valor da variável seja interpretado, basta colocar a variável dentro da tag `${}` ou apenas o `$` antes da variável:

```dart
void main() {
  String nome = 'Dart';
  int idade = 25;
  bool vivo = false;
  
  print('O nome é ${nome} a idade é $idade e o $nome está ${vivo}!'); // O nome é Dart a idade é 25 e o Dart está false!
  
  print('A soma de 1 + 2 é ${1 + 2}'); // A soma de 1 + 2 é 3
  
  print('O nome ${nome} possui ${nome.length} caracteres'); // O nome Dart possui 4 caracteres
}
```

## Propriedades de String
> [propriedade] -> [tipo retornado]

* **codeUnits** -> List<int>

Essa propriedade retorna uma lista de inteiros onde cada item da lista corresponde ao número do caracter correspondente ao UTF-16.

```dart
void main() {
  String nome = 'Vader';
  
  print(nome.codeUnits); // [86, 97, 100, 101, 114]
}
```

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

* **isEmpty** -> bool

Essa propriedade analisa a variável e se caso a variável estiver vazia, o retorno será `true` caso não esteja vazia o retorno será `false`.

```dart
void main() {
  String myVar = 'Skywalker';
  String myVar2 = '';
  String myVar3 = ' ';
  String myVar4;
  
  print(myVar.isEmpty); // false
  print(myVar2.isEmpty); // true
  print(myVar3.isEmpty); // false
  print(myVar4.isEmpty); // Uncaught TypeError: C.JSNull_methods.get$isEmpty is not a functionError: TypeError: C.JSNull_methods.get$isEmpty is not a function
}
```

* **isNotEmpty** -> bool

Essa propriedade analisa a variável e se caso a variável estiver vazia, o retorno será `true` caso não esteja vazia o retorno será `false`.

```dart
void main() {
  String myVar = 'Skywalker';
  String myVar2 = '';
  String myVar3 = ' ';
  String myVar4;
  
  print(myVar.isNotEmpty); // true
  print(myVar2.isNotEmpty); // false
  print(myVar3.isNotEmpty); // true
  print(myVar4.isNotEmpty); // Uncaught TypeError: C.JSNull_methods.get$isNotEmpty is not a functionError: TypeError: C.JSNull_methods.get$isNotEmpty is not a function
}
```

* **length** -> int

Essa propriedade analisa a variável e retorna o número de caracteres que ela possui.

```dart
void main() {
  String myVar = 'Skywalker';
  String myVar2 = '';
  String myVar3 = ' ';
  
  print(myVar.length); // 9
  print(myVar2.length); // 0
  print(myVar3.length); // 1
}
```

* **runes** -> Runes

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

## Métodos de String
> [propriedade] -> [tipo retornado]

* **compareTo()** -> int

Esse método compara as duas Strings tendo como referência o `length` de cada uma, caso tenha a mesma quantidade de caracteres o retorno será `0`, caso o `length` da variável seja maior que o da variável passada por parâmetro, o retorno será `1` caso seja menor o retrno será `-1`;

```dart
void main() {
  String myVar = 'Skywalker';
  
  print(myVar.compareTo('Skywalker')); // 0
  print(myVar.compareTo('Skywalke')); // 0
  print(myVar.compareTo('Skywalkers')); // 0
}
```

* **contains()** -> bool

Esse método pega o valor passado por parâmetro e tenta encontrar o mesmo valor na string do método, encontrando ao menos uma incidência do valor o método retorna `true`, não encontrando ele retorna `false`. O método também aceita um segundo parâmetro do tipo inteiro que vai informar a partir de qual index(caracter) se iniciará a busca.

```dart
void main() {
  String myVar = 'Skywalker';
  
  print(myVar.contains('a')); // true
  print(myVar.contains('S')); // true
  print(myVar.contains(new RegExp(r'[A-Z]'))); // true
  print(myVar.contains('y', 3)); // false
}
```