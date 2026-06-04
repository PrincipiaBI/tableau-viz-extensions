# tableau-viz-extensions

Custom Tableau Dashboard Extensions for Principia, hosted on GitHub Pages.

**GitHub Pages URL:** `https://principiabi.github.io/tableau-viz-extensions/`

---

## Extensions

### Stoplight

A traffic light visual (green/yellow/red) driven by a `STATUS` column in your worksheet data.

| STATUS Value | Light | Label |
|---|---|---|
| 1 | Green | On Track |
| 2 | Yellow | At Risk |
| 3 | Red | Off Track |

**Files:** `stoplight/index.html`, `stoplight/config.html`, `stoplight/stoplight.trex`

---

## Setup & Deployment

### 1. Enable GitHub Pages

1. Go to **Settings > Pages** in this repository
2. Under "Source", select **Deploy from a branch**
3. Choose branch `main`, folder `/ (root)`
4. Click Save
5. Wait 1-2 minutes for the site to deploy

Your extensions will be available at:
`https://principiabi.github.io/tableau-viz-extensions/<extension-name>/index.html`

### 2. Add to Tableau Cloud Allowlist

Since extensions request full data access, a Tableau Cloud site admin must allowlist the domain:

1. Go to **Tableau Cloud > Settings > Extensions**
2. Under "Enable Specific Extensions", click **Add Extension**
3. Enter URL: `https://principiabi.github.io`
4. Set to **Allow** and check **Full Data Access**
5. Save

### 3. Add Extension to a Dashboard

1. Download the `.trex` file for the extension you want (e.g., `stoplight/stoplight.trex`)
2. In Tableau Desktop or Tableau Cloud web editing:
   - Drag an **Extension** object onto the dashboard
   - Choose "Access Local Extensions" (or "My Extensions")
   - Browse to and select the downloaded `.trex` file
3. The extension loads and prompts you to configure (pick a worksheet)
4. The extension reads the `STATUS` column from the selected worksheet's filtered data

### 4. How Filtering Works

The stoplight extension uses `getSummaryDataAsync()` which respects all worksheet filters. When you filter your dashboard to a specific KPI, only the filtered rows are visible to the extension. It reads the STATUS value from the first row of the filtered result.

---

## Adding New Extensions

Create a new subfolder (e.g., `gauge/`) with its own `index.html`, `config.html`, and `.trex` manifest. The `.trex` URL should point to:
```
https://principiabi.github.io/tableau-viz-extensions/<folder-name>/index.html
```

No changes to the GitHub Pages configuration are needed -- new folders are automatically served.
