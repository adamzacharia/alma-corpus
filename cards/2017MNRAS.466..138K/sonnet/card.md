# A merger in the dusty, z = 7.5 galaxy A1689-zD1?

`2017MNRAS.466..138K` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Knudsen, Kirsten K. | arXiv: 1603.03222 | DOI: 10.1093/mnras/stw3066

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the structure of the dust emission in z=7.5 galaxy A1689-zD1, what is its dust temperature, and can [CII] or CO(3-2) be detected to measure ISM properties and the systemic redshift?  
  > "In this paper we present a follow-up study of A1689-zD1 aimed at a detailed investigation of the structure of the dust emission and thus the distribution of obscured star formation." (Introduction)
- Target **A1689-zD1**: coordinates _not stated_; z/distance z = 7.5 (sigma_z ~ 0.2); magnification 9.3  
  > "A1689-zD1 is strongly lensed by a factor of 9.3, thus providing constraints on a sub-$L^\star$ galaxy" (Introduction); "The gravitationally-lensed galaxy A1689-zD1 is one of the most distant spectroscopically confirmed sources ($z=7.5$)." (abstract); distance from Lyman-alpha break in X-Shooter spectrum (Watson et al. 2015)  
  > "A1689-zD1 is strongly lensed by a factor of 9.3, thus providing constraints on a sub-$L^\star$ galaxy" (Introduction); "The gravitationally-lensed galaxy A1689-zD1 is one of the most distant spectroscopically confirmed sources ($z=7.5$)." (abstract)

## Data provenance

- ALMA projects: 2013.1.01064.S
- bands: Band 6 and Band 7  
  > "the observations carried out during December 2014 using band 6, and May 2015 and April 2016 with band 7." (2.1 ALMA observations)
- frequencies and spectral setup: Band 6: three setups of three spws, continuous 216.51-231.06 GHz; Band 7 tuned to 343.5 GHz continuum  
  > "which enabled continuous coverage from 216.51 to 231.06 GHz corresponding to the redshift range $z = 7.225-7.778$ for \[C ii\]" (2.1 ALMA observations); "The band 7 receiver was tuned to 343.5 GHz for continuum measurements." (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 348 m  
  > "The telescope configuration has baselines extending between 15 and 348 m." (2.1 ALMA observations)
- angular resolution: Beam dimensions ~1.3 x 0.68 arcsec implied (astrometric uncertainty half beam: 0.65 x 0.34 arcsec)  
  > "the most conservative estimate of the astrometric uncertainty is half the beam dimensions, meaning $\sim 0.65$ arcsec $\times 0.34$ arcsec." (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: Continuum rms 21 uJy/beam (B6), 45 uJy/beam (B7); cube rms ~0.5-0.8 mJy/beam/channel in 26 km/s channels  
  > "Using natural weighting, the obtained rms is 21 $\mu$Jy beam$^{-1}$ and 45 $\mu$Jy beam$^{-1}$, respectively." (2.1 ALMA observations)
- time on source: _not stated_
- observing dates: 08-12-2014 (B6); 05-05-2015 and 11-04-2016 (B7)  
  > "| 11-04-2016   | 42            | J1256$-$0547 | J1256$-$0547    | 343.5 (continuum)         |" (Table 1)
- pi or archival as stated: _not stated_
- Line: [CII] 2P3/2-2P1/2 (1900.537 GHz)
- Line: CO J=3-2 (GBT) (345.796 GHz)
- Other facility **GBT**: Q-band CO(3-2) search, 38.710-42.65 GHz, VEGAS  
  > "The dual-beam $Q$-band receiver was tuned to a central frequency of 40.265 GHz covering the frequency range of 38.710-42.65 GHz" (2.2 GBT observations)
- Other facility **HST**: Near-infrared image for comparison with ALMA contours  
  > "we show the bands 6 and 7 contours overlaid on an *HST* near-infrared image." (3.1 Continuum)
- External data: Rest of the SED (optical/NIR/Herschel photometry), stellar mass and SFR, redshift from X-Shooter  
  > "we show the measured fluxes together with the rest of the SED as presented in (cite: watson15)." (3.1 Continuum) [from (cite: watson15)]
- External data: Lensing magnification from updated Abell 1689 mass model  
  > "The estimates of the lensing magnification are based on an updated mass model of Abell 1689 (cite: limousin07)" (footnote 6) [from (cite: limousin07)]

## Processing

### Calibration

- pipeline or manual: Observatory pipeline reduction with minor extra flagging; band-7 flux scale of final observations adjusted manually  
  > "The results from the pipeline reduction[^4] carried out by the observatory was generally sufficient with only some minor extra flagging, which did not change the final result." (2.1 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede, Titan (B6); J1256-0547 (3C279) (B7)  
  > "| *Band 6* | 08-12-2014   | 35            | Ganymede     | J1256$-$0547    | 217.455, 219.036, 220.456 |" (Table 1)
- flux scale uncertainty: 10% conservative  
  > "we place a conservative flux calibration uncertainty of 10% for our band-6 results." (2.1 ALMA observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Using natural weighting, the obtained rms is 21 $\mu$Jy beam$^{-1}$ and 45 $\mu$Jy beam$^{-1}$, respectively." (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 26 km/s channels; spectrum Hanning smoothed  
  > "note that the spectrum shown in the figure is Hanning smoothed and the r.m.s. is $\sim0.3$ mJy" (3.2 [C ii] line search)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Astrometric uncertainty estimate as half the beam  
  > "Similar to our description in (cite: watson15), the most conservative estimate of the astrometric uncertainty is half the beam dimensions" (2.1 ALMA observations) [from (cite: watson15)]
- SED fits (magphys, grasil) updated from previous setup  
  > "We update the magphys (cite: dacunha08) and grasil (cite: silva98; iglesias07; michalowski10) SED model fits from (cite: watson15)" (3.1 Continuum) [from (cite: watson15)]
- CMB effect correction on observed flux  
  > "following the analysis of (cite: dacunha13)" (3.1 Continuum) [from (cite: dacunha13)]

### Not stated but needed to reproduce (our reading)

- Pixel size, image size, CASA version, and pipeline version
- Band 6 and 7 synthesized beams and uv coverage
- Line-free channels and any continuum subtraction
- Exact flux densities adopted for 3C279 in band 7 update
- uvmultifit initial parameters and fitting setup
- magphys/grasil priors and input photometry
- Procedure for Gaussian line fit and spectrum extraction aperture
- Lenstool model parameters for magnification

## Analysis recipe

1. **Fit continuum structure and flux**: uvmultifit with circular 2D Gaussians fit to bands 6 and 7 together, allowing astrometric offset between bands  
  > "Using the program uvmultifit (cite: martividal14) assuming a circular 2D Gaussian, we fit both bands together" (3.1 Continuum)
   - software: uvmultifit
   - fitting: _not stated_
   - validation: Elliptical Gaussian fit does not improve results  
  > "We note that fitting an elliptical 2D Gaussian function does not improve the results" (3.1 Continuum)
2. **Dust temperature and FIR luminosity from band ratio**: Modified blackbody nu^beta B_nu(T) fit to flux ratio B7/B6 with CMB correction for beta = 1.5, 1.75, 2.0  
  > "We constrain the temperature of a modified blackbody spectrum using the ratio of the fluxes from bands 7 and 6" (3.1 Continuum)
   - assumption: z = 7.5, CMB temperature ~23.4 K, magnification 9.3  
  > "For $z = 7.5$ the cosmic microwave background (CMB) temperature is $\sim
23.4$ K." (3.1 Continuum)
   - fitting: _not stated_
   - validation: _not stated_
3. **SED fitting for SFR, stellar and dust mass**: Update magphys and grasil fits with new ALMA photometry and CMB correction  
  > "using the new ALMA band 6 + 7 photometry including the same correction for CMB effects" (3.1 Continuum)
   - software: magphys, grasil
   - fitting: _not stated_
   - validation: Compared to Watson et al. 2015 results  
  > "The largest change in the derived parameters compared to (cite: watson15) is the lower nominal dust mass from the grasil fit" (3.1 Continuum)
4. **Search for [CII] line in band 6**: Extract spectrum at source position; map features above 0.6 mJy (2 sigma) integrated over 100 MHz; Gaussian fit to best candidate  
  > "We investigate all tentative emission features above 0.6 mJy (corresponding to $2\sigma$; indicated in Fig. [3](#fig:result)) and create maps integrated over 100 MHz" (3.2 [C ii] line search)
   - software: CASA
   - fitting: Gaussian fit to the 220.903 GHz feature  
  > "fitting a Gaussian function implies a peak flux density of $S_{\rm peak} = 0.77\pm0.20$ mJy beam$^{-1}$" (3.2 [C ii] line search)
   - validation: Spatial coincidence with continuum position  
  > "only in the case of 220.903 GHz are they following the same position as the dust continuum" (Mapping of candidate emission lines)
5. **CO(3-2) limit and gas mass**: 3 sigma limit from GBT spectrum with same linewidth as tentative [CII]; gas mass with CMB correction and alpha_CO  
  > "We place a $3\sigma$ limit for the same linewidth as the tentative \[C ii\] line ." (3.3 CO(3-2) line search)
   - software: gbtidl
   - assumption: Half of intrinsic flux missed due to CMB; thermally excited CO(3-2); alpha_CO = 4  
  > "Under the assumption that half of the intrinsic flux is missed due to the CMB radiation field and that the CO(3-2) is thermally excited" (3.3 CO(3-2) line search)
   - fitting: _not stated_
   - validation: _not stated_
6. **Merger probability estimate**: Abundance matching for halo mass, then merger rate from Millennium II fitting formulae integrated for xi_min = 0.3, z=7.5 to 15  
  > "we take the results of (cite: fakhouri10) based on the statistics of the Millennium II simulation (specifically, their fitting formulae 1 and 2)." (4.1 Could A1689-zD1 be a merging galaxy pair?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : reduction, calibration, imaging  
  > "was used for reduction, calibration, and imaging." (2.1 ALMA observations)
- **uvmultifit** : fitting Gaussians to visibilities  
  > "Using the program uvmultifit (cite: martividal14) assuming a circular 2D Gaussian" (3.1 Continuum)
- **gbtidl** : GBT data reduction and calibration  
  > "gbtidl was used to carry out the data reduction and calibration." (2.2 GBT observations)
- **magphys** : SED fit  
  > "We update the magphys (cite: dacunha08) and grasil" (3.1 Continuum)
- **grasil** : SED fit  
  > "grasil (cite: silva98; iglesias07; michalowski10) SED model fits" (3.1 Continuum)
- **lenstool** : lensing magnification  
  > "with the calculations done using lenstool (cite: jullo07; jullo09)." (footnote 6)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 7 total flux density | 1.33 | 0.14 | mJy | 1 | $f_{\rm B7} = 1.33\pm0.14$ mJy |
| Band 6 total flux density | 0.56 | 0.1 | mJy | 1 | $f_{\rm B6} = 0.56\pm0.1$ mJy |
| FWHM diameter NE component | 0.52 | 0.12 | arcsec | 1 | measure a diameter (FWHM) of $0.52\pm0.12$ arcsec and $0.62\pm0.12$ arcsec for the two components |
| FWHM diameter SW component | 0.62 | 0.12 | arcsec | 1 | measure a diameter (FWHM) of $0.52\pm0.12$ arcsec and $0.62\pm0.12$ arcsec for the two components |
| Dust temperature (beta=1.5, 1.75, 2.0) | 46.5, 40.5, 35.8 | not stated | K | 2 | We find the best-fitting values of $T \sim 46.5$, 40.5, and 35.8 K for $\beta = 1.5$, 1.75, and 2.0, respectively. |
| FIR luminosity (T=40.5 K, beta=1.75, lensing-corrected) | 1.8e11 | not stated | Lsun | 2 | the far-infrared luminosity is $1.7\times10^{12}$ L$_\odot$ ($1.8\times10^{11}$ L$_\odot$ after correcting for magnification) |
| Dust mass (magphys), log Mdust | 7.6 | +0.27/-0.18 | log Msun | 3 | $\log ( M_{\rm dust} / {\rm M}_\odot) = 7.6^{+0.27}_{-0.18}$ from magphys |
| Dust mass (grasil), log Mdust | 7.2 | 0.2 | log Msun | 3 | $\log ( M_{\rm dust} / {\rm M}_\odot) = 7.2\pm0.2$ from grasil |
| Tentative [CII] redshift | 7.6031 | 0.0004 | dimensionless | 4 | a redshift of $z_{\rm [CII]} = 7.6031\pm0.0004$ |
| Tentative [CII] velocity-integrated intensity | 0.126 | 0.050 | Jy km/s | 4 | $I_{\rm [CII]} = 0.126 \pm
0.050$ Jy km s$^{-1}$ |
| L[CII]/LFIR | <0.0002 | not stated | dimensionless | 4 | the luminosity ratio is $L_{\rm [CII]}/L_{\rm FIR} < 0.0002$ |
| Molecular gas mass upper limit | 7.2e9 | not stated | Msun | 5 | we estimate an upper limit on the molecular gas mass of $7.2\times10^9$ M$_\odot$ |
| Expected number of major mergers N_m | ~2.1 | not stated | dimensionless | 6 | we find that $N_m\sim2.1$. |

## Qualitative findings

- Dust continuum resolved into two components resembling HST NIR morphology, suggesting merger or clumpy disc  
  > "The rough spatial morphology is similar to what is observed in the near-infrared with *HST* and points to a perturbed dynamical state" (abstract)

## Claim tuples

- H: Does the dust emission of A1689-zD1 show resolved structure indicative of a merger or clumpy disc? | E: uvmultifit Gaussian fits to Band 6 and 7 continuum compared to HST | R: Two components of FWHM ~0.5-0.6 arcsec, sizes ~0.4-1.7 kpc after lensing correction | F: Galaxy is either two interacting proto-galaxies or a clumpy proto-disc | **partially**
- H: What is the dust temperature? | E: Modified blackbody fit to B7/B6 flux ratio with CMB correction | R: T ~35-45 K for beta 1.5-2 | F: FIR luminosity 1.8e11 Lsun consistent with previous single-band results | **supported**
- H: Can [CII] be detected to fix the redshift? | E: Band 6 spectral scan 216.5-231 GHz | R: No strong line; a 3 sigma tentative feature at 220.903 GHz | F: Tentative z=7.603; [CII] deficient relative to FIR | **partially**
- H: Is CO(3-2) detectable with GBT? | E: GBT Q-band spectrum | R: No detection; molecular gas mass limit <7e9 Msun | F: CMB could explain non-detection; limit only order-of-magnitude | **supported**

## Reasoning

- Why this data: Band 6 designed to cover wide frequency range since redshift came from Lyman break only  
  > "we designed the observations to cover a large frequency range." (2.1 ALMA observations)
- Why this method: _not stated_
- Alternative: Elliptical Gaussian fit did not improve results  
  > "fitting an elliptical 2D Gaussian function does not improve the results" (3.1 Continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): [CII] feature only tentative (3 sigma); systemic redshift may not be covered  
  > "It is possible that the systemic redshift of A1689-zD1 may not have been covered by the observations." (4.2 Redshift)
- Limitation (authors): ALMA data quality insufficient to confirm elongated clumps  
  > "however, the ALMA data does not have sufficient quality to further reaffirm this." (3.1 Continuum)
- Caveat (inferred, ours): Tentative [CII] line at 3 sigma was chosen post hoc among several candidates; significance not corrected for trials
- Caveat (inferred, ours): Two-component sizes at ~0.5 arcsec are near resolution limit with low S/N
- Caveat (inferred, ours): Dust temperature from only two bands is degenerate with beta
- Caveat (inferred, ours): Merger probability from abundance matching is only a statistical argument

## Reproducibility

- Data public (paper): ALMA data cited by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01064.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, CASA version)
- Missing: uvmultifit setup
- Missing: SED code configurations
- Missing: GBT raw data processing parameters
- Data volume (inferred): ~20-50 GB raw ALMA (Cycle 2 band 6 and 7 EBs), plus small GBT dataset
- Score (inferred): 3/5, ALMA data identified and pipeline products mostly used, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Imaging and fit setups are underspecified, and key results depend on a tentative line and external SED data.

## Links

- Method: (cite: martividal14) (uvmultifit visibility fitting)
- Method: (cite: dacunha13) (CMB effects on high-z observations)
- Companion: (cite: watson15) (Original dust detection and SED of A1689-zD1)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 45,
  "rate": 0.562
 },
 "evidence_ok": true
}
```
