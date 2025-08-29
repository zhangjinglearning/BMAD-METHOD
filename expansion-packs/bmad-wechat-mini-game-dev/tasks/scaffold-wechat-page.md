# Task: Scaffold New WeChat Mini-Game Page

**ID:** `scaffold-wechat-page`
**Name:** Scaffold WeChat Page
**Description:** Creates the standard four files (`.wxml`, `.wxss`, `.js`, `.json`) for a new WeChat mini-game page with basic boilerplate content.

---

### Instructions

You are the `@dev` agent. Your task is to scaffold a new page for a WeChat Mini-Game.

1.  **Get Page Name:**
    - Ask the user for the name of the new page (e.g., `index`, `profile`, `level-select`).
    - The path will be `pages/{{page_name}}/`.

2.  **Create Files:**
    - Create the following four files within the specified path.

    ---
    **File: `pages/{{page_name}}/index.js`**
    ```javascript
    // pages/{{page_name}}/index.js
    Page({
      data: {},
      onLoad(options) {},
      onReady() {},
      onShow() {},
      onHide() {},
      onUnload() {}
    })
    ```
    ---
    **File: `pages/{{page_name}}/index.wxml`**
    ```html
    <!--pages/{{page_name}}/index.wxml-->
    <view class="container">
      <text>This is the {{page_name}} page.</text>
    </view>
    ```
    ---
    **File: `pages/{{page_name}}/index.wxss`**
    ```css
    /**pages/{{page_name}}/index.wxss**/
    .container {
      height: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      padding: 200rpx 0;
      box-sizing: border-box;
    }
    ```
    ---
    **File: `pages/{{page_name}}/index.json`**
    ```json
    {
      "usingComponents": {}
    }
    ```
    ---

3.  **Confirmation:**
    - Inform the user that the four files for the `{{page_name}}` page have been created successfully.
