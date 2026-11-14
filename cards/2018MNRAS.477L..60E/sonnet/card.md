# Giant galaxy growing from recycled gas: ALMA maps the circumgalactic molecular medium of the Spiderweb in [C I]

`2018MNRAS.477L..60E` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Emonts, B. H. C. | arXiv: 1802.08742 | DOI: 10.1093/mnrasl/sly034

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Is the cold molecular CGM of the Spiderweb Galaxy metal-rich and linked to in-situ star formation, and how do its [C I] and CO excitation compare to proto-cluster galaxies?  
  > "Here we present observations sensitive to low-surface-brightness extended emission of atomic carbon, [C i] $^{3}$P$_{1}$-$^{3}$P$_{0}$ (hereafter [C i]) in the CGM of the Spiderweb Galaxy." (1 Introduction)
- Target **Spiderweb Galaxy (MRC 1138-262)**: coordinates _not stated_; z/distance z = 2.2 (z=2.1612 velocity reference); D_L = 17309 Mpc  
  > "We assume H$_{0} = 71$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_\textrm{M} = 0.27$ and $\Omega_{\Lambda} = 0.73$, i.e., 8.4 kpc/$^{\prime\prime}$ and $D_{\rm L} = 17309$ Mpc at z = 2.2 (EM16)." (1 Introduction); distance from cosmology H0=71, OmegaM=0.27, OmegaL=0.73 (EM16)  
  > "We assume H$_{0} = 71$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_\textrm{M} = 0.27$ and $\Omega_{\Lambda} = 0.73$, i.e., 8.4 kpc/$^{\prime\prime}$ and $D_{\rm L} = 17309$ Mpc at z = 2.2 (EM16)." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00851.S
- bands: _not stated_
- frequencies and spectral setup: Two adjacent 1.875 GHz SPWs on [CI] (~155.7 GHz) and two on CO(4-3) (~145.8 GHz)  
  > "We placed two adjacent spectral windows of 1.875 GHz on [C i] $^{3}$P$_{1}$-$^{3}$P$_{0}$ at $\nu_{\rm obs}$ $\sim$ 155.7 GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m, compact configuration C36-1  
  > "in its most compact 12m configuration (C36-1; baselines 15$-$161m)" (2 Observations)
- configurations: _not stated_
- baselines: 15-161 m  
  > "in its most compact 12m configuration (C36-1; baselines 15$-$161m)" (2 Observations)
- angular resolution: 2.3" x 1.5", PA 73.4 deg  
  > "The synthesized beam is 2.3$^{\prime\prime}$ $\times$1.5$^{\prime\prime}$ with PA=73.4$^{\circ}$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.085 mJy/beam/channel (60 km/s)  
  > "The resulting noise is 0.085 mJy beam$^{-1}$ channel$^{-1}$." (2 Observations)
- time on source: 1.8 hrs ALMA; ~90 hrs per pointing ATCA  
  > "We observed the Spiderweb for 1.8 hrs on-source during ALMA cycle-3 on 16 Jan 2016" (2 Observations)
- observing dates: 16 Jan 2016 (ALMA)  
  > "during ALMA cycle-3 on 16 Jan 2016" (2 Observations)
- pi or archival as stated: _not stated_
- Line: [C I] 3P1-3P0 (492.16 GHz)
- Line: CO 4-3 (461.04 GHz)
- Other facility **ATCA**: CO(1-0) 2-pointing mosaic at ~36.5 GHz  
  > "Using the ATCA, we made a 2-pointing mosaic with an on-source time of $\sim$90 hrs per pointing at $\nu_{\rm obs}$ $\sim$ 36.5 GHz to observe CO(1-0)." (2 Observations)
- External data: [C I] 3P2-3P1 high-resolution ALMA data, tapered and smoothed for comparison  
  > "We compare our [C i] $^{3}$P$_{1}$-$^{3}$P$_{0}$ detection with [C i] $^{3}$P$_{2}$-$^{3}$P$_{1}$ data from (cite: gul16)" (3 Results) [from Gullberg et al. 2016 (cite: gul16)]
- External data: High-resolution VLA CO(1-0) data tapered to ALMA resolution  
  > "we tapered existing high-resolution VLA data (EM16) to the spatial resolution of our ALMA data." (Table 1 footnote) [from Emonts et al. 2016 (cite: emo16)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We imaged our field using natural weighting out to $\sim$33$^{\prime\prime}$" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: binned to 30 km/s, Hanning smoothed to 60 km/s  
  > "We binned the data to 30 km s$^{-1}$ channels and cleaned signal $\geq$1 mJy bm$^{-1}$. We then Hanning smoothed the data to a resolution of 60 km s$^{-1}$." (2 Observations)
- final beam: 2.3" x 1.5" PA 73.4 deg  
  > "The synthesized beam is 2.3$^{\prime\prime}$ $\times$1.5$^{\prime\prime}$ with PA=73.4$^{\circ}$." (2 Observations)
- final rms: 0.085 mJy/beam/channel  
  > "The resulting noise is 0.085 mJy beam$^{-1}$ channel$^{-1}$." (2 Observations)

### Inherited from earlier work

- ATCA observing strategy and MIRIAD data reduction  
  > "The observing strategy and data reduction in MIRIAD followed EM16." (2 Observations) [from EM16 (Emonts et al. 2016, cite: emo16)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- Calibrators and flux scale
- Clean mask details, cell and image size
- Continuum subtraction and line-free channels
- Taper parameters for the 8 arcsec beam
- Spectral extraction apertures
- Exact CO(1-0) intensity combination weights

## Analysis recipe

1. **Image ALMA cubes**: Bin to 30 km/s, clean, Hanning smooth to 60 km/s, natural weighting  
  > "We binned the data to 30 km s$^{-1}$ channels and cleaned signal $\geq$1 mJy bm$^{-1}$." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Separate CGM from central radio galaxy**: Taper to ~8" beam, extract spectrum, subtract central radio galaxy line profile  
  > "We therefore taper the ALMA data to a beam of $\sim$8$^{\prime\prime}$ ($\sim$70 kpc), which covers the full CO(1-0) halo." (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive masses and abundance**: M_H2 from CO(1-0) with alpha_CO; [CI] mass with Tex~30 K; X[CI]/XH2 = M[CI]/(6 MH2)  
  > "This results in a [C i] abundance of $X_\mathrm{[CI]}$/$X_\mathrm{H_2}$ = M$_\mathrm{[CI]}$/(6M$_\mathrm{H_2}$)" (4 Discussion)
   - assumption: alpha_CO=4 scaling; Tex~30 K  
  > "assuming T$_\mathrm{ex}$$\sim$30 K (cite: wei05)" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA data reduction  
  > "The ALMA data were reduced in CASA" (2 Observations)
- **MIRIAD** : ATCA data reduction  
  > "The observing strategy and data reduction in MIRIAD followed EM16." (2 Observations)
- **LINMOS** : combining the two ATCA pointings  
  > "combined them using the task LINMOS" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CGM M_H2 | 1.0e11 (alpha_CO/4) | 0.4e11 | Msun | 3 | M$_\mathrm{H_2}$ $\sim$ 1.0$\pm$0.4$\times$10$^{11}$($\alpha_\mathrm{CO}$/4) M$_{\odot}$ |
| CGM M_[CI] | 8.9e6 | 1.4e6 | Msun | 3 | M$_\mathrm{[CI]}$$\sim$8.9$\pm$1.4$\times$10$^{6}$ M$_{\odot}$ |
| CGM X[CI]/XH2 | 1.5e-5 (4/alpha_CO) | 0.6e-5 | dimensionless | 3 | $\sim$ 1.5$\pm$0.6$\times$10$^{-5}$ (4/$\alpha_\mathrm{CO}$) |
| [CI] 2-1/1-0 ratio of MRC 1138-262 | 0.62 | not stated | dimensionless | 0 | $L^{\prime}_\mathrm{[CI]2 \rightarrow 1}$/$L^{\prime}_\mathrm{[CI]1 \rightarrow 0}$ $\sim$ 0.62 |

## Qualitative findings

- [CI] and CO(4-3) detected across ~50 kpc in CGM, ~30% of total flux on 17-70 kpc scales  
  > "$\sim$30$\%$ of the total flux is spread on 17-70 kpc scales" (3 Results)

## Claim tuples

- H: The molecular CGM is metal-rich and linked to in-situ star formation | E: [CI], CO(4-3), CO(1-0) ratios and carbon abundance in CGM vs proto-cluster galaxies | R: CGM ratios similar to proto-cluster galaxies; X[CI]/XH2 close to Milky Way | F: Molecular CGM is metal-rich and not diffuse | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: CGM gas mainly tidally stripped from proto-cluster galaxies is unlikely  
  > "it is unlikely that the cold CGM consists mainly of gas that is currently being tidally stripped from proto-cluster galaxies" (4.1 Mixing in the CGM)
- How they decided it was enough: _not stated_
- Limitation (authors): Beam-smearing errors prevented improving ATCA CO(1-0) over earlier work  
  > "This prevented us from improving the image of the faint CO(1-0) in the halo compared with EM16." (2 Observations)
- Caveat (inferred, ours): alpha_CO assumed
- Caveat (inferred, ours): Central profile subtraction uncertain
- Caveat (inferred, ours): CO(1-0) beam mismatch

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version
- Missing: calibration details
- Missing: tapering and aperture details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Archive data are available but processing details are sparse and the CO(1-0) data are ATCA.
- Rediscovery candidate: no, Recipe is incomplete and relies on ATCA and VLA data.

## Links

- Companion: Emonts et al. 2016 (cite: emo16) (Original CO(1-0) detection of molecular halo)

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 28,
  "rate": 0.444
 },
 "evidence_ok": true
}
```
