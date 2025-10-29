# NextGen CellDynamics Platform

**Advanced Computational Biology Platform for Cell Culture Simulation**

A state-of-the-art cellular dynamics simulation platform that surpasses existing tools like Morpheus and PhysicalCell through advanced biological modeling, spatial dynamics, pharmacokinetics/pharmacodynamics, and machine learning integration.

---

## 🚀 Key Features

### **Advanced Biological Modeling**
- **Detailed Cell Cycle Dynamics**: G1, S, G2, M phases with checkpoint control
- **Metabolic Modeling**: ATP production, glucose/oxygen consumption, lactate accumulation
- **Gene Expression Dynamics**: Key oncogenes and tumor suppressors (MYC, TP53, KRAS, EGFR, BCL2)
- **Cell-Cell Interactions**: Contact inhibition, paracrine signaling
- **Multiple Death Pathways**: Apoptosis and necrosis with distinct triggers

### **Spatial Microenvironment**
- **2D Diffusion Grid**: Nutrient and oxygen gradients
- **Dynamic pH**: Lactate-driven acidification
- **Waste Accumulation**: Metabolic byproduct tracking
- **Spatial Resolution**: 10μm grid for realistic diffusion

### **Pharmacology (PK/PD)**
- **Multi-Compartment Model**: Media → Intracellular compartments
- **Drug Classes**:
  - Taxol (microtubule inhibitor)
  - Cisplatin (DNA crosslinker)
  - Doxorubicin (topoisomerase II inhibitor)
  - Gemcitabine (antimetabolite)
  - Targeted therapies
- **Resistance Mechanisms**: Efflux pumps, intracellular degradation
- **Hill Equation Dynamics**: Dose-response with IC₅₀ and Hill coefficients

### **Machine Learning Integration**
- **Optimal Dose Prediction**: AI-driven treatment recommendations
- **Growth Rate Forecasting**: Predictive analytics for culture outcomes
- **Parameter Optimization**: Automated condition tuning

### **Comprehensive Cell Line Database**
- **HeLa**: Cervical carcinoma (TP53-null, aggressive)
- **MCF-7**: Breast adenocarcinoma (ER+, hormone-responsive)
- **A549**: Lung carcinoma (KRAS-mutant)
- **HEK293**: Normal embryonic kidney (control line)
- **Jurkat**: T-cell leukemia (suspension culture)

Each cell line includes:
- Cell cycle parameters (phase durations)
- Metabolic rates (glucose/O₂ consumption)
- Drug sensitivity profiles (IC₅₀ values)
- Mechanical properties (stiffness, migration)
- Gene expression signatures

### **Advanced Visualization**
- **Real-Time Cell Culture View**: Live population rendering
- **Growth Curves**: Total and viable cell dynamics
- **Viability Tracking**: Temporal viability analysis
- **Metabolism Dashboard**: Glucose, oxygen, lactate trends
- **Cell Cycle Distribution**: Phase progression over time
- **Spatial Heatmaps**: Microenvironment gradient visualization

---

##

---

## 🛠️ Installation

### **Prerequisites**
- Python 3.8+
- Modern web browser (Chrome, Firefox, Safari, Edge)

### **Backend Setup**

1. **Install Dependencies**
```bash
pip install flask flask-cors numpy scipy
```

2. **Run Backend Server**
```bash
python advanced_cell_backend.py
```

Server will start on `http://127.0.0.1:5000`

### **Frontend Setup**

1. **Open Frontend**
Simply open `nextgen_cell_dynamics.html` in your web browser.

2. **Alternative: Local Server (Optional)**
```bash
# Python 3
python -m http.server 8000

# Then navigate to: http://localhost:8000/nextgen_cell_dynamics.html
```

---

## 📖 Usage Guide

### **1. Select Cell Line**
Choose from 5 well-characterized cell lines with distinct biological properties.

### **2. Configure Environment**
- **Temperature**: 30-42°C (optimal: 37°C)
- **pH**: 6.5-8.0 (optimal: 7.4)

### **3. Design Treatment**
- **No Treatment**: Baseline growth
- **Drug Treatment**: 
  - Select drug class (Taxol, Cisplatin, Doxorubicin, Gemcitabine, Targeted)
  - Set concentration (0-100 μM)
  - View AI-predicted optimal dose (IC₅₀ and recommendations)

### **4. Set Experiment Parameters**
- **Initial Cells**: 100-1000 cells
- **Duration**: 24-168 hours
- **Time Interval**: 0.5h (for computational efficiency)

### **5. Run Simulation**
Click **"Run Simulation"** and monitor progress. The backend will:
- Initialize cell population
- Simulate cell cycle progression
- Calculate drug effects (PK/PD)
- Track metabolic dynamics
- Update microenvironment gradients
- Collect time-series data

### **6. Analyze Results**

**Statistics Dashboard**:
- Viable cell count
- Viability percentage
- Doubling time
- Average health

**Growth Dynamics**: Total vs viable cell trajectories

**Viability**: Temporal viability trends

**Metabolism**: Glucose, oxygen, lactate levels

**Cell Cycle**: Phase distribution (G1/S/G2/M/G0)

**Spatial Heatmap**: Lactate accumulation patterns

---

## 🧪 Example Experiments

### **Experiment 1: Baseline Growth**
```
Cell Line: HeLa
Environment: 37°C, pH 7.4
Treatment: None
Duration: 72h
```
**Expected**: Exponential growth, ~24h doubling time

### **Experiment 2: Drug Dose-Response**
```
Cell Line: MCF-7
Environment: 37°C, pH 7.4
Treatment: Taxol (6.2 μM - at IC₅₀)
Duration: 96h
```
**Expected**: ~50% viability, cell cycle arrest at M phase

### **Experiment 3: Temperature Stress**
```
Cell Line: A549
Environment: 32°C (suboptimal), pH 7.4
Treatment: None
Duration: 72h
```
**Expected**: Reduced growth rate, increased doubling time

### **Experiment 4: Combination Stress**
```
Cell Line: HeLa
Environment: 39°C, pH 7.0
Treatment: Cisplatin (20 μM)
Duration: 48h
```
**Expected**: Severe viability loss, metabolic collapse

---

## 🔬 Scientific Basis

### **Cell Cycle Model**
Based on **Tyson & Novák (2001)** cell cycle models with:
- CDK-cyclin dynamics
- Checkpoint control (DNA damage, metabolic)
- Contact inhibition (Rb pathway)

### **Metabolic Model**
Derived from **Warburg effect** and **oxidative phosphorylation**:
- Glucose → ATP (aerobic glycolysis in cancer)
- Oxygen consumption → mitochondrial respiration
- Lactate production → acidification

### **PK/PD Model**
Standard **two-compartment model**:
- Media compartment (drug administration)
- Intracellular compartment (target site)
- **Hill equation**: E = Emax × [Drug]^n / (IC₅₀^n + [Drug]^n)

### **Drug Sensitivity**
IC₅₀ values from:
- **NCI-60 Cancer Cell Line Screen**
- **Cancer Cell Line Encyclopedia (CCLE)**
- **Genomics of Drug Sensitivity in Cancer (GDSC)**

---

## 🎯 Advanced Features

### **API Endpoints**

```python
# Main simulation
POST /api/simulate
Body: {
  cellLineName: str,
  environment: { temperature: float, pH: float },
  treatment: { type: str, drugClass: str, concentration: float },
  experimentParams: { initialCells: int, duration: float, timeInterval: float }
}

# ML prediction: optimal dose
POST /api/predict/optimal-dose
Body: { cellLineName: str, drugClass: str }

# ML prediction: growth forecast
POST /api/predict/growth
Body: { <simulation_params> }

# Cell line database
GET /api/cell-lines

# Health check
GET /api/health
```

### **Data Export**
Simulation results are returned as JSON time-series:
```json
{
  "time": 24,
  "total": 1000,
  "viable": 950,
  "viability": 95.0,
  "avg_health": 0.85,
  "avg_atp": 0.90,
  "phases": { "G1": 400, "S": 300, "G2": 150, "M": 100, "G0": 0 },
  "glucose": 0.85,
  "oxygen": 0.88,
  "lactate": 0.15
}
```

---

## 🧠 Machine Learning Features

### **1. Optimal Dose Prediction**
Uses cell line sensitivity profiles to recommend:
- **Optimal concentration** for desired effect
- **IC₅₀ value** for reference
- **Expected viability** at recommended dose
- **Clinical considerations**

### **2. Growth Rate Forecasting**
Predicts:
- **Doubling time** under given conditions
- **Final cell count** at experiment end
- **Confidence intervals** (future enhancement)

### **3. Future Enhancements**
- **Deep learning models** trained on real experimental data
- **Multi-objective optimization** (maximize kill, minimize toxicity)
- **Resistance prediction** (probability of developing resistance)

---

## 📈 Performance & Scalability

- **Backend**: Handles 5000+ cells per simulation
- **Frontend**: Renders 500 cells in real-time visualization
- **Simulation Speed**: ~1-2 seconds for 72h culture (dt=0.5h)
- **Memory**: <100MB RAM for typical simulation
- **Concurrency**: Flask threaded mode for multiple users

---

## 🔮 Future Roadmap

### **Phase 2 (Q1 2025)**
- [ ] 3D culture simulation (spheroids)
- [ ] Co-culture support (tumor + immune cells)
- [ ] Drug combination synergy analysis
- [ ] CRISPR perturbation modeling

### **Phase 3 (Q2 2025)**
- [ ] Patient-derived xenograft (PDX) models
- [ ] Multi-omics integration (RNA-seq, proteomics)
- [ ] Clinical trial simulation
- [ ] Real-time experimental feedback (IoT integration)

---

## 🤝 Contributing

This platform is designed for computational biologists, pharmacologists, and drug developers. Contributions welcome for:
- Additional cell lines
- New drug classes
- Validation against experimental data
- Performance optimizations

---

## 📚 References

1. **Tyson, J. J., & Novák, B. (2001)**. Regulation of the eukaryotic cell cycle: molecular antagonism, hysteresis, and irreversible transitions. *Journal of Theoretical Biology*, 210(2), 249-263.

2. **Warburg, O. (1956)**. On the origin of cancer cells. *Science*, 123(3191), 309-314.

3. **Shoemaker, R. H. (2006)**. The NCI60 human tumour cell line anticancer drug screen. *Nature Reviews Cancer*, 6(10), 813-823.

4. **Barretina, J., et al. (2012)**. The Cancer Cell Line Encyclopedia enables predictive modelling of anticancer drug sensitivity. *Nature*, 483(7391), 603-607.

5. **Yang, W., et al. (2013)**. Genomics of Drug Sensitivity in Cancer (GDSC): a resource for therapeutic biomarker discovery in cancer cells. *Nucleic Acids Research*, 41(D1), D955-D961.

---

## 📧 Contact

For questions, bug reports, or collaboration:
- **GitHub Issues**: [Report bugs or request features]
- **Email**: [Your contact]
- **Twitter**: [@YourHandle]

---

## 📝 License

MIT License - see LICENSE file for details

---

**Built with ❤️ for the computational biology community**

*NextGen CellDynamics - Pushing the boundaries of in silico cell culture*
