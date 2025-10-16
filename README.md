# Final-Project
Community Health Reporting Platform
# Community Health Reporting Platform

A web application that enables community members to report health issues and allows health workers and administrators to manage and track these reports efficiently.

##  Features

### For Community Members
- **User Registration & Authentication** - Secure signup and login system
- **Health Issue Reporting** - Submit detailed health reports with categories and priorities
- **Report Tracking** - View personal report history and status updates
- **Real-time Updates** - See updates from health workers on submitted reports

### For Health Workers & Administrators
- **Dashboard** - View all community health reports in one place
- **Report Management** - Update report status and add progress comments
- **Priority Handling** - Manage reports based on severity and urgency
- **Role-based Access** - Different permissions for community members, health workers, and admins

### Technical Features
- **Responsive Design** - Works on desktop, tablet, and mobile devices
- **RESTful API** - Clean API structure for future extensions
- **JWT Authentication** - Secure token-based authentication
- **MySQL Database** - Reliable data storage with proper relationships

## Technology Stack

### Frontend
- **HTML5** - Semantic markup
- **CSS3** - Modern styling with Flexbox/Grid
- **Vanilla JavaScript** - ES6+ features, async/await
- **Responsive Design** - Mobile-first approach

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web application framework
- **MySQL** - Relational database
- **JWT** - JSON Web Tokens for authentication
- **bcryptjs** - Password hashing
- **Express Validator** - Input validation

##  Prerequisites

Before running this application, ensure you have the following installed:

- **Node.js** (v14 or higher)
- **MySQL** (v5.7 or higher)
- **npm** (usually comes with Node.js)

## Installation & Setup

### 1. Clone the Repository
```bash
git clone <repository-url>
cd community-health-app
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Database Setup

#### Create MySQL Database
```sql
CREATE DATABASE community_health;
```

#### Run Database Schema
Execute the SQL commands from the `database-schema.sql` file (located in the project root) in your MySQL client:

```bash
mysql -u your_username -p community_health < database-schema.sql
```

### 4. Environment Configuration

Create a `.env` file in the root directory:

```env
# Database Configuration
DB_HOST=localhost
DB_USER=your_mysql_username
DB_PASSWORD=your_mysql_password
DB_NAME=community_health

# JWT Secret
JWT_SECRET=your_very_secure_jwt_secret_key_here

# Server Port
PORT=3000
```

### 5. Start the Application

#### Development Mode
```bash
npm run dev
```

#### Production Mode
```bash
npm start
```

The application will be available at `http://localhost:3000`

## Project Structure

```
community-health-app/
├── public/                 # Frontend assets
│   ├── css/
│   │   └── style.css      # Main stylesheet
│   ├── js/
│   │   └── script.js      # Frontend JavaScript
│   └── index.html         # Main HTML file
├── server/                # Backend code
│   ├── config/
│   │   └── database.js    # Database configuration
│   ├── controllers/       # Route controllers
│   │   ├── authController.js
│   │   └── reportController.js
│   ├── models/           # Data models
│   │   ├── User.js
│   │   └── Report.js
│   ├── routes/           # API routes
│   │   ├── auth.js
│   │   └── reports.js
│   ├── middleware/       # Custom middleware
│   │   └── auth.js
│   └── server.js         # Main server file
├── package.json
├── .env                  # Environment variables
└── README.md
```

## Database Schema

### Users Table
Stores user authentication and role information
- `id`, `username`, `email`, `password`, `role`, `created_at`, `updated_at`

### Reports Table
Main table for health issue reports
- `id`, `user_id`, `title`, `description`, `location`, `category`, `priority`, `status`, `latitude`, `longitude`, `image_url`, `created_at`, `updated_at`

### Report Updates Table
Tracks comments and status changes on reports
- `id`, `report_id`, `user_id`, `comment`, `status_change`, `created_at`

##  API Endpoints

### Authentication Routes
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/profile` - Get user profile

### Report Routes
- `POST /api/reports` - Create new health report
- `GET /api/reports` - Get all reports (with authentication)
- `GET /api/reports/my-reports` - Get user's own reports
- `GET /api/reports/:id` - Get specific report details
- `POST /api/reports/:id/updates` - Add update to report (health workers/admins only)

## User Roles

### Community Member
- Register and login
- Submit health reports
- View all reports
- Track personal reports

### Health Worker
- All Community Member privileges
- Add updates to reports
- Change report status
- Monitor community health issues

### Administrator
- All Health Worker privileges
- User management (future enhancement)
- System configuration (future enhancement)

## Report Categories

1. **Sanitation** - Waste management, cleanliness issues
2. **Disease Outbreak** - Infectious disease concerns
3. **Health Facility** - Clinic/hospital related issues
4. **Environmental** - Pollution, water quality, etc.
5. **Other** - Any other health concerns

## Priority Levels

- **Critical** - Immediate attention required
- **High** - Urgent attention needed
- **Medium** - Standard priority (default)
- **Low** - Minor issues

## Usage Guide

### For Community Members

1. **Register/Login**: Create an account or login to existing account
2. **Submit Report**: Click "Report Issue" and fill out the form with:
   - Title and description
   - Category and priority
   - Location details
3. **Track Progress**: View "My Reports" to see status updates
4. **Browse Reports**: View all community reports on the home page

### For Health Workers/Admins

1. **Login** with health worker/admin credentials
2. **Review Reports**: Browse all reports on the dashboard
3. **Manage Reports**: Click on any report to view details and:
   - Add comments and updates
   - Change report status
   - Monitor resolution progress

## 🔧 Development

### Adding New Features

1. **Backend Changes**:
   - Add new model in `server/models/`
   - Create controller in `server/controllers/`
   - Define routes in `server/routes/`
   - Update database schema if needed

2. **Frontend Changes**:
   - Update HTML in `public/index.html`
   - Add styles in `public/css/style.css`
   - Implement functionality in `public/js/script.js`

### Database Modifications
When modifying the database schema:
1. Update the SQL schema file
2. Modify corresponding model files
3. Update any affected controllers

## Troubleshooting

### Common Issues

1. **Database Connection Error**
   - Verify MySQL is running
   - Check `.env` file credentials
   - Ensure database exists

2. **Authentication Issues**
   - Clear browser localStorage
   - Check JWT secret in `.env`
   - Verify user exists in database

3. **Port Already in Use**
   - Change PORT in `.env` file
   - Kill existing process: `npx kill-port 3000`

### Logs
- Check console for error messages
- Monitor MySQL query logs if needed
- Use browser developer tools for frontend issues

##  Future Enhancements

- [ ] Image upload functionality for reports
- [ ] Email/SMS notifications
- [ ] Map integration for location visualization
- [ ] Analytics dashboard with charts
- [ ] Mobile application
- [ ] Multi-language support
- [ ] Report exporting
- [ ] User management panel
- [ ] API rate limiting
- [ ] Automated report reminders

##  Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/new-feature`
3. Commit changes: `git commit -am 'Add new feature'`
4. Push to the branch: `git push origin feature/new-feature`
5. Submit a pull request

### Code Style Guidelines
- Use consistent indentation (2 spaces)
- Follow JavaScript ES6+ standards
- Comment complex logic
- Maintain responsive design principles

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support and questions:
1. Check the troubleshooting section above
2. Review API documentation
3. Create an issue in the repository
4. Contact the development team

## Acknowledgments

- Built with Node.js and Express.js
- MySQL for reliable data storage
- Modern CSS for responsive design
- JWT for secure authentication

---

Note: This is a community health application designed to improve public health reporting and response. Always ensure proper data privacy measures are implemented when deploying in production environments.
