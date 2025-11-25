# n8n Webhook Configuration Guide

## Production Webhook URL

```
https://lcharyfire1.app.n8n.cloud/webhook/7abdcd0a-09a9-48bf-826f-4d4662e0fde4
```

**This is already configured in `index.html` - No changes needed!**

---

## 🔧 n8n Workflow Setup

### Workflow Structure

Your AudioLearner workflow should have this structure:

```
Webhook Trigger
    ↓
AI Agent (Research & Summarize)
    ↓
Generate Audio Node
    ↓
Respond to Webhook
    ├── Response Type: Binary File
    └── Input Field Name: data
    ↓
Response: "When last node finishes"
```

---

## ✅ Configuration Checklist

### 1. Webhook Trigger Node
- [ ] Path: `/7abdcd0a-09a9-48bf-826f-4d4662e0fde4`
- [ ] Method: POST
- [ ] Response dropdown: **"When last node finishes"** (IMPORTANT!)
- [ ] Workflow is **ACTIVE** (toggle must be ON)

### 2. AI Agent Node
- [ ] Configured to research topics
- [ ] Outputs summarized text
- [ ] Connected to Generate Audio node

### 3. Generate Audio Node
- [ ] Resource: Audio
- [ ] Operation: Generate Audio
- [ ] Model: TTS-1 (or your preference)
- [ ] Text Input: Mapped from AI Agent output
- [ ] Output: Binary audio file

### 4. Respond to Webhook Node
- [ ] Respond With: **Binary File** (CRITICAL)
- [ ] Response Data Source: Specify Myself
- [ ] Input Field Name: `data`
- [ ] Connected from Generate Audio node

---

## 📤 Expected Request/Response

### Frontend Sends (JSON):
```json
{
  "topic": "AI Agents",
  "timePeriod": "Today"
}
```

### Backend Returns:
- **Content-Type**: audio/mpeg
- **Body**: Binary MP3 audio file (4-10 MB typical)

---

## 🧪 Testing Your Webhook

### Test 1: Browser Console
1. Open your AudioLearner app in browser
2. Open DevTools (F12)
3. Go to Console tab
4. Enter topic and select time period
5. Click "Generate Audio"
6. You should see logs like:
```
Sending request to webhook: https://...
Response status: 200
Audio blob size: 5242880 bytes
Audio URL created: blob:https://...
```

### Test 2: Using curl
```bash
curl -X POST https://lcharyfire1.app.n8n.cloud/webhook/7abdcd0a-09a9-48bf-826f-4d4662e0fde4 \
  -H "Content-Type: application/json" \
  -d '{
    "topic": "AI Agents",
    "timePeriod": "Today"
  }' \
  --output test-audio.mp3 \
  -v
```

Expected response:
- HTTP 200 OK
- File size > 1MB
- Can play the MP3 file

### Test 3: Postman
1. Create new POST request
2. URL: `https://lcharyfire1.app.n8n.cloud/webhook/7abdcd0a-09a9-48bf-826f-4d4662e0fde4`
3. Headers: `Content-Type: application/json`
4. Body (raw JSON):
```json
{
  "topic": "Climate Change",
  "timePeriod": "Last week"
}
```
5. Send and verify response

---

## 🔍 Troubleshooting

### Issue: "Failed to fetch" error

**Causes:**
- Workflow is not ACTIVE (toggle OFF)
- Webhook path is incorrect
- Network/CORS issue

**Solutions:**
1. Check workflow toggle is ON (blue)
2. Verify webhook path matches exactly
3. Check n8n Cloud status (https://status.n8n.io)
4. Look at n8n execution logs for errors

---

### Issue: Empty audio file returned

**Causes:**
- "Generate Audio" node not running
- Output not connected properly
- API rate limit exceeded

**Solutions:**
1. Check "Generate Audio" node output
2. Verify "Respond to Webhook" receives data
3. Check n8n error logs
4. Wait a few minutes and try again

---

### Issue: Timeout (>30 seconds)

**Causes:**
- n8n processing is slow
- API requests taking too long
- Free tier rate limits

**Solutions:**
1. Try "Today" time period (faster)
2. Use shorter topics
3. Wait and retry
4. Upgrade n8n plan if persistent

---

### Issue: CORS error

**Causes:**
- Browser blocking cross-origin request
- Webhook not responding to OPTIONS

**Solutions:**
1. This shouldn't happen with n8n webhooks
2. Check browser console for exact error
3. Verify webhook URL is public

---

## 📊 Monitoring

### Check Workflow Execution
1. Go to n8n Cloud Dashboard
2. Open your AudioLearner workflow
3. Click "Executions" tab
4. See all webhook calls:
   - Green ✅ = Success
   - Red ❌ = Failed
   - Gray ⚪ = Running

### Common Execution Issues
- Check input data is received correctly
- Verify each node processes data
- Look at error messages in red boxes
- Check API usage/limits

---

## 🔐 Security

- Webhook URL is public (anyone can call it)
- API keys are hidden in n8n (not exposed)
- No authentication on webhook (you may want to add)
- Audio files are temporary (deleted after session)

### Optional: Add API Key Authentication
You can add an API key requirement:
1. In Webhook trigger, add custom header check
2. Verify Authorization header
3. Only respond to authenticated requests

---

## 📈 API Rate Limits

**OpenAI API:**
- Research: 3 requests/min (free tier)
- Audio generation: 100 requests/day
- Rate limit: Check OpenAI account

**n8n Cloud:**
- Executions: Based on plan
- Webhook calls: Unlimited

---

## 💡 Tips

1. **Test locally first** - Use curl before deploying
2. **Monitor executions** - Check n8n logs for issues
3. **Keep time periods short** - "Today" is fastest
4. **Handle errors gracefully** - App has error messages
5. **Cache results** - Don't regenerate same topic

---

## 📞 Need Help?

**Webhook not responding?**
- Check workflow is active
- Verify path in n8n matches URL in HTML
- Test with curl command above

**Audio not generating?**
- Check "Generate Audio" node configuration
- Verify API keys in n8n
- Check n8n execution logs

**Still stuck?**
- See DEPLOYMENT_GUIDE.md for more help
- Check n8n documentation
- Contact n8n support

---

## ✅ Production Checklist

Before going live:

- [ ] Workflow is ACTIVE
- [ ] Webhook path is correct
- [ ] "Respond to Webhook" is configured
- [ ] Audio generation works in testing
- [ ] Error handling is in place
- [ ] Audio files are generated correctly
- [ ] Browser can download MP3
- [ ] Performance is acceptable

**All set?** Deploy to production! 🚀
