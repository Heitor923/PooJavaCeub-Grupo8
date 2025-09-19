# Loja de Musica - Java

```mermaid
classDiagram
    class Produto {
        <<abstract>>
        - int codigo
        - String nome
        - double preco
        - Categoria categoria
        + Produto(int codigo, String nome, double preco, Categoria categoria)
        + getCodigo() int
        + getNome() String
        + getPreco() double
        + getCategoria() Categoria
        + setPreco(double preco) void
        + exibirDetalhes() void
    }

    class Instrumento {
        - String tipo
        - String marca
        + Instrumento(int codigo, String nome, double preco, Categoria categoria, String tipo, String marca)
        + getTipo() String
        + getMarca() String
        + exibirDetalhes() void
    }

    class Acessorio {
        - String material
        + Acessorio(int codigo, String nome, double preco, Categoria categoria, String material)
        + getMaterial() String
        + exibirDetalhes() void
    }

    class Funcionario {
        - int id
        - String nome
        + Funcionario(int id, String nome)
        + cadastrarProduto(Produto p) void
        + consultarProduto(int codigo) Produto
        + gerarVenda() Venda
        + consultarVenda(int id) Venda
    }

    class Venda {
        - int id
        - Date data
        - List~ItemVenda~ itens
        - double valorTotal
        + Venda(int id, Date data)
        + adicionarProduto(Produto p, int qtd) void
        + calcularTotal() double
        + getValorTotal() double
    }

    class ItemVenda {
        - Produto produto
        - int quantidade
        - double subtotal
        + ItemVenda(Produto produto, int quantidade)
        + calcularSubtotal() double
        + getProduto() Produto
        + getQuantidade() int
    }

    class Categoria {
        <<enumeration>>
        CORDAS
        PERCUSSAO
        SOPRO
        ELETRONICO
        ACESSORIOS
    }

    Produto <|-- Instrumento
    Produto <|-- Acessorio
    Venda "1" *-- "many" ItemVenda
    ItemVenda "1" --> "1" Produto
    Funcionario "1" --> "*" Venda
    Produto --> Categoria





