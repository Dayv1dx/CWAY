# NETWORK COMMUNICATIONS BASICS

## **Visão Geral da Comunicação de Dados**

De acordo com o protocolo de comunicação, o dado é transferido entre uma unidades funcionais usando tecnologia de transmissão, de modo a realizar a troca de informações entre computadores e terminais, e entre outros dispositivos terminais de dados.

Uma comunicação de dados completa deve ser composta por cinco partes?

- **Mensagem:** Um pacote é um bloco de dados em comunicação. Informações como textos, números, imagens, audio e vídeos são codificados e transmitidos em pacotes.

- **Remetente:** É o dispositivo que manda os pacotes, pode ser um computador, celular, servidor, etc.

- **Receptor:**  É o dispositivo que recebe os pacotes, pode ser um computador, celular, servidor, etc.

- **Meio:** Se refere ao meio para o sinal de transmissão. Meios de transmissão comuns em LANs incluem fibras ópticas, cabos coaxiais e pares trançados.

- **Protocolo:** É o conjunto de regras que governam a comunicação de dados, isso representa um conjunto de convenções entre os dispositivos de comunicação. Sem protocolo, mesmo que dois dispositivos estiverem conectados fisicamente, eles não podem se comunicar.

### **Características da Comunicação de Dados**

A comutação de pacotes sem conexão usa a comutação de pacotes para encapsular as informações do usuário em pacotes. Cada pacote possui um cabeçalho (_header_), que é
usado para roteamento, controle de erros e controle de fluxo. A duração e o intervalo de cada pacote pode ser alterado. Portanto, a comutação de pacotes suporta múltiplas taxas. Nesse tipo de comutação os pacotes ocupam recursos da rede somente quando eles são transmitidos. Os recursos de rede podem ser compartilhados por serviços.

- **Modos de transmissão:**

	- _Simplex:_ Nesse modo a comunicação é unidirecional, apenas um dos dispositivos pode enviar pacotes. Teclados e displays são exemplos desse tipo de comunicação, pois o teclado apenas pode ser usado para _input_ e um monitor apenas para _output_.

	- _Half-duplex:_ Nesse modo a comunicação é bidirecional, ambos dispositivos podem mandar pacotes, porém não ao mesmo tempo. O _walkie-talkie_ é um exemplo típico desse sistema.
	
	- _Full-duplex:_ Nesse modo a comunicação, ambos dispositivos podem mandar e receber dados de forma simultânea. A Rede telefônica é um exemplo.

## **Protocolo TCP/IP**

1. **Estrutura do modelo TCP/IP:**

![enter image description here](https://media.geeksforgeeks.org/wp-content/uploads/20230417045622/OSI-vs-TCP-vs-Hybrid-2.webp)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgxMTgyMDU2MSwxMjE2OTQ4MTgsLTEzOD
AwODMzNzYsLTIwMDI0MDc0ODEsLTE4MzA2MTExMjgsNDU5NDAw
MzAwXX0=
-->