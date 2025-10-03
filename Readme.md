# Augmented Reality Renderer

PyTorch3D-based augmented reality pipeline that renders a 3D cow mesh and composites it onto real images using camera pose estimation.

## Requirements

```bash
pytorch3d
opencv-python
numpy
matplotlib
```

## Setup

1. **Data Structure:**
```
project/
├── test-images/
│   ├── image_1.jpeg
│   ├── image_2.jpeg
│   └── ...
├── poses.json
└── notebook.ipynb
```

2. **Configure poses.json:**
```json
[
    {
        "image_file": "image_1.jpeg",
        "R_plane": [
            [0.951, -0.023, 0.308],
            [0.008, 0.999, 0.050],
            [-0.308, -0.045, 0.950]
        ],
        "T_plane": [[-2.088], [-3.820], [12.197]]
    }
]
```

## Usage

Run the Colab notebook which will:
1. Load poses from JSON
2. Compute camera transformations
3. Render 3D cow for each pose
4. Composite onto real images
5. Overlay coordinate axes

## Output

Grid visualization with 3 columns per image:
- **Real Image**: Original calibration pattern
- **Rendered Cow**: 3D mesh from computed viewpoint
- **Composite**: Cow overlaid on real image with axes

## Parameters

- `W, H = 256`: Render resolution
- `axis_len = 0.5`: World axes length
- `mask_threshold = 0.01`: Alpha compositing threshold
- `distance = r/3`: Camera distance scaling

## Notes

- Uses checkerboard patterns for pose calibration
- Binary mask compositing for solid (non-transparent) overlay
- Supports batch processing of multiple images