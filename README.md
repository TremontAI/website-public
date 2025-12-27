# Tremont AI Static Website

A minimal, verification-ready public website for Tremont AI. This site is built with plain HTML/CSS and is designed to be performant, accessible, and easily deployable.

## Project Structure

```
tremont-site/
├── assets/
│   └── logo-placeholder.svg
├── css/ (mapped to root styles.css in this build)
├── index.html
├── privacy.html
├── security.html
├── terms.html
├── robots.txt
├── sitemap.xml
└── styles.css
```

## Local Preview

To preview the site locally, run a simple HTTP server in the project directory:

```bash
# Python 3
python3 -m http.server

# Node.js (if installed)
npx serve .
```

Then visit `http://localhost:8000` in your browser.

## Deployment

### Option 1: AWS S3 + CloudFront (Recommended)

1.  **Create an S3 Bucket**:
    *   Name: `your-domain-name` (e.g., tremont.ai).
    *   Uncheck "Block all public access" (if using S3 website hosting directly) OR keep blocked and use CloudFront OAI/OAC (more secure).
    *   Enable "Static website hosting" in properties if not using CloudFront OAC.

2.  **Upload Content**:
    *   Upload all files in `tremont-site/` to the root of the bucket.
    *   Ensure permissions allow public read (or use bucket policy).

3.  **Configure CloudFront**:
    *   Create a Distribution.
    *   Origin Domain: Select your S3 bucket.
    *   Viewer Protocol Policy: Redirect HTTP to HTTPS.
    *   Default Root Object: `index.html`.
    *   Alternat Domain Names (CNAMEs): `tremont.ai`, `www.tremont.ai`.
    *   SSL Certificate: Request a free certificate in AWS ACM (us-east-1).

### Option 2: Vercel (Alternative)

1.  Install Vercel CLI: `npm i -g vercel`
2.  Run `vercel` in the `tremont-site` directory.
3.  Follow the prompts. Vercel will automatically detect the static HTML files and deploy them globally with SSL.

## Placeholders

Before final launch, ensure you replace the following tokens in all files:
- `{{YOUR_DOMAIN}}`
- `{{LEGAL_NAME}}`
- `{{PHONE}}`
- `{{CITY}}`, `{{STATE}}`, `{{COUNTRY}}`
- `{{LINKEDIN_URL}}`
- `2025`
