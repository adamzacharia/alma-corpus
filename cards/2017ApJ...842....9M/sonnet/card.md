# Detection of Exocometary CO within the 440 Myr Old Fomalhaut Belt: A Similar CO+CO<SUB>2</SUB> Ice Abundance in Exocomets and Solar System Comets

`2017ApJ...842....9M` | The Astrophysical Journal 2017 | first author: Matrà, L. | arXiv: 1705.05868 | DOI: 10.3847/1538-4357/aa71b4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, astrochemistry
- Question: Is there CO gas co-located with the Fomalhaut dust belt, is it exocometary, and what CO+CO2 ice mass fraction in exocomets does it imply?  
  > "We here present the detection of CO J=2-1 emission co-located with dust emission from the cometary belt in the 440 Myr-old Fomalhaut system." (abstract)
- Target **Fomalhaut**: coordinates _not stated_; z/distance 7.7 pc  
  > "Fomalhaut, at a distance of 7.7 pc, is the nearest circumstellar disk where CO has been searched for by ALMA to date." (3.3 Total flux and CO mass); "The nearby (cite: vanLeeuwen2007), 440$\pm$40 Myr-old (cite: Mamajek2012), A3V (cite: Gray1989) star Fomalhaut" (Introduction); distance from not stated (van Leeuwen 2007 cited for 'nearby')  
  > "Fomalhaut, at a distance of 7.7 pc, is the nearest circumstellar disk where CO has been searched for by ALMA to date." (3.3 Total flux and CO mass); "The nearby (cite: vanLeeuwen2007), 440$\pm$40 Myr-old (cite: Mamajek2012), A3V (cite: Gray1989) star Fomalhaut" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00966.S
- bands: Band 6 (1.3 mm continuum, CO J=2-1)  
  > "We observed the Fomalhaut belt with the ALMA array using Band 6 receivers" (Observations)
- frequencies and spectral setup: native spectral resolution 1.27 km/s around CO J=2-1 (230.538 GHz)  
  > "a native spectral resolution of 1.27 km/s around the rest frequency of the CO J=2-1 transition (230.538 GHz)" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.36''x2.13'' tapered (1.52''x1.12'' natural weights)  
  > "($2.36\ensuremath{''}\times2.13\ensuremath{''}$, as opposed to the $1.52\ensuremath{''}\times1.12\ensuremath{''}$ resolution achieved from natural visibility weights)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.7 mJy/beam per 1.3 km/s channel  
  > "Our final data cube has a root-mean-square (RMS) noise level of 0.7 mJy beam$^{-1}$ in a 1.3 km/s channel" (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- External data: Dust ring orbital parameters (semimajor axis 136.3 AU, width, eccentricity, pericentre, proper eccentricity 0.06) from 1.3 mm continuum fit  
  > "with the same orbital parameters as the dust ring, obtained from dust continuum imaging (cite: Macgregor2017)" (3.2 Spectral + spatial filter) [from (cite: Macgregor2017)]
- External data: CO J=3-2 3 sigma upper limit 18e-22 W m-2  
  > "the 3$\sigma$ upper limit of $18\times10^{-22}$ Wm$^{-2}$ on the J=3-2 line flux from (cite: Matra2015)" (3.4 Consistency with archival Band 7 observations) [from (cite: Matra2015)]
- External data: Stellar luminosity 16.6 Lsun and fractional luminosity 7.8e-5  
  > "a stellar luminosity of 16.6 L$_{\odot}$ and fractional luminosity of $7.8\times10^{-5}$ (cite: KennedyWyatt2014)" (B. mass loss rate) [from (cite: KennedyWyatt2014)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "The expected systematic flux calibration accuracy is of order $\sim10$% (cite: Fomalont2014)." (Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA, no deconvolution; dirty cube, primary-beam corrected  
  > "We do not apply any image deconvolution, but carry out our analysis (next Section) on the primary beam-corrected dirty CO data cube." (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: taper applied in CLEAN to match ring width  
  > "we apply a taper within `CLEAN` to achieve an imaging resolution that better matches the width of the ring" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA on combined visibilities  
  > "we carried out continuum subtraction on the combined visibility dataset using the `uvcontsub` task" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.7 mJy/beam in 1.3 km/s channel  
  > "RMS) noise level of 0.7 mJy beam$^{-1}$ in a 1.3 km/s channel" (Observations)

### Inherited from earlier work

- Observational setup, calibration, data reduction and continuum imaging  
  > "The observational setup, as well as the calibration, data reduction and continuum imaging process are described in detail in (cite: Macgregor2017)." (Observations) [from (cite: Macgregor2017)]
- Spectro-spatial filtering technique and NLTE CO excitation analysis  
  > "the spectro-spatial filtering technique first applied in (cite: Matra2015)" (Introduction) [from (cite: Matra2015)]
- Steady-state collisional cascade framework for ice fraction  
  > "in the framework described in (cite: Matra2015)" (4.3) [from (cite: Matra2015)]

### Not stated but needed to reproduce (our reading)

- Observing dates, array configurations, baselines, time on source
- Calibrators and CASA version
- Channel width/line-free channels used for uvcontsub, image size and cell size
- Exact filter implementation (pixel mask, sum weighting)
- Electron-density grid and collision-rate data for NLTE model
- Dust ring parameter values (PA, inclination, eccentricity) from Macgregor et al. 2017

## Analysis recipe

1. **Image CO cube**: Continuum subtraction, tapered dirty imaging, primary-beam correction  
  > "we carried out continuum subtraction on the combined visibility dataset using the `uvcontsub` task" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Dirty beam sidelobes below ~4%  
  > "never above the $\sim$4% level" (Observations)
2. **Spatial filter detection**: Integrate cube over region where continuum is >4 sigma (~40 beams)  
  > "spatially integrate the CO data cube over this region where the continuum is detected" (3.1)
   - fitting: _not stated_
   - validation: 3.3 sigma peak at stellar velocity  
  > "presents a 3.3$\sigma$ peak at a velocity consistent with the expected $v_{\star, \rm LSR}$" (3.1)
3. **Spectro-spatial filter and kinematics**: Shift spectra by Keplerian velocity field (1.92 Msun, dust ring orbit) for both rotation senses and sum  
  > "we shift the 1D spectrum at each $(x_{\rm sky}, y_{\rm sky})$ pixel location by $-v_z (x_{\rm sky}, y_{\rm sky})$" (3.2)
   - assumption: vertically flat Keplerian disk with dust-ring orbital parameters  
  > "CO gas lies in a vertically flat disk in Keplerian rotation around a star of 1.92 $M_{\odot}$" (3.2)
   - fitting: _not stated_
   - validation: SNR maximised only for correct velocity field  
  > "the SNR of the CO line is maximised only for the correct velocity field" (3.2)
4. **Line flux and CO mass**: Gaussian fit to filtered spectrum; NLTE excitation with electron colliders, Tk 10-1000 K; optical depth check  
  > "we use a non-local thermodynamic equilibrium (NLTE) molecular excitation analysis (cite: Matra2015) to derive constraints on the total CO mass" (3.3)
   - assumption: optically thin; electrons dominant colliders  
  > "We take the main colliders to be electrons" (3.3)
   - fitting: Gaussian fit  
  > "we fit a Gaussian to the spectro-spatially filtered spectrum derived above and shown in Fig. [1](#fig:spectra) (centre left)" (3.3 Total flux and CO mass)
   - validation: tau <~ 0.18  
  > "$\tau\lesssim 0.18$" (3.3)
5. **Radial and azimuthal morphology**: Spectral filter on full cube, semimajor-axis profile, 6 wedges, azimuthal profile fitted with cosine  
  > "We use Levenberg-Marquardt least-squares minimization to find the best-fit phase, mean intensity and pericentre to apocentre intensity enhancement" (3.5)
   - fitting: Levenberg-Marquardt least squares, cosine model  
  > "We use Levenberg-Marquardt least-squares minimization to find the best-fit phase, mean intensity and pericentre to apocentre intensity enhancement" (3.5 Radial and azimuthal morphology)
   - validation: _not stated_
6. **CO+CO2 ice mass fraction**: Steady-state collisional cascade: f = 1/(1+Mdot_Dmin/Mdot_CO)  
  > "In steady state, the outgassing rate of CO+CO$_2$ molecules equals their destruction rate" (4.3)
   - assumption: CO photodissociation timescale 120 yr  
  > "photodissociates the molecule on a timescale $t_{\rm phd}$ of 120 years" (4.1)
   - fitting: _not stated_
   - validation: Compared with beta Pic, HD181327 and Solar System comets  
  > "Fig. [6](#fig:comcomp) also shows that the CO+CO$_2$ mass fraction in exocomets is consistent with that of Solar System comets." (4.4 Comparison with other CO-bearing systems: an overall similarity to Solar System comets)
7. **Pericentre glow model**: Analytic mass-loss-rate vs true anomaly plus RADMC-3D sky-projected model  
  > "produce a sky-projected model image using the `RADMC-3D`[^1] radiative transfer code" (4.6)
   - software: RADMC-3D
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : uvcontsub and CLEAN imaging  
  > "using the `uvcontsub` task within the `CASA` software package" (Observations)
- **RADMC-3D** : sky-projected CO ring model  
  > "produce a sky-projected model image using the `RADMC-3D`[^1] radiative transfer code" (4.6)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectro-spatially filtered CO J=2-1 detection significance | 5.4 | not stated | sigma | 3 | this method boosts the SNR of the peak to $5.4\sigma$ |
| Integrated CO J=2-1 line flux | 68 | 16 | mJy km/s | 4 | The best-fit integrated line flux is $68\pm16$ mJy km/s |
| CO line centroid velocity | 6.1 | 0.2 | km/s | 4 | the best-fit velocity is $6.1\pm0.2$ km/s |
| CO mass | 0.65-42e-7 | ±1σ flux limits | Earth masses | 4 | The CO mass derived is in the range $0.65-42 \times10^{-7}$ M$_{\oplus}$ |
| CO+CO2 ice mass fraction | 4.6-76 | not stated | % | 6 | The CO+CO$_2$ ice mass fraction in Fomalhaut is therefore in the range 4.6-76% |
| Fraction of flux in S wedge | 49 | 27 | % | 5 | contributes to $(49\pm 27)$% of the flux integrated across all azimuths |
| Pericentre enhancement from cosine fit | 88 | 25 | % | 5 | pericentre enhancement with respect to apocentre of $(88\pm25)$% |
| Maximum optical depth | 0.18 | not stated | dimensionless | 4 | $\tau\lesssim 0.18$ |
| Mass loss rate of smallest grains | 1.1e-2 | not stated | Earth masses/Myr | 6 | mass loss rate of the smallest grains in the Fomalhaut belt of $1.1\times10^{-2}$ M$_{\oplus}$ Myr$^{-1}$ |

## Qualitative findings

- Ring sky-projected rotation axis matches the star's; SE ansa approaching, NW receding  
  > "CO gas in the NW ansa is moving away from us, while gas in the south-east (SE) ansa is coming towards us" (3.2)

## Claim tuples

- H: CO gas exists in the Fomalhaut belt | E: Spatial and spectro-spatial filtering of ALMA Band 6 cube | R: 5.4 sigma detection, 68±16 mJy km/s | F: First CO detection in Fomalhaut, co-located with dust, of exocometary origin | **supported**
- H: Exocomet CO+CO2 content resembles Solar System comets | E: Steady-state cascade model | R: 4.6-76% | F: Consistent with other belts and Solar System comets | **supported**
- H: CO is enhanced near pericentre | E: Wedge and azimuthal profiles | R: 49±27% of flux in S wedge; 88±25% enhancement | F: Tentative; exceeds steady-state prediction (14.5%) at 2.9 sigma | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Spatial and spectral filtering boosts SNR of faint emission  
  > "we obtain a spectrum which is free from noise originating from spectral channels as well as spatial locations where no CO emission is expected" (3.2)
- Alternative: Primordial CO rejected: column densities insufficient for shielding  
  > "we conclude that the observed CO cannot have survived since the protoplanetary phase" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Low SNR prevents distinguishing whether all emission is from S wedge; excitation model omits UV/IR pumping  
  > "given the low SNR levels, we cannot distinguish whether all of the emission originates from this wedge" (3.5)
- Caveat (inferred, ours): Dirty-image filtering with assumed ring geometry may bias significance
- Caveat (inferred, ours): Wedge asymmetry is post hoc, low SNR
- Caveat (inferred, ours): CO mass range spans over an order of magnitude
- Caveat (inferred, ours): Solar System comet comparison assumes dust/ice ratio of 4

## Reproducibility

- Data public (paper): Project code given; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00966.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration and setup details deferred to Macgregor et al. 2017
- Missing: Filter code not released
- Missing: Dust ring parameter values needed from companion paper
- Data volume (inferred): tens of GB (mosaic Band 6 visibilities)
- Score (inferred): 3/5, Data is archival with project code and clear filtering concept, but key geometry and calibration come from companion paper and code is not provided.
- Rediscovery candidate: no, Recipe depends on unstated parameters from Macgregor et al. 2017 and custom filtering code.

## Links

- Method: (cite: Matra2015) (Spectro-spatial filtering, NLTE excitation and steady-state ice model)
- Companion: (cite: Macgregor2017) (Observations, calibration and 1.3 mm dust continuum ring fit)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 78,
  "stated": 42,
  "rate": 0.538
 },
 "evidence_ok": true
}
```
