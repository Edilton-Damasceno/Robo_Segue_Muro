<h1>
  Robô Seguidor de Muro
</h1>

<p>
 <a href="#-sobre">Sobre</a> | 
 <a href="#-como-funciona">Como funciona</a> | 
 <a href="-preview">Preview</a> |
 <a href="#-tecnologias">Tecnologias</a> | 
 <a href="#-autor">Autor</a>
</p>


## Sobre 

<div align="justify">O projeto consiste em desenvolver um **Robô seguidor de muro** utilizando `Verilog`, uma linguagem de descrição de hardware. O robô é capaz de se locomover em um mapa, buscando um muro à sua esquerda para segui-lo. Sensores são utilizados à frente e a esquerda do Robô para detectar a presença do muro e controlar os movimentos do robô para mantê-lo próximo ao muro.

Utilizando o `Quartus Prime Lite Edition` e o `ModelSim`, o projeto é simulado com uso de um testbench, fornecido pelo docente, para garantir seu correto funcionamento. Essa atividade prática foi proposta na matéria de Laboratório Integrado I, do curso de Engenharia de Computação da Universidade Federal da Bahia.</div>


## Como funciona 
![Alt text](mapa-2.png)

<div align="justify">O mundo do robô é uma matriz de células, na qual cada componente é livre (células brancas) ou ocupado por um muro (células escuras). O robô, mostrado como um triângulo, é colocado em qualquer célula livre, respeitando uma das direções paralelas ao gradeado da matriz (horizontal ou vertical), com sua frente voltada para qualquer um dos 4 sentidos possíveis (Norte, Sul, Leste ou Oeste). O robô possui 2 sensores binários: head (sensor situado na frente do robô, que retorna 1 quando a célula situada à frente do robô está ocupada por um muro – caso contrário, retorna 0) e left (sensor situado na lateral esquerda do robô, que retorna 1 quando a célula do lado esquerdo do robô é ocupada por um muro - caso contrário, retorna 0).</div>

<br>


<div align="justify">Em relação à movimentação, o robô é capaz de fazer apenas 2 tipos de movimento: avançar para uma célula livre à sua frente ou rotacionar 90° para a esquerda, mantendo-se na mesma célula em que se encontra. Cada movimento consome 1 pulso de clock.</div>

O algoritmo controla o robô da seguinter forma:
- Bloco initial:
  + <div align="justify"> Nesse bloco, é definido o estado inicial, de acordo com a FSM (Finite State Machine), o Robô tem três estados, `procurando_muro`, `rotacionado` e `acompanhando_muro`. O estado inicial do robô é `procurando_muro`. </div>

<br>

- Primeiro procedimento/always:
  + <div align="justify">No primeiro procedimento é implementado o decodificador de próximo estado, em um bloco de procedimento always em que em sua lista de sensibilidade está o `clock` (ativo em baixo) e o `reset` (ativo em baixo). Nele é tratado o evento de reset, em que quando ocorre, analisa-se quais são valores de entrada e atribui o devido valor ao estado.</div>

<br>

- Segundo procedimento/always:
  + No segundo procedimento tem-se a atribuição de saídas e do estado, constando na lista de sensibilidade o `state`, o `head` e o `left`. Nesse bloco, avaliamos quais foram as entradas e qual é o estado atual, para definirmos quais serão as saídas e o novo estado.



### Finite Machine State (FSM)
---

![Alt text](image-1.png)

### Simulação
---
  ![Alt text](image.png)
