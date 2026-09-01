# enuacbd.com — Blog Crawl Status Tracker

Live page: **https://aouwalitshikkha.github.io/enuacbd-crawl-status/**

Interactive table of every published blog on [enuacbd.com](https://enuacbd.com), showing:

| Column | Meaning |
|---|---|
| URL | Blog slug + title (linked) |
| Last Modified | Last blog edit, in Dhaka time (UTC+6) |
| Last Crawled by Google | Last Google crawl from Search Console URL Inspection, in Dhaka time |
| Status | OK / STALE / NOT CRAWLED |

## Features

- **Filters** — search by URL/title, filter by status, filter by date range (Last Modified and Last Crawled, independently)
- **Sortable columns** — click any header to sort
- **Live summary cards** — OK / Stale / Not crawled counts update with every filter

## Data pipeline

This page is rebuilt **daily at 3:30 AM Bangladesh time** by a scheduled job that:

1. Fetches all published blogs from the `enuacbd.com` DRF API
2. Runs Google Search Console **URL Inspection** for each URL to get its last crawl time
3. Builds this filterable HTML page and pushes it to this repo (GitHub Pages auto-deploys)

**Last modified** = the blog's `modification_date` from the CMS.  
**Status** = OK when Google's last crawl is newer than the blog's last edit; STALE when the edit is newer than the crawl; NOT CRAWLED when Google has never crawled the URL.

*Crawl and edit times are shown in Dhaka (Asia/Dhaka, UTC+6).*
