# RK Automation - License-Gated Dashboard Configuration

## n8n Webhook Configuration

### Required Webhooks

#### 1. License Verification Webhook
- **URL**: `https://YOUR-N8N-DOMAIN/webhook/verify-license`
- **Method**: POST
- **Expected Input**: 
  ```json
  {
    "license_key": "string"
  }
  ```
- **Expected Output**:
  ```json
  {
    "valid": true/false
  }
  ```

#### 2. Invoice Generator Webhook
- **URL**: `https://YOUR-N8N-DOMAIN/webhook/invoice-generator`
- **Method**: POST
- **Expected Input**:
  ```json
  {
    "license_key": "string",
    "invoice_data": "string"
  }
  ```
- **Expected Output**:
  ```json
  {
    "invoice_content": "string"
  }
  ```

## Setup Instructions

### 1. Update Webhook URLs
In `script.js`, replace the placeholder URLs with your actual n8n webhook URLs:

```javascript
this.config = {
    licenseVerificationUrl: 'https://your-actual-n8n-domain.com/webhook/verify-license',
    invoiceGeneratorUrl: 'https://your-actual-n8n-domain.com/webhook/invoice-generator',
    licenseKeyStorageKey: 'rk_automation_license_key'
};
```

### 2. Security Considerations

#### License Verification Workflow
- Validate license key against your database
- Check expiration dates
- Verify license status (active, suspended, expired)
- Return appropriate error messages for different failure scenarios

#### Invoice Generator Workflow
- Verify license key before processing
- Implement rate limiting per license
- Log all invoice generation attempts
- Sanitize input data
- Implement proper error handling

### 3. Demo Mode
The current implementation includes demo mode functionality:
- Any non-empty license key is accepted for testing
- Mock invoice generation when n8n webhooks are unavailable
- Remove demo mode code before production deployment

### 4. Production Deployment Checklist

- [ ] Replace placeholder webhook URLs with actual endpoints
- [ ] Remove demo mode code
- [ ] Implement proper license validation logic
- [ ] Add rate limiting
- [ ] Set up monitoring and logging
- [ ] Test all error scenarios
- [ ] Implement proper CORS headers
- [ ] Add API authentication if needed

## Extending the Dashboard

### Adding New Tools

To add new tools to the dashboard:

1. **Add HTML Structure**:
   ```html
   <div class="dashboard-card new-tool-card">
       <div class="card-header">
           <div class="card-icon">
               <i class="fas fa-your-icon"></i>
           </div>
           <div class="card-title">
               <h4>Your Tool Name</h4>
               <p>Tool description</p>
           </div>
       </div>
       <div class="card-content">
           <!-- Tool content -->
       </div>
   </div>
   ```

2. **Add CSS Styling**:
   ```css
   .new-tool-card .card-icon {
       background: var(--gradient-your-color);
   }
   ```

3. **Add JavaScript Functionality**:
   ```javascript
   // Add to LicenseGatedDashboard class
   setupNewToolEventListeners() {
       // Your event listeners
   }
   
   async callNewToolAPI(data) {
       // Your API call logic
   }
   ```

### Example: Revision Assistant Tool

```html
<div class="dashboard-card revision-assistant-card">
    <div class="card-header">
        <div class="card-icon">
            <i class="fas fa-edit"></i>
        </div>
        <div class="card-title">
            <h4>Revision Assistant</h4>
            <p>AI-powered invoice revision suggestions</p>
        </div>
    </div>
    <div class="card-content">
        <div class="form-group">
            <label for="revisionData">Invoice to Revise</label>
            <textarea id="revisionData" placeholder="Paste invoice content here..."></textarea>
        </div>
        <button id="suggestRevisionsBtn" class="btn-primary">
            <i class="fas fa-lightbulb"></i>
            Suggest Revisions
        </button>
        <div id="revisionResult" class="result-container" style="display: none;">
            <!-- Revision suggestions -->
        </div>
    </div>
</div>
```

## Testing

### Manual Testing Checklist

- [ ] License form validation
- [ ] License verification with valid/invalid keys
- [ ] Dashboard auto-login with stored license
- [ ] Invoice generation with sample data
- [ ] Error handling for network failures
- [ ] Logout functionality
- [ ] Responsive design on mobile devices
- [ ] Cross-browser compatibility

### Test License Keys

For testing purposes, you can use:
- Valid: Any non-empty string (demo mode)
- Invalid: Empty string or null
- Network error: Disconnect internet to test error handling

## Support

For technical support or customization requests:
- Email: hello@rkautomation.com
- Documentation: [Your documentation URL]
- GitHub Issues: [Your repository URL]
