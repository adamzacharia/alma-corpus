# The Planet Formation Potential around a 45 Myr Old Accreting M Dwarf

`2019ApJ...872...92F` | The Astrophysical Journal 2019 | first author: Flaherty, Kevin | arXiv: 1812.04124 | DOI: 10.3847/1538-4357/aaf794

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, protoplanetary_disks
- Question: Is the 45 Myr old accreting M dwarf W0808 hosting a gas-rich protoplanetary disk or a debris disk, and what is the origin of its cold dust?  
  > "To better understand the cold gas and dust properties of this system, we obtained ALMA observations of the 1.3mm continuum and the CO/$^{13}$CO/C$^{18}$O J=2-1 emission lines." (abstract)
- Target **W0808 (WISEJ080822.18-644357.3)**: coordinates 08:08:22.178 -64:43:57.20 (epoch of observations, GAIA DR2 predicted)  
  > "The phase center is shifted to match the stellar position at the epoch of the observations (08:08:22.178 -64:43:57.20) as predicted by GAIA DR2 data" (2 Data); "distance                 |        101.4$\pm$0.6$^{a}$ pc" (Table 1); z/distance 101.4±0.6 pc  
  > "The phase center is shifted to match the stellar position at the epoch of the observations (08:08:22.178 -64:43:57.20) as predicted by GAIA DR2 data" (2 Data); "distance                 |        101.4$\pm$0.6$^{a}$ pc" (Table 1); distance from GAIA DR2  
  > "The phase center is shifted to match the stellar position at the epoch of the observations (08:08:22.178 -64:43:57.20) as predicted by GAIA DR2 data" (2 Data); "distance                 |        101.4$\pm$0.6$^{a}$ pc" (Table 1)

## Data provenance

- ALMA projects: 2017.1.01521.S
- bands: 1.3 mm (~232 GHz)  
  > "we obtained ALMA observations of the 1.3mm continuum" (abstract)
- frequencies and spectral setup: continuum window at 232 GHz (2 GHz bandwidth); three windows on CO, 13CO, C18O (2-1) with 480 channels of 244.141 kHz (0.38 km/s)  
  > "One spectral window was devoted to the continuum at 232 GHz, with a 2 GHz bandwidth" (2 Data); "with 480 channels of width 244.141 kHz (0.38 km s$^{-1}$)" (2 Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1.4 km, 45 antennas  
  > "W0808 was observed with 45 antennas with baselines ranging from 15m to 1.4km" (2 Data)
- angular resolution: 0.41"x0.32" (natural weighting continuum beam)  
  > "which results in a beam of $0.41\ensuremath{''}$x$0.32\ensuremath{''}$ and an rms of 23 $\mu$Jy/beam" (2 Data)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 23 uJy/beam; line rms 1.8 mJy/beam/channel  
  > "with an rms of 1.8 mJy/beam/channel" (2 Data)
- time on source: 41 min total integration  
  > "a total integration time of 41 min" (2 Data)
- observing dates: January 18, 2018  
  > "ALMA observations were taken on January 18, 2018 as part of project 2017.1.01521.S (PI: K. Flaherty)." (2 Data)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **Gaia DR2**: stellar position, parallax, proper motion  
  > "with updates to the stellar position, distance, luminosity, and proper motion based on the GAIA second data release" (2 Data)
- Other facility **ALLWISE**: IR emission position for comparison with ALMA  
  > "offset between the ALMA and ALLWISE (cite: cut13) emission positions" (4.3 Contamination from a background galaxy)
- External data: Stellar parameters (Teff, RV, mass, age, spectral type, etc.)  
  > "Stellar properties of W0808, drawn from (cite: mur18)." (Table 1) [from (cite: mur18)]
- External data: Dust opacity 2.3 g cm^-2 at 1.3mm  
  > "assuming an opacity of 2.3 g cm$^{-2}$ at 1.3mm (cite: bec90)" (3.1 Cold Dust Emission) [from (cite: bec90)]
- External data: Dust masses vs age of M dwarf protoplanetary and debris disks for comparison  
  > "Figure [3](#mass_age) shows dust mass, as derived from sub-mm emission, as a function of age for protoplanetary disks" (3.1 Cold Dust Emission) [from (cite: ric12; ric14; van16; liu04; mat15; hol17 etc.)]
- External data: CO photodissociation rates  
  > "we utilize the photodissociation rates of (cite: vis09)" (3.2 The lack of Gas Emission) [from (cite: vis09)]
- External data: FUV/J-band flux ratio 4e-5  
  > "we assume the ratio between the FUV and J-band flux densities is 4$\times$10$^{-5}$" (3.2 The lack of Gas Emission) [from (cite: sch18)]
- External data: Template SEDs of extragalactic sources  
  > "along with template SEDs for extragalactic sources (cite: kir15)" (4.3 Contamination from a background galaxy) [from (cite: kir15)]
- External data: Schechter function for background galaxy chance probability  
  > "based on the Schechter function of (cite: car15)" (4.3 Contamination from a background galaxy) [from (cite: car15)]

## Processing

### Calibration

- pipeline or manual: standard ALMA calibration script  
  > "The visibilities were calibrated using the standard ALMA calibration script" (2 Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, all four spectral windows used for continuum  
  > "we use all four bands to image the continuum, with the CASA `clean` task using natural weighting" (2 Data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with the CASA `clean` task using natural weighting" (2 Data)
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
- final beam: 0.41"x0.32"  
  > "which results in a beam of $0.41\ensuremath{''}$x$0.32\ensuremath{''}$" (2 Data)
- final rms: 23 uJy/beam continuum  
  > "an rms of 23 $\mu$Jy/beam" (2 Data)

### Inherited from earlier work

- Stellar parameters taken from earlier work  
  > "Stellar parameters for W0808 (Table [1](#stellar_properties)) are taken from (cite: mur18)" (2 Data) [from (cite: mur18)]
- Dust mass opacity prescription  
  > "assuming an opacity of 2.3 g cm$^{-2}$ at 1.3mm (cite: bec90)" (3.1 Cold Dust Emission) [from (cite: bec90)]
- Dust dynamics (blowout, PR/wind drag) following prescriptions  
  > "Based on the prescriptions of (cite: str06) we can estimate the role of radiation/wind pressure and Poynting-Robertson drag" (4.1 Planetesimal Collisions) [from (cite: str06)]

### Not stated but needed to reproduce (our reading)

- CASA version used for calibration and imaging
- Clean threshold, masking, cell size and image size
- Spectral channel binning/velocity range used for line cubes
- Exact model and software for the point source visibility fit
- Details of the CO LTE mass calculation (molecular data, partition function)
- Dust temperature/opacity details such as frequency scaling for kappa
- Details of the photodissociation calculation (Draine field scaling, self-shielding setup)
- Details of the stellar wind drag calculation parameters

## Analysis recipe

1. **calibrate visibilities and shift phase center**: Standard ALMA calibration script; phase center shifted to Gaia DR2 predicted stellar position  
  > "The visibilities were calibrated using the standard ALMA calibration script" (2 Data)
   - software: CASA
   - parameter: J0635-7516 gain and bandpass; J0904-5735 phase  
  > "with J0635-7516 used for gain and bandpass calibration and J0904-5735 used for phase calibration" (2 Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **image continuum and measure flux**: CASA clean with natural weighting on all four spectral windows; point-source fit to visibilities for total flux  
  > "a point source fit to the visibilities derives a total flux of 198$\pm$15 $\mu$Jy" (2 Data)
   - software: CASA
   - fitting: point source fit to visibilities  
  > "a point source fit to the visibilities derives a total flux of 198$\pm$15 $\mu$Jy" (2 Data)
   - validation: checked amplitude time series for stellar flare  
  > "we find no evidence for a strong stellar flare in the amplitude time series" (2 Data)
3. **derive dust mass**: Optically thin dust mass M_d = F d^2 /(kappa B(T))  
  > "Assuming that the dust emission is optically thin we can estimate the dust mass" (3.1 Cold Dust Emission)
   - parameter: T_dust = 20 K; opacity 2.3 g cm^-2 at 1.3mm  
  > "assuming an opacity of 2.3 g cm$^{-2}$ at 1.3mm (cite: bec90), and a dust temperature of 20 K" (3.1 Cold Dust Emission)
   - assumption: Optically thin emission; disk radius <16 au implied by unresolved emission at 101 pc; blackbody grains at 16 au have 20 K  
  > "Blackbody grains 16 au from W0808 have a temperature of $T_{\rm dust}$= 20 K" (3.1 Cold Dust Emission)
   - fitting: _not stated_
   - validation: discussed uncertainty: smaller disk implies hotter dust and smaller mass; optically thick would make it a lower limit  
  > "If the dust emission is compact enough to be optically thick then our estimate is a lower limit on the total dust mass." (3.1 Cold Dust Emission)
4. **CO flux and mass upper limits**: 3sigma flux limit assuming uniform ring to 16 au at 45 deg inclination (~1 beam, ~10 channels); LTE mass at 20 K  
  > "we derive a 3$\sigma$ upper limit on the CO(2-1) flux of $<$10 mJy km s$^{-1}$" (3.2 The lack of Gas Emission)
   - parameter: Tex = 20 K; also 1071 K and 237 K  
  > "with an excitation temperature of 20 K, the flux limit corresponds to an upper limit on the cold CO gas mass" (3.2 The lack of Gas Emission)
   - assumption: LTE; NLTE would likely raise the limit  
  > "We caution that full NLTE calculations are needed to accurately constrain the CO mass" (3.2 The lack of Gas Emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **CO photodissociation timescale**: Photodissociation rates of Visser et al. with stellar FUV plus Draine interstellar field, with and without self-shielding  
  > "we utilize the photodissociation rates of (cite: vis09)" (3.2 The lack of Gas Emission)
   - parameter: FUV/J flux density ratio 4e-5; 5e-6 Mearth CO over 30 au diameter for self-shielding  
  > "spread evenly over a region with a diameter of 30 au" (3.2 The lack of Gas Emission)
   - fitting: _not stated_
   - validation: _not stated_
6. **assess origin of dust: PR drag, collisions, background galaxy**: Strubbe & Chiang prescriptions for wind drag; SED comparison with z=2 template; Schechter function chance-coincidence probability  
  > "there is a 0.01% chance of detecting a background galaxy at 8$\sigma$ within 0$\ensuremath{''}$5 of the stellar position" (4.3 Contamination from a background galaxy)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging (clean) and calibration  
  > "astropy (cite: astropy), CASA (cite: mcm07)" (Software)
- **astropy** : not stated beyond listing  
  > "astropy (cite: astropy), CASA (cite: mcm07)" (Software)
- **BANYAN Sigma** : moving group membership probability  
  > "the BANYAN $\Sigma$ tool (cite: gag18) returns a 95% probability of membership" (2 Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm continuum total flux (point source fit) | 198 | 15 | uJy | 2 | a point source fit to the visibilities derives a total flux of 198$\pm$15 $\mu$Jy |
| Continuum peak flux | 194 | rms 23 uJy/beam | uJy/beam | 2 | The continuum emission is significantly detected with a peak flux of 194 $\mu$Jy/beam |
| Dust mass | 0.057 | 0.006 | Earth masses | 3 | We derive a dust mass of 0.057$\pm$0.006 M$_{\oplus}$ |
| Disk radius upper limit | <16 | not stated | au | 3 | The emission is unresolved, which implies a disk radius $<$16 au at 101 pc. |
| CO(2-1) flux 3sigma upper limit | <10 | not stated | mJy km/s | 4 | we derive a 3$\sigma$ upper limit on the CO(2-1) flux of $<$10 mJy km s$^{-1}$ |
| Cold CO gas mass upper limit (LTE, 20 K) | <5e-6 | not stated | Earth masses | 4 | upper limit on the cold CO gas mass of $<$5$\times10^{-6}$ M$_{\oplus}$ |
| CO photodissociation timescale close to star (<10 au), no self-shielding | ~12 | not stated | years | 5 | destroying CO molecules within $\sim$12 years |
| CO photodissociation timescale with self-shielding, 10-20 au | 150-350 | not stated | years | 5 | the photo-dissociation timescale increases to 150-350 years between 10 and 20 au |
| Chance probability of background galaxy at 8sigma within 0.5" | 0.01 | not stated | percent | 6 | there is a 0.01% chance of detecting a background galaxy at 8$\sigma$ within 0$\ensuremath{''}$5 of the stellar position |

## Qualitative findings

- No CO, 13CO or C18O emission detected, ruling out a gas-rich protoplanetary disk  
  > "No cold CO gas is detected from this system, ruling out a gas-rich protoplanetary disk." (abstract)
- PR drag could move grains from the outer disk inward to supply the IR excess  
  > "dust grains released in the outer disk can migrate inwards via PR drag, potentially serving as a source of grains for the strong infrared excess." (abstract)

## Claim tuples

- H: W0808 hosts a gas-rich protoplanetary disk | E: ALMA CO/13CO/C18O 2-1 search | R: No line emission; 3sigma CO flux <10 mJy km/s, CO mass <5e-6 Mearth | F: No gas-rich protoplanetary disk; more like debris disk | **supported**
- H: Cold dust is present and is debris-like | E: 1.3 mm continuum imaging and optically thin mass | R: 198±15 uJy unresolved, 0.057±0.006 Mearth, radius <16 au | F: Weak sub-mm flux consistent with collisional-cascade debris disk | **supported**
- H: ALMA emission arises from a background galaxy | E: SED comparison with z=2 templates, position offset, Schechter probability | R: IR 2-3 orders brighter than template; 0.01% chance | F: Emission most likely from dust around W0808 | **supported**
- H: Outer-disk dust can feed the IR excess via PR/wind drag | E: Analytic drag estimates following Strubbe & Chiang | R: Wind ≳ solar mass loss rate drags micron grains inward within age | F: Possible common origin, but requires wind constraints | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Background galaxy contamination rejected as unlikely  
  > "suggesting that the emission is not from a background galaxy" (4.3 Contamination from a background galaxy)
- Alternative: Recent planetary-body collision remains possible, with silica emission as a test  
  > "The presence of silica emission (cite: lis09)" (4.2 Planetary-body collisions)
- How they decided it was enough: _not stated_
- Limitation (authors): Unresolved emission makes the dust mass uncertain; higher resolution needed  
  > "additional observations at higher spatial resolution are needed to more accurately constrain the dust mass" (3.1 Cold Dust Emission)
- Limitation (authors): LTE CO limit may be too low; NLTE would raise it  
  > "which will likely result in a higher upper limit on the CO gas mass" (3.2 The lack of Gas Emission)
- Caveat (inferred, ours): Dust mass depends strongly on the assumed 20 K temperature and opacity
- Caveat (inferred, ours): 8 sigma detection of an unresolved source; background galaxy not fully excluded
- Caveat (inferred, ours): Stellar wind mass loss rate unconstrained
- Caveat (inferred, ours): Single short observation, no resolved structure

## Reproducibility

- Data public (paper): Project code given; data use acknowledged via ADS/JAO.ALMA  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01521.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: clean parameters (threshold, cell, image size)
- Missing: exact point-source fit procedure
- Missing: CO LTE mass calculation details
- Data volume (inferred): ~10-20 GB raw for a 41 min Band 6 execution
- Score (inferred): 4/5, Simple dataset and recipe with numeric results, but imaging parameters and CASA version unstated.
- Rediscovery candidate: yes, Single archival project, simple recipe, numeric flux and mass results.

## Links

- Method: (cite: str06) (dust dynamics prescriptions)
- Method: (cite: vis09) (CO photodissociation rates)
- Companion: (cite: mur18) (discovery of accretion, stellar parameters, SED with warm dust rings)
- Companion: (cite: sil16) (discovery of infrared excess)
- Related: Gaia DR2
- Related: ALLWISE

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 53,
  "rate": 0.602
 },
 "evidence_ok": true
}
```
