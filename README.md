# Information Exploration

A Quarto textbook for **INFO 3401: Information Exploration** at the University
of Colorado Boulder, by Brian C. Keegan, Ph.D.

The book teaches undergraduate information-science students how to find,
clean, analyze, and communicate with real-world data. It uses Python
(pandas, NLTK, networkx, geopandas, statsmodels) and SQL (SQLite), and
covers both tabular and non-tabular data. The audience is juniors and
seniors who are curious about data and technology but often lack confidence
in their technical abilities. The voice is reassuring, confident second
person — the book treats paratechnical skills and public-interest framing
as first-class topics alongside the analytical techniques.

## Book Structure

| Part | Chapters | Topics |
|------|----------|--------|
| **I: Foundations** | 4 | Workspace setup, documentation and errors, research questions, public interest data science |
| **II: Python** | 4 | Loading, cleaning, extending, and reshaping data with pandas |
| **III: SQL** | 4 | Loading, cleaning, extending, and reshaping data with SQLite |
| **IV: Non-Tabular Data** | 5 | Spatial (geopandas), network (networkx), text (nltk), time series (statsmodels/prophet), structured web data (requests + BeautifulSoup) |
| **V: Analysis** | 4 | Descriptive statistics, visualization, hypothesis testing, linear models |
| **Appendices** | 2 | Dataset documentation; AI use disclosure |

## Repository Structure

```
Information-Exploration-Book/
├── _quarto.yml                    # Book configuration
├── index.qmd                      # Preface
├── 01-setup.qmd                   # I: Foundations
├── 02-documentation.qmd
├── 03-research-questions.qmd
├── 04-public-interest.qmd
├── 05-py-loading.qmd              # II: Python
├── 06-py-cleaning.qmd
├── 07-py-extending.qmd
├── 08-py-reshaping.qmd
├── 09-sql-loading.qmd             # III: SQL
├── 10-sql-cleaning.qmd
├── 11-sql-extending.qmd
├── 12-sql-reshaping.qmd
├── 13-spatial.qmd                 # IV: Non-Tabular Data
├── 14-dyadic.qmd
├── 15-textual.qmd
├── 16-temporal.qmd
├── 17-structured.qmd
├── 18-descriptive.qmd             # V: Analysis
├── 19-visualization.qmd
├── 20-hypothesis-testing.qmd
├── 21-linear-models.qmd
├── appendix-datasets.qmd          # Appendix A
├── appendix-llm-methods.qmd       # Appendix B
├── book/                          # Rendered HTML output
├── LICENSE
└── README.md
```

## Building the Book

This book is built with [Quarto](https://quarto.org/). To render locally:

```bash
quarto render
```

Output appears in `book/`. The book is configured with `execute.eval: false`
in `_quarto.yml`, so code blocks display as source but are not executed
during render. This keeps the build fast and independent of the datasets
described in Appendix A.

To verify the configuration:

```bash
quarto check
```

## Datasets

All datasets used in the book are documented in Appendix A
(`appendix-datasets.qmd`) — source, URL, columns, and known quirks for
each one. Files not shipped with this repository (e.g., Census TIGER/Line
shapefiles, FRED time series) link to the original publisher.

## Contributing

This textbook is actively maintained for INFO 3401. Pull requests that
correct typos, tighten examples, or flag broken cross-references are
welcome. For larger structural changes, open an issue first to discuss.

## License

See [`LICENSE`](./LICENSE).

## Acknowledgments

This book grew out of the INFO 3401: Information Exploration course at
the University of Colorado Boulder. It reflects the contributions of many
students whose questions, mistakes, and feedback shaped the material into
its current form.

AI assistance used in drafting and editing is disclosed in
**Appendix B: AI Use Disclosure** (`appendix-llm-methods.qmd`).
