# Godot Virtual Joystick

<img src="addons/virtual_joystick/previews/CoverPreview.svg" width="100%">

A simple yet powerful virtual joystick for touchscreens in Godot, packed with useful options to enhance your game's mobile experience.

[![Godot Engine](https://img.shields.io/badge/Godot-4.2%2B-brightgreen)](https://godotengine.org)
[![GitHub](https://img.shields.io/badge/GitHub-Repo-blue)](https://github.com/MarcoFazioRandom/Virtual-Joystick-Godot)

## 🎮 Features

- Easy to integrate
- Customizable appearance
- Multiple joystick modes
- Input action support
- Visibility options

## 📸 Preview

<p align="center">
  <img src="addons/virtual_joystick/previews/ShowcasePreview.png" width="85%">
</p>

## 🚀 Quick Start

1. Add the joystick to your scene
2. Configure the options
3. Use the following script to get started:

```gdscript
extends Sprite2D

@export var speed : float = 100
@export var joystick_left : VirtualJoystick
@export var joystick_right : VirtualJoystick

var move_vector := Vector2.ZERO

func _process(delta: float) -> void:
    # Movement using Input functions:
    move_vector = Input.get_vector("ui_left", "ui_right", "ui_up", "ui_down")
    position += move_vector * speed * delta
    
    # Rotation:
    if joystick_right and joystick_right.is_pressed:
        rotation = joystick_right.output.angle()
```

## ⚙️ Options

| Option | Description |
|--------|-------------|
| Joystick Mode | Fixed, Dynamic, or Following |
| Dead Zone Size | Minimum distance for output |
| Clamp Zone Size | Maximum distance for output |
| Visibility Mode | Always, Touchscreen Only, or When Touched |
| Use Input Actions | Trigger input actions defined in Project Settings |

## 🛠 Setup Tips

1. Create a `CanvasLayer` node named "UI" for all UI elements
2. Add the Joystick scene as a child of the UI node
3. Enable "Editable Children" to customize joystick appearance
4. Refer to the example scene in the "Test" folder

## 📘 FAQ

### Multitouch Issues?

Ensure these settings in Project -> Project Settings -> General -> Input Devices:
- "Emulate Touch from Mouse" : ON
- "Emulate Mouse from Touch" : OFF

### Input.get_vector() Not Working?

⚠️ **Fixed in Godot 4.2.1**

For earlier versions, use this workaround:

```gdscript
input_vector := Vector2.ZERO
input_vector.x = Input.get_axis("ui_left", "ui_right")
input_vector.y = Input.get_axis("ui_up", "ui_down")
```

## 🤝 Contributing

Contributions are welcome! Feel free to submit issues or pull requests on the [GitHub repository](https://github.com/MarcoFazioRandom/Virtual-Joystick-Godot).

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Made with ❤️ for the Godot community
