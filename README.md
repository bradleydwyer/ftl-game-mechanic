# FTL Game Mechanics Simulation

An interactive demonstration of light-lag physics, special relativity effects, and density wave theory through various space simulations.

## Overview

This project explores how the finite speed of light affects our perception of moving objects, particularly when those objects travel faster than light (FTL). It includes simulations ranging from simple ship demos to complex galaxy dynamics and our solar system.

## Versions

### ftl.html - Original Light-Lag Demo
The foundational demo showcasing core light-lag concepts:
- Single ship with FTL probe companion
- Visual demonstration of light travel delay
- Doppler shift effects (red/blue coloring based on relative motion)
- FTL probe provides real-time data within sensor range
- Expanding light wave visualization
- Player speeds from 0.25c to 8c

### galaxy.html - Realistic Galaxy Scale
A scientifically accurate galaxy simulation:
- 100,000 light-year diameter galaxy
- 2,000 stars with proper light-lag physics
- Time compression: 1 second = 1,000 years
- Demonstrates how we see distant stars from different points in time

### galaxy-toy.html - Visual Galaxy
Optimized for visual appeal and immediate feedback:
- 2,000 stars in full disc distribution
- Smooth interpolation for enhanced visuals
- Focus on aesthetics while maintaining core physics

### galaxy-hybrid.html - Scale Comparison Galaxy
Bridges visual and scientific approaches:
- Toggle between fast/realistic rotation speeds
- Displays both pixel and light-year measurements
- Real unit conversions alongside visual representation

### galaxy-toy2.html - Emergent Spiral Galaxy
Advanced simulation demonstrating density wave theory:
- 10,000 uniformly distributed stars (no initial spiral structure)
- Spiral arms emerge naturally from density wave dynamics
- 4 spiral arms (2 major, 2 minor) from central bar
- Stars slow 10-90% in high-density regions
- Adjustable pattern rotation speed
- Shows how spiral galaxies maintain their structure

### solar-system.html - Sol System Simulation
Accurate model of our solar system with light-lag:
- All 8 planets with correct orbital periods and distances
- Real-time physics (1 second = 1 second)
- 10 AI ships with unique symbols and speeds (0.1c to 16c)
- Autopilot system with smooth navigation
- Multiple visible images for FTL ships
- Keyboard controls for zoom and camera modes

## Key Physics Concepts

### Light-Lag
Objects are seen based on when light left them, not their current position. Distance determines how far back in time you're seeing.

### Doppler Shift
Motion affects perceived color - approaching objects appear blue-shifted, receding objects appear red-shifted.

### Density Wave Theory
Spiral galaxy arms are density waves (like traffic jams) rather than fixed material structures. Stars flow through these regions, slowing down in high-density areas.

## Controls

### Common Controls
- Arrow keys: Move player ship
- Speed selector: Choose velocity (multiples of c)
- Space: Pause (some versions)
- +/-: Zoom (some versions)

### Galaxy-specific Controls
- Checkboxes for visual options
- Sliders for physics parameters
- Pattern speed adjustment

## Technical Features

- Position history tracking for accurate light-cone physics
- Multiple image rendering for FTL objects
- Performance optimizations for thousands of objects
- Adaptive tolerance for preventing visual artifacts
- Real-time interpolation for smooth motion

## Educational Value

These simulations help visualize:
- Why we see stars as they were, not as they are
- How FTL travel would create multiple visible images
- Why spiral galaxies maintain their shape
- The relationship between distance and time in astronomy
- Special relativity effects in an intuitive way

## Getting Started

Simply open any HTML file in a modern web browser. No installation required. Each simulation is self-contained and includes its own controls and instructions.

## Requirements

- Modern web browser with HTML5 Canvas support
- JavaScript enabled
- Recommended: Chrome, Firefox, Safari, or Edge

## License

This educational project demonstrates physics concepts through interactive visualization.