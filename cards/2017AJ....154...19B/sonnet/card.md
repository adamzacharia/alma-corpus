# The Density of Mid-sized Kuiper Belt Objects from ALMA Thermal Observations

`2017AJ....154...19B` | The Astronomical Journal 2017 | first author: Brown, Michael E. | arXiv: 1702.07414 | DOI: 10.3847/1538-3881/aa6346

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: Can ALMA thermal observations of four satellite-bearing mid-sized KBOs improve diameter (and hence density) measurements, given uncertain millimeter emissivity and model uncertainty?  
  > "The substantial collecting area of the Atacama Large Millimeter Array allows significantly more precise measurements of thermal emission from outer solar system objects and could potentially greatly improve the density measurements." (abstract)
- Target **2002 UX25**: coordinates _not stated_; z/distance 40.22 AU (band 6), 40.18 AU (band 7) at observation  
  > "| 2002 UX25 | 6 | 2013-Nov-18/02:00-02:45 | 40.22 | 0.81 X 0.72 | Neptune | J0238+1636 |" (Table 1); distance from Table 1 observing geometry  
  > "| 2002 UX25 | 6 | 2013-Nov-18/02:00-02:45 | 40.22 | 0.81 X 0.72 | Neptune | J0238+1636 |" (Table 1)
- Target **Salacia**: coordinates _not stated_; z/distance 43.80 AU  
  > "| Salacia | 6 | 2013-Nov-04/23:05-24:06 | 43.80 | 0.94 X 0.73 | Neptune | J2253+1608 |" (Table 1); distance from Table 1 observing geometry  
  > "| Salacia | 6 | 2013-Nov-04/23:05-24:06 | 43.80 | 0.94 X 0.73 | Neptune | J2253+1608 |" (Table 1)
- Target **Quaoar**: coordinates _not stated_; z/distance 43.77 AU (band 6), 42.95 AU (band 7)  
  > "| Quaoar | 6 | 2013-Nov-04/22:10-22:45 | 43.77 | 1.20 X 0.63 | Neptune | J1733-1304 |" (Table 1); distance from Table 1 observing geometry  
  > "| Quaoar | 6 | 2013-Nov-04/22:10-22:45 | 43.77 | 1.20 X 0.63 | Neptune | J1733-1304 |" (Table 1)
- Target **Orcus**: coordinates _not stated_; z/distance 48.37 AU (band 6), 48.19 AU (band 7)  
  > "| Orcus | 6 | 2013-Nov-04/12:40-12:55 | 48.37 | 0.83 X 0.67 | Titan | J1007-0207 |" (Table 1); distance from Table 1 observing geometry  
  > "| Orcus | 6 | 2013-Nov-04/12:40-12:55 | 48.37 | 0.83 X 0.67 | Titan | J1007-0207 |" (Table 1)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (~230 GHz) and Band 7 (~345 GHz)  
  > "All observations in this paper were taken in Bands 6 and 7, near 230 and 350 GHz, in the “continuum” (or “TDM”) mode, with the standard frequency tunings." (2 Observations)
- frequencies and spectral setup: Band 6: 220–222, 222–224, 236–238, 238–240 GHz; Band 7: 337–339, 339–341, 349–351, 351–353 GHz; effective 230 and 345 GHz  
  > "In the final data analysis we average over the entire frequency range in both bands, and use 230 GHz and 345 GHz as the effective frequencies in our modeling." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array  
  > "All observations were undertaken with the 12-m array of the Atacama Large Millimeter Array (ALMA)." (2 Observations)
- configurations: mostly C32-3  
  > "The array was mostly in the C32-3 configuration, which yields a resolution of $\sim$0.9" in band 6 and $\sim$0.6" in band 7" (2 Observations)
- baselines: _not stated_
- angular resolution: 0.45-1.20 arcsec per observation (Table 1)  
  > "| Quaoar | 6 | 2013-Nov-04/22:10-22:45 | 43.77 | 1.20 X 0.63 | Neptune | J1733-1304 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: roughly 20-30 minutes on source per ~1 hr observation  
  > "Each observation was of order 1 hour in duration, including all calibration overheads, which resulted in roughly 20-30 minutes on source." (2 Observations)
- observing dates: mostly November 2013; one in March 2014  
  > "most of which were executed in November 2013 (with a single observation in March 2014)." (2 Observations)
- pi or archival as stated: _not stated_
- Other facility **Spitzer Space Telescope**: Thermal fluxes of targets used in fits (via literature)  
  > "we limit the initial modeling to shorter wavelengths to explore this effect using only the data from Spitzer and the shorter Herschel bands." (4 Spitzer/Herschel fits)
- Other facility **Herschel Space Telescope**: Thermal fluxes (to 250 μm used in fits)  
  > "we limit the initial modeling to shorter wavelengths to explore this effect using only the data from Spitzer and the shorter Herschel bands." (4 Spitzer/Herschel fits)
- External data: Spitzer/Herschel flux densities and previous diameters of the four KBOs  
  > "Table notes: $^{1}$ (cite: 2013_Fornasier)" (Table 3) [from (cite: 2013_Fornasier)]
- External data: Vanth 2.61 mag fainter than Orcus  
  > "We fix Vanth to be 2.61 magnitudes fainter than Orcus (cite: 2010_Brown)" (7 Effects of satellites) [from (cite: 2010_Brown)]
- External data: Phase integral relation q=0.336p_v+0.479  
  > "(cite: 2009_Brucker) shows that the icy Saturnian and Uranian satellites roughly follow a linear function given by $q=0.336p_v+0.479$." (3.2 MCMC thermal modeling) [from (cite: 2009_Brucker)]
- External data: Charon flux 7.0±0.07 mJy at 840 μm  
  > "which has been measured to have a flux of 7.0$\pm$0.07 mJy at 840 $\mu$m (cite: 2015DPS....4721004B)" (Conclusion) [from (cite: 2015DPS....4721004B)]

## Processing

### Calibration

- pipeline or manual: ALMA observatory pipeline calibration in CASA  
  > "Initial calibration of the data was provided by the ALMA observatory, and is done in the CASA reduction package via the ALMA pipeline (cite: 2014_Muders)." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Titan  
  > "Neptune and Titan were used as the absolute flux density scale calibrators for all observations (cite: 2012_Butler)." (2 Observations)
- flux scale uncertainty: ±5%  
  > "Flux densities measured by ALMA are specified to have an accuracy of $\pm$5%" (5 Spitzer/Herschel/ALMA fits)
- self calibration: _not stated_

### Imaging

- task: imaged in AIPS after export from CASA  
  > "At this point we exported the data from CASA and continued the data reduction in the AIPS package" (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We imaged each of the objects at each band with natural weighting." (2 Observations)
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

- Standard thermal model with beaming factor approach adopted  
  > "We will thus adopt the same general approach." (3.1 Background) [from (cite: 2013_Lellouch)]
- ALMA flux scale from Neptune/Titan models  
  > "Neptune and Titan were used as the absolute flux density scale calibrators for all observations (cite: 2012_Butler)." (2 Observations) [from (cite: 2012_Butler)]

### Not stated but needed to reproduce (our reading)

- Which CASA/pipeline and AIPS versions were used
- Flagging details and which antennas were removed
- Visibility-fitting model specifics in AIPS (point source vs. other)
- Spitzer/Herschel flux values and absolute magnitudes used as inputs (in tables of cited work)
- System masses used for density calculation
- Exact priors ranges for diameter, albedo, beaming factor
- Cleaning parameters (cell, image size, iterations)
- ALMA project code

## Analysis recipe

1. **Calibrate and image ALMA continuum**: ALMA pipeline calibration in CASA, then export to AIPS and image with natural weighting  
  > "We imaged each of the objects at each band with natural weighting." (2 Observations)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure flux densities and offsets**: Fit visibilities directly; cross-checked with image flux, CLEAN components, and image-plane Gaussian fit  
  > "We take the visibility fit value as the best value, as it avoids the biases of fitting in the image plane in the presence of correlated noise (cite: 2004_Greisen)." (2 Observations)
   - software: AIPS
   - fitting: _not stated_
   - validation: Four techniques agreed better than 1σ  
  > "We found good agreement (better than the final 1$\sigma$ uncertainty) for all of these techniques." (2 Observations)
3. **Fit thermal model to Spitzer/Herschel (and ALMA) data**: Standard thermal model with beaming factor; MCMC with free diameter, albedo, beaming factor; emissivity (0.8-1.0) and phase integral (factor 2 around Brucker fit) as nuisance parameters; also fit to H_V  
  > "free parameters are diameter, albedo, and beaming factor, with variations in emissivity and phase integral and the uncertainties in measured absolute magnitude also included as nuisance parameters." (3.2 MCMC thermal modeling)
   - software: emcee
   - parameter: 100 chains, 10^4 steps after 10^3 burn-in  
  > "run an ensemble of 100 chains through $10^4$ steps after a $10^3$ step initialization (“burn-in”) period." (3.2 MCMC thermal modeling)
   - assumption: Bolometric emissivity 0.8 to 1.0  
  > "We will take values from 0.8 to 1.0 to encompass the range of possible uncertainty and allow our emissivity to vary between these values." (3.2 MCMC thermal modeling)
   - fitting: emcee affine-invariant ensemble sampler, uniform priors, median and 68.2% range reported  
  > "we assign uniform priors to the parameters" (3.2 MCMC thermal modeling)
   - validation: Chains converge; compare with previous diameters  
  > "The chains converge with no obvious memory of initial condition." (3.2 MCMC thermal modeling)
4. **Derive effective millimeter emissivity**: Compare ALMA fluxes to Spitzer/Herschel-only model fits  
  > "In Figure [6](#emissivity) we use the Spitzer/Herschel only fits of the previous section to determine the effective emissivity as a function of wavelength." (5 Spitzer/Herschel/ALMA fits)
   - fitting: _not stated_
   - validation: _not stated_
5. **Account for satellites and compute densities**: Simple case D^2=D_e^2(1+10^{-ΔV/2.5})^-1; Orcus-Vanth two-body MCMC; satellite density 0.5 g/cm3 to primary density; subtract satellite mass from system mass  
  > "We will make the assumption that satellite densities can range from 0.5 g cm$^{-3}$ up to the density of the primary." (8 Densities)
   - software: emcee
   - assumption: Orcus and Vanth share beaming factor, emissivity, phase integral; Vanth albedo ≤ Orcus  
  > "we force Orcus and Vanth to have the same beaming factor, bolometric emissivity, and phase integral" (7 Effects of satellites)
   - fitting: _not stated_
   - validation: _not stated_
6. **Test ALMA-only diameters**: Rerun MCMC with ALMA data scaled by mean effective emissivity of other three objects; check against Charon  
  > "we assume that the effective emissivity of each object is the average of that measured from the other three objects." (Conclusion)
   - software: emcee
   - fitting: same MCMC  
  > "We use the Python package *emcee* (cite: 2013_Foreman-Mackey), which provides a convenient and parallel implementation of the (cite: 2012_Hou) affine invariant ensemble sampler for MCMC." (Multi-parameter Markov chain Monte Carlo thermal modeling)
   - validation: Charon diameter within 1.3σ of measured  
  > "which is within 1.3$\sigma$ of the measured value of 1212$\pm$6 km (cite: 2015_Stern)." (Conclusion)

## Software

- **CASA** : ALMA pipeline calibration  
  > "is done in the CASA reduction package via the ALMA pipeline (cite: 2014_Muders)." (2 Observations)
- **AIPS** : imaging and visibility fitting  
  > "At this point we exported the data from CASA and continued the data reduction in the AIPS package" (2 Observations)
- **emcee** : MCMC thermal modeling  
  > "We use the Python package *emcee* (cite: 2013_Foreman-Mackey)" (3.2 MCMC thermal modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA flux density 2002 UX25 band 6 | 0.49 | 0.03 | mJy | 2 | / 2002 UX25 /  6   / 0.49 $\pm$ 0.03 / |
| ALMA flux density Quaoar band 7 | 1.89 | 0.07 | mJy | 2 | /  Quaoar   /  7   / 1.89 $\pm$ 0.07 / |
| Spitzer/Herschel diameter Orcus (system) | 965 | 40 | km | 3 | /   Orcus   /  0.23$\pm$0.02  /  965 $\pm$ 40  /  958 $\pm$ 22  / |
| Spitzer/Herschel diameter Quaoar | 1083 | 50 | km | 3 | /  Quaoar   /  0.12$\pm$0.01  / 1083 $\pm$ 50  / 1073 $\pm$ 38  / |
| ALMA flux deficit vs Spitzer/Herschel prediction | ~30% lower | not stated | percent | 4 | The ALMA flux densities are systematically about 30% lower than predicted from the Spitzer/Herschel observations. |
| Orcus diameter (with Vanth) | 885 | +55/-80 | km | 5 | The median of the marginalized posterior distribution of the diameter is 885$^{+55}_{-80}$ km for Orcus |
| Orcus density | 1.65 | +0.34/-0.24 | g cm^-3 | 5 | We arrive at an Orcus density of $1.65^{+0.34}_{-0.24}$ g cm$^{-3}$. |
| ALMA-only diameter Orcus | 1075 | +121/-156 | km | 6 | Orcus is $1075\substack{+121 \\ -156}$ km |
| Charon ALMA-only-model diameter | 1355 | 110 | km | 6 | find a diameter of 1355$\pm$110 km |
| Mean effective emissivity of 4 KBOs | 0.685 | not stated | dimensionless | 4 | assumed emissivity of 0.685 – the average of the values for our 4 KBOs |

## Qualitative findings

- Millimeter effective emissivity is suppressed, preventing direct use of ALMA data for diameters.  
  > "effects due to effective emissivity at millimeter wavelengths make it difficult to use the millimeter data directly to find diameters and thus volumes for these bodies." (abstract)

## Claim tuples

- H: Can ALMA data reduce KBO diameter uncertainty? | E: Fit Spitzer/Herschel with and without ALMA, and ALMA-only with emissivity correction | R: ALMA fluxes ~30% below predictions; combined fits poor; ALMA-only diameters have 2-3x larger uncertainties | F: ALMA cannot improve sizes without independent mm emissivity knowledge | **supported**
- H: Are published radiometric size uncertainties realistic? | E: MCMC with emissivity and phase integral marginalized | R: Diameter uncertainties increased on average ~25% | F: Published uncertainties are likely too small | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: ALMA calibration error rejected as cause of flux deficit given ±5% accuracy and Neptune/Titan models  
  > "A calibration uncertainty of this magnitude in the ALMA data is unlikely, given the care with which these data are calibrated." (5 Spitzer/Herschel/ALMA fits)
- How they decided it was enough: _not stated_
- Limitation (authors): Vanth fit is not a detection; Vanth could be darker and larger  
  > "This model fit should not be considered a detection of Vanth" (7 Effects of satellites)
- Caveat (inferred, ours): Emissivity cause is inferred, not tested independently
- Caveat (inferred, ours): Only four objects, so average emissivity may not generalize
- Caveat (inferred, ours): Natural-weighted visibility fit details sparse

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA project code not printed
- Missing: Input Spitzer/Herschel fluxes and masses
- Missing: Software versions and priors
- Data volume (inferred): ~10-50 GB raw for 8 short continuum execution blocks
- Score (inferred): 3/5, Method clear and data small, but project code, inputs, and several settings are not stated.
- Rediscovery candidate: no, Project code not stated in paper and the main inputs come from literature tables not reproduced.

## Links

- Method: (cite: 2013_Foreman-Mackey) (emcee sampler)
- Method: (cite: 2012_Butler) (Neptune/Titan flux models)
- Companion: (cite: density_paper) (earlier KBO density-diameter trend)
- Companion: (cite: 2013_Fornasier) (previous Herschel/Spitzer diameters)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00619.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 49,
  "rate": 0.563
 },
 "evidence_ok": true
}
```
