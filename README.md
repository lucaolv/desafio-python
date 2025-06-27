# Desafio Node - API de Produtos

Este projeto é uma API simples para gerenciamento de produtos, desenvolvida em Python utilizando o framework Flask. O objetivo é demonstrar a estrutura de uma aplicação backend organizada em camadas (controllers, models, repositories) e como criar testes unitários para garantir a qualidade do código.

## Estrutura do Projeto

```
app/
  controllers/
    product_controller.py
  models/
    product.py
  repositories/
    product_repository.py
  routes.py
  __init__.py
run.py
requirements.txt
tests/
  test_product_controller_pytest.py
  test_product_model.py
  test_product_repository.py
```

## Camadas da Aplicação

### 1. Models

- **Arquivo:** `app/models/product.py`
- **Função:** Define a estrutura dos dados de um produto (campos como id, nome, descrição, preço, categoria, estoque, datas de criação e atualização).
- **Principais métodos:**
  - `to_dict()`: Converte o produto para um dicionário (útil para retornar em JSON).
  - `update()`: Atualiza os campos do produto.

### 2. Repositories

- **Arquivo:** `app/repositories/product_repository.py`
- **Função:** Responsável por armazenar, buscar, atualizar e remover produtos em memória (simulando um banco de dados).
- **Principais métodos:**
  - `create()`: Cria um novo produto.
  - `get_all()`: Retorna todos os produtos.
  - `get_by_id()`: Busca um produto pelo ID.
  - `get_by_category()`: Busca produtos por categoria.
  - `update()`: Atualiza um produto existente.
  - `delete()`: Remove um produto.
  - `search()`: Busca produtos pelo nome ou descrição.

### 3. Controllers

- **Arquivo:** `app/controllers/product_controller.py`
- **Função:** Define as regras de negócio e como responder às requisições HTTP (GET, POST, PUT, DELETE).
- **Principais métodos:**
  - `get_all_products()`: Lista todos os produtos, com filtros opcionais por categoria ou busca textual.
  - `get_product(product_id)`: Busca um produto pelo ID.
  - `create_product()`: Cria um novo produto a partir dos dados enviados na requisição.
  - `update_product(product_id)`: Atualiza um produto existente.
  - `delete_product(product_id)`: Remove um produto.

### 4. Rotas

- **Arquivo:** `app/routes.py`
- **Função:** Faz o mapeamento das URLs para os métodos do controller.

### 5. Inicialização da Aplicação

- **Arquivo:** `run.py`
- **Função:** Ponto de entrada da aplicação Flask.

## Testes Unitários

Os testes garantem que cada parte da aplicação funciona corretamente, mesmo após alterações no código.

- **Controllers:** Testes para cada endpoint, simulando requisições HTTP e verificando as respostas.
- **Models:** Testes para os métodos da model `Product`, como conversão para dicionário e atualização de campos.
- **Repositories:** Testes para todas as operações do repositório, como criar, buscar, atualizar, remover e buscar produtos.

Os testes estão na pasta `tests/` e utilizam o framework PyTest.

### Como rodar os testes

1. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   pip install pytest
   ```
2. Execute os testes:
   ```bash
   pytest tests/
   ```

Se aparecer erro de importação do módulo `app`, defina a variável de ambiente `PYTHONPATH` para a raiz do projeto:

No bash:

```bash
export PYTHONPATH=.
pytest tests/
```

No Windows (cmd):

```cmd
set PYTHONPATH=.
pytest tests/
```

## Como executar a aplicação

1. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```
2. Execute o servidor Flask:
   ```bash
   python run.py
   ```
3. Acesse os endpoints usando ferramentas como Postman, Insomnia ou seu navegador.

## Endpoints disponíveis

- `GET /products` — Lista todos os produtos (pode filtrar por categoria ou busca textual)
- `GET /products/<id>` — Busca um produto pelo ID
- `POST /products` — Cria um novo produto
- `PUT /products/<id>` — Atualiza um produto existente
- `DELETE /products/<id>` — Remove um produto

## Observações

- O repositório de produtos é em memória, ou seja, os dados são perdidos ao reiniciar a aplicação.
- O projeto é ideal para quem está começando a aprender sobre APIs, Flask e testes em Python.

---

Se tiver dúvidas ou quiser expandir a aplicação, fique à vontade para explorar e modificar o código!
