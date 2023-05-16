# Custom_API_Based_Website
Build a custom website using an API that you find interesting.
Let's build a custom website using the SpaceX API. The SpaceX API provides information about SpaceX's rocket launches, rockets, capsules, and more. We'll use Python along with the Flask framework to create a simple website that displays information about the latest SpaceX launch.

Here's a step-by-step guide to building the website:

Step 1: Install Flask
---------------------
Make sure you have Flask installed. You can install it using pip:

```
pip install flask
```

Step 2: Create a new Flask app
------------------------------
Create a new Python file, let's call it `app.py`, and add the following code:

```python
from flask import Flask, render_template
import requests

app = Flask(__name__)

@app.route('/')
def index():
    response = requests.get('https://api.spacexdata.com/v4/launches/latest')
    data = response.json()
    return render_template('index.html', data=data)

if __name__ == '__main__':
    app.run(debug=True)
```

Step 3: Create the HTML template
-------------------------------
Create a new folder called `templates` and within it, create a file called `index.html`. Add the following code to the `index.html` file:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Latest SpaceX Launch</title>
</head>
<body>
    <h1>Latest SpaceX Launch</h1>
    <h2>Mission Name: {{ data['name'] }}</h2>
    <h3>Details: {{ data['details'] }}</h3>
    <h3>Launch Date: {{ data['date_utc'] }}</h3>
    <h3>Launch Success: {% if data['success'] %}Yes{% else %}No{% endif %}</h3>
</body>
</html>
```

Step 4: Run the Flask app
-------------------------
Save all the changes, and from the command line, navigate to the directory containing `app.py`. Run the following command to start the Flask app:

```
python app.py
```

You should see output similar to the following:

```
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```

Now, open your web browser and go to `http://127.0.0.1:5000/`. You should see the latest SpaceX launch information displayed on the webpage.

That's it! You have built a custom website that retrieves data from the SpaceX API using Python and Flask. You can further enhance the website by adding more information or incorporating additional API endpoints.