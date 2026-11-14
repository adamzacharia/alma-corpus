# Unveiling the early-stage anatomy of a protocluster hub with ALMA

`2017MNRAS.464L..31H` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Henshaw, J. D. | arXiv: 1608.00009 | DOI: 10.1093/mnrasl/slw154

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What is the internal structure (filaments and cores) of the early-stage protocluster hub H6 in IRDC G035.39-00.33, and are the filament widths consistent with the quasi-universal ~0.1 pc width?  
  > "It remains unknown, for example, whether filamentary structures exist internally within hubs, and if so, what role they may play in the subsequent evolution of protocluster cores." (Introduction)
- Target **H6 hub in IRDC G035.39-00.33 (cloud H)**: coordinates _not stated_; z/distance kinematic distance 2.9 kpc  
  > "This cloud is reasonably massive ($\sim~2\times~10^{4}$ M$_{\odot}$ at a kinematic distance of $2.9\,{\rm kpc}$;" (Introduction); distance from (cite: simon_2006b; kainulainen_2013)  
  > "This cloud is reasonably massive ($\sim~2\times~10^{4}$ M$_{\odot}$ at a kinematic distance of $2.9\,{\rm kpc}$;" (Introduction)

## Data provenance

- ALMA projects: 2013.1.01035.S
- bands: Band 7 (1.07 mm continuum)  
  > "ALMA cycle 2 Band 7 observations were carried out towards the H6 hub" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 1.875 GHz centred on 277.5 GHz  
  > "The spectral set up included a 1.875 GHz continuum band centred on 277.5 GHz." (2 Observations)
- arrays: 12 m ALMA and 7 m ACA  
  > "using the 12 m ALMA and 7 m ACA arrays" (2 Observations)
- configurations: _not stated_
- baselines: shortest 7 m baseline 9 m  
  > "The shortest available baseline from the 7 m array was $D=9$ m." (2 Observations)
- angular resolution: 1.4 x 0.8 arcsec, PA -57.9 deg  
  > "with a position angle ${\rm P.\,A.}=-57.9\ensuremath{^\circ}$" (2 Observations)
- max recoverable scale: ~30 arcsec (~0.4 pc)  
  > "We are therefore sensitive to emission on scales up to $\sim30\,{\rm arcsec}$ ($\sim0.4\,{\rm pc})$." (2 Observations)
- sensitivity: 1 sigma rms 0.2 mJy/beam  
  > "The continuum image reaches a 1$\sigma_{\rm rms}$ noise level of 0.2 mJy beam$^{-1}$" (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Spitzer IRAC / GLIMPSE**: 8 micron image for context  
  > "shows the *Spitzer* Infrared Array Camera (IRAC) 8 $\mu$m  image of ${\rm G}035.39-00.33$" (2 Observations)
- Other facility **PdBI**: 3.2 mm continuum sources for comparison  
  > "yellow diamonds indicate the position of the 3.2 mm continuum sources previously identified with the Plateau de Bure Interferometer" (3 Results)
- External data: 1.2 mm dust continuum image of H6, used to estimate ~0.8 Jy integrated flux at 1.07 mm  
  > "we estimate that the integrated flux at 1.07 mm is $\sim0.8$ Jy (assuming a dust emissivity index, $\beta=1.75$)" (2 Observations) [from (cite: rathborne_2006)]
- External data: PdBI 3.2 mm core catalogue and mass range  
  > "yellow diamonds indicate the position of the 3.2 mm continuum sources previously identified with the Plateau de Bure Interferometer" (3 Results) [from (cite: henshaw_2016b)]
- External data: 1D velocity dispersion ~0.7 km/s (3D) from line fitting  
  > "the mean value derived from line-fitting; (cite: henshaw_2014)" (4 Anatomy) [from (cite: henshaw_2014)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune  
  > "Flux calibration was performed using Neptune." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: 12 m and 7 m data combined and imaged in CASA  
  > "The 12 m and 7 m visibility data were combined and imaged in casa." (2 Observations)
- deconvolver: MultiScale clean  
  > "Imaging and deconvolution was performed using MultiScale clean with natural weighting." (2 Observations)
- weighting robust: natural weighting  
  > "Imaging and deconvolution was performed using MultiScale clean with natural weighting." (2 Observations)
- uv taper: _not stated_
- cell size: 0.15 arcsec pixel  
  > "a single $0.15\,{\rm arcsec}\times0.15\,{\rm arcsec}$ pixel" (3 Results)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied before noise estimate  
  > "estimated from emission-free regions after primary beam correction" (2 Observations)
- array combination: 12 m + 7 m visibilities combined  
  > "The 12 m and 7 m visibility data were combined and imaged in casa." (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Assumptions for column density/mass (dust temperature, opacity, gas-to-dust) discussed in detail elsewhere  
  > "For an in-depth discussion on these considerations, please see (cite: henshaw_2016b)." (3 Results) [from (cite: henshaw_2016b)]
- Filament width models  
  > "Two independent models are used to establish the filament width ((cite: smith_2014; federrath_2016))." (3 Results) [from (cite: smith_2014; federrath_2016)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- Multiscale scales, clean threshold, and mask
- Number of mosaic pointings' weighting and 12m/7m relative weighting
- Exact filament crest definition, slice breadth, and fitting method/priors for the profile fits
- Background subtraction and beam-deconvolution procedure for the Gaussian width
- Mass-sensitivity conversion and flux uncertainty
- Filament F coordinates and region/field centre
- Whether the 7 m data were used for mass/flux corrections

## Analysis recipe

1. **Image combined 12 m + 7 m continuum**: Combined visibilities imaged with MultiScale clean, natural weighting  
  > "Imaging and deconvolution was performed using MultiScale clean with natural weighting." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared total flux (~0.5 Jy) to ~0.8 Jy estimated from 1.2 mm image; ~60 per cent recovered  
  > "The total flux in our ALMA image is $\sim0.5$ Jy, indicating that we recover about 60 per cent of the total flux." (2 Observations)
2. **Convert continuum to column density**: Optically thin dust emission to N_H  
  > "(i) the dust continuum emission is optically thin" (3 Results)
   - parameter: kappa = 1.26 cm2/g, T_d = 13 K, R_gd = 141  
  > "a dust temperature, $T_{\rm d}=13$ K." (3 Results)
   - assumption: Ossenkopf & Henning thin ice mantle dust, beta = 1.75  
  > "valid for the moderately coagulated thin ice mantle dust model of (cite: ossenkopf_1994), assuming $\beta=1.75$" (3 Results)
   - fitting: _not stated_
   - validation: Column density uncertainty ~50 per cent  
  > "the uncertainty in $N_{\rm H}$ is $\sim50$ per cent" (3 Results)
3. **Fit filament radial profile for width**: Median radial surface density profile of filament F fitted with Plummer (p=2, p=4) and Gaussian models  
  > "We follow a conservative approach to estimating the filament width, using the median, rather than mean surface density profile" (3 Results)
   - parameter: inclination i = 0; W_f ~ 3 R_flat for p=2  
  > "For $p=2$, the filament width is $W_{\rm f}\sim3R_{\rm flat}$" (3 Results)
   - fitting: Least-squares-like fit not specified; Plummer and Gaussian models  
  > "Two independent models are used to establish the filament width ((cite: smith_2014; federrath_2016)). First we consider the filament as an idealized cylinder, the surface density profile of which can be described by a Plummer profile" (Results)
   - validation: Individual fits to ~150 radial cuts; mean profile widths in footnote  
  > "From a sample of $\sim150$ radial cuts, we find a mean width of $W_{\rm f}\approx~0.029\,\pm\,0.013$ pc" (3 Results)
4. **Extract compact cores and derive properties**: Dendrogram leaves from astrodendro; masses, densities and free-fall times  
  > "we use astrodendro to first extract the sources." (3 Results)
   - software: astrodendro
   - parameter: min_value=3 sigma_rms; min_delta=1 sigma_rms; min_npix=60  
  > "${\tt min\_value}=~3\sigma_{\rm rms}$; ${\tt min\_delta}=~1\sigma_{\rm rms}$; ${\tt min\_npix}=60$." (Footnote 3)
   - fitting: _not stated_
   - validation: Compared with PdBI core masses (~30 per cent lower on average)  
  > "we note a $\sim30$ per cent reduction, on average (although this can be $\sim60$ per cent)" (3 Results)
5. **Compare width with sonic scale**: Federrath (2016) sonic scale without magnetic field  
  > "By excluding the effects of magnetic fields from equation [\[Eq:sonic\]](#Eq:sonic) (i.e. $\beta\rightarrow\infty$)" (4 Anatomy)
   - parameter: T=13 K, sigma_3D~0.7 km/s, L=0.35 pc  
  > "and $L=0.35$ pc (the projected extent of the filament in Fig. [2](#Figure:cont_map))" (4 Anatomy)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Combining and imaging 12 m and 7 m data  
  > "The 12 m and 7 m visibility data were combined and imaged in casa." (2 Observations)
- **astrodendro** : Core extraction via dendrogram leaves  
  > "we use astrodendro to first extract the sources." (3 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Filament width (Gaussian, deconvolved FWHM) | 0.028 | 0.005 | pc | 3 | $W_{\rm f}\approx~0.028\,\pm~\,0.005$ pc |
| Filament width (Plummer p=2) | 0.027 | 0.006 | pc | 3 | The resultant width is $W_{\rm f}\approx~0.027\,\pm\,0.006$ pc. |
| R_flat | 0.009 | 0.001 | pc | 3 | we find $R_{\rm flat}=0.009\pm0.001$ pc |
| Number of compact cores / leaves | 28 | not stated | dimensionless | 4 | Our ALMA continuum image also reveals the presence of 28 high-contrast, compact cores embedded within the filaments. |
| Core mass range | 0.3-10.4 | ~60 per cent | Msun | 4 | Leaf masses range from $0.3\,{\rm M_{\odot}}<M_{\rm c}<10.4\,{\rm M_{\odot}}$ |
| Sonic scale | ~0.03 | not stated | pc | 5 | we find a sonic scale $\lambda_{\rm sonic}\approx0.03$ pc |
| Flux recovered | ~60 | not stated | per cent | 1 | indicating that we recover about 60 per cent of the total flux |

## Qualitative findings

- The hub comprises multiple intra-hub filaments each with its own core population, rather than a single bead on a string.  
  > "it comprises multiple intra-hub filaments, each of which retains its integrity as an independent structure and possesses its own embedded core population." (abstract)

## Claim tuples

- H: Do filaments in the H6 hub match the ~0.1 pc quasi-universal width? | E: Fit Plummer and Gaussian models to the median radial profile of filament F | R: Width ~0.028 pc | F: Filaments are >=3 times narrower than 0.1 pc | **supported**
- H: Is the previously reported dearth of 2-8 Msun cores real? | E: Extract cores with astrodendro in the ALMA+ACA image | R: Cores found in the 2-8 Msun range | F: Dearth may be observational; low-mass cores form coevally | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Too few cores for a robust core mass function; sonic scale depends on the mosaic field of view.  
  > "With only 24 cores identified in this study, we are unable to establish a robust statistical determination of the mass function in the H6 hub." (4 Anatomy)
- Caveat (inferred, ours): Width from a single filament with fixed temperature 13 K
- Caveat (inferred, ours): Flux recovery ~60 per cent may bias widths and masses
- Caveat (inferred, ours): Uniform dust temperature for cores is questionable
- Caveat (inferred, ours): Sonic scale comparison is simplistic

## Reproducibility

- Data public (paper): Project code and acknowledgement given; public status not explicitly stated  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01035.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: clean parameters (scales, threshold, mask)
- Missing: profile fitting details
- Data volume (inferred): ~20-100 GB
- Score (inferred): 5/5, Data identified and key analysis parameters mostly given, but imaging and fitting details are missing.
- Rediscovery candidate: no, Imaging and fitting recipes are incomplete, and public availability is not stated.

## Links

- Method: (cite: henshaw_2016b) (Dust assumptions and core analysis)
- Companion: (cite: henshaw_2014) (Kinematics of the cloud)
- Related: GLIMPSE

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
  "facts": 74,
  "stated": 44,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
