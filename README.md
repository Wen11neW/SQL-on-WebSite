# SQL-on-WebSite
Это очень поверхностное упражнение по sql бд на сайте на python с помощью flask!!!
This is very superficial exercise on sql database on a website in python using flask!!!

Все задания будут в main.py / All tasks will be in main.py
Сначала скачаем все зависимости. (ПРЕДУПРЕЖДЕНИЕ! ЭТОТ ГАЙД УЧИТЫВАЕТ, ЧТО У ВАС УЖЕ ЕСТЬ VS CODE, УСТАНОВЛЕННЫЙ PYTHON С 3 ВЕРСИИ И НАСТРОЕННЫЙ VS CODE) Скачиваем расширение для visual studio code "SQLite3 Editor", теперь скачиваем библеотеки flask и flask_sqlalchemy коммандами в консоли pip install flask и аналагично pip install flask_sqlalchemy 

First, let's download all the dependencies. (WARNING! THIS GUIDE CONSIDERS THAT YOU ALREADY HAVE VS CODE, INSTALLED PYTHON FROM VERSION 3 AND CONFIGURED VS CODE) Download the extension for visual studio code "SQLite3 Editor", now download the flask and flask_sqlalchemy libraries using the commands in the console pip install flask and similarly pip install flask_sqlalchemy

Теперь можно приступать. / Now you can get started.
В 1 задании нужно создать таблицу БД (позже ты поймешь зачем все это делать) (как собственно и написано, в других заданиях так же), создай класс Card ( class Card(db.Model): ) и в классе создай 4 переменные (столбцы) - id, title, subtitle, text. Например: title = db.Column(db.String(100), nullable=False) На нем ты можешь увидеть, что функция db.Column создает столбец, db.String(100) указывает тип данных строчка и ставит ограничение в 100 символов, а nullable=False дает настройки, что поле не должно быть пустым. Теперь нужно сделать еще переменные которые уже были перечислены, вот что нужно для отдельных переменых:

id - должен иметь тип данных Integer, а настройки  primary_key=True
title (указано в примере выше) и subtitle - должны быть строчкой и иметь ограничение, а настройки должны обозначать отсутствие возможности оставить поле пустым
text - должен быть типом данных Text и иметь такие же настройки как title, но не иметь ограничения в символах.

In task 1 you need to create a database table (later you will understand why all this is done) (as it is actually written, in other tasks it is the same), create a class Card ( class Card(db.Model):) and in the class create 4 variables (columns ) - id, title, subtitle, text. For example: title = db.Column(db.String(100), nullable=False) Here you can see that the db.Column function creates a column, db.String(100) indicates the data type is string and sets a limit of 100 characters, and nullable=False gives settings that the field should not be empty. Now we need to make more variables that have already been listed, here is what is needed for individual variables:

id - must have an Integer data type, and settings primary_key=True
title (indicated in the example above) and subtitle - should be a line and have a limitation, and the settings should indicate that it is not possible to leave the field empty
text - must be a Text data type and have the same settings as title, but not have a character limit.

Теперь в том же классе нужно прописать функцию для вывода объектов по id  /  Now in the same class you need to write a function to display objects by id:
def __repr__(self):
            return f'<Card {self.id}>'

Теперь сделай то, зачем мы все это писали! (ВНИМАНИЕ!!! НУЖНО ОТКРЫТЬ ПАПКУ С main.py В VS CODE БЕЗ ДОПОЛНИТЕЛЬНЫХ ПАПОК (кроме моих в проекте), ЧТОБЫ НЕ БЫЛО ОШИБОК!!!)запускай скрипт в косноли в vs code, нажимай сочетании клавиш Ctrl + C, введи в консоль python -> from main import app, db -> app.app_context().push() -> db.create_all()  (вообщем 3 команды), после этого у тебя должна появиться папка instance с файлом diary.db (это и есть наша база)

Now do what we wrote all this for! (ATTENTION!!! YOU NEED TO OPEN THE FOLDER WITH main.py IN VS CODE WITHOUT ADDITIONAL FOLDERS (except mine in the project), SO THAT THERE ARE NO ERRORS!!!) run the script in Kosnoll in vs code, press the key combination Ctrl + C, enter in python console -> from main import app, db -> app.app_context().push() -> db.create_all() (generally 3 commands), after that you should have an instance folder with the diary.db file (this is there is our base)

В задании 2 нужно будет добавить сохранение данных в нашу БД через сам сайт. Найди комментарий с меткой Шаг 1 и добавь туда эти 3 строки кода с нашими данными:

In task 2 you will need to add data storage to our database through the site itself. Find the comment labeled Step 1 and add these 3 lines of code with our data there:

card = Card(title=title, subtitle=subtitle, text=text)
db.session.add(card)
db.session.commit()

Во 2-ом шаге нужно отобразить объекты из БД в index.html этой строчкой   /   In the 2nd step you need to display objects from the database in index.html with this line:

Card.query.order_by(Card.id).all()

(НЕ ЗАБУДЬ ОТКОММЕНТИРОВАТЬ СТРОЧКУ cards=cards)   /   (DO NOT FORGET TO UNCOMMENT OUT THE LINE cards=cards)

В 3-ем шаге нужно отобразить нужную карточку по id   /   In the 3rd step you need to display the desired card by id:

Card.query.get(id)

(И не забудь заглянуть в базу данных с помощью SQLite3 Editor. Ты можешь добавлять, изменять и удалять записи прямо здесь, и все изменения сразу же отобразятся на сайте. Главное не забывай нажимать кнопку "Подтвердить")

(And don’t forget to look into the database using SQLite3 Editor. You can add, change and delete records right here, and all changes will immediately appear on the site. Just don’t forget to click the “Confirm” button)

Вот и все! Это было очееееень поверхностно, если хочешь нормально изучить эту тему почитай документацию, потому что я очень плохой учитель, надеюсь ты выбрал правильный путь в освоении этой профессии, да и мне только учиться. удачи!

That's all! This was very superficial, if you want to study this topic properly, read the documentation, because I am a very bad teacher, I hope you chose the right path in mastering this profession, and I just have to learn. Good luck!
