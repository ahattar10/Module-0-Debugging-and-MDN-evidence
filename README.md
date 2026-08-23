# Module 0 Debugging and MDN Evidence

## Project Overview

Debugging exercise for `index.html` and `styles.css`, documented with MDN citations and validator evidence.

## Tools Used

- Nu HTML Checker
- MDN Documentation
- Chrome Devtools
---

## Issue 1: Heading order out of sequence

**What I observed:**

The page used an H3 heading before an H2 heading, which skips a level and breaks the logical document outline.

**Evidence and citation:**

I ran `index.html` through the Nu HTML Checker and it flagged the heading as out of order.

<img width="600" alt="NU HTML validator before" src="https://github.com/user-attachments/assets/af467eb2-677f-44b3-a07b-d54e1eccc383" />

MDN's [HTML Heading Elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements) page states:

> "Do not skip heading levels: always start from `<h1>`, followed by `<h2>` and so on."

<img width="600" alt="MDN page" src="https://github.com/user-attachments/assets/714a4fe4-7bd0-425a-81f5-7628afad5284" />

Following this guidance, I corrected the heading order so the levels progress without skipping.

**Fix applied:**

I changed the earlier heading from H3 to H2 so the heading levels progress in order without skipping.

After the fix, the Nu HTML Checker reported no errors.
<img width="1030" height="786" alt="Nu_HTML validatior after" src="https://github.com/user-attachments/assets/489dbc1f-439e-492b-b842-f08df9a60aa7" />

---

## Issue 2: Focus outline removed from links

**What I observed:**

The page removed the outline from focused links. When I pressed Tab to move through the page, there was no visible indicator.

I opened DevTools and checked the `:focus` state on a link. The rule being applied was `outline: none`, which removed the focus indicator.

![focus](<tab button before.png>)

![focus](<focus is not correct.png>)

MDN's [focus](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/:focus) page states: 

> "Never just remove the focus outline (visible focus indicator) without replacing it with a focus outline that will pass WCAG 2.1 SC 1.4.11 Non-Text Contrast."

Following this guidance, I added a visible outline back to the focused links.

**Fix applied:**

I changed the `outline: none` rule to a visible focus indicator.  

```css
a:focus {
  outline: 3px solid #0077cc;
  outline-offset: 2px;
}
```

After the fix, the blue outline appears on each link as I Tab through the page.

![focus](<tab button after.png>)