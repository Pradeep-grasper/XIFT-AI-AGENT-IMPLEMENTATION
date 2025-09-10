XIFT-AI Agent: Fitness Tracker Application
This document outlines the implementation of the XIFT-AI Agent, a fitness tracking application that has moved from the conceptual stage to a working implementation. The application provides users with AI-driven insights and recommendations based on their logged workout and health data.



Table of Contents
Architecture

Core Functionalities

Project Structure

Testing

Architecture
The application is built using a modern, scalable architecture:


Frontend: A Flutter application provides the user interface.

Backend Services:


Firebase Firestore: Serves as the real-time, scalable NoSQL database for storing user data.


Firebase Authentication: Manages user login and security.



Google Gemini Pro API: Used for generating AI insights.

AI & Analytics Flow
The user logs their workouts and metrics through the Flutter app.

This data is then saved to Firebase Firestore.

AI insights are generated dynamically by the Gemini LLM.

The user can access all logs and insights from the app's dashboard.

Core Functionalities
The application implements several key features to provide a comprehensive fitness tracking experience:


User Authentication: Secure user login is handled by FirebaseAuth.


Workout Logging: Users can log various details about their workouts, including name, type, distance, duration, pace, heart rate, calories, weight, and BMI.

Health & Fitness Metrics:


Health: Tracks resting/target/max heart rate, blood pressure, temperature, blood oxygen, sugar, and sleep.


Fitness: Logs weight, height, BMI, body fat, muscle mass, water, bone mass, and BMR.

Real-Time AI Insights:

The system constructs prompts from user data to generate personalized feedback.


These insights are saved to Firestore and displayed on the user's dashboard.


Real-Time Streaming: The Flutter UI streams real-time updates for workouts, metrics, and insights.


Data Management: The application supports full CRUD (Create, Read, Update, Delete) operations for all workouts and metrics.

Project Structure
The project is organized into several main modules:


main.dart (Main App Entrypoint): This file initializes Firebase and Gemini , handles the onboarding logic using 

SharedPreferences , and controls the application's navigation and authentication state.



FirestoreService: This service encapsulates all Firestore CRUD operations for workouts and health/fitness metrics. It also streams data for real-time UI updates and contains modular functions for saving and deleting data.




InsightService: This service is responsible for fetching the latest user data from Firestore , crafting prompts , calling the Gemini Pro API to generate advice , and saving the AI insight back to the user's profile.




Testing
The application has undergone manual testing to ensure core functionalities are working as expected. Key areas that have been tested include:

Core user flows such as authentication, data logging, and the generation of AI insights.

Verification that Firestore streams update the dashboard in real-time.

The integration with the Gemini API has been tested with various sample user and workout data.
