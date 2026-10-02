# Extension Tracker notebooks

Notebooks for exploring the open data of [Extension Tracker](https://extensiontracker.com), a public
record of the extensions in the Chrome Web Store: their users, ratings, versions, permissions and
changes over time. They run in Google Colab, Kaggle or Jupyter and read the weekly data files
straight from `data.extensiontracker.com`, so there's nothing to download first.

| Notebook | What it covers | Open it in |
|----------|----------------|------------|
| [Getting started](01-getting-started.ipynb) | What's in a weekly set of files; the extensions with the most users, categories, ratings and publication years | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/WebIterate-Dev/extension-tracker-notebooks/blob/main/01-getting-started.ipynb) [![Open in Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://github.com/WebIterate-Dev/extension-tracker-notebooks/blob/main/01-getting-started.ipynb) |
| [Permissions](02-permissions.ipynb) | The most requested permissions, Manifest V2 and V3, and the extensions that can read and change data on every website | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/WebIterate-Dev/extension-tracker-notebooks/blob/main/02-permissions.ipynb) [![Open in Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://github.com/WebIterate-Dev/extension-tracker-notebooks/blob/main/02-permissions.ipynb) |
| [Changes and removals](03-changes-and-removals.ipynb) | The change log: removals, new extensions, new versions, added permissions and Enhanced Safe Browsing | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/WebIterate-Dev/extension-tracker-notebooks/blob/main/03-changes-and-removals.ipynb) [![Open in Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://github.com/WebIterate-Dev/extension-tracker-notebooks/blob/main/03-changes-and-removals.ipynb) |

GitHub shows each notebook with the results of its last run, so you can read them without running
anything.

## The data

Every Sunday, Extension Tracker publishes a set of files named for that day, at
`https://data.extensiontracker.com/YYYY-MM-DD/`:

- `extensions-YYYY-MM-DD.parquet`: one row for every extension, including removed ones;
- `history-YYYY-MM-DD.parquet`: the users and rating recorded at every check;
- `changes-YYYY-MM-DD.parquet`: every change, one row per changed field;
- CSV copies, a file for themes and apps, coverage figures, and `SCHEMA.md`, which explains every
  file and column.

[`index.json`](https://data.extensiontracker.com/index.json) lists every set, and
[`latest.json`](https://data.extensiontracker.com/latest.json) describes the newest. How the data is
collected is explained in the [methodology](https://extensiontracker.com/methodology).

The notebooks read one dated set, so they give the same results every time they run: published sets
never change and stay online. To use another set, change `SET` at the top of a notebook. The first
notebook shows how to read the newest one.

## Running them

**In Colab or Kaggle,** use the buttons above. Both already have pandas, pyarrow and matplotlib.
On Kaggle, a notebook needs internet access to read the files: if a cell can't connect, turn on
Internet in the notebook's settings, which Kaggle allows once your account has a verified phone
number.

**In Jupyter,** with Python 3.10 or later:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

On a Mac with Python from python.org, if reading a file fails with `CERTIFICATE_VERIFY_FAILED`, run
`Install Certificates.command` from that Python's folder in Applications.

## License and credit

The code here is under the [MIT license](LICENSE). The data is under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/): if you use it, credit Extension Tracker and
link to https://extensiontracker.com. Names, summaries and other text written by developers belong to
them.

Extension Tracker is run by [Web Iterate](https://webiterate.dev/). It isn't affiliated with Google.
