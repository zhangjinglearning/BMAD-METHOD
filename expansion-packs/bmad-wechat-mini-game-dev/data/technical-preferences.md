# WeChat Mini Game - Technical Preferences & Best Practices

This document contains user-defined preferences and critical best practices for Mini Game development, based on official documentation and performance guidelines.

---

## 1. Performance & Runtime

- **Target Framerate:** Casual games must maintain a minimum of **30 FPS** on low-end test devices. More intensive games should target **60 FPS** on mid-to-high-end devices.
- **WASM is Core:** All game logic should be compiled to WebAssembly (WASM) for maximum performance.
- **iOS JIT Mode:** For games requiring high performance, enabling the **iOS High Performance Mode** to allow JIT compilation is mandatory. Be aware this requires extra optimization for memory and startup time. For hyper-casual games, the default non-JIT mode is acceptable.

## 2. Rendering & Graphics (WebGL)

- **WebGL 2.0:** Where device support allows, **WebGL 2.0** should be enabled to leverage features like GPU Instancing and SRP Batching.
- **Texture Compression:** Use platform-specific compressed texture formats. **ASTC** is the required format for all textures on iOS to optimize memory usage.
- **Object Pooling:** Do not instantiate and destroy objects frequently in the game loop (e.g., bullets, effects). Implement an **object pooling** system to recycle and reuse game objects.

## 3. Asset & Memory Management

- **Sub-packaging (`分包`):** Large assets, levels, or non-critical resources **must** be placed in sub-packages to keep the initial download size small.
- **Memory Limits:** Be mindful of strict memory limits on mobile devices. Profile memory usage frequently using the WeChat DevTools.
- **Asset Loading:** Load assets asynchronously. Do not block the main thread during initial game load.

## 4. Anti-Patterns to Avoid

- **Ignoring iOS Non-JIT Mode:** Do not assume JIT compilation is available. Test performance on iOS devices in default mode.
- **Using Uncompressed Textures:** Avoid using large PNGs where a compressed format like ASTC (for iOS) or ETC2 (for Android) would be more memory-efficient.
- **Blocking the Main Thread:** Any long-running operation (e.g., complex calculations, large data processing) should be moved to a Worker thread if possible.
