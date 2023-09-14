# **Visão Geral da VLAN**

Virtual Local Area Network (VLAN) divide logicamente os recursos e usuários da rede em pequenas redes lógicas. As funções e operações da VLAN são similares aos da tradicional LAN e ela fornece interconexão entre terminais com um certo intervalo. As vantagens do seu uso são:

- Isola os domínios de broadcast e suprime seus pacotes
- Reduz os custos de mudança e movimento
- Cria grupos virtuais de trabalho para atuarem de maneiras diferentes e seus usuários não estão restritos a dispositivos físicos.
- Melhora a segurança da comunicação e a robustez da rede

## **Gerenciamento de Tag na VLAN**

Para controlar o encaminhamento. o switch adiciona a VLAN Tag ao quadro Ethernet antes de encaminhar para que o pacote de dados, ao chegar no switch de destino, seja encaminhado para a porta certa.

## **O método de divisão da VLAN**

As VLANs podem ser divididas em:
- Portas do switch Ethernet
- Endereço MAC
- Protocolo
-  IP Subnets

Normalmente, as portas são utilizadas pois são fáceis de manter e configurar

# **Configuração e Implementação da VLAN**

Os dado na VLAN podem ser transferidos por meio de múltiplos switches. 

- _Acess-link:_ Conecta o usuário a VLAN
- _Trunk-link:_ Conecta um switch a outro. 

# Roteamento da VLAN

Uma desvantagem do uso de VLANs é que elas não podem se comunicar entre si, ou seja, elas isolam dois domínios de broadcast.

Para resolver o problema dos requisitos excessivos de interface física, um
roteador é introduzido no desenvolvimento de tecnologias VLAN. O roteador é um dispositivo de rede de Camada 3, que requer apenas uma interface Ethernet para implementar comunicação entre VLANs. Ao criar subinterfaces, esse dispositivo pode funcionar como gateway de todas as VLANs e encaminhar dados entre elas.

# Funcionalidades da VLAN na Rede de Acesso

A OLT (Optical Line Terminal) suporta em torno de 4000 VLANs, os tipos e atributos das VLANs são:

- **Tipo:** Standard, Smart, Mux e Super.
- **Atributos:** Common, QinQ e Stacking.


