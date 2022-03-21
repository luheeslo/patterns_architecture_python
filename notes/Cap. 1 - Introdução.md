---
tags: [architetural_patterns_python]
title: Cap. 1 - Introdução
created: '2022-03-10T21:32:41.752Z'
modified: '2022-03-15T19:41:08.336Z'
---

# Cap. 1 - Introdução

O desenvolvimento de sistemas de software tende a ser caótico com o tempo, se tornando um grande aglogomerado de classes de gerenciamento e utilitárias, mesmo seguindo alguns princípios básicos de design de código como clean code. Isso resulta geralmente em um forte acoplamento entre as regras de negócio e a infraestrutura, resultando em uma base de código dificil de mudar sem quebrar as funcionalidades. Os engenheiros costuma chamar essa situação onde há forte depêndencias entre os módulos de antipadrão Big Ball of Mud:

<p align="center">
  <img src="@attachment/apwp_0001.png" width="192">
</p>

Segundo o conceito em inglês:

    A big ball of mud is the natural state of software in the same way that wilderness is the natural state of your garden. It takes energy and direction to prevent the collapse.

Apesar disso, existe alguns técnicas para evitar criar uma bola de lama que não tão complexas como imaginamos:


- Encapsulamento e abstrações

- Arquitetura em camadas

- Princípio da inversão de independência


## Encapsulamento e abstrações

- Dois conceitos básicos da ciência da computação.
- *Encapsulamento* está relacionada com duas idéias: simplificar o comportamento e esconder dados. Nesse discussão, usaremos o primeiro conceito.
- Encapsulamos o comportamento identificando uma tarefa que necessita ser feita em nosso código e relaciona-la a uma objeto ou função. Nós chamamos essa função ou objeto de *abstração*.
- Encapsular comportamentos usando abstrações é uma poderosa ferramenta para fazer código mais expressivo, mais testável e fácil de manter.

## Camadas

- Quando uma função, módulo ou objeto usa outro, dizemos que um depende do outro. Essas dependências formam um tipo de rede ou grafo.
 - Mudar um nodo em um grafo se torna difícil pois pode afetar outras partes do sistema. A arquitetura em camadas são uma forma de lidar com esse problema.
 - Nessa arquitetura, nós dividimos nosso código em catgorias ou papéis discretos e  introduzimos quais categorias de código podem chamar umas ás outras. Um exemplo básico é a arquitetura em três camadas:

 <p align="center">
  <img src="@attachment/apwp_0002.png" width="500">
</p>

- Nesse modelo, nós temos componentes de interfaces do usuário, que poderia ser uma página web, uma API ou linha de comando; esses componentes se comunicam com a camada de lógica de negócio que contém nossas regras de negócio e nossos workflows; e finalmente, nós temos uma camada de banco de dados que é responsável por carregar e recuperar dados.

## O Príncipio de Inversão de Dependência

- A definição formal do DIP pode ser dividido em dois conceitos:

1. Módulos de alto nível não devem depender de módulos de baixo nível. Ambos devem depender de abstrações

2. Abstrações não dependem de detalhes. Em vez disso, detalhes devem depender das abstrações

- *Módulos de alto nível* são os códigos que sua organização realmente se importa. Talvez você trabalha para uma companhia farmacêutica e seus módulos de alto nível lidam com pacientes e ensaios. Talvez você trabalha para um banco e seus módulos de alto nível gerenciam transações e trocas. Os módulos de alto nível de um sistema de software são funções, classes e pacotes que lidam com conceitos do mundo real.

- Em contraste, *módulos de baixo nível* são os códigos que sua organização "não se importa". São os assuntos técnicos como HTTP, SMTP, AMPQ, sistemas de arquivos ou sockets de rede que não são interessantes para os stackholders do negócio. Tudo o que importa é se os conceitos de alto nível estejam funcionando corretamente.

- *Depender* não significa *importações* ou *chamadas* necessariamente, mas em vez disso uma idéia mais geral que um módulo *conhece* ou *precisa* de outro módulo.

- O primeiro conceito fala que código de negócio não deve depender de detalhes técnicos; em vez disso **ambos devem usar abstrações pois queremos alterá-los independentemente um do outro**.

- Módulos de alto nível devem ser fáceis de mudar em resposta ás necessidades dos negócios. Módulos de baixo nível dificilmente mudam e.x.: refatorar um nome de função vs definir, testar e fazer deploy de uma migração de banco de dados por causa de uma mudança no nome. Não queremos que a lógica de negócio mude porque estão acoplados a detalhes de infraestrutura de baixo-nível. E vice-versa.  Adicionar uma abstração entre eles permite que os dois mudem independente do outro.

- O segundo coneito vai ser esclarecido no capítulo 4.
