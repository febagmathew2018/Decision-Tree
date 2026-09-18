# Churn Lab — a decision tree notebook

An interactive single-page app that mimics a Jupyter Notebook to teach how a decision tree predicts customer churn. Twelve numbered cells, each with runnable output, a collapsible backend explanation, and a listen button that reads the explanation aloud.

No build step, no dependencies, no server. One HTML file.

## Run it

Open `index.html` in a browser. That's it.

Or serve it locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Publish it with GitHub Pages

1. Push `index.html` to the repository root on the `main` branch.
2. Go to **Settings → Pages**.
3. Under **Source**, pick **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Save. The site appears at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

## What's inside

The page ships a real CART implementation in JavaScript — gini impurity, greedy threshold search, `min_samples_leaf` pruning, and gini-based feature importances — running over 240 seeded synthetic telecom customers. Every number on the page comes from that model, so the cells stay consistent with each other.

| Cell | What it does |
|------|--------------|
| 1 | Imports and the fixed random seed |
| 2 | Loads the dataset, paginated table |
| 3 | Column types, missing values, `describe()` |
| 4 | Churn rate by segment, switchable feature |
| 5 | Label encoding, before/after toggle |
| 6 | Stratified train/test split with an adjustable `test_size` |
| 7 | Gini impurity and information gain, threshold slider |
| 8 | Fits the tree; `max_depth` and `min_samples_leaf` controls |
| 9 | Clickable SVG tree diagram |
| 10 | Confusion matrix, decision threshold dial, per-quadrant customers |
| 11 | Feature importance bars |
| 12 | Live prediction with the full decision path |

Cells run like a kernel: running cell 9 executes 1–8 as dependencies first, and changing the split or depth refreshes every downstream cell that has already run.

## Browser support

The read-aloud buttons use the Web Speech API (`speechSynthesis`), available in current Chrome, Edge, Safari, and Firefox. Where it isn't, the button says so and everything else still works.

## Editing

Each cell is one object in the `CELLS` array near the bottom of the file: `code` is the Python shown, `explain` is the backend write-up (also the audio script), and `render(out)` draws the interactive output. Add a cell by appending an object with the next `n`.

## License

MIT
