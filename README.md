# Recognising Emotions from Faces with a CNN

Can a small convolutional network tell whether a face looks **happy, sad or afraid**? This project builds one from scratch, trains it on a few hundred photos per class, and looks honestly at how well it generalises.

## The data

Face images in three classes, **fear, happy and sad**: 1,396 images for training and 300 held out for validation, loaded with a directory-based image generator so the folder name is the label.

## The approach

A convolutional neural network (convolution and pooling layers followed by dense layers) is trained for 10 epochs with the Adam optimiser. Images are rescaled and fed through an image-data generator, and the final model is saved for reuse.

## What the results show

| | |
|---|---|
| Random guessing (3 classes) | 33 % |
| **Test accuracy** | **52 %** |

The model clearly learns *something*, well above the 33 % chance level, but it is far from reliable, and the test loss (≈ 3.1) is much higher than the training loss. That gap is the signature of **overfitting**: with under 1,500 training images, a network from scratch memorises the training faces instead of learning what a smile or a frown looks like.

## What you can take from this

1. Report accuracy next to the chance level. 52 % sounds poor until you know that guessing gets 33 %.
2. Facial expressions are subtle, and small datasets are not enough to learn them from scratch.
3. The standard remedies are the ones to try next: **data augmentation** (flips, small rotations and shifts), **transfer learning** from a network pre-trained on a large face or image dataset, and stronger **regularisation** (dropout, early stopping).

## Files

- `master.ipynb`: data loading, model, training, evaluation
- `data/`, `validation/`: the training and validation images, one folder per emotion
