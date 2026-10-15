# Представления (VIEW) в SQL Server

**Представление (View)** — это виртуальная таблица, которая в отличие от обычных таблиц не хранит физические данные, а содержит SQL-запрос, динамически извлекающий информацию в момент обращения.

## 1. Преимущества использования представлений
* **Упрощение комплексных операций:** Позволяют скрыть сложные `JOIN`-соединения и вложенные запросы за простым именем виртуальной таблицы.
* **Защита данных:** Позволяют гибко разграничивать доступ, предоставляя пользователю доступ только к определенной части полей или строк базовой таблицы, а не ко всей базе данных.
* **Форматирование данных:** Позволяют возвращать данные из таблиц в уже предопределенной, удобной для конечного пользователя форме.

## 2. Специальные типы представлений в T-SQL
Помимо стандартных пользовательских представлений выделяют:
* **Индексированные представления** (физически сохраняют вычисленный результат на диске для ускорения сложных выборок).
* **Секционированные представления** (собирают данные из нескольких горизонтально разделенных таблиц).
* **Системные представления** (предоставляют метаданные о самой СУБД).

---

## 3. Модифицируемые представления (Updatable Views)
**Модифицируемое представление** — это представление, через которое можно изменять данные (`UPDATE`, `INSERT`, `DELETE`) в базовых таблицах, на которых оно построено.

### Критерии модифицируемости (ANSI):
1. Запрос должен ссылаться **строго на одну** базовую таблицу.
2. Желательно наличие первичного ключа этой таблицы в списке вывода.
3. Отсутствие агрегатных функций (`SUM`, `AVG`, `COUNT` и др.).
4. Отсутствие ключевого слова `DISTINCT`.
5. Отсутствие конструкций `GROUP BY` или `HAVING`.
6. Отсутствие подзапросов в секции выборки и фильтрации (в некоторых реализациях СУБД это ограничение смягчено).
7. Отсутствие констант, строк или вычисляемых выражений (например, `comm * 100`) среди выбранных полей.
8. Для выполнения `INSERT` представление должно включать все столбцы базовой таблицы с ограничением `NOT NULL`, если для них не задано значение по умолчанию (`DEFAULT`).

---

## 4. Синтаксис и примеры операций (DDL / DML)

### Исходная структура таблиц для примеров:
```sql
CREATE TABLE Products(
    Id INT IDENTITY PRIMARY KEY,
    ProductName NVARCHAR(30) NOT NULL,
    Manufacturer NVARCHAR(20) NOT NULL,
    ProductCount INT DEFAULT 0,
    Price MONEY NOT NULL
);

CREATE TABLE Customers(
    Id INT IDENTITY PRIMARY KEY,
    FirstName NVARCHAR(30) NOT NULL
);

CREATE TABLE Orders(
    Id INT IDENTITY PRIMARY KEY,
    ProductId INT NOT NULL REFERENCES Products(Id) ON DELETE CASCADE,
    CustomerId INT NOT NULL REFERENCES Customers(Id) ON DELETE CASCADE,
    CreatedAt DATE NOT NULL,
    ProductCount INT DEFAULT 1,
    Price MONEY NOT NULL
);
```

### Создание представления (`CREATE VIEW`)
Объединяет три таблицы с помощью оператора `INNER JOIN`:
```sql
CREATE VIEW OrdersProductsCustomers AS
SELECT Orders.CreatedAt AS OrderDate, 
       Customers.FirstName AS Customer,
       Products.ProductName As Product
FROM Orders 
INNER JOIN Products ON Orders.ProductId = Products.Id
INNER JOIN Customers ON Orders.CustomerId = Customers.Id;
```

### Выборка данных из представления
Используется точно так же, как и обычный `SELECT` к физической таблице:
```sql
SELECT * FROM OrdersProductsCustomers;
```

### Изменение логики представления (`ALTER VIEW`)
Используется для перезаписи структуры без удаления прав доступа:
```sql
ALTER VIEW OrdersProductsCustomers AS 
SELECT Orders.CreatedAt AS OrderDate, 
       Customers.FirstName AS Customer,
       Products.ProductName AS Product,
       Products.Manufacturer AS Manufacturer -- Добавили новое поле
FROM Orders 
INNER JOIN Products ON Orders.ProductId = Products.Id
INNER JOIN Customers ON Orders.CustomerId = Customers.Id;
```

### Удаление представления (`DROP VIEW`)
```sql
DROP VIEW OrdersProductsCustomers;
```
*Примечание: при удалении базовых физических таблиц необходимо вручную удалить зависимые от них представления.*
