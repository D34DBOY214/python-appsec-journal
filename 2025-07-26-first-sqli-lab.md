 # First SQL Injection Lab — PortSwigger

  **Date:** 2025-07-26
  **Type:** Lab
  **Lab:** SQL injection vulnerability in WHERE clause allowing retrieval of hidden
  data

  ## What the lab asked

  The shop page shows products filtered by category, like:

  ```text
  /filter?category=Gifts

  Some products are marked as unreleased. The goal was to display all products,    
  including unreleased ones.

  Why the app is vulnerable

  The application takes the category value from the URL and pastes it directly into
  a SQL query. It does not use a parameter or prepared statement.

  Likely original query:

  SELECT * FROM products WHERE category = 'Gifts' AND released = 1

  Because the category value is inserted directly, I can change the query logic by 
  sending special characters.

  The payload I used

  /filter?category='+OR+1=1--

  Decoded, that becomes:

  ' OR 1=1--

  What it does:

  - The first ' closes the string around the original category value.
  - OR 1=1 adds a condition that is always true.
  - -- turns the rest of the query into a SQL comment, so the original AND released
  = 1 check is ignored.

  The final query becomes:

  SELECT * FROM products WHERE category = '' OR 1=1--' AND released = 1

  The result

  The server returned all products, including unreleased ones, because the OR 1=1  
  condition made the WHERE clause always true.

  Why this is a real problem

  If an application builds SQL by putting user input straight into the string, the 
  database cannot tell the difference between data and commands. Anything the      
  attacker types becomes part of the query.

  The secure fix

  Use a parameterized query so the input is treated only as data, never as SQL     
  code:

  cursor.execute(
      "SELECT * FROM products WHERE category = ? AND released = 1",
      (category,)
  )

  The ? placeholder keeps the category value separate from the query structure.    

  What I still don't understand

  - What happens if the app uses double quotes around the input instead of single  
  quotes?
  - Can this same payload work in NoSQL or other databases?
  - How do tools like SQLMap detect this automatically?
