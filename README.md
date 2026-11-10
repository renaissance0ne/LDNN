# LDNN – Weekly Neural Network Notebooks

Jupyter notebooks for each week of the course, plus the datasets they use in the `data/` folder.

| Week | Notebook | Data file used |
|------|----------|----------------|
| 1  | `Week_1_(weight_and_bias_value_effects_the_value_of_neurons).ipynb` | – |
| 2  | `Week_2_(purelin(n)).ipynb` | – |
| 3  | `Week_3_(tansig(n)).ipynb` | – |
| 4  | `Week_4_(logsig(n)).ipynb` | – |
| 5  | `Week_5_(perceptron_lineraly_separable_problems).ipynb` | – |
| 6  | `Week_6_(perceptron_non_linearly_separable_problems).ipynb` | – |
| 7  | `Week_7_(graph_with_multiple_curve).ipynb` | – |
| 8  | `Week_8_(spyder_IDE).ipynb` | `data/heart_week8.csv` |
| 9  | `Week_9_(installing_keras_tf_pytorch).ipynb` | `data/face_week9.jpg` |
| 10 | `Week_10_(IMDB_LSTM_GRU).ipynb` | `data/archive_week10.zip` (IMDB dataset) |
| 11 | `Week_11_(autoencoder_algorithms).ipynb` | – |
| 12 | `Week_12_(GAN_image_generation).ipynb` | – |

---

## Running the notebooks in Google Colab

The notebooks load their data with relative paths such as `data/heart_week8.csv`.
Opening a notebook in Colab only copies the notebook itself, **not** the `data/`
folder, so you need to bring the data into the Colab runtime as well. Pick one
of the options below.

### Option 1 – Clone the whole repo inside Colab (recommended)

This gives you every notebook and the full `data/` folder, and the relative
paths in the notebooks work without changes.

1. Go to <https://colab.research.google.com> and create a new notebook
   (or open any of the notebooks as described in Option 2).
2. Run this in the first cell:

   ```python
   !git clone https://github.com/renaissance0ne/LDNN.git
   %cd LDNN
   !ls data
   ```

   You should see `archive_week10.zip`, `face_week9.jpg` and `heart_week8.csv`.
3. Open a notebook from the cloned repo: in the left sidebar click the
   **Files** (folder) icon, open the `LDNN` folder and double-click the
   `.ipynb` file you want. Alternatively, keep working in the current notebook –
   since you are now inside `LDNN/`, code like
   `pd.read_csv('data/heart_week8.csv')` will work directly.

### Option 2 – Open a notebook straight from GitHub, then fetch the data

1. Open the notebook in Colab, either by:
   - In Colab, **File → Open notebook → GitHub** tab, paste
     `https://github.com/renaissance0ne/LDNN`, and pick the notebook; or
   - Using a direct link of the form
     `https://colab.research.google.com/github/renaissance0ne/LDNN/blob/main/<notebook-name>.ipynb`
     (spaces/brackets in the file name are fine; copy the name from GitHub).
2. Add and run a cell **at the top** of the notebook to pull in the data folder:

   ```python
   !git clone https://github.com/renaissance0ne/LDNN.git repo
   !cp -r repo/data .
   !ls data
   ```

   Or download only the file that week needs:

   ```python
   !mkdir -p data
   # Week 8
   !wget -q -O data/heart_week8.csv https://raw.githubusercontent.com/renaissance0ne/LDNN/main/data/heart_week8.csv
   # Week 9
   !wget -q -O data/face_week9.jpg https://raw.githubusercontent.com/renaissance0ne/LDNN/main/data/face_week9.jpg
   # Week 10
   !wget -q -O data/archive_week10.zip https://github.com/renaissance0ne/LDNN/raw/main/data/archive_week10.zip
   ```

3. Run the rest of the notebook as normal.

> Saving: notebooks opened from GitHub are temporary. Use
> **File → Save a copy in Drive** (or **File → Save a copy in GitHub**) to keep
> your changes.

### Option 3 – Upload the data manually

1. Download the files from the repo's `data/` folder on GitHub
   (open each file → **Download raw file**).
2. In Colab, run:

   ```python
   !mkdir -p data
   ```
3. Click the **Files** icon in the left sidebar, open the `data` folder, and
   drag the downloaded files into it (or use the **Upload** button).

Uploaded files are deleted when the Colab runtime resets, so you will need to
repeat this in a new session.

### Notes

- **Week 10:** `data/archive_week10.zip` is read directly by pandas
  (`pd.read_csv("data/archive_week10.zip")`), so you don't need to unzip it.
- **GPU:** Weeks 10–12 (LSTM/GRU, autoencoders, GANs) run much faster with a GPU:
  **Runtime → Change runtime type → T4 GPU**.
- **Restarting the runtime** keeps the current folder's files but a full
  *disconnect/delete runtime* wipes them – just re-run the clone cell.
