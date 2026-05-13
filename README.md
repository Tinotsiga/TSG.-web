# TSG.connect - Login Page

A professional and responsive login page built with HTML and CSS featuring a modern red and white theme.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [HTTPS Configuration](#https-configuration)
- [Project Structure](#project-structure)
- [Technologies Used](#technologies-used)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Overview

TSG.connect is a clean and modern login page designed for user authentication. It provides a user-friendly interface with form validation and responsive design that works seamlessly across all devices.

## ✨ Features

- **Responsive Design**: Works perfectly on desktop, tablet, and mobile devices
- **Modern UI**: Red and white color scheme with smooth animations
- **Form Validation**: Input fields with focus states and hover effects
- **User-Friendly**: Intuitive form with clear labels and organized layout
- **Accessibility**: Proper semantic HTML and accessible form elements
- **Cross-Browser Compatible**: Works on all modern browsers

## 🚀 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Tinotsiga/TSG.-web.git
   ```

2. **Navigate to the project directory**
   ```bash
   cd TSG.-web
   ```

3. **Open the project in your browser**
   - Simply open `index.html` in your preferred web browser
   - Or use a local server (see HTTPS Configuration section)

## 💻 Usage

### Running Locally

**Option 1: Direct Browser Opening**
- Open the `index.html` file directly in your browser

**Option 2: Using Python (Local Server)**
```bash
# Python 3
python -m http.server 8000

# Then visit: http://localhost:8000
```

**Option 3: Using Node.js (Live Server)**
```bash
# Install live-server globally
npm install -g live-server

# Run live-server
live-server

# Visit: http://127.0.0.1:8080
```

## 🔒 HTTPS Configuration

### For Development (Local HTTPS)

**Using Python with Self-Signed Certificate:**
```bash
# Generate self-signed certificate (valid for 365 days)
openssl req -x509 -newkey rsa:4096 -nodes -out cert.pem -keyout key.pem -days 365

# Run HTTPS server with Python
python3 -m http.server --certificate cert.pem --key key.pem 8443
```

**Using Node.js with Express:**
```bash
npm install express
```

Create `server.js`:
```javascript
const express = require('express');
const https = require('https');
const fs = require('fs');
const path = require('path');

const app = express();

// Serve static files
app.use(express.static(path.join(__dirname)));

// HTTPS options
const options = {
  key: fs.readFileSync('key.pem'),
  cert: fs.readFileSync('cert.pem')
};

// Create HTTPS server
https.createServer(options, app).listen(8443, () => {
  console.log('HTTPS Server running at https://localhost:8443');
});
```

Run with:
```bash
node server.js
```

### For Production (Let's Encrypt)

**Using Nginx with Let's Encrypt:**

1. **Install Certbot**
   ```bash
   sudo apt-get update
   sudo apt-get install certbot python3-certbot-nginx
   ```

2. **Obtain Certificate**
   ```bash
   sudo certbot certonly --nginx -d yourdomain.com
   ```

3. **Configure Nginx**
   ```nginx
   server {
       listen 443 ssl http2;
       server_name yourdomain.com;

       ssl_certificate /etc/letsencrypt/live/yourdomain.com/fullchain.pem;
       ssl_certificate_key /etc/letsencrypt/live/yourdomain.com/privkey.pem;

       root /var/www/tsg-web;
       index index.html;

       location / {
           try_files $uri $uri/ =404;
       }
   }

   # Redirect HTTP to HTTPS
   server {
       listen 80;
       server_name yourdomain.com;
       return 301 https://$server_name$request_uri;
   }
   ```

4. **Restart Nginx**
   ```bash
   sudo systemctl restart nginx
   ```

### Using GitHub Pages (Free HTTPS)

1. **Enable GitHub Pages** in repository settings
2. **HTTPS is automatically enabled** for `username.github.io` domains
3. **Access your site:**
   ```
   https://tinotsiga.github.io/TSG.-web/
   ```

## 📁 Project Structure

```
TSG.-web/
├── index.html          # Main HTML file
├── Style.css           # CSS stylesheet (red & white theme)
├── script.js           # JavaScript file (if needed)
├── README.md           # Documentation (this file)
└── .gitignore          # Git ignore file
```

## 🛠️ Technologies Used

- **HTML5**: Semantic markup and form elements
- **CSS3**: Modern styling with animations and responsive design
- **JavaScript**: Form handling and validation
- **Git/GitHub**: Version control and repository hosting

## 📝 Form Fields

- **Username**: Text input for user identification
- **Email**: Email input field
- **Phone**: Telephone input field
- **Gender**: Radio button selection (Male/Female)
- **Password**: Secure password input field
- **Submit**: Form submission button

## 🎨 Color Scheme

- **Primary Red**: `#dc3545`
- **Secondary Red**: `#c82333`
- **White**: `#ffffff`
- **Background**: Light gray gradient `#f5f5f5` to `#ffffff`

## 🔐 Security Considerations

1. **Never use HTTP in production** - Always use HTTPS
2. **Validate form data** on both client and server side
3. **Use secure password handling** - Hash passwords server-side
4. **Implement CSRF protection** - Add CSRF tokens to forms
5. **Use Content Security Policy (CSP)** headers
6. **Keep dependencies updated** - Regular security audits

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the MIT License.

## 📞 Contact

For questions or support, please contact:
- **Email**: tinotsiga0@gmail.com
- **GitHub**: [@Tinotsiga](https://github.com/Tinotsiga)
- **Repository**: [TSG.-web](https://github.com/Tinotsiga/TSG.-web)

---

**Last Updated**: May 13, 2026
