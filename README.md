# SmartRoute360

SmartRoute360 is a React + Vite pathfinding visualizer built on top of a road-network graph and a Leaflet map. It lets you choose a start point, destination, and algorithm, then visualize node exploration, the final route, blocked nodes, and a realistic vehicle animation on the computed path.

## Features

- Visualize shortest-path and search algorithms on a real map
- Switch between A*, Dijkstra, Bidirectional Dijkstra, BFS, Greedy Best-First Search, and DFS
- Set start and end points directly from the map
- Block and unblock graph nodes using keyboard-assisted map interaction
- View live metrics such as runtime, explored nodes, path size, and route distance
- Animate a vehicle moving along the resulting route

## Tech Stack

- React 19
- Vite
- Leaflet
- Tailwind CSS
- Lucide React

## Getting Started

### Prerequisites

- Node.js 18 or later
- npm

### Install dependencies

```bash
npm install
```

### Start the development server

```bash
npm run dev
```

### Build for production

```bash
npm run build
```

### Lint the project

```bash
npm run lint
```

### Preview the production build

```bash
npm run preview
```

## Project Structure

```text
Smart Route/
├── public/
├── scripts/
│   ├── convertGeoJSON.js
│   └── export.geojson
├── src/
│   ├── algorithms/
│   │   └── pathfinding.js
│   ├── assets/
│   ├── components/
│   │   ├── MapLegend.jsx
│   │   ├── MapOverlay.jsx
│   │   ├── MetricsPanel.jsx
│   │   └── Sidebar.jsx
│   ├── hooks/
│   │   ├── useAlgorithms.js
│   │   ├── useMapInit.js
│   │   ├── useMapOverlays.js
│   │   └── useVehicle.js
│   ├── utils/
│   │   ├── graphUtils.js
│   │   ├── mathUtils.js
│   │   └── PriorityQueue.js
│   ├── App.jsx
│   ├── graph.json
│   ├── index.css
│   └── main.jsx
├── eslint.config.js
├── index.html
├── package.json
└── vite.config.js
```

## How It Works

1. `src/graph.json` stores the road-network graph used by the application.
2. `useMapInit` loads the graph and initializes the Leaflet map.
3. `useAlgorithms` runs the selected pathfinding algorithm and prepares exploration data.
4. `useMapOverlays` renders the explored nodes, blocked nodes, markers, and final route.
5. `useVehicle` animates a vehicle marker along the computed path.

## Map Controls

- Single click: set the start point
- Double click: set the destination
- `Ctrl + Click`: block or unblock the nearest node
- Scroll: zoom
- Drag: pan the map

## Algorithms Included

- A*
- Dijkstra
- Bidirectional Dijkstra
- Breadth-First Search
- Greedy Best-First Search
- Depth-First Search

## Graph Data Preparation

The app already includes a prepared graph file at `src/graph.json`.

The helper script in `scripts/convertGeoJSON.js` can be used to generate graph-style data from `scripts/export.geojson`. If you use this workflow, review the output path before running the script so the generated file lands where you want it.

## Notes for Contributors

- Keep commits grouped by feature area such as `core algorithms`, `map hooks`, or `UI components`
- Avoid committing experimental files unless they are part of the final app
- Prefer updating the modular files in `src/hooks`, `src/components`, `src/utils`, and `src/algorithms` instead of reviving older prototype files

## Current Main Files

- `src/App.jsx`: main application layout and composition
- `src/hooks/useAlgorithms.js`: algorithm execution and run-state management
- `src/hooks/useMapInit.js`: graph loading and map setup
- `src/hooks/useMapOverlays.js`: map markers, explored nodes, and route polylines
- `src/hooks/useVehicle.js`: vehicle animation logic
- `src/algorithms/pathfinding.js`: all implemented search algorithms

