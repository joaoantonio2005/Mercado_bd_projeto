# Mercado_bd_projeto

CREATE DATABASE mercado
CHARACTER SET utf8mb4

COLLATE utf8mb4_unicode_ci;
use mercado; 

CREATE TABLE Estoque(
id_estoque INT AUTO_INCREMENT PRIMARY KEY,
    nome_produto VARCHAR(100) NOT NULL,
    quantidade INT NOT NULL,
    preco DECIMAL(10, 2) NOT NULL,
    data_entrada DATE NOT NULL,
    descricao_produto TEXT
);

 -- CRIANDO a tabela de clientes
CREATE TABLE Clientes(
	id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nome_cliente VARCHAR(100) NOT NULL,
    telefone VARCHAR(15),
    email VARCHAR(100),
    data_registro DATE NOT NULL,
    endereco VARCHAR(100)
);


create table Funcionarios (
id_funcionario int auto_increment primary key,
nome_funcionario varchar(100) not null,
telefone varchar(15),
email varchar(100),
cargo varchar(50),
salario decimal(10,2),
data_contratacao date not null
);

create table Servicos (
id_servico int auto_increment primary key,
nome_servico varchar(100) not null,
descricao_servico text,
preco_servico decimal(10,2) not null,
duracao_estimada time
);

CREATE TABLE Vendas(
id_venda INT AUTo_INCREMENT PRIMARY KEY, -- Chave primária
    data_venda DATE NOT NULL,
    total DECIMAL(10,2) NOT NULL,
    id_cliente INT NOT NULL,
id_funcionario INT NOT NULL
);

CREATE TABLE Itens_Venda(
id_item_venda INT AUTO_INCREMENT PRIMARY KEY,
    id_venda INT,
    id_estoque INT,
quantidade_vendida INT NOT NULL,
    preco_unitario DECIMAL(10,2) NOT NULL,
    CONSTRAINT fk_itens_venda_venda FOREIGN KEY (id_venda) REFERENCES Vendas(id_venda),
    CONSTRAINT fk_itens_venda_estoque FOREIGN KEY (id_estoque) REFERENCES Estoque(id_estoque)
);







INSERT INTO Estoque (nome_produto, quantidade, preco, data_entrada, descricao_produto) values
('Ração para cães','100','50.00','2024-01-10','Ração Premium para cães adultos'),
('Ração para Gatos','80','45.00','24-01-12','Ração Nutritiva para gatos'),
('Brinquedo para Cães','150','25.00','2024-01-15','Brinquedo interativo para cães'),
('Brinquedos para Gatos','120','20.00','2024-01-18','Brinquedo interativo para gatos'),
('Shampoo para Pets','200','30.00','2024-01-20','Shampoo hipoalergênico para pets'),
('Coleira para Cães','75','15.00','2024-01-22','Coleira ajustável para cães grandes'),
('Coleira para Gatos','50','10.00','2024-01-25','Coleira com guizo para gatos'),
('Arroz','60','55.00','2024-01-27','Arroz São João'),
('Feijão','90','35.00','2024-01-30','Feijão da vovó'),
('Shampoo','40','75.00','2024-02-02','Shampoo Seda'),
('Condicionador','35','80.00','2024-02-05','Condicionador Seda'),
('Mascara de cabelo','25','65.00','2024-02-07','Mascara Seda'),
('Escova de cabelo','15','120.00','2024-02-10','Escova de cabelo normal'),
('Cuscuz','50','22.00','2024-02-12','Cuscuz Flocão'),
('feijão','40','18.00','2024-02-15','feijão do Sitio'),
('Tomate','20','150.00','2024-02-18','tomate kilo'),
('Batata','30','100.00','2024-02-20','batata kilo'),
('Miojo','10','810.00','2024-02-22','miojo galinha caipira'),
('Leite condensado','25','70.00','2024-02-27','Leite moca'),
('Leite desnatado','15','75.00','2024-02-27','leite piracanjuba'),
('Sabonete','5','300.00','2024-02-28','Sabonete Dove');

INSERT INTO Funcionarios (nome_funcionario, telefone, email, cargo, salario, data_contratacao) VALUES
('Castanhari', '11900000001', 'lucas@gmail.com', 'Atendente', 2000.00, '2024-01-01'),
('Julio Cocielo', '11900000002', 'fernanda@gmail.com', 'Gerente', 3000.00, '2024-01-02'),
('Felipe Neto', '11900000003', 'juliano@gmail.com', 'repositor', 4000.00, '2024-01-03'),
('Mitico', '11900000004', 'tatiane@gmail.com', 'Recepcionista', 1800.00, '2024-01-04'),
('Lusquinha', '11900000005', 'marcelo@gmail.com', 'repositor', 2200.00, '2024-01-05'),
('Gabriel pereira', '11900000006', 'carla@gmail.com', 'caixa de mercado', 2500.00, '2024-01-06'),
('Chaves', '11900000007', 'bruno@gmail.com', 'Atendente', 2000.00, '2024-01-07'),
('Paty', '11900000008', 'patricia@gmail.com', 'atendente', 4000.00, '2024-01-08'),
('Lucas', '11900000009', 'andre@gmail.com', 'Recepcionista', 1800.00, '2024-01-09'),
('Igao', '11900000010', 'claudia@gmail.com', 'Gerente', 3000.00, '2024-01-10'),
('Lucas Vasquez', '11900000011', 'leonardo@gmail.com', 'repositor', 2200.00, '2024-01-11'),
('Goleiro Bruno', '11900000012', 'bruna@gmail.com', 'Atendente', 2000.00, '2024-01-12'),
('Lionel penis', '11900000013', 'gustavo@gmail.com', 'caixa do mercado', 2500.00, '2024-01-13'),
('Cristiano Tarado', '11900000014', 'eduardo@gmail.com', 'Veterinário', 4000.00, '2024-01-14'),
('Platao', '11900000015', 'renata@gmail.com', 'Recepcionista', 1800.00, '2024-01-15');


INSERT INTO Servicos (nome_servico, descricao_servico, preco_servico, duracao_estimada) VALUES
('Caixa', 'Trabalha no caixa', 50.00, '00:45:00'),
('Acogue', 'trablha na funcao no corte de carnes', 80.00, '01:15:00'),
('Padaria', 'Trabalha com as massas', 120.00, '01:30:00'),
('Repositor', 'Repositor de das mercadorias', 60.00, '00:30:00'),
('Gerente', 'Trabalha gerenciando o Mercado', 70.00, '00:20:00');


INSERT INTO Clientes (nome_cliente, telefone, email, endereco, data_registro) VALUES 
('João da Silva', '1234-5678', 'joao@example.com', 'Rua das Flores, 123', '2024-10-25'),
('Maria Oliveira', '9876-5432', 'maria@example.com', 'Avenida Central, 456', '2024-10-25'),
('Pedro Santos', '2345-6789', 'pedro@example.com', 'Travessa da Luz, 789', '2024-10-25'),
('Ana Paula', '3456-7890', 'ana@example.com', 'Rua do Sol, 101', '2024-10-25'),
('Carlos Eduardo', '4567-8901', 'carlos@example.com', 'Praça da Alegria, 202', '2024-10-25'),
('Fernanda Lima', '5678-9012', 'fernanda@example.com', 'Rua das Acácias, 303', '2024-10-25'),
('Ricardo Gomes', '6789-0123', 'ricardo@example.com', 'Avenida Brasil, 404', '2024-10-25'),
('Luciana Martins', '7890-1234', 'luciana@example.com', 'Rua do Comércio, 505', '2024-10-25'),
('Bruno Costa', '8901-2345', 'bruno@example.com', 'Largo da Paz, 606', '2024-10-25'),
('Juliana Mendes', '9012-3456', 'juliana@example.com', 'Estrada do Mar, 707', '2024-10-25'),
('André Almeida', '0123-4567', 'andre@example.com', 'Rua dos Lírios, 808', '2024-10-25'),
('Tatiane Rocha', '1234-5670', 'tatiane@example.com', 'Avenida dos Jacarandás, 909', '2024-10-25'),
('Felipe Nascimento', '2345-6781', 'felipe@example.com', 'Rua da Liberdade, 111', '2024-10-25'),
('Mariana Ribeiro', '3456-7892', 'mariana@example.com', 'Travessa do Rio, 222', '2024-10-25'),
('Vinícius Ferreira', '4567-8903', 'vinicius@example.com', 'Avenida da Vitória, 333', '2024-10-25');

   
INSERT INTO Vendas (data_venda, total, id_cliente, id_funcionario) VALUES
(2024-03-25, 200.00, 6, 6);


select * from itens_venda;

CREATE TABLE Itens_Venda(
id_item_venda INT AUTO_INCREMENT PRIMARY KEY,
    id_venda INT,
    id_estoque INT,
quantidade_vendida INT NOT NULL,
    preco_unitario DECIMAL(10,2) NOT NULL,
    CONSTRAINT fk_itens_venda_venda FOREIGN KEY (id_venda) REFERENCES Vendas(id_venda),
    CONSTRAINT fk_itens_venda_estoque FOREIGN KEY (id_estoque) REFERENCES Estoque(id_estoque)
);
