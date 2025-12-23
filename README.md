Exported prompt:

# Prompt: Create juul.cat - Vaping Cat Clicker Game

Create a single-file HTML game called "juul.cat" - an infinite clicker game featuring a vaping cat. The game should be fully self-contained with embedded images as base64 and no external dependencies.

## Core Gameplay

**Objective:** Click anywhere (or press Space/Enter) to earn "puffs". No limit - infinite clicker with exponential progression through upgrades.

**Stats Tracking:**
- Session Puffs: Current session count (resets on refresh)
- Total Puffs: All-time cumulative (persists in localStorage, used as currency)

**Visual Effects:**
- Smoke cloud animations on each click (💨, ☁️, 🌫️, 💭 emojis)
- Juul pod particle effects (spinning images) every 3 puffs
- Cat image scales up 5% briefly on click
- All effects use CSS animations

## Upgrade System (Shop)

**10 Base Multipliers** (progressive unlock, must buy in order):
1. 2x Multiplier - 100 puffs
2. 3x Multiplier - 300 puffs (requires 2x)
3. 5x Multiplier - 1,000 puffs (requires 3x)
4. 10x Multiplier - 5,000 puffs (requires 5x)
5. 25x Multiplier - 25,000 puffs (requires 10x)
6. 50x Multiplier - 100,000 puffs (requires 25x)
7. 100x Multiplier - 500,000 puffs (requires 50x)
8. 250x Multiplier - 2,500,000 puffs (requires 100x)
9. 500x Multiplier - 10,000,000 puffs (requires 250x)
10. 1000x Multiplier - 50,000,000 puffs (requires 500x)

**3 Session Multipliers** (multiply everything - gold/yellow highlight):
1. 3x Session - 5,000,000 puffs (requires 250x base)
2. 5x Session - 25,000,000 puffs (requires 3x session)
3. 10x Session - 100,000,000 puffs (requires 5x session)

**How it works:** Base multipliers set puffs per click. Session multipliers multiply the base.
Example: 1000x base × 10x session = 10,000 puffs per click!

**Shop features:**
- Costs subtract from Total Puffs
- All purchases persist in localStorage
- Show current multiplier: "10000x active (1000x × 10x)" if session multiplier owned
- Display user's available puffs
- Lock/unlock system with "Requires previous upgrade" messaging

## Anti-Cheat System

**Detection:** Monitor click intervals. Clicks faster than 50ms are suspicious.

**Progressive Warnings (100 strike system):**
- 0-30 suspicious clicks: No warning
- 30-70 clicks: Red tint on screen, red session box, warning text appears
- 70-100 clicks: Intense red effects, cat image shaking
- 100+ clicks: Game over - explosion animation (💥), cat fades out, show "AUTOCLICKER DETECTED" screen

**Visual effects for cheating:**
- Red filter on cat image (increases with suspicion)
- Background gradient turns red
- Cat shakes violently
- Warning text: "⚠️ SUSPICIOUS CLICKING: X strikes left ⚠️"

**Fairness:** Suspicion slowly decreases (0.5 per normal click) so fast legitimate clickers aren't punished.

## Multilingual Support (4 Languages)

Default language: **English**

**Languages:** English, Català, Español, Русский

**Translate ALL of these elements:**
- Button text (Shop, Rules, Reset, GitHub)
- Stat labels (Session Puffs, Total Puffs)
- Subtitle ("click anywhere to rip the juul ⚡")
- Warning messages
- Shop modal (title, items, prices, descriptions)
- Rules modal (all content)
- Game over screen
- Confirmation dialogs
- Success messages
- All 13 multiplier names and descriptions

**Language switcher:** 4 buttons (Català, English, Español, Русский) positioned at bottom of content, scrolls with page. Save preference to localStorage.

## UI Layout & Design

**Top buttons (fixed):**
- Reset (top-left, red tinted) - Opens confirmation dialog
- Rules (top-center-right, blue tinted) - Opens rules modal
- Shop (top-right, standard) - Opens shop modal

**Main content (centered, flexbox, scrollable):**
- Title: "juul.cat 💨" with floating animation
- Cat image (vaping cat with Juul)
- Stats boxes (2): Session Puffs (with multiplier display) | Total Puffs
- Subtitle text
- Warning text (hidden unless cheating detected)
- Language switcher (4 buttons, wraps on mobile)

**Bottom button (fixed):**
- GitHub link (bottom-right) - Links to https://github.com/juulcatsite/juulcat

**Color scheme:**
- Background: Purple gradient (#667eea to #764ba2)
- Danger mode: Red gradient when cheating
- Session multipliers: Gold/yellow tint
- Glassmorphism effects (backdrop-blur) on all UI elements

**Typography:**
- System font stack: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif
- Responsive sizing using clamp() for all text

## Responsive Design

**Use modern CSS:**
- Flexbox layout (no fixed pixel positioning)
- `clamp()` for responsive font sizes
- Viewport units (vw, vh) for spacing
- `max-width` + `aspect-ratio` for containers
- All sizing should be fluid and adaptive

**Key responsive features:**
- Title: `clamp(2rem, 8vw, 4rem)`
- Cat container: max-width 500px on desktop, 280px on mobile
- Stats boxes: flexible with `clamp()` padding
- Language buttons: wrap on small screens
- All spacing uses flexible units (rem, vh, vw)

**Mobile optimizations:**
- Touch-friendly buttons (`touch-action: manipulation`)
- No tap highlight (`-webkit-tap-highlight-color: transparent`)
- Proper button sizing (minimum 44px touch targets)
- Content scrolls naturally, no cutoff

## Modals

**Shop Modal:**
- Full-screen overlay with scrollable content
- Shows user's available puffs at top
- Lists all 13 upgrades (10 base + 3 session)
- Each item shows: name, description, price, buy/owned/locked button
- Session multipliers have gold background
- Close button (×) in top-right

**Rules Modal:**
- Explains game mechanics:
  - How to play (click/space/enter)
  - Stats explanation
  - Base vs Session multipliers with examples
  - Anti-cheat warning (vague: "Don't cheat or cat explodes!")
  - Tips for progression
- Fully translated in all 4 languages
- Close button (×)

**Game Over Modal (Autoclicker Detection):**
- Black background with red text
- Shows final score
- "AUTOCLICKER DETECTED" message
- "Try Again (Legitimately)" restart button

## Data Persistence (localStorage)

**Save these items:**
- `juulcat-total-puffs`: Total puffs count
- `juulcat-upgrades`: Array of owned upgrade IDs (JSON)
- `juulcat-lang`: Current language preference

**Auto-save:** Every 5 puffs during gameplay

**Reset function:** Clear all localStorage data with confirmation dialog

## Milestone Messages

Show popup messages at these puffs:
- 50: "Half a hundy! 💯"
- 100: "TRIPLE DIGITS! 🎉"
- 420: "NICE 😎"
- 500: "FIVE HUNDRED! 🔥"
- 1000: "ONE THOUSAND! 🚀"

(Translate these for all languages)

## Technical Requirements

**Single HTML file:**
- All CSS in `<style>` tag
- All JavaScript in `<script>` tag
- Cat image embedded as base64 PNG
- Juul pod image embedded as base64 WEBP
- No external dependencies or CDN links

**Browser compatibility:**
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile responsive (iOS Safari, Chrome Mobile)
- Works offline (fully self-contained)

**Performance:**
- Smooth animations (CSS transforms, no layout thrashing)
- Efficient particle cleanup (remove after animation)
- Debounced auto-save

## Images Needed

You'll need to embed these as base64:
1. **Cat image**: Photo of a cat holding/vaping a Juul device
2. **Juul pod image**: Image of a Juul pod for particle effects

## Additional Features

**Keyboard support:**
- Space or Enter to click
- Escape to close modals

**Click exclusions:** Don't count clicks on:
- Buttons (Shop, Rules, Reset)
- Modals
- Language switcher
- GitHub link

**Visual polish:**
- Smooth transitions (0.3s ease)
- Hover effects on all buttons
- Active states (scale down on press)
- Loading states handled gracefully

## Rules Modal Content Structure

For each language, include:

1. **How to Play** - Click/keyboard instructions
2. **Stats** - Session vs Total explanation
3. **Upgrades** - Base multipliers (2x→1000x) and Session multipliers (3x, 5x, 10x) with unlock requirements
4. **Max Power** - Example: "1000x base × 10x session = 10,000 puffs per click!"
5. **Anti-Cheat** - Vague warning about suspicious clicking causing explosion
6. **Tips** - Upgrade strategy, save for session multipliers, reset option

## Testing Checklist

Ensure the game:
- ✅ Counts clicks correctly with multipliers
- ✅ Saves and loads progress from localStorage
- ✅ Detects autoclickers and shows game over
- ✅ All translations work properly
- ✅ Responsive on mobile and desktop
- ✅ Shop locks/unlocks correctly
- ✅ Reset clears everything with confirmation
- ✅ Modals open/close properly
- ✅ No content cutoff on any screen size
- ✅ Language switcher scrolls with content
- ✅ GitHub link opens in new tab

## Style Notes

- Comic, playful vibe (not serious/professional)
- Smooth, modern animations
- Purple aesthetic (vaping/juul brand colors)
- Glassmorphism effects
- Clean, readable interface
- No clutter - minimalist where possible

---

**Output:** One complete, working HTML file that I can open in a browser and play immediately. Name it `index.html` or `juul.cat.html`.
