# Демонстрационное приложение "Библиотека" на фреймворке Laravel5

## Задание

Необходимо реализовать на Laravel/Symfony приложение, которое представляет собой библиотеку, где есть пользователи (User) и книги (Book).

Список действий, которые должны быть доступны при помощи REST API:

- добавление новой книги в библиотеку

- отметка, о взятии книги пользователем (TEST)

- список книг, взятых пользователем

- статистика самых читающих пользователей (TEST)

Отмеченные знаком “(TEST)” действия необходимо покрыть при помощи тестов. Оформить в виде git репозитория, продемонстрировав историю разработки.

## Реализация

### Тезисы

Так как нет четкого технического задания, можем принять следующие принципы создаваемого приложения:

- В приложении должны быть пользователи (User) и книги (Book).

- Так как в классическом приложении под пользователями понимаются операторы работающие в приложении,
а в нашем случае под пользователями понимаются Читатели, то модель User будем воспринимать как "Читатели"
- Для упрощения примера, операторов в системе не будет и авторизация отсутствует.

- Так как в библиотеке может быть несколько экземпляров одной книги, принято решение описание книги хранить в модели "Book".
И реализовать модель "BookUnit" для описания экземпляров книг. Вся дальнейшая работа по выдаче книг и их возврату идет с моделью "BookUnit"

- Журналирование выдачи книги можно производить в модели "BookUnit" через поля: (bool) "на руках", (User) "у читателя", (timestamp) "когда выдано".
Но так как в ТЗ указана возможность получения статистики самых читающих пользователей, то принято решение вести историю взятия книг на руки через модель "BooksInHand".

### Сущьности БД

Book - книги
- name: Наименование книги
- autor: Автор книги
- description: Описание книги

BookUnit - Экземпляры книг
- book_id: Ссылка на книгу
- barcode: Штрих код

BooksInHand - Журнал выдачи экземпляров книг
- book_unit_id: Ссылка на Экземпляр книги
- user_id: Ссылка на Читателя
- take_at: Временная метка выдачи книги
- return_at: Временная метка возврата книги

User - Читатели
- name: ФИО
- email: Эл.адрес
- password: Пароль (не используется)





