# EV ChargeNet Dashboard

A comprehensive web-based management system for electric vehicle charging station networks. This application provides a full-stack solution with user authentication, vehicle management, charging session tracking, and station monitoring.

## 🚀 Features

- **User Authentication**: Login and signup functionality with profile management
- **Dashboard**: Real-time overview of charging activity, energy consumption, and costs
- **Vehicle Management**: Track and manage multiple electric vehicles
- **Charging Sessions**: Monitor and filter charging history with detailed receipts
- **Station Locator**: Browse nearby charging stations with facilities information
- **Payment Tracking**: View payment preferences and total spending
- **Maintenance Records**: Track maintenance schedules and service history
- **Facilities Overview**: Check available amenities at charging stations

## 📋 Prerequisites

- Node.js (v18 or higher)
- MySQL Server (v5.7 or higher)
- npm or yarn package manager

## 🛠️ Installation

### 1. Clone the Repository

```bash
git clone <repository-url>
cd ev_charging_gui
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Database Setup

1. Create a MySQL database named `ev_charging_station_network`
2. Import your database schema (tables, stored procedures, functions, triggers)
3. Update database credentials in `server.js`:

```javascript
const db = mysql.createPool({
  host: 'localhost',
  user: 'root',
  password: 'your_password', // Update this
  database: 'ev_charging_station_network',
  waitForConnections: true,
  connectionLimit: 10,
  queueLimit: 0
});
```

### 4. Required Database Tables

The application expects the following tables:
- `user` - User accounts
- `user_payment` - Payment preferences
- `vehicle` - Vehicle information
- `charging_station` - Station locations
- `station_facility` - Station amenities
- `charger` - Charging equipment
- `maintenance` - Maintenance records
- `charging_session` - Charging history
- `services` - Service contacts
- `userinformation` - Additional user data
- `uservehiclestation` - Relationship data

### 5. Required Database Functions/Procedures

- **Function**: `get_total_spent(user_id)` - Calculates total spending per user
- **Procedure**: `get_user_history(user_id)` - Retrieves user charging history
- **Trigger**: Auto-calculate cost in `charging_session` table based on energy consumed

## 🚀 Running the Application

### Start the Backend Server

```bash
npm start
```

The server will start on `http://localhost:3000`

### Access the Frontend

Open `index.html` in a web browser or serve it using a local web server:

```bash
# Using Python
python -m http.server 8000

# Using Node.js http-server (install globally: npm install -g http-server)
http-server -p 8000
```

Then navigate to `http://localhost:8000`

## 📁 Project Structure

```
ev_charging_gui/
├── server.js           # Express backend server
├── index.html          # Main HTML interface
├── script.js           # Frontend JavaScript logic
├── style.css           # Styling and themes
├── package.json        # Project dependencies
├── db_config.js        # Database configuration (legacy)
└── README.md           # This file
```

## 🔌 API Endpoints

### Generic CRUD Operations

For each table: `user`, `vehicle`, `charging_station`, etc.

- `GET /api/<table>` - Get all records
- `GET /api/<table>/:id` - Get record by ID
- `POST /api/<table>` - Create new record
- `PUT /api/<table>/:id` - Update record
- `DELETE /api/<table>/:id` - Delete record

### Special Endpoints

- `GET /api/total_spent/:uid` - Get total spending for a user
- `GET /api/user_history/:uid` - Get charging history for a user
- `POST /api/charging_session_insert` - Insert charging session (triggers auto-cost calculation)
- `GET /api/schema/:table` - Get column names for a table

## 👤 User Guide

### First Time Setup

1. Open the application in your browser
2. Click "Create account" on the login screen
3. Fill in your details (name, email, phone, address)
4. Optionally add a vehicle during signup
5. Click "Create account" to register and auto-login

### Using the Dashboard

- **Dashboard**: View energy consumption, costs, and recent sessions
- **My Vehicles**: Manage your registered vehicles
- **Charging Sessions**: Filter and view your charging history
- **Nearby Stations**: Browse available charging stations
- **Payment Summary**: Track your spending and payment methods
- **Profile Settings**: Update your personal information

### Starting a Charging Session

1. Click "Start New Charging Session" button
2. Enter Vehicle ID, Charger ID, and Energy Consumed
3. The system will automatically calculate the cost

## 🎨 UI Features

- **Responsive Design**: Works on desktop and mobile devices
- **Interactive Charts**: Visualize energy consumption with Chart.js
- **Real-time Updates**: Data refreshes when navigating between views
- **Dark Sidebar**: Modern, professional interface
- **Error Handling**: Debug console for troubleshooting

## 🔐 Security Notes

- Currently uses localStorage for session management (client-side only)
- No password authentication implemented (email-based login only)
- **For production use**: Implement proper authentication with JWT tokens, password hashing, and secure session management

## 🐛 Troubleshooting

### Server Won't Start

- Check that MySQL is running
- Verify database credentials in `server.js`
- Ensure port 3000 is available

### Database Connection Errors

- Confirm database name matches (`ev_charging_station_network`)
- Check MySQL user permissions
- Verify all required tables exist

### Frontend Not Loading Data

- Check browser console for errors
- Ensure backend server is running on port 3000
- Verify CORS is enabled (already configured in server.js)

### Debug Console

The application includes a debug console that appears at the bottom-right when errors occur. This helps identify JavaScript issues during development.

## 📦 Dependencies

### Backend
- **express** (5.1.0): Web framework
- **mysql2** (3.15.3): MySQL database driver
- **cors** (2.8.5): Cross-origin resource sharing

### Frontend
- **Chart.js** (CDN): Data visualization

## 🔄 Future Enhancements

- Implement proper authentication with passwords
- Add real-time charging status monitoring
- Integrate payment gateway
- Add map visualization for stations
- Mobile app development
- Admin dashboard for station operators
- Email notifications for completed sessions
- Generate PDF receipts

## 📄 License

ISC

## 👥 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📞 Support

For issues or questions, please check the debug console or contact the development team.

---

**Built with ⚡ for the EV Charging Community**
