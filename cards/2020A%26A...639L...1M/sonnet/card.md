# Ongoing flyby in the young multiple system UX Tauri

`2020A&A...639L...1M` | Astronomy and Astrophysics 2020 | first author: Ménard, F. | arXiv: 2006.02439 | DOI: 10.1051/0004-6361/202038356

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Is the spiral structure in the UX Tau A disk caused by a recent flyby of UX Tau C or by a bound companion orbit?  
  > "We now test the hypothesis that the spirals observed UX Tau A are due to the dynamical response of the disk to a gravitational perturbation by UX Tau C." (3 Hydrodynamical modeling of UX Tau)
- Target **UX Tau (A, B, C)**: coordinates _not stated_; z/distance 147±2 pc  
  > "It is located in the Taurus molecular cloud at d = $147\pm2$ pc (cite: GAIA-DR2-2018)." (Introduction); distance from Gaia DR2  
  > "It is located in the Taurus molecular cloud at d = $147\pm2$ pc (cite: GAIA-DR2-2018)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00888.S
- bands: Band 7 (0.84 mm) continuum; 12CO (3-2)  
  > "The left insert is a zoom of the Band 7 (0.84mm) continuum emission showing the ringed structure of the disk at that frequency." (7 ALMA archival data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Continuum 0.20''x0.17'' at PA -21.0 deg; CO 0.24''x0.18'' at PA -24.7 deg  
  > "We imaged the CO line using a channel width of 0.24413 MHz and a natural weighting resulting in a 0.24$''$ $\times$ 0.18$''$ beam at PA $=$ -24.7$^\circ$." (7 ALMA archival data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 August 10  
  > "The observation took place on 2016 August 10." (7 ALMA archival data)
- pi or archival as stated: Archival, program PI Akiyama  
  > "presented archival deep and high-resolution data obtained by program 2015.1.00888.S (PI Akiyama)." (7 ALMA archival data)
- Line: 12CO J=3-2 (not stated)
- Other facility **VLT/SPHERE (IRDIS)**: J- and H-band polarized intensity images showing scattered-light spirals  
  > "We obtained three different NIR differential polarization imaging data sets (DPI; see (cite: vanHolstein2020; deBoer2020)) with the IRDIS camera (cite: Dohlen2008) of SPHERE" (2.1 Near-infrared high-contrast imaging with SPHERE)
- External data: Disk inclination 40 deg and PA 167 deg from continuum fit  
  > "From the same continuum data, (cite: Francis2020) fit an inclination i$_{\mathrm d}=40\ensuremath{^\circ}$ at a PA = 167$^\circ$." (7 ALMA archival data) [from Francis & van der Marel 2020 (cite: Francis2020)]
- External data: Disk mass of UX Tau A 0.05 Msun  
  > "assuming a total disk mass of $0.05~M_\odot$ (cite: Akeson2019)" (3 Hydrodynamical modeling of UX Tau) [from Akeson et al. 2019 (cite: Akeson2019)]
- External data: Stellar mass ratio q between 0.08 and 0.22  
  > "the mass ratio $q=M_\mathrm{C}/M_\mathrm{A}$ ranges between 0.08 and 0.22 (cite: Kraus2009; Zapata2020)" (3 Hydrodynamical modeling of UX Tau) [from Kraus2009; Zapata2020]
- Simulation/model as data: Phantom SPH simulations of bound (B-) and parabolic flyby (F-) runs  
  > "These runs are labeled B- and F-, respectively." (3 Hydrodynamical modeling of UX Tau)

## Processing

### Calibration

- pipeline or manual: Supplied reduction script  
  > "We performed our own reduction using the supplied reduction script and version 4.7.2 of the CASA software" (7 ALMA archival data)
- casa version: CASA 4.7.2  
  > "We performed our own reduction using the supplied reduction script and version 4.7.2 of the CASA software" (7 ALMA archival data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Three rounds of phase-only, solints inf, 60s, 40s; ~2x gain in RMS and dynamic range  
  > "three rounds of phase-only self-calibration using successively shorter solution intervals ($\infty$, 60s, 40s)" (7 ALMA archival data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Continuum: Briggs (robust not stated); CO: natural  
  > "We imaged the continuum visibilities using Briggs weighting resulting in a 0.20$''$ $\times$ 0.17$''$ beam at PA $=$ -21.0$^\circ$." (7 ALMA archival data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA; self-cal solutions applied  
  > "we subtracted the continuum data using the uvcontsub routine of CASA, and applied the self-cal solution to the resulting visibilities" (7 ALMA archival data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Continuum 0.20''x0.17''; CO 0.24''x0.18''  
  > "natural weighting resulting in a 0.24$''$ $\times$ 0.18$''$ beam at PA $=$ -24.7$^\circ$" (7 ALMA archival data)
- final rms: _not stated_

### Inherited from earlier work

- Same ALMA data set as earlier papers  
  > "ALMA CO observations of UX Tauri were presented in (cite: Francis2020) and (cite: Zapata2020). We used the same data set." (2.2 ALMA archival data) [from Francis2020; Zapata2020]
- SPHERE reduction with IRDAP pipeline  
  > "The final data reduction was performed with the IRDAP pipeline[^1] presented in (cite: vanHolstein2020)." (2.1 Near-infrared high-contrast imaging with SPHERE) [from vanHolstein2020]
- Disk orientation set following earlier analysis  
  > "following the analysis of (cite: Francis2020)" (3 Hydrodynamical modeling of UX Tau) [from Francis2020]

### Not stated but needed to reproduce (our reading)

- Briggs robust value for continuum
- Image size and cell size
- CO moment map clipping thresholds and channel selection
- Line-free channels for uvcontsub
- Final rms values
- Phantom setup files and random seeds
- Initial disk temperature profile and aspect ratio

## Analysis recipe

1. **Reduce and self-calibrate ALMA data**: Supplied reduction script in CASA 4.7.2, three rounds phase-only self-cal  
  > "We performed our own reduction using the supplied reduction script and version 4.7.2 of the CASA software" (7 ALMA archival data)
   - software: CASA
   - parameter: solints inf, 60s, 40s  
  > "successively shorter solution intervals ($\infty$, 60s, 40s)" (7 ALMA archival data)
   - fitting: _not stated_
   - validation: RMS and dynamic range improved ~2x  
  > "resulting in a gain of a factor $\sim$2 in RMS noise and dynamic range" (7 ALMA archival data)
2. **Image continuum and CO and compare with SPHERE**: Briggs continuum imaging; uvcontsub then natural-weighted CO cube; moment 0 and peak velocity maps compared with scattered-light spirals  
  > "The CO line emission and the dust continuum emission maps are shown in Fig. [6](#fig:ALMAco)." (7 ALMA archival data)
   - software: CASA
   - parameter: channel width 0.24413 MHz  
  > "We imaged the CO line using a channel width of 0.24413 MHz" (7 ALMA archival data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Hydrodynamical simulations of flyby vs bound orbit**: SPH Phantom runs with 500000 particles, B- and F-runs compared qualitatively with observed spirals  
  > "The disk is modeled using 500 000 gas SPH particles and assuming a total disk mass of $0.05~M_\odot$ (cite: Akeson2019)." (3 Hydrodynamical modeling of UX Tau)
   - software: Phantom
   - parameter: Rin=10 au, Rout=60 or 90 au, Rp=100 au, omega=-130 deg, q=0.2  
  > "For F-runs, we consider prograde flybys with $R_\mathrm{p}=100$ au and $\omega=-130\ensuremath{^\circ}$ as well." (3 Hydrodynamical modeling of UX Tau)
   - assumption: Orbit in plane of sky, 40 deg to disk midplane; masses 1.0 and 0.2 Msun; alpha_SS~0.005  
  > "The masses of the primary star and the perturber are set to 1.0 M$_\odot$ and 0.2 M$_\odot$, for a mass ratio $q=0.2$" (3 Hydrodynamical modeling of UX Tau)
   - fitting: _not stated_
   - validation: Qualitative match to observed spirals  
  > "A prograde flyby (e.g., panel F90-a100 in Fig. [3](#fig:sims)) provides an excellent qualitative match to the ensemble of observations." (5 Concluding remarks)

## Software

- **CASA** 4.7.2: ALMA reduction, self-calibration, imaging, uvcontsub  
  > "version 4.7.2 of the CASA software" (7 ALMA archival data)
- **Phantom** : SPH simulations  
  > "smoothed particle hydrodynamics (SPH) Phantom code (cite: Price2018b)" (3 Hydrodynamical modeling of UX Tau)
- **IRDAP** : SPHERE polarimetric reduction  
  > "The final data reduction was performed with the IRDAP pipeline" (2.1 Near-infrared high-contrast imaging with SPHERE)
- **splash** : Adaptive de-noising of SPHERE images  
  > "implemented in the splash software (cite: Price2007)" (8 Novel DE-NOISING procedure)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Projected separation of UX Tau C from A | 2.70 | 0.02 | arcsec | 0 | UX Tau C has a projected separation of 2.70$''$$\pm$0.02$''$ at PA = 181.5$^\circ$$\pm$1.0$^\circ$ |
| Inclination of UX Tau C disk | >=60 | not stated | deg | 0 | SPHERE marginally resolved the disk of UX Tau C and the inclination is i$\geq$60$^\circ$. |
| Orbital period in simulations | ~7000 | not stated | yr | 3 | The orbital period is of order 7000 yr in our simulations. |

## Qualitative findings

- Scattered-light spirals of UX Tau A have counterparts in 12CO; disks of A and C have misaligned velocity gradients  
  > "The rotational velocity gradients of the two disks are misaligned." (5 Concluding remarks)

## Claim tuples

- H: UX Tau C is a recent flyby perturber rather than a bound companion | E: SPH bound and parabolic runs compared with SPHERE and ALMA CO spirals | R: Prograde flyby gives prominent long-lived spirals; bound orbits truncate disk and spirals fade after a few orbits | F: Flyby scenario favoured | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Bound orbit gives a decent match only during the first few orbits  
  > "A bound orbit solution can also provide a decent qualitative match, but only during the first few orbits." (5 Concluding remarks)
- How they decided it was enough: _not stated_
- Limitation (authors): Simulations cannot reproduce the outer southwest CO spiral; orbital geometry is degenerate  
  > "Our simulations are unable to reproduce the outer spiral located to the southwest" (4.1 UX Tau C: Bound companion or flyby)
- Caveat (inferred, ours): Only qualitative simulation comparison; no quantitative fit
- Caveat (inferred, ours): Orbit assumed in plane of sky
- Caveat (inferred, ours): Limited exploration of parameter space

## Reproducibility

- Data public (paper): Archival ALMA program 2015.1.00888.S  
  > "presented archival deep and high-resolution data obtained by program 2015.1.00888.S (PI Akiyama)." (7 ALMA archival data)
- Products in archive: _not stated_
- Missing: Phantom setup parameters
- Missing: Imaging parameters
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Archival data public, but ALMA analysis is minor and mostly qualitative; imaging details are sparse.
- Rediscovery candidate: no, Results are qualitative and simulation-based.

## Links

- Method: van Holstein et al. 2020 (IRDAP SPHERE reduction)
- Companion: Francis & van der Marel 2020; Zapata et al. 2020 (Same ALMA data set)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 38,
  "rate": 0.535
 },
 "evidence_ok": true
}
```
