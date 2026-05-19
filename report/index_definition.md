# Affordable Liveability Index (ALI)

**Goal:** Develop a composite indicator to compare countries on overall liveability **relative to cost pressure**.

**Unit of analysis:** Countries  
**Reference year:** 2022 (single year cross-sectional index)

## Conceptual model (pillars)
ALI is built from three sub-indices:

1. **Cost Pressure (CP)** *(higher CP = worse affordability)*  
2. **Economic Opportunity (EO)** *(higher EO = better opportunity)*  
3. **Quality of Life & Environment (QLE)** *(higher QLE = better living conditions)*

The final ALI score rewards high opportunity and quality of life, and penalizes high cost pressure.

## Weighting (baseline)
- Equal pillar weights: CP 1/3, EO 1/3, QLE 1/3
- Equal weights for indicators within each pillar

I will later run a sensitivity check using alternative weights and compare rank stability.

## Normalisation
Min–max scaling to [0, 100] after applying “direction” rules:
- Indicators where higher is worse (e.g. pollution, unemployment, cost pressure) are reverse-coded.