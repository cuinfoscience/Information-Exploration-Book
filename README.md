# Information Exploration

A Quarto textbook for **INFO 3401: Information Exploration** at the University of Colorado Boulder, by Brian C. Keegan, Ph.D.

The book teaches exploratory data analysis using Python (pandas) and SQL (SQLite), organized around a four-stage Load–Clean–Extend–Reshape workflow applied consistently across both tools. It is designed for undergraduate students who have completed one introductory Python course.

## Book Structure

| Part | Chapters | Topics |
|------|----------|--------|
| **I: Foundations** | 7 | Terminal, project organization, documentation, Python environments, error messages, research questions, public interest data science |
| **II: Python** | 4 | Loading, cleaning, extending, and reshaping data with pandas |
| **III: SQL** | 4 | Loading, cleaning, extending, and reshaping data with SQLite |
| **IV: Analysis** | 3 | Descriptive statistics, visualization, hypothesis testing |
| **Appendices** | 2 | Dataset documentation; AI use disclosure |

## Datasets

All datasets are available in the accompanying GitHub repository under `data/`. Each chapter assumes the relevant files are in your working directory. Dataset sources and known quirks are documented in the [Datasets appendix](appendix-datasets.qmd).

| Dataset | Source | Used in |
|---------|--------|---------|
| Colorado Cannabis Sales by County | Colorado Department of Revenue | Python Loading, SQL Loading |
| Boulder County Voter Registration | Boulder County Clerk and Recorder | Python Cleaning |
| Lahman Baseball Database | Sean Lahman | Python Extending, Python Reshaping |
| Colorado Population Estimates (DOLA) | Colorado State Demography Office | Python Extending, Python Reshaping, SQL Cleaning, SQL Reshaping |
| CDC Mortality Data | CDC WONDER | SQL Cleaning, SQL Reshaping |
| CBI Crime Statistics | Colorado Bureau of Investigation | SQL Cleaning, SQL Reshaping |
| Boulder County Assessor — Buildings | Boulder County Assessor | SQL Extending |

## Building the Book

### Prerequisites

Install [Quarto](https://quarto.org/docs/get-started/) (version 1.4 or later) and a Python environment with the required packages.

```bash
# Create and activate a conda environment
conda create -n info3401 python=3.11
conda activate info3401

# Install required Python packages
pip install pandas numpy matplotlib seaborn scipy jupyter
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

Output is written to the `book/` directory. Open `book/index.html` in a browser to view it.

To preview a single chapter with live reload:

```bash
quarto preview ch-py-loading.qmd
```

To render to a specific format:

```bash
quarto render --to pdf        # PDF via LaTeX (requires a LaTeX distribution)
quarto render --to docx       # Word document
```

### Notes on Code Execution

The `_quarto.yml` file sets `eval: false` globally, which means code blocks are displayed but not executed during the render. This is intentional: the datasets are not included in the repository, and running the code requires them to be present in the working directory.

To execute code blocks interactively, open the `.qmd` files as Jupyter notebooks:

```bash
quarto convert ch-py-loading.qmd   # converts to .ipynb for Jupyter
```

## Repository Structure

```
Information-Exploration-Book/
├── _quarto.yml              # Book configuration and chapter ordering
├── index.qmd                # Preface
├── ch-terminal.qmd          # Part I: Foundations
├── ch-projects.qmd
├── ch-documentation.qmd
├── ch-environments.qmd
├── ch-errors.qmd
├── ch-research-questions.qmd
├── ch-public-interest.qmd
├── ch-py-loading.qmd        # Part II: Python
├── ch-py-cleaning.qmd
├── ch-py-extending.qmd
├── ch-py-reshaping.qmd
├── ch-sql-loading.qmd       # Part III: SQL
├── ch-sql-cleaning.qmd
├── ch-sql-extending.qmd
├── ch-sql-reshaping.qmd
├── ch-descriptive.qmd       # Part IV: Analysis
├── ch-visualization.qmd
├── ch-hypothesis-testing.qmd
├── appendix-datasets.qmd    # Appendices
├── appendix-llm-methods.qmd
├── book/                    # Rendered HTML output (generated; not committed)
└── data/                    # Course datasets (see appendix-datasets.qmd)
```

## Contributing

Contributions are welcome. Before opening a pull request, please read the following:

### Reporting Errors

If you find a technical error — incorrect code, a wrong description of pandas or SQL behavior, a broken exercise — please [open an issue](https://github.com/cuinfoscience/Information-Exploration-Book/issues) with:

1. The chapter file and section heading where the error appears
2. A description of the error
3. The correct information and, if available, a link to primary documentation

### Proposing Changes

For content changes beyond error corrections (new sections, reorganization, additional exercises), open an issue first to discuss the change before submitting a pull request. This avoids duplicated effort and ensures proposed additions fit the book's scope and pedagogical approach.

### Style Conventions

- Section anchors follow the pattern `{#sec-filename-sectionname}`, e.g., `{#sec-py-loading-checklist}`
- Cross-references use `@sec-` notation throughout
- Callout boxes use Quarto's built-in callout types: `.callout-note`, `.callout-tip`, `.callout-warning`, `.callout-important`
- Code blocks specify the language: ` ```{python} `, ` ```{sql} `, ` ```{bash} `
- Exercises are placed in collapsible `.callout-note collapse="true"` blocks with solutions nested inside

### Commit Message Format

Use a short imperative summary followed by a blank line and a more detailed explanation if needed:

```
fix: correct read_csv header parameter description in ch-py-loading

The header parameter uses zero-indexing, so header=2 selects the third
row, not the second. Updated the inline comment and prose explanation.
```

Common prefixes: `fix:` (bug/error), `feat:` (new content), `refactor:` (restructuring without content change), `docs:` (README, comments).

## License

The book content is copyright Brian C. Keegan, Ph.D. Code examples are available under the MIT License. See `LICENSE` for details.

## Acknowledgments

This book grew out of the INFO 3401: Information Exploration course at the University of Colorado Boulder. It reflects the contributions of many students whose questions, mistakes, and feedback shaped the material into its current form. See [Appendix B: AI Use Disclosure](appendix-llm-methods.qmd) for an account of the role of large language models in producing this text.
