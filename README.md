# LDNN – Weekly Neural Network Notebooks

Jupyter notebooks for each week of the course, plus the datasets they use in the `data/` folder.
Each code block has short comments explaining what it does.

| Week | Notebook | Topic | Data file used |
|------|----------|-------|----------------|
| 1  | `Week_1_(weight_and_bias_value_effects_the_value_of_neurons).ipynb` | Two-layer network forward pass with sigmoid | – |
| 2  | `Week_2_(purelin(n)).ipynb` | Linear (`purelin`) activation | – |
| 3  | `Week_3_(tansig(n)).ipynb` | Tan-sigmoid (`tansig`) activation | – |
| 4  | `Week_4_(logsig(n)).ipynb` | Log-sigmoid (`logsig`) activation | – |
| 5  | `Week_5_(perceptron_lineraly_separable_problems).ipynb` | Perceptron on AND (linearly separable) | – |
| 6  | `Week_6_(perceptron_non_linearly_separable_problems).ipynb` | Perceptron on XOR (not linearly separable) | – |
| 7  | `Week_7_(graph_with_multiple_curve).ipynb` | CNN on CIFAR-10 with training/validation accuracy curves | – |
| 8  | `Week_8_(spyder_IDE).ipynb` | LSTM classifier for heart disease | `data/heart_week8.csv` |
| 9  | `Week_9_(installing_keras_tf_pytorch).ipynb` | CNN steps on an image: convolution, ReLU, pooling, flatten, dense | `data/face_week9.jpg` |
| 9  | `Week_9_short_version.ipynb` | Drawing a face bounding box with OpenCV/Matplotlib | `data/face_week9.jpg` |
| 10 | `Week_10_(IMDB_LSTM_GRU).ipynb` | IMDB dataset exploration and sentiment class distribution | `data/archive_week10.zip` (IMDB dataset) |
| 10 | `Week_10_short_version.ipynb` | IMDB sentiment classification with an LSTM | `data/archive_week10.zip` (IMDB dataset) |
| 11 | `Week_11_(autoencoder_algorithms).ipynb` | Dense autoencoder on MNIST | – |
| 12 | `Week_12_(GAN_image_generation).ipynb` | GAN generating MNIST digits (with batch norm, saves sample grids) | – |
| 12 | `Week_12_short_version.ipynb` | Minimal GAN on MNIST | – |

### Requirements

Python 3 with `numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`,
`tensorflow` and `opencv-python`. All of these are preinstalled in Google Colab.

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
     `https://colab.research.google.com/github/renaissance0ne/LDNN/blob/master/<notebook-name>.ipynb`
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
   !wget -q -O data/heart_week8.csv https://raw.githubusercontent.com/renaissance0ne/LDNN/master/data/heart_week8.csv
   # Week 9
   !wget -q -O data/face_week9.jpg https://raw.githubusercontent.com/renaissance0ne/LDNN/master/data/face_week9.jpg
   # Week 10
   !wget -q -O data/archive_week10.zip https://github.com/renaissance0ne/LDNN/raw/master/data/archive_week10.zip
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
