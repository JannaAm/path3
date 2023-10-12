### 🔥 Испытание 3: «Сердце Джунглей» 🔥

[![Typing SVG](https://readme-typing-svg.herokuapp.com?color=%2336BCF7&lines=Мой+любимый+SQL)](https://git.io/typing-svg)

<img src="https://pa1.narvii.com/7446/9f8a6f798ba73c14efc81d374004d266739c4909r1-400-50_hq.gif" height="32" width="1000"> 

### ✨ Задача 1 ✨
#### Дано: три таблицы.

<br>***Destination (id, name, id_status)***.
<br>***Tickets (id, id_destination, lowest_price, highest_pice)***.
<br>***Status (id, name)***.</br>

**Необходимо**: составить запросы, которые помогут получить следующую информацию:

1. Уникальные названия маршрутов (destination.name), для которых существуют билеты (есть запись в tickets). Вывести только названия.
2. Дополните предыдущий запрос: ограничьте маршруты статусом «No visa».
3. Найдите маршруты, максимальная цена которых выше общей средней. Общая средняя находится как среднее значение lowest_price и highest_price. Вывести названия и высшую цену.

<br>CREATE TABLE Destination ( 
<br>ID INTEGER , 
<br>name VARCHAR(255), 
<br>id_status INTEGER);</br>

<br>CREATE TABLE Tickets (
<br>ID INTEGER, 
<br>id_destination INTEGER, 
<br>lowest_price DECIMAL(10,2), 
<br>highest_price DECIMAL(10,2));</br>

<br>CREATE TABLE Status ( 
<br>ID INTEGER, 
<br>name VARCHAR(255) );</br>

<br>INSERT INTO Destination (ID, name, id_status) 
<br>VALUES 
<br>(1, 'Paris', 1), 
<br>(2, 'London', 2), 
<br>(3, 'New York', 1), 
<br>(4, 'Tokyo', 3), 
<br>(5, 'Sydney', 2);</br>

<br>INSERT INTO Tickets (ID, id_destination, lowest_price, highest_price) 
<br>VALUES 
<br>(1, 1, 100.00, 200.00), 
<br>(2, 2, 150.00, 250.00), 
<br>(3, 3, 200.00, 300.00), 
<br>(4, 4, 250.00, 350.00), 
<br>(5, 5, 300.00, 400.00);</br>

<br>INSERT INTO Status (ID, name) 
<br>VALUES 
<br>(1, 'Available'), 
<br>(2, 'Sold'), 
<br>(3, 'Reserved');</br>

<br>SELECT * FROM Destination;
<br>SELECT * FROM Tickets;
<br>SELECT * FROM Status;</br>

### 🚩 Задача 2 🚩
#### Дано : две таблицы.

**Необходимо**: составить запросы, которые помогут получить следующую информацию:

1. Список уникальных классов. Вывести только названия.
2. Количество часов, проведенных на занятиях, для каждого пользователя. Вывести фамилию, имя и количество часов.
3. Средний возраст пользователей, посещающих класс Flex.

###  ⚡ Задача 3 ⚡
#### Дано: две таблицы. 

**Необходимо**: составить запросы, которые помогут получить следующую информацию:

1. Уникальные названия всех книг, опубликованных после 1990 года. Вывести только названия.
2. Для каждого автора найти сумму напечатанных страниц. Вывести полное имя автора и сумму страниц.
3. Подсчитать количество книг авторов каждого века. Вывести век и количество книг.
