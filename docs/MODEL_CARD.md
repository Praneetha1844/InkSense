# Model card: InkSense

## Summary

A small convolutional neural network (Keras) that classifies a 28x28 grayscale image of a single handwritten capital letter into one of 26 classes (A to Z). It is a learning project, not a production recogniser.

## Intended use

- Studying a basic CNN on a standard handwriting dataset.
- A baseline for comparing other architectures.

**Not intended for:** reading real documents, forms or signatures, accessibility tools or any decision that affects people.

## Data

*A-Z Handwritten Alphabets in CSV format* (Kaggle). The notebook's saved output shows 102,629 images after loading and splitting, which may differ from the full published file. Not included here. See [data/README.md](../data/README.md). Licence not documented in this repository.

## Model

`Conv2D(32)`, `MaxPool`, `Conv2D(64, same)`, `MaxPool`, `Conv2D(128, valid)`, `MaxPool`, `Flatten`, `Dense(64)`, `Dense(128)`, `Dense(26, softmax)`; ReLU activations; Adam (learning rate 0.001); categorical cross-entropy; 1 epoch. Inputs are raw pixel values from 0 to 255.

## Results (from the saved notebook output)

| Run | Training accuracy | Validation accuracy | Validation loss |
|---|---|---|---|
| First training cell | 95.53% | 97.96% | `nan` |
| Second training cell | 95.71% | 98.06% | `nan` |

The validation loss is `nan` in both runs and the cause has not been confirmed. A likely factor is the unscaled 0-255 input, but this is a hypothesis. The notebook ends with unexecuted cells that check for non-finite values and re-train on scaled inputs with a fixed seed. No results are reported for them.

## Limitations and risks

- **Unreliable validation loss** (`nan`) means the reported validation accuracy should be treated with caution.
- **One epoch, no augmentation, no tuning.**
- **No separate test set.** The 20% held-out split is the validation data, and it is not seeded, so the saved numbers cannot be reproduced exactly.
- **Narrow input.** Single clean 28x28 capital letters. Not tested on lowercase letters, digits, words, other scripts or photographs.
- **No per-class analysis.** Visually similar letters (for example I and L, or O and Q) may be confused more, but this has not been measured.
- **Dataset provenance** and writer diversity are unknown, so performance on other handwriting styles is unknown.
- **Fairness:** if used on people's handwriting, accuracy may differ between writers or scripts. This has not been evaluated.

## Ways to improve

See the future-work list in the [README](../README.md).
