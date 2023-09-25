# **Princípios do GPON**

![arquitetura GPON](https://i.ytimg.com/vi/Oi0SNlMzMjQ/maxresdefault.jpg)

PON é uma rede óptica passiva _point-to-multipoint_ (P2MP), já GPON (_Gigabit-capable Passive Optical Network_) é um tipo de rede PON com uma capacidade de _downstream_ de 2,5Gbps e 1,25 Gbps no sentido _upstream_, ela é composta basicamente por:

- OLT (Optical line terminal)
- ODN, que é uma rede de distribuição que consiste nos _splitters_ e nas fibras ópticas, ou seja, as conexões físicas da rede.
- ONU (Optical network unit) ou ONT (Optical network terminal)

Parâmetro básicos da rede GPON:

|  Parâmetro | Valor  |
|--|--|
| Máxima distância lógica | 60 km  
| Máxima distância física de trasmissão | 40 km |
| Máxima distância diferencial | 40 km | 
| Razão máxima no splitter | 1:128 |

## **Modos de multiplexação de dados no GPON**

O GPON implementa uma transmissão bidirecional em uma única fibra e esse sistema usa a tecnologia WDM (_Wavelength Division Multiplexing_). Para separar os sinais para múltiplos usuários na mesma fibra óptica, são usadas as seguintes tecnologias:

- _Broadcast_ é usado para _downlink_
- TDMA (Time Division Multiple Access) é usado para _uplink_  

![enter image description here](https://jornathunderlinkcom.files.wordpress.com/2016/04/e59bbee789876.png)

### **GPON Downstream**

<img src="images/06 - gpon down.png"/>

### **GPON Upstream**

<img src="images/06 - gpon up.png"/>


## **Modos de multiplexação de dados no GPON**

<img src="images/06 - gpon service map.png"/>

O quadro do modo de encapsulamento GPON (GEM) é a menor unidade portadora de serviço na tecnologia GPON e é a estrutura de encapsulamento mais básica. Todos os serviços são encapsulados em frames GEM e transmitidos em linhas GPON. Os serviços são identificados pelas portas GEM. Cada porta GEM é identificada por um ID de porta exclusivo, que é alocado globalmente pela OLT. Ou seja, cada ONU/ONT conectada à OLT não pode utilizar uma porta GEM com o mesmo ID de porta. Uma porta GEM identifica o canal virtual de serviço entre a OLT e a ONU/ONT, ou seja, o canal que transporta o fluxo de serviço. A porta GEM é semelhante ao VPI/VCI na conexão virtual ATM.

T-CONT: É uma operadora para transporte de serviços no sentido upstream GPON. Todas as portas GEM precisam ser mapeadas para T-CONTs. A OLT transmite serviços upstream no modo de agendamento DBA. Um T-CONT é a unidade básica de controle dos fluxos de serviço upstream em um sistema GPON. Cada T-CONT é identificado exclusivamente por um Alloc-ID. O Alloc-ID é alocado globalmente pela OLT. Ou seja, cada ONU/ONT conectada à OLT não poderá utilizar o T-CONT com o mesmo Alloc-ID.

A Figura 1 mostra o princípio de multiplexação de serviço no sistema GPON. Diferentes serviços são mapeados para diferentes portas GEM no ONT. As portas GEM transportam os serviços e então mapeiam os serviços para diferentes tipos de T-CONTs para transmissão upstream. Um T-CONT é uma unidade portadora básica na direção upstream de uma linha GPON. No lado OLT, o T-CONT primeiro demodula a unidade de porta GEM e, em seguida, envia a carga útil da porta GEM demodulada para o chip GPON MAC para processamento. Outras etapas de processamento são as mesmas do switch ou da rede de acesso.

## **A chave da tecnologia GPON**

1. Ranging
2. Upstream dynamic bandwidth
3. Downstream AES encryption

### **Ranging**

A distância entre as ONUs e as OLTs, e são diferentes, consequentemente o tempo de transmissão dos sinais ópticos na fibra também. A OLT aloca diferentes _timeslots_ para cada ONU fazer o _upstream_ dos dados, para garantir que cada ONU use um _timeslots_ diferente e evite conflitos de dados, a OLT usa o RTD (Round trip delay). Esse processo consiste na OLT enviar um sinal e com isso calcular a distância física de cada ONU conectada e propõe o _equalization delay_ (EqD) para garantir que não ocorra conflitos no splitter quando as ONU mandarem os dados.

### **Upstream dynamic bandwidth**

DBA (Dynamic Bandwith Assigment) é um jeito de alocar a largura de banda em microsegundos ou milisegundos, isso melhora a utilização das portas PON. Funciona de dois modos:

- SR-DBA: _status report-DBA_
- NSR-DBA: _non status report-DBA_

### **Downstream AES encryption**

A tecnologia broadcast é usada no _downstream_ do GPON, como garantir que o dado de uma ONU não irá para outra? Usano um algoritmo de encriptação chamado _Advanced Encryption System_ (AES)

<img src="images/06 - aes.png"/>

## **Gerenciamento e modos de provisionamento do sistema GPON**

### **GPON Terminal Authentication**

Na autenticação GPON, a OLT autentica a validação de uma ONU baseado no Serial Number (SN) da ONU ou na senha, e rejeita o acesso de ONU não autorizadas. No sistema GPON, apenas as ONU autenticadas podem acessar o sistema PON. Isso atende ao requisito de flexibilidade and _easy-to-maintain_ da rede. Os principais modos de autenticação são:

1. SN authentication
2. SN + Password authentication

### **GPON Terminal Management Model**

O sistema GPON gerencia a ONU através do canal de gerenciamento OMCI entre a OLT and a ONU.

- OMCI: _ONU Management Control Interface_, OMCI é um protocolo de gerenciamento mestre-escravo. A OLT é o dispositivo mestre e uma ONU é o dispositivo escravo. Após a ONU concluir o processo de registro, um canal OMCI é estabelecido. O OLT controla múltiplas ONUs conectadas a ela através de canais OMCI. Esse protocolo suporta configuração offline de ONUs. A ONU não precisa salvar as configurações localmente, o que facilita o provisionamento do serviço

- SNMP: _Simple Network Management Protocol_
- 
<img src="images/06 - omci_1.png"/>

<img src="images/06 - omci_2.png"/>

<img src="images/06 - omci_3.png"/>

<img src="images/06 - omci_4.png"/>

## **GPON Network Protection**

<img src="images/06 - typb-s.png"/>

- Vantagens: A rede é simples, o gerenciamento OLT/ONU é simples e o provisionamento de serviços é simples.

- Desvantagem: Os serviços são interrompidos se a OLT estiver com defeito. Geralmente, as fibras ópticas são roteadas no mesmo tubo. Portanto, duas fibras ópticas podem ser desconectadas ao mesmo tempo.

- Cenário de aplicação: Este esquema de proteção é usado para proteger serviços importantes, como serviços de acesso a linhas privadas empresariais e serviços de acesso a linhas privadas de estações base.

<img src="images/06 - typb-d.png"/>

- Vantagem: Duas fibras ópticas de backbone são conectadas a dois OLTs para implementar recuperação remota de desastres.

-  Desvantagem: A rede é complexa, o custo é alto e a configuração da OLT é complexa.

- Cenário de aplicação: Esta solução é utilizada para proteger serviços importantes do usuário, especialmente aqueles que exigem recuperação remota de desastres. Ele pode ser usado para proteger serviços de acesso a linhas privadas empresariais e serviços de acesso a linhas privadas de estações base.

<img src="images/06 - typc-s.png"/>

- Vantagem: A rede é simples e o gerenciamento OLT/ONU é simples.

- Desvantagem: Os serviços são interrompidos se a OLT estiver com defeito. Geralmente, as fibras ópticas são roteadas no mesmo tubo. Portanto, duas fibras ópticas podem ser desconectadas ao mesmo tempo.

- Cenário de aplicação: Serviços importantes de usuários são protegidos, incluindo serviços de acesso a linhas privadas empresariais e serviços de acesso a linhas privadas de estação base

<img src="images/06 - typc-d.png"/>

No cenário de rede dual-homing, as duas linhas PON entre a ONU e os dois OLTs estão no estado ativo/standby e não podem encaminhar pacotes ao mesmo tempo. 

- Vantagem: Quando a OLT ou o link upstream da OLT está com defeito, os serviços podem ser comutados para a outra OLT.

- Desvantagens: redes complexas, alto custo e gerenciamento complexo de ONUs.

- Cenário de aplicação: Este modo é usado principalmente para proteção de energia e também pode ser usado para proteger serviços de acesso a linhas privadas empresariais e serviços de acesso a linhas privadas de estações base.
