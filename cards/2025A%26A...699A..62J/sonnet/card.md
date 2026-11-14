# ALMA observation of an evolving magnetized corona in the radio-quiet changing-state active galactic nucleus NGC 1566

`2025A&A...699A..62J` | Astronomy and Astrophysics 2025 | first author: Jana, Arghajit | arXiv: 2505.13242 | DOI: 10.1051/0004-6361/202554491

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What is the origin of the mm continuum emission in the changing-state AGN NGC 1566, and how does it vary with X-ray flux and accretion state?  
  > "We investigate the variability and origin of the mm emission and its relation to the accretion state." (Introduction)
- Target **NGC 1566**: coordinates _not stated_; z/distance z = 0.005; 17.9 Mpc  
  > "NGC 1566, a nearby (z =0.005) CSAGN, located at a distance of $17.9$ Mpc (cite: koss2022)" (Introduction); distance from koss2022 (BASS)  
  > "NGC 1566, a nearby (z =0.005) CSAGN, located at a distance of $17.9$ Mpc (cite: koss2022)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00474.S, 2015.1.00925.S, 2017.1.00392.S, 2021.1.01150.S, 2023.1.01182.S
- bands: Band 6 (230 GHz), eight epochs 2014-2023  
  > "ALMA observed NGC 1566 in Band 6 (230 GHz) across eight epochs between 2014 and 2023." (2 Observation and data analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam sizes 0.2'' to 7.3'' (~20-640 pc)  
  > "beam sizes ranging from $0.2''$ to $7.3''$, corresponding to physical scales of $\sim 20-640$ pc" (2 Observation and data analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014-06-29 to 2023-12-15  
  > "2014-06-29" (Table 1)
- pi or archival as stated: archival, publicly available  
  > "All the data used in the paper are publicly available." (DATA AVAILABILITY)
- Other facility **Swift/BAT**: 14-150 keV X-ray fluxes  
  > "The $14-150$ keV X-ray fluxes were obtained from the $14-195$ keV or $15-50$ keV *Swift*/BAT count rate" (2 Observation and data analysis)
- Other facility **Swift/XRT**: 2-10 keV fluxes  
  > "The $2-10$ keV fluxes were obtained from spectral analysis of $0.5-10$ keV *Swift*/XRT observations." (2 Observation and data analysis)
- Other facility **WISE, ASAS-SN, Swift/UVOT**: MIR, optical, UV light curves  
  > "We obtained mid-infrared (MIR) lightcurves from WISE in W1 (3.4 $\mu m$) and W2 (4.6 $\mu m$) band from IPAC." (Multi-wavelength observations)
- External data: Eddington-ratio dependent bolometric correction  
  > "The bolometric luminosity ($L_{\rm bol}$) was calculated using Eddington ratio ($\lambda_{\rm Edd}$) dependent bolometric correction factors ($\kappa_{\rm 14-195~keV}$) of (cite: Gupta2024)." (2 Observation and data analysis) [from (cite: Gupta2024)]
- External data: UVW2 host galaxy flux  
  > "The host galaxy flux was taken from (cite: Gupta2024)." (Multi-wavelength observations) [from (cite: Gupta2024)]
- External data: X-ray corona size 20-40 Rg  
  > "The size of the X-ray corona ($R_{\rm X}$) is estimated to be $R_{\rm X}\sim 20-40$ $R_{\rm g}$ from the broadband X-ray spectral study of NGC 1566 (cite: AJ2021)" (3.3.4 Synchrotron emission in X-ray corona) [from (cite: AJ2021)]

## Processing

### Calibration

- pipeline or manual: Archival data calibrated with scriptForPI.py  
  > "The data were calibrated using python script `scriptForPI.py` in appropriate CASA version." (ALMA data reduction)
- casa version: CASA 6.5.4.9  
  > "The data were processed using CASA version 6.5.4.9 and the ALMA Pipeline version 2020.1.0.40" (2 Observation and data analysis)
- pipeline version: ALMA Pipeline 2020.1.0.40  
  > "The data were processed using CASA version 6.5.4.9 and the ALMA Pipeline version 2020.1.0.40" (2 Observation and data analysis)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% added to all data  
  > "We have included an error of $10\%$ in all data, as recommended in the ALMA proposer’s guide." (2 Observation and data analysis)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "First, using CASA task `tclean`, we generated clean images with appropriate cell sizes" (ALMA data reduction)
- deconvolver: _not stated_
- weighting robust: briggs, robust=0.5  
  > "weighting = briggs (robust=0.5) and original beam sizes" (ALMA data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: only continuum channels used  
  > "For our analysis, we only considered the channels with continuum emissions for." (2 Observation and data analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: images also made at common beam 7.31'' x 4.96''  
  > "we made their final clean images with a same beam size of $7.31'' \times 4.96''$" (ALMA data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- X-ray flux conversion assuming power-law Gamma=1.8  
  > "assuming a power-law spectrum with $\Gamma = 1.8$ (cite: Ricci17)." (2 Observation and data analysis) [from (cite: Ricci17)]
- SF contribution to mm via Equation 3  
  > "using Equation 3 of (cite: Kawamuro2022)" (3.3.1 Star formation and dust) [from (cite: Kawamuro2022)]
- Source size via Equation 22  
  > "using Equation (22) of (cite: Laor2008)" (3.3.4 Synchrotron emission in X-ray corona) [from (cite: Laor2008)]

### Not stated but needed to reproduce (our reading)

- Line-free/continuum channel selection per epoch
- Cell size, image size, masking and cleaning threshold
- Fitting method for the flux-flux relation and the intrinsic scatter
- Black hole mass used for lambda_Edd and Rg
- Exact BAT/XRT fluxes and time-matching to ALMA epochs
- Swift/XRT fit details (the model description is inconsistent: BB vs DISKBB)
- How peak flux and uncertainty were measured (Gaussian fit)

## Analysis recipe

1. **Image ALMA continuum and measure fluxes**: tclean images with all spws, per-spw images, peak flux; Gaussian 2D fit shows unresolved nucleus  
  > "We used all the spectral windows to generate each clean image." (ALMA data reduction)
   - software: CASA
   - parameter: briggs robust=0.5  
  > "weighting = briggs (robust=0.5)" (ALMA data reduction)
   - fitting: _not stated_
   - validation: Fluxes at original beam within ~5% of those at common beam  
  > "We found the fluxes with the original beam size are within $\sim 5\%$ of the ones with the beam size of $7.3'' \times 4.96''$." (ALMA data reduction)
2. **Derive in-band spectral index**: Power-law fit to fluxes in four spws, F_nu ∝ nu^alpha  
  > "An in-band spectral index ($\alpha_{\rm mm}$) was derived from flux measurements in four spectral windows, following $F_{\nu} \propto \nu^{\alpha_{\rm mm}}$." (2 Observation and data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive X-ray fluxes and bolometric luminosity**: BAT/XRT rates converted to 14-150 keV; L_bol from lambda_Edd-dependent bolometric correction  
  > "$\log \kappa_{\rm 14-195} = (0.13 \pm 0.04) \log \lambda_{\rm Edd} + (1.04 \pm 0.05)$." (2 Observation and data analysis)
   - software: XSPEC
   - assumption: power law with Gamma = 1.8  
  > "assuming a power-law spectrum with $\Gamma = 1.8$ (cite: Ricci17)." (2 Observation and data analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Correlate mm and X-ray flux**: Spearman correlation and linear fit in log space with intrinsic scatter  
  > "Spearman correlation index of 0.54 and a p-value of 0.0168" (3.2 Relation between mm and X-ray emissions)
   - fitting: _not stated_
   - validation: Compared with Kawamuro2022 and Ricci2023  
  > "While studying the relation between $\log L_{\rm 230~GHz}$ and $\log L_{\rm 14-150~keV}$ for 98 RQAGNs, (cite: Kawamuro2022) found a steeper slope, $\sim 1.19\pm0.08$ with a scatter of 0.30 dex." (Results and discussions: Relation between mm and X-ray emissions)
5. **Test origin scenarios and estimate source size and magnetic field**: Order-of-magnitude estimates for SF, jet, outflow shock and self-absorbed synchrotron corona (equipartition)  
  > "considering magnetic energy density is in equipartition with the photon energy density" (3.3.4 Synchrotron emission in X-ray corona)
   - assumption: outflow velocity taken as escape velocity  
  > "Conservatively assuming the outflow velocity as the escape velocity" (3.3.3 Outflow driven shock)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.4.9: calibration and tclean imaging  
  > "we used CASA 6.5.4.9 for the following tasks" (ALMA data reduction)
- **ALMA Pipeline** 2020.1.0.40: data processing  
  > "ALMA Pipeline version 2020.1.0.40" (2 Observation and data analysis)
- **XSPEC** : Swift/XRT spectral fitting  
  > "Spectra were modeled in XSPEC as TBABS" (X-ray data analysis)
- **UVOTSOURCE** : Swift/UVW2 photometry  
  > "The *Swift*/UVW2 photometric flux was estimated using UVOTSOURCE task." (Multi-wavelength observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spearman correlation, F230 vs F14-150keV | 0.54 (p=0.0168) | not stated | dimensionless | 4 | Spearman correlation index of 0.54 and a p-value of 0.0168 |
| Slope of log F230 vs log F14-150 | 0.39 | ±0.13 | dimensionless | 4 | $\log F_{\rm 230~GHz} = (0.39 \pm 0.13) \log F_{\rm 14-150~keV} + (-10.62 \pm 1.34)$ |
| Intrinsic scatter | 0.05 | 1 sigma | dex | 4 | with an intrinsic scatter of 0.05 dex ($1\sigma$ level) |
| Median log(F230/F14-150) | -4.42 | ±0.21 | dimensionless | 4 | $\log (F_{\rm 230~GHz}/F_{\rm 14-150~keV}) = -4.42 \pm 0.21$ |
| Median ratio for lambda_Edd<1e-2 | -4.01 | ±0.22 | dimensionless | 4 | for $\lambda_{\rm Edd} < 10^{-2}$, the median ratio is found to be $-4.01\pm 0.22$ |
| Median ratio for lambda_Edd>1e-2 | -4.52 | ±0.20 | dimensionless | 4 | while for $\lambda_{\rm Edd} > 10^{-2}$ it is $-4.52\pm 0.20$ |
| Self-absorbed source size | 4-7e-5 pc (~100-200 Rg) | not stated | pc | 5 | $R_{\rm mm}\sim 4-7 \times 10^{-5}$ pc or $\sim 100-200$ $R_{\rm g}$ |
| Equipartition magnetic field | 100-300 | not stated | G | 5 | The equipartition magnetic field ($B_{\rm eq}$) is found in the range $\sim 100-300$ G |
| mm flux at peak (2018) and 2023 | ~9.8 mJy; ~3.5 mJy | ±1.0; ±0.4 | mJy | 1 | the mm flux was also observed to increase by a factor of $\sim 2$ ($\sim 9.8\pm1.0$ mJy) |

## Qualitative findings

- Central mm source is unresolved at all resolutions; flat spectral index consistent with compact optically thick synchrotron  
  > "the central emission appears unresolved at all resolutions probed" (2 Observation and data analysis)

## Claim tuples

- H: mm emission is coupled to X-ray emission | E: Correlate ALMA 230 GHz flux with Swift 14-150 keV flux over 8 epochs | R: Spearman 0.54, slope 0.39±0.13, scatter 0.05 dex | F: Common origin | **supported**
- H: Star formation, jet, or outflow shocks produce the mm emission | E: Order-of-magnitude estimates | R: SF and outflow far below observed flux; jet behavior contradicts BHXB analogy | F: These are discarded; free-free ~1 mJy non-variable | **supported**
- H: mm emission arises in a compact optically thick source | E: In-band spectral index | R: alpha_mm from -0.26±0.53 to 0.13±0.38, no correlation with flux | F: Compact synchrotron source, possibly the corona | **supported**
- H: mm/X-ray ratio depends on accretion state | E: Compare ratio vs lambda_Edd | R: Ratio higher at low lambda_Edd (-4.01 vs -4.52) | F: No clear link, but higher in low-accretion state | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Star formation, dust, compact jet and outflow shock rejected as dominant mm sources  
  > "We discard star formation, outflow-driven shock, and compact jet as possible contributors to the mm emission." (Summary & Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Detailed SED modeling is needed to constrain the magnetic field  
  > "This suggests a detailed SED modeling is required to constrain the magnetic field in NGC 1566." (3.3.4 Synchrotron emission in X-ray corona)
- Caveat (inferred, ours): Only 8 epochs; correlation moderate (p=0.017) and slope flat, possibly from constant contamination
- Caveat (inferred, ours): X-ray fluxes are from different instruments and not simultaneous with ALMA
- Caveat (inferred, ours): Different beam sizes include extended emission at the coarse resolution
- Caveat (inferred, ours): Origin arguments are order-of-magnitude

## Reproducibility

- Data public (paper): All data publicly available  
  > "All the data used in the paper are publicly available." (DATA AVAILABILITY)
- Products in archive: _not stated_
- Missing: Black hole mass and exact BAT/XRT flux tables
- Missing: Regression method for the flux relation
- Missing: Time-matching of X-ray to ALMA epochs
- Missing: Spectral index fitting details
- Data volume (inferred): ~50-200 GB across 6 projects
- Score (inferred): 5/5, Public data and simple imaging with robust=0.5 are given, but the fitting and X-ray processing details are partly missing.
- Rediscovery candidate: yes, Data are public, the recipe is simple, and the results are numeric (fluxes, spectral indices, correlation).

## Links

- Method: (cite: Hunter2023) (ALMA pipeline reference)
- Method: (cite: Gupta2024) (Bolometric correction)
- Companion: (cite: Kawamuro2022) (230 GHz vs X-ray sample comparison)
- Companion: (cite: Ricci2023mm) (100 GHz vs X-ray correlation)
- Related: BASS
- Related: Swift/BAT 157-month catalog

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2018.1.01651.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 42,
  "rate": 0.545
 },
 "evidence_ok": true
}
```
