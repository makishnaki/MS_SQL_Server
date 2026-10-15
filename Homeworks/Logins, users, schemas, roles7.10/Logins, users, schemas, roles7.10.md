# Домашнее задание

**Студент:**  Егорченкова Кристина
**Группа:**  РПО 11/2
**Тема**  Logins, users, schemas, roles

# Анализ
- **Что изучалось:** блокировка чтения при попытке доступа к незафиксированным данным
- **В чем заключается задание:** пошаговый запуск параллельных транзакций с имитацией удаления строки и фиксацией задержки во второй сессии
- **Какие навыки закрепляет:** предотвращение аномалии грязного чтения и понимание работы разделяемых и монопольных блокировок

## BEGIN TRANSACTION и COMMIT
![бд](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd80.png)

## ROLLBACK
![бд](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd81.png)

## SAVE TRANSACTION
![бд](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd82.png)
![бд](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd83.png)
## Системная функция @@TRANCOUNT
![бд](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd84.png)

## Системное представление sys.dm_tran_locks
![бд](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd85.png)

## Взаимоблокировки (Deadlocks)
![бд](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd86.png)

## Уровень изоляции READ UNCOMMITTED («Грязное чтение»)
![бд](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd89.png)

## Уровень изоляции READ COMMITTED (Защита от грязного чтения)
![бд](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd88.png)
