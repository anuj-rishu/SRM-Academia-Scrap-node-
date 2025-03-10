# SRM Academia API

A comprehensive Node.js API server that scrapes and serves SRM University academic data including courses, attendance, timetables, and more.

## Overview
This API provides programmatic access to SRM Academia data through a RESTful interface. It handles authentication, scraping, and data formatting to deliver structured information that can be used in various applications.

## Features

### Authentication System
- Secure login with SRM credentials
- Token-based authentication
- Automatic session management

### Academic Information
- Course details and registration data
- Current attendance percentages
- Academic calendar & day order
- Internal marks and test scores
- Complete timetable with room numbers
- User profile and photo

### Class Scheduling
- Today's class schedule
- Upcoming classes with time remaining

### Performance Optimizations
- Response caching (2-minute TTL)
- Compression for faster data transfer
- ETag support for bandwidth savings
- Rate limiting to prevent abuse

## Tech Stack
- **Node.js** - JavaScript runtime
- **Express.js** - Web application framework
- **Axios** - HTTP client for requests
- **Cheerio** - HTML parsing and scraping
- **CORS** - Cross-origin resource sharing
- **Compression** - Response compression
- **Rate Limiting** - Request throttling

## Installation

### Clone the repository
```sh
 git clone https://github.com/anuj-rishu/SRM-Academia-Scrap-node-
 cd SRM-Academia-Scrap-node-
```

### Install dependencies
```sh
 npm install
```



### Start the server
```sh
 npm start
```

## API Endpoints

### Authentication
| Method | Endpoint | Description | Request Body | Auth Required |
|--------|---------|-------------|--------------|--------------|
| POST   | `/login` | User login  | `{ "account": "email@srmist.edu.in", "password": "yourpassword" }` | No |
| DELETE | `/logout` | User logout | None | Yes |

### Academic Data
| Method | Endpoint | Description | Auth Required |
|--------|---------|-------------|--------------|
| GET    | `/courses` | Get registered courses | Yes |
| GET    | `/attendance` | Get attendance details | Yes |
| GET    | `/marks` | Get internal marks & test scores | Yes |
| GET    | `/timetable` | Get complete timetable | Yes |
| GET    | `/calendar` | Get academic calendar | Yes |
| GET    | `/dayorder` | Get today's day order | Yes |
| GET    | `/profile` | Get detailed profile information | Yes |
| GET    | `/user` | Get basic user information | Yes |

### Class Scheduling
| Method | Endpoint | Description | Auth Required |
|--------|---------|-------------|--------------|
| GET    | `/today-classes` | Get today's classes | Yes |
| GET    | `/upcoming-classes` | Get upcoming classes | Yes |

## Authentication
The API uses token-based authentication. After a successful login, you'll receive a token that should be included in subsequent requests as an `X-CSRF-Token` header.

Example:
```sh
curl -H "X-CSRF-Token: your_token" http://localhost:9000/attendance
```

## Error Handling
The API returns appropriate HTTP status codes:
- **200**: Success
- **400**: Bad Request (missing parameters)
- **401**: Unauthorized (invalid token)
- **403**: Forbidden (access denied)
- **429**: Too Many Requests (rate limit exceeded)
- **500**: Server Error

## Rate Limiting
Requests are limited to **500 requests per 15-minute window** to prevent abuse.

## Caching
Responses are cached for **2 minutes** to improve performance and reduce load on the SRM servers.

## Project Structure
```
.
├── controllers  # Handles request logic
├── middlewares  # Authentication and security middleware
├── models       # Database schemas
├── routes       # API route definitions
├── services     # Business logic and API requests
├── utils        # Helper functions
└── index.js     # Main server file
```

## Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License
This project is licensed under the **Apache License 2.0** - see the [LICENSE](LICENSE) file for details.

## Disclaimer
This project is **not officially affiliated** with SRM Institute of Science and Technology. It is created for **educational purposes** and personal use only.

---
Developed by **Anuj Rishu Tiwari**

GitHub: [anuj-rishu](https://github.com/anuj-rishu)
LinkedIn: [anuj-rishu](https://linkedin.com/in/anuj-rishu)

