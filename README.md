

---

# WikiFinder

A simple Vue app that lets users search any keyword and get relevant articles using the Wikipedia API.

## Features
- 🔍 Live search from Wikipedia
- 🧠 Supports any keyword (years, people, events, topics)
- 💡 Clean UI and dynamic results
- 🧠 HTML tags removed from content for clean display
- 🧪 Built with **Vue.js**, **HTML**, and **CSS**
- 💡 Clean and responsive UI with beautiful hover effects

---

### 📸 Demo

![screenshot](./screenshot.png) <!-- Optional: Add a real screenshot here -->

---

### 🛠️ Tech Stack

- **Vue.js 3**
- **HTML5**
- **CSS3**
- **Wikipedia REST API**

---

### 🔧 Setup Instructions

1. **Clone the repository:**
   ```bash
   git clone https://github.com/asdf2341/historical-events-finder.git
   cd historical-events-finder
   ```

2. **Install dependencies:**
   > Only needed if you're using Vue CLI setup  
   ```bash
   npm install
   ```

3. **Run the project:**
   ```bash
   npm run serve
   ```

4. **Or use in-browser development:**  
   If using Vue via CDN in a simple `index.html`, just open the file in your browser.

---

### 🧠 How It Works

- You enter a year (e.g., `2001`)
- The app fetches search results from Wikipedia’s API:
  ```
  https://en.wikipedia.org/w/api.php?action=query&list=search&srsearch=2001&format=json&origin=*
  ```
- The results (titles + descriptions) are displayed in a styled table
- HTML tags from the response are stripped using a small utility function

---

### ✨ Example

```js
async fetchEvents() {
  const res = await fetch(`https://en.wikipedia.org/w/api.php?action=query&list=search&srsearch=${this.years}&format=json&origin=*`);
  const data = await res.json();
  this.events = data.query.search;
}
```

---

### 📁 Folder Structure (if using Vue CLI)

```
src/
├── App.vue
├── main.js
└── assets/
```

---

### 🙌 Credits

- Wikipedia for the amazing open data
- Vue.js for the reactive framework
- Your brain 🧠 for learning and building!

---

### 📃 License

This project is open-source and free to use.

---

Would you like this exported as a real `.md` file or styled version for GitHub? Or want to host it?
