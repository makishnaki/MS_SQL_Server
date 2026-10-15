# Домашнее задание

**Студент:**  Егорченкова Кристина
**Группа:**  РПО 11/2
**Тема**  clustered

# Анализ
- **Что изучалось:** влияние структуры таблицы (куча против B-дерева) на скорость точечного поиска данных
- **В чем заключается задание:** генерация 100 000 строк тестовых данных в Heap-таблицу, замер количества логических чтений до и после создания кластеризованного индекса с помощью команды SET STATISTICS IO ON
- **Какие навыки закрепляет:** анализ стоимости выполнения запросов, сравнение механизмов полного сканирования таблицы Table Scan и поиска по индексу Clustered Index Seek


# Создание кластеризованного индекса на heap-таблице
![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd38.png)

![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd39.png)

![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd40.png)

![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd41.png)

![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd42.png)

![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd43.png)



# Некластеризованный индекс для точечного поиска
![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd44.png)

![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd45.png)

Key lookup используется, потому что в запросе нужны ProductID Name и Price. Последнего в некластеризованном индексе нет, по этому нужно дополнительное обращение key lookup


# Разница между Seek и Scan
![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd46.png)

![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd47.png) 
- Точечный поиск одной уникальной строки по ключу

![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd48.png) 
- Поиск по диапазону

![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd50.png) 
- Полное сканирование потому что условию соответствуют все строчки


# Хранилище запросов
## Топ ресурсоемких запросов
![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd57.png) 

## Общее потребление ресурсов
![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd58.png) 

## Статистика ожидания запросов
![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd59.png) 


![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd51.png) 
![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd52.png) 
![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd53.png) 
![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd54.png) 
![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd55.png) 
![функция](https://github.com/makishnaki/MS_SQL_Server/blob/main/picFolder/bd56.png) 
