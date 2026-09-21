# ERD Maker 📐

A fast, lightweight, and modern Entity-Relationship Diagram (ERD) editor that runs entirely in your browser with **zero dependencies**. Design database schemas visually, establish relationships with automatic cardinality lines, organize tables into domain groups, customize themes and colors, manage multiple saved diagrams locally, and export directly to SQL, high-resolution PNG, SVG, or JSON.

---

## ✨ Features

- **⚡ Zero Setup & Self-Contained**: Single-file web application (`erd-maker.html`). No build tools, Node servers, or external libraries required.
- **📁 Multi-Diagram Local Browser Storage**:
  - Save, manage, switch, duplicate, and rename multiple diagrams locally inside your browser's `localStorage` with zero cloud or backend dependencies.
  - **Live Auto-Save & Status Pill**: Continuously auto-saves every change with a real-time status indicator (`● Auto-saved` / `● Saving...`).
  - **Editable Diagram Title**: Rename your diagram directly from the toolbar.
  - **Saved Diagrams Library**: Search, view stats (tables, relationships, groups), duplicate, export, or delete diagrams from a modal manager.
  - **Starter Templates**: Instantly start with pre-built schema templates (**Blank Canvas**, **E-Commerce**, **Blog / CMS**, and **Social App**).
  - **Quick Save Shortcut**: Press <kbd>Ctrl+S</kbd> / <kbd>Cmd+S</kbd> anytime for instant save and toast notification.
- **🌓 White Background & Dark Mode Theming**:
  - One-click toggle between sleek dark mode and crisp white-background light mode.
  - Automatically adjusts canvas grid dots, table card contrasts, shadows, modal styling, and SVG relationship lines.
  - Theme preference is saved locally across sessions.
- **🎨 Custom Table & Group Colors**:
  - Click the swatch on any table or group header to pick from 12 modern palette presets or choose any custom hex color with the native color picker.
  - Table cards feature an accent top stripe matching their color for instant visual categorization.
- **📦 Group Tables (Domains & Bounded Contexts)**:
  - Add domain containers (`+ Group`) to organize related tables (e.g., Auth, Billing, Catalog).
  - **Synchronized Dragging**: Dragging a group header moves the container and all member tables inside together, dynamically updating relationship connectors.
  - Interactive resize handle at the bottom-right corner.
  - Delete or ungroup containers without removing member tables.
- **🔗 Smart Relationship Connectors**:
  - Drag connector ports from any field to another to establish foreign-key relationships.
  - Supports **1—1** (one-to-one), **1—N** (one-to-many), and **N—N** (many-to-many) cardinalities with standard crow's foot notation.
  - Automatic orthogonal elbow routing and side detection (left/right).
- **💾 Comprehensive Export & Import**:
  - **Export as Image (PNG)**: Renders a 2x high-resolution (Retina quality) image with diagram bounding box and active theme background.
  - **Export as SVG**: Generates clean, scalable vector graphics suitable for Figma, Illustrator, and documentation.
  - **Export as SQL**: Generates ANSI-compliant `CREATE TABLE` and `ALTER TABLE ... ADD CONSTRAINT FOREIGN KEY` DDL scripts.
  - **Export as JSON / Import JSON**: Losslessly save and reload diagrams into your local diagram library.
- **🔍 Canvas Navigation**:
  - Smooth pan and pinch/wheel zoom (30% to 220%).
  - **Fit to Screen**: Instantly centers and scales the entire diagram into view.

---

## 🚀 Quick Start

No installation or build steps are necessary:

1. Clone or download this repository:
   ```bash
   git clone https://github.com/your-username/erd-maker.git
   ```
2. Open [`erd-maker.html`](erd-maker.html) in any modern web browser (Chrome, Firefox, Edge, Safari):
   - Double-click the file, or
   - Drag and drop it into an open browser tab, or
   - Serve it via a local static server:
     ```bash
     npx serve .
     ```

---

## 🕹️ Controls & Shortcuts

| Action | Control |
| :--- | :--- |
| **Quick Save** | <kbd>Ctrl+S</kbd> / <kbd>Cmd+S</kbd> or click **💾 Save** |
| **Manage Diagrams** | Click **📁 Diagrams** in toolbar |
| **Rename Diagram** | Click & type in the toolbar title input or click **Rename** in Diagrams modal |
| **Add Table** | Click **+ Table** in the toolbar, or **Double-Click** empty canvas |
| **Add Group** | Click **+ Group** in toolbar (wraps selected table or creates in center) |
| **Pan Canvas** | Click & drag empty canvas or group background |
| **Zoom In / Out** | Scroll wheel, or use `+` / `−` zoom buttons in the toolbar |
| **Fit View** | Click **Fit** in the toolbar |
| **Connect Fields** | Click & drag a field's circular dot to another field's dot |
| **Change Cardinality** | Click any relationship line to open the popover (`1—1`, `1—N`, `N—N`, `Delete`) |
| **Change Color** | Click the circular swatch in any table or group header |
| **Move Group + Tables** | Click and drag the group's header bar |
| **Resize Group** | Drag the bottom-right corner handle of the group |
| **Delete Table / Group** | Select table or group and press <kbd>Delete</kbd> or <kbd>Backspace</kbd>, or click `✕` |
| **Close Modal / Popover** | Press <kbd>Escape</kbd> or click `✕` |
| **Toggle Theme** | Click the **☀️ Light / 🌙 Dark** button in the toolbar |

---

## 🛠️ Technology Stack

- **HTML5**: Semantic layout, SVG canvas, and standard Canvas 2D API for high-resolution rendering.
- **Vanilla CSS**: CSS Custom Properties (Variables), `color-mix`, CSS Grid, and Flexbox for modern responsive styling.
- **Vanilla JavaScript (ES6+)**: Zero framework overhead, fast DOM updates, pure client-side state machine, and analytic geometry calculations.
- **Storage Engine**: Native `localStorage` multi-document store with automatic legacy schema migration.
- **Typography**: Google Fonts (*Inter* for UI and *IBM Plex Mono* for schema code & fields).

---

## 📄 Schema Export Example

When exporting to SQL, ERD Maker automatically structures your tables, column constraints, primary keys, and foreign keys:

```sql
CREATE TABLE users (
  id UUID NOT NULL PRIMARY KEY,
  email VARCHAR(255) NOT NULL,
  created_at DATETIME
);

CREATE TABLE posts (
  id UUID NOT NULL PRIMARY KEY,
  user_id UUID NOT NULL,
  title VARCHAR(255) NOT NULL,
  body TEXT
);

ALTER TABLE posts ADD CONSTRAINT fk_posts_user_id FOREIGN KEY (user_id) REFERENCES users(id);
```

---

## 📝 License

MIT License. Free to use, modify, and distribute for personal and commercial projects.
