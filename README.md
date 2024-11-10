# YOLO Segmentation Annotation Visualizer

A Python tool for visualizing YOLO format segmentation / bounding box annotations. This tool helps in validating and visualizing segmentation masks from YOLO formatted datasets, making it easier to verify annotations and debug segmentation models.

## Features

- Visualize single image segmentation annotations
- Batch visualization of multiple images
- Support for YOLO format segmentation labels
- Automatic class color assignment
- Class label overlay on segments
- Configurable transparency and visualization parameters
- Automatic label file detection
- Selective image visualization from a list

## Prerequisites

```bash
pip install -r requirements.txt
```

Required packages:
- OpenCV (cv2)
- NumPy
- Matplotlib
- PyYAML
- Pillow

## Installation

Clone the repository:
```bash
git clone https://github.com/SakibAhmedShuva/YOLO-Segmentation-Annotation-Visualizer.git
cd YOLO-Segmentation-Annotation-Visualizer
```

### Dataset Structure

Your dataset should ideally be organized as follows:
```
dataset/
├── data.yaml
├── images/
│   ├── image1.jpg
│   ├── image2.jpg
│   └── ...
└── labels/
    ├── image1.txt
    ├── image2.txt
    └── ...
```
You can manually define the paths, so no worries.

### YAML Configuration

The `data.yaml` file should contain class names in the following format:
```yaml
names:
  0: class1
  1: class2
  ...
```

## API Reference

### YOLOSegmentationVisualizer

#### `__init__(yaml_path)`
Initialize the visualizer with path to YAML config file.

#### `visualize_single_image(image_path, label_path=None)`
Visualize a single image with its segmentation mask.
- `image_path`: Path to the image file
- `label_path`: Path to the label file. If None, attempts to find the corresponding label file

#### `visualize_batch(images_dir, labels_dir, num_images=5)`
Visualize multiple images with their segmentation masks.
- `images_dir`: Directory containing images
- `labels_dir`: Directory containing label files
- `num_images`: Number of images to visualize (default: 5)

### Example Scripts

#### Visualize Selected Images
```python
if __name__ == "__main__":
    # Initialize visualizer
    yaml_path = 'path/to/data.yaml'
    visualizer = YOLOSegmentationVisualizer(yaml_path)
    
    # Define list of images to visualize
    selected_images = [
        "12Volt_041.jpg",
        "2008_Dodge_Challenger_27.jpg",
        "2011_BMW_5-Series_68.jpg",
        "2011_BMW_5-Series_69.jpg",
    ]

    # Loop through each image to visualize
    for img_name in selected_images:
        image_path = f'path/to/images/{img_name}'
        label_path = f'path/to/labels/{img_name.split(".")[0]}.txt'
        visualizer.visualize_single_image(image_path, label_path)
```

## Example Output

The visualizer will display images with:
- Colored overlay for each segmented region
- Class labels at the centroid of each segment
- Semi-transparent fill for better visibility
- Different colors for different classes

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- YOLO project for the annotation format
- OpenCV and Matplotlib for visualization capabilities
