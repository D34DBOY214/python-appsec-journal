# 2025-07-26 First SQL Injection Lab

 The lab asked me to perform a SQL injection attack to cause the application to display one or more unreleased products.
 I clicked a product category and added `'+OR+1=1--` to the end of the URL parameter.
 The application ignored its normal filtering rules, forced a true condition, and unlocked all products including unreleased ones, solving the lab.
- I am still a bit unsure how the database handles the comment characters (`--`) to safely ignore the rest of the original query.
