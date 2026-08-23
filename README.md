# Module 0 Debugging and MDN Evidence

## Project Overview

Debugging exercise for `index.html` and `styles.css`, documented with MDN citations and validator evidence.

## Tools Used

- Nu HTML Checker
- MDN Documentation
- Chrome DevTools

---

## Issue 1: Heading order out of sequence

**Condition and symptom:**

The page used an H3 heading before an H2 heading, which skips a level and breaks the logical document outline.

**Evidence:**

I ran `index.html` through the Nu HTML Checker and it flagged the heading as out of order.

<img width="600" alt="NU HTML validator before" src="https://github.com/user-attachments/assets/af467eb2-677f-44b3-a07b-d54e1eccc383" />

**Root cause:**

The markup used an H3 element where the document structure expected an H2. The earlier heading was coded at the wrong level, which skipped a heading level and broke the outline.

**MDN authority:**

MDN's [HTML Heading Elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements) page states:

> "Do not skip heading levels: always start from `<h1>`, followed by `<h2>` and so on."

<img width="600" alt="MDN page" src="https://github.com/user-attachments/assets/714a4fe4-7bd0-425a-81f5-7628afad5284" />

Following this guidance, I corrected the heading order so the levels progress without skipping.

**Correction:**

I changed the earlier heading from H3 to H2 so the heading levels progress in order without skipping.

**Observed test:**

- **Condition:** Ran the repaired `index.html` through the Nu HTML Checker.
- **Expected result:** The validator reports no heading errors.
- **Actual result:** After the fix, the Nu HTML Checker reported no errors.

<img width="1030" height="786" alt="Nu HTML validator after" src="https://github.com/user-attachments/assets/489dbc1f-439e-492b-b842-f08df9a60aa7" />

---

## Issue 2: Focus outline removed from links

**Condition and symptom:**

The page removed the outline from focused links. When I pressed Tab to move through the page, there was no visible indicator showing which link was active.

**Evidence:**

I opened DevTools and checked the `:focus` state on a link. The rule being applied was `outline: none`, which removed the focus indicator.

![screenshot](<tab button before-1.png>)

![screenshot](<focus is not correct-1.png>)

**Root cause:**

The stylesheet contained the rule `a:focus { outline: none; }`, which removed the browser's default focus indicator from links without providing a replacement.

**MDN authority:**

MDN's [focus](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/:focus) page states:

> "Never just remove the focus outline (visible focus indicator) without replacing it with a focus outline that will pass WCAG 2.1 SC 1.4.11 Non-Text Contrast."

Following this guidance, I added a visible outline back to the focused links.

**Correction:**

I changed the `outline: none` rule to a visible focus indicator.

![screenshot](<tab button after-1.png>)

---

## Issue 3: Card grid columns overflow the container

**Condition and symptom:**

The card section used fixed-width columns that overflowed the main content area. The three cards did not fit inside the white container and extended past its right edge.

**Evidence:**

I opened DevTools and inspected the `.cards` section. The grid rule at `styles.css:47` set the columns to fixed pixel widths:

![screenshot](<cards dont fit before.png>)

The grid was set to `grid-template-columns: 300px 300px 300px`, which totals 932px including gaps. The main element provides only 896px of usable width after its padding, so the cards overflowed the container.

**Root cause:**

The grid used hard-coded pixel widths for its three columns instead of flexible sizing. The fixed columns exceeded the available space inside the main element.

**MDN authority:**

MDN's [grid-template-columns](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/grid-template-columns) page explains the `fr` unit:

> "Is a non-negative dimension with the unit fr specifying the track's flex factor. Each `<flex>`-sized track takes a share of the remaining space in proportion to its flex factor."
![MDN grid-template-columns page showing fr unit](<MDN grid_template_flex.png>)


Following this guidance, I changed the fixed pixel columns to flexible fractions so the cards expand and contract with the container.

**Correction:**

I changed the grid columns from fixed pixels to flexible fractions. 

![screenshot](<cards after .png>)