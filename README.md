# 📖 Biblia Sacra - Custom Bibles Repository

Welcome to the **Custom Bibles Repository** for the [Biblia Sacra](https://bibliasacra.web.app) app! 

To respect copyright laws, the core Biblia Sacra application only comes pre-loaded with public domain translations. However, the app features a **"Bring Your Own Bible" (BYOB)** engine. This allows you to connect the app to any securely hosted folder of JSON files to read your preferred modern translations (like the ESV, NIV, or NABRE) seamlessly within the app.

This repository serves two purposes:
1. **Ready-to-Use Samples:** Provides pre-formatted, ready-to-use links for popular translations.
2. **Developer Guide:** Shows you exactly how to format and host your own Custom Bibles.

---

## 🚀 Quick Start: Use a Pre-Hosted Bible

If you just want to add a translation we already have in this repository (like the ESV or NABRE), it only takes 10 seconds.

### Step 1: Copy a Base URL
Copy one of the following URLs to your clipboard:

*   **ESV (English Standard Version):**
    `https://exanx.github.io/bible-json/ESV-66-Books`
*   **NABRE (New American Bible Revised Edition):**
    `https://exanx.github.io/bible-json/NABRE-73-Books`

### Step 2: Add it to the App
1. Open the **Biblia Sacra** app and open the menu/sidebar.
2. Scroll down to the **Custom Bibles** section.
3. In the **Name** box, type a name (e.g., `ESV`).
4. In the **Base URL** box, paste the link you copied above.
5. Click **Add Custom Bible**.
6. Scroll back up to the **Translation** dropdown, select your new custom Bible, and start reading!

---

## 🛠️ How to Create & Host Your Own Custom Bible

Want to add a translation that isn't listed here? You can easily format and host your own!

### 1. Format the JSON Files
You need to create a folder containing an individual JSON file for each book of the Bible. 
* The filenames **must match standard book names exactly** (e.g., `Genesis.json`, `1 Corinthians.json`, `Song of Solomon.json`).
* Inside each file, the JSON structure must be organized by `"Chapter" -> "Verse" -> "Text"`.

**Example of `Genesis.json`:**
```json
{
  "1": {
    "1": "In the beginning God created the heavens and the earth.",
    "2": "The earth was without form, and void; and darkness was on the face of the deep...",
    "3": "God said, \"Let there be light,\" and there was light."
  },
  "2": {
    "1": "The heavens and the earth were finished, and all their vast array.",
    "2": "On the seventh day God finished his work which he had done..."
  }
}

Note on 66-book vs 73-book Bibles: Biblia Sacra defaults to the 73-book Catholic
canon. If you are uploading a Protestant translation (66 books), simply omit the
files for the Deuterocanonical books (like Tobit.json or 1 Maccabees.json). If
you click on one of these books in the app while reading a 66-book translation,
the app will gracefully tell you the book is not available in that version.

2. Host the Files on GitHub Pages (Free)

The app cannot read "raw" GitHub files reliably due to CORS (security) and
formatting restrictions. You must use GitHub Pages to serve the files properly.

1.  Create a Repository: Make a new, public GitHub repository (e.g.,
    my-custom-bibles).
2.  Upload Files: Upload your folder of JSON files into this repo (e.g., upload
    a folder named NIV).
3.  Turn on Pages:
      - Go to your repository's Settings tab.
      - Click Pages on the left sidebar.
      - Under Build and deployment, set the Source to Deploy from a branch.
      - Select your main or master branch and click Save.
4.  Get your Base URL: Wait ~2 minutes for GitHub to build your site. GitHub
    will provide a link like https://[YourUsername].github.io/my-custom-bibles/.
      - Add your folder name to the end of it.
      - Your final Base URL will look like this:
        https://[YourUsername].github.io/my-custom-bibles/NIV

(Ensure there is no trailing slash / at the very end of your Base URL!)

3. Connect to the App

Take your new GitHub Pages Base URL, paste it into the Custom Bibles section
inside the Biblia Sacra app, and you're good to go!

❓ Troubleshooting

  - "Loading..." gets stuck or shows an error in the app:
      - Make sure you are using a GitHub Pages link (.github.io), not a
        raw.githubusercontent.com or github.com link.
      - Ensure your Base URL does not end with a slash /.
      - Ensure your filenames perfectly match standard casing and spacing (e.g.,
        1 Samuel.json, not 1samuel.json or 1_Samuel.json).
  - Can I host files on my own private server?
      - Yes, but your server must be configured to allow CORS
        (Access-Control-Allow-Origin: *), otherwise the web browser will block
        Biblia Sacra from fetching your files. (This is why GitHub Pages is
        highly recommended—it handles CORS automatically).

