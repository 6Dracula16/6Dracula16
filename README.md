DJANGO - library
Flask
Piramid
from flask import Flask, render_template, request
app = Flask(__name__)

favorite_songs = [
    "Song 1",
    "Song 2",
    "Song 3"
]

@app.route('/')
def index():
    return render_template('index.html', songs=favorite_songs)

@app.route('/auth', methods=['GET', 'POST'])
def auth():
    if request.method == 'POST':
        username = request.form['username']
        return render_template('auth.html', username=username)
    return render_template('auth.html')

@app.route('/table')
def table():
    return render_template('table.html')

@app.route('/image')
def image():
    return render_template('image.html')

@app.route('/text')
def text():
    variable_text = "Это текст, переданный через переменную."
    return render_template('text.html', text=variable_text)

if __name__ == '__main__':
    app.run()



HTML
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Главная страница</title>
</head>
<body>
    <h1>Добро пожаловать на главную страницу!</h1>
    <h2>Ваши любимые песни:</h2>
    <ul>
        {% for song in songs %}
            <li>{{ song }}</li>
        {% endfor %}
    </ul>
</body>
</html>

<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <title>Авторизация</title>
</head>
<body class="container">
    <h1>Авторизация</h1>
    <form method="POST">
        <div class="form-group">
            <label for="username">Имя пользователя:</label>
            <input type="text" id="username" name="username" class="form-control" required>
        </div>
        <button type="submit" class="btn btn-primary">Отправить</button>
    </form>

    {% if username %}
        <h2>Вы ввели: {{ username }}</h2>
    {% endif %}
</body>
</html>

PYTHON

from flask import Flask, render_template, request
app = Flask(__name__)

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        username = request.form['username']
        password = request.form['password']
        return 'You are logged in! ' + username + '   ' +  password
    else:
        return render_template('form.html')

if __name__=='__main__':
    app.run()
