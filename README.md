# SEQUENCE | Spatial Intelligence | Vertascan

Browser-based conceptual architecture and space feasibility editor. Open `index.html` or deploy the directory to GitHub Pages. No backend, credentials or build step required.

## Deployment

Upload `index.html` to the repository root and enable **Settings → Pages → Deploy from a branch → main / root**. The file works on standard HTTPS static hosting. The 2D editor, spatial analyses, project saves and exports use native browser APIs. 3D initially loads the explicitly pinned Three.js ES module version **0.160.1** from jsDelivr; if it is unavailable, a basic native canvas isometric preview replaces the enhanced 3D renderer.

For **offline enhanced Three.js** support, download `https://cdn.jsdelivr.net/npm/three@0.160.1/build/three.module.js` to a local `vendor/three.module.js`, then change `THREE_URL` in `index.html` to `'./vendor/three.module.js'`. The editor and file exports already function without external dependencies.

## Features implemented

- 2D polygons, room rectangles, mass rectangles, rectangular site, selection, drag, vertex editing, undo/redo, pan/zoom/grid/snap.
- Editable object width, depth, location, name, classification; mass floor count and height.
- Live site coverage, footprint, area by space, GFA, NFA, efficiency, height and FAR.
- Color-coded room categories and residential/office/retail/mixed-use space presets.
- Basic 3D extruded geometry, elevation and side camera modes, 3D orbit/pan/zoom when Three.js loads, visual material modes.
- User-editable simple zoning limits, polygon overlap and clearance heuristics.
- Design option snapshots and metric comparison.
- JSON save/open and local autosave; SVG plan, CSV schedule, PNG screenshot, DXF floor-line export and self-contained GLB mesh export.
- Keyboard shortcuts; responsive interface.

## Scope / limitations

This is an MVP for concept planning rather than a production BIM or code compliance engine. It does not implement robust Boolean solids, split operations, camera clipping or walk-through, photorealistic materials, latitude-based solar studies, or calibrated building-code checking. The elevation/section labels use simplified views; the section option is **not a true clipped section**. Calculated site area and mass footprint treat each polygon independently; multiple overlapping masses count twice. Rectangular setback checks are bounding-box checks, not arbitrary polygon setbacks. GLB export consists of simple extrusions with object IDs and is not a detailed IFC model. Native project sizes and performance depend on hardware.

## Local test

Use a static file server (`python -m http.server 8000`) for development testing, then open `http://localhost:8000`. Access is also supported by opening `index.html` directly on most desktop browsers with network access for Three.js. GitHub Pages provides correct HTTPS origin.
