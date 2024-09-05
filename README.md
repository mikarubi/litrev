## Pipeline for semi-automated analysis of network-neuroscience literature

### Requirements

- Jupyter Notebook running Python 3. <https://docs.jupyter.org/en/latest/install.html>
- Python packages and versions: python 3.11, notebook 6.5, ipywidgets 7.8, requests, html2text.
- Additional requirements for reproducing the full analysis:
  - Ability to download reference records from the _Web of Science_ website.
  - Ability to download full-text articles from individual journal websites.


### Setup via virtual environment
- The following commands establish a working virtual environment:

1. Using native Python (via `requirements.txt`):
```
cd /path/to/litrev
python3 -m venv litrev_env
source litrev_env/bin/activate
pip install -r requirements.txt
```
2. Using Anaconda (<https://anaconda.org/>):
```
conda create -n litrev_env python=3.11 notebook=6.5 ipywidgets=7.8 anaconda::requests conda-forge::html2text
conda activate litrev_env
```

### Summary

- _Step 1_: Environment set up and loading of previously analyzed data.
- _Step 2_: Specification of the full literature search query and instructions for manually downloading all reference records that match this query from the Web of Science.
- _Step 3_: Automated download of all full-text articles that match the specified search query.
- _Step 4_: Automated curation and cleaning of article text for all downloaded articles.
- _Step 5_: Automated extraction of relevant text segments and emphasis of potential keywords.
- _Step 6_: Automated scoring of the presence or absence of circular analyses based on manual evaluation of specified criteria.
- _Step 7_: Automated storage of collated evaluations and scores in a simple database and a summary table.


### Execution

- Launch the _Jupyter Notebook_ environment.
- Open the file `analysis.ipynb` file in the _Jupyter Notebook_ environment.
- Select the _Run All_ option from the _Cell_ menu.
- Scroll to _Step 6_ to interact with article text and evaluations:
  - All articles, except for _Article 1_, are sorted in pseudorandom order.
  - Use the _Previous article_ and _Next article_ buttons to navigate between articles.
  - Alternatively, enter the article number directly into the _Article_ field.
  - Adjust the viewing window height using the _Text-window height_ slider.
  - The _Methods and Results_ tab (default selection) shows curated article text:
    - All potential keywords in the article text are highlighted in pink.
    - All paragraphs that contain potential keywords are highlighted in yellow.
    - The article accession number and abstract are highlighted in gray.
  - The _Evaluation_ tab shows the scoring and evaluation for each article:
    - _Condition 1_ determines the suitability of the article for evaluation.
    - _Conditions 2–3_ determine the presence or absence of circular analyses.
    - _Condition 4_ evaluates the presence of circular analyses from _Conditions 1–3_.
- The collated evaluations and scores are stored in the ./results folder:
  - The file `./results/summary.csv` contains a summary table with article accession numbers and evaluations.
  - The file `./results/results.zip/records.json` contains the database of curated article data and evaluations.
  - All other files in `./results/results.zip` and in `./results/eqns` are images of article equations (used for displaying equations alongside article text).


