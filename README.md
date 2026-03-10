# InfluenceRank

A Jupyter notebook that finds the top 50 YouTube influencers in a given sector using the free YouTube Data API. No subscription, no scraping, no third-party services.

Built as an open alternative to tools like Modash and HypeAuditor — which do the same thing but charge a few hundred dollars a month for the privilege.

---

## How it works

You pick a sector from a list of 20 (fitness, finance, gaming, food, etc.), point it at your YouTube API key, and run the notebook. It searches YouTube across a set of relevant keywords, pulls channel and video statistics, and produces a ranked list of the top 50 creators in that space.

Each channel gets a **Strength Score out of 100**, made up of five things:

- **Reach (25%)** — subscriber count, log-scaled so one mega-channel doesn't skew everything
- **Engagement (30%)** — average likes and comments relative to average views
- **Authenticity (20%)** — views per subscriber, which is a decent proxy for fake or dead followers. A channel with 800K subscribers and 4K average views is a red flag, and this catches it.
- **Consistency (15%)** — how many videos they've posted in the last 90 days
- **Momentum (10%)** — whether their most recent videos are outperforming their own average

---

## What you need

Just a YouTube Data API v3 key. It's free, takes about five minutes to set up, and gives you 10,000 units a day — enough for around 20 runs.

1. Head to [console.cloud.google.com](https://console.cloud.google.com/) and create a project
2. Go to **APIs & Services > Library**, find **YouTube Data API v3**, and enable it
3. Under **Credentials**, create an API key and copy it
4. Paste it into Cell 2 of the notebook and you're good to go

---

## Running it

```bash
git clone https://github.com/YOUR_USERNAME/influencerank.git
cd influencerank
jupyter notebook youtube_influencer_finder.ipynb
```

Or just open it in Google Colab if you don't want to run anything locally.

All dependencies install automatically in the first cell. Once you've set your API key and chosen a sector, run all cells and let it go. The whole thing takes a couple of minutes depending on how many channels it finds.

---

## What you get

A ranked table in the notebook, plus three charts saved as PNGs — a bar chart of the top 20 by score, a scatter plot mapping engagement against reach, and a radar breakdown for the top 5 channels. The full dataset also exports to a timestamped CSV.

---

## Sectors

Fitness, Finance, Tech, Gaming, Beauty, Fashion, Food, Travel, Business, Education, Music, Sustainability, Parenting, Mental Health, Sports, Art, Cars, DIY, Pets, Politics. You can add your own by dropping a new entry into the `SECTORS` dictionary in Cell 2.

---

## A few caveats

This only covers YouTube. Instagram and TikTok have locked down their APIs to the point where doing this properly isn't feasible without paid access. The authenticity score is a statistical signal, not a forensic audit — it's good at flagging suspicious channels but it's not the same as a full fake-follower analysis.

---

MIT Licence.
