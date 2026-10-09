# Article Avenue Backend

## Overview
Article Avenue is a full-stack web application for creating, publishing, and discovering articles. Users can sign up, write and edit articles, save drafts, publish completed posts, and browse public article and author pages.

This repository contains the Django backend of the application, which handles application logic, authentication, article management, database interactions, media storage, and API communication with the React frontend.

## Technical Details
The backend was built with Django and uses PostgreSQL for persistent data storage. Django's Object-Relational Mapping (ORM) is used to retrieve and modify user, published article, and draft article records.

The backend uses session-based authentication to maintain logged-in user state across requests. User passwords are hashed before being stored.

Uploaded media such as article thumbnails and profile pictures are handled through Django's media system, while CORS configuration allows the separately hosted React frontend to communicate with the backend.

## API and Database

### API

- User sign-up and sign-in
- Session management and authentication
- Create, retrieve, update, and delete published articles
- Create, retrieve, update, and delete draft articles
- Retrieve articles by username, title, and category
- Author and profile information retrieval

### Database

- PostgreSQL storage for users, published articles, and drafts
- Article records include content, titles, author usernames, categories, descriptions, timestamps, and thumbnail references
- Article thumbnail and profile picture paths are stored as references to media files

## Architecture

The diagram below shows the overall Article Avenue architecture and how the Django backend handles requests from the React frontend and communicates with the PostgreSQL database.

<img width="100%" alt="Article Avenue Architecture" src="https://github.com/user-attachments/assets/bbae9bf8-465d-4a37-b5a7-9f466081bd7e">

## Challenges

One challenge was improving the performance of the public article page. Article thumbnail images were initially stored directly in PostgreSQL, which increased the amount of data transferred when loading articles. We changed the backend design so that thumbnail image files were stored on the server while the database stored references to them instead. This reduced the amount of data being transferred and improved response times.

## Related Repositories

This backend repository was created after the original Article Avenue project was separated into frontend and backend repositories to support deployment.

- Frontend repository: [Article Avenue Frontend](https://github.com/ala264/articleAvenueFrontend)
- Original combined repository: [Article Avenue (Earlier Version)](https://github.com/hathaull/article_app)
