# Setup
Follow these steps to set up and run the project locally.

## install

1 Creat json file

```
npm init -y
```

---

2  Install Dependencies
Install the necessary packages to get the project running:

```
npm install express mysql2 express-session ejs multer bcrypt
```

Express: Web framework for building the server.

MySQL2: Library for connecting to MySQL database.

Express-session: Middleware for managing user sessions.

EJS: Templating engine to render HTML views.

Multer: Middleware for handling file uploads.

Bcrypt: Library for password hashing.


---

3 SQL
Creat database

```
CREATE TABLE users (
  id int NOT NULL AUTO_INCREMENT,
  username varchar(50) NOT NULL,
  password varchar(255) NOT NULL,
  PRIMARY KEY (id),
  UNIQUE KEY username (username)
);

CREATE TABLE places (
  id int NOT NULL AUTO_INCREMENT,
  name varchar(255) NOT NULL,
  description text,
  image1 mediumblob,
  image2 mediumblob,
  image3 mediumblob,
  image4 mediumblob,
  PRIMARY KEY (id)
) ;

CREATE TABLE reviews (
  id int NOT NULL AUTO_INCREMENT,
  place_id int NOT NULL,
  user_id int NOT NULL,
  text text NOT NULL,
  created_at timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  image longblob,
  PRIMARY KEY (id),
  KEY place_id (place_id),
  KEY user_id (user_id),
  CONSTRAINT reviews_ibfk_1 FOREIGN KEY (place_id) REFERENCES places (id),
  CONSTRAINT reviews_ibfk_2 FOREIGN KEY (user_id) REFERENCES users (id)
);
```
---

> [!IMPORTANT]
> Don't forget to change your password to be the same as your MySQL.
