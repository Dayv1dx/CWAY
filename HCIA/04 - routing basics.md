# **Noções básicas de roteamento**

Roteamento é uma caminho de informação que pode orientar o encaminhamento do pacote IP. Roteadores fornecem um mecanismo para interconexão entre redes heterogêneas para transmitir pacotes de uma rede para outra, eles selecionam os caminhos apropriados baseado no _header_ do pacote e o envia para a próxima rota e finalmente o pacote e mandado para o _host_ de destino.

Dependendo se o destino está diretamente conectado ao roteador, pode ser dividido em: 

- Roteamento direto: A rede de destino está diretamente conectada ao roteador.

- Roteamento indireto:  A rede de destino não está diretamente conectada ao roteador.

## **Tabela de roteamento IP**

A chave de um roteador para encaminhar pacotes é a tabela de roteamento. Cada roteador possui um tabela de roteamento e as entradas de rota dentro dela indicarão qual porta física deve ser usado para enviar um pacote para a rede ou _host_, ou qual próximo roteador que pode alcançar o caminho. Pacotes com destino que não existe no tabela de roteamento será descartada. Os seguintes itens fazem parte da tabela:

- Destino: Identifica o endereço de destino ou rede de destino do IP
pacote.

- Máscara: Juntamente com o endereço de destino, identifica o endereço de um
segmento de rede onde o host ou roteador de destino está localizado.

- Interface: Indica qual interface será usada para encaminhar o pacote IP para fora do roteador.

- Next-Hop: Especifica o endereço da interface do próximo roteador que o IP pacote irá passar

### **Source of Routing**

O campo Protocolo na tabela de roteamento especifica a origem de uma rota, ou seja, como uma rota é gerada. Existem três tipos de rotas:

1. **Rotas descobertas por protocolos da camada de enlace (direto):** Custo pequeno, configuração simples, sem manutenção manual. Somente as rotas no segmento de rede ao qual a interface pertence pode ser descoberta. Essas rotas também são chamadas de rotas de interface ou rotas diretas.

2. **Roteamento estático de configuração manual (estático):** Sem custo, configuração simples, manutenção manual. Rotas estáticas são configurado manualmente pelos administradores. Rotas estáticas podem ser usadas para estabelecer uma rede interligada. No entanto, quando ocorre uma falha na rede, rotas estáticas não podem ser retificadas automaticamente e devem ser corrigidas manualmente configurado pelo administrador.

3. **Roteamento descoberto pelo protocolo de roteamento dinâmico (RIP, OSPF, etc.)**

Quando a topologia de rede é complexa, a configuração manual de rotas estática é demorado e sujeito a erros. Neste caso, os protocolos de roteamento dinâmicos podem ser usados ​​para descobrir e modificar rotas automaticamente sem manutenção manual. No entanto, os protocolos de roteamento dinâmico têm custos elevados e configurações complexas.

### **Longest Match Principle**

Se houverem muitas entradas de roteamento na rede de destino, o roteador irá priorizar a mascara de maior número.

### **Preferência de roteamento**

Um roteador pode aprender as rotas para a mesma rede de destino através de múltiplos protocolos (incluindo rotas estáticas). Quando essas rotas encontram a regra da correspondência mais longa (Longest Match Principle), o roteador deve determinar qual rota é preferida. Portanto, cada roteamento tem uma prioridade de protocolo. Quando existem múltiplas rotas, a rota descoberta pelo protocolo de roteamento com a prioridade mais alta torna-se a rota ideal e é adicionado à tabela de roteamento. Quanto menor o valor, maior a preferência.

## **Classificação das rotas**

Existem muitas maneiras de classificar rotas. Existem três fontes de roteamento, portanto, se classificarmos as rotas de acordo com a origem, elas podem ser divididas em:

- Rotas diretas: Custo pequeno, configuração simples, as rotas pertencem a interfaces locais.

- Rotas estáticas: Sem custo, configuração simples, manutenção manual. Quando ocorrem  mudanças de topologia, as rotas estáticas não mudarão. Apenas para topologias simples de rede.

- Rotas dinâmicas: Alto custo, configuração complexa, sem manutenção manual.
Pode ser aplicado a topologias de rede complexas. Quando a topologia muda,
rotas dinâmicas podem mudar.

### **Autonomous Systems (AS)**

É um grupo de roteadores que são gerenciados pela mesma organização e usam a mesma política de roteamento. Um AS pode ser um conjunto de roteadores que executam um único IGP (protocolo de gateway interno) ou um conjunto de roteadores que executam diferentes
protocolos de roteamento, mas pertencem à mesma organização. Em ambos os casos, o
o mundo exterior considera todo o AS como uma entidade.

### ** IGP e EGP**

De acordo com a área de trabalho, os protocolos de roteamento podem ser divididos em:

- IGP (_Interior Gateway Protocols_): RIP e IS-IS trocam informações de roteamento no mesmo AS. Tanto RIP quanto IS-IS são IGPs. O IGP é usado para descobrir e calcular informações de roteamento em um AS.

- EGP (_Exterior Gateway Protocols_): BGP é usado para conectar diferentes ASs e trocar informações de roteamento entre AS. Políticas de roteamento e filtragem de rotas são usadas para controlar o transmissão de informações de roteamento entre ASs.

## **Introdução as rotas estáticas**

Uma rota estática é uma rota especial configurada manualmente por uma rede
administrador. Rotas estáticas são fáceis de configurar e não precisam ocupar recursos da CPU para calcular e analisar rotas como fazem as rotas dinâmicas. A desvantagem das rotas estáticas é que elas não podem se adaptar às mudanças em uma rede automaticamente, portanto, as alterações na rede exigem reconfiguração manual.
Rotas estáticas são adequadas para redes com estruturas comparativamente simples. Não é
aconselhável configurar e manter rotas estáticas para uma rede com uma estrutura complexa. No entanto, as rotas estáticas reduzem o efeito da largura de banda e do consumo de recursos da CPU que ocorre quando outros protocolos são implementados.

## **Roteamento VLAN**


