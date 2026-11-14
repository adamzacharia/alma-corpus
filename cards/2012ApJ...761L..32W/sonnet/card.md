# ALMA Submillimeter Continuum Imaging of the Host Galaxies of GRB 021004 and GRB 080607

`2012ApJ...761L..32W` | The Astrophysical Journal Letters 2012 | first author: Wang, Wei-Hao | arXiv: 1211.2807 | DOI: 10.1088/2041-8205/761/2/L32

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, transients
- Question: Do the GRB 021004 and GRB 080607 host galaxies at z>2 have significant dust-obscured star formation, and is the large afterglow extinction of the dark burst GRB 080607 representative of its host?  
  > "Here we use the ALMA results to estimate the infrared luminosities of the two host galaxies, and to examine whether there exist highly obscured star-forming regions that are not revealed by optical observations." (Introduction)
- Target **GRB 021004 host**: coordinates _not stated_; z/distance z=2.330  
  > "we observed the host galaxies of GRB 021004 ($z=2.330$) and GRB 080607 ($z=3.036$) at 345 GHz." (Introduction); distance from _not stated_
- Target **GRB 080607 host**: coordinates _not stated_; z/distance z=3.036  
  > "we observed the host galaxies of GRB 021004 ($z=2.330$) and GRB 080607 ($z=3.036$) at 345 GHz." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00101.S
- bands: _not stated_
- frequencies and spectral setup: Four spectral windows centered at 338, 340, 350, 352 GHz, each 2 GHz bandwidth  
  > "Four spectral windows were tuned to center at 338, 340, 350, and 352 GHz, each with a 2 GHz bandwidth." (Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array, Cycle 0  
  > "Observations of the continuum emission at 345 GHz from the host galaxies of GRB 021004 and GRB 080607 ware obtained using the ALMA 12-m array." (Observation and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.55"x1.25" (GRB 021004); 1.56"x0.87" (GRB 080607)  
  > "$1.55\ensuremath{''} \times 1.25\ensuremath{''}$, $-20\ensuremath{^\circ}$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma 0.113 mJy (GRB 021004); 0.098 mJy (GRB 080607)  
  > "| Sensitivity (1 $\sigma$) | 0.113 mJy | 0.098 mJy |" (Table 1)
- time on source: 42.6 min (GRB 021004); 48.2 min (GRB 080607)  
  > "| On-Target Integration | 42.6 min | 48.2 min |" (Table 1)
- observing dates: GRB 021004: Oct 22 and Nov 5, 2011; GRB 080607: Nov 16, 2011 and Jan 12, 2012  
  > "| Observing Date | Oct 22, 2011 | Nov 16, 2011 |" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **HST WFC3 F160W**: Optical/NIR image for overlay of ALMA contours  
  > "its 345 GHz flux contours overlaid on an *HST* WFC3 F160W image" (GRB 080607)
- External data: Infrared SED template library (105 templates) used to derive L_IR  
  > "this can be done using the infrared spectral energy distribution (SED) library of (cite: chary01)." (GRB 021004) [from Chary & Elbaz 2001 (cite: chary01)]
- External data: Stellar masses of hosts and optical photometry/SFRs for comparison  
  > "The host galaxy of GRB 080607 has a better constrained stellar mass of 1–3 $\times10^{10} M_\ensuremath{\odot}$ (cite: chen11a)." (Discussion) [from Chen et al. 2011a; Savaglio et al. 2009; Chen et al. 2009]

## Processing

### Calibration

- pipeline or manual: Calibrated by JAO; authors inspected the calibration in CASA  
  > "We further inspected the JAO calibration in CASA, and Fourier-transformed the complex visibility to make our own images." (Observation and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Delivered data already bandpass, flux and gain calibrated by JAO  
  > "The delivered data were already bandpass, flux, and gain (phase and amplitude) calibrated by JAO" (Observation and Data Reduction)
- flux calibrator: Callisto (GRB 021004); Titan (GRB 080607)  
  > "| Flux Calibrator | Callisto | Titan |" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: GRB 021004 left dirty; GRB 080607 CLEANed  
  > "We detect the host galaxy of GRB 080607, and therefore “CLEANed” the sidelobes of the detected object in CASA." (Observation and Data Reduction)
- weighting robust: Natural weighting  
  > "we gave all visibility data equal weights regardless of their density distribution in the $uv$ plane (i.e., “natural weighting”)." (Observation and Data Reduction)
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
- final beam: 1.55"x1.25", PA -20 deg; 1.56"x0.87", PA 3 deg  
  > "$1.56\ensuremath{''} \times 0.87\ensuremath{''}$, $3\ensuremath{^\circ}$" (Table 1)
- final rms: 0.094 mJy/beam within primary beam (GRB 080607)  
  > "The rms noise is measured to be 0.094 mJy beam$^{-1}$ within the primary beam." (GRB 080607)

### Inherited from earlier work

- SFR conversion SFR = 1.7e-10 L_IR/Lsun  
  > "SFR ($M_\ensuremath{\odot}$ yr$^{-1}$) $= 1.7\times10^{-10}$ $L_{\rm IR}/L_\ensuremath{\odot}$ (cite: kennicutt98)" (GRB 021004) [from (cite: kennicutt98)]
- Main-sequence relation SFR = 200 M11^0.9 for z~2  
  > "For $z\sim2$, (cite: daddi07) found SFR = 200 $M_{11}^{0.9}$ ($M_\ensuremath{\odot}$ yr$^{-1}$) for main-sequence galaxies" (Discussion) [from (cite: daddi07)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Imaging parameters: cell size, image size, CLEAN threshold/mask, iterations
- Method and region used for point-source and Gaussian fits
- How L_IR was integrated from templates (8-1000 micron) and template matching tolerance
- Flux scale uncertainty
- Whether the four spectral windows were all combined

## Analysis recipe

1. **Make continuum images**: Inspect JAO calibration, Fourier transform visibilities with natural weighting; dirty image for GRB 021004, CLEAN for GRB 080607  
  > "We further inspected the JAO calibration in CASA, and Fourier-transformed the complex visibility to make our own images." (Observation and Data Reduction)
   - software: CASA
   - parameter: natural weighting  
  > "(i.e., “natural weighting”)" (Observation and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure 345 GHz flux**: Point-source flux at host location; for GRB 080607 point-source and 2-D Gaussian fits  
  > "We measure a flux of 0.31 mJy by fitting the emission with a point-source model." (GRB 080607)
   - software: CASA
   - fitting: Point-source model and extended 2-D Gaussian  
  > "We therefore also fit the emission with an extended 2-D Gaussian, and obtain a slightly higher integrated flux of 0.32 mJy." (GRB 080607)
   - validation: Pixel brightness histogram fitted with Gaussian (sigma=0.096 mJy/beam); spurious-peak probability between 5e-4 and 5e-3  
  > "Thus the probability of finding a $>3.3\sigma$ spike at the location of our target is between $5\times10^{-4}$ (assuming a Gaussian noise) and $5\times10^{-3}$" (GRB 080607)
3. **Derive L_IR and SFR**: Redshift CE01 templates and select those consistent with the observed 345 GHz flux or upper limit; convert L_IR to SFR  
  > "We thus redshift the CE01 SEDs to $z=2.330$ and look for those with observed 345 GHz fluxes below our upper limit." (GRB 021004)
   - parameter: 3-sigma upper limit 0.33 mJy for GRB 021004  
  > "adopting the 3-$\sigma$ upper limit of 0.33 mJy" (GRB 021004)
   - assumption: Dust temperature from CE01 luminosity-dependent templates; cosmology H0=71, OmegaM=0.27, OmegaL=0.73  
  > "We adopt cosmological parameters of $H_0=71$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_M=0.27$, and $\Omega_\Lambda=0.73$" (Introduction)
   - fitting: _not stated_
   - validation: Compared SEDs with optical/NIR photometry and with optical SFRs  
  > "the bottom panel of Figure [2](#fig2) further shows that the SED is well represented by known dusty templates of local galaxies across the full spectral range." (GRB 080607)

## Software

- **CASA** : Calibration inspection, imaging, CLEAN, flux fitting  
  > "All the above calibration and imaging were carried out using Common Astronomy Software Applications (cite: mcmullin07)." (Observation and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| S345 GRB 080607 host | 0.31 | 0.09 | mJy | 2 | $S_{345} = 0.31\pm 0.09$ mJy |
| S345 GRB 021004 host | 0.17 | 0.11 | mJy | 2 | The 345 GHz point-source flux measured at the location of the host galaxy is $0.17\pm0.11$ mJy. |
| L_IR GRB 080607 host | 2.4e11 to 4.5e11 | range | Lsun | 3 | $L_{\rm IR}=(2.4$–$4.5)\times10^{11}~L_\ensuremath{\odot}$ |
| L_IR upper limit GRB 021004 host (3 sigma) | <3.1e11 | not stated | Lsun | 3 | 3-$\sigma$ upper limit of $L_{\rm IR}<3.1\times10^{11}~L_\ensuremath{\odot}$ |
| SFR GRB 080607 host | 41–77 | range | Msun/yr | 3 | The inferred SFR is between 41 and 77 $M_\ensuremath{\odot}$ yr$^{-1}$. |
| SFR upper limit GRB 021004 host | <53 | 3 sigma | Msun/yr | 3 | the 3-$\sigma$ upper limit of the SFR of the host galaxy is 53 $M_\ensuremath{\odot}$ yr$^{-1}$ |
| Detection significance GRB 080607 | 3.3 | not stated | sigma | 2 | we adopt the more conservative measurement of 0.31 mJy with a statistical significance of 3.3 $\sigma$. |

## Qualitative findings

- Neither host is a ULIRG; both lie at the faint end of the submillimeter galaxy population and are consistent with main-sequence galaxies.  
  > "The continuum imaging observations show that the two galaxies are not ultraluminous infrared galaxies" (abstract)

## Claim tuples

- H: GRB 080607 host is a dusty, highly star-forming galaxy | E: ALMA 345 GHz imaging and CE01 template fitting | R: S345=0.31±0.09 mJy, L_IR=(2.4-4.5)e11 Lsun, SFR 41-77 | F: LIRG-like host, not ULIRG; afterglow extinction is local to a sightline | **supported**
- H: GRB 021004 host has hidden dust-obscured star formation | E: Deep ALMA 345 GHz imaging | R: Not detected; L_IR<3.1e11 Lsun, SFR<53 | F: Not a ULIRG; consistent with optical SFRs | **supported**

## Reasoning

- Why this data: Selected fields with early-time afterglow spectra constraining ISM absorption; two extremes in column density  
  > "The GRB fields were selected to have early-time afterglow spectra available for constraining the ISM absorption properties of the host galaxies" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): GRB 080607 detection is marginal (3.3 sigma) with possible non-Gaussian noise; single-band photometry requires template dust temperature  
  > "However, there are hints of a non-Gaussian noise." (GRB 080607)
- Caveat (inferred, ours): Detection at 3.3 sigma with a second unassociated spike suggests noise may be non-Gaussian
- Caveat (inferred, ours): L_IR relies on a single band and local templates
- Caveat (inferred, ours): Only two targets

## Reproducibility

- Data public (paper): Project code given in acknowledgments; public status not explicitly stated  
  > "This paper makes use of the ALMA data: ADS/JAO.ALMA#2011.0.00101.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Details of template selection and L_IR integration
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Simple data and analysis, but imaging and fitting details missing.
- Rediscovery candidate: yes, Cycle 0 data are likely public, the recipe is short, and results are numeric fluxes.

## Links

- Method: Chary & Elbaz 2001 (cite: chary01) (IR SED template library)
- Companion: Chen et al. 2011a (cite: chen11a) (Optical SED fit of GRB 080607 host)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
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
  "stated": 35,
  "rate": 0.53
 },
 "evidence_ok": true
}
```
