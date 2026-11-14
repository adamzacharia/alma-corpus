# The Galaxy Activity, Torus, and Outflow Survey (GATOS): X. Molecular gas clumpiness under the influence of AGN

`2026A&A...705A..33E` | Astronomy and Astrophysics 2026 | first author: Esposito, Federico | arXiv: 2510.18957 | DOI: 10.1051/0004-6361/202556485

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How does the clumpiness of nuclear (50-200 pc) molecular gas in nearby Seyfert galaxies depend on AGN X-ray luminosity, Eddington ratio and gas concentration?  
  > "In this work, we focus on the clumpiness of the molecular gas, a property that reflects how fragmented or structured the emission is within the nuclear region." (1 Introduction)
- Target **16 nearby AGN host galaxies (NGC 613, 1068, 1326, 1365, 1433, 1566, 1672, 3227, 4941, 5643, 6300, 6814, 7213, 7314, 7465, 7582)**: coordinates _not stated_; z/distance D_L 7.2-27.2 Mpc  
  > "Distances ($D_{\text{L}}$) are median values of redshift-independent distances taken from the Nasa Extragalactic Database (NED)." (Table 1 notes); distance from median redshift-independent distances from NED  
  > "Distances ($D_{\text{L}}$) are median values of redshift-independent distances taken from the Nasa Extragalactic Database (NED)." (Table 1 notes)

## Data provenance

- ALMA projects: 2017.1.00082.S, 2018.1.00113.S, 2015.0.00404.S, 2016.1.00254.S, 2016.0.00296.S
- bands: Band 7 (CO(3-2))  
  > "All galaxies have CO($3-2$) emission observed with the Atacama Large Millimeter/submillimeter Array (ALMA) Band 7, covering a field of view of 17$''$" (2 Sample description)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.08'' to 0.2'' (4-16 pc)  
  > "spatial resolutions ranging from 0.08$''$ to 0.2$''$, corresponding to a physical size range of $4-16$ pc" (2 Sample description)
- max recoverable scale: _not stated_
- sensitivity: 6 to 28 mJy km/s/beam  
  > "The sensitivity of the CO($3-2$) maps ranges from 6 to 28 mJy km s$^{-1}$ beam$^{-1}$." (2 Sample description)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Other facility **Swift-BAT**: parent hard X-ray selection of GATOS core sample  
  > "The GATOS core sample was selected from the 70 month *Swift*-BAT all-sky hard-X ray survey" (2 Sample description)
- External data: CO(3-2) data, inclinations and position angles (kinemetry)  
  > "Inclinations and position angles of the targets are taken from (cite: garciaburillo21)" (2 Sample description) [from (cite: garciaburillo21)]
- External data: X-ray luminosities and Eddington ratios  
  > "X-ray luminosities ($L_{\rm X}^{2-10 \text{ keV}}$) are taken from (cite: ricci17); (cite: combes19); (cite: garciaburillo24)." (Table 1 notes) [from (cite: ricci17); (cite: combes19); (cite: garciaburillo24); (cite: koss17)]

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
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Gaussian kernels: common 16 pc resolution, then 20-100 pc FWHM in 10 pc steps  
  > "we first smooth all the CO maps to a common physical resolution of 16 pc, corresponding to the largest ALMA beam in the sample." (3.1 Identifying the clumps)
- final beam: 16 pc  
  > "we first smooth all the CO maps to a common physical resolution of 16 pc" (3.1 Identifying the clumps)
- final rms: _not stated_

### Inherited from earlier work

- Calibration, imaging, moment maps and kinematics of the CO(3-2) data  
  > "The CO($3-2$) data used here were analysed in detail by (cite: garciaburillo21), where moment maps and kinematic modelling are discussed." (2 Sample description) [from (cite: garciaburillo21)]
- Clumpiness procedure  
  > "we follow the procedure outlined in (cite: conselice03) to identify the clumps" (3.1 Identifying the clumps) [from (cite: conselice03)]
- 50 pc and 200 pc apertures  
  > "we follow (cite: garciaburillo21; garciaburillo24) in defining two concentric regions centred on the AGN position" (3.3 Measuring nuclear and circumnuclear clumpiness) [from (cite: garciaburillo21; garciaburillo24)]

### Not stated but needed to reproduce (our reading)

- Calibration, imaging parameters and CASA version of the CO(3-2) cubes (deferred to GATOS I)
- How moment-0 maps were made (masking, clipping) and which maps were used
- Pixel size and resampling used for smoothing
- How the I-B>0 pixels were handled for noise
- Exact PWLF settings and the F-test implementation
- Which ALMA project maps to which galaxy
- Whether primary beam correction was applied

## Analysis recipe

1. **Sample selection and map homogenisation**: Discard galaxies with i>75 deg, leaving 16; smooth CO(3-2) maps to common 16 pc resolution  
  > "we have decided to discard the highly inclined ($i > 75^{\circ{}}$) galaxies from the original sample" (2 Sample description)
   - software: astropy
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify clumps via blurred-map subtraction**: Smooth with larger Gaussian kernel (20-100 pc) to get B; I-B residual keeping positive pixels  
  > "We subtract this smoothed map from the 16-pc map and retain only the pixels with positive residuals" (3.2 Smoothing CO(3-2) maps)
   - software: photutils
   - parameter: kernel FWHM 20-100 pc  
  > "we use smoothing kernels with FWHM between 20 and 100 pc in the following analysis" (3.2 Smoothing CO(3-2) maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure clumpiness in 50 pc and 200 pc apertures**: Three methods: median (I-B)/I; sum(I-B)/sum(I); sum of I in clumps / total  
  > "we separately sum the $I-B$ and $I$ values within the apertures and then divide them." (3.3 Method #2)
   - software: photutils
   - parameter: ~10% flux calibration error propagated to ~17% (Method 2) and ~14% (Method 3)  
  > "we assume a $\sim 10\%$ error on the flux measurements, which propagates to a $\sim 14\%$ uncertainty." (3.3 Method #3)
   - assumption: same alpha_CO for clumpy and smooth gas  
  > "assuming the same $\alpha_{CO}$ for both the clumpy emission and the underlying smooth emission" (3.3 Method #2)
   - fitting: _not stated_
   - validation: Three methods compared for robustness  
  > "Using multiple approaches allows us to test the robustness of our results against these effects" (3.3 Method #3)
4. **Fit clumpiness vs L_X for breakpoints**: pwlf one- and two-segment fits, F-test at 95%, t-test on slope; LOOCV and 1000 Monte Carlo runs  
  > "We then perform an F-test (at the 95% confidence level) to evaluate whether the two-segment model provides a statistically significant improvement" (3.4 Estimating the influence of AGN on clumpiness)
   - software: pwlf
   - parameter: L_X uncertainty ±0.15 dex; breakpoint reliable if LOOCV std <10% of L_X range  
  > "we assume a $\pm0.15$ dex uncertainty for $L_{\text{X}}$" (3.4 Estimating the influence of AGN on clumpiness)
   - fitting: piecewise linear least squares (pwlf); Monte Carlo resampling for 1 sigma interval  
  > "we run 1000 Monte Carlo simulations, taking into account the data uncertainties in both axes" (3.4 Estimating the influence of AGN on clumpiness)
   - validation: LOOCV and Monte Carlo  
  > "We consider a breakpoint reliable only if the standard deviation of its LOOCV distribution is smaller than 10% of the $L_{\text{X}}$-range of the data." (3.4 Estimating the influence of AGN on clumpiness)

## Software

- **pwlf** : piecewise linear fitting  
  > "we apply the Piecewise Linear Fitting (PWLF) algorithm using the Python package `pwlf`" (3.4 Estimating the influence of AGN on clumpiness)
- **Photutils** : Python library acknowledged  
  > "Photutils (cite: photutils)" (Acknowledgements)
- **kinemetry** : inclinations and position angles (from earlier work)  
  > "performed with the `kinemetry` software (cite: krajnovic06)" (2 Sample description)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Method 2 L_X breakpoint, 90-100 pc smoothing, 50 pc aperture | 41.99 | +0.44/-0.62 | log erg/s | 4 | 41.99_{-0.62}^{+0.44}$ and $42.03_{-0.34}^{+0.32}$ |
| Method 3 L_X breakpoint | 42.03 | +0.32/-0.34 | log erg/s | 4 | 41.99_{-0.62}^{+0.44}$ and $42.03_{-0.34}^{+0.32}$ |
| Method 3 baseline clump fraction at smallest smoothing | ~0.6 | not stated | dimensionless | 3 | Method #3 starts from a baseline value of $\Sigma_{\text{clumps}} / \Sigma_{\text{tot}} \approx 0.6$ |
| Method 1 median clumpiness range (50 pc aperture) | 0.08 to 0.39 | +0.03/-0.03 and +0.11/-0.10 | dimensionless | 3 | to range from $0.08_{-0.03}^{+0.03}$ to $0.39_{-0.10}^{+0.11}$ |

## Qualitative findings

- Clumpiness is flat up to L_X~10^42 erg/s then drops; the 200 pc aperture shows continuous anticorrelation  
  > "clumpiness remains roughly constant up to a threshold luminosity of $L_{\text{X}} \approx 10^{42}$ erg s$^{-1}$, beyond which it drops sharply" (6 Conclusions)

## Claim tuples

- H: AGN power reduces nuclear molecular gas clumpiness | E: Three clumpiness estimators vs L_X for 16 galaxies, 50 pc aperture, nine smoothing scales | R: Breakpoint near L_X~10^42 erg/s for Methods 2 and 3 at large smoothing; weak anticorrelation at small smoothing | F: Higher AGN luminosity is associated with smoother gas, interpreted as negative feedback | **supported**
- H: Clumpiness correlates with the concentration index | E: Clumpiness vs CCI | R: Rising trend with break at CCI~0.1; ratio vs CCI breaks at ~0.6 | F: Clumpiness related to concentration, not 1:1 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Breakpoint for Method 1 is poorly constrained; 200 pc aperture affected by noise  
  > "indicating that the exact position of the $L_{\text{X}}$ breakpoint is not well constrained and should be treated with caution" (4.1 The nuclear region)
- Caveat (inferred, ours): Only 16 galaxies; breakpoints depend on few high-L_X objects
- Caveat (inferred, ours): Clumpiness depends on smoothing kernel choice
- Caveat (inferred, ours): Inclination and noise effects not modelled
- Caveat (inferred, ours): Clumps defined by I-B>0 are not physical clouds

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduced CO(3-2) cubes/moment maps from GATOS I
- Missing: Exact smoothing implementation and masking
- Data volume (inferred): ~10-50 GB for archive cubes of 16 galaxies; moment maps small
- Score (inferred): 3/5, Simple algorithm described and numbers given, but input maps and details come from earlier paper.
- Rediscovery candidate: no, Input maps depend on earlier-paper processing and not all steps are specified.

## Links

- Method: (cite: conselice03) (clumpiness parameter)
- Method: (cite: pwlf) (piecewise fitting)
- Companion: (cite: garciaburillo21) (GATOS CO(3-2) data and kinematics)
- Companion: (cite: garciaburillo24) (concentration index vs L_X)
- Related: GATOS
- Related: NUGA
- Related: PHANGS

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.0.00404.S",
  "2016.1.00254.S",
  "2016.0.00296.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 30,
  "rate": 0.429
 },
 "evidence_ok": true
}
```
