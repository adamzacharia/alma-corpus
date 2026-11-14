# The 2014 ALMA Long Baseline Campaign: First Results from High Angular Resolution Observations toward the HL Tau Region

`2015ApJ...808L...3A` | The Astrophysical Journal Letters 2015 | first author: ALMA Partnership | arXiv: 1503.02649 | DOI: 10.1088/2041-8205/808/1/L3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What is the structure, geometry, spectral index and molecular kinematics of the HL Tau disk at the highest resolution yet, and what do the bright and dark rings imply about planet formation?  
  > "What is the nature of the remarkable pattern of bright and dark rings in the continuum emission from the HL Tau protoplanetary disk?" (Discussion)
- Target **HL Tau**: coordinates 04:31:38.42545 +18:13:57.242 (J2000, 1.0 mm peak)  
  > "In this paper we adopt the standard mean distance to Taurus of 140 pc (cite: Rebull04) for the HL Tau region" (Introduction); "HL Tau | 04:31:38.42545 (0.00009) | 18:13:57.242 (0.001)" (Table 1); z/distance 140 pc  
  > "In this paper we adopt the standard mean distance to Taurus of 140 pc (cite: Rebull04) for the HL Tau region" (Introduction); "HL Tau | 04:31:38.42545 (0.00009) | 18:13:57.242 (0.001)" (Table 1); distance from mean Taurus distance (Rebull et al. 2004)  
  > "In this paper we adopt the standard mean distance to Taurus of 140 pc (cite: Rebull04) for the HL Tau region" (Introduction); "HL Tau | 04:31:38.42545 (0.00009) | 18:13:57.242 (0.001)" (Table 1)
- Target **XZ Tau A/B**: coordinates 04:31:40.097 +18:13:56.67  
  > "XZ Tau A                                                                                  | 04:31:40.09714 (0.00004) | 18:13:56.674 (0.001)" (Table 1); z/distance 140 pc (Taurus)  
  > "XZ Tau A                                                                                  | 04:31:40.09714 (0.00004) | 18:13:56.674 (0.001)" (Table 1); distance from Taurus mean distance  
  > "XZ Tau A                                                                                  | 04:31:40.09714 (0.00004) | 18:13:56.674 (0.001)" (Table 1)
- Target **LkHa358**: coordinates 04:31:36.15383 +18:13:42.919  
  > "LkH$\alpha$358                                                                            | 04:31:36.15383 (0.00007)" (Table 1); z/distance 140 pc (Taurus)  
  > "LkH$\alpha$358                                                                            | 04:31:36.15383 (0.00007)" (Table 1); distance from Taurus mean distance  
  > "LkH$\alpha$358                                                                            | 04:31:36.15383 (0.00007)" (Table 1)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 (2.9 mm), Band 6 (1.3 mm), Band 7 (0.87 mm)  
  > "the 1.3 mm and 0.87 mm data (Bands 6 and 7) have four 2 GHz (1.875 GHz usable) spectral windows" (2 Observations and Data Reduction)
- frequencies and spectral setup: Band 6/7: four 2 GHz continuum spws, 128 channels; Band 3: two tunings with narrow spws on HCO+, HCN, 12CO, CN  
  > "One used three continuum spws, along with two narrow bandwidth spws centered on HCO$^+$ (1-0) and HCN (1-0)" (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 15.2 km  
  > "baselines ranging from 15 m to 15.2 km" (2 Observations and Data Reduction)
- angular resolution: 0.075'' (10 AU) to 0.025'' (3.5 AU) continuum; 1.1'' and 0.25'' for lines  
  > "unprecedented angular resolutions of 0.075$''$ (10 AU) to 0.025$''$ (3.5 AU)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 30 min on-source per execution; 7 (Band 3), 9 (Band 6), 10 (Band 7) executions  
  > "Each of the 2.9 mm SBs were executed seven times, while the 1.3 mm and 0.87 mm SBs were executed nine and ten times respectively." (2 Observations and Data Reduction)
- observing dates: 2014 Oct 14 to Nov 14  
  > "The ALMA SV data on HL Tau was taken between 2014 October 14 and November 14 with baselines ranging from 15 m to 15.2 km." (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: HCO+ 1-0 (not stated)
- Line: HCN 1-0 (not stated)
- Line: 12CO 1-0 (not stated)
- Line: CN 1-0 (not stated)
- Other facility **HST**: Halpha and [SII] images shown with outflow  
  > "The strong H$\alpha$ and \[SII\] emission (observed with the *HST*)" (3 Results)
- External data: 1.3 mm CARMA position of HL Tau (epoch 2009.08) used for proper motion  
  > "The position reported by (cite: Kwon2011) from 1.3 mm CARMA observations is $04^{\rm h}31^{\rm m}38^{\rm s}.418$" (3.1.1 Position and Proper Motion) [from (cite: Kwon2011)]
- External data: Optical/IR proper motions from VizieR  
  > "the weighted average of optical and infrared proper motions for HL Tau listed in Vizier" (3.1.1 Position and Proper Motion) [from (cite: Dias2014; Zacharias2013; Roeser2010)]
- External data: JVLA 7 mm flux densities of XZ Tau  
  > "the JVLA 7 mm flux densities from (cite: Forgan2014)" (3.2 XZ Tau 2.9 mm Continuum) [from (cite: Forgan2014)]

## Processing

### Calibration

- pipeline or manual: CASA standard science operations procedure with two exceptions (corrected phase calibrator position, LBC antenna positions)  
  > "The data were calibrated in CASA 4.2.2 using the same procedure adopted for standard science operations, with two exceptions." (Imaging Details)
- casa version: CASA 4.2.2  
  > "The data were calibrated in CASA 4.2.2" (Imaging Details)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 and J0510+1800, chosen dynamically  
  > "alternated between the frequently monitored quasars J0423-0120 and J0510+1800" (Imaging Details)
- flux scale uncertainty: 5%  
  > "we estimate that the absolute flux calibration is good to within $5\%$ for the final combined data at each wavelength" (Imaging Details)
- self calibration: continuum iteratively self-calibrated; not applied to line data  
  > "the combined continuum data at each band was iteratively self-calibrated." (Imaging Details)

### Imaging

- task: CASA clean, multi-frequency synthesis  
  > "The continuum images for all three bands were made using multi-frequency synthesis" (Imaging Details)
- deconvolver: multiscale clean; nterms=2 for combined Band 6+7  
  > "accounting for spatial variations in the spectral index (CASA *clean* parameter *nterms=2*)" (Imaging Details)
- weighting robust: continuum robust=0.0; 1.1'' line cubes robust=0.5; 0.25'' HCO+ cube robust=0.0  
  > "CASA *clean* parameter *robust=0.0*" (Imaging Details); "imaged with *robust=0.5*, and a velocity width of 0.25 km s$^{-1}$" (Imaging Details)
- uv taper: lines tapered to ~1.1'' and ~0.25''  
  > "the data for the four Band 3 line transitions were tapered to a resolution of $\sim1.1\ensuremath{''}$" (Imaging Details)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 5, 15 (plus 45 for CO)  
  > "with scales of 0, 5, and 15, approximately corresponding to 0, 1, and 3$\times$ the synthesized beam" (Imaging Details)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: measurements made on primary-beam-corrected images  
  > "All measurements are made from images corrected for primary beam attenuation." (Table 1)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.9 mm 85.3x61.1 mas; 1.3 mm 35.1x21.8 mas; 0.87 mm 29.9x19.0 mas; 1.0 mm 33.5x21.1 mas  
  > "1.0 mm (Combined Band 6+7, 287.2 GHz) 33.5 $\times$ 21.1 mas, PA$= +9\ensuremath{^\circ}$" (Table 1)
- final rms: 9 (2.9 mm), 11 (1.3 mm), 23 (0.87 mm), 12 (1.0 mm) uJy/beam  
  > "HL Tau                                                                                    | 04:31:38.4253 (0.0002)   | 18:13:57.240 (0.004) | 9" (Table 1)

### Inherited from earlier work

- Detailed tuning frequencies, astrometry and LBC antenna position corrections  
  > "(cite: ALMA15a) gives the detailed tuning frequencies for each band." (2 Observations and Data Reduction) [from (cite: ALMA15a)]
- Distance of 140 pc  
  > "we adopt the standard mean distance to Taurus of 140 pc (cite: Rebull04)" (Introduction) [from (cite: Rebull04)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum selection per spw
- Self-calibration solution intervals and number of iterations
- Clean thresholds, masks, image size and cell size
- MCMC priors, likelihood and walker settings for ring ellipse fits
- Details of Gaussian visibility fit and deprojection
- Rest frequencies of lines
- Frequency of the exact spws used for each band continuum

## Analysis recipe

1. **Calibrate and image continuum and lines**: CASA calibration with corrected calibrator position, multiscale MFS clean, self-calibration; Band 6+7 combined with nterms=2 to give spectral index map  
  > "we also made a combined Band 6+7 (1.0 mm) image (fractional bandwidth $44\%$)" (Imaging Details)
   - software: CASA
   - parameter: robust=0.0, scales 0,5,15  
  > "with scales of 0, 5, and 15" (Imaging Details)
   - fitting: _not stated_
   - validation: Positions consistent across bands to better than 2 mas after correcting phase calibrator position  
  > "the positions are consistent between the three observed bands to better than 2 mas" (3.1.1 Position and Proper Motion)
2. **Measure positions, proper motion, flux densities**: Gaussian fits to peak; compare 1.0 mm ALMA position with CARMA position; flux within 4 sigma contour  
  > "The flux density was measured within the 4$\sigma$ contour" (Table 1)
   - assumption: 2 mas ALMA and 5 mas CARMA astrometric uncertainty  
  > "we assume an overall astrometric uncertainty of 5 mas for this measurement" (3.1.1 Position and Proper Motion)
   - fitting: Gaussian fitting  
  > "we first followed the standard practice of fitting a Gaussian to the visibility data." (Results, Continuum Emission)
   - validation: Compared with PdBI proper motion  
  > "This result is in good agreement with the proper motion adopted by (cite: Guilloteau2011)" (3.1.1 Position and Proper Motion)
3. **Fit ring ellipses for inclination and PA**: Points on zeroth-order ellipses moved to nearest radial max/min; ellipses fit with MCMC for eight most distinct rings; weighted mean i and PA  
  > "Eight rings retained $>55\%$ of the points, to which we subsequently fit an ellipse, including its center position, using a Markov Chain Monte Carlo (cite: Foreman2013)." (3.1.3 Spatially Resolved Disk Geometry and Spectral Index)
   - software: emcee
   - assumption: initial circular orbits about 1.0 mm peak with i, PA from Gaussian uv fit  
  > "we assumed that the rings trace circular orbits around a common center position defined by the 1.0 mm continuum peak position" (3.1.3 Spatially Resolved Disk Geometry and Spectral Index)
   - fitting: MCMC ellipse fit (priors not stated)  
  > "to which we subsequently fit an ellipse, including its center position, using a Markov Chain Monte Carlo" (Results, Spatially Resolved Disk Geometry and Spectral Index)
   - validation: Consistent with uv-plane Gaussian fit i=46.2, PA=138.2  
  > "we obtain $i = 46.2\pm 0.2\ensuremath{^\circ}$ and P.A.$=138.2\pm 0.2\ensuremath{^\circ}$" (3.1.2 Continuum Emission)
4. **Spectral index, brightness temperature and beta**: Spectral index from Band 6+7 image; T_B profile; beta = alpha - 2 in optically thin limit for dark rings  
  > "An estimate for the value of the dust opacity spectral index $\beta$ can be derived in the optically thin limit for warm dust where $\beta=\alpha-2$" (3.1.3 Spatially Resolved Disk Geometry and Spectral Index)
   - assumption: optically thin warm dust in dark rings  
  > "An estimate for the value of the dust opacity spectral index $\beta$ can be derived in the optically thin limit for warm dust where $\beta=\alpha-2$" (Results, Spatially Resolved Disk Geometry and Spectral Index)
   - fitting: _not stated_
   - validation: Compared T_B with Kwon2011 disk models  
  > "The observed $T_B$ in the central peak and the B1 ring do indeed lie between the values of $T_s$ and $T_m$ at those radii predicted from the (cite: Kwon2011) “thick-disk" model" (Results, Spatially Resolved Disk Geometry and Spectral Index)
5. **Disk kinematics and enclosed mass**: Keplerian estimate from HCO+ velocity extrema +-5 km/s at ~25 AU, i=47 deg, systemic 7.0 km/s  
  > "we find that with $i=47\ensuremath{^\circ}$, the enclosed mass is $\sim 1.3$ M$_\odot$" (3.1.4 Compact Spectral Lines)
   - assumption: circular Keplerian motion  
  > "Under the assumption of circular Keplerian motion" (3.1.4 Compact Spectral Lines)
   - fitting: _not stated_
   - validation: Caveat: infall and absorption complicate pattern  
  > "However, it is clear that even on the less absorbed red-shifted side, the velocity pattern is not so simple, and may for example have a contribution from infall" (Results, Compact Spectral Lines)

## Software

- **CASA** 4.2.2: calibration and imaging (clean)  
  > "The data were calibrated in CASA 4.2.2" (Imaging Details)
- **emcee** : MCMC ellipse fitting of rings (cited Foreman-Mackey 2013)  
  > "using a Markov Chain Monte Carlo (cite: Foreman2013)" (3.1.3 Spatially Resolved Disk Geometry and Spectral Index)
- **Astropy** : general analysis  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk inclination (ring fits) | 46.72 | 0.05 | deg | 3 | disk inclination ($46.72\ensuremath{^\circ}\pm0.05\ensuremath{^\circ}$) |
| Disk position angle (ring fits) | 138.02 | 0.07 | deg | 3 | position angle ($+138.02\ensuremath{^\circ}\pm0.07\ensuremath{^\circ}$) |
| HL Tau 1.0 mm flux density | 1441.5 | 1.8 | mJy | 2 | 1441.5 (1.8) |
| HL Tau 0.87 mm flux density | 2140.8 | 3.7 | mJy | 2 | the ALMA measurement of $2140.8\pm 3.7$ mJy |
| Average spectral index 2.9-0.87 mm | 2.77 | 0.13 | dimensionless | 4 | the average spectral index is $\alpha = 2.77\pm 0.13$ |
| Proper motion | v_RA=+18.5, v_Dec=-22.3 | 1 | mas/yr | 2 | $v_{R.A.}=+18.5\pm 1$ mas year$^{-1}$, and $v_{Dec.}=-22.3\pm 1$ mas year$^{-1}$ |
| Brightness temperature at peak, B1, B6 | 212.4, 59, 24 | 0.8, 3, 2 | K | 4 | 212.4$\pm 0.8$ K, $59\pm 3$ K, and $24\pm 2$ K |
| Enclosed (stellar) mass | ~1.3 | not stated | Msun | 5 | the enclosed mass is $\sim 1.3$ M$_\odot$ |
| beta in dark rings D1, D2, D5, D6 | ~0.8, 0.7, 0.6, 0.3 | not stated | dimensionless | 4 | We estimate $\beta\sim0.8$ for D1, $\beta\sim0.7$ for D2, $\beta\sim0.6$ for D5 and $\beta\sim0.3$ for D6 |
| XZ Tau A-B separation | 273 at PA 128.7 | 1 mas; 0.5 deg | mas | 2 | separated by 273$\pm1$ mas at a position angle of 128.7$\pm0.5\ensuremath{^\circ}$ |

## Qualitative findings

- Seven pairs of bright and dark rings seen at all wavelengths; ring centers offset from the continuum peak with offsets increasing with radius  
  > "Interestingly, the magnitude of the position offset increases with orbital distance from the center." (3.1.3 Spatially Resolved Disk Geometry and Spectral Index)

## Claim tuples

- H: Are the dark rings lower optical depth / column density features? | E: Spectral index and T_B profiles across rings | R: Dark rings have alpha ~2.3-3.0 and lower T_B than bright rings | F: Dark rings are optically thin with some grain growth | **supported**
- H: Do the rings point to planet formation? | E: Ring ellipse fits and period ratios | R: Center offsets increase with radius; near-integer resonances | F: Dark rings are likely gaps from planet formation | **partially**
- H: Can the molecular disk kinematics give the stellar mass? | E: HCO+(1-0) 0.25'' channel maps | R: Roughly Keplerian pattern 2-12 km/s, absorption at low blue velocities | F: M*~1.3 Msun, needs radiative transfer refinement | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Subtle azimuthal features may reflect uv-coverage differences; 12CO misses flux from lack of short spacings  
  > "we strongly caution against over-interpretation of subtle features unless verified by detailed modeling" (3.1.2 Continuum Emission)
- Caveat (inferred, ours): Ring ellipse offsets could arise from non-circular imaging artefacts or vertical structure
- Caveat (inferred, ours): Resonance claims depend on ring radii and Keplerian assumption
- Caveat (inferred, ours): Stellar mass from a single velocity extremum is crude

## Reproducibility

- Data public (paper): Raw data, calibration scripts and images publicly available from ALMA SV page  
  > "All of the images described in this paper are publicly available from the ALMA Science Verification page" (2 Observations and Data Reduction)
- Products in archive: _not stated_
- Code: Full imaging scripts on CASA guide  
  > "Additional details along with the full imaging scripts are available from <http://casaguides.nrao.edu/index.php?title=ALMA2014_LBC_SVDATA>." (Footnote 2)
- Missing: MCMC priors and ring-fit details
- Missing: Gaussian uv-fit specifics
- Missing: ALMA project code not printed in paper text
- Data volume (inferred): Several hundred GB (many long-baseline executions across three bands; raw ~ hundreds of GB)
- Score (inferred): 4/5, Public data, scripts and clear imaging parameters; some fit details missing.
- Rediscovery candidate: yes, Public SV data, stated imaging recipe, numeric results (i, PA, fluxes, spectral index).

## Links

- Method: (cite: ALMA15a) (LBC data description, tunings and astrometry)
- Method: (cite: Foreman2013) (MCMC sampler)
- Companion: (cite: ALMA15a) (Companion LBC paper)
- Related: ALMA 2014 Long Baseline Campaign Science Verification

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00015.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 59,
  "rate": 0.728
 },
 "evidence_ok": true
}
```
