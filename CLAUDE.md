# Claude.md

## Project Direction

Transform the portfolio UI into a **professional, lightweight sky-blue themed portfolio**.

The reference design uses a clean editorial layout with large typography, generous whitespace, subtle cards, and minimal visual decoration. Keep that design philosophy, but replace the current neutral/gray visual identity with a refined sky-blue palette.

The result must feel like a real software engineer's portfolio — **not an AI-generated template**.

---

## Core Goals

1. Professional and credible
2. Lightweight and fast
3. Clean visual hierarchy
4. Sky-blue visual identity
5. Minimal animations
6. No unnecessary UI decoration
7. No generic "AI portfolio" aesthetic
8. Responsive on mobile, tablet, and desktop
9. Accessible and readable
10. Easy to maintain

---

## Visual Direction

### Primary Theme

Use sky blue as the main accent.

Recommended palette:

- Primary: `#38BDF8`
- Primary Dark: `#0284C7`
- Primary Soft: `#E0F2FE`
- Primary Pale: `#F0F9FF`
- Background: `#FFFFFF`
- Surface: `#F8FAFC`
- Text: `#111827`
- Secondary Text: `#64748B`
- Border: `#E2E8F0`

Do not use the entire palette everywhere.

Use sky blue primarily for:

- links
- buttons
- active navigation
- small accents
- icons
- hover states
- selected elements
- subtle gradients when genuinely useful

The interface should remain mostly white and neutral.

---

## Design Principles

### 1. Avoid AI Slop

Do NOT create:

- excessive gradients
- glowing blue blobs
- giant abstract 3D shapes
- excessive glassmorphism
- excessive rounded cards
- random floating elements
- meaningless badges
- unnecessary statistics
- fake testimonials
- generic "Innovative / Passionate / Creative" filler
- excessive animations
- oversized decorative icons
- random code snippets purely for decoration
- excessive shadows
- purple-to-blue AI-style gradients
- "AI startup landing page" aesthetics

The portfolio should look like it was designed intentionally by a professional developer.

Prefer:

- typography
- whitespace
- alignment
- grid structure
- subtle borders
- restrained shadows
- small color accents
- real project information
- clear navigation

---

## Typography

Use a modern sans-serif font.

Preferred options:

1. Inter
2. Geist
3. Manrope
4. DM Sans

Do not use overly decorative fonts.

Typography should create the visual hierarchy.

Suggested scale:

- Hero heading: large and bold
- Section heading: medium-large
- Project title: medium
- Body text: 16px
- Supporting text: 14px
- Small metadata: 12–13px

Avoid making every heading extremely large.

---

## Layout

Maintain the strong left/right composition from the reference.

### Hero

The hero should contain:

- name
- professional title
- short introduction
- technology stack
- social links

Example positioning:

```text
Al Fatih
Zainul
Falah

Software Engineer & Creative Technologist

Short, confident introduction.

[Tech stack]

[GitHub] [Portfolio/Social] [LinkedIn] [Other]
```

The hero should immediately communicate:

**Who I am + what I do + what I build.**

Do not fill the hero with unnecessary text.

---

## Project Showcase

Use real projects as the primary visual content.

Each project should communicate:

- project name
- short description
- technology
- role or contribution
- relevant link

Use simple cards or editorial project layouts.

Cards should not look like generic SaaS dashboard cards.

Recommended styling:

- white background
- thin border
- subtle shadow
- 12–20px border radius
- small sky-blue accent
- clean typography

Avoid excessive card nesting.

---

## Navigation

Navigation should be simple.

Recommended sections:

- Home
- About
- Projects
- Skills
- Contact

Do not create unnecessary navigation items.

The active navigation state can use sky blue.

---

## Technology Stack

Show technologies clearly without turning the page into a logo wall.

Relevant technologies may include:

- PHP
- Laravel
- JavaScript
- React
- Vue.js
- Flutter
- Tailwind CSS
- Bootstrap
- MySQL
- PostgreSQL
- Git
- Docker

Only display technologies that are actually relevant to the portfolio.

Use official logos when available.

Keep icon sizing consistent.

---

## Animation

Animation should be subtle and purposeful.

Allowed:

- fade-in
- slight translate
- hover elevation
- color transition
- navigation indicator
- gentle card movement

Avoid:

- constant floating animations
- excessive parallax
- spinning elements
- animated backgrounds
- cursor-following effects
- excessive scroll effects

Animation should never make the website feel heavy.

Respect:

```css
prefers-reduced-motion
```

---

## Performance

The website must remain lightweight.

Prioritize:

- optimized images
- lazy loading
- minimal JavaScript
- reusable components
- CSS over JavaScript when possible
- no unnecessary animation libraries
- no unnecessary dependencies
- optimized SVGs
- semantic HTML

Do not install a library just to solve a simple styling problem.

---

## Responsive Design

The design must work well at:

- 320px
- 375px
- 390px
- 768px
- 1024px
- 1280px
- 1440px+

### Mobile

On mobile:

- reduce hero typography
- stack columns vertically
- keep navigation simple
- prevent horizontal overflow
- make buttons touch-friendly
- reduce decorative elements
- maintain generous but reasonable spacing

Do not simply shrink the desktop layout.

Create a proper mobile composition.

---

## Accessibility

Follow basic accessibility standards.

Requirements:

- sufficient color contrast
- semantic HTML
- meaningful `alt` attributes
- keyboard-accessible navigation
- visible focus states
- buttons must be real buttons
- links must be real links
- form fields must have labels
- do not rely only on color to communicate state

Sky blue text on white must have enough contrast.

When `#38BDF8` does not provide enough contrast for text, use `#0284C7` instead.

---

## Content Style

Writing should sound like a real developer.

Use:

- concise sentences
- specific descriptions
- real technical information
- confident but modest language

Avoid:

- corporate buzzwords
- exaggerated claims
- generic motivational phrases
- fake expertise
- excessive adjectives

Bad:

> "I am a passionate and innovative software engineer who transforms ideas into cutting-edge digital experiences."

Better:

> "I build web applications with PHP, Laravel, JavaScript, and modern frontend tools."

Keep content direct.

---

## Code Quality

Keep the implementation simple.

Follow the existing project's architecture unless there is a strong reason to change it.

Rules:

- reuse components
- avoid duplicated code
- use clear naming
- keep components focused
- avoid unnecessary abstraction
- avoid overengineering
- remove unused imports
- remove unused CSS
- keep dependencies minimal

Do not rewrite working code unnecessarily.

---

## Styling Rules

Prefer:

- CSS variables
- Tailwind utility classes if Tailwind is already installed
- existing design tokens
- consistent spacing
- consistent border radius
- consistent typography

Do not introduce a second styling system without a reason.

Suggested CSS variables:

```css
:root {
  --primary: #38BDF8;
  --primary-dark: #0284C7;
  --primary-soft: #E0F2FE;
  --primary-pale: #F0F9FF;

  --background: #FFFFFF;
  --surface: #F8FAFC;

  --text: #111827;
  --text-muted: #64748B;

  --border: #E2E8F0;
}
```

---

## Visual Weight

The portfolio should feel:

**70% white / neutral**
**20% typography / dark elements**
**10% sky-blue accent**

Sky blue is an accent, not the entire background.

Do not turn every section blue.

---

## Shadows

Use shadows sparingly.

Preferred:

```css
box-shadow: 0 8px 30px rgba(15, 23, 42, 0.06);
```

Avoid large dramatic shadows.

Borders are often preferable to shadows.

---

## Border Radius

Keep radius consistent.

Recommended:

- buttons: 8–10px
- cards: 12–16px
- inputs: 8–10px
- small badges: 6–8px

Avoid excessive pill-shaped UI unless it has a clear purpose.

---

## Do Not Change

Unless explicitly requested, do not remove or significantly alter:

- project information
- technology names
- social links
- personal information
- existing functional behavior
- routing
- API integration
- working components

The task is primarily a **visual redesign**, not a complete rewrite.

---

## Before Making Changes

1. Inspect the existing project structure.
2. Identify the framework and styling system.
3. Reuse existing components where possible.
4. Identify existing colors and design tokens.
5. Check responsive behavior.
6. Make the smallest reasonable set of changes.

Do not blindly rewrite the project.

---

## Final Quality Checklist

Before finishing, verify:

- [ ] Sky-blue theme is consistent
- [ ] Design remains mostly white and clean
- [ ] No excessive gradients
- [ ] No AI-slop visual patterns
- [ ] No unnecessary animations
- [ ] Typography has clear hierarchy
- [ ] Project section is easy to scan
- [ ] Navigation is simple
- [ ] Mobile layout works correctly
- [ ] No horizontal overflow
- [ ] Images are optimized
- [ ] No unnecessary dependencies were added
- [ ] Existing functionality still works
- [ ] Accessibility basics are maintained
- [ ] UI looks professional rather than template-generated

---

## Overall Design Statement

> Build a clean, editorial-style software engineer portfolio with a restrained sky-blue identity. Prioritize typography, whitespace, real project content, and usability over visual effects. The final result should feel lightweight, professional, personal, and intentionally designed — never like generic AI-generated web design.
