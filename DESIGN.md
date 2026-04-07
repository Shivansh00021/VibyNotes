# Design System Strategy: The Midnight Curator

## 1. Overview & Creative North Star
The North Star for this design system is **"The Midnight Curator."** 

We are moving away from the "utility-first" clutter of traditional note-taking apps. Instead, we are building a high-end digital sanctuary. This system treats every note as a curated artifact. By leveraging intentional asymmetry and tonal depth, we avoid the rigid, "boxed-in" feeling of generic templates. We prioritize white space (or "dark space") and typographic weight to guide the eye, creating a layout that feels editorial, rhythmic, and effortlessly premium.

## 2. Colors & Surface Philosophy
The palette is rooted in a deep, nocturnal spectrum, designed to eliminate eye strain while maintaining a high-fashion aesthetic.

### The "No-Line" Rule
**Explicit Instruction:** Designers are prohibited from using 1px solid borders for sectioning or containment. Structural boundaries must be defined solely through background color shifts or tonal transitions.
*   *Implementation:* Use `surface-container-low` for the main canvas and `surface-container-high` for interactive elements. This creates a "molded" look rather than a "drawn" one.

### Surface Hierarchy & Nesting
Treat the UI as a series of physical layers—like stacked sheets of tinted obsidian.
*   **Base:** `surface` (#0b1326)
*   **Elevated Section:** `surface-container` (#171f33)
*   **Interactive Cards:** `surface-container-highest` (#2d3449)
*   **Active States:** Utilize a subtle `primary_container` (#a78bfa) at 10-15% opacity to "lift" an element without breaking the dark-mode immersion.

### The "Glass & Gradient" Rule
To inject "soul" into the interface, floating elements (modals, FABs, navigation bars) should utilize **Glassmorphism**. 
*   **Recipe:** `surface_container_high` at 70% opacity + `backdrop-blur: 20px`.
*   **Glows:** For primary actions, use a subtle linear gradient from `primary` (#cebdff) to `primary_container` (#a78bfa) at a 135° angle.

## 3. Typography: The Editorial Voice
We utilize a dual-font strategy to balance character with legibility.

*   **Display & Headlines (Manrope):** This is our "Editorial" voice. Use `display-lg` and `headline-md` with tight letter-spacing (-0.02em) to create an authoritative, modern feel.
*   **Body & Labels (Plus Jakarta Sans):** Our "Functional" voice. This typeface offers exceptional readability at small sizes. 
*   **Hierarchy Tip:** Contrast a `display-md` heading with a `label-sm` in `on_tertiary_fixed_variant` for metadata. The massive scale jump creates an intentional, high-end rhythmic tension.

| Role | Token | Font | Size |
| :--- | :--- | :--- | :--- |
| Hero | `display-lg` | Manrope | 3.5rem |
| Title | `title-lg` | Plus Jakarta Sans | 1.375rem |
| Reading | `body-lg` | Plus Jakarta Sans | 1rem |
| Metadata | `label-sm` | Plus Jakarta Sans | 0.6875rem |

## 4. Elevation & Depth
In this design system, shadows are light, not dark. They represent the "glow" of a digital object.

*   **The Layering Principle:** Place a `surface-container-lowest` card on a `surface-container-low` section to create a soft, natural "recessed" effect.
*   **Ambient Shadows:** For floating notes or menus, use extra-diffused shadows.
    *   *Value:* `0px 20px 40px rgba(0, 0, 0, 0.3)` combined with a subtle outer glow using the `secondary` (#5de6ff) token at 5% opacity.
*   **The "Ghost Border" Fallback:** If a border is required for accessibility, use the `outline_variant` token at **15% opacity**. Never use 100% opaque lines.

## 5. Components

### Buttons
*   **Primary:** Gradient fill (`primary` to `primary_container`), `xl` (1.5rem) rounded corners. Text color: `on_primary`.
*   **Secondary:** No fill. "Ghost Border" (`outline_variant` @ 20%) with `Plus Jakarta Sans` Bold.
*   **Tertiary:** Text only in `secondary` (#5de6ff). Use for low-emphasis actions like "Cancel."

### Cards (Note Previews)
*   **Style:** No borders. Use `surface-container-highest`.
*   **Interaction:** On hover, transition the background to `surface_bright` and apply a 2px `secondary_fixed` bottom-glow.
*   **Spacing:** Enforce a strict 24px internal padding to ensure the "Editorial" breathing room.

### Input Fields
*   **Canvas:** `surface_container_lowest` (#060e20).
*   **State:** When active, the label should shift to `secondary` (#5de6ff) and the container should receive a soft `backdrop-filter` blur.

### Note Lists
*   **Forbidden:** Horizontal divider lines.
*   **Standard:** Use 16px of vertical white space and a 4px `primary` accent bar on the left of the "Active" note to denote selection.

### Custom Component: The "Vibe Tag"
*   A selection chip using `secondary_container` (#00cbe6) with a 10% opacity fill and a `secondary` text color. Used for categorizing notes by mood or project.

## 6. Do’s and Don’ts

### Do:
*   **Do** use asymmetrical margins (e.g., a wider left margin for titles) to create an editorial feel.
*   **Do** use the `secondary` (#5de6ff) accent sparingly for "micro-moments"—a cursor blink, a notification dot, or a successful save icon.
*   **Do** prioritize typography over icons. Let the words speak.

### Don't:
*   **Don't** use pure black (#000000). It kills the "Midnight" depth. Always stay within the `surface` token range.
*   **Don't** use standard "drop shadows" on cards. Stick to tonal layering and high-diffusion ambient glows.
*   **Don't** cram information. If a screen feels busy, increase the padding-block by 20%.