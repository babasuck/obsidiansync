
## Выборка данных

`find()` - найти документ по заданной информации, если без параметров вернет **Cursor** (по сути итератор) всех документов.
`findOne()` - найти один документ

```shell
db.users.find({name: "Tom", age: 32})
db.users.find({name: null}) # У кого нет имени
```

## Вставка данных

`insertOne()` - вставляет документ в коллекцию, передавать BSON
```shell
db.users.insertOne({"name": "Tom", "age": 32, languages: ["english", "german"]})
```
