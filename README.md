Health & Fitness Platform
A comprehensive full-stack health and fitness tracking platform built with FastAPI, SQLModel, and vanilla JavaScript.

Overview
This platform provides a unified solution for managing workouts, heart rate monitoring, sleep tracking, nutrition analysis, product recommendations, and community blogs. It features AI-powered insights, real-time heart rate monitoring via WebSocket, and role-based access control.

Tech Stack
Backend
FastAPI - Modern, fast web framework for building APIs
SQLModel - ORM built on SQLAlchemy and Pydantic
SQLite - Database (demo mode)
JWT - Authentication (python-jose)
Passlib - Password hashing
WebSockets - Real-time heart rate streaming
OpenAI API - AI-powered features (optional)
Frontend
HTML5 - Semantic markup
CSS3 - Custom responsive styling
Vanilla JavaScript - No framework dependencies
Chart.js - Heart rate visualization
WebSocket API - Real-time data streaming
Key Features
User Features
✅ User signup/login with JWT authentication
✅ Personal dashboard with comprehensive health metrics
✅ Real-time heart rate monitoring with simulated data
✅ AI-powered adaptive workout plan generator
✅ Heart rate anomaly detection using z-score algorithm
✅ AI vision-based food nutrition analyzer (requires OpenAI API key)
✅ Sleep, workout, and nutrition tracking
✅ BMI calculator with trend tracking
✅ Personalized product recommendations
✅ Community blog system (create/view/delete own posts)
✅ Product browsing with search functionality
Admin Features
✅ System analytics dashboard
✅ User management
✅ Product CRUD operations
✅ Blog moderation (delete any post)
✅ System overview and statistics
Project Structure
.
├── main.py                 # FastAPI application and API endpoints
├── models.py              # SQLModel database models
├── config.py              # Configuration settings
├── seed_data.py           # Database seeding script
├── static/
│   ├── index.html         # Public homepage
│   ├── login.html         # Login page
│   ├── signup.html        # User registration
│   ├── dashboard.html     # User dashboard with charts
│   ├── products.html      # Product listing
│   ├── blogs.html         # Blog listing and creation
│   ├── profile.html       # User profile management
│   ├── admin.html         # Admin dashboard
│   ├── css/
│   │   └── style.css      # Custom responsive styles
│   └── js/
│       ├── auth.js        # Authentication logic
│       ├── dashboard.js   # Dashboard functionality
│       ├── products.js    # Product browsing
│       ├── blogs.js       # Blog management
│       ├── profile.js     # Profile updates
│       └── admin.js       # Admin operations
└── health_fitness.db      # SQLite database (auto-created)
Getting Started
Default Credentials
Note: Admin user creation may fail due to bcrypt compatibility. Create a new admin user through signup and manually update the role in the database if needed.

Alternatively, create users via signup page.

Running the Application
The application automatically starts on port 5000:

http://localhost:5000
Seeding Sample Data
Sample products and blogs can be added by running:

python seed_data.py
API Endpoints
Authentication
POST /auth/signup - Create new user account
POST /auth/login - Login with email/password
User
GET /api/user/me - Get current user profile
PUT /api/user/me - Update user profile
Health Metrics
GET /api/heart-rate/history - Get heart rate history
POST /api/heart-rate - Save heart rate reading
GET /api/heart-rate/simulate/{duration} - Generate simulated data
GET /api/heart-rate/anomalies - Detect anomalies
WS /ws/heart-rate/{user_id} - Real-time heart rate streaming
Workouts
GET /api/workouts - Get user workouts
POST /api/workouts - Log new workout
Sleep
GET /api/sleep - Get sleep records
POST /api/sleep - Log sleep data
Nutrition
GET /api/nutrition - Get nutrition logs
POST /api/nutrition - Log nutrition data
POST /api/ai/nutrition-image - Analyze food image (requires OpenAI)
AI Features
POST /api/ai/workout-plan - Generate personalized workout plan
GET /api/bmi - Calculate BMI
Products
GET /api/products - List all products (public)
GET /api/products?search=query - Search products
GET /api/products/recommended - Get personalized recommendations
POST /api/products - Create product (admin only)
DELETE /api/products/{id} - Delete product (admin only)
Blogs
GET /api/blogs - List all blogs (public)
POST /api/blogs - Create blog post (authenticated)
DELETE /api/blogs/{id} - Delete blog (author or admin)
Admin
GET /api/admin/users - List all users (admin only)
GET /api/admin/analytics - System analytics (admin only)
Heart Rate Simulator
The platform includes a realistic heart rate simulator that:

Generates BPM values based on activity levels (resting, walking, jogging, running, cooldown)
Includes natural variability using sine waves (breathing patterns)
Simulates activity transitions
Provides real-time streaming via WebSocket
Note: This is simulated data for demonstration; real device integration planned for production
AI Features
Workout Plan Generator
Generates personalized workout plans based on:

User age, height, weight, BMI
Workout history
Sleep quality
Fitness goals
Anomaly Detection
Uses z-score algorithm to detect:

Unusually high resting heart rate
Heart rate spikes during low exertion
Sudden drops during intense workouts
Nutrition Analyzer
Analyzes food images using OpenAI Vision API to extract:

Food name
Calories
Macros (protein, carbs, fats)
Portion size estimates
Note: AI features require OPENAI_API_KEY environment variable. Without it, the app provides fallback responses.

Product Recommendation Engine
Rule-based recommendation system considering:

User BMI
Nutrition deficiencies
Workout types
User goals (weight loss, muscle gain, endurance, general fitness)
Environment Variables
Optional environment variables:

SESSION_SECRET - Session secret key (auto-generated if not set)
OPENAI_API_KEY - OpenAI API key for AI features
Database Schema
Users - User accounts with profile information
HeartRate - Heart rate readings with timestamps
Workouts - Workout logs (type, duration, calories)
Sleep - Sleep tracking (hours, quality)
Nutrition - Food logs with macro breakdown
Products - Health & fitness products catalog
Blogs - Community blog posts
Anomalies - Detected health anomalies
Security Features
Password hashing with bcrypt
JWT token-based authentication
Role-based access control (USER/ADMIN)
Protected API endpoints
Session management
Recent Changes
Initial project setup and architecture
Database models and API endpoints created
Frontend pages with responsive design
Real-time heart rate monitoring implemented
AI integration for workout plans and nutrition analysis
Product recommendation system
Blog community features
Admin dashboard with analytics
Development Notes
Known Issues
Bcrypt version compatibility may cause admin user creation to fail on startup
Workaround: Create users via signup page
OpenAI API features are optional and require API key configuration
Future Enhancements
Integrate real wearable device APIs (Fitbit, Apple Watch, Garmin)
Payment gateway for product purchases
Social features (follow users, like/comment on blogs)
Advanced analytics with health trend predictions
Mobile app development
Enhanced AI features with personalized meal planning
Contributing
This is a demonstration project showcasing a full-stack health & fitness platform made by Samriddhi Kasaju

License
Educational/Demo Project by Sam - November 2025
