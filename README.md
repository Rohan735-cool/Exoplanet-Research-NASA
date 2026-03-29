<div align="center">
  <img src="https://img.shields.io/badge/Exoplanet%20Census-%23FF6B6B?style=for-the-badge&logo=nasa&logoColor=white" alt="badge">
  <br><br>
  <h1>🌌 The Exoplanet Census: Fulton Gap & Observational Bias</h1>
  <img src="banner.gif" width="100%" alt="Animated exoplanet radius gap">
  <p><i>Independent analysis of 6,000+ NASA exoplanets revealing photoevaporation's role in the <b>1.5–2.0 R⊕ gap</b>.</i></p>
</div>

[![Stars](https://img.shields.io/github/stars/Rohan735-cool/Exoplanet-Research-NASA)](https://github.com/Rohan735-cool/Exoplanet-Research-NASA)
[![Forks](https://img.shields.io/github/forks/Rohan735-cool/Exoplanet-Research-NASA)](https://github.com/Rohan735-cool/Exoplanet-Research-NASA)
[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB)](https://python.org)

## 📋 Contents
- [🎯 Key Findings](#-key-findings)
- [🛠️ Quick Start](#️-quick-start)
- [📊 Results](#-results)
- [🔭 Live Demo](#-live-demo)

## 🎯 Key Findings
- **Bimodal radius gap** at 1.5–2.0 R⊕ confirms photoevaporation theory.
- Transit methods dominate small-planet detection; RV biased toward massive worlds.
- 6,253 exoplanets analyzed (Oct 2025 NASA data).

## 🛠️ Quick Start
```bash
git clone https://github.com/Rohan735-cool/Exoplanet-Research-NASA
cd Exoplanet-Research-NASA
pip install -r requirements.txt
jupyter notebook Exoplanet_Analysis_1.ipynb
```

**Data**: [NASA PSCompPars (84 header rows)](https://exoplanetarchive.ipac.caltech.edu/)

## 📊 Results

| Plot | Description | Key Insight |
|------|-------------|-------------|
| ![Orbital](Plots/Orbitals.png) | Log orbital period histogram | Hot Jupiters cluster <10 days |
| ![KDE](Plots/KDE.jpg) | Radius density (KDE, bw=0.2) | Dip at 1.5–2.0 R⊕ (red zone) |
| ![Scatter](Plots/Scatter.jpg) | Log radius vs stellar mass | Transit bias for R<4 R⊕ |

## 🔭 Live Demo
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/Rohan735-cool/Exoplanet-Research-NASA/main?urlpath=%2Fdoc%2Ftree%2FExoplanet_Analysis_1.ipynb)
*Click to run analysis in-browser (no install needed!)*

## 🌟 Why This Matters
The Fulton Gap suggests most sub-Neptunes lose atmospheres near their stars, leaving rocky cores. This analysis quantifies **observational biases** across 4 detection methods.

## 🤝 Contribute
1. Fork → Fix → PR
2. Issues welcome: data updates, ML predictions, 3D orbits
3. Star if this sparks your exoplanet curiosity! ⭐


<div align="center">

**🔭 This research uses data from the**  
[![NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/images/export.png)](https://exoplanetarchive.ipac.caltech.edu/)  
**operated by Caltech under NASA contract.**

</div>
