# 400 pc Imaging of a Massive Quasar Host Galaxy at a Redshift of 6.6

`2019ApJ...874L..30V` | The Astrophysical Journal Letters 2019 | first author: Venemans, Bram P. | arXiv: 1903.09202 | DOI: 10.3847/2041-8213/ab11cc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the distribution and kinematics of [C II] gas and dust on ~400 pc scales in the z=6.6 quasar host J0305-3150, and what causes the observed cavities?  
  > "The unprecedented high resolution of the observations reveals a complex morphology of gas within 3 kpc of the accreting central black hole." (abstract)
- Target **J0305-3150**: coordinates 03h05m16.919s, -31d50m55.86s (NIR position)  
  > "The resulting NIR location of the quasar is 03$^\mathrm{h}$05$^\mathrm{m}$16$^\mathrm{s}\!$.919, –31$^\circ$50$^\prime$55.86$''$ with an uncertainty of 0.02$''$" (3.1 Dust and [C II] emission); "resulting in $z_\mathrm{[CII]}=6.61391\pm0.00015$" (3.1 Dust and [C II] emission); z/distance z_[CII] = 6.61391 ± 0.00015  
  > "The resulting NIR location of the quasar is 03$^\mathrm{h}$05$^\mathrm{m}$16$^\mathrm{s}\!$.919, –31$^\circ$50$^\prime$55.86$''$ with an uncertainty of 0.02$''$" (3.1 Dust and [C II] emission); "resulting in $z_\mathrm{[CII]}=6.61391\pm0.00015$" (3.1 Dust and [C II] emission); distance from Gaussian fit to the [C II] line in these data  
  > "The resulting NIR location of the quasar is 03$^\mathrm{h}$05$^\mathrm{m}$16$^\mathrm{s}\!$.919, –31$^\circ$50$^\prime$55.86$''$ with an uncertainty of 0.02$''$" (3.1 Dust and [C II] emission); "resulting in $z_\mathrm{[CII]}=6.61391\pm0.00015$" (3.1 Dust and [C II] emission)

## Data provenance

- ALMA projects: 2017.1.01532.S
- bands: _not stated_
- frequencies and spectral setup: [C II] at 249.6 GHz in one 1.875 GHz band; three other 1.875 GHz bands for continuum at 252.1, 264.6, 266.6 GHz  
  > "Three other bandpasses of 1.875 GHz each were placed to measure the FIR continuum at observed frequencies of 252.1, 264.6, and 266.6 GHz." (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-8  
  > "in configuration C43-8" (2 ALMA Observations)
- baselines: 92 to 13,894 m, 43 antennas  
  > "The number of antennas was 43 with baselines between 92 and 13,894 m." (2 ALMA Observations)
- angular resolution: 0.076" x 0.071" (410 x 385 pc), natural weighting  
  > "The final beam using natural weighting has a size of 0.076$''$ $\times$ 0.071$''$, which corresponds to 410 pc $\times$ 385 pc at $z=6.6$." (2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: 87 uJy/beam per 30 MHz (36 km/s) bin  
  > "The rms noise around the redshifted \[C II\] line is 87 $\mu$Jy beam$^{-1}$ per 30 MHz bin (36 km s$^{-1}$)." (2 ALMA Observations)
- time on source: 7.6 hr total, 3.5 hr on-source  
  > "The total observing time was 7.6 hr, of which 3.5 hr were on-source." (2 ALMA Observations)
- observing dates: 2017 November 12-18  
  > "we observed J0305–3150 between 2017 November 12 and 18 with ALMA in configuration C43-8." (2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um (2P3/2-2P1/2) (not stated)
- Other facility **GAIA DR2**: Astrometric correction of the NIR quasar position  
  > "we recomputed the near-infrared (NIR) location of the quasar by correcting the positions of nearby stars with a match in the GAIA DR2 catalog" (3.1 Dust and [C II] emission)
- External data: Black hole mass ~1e9 Msun  
  > "has a black hole mass of $\sim1\times10^9$ $M_\ensuremath{\odot}$ (cite: ven13; der14; maz17b)" (1 Introduction) [from (cite: ven13; der14; maz17b)]
- External data: Star formation rate ~1500 Msun/yr  
  > "for the observed star formation rate of 1500 $M_\ensuremath{\odot}$ yr$^{-1}$ (cite: ven16)" (5 Origin of the [C II] cavities) [from (cite: ven16)]
- External data: ISM density 1e5 cm^-3 from multiline analysis  
  > "has been estimated to be 10$^5$ cm$^{-3}$ (cite: ven17b)" (5 Origin of the [C II] cavities) [from (cite: ven17b)]
- External data: Bolometric luminosity 7.5e46 erg/s  
  > "$L_\mathrm{bol}=7.5\times10^{46}$ erg s$^{-1}$ (cite: maz17b)" (5 Origin of the [C II] cavities) [from (cite: maz17b)]

## Processing

### Calibration

- pipeline or manual: CASA, standard reduction steps  
  > "The data were reduced using the Common Astronomy Software Application package (cite: mul07), following the standard reduction steps." (2 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 (bandpass and flux)  
  > "Bandpass and flux calibration was performed through observations of J0522–3627." (2 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The final beam using natural weighting has a size of 0.076$''$ $\times$ 0.071$''$" (2 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channels averaged to 30 MHz (36 km/s)  
  > "we have averaged the emission into channels with a width of 30 MHz (36 km s$^{-1}$; see Figure [3](#fig:channel))." (3.2 Gas Dynamics)
- final beam: 0.076" x 0.071"  
  > "0.076$''$ $\times$ 0.071$''$" (2 ALMA Observations)
- final rms: 87 uJy/beam per 30 MHz bin  
  > "87 $\mu$Jy beam$^{-1}$ per 30 MHz bin" (2 ALMA Observations)

### Inherited from earlier work

- Dust SED shape: T=47 K, beta=1.6, for L_FIR  
  > "we follow the literature and assume a dust temperature of 47 K and a dust emissivity index of $\beta=1.6$" (1 Introduction) [from (cite: bee06; wan08b; wan13; wil13; ven16)]

### Not stated but needed to reproduce (our reading)

- CASA version
- tclean parameters (cell, image size, masks, deconvolver, threshold)
- continuum subtraction method and line-free channels
- self-calibration
- flux scale uncertainty
- how moment maps were made (clipping)
- MCMC walkers, steps, burn-in, N pixels
- model cube construction details and jet model equations
- aperture and Gaussian fit procedures for companions
- [C II] rest frequency adopted

## Analysis recipe

1. **Image and measure fluxes**: CASA reduction, natural weighting; total flux in 0.75" radius aperture; Gaussian line fit for redshift and flux  
  > "We measured the total flux of the quasar host galaxy in an aperture with a radius of 0.75$''$." (3.1 Dust and [C II] emission)
   - software: CASA
   - assumption: L_FIR from dust SED with T=47 K, beta=1.6, 42.5-122.5 um  
  > "Far-infrared luminosities, $L_{\mathrm{FIR}}$, are computed by integrating the dust spectral energy distribution (SED) between the rest-frame wavelengths 42.5 and 122.5 $\mu$m" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Kinematic modelling of [C II] cube**: Four 3D models (Disk A, B, C, Rot+Jet D) convolved with the primary beam, fit to cube with chi-squared on bootstrapped pixels  
  > "we do not sum up all of the pixels in our data, but instead use a bootstrap method, whereby we randomly select $N$ pixels from the data cube and calculate the $\chi^2$ value of these pixels." (4 Kinematic Modeling)
   - software: emcee
   - parameter: Model velocities -216 to +216 km/s, excluding channels affected by close companion  
  > "The model cube has velocities that range from –216 to +216 km s$^{-1}$." (4 Kinematic Modeling)
   - fitting: emcee affine-invariant MCMC, flat priors, initial guesses from visual inspection  
  > "For all parameters, we assume flat priors, and we initiate the parameters with rough estimates from visual inspection of the data." (4 Kinematic Modeling)
   - validation: Verified initial guesses do not affect MCMC results  
  > "We have verified that these initial guesses do not affect the results of the MCMC analysis." (4 Kinematic Modeling)
3. **Energy required for cavities**: Chevalier (1974) expanding shell energy formula with d~0.5 kpc, n=1e5 cm^-3, v_exp~80 km/s; compare with SNe and AGN energy  
  > "Taken together, we derive a required energy of $\sim$$3\times10^{59}$ erg" (5 Origin of the [C II] cavities)
   - assumption: 5% of accreted energy deposited as thermal energy in ISM; 1 SN per 200 Msun of stars  
  > "Assuming that 5% of the accreted energy is deposited as thermal energy in the ISM (cite: dim05)" (5 Origin of the [C II] cavities)
   - fitting: _not stated_
   - validation: _not stated_
4. **Companion properties**: Gaussian fits to [C II] of companions; SFR from De Looze relation; H2 mass with alpha_[CII]=31  
  > "Molecular gas mass, derived from the \[C II\] luminosity using a $L_\mathrm{[CII]}$-to-H$_2$ conversion factor of $\alpha_\mathrm{[CII]} = 31$ $M_\ensuremath{\odot}$/$L_\ensuremath{\odot}$" (Table 2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction  
  > "The data were reduced using the Common Astronomy Software Application package (cite: mul07)" (2 ALMA Observations)
- **emcee** : MCMC sampling of kinematic model parameters  
  > "we have used the affine invariant MCMC ensemble sampler code, `emcee` (cite: for13)" (4 Kinematic Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total continuum flux density | 5.34 | 0.19 | mJy | 1 | The total continuum flux density is 5.34$\pm$0.19 mJy around the \[C II\] line |
| [C II] line flux | 5.43 | 0.33 | Jy km/s | 1 | The total brightness of the \[C II\] line is 5.43$\pm$0.33 Jy km s$^{-1}$ |
| L_[CII] | 5.90e9 | 0.36e9 | Lsun | 1 | $L_\mathrm{[CII]}$ = $(5.90\pm0.36)\times10^9$ $L_\ensuremath{\odot}$ |
| Systemic redshift z_[CII] | 6.61391 | 0.00015 | dimensionless | 1 | $z_\mathrm{[CII]}=6.61391\pm0.00015$ |
| Energy required for cavities | ~3e59 | not stated | erg | 3 | we derive a required energy of $\sim$$3\times10^{59}$ erg |
| Disk C inclination | 34.7 | +1.8/-1.7 | deg | 2 | $34.7^{+1.8}_{-1.7}$ |
| Companion C3 [C II] flux | 1.13 | 0.17 | Jy km/s | 4 | $1.13\pm0.17$ |

## Qualitative findings

- Gas is dispersion-dominated with little ordered rotation, not settled in a disk; two ~0.5 kpc [C II] cavities offset from the black hole; three [C II] companions.  
  > "The gas has a high velocity dispersion with little ordered motion along the line of sight" (abstract)

## Claim tuples

- H: Gas kinematics are consistent with a simple rotating disk | E: Fit four 3D models to the [C II] cube with MCMC | R: Constant-velocity disk inconsistent; truncated disk and others do not give adequate fits | F: Gas is dispersion-dominated and not yet settled in a disk | **supported**
- H: Cavities are produced by supernovae or by AGN energy | E: Compute required energy and compare with SN and AGN output | R: ~3e59 erg, equal to 300 million SNe, AGN needs ~2.5 Myr | F: Energy must originate from the AGN, without suppressing star formation | **partially**
- H: The quasar has companion galaxies | E: Search the deep cube for [C II] emitters | R: Three [C II] emitters at the quasar redshift | F: Interactions may have triggered star formation and AGN activity | **partially**

## Reasoning

- Why this data: Resolve the host structure and explore its kinematics, and probe black hole sphere of influence scales  
  > "To resolve the structure of the host galaxy and explore its detailed kinematics, we observed J0305–3150" (2 ALMA Observations)
- Why this method: _not stated_
- Alternative: Supernova-driven cavities rejected as they would need ~40 Myr of constant SFR in a restricted volume  
  > "would then require a constant star formation rate over $\sim$40 million years in a very restricted volume" (5 Origin of the [C II] cavities)
- How they decided it was enough: _not stated_
- Limitation (authors): Models are oversimplified, assuming a smooth decreasing intensity profile  
  > "This clearly is an oversimplification, as the moment 0 map shows obvious evidence of nonexponential emission" (4.1 Modeling Results)
- Caveat (inferred, ours): Simple parametric models do not fit; conclusions about cavity origin are qualitative
- Caveat (inferred, ours): Energy estimate relies on assumed density from another paper and an adopted v_exp
- Caveat (inferred, ours): Uncertainties on L_FIR ignore SED shape (factor 2-3)

## Reproducibility

- Data public (paper): ALMA project code given in acknowledgments; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01532.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: MCMC configuration and model equations
- Missing: aperture and fitting details for companions
- Data volume (inferred): ~100-300 GB raw (long-baseline, 4 spectral windows, 7.6 hr)
- Score (inferred): 3/5, Data identified, but imaging and modelling details are sparse.
- Rediscovery candidate: no, Imaging and modelling recipe is incomplete.

## Links

- Method: (cite: for13) (emcee sampler)
- Companion: (cite: ven16) (Previous lower-resolution ALMA observations of the same quasar)
- Companion: (cite: ven17b) (CO detections and ISM density)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 39,
  "rate": 0.565
 },
 "evidence_ok": true
}
```
