# Truth or Delusion? A Possible Gravitational Lensing Interpretation of the Ultraluminous Quasar SDSS J010013.02+280225.8 at z = 6.30

`2020ApJ...891...64F` | The Astrophysical Journal 2020 | first author: Fujimoto, Seiji | arXiv: 1909.13512 | DOI: 10.3847/1538-4357/ab718c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Is the resolved quadruple ALMA 1-mm continuum structure of the z=6.30 quasar J0100+2802 due to strong gravitational lensing or to multiple star-forming regions, and how would lensing change its BH mass?  
  > "which can be interpreted as either multiple dusty star-forming regions in the host galaxy or multiple images due to strong gravitational lensing." (abstract)
- Target **SDSS J010013.02+280225.8 (J0100+2802)**: coordinates RA 1:00:13.026, Dec +28:02:25.81 (J2000)  
  > "| Total | 1:00:13.026    | +28:02:25.81   | 1.3                 | 21    |       |" (Table 1); "an ultra-luminous quasar (QSO) at $z=6.30$" (abstract); z/distance z = 6.30  
  > "| Total | 1:00:13.026    | +28:02:25.81   | 1.3                 | 21    |       |" (Table 1); "an ultra-luminous quasar (QSO) at $z=6.30$" (abstract); distance from Wu et al. 2015 (cite: wu2015)  
  > "| Total | 1:00:13.026    | +28:02:25.81   | 1.3                 | 21    |       |" (Table 1); "an ultra-luminous quasar (QSO) at $z=6.30$" (abstract)

## Data provenance

- ALMA projects: 2015.1.00692.S
- bands: Band 6 (~1.25 mm)  
  > "centered at an observed frequency of 239.8 GHz (i.e., $\sim$1.25 mm)" (2 Data & Reduction)
- frequencies and spectral setup: four spectral windows, 7.5 GHz bandwidth, centered at 239.8 GHz  
  > "The available 7.5 GHz bandwidth with four spectral windows was centered at an observed frequency of 239.8 GHz" (2 Data & Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 2.5 km, 44 antennas  
  > "using 44 antennas with the projected baselines ranging from 15 m to 2.5 km" (2 Data & Reduction)
- angular resolution: LR 0.29''x0.15''; MR 0.23''x0.12''; HR 0.21''x0.09''  
  > "whose final synthesized beam sizes are $0.23\ensuremath{''}\times0.12\ensuremath{''}$ and $0.21\ensuremath{''}\times0.09\ensuremath{''}$" (2 Data & Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~74 min  
  > "The total on-source time was $\sim$ 74 min." (2 Data & Reduction)
- observing dates: 2016 September 4  
  > "Observations were carried out on 2016 September 4 in the cycle 4 program" (2 Data & Reduction)
- pi or archival as stated: Cycle 4 program, PI X. Fan (see Wang et al. 2019)  
  > "in the cycle 4 program (PI: X. Fan; see (cite: wang2019))" (2 Data & Reduction)
- Other facility **HST/ACS F850LP**: High-resolution optical map from Hubble Legacy Archive (PI X. Fan)  
  > "we present the HST/F850LP map for J0100+2802 obtained from the final flat-field and flux calibrated science products in the Hubble Legacy Archive (PI: X. Fan)" (3.2 Comparison with HST)
- Other facility **VLT/X-shooter**: Archival optical-NIR spectrum showing Mg II absorption and possible Lya at z=2.33  
  > "latest optical–NIR spectroscopy with VLT/X-shooter from the ESO archive (PI: M. Pettini; see (cite: becker2019))" (3.1 ALMA)
- Other facility **Gaia DR2**: Astrometric correction of HST vs ALMA  
  > "The astrometry between HST and ALMA is corrected based on the GAIA DR2 catalog (cite: gaia2018)." (3.2 Comparison with HST)
- External data: L_bol and M_BH (1.24e10 Msun) of J0100+2802, and absorbers at z=2.33 and 3.34  
  > "the BH mass $M_{\rm BH}$ is evaluated to be 1.24$\,\pm\,0.19\times10^{10}\,M_{\odot}$ via the single-epoch virial $M_{\rm BH}$ estimator" (1 Introduction) [from Wu et al. 2015 (cite: wu2015)]
- External data: Velocity dispersion to stellar mass scaling relation for quiescent galaxies  
  > "from the scaling relation for quiescent galaxies (cite: zahid2016), the velocity dispersion of 121 km s$^{-1}$ corresponds to the $M_{\rm star}$ value" (3.1 ALMA) [from (cite: zahid2016)]

## Processing

### Calibration

- pipeline or manual: Standard reduction with ALMA-provided scripts  
  > "in the standard manner with the scripts provided by the ALMA observatory" (2 Data & Reduction)
- casa version: CASA 4.7.0 for reduction; CASA 5.4.0 for further analysis  
  > "For further data analyses, we use the CASA version 5.4.0." (2 Data & Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2253+1608 and J0238+1636  
  > "J2253+1608 and J0238+1636 were observed as the flux calibrator" (2 Data & Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, line-free channels in all spws  
  > "The continuum images are produced with the line-free channels in all spectral windows by the CLEAN algorithm with the *tclean* task." (2 Data & Reduction)
- deconvolver: _not stated_
- weighting robust: natural (LR); Briggs robust 0.5 (MR); robust 0.2 (HR)  
  > "We refer to the natural-, the briggs- (robust = 0.5), the briggs-weighted (robust = 0.2) maps as “LR”, “MR”, and “HR” maps, respectively." (2 Data & Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CLEAN boxes at peak pixels with S/N>=5 in auto mode; clean to 3 sigma  
  > "The CLEAN boxes are set at the peak pixel positions with S/N $\geq$ 5 in the auto mode, and the CLEAN routines are proceeded down to the 3$\sigma$ level." (2 Data & Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: LR 0.29''x0.15''  
  > "The final natural-weighted image is characterized by a synthesized beam size of $0.29\ensuremath{''}\times0.15\ensuremath{''}$ and the rms noise level of 16 $\mu$Jy/beam." (2 Data & Reduction)
- final rms: 16 (LR), 17 (MR), 20 (HR) uJy/beam  
  > "with the rms noise levels of 17 $\mu$Jy/beam and 20 $\mu$Jy/beam, respectively" (2 Data & Reduction)

### Inherited from earlier work

- MR imaging parameters same as the continuum map of Wang et al. 2019; morphology reproduced  
  > "Note that the imaging parameter of the MR map is the same as the continuum map produced in (cite: wang2019)" (2 Data & Reduction) [from (cite: wang2019)]
- Positional uncertainty formula from ALMA technical handbook  
  > "where $\sigma$ is the peak SNR, $\nu$ is the observing frequency in GHz, and $B$ is the maximum baseline length in kilometers" (3.1 ALMA) [from ALMA technical handbook Section 10.5.2]

### Not stated but needed to reproduce (our reading)

- Spectral window line-free channel selection
- Cell size and image size
- Exact tclean parameters (niter, gain, mask settings)
- glafic fitting setup details and best-fit SIE parameters (other than Einstein radius and e)
- How the 0.8'' aperture flux and peak positions were measured
- Details of simobserve configuration and noise

## Analysis recipe

1. **Image continuum at three weightings**: tclean on line-free channels with natural, Briggs 0.5 and 0.2 weighting  
  > "We also produced a briggs-weighted maps with the robust parameter of 0.5 and 0.2" (2 Data & Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: MR map morphology compared with Wang et al. 2019  
  > "we confirm that the same morphology is reproduced in the MR map as the previous works" (2 Data & Reduction)
2. **Identify components and test for noise/diffuse-emission false peaks**: Four peaks >5 sigma in HR map; 1,000 mock simobserve realisations of uniform diffuse emission  
  > "We repeat from the mock observation to producing the HR map 1,000 times, and identify positive peaks within the radius of $0.2\ensuremath{''}$ from the center of the diffuse emission." (3.1 ALMA)
   - software: CASA simobserve
   - assumption: Uniform diffuse flux 0.7 mJy over 0.8'' diameter  
  > "Here we assume a uniform flux distribution whose total flux is estimated from the resolved, diffuse emission of 0.7 mJy (= 1.3 mJy – 0.6 mJy) with the diameter of $0.8\ensuremath{''}$." (3.1 ALMA)
   - fitting: _not stated_
   - validation: 8/1000 maps contain >5.4 sigma peaks; none >7 sigma  
  > "We find that 8 out of the 1,000 HR maps contain the positive peaks over the 5.4$\sigma$ level" (3.1 ALMA)
3. **Lens mass model fit to four ALMA peaks**: SIE plus external shear fit to peak positions and fluxes; lens at z=2.33  
  > "The mass model consists of a singular isothermal ellipsoid (SIE) and an external shear." (3.1 ALMA)
   - software: glafic
   - parameter: positional error 0.03''; flux error 10%  
  > "The flux errors are assumed to be 10 %." (3.1 ALMA)
   - assumption: Gaussian prior on shear gamma=0.05±0.05; no prior on SIE centroid  
  > "we add a Gaussian prior on the amplitude of the external shear of $\gamma=0.05 \pm 0.05$" (3.1 ALMA)
   - fitting: best-fit chi2/dof = 6.11/3  
  > "we obtain the best-fit mass model with the $\chi^2$ over the degree of freedom of 6.11/3" (3.1 ALMA)
   - validation: Model positions and intrinsic fluxes consistent with observations within errors  
  > "We find that all the four positions are consistent within the errors." (3.1 ALMA)
4. **Test HST single-component morphology with mock PSF injection**: Measure HST PSF from stars; inject three PSFs in 2:1:1 ratio at varying separation l; compare FWHM  
  > "Finally, we measure the FWHM values for the single-like component in the mock HST map as a function of $l$." (3.2 Comparison with HST)
   - software: SExtractor
   - fitting: _not stated_
   - validation: Observed FWHM 0.113'' matches l=0.04''  
  > "We also find that the FWHM of J0100+2802 corresponds to the simulation results with $l=0.''04$." (3.2 Comparison with HST)
5. **Correct M_BH for magnification**: Apply magnification to UV luminosity in Mg II virial estimator  
  > "If we apply the total magnification correction to the UV luminosity in Equation [\[eq:Mbh\]](#eq:Mbh), the intrinsic $M_{\rm BH}$ estimate is decreased by a factor of $\sim$17.3." (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0 (reduction), 5.4.0 (analysis): calibration, tclean imaging, simobserve  
  > "For further data analyses, we use the CASA version 5.4.0." (2 Data & Reduction)
- **glafic** : parametric lens mass modelling  
  > "we construct a mass model with the parametric gravitational lensing package glafic (cite: oguri2010)" (3.1 ALMA)
- **SExtractor** 2.5.0: identify stars and evaluate HST PSF  
  > "we identify isolated and unsaturated stars with SExtractor version 2.5.0 (cite: bertin1996)" (3.2 Comparison with HST)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total continuum flux density (0.8'' aperture) | 1.3 | not stated | mJy | 1 | The total flux density is estimated to be 1.3 mJy with an aperture diameter of $0.8\ensuremath{''}$ |
| Peak significance in LR map | 21 | not stated | sigma | 1 | a continuum emission is clearly detected with the 21$\sigma$ level at the peak |
| Einstein radius | 0.14 | not stated | arcsec | 3 | the Einstein radius is 0.14$''$ which corresponds to the line-of-sight velocity dispersion of the lensing galaxy of 121 km s$^{-1}$ |
| Total ALMA magnification | ~58 (2sigma range 18-117) | 2 sigma range | dimensionless | 3 | The best-fitting mass model predicts the total magnification of $\sim 58$ for the ALMA source |
| Lens ellipticity | 0.14 | ±0.09 | dimensionless | 3 | the ellipticity is not very well constrained in our model with $e=0.14\pm0.09$ ($1\sigma$) |
| HST emission FWHM | 0.113 | not stated | arcsec | 4 | the FWHM for J0100+2802 in the observed HST map that is estimated to be $0.''113$ |
| HST PSF FWHM | 0.103 | ±0.003 | arcsec | 4 | The FWHM of the PSF is estimated to be $0.''103$ $\pm$ $0.''003$ |
| Total magnification of HST emission | ~450 | factor of a few | dimensionless | 5 | our fiducial mass model predicts the total magnification factor of $\sim450$ for the quadruple images in the HST map |
| Mg II absorption redshift | 2.3244 | ±0.0002 | dimensionless | 0 | Mg ii absorption line feature at $z=2.3244\pm0.0002$ |
| Lya velocity offset from Mg II | 810 | ±90 | km/s | 0 | The Ly$\alpha$ velocity offset from the Mg ii absorption is estimated to be $810\pm90$ km s$^{-1}$ |

## Qualitative findings

- A simple SIE+shear lens at z=2.33 reproduces the four ALMA component positions and fluxes; lensing and multiple-star-forming-region interpretations cannot be distinguished yet.  
  > "we cannot draw definitive conclusion between the two possibilities of 1) the quadruply imaged lens system and 2) the multiple dusty star-forming system" (4 Discussion)

## Claim tuples

- H: The four ALMA components are lensed images | E: glafic SIE+shear fit to HR map peaks with lens at z=2.33 | R: chi2/dof 6.11/3; positions and intrinsic fluxes consistent; magnification ~58 | F: Lensing is a viable interpretation | **supported**
- H: An ALMA-HST source-plane offset explains single HST component | E: Caustic analysis and mock HST PSF injection | R: FWHM 0.113'' matches l=0.04''; ~50 pc offset; magnification ~450 | F: Consistent with data | **partially**
- H: Lensing lowers intrinsic M_BH | E: Apply magnification to Mg II virial estimator | R: M_BH decreased by ~17.3, below 1e9 Msun | F: Most massive z>6 BH may be overestimated | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Multiple dusty star-forming regions or a merger in the host galaxy cannot be ruled out  
  > "Note that we cannot rule out the possibility of 2)." (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Lens model poorly constrained; magnification uncertain by a factor of a few  
  > "our estimate of the total magnification factor should be uncertain by a factor of a few or so" (4 Discussion)
- Caveat (inferred, ours): Only 3 degrees of freedom in lens fit, with a high chi2
- Caveat (inferred, ours): Lya line at 5.3 sigma is marginal
- Caveat (inferred, ours): Lens galaxy not directly detected
- Caveat (inferred, ours): AID4 at 5.4 sigma is marginal

## Reproducibility

- Data public (paper): ALMA project 2015.1.00692.S; HST from the Hubble Legacy Archive; X-shooter from the ESO archive  
  > "obtained from the final flat-field and flux calibrated science products in the Hubble Legacy Archive (PI: X. Fan)" (3.2 Comparison with HST)
- Products in archive: _not stated_
- Missing: Full tclean parameters
- Missing: glafic input files
- Missing: Aperture photometry and peak-finding details
- Data volume (inferred): ~20-50 GB raw single-EB Band 6 data
- Score (inferred): 3/5, Public data and named tools, but many imaging and lens-fit details are missing.
- Rediscovery candidate: no, Lens modelling and imaging details are insufficiently specified for a precise reproduction.

## Links

- Method: Oguri 2010 (cite: oguri2010) (glafic lens modelling package)
- Companion: Wang et al. 2019 (cite: wang2019) (Original publication of the same ALMA data)
- Related: SDSS
- Related: 2MASS
- Related: WISE

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 46,
  "rate": 0.622
 },
 "evidence_ok": true
}
```
