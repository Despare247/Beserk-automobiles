# Beserk Automobiles - Setup & Testing Guide

## 📋 Prerequisites
- **Node.js** v18+ (Download from [nodejs.org](https://nodejs.org))
- **npm** (comes with Node.js)
- **MongoDB** (optional - for full backend testing)
  - Local: Download from [mongodb.com](https://www.mongodb.com/try/download/community)
  - Cloud: Use [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)

## 🚀 Quick Start Setup

### Step 1: Install Dependencies

```bash
# Install root dependencies
npm install

# Install frontend dependencies
cd client
npm install
cd ..

# Install server dependencies
cd server
npm install
cd ..
```

### Step 2: Configure Environment (Optional for testing UI)

The `.env` file is already created in the `server` folder with default settings.

If you want to use MongoDB:
1. Open `server/.env`
2. Update `MONGODB_URI` with your MongoDB connection string:
   ```
   MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/beserk-automobiles
   ```

### Step 3: Start the Application

**Option A: Run Both Frontend & Backend (Recommended)**
```bash
npm run dev
```
This will start:
- Frontend: http://localhost:5173
- Backend: http://localhost:5000

**Option B: Run Separately**

Frontend only:
```bash
cd client
npm run dev
```

Backend only:
```bash
cd server
npm run dev
```

## 🧪 Testing the Application

### Frontend Features to Test

#### 1. **Home Page** (http://localhost:5173)
- ✅ Hero section with "Shop Now" and "Book Service" buttons
- ✅ Features section with 4 cards
- ✅ Categories section (Vehicles, Parts, Accessories)
- ✅ Services preview section

#### 2. **Dark/Light Theme**
- Click the 🌙 icon in navbar to toggle theme
- ✅ All colors should change smoothly
- ✅ Theme should persist across pages

#### 3. **Product Catalog** (http://localhost:5173/products)
- ✅ Browse all products (6 mock products included)
- ✅ Filter by category (All, Vehicles, Parts, Accessories)
- ✅ Filter by price range (0-$100,000)
- ✅ Search products by name
- ✅ Add products to cart
- ✅ Reset filters button

#### 4. **Shopping Cart** (http://localhost:5173/cart)
- ✅ View cart items with emoji icons
- ✅ Increase/decrease item quantities
- ✅ Remove items from cart
- ✅ See automatic calculations:
  - Subtotal
  - Free shipping for orders > $100
  - 10% tax calculation
  - Total price
- ✅ "Proceed to Checkout" button (requires login)

#### 5. **Authentication**

**Login Page** (http://localhost:5173/login)
- Test credentials (any email/password):
  - Email: test@example.com
  - Password: password123
- ✅ Successful login redirects to home
- ✅ User name displays in navbar
- ✅ Logout button appears

**Register Page** (http://localhost:5173/register)
- ✅ Create account with name, email, password
- ✅ Password confirmation validation
- ✅ Redirects to home on success
- ✅ Links between Login/Register pages

#### 6. **Service Booking** (http://localhost:5173/services)
- ✅ View 6 services with prices and durations
- ✅ Click "Book Now" button
- ✅ Modal opens with service booking form
- ✅ Select date and time
- ✅ Confirm booking
- ✅ Modal closes on success

#### 7. **Admin Dashboard** (http://localhost:5173/admin)
- Note: Only visible if logged in as admin user
- Manual test: Edit `Login.jsx` and set `isAdmin: true`
- ✅ Overview tab with statistics
- ✅ Products management table
- ✅ Orders management table
- ✅ Service bookings table

#### 8. **Responsive Design**
- ✅ Test on mobile (resize browser to 375px width)
- ✅ Test on tablet (768px width)
- ✅ Test on desktop (1400px+ width)
- ✅ All layouts should be properly aligned

#### 9. **Navigation**
- ✅ Navbar links work (Home, Shop, Services, Admin)
- ✅ Footer links work
- ✅ Cart counter updates
- ✅ Theme toggle works

### Backend API Testing (Optional)

If MongoDB is running, test these endpoints:

```bash
# Test API connection
curl http://localhost:5000/api

# Response should show: {"message":"Beserk Automobiles API"}
```

## 📊 Test Checklist

### UI/UX Tests
- [ ] All pages load without errors
- [ ] Theme toggle works smoothly
- [ ] Navigation is intuitive
- [ ] Forms validate input
- [ ] Buttons have hover effects
- [ ] Mobile responsive design works

### Feature Tests
- [ ] Products filter correctly
- [ ] Cart calculations are accurate
- [ ] Login/Register flow works
- [ ] Service booking modal appears
- [ ] Admin dashboard displays (with admin user)
- [ ] Search functionality works

### Data Persistence Tests
- [ ] Cart persists on page refresh
- [ ] User stays logged in (localStorage)
- [ ] Theme preference persists

## 🐛 Troubleshooting

### Port Already in Use
```bash
# Kill process on port 5000 (backend)
lsof -ti:5000 | xargs kill -9

# Kill process on port 5173 (frontend)
lsof -ti:5173 | xargs kill -9
```

### Dependencies Not Installing
```bash
# Clear npm cache
npm cache clean --force

# Delete node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

### MongoDB Connection Errors
- Ensure MongoDB is running locally or use MongoDB Atlas
- Check connection string in `server/.env`
- For local MongoDB: `mongodb://localhost:27017/beserk-automobiles`

### Hot Reload Not Working
- Restart the dev server
- Check if port 5173 is available

## 📝 Mock Data Included

### Products (6 items)
- BMW 3 Series - $25,000
- Toyota Corolla - $18,000
- Engine Oil - $45
- Brake Pads - $89
- LED Headlights - $199
- Car Seat Covers - $120

### Services (6 services)
- Oil Change - $45
- Tire Rotation - $65
- Brake Inspection - $85
- Battery Check - $35
- Full Engine Tune-up - $250
- Air Filter Replacement - $55

## 🎯 Next Steps

1. ✅ Setup complete - run `npm run dev`
2. Test all features listed above
3. Implement backend API endpoints in `server/src/`
4. Connect frontend to real API endpoints
5. Add database operations for products, orders, services
6. Implement JWT authentication
7. Deploy to production

## 📞 Support

For issues or questions:
1. Check the console for error messages
2. Review the component files in `client/src/`
3. Check API routes in `server/src/server.js`
4. Ensure all dependencies are installed correctly

---

**Beserk Automobiles** © 2024 - Ready to drive! 🚗
