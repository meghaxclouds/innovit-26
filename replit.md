# FarmGPT  

# Overview

FarmGPT is a bilingual (English/Hindi) mobile farming assistant application built with Expo (React Native) on the frontend and Express.js on the backend. It provides Indian farmers with location-based weather data, crop recommendations, soil information, government scheme details, a community messaging feature, and a crop calendar so that they can . The app uses GPS to detect the farmer's location, fetches real-time weather data from OpenWeatherMap, and provides tailored agricultural advice based on weather conditions and regional soil data.

# Mode of communication
for this prototype language primarily used is English and Hindi.

# System Architecture

# Frontend  
 Built with Expo / React Native
 Runs on Android , iOS and Web


- **Framework**:

uses expo-router for file-based routing

**Screen and Navigation**: File-based routing via "expo-router"
all screens live in the "app/" folder
(index, language, dashboard, recommendations, weather-detail, schemes, community, crop-calendar, about)
**State Management**:
uses React Context API
Stores :
language preference, location, weather data, forecast, and community messages. 
AsyncStorage persists language selection.

**Data Fetching**: 
TanStack React Query  

**UI & Design**:
Green agricultural theme
 
**Bilingual Support**: 
 English/Hindi translation system
 

# Backend 
Built with Express.js 
Handle secure API calls

**Runtime**: 
Runs on Node.js
Written in TypeScript 

**API Routes** 
 
**Storage** 
 uses in-memory storage (`MemStorage`)  
 no real database storage used yet.


 

**Static Data Files**  
 Crop recommendations
 soil data 
 government schemes
 crop calendar
  
**Database Schema**  
 PostgreSQL  
  Currently only has username/password fields. The schema exists but the app primarily uses `MemStorage`.
- **Drizzle Config** (`drizzle.config.ts`): Configured for PostgreSQL via `DATABASE_URL` environment variable. Use `npm run db:push` to push schema to database.

### Key Architectural Decisions

1. **Proxy pattern for API keys**: 
Weather API calls go through the Express server  

2. **Offline-capable data**:
Agricultural data (crops, soil, schemes, calendar) is bundled with the app as static TypeScript files, so core features work without network connectivity.
3. **Bilingual**: 
Every user has both English and Hindi versions.  

4. **Shared schema pattern**:  
Frontend and backend (Drizzle schema, Zod validators).

# Build & Run Commands

Development
- `npm run server:dev` — Start Express backend in development mode (uses tsx)
- `npm run expo:dev` — Start Expo development server

Database
- `npm run db:push` — Push Drizzle schema to PostgreSQL

Production
- `npm run server:build` — Bundle server with esbuild
- `npm run server:prod` — Run production server
 
 