# Path.io - Demo Guide

## What This Application Does

Path.io is a real-time location tracking web application that:

1. **Requests Location Permission**: When you open the page, your browser will ask for permission to access your location
2. **Centers the Map**: Once permission is granted, the map centers on your current location
3. **Tracks Your Movement**: As you move around, the app continuously tracks your position
4. **Draws Your Path**: A blue line is drawn on the map showing everywhere you've been since opening the page
5. **Shows Your Location**: A blue marker indicates your current position on the map

## Key Features

### Location Tracking
- Uses the browser's Geolocation API with `watchPosition()` for continuous tracking
- High accuracy mode enabled for best results
- Updates in real-time as you move

### Path Visualization
- Blue line drawn using MapLibre GL JS
- Line width: 4 pixels with 80% opacity
- Round line joins and caps for smooth appearance
- Line persists as you move

### Map Display
- Uses OpenStreetMap tiles
- Interactive controls (zoom, rotate)
- Starts at zoom level 15 once location is acquired
- Attribution to OpenStreetMap contributors

### Status Information
- Shows number of points tracked
- Displays GPS accuracy (e.g., ±10m)
- Error messages if location access is denied or unavailable

### Data Persistence
- Path data stored in memory only
- **Resets on page refresh** (as required)
- No data sent to any server
- Completely client-side

## Example Usage Scenarios

### Walking/Running Tracker
1. Open the app on your phone
2. Start your walk or run
3. Watch your path draw on the map in real-time
4. See total distance and route visualization

### Bike Ride Logger
1. Mount phone on bike
2. Open app and grant location access
3. Your entire bike route is tracked
4. Refresh when done to start a new ride

### City Exploration
1. Exploring a new city
2. Track where you've been
3. Visual record of your wandering
4. Easy to see which streets you've covered

## Technical Implementation

### HTML Structure
```
index.html (single file, ~7KB)
├── MapLibre GL JS library (CDN)
├── MapLibre CSS (CDN)
├── Embedded JavaScript
└── Embedded CSS
```

### JavaScript Components
1. **Map Initialization**: Creates MapLibre map with OSM tiles
2. **Geolocation Setup**: Configures watchPosition with high accuracy
3. **Path Tracking**: Maintains array of coordinates
4. **Line Rendering**: Updates GeoJSON source with path data
5. **Marker Updates**: Moves user marker on position change
6. **Status Updates**: Shows tracking info and errors

### Map Style Configuration
```javascript
{
  version: 8,
  sources: {
    'osm': {
      type: 'raster',
      tiles: [
        'https://a.tile.openstreetmap.org/{z}/{x}/{y}.png',
        'https://b.tile.openstreetmap.org/{z}/{x}/{y}.png',
        'https://c.tile.openstreetmap.org/{z}/{x}/{y}.png'
      ]
    }
  }
}
```

### Line Style Configuration
```javascript
{
  'line-color': '#3887be',    // Blue color
  'line-width': 4,            // 4 pixel width
  'line-opacity': 0.8         // 80% opacity
}
```

## Browser Console Examples

When the app is running, you can check the browser console to see:

```javascript
// Check current path length
console.log(pathCoordinates.length); // e.g., 42 points

// View first coordinate
console.log(pathCoordinates[0]); // e.g., [-122.4194, 37.7749]

// Check marker position
console.log(userMarker.getLngLat()); // Current location
```

## Deployment Checklist

- [x] Single HTML file (no build process needed)
- [x] Uses CDN for dependencies (works on any static host)
- [x] No server-side code required
- [x] Mobile responsive
- [x] HTTPS compatible (required for geolocation)
- [x] GitHub Pages ready

## Expected Behavior

1. **First Load**: Map shows world view, prompts for location
2. **Permission Granted**: Map flies to user location, tracking starts
3. **Movement**: Line extends, point count increases
4. **Stationary**: Marker stays in place, no new points added (or very close)
5. **Refresh**: Everything resets, new tracking session begins

## Privacy & Security

- All processing happens in the browser
- No location data leaves your device
- No cookies or tracking
- No analytics
- No external API calls (except map tiles and CDN)
- Source code is fully visible and auditable
