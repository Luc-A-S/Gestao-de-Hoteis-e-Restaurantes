# Gestão de Hotéis e Restaurantes

Um projeto para facilitar a administração do dia a dia de hotéis e restaurantes. A ideia é ter tudo em um só lugar, ficando mais fácil organizar as coisas, economizando tempo e garantindo uma experiência incrível para os clientes!

## Objetivo do Banco de Dados

_Fornecer uma estrutura para o gerenciamento das operações diárias de um hotel. Ele permite que as informações sobre os clientes, reservas, quartos, pedidos e itens consumidos sejam armazenadas de forma eficiente e facilmente acessível para os gestores do hotel._

## Estrutura

### 1. USR_GESTAO_HOTEL_CLIENTES

> Armazena os dados dos clientes do hotel.

• **[CLIENTE_ID]:** Identificador único do cliente _(Chave Primária)_.

• **[NOME]:** Nome do cliente.

• **[EMAIL]:** Endereço de e-mail do cliente.

• **[TELEFONE]:** Número de telefone do cliente.

_

### 2. USR_GESTAO_HOTEL_QUARTOS

> Armazena as informações sobre os quartos do hotel.

• **[QUARTO_ID]:** Identificador único do quarto _(Chave Primária)_.

• **[NUMERO]:** Número do quarto.

• **[TIPO]:** Tipo do quarto _(Ex: Simples, Duplo, etc.)_.

• **[PRECO_DIARIA]:** Preço da diária do quarto.

_

### 3. USR_GESTAO_HOTEL_RESERVAS

> Registra as reservas feitas pelos clientes para os quartos do hotel.

• **[RESERVA_ID]:** Identificador único da reserva _(Chave Primária)_.

• **[CLIENTE_ID]:** Identificador do cliente _(Chave Estrangeira de [USR_GESTAO_HOTEL_CLIENTES])_.

• **[QUARTO_ID]:** Identificador do quarto reservado _(Chave Estrangeira de [USR_GESTAO_HOTEL_QUARTOS])_.

• **[DATA_CHECKIN]:** Data de entrada do cliente.

• **[DATA_CHECKOUT]:** Data de saída do cliente.

• **[STATUS]:** Status da reserva _(Ex: Confirmada, Cancelada)_.

_

### 4. USR_GESTAO_HOTEL_PEDIDOS

> Registra os pedidos feitos pelos clientes durante a estadia no hotel.

• **[PEDIDO_ID]:** Identificador único do pedido _(Chave Primária)_.

• **[CLIENTE_ID]:** Identificador do cliente que fez o pedido _(Chave Estrangeira de USR_GESTAO_HOTEL_CLIENTES)_.

• **[DATA_PEDIDO]:** Data e hora em que o pedido foi feito.

• **[TOTAL]:** Valor total do pedido.

• **[STATUS]:** Status do pedido _(Ex: Pago, Pendente)_.

_

### 5. USR_GESTAO_HOTEL_ITENS_PEDIDO

> Armazena os itens consumidos pelos clientes dentro de cada pedido.

• **[ITEM_PEDIDO_ID]:** Identificador único do item do pedido _(Chave Primária)_.

• **[PEDIDO_ID]:** Identificador do pedido _(Chave Estrangeira de USR_GESTAO_HOTEL_PEDIDOS)_.

• **[NOME_ITEM]:** Nome do item _(Ex: Refrigerante, Pizza, etc.)_.

• **[QUANTIDADE]:** Quantidade do item pedido.

• **[PRECO_UNITARIO]:** Preço unitário do item.

## Relacionamentos entre as Tabelas

• _A tabela **USR_GESTAO_HOTEL_RESERVAS** faz referência à tabela **USR_GESTAO_HOTEL_CLIENTES** através da chave estrangeira **[CLIENTE_ID]**, associando cada reserva a um cliente._

• _A tabela **USR_GESTAO_HOTEL_RESERVAS** também faz referência à tabela **USR_GESTAO_HOTEL_QUARTOS** através da chave estrangeira **[QUARTO_ID]**, associando a reserva a um quarto específico._

• _A tabela **USR_GESTAO_HOTEL_PEDIDOS** faz referência à tabela **USR_GESTAO_HOTEL_CLIENTES** através da chave estrangeira **[CLIENTE_ID]**, associando cada pedido a um cliente._

• _A tabela **USR_GESTAO_HOTEL_ITENS_PEDIDO** faz referência à tabela **USR_GESTAO_HOTEL_PEDIDOS** através da chave estrangeira **[PEDIDO_ID]**, associando cada item a um pedido específico._

## Diagrama

### 1. USR_GESTAO_HOTEL_RESERVAS

• **[CLIENTE_ID]** -> **USR_GESTAO_HOTEL_CLIENTES**

• **[QUARTO_ID]** -> **USR_GESTAO_HOTEL_QUARTOS**

_

### 2. USR_GESTAO_HOTEL_PEDIDOS

• **[CLIENTE_ID]** -> **USR_GESTAO_HOTEL_CLIENTES**

_

### 3. USR_GESTAO_HOTEL_ITENS_PEDIDO

• **[PEDIDO_ID]** -> **USR_GESTAO_HOTEL_PEDIDOS**

## Como Executar os Scripts no Oracle

### 1. Usando o SQL*Plus

> O **SQL*Plus** é uma ferramenta de linha de comando para executar comandos SQL no Oracle.

1 - Abra o **SQL*Plus**.

2 - Conecte-se ao banco de dados Oracle com o comando:

**[CONNECT usuario/senha@banco]**

3 - Execute os scripts de criação e inserção de dados:

**[@caminho_do_script/criar_tabelas.sql]**

**[@caminho_do_script/inserir_dados.sql]**

4 - Verifique se as tabelas foram criadas corretamente com o comando:

**[SELECT * FROM USR_GESTAO_HOTEL_CLIENTES;]**

_

### 2. Usando o SQL Developer

> O **SQL Developer** é uma interface gráfica para trabalhar com bancos de dados Oracle.

1 - Abra o **SQL Developer** e conecte-se ao banco de dados Oracle.

2 - Crie uma nova conexão com as credenciais de acesso ao banco.

3 - No painel de navegação, clique com o botão direito na conexão e selecione **Open SQL Worksheet**.

4 - No editor de SQL, copie e cole o conteúdo dos scripts _(de criação e inserção de dados)_ e clique em **Run** _(ícone de "play")_.

_

### 3. Executando os Scripts

• Para criar as tabelas, execute o script de criação.

• Para inserir dados, execute o script de inserção.

• Verifique a integridade das tabelas e dados utilizando comandos **[SELECT]** para visualizar os registros.
