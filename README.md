# TodoApi

Учебный пример минимального API на ASP.NET Core по [руководству с Microsoft Learn](https://learn.microsoft.com/aspnet/core/fundamentals/minimal-apis/), адаптированный для хранения списка задач. Проект демонстрирует:
- применение Entity Framework Core с встроенной InMemory-базой;
- использование `RouteGroupBuilder` для группировки маршрутов;
- автоматическую генерацию OpenAPI/Swagger через `NSwag.AspNetCore`.

## Запуск

```bash
dotnet restore
dotnet run
```

По умолчанию приложение стартует на `https://localhost:7247` и `http://localhost:5150`. В режиме разработки доступна документация по адресу `https://localhost:7247/swagger`.

## Доступные конечные точки

Все маршруты сгруппированы под префиксом `/todo-items`. Возвращаются DTO без поля `Secret`.

| Метод | Маршрут           | Описание                               |
|-------|-------------------|----------------------------------------|
| GET   | `/todo-items/`    | Получить все задачи                    |
| GET   | `/todo-items/complete` | Получить только завершённые задачи |
| GET   | `/todo-items/{id}` | Получить задачу по идентификатору     |
| POST  | `/todo-items/`    | Создать задачу                         |
| PUT   | `/todo-items/{id}` | Обновить существующую задачу          |
| DELETE| `/todo-items/{id}` | Удалить задачу                         |

## Пример запроса

```bash
curl -X POST https://localhost:7247/todo-items/ \
  -H "Content-Type: application/json" \
  -d '{ "name": "Посмотреть урок про Minimal API", "isComplete": false }'
```

## Стек

- .NET 9
- ASP.NET Core Minimal API
- Entity Framework Core InMemory provider
- NSwag для OpenAPI
