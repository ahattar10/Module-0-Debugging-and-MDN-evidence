# Module 0 Debugging and MDN Evidence

## Project Overview

Debugging exercise for `index.html` and `styles.css`, documented with MDN citations and validator evidence.

## Tools Used

- Nu HTML Checker
- MDN Documentation

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
