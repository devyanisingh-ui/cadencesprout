# CadenceSprout — Stitch Prompts

Google Stitch UI generation prompts for all CadenceSprout screens. Each prompt is fully self-contained — Stitch needs no other document to generate the screen.

---

## Master Screen Table

| Screen ID | Screen Name | Platform | Section | Status |
|-----------|------------|---------|---------|--------|
| T-0 | Teacher Login | Mobile (iOS-first) | 4.1 Teacher App | ✅ Ready |
| T-1 | Home Feed (Class Feed) | Mobile (iOS-first) | 4.1 Teacher App | ✅ Ready |
| T-2 | Post Composer | Mobile (iOS-first) | 4.1 Teacher App | ✅ Ready |
| T-2A | Manual Child Tag Picker | Mobile (iOS-first) | 4.1 Teacher App | ✅ Drafted |
| T-3 | Post Detail | Mobile (iOS-first) | 4.1 Teacher App | ✅ Ready |
| T-4 | Attendance | Mobile (iOS-first) | 4.1 Teacher App | ✅ Ready |
| T-5 | Class Roster | Mobile (iOS-first) | 4.1 Teacher App | ✅ Ready |
| T-5A | Child Detail | Mobile (iOS-first) | 4.1 Teacher App | ✅ Drafted |
| T-6 | Milestone Tracker (per child) | Mobile (iOS-first) | 4.1 Teacher App | ✅ Ready |
| T-6A | Milestone Picker | Mobile (iOS-first) | 4.1 Teacher App | ✅ Drafted |
| T-7 | Profile / Settings | Mobile (iOS-first) | 4.1 Teacher App | ✅ Ready |
| P-0 | Parent App Phone Number Entry / OTP Request | Mobile (iOS-first) | 4.2 Parent App | ✅ Drafted |
| P-0A | Parent App OTP Verification | Mobile (iOS-first) | 4.2 Parent App | ✅ Drafted |
| P-1 | Magic-Link Web View (Feed First) | Mobile (iOS-first) | 4.2 Parent App | ✅ Drafted |
| P-2 | DPDP Consent Screen | Mobile (iOS-first) | 4.2 Parent App | ❌ Pending |
| P-3 | Parent Home Feed | Mobile (iOS-first) | 4.2 Parent App | ❌ Pending |
| P-4 | Post Detail | Mobile (iOS-first) | 4.2 Parent App | ❌ Pending |
| P-5 | Milestone Progress | Mobile (iOS-first) | 4.2 Parent App | ❌ Pending |
| P-6 | Year-End Portfolio | Mobile (iOS-first) | 4.2 Parent App | ❌ Pending |
| P-7 | Notifications | Mobile (iOS-first) | 4.2 Parent App | ❌ Pending |
| P-8 | Profile / Data & Privacy | Mobile (iOS-first) | 4.2 Parent App | ❌ Pending |
| A-1 | Dashboard Home | Web | 4.3 Admin Web | ❌ Pending |
| A-2 | Parent Feed (Read-Only) | Web | 4.3 Admin Web | ❌ Pending |
| A-3 | Admissions Pipeline | Web | 4.3 Admin Web | ❌ Pending |
| A-4 | Fee Management | Web | 4.3 Admin Web | ❌ Pending |
| A-5 | Attendance Dashboard | Web | 4.3 Admin Web | ❌ Pending |
| A-6 | Staff Management | Web | 4.3 Admin Web | ❌ Pending |
| A-7 | School Settings | Web | 4.3 Admin Web | ❌ Pending |
| A-8 | Reports | Web | 4.3 Admin Web | ❌ Pending |
| A-9 | Login | Web | 4.3 Admin Web | ❌ Pending |
| TW-1 | Teacher Web Login | Web | 4.4 Teacher Web | ❌ Pending |
| TW-2 | Teacher Web Home Feed | Web | 4.4 Teacher Web | ❌ Pending |
| TW-3 | Teacher Web Post Composer | Web | 4.4 Teacher Web | ❌ Pending |
| TW-4 | Teacher Web Attendance | Web | 4.4 Teacher Web | ❌ Pending |
| TW-5 | Teacher Web Class Roster | Web | 4.4 Teacher Web | ❌ Pending |
| TW-6 | Teacher Web Milestone Tracker (per child) | Web | 4.4 Teacher Web | ❌ Pending |
| TW-7 | Teacher Web Profile / Settings | Web | 4.4 Teacher Web | ✅ Drafted |
| PW-1 | Parent Web Magic-Link Feed | Web | 4.5 Parent Web | ❌ Pending |
| PW-2 | Parent Web Full Feed (After OTP Login) | Web | 4.5 Parent Web | ❌ Pending |
| PW-3 | Parent Web Post Detail | Web | 4.5 Parent Web | ❌ Pending |
| PW-4 | Parent Web Milestone Progress | Web | 4.5 Parent Web | ❌ Pending |
| PW-5 | Parent Web Profile / Settings | Web | 4.5 Parent Web | ✅ Drafted |
| PW-6 | Parent Web Privacy Settings (DPDP Consent Management) | Web | 4.5 Parent Web | ✅ Drafted |

---

## Design System Reference (applies to all screens)

**Brand:** CadenceSprout — a warm, editorial app for Indian preschool teachers. Think Seesaw meets a boutique Indian school newsletter. Never generic, never cold.

**Palette (light mode):**
- Background: `#FAF7F2` (warm cream)
- Surface / card: `#FFFFFF`
- Primary action: `#5C8B6E` (sage green)
- Accent: `#C4784A` (terracotta)
- Text primary: `#1A1A1A`
- Text secondary: `#6B6B6B`
- Divider: `#E8E2D9`
- Success: `#4A8C5C`
- Error: `#C0392B`

**Palette (dark mode):**
- Background: `#1A1A1A`
- Surface / card: `#242424`
- Primary action: `#7AAF8C` (lighter sage)
- Accent: `#D4875A` (lighter terracotta)
- Text primary: `#F5F2EC`
- Text secondary: `#9A9A9A`
- Divider: `#333333`

**Typography:**
- Headlines / post captions: Fraunces (serif, italic feel) — warmth and personality
- UI labels, body, buttons: Inter (sans-serif) — clean and readable
- Font sizes: body 14sp, label 12sp, heading 18sp, caption 16sp

**Components:**
- Buttons: 48dp tall, 8dp radius, full-width primary in sage green
- Cards: 12dp radius, 2dp shadow (elevation 2), white surface on cream background
- Bottom tab nav: 4 tabs, active tab in sage green, inactive in `#9A9A9A`
- FAB: 56dp circle, sage green, bottom-right, 16dp from screen edge
- Input fields: 48dp tall, outlined style, 8dp radius, sage green focus border
- Child chips: 28dp tall, 8dp radius pill — solid sage green when confirmed, dashed border when AI-suggested/unconfirmed
- Skeleton loaders: warm cream (#EDE8DF) pulsing rectangles

**School placeholder:** "Sunshine Preschool" with a sun+leaf icon (circular, warm yellow + green)

**Persona names:** Sunita (teacher), Meera (parent), Rohan / Aarav / Priya (children), Rajesh (admin/principal)

**Platform:** React Native, iOS-first (iPhone 14 Pro viewport: 393×852pt). Safe area insets respected. Bottom tab nav sits above home indicator.

---

## Hardcoded Navigation Rules

Every prompt must explicitly include its navigation/menu. Do not invent, rename, hide, or swap menu items between screens.

- Teacher mobile primary menu: `Feed | Attendance | Roster | Profile`
- Teacher mobile detail screens: keep teacher menu context and use back navigation; do not create extra tabs
- Teacher mobile modals/bottom sheets: no separate menu; inherit invoking screen context
- Parent mobile authenticated menu: `Feed | Milestones | Portfolio | Profile`
- Parent mobile pre-auth screens: no persistent menu
- Teacher web sidebar: `Feed | Attendance | Roster | Milestones | Profile`
- Parent web authenticated navigation:
  - Mobile bottom nav: `Feed | Milestones | Portfolio | Profile`
  - Desktop header nav: `Feed | Milestones | Portfolio | Profile`
- Settings and privacy screens must keep `Profile` as the active menu context

---

## Section 4.1 — Teacher App (Mobile)

---

### Screen T-0: Teacher Login

**Prompt for Google Stitch:**

Design a mobile login screen for CadenceSprout, a warm and editorial preschool app used by Indian teachers.

**Navigation / Menu (hardcoded):**
- No persistent menu on this pre-auth screen
- Do not show the teacher bottom tab bar here

**Layout:**
- iPhone 14 Pro viewport (393×852pt), portrait orientation
- Background: `#FAF7F2` (warm cream), full bleed
- Vertically centered content block, roughly 60% of screen height, horizontally padded 24dp on each side
- Top area: school logo placeholder — circular icon (sun + leaf motif, warm yellow #F5C842 + sage green #5C8B6E), 72×72dp, centered, followed by "Sunshine Preschool" in Inter Semibold 14sp, `#6B6B6B`, 8dp below the icon
- Below school name: "CadenceSprout" wordmark in Fraunces Regular 24sp, `#1A1A1A`, centered, 24dp below
- 40dp vertical gap before the form

**UI Elements:**
- Phone number field: full width, 48dp tall, outlined (1dp border `#E8E2D9`, 8dp radius), left side shows "+91" prefix in Inter Regular 14sp `#6B6B6B` with a vertical divider, numeric keypad triggers on focus, placeholder "Phone number" in `#9A9A9A`
- 16dp gap
- Password field: full width, 48dp tall, same outlined style, placeholder "Password" in `#9A9A9A`, right side shows eye icon (24dp, `#9A9A9A`) to toggle mask/unmask
- 12dp gap
- "Forgot password?" right-aligned text link, Inter Regular 13sp, `#5C8B6E` (sage green)
- 24dp gap
- [Log In] primary button: full width, 48dp tall, 8dp radius, fill `#5C8B6E`, label "Log In" in Inter Semibold 16sp white
- Footer at bottom of screen: "Powered by CadenceSprout" centered, Inter Regular 11sp `#9A9A9A`

**Colors & Typography:**
- Background `#FAF7F2`, form fields white surface, primary sage `#5C8B6E`
- Font: Inter throughout; wordmark in Fraunces

**States (include all as artboard variants or annotated states):**

*Default:* Empty phone and password fields, Log In button enabled but visually muted (full opacity sage green)

*Typing:* Active field gets 2dp sage green border `#5C8B6E`, keyboard slides up, content block shifts up to stay visible above keyboard

*Loading:* Log In button shows a small white spinner (20dp) replacing the label; inputs are disabled (opacity 0.5); no other change

*Error (invalid credentials):* Below the password field, inline error text in `#C0392B` Inter Regular 13sp: "Incorrect phone number or password." — fields retain their current values, border turns red `#C0392B`

*Success:* Brief green checkmark flash on the button (200ms), then transition away to Home Feed

*Dark mode:* Background `#1A1A1A`, card/fields on `#242424` surface, text `#F5F2EC`, sage green lightens to `#7AAF8C`, borders `#333333`, secondary text `#9A9A9A`

**Interactions & Animations:**
- Keyboard appears: content block translates up smoothly (spring animation, 300ms)
- Log In tap: button scale-down 0.97 on press (haptic feedback), spinner appears
- Error shake: form block does a brief horizontal shake (2 cycles, 150ms total) on invalid credentials
- Transition to Home Feed: fade + slide-up (300ms)

---

### Screen T-1: Home Feed (Class Feed)

**Prompt for Google Stitch:**

Design the Home Feed screen of CadenceSprout, the primary daily landing screen for Sunita (a preschool teacher at Sunshine Preschool). This is a mobile screen, React Native, iOS-first (iPhone 14 Pro, 393×852pt).

**Navigation / Menu (hardcoded):**
- Render the bottom tab bar exactly as: `Feed | Attendance | Roster | Profile`
- Feed is active

**Layout:**
- Background: `#FAF7F2` (warm cream), full bleed
- Top: native status bar (dark icons on cream) + custom header (56dp tall): left side — circular school logo (sun+leaf, 32dp), right of logo — "Sunshine Preschool" Inter Semibold 14sp `#1A1A1A` stacked above "LKG A" Inter Regular 12sp `#6B6B6B`; right side of header — notification bell icon 24dp `#6B6B6B`
- Bottom: tab bar (56dp, white surface, top border 1dp `#E8E2D9`): 4 tabs left to right — Feed (active, sage green icon + label), Attendance (inactive grey), Roster (inactive grey), Profile (inactive grey). Each tab: 24dp icon + 11sp label below, tappable area full-width tab zone
- Body: scrollable feed area between header and tab bar, 16dp horizontal padding

**UI Elements (Post Card):**
Show 2 full post cards and a partial third card (to signal scrollability):

Post card structure (12dp radius, white surface, 2dp shadow):
- Full-bleed photo (4:3 ratio, 345dp wide, ~259dp tall, top 12dp radius, bottom flush) — placeholder: warm classroom scene or colorful finger painting
- Card body below photo, 12dp padding:
  - Caption in Fraunces Italic 16sp `#1A1A1A`: e.g. "Rohan showed incredible focus during block building today — spatial reasoning is blooming! 🌱"
  - 8dp gap
  - Child chips row: solid sage green pill chips (28dp tall, 8dp radius, `#5C8B6E` fill, white text Inter Regular 12sp) — e.g. "Rohan" "Aarav" "Priya"
  - 8dp gap
  - Bottom meta row: left — "2 hours ago" Inter Regular 12sp `#9A9A9A`; right — eye icon + "14 / 18 parents viewed" Inter Regular 12sp `#9A9A9A`

FAB: 56dp circle, `#5C8B6E` sage green, white `+` icon (24dp), fixed bottom-right, 16dp from right edge, 16dp above tab bar top

**Colors & Typography:**
- Cream background, white cards, sage green primary, Fraunces for captions, Inter for metadata

**States (as variants):**

*Loading (skeleton):* Replace post cards with skeleton cards — same card dimensions, photo area is a warm cream `#EDE8DF` pulsing rectangle (shimmer animation left-to-right), caption area is 3 lines of rounded rectangles in `#EDE8DF`, chip area is 2 oval placeholders

*Empty — no students yet:* Remove post cards. Center in body: a warm illustration placeholder (e.g. an empty classroom with chairs and sunlight, soft watercolor style), below it: "Add your students to get started" Inter Semibold 16sp `#1A1A1A`, below that a secondary button (outlined sage green): "Add Students"

*No posts today:* Show past posts normally, but at the top of the feed below the header, show a date-grouped section header: "Today · No posts yet" in Inter Regular 13sp `#9A9A9A`, with a subtle dotted separator line. Past posts appear below with their own date headers.

*Offline banner:* Persistent horizontal banner (40dp tall, `#C4784A` terracotta fill) pinned below the custom header: left — wifi-off icon 16dp white, "You're offline — showing saved content" Inter Regular 13sp white

*Dark mode:* Background `#1A1A1A`, cards `#242424`, caption text `#F5F2EC`, meta text `#9A9A9A`, tab bar `#242424`, header `#1A1A1A`, FAB `#7AAF8C`

**Interactions & Animations:**
- Pull-to-refresh: standard iOS spinner in sage green, refreshes feed
- FAB tap: spring scale-up animation (0.95→1.05→1.0, 200ms), opens Post Composer as modal slide-up
- Post card tap: navigates to Post Detail (T-3) with a hero image expand transition
- Tab switch: immediate, no animation, icon + label color transitions to/from sage
- Skeleton to content: fade-in per card as data loads (stagger 80ms per card)

---

### Screen T-2: Post Composer

**Prompt for Google Stitch:**

Design the Post Composer screen for CadenceSprout's teacher app. This is a modal that slides up over the Home Feed when Sunita taps the FAB. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- No separate menu inside this modal
- Inherit teacher app navigation context from Home Feed: `Feed | Attendance | Roster | Profile`

**Layout:**
- Background: `#FAF7F2` (warm cream), fills the full modal
- Modal handle: 4dp×32dp rounded pill in `#E8E2D9`, centered, 12dp from top
- Header row (56dp, no border): left — "✕ Discard" Inter Regular 15sp `#C0392B`; center — "New Post" Inter Semibold 16sp `#1A1A1A`; right — [POST] button 36dp tall 8dp radius `#5C8B6E` fill white text Inter Semibold 15sp
- Body: vertically scrollable, 16dp horizontal padding

Content order top to bottom:
1. **Photo preview area** — 345dp wide, 259dp tall (4:3), 12dp radius, shows selected photo center-cropped. Below the photo: small row of thumbnail chips if multiple photos (28dp tall each), with a "+" add more chip at the end
2. **Caption field** (16dp top gap) — multiline, min 3 lines, no visible border, placeholder in Fraunces Italic 16sp `#9A9A9A`: "What happened in this moment?" When AI caption is present: Fraunces Italic 16sp `#1A1A1A` text appears. Top-right corner of caption area: a small ✨ badge (16dp, `#5C8B6E`) indicating AI-drafted
3. **Children row** (16dp top gap) — label "In this post:" Inter Semibold 13sp `#6B6B6B` above chip row. Chips: solid sage for confirmed, dashed border sage for AI-suggested (same pill style, dashed 1.5dp border `#5C8B6E`, sage text, transparent fill). Tap chip to confirm/remove. "Add manually +" text link at end of chip row, Inter Regular 13sp `#5C8B6E`
4. **Milestones row** (12dp top gap) — "Add milestones (optional) ›" full-width tappable row, Inter Regular 14sp `#6B6B6B`, right chevron icon; 1dp top/bottom dividers in `#E8E2D9`
5. **Class row** (0dp gap, below milestones divider) — "Class: LKG A ›" same row style — tappable to change class if teacher has multiple

**Colors & Typography:**
- Same warm palette; caption uses Fraunces for that editorial feel; all other text Inter

**States (as variants):**

*AI caption loading:* Caption area shows a shimmer animation — two lines of `#EDE8DF` rounded rectangles pulsing, with "Drafting caption..." in Inter Regular 13sp `#9A9A9A` above them

*AI caption ready:* Caption text populates with a gentle fade-in; ✨ badge visible; cursor placed at end for editing

*AI caption failed:* Caption area shows empty placeholder only, ✨ badge absent; a subtle toast at bottom: "AI caption unavailable — write your own" Inter Regular 13sp white on `#333333`, 4dp radius, auto-dismiss 3s

*Face recognition pending:* Child chips all grey dashed with "..." label, small spinner (12dp) inside each chip

*Face recognition complete:* Some chips turn solid sage (confirmed), some remain dashed (low confidence); "Couldn't identify 2 children — add manually" text if any remain uncertain

*Upload in progress (POST tapped):* [POST] button becomes a horizontal progress bar (same 36dp height, fills left to right in sage green, remaining fill in `#E8E2D9`); optimistic post card appears on the feed behind the (partially transparent) modal

*Upload failed:* Toast at bottom of screen (persistent, not auto-dismiss): "Upload failed — tap to retry" Inter Semibold 14sp, `#FAF7F2` text on `#C4784A` terracotta background, full width with a "Retry" button right-aligned

*Dark mode:* Background `#1A1A1A`, caption area `#242424`, chip fills and borders adjusted, shimmer in `#333333`

**Interactions & Animations:**
- Modal slides up from bottom (spring, 350ms); background dims to 40% black overlay
- Photo tap: opens native image picker
- Caption field: cursor auto-placed after AI text; typing replaces AI draft (✨ badge remains as attribution)
- POST tap: haptic feedback (medium impact), progress bar animates, modal closes on success with a "Posted!" confetti burst (3 colored dots: sage, terracotta, cream, 500ms)
- Discard tap: confirmation bottom sheet "Discard this post?" with [Discard] (red) and [Keep editing] (sage)

---

### Screen T-3: Post Detail

**Prompt for Google Stitch:**

Design the Post Detail screen for CadenceSprout's teacher app. Sunita taps a post card from the Home Feed to see full details and parent engagement. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- Keep teacher app navigation context as `Feed | Attendance | Roster | Profile`
- Use back navigation in the header; do not add a second tab bar

**Layout:**
- Background: `#FAF7F2` (warm cream)
- Header (56dp): back chevron `←` left 24dp `#1A1A1A`, center "Post" Inter Semibold 16sp, right: share icon 24dp `#6B6B6B`
- Body: scrollable, no horizontal padding on the photo

Content top to bottom:
1. **Full-bleed photo** — 393dp wide, ~295dp tall (4:3), flush to screen edges, no radius. If multiple photos: horizontal swipe carousel with page dots (5dp circles, active sage green, inactive `#E8E2D9`) pinned bottom-right of image
2. **Post meta block** (16dp padding, 16dp top gap): "2 hours ago · LKG A" Inter Regular 12sp `#9A9A9A`
3. **Caption** (8dp top gap): Fraunces Italic 18sp `#1A1A1A`, e.g. "Rohan showed incredible focus during block building today — spatial reasoning is blooming! 🌱" Full text, no truncation
4. **Children chips** (12dp top gap): label "Children tagged:" Inter Semibold 12sp `#6B6B6B`, then chip row: solid sage chips per child
5. **Milestones block** (12dp top gap, only if milestones exist): label "Milestones observed:" Inter Semibold 12sp `#6B6B6B`, then list of milestone tags — small pill with `#EDE8DF` fill, `#6B6B6B` text, e.g. "Spatial reasoning" "Motor skills"
6. **Engagement block** (12dp top gap, 1dp top divider `#E8E2D9`): eye icon `#5C8B6E` + "Seen by 14 of 18 parents" Inter Semibold 14sp `#1A1A1A`; below: horizontal progress bar (345dp, 8dp tall, 4dp radius, sage green fill proportional to 14/18)
7. **Comments section** (16dp top gap, 1dp top divider): "Comments (3)" Inter Semibold 14sp `#1A1A1A`; each comment: circular avatar (32dp) + name Inter Semibold 13sp + comment text Inter Regular 13sp + timestamp 11sp `#9A9A9A`; parent name in terracotta `#C4784A` to distinguish from teacher

**Colors & Typography:** Cream background, white content blocks, Fraunces for caption, Inter elsewhere, sage engagement accent

**States:**

*Loading:* Skeleton version — photo area is a pulsing cream rectangle, caption area is 3 lines skeleton, engagement block skeleton

*No comments:* Comments section shows "No comments yet." Inter Regular 13sp `#9A9A9A`, centered

*Dark mode:* Background `#1A1A1A`, content `#242424`, text `#F5F2EC`, page dots adjusted, engagement bar lighter sage

**Interactions & Animations:**
- Hero image expand transition from feed card (shared element animation, 300ms)
- Photo swipe: horizontal scroll snap between images, page dots update
- Pull down from top: dismiss back to feed (iOS-style interactive dismiss)
- Parent avatar tap: no navigation (read-only in teacher view)

---

### Screen T-4: Attendance

**Prompt for Google Stitch:**

Design the Attendance screen for CadenceSprout's teacher app. Sunita marks daily attendance from the bottom nav. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- Render the bottom tab bar exactly as: `Feed | Attendance | Roster | Profile`
- Attendance is active

**Layout:**
- Background: `#FAF7F2` (warm cream)
- Header (56dp): center — "Attendance" Inter Semibold 16sp; left — `←` back chevron (only shown when viewing a past date); right — calendar icon 24dp `#6B6B6B`
- Below header: date row (40dp, 16dp horizontal padding): left `‹` arrow, center "Thursday, 26 March 2026" Inter Semibold 14sp `#1A1A1A`, right `›` arrow (disabled for today — greyed out); back-navigation allows corrections up to 7 days
- Below date: class + stats row: "LKG A · 22 children" Inter Regular 13sp `#6B6B6B`, right side: "Present: 18 · Absent: 2" Inter Regular 13sp `#5C8B6E` (updates live as teacher marks)
- Body: flat scrollable list, 16dp horizontal padding, 8dp between rows
- Bottom: [Submit Attendance] full-width button (48dp, 8dp radius, `#5C8B6E` fill white text Inter Semibold 16sp), floating above tab bar with 16dp padding on all sides; white background behind it with 1dp top border `#E8E2D9`
- Bottom tab bar (same as T-1, Attendance tab active in sage)

**UI Elements (Attendance Row):**
Each row (68dp tall, white card, 8dp radius, 12dp horizontal padding, 4dp vertical padding):
- Left: circular child photo (44dp, placeholder warm placeholder avatar with child initial, sage green background)
- Right of photo: child name Inter Semibold 15sp `#1A1A1A` + below it: age "4 yrs" Inter Regular 12sp `#9A9A9A`
- Far right: Present/Absent toggle — custom 2-state pill toggle (72dp × 32dp, 16dp radius): present state fills sage green `#5C8B6E` with "P" Inter Semibold 12sp white; absent state fills `#E8E2D9` with "A" Inter Regular 12sp `#9A9A9A`
- If absent: a small "reason ›" tappable text appears below the toggle in Inter Regular 12sp `#C4784A` terracotta

Show approximately 6–7 rows visible before scroll.

**Colors & Typography:** Cream background, white rows, sage presence toggle, terracotta absence accent

**States:**

*Not yet taken (initial load):* All toggles in unset/neutral state — grey pill with no "P" or "A" active, placeholder appearance; date header shows today; Submit button is disabled (opacity 0.5) until all children are marked

*In progress:* Some rows marked P (sage), some A (grey+A), some still unset; counter in stats row updates: "Present: 12 · Absent: 3 · Unmarked: 7"; Submit button remains disabled while any unmarked remain

*All marked, not submitted:* Submit button becomes fully enabled (full opacity sage); "All 22 marked ✓" appears in the stats row in sage green

*Submitted:* All toggles become read-only (opacity 0.7, no tap response); button changes to "✓ Attendance Submitted" with a green checkmark, disabled state; a toast at top: "Attendance saved for today" auto-dismisses 3s; top-right edit icon appears for corrections until midnight

*Past date (viewing corrections):* Date row shows the past date, right `›` arrow is enabled up to today; "Submitted" badge in sage green shown next to the date; rows are editable; Submit button shows "Update Attendance"

*Dark mode:* Background `#1A1A1A`, rows `#242424`, toggle present `#7AAF8C`, absent `#333333`, text `#F5F2EC`

**Interactions & Animations:**
- Toggle tap: spring animation (toggle thumb slides 200ms), haptic feedback (light)
- Absence reason: bottom sheet slides up with preset reasons (Sick / Family function / Unspecified) + free text field
- Submit tap: medium haptic, button spins briefly, then success state
- Date navigation arrows: slide in new roster from left/right (200ms)

---

### Screen T-5: Class Roster

**Prompt for Google Stitch:**

Design the Class Roster screen for CadenceSprout's teacher app. Sunita views all children in her class and their parent contact status. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- Render the bottom tab bar exactly as: `Feed | Attendance | Roster | Profile`
- Roster is active

**Layout:**
- Background: `#FAF7F2` (warm cream)
- Header (56dp): center "Class Roster" Inter Semibold 16sp; right — search icon 24dp `#6B6B6B`
- Search bar (appears when search icon tapped, 48dp tall, 16dp padding): outlined field, 8dp radius, placeholder "Search children…" Inter Regular 14sp `#9A9A9A`, sage green focus border
- Class summary strip (40dp, 16dp horizontal padding): "LKG A · 22 children" Inter Regular 13sp `#6B6B6B`, right side: "18 parents active" Inter Regular 13sp `#5C8B6E`
- Body: flat scrollable list, 16dp horizontal padding, 8dp between rows
- Bottom tab bar (Roster tab active in sage)

**UI Elements (Roster Row):**
Each row (72dp tall, white card, 8dp radius, 12dp padding):
- Left: circular child photo avatar (48dp, warm placeholder with initial, different pastel background per child — rotate through: `#E8F4EC` sage-tint, `#FEF3E7` terracotta-tint, `#F0EBE3` cream-tint)
- Center block: child name Inter Semibold 15sp `#1A1A1A`; below — "4 yrs · Adm #2341" Inter Regular 12sp `#9A9A9A`; below — parent name "Parent: Meera" Inter Regular 12sp `#6B6B6B`

---

## Screen P-2: DPDP Consent Screen (Stitch Prompt)

Design brief (self-contained Stitch prompt):

Design a mobile DPDP Consent Screen for CadenceSprout (Parent app, first-run modal). This screen collects per-type data consent for a child before showing the feed. Produce: a PNG wireframe (mobile), a self-contained single-file HTML sketch (no external deps), and a content/copy JSON for engineers.

Constraints and platform:
- iPhone 14 Pro viewport (393×852pt), portrait. React Native implementation.
- Brand: warm editorial (see Design System Reference). Use Fraunces for headings and Inter for UI copy.
- Accessibility: all tappable controls >=44×44pt, color contrast >=4.5:1 for text, provide accessible labels for screen readers.

Goal & user:
- Goal: get clear, informed, per-type consent from the parent for storing and processing their child's data (including AI face recognition) so the app can show personalized posts.
- User: Meera, a working parent who may be privacy-cautious and wants a short, trustworthy explanation.

Deliverables (produce all):
1. PNG wireframe: single screen + two variants (consent all pre-checked, one consent unchecked). Export to `/tmp/p2-consent-wf.png`.
2. Single-file HTML sketch placed at `/tmp/p2-consent-sketch.html` demonstrating layout, fonts (system fallback), and accessible form controls. Include inline comments explaining ARIA labels and focus order.
3. JSON copy bundle (compact) containing: `title`, `description`, `consent_items` (array of {id, short_label, long_description, default_checked, revoke_note}), `primary_cta`, `secondary_action`, `legal_link_text`.
4. Small style guide excerpt (colors, sizes for this screen) as YAML block at end of HTML.

Screen structure (strict):
- Modal header: school logo left, center title: "Your child's privacy" (Fraunces 18sp), close `X` top-right (accessible label "Close consent modal").
- Intro copy: one-line supportive sentence: "Your child's privacy is our first commitment." (Inter 14sp, `#1A1A1A`) then 2–3 sentence explanation (Inter 13sp `#6B6B6B`), max 3 lines.
- Consent items list (vertical stack, 16dp gaps): each item is a full-width row with:
  - Checkbox (48dp tappable area) left
  - Short label (Inter Semibold 14sp)
  - Long description (Inter Regular 13sp, muted color) under the label
  - Small `i` info icon that expands inline to show one-line examples when tapped (animated expand/collapse)
- Consent items to include (exact copy keys, include these descriptions in JSON):
  1. `share_updates`: "Share daily updates with you only" — explains parents will receive photos/videos in this private feed.
  2. `face_recognition`: "Recognise [child name] in class photos (AI — server-side)" — explains face recognition is used to suggest tags; includes opt-out effect: "If you opt out, your child will not be auto-tagged; teachers can tag manually." Provide `revoke_note` explaining deletion timeline (24 hours).
  3. `store_in_india`: "Store data in India (deleted when you leave)" — clarifies data residency and deletion policy.
- Consent UX rules:
  - All items default to checked but editable.
  - Each checkbox toggles immediately and is persisted optimistically; show inline saving spinner if network latency > 500ms.
  - If `face_recognition` is unchecked AND it was previously enabled, show a subtle confirm banner: "Turning this off will remove existing face data within 24 hours. Continue?" with Confirm / Cancel.
  - Provide an inline link to full privacy policy modal: "See full privacy policy" (opens accessible modal overlay).
- CTA row pinned to bottom above safe-area: Primary CTA (full-width) `I agree` (sage green, `#5C8B6E`). Secondary text button under it: `Ask my school later` (neutral link style). Also include a tertiary tiny link: "Manage data later in Profile > Data & Privacy".

States and variants to produce:
- Default (all pre-checked) — show enabled primary CTA.
- One unchecked (face_recognition unchecked) — show confirm banner variant when toggled off.
- Offline state — toggles disable (opacity 0.5), primary CTA shows offline tooltip: "You're offline — consent will be saved when you're online." Include retry affordance.
- Error state — if save fails, show inline error under the affected consent item and toast: "We couldn't save your choice. Try again."

Accessibility & copy guidance:
- Provide clear accessible labels (e.g., checkbox `aria-labelledby` references the short label). Provide `aria-describedby` for long descriptions.
- Ensure focus order: close `X` → first checkbox → subsequent checkboxes → primary CTA → secondary link.
- Provide a short, friendly confirmation toast after `I agree`: "Thanks! You're all set — returning to the feed." and move focus to the feed content.

Acceptance criteria for Stitch output:
- PNG wireframe and HTML sketch render similar layouts (visual parity). HTML includes comments with ARIA and focus order. JSON copy contains the specified fields.
- All tappable controls annotated with min touch size and accessible labels.
- Provide a one-paragraph rationale at top of the HTML explaining the UX choices (2–3 sentences).

Developer notes (include in HTML comments):
- Persist consent via `POST /api/v1/parents/{parent_id}/consent` with payload `{items: {share_updates: true, face_recognition: false, store_in_india: true}}` — show optimistic UI and rollback on error.
- If toggling `face_recognition` from true→false, queue deletion job `DeleteChildFaceDataJob` and display the 24-hour deletion message.

End of prompt. Use explicit copy from the JSON bundle when generating UI text. Keep everything concise and parent-friendly.

- Right: parent status badge (pill, 24dp tall, 8dp horizontal padding, Inter Regular 11sp):
  - Active: `#E8F4EC` fill, `#4A8C5C` text "Active"
  - Invited: `#FEF3E7` fill, `#C4784A` text "Invited"
  - Not invited: `#F0EBE3` fill, `#9A9A9A` text "Not invited"
- Right edge: chevron `›` 16dp `#9A9A9A`

Show approximately 7–8 rows before scroll. First row: Aarav (Active), Second: Priya (Active), Third: Rohan (Invited), Fourth: child with "Not invited" for contrast.

**Colors & Typography:** Warm tinted avatars, status badges with semantic colours, Inter throughout

**States:**

*Default list:* Rows as above, search bar hidden

*Search active:* Search bar visible below header, keyboard up, list filters in real-time to matching children; no match: "No children match 'xyz'" centered in body Inter Regular 14sp `#9A9A9A`

*Child detail (tap on row):* Navigate to a detail sheet (show as bottom sheet or full screen — design as full screen): child name as header, 80dp circular avatar, DOB + age, parent name(s) with phone number (masked: 98765 ••••0), parent status badge, "Recent posts (3) ›" tappable row, "Milestones ›" tappable row, "Attendance this month: 18/22 days" row

*Dark mode:* Background `#1A1A1A`, rows `#242424`, avatars use darker tint versions, status badges darken fills, text `#F5F2EC`

**Interactions & Animations:**
- Search icon tap: search bar slides down (200ms) and keyboard appears
- Row tap: push navigation with slide-left transition (standard iOS)
- Search clear: rows animate back to full list (subtle fade)

---

### Screen T-6: Milestone Tracker (per child)

**Prompt for Google Stitch:**

Design the Milestone Tracker screen for CadenceSprout's teacher app. Sunita views and records developmental milestones for a specific child (Rohan, age 4). This is accessed from the Class Roster by tapping a child. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- Keep teacher app navigation context as `Feed | Attendance | Roster | Profile`
- Use back navigation as the primary way out; do not add a milestone-specific bottom menu

**Layout:**
- Background: `#FAF7F2` (warm cream)
- Header (56dp): back `←` left, center "Rohan's Milestones" Inter Semibold 16sp, right: "Add +" Inter Semibold 14sp `#5C8B6E` (tappable)
- Child identity strip (72dp, white surface, 16dp padding, no radius): circular photo (48dp, warm placeholder), "Rohan" Inter Semibold 16sp `#1A1A1A`, below "LKG A · 4 yrs" Inter Regular 13sp `#9A9A9A`. Right side: milestone progress ring (circular progress indicator, 48dp, sage green arc, center shows "12/20" in Inter Semibold 12sp `#1A1A1A`)
- Domain tab bar (48dp, horizontal scroll if needed): 5 tabs — Physical | Cognitive | Language | Social-Emotional | Aesthetic. Active tab: Inter Semibold 14sp `#1A1A1A` with 2dp sage green underline; inactive: Inter Regular 14sp `#9A9A9A`
- Body: scrollable milestone list for selected domain, 16dp horizontal padding
- Bottom: standard tab bar (not shown when accessed as detail view — show back navigation only)

**UI Elements (Milestone Row):**
Each milestone row (white card, 12dp padding, 8dp radius, 8dp gap between rows):
- Left: status icon (24dp circle): achieved — `#5C8B6E` filled circle with white checkmark; not yet — `#E8E2D9` circle with no icon
- Center: milestone name Inter Semibold 14sp `#1A1A1A`, e.g. "Balances on one foot for 5 seconds"; below — age range Inter Regular 12sp `#9A9A9A` "Ages 3.5–4.5"; if achieved: date "Observed 12 Mar 2026" Inter Regular 11sp `#5C8B6E`
- Right (if achieved): "Seen in post ›" tappable text Inter Regular 12sp `#C4784A` terracotta with arrow

Show in Cognitive tab: 4–5 milestones, mix of achieved (checkmark) and not-yet. Example milestones:
- "Sorts objects by 2 attributes" — Achieved (12 Mar)
- "Counts to 10 correctly" — Achieved (20 Feb)
- "Understands cause and effect" — Not yet
- "Names 5+ colours correctly" — Not yet
- "Follows 3-step instructions" — Achieved (5 Mar)

**Colors & Typography:** Warm cream base, white cards, sage green achievement accents, Fraunces not used here (this is data, not editorial), Inter throughout

**States:**

*No milestones logged (new child):* Domain tab shows empty state: a small warm illustration (growth seedling icon in sage + terracotta), "Milestones will appear here as you observe them" Inter Regular 14sp `#9A9A9A`, centered; "Add Observation +" button below (outlined sage green, 48dp)

*Domain switching:* Tabs slide to active, list fades to new domain content (150ms fade)

*Add milestone (tap "Add +"):* Bottom sheet slides up: NEP 2020 domain selector (5 domain pills), then a scrollable list of milestones in that domain. Tap a milestone to mark it observed today. "Date" field (defaults to today, editable). "Link to post (optional) ›" field. [Save] button sage green full-width.

*Dark mode:* Background `#1A1A1A`, cards `#242424`, text `#F5F2EC`, achievement icons lighter sage `#7AAF8C`, tab underline same sage, not-yet circles `#333333`

**Interactions & Animations:**
- Domain tab switch: underline slides to new tab (spring, 200ms), list content fades in/out
- Milestone row tap: row expands to show "Mark as observed" action if not achieved; shows full post link if achieved
- Progress ring: animated fill on load (arc sweeps from 0 to current, 600ms ease-out)
- Add bottom sheet: spring slide-up from bottom (350ms)

---

### Screen T-7: Profile / Settings

**Prompt for Google Stitch:**

Design the Profile & Settings screen for CadenceSprout's teacher app. Sunita accesses this from the bottom nav to manage her account and preferences. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- Render the bottom tab bar exactly as: `Feed | Attendance | Roster | Profile`
- Profile is active

**Layout:**
- Background: `#FAF7F2` (warm cream)
- Header: none (this is a tab, no back button); top of body serves as the visual header
- Bottom tab bar (Profile tab active in sage)
- Body: non-scrollable for first viewport; if content overflows, allow scroll

Content top to bottom (16dp horizontal padding throughout):

1. **Profile card** (white card, 12dp radius, 16dp padding, 16dp top gap): circular photo placeholder (72dp, sage green background with "S" initial for Sunita), right of photo: "Sunita Sharma" Inter Semibold 18sp `#1A1A1A`; below — "Class Teacher · LKG A" Inter Regular 14sp `#6B6B6B`; below — "Sunshine Preschool" Inter Regular 13sp `#9A9A9A`
   Right of card: a small `›` edit icon (16dp `#9A9A9A`) indicating tappable for profile edit

2. **Settings section** (16dp top gap): section header "Notifications" Inter Semibold 13sp `#9A9A9A` uppercase 11sp letter-spacing

   Setting rows (same white card, rows separated by 1dp dividers `#E8E2D9`):
   - "New parent comment" row: label Inter Regular 15sp `#1A1A1A`, right: iOS-style toggle (on, sage green)
   - "Daily attendance reminder" row: same style, toggle on, sage green
   - "Post published confirmation" row: toggle off (`#E8E2D9`)

3. **About section** (12dp top gap): section header "About" same style
   - "App version" row: label left, "v1.0.0" Inter Regular 14sp `#9A9A9A` right, no chevron
   - "Privacy Policy ›" row: label sage green, chevron right
   - "Terms of Service ›" row: same

4. **Log Out button** (24dp top gap): full-width outlined button (48dp, 1.5dp border `#C0392B`, 8dp radius, "Log Out" Inter Semibold 16sp `#C0392B`, no fill — white/transparent background)

**Colors & Typography:** Warm cream, white cards, sage toggles, red logout — clear visual hierarchy, all Inter

**States:**

*Default:* As above, notifications on/on/off

*Toggle tap:* Toggle animates between on (sage green thumb right) and off (grey thumb left), spring animation 200ms, saves preference immediately (no save button needed)

*Log Out tap:* Confirmation alert (iOS native alert style): "Log out of CadenceSprout?" with [Cancel] (default) and [Log Out] (red destructive). On confirm: session cleared, transition to T-0 Login screen

*Profile edit (tap edit icon):* Navigate to edit screen (or in-place field editing): name field, photo picker, read-only class + school

*Dark mode:* Background `#1A1A1A`, profile card + settings card `#242424`, section headers `#9A9A9A`, dividers `#333333`, text `#F5F2EC`, toggles: on = `#7AAF8C`, off = `#444444`

**Interactions & Animations:**
- Tab arrives: profile card fades in (150ms), settings rows stagger-fade in (80ms each)
- Toggle: haptic light on change
- Log Out confirm: transition to Login with a full fade (400ms) — not a slide (implies session reset, not navigation)
- Privacy/Terms links: open in-app browser (SFSafariViewController)

---

### Screen T-2A: Manual Child Tag Picker

**Prompt for Google Stitch:**

Design a bottom-sheet child tag picker for CadenceSprout's teacher app. This sheet opens from the Post Composer when AI tagging is missing or incorrect. The design should feel quick, confidence-building, and teacher-friendly on a busy classroom day.

**Navigation / Menu (hardcoded):**
- No separate menu inside this bottom sheet
- Inherit teacher app navigation context from the invoking screen: `Feed | Attendance | Roster | Profile`

**Layout:**
- iPhone 14 Pro viewport, presented as a bottom sheet over a dimmed Post Composer background
- Sheet height: ~78% of screen, white surface `#FFFFFF`, top corners 20dp radius
- Top handle: 4×36dp pill in `#E8E2D9`, centered, 10dp from top
- Header row: left "Cancel" in Inter Regular 15sp `#6B6B6B`, center title "Tag children in this post" Inter Semibold 16sp `#1A1A1A`, right [Done] text button in sage `#5C8B6E`
- Body padding: 16dp horizontal
- Search field at top: 48dp tall, outlined, 10dp radius, search icon 16dp, placeholder "Search by child name"
- Scrollable child roster list below:
  - Each row 60dp tall, white background
  - Left: 36dp circular avatar/photo
  - Middle: child name Inter Medium 15sp `#1A1A1A`
  - Right: empty circle selector or filled sage check chip when selected
- Selected tray pinned above footer: horizontal row of selected child chips in solid sage green with white text

**States:**

*Default:* Full roster list, no child selected, Done button disabled at 50% opacity

*Search active:* Keyboard up, filtered roster list updates live

*Selection made:* One or more selected chips appear in tray, Done button enabled

*No results:* Warm empty state with small magnifier icon and copy "No children found for 'Ria'" in Inter Regular 14sp `#9A9A9A`

*Loading:* Skeleton list rows with avatar circles + text bars

*Dark mode:* Sheet `#242424`, dim overlay deeper, rows `#242424`, text `#F5F2EC`, borders `#333333`, selected chips `#7AAF8C`

**Interactions & Animations:**
- Sheet slides up with spring animation (350ms)
- Selecting a child animates check indicator and adds chip to tray with scale-in
- Done closes sheet and returns selected chips to Post Composer
- Clear selection via chip `x` icon removes child with fade-out

---

### Screen T-5A: Child Detail

**Prompt for Google Stitch:**

Design a mobile child detail screen for CadenceSprout's teacher app. This screen opens when a teacher taps a child in the class roster. It should feel informative and warm, like a single child's living classroom profile.

**Navigation / Menu (hardcoded):**
- Keep teacher app navigation context as `Feed | Attendance | Roster | Profile`
- Use back navigation in the header; do not add child-specific tabs

**Layout:**
- iPhone 14 Pro viewport, portrait
- Background `#FAF7F2`
- Native-style header with back chevron left, title "Child Profile" centered, more icon right
- Scrollable body, 16dp horizontal padding
- Top profile card:
  - White card, 16dp radius, 18dp padding
  - Top row: 72dp child photo, right side child name in Fraunces Regular 24sp `#1A1A1A`
  - Subtext: age, DOB, class name in Inter Regular 14sp `#6B6B6B`
- Parent section card:
  - Section title "Family Contacts" uppercase Inter Semibold 11sp `#9A9A9A`
  - Parent rows with relationship label, phone number, status badge
  - Quick action icons for call and WhatsApp on each row
- Milestone summary card:
  - Section title
  - 5 mini domain bars or ring summaries
  - CTA row: "View full milestone tracker ›"
- Recent posts card:
  - Latest 3 post previews, each with thumbnail, short caption, date

**States:**

*Normal:* All cards visible with parent info, milestone summary, recent posts

*No parent linked:* Parent card shows warm empty state: "No parent contact added yet." with muted illustration

*No recent posts:* Recent posts card shows "No posts for this child yet."

*Loading:* Skeleton header card, skeleton parent rows, skeleton post previews

*Dark mode:* Background `#1A1A1A`, cards `#242424`, text `#F5F2EC`, dividers `#333333`

**Interactions & Animations:**
- Back returns to roster with slide-right transition
- WhatsApp icon opens external WhatsApp deep link
- View full milestone tracker pushes to T-6
- Post preview tap opens T-3 Post Detail

---

### Screen T-6A: Milestone Picker

**Prompt for Google Stitch:**

Design a milestone picker bottom sheet for CadenceSprout's teacher app. The picker is used to browse and attach NEP 2020 milestones without overwhelming the teacher. It should feel structured, educational, and lightweight.

**Navigation / Menu (hardcoded):**
- No separate menu inside this bottom sheet
- Inherit teacher app navigation context from the invoking screen: `Feed | Attendance | Roster | Profile`

**Layout:**
- Presented as a bottom sheet over either the Post Composer or Child Milestone Tracker
- Sheet height ~82% of screen, white surface, 20dp top corners
- Header: "Select milestone" centered, Cancel left, [Add] right in sage green
- Search field below header: 48dp outlined input, placeholder "Search milestones"
- Domain tab row below search:
  - 5 horizontally scrollable pills: Physical, Cognitive, Language, Social-Emotional, Aesthetic
  - Active pill filled sage green with white text; inactive pills white with sage border/text
- Scrollable list of milestone rows:
  - Title Inter Medium 15sp `#1A1A1A`
  - Domain/age metadata in Inter Regular 12sp `#9A9A9A`
  - Checkbox or selected state on right
- Selected tray pinned above footer with compact selected milestone count and chips

**States:**

*Default:* Domain tabs visible, list populated, Add button disabled

*Search active:* Filtered results update live

*Selection made:* Add button enabled, selected tray visible

*No results:* Educational empty state with copy "No milestones found for your search."

*Loading:* Skeleton pills + skeleton list rows

*Dark mode:* Sheet `#242424`, text `#F5F2EC`, inactive pills dark with `#333333` border, active pill `#7AAF8C`

**Interactions & Animations:**
- Tab switches animate underline/fill transition 180ms
- Selecting a milestone animates checkbox fill + tray chip insertion
- Add button returns selected milestones to source screen
- Sheet closes with spring slide-down

---

*End of Section 4.1 — 11 screens (T-0 through T-7, plus T-2A, T-5A, T-6A)*

---

## Section 4.2 — Parent App (Mobile)

---

### Screen P-0: Parent App Phone Entry / OTP Request

**Prompt for Google Stitch:**

Design a mobile phone number entry and OTP request screen for CadenceSprout's parent app. This is the first native app screen a parent sees after tapping "Get the app" from a WhatsApp magic-link flow. The goal is to feel warm, premium, and friction-light, like a boutique school app rather than a banking or telecom OTP screen.

**Navigation / Menu (hardcoded):**
- No persistent parent menu on this pre-auth screen
- Do not show `Feed | Milestones | Portfolio | Profile` yet

**Layout:**
- iPhone 14 Pro viewport (393×852pt), portrait orientation
- Background: `#FAF7F2` (warm cream), full bleed
- Safe area respected; content vertically arranged with generous breathing room
- Top 20% of screen: warm branded welcome block
  - Circular school logo placeholder (72×72dp) centered — sun + leaf motif in warm yellow `#F5C842` and sage green `#5C8B6E`
  - 12dp below: "Sunshine Preschool" in Inter Semibold 14sp `#6B6B6B`, centered
  - 20dp below: "See every update from your child's day" in Fraunces Regular 28sp `#1A1A1A`, centered, max width 300dp, 120% line-height
  - 12dp below: supporting copy in Inter Regular 15sp `#6B6B6B`, centered: "Enter your phone number to get a one-time code and continue."
- Middle content block (24dp horizontal padding, 32dp top gap from hero):
  - White surface card, 16dp radius, 20dp padding, subtle shadow (`0 2px 8px rgba(0,0,0,0.06)`)
  - Phone number label in Inter Semibold 13sp `#6B6B6B`
  - 8dp gap
  - Phone number input: full width, 52dp tall, outlined 1.5dp border `#E8E2D9`, 10dp radius
    - Left fixed prefix area: `+91` in Inter Regular 15sp `#6B6B6B`
    - Vertical divider after prefix
    - Input placeholder: "Phone number" in Inter Regular 15sp `#9A9A9A`
  - 12dp gap
  - Legal footnote: Inter Regular 12sp `#9A9A9A`, 140% line-height: "By continuing, you agree to receive a one-time verification code by SMS."
  - 20dp gap
  - [Send OTP] primary button: full width, 52dp tall, 10dp radius, fill `#5C8B6E`, label Inter Semibold 16sp white
  - 12dp gap
  - Secondary text link centered: "Open via WhatsApp link instead" in Inter Medium 14sp `#C4784A`
- Bottom area pinned above home indicator:
  - Small reassurance row centered with shield/check icon 14dp in sage and text "Private by design. Your child's data stays protected." in Inter Regular 12sp `#9A9A9A`

**Colors & Typography:**
- Background `#FAF7F2`
- Surface `#FFFFFF`
- Primary action `#5C8B6E`
- Accent link `#C4784A`
- Text primary `#1A1A1A`
- Text secondary `#6B6B6B`
- Dividers/borders `#E8E2D9`
- Headline uses Fraunces; all interactive and support text uses Inter

**States (include all as artboard variants or annotated states):**

*Default:* Empty phone field, Send OTP button disabled at 55% opacity, no error text

*Typing:* Numeric keypad visible, input border becomes 2dp sage green `#5C8B6E`, Send OTP button enabled once a valid 10-digit Indian number is entered

*Loading:* Send OTP button shows a white spinner (20dp) replacing the label, field disabled at 50% opacity, no full-screen loader

*Invalid number:* Inline error below input in Inter Regular 13sp `#C0392B`: "Enter a valid phone number." Input border turns red `#C0392B`

*Send failed:* Full-width inline error banner inside the card, 10dp radius, pale terracotta background `#F7E3D8`, left error icon 16dp terracotta, text `#A14F2A`: "We couldn't send your code. Please try again."

*Success / OTP sent:* Brief success banner in soft sage background `#E7F2EA` with check icon + text "Code sent to +91 98XXXX3210", then transition to OTP verification screen

*Dark mode:* Background `#1A1A1A`, card `#242424`, headline `#F5F2EC`, body text `#9A9A9A`, input border `#333333`, primary button `#7AAF8C`, accent link `#D4875A`

**Interactions & Animations:**
- Screen load: logo and headline fade/slide up together (250ms), card follows with slight stagger (120ms delay)
- Input focus: border color transition 150ms ease, card shifts upward slightly to accommodate keyboard
- Send OTP tap: button scales to 0.97 on press with light haptic feedback
- Success: success banner fades in, then whole screen transitions with fade + slide-left to OTP verification (300ms)
- WhatsApp link tap: opens external deep link or web fallback, not an in-app browser

---

### Screen P-0A: Parent App OTP Verification

**Prompt for Google Stitch:**

Design a mobile OTP verification screen for CadenceSprout's parent app. This screen immediately follows phone number entry. It should feel calm, trustworthy, and premium, not transactional or banking-like. The parent should feel they are one short step away from seeing their child's updates.

**Navigation / Menu (hardcoded):**
- No persistent parent menu on this pre-auth screen
- Do not show `Feed | Milestones | Portfolio | Profile` yet

**Layout:**
- iPhone 14 Pro viewport (393×852pt), portrait orientation
- Background: `#FAF7F2` warm cream
- Safe area respected; vertically centered content with generous whitespace
- Top area:
  - Small back chevron at top-left, 24dp, `#6B6B6B`
  - 28dp below: headline in Fraunces Regular 30sp `#1A1A1A`, centered: "Enter your code"
  - 12dp below: supporting text in Inter Regular 15sp `#6B6B6B`, centered, max width 300dp: "We sent a 6-digit code to +91 98XXXX3210"
- Main card centered on screen with 24dp horizontal padding:
  - White card, 16dp radius, 24dp padding, subtle shadow
  - OTP input row centered: 6 individual boxes, each 44×52dp, 10dp radius, 1.5dp border `#E8E2D9`, white fill, 10dp gap between boxes
  - Each OTP digit uses Inter Semibold 22sp `#1A1A1A`, centered
  - 16dp gap
  - Countdown / helper row centered: "Resend in 00:24" in Inter Regular 13sp `#9A9A9A`
  - 20dp gap
  - [Verify OTP] primary button, full width, 52dp height, 10dp radius, fill `#5C8B6E`, label Inter Semibold 16sp white
  - 12dp gap
  - Secondary text link centered: "Change phone number" in Inter Medium 14sp `#C4784A`
- Bottom reassurance note above home indicator: lock icon 14dp + "Secure sign in for your child's private feed" in Inter Regular 12sp `#9A9A9A`

**Colors & Typography:**
- Same CadenceSprout parent palette as P-0
- Fraunces only for the headline
- Inter for inputs, buttons, helper text, links

**States (include all as artboard variants or annotated states):**

*Default:* Empty OTP boxes, Verify button disabled at 55% opacity

*Typing:* Active box border becomes 2dp sage green `#5C8B6E`, entered boxes show digits, focus auto-advances

*Loading:* Verify button shows white spinner; OTP boxes disabled at 50% opacity

*Invalid OTP:* Inline error under OTP row in Inter Regular 13sp `#C0392B`: "That code is incorrect or expired." All boxes keep current digits, borders turn red

*Resend available:* Timer reaches zero, helper row becomes tappable text link in terracotta `#C4784A`: "Resend code"

*Success:* A small success banner appears inside the card: soft sage background, check icon, text "Verified", then transition to consent or feed

*Dark mode:* Background `#1A1A1A`, card `#242424`, boxes `#242424`, borders `#333333`, digits `#F5F2EC`, button `#7AAF8C`, helper text `#9A9A9A`

**Interactions & Animations:**
- Auto-advance to next OTP box on digit entry
- Full-code paste fills all 6 boxes instantly
- Verify tap scales button to 0.97 with light haptic feedback
- Success transitions with fade + slide-left to next screen (300ms)
- Back tap returns to P-0 with slide-right transition

---

### Screen P-1: Magic-Link Web View (Feed First)

**Prompt for Google Stitch:**

Design the P-1 Magic-Link Web View screen for CadenceSprout. This is a frictionless mobile web view accessed directly from a WhatsApp link, allowing parents to see their child's latest update instantly without installing the app or logging in.

**Navigation / Menu (hardcoded):**
- No persistent menu on this screen.
- Because this is a pre-auth web view, do not include any bottom tab bar, top hamburger menu, or side drawer.

**Layout:**
- iPhone 14 Pro viewport (393×852pt), portrait orientation.
- Background: `#FAF7F2` (warm cream), full bleed.
- Header (64dp tall, no background, 1dp bottom border `#E8E2D9`): Centered block containing the school logo (circular 32×32dp placeholder with a warm yellow `#F5C842` and sage green `#5C8B6E` sun+leaf motif), followed immediately below by "Powered by CadenceSprout" in Inter Regular 12sp `#9A9A9A`.
- Body: Vertically scrollable, with 16dp horizontal padding around content.
- Floating soft install banner (conditional): Anchored to the bottom of the viewport, 16dp above the bottom edge.

**UI Elements (Primary Post Card):**
- Card container (white surface `#FFFFFF`, 12dp border radius, 2dp shadow `elevation: 2` or `box-shadow: 0 2px 4px rgba(0,0,0,0.05)`).
- Full-bleed photo: 4:3 aspect ratio (e.g., 361dp wide × 270dp tall) anchored to the top of the card with top 12dp border radii. Placeholder image: A vibrant preschool activity like finger painting.
- Card Body (below photo, 16dp padding on all sides):
  - Caption: Fraunces Italic 18sp `#1A1A1A`. Example text: "Aarav had a wonderful time exploring colors today! 🌱"
  - 12dp gap.
  - Child Name Tag: Solid pill (28dp tall, 8dp radius), fill `#5C8B6E`, text "Aarav" in Inter Regular 12sp `#FFFFFF`.
  - 16dp gap.
  - Action Row: Circular ❤️ reaction button (44×44dp, `#FAF7F2` background, 20dp heart icon in `#9A9A9A` for default, `#C0392B` for liked). Next to it, text "React to this moment" in Inter Regular 13sp `#6B6B6B`.

**UI Elements (Soft Install Banner):**
- Floating card anchored at the bottom: 12dp radius, `#FFFFFF` background, 4dp shadow (`box-shadow: 0 4px 12px rgba(0,0,0,0.1)`), 16dp padding all around.
- Left side: "Get the app for all of Aarav's updates" in Inter Semibold 14sp `#1A1A1A`, max width 200dp.
- Right side: [Get App] button, 36dp tall, 8dp radius, fill `#5C8B6E`, text Inter Semibold 13sp white.
- Dismiss icon: Small '✕' (16dp, `#9A9A9A`) in the top right corner.

**Colors & Typography:**
- Background `#FAF7F2`, Surface `#FFFFFF`, Primary `#5C8B6E`, Accent (Heart) `#C0392B`.
- Fraunces (serif) only for the caption text. Inter (sans-serif) for all other UI labels and helper copy.

**States (include all as artboard variants or annotated states):**

*First visit (Default):* Header and post card visible. Soft install banner is hidden. Heart icon is outline `#9A9A9A`.

*Reacted State:* Heart icon fills solid `#C0392B`.

*Seen 3+ times:* Floating soft install banner appears at the bottom.

*Expired token:* Post card is hidden. Centered in the body is the text "This link has expired. Ask your school to send a new one." in Inter Regular 16sp `#1A1A1A`. Below it, a full-width primary button "Contact School via WhatsApp" (48dp tall, 8dp radius, fill `#5C8B6E`, text white Inter Semibold 16sp).

*Dark mode:* Background `#1A1A1A`, card surfaces `#242424`, primary text `#F5F2EC`, secondary text `#9A9A9A`, sage primary `#7AAF8C`, divider borders `#333333`.

**Interactions & Animations:**
- Reaction tap: Heart icon turns `#C0392B` instantly with a quick scale-bounce (1.0 → 1.3 → 1.0 over 200ms) and light haptic feedback.
- Banner dismiss (✕) tap: Banner slides down out of the viewport and fades (250ms ease-out).
- Get App tap: Normal button press state, then navigates to the app store.

---

## Section 4.4 — Teacher Web

---

### Screen TW-7: Teacher Web Profile / Settings

**Prompt for Google Stitch:**

Design a desktop-first profile and settings screen for CadenceSprout's teacher web app. This should feel like the browser companion to the teacher mobile app: warm, editorial, and calm, but with the efficiency of a modern web settings page.

**Navigation / Menu (hardcoded):**
- Render the left sidebar exactly as: `Feed | Attendance | Roster | Milestones | Profile`
- Profile is active

**Layout:**
- Desktop viewport 1280×900px
- Background `#FAF7F2`
- Persistent left sidebar (240px) matching the teacher web app with logo, nav links, teacher mini-profile at bottom
- Main content area with 40px page padding
- Page header: "Profile & Settings" in Fraunces Regular 32px `#1A1A1A`, subcopy in Inter Regular 15px `#6B6B6B`
- Two-column main layout:
  - Left column (340px): profile summary card
  - Right column (fluid): stacked settings panels
- Cards/panels: white, 16px radius, subtle shadow, 24px padding

**Content:**
- Left profile card:
  - 88px avatar
  - Teacher name
  - Role and class assignment
  - School name
  - Small edit profile button
- Right settings panels:
  - Notifications with 3 toggles
  - Preferences with language and upload quality dropdowns
  - Browser permissions/help panel with browser notification status banner
  - Account panel with logout button and app version text

**States:**

*Default:* All settings visible, toggles in current state

*Browser notifications blocked:* Amber inline banner with "Enable in browser settings" CTA

*Save success:* Top-right toast "Settings updated."

*Save failed:* Inline row-level error message beneath the changed control

*Loading:* Skeleton profile card + skeleton rows in each panel

**Interactions & Animations:**
- Toggles update optimistically
- Dropdown menus open below trigger with soft scale/fade
- Logout opens centered confirmation modal
- Sidebar remains static; only content area scrolls if needed

---

## Section 4.5 — Parent Web

---

### Screen PW-5: Parent Web Profile / Settings

**Prompt for Google Stitch:**

Design a mobile-first responsive profile and settings screen for CadenceSprout's parent web experience. This screen should feel family-friendly, private, and lightweight, with a strong sense of trust.

**Navigation / Menu (hardcoded):**
- Mobile bottom nav must be exactly: `Feed | Milestones | Portfolio | Profile`
- Desktop header nav must be exactly: `Feed | Milestones | Portfolio | Profile`
- Profile is active in both cases

**Layout:**
- Primary viewport mobile web 375×812px, but include responsive hints for desktop
- Background `#FAF7F2`
- Mobile header with school logo left, page title centered, no heavy chrome
- Scrollable body with 16dp horizontal padding
- Top profile card:
  - Parent name
  - Masked phone number
  - School name
  - Linked child summary
- Grouped white settings cards:
  - Notifications card with per-post and daily digest toggles
  - Privacy card with "Data & Privacy ›" and "Privacy Policy ›" rows
  - About card with app/web version row
  - Account card with outlined red Log Out button
- On desktop, center content in a 720px column with more breathing room

**States:**

*Default:* Profile card + all settings groups visible

*Loading:* Skeleton profile card and skeleton rows

*Save success:* Toast "Settings updated."

*Save failed:* Inline error under affected toggle row

*Dark mode:* Background `#1A1A1A`, cards `#242424`, text `#F5F2EC`, dividers `#333333`

**Interactions & Animations:**
- Toggle switches animate smoothly with 180ms spring
- Data & Privacy row navigates to PW-6
- Log Out opens centered confirmation modal on desktop, bottom sheet confirmation on mobile

---

### Screen PW-6: Parent Web Privacy Settings

**Prompt for Google Stitch:**

Design a web view privacy settings screen for CadenceSprout's parent web experience. This screen manages DPDP consent and must feel serious, transparent, and reassuring without becoming legalistic or cold.

**Navigation / Menu (hardcoded):**
- Mobile bottom nav must be exactly: `Feed | Milestones | Portfolio | Profile`
- Desktop header nav must be exactly: `Feed | Milestones | Portfolio | Profile`
- Keep `Profile` as the active menu context

**Layout:**
- Mobile web viewport 375×812px primary, responsive up to desktop
- Background `#FAF7F2`
- Header: back chevron, title "Your child's privacy controls", school logo context
- Centered content column with 16dp horizontal padding mobile, 720px max width desktop
- Main white card with 18dp radius, 20dp padding:
  - Child context row with child avatar and name
  - Three consent rows, each with:
    - Title in Inter Semibold 15sp `#1A1A1A`
    - Description text in Inter Regular 13sp `#6B6B6B`
    - Toggle on right
    - "Last updated: [date]" caption below where applicable
  - One consent row is informational/read-only and uses a disabled toggle appearance
  - Link row: "See full privacy policy"
- Sticky bottom action area:
  - [Save changes] primary button only visible when changes have been made

**States:**

*Default:* All current consent states visible, Save button hidden

*Toggle changed:* Save button appears from bottom with slide-up animation

*Revoke confirmation:* Face-recognition toggle off opens modal dialog with warm white surface, destructive confirm, and explanatory text

*Saved:* Top toast "Privacy settings updated."

*Revocation pending:* Soft terracotta info banner: "Existing recognition data will be deleted within 24 hours."

*Dark mode:* Background `#1A1A1A`, card `#242424`, text `#F5F2EC`, borders `#333333`, primary button `#7AAF8C`

**Interactions & Animations:**
- Toggle animations use smooth spring motion
- Save bar slides up only when there are unsaved changes
- Privacy policy opens in modal overlay on mobile and centered modal on desktop
- Destructive confirmation modal uses red confirm button and neutral cancel button

---

*End of current prompt additions — newly drafted screens include P-0A, P-1, T-2A, T-5A, T-6A, TW-7, PW-5, and PW-6*
