# ALMA imprint of intergalactic dark structures in the gravitational lens SDP.81

`2016MNRAS.457.2936I` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Inoue, Kaiki Taro | arXiv: 1510.00150 | DOI: 10.1093/mnras/stw168

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, cosmology
- Question: Whether anomalous flux ratios and astrometric shifts in the lensed images of SDP.81 reveal perturbations from intergalactic dark structures along the line of sight  
  > "we report our analysis of the ALMA long baseline science verification data of SDP.81 (used by the authors previously mentioned) to investigate possible gravitational perturbations by dark (sub-)structures along the line of sight" (Introduction)
- Target **SDP.81 (H-ATLAS J090311.6+003906)**: coordinates _not stated_; z/distance source z=3.042; lens z=0.2999  
  > "The source is an SMG at $z=3.042$ (cite: negrello2010) and the primary lens is a massive elliptical galaxy at $z=0.2999$ (cite: negrello2014)." (Introduction); distance from negrello2010; negrello2014  
  > "The source is an SMG at $z=3.042$ (cite: negrello2010) and the primary lens is a massive elliptical galaxy at $z=0.2999$ (cite: negrello2014)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00016.SV
- bands: Band 4 (151 GHz), 6 (235 GHz), 7 (290 GHz); bands 6 and 7 continuum and CO(8-7) used  
  > "SDP.81 was observed in 2014 October as part of the Long Baseline Campaign at band 4(151 GHz), 6(235 GHz) and 7(290 GHz)." (2 DATA)
- frequencies and spectral setup: CO(8-7) channels 21.0 km/s wide; channels 47-52 used  
  > "The CO data were binned spectrally into channels with 21.0 $\textrm{km}\, \textrm{s}^{-1}$ wide." (2 DATA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 7 continuum beam 31x23 mas (PA 16 deg); CO(8-7) tapered beam 169x117 mas (PA 47 deg)  
  > "are $31\times 23\,$mas (PA$=16^\circ$) and $169 \times 117\,$mas (PA$=47^\circ$), respectively." (2 DATA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014 October  
  > "SDP.81 was observed in 2014 October as part of the Long Baseline Campaign" (2 DATA)
- pi or archival as stated: _not stated_
- Line: CO 8-7 (228.055 GHz (observed))
- External data: Semi-linear inversion lens model parameters used for comparison and a third inversion model  
  > "The differences between the "concordant" parameters and those in (cite: dye2015), which uses a semi-linear inversion method" (4.1 Best-fitted Model) [from (cite: dye2015)]
- External data: Fitting formula for p(eta) and constant-shift filter W_CS(k)  
  > "Using so called the "constant shift" filtering function $W_{CS}(k)$ (cite: takahashi-inoue2014)" (5.1 Semi-analytic Estimate) [from (cite: takahashi-inoue2014)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Processed archival science-verification images used  
  > "We used the processed archival images of the band 6 and 7 continuums and the CO(8-7) line, whose calibration and imaging were carried out using the Common Astronomy Software Applications (CASA)" (2 DATA)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 1 (Briggs), CLEAN  
  > "The images were processed using the CLEAN algorithm with a $robust=1$ weighting (Briggs weighting) of the visibilities." (2 DATA)
- uv taper: CO(8-7): 1000 kλ taper to ~170 mas; continuum untapered  
  > "the CO(8-7) images with $uv$-tapering (1000k$\lambda$) to a resolution of $\sim 170\,$mas" (2 DATA)
- cell size: 0.005 arcsec (continuum), 0.02 arcsec (CO)  
  > "The pixel sizes are $0.005$ and $0.02$ arcsec, respectively." (2 DATA)
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

- Data processing and archive images as described in the science verification paper  
  > "(see (cite: vlahakis2015) for detail)" (2 DATA) [from (cite: vlahakis2015)]
- Semi-analytic magnification perturbation method  
  > "For detail, see (cite: inoue-takahashi2012; takahashi-inoue2014)." (5 Perturbation by Intergalactic Structures) [from (cite: inoue-takahashi2012; takahashi-inoue2014)]

### Not stated but needed to reproduce (our reading)

- Own lens-fitting code not released; optimizer details missing
- Exact pixel coordinates of the clump peaks used as fit positions
- Image-plane CLEAN products' exact archive file names
- Channel velocity-to-index mapping and noise rms per channel
- Aperture centres in the source plane
- Details of CASA version used for archive images

## Analysis recipe

1. **Fit SIE+external shear lens model**: Simultaneous chi^2 fit of positions of bright clump peaks (S/N>~10) and the lens galaxy AGN centroid in band 7 continuum  
  > "In order to implement the simultaneous $\chi^2$ fitting of the positions of the centroids of lensed images and the lensing galaxy, we used our developed code." (3.1 Canonical Lens Model)
   - software: in-house code, GRAVLENS
   - parameter: position errors 1/4 of beam (6x8 mas); G error 0.02 arcsec  
  > "the 1$\,\sigma$ errors are 1/4 of $\theta_{\textrm{beam}}$, i.e., $6 \times 8$ mas with the same PA direction." (3.3 Modelling)
   - assumption: SIE plus external shear  
  > "we adopt a singular isothermal ellipsoid (SIE) (cite: kormann1994)" (3.1 Canonical Lens Model)
   - fitting: chi^2 minimization; 1 sigma from parameter range with reduced chi^2 < 1  
  > "The 1 $\sigma$ uncertainty in the model parameters are obtained by finding a range of each parameter that gives the reduced $\chi^2$ less than 1." (4.1 Best-fitted Model)
   - validation: Code compared with GRAVLENS, chi^2 within a few percent; compared with literature models  
  > "The obtained $\chi^2$ values are consistent each other within a few percent." (3.1 Canonical Lens Model)
2. **Measure source-plane aperture flux ratios**: Invert images to source plane, uniform/magnification weighted combination, compute aperture fluxes of B,C,D relative to A; errors from Monte Carlo of 100 random points in noise ring  
  > "First, we randomly selected 100 points within a ring region with an angular distance $R$ from the centre of the lens satisfying $3.5<R<4.3$ arcsec." (4.2 Flux in Aperture)
   - parameter: aperture radii 0.04, 0.05, 0.06 arcsec  
  > "computed the fluxes in circles with aperture radius $0.04,0.05,0.06$ arcsec" (4.2 Flux in Aperture)
   - fitting: _not stated_
   - validation: Hypothetical observation with beam convolution gives <4% error  
  > "We have found that the errors in the aperture flux ratios are less than 4 percent." (4.2 Flux in Aperture)
3. **Find astrometric shifts in CO(8-7)**: Reconstruct source images per channel from A+D and B+C with best-fit band 7 model and compare difference  
  > "we plot the difference in the surface brightness between the inverted image reconstructed from B and C images (B+C) and that from of A and D images (A+D)" (4.3 Astrometric Shift)
   - fitting: _not stated_
   - validation: Positional uncertainty ~0.01 arcsec from S/N~8 compared with observed shift  
  > "equation ([\[accuracy\]](#accuracy)) gives the expected positional uncertainty $\sim 0.01$ arcsec." (4.3 Astrometric Shift)
4. **Compare with theory and toy clump model**: Semi-analytic eta statistic with W_CS filter and p(eta); compensated homogeneous spherical clump added to SIEES by trial and error  
  > "After some trial and errors, we found a set of parameters that can explain the both anomalous features (Table 5)." (5.2 Homogeneous Spherical Clump)
   - assumption: Planck+WMAP cosmology, H0=67.3  
  > "a Hubble constant $H_0=67.3\, \textrm{km}\,\textrm{s}^{-1} \textrm{Mpc}^{-1}$" (Introduction)
   - fitting: _not stated_
   - validation: Clump model brings aperture ratios to within 0.5-1.5 sigma of 1  
  > "the aperture flux ratios are consistent with being equal to 1 at the $0.5\,\sigma -1.5\,\sigma$ level" (5.2 Homogeneous Spherical Clump)

## Software

- **CASA** : Calibration and imaging of archival images  
  > "calibration and imaging were carried out using the Common Astronomy Software Applications (CASA)" (2 DATA)
- **GRAVLENS** : Check of own lens fitting code  
  > "We checked the accuracy of our code by comparing it with other numerical codes such as GRAVLENS" (3.1 Canonical Lens Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Reduced chi^2 of best-fit SIEES | 0.22 (0.647/(16-13)) | not stated | dimensionless | 1 | the reduced $\chi^2$ ($=\chi^2$/dof) is $0.647/(16-13)=0.22$ |
| Einstein radius b | 1.605 | +0.030/-0.004 | arcsec | 1 | $1.605^{+0.030}_{-0.004}$ |
| Aperture flux ratio B/A (best-fit, 0.06 arcsec) | 0.820 | 0.062 | dimensionless | 2 | ratio / 0.820 / 0.801 / 0.945 |
| Aperture flux ratio C/A (best-fit, 0.06 arcsec) | 0.801 | 0.060 | dimensionless | 2 | ratio / 0.820 / 0.801 / 0.945 |
| Clump mass inside R+ | 2.66e9 | not stated | Msun/h | 4 | The mass inside $R_+=3.47
\textrm{kpc} h^{-1}$ is $2.66 \times 10^9 M_{\odot}h^{-1}$ |
| Mean surface mass density of clump | 6.76e8 | not stated | Msun/h arcsec^-2 | 4 | the mean surface mass density inside $R_+$ is $6.76\times 10^8 M_{\odot}h^{-1} \textrm{arcsec}^{-2}$ |

## Qualitative findings

- Image B (positive parity) is demagnified, which positive-density subhaloes cannot explain; a negative-density line-of-sight structure can  
  > "However, our result indicates that image B is *demagnified* in comparison with the prediction of a best-fitted model with a smooth potential." (4.2 Flux in Aperture)

## Claim tuples

- H: Band 7 aperture flux ratios deviate from unity | E: Source-plane aperture fluxes with SIEES models | R: B/A and C/A ~0.8-0.9, 2-3 sigma deviation | F: Flux ratios of B and C are perturbed by 10-20 percent | **partially**
- H: Astrometric shifts exist near the caustic | E: Source reconstruction from CO(8-7) channels | R: Asymmetric feature >~3 sigma at channel 50 | F: Shifts of order 0.01 arcsec imprint | **partially**
- H: Line-of-sight dark structures explain the anomalies | E: Semi-analytic eta and compensated clump model | R: Clump with mean surface density ~1e8 can explain both | F: Intergalactic dark structures consistent with data | **supported**

## Reasoning

- Why this data: Lensed SMGs are ideal targets as redshifts are biased at z=2-3 and ALMA gives high resolution  
  > "strongly lensed submillimetre galaxies (SMGs) are ideal targets as their redshifts are biased at $z=$2-3" (Introduction)
- Why this method: _not stated_
- Alternative: Subhaloes in the lens galaxy cannot easily explain B demagnification  
  > "The feature may be a problem if one tries to explain the anomaly by putting a single subhalo in the lensing galaxy." (4.2 Flux in Aperture)
- How they decided it was enough: _not stated_
- Limitation (authors): Canonical lens model may be too simple; core, power-law deviation, multipoles could explain anomalies  
  > "The canonical lens model that we have considered may have been too simple." (6 Conclusion and Discussion)
- Limitation (authors): No optimal solution for convergence and shear perturbation  
  > "We have not obtained an optimal solution for the perturbation of convergence and shear." (6 Conclusion and Discussion)
- Caveat (inferred, ours): Fits only use CLEANed image peaks, not visibilities; no proper error model
- Caveat (inferred, ours): Reduced chi^2 of 0.22 with dof 3 indicates overfitting and weak constraints
- Caveat (inferred, ours): Clump parameters tuned by hand, no posterior or significance of the model
- Caveat (inferred, ours): Significance 2-3 sigma only and sensitive to lens model choice
- Caveat (inferred, ours): Single-channel astrometric feature of modest S/N

## Reproducibility

- Data public (paper): Science verification data from ALMA Science Portal  
  > "We used the ALMA science verification data on SDP.81 taken from the ALMA Science Portal" (2 DATA)
- Products in archive: _not stated_
- Missing: Lens fitting and source reconstruction code not released
- Missing: Aperture centres and exact peak positions
- Missing: Optimizer settings
- Data volume (inferred): ~ few GB (processed images only)
- Score (inferred): 3/5, Public processed images and clear method outline, but custom unreleased code and hand-tuned clump parameters.
- Rediscovery candidate: no, Key analysis depends on unreleased code and manual tuning, though data are public.

## Links

- Method: (cite: inoue-takahashi2012) (Eta statistic and semi-analytic perturbation method)
- Method: (cite: takahashi-inoue2014) (Filtering function and p(eta) fitting formula)
- Companion: (cite: vlahakis2015) (ALMA SDP.81 science verification data description)
- Companion: (cite: dye2015) (Semi-linear inversion lens model)
- Related: ALMA Long Baseline Campaign

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 36,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
