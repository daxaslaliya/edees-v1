EDEÈS — DEPLOYMENT GUIDE
========================

BEFORE UPLOADING
1. Add your images to /images (see images/README.txt) and your real logo as images/logo.png.
2. Open index.html and edit: PRODUCTS array, address, phone, email, social links.
3. Replace "yourdomain.com" with your real domain in:
   index.html (canonical + og tags), robots.txt, sitemap.xml
   (VS Code: Ctrl+Shift+H -> find yourdomain.com -> replace across files).
4. Open index.html by double-click to test locally.

OPTION A — CPANEL / SHARED HOSTING (GoDaddy, Hostinger, BigRock, etc.)
1. Log in to cPanel -> File Manager -> public_html.
2. Upload everything inside the edees-site folder (not the folder itself), or upload the zip and Extract.
3. Point your domain: in your domain registrar, set the nameservers given by your host
   (or add an A record to the host's IP).
4. In cPanel -> SSL/TLS (or "Let's Encrypt") -> install a free SSL certificate.
   The .htaccess already redirects http -> https and www -> non-www.
   If SSL is not ready yet, delete the HTTPS block in .htaccess temporarily.

OPTION B — VPS / NGINX
1. Upload files to /var/www/edees.
2. Server block: root /var/www/edees; index index.html; error_page 404 /404.html;
3. Run: sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
   (.htaccess does not work on Nginx — ignore it.)

OPTION C — FREE STATIC HOSTING (Netlify / Vercel / Cloudflare Pages)
1. Create an account, choose "Add new site" -> drag and drop the edees-site folder.
2. Open Domain settings -> Add custom domain -> follow the DNS instructions
   (usually: A record to the given IP and CNAME for www).
3. HTTPS is enabled automatically.

DNS BASICS
- A record:     @    -> your server IP
- CNAME record: www  -> yourdomain.com
- DNS changes can take from a few minutes up to 24 hours.

AFTER GOING LIVE
- Submit https://yourdomain.com/sitemap.xml in Google Search Console.
- Test on mobile and check every image loads (file names are case-sensitive on servers: logo.png, not Logo.PNG).
- Note: the bag/checkout is a front-end demo. To take real orders, connect Shopify, WooCommerce or Razorpay.
