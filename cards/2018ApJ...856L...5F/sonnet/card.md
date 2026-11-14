# ALMA Detections of CO Emission in the Most Luminous, Heavily Dust-obscured Quasars at z &gt; 3

`2018ApJ...856L...5F` | The Astrophysical Journal Letters 2018 | first author: Fan, Lulu | arXiv: 1711.10615 | DOI: 10.3847/2041-8213/aab496

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What are the molecular gas properties and kinematics (merger or outflow signatures) of three WISE-selected hyper-luminous obscured QSOs at z>3, and do they follow the L'CO-LFIR relation of unobscured QSOs?  
  > "Our purpose is to study the molecular gas properties and search the clues for feeding and feedback processes in the most luminous obscured QSOs." (Introduction)
- Target **W0149+2350**: coordinates 01:49:46.17 +23:50:14.66  
  > "W0149+2350 | 3.228 | 03-08-2016 | 40" (Table 1); z/distance z_opt = 3.228; z_CO = 3.2298-3.2432  
  > "W0149+2350 | 3.228 | 03-08-2016 | 40" (Table 1); distance from optical redshift from Wu et al. 2012; CO redshift from Gaussian fits  
  > "W0149+2350 | 3.228 | 03-08-2016 | 40" (Table 1)
- Target **W0220+0137**: coordinates 02:20:52.124 +01:37:11.23  
  > "W0220+0137 | 3.122 | 25-07-2016 | 44" (Table 1); z/distance z_opt = 3.122; z_CO = 3.1341, 3.1386  
  > "W0220+0137 | 3.122 | 25-07-2016 | 44" (Table 1); distance from optical redshift from Wu et al. 2012; CO redshift from Gaussian fits  
  > "W0220+0137 | 3.122 | 25-07-2016 | 44" (Table 1)
- Target **W0410-0913**: coordinates 04:10:10.606 -09:13:04.96  
  > "W0410$-$0913 | 3.592 | 24-07-2016 | 39" (Table 1); z/distance z_opt = 3.592; z_CO = 3.6312, 3.6251  
  > "W0410$-$0913 | 3.592 | 24-07-2016 | 39" (Table 1); distance from optical redshift from Wu et al. 2012; CO redshift from Gaussian fits  
  > "W0410$-$0913 | 3.592 | 24-07-2016 | 39" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01148.S
- bands: Band 3  
  > "Observations were carried out with ALMA during Cycle 3 using the Band 3 receiver." (Targets, Observations and Analysis)
- frequencies and spectral setup: One spectral window on redshifted CO(4-3) (line mode, centres 109.054, 109.998, 100.393 GHz); three other spectral windows in continuum mode  
  > "The spectral window of the redshifted CO$(4-3)$ line used a setup for spectral line mode, while the three remaining spectral windows used a continuum mode setup." (Targets, Observations and Analysis)
- continuum bandwidth: _not stated_
- arrays: 39-44 antennas  
  > "W0220+0137 | 3.122 | 25-07-2016 | 44" (Table 1)
- configurations: _not stated_
- baselines: 15 to 1124 m (1396 m for W0149+2350)  
  > "The telescope configuration included baselines between 15 and 1124 m (though 1396 m for W0149+2350)." (Targets, Observations and Analysis)
- angular resolution: 0.2 arcsec (W0149+2350)  
  > "The angular resolution is 0.2 arcsec, which corresponds to $\sim$1.5 kpc at $z\sim3.2$." (Results)
- max recoverable scale: _not stated_
- sensitivity: rms ~0.59, 1.04, 0.84 mJy/beam per ~21-23.5 km/s channel  
  > "In the line spectral window, the rms is $\sim0.59$ mJy/beam per 21.5 km s$^{-1}$ channel." (Results)
- time on source: _not stated_
- observing dates: 03-08-2016, 25-07-2016, 24-07-2016  
  > "W0149+2350 | 3.228 | 03-08-2016 | 40" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=4-3 (not stated)
- Other facility **HST**: F160W images for overlay (W0149+2350, W0410-0913)  
  > "overlaid on the *HST* F160W image" (Results)
- Other facility **Herschel**: FIR photometry used in SED decomposition  
  > "considering the blended *Herschel* photometry" (Discussions)
- Other facility **WISE**: Sample selection (W1W2 dropouts)  
  > "by using a so-called “*W1W2* dropout" method" (Targets, Observations and Analysis)
- External data: Optical redshifts of the targets  
  > "using the optical redshift taken from (cite: wu2012)" (Targets, Observations and Analysis) [from (cite: wu2012)]
- External data: L'CO-LFIR comparison compilation of other populations  
  > "other populations from compilation in (cite: carilli2013)" (Discussions) [from (cite: carilli2013)]

## Processing

### Calibration

- pipeline or manual: Observatory pipeline reduction with minor extra flagging  
  > "The results from the pipeline reduction[^2] carried out by the observatory were generally sufficient with only some minor extra flagging, which did not significantly change the final result." (Targets, Observations and Analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636, J0006-0623, J0423-0120  
  > "W0149+2350 | 3.228 | 03-08-2016 | 40 | J0237+2848 | J0238+1636 | J0151+2517" (Table 1)
- flux scale uncertainty: 10%  
  > "For the absolute flux calibration, we adopted a conservative uncertainty of 10%." (Targets, Observations and Analysis)
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

- SED decomposition method for L_FIR  
  > "with SED decomposition method used in our previous work (cite: fan2016b)" (Discussions) [from (cite: fan2016b)]
- CO line luminosity via Equation 3  
  > "The CO line luminosities are derived from the Gaussian fit results, using Equation 3 in (cite: solomon2005)." (Results) [from (cite: solomon2005)]
- CO excitation and alpha_CO  
  > "Adopting QSO excitation $L'_{\rm CO(4-3)}/L'_{\rm CO(1-0)} = 0.87$ and the CO-to-gas mass conversion factor" (Discussions) [from (cite: carilli2013)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Imaging parameters (weighting, robust, cell, image size, deconvolver, clean threshold)
- Continuum-subtraction and line-free channels
- Exact UVMULTIFIT model setup and initial guesses
- Image-plane beam sizes
- PV diagram slit position and width
- SED fitting details for L_FIR and the resulting values
- Rest frequency of CO(4-3) used
- Integration times

## Analysis recipe

1. **Calibrate and image**: Observatory pipeline reduction with minor extra flagging, in CASA  
  > "Reduction, calibration, and imaging were done using CASA" (Targets, Observations and Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Extra flagging did not significantly change the result  
  > "with only some minor extra flagging, which did not significantly change the final result" (Targets, Observations and Analysis)
2. **Fit continuum and line properties**: UVMULTIFIT fits of continuum and CO(4-3) line; Gaussian line components  
  > "Using UVMULTIFIT (cite: martividal14), we estimate the continuum and emission line properties." (Results)
   - software: UVMULTIFIT
   - parameter: Single vs double Gaussian compared with reduced chi2  
  > "which gives a better fit with the reduced $\chi^2=0.74$ than a single Gaussian does with reduced $\chi^2=0.86$" (Results)
   - assumption: All lines assumed Gaussian  
  > "All lines are assumed to be Gaussian" (Results)
   - fitting: Gaussian line fits in the uv plane  
  > "Using UVMULTIFIT (cite: martividal14), we estimate the continuum and emission line properties. The CO line luminosities are derived from the Gaussian fit results" (Results)
   - validation: Reduced chi2 comparison  
  > "We fit the CO$(4-3)$ line with a double Gaussian, which gives a better fit with the reduced $\chi^2=0.74$ than a single Gaussian does with reduced $\chi^2=0.86$." (Results)
3. **Derive L'CO and molecular gas mass**: L'CO from Solomon & Vanden Bout; Mgas from alpha_CO and r41  
  > "we derive the molecular gas masses of the three dust-obscured QSOs" (Discussions)
   - assumption: L'CO(4-3)/L'CO(1-0)=0.87; alpha_CO=0.8 Msun (K km/s pc^2)^-1  
  > "$\alpha_{CO}=0.8 M_\odot\,({\rm K\,km\,s^{-1}\,pc^2})^{-1}$" (Discussions)
   - assumption: Flat LCDM, H0=70, OmegaM=0.3, OmegaL=0.7  
  > "we assume a flat ${\rm \Lambda}$CDM cosmology with $H_0 = 70$ km s$^{-1}$, $\Omega_M = 0.3$, and $\Omega_\Lambda = 0.7$" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare L'CO with L_FIR**: SED decomposition including new ALMA continuum to get L_FIR; plot against compilation  
  > "The new ALMA continuum measurements have been included." (Discussions)
   - parameter: beta=2.0 for W0220+0137 and W0410-0913 (1.6 previously)  
  > "a larger $\beta$ (2.0, instead of the previously adopted value 1.6) is required" (Discussions)
   - assumption: L_FIR is total of components due to blended Herschel photometry  
  > "However, we take the estimated $L_{\rm FIR}$ as the *total* luminosity of different components considering the blended *Herschel* photometry." (Discussions)
   - fitting: _not stated_
   - validation: L_FIR changes by up to 0.1 dex with beta  
  > "the derived $L_{\rm FIR}$ only have a slight difference (up to 0.1 dex)" (Discussions)
5. **Kinematics via PV diagrams**: Position-velocity diagrams of CO(4-3) to assess merger/outflow/rotation  
  > "we plot position-velocity (PV) diagrams of the CO$(4-3)$ emission line" (Discussions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Reduction, calibration, imaging  
  > "Reduction, calibration, and imaging were done using CASA" (Targets, Observations and Analysis)
- **UVMULTIFIT** : Fitting continuum and line properties in uv plane  
  > "Using UVMULTIFIT (cite: martividal14), we estimate the continuum and emission line properties." (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| W0149 total L'CO(4-3) | 2.40 | 0.50 | 1e10 K km/s pc^2 | 3 | W0149-total /  /  /  /  /  / $0.81\pm 0.18$ / $2.40\pm0.50$ / $1.7\pm0.4$ |
| W0149 total Mgas | 1.7 | 0.4 | 1e10 Msun | 3 | W0149-total /  /  /  /  /  / $0.81\pm 0.18$ / $2.40\pm0.50$ / $1.7\pm0.4$ |
| W0220 total L'CO(4-3) | 3.39 | 0.65 | 1e10 K km/s pc^2 | 3 | W0220-total /  /  /  /  /  / $1.21\pm 0.23$ / $3.39\pm0.65$ / $2.4\pm0.5$ |
| W0220 total Mgas | 2.4 | 0.5 | 1e10 Msun | 3 | W0220-total /  /  /  /  /  / $1.21\pm 0.23$ / $3.39\pm0.65$ / $2.4\pm0.5$ |
| W0410 total L'CO(4-3) | 17.90 | 1.50 | 1e10 K km/s pc^2 | 3 | W0410-total /  /  /  /  /  / $5.07\pm 0.42$ / $17.90\pm1.50$ / $12.5\pm1.1$ |
| W0410 total Mgas | 12.5 | 1.1 | 1e10 Msun | 3 | W0410-total /  /  /  /  /  / $5.07\pm 0.42$ / $17.90\pm1.50$ / $12.5\pm1.1$ |
| W0410 comp1 peak flux | 6.69 | 0.37 | mJy | 2 | W0410-comp1 / 04:10:10.606 / $-$09:13:04.96 / $3.6312\pm0.0003$ / $6.69\pm0.37$ / $560\pm 44$ |
| W0149 continuum lower/upper sideband | 111/171 | 28/41 | uJy | 2 | $111\pm28$/$171\pm41$ $\mu$Jy |
| W0220 continuum lower/upper sideband | 78/180 | 24/31 | uJy | 2 | $78\pm24$/$180\pm31$ $\mu$Jy |
| W0410 continuum lower/upper sideband | 121/258 | 37/40 | uJy | 2 | $121\pm37$/$258\pm40$ $\mu$Jy |

## Qualitative findings

- All three QSOs show complex CO velocity structures disfavoring a rotating disk  
  > "The PV-diagrams also suggest that all of three QSOs have complex velocity structures, which may disfavor the scenario of rotation disk." (Discussions)
- No serendipitous continuum or CO companions in the Band 3 FOV  
  > "we have not found any serendipitous detection of dust continuum or CO emission line around our obscured QSOs" (Discussions)

## Claim tuples

- H: Obscured hyper-luminous QSOs at z>3 are gas-rich | E: CO(4-3) detection and conversion to Mgas | R: Total gas masses 1.7e10 to 1.25e11 Msun | F: The QSOs are gas-rich systems | **supported**
- H: Obscured QSOs follow the L'CO-LFIR relation of unobscured QSOs | E: Compare with Carilli & Walter compilation | R: Similar relation | F: Possibly similar objects at different evolutionary stages | **supported**
- H: CO kinematics indicate merger or outflow | E: Multi-Gaussian line fits and PV diagrams | R: Three components in W0149; double Gaussian in other two | F: Possible merger in W0149+2350; possible outflows in W0220+0137 and W0410-0913 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Merger vs outflow interpretations cannot be fully distinguished  
  > "though the scenario of having a molecular outflow can not be excluded" (Discussions)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample and limited S/N for double-Gaussian preference; W0410 line truncated at band edge  
  > "despite the choice is not as convincing as for W0149+2350 due to the limited signal-to-noise" (Discussions)
- Caveat (inferred, ours): Double-Gaussian preference rests on small reduced chi2 differences
- Caveat (inferred, ours): Outflow inference from asymmetric profiles is weak
- Caveat (inferred, ours): Low resolution cannot separate components spatially
- Caveat (inferred, ours): Optical redshift offset in W0410 of ~2500 km/s unexplained

## Reproducibility

- Data public (paper): Project code and PI given; public status not stated  
  > "ADS/JAO.ALMA#2015.1.01148.S (PI: Lulu Fan)" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: CASA version
- Missing: UVMULTIFIT model details
- Missing: L_FIR values and SED fits
- Data volume (inferred): ~20-50 GB raw for three Band 3 execution blocks
- Score (inferred): 3/5, Data are identifiable and results tabulated, but imaging and fitting details are largely missing.
- Rediscovery candidate: no, Imaging and fit setup are insufficiently specified, though the data are probably public after the proprietary period.

## Links

- Method: (cite: martividal14) (UVMULTIFIT uv-plane fitting)
- Method: (cite: solomon2005) (CO luminosity equation)
- Companion: (cite: fan2016b) (SED decomposition for L_FIR)
- Companion: (cite: wu2012) (Source selection and optical redshifts)
- Related: WISE W1W2-dropout hot DOG sample

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 50,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
