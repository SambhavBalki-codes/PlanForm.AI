# PlanForm.AI 🏗️
### Transforming 2D Floor Plans into Intelligent Structural Insights

**PlanForm.AI** is an AI-powered structural intelligence platform that transforms architectural floor plan images into actionable engineering insights. By combining Computer Vision, Graph-Based Spatial Reasoning, 3D Visualization, AI-driven recommendations, and Blockchain technology, it bridges the gap between architectural blueprints and structural decision-making.

Upload a floor plan and let PlanForm.AI automatically detect walls, rooms, doors, and windows, reconstruct an interactive 3D representation, recommend suitable construction materials, and explain the engineering rationale behind every recommendation.

For transparent and immutable record-keeping, analysis results can also be registered on the **Stellar Blockchain**.

---

## 🎥 Project Demo

**Watch PlanForm.AI in Action**

[▶️ Watch the Project Demo](https://lnkd.in/p/dkbwS-jU)

Explore the complete workflow, from blueprint upload and structural analysis to 3D visualization, material recommendations, and blockchain registration.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| **Intelligent Floor Plan Parsing** | OpenCV-powered detection of walls, rooms, doors, and windows from architectural blueprints. |
| **Graph-Based Spatial Reasoning** | Models wall segments as a graph and identifies structural openings through geometric gap analysis. |
| **Interactive 3D Reconstruction** | Converts detected floor plans into interactive Three.js models featuring extruded walls, door leaves, window panels, and wall labels. |
| **AI-Powered Material Recommendations** | Evaluates approximately 100 construction materials using cost, strength, durability, span, and thermal efficiency. |
| **Explainable AI Insights** | Uses Groq-powered LLMs to generate engineering explanations, material selection rationale, and structural trade-offs. |
| **AI Engineering Assistant** | Enables users to ask follow-up questions about structural elements, material choices, and analysis results. |
| **Stellar Blockchain Registry** | Registers immutable analysis records on the Stellar Testnet using Soroban smart contracts. |
| **Coordinate Overlay Generation** | Produces annotated blueprint images with detected wall endpoints for visual verification and cross-referencing. |

---

## 🏛️ System Architecture

PlanForm.AI follows a modular architecture consisting of a React frontend, Node.js orchestration layer, and an independent Python Computer Vision service.

```text
                   ┌──────────────────────────┐
                   │       React + Vite       │
                   │       Frontend           │
                   └────────────┬─────────────┘
                                │
                         REST API Requests
                                │
                                ▼
                   ┌──────────────────────────┐
                   │    Node.js + Express     │
                   │                          │
                   │  • File Upload (Multer)  │
                   │  • Pipeline Orchestration│
                   │  • Structural Classifier │
                   │  • Material Scoring      │
                   └──────┬───────────┬───────┘
                          │           │
                 HTTP     │           │ Groq API
                          ▼           ▼
              ┌────────────────┐  ┌──────────────┐
              │ Python FastAPI │  │  Groq LLM    │
              │  CV Service    │  │              │
              │                │  │ AI Insights  │
              │ • OpenCV       │  │ Explanations │
              │ • Wall Detection│  │ Chat         │
              │ • Symbol       │  └──────────────┘
              │   Recognition  │
              │ • Graph Analysis│
              │ • Coordinates  │
              └───────┬────────┘
                      │
                 Analysis Results
                      │
                      ▼
              ┌────────────────┐
              │ React Results  │
              │                │
              │ • Layout Viewer│
              │ • 3D Model     │
              │ • Material     │
              │   Recommendations
              │ • AI Insights  │
              └───────┬────────┘
                      │
                      ▼
              ┌────────────────┐
              │ Stellar Testnet│
              │ Soroban        │
              │ Smart Contract │
              └────────────────┘
```

---

## 🛠️ Technology Stack

### Frontend
- **React 19** – Component-based user interface.
- **Vite 8** – Frontend development and build tooling.
- **Tailwind CSS** – Utility-first styling.
- **Three.js** – 3D rendering and visualization.
- **React Three Fiber & Drei** – Declarative 3D scene development.
- **Framer Motion** – UI animations and transitions.
- **Stellar SDK & Freighter API** – Blockchain wallet integration.

### Backend
- **Node.js & Express 5** – REST API and pipeline orchestration.
- **Multer** – Multipart image upload handling.
- **Axios** – HTTP communication between services.
- **Groq SDK** – LLM-powered explanations and conversational AI.

### Computer Vision & Processing
- **Python 3.10+**
- **FastAPI & Uvicorn**
- **OpenCV** – Image processing and geometric feature detection.
- **NumPy** – Numerical and coordinate operations.
- **Pillow** – Image manipulation.
- **scikit-image** – Image processing utilities.

### Blockchain
- **Stellar Testnet** – Blockchain network.
- **Soroban** – Smart contract platform.
- **Rust** – Smart contract development.
- **Freighter** – Browser-based Stellar wallet.

---

## 📂 Project Structure

```text
PlanForm.AI/
│
├── client/                         # React + Vite frontend
│   └── src/
│       ├── components/             # UI and visualization components
│       ├── pages/                  # Application pages
│       └── services/               # API and Stellar integration
│
├── server/                         # Node.js + Express backend
│   ├── controllers/                # Request controllers
│   ├── services/                   # Core application services
│   ├── utils/                      # Scoring and classification logic
│   └── config/                     # Application configuration
│
├── cv-service/                     # Python Computer Vision service
│   ├── app.py                      # FastAPI application
│   └── parser/
│       ├── preprocess.py           # Floor plan processing pipeline
│       └── graph_utils.py          # Wall graph and opening detection
│
├── smart-contract/                 # Soroban smart contracts
│   └── contracts/
│       └── blueprint_registry/
│           └── src/lib.rs
│
├── data/
│   └── materials.json              # Construction material catalog
│
├── deploy-contract.sh              # Linux/macOS deployment script
└── deploy-contract.ps1             # Windows deployment script
```

---

## 🚀 Getting Started

### Prerequisites

Ensure the following tools are installed:

| Technology | Requirement |
|---|---|
| Node.js | LTS (20 or higher) |
| npm | Latest stable |
| Python | 3.10 or higher |
| pip | Latest stable |
| Rust & Cargo | Latest stable |
| Stellar CLI | Latest stable |

Install the Stellar CLI:

```bash
cargo install --locked stellar-cli
```

### 1. Clone the Repository

```bash
git clone https://github.com/your-org/planform-ai.git
cd PlanForm.AI
```

### 2. Install Backend Dependencies

```bash
cd server
npm install
```

### 3. Install Frontend Dependencies

```bash
cd ../client
npm install
```

### 4. Install Computer Vision Dependencies

```bash
cd ../cv-service
pip install -r requirements.txt
```

### 5. Configure Environment Variables

Create a `.env` file inside the `server/` directory:

```env
GROQ_API_KEY=your_groq_api_key
PORT=5000
```

Create a `.env` file inside the `client/` directory:

```env
VITE_CONTRACT_ID=your_soroban_contract_id
VITE_STELLAR_NETWORK=testnet
```

### 6. Run the Application

Start all three services in separate terminal windows.

**Terminal 1 – Computer Vision Service**

```bash
cd cv-service
uvicorn app:app --reload --port 8000
```

**Terminal 2 – Backend API**

```bash
cd server
npm run dev
```

**Terminal 3 – Frontend**

```bash
cd client
npm run dev
```

Open the application in your browser:

```text
http://localhost:5173
```

---

## ⚙️ How the Analysis Pipeline Works

PlanForm.AI processes an uploaded blueprint through a sequence of computer vision, geometric reasoning, structural classification, and AI-powered analysis stages.

**1. Blueprint Upload**

The user uploads an architectural floor plan through the React interface. Multer handles the image upload, and the Node.js backend forwards it to the Python CV service.

**2. Image Preprocessing & Wall Extraction**

OpenCV processes the image using thresholding and image segmentation techniques. It estimates wall thickness, separates structural lines from annotations, and applies Hough Line Detection to identify wall boundaries.

**3. Door & Window Recognition**

Geometric features and connected components are used to detect door arcs, window symbols, and other architectural openings.

**4. Gap Classification**

Detected wall discontinuities are analyzed using proximity to architectural symbols and geometric heuristics to classify gaps as doors, windows, or general openings.

**5. Graph-Based Spatial Modeling**

Detected wall segments are represented as graph edges with stable identifiers such as `W-03`. This enables spatial relationship analysis and consistent element tracking.

**6. Structural Classification**

The backend estimates physical dimensions by converting pixel measurements into metres and classifies structural elements into categories such as:

- Partition walls
- Load-bearing walls
- Long-span elements
- Beams
- Slabs
- Columns

**7. Material Recommendation Engine**

A scoring engine evaluates candidates from the construction material catalog using weighted parameters such as:

- Material cost
- Structural strength
- Durability
- Thermal efficiency
- Span suitability

The system ranks materials according to their suitability for each classified structural element.

**8. AI-Generated Engineering Explanations**

Groq-powered LLMs generate natural-language explanations covering project insights, material selection rationale, and important engineering trade-offs.

**9. Results & Visualization**

The frontend presents the processed layout, interactive 3D reconstruction, material recommendations, coordinate overlays, and AI-generated explanations.

---

## ⛓️ Blockchain Integration

PlanForm.AI integrates **Stellar Testnet and Soroban smart contracts** to provide an immutable record of analyzed blueprints.

### Registration Workflow

1. Connect a Freighter wallet configured for Stellar Testnet.
2. Fund the wallet using Friendbot if the account requires testnet XLM.
3. Select **Store Blueprint on Blockchain**.
4. The application generates a SHA-256 hash of the material recommendations.
5. The hash and associated project metadata are submitted to the Soroban smart contract.
6. After successful confirmation, the application provides a blueprint ID and Stellar block explorer reference.

### On-Chain Information

The smart contract stores:

- Project name
- Owner wallet address
- Cost estimate
- Materials hash
- Room count
- Total floor area
- Registration timestamp

This provides a verifiable record of the registered analysis.

---

## 🔗 Smart Contract Deployment

The project includes deployment scripts for both Linux/macOS and Windows.

**Linux / macOS**

```bash
chmod +x deploy-contract.sh
./deploy-contract.sh
```

**Windows (PowerShell)**

```powershell
.\deploy-contract.ps1
```

The deployment scripts automate the following operations:

1. Compile the Rust smart contract into WebAssembly (WASM).
2. Create a Stellar deployer identity if one does not already exist.
3. Fund the deployer account using Friendbot.
4. Deploy the contract to Stellar Testnet.
5. Configure the contract ID in `client/.env`.
6. Initialize the deployed contract.

---

## 📡 API Reference

### 1. Analyze Floor Plan

`POST /api/pipeline/analyze`

Accepts a `multipart/form-data` request containing the uploaded floor plan.

**Request:**

| Parameter | Type | Description |
|---|---|---|
| `floorPlan` | File | Architectural floor plan image |

**Sample Response:**

```json
{
  "success": true,
  "parsedLayout": {
    "walls": 28,
    "rooms": 7,
    "wallSegments": []
  },
  "structuralElements": [],
  "recommendations": [],
  "aiExplanation": "..."
}
```

### 2. AI Engineering Chat

`POST /api/pipeline/chat`

Accepts a JSON request containing a user question and the existing analysis context.

**Sample Request:**

```json
{
  "message": "Why was RCC chosen for the load-bearing walls?",
  "aiExplanation": "...",
  "recommendations": [],
  "parsedLayout": {},
  "chatHistory": []
}
```

**Sample Response:**

```json
{
  "success": true,
  "reply": "RCC was selected because..."
}
```

---

## 🔮 Future Scope

Potential directions for extending PlanForm.AI include:

- Improved detection accuracy for complex and low-resolution architectural drawings.
- More advanced structural analysis and load estimation.
- Support for additional blueprint formats and multi-floor buildings.
- Enhanced material recommendations using regional pricing and availability.
- Integration with additional blockchain networks.
- Exportable engineering reports and detailed 3D model formats.

---

## 👨‍💻 Project

**PlanForm.AI** — Combining Computer Vision, Artificial Intelligence, 3D Modeling, and Blockchain to make structural intelligence more accessible.

[▶️ Watch Demo](https://lnkd.in/p/dkbwS-jU)

