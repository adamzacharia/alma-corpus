# On the Nature of the Tertiary Companion to FW Tau: ALMA CO Observations and SED Modeling

`2015ApJ...806L..22C` | The Astrophysical Journal Letters 2015 | first author: Caceres, Claudio | arXiv: 1504.05644 | DOI: 10.1088/2041-8205/806/2/L22

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What is the nature of the tertiary companion to FW Tau: a brown dwarf in an edge-on disk or a planetary mass object in a low-inclination disk?  
  > "current observations are consistent with either a brown dwarf embedded in an edge-on disk or a planet embedded in a low inclination disk" (abstract)
- Target **FW Tau (triple system, tertiary companion)**: coordinates _not stated_; z/distance d~140 pc  
  > "This system belongs to the nearby ($d\sim140$ pc) and young ($\sim2$ Myr) Taurus-Auriga star forming region (cite: goldsmith_etal2008)." (Introduction); distance from Taurus-Auriga region distance (cite: goldsmith_etal2008)  
  > "This system belongs to the nearby ($d\sim140$ pc) and young ($\sim2$ Myr) Taurus-Auriga star forming region (cite: goldsmith_etal2008)." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00350.S
- bands: Band 6, Cycle 1  
  > "We obtained one epoch observation in band 6, with the correlator configured to obtain one baseband centered at 230.52 GHz" (ALMA cycle 1 observations)
- frequencies and spectral setup: one baseband at 230.52 GHz for 12CO(2-1); continuum basebands at 228.52, 214.52, 212.52 GHz; 488.28 kHz spacing, 3840 channels per 1.875 GHz baseband  
  > "with a unique spectral spacing of 488.28 kHz in 3 840 channels for each 1.875 GHz baseband" (ALMA cycle 1 observations)
- continuum bandwidth: 7.5 GHz total  
  > "The total bandwidth for the observations was 7.5 GHz" (ALMA cycle 1 observations)
- arrays: _not stated_
- configurations: 27 antennas, compact configuration  
  > "The observations were carried out using 27 antennas in a compact configuration" (ALMA cycle 1 observations)
- baselines: 15.8 m to 462.9 m (12.2 to 356.1 kλ)  
  > "implying we obtained baselines ranging from 15.8 m to 462.9 m (12.2 to 356.1 k$\lambda$)" (ALMA cycle 1 observations)
- angular resolution: 0.75" x 1.31", PA -48.6 deg  
  > "with an elongated beam size of $0.75\ensuremath{''}\times1.31\ensuremath{''}$ and a position angle of $-48.6\ensuremath{^\circ}$ (north-east)" (ALMA cycle 1 observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.18 mJy/beam; CO channel rms 21.1 mJy/beam per 0.635 km/s  
  > "The mean rms associated to the individual $^{12}$CO (2–1) channels is 21.1 mJy/beam per 0.635 km s$^{-1}$ bin" (ALMA cycle 1 observations)
- time on source: 3.6 min  
  > "which translates to a total time on source of 3.6 min for the field" (ALMA cycle 1 observations)
- observing dates: 2013 December 4  
  > "We observed FW Tau with ALMA in Cycle 1 on 2013 December 4." (ALMA cycle 1 observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.52 GHz)
- Other facility **Spitzer, Herschel, WISE, near-IR imaging, JCMT**: Literature photometry for the SED  
  > "These unresolved observations cover the *Spitzer* photometry from (cite: cieza_etal2012), the *Herschel* data from (cite: howard_etal2013)" (Spectral Energy Distributions)
- External data: Near-IR photometry of binary and third component (J,H,K,L)  
  > "(1) (cite: kraus_etal2014)" (Table 1) [from (cite: kraus_etal2014)]
- External data: 1.3 mm flux 1.78±0.03 mJy of third object  
  > "This detection is above the $1.78\pm 0.03$ mJy reported by and" (ALMA cycle 1 observations) [from (cite: kraus_etal2015)]
- External data: 850 um 4.5±1.1 mJy and 450 um upper limit  
  > "the $4.5\pm1.1$ mJy at 850 $\mu$m measurement of (cite: andrews_williams2005)" (ALMA cycle 1 observations) [from (cite: andrews_williams2005)]
- External data: Herschel 70-160 um photometry  
  > "(5) (cite: howard_etal2013)" (Table 1) [from (cite: howard_etal2013)]
- External data: Evolutionary models for mass-age-luminosity  
  > "assuming the evolutionary models of (cite: baraffe_etal2015)" (Disk models) [from (cite: baraffe_etal2015)]

## Processing

### Calibration

- pipeline or manual: Standard calibration steps  
  > "Standard calibration steps were applied to the data." (ALMA cycle 1 observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: one iteration of self-calibration for low-order phase errors  
  > "we applied one iteration of self-calibration in order to correct low-order phase calibration errors" (ALMA cycle 1 observations)

### Imaging

- task: CLEAN in CASA  
  > "Deconvolving the set of visibilities with the CLEAN task implemented in CASA (cite: mcmullin_etal2007)" (ALMA cycle 1 observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting we obtained the final images" (ALMA cycle 1 observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in the visibility domain  
  > "after removing the continuum contribution in the visibility domain" (ALMA cycle 1 observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.18 mJy/beam continuum  
  > "The continuum image has an rms of 0.18 mJy/beam" (ALMA cycle 1 observations)

### Inherited from earlier work

- Extinction A_V=0.4 for SED  
  > "we assumed an extinction towards the line of sight of $A_V=0.4$ (cite: kraus_etal2014)" (Disk models) [from (cite: kraus_etal2014)]

### Not stated but needed to reproduce (our reading)

- CASA version
- flux calibrator and flux scale
- line-free channels and continuum channel selection
- self-calibration solint and reference antenna
- image size, cell size, clean threshold
- MCFOST fitting procedure and parameter grid ranges
- how the line moment/position offset was measured

## Analysis recipe

1. **Image continuum and CO(2-1)**: CLEAN with natural weighting after self-calibration; continuum subtracted in uv  
  > "Deconvolving the set of visibilities with the CLEAN task implemented in CASA (cite: mcmullin_etal2007) and using natural weighting we obtained the final images." (ALMA cycle 1 observations)
   - software: CASA
   - fitting: Gaussian fit to the line profile  
  > "a maximum of 72.8 mJy, based on a Gaussian fit to the line profile" (ALMA cycle 1 observations)
   - validation: _not stated_
2. **Edge-on disk SED model**: MCFOST radiative transfer exploring Md, H0, beta, grain sizes, gamma, inclination 70-85 deg; mass constrained with age from Baraffe tracks  
  > "We explore various parameters for reproducing the SED, i.e. the disk dust mass $\mathrm{M}_\mathrm{d}$, the scale height at 100 au $H_0$" (An edge-on disk around a substellar object)
   - software: MCFOST
   - parameter: disk fixed to 100 au in diameter  
  > "We fixed the size of the disk to be 100 au in diameter" (An edge-on disk around a substellar object)
   - assumption: binary = two M5 dwarfs, Teff=3200 K, 0.22 Msun, 140 pc  
  > "with temperatures of $\mathrm{T}_\mathrm{eff}=3200$ K, masses of $M=0.22\,\mathrm{M}_\odot$ and a distance of 140 pc" (Disk models)
   - fitting: manual parameter exploration, no formal fit  
  > "A complete parameter study is beyond the scope of this letter and not warranted given the limited quality of the current data." (Disk models)
   - validation: compare to SED and CO line  
  > "As an example for an edge-on model that explains all the available observations, we show a model fit to the SED and the CO line assuming a 5 Myr old $40\,\mathrm{M}_\mathrm{Jup}$ third object" (Disk models)
3. **CO line model**: MCFOST gas model with ISM CO/H2, freezing 20 K, turbulence 0.1-0.2 km/s, observed spectral resolution  
  > "assuming an ISM CO/H$_2$ abundance, a freezing temperature of 20 K (cite: qi_etal2004; degregoriomonsalvo_etal2013), turbulent velocities ranging from 0.1–0.2 km s$^{-1}$" (An edge-on disk around a substellar object)
   - software: MCFOST
   - fitting: _not stated_
   - validation: _not stated_
4. **Planetary-mass companion model with external irradiation**: MCFOST disk irradiated by the binary at varying distance/orientation  
  > "the distance and the relative orientation of the binary with respect to the disk were changed in order to explore different configurations for the external illumination" (A disk around a planetary mass companion object)
   - software: MCFOST
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : CLEAN imaging  
  > "CLEAN task implemented in CASA (cite: mcmullin_etal2007)" (ALMA cycle 1 observations)
- **MCFOST** : dust and CO radiative transfer modeling  
  > "Using the radiative transfer code MCFOST (cite: pinte_etal2006; pinte_etal2009)" (An edge-on disk around a substellar object)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux of third object | 3.4 | 0.2 | mJy | 1 | The total flux from the third object is $3.4\pm0.2$ mJy. |
| 12CO(2-1) line center | 5.7 | not stated | km/s | 1 | centered at 5.7 km s$^{-1}$, with a measured FWHM of 1.9 km s$^{-1}$ |
| CO line integrated flux | 156 | not stated | mJy km/s | 1 | we obtain a total flux of 156 mJy km s$^{-1}$ |
| Offset between continuum and line peaks | 0.38 | 0.16 | arcsec | 1 | separated by $0.38\pm0.16$ arcsec |
| Edge-on model dust mass | ~3 | not stated | Earth masses | 2 | a dust mass of $\sim3\,\mathrm{M}_\oplus$ and a disk inner radius of $\sim 1$ au are required |
| Edge-on inclination | 80.5 | not stated | deg | 2 | an inclination close to $i\simeq80.5$ deg is required |
| Upper mass limit of third object (age<6 Myr) | ≲60 | not stated | MJup | 2 | would imply the mass of the third object to be $\lesssim60\,\mathrm{M}_\mathrm{Jup}$ |
| PMC model dust mass | ~2-3 | not stated | Earth masses | 4 | We find that $\sim2-3\,\mathrm{M}_\oplus$ of dust are enough to reproduce the emission |

## Qualitative findings

- First clear detection of single-peaked 12CO(2-1) from the third object, indicating a gas disk  
  > "present for the first time a clear detection of a single peak $^{12}$CO (2–1) line" (abstract)

## Claim tuples

- H: The third object hosts a gas disk | E: ALMA Band 6 12CO(2-1) imaging | R: SNR~4 single-peaked line at the companion position | F: gas disk exists, though low SNR | **supported**
- H: Edge-on disk around a brown dwarf explains the data | E: MCFOST SED and CO modeling | R: all excess reproduced with i=80.5 deg, 40 MJup | F: consistent; coeval argument implies substellar | **supported**
- H: Planetary-mass object with low-inclination disk explains the data | E: MCFOST with binary irradiation | R: SED and single-peaked line reproduced, with weak CO needing low gas mass | F: also consistent; cannot discriminate | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Stellar masses ruled out for the edge-on case if coeval with binary  
  > "We can therefore rule out stellar masses but the third object might be a forming brown dwarf seen edge-on." (An edge-on disk around a substellar object)
- How they decided it was enough: _not stated_
- Limitation (authors): Low SNR and possible cloud contamination prevent constraining mass; gas content unconstrained  
  > "the total gas content of the disk remains an observationally unconstrained parameter" (An edge-on disk around a substellar object)
- Caveat (inferred, ours): Models are single hand-picked examples without a formal fit or uncertainties
- Caveat (inferred, ours): SNR~4 line, unresolved data and cloud contamination make mass/inclination degenerate
- Caveat (inferred, ours): Only 3.6 min on source

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: MCFOST input files and parameter grid
- Missing: CASA version and clean parameters
- Missing: SED photometric dereddening details
- Data volume (inferred): ~10-20 GB raw (single short Band 6 execution)
- Score (inferred): 3/5, ALMA data are archival-accessible and the imaging steps are simple, but the modeling is non-formal and the parameters are only partly specified.
- Rediscovery candidate: no, Main modeling results are example models without a complete recipe; the numeric ALMA measurements are few.

## Links

- Method: (cite: pinte_etal2006; pinte_etal2009) (MCFOST radiative transfer code)
- Companion: (cite: kraus_etal2015) (Earlier ALMA 1.3 mm detection of the third object)
- Companion: (cite: kraus_etal2014) (Discovery/characterization of the tertiary)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 39,
  "rate": 0.565
 },
 "evidence_ok": true
}
```
