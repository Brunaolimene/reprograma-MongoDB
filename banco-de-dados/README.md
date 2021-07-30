Reprograma | Back And | Banco de dados 
 
<h1 align="center">
    <br>
    <p align="center">Banco de dados - consultas<p>
</h1>




Na atividade da semana, foi solicidado que fosse criado um novo banco de dados e uma coleção com um nome pertinente, de acordo com os dados e tema escolhido. Em seguida devem ser feitos os comandos abaixo:

* Inserção de documentos
* Atualização de documentos
* Exclusão de documentos
* Consulta com projeção
* Consulta utilizando combinação entre os seletores
* Consulta paginada e ordenada (utilizar skip, limit e sort)

Após a conclusão dessa consulta, tudo deve ser descrito no arquivo README.md

---
### **Abaixo será descrito o passo a passo para a consulta no mongo e Robo 3T.** 

---

1. Subir o servidor, colocando o caminho no Prompt de Comando. 
```
C:\Program Files\MongoDB\Server\5.0\bin
```
2. Entrar na pasta bin pelo terminal e dar o mongod. 

3. Acessar o Robo 3T e criar um dataBase.
```
Foi criado um dataBase chamado "biblioteca"
```
4. criar um json e inserir novo documento no Robo 3T (primeiro item do exercicio).
```
db.livros.insertMany([
    {

        "nome": 'Marley e eu' ,
        "categoria": 'cuidado com animais' ,
        "paginas": 288 ,
        "autor": 'John Grogan'
        
    },
    { 
        "nome": 'O diario de Anne Frank' ,
        "categoria": 'Biografias e Casos verdadeiros' ,
        "paginas": 224 ,
        "autor": 'Anne Frank'

    },
    { 
        "nome": 'Revolucao dos bichos' ,
        "categoria": 'Ficcao' ,
        "paginas": 336 ,
        "autor":  'George Orwell'

    },
    { 
        "nome": 'Pai rico pai pobre' ,
        "categoria": 'Financas e investimentos' ,
        "paginas": 336 ,
        "autor": ' Robert Kiyosaki, Sharon L. Lechter'

    },
    { 
        "nome": 'O homem mais rico da Babilonia' ,
        "categoria": 'Autoajuda' ,
        "paginas": 160 ,
       "autor": ' George Samuel Clason'
    }
])
```
5. Rodar o comando abaixo para o Robo 3T listar o documento criado: 
```
db.getCollection('livros').find({})
```
6. Para atualizar o documento: 
```
db.getCollection('livros').update(
    {
        "nome": "Marley e eu"
    },
    
    {
        $set:{"paginas" : "289"}
    }
  )
```
7. Para excluir documentos:
```
db.livros.remove({"paginas": "160"})
```
8. Consultar com projeção: 

**Para consultar do livro com maior número de páginas para  o menor número de páginas** 
```
db.getCollection("livros").find().sort({"paginas": -1})
```
**Para consultar do livro com menor número de páginas para  o maior número de páginas**
```
db.getCollection("livros").find().sort({"paginas": 1})
```
8. Consulta utilizando combinação entre os seletores:
 ```
db.getCollection("livros").find({"categoria":"Autoajuda","paginas":"160"})
```
9.Consulta paginada e ordenada: 
```
db.getCollection("livros").find({"categoria": "Autoajuda"}).limit(2)
```





