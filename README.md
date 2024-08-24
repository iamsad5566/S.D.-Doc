# Overview
The Sustainable Diet Platform is designed to promote sustainable eating habits through a mobile application. The platform provides various services, including member management, knowledge content, discussion forums, activities and news updates, geographic information services, and email services. Each service is built as a microservice to ensure scalability, flexibility, and ease of maintenance.
## System Architecture
## Mobile App

- Description: Interface for users to interact with the platform.
- Technologies: Flutter (for mobile development).

## Web App (Future Implementation)

- Description: Interface for backend maintenance and administrative tasks.
- Technologies: Next.js (for web development).

## RBAC-Member Service

- Description: Handles all member-related functionalities, including authentication, authorization, and session management.
- Technologies: Go, PostgreSQL, Redis, gRPC.
- Components:

    - OAuth2.0 Component: Manages Google login.
    - Token Management Component: Issues and verifies JWT tokens.
    - Member Database Component: Stores member information and settings in PostgreSQL.
    - Session Management Component: Handles login time updates using Redis.
    - gRPC Interface Component: Communicates with other services to verify token validity.
    - Request Handling Component: Processes incoming requests from the frontend.

## Knowledge Service

- Description: Provides monthly themes related to flowers and solar terms, knowledge about agricultural products and crops from various counties, and recipe information.
- Technologies: Go, MongoDB.
- Components:

    - Content Database Component: Stores knowledge content in MongoDB.
    - Content Delivery Component: Delivers content to users.
    - Request Handling Component: Processes incoming requests from the frontend.

## Recipe Service

- Description: Manages recipe content and discussions.
- Technologies: Go, MongoDB, PostgreSQL, gRPC.
- Components:

    - Recipe Database Component: Stores recipes in MongoDB.
    - Comment Management Component: Manages comments using PostgreSQL.
    - Recipe Management Component: Manages recipe content and interactions.
    - Member Verification Component: Verifies member access to recipe content.
    - gRPC Interface Component: Communicates with the RBAC-Member Service.
    - Request Handling Component: Processes incoming requests from the frontend.

## Notification Service
- Description: Handles push notifications to users.
- Technologies: Go, MongoDB, FCM, NATS.
- Components:

    - FCM Component: Responsible for sending push notifications.
    - NATS Component: Receives push notification messages.
    - MongoDB Component: Stores news information and FCM tokens.
    - Request Handling Component: Processes incoming requests and messages.

## Challenge Service
- Description: Manages monthly challenges, exploration tasks, member achievements, and badges.
- Technologies: Go, PostgreSQL, gRPC.
- Components:

    - Challenge Database Component: Stores challenge and task information.
    - Achievement Component: Manages member achievements and badges.
    - gRPC Interface Component: Communicates with the RBAC-Member Service for verification.
    - Request Handling Component: Processes incoming requests from the frontend.

## Broadcaster
- Description: A daemon service for web scraping and scheduled tasks.
- Technologies: Go, Colly, NATS.
- Components:

    - Web Scraping Component: Uses Colly to scrape news websites.
    - Scheduled Task Component: Checks for new months and solar terms.
    - NATS Publishing Component: Sends messages to NATS for Notification Service processing.

## Geographic Information Service

- Description: Converts GPS coordinates to location information (city/county).
- Technologies: Go, PostgreSQL (OSM).
- Components:

    - OSM Database Component: Manages geographic information using a self-hosted PostgreSQL (OSM) database.
    - Geocoding Component: Converts GPS coordinates to geographic locations.
    - GPS to City/County Conversion Component: Translates geographic locations to specific city/county information.
    - Request Handling Component: Processes incoming requests from the frontend.

## Mail Service

- Description: Handles password reset functionality for forgotten passwords.
- Technologies: Go, PostgreSQL.
- Components:

    - Mail Database Component: Stores email-related information in PostgreSQL.
    - Password Reset Component: Manages the password reset process.
    - Email Sending Component: Responsible for sending password reset emails.
    - Request Handling Component: Processes incoming requests from the frontend.

## Security

- Database Authentication: All backend databases require certificate authentication for login.
- Data Encryption: Private data is encrypted using bcrypt.
- HTTPS: All services communicate over HTTPS for secure data transmission.
- gRPC: Services use gRPC for efficient and reliable inter-service communication.
- JWT: JSON Web Tokens (JWT) are used for secure authentication and authorization.

## Scalability

- Each microservice is designed to be scalable and can be deployed independently to handle increased load.
- Redis and PostgreSQL are used for efficient session management and data storage.
- MongoDB is utilized for storing unstructured content, ensuring flexibility and scalability.

## Future Enhancements

- Implementation of the web app for backend maintenance and administrative tasks.

## Continuous Integration and Deployment

- All developed backends use GitHub workflows for CI/CD to automate testing and deployment processes.