# 🚀 Mentorship Under 40 - Landing Page

A modern, responsive landing page for Dr. Kusi-Boadum's mentorship program, built with Node.js, MongoDB, and modern web technologies.

## ✨ Features

- **Responsive Design** - Works perfectly on all devices
- **Modern UI/UX** - Beautiful gradients, animations, and interactions
- **Registration System** - Collect and manage mentorship applications
- **Admin Panel** - Complete dashboard for managing registrations
- **Database Integration** - MongoDB backend with Mongoose ODM
- **RESTful API** - Clean, organized endpoints
- **JWT Authentication** - Secure admin access
- **CSV Export** - Download registration data
- **Search & Filter** - Advanced admin features

## 🛠️ Tech Stack

### Frontend
- **HTML5** - Semantic markup
- **CSS3** - Modern styling with gradients and animations
- **JavaScript (ES6+)** - Interactive features and API calls
- **Font Awesome** - Beautiful icons

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling
- **JWT** - JSON Web Token authentication
- **bcryptjs** - Password hashing
- **CORS** - Cross-origin resource sharing
- **Helmet** - Security middleware

## 📁 Project Structure

```
mentorship-landing-page/
├── public/                 # Static files served by Express
│   ├── index.html         # Main landing page
│   ├── admin.html         # Admin panel
│   ├── daddy.png          # Mentor image
│   └── mentorship-1.png   # Logo image
├── models/                 # MongoDB schemas
│   └── Registration.js    # Registration data model
├── routes/                 # API endpoints
│   ├── registration.js    # Registration CRUD operations
│   └── admin.js          # Admin operations & authentication
├── server.js              # Main server file
├── package.json           # Dependencies & scripts
├── env.example            # Environment variables template
├── README.md              # This file
└── NODEJS_DEPLOYMENT_GUIDE.md  # Deployment instructions
```

## 🚀 Quick Start

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local or Atlas)
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/mentorship-landing-page.git
   cd mentorship-landing-page
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment setup**
   ```bash
   # Copy environment template
   cp env.example .env
   
   # Edit .env with your settings
   nano .env
   ```

4. **Start MongoDB** (if using local)
   ```bash
   # Windows: Start MongoDB service
   # Mac/Linux:
   sudo systemctl start mongod
   sudo systemctl enable mongod
   ```

5. **Run the application**
   ```bash
   # Development mode
   npm run dev
   
   # Production mode
   npm start
   ```

6. **Access the application**
   - Landing Page: `http://localhost:3000`
   - Admin Panel: `http://localhost:3000/admin.html`
   - API Health: `http://localhost:3000/api/health`

## 🔧 Configuration

### Environment Variables

Create a `.env` file in the root directory:

```env
# Server Configuration
PORT=3000
NODE_ENV=development

# MongoDB Configuration
MONGODB_URI=mongodb://localhost:27017/mentorship_db

# Admin Authentication
ADMIN_PASSWORD=your_secure_admin_password_here
JWT_SECRET=your_super_secret_jwt_key_here

# CORS Configuration
ALLOWED_ORIGINS=http://localhost:3000,http://localhost:5000
```

### MongoDB Setup

#### Local MongoDB
```bash
# Install MongoDB
# Windows: Download from mongodb.com
# Mac: brew install mongodb-community
# Linux: sudo apt install mongodb

# Start MongoDB
sudo systemctl start mongod
sudo systemctl enable mongod
```

#### MongoDB Atlas (Cloud)
1. Create account at [MongoDB Atlas](https://www.mongodb.com/atlas)
2. Create a free cluster
3. Get connection string
4. Update `MONGODB_URI` in `.env`

## 📱 Usage

### Landing Page
- **Home Section** - Hero banner with call-to-action
- **About Section** - Mentor information and image
- **Program Features** - What participants will gain
- **Registration Form** - Application submission
- **Contact Section** - Contact information and social links

### Admin Panel
- **Login** - Secure admin authentication
- **Dashboard** - Statistics and overview
- **Registrations** - View, edit, and manage applications
- **Search & Filter** - Find specific registrations
- **Export** - Download data as CSV
- **Status Management** - Approve/reject applications

### API Endpoints

#### Registration
- `POST /api/registration` - Create new registration
- `GET /api/registration/:id` - Get registration by ID
- `PUT /api/registration/:id` - Update registration
- `DELETE /api/registration/:id` - Delete registration

#### Admin
- `POST /api/admin/login` - Admin authentication
- `GET /api/admin/registrations` - Get all registrations
- `GET /api/admin/stats` - Get statistics
- `GET /api/admin/export` - Export to CSV
- `PATCH /api/admin/registrations/:id/status` - Update status

## 🎨 Customization

### Colors
The design uses a modern gradient color scheme:
- Primary: `#8B2CF5` (Purple)
- Secondary: `#E91E63` (Pink)
- Accent: `#FF6B35` (Orange)

### Images
- **Logo**: `mentorship-1.png` (50x50px, circular)
- **Mentor**: `daddy.png` (400x400px, rounded corners)

### Content
Edit the HTML files to customize:
- Text content
- Contact information
- Social media links
- Program features

## 🔒 Security Features

- **JWT Authentication** - Secure admin access
- **Input Validation** - Server-side data validation
- **SQL Injection Protection** - Mongoose ODM protection
- **CORS Configuration** - Controlled cross-origin access
- **Rate Limiting** - API abuse prevention
- **Helmet Security** - HTTP security headers

## 📊 Database Schema

### Registration Model
```javascript
{
  fullName: String,      // Required
  email: String,         // Required, unique
  phone: String,         // Required
  age: String,           // Required (18-25, 26-30, 31-35, 36-40)
  occupation: String,    // Optional
  goals: String,         // Required (min 10 chars)
  experience: String,    // Optional
  status: String,        // pending, approved, rejected
  notes: String,         // Admin notes
  createdAt: Date,       // Auto-generated
  updatedAt: Date        // Auto-generated
}
```

## 🚀 Deployment

For detailed deployment instructions, see [NODEJS_DEPLOYMENT_GUIDE.md](./NODEJS_DEPLOYMENT_GUIDE.md)

### Quick Deployment Options
1. **VPS Hosting** - DigitalOcean, Linode, Vultr ($3.50-20/month)
2. **Cloud Hosting** - AWS, Google Cloud, Heroku
3. **MongoDB Atlas** - Cloud database (free tier available)

## 🧪 Testing

### Manual Testing
1. **Landing Page**: Test responsiveness on different devices
2. **Registration Form**: Submit test data
3. **Admin Panel**: Login and manage registrations
4. **API Endpoints**: Use Postman or browser

### API Testing
```bash
# Health check
curl http://localhost:3000/api/health

# Test registration
curl -X POST http://localhost:3000/api/registration \
  -H "Content-Type: application/json" \
  -d '{"fullName":"Test User","email":"test@example.com","phone":"1234567890","age":"18-25","goals":"Test goals"}'
```

## 📝 Scripts

```json
{
  "start": "node server.js",        // Production
  "dev": "nodemon server.js"        // Development with auto-reload
}
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Support

- **Documentation**: Check this README and deployment guide
- **Issues**: Create an issue on GitHub
- **Email**: Contact the development team

## 🙏 Acknowledgments

- Dr. Kusi-Boadum for the mentorship vision
- Font Awesome for beautiful icons
- MongoDB and Node.js communities
- Express.js framework contributors

---

**Built with ❤️ for empowering the next generation of leaders under 40**
