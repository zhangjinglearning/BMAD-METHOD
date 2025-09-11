# Technical Preferences for WeChat Mini Game Development

This document outlines the recommended technical stack, patterns, and best practices for developing high-quality WeChat Mini Games. These are guidelines, not strict rules, and can be adapted based on project needs.

## 1. Programming Language

-   **Preference:** **TypeScript**
-   **Rationale:** For any project beyond a simple prototype, TypeScript is strongly preferred over plain JavaScript. Its static typing helps catch common errors during development, improves code readability, and makes refactoring safer. This leads to more maintainable and robust code, especially for larger teams.

## 2. Project Structure

A consistent project structure is crucial for maintainability. The following structure is recommended:

```
/
|-- /assets/          # All static assets
|   |-- /images/
|   |-- /audio/
|   |-- /fonts/
|-- /components/      # Reusable UI components
|-- /pages/           # All game pages/scenes
|-- /services/        # Modules for backend communication
|-- /utils/           # Utility functions (e.g., API wrappers, formatters)
|-- app.js            # App entry point
|-- app.json          # Global configuration
|-- app.wxss          # Global styles
|-- project.config.json # Developer tool configuration
```

## 3. State Management

-   **For Simple Games/Prototypes:** A simple global object or an event bus can be sufficient.
-   **For Complex Games:** For games with complex state, consider a lightweight state management library (e.g., `mobx-miniprogram` or a custom implementation of the Redux pattern). This helps to manage state in a predictable and centralized way. Avoid scattering state across multiple pages and components directly.

## 4. Rendering

-   **Preference:** **Native Canvas API**
-   **Rationale:** For most 2D casual and hyper-casual games, directly using the `wx.createCanvas()` API provides the best performance and lowest overhead. It gives you full control over the rendering loop.
-   **For Complex Graphics:** If the game requires more advanced features (e.g., complex animations, particle systems, 3D), consider using a game engine that can export to WeChat Mini Games, such as **Cocos Creator** or **LayaAir**.

## 5. WeChat API Usage

-   **Best Practice:** **Wrap API calls in utility functions.**
-   **Rationale:** Avoid calling `wx.` APIs directly in your page or component logic. Create a `utils/wx-api.js` module that wraps these calls. This makes the code cleaner, allows for easier mocking during testing, and provides a central place to handle common logic like error handling or loading indicators.
-   **Example (`utils/wx-api.js`):**
    ```javascript
    export const login = () => {
      return new Promise((resolve, reject) => {
        wx.login({
          success: res => resolve(res),
          fail: err => reject(err),
        });
      });
    };
    ```

## 6. Asset Management

-   **Optimization is Key:** Mini Games have a package size limit. All assets must be optimized.
    -   **Images:** Use tools like TinyPNG to compress PNGs and JPEGs. Use texture atlases (sprite sheets) to reduce the number of draw calls.
    -   **Audio:** Use compressed audio formats like MP3.
-   **Loading Strategy:** Use the **subpackaging** (`subpackages`) feature in `app.json` to load non-essential assets on demand, reducing the initial load time.

## 7. Backend Services

-   **Default Choice:** **WeChat Cloud Base (Tencent Cloud)**
-   **Rationale:** For most projects, WeChat Cloud Base is the preferred choice. It's deeply integrated with the Mini Game ecosystem, providing serverless functions, a cloud database, and file storage out-of-the-box. This significantly simplifies backend development.
-   **Alternative:** For complex backend requirements or existing infrastructure, a **custom backend** (e.g., Node.js) is a viable option.

## 8. Performance

-   **Object Pooling:** For frequently created and destroyed objects (like bullets or effects), use an object pool to reduce garbage collection overhead.
-   **Throttling Events:** For frequent events like touch moves, use `throttle` to limit how often the event handler is called.
-   **Offscreen Canvas:** For complex drawing operations, use an offscreen canvas to prepare graphics in the background and then transfer them to the main canvas.

## 9. Code Style and Linting

-   **Enforce Consistency:** Use **ESLint** and **Prettier** to maintain a consistent code style across the project. Configure them to run automatically on save and as a pre-commit hook. This reduces trivial comments in code reviews and improves readability.
