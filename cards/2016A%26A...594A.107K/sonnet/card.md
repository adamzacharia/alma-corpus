# Close stellar conjunctions of α Centauri A and B until 2050 . An m<SUB>K</SUB> = 7.8 star may enter the Einstein ring of α Cen A in 2028

`2016A&A...594A.107K` | Astronomy and Astrophysics 2016 | first author: Kervella, P. | arXiv: 1610.06079 | DOI: 10.1051/0004-6361/201629201

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: stellar_physics, milky_way_ism
- Question: Where and when will alpha Cen A and B closely approach background stars until 2050, and what is the potential of these conjunctions (lensing, planet searches, astrometry)?  
  > "In this paper, we use new and archival observations of $\alpha$ Cen to determine the conjunctions with background stars that will occur in the coming decades." (Introduction)
- Target **alpha Centauri A and B**: coordinates A: 14:39:31.813 -60:50:00.01 (SOFI, 2009-02-25)  
  > "The main stars $\alpha$ Cen A and B are located at a distance of only $d = 1.338 \pm 0.001$ pc ($\pi = 747.17 \pm 0.61$ mas; Sect. [\[orbit\]](#orbit))." (Introduction); z/distance d = 1.338 ± 0.001 pc (π = 747.17 ± 0.61 mas)  
  > "The main stars $\alpha$ Cen A and B are located at a distance of only $d = 1.338 \pm 0.001$ pc ($\pi = 747.17 \pm 0.61$ mas; Sect. [\[orbit\]](#orbit))." (Introduction); distance from orbit fit in this paper  
  > "The main stars $\alpha$ Cen A and B are located at a distance of only $d = 1.338 \pm 0.001$ pc ($\pi = 747.17 \pm 0.61$ mas; Sect. [\[orbit\]](#orbit))." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00170.S
- bands: ALMA bands 6, 7, 8, 9 (relative astrometry of A and B)  
  > "ALMA B9$^b$" (Table 2); "shorter wavelengths in ALMA bands 7, 8 and 9" (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014.5126 (B7), 2014.5426 (B9), 2014.9574 (B6), 2015.3326 (B8)  
  > "| 2014.5426 | $282.91  \pm 0.15$ |      $4.208   \pm 0.01$ | **ALMA B9**$^b$  |" (Table 2)
- pi or archival as stated: archival observations collected by another team, not designed for absolute astrometry  
  > "Unfortunately, these observations were not designed to obtain the best possible absolute astrometry" (Observations and data reduction)
- Other facility **VLT/NACO**: new K_s imaging 27 March 2016 and archival acquisition image 2004; positions of S stars and A-B relative astrometry  
  > "We obtained a series of $60 \times 3$ s exposures using a $K_s$ broadband filter" (VLT/NACO adaptive optics)
- Other facility **NTT/SOFI**: archival J_s image 25 Feb 2009 used as reference frame for barycentre and S stars  
  > "This image was obtained on 25 February 2009 at UT 08:32:38." (NTT/SUSI2 and NTT/SOFI imaging)
- Other facility **NTT/SUSI2**: VRIZ imaging and field star catalog  
  > "The SUSI2 exposures of the field around $\alpha$ Cen in the $VRIZ$ bands were presented by , where a catalog of the sources is also provided." (NTT/SUSI2 and NTT/SOFI imaging)
- Other facility **Hipparcos**: 1991.25 positions of A and B for proper motion  
  > "we used the very accurate positions of $\alpha$ Cen A and B measured by *Hipparcos* at epoch 1991.25" (Apparent trajectories of alpha Cen A & B)
- External data: Radial velocity data set (SB9) used for orbit fit  
  > "We downloaded the radial velocities from the Ninth Catalog of Spectroscopic Binary Orbits" (Revised orbital elements and parallax) [from SB9 (Pourbaix et al. 2004)]
- External data: Archival relative astrometry of A-B from Washington Double Star catalog  
  > "The archival astrometric measurements were retrieved from the Washington Double Star catalog" (Revised orbital elements and parallax) [from Washington Double Star catalog]
- External data: Photometry of S stars (K07 catalog, Spitzer, WISE, MSX)  
  > "| Bessel V | 0.54 | $20.04 \pm 0.46$ | $3.5 \pm 1.6$ | K07 |" (Table 3) [from Kervella & Thévenin 2007]
- Simulation/model as data: Castelli-Kurucz SED model library used to fit S-star photometry  
  > "We adjusted to the photometry the spectral energy distribution (SED) models from the library by" (Approaches of S1 to S6 until 2031)

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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Same radial velocity data set as earlier orbit determination  
  > "we thus recomputed the orbital parameters of $\alpha$ Cen using the same high precision radial velocity data set as ." (Revised orbital elements and parallax) [from Pourbaix & Boffin 2016 (previous orbit)]
- NACO S27 astrometric calibration taken from earlier work  
  > "The astrometric calibration for the S27 camera is taken from : the plate scale is $27.01 \pm 0.05$ mas/pix" (VLT/NACO adaptive optics) [from not stated (citation missing in text)]

### Not stated but needed to reproduce (our reading)

- How the ALMA band 6-9 centroid positions were measured (imaging, fitting, beam, calibration from archive)
- Which ALMA data products or reduction used for the project 2013.1.00170.S
- Orbit fitting algorithm and weighting details
- Method for computing conjunction list and photometric extraction for NACO/SOFI
- Fit procedure for the SED (optimiser, priors)

## Analysis recipe

1. **Reference images to 2MASS frame**: Match WCS of SOFI, SUSI2 and NACO images to 2MASS using reference stars  
  > "The binding of the SOFI image to the 2MASS frame relies on a sample of 14 bright unsaturated stars spread over the SOFI field." (Astrometric referencing)
   - parameter: SOFI residual std 0.07 arcsec, adopted sigma 0.035 arcsec  
  > "We conservatively adopted an uncertainty of half of this value ($\sigma_\mathrm{SOFI} = 0.035\ensuremath{''}$)" (Astrometric referencing)
   - fitting: _not stated_
   - validation: NACO and SOFI agree within 0.05 arcsec on bright stars  
  > "We checked on the brightest stars that the agreement between the coordinate systems of NACO and SOFI is well within $\pm 0.05\ensuremath{''}$." (Astrometric referencing)
2. **Fit orbit, parallax and masses**: Fit A-B relative astrometry (incl. ALMA B9 as fiducial) and radial velocities with constant velocity terms and 3 m/s added jitter  
  > "We chose to give a dominant weight to the ALMA band 9 astrometry obtained at epoch 2014.5426, to make it our fiducial astrometric point." (Revised orbital elements and parallax)
   - parameter: uniform 3 m/s added quadratically to RV errors  
  > "we added quadratically a uniform uncertainty of $\sigma = 3$ m s$^{-1}$ to all radial velocity measurement errors" (Revised orbital elements and parallax)
   - fitting: _not stated_
   - validation: reduced chi2 = 0.95  
  > "The best-fit reduced $\chi^2$ is 0.95" (Revised orbital elements and parallax)
3. **Barycentric proper motion and trajectories**: Combine Hipparcos and SOFI barycentre positions corrected for parallax; propagate in 3D with orbital separation  
  > "The barycenter position is propagated in time using the 3-D velocity vector components to allow for the full 3-D rectilinear motion." (Apparent trajectories of alpha Cen A & B)
   - fitting: _not stated_
   - validation: ephemeris matches SOFI positions to 0.025 and 0.029 arcsec  
  > "match the observed positions with SOFI (Table [\[alfcen-positions\]](#alfcen-positions)) to $0.025\ensuremath{''}$ and $0.029\ensuremath{''}$, respectively." (Apparent trajectories of alpha Cen A & B)
4. **List conjunctions and characterise S stars**: Compute minimum approach distances for stars within 5 arcsec; fit SEDs of S1-S6 for Teff, angular diameter, E(B-V)  
  > "We limited our selection to impact parameters smaller than $5\ensuremath{''}$ (6.5 AU at the distance of $\alpha$ Cen)" (List of close approaches until 2050)
   - assumption: R_V = 3.1 Galactic extinction law; null proper motion for S1-S6; 10 mas/yr proper motion uncertainty for later stars  
  > "computed assuming a classical Galactic extinction law with $R_V = A_V / E(B-V)=3.1$" (Approaches of S1 to S6 until 2031)
   - fitting: _not stated_
   - validation: _not stated_
5. **Lensing deflection and amplification**: Point-lens Einstein radius, image shifts and amplification  
  > "The photometric amplification factor $A$ is given by the expression:" (Relativistic deflection and amplification)
   - assumption: Point lens, neglect other component  
  > "we consider only the gravitational lensing by the approached component of $\alpha$ Cen and we neglect the influence of the other." (Relativistic deflection and amplification)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Astropy** : acknowledged as used in the research  
  > "This research made use of Astropy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| parallax of alpha Cen | 747.17 | 0.61 | mas | 2 | / $\pi$ (mas) / $743 \pm 1.3$ / $747.17 \pm 0.61$ / |
| mass of alpha Cen A | 1.1055 | 0.0039 | Msun | 2 | / $m_A$ ($M_\odot$) / $1.133 \pm 0.0050$ / $1.1055 \pm 0.0039$ / |
| mass of alpha Cen B | 0.9373 | 0.0033 | Msun | 2 | / $m_B$ ($M_\odot$) / $0.972 \pm 0.0045$ / $0.9373 \pm 0.0033$ / |
| barycentric proper motion (RA, Dec) | -3619.9, +693.8 | 3.9 each | mas/yr | 3 | $\mu_\alpha = -3619.9\pm 3.9$ mas yr$^{-1}$ and $\mu_\delta = +693.8\pm 3.9$ mas yr$^{-1}$ |
| minimum approach distance of S5 to alpha Cen A (2028-05-06) | 0.015 | 0.135 | arcsec | 4 | $\rho_\mathrm{min} = 0.015\pm 0.135$ arcseconds |
| S5 angular diameter | 0.47 | 0.05 | mas | 4 | $\theta_\mathrm{LD} = 0.47 \pm 0.05$ mas |
| Einstein radius of alpha Cen A | 81.97 | 0.09 | mas | 5 | we obtained an Einstein radius of $\theta_E(A) = 81.97 \pm 0.09$ mas |
| probability S5 enters Einstein ring of alpha Cen A | 45 | not stated | percent | 5 | giving a probability of 45% that S5 will enter the Einstein ring of $\alpha$ Cen A |
| ALMA B9 relative separation A-B at 2014.5426 | 4.208 | 0.01 | arcsec | 2 | / 2014.5426 / $282.91  \pm 0.15$ /      $4.208   \pm 0.01$ / **ALMA B9**$^b$  / |

## Qualitative findings

- Position angle of A-B deviates ~+1 deg from earlier orbit predictions by 2016  
  > "reaching in 2016 approximately $+1^\circ$ (more than $3\sigma$ significance)" (Revised orbital elements and parallax)

## Claim tuples

- H: Do alpha Cen A/B have favourable close conjunctions with background stars before 2050? | E: Built a field-star catalog from SUSI2, SOFI, NACO and computed apparent trajectories | R: Six conjunctions to 2031; S5 (mK=7.8) passes 0.015±0.135 arcsec from A in May 2028 | F: S5 gives the most favourable conjunction in the next three decades | **supported**
- H: Can new differential astrometry (incl. ALMA) refine orbit and parallax? | E: Orbit fit with ALMA B9 fiducial point plus RVs | R: π = 747.17 ± 0.61 mas, smaller a, lower masses than previous work | F: Improved orbital parameters and parallax | **supported**
- H: Will S5 be lensed significantly? | E: Point-lens computation | R: 45% probability of entering Einstein ring; amplification could reach factor ~5 | F: Lensing may be observable | **partially**

## Reasoning

- Why this data: ALMA band 7-9 images give very accurate differential A-B astrometry despite poor absolute referencing  
  > "However, the differential astrometry within the interferometric field of view is very accurate, and essentially limited by the signal-to-noise ratio of the images." (ALMA millimeter interferometry)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA observations have 1-2 arcsec offsets from ICRS and were not designed for astrometry  
  > "variable offsets of 1 to $2\ensuremath{''}$ with respect to the ICRS are present in the images" (ALMA millimeter interferometry)
- Limitation (authors): S-star proper motions not statistically significant; nature of S stars poorly constrained by broadband photometry  
  > "broadband photometry alone is insufficient to determine precisely the nature of the S stars" (Approaches of S1 to S6 until 2031)
- Caveat (inferred, ours): ALMA centroid measurement procedure undocumented
- Caveat (inferred, ours): S5 impact parameter uncertainty larger than Einstein radius; predictions depend on Gaia refinement
- Caveat (inferred, ours): S-star distances and nature speculative

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; ESO archive data used  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00170.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA centroiding procedure and calibration details
- Missing: Orbit fit code/algorithm
- Missing: Reference citations in the text are mostly blank
- Data volume (inferred): ALMA part small (4 archival continuum images, tens of GB raw); NACO/SOFI small
- Score (inferred): 2/5, ALMA role minor and its processing is not described; orbit fit algorithm unspecified.
- Rediscovery candidate: no, ALMA processing not described and methods incomplete.

## Links

- Companion: Pourbaix & Boffin 2016 (previous orbital elements compared and radial velocity set reused)
- Related: ALMA 2013.1.00170.S (Liseau et al. 2015)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 35,
  "rate": 0.461
 },
 "evidence_ok": true
}
```
