# 🏠 HomeRent - House Rental Management System

A modern, full-stack web application for managing house rentals in Tamil Nadu, India. Connect house owners with seekers seamlessly!

![Status](https://img.shields.io/badge/status-active-success.svg)
![Platform](https://img.shields.io/badge/platform-web-blue.svg)

## ✨ Features

### 👤 For Seekers
- 🔍 **Browse Houses** - Search and filter houses across all Tamil Nadu districts
- 📋 **Advanced Filters** - Filter by district, bedrooms, rent range, and keywords
- 📸 **Photo Galleries** - View multiple photos of each property
- 📅 **Book Houses** - Request bookings with your details (name, mobile, dates)
- 📊 **Track Bookings** - View all your booking requests (Pending/Accepted/Rejected)
- 💰 **Transparent Pricing** - See rent estimates before booking

### 🏘️ For Owners
- ➕ **List Properties** - Add your houses with photos, details, and pricing
- 📤 **Image Upload** - Upload up to 5 photos via Cloudinary
- ✏️ **Edit Listings** - Update your property details anytime
- 🗑️ **Delete Properties** - Remove listings when needed
- 📬 **Manage Requests** - View booking requests with seeker details
- ✅ **Accept/Reject** - Approve or decline booking requests
- 📈 **Dashboard** - Track total houses, pending, and accepted bookings

## 🛠️ Tech Stack

### Frontend
- 🌐 **HTML5** - Semantic markup
- 🎨 **CSS3** - Custom responsive design
- ⚡ **JavaScript (ES6+)** - Modern vanilla JS
- 🔥 **Firebase SDK** - Authentication & Firestore database

### Backend
- 🐍 **Python 3.x** - Backend runtime
- 🌶️ **Flask** - Web framework
- ☁️ **Cloudinary** - Image hosting & CDN
- 🔐 **python-dotenv** - Environment variables

### Database
- � **Cloud Firestore** - NoSQL database
- 🔐 **Firebase Auth** - User authentication

## 📁 Project Structure

```
house-rental-app/
├── 📂 backend/
│   ├── app.py              # Flask server
│   ├── .env                # Environment variables (Cloudinary keys)
│   └── requirements.txt    # Python dependencies
│
├── 📂 frontend/
│   ├── 📂 css/
│   │   └── style.css       # All styles with responsive design
│   ├── 📂 js/
│   │   ├── auth.js         # Authentication logic
│   │   ├── browse.js       # Seeker browsing & filtering
│   │   ├── bookings.js     # House details & booking management
│   │   ├── houses.js       # Owner property management
│   │   ├── firebase.js     # Firebase initialization
│   │   ├── config.js       # Firebase config
│   │   └── utils.js        # Helper functions
│   ├── index.html          # Landing page
│   ├── login.html          # Login page
│   ├── register.html       # Registration page
│   ├── owner_dashboard.html    # Owner dashboard
│   ├── seeker_browse.html      # House browsing page
│   ├── house_details.html      # Property details page
│   ├── my_bookings.html        # Seeker's bookings
│   ├── add_house.html          # Add new property
│   └── edit_house.html         # Edit property
│
└── README.md               # This file!
```

## 🚀 Installation & Setup

### Prerequisites
- 🐍 Python 3.x installed
- 🔥 Firebase project created
- ☁️ Cloudinary account (for image uploads)

### Step 1: Clone the Repository
```bash
git clone <your-repo-url>
cd house-rental-app
```

### Step 2: Backend Setup
```bash
cd backend
pip install -r requirements.txt
```

Create a `.env` file in the `backend` folder:
```env
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

### Step 3: Firebase Setup

1. 🌐 Go to [Firebase Console](https://console.firebase.google.com/)
2. ➕ Create a new project
3. 🔥 Enable **Firestore Database**
4. 🔐 Enable **Email/Password Authentication**
5. ⚙️ Get your Firebase config from Project Settings
6. 📝 Update `frontend/js/config.js` with your Firebase credentials

### Step 4: Create Firestore Indexes

Go to Firebase Console → Firestore Database → Indexes tab and create these 3 indexes:

**Index 1: Houses by Owner**
- Collection: `houses`
- Fields: `owner_uid` (Ascending), `created_at` (Descending)

**Index 2: Bookings by Owner**
- Collection: `bookings`
- Fields: `owner_uid` (Ascending), `created_at` (Descending)

**Index 3: Bookings by Seeker**
- Collection: `bookings`
- Fields: `seeker_uid` (Ascending), `created_at` (Descending)

### Step 5: Run the Application

Start the Flask backend:
```bash
cd backend
python app.py
```

🌐 Open your browser and navigate to:
```
http://localhost:5000
```

## 📊 Database Schema

### 👥 Users Collection
```javascript
{
  uid: string,           // Firebase Auth UID
  email: string,         // User email
  name: string,          // Full name
  role: "owner" | "seeker"  // User type
}
```

### 🏘️ Houses Collection
```javascript
{
  owner_uid: string,      // Reference to owner
  title: string,          // Property title
  description: string,    // Property description
  district: string,       // Tamil Nadu district
  place: string,          // Specific location
  rent_per_month: number, // Monthly rent in INR
  bedrooms: number,       // Number of bedrooms
  bathrooms: number,      // Number of bathrooms
  available_from: timestamp,  // Availability date
  images: string[],       // Cloudinary image URLs
  created_at: timestamp   // Creation timestamp
}
```

### 📅 Bookings Collection
```javascript
{
  house_id: string,       // Reference to house
  seeker_uid: string,     // Reference to seeker
  owner_uid: string,      // Reference to owner
  seeker_name: string,    // Seeker's name
  seeker_mobile: string,  // Seeker's mobile (10 digits)
  start_date: timestamp,  // Booking start date
  end_date: timestamp,    // Booking end date
  status: "pending" | "accepted" | "rejected",
  created_at: timestamp   // Request timestamp
}
```

## 🎯 Usage Guide

### For Seekers 👤

1. **Register**: Click "Get Started" → Register as Seeker
2. **Browse**: View all available houses  
3. **Filter**: Use filters to narrow down options
4. **View Details**: Click "View Details" on any house
5. **Book**: Click "Book Now", fill in your details
6. **Track**: Check "My Bookings" to see request status

### For Owners 🏘️

1. **Register**: Click "Get Started" → Register as Owner
2. **Add Property**: Click "Add New House"
3. **Upload Photos**: Add up to 5 photos
4. **Fill Details**: Enter property information
5. **Manage Requests**: View booking requests on dashboard
6. **Accept/Reject**: Respond to booking requests
7. **Edit/Delete**: Update or remove your listings

## 🎨 Features in Detail

### 🔍 Smart Filtering
- **By District**: Filter from 38 Tamil Nadu districts
- **By Bedrooms**: 1 BHK, 2 BHK, 3 BHK, 4+ BHK
- **By Rent**: Set minimum and maximum rent range
- **Search**: Search by keywords in title, place, or description
- **Sort**: Latest first, Price low-to-high, high-to-low

### 📱 Responsive Design
- ✅ Desktop (1200px+)
- ✅ Tablet (768px - 992px)
- ✅ Mobile (480px - 768px)
- ✅ Small Mobile (<480px)
- ✅ Landscape mode optimization

### 🔒 Security
- 🔐 Firebase Authentication
- 🛡️ Role-based access control
- ✅ Input validation
- 🚫 Protected routes

## 🐛 Troubleshooting

### "Error loading properties"
- ✅ Make sure you've created all 3 Firestore indexes
- ⏰ Wait 1-2 minutes for indexes to build

### Images not uploading
- ✅ Check Cloudinary credentials in `.env`
- ✅ Verify Cloudinary account is active

### Firebase errors
- ✅ Verify Firebase config in `config.js`
- ✅ Check Firestore and Auth are enabled

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 👨‍� Developer

Developed with ❤️ using modern web technologies

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

---

Made with 💙 for connecting home seekers and owners across Tamil Nadu! 🏠✨
