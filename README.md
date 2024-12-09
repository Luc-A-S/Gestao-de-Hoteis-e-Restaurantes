# Gestão de Hotéis e Restaurantes

Um projeto para facilitar a administração do dia a dia de hotéis e restaurantes. A ideia é ter tudo em um só lugar, ficando mais fácil organizar as coisas, economizando tempo e garantindo uma experiência incrível para os clientes!

## Objetivo do Banco de Dados

_Fornecer uma estrutura para o gerenciamento das operações diárias de um hotel. Ele permite que as informações sobre os clientes, reservas, quartos, pedidos e itens consumidos sejam armazenadas de forma eficiente e facilmente acessível para os gestores do hotel._

## Estrutura

#### 1. USR_GESTAO_HOTEL_CLIENTES

> Armazena os dados dos clientes do hotel.

• **[CLIENTE_ID]:** Identificador único do cliente _(Chave Primária)_.

• **[NOME]:** Nome do cliente.

• **[EMAIL]:** Endereço de e-mail do cliente.

• **[TELEFONE]:** Número de telefone do cliente.


#### 2. USR_GESTAO_HOTEL_QUARTOS

> Armazena as informações sobre os quartos do hotel.

• **[QUARTO_ID]:** Identificador único do quarto _(Chave Primária)_.

• **[NUMERO]:** Número do quarto.

• **[TIPO]:** Tipo do quarto _(Ex: Simples, Duplo, etc.)_.

• **[PRECO_DIARIA]:** Preço da diária do quarto.


#### 3. USR_GESTAO_HOTEL_RESERVAS

> Registra as reservas feitas pelos clientes para os quartos do hotel.

• **[RESERVA_ID]:** Identificador único da reserva _(Chave Primária)_.

• **[CLIENTE_ID]:** Identificador do cliente _(Chave Estrangeira de [USR_GESTAO_HOTEL_CLIENTES])_.

• **[QUARTO_ID]:** Identificador do quarto reservado _(Chave Estrangeira de [USR_GESTAO_HOTEL_QUARTOS])_.

• **[DATA_CHECKIN]:** Data de entrada do cliente.

• **[DATA_CHECKOUT]:** Data de saída do cliente.

• **[STATUS]:** Status da reserva _(Ex: Confirmada, Cancelada)_.


#### 4. USR_GESTAO_HOTEL_PEDIDOS

> Registra os pedidos feitos pelos clientes durante a estadia no hotel.

• **[PEDIDO_ID]:** Identificador único do pedido _(Chave Primária)_.

• **[CLIENTE_ID]:** Identificador do cliente que fez o pedido _(Chave Estrangeira de USR_GESTAO_HOTEL_CLIENTES)_.

• **[DATA_PEDIDO]:** Data e hora em que o pedido foi feito.

• **[TOTAL]:** Valor total do pedido.

• **[STATUS]:** Status do pedido _(Ex: Pago, Pendente)_.
