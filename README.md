BinBuddy: CleanStreet Challenge 🌿🗑️
A Hackathon-Winning Community Waste Pickup & Civic Reporting Web Application Built with React (Vite) + Tailwind CSS ("Fresh Earth" Design System) + Express (REST) + SQLite + Framer Motion.

🌟 Overview & Mission
BinBuddy empowers urban neighborhoods, ward corporators, and municipal sanitation crews to eliminate street garbage hotspots through verified citizen reporting, real-time priority escalation, and smart waste stream segregation.

Key Value Pillars
50-Item Waste Segregation Lookup: Instant keyword classification into color-coded streams (Green Wet, Blue Dry, Red Sanitary, Amber E-Waste, Red Hazard).
Public Ward Status Board: Interactive Kanban (Reported → Assigned → Cleaned) with drag-and-drop mechanics and live priority escalation heuristics.
Smart Duplicate & Proximity Check: Automatically detects existing nearby grievances as citizens type landmarks, encouraging community upvoting instead of duplicate ticket flooding.
Tipper Truck Countdown & GPS Tracker: Real-time simulated countdown clock with an animated truck navigating the ward collection route.
Sanitation Worker Field Manifest: Specialized crew interface to review daily route stops, dispatch squad members, and upload resolution photo proofs.
Community Eco-Points & Gamified Quiz: 5-question dilemma mini-game with canvas confetti, shake feedback, progressive badge unlocking, and ward leaderboard.
Apartment E-Waste Drive Pooling: Cluster bulk pooling with progress bar toward the 250 kg municipal pickup threshold.
🎨 Design System: "Fresh Earth"
BinBuddy is designed with an organic, civic-friendly palette that evokes clean streets, nature, and municipal stewardship.

Token	Hex Code	Purpose
cream-50	#FFFBF0	Primary page background
cream-100	#FAF3E0	Card & container surface
cream-200	#F1E6C8	Borders & subtle separators
leaf-300	#BFE3B4	Light leaf accents
leaf-400	#8FCB81	Vibrant green highlights
leaf-500	#5FAE5B	Primary interactive brand color
leaf-700	#2F6B3A	Deep forest text & accents
bark-400	#A47551	Earthy secondary text
bark-600	#6F4E37	Secondary body text
bark-900	#3B2A20	High-contrast heading typography
marker	#FFE58A	Hand-drawn highlighter sweep
Dark Mode	#1E1A14 (bg), #2A241B (cards)	Dedicated high-contrast dark palette
Typography
Display Headings: "Fraunces" (Google Fonts serif, weights 600–800)
Body & UI: "Plus Jakarta Sans" (Google Fonts sans-serif, weights 400–800)
Handwritten Accents & Badges: "Caveat" (Google Fonts cursive)
🏗️ Architecture & File Structure
binbuddy/
├── package.json                    # Root npm scripts (dev, build, start)
├── README.md                       # Comprehensive documentation & 2-min demo script
├── server/                         # Express REST API + SQLite backend
│   ├── package.json
│   ├── index.js                    # Express app, CORS, routes & static client serving
│   ├── db.js                       # Native SQLite initialization & seeding engine
│   ├── binbuddy.sqlite             # Embedded database file
│   └── data/
│       ├── seedItems.js            # 50 household waste items with disposal tips
│       ├── seedTickets.js          # 8 ward complaint tickets (Reported/Assigned/Cleaned)
│       └── seedSchedule.js         # Ward collection timetables & truck simulation
└── client/                         # Vite + React single page application
    ├── index.html                  # HTML entry point with Google Fonts
    ├── vite.config.js              # Vite bundler config with /api proxy
    ├── tailwind.config.js          # Fresh Earth colors, fonts & custom keyframe animations
    ├── postcss.config.js
    ├── package.json
    └── src/
        ├── main.jsx                # React DOM root
        ├── App.jsx                 # App composition with Context Providers
        ├── index.css               # Paper-grain textures, markers & custom styles
        ├── context/
        │   ├── ThemeContext.jsx    # Dark/Light mode state with localStorage sync
        │   ├── ToastContext.jsx    # Animated notification dispatch
        │   ├── WardContext.jsx     # Ward selector, truck countdown & user roles
        │   └── TicketContext.jsx   # Ticket store, upvotes & proximity detection
        ├── components/
        │   ├── Navbar.jsx          # Ward picker, Citizen/Worker toggle, dark mode
        │   ├── Highlight.jsx       # Marker sweep on scroll (scaleX 0 -> 1)
        │   ├── AnimatedHeading.jsx # Staggered word-by-word reveal with blur-to-sharp
        │   ├── FloatingParticles.jsx# Floating leaves & recycle drift animations
        │   ├── TiltCard.jsx        # 3D interactive tilt & shadow lift
        │   ├── CountUp.jsx         # Animated number ticker
        │   ├── ToastContainer.jsx  # Slide-in toast alerts
        │   ├── SkeletonLoader.jsx  # Accessible pulse shimmer placeholders
        │   ├── WavyDivider.jsx     # Organic SVG section dividers
        │   └── Footer.jsx          # Civic contacts & helplines
        ├── sections/
        │   ├── HeroSection.jsx     # Typewriter rotating words, stats counter, CTAs
        │   ├── TruckCountdown.jsx  # Ticking timer & animated driving vehicle road
        │   ├── ScheduleTracker.jsx # Monthly calendar with color dots & rules
        │   ├── WasteLookup.jsx     # Instant 50-item live search with bounce badges
        │   ├── IncidentReporterModal.jsx # FileReader photo upload + duplicate detector
        │   ├── WardKanbanBoard.jsx # 3-column status board, drag-and-drop, upvotes
        │   ├── SanitationManifest.jsx # Field route stops & resolution modal
        │   ├── SegregationQuiz.jsx # 5-question mini-game, confetti & badges
        │   └── EWasteDriveScheduler.jsx# Apartment pooling progress bar & slot booking
        └── utils/
            ├── api.js              # Resilient fetch client with localStorage fallback
            ├── scoring.js          # Priority heuristic scoring formula
            └── fallbackData.js     # Standalone offline seed data
⚡ Quick Start & Setup
Prerequisites
Node.js v18+ or higher (tested on Node.js v26.13.1)
npm v9+
1. Installation
Clone or navigate into the repository:

cd binbuddy
Install dependencies for both frontend and backend:

# Install client dependencies
cd client && npm install

# Install server dependencies
cd ../server && npm install
2. Development Mode (Running Client + Server)
In one terminal, start the Express backend:

cd server
npm start
# Server starts on http://localhost:3001
In a second terminal, start the Vite development server:

cd client
npm run dev
# Client starts on http://localhost:5173 with automatic /api proxy
3. Production Single-Port Mode
You can build the React frontend and let Express serve both the frontend and REST API simultaneously on port 3001:

cd client
npm run build

cd ../server
npm start
# Visit http://localhost:3001 in your browser!
⏱️ 2-Minute Hackathon Demo Script
Follow this script to showcase all 10 core features in 120 seconds:

Step 1: Waste Segregation Lookup (0:00 - 0:25)
Scroll to the Waste Segregation Lookup section.
In the live search box, type broken tube light.
Observe: The result drops into place with a bounce animation.
Notice: It displays a bright Red Hazard Bin badge and a highlighted safety warning: "DANGER: Contains toxic mercury vapor. Do NOT shatter. Wrap unbroken tubes in newspaper before hazardous waste pickup."
Click "🔵 Dry Recyclables" to see PET bottles, cardboard, and aluminium cans.
Step 2: Spotting & Lodging a Civic Issue with Proximity Detection (0:25 - 0:50)
Click the "Report an Issue" button in the navbar.
Under landmark, type: Colony Park Gate.
Observe: The Smart Proximity / Duplicate Check immediately triggers! A warning banner appears displaying: "Nearby Existing Ticket Detected: TKT-101 Overflowing dumpster outside Colony Park gate".
Show judges how citizens can click "Upvote This (+19)" to escalate an existing report rather than cluttering the board with duplicates.
Alternatively, fill in a new landmark: Maple Avenue Corner, select category Illegal Construction Debris, select an image using the FileReader photo uploader, and click "Post to Ward Board".
A toast notification slides in confirming ticket creation!
Step 3: Ward Kanban Board & Priority Escalation (0:50 - 1:15)
Scroll to the Public Ward Status Board.
Notice the 3 columns: Reported, Assigned, and Cleaned.
Locate high-severity issues (like chemical spills or biohazards) and point out the pulsing 🔥 Escalated flame badge.
Explain the ranking heuristic: 
Score
=
(
Upvotes
×
2
)
+
(
Age in Days
×
1.5
)
+
Category Weight
Click the Upvote button on any ticket:
Notice the button pop animation.
Watch the floating +1 👍 particle float upwards.
Note that duplicate votes in the same session are automatically prevented!
Drag a card from Reported to Assigned (or click Assign).
Step 4: Sanitation Worker Manifest View (1:15 - 1:40)
In the top navbar, toggle the role switcher from "Citizen" to "Crew Mode" (or click Manifest in navigation).
The UI enters the Municipal Sanitation Worker Portal.
Show the Today's Route Stops checklist (e.g. Depot inspection, Commercial Line, School Bus Stop) and check off completed stops.
On any assigned ticket, click "Mark Resolved".
In the resolution modal, attach an after-cleanup photo, enter a brief confirmation note (e.g., "Cleared dumpster with hydraulic compactor and disinfected surface with lime powder"), and click "Confirm & Mark Cleaned ✓".
Switch back to the Ward Status Board: the card is now in the Cleaned & Verified column!
Step 5: Tipper Truck Live Countdown & Eco-Quiz (1:40 - 2:00)
Scroll to the Tipper Truck Countdown:
Point out the live ticking clock (MM:SS).
Watch the animated CNG tipper truck vehicle navigate along the progress road towards the citizen's doorstep.
Switch wards in the dropdown to observe route and driver details change dynamically.
Jump to the Segregation Eco-Quiz:
Answer the pizza box question (Green Wet Bin).
Enjoy the confetti blast and watch the eco-score tick up by +100 points.
Intentionally pick a wrong answer on the next question to demonstrate the subtle card shake feedback.
Show the unlocked badge (Sprout / Forest Guardian) and the community leaderboard.
🔒 Reliability & Offline Fallback
BinBuddy features Zero-Downtime Resilience:

If the Express backend is running, state is persisted in an embedded SQLite database (node:sqlite).
If the backend is stopped or network drops, all API client calls in api.js transparently fall back to localStorage and bundled seed data.
Upvotes, status changes, and new tickets continue functioning offline without throwing unhandled exceptions.
♿ Accessibility & Responsiveness
WCAG AA Compliance: High-contrast text on cream/bark backgrounds.
Motion Accessibility: Automatically respects prefers-reduced-motion: reduce by disabling heavy keyframes for sensitive users.
Mobile First: Verified on 375px mobile screens (responsive drawer, touch-friendly tap targets, swipeable kanban controls) and 1280px+ desktop layouts.
🏆 CleanStreet Challenge Verdict
BinBuddy bridges the gap between everyday citizen convenience, rigorous waste segregation education, and ground-level municipal sanitation execution.
