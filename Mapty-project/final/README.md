# JavaScript Functions Overview

This README provides an overview of the JavaScript functions used in the provided code. These functions are based on the courses in JavaScript that were studied.

## 1. `Workout` Class
- **Description**: Represents a workout session.
- **Properties**:
  - `date`: Date object representing the date of the workout.
  - `id`: Unique identifier for the workout session.
  - `clicks`: Number of clicks on the workout.
- **Methods**:
  - `_setDescription`: Private method to set the description of the workout.

## 2. `Running` Class (Extends `Workout`)
- **Description**: Represents a running workout session.
- **Properties**:
  - `type`: Type of workout (running).
  - `cadence`: Cadence of running.
- **Methods**:
  - `calcPace`: Method to calculate pace of running workout.

## 3. `Cycling` Class (Extends `Workout`)
- **Description**: Represents a cycling workout session.
- **Properties**:
  - `type`: Type of workout (cycling).
  - `elevationGain`: Elevation gain during cycling.
- **Methods**:
  - `calcSpeed`: Method to calculate speed of cycling workout.

## 4. `App` Class
- **Description**: Main application class handling UI interactions and map functionality.
- **Properties**:
  - `#map`: Reference to the map object.
  - `#mapZoomLevel`: Zoom level of the map.
  - `#mapEvent`: Event handler for map events.
  - `#workouts`: Array containing workout sessions.
- **Methods**:
  - `_getPosition`: Method to get user's geolocation.
  - `_loadMap`: Method to load map based on user's geolocation.
  - `_showForm`: Method to show workout form on map click.
  - `_hideForm`: Method to hide workout form.
  - `_toggleElevationField`: Method to toggle elevation field based on workout type.
  - `_newWorkout`: Method to handle submission of new workout form.
  - `_renderWorkoutMarker`: Method to render workout marker on map.
  - `_renderWorkout`: Method to render workout details in the list.
  - `_moveToPopup`: Method to move map view to workout marker on list item click.
  - `_setLocalStorage`: Method to save workouts to local storage.
  - `_getLocalStorage`: Method to retrieve workouts from local storage.
  - `reset`: Method to reset workouts data.

---

