# PixelPlanet - Multiplayer Pixel Canvas

A collaborative multiplayer pixel art canvas with user accounts, real-time collaboration, and persistent storage.

## 🚀 Features

- **Account System**: Register and login with username/password
- **Multiplayer Canvas**: Shared 512x512 pixel canvas
- **Real-time Collaboration**: See other players online
- **Personal Statistics**: Track your pixel count
- **Brush Mode**: Hold Shift + Drag to paint
- **Zoom & Pan**: Smooth navigation (0.25x - 32x zoom)
- **Grid Toggle**: Press G to show/hide grid
- **30 Color Palette**: Beautiful color selection
- **Keyboard Shortcuts**: 1-9 for quick colors, WASD for movement

## 📦 Deploying to GitHub Pages

### Quick Deploy

1. **Create a new repository** on GitHub
2. **Upload** the `pixelplanet_multiplayer.html` file
3. **Rename it to** `index.html`
4. Go to **Settings** → **Pages**
5. Select **main branch** as source
6. Click **Save**
7. Your site will be live at `https://yourusername.github.io/repository-name/`

### Alternative: Use gh-pages branch

```bash
# Clone your repo
git clone https://github.com/yourusername/your-repo.git
cd your-repo

# Add the file
mv pixelplanet_multiplayer.html index.html
git add index.html
git commit -m "Add PixelPlanet"
git push origin main

# Or create gh-pages branch
git checkout -b gh-pages
git push origin gh-pages
```

## ⚠️ Important Notes

### Storage Compatibility

This app is designed to work with Claude's storage API. When running on GitHub Pages (or any static host), it will automatically fall back to **localStorage** for demo purposes.

**Limitations of localStorage fallback:**
- ✅ Works for single-user testing
- ❌ NOT truly multiplayer (data only saved locally)
- ❌ Data lost when clearing browser cache
- ❌ Not shared between different browsers/devices

### Making it Truly Multiplayer

To enable real multiplayer on GitHub Pages, you'll need a backend. Here are your options:

#### Option 1: Firebase (Recommended for beginners)

```javascript
// Add to <head>
<script src="https://www.gstatic.com/firebasejs/9.0.0/firebase-app.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.0.0/firebase-database.js"></script>

// Replace storage API calls with Firebase
const database = firebase.database();

// Example: Save canvas
database.ref('canvas').set(canvasData);

// Example: Get online users
database.ref('online').on('value', (snapshot) => {
  const users = snapshot.val();
});
```

#### Option 2: Supabase (More features)

```javascript
// Add to <head>
<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

// Initialize
const supabase = createClient('YOUR_URL', 'YOUR_KEY');

// Example: Save pixel
await supabase.from('pixels').insert({ x, y, color, user });
```

#### Option 3: Your Own Backend

Create a simple API server:
- Node.js + Express + MongoDB
- Python + Flask + PostgreSQL
- Any backend framework you prefer

## 🎮 Controls

| Action | Control |
|--------|---------|
| Place Pixel | Click |
| Brush Mode | Shift + Drag |
| Pan Canvas | Drag (without Shift) |
| Zoom In/Out | Mouse Wheel |
| Quick Color | Keys 1-9 |
| Toggle Grid | G |
| Move View | WASD |

## 🎨 How to Use

1. **Open the site** in your browser
2. **Register** a new account (or login if you have one)
3. **Select a color** from the palette at the bottom
4. **Click** to place a pixel
5. **Hold Shift + Drag** to paint multiple pixels
6. **See other players** in the online list (top right)
7. **Track your progress** - pixel count is saved to your account

## 🛠️ Customization

You can easily customize the app by editing the HTML file:

### Change Canvas Size
```javascript
const CANVAS_SIZE = 512; // Change to 256, 1024, etc.
```

### Modify Colors
```javascript
const COLORS = [
    '#FFFFFF', '#E4E4E4', // Add or remove colors
];
```

### Adjust Zoom Limits
```javascript
const MIN_ZOOM = 0.25;
const MAX_ZOOM = 32;
```

## 📱 Mobile Support

The app includes full touch support:
- Tap to place pixel
- Drag to pan
- Pinch to zoom

## 🐛 Troubleshooting

### "Login failed" or "Registration failed"
- In localStorage mode, data persists only in your browser
- Clear your browser cache if you encounter issues

### Online players list shows only me
- This is expected when using localStorage fallback
- Implement a real backend for true multiplayer

### Canvas is not saving
- Check browser console for errors
- Ensure localStorage is enabled
- Consider implementing cloud storage

## 📄 License

Free to use and modify. No attribution required.

## 🤝 Contributing

Feel free to:
- Report bugs
- Suggest features
- Submit pull requests
- Share your awesome pixel art!

## 🌟 Credits

Built with vanilla JavaScript - no frameworks needed!

---

**Enjoy creating collaborative pixel art! 🎨**
