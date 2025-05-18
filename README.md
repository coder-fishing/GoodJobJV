# GoodJob Project Setup Guide

## Video Tutorial

### Hướng dẫn cài đặt 
![Setup ](.github/assets/Video.mp4)

### Hướng dẫn cài đặt Demo Chức năng cơ bản

https://drive.google.com/file/d/1WcNsDNxK2gIkf9VTMnra5mgBk-av8RMN/view?usp=sharing



## Database Setup
1. Install MySQL Server
2. Create a new database named `au2`:
```sql
CREATE DATABASE au2;
```

## Backend Setup (GoodJobBackEnd)

### Prerequisites
1. Install IntelliJ IDEA (Ultimate version recommended for better Spring Boot support)
2. Install JDK 17 or later
3. Install MySQL Server

### Facebook OAuth Setup
1. Go to [Facebook Developers](https://developers.facebook.com/)
2. Create a new app or select existing app
3. Add Facebook Login product
4. Configure OAuth settings:
   - Add OAuth redirect URI: `http://localhost:8080/login/oauth2/code/facebook`
   - Get Client ID and Client Secret
   - Add these to your `.env` file

### Google OAuth Setup
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing project
3. Enable Google+ API
4. Configure OAuth consent screen
5. Create OAuth 2.0 credentials:
   - Add OAuth redirect URI: `http://localhost:8080/login/oauth2/code/google`
   - Get Client ID and Client Secret
   - Add these to your `.env` file

### Gmail SMTP Setup
1. Go to your Google Account settings
2. Enable 2-Step Verification if not already enabled
3. Generate an App Password:
   - Go to Security > 2-Step Verification > App passwords
   - Select "Mail" and your device
   - Copy the generated password
   - Add to your `.env` file as `MAIL_PASSWORD`

### Environment Setup
1. Create `.env` file in `GoodJobBackEnd` directory:
```env
# Google OAuth2
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret

# Facebook OAuth2
FACEBOOK_CLIENT_ID=your_facebook_client_id
FACEBOOK_CLIENT_SECRET=your_facebook_client_secret

# JWT
JWT_SECRET=your_jwt_secret

# Email
MAIL_USERNAME=your_gmail_address
MAIL_PASSWORD=your_app_specific_password
```

### Running Backend
1. Open project in IntelliJ IDEA
2. Wait for Gradle to sync and download dependencies
3. Run the application using IntelliJ's built-in tools:
   - Find `GoodJobApplication.java`
   - Click the green play button
   - Server will start on `http://localhost:8080`

## Frontend Setup (GoodJobWeb)

### Prerequisites
1. Install Node.js (LTS version)
2. Install Yarn package manager

### Installation
1. Open terminal in `GoodJobWeb` directory
2. Install dependencies:
```bash
yarn install
```

### Running Frontend
1. Start development server:
```bash
yarn dev
```
2. Press 'o' to open in browser or visit `http://localhost:5173`

## Additional Notes
- Make sure MySQL server is running before starting the backend
- Keep your `.env` file secure and never commit it to git
- For development, both frontend and backend servers need to be running simultaneously
- Check application.properties for database configuration if needed
- Backend runs on port 8080, frontend on port 5173

## Troubleshooting
- If database connection fails, check MySQL credentials and database existence
- If OAuth login fails, verify credentials in `.env` file
- For email issues, make sure Gmail App Password is correctly configured
- For frontend build issues, try deleting `node_modules` and running `yarn install` again 