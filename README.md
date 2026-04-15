# Information Exploration

A Quarto textbook for **INFO 3401: Information Exploration** at the
University of Colorado Boulder, by Brian C. Keegan, Ph.D.

The book teaches undergraduate information-science students how to find,
clean, analyze, and communicate with real-world data. It uses Python
(pandas, NLTK, networkx, geopandas, statsmodels) and SQL (SQLite), and
covers both tabular and non-tabular data. The audience is juniors and
seniors who are curious about data and technology but often lack
confidence in their technical abilities. The voice is reassuring,
confident second person — the book treats paratechnical skills and
public-interest framing as first-class topics alongside the analytical
techniques.

## Book Structure

| Part | Chapters | Topics |
|------|----------|--------|
| **I: Foundations** | 4 | Workspace setup, documentation and errors, research questions, public interest data science |
| **II: Python** | 4 | Loading, cleaning, extending, and reshaping data with pandas |
| **III: SQL** | 4 | Loading, cleaning, extending, and reshaping data with SQLite |
| **IV: Non-Tabular Data** | 5 | Spatial (geopandas), network (networkx), text (nltk), time series (statsmodels/prophet), structured web data (requests + BeautifulSoup) |
| **V: Analysis** | 5 | Descriptive, qualitative, comparative, visual, and modeling exploration |
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
├── 19-qualitative.qmd
├── 20-comparative.qmd
├── 21-visualization.qmd
├── 22-modeling.qmd
├── appendix-datasets.qmd          # Appendix A
├── appendix-llm-methods.qmd       # Appendix B
├── book/                          # Rendered HTML output
├── LICENSE
└── README.md
```

## Datasets

All datasets used in the book are documented in Appendix A
(`appendix-datasets.qmd`) — source, URL, columns, and known quirks for
each one. Files not shipped with this repository (e.g., Census TIGER/Line
shapefiles, FRED time series) link to the original publisher.

| Dataset | Source | Used in |
|---------|--------|---------|
| Colorado Cannabis Sales by County | Colorado Department of Revenue | Python Loading, SQL Loading |
| Boulder County Voter Registration | Boulder County Clerk and Recorder | Python Cleaning |
| Lahman Baseball Database | Sean Lahman | Python Extending, Python Reshaping, Analysis |
| Colorado Population Estimates (DOLA) | Colorado State Demography Office | Python Extending, Python Reshaping, SQL Cleaning, SQL Reshaping |
| CDC Mortality Data | CDC WONDER | SQL Cleaning, SQL Reshaping |
| CBI Crime Statistics | Colorado Bureau of Investigation | SQL Cleaning, SQL Reshaping |
| Boulder County Assessor — Buildings | Boulder County Assessor | SQL Extending |
| Census TIGER/Line Shapefiles | US Census Bureau | Spatial |
| ICON / KONECT network datasets | Various | Network |
| Project Gutenberg / NLTK corpora | Various | Text |
| FRED / World Bank / IMF series | Various | Time Series |

## Building the Book

### Prerequisites

Install [Quarto](https://quarto.org/docs/get-started/) (version 1.4 or
later) and a Python environment with the required packages.

```bash
# Create and activate a conda environment
conda create -n info3401 python=3.11
conda activate info3401

# Install required Python packages
pip install pandas numpy matplotlib seaborn scipy statsmodels jupyter \
            geopandas networkx nltk requests beautifulsoup4
```

Verify Quarto is installed:

```bash
quarto check
```

### Rendering

To render the full book to HTML:

```bash
quarto render
```

Output is written to the `book/` directory. Open `book/index.html` in a
browser to view it. The book is configured with `execute.eval: false` in
`_quarto.yml`, so code blocks display as source but are not executed
during render. This keeps the build fast and independent of the datasets
described in Appendix A.

To preview a single chapter with live reload:

```bash
quarto preview 05-py-loading.qmd
```

To render to a specific format:

```bash
quarto render --to pdf        # PDF via LaTeX (requires a LaTeX distribution)
quarto render --to docx       # Word document
```

### Notes on Code Execution

The `_quarto.yml` file sets `eval: false` globally, which means code
blocks are displayed but not executed during the render. This is
intentional: the datasets are not included in the repository, and running
the code requires them to be present in the working directory.

To execute code blocks interactively, open the `.qmd` files as Jupyter
notebooks:

```bash
quarto convert 05-py-loading.qmd   # converts to .ipynb for Jupyter
```

## Contributing

Contributions are welcome. Before opening a pull request, please read the
following:

### Reporting Errors

If you find a technical error — incorrect code, a wrong description of
pandas or SQL behavior, a broken exercise — please
[open an issue](https://github.com/cuinfoscience/Information-Exploration-Book/issues)
with:

1. The chapter file and section heading where the error appears
2. A description of the error
3. The correct information and, if available, a link to primary documentation

### Proposing Changes

For content changes beyond error corrections (new sections,
reorganization, additional exercises), open an issue first to discuss the
change before submitting a pull request. This avoids duplicated effort
and ensures proposed additions fit the book's scope and pedagogical
approach.

### Style Conventions

- Section anchors follow the pattern `{#sec-filename-sectionname}`,
  e.g., `{#sec-py-loading-checklist}`
- Cross-references use `@sec-` notation throughout
- Callout boxes use Quarto's built-in callout types: `.callout-note`,
  `.callout-tip`, `.callout-warning`, `.callout-important`
- Code blocks specify the language: ` ```{python} `, ` ```{sql} `,
  ` ```{bash} `
- Exercises are placed in collapsible `.callout-note collapse="true"`
  blocks with solutions nested inside

### Commit Message Format

Use a short imperative summary followed by a blank line and a more
detailed explanation if needed:

```
fix: correct read_csv header parameter description in 05-py-loading

The header parameter uses zero-indexing, so header=2 selects the third
row, not the second. Updated the inline comment and prose explanation.
```

Common prefixes: `fix:` (bug/error), `feat:` (new content), `refactor:`
(restructuring without content change), `docs:` (README, comments).

## License

The book content is copyright Brian C. Keegan, Ph.D. Code examples are
available under the MIT License. See `LICENSE` for details.

## Acknowledgments

This book grew out of the INFO 3401: Information Exploration course at
the University of Colorado Boulder. It reflects the contributions of
many students whose questions, mistakes, and feedback shaped the
material into its current form. See
[Appendix B: AI Use Disclosure](appendix-llm-methods.qmd) for an account
of the role of large language models in producing this text.
