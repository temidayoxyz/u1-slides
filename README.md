# U1 Slides

**A presentation application. Open, edit and save the files you already have.**

Part of the [UnsoftOne](https://github.com/temidayoxyz/unsoftone) suite.

```
Download. Install. Work.
```

No account. No subscription. No sign-in. No internet connection. No telemetry.
Your files stay on your disk, in standard formats, readable by any other
software.

---

## Status: not started

**Nothing has been built yet.** This repository is a placeholder holding the
project's direction and history so that work can start cleanly and be picked up
without reconstructing context.

U1 Slides begins after U1 Docs is genuinely working. That sequencing is
deliberate — see
[ADR-0008](https://github.com/temidayoxyz/unsoftone/blob/main/docs/adr/0008-product-sequencing-u1-docs-first.md).

---

## This is expected to be the hardest of the four

We would rather say this now than after committing to a date.

PPTX is not primarily a text problem, which is where most of the shared
infrastructure is concentrated. It is:

- **floating shapes at absolute coordinates** — not flow layout
- **z-order** — what is in front of what, and what happens when it is wrong
- **autofit text behaviour** — PowerPoint shrinks, grows or overflows text to
  fit a shape, with rules that are not documented and are not consistent
- **theme inheritance** — colours and fonts cascading through several
  inheritance levels in ways that must be resolved to draw anything at all
- **animation and transition** metadata that must be preserved even if we never
  render it

This is why [`PLAN.md`](https://github.com/temidayoxyz/unsoftone/blob/main/PLAN.md)
does not commit to a date for U1 Slides.

**Practical consequence:** getting a PPTX to *display correctly* is much easier
than getting it to *edit correctly*. Preserving animation, transitions, charts
and SmartArt untouched — even when we cannot edit them — is the requirement that
matters most. See
[ADR-0005](https://github.com/temidayoxyz/unsoftone/blob/main/docs/adr/0005-ooxml-lossless-layer.md).

---

## What this will be

A presentation application capable of opening, editing, saving and exporting the
files people already encounter in the Microsoft Office ecosystem.

### Feature depth, in priority order

1. Slide canvas, zoom, pan, scroll
2. Slide creation, deletion, ordering, duplication
3. Text boxes: content, formatting, alignment, autofit
4. Placeholders and layout inheritance
5. Images: insert, resize, crop, position
6. Basic shapes, lines, fills, borders
7. Slide masters and layouts
8. Themes: colours, fonts, background
9. Tables and charts
10. Speaker notes
11. Animation and transitions — preserved from the start, editing later
12. Import and export: PPTX, PDF

---

## Compatibility

Tracked in the
[ecosystem compatibility matrix](https://github.com/temidayoxyz/unsoftone/blob/main/docs/compatibility.md).

| Format  | Status                                                      |
| ------- | ----------------------------------------------------------- |
| `.pptx` | Primary target. Not started.                                |
| `.pdf`  | Import and export planned.                                  |
| `.odp`  | After PPTX.                                                 |
| `.ppt`  | Legacy binary. Deliberately not committed to.               |

---

## What carries over from U1 Docs

The work on U1 Docs is not wasted here. The following transfer directly:

- font management, shaping and inline text layout
- the OOXML/OPC container layer — PPTX and DOCX share it
- undo/redo engine, clipboard handling, accessibility plumbing
- PDF export

That shared foundation is exactly why
[ADR-0008](https://github.com/temidayoxyz/unsoftone/blob/main/docs/adr/0008-product-sequencing-u1-docs-first.md)
builds one product deeply before starting the others. The second product is
cheaper than the first by a large margin.

---

## Building

Nothing to build yet. This project is Rust — see
[ADR-0001](https://github.com/temidayoxyz/unsoftone/blob/main/docs/adr/0001-rust-first-architecture.md).

---

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) first.

**This project is not ready for feature contributions.** The most useful
contributions right now are discussion and real-world `.pptx` files that break
things — particularly ones with animations, SmartArt, charts or unusual
layouts. Redact anything you are not permitted to share.

Please do not send documents containing anything you are not permitted to
share.

---

## Related

| Project                      | What it is                            |
| ---------------------------- | ------------------------------------- |
| [`unsoftone`](https://github.com/temidayoxyz/unsoftone) | Ecosystem direction, ADRs, roadmap |
| [`u1-docs`](https://github.com/temidayoxyz/u1-docs)     | Word processing — in progress        |
| [`u1-sheets`](https://github.com/temidayoxyz/u1-sheets) | Spreadsheets                         |
| [`u1-notes`](https://github.com/temidayoxyz/u1-notes)   | Notes                                |

## License

[GPL-3.0](LICENSE) ·
[ADR-0006](https://github.com/temidayoxyz/unsoftone/blob/main/docs/adr/0006-license-gpl-3.md)
