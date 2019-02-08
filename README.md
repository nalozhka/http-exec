# Http-Exec — аддон-микросервис для исполнения всякого внути контейнера #

Сервис работает так: парсит GET-запрос на предмет совпадения с именами файлов в `HTTP_EXEC_BINARY_FOLDER_PATH` (это переменная окружения), и если файл существует и у него есть права на исполнение запускает его и перенаправляет его стандартный вывод в тело HTTP-ответа.

## Аутентификация ##

Есть возможность аутентифицировать входящие запросы с помощью заголовка `X-Nalogka-Auth`.
По умолчанию аутентификация энфорсится — т.е. если явно не указано ее не использовать (`HTTP_EXEC_USE_AUTHENTICATION` == `false` или `no`), считается что она включена.
В этом случае если файла `HTTP_EXEC_SECRET_PATH` (файла, в котором хранится секрет) не существует, или его невозможно открыть, всегда будет возвращаться 403 ошибка.

## Как запускать? ##

Запускается этот микросервис просто — `./http-exec.py` — без аргументов. Слушает по-умолчанию на 8000-м порту.

## Микросервис или нет? ##

Теоритически его можно запускать и на обычной машине.