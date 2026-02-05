# ARay - Augmented Reality Eyewear Try-On Application

## Overview

**ARay** is an innovative Android application that combines **Augmented Reality (AR)** technology with e-commerce to provide customers with a virtual eyewear try-on experience. The app allows users to visualize different types of glasses (eyeglasses, sunglasses, reading glasses, and power glasses) in real-time using their device's camera before making a purchase. It features a complete shopping ecosystem with user authentication, product catalog, shopping cart, order management, and payment integration.

**Tagline:** "We Care For You!" - Get A Look

---

## Key Features

### User Features
- **Augmented Reality Try-On**: Use AR technology to virtually try on different eyewear styles in real-time
- **User Authentication**: Secure login and registration with multi-step signup process (3-step registration with OTP verification)
- **Product Catalog**: Browse and search through various eyewear categories:
  - Eye Glasses
  - Sun Glasses
  - Reading Glasses
  - Power Glasses
- **Featured Products**: View trending and featured eyewear items
- **Shopping Cart**: Add, modify quantities, and manage items before checkout
- **Search Functionality**: Search for specific products across the catalog
- **Order Management**: View purchase history and order details
- **Password Recovery**: Secure password reset via email or SMS
- **User Profile & Settings**: Manage account information and preferences
- **Session Management**: Persistent login sessions with secure session handling

### Admin Features
- **Admin Dashboard**: Dedicated admin interface for store management
- **Product Management**: Add new eyewear products with details and images
- **Product Images**: Upload and manage product images
- **Order Management**: View and process new customer orders
- **Order Details**: Track individual order information and status
- **Inventory Control**: Manage product categories and listings

### Payment Integration
- **Razorpay Integration**: Secure payment gateway for online transactions
- **Order Confirmation**: Instant order confirmation after successful payment
- **Purchase History**: Access to all previous purchases and invoices

---

## Technical Stack

### Architecture & Framework
- **Language**: Java (with Kotlin stdlib support)
- **Target API**: Android 24 (Minimum) - 29 (Target)
- **Build System**: Gradle
- **IDE**: Android Studio (with AndroidX support)

### Core Libraries & Dependencies

**UI & Design**
- androidx.appcompat:appcompat:1.2.0
- androidx.constraintlayout:constraintlayout:2.0.4
- com.google.android.material:material:1.3.0
- androidx.recyclerview:recyclerview:1.1.0
- androidx.cardview:cardview:1.0.0
- com.airbnb.android:lottie:3.4.1 (animations)
- com.cuberto:liquid-swipe:1.0.0 (liquid swipe animations)

**Augmented Reality**
- com.google.ar.sceneform:assets:1.17.1
- com.google.ar.sceneform.ux:sceneform-ux:1.17.1
- ARCore support (Android hardware.camera.ar required)

**Backend & Database**
- com.google.firebase:firebase-database:19.6.0
- com.google.firebase:firebase-auth:20.0.2
- com.google.firebase:firebase-storage:19.2.1
- com.firebaseui:firebase-ui-database:6.2.1

**Image & Media Handling**
- com.github.bumptech.glide:glide:4.11.0
- com.squareup.picasso:picasso:2.71828
- de.hdodenhof:circleimageview:3.1.0
- com.theartofdev.edmodo:android-image-cropper:2.8.+

**UI Components**
- com.hbb20:ccp:2.3.1 (Country Code Picker)
- com.chaos.view:pinview:1.4.3 (PIN/OTP input)
- com.cepheuen.elegant-number-button:lib:1.0.2 (Quantity selector)
- com.ismaeldivita.chipnavigation:chip-navigation-bar:1.3.2

**Payment**
- com.razorpay:checkout:1.6.6 (Razorpay payment gateway)

**Networking**
- com.android.volley:volley:1.1.1

**Testing**
- junit:junit:4.12
- androidx.test.ext:junit:1.1.2
- androidx.test.espresso:espresso-core:3.3.0

---

## Project Structure

```
ARay/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/SidStudio/ARay/
│   │   │   │   ├── Activities (DashboardActivity, LoginActivity, etc.)
│   │   │   │   ├── Admin/ (AdminDashboardActivity, AdminAddProduct, etc.)
│   │   │   │   ├── Databases/ (Models & Session Management)
│   │   │   │   ├── HelperClasses/ (Adapters & Utilities)
│   │   │   │   └── Fragments (SessionDashboardFragment, etc.)
│   │   │   ├── res/
│   │   │   │   ├── layout/ (XML layout files for all activities/fragments)
│   │   │   │   ├── drawable/ (Icons and drawable resources)
│   │   │   │   ├── anim/ (Animation resources)
│   │   │   │   ├── values/ (Strings, colors, dimensions)
│   │   │   │   ├── mipmap-*/ (App icons and launcher images)
│   │   │   │   └── menu/ (Navigation menu definitions)
│   │   │   ├── AndroidManifest.xml
│   │   │   └── assets/
│   │   ├── test/ (Unit tests)
│   │   └── androidTest/ (Instrumented tests)
│   ├── build.gradle (App-level dependencies)
│   └── google-services.json (Firebase configuration)
├── build.gradle (Project-level dependencies)
├── gradle.properties
├── settings.gradle
└── README.md
```

---

## Main Activities & Flow

### User Flow

1. **SplashScreen** - Initial app launch screen
2. **LoginStartupScreen** - Login/Signup entry point with onboarding
3. **LoginActivity** - User login with credentials
4. **SignUp (3-step process)**:
   - SignUp1stClass - Basic info (name, username, email)
   - SignUp2ndClass - Password and phone setup
   - SignUp3rdClass - Profile completion
   - VerifyOTP - OTP verification via SMS/Email
5. **DashboardActivity** - Main user hub with:
   - Featured products carousel
   - Product categories
   - Navigation menu
   - Quick access to cart, orders, profile
6. **GlassesList** - Browsable catalog of eyewear
7. **ARscreen** - AR try-on experience with real-time model rendering
8. **CartActivity** - Shopping cart with quantity adjustment
9. **ConfirmOrderActivity** - Order review before checkout
10. **PaymentActivity** - Razorpay payment processing
11. **GetPurchseDetailsActivity** - Order history and details
12. **Settings** - User account and app preferences
13. **ForgetPassword** - Password recovery with SMS/Email options

### Admin Flow

1. **AdminDashboardActivity** - Admin control panel
2. **AdminAddItem** - Add new product items
3. **AdminAddProduct** - Configure product details and images
4. **AdminNewOrdersActivity** - View incoming orders
5. **AdminOrderedProductDetailsActivity** - Process order details

---

## Database Schema

The application uses **Firebase Realtime Database** with the following main models:

- **UserHelperClass** - User account information
- **ModelGlasses** - Eyewear product details
- **CartModel** - Shopping cart items with quantities
- **AdminOrdersModel** - Order information from customers
- **SessionManager** - User session management and authentication

---

## Permissions Required

```xml
android.permission.INTERNET
android.permission.CAMERA
android.permission.READ_EXTERNAL_STORAGE
android.permission.WRITE_EXTERNAL_STORAGE
android.hardware.camera.ar (required for AR features)
```

---

## Firebase Configuration

The app requires Firebase setup with:
- **Authentication**: Email/Password authentication
- **Realtime Database**: For user data, products, orders, and cart
- **Cloud Storage**: For product images and AR models
- **Configuration**: Add your `google-services.json` file to the `app/` directory

---

## Minimum Requirements

- **Android SDK**: API Level 24 (Android 7.0)
- **Target SDK**: API Level 29 (Android 10)
- **Device Requirements**: ARCore-compatible device for AR features
- **RAM**: Minimum 2GB (Recommended 3GB+)
- **Internet**: Active internet connection required

---

## Build & Run

### Prerequisites
- Android Studio (Latest version recommended)
- JDK 1.8+
- Android SDK (API 29)
- Gradle 4.0.0+

### Steps to Build

1. **Clone the repository**
   ```bash
   git clone https://github.com/Siddhesh-hub/ARay.git
   cd ARay
   ```

2. **Open in Android Studio**
   - Launch Android Studio
   - Select "Open an Existing Project"
   - Navigate to and select the `ARay` folder

3. **Configure Firebase**
   - Place your `google-services.json` in the `app/` directory
   - Update Firebase credentials in the project settings

4. **Build the Project**
   ```bash
   ./gradlew build
   ```

5. **Run the Application**
   - Connect an Android device (API 24+) via USB
   - Enable Developer Mode on device
   - Run the app through Android Studio (Ctrl+R or Run button)
   - Alternatively: `./gradlew installDebug`

---

## Key Implementation Highlights

### AR Implementation
- Uses Google ARCore and Sceneform for 3D model rendering
- Loads eyewear models from Firebase Storage
- Renders models on detected augmented faces
- Real-time visualization with camera feed

### Authentication & Security
- Firebase Authentication for secure login/registration
- OTP verification for account security
- Session management with persistent login
- Password reset functionality

### E-commerce Features
- Firebase Realtime Database for real-time product updates
- Cart management with instant price calculations
- Razorpay payment gateway integration
- Order tracking and history

### UI/UX
- Material Design components
- Responsive layouts with ConstraintLayout
- Smooth animations with Lottie
- Navigation drawer with menu management
- RecyclerView for efficient list rendering

---

## Development Notes

- **Code Language**: Primarily Java with Kotlin stdlib support
- **Architecture**: Activity-based with Fragment support
- **Database**: Firebase Realtime Database with custom models
- **Image Processing**: Glide for efficient image loading with caching
- **Network**: Volley for HTTP requests
- **State Management**: SharedPreferences via SessionManager

---

## Future Enhancements

Potential features for future versions:
- Virtual try-on history and saved preferences
- Social sharing of AR try-ons
- Size recommendation system
- User reviews and ratings
- Loyalty program and discounts
- Video tutorials for AR features
- Multi-language support
- Dark mode UI

---

## License

This project is part of the SidStudio Android Learning Series.

---

## Author

**Siddhesh** - SidStudio  
GitHub: [Siddhesh-hub](https://github.com/Siddhesh-hub)

---

## Support & Contact

For issues, feature requests, or questions regarding this project:
- Open an issue on GitHub
- Contact through SidStudio

---

## Disclaimer

This is a learning project developed to demonstrate Android development skills including AR, e-commerce, authentication, and payment integration. Ensure all third-party services (Firebase, Razorpay) are properly configured with your own credentials before production deployment.

---

**Last Updated**: February 2026
