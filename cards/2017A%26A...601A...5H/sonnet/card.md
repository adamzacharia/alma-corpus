# ALMA observations of the nearby AGB star L<SUB>2</SUB> Puppis. II. Gas disk properties derived from <SUP>12</SUP>CO and <SUP>13</SUP>CO J = 3-2 emission

`2017A&A...601A...5H` | Astronomy and Astrophysics 2017 | first author: Homan, Ward | arXiv: 1803.05222 | DOI: 10.1051/0004-6361/201630340

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the physical conditions (temperature, density, velocity, abundance) of the gas disk around L2 Pup, and does its angular momentum require a binary companion?  
  > "we model the optically thick $^{\rm 12}$CO $J=$3$-$2 and the optically thin $^{\rm 13}$CO $J=$3$-$2 rotational transition to constrain the physical conditions in the disk." (abstract)
- Target **L2 Puppis**: coordinates RA 07:13:32.475914 DEC –44:38:17.91396 (ICRS)  
  > "ICRS position RA 07:13:32.475914 DEC –44:38:17.91396" (2 ALMA data description); "At a distance of only 64 pc ($\pi = 15.61 \pm 0.99$ mas; (cite: VanLeeuwen2007))" (1 Introduction); z/distance 64 pc  
  > "ICRS position RA 07:13:32.475914 DEC –44:38:17.91396" (2 ALMA data description); "At a distance of only 64 pc ($\pi = 15.61 \pm 0.99$ mas; (cite: VanLeeuwen2007))" (1 Introduction); distance from parallax, van Leeuwen 2007  
  > "ICRS position RA 07:13:32.475914 DEC –44:38:17.91396" (2 ALMA data description); "At a distance of only 64 pc ($\pi = 15.61 \pm 0.99$ mas; (cite: VanLeeuwen2007))" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00141.S
- bands: Band 7  
  > "In November 2015, we obtained spatially resolved ALMA band 7 observations of the CSE of L$_{\rm 2}$ Pup" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: most extended, 16-km configuration  
  > "using the most extended, 16-km configuration" (1 Introduction)
- baselines: 0.09 to 16 km  
  > "providing baselines from 0.09 to 16 km" (2 ALMA data description)
- angular resolution: 15 x 18 mas  
  > "with a resolution of $15 \times 18 \rm\ mas$" (abstract)
- max recoverable scale: ~250 mas reliable; ~450 mas maximum recoverable scale  
  > "the maximum recoverable scale of the configuration is $\sim$450 mas" (2.1 12CO emission)
- sensitivity: rms 2.5 (12CO) and 2.6 (13CO) mJy/beam; 0.22 km/s resolution  
  > "a rms noise (off-source) of 2.5 and 2.6 mJy beam$^{\rm -1}$, respectively" (2 ALMA data description)
- time on source: 7953 sec on-source  
  > "Integration time & 7953 sec on-source" (Table casa)
- observing dates: 2015 Nov 5  
  > "observed on 2015 Nov 5 by ALMA" (2 ALMA data description)
- pi or archival as stated: PI Kervella  
  > "project code 2015.1.00141.S (PI Kervella)" (2 ALMA data description)
- Line: 12CO J=3-2 (345.765 GHz)
- Line: 13CO J=3-2 (330.587 GHz)
- Other facility **JCMT**: 12CO J=3-2 single-dish detection from literature, peak ~59 Jy  
  > "detected $^{\rm 12}$CO J$=$3$-$2 with the JCMT (beam size 13"), with a peak of $\approx59$ Jy" (2.1 12CO emission)
- External data: Central mass 0.659 ± 0.052 Msun and Keplerian/sub-Keplerian velocity field (r^-0.85 beyond 6 AU)  
  > "resulting in a very accurate determination of the central mass of the system (0.659 $\pm$ 0.052 $\,{\rm M}_\odot$)" (2.1 12CO emission) [from (cite: Kervella2016)]
- External data: Dust composition and dust disk inner rim at 6 AU  
  > "The dust composition has been adopted from (cite: Kervella2015)" (3.1 LIME) [from (cite: Kervella2015)]
- External data: CO collisional rates  
  > "the collisional rates were taken from (cite: Yang2010)" (3.1 LIME) [from (cite: Yang2010)]
- External data: CO spectroscopic data from LAMDA  
  > "The spectroscopic CO data of the LAMDA database (cite: Schoier2005) were used" (3.1 LIME) [from (cite: Schoier2005)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA procedures, phase-referencing  
  > "Standard ALMA observing and data reduction procedures were used, including phase-referencing." (2 ALMA data description)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~7%  
  > "The flux scale is accurate to about 7%" (2 ALMA data description)
- self calibration: Line-free continuum channels used to self-calibrate, applied to all target data  
  > "The line-free continuum channels of L$_{\rm 2}$ Pup were used to self-calibrate the continuum and the solutions applied to all target data" (2 ALMA data description)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 2.5 mas  
  > "A 2.5 mas pixel size and an image size of $2.56\ensuremath{''}$ was used." (2 ALMA data description)
- image size: 2.56 arcsec  
  > "A 2.5 mas pixel size and an image size of $2.56\ensuremath{''}$ was used." (2 ALMA data description)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted after self-calibration  
  > "and then the continuum was subtracted." (2 ALMA data description)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.020" x 0.015"  
  > "The synthesised beam size is $\sim (0.020\ensuremath{''} \times 0.015\ensuremath{''})$" (2 ALMA data description)
- final rms: 2.5 mJy/beam (12CO), 2.6 (13CO)  
  > "a rms noise (off-source) of 2.5 and 2.6 mJy beam$^{\rm -1}$, respectively" (2 ALMA data description)

### Inherited from earlier work

- ALMA observing set-up and continuum residual discussion  
  > "For an extensive description of the ALMA observing set-up as well as an in-depth discussion of the continuum residuals see (cite: Kervella2016)." (2 ALMA data description) [from (cite: Kervella2016)]
- Velocity field regimes (Keplerian inside 6 AU, r^-0.85 outside) and central mass  
  > "Following these findings, we separated our velocity model into two regimes, the inner disk ($r < 6\rm AU$), and the outer disk ($r > 6\rm AU$)." (4.1 Dominant and turbulent velocity field) [from (cite: Kervella2016)]

### Not stated but needed to reproduce (our reading)

- tclean/imaging parameters (weighting, robust, deconvolver) used for the cubes
- Line-free channels and self-calibration solution intervals
- LIME and CASA versions and simulation task settings (simobserve parameters)
- Exact LIME model input files and convergence settings
- Procedure for computing disk mass and angular momentum (integration limits)
- Which spectral setup/cubes were taken from Paper I processing

## Analysis recipe

1. **Characterise observed emission**: Channel maps, integrated-intensity maps, PVDs with narrow and wide slits; max velocity from tails at 2x rms  
  > "we constructed 11 PVDs with a vertical separation of 10 mas. We extracted the maximal velocity at each offset by measuring the length of the tails of each PVD" (2.1 12CO emission)
   - fitting: _not stated_
   - validation: _not stated_
2. **Forward-model with 3D NLTE RT**: Parametric disk model (velocity, density, temperature, abundance) run through LIME, then CASA simulated ALMA observation with same antenna positions  
  > "We perform 3D radiative transfer via the `LIME` code. The result of the radiative transfer calculations are subsequently subjected to the simulation observation algorithms of `CASA`" (3 Computational methods)
   - software: LIME, CASA
   - parameter: 10^5 grid points plus 10^4 boundary points; inclination 82 deg  
  > "The model is sampled by $10^5$ grid points" (3.1 LIME); "at an inclination of 82 degrees" (5 Radiative transfer results)
   - assumption: Gas-to-dust 100; stellar blackbody 3500 K, 2500 Lsun; 12CO/H2 = 1e-4  
  > "a gas-to-dust mass ratio of 100" (3.1 LIME); "We have thus chosen to set the $^{\rm 12}$CO/H$_{\rm 2}$ ratio to the constant value of $10^{-4}$ for this model" (4.4 12CO and 13CO molecular abundance)
   - fitting: Manual iterative adjustment to visual resemblance; no grid or statistical fit  
  > "we do not refer to a statistically significant result that follows from extensive and detailed post-processing, but rather to the set of parameters for which the simulated emission shows a good visual resemblance" (3.3 Modelling strategy)
   - validation: Compare model and data PVDs and channel maps  
  > "We shall thus focus the rest of the comparative discussion on the PVDs" (5 Radiative transfer results)
3. **Derive disk mass and angular momentum, companion mass**: Integrate density and velocity structure; assume solar-like stellar angular momentum and 30% transfer efficiency  
  > "By assuming the companion follows Keplerian rotation, and by assuming an angular momentum transfer efficiency of 30%" (6.4.1 Disk origin)
   - assumption: Main-sequence angular momentum ~ Sun's 1e41 m^2 kg/s  
  > "Recent work has shown the Sun to contain approximately $10^{41}\ {\rm m^2 kg/s}$ of angular momentum" (6.4.1 Disk origin)
   - fitting: _not stated_
   - validation: Sensitivity with ±25% parameter variation  
  > "Assuming each parameter would have its true physical value between plus and minus 25% of the determined value" (6.3.1 Disk mass)

## Software

- **LIME** : 3D NLTE radiative transfer  
  > "We used the full 3D, non-local thermodynamical equilibrium (NLTE), infrared (IR) and submillimeter radiative transfer (RT) code `LIME`" (3.1 LIME)
- **CASA** : Simulating ALMA observations of model  
  > "we post-processed it with `CASA` (cite: McMullin2007) to simulate an observation with ALMA" (3.2 CASA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Radial H2 density power-law slope p | -3.1 | not stated | dimensionless | 2 | the data is best modelled by simply assuming a radial power law drop characterised by $p=-3.1$ |
| 12CO/13CO abundance ratio | 10 | not stated | dimensionless | 2 | resulting in a $^{\rm 12}$CO over $^{\rm 13}$CO abundance of 10 |
| Disk mass | 2.2e-4 | 0.65e-4 to 9.7e-4 (±25% parameter range) | Msun | 3 | the mass of the disk is found to be approximately $2.2 \times 10^{-4} \,{\rm M}_\odot$ |
| Total disk angular momentum | 3.1e42 | not stated | m^2 kg/s | 3 | $$L_{\rm tot} = 3.1 \times 10^{42}\ {\rm m^2 kg/s}.$$ |
| Companion mass | ~1 | 0.25 to 5.5 | Jupiter mass | 3 | the mass of the companion could be expected to lie within the 0.25 to 5.5 Jupiter mass range |
| Inner rim radius | 2.0 | not stated | AU | 2 | the inner rim of the gas being located at approximately $r_{\rm c} = 2.0 \rm AU$ |
| Small-scale random motion sigma | 0.55 | not stated | km/s | 2 | corresponds to a SSRM standard deviation of $v_{\rm ssrm} = 0.55 \, {\rm km}\, {\rm s}^{-1}$ |

## Qualitative findings

- 12CO self-absorption near systemic velocity indicates cold, optically thick outer disk  
  > "This is probably due to self-absorption along the line of sight to the star by the outer regions of the disk" (2.1 12CO emission)

## Claim tuples

- H: Disk angular momentum exceeds what the star could supply | E: Integrate modelled density and velocity fields | R: L = 3.1e42 m^2 kg/s, ~30x solar-like stellar value | F: A ~1 Jupiter-mass compact companion is implied | **supported**
- H: Disk has a complex temperature structure | E: Model 12CO emission with LIME | R: Three-regime radial profile, ~500 K plateau beyond 6 AU, 2500 K inner walls vs 1000 K midplane | F: Dust plays a thermodynamical role | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Full parameter grid infeasible, so iterative manual fitting starting with 12CO then refining with 13CO  
  > "Such an analysis cannot simply be performed with present-day computational facilities." (3.3 Modelling strategy)
- How they decided it was enough: _not stated_
- Limitation (authors): No statistical errors; 12CO abundance assumed and degenerate with density; large-scale emission resolved out  
  > "we cannot quantify the quality of the model in terms of statistically significant errors" (6.1 Parameter sensitivity)
- Caveat (inferred, ours): Visual-only fits with no uncertainties
- Caveat (inferred, ours): Density scale tied to assumed CO abundance
- Caveat (inferred, ours): Angular momentum argument relies on solar analog assumption

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00141.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: LIME model input scripts
- Missing: Imaging parameters
- Missing: Cube products from Paper I
- Data volume (inferred): ~50-200 GB raw for one long-baseline Band 7 execution
- Score (inferred): 3/5, Model parameters tabulated, but fitting is manual and imaging/software details are missing.
- Rediscovery candidate: no, Results come from manual visual model tuning, so not mechanically reproducible.

## Links

- Method: Brinch & Hogerheijde 2010 (LIME code description)
- Companion: Kervella et al. 2016 (Paper I) (Observations, Keplerian analysis, companion detection)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 66,
  "stated": 43,
  "rate": 0.652
 },
 "evidence_ok": true
}
```
