# NutriSync - Requirements Documentation

## Project Overview

NutriSync is an AI-powered nutrition and health tracking web application that provides personalized insights, meal planning, and progress tracking for users looking to optimize their health and nutrition journey.

## Functional Requirements

### 1. User Authentication & Authorization
- User registration with email and password
- Secure login/logout functionality
- Protected routes requiring authentication
- User session management
- Password security and validation

### 2. Body Metrics Analysis
- **BMI Calculator**
  - Input: Height (cm/inches), Weight (kg/lbs)
  - Output: BMI value with health category classification
  - Visual representation of BMI range
  
- **BMR Calculator**
  - Input: Age, gender, height, weight, activity level
  - Output: Basal Metabolic Rate calculation
  - Daily calorie recommendations based on goals (weight loss/gain/maintenance)

### 3. AI-Powered Nutrition Analysis
- **NutriScan Feature**
  - Image upload functionality for food items
  - AI-based dish recognition using Google Gemini API
  - Nutritional breakdown per 100g:
    - Calories (kcal)
    - Protein (g)
    - Carbohydrates (g)
    - Fat (g)
  - Support for Indian cuisine dishes
  - Image storage and retrieval

### 4. Meal Planning
- **AI Meal Planner**
  - Input parameters:
    - Preferred ingredients
    - Cuisine type
    - Meal type (breakfast/lunch/dinner/snack)
    - Target calorie range
  - Output: Personalized meal recommendations with nutritional values
  - Save and retrieve meal plans

### 5. Progress Tracking
- **Weight Tracker**
  - Daily weight entry logging
  - Historical weight data visualization
  - Trend analysis with charts
  - Goal progress indicators
  
- **Nutrition Progress Dashboard**
  - Daily calorie tracking
  - Macronutrient tracking (protein, carbs, fat)
  - Visual progress bars and percentages
  - Goal vs. actual consumption comparison

### 6. Diet Logging
- **Manual Entry**
  - Food name and portion size
  - Meal type categorization
  - Manual nutritional value input
  - Timestamp tracking
  
- **AI-Powered Entry**
  - Natural language food description
  - Automatic nutritional analysis
  - Portion estimation
  - Auto-categorization by meal type

### 7. User Dashboard
- Personalized health metrics overview
- Quick access to all features
- Recent activity summary
- Goal tracking widgets
- Nutrition recommendations

## Non-Functional Requirements

### 1. Performance
- Fast image processing (< 5 seconds for AI analysis)
- Responsive UI with smooth transitions
- Efficient data loading and caching
- Optimized API calls

### 2. Usability
- Intuitive and clean user interface
- Mobile-responsive design
- Accessible navigation
- Clear visual feedback for user actions
- Error handling with user-friendly messages

### 3. Security
- Secure authentication with Supabase
- Environment variable protection for API keys
- HTTPS for data transmission
- Input validation and sanitization
- Protected API endpoints

### 4. Scalability
- Database design supporting multiple users
- Efficient file storage for uploaded images
- API rate limiting considerations
- Modular component architecture

### 5. Reliability
- Error handling and recovery
- Data validation
- Backup and data persistence
- API fallback mechanisms

## Technical Requirements

### Frontend Stack
- **Framework**: React 18.3.1 with TypeScript
- **Build Tool**: Vite 7.3.1
- **Styling**: Tailwind CSS 3.4.11
- **UI Components**: Shadcn UI (Radix UI primitives)
- **Routing**: React Router DOM 6.26.2
- **State Management**: Tanstack React Query 5.56.2
- **Forms**: React Hook Form 7.53.0 with Zod validation
- **Animations**: Framer Motion 11.18.2
- **Charts**: Recharts 2.12.7
- **Icons**: Lucide React 0.462.0

### Backend Stack
- **Runtime**: Node.js with Express 4.21.2
- **File Upload**: Multer 2.0.2
- **HTTP Client**: Axios 1.8.3
- **CORS**: cors 2.8.5
- **Environment**: dotenv 16.4.7

### Database & Authentication
- **Database**: Supabase (PostgreSQL)
- **Authentication**: Supabase Auth
- **Storage**: Supabase Storage for images

### External APIs
- **AI Service**: Google Gemini API for:
  - Food image recognition
  - Nutritional analysis
  - Meal recommendations

## System Architecture

### Frontend Architecture
```
src/
├── components/        # Reusable UI components
├── pages/            # Route-based page components
├── contexts/         # React Context providers
├── hooks/            # Custom React hooks
├── utils/            # Utility functions
├── integrations/     # External service integrations
└── lib/              # Shared libraries
```

### Backend Architecture
```
backend/
├── server.js         # Express server setup
├── uploads/          # Temporary file storage
└── .env              # Environment configuration
```

## API Requirements

### Backend Endpoints
- `POST /api/analyze` - Upload and analyze food image
- `POST /api/meal-plan` - Generate meal recommendations
- File upload handling with multipart/form-data
- CORS enabled for frontend communication

### External API Integration
- Google Gemini API for AI-powered features
- Supabase API for database operations
- Supabase Auth API for user management

## Data Models

### User Profile
- User ID (UUID)
- Email
- Personal metrics (age, height, weight, gender)
- Activity level
- Health goals
- Created/updated timestamps

### Weight Entry
- Entry ID
- User ID (foreign key)
- Weight value
- Date
- Notes (optional)

### Meal Log
- Log ID
- User ID (foreign key)
- Food name
- Meal type
- Nutritional values
- Portion size
- Timestamp

### Nutrition Goals
- Goal ID
- User ID (foreign key)
- Daily calorie target
- Protein target
- Carbs target
- Fat target

## Environment Variables

### Frontend (.env)
```
VITE_SUPABASE_URL=<supabase-project-url>
VITE_SUPABASE_ANON_KEY=<supabase-anon-key>
```

### Backend (backend/.env)
```
PORT=5000
GEMINI_API_KEY=<google-gemini-api-key>
```

## Browser Support
- Chrome (latest 2 versions)
- Firefox (latest 2 versions)
- Safari (latest 2 versions)
- Edge (latest 2 versions)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Deployment Requirements
- Frontend: Vercel (configured via vercel.json)
- Backend: Node.js hosting service
- Database: Supabase cloud
- File Storage: Backend uploads directory or cloud storage

## Development Requirements
- Node.js 18+ and npm/bun
- Git for version control
- Code editor with TypeScript support
- Environment variable configuration
- Google Gemini API access
- Supabase project setup

## Testing Requirements
- Component testing for UI elements
- API endpoint testing
- Authentication flow testing
- Image upload and processing testing
- Form validation testing
- Responsive design testing

## Future Enhancements
- Multi-language support
- Integration with fitness tracking devices
- Social sharing features
- Expanded food database
- Barcode scanning
- Recipe suggestions
- Meal prep planning
- Grocery list generation
- Nutritionist consultation booking
- Community features and forums

## Constraints & Limitations
- Requires active internet connection
- Dependent on Google Gemini API availability
- Image analysis accuracy varies by image quality
- Limited to foods recognizable by AI model
- Nutritional data is approximate
- Not a substitute for professional medical advice

## Compliance & Legal
- MIT License (open-source)
- User data privacy compliance
- GDPR considerations for user data
- Terms of service for AI-generated content
- Disclaimer for health-related information
- API usage terms compliance (Google Gemini)
