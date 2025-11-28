# TravelHub Setup Guide
## Cliqtrix 2025 Contest

### Prerequisites

Before you begin, ensure you have the following:

1. **Zoho SalesIQ Account**
   - Sign up at https://www.zoho.com/salesiq/
   - Create a free account

2. **Website**
   - Use Zoho Sites (free) or Weebly
   - Alternative: Use existing website

3. **External CRM** (Choose one)
   - MongoDB Atlas (Free tier available)
   - Google Sheets
   - AirTable
   - Note: DO NOT use Zoho CRM or Salesforce

4. **Payment Gateway** (Choose one)
   - Stripe (Global)
   - Razorpay (India-focused)

5. **OTP Service** (Choose one)
   - Twilio
   - AWS SNS

6. **AI Service**
   - OpenAI API for recommendations

### Step-by-Step Setup

#### 1. Zoho SalesIQ Setup

```bash
# Go to Zoho SalesIQ
https://www.zoho.com/salesiq/

# Create account and verify email
# Create a new website or add to existing one
# Go to Settings > Live Chat Widget
# Copy the tracking code and add to your website
```

#### 2. Create External CRM (Google Sheets Example)

```bash
# Create a Google Sheet with these columns:
- id (auto-increment)
- name (visitor name)
- email (visitor email)
- phone (phone number)
- package_selected (package ID)
- created_date (timestamp)
- source (source of lead)

# Share the sheet and generate API key
# Use Google Sheets API v4
```

#### 3. Configure API Keys

```bash
# Copy config/api-keys-template.env to config/api-keys.env
cp config/api-keys-template.env config/api-keys.env

# Edit and add your actual API keys
# Get the following:

# CRM API Key
CRM_API_KEY=your_api_key
CRM_API_URL=https://sheets.googleapis.com/v4

# Twilio Setup
TWILIO_ACCOUNT_SID=ACxxxxxxxxxxxxxxxxxx
TWILIO_AUTH_TOKEN=your_auth_token
TWILIO_PHONE_NUMBER=+1234567890

# Stripe Setup
STRIPE_SECRET_KEY=sk_test_xxxxxxxx
STRIPE_PUBLISHABLE_KEY=pk_test_xxxxxxxx

# OpenAI Setup
OPENAI_API_KEY=sk-xxxxxxxx
```

#### 4. Deploy Bot Code to Zoho SalesIQ

1. **Open Zoho SalesIQ Dashboard**
   - Go to https://www.zoho.com/salesiq/
   - Navigate to Bot Builder

2. **Create New Bot**
   - Click "Create Bot"
   - Choose "Deluge" or "Codeless" builder

3. **Add Bot Code**
   - Copy the code from `bot-code/main.deluge`
   - Paste it into the bot editor
   - Update the API endpoints in the code

4. **Configure Handlers**
   - Set up message handlers for:
     - Featured packages request
     - Find package search
     - My packages/bookings
     - OTP verification
     - Payment processing

5. **Test the Bot**
   - Test on your website
   - Verify all features work:
     - Featured packages display
     - OTP sending/verification
     - CRM lead creation
     - Payment initiation

#### 5. Publish Bot

1. **Test Thoroughly**
   - Go through all user flows
   - Check error handling
   - Verify API connections

2. **Publish to Website**
   - Click "Publish"
   - Generate installation link

3. **Generate Installation Link**
   - Copy the bot installation link
   - Save for Cliqtrix submission

### Testing Checklist

- [ ] Bot responds to messages
- [ ] Featured packages display correctly
- [ ] Package search works with AI recommendations
- [ ] OTP is sent to phone number
- [ ] OTP verification works
- [ ] Lead is created in CRM
- [ ] User can provide feedback
- [ ] User can rebook previous package
- [ ] Payment gateway initializes
- [ ] Bot handles errors gracefully

### Cliqtrix Submission

#### Required Information

1. **GitHub Repository URL**
   ```
   https://github.com/harithanandakumar/cliqtrix-2025-tours-holidays-bot
   ```

2. **Zoho SalesIQ Installation Link**
   ```
   [Generated after publishing bot]
   ```

3. **Bot Description**
   - Highlight all features
   - Mention brownie points (OTP, OAuth, AI)
   - Describe integrations

#### Submission Steps

1. Go to https://zurl.co/CO800
2. Fill in your registration email
3. Select "SalesIQ Zobot" as app type
4. Enter bot name: "TravelHub - Tours & Holidays Chatbot"
5. Paste the SalesIQ installation link
6. Add comprehensive description
7. Paste GitHub repository URL
8. Submit before November 30, 2025 11:59 PM IST

### Troubleshooting

**Bot not responding**
- Check SalesIQ widget is installed on website
- Verify bot is published
- Check browser console for errors

**OTP not sending**
- Verify Twilio credentials
- Check phone number format (+1 XXXXXXXXXX)
- Ensure Twilio account has credits

**Lead not created in CRM**
- Verify API key in config
- Check CRM sheet/database has correct columns
- Test API endpoint with Postman first

**Payment not processing**
- Verify Stripe/Razorpay keys
- Test in sandbox mode first
- Check webhook configuration

### Resources

- [Zoho SalesIQ Help](https://www.zoho.com/salesiq/help/)
- [Deluge Documentation](https://www.zoho.com/deluge/)
- [Twilio SMS API](https://www.twilio.com/docs/sms)
- [Stripe Documentation](https://stripe.com/docs)
- [Razorpay Documentation](https://razorpay.com/docs/)

### Support

For issues:
1. Check troubleshooting section above
2. Review code comments in bot-code/main.deluge
3. Test APIs individually with Postman
4. Check GitHub issues
5. Contact: contact@cliqtrix.com
