## Database Schema

### 1. `users` Table

| Column Name | Data Type    | Constraints                | Description                   |
|-------------|--------------|----------------------------|-------------------------------|
| `id`        | INT          | PRIMARY KEY, AUTO_INCREMENT | Unique ID for each user       |
| `username`  | VARCHAR(50)  | NOT NULL, UNIQUE           | Username of the user          |
| `password`  | VARCHAR(255) | NOT NULL                  | Hashed password for the user  |
| `email`     | VARCHAR(100) | NOT NULL, UNIQUE           | Email address of the user     |

---

### 2. `posts` Table

| Column Name   | Data Type    | Constraints                | Description                             |
|---------------|--------------|----------------------------|-----------------------------------------|
| `id`          | INT          | PRIMARY KEY, AUTO_INCREMENT | Unique ID for each post                |
| `title`       | VARCHAR(255) | NOT NULL                  | Title of the blog post                 |
| `content`     | TEXT         | NOT NULL                  | Content/body of the blog post          |
| `author_id`   | INT          | NOT NULL, FOREIGN KEY (`users.id`) | ID of the user who created the post  |
| `created_at`  | TIMESTAMP    | DEFAULT CURRENT_TIMESTAMP | Timestamp when the post was created    |
| `updated_at`  | TIMESTAMP    | DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP | Timestamp for last update |

---

### 3. `comments` Table

| Column Name   | Data Type    | Constraints                | Description                             |
|---------------|--------------|----------------------------|-----------------------------------------|
| `id`          | INT          | PRIMARY KEY, AUTO_INCREMENT | Unique ID for each comment             |
| `post_id`     | INT          | NOT NULL, FOREIGN KEY (`posts.id`) | ID of the associated blog post       |
| `content`     | TEXT         | NOT NULL                  | Content/body of the comment            |
| `author_id`   | INT          | NOT NULL, FOREIGN KEY (`users.id`) | ID of the user who wrote the comment |
| `created_at`  | TIMESTAMP    | DEFAULT CURRENT_TIMESTAMP | Timestamp when the comment was created |

---

### Relationships

- **`users` → `posts`**: One-to-Many  
  A user can create multiple posts.
- **`posts` → `comments`**: One-to-Many  
  A post can have multiple comments.
- **`users` → `comments`**: One-to-Many  
  A user can write multiple comments.

## Setup Database
```sql
# For creating user table
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE
);

# For creating posts table
CREATE TABLE posts (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    author_id INT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (author_id) REFERENCES users(id)
);

# For creating comments table
CREATE TABLE comments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    post_id INT NOT NULL,
    content TEXT NOT NULL,
    author_id INT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (post_id) REFERENCES posts(id),
    FOREIGN KEY (author_id) REFERENCES users(id)
);


