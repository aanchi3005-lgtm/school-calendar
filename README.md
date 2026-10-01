# Class Calendar Maker

A one-page website that turns the school's printed yearly planner into a colour-coded calendar for one class, ready to print.

**Live site:** https://aanchi3005-lgtm.github.io/school-calendar/

No login, no app to install, and no data is sent anywhere. It works on phones and laptops.

There are two pages:

| Page | Link | For |
|---|---|---|
| `index.html` | https://aanchi3005-lgtm.github.io/school-calendar/ | Our school. The 2025–26 dates are already built in. |
| `make.html` | https://aanchi3005-lgtm.github.io/school-calendar/make.html | Any school. Parents add their own calendar screenshots. |

## Any school: make.html

1. Add screenshots or photos of every page of the school's yearly calendar. If you have the calendar as text or a PDF, use **Paste it instead**, which is more accurate.
2. Tap **Read dates from pictures**. The page reads the text on your own device; pictures are never uploaded. The first time, it downloads a text reader (about 5 MB).
3. **Check the list of dates** and fix anything wrong. Reading pictures is not perfect.
4. Pick the class and print, as below.

**Tips for good results**
- Flat screenshots (of a PDF, website or WhatsApp image) read far better than photos of a printed booklet.
- For photos: lay the page flat, fill the frame, use good light, and avoid shadows and curved pages.
- If a picture comes out sideways, use the ↺ ↻ buttons on it before reading.
- Once the list is correct, tap **Save dates file** and share that file with other parents. They tap **Load dates file** and skip the reading step.

---

## For parents: how to use it

1. Open the link.
2. Tap your child's class: **Nursery, KG, P1, P2, P3, P4 or P5**.
3. Optional: type your child's name (printed at the top) and pick their **house** to see the weeks it is on duty.
4. Choose a layout:
   - **Whole year on one page**, good for the fridge
   - **One month per page**, 12 pages with room for notes
   - **Both**, 13 pages
5. Tap **Print calendar**.

### Print settings

- Paper: **A4**
- Layout: **Landscape**
- Tick **Background graphics** (sometimes under "More settings"), or the colours won't print
- To keep a copy instead of printing, choose **Save as PDF** as the printer

**On a phone:** if the link opened inside Instagram or WhatsApp, use the **⋯** menu and pick **Open in browser** first. Then use Print, or Share → Print.

### What the colours mean

| Colour | Meaning |
|---|---|
| Red | Holiday |
| Orange | Vacation / break |
| Purple | Exam / test |
| Yellow | Parent-teacher meeting (PTM) |
| Green | School event |
| Blue | Your house on duty (only when a house is picked) |

Sundays have red date numbers. "Mid" means the planner gives only the middle of the month, with no exact date.

By default the calendar shows only events for the chosen class, plus holidays for the whole school. Untick **Only show events for this class** to see everything.

---

## About the dates

- **Source:** the school's *Proposed School Planner 2025–26* (pages 20–23), session **April 2025 – March 2026**.
- The planner says dates may be rescheduled or cancelled, so always follow the school's latest circulars.
- "Nursery to P2" in the planner is shown as Nursery, KG, P1 and P2.
- The site keeps nothing about you except your last choices (class, name, house), which are saved only in your own browser.

---

## For the maintainer: updating the site

Everything is in one file, `index.html`. The `.nojekyll` file tells GitHub Pages to serve the files as they are, so leave it in place.

### Change or add dates

Open `index.html` and find the block marked `School data (from the printed planner)`. Each date is one line:

```js
['2025-08-15', '', 'Independence Day', 'holiday'],
['2025-05-05', '2025-05-09', 'Periodic Test 1', 'exam', 'P3-P5'],
['2025-04-01', '2025-04-26', 'Mother Teresa House on duty', 'house', '', 'Mother Teresa'],
['2025-09-15', '', 'Hindi Elocution (mid-Sept, date TBA)', 'event', 'P1,P2', null, true],
```

| Position | Meaning | Example |
|---|---|---|
| 1 | Start date (YYYY-MM-DD) | `'2025-05-05'` |
| 2 | End date for ranges, or `''` for a single day | `'2025-05-09'` |
| 3 | Title | `'Periodic Test 1'` |
| 4 | Type: `holiday`, `vacation`, `exam`, `ptm`, `event` or `house` | `'exam'` |
| 5 | Classes: leave empty for everyone, or list them (`'P4,P5'`) or give a range (`'Nursery-P2'`) | `'P3-P5'` |
| 6 | House name (for `house` lines only) | `'Mother Teresa'` |
| 7 | `true` if the date is approximate ("mid-month") | `true` |

Keep the lines in date order, and give each line a trailing comma.

### Start a new school year

In the same block, update:

- `planner:` the planner's name, e.g. `'Proposed School Planner 2026–27'`
- `y:` the year the session starts, e.g. `2026`
- `name:` the school name to print on the calendar header (optional)
- the list of dates

### Publish the change

On GitHub, open `index.html` → click the **pencil icon** → paste in the new version → **Commit changes**. The site updates within a minute or two, and the link stays the same.

---

## Hosting

This is a static site on **GitHub Pages** (Settings → Pages → Branch: `main`, folder `/ (root)`). It loads fonts from Google Fonts and falls back to system fonts when offline, so the `index.html` file also works when opened straight from a computer.
