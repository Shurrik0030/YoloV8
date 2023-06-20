# YoloV8
Use [YOLOv8](https://github.com/ultralytics/ultralytics) in your C# project, for object detection, pose estimation and more, in a simple and intuitive way, using [ONNX Runtime](https://github.com/microsoft/onnxruntime)

# Use

## Export from PyTorch

Run the following Python code to export the model to ONNX format:

```python
from ultralytics import YOLO 

# Load a model
model = YOLO('path/to/model')

# export the model to ONNX format
model.export(format='onnx', opset=15)
```

Note: Pay attention to specify `opset=15` because the ONNX Runtime currently only supports up to Opset 15.

## Use in ONNX-Runtime

```csharp
using var predictor = new YoloV8(model);

var detectionResult = predictor.Detect("path/to/image");

Console.WriteLine(detectionResult);
```

# Plotting

You can use the following code to predict and plot a image, and save to file:

```csharp
var image = "path/to/image";

using var predictor = new YoloV8("path/to/model");

var poseResult = predictor.Pose(image);

using var origin = Image.Load<Rgb24>(image);
using var ploted = PlottingUtilities.PlotImage(origin, result);

ploted.Save("./pose_demo.jpg")
```

## Examples:

#### Detection:
![detect_demo!](https://raw.githubusercontent.com/dme-compunet/YoloV8/main/assets/detect_demo.jpg)

#### Pose:
![pose_demo!](https://raw.githubusercontent.com/dme-compunet/YoloV8/main/assets/pose_demo.jpg)

# License

MIT License