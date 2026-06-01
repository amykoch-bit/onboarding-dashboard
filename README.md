# ConductorOne Onboarding Dashboard

People Ops onboarding tracker with Notion, Google Calendar, and Slack integrations.

## Deploy to Vercel (5 minutes)

### Step 1 — Upload to Vercel
1. Go to [vercel.com](https://vercel.com) and sign in (free account)
2. Click **Add New → Project**
3. Drag and drop the `onboarding-dashboard` folder (or zip file)
4. **Before clicking Deploy**, click **"Environment Variables"** and add:
   - Key: `ANTHROPIC_API_KEY`
   - Value: your API key from [console.anthropic.com](https://console.anthropic.com)
5. Click **Deploy** — you'll get a live URL like `https://onboarding-dashboard-xxx.vercel.app`

Your API key stays securely on Vercel's servers and is never exposed in the browser.

### Step 2 — First-time settings
Open your deployed URL and go to the **Settings tab**:
- **Notion database ID** — paste the ID after building your database (see below)
- **Team emails** — Amy, Jenni, Brian, Liz
- **NetUniverse return URL** — the ConductorOne hardware return link

Settings save to your browser only.

---

## Notion database setup

### Automatic (recommended)
Once deployed, open your Vercel URL and use the Notion setup tool — it will create the full database automatically since the API call goes through your server.

### Manual
Create a full-page Table database in Notion named **"New Hire Onboarding Tracker"** with these properties:

| Property | Type | Notes |
|---|---|---|
| Name | Title | |
| Start Date | Date | |
| Location | Select | Options: SF, PDX, Remote |
| Stage | Select | Options: Pre-boarding, Week 1, Week 2, Week 3, Week 4, Complete |
| Role | Text | |
| Manager | Text | |
| Personal Email | Email | |
| Cleary ✓ | Checkbox | |
| Checkr ✓ | Checkbox | |
| Cal Invites ✓ | Checkbox | |
| Union Station ✓ | Checkbox | |
| Sequoia/Niural ✓ | Checkbox | |
| Net Universe ✓ | Checkbox | |
| Days Until Start | Formula | `dateBetween(prop("Start Date"), now(), "days")` |

Add filtered views: All Hires (no filter), SF, PDX, Remote (filter by Location), Starting Soon (Days Until Start < 14).

Get the database ID from the URL — the 32-character string before `?v=` — and paste it into Settings.

---

## Embed in Notion

1. Open your Notion HR / People Ops page
2. Click **+** to add a block → search for **Embed**
3. Paste your Vercel URL
4. Resize to fill the page (~800px height works well)

---

## What each integration does

| Action | What happens |
|---|---|
| Add new hire | Auto-posts to #new-hires in Slack + adds row to Notion |
| Create cal invites | Creates 3 Google Calendar events (first day, anniversary, birthday) |
| Add to Notion | Syncs hire to your Notion database |
| Post to #new-hires | Posts checklist status update to Slack |
| What's missing? | AI prioritization of remaining steps |
| Email laptop return | Sends Gmail with NetUniverse return link |
| Post Checkr removal | Posts reminder to #new-hires |
