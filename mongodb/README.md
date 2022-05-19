# MongoDB

[Oque e mongoDB // Whats is mongoDB](https://www.mongodb.com/what-is-mongodb)

MongoDB é um banco de dados de documentos com a escalabilidade e flexibilidade que você deseja com a consulta e indexação que você precisa

Facilita o desenvolvimento

O modelo de documento do MongoDB é simples para os desenvolvedores aprenderem e usarem, enquanto ainda fornece todos os recursos necessários para atender aos requisitos mais complexos em qualquer escala. Fornecemos drivers para mais de 10 idiomas, e a comunidade construiu dezenas de outros.

MongoDB armazena dados em documentos flexíveis, semelhantes a JSON , o que significa que os campos podem variar de documento para documento e a estrutura de dados pode ser alterada ao longo do tempo

O modelo de documento é mapeado para os objetos no código do aplicativo , facilitando o trabalho com os dados

Consultas ad hoc, indexação e agregação em tempo real fornecem maneiras poderosas de acessar e analisar seus dados

O MongoDB é um banco de dados distribuído em sua essência , portanto, alta disponibilidade, dimensionamento horizontal e distribuição geográfica são integrados e fáceis de usar

O MongoDB é gratuito para usar . As versões lançadas antes de 16 de outubro de 2018 são publicadas sob a AGPL.

</br>

## Installation

[readme](https://github.com/mongodb/mongo)

</br>

## Algumas linguagens que tem suporte

```python
# JavaScript
# Python
# Java
# C++
# C#
```

Nesse exemplo, vou dedicar a implementações em [Java](https://www.mongodb.com/docs/drivers/java/sync/current/quick-start/)

## Querys no mongoDB

[quick-refence](https://www.mongodb.com/docs/drivers/java/sync/current/quick-reference/)

```kotlin
// Pseudo Codigo

// Class Conector do MongoDB
private val mongoClient: MongoClient

// Conectando com o banco 'leve'
// Conectando com a collection 'movie'
val getCollection = mongoClient
  .getDatabase("leve")
  .getCollection("movie", Movie::class.java)


 var movie = Movie(
            plot = "PLOT01",
            genres = listOf("M"),
            title = "FIM DOS TEMPOS 01EP02TEMP"
        )

// Inserindo dados na Collection, utilizando a class Movie
getCollection.insertOne(movie)

// Atualizando um campo
// 1- Filtra a collection que tive o campo "email" igual a "1gerson.filho@loggi.com"
// 2- Atualiza o campo "notifications" dessa coleção para movie
// .set
getCollection().updateOne(
    Filters.eq("email", "1gerson.filho@loggi.com"),
    Updates.set("notifications",movie)
)

// Busque a coleção com o campo "email" de valor "gerson.filho@loggi.com"
getCollection().find(Filters.eq("email","gerson.filho@loggi.com")).toList()


// Incrementa o campo
// .inc
getCollection().updateOne(
    Filters.eq("email", "1gerson.filho@loggi.com"),
        Updates.inc("qtde",1)
)


// Inclui um novo item. O campo deve ser do tipo Array
// .push
getCollection().updateOne(
    Filters.eq("email", "1gerson.filho@loggi.com"),
        Updates.push("usertokens",movie)
)


// Subistitui todo um documento. O novo dado deve respeitar o tipo
getCollection().replaceOne(
    Filters.eq("email", "1gerson.filho@loggi.com"),
        notification
)

// Verificando se existe um item em um array, de um campo de um documento
// userNotification: {
//    id: 34
//    ...
//    usertokens: [
//        {
//            0: {
//              tokenFCM: 1
//            },
//            1: {
//              tokenFCM: 2
//            }
//        }
//    ]
// }
// A primeira query no mongodb, me retorna o documento, que com
// .first() consigo trabalhar como sendo a class UserNotification
// E nela consigo iterar no attributo usertokens que e um array
// Fiz essa iteração pq não consegui fazer tudo com uma query
// direto no mongodb
val document = getCollection().find(Filters.eq("_id", cognitoSub)).first()

document.usertokens.filter { it.tokenFCM == "userTokenFCM.tokenFCM" }.isEmpty()

```

</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>

```python
import foobar

# returns 'words'
foobar.pluralize('word')

# returns 'geese'
foobar.pluralize('goose')

# returns 'phenomenon'
foobar.singularize('phenomena')
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)
