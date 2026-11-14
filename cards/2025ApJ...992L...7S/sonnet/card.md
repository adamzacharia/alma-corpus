# Characterization of Two Cool Galaxy Outflow Candidates Using Mid-infrared Emission from Polycyclic Aromatic Hydrocarbons

`2025ApJ...992L...7S` | The Astrophysical Journal Letters 2025 | first author: Sutter, Jessica | arXiv: 2509.12058 | DOI: 10.3847/2041-8213/ae08b7

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: Do NGC 4424 and NGC 4694 host cool galactic outflows, as traced by extraplanar PAH emission in JWST MIRI F770W, and what are their gas masses and mass outflow rates?  
  > "We characterize two candidate cool galactic outflows in two relatively low mass, highly inclined Virgo cluster galaxies: NGC 4424 and NGC 4694." (abstract)
- Target **NGC 4424**: coordinates _not stated_; z/distance 16.20 Mpc  
  > "| Distance \[Mpc\] | 16.20 | 15.76 |" (Table 1); "Distances are from (cite: Anand2021)" (Table 1); distance from Anand2021  
  > "| Distance \[Mpc\] | 16.20 | 15.76 |" (Table 1); "Distances are from (cite: Anand2021)" (Table 1)
- Target **NGC 4694**: coordinates _not stated_; z/distance 15.76 Mpc  
  > "| Distance \[Mpc\] | 16.20 | 15.76 |" (Table 1); "Distances are from (cite: Anand2021)" (Table 1); distance from Anand2021  
  > "| Distance \[Mpc\] | 16.20 | 15.76 |" (Table 1); "Distances are from (cite: Anand2021)" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00886.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA CO(2-1) maps from the PHANGS-ALMA program (archival, from Leroy2021a,b)  
  > "Atacama Large Millimeter Array (ALMA) maps of the CO (*J*=2-1) line obtained as part of PHANGS program (cite: Leroy2021a; Leroy2021b)" (2.3 Multi-Wavelength Data)
- Line: CO J=2-1 (not stated)
- Other facility **JWST MIRI/NIRCam (PHANGS-JWST Cycle 2 Treasury)**: F770W, F2100W, F150W, F187N, F300M, F335M photometry; main data for outflow identification  
  > "which mapped them in two MIRI and four NIRCam bands" (2.3 James Webb Space Telescope Imaging)
- Other facility **VLT/MUSE**: optical IFU data for SFR surface density and ionized-gas emission  
  > "The MUSE data are used to measure the star-formation rate surface density" (2.3 Multi-Wavelength Data)
- Other facility **VLA VIVA**: 21 cm HI maps  
  > "21 cm H I maps from the Very Large Array (VLA) Imaging of Virgo spirals in Atomic gas (VIVA) survey" (2.3 Multi-Wavelength Data)
- External data: Distances  
  > "Distances are from (cite: Anand2021)" (Table 1) [from (cite: Anand2021)]
- External data: Inclinations, PAs from rotation curves  
  > "orientation parameters are from (cite: Lang2020)" (Table 1) [from (cite: Lang2020)]
- External data: Stellar masses and SFRs  
  > "the stellar masses and star formation rates are from (cite: Leroy2019)" (Table 1) [from (cite: Leroy2019)]
- External data: Outflow velocity vs SFR from CO outflow sample  
  > "we would expect outflow velocities of $\sim$100-130 km s$^{-1}$" (4.2 Estimating Mass Outflow Rates in the MIR) [from (cite: Stuber2021)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: all JWST data smoothed to common 0.85'' (~65 pc) using stpsf models and Aniano2011 method  
  > "we smooth all data to a common resolution of 0.85$''$, which corresponds to a physical resolution of $\sim65$ pc in both candidates." (2.3 James Webb Space Telescope Imaging)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- JWST data processing with pjpipe  
  > "All JWST data were processed using `pjpipe`[^1] (cite: Williams2024), which supplements the official JWST pipeline." (2.3 James Webb Space Telescope Imaging) [from (cite: Williams2024)]
- F770W to gas surface density / I_CO(2-1) conversion  
  > "we first convert the F770W$_{\rm SS}$ map to a gas surface density map using the method described by (cite: Chown2025)." (4.2 Estimating Mass Outflow Rates in the MIR) [from (cite: Chown2025)]
- Stellar continuum subtraction F770W - 0.22 x F300M  
  > "we subtract stellar continuum using the calibration from (cite: Sutter2024)" (2.3 James Webb Space Telescope Imaging) [from (cite: Sutter2024)]
- ALMA CO data reduction  
  > "obtained as part of PHANGS program (cite: Leroy2021a; Leroy2021b)" (2.3 Multi-Wavelength Data) [from (cite: Leroy2021a; Leroy2021b)]

### Not stated but needed to reproduce (our reading)

- ALMA CO imaging/calibration details (arrays, beam, rms, moment-map method) not given; relies on PHANGS-ALMA release
- How moment 1 velocities of 13 and 39 km/s were extracted (region, masking)
- Exact contour construction details for 'red contours' used for l
- Uncertainty derivation of the mass outflow rate
- Mapping of PHANGS-ALMA CO products to the cited project code

## Analysis recipe

1. **Process and smooth JWST images, subtract stellar continuum**: pjpipe processing, smoothing to 0.85'' with Aniano2011 kernels; F770W_SS = F770W - 0.22 x F300M  
  > "F770W}_{\rm{SS}}=\rm{F770W}-0.22\times \rm{F300M}." (2.3 James Webb Space Telescope Imaging)
   - software: pjpipe, stpsf
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify outflow pixels**: Select pixels with F770W_SS/F300M above twice the mean central (<0.15 R25) value and beyond 0.15 R25; compare with 18 high-inclination galaxies  
  > "identifying all pixels with a F770W$_{\rm{SS}}$/F300M value greater than twice the average F770W$_{\rm{SS}}$/F300M value all pixels within the central 0.15$R_{25}$" (3 Outflow Candidate Identification)
   - fitting: _not stated_
   - validation: Comparison sample of 18 galaxies shows none reaching twice the central ratio  
  > "Only the two outflow candidate host galaxies show F770W$_{\rm{SS}}$/F300M reaching above twice the central ratio" (3 Outflow Candidate Identification)
3. **Derive gas mass**: Predict I_CO(2-1) from F770W_SS via galaxy-specific power-law relation, convert with alpha_CO = 0.8 and R21 = 0.65  
  > "We convert from predicted F770W$_{\rm SS}$-predicted $I_{\rm{CO}(2-1)}$ to a gas mass using a single $\alpha_{\rm{CO}}$ of $0.8$" (4.2 Estimating Mass Outflow Rates in the MIR)
   - parameter: m, b, x0 = 0.816, 0.406, 0.480 (NGC 4424); 0.821, 0.294, 0.360 (NGC 4694)  
  > "with $m, b, x_0 = 0.816, 0.406, 0.480$ for NGC 4424 and $0.821, 0.294, 0.360$ for NGC 4694" (4.2 Estimating Mass Outflow Rates in the MIR)
   - assumption: alpha_CO range 0.35 to 4.35 for uncertainty  
  > "Assuming a maximum and minimum $\alpha_{\rm{CO}}$ of the Milky Way $\alpha_{\rm{CO}}=4.35$" (4.2 Estimating Mass Outflow Rates in the MIR)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute mass outflow rate**: Mdot = M v / l with v = 80 +/- 20 km/s and l from largest radial extent of contours (1-2 kpc), no inclination correction  
  > "we assume a velocity of $v =80\pm20$ km s$^{-1}$" (4.2 Estimating Mass Outflow Rates in the MIR)
   - assumption: relatively constant density; velocity perpendicular to galaxy plane in maximal case  
  > "Assuming the maximal case that these velocities are exactly perpendicular to the plane of each galaxy" (4.2 Estimating Mass Outflow Rates in the MIR)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **pjpipe** : JWST data processing  
  > "All JWST data were processed using `pjpipe`" (2.3 James Webb Space Telescope Imaging)
- **stpsf** : PSF models for smoothing  
  > "The data were smoothed using the `stpsf` models" (2.3 James Webb Space Telescope Imaging)
- **astropy** : listed software  
  > "astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A)," (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| log10 gas mass NGC 4424 outflow | 7.11 | +0.74/-0.35 | log10 Msun | 3 | NGC 4424: $\log_{10}M[$M$_\odot]=7.11^{7.85}_{6.76}$ |
| log10 gas mass NGC 4694 outflow | 6.37 | +0.73/-0.36 | log10 Msun | 3 | NGC 4694: $\log_{10}M[$M$_\odot]=6.37^{7.10}_{6.01}$ |
| Mass outflow rate NGC 4424 | 0.4 | +2.0/-0.3 | Msun/yr | 4 | NGC 4424 is $\sim 0.4^{+2.0}_{-0.3}$ M$_{\odot}$ yr$^{-1}$ |
| Mass outflow rate NGC 4694 | 0.2 | +0.8/-0.15 | Msun/yr | 4 | NGC 4694 is $\sim0.2^{+0.8}_{-0.15}$ M$_{\odot}$ yr$^{-1}$ |
| Mean F770W_SS/F2100W in outflows (NGC 4424, NGC 4694) | 1.45, 1.38 | not stated | dimensionless | 0 | / $\overline{\rm{F770W_{\rm{SS}} / F2100W}}$ / 1.45 / 1.38 / |

## Qualitative findings

- Filamentary PAH emission extends off the stellar disk in both galaxies, bright in F770W and F2100W, absent in NIRCam bands; ionized gas outflows adjacent but not overlapping.  
  > "These ionized gas outflows seem to be adjacent to, but not overlapping with, the cool outflows detected in the F770W band." (4.1.2 MUSE IFU Observations)

## Claim tuples

- H: The two galaxies host cool outflows detectable in PAH emission | E: F770W_SS/F300M ratio maps compared with 18 high-inclination galaxies | R: Only these two show ratios above twice the central value off-plane and rising ratio with height | F: Extended PAH structures are candidate cool outflows, not tidal stripping | **supported**
- H: Outflows have mass loading near unity | E: MIR-derived gas mass with assumed velocity and extent | R: Mdot ~0.4 and ~0.2 Msun/yr | F: Consistent with mass loading ~unity but order of magnitude uncertain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: MIRI is more sensitive than ALMA CO for the faint outflow edges, so predicted I_CO from F770W is used  
  > "to leverage the higher sensitivity of the MIRI observations" (4.2 Estimating Mass Outflow Rates in the MIR)
- Alternative: F150W rejected for continuum removal due to striping; F300M used instead  
  > "We use the F300M images to remove continuum instead of F150W due to persistent striping in F150W" (2.3 James Webb Space Telescope Imaging)
- How they decided it was enough: _not stated_
- Limitation (authors): No velocity information from photometry so outflows cannot be confirmed; velocities highly uncertain; alpha_CO uncertainty up to factor of four  
  > "we cannot definitively confirm whether these structures are truly outflows" (1 Introduction); "less than half the pixels within the outflows have strong enough CO detections for a robust measurement of the velocity" (4.2 Estimating Mass Outflow Rates in the MIR)
- Caveat (inferred, ours): Velocity and path length poorly constrained, so Mdot is order-of-magnitude
- Caveat (inferred, ours): Tidal stripping/ram pressure not fully excluded
- Caveat (inferred, ours): Threshold of 2x central ratio is empirically set
- Caveat (inferred, ours): Single alpha_CO and R21 assumed

## Reproducibility

- Data public (paper): JWST data from MAST programs 2107 and 3707; ALMA data PHANGS-ALMA  
  > "These observations are associated with programs 2107 and 3707." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA CO moment map processing details
- Missing: Contour definitions for outflow region
- Missing: Mdot uncertainty propagation
- Data volume (inferred): ~10-50 GB (JWST mosaics plus PHANGS-ALMA CO cubes for two galaxies)
- Score (inferred): 3/5, Mostly public data and simple arithmetic, but key inputs rely on cited papers and ALMA use is minor with limited detail.
- Rediscovery candidate: no, ALMA role is minor and several steps rely on inherited calibrations and contours not fully specified.

## Links

- Method: (cite: Williams2024) (pjpipe JWST processing)
- Method: (cite: Chown2025) (F770W to CO/gas conversion)
- Method: (cite: Sutter2024) (stellar continuum subtraction calibration)
- Companion: (cite: Stuber2021) (CO outflow search in PHANGS-ALMA galaxies)
- Related: PHANGS-JWST Cycle 2 Treasury
- Related: PHANGS-ALMA
- Related: VIVA
- Related: PHANGS-MUSE

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 34,
  "rate": 0.436
 },
 "evidence_ok": true
}
```
