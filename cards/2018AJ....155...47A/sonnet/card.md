# Optical and Radio Observations of the T Tauri Binary KH 15D (V582 Mon): Stellar Properties, Disk Mass Limit, and Discovery of a CO Outflow

`2018AJ....155...47A` | The Astronomical Journal 2018 | first author: Aronow, Rachel A. | arXiv: 1711.11434 | DOI: 10.3847/1538-3881/aa9ed7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the stellar properties of the KH 15D binary now that Star B is fully visible, how massive is its circumbinary disk (from radio continuum), and is there a CO outflow associated with it?  
  > "Decades of photometry on the system now allow us to infer the effective temperature, radius, mass and age of each binary component." (abstract)
- Target **KH 15D (V582 Mon)**: coordinates 6:41:10.31 +9:28:33.2 (optical, SIMBAD); 6:41:10.34 +9:28:33.5 (IR)  
  > "The images are aligned using an average of the optical (6:41:10.31 +9:28:33.2; SIMBAD) and infrared (6:41:10.34 +9:28:33.5; CSI NGC2264) positions of KH 15D" (3.3.1 SMA Line Emission); "we adopt a distance of 800 $\pm$ 20 pc (the unweighted mean, omitting the discrepant (cite: Dzib2014) value)" (3.1 Optical Photometry and Stellar Characteristics); z/distance 800 ± 20 pc  
  > "The images are aligned using an average of the optical (6:41:10.31 +9:28:33.2; SIMBAD) and infrared (6:41:10.34 +9:28:33.5; CSI NGC2264) positions of KH 15D" (3.3.1 SMA Line Emission); "we adopt a distance of 800 $\pm$ 20 pc (the unweighted mean, omitting the discrepant (cite: Dzib2014) value)" (3.1 Optical Photometry and Stellar Characteristics); distance from unweighted mean of published NGC 2264 distances (Table 3)  
  > "The images are aligned using an average of the optical (6:41:10.31 +9:28:33.2; SIMBAD) and infrared (6:41:10.34 +9:28:33.5; CSI NGC2264) positions of KH 15D" (3.3.1 SMA Line Emission); "we adopt a distance of 800 $\pm$ 20 pc (the unweighted mean, omitting the discrepant (cite: Dzib2014) value)" (3.1 Optical Photometry and Stellar Characteristics)

## Data provenance

- ALMA projects: 2015.1.01527.S
- bands: Band 4 (137–153 GHz)  
  > "ALMA observations in Band 4 (1959–2188 $\mu$m; 137–153 GHz) did not reveal a source at the location of KH 15D." (3.2.2 ALMA Non-Detection)
- frequencies and spectral setup: 4 spws, 128 channels of 15.625 MHz each  
  > "Each spectral window contains 128 channels, each 15.625 MHz wide." (2.3 Radio Observations: ALMA)
- continuum bandwidth: 7.5 GHz usable  
  > "for a total usable continuum bandwidth of 7.5 GHz" (2.3 Radio Observations: ALMA)
- arrays: forty-six 12-m antennas  
  > "The object was observed for a total of 11.2 minutes using forty-six 12-m antennas." (2.3 Radio Observations: ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.4" x 1.8" synthesized beam (quoted as 1.5")  
  > "The size of the synthesized beam is $1.4\ensuremath{''} \times 1.8\ensuremath{''}$." (2.3 Radio Observations: ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 46 µJy (continuum)  
  > "The final cleaned ALMA Band 4 image has an rms noise of $\sigma=$ 46 $\mu$Jy" (3.2.2 ALMA Non-Detection)
- time on source: 11.2 minutes  
  > "The object was observed for a total of 11.2 minutes using forty-six 12-m antennas." (2.3 Radio Observations: ALMA)
- observing dates: ALMA 2016 January 16; SMA 2010 Oct 13 and 2011 Oct 25  
  > "Atacama Large Millimeter/submillimeter Array (ALMA) Band 4 observations of KH 15D were obtained on January 16, 2016" (2.3 Radio Observations: ALMA)
- pi or archival as stated: _not stated_
- Line: CO (SMA) J=3–2 (345.796 GHz)
- Other facility **SMA**: 870 µm continuum and CO J=3–2 maps revealing the outflow  
  > "The SMA data revealed a CO J=3–2 line source that is spatially coincident with the filamentary jet of shocked gas seen in the near-IR" (3.3 Radio Line Emission)
- Other facility **SMARTS/ANDICAM 1.3 m (CTIO)**: VRIJHK photometry 2015–2017  
  > "obtained with the ANDICAM instrument on the 1.3 m telescope at Cerro-Tololo Inter-American Observatory (CTIO), operated by the SMARTS consortium" (2.1 Optical and Near-IR CCD Data: SMARTS)
- External data: H2 narrow-band image of the jet, overlaid on CO  
  > "we overlap the image of the H$_2$ emission from (cite: Tokunaga2004) over the CO emission" (3.3.1 SMA Line Emission) [from (cite: Tokunaga2004)]
- External data: E(B-V)=0.075±0.003  
  > "The mean foreground reddening to the cluster is only E(B-V) = 0.075 $\pm$ 0.003, as recently derived by (cite: Turner2012)." (3.1 Optical Photometry and Stellar Characteristics) [from (cite: Turner2012)]
- External data: Teff and BC from V-I colour  
  > "The intrinsic V-I color was then used to estimate the effective temperature and bolometric correction, BC$_\mathrm{V}$, of each star following Table 6 of (cite: PM13)." (3.1 Optical Photometry and Stellar Characteristics) [from (cite: PM13)]
- External data: PARSEC isochrones for ages and masses  
  > "Also plotted are isochrones from (cite: Marigo2017)" (4.1 Stellar Characteristics) [from (cite: Marigo2017)]

## Processing

### Calibration

- pipeline or manual: ALMA Science Pipeline  
  > "The data were calibrated using the ALMA Science Pipeline." (2.3 Radio Observations: ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 20% (SMA)  
  > "the absolute flux scale was set using observations of Callisto and Uranus, with an estimated accuracy of 20%" (2.2 Radio Observations: SMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Deconvolution was carried out using the CLEAN algorithm and applying natural weighting." (2.3 Radio Observations: ALMA)
- uv taper: baselines <40 kλ excluded for continuum  
  > "coverage from the shortest baselines ($<$40 k$\lambda$) was excluded from the data set during this step" (2.3 Radio Observations: ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub for line channel maps  
  > "The continuum emission was subtracted using the CASA task `uvcontsub`" (2.3 Radio Observations: ALMA)
- line free channels: line channels identified from sharp peaks in channel vs amplitude plot and excised  
  > "The channels containing line emission were determined from sharp peaks in a plot of channel vs. amplitude." (2.3 Radio Observations: ALMA)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.4" x 1.8"  
  > "The size of the synthesized beam is $1.4\ensuremath{''} \times 1.8\ensuremath{''}$." (2.3 Radio Observations: ALMA)
- final rms: 46 µJy (from 220 µJy before excluding short baselines)  
  > "This technique reduced the rms noise of the image from 220 $\mu$Jy to 46 $\mu$Jy." (2.3 Radio Observations: ALMA)

### Inherited from earlier work

- SMARTS observing and reduction process  
  > "The observing and reduction process is identical to what has been used for many years and is described in more detail by (cite: WindemuthHerbst2014)." (2.1 Optical and Near-IR CCD Data: SMARTS) [from (cite: WindemuthHerbst2014)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- tclean parameters (cell, image size, mask, threshold, iterations)
- flux calibrator and other calibrators for ALMA
- exact line-free channel list
- SMA imaging parameters for CO outflow (integrated velocity range, noise, mask)
- how the outflow position angle and length were measured
- details of SED blackbody fit and isochrone fitting

## Analysis recipe

1. **ALMA Band 4 continuum image and upper limit**: Excise line channels, average with split, exclude baselines <40 kλ, CLEAN with natural weighting; 3σ upper limit on flux  
  > "all channels containing line emission were excised out from the calibrated visibilities and the remaining channels were then averaged together, using the CASA task `split`" (2.3 Radio Observations: ALMA)
   - software: CASA
   - parameter: 40 kλ cutoff chosen to minimize rms  
  > "The 40 k$\lambda$ value was chosen to minimize the rms noise in the continuum image" (2.3 Radio Observations: ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **disk mass upper limit**: Optically thin isothermal relation M_d = d^2 F_nu / (kappa_nu B_nu(T_c))  
  > "If we assume that the emission is from an isothermal and optically thin portion of the disk, we can estimate an upper limit for the total mass of the disk" (3.2.2 ALMA Non-Detection)
   - parameter: 3σ flux limit 0.14 mJy  
  > "We can therefore place a 3$\sigma$ upper limit on the 2 mm flux density of the disk at 0.14 mJy." (3.2.2 ALMA Non-Detection)
   - assumption: kappa = 3 (1 mm/λ) cm2/g; T_c = 25 K; d = 800 pc  
  > "The opacity was estimated to be $\kappa_\nu \approx$ 3 (1 mm$/\lambda)$ cm$^2$ g$^{-1}$." (3.2.2 ALMA Non-Detection); "A characteristic temperature of 25 K (cite: AndrewsWilliams) was chosen" (3.2.2 ALMA Non-Detection)
   - fitting: _not stated_
   - validation: _not stated_
3. **identify ALMA spectral features**: Splatalogue search, shift data with cvel to candidate rest frequencies, Gaussian fit to compare velocity with cloud velocity  
  > "The data were then shifted to the rest frequency of each of these candidate spectral features using the CASA task `cvel`, and a Gaussian was fit to the shifted profile" (3.3.2 ALMA Line Emission)
   - software: CASA, Splatalogue
   - fitting: Gaussian to line profile  
  > "a Gaussian was fit to the shifted profile in order to find the central velocity." (ALMA Line Emission)
   - validation: compared with cloud velocity of 10–21 km/s from SMA  
  > "This velocity was compared to the velocity of the cloud emission in the SMA channel maps (10–21 km/s)." (3.3.2 ALMA Line Emission)
4. **SMA CO outflow mapping**: miriad imaging of CO J=3-2 channel maps; overlay on H2 image  
  > "Continuum and spectral line imaging and CLEAN deconvolution were done in the `miriad` package." (2.2 Radio Observations: SMA)
   - software: MIR, miriad
   - fitting: _not stated_
   - validation: alignment with H2 jet and position angle of optical polarization  
  > "The position angle of the radio outflow also agrees precisely with the direction of polarization of the optical emission during the faint phase." (abstract)
5. **stellar properties from photometry**: Mean unocculted magnitudes, extinction correction, Teff and BC from intrinsic V-I (Pecaut & Mamajek), L and R, masses and ages from PARSEC isochrones  
  > "Stellar luminosities were calculated from the resulting bolometric magnitudes, and radii were determined from the effective temperatures and luminosities." (3.1 Optical Photometry and Stellar Characteristics)
   - assumption: d=800 pc, E(B-V)=0.075, R=3.1, solar metallicity  
  > "We have adopted a reddening value of E(B-V) = 0.075 and a standard extinction law from (cite: Cardelli1989), which has a ratio of total to selective extinction of R $=3.1$." (3.1 Optical Photometry and Stellar Characteristics)
   - fitting: blackbody SED fit as alternative  
  > "Alternatively, the effective temperatures can be estimated by fitting a blackbody curve to the full VRIJHK spectral energy distribution of each star." (Stellar Characteristics)
   - validation: compared with archival photographic I=13.57±0.03 and Winn 2006 model  
  > "(cite: Winn2006) determined the mean brightness of the combined starlight at this time to be I = $13.57\pm0.03$ mag, in excellent agreement with our result." (Optical Photometry and Stellar Characteristics)

## Software

- **CASA** : split, uvcontsub, cvel, CLEAN  
  > "using the CASA task `split`" (2.3 Radio Observations: ALMA)
- **MIR** : SMA calibration  
  > "All of the calibration was performed using the `MIR` software package." (2.2 Radio Observations: SMA)
- **miriad** : SMA imaging, CLEAN, uvfit  
  > "Continuum and spectral line imaging and CLEAN deconvolution were done in the `miriad` package." (2.2 Radio Observations: SMA)
- **Splatalogue** : line identification  
  > "we submitted a Splatalogue[^1] search querying all spectral lines" (3.3.2 ALMA Line Emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA Band 4 continuum rms | 46 | not stated | µJy | 1 | rms noise of $\sigma=$ 46 $\mu$Jy |
| 3σ 2 mm flux upper limit | 0.14 | not stated | mJy | 1 | We can therefore place a 3$\sigma$ upper limit on the 2 mm flux density of the disk at 0.14 mJy. |
| Disk mass upper limit | 0.0016 Msun (1.7 MJup) | not stated | Msun | 2 | resulting in an upper mass limit of 0.0016 $M_\odot$, corresponding to 1.7 Jupiter masses |
| SMA tentative flux 2010 | 5.1 | 1.9 | mJy | 4 | This yielded a tenatative detection of $5.1\pm1.9$ mJy |
| CO outflow position angle | 17.6 | 0.3 | degrees | 4 | find it to be 17.6 $\pm$ 0.3 degrees |
| CO outflow extent | 15 arcsec each side, ~24,000 AU total | not stated | arcsec | 4 | This CO outflow extends 15$\ensuremath{''}$ to both the north and the south |
| Star A / Star B radius | 1.41 / 1.52 | 0.05 / 0.16 | Rsun | 5 | Radius ($R_\odot$)     /  $1.41\pm0.05$  /     $1.52\pm0.16$ |
| Star A / Star B Teff | 3970 / 4140 | 40 / 155 | K | 5 | T$_\mathrm{eff}$ (K)   /   $3970\pm40$   /      $4140\pm155$ |
| System age | 2.5–5.0 (best 3.5) | not stated | Myr | 5 | The age of the system is likely between 2.5–5.0 Myr, with 3.5 Myr providing the best simultaneous fit to both stars. |

## Qualitative findings

- CO outflow coincides with the H2 jet and the KH 15D systemic velocity, but is offset ~1" from the star  
  > "There is, nonetheless, an intriguing small, but real, offset ($\sim 1 \ensuremath{''}$ or 800 AU) of the stellar image from the central line of the molecular emission" (3.3.1 SMA Line Emission)

## Claim tuples

- H: The circumbinary disk is detectable in mm continuum | E: ALMA Band 4 continuum imaging | R: No detection, rms 46 µJy | F: Disk mass < 1.7 MJup | **supported**
- H: A CO outflow is associated with KH 15D | E: SMA CO J=3-2 channel maps vs H2 jet, velocity, PA | R: Linear CO structure at 3–7 km/s, PA 17.6° | F: Outflow associated with KH 15D, nearly orthogonal to line of sight | **supported**
- H: Stellar parameters of both stars can be derived from photometry | E: V-I colour Teff, isochrone comparison | R: Coeval ~0.7 Msun stars, 2.5–5 Myr | F: Consistent with earlier studies | **supported**

## Reasoning

- Why this data: Radio continuum was designed to detect disk thermal emission  
  > "The main goal of the radio observations was to detect the inferred KH 15D accretion disk directly through its expected thermal continuum emission" (3.2 Radio Continuum Results)
- Why this method: _not stated_
- Alternative: Teff from spectral type and blackbody SED fit rejected in favour of V-I colour  
  > "we prefer to use the intrinsic color as our primary guide to effective temperatures" (4.1 Stellar Characteristics)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass limit depends on opacity and temperature; only particles smaller than wavelength detectable  
  > "This mass estimate is sensitive to assumptions about the opacity and characteristic temperature." (3.2.2 ALMA Non-Detection)
- Limitation (authors): ALMA velocity resolution coarse  
  > "The velocity resolution in both ALMA channel maps is coarse (68 km/s in spectral window 0, 62 km/s in spectral window 2)" (2.3 Radio Observations: ALMA)
- Caveat (inferred, ours): ALMA non-detection conflicts with SMA 'detection' and is unexplained
- Caveat (inferred, ours): Disk mass limit relies on assumed opacity/temperature
- Caveat (inferred, ours): CO outflow comes from SMA data, not ALMA; ALMA part is minor
- Caveat (inferred, ours): Isochrone ages depend strongly on Teff scale

## Reproducibility

- Data public (paper): ALMA project code acknowledged; SMA data archival status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01527.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA/pipeline versions
- Missing: tclean parameters
- Missing: SMA line imaging parameters and outflow measurement method
- Missing: project code printed differs from archive-linked code (2015.1.01537.S)
- Data volume (inferred): ~1–5 GB (short Band 4 ALMA execution)
- Score (inferred): 3/5, Short ALMA dataset and simple mass calculation are reproducible, but imaging details are missing and the key outflow result is from SMA data.
- Rediscovery candidate: no, The main outflow result relies on SMA data and imaging details are incomplete; the ALMA part is only a non-detection.

## Links

- Method: (cite: WindemuthHerbst2014) (photometric observing and reduction process)
- Companion: (cite: Tokunaga2004) (H2 jet imaging)
- Companion: (cite: Winn2006) (dynamical model of the system)
- Related: SMARTS
- Related: NGC 2264

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.01527.S"
 ],
 "obscore_codes_not_in_card": [
  "2015.1.01537.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 51,
  "rate": 0.662
 },
 "evidence_ok": true
}
```
