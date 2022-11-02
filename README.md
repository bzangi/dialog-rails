### Setup
Ruby 2.7.5
Rails 6
No diretório em que for clonado o repositório, execute na linha de comando
- `bundle install`
- `rake db:create`
- `rake db:migrate`
- `rake db:seed`
DB: `library_development` 

### Endpoints
Para iniciar o projeto execute `rails server`
- Em `http://localhost:3000/` pode ser encontrada a lista de usuários paginada, ao final da lista o botão para criação de novos usuários;
- Em `http://localhost:3000/users/:id` é descrito um usuário com a opção de editar ou deletar ele
- Em `http://localhost:3000/users/:id/edit` é possível editar o usuário
- Em `http://localhost:3000/graphiql` é possível acessar a API 

- Query para listar todos os usuários 
``` graphql
 query{
   allUsers{
     id
     name
     age
     sex
     city
     uf
    }
  }
```

- Mutation para criar novo usuário
``` graphql
mutation{
  createUser(input:{
    name: "User",
    age: 25,
    sex: "Other",
    city: "São Paulo",
    uf: "SP"
  }){
    id,
    name,
    age
  }
}
```
- Mutation para deletar usuário
```graphql
mutation{
  destroyUser(input: {id:1}){
    id
  }
}
```
- Mutation para dar update em usuário
```graphql
mutation{
  updateUser(input:{
    id: 100
    name: "Novo nome"
  }){
    age
  }
}
```

> Essa mutation joga um erro após a execução do update (o update roda com sucesso, investiguei mas sem muito sucesso, decidi deixar ela pro crud não ficar incompleto, se descobrirem onde errei aceito sugestões)
