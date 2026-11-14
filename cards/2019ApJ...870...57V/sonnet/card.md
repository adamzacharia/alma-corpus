# An Enormous Molecular Gas Flow in the RX J0821+0752 Galaxy Cluster

`2019ApJ...870...57V` | The Astrophysical Journal 2019 | first author: Vantyghem, A. N. | arXiv: 1811.09653 | DOI: 10.3847/1538-4357/aaf1b4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, galaxy_clusters_and_sz
- Question: How did the ~10^10 Msun molecular gas reservoir in the RXJ0821 BCG form, and how is it related to X-ray cavities and ICM sloshing?  
  > "In this work we focus on the morphology and kinematics of the molecular gas, relating it to features in the X-ray image." (Introduction)
- Target **RXJ0821.0+0752 BCG**: coordinates _not stated_; z/distance z=0.11087; D_L=510 Mpc  
  > "At the redshift of RXJ0821 ($z=0.11087$; see Section [2.2.1](#sec:systemic)), the angular scale is $1''=2.0\rm\; kpc$ and the luminosity distance is $510\rm\; Mpc$." (Introduction); distance from systemic redshift from ALMA CO spectra  
  > "At the redshift of RXJ0821 ($z=0.11087$; see Section [2.2.1](#sec:systemic)), the angular scale is $1''=2.0\rm\; kpc$ and the luminosity distance is $510\rm\; Mpc$." (Introduction)

## Data provenance

- ALMA projects: 2016.1.01269.S
- bands: Band 3 (CO 1-0) and Band 7 (CO 3-2)  
  > "fell in Bands 3 and 7, respectively." (2.2 ALMA)
- frequencies and spectral setup: CO(1-0) 103.848 GHz, CO(3-2) 311.528 GHz, 13CO(3-2) 297.827 GHz; remaining basebands for continuum  
  > "The remaining three Band 3 basebands and two Band 7 basebands were used to measure the sub-mm continuum emission." (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 18-1124 m (Band 3); 15-3247 m (Band 7); 40 antennas  
  > "with baselines ranging from $18-1124\rm\; m$ for Band 3 and $15-3247\rm\; m$ for Band 7." (2.2 ALMA)
- angular resolution: 0.61x0.59 arcsec (CO1-0); 0.21x0.165 arcsec (CO3-2)  
  > "had synthesized beams of $0.61''\times 0.59''$ (P.A. $-70.4^{\circ}$) and $0.21''\times 0.165''$ (P.A. $37.2^{\circ}$), respectively." (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.5 and 1.1 mJy/beam in line-free channels  
  > "The RMS noise in the line-free channels were $0.5$ and $1.1\rm\; mJy~{\rm beam}^{-1}$, respectively." (2.2 ALMA)
- time on source: 86.7 min (Band 3); 22.7 min (Band 7)  
  > "(Band 3; 86.7 minutes on source) and Nov 4 and 2016 Oct 1 (Band 7; 22.7 minutes on source)" (2.2 ALMA)
- observing dates: 2016 Oct 30 (Band 3); Nov 4 and Oct 1 2016 (Band 7)  
  > "were conducted on 2016 Oct 30 (Band 3; 86.7 minutes on source)" (2.2 ALMA)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (103.848 GHz (redshifted))
- Line: CO 3-2 (311.528 GHz (redshifted))
- Line: 13CO 3-2 (297.827 GHz (redshifted))
- Other facility **Chandra ACIS-S3**: 63.5 ks X-ray imaging and spectra (ObsIDs 17194, 17563)  
  > "The final exposure time of the cleaned data was 63.5 ks." (2.1 Chandra)
- Other facility **HST F606W**: optical image used for BCG nucleus centroid  
  > "The annuli were centered on the BCG nucleus as determined from the HST F606W image." (3.1)
- External data: XCO = 1.05e20 cm-2 (K km/s)-1 and CO(3-2)/(1-0) flux ratio of 8  
  > "Following V17, CO(3-2) line fluxes have been converted to molecular gas masses by assuming a CO (3-2)/(1-0) flux ratio of $8$." (4.1) [from Vantyghem17]
- External data: Cluster mass profiles used for gravity in buoyancy time  
  > "The acceleration under gravity is determined using the cluster mass profiles from (cite: Hogan17b)." (3.2) [from Hogan17b]
- External data: Galactic NH = 2.01e20 cm-2  
  > "The foreground hydrogen column density was fixed to the Galactic value of $N_H = 2.01\ensuremath{\times 10^{20}}\hbox{$\rm\; cm^{-2}\,$}$ (cite: Kalberla05)." (3.1) [from Kalberla05]

## Processing

### Calibration

- pipeline or manual: CASA pipeline reduction scripts  
  > "The observations were calibrated in casa version 4.7.0 (cite: casa) using the pipeline reduction scripts." (2.2 ALMA)
- casa version: 4.7.0  
  > "calibrated in casa version 4.7.0" (2.2 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: uvcontsub and clean  
  > "Continuum-subtracted data cubes were created using uvcontsub and clean." (2.2 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 2  
  > "Images of the line emission were reconstructed using Briggs weighting with a robust parameter of 2." (2.2 ALMA)
- uv taper: additional taper for CO(3-2), smoothing on scales below 0.1 arcsec  
  > "An additional $uv$ tapering was used to smooth the CO(3-2) image on scales below 0.1 arcsec." (2.2 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.61x0.59 arcsec; 0.21x0.165 arcsec  
  > "The final CO(1-0) and CO(3-2) data cubes had synthesized beams of $0.61''\times 0.59''$ (P.A. $-70.4^{\circ}$)" (2.2 ALMA)
- final rms: 0.5 and 1.1 mJy/beam; 3 and 5 km/s channels  
  > "The CO(1-0) and CO(3-2) images were binned to $3$ and $5\hbox{$\rm\; km\rm\; s^{-1}\,$}$ velocity channels, respectively." (2.2 ALMA)

### Inherited from earlier work

- ALMA observations and reduction described in detail elsewhere  
  > "The ALMA observations of RXJ0821+0752 are described in detail in V17." (2.2 ALMA) [from Vantyghem17]
- CO(3-2)/(1-0) ratio of 8 and sub-Galactic XCO  
  > "Following V17, CO(3-2) line fluxes have been converted to molecular gas masses by assuming a CO (3-2)/(1-0) flux ratio of $8$." (4.1) [from Vantyghem17]
- Cooling radius defined where tcool < 5 Gyr  
  > "Following (cite: McDonald10), we define the cooling radius, $r_{\rm cool}$, as the radius where the cooling time falls below $5\rm\; Gyr$." (3.3) [from McDonald10]

### Not stated but needed to reproduce (our reading)

- Channels used for continuum fitting in uvcontsub
- clean threshold, mask, cell and image size
- Flux calibrator and flux-scale uncertainty
- Pixel-fit Gaussian priors/initial guesses and Monte Carlo procedure details
- Cavity ellipse region coordinates
- Continuum image weighting/robust

## Analysis recipe

1. **Reduce Chandra data and make X-ray image**: Reprocess with ciao, clean flares with lc_clean, sum 0.5-7 keV events, remove point sources with wavdetect, blank-sky background  
  > "Point sources were identified and removed using wavdetect and confirmed via visual inspection." (2.1 Chandra)
   - software: ciao, wavdetect, lc_clean
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive ICM radial profiles**: Deprojected spectra in eight annuli fit with phabs x apec; derive density, pressure, entropy, cooling time  
  > "The projected and deprojected spectra were both fit by a single temperature thermal model with photoelectric absorption, phabs$\times$apec." (3.1)
   - software: xspec, dsdeproj
   - parameter: min 2500 net counts per annulus; C-stat for projected, chi2 with 25 counts/bin for deprojected  
  > "Each region had a minimum of 2500 net counts." (3.1)
   - assumption: nH = ne/1.2; NH fixed to Galactic; Anders & Grevesse abundances  
  > "and $n_H=n_e/1.2$ is assumed to be constant within each annulus." (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Cavity energetics**: Ellipse fit to depression; E=4pV; age from buoyant rise and sound crossing time  
  > "The enthalpy required to inflate the cavity is given by $E_{\rm cav}=4pV$" (3.2)
   - parameter: drag coefficient C=0.75; efficiency 0.1  
  > "Here $C=0.75$ is the drag coefficient (cite: Churazov01)" (3.2)
   - assumption: line-of-sight size sqrt(ab); pressure balance with surroundings  
  > "The cavity volume was computed by assuming that its size along the line-of-sight is given by the geometric mean of the semi-major and semi-minor axes" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Cooling flow mass deposition rate**: Add mkcflow component within r_cool=50 kpc, Tmin 0.1 keV  
  > "we added an mkcflow component to the previous thermal model." (3.3)
   - software: xspec
   - fitting: _not stated_
   - validation: _not stated_
5. **Map CO flux, velocity, FWHM**: Fit up to two Gaussians per pixel (beam-size averaging), 3 sigma detection, Monte Carlo significance test  
  > "Up to two Gaussian components, representing multiple coincident velocity structures, were used to model each pixel’s spectrum." (4)
   - parameter: at least 2500 Monte Carlo iterations  
  > "The significance of each velocity component was tested using a Monte Carlo analysis with at least 2500 iterations." (4)
   - fitting: _not stated_
   - validation: _not stated_
6. **Molecular gas mass**: Mmol from CO(1-0) flux with sub-Galactic XCO; CO(3-2) scaled by ratio 8  
  > "We have adopted this sub-Galactic value throughout this paper." (4.1)
   - assumption: XCO = 1.05e20, half Galactic  
  > "This is half the Galactic value." (4.1)
   - fitting: _not stated_
   - validation: _not stated_
7. **Continuum flux in clumps**: Box fluxes grown until S/N 1.5 in regions A and B  
  > "Each box was centered on the source and grown until the signal-to-noise fell to $1.5$." (5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: calibration and imaging  
  > "calibrated in casa version 4.7.0" (2.2 ALMA)
- **ciao** 4.5: Chandra reprocessing  
  > "reprocessed using ciao version 4.5 and caldb version 4.6.7" (2.1 Chandra)
- **xspec** 12.7.1: X-ray spectral fitting  
  > "performed using xspec v12.7.1" (3.1)
- **dsdeproj** : spectral deprojection  
  > "Spectral deprojection was performed using the geometric method dsdeproj" (3.1)
- **Astropy** : general analysis  
  > "This research made use of Astropy" (Acknowledgments)
- **APLpy** : plotting  
  > "This research made use of APLpy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular gas mass | 1.07e10 | 0.02e10 | Msun | 6 | the molecular gas mass is $(1.07\pm0.02)\ensuremath{\times 10^{10}}\hbox{$\rm\thinspace M_{\odot}$}$. |
| Total CO(1-0) flux | 8.06 | 0.08 | Jy km/s | 5 | $8.06\pm0.08$ and $65.6\pm1.5\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$ |
| Total CO(3-2) flux | 65.6 | 1.5 | Jy km/s | 5 | $8.06\pm0.08$ and $65.6\pm1.5\hbox{$\rm\; Jy\rm\; km\rm\; s^{-1}\,$}$ |
| Cavity power | 1.3e43 | not stated | erg/s | 3 | $P_{\rm cav}$ / $1.3\ensuremath{\times 10^{43}}\hbox{$\rm\; erg\rm\; s^{-1}\,$}$ |
| Cavity enthalpy 4pV | 4.2e57 | not stated | erg | 3 | $4pV$ / $4.2\ensuremath{\times 10^{57}}\rm\; erg$ |
| Mass deposition rate within 50 kpc | 34 | 10 | Msun/yr | 4 | The best-fitting mass deposition rate is $\dot{M}_{\rm cool} = 34\pm10\hbox{$\hbox{$\rm\thinspace M_{\odot}$}\rm\; yr^{-1}\,$}$ |
| Systemic redshift | 0.11087 | 0.00004 | dimensionless | 5 | we adopt a systemic redshift of $z=0.11087\pm0.00004$ |
| Hot gas displaced by cavity | 2.4e8 (Table: 2.3e8) | not stated | Msun | 3 | A total of $2.4\ensuremath{\times 10^{8}}\hbox{$\rm\thinspace M_{\odot}$}$ of hot gas has been displaced in inflating the X-ray cavity. |

## Qualitative findings

- All CO emission lies kpc away from the nucleus in two clumps with a diffuse envelope along an X-ray plume  
  > "All of the CO line emission, originating from a $10^{10}\,M_{\odot}$ molecular gas reservoir, is located several kpc away from the nucleus of the central galaxy." (abstract)

## Claim tuples

- H: Stimulated cooling by cavity uplift formed the molecular gas | E: Compare mass of ICM displaced by the X-ray cavity to molecular mass | R: Displaced 2.4e8 Msun, about 40 times smaller than molecular gas mass | F: Cavity uplift can lift only a few percent of the gas | **refuted**
- H: Sloshing induced by a nearby galaxy triggered condensation | E: Compare offsets of X-ray peak, BCG, molecular gas and nearby galaxy | R: Mutual offsets and coincidence with X-ray plume | F: Sloshing is argued to be the mechanism | **partially**
- H: A merger donated or displaced the gas | E: Estimate gas masses of the nearby galaxy and velocities | R: Insufficient gas and low relative velocity | F: Merger origin not well motivated | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Merger donation/displacement and cavity uplift rejected  
  > "While uplift behind X-ray cavities is a promising cold gas formation mechanism in other BCGs, it fails here." (6.2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Cavity is putative; no radio image  
  > "Without an image of the radio source we cannot conclusively determine if this feature is an X-ray cavity." (3.2)
- Limitation (authors): XCO systematically uncertain  
  > "However, significant systematic uncertainties were unavoidable in the V17 analysis." (4.1)
- Caveat (inferred, ours): Sloshing conclusion is qualitative with no simulation
- Caveat (inferred, ours): Cavity is uncertain so displaced mass argument is soft
- Caveat (inferred, ours): Systemic velocity from gas only

## Reproducibility

- Data public (paper): ALMA project cited by ID; archive availability implied  
  > "This paper makes use of the ALMA data ADS/JAO.ALMA 2016.1.01269.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters and masks
- Missing: line-free channels
- Missing: pixel-fit details
- Data volume (inferred): ~50-100 GB raw ALMA plus Chandra ~ few GB
- Score (inferred): 3/5, Public data and many formulas given, but imaging parameters and fitting details are sparse or inherited.
- Rediscovery candidate: yes, Public data and clear numeric targets (gas mass, fluxes) though imaging details missing.

## Links

- Method: Vantyghem17 (Original ALMA data description and XCO)
- Companion: Vantyghem17 (First presentation of same ALMA data)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 88,
  "stated": 49,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
