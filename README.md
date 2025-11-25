// Fusion Palate — Next.js 14 Deployable (full project scaffold)
// Drop the contents below into a folder, run `npm install` then `npm run dev` to preview.
// This is a Next.js 14 app using the App Router, TailwindCSS, and includes placeholder images and an SVG logo.

/*
Project structure (files below). Save each file with the given path.

package.json
next.config.js
tailwind.config.js
postcss.config.cjs
/public/
  favicon.ico
  logo.svg
  hero.jpg
  pilau.jpg
  biryani.jpg
  nyama.jpg
/app/layout.jsx
/app/page.jsx
/app/menu/page.jsx
/app/about/page.jsx
/app/catering/page.jsx
/app/contact/page.jsx
/app/globals.css
/components/Header.jsx
/components/Footer.jsx
/components/Hero.jsx
/components/DishCard.jsx
/styles/variables.css

Instructions:
1) Copy each file into your local project folder exactly as named.
2) Run: npm install
3) Run: npm run dev
4) Open http://localhost:3000
5) To deploy: push to GitHub and import project in Vercel, or drag-and-drop the folder into Vercel.

*/

/* ---------- package.json ---------- */
// Save as package.json
{
  "name": "fusion-palate-next",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev -p 3000",
    "build": "next build",
    "start": "next start -p 3000",
    "lint": "next lint"
  },
  "dependencies": {
    "next": "14.0.0",
    "react": "18.2.0",
    "react-dom": "18.2.0",
    "framer-motion": "10.12.16"
  },
  "devDependencies": {
    "autoprefixer": "10.4.14",
    "postcss": "8.4.24",
    "tailwindcss": "3.4.6"
  }
}

/* ---------- next.config.js ---------- */
// Save as next.config.js
export default {
  experimental: {
    appDir: true,
  },
}

/* ---------- tailwind.config.js ---------- */
// Save as tailwind.config.js
export default {
  content: ["./app/**/*.{js,ts,jsx,tsx}", "./components/**/*.{js,ts,jsx,tsx}"],
  theme: { extend: {} },
  plugins: [],
}

/* ---------- postcss.config.cjs ---------- */
// Save as postcss.config.cjs
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}

/* ---------- public/logo.svg ---------- */
// Save as public/logo.svg
<?xml version="1.0" encoding="utf-8"?>
<svg width="200" height="200" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="g" x1="0" x2="1">
      <stop offset="0%" stop-color="#F6C667"/>
      <stop offset="100%" stop-color="#D95D39"/>
    </linearGradient>
  </defs>
  <rect width="100%" height="100%" rx="18" fill="white" />
  <g transform="translate(40,40)">
    <circle cx="60" cy="40" r="36" fill="url(#g)" />
    <text x="60" y="48" font-family="Georgia, serif" font-size="32" text-anchor="middle" fill="white" font-weight="700">FP</text>
  </g>
</svg>

/* ---------- public/hero.jpg, pilau.jpg, biryani.jpg, nyama.jpg ---------- */
// For quick preview, you can download images from Unsplash or replace with your own.
// If you prefer, use these example Unsplash URLs inside components instead of local files.

/* ---------- app/layout.jsx ---------- */
// Save as app/layout.jsx
import './globals.css'
import Header from '../components/Header'
import Footer from '../components/Footer'

export const metadata = {
  title: 'Fusion Palate',
  description: 'Authentic East & West African cuisine with a touch of luxury — Berlin catering',
}

export default function RootLayout({ children }){
  return (
    <html lang="en">
      <body>
        <Header />
        <main>{children}</main>
        <Footer />
      </body>
    </html>
  )
}

/* ---------- app/page.jsx (Home) ---------- */
// Save as app/page.jsx
import Hero from '../components/Hero'
import DishCard from '../components/DishCard'

const dishes = [
  { name: 'Pilau', img: '/pilau.jpg' },
  { name: 'Biryani', img: '/biryani.jpg' },
  { name: 'Nyama Choma', img: '/nyama.jpg' }
]

export default function Home(){
  return (
    <div className="min-h-screen bg-[var(--bg)] text-[var(--text)]">
      <div className="max-w-6xl mx-auto px-6 py-12">
        <Hero />
        <section className="py-12">
          <h2 className="text-3xl font-bold mb-6">Signature Dishes</h2>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
            {dishes.map((d, i) => (
              <DishCard key={i} name={d.name} img={d.img} />
            ))}
          </div>
        </section>
      </div>
    </div>
  )
}

/* ---------- app/menu/page.jsx ---------- */
// Save as app/menu/page.jsx
export default function MenuPage(){
  const menu = [
    { title: 'Pilau', price: '€11' },
    { title: 'Biryani', price: '€13' },
    { title: 'Nyama Choma', price: '€14' },
    { title: 'Mukimo', price: '€10' },
    { title: 'Finger Platter', price: '€14' },
    { title: 'Roasted Chicken', price: '€13' }
  ]

  return (
    <div className="max-w-6xl mx-auto px-6 py-12">
      <h1 className="text-3xl font-bold mb-4">Menu</h1>
      <div className="grid md:grid-cols-2 gap-4">
        {menu.map((item, idx) => (
          <div key={idx} className="p-4 bg-white rounded shadow">
            <div className="flex justify-between">
              <div className="font-semibold">{item.title}</div>
              <div className="text-gray-600">{item.price}</div>
            </div>
          </div>
        ))}
      </div>
    </div>
  )
}

/* ---------- app/about/page.jsx ---------- */
// Save as app/about/page.jsx
export default function AboutPage(){
  return (
    <div className="max-w-6xl mx-auto px-6 py-12">
      <h1 className="text-3xl font-bold">Our Story</h1>
      <p className="mt-4 text-gray-700">Fusion Palate blends East & West African culinary traditions with a hint of Jamaican soul. We focus on authentic flavour, seasonal sourcing and refined presentation for events across Berlin.</p>
    </div>
  )
}

/* ---------- app/catering/page.jsx ---------- */
// Save as app/catering/page.jsx
export default function CateringPage(){
  return (
    <div className="max-w-6xl mx-auto px-6 py-12">
      <h1 className="text-3xl font-bold">Catering</h1>
      <p className="mt-4 text-gray-700">Private events, corporate catering, and pop-ups — bespoke menus and service for your event.</p>
    </div>
  )
}

/* ---------- app/contact/page.jsx ---------- */
// Save as app/contact/page.jsx
'use client'
import { useState } from 'react'

export default function ContactPage(){
  const [sent, setSent] = useState(false)
  return (
    <div className="max-w-6xl mx-auto px-6 py-12">
      <h1 className="text-3xl font-bold">Contact & Bookings</h1>
      <p className="mt-4 text-gray-700">Email hello@fusionpalate.berlin or use the form below.</p>
      <form className="mt-6 bg-white p-6 rounded-lg shadow" onSubmit={(e)=>{e.preventDefault(); setSent(true)}}>
        <input className="w-full p-2 border rounded mb-3" placeholder="Full name" required />
        <input className="w-full p-2 border rounded mb-3" placeholder="Email" required />
        <textarea className="w-full p-2 border rounded mb-3" placeholder="Message" rows={5}></textarea>
        <button className="bg-[var(--accent)] text-white px-4 py-2 rounded">Send</button>
        {sent && <div className="text-sm text-green-600 mt-3">Request sent. We'll be in touch.</div>}
      </form>
    </div>
  )
}

/* ---------- components/Header.jsx ---------- */
// Save as components/Header.jsx
import Link from 'next/link'
import Image from 'next/image'
import LogoImport from '../public/logo.svg'

export default function Header(){
  // Resolve logo import safely for different environments
  let logoSrc = ''
  try {
    if (!LogoImport) logoSrc = ''
    else if (typeof LogoImport === 'string') logoSrc = LogoImport
    else if (typeof LogoImport === 'object') logoSrc = LogoImport.default || LogoImport.src || ''
  } catch (e) { logoSrc = '' }

  const nav = [
    { label: 'Menu', href: '/menu' },
    { label: 'Catering', href: '/catering' },
    { label: 'About', href: '/about' },
    { label: 'Contact', href: '/contact' }
  ]

  return (
    <header className="bg-white shadow-sm">
      <div className="max-w-6xl mx-auto px-6 py-4 flex items-center justify-between">
        <Link href="/" className="flex items-center gap-3">
          {logoSrc ? (
            // next/image can accept static imports, but for simplicity we use a standard img tag here
            <img src={logoSrc} alt="Fusion Palate" className="w-12 h-12 object-contain rounded" />
          ) : (
            <div className="w-12 h-12 rounded-full bg-gradient-to-tr from-yellow-400 via-orange-300 to-red-400 flex items-center justify-center text-white font-bold">FP</div>
          )}
          <div>
            <div className="font-bold text-lg">Fusion Palate</div>
            <div className="text-xs text-gray-500">Authentic good fusion food · Berlin</div>
          </div>
        </Link>

        <nav className="hidden md:flex gap-6 text-sm">
          {Array.isArray(nav) && nav.map(item => (
            <Link key={item.href} href={item.href}>{item.label}</Link>
          ))}
          <Link href="/contact" className="bg-[var(--accent)] text-white px-3 py-2 rounded-lg">Book</Link>
        </nav>
      </div>
    </header>
  )
}

/* ---------- components/Footer.jsx ---------- */
// Save as components/Footer.jsx
export default function Footer(){
  return (
    <footer className="bg-white border-t mt-12 py-6">
      <div className="max-w-6xl mx-auto px-6 text-sm text-gray-600 flex flex-col md:flex-row justify-between">
        <div>© {new Date().getFullYear()} Fusion Palate — Berlin</div>
        <div className="mt-2 md:mt-0">hello@fusionpalate.berlin · +49 30 1234 5678</div>
      </div>
    </footer>
  )
}

/* ---------- components/Hero.jsx ---------- */
// Save as components/Hero.jsx
export default function Hero(){
  return (
    <section className="rounded-3xl overflow-hidden shadow-lg mt-6">
      <div className="h-64 bg-cover bg-center flex items-center justify-center" style={{backgroundImage: "url('/hero.jpg')"}}>
        <div className="bg-black/40 p-6 rounded-xl text-center">
          <h1 className="text-4xl font-extrabold text-white">Fusion Palate</h1>
          <p className="text-gray-200 mt-2">Authentic African fusion with a touch of luxury — Berlin catering & pop-ups</p>
        </div>
      </div>
    </section>
  )
}

/* ---------- components/DishCard.jsx ---------- */
// Save as components/DishCard.jsx
export default function DishCard({name, img}){
  return (
    <div className="rounded-2xl overflow-hidden shadow bg-white">
      <img src={img} alt={name} className="h-40 w-full object-cover" />
      <div className="p-4">
        <h3 className="font-semibold">{name}</h3>
      </div>
    </div>
  )
}

/* ---------- styles/variables.css ---------- */
:root{
  --accent: #D95D39;
  --accent-2: #F6C667;
  --bg: #F8F8F5;
  --text: #1F2937;
  --muted: #6B7280;
  --luxury: #0F172A;
}

/* ---------- app/globals.css ---------- */
@import '../styles/variables.css';
@tailwind base;
@tailwind components;
@tailwind utilities;

body { font-family: Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; background-color: var(--bg); color: var(--text); }

/* ---------- End of project files ---------- */
