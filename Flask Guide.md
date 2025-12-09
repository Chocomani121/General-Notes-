# - SQLAlchemy V.2.0.44 - 
- CMD database
- Set up: import module through cmd/powershell
- pip install flask-sqlalchemy
- Import SQLAlchemy to flask
```
Package           Version
----------------- -------
aiofiles          25.1.0
bcrypt            5.0.0
blinker           1.9.0
click             8.3.1
colorama          0.4.6
dict-toolbox      5.0.0
dnspython         2.8.0
email-validator   2.3.0
Flask             3.1.2
Flask-Admin       2.0.2
Flask-Bcrypt      1.0.1
Flask-SQLAlchemy  3.1.1
Flask-WTF         1.2.2
greenlet          3.2.4
idna              3.11
itsdangerous      2.2.0
Jinja2            3.1.6
lazy-object-proxy 1.12.0
MarkupSafe        3.0.3
msgpack           1.1.2
nest-asyncio      1.6.0
pip               25.3
pop               27.1.0
pop-config        12.0.4
pop-loop          1.1.0
PyYAML            6.0.3
rend              7.0.2
sniffio           1.3.1
SQLAlchemy        2.0.44
toml              0.10.2
typing_extensions 4.15.0
Werkzeug          3.1.3
WTForms           3.2.1

```
# Updated Package Structure 

```
Database Creation
1.Create > create_db.py
2.Inside create_db.py "folder"

CMD
> python
> from models import app, db, User //* to load Python REPL into your memory. *//
or
> updated file package structure
>>> from app import app, db
>>> with app.app_context():
...     db.create_all()
...
from run import app
from app import models
from app.models import User

with app.app_context():
    u = User.query.get(1)
    print(u.id, u.username, u.email)



# Create all database tables within the Flask app context
with app.app_context():
    db.create_all()
    print("✔ Database created successfully!")

token from itsdangerous import URLSafeTimedSerializer as Serializer - for password

#Post
>>> with app.app_context():
...     posts = Post.query.all()
...     for p in post:
...             print(p.id, p.title, p.date_posted)


# CMD
 > python
 > db.create_all()
 -- folder name would appear ("site.db)
 > from flaskblog import User, Post
 -- this is to import user and post 
```
# Commands
 - Adding User, using cmd
```
from app import app, db, User
with app.app_context():
    new_user = User(username='Corey', email='C@demo.com', password='password')
    db.session.add(new_user)
    db.session.commit()

    users = User.query.all()
    print(users)
```
- Insert more Users
```
with app.app_context():
    user2 = User(username='Alice', email='alice@example.com', password='test123')
    user3 = User(username='Bob', email='bob@example.com', password='hello')
    db.session.add_all([user2, user3])
    db.session.commit()

    print(User.query.all())
```
- Select User by ID
```
with app.app_context():
    user = User.query.get(1)   # get user with id = 1
    print(user.id, user.username, user.email)
```
- Query Users
```
with app.app_context():
    user = User.query.filter_by(username='Corey').first()
    print(user)
```
- See User details
```
with app.app_context():
    for u in User.query.all():
        print(u.id, u.username, u.email)
```
- Delete User
```
with app.app_context():
    user = User.query.filter_by(username='Corey').first()
    db.session.delete(user)
    db.session.commit()
```
- Fix hashing (if password is not hased yet)
```
from werkzeug.security import generate_password_hash

hashed = generate_password_hash("password123")
```
#
POST Commands
- See all Post
```
with app.app_context():
    posts = Post.query.all()
    print(posts)
```
- Print Post Details
```
with app.app_context():
    for p in Post.query.all():
        print(p.id, p.title, p.content, p.author.username)
```
- Get Post
```
with app.app_context():
    user = User.query.get(1)
    for p in user.posts:
        print(p.id, p.title)
```
- Create New Post
```
with app.app_context():
    post = Post(title="Hello", content="My first post", user_id=1)
    db.session.add(post)
    db.session.commit()
```
- Get Specific User Post *Note - print inside the loop must be indented by 4 spaces, not 1.
```
with app.app_context():
    user = User.query.get(1)
    print("User:", user.username)

    for p in user.posts:
        print("Post:", p.id, p.title)

```

