# 🔥 ThermoForge ❄️

**An Emergent Simulation of Fire vs. Ice**

Part of the **Forge Theory** collection - demonstrating how complex thermal dynamics emerge from simple rules of diffusion and decay.

---

## 🎯 What Is This?

ThermoForge is an interactive cellular automaton that simulates the battle between heat and cold. Paint fire or ice onto a grid and watch as thermal energy spreads, decays, and creates emergent patterns of flow and boundary formation.

**Key Features:**
- **Dual Temperature System**: Fire (positive heat) vs Ice (negative cold)
- **Realistic Diffusion**: Heat spreads to neighbors through weighted averaging
- **Entropy Decay**: All temperatures naturally drift toward equilibrium (0)
- **Wind Physics**: Directional wind carries embers and frost particles
- **Particle Feedback Loop**: Airborne particles land back on the grid, spreading heat/cold
- **Real-time Statistics**: Track hot cells, cold cells, embers, and frost particles

---

## 🧠 The Emergence

ThermoForge demonstrates how **three simple rules** create realistic thermal behavior:

### Rule 1: Diffusion
Each cell averages its temperature with its 8 neighbors (20% weight to neighbors, 80% self). This creates smooth heat/cold gradients without explicit "flow" logic.

### Rule 2: Entropy
All temperatures decay toward zero at a constant rate (0.005 per tick). Hot cools down, cold warms up - the universe seeks equilibrium.

### Rule 3: Wind Transport
Particles spawn from extreme temperatures (>2.0 or <-2.0) and drift with the wind. When they land, they transfer thermal energy to new locations.

**What Emerges:**
- **Thermal Boundaries**: Stable zones form where fire and ice meet
- **Flow Channels**: Wind creates "rivers" of heat or cold
- **Pulse Waves**: Large temperature sources send ripples across the grid
- **Self-Organization**: Without central control, the system creates structure

---

## 🎮 How to Use

1. **Select Your Tool**: Toggle between Fire (🔥) and Ice (❄️)
2. **Paint**: Click or drag on the grid to apply heat or cold
3. **Control Wind**: 
   - Adjust wind speed (0-10)
   - Set wind direction (0-360°)
4. **Observe**: Watch thermal dynamics unfold in real-time
5. **Reset**: Clear the grid and start fresh

### Interaction Tips:
- **Small brushes** create focused heat sources
- **Wind at 5+** creates dramatic particle flows
- **Fire vs Ice battlelines** form naturally at temperature boundaries
- **Circular patterns** emerge when painting in the center without wind

---

## 🔬 Technical Deep Dive

### Grid System
- **Resolution**: 100×100 cells
- **Update Rate**: 30ms per tick (~33 fps)
- **Temperature Range**: -10.0 (extreme cold) to +10.0 (extreme heat)

### Diffusion Algorithm
```javascript
// Weighted average with 8 neighbors
const avgHeat = neighborSum / neighborCount;
let diffusedHeat = (currentHeat * 0.8) + (avgHeat * 0.2);
```

This creates smooth thermal gradients while preserving energy conservation (minus entropy).

### Particle System
- **Spawn Threshold**: Abs(temperature) > 2.0
- **Spawn Rate**: 1% chance per tick, scaled by temperature intensity
- **Lifespan**: 60-100 frames
- **Physics**: Velocity + wind vector + gravity (upward drift)
- **Landing**: 10% chance when life < 20, transfers ±3.0 temperature

### Color Mapping
- **Fire**: HSL gradient from red (0°) to yellow (40°), increasing lightness
- **Ice**: HSL gradient from light blue (220°) to deep blue (240°), increasing lightness
- **Neutral**: Dark grey (#111)

---

## 📊 Performance Notes

**Current Stats:**
- ~100,000 calculations per tick (100×100 grid)
- Dual canvas rendering (grid + particles)
- No external dependencies
- Fully offline-capable

**Optimization Opportunities** (if needed):
- Use `Float32Array` for 2x speed on large grids
- Reduce neighbor checks from 8 to 4 (cardinal only)
- Spatial partitioning for "dormant" cells near equilibrium
- WebGL rendering for grids >200×200

---

## 🧪 Experiment Ideas

### 1. **Fire Wall vs Ice Wall**
Paint a vertical line of fire on the left, ice on the right. Watch the thermal boundary stabilize.

### 2. **Wind Channel**
Set wind to 8-10 and paint fire in the lower left. Observe the "river" of embers flowing across the grid.

### 3. **Thermal Pulse**
Paint a large circle of fire in the center with no wind. Watch concentric heat waves expand outward.

### 4. **Cold Vortex**
Set wind direction to rotate (0° → 90° → 180° → 270°) while painting ice. Creates swirling frost patterns.

### 5. **Equilibrium Race**
Paint equal amounts of fire and ice. Which reaches equilibrium first? (Hint: Check particle spawn rates)

---

## 🎨 Forge Theory Context

ThermoForge explores **thermal emergence** - how heat and cold interact through diffusion and transport. It demonstrates:

- **Energy Conservation** (with entropy loss)
- **Boundary Formation** (phase transitions)
- **Transport Dynamics** (convection via particles)
- **Self-Organization** (patterns without planning)

This fits within the broader Forge Theory framework:
- **Layer 1**: Simple rules (diffusion, decay, wind)
- **Layer 2**: Interaction substrate (grid + particles)
- **Layer 3**: Emergent phenomena (boundaries, flows, waves)

---

## 🛠️ Technical Stack

- **Pure HTML/CSS/JavaScript** - No frameworks, no build process
- **Canvas API** - Dual-layer rendering
- **Cellular Automaton** - Grid-based physics
- **Particle System** - Airborne thermal transport
- **Mobile-Optimized** - Touch controls and responsive layout

---

## 📖 Code Structure

```
ThermoForge
├── Grid System (heat[][])
│   ├── Diffusion calculation
│   ├── Entropy decay
│   └── Neighbor averaging
│
├── Particle System (particles[])
│   ├── Spawn from extreme temps
│   ├── Wind-affected physics
│   └── Landing/transfer logic
│
├── Rendering
│   ├── Grid canvas (thermal colors)
│   └── Smoke canvas (particles)
│
└── UI Controls
    ├── Paint tools (fire/ice)
    ├── Wind controls
    └── Real-time stats
```

---

## 🚀 Future Enhancements

**Potential Additions** (not yet implemented):
- **Phase Transitions**: Ice → Water → Steam state changes
- **Thermal Inertia**: Materials with different heat capacities
- **Convection Bias**: Hot rises, cold sinks naturally
- **Steam Zones**: Neutral particles spawn where fire meets ice
- **Interactive Wind**: Click-drag to create localized gusts
- **Preset Scenarios**: Load interesting starting configurations

---

## 📜 License & Usage

**Free to use, modify, and learn from.**

This is an educational simulation demonstrating emergent thermal dynamics. Use it to:
- Learn about cellular automata
- Explore diffusion algorithms
- Understand particle systems
- Teach thermal physics concepts

**Attribution appreciated but not required.**

---

## 🧑‍💻 About Forge Theory

Forge Theory is a collection of educational simulations demonstrating how **complexity emerges from simplicity**. Each "Forge" explores a different domain:

- **TreeForge**: Fractal growth and branching
- **EcoForge**: Ecosystem dynamics
- **NeuroForge**: Neural network emergence
- **LinguaForge**: Language evolution
- **LifeForge**: Cellular automata (Conway's Game of Life)
- **Cosmogenesis**: Universe formation
- **ThermoForge**: Thermal dynamics ← *You are here*

---

## 🤝 Contributing

Found an interesting emergent pattern? Have optimization ideas? Want to add features?

**Suggestions Welcome:**
- Open an issue describing the behavior/feature
- Include screenshots of interesting patterns
- Share parameter combinations that create cool effects

**Code Contributions:**
- Keep it dependency-free
- Maintain the simple rule → complex behavior philosophy
- Document emergent phenomena you discover

---

## 📞 Contact

Created by **James (ShapedMaker3D / Giblets Creations)**

Part of the ongoing exploration of emergence, complexity, and self-organization in computational systems.

---

**🔥 Fire seeks to expand. ❄️ Ice seeks to preserve. ⚖️ The grid seeks equilibrium.**

*Let the thermal battle begin.*
