PersonaX-Web
<br>
Minor Project 2nd Year 2025
<br>
Repo structure
personax-fullstack/
├─ README.md
├─ .env.example
├─ package.json
├─ client/
│  ├─ package.json
│  ├─ postcss.config.js
│  ├─ tailwind.config.cjs
│  ├─ public/
│  │  └─ index.html
│  └─ src/
│     ├─ main.jsx
│     ├─ App.jsx
│     ├─ index.css
│     ├─ components/
│     │  ├─ Hero.jsx
│     │  ├─ Stats.jsx
│     │  ├─ Testimonials.jsx
│     │  └─ Footer.jsx
│     └─ assets/
│        ├─ hero.jpg (placeholder)
│        └─ ...
└─ server/
   ├─ package.json
   ├─ server.js
   ├─ routes/
   │  └─ api.js
   ├─ models/
   │  └─ ClientTestimonial.js
   ├─ controllers/
   │  └─ testimonialsController.js
   └─ seed/
      └─ seed.js
<br>
Root package.json
<br>
{
  "name": "personax-fullstack",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "start": "node server/server.js",
    "client": "cd client && npm start",
    "server": "cd server && npm run dev",
    "dev": "concurrently \"npm:server\" \"npm:client\"",
    "build": "cd client && npm run build"
  },
  "devDependencies": {
    "concurrently": "^8.0.0"
  }
}
