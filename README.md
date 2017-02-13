# Homework #3

## Instructions
---
1. Create a project folder.  Setup your virtual environment.  Install `flask`.

2. Create a `/templates` folder in your project directory with the following `html` templates.
	
    *home.html*
    ```
    <!DOCTYPE html>
    <img src="https://lambdaschool.com/static/assets/images/lambda.png">
    <h1>Food Database</h1>
    <form action="{{ url_for('search') }}" method="GET">
        <h3>Search</h3>
        <input type="text" name="name" />
        <input type="submit" />
    </form>
    <h3><a href="/enternew">Add Food</a></h3>
    <h3><a href="/list">Show Foods</a></h3>
    <h3><a href="/favorite">Favorite Food</a></h3>
    <br>
    <br>
    <br>
    <h3>Apply now for a chance to attend one of our immersive programs beginning in April 2017.</h3>
    <p>Our immersive programs combine small class sizes, world class instructors, a curriculum comprised of cutting edge technologies, and career counseling to help you begin a successful career as a software engineer.  All at a fraction of the cost of a traditional Computer Science degree.</p>
    <h4>Our curriculum includes:</h4>
    <ul>
      <li>Computer science fundamentals including data structures, algorithms, complexity analysis, an intro to data science, and more</li>
      <li>Front-end web development using HTML, CSS/SASS, React, Redux, client testing, and more  </li>
      <li>Back-end development including Node/Express, MySQL, MongoDB, Redis, auth/security, devops, server testing, and more </li>
      <li>An introduction to mobile development using React Native</li>
      <li>Agile development</li>
      <li>Interviewing strategies, resume writing, and how to leverage social media and other online resources to help you find the right job</li>
      <li>Long-term career strategies and how to position yourself to not just find a job but to create a successful and lucrative career as a software engineer</li>
    </ul>

    ```
    *food.html*
    ```
    <form action = "{{ url_for('addrecord') }}" method = "POST">
      <h3>Food Info</h3>
      Name<br>
      <input type = "text" name = "name" /></br>
      Calories<br>
      <textarea name = "calories" ></textarea><br>
      Cuisine<br>
      <input type = "text" name = "cuisine" /><br>
      Vegetarian<br>
      <input type = "text" name = "is_vegetarian" /><br>
      Gluten Free<br>
      <input type = "text" name = "is_gluten_free" /><br>
      <input type = "submit" value = "submit" /><br>
	</form>
    ```
    
    *list.html*
    ```
    <table border = 1>
      <thead>
        <td>Name</td>
        <td>Calories</td>
        <td>Cuisine</td>
        <td>Vegetarian</td>
        <td>Gluten Free</td>
      </thead>

      {% for row in rows %}
      <tr>
        <td>{{row["name"]}}</td>
        <td>{{row["calories"]}}</td>
        <td>{{row['cuisine']}}</td>
        <td>{{row['is_vegetarian']}}</td>
        <td>{{row['is_gluten_free']}}</td>
      </tr>
      {% endfor %}
	</table>

	<a href = "/">Home</a>
	```
    
    *result.html*
    ```
    <h1>result of addition : {{ message }}</h1>
	<h2><a href = "/">go back to home page</a></h2>
	<h2><a href = "/list">See Food List</a></h2>
    ```

3. Initialize your database.  Create a file called `initdb.py`.  Copy the contents shown below into `initdb.py`.  Run `initdb.py` with this command: `Python initdb.py`.  After running this script a file called `database.db` is created.  This is your `SQLite3` database.  `SQLite3` reads and writes to a single static file without needing a separate database server running locally.

	*initdb.py*
    ```
    import sqlite3

    connection = sqlite3.connect('database.db')
    print 'Opened database successfully';

    connection.execute('CREATE TABLE foods (name TEXT, calories TEXT, cuisine TEXT, is_vegetarian TEXT, is_gluten_free TEXT)')
    print 'Table created successfully';
    
    connection.close()
	```

4. Create your server file, import the needed dependencies, and create the home route (`/`).  This route should render the `home.html` template.  Start your server and go to `localhost:5000/`.

Your file structure should now look like this:
```
 project-name/
 --server.py (or whatever you named your python script)
 --initdb.py
 --database.db
 --templates/
 ---- home.html
 ---- food.html
 ---- list.html
 ---- result.html
 --venv/
```
    
5. Implement the `/enternew` route.  This route should simply render `food.html`.


6. Implement the `/addfood` route.  This route should accept a `POST` request.  This route should accept the form data sent from the `food.html` template and `INSERT` it into the database.  Use the lecture code as a reference.
	

7. Implement
