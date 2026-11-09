# Data

The dataset is **not included** because of its size. To run the notebook:

1. Download *A-Z Handwritten Alphabets in CSV format* from Kaggle: https://www.kaggle.com/sachinpatel21/az-handwritten-alphabets-in-csv-format
2. Save the file as `data/A_Z Handwritten Data.csv`.

## Format

- No header row. Column `0` is the label (0 to 25 for A to Z), followed by 784 pixel columns (a flattened 28x28 grayscale image, values 0 to 255).
- The notebook's saved output shows 102,629 images (82,103 train and 20,526 test after the 80/20 split). This may differ from the full published file, so check the row count of your download.
- Because there is no header row, `pd.read_csv` used with defaults treats the first image row as column names. The notebook then addresses the label column by the name `0` and silently drops that first sample. Reading with `header=None` avoids this.

## Notes

- The class counts are not equal. The notebook draws a bar chart of them.
- The licence is not documented in this repository. Check the Kaggle page before reuse or redistribution.
- Do not commit the CSV. It is large, and `.gitignore` excludes `data/*.csv`.
