##Setup

#install

1 Creat json file
npm init -y

2 Install necessary packages.
npm install express mysql2 express-session ejs multer bcrypt

#SQL
Creat database

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
