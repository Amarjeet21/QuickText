# QuickText - Image to Text Converter

A production-ready React.js (Vite) application that converts images into text using Google Gemini AI with a beautiful glassmorphism UI.

**Live URL:** https://quicktext-omega.vercel.app

![QuickText Preview](https://via.placeholder.com/800x400/667eea/ffffff?text=QuickText+Preview)

## Features

- **Drag & Drop Upload** - Easily drop images or click to browse
- **AI-Powered OCR** - Extract text from images using Google Gemini AI
- **Copy to Clipboard** - One-click copy of extracted text
- **Download Options** - Save as TXT or PDF
- **Custom PDF Header** - logo, name, address, phone
- **Custom PDF Footer** - Email and website
- **Modern UI** - Glassmorphism design with smooth animations
- **Responsive** - Works on desktop, tablet, and mobile
- **Toast Notifications** - Real-time feedback for all actions

## Tech Stack

| Technology | Purpose |
|------------|---------|
| **React 19.2.4** | UI Framework |
| **Vite 8.0.1** | Build Tool |
| **Google Gemini API** | AI Text Extraction (gemini-2.5-flash-lite) |
| **jsPDF 4.2.1** | PDF Generation |
| **Framer Motion** | Animations |
| **Lucide React** | Icons |
| **Axios** | HTTP Client |
| **Vercel** | Deployment |

## Project Structure

```
QuickText/
├── src/
│   ├── components/
│   │   ├── DropZone/          - Drag & drop file upload
│   │   ├── ImagePreview/      - Image preview with remove
│   │   ├── ResultPanel/       - Text output with actions
│   │   ├── Header/            - App header with logo
│   │   ├── Toast/             - Toast notifications
│   │   └── LoadingSpinner/    - Loading animation
│   ├── services/
│   │   └── geminiApi.js       - Gemini API integration
│   ├── utils/
│   │   ├── fileUtils.js       - File handling utilities
│   │   ├── downloadUtils.js   - TXT/PDF download
│   │   └── validationUtils.js - Validation functions
│   ├── hooks/
│   │   └── useToast.js        - Toast notification hook
│   ├── styles/
│   │   ├── variables.css      - CSS custom properties
│   │   └── global.css        - Global styles
│   ├── App.jsx                - Main app component
│   └── main.jsx               - Entry point
├── public/
│   └── gmr-logo-color.png    - PDF header logo
├── .env.example               - Environment template
├── index.html                 - HTML entry
├── package.json               - Dependencies
├── vite.config.js             - Vite config
└── README.md                  - This file
```

## PDF Customization

### Header (Sky-Blue Background)
- GMR Logo (right side)
- GMR SCAN REPORT (left side)
- 2552 Walnut Ave. Suite 100 Tustin, CA 92780
- Phone: 800-523-7187

### Footer (Sky-Blue Background)
- Email: **************
- Website: ***************

## Setup Instructions

### 1. Clone the repository

```bash
git clone <repository-url>
cd QuickText
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure API Key

1. Copy the example environment file:
```bash
cp .env.example .env
```

2. Get your Gemini API key:
   - Go to [Google AI Studio](https://aistudio.google.com/app/apikey)
   - Create a new API key
   - Copy the key

3. Add your API key to `.env`:
```
VITE_GEMINI_API_KEY=your_actual_api_key_here
```

### 4. Start development server

```bash
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### 5. Build for production

```bash
npm run build
```

## Deployment

### Vercel (Recommended)

1. Install Vercel CLI:
```bash
npm i -g vercel
```

2. Login to Vercel:
```bash
vercel login
```

3. Deploy:
```bash
vercel --prod
```

4. Add environment variable in Vercel dashboard:
   - Go to Settings → Environment Variables
   - Add `VITE_GEMINI_API_KEY` with your API key

## Security Considerations ⚠️

### API Key Exposure Risk

This is a **frontend-only** application, which means your Gemini API key is exposed in the browser. Anyone can view it in Developer Tools → Network or Application tab.

**Mitigations:**

1. **Domain Restriction** (Quick Fix):
   - Go to [Google Cloud Console](https://console.cloud.google.com/)
   - Navigate to APIs & Services → Credentials
   - Edit your API key
   - Under "Website restrictions", add your deployed domain

2. **Use a Proxy** (Better):
   - Deploy a simple Cloudflare Worker or Edge Function
   - Forward requests through the worker
   - Worker hides the API key

3. **Full Backend** (Best):
   - Add a Node.js backend
   - Backend makes API calls
   - Frontend never sees the key

## Troubleshooting

### "API key is missing"
- Make sure you've created a `.env` file with `VITE_GEMINI_API_KEY`
- Restart the dev server after adding the key

### "Invalid file type"
- Supported formats: JPG, PNG, WebP, GIF, BMP

### "File too large"
- Maximum file size: 10MB

### "Rate limit exceeded"
- Wait a minute, then try again
- Check your Google Cloud quota

### "No text found in image"
- The image might not contain readable text
- Try a clearer image with better contrast

## License

MIT License - Feel free to use this for personal or commercial projects.

---

Made with ❤️ using React, Vite, and Gemini API
