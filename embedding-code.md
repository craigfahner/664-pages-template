# Code Examples

[← Back to home](README.md)

## Running a Whole Notebook in the Browser (JupyterLite)

This site includes [JupyterLite](https://jupyterlite.readthedocs.io/), a version of Jupyter that runs entirely in the web browser. Visitors can open, edit, and run your notebook without installing Python, Anaconda, or Jupyter. The Python code runs on *their* computer, inside the browser, using [Pyodide](https://pyodide.org/) (Python compiled to WebAssembly).

**[Open the example notebook →](notebook/notebooks/index.html?path=week10.ipynb)**

Or try it right here:

<iframe src="notebook/notebooks/index.html?path=week10.ipynb" width="100%" height="600" style="border: 1px solid #ccc;"></iframe>

*(The embedded notebook only appears on the published site, not when viewing this file on GitHub.com.)*

### How It's Set Up

Three pieces make this work:

1. **The `notebook/` folder.** Everything in it (notebooks, `.csv` files, images) gets copied into JupyterLite and appears in its file browser. Your notebook can open data files with normal relative paths, like `pd.read_csv("senate_average_recent.csv")`.
2. **The build workflow** in `.github/workflows/pages.yml`. Each time you push, a GitHub Action builds the Markdown pages with Jekyll, then runs `jupyter lite build` on the `notebook/` folder and publishes the result at `/notebook/` on your site.
3. **The Pages setting.** In **Settings → Pages**, **Source** must be set to **GitHub Actions** (not "Deploy from a branch"), so GitHub publishes what the workflow built.

### Adding Your Own Notebook

1. Put your `.ipynb` file, and any data files it reads, in the `notebook/` folder.
2. Link to it from any page. Replace `YOUR-NOTEBOOK.ipynb` with your file's name:

   ```markdown
   [Open my notebook](notebook/notebooks/index.html?path=YOUR-NOTEBOOK.ipynb)
   ```

   To embed it in a page instead, paste this HTML into your Markdown file:

   ```html
   <iframe src="notebook/notebooks/index.html?path=YOUR-NOTEBOOK.ipynb" width="100%" height="600"></iframe>
   ```

3. Commit and push, then watch the **Actions** tab until the build finishes.

There are two interfaces to choose from:

| URL | Opens |
| --- | --- |
| `notebook/notebooks/index.html?path=FILE.ipynb` | One notebook, in the simple Jupyter Notebook view |
| `notebook/lab/index.html?path=FILE.ipynb` | The full JupyterLab interface, with a file browser |

### Installing Packages

Many common packages are built into Pyodide and load automatically when you `import` them, including `pandas`, `numpy`, `matplotlib`, and `wordcloud`. Other pure-Python packages from PyPI can be installed with `%pip`. Add a cell like this at the top of your notebook:

```python
# Running in the browser (JupyterLite)? Install the packages that aren't
# built into Pyodide first. On a regular Jupyter install this cell does nothing.
import sys

if "pyodide" in sys.modules:
    %pip install plotly nbformat pydeck
```

Because of the `if` check, the same notebook still works in regular Jupyter on your own computer. Plotly charts also need `nbformat` installed, as shown above.

### Things to Know

- **The first load is slow.** The browser has to download Python and its packages (tens of megabytes) the first time. After that it's cached.
- **Changes are saved in the visitor's browser only.** If a visitor edits your notebook, their changes stay in their own browser storage. They never change the files in your repo. To get back to the original, they can clear the site's data in their browser.
- **Not every package works.** Packages that need compiled code (C, Rust, etc.) only work if Pyodide has built them. Check the [list of Pyodide packages](https://pyodide.org/en/stable/usage/packages-in-pyodide.html). Packages that use the network, threads, or your computer's hardware (webcams, GPUs, etc.) may not work at all.
- **Loading data from other websites may be blocked.** Browsers only let pages load data from other sites that allow it. Putting your data files in the `notebook/` folder is the most reliable option.

---

Previous: [← About the Project](about.md)
