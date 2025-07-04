# FTL Game Mechanics Simulation

## Project Overview
This project demonstrates light-lag physics and density wave theory through interactive visualizations. It started as a simple RTS light-lag demo and evolved into sophisticated galaxy simulations showing how spiral arms form through density waves.

## Files

### ftl.html
- Original light-lag demo with single ship and FTL probe
- Demonstrates:
  - Light travel delay based on 2D distance
  - Position history tracking for light cone physics
  - Doppler shift visualization (red/blue based on relative velocity)
  - FTL probe providing real-time sensor data within range
  - Light wave visualization showing speed of light
  - Player movement at various multiples of c (0.25c to 8c)

### galaxy.html
- Realistic galactic scale simulation (100,000 light-years across)
- 2000 stars with proper light-lag physics
- Time compression: 1 second = 1000 years
- Shows how light from distant stars arrives at different times

### galaxy-toy.html
- Visually optimized galaxy with immediate feedback
- 2000 stars in full disc distribution (not spiral)
- Interpolation for smooth rendering
- Focus on visual appeal over strict realism

### galaxy-hybrid.html
- Combines visual scale with real unit conversions
- Toggle between fast/realistic rotation speeds
- Shows both pixel and light-year measurements

### galaxy-toy2.html
- **Advanced barred spiral galaxy with emergent density waves**
- Key features:
  - 10,000 stars uniformly distributed (no initial spiral structure)
  - Density wave theory: spiral arms are "traffic jams" not material structures
  - 4 spiral arms (2 major, 2 minor) emerging from central bar
  - Stars slow down 10-90% in high-density regions
  - Adjustable pattern rotation speed (-0.1 to +0.1 rad/s)
  - Bar rotates 1.5x faster than spiral arms
  - No star formation - structure emerges purely from dynamics
  - Doppler coloring shows stellar velocities
  - Brightness enhancement in arms shows density structure

### solar-system.html
- **Accurate Sol system simulation with light-lag physics**
- Key features:
  - All 8 planets with correct orbital periods and distances
  - Real-time physics (1 second = 1 second, no time compression)
  - 10 AI ships with unique symbols (◆ ▲ ● ■ ★ ♦ ▼ ◐ ✦ ◈)
  - Each AI has unique speed: 16c, 8c, 4c, 2c, 1.5c, 1c, 0.75c, 0.5c, 0.25c, 0.1c
  - Autopilot system with target selection dropdown
  - Smooth zoom adjustment during autopilot
  - Multiple visible images for FTL ships
  - Adaptive tolerance for preventing flicker
  - Keyboard shortcuts: +/- for zoom, Tab for camera mode, Space for pause
  - Light waves show in each AI's color

## Key Concepts Implemented

### Light-Lag Physics
- Every object has a position history
- Observer sees objects based on when light left them
- Distance determines how far back in time you see
- Multiple images possible with FTL travel

### Doppler Shift
- Implemented with non-linear scaling for visual clarity
- 50% color shift at 1c relative velocity
- Blue shift for approaching, red shift for receding
- Proper calculation using relative velocities

### Density Wave Theory (galaxy-toy2.html)
- Spiral arms are density waves, not material structures
- Stars orbit uniformly but slow in high-density regions
- Creates self-sustaining spiral pattern
- Individual stars flow through arms (like cars through traffic)
- Pattern persists even though material moves through it
- Central bar creates resonances that help form spiral structure

## Controls (galaxy-toy2.html)

### Checkboxes
- **Show Density Field**: Visualize underlying density pattern
- **Show Stars**: Toggle star rendering
- **Enable Density Waves**: Toggle whether density affects star motion
- **Rotate Density Patterns**: Allow pattern rotation
- **Show Light Waves**: Expanding circles at light speed

### Sliders
- **Bar Strength**: 0-1, affects orbital resonances
- **Pattern Speed**: -0.1 to 0.1 rad/s, controls rotation rate

### Player Controls
- Arrow keys for movement
- Speed selector for multiples of light speed

## Technical Implementation

### Performance Optimizations
- Position history with automatic cleanup
- Interpolation between stored positions
- Distance-based culling (removed in galaxy-toy2 for accuracy)
- Squared distance calculations where possible
- Adjustable tolerance for light cone matching

### Visualization Techniques
- Doppler shift using RGB color interpolation
- Brightness modulation based on local density
- Density field using grid sampling
- Light waves with fade-out over distance
- Bar glow effect using linear gradients

## Physics Accuracy

### Correct Implementation
- Light cones expand at c from emission point
- Stars flow through density waves (not locked to pattern)
- Differential rotation (inner stars orbit faster)
- Bar resonances affect orbital velocities
- No initial spiral structure (emerges from dynamics)

### Simplifications
- 2D instead of 3D
- Discrete time steps (60 fps)
- Simplified gravity (circular orbits only)
- No gas dynamics or star formation
- No dark matter halo effects

## Testing Scenarios

1. **Uniform Distribution Test**
   - Start galaxy-toy2 with density waves OFF
   - Verify completely uniform star distribution
   - Enable waves and watch structure emerge

2. **Pattern Speed Test**
   - Set pattern speed to 0 (stationary waves)
   - Observe stars flowing through static pattern
   - Try negative speeds for reverse rotation

3. **Light-Lag Verification**
   - Move player at high speed in any galaxy sim
   - Verify stars appear/disappear based on light travel time
   - Check Doppler shifts match motion direction

## Known Issues and Solutions

### Issue: Stars "shimmering" at distance
**Solution**: Simplified position matching algorithm, increased tolerance

### Issue: Spiral structure persisting from initialization
**Solution**: Removed ALL density-based star placement at creation

### Issue: Stars getting locked in spiral patterns
**Solution**: Reduced velocity modifications, added random perturbations

### Issue: Performance with 5000+ stars
**Solution**: Optimized to 2000 stars for most sims, 10000 for galaxy-toy2

## Session State (2025-01-02)

### Current Implementation Status
- All galaxy simulations working with improved fidelity
- Solar system simulation (solar-system.html) with accurate physics
- 10 AI ships with unique symbols and speeds
- Advanced autopilot system with target selection
- Light cone physics properly implemented for all objects

### Recent Changes (ftl.html & galaxy files)
- Fixed position jumping with interpolation
- Increased star count to 5000 then optimized to 2000 for performance
- Changed from spiral to disc distribution
- Created galaxy-toy2.html with emergent density wave theory

### Recent Changes (solar-system.html)
- Created accurate Sol system model with all 8 planets
- Real-time physics (1 second = 1 second)
- Implemented multiple AI ships (10 total) with unique symbols
- Each AI has unique speed: 16c, 8c, 4c, 2c, 1.5c, 1c, 0.75c, 0.5c, 0.25c, 0.1c
- Fixed light cone tolerance (was 0.05 AU causing 25s early visibility, now 0.001 AU)
- Added adaptive tolerance for planets vs high-speed objects
- Removed pre-populated history for moving objects
- Fixed text color persistence with ctx.save()/restore()
- Added autopilot with target selection and smooth zoom
- Removed dashed lines from actual position display

### Key Fixes
- Light cone physics: Objects only visible when light reaches observer
- Multiple image rendering for FTL travel works correctly
- Performance optimized with adaptive sampling
- Planet flickering fixed with looser tolerance
- Autopilot cancels on manual movement

### Configuration
- Git repository initialized
- .claude/settings.local.json configured for git operations
- All changes committed with descriptive messages