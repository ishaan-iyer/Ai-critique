### Layout: features
- **What:** AI layout → feature + supporting layout
- **Why:** my brief says "calm, confident"
- **Verified:** checked at 375px and 1280px

### Microinteractions: FlowState

#### Interactive control: `.button` — job: feedback

| State | Visual treatment |
|---|---|
| Default | Primary gradient or outlined secondary button |
| Hover | Brightens, lifts slightly, and increases shadow; secondary adds a soft fill |
| Focus-visible | High-contrast outline and outer ring |
| Active | Darkens, presses down, and reduces shadow |
| Disabled | Reduced opacity, no shadow or movement, and a not-allowed cursor |

Durations and easing use the motion tokens in `after/tokens.css`.

#### Parent trigger: `.card .arrow` — job: orientation

| State | Visual treatment |
|---|---|
| Default | Arrow rests beside the card link |
| Card hover | Arrow slides 5px right |
| Link focus-visible | Arrow slides 5px right when keyboard focus is inside the card |
| Reduced motion | Arrow remains still while focus and hover styling remain visible |

#### Looping animation: `.status-pulse` — job: attention

| State | Visual treatment |
|---|---|
| Default | Small green status dot |
| Loop | Dot gently pulses in scale and opacity |
| Reduced motion | Scale motion is replaced by a gentle opacity fade |
