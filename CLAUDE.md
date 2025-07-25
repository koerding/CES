# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a 2-Nest Economic Model with Endogenous Labor Allocation - an interactive web application that visualizes economic models using CES (Constant Elasticity of Substitution) and PSI (S-curve) aggregation methods.

## Architecture

The project is a single-page web application with:
- **index.html**: Self-contained HTML file with embedded CSS and JavaScript
- No external dependencies except Chart.js (loaded from CDN)
- Mathematical economic modeling functions implemented in vanilla JavaScript
- Interactive parameter controls with real-time chart updates

## Key Components

### Mathematical Functions (index.html:386-607)
- `computeP()`: Computes physical production output
- `computeI()`: Computes intelligence/AI production output  
- `computeY()`: Computes total output using CES or PSI aggregation
- `betaPStar()`: Finds optimal labor allocation using Brent's method
- Supporting derivative functions for marginal products

### UI Components
- Tab-based parameter controls (Basic, Nests, Top, PSI)
- Real-time updating charts (wage, output, allocation)
- Slider inputs with live value display

## Development Commands

Since this is a static HTML/JS application:
- **Run locally**: Open index.html in a web browser
- **Development server**: `python -m http.server 8000` or any static file server
- **No build process required** - direct file editing

## Testing

No automated tests are present. Manual testing involves:
1. Adjusting parameter sliders and verifying chart updates
2. Checking mathematical consistency across different parameter combinations
3. Ensuring UI responsiveness and error handling