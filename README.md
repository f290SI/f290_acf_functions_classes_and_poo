# Funções, Classes e POO

## Funções

Funções em Dart se assemelham as linguagem convencionais, porém, possuem particularidades muito especificas às quais iremos abordar com exemplos práticos logo abaixo.

> Declaração de Retornos. O Dart permite a omissão de tipos de retorno na declaracao de metodos; facilita o desenvolvimento com códigos menos verbosos, isso é o máximo, porém, dificulta a legibilidade para outros desenvolvedores, ou seja, devemos ponderar a omissão de retonnos em projetos compartilhados.

> A cada alteracao na funcao abaixo, altere a chamada no metodo `main`.
 
### Funções Void

As funções void não possuem retorno e no exemplo abaixo iremos omitir o retorno.

#### Funções sem parametros

```java
// Declaracao de funcoes em Dart

// modificador retorno identificadoMetodo(tipo paramentro) {corpo do metodo}
void exibirNumeroDaSorte() {
  int numeroDaSorte = Random().nextInt(10) + 1;
  print('Seu número da sorte é $numeroDaSorte');
}
```

 A funcao abaixo não possui retorno, e não possui parametros. Iremos gradativamente testar as opções de parametrização de funcoes em Dart para facilitar o entendimento na utilizacao do `Flutter Framework` 

#### Funções com parametros por posição

São as funcoes convencionais onde os parametros declarados, durante a chamada de uma funcao, argumentos devem ser passados na ordem à qual eles foram criados.

```java
void exibirNumeroDaSorte(String nome) {
  int numeroDaSorte = Random().nextInt(10) + 1;
  print('$nome, seu número da sorte é $numeroDaSorte');
}

void exibirNumeroDaSorte(String nome, int limite) {
  int numeroDaSorte = Random().nextInt(limite) + 1;
  print('$nome, seu número da sorte é $numeroDaSorte');
}
```
> Estes são obrigatorios a ordem nao pode ser alterada.

#### Funções com parametros opcionais

Parametros opcionais possibilitam flexibilização na criacao de funcoes e reducao de sobrecargas desnecessarias de metodos.

> Mesmo sendo opcionais, sua posicao ainda importa para a passagem de argumentos na funcao. Voce pode remover o parametro limite na chamada da funcao, mas nao pode alterar sua ordem.

No exemplo abaixo, alteramos o atributo limite o cercando com `[]` e adicionando um valor padrao `[int limite = 100]`. Caso ele nao seja passado, um valor padrao é atribuido. COm certeza economizamos algumas validações aqui!

```java
void exibirNumeroDaSorte(String nome, [int limite = 100]) {
  int numeroDaSorte = Random().nextInt(limite) + 1;
  print('$nome, seu número da sorte é $numeroDaSorte');
}
```

#### Funções com parametros nomeados

> E se nós precisacemos de mais de 1 parametro opicional? Em qual posição ele ficaria? Nao informa-lo afetaria a posicao dos demais?

Faça o teste após aplicar a lateracao abaixo; nela tornamos os 2 parametros opcionais. Teste omitinto 1 parametro por vez.

```java
void exibirNumeroDaSorte([String nome = 'Anonimo', int limite = 100]) {
  int numeroDaSorte = Random().nextInt(limite) + 1;
  print('$nome, seu número da sorte é $numeroDaSorte');
}
```

Os partametros nomeados são opcionais e podemos informá-los em qaulquer ordem. 
Eles aumentam aflexibilidade dos metodos mas em contra-partida fazem com que voce implemente as variações de combinacoes com os parametros nomeados.

> Realize os mesmos testes anteriores, mas desta vez urilizando os paramentros nomeados. Lembre-se se passar os nomes dos parametros!

Altere o método com o codigo abaixo.

```java
void exibirNumeroDaSorte({String nome = 'Anonimo', int limite = 100}) {
  int numeroDaSorte = Random().nextInt(limite) + 1;
  print('$nome, seu número da sorte é $numeroDaSorte');
}
```

> E aí? Funcionou? 

Com este exemplo nós concluimos os testes com parametros de funções e suas particularidas a nível de parametros!

### Funções como Tipo

Como discutido em aula, em `Dart` funções possuem tipo, ou seja existem tipos de dados para funções.

Como tipos, podemos compara-las com variaveis às quais podemos armazenar, utilizar como retorno de funcao e até mesmo passa-las como argumento de função.

> Sim, você realmente leu isso mesmo; super poderes novinhos para as funções.

**Vamos testas estas novas funcionalidades.**

#### Como Tipos

No método `main` remova ou comente os testes anteriores inclua o trecho abaixo.

```java
  Function dobro = (int x) => x * 2;
  print(dobro.runtimeType);
```

> Estamos atribuindo à variavel do tipo Function uma funcao anonima, uma funcao anonima é uma funcao à qual nao atribuimos um identificador.

O resultado foi `(int) => int`, uma funcao que recebe um parametro int e retorna um int; ou seja, armazenamos uma função numa variavel do tipo Function.

Nós podemos também criar uma função multiplier para poder criar funções, dobro, triplo, quadruplo de forma dinamica.

Adicione o trecho abaixo.

```dart
  Function multiplier = (int x, int m) => x * m;

  var triplo = (int v) => multiplier(v, 3);

  print(triplo.runtimeType);

  print(triplo(10));
```

> Como resultado; o objeto triple é apresentado com o tipo (int) => dynamic, ou seja ele é um objeto do tipo Function.

## P.O.O

O paradigma de Programação Orientada a Objetos é fundamental para a criação de aplicações mais fáceis de manter, reutilizar e evoluir.

Iremos verificar os principais conceitos da P.O.O em Dart para facilitar a criação de Apps em Flutter.

> O Dart oferrece algumas vantagens com relação às linguagens mais coinhecidas como Java, como por exemplo os contrutores nomeados, fowards constructors, flexibilização de param,etros, herança múltipla com Mixins, dentre outras. 

### Classes

Assim como nas demais linguagens, as classes em dart são estruturas que definem atributos e comportamentos; estes são utilizados para encapsular regras de negócio que irão reger nossas aplicações.

Vamos criar uma classe simples para exemplificar estes conceitos.

```dart
class Pessoa {
  // Atributos
  String? nome;
  String? email;
  String? telefone;

  // Comportamentos
  cantar() {
    print('$nome cantando!');
  }

  dancar() {
    print('$nome dançando!');
  }

  exibirContato() {
    print('''
    Estamos com agenda disponivel!\n\n
    Nome: $nome\n
    E-Mail: $email\n
    Telefone: $telefone
    ''')
  }

  @override
  String toString() {
    return 'Pessoa(nome=$_nome, telefone=$telefone, email=$email)';
  }
}
```



