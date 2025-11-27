**Modelo Conceitual** (.brM3)\
**Modelo Lógico** (.txt)\
**Modelo Físico** (.sql) 

Descrição:
=
Este banco de dados organiza informações sobre motoristas, estacionamentos, vagas e a relação entre eles por meio da tabela Gerencia. O objetivo é permitir o controle de quais motoristas gerenciam quais vagas dentro de cada estacionamento.

Estrutura das Tabelas:
=

**Motorista**
Contém os dados básicos dos motoristas.
Atributos: Id_motorista (PK), Nome, Telefone.

**Estacionamento**
Armazena informações dos estacionamentos cadastrados.
Atributos: Id_estacionamento (PK), Nome, Endereco.

**Vaga**
Representa as vagas disponíveis dentro de um estacionamento.
Atributos: Id_vaga (PK), Numero, Estado, Id_estacionamento (FK).
Relacionamento: Um estacionamento pode ter várias vagas (1:N).

**Gerencia**
Tabela associativa que relaciona motoristas, estacionamentos e vagas.
Atributos: Id_motorista (FK), Id_estacionamento (FK), Id_vaga (FK).
Chave primária composta por (Id_motorista, Id_estacionamento, Id_vaga).
Relacionamento: Representa uma relação N:N entre Motorista e Vaga, considerando o contexto do Estacionamento.

Script SQL:
=
```
CREATE TABLE Motorista (
Id_motorista INT PRIMARY KEY,
Nome VARCHAR(100) NOT NULL,
Telefone VARCHAR(15)
);

CREATE TABLE Estacionamento (
Id_estacionamento INT PRIMARY KEY,
Nome VARCHAR(100) NOT NULL,
Endereco VARCHAR(255)
);

CREATE TABLE Vaga (
Id_vaga INT PRIMARY KEY,
Numero VARCHAR(10) NOT NULL,
Estado VARCHAR(50),
Id_estacionamento INT NOT NULL,
FOREIGN KEY (Id_estacionamento) REFERENCES Estacionamento(Id_estacionamento)
);

CREATE TABLE Gerencia (
Id_motorista INT NOT NULL,
Id_estacionamento INT NOT NULL,
Id_vaga INT NOT NULL,
PRIMARY KEY (Id_motorista, Id_estacionamento, Id_vaga),
FOREIGN KEY (Id_motorista) REFERENCES Motorista(Id_motorista),
FOREIGN KEY (Id_estacionamento) REFERENCES Estacionamento(Id_estacionamento),
FOREIGN KEY (Id_vaga) REFERENCES Vaga(Id_vaga)
);
```

## Grupo: Felipe Siller, Lucas Oliveira, Iago Colt
