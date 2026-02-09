# Timestamp Microservice API

<table>
<tr>
<td width="200">
<div align="center">
<img width="180" height="180" alt="Timestamp Icon" src="https://raw.githubusercontent.com/freeCodeCamp/freeCodeCamp/main/docs/images/icons/clock.svg" />
</div>
</td>
<td>
  <h3>A RESTful Microservice for Unix & UTC Timestamp Conversion</h3>
  
  **Core Capabilities:**
  - 🕐 Current Timestamp Retrieval
  - 🔄 Unix to UTC Conversion
  - 📅 UTC to Unix Conversion
  - ✅ Date Validation & Error Handling
  - ⚡ Fast & Lightweight API
  - 🎯 FreeCodeCamp Certified Project
</td>
</tr>
</table>

<p align="center"> 
  <a href="https://timestamp-microservice.andradeoromulo.repl.co/"><img alt="Live Demo" src="https://img.shields.io/badge/demo-live-brightgreen?style=for-the-badge" /></a>
  <a href="https://www.freecodecamp.org/learn/apis-and-microservices/"><img alt="FreeCodeCamp" src="https://img.shields.io/badge/FreeCodeCamp-Certified-success?style=for-the-badge&logo=freecodecamp" /></a>
  <a href="https://opensource.org/licenses/MIT"><img alt="License" src="https://img.shields.io/badge/license-MIT-blue?style=for-the-badge" /></a>
  <a href="https://nodejs.org/"><img alt="Node.js" src="https://img.shields.io/badge/node.js-16+-green?style=for-the-badge&logo=node.js" /></a>
</p>

<p align="center">
  <a href="#about">About</a> •
  <a href="#features">Features</a> •
  <a href="#api-endpoints">API Endpoints</a> •
  <a href="#getting-started">Getting Started</a> •
  <a href="#usage-examples">Usage Examples</a> •
  <a href="#technology-stack">Technology Stack</a> •
  <a href="#contributing">Contributing</a>
</p>

---

## About

The **Timestamp Microservice** is a RESTful API built as part of the [freeCodeCamp APIs and Microservices Certification](https://www.freecodecamp.org/learn/apis-and-microservices/). This project demonstrates fundamental backend development concepts including:

- RESTful API design and implementation
- Date/time manipulation and validation
- Error handling and edge case management
- JSON response formatting
- Express.js routing and middleware

Whether you need to convert Unix timestamps to human-readable dates, parse UTC date strings, or simply get the current time in multiple formats, this microservice provides a simple, reliable solution.

---

## Features

### ✨ Current Timestamp
Get the current date and time instantly in both Unix timestamp and UTC format with a single API call.

### ✨ Flexible Date Input
Accepts multiple date formats including:
- Unix timestamps (milliseconds since epoch): `1451001600000`
- ISO-8601 UTC date strings: `2015-12-25`
- Natural date formats: `December 25, 2015`

### ✨ Robust Validation
Intelligent date validation that returns clear error messages for invalid inputs, ensuring your applications handle edge cases gracefully.

### ✨ Zero Configuration
No API keys, authentication, or registration required. Simply call the endpoint and get your response instantly.

### ✨ Cross-Origin Support
CORS-enabled API allows integration from any web application or service without restriction.

---

## API Endpoints

### 📍 GET `/api/timestamp`

Returns the current timestamp in Unix and UTC formats.

**Response:**
```json
{
  "unix": 1708645200000,
  "utc": "Thu, 22 Feb 2024 18:20:00 GMT"
}
```

---

### 📍 GET `/api/timestamp/:date`

Converts the provided date parameter to both Unix timestamp and UTC string.

**Parameters:**
- `date` (string) - Unix timestamp (milliseconds) or UTC date string

**Valid Request Examples:**
```
/api/timestamp/2015-12-25
/api/timestamp/1451001600000
/api/timestamp/December%2025,%202015
```

**Success Response:**
```json
{
  "unix": 1451001600000,
  "utc": "Fri, 25 Dec 2015 00:00:00 GMT"
}
```

**Error Response:**
```json
{
  "error": "Invalid Date"
}
```

---

## Getting Started

### Prerequisites

- **Node.js** 16.x or higher
- **npm** 8.x or higher

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/timestamp-microservice.git
cd timestamp-microservice

# Install dependencies
npm install

# Start the server
npm start
```

The API will be available at `http://localhost:3000`

### Quick Test

```bash
# Test current timestamp
curl http://localhost:3000/api/timestamp

# Test with specific date
curl http://localhost:3000/api/timestamp/2015-12-25

# Test with Unix timestamp
curl http://localhost:3000/api/timestamp/1451001600000
```

---

## Usage Examples

### JavaScript (Fetch API)

```javascript
// Get current timestamp
fetch('https://timestamp-microservice.andradeoromulo.repl.co/api/timestamp')
  .then(response => response.json())
  .then(data => {
    console.log('Current Unix timestamp:', data.unix);
    console.log('Current UTC time:', data.utc);
  });

// Convert specific date
fetch('https://timestamp-microservice.andradeoromulo.repl.co/api/timestamp/2015-12-25')
  .then(response => response.json())
  .then(data => {
    if (data.error) {
      console.error('Invalid date provided');
    } else {
      console.log('Unix:', data.unix);
      console.log('UTC:', data.utc);
    }
  });
```

### Python (Requests)

```python
import requests

# Get current timestamp
response = requests.get('https://timestamp-microservice.andradeoromulo.repl.co/api/timestamp')
data = response.json()
print(f"Unix: {data['unix']}, UTC: {data['utc']}")

# Convert specific date
date_response = requests.get('https://timestamp-microservice.andradeoromulo.repl.co/api/timestamp/1451001600000')
date_data = date_response.json()
print(f"Unix: {date_data['unix']}, UTC: {date_data['utc']}")
```

### cURL

```bash
# Current timestamp
curl https://timestamp-microservice.andradeoromulo.repl.co/api/timestamp

# Specific date (ISO-8601)
curl https://timestamp-microservice.andradeoromulo.repl.co/api/timestamp/2015-12-25

# Unix timestamp
curl https://timestamp-microservice.andradeoromulo.repl.co/api/timestamp/1451001600000

# Invalid date (returns error)
curl https://timestamp-microservice.andradeoromulo.repl.co/api/timestamp/invalid-date
```

---

## Technology Stack

| Technology | Purpose |
|------------|---------|
| **Node.js** | JavaScript runtime environment |
| **Express.js** | Web application framework |
| **JavaScript (ES6+)** | Core programming language |
| **CORS** | Cross-origin resource sharing |

---

## Project Structure

```
timestamp-microservice/
├── server.js           # Main application entry point
├── package.json        # Project dependencies and scripts
├── README.md          # Project documentation
└── public/            # Static files (if any)
```

---

## Development

### Running in Development Mode

```bash
# Install nodemon for auto-restart
npm install -g nodemon

# Run with nodemon
nodemon server.js
```

### Testing

Test the following scenarios to ensure proper functionality:

✅ **Valid Inputs:**
- Current timestamp: `/api/timestamp`
- Valid ISO date: `/api/timestamp/2015-12-25`
- Valid Unix timestamp: `/api/timestamp/1451001600000`

❌ **Invalid Inputs:**
- Invalid date string: `/api/timestamp/invalid-date`
- Malformed timestamp: `/api/timestamp/not-a-number`

---

## Deployment

### Deploy to Repl.it

1. Create account at [Repl.it](https://replit.com/)
2. Import repository from GitHub
3. Click "Run" to start the server
4. Your API is live!

### Deploy to Heroku

```bash
# Login to Heroku
heroku login

# Create new app
heroku create your-timestamp-api

# Deploy
git push heroku main

# Open app
heroku open
```

### Deploy to Vercel

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel
```

---

## Contributing

Contributions, issues, and feature requests are welcome! This is a learning project, so feedback is especially appreciated.

### How to Contribute

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add some amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Areas for Improvement

- [ ] Add support for different time zones
- [ ] Implement rate limiting
- [ ] Add comprehensive test suite
- [ ] Support for additional date formats
- [ ] API documentation page
- [ ] Response caching for performance

---

## License

This project is licensed under the **MIT License** - see the LICENSE file for details.

---

## Acknowledgments

- **freeCodeCamp** - For the excellent curriculum and project specifications
- **Express.js Team** - For the robust web framework
- **Node.js Community** - For comprehensive documentation and support

---

## Contact & Feedback

I'm a student developer working on the freeCodeCamp Backend and API certification. I'd love to hear your feedback, suggestions, or corrections! 🤓

- **Live Demo**: [View on Repl.it](https://timestamp-microservice.andradeoromulo.repl.co/)
- **Challenge**: [FreeCodeCamp Project Page](https://www.freecodecamp.org/learn/apis-and-microservices/apis-and-microservices-projects/timestamp-microservice)
- **Issues**: [Report a Bug](https://github.com/yourusername/timestamp-microservice/issues)

---

<div align="center">

### Built with 💻 as part of the freeCodeCamp Curriculum

**[Live Demo](https://timestamp-microservice.andradeoromulo.repl.co/)** • 
**[freeCodeCamp Profile](https://www.freecodecamp.org/yourusername)** • 
**[GitHub](https://github.com/yourusername)**

⭐ **Star this repo if you found it helpful!** ⭐

---

*Part of my journey learning Backend Development and APIs*

</div>
