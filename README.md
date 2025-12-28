# RK Automation Website

A modern, Apple-esque website for RK Automation's AI-powered invoice automation services, featuring n8n API integration.

## Features

- 🎨 **Modern Design**: Apple-inspired UI with colorful gradients
- 📱 **Responsive**: Mobile-first design that works on all devices
- 🤖 **n8n Integration**: Built-in API integration for invoice automation workflows
- ⚡ **Interactive Demo**: Try the invoice processing functionality
- 📧 **Contact Form**: Lead generation with form validation
- 🚀 **Fast Loading**: Optimized for performance

## Quick Start

### Option 1: Python HTTP Server (Recommended)
```bash
# Navigate to the project directory
cd "RK-front end"

# Start the development server
python3 -m http.server 8000

# Open your browser and visit
# http://localhost:8000
```

### Option 2: Node.js HTTP Server
```bash
# Install a simple HTTP server globally
npm install -g http-server

# Navigate to the project directory
cd "RK-front end"

# Start the server
http-server -p 8000

# Open your browser and visit
# http://localhost:8000
```

### Option 3: Live Server (VS Code)
If you're using VS Code:
1. Install the "Live Server" extension
2. Right-click on `index.html`
3. Select "Open with Live Server"

## Project Structure

```
RK-front end/
├── index.html          # Main HTML file
├── styles.css          # CSS styles with Apple-esque design
├── script.js           # JavaScript with n8n API integration
├── package.json        # Project configuration
└── README.md          # This file
```

## n8n API Integration

The website includes a complete n8n API client for invoice automation:

### Features
- File upload with drag & drop
- Base64 encoding for API transmission
- Mock processing with realistic results
- Error handling and loading states
- Real-time status updates

### Configuration
To connect to your actual n8n instance, update the API endpoint in `script.js`:

```javascript
// Replace with your n8n webhook URL
this.apiEndpoint = 'https://your-n8n-instance.com/webhook/invoice-processor';
```

### API Endpoints Used
- `POST /webhook/invoice-processor` - Process invoice files
- `GET /api/workflows/{id}/status` - Check workflow status
- `POST /api/workflows/{id}/trigger` - Trigger workflows

## Customization

### Colors and Gradients
The website uses CSS custom properties for easy theming. Update the `:root` variables in `styles.css`:

```css
:root {
    --primary-color: #007AFF;
    --secondary-color: #5856D6;
    --accent-color: #FF3B30;
    /* ... more variables */
}
```

### Content Updates
- **Company Info**: Update contact details in the HTML
- **Services**: Modify the services section to match your offerings
- **Branding**: Change the logo and company name throughout the site

## Deployment

### Static Hosting (Recommended)
Deploy to any static hosting service:
- **Netlify**: Drag and drop the folder
- **Vercel**: Connect your GitHub repository
- **GitHub Pages**: Push to a GitHub repository
- **AWS S3**: Upload files to an S3 bucket

### Server Requirements
- No server-side processing required
- Works with any web server
- HTTPS recommended for production

## Browser Support

- Chrome 60+
- Firefox 60+
- Safari 12+
- Edge 79+

## Performance

- Optimized images and fonts
- Minimal JavaScript footprint
- CSS-only animations where possible
- Lazy loading for better performance

## Security

- No sensitive data stored in client-side code
- API keys should be handled server-side
- Form validation on both client and server
- HTTPS required for production

## Support

For technical support or customization requests, contact:
- Email: hello@rkautomation.com
- Phone: +1 (555) 123-4567

## License

MIT License - feel free to use and modify for your projects.
