# AI Placement Helper

A comprehensive tool to help job seekers analyze job descriptions, research companies, and prepare for interviews.

## Getting Started

Follow these instructions to run the application locally.

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or cloud instance)
- Windows OS (for the included start scripts)

### Installation

1. Clone the repository
2. Install backend dependencies:
   ```
   cd backend
   npm install
   ```
3. Install frontend dependencies:
   ```
   cd frontend
   npm install
   ```

### Environment Setup

Make sure the backend `.env` file contains the following:

```
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
PORT=5000
SERP_API_KEY=your_serp_api_key
```

## Running the Application

### Option 1: Using the improved startup script (recommended)

Run the following command from the project root:

```
node start-with-seed.js
```

This script will:
1. Test and seed the database if needed
2. Start the LLM server (if available)
3. Start the backend server
4. Start the frontend development server

### Option 2: Manual startup

Start each component separately:

1. **Seed the database (if not already populated):**
   ```
   cd backend
   node scripts/test-db-connection.js
   ```

2. **Start the backend server:**
   ```
   cd backend
   npm start
   ```

3. **Start the frontend development server:**
   ```
   cd frontend
   npm start
   ```

## Troubleshooting

### Company Information Not Showing Up

If you see "No information found" when searching for companies:

1. Check if the database is properly seeded:
   ```
   cd backend
   node scripts/test-db-connection.js
   ```

2. Check backend logs for any errors (usually shown in the backend terminal)

3. Test the API directly:
   ```
   curl http://localhost:5000/api/company/Infosys
   ```

4. If you see a 204 status code or empty response, try:
   - Restarting the backend server
   - Checking MongoDB connection in the backend logs
   - Verifying that the database contains company records

### Backend Connection Issues

If the frontend cannot connect to the backend:

1. Ensure the backend is running on port 5000
2. Check for CORS issues in the browser console
3. Verify that the frontend is configured to use `http://localhost:5000` for API calls

## Features

- **Job Analysis**: Analyze job descriptions and extract key information
- **Company Research**: Get comprehensive information about companies
- **Interview Preparation**: Learn about interview processes and best practices

## Data Sources

Company information is sourced from:

1. Internal database (pre-seeded with popular companies)
2. External APIs, including:
   - SerpAPI (Google Knowledge Graph)
   - WikiData
   - Wikipedia
   - DuckDuckGo

## Enhanced Company Information

The application now features a comprehensive company information system with detailed data on numerous companies. The enhanced data includes:

- **Basic Information**: Name, description, headquarters, industry, founding year, employee count, revenue, website
- **Leadership**: CEO and key executives
- **Social Media**: Links to official company profiles on LinkedIn, Twitter, Facebook, etc.
- **Financial Information**: Stock symbol, exchange, market cap, and stock price
- **Key Achievements**: Major company milestones and innovations
- **Awards & Recognition**: Industry awards and honors received
- **Technology Stack**: Technologies and frameworks used by the company
- **Products & Services**: Main offerings and services
- **Office Locations**: Global presence and key office locations
- **Work Environment**: Office type, dress code, work hours, WFH policy
- **Hiring Process**: Application information, timeframes, required documents
- **Salary Information**: Average salary ranges by level, bonus structure, equity options
- **Culture**: Values, work-life balance, team environment, diversity initiatives
- **Benefits**: Healthcare, insurance, PTO, perks, retirement plans
- **Career Growth**: Promotion opportunities, training programs, career paths
- **Interview Process**: Interview rounds, tips, common questions
- **Employee Reviews**: Real insights from current/former employees
- **Recent News**: Latest company developments and announcements

### Adding or Updating Company Data

The database comes pre-seeded with information on popular companies. To add your own or update existing entries:

1. Run the dedicated database seeding tool:
   ```
   node seed-db.js
   ```

2. To add new companies, edit the `backend/scripts/seedCompanies.js` file and add company objects following the existing format.

3. You can also add companies directly to the MongoDB database if you prefer.

### Enhancing Hiring Process & Career Data

To ensure all companies have comprehensive information about hiring processes and career growth opportunities, run:

```
cd backend
node scripts/enhance-hiring-data.js
```

This script will:
- Check all companies in the database for missing hiring process, career growth, or interview process information
- Add standardized, quality data to any company with incomplete information
- Preserve any existing data while only filling in missing sections
- Provide immediate feedback on which companies were enhanced

The default data includes:
- **Hiring Process**: Required documents, application portal, timeframes, background check information
- **Career Growth**: Promotion opportunities, training programs, mentorship, career paths
- **Interview Process**: Common questions, interview rounds, preparation tips, typical duration

This enhancement ensures a consistent user experience across all company profiles, regardless of data source.

### Complete Data Preparation

For a complete database setup that handles all preparation steps in one command, use:

```
cd backend
node scripts/prepare-all-data.js
```

This comprehensive script will:
1. Test the database connection
2. Seed the database with company information
3. Enhance all companies with complete hiring process and career data

This is the recommended approach when setting up the application for the first time or after a database reset.

### Viewing Company Information

1. Navigate to the Company Information page in the application
2. Search for a company by name
3. Browse the detailed information organized in sections

The company information feature helps job seekers make informed decisions about potential employers and prepare effectively for interviews.

## Contributing

Contributions are welcome! Please feel free to submit pull requests. 