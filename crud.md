/* Para implementar as quatro operações de CRUD (Create, Read, Update, Delete) para um recurso de livros em uma livraria, podemos utilizar as seguintes rotas:

Criar um livro (Create):
Rota: POST /livros
Corpo da requisição: */

{
   "nome": "O Pequeno Príncipe",
   "autor": "Antoine de Saint-Exupéry",
   "ISBN": "978-3-16-148410-0"
}
/* 
Resposta da requisição(em caso de sucesso): */

{
   "id": 1,
   "nome": "O Pequeno Príncipe",
   "autor": "Antoine de Saint-Exupéry",
   "ISBN": "978-3-16-148410-0"
}

/* Ler um livro (Read):
Rota: GET /livros/{id}
Parâmetro de URL: id (identificador do livro)
Resposta da requisição(em caso de sucesso): */

{
   "id": 1,
   "nome": "O Pequeno Príncipe",
   "autor": "Antoine de Saint-Exupéry",
   "ISBN": "978-3-16-148410-0"
}
/* Atualizar um livro (Update):
Rota: PUT /livros/{id}
Parâmetro de URL: id (identificador do livro)
Corpo da requisição: */

{
   "nome": "O Pequeno Príncipe",
   "autor": "Antoine de Saint-Exupéry",
   "ISBN": "978-3-16-148410-0"
}
/* Resposta da requisição(em caso de sucesso): */

{
   "id": 1,
   "nome": "O Pequeno Príncipe",
   "autor": "Antoine de Saint-Exupéry",
   "ISBN": "978-3-16-148410-0"
}
/* Deletar um livro (Delete):
Rota: DELETE /livros/{id}
Parâmetro de URL: id (identificador do livro)
Resposta da requisição(em caso de sucesso): */

{
   "message": "Livro removido com sucesso."
}

/* 
Essas rotas permitem a interação com o recurso de livros em uma livraria, permitindo a criação, leitura, atualização e remoção de livros do estoque. É importante lembrar que essas rotas são apenas um exemplo e que as rotas e estrutura do sistema podem variar dependendo das necessidades da aplicação. */