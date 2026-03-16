# Brandon's Buddies Chatbot — Setup Guide

## What You Have
- `api/chat.js` — your secure backend server (deploys to Vercel)
- `vercel.json` — Vercel configuration
- `public/widget.html` — the chat widget code for your WordPress site
- This setup guide

---

## Step 1 — Get Your Anthropic API Key

1. Go to **console.anthropic.com**
2. Sign up for an account (requires a credit card)
3. Go to **API Keys** in the left menu
4. Click **Create Key** and name it "Brandon's Buddies"
5. Copy the key — it starts with `sk-ant-...`
6. Keep this key private — never share it or post it publicly

**Estimated monthly cost at Brandon's Buddies volume: under $5 CAD**

---

## Step 2 — Deploy to Vercel (Free)

1. Go to **vercel.com** and sign up for a free account
2. Click **Add New Project**
3. Choose **Upload** (or connect to GitHub if you use it)
4. Upload the entire `brandons-buddies-chatbot` folder
5. When asked for **Environment Variables**, add:
   - Name: `ANTHROPIC_API_KEY`
   - Value: your API key from Step 1
6. Click **Deploy**
7. Wait about 60 seconds for deployment to complete
8. Copy your deployment URL — it will look like:
   `https://brandons-buddies-chatbot.vercel.app`

---

## Step 3 — Update the Widget with Your Vercel URL

1. Open `public/widget.html` in any text editor
2. Find this line near the bottom:
   ```
   const BB_API_URL = 'YOUR_VERCEL_URL/api/chat';
   ```
3. Replace `YOUR_VERCEL_URL` with your actual Vercel URL:
   ```
   const BB_API_URL = 'https://brandons-buddies-chatbot.vercel.app/api/chat';
   ```
4. Save the file

---

## Step 4 — Add to Your WordPress Site

**Option A — Insert Headers and Footers Plugin (Recommended)**
1. In your WordPress dashboard go to **Plugins > Add New**
2. Search for **"Insert Headers and Footers"** by WPCode
3. Install and activate it
4. Go to **Settings > Insert Headers and Footers**
5. In the **Footer** section, paste the entire contents of `widget.html`
6. Click **Save**
7. Visit your website — the chat button will appear in the bottom right corner

**Option B — Theme Editor**
1. In WordPress go to **Appearance > Theme Editor**
2. Select `footer.php` from the right sidebar
3. Paste the entire contents of `widget.html` just before the `</body>` tag
4. Click **Update File**

---

## Step 5 — Test It

1. Visit brandonsbuddies.org
2. Look for the blue chat button in the bottom right corner
3. Click it and ask a question
4. Test in both English and French
5. Confirm the donation link and shop link work correctly

---

## Updating the Bot's Knowledge

When you add new campaigns, products, or events, update the bot by editing the `SYSTEM_PROMPT` in `api/chat.js`. The prompt contains everything the bot knows. After editing, redeploy to Vercel (free and takes under 60 seconds).

**Examples of updates to make:**
- Add the Buddies Unite walk date once confirmed
- Add Monthly Buddy program details once launched
- Add new t-shirt styles or prices
- Add new events or campaigns

---

## Troubleshooting

**Chat button not appearing:**
- Check that the widget code was saved correctly in WordPress
- Clear your browser cache and try again

**Bot says it can't connect:**
- Verify your Vercel URL is correct in the widget code
- Check that your API key is set correctly in Vercel environment variables
- Visit your Vercel dashboard and check the deployment logs

**CORS error:**
- Open `api/chat.js` and confirm the `Access-Control-Allow-Origin` header matches your exact website URL including https://

---

## Cost Summary

| Service | Monthly Cost |
|---|---|
| Vercel hosting | Free |
| Anthropic API (Claude Haiku) | ~$1–5 CAD at your volume |
| WordPress plugin | Free |
| **Total** | **Under $5 CAD/month** |

---

## For Your Consulting Business

This exact setup — with a different system prompt — works for any business. To adapt it for a new client:

1. Copy the `api/chat.js` file
2. Replace the `SYSTEM_PROMPT` with the client's business information
3. Deploy a new Vercel project for that client
4. Update the widget with the new URL
5. Install on their website

Each client deployment takes approximately 2 hours once you have done it once.
Suggested client fee: $800–$1,500 setup + $100–200/month maintenance

---

*Brandon's Buddies Chatbot — Built with Claude AI*
*Buddies Fight Together. 💙*
