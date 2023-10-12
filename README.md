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
<br>(5, 'Sydney', 4);</br>

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
<br>(3, 'Reserved')
<br>(4, 'No visa');</br>

<br>SELECT * FROM Destination;
<br>SELECT * FROM Tickets;
<br>SELECT * FROM Status;</br>

<br> 1. Уникальные названия маршрутов (destination.name), для которых существуют билеты (есть запись в tickets). Вывести только названия.
#### Запрос 
SELECT DISTINCT d.name FROM Destination d 
INNER JOIN Tickets t ON d.ID = t.id_destination;

<br> 2. Дополните предыдущий запрос: ограничьте маршруты статусом «No visa».
#### Запрос 
<br>SELECT DISTINCT d.name FROM Destination d 
<br>INNER JOIN Tickets t ON d.ID = t.id_destination 
<br>INNER JOIN Status s ON d.id_status = s.ID WHERE s.name = 'No visa';</br>

3. Найдите маршруты, максимальная цена которых выше общей средней.
<br>Общая средняя находится как среднее значение lowest_price и highest_price. Вывести названия и высшую цену.</br>
#### Запрос
<br>SELECT d.name, MAX(t.highest_price) AS highest_price FROM Destination d 
<br>INNER JOIN Tickets t ON d.ID = t.id_destination WHERE (t.highest_price + t.lowest_price)/2 > 
<br>(SELECT AVG(highest_price + lowest_price)/2 FROM Tickets) 
<br>GROUP BY d.name;</br>

<img src="https://pa1.narvii.com/7446/9f8a6f798ba73c14efc81d374004d266739c4909r1-400-50_hq.gif" height="32" width="1000"> 


### 🚩 Задача 2 🚩
#### Дано : две таблицы.

**Необходимо**: составить запросы, которые помогут получить следующую информацию:

1. Список уникальных классов. Вывести только названия.
2. Количество часов, проведенных на занятиях, для каждого пользователя. Вывести фамилию, имя и количество часов.
3. Средний возраст пользователей, посещающих класс Flex.

<br>CREATE TABLE users 
<br>( id_user INTEGER, 
<br>user_name VARCHAR(255), 
<br>user_surname VARCHAR(255), 
<br>user_weight DECIMAL(5,2), 
<br>age INTEGER);</br>

<br>CREATE TABLE visits 
<br>( id_visit INTEGER, 
<br>id_user INTEGER, 
<br>hours_spent INTEGER, 
<br>class_name VARCHAR(255), 
<br>visit_date DATE);</br>

<br>INSERT INTO users (id_user, user_name, user_surname, user_weight, age) 
<br>VALUES 
<br>(1, 'Anna', 'Ivanova', 56, 18), 
<br>(2, 'Igor', 'Bulik', 75, 45), 
<br>(3, 'Max', 'Nikolsky', 67, 16), 
<br>(4, 'Kate', 'Svet', 66, 30);</br>


<br>INSERT INTO visits (id_visit, id_user, hours_spent, class_name, visit_date) 
VALUES 
<br>(1, 1, 1, 'Zumba', '2023-06-30'), 
<br>(2, 3, 2, 'Swimming pool', '2023-07-04'), 
<br>(3, 5, 1, 'Flex', '2023-07-09'), 
<br>(4, 1, 3, 'Flex', '2023-07-15'), 
<br>(5, 5, 2, 'Step', '2023-07-20'), 
<br>(6, 2, 1.5, 'Football', '2023-07-22');</br>

<br>SELECT * FROM users;
<br>SELECT * FROM visits;</br>

<br>1. Список уникальных классов. Вывести только названия. 
#### Запрос 
SELECT DISTINCT class_name
FROM visits;

2. Количество часов, проведенных на занятиях, для каждого пользователя. Вывести фамилию, имя и количество часов.
#### Запрос 
<br>SELECT users.user_surname, users.user_name, SUM(visits.hours_spent) AS total_hours_spent 
<br>FROM users JOIN visits ON users.id_user = visits.id_user 
<br>GROUP BY users.user_surname, users.user_name;</br> 

3. Средний возраст пользователей, посещающих класс Flex.
#### Запрос
<br>SELECT AVG(users.age) AS average_age 
<br>FROM users JOIN visits ON users.id_user = visits.id_user 
<br>WHERE visits.class_name = 'Flex';</br>

<img src="https://pa1.narvii.com/7446/9f8a6f798ba73c14efc81d374004d266739c4909r1-400-50_hq.gif" height="32" width="1000"> 

###  ⚡ Задача 3 ⚡
#### Дано: две таблицы. 

**Необходимо**: составить запросы, которые помогут получить следующую информацию:

1. Уникальные названия всех книг, опубликованных после 1990 года. Вывести только названия.
2. Для каждого автора найти сумму напечатанных страниц. Вывести полное имя автора и сумму страниц.
3. Подсчитать количество книг авторов каждого века. Вывести век и количество книг.

<br>CREATE TABLE book
<br>(id_book INTEGER, 
<br>title VARCHAR, 
<br>id_author INTEGER,
<br>pages INTEGER,
<br>year_puplish DATE);</br>

<br>CREATE TABLE author 
<br>(id_author INTEGER,
<br>full_name VARCHAR,
<br>century INTEGER);</br>

<br>INSERT INTO book (id_book, title, id_author, pages, year_puplish) 
<br>VALUES 
<br>(1, 'Harry Potter and the Philosopher''s Stone', 1, 327, '1997-06-26'),
<br>(2, 'To Kill a Mockingbird', 2, 281, '1960-07-11'),
<br>(3, 'The Great Gatsby', 3, 180, '1925-04-10'),
<br>(4, 'Pride and Prejudice', 4, 279, '1813-01-28'),
<br>(5, '1984', 5, 328, '1949-06-08');</br>

<br>INSERT INTO author (id_author, full_name, century)
<br>VALUES
<br>(1, 'J.K. Rowling', 20),
<br>(2, 'Harper Lee', 20),
<br>(3, 'F. Scott Fitzgerald', 20),
<br>(4, 'Jane Austen', 19),
<br>(5, 'George Orwell', 20);</br>

<br>SELECT * FROM book;
<br>SELECT * FROM author;</br>

1. Уникальные названия всех книг, опубликованных после 1990 года. Вывести только названия.
#### Запрос
<br>SELECT DISTINCT title
<br>FROM book
<br>WHERE year_puplish > '1990-12-31'; </br>


2. Для каждого автора найти сумму напечатанных страниц. Вывести полное имя автора и сумму страниц.
#### Запрос
<br>SELECT author.full_name, SUM(book.pages) AS total_pages
<br>FROM book
<br>JOIN author ON book.id_author = author.id_author
<br>GROUP BY author.full_name;</br>


3. Подсчитать количество книг авторов каждого века. Вывести век и количество книг.
#### Запрос
<br>SELECT author.century, COUNT(book.id_book) AS book_count
<br>FROM book
<br>JOIN author ON book.id_author = author.id_author
<br>GROUP BY author.century;</br>

<img src="https://pa1.narvii.com/7446/9f8a6f798ba73c14efc81d374004d266739c4909r1-400-50_hq.gif" height="32" width="1000"> 
