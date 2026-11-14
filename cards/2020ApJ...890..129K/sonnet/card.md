# Detection of Irregular, Submillimeter Opaque Structures in the Orion Molecular Clouds: Protostars within 10,000 yr of Formation?

`2020ApJ...890..129K` | The Astrophysical Journal 2020 | first author: Karnath, N. | arXiv: 2001.04997 | DOI: 10.3847/1538-4357/ab659e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do the extended, irregular, optically thick PBRs in Orion trace the earliest protostars (opaque regions preceding hydrostatic cores), and on what timescale are they collapsing?  
  > "A key question is whether these structures are evolving on free fall times of $\sim\,$100 years, or whether they are evolving on Kelvin-Helmholtz times of several thousand years." (abstract)
- Target **HOPS 400-A/B, 401, 402, 403, 404 (PACS Bright Red Sources in Orion B)**: coordinates e.g. HOPS 400-B 05:42:45.26 -01:16:14.14 (J2000); see Table 1  
  > "All of the PBRs presented here are found in Orion B and we adopt a common distance of 400 pc for all the protostars in this study (cite: kounkel2018)." (1 Introduction); z/distance 400 pc  
  > "All of the PBRs presented here are found in Orion B and we adopt a common distance of 400 pc for all the protostars in this study (cite: kounkel2018)." (1 Introduction); distance from Kounkel et al. 2018  
  > "All of the PBRs presented here are found in Orion B and we adopt a common distance of 400 pc for all the protostars in this study (cite: kounkel2018)." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00041.S
- bands: ALMA 0.87 mm (Band 7); VLA Ka-band 8.1 mm  
  > "The observations used the Ka-band receivers and the correlator was used in the wide bandwidth mode (3-bit samplers)" (2.2 VLA Observations and Reduction)
- frequencies and spectral setup: Basebands centered at 333 and 344 GHz (1.875 GHz each); 12CO 3-2 (937.5 MHz, 0.489 km/s channels); 13CO 3-2 (234.375 MHz, 0.128 km/s channels); total continuum bandwidth ~4.75 GHz  
  > "The total aggregate continuum bandwidth was $\sim$4.75 GHz." (2.1 ALMA 0.87 mm Observations and Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: VLA A-configuration  
  > "The observations with the VLA were conducted in the A-configuration" (2.2 VLA Observations and Reduction)
- baselines: 15.1 m to 3697 m (ALMA)  
  > "with baselines between 15.1 m to 3697 m" (2.1 ALMA 0.87 mm Observations and Reduction)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: ALMA continuum rms ~0.31 mJy/beam; 12CO 17.7 mJy/beam (1 km/s); 13CO 33.3 mJy/beam (0.44 km/s)  
  > "are $\sim$0.31 mJy beam$^{-1}$, 17.7 mJy beam$^{-1}$ (1 km s$^{-1}$ channels), and 33.3 mJy beam$^{-1}$ (0.44 km s$^{-1}$ channels), respectively." (2.1 ALMA 0.87 mm Observations and Reduction)
- time on source: ALMA ~0.9 min per target; VLA ~1 hr on-target  
  > "The total time spent on each target was $\sim$0.9 minutes." (2.1 ALMA 0.87 mm Observations and Reduction)
- observing dates: ALMA: 2016 Sep 4-5 and 2017 Jul 19; VLA: Oct 21, 23, 29, 31 and Dec 19, 2016  
  > "The Cycle 4 ALMA 0.87 mm observations were conducted on 2016 September 4 and 5, and 2017 July 19" (2.1 ALMA 0.87 mm Observations and Reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.79599 GHz)
- Line: 13CO J=3-2 (330.58797 GHz)
- Other facility **VLA**: 8.1 mm continuum imaging  
  > "one 4 GHz baseband centered at 36.9 GHz (8.1 mm)" (2.2 VLA Observations and Reduction)
- External data: Bolometric luminosities, Tbol and Ltot from SED fits  
  > "$^{c}$ Furlan et al. (2016)" (Table 2) [from (cite: furlan2016)]
- External data: Fiducial dust opacity kappa_8.1 = 0.144 cm2/g from 1.3 mm 0.899 cm2/g with beta=1  
  > "This value comes from the 1.3 mm opacity of 0.899 cm$^{2}$ g$^{-1}$ (cite: ossenkopf1994) extrapolated to 8.1 mm using a $\beta$=1 as the dust opacity spectral index." (3.3 Temperatures, Radii, and Masses) [from (cite: ossenkopf1994); (cite: segura2016; tychoniec2018)]
- External data: Protostellar lifetime of 0.5 Myr  
  > "For a protostellar lifetime of 0.5 Myr (cite: dunham2014)" (4.1 The Statistical Lifetime) [from (cite: dunham2014)]

## Processing

### Calibration

- pipeline or manual: ALMA manually reduced by Dutch Allegro ARC node; VLA scripted pipeline  
  > "The data were manually reduced and imaged using the Common Astronomy Software Application (cite: mcmullin2007) by the Dutch Allergro ARC Node." (2.1 ALMA 0.87 mm Observations and Reduction)
- casa version: ALMA self-cal/imaging CASA 4.7.2; VLA pipeline CASA 4.4.0, imaging CASA 4.5.1  
  > "We used CASA 4.7.2 for all self-calibration and imaging." (2.1 ALMA 0.87 mm Observations and Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% for ALMA and VLA  
  > "The absolute flux calibration accuracy is expected to be $\sim$10%" (2.1 ALMA 0.87 mm Observations and Reduction)
- self calibration: up to three rounds of phase-only self-calibration on continuum, applied to line data  
  > "up to three rounds of phase-only self-calibration were performed on the continuum data to increase the S/N." (2.1 ALMA 0.87 mm Observations and Reduction)

### Imaging

- task: VLA: clean, nterms=1 across both basebands, multi-frequency synthesis  
  > "using Natural weighting, multi-frequency synthesis with *nterms=1* across both basebands." (2.2 VLA Observations and Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (ALMA continuum); Natural for lines; VLA Natural  
  > "The continuum images were deconvolved using Briggs weighting with a robust parameter of 0.5" (2.1 ALMA 0.87 mm Observations and Reduction)
- uv taper: Lines: baselines >50 kλ with outer taper 500 kλ; continuum uses baselines >25 kλ  
  > "The continuum image also only uses uv-points at baselines $>$25 k$\lambda$ to mitigate striping" (2.1 ALMA 0.87 mm Observations and Reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using line-free regions of spectral windows  
  > "The continuum subtraction was done using line-free regions of the spectral windows to estimate the continuum level using the $uvcontsub$ task." (2.1 ALMA 0.87 mm Observations and Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ALMA continuum 0.11x0.10 arcsec; lines 0.25x0.24 arcsec; VLA 0.08x0.07 arcsec  
  > "The synthesized beams are 0.08$''$$\times$0.07$''$ (32 AU $\times$ 28 AU)." (2.2 VLA Observations and Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Gaussian-fit flux density measurements and fiducial dust opacity kept consistent with the VANDAM survey paper  
  > "For consistency with Tobin et al. (accepted), we use the Gaussian fitting results in our tables and analysis." (2.1 ALMA 0.87 mm Observations and Reduction) [from Tobin et al. (accepted)]
- Outflow mass via LTE method at 70 K  
  > "The outflow masses are calculated using the LTE approximation following the method in (cite: yildiz2015) and assume a gas temperature of 70 K." (3.5 Outflow Properties) [from (cite: yildiz2015)]
- Outflow force method  
  > "We calculate the outflow force F$_{CO}$ using the method in (cite: vandermarel2013) assuming an inclination of 50$^{\circ}$." (3.5 Outflow Properties) [from (cite: vandermarel2013)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum and uvcontsub
- Image size, cell size, cleaning threshold/masks and iterations
- Self-calibration solution intervals
- Flux/bandpass/phase calibrator names and VLA flux scale
- Exact outflow velocity ranges per lobe and the red/blue integration limits
- Method for the half-maximum contour area and beam subtraction details
- Details of binomial probability calculation
- Details of Gaussian fits (regions)

## Analysis recipe

1. **Image continuum and measure flux densities**: Gaussian fitting (also polygon) of ALMA 0.87 mm and VLA 8.1 mm images  
  > "The flux density of the objects and surrounding extended structure are measured both using Gaussian fitting and a measurement within a polygon region" (2.1 ALMA 0.87 mm Observations and Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Gaussian and polygon results agree within uncertainties  
  > "these yield measured flux densities that are within the uncertainty of one another." (2.1 ALMA 0.87 mm Observations and Reduction)
2. **Brightness temperature profiles and optical depth**: Cuts along RA of Tb at 0.87 and 8 mm in Rayleigh-Jeans limit; Tb ratio compared to optically thick threshold for beta 1-1.8  
  > "When the ratio of the 8 mm to 0.87 mm brightness temperature exceeds 0.16 assuming $\beta=1$ (or exceeds 0.03 with $\beta=1.8$), the 0.87 mm emission is becoming optically thick" (3.2 Brightness Temperature Profiles)
   - assumption: Rayleigh-Jeans limit, constant dust temperature, beta 1-1.8  
  > "Given a constant dust temperature, the ratio of the brightness temperatures is given by the equation" (3.2 Brightness Temperature Profiles)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive dust temperature, radius and mass**: Td from mean 0.87 mm Tb within half-max contour; r_decon from sqrt(A/pi) minus beam in quadrature; mass from optically thin 8 mm flux, M=F d^2/(kappa B(Td)) times 100  
  > "we use the average 0.87 mm brightness temperature for pixels within the half maximum of the 0.87 mm emission and assume the 0.87 mm emission is optically thick everywhere within this contour." (3.3 Temperatures, Radii, and Masses)
   - parameter: kappa_8.1 = 0.144 cm2/g  
  > "we adopt $\kappa_{8.1}$ = 0.144 cm$^{2}$ g$^{-1}$" (3.3 Temperatures, Radii, and Masses)
   - assumption: 8 mm optically thin, negligible free-free, gas-to-dust 100:1, distance 400 pc  
  > "An additional assumption is that the 8 mm emission traces the dust, with a negligible free-free contribution." (3.3 Temperatures, Radii, and Masses)
   - fitting: _not stated_
   - validation: Range of opacity laws tested (Table 3); mass uncertainty over an order of magnitude  
  > "We conclude that the uncertainty in mass from the dust law is over one order of magnitude." (3.3 Temperatures, Radii, and Masses)
4. **Luminosities and timescales**: Lop=4 pi sigma r^2 Td^4; free-fall time; Kelvin-Helmholtz time t_KH=(3/5)GM^2/(LR)  
  > "where we assume $\alpha = 3/5$ for a constant density sphere." (3.4 Luminosities and Timescales)
   - assumption: spherical constant-density geometry  
  > "assuming a spherical geometry with a constant radius at all wavelengths" (3.4 Luminosities and Timescales)
   - fitting: _not stated_
   - validation: _not stated_
5. **Outflow properties from 12CO**: LTE outflow masses at 70 K, force and dynamical times assuming 50 deg inclination  
  > "The resulting dynamical times assume a 50$^{\circ}$ inclination" (3.5 Outflow Properties)
   - assumption: Tgas 70 K, inclination 50 deg  
  > "assume a gas temperature of 70 K" (3.5 Outflow Properties)
   - fitting: _not stated_
   - validation: Compared to CARMA outflows from Tobin et al. 2016  
  > "The masses of the outflow lobes in HOPS 400-A and 403 are within an order of magnitude of (cite: tobin2016)." (3.5 Outflow Properties)
6. **Statistical lifetime**: t_stat = 4/328 x 0.5 Myr; binomial probability versus lifetime  
  > "the duration is t$_{stat} = 4/328~ \times 0.5~{\rm Myr} \approx 6000$ yrs" (4.1 The Statistical Lifetime)
   - assumption: Constant star formation rate; stage common to all protostars  
  > "ii.) that the star formation rate is constant over a protostellar lifetime" (4.1 The Statistical Lifetime)
   - fitting: _not stated_
   - validation: _not stated_
7. **Virial/support analysis**: Compare thermal, turbulent, magnetic and rotational support using virial theorem for constant density spheres  
  > "The zones are in virial equilibrium when $2T = U$." (4.2 Inside the Opacity Horizon)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2 (ALMA); 4.4.0 pipeline and 4.5.1 clean (VLA): Calibration, self-calibration, imaging, uvcontsub  
  > "We used CASA 4.7.2 for all self-calibration and imaging." (2.1 ALMA 0.87 mm Observations and Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deconvolved radii | 29 to 84 | not stated | AU | 3 | The deconvolved radii range from 29 to 84 AU (Table [2](#tbl:pbrsproperties)). |
| Dust temperatures | 33 to 95 | not stated | K | 3 | The resulting dust temperatures, given in Table [2](#tbl:pbrsproperties), range from 33 to 95 K. |
| HOPS 403 mass (kappa=0.144) | 1.20 | not stated | Msun | 3 | / 403 / 41 / 1.20 / 84.1 / |
| KH times using Lop | 250-3600 | not stated | yr | 4 | Adopting L$_{op}$ results in times ranging from 250-3600 years. |
| Statistical lifetime | 6000 | not stated | yr | 6 | $\approx 6000$ yrs |
| Turbulent velocity required for HOPS 402 | ~1.3 | not stated | km/s | 7 | we estimate that turbulent velocities of $\sim$1.3 km s$^{-1}$ are required |
| HOPS 400-B 8 mm flux density | 2.598 | 0.088 | mJy | 1 | / 400-B / irregular / 05:42:45.26 / -01:16:14.14 / 2.598$\pm$0.088 / |

## Qualitative findings

- Four irregular PBRs are optically thick at 0.87 mm over ~100 AU with internal heating  
  > "We have resolved four irregular protostars that are optically thick at 0.87 mm over $\sim$100 AU diameter regions" (4 Discussion)

## Claim tuples

- H: Irregular PBRs are optically thick, internally heated opaque regions | E: Brightness temperature profiles at 0.87 and 8 mm | R: Tb ratio exceeds 0.16 over much of emission; Td 33-95 K above typical cloud | F: Internal heating and optically thick 0.87 mm emission | **supported**
- H: Collapse proceeds on free fall vs Kelvin-Helmholtz timescale | E: Compare t_ff, t_KH and t_stat | R: t_ff<150 yr, t_KH 250-3600 yr, t_stat~6000 yr | F: Closer to KH time; internal support needed | **partially**
- H: Outflows trace hydrostatic cores | E: 12CO outflow velocities and implied central temperature | R: HOPS 404 ~2 km/s implies ~140 K | F: HOPS 404 outflow may be driven by a FHSC | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Free fall, turbulence, magnetic and rotational support scenarios considered; stable Keplerian disks judged very unlikely  
  > "it is very unlikely that the irregular protostars are stable Keplerian disks surrounding protostars" (4.2.4 Rotational Support and Disks)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass uncertainty from dust opacity exceeds one order of magnitude  
  > "We conclude that the uncertainty in mass from the dust law is over one order of magnitude." (3.3 Temperatures, Radii, and Masses)
- Caveat (inferred, ours): Small sample of four sources; statistical lifetime sensitive to assumptions
- Caveat (inferred, ours): Optically thick 0.87 mm Td may not represent mass-averaged temperature
- Caveat (inferred, ours): 8 mm may not be optically thin or free-free free
- Caveat (inferred, ours): ALMA snapshots with short integrations limit outflow recovery

## Reproducibility

- Data public (paper): ALMA project 2015.1.00041.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2015.1.00041.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks)
- Missing: Gaussian fit regions
- Missing: VLA project code
- Missing: Outflow velocity integration limits
- Data volume (inferred): ~50-100 GB for ALMA raw plus VLA data
- Score (inferred): 3/5, Recipe is simple and numeric but several imaging and measurement details are missing, and VLA data code not given.
- Rediscovery candidate: no, Key derived values need Gaussian and half-max measurements with unspecified details, and VLA data are not identified.

## Links

- Method: Tobin et al. (accepted) (VANDAM Orion survey data reduction and fiducial opacity)
- Companion: (cite: stutz2013) (Identified PBR sample)
- Companion: (cite: furlan2016) (HOPS SEDs and luminosities)
- Related: VANDAM Orion
- Related: Herschel Orion Protostar Survey (HOPS)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 81,
  "stated": 48,
  "rate": 0.593
 },
 "evidence_ok": true
}
```
