# Formation of wide binaries by turbulent fragmentation

`2017NatAs...1E.172L` | Nature Astronomy 2017 | first author: Lee, Jeong-Eun | arXiv: 1707.00233 | DOI: 10.1038/s41550-017-0172

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Did the wide protostellar binary IRAS 04191+1523 form by turbulent fragmentation, as tested by disk axis misalignment, young age and Keplerian-derived masses?  
  > "Finding an isolated low mass wide binary system in the earliest stage of formation, before tidal evolution could occur, would prove that turbulent fragmentation is a viable mechanism" (abstract)
- Target **IRAS 04191+1523**: coordinates Cycle 2 phase center (J2000) 04h22m00.41s, +15d30'21.2''  
  > "IRAS 04191+1523 is a known protostellar binary system with a projected separation of 6$''$.1 ($\sim 860$ AU) between members(cite: Duchene2004) in Taurus, whose distance is 140 pc." (main text); z/distance 140 pc (Taurus)  
  > "IRAS 04191+1523 is a known protostellar binary system with a projected separation of 6$''$.1 ($\sim 860$ AU) between members(cite: Duchene2004) in Taurus, whose distance is 140 pc." (main text); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00537.S, 2015.1.00186.S
- bands: 1.3 mm continuum (Band 6)  
  > "IRAS 04191+1523 was observed with ALMA simultaneously in the 1.3 mm continuum and the C$^{18}$O (J=2–1) emission on 4 January 2015" (main text)
- frequencies and spectral setup: Cycle 2: SPWs at 219.5604 (C18O), 216.113 (DCO+), 231.322 GHz (N2D+), 58.6 MHz each, 61 kHz resolution; continuum 234 GHz. Cycle 3: continuum windows at 231.1 and 218.5 GHz, 2 GHz each  
  > "each with a bandwidth of 58.6 MHz and spectral resolution of 61 kHz ($\Delta v \sim$0.08 km s$^{-1}$). A continuum window was centered at 234 GHz with a bandwidth of 468.75 MHz." (Methods)
- continuum bandwidth: _not stated_
- arrays: 12-m; 38 antennas (Cycle 2), 40 antennas (Cycle 3)  
  > "Forty 12-m antennas were used with baselines in the range from 15 m ($\simeq$11 k$\lambda$) to 3 km ($\simeq$2327 k$\lambda$)" (Methods)
- configurations: _not stated_
- baselines: Cycle 2: 15-350 m; Cycle 3: 15 m-3 km  
  > "baselines in the range from 15 m ($\simeq$10 k$\lambda$) to 350 m ($\simeq$255 k$\lambda$)" (Methods)
- angular resolution: Cycle 2 1.83''x1.26'' (natural); Cycle 3 0.24''x0.14'' (uniform)  
  > "to provide the synthesized beam size of $0''.24 \times 0''.14$ (PA=$14^{\circ}.7$) when the uniform weighting is adopted." (Methods)
- max recoverable scale: _not stated_
- sensitivity: Cycle 2 rms: C18O 7, DCO+ 5, N2D+ 8 mJy/beam, continuum 1.0 mJy/beam; Cycle 3 continuum 0.45 mJy/beam  
  > "For the Cycle 3 data, the rms noise level for the continuum is 0.45 mJy beam$^{-1}$." (Methods)
- time on source: Cycle 2 54 min total; Cycle 3 13 min  
  > "the total observing time was 54 minutes" (Methods)
- observing dates: 2015 Jan 4 (Cycle 2); 2016 Sep 28 (Cycle 3)  
  > "on 2015 Jan. 4 and during Cycle 3 (2015.1.00186.S, PI: Michael Dunahm) on 2016 Sep. 28" (Methods)
- pi or archival as stated: _not stated_
- Line: C18O J=2-1 (219.5604 GHz)
- Line: DCO+ J=3-2 (216.113 GHz)
- Line: N2D+ J=3-2 (231.322 GHz)
- Other facility **Herschel/PACS**: Images showing a single core (from literature)  
  > "The Herschel/PACS images(cite: Bulger2014) show a single core" (main text)
- External data: Total envelope mass 0.1 Msun  
  > "The total mass of the protostellar envelope is 0.1 M$_\odot$(cite: Young2006)." (main text) [from Young2006]
- External data: Luminosities 0.6 and 0.04 Lsun for A and B  
  > "The primary (protostar A) has a luminosity of 0.6 L$_\odot$, and the secondary (protostar B) has 0.04 L$_\odot$" (main text) [from Duchene2004; Connelley2008; Dang-Duc2016]
- External data: Dust opacity kappa_1.3 = 3.5 cm2/g  
  > "The assumed dust opacity, commonly used for disks(cite: Andrews2005), is $\kappa_{1.3}$= 3.5 cm$^2$ g$^{-1}$ ." (Methods) [from Andrews2005]

## Processing

### Calibration

- pipeline or manual: standard reduction with CASA  
  > "We carried out a standard reduction using CASA(cite: McMullin2007) for both data sets." (Methods)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (both cycles)  
  > "The nearby quasar J0510+1800 was used for phase and flux calibration" (Methods)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN algorithm  
  > "The visibility data were imaged using the CLEAN algorithm with natural weighting for C$^{18}$O" (Methods)
- deconvolver: _not stated_
- weighting robust: natural for C18O; uniform for continuum  
  > "uniform weighting was used for the continuum images to provide higher resolutions" (Methods)
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
- final beam: Cycle 3: 0.24''x0.14''; Cycle 2: 1.83''x1.26''  
  > "to provide the synthesized beam size of $1''.83 \times 1''.26$ (PA=$-88.3^{\circ}$) when the natural weighting is adopted." (Methods)
- final rms: _not stated_

### Inherited from earlier work

- Binary stability test (kinetic to gravitational energy ratio)  
  > "With these masses, we can test the stability of this protostellar binary system(cite: Pineda2015)." (Methods) [from Pineda2015]

### Not stated but needed to reproduce (our reading)

- CASA version
- CLEAN parameters (cell, image size, masks, threshold, robust)
- Continuum subtraction and line-free channels for C18O
- Details of Keplerian fitting (fit function, how the peak positions were weighted, systemic velocity)
- Flux calibrator flux density values
- Why the Cycle 2 resolution is quoted as both 1.5'' and 1.2''

## Analysis recipe

1. **Measure continuum flux, size and inclination**: Gaussian fits with CASA imfit on high-resolution continuum; inclination from cos^-1(min/maj)  
  > "The continuum flux density and peak intensity are measured with the task, imfit in CASA." (Supplementary Table 1)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared fluxes between low and high resolution images  
  > "The agreement between continuum fluxes from the two resolution images of protostar A indicates that the continuum sources are disks." (main text)
2. **Derive disk dust masses**: Optically thin M = D^2 F / (kappa B(T))  
  > "When the emission is optically thin and the dust temperature is constant, the disk mass is calculated by" (Methods)
   - assumption: Tdust 30 K, gas-to-dust 100, kappa1.3 = 3.5 cm2/g, D=140 pc  
  > "Assuming a dust temperature of 30 K and a gas-to-dust mass ratio of 100" (main text)
   - fitting: _not stated_
   - validation: _not stated_
3. **Position angles of disks**: Connect blue and red channel emission peaks per channel; mean and std for velocity shifts vs +-0.9 to +-1.4  
  > "In each channel, the positions of the blue- and red-shifted emission peaks were connected to determine the position angle." (Methods)
   - fitting: _not stated_
   - validation: _not stated_
4. **Protostellar masses from Keplerian rotation**: Gaussian-fit peak positions of C18O along a line per velocity; fit Keplerian profile in peak position-velocity diagram; correct by 1/sin^2 i; only blue wing for B  
  > "the position of the emission peak is found by Gaussian fitting of the emission distribution along the white line in Figure [3](#fig:disk) for a given velocity." (main text)
   - assumption: Edge-on for minimum mass; inclinations from continuum  
  > "Protostar A and B both have $M_*=0.09$ M$_\odot$, assuming edge-on disks" (main text)
   - fitting: _not stated_
   - validation: Power-law fits have index near 0.5  
  > "The best-fit power-law profiles to the data have power indices similar to the value (0.5) for the Keplerian rotation" (Methods)

## Software

- **CASA** : Calibration, CLEAN imaging, imfit  
  > "We carried out a standard reduction using CASA(cite: McMullin2007) for both data sets." (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk mass A | 3.70e-3 | 0.08e-3 | Msun | 2 | $(3.70 \pm 0.08) \times 10^{-3}$ M$_\odot$ |
| Disk mass B | 4.91e-3 | 0.22e-3 | Msun | 2 | $(4.91\pm 0.22) \times 10^{-3}$ M$_\odot$ |
| Inclination-corrected mass A | 0.14 | 0.01 | Msun | 4 | 0.14 (0.01) |
| Inclination-corrected mass B | 0.12 | 0.01 | Msun | 4 | 0.12 (0.01) |
| Disk PA difference (continuum) | 55 | 5 | deg | 1 | significantly different by $55\pm 5$ degrees |
| Disk axis misalignment (gas) | 77 | not stated | deg | 3 | The difference in the projected position angles of the two disks is about 77$\mbox{$^\circ$}$. |
| Orbital period | 5e4 | 5.5e3 | yr | 0 | $\sim5\times 10^4~(\pm~5.5\times10^3)$ years |

## Qualitative findings

- Both protostars host disks, and the system is too young for tidal evolution to have produced the wide separation.  
  > "The system is too young(cite: Dunham2006) to have evolved from a close binary and the disk axes are misaligned" (abstract)

## Claim tuples

- H: Wide binary formed by turbulent fragmentation | E: High-resolution ALMA continuum and C18O of both components | R: Misaligned disk axes (77 deg), orbital period ~5e4 yr comparable to age | F: Turbulent fragmentation formed the binary | **supported**
- H: Protostar B is a proto-brown dwarf | E: Keplerian rotation fits to C18O | R: M = 0.12 Msun after inclination correction | F: B is not substellar | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Disk fragmentation plus tidal evolution rejected: low stellar density in Taurus, tidal timescale ~100 Myr far exceeds system age  
  > "Disk fragmentation and tidal evolution by cluster members cannot explain the existence of this pair either because the stellar density in Taurus is too low" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Red wing of B is contaminated by infall, so only blue wing used  
  > "Therefore, we use only the blue wing to determine the Keplerian rotation for protostar B." (Methods)
- Caveat (inferred, ours): Keplerian masses depend on inclinations from dust size ratios with large uncertainty
- Caveat (inferred, ours): Infall contamination may bias velocity profiles
- Caveat (inferred, ours): Single system; age estimate relies on assumed accretion rate
- Caveat (inferred, ours): Fit uncertainties likely underestimate systematics

## Reproducibility

- Data public (paper): Data available from ALMA archive for both project codes  
  > "are available from ALMA archives with project codes 2013.1.00537.S" (Methods)
- Products in archive: _not stated_
- Missing: CASA version and CLEAN parameters
- Missing: Keplerian fitting details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and simple analysis, but imaging and fitting details missing.
- Rediscovery candidate: yes, Public data, simple imfit and Keplerian analysis with numeric results, though some settings are unstated.

## Links

- Companion: Offner2016 (Misalignment as an indicator of turbulent fragmentation)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 34,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
