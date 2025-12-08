PLAYSCROLLER - Real-Time Script Synchronization System
=======================================================

OVERVIEW
PlayScroller is a two-component web application system that enables real-time 
synchronization of script (PDF) viewing between a Stage Manager and multiple 
Actors. The Stage Manager controls the scroll position, which is instantly 
mirrored on all connected actors' devices over the internet.

LIVE APPLICATIONS
• Stage Manager App: https://playscroller.web.app/sm-app.html
• Actor App: https://playscroller.web.app/actor-app.html
• GitHub Repository: https://github.com/kenjenks/playscroller/

QUICK START GUIDE
1. STAGE MANAGER SETUP:
   a. Open https://playscroller.web.app/sm-app.html
   b. Click "Set PDF URL..." button (hamburger menu)
   c. Enter a publicly accessible PDF URL
   d. Click "Load PDF"
   e. Use the menu to "Show Actor QR Code"
   f. Actors scan this QR code with their device cameras
   g. The Stage Manager can also open the app using a URL with an embedded link to the PDF in URL-encoded format, like https://playscroller.web.app/sm-app.html
?pdfurl=https%3A%2F%2Fupload.wikimedia.org%2Fwikipedia%2Fcommons%2F7%2F7c%2FRomeo_and_Juliet_%25281917%2529_Yale.pdf%0A

2. ACTOR SETUP:
   a. Open camera app on mobile device
   b. Scan the QR code displayed by the Stage Manager
   c. The browser will open automatically with the synchronized script
   d. The PDF will automatically scroll to match the Stage Manager's position

PDF REQUIREMENTS
• Must be publicly accessible via URL
• Must have CORS headers enabled (most public file hosts do)
• Recommended hosting: Google Drive, Dropbox, or any web server
• Google Drive links are automatically converted to direct download links
• Example format: https://example.com/path/to/script.pdf

STAGE MANAGER APP FEATURES
• PDF URL Input: Load any publicly accessible PDF
• Real-time Scroll Broadcasting: Throttled to prevent overload
• QR Code Generation: Creates scannable codes for actors
• Dark Mode: Toggle between light/dark themes
• Text Search: Enhanced multi-word phrase search across PDF
• Bookmarks: Save and jump to specific positions
• Session Management: Start/reset synchronization sessions
• Status Indicator: Shows current page and scroll percentage
• Responsive Design: Works on desktop and tablet devices

ACTOR APP FEATURES
• Automatic PDF Loading: From QR code parameters
• Real-time Synchronization: Smooth scrolling to match SM position
• Multi-color Text Highlighting: Four-color highlight system with persistence
• Dark Mode: Automatic theme matching with system preference
• Cookie Persistence: Highlight preferences saved between sessions
• Full PDF Access: Entire PDF downloaded to device
• Responsive Design: Optimized for mobile/tablet use

HIGHLIGHT SYSTEM (Actor App)
• Four colors available: Yellow, Pink, Blue, Green
• Enter text to highlight across all pages
• Highlights persist via cookies (30-day expiration)
• Clear individual colors by emptying input field
• "Clear All Highlights" button to reset all colors
• Works in both light and dark modes

TEXT SEARCH (Stage Manager App)
• Enhanced multi-word phrase search
• Finds phrases even when split across lines
• Navigation buttons to jump between matches
• Visual highlighting of all matches
• Current match highlighted in orange

BOOKMARKS (Stage Manager App)
• Save current position as bookmark
• Name bookmarks for easy identification
• Edit or delete existing bookmarks
• Click to jump to bookmark position
• Persists via cookies (365-day expiration)

BACKEND ARCHITECTURE
1. FIREBASE REAL-TIME DATABASE:
   • Stores session metadata and scroll state
   • Structure: sessions/{session_id}/viewState
   • Data: {page: number, y_percent: number, timestamp}
   • Security: Anonymous auth required for read/write

2. FIREBASE AUTHENTICATION:
   • Anonymous sign-in for both SM and Actors
   • No user registration required
   • Unique user IDs generated per session

3. FIREBASE HOSTING:
   • Static file hosting for both apps
   • Global CDN distribution
   • HTTPS enabled by default

4. PDF.JS LIBRARY:
   • Client-side PDF rendering
   • Text extraction for search/highlighting
   • No server-side processing needed

SECURITY & PRIVACY
• All data transmission encrypted (HTTPS)
• Anonymous authentication only
• Session data automatically expires
• No personal information collected
• Actors can only read, not modify session data
• Each session has unique, hard-to-guess ID

TECHNICAL DETAILS
• Frontend: HTML5, CSS3 (Tailwind), Vanilla JavaScript (ES6 Modules)
• PDF Rendering: PDF.js v2.11.338
• QR Codes: QRious v4.0.2
• Database: Firebase Realtime Database
• Hosting: Firebase Hosting
• Authentication: Firebase Anonymous Auth
• Responsive Design: Mobile-first approach

USAGE NOTES
1. Stage Manager should use a device with stable internet connection
2. Actors can join at any time during an active session
3. PDFs remain cached on actor devices for offline viewing
4. Highlights are saved per browser, not per session
5. Dark mode preference saved in localStorage
6. No installation required - works in modern browsers

TROUBLESHOOTING
• PDF won't load: Check URL accessibility and CORS headers
• QR code not scanning: Ensure good lighting, try larger display
• Sync lagging: Check internet connectivity on all devices
• Search not finding text: Try simpler search terms
• Highlights not appearing: Check text matches exactly (case-insensitive)

BROWSER SUPPORT
• Chrome 60+
• Firefox 60+
• Safari 12+
• Edge 79+
• iOS Safari 12+
• Chrome for Android 60+

DEVELOPMENT
The project is open source on GitHub. Key files:
• sm-app.html: Stage Manager application
• actor-app.html: Actor application
• Firebase configuration in both files

LICENSE & ATTRIBUTION
• Open source for educational and non-commercial use
• Built with PDF.js (Mozilla), QRious, Tailwind CSS
• Firebase services by Google

For support or contributions, visit the GitHub repository.
