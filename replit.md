# IsotopeVerse - Interactive Nuclear Applications Learning Platform

## Overview

IsotopeVerse is a modern, interactive web application designed to educate users about the non-energy applications of isotopes in medicine, agriculture, and industry. The platform features a single-page application with multiple educational sections, interactive simulations, a cost-benefit calculator, and an AI chatbot assistant named "Isotopo."

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
The application uses a modern React-based frontend built with:
- **React 18** with TypeScript for type safety
- **Vite** as the build tool and development server
- **Wouter** for client-side routing (lightweight alternative to React Router)
- **TanStack Query** for server state management and data fetching
- **Tailwind CSS** with custom CSS variables for styling
- **shadcn/ui** component library for consistent UI components

### Backend Architecture
The backend follows a simple Express.js REST API pattern:
- **Express.js** server with TypeScript
- **In-memory storage** (MemStorage class) for development/demo purposes
- RESTful API endpoints for chat functionality
- Static file serving for the built React application
- Development-only Vite integration for hot module replacement

### Component Structure
The application is organized into sections:
- **Hero Section**: Landing area with main call-to-action
- **Educational Sections**: Learn, Quiz, Simulate, Map sections
- **Interactive Components**: Chatbot, navigation, data visualization
- **UI Components**: Reusable shadcn/ui components with custom theming

## Key Components

### 1. Chat System
- **Purpose**: Provide interactive Q&A about isotope applications
- **Implementation**: Simple keyword-based response system with predefined responses
- **Storage**: Chat history stored in memory with user association
- **UI**: Floating chatbot widget with expandable chat interface

### 2. Quiz System
- **Purpose**: Interactive learning assessment
- **Implementation**: Client-side quiz with predefined questions
- **Features**: Progress tracking, explanations, scoring
- **State Management**: Local component state

### 3. Cost-Benefit Calculator
- **Purpose**: Demonstrate economic impact of isotope applications
- **Implementation**: Client-side calculator with preset formulas
- **Features**: Application type selection, scale adjustment, ROI calculation
- **Data**: Static calculation models for different sectors

### 4. Data Visualization
- **Purpose**: Display isotope application statistics and global usage
- **Implementation**: Chart.js integration via CDN
- **Types**: Pie charts for sector distribution, bar charts for economic impact
- **Data**: Static data sets loaded client-side

### 5. Navigation System
- **Purpose**: Smooth scrolling between page sections
- **Implementation**: Intersection Observer API for active section detection
- **Features**: Responsive mobile menu, smooth scroll behavior

## Data Flow

### Client-Server Communication
1. **API Requests**: TanStack Query handles HTTP requests to `/api/*` endpoints
2. **Chat Flow**: User message → API request → keyword matching → response storage → UI update
3. **Static Data**: All educational content and statistics are embedded in the frontend
4. **Error Handling**: Centralized error handling through TanStack Query and Express middleware

### State Management
1. **Server State**: Managed by TanStack Query with caching and error handling
2. **Component State**: Local React state for UI interactions
3. **Global State**: Minimal global state, mostly handled through URL and local storage

## External Dependencies

### Frontend Dependencies
- **UI Framework**: React, shadcn/ui components, Radix UI primitives
- **Styling**: Tailwind CSS, class-variance-authority for component variants
- **Data Fetching**: TanStack Query for server state management
- **Charts**: Chart.js loaded via CDN for data visualization
- **Form Handling**: React Hook Form with Zod validation
- **Date Handling**: date-fns for date manipulation

### Backend Dependencies
- **Server Framework**: Express.js with TypeScript support
- **Database ORM**: Drizzle ORM configured for PostgreSQL (not actively used)
- **Session Management**: connect-pg-simple for PostgreSQL sessions (not actively used)
- **Development Tools**: tsx for TypeScript execution, esbuild for production builds

### Development Dependencies
- **Build Tools**: Vite, esbuild, PostCSS, Autoprefixer
- **Database**: Drizzle Kit for schema management and migrations
- **Cloud Database**: Neon Database serverless driver (configured but not used)

## Deployment Strategy

### Build Process
1. **Frontend Build**: Vite builds React app to `dist/public`
2. **Backend Build**: esbuild bundles server code to `dist/index.js`
3. **Static Assets**: Frontend assets served by Express in production

### Environment Configuration
- **Development**: Vite dev server with HMR, Express API server
- **Production**: Single Express server serving both API and static files
- **Database**: Currently using in-memory storage, configured for PostgreSQL migration

### Scalability Considerations
- **Database**: Ready to migrate from in-memory to PostgreSQL using existing Drizzle schema
- **Session Management**: PostgreSQL session store configured for production
- **Static Assets**: Can be moved to CDN by updating build configuration
- **API Scaling**: Stateless API design allows for horizontal scaling

### Security Features
- **Input Validation**: Zod schemas for data validation
- **CORS**: Configured for cross-origin requests
- **Error Handling**: Centralized error handling prevents information leakage
- **Session Security**: Secure session configuration ready for production

## Development Notes

The application is designed as an educational platform with a focus on user engagement through interactive elements. The current implementation uses in-memory storage for simplicity, but the architecture supports easy migration to persistent storage. The modular component structure and TypeScript implementation ensure maintainability and type safety throughout the application.