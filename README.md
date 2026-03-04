# URDF-SDF Converter

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![ROS 2 Compatible](https://img.shields.io/badge/ROS2-compatible-green.svg)](https://ros.org/)

A powerful Python package for bidirectional conversion between URDF (Unified Robot Description Format) and SDF (Simulation Description Format) files. This tool is essential for robotics developers working with Gazebo simulation and ROS 2.

## 🚀 Features

- **Bidirectional Conversion**: Convert URDF ↔ SDF formats seamlessly
- **Validation**: Check converted files for errors and compatibility issues
- **Visualization**: Generate tree diagrams of robot structure
- **Batch Processing**: Convert multiple robot models efficiently
- **Physics Preservation**: Maintain mass, inertia, friction, and collision properties
- **Sensor Compatibility**: Preserve sensor configurations during conversion
- **Gazebo Extensions**: Handle Gazebo-specific tags and plugins
- **ROS 2 Integration**: Compatible with ROS 2 robot descriptions

## 📦 Installation

```bash
pip install urdf-sdf-converter
```

Or install from source:

```bash
git clone https://github.com/strangerwhoisharborofdoom/urdf-sdf-converter.git
cd urdf-sdf-converter
pip install -e .
```

## 🔧 Usage

### Convert URDF to SDF

```python
from urdf_sdf_converter import URDFToSDFConverter

converter = URDFToSDFConverter()
converter.convert_file('robot.urdf', 'robot.sdf')
```

### Convert SDF to URDF

```python
from urdf_sdf_converter import SDFToURDFConverter

converter = SDFToURDFConverter()
converter.convert_file('robot.sdf', 'robot.urdf')
```

### Command Line Interface

```bash
# URDF to SDF
urdf2sdf robot.urdf robot.sdf

# SDF to URDF
sdf2urdf robot.sdf robot.urdf

# Batch conversion
urdf2sdf-batch ./urdfs/ ./sdfs/

# Validate converted file
validate-sdf robot.sdf --verbose
```

### Validation

```python
from urdf_sdf_converter import SDFValidator

validator = SDFValidator()
errors, warnings = validator.validate('robot.sdf')

if errors:
    print(f"Found {len(errors)} errors:")
    for error in errors:
        print(f"  - {error}")
```

## 📁 Project Structure

```
urdf-sdf-converter/
├── urdf_sdf_converter/     # Main package
│   ├── __init__.py
│   ├── urdf_to_sdf.py      # URDF → SDF conversion logic
│   ├── sdf_to_urdf.py      # SDF → URDF conversion logic
│   ├── validator.py        # File validation utilities
│   ├── visualizer.py       # Robot structure visualization
│   └── cli.py              # Command-line interface
├── examples/               # Example robot models
│   ├── rrbot.urdf
│   ├── gripper.sdf
│   └── mobile_base.urdf
├── tests/                  # Unit tests
│   ├── test_conversion.py
│   ├── test_validation.py
│   └── test_cli.py
├── docs/                   # Documentation
│   ├── installation.md
│   ├── api_reference.md
│   └── troubleshooting.md
├── setup.py
├── requirements.txt
├── README.md
└── LICENSE
```

## 🔬 Technical Details

### Supported URDF Elements
- Links and joints
- Collision geometries (box, sphere, cylinder, mesh)
- Visual geometries and materials
- Inertial properties (mass, COM, inertia matrix)
- Sensors (IMU, LiDAR, camera, depth)
- Actuators and transmissions
- Gazebo-specific tags

### Supported SDF Elements
- Models and links
- Joints (revolute, prismatic, continuous, fixed)
- Collision and visual elements
- Physics properties (friction, restitution)
- Sensors and plugins
- Nested models
- World files

### Conversion Limitations
- Some Gazebo plugins may not have URDF equivalents
- SDF nested models are flattened in URDF
- Custom SDF plugins require manual mapping

## 🧪 Testing

```bash
# Run all tests
pytest tests/

# Run with coverage
pytest tests/ --cov=urdf_sdf_converter

# Test specific conversion
pytest tests/test_urdf_to_sdf.py -v
```

## 📝 Examples

See the `examples/` directory for sample robot models:

- **RRBot**: Simple 2-link robotic arm
- **Gripper**: Parallel jaw gripper with collision geometries
- **Mobile Base**: Differential drive robot with sensors

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guidelines](CONTRIBUTING.md) first.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Open Robotics](https://www.openrobotics.org/) for SDF and Gazebo
- [ROS community](https://www.ros.org/) for URDF specification
- Contributors and testers

## 📧 Contact

- **Author**: Pavan C N
- **GitHub**: [@strangerwhoisharborofdoom](https://github.com/strangerwhoisharborofdoom)
- **Issues**: [Report bugs or request features](https://github.com/strangerwhoisharborofdoom/urdf-sdf-converter/issues)

## 🗺️ Roadmap

### Version 0.1.0 (Current)
- ✅ Basic URDF ↔ SDF conversion
- ✅ Validation for common errors
- ✅ CLI tools
- ✅ Example robot models

### Version 0.2.0 (Planned)
- ⏳ Support for SDF 1.9 features
- ⏳ Enhanced visualization (3D preview)
- ⏳ Batch processing improvements
- ⏳ ROS 2 launch file generation

### Version 0.3.0 (Future)
- ⏳ Web-based converter interface
- ⏳ Automatic mesh optimization
- ⏳ Integration with Gazebo simulator
- ⏳ Python API documentation
