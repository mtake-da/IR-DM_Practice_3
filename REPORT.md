Report - Running the code (simple language)

What I did:
- Ran parts of `PA1-skeleton.ipynb` to load helpers.
- Ran a small Python snippet to read the `toy-data` folder and show file contents.

What I found:
- `toy-data` has three subfolders: `0`, `1`, `2`.
- I printed each file and its text. Example contents:
  - `toy-data/0/fine.txt`: "i'm fine , thank you"
  - `toy-data/0/hello.txt`: "hi hi\nhow are you ?"
  - `toy-data/1/bye.txt`: "good to see you , bye\nsee you later ?"
  - `toy-data/1/byebye.txt`: repeated "bye"
  - `toy-data/2/` contains files same as `0`.

Errors / issues:
- The notebook has cells that expect the full dataset `pa1-data/` which is not present here. Those cells raise `FileNotFoundError` if executed. I skipped those cells.
- There is a macOS `.DS_Store` file in `toy-data`; I skipped it while listing directories.

Files created by running the notebook:
- `submission/imports.py` (generated when running setup cells).

How to reproduce locally:
1. (Optional) Create and activate the Conda environment as described in `README.md`:

   conda env create -f environment.yml
   conda activate cs276-pa1

2. Start Jupyter and open the notebook, or run the notebook cells in order:

   jupyter notebook

3. To reproduce the quick read of `toy-data` from command line, run this Python snippet from the repo root:

   python - <<'PY'
   import os
   root = 'toy-data'
   for d in sorted(os.listdir(root)):
       full_d = os.path.join(root, d)
       if not os.path.isdir(full_d):
           continue
       for fname in sorted(os.listdir(full_d)):
           path = os.path.join(full_d, fname)
           with open(path) as f:
               print(path, ':', f.read().strip())
   PY
