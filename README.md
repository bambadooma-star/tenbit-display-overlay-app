# 🎯 TenBit Display Overlay

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011-blue?style=for-the-badge&logo=windows" alt="Windows" />
  <img src="https://img.shields.io/badge/Architecture-x64-brightgreen?style=for-the-badge" alt="x64" />
  <img src="https://img.shields.io/badge/Color%20Depth-10--bit%20%2830--bit%20RGB%29-purple?style=for-the-badge" alt="10-bit" />
  <img src="https://img.shields.io/badge/DWM%20Engine-Direct3D%2011%20Flip-orange?style=for-the-badge" alt="D3D11" />
  <img src="https://img.shields.io/badge/Release-v1.0.0-emerald?style=for-the-badge" alt="v1.0.0" />
</p>

<p align="center">
  <strong>The Professional Real-Time Windows Desktop HUD for True 10-bit SDR & HDR Display Verification.</strong><br>
  Stop guessing if your color pipeline is truly delivering 1.07 billion colors. Verify your hardware, DWM swapchains, and active application content in real time.
</p>

---

## ⚡ The Problem: The "Fake 10-Bit" Illusion in Windows

Thousands of digital colorists, video editors, 3D artists, and photographers invest in high-end 10-bit SDR monitors or wide-gamut displays. 

However, in Windows:
- **DWM Windowed Composition** often silently downsamples buffers to 8-bit (`DXGI_FORMAT_B8G8R8A8_UNORM`) without any user warning.
- Media players and photo viewers frequently configure a 10-bit output swapchain (`rgb10_a2`), but feed it with **standard 8-bit JPEG or 8-bit SDR video**, creating a false sense of security.
- Web browsers display 4K streams at 8-bit sRGB while users assume they are receiving full 10-bit graduation.

**TenBit Display Overlay solves this permanently.** It is an ultra-lightweight, hardware-direct desktop HUD that continuously monitors the active foreground application and exposes both the **display presentation format** and the **underlying content bit depth**.

---

## ✨ Features

- 🔬 **Deep Swapchain Telemetry**  
  Directly inspects Win32 Direct3D 11, DirectX 12, and Vulkan swapchain presentation buffers in real time (`DXGI_FORMAT_R10G10B10A2_UNORM` vs `DXGI_FORMAT_B8G8R8A8_UNORM`).

- 🎯 **Deep In-Process Content Inspection**  
  Distinguishes between a player's swapchain and the actual file/stream color depth. Accurately flags 8-bit phone photos, 8-bit YouTube VP9 streams, 10-bit HEIF/ProRes, and 16-bit master images.

- 🖥️ **Hardware CCD Integration**  
  Directly queries the Windows Connecting and Configuring Displays (CCD) subsystem for exact `BitsPerColorChannel` (10 bpc / 30-bit total RGB), color encoding (`RGB 4:4:4`), and Advanced Color Management (ACM) states.

- 📌 **Enforced Absolute Z-Order (`HWND_TOPMOST`)**  
  Stays persistently visible above all fullscreen windows, games, and creative suites. Never gets hidden behind active workspaces.

- 🔒 **HUD Focus Lock Memory**  
  Clicking or dragging the HUD never overwrites your inspected status. It intelligently retains and locks onto the last active workspace application.

- 🧪 **Built-in Physical Banding Ramp Test**  
  Includes a one-click 16-bit Direct3D test pattern comparison tool to visually prove banding elimination on your physical panel.

---

## 📊 Technical Comparison

| Capability | Standard Windows Settings | GPU Control Panel | TenBit Display Overlay |
| :--- | :---: | :---: | :---: |
| **Physical Display BPC Query** | Basic / Hidden | Static Link Speed | **Real-Time CCD Query** |
| **Active App Swapchain Inspection** | ❌ No | ❌ No | **✅ Real-Time (D3D11 / DXGI)** |
| **Actual Media Bit Depth Detection** | ❌ No | ❌ No | **✅ In-Process Deep Probe** |
| **Silent 8-Bit DWM Downsampling Detection** | ❌ No | ❌ No | **✅ Instant Warning Badge** |
| **Always-On-Top Mini HUD Mode** | ❌ No | ❌ No | **✅ Included** |
| **Hardware AV1 / VP9 NVDEC Awareness** | ❌ No | ❌ No | **✅ Included** |

---

## 🚀 Quick Start (Portable Executable)

1. Download **`TenBitDisplayOverlay.exe`** from the [Latest Releases](https://github.com/bambadooma-star/tenbit-display-overlay-app/releases/latest).
2. Run the executable — no installer or administrative privileges required.
3. The sleek HUD will appear in the top-left of your desktop.
4. Click on any creative application (Photoshop, DaVinci Resolve, MPV, Chrome, Lightroom) to see its active color pipeline status instantly.

---

## 💻 System Requirements

- **Operating System**: Windows 10 (1903+) or Windows 11 (64-bit).
- **GPU**: NVIDIA GeForce / RTX, AMD Radeon, or Intel Arc with Direct3D 11 support.
- **Display**: Any display (optimal for 10-bit SDR or HDR panels over DisplayPort 1.4 or HDMI 2.0+).

---

## 🔒 Security & Code Integrity

This official release binary is built with bytecode protection and anti-tampering verification to guarantee binary authenticity and protect proprietary telemetry algorithms.

---

## 📄 License

Copyright © 2026. All rights reserved.  
Free for personal and non-commercial evaluation. For commercial licensing and SDK integration inquiries, contact the repository maintainers.
