# Starlink Satellite Tracker

An interactive web application for discovering and tracking nearby Starlink satellites based on an observer's geographic location.

The application retrieves satellite data from the N2YO API and visualizes selected satellites on an animated world map built with React, D3.js, and HTML Canvas.

## Features

- Search for nearby Starlink satellites based on observer location
- Configure longitude, latitude, elevation, minimum altitude, and tracking duration
- Retrieve nearby satellite information from the N2YO API
- Display satellite names and launch dates
- Select and track multiple satellites simultaneously
- Retrieve predicted satellite positions for a specified time period
- Visualize satellite movement on an animated world map
- Display satellite positions using geographic map projection
- Render multiple satellites with distinct colors

## Tech Stack

### Frontend

- React
- JavaScript
- Ant Design
- Axios

### Data Visualization

- D3.js
- D3 Geo
- D3 Geo Projection
- TopoJSON
- HTML Canvas

### External Data

- N2YO Satellite API
- World Atlas TopoJSON dataset

## How It Works

The application allows the user to provide an observer location:

- Longitude
- Latitude
- Elevation
- Minimum altitude
- Tracking duration

The application then queries the N2YO API for nearby Starlink satellites.

```text
Observer Location
        |
        v
N2YO Nearby Satellite API
        |
        v
Nearby Starlink Satellites
        |
        v
Select Satellites
        |
        v
N2YO Satellite Position API
        |
        v
Predicted Position Data
        |
        v
D3 Geographic Projection
        |
        v
Animated World Map
```

Users can select one or more satellites from the returned list and track their predicted movement on the world map.

## Application Architecture

The application is organized into several React components:

```text
App
 |
 +-- Header
 |
 +-- Main
 |    |
 |    +-- SatSetting
 |    |
 |    +-- SatelliteList
 |    |
 |    +-- WorldMap
 |
 +-- Footer
```

### SatSetting

Provides the form used to configure the observer location and tracking parameters.

Input validation is handled using Ant Design form components.

### SatelliteList

Displays nearby Starlink satellites returned by the N2YO API.

Users can select multiple satellites and send the selected satellites to the map for tracking.

### WorldMap

Handles the geographic visualization and satellite animation.

The world map is generated from TopoJSON geographic data using D3.

Satellite longitude and latitude coordinates are converted into canvas coordinates using the Kavrayskiy VII geographic projection.

Two HTML Canvas layers are used:

- A base layer for the world map and geographic grid
- A tracking layer for animated satellite positions

This allows the satellite animation to be updated independently without redrawing the underlying world map.

## Satellite Tracking

After satellites are selected, the application retrieves predicted position data for each satellite.

Multiple requests are performed concurrently and the returned position data is used to animate satellite movement over time.

Each satellite is rendered using a different color and labeled on the map.

## API

Satellite data is provided by the N2YO API.

The application uses endpoints for:

- Finding satellites above an observer location
- Retrieving predicted satellite positions

Starlink satellites are queried using the Starlink satellite category.

## Project Structure

```text
src/
├── assets/
│   └── images/
│
├── components/
│   ├── App.js
│   ├── Footer.js
│   ├── Header.js
│   ├── Main.js
│   ├── SatSetting.js
│   ├── SatelliteList.js
│   └── WorldMap.js
│
├── styles/
│   ├── App.css
│   ├── Footer.css
│   ├── Header.css
│   ├── Main.css
│   ├── SatSetting.css
│   ├── SatelliteList.css
│   └── WorldMap.css
│
├── constants.js
├── index.css
├── index.js
└── setupTests.js
```

## Running the Project

### Prerequisites

- Node.js
- npm
- N2YO API key

Clone the repository:

```bash
git clone https://github.com/charliecheng19882006/starlink-satellite-tracker.git
cd starlink-satellite-tracker
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm start
```

The application will run locally using the React development server.

> The project depends on external satellite APIs and was originally built with an earlier React ecosystem. Additional configuration or dependency updates may be required when running the project today.

## Future Improvements

Potential improvements include:

- Move external API requests behind a backend service
- Improve API key management
- Upgrade React and project dependencies
- Add additional satellite categories
- Improve map interaction and satellite selection
- Add satellite trajectory paths
- Add automated tests
- Add responsive mobile support
- Containerize and deploy the application

## Project Purpose

This project was built to explore frontend development, REST API integration, geographic data visualization, and real-time-style animation using React and D3.

It demonstrates how external satellite data can be transformed into an interactive geospatial visualization in a web application.
