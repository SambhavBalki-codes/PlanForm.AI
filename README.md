# PlanForm.AI

**PlanForm.AI** is an AI-powered structural intelligence platform that transforms static floor plan images into **interactive architectural insights**.

Upload a blueprint and the system automatically:

- Detects **walls, rooms, doors, and windows**
- Converts the plan into a **structured spatial graph**
- Generates a **3D model**
- Recommends **construction materials**
- Explains the reasoning behind every recommendation using **AI**

The platform combines **Computer Vision, Graph Analysis, and Large Language Models** into a single intelligent pipeline.

---

# Key Capabilities

## 1. Floor Plan Parsing

The computer vision service processes uploaded floor plan images using **OpenCV**.

Steps include:

1. Separating **thick wall lines** from **thin annotation lines**
2. Running **Hough Line Detection** to identify wall edges
3. Merging parallel edges into **centerline walls**
4. Snapping endpoints to build **clean junctions**

This converts a noisy blueprint into structured wall geometry.

---

## 2. Door and Window Detection

PlanForm identifies openings through pattern recognition.

### Doors
- Detected using **quarter-circle arc patterns**
- Matched with wall openings

### Windows
- Detected via **parallel line pairs**
- Hollow rectangular contours

All detected openings are validated against wall gaps to ensure accurate placement.

---

## 3. Graph-Based Spatial Reasoning

Once walls are detected, they are converted into a **spatial graph**.

- **Nodes:** wall endpoints
- **Edges:** wall segments

Each edge contains metadata like:

- Wall ID
- Orientation
- Length
- Adjacency

This graph enables:

- Gap detection
- Room inference
- Structural reasoning

---

## 4. Interactive 3D Model Viewer

The parsed layout is rendered in the browser using **Three.js**.

The viewer generates:

- **Extruded walls**
- **Transparent door gaps**
- **Glass window panels**

Users can rotate, zoom, and inspect the model interactively.

---

## 5. Material Recommendation Engine

PlanForm evaluates a catalog of **100+ construction materials**.

Each wall segment is classified based on **structural span**:

- Partition wall
- Load-bearing wall
- Long span
- Beam support

A scoring system ranks materials using criteria such as:

- Structural strength
- Cost efficiency
- Suitability for span
- Durability

---

## 6. AI Explanation and Chat

After analysis, the system sends structured results to **Groq's LLM API**.

The AI generates:

- Project summary
- Element-by-element reasoning
- Material tradeoffs
- Construction insights

A **floating chat assistant** allows users to ask follow-up questions such as:

- "Why did you choose reinforced concrete for this wall?"
- "What happens if I increase the span?"

---

## 7. Blockchain Blueprint Registry

PlanForm allows architectural results to be **registered on-chain**.

Using the **Stellar testnet** and **Soroban smart contracts**, the system stores a hashed record of:

- Material recommendations
- Room count
- Estimated area
- Cost estimates

Users can connect their **Freighter wallet** to register a blueprint.

This creates a **tamper-proof structural record**.

---

## 8. Coordinate Overlay Visualization

The CV service generates an **annotated version of the blueprint**.

This overlay shows:

- Wall endpoint coordinates
- Junction points
- Spatial references

The annotated version appears in the **layout viewer**, helping users cross-reference the **2D blueprint and 3D model**.

---

# System Architecture

```
            Upload Floor Plan
                    │
                    ▼
            Node.js API Server
                    │
        ┌───────────┴───────────┐
        ▼                       ▼
Computer Vision Service    AI Reasoning
   (FastAPI + OpenCV)      (Groq LLM)
        │                       │
        ▼                       ▼
  Spatial Graph          Material Analysis
        │
        ▼
  3D Model Generation
        │
        ▼
  React + Three.js Viewer
        │
        ▼
 Blockchain Registry (Stellar)
```

---

# Repository Structure

```
PlanForm.AI
│
├── client/               React + Vite frontend
├── server/               Node.js Express API
├── cv-service/           Python FastAPI computer vision service
├── smart-contract/       Soroban smart contract code
├── data/                 Local data files
│
├── deploy-contract.sh    Contract deployment script (Linux/macOS)
├── deploy-contract.ps1   Contract deployment script (Windows)
│
└── package.json          Root dependencies
```

---

# Tech Stack

## Frontend

- React (Vite)
- Tailwind CSS
- Three.js
- React Three Fiber
- Drei
- Framer Motion

## Backend

- Node.js
- Express
- Multer
- Axios
- Groq SDK

## Computer Vision Service

- FastAPI
- Uvicorn
- OpenCV
- NumPy
- Pillow
- scikit-image

## Blockchain

- Stellar SDK
- Soroban Smart Contracts
- Freighter Wallet

---

# Getting Started

## Prerequisites

Make sure you have installed:

- **Node.js (LTS recommended)**
- **Python 3.10+**
- **pip**

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/planform-ai.git
cd planform-ai
```

### 2. Install dependencies

```bash
npm install
```

### 3. Setup the CV service

```bash
cd cv-service
pip install -r requirements.txt
```

---

## Running the Project

### Start backend

```bash
cd server
npm run dev
```

### Start frontend

```bash
cd client
npm run dev
```

### Start CV service

```bash
uvicorn main:app --reload
```

---

# Future Improvements

Planned enhancements include:

- Handling **hand-drawn floor plans**
- Detecting **non-orthogonal walls**
- Integrating **real-time construction material pricing**
- Automatic **room classification**
- Structural **load simulation**
- Exporting models to **CAD / BIM formats**

---

# Use Cases

PlanForm can be used by:

- Architects
- Civil engineers
- Real estate developers
- Construction planners
- Architecture students

---

# License

MIT License
