# Architecture Patterns with Python

## Why Do Our Designs Go Wrong

1. Encapsulation and Abstractions
2. Layering
3. The Dependency Inversion Principle

## Cap. 1: Domain Modeling

- **Domain modeling**: This is the part of your code that is closest to the business, 
the most likely to change, and the place where you deliver the most value to the 
business. Make it easy to understand and modify.

The domain is a fancy way of saying the problem you’re trying to solve.

- **Distinguish entities from value objects**: A value object is defined by its 
attributes. It’s usually best implemented as an immutable type. If you chan-
ge an attribute on a Value Object, it represents a different object. In con-
trast, an entity has attributes that may vary over time and it will still 
be the same entity. It’s important to define what does uniquely identify an 
entity (usually some sort of name or reference field).
- **Not everything has to be an object**: Python is a multiparadigm language, 
so let the "verbs" in your code be functions. For every FooManager, BarBuilder, 
or BazFactory, there’s often a more expressive and readable manage_foo(), 
build_bar(), or get_baz() waiting to happen.
- **This is the time to apply your best OO design principles**: Revisit the SOLID principles and 
all the other good heuristics like "has a versus is-a," "prefer composition over inheritance," 
and so on. 

## Cap. 2: Repository Pattern

Em cada capítulo nós iremos sumarizar os custos e beneficíos de cada padrão arquitetural que 
introduzimos. Queremos deixar claro que nós não estamos dizendo que cada aplicação necessita
ser construída dessa forma; ás vezes, por causa da complexidade e do domínio do aplicativo,va-
le a pena investir tempo e esforço na adição dessas camadas extras de indireção.

Então vamos mostrar os prós e contras do padrão Repository e da persistence ignorance(
https://www.cosmicpython.com/book/chapter_02_repository.html#_the_normal_orm_way_model_depends_on_orm ).

### Prós

- Temos uma interface simples entre a camada de persistência e nosso modelo de domínio.
- É fácil fazer uma versão fake do repositório para testes de unidade ou para trocar diferentes
soluções de armazenamento, porquê desaclopamos completamente o modelo da infraestrutura.
- Escrever o modelo de domínio antes de pensar sobre persistencia nós ajuda a focar nos problemas
de negócio em questão. Se quisermos mudar radicalmente nossa abordagem, podemos fazer isso em nos-
so modelo, sem precisar nos preocupar com chaves estrangeiras ou migrações até mais tarde.
- Nosso esquema de banco de dados é realmente simples, porque temos controle completo sobre como 
mapeamos nossos objetos em tabelas.

### Contras

- Manter mapeamentos ORM na mão requere trabalho extra e mais código.
- Qualquer camada extra de indireção sempre aumenta o custo de manuten-
ção e adiciona um "WTF Factor" para programadores python que nunca viram
o padrão Repositório antes.

