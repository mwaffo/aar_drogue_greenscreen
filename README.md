---

# Green Screen Data for Training a YOLO DNN Model for YP Detection in Maritime Environments

This repository provides datasets and configuration files essential for training a YOLO-based deep neural network (DNN) model tailored for detecting YPs in maritime settings. The dataset was collected using a 1/10 scale model YP689 in a controlled laboratory environment, designed to closely replicate real-world data. Industry-standard chroma key techniques were applied, with lessons from prior USNA studies enhancing dataset realism for effective model training.

## Folder Structure

- **`train/`**: Contains synthetic training images with a small-scale YP model placed in front of a green screen backdrop, simulating various orientations and lighting conditions. Augmentation techniques—such as rotation, scaling, and brightness adjustments—were applied to enhance model robustness by increasing image diversity.
- **`valid/`**: Includes validation images created similarly to the training data, ensuring consistent performance tracking during model training.
- **`test/`**: Houses real-world images of the full-scale YP, captured from video files in natural maritime settings. These images serve as a benchmark for evaluating model performance under actual deployment conditions.
- **`data.yaml`**: A configuration file that defines paths to the train, validation, and test sets, and specifies information on class labels and the total number of classes.

## Usage

1. Ensure that the `train/`, `valid/`, and `test/` folders are in the repository’s root directory.
2. Update `data.yaml` with the correct paths to these folders:
   ```yaml
   train: /path/to/train
   val: /path/to/valid
   test: /path/to/test
   nc: <number_of_classes>
   names: ['YPXXX', ...]
   ```
3. Use `data.yaml` to configure your YOLO model (e.g., YOLOv5, YOLOv8).

## Example Command for Training

For YOLOv5, initiate training with:
```bash
python train.py --img 416--batch 16 --epochs 50 --data data.yaml --weights yolov5s.pt
```
This command will train the model using the data paths specified in `data.yaml`.

## Data Collection and Preparation Details

- **Synthetic Training Data**: The dataset was generated with industry-standard chroma key techniques, featuring a green screen backdrop that allowed effective separation of the background and foreground. The model YP was photographed in multiple orientations to replicate various viewing angles. Separate lighting minimized shadows and reflections, maintaining uniform subject illumination for optimal post-processing.
- **Testing Data**: Extracted from video recordings, real-world images showcase the full-scale YP in maritime conditions, providing realistic data for model evaluation after training.

## Notes

- Each image in `train/`, `valid/`, and `test/` must have a corresponding annotation file in YOLO format.
- Modify `nc` (number of classes) and `names` in `data.yaml` according to the detection task specifics.

## License

MIT, Apache 2.0, etc.

---
