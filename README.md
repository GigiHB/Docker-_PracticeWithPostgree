This repository contains a simple setup using **Docker Compose** to run a PostgreSQL database and pgAdmin (a web interface for managing PostgreSQL).  
Beginner exercise to practice Docker commands, manage logs, connect to a database, and stop everything cleanly.

# 1. Start the containers in detached mode
docker compose up -d 

## 2. Check running containers 
docker ps 
You should see:
pg-database → PostgreSQL
pg-admin → pgAdmin (GUI for PostgreSQL)

## 3. Connect with PostgreeSQL from terminal 
docker exec -it pg-database psql -U admin -d practice_db

## 4. In the promt use SQL to build tables and play with it: 
CREATE TABLE users (id SERIAL PRIMARY KEY, name TEXT);
INSERT INTO users (name) VALUES ('Alice'), ('Bob');
SELECT * FROM users;

CREATE TABLE frutas (
  id SERIAL PRIMARY KEY,
  nombre VARCHAR(50),
  color VARCHAR(20),
  precio NUMERIC(5,2)
);

INSERT INTO frutas (nombre, color, precio)
VALUES
('manzana', 'rojo', 10.50),
('pera', 'verde', 8.00),
('manzana', 'verde', 9.20);

SELECT * FROM frutas;

## 5.- Exit with: 
\q 

## 6.- Access to PGAdmin (GUI)
open your browser at: 
http://localhost:8080

Log in and create a new pgAdmin:
Use these settings:

Host: db
User: admin
Password: secret
Database: practice_db

## 7.- View the logs 
docker compose logs -f

## 8.- Stop with: 
cntrl+c 

## 9.- STOP THE CONTAINERS AND DELATE DATABASE DATA 
docker compose down -v

