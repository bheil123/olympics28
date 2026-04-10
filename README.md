# LA Olympics Ticket Selector

Interactive tool for planning LA 2028 Olympic ticket purchases during timed presale windows.

**Live app:** https://bheil123.github.io/olympics28/ticket_selector.html

## How to Use

### Quick Start
1. Open the [live app](https://bheil123.github.io/olympics28/ticket_selector.html)
2. Check the sports you're interested in from the left sidebar
3. Set your date ranges (3 customizable ranges, can overlap)
4. Use Gender/Discipline filter to narrow to Women's, Men's, or Mixed events
5. Click sessions to select them - a ticket count dropdown (1-12) appears on each
6. Switch to the **Football** tab to select football/soccer sessions separately
7. Check the **Calendar** tab to see your picks on a weekly grid with conflict warnings
8. Click **Save to Link - Share/Bookmark** to save your selections as a shareable URL

### Features
- **Two ticket pools:** 12 tickets for main events + 12 tickets for football (soccer), tracked separately
- **Per-session ticket counts:** Each selected session gets its own ticket quantity (1-12)
- **Gender tags:** Sessions tagged as Women's (W), Men's (M), or Mixed (M/W)
- **Conflict detection:** Warns when selected sessions overlap in time on the same day
- **Custom date ranges:** Define up to 3 date ranges, toggle any combination on/off
- **Football multi-venue:** Check any combination of football venues (San Jose, Rose Bowl, etc.)
- **Save/restore:** Bookmark the generated link or share it - all selections are encoded in the URL. Auto-saves to browser localStorage as well.
- **Export:** Download selections as CSV and copy a quick-reference session code list to clipboard
- **Calendar view:** See all selected events on a July 2028 weekly calendar grid
- **Ticket Tracker:** Table view matching the format used by other family members

### Tabs
- **Browse Sessions** - Filter and select from all 843 Olympic sessions
- **Football (Soccer)** - Separate tab for the 12-ticket football pool with venue filtering
- **Ticket Tracker** - Table summary of all picks with session codes, times, and ticket counts
- **Calendar** - Visual weekly calendar (July 10-30) showing selected events by day

## Data Sources

All session data was extracted from official LA 2028 Olympic competition schedule PDFs (Version 3.0, dated March 16, 2026):

| PDF | Description | Contents |
|-----|-------------|----------|
| `LA28OlympicGamesCompetitionScheduleByEventV3.0.pdf` | **Primary data source** | 843 sessions with Sport, Venue, Zone, Session Code, Date, Games Day, Session Type, Description, Start/End times |
| `LA28OlympicGamesCompetitionScheduleByDayV3.0.pdf` | Schedule organized by day | Cross-reference for daily schedule layout |
| `LA28OlympicGamesCompetitionScheduleBySessionV3.0.pdf` | Visual grid by venue/session | Cross-reference for venue-based session view |

### Data extraction process
1. PDFs were parsed using Python (`pdfplumber` library) to extract tabular data
2. Session codes were mapped to sport names using the 2-4 letter prefix system (e.g., GAR = Artistic Gymnastics, ATH = Athletics, FBL = Football)
3. Gender classification (Women's/Men's/Mixed) was derived from session descriptions
4. Opening/Closing Ceremony sessions were added manually (not in the event-by-event PDF)
5. The extracted data is stored in `all_sessions.json` (843 sessions)

### Important notes from the official schedule
- All times are **Pacific Time (PT)** in 24-hour format
- All dates are in **2028**
- Football (Soccer) kickoff times are **TBD** for group stage and quarterfinal matches
- The schedule is subject to change until the conclusion of the Games
- Gold medal sessions and bronze medal sessions are distinguished in the source data

## Files

| File | Purpose |
|------|---------|
| `ticket_selector.html` | The main interactive app (single HTML file, no dependencies) |
| `all_sessions.json` | Extracted session data (843 sessions) used by the app |
| `all_sessions.csv` | Same data in CSV format for spreadsheet use |
| `LA2028_Ticket_Selector.xlsx` | Excel workbook with multiple sheets (Gymnastics, Athletics, Football focus views) |
| `extract_data.py` | Python script used to extract data from the source PDFs |

## Key Dates

- **July 10-13:** Football preliminaries begin (pre-Opening Ceremony)
- **July 14:** Opening Ceremony (Day 0)
- **July 15-29:** Competition days (Day 1-15)
- **July 30:** Closing Ceremony (Day 16)

## Football Venues

Football (soccer) is played at venues across the US, not just LA:

| Venue | Location | Events |
|-------|----------|--------|
| San Jose Stadium | San Jose, CA | Women's group stage + quarterfinal |
| Rose Bowl Stadium | Pasadena, CA | Women's QF, Men's/Women's SF, Gold Medal matches |
| San Diego Stadium | San Diego, CA | Women's group + QF, Men's/Women's SF, Bronze matches |
| Nashville Stadium | Nashville, TN | Men's/Women's group + QF |
| Columbus Stadium | Columbus, OH | Men's/Women's group + QF |
| New York Stadium | New York, NY | Men's/Women's group + QF |
| St. Louis Stadium | St. Louis, MO | Men's/Women's group + QF |
