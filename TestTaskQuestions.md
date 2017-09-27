# Тестовое задание

## Технические навыки

* Работа с базой данных Amazon DynamoDb. [Библиотека которая Вам в этом поможет](http://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/DynamoDB/DocumentClient.html)
* NodeJs
* Работа с Rest Api запросами
* Парсинг документа

### Реализовать скрипт, позволяющий выполнить следующие:
- загрузка текстовых вопросов – напрямую в указанную базу данных (обязательно)
- загрузка вопросов-картинок с помощью существующего Rest api (обязательно)
- загрузка видео вопросов (плюшка в карму за налаживание процесса)

### Порядок выполнения задания:
1. Загрузка документа-ексель и его парсинг в нужном формате. (Выбор npm библиотеки на Ваше усмотрение)
2. Полученные текстовые вопросы преобразовываются в необходимый формат для загрузки в БД. Таблица для тестовой загрузки `kobro-development-questions`. Как только у Вас будет готова эта часть, необходимо будет уточнить аккаунт и таблицы для итоговой загрузки. 

Ключи для БД:

```
"accessKeyId": "AKIAIEDAGSXQFPFB44YA"
"secretAccessKey": "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",
"region": "eu-west-1"
```

```
{
  "answerOptions": [
    String,
    String,
    String,
    String
  ],
  "author": String, //nickname of author
  "correct": String,
  "dateOfCreation": number, //timestampe format
  "dateOfPublication": number, //timestampe format
  "id": String, //id of question
  "labels": [
    String
  ],
  "status": "Published",
  "text": String,
  "type": "text",
  "userId": String //code of user
}
```

Для поля `author` необходимо узнать `nickname` из таблицы `kobro-development-users` по коду `userId`.
Это заполение требует уточнения: `userId` может не соответсвовать реальным данным.

**Пункт считается выполненным в случае полной реализации условия.**


