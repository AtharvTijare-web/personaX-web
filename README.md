PersonaX-Web
<br>
Minor Project 2nd Year 2025
<br>
Repo structure
<br>
personax-fullstack/
<br>
├─ README.md
<br>
├─ .env.example
<br>
├─ package.json
<br>
├─ client/
<br>
│  ├─ package.json
<br>
│  ├─ postcss.config.js
<br>
│  ├─ tailwind.config.cjs
<br>
│  ├─ public/
<br>
│  │  └─ index.html
<br>
│  └─ src/
<br>
│     ├─ main.jsx
<br>
│     ├─ App.jsx
<br>
│     ├─ index.css
<br>
│     ├─ components/
<br>
│     │  ├─ Hero.jsx
<br>
│     │  ├─ Stats.jsx
<br>
│     │  ├─ Testimonials.jsx
<br>
│     │  └─ Footer.jsx
<br>
│     └─ assets/
<br>
│        ├─ hero.jpg (placeholder)
<br>
│        └─ ...
<br>
└─ server/
<br>
   ├─ package.json
   <br>
   ├─ server.js
   <br>
   ├─ routes/
   <br>
   │  └─ api.js
   <br>
   ├─ models/
   <br>
   │  └─ ClientTestimonial.js
   <br>
   ├─ controllers/
   <br>
   │  └─ testimonialsController.js
   <br>
   └─ seed/
   <br>
      └─ seed.js
      <br>
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
