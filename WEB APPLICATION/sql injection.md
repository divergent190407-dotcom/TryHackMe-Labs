## sql basic
- It has a database, like we usually have servers where data is stored.
1. Get all users : 
- select * from users; 
- * means all; users is a column after the whole thing
2. From a specific user
- select * from users where username = 'alice';
- <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e470ced7-346f-450d-b07c-f901a5ff9907" />
- where it is the intersation ofboth: 
- select * from users where username='admin' and password='p4ssword';
- where username starts with a:
- select * from users where username like 'a%';
- username ends with n:
- select * from users where username like '%n';
- contains mi within them:
- select * from users where username like '%mi%';
- union:
- SELECT name,address,city,postcode from customers UNION SELECT company,address,city,postcode from suppliers;
- to insert:
- insert into users (username,password) values ('bob','password123');
- to update:
- update users SET username='root',password='pass123' where username='admin';
- to delete:
- delete from users where username='martin';
## types
- in-band:
- In-Band Injection is the easiest type to detect and exploit; In-Band just refers to the same method of communication being used to exploit the vulnerability and also receive the results, for example, discovering an Injection vulnerability on a website page and then being able to extract data from the database to the same page.
- error based:
- This type of Injection is the most useful for easily obtaining information about the database structure, as error messages from the database are printed directly to the browser screen. This can often be used to enumerate a whole database.
- union based:
- This type of Injection utilises the UNION operator alongside a SELECT statement to return additional results to the page. This method is the most common way of extracting large amounts of data via an Injection vulnerability.
- 
### how login works
- enter your credentials, then build an SQL query, then send a request to the database, then match found or not found.
- SELECT * FROM users WHERE username = 'alice' AND password = 'pass1234';
- AND is a true condition; if both statements are true then the result will be true. 
- for hacker : - SELECT * FROM users WHERE username = 'alice'-- AND password = 'anything';
- -- is to make the later part a comment
- - SELECT * FROM users WHERE username = 'alice' or 1=1 --;
- or condition is that if one is true and another one is false, it results into true.
## SQL Injection
- When you can manipulate the SQL queries that the web application sends to its database.
- The consequences can be severe: unauthorised access to sensitive data, bypassed authentication, modified or deleted records, and in some cases, full control of the database server itself.
## SQL injection using the URL
- https;//site.com/product?id=5'
- id=5 is a parameter here.
- The ' sign is to make a change, maybe an error or any change. After adding, if such changes are observed, then SQL injection is possible on that page.
  ### payloads
## tool
- sqlmap on kali
