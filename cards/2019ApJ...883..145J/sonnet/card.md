# ALMA Unveils Widespread Molecular Gas Clumps in the Ram Pressure Stripped Tail of the Norma Jellyfish Galaxy

`2019ApJ...883..145J` | The Astrophysical Journal 2019 | first author: Jáchym, Pavel | arXiv: 1905.13249 | DOI: 10.3847/1538-4357/ab3e6c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: How is cold molecular gas distributed in the ram pressure stripped tail of ESO 137-001, and does it form in situ or come from direct stripping?  
  > "We would like to understand the formation and evolution of star-forming molecular clouds in RPS tails. What are the roles of in-situ formation versus direct stripping?" (Introduction)
- Target **ESO 137-001**: coordinates _not stated_; z/distance z = 0.0163; 1 arcsec ≈ 0.327 kpc  
  > "is one of the nearest ’jellyfish galaxies’ ($z=0.0163$)" (ESO 137-001); "assuming $H_0= 
71$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_M= 0.27$, $1\ensuremath{''}\approx 
0.327$ kpc" (ESO 137-001); distance from redshift with H0 = 71 km/s/Mpc, Omega_M = 0.27  
  > "is one of the nearest ’jellyfish galaxies’ ($z=0.0163$)" (ESO 137-001); "assuming $H_0= 
71$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_M= 0.27$, $1\ensuremath{''}\approx 
0.327$ kpc" (ESO 137-001)

## Data provenance

- ALMA projects: 2015.1.01520.S
- bands: Band 6, CO(2-1) at sky frequency 227.955 GHz  
  > "Using Band 6 in dual polarization mode, a spectral window was centered at the CO(2-1) line at a sky frequency of 227.955 GHz" (2 Observations)
- frequencies and spectral setup: FDM line window with ~0.64 km/s resolution; three continuum windows at ~229.746, 240.268, 241.942 GHz  
  > "Three spectral windows were set to observe the continuum, centered at sky frequencies of $\sim 
229.746$ GHz, 240.268 GHz, and 241.942 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array plus 7m ACA  
  > "Additional 7m ACA array observations were obtained to increase the maximum recoverable spatial scale." (2 Observations)
- configurations: _not stated_
- baselines: 12m: 15.1-469 m; ACA: 8.9-48.9 m  
  > "The antennas were arranged in compact configurations with baselines in the range $15.1- 
469$ m." (2 Observations)
- angular resolution: _not stated_
- max recoverable scale: ~18 arcsec (~6 kpc)  
  > "The largest recoverable scale is $\sim 18\ensuremath{''}$" (2 Observations)
- sensitivity: ~2.2 mJy/beam in 5 km/s channels (concatenated cube)  
  > "are $\sim 2.2$ mJy beam$^{-1}$ in 5 km s$^{-1}$ channels" (2 Observations)
- time on source: 12m ~1.9 min per pointing (131 pointings); ACA ~10 min per pointing (52 pointings)  
  > "An average on-source time per pointing was $\sim 1.9$ min." (2 Observations)
- observing dates: January to July 2016  
  > "The observations were carried out with ALMA from January to July, 2016" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **APEX**: single-dish CO(2-1) for flux comparison  
  > "We use our previously obtained single-dish observations of ESO 137-001 with APEX (cite: jachym2014)" (2.1 Compact-to-extended molecular ratio)
- Other facility **HST, MUSE, Chandra**: ancillary young-star, Halpha and X-ray images  
  > "together with observations from *HST*, *Chandra* and VLT/ *MUSE*" (abstract)
- External data: X-ray contours  
  > "Contours of X-ray emission are added into the overlay (cite: sun2010)." (3.3 Multi-phase view of the RPS tail) [from (cite: sun2010)]
- External data: MUSE Halpha map  
  > "later confirmed from the detailed MUSE H$\alpha$ map (cite: fumagalli2014)" (3.1) [from (cite: fumagalli2014)]
- External data: HI upper limit from ATCA  
  > "a weak upper limit obtained from ATCA (the Australia Telescope Compact Array) observations of $\sim 5\times 10^8~M_\odot$ (cite: vollmer2001)" (4.2) [from (cite: vollmer2001)]

## Processing

### Calibration

- pipeline or manual: 12m and ACA datasets calibrated separately with the ALMA pipeline  
  > "The 12m array and ACA datasets were calibrated separately with the ALMA pipeline." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, J1617-5848 (12m and ACA), J1427-4206 (ACA)  
  > "Flux calibration was based on observations of Titan, J1617-5848 (12m and ACA) and J1427-4206 (ACA only)." (2 Observations)
- flux scale uncertainty: CO flux uncertainties ~5-20%  
  > "The uncertainties in the CO flux are estimated to be about $5-20\%$." (2 Observations)
- self calibration: _not stated_

### Imaging

- task: CASA uvcontsub, Briggs cleaning, concatenate  
  > "the continuum was subtracted in the *uv-*plane using the task `uvcontsub` first, followed by Briggs cleaning with a robust parameter of 0.5" (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust 0.5 for cubes; robust 2.0 for final maps  
  > "the maps presented in this paper were produced with a robust parameter of 2.0" (2 Observations)
- uv taper: _not stated_
- cell size: 0.14 arcsec  
  > "The final cube measures $2048\times 
2048$ pixels of $0.14\ensuremath{''}$ per pixel" (2 Observations)
- image size: 2048x2048 pixels, 64 channels  
  > "64 channels of 5 km s$^{-1}$ width" (2 Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "The maps are corrected for primary beam attenuation." (2 Observations)
- array combination: 12m and ACA cubes concatenated with CASA concatenate after checking weights  
  > "The two datacubes were concatenated in a standard manner (after checking the ratio of the weights)" (2 Observations)
- smoothing: spectral smoothing to 5 km/s  
  > "spectral smoothing to 5 km s$^{-1}$" (2 Observations)
- final beam: ~1.4 x 1.2 arcsec, PA 58 deg  
  > "the synthesized angular resolution $\sim 1.4\ensuremath{''}\times 1.2\ensuremath{''}$ (${\rm PA}= 58^\circ$)" (2 Observations)
- final rms: ~2 mJy/beam  
  > "The resulting RMS level is $\sim 2$ mJy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- APEX single-dish CO observations used for comparison  
  > "We use our previously obtained single-dish observations of ESO 137-001 with APEX (cite: jachym2014)" (2.1) [from (cite: jachym2014)]
- Ram-pressure/orbit model for travel times and fireball separation  
  > "Semi-analytic modeling indicates that ESO 137-001 is currently only $\sim 100$ Myr before pericenter" (3.4) [from (cite: jachym2014)]

### Not stated but needed to reproduce (our reading)

- Clean threshold, masks and niter
- Line-free channels for uvcontsub
- Exact channel ranges/number of channels per clump in the manual integration
- Aperture definitions for CO features and APEX comparison
- Clump size and linewidth measurement method
- Weights applied when concatenating 12m and ACA
- Inputs for the stripping travel-time model

## Analysis recipe

1. **Image the CO(2-1) cube**: uvcontsub, Briggs clean, smooth to 5 km/s, concatenate 12m+ACA, primary beam correct  
  > "the continuum was subtracted in the *uv-*plane using the task `uvcontsub` first, followed by Briggs cleaning with a robust parameter of 0.5" (2 Observations)
   - software: CASA
   - parameter: robust 2.0 for final maps  
  > "produced with a robust parameter of 2.0" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make integrated intensity and velocity maps**: Manually identify peak channel per pixel and integrate a limited channel range around it; velocity field by analogous method  
  > "We therefore manually identified channels with maximum brightness in each pixel of the mosaic and integrated the spectrum only over a limited range of channels" (2 Observations)
   - software: astropy
   - fitting: _not stated_
   - validation: Better results than standard moment maps  
  > "With this procedure we were able to reach better results than with the standard moment maps." (2 Observations)
3. **Compare ALMA and APEX fluxes**: Flux ratio in common apertures to estimate resolved-out extended emission  
  > "in the tail regions the APEX-to-ALMA ratio increases to values of $3-4$" (2.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive H2 masses**: CO(2-1) flux converted via Solomon & Vanden Bout relation  
  > "We follow the standard relation for the CO(1-0) luminosity of (cite: solomon2005)" (Footnote 1)
   - assumption: CO(2-1)/CO(1-0)=0.8; alpha_CO Galactic 2e20 cm-2 (K km/s)-1; factor 1.36 for helium  
  > "assume the ratio of CO(2-1)-to-CO(1-0) of 0.8 (cite: leroy2009), and a CO/H$_2$ conversion factor of $2\times 10^{20}$ cm$^{-2}$(K km s$^{-1})^{-1}$" (Footnote 1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate clump virial parameters**: alpha = 5 sigma^2 R/(G M)  
  > "\alpha= 5\sigma^2 R/(G\,M)," (3.2)
   - fitting: _not stated_
   - validation: Uncertainty admitted to be large  
  > "however the uncertainty of these estimates may be large" (3.2)
6. **Test filament fragmentation**: Most unstable wavelength of isothermal cylinder compared with clump spacing  
  > "we can estimate the most unstable scale" (4.2)
   - assumption: T = 15 K  
  > "assuming $T= 15$ K to calculate the sound speed" (4.2)
   - fitting: _not stated_
   - validation: Within factor 2-3 of observed separation  
  > "which is within a factor of $\sim 2-3$ consistent with the observed clump separation in the filament" (4.2)

## Software

- **CASA** : calibration, uvcontsub, clean, concatenate  
  > "Using the CASA software package (cite: mcmullin2007)" (2 Observations)
- **astropy** : channel integration of spectra  
  > "CASA (cite: mcmullin2007), GILDAS (cite: guilloteau2000), astropy (cite: astropy2013)" (Software)
- **GILDAS** : listed in software section; use not stated  
  > "CASA (cite: mcmullin2007), GILDAS (cite: guilloteau2000), astropy (cite: astropy2013)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO flux of galaxy disk | 43 | 5 | Jy km/s | 2 | is $\sim 43\pm 5$ Jy km s$^{-1}$ |
| H2 mass of disk | 6.9e8 | not stated | Msun | 4 | H$_2$ mass[^1] of $\sim 6.9\times 10^8~M_\odot$ |
| CO flux of central tail | 57 | 10 | Jy km/s | 2 | total CO integrated flux of $57\pm 
10$ Jy km s$^{-1}$ |
| H2 mass of central tail | 9.1e8 | not stated | Msun | 4 | $M({\rm H}_2)\sim 9.1\times 
10^8~M_\odot$ |
| APEX-to-ALMA flux ratio in tail | 3-4 | not stated | dimensionless | 3 | the APEX-to-ALMA ratio increases to values of $3-4$ |
| virial parameter range | 2-12 | not stated | dimensionless | 5 | The parameter $\alpha$ spans a range of $\sim 2- 12$ |
| fragmentation lengthscale | ~250 | not stated | pc | 6 | the corresponding fragmentation lengthscale is $\sim 250$ pc |

## Qualitative findings

- Rich distribution of mostly compact CO clumps out to ~60 kpc, associated with all three tail components  
  > "the map reveals a rich distribution of mostly compact CO emission regions detected in the tail out to nearly 60 kpc distance from the disk" (3.1)

## Claim tuples

- H: Dense molecular gas is widespread in the tail | E: ALMA+ACA CO(2-1) mosaic | R: ~9e8 Msun H2 in compact clumps out to ~60 kpc | F: Tail hosts a large molecular gas reservoir | **supported**
- H: Tail clumps are gravitationally bound | E: Virial parameter estimate | R: alpha ~2-12 | F: Clumps are unbound and will disperse | **partially**
- H: CO features form in situ or by direct stripping | E: Morphology and orientation relative to tail and other phases | R: Tilted feature vs filament parallel to tail | F: Tilted feature likely directly stripped; parallel filaments likely formed in situ | **partially**
- H: Fireballs have molecular heads | E: CO overlay with HST and Halpha | R: CO clumps at heads of small, super and double-sided fireballs | F: First detection of molecular component of fireballs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Standard moment maps rejected since faint features hidden in noise  
  > "many faint features stayed hidden in the noise" (2 Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA resolves out 67-75% of tail CO due to missing total power  
  > "resolve out $\sim 67\%- 75\%$ of the CO emission" (2.1)
- Caveat (inferred, ours): Manual channel integration is subjective and not reproducible exactly
- Caveat (inferred, ours): Galactic alpha_CO assumed in tail
- Caveat (inferred, ours): Single-dish comparison not a proper short-spacing combination

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Clean parameters, masks and channel selections
- Missing: Aperture definitions
- Missing: Orbit/stripping model details
- Data volume (inferred): ~100-300 GB raw for 131-pointing 12m mosaic plus ACA
- Score (inferred): 5/5, Data identified and main steps given but manual integration and several imaging details unstated.
- Rediscovery candidate: no, Manual, subjective feature integration and unspecified apertures limit redoing the numbers.

## Links

- Companion: (cite: jachym2014) (Earlier APEX CO observations and stripping model of ESO 137-001)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 77,
  "stated": 48,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
