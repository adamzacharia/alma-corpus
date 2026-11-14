# The Molecular Gas Content and Fuel Efficiency of Starbursts at z ∼ 1.6 with ALMA

`2018ApJ...867...92S` | The Astrophysical Journal 2018 | first author: Silverman, J. D. | arXiv: 1810.01596 | DOI: 10.3847/1538-4357/aae25e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do starbursts at z~1.6 (>4x above the main sequence) have higher star formation efficiency or higher gas fractions than main-sequence galaxies, based on CO(2-1)?  
  > "The question of whether starburst outliers from the MS owe their higher sSFR to a higher gas fraction or to a higher star formation efficiency (or combination thereof) remains an unsettled issue" (Final Remarks)
- Target **PACS starburst sample in COSMOS (12 galaxies, z~1.6)**: coordinates e.g. PACS-787 10:02:27.95 +02:10:04.4 (Table 1)  
  > "| 787 | 10:02:27.95 | 02:10:04.4 | 1.5234 | 10.56 | 12.83$\pm$0.04 | 991$^{+96}_{-87}$ | 0.8 |  |" (Table 1); z/distance z_spec 1.44-1.68 from Halpha  
  > "| 787 | 10:02:27.95 | 02:10:04.4 | 1.5234 | 10.56 | 12.83$\pm$0.04 | 991$^{+96}_{-87}$ | 0.8 |  |" (Table 1); distance from FMOS-COSMOS Halpha spectroscopic redshifts  
  > "| 787 | 10:02:27.95 | 02:10:04.4 | 1.5234 | 10.56 | 12.83$\pm$0.04 | 991$^{+96}_{-87}$ | 0.8 |  |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00861.S, 2012.1.00952.S, 2016.1.01426.S
- bands: Band 3 (CO(2-1) redshifted)  
  > "We selected spectral windows to detect $^{12}$C$^{16}$O(2 - 1; $\nu_{rest}$=230.538 GHz) redshifted into Band 3." (4 ALMA observations and data analysis)
- frequencies and spectral setup: Four base bands of 1.875 GHz each  
  > "Four base bands ($\Delta\nu=1.875$ GHz each) were configured to detect CO emission for multiple targets (2 - 3)" (4 ALMA observations and data analysis)
- continuum bandwidth: _not stated_
- arrays: 38-39 12m antennas  
  > "with 38 - 39 12m antennas on 4, 11, and 13 of March 2016" (4 ALMA observations and data analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.7-1.8 arcsec  
  > "yielded an angular resolution between 1.7-1.8$\ensuremath{''}$" (4 ALMA observations and data analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 4, 11, 13 March 2016  
  > "with 38 - 39 12m antennas on 4, 11, and 13 of March 2016" (4 ALMA observations and data analysis)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **NOEMA**: CO observation of PACS-164  
  > "a single observation of PACS-164 (cite: Silverman2015a) with the NOEMA interferometer" (2.3 Cycle 1 ALMA sample)
- Other facility **Herschel/Spitzer**: IR photometry for SFRs  
  > "We use the long wavelength photometry from Spitzer (24 $\mu$m; (cite: Sanders2007)), Herschel PACS (100 and 160 $\mu$m; (cite: Lutz2011))" (2.2 SFR)
- Other facility **Subaru FMOS**: Spectroscopic redshifts  
  > "we first acquired spectroscopic redshifts of $Herschel$ sources through the FMOS-COSMOS survey" (2 Selection of the sample)
- External data: Comparison sample of 131 typical star-forming galaxies plus starbursts with CO  
  > "a reference sample is utilized as compiled by (cite: Sargent2014) that includes 131 ‘typical’ star-forming galaxies at $z\lesssim4$ with measurements of their CO luminosity" (2.4 Comparison sample) [from (cite: Sargent2014)]
- External data: Cycle 1 ALMA CO data for five starbursts  
  > "The five $Herschel$-detected starbursts observed in Cycle 1 with ALMA, as fully described in (cite: Silverman2015a)" (2.3 Cycle 1 ALMA sample) [from (cite: Silverman2015a)]

## Processing

### Calibration

- pipeline or manual: standard analysis pipeline in CASA  
  > "Analysis of the interferometric data set is carried out using the standard analysis pipeline available with CASA Version 4.6" (4 ALMA observations and data analysis)
- casa version: CASA 4.6  
  > "CASA Version 4.6" (4 ALMA observations and data analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0854+2006, J0948+0022, Callisto, J1058+0133 (flux, phase, bandpass)  
  > "including J0854+2006, J0948+0022, Callisto, and J1058+0133" (4 ALMA observations and data analysis)
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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Cycle 1 data and sample details  
  > "Further details on the scientific results are given in (cite: Silverman2015a)." (2.3 Cycle 1 ALMA sample) [from (cite: Silverman2015a)]
- alpha_CO=1.3 from dynamical mass of PACS-787  
  > "This estimate of $\alpha_{CO}$ is based on a dynamical assessment of the gas mass using a higher resolution observation with ALMA of CO(5-4) emission from PACS-787" (4.2 Total molecular gas mass) [from Silverman et al. 2018, in press]
- MS CO luminosity and gas mass relations and sSFR parametrization  
  > "the expected value of the CO luminosity for MS galaxies ($<L^{\prime}_{CO, MS}>$) is based on Equation 1 of (cite: Sargent2014)" (4 Results) [from (cite: Sargent2014)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters for tclean/clean (weighting, robust, cell, image size, deconvolver)
- Channel range used for immoments and continuum-free channels
- Flux calibration uncertainty
- Cycle 1 and NOEMA data reduction details
- Details of the dynamical alpha_CO derivation
- Sizes for PACS-472 and details of the Hyperz SED fitting setup
- KS test details and comparison sample selection

## Analysis recipe

1. **Measure CO(2-1) flux**: Moment-0 image over the full line width, then elliptical Gaussian fit with imfit; checked by uv-plane fit and GILDAS  
  > "The emission is then modeled with an elliptical Gaussian using the CASA tool ‘imfit’ that returns a source centroid, deconvolved source size, and integrated flux." (4 ALMA observations and data analysis)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: uv-plane fit and independent GILDAS analysis  
  > "we confirm these measurements by fitting the emission in the $uv$-plane and through an independent effort using GILDAS available in the MAPPING package" (4 ALMA observations and data analysis)
2. **Derive CO luminosity**: L' = 3.25e7 S dv D_L^2/((1+z)^3 nu_obs^2); convert to CO(1-0) with ratio 0.85  
  > "$L^{\prime}_{CO(2-1)}$/$L^{\prime}_{CO(1-0)}=0.85$ (cite: Daddi2015)" (4.1 CO-to-TIR luminosity relation)
   - assumption: H0=70, OmegaL=0.7, OmegaM=0.3; r21=0.85  
  > "assume $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\Lambda}=0.7$, $\Omega_{\rm{M}}=0.3$" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare L'CO/LTIR with MS**: Normalize to MS expectation from Sargent2014 and compare vs delta_MS; KS test  
  > "Based on a Kolmogorov-Smirnov test, there is only a probability of 0.07% of randomly drawing values" (4.1 CO-to-TIR luminosity relation)
   - fitting: _not stated_
   - validation: Also repeated with Speagle2014 MS  
  > "This result appears to be valid even if using the parameterization of the MS at $z\sim1.6$ from (cite: Speagle2014)" (4.1 CO-to-TIR luminosity relation)
4. **Gas mass and depletion time**: Mgas = alpha_CO L'CO(1-0); tau_depl = Mgas/SFR  
  > "the time to deplete its gas reservoir if forming stars at a constant rate ($\tau_{depl}$=1/SFE)" (4.3 Gas depletion times)
   - parameter: alpha_CO = 1.3 (alternative 4.36) Msun/(K km/s pc^2)  
  > "A single value of this factor ($\alpha_{CO}=1.3$ M$_{\odot}$ / (K km s$^{-1}$ pc$^{2}$)) is applied across our starburst sample." (4.2 Total molecular gas mass)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: Results repeated with alpha_CO=4.36  
  > "we present our analysis in all subsequent plots also with this higher value for $\alpha_{CO}=4.36$" (4.2 Total molecular gas mass)

## Software

- **CASA** 4.6: pipeline, immoments, imfit  
  > "standard analysis pipeline available with CASA Version 4.6" (4 ALMA observations and data analysis)
- **GILDAS (MAPPING)** : independent flux check  
  > "through an independent effort using GILDAS available in the MAPPING package" (4 ALMA observations and data analysis)
- **Hyperz** : SED fitting for stellar mass  
  > "Stellar masses are determined by fitting the spectral energy distribution (SED) using Hyperz" (2.1 Stellar mass)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) line intensity range, Cycle 3 | 0.26 to 1.64 | not stated | Jy km/s | 1 | The line intensities (I$_{\rm CO}$) span a range of 0.26 to 1.64 Jy km s$^{-1}$ |
| PACS-787 CO size (major axis FWHM) | 1.96 | 0.54 | arcsec | 1 | $1.96\pm0.54\ensuremath{''}~(16.6~{\rm kpc; FWHM-major~axis}) |
| Gas masses | 1.4 to 7.5e10 | not stated | Msun | 4 | Gas masses for the ALMA starbursts (filled red circles) range between 1.4 and $7.5\times10^{10}$ M$_{\odot}$ |
| Gas depletion times | ~40-100 | not stated | Myr | 4 | short gas depletion times ranging from $\sim40-100$ Myrs |
| KS probability | 0.07 | not stated | percent | 3 | there is only a probability of 0.07% of randomly drawing values |
| Significance of mean offset in L'CO/<L'CO,MS> | 13 | not stated | sigma | 3 | is significant at the $13\sigma$ level |

## Qualitative findings

- CO emission is spatially offset from UV, co-spatial with IRAC stellar mass  
  > "the centroid of the CO emission was always co-spatial with the stellar mass distribution as traced by the $Spitzer$/IRAC 3.6 - 8 $\mu$m bands" (6 Location of CO-emitting regions)

## Claim tuples

- H: Starbursts have lower L'CO/LIR than MS galaxies | E: CO(2-1) in 12 starbursts vs the Sargent2014 comparison sample | R: Offset to lower L'CO; KS probability 0.07%, 13 sigma mean difference | F: CO decline is continuous with distance above MS | **supported**
- H: Starburst boost is due to higher SFE rather than gas fraction | E: Convert to Mgas with alpha_CO=1.3 | R: Gas fractions similar to MS; depletion times 40-100 Myr | F: SFE increases continuously; depends on alpha_CO | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Select by sSFR rather than SFR to avoid massive MS galaxies  
  > "By selecting galaxies based on their sSFR (cite: Rodighiero2011), we avoid the inclusion of star-forming galaxies at the massive end of the MS" (2.2 SFR)
- Alternative: alpha_CO=4.36 as alternative; PACS-472 removed due to misidentified redshift  
  > "This misidentification explains a lack of a CO detection at the expected observed frequency thus we remove it from the sample." (4 ALMA observations and data analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO is the dominant systematic uncertainty  
  > "the uncertainty on the appropriate value of $\alpha_{CO}$ is the dominant systematic error in our measure of derived properties" (4.2 Total molecular gas mass)
- Caveat (inferred, ours): alpha_CO calibrated on a single merger (PACS-787)
- Caveat (inferred, ours): Unresolved low-resolution data; CO(2-1)/CO(1-0)=0.85 assumed
- Caveat (inferred, ours): Small sample, selection effects and Eddington-type bias possible

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Final alpha_CO derivation in Silverman 2018
- Missing: Sargent2014 comparison data
- Missing: Cycle 1 and NOEMA data
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Project code is given and results are numeric, but imaging details and the alpha_CO derivation are missing.
- Rediscovery candidate: no, Imaging recipe is incomplete and key inputs come from other papers.

## Links

- Method: (cite: Sargent2014) (MS CO relations and comparison sample)
- Companion: (cite: Silverman2015a) (Cycle 1 sample)
- Related: FMOS-COSMOS
- Related: COSMOS

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00260.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 36,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
