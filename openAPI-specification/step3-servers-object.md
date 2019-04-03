# Руководство OpenAPI Шаг 3: Объект `servers`

| [*Шаг 1: объект* `openapi`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.5.%20Step%201%20The%20openapi%20object.md) | --> | [*Шаг 2: объект* `info`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.6.%20Step%202%20The%20info%20object.md) | --> | [**Шаг 3: объект** `servers`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.7.%20Step%203%20The%20servers%20object.md) | --> | [*Шаг 4: объект* `paths`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.8.%20Step%204%20The%20paths%20object.md) | --> | [*Шаг 5: объект* `components`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.9.%20Step%205%20The%20components%20object.md) | --> | [*Шаг 6: объект* `security`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.10.%20Step%206%20security%20object.md) | --> | [*Шаг 7: объект* `tags`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.11.%20Step%207%20The%20tags%20object.md) | --> | [*Шаг 8: объект* `externalDocs`](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/4.12.%20Step%208%20The%20externalDocs%20object.md) |

В объекте `servers` указывается базовый путь, используемый в ваших запросах API. Базовый путь - это часть URL, которая находится перед конечной точкой.

[Пример объекта `servers`](#sample)

[Опции URL сервера](#options)

[Отображение в Swagger UI](#appearance)

<a name="sample"></a>
## Пример объекта `servers`

Пример объекта `servers`

    servers:
    - url: https://api.openweathermap.org/data/2.5/

Каждая из конечных точек (называемых в спецификации `paths`) будет добавляться ​​к URL-адресу сервера, при отправке пользователями пробных запросов `Try it out`. Например, если одним из путей является` /weather`, то при отправке запроса Swagger UI представит путь к `{server URL}{path}` или [https://api.openweathermap.org/data/2.5/weather](https://api.openweathermap.org/data/2.5/weather).
<a name="options"></a>
## Опции URL сервера

Объект `servers` обладает гибкой настройкой. Можно указать несколько URL-адресов серверов, которые могут относиться к различным средам (тестовая, бета-версия, рабочая версия). При наличии нескольких URL-адресов серверов, пользователи могут выбирать среду в раскрывающемся списке серверов. Можно указать несколько URL-адресов серверов, например:

    servers:
      - url: https://api.openweathermap.org/data/2.5/
        description: Production server
      - url: http://beta.api.openweathermap.org/data/2.5/
        description: Beta server
      - url: http://some-other.api.openweathermap.org/data/2.5/
        description: Some other server

В Swagger UI выбор из нескольких серверов осуществляется при помощи выпадающего списка

![multiservers](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/img/7.png?raw=true)

Если указан один сервер все равно будет отображаться выпадающий список, но с одним вариантом.

В URL-адрес сервера также можно включать переменные, которые будут заполняться сервером во время выполнения. Кроме того, если для разных путей (конечных точек) требуются разные URL-адреса сервера, можно добавить объект `servers` в качестве свойства в объекте операции объекта `path`. URL-адрес локально объявленных серверов переопределяет URL-адрес глобальных серверов.

См. [Overriding Servers](https://swagger.io/docs/specification/api-host-and-base-path/) в разделе «Сервер API и базовый URL» (документы Swagger) для получения дополнительной информации.

<a name="appearance"></a>
## 👨‍💻 Отображение в Swagger UI

Вставим объект `servers` (первый пример кода выше, показывающий только один URL) в редактор Swagger, добавив к имеющемуся коду. Swagger UI будет выглядеть следующим образом:

![servers](https://github.com/Starkovden/Documenting_APIs/blob/master/4.%20OpenAPI%20specification%20and%20Swagger/img/8.png?raw=true)