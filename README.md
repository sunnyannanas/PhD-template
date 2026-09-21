# PhD Thesis Template — University of Portsmouth

A LaTeX thesis template structured for doctoral submissions at the University of Portsmouth. It follows the standard PhD thesis format and includes pre-configured front matter, a recommended chapter structure, acronym management with PDF tooltips, and working examples of tables, figures, and TikZ diagrams.

## Requirements

- A LaTeX distribution with pdflatex (e.g. [TeX Live](https://www.tug.org/texlive/) or [MiKTeX](https://miktex.org/))
- The following packages must be available (all are included in a full TeX Live / MiKTeX installation):

  `scrbook`, `setspace`, `hyperref`, `inputenc`, `babel`, `fontenc`, `graphicx`, `fancyhdr`, `lmodern`, `type1cm`, `color`, `units`, `enumerate`, `array`, `multirow`, `adjustbox`, `pdflscape`, `mdframed`, `pgfplots`, `tikz`, `comment`, `xcolor`, `float`, `fdsymbol`, `pdfpages`, `subcaption`, `longtable`, `tabularx`, `booktabs`, `placeins`, `colortbl`, `pdfcomment`, `acronym`, `nowidow`, `natbib`, `caption`

To compile, run pdflatex twice (the second pass resolves cross-references):

```bash
pdflatex main.tex
pdflatex main.tex
```

Or use latexmk for automatic multi-pass compilation:

```bash
latexmk -pdf main.tex
```

## File Structure

```
.
├── main.tex                    # Root document — packages, settings, include order
├── references.bib              # BibTeX bibliography
├── apa_like.bst                # Bibliography style file
│
├── 0.1_Titelpage.tex           # Title page
├── 0.2_Abstract.tex            # Abstract (~300 words, no abbreviations)
├── 0.3_Declaration.tex         # Declaration of originality
├── 0.4_Acknowledgments.tex     # Acknowledgements
├── 0.5_AI_Acknowledgments.tex  # AI Acknowledgement Statement (mandatory)
├── 0.6_Publications.tex        # List of publications
├── 0.7_Definitions.tex         # Acronym definitions
│
├── 1_Introduction.tex          # Chapter 1 — also documents the template itself
├── 2_Literature_review.tex     # Chapter 2
├── 3_Methodology.tex           # Chapter 3
├── 4_Main_Chapter.tex          # Chapter 4
├── 5_Main_Chapter.tex          # Chapter 5
├── 6_Main_Chapter.tex          # Chapter 6
├── 7_Main_Chapter.tex          # Chapter 7
├── 8_Conclusion.tex            # Chapter 8
├── 9_Appendix.tex              # Appendix (excluded from List of Figures/Tables)
│
└── figures/
    ├── chapter_0/              # Title page image (university coat of arms)
    ├── chapter_1/              # Figures for Chapter 1
    ├── chapter_2/              # Figures for Chapter 2
    └── chapter_3/              # Figures for Chapter 3
```

## Getting Started

1. **Title page** — edit `0.1_Titelpage.tex` to update your name, thesis title, and submission date.
2. **Abstract** — replace the placeholder text in `0.2_Abstract.tex` with your own (~300 words, no abbreviations).
3. **Declaration** — `0.3_Declaration.tex` contains a ready-to-use declaration. Update the name, location, and date.
4. **AI Acknowledgement** — fill in `0.5_AI_Acknowledgments.tex`. This section is mandatory for all submissions. If you did not use AI tools, state that explicitly.
5. **Acronyms** — add or remove entries in `0.7_Definitions.tex` using `\acro{SHORT}{Full expansion}`. See the Acronyms section below for usage.
6. **Chapters** — write your content in the numbered chapter files. Add more chapter files and `\include{}` them in `main.tex` if needed.
7. **References** — add BibTeX entries to `references.bib` and cite using `\citep{}` or `\citet{}` (natbib).
8. **Figures** — place images in the relevant `figures/chapter_X/` subdirectory and include them with `\includegraphics{}`.

## Acronyms

Acronyms are defined in `0.7_Definitions.tex` and managed by the `acronym` package with `[nohyperlinks,printonlyused]`. The template also uses `pdfcomment` to add hover tooltips to abbreviations in the PDF.

| Command | Behaviour |
|---|---|
| `\ac{KEY}` | Full form on first use, short form thereafter |
| `\acs{KEY}` | Always short form, with PDF tooltip showing the full expansion |
| `\acsp{KEY}` | Plural short form, with PDF tooltip |
| `\acl{KEY}` | Always full form |

To add a new acronym, add a line to the `acronym` environment in `0.7_Definitions.tex`:

```latex
\acro{XYZ}{Your Full Expansion Here}
```

The template ships with pre-configured acronyms relevant to machine learning and data science research. Because `printonlyused` is enabled, only the acronyms you actually cite in your thesis body will appear in the compiled Definitions list.

## Appendix

The appendix (`9_Appendix.tex`) is configured so that figures and tables inside it do **not** appear in the List of Figures or List of Tables in the front matter. This is controlled by:

```latex
\captionsetup[figure]{list=no}
\captionsetup[table]{list=no}
```

at the top of the appendix file. The appendix includes three worked examples you can use as references:

- `tab:example_appendix` — a `booktabs` table
- `fig:example_appendix` — an `\includegraphics{}` figure
- `fig:tikz_appendix` — a TikZ flowchart

The appendix is also where ethics confirmation documents and UPR16 forms should be placed.

## AI Acknowledgement Statement

The AI Acknowledgement Statement is **mandatory** for all doctoral submissions at the University of Portsmouth. The template provides a draft in `0.5_AI_Acknowledgments.tex` with placeholder sections for writing and coding use. Key points:

- If no AI tools were used, state this explicitly.
- AI used as a research subject or tool may be signposted to the relevant thesis sections rather than described again.
- Unacknowledged use of AI may constitute misconduct.
- All references must be verified by you — AI-generated references are not reliable.
- Grammar and spell-check tools (e.g. Grammarly) are permitted, but you must make every suggested change yourself.

## Bibliography

The template uses `natbib` with an `apalike` bibliography style. The bibliography is generated from `references.bib`. Citation commands:

```latex
\citep{key}   % (Author, Year)
\citet{key}   % Author (Year)
```

The bibliography heading is renamed to "References" via `\renewcommand{\bibname}{References}` in `main.tex`.

## Notes on Compilation Warnings

- **Label(s) may have changed / Rerun** — standard LaTeX behaviour; run pdflatex twice or use latexmk.
- **fancyhdr with KOMA-Script** — a known compatibility warning. The header/footer functionality works correctly; the warning can be suppressed by switching to `scrlayer-scrpage` if desired.

## Author & Creator

**sunnyannanas**

