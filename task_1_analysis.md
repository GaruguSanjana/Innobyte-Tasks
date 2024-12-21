# Task 1: Requirement Analysis for Blog API

## Core Features & Functionalities

1. **User Authentication**:
   - Users need to register, log in, and maintain user roles (admin, author, reader).

3. **Blog Post Management**:
   - Create, read, update, and delete blog posts (CRUD operations).
   - Posts should have attributes like title, content, tags, and category.

4. **Comment Management**:
   - Users can add, view, update, and delete comments on posts.
   - Comments are linked to specific blog posts.

5. **Likes/Dislikes**:
   - Users can like or dislike both blog posts and comments.

6. **Define User Roles:**:
   - Admin: Full access to the system, can manage users, posts, comments, and view all data.
   - Author: Can create, edit, and delete their own posts, manage their comments, and interact with other users’ posts.
   - Reader: Can only read posts and comments, as well as interact with likes/dislikes.

## API Endpoints

### User Endpoints
- **POST /users/register**: Registers a new user.
- **POST /users/login**: Logs in a user and returns a JWT token.

### Blog Post Endpoints
- **GET /posts**: Retrieve all blog posts.
- **GET /posts/{id}**: Retrieve a specific post by ID.
- **POST /posts**: Create a new post (authenticated).
- **PUT /posts/{id}**: Update a specific post.
- **DELETE /posts/{id}**: Delete a post.

### Comment Endpoints
- **POST /comments**: Add a comment to a post.
- **GET /comments/{postId}**: Retrieve all comments for a specific post.
- **PUT /comments/{id}**: Edit a comment.
- **DELETE /comments/{id}**: Delete a comment.

### Likes/Dislikes
- **POST /posts/{id}/like**: Like a post.
- **POST /posts/{id}/dislike**: Dislike a post.
- **POST /comments/{id}/like**: Like a comment.
- **POST /comments/{id}/dislike**: Dislike a comment.


## Conclusion

This document outlines the key features and the API endpoints for the Blog API application.
