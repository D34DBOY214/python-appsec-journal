  # First SQL Injection Lab — PortSwigger
                                                                                                                                                                                                             **Date:** 2025-07-26
  **Type:** Lab
  **Lab:** SQL injection vulnerability in WHERE clause allowing retrieval of hidden data
                                                                                                                                                                                                             ## What the lab asked

  The shop page shows products filtered by category, like:

  ```text
  /filter?category=Gifts
  
  Some products are marked as unreleased. The goal was to display all products, including unreleased ones.

  Why the app is vulnerable

  The application takes the category value from the URL and pastes it directly into a SQL query. It does not use a parameter or prepared statement.

  Likely original query:

  SELECT * FROM products WHERE category = 'Gifts' AND released = 1

  Because the category value is inserted directly, I can change the query logic bysending special characters.

  The payload I used

  /filter?category='+OR+1=1--

  Decoded, that becomes:

  ' OR 1=1--
