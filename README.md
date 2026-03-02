# Dynamic Response and Stability Analysis of High Earth-Rockfill Dam

This repository contains FLAC3D numerical simulation scripts for the **dynamic response and stability analysis of a high earth-rockfill dam with deep overburden in a strong earthquake area**.

## Project Overview

The project performs seismic analysis of a high earth-rockfill dam constructed on deep overburden using the two-dimensional explicit finite-difference code FLAC3D. The analysis covers:

- **Dynamic response analysis**: acceleration, velocity, and displacement response of the dam body under strong earthquake loading
- **Seismic stability analysis**: time-history of the slope factor of safety (FOS) computed by cyclic strength-reduction during shaking

## File Description

| File | Description |
|------|-------------|
| `dynamic_analysis.dat` | Main FLAC3D dynamic analysis script |
| `pointmirror.txt` | History monitoring point definitions (crest, slopes, base) |
| `000slopeygdyna.txt` | Dynamic slope stability (FOS) calculation via strength reduction |
| `taft2.txt` | Taft 1952 earthquake horizontal acceleration time series (scaled, dt=0.02 s) |

## Analysis Workflow

1. **Pre-processing** – Build static model and apply pore-water pressure (`Model_03_pwater.sav` generated separately).
2. **Dynamic configuration** – Switch to dynamic mode, apply quiet (absorbing) boundaries on lateral and base faces.
3. **Seismic input** – Apply the Taft acceleration record (amplitude ×2.0) at the model base as a free-field boundary condition.
4. **Cyclic FOS** – Every 0.1 s of dynamic time the strength-reduction factor of safety is evaluated and recorded.
5. **Post-processing** – Saved state files (`*.sav`) and output tables are used for result visualisation.

## Key Parameters

| Parameter | Value |
|-----------|-------|
| Local damping ratio | 0.05 (ξ = 5 %) |
| Seismic record | Taft 1952 (scaled ×2.0) |
| Duration | 15 s |
| Time step (input) | 0.02 s |
| FOS evaluation interval | 0.1 s |

## Requirements

- FLAC3D 3.x or later (Itasca Consulting Group)
- Pre-computed static model save file `Model_03_pwater.sav`
