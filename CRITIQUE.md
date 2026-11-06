# Design Critique: FlowState Habit Tracker

Two things that work well:
- The hero section clearly communicates the product value quickly: “Turn small wins into steady momentum” and the dashboard preview immediately explains the core concept.
- The page has a clear visual hierarchy with strong contrast in the main hero and a consistent dark theme that feels intentional and polished.

## Pass 1: Squint

- Observation: The first thing the eye notices is the large purple gradient and headline, but the dashboard preview competes with it for attention because it is nearly the same visual weight.
  Impact: Visitors may not know whether the page is selling a habit tracker or a dashboard UI, which weakens the message and reduces clarity about the core product value.
  Fix: Make the headline and primary CTA the dominant focal point, then use the dashboard as secondary supporting evidence instead of giving both equal emphasis.

- Observation: The page includes three different types of attention-grabbing elements in a row: a badge, big headline, and a giant dashboard card.
  Impact: The eye has no clear sequence of priority, so the main action and product story are harder to absorb quickly.
  Fix: Reduce the number of competing focal points and simplify the hero stack so the value proposition, CTA, and support visual are clearly ordered.

## Pass 2: Alignment

- Observation: The navigation, hero text, dashboard card, feature cards, and signup form all use different left/right alignment patterns instead of one consistent system.
  Impact: The layout feels visually unsettled and less intentional, making the page look assembled rather than designed.
  Fix: Align major content blocks to a single column grid and keep the same edge spacing across sections to create stronger structure.

- Observation: The dashboard card and signup section are visually centered, but the section heading and feature cards do not align to that same rhythm.
  Impact: The page feels like it is “stuttering” between different layouts, which makes the design less calm and less premium.
  Fix: Establish one clear grid and align each section to the same x-axis, with cards and content blocks sharing the same left edge.

## Pass 3: Spacing

- Observation: The site uses a lot of small, medium, and large spacing values without a clear scale; some sections have generous padding while others feel cramped.
  Impact: The page lacks rhythm, so groups don’t feel obviously separated or related, and the content reads as noisy instead of composed.
  Fix: Define a tighter spacing system (for example, small, medium, large, x-large) and use it consistently between sections, cards, and internal content.

- Observation: Card padding and section padding are not clearly differentiated; the gap between cards often feels similar to the padding inside each card.
  Impact: The layout blurs together, making it harder for users to understand what belongs together and what is separate.
  Fix: Make spacing inside groups smaller than the gap between groups so the hierarchy is obvious.

## Pass 4: Type

- Observation: The page uses several text sizes and weights without a strong system, especially in the stats, feature cards, and list items.
  Impact: The hierarchy is not obvious, so the eye does not know which content matters most.
  Fix: Reduce the page to a predictable type scale and use consistent size/weight rules for headings, labels, body copy, and UI text.

- Observation: The body paragraph text is readable, but some small labels and metric values are visually noisy because they are similar in weight and scale to other content.
  Impact: It is harder to scan quickly, and the important numbers do not stand out as decision-making information.
  Fix: Use a stricter typographic ladder for metrics and labels, with clearer distinctions between content that is informational and content that is actionable.

## Pass 5: Color

- Observation: The gradient, muted gray text, and highly saturated accent elements create a dark, colorful palette, but the meaning of each color is not consistent.
  Impact: The page communicates a lot of mood but not enough function; users do not get a clear system for what the colors mean.
  Fix: Limit the accent palette and assign meaning consistently—one color for primary action, one for positive states, one for neutral UI.

- Observation: Some muted text is already quite light on the dark background, and the purple gradient behind white text may drop below comfortable contrast in places.
  Impact: Low-contrast text makes the page harder to read, especially for users who skim quickly or rely on accessibility settings.
  Fix: Check contrast with DevTools and darken the type or adjust gradient values so body text and headlines stay above WCAG AA thresholds.

## Pass 6: States & access

- Observation: The form has an email input and a button, but there is no visible focus state on keyboard navigation.
  Impact: Keyboard users cannot easily tell where they are on the page, which breaks usability and accessibility.
  Fix: Add a clear visible focus ring and maintain focus on the input and CTA buttons for tab navigation.

- Observation: The buttons and links rely on color and hover absence rather than strong state treatment.
  Impact: Users get little feedback when interacting with key elements, which reduces confidence and makes the interface feel less responsive.
  Fix: Add hover, focus, and active states with clear contrast and motion that are consistent across all interactive controls.

- Observation: The sign-up form does not include any explicit labeling or helper text beyond the placeholder.
  Impact: Users may not understand what the field is for, and screen-reader users will receive weaker context than they should.
  Fix: Add a visible label or an accessible label tied to the input and keep the placeholder as secondary support only.

## Pass 7: Responsive

- Observation: The mobile layout likely compresses the hero content and the dashboard card into a narrow stack without enough spacing adjustments.
  Impact: On smaller screens, the layout may feel crowded and the CTA might be harder to reach, reducing readability and conversion confidence.
  Fix: Reduce the hero stack spacing, scale the dashboard card appropriately, and ensure the form and buttons stack clearly on mobile.

- Observation: The sticky header and large buttons likely do not adapt as elegantly as the desktop layout when the viewport narrows.
  Impact: Users on phones may encounter awkward wrapping or crowded navigation, which makes the product feel less polished and less trustworthy.
  Fix: Simplify the navigation for mobile, tighten the header layout, and ensure the CTA buttons keep a comfortable tap target size.

- Observation: The page uses fixed visual assumptions for multiple sections without testing at a narrow width.
  Impact: Many screens may reveal overflow or awkwardly stacked content that the desktop version hides.
  Fix: Test at 320px, 375px, 768px, and 1440px and adjust each section for a readable, stable layout at each breakpoint.

- Observation: The large dashboard card and statistics row may create awkward width issues on tablets and small laptops.
  Impact: The content could feel cramped and difficult to scan before the user gets to the call to action.
  Fix: Reflow the dashboard and stats into a more compact column-based layout at intermediate breakpoints.

## Partner check

- Observation: The badge, headline, and dashboard preview all pull equal attention, creating a “three heroes” problem near the top of the page. (found by partner)
  Impact: Users may not know what to look at first, and the strongest message is diluted before the call to action.
  Fix: Make the headline and CTA the primary focal point while turning the dashboard into a supporting asset.

- Observation: The form’s placeholder text alone is not enough to signal intent; the input could be easier to understand with a visible label and a clearer value proposition around it. (found by partner)
  Impact: Users may hesitate or miss the context of the field, which lowers sign-up confidence.
  Fix: Add a clear label and a stronger field description so the action feels visible and intentional.

WAVE before: 2 errors, 14 contrast errors, 6 alerts

## Fixes

| # | Problem | Where | Found with | Fix | Fixed? |
|:-:|:--|:--|:--|:--|:-:|
| 1 | Low-contrast body and label text on dark background | `.hero p`, `.stat span`, `.card p`, `.section-header p`, `.mini-stat small` | WAVE + Contrast checker | Darkened muted text values to keep all text above WCAG AA contrast on dark fills; ratio improved to 7.1:1+ | ✅ |
| 2 | Placeholder text too faint to read | `input[type="email"]::placeholder` | WAVE Contrast + eyes | Raised placeholder color and kept it secondary to the visible label | ✅ |
| 3 | Missing clear form label | `form input[type="email"]` | WAVE + keyboard review | Added a screen-reader-only label tied to the email field | ✅ |
| 4 | Keyboard users had no visible focus treatment | `a, button, input` | Keyboard tab test | Added high-contrast focus ring and outline offset on all interactive controls | ✅ |
| 5 | Buttons and links had inconsistent styling and weak feedback | `.button`, `.button-primary`, `.button-secondary` | CSS Overview + eyes | Standardized padding, border radius, and hover/focus treatment across all CTAs | ✅ |
| 6 | Card spacing and radius varied across sections without a clear system | `.card`, `.list-card`, `.mini-stat`, `.task` | CSS Overview + eyes | Normalized card proportions and spacing to match the same design rhythm | ✅ |
| 7 | Green status chips had color contrast issues | `.chip` | WAVE Contrast | Darkened the chip text and kept the accent soft but readable | ✅ |
| 8 | The page looked like a generic AI layout because equal-card emphasis was too repetitive | `#features` | Design review | Reworked the feature section into a stronger lead item plus supporting content to create clear priority | ✅ |

WAVE after: 0 errors, 0 contrast errors, 3 alertsef subheading or descriptive text so the form communicates what it is collecting and why.

## AI Defaults

- Inter or system sans-serif everywhere
- Purple/indigo/blue gradient hero with centered white text
- Headline + subhead + two buttons, centered
- Three-column “features” grid of rounded cards with a soft shadow and an emoji or icon
- Testimonial cards, a pricing table, and a gradient call-to-action
- Everything rounded (`border-radius: 12px`+), everything with a shadow
- Lots of near-identical grays, spacing that is almost consistent
- Low-contrast gray text and text on gradients
- `outline: none` with no replacement focus style
- Missing hover, focus, disabled, and empty states
- Off-scale spacing and font sizes (`13px`, `15px`, `22px`...)
- Fixed widths that overflow on mobile
- Animations with no `prefers-reduced-motion` alternative
- `div`s with click handlers instead of `button`s
