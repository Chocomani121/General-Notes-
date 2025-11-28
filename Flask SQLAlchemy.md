# SQLAlchemy V.2.0.44 Commands CMD 
- CMD database
- Set up: import module through cmd/powershell
- pip install flask-sqlalchemy
- Import SQLAlchemy to flask

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

