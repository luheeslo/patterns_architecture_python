---
title: 'Parte 1: Construindo uma arquitetura para suportar modelagem de domínio'
created: '2022-03-21T23:41:05.193Z'
modified: '2022-03-22T00:49:19.540Z'
---

# Parte 1: Construindo uma arquitetura para suportar modelagem de domínio

Nessa parte, o livro se concentra em arquitetar um sistema baseado no modelo de negócio em vez do modelo baseado no esquema de dados. O princípio é **focar no comportamento do sistema primeiro e isso conduzir os requisitos de armazenamento** pois o cliente se importa o que um sistema faz, caso contrário eles continuariam usando a panilha.

Objetivos da parte 1:

- Mostrar como construir um modelo de objeto rico através do TDD.
- Manter o modelo desacoplado dos conceitos técnicos.
- Mostrar como construir um código ignnorante à persistência.
- Criar APIs estáveis em nosso domínio para que possamos refatorar agressivamente.

Para atender esses objetivos, o livro vai apresentar 4 padrões de projeto chaves:

- O padrão **Repository**, uma abstração sobre a ideia de armazenamento persistente.
- O padrão **Service Layer** para definir claramente onde nossos casos de uso iniciam e terminam.
- O padrão **Unit of Work** para providenciar operações atômicas.
- O padrão **Aggregate** para impor a integridade dos dados.

No final, a aplicação deve está projetado de acordo com o diagrama de componente abaixo:

<p align="center">
  <img src="@attachment/apwp_p101.png" width="500">
</p>

O livro irá também falará de acoplamento e abstrações e mostrará porquê escolheu os padrões de abstrações. 
