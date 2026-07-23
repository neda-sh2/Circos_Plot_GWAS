# Circos Plot Visualization of GWAS Association Data

## Overview
This project builds an interactive, multi-track Circos-style genome visualization from raw GWAS association data using PCircos, a Python/Plotly-based reimplementation of the classic Circos genome plotting tool. It covers the full workflow from raw data to rendered plot, including the data wrangling step that's often the hardest part of using specialized bioinformatics visualization tools.

## Biological Question
How can genome-wide association results and variant density be displayed together on a single, interactive circular genome plot, making patterns across chromosomes easier to spot at a glance?

## Data
- **GWAS association results** (chromosome, position, p-value)  
  Download: `wget https://raw.githubusercontent.com/phagenomics/kgi-demo/main/AssocDemo.txt`
- **PCircos demo data and configuration templates** (bundled with the cloned repository)

Data downloads automatically when running the notebook; PCircos is cloned directly from GitHub.

## Methods & Tools

**Language:** Python 3.10+ with command-line tools (bash, awk, grep)

| Tool | Purpose |
|---|---|
| PCircos | Circular genome plot rendering (Plotly-based) |
| `awk` / `grep` / `sort` | Reformatting raw GWAS output into PCircos's required track format |
| `pandas` | General data handling |
| JSON | Plot configuration |

**Pipeline:**
1. Clone and install PCircos and its plotting dependencies
2. Validate the tool using its bundled demo configuration
3. Transform raw GWAS data into PCircos's tab-separated scatter and heatmap track formats
4. Write a custom JSON configuration combining multiple data tracks
5. Render the final interactive Circos plot

## Key Results
- Successfully reformatted standard GWAS output (chromosome, position, p-value) into the chromosome-prefixed track format required by Circos-style tools
- Built a multi-track plot combining a p-value scatter track with two variant density heatmap tracks
- Demonstrated that PCircos's Plotly backend enables interactive hover tooltips, an improvement over static Circos output

## How to Run

**Option 1 — Google Colab (recommended)**
1. Upload `Circos_Plot_GWAS.ipynb` to Google Colab
2. Run all cells top to bottom — PCircos is cloned and data downloaded automatically

**Option 2 — Local environment**
```bash
git clone https://github.com/yourusername/circos-gwas-visualization
cd circos-gwas-visualization
pip install -r requirements.txt
jupyter notebook Circos_Plot_GWAS.ipynb
```

**Note:** PCircos pins several dependencies to older versions (e.g., `plotly==3.6.1`, `dash==0.39.0`). These may conflict with newer packages in your environment — running in a fresh virtual environment or Colab session is recommended. Additionally, the exact JSON schema for combining multiple tracks should be verified against `config/default_params.json` in the cloned PCircos repository, as field names can be version-sensitive.

## Project Structure
```
circos-gwas-visualization/
├── README.md
├── Circos_Plot_GWAS.ipynb
└── requirements.txt
```
