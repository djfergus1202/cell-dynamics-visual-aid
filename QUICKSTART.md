# 🚀 Quick Start Guide - NextGen CellDynamics

Get up and running in **5 minutes**!

---

## Step 1: Install Dependencies (30 seconds)

```bash
pip install flask flask-cors numpy scipy
```

Or use the requirements file:
```bash
pip install -r requirements.txt
```

---

## Step 2: Start Backend Server (10 seconds)

```bash
python advanced_cell_backend.py
```

You should see:
```
======================================================================
Advanced Cellular Dynamics Backend v2.0
======================================================================
Features:
  ✓ Detailed cell cycle modeling (G1/S/G2/M checkpoints)
  ✓ Spatial nutrient/oxygen gradients
  ✓ Multi-compartment PK/PD
  ✓ Cell-cell interactions
  ✓ Machine learning prediction
  ✓ Metabolic dynamics
======================================================================

Server starting on http://127.0.0.1:5000
```

---

## Step 3: Open Frontend (5 seconds)

**Option A: Direct File**
- Simply double-click `nextgen_cell_dynamics.html`
- OR right-click → Open With → Your Browser

**Option B: Local Server (optional)**
```bash
python -m http.server 8000
# Then visit: http://localhost:8000/nextgen_cell_dynamics.html
```

---

## Step 4: Run Your First Simulation! (2 minutes)

### **Quick Test: HeLa Growth**

1. **Select Cell Line**: Leave as "HeLa" (default)
2. **Environment**: 37°C, pH 7.4 (defaults are optimal)
3. **Treatment**: "No Treatment" (default)
4. **Experiment**:
   - Initial Cells: 500
   - Duration: 72 hours
5. **Click**: "▶️ Run Simulation"

⏱️ Wait ~2 seconds for results

**Expected Results**:
- Final viable cells: ~2,000-2,500
- Viability: >95%
- Doubling time: ~24h
- You'll see exponential growth curves!

---

### **Advanced Test: Drug Treatment**

1. **Cell Line**: Switch to "MCF-7" (breast cancer)
2. **Environment**: Keep at 37°C, pH 7.4
3. **Treatment**: 
   - Type: "Drug Treatment"
   - Class: "Taxol (Microtubule Inhibitor)"
   - Concentration: **6.2 μM** (this is the IC₅₀)
4. **Duration**: 96 hours
5. **Run Simulation**

**Expected Results**:
- ~50% cell death
- Viability drops to ~50%
- Cell cycle arrest (M phase accumulation)
- Watch metabolism charts show stress!

---

## Step 5: Validate Installation (optional, 3 minutes)

Run the comprehensive test suite:

```bash
python validate_system.py
```

This will test:
- ✅ Server connectivity
- ✅ Cell line database
- ✅ Baseline growth
- ✅ Drug treatments
- ✅ ML predictions
- ✅ Stress conditions
- ✅ Performance benchmarks

---

## 🎯 Pro Tips

### **Explore All Charts**
Click the tabs in the visualization panel:
- **Growth Dynamics**: Total vs viable cells
- **Viability**: Temporal trends
- **Metabolism**: Glucose, oxygen, lactate
- **Cell Cycle**: Phase distribution

### **Try ML Predictions**
When you select drug treatment, the system automatically shows:
- 🎯 Optimal dose recommendation
- 📊 IC₅₀ value for the cell line
- 💡 Expected outcome

### **Stress Testing**
Try extreme conditions:
- Temperature: 32°C or 40°C
- pH: 7.0 or 7.8
- High drug doses: 50-100 μM

Watch how cells respond realistically!

---

## 📊 Understanding Results

### **Statistics Dashboard**
- **Viable Cells**: Living, functional cells
- **Viability %**: Percentage of cells alive
- **Doubling Time**: How fast culture grows
- **Avg Health**: Overall cell condition (0-100%)

### **Growth Curve**
- **Blue line**: Total cell count
- **Green line**: Viable cells only
- Gap = dead cells being cleared

### **Metabolism Charts**
- **Glucose**: Nutrient availability (↓ = depletion)
- **Oxygen**: O₂ levels (↓ = hypoxia)
- **Lactate**: Waste accumulation (↑ = acidification)

### **Cell Cycle**
- **G1** (blue): Growth phase
- **S** (green): DNA synthesis
- **G2** (yellow): Preparation for division
- **M** (purple): Mitosis
- **G0** (gray): Quiescent/arrested

---

## 🔧 Troubleshooting

### **"Cannot connect to backend"**
✅ Make sure backend is running:
```bash
python advanced_cell_backend.py
```

### **Simulation takes too long**
✅ Reduce duration or increase time interval:
- Duration: Try 48h instead of 168h
- Time interval: Use 1.0h instead of 0.5h

### **Charts not showing**
✅ Click "Run Simulation" first to generate data
✅ Try refreshing the browser

### **Port already in use**
✅ Change backend port in code:
```python
app.run(debug=True, port=5001)  # Use 5001 instead
```
Then update frontend API_BASE to match.

---

## 🎓 Learn More

**Documentation**: See `README.md` for comprehensive guide

**Examples**: 
```python
# Example 1: Temperature stress
Cell Line: HEK293
Temperature: 32°C
Duration: 72h
Result: Slower growth

# Example 2: Drug combination (coming soon)
Cell Line: A549
Drug: Cisplatin 15 μM + Gemcitabine 20 μM
Result: Synergistic killing
```

**Validation**: Run `validate_system.py` for detailed tests

---

## 📈 Next Steps

1. ✅ Run baseline experiments for all 5 cell lines
2. ✅ Test each drug class at different concentrations
3. ✅ Create dose-response curves
4. ✅ Compare drug sensitivities across cell lines
5. ✅ Explore environmental stress effects

---

## 🆘 Need Help?

- **Documentation**: `README.md`
- **Validation**: `python validate_system.py`
- **API Reference**: Check `README.md` → API Endpoints section

---

**🎉 You're ready! Start simulating advanced cell cultures now!**

*NextGen CellDynamics - Making computational biology accessible*
