# FTL Light-Lag RTS Demo

## Project Overview
This is an interactive visualization demonstrating light-lag physics for a real-time strategy game concept. It shows how information propagates at the speed of light and how faster-than-light travel affects perception.

## Key Features

### Core Physics
- **Light-cone based rendering**: Objects are seen as they were when their light reaches the observer
- **Position history tracking**: Maintains 30 seconds of position history for accurate light propagation
- **Multiple simultaneous images**: When traveling FTL, you can see the same object at multiple time points
- **Doppler shift visualization**: Objects appear red/blue shifted based on relative motion

### Controls
- **Player Movement**: Arrow keys control yellow triangle player ship
- **Player Max Speed**: Dropdown with options from 0.25c to 8c
- **Ship Speed**: Remote ship oscillation speed from 0.25c to 8c
- **Oscillation Amplitude**: How far the remote ship moves (0-150 pixels)
- **Horizontal Movement**: Toggle between vertical/horizontal oscillation
- **FTL Probe**: Deployable sensor that provides real-time data within its range
- **Probe positioning**: Click anywhere on canvas to place probe
- **Ghost Display Modes**:
  - Always show: All light-based images visible
  - Hide when ship in probe range: Hides ghosts when real-time data available
  - Hide inside probe area: Hides any ghost within probe sensor bubble
- **Show Light Waves**: Visualizes expanding light circles every 1 second

### Technical Details

#### Constants
- Light speed: 60 pixels/second (`c_px_per_sec`)
- Player acceleration: 240 px/s²
- Player friction: 0.95 (5% velocity loss per frame when not accelerating)
- Probe sensor range: 80 pixels
- Light wave interval: 1 second
- Light wave fade duration: 40 seconds
- Position history duration: 30 seconds

#### Doppler Shift Calculation
- Handles relative velocities from -16c to +16c
- Uses logarithmic scaling for extreme velocities
- Color mapping:
  - Blue shift (approaching): RGB gradient from white to pure blue
  - Red shift (receding): RGB gradient from white to pure red
  - Neutral (no relative motion): White

#### Ship Oscillation
- Frequency calculated to achieve desired maximum velocity
- For sinusoidal motion: `f = (speed * c) / (2π * amplitude)`
- Maximum velocity occurs at center of oscillation

### Recent Improvements
1. Fixed edge collision physics - velocity components are zeroed when hitting canvas boundaries
2. Extended Doppler shift range to handle up to 16c relative velocity
3. Replaced sliders with discrete speed selections for precise control
4. Added light wave visualization to show speed of light propagation
5. Implemented proper light-cone physics with position history

### Settings Persistence
All settings are saved to localStorage under the key `ftlDemoSettings`:
- Distance, amplitude, speeds
- Toggle states (probe, movement, display modes)
- Probe position and phase
- Backwards compatibility with old setting names

### Known Edge Cases
- When player hits canvas edge, velocity in that direction is zeroed to prevent "stuck at high speed" Doppler shifts
- Light waves are cleaned up when they expand beyond canvas + 100px margin
- Ghost images fade based on age (max 0.8 alpha, min 0.2 alpha over 10 seconds)

### Testing Scenarios
1. **Chase scenario**: Set both speeds to same value, enable horizontal movement
2. **FTL intercept**: Set player to 4c+, move to intercept old light signals
3. **Doppler extremes**: Set both to 8c, move directly toward/away
4. **Probe deployment**: Click to place probe, watch real-time vs delayed data
5. **Light wave racing**: Set ship to 1c, watch ship move with its own light waves

## File Structure
- `ftl.html`: Single-file implementation with inline CSS and JavaScript
- Self-contained, no external dependencies

## Git History
- Initial commit: Basic light-lag demo
- Major enhancement: Added proper light-cone physics, player movement, FTL mode
- Doppler shift: Added red/blue shift visualization
- Speed controls: Discrete c-multiple selections and light wave visualization

## Future Enhancement Ideas
- Multiple remote ships at different distances
- Weapon projectiles that respect light-lag
- Mini-map showing "true" positions
- Network lag simulation on top of light-lag
- Save/load different scenarios
- Performance optimizations for larger fleets