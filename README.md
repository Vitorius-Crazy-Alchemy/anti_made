Vitorius Data Disabler — Anti-MAID Privacy Shield
Overview
Vitorius Data Disabler is an open, high-assurance Android privacy tool engineered specifically to defend users against modern mobile surveillance, commercial ad-exchange telemetry, real-time bidding (RTB) bidstream harvesting, and location-data intelligence broker tracking (such as platforms like Babel Street, Locate X, Anomaly Six, and global ad networks).
By targeting the primary vector of mobile tracking—the Mobile Advertising ID (MAID / AAID)—Vitorius Data Disabler provides real-time audit visibility, system-level privacy shortcuts, app permission scanning, and actionable security hardening steps.
The Threat Model: How MAID Tracking Works
Every Android device running Google Play Services historically generates a unique, user-resettable Mobile Advertising ID (MAID / AAID). Ad networks and SDKs embedded inside thousands of free mobile applications (games, weather apps, flashlight utilities) continuously harvest this MAID alongside:
1.
Precise GPS / Network Location Coordinates (Latitude, Longitude, Altitude)
2.
Device Telemetry (IP address, Wi-Fi BSSID/SSID, device model)
3.
Timestamped Activity Logs
During real-time bidding (RTB) ad auctions, this telemetry payload is broadcast across global ad exchanges. Commercial data brokers and intelligence contractors scrape this bidstream data to build persistent, high-precision physical movement profiles and home/work location maps tied to specific devices.
Key Features & Technical Capabilities
1. Real-Time MAID / AAID Status Checker
•
Instant Verification: Queries Google Play Services AdvertisingIdClient off the main thread to determine whether your device has an active tracking GUID or a zeroed-out ID.
•
Zeroed ID Detection: Verifies if your device's MAID has been successfully reset to 00000000-0000-0000-0000-000000000000 (introduced in Android 12+ when you delete your Advertising ID).
•
1-Click System Privacy Shortcut: Launches Google's hidden Ads Privacy settings page (com.google.android.gms.settings.ADS_PRIVACY) in a single tap so you can delete or reset your Advertising ID immediately without hunting through system sub-menus.
2. Deep Installed App Permission Audit
•
Full Package Inspection: Uses Android's PackageManager API to scan every installed system and user application.
•
AD_ID Permission Detection: Identifies apps explicitly declaring <uses-permission android:name="com.google.android.gms.permission.AD_ID"/> to access your Advertising Identifier.
•
Location Permission Mapping: Cross-references AD_ID declarations against Precise (ACCESS_FINE_LOCATION), Coarse (ACCESS_COARSE_LOCATION), and Background (ACCESS_BACKGROUND_LOCATION) location permissions.
3. Automated Risk Classification Engine
Apps are categorized into four distinct risk tiers based on their telemetry exposure:
•
🚨 CRITICAL TRACKER: App requests AD_ID + Location Permissions + Internet Access. This represents the exact dual vector used by intelligence data brokers to correlate physical locations with device profiles.
•
⚠️ HIGH RISK: App requests AD_ID + Internet Access without active location access.
•
📍 LOCATION TRACKER: App requests Location Permissions + Internet Access without declaring AD_ID.
•
🛡️ LOW RISK: App maintains minimal or no tracking permissions.
4. Interactive App Management & Filtering
•
Real-time Search & Filter: Instantly search apps by name or package identifier (com.example.app).
•
Categorized Filter Chips: Isolate Critical (MAID+GPS) apps, High Risk apps, or filter specifically for User Installed third-party apps.
•
Direct Permission Revocation: Launch any app's system details page (Settings.ACTION_APPLICATION_DETAILS_SETTINGS) directly from the audit list to revoke background location permissions or uninstall suspicious trackers.
5. Interactive Anti-Tracking Defense Guide
Provides step-by-step technical hardening workflows with system intent shortcuts:
•
Step 1: Zero Out Advertising ID — Sever ad-broker profile linkage system-wide.
•
Step 2: Revoke App Location Access — Audit and prune unnecessary GPS permissions.
•
Step 3: Harden System Location Settings — Shortcuts to turn off Google Location Accuracy and Location History / Timeline telemetry.
•
Step 4: Encrypted Private DNS Configuration — Instructions and shortcuts to configure Private DNS (e.g. NextDNS / AdGuard) to sinkhole outgoing ad-tech bidstream requests at the network layer.
Technical Architecture & Privacy Guarantees
•
100% On-Device Analysis: All scanning, permission auditing, and risk evaluations run locally on your phone. No data, telemetry, or app lists ever leave your device.
•
Zero Analytics or Tracking: Vitorius Data Disabler contains no third-party SDKs, no ad frameworks, no analytics trackers, and requests no internet permission for itself.
•
R8 / ProGuard Optimized: Built with strict R8 code shrinking and resource optimization for an ultra-lightweight footprint and minimal resource overhead.
•
Modern Material 3 Jetpack Compose UI: Built natively using Kotlin, Coroutines, StateFlow, Clean Architecture, and Material Design 3 guidelines.


