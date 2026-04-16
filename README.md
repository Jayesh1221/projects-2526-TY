<h1>1. Project Title: </h1>Krushi Sakha
<p><h2>2. Project description: </h2>Krushi Sakha is an Android-based platform that empowers registered farmers with a scientific, end-to-end roadmap for complete crop management. By guiding users through a structured 5-pillar "Crop Loop"—from pre-sowing preparation to scientific storage—the application bridges the agricultural knowledge gap to optimize yields and prevent financial loss.</p>
<h1>3. Group no: </h1>11
<p><h1>4. Team members: </h1>1. Gujar Jayesh Nagesh <br>
  2. Kor Darshan Pruthviraj <br>
  3. Puranik Amay Tushar <br>
  4. Patil Krish Chandrashekhar </p>
<p><h1>5. Tech stack: </h1>Here is the technical stack and architecture driving the Krushi Sakha application:
​Frontend & Mobile Environment
​Platform: Native Android
​IDE: Android Studio
​Language: Java
​UI Design: XML layouts
​Backend & Cloud Services (Google Firebase)
​Authentication: Firebase Authentication (Managing secure logins for both Farmers and Admins/Experts)
​Database: Firebase Realtime Database (Using a NoSQL JSON structure)
​Media Storage: Firebase Storage (For housing high-quality pest/disease photos and agricultural case studies)</p>
<p><h1>6. Project Structure: </h1>KrushiSakha/
│
├── app/                                  # Main application module
│   ├── src/main/
│   │   ├── java/com/project/krushisakha/ # Java Source Code
│   │   │   ├── activities/               # UI Controllers
│   │   │   │   ├── splash/               # Splash screen and routing logic
│   │   │   │   ├── auth/                 # Authentication Flow
│   │   │   │   │   ├── FarmerLoginActivity.java
│   │   │   │   │   ├── FarmerRegisterActivity.java
│   │   │   │   │   └── AdminLoginActivity.java
│   │   │   │   ├── farmer/               # Authenticated farmer views
│   │   │   │   └── admin/                # Admin data entry views
│   │   │   │
│   │   │   ├── adapters/                 # RecyclerView Adapters
│   │   │   │   ├── CropListAdapter.java  # TextWatcher filtering for search
│   │   │   │   └── DiseaseAdapter.java   # Nested RecyclerView for Pillar 4
│   │   │   │
│   │   │   ├── models/                   # Simplified POJO classes
│   │   │   │   ├── User.java             # Handles role-based access (Farmer vs Admin)
│   │   │   │   ├── Crop.java             # Flattened, single-language model
│   │   │   │   └── Disease.java
│   │   │   │
│   │   │   ├── network/                  # Database and API handling
│   │   │   │   └── FirebaseHelper.java   # Centralized DB logic, Disk Persistence config
│   │   │   │
│   │   │   └── utils/                    # Helper classes
│   │   │       ├── GlideUtils.java       # Image loading and memory management
│   │   │       └── Constants.java        # Static Firebase node keys
│   │   │
│   │   ├── res/                          # Android Resources
│   │   │   ├── layout/                   # XML UI definitions
│   │   │   └── values/                   # Single language strings (strings.xml), colors, themes
│   │   │
│   │   └── AndroidManifest.xml           # App permissions and activity declarations
│   │
│   ├── build.gradle                      # App-level Gradle 
│   └── google-services.json              # Firebase config file (MUST BE IN .gitignore)
│
├── build.gradle                          # Project-level Gradle
├── settings.gradle
├── .gitignore                            # Excludes IDE files, build caches, and sensitive keys
└── README.md                             # Project documentation</p>
<p><h1>7. Prerequisites and installation steps: </h1>## 🚀 Comprehensive Installation & Setup Guide

This section provides an exhaustive, step-by-step walkthrough to configure the **Krushi Sakha** development environment, initialize the backend infrastructure, and deploy the application locally. 

### Phase 1: Local Environment Preparation
Before cloning the repository, ensure your local development environment meets the strict technical prerequisites.

1. **Install Java Development Kit (JDK):**
   * Download and install **JDK 17** (or higher) from the official Oracle website or adoptium.net.
   * Ensure your `JAVA_HOME` environment variable is correctly mapped to your JDK installation path.
2. **Install Android Studio:**
   * Download the latest stable release of [Android Studio](https://developer.android.com/studio).
   * During installation, ensure the **Android SDK**, **Android SDK Command-line Tools**, and **Android Emulator** components are checked.
   * Open Android Studio -> SDK Manager -> SDK Platforms: Ensure **API 34/35 (Android 14/15)** is installed.
3. **Install Git:**
   * Download and install Git from [git-scm.com](https://git-scm.com/).
   * Verify installation by running `git --version` in your terminal.

---

### Phase 2: Repository Acquisition
1. Open your terminal, Command Prompt, or Git Bash.
2. Navigate to the directory where you wish to store the project:
   ```bash
   cd path/to/your/workspace
Phase 3: Firebase Backend Configuration (Strictly Required)
Krushi Sakha relies on Firebase for role-based authentication, offline-capable database management, and image storage. You must connect the app to your own Firebase instance for it to compile and run.
3.1 Create the Firebase Project
Navigate to the Firebase Console and log in with your Google Account.
Click Create a Project and name it exactly: KrushiSakha.
Disable Google Analytics (not required for this academic build) and click Create Project.
3.2 Register the Android Application
On the Firebase Project Overview page, click the Android Icon to add an app.
Android Package Name: Enter exactly com.project.krushisakha (this must match the applicationId in your app/build.gradle).
App Nickname: Enter Krushi Sakha App.
SHA-1 Certificate (Optional but recommended): Run ./gradlew signingReport in your Android Studio terminal to generate your debug SHA-1 key and paste it here.
Click Register App.
3.3 Download and Apply Configuration
Click the Download google-services.json button.
Move this downloaded file into the app/ module directory of your cloned project (KrushiSakha/app/google-services.json).
Note: This file contains sensitive API keys and is intentionally excluded from version control via .gitignore.
3.4 Initialize Required Firebase Services
Navigate through the left-hand menu in the Firebase Console to enable the following:
Authentication:
Go to Build > Authentication > Get Started.
Go to the Sign-in method tab.
Enable Email/Password (Required for both Farmer and Admin login flows).
Realtime Database:
Go to Build > Realtime Database > Create Database.
Choose your closest geographic location.
Start in Test Mode (you will update the security rules later to separate Admin vs. Farmer read/write access).
Storage:
Go to Build > Storage > Get Started.
Start in Test Mode. This is where high-quality images for the 5-Pillar crop stages (e.g., disease photos) will be hosted to serve the Glide image loading library.
Phase 4: Android Studio Initialization & Sync
Open Android Studio.
Select Open and browse to the KrushiSakha folder you cloned. Click OK.
Gradle Sync: Android Studio will automatically begin indexing and downloading required dependencies (such as the Firebase BoM, Glide, and RecyclerView libraries).
If it does not start automatically, click the "Sync Project with Gradle Files" icon (the elephant with an arrow) in the top toolbar.
Verify JDK: Go to File > Project Structure > SDK Location. Ensure the Gradle JDK is set to the Java 17 installation from Phase 1.
Wait until the bottom status bar reads: Gradle sync finished.
Phase 5: Database Seeding (The Crop Loop)
To fully test the application, you must seed the Firebase Realtime Database with initial data conforming to the 5-Pillar architecture.
In the Firebase Console, go to Realtime Database.
Click the three vertical dots (⋮) in the top right corner of the database viewer and select Import JSON.
Upload your initial crops_data.json file (ensure it follows the flattened, single-language structure containing Pre-Sowing, Sowing, Nutrient/Water, Protection, and Storage nodes).
Phase 6: Build & Execution
Prepare a Device:
Physical Device: Enable Developer Options and USB Debugging on your Android phone. Connect it via USB.
Emulator: Open the Device Manager in Android Studio, click Create Device, select a hardware profile (e.g., Pixel 6), and download the API 34 system image. Launch the emulator.
Run the App:
Select your connected device or emulator from the device drop-down menu in the top toolbar.
Click the green Run 'app' button (or press Shift + F10).
Verify Build: Gradle will assemble the APK and install it. The Krushi Sakha splash screen should appear, followed by the Authentication screen.
🛠️ Troubleshooting & Common Errors
Error: Default FirebaseApp is not initialized
Fix: You forgot to place the google-services.json file in the app/ directory, or the package name inside the JSON does not match com.project.krushisakha.
Error: Minimum supported Gradle version is...
Fix: Navigate to gradle/wrapper/gradle-wrapper.properties and update the distributionUrl to the required version prompted by Android Studio.
Error: Data not loading / App crashes on launch
Fix: Ensure Firebase Realtime Database rules are set to allow reads (".read": true) during testing, and verify your device has an active internet connection for the initial fetch before Disk Persistence takes over.
</p>
