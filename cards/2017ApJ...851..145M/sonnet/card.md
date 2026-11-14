# ALMA Reveals Metals yet No Dust within Multiple Components in CR7

`2017ApJ...851..145M` | The Astrophysical Journal 2017 | first author: Matthee, J. | arXiv: 1709.06569 | DOI: 10.3847/1538-4357/aa9931

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Are there metals and dust in CR7 (z=6.6 Lyα emitter), and do metallicity and dust content vary between its UV clumps?  
  > "In this paper, we answer to the question of the presence of metals in CR7, and test whether the metallicity and dust content varies between different UV components." (Introduction)
- Target **CR7 (COSMOS Redshift 7)**: coordinates 10:00:58.00 +01:48:15.3 (J2000)  
  > "We observed CR7 (10:00:58.00 +01:48:15.3, J2000) in band 6 with ALMA during cycle 3" (2.1 Observations & data reduction); "is also spectroscopically confirmed at $z_{\rm Ly\alpha}=6.604$" (2 UV properties of CR7); z/distance z_Lya = 6.604; [CII] z = 6.600  
  > "We observed CR7 (10:00:58.00 +01:48:15.3, J2000) in band 6 with ALMA during cycle 3" (2.1 Observations & data reduction); "is also spectroscopically confirmed at $z_{\rm Ly\alpha}=6.604$" (2 UV properties of CR7); distance from Lyα spectroscopic redshift (Sobral2015); [CII] fit in this paper  
  > "We observed CR7 (10:00:58.00 +01:48:15.3, J2000) in band 6 with ALMA during cycle 3" (2.1 Observations & data reduction); "is also spectroscopically confirmed at $z_{\rm Ly\alpha}=6.604$" (2 UV properties of CR7)

## Data provenance

- ALMA projects: 2015.1.00122.S
- bands: Band 6  
  > "We observed CR7 (10:00:58.00 +01:48:15.3, J2000) in band 6 with ALMA during cycle 3" (2.1 Observations & data reduction)
- frequencies and spectral setup: 4 spectral windows centred at 249.94592, 247.94636, 234.94917, 232.9496 GHz, 1875 MHz bandwidth each; 19.4 km/s native resolution  
  > "We observed in four spectral windows centred at 249.94592, 247.94636, 234.94917 and 232.9496 GHz with a bandwidth of 1875 MHz" (2.1 Observations & data reduction); "with a velocity resolution of 19.4 km s$^{-1}$" (2.1 Observations & data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-4  
  > "with configuration C43-4, aimed to achieve a 0.3$''$ angular resolution" (2.1 Observations & data reduction)
- baselines: _not stated_
- angular resolution: beam 0.82x0.77'' FWHM, PA -49.5 deg (after 0.7'' taper)  
  > "$0.82\times0.77''$ FWHM), with a position angle of $-49.5 \degree$" (2.1 Observations & data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.06 mJy/beam per 38.8 km/s channel; continuum rms 7 uJy/beam  
  > "results in rms=0.06 mJy beam$^{-1}$ in 38.8 km s$^{-1}$ channels" (2.1 Observations & data reduction); "we measure an rms of 7 $\mu$Jy beam$^{-1}$ at $\lambda_0 \approx 160 \mu$m" (4.2 Upper limits for CR7)
- time on source: 6.0 h, 35-43 antennas  
  > "The target has been observed with between 35-43 antennas for a total on source integration time of 6.0h" (2.1 Observations & data reduction)
- observing dates: 22, 23, 24 May and 4, 8 November 2016  
  > "on 22, 23, 24 May and 4, 8 November 2016" (2.1 Observations & data reduction)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (nu(z=6.604) = 249.9395 GHz observed)
- Other facility **HST/WFC3**: Near-IR imaging of UV clumps (photometry from Bowler2016)  
  > "The latest photometry on the *HST*/WFC3 imaging in the F110W and F160W filters has been performed by (cite: Bowler2016)." (2 UV properties of CR7)
- Other facility **Subaru/Suprime-Cam**: NB921 and z' imaging for Lyα flux  
  > "we first correct the Subaru/S-Cam NB921 image for the contribution from the UV continuum by subtracting the $z'$ image" (2 UV properties of CR7)
- Other facility **VLT/X-SHOOTER**: Lyα profile at clump A  
  > "compare these to the Ly$\alpha$ profile measured with VLT/X-SHOOTER at the peak of Ly$\alpha$ emission" (3.2.1 Measurements of individual clumps)
- External data: HST F110W/F160W photometry of clumps A, B, C  
  > "The latest photometry on the *HST*/WFC3 imaging in the F110W and F160W filters has been performed by (cite: Bowler2016)." (2 UV properties of CR7) [from (cite: Bowler2016)]
- External data: COSMOS2015 catalog IDs/photo-z of foreground galaxies  
  > "associated with ID number 339509 in the catalog from (cite: Laigle2016), photo$-z=0.84$" (4.1 Blind detections) [from (cite: Laigle2016)]
- External data: Literature [CII]/SFR/UV-slope samples and local SFR-L[CII] relation  
  > "we show how our [Cii] measurements of the UV components of CR7, their sum, and the integrated CR7 measurements compare to samples at $z\sim5-7$ and to the local relation." (5 The SFR-L[CII] relation) [from (cite: DeLooze2014); (cite: Barisic2017)]
- Simulation/model as data: Vallini2015 model of [CII] strength vs metallicity used to infer Z/Zsun  
  > "the dotted lines illustrate how the [Cii] strength changes with metallicity in the model from (cite: Vallini2015)" (5 The SFR-L[CII] relation)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.0  
  > "Data have been reduced using Casa version 4.7.0" (2.1 Observations & data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1058+0133 (bandpass and flux); phase calibrator J0948+0022  
  > "The quasar J1058+0133 has been observed regularly as a bandpass and flux calibrator" (2.1 Observations & data reduction)
- flux scale uncertainty: ~10 %  
  > "resulting in typical flux calibration errors of $\sim10$ %" (2.1 Observations & data reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with natural weighting and channel averaging resulting in a 38.8 km s$^{-1}$ velocity resolution" (2.1 Observations & data reduction)
- uv taper: Gaussian FWHM=0.7''; tested 0.4-0.8''  
  > "We use uv tapering of the visibilities with a Gaussian width FWHM=0.7$''$ to optimise the S/N ratio." (2.1 Observations & data reduction)
- cell size: _not stated_
- image size: 51.2'' x 51.2'' collapsed images  
  > "which has a size of $51.2''\times51.2''$, centred on CR7" (2.3 Line-sensitivity measurements)
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

- IR luminosity upper limit conversion (T=35 K modified blackbody, Wien slope 2.9, beta_IR=1.5, CMB removal)  
  > "We follow (cite: Schaerer2015) to convert this limit into a 3$\sigma$ upper limit on the infrared luminosity" (4.2 Upper limits for CR7) [from (cite: Schaerer2015); (cite: daCunha2013)]
- Dust mass method and absorption coefficient  
  > "We follow the method outlined in (cite: Ota2014), which assumes a dust mass absorption coefficient" (4.2 Upper limits for CR7) [from (cite: Ota2014)]
- Dynamical mass formula  
  > "Dynamical masses are computed following (cite: Wang2013)" (3.3 Sizes and dynamical masses) [from (cite: Wang2013)]
- SFR_IR from IR luminosity  
  > "Following the prescription from (cite: Kennicutt1998), we measure a 3$\sigma$ upper limit of the dust obscured SFR$_{\rm IR} < 5.4$" (4.2 Upper limits for CR7) [from (cite: Kennicutt1998)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction (none applied to [CII]; the continuum image includes the line)
- Cleaning parameters (deconvolver, threshold, masks, cell size) for tclean
- Exact velocity range/channel selection for the collapsed images and velocity slices
- Conversion constants for UV SFR (UV luminosity to SFR calibration)
- Whether archive pipeline or manual calibration was used
- The Lyα redshift reference used for velocity zero point

## Analysis recipe

1. **Reduce and image ALMA data**: CASA reduction, natural weighting, channel averaging to 38.8 km/s, uv taper 0.7''  
  > "Data have been reduced using Casa version 4.7.0 (cite: McMullin2007) with natural weighting and channel averaging resulting in a 38.8 km s$^{-1}$ velocity resolution." (2.1 Observations & data reduction)
   - software: CASA
   - parameter: taper FWHM 0.7''  
  > "We use uv tapering of the visibilities with a Gaussian width FWHM=0.7$''$ to optimise the S/N ratio." (2.1 Observations & data reduction)
   - fitting: _not stated_
   - validation: Repeated with tapers 0.4-0.8''; results consistent within errors  
  > "but find that all changes in luminosity, line-width and size measurements are consistent within the error-bars." (2.1 Observations & data reduction)
2. **Astrometric alignment to HST**: Shift ALMA by 0.25'' west to align [CII] clumps with UV clumps A and B; consistent with foreground continuum sources  
  > "we align the ALMA data with *HST* and Subaru narrow-band data by applying an offset of 0.25$''$ to the west" (2.2 Astrometry)
   - assumption: Offset is due to astrometry errors, not physical  
  > "we assume that the offsets between the UV positions and [Cii] positions are due to errors in the astrometry" (2.2 Astrometry)
   - fitting: _not stated_
   - validation: Positions of two foreground continuum detections agree with offset  
  > "We note that the positions of two serendipitous IR continuum-detections of foreground galaxies are also in agreement with this offset" (2.2 Astrometry)
3. **Noise and significance estimation**: Integrate flux in 100,000 random circular apertures on collapsed image, r=0.35''  
  > "We place circular apertures on 100,000 random positions on the image and integrate the flux over the scales confined by these apertures." (2.3 Line-sensitivity measurements)
   - parameter: 1 sigma = 16.9 mJy/beam km/s for beam-sized apertures  
  > "which results in 16.9 mJy beam$^{-1}$ km s$^{-1}$ for beam-sized apertures on the collapsed image" (2.3 Line-sensitivity measurements)
   - fitting: _not stated_
   - validation: Distribution of random-aperture fluxes approximately Gaussian  
  > "the distribution of fluxes measured on random positions approximately follows a gaussian" (2.3 Line-sensitivity measurements)
4. **Measure [CII] luminosities and line profiles of clumps**: Aperture photometry (0.35'' radius; 0.55'' for A, 0.50'' for C-2) and Gaussian line fits; L_CII from Solomon/Carilli-Walter formula  
  > "For clumps A and C-2, we use 0.55$''$ and 0.50$''$ apertures respectively to account for the fact that these sources are slightly extended." (3.2.1 Measurements of individual clumps)
   - parameter: L_CII/Lsun = 1.04e-3 x S dv x nu_obs x D_L^2, D_L = 64457.8 Mpc  
  > "luminosity distance in Mpc (64457.8 Mpc at $z=6.60$)" (2.3 Line-sensitivity measurements)
   - assumption: LCDM with Om=0.70, OL=0.30, H0=70  
  > "we assume a $\Lambda$CDM cosmology with $\Omega_M = 0.70$, $\Omega_{\Lambda} = 0.30$ and H$_0 = 70$ km s$^{-1}$ Mpc$^{-1}$" (1 Introduction)
   - fitting: Gaussian profile fits for velocity offset, width, amplitude  
  > "We measure the velocity offset between [Cii] and Ly$\alpha$ and the [Cii] line-width and amplitude by fitting gaussian profiles." (3.2.1 Measurements of individual clumps)
   - validation: Errors from random apertures with same geometry  
  > "This error has been estimated by measuring the flux in randomly located apertures with the same geometry as the 3$\sigma$ contours." (3.1 Total luminosity)
5. **Sizes and dynamical masses**: 2D Gaussian fits with fixed beam shape and positions, noise added from random cutouts, 5000 repeats; deconvolve; M_dyn formula  
  > "This is repeated 5000 times in order to estimate the statistical reliability of the fit." (3.3 Sizes and dynamical masses)
   - parameter: M_dyn/Msun (sin i)^2 = 1.94e5 v_FWHM^2 r_1/2  
  > "\rm M_{\rm dyn} /M_{\odot} (\sin {\it i})^2 = 1.94\times10^5 \times v_{\rm FWHM, [CII]}^2 \times  r_{1/2,\rm [CII]}" (3.3 Sizes and dynamical masses)
   - assumption: Not corrected for inclination  
  > "This results in dynamical masses (uncorrected for inclination)" (3.3 Sizes and dynamical masses)
   - fitting: Free parameters: amplitudes and widths  
  > "Hence, the free parameters are the amplitudes and widths of the gaussian profiles." (3.3 Sizes and dynamical masses)
   - validation: _not stated_
6. **UV slopes and UV SFRs**: Correct F110W for Lyα, compute beta, SFR_UV with Meurer1999 attenuation, 10,000 Monte Carlo perturbations  
  > "We take the measurement uncertainties in the rest-UV magnitudes into account by perturbing these values 10,000 times" (2 UV properties of CR7)
   - assumption: Salpeter IMF 0.1-100 Msun; Meurer attenuation law  
  > "assume a (cite: Salpeter1995) initial mass function (IMF) with mass limits $0.1$ M$_{\odot}$ and $100$ M$_{\odot}$" (1 Introduction)
   - fitting: _not stated_
   - validation: SMC-like law would change results only marginally  
  > "our final results would also only change marginally if an SMC-like attenuation law is used" (2 UV properties of CR7)
7. **IR continuum limits, dust mass and SFR_IR**: 3 sigma limit from 7 uJy/beam rms; modified blackbody at T_d=35 K (also 25, 45 K); dust mass with kappa=1.875(nu/239.84)^beta m2/kg; Kennicutt SFR_IR  
  > "under the assumption that the dust temperature is 35 K and a modified black body SED with a power-law slope of $2.9$ in the Wien regime, $\beta_{\rm IR} = 1.5$" (4.2 Upper limits for CR7)
   - parameter: T_d = 35 K, beta_IR = 1.5  
  > "under the assumption that the dust temperature is 35 K" (4.2 Upper limits for CR7)
   - assumption: CMB contribution removed; [CII] line contamination negligible  
  > "Note that we do not remove contamination from the [Cii] line as we expect that this is negligible" (4.2 Upper limits for CR7)
   - fitting: _not stated_
   - validation: _not stated_
8. **Combine UV and IR for SFR_UV+IR**: Require dust-corrected minus dust-free SFR < 5.4 Msun/yr in each of 10,000 realisations  
  > "constraining that the difference between dust-corrected SFR and dust-free SFR is $<5.4$ M$_{\odot}$ yr$^{-1}$ in each of the 10,000 realisations" (4.2 Upper limits for CR7)
   - fitting: _not stated_
   - validation: Sum of clumps roughly consistent with total ground-based SFR  
  > "which is roughly consistent with the sum of the *HST* detected clumps and indicates no other significant source of star-formation" (4.2 Upper limits for CR7)
9. **Place clumps on SFR-L[CII] relation and infer metallicity**: Compare with local relation and literature, and Vallini2015 metallicity models  
  > "Using these models, we find that the components in CR7 would have gas-metallicities $0.1<$ Z/Z$_{\odot}<0.2$" (5 The SFR-L[CII] relation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: Data reduction and imaging  
  > "Data have been reduced using Casa version 4.7.0 (cite: McMullin2007)" (2.1 Observations & data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total L[CII] | 2.17e8 | 0.36e8 | Lsun | 4 | we measure L$_{\rm [CII]}$ = $2.17\pm0.36\times10^8$ L$_{\odot}$ in the collapsed image |
| Total [CII] FWHM | 299 | 27 | km/s | 4 | best-fitted with a line-width of $v_{\rm FWHM}=299\pm27$ km s$^{-1}$ |
| Clump A L[CII] (aperture) | 0.96e8 | 0.20e8 | Lsun | 4 | L$_{\rm [CII]} = (0.96\pm0.20) \times 10^8$ L$_{\odot}$ |
| Clump A [CII] offset from Lya | -146 | 27 | km/s | 4 | $\Delta$v$_{\rm Ly\alpha}$/km s$^{-1}$ / $-146\pm27$ |
| Clump A dynamical mass/sin^2 i | 3.9e10 | 1.7e10 | Msun | 5 | $(3.9\pm1.7)\times10^{10}$ M$_{\odot}$ for component A |
| 3sigma L_IR (T_d=35 K) | <3.14e10 | not stated | Lsun | 7 | L$_{\rm IR} < 3.14\times10^{10}$ L$_{\odot}$ |
| Dust mass limit (T_d=35 K) | <8.1e6 | not stated | Msun | 7 | M$_{\rm dust} < 8.1 (27.5)\times10^6$ M$_{\odot}$ if the dust temperature is 35 (25) K |
| SFR_IR limit | <5.4 | not stated | Msun/yr | 7 | dust obscured SFR$_{\rm IR} < 5.4$ M$_{\odot}$ yr$^{-1}$ |
| SFR_UV+IR clumps A, B, C | 28, 5, 7 | +1/-1, +2/-1, +1/-1 | Msun/yr | 8 | SFR$_{\rm UV+IR} = 28^{+1}_{-1},  5^{+2}_{-1},  7^{+1}_{-1}$ M$_{\odot}$ yr$^{-1}$ for clump A, B and C |
| log10(L[CII]/L_IR) lower limit | >-2.1 | not stated | dimensionless | 7 | log$_{10}$(L$_{\rm [CII]}$/L$_{\rm IR}$)$>-2.1$ |
| Gas metallicity | 0.1<Z/Zsun<0.2 | not stated | Zsun | 9 | we find that the components in CR7 would have gas-metallicities $0.1<$ Z/Z$_{\odot}<0.2$ |

## Qualitative findings

- [CII] emission comprises multiple components (A, B, B-2, C-2) separated spatially and in velocity; no clear ordered rotation  
  > "The three velocity channels reveal that the [Cii] emission in CR7 consists of multiple, well separated components." (3.2 Multiple separated [CII] components)

## Claim tuples

- H: Metals are present in CR7 | E: Search for [CII] in ALMA band 6 cube | R: Extended [CII] with L=2.17e8 Lsun | F: Metals present; gas not primordial | **supported**
- H: CR7 has significant dust | E: Continuum search in four spectral windows | R: No detection, rms 7 uJy/beam; L_IR<3.14e10 Lsun | F: Little or no dust; low dust-to-metal ratio | **supported**
- H: Strong Lyα emission anticorrelates with [CII] luminosity | E: Place CR7 clumps on SFR-L[CII] relation | R: All clumps consistent with local relation | F: Lyα strength not the main driver of scatter | **supported**
- H: CR7 is a build-up of a central galaxy via satellite accretion | E: Compare [CII] kinematic components with simulations | R: Multiple velocity-offset components; A has highest dynamical mass | F: Likely central galaxy A with inflowing satellites | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: PopIII-dominated or AGN-powered clump A disfavoured by metallicity and L[CII]/L_IR  
  > "Therefore, it is ruled out that the luminosity in all clumps in CR7 is dominated by PopIII-like stars" (7.2 On the nature of CR7)
- How they decided it was enough: _not stated_
- Limitation (authors): Luminosities of A and C-2 depend on aperture size (factor ~2); dynamical masses are rough  
  > "Therefore, the luminosities of clumps A and C-2 should be interpreted with caution." (3.2.1 Measurements of individual clumps)
- Limitation (authors): UV slopes of B and C poorly constrained  
  > "Due to the shallow depth of the observations, the UV slopes of clumps B and C are only poorly constrained" (2 UV properties of CR7)
- Caveat (inferred, ours): Conclusions text quotes L_IR<2.8e10 and M_dust<2.7e6, inconsistent with the 3.14e10 and 8.1e6 in the body
- Caveat (inferred, ours): Metallicity from one model with ionisation uncertainty
- Caveat (inferred, ours): Mostly marginally resolved clumps; the 0.25'' astrometric shift assumed

## Reproducibility

- Data public (paper): ALMA data cited by project code in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00122.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Exact velocity ranges for collapsed maps
- Missing: Aperture centres and UV SFR calibration constant
- Data volume (inferred): ~50-100 GB raw (6 h, 4 spws, Band 6)
- Score (inferred): 3/5, Public data and a clear measurement recipe, but imaging parameters are missing and the conclusions quote different limits than the body.
- Rediscovery candidate: yes, Public data, moderately complete recipe, numeric main results (L[CII], limits).

## Links

- Method: (cite: Schaerer2015) (IR luminosity limit conversion)
- Method: (cite: Wang2013) (Dynamical mass formula)
- Companion: (cite: Sobral2017) (HST grism and spectroscopy re-analysis of CR7)
- Companion: (cite: Sobral2015) (Original CR7 spectroscopy)

## Checks

```json
{
 "quotes": 84,
 "quotes_ok": 84,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 96,
  "stated": 61,
  "rate": 0.635
 },
 "evidence_ok": true
}
```
