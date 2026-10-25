# 🎓 Web Development Assignment Portal

> Create web development assignments with an **automatic live preview** and **ready-to-copy source code**, all in a single HTML file. No backend, no build step, no dependencies.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen)
![Build](https://img.shields.io/badge/build%20step-none-blue)
![License](https://img.shields.io/badge/license-MIT-green)

---

## 📖 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [How It Works](#-how-it-works)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
- [Usage Guide](#-usage-guide)
- [Project Structure](#-project-structure)
- [Security Notes](#-security-notes)
- [Browser Support](#-browser-support)
- [Deploy with GitHub Pages](#-deploy-with-github-pages)
- [Customization](#-customization)
- [Known Limitations](#-known-limitations)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)
- [Author](#-author)

---

## 📌 About the Project

The **Web Development Assignment Portal** is a lightweight, browser-based tool for teachers, tutors, and course creators who want to share HTML, CSS, and JavaScript practice assignments with students.

Instead of manually preparing a preview page and formatting code snippets for every assignment, you simply:

1. Enter a title and instructions.
2. Paste or upload your HTML, CSS, and JavaScript.
3. Click **Generate Assignment**.

The portal instantly produces:

- A formatted assignment heading with instructions
- A **live output preview** of the working result
- Separate, **copy-ready code blocks** for `index.html`, `style.css`, and `script.js`

Everything runs entirely in the browser. There is no server, no database, and no installation.

---

## ✨ Features

| Feature | Description |
| --- | --- |
| 📝 **Assignment Builder** | Add a title and detailed instructions for students |
| 📂 **File Upload** | Load `.html`, `.htm`, `.css`, `.js`, or `.txt` files straight into the editors |
| ✍️ **Manual Code Entry** | Write or paste HTML, CSS, and JavaScript in dedicated monospace editors |
| ⚡ **Live Preview** | Instantly renders the combined code in an isolated, sandboxed iframe |
| 💻 **Source Code Viewer** | Displays HTML, CSS, and JS in separate dark-themed code boxes |
| 📋 **One-Click Copy** | Copy any code section with a single button, with a clipboard fallback for restricted browsers |
| 🧹 **Clear Form** | Reset the entire editor and hide the generated output (with confirmation) |
| ✅ **Input Validation** | Requires a title and at least one code section before generating |
| 📱 **Responsive Design** | Works on desktops, tablets, and phones |
| ♿ **Accessible Status Messages** | Uses `aria-live` so status updates are announced to screen readers |
| 🚫 **Zero Dependencies** | Pure HTML, CSS, and vanilla JavaScript |

---

## ⚙️ How It Works

```
┌──────────────────────┐
│  Teacher enters      │
│  title, instructions │
│  + HTML / CSS / JS   │
└──────────┬───────────┘
           │  Click "Generate Assignment"
           ▼
┌──────────────────────┐
│  Input validation    │
│  (title + code)      │
└──────────┬───────────┘
           ▼
┌──────────────────────────────────────────────┐
│  1. Show title + description                 │
│  2. Print HTML / CSS / JS in code boxes      │
│  3. Combine code into one HTML document      │
│  4. Inject it into a sandboxed iframe        │
└──────────┬───────────────────────────────────┘
           ▼
┌──────────────────────┐
│  Students view the   │
│  live output and     │
│  copy the source     │
└──────────────────────┘
```

**Under the hood:**

- Uploaded files are read with the browser's `File.text()` API and placed into the matching editor.
- On generation, the CSS is wrapped in a `<style>` tag, the HTML goes in the `<body>`, and the JavaScript is placed in a `<script>` tag. Any closing `</script` sequence inside the JS is escaped so it cannot break the preview document.
- The final document is assigned to the iframe's `srcdoc` attribute, so nothing is written to disk or sent over the network.
- Code is inserted into the code boxes using `textContent`, so it is displayed as plain text and is never executed or parsed as HTML on the portal page itself.

---

## 🛠 Tech Stack

- **HTML5**: semantic structure (`header`, `main`, `section`)
- **CSS3**: Flexbox, CSS Grid, media queries, no frameworks
- **Vanilla JavaScript (ES6+)**: async/await, template literals, Clipboard API, `srcdoc` iframes

---

## 🚀 Getting Started

### Prerequisites

Only a modern web browser. Nothing else to install.

### Option 1: Open directly

```bash
# Clone the repository
git clone https://github.com/brijeshsingh16/webdev-assignment-portal.git

# Move into the project folder
cd webdev-assignment-portal
```

Then double-click `index.html`, or open it from your browser with **File → Open File**.

### Option 2: Run a local server (optional)

```bash
# Using Python 3
python -m http.server 8000

# Or using Node.js
npx serve .
```

Visit `http://localhost:8000` in your browser.

---

## 🧭 Usage Guide

### 1. Create an assignment

1. Enter an **Assignment Title** (required), for example: `Student Registration Form`.
2. Write the **Assignment Instructions** describing the task and requirements. If left blank, the portal displays *"Complete this practical assignment."*

### 2. Add code

You can either:

- **Upload** an HTML, CSS, or JavaScript file using the matching upload box, or
- **Type / paste** code directly into the HTML, CSS, and JavaScript editors.

You can also upload a file and then edit it in the editor before generating.

> At least one of the three code sections must contain code.

### 3. Generate

Click **Generate Assignment**. The page scrolls to the result, which includes:

- The assignment title and instructions
- **Live Output**: a 400px preview frame
- **Source Code for Students**: HTML, CSS, and JavaScript, each with a copy button

### 4. Share with students

Students can copy each section into `index.html`, `style.css`, and `script.js` in their own project folder and practice from there.

### 5. Start over

Click **Clear Form** and confirm to reset all fields, uploads, the preview, and the generated output.

### Example

**HTML**
```html
<h1>Hello, Student!</h1>
<button id="btn">Click me</button>
<p id="msg"></p>
```

**CSS**
```css
body { font-family: Arial, sans-serif; text-align: center; }
button { padding: 10px 18px; }
```

**JavaScript**
```javascript
document.getElementById("btn").addEventListener("click", () => {
  document.getElementById("msg").textContent = "You clicked the button!";
});
```

---

## 📁 Project Structure

```
webdev-assignment-portal/
├── index.html     # The entire application (markup, styles, and logic)
└── README.md      # Project documentation
```

The whole portal lives in one self-contained `index.html`, so it is easy to host, share, and learn from.

### Key code sections in `index.html`

| Section | Purpose |
| --- | --- |
| `<style>` | All styling, including the responsive layout and the dark code boxes |
| `Create a New Assignment` card | Title, instructions, file uploads, and code editors |
| `#assignment` section | Hidden until an assignment is generated |
| `loadFile()` | Reads an uploaded file into its editor |
| `generateAssignment()` | Validates input, renders the output, and builds the preview document |
| `[data-copy]` handlers | Copy buttons with a fallback for blocked clipboard access |
| `#clearBtn` handler | Confirms and resets everything |

---

## 🔒 Security Notes

- The live preview runs inside an iframe with `sandbox="allow-scripts"`. Scripts can run, but the preview has an opaque origin, so it cannot access the portal page's DOM, cookies, or storage.
- Forms, popups, top-level navigation, and same-origin access are **not** enabled in the sandbox.
- Source code is displayed with `textContent`, preventing injection into the portal page.
- Because the portal executes whatever JavaScript you provide, only preview code you trust, particularly if you adapt this project to accept code from other people.

---

## 🌐 Browser Support

Works in current versions of:

- Google Chrome
- Microsoft Edge
- Mozilla Firefox
- Safari

The Clipboard API requires a secure context (`https://` or `localhost`). When it is unavailable, the portal automatically falls back to `document.execCommand("copy")`.

---

## 📡 Deploy with GitHub Pages

1. Push the project to your GitHub repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select the `main` branch and the `/ (root)` folder, then click **Save**.
5. After a minute or two, your site will be live at:

```
https://brijeshsingh16.github.io/webdev-assignment-portal/
```

---

## 🎨 Customization

All styling is at the top of `index.html`. Some quick tweaks:

| Change | Where |
| --- | --- |
| Header color | `header { background: #312e81; }` |
| Accent / button color | `button { background: #4f46e5; }` |
| Heading color | `h2 { color: #4338ca; }` |
| Preview height | `#previewFrame { height: 400px; }` |
| Code box theme | `pre { background: #0f172a; color: #e2e8f0; }` |
| Default description text | `description \|\| "Complete this practical assignment."` in `generateAssignment()` |

---

## ⚠️ Known Limitations

- Assignments are **not saved**. Refreshing the page clears everything.
- The preview is limited to a single HTML page with one CSS and one JS file.
- External resources (CDN links, fonts, images) depend on the sandboxed preview's network access and may behave differently from a normal page.
- There are no user accounts, so there is no separate teacher or student login.

---

## 🗺 Roadmap

- [ ] Save and load assignments (`localStorage`)
- [ ] Export an assignment as a ZIP (`index.html`, `style.css`, `script.js`)
- [ ] Shareable assignment links
- [ ] Syntax highlighting for the code boxes
- [ ] Dark mode toggle
- [ ] Multiple pages or assets per assignment
- [ ] Download buttons for each code file
- [ ] Assignment templates

Contributions toward any of these are welcome.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. **Fork** the repository
2. Create a feature branch
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. Commit your changes
   ```bash
   git commit -m "Add: your feature description"
   ```
4. Push to your branch
   ```bash
   git push origin feature/your-feature-name
   ```
5. Open a **Pull Request**

Please keep the project dependency-free and the code readable for beginners.

---

## 📄 License

This project is licensed under the **MIT License**. Add a `LICENSE` file to the repository root to make it official. You can create one from GitHub with **Add file → Create new file → `LICENSE`** and choosing the MIT template.

---

## 👤 Author

**Brijesh Singh**

- GitHub: [@brijeshsingh16](https://github.com/brijeshsingh16)
- Repository: [webdev-assignment-portal](https://github.com/brijeshsingh16/webdev-assignment-portal)

---

<p align="center">
  If you found this project useful, please consider giving it a ⭐ on GitHub!
</p>
