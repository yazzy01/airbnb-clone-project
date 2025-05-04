# AirBnB Clone Project

## Project Overview
This repository contains an AirBnB clone project - a simplified web application that mimics the core functionalities of the popular accommodation rental platform, AirBnB. The backend is designed to provide a robust and scalable foundation for managing user interactions, property listings, bookings, and payments.

## Project Goals
- Develop a command interpreter to manage AirBnB objects
- Implement a secure system for user registration, authentication, and profile management
- Develop features for property listing creation, updates, and retrieval
- Create a booking mechanism for users to reserve properties
- Integrate a payment system to handle transactions
- Allow users to leave reviews and ratings for properties
- Implement a base class for all models in the system
- Create a simple flow of serialization/deserialization
- Create an abstracted storage engine
- Develop unit tests to validate all classes and storage engine
- Ensure efficient data retrieval and storage through database optimizations

## Team Roles
Here's a breakdown of the key roles and responsibilities within our project team:

### Project Manager
- Oversees the entire project lifecycle
- Creates and maintains the project roadmap
- Ensures deliverables are completed on time
- Facilitates communication between team members
- Identifies and mitigates project risks

### Backend Developer
- Implements the command interpreter functionality
- Develops the object models (User, Place, State, City, etc.)
- Creates the storage engine and serialization/deserialization methods
- Implements API endpoints and business logic
- Writes unit tests for backend components
- Ensures data integrity and security

### Database Administrator
- Designs the database schema
- Implements the file storage system
- Plans for future migration to MySQL/PostgreSQL
- Manages database indexing and optimizations
- Optimizes data access patterns
- Ensures data persistence and recovery mechanisms

### Frontend Developer
- Designs and implements the user interface
- Creates responsive web pages using HTML, CSS, and JavaScript
- Ensures cross-browser compatibility
- Implements user interaction features
- Connects the frontend with the backend API

### Quality Assurance Engineer
- Develops and executes test plans
- Identifies and documents bugs
- Performs regression testing
- Validates that the application meets requirements
- Ensures overall code quality and performance

### DevOps Engineer
- Sets up the development, testing, and production environments
- Implements continuous integration and deployment pipelines
- Manages version control systems
- Handles server configuration and maintenance
- Monitors application performance and availability

Each role is crucial for the successful implementation of the AirBnB clone project, and team members may take on multiple roles depending on the phase of the project.

## Technology Stack

Here's a detailed breakdown of the technology stack used in our AirBnB clone project:

### Python
- **Purpose**: Core programming language for backend development
- **Usage**: Implements the command interpreter, models, and business logic
- **Benefits**: Strong typing, extensive libraries, and excellent for object-oriented programming

### Django
- **Purpose**: High-level Python web framework
- **Usage**: Building the RESTful API and web application structure
- **Benefits**: Robust ORM, built-in admin interface, and security features

### Django REST Framework
- **Purpose**: Toolkit for building Web APIs
- **Usage**: Creating and managing RESTful APIs for the application
- **Benefits**: Powerful serialization, authentication, and viewsets

### PostgreSQL
- **Purpose**: Advanced open-source relational database
- **Usage**: Primary data storage for production environment
- **Benefits**: ACID compliance, JSON support, and excellent performance

### JSON (JavaScript Object Notation)
- **Purpose**: Data interchange format for storage
- **Usage**: Serializes and deserializes Python objects for persistency
- **Benefits**: Lightweight, human-readable, and language-independent

### GraphQL
- **Purpose**: Query language for APIs
- **Usage**: Provides flexible data querying capabilities
- **Benefits**: Reduced over-fetching and under-fetching of data

### Celery
- **Purpose**: Asynchronous task queue/job queue
- **Usage**: Handling background tasks like email notifications and payment processing
- **Benefits**: Distributed architecture and task scheduling

### Redis
- **Purpose**: In-memory data structure store
- **Usage**: Caching and session management
- **Benefits**: Fast performance and support for various data structures

### HTML (HyperText Markup Language)
- **Purpose**: Standard markup language for web pages
- **Usage**: Defines the structure and content of web pages
- **Benefits**: Universal browser support and semantic structure

### CSS (Cascading Style Sheets)
- **Purpose**: Style sheet language for presentation
- **Usage**: Designs the visual layout and aesthetics of web pages
- **Benefits**: Separation of content and presentation, responsive design capabilities

### JavaScript
- **Purpose**: Programming language for web interactivity
- **Usage**: Implements dynamic features and user interactions
- **Benefits**: Client-side execution, asynchronous programming, and DOM manipulation

### Docker
- **Purpose**: Containerization platform
- **Usage**: Creating consistent development and deployment environments
- **Benefits**: Isolation, portability, and scalability

### Unittest Framework
- **Purpose**: Python's built-in testing framework
- **Usage**: Tests the functionality of classes, methods, and features
- **Benefits**: Automated testing, test discovery, and test organization

## Database Design

The AirBnB clone project requires a well-structured database to store and manage various entities. Below is an overview of the key entities and their relationships:

### User
- **Fields:**
  - `id`: Unique identifier for each user
  - `email`: User's email address (used for authentication)
  - `password`: Encrypted password for account security
  - `first_name`: User's first name
  - `last_name`: User's last name
  - `created_at`: Timestamp when the user account was created
- **Relationships:**
  - A User can have multiple Places (as an owner)
  - A User can make multiple Bookings
  - A User can write multiple Reviews

### Place
- **Fields:**
  - `id`: Unique identifier for each property
  - `owner_id`: Reference to the User who owns the place
  - `name`: Name of the place
  - `description`: Detailed description of the place
  - `price_per_night`: Cost to stay per night
  - `latitude`: Geographic coordinate
  - `longitude`: Geographic coordinate
- **Relationships:**
  - A Place belongs to a User (owner)
  - A Place is located in a City
  - A Place can have multiple Bookings
  - A Place can have multiple Reviews
  - A Place can have multiple Amenities

### City
- **Fields:**
  - `id`: Unique identifier for each city
  - `name`: Name of the city
  - `state_id`: Reference to the State where the city is located
- **Relationships:**
  - A City belongs to a State
  - A City can have multiple Places

### State
- **Fields:**
  - `id`: Unique identifier for each state
  - `name`: Name of the state
- **Relationships:**
  - A State can have multiple Cities

### Booking
- **Fields:**
  - `id`: Unique identifier for each booking
  - `place_id`: Reference to the booked Place
  - `user_id`: Reference to the User making the booking
  - `check_in_date`: Start date of the booking
  - `check_out_date`: End date of the booking
  - `status`: Current status of the booking (confirmed, cancelled, etc.)
- **Relationships:**
  - A Booking belongs to a User
  - A Booking is for a specific Place
  - A Booking can have associated Payments

### Payment
- **Fields:**
  - `id`: Unique identifier for each payment
  - `booking_id`: Reference to the associated Booking
  - `amount`: Payment amount
  - `currency`: Currency code
  - `status`: Payment status (pending, completed, failed, etc.)
- **Relationships:**
  - A Payment belongs to a Booking

### Review
- **Fields:**
  - `id`: Unique identifier for each review
  - `place_id`: Reference to the reviewed Place
  - `user_id`: Reference to the User writing the review
  - `text`: Content of the review
  - `rating`: Numerical rating (typically 1-5)
  - `created_at`: Timestamp when the review was posted
- **Relationships:**
  - A Review belongs to a User
  - A Review is for a specific Place

### Amenity
- **Fields:**
  - `id`: Unique identifier for each amenity
  - `name`: Name of the amenity (e.g., WiFi, Pool, etc.)
- **Relationships:**
  - An Amenity can be associated with multiple Places
  - A Place can have multiple Amenities

## API Endpoints Overview

### Users
- `GET /users/` - List all users
- `POST /users/` - Create a new user
- `GET /users/{user_id}/` - Retrieve a specific user
- `PUT /users/{user_id}/` - Update a specific user
- `DELETE /users/{user_id}/` - Delete a specific user

### Properties/Places
- `GET /properties/` - List all properties
- `POST /properties/` - Create a new property
- `GET /properties/{property_id}/` - Retrieve a specific property
- `PUT /properties/{property_id}/` - Update a specific property
- `DELETE /properties/{property_id}/` - Delete a specific property

### Bookings
- `GET /bookings/` - List all bookings
- `POST /bookings/` - Create a new booking
- `GET /bookings/{booking_id}/` - Retrieve a specific booking
- `PUT /bookings/{booking_id}/` - Update a specific booking
- `DELETE /bookings/{booking_id}/` - Delete a specific booking

### Payments
- `POST /payments/` - Process a payment

### Reviews
- `GET /reviews/` - List all reviews
- `POST /reviews/` - Create a new review
- `GET /reviews/{review_id}/` - Retrieve a specific review
- `PUT /reviews/{review_id}/` - Update a specific review
- `DELETE /reviews/{review_id}/` - Delete a specific review

## Feature Breakdown

### User Management
The User Management system handles user registration, authentication, and profile management. It provides secure login mechanisms, password recovery options, and user profile customization, establishing the foundation for user identity within the platform.

### Property Management
Property Management allows hosts to create, update, and showcase their property listings. This feature includes property details, photos, amenities, and availability calendars, enabling hosts to effectively market their spaces to potential guests.

### Booking System
The Booking System facilitates the reservation process between guests and hosts. It manages availability checks, booking requests, confirmation processes, and cancellation policies, ensuring a seamless reservation experience for both parties.

### Payment Processing
Payment Processing handles all financial transactions within the platform. It securely processes payments from guests to hosts, manages refunds when necessary, and maintains payment records, providing the essential economic infrastructure for the marketplace.

### Review System
The Review System enables guests to share their experiences through ratings and written feedback. It builds trust within the community by allowing prospective guests to make informed decisions based on others' experiences, while helping hosts improve their offerings.

### Search and Filtering
Search and Filtering functionality allows users to find properties based on location, price, amenities, and availability. This feature uses advanced algorithms to deliver relevant results, enhancing the user experience by simplifying the property discovery process.

### Messaging System
The Messaging System facilitates communication between hosts and guests. It provides a secure channel for discussing booking details, answering questions, and coordinating check-in arrangements, fostering clear communication throughout the booking journey.

### Notification Service
The Notification Service keeps users informed about important events and updates. It sends timely alerts for booking confirmations, messages, upcoming stays, and system announcements, ensuring users stay connected with their account activities.

### Admin Dashboard
The Admin Dashboard provides platform administrators with tools to manage users, properties, and transactions. It includes reporting capabilities, user verification processes, and content moderation features, helping maintain platform integrity and quality standards.

### API Infrastructure
The API Infrastructure serves as the backbone for service integration and third-party connections. It follows RESTful design principles with comprehensive documentation, enabling developers to extend functionality and integrate with external services.

## Project Timeline
This project will be developed incrementally with multiple phases, starting with a command-line interface and eventually building up to a fully functional web application with a comprehensive API.

## Authors
- [Yassir Rzigui](https://github.com/yazzy01)