# Portfolio Contact Form Setup

This portfolio includes a contact form that can be configured to send emails directly to your inbox using EmailJS.

## Environment Variables Setup

### 1. Copy the Environment File
```bash
cp .env.example .env
```

### 2. EmailJS Configuration (Optional but Recommended)

To enable direct email sending through the contact form:

1. **Sign up for EmailJS**: Go to [https://www.emailjs.com/](https://www.emailjs.com/) and create a free account

2. **Create an Email Service**: 
   - Go to "Email Services" and add your email provider (Gmail, Outlook, etc.)
   - Note down the **Service ID**

3. **Create an Email Template**:
   - Go to "Email Templates" and create a new template
   - Use these template variables in your email template:
     - `{{from_name}}` - Sender's name
     - `{{from_email}}` - Sender's email
     - `{{subject}}` - Email subject
     - `{{message}}` - Email message
     - `{{to_email}}` - Your email (sarweshero@gmail.com)
   - Note down the **Template ID**

4. **Get your Public Key**:
   - Go to "Account" → "General"
   - Copy your **Public Key**

5. **Update your .env file**:
```env
PUBLIC_EMAILJS_PUBLIC_KEY=your_actual_public_key_here
PUBLIC_EMAILJS_SERVICE_ID=your_actual_service_id_here
PUBLIC_EMAILJS_TEMPLATE_ID=your_actual_template_id_here
PUBLIC_CONTACT_EMAIL=sarweshero@gmail.com
```

### 3. Fallback Behavior

If EmailJS is not configured, the contact form will:
- Show a success message
- Open the user's default email client
- Pre-fill the email with the form data
- Direct the email to your contact email address

## Environment Variables Explained

| Variable | Description | Required |
|----------|-------------|----------|
| `PUBLIC_EMAILJS_PUBLIC_KEY` | Your EmailJS public key | Optional |
| `PUBLIC_EMAILJS_SERVICE_ID` | Your EmailJS service ID | Optional |
| `PUBLIC_EMAILJS_TEMPLATE_ID` | Your EmailJS template ID | Optional |
| `PUBLIC_CONTACT_EMAIL` | Your contact email address | Yes |

## Security Notes

- All environment variables starting with `PUBLIC_` are exposed to the client-side
- Never put sensitive/private keys in `PUBLIC_` variables
- The EmailJS public key is safe to expose as it's designed for client-side use
- Keep your `.env` file in `.gitignore` (already included)

## Testing

1. **With EmailJS**: Messages will be sent directly to your email
2. **Without EmailJS**: User's email client will open with pre-filled message

Both methods ensure you receive the contact form submissions!