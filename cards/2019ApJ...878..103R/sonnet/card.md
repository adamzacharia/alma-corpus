# Modeling the Protoplanetary Disks of Two Brown Dwarfs in the Taurus Molecular Cloud

`2019ApJ...878..103R` | The Astrophysical Journal 2019 | first author: Rilinger, Anneliese M. | arXiv: 1905.05829 | DOI: 10.3847/1538-4357/ab211d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the disk radii and masses of two Taurus brown dwarfs (CFHT Tau 4, 2M0444), and what do they imply for brown dwarf formation and planet formation?  
  > "By combining modeling of the spectral energy distributions and ALMA images, we obtain disk radii and masses for these objects" (abstract)
- Target **CFHT Tau 4 (2MASS J04394748+2601407)**: coordinates _not stated_; z/distance 147.1±5.1 pc  
  > "Distances are derived from Gaia DR2 parallax measurements" (Table 1); distance from Gaia DR2 parallax  
  > "Distances are derived from Gaia DR2 parallax measurements" (Table 1)
- Target **2M0444 (2MASS J04442713+2512164)**: coordinates _not stated_; z/distance 141.0±2.7 pc  
  > "Distances are derived from Gaia DR2 parallax measurements" (Table 1); distance from Gaia DR2 parallax  
  > "Distances are derived from Gaia DR2 parallax measurements" (Table 1)

## Data provenance

- ALMA projects: 2016.1.01511.S, 2015.1.00934.S
- bands: Band 7 (0.89 mm)  
  > "Archival ALMA Band 7 (0.89 mm) continuum observations of the two BDs were used in this analysis." (2 Observations)
- frequencies and spectral setup: Two 2 GHz SPWs; CFHT Tau 4: 333.806, 343.911 GHz; 2M0444: 332.013, 344.013 GHz  
  > "For CFHT Tau 4, the spectral windows were centered on 333.806 GHz and 343.911 GHz; for 2M0444, 332.013 GHz and 344.013 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array; 42 antennas (CFHT Tau 4), 39 antennas (2M0444)  
  > "using 39 antennas in the 12 m array" (2 Observations)
- configurations: _not stated_
- baselines: 17 m to 2600 m (CFHT Tau 4); 15 m to 1100 m (2M0444)  
  > "Baselines ranged from 17 m to 2600 m for CFHT Tau 4 and 15 m to 1100 m for 2M0444." (2 Observations)
- angular resolution: 0.24x0.12 arcsec (CFHT Tau 4); 0.28x0.19 arcsec (2M0444)  
  > "For 2M0444, the resulting beam size is $0\rlap.''28 \times 0\rlap.''19$ (position angle = $-31.02^{\circ}$)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 4.5 min (CFHT Tau 4); 46 min (2M0444), total integration  
  > "The total integration time was 4.5 minutes for CFHT Tau 4 and 46 minutes for 2M0444." (2 Observations)
- observing dates: 2017 July 6 (CFHT Tau 4); 2016 July 24 (2M0444)  
  > "Observations of CFHT Tau 4 were taken in Cycle 4 on 2017 July 6" (2 Observations)
- pi or archival as stated: Archival  
  > "Archival ALMA Band 7 (0.89 mm) continuum observations" (2 Observations)
- Other facility **Spitzer IRS/IRAC/MIPS, WISE, 2MASS, UKIDSS, SDSS, Pan-STARRS, Herschel, SCUBA, IRAM, SMA, VLA, Gaia**: Photometry for SEDs (via VizieR), Spitzer IRS spectrum for 2M0444, Gaia distances  
  > "The SEDs were constructed using photometric data points from visible to millimeter wavelengths taken from the VizieR catalogue access tool" (3.1.1 SED Fitting)
- External data: All stellar parameters of CFHT Tau 4  
  > "All values for CFHT Tau 4 are from (cite: andrews13)." (Table 1) [from (cite: andrews13)]
- External data: 2M0444 temperature and luminosity; mass from Ricci13; extinction from Bouy08  
  > "Temperature and luminosity for 2M0444 are from (cite: luhman04); mass for 2M0444 is from (cite: ricci13)" (Table 1) [from (cite: luhman04); (cite: ricci13); (cite: bouy08)]
- External data: 2M0444 mass accretion rate 2e-10 Msun/yr  
  > "We fixed $\dot{M}$ at $2\times10^{-10}$ ${\rm {\it M}_{\odot}\,yr^{-1}}$ for 2M0444 (cite: bouy08)" (3.1.1 SED Fitting) [from (cite: bouy08)]
- External data: Photospheric color table (M6 adopted)  
  > "The photospheres are constructed using the (cite: kh95) color table and the dereddened observed J-band magnitude of the object." (3.1.1 SED Fitting) [from (cite: kh95)]

## Processing

### Calibration

- pipeline or manual: Archive calibration scripts from ALMA staff, no extra flagging  
  > "We used the calibration scripts as provided by ALMA staff in the archive with no additional flagging required." (2 Observations)
- casa version: CASA v5.1.2  
  > "CASA (v5.1.2; McMullin et al. 2007)" (Software)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (flux and bandpass)  
  > "The quasar J0510+1800 was observed as a flux and bandpass calibrator for both objects." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "Deconvolved images were obtained using the task CLEAN with natural weighting in CASA." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Deconvolved images were obtained using the task CLEAN with natural weighting in CASA." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.13 mJy/beam (CFHT Tau 4); 0.09 mJy/beam (2M0444)  
  > "with an rms of 0.09 mJy beam$^{-1}$, producing a peak S/N of 60" (2 Observations)

### Inherited from earlier work

- Procedure for modeling ALMA Band 7 data with SED-based model images  
  > "Following (cite: macias18), we modeled the ALMA Band 7 data described in Section [2](#obs)." (3.1.2 ALMA Data) [from (cite: macias18)]
- Pre-transitional disk structure with annular gap  
  > "the disk structure can be modified to include an annular gap within the disk following (cite: espaillat11)" (3.1.1 SED Fitting) [from (cite: espaillat11)]
- Wall radii and disk mass computation  
  > "$^{d}$ Calculated using $\dot{M}$ and $\alpha$ following (cite: diad05)" (Table 3) [from (cite: diad05)]

### Not stated but needed to reproduce (our reading)

- DIAD code availability and exact grid steps
- Photometry flux uncertainties used in chi2
- Clean parameters (cell, image size, mask, threshold)
- How model images were generated from SED models (scaling, wavelength)
- Criteria for model-vs-data comparison in visibilities (no quantitative fit statistic)
- Gap inner edge assumptions for 2M0444 (0.02 au)

## Analysis recipe

1. **Fit SEDs with DIAD models**: Grid of DIAD models, best fit by minimum chi2, visual inspection and iterative grid refinement  
  > "We ran grids of models and determined the best-fit parameters by selecting models with minimum $\chi^2$, visually inspecting the model fits, and iteratively refining the grids." (3.1.1 SED Fitting)
   - software: DIAD
   - parameter: Ranges: amax_atm 0.25–1.0 um, amax_mid 500 um–1 cm, epsilon 0.001–0.1, Twall,out 75–1400 K, alpha 0.0001–0.01, Rout 30–100 au, i 25–80 deg  
  > "0.25–1.0 $\mu$m for a$_{max, atm}$, 500 $\mu$m–1 cm for a$_{max, mid}$, 0.001–0.1 for $\epsilon$" (3.1.1 SED Fitting)
   - assumption: Dust-to-gas 0.01; Twall,in 1400 K; Mdot fixed (1e-10 CFHT Tau 4, 2e-10 2M0444); grain size power law -3.5, min size 0.005 um  
  > "We assumed a fixed dust-to-gas mass ratio of 0.01." (3.1.1 SED Fitting)
   - fitting: Grid search, chi2 minimum; no MCMC because too costly  
  > "This expense renders common statistical methods of estimating best-fit model parameters and their uncertainties" (3.1.1 SED Fitting)
   - validation: Uncertainties are only qualitative ranges  
  > "should not be considered an accurate quantitative estimate of the uncertainties, but rather a qualitative approximation" (3.1.1 SED Fitting)
2. **Fit ALMA continuum geometry and radius**: Make model images from best SED models, Fourier transform and sample at observed uv coverage in CASA; adjust inclination, PA, radius  
  > "Three parameters were adjusted to improve the fit of the model image to the data: inclination, position angle, and radius." (3.1.2 ALMA Data)
   - software: CASA
   - fitting: Manual adjustment; contour comparison  
  > "Contours of the models and the ALMA observations were compared to assess the model fit." (3.1.2 ALMA Data)
   - validation: Radial profiles within 1 sigma and visibility comparison  
  > "We varied disk radius, position angle, and inclination for each object until the model profile was within 1$\sigma$ of the observed profile and the residuals were minimized." (3.1.2 ALMA Data)
3. **Compute disk mass and compare to formation models**: Integrate surface density (from Mdot and alpha) over disk radius  
  > "The total disk mass was computed by integrating over the surface mass density of the disk (as determined by $\dot{M}$ and the best-fit $\alpha$) over the radius of the disk." (3.2 Model Results)
   - software: DIAD
   - assumption: dust-to-gas 0.01  
  > "assuming a dust-to-gas mass ratio of 0.01" (3.2 Model Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.2: Calibration, CLEAN imaging, simulating model visibilities  
  > "The data were calibrated using the Common Astronomy Software Applications (CASA) package" (2 Observations)
- **DIAD** : Disk radiative transfer SED models  
  > "The disk structure is modeled using the D’Alessio Irradiated Accretion Disk (DIAD) radiative transfer models" (3.1.1 SED Fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CFHT Tau 4 disk mass | 0.42 | +0.08/-0.05 | M_Jup | 3 | 0.42$^{+0.08}_{-0.05}$ |
| 2M0444 disk mass | 2.05 | +0.07/-0.06 | M_Jup | 3 | 2.05$^{+0.07}_{-0.06}$ |
| CFHT Tau 4 outer radius | 80 | 10 | au | 2 | 80$\pm$10 |
| 2M0444 outer radius | 100 | 10 | au | 2 | 100$\pm$10 |
| CFHT Tau 4 inclination / PA | 70 / 40 | 10 / 10 | deg | 2 | a position angle of 40$^{\circ}$, and an inclination of 70$^{\circ}$ |
| 2M0444 inclination / PA | 40 / 70 | 10 / 10 | deg | 2 | a position angle of 70$^{\circ}$, and an inclination of 40$^{\circ}$ |
| 2M0444 disk temperature at 0.27 au | 117 | not stated | K | 0 | We find the temperature of the disk at 0.27 au to be 117 K. |

## Qualitative findings

- 2M0444 SED requires a pre-transitional disk with gap 0.02–0.27 au  
  > "the disk of 2M0444 is best fit with a pre-transitional disk model with a gap in the disk from 0.02 au to 0.27 au" (4.3 Gap in the Disk of 2M0444)

## Claim tuples

- H: Do BD disk radii favor ejection or non-ejection formation? | E: Model ALMA Band 7 visibilities with SED-based models | R: Radii 80 au and 100 au | F: Radii larger than ejection simulations predict, favoring non-ejection, though selection effects limit firmness | **partially**
- H: Are the disks massive enough to form planets? | E: DIAD disk masses compared to Payne & Lodato core accretion results | R: 0.42 and 2.05 M_Jup | F: 2M0444 can form Earth-mass planets; CFHT Tau 4 unlikely | **supported**
- H: Does 2M0444 have a disk gap? | E: SED fit with full vs pre-transitional models | R: Full disk fails mid-IR excess; pre-transitional fits | F: 2M0444 is a pre-transitional disk | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: MCMC infeasible because DIAD is computationally expensive, so grids were used  
  > "Given the complexity of DIAD, running disk models is computationally expensive." (3.1.1 SED Fitting)
- Alternative: Snowline origin of the 2M0444 gap rejected: temperature 117 K at 0.27 au does not match H2O, CO or CO2 snowlines  
  > "The snowlines of common molecules were either too warm (H$_2$O at 128–150 K) or too cold" (4.3 Gap in the Disk of 2M0444)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties are qualitative; selection effects make conclusions difficult; brightest disks may be atypical  
  > "The selection effects resulting from the evolution of the disk, and the timescale on which this evolution occurs, make firm conclusions difficult." (4.1 Disk Radius and BD Formation)
- Caveat (inferred, ours): No formal fit or uncertainty for radius; by-eye matching
- Caveat (inferred, ours): Mdot fixed and assumed for CFHT Tau 4 drives disk mass
- Caveat (inferred, ours): Mass depends on assumed dust-to-gas 0.01 and alpha
- Caveat (inferred, ours): Short 4.5 min observation of CFHT Tau 4 gives S/N of 14
- Caveat (inferred, ours): Two objects only

## Reproducibility

- Data public (paper): Archival ALMA data with project codes given  
  > "Archival ALMA Band 7 (0.89 mm) continuum observations of the two BDs were used in this analysis." (2 Observations)
- Products in archive: _not stated_
- Missing: DIAD code access and best-fit model SED files
- Missing: Clean parameters
- Missing: Procedure details for model images in uv fitting
- Data volume (inferred): ~10-30 GB for both continuum datasets
- Score (inferred): 3/5, Public data and numeric results, but DIAD is a specialized code and the fitting is by eye with sparse imaging details.
- Rediscovery candidate: no, DIAD model code is not generally available and the fitting is manual.

## Links

- Method: (cite: macias18) (ALMA data modeling approach followed)
- Method: (cite: diad05) (DIAD model and mass calculation)
- Method: (cite: espaillat11) (Pre-transitional disk modification)
- Companion: (cite: ricci13); (cite: ricci14) (Previous ALMA/SMA observations and radius constraints of the same disks)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 44,
  "rate": 0.62
 },
 "evidence_ok": true
}
```
