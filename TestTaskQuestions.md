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
  "status": "Test",
  "text": String,
  "type": "text",
  "userId": String //code of user
}
```

Для поля `author` необходимо узнать `nickname` из таблицы `kobro-development-users` по коду `userId`.
Это заполение требует уточнения: `userId` может не соответсвовать реальным данным.
После того как загрузка будет происходить не в тестовый аккаунт, поле "status": "Published".

При загрузке также учесть, что пропускная способность таблицы ограничена. Поэтому загрузку стоит производить с таймаутами, которые определить опытным путем, исходя из характеристик таблицы.

**Пункт считается выполненным в случае полной реализации условия.**

3. Для тестов необходимо использовать существующий сервер, к которому можно обратиться по адресу `появится чуть позже` 
с заголовком 
`Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJodHRwOi8va29icm8uY29tIiwiYXVkIjoiaHR0cDovL2tvYnJvLmNvbSIsImV4cCI6MjQ3MDk4MjgwMCwibmJmIjoxNDcwOTc1NjAwLCJzdWIiOiI1OEEzRjg2MTg0NDQ0ODZGODAxMzU3NEY0IiwiaWRwIjoid2luYXV0aCIsImFtciI6WyJDb29raWVzIl0sInVzZXIiOnsic3RhZmYiOiJzdGFmZiIsInBob25lTm1iIjoiMSIsImF2YXRhciI6Imh0dHBzOi8vbGgzLmdvb2dsZXVzZXJjb250ZW50LmNvbS8tWGRVSXFkTWtDV0EvQUFBQUFBQUFBQUkvQUFBQUFBQUFBQUEvNDI1MnJzY2J2NU0vcGhvdG8uanBnP3N6PTUwIiwiZW1haWwiOiJhbmFzdGFzaWEucGVybWlub3ZhQG1pZm9ydC5vcmciLCJwZXJtcyI6WyJjcmVhdGUiLCJzZWU6b3duIiwidXNlciIsImVkaXQiLCJwbGF5Il0sImNvZGUiOiIyNjEiLCJhdXRoIjp7Imdvb2dsZSI6eyJhY2Nlc3NUb2tlbiI6InlhMjkuR2wzWEJGOXJkME9CVGdESFVxLUhjeEt2RnBBdTFvVkFpVTR2aUJNajBIREppT1FsSDNHT0FodU91akN3Mk5QZDk0TTJaZnUyVlFkSTVfZ0ZER2RENmMxeWc2cnVSUDlBNEtHR0MwTEVuWnRZTTl2Z0U1WHFYZ3g3QVRxLWdwYyIsImlkIjoiMTA3ODMzNjc3MzAwMzc1MDYzNjYzIiwidGltZXN0YW1wIjoxNTA2ODc5MDkzNzE0fX0sImFtb3VudFJldmlld2VkUXVlc3Rpb25zIjowLCJyb2xlIjoic3VwcGxpZXIiLCJuaWNrbmFtZSI6IkFuYXN0YXNpYVBicm8iLCJuYW1lcyI6WyJBbmFzdGFzaWEiLCJQZXJtaW5vdmEiXSwicGFzc3BvcnQiOiIxIn0sImlhdCI6MTUwNjg3OTA5M30.bQr7XjuOU-UGRDmN11rBw6Y5uh_iYRuUq7ltwmbyfp4FhS999gXgOFyetOliJQ0eg96n4CU6qncTVxNDVcGxCOPaWDRLD52wKZxKCiZXehKRVrrmXj-xYwEL5-i5HngIahfMyVdvImc9h3U2S5E2xcDMwMExLHroImo0v7mxShc` на урл /question, формат - POST

Тело запроса:
```
{
  answerDetailed: String,
  answerOptions: [String]
  author: String,
  correct: String,
  image: {
  awsSourse: "https://s3-eu-west-1.amazonaws.com/kobro.downloads/Unit-Test-1.png", // Уточнить
  name: "Unit-Test-1.png",
  path: "src/main/resources/static/downloads/Unit-Test-1.png"
  },
  labels: [String]
  points: {start: {x: 0, y: 0}, end: {x: 119, y: 64}} //Координаты нарезки - уточнить
  text: String,
  type: "image"
```
* !!!!В базу зарегать сапплайеров. ИЛИ ПРОЩЕ РУКАМИ БЕЗ СЕРВИСА СДЕЛАТЬ? *

С помощью указанного токена занести вопросы в базу. Сохранить соотношение айдишников вопросов и userId. По этим userId сопоставить никнейм автора, имя и фамилию в виде массива строк: `[String, String]`, увеличить ему поле amountQuestions на нужное количество. Сохранить изменения. 

После того как загрузка будет происходить не в тестовый аккаунт, пройтись по базе и установить поле "status": "Published".

При загрузке также учесть, что пропускная способность таблицы ограничена. Поэтому загрузку стоит производить с таймаутами, которые определить опытным путем, исходя из характеристик таблицы.

**Пункт считается выполненным в случае полной реализации условия.**

4. Загрузка видео вопроса будет происходить следующим образом. Необходимо скачать видео из документа по ссылкам, разрезать в нужном месте. Загрузить на S3 по отдельности исходное видео, видео-вопрос и ответ. Полученные данные сохранить в БД. Credentials теже, что и при загрузке в DynamoDb.
```
{
  "answerOptions": [String],
  "author": String,
  "correct": String,
  "dateOfCreation": timestamp - number,
  "dateOfPublication": timestamp - number,
  "fullVideo": "https://s3-eu-west-1.amazonaws.com/kobro.video/030001e0-5be5-11e7-9183-153259fffa33.mp4", //урл где хранится видео на S3
  "id": String, //генерируется программно
  "labels": [String],
  "offset": Number, //Уточнить
  "path": "D:\\Projects\\kobro-cms\\src\\main\\resources\\static\\downloads\\eN2dFz0yiq8.mp4", //уточнить
  "point": "25:31", //Точка нарезки
  "status": "Test",
  "text": String,
  "type": "video",
  "url": "https://www.youtube.com/watch?v=eN2dFz0yiq8", //исходный урл из екселя
  "urlAnswer": "https://s3-eu-west-1.amazonaws.com/kobro.video/030001e0-5be5-11e7-9183-153259fffa33-answer.mp4", //нарезанный кусок
  "urlQuestion": "https://s3-eu-west-1.amazonaws.com/kobro.video/030001e0-5be5-11e7-9183-153259fffa33-question.mp4", //нарезанный кусок
  "userId": String // уточнить
}
```
