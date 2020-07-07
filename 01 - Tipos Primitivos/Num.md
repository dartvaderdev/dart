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

> [propriedade/metodo] -> [tipo retornado]

## Propriedades de Num
	* **__hasCode__** -> int
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
	* **__isFinit__** -> bool
