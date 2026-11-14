# Highly Ordered and Pinched Magnetic Fields in the Class 0 Protobinary System L1448 IRS 2

`2019ApJ...879...25K` | The Astrophysical Journal 2019 | first author: Kwon, Woojin | arXiv: 1805.07348 | DOI: 10.3847/1538-4357/ab24c8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How do magnetic fields change on ~100 au scales in the Class 0 proto-binary L1448 IRS 2, whose cloud-scale field is aligned with the outflow, and is the field consistent with a central disk or strong magnetic braking?  
  > "we report polarimetric observations of the Atacama Large Millimeter/submillimeter Array (ALMA) toward L1448 IRS 2 focusing on how the magnetic fields change on 100 au scales." (Introduction)
- Target **L1448 IRS 2**: coordinates _not stated_; z/distance about 300 pc  
  > "in the Perseus molecular cloud at a distance of about 300 pc" (Target and Observations); distance from Zucker et al. 2018; Ortiz-Leon et al. 2018  
  > "in the Perseus molecular cloud at a distance of about 300 pc" (Target and Observations)

## Data provenance

- ALMA projects: 2016.1.00604.S, 2013.1.00031.S
- bands: Band 6 (233 GHz continuum)  
  > "Polarimetric observations toward L1448 IRS 2 in ALMA Band 6 were made on 2016 November 12 and 14" (Target and Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 42 and 40 antennas  
  > "The November 12 and 14 tracks have 42 and 40 antennas in the array, respectively." (Target and Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.57" x 0.37" (PA = 9.14 deg)  
  > "The final image has a synthesized beam of $0.57\ensuremath{''}\times0.37\ensuremath{''}$ (PA = $9.14\ensuremath{^\circ}$)." (Target and Observations)
- max recoverable scale: _not stated_
- sensitivity: rms Stokes I ~0.10, Q and U ~0.014 mJy/beam; polarization intensity 0.008 mJy/beam  
  > "The noise levels of Stokes I (total intensity), Q, and U maps are $\sim0.10$, $\sim0.014$, and $\sim0.014$ mJy beam$^{-1}$, respectively." (Target and Observations)
- time on source: Individual tracks ~3 hours  
  > "Individual tracks were run over 3 hours to achieve a good parallactic angle coverage." (Target and Observations)
- observing dates: 2016 November 12 and 14  
  > "were made on 2016 November 12 and 14" (Target and Observations)
- pi or archival as stated: PI Woojin Kwon (2016.1.00604.S)  
  > "(2016.1.00604.S, PI: Woojin Kwon)" (Target and Observations)
- Other facility **ALMA CO 2-1 (Tobin et al. 2018)**: CO 2-1 outflow contours overlaid, beam 0.35" x 0.25"  
  > "The blue and red contours overlaid in the figure are CO 2-1 molecular line data taken by ALMA" (Results)
- External data: Outflow inclination ~57 deg  
  > "reported that the bipolar outflow is inclined by about $57\ensuremath{^\circ}$" (Polarization intensity and fraction) [from Tobin et al. 2007 (cite: 2007ApJ...659.1404T)]
- External data: Dust opacity 0.01 cm2/g at 233 GHz  
  > "$\kappa_{\nu}
= 0.01~\textrm{cm}^2\,\textrm{g}^{-1}$ at 233 GHz (cite: 1994A&A...291..943O)" (Magnetic field strength) [from Ossenkopf & Henning 1994 (cite: 1994A&A...291..943O)]
- External data: Dust temperature 30 K  
  > "$T_d = 30$ K (cite: 2009ApJ...696..841K)" (Magnetic field strength) [from Kwon et al. 2009 (cite: 2009ApJ...696..841K)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636, 1.085 Jy at 233 GHz, spectral index ~ -0.45  
  > "Its flux was set to 1.085 Jy at 233 GHz with a spectral index of about -0.45." (Target and Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Images were made using a Brigg’s weighting with a robust parameter of 0.5." (Target and Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Execution blocks calibrated separately and combined when imaging  
  > "All the execution blocks were calibrated separately and combined when making images." (Target and Observations)
- smoothing: _not stated_
- final beam: 0.57" x 0.37", PA 9.14 deg  
  > "The final image has a synthesized beam of $0.57\ensuremath{''}\times0.37\ensuremath{''}$ (PA = $9.14\ensuremath{^\circ}$)." (Target and Observations)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- Polarization calibration details (leakage, angle)
- Polarization debiasing recipe, S/N cut for vectors
- Pixel size, image size, clean threshold, masks
- Whether 2013.1.00031.S data were used and how
- Non-thermal linewidth was assumed, not measured
- Method for computing the 10 deg angle dispersion

## Analysis recipe

1. **Make Stokes I, Q, U and polarization maps**: Combine separately calibrated execution blocks and image with Briggs weighting; debias polarization intensity using Q and U noise  
  > "The polarization intensity map achieved by the Stokes Q and U maps with a debias using the Stokes Q and U map noise level has a RMS noise of 0.008 mJy beam$^{-1}$." (Target and Observations)
   - parameter: robust = 0.5  
  > "Images were made using a Brigg’s weighting with a robust parameter of 0.5." (Target and Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Infer B-field morphology and polarization fraction vs intensity**: Rotate polarization by 90 deg to get B vectors; compare with outflow; plot Pfrac vs I and read power-law slopes  
  > "In Figure [1](#fig_mag_out), we rotate the polarization directions by 90 degree and infer the magnetic fields." (Magnetic field morphology)
   - assumption: Grains aligned with magnetic fields; optical depth tau~0.2 at peak for T=30 K  
  > "which corresponds to an optical depth $\tau \sim 0.2$ when assuming $T = 30$ K" (Magnetic field morphology)
   - fitting: Slopes estimated qualitatively  
  > "Interestingly, Figure [4](#fig_pi) shows multiple slopes that encompass the limits of the distributions in a qualitative manner." (Polarization intensity and fraction)
   - validation: _not stated_
3. **Estimate B-field strength with DCF and magnetic braking timescale**: Smooth Q and U with 3x larger beam axes for background field, measure dispersion in 0.3-6.5 mJy/beam region, mass from dust continuum, apply DCF; Alfven speed and braking time  
  > "we smoothed the Stokes Q and U maps with a nine-times larger beam (extended in both major and minor axes of the original beam by a factor of three)" (Magnetic field strength)
   - parameter: F = 91 mJy, D = 300 pc, kappa = 0.01 cm2/g, Td = 30 K  
  > "Using $F_{\nu} = 91$ mJy, $D = 300$ pc" (Magnetic field strength)
   - assumption: Gas-to-dust ratio 100; trans-sonic non-thermal velocity ~0.3 km/s at 30 K; cylinder geometry  
  > "it may be reasonable to adopt the trans-sonic velocity at 30 K: $\sim 0.3$ km s$^{-1}$." (Magnetic field strength)
   - fitting: _not stated_
   - validation: Admitted very rough; outflow and collapse may degrade DCF  
  > "We are aware that the field orientations can be affected by outflows and gravitational collapse near a protostellar system, which will likely degrade the accuracy of the DCF method" (Magnetic field strength)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Plane-of-sky B field strength | 640 | not stated | microGauss | 3 | the magnetic field strength in the plane of the sky of about 640 $\mu$G |
| Total mass in 0.3-6.5 mJy/beam region | 0.08 | not stated | Msun | 3 | the total mass is estimated to be 0.08 M$_\ensuremath{\odot}$ |
| Magnetic braking timescale | ~1700 | not stated | years | 3 | This timescale is calculated to be $\sim1700$ years. |
| Position angle dispersion | 10 | not stated | deg | 3 | The measured dispersion is estimated as $10\ensuremath{^\circ}$ |
| Pfrac-I slope above 10 mJy/beam | -0.5 | not stated | dimensionless | 2 | For the central region that is brighter than 10 mJy beam$^{-1}$  the slope is $-0.5$. |
| Maximum polarization fraction | up to 40% | not stated | percent | 2 | The highest polarization fractions, reaching levels of up to 40% |

## Qualitative findings

- Clear hourglass B field, poloidal outside and toroidal at the center, plus a clumpy depolarized strip perpendicular to the outflow  
  > "poloidal in the outer regions and rapidly switching to toroidal in the inner region" (Conclusion)

## Claim tuples

- H: Does the B field change from outflow-aligned to a disk-like pattern on 100 au scales? | E: ALMA Band 6 polarimetry at ~100 au | R: Hourglass field with central toroidal-like pattern | F: Consistent with a toroidal field from a disk, though self-scattering or accretion-dragged fields are possible | **partially**
- H: Is the field strong enough to hinder disk formation? | E: DCF estimate | R: B_POS ~640 uG, braking time ~1700 yr | F: Braking should be efficient, in tension with a central disk, implying non-ideal MHD or turbulence | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Self-scattering cannot be ruled out with Band 6 alone; accretion-dragged field considered less likely  
  > "self-scattering cannot be ruled out by the data set taken only in Band 6" (Magnetic field morphology)
- How they decided it was enough: _not stated_
- Limitation (authors): DCF very rough; no observed non-thermal linewidth; central mass uncertain  
  > "We do not have an observational non-thermal linewidth" (Magnetic field strength)
- Caveat (inferred, ours): DCF in a collapsing, outflow-affected region with assumed linewidth is highly uncertain
- Caveat (inferred, ours): Band 6 alone cannot separate scattering from alignment
- Caveat (inferred, ours): Slope regimes are not fitted quantitatively

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and polarization pipeline details
- Missing: Imaging parameters beyond robust
- Missing: Polarization vector selection criteria
- Data volume (inferred): ~20-50 GB for two Band 6 polarization tracks
- Score (inferred): 4/5, Data are in the ALMA archive and the analysis is simple, but the calibration and imaging details are sparse.
- Rediscovery candidate: no, Calibration, polarization processing and vector selection are not specified enough to redo the recipe reliably.

## Links

- Method: Davis 1951; Chandrasekhar & Fermi 1953 (DCF field strength method)
- Companion: Tobin et al. 2018 (cite: 2018ApJ...867...43T) (ALMA CO 2-1 data used)
- Related: CARMA TADPOL

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 30,
  "rate": 0.476
 },
 "evidence_ok": true
}
```
