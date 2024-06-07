# Overview
The Sustainable Diet Platform is designed to promote sustainable eating habits through a mobile application. The platform provides various services, including member management, knowledge content, discussion forums, activities and news updates, and geographic information services. Each service is built as a microservice to ensure scalability, flexibility, and ease of maintenance.

## System Architecture
### Mobile App
- **Description:** Interface for users to interact with the platform.
- **Technologies:** Flutter (for mobile development).
### Web App (Future Implementation)
- **Description:** Interface for backend maintenance and administrative tasks.
- **Technologies:** Next.js (for web development).
### RBAC Member Management Service
- **Description:** Handles all member-related functionalities, including authentication, authorization, and session management.
- **Technologies:** Go, PostgreSQL, Redis, gRPC.
- **Components:**
    - **OAuth2.0 Component:** Manages Google login.
    - **Token Management Component:** Issues and verifies JWT tokens.
    - **Member Database Component:** Stores member information and settings in PostgreSQL.
    - **Session Management Component:** Handles login time updates using Redis.
    - **gRPC Interface Component:** Communicates with other services to verify token validity.
    - **Request Handling Component:** Processes incoming requests from the frontend.
## Knowledge Content Service
- **Description:** Provides monthly themes related to flowers and solar terms, knowledge about agricultural products and crops from various counties, and recipe information.
- **Technologies:** Go, MongoDB, gRPC.
- **Components:**
    - **Content Database Component:** Stores knowledge content in MongoDB.
    - **Content Delivery Component:** Delivers content to users.
    - **Member Verification Component:** Verifies member access to specific content.
    - **gRPC Interface Component:** Communicates with the RBAC Member Management Service.
    - **Request Handling Component:** Processes incoming requests from the frontend.
## Discussion Forum Service
- **Description:** Manages discussion content for the platform’s forums.
- **Technologies:** Go, MongoDB, gRPC.
- **Components:**
    - **Discussion Database Component:** Stores forum discussions in MongoDB.
    - **Forum Management Component:** Manages forum content and interactions.
    - **Member Verification Component:** Verifies member access to forum content.
    - **gRPC Interface Component:** Communicates with the RBAC Member Management Service.
    - **Request Handling Component:** Processes incoming requests from the frontend.
## Activity and News Service
- **Description:** Updates activities and pushes new information to users. Includes a push notification system using WebSocket and NATS.
- **Technologies:** Go, MongoDB, gRPC, WebSocket, NATS.
- **Components:**
    - **Activity Database Component:** Stores activity and news information in MongoDB.
    - **News Delivery Component:** Manages the delivery of news updates to users.
    - **Member Verification Component:** Verifies member access to specific news content.
    - **gRPC Interface Component:** Communicates with the RBAC Member Management Service.
    - **Request Handling Component:** Processes incoming requests from the frontend.
    - **WebSocket Component:** Manages real-time communication with the frontend.
    - **NATS Component:** Handles message publishing and subscribing for push notifications.
    - **Crawler/Scraper Component:** Automatically or manually fetches data from external sources.
    - **RESTful API Component:** Provides endpoints for communication with other services.
## Geographic Information Service
- **Description:** Converts GPS coordinates to location information (city/county).
- **Technologies:** Go, PostgreSQL (OSM), gRPC.
- **Components:**
    - **OSM Database Component:** Manages geographic information using a self-hosted PostgreSQL (OSM) database.
    - **Geocoding Component:** Converts GPS coordinates to geographic locations.
    - **GPS to City/County Conversion Component:** Translates geographic locations to specific city/county information.
    - **Request Handling Component:** Processes incoming requests from the frontend.
## Security
- **Database Authentication:** All backend databases require certificate authentication for login.
- **Data Encryption:** Private data is encrypted using bcrypt.
- **HTTPS:** All services communicate over HTTPS for secure data transmission.
- **gRPC:** Services use gRPC for efficient and reliable inter-service communication.
- **JWT:** JSON Web Tokens (JWT) are used for secure authentication and authorization.
## Scalability
- Each microservice is designed to be scalable and can be deployed independently to handle increased load.
- Redis and PostgreSQL are used for efficient session management and data storage.
- MongoDB is utilized for storing unstructured content, ensuring flexibility and scalability.
## Future Enhancements
- Implementation of the web app for backend maintenance and administrative tasks.
## Continuous Integration and Deployment
- All developed backends use GitHub workflows for CI/CD to automate testing and deployment processes.