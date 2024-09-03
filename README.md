# PostgeSQL и Windows
## Входные данные:
- **Пользователь**: `postgres`
- **Пароль пользователя**: `1234`

## Запуск PowerShell и подключение к PostgreSQL:
- Откройте `PowerShell`. Для этого нажмите `Win + R`, введите `powershell` и нажмите `Enter`.
- Перейдите в папку с исполняемыми файлами `PostgreSQL`:
    ```powershell
    cd "C:\Program Files\PostgreSQL\16\bin"
    ```
- **Подключитесь** к `PostgreSQL` под пользователем `postgres`:
    ```powershell
    .\psql -U postgres
    ```
- Введите пароль `1234`, когда будет предложено.
## Создание базы данных:
- **Создайте** базу данных `online_store_tea`:
    ```sql
    CREATE DATABASE online_store_tea;
    ```
## Просмотр всех баз данных:
- Выполнить SQL-команду для получения списка баз данных:
```sql
SELECT datname FROM pg_database;
```
## Подключение к созданной базе данных:
- **Подключитесь** к базе данных:
    ```sql
    \c online_store_tea
    ```
## Изменение кодировки БД:
- Пример **замены кодировки** на `1251`:
    ```sql
    psql \! chcp 1251
    ```
## Создание таблиц:
- Пример **создания** таблицы `products`:
    ```sql
    CREATE TABLE products (
        id SERIAL PRIMARY KEY,
        name VARCHAR(100) NOT NULL,
        price NUMERIC(10, 2) NOT NULL
    );
    ```
## Добавление данных в таблицу:
- Пример **добавления данных** в таблицу `products`:
    ```sql
    INSERT INTO products (name, price) VALUES ('Чай черный', 150.00);
    INSERT INTO products (name, price) VALUES ('Чай зеленый', 200.00);
    ```
## Получение информации из таблицы:
- Пример запроса для **получения** всех продуктов:
    ```sql
    SELECT * FROM products;
    ```
## Удаление столбца из таблицы
- Чтобы **удалить столбец** из таблицы products, используйте команду `ALTER TABLE` с оператором `DROP COLUMN`. Например, для удаления столбца с именем `price`, выполните следующий SQL-запрос:
    ```sql
    ALTER TABLE products DROP COLUMN price;
    ```

## Добавление нового столбца в таблицу
- Чтобы **добавить новый столбец** в таблицу `products`, используйте команду `ALTER TABLE`, с оператором `ADD COLUMN`. Например, если вы хотите добавить столбец `description` типа `VARCHAR`, выполните следующий SQL-запрос:
    ```sql
    ALTER TABLE products ADD COLUMN description VARCHAR(255);
    ```

## Удаление Базы Данных
- Откройте `PowerShell`: Запустите `PowerShell` от имени администратора.
- Используйте команду `dropdb`: Введите следующую команду:
    ```powershell
    dropdb -U postgres online_store_tea
    ```
- **Введите пароль**: Если у вас настроена аутентификация по паролю, вам будет предложено ввести пароль для пользователя PostgreSQL.

### С помощью SQL-запроса
- Удалить базу данных в PostgreSQL с именем `online_store_tea` нужно использовать SQL-команду:
    ```sql
    DROP DATABASE online_store_tea;
    ```