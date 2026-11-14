# An ALMA view of the interstellar medium of the z = 4.77 lensed starburst SPT-S J213242-5802.9

`2016A&A...586L...7B` | Astronomy and Astrophysics 2016 | first author: Béthermin, M. | arXiv: 1601.01682 | DOI: 10.1051/0004-6361/201527739

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the ISM properties (gas mass, SFR, depletion time, [CII]/[NII] ratio, CO excitation) of the lensed starburst SPT2132-58 at z=4.77?  
  > "We investigated the physical properties of SPT2132-58, a lensed source at z=4.77." (Conclusion)
- Target **SPT-S J213242-5802.9 (SPT2132-58)**: coordinates _not stated_; z/distance z=4.768  
  > "SPT-S J213242-5802.9 at $z$=4.768 (cite: Weiss2013; Gullberg2015)" (Introduction); distance from Weiss2013; Gullberg2015  
  > "SPT-S J213242-5802.9 at $z$=4.768 (cite: Weiss2013; Gullberg2015)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00994.S, 2011.0.00957.S
- bands: Band 6 (new); Band 3 (cycle 0, reanalyzed)  
  > "SPT2132-58 was observed with ALMA in band 6 on February 23 2014" (2 Data)
- frequencies and spectral setup: 4 spws centered at 237.6, 239.5, 252.9, 254.8 GHz; 480 channels, 1875 MHz each  
  > "The four spectral windows are centered on 237.6, 239.5, 252.9, and 254.8 GHz." (2 Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 399 m  
  > "minimal baseline = 15 m, max = 399 m, RMS = 140 m" (2 Data)
- angular resolution: 1.55"x0.91" (band 6, natural); 7.7"x4.9" (band 3)  
  > "This results in a synthesized beam size of 1.55"$\times$0.91"." (2 Data)
- max recoverable scale: _not stated_
- sensitivity: 0.36 mJy/beam continuum; 1.6 mJy/beam per 25 km/s channel  
  > "The typical RMS noise is 0.36 mJy/beam for the continuum (combining the 4 spectral windows) and 1.6 mJy/beam/(25 km/s channel) for the spectra." (2 Data)
- time on source: 470 s  
  > "The on-source integration time is 470 s." (2 Data)
- observing dates: February 23 2014  
  > "on February 23 2014" (2 Data)
- pi or archival as stated: PI De Breuck  
  > "2012.1.00994.S, PI: De Breuck" (2 Data)
- Line: [NII] 205 um (1461.10 GHz)
- Line: CO 12-11 (1383.24 GHz)
- Line: [CI] 3P1-3P0 (492.16 GHz)
- Other facility **APEX/FLASH**: [CII] line  
  > "APEX/FLASH | (cite: Gullberg2015)" (Table 1)
- Other facility **ATCA**: CO(2-1)  
  > "ATCA | (cite: Aravena2015)" (Table 1)
- Other facility **SPT, LABOCA, Herschel/SPIRE**: continuum SED points  
  > "ALMA band 3, SPT, LABOCA, *Herschel*/SPIRE (Strandet et al. in prep.)" (4.1)
- External data: Magnification mu=5.7±0.5 from lens model  
  > "estimates the magnification to be $\mu$=5.7$\pm$0.5 (Spilker et al. in prep.)" (4.1) [from Spilker et al. in prep.]
- External data: CO(2-1) flux and T_dust=41K  
  > "T$_{\rm dust}$=41K, (cite: Aravena2015)" (4.1) [from (cite: Aravena2015)]
- External data: CO(5-4) flux  
  > "ALMA band 3 | (cite: Weiss2013)" (Table 1) [from (cite: Weiss2013)]
- External data: [CII] flux  
  > "APEX/FLASH | (cite: Gullberg2015)" (Table 1) [from (cite: Gullberg2015)]
- Simulation/model as data: Starburst SED templates of Magdis2012b; Nagao2012 [CII]/[NII] models  
  > "We used the starburst templates of (cite: Magdis2012b) to fit the continuum." (4.1)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "The data were calibrated by the standard ALMA pipeline." (2 Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "using the `clean` routine" (2 Data)
- deconvolver: _not stated_
- weighting robust: natural for spectra; Briggs robust=0.5 for continuum  
  > "We also produced a continuum image using a Briggs weighting with robust = 0.5" (2 Data)
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

- Band 3 cycle 0 data originally from Weiss2013, reanalyzed  
  > "we reanalyzed band 3 data obtained during the cycle 0 (cite: Weiss2013)" (2 Data) [from (cite: Weiss2013)]
- [CI] gas mass abundance and excitation factors  
  > "Assuming the abundance and excitation factors of (cite: Alaghband_Zadeh2013)" (4.1) [from (cite: Alaghband_Zadeh2013)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, clean threshold and masks
- Continuum subtraction and line-free channels
- Aperture dimensions for spectral extraction
- Actual values of abundance/excitation factors for [CI] mass
- SED fit details and photometry values
- Lens model (unpublished)

## Analysis recipe

1. **Image cubes and continuum**: CASA clean, natural weighting; Briggs 0.5 continuum  
  > "we chose a natural weighting to optimize the sensitivity" (2 Data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and fit lines**: Elongated aperture 2x beam; single Gaussian fits  
  > "All the lines are compatible with a single Gaussian function" (3 Results)
   - fitting: Gaussian, reduced chi2 up to 1.4  
  > "highest reduced $\chi^2$ is 1.4" (3 Results)
   - validation: _not stated_
3. **SED fit for L_IR and SFR**: Fit Magdis2012b starburst templates to multi-band continuum; SFR from Kennicutt1998  
  > "We used the starburst templates of (cite: Magdis2012b) to fit the continuum." (4.1)
   - assumption: Chabrier IMF; magnification 5.7  
  > "assuming a (cite: Chabrier2003) initial mass function" (4.1)
   - fitting: chi2_red=1.1  
  > "The quality of the fit is good ($\chi^2_{\rm red}$=1.1)" (4.1)
   - validation: _not stated_
4. **Gas mass, alpha_CO, depletion time**: [CI]-based gas mass (Papadopoulos2004); alpha_CO from CO(2-1) converted with SMG ratio  
  > "We estimated the gas mass from the \[CI\] emission (cite: Papadopoulos2004)." (4.1)
   - fitting: _not stated_
   - validation: Compared with alpha_CO from dust mass (Aravena2015)  
  > "This agrees with $\alpha_{\rm CO}$ of 0.9$\pm$0.3" (4.1)

## Software

- **CASA** : imaging with clean  
  > "We produced the images of our source with CASA (cite: McMullin2007)" (2 Data)
- **AIPS** : source size estimate  
  > "AIPS and CASA provide a similar best estimate of the source size" (3 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [NII] line flux | 1.73 | 0.15 | Jy km/s | 2 | 1.73$\pm$0.15 |
| CO(12-11) line flux | 1.36 | 0.16 | Jy km/s | 2 | 1.36$\pm$0.16 |
| Continuum flux at 246 GHz | 26.4 | 0.5 | mJy | 1 | integrated flux 26.4$\pm$0.5 mJy at 246 GHz |
| SFR | 1120 | 200 | Msun/yr | 3 | SFR of 1120$\pm$200 M$_\odot$/yr |
| Demagnified gas mass | 3.8e10 | 1.2e10 | Msun | 4 | demagnified gas mass of (3.8$\pm$1.2)$\times$10$^{10}$ M$_\odot$ |
| alpha_CO | 0.99 | 0.32 | Msun (K km/s pc2)^-1 | 4 | $\alpha_{\rm CO}$ = 0.99$\pm$0.32 |
| Depletion timescale | 34 | 13 | Myr | 4 | 34$\pm$13 Myr |
| [CII]/[NII] luminosity ratio | 26.3 | 5.7 | dimensionless | 0 | [CII]/[NII] luminosity ratio of 26.3$\pm$5.7 |

## Qualitative findings

- CO(12-11)/CO(5-4) ratio higher than all HERCULES sources; SLED does not settle presence of an AGN  
  > "SLED does not allow us to conclude on the presence or not of an AGN" (4.2)

## Claim tuples

- H: Is SPT2132-58 an extreme starburst? | E: SED fit, [CI] gas mass | R: SFR 1120 Msun/yr, Mgas 3.8e10, tdep 34 Myr | F: Very intense starburst with modest gas content | **supported**
- H: ISM metallicity | E: [CII]/[NII] ratio vs Nagao2012 models | R: ratio 26.3±5.7 | F: Chemically evolved ISM, 0.5-1.5 Zsun | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Depletion time may be underestimated if source is at end of starburst; differential magnification may affect line ratios  
  > "The depletion timescale could however be slightly underestimated if this source is observed at the end of the starburst." (4.1)
- Caveat (inferred, ours): Gas mass depends on [CI] with low S/N (3.2 sigma)
- Caveat (inferred, ours): Relies on unpublished lens model
- Caveat (inferred, ours): Very short exposure, single pointing

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Lens model
- Missing: SED photometry
- Missing: [CI] conversion parameters
- Missing: Imaging parameters
- Data volume (inferred): ~5-10 GB
- Score (inferred): 3/5, Data identified and public-type, but many imaging and modelling details missing or deferred to in-prep papers.
- Rediscovery candidate: no, Key inputs (magnification, SED photometry, [CI] factors) are unpublished or unstated.

## Links

- Companion: Weiss2013 (Original band 3 cycle 0 data)
- Companion: Gullberg2015 ([CII] detection)
- Companion: Aravena2015 (CO(2-1) and dust properties)
- Related: South Pole Telescope lensed sample
- Related: HERCULES

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 36,
  "rate": 0.514
 },
 "evidence_ok": true
}
```
