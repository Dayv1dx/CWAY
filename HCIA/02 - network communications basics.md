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

Em 1984, a Organização Internacional de Normalização (ISO - _International Organization for Standardization_) apresentou o Modelo de referência de interconexão de sistema aberto (OSI RM - _Open System Interconnection Reference Model_ ) para resolver o problema de compatibilidade entre redes e ajudar os fornecedores a produzir dispositivos de rede. O modelo de referência OSI está rapidamente se tornando o modelo básico de comunicação em rede de computadores. Ao projetar o modelo de referência OSI, o os seguintes princípios são seguidos:

-  Cada camada tem um limite claro para implementar funções específicas;

-  A divisão de camadas é benéfica para o estabelecimento de protocolos de padrão internacional;

- O número de camadas deve ser grande o suficiente para evite a duplicação de funções entre camadas.

Além de ter as seguintes vantagens:

- Simplifica a relação entre as operações de redes;

- Fornece uma compatibilidade _plug-and-play_ e interfaces padrão entre diferentes fornecedores;

- Permite que os fornecedores projetem redes interoperáveis entre dispositivos para promover a padronização;

-  Impede a mudança de rede em uma área de afetar a rede em outra área;

- As redes em diferentes áreas são
separados. Portanto, a rede em cada área pode ser atualizada rapidamente;

- Decompõe problemas complexos de rede em pequenos problemas simples, que são fácil de aprender e operar;

Diferentes camadas do modelo TCP/IP correspondem a protocolos diferentes. O
A pilha de protocolos TCP/IP é uma coleção de protocolos de comunicação de dados, incluindo muitos protocolos. O nome da pilha de protocolos deriva dos dois protocolos principais,
TCP (Protocolo de Controle de Transmissão) e IP (Protocolo de Internet). O TCP/IP pilha de protocolos garante que os dispositivos de rede possam se comunicar entre si. Isto é um conjunto de regras que regem como as informações são transmitidas pela rede.

2. **Encapsulamento e desencapsulamento de dados no modelo TCP/IP:**

![enter image description here](https://embeddedgeeks.com/wp-content/uploads/2020/06/encap-1.png)

Cada camada do TCP/IP permite que dados sejam transmitidos pela rede. Essas camadas usam unidades de dados de protocolo (PDUs) para trocar informações entre si para garantir que os dispositivos de rede possam se comunicar entre si. PDUs em diferentes camadas contêm informações diferentes. Portanto, PDUs em diferentes camadas têm nomes diferentes. Por exemplo, a PDU obtida após a camada de transporte adicionar
o cabeçalho (_header_) TCP para os dados da camada superior é chamado de segmento. O segmento de dados é
transmitido para a camada de rede, e o PDU obtido após a camada de rede
adiciona o _header_ IP é chamado de pacote. O pacote de dados é transmitido para os dados camada de enlace e a PDU obtida após a camada de enlace de dados encapsular os dados cabeçalho é chamado de _frame_, os _frames_ são convertidos em bits e transmitidos
mídia de rede. Este processo de passar dados pela pilha e adicionar cabeçalhos
e trailers é chamado de **encapsulamento**.

Depois dos dados serem encapsulados e transmitidos pela rede, o dispositivo receptor apaga as informações adicionadas (_headers_) e determina como fazer o upload dos dados para as devidas camadas de aplicação pela pilha de protocolo baseado na informações dos _headers_. Esse processo é chamadao de **desencapsulamento**. As camadas dos dispositivos se comunicam entre si por meio de encapsulamento e desencapsulamento.

### **A função da Camada Física:**
A camada física define os processos elétricos e mecânicos e as funções para ativar, manter e e remover linhas quando dois sistemas estão conectados. Ela define os seguintes recursos:

- _Voltage Level_:  Distância máxima de transmissão, modo de conexão física e a razão da transmissão de dados.

Especifica o tipo da mídia, tipo da interface e o tipo de sinalização.

### **A função da camada de dados:**

É a primeira camada lógica dentro da Camada de Dados, ela executa o endereçamento físico no terminal para ajudar a rede de dispositivos a determinar se deve transferir a mensagem para cima ao longo da pilha de protocolos.

A camada de dados se subdivide em duas:

- _LLC Sub-Layer:_ Logic Link Control Sub-Layer
- _MAC Sub-Layer:_ Media Acess Control Sub-Layer

A primeira sub-camada fica localizada entre a camada de rede e a MAC. Ela identifica o tipo de protocolo e encapsulamento dos dados para a transmissão ao longo da rede. Já a sub-camada MAC especifica como os dados são trasmitidos na camada física . Ela define o endereçamento físico, o tipo da rede, a notificação de erro, dentre outros.

- **Endereço da camada de dados e protocolos:** O endereço MAC tem 48 bits e os três primeiros bytes do produtos Huawei são 0x00E0FC. Os protocolos LAN e WAN estão nessa camada.

### **Dispositivos e Funções da Camada de Rede:**
A função dessa camada é encaminhar os pacotes entre as diferentes redes, desde a fonte até o destino final. A camada de dados garante que os pacotes podem ser encaminhados entre os dispositivos na mesma rede (_same link_), e a camada de rede garante que os pacotes podem ser encaminhados desde  a fonte até o destino final pela rede (_cross-link_). 

Existem duas funções na camada de rede:

- Forneçer endereços lógicos: Se os dados forem transmitidos através de redes (_cross-link_), endereços lógicos são usados ​​para endereçamento.

 - Roteamento: Encaminha pacotes de dados de uma rede para outra rede. 

### **Protocolo de Camada de Rede**

O protocolo IP fornece um modo de endereçamento globalmente unificado que protege as diferenças de endereço de rede física e torna possível a pesquisa de rotas. Também fornece um formato de pacotes globalmente unificado que protege as diferenças na camada de enlace de rede e torna  possível a comunicação entre redes.

Protocolo normalmente usado na Camada de Rede:

- **Internet Protocol (IP):** É o protocolo mais importante na camada de rede. Ele fornece lógica funções de  endereçamento, roteamento e encapsulamento e desencapsulamento de pacotes. ICMP, ARP e RARP ajudam IP.

- **Internet Control Message Protocol (ICMP):** É um protocolo de gerenciamento e fornece informações de serviço para IP. As mensagens ICMP são transportadas em pacotes IP.

- **Address Resolution Protocol (ARP):**  Implementa as dinâmicas de mapeamento entre os endereços IP e os endereços de hardware, ou seja, os endereços de hardware são obtidos baseado em um endereço IP conhecido.

- **Reverse Address Resolution Protocol (RARP):** Funciona de forma contrária ao ARP, ou seja, obtém os endereços de IP baseado em um endereço de hardware conhecido.

### Funções da Camada de Aplicação

Existem muitos protocolos na camada de aplicação. Os seguintes protocolos ajudam
você a usar e gerenciar a rede TCP/IP:

- FTP (File Transfer Protocol): Usado para transferir arquivos independentes, geralmente para sessões de usuário interativas.

- HTTP (Hypertext Transfer Protocol): Usado para transferir os arquivos que compõem as páginas da World Wide Web.

- TELNET : Transfere dados com informações de controle Telnet. Ele fornece um método padrão para interagir com dispositivos  terminais ou processos terminais, e suporta conexões terminal a terminal e processo a processo computação distribuída.

- SMTP (Simple Message Transfer Protocol) & POP3(Post Office Protocol).

- DNS (Domain Name Server): Nomes de domínio podem ser convertidos em endereços IP e recursos de nomes de domínio podem ser gerenciados de forma distribuída maneiras.

- TFTP (Trivial File Transfer Protocol): Design de transferência de arquivos para uso geral, alto rendimento.
- RIP (Routing Information Protocol): Um protocolo usado por um roteador para trocar informações de roteamento em uma rede IP.

- SNMP (Simple Network Management Protocol): Coleta rede gerenciamento de informações e trocas de gerenciamento de rede
informações entre o console de gerenciamento de rede e a rede dispositivos (como roteadores, pontes e servidores).

- Radius (Remote Authentication Dial In User Service): Autenticação remota protocolo para acesso dial-up, que implementa autenticação, autorização, e contabilização de usuários de acesso.

### **Endereço da Camada de Rede**

O endereço de rede identifica, de forma única, um dispositivo na camada de rede. Ele consiste em duas partes:

| Network ID | Host ID |
|:--:|:--:|
| 10. |8.2.48 |

Esse endereço é chamado de endereço IP, o qual é um endereço lógico, ao invés de um endereço de hardware, utilizado para comunicação entre dois dispositivos em redes diferentes. É composto por quatro bytes e normamente representado na notação decimal separado por ponto, exemplo 10.8.2.48.

## **Visão Geral da Ethernet**

Ethernet é uma implementação de tecnologia LAN definida no IEEE St 802.3 e faz parte do padrão LAN/MAN.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMTk1MjMzNTEsLTEwNTg3Nzg0ODMsMT
Y2NjU4NTMxMSwzMDE5NTU2MjQsLTY1NTE3NDYzMCwxMjgxMjMy
MTU1LDE3MTg4MjExMDksMTcxODI0MzE3NCwyMTMxNjc1OTEyLC
0yMzI3ODAyNjEsMTAyNjgyOTQ5MCwtMTU1NjM1MzE0OCwxMjIx
Mzc1NDE1LC01MTQxNzQzNTYsOTkwMDAxNzU5LDQ1NzQ4Mzg4NC
wtNjk2NzMxMDc0LDE0MDIyOTk4OCwtNjQyNzk3NDA3LC0yNTgx
NzE2N119
-->