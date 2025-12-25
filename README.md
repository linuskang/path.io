# path.io

A simple location tracking web application that visualizes your path on a map in real-time.

## Features

- 🗺️ Interactive map powered by MapLibre GL JS
- 📍 Real-time location tracking using the browser's Geolocation API
- 🛣️ Draws a line on the map showing where you've been
- 🔄 Path resets when you refresh the page
- 📱 Mobile-friendly and responsive
- 🌍 Uses OpenStreetMap tiles

## How to Use

1. Open `index.html` in a web browser (or visit the [live demo](https://linuskang.github.io/path.io/))
2. Click "Allow" when prompted to share your location
3. Move around and watch as your path is drawn on the map
4. Refresh the page to reset the path and start tracking a new route

## Deployment

This is a static HTML file that can be deployed anywhere:

### GitHub Pages
1. Push the repository to GitHub
2. Go to Settings > Pages
3. Select the branch to deploy (e.g., `main`)
4. Your site will be available at `https://[username].github.io/path.io/`

### Local Development
Simply open `index.html` in a web browser or use any HTTP server:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000/`

## Technical Details

- **Map Library**: MapLibre GL JS v3.6.2
- **Tile Server**: OpenStreetMap public tile servers
- **Location API**: Browser Geolocation API with `watchPosition()`
- **Data Storage**: In-memory (resets on page refresh)

## Browser Requirements

- Modern browser with Geolocation API support
- HTTPS connection (required for location access, except on localhost)
- Location services enabled on the device

## Privacy

All location data is processed locally in your browser and is never sent to any server. The path is stored only in memory and is lost when you refresh the page.