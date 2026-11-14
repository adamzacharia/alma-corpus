# ALMA Cycle 1 Observations of the HH46/47 Molecular Outflow: Structure, Entrainment, and Core Impact

`2016ApJ...832..158Z` | The Astrophysical Journal 2016 | first author: Zhang, Yichen | arXiv: 1602.02388 | DOI: 10.3847/0004-637X/832/2/158

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: How much mass, momentum and energy does the HH 46/47 outflow carry once CO optical depth is corrected, how is it entrained, and can it disperse its parent core?  
  > "We use $^{13}\mbox{CO}$ (1-0) and $\mbox{C}^{18}\mbox{O}$ (1-0) emission to correct for the $^{12}\mbox{CO}$ (1-0) optical depth to accurately estimate the outflow mass, momentum and kinetic energy." (abstract)
- Target **HH 46/47 (HH 47 IRS) molecular outflow**: coordinates map centre 08:25:40, -51:00:59 (J2000)  
  > "located on the outskirts of the Gum Nebula at a distance of 450 pc" (Introduction); "centered at $8^{\mathrm{h}}25^{\mathrm{m}}40^{\mathrm{s}}$, $-51^\circ00\ensuremath{'}59\ensuremath{''}$ (J2000)" (Observations); z/distance 450 pc  
  > "located on the outskirts of the Gum Nebula at a distance of 450 pc" (Introduction); "centered at $8^{\mathrm{h}}25^{\mathrm{m}}40^{\mathrm{s}}$, $-51^\circ00\ensuremath{'}59\ensuremath{''}$ (J2000)" (Observations); distance from Schwartz77; Reipurth00; Noriega04  
  > "located on the outskirts of the Gum Nebula at a distance of 450 pc" (Introduction); "centered at $8^{\mathrm{h}}25^{\mathrm{m}}40^{\mathrm{s}}$, $-51^\circ00\ensuremath{'}59\ensuremath{''}$ (J2000)" (Observations)

## Data provenance

- ALMA projects: 2012.1.00382.S
- bands: Band 3 (3 mm)  
  > "Two different correlator configurations were used to provide images on six molecular lines and two 2 GHz-wide continuum bands in Band 3." (Observations)
- frequencies and spectral setup: Config 1: 12CO 0.2 km/s channels, C17O 0.1 km/s, continuum 100.7 and 102.7 GHz; Config 2: 13CO, C18O, CS, C34S at 0.1 km/s  
  > "The continuum emission was observed with two 1875 MHz-wide bands." (Observations); "Each line was observed with a channel width of 30.5 kHz ($0.1~\mbox{km s}^{-1}$)" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array, 7m array (ACA), and 12m total power  
  > "Data from both the 12m array and the ACA (including the 7m array and the 12m total power dishes) were obtained." (Observations)
- configurations: _not stated_
- baselines: 12m: 12-528 m (12CO/C17O), 12-340 m (others); 7m: 7-44 m  
  > "The combined interferometric data have projected baselines ranging from 7 to 525 m for $^{12}\mbox{CO}$ and $\mbox{C}^{17}\mbox{O}$" (Observations)
- angular resolution: 1.3"x1.3" (12CO); 3.2"x1.6" (13CO, C18O)  
  > "The resulting synthesized beam is $1.3\ensuremath{''} \times 1.3\ensuremath{''}$ for the $^{12}\mbox{CO}$ data cube and $3.2\ensuremath{''} \times 1.6\ensuremath{''}$ for the $^{13}\mbox{CO}$ and $\mbox{C}^{18}\mbox{O}$ data cubes." (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Nov 5, 2013 to Apr 11, 2015  
  > "The observations were carried out using ALMA from November 5, 2013 to April 11, 2015." (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO 1-0 (115.27 GHz)
- Line: 13CO 1-0 (110.2 GHz)
- Line: C18O 1-0 (109.78 GHz)
- Line: CS 2-1 (97.98 GHz)
- Line: C17O 1-0 (112.36 GHz)
- Line: C34S 2-1 (96.41 GHz)
- External data: Core of 5 Msun within 0.1 pc with density profile rho ∝ r^-1.8  
  > "found that the remaining core has $5~M_\odot$ within 0.1 pc ($46\ensuremath{''}$, 20800 AU) with the radial density profile following a power-law $\rho\propto r^{-1.8}$" (4.1) [from van Kempen et al. 2009 (cite: vanKempen09)]
- External data: Abundance ratios X12,13=62 and X13,18=8.7  
  > "we adopt $X_{12,13}=62$ ((cite: Langer93)), $X_{13,18}=8.7$ (from \[$^{16}$O\]/\[$^{18}$O\]=540, (cite: Wilson92))" (3.7) [from Langer93; Wilson92]
- External data: Cloud LSR velocity 5.3 km/s  
  > "which is 5.3 $\mbox{km s}^{-1}$ ((cite: vanKempen09))" (2) [from vanKempen09]

## Processing

### Calibration

- pipeline or manual: Data edited, calibrated and imaged in CASA; details not given  
  > "The data were edited, calibrated and imaged in CASA." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN; 12m+7m combined with statwt weights; total power combined with feather  
  > "The data were imaged using the CLEAN algorithm." (Observations); "The interferometric data and the total power data were then combined in the image space using the CASA task *feather*." (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "Robust weighting with the robust parameter of 0.5 is used in the clean process." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: separate clean region per channel around brightest emission  
  > "For the spectral data we defined a different clean region for each channel, encircling the area with the brightest emission." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m+7m with statwt weights, then feather with total power  
  > "The 12m array and the 7m array visibilities were combined with their weighting factors estimated from the data noise using the CASA task *statwt*." (Observations)
- smoothing: _not stated_
- final beam: 1.3"x1.3" (12CO); 3.2"x1.6" (13CO, C18O)  
  > "The resulting synthesized beam is $1.3\ensuremath{''} \times 1.3\ensuremath{''}$ for the $^{12}\mbox{CO}$ data cube" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Continuum mass calculation method  
  > "using the method described in Paper I and assuming a dust temperature of 30 K" (3.1) [from Paper I (cite: Arce13)]
- Optical depth correction method  
  > "We estimate the correction factor to the optical depth following the method outlined by (cite: Dunham14)" (3.7) [from (cite: Dunham14)]
- Wide-angle wind shell model  
  > "Following the simple analytical description by (cite: Lee00)" (4.2) [from (cite: Lee00)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/pipeline details
- Self-calibration and flux scale uncertainty
- Line-free channels and continuum subtraction method
- Cell size, image size, clean threshold
- Total power and feather scaling parameters
- Exact pixel regions for outflow sub-regions
- Visually fitted model parameters (no fitting code or algorithm given)

## Analysis recipe

1. **Measure continuum and dust mass**: Peak and flux in 8" radius circle; mass via Paper I method  
  > "Integrated over a circle with radius of 8$\ensuremath{''}$, the total flux density of the continuum emission is $11\pm 0.012$ mJy." (3.1)
   - software: CASA
   - assumption: Tdust 30 K, gas-to-dust 100, beta=1, kappa(3mm)=0.9 cm2/g  
  > "assuming a dust temperature of 30 K, a gas-to-dust mass ratio of 100, and an emissivity spectral index ($\beta$) of 1." (3.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive CO optical depth correction**: Intensity ratios 13CO/C18O and 12CO/13CO per channel (pixels >5 sigma), weighted mean, parabola fit  
  > "we fit a parabola to the measured intensity ratios with the minimum point fixed at zero velocity" (3.7)
   - parameter: X12,13=62, X13,18=8.7  
  > "we adopt $X_{12,13}=62$ ((cite: Langer93)), $X_{13,18}=8.7$" (3.7)
   - assumption: Same Tex and beam filling factor for all isotopologues, C18O optically thin, LTE  
  > "have the same excitation temperature $T_{\mathrm{ex}}$ and beam filling factor, and that $\mbox{C}^{18}\mbox{O}$ is optically thin" (3.7)
   - fitting: Weighted parabola fit, weights inverse square of uncertainties  
  > "The weights are inversely proportional to the square of the uncertainties of the pixel intensity ratios." (3.7)
   - validation: reduced chi2 0.22 and 0.82  
  > "with a reduced $\chi^2$ of 0.22." (3.7)
3. **Compute outflow mass, momentum, energy**: LTE column density per channel with opacity correction; velocity cuts exclude cloud; max column density chosen where several isotopologues detected  
  > "At the pixels where more than one CO isotopologues are detected, we choose the highest column density calculated from these CO isotopologues." (3.7)
   - parameter: Tex = 15 K and 50 K; inclination 40 deg for momentum/energy  
  > "we will calculate the mass and other properties of the outflow using two typical values of $T_{\mathrm{ex}}$, 15 K and 50 K." (3.7)
   - assumption: CO abundance 1e-4 relative to H2; 2.34e-24 g per H2; beam filling factor 1  
  > "We adopt an abundance of $^{12}\mbox{CO}$ of $10^{-4}$ relative to $\mbox{H}_2$, and a gas mass of $2.34 \times 10^{-24}$ g per $\mbox{H}_2$ molecules." (3.7)
   - fitting: Power-law fit to mass spectra m(v) ∝ v^-gamma  
  > "We fit the combined mass spectra with power laws in a form of $m(v)\propto v^{-\gamma}$" (3.7)
   - validation: Compared with Paper I and survey values  
  > "are similar to those measured in Paper I with ALMA cycle 0 data." (3.7)
4. **Wide-angle wind model of blue lobe**: Parabolic shell with Hubble-law velocity compared with PV diagrams and channel maps  
  > "the morphology of such an outflowing shell is described by a parabola in the form of $z=CR^2$" (4.2)
   - fitting: Visual inspection of fits  
  > "The uncertainties are the range of the values with which relatively good fits can be achieved by visual inspection." (4.2)
   - validation: Inclination consistent with optical jet  
  > "The fitted inclination of the outflow is consistent with the value derived from the observations of the optical jet" (4.2)
5. **Model envelope rotation and infall in PV diagrams**: Analytic rotating infalling envelope model with fixed Rout, k_rho, k_T and T1000  
  > "we fix $R_\mathrm{out}=6\ensuremath{''}$ (2700 AU) from the current observation, and $k_\rho=1.8$" (4.3)
   - assumption: v_rot=j/R, infall from energy conservation  
  > "the rotation velocity is assumed to be inversely proportional to the radius, therefore conserving angular momentum" (4.3)
   - fitting: Not a detailed fit; example model  
  > "We are not performing a detailed model fit here" (4.3)
   - validation: Compared by eye to 13CO and C18O PV diagrams  
  > "The model reproduces most of the features in the PV diagrams" (4.3)
6. **Estimate CS outflow specific angular momentum and launch radius**: Velocity gradients across axis; Anderson03 and Ferreira06 formulas  
  > "We then can estimate the launching radius of this wind using the formula provided by (cite: Anderson03)" (4.4)
   - assumption: Angular momentum transport equal to linear momentum transport  
  > "Assuming the transport of angular momentum from a jet to its entrained outflow is on the same level as the jet’s linear momentum transport" (4.4)
   - fitting: _not stated_
   - validation: Authors call it tentative  
  > "We admit that this is only tentative evidence of outflow rotation." (4.4)

## Software

- **CASA** : Calibration, imaging, statwt, feather  
  > "The data were edited, calibrated and imaged in CASA." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak intensity | 6.4 | not stated | mJy/beam | 1 | has an intensity of 6.4 $\mbox{mJy}~\mbox{beam}^{-1}$ (0.33 K) |
| Continuum dust mass | 0.3 | not stated | Msun | 1 | Such a total flux corresponds to a mass of 0.3 $M_\odot$ |
| Total outflow mass (Tex=15 K) | 1.6 | not stated | Msun | 3 | the measured total mass of the CO outflow is 1.6 $M_\odot$ |
| Total momentum (inclination corrected) | 1.9 | not stated | Msun km/s | 3 | the total momentum is 1.9 $M_\odot~\mbox{km s}^{-1}$ (after correcting for inclination) |
| Total energy (inclination corrected) | 3.9e43 | not stated | erg | 3 | the total energy is $3.9\times 10^{43}$ erg (after correcting for inclination) |
| Mass spectrum slope, red lobe | -3.43 | 0.04 | dimensionless | 3 | We found a slope of $\gamma=-3.43\pm0.04$ for the red-shifted outflow |
| Mass spectrum slope, blue lobe | -2.78 | 0.11 | dimensionless | 3 | a slope of $\gamma=-2.78\pm0.11$ for the blue-shifted outflow |
| Wide-angle wind model inclination | 40 | 1 | deg | 4 | $i=40^\circ\pm 1^\circ$, $C=0.4\pm0.1~\mathrm{arcsec}^{-1}$, and $v_0=1.5\pm0.1~\mbox{km s}^{-1}~\mathrm{arcsec}^{-1}$ |
| Dynamical central mass | 0.3 | not stated | Msun | 5 | the dynamical central mass $m_*=0.3~M_\odot$ |
| Envelope infall rate | 3.2e-6 | not stated | Msun/yr | 5 | $\dot{m}_\mathrm{infall}=m_\mathrm{env}v_\mathrm{infall}/R=3.2 \times 
10^{-6}~M_\odot~\mathrm{yr}^{-1}$ |
| CS outflow specific angular momentum | 1600 | not stated | AU km/s | 6 | The specific angular momentum is then $j_\mathrm{CS} \approx 1600~\mbox{AU km s}^{-1}$ |

## Qualitative findings

- Opacity correction raises 12CO mass, momentum, energy by 8.5, 4.9, 2.4; 13CO/C18O add a further factor 3 in mass  
  > "Correcting for the $^{12}\mbox{CO}$ optical depth increases the estimated mass of the outflow by a factor of 8.5, the momentum by a factor of 4.9, and the kinetic energy by a factor of 2.4." (Summary and Conclusions)

## Claim tuples

- H: Optical depth and dense low-velocity gas were underestimated in earlier outflow budgets | E: Used 13CO and C18O to correct 12CO opacity and add low-velocity gas | R: Mass up by 8.5x, then a further 3x for red lobe; total 1.6 Msun | F: Outflow properties are significantly higher than survey values | **supported**
- H: The outflow can disperse its core within the embedded phase | E: Compared outflow and ambient mass distributions; estimated destruction timescale and efficiencies | R: Destruction time 0.52-1 Myr; efficiency 1/3 to 1/4 | F: Outflow can disperse the core and sets core-to-star efficiency | **supported**
- H: Entrainment is by jet bow-shocks and/or a wide-angle wind | E: Channel maps, PV diagrams, wind model, mass spectra | R: Red cavity wall has nested shells; blue high-velocity gas fit by wind model | F: Both mechanisms co-exist on both sides | **supported**
- H: CS traces a rotating outflow entrained by a disk wind | E: PV cuts perpendicular to CS jet-like structure | R: Velocity gradients; j about 1600 AU km/s; launch radius about 60 AU | F: Tentative toroidal entrainment by disk wind from large radii | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Specific angular momentum is only an upper limit; envelope model is over-simplified; CO depletion neglected  
  > "We note that the measured specific angular momentum is only an upper limit" (4.4); "the geometry or density/temperature distribution of the envelope in this model is over-simplified" (4.3)
- Caveat (inferred, ours): Single Tex and constant abundance ratios assumed across outflow
- Caveat (inferred, ours): Model fits by eye with no formal uncertainties
- Caveat (inferred, ours): Cloud/outflow separation by velocity cut is arbitrary
- Caveat (inferred, ours): Core destruction timescale depends on assumed outflow age

## Reproducibility

- Data public (paper): ALMA project 2012.1.00382.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2012.1.00382.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and calibration scripts
- Missing: Exact regions, masks, clean thresholds
- Missing: Model fitting details
- Data volume (inferred): hundreds of GB to ~1 TB raw (many 12m, 7m and TP execution blocks, mosaics)
- Score (inferred): 5/5, Data are public and the equations and adopted values are clear, but calibration/imaging details and masks are sparse and model fits are by eye.
- Rediscovery candidate: no, Imaging settings and regions are underspecified, and several key results come from visual model fitting.

## Links

- Method: Dunham et al. 2014 (cite: Dunham14) (Opacity correction method)
- Method: Lee et al. 2000 (cite: Lee00) (Wide-angle wind shell model)
- Companion: Arce et al. 2013 (cite: Arce13) (Paper I, ALMA Cycle 0 study of HH 46/47)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 48,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
