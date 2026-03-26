## 📘 **Obsidian Incident Report Dashboard**

A clean, professional system for tracking community incidents inside Obsidian.  
Includes a beautiful dashboard, an easy-to-use submission form, and automatic status updates.

👉 **Download the latest version (ZIP)**  
https://github.com/GathusHQ/obsidian-incident-report-dashboard/releases

### ✨ Features
- Overview cards showing Open / In-Progress / Closed counts
- Monthly severity trends
- Live search + filters by severity and status
- Guided form that creates consistent, well-formatted reports
- Built-in status updater (no manual editing needed)
- Optional image upload support

---

### 📁 Folder Structure

```
Incident Reports/
    Images/                    ← All uploaded photos go here
Incident Report Dashboard.md   ← Main dashboard + form
README.md
uploadincidentimage.js         ← Required for the "Upload Incident Image" button
```

Just drop these files into the **root** of any Obsidian vault.

---

### 🎨 Theme and Appearance Settings to Match the Screenshots

These settings are optional, but they will make your vault look like the screenshots shown in this guide. They don’t affect functionality—only appearance and layout.

### Theme

The screenshots use the **Obsidianite** theme with these style presets:
**_Obsidianite — Dark Mode_**

The dashboard works with any theme; this is just the one used in the screenshots.

### Appearance Settings

These settings affect layout, spacing, and how clean the pages look:

- Appearance → Inline title → **Off**
- Editor → Readable line length → **Off**
- Editor → Properties in document → **Hidden**
- Core plugins → Page preview → **Off**

### Editor Behavior

These settings ensure the dashboards open in the correct mode:

- Editor → Default view for new tabs → **Reading view**
- Editor → Default editing mode → **Source mode**

These match the environment used to create the screenshots and help the dashboards display cleanly and consistently.

---

## Screenshots

### Main Dashboard
![Dashboard – Part 1](screenshots/Incident%20Reports%20Dashboard%201.png)
![Dashboard – Part 2](screenshots/Incident%20Reports%20Dashboard%202.png)
![Dashboard – Part 3](screenshots/Incident%20Reports%20Dashboard%203.png)
![Dashboard – Part 4](screenshots/Incident%20Reports%20Dashboard%204.png)
![Dashboard – Part 5](screenshots/Incident%20Reports%20Dashboard%205.png)
![Dashboard – Part 6](screenshots/Incident%20Reports%20Dashboard%206.png)

### Incident Report
![Report Page – Part 1](screenshots/Incident%20Report%20Page%201.png)
![Report Page – Part 2](screenshots/Incident%20Report%20Page%202.png)
![Report Page – Part 3](screenshots/Incident%20Report%20Page%203.png)
![Report Page – Part 4](screenshots/Incident%20Report%20Page%204.png)

---

### 🚀 Installation (2 minutes)

1. Unzip the download.
2. Copy the contents into the **root** of your Obsidian vault.
   - Make sure `uploadincidentimage.js` goes inside the `Incident Reports/` folder.
3. Install and enable the **Dataview** plugin:
   - Settings → Community plugins → Browse → “Dataview”
   - Enable **Dataview**
   - Go to Dataview settings → Turn on **Enable JavaScript Queries**
4. Open `Incident Report Dashboard.md` and you’re ready to go.

That’s it — no renaming, no extra configuration.
**Note:** You can skip copying the Readme.md if you’ve already read it or don’t need it in your vault.

---

### 🔌 Required Plugins

- **Dataview** (required) — powers the entire dashboard and form.
- **QuickAdd** (optional) — only needed if you want the “Upload Incident Image” button to work.

---

### 🛠️ How to Create the QuickAdd Choice (Optional – for Image Upload)

The system works perfectly without QuickAdd.  
If you want the image upload button to function, follow these steps exactly — QuickAdd’s UI can be confusing, and the choice type must be set at creation time.

#### Step 1 — Create the Macro Choice

1. Go to: **Settings → Community Plugins → QuickAdd → Manage Choices**
2. In the text box, type the name first:

```
Upload Incident Image
```

3. Click the **dropdown next to “Add Choice”** (this is the part most people miss)

   It looks like:

```
[ Template ▼ ]  Add Choice
```

4. From the dropdown, select **Macro**

5. Now click **Add Choice**

You have now created a **Macro choice**.

---

#### Step 2 — Add the User Script

1. Click the **gear icon** ⚙️ next to your new choice
2. Find where it says **User Scripts**
3. In the script field, type or select:

```
uploadincidentimage
```

(QuickAdd will show it in the suggester — it automatically finds `.js` files anywhere in your vault, including inside `Incident Reports/`.)

4. Save the Macro
5. Make sure to activate your QuickAdd choice by clicking the **lightning bolt** ⚡ next to the gear icon.

---

#### Get your QuickAdd Command ID (one-time step)

**Easiest method (Console):**
- Press `Ctrl+Shift+I` (Windows/Linux) or `Cmd+Option+I` (Mac)
- Go to **Console** tab
- Paste this and press Enter:
  ```js
  console.table(app.commands.listCommands().filter(c => c.id.includes('choice')))
  ```
- Find “Upload Incident Image” and copy the full ID (looks like `quickadd:choice:xxxxxxxx-xxxx-...`)
- Open `Incident Report Dashboard.md`, find the line with `executeCommandById`, and replace `YOUR-ID-HERE` with your ID. It will look like this:

```
btn.onclick = async () => {
  app.commands.executeCommandById("quickadd:choice:YOUR-ID-HERE");
};
```

The button will now work and will automatically hide after an image is uploaded.

---

### 📝 How to Create a New Incident Report

1. Open **Incident Report Dashboard.md**
2. Scroll down to the **Incident Report Form**
3. Fill in the fields and click **Submit Incident Report**
4. The new report is automatically created in the `Incident Reports/` folder

---

### 📊 Using the Dashboard

Open `Incident Report Dashboard.md` to:
- See current open/in-progress/closed counts
- View severity trends over the last 12 months
- Browse “Current Incidents at a Glance”
- Search and filter all reports
- Click any report to open it

The dashboard refreshes automatically when you add or update reports.

---

### 🛠️ Customizing the System

You can safely edit:
- Incident types and severity levels
- Form fields
- Dashboard layout
- The `Incident Reports/` folder name (update the constant in the code if you do)

Everything is plain Markdown + DataviewJS.

---

### 🔧 Troubleshooting

- **Dashboard empty?** → Make sure reports are in the `Incident Reports/` folder and DataviewJS is enabled.
- **Upload Incident Image button not working?** → Make sure `uploadincidentimage.js` is inside the `Incident Reports/` folder and you’ve correctly set the QuickAdd command ID.
- **Status updates not working?** → Try refreshing the note (`Ctrl+R`).

---

### 🎉 Enjoy!

This kit is designed to be simple yet powerful. Feel free to customize it however you like.
