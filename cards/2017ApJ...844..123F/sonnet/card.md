# The Circumgalactic Medium of Submillimeter Galaxies. II. Unobscured QSOs within Dusty Starbursts and QSO Sightlines with Impact Parameters below 100 kpc

`2017ApJ...844..123F` | The Astrophysical Journal 2017 | first author: Fu, Hai | arXiv: 1705.08908 | DOI: 10.3847/1538-4357/aa7c63

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Are Herschel-selected SMGs near QSOs (5-30 arcsec) true projected SMG-QSO pairs, or are the QSOs hosted by SMGs, and what are the properties of the composites?  
  > "we obtained ALMA band-7 observations for 29 bright *Herschel* sources near optically bright QSOs at $z > 2.5$ (i.e., purportedly projected SMG$-$QSO pairs)." (1 Introduction)
- Target **29 Herschel 350um-peaker SMGs near z>2.5 QSOs in H-ATLAS/GAMA fields G09, G12, G15**: coordinates Herschel 250 um positions listed in Table 2 (e.g. G09 0847+0045 at 131.79600, +0.76550 deg)  
  > "The *Herschel* sources are selected from three equatorial fields of the *Herschel* Astrophysical Terahertz Large Area Survey (H-ATLAS) survey" (2 Sample Selection and ALMA Observations); z/distance QSO spectroscopic redshifts (e.g. 2.67-3.38 for the four composites); z=2.5 assumed for the other SMGs  
  > "The *Herschel* sources are selected from three equatorial fields of the *Herschel* Astrophysical Terahertz Large Area Survey (H-ATLAS) survey" (2 Sample Selection and ALMA Observations); distance from QSO spectroscopic redshifts from SDSS/BOSS/2QZ; assumed z=2.5 for other ALMA sources  
  > "The *Herschel* sources are selected from three equatorial fields of the *Herschel* Astrophysical Terahertz Large Area Survey (H-ATLAS) survey" (2 Sample Selection and ALMA Observations)

## Data provenance

- ALMA projects: 2015.1.00131.S
- bands: Band 7 (343 GHz/874 um)  
  > "We used the band 7 (343 GHz/874 $\mu$m) receivers with 4 spectral windows of 2 GHz-bandwidth." (2 Sample Selection and ALMA Observations)
- frequencies and spectral setup: 4 spectral windows of 2 GHz, centered at 337.5, 339.4, 347.5, 349.5 GHz  
  > "The spectral windows are centered at 337.5, 339.4, 347.5, and 349.5 GHz." (2 Sample Selection and ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas, 38 to 44 antennas  
  > "A total of 38 to 44 12-m antennae were used, with a minimum baseline of 15.1 m and a maximum baseline of 460 m." (2 Sample Selection and ALMA Observations)
- configurations: _not stated_
- baselines: 15.1 m to 460 m  
  > "A total of 38 to 44 12-m antennae were used, with a minimum baseline of 15.1 m and a maximum baseline of 460 m." (2 Sample Selection and ALMA Observations)
- angular resolution: ~0.5 arcsec FWHM (clean beams on average 0.56x0.43 arcsec)  
  > "The clean beams are on average 0.56$''$$\times$0.43$''$" (2 Sample Selection and ALMA Observations)
- max recoverable scale: 7.3 arcsec  
  > "ensures no flux on scales less than $\theta_{\rm MRS}$ = 7.3$''$ is resolved out by the interferometer" (2 Sample Selection and ALMA Observations)
- sensitivity: rms 0.12 mJy/beam (G09, G12), 0.14 mJy/beam (G15)  
  > "The clean’ed images have rms noises of 0.12 mJy/beam in the G09 and G12 fields and 0.14 mJy/beam in the G15 field." (2 Sample Selection and ALMA Observations)
- time on source: typical 200 s per target; each SB 47-51 min  
  > "Each SB lasted between 47 and 51 min, giving a typical on-source integration time of 200 s per target." (2 Sample Selection and ALMA Observations)
- observing dates: 2016 Mar 14 and Mar 30 (Cycle 3)  
  > "were carried out on 2016 Mar 14 and Mar 30" (2 Sample Selection and ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **Herschel (H-ATLAS, SPIRE)**: 250/350/500 um photometry and positions for sample selection and SED fitting  
  > "They are sources with SNR $>$ 3 in all three SPIRE (cite: Griffin10) bands (250, 350, and 500 $\mu$m)" (2 Sample Selection and ALMA Observations)
- Other facility **SDSS/BOSS/2QZ**: QSO optical positions, spectra, photometry, C IV line widths  
  > "so we measure the C iv FWHM using the spectrum from the 2dF QSO Redshift Survey (cite: Croom04)." (4.2 Properties of the Supermassive Black Holes)
- Other facility **WISE**: 3.4-22 um forced photometry for QSO SED fits  
  > "the SDSS-position “forced” Wide-Field Infrared Survey Explorer (cite: Wright10) photometry between 3.4 $\mu$m and 22 $\mu$m (cite: Lang14a)" (4.1 Properties of the QSO Host Galaxies)
- External data: Intrinsic QSO SED template (unobscured PG QSOs)  
  > "We adopt the intrinsic QSO SED from (cite: Symeonidis16)" (4.1.1 QSO Contribution to the IR Emission) [from (cite: Symeonidis16)]
- External data: Herschel flux deboosting table  
  > "The flux densities have been deboosted using the flux bias table of (cite: Valiante16)." (Table 2) [from (cite: Valiante16)]
- External data: C IV line widths from the SDSS DR12 Quasar catalog  
  > "we adopt the line widths in the SDSS Data Release 12 Quasar catalog (cite: Paris16)" (4.2 Properties of the Supermassive Black Holes) [from (cite: Paris16)]
- External data: Literature average AGN luminosities of star-forming galaxies at various L_IR  
  > "Then, we show the average AGN luminosities for star-forming galaxies at various IR luminosities from (cite: Fu10), (cite: Rafferty11), and (cite: Chen13)." (4.3 Star-Formation-AGN Co-evolution at z ~ 3) [from (cite: Fu10); (cite: Rafferty11); (cite: Chen13)]

## Processing

### Calibration

- pipeline or manual: Reduced measurement sets from NAASC, calibrated by the ALMA pipeline in CASA  
  > "we downloaded the reduced measurement sets from the North American ALMA Science Center (NAASC), which have been fully calibrated by the ALMA pipeline in the Common Astronomical Software Applications (CASA) package" (2 Sample Selection and ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Yes, calibrated measurement sets downloaded and imaged  
  > "For imaging, we downloaded the reduced measurement sets from the North American ALMA Science Center (NAASC)" (2 Sample Selection and ALMA Observations)
- flux calibrator: J0854+2006, J1229+0203, Titan (Butler-JPL-Horizons 2012 models)  
  > "(3) the QSOs J0854$+$2006, J1229$+$0203, and Titan" (2 Sample Selection and ALMA Observations)
- flux scale uncertainty: 5%, added in quadrature  
  > "We assume a flux calibration uncertainty of 5% (see § C.4.1 in the [ALMA Cycle 4 Technical Handbook]" (2 Sample Selection and ALMA Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean; impbcor for primary beam correction  
  > "We then ran the CASA task clean to Fourier transform the calibrated visibilities" (2 Sample Selection and ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We applied the Briggs weighting to the visibilities with a robustness parameter of 0.5" (2 Sample Selection and ALMA Observations)
- uv taper: _not stated_
- cell size: 0.08 arcsec  
  > "adequately sampled by the pixel size of 0.08$''$" (2 Sample Selection and ALMA Observations)
- image size: 22"x22" clean map per field  
  > "we generate a 22$''$$\times$22$''$ clean’ed map along with a primary beam pattern." (3.1 Properties of the ALMA Sources)
- masking: 1 arcsec-radius circular masks around sources >3 sigma; loop gain 0.1; threshold 0.15 mJy/beam  
  > "restricted the cleaning regions with 1$''$-radius circular masks around all of the detected sources above 3$\sigma$ level." (2 Sample Selection and ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: CASA impbcor with primary beam pattern estimated by clean  
  > "we construct primary beam corrected images with the CASA task impbcor and the primary beam pattern estimated by clean." (2 Sample Selection and ALMA Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.56"x0.43" on average  
  > "The clean beams are on average 0.56$''$$\times$0.43$''$" (2 Sample Selection and ALMA Observations)
- final rms: 0.12 mJy/beam (G09, G12); 0.14 mJy/beam (G15)  
  > "The clean’ed images have rms noises of 0.12 mJy/beam in the G09 and G12 fields and 0.14 mJy/beam in the G15 field." (2 Sample Selection and ALMA Observations)

### Inherited from earlier work

- Parent sample selection details  
  > "Refer to (cite: Fu16) for details about the parent sample." (2 Sample Selection and ALMA Observations) [from (cite: Fu16)]
- Dust/gas mass method (Rayleigh-Jeans, K-correction)  
  > "Following the method of (cite: Scoville16) to estimate the dust mass from the optically thin Rayleigh-Jeans dust emission" (4.1.2 Mass and Surface Density of the Interstellar Medium) [from (cite: Scoville16)]
- Black hole virial mass calibration  
  > "We estimate the black hole virial masses with the calibration of (cite: Vestergaard06)" (4.2 Properties of the Supermassive Black Holes) [from (cite: Vestergaard06)]
- Bolometric correction  
  > "we apply a bolometric correction to the quasar continuum luminosity with the luminosity-dependent QSO SEDs from (cite: Hopkins07)" (4.2 Properties of the Supermassive Black Holes) [from (cite: Hopkins07)]
- SFR calibration  
  > "SFRs are estimated with the (cite: Kennicutt98) calibration for the (cite: Chabrier03) IMF" (4.1.3 IR Luminosity and SFR Surface Density) [from (cite: Kennicutt98), (cite: Chabrier03)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations / niter and the exact mask definition procedure
- Whether continuum was formed from all four spws without line flagging
- Details of the SED fitting code, fitting method and priors (modified blackbody fit procedure)
- QSO template fit procedure to SDSS/WISE photometry
- Stacking procedure details for undetected QSOs
- Bootstrapping details for mean size
- CASA version used for pipeline/imaging

## Analysis recipe

1. **Image calibrated visibilities**: CASA clean with Briggs weighting, masks, then impbcor  
  > "We then ran the CASA task clean to Fourier transform the calibrated visibilities, to iteratively deconvolve the dirty beam, and to re-convolve with a clean beam." (2 Sample Selection and ALMA Observations)
   - software: CASA
   - parameter: robust 0.5, gain 0.1, threshold 0.15 mJy/beam, pixel 0.08"  
  > "The clean loop continues until the residuals inside the masks reach a threshold of 0.15 mJy/beam." (2 Sample Selection and ALMA Observations)
   - fitting: _not stated_
   - validation: rms consistent with expectation for antenna number  
  > "These are consistent with the expectation because only 38 antennae were used in the G15 field" (2 Sample Selection and ALMA Observations)
2. **Detect sources and measure flux, position, size**: Search for >4 sigma peaks in SNR maps; fit elliptical Gaussians simultaneously with imfit on non-PB-corrected maps, then correct for primary beam  
  > "Using the CASA task imfit, we model all of the sources in a given map simultaneously with elliptical Gaussians to measure their centroid positions, flux densities, and beam-deconvolved sizes." (3.1 Properties of the ALMA Sources)
   - software: CASA imfit
   - parameter: search primarily within 10 arcsec of field center; uncertainties following Condon97  
  > "We thus primarily search for sources within 10$''$ of the field center." (3.1 Properties of the ALMA Sources)
   - fitting: Elliptical Gaussian fits  
  > "Using the CASA task imfit, we model all of the sources in a given map simultaneously with elliptical Gaussians to measure their centroid positions, flux densities, and beam-deconvolved sizes." (Properties of the ALMA Sources)
   - validation: Sizes consistent with uv-plane fits per previous studies; sizes biased high at low SNR  
  > "previous ALMA studies have shown that the sizes derived from imfit are consistent with those derived from directly fitting the $uv$ visibilities" (3.1 Properties of the ALMA Sources)
3. **Upper limit on undetected QSOs and projected pair statistics**: Stack ALMA images at QSO positions; compute expected random pairs using Poisson nearest-neighbor distribution  
  > "we stack the ALMA images at the QSO positions for the ten QSOs that are undetected but are within 18$''$ of the field center." (3.2 Submillimeter Emission from the QSOs and their Host/Companion Galaxies)
   - parameter: Sigma_SMG = 92 deg^-2, N_QSO = 1,100  
  > "$\Sigma_{\rm SMG} = 92$ deg$^{-2}$ over 161.6 deg$^2$) and the number of $z > 2.5$ QSOs in the overlapping area ($N_{\rm QSO} = 1,100$)" (3.2 Submillimeter Emission from the QSOs and their Host/Companion Galaxies)
   - assumption: Poisson distribution of random positions  
  > "for a Poisson distribution of random positions on the sky, the probability density of finding a nearest neighbor" (3.2 Submillimeter Emission from the QSOs and their Host/Companion Galaxies)
   - fitting: _not stated_
   - validation: Predicted distribution compared with observed pair separations; fits at >30"  
  > "The predicted distribution fits the observations nicely at separations greater than 30$''$." (3.2 Submillimeter Emission from the QSOs and their Host/Companion Galaxies)
4. **Calibrate Herschel positional uncertainty**: Compare ALMA vs Herschel 250 um positions; add constant 0.7" to 0.6 FWHM/SNR to enclose 67% of fields  
  > "To make the curve enclose 18 out of the 27 fields (i.e., 67% or 1$\sigma$) in our sample, one can either multiply a factor of 1.4 or add a constant offset of 0.7$''$" (3.3 Herschel Positional Uncertainties)
   - parameter: 2D to 1D conversion factor 1.517; FWHM 17.8"  
  > "$$\begin{equation}
\Delta_{\rm 1D} = \Delta_{\rm 2D}/1.517" (3.3 Herschel Positional Uncertainties)
   - fitting: _not stated_
   - validation: _not stated_
5. **QSO correction of IR photometry via SED templates**: Fit QSO template to SDSS+WISE photometry (plus torus for G15 1450+0026), extrapolate to far-IR to subtract QSO contribution  
  > "we can fit the SDSS and WISE photometry with a QSO SED template and then estimate the QSO correction in the far-IR by extrapolating the best-fit QSO template." (4.1.1 QSO Contribution to the IR Emission)
   - parameter: Torus: QSO template reddened by A_V = 4 mag with Calzetti extinction law  
  > "it is constructed by reddening the QSO template by $A_V = 4$ mag with the (cite: Calzetti00) extinction law." (4.1.1 QSO Contribution to the IR Emission)
   - assumption: Negligible dust-obscured star formation at rest-frame <10 um  
  > "By assuming negligible contribution from dust-obscured star formation at $\lambda_{\rm rest} < 10$ $\mu$m" (4.1.1 QSO Contribution to the IR Emission)
   - fitting: _not stated_
   - validation: Uncertainty at least 0.13 dex from dispersion of QSO SEDs  
  > "The uncertainty of these estimates is at least 0.13 dex, which is the dispersion of individual QSO SEDs around the mean SED." (4.1.1 QSO Contribution to the IR Emission)
6. **Derive gas/dust mass and surface density**: Extrapolate observed 870 um luminosity to rest-frame 850 um with modified blackbody; apply L850/Mgas ratio and gas-to-dust ratio  
  > "we extrapolate the *observed* 870 $\mu$m luminosity to *rest-frame* 850 $\mu$m luminosity using a modified blackbody with $T = 25$ K, $\beta = 1.8$, and $\lambda_0 = 50$ $\mu$m." (4.1.2 Mass and Surface Density of the Interstellar Medium)
   - parameter: L850/Mgas = (6.7±1.7)e19 erg/s/Hz/Msun; Mgas/Mdust = 140  
  > "$L_\nu^{850}/M_{\rm gas} = (6.7\pm1.7)\times10^{19}$ erg s$^{-1}$ Hz$^{-1}$ $M_\odot^{-1}$" (4.1.2 Mass and Surface Density of the Interstellar Medium)
   - assumption: Galactic X_CO = 3e20 (alpha_CO = 6.5); alpha_CO=1.4 alternative  
  > "the Rayleigh-Jeans method assumes the Galactic CO-to-H$_2$ conversion factor, $X_{\rm CO} \equiv N_{\rm H_2}/W_{\rm CO} = 3\times10^{20}$" (4.1.2 Mass and Surface Density of the Interstellar Medium)
   - fitting: _not stated_
   - validation: _not stated_
7. **Fit IR luminosity and SFR**: Fit modified blackbody (optically thick, lambda0 = 150 um, beta = 2) to SPIRE+ALMA photometry; integrate 8-1000 um; SFR = L_IR/1e10 (Kennicutt98, Chabrier IMF)  
  > "We fixed $\lambda_0$ at 150 $\mu$m for a typical power-law slope of $\beta = 2$" (4.1.3 IR Luminosity and SFR Surface Density)
   - parameter: Redshift fixed (QSO z for composites, 2.5 otherwise)  
  > "assume a redshift of 2.5 for the remaining ALMA sources" (4.1 Properties of the QSO Host Galaxies)
   - assumption: Constant dust temperature, local thermal equilibrium  
  > "assuming local thermal equilibrium at a constant temperature $T$" (4.1.3 IR Luminosity and SFR Surface Density)
   - fitting: Modified blackbody fit; Monte Carlo simulations of synthetic photometry for statistical error  
  > "through Monte Carlo simulations of synthetic *Herschel* and ALMA photometry" (4.1.3 IR Luminosity and SFR Surface Density)
   - validation: Compared with optically thin models and Arp 220 SED; L_IR differs by ~0.1 dex  
  > "The resulting $L_{\rm IR}$ can be higher than the blackbody fits by $\sim$0.1 dex" (4.1.3 IR Luminosity and SFR Surface Density)
8. **BH mass, bolometric luminosity, accretion rate**: Virial mass from C IV FWHM and L1350 (Vestergaard & Peterson 2006); L_bol via Hopkins07 correction; Mdot = L_bol/6.3e45 with epsilon=0.1  
  > "we then assume a radiative efficiency of $\epsilon = 0.1$ to convert the bolometric luminosity to an accretion rate" (4.2 Properties of the Supermassive Black Holes)
   - assumption: No correction applied for C IV non-virial bias  
  > "However, we do not correct our BH masses, because the systematic bias is low at $\sim10^{9}$ $M_{\odot}$" (4.2 Properties of the Supermassive Black Holes)
   - fitting: _not stated_
   - validation: Zero-point uncertainty 0.36 dex  
  > "The 1$\sigma$ uncertainty of the zero point is 0.36 dex." (4.2 Properties of the Supermassive Black Holes)
9. **Compare growth of BH and galaxies; estimate QSO duty cycle**: Compare SFR/Mdot_BH of composites with present-day BH-stellar mass density ratio and literature AGN luminosities  
  > "If we were to shift the average QSO luminosity downward by 0.5 dex so that it reaches the level required by the present-day density ratio, then it implies a QSO duty cycle of $\sim$30%" (4.3 Star-Formation-AGN Co-evolution at z ~ 3)
   - assumption: 50% recycling of stellar mass; 50% gas fraction; gas exhaustion time 200 Myr  
  > "(1) a 50% gas fraction ($M_{\rm gas} = 0.5\,M_{\rm Bulge}$), (2) a gas exhaustion timescale of $\tau = 2\,M_{\rm gas}/{\rm SFR} = 200$ Myr, and (3) a 50% recycling rate of the stellar mass." (4.3 Star-Formation-AGN Co-evolution at z ~ 3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA pipeline calibration; clean, impbcor, imfit  
  > "which have been fully calibrated by the ALMA pipeline in the Common Astronomical Software Applications (CASA) package" (2 Sample Selection and ALMA Observations)
- **clean** : imaging of calibrated visibilities  
  > "We then ran the CASA task clean to Fourier transform the calibrated visibilities" (2 Sample Selection and ALMA Observations)
- **impbcor** : primary beam correction  
  > "we construct primary beam corrected images with the CASA task impbcor" (2 Sample Selection and ALMA Observations)
- **imfit** : elliptical Gaussian fits for source flux, position, size  
  > "Using the CASA task imfit, we model all of the sources in a given map simultaneously with elliptical Gaussians" (3.1 Properties of the ALMA Sources)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of ALMA sources detected | 39 (38 used) | not stated | sources | 2 | A total of 39 sources with flux densities between 0.7 mJy $\leq S_{870} \leq 14.4$ mJy are detected in 27 of the 29 ALMA fields. |
| Herschel sources that are SMGs (S870>2 mJy) | 20 of 29 (69%) | not stated | sources | 2 | These observations confirm that 20 of the 29 (69%) *Herschel* sources in our sample are SMGs with $S_{870} > 2$ mJy. |
| Mean intrinsic source size of 13 resolved high-SNR sources | 0.29 | 0.03 | arcsec | 2 | The mean source size of those is 0.29$''$$\pm$0.03$''$, where the uncertainty is from bootstrapping. |
| Stacked 3 sigma upper limit per undetected QSO | ~3.6 | not stated | mJy | 3 | The stacking analysis provides a 3$\sigma$ upper limit of $\sim$3.6 mJy per QSO |
| Expected projected pairs among six Herschel-QSO pairs | 1.4 | 1.0 | pairs | 3 | Since six of these eight pairs were observed by ALMA, we expect only $1.4\pm1.0$ projected pairs |
| Empirical Herschel-ALMA positional uncertainty (67% radius) | 4.22 | 0.14 | arcsec | 4 | 18 of the 27 fields (67%) show ALMA positions within 4.22$''$$\pm$0.14$''$ of the *Herschel* position |
| Mean SFR surface density of SMG-QSO composites | ~260 | not stated | Msun/yr/kpc^2 | 7 | The mean SFR surface density of the SMG-QSO composites is $\sim$260 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$. |
| Mean dust mass surface density (alpha_CO=6.5) | ~8e8 | not stated | Msun/kpc^2 | 6 | the average dust mass surface density is $\sim8\times10^8$ $M_{\odot}$ kpc$^{-2}$ |
| BH accretion rates of composites | 2-7 | not stated | Msun/yr | 8 | The estimated BH accretion rates range between 2 and 7 $M_{\odot}$ yr$^{-1}$, with Eddington ratios between 10 and 30% |
| BH accretion fraction of total bolometric luminosity | 30-60% | not stated | percent | 8 | BH accretion contributes a large fraction (30-60%) of the total bolometric luminosity |
| QSO duty cycle in SMGs at z~3 | ~30% (upper limit) | not stated | percent | 9 | then it implies a QSO duty cycle of $\sim$30% among SMGs with $L_{\rm IR} \sim 10^{13}$ $L_{\odot}$ at $z \sim 3$ |

## Qualitative findings

- No additional submillimeter companions around the four QSO-hosting SMGs and no significant UV reddening in the QSOs  
  > "No additional submillimeter companions are detected around these QSOs and the rest-frame ultraviolet spectra of the QSOs show no evidence of significant reddening." (abstract)

## Claim tuples

- H: Are Herschel-detected QSOs with <10" separation projected pairs or QSOs hosted by SMGs? | E: ALMA 870 um imaging of six such fields and comparison of ALMA vs optical QSO positions | R: Four of six QSOs are coincident with ALMA sources (offsets <0.15") | F: Four of the six pairs are SMG-QSO composite galaxies | **supported**
- H: Do the remaining two QSOs with nearby SMGs probe the CGM of SMGs at <100 kpc? | E: Poisson nearest-neighbor estimate of projected pairs | R: 1.4±1.0 expected projected pairs among six | F: At least one of the two is a projected pair, though a wet-dry merger cannot be excluded | **partially**
- H: Black holes grow faster relative to galaxies than present-day mass ratio in SMG-QSO composites | E: Compare Mdot_BH and SFR with present-day mass-ratio relation | R: Offset ~0.5 dex; BHs growing ~3x faster | F: QSO duty cycle in SMGs of <~30% | **supported**
- H: Does the standard formula for Herschel positional uncertainty hold? | E: Compare ALMA-Herschel offsets with 0.6 FWHM/SNR | R: Formula encloses only 14 of 27 (52%) instead of 68% | F: Underestimated; add 0.7" constant term | **supported**

## Reasoning

- Why this data: ALMA resolution needed because Herschel/single-dish beams cannot separate QSOs from SMGs  
  > "only interferometer observations can reveal its constituents." (1 Introduction)
- Why this method: Added constant offset preferred because Herschel positional uncertainty should not drop to fractions of an arcsec at high SNR  
  > "We prefer the latter because the positional uncertainty of *Herschel* should not decrease to a fraction of an arcsec even at the highest SNR" (3.3 Herschel Positional Uncertainties)
- Alternative: Multiplicative factor of 1.4 instead of additive 0.7" offset for positional uncertainty  
  > "one can either multiply a factor of 1.4 or add a constant offset of 0.7$''$ to Eq." (3.3 Herschel Positional Uncertainties)
- How they decided it was enough: _not stated_
- Limitation (authors): Redshifts of non-QSO SMGs unknown (assumed 2.5), making their results less reliable  
  > "The results for the rest of the sample are less reliable because of their unknown redshifts" (4.1.3 IR Luminosity and SFR Surface Density)
- Limitation (authors): Size measurements at SNR<10 are biased high  
  > "Note that the size estimates are biased high at ${\rm SNR} < 10$" (4.1.2 Mass and Surface Density of the Interstellar Medium)
- Limitation (authors): Duty cycle is an upper limit since no BH accretion assumed in SMGs without QSOs  
  > "This estimate of the QSO duty cycle should be considered as an upper limit" (4.3 Star-Formation-AGN Co-evolution at z ~ 3)
- Caveat (inferred, ours): Duty cycle estimate depends on assumed mass ratio, recycling fraction and a 0.5 dex shift, with small number (4) of objects
- Caveat (inferred, ours): Gas masses depend on assumed alpha_CO and T=25 K
- Caveat (inferred, ours): IR SED fits with fixed lambda0 and assumed redshift 2.5 for most SMGs
- Caveat (inferred, ours): Projected-pair probability rests on only 8 pairs and Poisson assumption ignoring clustering
- Caveat (inferred, ours): C IV virial masses may be biased

## Reproducibility

- Data public (paper): Data from ALMA project 2015.1.00131.S, downloaded as reduced measurement sets from NAASC  
  > "we downloaded the reduced measurement sets from the North American ALMA Science Center (NAASC)" (2 Sample Selection and ALMA Observations)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: SED fitting code and details
- Missing: Exact stacking procedure
- Missing: QSO template fit details and Herschel/SDSS/WISE photometry values for composites
- Data volume (inferred): ~10-50 GB (29 fields, band 7, short integrations; archive MS)
- Score (inferred): 3/5, Imaging and source extraction are well specified and data are public with a single project code, but SED fitting details and CASA version are missing.
- Rediscovery candidate: yes, Data are public, imaging parameters (robust 0.5, threshold, pixel) and imfit analysis are stated, and main results (source counts, fluxes, sizes) are numeric and tabulated.

## Links

- Method: (cite: McMullin07) (CASA)
- Method: (cite: Condon97) (imfit uncertainties and positional accuracy)
- Companion: (cite: Fu16) (Paper I: parent sample and projected SMG-QSO pair)
- Related: H-ATLAS
- Related: GAMA

## Checks

```json
{
 "quotes": 96,
 "quotes_ok": 96,
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
  "facts": 104,
  "stated": 79,
  "rate": 0.76
 },
 "evidence_ok": true
}
```
