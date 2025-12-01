# pip install flask-bcrypt
# Applying hash password CMD
 - from flask_bcrypt import Bcrypt
>>> bcrypt = Bcrypt()
>>> bcrypt.generate_password_hash('testing')
b'$2b$12$Celzg3dScyOuH36i57VuEu4/xY/W3nRY5tRXL2cgFpucwyTSaBjJm'
>>> bcrypt.generate_password_hash('testing').decode('utf-8') 
'$2b$12$SBI91hZLrixwa/8OgwM3uutO5rboiJUKlACSY6CuSHnKEllRhs2Jm'
>>> bcrypt.generate_password_hash('testing').decode('utf-8')
'$2b$12$rF0te92wx.WKA/2351FkWu6VQTITIkPh4KZXM2.d.GOA8cjIRwZZG'
>>> hased_pw = bcrypt.generate_password_hash('testing').decode('utf-8')
>>> bcrypt.check_password_hashed(hashed_pw, 'password') 

>>> bcrypt.check_password_hash(hased_pw, 'password')  
False
>>> bcrypt.check_password_hash(hased_pw, 'testing')  
True
