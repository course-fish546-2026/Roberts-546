# notebooks/

One Quarto document per week: `week00.qmd`, `week01.qmd`, … `week09.qmd`. Each one is that week's deliverable.

## The two files that come with the template

| File | What it is | What to do with it |
|---|---|---|
| `_template.qmd` | Blank starting point with the five required sections and a pre-push checklist | **Don't edit it.** Copy it each week. The leading `_` tells Quarto not to render it. |
| `week00.qmd` | Your Week 0 entry, partly filled in as an example | Fill in the blanks (`___`, `<your name>`, `<paste … here>`), render in RStudio Desktop, and push. |

## Starting a new week

Open your repository as an R Project first (**File → Open Project…** → `fish546.Rproj`; see the [R Projects guide](https://sr320.github.io/course-fish546-2026/r-projects.html)). Then, in the RStudio **Terminal** tab, from the top of your repository (replace `03` with the week number):

```bash
cp notebooks/_template.qmd notebooks/week03.qmd
```

Then open `notebooks/week03.qmd` and:

1. Change the `title:` to the week number and topic, and put your name in `author:`.
2. Fill in all five sections. Write "none" in a section instead of deleting it.
3. Click **Render**. This creates `week03.html` next to the `.qmd`.
4. Commit **both** `week03.qmd` and `week03.html`, then push.
5. Post the commit link on your Project Proposal issue.

## File paths inside a notebook

Code in a notebook runs with `notebooks/` as the working directory, so reach the rest of the repository with `../`:

```r
read.csv("../data/processed/counts.csv")
ggsave("../output/week03/volcano.png")
```

Save tables and figures under `output/weekNN/`, not in `notebooks/`.

Full instructions and the rubric: [How We Work](https://sr320.github.io/course-fish546-2026/how-we-work.html).
