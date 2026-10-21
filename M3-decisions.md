# M3 decisions

## Design tokens

The shared stylesheet is organized around three token groups at the top:

- **Color roles:** `--color-ink` and `--color-muted` handle text; `--color-page` and `--color-surface` distinguish the page from cards; `--color-brand` and `--color-brand-dark` identify interactive and structural areas; `--color-accent` marks focus and small highlights; `--color-border` separates components.
- **Spacing scale:** `--space-1` through `--space-12` keep gaps and padding consistent.
- **Type scale:** `--type-sm` through `--type-display` set a readable hierarchy, with the display size adapting to viewport width.

The content width is limited for long-form reading. Cards and buttons are reusable classes. The navigation has hover, current-page, and keyboard focus states. The 320 px fix stacks the header, collapses the cards to one column, and lets the skills table scroll within a labelled region.

## Rival prompt and defence

The rival stylesheet was generated from the four HTML pages only, using the prompt: **“Write a complete stylesheet for this markup.”** It is kept unchanged in `ai-style.css`; only the copies under `preview-ai/` link to it.

After reviewing the measurements, the AI defence was:

> “The blue palette gives the pages a consistent student-portfolio identity, and the container, cards, and repeated spacing make the content easy to scan. The shorter stylesheet is quick to understand. The gold button is intended to stand out as the main action, while the nested hover rule adds a stronger navigation cue. Some repeated colors are deliberate so each component can be adjusted locally.”

## Where the defence is right

- The body text pairs pass: the rival's body color measures **5.46:1** on the page and **5.87:1** on cards.
- The blue palette, centered content width, clear headings, and card grouping work for this portfolio.
- Repetition can make a small stylesheet straightforward to read. The rival has **39 qualified selectors**, compared with **60** in the custom stylesheet.

## Where it is wrong

- The argument that gold helps the primary action does not address readability: white button text on `#d6a640` is **2.24:1**, below 4.5:1. Normal navigation text is **4.44:1**, also below the target.
- The shorter file is not automatically easier to maintain: it has **32 hard-coded hex occurrences**, **7 repeated hex values**, a **four-group deepest selector**, and **one `!important`** override. The custom sheet uses **29 color-token references**, no repeated hex values, and no `!important`.
- The claim that the layout is complete is weakened by the 320 px inspection: the rival navigation remains on one row, its three-column cards stay compressed, and the skills table has no overflow treatment.

## Decisions and justified changes

- **Kept:** the limited reading width, card grouping, and clear blue visual identity. These choices fit the HTML and support scanability.
- **Rejected:** white text on a gold primary button. The measured ratio is too low; the custom button uses white text on the blue token instead (**7.07:1**).
- **Rejected:** deep selector nesting and `!important`. A direct class rule is easier to find and adjust.
- **Applied:** a narrow-screen media query and a labelled horizontal scroll region for the table, based on the 320 px findings. This is committed separately as `Fix narrow layouts with wrapping and table scrolling`.

## Authorship note

This project was generated with AI assistance, including `css/style.css`; it does **not** satisfy the assignment's “unaided stylesheet” requirement or the instruction to re-type adopted ideas personally. Use it as a VS Code reference. To submit work as your own unaided stylesheet, re-create the CSS yourself and describe the AI assistance honestly.
