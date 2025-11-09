📘 Projeto de E-commerce – Modelo Conceitual

Este repositório faz parte da Formação SQL Specialist, da Digital Innovation One (DIO).
O objetivo deste desafio foi criar e refinar o modelo conceitual de um sistema de e-commerce, aplicando os conceitos de Entidades, Relacionamentos e Regras de Negócio estudados ao longo da formação.

🎯 Objetivo do Desafio

O desafio propôs o refinamento do modelo apresentado em aula, adicionando três novos pontos de complexidade:

◾ Cliente PJ e PF – o sistema deve permitir o cadastro de clientes pessoa física e pessoa jurídica, mas uma mesma conta não pode possuir as duas informações.
◾ Pagamento – o cliente pode cadastrar mais de uma forma de pagamento e um pedido pode ter mais de um pagamento.
◾ Entrega – deve possuir código de rastreio e status, representando o acompanhamento do envio do pedido.

🏗️ Descrição do Projeto

O modelo foi desenvolvido no MySQL Workbench e representa o fluxo principal de um e-commerce single-vendor, ou seja, todos os produtos são vendidos pela própria plataforma.

As principais entidades do modelo são:

👤 Cliente

Representa o comprador.
Foi utilizada a técnica de especialização total e disjunta, criando as subclasses Pessoa Física e Pessoa Jurídica.
Assim, cada cliente é obrigatoriamente PF ou PJ, e nunca ambos ao mesmo tempo.

Subentidades:

Pessoa Física: armazena CPF.

Pessoa Jurídica: armazena CNPJ e Razão Social.

🏭 Fornecedor

Responsável pelo fornecimento dos produtos cadastrados na loja.

📦 Produto

Itens comercializados no e-commerce.
Cada produto pertence a um fornecedor e está vinculado ao estoque.

🏬 Estoque

Armazena a relação entre o produto e a quantidade disponível.
A entidade intermediária Produto_has_Estoque foi criada para representar a quantidade, já que ela depende tanto do produto quanto do local do estoque.

🧾 Pedido

Registra as informações principais de uma compra realizada por um cliente.
Inclui dados como descrição, status e valor do frete.

💳 Pagamento

Relaciona-se diretamente ao pedido.
Um pedido pode possuir um ou mais pagamentos, e cada pagamento pertence a apenas um pedido.
Essa estrutura permite representar diferentes formas de pagamento (como cartão de crédito ou PIX) para a mesma compra.

🚚 Entrega

Contém informações sobre o envio do pedido ao cliente.
Inclui tipo de frete, valor, código de rastreio, datas de envio e entrega, além do status da entrega.
Relaciona-se com Transportadora, responsável por realizar o envio.

🚛 Transportadora

Entidade que representa as empresas responsáveis pela entrega.
Uma transportadora pode realizar várias entregas.

🔗 Principais Relacionamentos

Cliente 1..N Pedido

Pedido 1..N Pagamento

Pedido 1..1 Entrega

Transportadora 1..N Entrega

Fornecedor 1..N Produto

Produto 1..N ItemPedido

Pedido 1..N ItemPedido

Produto N..N Estoque (via Produto_has_Estoque)

Cliente (superclasse) 1..1 Pessoa Física ou Pessoa Jurídica

📋 Regras de Negócio Representadas

Cada cliente é classificado como PF ou PJ (especialização total e disjunta).

Um pedido deve ter ao menos um item.

Um pedido pode ter mais de um pagamento, mas cada pagamento pertence a um único pedido.

Cada pedido possui uma entrega, associada a uma transportadora.

A quantidade de produtos é controlada na relação Produto_has_Estoque.

📂 Entrega do Projeto

Diagrama conceitual exportado em formato .png: e-commerce-refinado.png

Este README com a explicação do projeto e das decisões de modelagem

💡 Resumo Final

O projeto representa o modelo conceitual de um e-commerce, elaborado como parte da Formação SQL Specialist (DIO).
O modelo foi refinado para contemplar clientes PF/PJ, múltiplas formas de pagamento e controle de entrega com rastreio, aplicando de forma prática os conceitos de modelagem de dados e projeto de banco de dados relacional.
