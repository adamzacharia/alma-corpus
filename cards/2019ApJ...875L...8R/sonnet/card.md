# An Accreting Supermassive Black Hole Irradiating Molecular Gas in NGC 2110

`2019ApJ...875L...8R` | The Astrophysical Journal Letters 2019 | first author: Rosario, David J. | arXiv: 1903.07637 | DOI: 10.3847/2041-8213/ab1262

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Does the AGN directly alter the properties of molecular gas in the nucleus of NGC 2110, as seen in a region weak in CO 2-1 emission?  
  > "Here we present evidence for localised transformation of molecular gas through direct impact from the AGN’s radiation field in the nearby Seyfert 2 galaxy NGC 2110" (Introduction)
- Target **NGC 2110**: coordinates RA 5:52:11.379, Dec -7:27:22.52 (J2000, VLA radio core)  
  > "nearby Seyfert 2 galaxy NGC 2110 (luminosity distance $D_{L} = 34$ Mpc, $cz=2335$ km s$^{-1}$)" (Introduction); "We have adopted the VLA radio core as the coordinates of the nucleus (R.A.(J2000) $=$ 5:52:11.379, Dec.(J2000) $=$ -7:27:22.52)" (2.4 Image registration and astrometry); z/distance D_L = 34 Mpc, cz = 2335 km/s  
  > "nearby Seyfert 2 galaxy NGC 2110 (luminosity distance $D_{L} = 34$ Mpc, $cz=2335$ km s$^{-1}$)" (Introduction); "We have adopted the VLA radio core as the coordinates of the nucleus (R.A.(J2000) $=$ 5:52:11.379, Dec.(J2000) $=$ -7:27:22.52)" (2.4 Image registration and astrometry); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00474.S
- bands: Band 6  
  > "| ALMA                     | Band 6          | 2012.1.00474.S |" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.71'' x 0.45'' (PA -79 deg) common restoring beam  
  > "both with a common restoring beam of $0.71\ensuremath{''} \times 0.45\ensuremath{''}$ (PA of $-79^{\circ}$)" (2.1 ALMA spectroscopy)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 2-1 (230.54 GHz)
- Other facility **HST (WFPC2, NICMOS)**: Halpha+[NII] line map and F791W/F200N colour map  
  > "We produced a color map (Figure [1](#contextfigure)c) by dividing the F791W image by the deep NIR image (F200N)." (2.2 Optical and near-infrared (NIR) HST imaging)
- Other facility **VLT/SINFONI**: H2 1-0 S(1) and [Fe II] 1.25 um maps and kinematics  
  > "We used the K-band cube to measure the strength and kinematics of the H$_{2}$ 1–0 S(1) line at 2.12 $\mu$m" (2.3 VLT/SINFONI integral field unit (IFU) spectroscopy)
- Other facility **Spitzer/IRS**: MIR H2 0-0 S(0), S(1), S(2) line fluxes from CASSIS spectra  
  > "We downloaded fully reduced, background-subtracted, optimally-extracted mid-infrared (MIR) spectra of NGC 2110 from the [CASSIS]" (2.5 Spitzer/IRS high-resolution spectroscopy)

## Processing

### Calibration

- pipeline or manual: standard pipelines with parameters recommended by the observatories  
  > "Unless otherwise specified, we employed standard pipelines to reduce these data, adopting parameters recommended by the respective observatories." (2 Observations and data preparation)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN; 1 mm continuum map and CO 2-1 cube at 5 km/s  
  > "we used CLEAN to generate a 1mm continuum map and a CO 2$\rightarrow$1 cube with a velocity resolution of 5 km s$^{-1}$" (2.1 ALMA spectroscopy)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: resampled to 0.24'' square spaxels  
  > "We resampled these maps to $0.24\ensuremath{''}$ square spaxels for our final measurements." (2.1 ALMA spectroscopy)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Power-law H2 temperature distribution model and normalisation to the 0-0 S(1) line  
  > "Adopting the approach of (cite: togi16), we assume a uniform power law model of the distribution of H$_{2}$ temperatures" (3.2 Associated enhancement in warm molecular gas emission) [from Togi & Smith 2016 (cite: togi16)]
- CO-based molecular mass formula  
  > "Following (cite: solomon05):" (3.2 Associated enhancement in warm molecular gas emission) [from Solomon & Vanden Bout 2005 (cite: solomon05)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- CLEAN weighting, robust value, deconvolver, masking, threshold
- continuum-subtraction line-free channels
- primary beam correction details
- ALMA flux calibrator and flux uncertainty
- custom SINFONI reduction pipeline details
- H2 level energies/statistical weights and fitting procedure for n and T_l
- exact velocity-integration and moment procedure

## Analysis recipe

1. **Make ALMA CO 2-1 maps and kinematics**: CLEAN cube and continuum; integrate over 900 km/s window; fit single gaussian per spaxel with S/N>5  
  > "fitting a single gaussian to the line in each spaxel with an integrated S/N $> 5$, using the Python package" (2.1 ALMA spectroscopy)
   - software: CLEAN, LMFIT
   - parameter: 5 km/s channels; 0.24'' spaxels  
  > "a velocity resolution of 5 km s$^{-1}$" (2.1 ALMA spectroscopy)
   - fitting: single gaussian per spaxel  
  > "fitting a single gaussian to the line in each spaxel" (2.1 ALMA spectroscopy)
   - validation: _not stated_
2. **Model warm H2 excitation and total molecular mass**: Power-law temperature distribution dN ∝ T^-n dT fitted to H2 0-0 S(0),S(1),S(2) and 1-0 S(1) fluxes; mass for T>=50 K  
  > "The two free parameters are the power law index $n$ and the lower temperature T$_{\ell}$ respectively." (3.2 Associated enhancement in warm molecular gas emission)
   - parameter: upper temperature fixed at 50000 K; lower T 50 K for mass  
  > "The upper temperature of the distribution is fixed at $50000$ K" (3.2 Associated enhancement in warm molecular gas emission)
   - assumption: power law continuous beyond several 100 K; S(0) flux nominal uncertainty 0.3 dex  
  > "A nominal uncertainty of 0.3 dex for the line flux implies a mass in the range of $0.9$–$4.6\times10^{8}$ M$_{\odot}$." (3.2 Associated enhancement in warm molecular gas emission)
   - fitting: model fixed to formally measured S(0) flux  
  > "Fixing the model to the formally measured flux of the S(0) line, we obtain $n=4.48$" (3.2 Associated enhancement in warm molecular gas emission)
   - validation: model reproduces all four H2 line fluxes  
  > "a single power-law model tied to the formal flux of the S(0) line can reproduce the fluxes measured in all four H$_{2}$ lines quite well" (3.2 Associated enhancement in warm molecular gas emission)
3. **CO-based gas mass and surface densities**: Solomon & Vanden Bout formula with F_CO=13 Jy km/s in 4'' aperture; surface density from mass difference over 0.34 kpc^2  
  > "$F_{\rm CO} = 13$ Jy km s$^{-1}$from a 4" circular aperture centered on the nucleus" (3.2 Associated enhancement in warm molecular gas emission)
   - parameter: R12 = 1.4; alpha_CO 1.5-3  
  > "Taking $R_{12} = 1.4$ and $\alpha_{\rm CO}$ in the range of 1.5 – 3" (3.2 Associated enhancement in warm molecular gas emission)
   - assumption: D_L = 34 Mpc  
  > "luminosity distance $D_{L} = 34$ Mpc" (Introduction)
   - fitting: _not stated_
   - validation: compared with surface density in CO knots (200-350 Msun/pc^2)  
  > "molecular gas surface density of $200$– $350$ M$_{\odot}$ pc$^{-2}$ inferred using Equation [\[eq1\]](#eq1) in the bright CO knots" (3.2 Associated enhancement in warm molecular gas emission)

## Software

- **CLEAN** : ALMA continuum and CO cube imaging  
  > "we used CLEAN to generate a 1mm continuum map" (2.1 ALMA spectroscopy)
- **LMFIT** : gaussian line fits to CO kinematics  
  > "using the Python package [LMFIT]" (2.1 ALMA spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2 temperature power-law index n | 4.48 | not stated | dimensionless | 2 | we obtain $n=4.48$ |
| Molecular mass from H2 lines | 2.5e8 (range 0.9-4.6e8) | 0.3 dex in S(0) flux | Msun | 2 | we calculate M$_{\rm mol} = 2.5\times10^{8}$ M$_{\odot}$ |
| Molecular mass from CO 2-1 | 2-4e7 | not stated | Msun | 3 | we obtain M$_{\rm mol, CO}\approx2 - 4 \times10^{7}$ M$_{\odot}$ |
| Surface density in lacuna | 650 (180 low end) | not stated | Msun pc^-2 | 3 | we infer a molecular gas surface density of 650 M$_{\odot}$ pc$^{-2}$ |

## Qualitative findings

- CO 2-1 lacuna is co-spatial with AGN-ionised gas and hot H2, and CO and H2 velocity fields are continuous across it  
  > "The two structures are highly co-spatial, and the CO emission is noticeably weaker along the axis of the ionised gas." (3.1 A localised lack of cold molecular gas emission)

## Claim tuples

- H: The CO lacuna reflects AGN influence on molecular gas rather than absence of gas | E: Compared CO map with Halpha, [Fe II], H2 S(1) maps and modelled Spitzer H2 lines | R: Lacuna co-spatial with ionised/warm gas; H2 mass exceeds CO mass; surface densities similar to surroundings | F: Molecular disk extends into the lacuna and CO emission is suppressed by AGN radiation | **supported**
- H: CO and warm H2 trace the same dynamics | E: Compared CO and H2 1-0 S(1) velocity fields | R: both trace rotating disc with same asymmetry | F: cold and warm phases are connected | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dust extinction, CO absorption against continuum, and ILR stalling rejected as explanations of the lacuna  
  > "The lacuna is well-resolved, and therefore unlikely to arise from CO 2$\rightarrow$1 line absorption against the nuclear mm continuum" (3.1 A localised lack of cold molecular gas emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Photoionisation and shocks cannot be discriminated; S(0) constraint is formally an upper limit  
  > "The molecular gas diagnostics currently available do not strongly discriminate between these mechanisms." (3.3 AGN feedback suppresses CO 2→1 emission)
- Caveat (inferred, ours): Mass depends strongly on poorly detected S(0) line (S/N~2) with aperture mismatch
- Caveat (inferred, ours): alpha_CO and R12 are assumed
- Caveat (inferred, ours): No CO excitation modelling or higher-J lines to test excitation versus absence of gas

## Reproducibility

- Data public (paper): Program IDs listed for all datasets; Spitzer spectra from CASSIS  
  > "| ALMA                     | Band 6          | 2012.1.00474.S |" (Table 1)
- Products in archive: _not stated_
- Missing: ALMA imaging parameters and CASA version
- Missing: custom SINFONI pipeline
- Missing: H2 fit implementation
- Data volume (inferred): ~50-100 GB for ALMA raw plus small ancillary data
- Score (inferred): 3/5, Data are public with listed program IDs and the analysis is simple, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Multi-facility data and a custom pipeline; ALMA imaging recipe is incomplete.

## Links

- Method: Togi & Smith 2016 (cite: togi16) (H2 power-law temperature model)
- Companion: Rosario et al. 2010 (cite: rosario10) (earlier study of ionised gas in NGC 2110)
- Related: CASSIS
- Related: SINGS

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
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
  "facts": 67,
  "stated": 31,
  "rate": 0.463
 },
 "evidence_ok": true
}
```
