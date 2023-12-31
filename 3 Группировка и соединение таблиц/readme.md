# Группировка и соединение таблиц

1. Преобразование данных
2. Создать Источник - Excel
3. Выбираем файл Продажи по магазинам 19.04.2020 - 21.04.2020.xlsx
4. Загружаем все три

Таблица Товар
- Есть пробелы в столбце Категория
- Преобразование - Столбец Текст - Формат - Функция Усечь (trim)

Таблица Продажи
- Управление столбцами - Выбор столбцов - убираем ненужные столбцы (например пустые)


Что такое Группировка?
У нас есть объем записей, мы делим их на группы по какому-то признакому.
Затем по каждой из этих групп можно сделать подсчет.
- Делим на группы по какому-то признаку
- Проводим подсчет по каждой группе

#### Создание Настраиваемого столбца
1. Таблица Продажи
Выбираем столбец Продано шт.
Добавление столбца - Настраиваемый Столбец
Имя нового столбца - Сумма продаж, руб.
Настраиваемые формулы столбца - пишем =
Нажимаем на Цена продаж в Доступные столбцы затем * и выбираем Продано шт. и жмем ОК
Выбираем Тип данных - Целое число

2. Таблица Товар
Нам нужно выбрать первое слово в категориях и добавить суффикс
- Добавление стобца - Настраиваемый столбей
- Настраиваемая формула столбца = Text.Combine({"Префикс",Text.BeforeDelimiter([Категория], " ")}, " - ")

#### Создание Условного столбца
1. Таблица Товар
Мы хотим изменить некоторые строки столбца Категория. Например: Фрукты и Овощи поменять на Фру и ов. А Бакалея на Бак.
- Добавление столбца - Условный столбец
- Имя нового столбца - Категория с заменой
- Если ID товара равно 3 Фр и Ов
- Добавить предложение
- Если ID товара равно 4 Бак.
- В противном случае - Выберите столбец - Категория

#### Создание столбца Индекса
1. Таблица Товар
- Добавление столбца - Столбец индекса
- От 1 или можно настроить 

#### Создание столбца из примеров
1. Таблица Товар
- Выбираем Категория
- Столбец из примеров - Из выделения
- Даем название новому столбцу - Первое слово в категории
- Хлебопекарные 
Здесь по первому примеру PowerBI предлагает варианты для остальных строк

#### Группировка столбцов
1. Таблица Продажи
- Продажи - Ссылка
- Переименуем - Продажи по магазинам
Нам нужно сгруппировать данные по каждому магазину и понять сколько всего мы по ним продали.
- Главная страница - Группировать по 
- ID магазина
Что можно рассчитать
- Имя нового столбца - Сумма продаж, руб.
- Операция - Сумма
- Столбец - Сумма продаж, руб.

2. Таблица Продажи
- Продажи - Ссылка
- Переименуем - Средние продажи товаров в день по одному магазину
Нам нужно сгруппировать данные по магазину и понять сколько всего товаров мы в среднем продали.
- Главная страница - Группировать по 
- ID товара
Что можно рассчитать
- Имя нового столбца - В среднем продано, шт.
- Операция - Среднее
- Столбец - Продано шт.

3. Таблица Продажи
- Продажи - Ссылка
- Переименуем - Продажи по магазинам и товарам
Нам нужно сгруппировать данные по магазину и товарам и показать общую сумму продаж по ним.
- Главная страница - Группировать по 
- Подробнее
- ID магазина
- ID товара
Что можно рассчитать
- Имя нового столбца - Сумма продаж, руб.
- Операция - Сумма
- Столбец - Сумма продаж, руб.
- Добавить агрегирование
- Имя нового столбца - Продано шт.
- Операция - Сумма
- Столбец - Продано шт.

#### Объединение/слияние таблиц c одинаковой структурой и типами данных
Продажи в нескольких файлах
- Загрузим файлы 
- Выбираем Продажи и жмем ОК
- Выбираем нужные столбцы

Для того чтобы объединить у нас должны быть одинкаовое число и названия колонок 
- Загрузим первоначальные Продажи 
- Выбираем Продажи и жмем ОК
- Выбираем нужные столбцы
Проверяем колонки у обеих таблиц
1. Таблица Продажи2
- Главная страница - Объединить - Добавить запросы
- Две таблицы
 
#### Соединение таблиц с разной структурой по связи "Один ко многим". 
Внешние/внутренние соединение/анти-соединение слева/справа
1. Таблица Продажи по магазинам и товарам
- Главная страница - Объединить - Объединить запросы (Join, Merge)
- Магазин
- Выбираем из таблицы сверху и снизу ID магазина
- Тип соединения - Внешние соединение слева - ОК
- Столбец Магазин - жмем две стрелки для раскрытия 
- Выбираем Магазин и Количество сотрудников

2. Таблица Продажи по магазинам и товарам
- Главная страница - Объединить - Объединить запросы (Join, Merge)
- Магазин
- Выбираем из таблицы сверху и снизу ID товара
- Тип соединения - Внешние соединение слева - ОК
- Столбец Товар - жмем две стрелки для раскрытия 
- Выбираем Товар

Матрица
Выбираем столбцы
Преобразование - Отменить свертывание столбцов (unpivot)

можно обратно преобразовать
выбираем столбец Год
преобразование -столбец сведения
Столбец значений - Продажи, руб.

Создание параметров на примере Пути к источнику данных

Как можно смотреть со своего компьютера, так как путь к файлу может быть разный нужно указать свой путь к файлу источнику. Чтобы каждый раз его не укаызвать, создаем свой путь к файлу

Главная - Управление параметрами - Создать параметр
Даем имя чтобы легко отличить
Тип - Текст
Текущее значение - путь к вашему файлу источнику

Источник - Путь к файлу
Выбираем ваш параметр - ок
 
