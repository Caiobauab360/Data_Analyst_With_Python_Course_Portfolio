# Introduction to SQL

**Course description:**

Much of the world's raw data—from electronic medical records to customer transaction histories—lives in organized collections of tables called relational databases. Being able to wrangle and extract data from these databases using SQL is an essential skill within the data industry and in increasing demand.

In this two-hour introduction to SQL, you'll get to know the theory and the practice through bite-sized videos and interactive exercises where you can put your new-found skills to the test.

SQL is an essential language for building and maintaining relational databases, which opens the door to a range of careers in the data industry and beyond. You’ll start this course by covering data organization, tables, and best practices for database construction.

The second half of this course looks at creating SQL queries for selecting data that you need from your database. You’ll have the chance to practice your querying skills before moving on to customizing and saving your results.

PostgreSQL and SQL Server are two of the most popular SQL flavors. You’ll finish off this course by looking at the differences, benefits, and applications of each. By the end of the course you’ll have some hands-on experience in learning SQL and the grounding to start applying it on projects or continue your learning in a more specialized direction.

# Relational Databases

**Chapter description:**

Before writing any SQL queries, it’s important to understand the underlying data. In this chapter, we’ll discover the role of SQL in creating and querying relational databases. Using a database for a local library, we will explore database and table organization, data types and storage, and best practices for database construction.

# Databases 

**Personal notes:**

Databases are electronic systems designed to store and organize data efficiently. It is possible to configure a database containing information, as illustrated in the lesson's example, about clients, books, and transactions. This information is stored in objects called tables, with data organized in rows and columns. The lesson's database comprises a user table, a book table, and a checkout table.

A relational database establishes connections between data tables within the database. Through these relationships, we can draw conclusions about data stored in separate tables within the same database.

In contrast to data visualization tools like Excel, databases can store a significantly larger amount of data, and their storage is more secure due to encryption. The primary advantage of a database lies in its ability to allow multiple users to write queries simultaneously, collecting insights from the data. When a database is queried, the stored data remains unchanged; instead, the database information is accessed and presented based on the query instructions.

SQL - Structured Query Language, is the most widely used programming language for creating, querying, and updating relational databases.

**Exercises:**

**What are the advantages of databases?**

Which of the following are advantages of storing data in a database, rather than using traditional formats like spreadsheets?

        "All of the above"

**Data organization**

Understanding the organization of a database is an important first step when using SQL.

Take a look at the database below. Which of the following statements correctly describes its organization?

        "This is a relational database containing three tables: employees, job_levels, and departments."       

# Tables

**Personal notes:**

Tables contain related data on a specific subject within a database. They are organized in rows and columns, with rows commonly referred to as records and columns as fields. The fields in a table are constrained to those defined when the database was created, but the number of rows is unlimited.

Good table manners:

Table names should be in lowercase and cannot include spaces; underscores (_) are used instead. Ideally, a table name refers to a collective group, and it is acceptable to use plural names.

A record is a row in a table, containing data about an individual observation. A field is a column in a table, providing information about all observations in the table. As field names must be typed when querying a database with SQL, proper field nomenclature is crucial.

Field names should be in lowercase, without spaces, and in the singular form, referring to the information in that field for a single record. Two fields in a table cannot share the same name and should never have a name identical to the table in which they reside.

A unique identifier, sometimes called a "key," is a distinctive value that identifies a record, allowing it to be distinguished from other records in the same table. This value is often a number.


**Exercises:**

**Picking a unique ID**

A unique identifier is a value that distinguishes a record from others in the same table.

In the employees table, which fields do you believe is the most suitable choice for a unique identifier?

        'id'

**Setting the table in style**

Here are two versions of a table taken from a database.

Which table uses the correct naming format?

![Image 1](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/5ee9214e-e025-438d-8e1c-23ee63ecba2c)

# Data

**Personal notes:**

When creating a table, specifying a data type for each field is crucial. The chosen data type depends on the nature of the data the field will contain, as different data types are stored and processed differently, occupying varying amounts of storage space. Furthermore, specific operations may apply only to certain data types. Here are some commonly used data types:

VARCHAR: This is the most flexible data type and can store strings of varying lengths, from small to large – even up to tens of thousands of characters.

INT: A common integer data type capable of storing numbers ranging from just under two billion negative to just over two billion positive.

NUMERIC: This data type can store floating-point numbers with up to 38 digits, including those before and after the decimal point.

Schemas

Schemas are often referred to as the "blueprints" of a database. A schema illustrates the design of a database, showcasing included tables and any relationships among them. It also outlines the type of data each field can contain, providing a comprehensive overview of the database structure.

Database Storage

The data we encounter in a database table is physically stored on the hard drive of a server. Servers, centralized computers that perform services through network requests, handle tasks such as data access in our context. While any computer can serve as a server when configured to provide a service, servers are typically large and powerful machines equipped to manage high volumes of data requests. They play a crucial role not only in data access but also in accessing websites or files stored on the server.


**Exercises:**

**At your service**

Now that you know more about how data is stored, it's time to test those skills!

Select the statement about database storage that is false.

        "Servers are usually personal computers such as laptops."

**Finding data types**

Imagine that you are starting a new job and have just started getting to know your new employer's database. You know that it's important to know the data type—such as VARCHAR, INT, or NUMERIC—corresponding to each field in a table. Where could you find this information?

        "You can find this information by looking at a database schema."

# Querying

**Chapter description:**

Learn your first SQL keywords for selecting relevant data from database tables! After practicing querying skills in a database of books, you’ll customize query results using aliasing and save them as views so they can be shared. Finally, you’ll explore the differences between SQL flavors and databases such as PostgreSQL and SQL Server.

# Introducing queries

**Personal notes:**

**Introducing Queries**

In many organizations, SQL serves as a complement to other tools, such as spreadsheet applications. If the data of interest fits into a spreadsheet and has few relations with other relevant data, analyzing it within a spreadsheet might be sufficient. However, for extensive and diverse data, like those associated with a retail platform, organizing the data into a database proves to be a more effective approach.

**Keywords*

Keywords are reserved words used to indicate the operation we want our code to perform. The two most common keywords are SELECT and FROM. For instance, if we desire a list of all users in our library, the SELECT keyword specifies which fields should be selected, in this case, the "name" field.

```sql
SELECT name
```

The FROM keyword indicates the table where these fields are located; in this case, it is the "patrons" table.

```sql
FROM patrons;
```

**Our First Query*

Once the query is structured, the SELECT statement appears first, followed by the FROM statement in the next line. It is a best practice to conclude the query with a semicolon to signify its completion. Additionally, we capitalize keywords while keeping table and field names in lowercase.

```sql
SELECT name
FROM patrons;
```

The outcome of a query is referred to as the result set. It is essential to note that executing this query does not modify our database.

To select multiple fields, we can list various field names after the SELECT keyword, separated by commas.

```sql
SELECT card_num, name
FROM patrons;
```

To choose all fields, use an asterisk (*) instead of field names.

```sql
SELECT *
FROM patrons;
```

**Exercises:**

**SQL strengths**

Which of the below scenarios describes a situation in which using SQL would be useful?

        "Large amounts of data about many different but related areas of a business are housed in a relational database."

**Querying the books table**

You're ready to practice writing your first SQL queries using the SELECT and FROM keywords. Recall from the video that SELECT is used to choose the fields that will be included in the result set, while FROM is used to pick the table in which the fields are listed.

Feel free to explore books in the exercise. Let's zoom in on this table in the database schema to see the fields and data types it contains.

Your task in this exercise is to practice selecting fields from books.

**Instructions:**

- Use SQL to return a result set of all book titles included in the books table.

```sql
-- Return all titles from the books table
SELECT *
FROM books
```

- Select both the title and author fields from books.

```sql
-- Select title and author from the books table
SELECT title, author
FROM books;
```

- Select all fields from the books table

```sql
-- Select all fields from the books table
SELECT *
FROM books;
```

# Writing queries

**Personal notes:**

**Aliasing*

It can be beneficial to rename columns in our result set, either for clarity or brevity. We can achieve this using aliasing. For example, if we want to select the name and hiring year for each record in the employees' table, we could alias the name column as "first_name" in the query by adding the AS keyword to indicate an alias for "first_name" after selecting the name field:

```sql
SELECT name AS first_name, year_hired
FROM employees;
```

Aliasing applies only to the result of that specific query; the field name in the employees' table itself remains as "name" and is not altered.

**Selecting Distinct Records*

To obtain a list of unique years without repeated values, we can add the DISTINCT keyword before the field name in the SELECT statement:

```sql
SELECT DISTINCT year_hired
FROM employees;
```

**Distinct with Multiple Fields*

It is possible to return unique combinations of multiple field values by listing several fields after the DISTINCT keyword:

```sql
SELECT DISTINCT dept_id, year_hired
FROM employees;
```

**Views*

Let's discuss how to save SQL result sets. In SQL, a view refers to a table that is the result of a saved SELECT SQL statement. Views are considered virtual tables, meaning the data they contain is generally not stored in the database. Instead, it is the query code that is stored for future use. A benefit of this is that whenever the view is accessed, it automatically updates the query results to consider any updates in the underlying database.

To create a view, we add a line of code before the SELECT statement. CREATE VIEW, then the name we'd like for the new view, followed by the AS keyword to assign the query results to the new view name:

```sql
CREATE VIEW employee_hire_years AS
SELECT id, name, year_hired
FROM employees;
```

There is no result set when creating a view. Once the view is created, however, we can query it just like we would a regular table, selecting FROM with the name of the created view:

```sql
SELECT id, name
FROM employee_hire_years;
```

**Exercises:**

**Making queries DISTINCT**

You've learned that the DISTINCT keyword can be used to return unique values in a field. In this exercise, you'll use this understanding to find out more about the books table!

There are 350 books in the books table, representing all of the books that our local library has available for checkout. But how many different authors are represented in these 350 books? The answer is surely less than 350. For example, J.K. Rowling wrote all seven Harry Potter books, so if our library has all Harry Potter books, seven books will be written by J.K Rowling. There are likely many more repeat authors!

**Instructions:**

- Completed task after requesting a hint or solution
Write SQL code that returns a result set with just one column listing the unique authors in the books table.

```sql
-- Select unique authors from the books table
SELECT DISTINCT author
FROM books
```

- Update the code to return the unique author and genre combinations in the books table.

```sql
-- Select unique authors and genre combinations from the books table
SELECT DISTINCT author, genre
FROM books;
```

**Aliasing**

While the default column names in a SQL result set come from the fields they are created from, you've learned that aliasing can be used to rename these result set columns. This can be helpful for clarifying the intent or contents of the column.

Your task in this exercise is to incorporate an alias into one of the SQL queries that you worked with in the previous exercise!

**Instructions:**

- Add an alias to the SQL query to rename the author column to unique_author in the result set.

```sql
-- Alias author so that it becomes unique_author
SELECT DISTINCT author AS unique_author
FROM books;
```

**VIEWing your query**

You've worked hard to create the below SQL query:


    SELECT DISTINCT author AS unique_author
    FROM books;

What if you'd like to be able to refer to it later, or allow others to access and use the results? The best way to do this is by creating a view. Recall that a view is a virtual table: it's very similar to a real table, but rather than the data itself being stored, the query code is stored for later use.

**Instructions:**

- Add a single line of code that saves the results of the written query as a view called library_authors.

```sql
-- Save the results of this query as a view called library_authors
CREATE VIEW library_authors AS
SELECT DISTINCT author AS unique_author
FROM books;
```

- Check that the view was created by selecting all columns from library_authors.

```sql
-- Your code to create the view:
CREATE VIEW library_authors AS
SELECT DISTINCT author AS unique_author
FROM books;

-- Select all columns from library_authors
SELECT *
FROM library_authors;
```


# SQL flavors

**Personal notes:**

SQL has several versions or different types. Some are free, while others have customer support and are designed to complement major databases like Microsoft's SQL Server or Oracle Database, which are used by many companies. All types of SQL are used with table-based relational databases, and the vast majority of keywords are shared among them. All types of SQL must follow universal standards defined by the International Organization for Standardization (ISO) and the American National Standards Institute (ANSI).

**Two Popular SQL Flavors*

PostgreSQL is a free and open-source relational database system that was originally created at the University of California and was sponsored by the renowned Defense Advanced Research Projects Agency (DARPA) in the U.S. The name PostgreSQL is used to refer to both the database system itself and the SQL flavor used with it.

SQL Server is also a relational database system that comes in free and enterprise versions. It was created by Microsoft, making it well-suited to work with other Microsoft products. T-SQL is Microsoft's proprietary SQL type used with SQL Server databases.

**Comparing PostgreSQL and SQL Server*

Think of SQL types as dialects of the same language. Here's an example of a slight difference between SQL Server and PostgreSQL: when we want to limit the number of returned records, we use the LIMIT keyword in PostgreSQL. Here, we limit the number of selected employee names and IDs to only the first two records.

PostgreSQL:
```sql
SELECT id, name
FROM employees
LIMIT 2;
```

The exact same results are achieved in SQL Server using the TOP keyword instead of LIMIT:

SQL Server:
```sql
SELECT TOP(2) id, name
FROM employees;
```

**Exercises:**

**Limiting results**

Let's take a look at a few of the genres represented in our library's books.

Recall that limiting results is useful when testing code since result sets can have thousands of results! Queries are often written with a LIMIT of just a few records to test out code before selecting thousands of results from the database.

Let's practice with LIMIT!

**Instructions:**

- Using PostgreSQL, select the genre field from the books table; limit the number of results to 10.

```sql
-- Select the first 10 genres from books using PostgreSQL
SELECT genre
FROM books
LIMIT 10;
```

**Translating between flavors**

In the previous exercise, you wrote the following code using PostgreSQL:

    SELECT genre
    FROM books
    LIMIT 10;

The database in this course is a PostgreSQL database, so you won't be able to run SQL Server code in any of the exercises. What if you did want to update the above query to work with SQL Server, though? How would you do that?

        "Remove LIMIT statement and add TOP(10) after SELECT"


# Intermediate SQL

**Course description:**

SQL is the most popular language for turning raw data stored in a database into actionable insights. Using a database of films made around the world, this course covers:

✓ How to filter and compare data

✓ How to use aggregate functions to summarize data

✓ How to sort and group your data

✓ How to present your data cleanly using tools such as rounding and aliasing

Accompanied at every step with hands-on practice queries, this course teaches you everything you need to know to analyze data using your own SQL code today!

# Selecting Data

**Chapter description:**

In this first chapter, you’ll learn how to query a films database and select the data needed to answer questions about the movies and actors. You'll also understand how SQL code is executed and formatted.

# Querying a database

**Personal notes:**

While SQL can be used to create and modify databases, the focus of the course will be on querying databases. We will learn how to execute a query on a database using keywords that allow us to count and view all or a specific number of records. We'll also cover common SQL errors, style guidelines, and the order in which our code will be executed. We will be using PostgreSQL throughout.

We'll use a movie database with four tables: movies, reviews, people, and roles.

**COUNT()*

COUNT() can be used to count something in the tables. For example, to count the number of birthdates present in the people table, we'll use:
```sql
SELECT COUNT(birthdate) AS count_birthdates
FROM people;
```
If we want to count more than one field, we need to use COUNT multiple times. For example, to count the number of names and birthdates in the people table:
```sql
SELECT COUNT(name) AS count_names, COUNT(birthdate) AS count_birthdates
FROM people;
```
Using COUNT with a field name tells us how many values exist in a field. However, if we want to count the number of records in a table, we can use COUNT*; for example, this code provides the total number of records in the people table:
```sql
SELECT COUNT(*) AS total_records
FROM people;
```

**DISTINCT*

We can use the DISTINCT keyword to select all unique values from a field. For example, if we are interested in knowing which languages are represented in the films table, adding DISTINCT to our query will remove all duplicates:
```sql
SELECT DISTINCT language
FROM films;
```

Combining COUNT with DISTINCT is also common to count the number of unique values in a field. For example, this query counts the number of distinct birthdates in the people table:
```sql
SELECT COUNT(DISTINCT birthdate) AS count_distinct_birthdates
FROM people;
```

**Exercises:**

**Learning to COUNT()**

You saw how to use COUNT() in the video. Do you remember what it returns?

Here is a query counting film_id. Select the answer below that correctly describes what the query will return.

    SELECT COUNT(film_id) AS count_film_id
    FROM reviews;

Run the query in the console to test your theory!

        "The number of records containing a film_id."

**Practice with COUNT()**

As you've seen, COUNT(*) tells you how many records are in a table. However, if you want to count the number of non-missing values in a particular field, you can call COUNT() on just that field.

Let's get some practice with COUNT()! You can look at the data in the tables throughout these exercises by clicking on the table name in the console.

**Instructions:**

- Count the total number of records in the people table, aliasing the result as count_records.

```sql
-- Count the number of records in the people table
SELECT COUNT(id) AS count_records
FROM people;
```

- Count the number of records with a birthdate in the people table, aliasing the result as count_birthdate.

```sql
-- Count the number of birthdates in the people table
SELECT COUNT(birthdate) AS count_birthdate
FROM people; 
```

- Count the records for languages and countries in the films table; alias as count_languages and count_countries.

```sql
-- Count the records for languages and countries represented in the films table
SELECT COUNT(language) AS count_languages, COUNT(country) AS count_countries
FROM films;
```

**SELECT DISTINCT**

Often query results will include many duplicate values. You can use the DISTINCT keyword to select the unique values from a field.

This might be useful if, for example, you're interested in knowing which languages are represented in the films table. See if you can find out what countries are represented in this table with the following exercises.

**Instructions:**

- Return the unique countries represented in the films table using DISTINCT.

```sql
-- Return the unique countries from the films table
SELECT DISTINCT country 
FROM films;
```

- Return the number of unique countries represented in the films table, aliased as count_distinct_countries.

```sql
-- Count the distinct countries from the films table
SELECT COUNT(DISTINCT country) AS count_distinct_countries
FROM films;
```

# Query execution

**Personal notes:**

Unlike many programming languages, SQL code is not processed in the order it is written. The first line to be processed is the FROM statement. Before any data can be selected, the table from which the data will be selected needs to be indicated. Next is the SELECT statement. Finally, we can use the LIMIT keyword to limit the results to a specified number of records. For example, if we want to return only the first ten names from the people table:
```sql
SELECT name
FROM people
LIMIT 10;
```

Knowing the processing order is especially useful when debugging and creating aliases for fields and tables. Suppose we need to refer to an alias later in our code. In that case, this alias only makes sense to a processor when its declaration in the SELECT statement is processed before the alias reference is made elsewhere in the query.

**Debugging SQL*

Let's delve into SQL code debugging and how to read error messages. Some messages are extremely helpful, identifying and even suggesting a solution for the error.

**Exercises:**

**Order of execution**

SQL code is processed differently than other programming languages in that you need to let the processor know where to pull the data from before making selections.

It's essential to know your code's order of execution compared to the order it is written in to understand what results you'll get from your query and how to fix any errors that may come up.

        FROM
        SELECT
        LIMIT

**Debugging errors**

Debugging is an essential skill for all coders, and it comes from making many mistakes and learning from them.

In this exercise, you'll be given some buggy code that you'll need to fix.

**Instructions:**

- Debug and fix the SQL query provided.

```sql
-- Debug this code
SELECT certification
FROM films
LIMIT 5;
```

- Find the two errors in this code; the same error has been repeated twice.

```sql
-- Debug this code
SELECT film_id, imdb_score, num_votes
FROM reviews;
```

- Find the two bugs in this final query.

```sql
-- Debug this code
SELECT COUNT(birthdate) AS count_birthdays
FROM people;
```

# SQL style

**Personal notes:**

SQL code doesn't need to be organized for the processor to execute, but an organized code format is a universal standard to make the code more readable among different people worldwide.

Due to different formatting styles, it is helpful to follow an SQL style guide, such as Holywell's, which outlines best practices for indentation, capitalization, and naming conventions for tables, fields, and aliases: SQL Style Guide. Including a semicolon at the end of the query is considered a best practice for several reasons. First, some types of SQL require it, so it's a good habit to have. Also, the semicolon usage indicates its end, which is useful in a file containing multiple queries.

Adhering to SQL style guides allows for easier collaboration among peers. Having clean and readable code is highly valued in the community and is a professional setting that will make things easier for anyone wanting to understand or debug our queries.

**Exercises:**

**Formatting**

Readable code is highly valued in the coding community and professional settings. Without proper formatting, code and results can be difficult to interpret. You'll often be working with other people that need to understand your code or be able to explain your results, so having a solid formatting habit is essential.

In this exercise, you'll correct poorly written code to better adhere to SQL style standards.

**Instruction:**

- Adjust the sample code so that it is in line with standard practices.

```sql
-- Rewrite this query
SELECT person_id, role 
FROM roles 
LIMIT 10;
```

**Non-standard fields**

You may occasionally receive a dataset with poorly named fields. Ideally, you would fix these, but you can work around it with some added punctuation in this instance.

A sample query and schema have been provided; imagine you need to be able to run it with a non-standard field name. Select the multiple-choice answer that would correctly fill in the blank to return both a film's id and its number of Facebook likes for all reviews:

SELECT film_id, ___
FROM reviews;

        "facebook likes"

# Filtering Records

**Chapter description:**

Learn about how you can filter numerical and textual data with SQL. Filtering is an important use for this language. You’ll learn how to use new keywords and operators to help you narrow down your query to get results that meet your desired criteria and gain a better understanding of NULL values and how to handle them.

# Filtering numbers

**Personal notes:**

To filter, we need to use a new clause called WHERE, which allows us to focus only on the data relevant to our business questions.

**WHERE with Comparison Operators*

An example query where we filter to see only movies released after the year 1960 using the greater-than operator:
```sql
SELECT title
FROM films
WHERE release_year > 1960;
```

If we wanted to filter movies to see all releases EXCEPT those from the year 1960, we combine <> (not equal to), which is the default symbol in SQL that means "different from":
```sql
SELECT title
FROM films 
WHERE release_year <> 1960;
```

**Comparison Operators:*

">" Greater than or after;

"<" Less than or before;

"=" Equal to;

">=" Greater than or equal to;

"<=" Less than or equal to;

"<>" Not equal to.

**WHERE with Strings*

WHERE and the equals comparison operator can also be used with strings.
```sql
SELECT title
FROM films
WHERE country = 'Japan';
```

**Order of Execution*

Similar to LIMIT, this clause comes after the FROM statement when writing a query. If we use WHERE and LIMIT, the written order will be SELECT, FROM, WHERE, LIMIT.
```sql
SELECT item
FROM coats
WHERE color = 'green'
LIMIT 5;
```

**Exercises:**

**Filtering results**

The WHERE clause allows you to filter based on text and numeric values in a table using comparison operators.

What does the following query return?

SELECT title
FROM films
WHERE release_year > 2000;

        "Films released after the year 2000"

**Using WHERE with numbers**

Filtering with WHERE allows you to analyze your data better. You may have a dataset that includes a range of different movies, and you need to do a case study on the most notable films with the biggest budgets. In this case, you'll want to filter your data to a specific budget range.

Now it's your turn to use the WHERE clause to filter numeric values!

**Instructions:**

- Select the film_id and imdb_score from the reviews table and filter on scores higher than 7.0.

```sql
-- Select film_ids and imdb_score with an imdb_score over 7.0
SELECT film_id, imdb_score
FROM reviews
WHERE imdb_score > 7.0
```

- Select the film_id and facebook_likes of the first ten records with less than 1000 likes from the reviews table.

```sql
-- Select film_ids and facebook_likes for ten records with less than 1000 likes 
SELECT film_id, facebook_likes
FROM reviews
WHERE facebook_likes < 1000
LIMIT 10;
```

- Count how many records have a num_votes of at least 100,000; use the alias films_over_100K_votes.

```sql
-- Count the records with at least 100,000 votes
SELECT COUNT(*) AS films_over_100K_votes
FROM reviews
WHERE num_votes >= 100000;
```

**Using WHERE with text**

WHERE can also filter string values.

Imagine you are part of an organization that gives cinematography awards, and you have several international categories. Before you confirm an award for every language listed in your dataset, it may be worth seeing if there are enough films of a specific language to make it a fair competition. If there is only one movie or a significant skew, it may be worth considering a different way of giving international awards.

Let's try this out!

**Instructions:**

- Select and count the language field using the alias count_spanish.
- Apply a filter to select only Spanish from the language field.

```sql
-- Count the Spanish-language films
SELECT COUNT(language) as count_spanish
FROM films
WHERE language = 'Spanish'
```

# Multiple criteria

**Personal notes:**

Filtering with multiple criteria using the OR, AND, and BETWEEN operators.

**OR Operator*

OR is used when we want to filter by multiple criteria and only need to satisfy at least one condition.
Example using OR:
```sql
SELECT *
FROM coats 
WHERE colors = 'yellow' OR length = 'short';

SELECT title
FROM films
WHERE release_year = 1994 OR release_year = 2000;
```

**AND Operator*

If we want to satisfy all the criteria in our filter, we need to use AND with WHERE.
Example using AND:
```sql
SELECT *
FROM coats 
WHERE colors = 'yellow' AND length = 'short';

SELECT title
FROM films
WHERE release_year > 1994 AND release_year < 2000;
```

We can use AND and OR together. If a query has multiple filtering conditions, we need to put the individual clauses in parentheses to ensure the correct execution order; otherwise, we might not get the expected results.

**BETWEEN Operator*

Checking ranges is very common, and in SQL, the BETWEEN keyword provides a valuable shortcut for filtering values within a specified range.
Example using BETWEEN:
```sql
SELECT *
FROM coats 
WHERE buttons BETWEEN 1 AND 5;

SELECT title
FROM films
WHERE release_year 
	BETWEEN 1994 AND 2000;
```

**Exercises:**

**Using AND**

The following exercises combine AND and OR with the WHERE clause. Using these operators together strengthens your queries and analyses of data.

You will apply these new skills now on the films database.

**Instructions:**

- Select the title and release_year for all German-language films released before 2000.

```sql
-- Select the title and release_year for all German-language films released before 2000
SELECT title, release_year
FROM films
WHERE language = 'German' AND release_year < 2000;]
```

- Update the query from the previous step to show German-language films released after 2000 rather than before.

```sql
-- Update the query to see all German-language films released after 2000
SELECT title, release_year
FROM films
WHERE release_year > 2000
        AND language = 'German';
```

- Select all details for German-language films released after 2000 but before 2010 using only WHERE and AND.

```sql
-- Select all records for German-language films released after 2000 and before 2010
SELECT *
FROM films
WHERE release_year > 2000 AND release_year < 2010 AND language = 'German'
```

**Using OR**

This time you'll write a query to get the title and release_year of films released in 1990 or 1999, which were in English or Spanish and took in more than $2,000,000 gross.

It looks like a lot, but you can build the query up one step at a time to get comfortable with the underlying concept in each step. Let's go!

**Instructions:**

- Select the title and release_year for films released in 1990 or 1999 using only WHERE and OR.

```sql
-- Find the title and year of films from the 1990 or 1999
SELECT title, release_year
FROM films
WHERE release_year = 1990 OR release_year = 1999
```

- Filter the records to only include English or Spanish-language films.

```sql
SELECT title, release_year
FROM films
WHERE (release_year = 1990 OR release_year = 1999) AND 
        (language = 'English' OR language = 'Spanish');
-- Add a filter to see only English or Spanish-language films
```

- Finally, restrict the query to only return films worth more than $2,000,000 gross.

```sql
SELECT title, release_year
FROM films
WHERE (release_year = 1990 OR release_year = 1999)
        AND (language = 'English' OR language = 'Spanish')
-- Filter films with more than $2,000,000 gross
        AND (gross > 2000000);
```

**Using BETWEEN**

Let's use BETWEEN with AND on the films database to get the title and release_year of all Spanish-language films released between 1990 and 2000 (inclusive) with budgets over $100 million.

We have broken the problem into smaller steps so that you can build the query as you go along!

**Instructions:**

- Select the title and release_year of all films released between 1990 and 2000 (inclusive) using BETWEEN.

```sql
-- Select the title and release_year for films released between 1990 and 2000
SELECT title, release_year
FROM films
WHERE release_year
        BETWEEN 1990 AND 2000;
```

- Build on your previous query to select only films with a budget over $100 million.

```sql
SELECT title, release_year
FROM films
WHERE release_year BETWEEN 1990 AND 2000 
-- Narrow down your query to films with budgets > $100 million
        AND budget > 100000000;
```

- Now, restrict the query to only return Spanish-language films.

```sql
SELECT title, release_year
FROM films
WHERE release_year BETWEEN 1990 AND 2000
        AND budget > 100000000
-- Restrict the query to only Spanish-language films
        AND language = 'Spanish';
```

- Finally, amend the query to include all Spanish-language or French-language films with the same criteria.

```sql
SELECT title, release_year
FROM films
WHERE release_year BETWEEN 1990 AND 2000
        AND budget > 100000000
-- Amend the query to include Spanish or French-language films
        AND (language = 'Spanish' OR language = 'French');
```

# Filtering text

**Personal notes:**

Often, we'll want to search for a pattern rather than a specific text sequence in the real world. We'll be introducing three more SQL keywords into our vocabulary to help us achieve this: LIKE, NOT LIKE, and IN.

**LIKE*

In SQL, we can use the LIKE operator with a WHERE clause to search for a pattern in a field. We use a wildcard as a placeholder for some other values to do this. There are two wildcards in LIKE, the percentage sign (%) and the underscore (_):
- `%` - will match zero, one, or many characters in the text.
  ```sql
  SELECT name
  FROM people
  WHERE name LIKE 'Ade%';
  ```
- `_` - will match a single character.
  ```sql
  SELECT name
  FROM people
  WHERE name LIKE 'Ev_';
  ```

**NOT LIKE*

We can also use the NOT LIKE operator to find records that do not match the specified pattern. For example, in this query, we are finding records of people who do not have "A." as part of their first name:
```sql
SELECT name
FROM people
WHERE name NOT LIKE 'A.%';
```
*It's important to note that this operation is case-sensitive, so we need to be mindful of what we are querying.

**Wildcard Position*

We can find values that start, end, or contain characters at any position, as well as find records of a certain length. For example, this code will find all people whose name ends with "r":
```sql
SELECT name
FROM people
WHERE name LIKE '%r';
```
This code, on the other hand, will find records where the third character is "t":
```sql
SELECT name
FROM people
WHERE name LIKE '__t%';
```

**WHERE, IN*

What if we want to filter based on many conditions or within a range of numbers? The IN operator allows us to specify multiple values in a WHERE clause, making it easier and quicker to define numerous OR conditions.
```sql
SELECT title
FROM films 
WHERE release_year IN (1920, 1930, 1940);

SELECT title
FROM films
WHERE country IN ('Germany', 'France');
```

**Exercises:**

**LIKE and NOT LIKE**

The LIKE and NOT LIKE operators can be used to find records that either match or do not match a specified pattern, respectively. They can be coupled with the wildcards % and _. The % will match zero or many characters, and _ will match a single character.

This is useful when you want to filter text, but not to an exact word.

Do the following exercises to gain some practice with these keywords

**Instructions:**

- Select the names of all people whose names begin with 'B'.

```sql
-- Select the names that start with B
SELECT name
FROM people
WHERE name LIKE 'B%';
```

- Select the names of people whose names have 'r' as the second letter.

```sql
SELECT name
FROM people
-- Select the names that have r as the second letter
WHERE name LIKE '_r%'
```

- Select the names of people whose names don't start with 'A'.

```sql
SELECT name
FROM people
-- Select names that don't start with A
WHERE name NOT LIKE 'A%'
```

**WHERE IN**

You now know you can query multiple conditions using the IN operator and a set of parentheses. It is a valuable piece of code that helps us keep our queries clean and concise.

Try using the IN operator yourself!

**Instructions:**

- Select the title and release_year of all films released in 1990 or 2000 that were longer than two hours.

```sql
-- Find the title and release_year for all films over two hours in length released in 1990 and 2000
SELECT title, release_year
FROM films
WHERE release_year IN (1990, 2000)
        AND duration > 120
```

- Select the title and language of all films in English, Spanish, or French using IN.

```sql
-- Find the title and language of all films in English, Spanish, and French
SELECT title, language
FROM films
WHERE language IN ('English', 'Spanish', 'French')
```

- Select the title, certification and language of all films certified NC-17 or R that are in English, Italian, or Greek.

```sql
-- Find the title, certification, and language all films certified NC-17 or R that are in English, Italian, or Greek
SELECT title, certification, language
FROM films
WHERE certification IN ('NC-17', 'R') AND language IN ('English', 'Italian','Greek')
```

**Combining filtering and selecting**

Time for a little challenge. So far, your SQL vocabulary from this course includes COUNT(), DISTINCT, LIMIT, WHERE, OR, AND, BETWEEN, LIKE, NOT LIKE, and IN. In this exercise, you will try to use some of these together. Writing more complex queries will be standard for you as you become a qualified SQL programmer.

As this query will be a little more complicated than what you've seen so far, we've included a bit of code to get you started. You will be using DISTINCT here too because, surprise, there are two movies named 'Hamlet' in this dataset!

Follow the instructions to find out what 90's films we have in our dataset that would be suitable for English-speaking teens.

**Instructions:**

- Count the unique titles from the films database and use the alias provided.

- Filter to include only movies with a release_year from 1990 to 1999, inclusive.

- Add another filter narrowing your query down to English-language films.

- Add a final filter to select only films with 'G', 'PG', 'PG-13' certifications.

```sql
SELECT COUNT(DISTINCT title) AS nineties_english_films_for_teens
FROM films
WHERE release_year BETWEEN 1990 AND 1999
AND language = 'English'
AND certification IN('G', 'PG', 'PG-13');
```

# NULL values

**Personal notes:**

The COUNT keyword can be used to include or exclude non-null values depending on whether or not we use the asterisk in our query:
- COUNT(field_name) - Includes only non-null values;
- COUNT(*) - Includes null values.

In SQL, NULL represents a missing or unknown value. In the real world, our databases are likely to have empty fields due to human error or because the information is not available or unknown. Knowing how to handle these fields is essential, as they can affect any analysis we perform.

**IS NULL*

A quick way to see how many data are missing is to use IS NULL with the WHERE clause. Here's an example where we check which names do not have a recorded birthdate in our table:
```sql
SELECT name
FROM people
WHERE birthdate IS NULL;
```

**IS NOT NULL*

Here's an example of counting the missing birthdates in the people table:
```sql
SELECT COUNT(*) AS no_birthdates
FROM people
WHERE birthdate IS NULL;
```

Sometimes, we will want to filter out null values to get only results that are not null. To do this, we can use the IS NOT NULL operator. For example, this query provides the count of all people whose birthdates are not missing in the people table, giving us a new count:
```sql
SELECT COUNT(name) AS count_birthdates
FROM people
WHERE birthdate IS NOT NULL;
```

**COUNT() vs IS NOT NULL*

There is no difference in which one to use; both will count non-missing values.
Example using COUNT():
```sql
SELECT
  COUNT(certification) AS count_certification
FROM films;
```
Example using IS NOT NULL:
```sql
SELECT
  COUNT(certification) AS count_certification
FROM films
WHERE certification IS NOT NULL;
```

**Exercises:**

**What does NULL mean?**

I hope you were paying attention in the video. Pop quiz: What does NULL represent?

        "A missing value"

**Practice with NULLs**

Well done. Now that you know what NULL means and what it's used for, it's time for some more practice!

Let's explore the films table again to better understand what data you have.

**Instructions:**

- Select the title of every film that doesn't have a budget associated with it and use the alias no_budget_info.

```sql
-- List all film titles with missing budgets
SELECT title AS no_budget_info
FROM films
WHERE budget IS NULL;
```

- Count the number of films with a language associated with them and use the alias count_language_known.

```sql
-- Count the number of films we have language data for
SELECT COUNT(language) AS count_language_known
FROM films
```

# Aggregate Functions

**Chapter description:**

SQL allows you to zoom in and out to better understand an entire dataset, its subsets, and its individual records. You'll learn to summarize data using aggregate functions and perform basic arithmetic calculations inside queries to gain insights into what makes a successful film.

# Summarizing data

**Personal notes:**

One way to summarize data is by using SQL's aggregate functions. An aggregate function performs a calculation on multiple values and returns a single value. We've already seen the COUNT function, and now we'll explore functions used to calculate average, sum, minimum, and maximum for a specified field.

**Aggregate Functions:*
- AVG() - To find the average;

- SUM() - To perform the sum;

- MIN() - To find the minimum value;

- MAX() - To find the maximum value;

- COUNT() - Provides a total of non-null or non-missing records in a field.

These aggregate functions are used after the SELECT, just like we use COUNT(). The functions are used on the field (column) and not the records (rows).

**Non-Numerical Data:*

While these functions might seem mathematical, we can use many of them with both numerical and non-numerical fields. The average (AVG) and sum (SUM) are the two functions that we can only use on numerical fields since they involve arithmetic. We can use COUNT, MIN, and MAX with non-numerical fields. MIN and MAX will give the record that is figuratively the lowest or highest. The lowest might mean the letter A when dealing with strings or the oldest date when dealing with dates.

**Aliasing When Summarizing:*

Note how all the results in the query automatically updated the field name to the aggregate function used. It's a best practice to use an alias when summarizing data so that our results are clear to anyone reading our code.
```sql
SELECT MIN(country) AS min_country
FROM films;
```

**Exercises:**

**Practice with aggregate functions**

Now let's try extracting summary information from a table using these new aggregate functions. Summarizing is helpful in real life when extracting top-line details from your dataset. Perhaps you'd like to know how old the oldest film in the films table is, what the most expensive film is, or how many films you have listed.

Now it's your turn to get more insights about the films table!

**Instructions:**

- Use the SUM() function to calculate the total duration of all films and alias with total_duration.

```sql
-- Query the sum of film durations
SELECT SUM(duration) AS total_duration
FROM films;
```

- Calculate the average duration of all films and alias with average_duration.

```sql
-- Calculate the average duration of all films
SELECT AVG(duration) AS average_duration
FROM films;
```

- Find the most recent release_year in the films table, aliasing as latest_year.

```sql
-- Find the latest release_year
SELECT MAX(release_year) AS latest_year
FROM films;
```

- Find the duration of the shortest film and use the alias shortest_film.

```sql
-- Find the duration of the shortest film
SELECT MIN(duration) AS shortest_film
FROM films;
```

# Summarizing subsets

**Personal notes:**

**Using WHERE with Aggregate Functions:*

We can combine aggregate functions with the WHERE clause to gain more insights from our data. This is because the WHERE clause is executed before the SELECT statement.
```sql
SELECT AVG(budget) AS avg_budget
FROM films
WHERE release_year >= 2010;
```

**ROUND():*

In SQL, we can use ROUND() to round our number to a specified decimal place. There are two parameters for ROUND(): the number we want to round and the decimal place we want to round to. It can only be used with numerical fields.
```sql
-- Example: Recalculating the same average budget seen before using ROUND and specifying we want to round to two decimal places because we're dealing with currency:
SELECT ROUND(AVG(budget), 2) AS avg_budget
FROM films
WHERE release_year >= 2010;
```

**ROUND() to a Whole Number:*

The second parameter in our ROUND() function is optional, so we can omit it if we want to round to a whole number. Omitting the number or declaring it as 0 results in the same outcome.

**ROUND() using a Negative Parameter:*

We could also pass a negative number as the second parameter and still get a result. For example, here, the function is rounding to the left of the decimal point instead of the right.
```sql
SELECT ROUND(AVG(budget), -5) AS avg_budget
FROM films
WHERE release_year >= 2010;
```

**Exercises:**

**Combining aggregate functions with WHERE**

When combining aggregate functions with WHERE, you get a powerful tool that allows you to get more granular with your insights, for example, to get the total budget of movies made from the year 2010 onwards.

This combination is useful when you only want to summarize a subset of your data. In your film-industry role, as an example, you may like to summarize each certification category to compare how they each perform or if one certification has a higher average budget than another.

Let's see what insights you can gain about the financials in the dataset.

**Instructions:**

- Use SUM() to calculate the total gross for all films made in the year 2000 or later, and use the alias total_gross.

```sql
-- Calculate the sum of gross from the year 2000 or later
SELECT SUM(gross) AS total_gross
FROM films
WHERE release_year >= 2000;
```

- Calculate the average amount grossed by all films whose titles start with the letter 'A' and alias with avg_gross_A.

```sql
-- Calculate the average gross of films that start with A
SELECT AVG(gross) AS avg_gross_A
FROM films
WHERE title LIKE 'A%';
```

- Calculate the lowest gross film in 1994 and use the alias lowest_gross.
```sql
-- Calculate the lowest gross film in 1994
SELECT MIN(gross) AS lowest_gross
FROM films
WHERE release_year = 1994
```

- Calculate the highest gross film between 2000 and 2012, inclusive, and use the alias highest_gross.

```sql
-- Calculate the highest gross film released between 2000-2012
SELECT MAX(gross) AS highest_gross
FROM films
WHERE release_year between 2000 AND 2012;
```

**Using ROUND()**

Aggregate functions work great with numerical values; however, these results can sometimes get unwieldy when dealing with long decimal values. Luckily, SQL provides you with the ROUND() function to tame these long decimals.

If asked to give the average budget of your films, ten decimal places is not necessary. Instead, you can round to two decimal places to create results that make more sense for currency.

Now you try!

**Instructions:**

- Calculate the average facebook_likes to one decimal place and assign to the alias, avg_facebook_likes.

```sql
-- Round the average number of facebook_likes to one decimal place
SELECT ROUND(AVG(facebook_likes), 1) AS avg_facebook_likes
FROM reviews;
```

**ROUND() with a negative parameter**

A useful thing you can do with ROUND() is have a negative number as the decimal place parameter. This can come in handy if your manager only needs to know the average number of facebook_likes to the hundreds since granularity below one hundred likes won't impact decision making.

Social media plays a significant role in determining success. If a movie trailer is posted and barely gets any likes, the movie itself may not be successful. Remember how 2020's "Sonic the Hedgehog" movie got a revamp after the public saw the trailer?

Let's apply this to other parts of the dataset and see what the benchmark is for movie budgets so, in the future, it's clear whether the film is above or below budget.

**Instructions:**

- Calculate the average budget from the films table, aliased as avg_budget_thousands, and round to the nearest thousand.

```sql
-- Calculate the average budget rounded to the thousands
SELECT ROUND(AVG(budget), -3) AS avg_budget_thousands
FROM films;
```


# Aliasing and arithmetic

**Personal notes:**

We can perform basic arithmetic with symbols like plus, minus, multiplication, and division (+, -, *, /). Using parentheses with arithmetic indicates to the processor when the calculation needs to be executed. Some basic examples of how we can use arithmetic in SQL:
```sql
SELECT (4 + 3);
SELECT (4 - 3);
SELECT (4 * 3);
SELECT (4 / 3);
```
One needs to be careful with the division example. Similar to other programming languages, SQL assumes that we want to get an integer as a result if we divide an integer by another integer. For a correct division result, we can add decimals to our numbers. For example:
```sql
SELECT (4.0 / 3.0);
```
The main difference is that aggregate functions like SUM perform their operations on fields vertically, while arithmetic functions sum records horizontally.

We will always need to use an alias when summarizing data with both aggregate and arithmetic functions. For example:
```sql
SELECT MAX(budget) AS max_budget,
		MAX(duration) AS max_duration
FROM films;
```
*Aliases defined in the SELECT keyword cannot be used in the WHERE keyword due to the order of execution, causing an error when trying to run the code. It's important to remember the order of execution.

**Exercises:**

**Using arithmetic**

SQL arithmetic comes in handy when your table is missing a metric you want to review. Suppose you have some data on movie ticket sales, but the table only has fields for ticket price and discount. In that case, you could combine these by subtracting the discount from the ticket price to get the amount the film-goer paid.

You have seen that SQL can act strangely when dividing integers. What is the result if you divide a discount of two dollars by the paid_price of ten dollars to get the discount percentage?

        "0"

**Aliasing with functions**

Aliasing can be a lifesaver, especially as we start to do more complex SQL queries with multiple criteria. Aliases help you keep your code clean and readable. For example, if you want to find the MAX() value of several fields without aliasing, you'll end up with the result with several columns called max and no idea which is which. You can fix this with aliasing.

Now, it's over to you to clean up the following queries.

**Instructions:**

- Select the title and duration in hours for all films and alias as duration_hours; since the current durations are in minutes, you'll need to divide duration by 60.0.

```sql
-- Calculate the title and duration_hours from films
SELECT title, 
        (duration / 60.0) as duration_hours
FROM films;
```

- Calculate the percentage of people who are no longer alive and alias the result as percentage_dead.

```sql
-- Calculate the percentage of people who are no longer alive
SELECT COUNT(deathdate) * 100.0 / COUNT(*) AS percentage_dead
FROM people;
```

- Find how many decades (period of ten years) the films table covers by using MIN() and MAX(); alias as number_of_decades.

```sql
-- Find the number of decades in the films table
SELECT (MAX(release_year) - MIN(release_year)) / 10.0 AS number_of_decades
FROM films;
```

**Rounding results**

You found some valuable insights in the previous exercise, but many of the results were inconveniently long. We forgot to round! We won't make you redo them all; however, you'll update the worst offender in this exercise.

**Instructions:**

- Update the query by adding ROUND() around the calculation and round to two decimal places.

```sql
-- Round duration_hours to two decimal places
SELECT title, ROUND(duration / 60.0, 2) AS duration_hours
FROM films;
```

# Sorting and Grouping

**Chapter description:**

This final chapter teaches you how to sort and group data. These skills will take your analyses to a new level by helping you uncover critical business insights and identify trends and performance. You'll get hands-on experience to determine which films performed the best and how movie durations and budgets changed over time.

# Sorting results

**Personal notes:**

To gain more insights from our data, we can sort and group our results to put our data in a specific order.

**ORDER BY*

In SQL, the ORDER BY keyword is used to sort the results by one or more fields. When used alone, it is written after the FROM statement. ORDER BY will sort in ascending order by default.
```sql
SELECT title, budget
FROM films
ORDER BY budget; 
```
Adding the ASC keyword to our query to clarify that we are sorting in ascending order. We can use DESC to sort the results in descending order.
```sql
SELECT title, budget
FROM films
ORDER BY budget DESC;
```
We can add a WHERE clause before ORDER BY to filter the budget field only for non-null values and improve our results.
```sql
SELECT title, budget
FROM films
WHERE budget IS NOT NULL
ORDER BY budget DESC;
```
Note that we don't need to select the field we are sorting. For example, here's a query where we sort by release year and only look at the title.
```sql
SELECT title
FROM films
ORDER BY release_year; 
```
However, it's a good idea to include the field we are sorting in the SELECT statement for clarity.

**ORDER BY Multiple Fields*

ORDER BY can also be used to sort by multiple fields. It will sort by the first specified field and then by the next one, and so on. To specify multiple fields, we separate the field names with a comma. The second field we sort by can be thought of as a tiebreaker when the first field is not decisive in determining the order.
```sql
SELECT title, wins
FROM best_movies
ORDER BY wins DESC;
```
We can break this tie by adding a second sorting field to see which movie has the most wins and the highest IMDb score.
```sql
SELECT title, wins, imdb_score
FROM best_movies
ORDER BY wins DESC, imdb_score DESC;
```
We can also select a different order for each field we are sorting:
```sql
SELECT birthdate, name
FROM people
ORDER BY birthdate, name DESC; 
```

**Order of Execution:*
The FROM statement is executed first, followed by WHERE, then SELECT, ORDER BY, and finally, LIMIT.

**Exercises:**

**Sorting text**

SQL provides you with the ORDER BY keyword to sort one or more fields from your data. It can do this multi-directionally and helps make results easy to interpret.

How does ORDER BY sort a column of text values by default?

        "Alphabetically (A-Z)"

**Sorting single fields**

Now that you understand how ORDER BY works, you'll put it into practice. In this exercise, you'll work on sorting single fields only. This can be helpful to extract quick insights such as the top-grossing or top-scoring film.

The following exercises will help you gain further insights into the film database.

**Instructions:**

-Select the name of each person in the people table, sorted alphabetically.

```sql
-- Select name from people and sort alphabetically
SELECT name
FROM people
ORDER BY name;
```

- Select the title and duration for every film, from longest duration to shortest.

```sql
-- Select the title and duration from longest to shortest film
SELECT title, duration
FROM films
ORDER BY duration DESC;
```

**Sorting multiple fields**

ORDER BY can also be used to sort on multiple fields. It will sort by the first field specified, then sort by the next, and so on. As an example, you may want to sort the people data by age and keep the names in alphabetical order.

Try using ORDER BY to sort multiple columns.

**Instructions:**

- Select the release_year, duration, and title of films ordered by their release year and duration, in that order.

```sql
-- Select the release year, duration, and title sorted by release year and duration
SELECT release_year, duration, title
FROM films
ORDER BY release_year, duration;
```

- Select the certification, release_year, and title from films ordered first by certification (alphabetically) and second by release year, starting with the most recent year.

```sql
-- Select the certification, release year, and title sorted by certification and release year
SELECT certification, release_year, title
FROM films
ORDER BY certification, release_year DESC;
```

# Grouping data

**Personal notes:**

Often, we need to summarize data from a specific group of results.

**GROUP BY Single Fields*

SQL allows us to group with the GROUP BY clause. It is commonly used with aggregate functions to provide summary statistics.
```sql
SELECT certification, COUNT(title) AS title_count
FROM films
GROUP BY certification;
```
SQL will return an error if we try to SELECT a field that is not in our GROUP BY clause. We need to fix this by adding an aggregate function around the title.

**GROUP BY Multiple Fields*

We can use GROUP BY on multiple fields similar to ORDER BY. The query here selects and groups by certification and language while aggregating the title count:
```sql
SELECT certification, language, COUNT(title) AS title_count
FROM films
GROUP BY certification, language; 
```

**GROUP BY with ORDER BY*

We can combine GROUP BY with ORDER BY to group our results, perform a calculation, and then sort our results. For example, we can refine one of our previous queries by sorting the results by the title count in descending order:
```sql
SELECT
	certification,
	COUNT(title) AS title_count
FROM films
GROUP BY certification
ORDER BY title_count DESC;
```
ORDER BY is always written after GROUP BY, and note that we can reference the alias in the query.

**Order of Execution:*

FROM - SELECT - GROUP BY - ORDER BY.

**Exercises:**

**GROUP BY single fields**

GROUP BY is a SQL keyword that allows you to group and summarize results with the additional use of aggregate functions. For example, films can be grouped by the certification and language before counting the film titles in each group. This allows you to see how many films had a particular certification and language grouping.

In the following steps, you'll summarize other groups of films to learn more about the films in your database.

**Instructions:**

- Select the release_year and count of films released in each year aliased as film_count.

```sql
-- Find the release_year and film_count of each year
SELECT release_year, COUNT(films) AS film_count
FROM films
GROUP BY release_year;

```

- Select the release_year and average duration aliased as avg_duration of all films, grouped by release_year.

```sql
-- Find the release_year and average duration of films for each year
SELECT release_year, AVG(duration) AS avg_duration
FROM films
GROUP BY release_year;
```

**GROUP BY multiple fields**

GROUP BY becomes more powerful when used across multiple fields or combined with ORDER BY and LIMIT.

Perhaps you're interested in learning about budget changes throughout the years in individual countries. You'll use grouping in this exercise to look at the maximum budget for each country in each year there is data available.

**Instruction:**

- Select the release_year, country, and the maximum budget aliased as max_budget for each year and each country; sort your results by release_year and country.

```sql
-- Find the release_year, country, and max_budget, then group and order by release_year and country
SELECT release_year, country, MAX(budget) AS max_budget
FROM films
GROUP BY release_year, country;
```

**Answering business questions**

In the real world, every SQL query starts with a business question. Then it is up to you to decide how to write the query that answers the question. Let's try this out.

Which release_year had the most language diversity?

Take your time to translate this question into code. We'll get you started then it's up to you to test your queries in the console.

"Most language diversity" can be interpreted as COUNT(DISTINCT ___). Now over to you.

        "2006"

# Filtering grouped data

**Personal notes:**

In SQL, we cannot filter aggregate functions with WHERE clauses. Groups have their own special filtering keyword: HAVING. The reason why groups have their own keyword for filtering comes down to the order of execution. In the lesson example, the order is FROM, WHERE, GROUP BY, HAVING, SELECT, ORDER BY, and LIMIT.

**HAVING vs WHERE*
WHERE filters individual records, while HAVING filters grouped records.

**Exercises:**

**Filter with HAVING***

Your final keyword is HAVING. It works similarly to WHERE in that it is a filtering clause, with the difference that HAVING filters grouped data.

Filtering grouped data can be especially handy when working with a large dataset. When working with thousands or even millions of rows, HAVING will allow you to filter for just the group of data you want, such as films over two hours in length!

Practice using HAVING to find out which countries (or country) have the most varied film certifications.

**Instructions:**

- Select country from the films table, and get the distinct count of certification aliased as certification_count.

- Group the results by country.

- Filter the unique count of certifications to only results greater than 10.

```sql
SELECT country, COUNT(DISTINCT certification) AS certification_count
FROM films
GROUP BY country
HAVING COUNT(DISTINCT certification) > 10;
```

**HAVING and sorting**

Filtering and sorting go hand in hand and gives you greater interpretability by ordering our results.

Let's see this magic at work by writing a query showing what countries have the highest average film budgets.

**Instructions:**

- Select the country and the average budget as average_budget, rounded to two decimal, from films.

- Group the results by country.

- Filter the results to countries with an average budget of more than one billion (1000000000).

- Sort by descending order of the average_budget.

```sql
SELECT country, ROUND(AVG(budget),2) AS average_budget
FROM films
GROUP BY country
HAVING AVG(budget) > 1000000000
ORDER BY average_budget DESC;
```

**All together now**

It's time to use much of what you've learned in one query! This is good preparation for using SQL in the real world where you'll often be asked to write more complex queries since some of the basic queries can be answered by playing around in spreadsheet applications.

In this exercise, you'll write a query that returns the average budget and gross earnings for films each year after 1990 if the average budget is greater than 60 million.

This will be a big query, but you can handle it!

**Instructions:**

- Select the release_year for each film in the films table, filter for records released after 1990, and group by release_year.

```sql
-- Select the release_year for films released after 1990 grouped by year
SELECT release_year 
FROM films
WHERE release_year > 1990
GROUP BY release_year;
```

- Modify the query to include the average budget aliased as avg_budget and average gross aliased as avg_gross for the results we have so far.

```sql
-- Modify the query to also list the average budget and average gross
SELECT release_year, AVG(budget) AS avg_budget, AVG(gross) AS avg_gross
FROM films
WHERE release_year > 1990
GROUP BY release_year;
```

- Modify the query once more so that only years with an average budget of greater than 60 million are included.

```sql
SELECT release_year, AVG(budget) AS avg_budget, AVG(gross) AS avg_gross
FROM films
WHERE release_year > 1990
GROUP BY release_year
-- Modify the query to see only years with an avg_budget of more than 60 million
HAVING AVG(budget) > 60000000;
```

- Finally, order the results from the highest average gross and limit to one.

```sql
SELECT release_year, AVG(budget) AS avg_budget, AVG(gross) AS avg_gross
FROM films
WHERE release_year > 1990
GROUP BY release_year
HAVING AVG(budget) > 60000000
-- Order the results from highest to lowest average gross and limit to one
ORDER BY avg_gross DESC
LIMIT 1;
```

# Joining Data in SQL

**Course description:**

Joining data is an essential skill which enables us to draw information from separate tables together into a single, meaningful set of results. Learn to supercharge your queries using table joins and relational set theory in this course on joining data.

In this course, you’ll learn how to:

✓ Work with more than one table in SQL

✓ Use inner joins, outer joins and cross joins

✓ Leverage set theory, including unions, intersect, and except clauses

✓ Create nested queries

Every step is accompanied by exercises and opportunities to apply the theory and grow your confidence in SQL.

# Introducing Inner Joins

**Chapter description:**

In this chapter, you’ll be introduced to the concept of joining tables and will explore all the ways you can enrich your queries using joins—beginning with inner joins.

# The ins and outs of INNER JOIN

**Personal notes:**

Joining data is an essential skill that allows us to bring information from separate tables into a single, meaningful result set. A key is a single column or group of columns that uniquely identifies records in a table. With SQL joins, we can join on a key column or any other column.

The INNER JOIN shown in the lesson looks for records in both tables with the same values in the key column "id." It's common to start building the query with the join first and selecting the fields later. After FROM, we list the left table, followed by the INNER JOIN keyword and the right table. Then, we specify the field to match the tables, using the ON keyword. Finally, we add SELECT at the beginning of the query and choose the fields we want to return.

```sql
SELECT prime_ministers.country, prime_ministers.continent, prime_minister, president
FROM prime_ministers
INNER JOIN presidents
ON prime_ministers.country = presidents.country;
```

*When selecting columns that exist in both tables, such as "country" and "continent," the format `table.column_name` must be used to avoid an SQL error.

**Aliasing Tables*

In our INNER JOIN, we had to type "president" and "prime_minister" multiple times. Fortunately, we can alias table names using the same AS keyword used to alias column names. For example, we use the aliases p1 and p2 in our SELECT and ON clauses to shorten our query.

```sql
SELECT p1.country, p1.continent, prime_minister, president
FROM prime_ministers AS p1
INNER JOIN presidents AS p2
ON p1.country = p2.country;
```

**Using USING*

When joining on two identical column names, we can employ the USING command followed by the name of the shared column in parentheses. For example, since the join field is named "country" in both tables, we can use USING.

```sql
SELECT p1.country, p1.continent, prime_minister, president
FROM prime_ministers AS p1
INNER JOIN presidents AS p2
USING(country);
```

**Exercises:**

**Your first join**

Throughout this course, you'll be working with the countries database, which contains information about the most populous world cities in the world, along with country-level economic, population, and geographic data. The database also contains information on languages spoken in each country.

You can see the different tables in this database to get a sense of what they contain by clicking on the corresponding tabs. Click through them and familiarize yourself with the fields that seem to be shared across tables before you continue with the course.

In this exercise, you'll use the cities and countries tables to build your first inner join. You'll start off by selecting all columns in step 1, performing your join in step 2, and then refining your join to choose specific columns in step 3.

**Instructions:**

- Begin by selecting all columns from the cities table, using the SQL shortcut that selects all.

```sql
-- Select all columns from cities
SELECT *
FROM cities;
```

- Perform an inner join with the cities table on the left and the countries table on the right; do not alias tables here or in the next step.

- Identify the relevant column names to join ON by inspecting the cities and countries tabs in the console.

```sql
SELECT * 
FROM cities
INNER JOIN countries
on cities.country_code = countries.code
```

- Complete the SELECT statement to keep only the name of the city, the name of the country, and the region the country is located in (in the order specified).

- Alias the name of the city AS city and the name of the country AS country.

```sql
-- Select name fields (with alias) and region 
SELECT cities.name AS city, countries.name AS country, region
FROM cities 
INNER JOIN countries 
ON cities.country_code = countries.code;
```

**Joining with aliased tables**

Recall from the video that instead of writing full table names in queries, you can use table aliasing as a shortcut. The alias can be used in other parts of your query, such as the SELECT statement!

You also learned that when you SELECT fields, a field can be ambiguous. For example, imagine two tables, apples and oranges, both containing a column called color. You need to use the syntax apples.color or oranges.color in your SELECT statement to point SQL to the correct table. Without this, you would get the following error:

  column reference "color" is ambiguous

In this exercise, you'll practice joining with aliased tables. You'll use data from both the countries and economies tables to examine the inflation rate in 2010 and 2015.

When writing joins, many SQL users prefer to write the SELECT statement after writing the join code, in case the SELECT statement requires using table aliases.

**Instructions:**

- Start with your inner join in line 5; join the tables countries AS c (left) with economies (right), aliasing economies AS e.

- Next, use code as your joining field in line 7; do not use the USING command here.

- Lastly, select the following columns in order in line 2: code from the countries table (aliased as country_code), name, year, and inflation_rate.

```sql
-- Select fields with aliases
SELECT c.code AS country_code, name, year, inflation_rate
FROM countries AS c
-- Join to economies (alias e)
INNER JOIN economies AS e
-- Match on code field using table aliases
ON c.code = e.code;
```

**USING in action**

In the previous exercises, you performed your joins using the ON keyword. Recall that when both the field names being joined on are the same, you can take advantage of the USING clause.

You'll now explore the languages table from our database. Which languages are official languages, and which ones are unofficial?

You'll employ USING to simplify your query as you explore this question.

**Instructions:**

- Use the country code field to complete the INNER JOIN with USING; do not change any alias names.

```sql
SELECT c.name AS country, l.name AS language, official
FROM countries AS c
INNER JOIN languages AS l
-- Match using the code column
USING(code);
```

# Defining relationships

**Personal notes:**

**One-to-Many Relationships*

The first type of relationship we'll discuss is a one-to-many relationship. This is the most common type of relationship, where a single entity can be associated with multiple entities. For example, a university database might have a "Department" table (one) related to a "Professor" table (many) since one department can have multiple professors.

**One-to-One Relationships*

One-to-one relationships imply unique pairs between entities and are, therefore, less common. An example of such a relationship is a common premise in forensic science, where no two fingerprints are identical, so a specific fingerprint can only be generated by one person, one fingerprint for one finger.

**Many-to-Many Relationships*

Many-to-many relationships involve one entry being linked to several other entries, creating a web of interconnected relationships. This type of relationship often requires an intermediary table, known as a junction or associative table, to manage the connections between entities. For example, in a database for a bookstore, a "Book" table might be related to an "Author" table in a many-to-many relationship, as one book can have multiple authors, and one author can contribute to multiple books.

Understanding the nature of these relationships is crucial for designing a well-structured relational database, as it influences how tables are organized, keys are defined, and data integrity is maintained.

**Exercises:**

**Relationships in our database**

Now that you know more about the different types of relationships that can exist between tables, it's time to examine a few relationships in the countries database!

To answer questions about table relationships, you can explore the tables displayed as tabs in your console.

**Instructions:**

- Question: What best describes the relationship between code in the countries table and country_code in the cities table?

        "This is a one-to-many relationship."

- Question: Which of these options best describes the relationship between the countries table and the languages table?

        "This is a many-to-many relationship."

**Inspecting a relationship**

You've just identified that the countries table has a many-to-many relationship with the languages table. That is, many languages can be spoken in a country, and a language can be spoken in many countries.

This exercise looks at each of these in turn. First, what is the best way to query all the different languages spoken in a country? And second, how is this different from the best way to query all the countries that speak each language?

Recall that when writing joins, many users prefer to write SQL code out of order by writing the join first (along with any table aliases), and writing the SELECT statement at the end.

**Instructions:**

- Start with the join statement in line 6; perform an inner join with the countries table as c on the left with the languages table as l on the right.

- Make use of the USING keyword to join on code in line 8.

- Lastly, in line 2, select the country name, aliased as country, and the language name, aliased as language.

```sql
-- Select country and language names, aliased
SELECT c.name AS country, l.name AS language
-- From countries (aliased)
FROM countries AS c
-- Join to languages (aliased)
INNER JOIN languages as l
-- Use code as the joining field with the USING keyword
USING(code);
```

- Rearrange the SELECT statement so that the language column appears on the left and the country column on the right.

- Sort the results by language.

```sql
-- Rearrange SELECT statement, keeping aliases
SELECT l.name AS language, c.name AS country
FROM countries AS c
INNER JOIN languages AS l
USING(code)
-- Order the results by language
ORDER BY language;
```

- Question: Select the incorrect answer from the following options.

The query you generated in step 1 is provided below. Run this query (or the amendment you made in step 2) in the console to find the answer to the question.

SELECT c.name AS country, l.name AS language
FROM countries AS c
INNER JOIN languages AS l
USING(code)
ORDER BY country;

        "Alsatian is spoken in more than one country."

# Multiple joins

**Personal notes:**

**Joins on Joins*

A powerful feature of SQL is the ability to combine and execute multiple joins in a single query. We start with the same INNER JOIN as before and then chain another INNER JOIN to the result of our first INNER JOIN. Note that we use "left_table.id" in the last line of this example.

```sql
SELECT *
FROM left_table
INNER JOIN right_table
ON left_table.id = right_table.id
INNER JOIN another_table
ON left_table.id = another_table.id;
```

*If we want to perform the second join using the "id" field from "right_table" instead of "left_table," we can replace "left_table.id" with "right_table.id" in the final line.

Here's the final SQL query example for chaining a second INNER JOIN. Note that the syntax for the second join is exactly the same as the first join, but using "prime_minister" as the field to join:

```sql
SELECT
	p1.country,
	p1.continent,
	president,
	prime_minister,
	pm_start
FROM prime_ministers AS p1
INNER JOIN presidents AS p2
USING(country)
INNER JOIN prime_minister_terms as p3
USING(prime_minister);
```

*You could continue the chain and join as many tables as needed.

**Joining on Multiple Keys*

Another thing to know about joins is that not every value in the field being joined corresponds to exactly one record in the joining field of the right table. In the example shown, if we join on a field as we did before, the query will return multiple records from the right_table that correspond to the left_table on the id field. We can limit the returned records by providing an additional field to join by adding the AND keyword to our ON clause. In this example, we join on the date, a second column commonly used when joining on multiple fields.

```sql
SELECT *
FROM left_table
INNER JOIN right_table
ON left_table.id = right_table.id
    AND left_table.date = right_table.date;
```

**Exercises:**

**Joining multiple tables**

You've seen that the ability to combine multiple joins using a single query is a powerful feature of SQL.

Suppose you are interested in the relationship between fertility and unemployment rates. Your task in this exercise is to join tables to return the country name, year, fertility rate, and unemployment rate in a single result from the countries, populations and economies tables.

**Instructions:**

- Perform an inner join of countries AS c (left) with populations AS p (right), on code.
Select name, year and fertility_rate.

```sql
-- Select relevant fields
SELECT name, year, fertility_rate
-- Inner join countries and populations, aliased, on code
FROM countries AS c
INNER JOIN populations AS p
ON c.code = p.country_code;"
```
    
- Chain another inner join to your query with the economies table AS e, using code.
Select name, and using table aliases, select year and unemployment_rate from economies.

```sql
-- Select fields
SELECT name, e.year, fertility_rate, unemployment_rate
FROM countries AS c
INNER JOIN populations AS p
ON c.code = p.country_code
-- Join to economies (as e)
INNER JOIN economies AS e
-- Match on country code
ON p.country_code = e.code;
```

**Checking multi-table joins**

Have a look at the results for Albania from the previous query below. You can see that the 2015 fertility_rate has been paired with 2010 unemployment_rate, and vice versa.

        name	    year	fertility_rate	unemployment_rate

        Albania	    2015	    1.663	            17.1

        Albania	    2010	    1.663	            14

        Albania	    2015	    1.793	            17.1

        Albania	    2010	    1.793	            14

Instead of four records, the query should return two: one for each year. The last join was performed on c.code = e.code, without also joining on year. Your task in this exercise is to fix your query by explicitly stating that both the country code and year should match!

**Instruction:**

- Modify your query so that you are joining to economies on year as well as code.

```sql
SELECT name, e.year, fertility_rate, unemployment_rate
FROM countries AS c
INNER JOIN populations AS p
ON c.code = p.country_code
INNER JOIN economies AS e
ON c.code = e.code
        AND p.year = e.year;
-- Add an additional joining condition such that you are also joining on year
```

# Outer Joins, Cross Joins and Self Joins

**Chapter description:**

After familiarizing yourself with inner joins, you will come to grips with different kinds of outer joins. Next, you will learn about cross joins. Finally, you will learn about situations in which you might join a table with itself.

# LEFT and RIGHT JOINs

**Personal notes:**

In this chapter, we will cover outer joins, cross joins, and self-joins. Outer joins can retrieve records from other tables even if there are no matches for the field being joined.

**LEFT JOIN*

A LEFT JOIN will return all records in the left_table, and those records in the right_table that match the provided join field. An INNER JOIN returns only records matching the ids, while LEFT JOIN keeps all records in the left_table, as well as null values for right_val where there is no match in right_table. For example, let's say we want our query to include all countries with prime ministers, presidents if they happen to have them, and null values if they don't:

```sql
SELECT p1.country, prime_minister, president
FROM prime_ministers AS p1
LEFT JOIN presidents AS p2
USING(country);
```

*Note that LEFT JOIN can also be written as LEFT OUTER JOIN in SQL.

**RIGHT JOIN*

This is the second type of outer join and is much less common than LEFT JOIN, so it won't be extensively covered in this course. Instead of matching entries in the id column of left_table to the id column of right_table, a RIGHT JOIN does the reverse. All records are retained from right_table, even when id doesn't find a match in left_table. Null values are returned for the left_value field in records that don't find a match. An example of how RIGHT JOIN is performed; note that the order left_table and right_table is the same as we did in LEFT JOIN:

```sql
SELECT *
FROM left_table
RIGHT JOIN right_table
ON left_table.id = right_table.id;
```

*Note that RIGHT JOIN can also be written as RIGHT OUTER JOIN in SQL.

One of the main reasons RIGHT JOIN is not common is because it can always be rewritten as a LEFT JOIN. As we typically read from left to right, LEFT JOIN seems more intuitive for most users when constructing queries.

**Exercises:**

**This is a LEFT JOIN, right?**

Nice work getting to grips with the structure of joins! In this exercise, you'll explore the differences between INNER JOIN and LEFT JOIN. This will help you decide which type of join to use.

As before, you will be using the cities and countries tables.

You'll begin with an INNER JOIN with the cities table (left) and countries table (right). This helps if you are interested only in records where a country is present in both tables.

You'll then change to a LEFT JOIN. This helps if you're interested in returning all countries in the cities table, whether or not they have a match in the countries table.

**Instructions:**

- Perform an inner join with cities AS c1 on the left and countries as c2 on the right.
Use code as the field to merge your tables on.

```sql
SELECT 
        c1.name AS city,
        code,
        c2.name AS country,
        region,
        city_proper_pop
FROM cities AS c1
-- Perform an inner join with cities as c1 and countries as c2 on country code
INNER JOIN countries AS c2
ON c1.country_code = c2.code
ORDER BY code DESC;
```

- Change the code to perform a LEFT JOIN instead of an INNER JOIN.
After executing this query, have a look at how many records the query result contains.

```sql
SELECT 
        c1.name AS city, 
        code, 
        c2.name AS country,
        region, 
        city_proper_pop
FROM cities AS c1
-- Join right table (with alias)
LEFT JOIN countries AS c2
ON c1.country_code = c2.code
ORDER BY code DESC;
```

**Building on your LEFT JOIN**

You'll now revisit the use of the AVG() function introduced in a previous course.

Being able to build more than one SQL function into your query will enable you to write compact, supercharged queries.

You will use AVG() in combination with a LEFT JOIN to determine the average gross domestic product (GDP) per capita by region in 2010.

**Instructions:**

- Complete the LEFT JOIN with the countries table on the left and the economies table on the right on the code field.

- Filter the records from the year 2010.

```sql
SELECT name, region, gdp_percapita
FROM countries AS c
LEFT JOIN economies AS e
-- Match on code fields
USING(code)
-- Filter for the year 2010
WHERE year = 2010;
```

- To calculate per capita GDP per region, begin by grouping by region.

- After your GROUP BY, choose region in your SELECT statement, followed by average GDP per capita using the AVG() function, with AS avg_gdp as your alias.

```sql
-- Select region, and average gdp_percapita as avg_gdp
SELECT region, AVG(gdp_percapita) AS avg_gdp
FROM countries AS c
LEFT JOIN economies AS e
USING(code)
WHERE year = 2010
-- Group by region
GROUP BY region;
```

- Order the result set by the average GDP per capita from highest to lowest.

- Return only the first 10 records in your result.

```sql
SELECT region, AVG(gdp_percapita) AS avg_gdp
FROM countries AS c
LEFT JOIN economies AS e
USING(code)
WHERE year = 2010
GROUP BY region
-- Order by descending avg_gdp
ORDER BY avg_gdp DESC 
-- Return only first 10 records
LIMIT 10;
```

**Is this RIGHT?**

You learned that right joins are not used as commonly as left joins. A key reason for this is that right joins can always be re-written as left joins, and because joins are typically typed from left to right, joining from the left feels more intuitive when constructing queries.

It can be tricky to wrap one's head around when left and right joins return equivalent results. You'll explore this in this exercise!

**Instructions:**

- Write a new query using RIGHT JOIN that produces an identical result to the LEFT JOIN provided.

```sql
-- Modify this query to use RIGHT JOIN instead of LEFT JOIN
SELECT languages.name AS language, countries.name AS country, percent
FROM languages
RIGHT JOIN countries
USING(code)
ORDER BY countries;
```

# FULL JOINs

**Personal notes:**

FULL JOIN is the last of the three types of outer joins. A FULL JOIN combines a LEFT JOIN and a RIGHT JOIN. This type of join will return all ids because the FULL JOIN will return all ids, regardless of whether they have a match in the other table being joined. An example of a FULL JOIN:

```sql
SELECT 
	left_table.id AS L_id,
	right_table.id AS R_id,
	left_table.val AS L_val,
	right_table.val AS R_val
FROM left_table
FULL JOIN right_table
USING(id);
```

Note that the keyword FULL OUTER JOIN can also be used to return the same result in SQL.

For example, suppose we were interested in all countries in our database and wanted to check if they had a president, a prime minister, or both. Let's go through the code line by line to do this using a FULL JOIN. The SELECT statement begins by including the country as well as the prime_minister and president fields. Then, we specify prime_ministers as our left table and alias it as p1. Next, we add the FULL JOIN statement and add presidents as the right table, using the alias p2. Finally, the join is performed using the country as the join field in both tables.

```sql
SELECT p1.country AS country, prime_minister, president
FROM prime_minister AS p1
FULL JOIN presidents AS p2
ON p1.country = p2.country
LIMIT 10;
```

**Exercises:**

**Comparing joins**

In this exercise, you'll examine how results can differ when performing a full join compared to a left join and inner join by joining the countries and currencies tables. You'll be focusing on the North American region and records where the name of the country is missing.

You'll begin with a full join with countries on the left and currencies on the right. Recall the workings of a full join with the diagram below!

You'll then complete a similar left join and conclude with an inner join, observing the results you see along the way.

**Instructions:**

- Perform a full join with countries (left) and currencies (right).
Filter for the North America region or NULL country names.

```sql
SELECT name AS country, code, region, basic_unit
FROM countries
-- Join to currencies
FULL JOIN currencies
USING (code)
-- Where region is North America or name is null
WHERE region = 'North America'
        OR name is null
ORDER BY region;
```

- Repeat the same query as before, turning your full join into a left join with the currencies table.
Have a look at what has changed in the output by comparing it to the full join result.

```sql
SELECT name AS country, code, region, basic_unit
FROM countries
-- Join to currencies
LEFT JOIN currencies
USING (code)
WHERE region = 'North America' 
        OR name IS NULL
ORDER BY region;
```

- Repeat the same query again, this time performing an inner join of countries with currencies.
Have a look at what has changed in the output by comparing it to the full join and left join results!

```sql
SELECT name AS country, code, region, basic_unit
FROM countries
-- Join to currencies
INNER JOIN currencies
USING (code)
WHERE region = 'North America' 
        OR name IS NULL
ORDER BY region;
```

**Chaining FULL JOINs**

As you have seen in the previous chapter on INNER JOIN, it is possible to chain joins in SQL, such as when looking to connect data from more than two tables.

Suppose you are doing some research on Melanesia and Micronesia, and are interested in pulling information about languages and currencies into the data we see for these regions in the countries table. Since languages and currencies exist in separate tables, this will require two consecutive full joins involving the countries, languages and currencies tables.

**Instructions:**

- Complete the FULL JOIN with countries as c1 on the left and languages as l on the right, using code to perform this join.

- Next, chain this join with another FULL JOIN, placing currencies on the right, joining on code again.

```sql
SELECT 
        c1.name AS country, 
        region, 
        l.name AS language,
        basic_unit, 
        frac_unit
FROM countries as c1 
-- Full join with languages (alias as l)
FULL JOIN languages as l
USING(code)
-- Full join with currencies (alias as c2)
FULL JOIN currencies AS c2
USING(code)
WHERE region LIKE 'M%esia';
```

# Crossing into CROSS JOIN

**Personal notes:**

CROSS JOINs are different from the joins we've seen earlier: they create all possible combinations of two tables. Note that the syntax is minimal, and we don't specify ON or USING with CROSS JOIN:

```sql
SELECT id1, id2
FROM table1
CROSS JOIN table2;
```

For example, suppose all the prime ministers from Asia in our database have individual meetings scheduled with all the presidents from South America in our database, and we are journalists wanting to track all these meetings that will take place. We can create a query that returns all these combinations using a CROSS JOIN. We use a WHERE clause to focus only on prime ministers from Asia and presidents from South America.

```sql
SELECT prime_minister, president
FROM prime_ministers AS p1
CROSS JOIN presidents AS p2
WHERE p1.continent IN ('Asia')
	AND p2.continent IN ('South America');
```

**Exercises:**

**Histories and languages**

Well done getting to know all about CROSS JOIN! As you have learned, CROSS JOIN can be incredibly helpful when asking questions that involve looking at all possible combinations or pairings between two sets of data.

Imagine you are a researcher interested in the languages spoken in two countries: Pakistan and India. You are interested in asking:

What are the languages presently spoken in the two countries?
Given the shared history between the two countries, what languages could potentially have been spoken in either country over the course of their history?
In this exercise, we will explore how INNER JOIN and CROSS JOIN can help us answer these two questions, respectively.

**Instructions:**

- Complete the code to perform an INNER JOIN of countries AS c with languages AS l using the code field to obtain the languages currently spoken in the two countries.

```sql
SELECT c.name AS country, l.name AS language
-- Inner join countries as c with languages as l on code
FROM countries AS c
INNER JOIN languages AS l
USING(code)
WHERE c.code IN ('PAK','IND')
        AND l.code in ('PAK','IND');
```

- Change your INNER JOIN to a different kind of join to look at possible combinations of languages that could have been spoken in the two countries given their history.

- Observe the differences in output for both joins.

```sql
SELECT c.name AS country, l.name AS language
FROM countries AS c        
-- Perform a cross join to languages (alias as l)
CROSS JOIN languages AS l
WHERE c.code in ('PAK','IND')
        AND l.code in ('PAK','IND');
```

**Choosing your join**

Now that you're fully equipped to use joins, try a challenge problem to test your knowledge!

You will determine the names of the five countries and their respective regions with the lowest life expectancy for the year 2010. Use your knowledge about joins, filtering, sorting and limiting to create this list!

**Instructions:**

- Complete the join of countries AS c with populations as p.

- Filter on the year 2010.

- Sort your results by life expectancy in ascending order.

- Limit the result to five countries.

```sql
SELECT 
        c.name AS country,
        region,
        life_expectancy AS life_exp
FROM countries AS c
-- Join to populations (alias as p) using an appropriate join
LEFT JOIN populations as p
ON c.code = p.country_code
-- Filter for only results in the year 2010
WHERE year = 2010
-- Sort by life_exp
ORDER BY life_exp
-- Limit to five records
LIMIT 5;
```

# Self joins

**Personal notes:**

Self joins are automatic joins where a table is joined with itself. Self joins are used to compare values from part of a table with other values in the same table. For example, suppose all prime ministers are meeting in summits in their own continents. We want to create a new table showing all countries from the same continent as pairs.

Self joins don't have dedicated syntax like other joins we've seen. We can't simply write `SELF JOIN` in SQL code. Also, an alias is necessary for a self join. 

```sql
SELECT
    p1.country AS country1,
    p2.country AS country2,
    p1.continent
FROM prime_ministers AS p1
INNER JOIN prime_ministers AS p2
ON p1.continent = p2.continent
LIMIT 10;
```

In this case, the join will pair countries, including with themselves. To address this, we can use the `AND` clause to ensure multiple conditions are met in the `ON` clause. In our second condition, we use the not equal operator to exclude records that are identical.

```sql
SELECT
    p1.country AS country1,
    p2.country AS country2,
    p1.continent
FROM prime_ministers AS p1
INNER JOIN prime_ministers AS p2
ON p1.continent = p2.continent
    AND p1.country <> p2.country;
```

**Exercises:**

**Comparing a country to itself**

Self joins are very useful for comparing data from one part of a table with another part of the same table. Suppose you are interested in finding out how much the populations for each country changed from 2010 to 2015. You can visualize this change by performing a self join.

In this exercise, you'll work to answer this question by joining the populations table with itself. Recall that, with self joins, tables must be aliased. Use this as an opportunity to practice your aliasing!

Since you'll be joining the populations table to itself, you can alias populations first as p1 and again as p2. This is good practice whenever you are aliasing tables with the same first letter.

**Instructions:**

- Perform an inner join of populations with itself ON country_code, aliased p1 and p2 respectively.

- Select the country_code from p1 and the size field from both p1 and p2, aliasing p1.size as size2010 and p2.size as size2015 (in that order).

```sql
-- Select aliased fields from populations as p1
SELECT p1.country_Code, p1.size AS size2010, p2.size AS size2015
-- Join populations as p1 to itself, alias as p2, on country code
FROM populations AS p1
INNER JOIN populations AS p2
ON p1.country_code = p2.country_code;
```

- Since you want to compare records from 2010 and 2015, eliminate unwanted records by extending the WHERE statement to include only records where the p1.year matches p2.year - 5.

```sql
SELECT 
        p1.country_code, 
        p1.size AS size2010, 
        p2.size AS size2015
FROM populations AS p1
INNER JOIN populations AS p2
ON p1.country_code = p2.country_code
WHERE p1.year = 2010
-- Filter such that p1.year is always five years before p2.year
AND p1.year = p2.year-5;
```

# Set Theory for SQL Joins

**Chapter description:**

In this chapter, you will learn about using set theory operations in SQL, with an introduction to UNION, UNION ALL, INTERSECT, and EXCEPT clauses. You’ll explore the predominant ways in which set theory operations differ from join operations.

# Set theory for SQL Joins

**Personal notes:**

SQL has three main set operations: `UNION`, `INTERSECT`, and `EXCEPT`.

**UNION*

The `UNION` operator takes two tables as input and returns all records from both tables. If two records are identical, `UNION` will return them only once. There is an additional operator for unions called `UNION ALL`. In contrast to `UNION`, given the same two tables, `UNION ALL` includes duplicate records.

**UNION and UNION ALL Syntax*

You perform a `SELECT` statement on our first table, a `SELECT` statement on our second table, and specify a set operation.

```sql
SELECT *
FROM left_table
UNION
SELECT *
FROM right_table;
```

```sql
SELECT *
FROM left_table
UNION ALL
SELECT *
FROM right_table;
```

Instead of comparing and merging tables left and right, they stack fields on top of each other.

For all set operations, the number of selected columns and their respective data types must be identical.

**Exercises:**

**UNION vs. UNION ALL**

Nice work learning all about UNION and UNION ALL!

Two tables, languages and currencies, are provided. Run the queries provided in the console and select the correct answer for the multiple-choice questions in this exercise.

**Instructions:**

- Question: What result will the following SQL query produce?

SELECT * 
FROM languages
UNION
SELECT * 
FROM currencies;

        "A SQL error, because languages and currencies do not have the same number of fields"

- Question: What result will the following SQL query produce?

SELECT code FROM
languages
UNION ALL
SELECT code FROM 
currencies;

        "An unordered list of each country code in languages and currencies, including duplicates"

- Question: What will the following SQL query produce?

SELECT code 
FROM languages
UNION
SELECT curr_id 
FROM currencies;

         "A SQL error, because code and curr_id are not of the same data type"

**Comparing global economies**

Are you ready to perform your first set operation?

In this exercise, you have two tables, economies2015 and economies2019, available to you under the tabs in the console. You'll perform a set operation to stack all records in these two tables on top of each other, excluding duplicates.

When drafting queries containing set operations, it is often helpful to write the queries on either side of the operation first, and then call the set operator. The instructions are ordered accordingly.

**Instructions:**

- Begin your query by selecting all fields from economies2015.

- Create a second query that selects all fields from economies2019.

- Perform a set operation to combine the two queries you just created, ensuring you do not return duplicates.

```sql
-- Select all fields from economies2015
SELECT *
FROM economies2015  
-- Set operation
UNION
-- Select all fields from economies2019
SELECT *
FROM economies2019
ORDER BY code, year;
```

**Comparing two set operations**

You learned in the video exercise that UNION ALL returns duplicates, whereas UNION does not. In this exercise, you will dive deeper into this, looking at cases for when UNION is appropriate compared to UNION ALL.

You will be looking at combinations of country code and year from the economies and populations tables.

**Instructions:**

- Perform an appropriate set operation that determines all pairs of country code and year (in that order) from economies and populations, excluding duplicates.
Order by country code and year.

```sql
-- Query that determines all pairs of code and year from economies and populations, without duplicates
SELECT code, year
FROM economies
UNION
SELECT country_code, year
FROM populations
```

- Amend the query to return all combinations (including duplicates) of country code and year in the economies or the populations tables.

```sql
SELECT code, year
FROM economies
-- Set theory clause
UNION ALL
SELECT country_code, year
FROM populations
ORDER BY code, year;
```

# At the INTERSECT

**Personal notes:**

`INTERSECT` takes two tables as input and returns only the records that exist in both tables.

**INTERSECT Syntax*

The syntax for this set operation is similar to that of `UNION` and `UNION ALL`. You perform a `SELECT` statement on our first table, a `SELECT` on the second table, and specify our set operator between them:

```sql
SELECT id, val
FROM left_table
INTERSECT
SELECT id, val
FROM right_table;
```

Similar to `UNION`, for a record to be returned, `INTERSECT` requires all fields to match because in set operations, we don't specify any fields to match. This is also why it requires the left and right tables to have the same number of columns for comparing records.

**Exercises:**

**Review UNION and INTERSECT**

Which of the following definitions of set operations is correct?

        "INTERSECT: returns only records appearing in both tables"

# EXCEPT

**Personal notes:**

`EXCEPT` allows us to identify the records that are present in one table but not in another. More specifically, it retains only the records from the left table that are not present in the right table.

**EXCEPT Syntax*

For example, the SQL code shown in the lesson selects the `monarch` and `country` fields from the `monarchs` table and then looks for common entries in the `prime_minister` and `country` fields in the `prime_ministers` table, aiming to exclude those entries:

```sql
SELECT monarch, country
FROM monarchs
EXCEPT
SELECT prime_minister, country
FROM prime_ministers;
```

This operation is similar to a set difference, where it returns the records from the first table that are not found in the second table.

**Exercises:**

**You've got it, EXCEPT...**

Just as you were able to leverage INTERSECT to find the names of cities with the same names as countries, you can also do the reverse, using EXCEPT.

In this exercise, you will find the names of cities that do not have the same names as their countries.

**Instruction:** 

- Return all cities that do not have the same name as a country.

```sql
-- Return all cities that do not have the same name as a country
SELECT name
FROM cities
EXCEPT
SELECT name
FROM countries
ORDER BY name;
```

# Subqueries

**Chapter description:**

In this closing chapter, you’ll begin by investigating semi-joins and anti-joins. Next, you'll learn how to use nested queries. Last but not least, you’ll wrap up the course with some challenges!

# Subquerying with semi joins and anti joins

**Personal notes:**

**Semi Join*

A semi-join chooses records from the first table where a condition is met in the second table. Specifically, the semi-join will return all values from `left_table` where the values in `col1` are in a column we specify, i.e., `col2` in `right_table`.

**Example:*

Suppose we are interested in determining the presidents of countries that gained independence before 1800. We select the fields `president`, `country`, and `continent`. We can use a list of countries as a filter by incorporating it into an additional WHERE clause; this is called a subquery:

```sql
SELECT president, country, continent
FROM presidents
WHERE country IN
	(SELECT country
	FROM states
	WHERE indep_year < 1800);
```

It chooses the records in the first table where the country matches the list returned by our subquery.

**Anti Join*

An anti-join chooses records in the first table where `col1` does not find a match in `col2`. For example, to adapt our previous semi-join to determine the countries in the Americas founded after 1800, we add `NOT` before the `IN` statement. This is called an anti-join:

```sql
SELECT country, president
FROM presidents
WHERE continent LIKE '%America'
	AND country NOT IN
	(SELECT country
	FROM states
	WHERE indep_year < 1800);
```

Subqueries within the WHERE clause can be from the same table or a different table. For instance:

```sql
SELECT *
FROM some_table
WHERE some_field IN
	(SELECT some_numeric_field
	FROM another_table
	WHERE field2 = some_condition);
```

**Exercises:**

**Semi join**

Great job getting acquainted with semi joins and anti joins! You are now going to practice using semi joins.

Let's say you are interested in identifying languages spoken in the Middle East. The languages table contains information about languages and countries, but it does not tell you what region the countries belong to. You can build up a semi join by filtering the countries table by a particular region, and then using this to further filter the languages table.

You'll build up your semi join as you did in the video exercise, block by block, starting with a selection of countries from the countries table, and then leveraging a WHERE clause to filter the languages table by this selection.

**Instructions:**

-  Select country code as a single field from the countries table, filtering for countries in the 'Middle East' region.

```sql
-- Select country code for countries in the Middle East
SELECT code, region
FROM countries
WHERE region = 'Middle East';
```

- Write a second query to SELECT the name of each unique language appearing in the languages table; do not use column aliases here.

- Order the result set by name in ascending order.

```sql
-- Select unique language names
SELECT DISTINCT name 
FROM languages
-- Order by the name of the language
ORDER BY name;
```

- Create a semi join out of the two queries you've written, which filters unique languages returned in the first query for only those languages spoken in the 'Middle East'.

```sql
SELECT DISTINCT name
FROM languages
-- Add syntax to use bracketed subquery below as a filter
WHERE code IN 
        (SELECT code
        FROM countries
        WHERE region = 'Middle East')
ORDER BY name;
```

**Diagnosing problems using anti join**

Nice work on semi joins! The anti join is a related and powerful joining tool. It can be particularly useful for identifying whether an incorrect number of records appears in a join.

Say you are interested in identifying currencies of Oceanian countries. You have written the following INNER JOIN, which returns 15 records. Now, you want to ensure that all Oceanian countries from the countries table are included in this result. You'll do this in the first step.
```sql
SELECT c1.code, name, basic_unit AS currency
FROM countries AS c1
INNER JOIN currencies AS c2
ON c1.code = c2.code
WHERE c1.continent = 'Oceania';
```

If there are any Oceanian countries excluded in this INNER JOIN, you want to return the names of these countries. You'll write an anti join to this in the second step!

**Instructions:**

- Begin by writing a query to return the code and name (in order, not aliased) for all countries in the continent of Oceania from the countries table.

- Observe the number of records returned and compare this with the provided INNER JOIN, which returns 15 records.

```sql
-- Select code and name of countries from Oceania
SELECT code, name
FROM countries
WHERE continent = 'Oceania';
```

- Now, build on your query to complete your anti join, by adding an additional filter to return every country code that is not included in the currencies table.

```sql
SELECT code, name
FROM countries
WHERE continent = 'Oceania'
-- Filter for countries not included in the bracketed subquery
AND code NOT IN
(SELECT code
FROM currencies);
```

# Subqueries inside WHERE and SELECT

**Personal notes:**

The second most common type of subquery is inside a SELECT clause.

**Example:*

Suppose we want to count the number of monarchs listed in the monarchs table for each continent in the states table. In previous courses, we saw the use of GROUP BY to count data by a group. However, since our monarchs' data is in a different table than the states table, this would involve a careful join before the GROUP BY. Let's see how to do this with a subquery. First, we need to count all monarchs. Second, we need a WHERE statement that matches the `continent` fields in both tables. This subquery follows the selection of distinct continents and, therefore, counts all monarchs within them in the SELECT statement. A subquery inside a SELECT statement requires an alias, like `monarch_count` in this example:

```sql
SELECT DISTINCT continent,
	(SELECT COUNT(*)
	FROM monarchs
	WHERE states.continent = monarchs.continent) AS monarch_count
FROM states;
```

**Exercises:**

**Subquery inside WHERE**

The video pointed out that subqueries inside WHERE can either be from the same table or a different table. In this exercise, you will nest a subquery from the populations table inside another query from the same table, populations. Your goal is to figure out which countries had high average life expectancies in 2015.

You can use SQL to do calculations for you. Suppose you only want records from 2015 with life_expectancy above 1.15 * avg_life_expectancy. You could use the following SQL query.

```sql
SELECT *
FROM populations
WHERE life_expectancy > 1.15 * avg_life_expectancy
  AND year = 2015;
```
In the first step, you'll write a query to calculate a value for avg_life_expectancy. In the second step, you will nest this calculation into another query.

**Instructions:**

- Begin by calculating the average life expectancy from the populations table.

- Filter your answer to use records from 2015 only.

```sql
-- Select average life_expectancy from the populations table
SELECT AVG(life_expectancy)
FROM populations
-- Filter for the year 2015
WHERE year = 2015;
```

- The answer from your query has now been nested into another query; use this calculation to filter populations for all records where life_expectancy is 1.15 times higher than average.

```sql
SELECT *
FROM populations
-- Filter for only those populations where life expectancy is 1.15 times higher than average
WHERE life_expectancy > 1.15 * 
(SELECT AVG(life_expectancy)
FROM populations
WHERE year = 2015) 
        AND year = 2015;
```

**WHERE do people live?**

In this exercise, you will strengthen your knowledge of subquerying by identifying capital cities in order of largest to smallest population.

Follow the instructions below to get the urban area population for capital cities only. You'll use the countries and cities tables displayed in the console to help identify columns of interest as you build your query.

**Instruction:**

- Return the name, country_code and urbanarea_pop for all capital cities (not aliased).

```sql
-- Select relevant fields from cities table
SELECT name, country_code, urbanarea_pop
FROM cities
-- Filter using a subquery on the countries table
WHERE name IN
        (SELECT capital
        FROM countries)
ORDER BY urbanarea_pop DESC;
```

**Subquery inside SELECT**

As explored in the video, there are often multiple ways to produce the same result in SQL. You saw that subqueries can provide an alternative to joins to obtain the same result.

In this exercise, you'll go further in exploring how some queries can be written using either a join or a subquery.

In Step 1, you'll begin with a LEFT JOIN combined with a GROUP BY to select the nine countries with the most cities appearing in the cities table, along with the counts of these cities. In Step 2, you'll write a query that returns the same result as the join, but leveraging a nested query instead.

**Instructions:**

- Write a LEFT JOIN with countries on the left and the cities on the right, joining on country code.

- In the SELECT statement of your join, include country names as country, and count the cities in each country, aliased as cities_num.

- Sort by cities_num (descending), and country (ascending), limiting to the first nine records.

```sql
-- Find top nine countries with the most cities
SELECT countries.name AS country, COUNT(*) AS cities_num
FROM countries
LEFT JOIN cities
ON countries.code = cities.country_code
GROUP BY country
ORDER BY cities_num DESC, country
LIMIT 9;
```

- Complete the subquery to return a result equivalent to your LEFT JOIN, counting all cities in the cities table as cities_num.

- Use the WHERE clause to enable the correct country codes to be matched in the cities and countries columns.

```sql
SELECT countries.name AS country,
-- Subquery that provides the count of cities   
(SELECT COUNT(*)
FROM cities
WHERE countries.code = cities.country_code) AS cities_num
FROM countries
ORDER BY cities_num DESC, country
LIMIT 9;
```

# Subqueries inside FROM

**Personal notes:**

The last type of subquery we will cover is inside the FROM clause.

Suppose we are interested in all continents with monarchs, along with the most recent country to gain independence on that continent. An SQL query starts to extract all the most recent independence years per continent is shown. The query groups the records by continent and returns the most recent independence year for each group, using the MAX() function AS most_recent.

```sql
SELECT continent, MAX(indep_year) AS most_recent
FROM states
GROUP BY continent;
```

Now, how do we filter this for continents with monarchs? We haven't seen that we can include multiple tables in a FROM clause by adding a comma between them. In the following example, the syntax demonstrates including two different tables, `left_table` and `right_table`, in our FROM clause. We can include the DISTINCT command to avoid duplicates.

```sql
SELECT DISTINCT left_table.id, left_val
FROM left_table, right_table
WHERE left_table.id = right_table.id;
```

We can nest the subquery we initially wrote into a FROM statement, where we are selecting between `monarchs` and our subquery, nicknamed "sub". We also use the WHERE clause as before to identify records in both tables that match on the continent. As before, in our SELECT statement, we use the DISTINCT command to eliminate duplicates and select `sub.most_recent` to get the most recent independence year for each continent. Finally, we use the ORDER BY continent.

```sql
SELECT DISTINCT monarchs.continent, sub.most_recent
FROM monarchs,
	(SELECT
		continent,
		MAX(indep_year) AS most_recent
	FROM states
	GROUP BY continent) AS sub
WHERE monarchs.continent = sub.continent
ORDER BY continent;
```

**Exercises:**

**Subquery inside FROM**

Subqueries inside FROM can help select columns from multiple tables in a single query.

Say you are interested in determining the number of languages spoken for each country. You want to present this information alongside each country's local_name, which is a field only present in the countries table and not in the languages table. You'll use a subquery inside FROM to bring information from these two tables together!

**Instructions:**

- Begin with a query that groups by each country code from languages, and counts the languages spoken in each country as lang_num.

- In your SELECT statement, return code and lang_num (in that order).

```sql
-- Select code, and language count as lang_num
select code, count(*) as lang_num
from languages
group by code;
```

- Select local_name from countries, with the aliased lang_num from your subquery (which has been nested and aliased for you as sub).

- Use WHERE to match the code field from countries and sub.

```sql
-- Select local_name and lang_num from appropriate tables
SELECT local_name, sub.lang_num
FROM countries,
(SELECT code, COUNT(*) AS lang_num
FROM languages
GROUP BY code) AS sub
-- Where codes match
WHERE countries.code = sub.code
ORDER BY lang_num DESC;
```

**Subquery challenge**

You're near the finish line! Test your understanding of subquerying with a challenge problem.

Suppose you're interested in analyzing inflation and unemployment rate for certain countries in 2015. You are not interested in countries with "Republic" or "Monarchy" as their form of government, but are interested in all other forms of government, such as emirate federations, socialist states, and commonwealths.

You will use the field gov_form to filter for these two conditions, which represents a country's form of government. You can review the different entries for gov_form in the countries table.

**Instructions:**

- Select country code, inflation_rate, and unemployment_rate from economies.

- Filter code for the set of countries which do not contain the words "Republic" or "Monarchy" in their gov_form.

```sql
-- Select relevant fields
SELECT code, inflation_rate, unemployment_rate
FROM economies
WHERE year = 2015 
AND code NOT IN
-- Subquery returning country codes filtered on gov_form
        (SELECT code
        FROM countries
        WHERE (gov_form LIKE '%Monarchy%' OR gov_form LIKE '%Republic%'))
ORDER BY inflation_rate;
```

**Final challenge**

You've made it to the final challenge problem! Get ready to tackle this step-by-step.

Your task is to determine the top 10 capital cities in Europe and the Americas by city_perc, a metric you'll calculate. city_perc is a percentage that calculates the "proper" population in a city as a percentage of the total population in the wider metro area, as follows:

city_proper_pop / metroarea_pop * 100

Do not use table aliasing in this exercise.

**Instructions:**

- From cities, select the city name, country code, proper population, and metro area population, as well as the field city_perc, which calculates the proper population as a percentage of metro area population for each city (using the formula provided).

- Filter city name with a subquery that selects capital cities from countries in 'Europe' or continents with 'America' at the end of their name.

- Exclude NULL values in metroarea_pop.

- Order by city_perc (descending) and return only the first 10 rows.

```sql
SELECT name, country_code, city_proper_pop, metroarea_pop,  
        city_proper_pop / metroarea_pop * 100 AS city_perc
FROM cities
WHERE name IN
(SELECT capital
FROM countries
WHERE (continent = 'Europe'
        OR continent LIKE '%America'))
        AND metroarea_pop IS NOT NULL
ORDER BY city_perc desc
limit 10;
```

# Data Manipulation in SQL

**Course Description**

So you've learned how to aggregate and join data from tables in your database—now what? How do you manipulate, transform, and make the most sense of your data? This intermediate-level course will teach you several key functions necessary to wrangle, filter, and categorize information in a relational database, expand your SQL toolkit, and answer complex questions. You will learn the robust use of CASE statements, subqueries, and window functions—all while discovering some interesting facts about soccer using the European Soccer Database.

# We'll take the CASE

**Chapter Description:**

In this chapter, you will learn how to use the CASE WHEN statement to create categorical variables, aggregate data into a single column with multiple filtering conditions, and calculate counts and percentages.

# We'll take the CASE

**Personal notes:**

In this course, we'll be using the European Soccer Database—a relational database containing data on over 25,000 matches, 300 teams, and 10,000 players from Europe between 2008 and 2016. The data is contained in four tables—country, league, team, and match.

**CASE Statements*

CASE statements are SQL's version of an "IF this THEN that" statement. CASE statements have three parts—a WHEN clause, a THEN clause, and an ELSE clause.

- **WHEN:* Tests a specific condition. If this condition is true, it will return the item specified after the THEN clause. You can create multiple conditions by listing the WHEN and THEN statements in the same CASE statement.
- **THEN:* Specifies the value to be returned if the corresponding WHEN condition is true.
- **ELSE:* Returns a specified value if none of the WHEN conditions are true.

After you've completed the statement, you need to include the term `END` and give it an alias.

```sql
CASE 
  WHEN x = 1 THEN 'a'
  WHEN x = 2 THEN 'b'
  ELSE 'c' 
END AS new_column
```

**Example:*

Using a CASE statement to create a new variable that identifies matches as home team wins, away team wins, or ties. A new column is created with appropriate text for each match based on the result.

```sql
SELECT
  id,
  home_goal,
  away_goal,
  CASE 
    WHEN home_goal > away_goal THEN 'Home Team Win'
    WHEN home_goal < away_goal THEN 'Away Team Win'
    ELSE 'Tie' 
  END AS outcome
FROM match
WHERE season = '2013/2014';
```

**Exercises:**

**Basic CASE statements**

What is your favorite team?

The European Soccer Database contains data about 12,800 matches from 11 countries played between 2011-2015! Throughout this course, you will be shown filtered versions of the tables in this database in order to better explore their contents.

In this exercise, you will identify matches played between FC Schalke 04 and FC Bayern Munich. There are 2 teams identified in each match in the hometeam_id and awayteam_id columns, available to you in the filtered matches_germany table. ID can join to the team_api_id column in the teams_germany table, but you cannot perform a join on both at the same time.

However, you can perform this operation using a CASE statement once you've identified the team_api_id associated with each team!

**Instructions:**

- Select the team's long name and API id from the teams_germany table.

- Filter the query for FC Schalke 04 and FC Bayern Munich using IN, giving you the team_api_IDs needed for the next step.

```sql
SELECT
    -- Select the team long name and team API id
    team_long_name,
    team_api_id
FROM teams_germany
-- Only include FC Schalke 04 and FC Bayern Munich
WHERE team_long_name IN ('FC Schalke 04', 'FC Bayern Munich');
```

- Create a CASE statement that identifies whether a match in Germany included FC Bayern Munich, FC Schalke 04, or neither as the home team.

- Group the query by the CASE statement alias, home_team.

```sql
-- Identify the home team as Bayern Munich, Schalke 04, or neither
SELECT 
    CASE WHEN hometeam_id = 10189 THEN 'FC Schalke 04'
        WHEN hometeam_id = 9823 THEN 'FC Bayern Munich'
        ELSE 'Other' END AS home_team,
    COUNT(id) AS total_matches
FROM matches_germany
-- Group by the CASE statement alias
GROUP BY home_team;
```

**CASE statements comparing column values**

Barcelona is considered one of the strongest teams in Spain's soccer league.

In this exercise, you will be creating a list of matches in the 2011/2012 season where Barcelona was the home team. You will do this using a CASE statement that compares the values of two columns to create a new group -- wins, losses, and ties.

In 3 steps, you will build a query that identifies a match's winner, identifies the identity of the opponent, and finally filters for Barcelona as the home team. Completing a query in this order will allow you to watch your results take shape with each new piece of information.

The matches_spain table currently contains Barcelona's matches from the 2011/2012 season, and has two key columns, hometeam_id and awayteam_id, that can be joined with the teams_spain table. However, you can only join teams_spain to one column at a time.

**Instructions:**

- Select the date of the match and create a CASE statement to identify matches as home wins, home losses, or ties.

```sql
SELECT 
    -- Select the date of the match
    date,
    -- Identify home wins, losses, or ties
    CASE WHEN home_goal > away_goal THEN 'Home win!'
        WHEN home_goal < away_goal THEN 'Home loss :(' 
        ELSE 'Tie' END AS outcome
FROM matches_spain;
```

- Left join the teams_spain table team_api_id column to the matches_spain table awayteam_id. This allows us to retrieve the away team's identity.

- Select team_long_name from teams_spain as opponent and complete the CASE statement from Step 1.

```sql
SELECT 
    m.date,
    --Select the team long name column and call it 'opponent'
    t.team_long_name AS opponent, 
    -- Complete the CASE statement with an alias
    CASE WHEN m.home_goal > away_goal THEN 'Home win!'
        WHEN m.home_goal < away_goal THEN 'Home loss :('
        ELSE 'Tie' END AS outcome
FROM matches_spain AS m
-- Left join teams_spain onto matches_spain
LEFT JOIN teams_spain AS t
ON m.awayteam_id = t.team_api_id;
```

- Complete the same CASE statement as the previous steps.

- Filter for matches where the home team is FC Barcelona (id = 8634).

```sql
SELECT 
    m.date,
    t.team_long_name AS opponent,
    -- Complete the CASE statement with an alias
    CASE WHEN m.home_goal > m.away_goal  THEN 'Barcelona win!'
        WHEN m.home_goal < m.away_goal THEN 'Barcelona loss :(' 
        ELSE 'Tie' END AS outcome 
FROM matches_spain AS m
LEFT JOIN teams_spain AS t 
ON m.awayteam_id = t.team_api_id
-- Filter for Barcelona as the home team
WHERE m.hometeam_id = 8634; 
```

**CASE statements comparing two column values part 2**

Similar to the previous exercise, you will construct a query to determine the outcome of Barcelona's matches where they played as the away team. You will learn how to combine these two queries in chapters 2 and 3.

Did their performance differ from the matches where they were the home team?

**Instructions:**

- Complete the CASE statement to identify Barcelona's away team games (id = 8634) as wins, losses, or ties.

- Left join the teams_spain table team_api_id column on the matches_spain table hometeam_id column. This retrieves the identity of the home team opponent.

- Filter the query to only include matches where Barcelona was the away team.

```sql
-- Select matches where Barcelona was the away team
SELECT  
    m.date,
    t.team_long_name AS opponent,
    CASE WHEN home_goal < away_goal THEN 'Barcelona win!'
        WHEN home_goal > away_goal THEN 'Barcelona loss :(' 
        ELSE 'Tie' END AS outcome
FROM matches_spain AS m
-- Join teams_spain to matches_spain
LEFT JOIN teams_spain AS t 
ON m.hometeam_id = t.team_api_id
WHERE m.awayteam_id = 8634;
```

# In CASE things get more complex

**Personal notes:**

If you want to test multiple logical conditions in a CASE statement, you can use `AND` within your WHEN clause. For example, let's check if each match was played and won by the Chelsea team.

```sql
SELECT date, hometeam_id, awayteam_id,
  CASE 
    WHEN hometeam_id = 8455 AND home_goal > away_goal THEN 'Chelsea home win!'
    WHEN awayteam_id = 8455 AND home_goal < away_goal THEN 'Chelsea away win!'
    ELSE 'Loss or tie' 
  END AS outcome
FROM match
WHERE hometeam_id = 8455 OR awayteam_id = 8455;
```

To filter a query by a CASE statement, you can include the entire CASE statement, except its alias, within the WHERE clause. You can, for example, exclude null values using `END IS NOT NULL`.

```sql
SELECT date, season, 
  CASE 
    WHEN hometeam_id = 8455 AND home_goal > away_goal THEN 'Chelsea home win!'
    WHEN awayteam_id = 8455 AND home_goal < away_goal THEN 'Chelsea away win!'  
  END AS outcome
FROM match
WHERE 
  CASE 
    WHEN hometeam_id = 8455 AND home_goal > away_goal THEN 'Chelsea home win!'
    WHEN awayteam_id = 8455 AND home_goal < away_goal THEN 'Chelsea away win!'  
  END IS NOT NULL;
```

**Exercises:**

**In CASE of rivalry**

Barcelona and Real Madrid have been rival teams for more than 80 years. Matches between these two teams are given the name El Clásico (The Classic). In this exercise, you will query a list of matches played between these two rivals.

You will notice in Step 2 that when you have multiple logical conditions in a CASE statement, you may quickly end up with a large number of WHEN clauses to logically test every outcome you are interested in. It's important to make sure you don't accidentally exclude key information in your ELSE clause.

In this exercise, you will retrieve information about matches played between Barcelona (id = 8634) and Real Madrid (id = 8633). Note that the query you are provided with already identifies the Clásico matches using a filter in the WHERE clause.

**Instructions:**

- Complete the first CASE statement, identifying Barcelona or Real Madrid as the home team using the hometeam_id column.

- Complete the second CASE statement in the same way, using awayteam_id.

```sql
SELECT 
    date,
    -- Identify the home team as Barcelona or Real Madrid
    CASE WHEN hometeam_id = 8634 THEN 'FC Barcelona' 
        ELSE 'Real Madrid CF' END AS home,
    -- Identify the away team as Barcelona or Real Madrid
    CASE WHEN awayteam_id = 8634 THEN 'FC Barcelona' 
        ELSE 'Real Madrid CF' END AS away
FROM matches_spain
WHERE (awayteam_id = 8634 OR hometeam_id = 8634)
    AND (awayteam_id = 8633 OR hometeam_id = 8633);
```

- Construct the final CASE statement identifying who won each match. Note there are 3 possible outcomes, but 5 conditions that you need to identify.

- Fill in the logical operators to identify Barcelona or Real Madrid as the winner.

```sql
SELECT 
    date,
    CASE WHEN hometeam_id = 8634 THEN 'FC Barcelona' 
        ELSE 'Real Madrid CF' END as home,
    CASE WHEN awayteam_id = 8634 THEN 'FC Barcelona' 
        ELSE 'Real Madrid CF' END as away,
    -- Identify all possible match outcomes
    CASE WHEN home_goal > away_goal AND hometeam_id = 8634 THEN 'Barcelona win!'
        WHEN home_goal > away_goal AND hometeam_id = 8633 THEN 'Real Madrid win!'
        WHEN home_goal < away_goal AND awayteam_id = 8634 THEN 'Barcelona win!'
        WHEN home_goal < away_goal AND awayteam_id = 8633 THEN 'Real Madrid win!'
        ELSE 'Tie!' END AS outcome
FROM matches_spain
WHERE (awayteam_id = 8634 OR hometeam_id = 8634)
    AND (awayteam_id = 8633 OR hometeam_id = 8633);
```

**Filtering your CASE statement**

Let's generate a list of matches won by Italy's Bologna team! There are quite a few additional teams in the two tables, so a key part of generating a usable query will be using your CASE statement as a filter in the WHERE clause.

CASE statements allow you to categorize data that you're interested in -- and exclude data you're not interested in. In order to do this, you can use a CASE statement as a filter in the WHERE statement to remove output you don't want to see.

Here is how you might set that up:
```sql
SELECT *
FROM table
WHERE 
    CASE WHEN a > 5 THEN 'Keep'
         WHEN a <= 5 THEN 'Exclude' END = 'Keep';
```
In essence, you can use the CASE statement as a filtering column like any other column in your database. The only difference is that you don't alias the statement in WHERE.

**Instructions:**

- Identify Bologna's team ID listed in the teams_italy table by selecting the team_long_name and team_api_id.

```sql
-- Select team_long_name and team_api_id from team
SELECT
    team_long_name,
    team_api_id
FROM teams_italy
-- Filter for team long name
WHERE team_long_name = 'Bologna';
```

- Select the season and date that a match was played.

- Complete the CASE statement so that only Bologna's home and away wins are identified.

```sql
-- Select the season and date columns
SELECT 
  season,
  date,
  -- Identify when Bologna won a match
  CASE WHEN hometeam_id = 9857 
      AND home_goal > away_goal 
      THEN 'Bologna Win'
      WHEN awayteam_id = 9857 
      AND away_goal > home_goal 
      THEN 'Bologna Win' 
      END AS outcome
FROM matches_italy;
```

- Select the home_goal and away_goal for each match.

- Use the CASE statement in the WHERE clause to filter all NULL values generated by the statement in the previous step.

```sql
-- Select the season, date, home_goal, and away_goal columns
SELECT 
    season,
    date,
    home_goal,
    away_goal
FROM matches_italy
WHERE 
-- Exclude games not won by Bologna
    CASE WHEN hometeam_id = 9857 AND home_goal > away_goal THEN 'Bologna Win'
        WHEN awayteam_id = 9857 AND away_goal > home_goal THEN 'Bologna Win' 
        END IS NOT NULL;
```

# CASE WHEN with aggregate functions

**Personal notes:**

CASE statements can be used to create columns to categorize data and filter your data in the WHERE clause. You can also use CASE to aggregate data based on the result of a logical test.

**CASE WHEN with COUNT*

CASE statements are like any other column in your query, so you can include them inside an aggregate function. The difference begins in its THEN clause. Instead of returning a text string, you return the column that identifies the unique matching ID. When this CASE statement is inside the COUNT function, it counts each id returned by this CASE statement.

```sql
SELECT 
  season,
  COUNT(CASE WHEN hometeam_id = 8650 AND home_goal > away_goal THEN id END) AS home_wins
FROM match
GROUP BY season;
```

You can add a second CASE statement for the away team and group the query by season. When counting information in a CASE statement, you can return whatever you want - a number, text string, or any column in the table. SQL is counting the number of rows returned by the CASE statement.

```sql
SELECT 
  season,
  COUNT(CASE WHEN hometeam_id = 8650 AND home_goal > away_goal THEN id END) AS home_wins,
  COUNT(CASE WHEN awayteam_id = 8650 AND away_goal > home_goal THEN 'some random text' END) AS away_wins
FROM match
GROUP BY season;
```

**CASE WHEN with SUM*

Similarly, you can use the SUM function to calculate a total of any value. For example, let's say we are interested in the number of home and away goals that Liverpool scored in each season.

```sql
SELECT
  season,
  SUM(CASE WHEN hometeam_id = 8650 THEN home_goal END) AS home_goals,
  SUM(CASE WHEN awayteam_id = 8650 THEN away_goal END) AS away_goals
FROM match
GROUP BY season;
```

**CASE with AVG*

You can use the AVG function along with the CASE in two ways. First, you can calculate an average of data. This can be done using CASE in the same way we used the SUM function. You can also use it along with the ROUND function, placing it outside the aggregated CASE statement and including the number of decimal places at the end for easier reading of the values.

```sql
SELECT
  season,
  ROUND(AVG(CASE WHEN hometeam_id = 8650 THEN home_goal END), 2) AS avg_homegoals,
  ROUND(AVG(CASE WHEN awayteam_id = 8650 THEN away_goal END), 2) AS avg_awaygoals
FROM match
GROUP BY season;
```

The second key application of CASE with AVG is in percentage calculation. This requires a specific structure for your calculation to be accurate. For example, let's answer: What percentage of Liverpool's games did they win in each season?

```sql
SELECT
  season,
  AVG(CASE WHEN hometeam_id = 8455 AND home_goal > away_goal THEN 1
           WHEN hometeam_id = 8455 AND home_goal < away_goal THEN 0 END) AS pct_homewins,
  AVG(CASE WHEN awayteam_id = 8455 AND away_goal > home_goal THEN 1
           WHEN awayteam_id = 8455 AND away_goal < home_goal THEN 0 END) AS pct_awaywins
FROM match
GROUP BY season;
```

*You can add the ROUND function in this case as well to facilitate the reading of the results.

**Exercises:**

**COUNT using CASE WHEN**

Do the number of soccer matches played in a given European country differ across seasons? We will use the European Soccer Database to answer this question.

You will examine the number of matches played in 3 seasons within each country listed in the database. This is much easier to explore with each season's matches in separate columns. Using the country and unfiltered match table, you will count the number of matches played in each country during the 2012/2013, 2013/2014, and 2014/2015 match seasons.

**Instructions:**

- Create a CASE statement that identifies the id of matches played in the 2012/2013 season. Specify that you want ELSE values to be NULL.

- Wrap the CASE statement in a COUNT function and group the query by the country alias.

```sql
SELECT 
  c.name AS country,
  -- Count games from the 2012/2013 season
  COUNT(CASE WHEN m.season = '2012/2013' 
          THEN m.id ELSE NULL END) AS matches_2012_2013
FROM country AS c
LEFT JOIN match AS m
ON c.id = m.country_id
-- Group by country name alias
GROUP BY country;
```

- Create 3 CASE WHEN statements counting the matches played in each country across the 3 seasons.

- END your CASE statement without an ELSE clause.

```sql
SELECT 
  c.name AS country,
  -- Count matches in each of the 3 seasons
  COUNT(CASE WHEN m.season = '2012/2013' THEN m.id END) AS matches_2012_2013,
  COUNT(CASE WHEN m.season = '2013/2014' THEN m.id END) AS matches_2013_2014,
  COUNT(CASE WHEN m.season = '2014/2015' THEN m.id END) AS matches_2014_2015
FROM country AS c
LEFT JOIN match AS m
ON c.id = m.country_id
-- Group by country name alias
GROUP BY country;
```

**COUNT and CASE WHEN with multiple conditions**

In R or Python, you have the ability to calculate a SUM of logical values (i.e., TRUE/FALSE) directly. In SQL, you have to convert these values into 1 and 0 before calculating a sum. This can be done using a CASE statement.

There's one key difference when using SUM to aggregate logical values compared to using COUNT in the previous exercise --

Your goal here is to use the country and match table to determine the total number of matches won by the home team in each country during the 2012/2013, 2013/2014, and 2014/2015 seasons.

**Instructions:**

- Create 3 CASE statements to "count" matches in the '2012/2013', '2013/2014', and '2014/2015' seasons, respectively.

- Have each CASE statement return a 1 for every match you want to include, and a 0 for every match to exclude.

- Wrap the CASE statement in a SUM to return the total matches played in each season.

- Group the query by the country name alias.

```sql
SELECT 
    c.name AS country,
    -- Sum the total records in each season where the home team won
    SUM(CASE WHEN m.season = '2012/2013' AND m.home_goal > m.away_goal 
        THEN 1 ELSE 0 END) AS matches_2012_2013,
    SUM(CASE WHEN m.season = '2013/2014' AND m.home_goal > m.away_goal 
        THEN 1 ELSE 0 END) AS matches_2013_2014,
    SUM(CASE WHEN m.season = '2014/2015' AND m.home_goal > m.away_goal 
        THEN 1 ELSE 0 END) AS matches_2014_2015
FROM country AS c
LEFT JOIN match AS m
ON c.id = m.country_id
-- Group by country name alias
GROUP BY country;
```

**Calculating percent with CASE and AVG**

CASE statements will return any value you specify in your THEN clause. This is an incredibly powerful tool for robust calculations and data manipulation when used in conjunction with an aggregate statement. One key task you can perform is using CASE inside an AVG function to calculate a percentage of information in your database.

Here's an example of how you set that up:

AVG(CASE WHEN condition_is_met THEN 1
         WHEN condition_is_not_met THEN 0 END)
With this approach, it's important to accurately specify which records count as 0, otherwise your calculations may not be correct!

Your task is to examine the number of wins, losses, and ties in each country. The matches table is filtered to include all matches from the 2013/2014 and 2014/2015 seasons.

**Instructions:**

- Create 3 CASE statements to COUNT the total number of home team wins, away team wins, and ties, which will allow you to examine the total number of records.

```sql
SELECT 
    c.name AS country,
    -- Count the home wins, away wins, and ties in each country
    COUNT(CASE WHEN m.home_goal > m.away_goal THEN m.id 
        END) AS home_wins,
    COUNT(CASE WHEN  m.home_goal < m.away_goal THEN m.id 
        END) AS away_wins,
    COUNT(CASE WHEN  m.home_goal = m.away_goal THEN m.id 
        END) AS ties
FROM country AS c
LEFT JOIN matches AS m
ON c.id = m.country_id
GROUP BY country;
```

- Calculate the percentage of matches tied using a CASE statement inside AVG.

- Fill in the logical operators for each statement. Alias your columns as ties_2013_2014 and ties_2014_2015, respectively.

```sql
SELECT 
c.name AS country,
-- Calculate the percentage of tied games in each season
  AVG(CASE WHEN m.season='2013/2014' AND m.home_goal = m.away_goal THEN 1
        WHEN m.season='2013/2014' AND m.home_goal != m.away_goal THEN 0
        END) AS ties_2013_2014,
  AVG(CASE WHEN m.season='2014/2015' AND m.home_goal = m.away_goal THEN 1
        WHEN m.season='2014/2015' AND m.home_goal != m.away_goal THEN 0
        END) AS ties_2014_2015
FROM country AS c
LEFT JOIN matches AS m
ON c.id = m.country_id
GROUP BY country;
```

- The previous "ties" columns returned values with 14 decimal points, which is not easy to interpret. Use the ROUND function to round to 2 decimal points.

```sql
SELECT 
c.name AS country,
-- Round the percentage of tied games to 2 decimal points
  ROUND(AVG(CASE WHEN m.season='2013/2014' AND m.home_goal = m.away_goal THEN 1
        WHEN m.season='2013/2014' AND m.home_goal != m.away_goal THEN 0
        END),2) AS pct_ties_2013_2014,
  ROUND(AVG(CASE WHEN m.season='2014/2015' AND m.home_goal = m.away_goal THEN 1
        WHEN m.season='2014/2015' AND m.home_goal != m.away_goal THEN 0
        END),2) AS pct_ties_2014_2015
FROM country AS c
LEFT JOIN matches AS m
ON c.id = m.country_id
GROUP BY country;
```

# Short and Simple Subqueries

**Chapter description:**

In this chapter, you will learn about subqueries in the SELECT, FROM, and WHERE clauses. You will gain an understanding of when subqueries are necessary to construct your dataset and where to best include them in your queries.

# WHERE are the Subqueries?

**Personal notes:**

A subquery is a nested query within another query. You can identify a subquery by looking for an additional SELECT statement enclosed in parentheses, surrounded by another complete SQL statement. Subqueries are used to retrieve the desired information when you need to perform some intermediate transformations on your data before selecting, filtering, or calculating information.

A subquery can be placed anywhere in your query, such as the SELECT, FROM, WHERE, or GROUP BY clause. The placement depends on how you want your final data to look. A subquery can return various information, such as scalar quantities or numbers. It can return a list to be used for filtering or joining information, or it can return a table to further extract and transform data.

**Why use subqueries?*

Subqueries allow you to compare summarized values with detailed data. They also enable you to structure or reshape your data for various purposes. Finally, they allow you to combine data from tables where a regular join might not be possible.

**Simple subqueries*

A simple subquery is a query nested within another query that can be executed on its own. For example, here's a subquery in the WHERE clause - if you copy the entire inner query, you could execute it on its own and get a result:

```sql
SELECT home_goal
FROM match
WHERE home_goal > (
    SELECT AVG(home_goal)
    FROM match
);
```

A simple subquery is evaluated once in the entire query. This means that SQL processes the information inside the subquery first, obtains the required information, and then moves on to process information in the outer query.

**Subqueries in the WHERE clause*

They are useful for filtering results based on information that you would have to calculate separately beforehand. For example, let's generate a list of games in the 2012/2013 season where the number of home goals scored was above the overall average.

```sql
SELECT date, hometeam_id, awayteam_id, home_goal, away_goal
FROM match
WHERE season = '2012/2013'
      AND home_goal > (SELECT AVG(home_goal) FROM match);
```

This way, you have one less manual step to perform before getting the necessary results.

**Subquery filtering list with IN*

Subqueries are also useful for generating a filtering list. For example, to answer the question, "Which teams are part of the league in Poland?" The 'team' table does not have the country IDs, but the 'match' table has both country IDs and team IDs. In this case, you generate a list to compare with the 'team_api_id' column in the WHERE clause.

```sql
SELECT
    team_long_name,
    team_short_name AS abbr
FROM team
WHERE
    team_api_id IN 
    (SELECT hometeam_id
     FROM match
     WHERE country_id = 15722);
```

**Exercises:**

**Filtering using scalar subqueries**

Subqueries are incredibly powerful for performing complex filters and transformations. You can filter data based on single, scalar values using a subquery in ways you cannot by using WHERE statements or joins. Subqueries can also be used for more advanced manipulation of your data set. You will likely encounter subqueries in any real-world setting that uses relational databases.

In this exercise, you will generate a list of matches where the total goals scored (for both teams in total) is more than 3 times the average for games in the matches_2013_2014 table, which includes all games played in the 2013/2014 season.

**Instructions:**

- Calculate triple the average home + away goals scored across all matches. This will become your subquery in the next step. Note that this column does not have an alias, so it will be called ?column? in your results.

```sql
-- Select the average of home + away goals, multiplied by 3
SELECT 
    3 * AVG(home_goal + away_goal)
FROM matches_2013_2014;
```

- Select the date, home goals, and away goals in the main query.

- Filter the main query for matches where the total goals scored exceed the value in the subquery.

```sql
SELECT 
    -- Select the date, home goals, and away goals scored
    date,
    home_goal,
    away_goal
FROM  matches_2013_2014
-- Filter for matches where total goals exceeds 3x the average
WHERE (home_goal + away_goal) > 
    (SELECT 3 * AVG(home_goal + away_goal)
        FROM matches_2013_2014); 
```

**Filtering using a subquery with a list**

Your goal in this exercise is to generate a list of teams that never played a game in their home city. Using a subquery, you will generate a list of unique hometeam_ID values from the unfiltered match table to exclude in the team table's team_api_ID column.

In addition to filtering using a single-value (scalar) subquery, you can create a list of values in a subquery to filter data based on a complex set of conditions. This type of subquery generates a one column reference list for the main query. As long as the values in your list match a column in your main query's table, you don't need to use a join -- even if the list is from a separate table.

**Instructions:**

- Create a subquery in the WHERE clause that retrieves all unique hometeam_ID values from the match table.

- Select the team_long_name and team_short_name from the team table. Exclude all values from the subquery in the main query.

```sql
SELECT 
    -- Select the team long and short names
    team_long_name,
    team_short_name
FROM team
-- Exclude all values from the subquery
WHERE team_api_id NOT IN
    (SELECT DISTINCT hometeam_ID  FROM match);
```

**Filtering with more complex subquery conditions**

In the previous exercise, you generated a list of teams that have no home matches listed in the soccer database using a subquery in WHERE. Let's do some further exploration in this database by creating a list of teams that scored 8 or more goals in a home match.

In order to do this, you will construct a subquery in the WHERE statement with its own filtering condition.

**Instructions:**

- Create a subquery in WHERE clause that retrieves all hometeam_ID values from match with a home_goal score greater than or equal to 8.

- Select the team_long_name and team_short_name from the team table. Include all values from the subquery in the main query.

```sql
SELECT
    -- Select the team long and short names
    team_long_name,
    team_short_name
FROM team
-- Filter for teams with 8 or more home goals
WHERE team_api_id IN
    (SELECT hometeam_ID 
    FROM match
    WHERE home_goal >= 8);
```

# Subqueries in FROM

**Personal notes:**

Subqueries in the FROM statement are a powerful tool for restructuring and transforming your data. Often, the data you need to answer a question is not yet in the required format for direct querying, and it requires some additional processing to prepare it for analysis. For example, you might want to reshape your data or pre-filter it before performing calculations. They are also useful when calculating aggregates of aggregated information.

**FROM subqueries*

Let's examine the average home goals for each team in the database. First, we create the query that will become your subquery, selecting the 'team_long_name' from the 'team' table and the AVG of the 'home_goal' column from the 'match' table. The 'team' table is joined with the 'match' table using a LEFT JOIN on 'hometeam_id,' which will give you the home team's ID. The query is then filtered by season and grouped by team.

```sql
SELECT
    t.team_long_name AS team,
    AVG(m.home_goal) AS home_avg
FROM match AS m
LEFT JOIN team AS t
ON m.hometeam_id = t.team_api_id
WHERE season = '2011/2012'
GROUP BY team;
```

To get only the top team as the final result, you simply place this query without the semicolon inside the FROM statement of an outer query, remembering to name an alias. Then add it to the main query, selecting the 'team' and 'home_avg' columns from the subquery. Finally, order by 'home_avg' in descending order and limit the query to 3 results.

```sql
SELECT team, home_avg
FROM (SELECT
        t.team_long_name AS team,
        AVG(m.home_goal) AS home_avg
      FROM match AS m
      LEFT JOIN team AS t
      ON m.hometeam_id = t.team_api_id
      WHERE season = '2011/2012'
      GROUP BY team) AS subquery
ORDER BY home_avg DESC
LIMIT 3;
```

**Important to remember*

There are a few important things to remember when using subqueries in the FROM statement. First, you have the ability to create more than one subquery in the FROM statement of any main query. When doing so, make sure to give each subquery an alias and ensure that you can join them to each other, just as you would when querying a table in your database. Second, you can join a subquery to any existing table in your database. However, you need to make sure you have a column in the subquery that you can use with the JOIN you want to perform.

**Exercises:**

**Joining Subqueries in FROM**

The match table in the European Soccer Database does not contain country or team names. You can get this information by joining it to the country table, and use this to aggregate information, such as the number of matches played in each country.

If you're interested in filtering data from one of these tables, you can also create a subquery from one of the tables, and then join it to an existing table in the database. A subquery in FROM is an effective way of answering detailed questions that requires filtering or transforming data before including it in your final results.

Your goal in this exercise is to generate a subquery using the match table, and then join that subquery to the country table to calculate information about matches with 10 or more goals in total!

**Instructions:**

- Create the subquery to be used in the next step, which selects the country ID and match ID (id) from the match table.

- Filter the query for matches with greater than or equal to 10 goals.

```sql
SELECT 
    -- Select the country ID and match ID
    country_id, 
    id 
FROM match
-- Filter for matches with 10 or more goals in total
WHERE (home_goal + away_goal) >= 10;
```

- Construct a subquery that selects only matches with 10 or more total goals.

- Inner join the subquery onto country in the main query.

- Select name from country and count the id column from match.

```sql
SELECT
    -- Select country name and the count match IDs
    name AS country_name,
    COUNT(sub.id) AS matches
FROM country AS c
-- Inner join the subquery onto country
-- Select the country id and match id columns
INNER JOIN (SELECT country_id, id 
        FROM match
        -- Filter the subquery by matches with 10+ goals
        WHERE (home_goal + away_goal) >= 10) AS sub
ON c.id = sub.country_id
GROUP BY country_name;
```

**Building on Subqueries in FROM**

In the previous exercise, you found that England, Netherlands, Germany and Spain were the only countries that had matches in the database where 10 or more goals were scored overall. Let's find out some more details about those matches -- when they were played, during which seasons, and how many of the goals were home versus away goals.

You'll notice that in this exercise, the table alias is excluded for every column selected in the main query. This is because the main query is extracting data from the subquery, which is treated as a single table.

**Instructions:**

- Complete the subquery inside the FROM clause. Select the country name from the country table, along with the date, the home goal, the away goal, and the total goals columns from the match table.

- Create a column in the subquery that adds home and away goals, called total_goals. This will be used to filter the main query.

- Select the country, date, home goals, and away goals in the main query.

- Filter the main query for games with 10 or more total goals.

```sql
SELECT
    -- Select country, date, home, and away goals from the subquery
    country,
    date,
    home_goal,
    away_goal
FROM 
    -- Select country name, date, home_goal, away_goal, and total goals in the subquery
    (SELECT name AS country, 
            m.date, 
            m.home_goal, 
            m.away_goal,
        (m.home_goal + m.away_goal) AS total_goals
    FROM match AS m
    LEFT JOIN country AS c
    ON m.country_id = c.id) AS subq
-- Filter by total goals scored in the main query
WHERE total_goals >= 10;
```

# Subqueries in SELECT

**Personal notes:**

Subqueries in the SELECT statement are used to return a single aggregated value. This can be helpful when you cannot include an aggregated value in an ungrouped SQL query. They are also useful for performing complex mathematical calculations on information in your dataset.

**Example:*

Let's say we want to create a column to compare the total number of matches played in each season to the overall total number of matches played. We can first calculate the overall match count, which is 12,837.

```sql
SELECT COUNT(id) FROM match;
```

We can then add this single number to the SELECT statement, producing the following results. Alternatively, we can skip this step and add the subquery directly to the SELECT statement to get identical results.

```sql
SELECT
    season,
    COUNT(id) AS matches,
    (SELECT COUNT(id) FROM match) AS total_matches
FROM match
GROUP BY season;
```

**SELECT subqueries for mathematical calculations*

The single value returned by a subquery in SELECT can be used to calculate information based on existing information in a database. For example, the overall average number of goals scored in a match in all seasons is 2. If you want to calculate the difference from the average in any match, you can calculate this number in advance in a separate query and insert the value into the SELECT statement. Alternatively, you can use a subquery that calculates this value in a subquery in the SELECT statement and subtract it from the total goals in that match. Overall, this second option can save a lot of time and errors in your work, and the results are identical to manually performed calculations.

```sql
SELECT 
    date,
    (home_goal + away_goal) AS goals,
    (home_goal + away_goal) -
        (SELECT AVG(home_goal + away_goal)
        FROM match
        WHERE season = '2011/2012') AS diff
FROM match
WHERE season = '2011/2012';
```

There are some unique considerations when working with subqueries in SELECT. The first is that the subquery needs to return a single value. If the result of your subquery returns multiple rows, your entire query will generate an error. This is because the information retrieved in a SELECT query is applied identically to each row in the dataset, and that's not possible if there is more than one unit of information. The second thing to keep an eye on is the correct placement of your data filters in the main query and the subquery. Since the subquery is processed before the main query, you'll need to include relevant filters in the subquery, just like in the main query.

**Exercises:**

**Add a subquery to the SELECT clause**

Subqueries in SELECT statements generate a single value that allow you to pass an aggregate value down a data frame. This is useful for performing calculations on data within your database.

In the following exercise, you will construct a query that calculates the average number of goals per match in each country's league.

- In the subquery, select the average total goals by adding home_goal and away_goal.

- Filter the results so that only the average of goals in the 2013/2014 season is calculated.

- In the main query, select the average total goals by adding home_goal and away_goal. This calculates the average goals for each league.

- Filter the results in the main query the same way you filtered the subquery. Group the query by the league name.

```sql
SELECT 
    l.name AS league,
    -- Select and round the league's total goals
    ROUND(AVG(m.home_goal + m.away_goal), 2) AS avg_goals,
    -- Select & round the average total goals for the season
    (SELECT ROUND(AVG(home_goal + away_goal), 2) 
    FROM match
    WHERE season = '2013/2014') AS overall_avg
FROM league AS l
LEFT JOIN match AS m
ON l.country_id = m.country_id
-- Filter for the 2013/2014 season
WHERE season = '2013/2014'
GROUP BY l.name;
```

**Subqueries in Select for Calculations**

Subqueries in SELECT are a useful way to create calculated columns in a query. A subquery in SELECT can be treated as a single numeric value to use in your calculations. When writing queries in SELECT, it's important to remember that filtering the main query does not filter the subquery -- and vice versa.

In the previous exercise, you created a column to compare each league's average total goals to the overall average goals in the 2013/2014 season. In this exercise, you will add a column that directly compares these values by subtracting the overall average from the subquery.

**Instructions:**

- Select the average goals scored in a match for each league in the main query.

- Select the average goals scored in a match overall for the 2013/2014 season in the subquery.

- Subtract the subquery from the average number of goals calculated for each league.

- Filter the main query so that only games from the 2013/2014 season are included.

```sql
SELECT
    -- Select the league name and average goals scored
    name AS league,
    ROUND(AVG(m.home_goal + m.away_goal),2) AS avg_goals,
    -- Subtract the overall average from the league average
    ROUND(AVG(m.home_goal + m.away_goal) - 
        (SELECT AVG(home_goal + away_goal)
        FROM match 
        WHERE season = '2013/2014'),2) AS diff
FROM league AS l
LEFT JOIN match AS m
ON l.country_id = m.country_id
-- Only include 2013/2014 results
WHERE season = '2013/2014'
GROUP BY l.name;
```

# Subqueries Everywhere! And Best Practices!

**Personal notes:**

In SQL, you can include as many simple subqueries as necessary in various clauses in your query. However, your queries can quickly become long and hard to read.

**Format your queries*

A best practice you can start with in your SQL journey is to format your queries correctly. It's essential to properly align your SELECT, FROM, GROUP BY, WHERE, and all the information contained in them. It's also considered a best practice to annotate your queries with comments to tell the user what it does—inside a slash, asterisk, and ending with an asterisk and a slash (/* comment */). You can also use inline comments using two dashes (-- comment). Each information after an inline comment is treated as text, even if it's a recognized SQL command.

**Indent your queries*

Make sure you correctly indent all the information contained in a subquery. This way, you can easily return to the query and understand what information is being processed first, where you need to apply changes, such as a date range, and what you can expect from the results if you make those changes. Ensure you clearly indent all information that is part of a single column, such as a long CASE statement or a complicated subquery in SELECT.

Overall, you can read the Holywell SQL Style Guide to get a sense of all the formatting conventions when working with SQL queries.

**Is that subquery necessary?*

When deciding whether or not you need a subquery, it's important to know that each added subquery requires additional computational power to generate its results. Depending on the size of your database and the number of records you extract in your query, you might significantly increase the time needed to execute it.

Finally, when building a main query with multiple subqueries, ensure that your filters are placed correctly in each subquery and in the main query to generate accurate results.

**Exercises:**

**ALL the subqueries EVERYWHERE**

In soccer leagues, games are played at different stages. Winning teams progress from one stage to the next, until they reach the final stage. In each stage, the stakes become higher than the previous one. The match table includes data about the different stages that each match took place in.

In this lesson, you will build a final query across 3 exercises that will contain three subqueries -- one in the SELECT clause, one in the FROM clause, and one in the WHERE clause. In the final exercise, your query will extract data examining the average goals scored in each stage of a match. Does the average number of goals scored change as the stakes get higher from one stage to the next?

**Instructions:**

- Extract the average number of home and away team goals in two SELECT subqueries.

- Calculate the average home and away goals for the specific stage in the main query.

- Filter both subqueries and the main query so that only data from the 2012/2013 season is included.

- Group the query by the m.stage column.

```sql
SELECT 
    -- Select the stage and average goals for each stage
    m.stage,
    ROUND(AVG(m.home_goal + m.away_goal),2) AS avg_goals,
    -- Select the average overall goals for the 2012/2013 season
    ROUND((SELECT AVG(home_goal + away_goal) 
        FROM match 
        WHERE season = '2012/2013'),2) AS overall
FROM match AS m
-- Filter for the 2012/2013 season
WHERE season = '2012/2013'
-- Group by stage
GROUP BY m.stage;
```

**Add a subquery in FROM**

In the previous exercise, you created a data set listing the average home and away goals in each match stage of the 2012/2013 match season.

In this next step, you will turn the main query into a subquery to extract a list of stages where the average home goals in a stage is higher than the overall average for home goals in a match.

**Instructions:**

- Calculate the average home goals and average away goals from the match table for each stage in the FROM clause subquery.

- Add a subquery to the WHERE clause that calculates the overall average home goals.

- Filter the main query for stages where the average home goals is higher than the overall average.

- Select the stage and avg_goals columns from the s subquery into the main query.

```sql
SELECT 
    -- Select the stage and average goals from the subquery
    stage,
    ROUND(avg_goals,2) AS avg_goals
FROM 
    -- Select the stage and average goals in 2012/2013
    (SELECT
        stage,
        AVG(home_goal + away_goal) AS avg_goals
    FROM match
    WHERE season = '2012/2013'
    GROUP BY stage) AS s
WHERE 
    -- Filter the main query using the subquery
    s.avg_goals > (SELECT AVG(home_goal + away_goal) 
                    FROM match WHERE season = '2012/2013');
```

**Add a subquery in SELECT**

In the previous exercise, you added a subquery to the FROM statement and selected the stages where the number of average goals in a stage exceeded the overall average number of goals in the 2012/2013 match season. In this final step, you will add a subquery in SELECT to compare the average number of goals scored in each stage to the total.

**Instructions:**

- Create a subquery in SELECT that yields the average goals scored in the 2012/2013 season. Name the new column overall_avg.

- Create a subquery in FROM that calculates the average goals scored in each stage during the 2012/2013 season.

- Filter the main query for stages where the average goals exceeds the overall average in 2012/2013.

```sql
SELECT 
    -- Select the stage and average goals from s
    stage,
    ROUND(s.avg_goals,2) AS avg_goal,
    -- Select the overall average for 2012/2013
    (SELECT AVG(home_goal + away_goal) FROM match WHERE season = '2012/2013') AS overall_avg
FROM 
    -- Select the stage and average goals in 2012/2013 from match
    (SELECT
        stage,
        AVG(home_goal + away_goal) AS avg_goals
    FROM match
    WHERE season = '2012/2013'
    GROUP BY stage) AS s
WHERE 
    -- Filter the main query using the subquery
    s.avg_goals > (SELECT AVG(home_goal + away_goal) 
                    FROM match WHERE season = '2012/2013');
```

# Correlated Queries, Nested Queries, and Common Table Expressions

**Chapter description:**

In this chapter, you will learn how to use nested and correlated subqueries to extract more complex data from a relational database. You will also learn about common table expressions and how to best construct queries using multiple common table expressions.

# Correlated subqueries

**Personal notes:**

Correlated subqueries are a special type of subquery that uses values from the outer query to generate the final results. The subquery is executed again each time a new row in the final dataset is returned, properly generating each new piece of information. Correlated subqueries are used for special types of calculations, such as advanced joining, filtering, and evaluating data in the database.

**A Simple Example*

In the previous chapter, you completed an exercise that answered the question "Which stages of the match, where the odds increase in each stage, tend to have a number of goals scored above average?" We did this using three simple subqueries in the SELECT, FROM, and WHERE statements. However, the same output can also be produced with a correlated subquery.

This query has only one difference: instead of including a filter for the season, the WHERE clause filters the data where the stage and match from the outer table were extracted from the subquery in FROM, is greater than the overall average generated in the WHERE subquery. The entire WHERE statement is essentially saying, "Return stages where the values in the subquery are greater than the average."
```sql
SELECT
	s.stage,
	ROUND(s.avg_goals,2) AS avg_goal,
	(SELECT AVG(home_goal + away_goal)
	FROM match
	WHERE season = '2012/2013') AS overall_avg
FROM
	(SELECT
		stage,
		AVG(home_goal + away_goal) AS avg_goals
	FROM match
	WHERE season = '2012/2013'
	GROUP BY stage) AS s
WHERE s.avg_goals > (SELECT AVG(home_goal + away_goal)
					FROM match AS m
					WHERE s.stage > m.stage);
```
**Simple vs. Correlated Subqueries*

Simple subqueries can be used in extracting, structuring, or filtering information and can run independently of the main query. On the other hand, a correlated subquery cannot run on its own because it depends on values from the main query. Also, a simple subquery is evaluated once throughout the statement. A correlated subquery is evaluated in loops—once for each row generated by the dataset. This means that adding correlated subqueries will make your query's performance slower, as your query is recalculating information repeatedly.

Another example, let's answer the question: "What is the average number of goals scored in each country across all seasons of games?" You simply join the match table to the country table on the id, extract the country name, take an average of the goals scored, and group the entire query by the country name, generating one row with an average value per country.
```sql
SELECT
	c.name AS country,
	AVG(m.home_goal + m.away_goal) AS avg_goals
FROM country AS c
LEFT JOIN match AS m
ON c.id = m.country_id
GROUP BY country;
```
A correlated subquery can be used here instead of a join:
```sql
SELECT
	c.name AS country,
	(SELECT 
		AVG(home_goal + away_goal)
	FROM match AS m
	WHERE m.country_id = c.id) AS avg_goals
FROM country AS c
GROUP BY country;
```

**Exercises:**

**Basic Correlated Subqueries**

Correlated subqueries are subqueries that reference one or more columns in the main query. Correlated subqueries depend on information in the main query to run, and thus, cannot be executed on their own.

Correlated subqueries are evaluated in SQL once per row of data retrieved -- a process that takes a lot more computing power and time than a simple subquery.

In this exercise, you will practice using correlated subqueries to examine matches with scores that are extreme outliers for each country -- above 3 times the average score!

**Instructions:**

- Select the country_id, date, home_goal, and away_goal columns in the main query.

- Complete the AVG value in the subquery.

- Complete the subquery column references, so that country_id is matched in the main and subquery.

```sql
SELECT 
    -- Select country ID, date, home, and away goals from match
    main.country_id,
    date,
    main.home_goal, 
    main.away_goal
FROM match AS main
WHERE 
    -- Filter the main query by the subquery
    (home_goal + away_goal) > 
        (SELECT AVG((sub.home_goal + sub.away_goal) * 3)
        FROM match AS sub
        -- Join the main query to the subquery in WHERE
        WHERE main.country_id = sub.country_id);
```

**Correlated subquery with multiple conditions**

Correlated subqueries are useful for matching data across multiple columns. In the previous exercise, you generated a list of matches with extremely high scores for each country. In this exercise, you're going to add an additional column for matching to answer the question -- what was the highest scoring match for each country, in each season?

*Note: this query may take a while to load.

**Instructions:**

- Select the country_id, date, home_goal, and away_goal columns in the main query.

- Complete the subquery: Select the matches with the highest number of total goals.

- Match the subquery to the main query using country_id and season.

- Fill in the correct logical operator so that total goals equals the max goals recorded in the subquery.

```sql
SELECT 
    -- Select country ID, date, home, and away goals from match
    main.country_id,
    main.date,
    main.home_goal,
    main.away_goal
FROM match AS main
WHERE 
    -- Filter for matches with the highest number of goals scored
    (home_goal + away_goal) = 
        (SELECT MAX(sub.home_goal + sub.away_goal)
        FROM match AS sub
        WHERE main.country_id = sub.country_id
            AND main.season = sub.season);
```

# Nested subqueries

**Personal notes:**

Nested subqueries are exactly what they sound like—subqueries nested within other subqueries.

**Inner Subquery*

For example, let's answer a similar question with an additional layer—"How does the total goals for each month differ from the monthly average of goals scored?" The logic for the inner subquery is: first, select the sum of goals scored in each month. The month is queried using the EXTRACT function.
```sql
SELECT
	EXTRACT(MONTH from date) AS month,
	SUM(home_goal + away_goal) AS goals
FROM match
GROUP BY month;
```

**Outer Subquery*

Next, you can place the second outer subquery to calculate an average of the values in the previous table, giving you the monthly average of goals scored. Since this result is a scalar subquery, you can now place it in the main query to calculate the final dataset.
```sql
SELECT AVG(goals)
FROM (SELECT
		EXTRACT(MONTH from date) AS month,
		AVG(home_goal + away_goal) AS goals
	FROM match
	GROUP BY month) AS s;
```

**Final Query*

Finally, you can place the entire nested subquery in the SELECT statement, giving you a scalar value to compare with the sum of goals scored in each month.
```sql
SELECT
	EXTRACT(MONTH from date) AS month,
	SUM(m.home_goal + m.away_goal) AS total_goals,
	SUM(m.home_goal + m.away_goal) -
		(SELECT AVG(goals)
		FROM (SELECT
				EXTRACT(MONTH from date) AS month,
				SUM(home_goal + away_goal) AS goals
				FROM match
				GROUP BY month) AS s) AS diff
FROM match as m
GROUP BY month;
```

**Correlated Nested Subqueries*

It's also important to note that nested queries can be correlated or not. It can also be a combination of both. Each of the correlated subqueries can reference information from an outer subquery or the main query.

For example, this query answers the question: What is the average number of goals scored by each country in a match in the 2011/2012 season? It is quite similar to the example from the previous chapter, except it requires an additional step. It has a second nested subquery within the SELECT statement, and the outer subquery has a correlated statement with the main query.
```sql
SELECT
	c.name AS country,
	(SELECT AVG(home_goal + away_goal)
	FROM match AS m
	WHERE m.country_id = c.id 
		AND id IN (
			SELECT id
			FROM match
			WHERE season = '2011/2012')) AS avg_goals
FROM country AS c
GROUP BY country;
```

**Exercises:**

**Nested simple subqueries**

Nested subqueries can be either simple or correlated.

Just like an unnested subquery, a nested subquery's components can be executed independently of the outer query, while a correlated subquery requires both the outer and inner subquery to run and produce results.

In this exercise, you will practice creating a nested subquery to examine the highest total number of goals in each season, overall, and during July across all seasons.

**Instructions:**

- Complete the main query to select the season and the max total goals in a match for each season. Name this max_goals.

- Complete the first simple subquery to select the max total goals in a match across all seasons. Name this overall_max_goals.

- Complete the nested subquery to select the maximum total goals in a match played in July across all seasons.

- Select the maximum total goals in the outer subquery. Name this entire subquery july_max_goals.

```sql
SELECT
    -- Select the season and max goals scored in a match
    season,
    MAX(home_goal + away_goal) AS max_goals,
    -- Select the overall max goals scored in a match
(SELECT MAX(home_goal + away_goal) FROM match) AS overall_max_goals,
-- Select the max number of goals scored in any match in July
(SELECT MAX(home_goal + away_goal) 
    FROM match
    WHERE id IN (
        SELECT id FROM match WHERE EXTRACT(MONTH FROM date) = 07)) AS july_max_goals
FROM match
GROUP BY season;
```

**Nest a subquery in FROM**

What's the average number of matches per season where a team scored 5 or more goals? How does this differ by country?

Let's use a nested, correlated subquery to perform this operation. In the real world, you will probably find that nesting multiple subqueries is a task you don't have to perform often. In some cases, however, you may find yourself struggling to properly group by the column you want, or to calculate information requiring multiple mathematical transformations (i.e., an AVG of a COUNT).

Nesting subqueries and performing your transformations one step at a time, adding it to a subquery, and then performing the next set of transformations is often the easiest way to yield accurate information about your data. Let's get to it!

**Instructions:**

- Generate a list of matches where at least one team scored 5 or more goals.

```sql
-- Select matches where a team scored 5+ goals
SELECT
    country_id,
    season,
    id
FROM match
WHERE home_goal >= 5 OR away_goal >= 5;
```

- Turn the query from the previous step into a subquery in the FROM statement.

- COUNT the match ids generated in the previous step, and group the query by country_id and season.

```sql
-- Count match ids
SELECT
    country_id,
    season,
    COUNT(id) AS matches
-- Set up and alias the subquery
FROM(
    SELECT
        country_id,
        season,
        id
    FROM match
    WHERE home_goal >= 5 OR away_goal >= 5)  AS subquery
-- Group by country_id and season
GROUP BY country_id, season;
```

- Finally, declare the same query from step 2 as a subquery in FROM with the alias outer_s.

- Left join it to the country table using the outer query's country_id column.

- Calculate an AVG of high scoring matches per country in the main query.

```sql
SELECT
    c.name AS country,
    -- Calculate the average matches per season
    AVG(outer_s.matches) AS avg_seasonal_high_scores
FROM country AS c
-- Left join outer_s to country
LEFT JOIN (
SELECT country_id, season,
        COUNT(id) AS matches
FROM (
    SELECT country_id, season, id
    FROM match
    WHERE home_goal >= 5 OR away_goal >= 5) AS inner_s
-- Close parentheses and alias the subquery
GROUP BY country_id, season) AS outer_s
ON c.id = outer_s.country_id
GROUP BY country;
```

# Common Table Expressions

**Personal notes:**

As seen, the queries we are constructing are quickly becoming long and complex. It can become difficult to clearly keep track of each piece of your query. We will cover a common method to improve the readability and accessibility of information in subqueries—the Common Table Expression (CTE).

Common Table Expressions, or CTEs, are a special type of subquery that is declared before your main query. Instead of including subqueries, say in the FROM statement, you name them using the WITH statement and then reference it by name later in the FROM statement as if it were any other table in your database.

```sql
WITH cte AS (
	SELECT col1, col2
	FROM table
)
SELECT
	AVG(col1) AS avg_col
FROM cte;
```

For example, let's rewrite a query from a previous exercise using a CTE. The following query uses a subquery, s, in the FROM statement to generate a list of country IDs and match IDs that meet certain criteria—specifically, we only wanted matches with 10 or more goals scored in total. This subquery is then joined to the countries table, and the count of matches in the subquery is counted in the main query.

To rewrite this query using a Common Table Expression to represent the subquery, simply remove the subquery from the FROM clause, place it at the beginning of the query, declare it using the WITH syntax, followed by a CTE name and AS.

```sql
WITH s AS (
	SELECT country_id, id
	FROM match
	WHERE (home_goal + away_goal) >= 10
)
```

Finally, complete the rest of the query just as you would if the CTE were an existing table in the database. You select the country name from the countries table, count the number of matches in the CTE "s", perform the join to the countries table, and then group the results by the country name alias.

```sql
WITH s AS (
	SELECT country_id, id
	FROM match
	WHERE (home_goal + away_goal) >= 10
)
SELECT
	c.name AS country,
	COUNT(s.id) AS matches
FROM country AS c
INNER JOIN s
ON c.id = s.country_id
GROUP BY country;
```

If you have multiple subqueries you want to turn into a Common Table Expression, you can simply list them one after the other, with a comma between each CTE, and without a comma after the last one. You can then retrieve the necessary information for the main query—just make sure to join properly to this second CTE as well.

```sql
WITH s1 AS (
	SELECT country_id, id
	FROM match
	WHERE (home_goal + away_goal) >= 10),
s2 AS (
	SELECT country_id, id
	FROM match
	WHERE (home_goal + away_goal) <= 1
)
SELECT
	c.name AS country,
	COUNT(s1.id) AS high_scores,
	COUNT(s2.id) AS low_scores
FROM country AS c
INNER JOIN s1
ON c.id = s1.country_id
INNER JOIN s2
ON c.id = s2.country_id
GROUP BY country;
```

**Why use CTEs?*

Common Table Expressions have several benefits over a subquery written within your main query. First, the CTE is executed only once and then stored in memory, usually leading to an improvement in the time required to execute your query. Second, CTEs are an excellent tool for organizing long and complex queries; you can declare as many CTEs as you need, one after the other. You can also reference information in CTEs declared earlier. For example, if you have 3 CTEs in a query, your third CTE can retrieve information from the first and second CTEs. Finally, a CTE can refer to itself in a special kind of table called a recursive CTE.

**Exercises:**

**Clean up with CTEs**

In chapter 2, you generated a list of countries and the number of matches in each country with more than 10 total goals. The query in that exercise utilized a subquery in the FROM statement in order to filter the matches before counting them in the main query. Below is the query you created:
```sql
SELECT
  c.name AS country,
  COUNT(sub.id) AS matches
FROM country AS c
INNER JOIN (
  SELECT country_id, id 
  FROM match
  WHERE (home_goal + away_goal) >= 10) AS sub
ON c.id = sub.country_id
GROUP BY country;
```
You can list one (or more) subqueries as common table expressions (CTEs) by declaring them ahead of your main query, which is an excellent tool for organizing information and placing it in a logical order.

In this exercise, let's rewrite a similar query using a CTE.

**Instructions:**

- Complete the syntax to declare your CTE.

- Select the country_id and match id from the match table in your CTE.

- Left join the CTE to the league table using country_id.

```sql
-- Set up your CTE
WITH match_list AS (
    SELECT 
        country_id, 
        id
    FROM match
    WHERE (home_goal + away_goal) >= 10)
-- Select league and count of matches from the CTE
SELECT
    l.name AS league,
    COUNT(match_list.id) AS matches
FROM league AS l
-- Join the CTE to the league table
LEFT JOIN match_list ON l.id = match_list.country_id
GROUP BY l.name;
```

**Organizing with CTEs**

Previously, you modified a query based on a statement you completed in chapter 2 using common table expressions.

This time, let's expand on the exercise by looking at details about matches with very high scores using CTEs. Just like a subquery in FROM, you can join tables inside a CTE.

**Instructions:**

- Declare your CTE, where you create a list of all matches with the league name.

- Select the league, date, home, and away goals from the CTE.

- Filter the main query for matches with 10 or more goals.

```sql
-- Set up your CTE
WITH match_list AS (
-- Select the league, date, home, and away goals
    SELECT 
        l.name AS league, 
        m.date, 
        m.home_goal, 
        m.away_goal,
    (m.home_goal + m.away_goal) AS total_goals
    FROM match AS m
    LEFT JOIN league as l ON m.country_id = l.id)
-- Select the league, date, home, and away goals from the CTE
SELECT league, date, home_goal, away_goal
FROM match_list
-- Filter by total goals
WHERE total_goals >= 10;
```

**CTEs with nested subqueries**

If you find yourself listing multiple subqueries in the FROM clause with nested statement, your query will likely become long, complex, and difficult to read.

Since many queries are written with the intention of being saved and re-run in the future, proper organization is key to a seamless workflow. Arranging subqueries as CTEs will save you time, space, and confusion in the long run!

**Instructions:**

- Declare a CTE that calculates the total goals from matches in August of the 2013/2014 season.

- Left join the CTE onto the league table using country_id from the match_list CTE.

- Filter the list on the inner subquery to only select matches in August of the 2013/2014 season.

```sql
-- Set up your CTE
WITH match_list AS (
    SELECT 
        country_id,
    (home_goal + away_goal) AS goals
    FROM match
    -- Create a list of match IDs to filter data in the CTE
    WHERE id IN (
    SELECT id
    FROM match
    WHERE season = '2013/2014' AND EXTRACT(MONTH FROM date) = 8))
-- Select the league name and average of goals in the CTE
SELECT 
    l.name,
    AVG(goals)
FROM league AS l
-- Join the CTE onto the league table
LEFT JOIN match_list ON l.id = match_list.country_id
GROUP BY l.name;
```

# Deciding on techniques to use

**Personal notes:**

**Joins*

Joins allow you to directly combine information from 2 or more tables and, on their own, are mainly limited to simple combinations and aggregations of tables already present in your database. Joins are a universally important skill when working with a database that has more than one table. It is fair to say that joins are necessary to understand each of the other techniques mentioned below.

**Correlated Subqueries*

A correlated subquery allows you to combine information between a subquery and a table or another subquery. It helps you simplify your syntax and overcome the limitations of a join, namely that you cannot join two separate columns in one table to a single column in another at a time. However, it's important to remember that correlated subqueries can take a long time to process and will decrease query performance. Correlated subqueries are great for combining data from different columns in one or more tables.

**Multiple/Nested Subqueries*

Multiple and nested subqueries are useful when your data requires multi-step transformations before it's in the format you need for your final query. Breaking down the steps of your query process allows for better accuracy and reproducibility in your work. Multiple subqueries are great for answering questions like "What is the average deal size closed by each sales representative in the last quarter," which would require several steps to transform and prepare before generating the final query.

**Common Table Expression (CTE)*

Common Table Expressions allow you to organize your subqueries sequentially by declaring them at the beginning of your query. As CTEs are processed one at a time before your main query, you can reference information from a CTE created earlier, serving as an alternative to nested subqueries. CTEs are excellent for comparing a large amount of disparate information. For example, to create a summary table examining the marketing, sales, growth, and performance of engineering teams and their key metrics in the last quarter. With CTEs, you can extract data about the performance of each team one after the other and combine them in a single query.

**So, Which Do I Use?*

Often, this really depends on the database you are using, the field you are working in, and the questions you are asking. In general, it is recommended that you practice each technique with your own databases to determine which allows you to use and reuse your queries effectively and generates clear and accurate results. Each technique has its strengths and use cases, and the choice depends on the specific requirements of your analysis.

**Exercises:**

**Get team names with a subquery**

Let's solve a problem we've encountered a few times in this course so far -- How do you get both the home and away team names into one final query result?

Out of the 4 techniques we just discussed, this can be performed using subqueries, correlated subqueries, and CTEs. Let's practice creating similar result sets using each of these 3 methods over the next 3 exercises, starting with subqueries in FROM.

**Instructions:**

- Create a query that left joins team to match in order to get the identity of the home team. This becomes the subquery in the next step.

```sql
SELECT 
    m.id, 
    t.team_long_name AS hometeam
-- Left join team to match
FROM match AS m
LEFT JOIN team as t
ON m.hometeam_id = team_api_id;
```

- Add a second subquery to the FROM statement to get the away team name, changing only the hometeam_id. Left join both subqueries to the match table on the id column.

```sql
SELECT
    m.date,
    -- Get the home and away team names
    home.hometeam,
    away.awayteam,
    m.home_goal,
    m.away_goal
FROM match AS m

-- Join the home subquery to the match table
LEFT JOIN (
SELECT match.id, team.team_long_name AS hometeam
FROM match
LEFT JOIN team
ON match.hometeam_id = team.team_api_id) AS home
ON home.id = m.id

-- Join the away subquery to the match table
LEFT JOIN (
SELECT match.id, team.team_long_name AS awayteam
FROM match
LEFT JOIN team
-- Get the away team ID in the subquery
ON match.awayteam_id = team.team_api_id) AS away
ON away.id = m.id;
```

**Get team names with correlated subqueries**

Let's solve the same problem using correlated subqueries -- How do you get both the home and away team names into one final query result?

This can easily be performed using correlated subqueries. But how might that impact the performance of your query? Complete the following steps and let's find out!

**Instructions:**

- Using a correlated subquery in the SELECT statement, match the team_api_id column from team to the hometeam_id from match.

```sql
SELECT
    m.date,
(SELECT team_long_name
    FROM team AS t
    -- Connect the team to the match table
    WHERE t.team_api_id = m.hometeam_id) AS hometeam
FROM match AS m;
```

- Create a second correlated subquery in SELECT, yielding the away team's name.

- Select the home and away goal columns from match in the main query.

```sql
SELECT
    m.date,
    (SELECT team_long_name
    FROM team AS t
    WHERE t.team_api_id = m.hometeam_id) AS hometeam,
    -- Connect the team to the match table
    (SELECT team_long_name
    FROM team AS t
    WHERE t.team_api_id = m.awayteam_id) AS awayteam,
    -- Select home and away goals
    m.home_goal,
    m.away_goal
FROM match AS m;
```

**Get team names with CTEs**

You've now explored two methods for answering the question, How do you get both the home and away team names into one final query result?

Let's explore the final method - common table expressions. Common table expressions are similar to the subquery method for generating results, mainly differing in syntax and the order in which information is processed.

**Instructions:**

- Select id from match and team_long_name from team. Join these two tables together on hometeam_id in match and team_api_id in team.

```sql
SELECT 
    -- Select match id and team long name
    m.id, 
    t.team_long_name AS hometeam
FROM match AS m
-- Join team to match using team_api_id and hometeam_id
LEFT JOIN team AS t 
ON m.hometeam_id = t.team_api_id;
```

- Declare the query from the previous step as a common table expression. SELECT everything from the CTE into the main query.

```sql
-- Declare the home CTE
WITH home AS (
    SELECT m.id, t.team_long_name AS hometeam
    FROM match AS m
    LEFT JOIN team AS t 
    ON m.hometeam_id = t.team_api_id)
-- Select everything from home
SELECT *
FROM home;
```

- Let's declare the second CTE, away. Join it to the first CTE on the id column.

- The date, home_goal, and away_goal columns have been added to the CTEs. SELECT them into the main query.

```sql
WITH home AS (
SELECT m.id, m.date, 
        t.team_long_name AS hometeam, m.home_goal
FROM match AS m
LEFT JOIN team AS t 
ON m.hometeam_id = t.team_api_id),
-- Declare and set up the away CTE
away AS (
SELECT m.id, m.date, 
        t.team_long_name AS awayteam, m.away_goal
FROM match AS m
LEFT JOIN team AS t 
ON m.awayteam_id = t.team_api_id)
-- Select date, home_goal, and away_goal
SELECT 
    home.date,
    home.hometeam,
    away.awayteam,
    home.home_goal,
    away.away_goal
-- Join away and home on the id column
FROM home
INNER JOIN away
ON home.id = away.id;
```

**Which technique to use?**

The previous three exercises demonstrated that, in many cases, you can use multiple techniques in SQL to answer the same question.

Based on what you learned, which of the following statements is false regarding differences in the use and performance of multiple/nested subqueries, correlated subqueries, and common table expressions?

        "Correlated subqueries can reduce the length of your query, which improves query run time."


# Window Functions

**Chapter description:**

You will learn about window functions and how to pass aggregate functions along a dataset. You will also learn how to calculate running totals and partitioned averages.

# It's OVER

**Personal notes:**

Window functions are a class of functions that perform calculations on a set of results that has already been generated, also known as a "window." You can use window functions to perform aggregated calculations without having to group your data, as was done in subqueries within the SELECT statement. They can also be used to calculate information such as running totals, rankings, and moving averages.

**Example 1: Comparing with Overall Average*

Let's revisit the question from chapter 2: "How many goals were scored in each match in 2011/2012, and how does it compare to the overall average?" Instead of using a subquery in SELECT, we can calculate the overall average of goals and compare each match using the OVER() clause. This simplifies the syntax and improves processing time:

```sql
SELECT
	date,
	(home_goal + away_goal) AS goals,
	AVG(home_goal + away_goal) OVER() AS overall_avg
FROM match
WHERE season = '2011/2012';
```

The results are identical to the approach with a subquery in SELECT from chapter 2, but the syntax is more straightforward, and the processing time is faster.

**Example 2: Creating a Ranking (RANK)*

The RANK clause creates a column numbering in the dataset, from highest to lowest or vice versa, based on a specified column. Let's use the same query from the previous example to answer the question: "What is the ranking of matches based on the number of goals scored?":

```sql
SELECT
	date,
	(home_goal + away_goal) AS goals,
	RANK() OVER (ORDER BY home_goal + away_goal) AS goals_rank
FROM match
WHERE season = '2011/2012';
```

By default, the RANK function orders the results and ranks them from the smallest to the largest value. If we want to reverse the order and rank the results from largest to smallest, we can add the DESC function:

```sql
SELECT
	date,
	(home_goal + away_goal) AS goals,
	RANK() OVER (ORDER BY home_goal + away_goal DESC) AS goals_rank
FROM match
WHERE season = '2011/2012';
```

**Key Differences:*

- Window functions are processed after the entire query, except for the final ORDER BY statement.
- They use the result set to calculate information instead of directly accessing the database.
- Window functions are available in PostgreSQL, Oracle, MySQL, but not in SQLite.

**Exercises:**

**The match is OVER**

The OVER() clause allows you to pass an aggregate function down a data set, similar to subqueries in SELECT. The OVER() clause offers significant benefits over subqueries in select -- namely, your queries will run faster, and the OVER() clause has a wide range of additional functions and clauses you can include with it that we will cover later on in this chapter.

In this exercise, you will revise some queries from previous chapters using the OVER() clause.

**Instructions:**

- Select the match ID, country name, season, home, and away goals from the match and country tables.

- Complete the query that calculates the average number of goals scored overall and then includes the aggregate value in each row using a window function.

```sql
SELECT 
    -- Select the id, country name, season, home, and away goals
    m.id, 
    c.name AS country, 
    m.season,
    m.home_goal,
    m.away_goal,
    -- Use a window to include the aggregate average in each row
    AVG(m.home_goal + m.away_goal) OVER() AS overall_avg
FROM match AS m
LEFT JOIN country AS c ON m.country_id = c.id;
```

**What's OVER here?**

Window functions allow you to create a RANK of information according to any variable you want to use to sort your data. When setting this up, you will need to specify what column/calculation you want to use to calculate your rank. This is done by including an ORDER BY clause inside the OVER() clause. Below is an example:
```sql
SELECT 
    id,
    RANK() OVER(ORDER BY home_goal) AS rank
FROM match;
```
In this exercise, you will create a data set of ranked matches according to which leagues, on average, score the most goals in a match.

**Instructions:**

- Select the league name and average total goals scored from league and match.

- Complete the window function so it calculates the rank of average goals scored across all leagues in the database.

- Order the rank by the average total of home and away goals scored.

```sql
        SELECT 
            -- Select the league name and average goals scored
            l.name AS league,
            AVG(m.home_goal + m.away_goal) AS avg_goals,
            -- Rank each league according to the average goals
            RANK() OVER(ORDER BY AVG(m.home_goal + m.away_goal)) AS league_rank
        FROM league AS l
        LEFT JOIN match AS m 
        ON l.id = m.country_id
        WHERE m.season = '2011/2012'
        GROUP BY l.name
        -- Order the query by the rank you created
        ORDER BY league_rank;
```

**Flip OVER your results**

In the last exercise, the rank generated in your query was organized from smallest to largest. By adding DESC to your window function, you can create a rank sorted from largest to smallest.

SELECT 
    id,
    RANK() OVER(ORDER BY home_goal DESC) AS rank
FROM match;

**Instructions:**

- Complete the same parts of the query as the previous exercise.

- Complete the window function to rank each league from highest to lowest average goals scored.

- Order the main query by the rank you just created.

```sql
SELECT 
    -- Select the league name and average goals scored
    l.name AS league,
    AVG(m.home_goal + m.away_goal) AS avg_goals,
    -- Rank leagues in descending order by average goals
    RANK() OVER(ORDER BY AVG(m.home_goal + m.away_goal) DESC) AS league_rank
FROM league AS l
LEFT JOIN match AS m 
ON l.id = m.country_id
WHERE m.season = '2011/2012'
GROUP BY l.name
-- Order the query by the rank you created
ORDER BY league_rank;
```

# OVER with a PARTITION

**Personal notes:**

An important statement you can add to your OVER clause is PARTITION BY. It allows you to calculate separate values for different categories established in a partition. This is a way to compute different aggregated values within a column of data and apply them to a dataset, rather than having to calculate them in different columns.

**PARTITION syntax*

Just like before, use an aggregate function to calculate, such as AVG of the home_goal column. Then add the OVER clause afterward and inside the parentheses, indicate PARTITION BY, followed by the column by which you want to partition the average. This will return the overall average for, or PARTITION BY, each season.

```sql
AVG(home_goal) OVER(PARTITION BY season)
```

**Example: Expanding the Question*

Using the query from the previous lesson, answering the question "How many goals were scored in each match, and how does it compare to the overall average?". This is done using the OVER clause, and the query returns the date, goals scored, and the overall average. Let's expand the previous question and, instead, ask "How many goals were scored in each match, and how does it compare to the season average?". We can do this by adding a PARTITION BY clause to the OVER clause from the previous slide:

```sql
SELECT
	date,
	(home_goal + away_goal) AS goals,
	AVG(home_goal + away_goal) OVER(PARTITION BY season) AS season_avg
FROM match;
```

Specifying "PARTITION BY season" returns the average for each season on each row, according to the season to which each record belongs.

**PARTITION BY multiple columns*

You can also use PARTITION to calculate values split across multiple columns. In the following query, the OVER clause contains two columns to partition the AVG goals scored – season and country. The result set returns the average of goals scored per season and country.

```sql
SELECT
	c.name,
	m.season,
	(home_goal + away_goal) AS goals,
	AVG(home_goal + away_goal) OVER(PARTITION BY m.season, c.name) AS season_ctry_avg
FROM country AS c
LEFT JOIN match AS m
ON c.id = m.country_id;
```

**PARTITION BY considerations*

You can partition calculations by 1 or more columns as needed to answer a question you might have. Additionally, you can use PARTITION with any type of window function.

**Exercises:**

**PARTITION BY a column**

The PARTITION BY clause allows you to calculate separate "windows" based on columns you want to divide your results. For example, you can create a single column that calculates an overall average of goals scored for each season.

In this exercise, you will be creating a data set of games played by Legia Warszawa (Warsaw League), the top ranked team in Poland, and comparing their individual game performance to the overall average for that season.

Where do you see more outliers? Are they Legia Warszawa's home or away games?

**Instructions:**

- Complete the two window functions that calculate the home and away goal averages. Partition the window functions by season to calculate separate averages for each season.

- Filter the query to only include matches played by Legia Warszawa, id = 8673.

```sql
SELECT
    date,
    season,
    home_goal,
    away_goal,
    CASE WHEN hometeam_id = 8673 THEN 'home' 
        ELSE 'away' END AS warsaw_location,
    -- Calculate the average goals scored partitioned by season
    AVG(home_goal) OVER(PARTITION BY season) AS season_homeavg,
    AVG(away_goal) OVER(PARTITION BY season) AS season_awayavg
FROM match
-- Filter the data set for Legia Warszawa matches only
WHERE 
    hometeam_id = 8673 
    OR awayteam_id = 8673 
ORDER BY (home_goal + away_goal) DESC;
```

**PARTITION BY multiple columns**

The PARTITION BY clause can be used to break out window averages by multiple data points (columns). You can even calculate the information you want to use to partition your data! For example, you can calculate average goals scored by season and by country, or by the calendar year (taken from the date column).

In this exercise, you will calculate the average number home and away goals scored Legia Warszawa, and their opponents, partitioned by the month in each season.

**Instructions:**

- Construct two window functions partitioning the average of home and away goals by season and month.

- Filter the dataset by Legia Warszawa's team ID (8673) so that the window calculation only includes matches involving them.

```sql
SELECT 
    date,
    season,
    home_goal,
    away_goal,
    CASE WHEN hometeam_id = 8673 THEN 'home' 
        ELSE 'away' END AS warsaw_location,
    -- Calculate average goals partitioned by season and month
    AVG(home_goal) OVER(PARTITION BY season, 
            EXTRACT(month FROM date)) AS season_mo_home,
    AVG(away_goal) OVER(PARTITION BY season, 
            EXTRACT(month FROM date)) AS season_mo_away
FROM match
WHERE 
    hometeam_id = 8673
    OR awayteam_id = 8673
ORDER BY (home_goal + away_goal) DESC;
```

# Sliding windows

**Personal notes:**

In addition to calculating aggregate and ranking information, window functions can also be used to compute information that changes with each subsequent row in a dataset. Sliding windows are functions that perform calculations relative to the current row of a dataset. You can use sliding windows to compute a wide range of information that aggregates over a single row in your dataset—performing totals, sums, counts, and averages in any order you need. A sliding window calculation can also be partitioned by one or more columns, similar to a regular window.

**Sliding Window Keywords*

A sliding window function contains specific keywords within the OVER clause to specify the data you want to use in your calculations. The general syntax uses the phrase ROWS BETWEEN to indicate that you plan to slice information in your window function for each row in the dataset, and then you specify the starting and ending point of the calculation.

```sql
ROWS BETWEEN <start> AND <finish>
```

To start and finish your ROWS BETWEEN statement, you can specify several keywords, as shown below:

- `PRECEDING`
- `FOLLOWING`
- `UNBOUNDED PRECEDING`
- `UNBOUNDED FOLLOWING`
- `CURRENT ROW`

`PRECEDING` and `FOLLOWING` are used to specify the number of rows before or after the current row that you want to include in a calculation. `UNBOUNDED PRECEDING` and `UNBOUNDED FOLLOWING` tell SQL that you want to include every row from the beginning or end of the dataset in your calculations. Finally, `CURRENT ROW` tells SQL that you want to stop your calculation at the current row.

**Sliding Window Example*

The sliding window in this query includes several important pieces of information in its calculation. It first states that the goal is to calculate a sum of goals scored when Manchester City played as the home team during the 2011/2012 season. It then informs that you want to turn this calculation into a running total, ordered by the match date from oldest to newest and calculated from the beginning of the dataset up to the current row.

```sql
SELECT
	date,
	home_goal,
	away_goal,
	SUM(home_goal) OVER(ORDER BY date ROWS BETWEEN 
		UNBOUNDED PRECEDING AND CURRENT ROW) AS running_total
FROM match
WHERE hometeam_id = 8456 AND season = '2011/2012';
```

Your resulting dataset has a column calculating the total number of goals scored throughout the season, with a final total listed on the last row.

**Sliding Window Frame*

Using the `PRECEDING` statement, you can also calculate sliding windows with a more limited frame. For example, the query below is similar to the previous one, with a slightly modified sliding window. The phrase `UNBOUNDED PRECEDING` is replaced with `1 PRECEDING`, which calculates the sum of goals for Manchester City in the current and previous match.

```sql
SELECT
	date,
	home_goal,
	away_goal,
	SUM(home_goal) OVER(ORDER BY date ROWS BETWEEN 
		1 PRECEDING AND CURRENT ROW) AS last2
FROM match
WHERE hometeam_id = 8456 AND season = '2011/2012';
```

**Exercises:**

**Slide to the left**

Sliding windows allow you to create running calculations between any two points in a window using functions such as PRECEDING, FOLLOWING, and CURRENT ROW. You can calculate running counts, sums, averages, and other aggregate functions between any two points you specify in the data set.

In this exercise, you will expand on the examples discussed in the video, calculating the running total of goals scored by the FC Utrecht when they were the home team during the 2011/2012 season. Do they score more goals at the end of the season as the home or away team?

**Instructions:**

- Complete the window function by:

- Assessing the running total of home goals scored by FC Utrecht.

- Assessing the running average of home goals scored.

- Ordering both the running average and running total by date.

```sql
SELECT 
    date,
    home_goal,
    away_goal,
    -- Create a running total and running average of home goals
    SUM(home_goal) OVER(ORDER BY date 
        ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS running_total,
    AVG(home_goal) OVER(ORDER BY date 
        ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS running_avg
FROM match
WHERE 
    hometeam_id = 9908 
    AND season = '2011/2012';
```

**Slide to the right**

Now let's see how FC Utrecht performs when they're the away team. You'll notice that the total for the season is at the bottom of the data set you queried. Depending on your results, this could be pretty long, and scrolling down is not very helpful.

In this exercise, you will slightly modify the query from the previous exercise by sorting the data set in reverse order and calculating a backward running total from the CURRENT ROW to the end of the data set (earliest record).

**Instructions:**

- Complete the window function by:

- Assessing the running total of home goals scored by FC Utrecht.

- Assessing the running average of home goals scored.

- Ordering both the running average and running total by date, descending.

```sql
SELECT 
    -- Select the date, home goal, and away goals
    date,
    home_goal,
    away_goal,
    -- Create a running total and running average of home goals
    SUM(home_goal) OVER(ORDER BY date DESC
        ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING) AS running_total,
    AVG(home_goal) OVER(ORDER BY date DESC
        ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING) AS running_avg
FROM match
WHERE 
    awayteam_id = 9908 
    AND season = '2011/2012';
```

# Bringing it all together

**Exercises:**

**Setting up the home team CTE**

In this course, we've covered ways in which you can use CASE statements, subqueries, common table expressions, and window functions in your queries to structure a data set that best meets your needs. For this exercise, you will be using all of these concepts to generate a list of matches in which Manchester United was defeated during the 2014/2015 English Premier League season.

Your first task is to create the first query that filters for matches where Manchester United played as the home team. This will become a common table expression in a later exercise.

**Instructions:**

- Create a CASE statement that identifies each match as a win, lose, or tie for Manchester United.

- Fill out the logical operators for each WHEN clause in the CASE statement (equals, greater than, less than).

- Join the tables on home team ID from match, and team_api_id from team.

- Filter the query to only include games from the 2014/2015 season where Manchester United was the home team.

```sql
SELECT 
    m.id, 
    t.team_long_name,
    -- Identify matches as home/away wins or ties
    CASE WHEN m.home_goal > m.away_goal THEN 'MU Win'
        WHEN m.home_goal < m.away_goal THEN 'MU Loss'
        ELSE 'Tie' END AS outcome
FROM match AS m
-- Left join team on the home team ID and team API id
LEFT JOIN team AS t 
ON m.hometeam_id = t.team_api_id
WHERE 
    -- Filter for 2014/2015 and Manchester United as the home team
    season = '2014/2015'
    AND t.team_long_name = 'Manchester United';
```

**Setting up the away team CTE**

Great job! Now that you have a query identifying the home team in a match, you will perform a similar set of steps to identify the away team. Just like the previous step, you will join the match and team tables. Each of these two queries will be declared as a Common Table Expression in the following step.

The primary difference in this query is that you will be joining the tables on awayteam_id, and reversing the match outcomes in the CASE statement.

When altering CASE statement logic in your own work, you can reverse either the logical condition (i.e., home_goal > away_goal) or the outcome in THEN -- just make sure you only reverse one of the two!

**Instructions:**

- Complete the CASE statement syntax.

- Fill out the logical operators identifying each match as a win, loss, or tie for Manchester United.

- Join the table on awayteam_id, and team_api_id.

```sql
SELECT 
    m.id, 
    t.team_long_name,
    -- Identify matches as home/away wins or ties
    CASE WHEN m.home_goal > m.away_goal THEN 'MU Loss'
        WHEN m.home_goal < m.away_goal THEN 'MU Win'
        ELSE 'Tie' END AS outcome
-- Join team table to the match table
FROM match AS m
LEFT JOIN team AS t 
ON m.awayteam_id = t.team_api_id
WHERE 
    -- Filter for 2014/2015 and Manchester United as the away team
    season = '2014/2015'
    AND t.team_long_name = 'Manchester United';
```

**Putting the CTEs together**

Now that you've created the two subqueries identifying the home and away team opponents, it's time to rearrange your query with the home and away subqueries as Common Table Expressions (CTEs). You'll notice that the main query includes the phrase, SELECT DISTINCT. Without identifying only DISTINCT matches, you will return a duplicate record for each game played.

Continue building the query to extract all matches played by Manchester United in the 2014/2015 season.

**Instructions:**

- Declare the home and away CTEs before your main query.

- Join your CTEs to the match table using a LEFT JOIN.

- Select the relevant data from the CTEs into the main query.

- Select the date from match, team names from the CTEs, and home/ away goals from match in the main query.

```sql
-- Set up the home team CTE
WITH home AS (
SELECT m.id, t.team_long_name,
    CASE WHEN m.home_goal > m.away_goal THEN 'MU Win'
        WHEN m.home_goal < m.away_goal THEN 'MU Loss' 
        ELSE 'Tie' END AS outcome
FROM match AS m
LEFT JOIN team AS t ON m.hometeam_id = t.team_api_id),
-- Set up the away team CTE
away AS (
SELECT m.id, t.team_long_name,
    CASE WHEN m.home_goal > m.away_goal THEN 'MU Loss'
        WHEN m.home_goal < m.away_goal THEN 'MU Win' 
        ELSE 'Tie' END AS outcome
FROM match AS m
LEFT JOIN team AS t ON m.awayteam_id = t.team_api_id)
-- Select team names, the date and goals
SELECT DISTINCT
    m.date,
    home.team_long_name AS home_team,
    away.team_long_name AS away_team,
    m.home_goal,
    m.away_goal
-- Join the CTEs onto the match table
FROM match AS m
LEFT JOIN home ON m.id = home.id
LEFT JOIN away ON m.id = away.id
WHERE m.season = '2014/2015'
    AND (home.team_long_name = 'Manchester United' 
        OR away.team_long_name = 'Manchester United');
```

**Add a window function**

Fantastic! You now have a result set that retrieves the match date, home team, away team, and the goals scored by each team. You have one final component of the question left -- how badly did Manchester United lose in each match?

In order to determine this, let's add a window function to the main query that ranks matches by the absolute value of the difference between home_goal and away_goal. This allows us to directly compare the difference in scores without having to consider whether Manchester United played as the home or away team!

The equation is complete for you -- all you need to do is properly complete the window function!

**Instructions:**

- Set up the CTEs so that the home and away teams each have a name, ID, and score associated with them.

- Select the date, home team name, away team name, home goal, and away goals scored in the main query.

- Rank the matches and order by the difference in scores in descending order.

```sql
-- Set up the home team CTE
WITH home AS (
SELECT m.id, t.team_long_name,
    CASE WHEN m.home_goal > m.away_goal THEN 'MU Win'
        WHEN m.home_goal < m.away_goal THEN 'MU Loss' 
        ELSE 'Tie' END AS outcome
FROM match AS m
LEFT JOIN team AS t ON m.hometeam_id = t.team_api_id),
-- Set up the away team CTE
away AS (
SELECT m.id, t.team_long_name,
    CASE WHEN m.home_goal > m.away_goal THEN 'MU Loss'
        WHEN m.home_goal < m.away_goal THEN 'MU Win' 
        ELSE 'Tie' END AS outcome
FROM match AS m
LEFT JOIN team AS t ON m.awayteam_id = t.team_api_id)
-- Select columns and and rank the matches by goal difference
SELECT DISTINCT
    m.date,
    home.team_long_name AS home_team,
    away.team_long_name AS away_team,
    m.home_goal, m.away_goal,
    RANK() OVER(ORDER BY ABS(home_goal - away_goal) DESC) as match_rank
-- Join the CTEs onto the match table
FROM match AS m
LEFT JOIN home ON m.id = home.id
LEFT JOIN away ON m.id = away.id
WHERE m.season = '2014/2015'
    AND ((home.team_long_name = 'Manchester United' AND home.outcome = 'MU Loss')
    OR (away.team_long_name = 'Manchester United' AND away.outcome = 'MU Loss'));
```

# PostgreSQL Summary Stats and Window Functions

**Course description:**

Have you ever wondered how data professionals use SQL to solve real-world business problems, like generating rankings, calculating moving averages and running totals, deduplicating data, or performing time intelligence? If you already know how to select, filter, order, join and group data with SQL, this course is your next step. By the end, you will be writing queries like a pro! You will learn how to create queries for analytics and data engineering with window functions, the SQL secret weapon! Using flights data, you will discover how simple it is to use window functions, and how flexible and efficient they are.

# Introduction to window functions

**Chapter description:**

In this chapter, you'll learn what window functions are, and the two basic window function subclauses, ORDER BY and PARTITION BY.

# Introduction

**Personal notes:**

**Introduction to Window Functions*

Throughout this chapter, we will be using the dataset of the Summer Olympics, with each row representing a awarded medal. The columns include the year, city, sport, discipline, event, athlete's name, country, gender, and the type of medal awarded.

**Row Numbers*

The most basic thing you can do with a window function is assigning row numbers. Row numbers allow you to reference a row by its position or index rather than its values. Row number assigns a number to each row; in this query, it simply adds a column with the number or index of each row:

```sql
SELECT
	year, event, country,
	ROW_NUMBER() OVER() AS row_n
FROM summer_medals
WHERE medal = 'Gold';
```

The `OVER` clause indicates that a function is of the window type.

**Exercises:**

**Window functions vs GROUP BY**

Which of the following is FALSE?

        "Window functions can open a "window" to another table, whereas GROUP BY functions cannot."

**Numbering rows**

The simplest application for window functions is numbering rows. Numbering rows allows you to easily fetch the nth row. For example, it would be very difficult to get the 35th row in any given table if you didn't have a column with each row's number.

**Instruction:**

- Number each row in the dataset.
        
```sql
SELECT
*,
-- Assign numbers to each row
ROW_NUMBER() OVER() AS Row_N
FROM Summer_Medals
ORDER BY Row_N ASC;
```

**Numbering Olympic games in ascending order**

The Summer Olympics dataset contains the results of the games between 1896 and 2012. The first Summer Olympics were held in 1896, the second in 1900, and so on. What if you want to easily query the table to see in which year the 13th Summer Olympics were held? You'd need to number the rows for that.

**Instruction:**

- Assign a number to each year in which Summer Olympic games were held.

```sql      
SELECT
Year,

-- Assign numbers to each year
ROW_NUMBER() OVER() AS Row_N
FROM (
SELECT DISTINCT (year)
FROM Summer_Medals
ORDER BY Year ASC
) AS Years
ORDER BY Year ASC;
```
# ORDER BY

**Personal notes:**

**ORDER BY in Window Functions*

`ORDER BY` is a subsection of `OVER`. It sorts the rows related to the current row that the window function will use.

For example, taking the previous query, if you order by year in descending order within the `OVER` clause, the function will assign 1 to the first row of that window. This row will have the most recent year in the dataset:

```sql
SELECT
	year, event, country,
	ROW_NUMBER() OVER(ORDER BY Year DESC) AS row_n
FROM summer_medals
WHERE medal = 'Gold';
```

Adding `ORDER BY` to `OVER` changed the basis on which the `ROW NUMBER` function assigned numbers to rows, assigning lower numbers to more recent rows. And if you want to sort by both year and event? You can order by multiple columns in the `OVER` clause, just as you would normally outside it:

```sql
SELECT
	year, event, country,
	ROW_NUMBER() OVER(ORDER BY Year DESC, Event DESC) AS row_n
FROM summer_medals
WHERE medal = 'Gold';
```

You can use `ORDER BY` both inside and outside at the same time. For example, in this query, row numbers are assigned based on the year and event within `OVER`. After that, the `ORDER BY` outside `OVER` takes over and sorts the table results by country and row number. So, the `ORDER BY` inside `OVER` has an effect before the `ORDER BY` outside the `OVER` function:

```sql
SELECT
	year, event, country,
	ROW_NUMBER() OVER(ORDER BY Year DESC, Event DESC) AS row_n
FROM summer_medals
WHERE medal = 'Gold'
ORDER BY Country ASC, Row_n ASC;
```

**Reigning Champion*

One application of window functions is determining the reigning champion, which would be a champion who won in both the previous and the current years. To determine if a champion is the current champion, champions from the previous and current years need to be on the same row but in two different columns, so they can be compared. How do you get the value from a previous row without complex self-joins? Enter `LAG`.

`LAG` is a window function that takes a column and a number `n` and returns the value of the column `n` rows before the current row. For example, passing 1 as `n` returns the value from the previous row:

```sql
LAG(column, n) OVER()
```

This query returns the champions of the discus throw event. Getting the champion of each year is the first step to using `LAG` to obtain the previous champion of each year:

```sql
SELECT
	Year, Country AS champion
FROM Summer_medals
WHERE
	Year IN (1996, 2000, 2004, 2008, 2012)
	AND Gender = 'Men' AND medal = 'Gold'
	AND Event = 'Discus Throw';
```

After wrapping the previous query in a CTE, select the year and champion, and use `LAG` on the champion column with an `n` of 1, ordered by year in ascending order in `OVER`:

```sql
WITH Discus_Gold AS (
	SELECT
		Year, Country AS champion
	FROM Summer_Medals
	WHERE 
		Year IN (1996, 2000, 2004, 2008, 2012)
		AND Gender = 'Men' AND Medal = 'Gold'
		AND Event = 'Discus Throw'
)

SELECT
	Year, Champion,
	LAG(champion, 1) OVER (ORDER BY Year DESC) AS Last_Champion
FROM Discus_gold
ORDER BY Year ASC;
```

**Exercises:**

**Numbering Olympic games in descending order**

You've already numbered the rows in the Summer Medals dataset. What if you need to reverse the row numbers so that the most recent Olympic games' rows have a lower number?

**Instruction:**

- Assign a number to each year in which Summer Olympic games were held so that rows with the most recent years have lower row numbers.

```sql 
SELECT
Year,
-- Assign the lowest numbers to the most recent years
ROW_NUMBER() OVER(ORDER BY Year DESC) AS Row_N
FROM (
SELECT DISTINCT Year
FROM Summer_Medals
) AS Years
ORDER BY Year;
```

**Numbering Olympic athletes by medals earned**

Row numbering can also be used for ranking. For example, numbering rows and ordering by the count of medals each athlete earned in the OVER clause will assign 1 to the highest-earning medalist, 2 to the second highest-earning medalist, and so on.

**Instructions:**

- For each athlete, count the number of medals he or she has earned.

```sql
SELECT
-- Count the number of medals each athlete has earned
athlete,
COUNT(medal) AS Medals
FROM Summer_Medals
GROUP BY Athlete
ORDER BY Medals DESC;
```

- Having wrapped the previous query in the Athlete_Medals CTE, rank each athlete by the number of medals they've earned.

```sql
WITH Athlete_Medals AS (
SELECT
        -- Count the number of medals each athlete has earned
        Athlete,
        COUNT(*) AS Medals
FROM Summer_Medals
GROUP BY Athlete)

SELECT
-- Number each athlete by how many medals they've earned
athlete,
ROW_NUMBER() OVER (ORDER BY medals DESC) AS Row_N
FROM Athlete_Medals
ORDER BY Medals DESC;
```

**Reigning weightlifting champions**

A reigning champion is a champion who's won both the previous and current years' competitions. To determine if a champion is reigning, the previous and current years' results need to be in the same row, in two different columns.

**Instructions:**

- Return each year's gold medalists in the Men's 69KG weightlifting competition.

```sql
SELECT
-- Return each year's champions' countries
year,
country AS champion
FROM Summer_Medals
WHERE
Discipline = 'Weightlifting' AND
Event = '69KG' AND
Gender = 'Men' AND
Medal = 'Gold';
```

- Having wrapped the previous query in the Weightlifting_Gold CTE, get the previous year's champion for each year.

```sql
WITH Weightlifting_Gold AS (
SELECT
        -- Return each year's champions' countries
        Year,
        Country AS champion
FROM Summer_Medals
WHERE
        Discipline = 'Weightlifting' AND
        Event = '69KG' AND
        Gender = 'Men' AND
        Medal = 'Gold')

SELECT
Year, Champion,
-- Fetch the previous year's champion
LAG(Champion,1) OVER
        (ORDER BY year ASC) AS Last_Champion
FROM Weightlifting_Gold
ORDER BY Year ASC;
```

# PARTITION BY

**Personal notes:**

**PARTITION BY in Window Functions*

This `OVER` subclause divides the table into partitions based on the unique values of a column, similar to `GROUP BY`. Unlike `GROUP BY`, however, the results of a window function with `PARTITION BY` are not grouped into a single column. The partitions are operated on separately by the window function.

**Partitioning by One Column*

Adding `PARTITION BY event` to the `OVER` clause before `ORDER BY` will separate the table into two partitions, one for discus throw and another for triple jump, the two unique values in the event column. The only difference in the results is that the first row of triple jump champions has NULL as the last champion. This is because it is the first row in its partition:

```sql
WITH Discus_gold AS (
	-- Previous query for discus throw champions
)

SELECT
	Year, Event, Champion,
	LAG(Champion) OVER(PARTITION BY Event ORDER BY Event ASC, Year ASC) AS Last_champion
FROM Discus_Gold
ORDER BY Event ASC, Year ASC;
```

**Exercises:**

**Reigning champions by gender**

You've already fetched the previous year's champion for one event. However, if you have multiple events, genders, or other metrics as columns, you'll need to split your table into partitions to avoid having a champion from one event or gender appear as the previous champion of another event or gender.

**Instruction:**

- Return the previous champions of each year's event by gender.

```sql
WITH Tennis_Gold AS (
SELECT DISTINCT
        Gender, Year, Country
FROM Summer_Medals
WHERE
        Year >= 2000 AND
        Event = 'Javelin Throw' AND
        Medal = 'Gold')

SELECT
Gender, Year,
Country AS Champion,
-- Fetch the previous year's champion by gender
LAG(country) OVER (PARTITION BY gender
                ORDER BY gender ASC) AS Last_Champion
FROM Tennis_Gold
ORDER BY Gender ASC, Year ASC;
```

**Reigning champions by gender and event**

In the previous exercise, you partitioned by gender to ensure that data about one gender doesn't get mixed into data about the other gender. If you have multiple columns, however, partitioning by only one of them will still mix the results of the other columns.

**Instruction:**

- Return the previous champions of each year's events by gender and event.

```sql
WITH Athletics_Gold AS (
SELECT DISTINCT
        Gender, Year, Event, Country
FROM Summer_Medals
WHERE
        Year >= 2000 AND
        Discipline = 'Athletics' AND
        Event IN ('100M', '10000M') AND
        Medal = 'Gold')

SELECT
Gender, Year, Event,
Country AS Champion,
-- Fetch the previous year's champion by gender and event
LAG(Country) OVER (PARTITION BY gender, event
                ORDER BY Year ASC) AS Last_Champion
FROM Athletics_Gold
ORDER BY Event ASC, Gender ASC, Year ASC;
```

**Row numbers with partitioning**

If you run ROW_NUMBER() OVER (PARTITION BY Year ORDER BY Medals DESC) on the following table, what row number would the 2008 Iranian record have?

        | Year | Country | Medals |
        |------|---------|--------|
        | 2004 | IRN     | 32     |
        | 2004 | LBN     | 17     |
        | 2004 | KSA     | 4      |
        | 2008 | IRQ     | 29     |
        | 2008 | IRN     | 27     |
        | 2008 | UAE     | 12     

    Answer: 2

# Fetching, ranking, and paging

**Chapter description:**

In this chapter, you'll learn three practical applications of window functions: fetching values from different parts of the table, ranking rows according to their values, and binning rows into different tables.

# Fetching

**Personal notes:**

**Fetching Functions: LEAD, FIRST_VALUE, and LAST_VALUE*

We have already seen the `LAG` function, which returns the value n rows before the current row. The `LEAD` clause is almost the same, except that it returns the value n rows AFTER the current row. `LAG` and `LEAD` are relative fetching functions because the value they retrieve is always relative to the current row.

The other two fetching functions are `FIRST_VALUE` and `LAST_VALUE`. `FIRST_VALUE` returns the first value in the table or partition, while `LAST_VALUE` returns the last value in the table or partition. These two functions are absolute fetching functions because what they return does not depend on the current row and is absolute in relation to the table or partition.

**LEAD Function Example*

This query retrieves the cities where each set of Olympic Games was held, as well as the next two cities. Passing 1 as n to the `LEAD` function will get the next city, and passing 2 as n will get the city after that. Similar to `LAG`, `LEAD` will return NULL once it runs out of following rows.

```sql
WITH Hosts AS (
	SELECT DISTINCT Year, City
	FROM Summer_Medals)

SELECT 
	Year, City,
	LEAD(City, 1) OVER (ORDER BY Year ASC) AS Next_City,
	LEAD(City, 2) OVER (ORDER BY Year ASC) AS After_Next_City
FROM Hosts
ORDER BY Year ASC;
```

In this query, the last row will have a `Next_City` of NULL since there are no rows after it to fetch its value, and the penultimate row will have an `After_Next_City` of NULL since `LEAD City, 2` looks for the value two rows after the current row, and this row for the penultimate row does not exist.

**FIRST_VALUE and LAST_VALUE Function Example*

This query is similar to the previous one, except that it retrieves the first and last cities where the Olympic Games were held in this table.

```sql
SELECT 
	Year, City,
	FIRST_VALUE(City) OVER (ORDER BY Year ASC) AS First_City,
	LAST_VALUE(City) OVER (ORDER BY Year ASC RANGE BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS Last_City
FROM Hosts
ORDER BY Year ASC;
```

**Exercises:**

**Future gold medalists**

Fetching functions allow you to get values from different parts of the table into one row. If you have time-ordered data, you can "peek into the future" with the LEAD fetching function. This is especially useful if you want to compare a current value to a future value.

**Instruction:**

- For each year, fetch the current gold medalist and the gold medalist 3 competitions ahead of the current row.

```sql
WITH Discus_Medalists AS (
SELECT DISTINCT
    Year,
    Athlete
FROM Summer_Medals
WHERE Medal = 'Gold'
    AND Event = 'Discus Throw'
    AND Gender = 'Women'
    AND Year >= 2000)

SELECT
-- For each year, fetch the current and future medalists
year,
Athlete,
LEAD(Athlete, 3) OVER (ORDER BY year ASC) AS Future_Champion
FROM Discus_Medalists
ORDER BY Year ASC;
```

**First athlete by name**

It's often useful to get the first or last value in a dataset to compare all other values to it. With absolute fetching functions like FIRST_VALUE, you can fetch a value at an absolute position in the table, like its beginning or end.

**Instruction:**

- Return all athletes and the first athlete ordered by alphabetical order.

```sql
WITH All_Male_Medalists AS (
SELECT DISTINCT
    Athlete
FROM Summer_Medals
WHERE Medal = 'Gold'
    AND Gender = 'Men')

SELECT
-- Fetch all athletes and the first athlete alphabetically
athlete,
FIRST_VALUE(athlete) OVER (
    ORDER BY athlete ASC
) AS First_Athlete
FROM All_Male_Medalists;
```

**Last country by name**

Just like you can get the first row's value in a dataset, you can get the last row's value. This is often useful when you want to compare the most recent value to previous values.

**Instructions:**

- Return the year and the city in which each Olympic games were held.

- Fetch the last city in which the Olympic games were held.

```sql
WITH Hosts AS (
SELECT DISTINCT Year, City
    FROM Summer_Medals)

SELECT
Year,
City,
-- Get the last city in which the Olympic games were held
LAST_VALUE(city) OVER (
ORDER BY Year ASC
RANGE BETWEEN
    UNBOUNDED PRECEDING AND
    UNBOUNDED FOLLOWING
) AS Last_City
FROM Hosts
ORDER BY Year ASC;
```

# Ranking

**Personal notes:**

**Ranking Functions: ROW_NUMBER, RANK, and DENSE_RANK*

Another common application of window functions is ranking rows based on their values. Let's learn about the three ranking functions in this lesson. Assigning numbers to rows is one way to rank them. `ROW_NUMBER` always assigns unique numbers, even if the values of two rows are equal. It picks some other metric to assign numbers if the value you're ordering by is the same.

Another ranking function is `RANK`. It assigns the same number to rows with identical values, skipping the next numbers in such cases. `DENSE_RANK` also assigns the same number to rows with identical values but doesn't skip the next numbers.

**Example 1*

This query returns the number of Olympic Games each of these countries participated in. Note that some countries, like France and Denmark, participated in the same number of games.

```sql
SELECT
	Country, COUNT(DISTINCT Year) AS Games
FROM Summer_Medals
WHERE
	Country IN ('GBR', 'DEN, 'FRA', 'ITA', 'AUT', 'BEL', 'NOR', 'POL', 'ESP')
GROUP BY Country
ORDER BY Games DESC;
```

Let's apply the three ranking functions to see how each one deals with these repeated values. After wrapping the previous query in a CTE and applying the ranking functions, we'll observe the differences in the query output.

```sql
WITH Country_Games AS (...)

SELECT
	Country, Games,
	ROW_NUMBER() OVER (ORDER BY Games DESC) AS Row_N
FROM Country_Games
ORDER BY Games DESC, Country ASC;
```

The output of this query using `ROW_NUMBER()` is familiar; it assigns a unique number to each row based on the provided order. If two rows have the same value, it will still assign unique numbers to them, but based on an internally selected order.

```sql
WITH Country_Games AS (...)

SELECT
	Country, Games,
	ROW_NUMBER() OVER (ORDER BY Games DESC) AS Row_N
	RANK() OVER (ORDER BY Games DESC) AS Rank_N
FROM Country_Games
ORDER BY Games DESC, Country ASC;
```

Using `RANK()`, it will assign the same number to two rows if their values are equal; Denmark and France are tied for second place. After the repeated rankings, it jumps to the next ranking and immediately goes to four for Italy. `RANK` always skips the next numbers if it assigns the same number to two or more rows.

```sql
WITH Country_Games AS (...)

SELECT
	Country, Games,
	ROW_NUMBER() OVER (ORDER BY Games DESC) AS Row_N
	RANK() OVER (ORDER BY Games DESC) AS Rank_N
	DENSE_RANK() OVER (ORDER BY Games DESC) AS Dense_Rank_N
FROM Country_Games
ORDER BY Games DESC, Country ASC;
```

`DENSE_RANK` also assigns 2 to Denmark and France, but instead of skipping the next ranking, it assigns 3 to Italy. It never skips rankings. `ROW_NUMBER` and `RANK` will have the same last ranking, the row count, while the last ranking of `DENSE_RANK` is the count of unique values being ranked.

**Example 2*

What if you have multiple groups you need to rank separately in your data? We can use ranking functions along with `PARTITION BY`.

```sql
WITH Country_Medals AS (...)

SELECT
	Country, Athlete
	DENSE_RANK()
		- OVER (PARTITION BY Country ORDER BY Medals DESC) AS Rank_N
FROM Country_Medals
ORDER BY Country ASC, Medals DESC;
```

After partitioning by country, Russian athletes are correctly assigned the second ranking because they are only being ranked in relation to the other athletes in their group or partition. If you have more than one group whose rows you want to rank, make sure to partition by the column that divides your rows into the correct groups.

**Exercises:**

**Ranking athletes by medals earned**

In chapter 1, you used ROW_NUMBER to rank athletes by awarded medals. However, ROW_NUMBER assigns different numbers to athletes with the same count of awarded medals, so it's not a useful ranking function; if two athletes earned the same number of medals, they should have the same rank.

**Instruction:**

- Rank each athlete by the number of medals they've earned -- the higher the count, the higher the rank -- with identical numbers in case of identical values.

```sql
WITH Athlete_Medals AS (
SELECT
    Athlete,
    COUNT(*) AS Medals
FROM Summer_Medals
GROUP BY Athlete)

SELECT
Athlete,
Medals,
-- Rank athletes by the medals they've won
RANK() OVER (ORDER BY Medals DESC) AS Rank_N
FROM Athlete_Medals
ORDER BY Medals DESC;
```

**Ranking athletes from multiple countries**

In the previous exercise, you used RANK to assign rankings to one group of athletes. In real-world data, however, you'll often find numerous groups within your data. Without partitioning your data, one group's values will influence the rankings of the others.

Also, while RANK skips numbers in case of identical values, the most natural way to assign rankings is not to skip numbers. If two countries are tied for second place, the country after them is considered to be third by most people.

**Instruction:**

- Rank each country's athletes by the count of medals they've earned -- the higher the count, the higher the rank -- without skipping numbers in case of identical values.

```sql
WITH Athlete_Medals AS (
SELECT
    Country, Athlete, COUNT(*) AS Medals
FROM Summer_Medals
WHERE
    Country IN ('JPN', 'KOR')
    AND Year >= 2000
GROUP BY Country, Athlete
HAVING COUNT(*) > 1)

SELECT
Country,
-- Rank athletes in each country by the medals they've won
Athlete,
DENSE_rank() OVER (PARTITION BY country
                ORDER BY Medals DESC) AS Rank_N
FROM Athlete_Medals
ORDER BY Country ASC, RANK_N ASC;
```

**DENSE_RANK's output**

You have the following table:

        | Country | Medals |
        |---------|--------|
        | IRN     | 23     |
        | IRQ     | 19     |
        | LBN     | 19     |
        | SYR     | 19     |
        | BHR     | 7      |
        | KSA     | 3      |

If you were to use DENSE_RANK to order the Medals column in descending order, what rank would BHR be assigned?

        Answer: 3

# Paging

**Personal notes:**

Paging involves dividing data into (approximately) equal blocks. APIs, which are interfaces for data exchange between different web platforms, often return data in pages to reduce the size of the data being sent and make it more on-demand. Additionally, when data is sorted by a metric, separating the data into quartiles or thirds can help assess performance, as you can see if a data point is in the top third, middle, or bottom.

In SQL, to achieve pagination, you can use `NTILE(n)`, which is a window function that takes n as input and then divides the data into approximately n equal pages.

**Paging - Source table*

This query returns all 67 unique disciplines. Splitting them into 15 approximately equal pages will result in about 4 or 5 rows on each page. The reason the number of rows per page is not constant is that 67 is not divisible by 15, so there will be overflow on some pages.

```sql
SELECT
	DISTINCT Discipline
FROM Summer_Medals;
```

Putting the above query into a CTE and using `NTILE`, passing n as 15, will result in dividing the rows from the query into 15 pages, with about four or five rows per page. For example, page 1 has 5 rows, but page 2 has 4, although the results are truncated here for space.

```sql
WITH Disciplines AS (
	SELECT
		DISTINCT Disciplines
	FROM Summer_Medals)

SELECT 
	Discipline, 
	NTILE(15) OVER() AS Page
FROM Disciplines
ORDER BY Page ASC;
```

**Top, Middle, and Bottom Thirds*

Another use of `NTILE` is to divide the data into thirds or quartiles. In this query, the CTE 'Country_Medals' counts the number of medals each country received overall in each set of Olympic Games. Using `NTILE` and passing n as 3, and ordering by the awarded medals in descending order, the query results will be divided into thirds, with the top 33% of countries by awarded medals in the top third (with the value of the third column being 1), the middle 33% in the middle third (with the value of the third column being 2), and the bottom 33% in the bottom third (with the value of the third column being 3). This way, you can easily label the top, middle, or bottom % of your data.

```sql
WITH Country_Medals AS (
	SELECT
		Country, COUNT(*) AS Medals
	FROM Summer_Medals
	GROUP BY Country),

SELECT 
	Country, Medals,
	NTILE(3) OVER (ORDER BY Medals DESC) AS Third
FROM Country_Medals;
```

**Exercises:**

**Paging events**

There are exactly 666 unique events in the Summer Medals Olympics dataset. If you want to chunk them up to analyze them piece by piece, you'll need to split the events into groups of approximately equal size.

**Instruction:**

- Split the distinct events into exactly 111 groups, ordered by event in alphabetical order.

```sql
WITH Events AS (
SELECT DISTINCT Event
FROM Summer_Medals)

SELECT
--- Split up the distinct events into 111 unique groups
Event,
NTILE(111) OVER (ORDER BY event ASC) AS Page
FROM Events
ORDER BY Event ASC;
```

**Top, middle, and bottom thirds**

Splitting your data into thirds or quartiles is often useful to understand how the values in your dataset are spread. Getting summary statistics (averages, sums, standard deviations, etc.) of the top, middle, and bottom thirds can help you determine what distribution your values follow.

**Instructions:**

- Split the athletes into top, middle, and bottom thirds based on their count of medals.

```sql
WITH Athlete_Medals AS (
SELECT Athlete, COUNT(*) AS Medals
FROM Summer_Medals
GROUP BY Athlete
HAVING COUNT(*) > 1)

SELECT
Athlete,
Medals,
-- Split athletes into thirds by their earned medals
NTILE(3) OVER (ORDER BY Medals DESC) AS Third
FROM Athlete_Medals
ORDER BY Medals DESC, Athlete ASC;
```

- Return the average of each third.

```sql
WITH Athlete_Medals AS (
SELECT Athlete, COUNT(*) AS Medals
FROM Summer_Medals
GROUP BY Athlete
HAVING COUNT(*) > 1),

Thirds AS (
SELECT
    Athlete,
    Medals,
    NTILE(3) OVER (ORDER BY Medals DESC) AS Third
FROM Athlete_Medals)

SELECT
-- Get the average medals earned in each third
Third,
AVG(Medals) AS Avg_Medals
FROM Thirds
GROUP BY Third
ORDER BY Third ASC;

# Aggregate window functions and frames

**Chapter description:**

In this chapter, you'll learn how to use aggregate functions you're familiar with, like `AVG()` and `SUM()`, as window functions, as well as how to define frames to change a window function's output.

# Aggregate window functions

**Personal notes:**

You can use MAX and SUM, as well as other aggregate functions like COUNT, MIN, and AVG, as window functions. Using aggregate functions as window functions can be more efficient. Like any other window function, you can partition with aggregate functions.

**Example: Using MAX as a Window Function*

In this example, we want to find the highest number of medals awarded in a single discipline in each year. We can use the MAX function as a window function for this purpose. The result will show, for each year, the highest number of medals awarded in any discipline.

```sql
SELECT
	Year,
	Discipline,
	Medals,
	MAX(Medals) OVER (PARTITION BY Year) AS Max_Medals_In_Year
FROM Summer_Medals
ORDER BY Year, Medals DESC;
```

In this query, `MAX(Medals) OVER (PARTITION BY Year)` is used as a window function, and it calculates the maximum number of medals over each partition defined by the `Year`. This allows us to see the highest number of medals awarded in a discipline for each year.

**Example: Using SUM as a Window Function with PARTITION BY*

Now, let's say we want to find the total number of medals awarded in each discipline for each year. We can use the SUM function as a window function with the PARTITION BY clause to achieve this.

```sql
SELECT
	Year,
	Discipline,
	Medals,
	SUM(Medals) OVER (PARTITION BY Year, Discipline) AS Total_Medals_In_Discipline
FROM Summer_Medals
ORDER BY Year, Discipline;
```

In this query, `SUM(Medals) OVER (PARTITION BY Year, Discipline)` calculates the total number of medals for each discipline within each year. The PARTITION BY clause ensures that the summation is done separately for each combination of Year and Discipline.

You can similarly use other aggregate functions like COUNT, MIN, and AVG as window functions, and the PARTITION BY clause allows you to perform these calculations within specific partitions of your data.

**Exercises:**

**Running totals of athlete medals**

The running total (or cumulative sum) of a column helps you determine what each row's contribution is to the total sum.

**Instruction:**

- Return the athletes, the number of medals they earned, and the medals running total, ordered by the athletes' names in alphabetical order.

```sql
WITH Athlete_Medals AS (
SELECT
    Athlete, COUNT(*) AS Medals
FROM Summer_Medals
WHERE
    Country = 'USA' AND Medal = 'Gold'
    AND Year >= 2000
GROUP BY Athlete)

SELECT
-- Calculate the running total of athlete medals
athlete,
Medals,
SUM(medals) OVER (ORDER BY Athlete ASC) AS Max_Medals
FROM Athlete_Medals
ORDER BY Athlete ASC;
```

**Maximum country medals by year**

Getting the maximum of a country's earned medals so far helps you determine whether a country has broken its medals record by comparing the current year's earned medals and the maximum so far.

- Return the year, country, medals, and the maximum medals earned so far for each country, ordered by year in ascending order.

```sql
WITH Country_Medals AS (
SELECT
    Year, Country, COUNT(*) AS Medals
FROM Summer_Medals
WHERE
    Country IN ('CHN', 'KOR', 'JPN')
    AND Medal = 'Gold' AND Year >= 2000
GROUP BY Year, Country)

SELECT
-- Return the max medals earned so far per country
Year,
country,
medals,
MAX(medals) OVER (PARTITION BY country
                ORDER BY Year ASC) AS Max_Medals
FROM Country_Medals
ORDER BY Country ASC, Year ASC;
```

**Minimum country medals by year**

So far, you've seen MAX and SUM, aggregate functions normally used with GROUP BY, being used as window functions. You can also use the other aggregate functions, like MIN, as window functions.

**Instruction:**

- Return the year, medals earned, and minimum medals earned so far.

```sql
WITH France_Medals AS (
SELECT
    Year, COUNT(*) AS Medals
FROM Summer_Medals
WHERE
    Country = 'FRA'
    AND Medal = 'Gold' AND Year >= 2000
GROUP BY Year)

SELECT
Year,
Medals,
MIN(Medals) OVER (ORDER BY Year ASC) AS Min_Medals
FROM France_Medals
ORDER BY Year ASC;
```

# Frames

**Personal notes:**

Another way to alter the behavior of a Window function is by defining a frame. By default, a frame starts at the beginning of a table or partition and ends at the current row. Frames allow you to change the behavior of a window function by specifying which rows the function takes as input.

**ROWS BETWEEN Clause*

- `ROWS BETWEEN [START] AND [FINISH]`

A frame always starts with ROWS BETWEEN or RANGE BETWEEN. A frame always has a start and an end, which can be defined using one of the 3 clauses: PRECEDING, CURRENT ROW, and FOLLOWING.

- `n PRECEDING`: Defines the frame as starting or ending n rows before the current row.
- `CURRENT ROW`: Is used to define the start or end at the current row.
- `n FOLLOWING`: Is used to define n rows after the current row.

**Examples:*

- `ROWS BETWEEN 3 PRECEDING AND CURRENT ROW`

   This frame starts 3 rows before the current row and ends at the current row, so the frame has 4 rows.

- `ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING`

   This frame starts one row before the current row and ends one row after the current row, so the frame has 3 rows.

- `ROWS BETWEEN 5 PRECEDING AND 1 PRECEDING`

   This frame starts five rows before the current row and ends one row before the current row, so the frame has 5 rows.

**Exercises:**

**Number of rows in a frame**

How many rows does the following frame span?

ROWS BETWEEN 3 PRECEDING AND 2 FOLLOWING

        Answer: 6

**Moving maximum of Scandinavian athletes' medals**

Frames allow you to restrict the rows passed as input to your window function to a sliding window for you to define the start and finish.

Adding a frame to your window function allows you to calculate "moving" metrics, inputs of which slide from row to row.

**Instruction:**

- Return the year, medals earned, and the maximum medals earned, comparing only the current year and the next year.

```sql
WITH Scandinavian_Medals AS (
SELECT
    Year, COUNT(*) AS Medals
FROM Summer_Medals
WHERE
    Country IN ('DEN', 'NOR', 'FIN', 'SWE', 'ISL')
    AND Medal = 'Gold'
GROUP BY Year)

SELECT
-- Select each year's medals
year,
medals,
-- Get the max of the current and next years'  medals
MAX(medals) OVER (ORDER BY year ASC
            ROWS BETWEEN CURRENT ROW
            AND 1 FOLLOWING) AS Max_Medals
FROM Scandinavian_Medals
ORDER BY Year ASC;
```

**Moving maximum of Chinese athletes' medals**

Frames allow you to "peek" forwards or backward without first using the relative fetching functions, LAG and LEAD, to fetch previous rows' values into the current row.

- Return the athletes, medals earned, and the maximum medals earned, comparing only the last two and current athletes, ordering by athletes' names in alphabetical order.

```sql
WITH Chinese_Medals AS (
SELECT
    Athlete, COUNT(*) AS Medals
FROM Summer_Medals
WHERE
    Country = 'CHN' AND Medal = 'Gold'
    AND Year >= 2000
GROUP BY Athlete)

SELECT
-- Select the athletes and the medals they've earned
Athlete,
medals,
-- Get the max of the last two and current rows' medals 
MAX(medals) OVER (ORDER BY athlete ASC
            ROWS BETWEEN 2 PRECEDING
            AND CURRENT ROW) AS Max_Medals
FROM Chinese_Medals
ORDER BY Athlete ASC;
```

# Moving averages and totals

**Personal notes:**

A moving average (MA) is the average of the last n periods of values from a column. Moving averages are used in various industries; for example, in sales, a 10-day moving average is the average of units sold in the last ten days per day. It is used to indicate momentum and trends; if units sold per day are greater than their moving average, more units will be sold the next day. They are also useful for smoothing out seasonality, which would be the normal fluctuation in units sold per day.

On the other hand, a moving total is the sum of the last n periods of values from a column. For example, the sum of the last 3 medals from the Olympic Games for any set of Olympic Games. It is used to indicate recent performance; if the sum is decreasing, overall performance is decreasing, and vice versa.

**Examples* - The source table for the examples is the count of gold medals awarded to the United States after 1980.

**Moving Average*

Let's take the 3-year moving average, which is the average of medal gains in the last two and the current sets of Olympic Games for each year. Setting the window to start two rows before the current row and end at the current row, it passes these three rows as input to the AVG function. The first moving average is equivalent to the medals from the first year since there is no other value to calculate the average. The moving average of the second row is the average of its value and the value of the first row; the moving average of the third row is the average of its value and the two previous rows, and so on.

```sql
WITH US_Medals AS (
    -- Your initial query to get medal data
)

SELECT
    Year, Medals,
    AVG(Medals) OVER (ORDER BY Year ASC 
        ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) AS Medals_MA
FROM US_Medals
ORDER BY Year ASC;
```

**Moving Total*

A moving total works the same way as the moving average, but instead of the AVG function, you use the SUM function with the same frame. Thus, the moving total of the first row is the value of the first row, the value of the second row the moving total is the sum of the first and second row, and then for each row, the moving total is the sum of its value and the values of the two previous rows.

```sql
WITH US_Medals AS (
    -- Your initial query to get medal data
)

SELECT
    Year, Medals,
    SUM(Medals) OVER (ORDER BY Year ASC 
        ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) AS Medals_MT
FROM US_Medals
ORDER BY Year ASC;
```

**ROWS vs. RANGE*

In the previous video, we saw that the frame subclause of LAST_VALUE starts with RANGE BETWEEN, while the frames you've seen so far start with ROWS BETWEEN. RANGE BETWEEN works the same way as ROWS BETWEEN, with one significant difference. RANGE treats duplicates in the columns in the ORDER BY subclause as unique entities, while ROWS does not. In practice, ROWS BETWEEN is almost always used instead of RANGE.

**Exercises:**

**Moving average's frame**

If you want your moving average to cover the last 3 and current Olympic games, how would you define its frame?

        "ROWS BETWEEN 3 PRECEDING AND CURRENT ROW"

**Moving average of Russian medals**

Using frames with aggregate window functions allow you to calculate many common metrics, including moving averages and totals. These metrics track the change in performance over time.

**Instruction:**

- Calculate the 3-year moving average of medals earned.

```sql
WITH Russian_Medals AS (
SELECT
    Year, COUNT(*) AS Medals
FROM Summer_Medals
WHERE
    Country = 'RUS'
    AND Medal = 'Gold'
    AND Year >= 1980
GROUP BY Year)

SELECT
Year, Medals,
--- Calculate the 3-year moving average of medals earned
AVG(medals) OVER
    (ORDER BY Year ASC
    ROWS BETWEEN
    2 PRECEDING AND CURRENT ROW) AS Medals_MA
FROM Russian_Medals
ORDER BY Year ASC;
```

**Moving total of countries' medals**

What if your data is split into multiple groups spread over one or more columns in the table? Even with a defined frame, if you can't somehow separate the groups' data, one group's values will affect the average of another group's values.

**Instruction:**

- Calculate the 3-year moving sum of medals earned per country.

```sql
WITH Country_Medals AS (
SELECT
    Year, Country, COUNT(*) AS Medals
FROM Summer_Medals
GROUP BY Year, Country)

SELECT
Year, Country, Medals,
-- Calculate each country's 3-game moving total
SUM(Medals) OVER
    (PARTITION BY country
    ORDER BY Year ASC
    ROWS BETWEEN
    2 PRECEDING AND CURRENT ROW) AS Medals_MA
FROM Country_Medals
ORDER BY Country ASC, Year ASC;
```

# Beyond window functions

**Chapter description:**

In this last chapter, you'll learn some techniques and functions that are useful when used together with window functions.

# Pivoting

**Personal notes:**

Pivoting transforms a table by creating columns with unique values from one of its columns. In general, pivot tables are easier to analyze, especially when pivoted on a column ordered chronologically.

**CROSSTAB*

CROSSTAB allows you to pivot a table on a specific column. You need to use the CREATE EXTENSION statement before using CROSSTAB. CREATE EXTENSION makes extra functions in an extension available for use. The "tablefunc" extension contains the CROSSTAB function.

```sql
CREATE EXTENSION IF NOT EXISTS tablefunc;
```

After that, put your source query between two pairs of dollar signs. Then, in the parentheses after ct, write the column names and types for your new pivot table. The column names are the non-pivoted column and the unique values from the pivoted column.

```sql
CREATE EXTENSION IF NOT EXISTS tablefunc;

SELECT * FROM CROSSTAB($$
    source_sql TEXT
$$) AS ct (column_1 DATA_TYPE_1,
          column_2 DATA_TYPE_2,
          ...,
          column_n DATA_TYPE_N);
```

For example, in the following query, the CTE counts the gold medals awarded to three countries in the 2004, 2008, and 2012 Olympics. Then, the ranking of each country is calculated based on who won the most gold medals in each of the Olympics. Convert RANK to integer to determine the column type for the pivoted columns.

```sql
WITH Country_Awards AS (
    SELECT 
        Country, Year, COUNT(*) AS Awards
    FROM Summer_Medals
    WHERE
        Country IN ('CHN', 'RUS', 'USA')
        AND Year IN (2004, 2008, 2012)
        AND Medal = 'Gold' AND Sport = 'Gymnastics'
    GROUP BY Country, Year
    ORDER BY Country ASC, Year ASC
)

SELECT
    Country, Year,
    RANK() OVER (PARTITION BY Year ORDER BY Awards DESC) :: INTEGER AS rank
FROM Country_Awards
ORDER BY Country ASC, Year ASC;
```

Looking at the result, wouldn't it be easier to read if the column was pivoted by year? To change that, replace the ellipses with the source query. Then, in the parentheses after ct, list the column names and types for the pivot table. Since you're pivoting on the year, and the values are in awards, the columns are 'country' (the non-pivoted column) and the unique values in the year (2004, 2008, 2012). Make sure to list the unique values in the correct order.

```sql
CREATE EXTENSION IF NOT EXISTS tablefunc;

SELECT * FROM CROSSTAB($$
    ...
$$) AS ct (Country VARCHAR,
           "2004" INTEGER,
           "2008" INTEGER,
           "2012" INTEGER)
ORDER BY Country ASC;
```

The result shows the rankings pivoted by country and year, making it easier to read. Pivoting is useful when preparing data for visualization and reports.

**Exercises:**

**A basic pivot**

You have the following table of Pole Vault gold medalist countries by gender in 2008 and 2012.

    | Gender | Year | Country |
    |--------|------|---------|
    | Men    | 2008 | AUS     |
    | Men    | 2012 | FRA     |
    | Women  | 2008 | RUS     |
    | Women  | 2012 | USA     |

Pivot it by Year to get the following reshaped, cleaner table.

    | Gender | 2008 | 2012 |
    |--------|------|------|
    | Men    | AUS  | FRA  |
    | Women  | RUS  | USA  |

**Instructions:**

- Create the correct extension.

- Fill in the column names of the pivoted table.

```sql
-- Create the correct extension to enable CROSSTAB
CREATE EXTENSION IF NOT EXISTS tablefunc;

SELECT * FROM CROSSTAB($$
SELECT
    Gender, Year, Country
FROM Summer_Medals
WHERE
    Year IN (2008, 2012)
    AND Medal = 'Gold'
    AND Event = 'Pole Vault'
ORDER By Gender ASC, Year ASC;
-- Fill in the correct column names for the pivoted table
$$) AS ct (Gender VARCHAR,
        "2008" VARCHAR,
        "2012" VARCHAR)

ORDER BY Gender ASC;
```

**Pivoting with ranking**

You want to produce an easy scannable table of the rankings of the three most populous EU countries by how many gold medals they've earned in the 2004 through 2012 Olympic games. The table needs to be in this format:

    | Country | 2004 | 2008 | 2012 |
    |---------|------|------|------|
    | FRA     | ...  | ...  | ...  |
    | GBR     | ...  | ...  | ...  |
    | GER     | ...  | ...  | ...  |

You'll need to count the gold medals each country has earned, produce the ranks of each country by medals earned, then pivot the table to this shape.

**Instructions:**

- Count the gold medals that France (FRA), the UK (GBR), and Germany (GER) have earned per country and year.

```sql
-- Count the gold medals per country and year
SELECT
Country,
Year,
COUNT(*) AS Awards
FROM Summer_Medals
WHERE
Country IN ('FRA', 'GBR', 'GER')
AND Year IN (2004, 2008, 2012)
AND Medal = 'Gold'
GROUP BY country, year
ORDER BY Country ASC, Year ASC
```

- Select the country and year columns, then rank the three countries by how many gold medals they earned per year.

```sql
WITH Country_Awards AS (
SELECT
    Country,
    Year,
    COUNT(*) AS Awards
FROM Summer_Medals
WHERE
    Country IN ('FRA', 'GBR', 'GER')
    AND Year IN (2004, 2008, 2012)
    AND Medal = 'Gold'
GROUP BY Country, Year)

SELECT
-- Select Country and Year
Country,
Year,
-- Rank by gold medals earned per year
RANK() OVER (PARTITION BY Year ORDER BY Awards DESC) :: INTEGER AS rank
FROM Country_Awards
ORDER BY Country ASC, Year ASC;
```

- Pivot the query's results by Year by filling in the new table's correct column names.

```sql
CREATE EXTENSION IF NOT EXISTS tablefunc;

SELECT * FROM CROSSTAB($$
WITH Country_Awards AS (
    SELECT
    Country,
    Year,
    COUNT(*) AS Awards
    FROM Summer_Medals
    WHERE
    Country IN ('FRA', 'GBR', 'GER')
    AND Year IN (2004, 2008, 2012)
    AND Medal = 'Gold'
    GROUP BY Country, Year)

SELECT
    Country,
    Year,
    RANK() OVER
    (PARTITION BY Year
    ORDER BY Awards DESC) :: INTEGER AS rank
FROM Country_Awards
ORDER BY Country ASC, Year ASC;
-- Fill in the correct column names for the pivoted table
$$) AS ct (Country VARCHAR,
        "2004" INTEGER,
        "2008" INTEGER,
        "2012" INTEGER)

Order by Country ASC;
```

# ROLLUP and CUBE

**Personal notes:**

ROLLUP is a GROUP BY subclause that includes extra rows for group-level aggregations. In this query, grouping by country and rolling up medal will count all countries and totals at the medal level, count only country-level totals, and fill 'medal' with nulls for those rows.

```sql
SELECT
    Country, Medal, COUNT(*) AS Awards
FROM Summer_Medals
WHERE
    Year = 2008 AND Country IN ('CHN', 'RUS')
GROUP BY Country, ROLLUP(Medal) 
ORDER BY Country ASC, Medal ASC;
```

You can also use ROLLUP to generate grand totals. If you use ROLLUP on all GROUP BY columns, you will get an additional row with the grand total. ROLLUP is hierarchical; the order of columns in the ROLLUP clause affects the output. If you use ROLLUP on country and medal, you'll get country-level totals, but if you reverse the columns, you'll get medal-level totals. Both will include the grand total, though.

```sql
SELECT
    Country, Medal, COUNT(*) AS Awards
FROM Summer_Medals
WHERE
    Year = 2008 AND Country IN ('CHN', 'RUS')
GROUP BY Country, ROLLUP(Country, Medal) 
ORDER BY Country ASC, Medal ASC;
```

Rows where country is filled but medal is null represent country-level totals; for example, 184 total medals were awarded to China in 2008. The row with nulls in both columns is the grand total. Note that there are no medal-level totals since you are using ROLLUP by country first and then by medal, not vice versa. And what if you also want the total medals?

Enter CUBE.

CUBE is much like ROLLUP, except it's not hierarchical. It generates all possible group-level aggregations. Putting country and medal in the CUBE subclause will count at the country level, medal level, and grand totals.

```sql
SELECT
    Country, Medal, COUNT(*) AS Awards
FROM Summer_Medals
WHERE
    Year = 2008 AND Country IN ('CHN', 'RUS')
GROUP BY CUBE(Country, Medal) 
ORDER BY Country ASC, Medal ASC;
```

Note in the query result that medal-level totals are included, as well as country-level totals. Medal-level totals are those where country is null but medal is not.

**ROLL UP vs CUBE*

Use ROLLUP when you have hierarchical data in your columns, such as date parts, because in such cases, only a few group-level aggregations make sense. Use CUBE when you want all possible group-level aggregations. With ROLLUP and CUBE, you can succinctly generate many group-level aggregations.

**Exercises:**

**Country-level subtotals**

You want to look at three Scandinavian countries' earned gold medals per country and gender in the year 2004. You're also interested in Country-level subtotals to get the total medals earned for each country, but Gender-level subtotals don't make much sense in this case, so disregard them.

**Instructions:**

- Count the gold medals awarded per country and gender.

- Generate Country-level gold award counts.

```sql
-- Count the gold medals per country and gender
SELECT
Country,
Gender,
COUNT(*) AS Gold_Awards
FROM Summer_Medals
WHERE
Year = 2004
AND Medal = 'Gold'
AND Country IN ('DEN', 'NOR', 'SWE')
-- Generate Country-level subtotals
GROUP BY Country, ROLLUP(Gender)
ORDER BY Country ASC, Gender ASC;
```

**All group-level subtotals**

You want to break down all medals awarded to Russia in the 2012 Olympic games per gender and medal type. Since the medals all belong to one country, Russia, it makes sense to generate all possible subtotals (Gender- and Medal-level subtotals), as well as a grand total.

Generate a breakdown of the medals awarded to Russia per country and medal type, including all group-level subtotals and a grand total.

**Instructions:**

- Count the medals awarded per gender and medal type.

- Generate all possible group-level counts (per gender and medal type subtotals and the grand total).

```sql
-- Count the medals per gender and medal type
SELECT
gender,
medal,
COUNT(*) AS Awards
FROM Summer_Medals
WHERE
Year = 2012
AND Country = 'RUS'
-- Get all possible group-level subtotals
GROUP BY CUBE(gender, medal)
ORDER BY Gender ASC, Medal ASC;
```

# A survey of useful functions

**Personal notes:**

**Enter COALESCE*

COALESCE takes a list of values and returns the first non-null value, going from left to right. COALESCE is useful when using SQL operations that return nulls, such as ROLLUP and CUBE. Other operations that return nulls are pivot operations (when some of your rows have no corresponding values for the new columns) and positional operations like LAG, which always returns a null for the first row because it has no previous row.

The only change to the example query used in the previous lesson that needs to be made is to wrap the two columns with COALESCE and pass the string you want the column to contain if its value is null. The country column is null when it's the grand total, so the string should be both countries, while the medal column is null when it's the count of all medals, so it should be all medals.

```sql
SELECT
    COALESCE(Country,  'Both Countries') AS Country,
    COALESCE(Medal, 'All medals') AS Medal,
    COUNT(*) AS Awards
FROM Summer_Medals
WHERE
    Year = 2008 AND Country IN ('CHN', 'RUS')
GROUP BY Country, ROLLUP(Country, Medal) 
ORDER BY Country ASC, Medal ASC;
```

Make sure to name the output columns as the columns you passed as your first argument for consistent results. As seen in the query result, the nulls have been replaced with what was passed to each COALESCE.

**Enter STRING_AGG*

STRING_AGG takes all the values in a column and concatenates them, with a separator between each value. It is useful when you need to reduce the number of returned rows.

```sql
STRING_AGG(Letter, ', ')
```

To use STRING_AGG, simply wrap the final query from the previous lesson in a CTE called Country_Ranks. Then, use STRING_AGG on the country column and pass a comma separator with a space after it.

```sql
WITH Country_Medals AS (...)

Country_Ranks AS (...)

SELECT STRING_AGG(Country, ', ')
FROM Country_Medals;
```

Using COALESCE and STRING_AGG, you can clean up and condense the results of your queries.

**Exercises:**

**Cleaning up results**

Returning to the breakdown of Scandinavian awards you previously made, you want to clean up the results by replacing the nulls with meaningful text.

**Instruction:**

- Turn the nulls in the Country column to All countries, and the nulls in the Gender column to All genders.

```sql
SELECT
-- Replace the nulls in the columns with meaningful text
COALESCE(Country, 'All countries') AS Country,
COALESCE(Gender, 'All genders') AS Gender,
COUNT(*) AS Awards
FROM Summer_Medals
WHERE
Year = 2004
AND Medal = 'Gold'
AND Country IN ('DEN', 'NOR', 'SWE')
GROUP BY ROLLUP(Country, Gender)
ORDER BY Country ASC, Gender ASC;
```

**Summarizing results**

After ranking each country in the 2000 Olympics by gold medals awarded, you want to return the top 3 countries in one row, as a comma-separated string. In other words, turn this:

    | Country | Rank |
    |---------|------|
    | USA     | 1    |
    | RUS     | 2    |
    | AUS     | 3    |
    | ...     | ...  |

into this:

USA, RUS, AUS

**Instructions:**

- Rank countries by the medals they've been awarded.

```sql
WITH Country_Medals AS (
SELECT
    Country,
    COUNT(*) AS Medals
FROM Summer_Medals
WHERE Year = 2000
    AND Medal = 'Gold'
GROUP BY Country)

SELECT
    Country,
    -- Rank countries by the medals awarded
RANK() OVER (ORDER BY medals DESC)  AS Rank
FROM Country_Medals
ORDER BY Rank ASC;
```

- Return the top 3 countries by medals awarded as one comma-separated string.

```sql
WITH Country_Medals AS (
SELECT
    Country,
    COUNT(*) AS Medals
FROM Summer_Medals
WHERE Year = 2000
    AND Medal = 'Gold'
GROUP BY Country),

Country_Ranks AS (
SELECT
    Country,
    RANK() OVER (ORDER BY Medals DESC) AS Rank
FROM Country_Medals
ORDER BY Rank ASC)

-- Compress the countries column
SELECT STRING_AGG(Country, ', ')
FROM Country_Ranks
-- Select only the top three ranks
WHERE Rank <= 3;
```

# Functions for Manipulating Data in PostgreSQL

**Course Description:**

This course will provide you an understanding of how to use built-in PostgreSQL functions in your SQL queries to manipulate different types of data including strings, character, numeric and date/time. We'll travel back to a time where Blockbuster video stores were on every corner and if you wanted to
watch a movie, you actually had to leave your house to rent a DVD! You'll also get an introduction into the robust full-text search capabilities which provides a powerful tool for indexing and matching keywords in a PostgreSQL document. And finally, you'll learn how to extend these features by using PostgreSQL extensions.

# Overview of Common Data Types

**Chapter description:**

Learn about the properties and characteristics of common data types including strings, numerics and arrays and how to retrieve information about your database.

# Welcome!

**Personal notes:**

**Overview of Common Data Types*

In this chapter, we will learn about built-in functions and operators to extend the capabilities of your PostgreSQL database. We will use the Sakila database, a well-known sample database that models a fictional DVD rental store. The chosen database is highly normalized, allowing for significant sample queries and providing an excellent representation of PostgreSQL data types and custom functions.

**Common Data Types*

PostgreSQL has a robust set of native data types. Text data types such as CHAR, VARCHAR, and TEXT, numeric data types like INT and DECIMAL, date and time types like DATE, TIME, TIMESTAMP, INTERVAL, and even arrays.

It is important to have an understanding of the properties and characteristics of various data types whenever you are working with a relational database like PostgreSQL. Text data types like CHAR and VARCHAR allow for a fixed or variable number of characters and string data. Numeric data types enable you to store integers like 'payment_ID' and decimal numbers with variable precision, such as the 'amount' in the payment table.

**Determining Data Type from Existing Tables*

When working with existing databases, there will be times when you need to determine the data types of the columns you will be working with. PostgreSQL stores information about all database objects in a database system called INFORMATION SCHEMA. By querying certain tables in this database, you can determine information about the database, including column data types.

The following query will return the column_name and data type for the columns we saw in the previous slide. By executing this query, you will get a result where you can see that the title and description columns are indeed text data types, specifically VARCHAR and TEXT. However, you will notice that special_features is actually an ARRAY.

```sql
SELECT
    column_name,
    data_type
FROM INFORMATION_SCHEMA.COLUMNS
WHERE column_name IN ('title', 'description', 'special_features')
    AND table_name = 'film';
```

**Exercises:**

**Text data types**

You learned about some of the common data types that you'll work within PostgreSQL, some characteristics of these types, and how to determine the data type of a column in an existing table. Think back to the video and answer the following question:

Which of the following is not a valid text data type in PostgreSQL?

        "STRING"

**Getting information about your database**

As we saw in the video, PostgreSQL has a system database called INFORMATION_SCHEMA that allows us to extract information about objects, including tables, in our database.

In this exercise we will look at how to query the tables table of the INFORMATION_SCHEMA database to discover information about tables in the DVD Rentals database including the name, type, schema, and catalog of all tables and views and then how to use the results to get additional information about columns in our tables.

**Instructions:**

- Select all columns from the INFORMATION_SCHEMA.TABLES system database. Limit results that have a public table_schema.

```sql    
-- Select all columns from the TABLES system database
SELECT * 
FROM INFORMATION_SCHEMA.TABLES
-- Filter by schema
WHERE table_schema = 'public';
``` 

- Select all columns from the INFORMATION_SCHEMA.COLUMNS system database. Limit by table_name to actor

```sql    
-- Select all columns from the COLUMNS system database
SELECT * 
FROM INFORMATION_SCHEMA.COLUMNS
WHERE table_name = 'actor';
```   

**Determining data types**

The columns table of the INFORMATION_SCHEMA database also allows us to extract information about the data types of columns in a table. We can extract information like the character or string length of a CHAR or VARCHAR column or the precision of a DECIMAL or NUMERIC floating point type.

Using the techniques you learned in the lesson, let's explore the customer table of our DVD Rental database.

**Instructions:**

- Select the column name and data type from the INFORMATION_SCHEMA.COLUMNS system database.

- Limit results to only include the customer table.

```sql   
-- Get the column name and data type
SELECT
    column_name, 
    data_type
-- From the system database information schema
FROM INFORMATION_SCHEMA.COLUMNS 
-- For the customer table
WHERE table_name = 'customer';
```   

# Date and time data types

**Personal notes:**

Understanding how to work with these data types is crucial for preparing and extracting data for machine learning and data science. We will learn about the precision and features of timestamp data types, intervals, and date and time types.

**TIMESTAMP Data Types*

Most of the date and time data you will work with in SQL will have a TIMESTAMP data type. Timestamps contain both a date and a time value with microsecond precision. These data types are very common because they can be used to record an exact moment in time, such as when a payment was made or a record was last updated. PostgreSQL timestamps use the ISO 8601 format, which is a four-digit year, followed by a month and day with two digits each, separated by dashes.

**DATE and TIME Data Types*

When you need to store only a part of the TIMESTAMP in your database, the DATE and TIME types might be better options. The DATE and TIME types are essentially the date and time values of the TIMESTAMP.

**INTERVAL Data Types*

Finally, INTERVAL data types store date and time data as a period of time in years, months, days, hours, seconds, etc. Intervals are useful when you want to perform arithmetic on date and time columns.

**Looking at Date and Time Types*

We can use the same technique we learned in the previous lesson to determine information about a column with a date and time data type by querying the INFORMATION_SCHEMA system database.

PostgreSQL provides the ability to store TIMESTAMP and TIME data types with or without time zones. Although this is useful in certain situations, most of the time, you will work with timestamp values without time zones, which is the default behavior.

**Exercises:**

**Properties of date and time data types**

Which of the following is NOT correct?

       " TIME data types are stored with a timezone by default."

**Interval data types**

INTERVAL data types provide you with a very useful tool for performing arithmetic on date and time data types. For example, let's say our rental policy requires a DVD to be returned within 3 days. We can calculate the expected_return_date for a given DVD rental by adding an INTERVAL of 3 days to the rental_date from the rental table. We can then compare this result to the actual return_date to determine if the DVD was returned late.

Let's try this example in the exercise.

**Instructions:**

- Select the rental date and return date from the rental table.

- Add an INTERVAL of 3 days to the rental_date to calculate the expected return date`.

```sql
SELECT
-- Select the rental and return dates
rental_date,
return_date,
-- Calculate the expected_return_date
rental_date + INTERVAL '3 days' AS expected_return_date
FROM rental;
```

# Working with ARRAYs

**Personal notes:**

Arrays in PostgreSQL are very similar to arrays in most programming languages. You can create multi-dimensional arrays of varying lengths for any native data type in PostgreSQL.

**CREATE TABLE Example*

Most data science tasks involve getting data from a database using SQL queries with SELECT statements. Before you can extract data, someone needs to create the database, add at least one table with at least one column, and then insert some records. The CREATE TABLE statement, as seen in this example, will create an empty table called my_first_table with columns first_column and second_column defined as text and integer data types.

```sql
CREATE TABLE my_first_table (
    first_column text, 
    second_column integer
);
```

The following INSERT statement example will add a record to the my_first_table table with "text value" as the value for the first column and 12 as the value for the second column.

```sql
INSERT INTO my_first_table
    (first_column, second_column) VALUES ('text value', 12);
```

**ARRAY: A Special Type*

To create an ARRAY type, simply add "[ ]" to the end of the data type you want to make an array. Let's create a simple table with two array columns to illustrate how this is done. This table has an email column that will be a nested array of text data to store the email type and address for a given student_id. The "text_scores" column will contain an array of integer values representing test numerical scores.

```sql
CREATE TABLE grades (
    student_id INT,
    email text[][],
    text_scores INT[]
);
```

**INSERT Statements with ARRAYS*

Once the table is created, we can use INSERT statements to add some records to the table. Note how arrays are represented in SQL with brackets and quotes for the email and a comma-separated list of integers for the text_scores.

```sql
INSERT INTO grades
VALUES (1, '{{"work", "work1@datacamp.com"}, {"other","other1@datacamp.com"}}', '{92, 85, 96, 88}');
```

**Accessing ARRAYS*

Now that we have data in our table, let's see how you access array data in a SELECT statement. Accessing arrays in PostgreSQL is very similar to accessing arrays in other programming languages. For email, you can get the first element of the array using the array notation you see below with index values starting from 1.

```sql
SELECT
    email[1][1] AS type,
    email[1][2] AS address,
    test_scores[1]
FROM grades;
```

Note that array indices in PostgreSQL start with 1, not 0 as in Python.

**Searching ARRAYS*

The same notation used to access arrays in the SELECT statement can also be used in the WHERE clause as a filter. In the example below, we look for records that have 'work' as the value in the first index of the email array. Using the standard syntax for non-array columns like WHERE email='work' would result in an error.

```sql
SELECT
    email[1][1] AS type,
    email[1][2] AS address,
    test_scores[1]
FROM grades
WHERE email[1][1] = 'work';
```

**ARRAY Function and Operators*

The ANY function allows you to search for a value in an array and return a record if it finds a match. In the example below, we want to query all records where the email address contains "other" in any array value.

```sql
SELECT
    email[1][1] AS type,
    email[1][2] AS address,
    test_scores[1]
FROM grades
WHERE 'other' = ANY(email);
```

An alternative to the ANY function is the contains operator (@>). The syntax for this operator is a bit more complex but returns the same results as the ANY function, as shown below.

```sql
SELECT
    email[1][1] AS type,
    email[1][2] AS address,
    test_scores[1]
FROM grades
WHERE email @> ARRAY['other'];
```

**Exercises:**

**Accessing data in an ARRAY**

In our DVD Rentals database, the film table contains an ARRAY for special_features which has a type of TEXT[]. Much like any ARRAY data type in PostgreSQL, a TEXT[] array can store an array of TEXT values. This comes in handy when you want to store things like phone numbers or email addresses as we saw in the lesson.

Let's take a look at the special_features column and also practice accessing data in the ARRAY.

**Instructions:**

- Select the title and special features from the film table and compare the results between the two columns.

```sql    
-- Select the title and special features column 
SELECT 
title, 
special_features 
FROM film;
```

- Select all films that have a special feature Trailers by filtering on the first index of the special_features ARRAY.

```sql  
-- Select the title and special features column 
SELECT 
title, 
special_features 
FROM film
-- Use the array index of the special_features column
WHERE special_features[1] = 'Trailers';
```

- Now let's select all films that have Deleted Scenes in the second index of the special_features ARRAY.

```sql    
-- Select the title and special features column 
SELECT 
title, 
special_features 
FROM film
-- Use the array index of the special_features column
WHERE special_features[2] = 'Deleted Scenes';
```  

**Searching an ARRAY with ANY**

As we saw in the video, PostgreSQL also provides the ability to filter results by searching for values in an ARRAY. The ANY function allows you to search for a value in any index position of an ARRAY. Here's an example.

WHERE 'search text' = ANY(array_name)
When using the ANY function, the value you are filtering on appears on the left side of the equation with the name of the ARRAY column as the parameter in the ANY function.

**Instruction:**

- Match 'Trailers' in any index of the special_features ARRAY regardless of position.

```sql    
SELECT
title, 
special_features 
FROM film 
-- Modify the query to use the ANY function 
WHERE 'Trailers' = ANY(special_features);
```

**Searching an ARRAY with @>**

The contains operator @> operator is alternative syntax to the ANY function and matches data in an ARRAY using the following syntax.

    WHERE array_name @> ARRAY['search text'] :: type[]

So let's practice using this operator in the exercise.

**Instruction:**

- Use the contains operator to match the text Deleted Scenes in the special_features column.

```sql
SELECT 
title, 
special_features 
FROM film 
-- Filter where special_features contains 'Deleted Scenes'
WHERE special_features @> ARRAY['Deleted Scenes'];
```

# Working with DATE/TIME Functions and Operators

**Chapter description:**

Explore how to manipulate and query date and time objects including how to use the current timestamp in your queries, extract subfields from existing date and time fields and what to expect when you perform date and time arithmetic.

# Overview of basic arithmetic operators

**Personal notes:**

**Adding and Subtracting Date/Time Data*

Performing basic arithmetic operations on date and time data will become a useful skill in practice, but it's important to understand how the return values for these operations vary depending on the type of date and time data you're working with. For example, when you subtract date values, the result returned is an integer data type.

You can also add integer values to date data types. In this example, we are adding the integer number three to a date value, and the result shows three days greater than the original date, in this case, '2005-09-14'. When adding integer numbers to date values, the implicit precision is days.

```sql
SELECT date '2005-09-11' + integer '3';
```

However, when we perform the same operation on timestamp date/time data, as in the example below, we get an INTERVAL as a result '1 day 12:00:00':

```sql
SELECT timestamp '2005-09-11 00:00:00' - timestamp '2005-09-09 12:00:00';
```

**Calculating Time Periods with AGE*

The AGE function allows us to calculate the difference between two timestamp values. The AGE function takes two timestamp arguments, subtracts the first argument from the second, and returns an INTERVAL as a result, similar to the output in the previous example.

```sql
SELECT AGE(timestamp '2005-09-11 00:00:00', timestamp '2005-09-09 12:00:00');
```

**Date/Time Arithmetic Using INTERVALs*

Learning to use INTERVALs for date and time calculations is a very useful skill for developing real-world applications. Using an INTERVAL is a great technique when you need to perform relative date and time calculations. We can perform multiplication and division on date and time data using intervals, which is another useful tool when dealing with relative date and time data. For example, let's say we want to add 21 days to a date value using a timestamp and an interval:

```sql
SELECT timestamp '2019-05-01' + 21 * INTERVAL '1 day';
```

**Exercises:**

**Adding and subtracting date and time values**

In this exercise, you will calculate the actual number of days rented as well as the true expected_return_date by using the rental_duration column from the film table along with the familiar rental_date from the rental table.

This will require that you dust off the skills you learned from prior courses on how to join two or more tables together. To select columns from both the film and rental tables in a single query, we'll need to use the inventory table to join these two tables together since there is no explicit relationship between them. Let's give it a try!

**Instructions:**

- Subtract the rental_date from the return_date to calculate the number of days_rented.

```sql
SELECT f.title, f.rental_duration,
    -- Calculate the number of days rented
    r.return_date - r.rental_date AS days_rented
FROM film AS f
    INNER JOIN inventory AS i ON f.film_id = i.film_id
    INNER JOIN rental AS r ON i.inventory_id = r.inventory_id
ORDER BY f.title;
```

- Now use the AGE() function to calculate the days_rented.

```sql
SELECT f.title, f.rental_duration,
    -- Calculate the number of days rented
    AGE(r.return_date, r.rental_date ) AS days_rented
FROM film AS f
    INNER JOIN inventory AS i ON f.film_id = i.film_id
    INNER JOIN rental AS r ON i.inventory_id = r.inventory_id
ORDER BY f.title;
```

**INTERVAL arithmetic**

If you were running a real DVD Rental store, there would be times when you would need to determine what film titles were currently out for rental with customers. In the previous exercise, we saw that some of the records in the results had a NULL value for the return_date. This is because the rental was still outstanding.

Each rental in the film table has an associated rental_duration column which represents the number of days that a DVD can be rented by a customer before it is considered late. In this example, you will exclude films that have a NULL value for the return_date and also convert the rental_duration to an INTERVAL type. Here's a reminder of one method for performing this conversion.

SELECT INTERVAL '1' day * timestamp '2019-04-10 12:34:56'

**Instructions:**

- Convert rental_duration by multiplying it with a 1 day INTERVAL

- Subtract the rental_date from the return_date to calculate the number of days_rented.

- Exclude rentals with a NULL value for return_date.

```sql
SELECT
    f.title,
    -- Convert the rental_duration to an interval
    INTERVAL '1' day * f.rental_duration,
    -- Calculate the days rented as we did previously
    r.return_date - r.rental_date AS days_rented
FROM film AS f
    INNER JOIN inventory AS i ON f.film_id = i.film_id
    INNER JOIN rental AS r ON i.inventory_id = r.inventory_id
-- Filter the query to exclude outstanding rentals
WHERE r.return_date IS NOT NULL
ORDER BY f.title;
```

**Calculating the expected return date**

So now that you've practiced how to add and subtract timestamps and perform relative calculations using intervals, let's use those new skills to calculate the actual expected return date of a specific rental. As you've seen in previous exercises, the rental_duration is the number of days allowed for a rental before it's considered late. To calculate the expected_return_date you will want to use the rental_duration and add it to the rental_date.

**Instructions:**

- Convert rental_duration by multiplying it with a 1-day INTERVAL.

- Add it to the rental date.

```sql
SELECT
    f.title,
    r.rental_date,
    f.rental_duration,
    -- Add the rental duration to the rental date
    INTERVAL '1' day * f.rental_duration + r.rental_date AS expected_return_date,
    r.return_date
FROM film AS f
    INNER JOIN inventory AS i ON f.film_id = i.film_id
    INNER JOIN rental AS r ON i.inventory_id = r.inventory_id
ORDER BY f.title;
```

# Functions for retrieving current date/time

**Personal notes:**

**Retrieving the Current Timestamp*

One of the most common techniques is to retrieve the current date and time value in your query. PostgreSQL provides various functions to do this, starting with the NOW() function. NOW() allows you to retrieve a timestamp value for the current date and time with microsecond precision and time zone.

```sql
SELECT NOW();
```

If you want to retrieve the current timestamp without the time zone, you can do that using CAST (Casting).

```sql
SELECT NOW()::timestamp;
```

Casting (conversion) allows you to convert one data type to another, so that columns stored in your database can be retrieved and cast as a different type. There are several ways to cast data in your queries. The above syntax using the double colon operator is specific to PostgreSQL and not compliant with the SQL standard. We can use the CAST() function to achieve the same result by specifying the column name or, in this case, the NOW() function followed by the type name.

```sql
SELECT CAST(NOW() AS timestamp);
```

PostgreSQL provides alternative methods to retrieve the current date and time values. The CURRENT_TIMESTAMP function returns the same result as the NOW() function, and both approaches can be used quite interchangeably in your queries.

```sql
SELECT CURRENT_TIMESTAMP;
```

One difference between CURRENT_TIMESTAMP and NOW() is that with CURRENT_TIMESTAMP, you can specify a precision parameter, as you see in the example, which will round the seconds to the specified number of fractional digits.

```sql
SELECT CURRENT_TIMESTAMP(2);
```

**Current Date and Time*

Sometimes, you may want to get the current date or time, but you don't need the precision of a timestamp. In these cases, you can use the CURRENT_DATE and/or CURRENT_TIME functions. In this example, the CURRENT_DATE function will return a date value without the time.

```sql
SELECT CURRENT_DATE;
```

Additionally, you can use the CURRENT_TIME function to get the time value with the time zone without the date value, as seen earlier.

**Exercises:**

**Current timestamp functions**

Use the console to explore the NOW(), CURRENT_TIMESTAMP, CURRENT_DATE and CURRENT_TIME functions and their outputs to determine which of the following is NOT correct?

        "CURRENT_TIMESTAMP returns the current timestamp without timezone."

**Working with the current date and time**

Because the Sakila database is a bit dated and most of the date and time values are from 2005 or 2006, you are going to practice using the current date and time in our queries without using Sakila. You'll get back into working with this database in the next video and throughout the remainder of the course. For now, let's practice the techniques you learned about so far in this chapter to work with the current date and time.

As you learned in the video, NOW() and CURRENT_TIMESTAMP can be used interchangeably.

**Instructions:**

- Use NOW() to select the current timestamp with timezone.

```sql
-- Select the current timestamp
SELECT NOW();
```

- Select the current date without any time value.

```sql
-- Select the current date
SELECT CURRENT_DATE;
```
 
- Now, let's use the CAST() function to eliminate the timezone from the current timestamp.

```sql
--Select the current timestamp without a timezone
SELECT CAST( NOW() AS timestamp )
```

- Finally, let's select the current date.
Use CAST() to retrieve the same result from the NOW() function.

```sql
SELECT 
    -- Select the current date
    CURRENT_DATE,
    -- CAST the result of the NOW() function to a date
    CAST( NOW() AS date )
```

**Manipulating the current date and time**

Most of the time when you work with the current date and time, you will want to transform, manipulate, or perform operations on the value in your queries. In this exercise, you will practice adding an INTERVAL to the current timestamp as well as perform some more advanced calculations.

Let's practice retrieving the current timestamp. For this exercise, please use CURRENT_TIMESTAMP instead of the NOW() function and if you need to convert a date or time value to a timestamp data type, please use the PostgreSQL specific casting rather than the CAST() function.

**Instructions:**

- Select the current timestamp without timezone and alias it as right_now.

```sql
--Select the current timestamp without timezone
SELECT CURRENT_TIMESTAMP::timestamp AS right_now;
```

- Now select a timestamp five days from now and alias it as five_days_from_now.

```sql
SELECT
    CURRENT_TIMESTAMP::timestamp AS right_now,
    INTERVAL '5 days' + CURRENT_TIMESTAMP AS five_days_from_now;
```

- Finally, let's use a second-level precision with no fractional digits for both the right_now and five_days_from_now fields.

```sql
SELECT
    CURRENT_TIMESTAMP(2)::timestamp AS right_now,
    interval '5 days' + CURRENT_TIMESTAMP(2) AS five_days_from_now;
```

# Extracting and transforming date/ time data

**Personal notes:**

In this lesson, we will explore additional built-in functions that will help us transform timestamp and interval data types, creating new fields to prepare data for analysis. Let's start by looking at how to use the EXTRACT, DATE_PART, and DATE_TRUNC functions to manipulate timestamp date/time data and create new columns by extracting subfields from existing date and time values. This type of data manipulation is useful when the precision of a timestamp is not needed for analysis, and you want to use date parts such as year or month in your query, but the underlying data contains only a standard timestamp value. You may also not care about certain precisions like the time of day in some analyses, and truncating timestamps may be necessary.

**EXTRACT and DATE_PART*

To use these functions in your queries, you need to pass two parameters: the field identifier and the source.

```sql
EXTRACT(field FROM source)
```

```sql
DATE_PART('field', source)
```

The field parameter is an identifier or string if you are using DATE_PART, indicating which subfield you want to extract from the source. Various field identifiers include year, month, quarter, day of the week, etc. The source parameter needs to be a valid timestamp or interval data type.

```sql
SELECT EXTRACT(quarter FROM timestamp '2005-01-24 05:12:00') AS quarter;
```

```sql
SELECT DATE_PART('quarter', timestamp '2005-01-24 05:12:00') AS quarter;
```

EXTRACT and DATE_PART produce identical results and can be used interchangeably, with only minor variations in how you pass the field and source parameters.

**Extracting Sub-Fields from Timestamp Data*

In our DVD rentals database, each customer rental has a corresponding record in the payment table, and each transaction is recorded with a timestamp in the 'payment_date' column. While this level of detail is necessary for an e-commerce application, there will undoubtedly be times when you want to aggregate this data for use in model training, reporting, and/or trend analysis.

For example, you might want to identify the highest revenue per quarter. To do this, we want to aggregate the payment amount column and use the EXTRACT function to extract the quarter and year subfields from the payment_date column. We also introduce a technique with the GROUP BY clause that allows us to specify fields in the SELECT clause using a numeric reference, which is helpful when using functions to derive new columns.

```sql
SELECT
  EXTRACT(quarter FROM payment_date) AS quarter,
  EXTRACT(year FROM payment_date) AS year,
  SUM(amount) AS total_payments
FROM
  payment
GROUP BY 1, 2;
```

**Truncating Timestamps using DATE_TRUNC()*

The DATE_TRUNC() function will truncate the timestamp or interval data type to return a timestamp or interval at a specified precision. Precision values are a subset of the field identifiers that can be used with the EXTRACT() and DATE_PART() functions. For example, to truncate a date to the year, we pass the year identifier as the first parameter to the DATE_TRUNC function, resulting in an interval or timestamp instead of a numeric value.

```sql
SELECT DATE_TRUNC('year', TIMESTAMP '2005-05-21 15:30:30');
```

**Exercises:**

**Using EXTRACT**

You can use EXTRACT() and DATE_PART() to easily create new fields in your queries by extracting sub-fields from a source timestamp field.

Now suppose you want to produce a predictive model that will help forecast DVD rental activity by day of the week. You could use the EXTRACT() function with the dow field identifier in our query to create a new field called dayofweek as a sub-field of the rental_date column from the rental table.

You can COUNT() the number of records in the rental table for a given date range and aggregate by the newly created dayofweek column.

**Instructions:**

- Get the day of the week from the rental_date column.

```sql
SELECT 
-- Extract day of week from rental_date
EXTRACT(dow FROM rental_date) AS dayofweek 
FROM rental 
LIMIT 100;
```

- Count the total number of rentals by day of the week.

```sql
-- Extract day of week from rental_date
SELECT 
EXTRACT(dow FROM rental_date) AS dayofweek, 
-- Count the number of rentals
COUNT(rental) as rentals 
FROM rental 
GROUP BY 1;
```

**Using DATE_TRUNC**

The DATE_TRUNC() function will truncate timestamp or interval data types to return a timestamp or interval at a specified precision. The precision values are a subset of the field identifiers that can be used with the EXTRACT() and DATE_PART() functions. DATE_TRUNC() will return an interval or timestamp rather than a number. For example

SELECT DATE_TRUNC('month', TIMESTAMP '2005-05-21 15:30:30');
Result: 2005-05-01 00;00:00

Now, let's experiment with different precisions and ultimately modify the queries from the previous exercises to aggregate rental activity.

**Instructions:**

- Truncate the rental_date field by year.

```sql
-- Truncate rental_date by year
SELECT DATE_TRUNC('year', rental_date) AS rental_year
FROM rental;
```

- Now modify the previous query to truncate the rental_date by month.

```sql
-- Truncate rental_date by month
SELECT DATE_TRUNC('month', rental_date) AS rental_month
FROM rental;
```

- Let's see what happens when we truncate by day of the month.

```sql
-- Truncate rental_date by day of the month 
SELECT DATE_TRUNC('day', rental_date) AS rental_day 
FROM rental;
```

- Finally, count the total number of rentals by rental_day and alias it as rentals.

```sql
SELECT 
DATE_TRUNC('day', rental_date) AS rental_day,
-- Count total number of rentals 
COUNT('rental_day') AS rentals
FROM rental
GROUP BY 1;
```

**Putting it all together**

Many of the techniques you've learned in this course will be useful when building queries to extract data for model training. Now let's use some date/time functions to extract and manipulate some DVD rentals data from our fictional DVD rental store.

In this exercise, you are going to extract a list of customers and their rental history over 90 days. You will be using the EXTRACT(), DATE_TRUNC(), and AGE() functions that you learned about during this chapter along with some general SQL skills from the prerequisites to extract a data set that could be used to determine what day of the week customers are most likely to rent a DVD and the likelihood that they will return the DVD late.

**Instructions:**

- Extract the day of the week from the rental_date column using the alias dayofweek.

- Use an INTERVAL in the WHERE clause to select records for the 90 day period starting on 5/1/2005.

```sql
SELECT 
-- Extract the day of week date part from the rental_date
EXTRACT(day FROM rental_date) AS dayofweek,
AGE(return_date, rental_date) AS rental_days
FROM rental AS r 
WHERE 
-- Use an INTERVAL for the upper bound of the rental_date 
rental_date BETWEEN CAST('2005-05-01' AS date)
AND CAST('2005-05-01' AS date) + INTERVAL '90 day';
```

- Finally, use a CASE statement and DATE_TRUNC() to create a new column called past_due which will be TRUE if the rental_days is greater than the rental_duration otherwise, it will be FALSE.

```sql
SELECT 
c.first_name || ' ' || c.last_name AS customer_name,
f.title,
r.rental_date,
-- Extract the day of week date part from the rental_date
EXTRACT(dow FROM r.rental_date) AS dayofweek,
AGE(r.return_date, r.rental_date) AS rental_days,
-- Use DATE_TRUNC to get days from the AGE function
CASE WHEN DATE_TRUNC('day', AGE(r.return_date, r.rental_date)) > 
-- Calculate number of d
    f.rental_duration * INTERVAL '1' day 
THEN TRUE 
ELSE FALSE END AS past_due 
FROM 
film AS f 
INNER JOIN inventory AS i 
    ON f.film_id = i.film_id 
INNER JOIN rental AS r 
    ON i.inventory_id = r.inventory_id 
INNER JOIN customer AS c 
    ON c.customer_id = r.customer_id 
WHERE 
-- Use an INTERVAL for the upper bound of the rental_date 
r.rental_date BETWEEN CAST('2005-05-01' AS DATE) 
AND CAST('2005-05-01' AS DATE) + INTERVAL '90 day';
```

# Parsing and Manipulating Text

**Chapter description:**

Learn how to manipulate string and text data by transforming case, parsing and truncating text and extracting substrings from larger strings.

# Reformatting string and character data

**Personal notes:**

In this chapter, we will learn how to manipulate and transform string and character data. In this lesson, we'll start by exploring functions and operators that allow us to reformat and analyze string and character data. We will also see how to calculate the length of a string or determine the position of a character within a string. Finally, we'll learn how to truncate and pad string data.

**The String Concatenation Operator*

String concatenation allows you to merge two or more strings to form a single combined string. In this example, you can see how we can combine two separate columns from the customer table, first_name and last_name, to create a new column called full_name.

```sql
SELECT
  first_name,
  last_name,
  first_name || ' ' || last_name AS full_name
FROM customer;
```

**String Concatenation with Functions*

Additionally, PostgreSQL also has a built-in function for string concatenation. The CONCAT() function accepts one or more parameters and returns the concatenated string as a result. Each parameter can be a column from a database or a literal value separated by a comma. In this example, we see how we can perform the same concatenation operation using this function instead of the || operator, yielding an identical result.

```sql
SELECT
  CONCAT(first_name, ' ', last_name) AS full_name
FROM customer;
```

**String Concatenation with a Non-String Input*

PostgreSQL also allows concatenating string and non-string data, as in the example below where we append the customer_id column to the first_name and last_name columns. Non-string data can be used in concatenation with both the || operator and the concat() function.

```sql
SELECT
  customer_id || ': ' || first_name || ' ' || last_name AS full_name
FROM customer;
```

**Changing the Case of String*

There will also be times when you want to reformat string data to uppercase, lowercase, or initial capitalization. This is useful when you want to standardize a field in your dataset for manipulation. The UPPER function allows reformatting a string to change each character to its uppercase equivalent. UPPER takes a string as a parameter and returns that string in uppercase letters.

```sql
SELECT
  UPPER(email)
FROM customer;
```

Similarly, the LOWER function is analogous to UPPER but converts the string to lowercase. It is used in the same way.

```sql
SELECT 
  LOWER(title)
FROM film;
```

Likewise, the INITCAP function will convert a string to initial capitalization. For example, a column with full names where the first letter of each name needs to be uppercase and the rest lowercase.

```sql
SELECT
  INITCAP(title)
FROM film;
```

**Replacing Characters in a String*

The REPLACE function will find a substring in a string and replace it with a different substring. For instance, if we need to correct a grammatical error within a table and replace all occurrences of "A Astounding" with the correct text "An Astounding," we can use the REPLACE function. The function takes three parameters: the original string, the substring to find in the original string, and the replacement string.

```sql
SELECT
  REPLACE(description, 'A Astounding', 'An Astounding') AS description
FROM film;
```

**Manipulating String Data with REVERSE*

The REVERSE function takes a string as its only parameter and returns the same string reversed.

```sql
SELECT
  title,
  REVERSE(title)
FROM film AS f;
```

**Exercises:**

**Concatenating strings**

In this exercise and the ones that follow, we are going to derive new fields from columns within the customer and film tables of the DVD rental database.

We'll start with the customer table and create a query to return the customers name and email address formatted such that we could use it as a "To" field in an email script or program. This format will look like the following:

Brian Piccolo <bpiccolo@datacamp.com>

In the first step of the exercise, use the || operator to do the string concatenation and in the second step, use the CONCAT() functions.

**Instructions:**

- Concatenate the first_name and last_name columns separated by a single space followed by email surrounded by < and >.

```sql
-- Concatenate the first_name and last_name and email 
SELECT first_name || ' ' || last_name || ' <' || email || '>' AS full_email 
FROM customer
```

- Now use the CONCAT() function to do the same operation as the previous step.

```sql
-- Concatenate the first_name and last_name and email
SELECT CONCAT(first_name, ' ', last_name, ' ', '<', email, '>') AS full_email 
FROM customer
```

**Changing the case of string data**

Now you are going to use the film and category tables to create a new field called film_category by concatenating the category name with the film's title. You will also format the result using functions you learned about in the video to transform the case of the fields you are selecting in the query; for example, the INITCAP() function which converts a string to title case.

**Instructions:**

- Convert the film category name to uppercase.

- Convert the first letter of each word in the film's title to upper case.

- Concatenate the converted category name and film title separated by a colon.

- Convert the description column to lowercase.

```sql
SELECT 
-- Concatenate the category name to coverted to uppercase
-- to the film title converted to title case
UPPER(name)  || ': ' || INITCAP(title) AS film_category, 
-- Convert the description column to lowercase
LOWER(description) AS description
FROM 
film AS f 
INNER JOIN film_category AS fc 
    ON f.film_id = fc.film_id 
INNER JOIN category AS c 
    ON fc.category_id = c.category_id;
```

**Replacing string data**

Sometimes you will need to make sure that the data you are extracting does not contain any whitespace. There are many different approaches you can take to cleanse and prepare your data for these situations. A common technique is to replace any whitespace with an underscore.

In this example, we are going to practice finding and replacing whitespace characters in the title column of the film table using the REPLACE() function.

**Instruction:**

- Replace all whitespace with an underscore.

```sql
SELECT 
-- Replace whitespace in the film title with an underscore
REPLACE(title, ' ', '_') AS title
FROM film; 
```

# Parsing string and character data

**Personal notes:**

In this lesson, we will learn about string functions in PostgreSQL that allow us to analyze and manipulate text data. We will also learn how to combine and nest functions to provide additional features.

**Determining the Length of a String*

First, let's examine the CHAR_LENGTH function. It can be used to determine the number of characters in a string. CHAR_LENGTH accepts a string as input and returns the number of characters in the string as an integer for output. In this example, we see the CHAR_LENGTH function used on the title column of the film table in the DVD rental database.

```sql
SELECT
  title,
  CHAR_LENGTH(title)
FROM film;
```

LENGTH is analogous to CHAR_LENGTH, accepting the same parameter and returning the same result as you can see in this example. These two functions can be used interchangeably depending on your preference.

```sql
SELECT
  title,
  LENGTH(title)
FROM film;
```

**Finding the Position of a Character in a String*

The POSITION function returns an integer representing the number of characters from left to right before the search string is found.

```sql
SELECT 
  email,
  POSITION('@' IN email)
FROM customer;
```

STRPOS is analogous to POSITION with slightly different syntax, as shown in the example below.

```sql
SELECT
  email,
  STRPOS(email, '@')
FROM customer;
```

**Parsing String Data*

Now, let's look at some functions that will help parse strings into substrings. The LEFT function allows you to extract the first n characters from a string. For example, in this query, we are extracting the first fifty characters from the description column of the film table in our DVD rental database.

```sql
SELECT
  LEFT(description, 50)
FROM film;
```

The RIGHT function is very similar to LEFT, but it extracts the last n characters from a string.

```sql
SELECT
  RIGHT(description, 50)
FROM film;
```

**Extracting Substring of Character Data*

SUBSTRING allows us to extract a substring of text data. The SUBSTRING function takes three parameters: the source string or column, an integer representing the starting position of the source string, and another integer to specify the length of the substring we want to extract.

```sql
SELECT
  SUBSTRING(description, 10, 50)
FROM film AS f;
```

SUBSTRING can be combined with other functions to provide additional features. For example, we can extract the text to the left of the at sign (@) in an email address using a slightly different set of parameters in the SUBSTRING function. The first parameter remains the same, but the second parameter is replaced by the keyword FROM followed by an integer representing the starting position, and the third parameter includes the keyword FOR followed by an integer representing the end position. In this example, we use the POSITION function as the second parameter in the SUBSTRING function.

```sql
SELECT
  SUBSTRING(email FROM 0 FOR POSITION('@' IN email))
FROM customer;
```

Now, we can use a different technique if we want to extract the characters to the right of the at sign in the email column. In this example, we use the POSITION function as the second parameter of SUBSTRING to determine the starting position of the string, and CHAR_LENGTH to determine the last position, which is a handy trick for finding the last position of a string. The POSITION function will return the integer value of the position of the at sign in the string. To exclude the at sign from the result, we need to add one to the starting position.

```sql
SELECT
  SUBSTRING(email FROM POSITION('@' IN email) + 1 FOR CHAR_LENGTH(email))
FROM customer;
```

SUBSTR is analogous to SUBSTRING but only allows the parameters to be separated by commas and does not allow the alternative syntax with the keywords FROM and FOR.

```sql
SELECT 
  SUBSTR(description, 10, 50)
FROM film AS f;
```

**Exercises:**

**Determining the length of strings**

Determining the number of characters in a string is something that you will use frequently when working with data in a SQL database. Many situations will require you to find the length of a string stored in your database. For example, you may need to limit the number of characters that are displayed in an application or you may need to ensure that a column in your dataset contains values that are all the same length. In this example, we are going to determine the length of the description column in the film table of the DVD Rental database.

**Instructions:**

- Select the title and description columns from the film table.

- Find the number of characters in the description column with the alias desc_len.

```sql
SELECT 
-- Select the title and description columns
title,
description,
-- Determine the length of the description column
LENGTH(description) AS desc_len
FROM film;
```

**Truncating strings**

In the previous exercise, you calculated the length of the description column and noticed that the number of characters varied but most of the results were over 75 characters. There will be many times when you need to truncate a text column to a certain length to meet specific criteria for an application. In this exercise, we will practice getting the first 50 characters of the description column.

**Instruction:**

- Select the first 50 characters of the description column with the alias short_desc

```sql
SELECT 
-- Select the first 50 characters of description
LEFT(description, 50) AS short_desc
FROM 
film AS f; 
```

**Extracting substrings from text data**

In this exercise, you are going to practice how to extract substrings from text columns. The Sakila database contains the address table which stores the street address for all the rental store locations. You need a list of all the street names where the stores are located but the address column also contains the street number. You'll use several functions that you've learned about in the video to manipulate the address column and return only the street address.

**Instructions:**

- Extract only the street address without the street number from the address column.

- Use functions to determine the starting and ending position parameters.

```sql
SELECT 
-- Select only the street name from the address table
SUBSTRING(address FROM POSITION(' ' IN address)+1 FOR CHAR_LENGTH(address))
FROM 
address;
```

**Combining functions for string manipulation**

In the next example, we are going to break apart the email column from the customer table into three new derived fields. Parsing a single column into multiple columns can be useful when you need to work with certain subsets of data. Email addresses have embedded information stored in them that can be parsed out to derive additional information about our data. For example, we can use the techniques we learned about in the video to determine how many of our customers use an email from a specific domain.

**Instructions:**

- Extract the characters to the left of the @ of the email column in the customer table and alias it as username.

- Now use SUBSTRING to extract the characters after the @ of the email column and alias the new derived field as domain.

```sql
SELECT
-- Extract the characters to the left of the '@'
SUBSTRING(email FROM 1 FOR POSITION('@' IN email) - 1) AS username,
-- Extract the characters to the right of the '@'
SUBSTRING(email FROM POSITION('@' IN email) + 1 FOR CHAR_LENGTH(email)) AS domain
FROM customer;
```

# Truncating and padding string data

**Personal notes:**

In the next section, we will look at how to truncate and replace or overwrite characters in a string.

**Removing Whitespace from Strings*

The first function we will look at is TRIM. The TRIM function will remove characters from either the beginning or end of the string or both, and it accepts three parameters. The first parameter is optional and specifies whether you want to remove characters from the beginning or end of a string or both. If this parameter is omitted, the default value is both. The second parameter, which is also optional, specifies the characters to be removed from the string. If this parameter is omitted, the default value is whitespace. Finally, the last parameter is the string you want to trim.

```sql
-- TRIM([leading | trailing | both] [characters] FROM string)
SELECT TRIM(' padded ');
```

Most of the time, we will use this function without the first two parameters, with only the string as the single parameter. This default behavior will remove all whitespace from the beginning and end of the string, as you can see in this example.

```sql
SELECT TRIM(' padded ');
```

The LTRIM and RTRIM functions are analogous to TRIM but only remove characters from the beginning or end of the string, not both. Very similar to TRIM, we will use these functions with their default behavior to trim whitespace. In this example, we see that LTRIM removes only the spaces at the beginning of the selected string, while we will see the opposite result using RTRIM, which removes only the spaces at the end of the selected string.

```sql
SELECT LTRIM(' padded ');
SELECT RTRIM(' padded ');
```

**Padding Strings with Character Data*

The LPAD function appends a character or string to another string for a specified number of characters. This is useful when you need a field to have the same length and want to fill the string with a specific character, such as a space or tab. In this example, we are padding the word 'padded' with the hash character so that the returned string has a character length equal to ten.

```sql
SELECT LPAD('padded', 10, '#');
```

If you omit the third parameter in the LPAD function, as you can see in the example below, the string will be filled with a space character by default. When the length parameter is smaller than the original length of the string, the returned result will be truncated, removing the last letter.

```sql
SELECT LPAD('padded', 10);
SELECT LPAD('padded', 5);
```

The RPAD function is analogous to LPAD but will pad the string with characters to the right. The syntax works in the same way:

```sql
SELECT RPAD('padded', 10, '#');
```

**Exercises:**

**Padding**

Padding strings is useful in many real-world situations. Earlier in this course, we learned about string concatenation and how to combine the customer's first and last name separated by a single blank space and also combined the customer's full name with their email address.

The padding functions that we learned about in the video are an alternative approach to do this task. To use this approach, you will need to combine and nest functions to determine the length of a string to produce the desired result. Remember when calculating the length of a string you often need to adjust the integer returned to get the proper length or position of a string.

Let's revisit the string concatenation exercise but use padding functions.

**Instructions:**

- Add a single space to the end or right of the first_name column using a padding function.

- Use the || operator to concatenate the padded first_name to the last_name column.

```sql
-- Concatenate the padded first_name and last_name 
SELECT 
    RPAD(first_name, LENGTH(first_name)+1) || last_name AS full_name
FROM customer;
```

- Now add a single space to the left or beginning of the last_name column using a different padding function than the first step.

- Use the || operator to concatenate the first_name column to the padded last_name.

```sql
-- Concatenate the first_name and last_name 
SELECT 
    first_name || LPAD(last_name, LENGTH(last_name)+1) AS full_name
FROM customer; 
```

- Add a single space to the right or end of the first_name column.

- Add the characters < to the right or end of last_name column.

- Finally, add the characters > to the right or end of the email column.

```sql
-- Concatenate the first_name and last_name 
SELECT 
    RPAD(first_name, LENGTH(first_name)+1) 
    || RPAD(last_name, LENGTH(last_name)+2, ' <') 
    || RPAD(email, LENGTH(email)+1, '>') AS full_email
FROM customer; 
```

**The TRIM function**

In this exercise, we are going to revisit and combine a couple of exercises from earlier in this chapter. If you recall, you used the LEFT() function to truncate the description column to 50 characters but saw that some words were cut off and/or had trailing whitespace. We can use trimming functions to eliminate the whitespace at the end of the string after it's been truncated.

**Instructions:**

- Convert the film category name to uppercase and use the CONCAT() concatenate it with the title.

- Truncate the description to the first 50 characters and make sure there is no leading or trailing whitespace after truncating.

```sql
-- Concatenate the uppercase category name and film title
SELECT 
CONCAT(UPPER(c.name), ': ', f.title) AS film_category, 
-- Truncate the description and remove trailing whitespace
TRIM(TRAILING ' ' FROM SUBSTRING(f.description FROM 1 FOR 50)) AS film_desc
FROM 
film AS f 
INNER JOIN film_category AS fc 
    ON f.film_id = fc.film_id 
INNER JOIN category AS c 
    ON fc.category_id = c.category_id;
```

**Putting it all together**

In this exercise, we are going to use the film and category tables to create a new field called film_category by concatenating the category name with the film's title. You will also practice how to truncate text fields like the film table's description column without cutting off a word.

To accomplish this we will use the REVERSE() function to help determine the position of the last whitespace character in the description before we reach 50 characters. This technique can be used to determine the position of the last character that you want to truncate and ensure that it is less than or equal to 50 characters AND does not cut off a word.

This is an advanced technique but I know you can do it! Let's dive in.

**Instructions:**

- Get the first 50 characters of the description column

- Determine the position of the last whitespace character of the truncated description column and subtract it from the number 50 as the second parameter in the first function above.

```sql
SELECT 
UPPER(c.name) || ': ' || f.title AS film_category, 
-- Truncate the description without cutting off a word
LEFT(description, 50 - 
-- Subtract the position of the first whitespace character
    POSITION(
' ' IN REVERSE(LEFT(description, 50))
    )
        ) 
FROM 
film AS f 
INNER JOIN film_category AS fc 
    ON f.film_id = fc.film_id 
INNER JOIN category AS c 
    ON fc.category_id = c.category_id;
```

# Full-text Search and PostgresSQL Extensions

**Chapter description:**

An introduction into some more advanced capabilities of PostgreSQL like full-text search and extensions.

# Introduction to full-text search

**Personal notes:**

**The LIKE Operator*

The LIKE operator can be used in a WHERE clause to search for a pattern in a column. To do this, we use something called a wildcard as a placeholder for some other values. There are two wildcards we can use with LIKE. The first is the underscore (_) sign, which matches a single character. The second is the percent (%) sign, which will match zero or more characters of variable length.

In this example, we use the percent wildcard to match any title in the film table that starts with the word 'ELF' followed by zero or more characters.

```sql
SELECT title
FROM film
WHERE title LIKE 'ELF%';
```

Changing the position of the percent wildcard in our query produces a very different result. In this example, we use the percent wildcard to match a string that starts with one or more characters followed by the string 'ELF'.

```sql
SELECT title
FROM film
WHERE title LIKE '%ELF';
```

The LIKE operator is a great tool to use when searching for specific characters in a string. Sometimes, when conducting a text search, you will want to find variations of the characters you are searching for. For example, using LIKE to search the title column for any string that contains the word 'elf' in lowercase letters will return zero results.

```sql
SELECT title
FROM film
WHERE title LIKE '%elf';
```

**LIKE versus Full-Text Search*

However, consider this query that performs a full-text search using the 'to_tsvector' and 'to_tsquery' functions and the @@ match operator to search the 'title' column. Because full-text search is responsible for variations in the search string and is case-insensitive, we see that we get the expected results.

```sql
SELECT title, description
FROM film
WHERE to_tsvector(title) @@ to_tsquery('elf');
```

**What is Full-Text Search?*

Full-text search provides a means to perform natural language queries on text data using lemmatization (stemming), fuzzy string matching to handle spelling errors, and a mechanism to rank results by similarity to the search string.

**Full-Text Search Syntax*

Full-text search can be complex, but even a basic full-text search query can be a powerful tool. The example below is a basic technique to query a document, in this case, the title column, to match the characters 'elf.' The WHERE clause of the query uses the @@ match operator to compare the values returned by two built-in functions to perform the search, to_tsvector, and to_tsquery.

```sql
SELECT title, description
FROM film
WHERE to_tsvector(title) @@ to_tsquery('elf');
```

These functions convert text and string data into a tsvector data type, which is a sorted list of words that have been normalized into variants of the same word. These variants are called lexemes.

**Exercises:**

**A review of the LIKE operator**

The LIKE operator allows us to filter our queries by matching one or more characters in text data. By using the % wildcard we can match one or more characters in a string. This is useful when you want to return a result set that matches certain characteristics and can also be very helpful during exploratory data analysis or data cleansing tasks.

Let's explore how different usage of the % wildcard will return different results by looking at the film table of the Sakila DVD Rental database.

**Instructions:**

- Select all columns for all records that begin with the word GOLD.

```sql
-- Select all columns
SELECT *
FROM film
-- Select only records that begin with the word 'GOLD'
WHERE title LIKE 'GOLD%';
```

- Now select all records that end with the word GOLD.

```sql
SELECT *
FROM film
-- Select only records that end with the word 'GOLD'
WHERE title LIKE '%GOLD';
```

- Finally, select all records that contain the word 'GOLD'.

```sql
SELECT *
FROM film
-- Select only records that contain the word 'GOLD'
WHERE title LIKE '%GOLD%';
```

**What is a tsvector?**

You saw how to convert strings to tsvector and tsquery in the video and, in this exercise, we are going to dive deeper into what these functions actually return after converting a string to a tsvector. In this example, you will convert a text column from the film table to a tsvector and inspect the results. Understanding how full-text search works is the first step in more advanced machine learning and data science concepts like natural language processing.

**Instruction:**

- Select the film description and convert it to a tsvector data type.

```sql
-- Select the film description as a tsvector
SELECT to_tsvector(description)
FROM film;
```

**Basic full-text search**

Searching text will become something you do repeatedly when building applications or exploring data sets for data science. Full-text search is helpful when performing exploratory data analysis for a natural language processing model or building a search feature into your application.

In this exercise, you will practice searching a text column and match it against a string. The search will return the same result as a query that uses the LIKE operator with the % wildcard at the beginning and end of the string, but will perform much better and provide you with a foundation for more advanced full-text search queries. Let's dive in.

**Instructions:**

- Select the title and description columns from the film table.

- Perform a full-text search on the title column for the word elf.

```sql
-- Select the title and description
SELECT title, description
FROM film
-- Convert the title to a tsvector and match it against the tsquery 
WHERE to_tsvector(title) @@ to_tsquery('elf');
```

# Extending PostgreSQL

**Personal notes:**

**User-defined Data Types*

User-defined data types are created using the `CREATE TYPE` command, which registers the type in a system table and makes it available for use wherever PostgreSQL expects a type name.

Enumerated data types or ENUMs allow you to define a custom list of values that will never change, such as the days of the week. For example, a new data type called `dayofweek` is defined as an ENUM using the `CREATE TYPE` command with a comma-separated list of the days of the week.

```sql
CREATE TYPE dayofweek AS ENUM (
    'Monday',
    'Tuesday',
    'Wednesday',
    'Thursday',
    'Friday',
    'Saturday',
    'Sunday'
);
```

**Getting Information about User-defined Data Types*

Once your custom data type has been created, you can query the system table called `pg_type` to get information about all the data types available in your database, both user-defined and internal.

```sql
SELECT typname, typcategory
FROM pg_type
WHERE typname = 'dayofweek';
```

The query results return `dayofweek` for the type name of the data type we just created and 'E' for the category, where 'E' represents an ENUM type.

You can also use the INFORMATION_SCHEMA system database, as we learned earlier, to get information about user-defined data types. For example, querying `INFORMATION_SCHEMA.COLUMNS` and looking at the columns in the film table shows that the `rating` column is a user-defined data type with a `udt_name` of `mpaa_rating`.

```sql
SELECT column_name, data_type, udt_name
FROM INFORMATION_SCHEMA.COLUMNS
WHERE table_name = 'film';
```

**User-defined Functions*

Another way to extend the features of your PostgreSQL database is with user-defined functions. A user-defined function is PostgreSQL's equivalent to a stored procedure where you can group multiple queries and SQL statements together into a single package using the `CREATE FUNCTION` command.

In this example, we define the `squared` function, which takes an integer `i` as an input parameter and returns the square of that parameter as the result. The double dollar sign `$$` syntax specifies that the function will use SQL as the language.

```sql
CREATE FUNCTION squared(i integer) RETURNS integer AS $$
BEGIN
    RETURN i*i;
END;
$$ LANGUAGE plpgsql;
```

**User-defined Functions in the sakila Database*

The `get_customer_balance` function takes a `customer_id` and an `effective_date` as input parameters and calculates the current balance of a customer based on the `customer_id` and the timestamp.

The `inventory_held_by_customer` function takes an `inventory_id` as an input parameter and determines all rows that have a `return_date` equal to NULL, indicating that the customer still has the rental.

The `inventory_in_stock` function takes an `inventory_id` as an input parameter and determines if a specific `inventory_id` is in stock.

**Exercises:**

**User-defined data types**

ENUM or enumerated data types are great options to use in your database when you have a column where you want to store a fixed list of values that rarely change. Examples of when it would be appropriate to use an ENUM include days of the week and states or provinces in a country.

Another example can be the directions on a compass (i.e., north, south, east and west.) In this exercise, you are going to create a new ENUM data type called compass_position.

**Instructions:**

- Create a new enumerated data type called compass_position.

- Use the four positions of a compass as the values.

```sql
-- Create an enumerated data type, compass_position
CREATE TYPE compass_position AS ENUM (
  	-- Use the four cardinal directions
  	'North', 
  	'West',
  	'Est', 
  	'South'
);
```

- Select all columns from the pg_type table where the type name is equal to mpaa_rating.

```sql
SELECT *
FROM pg_type
WHERE typname='mpaa_rating'
```

**User-defined functions in Sakila**

If you were running a real-life DVD Rental store, there are many questions that you may need to answer repeatedly like whether a film is in stock at a particular store or the outstanding balance for a particular customer. These types of scenarios are where user-defined functions will come in very handy. The Sakila database has several user-defined functions pre-defined. These functions are available out-of-the-box and can be used in your queries like many of the built-in functions we've learned about in this course.

In this exercise, you will build a query step-by-step that can be used to produce a report to determine which film title is currently held by which customer using the inventory_held_by_customer() function.

**Instructions:**

- Select the title and inventory_id columns from the film and inventory tables in the database.

```sql
-- Select the film title and inventory ids
SELECT 
	f.title, 
    i.inventory_id
FROM film AS f 
	-- Join the film table to the inventory table
	INNER JOIN inventory AS i ON f.film_id=i.film_id
```

- inventory_id is currently held by a customer and alias the column as held_by_cust

```sql
-- Select the film title, rental and inventory ids
SELECT 
	f.title, 
    i.inventory_id,
    -- Determine whether the inventory is held by a customer
    inventory_held_by_customer(i.inventory_id) AS held_by_cust 
FROM film as f 
	-- Join the film table to the inventory table
	INNER JOIN inventory AS i ON f.film_id=i.film_id 
```

- Now filter your query to only return records where the inventory_held_by_customer() function returns a non-null value.

```sql
-- Select the film title and inventory ids
SELECT 
	f.title, 
    i.inventory_id,
    -- Determine whether the inventory is held by a customer
    inventory_held_by_customer(i.inventory_id) as held_by_cust
FROM film as f 
	INNER JOIN inventory AS i ON f.film_id=i.film_id 
WHERE
	-- Only include results where the held_by_cust is not null
    inventory_held_by_customer(i.inventory_id) IS NOT NULL
```

# Intro to PostgreSQL extensions

**Personal notes:**

**Commonly Used Extensions*

In this lesson, we will learn about some common extensions, namely fuzzystrmatch and pg_trgm, that enhance the full-text search capabilities of PostgreSQL. But first, let's delve into the PostgreSQL extension structure in more detail.

**Commonly Used Extensions*

Most PostgreSQL distributions come with a common set of widely used community-supported extensions that can be used by simply enabling them.

- **PostGIS:** Adds support to perform location queries in SQL.
- **PostPic:** Allows image processing within the database.
- **fuzzystrmatch and pg_trgm:** Provide functions that extend full-text search capabilities by finding similarities in strings.

**Querying Extension Metadata*

To discover which extensions are available in your specific PostgreSQL instance, you can query the `pg_available_extensions` system view, as shown in the example below, to determine a list of extensions that are available for installation and activation. The results return the names of the first two available extensions.

```sql
SELECT name
FROM pg_available_extensions;
```

A similar query on the `pg_extension` system table will tell you which extensions have already been activated in your database and are currently available for use.

```sql
SELECT extname
FROM pg_extension;
```

Any of the extensions returned from the `pg_available_extensions` system view can be loaded into your database and activated with a simple query using the `CREATE EXTENSION` command, an example of which is shown below. The `IF NOT EXISTS` clauses can be used to ensure that if the extension was previously enabled, the query will not generate an error message.

```sql
CREATE EXTENSION IF NOT EXISTS fuzzystrmatch;
```

**Using fuzzystrmatch or Fuzzy Searching*

When conducting a full-text search based on user input or seeking to perform natural language processing-based text data analysis and comparison, a function you will often use is `levenshtein` from the `fuzzystrmatch` extension.

The `levenshtein` function calculates the Levenshtein distance between two strings, which is the number of edits needed for the strings to be a perfect match.

```sql
SELECT levenshtein('GUMBO',  'GAMBOL');
```

**Compare Two Strings with pg_trgm*

The `pg_trgm` extension provides functions and operators to determine the similarity of two strings using trigram matches. Trigrams are groups of three consecutive characters in a string, and based on the number of matching trigrams in two strings, it provides a measure of how similar they are. This measurement can be calculated using the `similarity` function of this extension. The `similarity` function accepts two parameters, the first being the string you want to compare, and the second is the string you want to compare it to.

```sql
SELECT similarity('GUMBO', 'GAMBOL');
```

This function returns a number between 0 and 1, with 0 representing no matching trigrams and 1 representing a perfect match.

**Exercises:**

**Enabling extensions**

Before you can use the capabilities of an extension it must be enabled. As you have previously learned, most PostgreSQL distributions come pre-bundled with many useful extensions to help extend the native features of your database. You will be working with fuzzystrmatch and pg_trgm in upcoming exercises but before you can practice using the capabilities of these extensions you will need to first make sure they are enabled in our database. In this exercise you will enable the pg_trgm extension and confirm that the fuzzystrmatch extension, which was enabled in the video, is still enabled by querying the pg_extension system table.

**Instructions:**

- Enable the pg_trgm extension

```sql
-- Enable the pg_trgm extension
CREATE EXTENSION IF NOT EXISTS pg_trgm;
```

- Now confirm that both fuzzystrmatch and pg_trgm are enabled by selecting all rows from the appropriate system table.

```sql
-- Select all rows extensions
SELECT * 
FROM  pg_extension;
```

**Measuring similarity between two strings**

Now that you have enabled the fuzzystrmatch and pg_trgm extensions you can begin to explore their capabilities. First, we will measure the similarity between the title and description from the film table of the Sakila database.

**Instructions:**

- Select the film title and description.

- Calculate the similarity between the title and description.

```sql
-- Select the title and description columns
SELECT 
  title, 
  description, 
  -- Calculate the similarity
  similarity(title, description)
FROM 
  film
```

**Levenshtein distance examples**

Now let's take a closer look at how we can use the levenshtein function to match strings against text data. If you recall, the levenshtein distance represents the number of edits required to convert one string to another string being compared.

In a search application or when performing data analysis on any data that contains manual user input, you will always want to account for typos or incorrect spellings. The levenshtein function provides a great method for performing this task. In this exercise, we will perform a query against the film table using a search string with a misspelling and use the results from levenshtein to determine a match. Let's check it out.

**Instructions:**

- Select the film title and film description.

- Calculate the levenshtein distance for the film title with the string JET NEIGHBOR.

```sql
-- Select the title and description columns
SELECT  
  title, 
  description, 
  -- Calculate the levenshtein distance
  levenshtein(title, 'JET NEIGHBOR') AS distance
FROM 
  film
ORDER BY 3
```

**Putting it all together**

In this exercise, we are going to use many of the techniques and concepts we learned throughout the course to generate a data set that we could use to predict whether the words and phrases used to describe a film have an impact on the number of rentals.

First, you need to create a tsvector from the description column in the film table. You will match against a tsquery to determine if the phrase "Astounding Drama" leads to more rentals per month. Next, create a new column using the similarity function to rank the film descriptions based on this phrase.

**Istructions:**

- Select the title and description for all DVDs from the film table.

- Perform a full-text search by converting the description to a tsvector and match it to the phrase 'Astounding & Drama' using a tsquery in the WHERE clause.

```sql
-- Select the title and description columns
SELECT  
  title, 
  description 
FROM 
  film
WHERE 
  -- Match "Astounding Drama" in the description
 to_tsvector(description) @@ 
  to_tsquery('Astounding & Drama');
```

- Add a new column that calculates the similarity of the description with the phrase 'Astounding Drama'.

- Sort the results by the new similarity column in descending order.

```sql
SELECT 
  title, 
  description, 
  -- Calculate the similarity
  similarity(description,'Astounding Drama')
FROM 
  film 
WHERE 
  to_tsvector(description) @@ 
  to_tsquery('Astounding & Drama') 
ORDER BY 
	similarity(description,'Astounding Drama') DESC;
```

# Exploratory Data Analysis in SQL

**Course Description**

You have access to a database. Now what do you do? Building on your existing skills joining tables,  using basic functions, grouping data, and using subqueries, the next step in your SQL journey is  learning how to explore a database and the data in it.  Using data from Stack Overflow, Fortune 500 companies, and 311 help requests  from Evanston, IL, you'll get familiar with numeric, character, and date/time data types. You'll use  functions to aggregate, summarize, and analyze data without leaving  the database. Errors and inconsistencies in the data won't stop you!  You'll learn common problems to look for  and strategies to clean up messy data. By the end of this course, you'll be ready to start exploring your  own PostgreSQL databases and analyzing the data in them.

# What's in the database?

**Chapter description:**

Start exploring a database by identifying the tables and the foreign keys that link them. Look for missing values, count the number of observations, and join tables to understand how they're related. Learn about coalescing and casting data along the way.

# What's in the database?

**Personal notes:**

You've finally gained access to your company's database, but where do you start? What are the tables? How are they related? What columns exist in the tables?

**Database Client*

A database client is a program used to connect and work with a database. There are many different database clients, each with a different way of retrieving information about table names, columns in each table, and the formal relationships between tables. Refer to your database client's documentation to find commands for extracting this information. You can also obtain information about the database structure from the owner or creator of the database. One form of documentation is an entity-relationship diagram showing tables, their columns, and relationships between tables.

**Select a Few Rows*

After learning the names of tables in the database, one way to get a sense of what's in a table is to simply select a few rows from it. In this example, we use an asterisk to select all columns from the company table and use `LIMIT` to return only 5 rows. Remember that the rows returned from a table are not in a specific order by default.

```sql
SELECT *
FROM company
LIMIT 5;
```

**A Few Reminders*

When starting to explore the content of a table, remember a few additional things. `NULL` indicates missing data in a database. To check which values are `NULL`, use "IS NULL" or "IS NOT NULL"; you cannot use "example = NULL". The `COUNT(*)` function counts the number of rows. If you provide a column name to the `COUNT` function, it counts the number of non-NULL observations in the column, which is equal to the total number of rows minus the number of NULL values. If you count the distinct values of a column `COUNT(DISTINCT column_name)`, you get the number of different non-NULL values in the column. However, if you select these distinct values directly `SELECT DISTINCT COLUMN_NAME`, NULL will be included as a value if it exists in the column, even though it is not counted by the `COUNT` function.

**Exercises:**

**Explore table sizes**

Let's start by exploring five related tables:

stackoverflow: questions asked on Stack Overflow with certain tags
company: information on companies related to tags in stackoverflow
tag_company: links stackoverflow to company
tag_type: type categories applied to tags in stackoverflow
fortune500: information on top US companies
Count the number of rows in a table with

```sql
SELECT count(*) 
  FROM tablename;
Count the number of columns in a table by selecting a few rows and manually counting the columns in the result.
```

Which table has the most rows? Which table has the most columns?

    "stackoverflow has the most rows; fortune500 has the most columns"

**Count missing values**

Which column of fortune500 has the most missing values? To find out, you'll need to check each column individually, although here we'll check just three.

Course Note: While you're unlikely to encounter this issue during this exercise, note that if you run a query that takes more than a few seconds to execute, your session may expire or you may be disconnected from the server. You will not have this issue with any of the exercise solutions, so if your session expires or disconnects, there's an error with your query.

**Instructions:**

- First, figure out how many rows are in fortune500 by counting them.

```sql
-- Select the count of the number of rows
SELECT COUNT(*)
  FROM fortune500;
```

- Subtract the count of the non-NULL ticker values from the total number of rows; alias the difference as missing.

```sql
-- Select the count of ticker, 
-- subtract from the total number of rows, 
-- and alias as missing
SELECT count(*) - COUNT(ticker) AS missing
  FROM fortune500;
```

- Repeat for the profits_change column.

```sql
-- Select the count of profits_change, 
-- subtract from total number of rows, and alias as missing
SELECT count(*) - COUNT(profits_change) AS missing
  FROM fortune500;
```

- Repeat for the industry column.

```sql
-- Select the count of industry, 
-- subtract from total number of rows, and alias as missing
SELECT count(*) - COUNT(industry) AS missing
  FROM fortune500;
```

**Join tables**

Part of exploring a database is figuring out how tables relate to each other. The company and fortune500 tables don't have a formal relationship between them in the database, but this doesn't prevent you from joining them.

To join the tables, you need to find a column that they have in common where the values are consistent across the tables. Remember: just because two tables have a column with the same name, it doesn't mean those columns necessarily contain compatible data. If you find more than one pair of columns with similar data, you may need to try joining with each in turn to see if you get the same number of results.

Reference the entity relationship diagram if needed.

**Instructions:**

- Look at the contents of the company and fortune500 tables. Find a column that they have in common where the values for each company are the same in both tables.

- Join the company and fortune500 tables with an INNER JOIN.

- Select only company.name for companies that appear in both tables.

```sql
SELECT company.name
-- Table(s) to select from
  FROM company
       INNER JOIN fortune500
       ON company.ticker=fortune500.ticker;
```

# The keys to the database

**Personal notes:**

The second stage of exploring a database is understanding the formal relationships or links between tables. These explicit relationships are one of the benefits of having your data in a database rather than individual data files. Foreign keys are the formal way that database tables are linked, for example, a `film_actor` table with an `actor_id` column serves as a foreign key to the `actor` table, which has an `id` column.

**Foreign Keys*

A foreign key is a column that references a single specific row in the database. The referenced row is usually in a different table, but foreign keys can also reference a row in the same table. Foreign keys reference other rows using a unique identifier for the row. The unique ID typically comes from a primary key column in the referenced table. Primary keys are specially designated columns where each row has a unique and non-NULL value. Foreign key columns are constrained to contain a value that is in the referenced column or NULL. If the value is NULL, it indicates there is no relationship for that row.

**COALESCE Function*

`COALESCE` takes two or more values or column names as arguments. The three dots in brackets here indicate that additional values can be provided as inputs. The function operates row-wise on the input. It returns the first non-NULL value for each row, checking the columns in the order they are provided to the function. It is useful for specifying default or fallback values when selecting a column that may contain NULL values.

**Exercises:**

**Foreign keys**

Recall that foreign keys reference another row in the database via a unique ID. Values in a foreign key column are restricted to values in the referenced column OR NULL.

Using what you know about foreign keys, why can't the tag column in the tag_type table be a foreign key that references the tag column in the stackoverflow table?

Remember, you can reference the slides using the icon in the upper right of the screen to review the requirements for a foreign key.

    "stackoverflow.tag contains duplicate values"

**Read an entity relationship diagram**

The information you need is sometimes split across multiple tables in the database.

What is the most common stackoverflow tag_type? What companies have a tag of that type?

To generate a list of such companies, you'll need to join three tables together.

Reference the entity relationship diagram as needed when determining which columns to use when joining tables.

**Instructions:**

- First, using the tag_type table, count the number of tags with each type.

- Order the results to find the most common tag type.

```sql
SELECT type, count(*) AS count
  FROM tag_type
  GROUP BY type
  ORDER BY count ASC
```

- Join the tag_company, company, and tag_type tables, keeping only mutually occurring records.

- Select company.name, tag_type.tag, and tag_type.type for tags with the most common type from the previous step.

```sql
-- Select the 3 columns desired
SELECT company.name, tag_type.tag, tag_type.type
  FROM company
  	   -- Join to the tag_company table
       INNER JOIN tag_company 
       ON company.id = tag_company.company_id
       -- Join to the tag_type table
       INNER JOIN tag_type
       ON tag_company.tag = tag_type.tag
  -- Filter to most common type
  WHERE type='cloud';
```

**Coalesce**

The coalesce() function can be useful for specifying a default or backup value when a column contains NULL values.

coalesce() checks arguments in order and returns the first non-NULL value, if one exists.

coalesce(NULL, 1, 2) = 1
coalesce(NULL, NULL) = NULL
coalesce(2, 3, NULL) = 2
In the fortune500 data, industry contains some missing values. Use coalesce() to use the value of sector as the industry when industry is NULL. Then find the most common industry.

**Instructions:**

- Use coalesce() to select the first non-NULL value from industry, sector, or 'Unknown' as a fallback value.

- Alias the result of the call to coalesce() as industry2.

- Count the number of rows with each industry2 value.

- Find the most common value of industry2.

```sql
-- Use coalesce
SELECT COALESCE(industry, sector, 'Unknown') AS industry2,
       -- Don't forget to count!
       COUNT(*) AS industry_count
  FROM fortune500
-- Group by what? (What are you counting by?)
 GROUP BY industry2
-- Order results to see most common first
 ORDER BY industry_count DESC
-- Limit results to get just the one value you want
 LIMIT 1;
```

**Coalesce with a self-join**

You previously joined the company and fortune500 tables to find out which companies are in both tables. Now, also include companies from company that are subsidiaries of Fortune 500 companies as well.

To include subsidiaries, you will need to join company to itself to associate a subsidiary with its parent company's information. To do this self-join, use two different aliases for company.

coalesce will help you combine the two ticker columns in the result of the self-join to join to fortune500.

**Instructions:**

- Join company to itself to add information about a company's parent to the original company's information.

- Use coalesce to get the parent company ticker if available and the original company ticker otherwise.

- INNER JOIN to fortune500 using the ticker.

- Select original company name, fortune500 title and rank.

```sql
SELECT company_original.name, title, rank
  -- Start with original company information
  FROM company AS company_original
       -- Join to another copy of company with parent
       -- company information
	   LEFT JOIN company AS company_parent
       ON company_original.parent_id = company_parent.id
       -- Join to fortune500, only keep rows that match
       INNER JOIN fortune500 
       -- Use parent ticker if there is one, 
       -- otherwise original ticker
       ON coalesce(company_parent.ticker, 
                   company_original.ticker) = 
             fortune500.ticker
 -- For clarity, order by rank
 ORDER BY rank; 
```

# Column types and constraints

**Personal notes:**

In this lesson, we'll revisit the content of individual columns: data types and constraints on what values can exist in each column.

**Column Constraints*

Foreign keys and primary keys are two types of constraints that limit the values in a column, but columns can also be restricted in other ways. `UNIQUE` means that each value, except `NULL`, must be different from the values in all other rows. `NOT NULL` means the column cannot contain null values. Check constraints are a way to implement additional conditions on column values, such as requiring the column to contain only positive values (`column1 > 0`) or ensuring that the value of one column is greater than the value of another column (`columnA > columnB`).

**Data Types*

Constraints may limit the values in a column, but the main factor determining which values are allowed is the column type. Each column in the database can store only one data type. We'll explore numeric data, character data, date/time data, and boolean data types – the most common types we encounter, but not the only ones. There are also special data types for storing monetary values, data like points or lines, and structured data types like XML and JSON. These special types vary more between database implementations than the four common ones.

**Casting with CAST()*

Values can be temporarily converted from one type to another through a process called casting. When you convert a column as a different type, the data is converted to the new type only for the current query. To change the type of a value, use the `CAST` function. Specify the value you want to convert, which can be a single value or the name of a column. Then use the `AS` keyword and specify the name of the type to which you want to convert the data. Here's an example of converting the single numeric value 3.7 to an integer. The conversion from numeric to integer rounds the value to the nearest integer, which is 4.

```sql
SELECT CAST(3.7 AS integer); -- Returns the integer value 4
```

To convert the type of an entire column, insert the column name as the value. Below, a column named `total` is converted to the `integer` type. We need a `FROM` clause to specify from which table the column comes.

```sql
SELECT CAST(total AS integer)
FROM prices;
```

There's an alternative notation for conversion values, using double colons:

```sql
SELECT value::new_type;
```

**Exercises:**

**Effects of casting**

When you cast data from one type to another, information can be lost or changed. See how the casting changes values and practice casting data using the CAST() function and the :: syntax.

```sql
SELECT CAST(value AS new_type);

SELECT value::new_type;
```

**Instructions:**

- Select profits_change and profits_change cast as integer from fortune500.
Look at how the values were converted.

```sql
-- Select the original value
SELECT profits_change, 
	   -- Cast profits_change
       CAST(profits_change AS  integer) AS profits_change_int
  FROM fortune500;
```

- Compare the results of casting of dividing the integer value 10 by 3 to the result of dividing the numeric value 10 by 3.

```sql
-- Divide 10 by 3
SELECT 10/3, 
       -- Cast 10 as numeric and divide by 3
       10::numeric/3;
```

- Now cast numbers that appear as text as numeric.
Note: 1e3 is scientific notation.

```sql
SELECT '3.2'::numeric,
       '-123'::numeric,
       '1e3'::numeric,
       '1e-3'::numeric,
       '02314'::numeric,
       '0002'::numeric;
```

**Summarize the distribution of numeric values**

Was 2017 a good or bad year for revenue of Fortune 500 companies? Examine how revenue changed from 2016 to 2017 by first looking at the distribution of revenues_change and then counting companies whose revenue increased.

**Instructions:**

- Use GROUP BY and count() to examine the values of revenues_change.

- Order the results by revenues_change to see the distribution.

```sql
-- Select the count of each value of revenues_change
SELECT revenues_change, COUNT(*)
  FROM fortune500
GROUP BY revenues_change
 -- order by the values of revenues_change
 ORDER BY revenues_change;
```

- Repeat step 1, but this time, cast revenues_change as an integer to reduce the number of different values.

```sql
-- Select the count of each revenues_change integer value
SELECT revenues_change::integer, COUNT(*)
  FROM fortune500
 GROUP BY revenues_change::integer
 -- order by the values of revenues_change
 ORDER BY revenues_change;
```

- How many of the Fortune 500 companies had revenues increase in 2017 compared to 2016? To find out, count the rows of fortune500 where revenues_change indicates an increase.

```sql
-- Count rows 
SELECT COUNT(*)
  FROM fortune500
 -- Where...
 WHERE revenues_change > 0;
```

# Summarizing and aggregating numeric data

**Chapter description:**

You'll build on functions like min and max to summarize numeric data in new ways. Add average, variance, correlation, and percentile functions to your toolkit, and learn how to truncate and round numeric values too. Build complex queries and save your results by creating temporary tables.

# Numeric data types and summary functions

**Personal notes:**

There are 10 different numeric data types. First, the `integer` types. The base type is called `integer`, which can be abbreviated to `int`. It allows integers between approximately negative 2 billion and positive 2 billion. There are also `smallint` and `bigint` types with different ranges. `Serial` types are used for entire columns that automatically increment. They are used to generate ID columns for data that doesn't yet contain a unique identifier.

![Image 2](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/34806e1c-4241-412e-a6a2-bf1f8e57c3df)

There are also 3 decimal types with different precision levels. `Decimal` and `numeric` are two names for the same type. They can store numbers with very high precision. Precision refers to the number of digits in a number. `Real` and `double precision` types can store less precise numbers, meaning fewer digits in the number. One way in which column types are important is that functions and operators can behave differently for different data types.

![Image 3](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/f07b3270-b379-4b7d-a35b-34a2850ea0a4)

**Division*

When you divide integers, the result is truncated to also be an integer. If you include a decimal number in the calculation, the result becomes a decimal number as well.

**Range: Min and Max*

It's always good to check the range and summary statistics of values in a column. This can be done using the `MIN` and `MAX` functions.

**Variance*

Variance is a statistical measure of the amount of spread in a set of values. It tells how far the spread-out values are from the mean. Larger values indicate greater dispersion. Variance can be calculated for a sample of data or for a population. The formula is the same, except that the population variance is divided by the number of values, while the sample variance is divided by the number of values minus one. The `var_pop` function calculates the population variance.

```sql
SELECT var_pop(question_pct)
FROM stackoverflow;
```

The `var_samp` function calculates the sample variance. The sample variance will always be slightly larger than the population variance. The `variance` function is an alias for `var_samp`.

```sql
SELECT var_samp(question_pct)
FROM stackoverflow;
```

**Standard Deviation*

Standard deviation is another measure of variance. It is the square root of the variance. Similar to variance, there are functions for both sample and population versions of standard deviation.

```sql
SELECT stddev(question_pct)
FROM stackoverflow;
```

```sql
SELECT stddev_samp(question_pct)
FROM stackoverflow;
```

```sql
SELECT stddev_pop(question_pct)
FROM stackoverflow;
```

**Round*

Functions can return results with many decimal places. To make the results more readable, use the `round` function to round a numeric value to a specified number of decimal places. The `round` function takes a numeric value or column as the first parameter and the number of decimal places to retain as the second argument.

```sql
SELECT round(42.1256, 2);
```

**Summarize by Group*

In addition to calculating summary measures for entire columns, it's also good practice to summarize variables by groups of data. For example, besides summarizing the `question_pct` column in the overall `stackoverflow` table, we also want to calculate summary measures for each tag.

```sql
SELECT tag,
       MIN(question_pct),
       MAX(question_pct),
       AVG(question_pct)
FROM stackoverflow
GROUP BY tag;
```

**Exercises:**

**Division**

Compute the average revenue per employee for Fortune 500 companies by sector.

**Instructions:**

- Compute revenue per employee by dividing revenues by employees; use casting to produce a numeric result.

- Take the average of revenue per employee with avg(); alias this as avg_rev_employee.

- Group by sector.

- Order by the average revenue per employee.

```sql
-- Select average revenue per employee by sector
SELECT sector,
       AVG(revenues/employees::numeric) AS avg_rev_employee
  FROM fortune500
 GROUP BY sector
 -- Use the column alias to order the results
 ORDER BY avg_rev_employee;
```

**Explore with division**

In exploring a new database, it can be unclear what the data means and how columns are related to each other.

What information does the unanswered_pct column in the stackoverflow table contain? Is it the percent of questions with the tag that are unanswered (unanswered ?s with tag/all ?s with tag)? Or is it something else, such as the percent of all unanswered questions on the site with the tag (unanswered ?s with tag/all unanswered ?s)?

Divide unanswered_count (unanswered ?s with tag) by question_count (all ?s with tag) to see if the value matches that of unanswered_pct to determine the answer.

**Instructions:**

- Exclude rows where question_count is 0 to avoid a divide by zero error.

- Limit the result to 10 rows.

```sql
-- Divide unanswered_count by question_count
SELECT unanswered_count/question_count::decimal AS computed_pct, 
       -- What are you comparing the above quantity to?
       unanswered_pct
  FROM stackoverflow
 -- Select rows where question_count is not 0
 WHERE question_count != 0
 LIMIT 10;
```

**Summarize numeric columns**

Summarize the profit column in the fortune500 table using the functions you've learned.

You can access the course slides for reference using the PDF icon in the upper right corner of the screen.

**Instructions:**

- Compute the min(), avg(), max(), and stddev() of profits.

```sql
-- Select min, avg, max, and stddev of fortune500 profits
SELECT MIN(profits),
       MAX(profits),
       AVG(profits),
       STDDEV(profits)
  FROM fortune500;
```

- Now repeat step 1, but summarize profits by sector.
Order the results by the average profits for each sector.

```sql
-- Select sector and summary measures of fortune500 profits
SELECT MIN(profits),
       MAX(profits),
       AVG(profits),
       STDDEV(profits)
  FROM fortune500
 -- What to group by?
 GROUP BY sector
 -- Order by the average profits
 ORDER BY AVG;
```

**Summarize group statistics**

Sometimes you want to understand how a value varies across groups. For example, how does the maximum value per group vary across groups?

To find out, first summarize by group, and then compute summary statistics of the group results. One way to do this is to compute group values in a subquery, and then summarize the results of the subquery.

For this exercise, what is the standard deviation across tags in the maximum number of Stack Overflow questions per day? What about the mean, min, and max of the maximums as well?

**Instructions:**

- Start by writing a subquery to compute the max() of question_count per tag; alias the subquery result as maxval.

- Then compute the standard deviation of maxval with stddev().

- Compute the min(), max(), and avg() of maxval too.

```sql
-- Compute standard deviation of maximum values
SELECT stddev(maxval),
       -- min
       min(maxval),
       -- max
       max(maxval),
       -- avg
       avg(maxval)
  -- Subquery to compute max of question_count by tag
  FROM (SELECT max(question_count) AS maxval
          FROM stackoverflow
         -- Compute max by...
         GROUP BY tag) AS max_results; -- alias for subquery
```

# Exploring distributions

**Personal notes:**

Understanding the distribution of a variable is crucial for finding errors, outliers, and other anomalies in the data.

**Count Values*

For columns with a small number of discrete values, you can visualize the distribution by counting the number of observations with each distinct value. You can group and order the results by the column of interest. For example, counting the occurrences of distinct values in the `unanswered_count` column in the `stackoverflow` data with the tag `amazon-ebs`:

```sql
SELECT unanswered_count, COUNT(*)
FROM stackoverflow
WHERE tag='amazon-ebs'
GROUP BY unanswered_count
ORDER BY unanswered_count;
```

When dealing with a large number of distinct values, categorizing or grouping the values can make the output more useful.

**Truncate*

The `trunc` function is used to reduce the precision of a number by replacing the least significant numeric places with zeros. Truncation is different from rounding; you will never get a result with an absolute value greater than the original number. The `trunc` function takes two arguments: the value to be truncated and the number of places to truncate it.

```sql
SELECT trunc(42.1256, 2); -- returns 42.12
```

Negative values for the second argument indicate places before the decimal to replace with zero.

```sql
SELECT trunc(12345, -3); -- returns 12000
```

**Truncating and Grouping*

The `trunc` function can be used to group values in the `unanswered_count` column into three groups based on the digit in the tens place of the number.

```sql
SELECT trunc(unanswered_count, -1) AS trunc_ua, COUNT(*)
FROM stackoverflow
WHERE tag='amazon-ebs'
GROUP BY trunc_ua 
ORDER BY trunc_ua;
```

**Generate Series*

The `generate_series` function generates a series of numbers from a start value to an end value, inclusive, in steps of a third value.

```sql
SELECT generate_series(start, end, step);
```

For example, you can generate a series from 1 to 10 in steps of 2 or a series from 0 to 1 in steps of 1/10. `generate_series` can be used to group values into buckets.

In the example below, we want to create a series of lower and upper values and count the number of observations that fall into each bin. We use a `WITH` clause to create an alias for the results of a subquery to use later in the main query. We generate two series: one for the lower bounds of the bin and another for the upper bounds. As we are only summarizing data for the `amazon-ebs` tag, we create a subset of the `stackoverflow` table called `ebs`. Then, we write the main selection query to join the results of the subqueries we created and count the values. We join `ebs` and `bins` where the `unanswered_count` column is greater than or equal to the lower limit and strictly less than the upper limit. A left join keeps all bins in the result, even those without values in them. Finally, we group by the lower or upper bin values to count the values in each bin.

```sql
-- Create bins
WITH bins AS (
    SELECT generate_series(30, 60, 5) AS lower,
           generate_series(35, 65, 5) AS upper
    -- Subset data to tag of interest
    ),
    ebs AS (
    SELECT unanswered_count
    FROM stackoverflow
    WHERE tag='amazon-ebs'
)
-- Count values in each bin
SELECT lower, upper, COUNT(unanswered_count)
-- Left join keeps all bins
FROM bins
    LEFT JOIN ebs
    ON unanswered_count >= lower
    AND unanswered_count < upper
-- Group by bin bounds to create the groups
GROUP BY lower, upper
ORDER BY lower;
```

Each row in the output has the count of days where the number of questions was greater than or equal to the lower limit and strictly less than the upper limit. Note that the result contains bins with values of 0 because we counted non-null `unanswered_count` values rather than just the number of rows.

**Exercises:**

**Truncate**

Use trunc() to examine the distributions of attributes of the Fortune 500 companies.

Remember that trunc() truncates numbers by replacing lower place value digits with zeros:

    trunc(value_to_truncate, places_to_truncate)

Negative values for places_to_truncate indicate digits to the left of the decimal to replace, while positive values indicate digits to the right of the decimal to keep.

**Instructions:**

- Use trunc() to truncate employees to the 100,000s (5 zeros).
Count the number of observations with each truncated value.

```sql
-- Truncate employees
SELECT trunc(employees, -5) AS employee_bin,
       -- Count number of companies with each truncated value
       COUNT(*)
  FROM fortune500
 -- Use alias to group
 GROUP BY employee_bin
 -- Use alias to order
 ORDER BY employee_bin;
```

- Repeat step 1 for companies with < 100,000 employees (most common).
This time, truncate employees to the 10,000s place.

```sql
-- Truncate employees
SELECT trunc(employees, -4) AS employee_bin,
       -- Count number of companies with each truncated value
       COUNT(*)
  FROM fortune500
 -- Limit to which companies?
 WHERE employees <= 100000
 -- Use alias to group
 GROUP BY employee_bin
 -- Use alias to order
 ORDER BY employee_bin;
```

**Generate series**

Summarize the distribution of the number of questions with the tag "dropbox" on Stack Overflow per day by binning the data.

Recall:
```sql
generate_series(from, to, step)
```
You can reference the slides using the PDF icon in the upper right corner of the screen.

**Instructions:**

- Start by selecting the minimum and maximum of the question_count column for the tag 'dropbox' so you know the range of values to cover with the bins.

```sql
-- Select the min and max of question_count
SELECT MIN(question_count), 
       MAX(question_count)
  -- From what table?
  FROM stackoverflow
 -- For tag dropbox
 WHERE tag='dropbox';
```

- Next, use generate_series() to create bins of size 50 from 2200 to 3100.

- To do this, you need an upper and lower bound to define a bin.

- This will require you to modify the stopping value of the lower bound and the starting value of the upper bound by the bin width.

```sql
-- Create lower and upper bounds of bins
SELECT generate_series(2200, 3050, 50) AS lower,
       generate_series(2250, 3100, 50) AS upper;
```

- Select lower and upper from bins, along with the count of values within each bin bounds.

- To do this, you'll need to join 'dropbox', which contains the question_count for tag "dropbox", to the bins created by generate_series().

- The join should occur where the count is greater than or equal to the lower bound, and strictly less than the upper bound.

```sql
-- Bins created in Step 2
WITH bins AS (
      SELECT generate_series(2200, 3050, 50) AS lower,
             generate_series(2250, 3100, 50) AS upper),
     -- Subset stackoverflow to just tag dropbox (Step 1)
     dropbox AS (
      SELECT question_count 
        FROM stackoverflow
       WHERE tag='dropbox') 
-- Select columns for result
-- What column are you counting to summarize?
SELECT lower, upper, count(question_count) 
  FROM bins  -- Created above
       -- Join to dropbox (created above), 
       -- keeping all rows from the bins table in the join
       LEFT JOIN dropbox
       -- Compare question_count to lower and upper
         ON question_count >= lower 
        AND question_count < upper
 -- Group by lower and upper to count values in each bin
 GROUP BY lower, upper
 -- Order by lower to put bins in order
 ORDER BY lower;
```

# More summary functions

**Personal notes:**

So far, we have summarized individual columns. However, sometimes we want to understand the relationship between two columns. Correlation is a measure of the relationship between two variables. A correlation coefficient can range from 1 to -1, with larger values indicating a stronger positive relationship and more negative values indicating a stronger negative relationship.

**Correlation Function*

The `corr` function takes the names of two columns as arguments and returns the correlation between them. Rows with a null value in either column are excluded.

```sql
SELECT corr(assets, equity)
FROM fortune500;
```

**Median*

The median is the 50th percentile or midpoint in an ordered list of values. To obtain the median, use a percentile function like `percentile_disc`. The syntax for percentile functions is different from other functions because the data must be ordered for the calculation. It's called ordered-set aggregate syntax. The only argument for the function is a number between 0 and 1 corresponding to the desired percentile. You then type `WITHIN GROUP` and, in parentheses, order using `ORDER BY` and the name of the column for which you want to calculate the percentile. The `percentile_disc` function, which is the discrete percentile, always returns a value that exists in the column:

```sql
SELECT percentile_disc(percentile) WITHIN GROUP (ORDER BY column_name)
FROM table;
```

On the other hand, `percentile_cont`, or continuous percentile, interpolates between values around the specified percentile. It can return a value that is not in the original data.

```sql
SELECT percentile_cont(percentile) WITHIN GROUP (ORDER BY column_name)
FROM table;
```

**Percentile Examples*

For example, if we have four numbers: 1, 3, 4, and 5, the two percentile functions return different values for the median. The `percentile_disc` function returns 3, while the `percentile_cont` function interpolates between 3 and 4 to return 3.5.

```sql
SELECT val
FROM nums;

SELECT percentile_disc(0.5) WITHIN GROUP (ORDER BY val),
       percentile_cont(0.5) WITHIN GROUP (ORDER BY val)
FROM nums;
```

The formula used to calculate percentiles is quite complex, and sometimes the results may not be intuitive. Be aware that these functions may not always return the value you might expect for the 50th percentile, especially with an even number of values.

**Common Issues*

Before practicing the use of these functions, there are some common issues with numerical values that you should be aware of. First, error codes: sometimes certain values, such as 9, 99, or -99, may have a special meaning and not be true data values. Check any documentation for your database and be wary of values that seem out of place. These special codes may also denote missing values.

There are also additional special values, usually combinations of the letters N and A, used to denote missing values in other programs. It's also good to check whether 0 actually means 0 in the data and is not missing. In addition to errors or missing value codes, you also want to check for extreme outlier values. These may indicate data entry errors or other issues with the data.

Finally, just because data is in a numerical column type does not mean it should be treated as a number. ZIP codes might be stored in a numerical column, but it doesn't make sense to calculate the mean or variance of ZIP codes. Numeric values are also sometimes used to encode multiple-choice survey responses, even if the response options do not correspond to a numerical scale.

**Exercises:**

**Correlation**

What's the relationship between a company's revenue and its other financial attributes? Compute the correlation between revenues and other financial variables with the corr() function.

**Instructions:**

- Compute the correlation between revenues and profits.

- Compute the correlation between revenues and assets.

- Compute the correlation between revenues and equity.

```sql
-- Correlation between revenues and profit
SELECT corr(revenues, profits) AS rev_profits,
	   -- Correlation between revenues and assets
       corr(revenues, assets) AS rev_assets,
       -- Correlation between revenues and equity
       corr(revenues, equity) AS rev_equity 
  FROM fortune500;
```

**Mean and Median**

Compute the mean (avg()) and median assets of Fortune 500 companies by sector.

Use the percentile_disc() function to compute the median:
```sql
percentile_disc(0.5) 
WITHIN GROUP (ORDER BY column_name)
```

**Instructions:**

- Select the mean and median of assets.

- Group by sector.

- Order the results by the mean.

```sql
-- What groups are you computing statistics by?
SELECT sector,
       -- Select the mean of assets with the avg function
       AVG(assets) AS mean,
       -- Select the median
       percentile_disc(0.5) WITHIN GROUP (ORDER BY assets) AS median
  FROM fortune500
 -- Computing statistics for each what?
 GROUP BY sector
 -- Order results by a value of interest
 ORDER BY mean;
```

# Creating temporary tables

**Personal notes:**

You need special permissions in a database to create or update tables, but most users can create temporary tables that only they can see and that last only for the duration of a database session. Temporary tables can be useful for holding results to reference later or for breaking complex queries into smaller parts.

**Syntax*

One way to create a temporary table is with a SELECT query. The results of the query are saved as a table that you can use later. To do this, prefix any SELECT query with the words `CREATE TEMP TABLE`, followed by a name for the table you are creating and the keyword `AS`. This copies the result of the SELECT query into a new table that has no connection to the original table.

```sql
-- Create a table as
CREATE TEMP TABLE new_tablename AS
-- Query results to store in the table
SELECT column1, column2
FROM table;
```

There are other ways to create temporary tables as well. Using the `select into` syntax method, you add a special clause in the middle of a SELECT query to direct the results to a new temporary table. In this example, the added clause is the middle line of the code.

```sql
-- Select existing columns
SELECT column1, column2
-- Clause to direct results to a new temp table
INTO TEMP TABLE new_tablename
-- Existing table with existing columns
FROM table;
```

Both queries do the same thing, just with different syntax. In this lesson, we will focus on the `CREATE TEMP TABLE` syntax. It is the recommended method by PostgreSQL and allows for options not available with the `select into` syntax.

**Create a Table*

As an example, let's create a temporary table called `top_companies` with only the rank and title of the top 10 companies from Fortune500. We prefix our SELECT query with the temporary table creation syntax.

```sql
CREATE TEMP TABLE top_companies AS
SELECT rank,
       title
FROM fortune500
WHERE rank <= 10;
```

After creating the table, we can select from it. Note that the column names are taken from the result's column names.

```sql
SELECT *
FROM top_companies;
```

We can also insert new rows into a table after creating it. We use an `INSERT INTO` statement with the table name, followed by a `SELECT` query that generates the rows we want to add to the table. The columns generated by the `SELECT` query must match those already in the table. Here, we add to the table companies with ranks from 11 to 20.

```sql
INSERT INTO top_companies
SELECT rank, title
FROM fortune500
WHERE rank BETWEEN 11 AND 20;
```

Now, if we select from the temporary table `top_companies` again, we can see that the new rows have been added.

**Delete (Drop) Table*

To delete a table, use the `DROP TABLE` command. The table will be deleted immediately without warning. Deleting a table can be useful if you make a mistake when creating it or inserting values into it. Temporary tables will also be automatically deleted when you disconnect from the database.

```sql
DROP TABLE top_companies;
```

A variation of the `DROP TABLE` command adds the `IF EXISTS` clause before the table name. This means only try to delete the table after confirming that such a table exists. This variation is often used in scripts because it won't cause an error if the table does not exist.

```sql
DROP TABLE IF EXISTS top_companies;
```

**Exercises:**

**Create a temp table**

Find the Fortune 500 companies that have profits in the top 20% for their sector (compared to other Fortune 500 companies).

To do this, first, find the 80th percentile of profit for each sector with
```sql
percentile_disc(fraction) 
WITHIN GROUP (ORDER BY sort_expression)
```
and save the results in a temporary table.

Then join fortune500 to the temporary table to select companies with profits greater than the 80th percentile cut-off.

**Instructions:**

- Create a temporary table called profit80 containing the sector and 80th percentile of profits for each sector.

- Alias the percentile column as pct80.

```sql
-- To clear table if it already exists;
-- fill in name of temp table
DROP TABLE IF EXISTS profit80;

-- Create the temporary table
CREATE TEMP TABLE profit80 AS 
  -- Select the two columns you need; alias as needed
  SELECT sector, 
        percentile_disc(0.8) WITHIN GROUP (ORDER BY profits) AS pct80
    -- What table are you getting the data from?
    FROM fortune500
   -- What do you need to group by?
   GROUP BY sector;
   
-- See what you created: select all columns and rows 
-- from the table you created
SELECT * 
  FROM profit80;
```

- Using the profit80 table you created in step 1, select companies that have profits greater than pct80.

- Select the title, sector, profits from fortune500, as well as the ratio of the company's profits to the 80th percentile profit.

```sql
-- Code from previous step
DROP TABLE IF EXISTS profit80;

CREATE TEMP TABLE profit80 AS
  SELECT sector, 
         percentile_disc(0.8) WITHIN GROUP (ORDER BY profits) AS pct80
    FROM fortune500 
   GROUP BY sector;

-- Select columns, aliasing as needed
SELECT title, fortune500.sector, 
       profits, fortune500.profits/pct80 AS ratio
-- What tables do you need to join?  
  FROM fortune500 
       LEFT JOIN profit80
-- How are the tables joined?
       ON fortune500.sector=profit80.sector
-- What rows do you want to select?
 WHERE profits > pct80;
 ```

**Create a temp table to simplify a query**

The Stack Overflow data contains daily question counts through 2018-09-25 for all tags, but each tag has a different starting date in the data.

Find out how many questions had each tag on the first date for which data for the tag is available, as well as how many questions had the tag on the last day. Also, compute the difference between these two values.

To do this, first compute the minimum date for each tag.

Then use the minimum dates to select the question_count on both the first and last day. To do this, join the temp table startdates to two different copies of the stackoverflow table: one for each column - first day and last day - aliased with different names.

**Instructions:**

- First, create a temporary table called startdates with each tag and the min() date for the tag in stackoverflow.

```sql
-- To clear table if it already exists
DROP TABLE IF EXISTS startdates;

-- Create temp table syntax
CREATE TEMP TABLE startdates AS
-- Compute the minimum date for each what?
SELECT tag,
       MIN(date) AS mindate
  FROM stackoverflow
 -- What do you need to compute the min date for each tag?
 WHERE date<'2018-09-25'
 GROUP BY tag;
 -- Look at the table you created
 SELECT * 
   FROM startdates;
```

- Join startdates to stackoverflow twice using different table aliases.

- For each tag, select mindate, question_count on the mindate, and question_count on 2018-09-25 (the max date).

- Compute the change in question_count over time.

```sql
-- To clear table if it already exists
DROP TABLE IF EXISTS startdates;

CREATE TEMP TABLE startdates AS
SELECT tag, min(date) AS mindate
  FROM stackoverflow
 GROUP BY tag;
 
-- Select tag (Remember the table name!) and mindate
SELECT startdates.tag, 
       startdates.mindate,
       -- Select question count on the min and max days
	   so_min.question_count AS min_date_question_count,
       so_max.question_count AS max_date_question_count,
       -- Compute the change in question_count (max - min)
       so_max.question_count - so_min.question_count AS change
  FROM startdates
       -- Join startdates to stackoverflow with alias so_min
       INNER JOIN stackoverflow AS so_min
          -- What needs to match between tables?
          ON startdates.tag = so_min.tag
         AND startdates.mindate = so_min.date
       -- Join to stackoverflow again with alias so_max
       INNER JOIN stackoverflow AS so_max
       	  -- Again, what needs to match between tables?
          ON startdates.tag = so_max.tag
         AND so_max.date = '2018-09-25';
```

**Insert into a temp table**

While you can join the results of multiple similar queries together with UNION, sometimes it's easier to break a query down into steps. You can do this by creating a temporary table and inserting rows into it.

Compute the correlations between each pair of profits, profits_change, and revenues_change from the Fortune 500 data.

  The resulting temporary table should have the following structure:

    measure	         profits	profits_change	revenues_change
    profits	           1.00	         #	             #
    profits_change	     #	        1.00	           #
    revenues_change	     #	         #	           1.00

Recall the round() function to make the results more readable:
```sql
round(column_name::numeric, decimal_places)
```
Note that Steps 1 and 2 do not produce output. It is normal for the query result pane to say "Your query did not generate any results."

**Instructions:**

- Create a temp table correlations.

- Compute the correlation between profits and each of the three variables (i.e. correlate profits with profits, profits with profits_change, etc).

- Alias columns by the name of the variable for which the correlation with profits is being computed.

```sql
DROP TABLE IF EXISTS correlations;

-- Create temp table 
CREATE TEMP TABLE correlations AS
-- Select each correlation
SELECT 'profits'::varchar AS measure,
       -- Compute correlations
       corr(profits, profits) AS profits,
       corr(profits, profits_change) AS profits_change,
       corr(profits, revenues_change) AS revenues_change
  FROM fortune500;
```

- Insert rows into the correlations table for profits_change and revenues_change.

```sql
DROP TABLE IF EXISTS correlations;

CREATE TEMP TABLE correlations AS
SELECT 'profits'::varchar AS measure,
       corr(profits, profits) AS profits,
       corr(profits, profits_change) AS profits_change,
       corr(profits, revenues_change) AS revenues_change
  FROM fortune500;

-- Add a row for profits_change
-- Insert into what table?
INSERT INTO correlations
-- Follow the pattern of the select statement above
-- Using profits_change instead of profits
SELECT 'profits_change'::varchar AS measure,
       corr(profits_change, profits) AS profits,
       corr(profits_change, profits_change) AS profits_change,
       corr(profits_change, revenues_change) AS revenues_change
  FROM fortune500;

-- Repeat the above, but for revenues_change
INSERT INTO correlations
SELECT 'revenues_change'::varchar AS measure,
       corr(revenues_change, profits) AS profits,
       corr(revenues_change, profits_change) AS profits_change,
       corr(revenues_change, revenues_change) AS revenues_change
  FROM fortune500;
```

- Select all rows and columns from the correlations table to view the correlation matrix.

- First, you will need to round each correlation to 2 decimal places.

- The output of corr() is of type double precision, so you will need to also cast columns to numeric.

```sql
DROP TABLE IF EXISTS correlations;

CREATE TEMP TABLE correlations AS
SELECT 'profits'::varchar AS measure,
       corr(profits, profits) AS profits,
       corr(profits, profits_change) AS profits_change,
       corr(profits, revenues_change) AS revenues_change
  FROM fortune500;

INSERT INTO correlations
SELECT 'profits_change'::varchar AS measure,
       corr(profits_change, profits) AS profits,
       corr(profits_change, profits_change) AS profits_change,
       corr(profits_change, revenues_change) AS revenues_change
  FROM fortune500;

INSERT INTO correlations
SELECT 'revenues_change'::varchar AS measure,
       corr(revenues_change, profits) AS profits,
       corr(revenues_change, profits_change) AS profits_change,
       corr(revenues_change, revenues_change) AS revenues_change
  FROM fortune500;

-- Select each column, rounding the correlations
SELECT measure, 
       ROUND(profits::numeric, 2) AS profits,
       ROUND(profits_change::numeric, 2)  AS profits_change,
       ROUND(revenues_change::numeric, 2)  AS revenues_change
  FROM correlations;
```

# Exploring categorical data and unstructured text

**Chapter description:**

Text, or character, data can get messy, but you'll learn how to deal with inconsistencies in case, spacing, and delimiters. Learn how to use a temporary table to recode messy categorical data to standardized values you can count and aggregate. Extract new variables from unstructured text as you explore help requests submitted to the city of Evanston, IL.

# Character data types and common issues

**Personal notes:**

### Character Data Types and Common Issues

*PostgreSQL Character Type*

There are three types of character columns to store text strings in PostgreSQL: `character(n)`, which can be abbreviated as `char(n)`, `character varying(n)`, which can be abbreviated as `varchar(n)`, and `text`. They differ in the length of the text string they store. The length of a string is defined as the number of characters in it.

- Columns of type `character` store a string of fixed length; spaces are added to the end of shorter strings to compensate for any length difference. Spaces at the end of `char` fields are ignored when comparing values.

- Columns of type `varchar` can optionally specify a maximum string length; they allow strings of any size up to the specified maximum.

- Columns of type `text` or `varchar` without a specified maximum length can store strings of unlimited length.

*Types of Data*

Regardless of the formal column type, for analysis, we want to distinguish two types of text data: categorical variables and unstructured text. Categorical variables are short text strings with values that are repeated across multiple rows. They assume a finite and manageable set of distinct values. Days of the week, product categories, and multiple-choice answers to survey questions are all examples of categorical variables.

Unstructured text consists of longer strings with unique values, such as responses to open-ended survey questions or product reviews. To analyze unstructured text, we can create new variables that extract features from the text or indicate if the text has particular characteristics. For example, we could create binary indicator variables to denote whether the text contains specific keywords of interest.

*Grouping and Counting (Categorical Variables)*

The first things to check with categorical variables are the set of distinct categories and the number of observations, or rows, for each category. We can do this using `GROUP BY` and `COUNT`.

```sql
SELECT category, -- Categorical variable
       COUNT(*)   -- Count rows for each category
FROM product      -- Table
GROUP BY category; -- Categorical variable
```

Without sorting the results, it's challenging to tell which categories are commonly used and if any categories should be grouped.

*Order: Most Frequent Value*

Sorting by the count of each value helps us see the most and least frequent categories. It's good to check if categories with only a few observations have errors—such as spelling mistakes, uppercase/lowercase issues, or spacing.

```sql
SELECT category, -- Categorical variable
       COUNT(*)   -- Count rows for each category
FROM product      -- Table
GROUP BY category -- Categorical variable
ORDER BY count DESC; -- Show most frequent values first
```

*Order: Category Values*

It's also a good idea to try ordering the results by categories. This can help us identify possible duplicates and other errors in the data.

```sql
SELECT category, -- Categorical variable
       COUNT(*)   -- Count rows for each category
FROM product      -- Table
GROUP BY category -- Categorical variable
ORDER BY category;  -- Order by categorical variable
```

**Alphabetical Order*

Character types are sorted in alphabetical order. Spaces come before letters, and uppercase letters come before lowercase letters.

**Common Issues*

Inconsistencies and common issues with character data include:

1. **Differences in Case:*
   - `'apple' != 'Apple'` - case matters

2. **Whitespace Differences:*
   - `' apple' != 'apple'` - space count
   - `'' != '        '`

3. **Empty String vs. NULL:*
   - `'' != NULL` - empty string is not null

4. **Punctuation Differences:*
   - `'to-do' != 'to-do'` - differences in punctuation can be subtle

**Exercises:**

**Count the categories**

In this chapter, we'll be working mostly with the Evanston 311 data in table evanston311. This is data on help requests submitted to the city of Evanston, IL.

This data has several character columns. Start by examining the most frequent values in some of these columns to get familiar with the common categories.

**Instructions:**

- How many rows does each priority level have?

```sql
-- Select the count of each level of priority
SELECT priority, COUNT(*)
  FROM evanston311
 GROUP BY priority;
```

- How many distinct values of zip appear in at least 100 rows?

```sql
-- Find values of zip that appear in at least 100 rows
-- Also get the count of each value
SELECT zip, COUNT(*)
  FROM evanston311
 GROUP BY zip
HAVING COUNT(*) >= 100; 
```

- How many distinct values of source appear in at least 100 rows?

```sql
-- Find values of source that appear in at least 100 rows
-- Also get the count of each value
SELECT source, COUNT(*)
  FROM evanston311
 GROUP BY source
HAVING COUNT(*) >= 100; 
```

- Select the five most common values of street and the count of each.

```sql
-- Find the 5 most common values of street and the count of each
SELECT street, COUNT(*)
  FROM evanston311
 GROUP BY street
ORDER BY count(*) DESC
LIMIT 5;
```

**Spotting character data problems**

Explore the distinct values of the street column. Select each street value and the count of the number of rows with that value. Sort the results by street to see similar values near each other.

Look at the results.

Which of the following is NOT an issue you see with the values of street?

    "There are sometimes extra spaces at the beginning and end of values"

# Cases and spaces

**Personal notes:**

Two of the most common inconsistencies in text data are differences in character case and spaces within a string. We can handle these issues using functions to convert case or remove spaces and querying data with the `LIKE` operator.

*Converting Case*

One of the easiest ways to deal with case inconsistencies is to convert the character data to uppercase or lowercase. The `lower` and `upper` functions do just that. These functions do not affect punctuation or numbers.

```sql
SELECT lower('aBc DeFg 7-'); -- returns abc defg 7-
SELECT upper('aBc DeFg 7-'); -- returns ABC DEFG 7-
```

*Case-Insensitive Comparisons*

You can use the `lower` or `upper` function to perform case-insensitive comparisons. For example, if the fruit data has 8 entries corresponding to 'apple,' but there are 6 different ways to input the data:

```sql
SELECT (*)
FROM fruit;
```

To select rows from the fruit table with the value 'apple' regardless of case, you can convert all `fav_fruit` values to lowercase using the `lower` function. Then, select rows where the result of the function is equal to 'apple,' all lowercase.

```sql
SELECT *
FROM fruit
WHERE lower(fav_fruit) = 'apple';
```

Note that although we have uppercase and lowercase versions of 'apple' in our 5 results, we are still missing 3 values with leading or trailing spaces or with the plural 'apples.'

*Case-Insensitive Searches*

The `LIKE` operator can help match 'apple' values that may have extra spaces or 's' at the end. By using a `LIKE` pattern with a percentage sign before and after 'apple,' we match `fav_fruit` entries where 'apple' is anywhere in the string. Remember, with `LIKE`, the percentage sign matches any number of characters, including zero, while the underscore matches exactly one character.

```sql
SELECT *
FROM fruit
WHERE fav_fruit LIKE '%apple%';
```

To make this query case-insensitive, you can use `ILIKE` instead of `LIKE`. The additional 'I' stands for insensitive. `ILIKE` queries take longer to execute than `LIKE` queries, so use them only when necessary. Using `ILIKE` also selects variations of 'apple' with uppercase characters.

```sql
SELECT *
FROM fruits
WHERE fav_fruit ILIKE '%apple%';
```

*Trimming Spaces*

Returning to the issue of extra spaces, one way to deal with them is by using the `trim` function to remove spaces from one or both ends of a string. `Trim`, or `btrim`, removes spaces from both ends of a string by default. It also has options to use `rtrim`, which removes spaces only from the right, or `ltrim`, which removes spaces only from the left.

By default, `trim` functions remove only the space character, not other whitespace characters like tabs or newlines.

*Trimming Other Values*

While `trim` functions remove spaces by default, you can specify other characters to be removed. You can remove a single character, like an exclamation point, or a set of characters, all together in a single string.

```sql
SELECT trim('Wow!', '!');
SELECT trim('Wow!', '!wW');
```

The `trim` functions are case-sensitive, so in the second example, both uppercase and lowercase versions of the same letter were included. Instead of specifying both lowercase and uppercase versions of the same letter, we can combine functions. Remember that we can nest the call to one function inside another. In the example below, we first convert all characters to lowercase using `lower` and then use the `trim` function to remove exclamation points and the lowercase 'w.'

```sql
SELECT trim(lower('Wow!'), '!w');
```

**Exercises:**

**Trimming**

Some of the street values in evanston311 include house numbers with # or / in them. In addition, some street values end in a ..

Remove the house numbers, extra punctuation, and any spaces from the beginning and end of the street values as a first attempt at cleaning up the values.

**Instructions:**

- Trim digits 0-9, #, /, ., and spaces from the beginning and end of street.

- Select distinct original street value and the corrected street value.

- Order the results by the original street value.

```sql
SELECT distinct street,
       -- Trim off unwanted characters from street
       trim(street, '0, 1, 2, 3, 4, 5, 6, 7, 8, 9, #, /, .') AS cleaned_street
  FROM evanston311
 ORDER BY street;
```

**Exploring unstructured text**

The description column of evanston311 has the details of the inquiry, while the category column groups inquiries into different types. How well does the category capture what's in the description?

LIKE and ILIKE queries will help you find relevant descriptions and categories. Remember that with LIKE queries, you can include a % on each side of a word to find values that contain the word. For example:
```sql
SELECT category
  FROM evanston311
 WHERE category LIKE '%Taxi%';
% matches 0 or more characters.
```
Building up the query through the steps below, find inquires that mention trash or garbage in the description without trash or garbage being in the category. What are the most frequent categories for such inquiries?

**Instructions:**

- Use ILIKE to count rows in evanston311 where the description contains 'trash' or 'garbage' regardless of case.

```sql
-- Count rows
SELECT COUNT(*)
  FROM evanston311
 -- Where description includes trash or garbage
 WHERE description ILIKE '%trash%'
    OR description ILIKE '%garbage%';
```

- category values are in title case. Use LIKE to find category values with 'Trash' or 'Garbage' in them.

```sql
-- Select categories containing Trash or Garbage
SELECT category
  FROM evanston311
 -- Use LIKE
 WHERE category LIKE  '%Trash%'
    OR category LIKE '%Garbage%';
```

- Count rows where the description includes 'trash' or 'garbage' but the category does not.

```sql
-- Count rows
SELECT COUNT(*)
  FROM evanston311 
 -- description contains trash or garbage (any case)
 WHERE (description ILIKE '%trash%'
    OR description ILIKE '%garbage%') 
 -- category does not contain Trash or Garbage
   AND category NOT LIKE '%Trash%'
   AND category NOT LIKE '%Garbage%';
```

- Find the most common categories for rows with a description about trash that don't have a trash-related category.

```sql
-- Count rows with each category
SELECT category, count(*)
  FROM evanston311 
 WHERE (description ILIKE '%trash%'
    OR description ILIKE '%garbage%') 
   AND category NOT LIKE '%Trash%'
   AND category NOT LIKE '%Garbage%'
 -- What are you counting?
 GROUP BY category
 --- order by most frequent values
 ORDER BY count DESC
 LIMIT 10;
```

# Splitting and concatenating text

**Personal notes:**

*Substring*

The `left` and `right` functions take a string or the name of a string column and the number of characters to keep. `left` retains characters from the left, while `right` retains characters counting from the end.

```sql
SELECT left('abcde', 2),  -- First 2 characters
       right('abcde', 2); -- Last 2 characters
```

If the string contains fewer characters than the requested number, only the available characters will be returned.

To extract characters from the middle of a string, you can use the `substring` function. The function takes a string or column to operate on, the keyword `FROM`, the starting character index (starting from 1), the keyword `FOR`, and the number of characters to include in the substring.

```sql
SELECT substring('abcdef' FROM 2 FOR 3); -- returns 'bcd'
SELECT substr('abcdef', 2, 3);
```

*Delimiters*

The second string operation involves splitting a string into parts based on a delimiter. A delimiter is a character, such as a comma, or a string that separates fields or parts of the text.

The `split_part` function takes a string, the delimiter to split the string, and the numerical position of the split part to be returned, counting from one.

```sql
SELECT split_part('a, bc, d', ',' , 2); -- returns 'bc'
SELECT split_part('cats and dogs and fish', ' and ', 1); -- returns 'cats'
```

*Concatenating Text*

The third string operation is concatenation. The `concat` function takes any number of arguments, and it concatenates the text representation of all values into a single string.

```sql
SELECT concat('a', 2, 'cc'); -- Returns 'a2cc'
```

Values can also be concatenated with double pipes (`||`), which is the standard SQL operator for string concatenation. This operator works similarly to the `concat` function, except when null values are included. The `concat` function omits null values, while the double pipes will return NULL if any component is null.

```sql
SELECT 'a' || 2 || 'cc';
```

**Exercises:**

**Concatenate strings**

House number (house_num) and street are in two separate columns in evanston311. Concatenate them together with concat() with a space in between the values.

**Instructions:**

- Concatenate house_num, a space ' ', and street into a single value using the concat().

- Use a trim function to remove any spaces from the start of the concatenated value.

```sql
-- Concatenate house_num, a space, and street
-- and trim spaces from the start of the result
SELECT ltrim(concat(house_num,' ',street)) AS address
  FROM evanston311;
```

**Split strings on a delimiter**

The street suffix is the part of the street name that gives the type of street, such as Avenue, Road, or Street. In the Evanston 311 data, sometimes the street suffix is the full word, while other times it is the abbreviation.

Extract just the first word of each street value to find the most common streets regardless of the suffix.

To do this, use
```sql
split_part(string_to_split, delimiter, part_number)
```

**Instructions:**

- Use split_part() to select the first word in street; alias the result as street_name.

- Also select the count of each value of street_name.

```sql
-- Select the first word of the street value
SELECT split_part(street, ' ', 1) AS street_name, 
       count(*)
  FROM evanston311
 GROUP BY street_name
 ORDER BY count DESC
 LIMIT 20;
```

**Shorten long strings**

The description column of evanston311 can be very long. You can get the length of a string with the length() function.

For displaying or quickly reviewing the data, you might want to only display the first few characters. You can use the left() function to get a specified number of characters at the start of each value.

To indicate that more data is available, concatenate '...' to the end of any shortened description. To do this, you can use a CASE WHEN statement to add '...' only when the string length is greater than 50.

Select the first 50 characters of description when description starts with the word "I".

**Instructions:**

- Select the first 50 characters of description with '...' concatenated on the end where the length() of the description is greater than 50 characters. Otherwise just select the description as is.

- Select only descriptions that begin with the word 'I' and not the letter 'I'.

```sql
-- Select the first 50 chars when length is greater than 50
SELECT CASE WHEN length(description) > 50
            THEN left(description, 50) || '...'
       -- otherwise just select description
       ELSE description
       END
  FROM evanston311
 -- limit to descriptions that start with the word I
 WHERE description LIKE 'I %'
 ORDER BY description;
```

# Strategies for multiple transformations

**Personal notes:**

*Case WHEN*

When you need to apply various transformations to non-overlapping subsets of data, the `CASE WHEN` statement can be beneficial. In the provided example, the goal is to extract the main category from the "category" column—the part before a delimiter. Different `CASE WHEN` conditions are used for distinct delimiters: a colon followed by space, a hyphen surrounded by spaces, and a pipe surrounded by spaces. The last case, in this scenario, goes into the `ELSE` clause. The `LIKE` statement is utilized to select rows with each type of delimiter. Then, the `split_part` function is applied to those rows with the respective delimiter. The result is aliased as "major_category." This extracted category can then be used to group and aggregate the data.

```sql
SELECT
  CASE
    WHEN category LIKE '%:%' THEN split_part(category, ': ', 1)
    WHEN category LIKE '% - %' THEN split_part(category, ' - ', 1)
    ELSE split_part(category, ' | ', 1)
  END AS major_category,
  SUM(businesses)
FROM naics
GROUP BY major_category;
```

*Recording Table*

Another strategy for situations where multiple transformations are needed is to create a temporary table that maps confusing values. You can then use the recoded values in the standardized column by joining the original table with the temporary table.

**Step 1 - CREATE TEMP TABLE*

The first step is to create a temporary table with two columns: "original," containing the distinct values of `fav_fruit`, and "standardized," which will eventually contain the recoded values. Initially, the "standardized" column is filled with the original values.

```sql
CREATE TEMP TABLE recode AS
  SELECT DISTINCT fav_fruit AS original,
                  fav_fruit AS standardized
  FROM fruit;
```

**Step 2 - UPDATE values*

The next step is to update the recoding table using functions to clean up values in the "standardized" column. The format of an update statement is `UPDATE`, then the table name, followed by a `SET` statement where you specify the new values. Update statements can also include a `WHERE` clause to choose which rows to update.

Here, three update statements are needed. In the first one, the standardized value is set to be the lowercase version of the original value with spaces trimmed on both ends.

```sql
UPDATE recode
SET standardized = trim(lower(original));
```

In the second update, the standardized value is set to 'banana' only for rows that contain a double 'n'.

```sql
UPDATE recode
SET standardized = 'banana'
WHERE standardized LIKE '%nn%';
```

The third update statement removes 's' from the end of the standardized value using the `trim` function.

```sql
UPDATE recode
SET standardized = rtrim(standardized, 's');
```

Now, the recoding table contains cleaned and standardized values.

**Step 3: JOIN original and recode tables*

The final step is to use the recoding table by joining it with the original data.

```sql
SELECT standardized,
       COUNT(*)
FROM fruit
LEFT JOIN recode ON fav_fruit = original
GROUP BY standardized;
```

**Exercises:**

**Group and recode values**

There are almost 150 distinct values of evanston311.category. But some of these categories are similar, with the form "Main Category - Details". We can get a better sense of what requests are common if we aggregate by the main category.

To do this, create a temporary table recode mapping distinct category values to new, standardized values. Make the standardized values the part of the category before a dash ('-'). Extract this value with the split_part() function:
```sql
split_part(string text, delimiter text, field int)
```
You'll also need to do some additional cleanup of a few cases that don't fit this pattern.

Then the evanston311 table can be joined to recode to group requests by the new standardized category values.

**Instructions:**

- Create recode with a standardized column; use split_part() and then rtrim() to remove any remaining whitespace on the result of split_part().

```sql
-- Fill in the command below with the name of the temp table
DROP TABLE IF EXISTS recode;

-- Create and name the temporary table
CREATE TEMP TABLE recode AS
-- Write the select query to generate the table 
-- with distinct values of category and standardized values
  SELECT DISTINCT category, 
         rtrim(split_part(category, '-', 1)) AS standardized
    -- What table are you selecting the above values from?
    FROM evanston311;
    
-- Look at a few values before the next step
SELECT DISTINCT standardized 
  FROM recode
 WHERE standardized LIKE 'Trash%Cart'
    OR standardized LIKE 'Snow%Removal%';
```

- UPDATE standardized values LIKE 'Trash%Cart' to 'Trash Cart'.

- UPDATE standardized values of 'Snow Removal/Concerns' and 'Snow/Ice/Hazard Removal' to 'Snow Removal'.

```sql
-- Code from previous step
DROP TABLE IF EXISTS recode;

CREATE TEMP TABLE recode AS
  SELECT DISTINCT category, 
         rtrim(split_part(category, '-', 1)) AS standardized
    FROM evanston311;

-- Update to group trash cart values
UPDATE recode 
   SET standardized='Trash Cart' 
 WHERE standardized LIKE 'Trash%Cart';

-- Update to group snow removal values
UPDATE recode 
   SET standardized ='Snow Removal' 
 WHERE standardized LIKE 'Snow%Removal%';
    
-- Examine effect of updates
SELECT DISTINCT standardized 
  FROM recode
 WHERE standardized LIKE 'Trash%Cart'
    OR standardized LIKE 'Snow%Removal%';
```

- UPDATE recode by setting standardized values of 'THIS REQUEST IS INACTIVE…Trash Cart', '(DO NOT USE) Water Bill', 'DO NOT USE Trash', and 'NO LONGER IN USE' to 'UNUSED'.

```sql
-- Code from previous step
DROP TABLE IF EXISTS recode;

CREATE TEMP TABLE recode AS
  SELECT DISTINCT category, 
         rtrim(split_part(category, '-', 1)) AS standardized
    FROM evanston311;
  
UPDATE recode SET standardized='Trash Cart' 
 WHERE standardized LIKE 'Trash%Cart';

UPDATE recode SET standardized='Snow Removal' 
 WHERE standardized LIKE 'Snow%Removal%';

-- Update to group unused/inactive values
UPDATE recode 
   SET standardized='UNUSED' 
 WHERE standardized IN ('THIS REQUEST IS INACTIVE...Trash Cart', 
               '(DO NOT USE) Water Bill',
               'DO NOT USE Trash', 'NO LONGER IN USE');

-- Examine effect of updates
SELECT DISTINCT standardized 
  FROM recode
 ORDER BY standardized;
```

- Now, join the evanston311 and recode tables to count the number of requests with each of the standardized values

- List the most common standardized values first.

```sql
-- Code from previous step
DROP TABLE IF EXISTS recode;
CREATE TEMP TABLE recode AS
  SELECT DISTINCT category, 
         rtrim(split_part(category, '-', 1)) AS standardized
  FROM evanston311;
UPDATE recode SET standardized='Trash Cart' 
 WHERE standardized LIKE 'Trash%Cart';
UPDATE recode SET standardized='Snow Removal' 
 WHERE standardized LIKE 'Snow%Removal%';
UPDATE recode SET standardized='UNUSED' 
 WHERE standardized IN ('THIS REQUEST IS INACTIVE...Trash Cart', 
               '(DO NOT USE) Water Bill',
               'DO NOT USE Trash', 'NO LONGER IN USE');

-- Select the recoded categories and the count of each
SELECT standardized, COUNT(*)
-- From the original table and table with recoded values
  FROM evanston311
       LEFT JOIN recode 
       -- What column do they have in common?
       ON evanston311.category=recode.category
 -- What do you need to group by to count?
 GROUP BY standardized
 -- Display the most common val values first
 ORDER BY COUNT DESC;
```

**Create a table with indicator variables**

Determine whether medium and high priority requests in the evanston311 data are more likely to contain requesters' contact information: an email address or phone number.

Emails contain an @.
Phone numbers have the pattern of three characters, dash, three characters, dash, four characters. For example: 555-555-1212.
Use LIKE to match these patterns. Remember % matches any number of characters (even 0), and _ matches a single character. Enclosing a pattern in % (i.e. before and after your pattern) allows you to locate it within other text.

For example, '%___.com%'would allow you to search for a reference to a website with the top-level domain '.com' and at least three characters preceding it.

Create and store indicator variables for email and phone in a temporary table. LIKE produces True or False as a result, but casting a boolean (True or False) as an integer converts True to 1 and False to 0. This makes the values easier to summarize later.

**Instructions:**

- Create a temp table indicators from evanston311 with three columns: id, email, and phone.

- Use LIKE comparisons to detect the email and phone patterns that are in the description, and cast the result as an integer with CAST().

- Your phone indicator should use a combination of underscores _ and dashes - to represent a standard 10-digit phone number format.

- Remember to start and end your patterns with % so that you can locate the pattern within other text!

```sql
-- To clear table if it already exists
DROP TABLE IF EXISTS indicators;

-- Create the indicators temp table
CREATE TEMP TABLE indicators AS
  -- Select id
  SELECT id, 
         -- Create the email indicator (find @)
         CAST (description LIKE '%@%' AS integer) AS email,
         -- Create the phone indicator
         CAST (description LIKE '%___-___-____%' AS integer) AS phone 
    -- What table contains the data? 
    FROM evanston311;

-- Inspect the contents of the new temp table
SELECT *
  FROM indicators;
```

- Join the indicators table to evanston311, selecting the proportion of reports including an email or phone grouped by priority.

- Include adjustments to account for issues arising from integer division.

```sql
-- To clear table if it already exists
DROP TABLE IF EXISTS indicators;

-- Create the temp table
CREATE TEMP TABLE indicators AS
  SELECT id, 
         CAST (description LIKE '%@%' AS integer) AS email,
         CAST (description LIKE '%___-___-____%' AS integer) AS phone 
    FROM evanston311;
  
-- Select the column you'll group by
SELECT priority, 
       -- Compute the proportion of rows with each indicator
       sum(email)/count(*)::numeric AS email_prop, 
       sum(phone)/count(*)::numeric AS phone_prop 
  -- Tables to select from
  FROM evanston311
       LEFT JOIN indicators
       -- Joining condition
       ON evanston311.id=indicators.id
 -- What are you grouping by?
 GROUP BY priority;
```

# Working with dates and timestamps

**Chapter description:**

What time is it? In this chapter, you'll learn how to find out. You'll aggregate date/time data by hour, day, month, or year and practice both constructing time series and finding gaps in them.

# Date/time types and formats

**Personal notes:**

*ISO 8601*

To address the ambiguity of possible date/time formats, PostgreSQL stores date/time information according to the ISO 8601 standard. ISO 8601 specifies a way to record date/time information. The units are listed in order from the largest to the smallest—similar to the way we write numbers. Years come first, followed by months, and then days. When time information is added, it starts with hours, then minutes, and seconds.

```plaintext
YYYY-MM-DD HH:MM:SS
```

Each component has a fixed number of digits, so smaller values should be filled with leading zeros.

*UTC and Timezones*

Timezones are another factor that can complicate date and time information. PostgreSQL stores timestamps with timezone information according to Coordinated Universal Time (UTC). Timezones are defined in terms of their offset from UTC. Timestamps in PostgreSQL can include timezone information or not. When timezones are included, they appear at the end with a plus or minus sign, followed by the number of hours the timezone is offset from UTC.

*Date and Time Comparisons*

Date/time entries can be compared just like numbers, using greater than, less than, and equal to signs. You can obtain the current timestamp using the `now()` function, which is useful when comparing values to the current date/time.

```sql
SELECT now() > '2017-12-31';
```

*Date Subtraction*

In addition to comparing dates, you can also subtract them from each other. The result returns an `INTERVAL` type.

*Date Addition*

You can add time to existing dates. Adding an integer value to a date will add days. However, adding an integer to a timestamp will result in an error.

```sql
SELECT '2010-01-01'::date + 1;
```

Other time quantities, from years to seconds, can be added with `INTERVAL`. You specify an `INTERVAL` with a combination of numbers and words in single quotes, and then cast it as an `INTERVAL`.

```sql
SELECT '2018-12-10' :: date + 1 'year'::INTERVAL;
```

Alternatively, you can specify the `INTERVAL` in terms of various units, such as 1 year, 2 days, and 3 minutes.

```sql
SELECT '2018-12-10' :: date + '1 year 2 days 3 minutes'::INTERVAL;
```

**Exercises:**

**ISO 8601**

Which date format below conforms to the ISO 8601 standard?

    "2018-06-15 15:30:00"

**Date comparisons**

When working with timestamps, sometimes you want to find all observations on a given day. However, if you specify only a date in a comparison, you may get unexpected results. This query:
```sql
SELECT count(*) 
  FROM evanston311
 WHERE date_created = '2018-01-02';
returns 0, even though there were 49 requests on January 2, 2018.
```
This is because dates are automatically converted to timestamps when compared to a timestamp. The time fields are all set to zero:
```sql
SELECT '2018-01-02'::timestamp;
 2018-01-02 00:00:00
```
When working with both timestamps and dates, you'll need to keep this in mind.

**Instructions:**

- Count the number of Evanston 311 requests created on January 31, 2017 by casting date_created to a date.

```sql
-- Count requests created on January 31, 2017
SELECT count(*) 
  FROM evanston311
 WHERE date_created::date = '2017-01-31';
```

- Count the number of Evanston 311 requests created on February 29, 2016 by using >= and < operators.

```sql
-- Count requests created on February 29, 2016
SELECT count(*)
  FROM evanston311 
 WHERE date_created >= '2016-02-29' 
   AND date_created < '2016-03-01' ;
```

- Count the number of requests created on March 13, 2017.
Specify the upper bound by adding 1 to the lower bound.

```sql
-- Count requests created on March 13, 2017
SELECT count(*)
  FROM evanston311
 WHERE date_created >= '2017-03-13'
   AND date_created < '2017-03-13'::date + 1;
```

**Date arithmetic**

You can subtract dates or timestamps from each other.

You can add time to dates or timestamps using intervals. An interval is specified with a number of units and the name of a datetime field. For example:
```sql
'3 days'::interval
'6 months'::interval
'1 month 2 years'::interval
'1 hour 30 minutes'::interval
```
Practice date arithmetic with the Evanston 311 data and now().

**Instructions:**

- Subtract the minimum date_created from the maximum date_created.

```sql
-- Subtract the min date_created from the max
SELECT MAX(date_created) - MIN(date_created) 
  FROM evanston311;
```

- Using now(), find out how old the most recent evanston311 request was created.

```sql
-- How old is the most recent request?
SELECT now() - MAX(date_created)
  FROM evanston311;
```

- Add 100 days to the current timestamp.

```sql
-- Add 100 days to the current timestamp
SELECT now() + '100 days'::INTERVAL;
```

- Select the current timestamp and the current timestamp plus 5 minutes.

```sql
-- Select the current timestamp, 
-- and the current timestamp + 5 minutes
SELECT now(), now()+'5 minutes'::INTERVAL;
```

**Completion time by category**

The evanston311 data includes a date_created timestamp from when each request was created and a date_completed timestamp for when it was completed. The difference between these tells us how long a request was open.

Which category of Evanston 311 requests takes the longest to complete?

**Instructions:**

- Compute the average difference between the completion timestamp and the creation timestamp by category.

- Order the results with the largest average time to complete the request first.

```sql
-- Select the category and the average completion time by category
-- Select the category and the average completion time by category
SELECT category, 
       avg(date_completed-date_created) AS completion_time
  FROM evanston311
  group by category
 -- Order the results
 ORDER BY completion_time desc;
```

# Date/time components and aggregation

**Personal notes:**

*Common Date/Time Fields*

There are functions to extract individual components from date/time data, known as fields. First, you can obtain the century or decade to which a timestamp belongs. Definitions of date/time fields can be complicated and sometimes counterintuitive. You can also get the year, month, and day fields that make up a date. Similarly, you can obtain the hour, minute, and second fields, as seen earlier. 'week' is the week number in the year, based on the ISO 8601 definition. 'dow' is the day of the week—starting from Sunday, which has a value of 0, and ending on Saturday with a value of 6.

*Extracting Fields*

To extract these fields from a date or timestamp, you can use the functions `date_part` or `EXTRACT`. These functions expect a timestamp but automatically convert dates to timestamps. While these two functions return the same results, they have different syntax. `date_part` uses a comma to separate arguments, while `EXTRACT` uses the keyword `FROM`. The field name must be enclosed in single quotes when using the `date_part` function. With the `EXTRACT` function, the field name can be without quotes.

```sql
-- Using date_part
SELECT date_part('field', timestamp);

-- Using EXTRACT
SELECT EXTRACT(FIELD FROM timestamp);
```

The `EXTRACT` function often calls the `date_part` function, and the output results of both are labeled as `date_part`. The following examples show how to extract the month from the current timestamp:

```sql
SELECT date_part('month', now());

SELECT EXTRACT(MONTH FROM now());
```

Extracting fields is useful when analyzing how data varies over a larger unit of time. For instance, how do sales vary per month over the years? Using sales data from 2010 to 2016, are January sales generally higher than those in March?

*Truncating Fields*

Instead of extracting individual fields, you can also truncate dates and timestamps to a specified precision level. Dates and timestamps are ordered from left to right, from larger to smaller units. You can use the `date_trunc` function to specify how much of a date/time timestamp should be retained, similar to working with a numeric value. The types of fields that can be used with this function include all those mentioned earlier in the lesson, except for the day of the week. The `date_trunc` function replaces fields smaller or less significant than the specified field with zero or one, as appropriate. Months and days are set to 1, while hour fields are set to 0.

```sql
-- Using date_trunc
SELECT date_trunc('field', timestamp);

-- Example: Truncating to the month
SELECT date_trunc('month', now());
```

Truncating dates is useful when you want to count, average, or sum data associated with timestamps or dates over larger units of time.

**Exercises:**

**Date parts**

The date_part() function is useful when you want to aggregate data by a unit of time across multiple larger units of time. For example, aggregating data by month across different years, or aggregating by hour across different days.

Recall that you use date_part() as:
```sql
SELECT date_part('field', timestamp);
```
In this exercise, you'll use date_part() to gain insights about when Evanston 311 requests are submitted and completed.

**Instructions:**

- How many requests are created in each of the 12 months during 2016-2017?

```sql
-- Extract the month from date_created and count requests
SELECT date_part('month', date_created)AS month, 
       COUNT(*)
  FROM evanston311
 -- Limit the date range
 WHERE date_created >= '2016-01-01'
   AND date_created < '2018-01-01'
 -- Group by what to get monthly counts?
 GROUP BY month;
```

- What is the most common hour of the day for requests to be created?

```sql
-- Get the hour and count requests
SELECT date_part('hour', date_created) AS hour,
       count(*)
  FROM evanston311
 GROUP BY hour
 -- Order results to select most common
 ORDER BY COUNT DESC
 LIMIT 1;
```

- During what hours are requests usually completed? Count requests completed by hour.
Order the results by hour.

```sql
-- Count requests completed by hour
SELECT date_part('hour', date_completed) AS hour,
       COUNT(*)
  FROM evanston311
  group by hour
 order by count;
```

**Variation by day of week**

Does the time required to complete a request vary by the day of the week on which the request was created?

We can get the name of the day of the week by converting a timestamp to character data:
```sql
to_char(date_created, 'day') 
```
But character names for the days of the week sort in alphabetical, not chronological, order. To get the chronological order of days of the week with an integer value for each day, we can use:
```sql
EXTRACT(DOW FROM date_created)
```
DOW stands for "day of week."

**Instructions:**

- Select the name of the day of the week the request was created (date_created) as day.

- Select the mean time between the request completion (date_completed) and request creation as duration.

- Group by day (the name of the day of the week) and the integer value for the day of the week (use a function).

- Order by the integer value of the day of the week using the same function used in GROUP BY.

```sql
-- Select name of the day of the week the request was created 
SELECT to_char(date_created, 'day') AS day, 
       -- Select avg time between request creation and completion
       avg(date_completed -date_created) AS duration
  FROM evanston311 
 -- Group by the name of the day of the week (use the alias) and 
 -- integer value of day of week 
 GROUP BY day, EXTRACT(dow from date_created)
 -- Order by integer value of the day of the week
 ORDER BY EXTRACT(dow from date_created);
```

**Date truncation**

Unlike date_part() or EXTRACT(), date_trunc() keeps date/time units larger than the field you specify as part of the date. So instead of just extracting one component of a timestamp, date_trunc() returns the specified unit and all larger ones as well.

Recall the syntax:
```sql
date_trunc('field', timestamp)
```
Using date_trunc(), find the average number of Evanston 311 requests created per day for each month of the data. Ignore days with no requests when taking the average.

**Instructions:**

- Write a subquery to count the number of requests created per day.

- Select the month and average count per month from the daily_count subquery.

```sql
 -- Aggregate daily counts by month
SELECT date_trunc('month',day) AS month,
       avg(count)
  -- Subquery to compute daily counts
  FROM (SELECT date_trunc('day',date_created) AS day,
               count(*) AS count
          FROM evanston311
         GROUP BY day) AS daily_count
 GROUP BY month
 ORDER BY month;
```

# Aggregating with date/time series

**Personal notes:**

*Generate Series*

Recall the `generate_series` function, which we used with numerical data. We can use it with date/time data as well. The function expects timestamps for the `FROM` and `TO` arguments, and dates are automatically converted to timestamps. The last argument is an `INTERVAL`.

```sql
SELECT generate_series(FROM, TO, INTERVAL);
```

For example, if we want a range of two days, the result will be a series of timestamps between the specified start and end values, separated by the specified interval.

```sql
SELECT generate_series('2018-01-01',
                       '2018-01-15',
                       '2 days'::INTERVAL);
```

*Generate Series from the Beginning*

To obtain consistent values, generate series using the beginning of a month or year, not the end. To correctly generate a series for the last day of each month, generate a series using the beginning of each month, and then subtract 1 day from the result.

```sql
SELECT generate_series('2018-02-01',
                       '2019-01-01',
                       '1 month'::INTERVAL) - '1 day'::INTERVAL;
```

*Normal Aggregation*

Time series can also be used to find time units without observations. For example, you might want to count sales by the hour they occurred.

```sql
SELECT date_trunc('hour', date) AS hour, COUNT(*)
FROM sales
GROUP BY hour
ORDER BY hour;
```

Looking at the result, it's challenging to tell at first glance that there were no sales at 11 AM.

*Aggregation with Series*

To include hours without sales, generate a series of hours and then join it with the original data to introduce rows for missing hours. First, use a `WITH` clause to create the series of hours from 9 AM to 2 PM, and name it `hour_series`.

```sql
WITH hour_series AS (
    SELECT generate_series('2018-04-23 09:00:00', 
                           '2018-04-23 14:00:00',
                           '1 hour'::INTERVAL) AS hours
)
```

Next, join this with the sales data, matching the hour from the series to the sales date truncated to the hour. Count the date column instead of counting rows because we don't want to count null values. Group and order by hours to get the sales count per hour.

```sql
SELECT hours, COUNT(date)
FROM hour_series
LEFT JOIN sales
ON hours=date_trunc('hour', date)
GROUP BY hours
ORDER BY hours;
```

The result now includes all hours between 9 AM and 2 PM, with zeros for hours without sales. It's less likely that we will overlook hours with no sales.

*Aggregation with Bins*

If you want to aggregate data by an interval that is not equal to a unit of a date/time field, you can create bins. Let's count sales in 3-hour intervals during the day. First, create two series, one for the lower bound of each bin and another for the upper bound. The series for the upper bound starts and ends 3 hours after the lower limit.

```sql
WITH BINS AS (
    SELECT generate_series('2018-04-23 09:00:00', 
                           '2018-04-23 15:00:00',
                           '3 hour'::INTERVAL) AS lower,
           generate_series('2018-04-23 12:00:00', 
                           '2018-04-23 18:00:00',
                           '3 hour'::INTERVAL) AS upper
)
```

Then, join the bins with the sales data, where the sales date is greater than or equal to the lower bin and less than the upper bin. Group and order by bin limits.

```sql
SELECT lower, upper, COUNT(date)
FROM BINS
LEFT JOIN sales
ON date >= lower AND date < upper
GROUP BY lower, upper
ORDER BY lower;
```
The result is the count of sales made during each of the 3-hour intervals.

**Exercises:**

**Find missing dates**

The generate_series() function can be useful for identifying missing dates.

Recall:
```sql
generate_series(from, to, interval)
```
where from and to are dates or timestamps, and interval can be specified as a string with a number and a unit of time, such as '1 month'.

Are there any days in the Evanston 311 data where no requests were created?

**Instructions:**

- Write a subquery using generate_series() to get all dates between the min() and max() date_created in evanston311.

- Write another subquery to select all values of date_created as dates from evanston311.

- Both subqueries should produce values of type date (look for the ::).

- Select dates (day) from the first subquery that are NOT IN the results of the second subquery. This gives you days that are not in date_created.

```sql
 SELECT day
-- Subquery to generate all dates
-- from min to max date_created
  FROM (SELECT generate_series(min(date_created),
                               max(date_created),
                               '1 day')::date AS day
          -- What table is date_created in?
          FROM evanston311) AS all_dates
-- Select dates (day from above) that are NOT IN the subquery
 WHERE day not in  
       -- Subquery to select all date_created values as dates
       (SELECT date_created::date
          FROM evanston311);
```

**Custom aggregation periods**

Find the median number of Evanston 311 requests per day in each six month period from 2016-01-01 to 2018-06-30. Build the query following the three steps below.

Recall that to aggregate data by non-standard date/time intervals, such as six months, you can use generate_series() to create bins with lower and upper bounds of time, and then summarize observations that fall in each bin.

Remember: you can access the slides with an example of this type of query using the PDF icon link in the upper right corner of the screen.

**Instructions:**

- Use generate_series() to create bins of 6 month intervals. Recall that the upper bin values are exclusive, so the values need to be one day greater than the last day to be included in the bin.

- Notice how in the sample code, the first bin value of the upper bound is July 1st, and not June 30th.

- Use the same approach when creating the last bin values of the lower and upper bounds (i.e. for 2018).

```sql
-- Generate 6 month bins covering 2016-01-01 to 2018-06-30
-- Create lower bounds of bins
SELECT generate_series('2016-01-01',  -- First bin lower value
                       '2018-01-01',  -- Last bin lower value
                       '6 months'::interval) AS lower,
-- Create upper bounds of bins
       generate_series('2016-07-01',  -- First bin upper value
                       '2018-07-01',  -- Last bin upper value
                       '6 months'::interval) AS upper;
```

- Count the number of requests created per day. Remember to not count *, or you will risk counting NULL values.

- Include days with no requests by joining evanston311 to a daily series from 2016-01-01 to 2018-06-30.

```sql
-- Count number of requests made per day
SELECT day, count(date_created) AS count
-- Use a daily series from 2016-01-01 to 2018-06-30 
-- to include days with no requests
  FROM (SELECT generate_series('2016-01-01',  -- series start date
                               '2018-06-30',  -- series end date
                               '1 day'::interval)::date AS day) AS daily_series
       LEFT JOIN evanston311
       -- match day from above (which is a date) to date_created
       ON day = date_created::date
 GROUP BY day;
```
- Assign each daily count to a single 6 month bin by joining bins to daily_counts.

- Compute the median value per bin using percentile_disc().

```sql
-- Bins from Step 1
WITH bins AS (
	 SELECT generate_series('2016-01-01',
                            '2018-01-01',
                            '6 months'::interval) AS lower,
            generate_series('2016-07-01',
                            '2018-07-01',
                            '6 months'::interval) AS upper),
-- Daily counts from Step 2
     daily_counts AS (
     SELECT day, count(date_created) AS count
       FROM (SELECT generate_series('2016-01-01',
                                    '2018-06-30',
                                    '1 day'::interval)::date AS day) AS daily_series
            LEFT JOIN evanston311
            ON day = date_created::date
      GROUP BY day)
-- Select bin bounds and median of count
SELECT lower, 
       upper, 
       percentile_disc(0.5) WITHIN GROUP (ORDER BY count) AS median
-- Join bins and daily_counts
  FROM bins
       LEFT JOIN daily_counts
-- Where the day is between the bin bounds
       ON day >= lower
          AND day < upper
-- Group by bin bounds
 GROUP BY lower, upper
 ORDER BY lower;
```

**Monthly average with missing dates**

Find the average number of Evanston 311 requests created per day for each month of the data.

This time, do not ignore dates with no requests.

**Instructions:**

- Generate a series of dates from 2016-01-01 to 2018-06-30.

- Join the series to a subquery to count the number of requests created per day.

- Use date_trunc() to get months from date, which has all dates, NOT day.

- Use coalesce() to replace NULL count values with 0. Compute the average of this value.

```sql
--generate series with all days from 2016-01-01 to 2018-06-30
WITH all_days AS 
     (SELECT generate_series('2016-01-01',
                             '2018-06-30',
                             '1 day'::interval) AS date),
     -- Subquery to compute daily counts
     daily_count AS 
     (SELECT date_trunc('day', date_created) AS day,
             count(*) AS count
        FROM evanston311
       GROUP BY day)
-- Aggregate daily counts by month using date_trunc
SELECT date_trunc('month',date) AS month,
       -- Use coalesce to replace NULL count values with 0
       avg(coalesce(count, 0)) AS average
  FROM all_days
       LEFT JOIN daily_count
       -- Joining condition
       ON all_days.date=daily_count.day
 GROUP BY month
 ORDER BY month; 
```

# Time between events

**Personal notes:**

*Lead and Lag Functions*

The `lead` and `lag` functions allow us to shift the values in an ordered column by 1 row by default. We can then subtract the original values from the lead or lag values to obtain the difference between events. For these functions to work, you must specify how the rows should be ordered. Remember that rows in a database table do not have inherent order; they are ordered only when you explicitly specify an `ORDER BY`. These are window functions. You start with the function name and provide the column to which you want to apply lead or lag as an argument. You then add an `OVER` clause and an `ORDER BY` statement specifying how the rows should be ordered.

```sql
SELECT date,
       lag(date) OVER (ORDER BY date),
       lead(date) OVER (ORDER BY date)
FROM sales;
```

The `lag` function pushes all values down by one row. NULL is inserted at the beginning of the lag column, so the first sales time is now the second value in the lag column. The last sales time is discarded. The `lead` function does the opposite, pulling all values up by one row. The second sales time becomes the first value, and NULL is added to the end of the main column. The first sales time is discarded.

*Time Between Events*

If we order the dates from oldest to newest, we want to subtract the lagged date from the current date to calculate the difference between each sale and the previous sale.

```sql
SELECT date,
       date - lag(date) OVER (ORDER BY date) AS gap
FROM sales;
```

*Average Time Between Events*

To calculate the average interval, we need to use a subquery. We can't simply wrap the `AVG` function around the difference between sales because window functions cannot be used inside aggregation functions like `AVG`.

```sql
SELECT AVG(gap)
FROM (
    SELECT date - lag(date) OVER (ORDER BY date) AS gap
    FROM sales
) AS gaps;
```

*Change in a Time Series*

A time series is any variable that has a date or time associated with each value. In this example, we want to see how the quantity sold changes from one sale to the next. We can't calculate a change for the first value in a time series because there is no previous value.

```sql
SELECT date,
       amount,
       lag(amount) OVER (ORDER BY date),
       amount - lag(amount) OVER (ORDER BY date) AS change
FROM sales;
```

**Exercises:**

**Longest gap**

What is the longest time between Evanston 311 requests being submitted?

Recall the syntax for lead() and lag():
```sql
lag(column_to_adjust) OVER (ORDER BY ordering_column)
lead(column_to_adjust) OVER (ORDER BY ordering_column)
```

**Instructions:**

- Select date_created and the date_created of the previous request using lead() or lag() as appropriate.

- Compute the gap between each request and the previous request.

- Select the row with the maximum gap.

```sql
-- Compute the gaps
WITH request_gaps AS (
        SELECT date_created,
               -- lead or lag
               lag(date_created) OVER (order by date_created) AS previous,
               -- compute gap as date_created minus lead or lag
               date_created - lag(date_created) OVER (order by date_created) AS gap
          FROM evanston311)
-- Select the row with the maximum gap
SELECT *
  FROM request_gaps
-- Subquery to select maximum gap from request_gaps
 WHERE gap = (SELECT max(gap)
                FROM request_gaps);
```

**Rats!**

Requests in category "Rodents- Rats" average over 64 days to resolve. Why?

Investigate in 4 steps:

Why is the average so high? Check the distribution of completion times. Hint: date_trunc() can be used on intervals.

See how excluding outliers influences average completion times.

Do requests made in busy months take longer to complete? Check the correlation between the average completion time and requests per month.

Compare the number of requests created per month to the number completed.

Remember: the time to resolve, or completion time, is date_completed - date_created.

**Instructions:**

- Use date_trunc() to examine the distribution of rat request completion times by number of days.

```sql
-- Truncate the time to complete requests to the day
SELECT date_trunc('day',date_completed-date_created) AS completion_time,
-- Count requests with each truncated time
       count(*)
  FROM evanston311
-- Where category is rats
 WHERE category = 'Rodents- Rats'
-- Group and order by the variable of interest
 GROUP BY completion_time
 ORDER BY completion_time;
```

- Compute average completion time per category excluding the longest 5% of requests (outliers).

```sql
SELECT category, 
       -- Compute average completion time per category
       avg(date_completed-date_created) AS avg_completion_time
  FROM evanston311
-- Where completion time is less than the 95th percentile value
 WHERE (date_completed-date_created) < 
-- Compute the 95th percentile of completion time in a subquery
         (SELECT percentile_disc(0.95) WITHIN GROUP (order by date_completed-date_created)
            FROM evanston311)
 GROUP BY category
-- Order the results
 ORDER BY avg_completion_time DESC;
```

- Get corr() between avg. completion time and monthly requests. EXTRACT(epoch FROM interval) returns seconds in interval.

```sql
-- Compute correlation (corr) between 
-- avg_completion time and count from the subquery
SELECT corr(avg_completion, count)
  -- Convert date_created to its month with date_trunc
  FROM (SELECT date_trunc('month', date_created) AS month, 
               -- Compute average completion time in number of seconds           
               avg(EXTRACT(epoch FROM date_completed - date_created)) AS avg_completion, 
               -- Count requests per month
               count(*) AS count
          FROM evanston311
         -- Limit to rodents
         WHERE category='Rodents- Rats' 
         -- Group by month, created above
         GROUP BY month) 
         -- Required alias for subquery 
         AS monthly_avgs;
```

- Select the number of requests created and number of requests completed per month.

```sql
-- Compute monthly counts of requests created
WITH created AS (
       SELECT date_trunc('month',date_created) AS month,
              count(*) AS created_count
         FROM evanston311
        WHERE category='Rodents- Rats'
        GROUP BY month),
-- Compute monthly counts of requests completed
      completed AS (
       SELECT date_trunc('month',date_completed) AS month,
              count(*) AS completed_count
         FROM evanston311
        WHERE category='Rodents- Rats'
        GROUP BY month)
-- Join monthly created and completed counts
SELECT created.month, 
       created_count, 
       completed_count
  FROM created
       INNER JOIN completed
       ON created.month=completed.month
 ORDER BY created.month;
```

# Data-Driven Decision Making in SQL

**Course Description**

In this course, you will learn how to use SQL to support decision making. It is based on a case study about an online movie rental company with a database about customer information, movie ratings, background information on actors and more. You will learn to apply SQL queries to study for example customer preferences, customer engagement, and sales development. This course also covers SQL extensions for online analytical processing (OLAP), which makes it easier to obtain key insights from multidimensional aggregated data.

# Introduction to business intelligence for a online movie rental database

**Chapter description:**

The first chapter is an introduction to the use case of an online movie rental company, called MovieNow and focuses on using simple SQL queries to extract and aggregated data from its database.

# Introduction to data driven decision making

**Personal notes:**

Throughout this course, we will be using a PostgreSQL database from a fictional movie streaming platform called MovieNow. MovieNow offers an online streaming service for movies.

*Objectives of Data-Driven Decision Making*

The primary goal of data-driven decision-making is to achieve both short-term and long-term objectives. Valuable insights can be extracted from data to support short-term operational decisions. For instance, understanding the popularity of certain actors helps MovieNow decide whether to acquire specific movies for the platform. Additionally, last month's revenue might be crucial information for short-term investment decisions.

For long-term decisions, data-driven support can provide insights into customer growth and success in specific regions in the past. This information can inform the company's decisions about when and where to expand its market in the future. Moreover, understanding the long-term development of overall revenue helps MovieNow plan for long-term investments.

*KPIs: Key Performance Indicators*

Key Performance Indicators (KPIs) assist a company (or its subdivisions) in defining and monitoring success. Revenue is a straightforward indicator of success. For the MovieNow database, this is calculated as the sum of the prices of rented movies. For customer relationship management within the subdivision, KPIs such as 'customer satisfaction' could be quantified by the average rating of all movies, or 'customer engagement' as the number of active customers in a specific period.

**Exercises:**

**Exploring the database**

Explore the tables and its columns. Which of the following quantities can't be computed?

        "The number of movies with an international award."

**Exploring the table renting**

The table renting includes all records of movie rentals. Each record has a unique ID renting_id. It also contains information about customers (customer_id) and which movies they watched (movie_id). Furthermore, customers can give a rating after watching the movie, and the day the movie was rented is recorded.

**Instructions:**

- Select all columns from renting.

```sql
SELECT *  -- Select all
FROM renting;        -- From table renting
```

- Now select only those columns from renting which are needed to calculate the average rating per movie.

```sql
SELECT rating, movie_id  -- Select all columns needed to compute the average rating per movie
FROM renting;
```

- Question: In SQL missing values are coded with null. In which column of renting did you notice null values?

        "rating"

# Filtering and ordering

**Personal notes:**

*Filtering and Ordering in SQL*

A crucial aspect of querying data involves filtering records that are relevant to a specific research question. Additionally, arranging tables in a particular order is essential for future applications.

*WHERE Clause*

The `WHERE` clause in SQL is used to filter records based on a specified condition. It allows you to extract only those records that fulfill a particular criterion. A basic structure of the `WHERE` clause looks like this:

```sql
SELECT column1, column2, ...
FROM table
WHERE condition;
```

For example, to retrieve all movies with a rating higher than 8, you might use:

```sql
SELECT *
FROM movies
WHERE rating > 8;
```

This would return all rows from the "movies" table where the rating is greater than 8.

*ORDER BY Clause*

The `ORDER BY` clause in SQL is used to sort the result set based on one or more columns. It allows you to specify the order in which the rows should appear. The basic syntax is:

```sql
SELECT column1, column2, ...
FROM table
ORDER BY column1 [ASC | DESC], column2 [ASC | DESC], ...;
```

For example, to retrieve all movies sorted by release year in descending order, you might use:

```sql
SELECT *
FROM movies
ORDER BY release_year DESC;
```

This would return all rows from the "movies" table, sorted by the "release_year" column in descending order.

Combining `WHERE` and `ORDER BY` allows you to filter and sort your data simultaneously. For instance, if you want to retrieve movies released after 2000 and order them by rating in descending order:

```sql
SELECT *
FROM movies
WHERE release_year > 2000
ORDER BY rating DESC;
```

This would return movies released after 2000, sorted by rating in descending order.

**Exercises:**

**Working with dates**

For the analysis of monthly or annual changes, it is important to select data from specific time periods. You will select records from the table renting of movie rentals. The format of dates is 'YYYY-MM-DD'.

**Instructions:**

- Select all movies rented on October 9th, 2018.

```sql
SELECT *
FROM renting
WHERE date_renting = '2018-10-09'; -- Movies rented on October 9th, 2018
```

- Select all records of movie rentals between beginning of April 2018 till end of August 2018.

```sql
SELECT *
FROM renting
WHERE date_renting BETWEEN '2018-04-01' AND '2018-08-31' ; -- from beginning April 2018 to end August 2018
```

- Put the most recent records of movie rentals on top of the resulting table and order them in decreasing order.

```sql
SELECT *
FROM renting
WHERE date_renting BETWEEN '2018-04-01' AND '2018-08-31'
ORDER BY renting DESC; -- Order by recency in decreasing order
```

**Selecting movies**

The table movies contains all movies available on the online platform.

**Instructions:**

- Select all movies which are not dramas.

```sql
SELECT *
FROM movies
WHERE genre <> 'Drama'; -- All genres except drama
```

- Select the movies 'Showtime', 'Love Actually' and 'The Fighter'.

```sql
SELECT *
FROM movies
WHERE title IN ('Showtime', 'Love Actually', 'The Fighter'); -- Select all movies with the given titles
```

- Order the movies by increasing renting price.

```sql
SELECT *
FROM movies
ORDER BY renting_price DESC ; -- Order the movies by increasing renting price
```

**Select from renting**

Only some users give a rating after watching a movie. Sometimes it is interesting to explore only those movie rentals where a rating was provided.

**Instructions:**

- Select from table renting all movie rentals from 2018.

- Filter only those records which have a movie rating.

```sql
SELECT *
FROM renting
WHERE date_renting BETWEEN '2018-01-01' AND '2018-12-31' -- Renting in 2018
AND rating IS NOT NULL; -- Rating exists
```

# Aggregations - summarizing data

**Personal notes:**

In decision-making, it is often crucial to focus on summaries of specific groups rather than individual records. SQL provides powerful aggregation functions to help in summarizing and analyzing data.

*Overview of Aggregation*

Aggregation functions in SQL are used to perform calculations on a set of values to return a single value. Common aggregation functions include:

- *COUNT*: Counts the number of rows.
- *SUM*: Calculates the sum of numeric values.
- *AVG*: Computes the average of numeric values.
- *MIN*: Finds the minimum value in a set.
- *MAX*: Finds the maximum value in a set.

Here's a basic structure of an aggregation query:

```sql
SELECT AGGREGATE_FUNCTION(column) AS alias
FROM table
WHERE condition
GROUP BY column;
```

For example, to find the average rating for each genre in the "movies" table:

```sql
SELECT genre, AVG(rating) AS avg_rating
FROM movies
GROUP BY genre;
```

This would return the average rating for each unique genre.

*Aggregation with NULL Values*

Dealing with NULL values is a common challenge in data analysis. To identify NULL values in a specific column, you can use the `COUNT` function along with `DISTINCT` and compare it with the total number of rows in the table.

```sql
SELECT COUNT(*) AS total_rows, COUNT(DISTINCT column_with_nulls) AS non_null_rows
FROM your_table;
```

If `total_rows` and `non_null_rows` are different, it indicates the presence of NULL values in the specified column.

*DISTINCT and Aliases*

- **DISTINCT*: The `DISTINCT` keyword is used to return unique values in the result set. It eliminates duplicate values.

  ```sql
  SELECT DISTINCT column
  FROM table;
  ```

- **Aliases*: Aliases are used to give a column or a table a temporary name. They make the output more readable and can be helpful when using aggregate functions.

  ```sql
  SELECT AVG(column) AS average_value
  FROM table;
  ```

The `AS` keyword is optional when creating aliases.

By mastering these aggregation techniques, you can gain valuable insights from your data, making informed decisions based on summarized information.

**Exercises:**

**Summarizing customer information**

In most business decisions customers are analyzed in groups, such as customers per country or customers per age group.

**Instructions:**

- Count the number of customers born in the 80s.

```sql
SELECT COUNT(*) -- Count the total number of customers
FROM customers
WHERE date_of_birth BETWEEN '1980-01-01' AND '1989-12-31'; -- Select customers born between 1980-01-01 and 1989-12-31
```

- Count the number of customers from Germany.

```sql
SELECT count(*)   -- Count the total number of customers
FROM customers
WHERE country = 'Germany'; -- Select all customers from Germany
```

- Count the number of countries where MovieNow has customers.

```sql
SELECT count(DISTINCT country) -- Count the number of countries
FROM customers;
```

**Ratings of movie 25**

The movie ratings give us insight into the preferences of our customers. Report summary statistics, such as the minimum, maximum, average, and count, of ratings for the movie with ID 25.

**Instructions:**

- Select all movie rentals of the movie with movie_id 25 from the table renting.

- For those records, calculate the minimum, maximum and average rating and count the number of ratings 
for this movie.

```sql
SELECT MIN(rating) AS min_rating, -- Calculate the minimum rating and use alias min_rating
	   MAX(rating) AS max_rating, -- Calculate the maximum rating and use alias max_rating
	   AVG(rating)  AS avg_rating, -- Calculate the average rating and use alias avg_rating
	   COUNT(rating) number_ratings -- Count the number of ratings and use alias number_ratings
FROM renting
WHERE movie_id = '25'; -- Select all records of the movie with ID 25
```

**Examining annual rentals**

You are asked to provide a report about the development of the company. Specifically, your manager is interested in the total number of movie rentals, the total number of ratings and the average rating of all movies since the beginning of 2019.

**Instructions:**

- First, select all records of movie rentals since January 1st 2019.

```sql
SELECT *-- Select all records of movie rentals since January 1st 2019
FROM renting
WHERE date_renting BETWEEN '2019-01-01' AND now(); 
```

- Now, count the number of movie rentals and calculate the average rating since the beginning of 2019.

```sql
SELECT 
	COUNT(*), -- Count the total number of rented movies
	AVG(rating) -- Add the average rating
FROM renting
WHERE date_renting >= '2019-01-01';
```

- Use as alias column names number_renting and average_rating respectively.

```sql
SELECT 
	COUNT(*) AS number_renting, -- Give it the column name number_renting
	AVG(rating) as average_rating  -- Give it the column name average_rating
FROM renting
WHERE date_renting >= '2019-01-01';
```

- Finally, count how many ratings exist since 2019-01-01.

```sql
SELECT 
	COUNT(*) AS number_renting,
	AVG(rating) AS average_rating, 
    COUNT(rating) AS number_ratings -- Add the total number of ratings here.
FROM renting
WHERE date_renting >= '2019-01-01';
```

# Decision Making with simple SQL queries

**Chapter description:**

More complex queries with GROUP BY, LEFT JOIN and sub-queries are used to gain insight into customer preferences.

# Grouping movies

**Personal notes:**

The use of the `GROUP BY` clause allows us to apply aggregations to groups within a table, providing a way to analyze the success and potential of a business by looking at groups of customers or groups of products together.

*GROUP BY Applications*

When analyzing data, it's often beneficial to group information based on specific columns. For instance, let's say we have a `movies` table, and we want to find the average rating for each genre. We can achieve this using the `GROUP BY` clause:

```sql
SELECT genre, AVG(rating) AS avg_rating
FROM movies
GROUP BY genre;
```

In this example, the result will show each unique genre along with its corresponding average rating.

*GROUP BY with HAVING*

The `HAVING` clause is used in combination with `GROUP BY` to filter the results based on aggregated values. It allows you to specify conditions for groups rather than individual rows.

For example, if we want to find genres with an average rating greater than 4.0:

```sql
SELECT genre, AVG(rating) AS avg_rating
FROM movies
GROUP BY genre
HAVING AVG(rating) > 4.0;
```

This query retrieves genres with an average rating higher than 4.0.

*GROUP BY and Aggregation Functions*

You can use various aggregation functions along with `GROUP BY` to extract valuable insights from your data. Here are a few examples:

- **Count the number of movies in each genre:*

  ```sql
  SELECT genre, COUNT(*) AS movie_count
  FROM movies
  GROUP BY genre;
  ```

- **Find the maximum and minimum ratings for each genre:*

  ```sql
  SELECT genre, MAX(rating) AS max_rating, MIN(rating) AS min_rating
  FROM movies
  GROUP BY genre;
  ```

- **Calculate the total revenue for each genre:*

  Assuming there's a `revenue` column in the `movies` table.

  ```sql
  SELECT genre, SUM(revenue) AS total_revenue
  FROM movies
  GROUP BY genre;
  ```

Mastering the use of `GROUP BY` in SQL queries allows you to analyze data at a more granular level, providing insights into specific groups and facilitating data-driven decision-making.

**Exercises:**

**First account for each country.**

Conduct an analysis to see when the first customer accounts were created for each country.

**Instructions:**

- Create a table with a row for each country and columns for the country name and the date when the first customer account was created.

- Use the alias first_account for the column with the dates.

- Order by date in ascending order.

```sql
SELECT country, -- For each country report the earliest date when an account was created
	MIN(date_account_start) AS first_account
FROM customers
GROUP BY country
ORDER BY first_account;
```

**Average movie ratings**

For each movie the average rating, the number of ratings and the number of views has to be reported. Generate a table with meaningful column names.

**Instructions:**

- Group the data in the table renting by movie_id and report the ID and the average rating.

```sql
SELECT movie_id, 
       AVG(rating)   -- Calculate average rating per movie
FROM renting
GROUP BY movie_id;
```

- Add two columns for the number of ratings and the number of movie rentals to the results table.

- Use alias names avg_rating, number_rating and number_renting for the corresponding columns.

```sql
SELECT movie_id, 
       AVG(rating) AS avg_rating, -- Use as alias avg_rating
       COUNT(rating) AS number_rating, -- Add column for number of ratings with alias number_rating
       COUNT(*) AS number_renting -- Add column for number of movie rentals with alias number_renting
FROM renting
GROUP BY movie_id;
```

- Order the rows of the table by the average rating such that it is in decreasing order.

- Observe what happens to NULL values.

```sql
SELECT movie_id, 
       AVG(rating) AS avg_rating,
       COUNT(rating) AS number_ratings,
       COUNT(*) AS number_renting
FROM renting
GROUP BY movie_id
ORDER BY avg_rating DESC; -- Order by average rating in decreasing order
```

- Question: Which statement is true for the movie with average rating null?

        "The average is null because all of the ratings of the movie are null."

**Average rating per customer**

Similar to what you just did, you will now look at the average movie ratings, this time for customers. So you will obtain a table with the average rating given by each customer. Further, you will include the number of ratings and the number of movie rentals per customer. You will report these summary statistics only for customers with more than 7 movie rentals and order them in ascending order by the average rating.

**Instructions:**

- Group the data in the table renting by customer_id and report the customer_id, the average rating, the number of ratings and the number of movie rentals.

- Select only customers with more than 7 movie rentals.

- Order the resulting table by the average rating in ascending order.

```sql
SELECT customer_id, -- Report the customer_id
      AVG(rating),  -- Report the average rating per customer
      COUNT(rating),  -- Report the number of ratings per customer
      COUNT(*)  -- Report the number of movie rentals per customer
FROM renting
GROUP BY customer_id
HAVING COUNT(*) > 7 -- Select only customers with more than 7 movie rentals
ORDER BY AVG(rating); -- Order by the average rating in ascending order
```

# Joining movie ratings with customer data

**Personal notes:**

SQL queries often involve combining or joining data from multiple tables. One common type of join is the `LEFT JOIN`, which retains all rows from the left table and includes matching rows from the right table. If there's no match, the result will contain NULL values for columns from the right table.

*LEFT JOIN Example*

Let's say we have two tables: `movies` and `ratings`. The `movies` table contains information about movies, and the `ratings` table contains customer ratings for those movies.

```sql
-- Example LEFT JOIN
SELECT movies.movie_id, movies.title, ratings.rating, ratings.customer_id
FROM movies
LEFT JOIN ratings ON movies.movie_id = ratings.movie_id;
```

In this query:

- `movies` is the left table, and `ratings` is the right table.
- We're selecting the movie ID, title, rating, and customer ID.
- The `LEFT JOIN` is based on the condition `movies.movie_id = ratings.movie_id`.

The result will include all movies from the `movies` table, and for each movie, it will show the rating given by customers if available. If there's no rating for a movie, the corresponding columns from the `ratings` table will be NULL.

*Use Case: Analyzing Movie Ratings with Customer Data*

You might use a `LEFT JOIN` when you want to analyze movie ratings along with customer information, even if some movies haven't been rated. For example, you could find the average rating for each customer, including customers who haven't rated any movies:

```sql
SELECT customers.customer_id, AVG(ratings.rating) AS avg_rating
FROM customers
LEFT JOIN ratings ON customers.customer_id = ratings.customer_id
GROUP BY customers.customer_id;
```

In this query, the `LEFT JOIN` ensures that all customers are included in the result, and it calculates the average rating for each customer. If a customer hasn't rated any movies, their average rating will be NULL.

Understanding and mastering different types of joins is crucial for efficiently combining data from multiple tables and extracting meaningful insights from relational databases.

**Exercises:**

**Join renting and customers**

For many analyses it is necessary to add customer information to the data in the table renting.

**Instructions:**

- Augment the table renting with all columns from the table customers with a LEFT JOIN.

- Use as alias' for the tables r and c respectively.

```sql
SELECT * -- Join renting with customers
FROM renting AS r
LEFT JOIN customers AS c
ON c.customer_id = r.customer_id;
```

- Select only records from customers coming from Belgium.

```sql
SELECT *
FROM renting AS r
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
WHERE country = 'Belgium'; -- Select only records from customers coming from Belgium
```

- Average ratings of customers from Belgium.

```sql
SELECT AVG(rating) -- Average ratings of customers from Belgium
FROM renting AS r
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
WHERE c.country='Belgium';
```

**Aggregating revenue, rentals and active customers**

The management of MovieNow wants to report key performance indicators (KPIs) for the performance of the company in 2018. They are interested in measuring the financial successes as well as user engagement. Important KPIs are, therefore, the revenue coming from movie rentals, the number of movie rentals and the number of active customers.

**Instructions:**

- First, you need to join movies on renting to include the renting_price from the movies table for each renting record.

- Use as alias' for the tables m and r respectively.

```sql
SELECT *
FROM renting AS r
LEFT JOIN movies AS m -- Choose the correct join statment
ON r.movie_id = m.movie_id;
```

- Calculate the revenue coming from movie rentals, the number of movie rentals and the number of customers who rented a movie.

```sql
SELECT 
	SUM(m.renting_price), -- Get the revenue from movie rentals
	COUNT(*), -- Count the number of rentals
	COUNT(DISTINCT customer_id)  -- Count the number of customers
FROM renting AS r
LEFT JOIN movies AS m
ON r.movie_id = m.movie_id;
```

- Now, you can report these values for the year 2018. Calculate the revenue in 2018, the number of movie rentals and the number of active customers in 2018. An active customer is a customer who rented at least one movie in 2018.

```sql
SELECT 
	SUM(m.renting_price), 
	COUNT(*), 
	COUNT(DISTINCT r.customer_id)
FROM renting AS r
LEFT JOIN movies AS m
ON r.movie_id = m.movie_id
-- Only look at movie rentals in 2018
WHERE date_renting BETWEEN '2018-01-01' AND '2018-12-31';
```

**Movies and actors**

You are asked to give an overview of which actors play in which movie.

**Instructions:**

-Create a list of actor names and movie titles in which they act. Make sure that each combination of actor and movie appears only once.

- Use as an alias for the table actsin the two letters ai.

```sql
SELECT DISTINCT a.name, -- Create a list of movie titles and actor names
       m.title
FROM actsin AS ai
LEFT JOIN movies AS m
ON m.movie_id = ai.movie_id
LEFT JOIN actors AS a
ON a.actor_id = ai.actor_id;
```

# Money spent per customer with sub-queries

**Personal notes:**

In this lesson, we'll explore how to calculate the amount of money each customer spent on movie rentals at MovieNow using subqueries.

*Subqueries in SELECT*

Subqueries in the `SELECT` clause allow us to perform calculations or retrieve single values from another table and include those results in the main query. This is often used when you want to use the result of a subquery as a column in the main query.

Let's consider an example where we want to find the total amount of money each customer spent on movie rentals. We have two tables: `customers` and `rentals`. The `rentals` table contains information about movie rentals, including the rental cost.

```sql
-- Example of using a subquery in SELECT
SELECT
  customer_id,
  (SELECT SUM(rental_cost) FROM rentals WHERE rentals.customer_id = customers.customer_id) AS total_spent
FROM
  customers;
```

In this query:

- We're selecting the `customer_id` from the `customers` table.
- The subquery `(SELECT SUM(rental_cost) FROM rentals WHERE rentals.customer_id = customers.customer_id)` calculates the total rental cost for each customer by summing the `rental_cost` from the `rentals` table where the customer IDs match.
- The result is a list of customer IDs along with the corresponding total amount spent by each customer.

*Use Case: Money Spent per Customer*

You might use subqueries in the `SELECT` clause when you need to perform calculations or retrieve specific values from related tables and include those results as columns in the main query. Calculating the total amount spent per customer is just one example of how subqueries in `SELECT` can be beneficial.

Understanding how to use subqueries effectively is essential for performing complex analyses and generating insightful reports from relational databases.

**Exercises:**

**Income from movies**

How much income did each movie generate? To answer this question subsequent SELECT statements can be used.

**Instructions:**

- Use a join to get the movie title and price for each movie rental.

```sql
SELECT m.title, -- Use a join to get the movie title and price for each movie rental
       m.renting_price
FROM renting AS r
LEFT JOIN movies AS m
ON r.movie_id = m.movie_id;
```

- Report the total income for each movie.

- Order the result by decreasing income.

```sql
SELECT rm.title, -- Report the income from movie rentals for each movie 
       SUM(rm.renting_price) AS income_movie
FROM
       (SELECT m.title, 
               m.renting_price
       FROM renting AS r
       LEFT JOIN movies AS m
       ON r.movie_id=m.movie_id) AS rm
GROUP BY rm.title
ORDER BY income_movie DESC; -- Order the result by decreasing income
```

- Question: Which statement about the movie 'Django Unchained' is NOT correct?

        "The income from 'Django Unchained' is higher than from 'Simone'."

**Age of actors from the USA**

Now you will explore the age of American actors and actresses. Report the date of birth of the oldest and youngest US actor and actress.

**Instructions:**

- Create a subsequent SELECT statements in the FROM clause to get all information about actors from the USA.

- Give the subsequent SELECT statement the alias a.

- Report for actors from the USA the year of birth of the oldest and the year of birth of the youngest actor and actress.

```sql
SELECT a.gender, -- Report for male and female actors from the USA 
       MAX(a.year_of_birth), -- The year of birth of the oldest actor
       MIN(a.year_of_birth) -- The year of birth of the youngest actor
FROM
   (SELECT * -- Use a subsequen SELECT to get all information about actors from the USA
   FROM actors
   WHERE nationality = 'USA') AS a -- Give the table the name a
GROUP BY a.gender;
```

# Identify favorite actors of customer groups

**Personal notes:**

In this lesson, we'll combine different SQL statements for complex queries to explore who the favorite actors are for certain groups of customers. We'll use a combination of `LEFT JOIN`, `WHERE`, `GROUP BY`, `HAVING`, and `ORDER BY` statements to answer this question.

*Example Query*

Let's assume we have three tables: `customers`, `rentals`, and `movies`. We want to find out who the favorite actors are for customers who spent a certain amount or more on movie rentals. We'll use a combination of statements to achieve this.

```sql
-- Example of combining SQL statements for complex queries
SELECT
  customers.customer_id,
  customers.customer_name,
  actors.actor_name,
  COUNT(*) AS movies_rented
FROM
  customers
LEFT JOIN rentals ON customers.customer_id = rentals.customer_id
LEFT JOIN movies ON rentals.movie_id = movies.movie_id
LEFT JOIN movie_actors ON movies.movie_id = movie_actors.movie_id
LEFT JOIN actors ON movie_actors.actor_id = actors.actor_id
WHERE
  rentals.rental_cost >= 20
GROUP BY
  customers.customer_id, actors.actor_id
HAVING
  COUNT(*) >= 2
ORDER BY
  customers.customer_id, movies_rented DESC;
```

In this query:

- We're selecting the `customer_id`, `customer_name`, `actor_name`, and the count of movies rented (`movies_rented`).
- We use `LEFT JOIN` to combine information from multiple tables (`customers`, `rentals`, `movies`, `movie_actors`, and `actors`).
- The `WHERE` clause filters the results to include only rentals with a rental cost of $20 or more.
- The `GROUP BY` clause groups the results by customer and actor.
- The `HAVING` clause filters the groups to include only those with a count of rented movies (`movies_rented`) greater than or equal to 2.
- The `ORDER BY` clause orders the results by customer ID and the count of movies rented in descending order.

*Use Case: Identifying Favorite Actors of Customer Groups*

This type of query can help the MovieNow platform understand which actors are popular among customers who are willing to spend a significant amount on movie rentals. It provides insights into customer preferences and can influence content acquisition decisions for the streaming platform.

Combining various SQL statements allows for the creation of powerful queries that address complex questions and provide valuable insights for data-driven decision-making.

**Exercises:**

**Identify favorite movies for a group of customers**

Which is the favorite movie on MovieNow? Answer this question for a specific group of customers: for all customers born in the 70s.

**Instructions:**

- Augment the table renting with customer information and information about the movies.

- For each join use the first letter of the table name as alias.

```sql
SELECT *
FROM renting AS r
LEFT JOIN customers AS c   -- Add customer information
ON c.customer_id = r.customer_id
LEFT JOIN movies AS m   -- Add movie information
ON m.movie_id = r.movie_id;
```

- Select only those records of customers born in the 70s.

```sql
SELECT *
FROM renting AS r
LEFT JOIN customers AS c
ON c.customer_id = r.customer_id
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
WHERE date_of_birth BETWEEN '1970-01-01' AND '1979-12-31'; -- Select customers born in the 70s
```

- For each movie, report the number of times it was rented, as well as the average rating. Limit your results to customers born in the 1970s.

```sql
SELECT m.title, 
COUNT(*), -- Report number of views per movie
AVG(r.rating) -- Add the average rating for each movie
FROM renting AS r
LEFT JOIN customers AS c
ON c.customer_id = r.customer_id
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
WHERE c.date_of_birth BETWEEN '1970-01-01' AND '1979-12-31'
GROUP BY m.title;
```

- Remove those movies from the table with only one rental.

- Order the result table such that movies with highest rating come first.

```sql
SELECT m.title, 
COUNT(*),
AVG(r.rating)
FROM renting AS r
LEFT JOIN customers AS c
ON c.customer_id = r.customer_id
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
WHERE c.date_of_birth BETWEEN '1970-01-01' AND '1979-12-31'
GROUP BY m.title
HAVING COUNT(*) > 1 -- Remove movies with only one rental
ORDER BY AVG(r.rating); -- Order with highest rating first
```

**Identify favorite actors for Spain**

You're now going to explore actor popularity in Spain. Use as alias the first letter of the table, except for the table actsin use ai instead.

**Instructions:**

- Augment the table renting with information about customers and actors.

```sql
SELECT *
FROM renting as r 
LEFT JOIN customers AS c  -- Augment table renting with information about customers 
ON r.customer_id = c.customer_id
LEFT JOIN actsin AS ai  -- Augment the table renting with the table actsin
ON r.movie_id = ai.movie_id 
LEFT JOIN actors AS a  -- Augment table renting with information about actors
ON ai.actor_id = a.actor_id;
```

- Report the number of movie rentals and the average rating for each actor, separately for male and female customers.

- Report only actors with more than 5 movie rentals.

```sql
SELECT a.name,  c.gender,
       COUNT(*) AS number_views, 
       AVG(r.rating) AS avg_rating
FROM renting as r
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
LEFT JOIN actsin as ai
ON r.movie_id = ai.movie_id
LEFT JOIN actors as a
ON ai.actor_id = a.actor_id
GROUP BY a.name, c.gender -- For each actor, separately for male and female customers
HAVING AVG(r.rating) IS NOT NULL 
AND COUNT(*) > 5 -- Report only actors with more than 5 movie rentals
ORDER BY avg_rating DESC, number_views DESC;
```

- Now, report the favorite actors only for customers from Spain.

```sql
SELECT a.name,  c.gender,
       COUNT(*) AS number_views, 
       AVG(r.rating) AS avg_rating
FROM renting as r
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
LEFT JOIN actsin as ai
ON r.movie_id = ai.movie_id
LEFT JOIN actors as a
ON ai.actor_id = a.actor_id
WHERE country ='Spain' -- Select only customers from Spain
GROUP BY a.name, c.gender
HAVING AVG(r.rating) IS NOT NULL 
  AND COUNT(*) > 5 
ORDER BY avg_rating DESC, number_views DESC;
```

**KPIs per country**

In chapter 1 you were asked to provide a report about the development of the company. This time you have to prepare a similar report with KPIs for each country separately. Your manager is interested in the total number of movie rentals, the average rating of all movies and the total revenue for each country since the beginning of 2019.

**Instructions:**

- Augment the table renting with information about customers and movies.

- Use as alias the first latter of the table name.

- Select only records about rentals since beginning of 2019.

```sql
SELECT *
FROM renting AS r -- Augment the table renting with information about customers
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
LEFT JOIN movies AS m -- Augment the table renting with information about movies
ON r.movie_id = m.movie_id
WHERE date_renting >= '2019-01-01'; -- Select only records about rentals since the beginning of 2019
```

- Calculate the number of movie rentals.

- Calculate the average rating.

- Calculate the revenue from movie rentals.

- Report these KPIs for each country.

```sql
SELECT 
	c.country,                    -- For each country report
	COUNT(r.movie_id) AS number_renting, -- The number of movie rentals
	AVG(r.rating) AS average_rating, -- The average rating
	SUM(renting_price) AS revenue         -- The revenue from movie rentals
FROM renting AS r
LEFT JOIN customers AS c
ON c.customer_id = r.customer_id
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
WHERE date_renting >= '2019-01-01'
GROUP BY c.country;
```

# Data Driven Decision Making with advanced SQL queries

**Chapter description:**

The concept of nested queries and correlated nested queries is introduced and the functions EXISTS and UNION are used to categorize customers, movies, actors, and more.

# Nested query

**Personal notes:**

A nested query, also known as a subquery, is a query that appears within the `WHERE` or `HAVING` clause of another query. The entire `SELECT` block of the nested query is embedded within the outer query. This subquery is typically executed first by the query optimizer, and its result (which can be a single value or multiple values) is used by the outer query.

Here's a brief summary of nested queries:

*Types of Nested Queries:*

1. **Single-Value Subqueries:*
   - Returns a single value.
   - Commonly used with comparison operators (e.g., `=`) to compare a value with the result of the subquery.

   ```sql
   SELECT column_name
   FROM table_name
   WHERE column_name = (SELECT ...);
   ```

2. **Multiple-Value Subqueries:*
   - Returns multiple values.
   - Commonly used with the `IN` or `NOT IN` operators to filter results based on the result set of the subquery.

   ```sql
   SELECT column_name
   FROM table_name
   WHERE column_name IN (SELECT ...);
   ```

3. **Correlated Subqueries:*
   - A subquery that depends on the outer query.
   - The subquery references columns from the outer query, and its execution is dependent on each row processed by the outer query.

   ```sql
   SELECT column_name
   FROM table_name AS outer
   WHERE column_name = (SELECT ... FROM table_name AS inner WHERE inner.column = outer.column);
   ```

*Example:*

Consider an example where you want to find customers who have rented more movies than the average number of rentals:

```sql
-- Example of a nested query to find customers with more rentals than average
SELECT customer_id, customer_name
FROM customers
WHERE rentals > (SELECT AVG(rentals) FROM customers);
```

In this query, the nested subquery `(SELECT AVG(rentals) FROM customers)` calculates the average number of rentals across all customers, and the outer query then selects customers who have rented more movies than this average.

*Use Case:*

Nested queries are valuable when you need to perform a calculation or comparison based on the result of another query. They are versatile and can be used in various scenarios to filter, aggregate, or compare data within the context of a larger query.

**Exercises:**

**Often rented movies**

Your manager wants you to make a list of movies excluding those which are hardly ever watched. This list of movies will be used for advertising. List all movies with more than 5 views using a nested query which is a powerful tool to implement selection conditions.

**Instructions:**

- Select all movie IDs which have more than 5 views.

```sql
SELECT DISTINCT movie_id -- Select movie IDs with more than 5 views
FROM renting
GROUP BY movie_id
HAVING COUNT(*) > 5;
```

- Select all information about movies with more than 5 views.

```sql
SELECT *
FROM movies
WHERE movie_id IN -- Select movie IDs from the inner query
	(SELECT movie_id
	FROM renting
	GROUP BY movie_id
	HAVING COUNT(*) > 5);
```

**Frequent customers**

Report a list of customers who frequently rent movies on MovieNow.

**Instruction:**

- List all customer information for customers who rented more than 10 movies.

```sql
SELECT *
FROM customers
WHERE customer_id IN -- Select all customers with more than 10 movie rentals
	(SELECT customer_id
	FROM renting
	GROUP BY customer_id
	HAVING COUNT(*) > 10);
```

**Movies with rating above average**

For the advertising campaign your manager also needs a list of popular movies with high ratings. Report a list of movies with rating above average.

**Instructions:**

- Calculate the average over all ratings.

```sql
SELECT AVG(rating) -- Calculate the total average rating
FROM renting;
```

- Select movie IDs and calculate the average rating of movies with rating above average.

```sql
SELECT movie_id, -- Select movie IDs and calculate the average rating 
       AVG(rating)
FROM renting
GROUP BY movie_id
HAVING AVG(rating) > -- Of movies with rating above average
	(SELECT AVG(rating)
	FROM renting);
```

- The advertising team only wants a list of movie titles. Report the movie titles of all movies with average rating higher than the total average.

```sql
SELECT title -- Report the movie titles of all movies with average rating higher than the total average
FROM movies
WHERE movie_id IN
	(SELECT movie_id
	 FROM renting
     GROUP BY movie_id
     HAVING AVG(rating) > 
		(SELECT AVG(rating)
		 FROM renting));
```

# Correlated nested queries

**Personal notes:**

In correlated nested queries, the inner subquery refers to a column from a table declared in the outer query. This creates a dependency between the inner and outer queries. The nested query is evaluated once for each row processed by the outer query, and the result of the inner query depends on the specific row being processed.

*Example:*

Consider an example where you want to find customers who have rented more movies than the average number of rentals in their city:

```sql
-- Example of a correlated nested query to find customers with more rentals than city average
SELECT customer_id, customer_name, city
FROM customers AS outer
WHERE rentals > (SELECT AVG(rentals) FROM customers WHERE city = outer.city);
```

In this query:
- The outer query (`SELECT customer_id, customer_name, city FROM customers AS outer`) processes each row in the `customers` table.
- The correlated subquery `(SELECT AVG(rentals) FROM customers WHERE city = outer.city)` calculates the average number of rentals for customers in the same city as the current row in the outer query.

The result is a list of customers who have rented more movies than the average in their respective cities.

*Use Case:*

Correlated nested queries are useful when you need to perform comparisons or calculations based on values related to each row in the outer query. They are often used in scenarios where the result of the subquery depends on the specific characteristics or conditions of each row being processed in the outer query.

**Exercises:**

**Analyzing customer behavior**

A new advertising campaign is going to focus on customers who rented fewer than 5 movies. Use a correlated query to extract all customer information for the customers of interest.

**Instructions:**

- First, count number of movie rentals for customer with customer_id=45. Give the table renting the alias r.

```sql
-- Count movie rentals of customer 45
SELECT COUNT(*)
FROM renting AS r
WHERE r.customer_id = 45;
```

- Now select all columns from the customer table where the number of movie rentals is smaller than 5.

```sql
-- Select customers with less than 5 movie rentals
SELECT *
FROM customers AS c
WHERE 5 > 
	(SELECT count(*)
	FROM renting AS r
	WHERE r.customer_id = c.customer_id);
```

**Customers who gave low ratings**

Identify customers who were not satisfied with movies they watched on MovieNow. Report a list of customers with minimum rating smaller than 4.

**Instructions:**

- Calculate the minimum rating of customer with ID 7. 

```sql
-- Calculate the minimum rating of customer with ID 7
SELECT MIN(rating)
FROM renting AS r
WHERE r.customer_id = 7;
```

- Select all customers with a minimum rating smaller than 4. Use the first letter of the table as an alias.

```sql
SELECT *
FROM customers AS c
WHERE 4 > -- Select all customers with a minimum rating smaller than 4 
	(SELECT MIN(rating)
	FROM renting AS r
	WHERE r.customer_id = c.customer_id);
```

**Movies and ratings with correlated queries**

Report a list of movies that received the most attention on the movie platform, (i.e. report all movies with more than 5 ratings and all movies with an average rating higher than 8).

**Instructions:**

- Select all movies with more than 5 ratings. Use the first letter of the table as an alias.

```sql
SELECT *
FROM movies AS m
WHERE 5 < -- Select all movies with more than 5 ratings
	(SELECT COUNT(rating)
	FROM renting AS r
	WHERE r.movie_id = m.movie_id);
```

- Select all movies with an average rating higher than 8.

```sql
SELECT *
FROM movies AS m
WHERE 8 < -- Select all movies with an average rating higher than 8
	(SELECT AVG(rating)
	FROM renting AS r
	WHERE r.movie_id = m.movie_id);
```

# Queries with EXISTS

**Personal notes:**

The `EXISTS` function is a special case of a correlated nested query that allows you to check whether the result of a correlated nested query is empty or not. It returns a boolean value, either `TRUE` or `FALSE`. If the result of the correlated nested query has at least one row, indicating that it is not empty, `EXISTS` returns `TRUE`. If the nested query returns an empty table, it returns `FALSE`. When `EXISTS` returns `TRUE`, the corresponding row from the outer query is selected.

*Example:*

```sql
-- Example using EXISTS to find customers who have rented movies
SELECT customer_id, customer_name
FROM customers AS outer
WHERE EXISTS (SELECT * FROM rentals WHERE customer_id = outer.customer_id);
```

In this query:
- The outer query (`SELECT customer_id, customer_name FROM customers AS outer`) processes each row in the `customers` table.
- The correlated subquery `(SELECT * FROM rentals WHERE customer_id = outer.customer_id)` checks if the current customer in the outer query has rented any movies.

If the result of the subquery is not empty (i.e., the customer has rented movies), the row from the outer query is selected.

*NOT EXISTS*

The `NOT EXISTS` function is used to check if a subquery returns an empty set. It returns `TRUE` if the subquery is empty (no rows returned) and `FALSE` otherwise. It is essentially the opposite of `EXISTS`.

*Example:*

```sql
-- Example using NOT EXISTS to find customers who have not rented movies
SELECT customer_id, customer_name
FROM customers AS outer
WHERE NOT EXISTS (SELECT * FROM rentals WHERE customer_id = outer.customer_id);
```

In this query, the result is a list of customers who have not rented any movies.

Both `EXISTS` and `NOT EXISTS` are powerful tools for filtering results based on the presence or absence of rows in a correlated nested query. They are especially useful in scenarios where you need to check for the existence of related records in another table.

**Exercises:**

**Customers with at least one rating**

Having active customers is a key performance indicator for MovieNow. Make a list of customers who gave at least one rating.

**Instructions:**

- Select all records of movie rentals from customer with ID 115.

```sql
-- Select all records of movie rentals from customer with ID 115
SELECT *
FROM renting as r
WHERE r.customer_id = 115;
```

- Select all records of movie rentals from the customer with ID 115 and exclude records with null ratings.

```sql
SELECT *
FROM renting
WHERE rating IS NOT NULL -- Exclude those with null ratings
AND customer_id = 115;
```

- Select all records of movie rentals from the customer with ID 1, excluding null ratings.

```sql
SELECT *
FROM renting
WHERE rating IS NOT NULL -- Exclude null ratings
AND customer_id = 1; -- Select all ratings from customer with ID 1
```

- Select all customers with at least one rating. Use the first letter of the table as an alias.

```sql
SELECT *
FROM customers AS c -- Select all customers with at least one rating
WHERE EXISTS 
	(SELECT *
	FROM renting AS r
	WHERE rating IS NOT NULL 
	AND r.customer_id = c.customer_id);
```

**Actors in comedies**

In order to analyze the diversity of actors in comedies, first, report a list of actors who play in comedies and then, the number of actors for each nationality playing in comedies.

**Instructions:**

- Select the records from the table actsin of all actors who play in a Comedy. Use the first letter of the table as an alias.

```sql
SELECT *  -- Select the records of all actors who play in a Comedy
FROM actsin AS ai
LEFT JOIN movies AS m
ON ai.movie_id = m.movie_id
WHERE m.genre = 'Comedy';
```

- Make a table of the records of actors who play in a Comedy and select only the actor with ID 1.

```sql
SELECT *
FROM actsin AS ai
LEFT JOIN movies AS m
ON m.movie_id = ai.movie_id
WHERE m.genre = 'Comedy'
AND ai.actor_id = 1; -- Select only the actor with ID 1
```

- Create a list of all actors who play in a Comedy. Use the first letter of the table as an alias.

```sql
SELECT *
FROM actors AS a
WHERE EXISTS
	(SELECT *
	 FROM actsin AS ai
	 LEFT JOIN movies AS m
	 ON m.movie_id = ai.movie_id
	 WHERE m.genre = 'Comedy'
	 AND ai.actor_id = a.actor_id);
```

- Report the nationality and the number of actors for each nationality.

```sql
SELECT a.nationality, COUNT(*) -- Report the nationality and the number of actors for each nationality
FROM actors AS a
WHERE EXISTS
	(SELECT ai.actor_id
	 FROM actsin AS ai
	 LEFT JOIN movies AS m
	 ON m.movie_id = ai.movie_id
	 WHERE m.genre = 'Comedy'
	 AND ai.actor_id = a.actor_id)
GROUP BY a.nationality;
```

# Queries with UNION and INTERSECT

**Personal notes:**

*UNION*

The `UNION` operator is used to combine the results of two or more `SELECT` statements. It returns a single result set that includes all the rows from the combined queries. The `UNION` operator eliminates duplicate rows from the result set.

**Example:*

```sql
-- Example using UNION to combine results from two tables
SELECT customer_id, customer_name FROM customers
UNION
SELECT customer_id, customer_name FROM other_customers;
```

In this example, the `UNION` operator combines the results of the two `SELECT` statements, removing duplicate rows.

*INTERSECT*

The `INTERSECT` operator is used to retrieve the common rows from two or more `SELECT` statements. It returns a result set containing only the rows that appear in all the specified queries.

**Example:*

```sql
-- Example using INTERSECT to find common rows in two tables
SELECT customer_id, customer_name FROM customers
INTERSECT
SELECT customer_id, customer_name FROM preferred_customers;
```

In this example, the `INTERSECT` operator returns only the rows that are common to both tables, eliminating rows that do not appear in both result sets.

Both `UNION` and `INTERSECT` are powerful tools for combining or finding common rows across multiple tables or queries. They provide flexibility in constructing more complex queries to meet specific requirements.

**Exercises:**

**Young actors not coming from the USA**

As you've just seen, the operators UNION and INTERSECT are powerful tools when you work with two or more tables. Identify actors who are not from the USA and actors who were born after 1990.

**Instructions:**

- Report the name, nationality and the year of birth of all actors who are not from the USA.

```sql
SELECT name,  -- Report the name, nationality and the year of birth
       nationality, 
       year_of_birth
FROM actors
WHERE nationality <> 'USA'; -- Of all actors who are not from the USA
```

- Report the name, nationality and the year of birth of all actors who were born after 1990.

```sql
SELECT name, 
       nationality, 
       year_of_birth
FROM actors
WHERE year_of_birth > '1990'; -- Born after 1990
```

- Select all actors who are not from the USA and all actors who are born after 1990.

```sql
SELECT name, 
       nationality, 
       year_of_birth
FROM actors
WHERE nationality <> 'USA'
UNION -- Select all actors who are not from the USA and all actors who are born after 1990
SELECT name, 
       nationality, 
       year_of_birth
FROM actors
WHERE year_of_birth > 1990;
```

- Select all actors who are not from the USA and who are also born after 1990.

```sql
SELECT name, 
       nationality, 
       year_of_birth
FROM actors
WHERE nationality <> 'USA'
INTERSECT -- Select all actors who are not from the USA and who are also born after 1990
SELECT name, 
       nationality, 
       year_of_birth
FROM actors
WHERE year_of_birth > 1990;
```

**Dramas with high ratings**

The advertising team has a new focus. They want to draw the attention of the customers to dramas. Make a list of all movies that are in the drama genre and have an average rating higher than 9.

**Instructions:**

- Select the IDs of all dramas.

```sql
SELECT movie_id -- Select the IDs of all dramas
FROM movies
WHERE genre = 'Drama';
```

- Select the IDs of all movies with average rating higher than 9.

```sql
SELECT movie_id -- Select the IDs of all movies with average rating higher than 9
FROM renting
GROUP BY movie_id
HAVING AVG(rating) > 9;
```

- Select the IDs of all dramas with average rating higher than 9.

```sql
SELECT movie_id
FROM movies
WHERE genre = 'Drama'
INTERSECT  -- Select the IDs of all dramas with average rating higher than 9
SELECT movie_id
FROM renting
GROUP BY movie_id
HAVING AVG(rating) > 9;
```

- Select all movies of in the drama genre with an average rating higher than 9.

```sql
SELECT *
FROM movies
WHERE movie_id IN -- Select all movies of genre drama with average rating higher than 9
   (SELECT movie_id
    FROM movies
    WHERE genre = 'Drama'
    INTERSECT
    SELECT movie_id
    FROM renting
    GROUP BY movie_id
    HAVING AVG(rating)>9);
```

# Data Driven Decision Making with OLAP SQL queries

**Chapter description:**

The OLAP extensions in SQL are introduced and applied to aggregated data on multiple levels. These extensions are the CUBE, ROLLUP and GROUPING SETS operators.

# OLAP: CUBE operator

**Personal notes:**

*Introduction to OLAP*

OLAP, or Online Analytical Processing, is a category of tools and techniques that allow users to interactively analyze and explore data to gain insights. OLAP operations often involve aggregating and summarizing data to provide a better overview. Three key OLAP operators for this purpose are `CUBE`, `ROLLUP`, and `GROUPING SETS`.

*CUBE Operator*

The `CUBE` operator is used in SQL for OLAP operations to generate all possible subtotals and grand totals for a set of columns. It produces a result set that represents data at different levels of aggregation. The `CUBE` operator is typically used with the `GROUP BY` clause.

**Syntax:*

```sql
SELECT column1, column2, ..., aggregate_function(column)
FROM table
GROUP BY CUBE (column1, column2, ...);
```

**Example:*

```sql
-- Example using CUBE to generate subtotals and grand totals
SELECT category, city, SUM(sales)
FROM sales_data
GROUP BY CUBE (category, city);
```

In this example, the `CUBE` operator generates a result set with subtotals and grand totals for both the `category` and `city` columns, giving a comprehensive view of sales data.

The `CUBE` operator is useful for multidimensional analysis, allowing users to explore data at various levels of granularity. It's a powerful tool for business intelligence and reporting, providing a holistic view of aggregated data.

**Exercises:**

**Groups of customers**

Use the CUBE operator to extract the content of a pivot table from the database. Create a table with the total number of male and female customers from each country.

**Instruction:**

- Create a table with the total number of customers, of all female and male customers, of the number of customers for each country and the number of men and women from each country.

```sql
SELECT country, -- Extract information of a pivot table of gender and country for the number of customers
	   gender,
	   COUNT(*)
FROM customers
GROUP BY CUBE (gender, country)
ORDER BY country;
```

**Categories of movies**

Give an overview on the movies available on MovieNow. List the number of movies for different genres and release years.

**Instructions:**

- List the number of movies for different genres and the year of release on all aggregation levels by using the CUBE operator.

```sql
SELECT genre,
       year_of_release	,
       COUNT(*)
FROM movies
GROUP BY CUBE (genre, year_of_release)
ORDER BY year_of_release;
```

- Question: Which statement is NOT correct about the result table?

        "The year of release with most movies is 2014."

**Analyzing average ratings**

Prepare a table for a report about the national preferences of the customers from MovieNow comparing the average rating of movies across countries and genres.

**Instructions:**

- Augment the records of movie rentals with information about movies and customers, in this order. Use the first letter of the table names as alias.

```sql
-- Augment the records of movie rentals with information about movies and customers
SELECT *
FROM renting AS r
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id;
```

- Calculate the average rating for each country.

```sql
-- Calculate the average rating for each country
SELECT 
	c.country,
    AVG(r.rating)
FROM renting AS r
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
GROUP BY c.country;
```

- Calculate the average rating for all aggregation levels of country and genre.

```sql
SELECT 
	c.country, 
	m.genre, 
	AVG(r.rating) AS avg_rating -- Calculate the average rating 
FROM renting AS r
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
GROUP BY CUBE (m.genre, c.country); -- For all aggregation levels of country and genre
```

- Question: What is the average rating over all records, rounded to two digits?

        "7.94"

# ROLLUP

**Personal notes:**

The `ROLLUP` operator is another OLAP operator used in SQL to perform aggregations and generate subtotals and grand totals. Like the `CUBE` operator, `ROLLUP` is used in conjunction with the `GROUP BY` clause. However, it produces a more limited set of aggregations compared to `CUBE`.

**Syntax:*

```sql
SELECT column1, column2, ..., aggregate_function(column)
FROM table
GROUP BY ROLLUP (column1, column2, ...);
```

**Example:*

```sql
-- Example using ROLLUP to generate subtotals and grand totals
SELECT category, city, SUM(sales)
FROM sales_data
GROUP BY ROLLUP (category, city);
```

In this example, the `ROLLUP` operator generates a result set with subtotals and grand totals for the `category` and `city` columns. It produces a hierarchy of aggregations, creating a subtotal for each level of the specified columns.

The key difference between `CUBE` and `ROLLUP` is that `CUBE` generates all possible combinations of subtotals, while `ROLLUP` generates a more structured set of aggregations, following the specified hierarchy.

Both `CUBE` and `ROLLUP` are valuable tools for multidimensional analysis in business intelligence and reporting. They allow users to explore data at different levels of granularity and obtain insights into various aspects of the data.

**Exercises:**

**Number of customers**

You have to give an overview of the number of customers for a presentation.

**Instructions:**

- Generate a table with the total number of customers, the number of customers for each country, and the number of female and male customers for each country.

- Order the result by country and gender.

```sql
-- Count the total number of customers, the number of customers for each country, and the number of female and male customers for each country
SELECT country,
       gender,
	   COUNT(*)
FROM customers
GROUP BY ROLLUP (country, gender)
ORDER BY country, gender; -- Order the result by country and gender
```

**Analyzing preferences of genres across countries**

You are asked to study the preferences of genres across countries. Are there particular genres which are more popular in specific countries? Evaluate the preferences of customers by averaging their ratings and counting the number of movies rented from each genre.

**Instructions:**

- Augment the renting records with information about movies and customers.

```sql
-- Join the tables
SELECT *
FROM renting AS r
LEFT JOIN movies AS m
ON r.movie_id = m.movie_id
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id;
```

- Calculate the average ratings and the number of ratings for each country and each genre. Include the columns country and genre in the SELECT clause.

```sql
SELECT 
	c.country, -- Select country
	m.genre, -- Select genre
	AVG(r.rating), -- Average ratings
	COUNT(*)  -- Count number of movie rentals
FROM renting AS r
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
GROUP BY (country, genre) -- Aggregate for each country and each genre
ORDER BY c.country, m.genre;
```

- Finally, calculate the average ratings and the number of ratings for each country and genre, as well as an aggregation over all genres for each country and the overall average and total number.

```sql
-- Group by each county and genre with OLAP extension
SELECT 
	c.country, 
	m.genre, 
	AVG(r.rating) AS avg_rating, 
	COUNT(*) AS num_rating
FROM renting AS r
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
GROUP BY ROLLUP (country, genre)
ORDER BY c.country, m.genre;
```

# GROUPING SETS

**Personal notes:**

*GROUPING SETS in OLAP*

The `GROUPING SETS` clause is a powerful and flexible OLAP feature in SQL that allows you to specify multiple grouping sets within a single `GROUP BY` query. It provides a way to define several levels of aggregation in a single query, enabling a more customized and efficient approach to summarizing data.

**Syntax:*

```sql
SELECT column1, column2, ..., aggregate_function(column)
FROM table
GROUP BY GROUPING SETS ((column1, column2, ...), (column1), (column2), ...);
```

**Example:*

```sql
-- Example using GROUPING SETS to specify multiple levels of aggregation
SELECT country, genre, COUNT(*)
FROM rentings_extended
GROUP BY GROUPING SETS ((country, genre), (country), (genre), ());
```

In this example, the `GROUPING SETS` clause is used to define four groups: one for the combination of `country` and `genre`, one for `country` only, one for `genre` only, and an empty grouping set (representing the grand total). The result is a combination of the aggregations for each specified grouping set.

The `GROUPING SETS` clause is particularly useful when you want to aggregate data at various levels within the same query, avoiding the need to execute multiple separate queries or use complex `UNION` operations.

It provides a more efficient way to obtain aggregated results for different dimensions, making it a valuable tool for data analysis and reporting in OLAP scenarios.

**Exercises:**

**Queries with GROUPING SETS**

What question CANNOT be answered by the following query?
```sql
SELECT 
  r.customer_id, 
  m.genre, 
  AVG(r.rating), 
  COUNT(*)
FROM renting AS r
LEFT JOIN movies AS m
ON r.movie_id = m.movie_id
GROUP BY GROUPING SETS ((r.customer_id, m.genre), (r.customer_id), ());
```

        Answer: "What is the average rating for each genre?"

**Exploring nationality and gender of actors**

For each movie in the database, the three most important actors are identified and listed in the table actors. This table includes the nationality and gender of the actors. We are interested in how much diversity there is in the nationalities of the actors and how many actors and actresses are in the list.

**Instruction:**

- Count the number of actors in the table actors from each country, the number of male and female actors and the total number of actors.

```sql
SELECT 
	nationality, -- Select nationality of the actors
    gender, -- Select gender of the actors
    COUNT(*) -- Count the number of actors
FROM actors
GROUP BY GROUPING SETS ((nationality), (gender), ()); -- Use the correct GROUPING SETS operation
```

**Exploring rating by country and gender**

Now you will investigate the average rating of customers aggregated by country and gender.

**Instructions:**

- Select the columns country, gender, and rating and use the correct join to combine the table renting with customer.

```sql
SELECT 
	c.country, -- Select country, gender and rating
    c.gender,
    r.rating
FROM renting AS r
LEFT JOIN customers AS c -- Use the correct join
ON r.customer_id = c.customer_id;
```

- Use GROUP BY to calculate the average rating over country and gender. Order the table by country and gender.

```sql
SELECT 
	c.country, 
    c.gender,
	AVG(r.rating) -- Calculate average rating
FROM renting AS r
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
GROUP BY country, gender -- Order and group by country and gender
ORDER BY country, gender;
```

- Now, use GROUPING SETS to get the same result, i.e. the average rating over country and gender.

```sql
SELECT 
	c.country, 
    c.gender,
	AVG(r.rating)
FROM renting AS r
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
GROUP BY GROUPING SETS ((country, gender)); -- Group by country and gender with GROUPING SETS
```

- Report all information that is included in a pivot table for country and gender in one SQL table.

```sql
SELECT 
	c.country, 
    c.gender,
	AVG(r.rating)
FROM renting AS r
LEFT JOIN customers AS c
ON r.customer_id = c.customer_id
-- Report all info from a Pivot table for country and gender
GROUP BY GROUPING SETS ((country, gender), (country), (gender), ());
```

# Bringing it all together

**Exercises:**

**Customer preference for genres**

You just saw that customers have no clear preference for more recent movies over older ones. Now the management considers investing money in movies of the best rated genres.

- Augment the records of movie rentals with information about movies. Use the first letter of the table as alias.

```sql
SELECT *
FROM renting AS r
LEFT JOIN movies AS m -- Augment the table with information about movies
ON r.movie_id = m.movie_id;
```

- Select records of movies with at least 4 ratings, starting from 2018-04-01.

```sql
SELECT *
FROM renting AS r
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
WHERE r.movie_id IN ( -- Select records of movies with at least 4 ratings
	SELECT movie_id
	FROM renting
	GROUP BY movie_id
	HAVING COUNT(rating) >= 4 )
AND r.date_renting >= '2018-04-01'; -- Select records of movie rentals since 2018-04-01
```

- For each genre, calculate the average rating (use the alias avg_rating), the number of ratings (use the alias n_rating), the number of movie rentals (use the alias n_rentals), and the number of distinct movies (use the alias n_movies).

```sql
SELECT m.genre, -- For each genre, calculate:
	   AVG(r.rating) AS avg_rating,-- The average rating and use the alias avg_rating
	   COUNT(r.rating) AS n_rating,-- The number of ratings and use the alias n_rating
	   COUNT(*) AS n_rentals,-- The number of movie rentals and use the alias n_rentals
	   COUNT (DISTINCT r.movie_id) AS n_movies -- The number of distinct movies and use the alias n_movies
FROM renting AS r
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
WHERE r.movie_id IN ( 
	SELECT movie_id
	FROM renting
	GROUP BY movie_id
	HAVING COUNT(rating) >= 3)
AND r.date_renting >= '2018-01-01'
GROUP BY m.genre;
```

- Order the table by decreasing average rating.

```sql
SELECT genre,
	   AVG(rating) AS avg_rating,
	   COUNT(rating) AS n_rating,
       COUNT(*) AS n_rentals,     
	   COUNT(DISTINCT m.movie_id) AS n_movies 
FROM renting AS r
LEFT JOIN movies AS m
ON m.movie_id = r.movie_id
WHERE r.movie_id IN ( 
	SELECT movie_id
	FROM renting
	GROUP BY movie_id
	HAVING COUNT(rating) >= 3 )
AND r.date_renting >= '2018-01-01'
GROUP BY genre
ORDER BY avg_rating DESC; -- Order the table by decreasing average rating
```

**Customer preference for actors**

The last aspect you have to analyze are customer preferences for certain actors.

**Instructions:**

- Join the tables.

```sql
-- Join the tables
SELECT *
FROM renting AS r
LEFT JOIN actsin AS ai
ON r.movie_id = ai.movie_id
LEFT JOIN actors AS a
ON ai.actor_id = a.actor_id;
```

- For each combination of the actors' nationality and gender, calculate the average rating, the number of ratings, the number of movie rentals, and the number of actors.

```sql
SELECT a.nationality,
       a.gender,
	   AVG(r.rating) AS avg_rating, -- The average rating
	   COUNT(r.rating) AS n_rating, -- The number of ratings
	   COUNT(*) AS n_rentals, -- The number of movie rentals
	   COUNT (DISTINCT a.actor_id) AS n_actors -- The number of actors
FROM renting AS r
LEFT JOIN actsin AS ai
ON ai.movie_id = r.movie_id
LEFT JOIN actors AS a
ON ai.actor_id = a.actor_id
WHERE r.movie_id IN ( 
	SELECT movie_id
	FROM renting
	GROUP BY movie_id
	HAVING COUNT(rating) >=4 )
AND r.date_renting >= '2018-04-01'
GROUP BY (a.nationality, a.gender); -- Report results for each combination of the actors' nationality and gender
```

- Provide results for all aggregation levels represented in a pivot table.

```sql
SELECT a.nationality,
       a.gender,
	   AVG(r.rating) AS avg_rating,
	   COUNT(r.rating) AS n_rating,
	   COUNT(*) AS n_rentals,
	   COUNT(DISTINCT a.actor_id) AS n_actors
FROM renting AS r
LEFT JOIN actsin AS ai
ON ai.movie_id = r.movie_id
LEFT JOIN actors AS a
ON ai.actor_id = a.actor_id
WHERE r.movie_id IN ( 
	SELECT movie_id
	FROM renting
	GROUP BY movie_id
	HAVING COUNT(rating) >= 4)
AND r.date_renting >= '2018-04-01'
GROUP BY GROUPING SETS ((a.nationality, a.gender), (a.nationality), (a.gender), ()); -- Provide results for all aggregation levels represented in a pivot table
```

# Data Communication Concepts

**Course Description**

You’ve analyzed your data, run your model, and made your predictions.  Now, it's time to bring your data to life! Presenting findings to stakeholders so they can make data-driven decisions is an essential skill for all data scientists. In this course, you’ll learn how to use storytelling to connect with your audience and help them understand the content of your presentation—so they can make the right decisions. Through hands-on exercises, you’ll learn the advantages and disadvantages of oral and written formats. You’ll also improve how you translate technical results into compelling stories, using the correct data, visualizations, and in-person presentation techniques. Start learning and improve your data storytelling today.

# Storytelling with Data

**Chapter description:**

Let's start with the importance of data storytelling and the elements you need to tell stories with data. You'll learn best practices to influence how decisions are made before learning how to translate technical results into stories for non-technical stakeholders.

# Fundamentals of storytelling

**Personal notes:**

### Fundamentals of Data Storytelling

*What is Data Storytelling?*

Data storytelling is a powerful mechanism for sharing insights supported by a compelling narrative and efficient visualizations. Anecdotes stimulate people's imagination, and stories are more memorable than metrics, adding value by providing context to the data. Thanks to this, the audience can understand the insights, facilitating the decision-making process and, in turn, driving actions and changes.

*Elements of Data Storytelling:*
1. *Three-Minute Story:* The concept of a three-minute story challenges us to focus on essential elements if we only had three minutes to tell a story. It emphasizes brevity and clarity in communication.

2. *The Big Idea:* This concept encourages us to articulate the unique viewpoint of our story in a single sentence. It helps distill the core message, making it clear and concise.

*Three Central Elements for Any Data Story:*
1. *Insightful:* Derives clear learnings from the analysis.
2. *Explanatory:* Helps the audience understand the insights.
3. *Concise:* Presents only concrete and specific facts.

*Building an Effective Data Story:*
1. *Inclusion of Relevant Discoveries:* Include findings from models or analyses that apply to the situation. Base the story on accurate and reliable data, excluding unreliable results.

2. *Actionable Insights:* The story should always include actionable insights—data that drives action.

3. *Engaging Narrative:* A good data story comprises a compelling and easy-to-understand narrative, focusing on key points necessary for driving change.

4. *Central Theme:* While it may be tempting to include many disconnected facts, an effective narrative revolves around a central vision, considering the background and the target audience to clarify the facts for them.

5. *Linear Sequence:* Every data story follows a linear sequence, ensuring that all data points complement each other until the conclusion is reached. However, caution should be exercised to avoid including misleading charts.

Effective data storytelling involves crafting a narrative that is not only informative but also captivating, ensuring that the audience can comprehend and act upon the presented insights.

**Exercises:**

**The story begins**

You recently started working as a data scientist at a company named Communicatb. For your first project, you and your team need to analyze customer churn data for a cell phone company. The goal is to predict their behavior and help develop a program to retain customers.

Your team lead knows you are an expert on storytelling. She asks you to explain to the team why crafting a compelling story is important when delivering results. You write down a list of reasons to be prepared.

One of the statements you wrote is false. Can you select which one is it?

        "Even if your data do not reveal a distinct customer behavior, storytelling might influence stakeholders to create the retention program."

**Building a story**

You nailed it! Your explanation of why stories are efficient when conveying insights went very well! Now, your team lead would like you to give a short presentation. You're going to explain the different steps involved in telling a story with data to the team. It will be the starting point for delivering the results of the churn project when it's ready.

You know it is an important task. To prepare for your talk, you look for your notes on the storytelling course you took, but realize that some parts are erased. So you need to remember the do's and dont's of data storytelling.

Which of the following statements about effective data storytelling are true, and which are false?

**Instruction:**

- Correctly classify the statements as either true or false.

![Image 4](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/d61b00aa-1631-4e37-b8bb-2e840007fe68)

# Translating technical results

**Personal notes:**

### Translating Technical Results

*Understanding the Audience's Technical Proficiency:*

It's crucial to assess the technical proficiency of your audience. Simplifying this into technical and non-technical categories facilitates better comprehension. Technical knowledge exists on a continuum, and it's your responsibility to gauge your audience's technical proficiency. While data professionals may enjoy discussing methods, less technical audiences are generally concerned with outcomes and implications.

*ADEPT Technique:*

The ADEPT technique, recommended by Kalid Azad, can be highly valuable. Here's a breakdown of the ADEPT principles:

1. *Analogies:*
   - Use analogies to relate new concepts to things that your audience is already comfortable with and understands well. Analogies bridge the gap between unfamiliar technical terms and familiar concepts.

2. *Diagrams:*
   - Visual aids, such as diagrams, are essential to help your audience visualize complex ideas. Diagrams provide a clear and structured representation, aiding in understanding.

3. *Examples:*
   - Illustrative examples have powerful explanatory capabilities. Real-world examples or scenarios can make technical concepts more relatable and easier to grasp.

4. *Plain Language:*
   - Pay attention to the language you use. Avoid unnecessary technical jargon, and opt for plain language that is easily understood. Technical terms may not be familiar to everyone, especially in scenarios where you're presenting to non-data sectors.

5. *Technical to Non-Technical Translation:*
   - Consider how to translate technical results into a language that resonates with a non-technical audience. Focus on the broader implications and outcomes rather than diving deep into technical details.

By incorporating the ADEPT technique, you can enhance the effectiveness of your communication, ensuring that your message is accessible and impactful for audiences across varying levels of technical expertise.

**Exercises:**

**A non-tech story**

The exploratory data analysis on the churn project is finished! It's now time for the monthly update meeting. You will have to explain your results to the operation specialist and the program director. You are addressing a non-technical audience, and want to make sure that your presentation is adapted to the audience you're addressing so that your message gets across.

You write down some statements you could use to explain your work, but you believe some of them are more suitable for a non-technical story, while others are too technical to include.

Can you select which sentences you should use in this case?

**Instruction:**

- Correctly classify the examples as more suitable either for a tech or non-tech stories.

![Image 5](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/367306f3-f231-463b-ae35-7e8c15aecab2)


**Be aware**

The meeting was a success! The program director asks you to send your results to the business specialists. You need to write a report and send it by email by the end of the week. You have never met them, so you ask for their background and goals.

After you gather data, you realize you will be communicating your results to a different audience. You want them to understand your results.

Can you select which of the following examples are best practices to translate your results?

**Instruction:**

- Correctly classify the examples as either best practice or bad practice.

![Image 6](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/4f306380-4a9e-4cf5-acc1-aec131b43310)


# Impacting the decision-making process

**Personal notes:**

*Compelling Narrative:*

After uncovering relevant insights in our data, it's crucial to present them meaningfully to our target audience. This involves crafting a compelling narrative that includes key points and facilitates change. In essence, we need a persuasive narrative that organizes information to engage the audience and make them care about the shared results or information.

*Narrative Structure:*

There are various narrative structures, but it all boils down to a framework that guides how we present our story. To initiate our data story, we should provide background details: insights into the problem that motivated the analysis, changes in the previous situation justifying an analysis, and who/what the analysis is focusing on.

After introducing the problem, evidence of contributing factors should be presented. However, only relevant information should be included, avoiding detailed data that might overwhelm the audience. Additional supporting evidence and data can be provided, helping to explain at a deeper level the root cause of the problem.

All evidence should lead to the climax: the moment when we introduce the central finding of our analysis. This should offer clear insights into what could happen if nothing is changed. Once the main discovery is revealed, we should conclude by exploring potential solutions and opportunities, recommending a course of action. Being proactive and guiding the audience through understanding what to do with our results is essential for impacting the decision-making process.

With these steps, we create a narrative that captures the interest of our audience.

*Building Narrative:*

During analysis, several observations can be made, leading to the construction of a narrative. This may involve examining how a variable changes over time or within a standard time cycle, focusing on relationships between two variables, or exploring similarities and differences among data groups. As we craft our narrative, it's crucial to ensure that these data points create a relevant and relatable story. The narrative should resonate with the audience and effectively convey the key messages derived from the analysis.

**Exercises:**

**Is it a true story?**

You have done an amazing job explaining your exploratory data analysis on the churn project. Now, it's time to run the model to predict customer churn. You know that you will have to craft an effective story to present these results.

You want to be prepared. So you read your notes on how to build a compelling narrative. But you realized that one of your notes is not accurate.

Which of the following statements is false?

        Answer: "Unless you have a great data groundwork to support your central insight, your findings will need a well-formed and compelling narrative to drive action and change."

**Structured to impact**

Your project on customer churn is done. You analyzed the data and built your model. You followed the steps for storytelling. Now, it's time to structure your story to have an impact at the decision-making level. You want stakeholders to follow your recommendations.

You like to write things down. So you take a pen and paper, and write down the different things you want to say in order on sticky notes. The window suddenly opens, throwing all of your notes on the floor.

Can you organize the steps for telling a story with data that is solid enough to influence the decision-makers?

**Instruction:**

- Order the steps chronologically: the first step should be on top and the last step at the bottom.

![Image 7](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/3be31aa5-f0db-492a-8198-e884a766793b)

**A story to compare**

Great job organizing your narrative structure! The next step is to think about how you will present your insights.

You start reading and discover there are several ways to present data stories. You can compare your data, show correlation, cluster your data…

You are curious to know what type of data story would be a good fit for your data. You write down the central finding, your insights and the supporting evidence.

Can you classify your findings into the following categories?

**Instruction:**

- Correctly classify the following examples as comparison, correlation or clustering.

![Image 8](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/1a9ad4af-98fb-41fe-8032-ec9af8e11018)

# Preparing to Communicate the Data

**Chapter description:**

Deepen your storytelling knowledge. Learn how to avoid common mistakes when telling stories with data by tailoring your presentations to your audience. Then learn best practices for including visualizations and choosing between oral or written formats to make sure your presentations pack a punch!

# Selecting the right data

**Personal notes:**

*Inclusive Insights:*
Selecting the right data involves incorporating sufficient contextual insights into our story to support our main point without overwhelming our report with information. In other words, we include the minimum amount of results that will bolster our narrative. Remember that data is one of the three central elements of any story. Once we find the insights, we need to showcase our results appropriately to highlight a different view of the data for each audience.

*Stakeholders:*
Stakeholders can be anyone or a group of people with an interest in the outcome of a project, decision, or activity derived from it. Different stakeholders will be interested in different findings, so we need to tailor how we present our results to each of them. As mentioned earlier, stakeholders can be technical or non-technical.

*Identifying Personas:*
Among them, we may have different types of audiences. A useful tool is identifying audience personas. This means describing the interests in project outcome and technical knowledge of someone who represents our ideal target audience. Defining personas helps select customized findings to better convey our key insights.

1. *Executive Team:*
   The first person you might report to is the executive team—likely the CEO, an investor, a director, or a founder. They have a basic understanding of technical aspects and usually need to inform their decisions using our project findings.

2. *Project Manager:*
   When telling the story to our project manager, we can showcase the total cost of the upcoming proposal steps and general metrics, as well as the risk of our plan failing.

3. *Tech Team:*
   We can also present a report to our project collaborators or a technical supervisor with high technical knowledge. They are likely interested in replicating or continuing the project.

4. *General Audience:*
   Finally, we can present our story to an external client or another department employee, likely with basic technical knowledge, wanting to understand the project's impact.
 
**Exercises:**

**The truth about salaries**

Your predictive model for customer churn, which you worked on in Chapter 1, has been deployed. Your project manager asks you to work on a new internal project. The goal is to analyze a database with employee salaries in San Francisco, USA.

After doing an exhaustive exploratory data analysis, you have to present your findings to the human resources team. They want to compare San Francisco salary growth to the one at the company; they need to understand how to forecast salaries for the next year. You are about to copy the graphs from your analysis. Your manager reminds you to select the right data for your stakeholders.

You start by writing down what you believe can help you choose the proper findings.

One of the statements you wrote is false. Can you select which one it is?

        Answer: "Select all collected numerical data about San Francisco salaries and show them in a big dashboard so it helps understand in detail why salaries have been increasing."


**Earning interests**

Well done! Your presentation with the human resource department was a success. Your team lead asks you to show your data analysis results to different stakeholders. Before you dive into preparing the presentation or the report, you want to make sure that you are aligned with their interests.

With that goal in mind, you define several personas. It will help you select the suitable data later. You write down the personas, their knowledge, and their interest on this project.

Can you classify your notes into the following audience personas?

**Instruction:**

- Correctly classify the following examples as Human Resources Director, technical supervisor, or marketing staff.

![Image 9](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/e054ecb9-99cc-4099-9ebb-83a61cddd8a7)

# Showing relevant statistics

**Personal notes:**

*Variations of Data:*

Sometimes, we want to compare one or several specific variables over time. The difference can be expressed with an absolute number or a growth rate. When focusing on one variable, an absolute number is okay, but when looking at various variables, the growth rate tends to be more informative as it allows for comparisons across different scales. Absolute changes for a small number may seem small even if the relative change is large, and vice versa.

*Ratio:*

A ratio is a comparison of two variables expressed as a quotient, like revenue per customer: calculated as the total revenue of the product in dollars divided by the number of customers. Ratios help normalize values, which, in turn, aids in comparing the distribution of data from originally different scales.

*Aggregates:*

Sometimes we need to summarize numerical data into an aggregate—a number that gives an idea of one or a representative value. It can be a simple total or count, like total sales or how long a campaign will last. Another common aggregate is the average, such as the average number of chocolates or snacks sold per year or the average (median) price of each product. The average can be misleading, especially if there are outliers.

*p-value:*

When communicating results, we often need to provide evidence that they are statistically significant (i.e., not due to randomness). A p-value below 0.05 is considered an indicator of significance by convention. The lower it is below 0.05, the stronger the indicator. However, it is not proof of evidence; it only rejects or accepts a hypothesis without saying anything about its truth. Due to the frequency with which p-value metrics are misunderstood or confusing for the public, consider alternative metrics or add a few more in support.

**Exercises:**

**Salary variation**

You have selected suitable data for your story on San Francisco salaries. Now, you evaluate which metrics you should use.

You want to convey the following message to the human resource team: "The total pay of employees has increased or decreased according to their job title from 2017 to 2018."

You prepared the two visualizations below, but you are unsure which one is best.

One of the following options is True. Can you select which one is it?

        "The graph on the right is the best way to convey the message. With percentage change, the magnitude of the salary change depending on the job is more evident."

**On a payroll**

Good job on selecting the most impactful visualization! Your insight made an impact. The human resource team lead asked you to show more findings. You go back to your exploratory data analysis and select some data.

But you want to explore different variants of the same data to discover the best one for explaining your distinct insights to the human resource team.

Can you decide what data variant would be best suited depending on the finding you want to show?

**Instruction:**

- Correctly classify the following examples as total values, change or ratio.

![Image 10](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/b4f84a31-44cc-4c60-af18-84c5050e05cd)

**It's not significant**

You have a big deadline ahead. You need to submit a report on the data analysis for the project on San Francisco salaries to your technical lead. He will read it and report your results to the senior management team.

You have a story, and you select data to support it. You want to show comparisons of average pay for people with different job titles.

You are hesitant to show p-values. You know that there are a lot of misconceptions around it. You decide to use it anyway. However, you plan to clarify any confusion about p-values, so your audience understands its meaning and trusts your results.

Can you classify these statements as good use or misuse of the p-value?

**Instruction:**

- Correctly classify the following examples as either a good use or a misuse.

![Image 11](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/400817b9-39fa-429e-8654-fec175543f4c)

# Visualizations for different audiences

**Personal notes:**

*Provide Context:*

When we find insights and have the right data, we still need to choose and adjust a visualization for the message we want to convey. Again, we should consider our audience's expertise and familiarity with concepts to select charts they can easily interpret.

*Provide Context:*

Visualizations should also provide context to support our message. For an investor, we might include a chart showing the factors that most influence a customer to buy our products. A technical leader will be interested in that but also more details about the analysis itself, like the detailed importance of the feature.

*More Best Practices:*

The Pareto principle states that the majority of outputs come from a minority of inputs. Therefore, in addition to the data contributing to our story, there will be some less relevant data that we still want to include. We should aggregate them to reduce noise. Our visual assets can become accessible and engaging by considering the audience's background and simplifying the visuals to the audience's knowledge level. Basically, you care about how many insights your audience gets from your visualization and how quickly they get it. A complex plot gives many insights but takes time to understand; a simple plot gives few insights but is quick to understand. Overall, less is more. Instead of showing many detailed visuals, we should focus on the simplest and most relevant ones that support our message.

*McCandless Method:*

There are some steps we can follow to include and present the visualization effectively to our audience. They were established by David McCandless, a British data journalist. First, we should give a title to our chart, which we then use to introduce the visualization and focus the audience's attention on it. The title should be short, clear, and obvious: it supports our story and clarifies the visualization. When in doubt, we can use the y-axis vs x-axis technique. Next, we should anticipate common questions from our audience. With these questions answered before they are even asked, attention is directed to our chart and our story. After that, we need to clarify which insights the visual is showing. We should explain what they are seeing and not assume they will ask later or understand on their own. For example, chocolate sales decreased over time. Finally, we need to help the audience relate to the chart and its insights. Make sure they understand why the insights are important, how it will support additional insights in the presentation, or how these insights can be put into practice.

**Exercises:**

**Salary development**

You are presenting your data analysis of San Francisco salaries to the business development department.

You have your story, and you selected data and metrics to support it. But choosing the visualizations is still an ongoing task. You decide to speed it up by getting hands-on. You want to follow the best practices.

The message you want to convey is: "San Francisco salaries have been constantly going up in the last 4 years. The percentage variation is 10% annually. The salary of people working in the private sector, such as software or biotechnology, have increased by 100k."

Can you classify if these practices would be good or bad when presenting to the business department?

**Instruction:**

- Correctly classify the following statements as being either true or false for choosing an effective visualization.

![Image 12](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/a0a1ee33-07cc-4e01-91e6-1706b9bd7c9c)

**Salary on demand**

You have selected visualizations for the business development department.

It's time to include them in your report and present them. You are aware of the steps you should follow to include and present visualizations effectively, and you want to do your best and impress your business coworkers. So you ask a colleague to help you organize your thoughts.

Can you order the steps for including and presenting visual data effectively?

**Instruction:**

- Order the steps chronologically: the first step should be on top and the last step at the bottom.

![Image 13](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/49883af4-8387-4bc8-b181-1851657627e4)

# Choosing the appropriate format

**Personal notes:**

*Presentation Strategy:*

A good communication format displays key project information in an innovative and easy-to-understand way. There are two main formats we will discuss here: written reports and oral presentations. Most data science projects will require both a written report and an oral presentation, but ultimately, it depends on the situation and the specific project.

*Presentation Strategy:*

There are several things to consider when sharing findings: our audience, the content to include, special requirements to take into account, and which channel to use. All these elements help us define the best format to communicate our results.

*Stakeholders:*

The first thing to consider is who we are presenting to; this helps figure out why they need to know about the findings. Is it for accountability? To understand the methodology? How will they use our findings - to make a decision, initiate a new project? What information do they need from our results? The impact our findings have?

*Content:*

The answers to these questions help us decide what content to include. Should we focus on results, conclusions, include recommendations, or just explain the methods in detail?

*Requirements:*

The next step is to identify if any stakeholders have special requirements. Do they have enough time to read a detailed report, or is a short meeting better? Do they report to someone else and need a document to back up a claim? Are they in a different time zone, so written communication is preferable?

*Consumption:*

We also need to think about how our presentation will be consumed. Could we write a document like a Word file, a Jupyter notebook, a blog post, or an article? We could also build a slide deck. How will it be delivered? Will we present directly to stakeholders, being able to respond to comments or questions, or will we share via email or Slack and answer questions later? Finally, what would be the audience size? We cannot present things the same way in a conference room with six people or in a hall for two hundred people.

*Oral Communication:*

Oral communication allows building a relationship with the audience and facilitates immediate feedback or actions. It conveys a rich message because body language and voice add meaning. However, the message cannot be revised because there is no permanent record of communication and is not suitable for long messages, as the longer the presentation, the higher the chance the audience will lose focus at some point.

*Written Communication:*

The written format provides records of communication so that the message can be reviewed in the long term. It is easy to share with large audiences and is less prone to emotional reactions. It is also suitable for sharing code with any interested technical individuals for review or replication. However, not seeing the audience's reaction makes adaptation more challenging, as feedback is not immediate but will come later in the form of comments.

**Exercises:**

**A communication problem**

Your coworker has been working on a project on price predictions. He asks you to help him choose the most suitable format to deliver his results to the executive board as well as to his team.

You give him a set of advice and rules of thumb, so he can make an informed decision. When you arrive home, you realize that you made one mistake.

Which of the following advice should you not have provided?

        "If a software engineer in your team wants to continue your project with new data, the central piece of information to include in your meeting is the project conclusions."

**Should we meet?**

It's Friday. Your project manager comes by your desk. She asks you about the status of your project on salaries for San Francisco employees. She tells you that you need to close the project. Fortunately, you have finished building the model.

But to close it, you need to communicate the results to the different stakeholders. After she talks with the people involved, you start to receive emails asking about the results. You need to decide if you are going to use an oral presentation or a written report.

Can you decide what type of format would be best suited depending on the situation and requirements?

**Instruction:**

- Correctly classify the following inquiries as suitable for an oral or written format.

![Image 14](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/3f8b92bd-a175-4cd9-be14-35bc84b531d2)

**When in doubt**

You manage to deliver the results to almost all the stakeholders. You are about to start writing the report for the founder when you get an email. Your founder is coming by the office the following Friday. Your manager wants to know if presenting the project during a meeting would be better.

You have second thoughts about changing the format. So you decide to write down beneficial and unfavorable aspects of an oral presentation.

Can you classify your thoughts correctly?

**Instruction:**

- Correctly classify examples where an oral presentation is either beneficial or a unfavorable.

![Image 15](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/90a0d6b3-93b5-40d9-a9cb-d029f3a91f18)

# Structuring Written Reports

**Chapter description:**

Now that you understand how to prepare for communicating findings, it’s time to learn how to structure your reports. You'll also learn the importance of reproducibility (work smarter, not harder) and how to get to the point when describing your findings. You’ll then get to apply all you’ve learned to a real-world use case as you create a compelling report on credit risk.

# Types of reports

**Personal notes:**

*Types of Reports:*

There are different types of reports:

- *Informative Reports:* Provide factual information, are usually short, lack a rigid structure, and aim to inform about facts without adding any analysis.
  
- *Analytical Reports:* Provide analyses and demonstrate relationships or recommendations, can vary in size but have a rigid structure, and aim to guide decision-making based on data.
  
- *Final Reports:* Include detailed data analyses, findings, and results, as well as visual resources. They are generally long because they are intended for audiences that need technical details.
  
- *Summary Reports:* Include key findings and recommendations, as well as visual resources. They are usually short, under five pages, and, as a summary of a final report, may include links to the main document. They are intended for decision-makers who do not need technical details.

*Report Structure:*

There is a straightforward structure to follow for analytical, final, and summary reports. The first section is the introduction, where we summarize the report's objective. After that, contextual information about why we conducted the analysis shown should be included. To conclude the introduction, we must summarize our analysis questions.

Next, we create sections for the body of the report. In the data section, we write a description of the most relevant data used, potentially including tables. In the methods section, we describe the methods used to collect and analyze the data and build the model. In the analysis section, we include the selected data for analysis and model using visual resources, such as charts. In the results section, we describe and explain the results of our analysis, and we may include visual resources to assess them.

Finally, we create a conclusion section, where we restate the analysis questions, as well as summarize the most important results of the analysis. This part is the appropriate place to add our recommendations for the next steps.

*Report Structure (Business Context):*

In a business context, your audience is different, so you need to adapt. An efficient method is the 1-3-25 approach: 1-page abstract, a maximum of 3 pages of an executive summary, and a maximum of 25 pages of details. The executive summary is enough for people to understand and have their conclusions about whether it's worth reading the full report. Again, we must keep our audience in mind. Each stakeholder is interested in different parts of our report, so we should tailor accordingly.

**Exercises:**

**Something to report**

You need to present a report regarding your findings about customer churn and the predictive model you used, which you worked on in Chapter 1. Your project manager asks you to write it according to industry standards. You're aware that this requires you to follow a strict structure. Your manager also specifies that the report will be shared with technical stakeholders.

First, you write the sections separately: it's easier to handle that way. Then comes the time to bring all the sections together.

Can you organize the sections you wrote for the report in the correct order?

**Instruction:**

- Order the report sections so that the first section should be on top and the last at the bottom.

![image 16](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/8cd1a2b7-b507-40e8-afce-61af48563015)

**In summary**

Well done ordering the sections in your technical stakeholder report. Your project lead asks you to write a report to send to the directory board. They are non-technical stakeholders. You will revisit your previous report and tailor it as a summary report. But first, you want to refresh how a final report and a summary report differ.

Can you correctly classify the statements as characteristics of a final or summary report?

**Instruction:**

- Correctly classify the examples as a feature of either a final or summary report.

![Image 17](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/5773ed60-0b53-4393-9fec-01a13910edd5)

# Reproducibility and references

**Personal notes:**

### Reproducibility and References

*Written Report:*

A fundamental part of communicating our findings is ensuring that a report is clear and reproducible.

*Best Practices:*

- *Documentation:* Document all scripts used to obtain results, using comments in the code, and list all packages used in the environment. Version control systems like git can be useful for tracking changes and versions of scripts.
  
- *Avoid Manual Manipulation:* Avoid any manual data manipulation. Never directly edit the dataset in an editor. Save all versions of the dataset if possible. Save raw data along with a script with intermediate steps to create a clear narrative around data transformation.

- *Machine Learning Algorithms and Pipelines:* Use machine learning algorithms or pipelines in your workflow. Set a random seed to introduce reproducibility in model outputs. A random seed controls variable randomness, ensuring that a change is due to the model, not just randomness.

- *Interpretability:* Interpretability is crucial. A compelling narrative helps the audience understand and interpret findings. A clear story with a convincing narrative aids in reproducibility as the audience can comprehend and reproduce the conclusions.

- *Citations:* Properly cite the work of others used in the analysis. Citations provide essential information to identify and locate a specific publication. The APA style, which places the author's name first and the publication date next, is commonly used. Reference management tools like EndNote, Mendeley, and RefWorks help manage citations, change styles automatically, and search for sources online.

*In a Business Context:*

In a business context, reference citation rules are more relaxed. Many people simply include a hyperlink to the reference source. In this case, what matters is that the information is easily retrievable if the reader wants to consult the material from the sources.

**Exercises:**

**Replicate me**

Your manager asks you to write a report on your customer churn project for your peers at the New York office. She mentions that the team wants to replicate your work. After wrapping up the report, you add a link to your code repository. She looks confused and asks you why you did that.

You explain: If the New York team wants to replicate my work, then they should have access to the same ___ and the same ___ I used. However, if they want to achieve ___ , they can use their own set of tools.

Fill in the blank spaces by choosing the correct word combination from the options.

        "data, code, reproducibility"

**Same results**

Your manager is very interested in learning more about reproducibility. She asks you to give a short presentation at the weekly meeting. You're going to introduce the best practices to create reproducible data science results.

You prepare a slide presenting bad practices, and another one highlighting best practices.

Which of the following statements are considered best practices in reproducibility, and which should be avoided?

**Instruction:**

- Correctly classify the statements as best or bad practices.

![Image 18](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/a4527643-d122-4544-a2b6-3ae1d70d1185)

# Write precise and clear reports

**Personal notes:**

In data science, writing should be concise and precise to avoid misunderstandings and confusion. The target audience should understand our message, and there is no place for sentences that do not add information or introduce possible misunderstandings in our reports.

*Empty Phrases:*

Empty phrases distract and should be avoided. Be direct and get straight to the point. If a sentence doesn't add relevant information, remove it.

*Concrete Nouns:*

Effective technical writing is concise and direct. Use concrete nouns and avoid excessive use of pronouns like 'this' and 'that' to ensure clarity about what they refer to. Both active and passive voices have their critiques, with the active voice emphasizing the author over the facts and the passive voice being criticized for being too passive and challenging to read.

*Redundant Adjectives and Adverbs:*

In an attempt to emphasize an argument, it's easy to use redundant adjectives and adverbs. To keep the report concise, eliminate these unnecessary descriptors.

**Exercises:**

**Half-empty glass**

Your coworker, whom you helped with a project on price predictions in Chapter 2, asks you now to read his report. He wants your feedback as the report is designed for the executive team. Particularly, you should focus on fixing any empty or fat phrase, or colloquialism.

Can you help him identify improvable sentences, and suggest a better alternative?

**Instruction:**

- Correctly classify the examples as improvable or intelligible versions.

![Image 19](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/3c17ea43-6c55-4ab0-adbd-001151a7ed30)

**Strong words**

Your coworker is very satisfied with your feedback. He now asks you to look at another report he wrote for technical stakeholders. You noticed that the writing style is confusing and verbose. You decide to help him use more concrete nouns, and to fix redundant adjectives and run-on sentences.

Can you classify which of the following examples are intelligible, and which ones can be improved?

**Instruction:**

- Correctly classify the examples as either the correct or uncorrected version.

![Image 20](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/e002552b-2aa1-4519-a17d-f8e6c553dd09)

# Case study: report on credit risk

**Exercises:**

**Credit me**

You are about to leave the office when you get a call from the operation director. She tells you that you need to write a report on the credit score to present to the advisory board. She explains: "They want to understand your analysis to help plan a strategy to pre-select customers for loans".

Which of the following reports is the most suitable to write in this case?

       "An analytic report with boxplots displaying the relationship between loan and customer traits, and a barplot of most important predictors."

**Report my credit**

Your analytic report on the credit score project was a success. Your project manager was very satisfied with your work. Now, it's time to write the summary report for the financial department director. You want her to understand the key findings. Particularly, that the most important features for predicting a loan default are income, age, and employment length.

Can you put in order the sections of your summary report?

**Instruction:**

- Order the report sections so that the first section should be on top and the last at the bottom.

![Image 21](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/90634f40-1077-4e83-92a8-15c42ca2a125)

# Building Compelling Oral Presentations

**Chapter description:**

You'll finish by learning simple techniques to structure a presentation, communicate insights, and inspire your audience to take action. Lastly, you'll learn how to improve your communication style and prepare to handle questions from your audience.

# Planning an oral presentation

**Personal notes:**

To structure the presentation effectively, it's crucial to consider the purpose, the audience, and the message you want to convey.

*Purpose:*

Define the purpose of your presentation based on its type:
- *Informative Presentation:* Providing information on current negative and positive ratings and associated words.
- *Instructive Presentation:* Explaining how the analysis model was constructed.
- *Persuasive Presentation:* Convincing stakeholders to take actions to address high numbers of negative reviews.

*Audience:*

Consider your audience, whether they are technical colleagues, managers, executives, or clients. Also, think about the size of the audience, whether it's a small team meeting or a large conference.

*Message:*

Identify the key message you want your audience to remember. Craft a compelling opening statement, focus on a central message (preferably a single sentence), and end with a closing statement that reinforces the central message.

*Structure:*

Based on the purpose, audience, and message, structure your presentation. Start with an introduction, providing essential information to grab the audience's attention. Then, delve into methods, analysis, and model results, adjusting the level of technical detail based on the audience. Finally, conclude by revisiting the introduction and adding a call-to-action or recommendations for next steps.

*Outline:*

Create an outline with about five sections to maintain audience engagement:
1. *Reason for Analysis*
2. *Exploratory Analysis*
3. *Sentiment Analysis*
4. *Conclusion*
5. *Recommended Actions*

Consider the time available for the presentation, as it will influence the planning and pacing of the content delivery.

**Exercises:**

**Is this the plan?**

You need to present your findings on software development sector salaries for San Francisco employees and the predictive model you used, which you worked on in Chapter 2, to the executive team.

You open your computer and start drafting slides. But then, you recall the course you took on communicating with data. You feel that you are missing something. So you write down the facts you remember to build a compelling oral presentation.

Can you identify which of the following statements is correct?

**Instruction:**

- Correctly classify the statements as either true or false.

![Image 22](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/c3888b13-83c4-40fd-88fb-a19db4ef8684)

**An effective plan!**

Well done! You identified which statements were correct. Now, you know how to plan your slides on salaries for San Francisco employees. It's time to determine which sections you will include in your presentation.

Can you put in order the topics for the sections of your oral presentation?

**Instruction:**

- Order the presentation sections so that the first section should be on top and the last at the bottom.

![Image 23](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/1ece0d71-7131-4450-ad09-314b1583b138)

# Building presentation slides

**Personal notes:**

Creating effective slides is essential to support the narrative you're conveying. Consider your audience's attention span, aiming for dynamic presentations with concise content on each slide. Each slide should carry a single message to maintain clarity and engagement.

*Color:*

- Use a minimal color palette necessary to convey your message.
- Ensure good contrast between text and background for readability.
- Be mindful of colorblind individuals to avoid issues with color distinction.

*Fonts:*

- Choose fonts that enhance readability.
- Keep text short and use larger fonts.
- Limit font styles and sizes to convey the message without distraction.

*Text Slide:*

- Avoid excessive text; focus on key points.
- Include a concise and specific slide title to capture attention.
- Use bullet points or stratification to break down complex information.

*Visualization Slide:*

- Replace text-heavy slides with visuals like graphs or charts.
- Introduce visual elements sequentially to guide the audience through the information.
- Highlight specific aspects of visuals to emphasize key points.
- Use only one or two full-sized graphs per slide to avoid information overload.

Remember, slides are a support tool for your presentation, not standalone documents. Keep them visually appealing, concise, and aligned with your spoken words to enhance overall comprehension.

**Exercises:**

**A color building**

You have planned the presentation for your findings on software development sector salaries for San Francisco employees. Now, it's time to build the slides. After putting your slide deck together, you ask your coworker to give you feedback. She makes comments on the different slides.

You start by reviewing the following graph slide.

One of the comments she wrote about the slide is not correct. Can you select which one it is?

        "The headline looks stylish. Even though the spacing between the letters is small, the font adds originality to the slide."

**Too much text**

Your coworker also gives you feedback on slides that only have text. She feels like the slide can be improved a lot. She gives you some options on how you can improve the slide.

One of the following statements is not correct. Can you select which one is it?

       "Highlight the keywords in the text using red, green, yellow, blue, and magenta. Using several colors will help catch the audience's attention." 

**The right building**

Well done building a text slide! Now, you need to review the rest of the comments from your coworker. She left you the feedback in two stacks of notes: one stack for best practices and one stack for what you should avoid. However, the stacks fell during your lunch break and are all mixed up.

Can you classify which of the following comments are best practice in building a presentation, and which ones should be avoided?

**Instruction:**

- Correctly classify the comments as either best practices or practices to avoid.

![Image 24](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/b23ffa62-3869-4d04-9293-932da167dc07)

# Delivering the presentation

**Personal notes:**

*Practice:*

Practicing is crucial for a successful presentation. Draft a script, not to memorize it, but to guide an efficient articulation of thoughts and insights. Frequent practice helps you become more familiar with the content, identify distracting patterns, and refine your delivery. Anticipate and prepare responses for potential follow-up questions. Rehearse in a setup close to the presentation context, using real slides, speaking aloud, and addressing possible inquiries.

*Deliver the Presentation:*
1. *Emotional Awareness:*
   - Be conscious of your emotions as the audience can perceive them.
   - Confidence in your delivery builds trust in your content.

2. *Attention Span:*
   - Audience attention typically ranges from 5 to 20 minutes.
   - Employ strategies like eye contact, interactivity, and questions to engage the audience.
   - Speak with them, not at them, fostering a connection and empathy.

3. *Language and Tone:*
   - Choose language carefully, avoiding phrases that may alienate or confuse.
   - Refrain from phrases like "As we know" or "obviously" to maintain a connection.

4. *Timing:*
   - Stay within the allotted presentation time to respect the audience's schedule.
   - Incorporate pauses to allow the audience time to process information.

5. *Q&A Session:*
   - Encourage questions during or at the end of the presentation.
   - Being open to feedback and questions shows engagement and a willingness to help the audience understand the message.

Remember, effective communication is not just about delivering information; it's about building a connection with your audience. Stay authentic, engage your audience, and be responsive to their needs and inquiries.

**Exercises:**

**Put it into practice**

Excellent job creating those slides for the project on software development sector salaries for San Francisco employees!

Now that you have your slide deck ready, it's time to deliver your presentation. Your project manager sends you an email. She asks you if you can have the meeting at the end of the afternoon. You are unsure because you need to practice. So you ask for some time for rehearsal. To convince your manager, you make a list of the advantages of practicing and rehearsing a presentation.

Can you decide which examples you wrote are correct and which ones are incorrect?

**Instruction:**

- Correctly classify the statements as either true or false.

![Image 25](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/890356c2-ebcd-47fc-b1e1-6279931fdd56)

**Best practice**

Your rehearsal went very well! You are ready to present to the stakeholders.

However, you feel nervous. You know this is completely normal but you don't want to look like you are unsure of your content. You take three big breaths and remember your training. There are some key points that will help you deliver the presentation effectively.

Can you identify which of these statements are suitable points to consider, and which ones are not?

**Instruction:**

- Correctly classify the following examples as either a true or false.

![Image 26](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/89c6022b-e3e5-40e1-8a2c-6f3d12506b0f)

# Avoiding common errors

**Personal notes:**

*Length:*

- Many presentations suffer from ineffectiveness due to excessive length. Consider the audience's attention span, and exceeding 20 minutes poses the risk of losing their engagement. Allocate time for potential audience questions.

*Purpose:*

- Forgetting to clearly state the presentation's objective in the introduction is a common error. This oversight can hinder the audience's understanding of the findings, diminishing the impact of the story.

*Guide Audience:*

- As speakers, guide the audience by delivering a sequence of information that supports the story and keeps their attention. Instead of saving all findings for the end, integrate them throughout, providing a backbone for the message.

*Audience Involvement:*

- Avoid presenting as a monologue; involve the audience. Begin with a strong introduction, stating who you are and why you're presenting. Clearly declare main assumptions to show empathy. Engage the audience with questions, relate content to the main idea, and maintain their involvement.

*Body Language:*

- The speaker is central to the presentation, so leverage body language for emphasis. Use natural gestures, hand movements, or facial expressions to create emphasis. Positive body language conveys confidence and enhances audience focus.

*Voice Tonality:*

- Utilize voice as a tool. Vary tones to emphasize the message; speak quickly for urgency or excitement, and slowly for significance. Pay attention to intonation; sound engaged and interested, as a lack of enthusiasm can disengage the audience.

Remember, effective presentations require a balance between content, delivery, and audience engagement. Be mindful of these common errors to enhance the impact of your message.

**Exercises:**

**The true mistake**

Your coworker asks you to help him practice for his presentation. He wants your feedback so he can be prepared to deliver an important project to the company's CEO.

He gives you a list of best practices he should observe during his speech. But you notice that some of them are not correct.

Can you identify which statements are wrong?

**Instruction:**

- Correctly classify the statements as either true or false.

![Image 27](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/bfc90d72-1986-4b60-af80-937789251e1c)

**Do's and don'ts**

It's the day before the presentation for your project on customer churn. Your team lead arrives and tells you that the CEO will be there to listen to your results. You start getting nervous.

You have planned your presentation. You built the slides focusing on a non-tech audience. You have practiced and rehearsed with some colleagues. But you really want to avoid making any common mistakes during your talk. So you decide to practice one more time.

To achieve your goal, you need to remember best practices so you can implement them. Also, you should make a list of common errors so you can avoid them.

**Instruction:**

- Correctly classify the examples as either a best practice or a common mistake.

![Image 28](https://github.com/Caiobauab360/Data_Analyst_With_SQL_Course_Portfolio/assets/127256295/74d5f59a-befa-4d6a-b7b5-515f1467a46f)