# MySQL: A Beginner's Guide

## Introduction to MySQL

MySQL is one of the most popular open-source relational database management systems (RDBMS). It uses Structured Query Language (SQL) to manage and organize data in tables with rows and columns.

### Key Features of MySQL
- Open-source and free to use
- Reliable and secure data storage
- Supports multiple users and concurrent connections
- Compatible with various programming languages
- Excellent performance and scalability

## Understanding Database Concepts

### Database Structure
- **Database**: A collection of organized data
- **Tables**: Structured lists of data organized in rows and columns
- **Columns**: Define the type of data stored (e.g., text, numbers, dates)
- **Rows**: Contain the actual data entries
- **Primary Keys**: Unique identifiers for each row

### Basic MySQL Operations
- CREATE: Make new databases and tables
- INSERT: Add data to tables
- SELECT: Retrieve data from tables
- UPDATE: Modify existing data
- DELETE: Remove data from tables

## Docker Overview

Docker is a platform that uses containerization technology to package applications and their dependencies together. This makes it easy to run applications consistently across different environments.

### Benefits of Using Docker
- Consistent development environments
- Easy setup and configuration
- Isolated applications
- Portable across different systems
- Efficient resource usage

## Setting Up MySQL with Docker

### Prerequisites
- Docker installed on your system
- Basic understanding of command line interface
- Text editor for configuration files

### Step-by-Step Setup

1. **Pull MySQL Image**
```bash
docker pull mysql:latest
```

2. **Create and Run MySQL Container**
```bash
docker run --name mysql-db \
  -e MYSQL_ROOT_PASSWORD=yourpassword \
  -e MYSQL_DATABASE=mydatabase \
  -p 3306:3306 \
  -d mysql:latest
```

3. **Verify Container is Running**
```bash
docker ps
```

### Understanding the Docker Run Command
- `--name mysql-db`: Names your container
- `-e MYSQL_ROOT_PASSWORD`: Sets root password
- `-e MYSQL_DATABASE`: Creates initial database
- `-p 3306:3306`: Maps container port to host port
- `-d`: Runs container in detached mode

## Connecting to MySQL Container

### Using Command Line
```bash
docker exec -it mysql-db mysql -u root -p
```

### Using GUI Tools
1. Host: localhost
2. Port: 3306
3. Username: root
4. Password: yourpassword

## Basic MySQL Commands

### Database Operations
```sql
-- Create database
CREATE DATABASE example_db;

-- Show databases
SHOW DATABASES;

-- Use database
USE example_db;
```

### Table Operations
```sql
-- Create table
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50),
    email VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Show tables
SHOW TABLES;

-- Describe table structure
DESCRIBE users;
```

### Data Operations
```sql
-- Insert data
INSERT INTO users (username, email) 
VALUES ('john_doe', 'john@example.com');

-- Select data
SELECT * FROM users;

-- Update data
UPDATE users SET email = 'new_email@example.com' 
WHERE username = 'john_doe';

-- Delete data
DELETE FROM users WHERE username = 'john_doe';
```

## Docker Container Management

### Common Commands
```bash
# Stop container
docker stop mysql-db

# Start container
docker start mysql-db

# Remove container
docker rm mysql-db

# View container logs
docker logs mysql-db
```

## Data Persistence

### Using Docker Volumes
```bash
docker run --name mysql-db \
  -e MYSQL_ROOT_PASSWORD=yourpassword \
  -v mysql-data:/var/lib/mysql \
  -p 3306:3306 \
  -d mysql:latest
```

## Best Practices

1. **Security**
   - Always use strong passwords
   - Never expose root password in production
   - Use custom users with limited privileges

2. **Backup**
   - Regularly backup your databases
   - Test restore procedures
   - Use Docker volumes for persistence

3. **Performance**
   - Monitor resource usage
   - Optimize queries
   - Index frequently queried columns

## Troubleshooting

### Common Issues and Solutions

1. **Cannot connect to MySQL**
   - Check if container is running
   - Verify port mapping
   - Confirm network settings

2. **Data disappears after container restart**
   - Use Docker volumes
   - Check volume mounting
   - Verify persistence configuration

3. **Performance issues**
   - Check container resources
   - Monitor system logs
   - Optimize MySQL configuration

## Next Steps

1. Learn advanced MySQL concepts
   - Joins and relationships
   - Transactions
   - Stored procedures

2. Explore Docker Compose
   - Multi-container applications
   - Environment configuration
   - Service orchestration

3. Study database design
   - Normalization
   - Indexing strategies
   - Performance optimization

## Resources

- [MySQL Documentation](https://dev.mysql.com/doc/)
- [Docker Documentation](https://docs.docker.com/)
- [Docker Hub MySQL](https://hub.docker.com/_/mysql)
