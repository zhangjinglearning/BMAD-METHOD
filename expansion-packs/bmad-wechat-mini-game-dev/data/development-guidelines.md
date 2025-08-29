# WeChat Mini Game Development Guidelines

This document provides the core technical preferences, coding standards, and anti-patterns for developing WeChat Mini Games with this expansion pack. Agents will reference this document to ensure consistency and quality.

---

## 1. Technical Preferences

### Framework
- **WeChat Mini Game Base Library:** v2.25.3 or higher
- **State Management:** `mobx-miniprogram-bindings` is preferred for complex state.
- **UI Component Library:** `WeUI` is approved for use.

### API Conventions
- All backend requests must use the `wx.request` API wrapper provided in `utils/request.js`.
- **Authentication:** Tokens must be passed in the header as 'X-Auth-Token'.
- **Base API URL:** `https://api.yourgame.com/v1`

---

## 2. Coding Standards

### File and Directory Structure
- All pages must be located in the `/pages` directory.
- All reusable components must be located in the `/components` directory.
- Utility functions should be placed in `/utils`.
- Each page or component must consist of four files: `.js`, `.wxml`, `.wxss`, and `.json`.

### JavaScript (`.js`)
- Always use strict mode (`'use strict';`).
- Use `const` for variables that are not reassigned, and `let` for variables that are. Avoid `var`.
- All asynchronous operations must return a Promise. Use `async/await` for cleaner code.
- Keep business logic out of the Page/Component lifecycle methods. Create separate helper methods.
- Use `this.setData()` for all UI updates. Avoid direct manipulation of `this.data`.

### WXML (`.wxml`)
- Use `wx:if` and `wx:else` for conditional rendering. Use the `hidden` attribute for simple show/hide toggles.
- Use `wx:for` for list rendering. Always specify a `wx:key` for performance.
- Bind events using `bind:tap` or `catch:tap`. Use `catch` to prevent event bubbling when necessary.

### WXSS (`.wxss`)
- Use `rpx` (responsive pixels) for sizing and positioning to ensure adaptability across different screen sizes.
- Define common styles in a global stylesheet (`/app.wxss`) and import them into component styles where needed.
- Keep styles scoped to their component to avoid conflicts.

---

## 3. Anti-Patterns to Avoid
- Do not use `wx.getStorageSync()` for large or frequently changing data. Use it only for static configuration or user preferences.
- Avoid using `setTimeout` for UI updates; use `this.setData()` callbacks or `wx.nextTick`.
- Do not place business logic inside `.wxml` files using `wxs`. Keep logic in the `.js` file.
