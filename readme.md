# We Rate Desserts

## Overview
We will be building a website where users can add their name and upload desserts with dessert reviews.

Your teacher will share credentials for MongoDB so we will all be working with the same data.

## Your Goals
You will be able to practice
- Writing Flask Routes
- Processing Forms
- Inserting to a Database
- Querying a Database
- Incorporate Bootstrap Components
- Style with Bootstrap Classes
- Write custom CSS

## To-Do
1. Add yourself as a user
2. Add a dessert
3. Add a review for the dessert
4. Add HTML to the pages to display the information
5. Use CSS and Bootstrap to style the information
6. Write additional routes (and functions in model.py) to add functionality below

## How to: Write a Flask Route
When writing a new flask route, consider these steps
1. Come up with a descriptive function to define - `def function_name()`
2. Include the route decorate - `@app.route('/route_name')`
3. If you are writing a route to accept a POST request from a form, include `methods=['GET','POST']`
4. If necessary, gather info from the user -- process a form, read from a `session`, do a database lookup
5. If necessary, send that info to a function from your `model.py` to do your businss logic
6. Package up the data needed for your `render_template` in a `data={}`
7. Include a `return` statement with a `render_template('templateName.html', data=data)`

### Note
> The routes already written should remain as written. Especially the routes that handle adding the form data to the documents that are inserted into the database. This is to ensure compatibility across the class projects

## Things to Include
- Filter by Dessert Category
- Filter by Dessert Rating
- Filter by User
- Calculate average rating for a dessert
- Calculate the [Net Promotor](https://en.wikipedia.org/wiki/Net_Promoter) score for a dessert
- And anything else

## Additional Flask Features Included
- `url_for()` - This function takes at least one argument and any number of keyword arguments. The first argument is a string that matches the name of a route function (the function name, not the route decorator). The additional keyword arguments can be used to pass information that is a route parameter. Using url_for is a best practice when creating links within your flask_app to other routes of your flask_app
```html
<a href="{{url_for('users_detail', USER=user.name)}}">Details</a>
```
- `<route_parameter>` - You can get information from the url of the route by putting the parameter within <> inside the route decorator. The parameter must also be in the () in the function definition.
```python
@app.route('/users/<USER>')
def users_detail(USER):
    #business logic
```
- `redirect` - Sometimes you want to have in the control flow of a one route sending the user to another route. Not just render the template used in that route but actually force their web browser to make a `GET` request of the other route. To do this, you use the `redirect` function (make sure you `from flask import redirect` in your `app.py`). This a great feature to handle a user going to a route and not providing enough information OR it's a way to follow the [Post/Redirect/Get](https://en.wikipedia.org/wiki/Post/Redirect/Get) pattern of modern web design. There's an example of the Post/Redirect/Get in this app when a user submits a new dessert or a new review.
```python
@app.route('/users/<USER>')
def users_detail(USER):
    #business logic
```
- `control flow in templates` - inside of Flask templates you can include control flow like `for` loops and `if` statements. To do this, you use {% <controlflow> %} and need to include end statements. Here's some examples
```python
{% for dessert in data.desserts %}
    #business logic
{% endfor %}
```
```python
{% if dessert.category == 'pie'%}
    #business logic
{% else %}
    #business logic
{% endif %}
```
