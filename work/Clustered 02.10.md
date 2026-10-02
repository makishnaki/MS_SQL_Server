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
