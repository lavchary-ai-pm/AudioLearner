# 🎙️ AudioLearner - AI Audio Lesson Generator

An intelligent AI-powered web application that transforms any topic into a personalized audio lesson in seconds.

## ✨ Features

- **AI-Powered Research**: Researches trending topics and current information
- **Smart Summaries**: Converts complex topics into digestible lessons
- **Voice Generation**: Creates natural-sounding audio from text
- **Time Period Selection**: Choose from Today, Last 3 days, or Last week
- **Download MP3**: Save audio lessons for offline access
- **Responsive Design**: Works seamlessly on desktop and mobile
- **Real-Time Generation**: Get audio instantly
- **Beautiful UI**: Modern dark theme with green accents

## 🚀 Quick Start

### For Users
1. Visit your deployed AudioLearner URL
2. Enter a topic (e.g., "AI Agents", "Climate Change")
3. Select a time period (Today, Last 3 days, or Last week)
4. Click "Generate Audio"
5. Listen to your personalized audio lesson or download as MP3

### For Developers

**What You Need:**
- GitLab account (free)
- Cloudflare account (free tier)
- n8n Cloud instance with configured workflow

## 📦 Deployment Package Contents

```
audiolearner/
├── index.html                  # Main application (LATEST VERSION)
├── README.md                   # This file
├── .gitignore                  # Git configuration
├── WEBHOOK_CONFIG.md          # n8n workflow setup guide
└── DEPLOYMENT_GUIDE.md        # Step-by-step deployment instructions
```

## 🎯 What's New in This Version

✅ **Compact Design** - Minimal white space, everything fits on screen
✅ **Top-Aligned Layout** - No unnecessary scrolling
✅ **Equal-Sized Buttons** - Generate and Clear buttons match
✅ **Optimized Spacing** - Reduced margins and padding
✅ **Mobile Optimized** - Responsive on all devices
✅ **Fast Loading** - Single HTML file, no build process needed

## 🛠️ Technology Stack

- **Frontend**: HTML, CSS (Tailwind), JavaScript (vanilla)
- **Backend**: n8n Cloud Workflows
- **AI**: OpenAI (research, summarization, voice generation)
- **Hosting**: Cloudflare Pages (free)
- **Version Control**: GitLab

## 📋 Setup Instructions

### Step 1: Create GitLab Repository (2 minutes)
1. Go to https://gitlab.com
2. Click "New project" → "Create blank project"
3. Name it: `audiolearner`
4. Set visibility to Public
5. Upload all files from this package

### Step 2: Create Cloudflare Pages Project (5 minutes)
1. Go to https://dash.cloudflare.com
2. Click "Workers & Pages" in sidebar
3. Click "+ Create application" → "Pages" tab
4. Click "Connect to Git" → Authorize GitLab
5. Select `audiolearner` repository
6. **IMPORTANT:** Leave build settings empty
   - Build command: (empty)
   - Build output directory: (empty)
7. Click "Save and deploy"

### Step 3: Configure n8n Webhook (Already Set)
- Webhook URL is already configured in `index.html`
- Production URL: `https://lcharyfire1.app.n8n.cloud/webhook/7abdcd0a-09a9-48bf-826f-4d4662e0fde4`
- No additional setup needed!

### Step 4: Test Your App (5 minutes)
1. Wait for Cloudflare to deploy (1-2 minutes)
2. Visit your Pages URL (shown in Cloudflare Dashboard)
3. Test with:
   - Topic: "AI Agents"
   - Time Period: "Today"
4. Click "Generate Audio"
5. Audio should generate in 10-30 seconds

## ⚡ Performance

- **Load time**: < 1 second
- **Audio generation**: 10-30 seconds (n8n processing)
- **Audio size**: 4-10 MB typical
- **Uptime**: 99.9% (Cloudflare)
- **Cost**: Free tier

## 📱 Responsive Design

- ✅ Desktop (1024px+): Full layout with proper spacing
- ✅ Tablet (768px+): Optimized layout
- ✅ Mobile (<768px): Compact, single-column layout
- ✅ All screen sizes supported

## 🔒 Security

- ✅ HTTPS encryption (Cloudflare)
- ✅ No API keys exposed
- ✅ n8n handles authentication
- ✅ Safe binary file handling
- ✅ HTML escaping for user input

## 📖 Full Documentation

See included files for detailed information:
- **DEPLOYMENT_GUIDE.md** - Complete step-by-step deployment
- **WEBHOOK_CONFIG.md** - n8n workflow configuration
- **README.md** - This file

## 🆘 Troubleshooting

### App won't load
- Check Cloudflare deployment is complete
- Clear browser cache
- Try incognito/private mode

### "Failed to fetch" error
- Check n8n workflow is active
- Verify webhook URL in browser console
- Check n8n Cloud status

### No audio generated
- Verify n8n "Respond to Webhook" node is configured
- Check "Generate Audio" node has correct settings
- Test webhook with curl command (see WEBHOOK_CONFIG.md)

### Slow responses
- n8n free tier has rate limits
- Try shorter time periods (Today works best)
- Wait a few minutes and try again

## 💡 Tips for Best Results

1. **Use short time periods** - "Today" generates fastest
2. **Specific topics work better** - "AI Agents" beats "Technology"
3. **Test during off-peak hours** - Faster API responses
4. **Download immediately** - Audio URLs expire after session

## 🚀 Next Steps After Deployment

1. **Add custom domain** - Point your domain to Cloudflare Pages
2. **Set up analytics** - Monitor traffic and usage
3. **Collect feedback** - Improve based on user feedback
4. **Promote** - Share on social media, portfolio, LinkedIn
5. **Enhance** - Add more features, improve UI/UX

## 📞 Support

For issues with:
- **Deployment**: See DEPLOYMENT_GUIDE.md
- **n8n setup**: See WEBHOOK_CONFIG.md
- **General questions**: Check this README

## 📄 License

MIT License - Feel free to use and modify

---

**Ready to deploy?** Follow the Quick Start instructions above and you'll be live in ~15 minutes! 🎉

**Need help?** Check DEPLOYMENT_GUIDE.md for detailed instructions.

**Questions?** See WEBHOOK_CONFIG.md for technical details.
