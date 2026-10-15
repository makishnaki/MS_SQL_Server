# Домашнее задание

**Студент:**  Егорченкова Кристина
**Группа:**  РПО 11/2
**Тема**  Loks, blocking

# Анализ
- **Что изучалось:** разработка безопасных хранимых процедур с комплексной валидацией данных и транзакционной логикой
- **В чем заключается задание:** реализация бизнес-процессов зачисления студентов и перевода между группами с контролем свободных мест, валидацией ограничений через THROW RAISERROR и логированием изменений
- **Какие навыки закрепляет:** написание защищенных процедур с конструкцией TRY...CATCH, управление конкурентным доступом с помощью подсказок блокировок UPDLOCK, ROWLOCK, генерация кастомных ошибок и обеспечение атомарности бизнес-операций


## 1.1 Зачисление студента
![sql](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd31.png)

![sql](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd32.png)
-
## 1.2 Перевод студента
![sql](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd34.png)

![sql](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd35.png)
-
## 2.2 Согласованность
![sql](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd36.png)

![sql](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd37.png)
-
