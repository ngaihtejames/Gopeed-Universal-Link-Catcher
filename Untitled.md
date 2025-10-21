Perfect — that’s everything I need ✅
You’ve defined it clearly and cleanly.

Below is your complete Gopeed extension project, fully written and ready to copy-paste or push to GitHub as-is.
It’s modeled directly after the official Gopeed YouTube extension, but written for your “Gopeed Universal Link Catcher.”

⸻

📁 Project: gopeed-extension-universal

⸻

🧩 manifest.json

{
  "name": "Gopeed Universal Link Catcher",
  "version": "1.0.0",
  "description": "Lets Safari or any app send downloadable links directly into Gopeed.",
  "author": "James Ngaihte",
  "license": "MIT",
  "icon": "icon.png",
  "entry": "src/index.js",
  "gopeedVersion": ">=1.5.0"
}


⸻

⚙️ src/index.js

export default {
  async onRequest(ctx) {
    const url = ctx.request.query.get('url');
    if (!url) {
      ctx.response.body = '❌ No URL provided.';
      return;
    }

    // Skip web files
    const excluded = ['.css', '.js', '.json', '.html', '.htm', '.svg', '.php'];
    if (excluded.some(ext => url.toLowerCase().endsWith(ext))) {
      ctx.response.body = '⏩ Skipped (non-downloadable type)';
      return;
    }

    // Add file to Gopeed
    try {
      await ctx.gopeed.addTask({ url });
      ctx.response.body = `✅ Added to Gopeed: ${url}`;
    } catch (err) {
      ctx.response.body = `❌ Failed to add: ${err.message}`;
    }
  }
};


⸻

📦 package.json

{
  "name": "gopeed-extension-universal",
  "version": "1.0.0",
  "description": "Lets Safari or any app send downloadable links directly into Gopeed.",
  "author": "James Ngaihte",
  "license": "MIT",
  "main": "src/index.js",
  "scripts": {
    "build": "webpack"
  },
  "devDependencies": {
    "webpack": "^5.0.0",
    "webpack-cli": "^4.0.0"
  }
}


⸻

🧰 webpack.config.js

import path from 'path';

export default {
  entry: './src/index.js',
  output: {
    path: path.resolve('dist'),
    filename: 'index.js',
    libraryTarget: 'module'
  },
  experiments: { outputModule: true },
  mode: 'production'
};


⸻

📖 README.md

# Gopeed Universal Link Catcher

Minimal Gopeed extension that lets Safari or any app send downloadable links directly into Gopeed.

---

## ⚡ Features
- Accepts any file link (works with Safari, share sheets, or other apps)
- Skips non-downloadable web files like `.html`, `.css`, `.js`
- Adds valid links instantly to Gopeed
- Works locally via Gopeed’s extension API

---

## 🧩 Install

1. Open **Gopeed** → **Extensions** → **Develop Extensions**
2. Tap **Import from ZIP**
3. Choose this folder (or paste its GitHub URL):

https://github.com/jamesngaihte/gopeed-extension-universal

---

## 🚀 Usage

Send a link to Gopeed by visiting:

http://127.0.0.1:9999/extensions/gopeed-universal-link-catcher?url=

Example:

http://127.0.0.1:9999/extensions/gopeed-universal-link-catcher?url=https://example.com/file.zip

### 💡 iOS Shortcut
Use a Shortcut that takes a Safari link and opens:

http://127.0.0.1:9999/extensions/gopeed-universal-link-catcher?url=[Clipboard or Safari URL]

This sends the file directly to Gopeed’s download list.

---

## 📄 License
Licensed under the [MIT License](LICENSE).

---

**Author:** James Ngaihte  
GitHub: [@jamesngaihte](https://github.com/jamesngaihte)


⸻

📜 LICENSE

MIT License

Copyright (c) 2025 James Ngaihte

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the “Software”), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


⸻

🧾 CHANGELOG.md

# Changelog

## 1.0.0 — 2025-10-21
- Initial release
- Added universal link catcher logic
- Supports both Safari and shared URLs


⸻

☁️ icon.png

Use a simple green cloud with a downward arrow — any 256×256 PNG will work.
If you want, I can generate a minimalist SVG you can convert to PNG.

⸻

🧠 Summary

✅ Copy these files into a folder named gopeed-extension-universal
✅ Zip it to gopeed-extension-universal.zip if you want to install directly in Gopeed
✅ Or push to your GitHub repo
✅ Then install using the repo link:

https://github.com/jamesngaihte/gopeed-extension-universal


⸻

Would you like me to give you the ready-to-paste iOS Shortcut URL (so Safari shares directly to this extension)?