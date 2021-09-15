
●  	What did you like about this project?
It is more like an exercise rather than an assessment.

●  	What did you struggle with in this project?
Understanding the questions especially question 4

●  	What would make your experience with this assessment better?
I am glad to experience another variation of the assessment.

-----------------------------------------------------------------------------------------------------------------------

2a) What are the Top 25 schools (.edu domains)?

SELECT email_domain AS Top_25_Schools, COUNT(*)
FROM users
GROUP by 1
ORDER by 2 DESC
LIMIT 25;


2b) How many .edu learners are located in New York?

SELECT COUNT(*) AS "New York Learners"
FROM users
WHERE city ="New York" and email_domain LIKE "%.edu";


2c)The mobile_app column contains either mobile-user or NULL. How many of these Codecademy learners are using the mobile app?

SELECT COUNT(*) AS Mobile_App_User
FROM users 
WHERE mobile_app = "mobile-user";


3) Query for the sign up counts for each hour.

SELECT strftime('%H', sign_up_at) AS Specific_Hour, 
COUNT(*) AS Total_Signups
FROM users
GROUP BY 1


4a) Do different schools (.edu domains) prefer different courses?

SELECT users.email_domain AS Different_Schools, COUNT(*) AS Entries,
progress.learn_cpp,
progress.learn_sql,
progress.learn_html,
progress.learn_javascript,
progress.learn_java
FROM users
JOIN progress
ON users.user_id = progress.user_id
Group by 1;


4b) What courses are the New Yorkers students taking?

SELECT progress.user_id AS Student_ID, 
users.city, 
progress.learn_cpp, 
progress.learn_sql, 
progress.learn_html, 
progress.learn_javascript, progress.learn_java
FROM users
JOIN progress
ON users.user_id = progress.user_id 
WHERE city = "New York";


4c) What courses are the Chicago students taking?

SELECT progress.user_id AS Student_ID, 
users.city, 
progress.learn_cpp, 
progress.learn_sql, 
progress.learn_html, 
progress.learn_javascript, 
progress.learn_java
FROM users
JOIN progress
ON users.user_id = progress.user_id 
WHERE city = "Chicago";

