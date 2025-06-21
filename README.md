# Textura Backend

A Node.js Express server for the Textura e-commerce application that provides product data and image assets.

## Prerequisites

- Node.js (v14 or higher)
- npm (v6 or higher)

## Installation

Follow these steps to set up the backend server:

```bash
# Clone the repository
git clone https://github.com/PhucFanMu20Nams/texturafontback.git

# Navigate to the backend directory
cd texturafontback/backend

# Install dependencies
npm install
```

## Project Structure

```
textura-backend/
├── .gitignore          # Git ignore rules
├── package.json        # Node.js dependencies and scripts
├── server.js           # Main server entry point
├── data/               # Data files
│   └── products.json   # Product catalog information
├── images/             # Optimized images for serving
│   └── products/       # Product images
├── original-images/    # High-quality original images
└── routes/
    └── products.js     # Product API endpoints
```

## Running the Server

Start the backend server with:

```bash
node server.js
```

The server will run at http://localhost:5000.

You should see the message: `Server running on port 5000`

## API Endpoints

### Product Routes

| Endpoint | Method | Description | Query Parameters |
|----------|--------|-------------|-----------------|
| `/api/products` | GET | Get all products | `page`: Page number (default: 1)<br>`limit`: Products per page (default: 12) |
| `/api/products/:id` | GET | Get product by ID | - |

### Image Routes

Images can be accessed directly via:
- `/images/products/[filename]`

Example: http://localhost:5000/images/products/lightweight-linen-shirt.jpg

## CORS Configuration

The server is configured to allow cross-origin requests, making it suitable for local development with a separate frontend application (typically running on a different port like 5173).

## Troubleshooting

### CORS Issues

If you encounter CORS issues when accessing images, check that the following settings are correctly configured in server.js:

```javascript
app.use(helmet.crossOriginResourcePolicy({ 
  policy: "cross-origin" 
}));

app.use(cors({
  origin: true,
  credentials: true
}));
```

### Image Loading Problems

If images aren't loading properly, ensure:
1. The image files exist in the correct location
2. File permissions allow the server to read the files
3. The paths in products.json correctly reference the images

## Development

To modify the product catalog, edit products.json. The server will load changes on restart.

## License

This project is proprietary. All rights reserved.
