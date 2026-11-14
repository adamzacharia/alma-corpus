# ALMA Lensing Cluster Survey: Dust mass measurements as a function of redshift, stellar mass, and star formation rate from z = 1 to z = 5

`2025A&A...693A.190J` | Astronomy and Astrophysics 2025 | first author: Jolly, Jean-Baptiste | arXiv: 2411.11212 | DOI: 10.1051/0004-6361/202346239

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: How do average dust mass of galaxies evolve with redshift (z=1 to 5), stellar mass and SFR, measured by stacking ALCS band-6 continuum at HST-IRAC catalogue positions?  
  > "we aimed at constraining the dust mass evolution with redshift, stellar mass and star formation rate (SFR)." (abstract); "By binning galaxies by redshift, and further splitting them according to their stellar mass or SFR, we study the evolution of the dust mass with redshift, and its scaling relation with stellar mass and SFR." (1 Introduction)
- Target **33 ALCS lensing clusters (16 RELICS, 12 CLASH, 5 Frontier Fields)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Stacked sample of 4103 lensed galaxies at 1<=z<5 (HST-IRAC catalogue)**: coordinates positions from the Kokorev2022 HST-IRAC catalogue (values not given in paper)  
  > "When available, spectroscopic redshifts are used in place of photometric redshifts." (2.2 Source catalogue); "Sources were spatially aligned using the position extracted from the (cite: Kokorev2022) catalog." (3.1 Stacking); z/distance 1<=z<5, spectroscopic where available, otherwise photometric  
  > "When available, spectroscopic redshifts are used in place of photometric redshifts." (2.2 Source catalogue); "Sources were spatially aligned using the position extracted from the (cite: Kokorev2022) catalog." (3.1 Stacking); distance from Kokorev2022 catalogue  
  > "When available, spectroscopic redshifts are used in place of photometric redshifts." (2.2 Source catalogue); "Sources were spatially aligned using the position extracted from the (cite: Kokorev2022) catalog." (3.1 Stacking)

## Data provenance

- ALMA projects: 2018.1.00035.L, 2013.1.00999.S, 2015.1.01425.S
- bands: Band 6 (lambda ~ 1.2 mm)  
  > "It observed 33 lensing clusters in band 6" (2.1 ALCS)
- frequencies and spectral setup: double frequency window setup: 250.0-257.5 GHz and 265.0-272.5 GHz  
  > "in a double frequency window setup, observing both from 250.0 to 257.5 GHz and from 265.0 to 272.5 GHz, for a total bandwidth of 15 GHz" (2.1 ALCS)
- continuum bandwidth: total bandwidth of 15 GHz  
  > "for a total bandwidth of 15 GHz" (2.1 ALCS)
- arrays: _not stated_
- configurations: compact array configurations C43-1 and C43-2  
  > "in compact array configurations C43-1 and C43-2" (2.1 ALCS)
- baselines: _not stated_
- angular resolution: synthesized beam FWHM 2 arcsec (uv-tapered)  
  > "the full width at half maximum of the synthesized beam is 2 arcsec" (2.1 ALCS)
- max recoverable scale: _not stated_
- sensitivity: average map RMS ~63 uJy/beam (per-cluster values in Table 1)  
  > "Average: 63" (Table 1); "The average RMS of the maps is $\sim63\, \mathrm{\mu}$Jy/beam" (2.1 ALCS)
- time on source: _not stated_
- observing dates: December 2018 to December 2019 (cycles 6 and 7)  
  > "Observations were carried out between December 2018 and December 2019 (cycles 6 and 7)" (2.1 ALCS)
- pi or archival as stated: ALCS large program (PI K. Kohno) concatenated, when available, with archival ALMA Frontier Fields data (PI Bauer)  
  > "When available, the ALCS data were concatenated with existing ALMA data" (2.1 ALCS)
- Other facility **HST and Spitzer/IRAC (catalogue photometry)**: Source positions, redshifts, SFRs, stellar masses and magnifications come from the HST-IRAC catalogue of Kokorev2022  
  > "We extracted the positions, redshifts, physical characteristics (SFRs and stellar masses) as well as lensing magnifications of galaxies at $1\leq z \leq 5$ from the HST-IRAC catalog presented in (cite: Kokorev2022)." (2.2 Source catalogue)
- External data: HST-IRAC catalogue: positions, redshifts, SFRs, stellar masses, magnifications  
  > "We extracted the positions, redshifts, physical characteristics (SFRs and stellar masses) as well as lensing magnifications of galaxies at $1\leq z \leq 5$ from the HST-IRAC catalog presented in (cite: Kokorev2022)." (2.2 Source catalogue) [from (cite: Kokorev2022)]
- External data: Dust opacity kappa = 0.0431 m^2/kg at nu0 = 352.6 GHz  
  > "We used $\kappa_{\nu_0}$=0.0431 m$^2$ kg$^{-1}$ with ${\nu_0}=352.6$ GHz (cite: Li2001; Magnelli2020)." (3.3 Measuring M_dust) [from (cite: Li2001; Magnelli2020)]
- External data: Dust emissivity index beta = 1.8 (Galactic, Planck)  
  > "We used $\beta=1.8$, the Galactic dust emissivity index measurement from the *Planck* data (cite: Planck2011)" (3.3 Measuring M_dust) [from (cite: Planck2011)]
- External data: Main sequence SFR_MS for Delta(MS) (quiescence diagnostic)  
  > "the expected SFR for a galaxy with the same stellar mass and on the MS (cite: Speagle2014)" (2.2 Source catalogue) [from (cite: Speagle2014)]
- External data: COSMOS2020 stellar mass function used for sample completeness check  
  > "we compare its stellar mass function (SMF) to the one derived in the COSMOS2020 sample (cite: Weaver2022; Weaver2023)" (2.2 Source catalogue) [from (cite: Weaver2022; Weaver2023)]
- External data: CMB correction prescription (Equation 18)  
  > "This is corrected by following Equation 18 of (cite: DaCunha2013)." (3.3 Measuring M_dust) [from (cite: DaCunha2013)]
- External data: Magnification uncertainty of 20%  
  > "following (cite: Sun2022) and (cite: Fujimoto2023) we use a magnification uncertainty of 20% of the magnification associated to each subsample" (3.4 Uncertainty computation) [from (cite: Sun2022; Fujimoto2023)]
- Simulation/model as data: Semi-analytical dust-mass predictions (Popping2017, SHARK, Vijayan2019, Triani2020) compared with measured dust masses  
  > "When comparing our results to the semi-analytical modeling from (cite: Popping2017; Shark; Vijayan2019; Triani2020)" (5 Discussion)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.4.0 (26 cycle-6 clusters); CASA 5.6.1 (remaining cycle-7 clusters)  
  > "package version 5.4.0 for the 26 clusters observed in cycle 6 and v5.6.1 for the remaining clusters observed in cycle 7" (2.1 ALCS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Throughout this paper, we use natural-weighted, primary-beam-corrected, and *uv*-tapered continuum maps, with a tapering parameter of 2 arcsec" (2.1 ALCS)
- uv taper: 2 arcsec  
  > "Throughout this paper, we use natural-weighted, primary-beam-corrected, and *uv*-tapered continuum maps, with a tapering parameter of 2 arcsec" (2.1 ALCS)
- cell size: 0.16 arcsec  
  > "with a corresponding pixel size of 0.16 arcsec" (2.1 ALCS)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: primary-beam-corrected maps used  
  > "Throughout this paper, we use natural-weighted, primary-beam-corrected, and *uv*-tapered continuum maps, with a tapering parameter of 2 arcsec" (2.1 ALCS)
- array combination: ALCS data concatenated with existing ALMA Frontier Fields data when available  
  > "When available, the ALCS data were concatenated with existing ALMA data" (2.1 ALCS)
- smoothing: _not stated_
- final beam: synthesized beam FWHM 2 arcsec  
  > "the full width at half maximum of the synthesized beam is 2 arcsec" (2.1 ALCS)
- final rms: average ~63 uJy/beam (Table 1 gives per-map values)  
  > "Average: 63" (Table 1)

### Inherited from earlier work

- Full description of the ALCS survey and its data  
  > "Full description of the survey can be found in (cite: KohnoALCS)." (2.1 ALCS) [from (cite: KohnoALCS)]
- Catalogue construction, redshifts, SFRs, stellar masses, magnifications  
  > "We extracted the positions, redshifts, physical characteristics (SFRs and stellar masses) as well as lensing magnifications of galaxies at $1\leq z \leq 5$ from the HST-IRAC catalog presented in (cite: Kokorev2022)." (2.2 Source catalogue) [from (cite: Kokorev2022)]
- Stacking code and bootstrap/empty-stack routines  
  > "(see (cite: Jolly2020) for a detailed description of the bootstrapping routine included in LINESTACKER)" (3.4 Uncertainty computation) [from (cite: Jolly2020)]
- Optically thin modified blackbody dust mass equation  
  > "we use a single modified blackbody curve, under the approximation of an optically thin regime, following (cite: Kovacs2010) and (cite: Magnelli2020)" (3.3 Measuring M_dust) [from (cite: Kovacs2010) and (cite: Magnelli2020)]
- Single cold-component mass-weighted dust temperature of 25 K  
  > "Following (cite: Magnelli2020) and (cite: Pozzi2021) we decided to use a single cold component to account for the dust temperature" (3.3 Measuring M_dust) [from (cite: Magnelli2020); (cite: Pozzi2021)]
- Lower-redshift and cluster sources studied separately  
  > "as lower redshift sources as well as cluster sources were presented in a separate paper" (2.2 Source catalogue) [from (cite: Guerrero)]

### Not stated but needed to reproduce (our reading)

- LINESTACKER version and exact call settings (aperture/beam normalisation, handling of PB edge, random source-free coordinate selection and seeds)
- tclean parameters used to make the tapered maps (niter, threshold, masking, robust-free natural weights, imaging channels) and whether the continuum was line-free or full bandwidth
- Pipeline versus manual calibration, flux calibrators and flux scale uncertainty for ALCS and the concatenated Frontier Fields data
- Exact stack/image positions and how concatenated multi-project fields were combined
- The functional form of the quadratic fits (variables in log or linear space, parametrisation of a and b) and fitting method
- Version/vintage of the Kokorev2022 catalogue and the exact SED-fitting-derived SFR and mass definitions (IMF, SFR timescale)
- Exact CMB correction implementation (Equation 18 of DaCunha2013) and how the correction was applied per subsample
- How cosmological D_L was computed per subsample (use of mean z versus per-source) and how the average magnification was computed (arithmetic mean)

## Analysis recipe

1. **Select the source sample from the HST-IRAC catalogue**: Sequential cuts on redshift, quality, mass, SFR, H-band magnitude, primary beam level, z range and magnification, leaving 4103 sources  
  > "In total, our full sample finally adds up to a total of 4103 sources." (2.2 Source catalogue); "have H-band magnitudes above 24, to avoid contamination from blue faint galaxies" (2.2 Source catalogue)
   - parameter: PB > 0.5; 1<=z<5; 10^8<=M*<=10^12 Msun; 0.001<=SFR<=10^3 Msun/yr; magnification <100  
  > "have associated PB values higher than 0.5" (2.2 Source catalogue); "(vii) have a magnification factor below 100" (2.2 Source catalogue)
   - assumption: Spectroscopic redshifts used where available, otherwise photometric; SFR and stellar mass corrected for magnification  
  > "When available, spectroscopic redshifts are used in place of photometric redshifts." (2.2 Source catalogue)
   - fitting: _not stated_
   - validation: Compared the sample stellar mass function with COSMOS2020; flagged over-density at z>4  
  > "The studied sample seems to present an over-density of sources at $z>4$" (2.2 Source catalogue)
2. **Bin sources into redshift, stellar mass and SFR subsamples**: Four redshift bins split by either four stellar-mass bins or five SFR bins  
  > "To study the evolution of dust mass across redshift we separated the sources in four redshift bins" (2.3 Subsamples); "We additionally split sources according to either their SFRs or stellar masses in the following bins" (2.3 Subsamples)
   - parameter: Redshift bins 1-2, 2-3, 3-4, 4-5; individually detected sources not excluded  
  > "One should note that sources individually detected in the ALCS data are not excluded from the samples." (2.3 Subsamples)
   - fitting: _not stated_
   - validation: _not stated_
3. **Stack 1.2 mm continuum and measure stacked flux**: Unweighted mean stack, pixel to pixel, single channel mode, on uv-tapered images; flux integrated in a central circle of radius 2 arcsec and divided by beam area in pixels  
  > "Sources were stacked pixel to pixel using mean stacks without weights" (3.1 Stacking); "with a radius $R_{\rm integ}=2''$ (12.5 pixels), corresponding to the synthesized beam size" (3.1 Stacking)
   - software: LINESTACKER
   - parameter: Stamp size 9.76 x 9.76 arcsec^2 (61 x 61 pixels)  
  > "Stacking was operated with stamp sizes of 9.76 $\times$ 9.76 arcsec$^2$ (61 $\times$ 61 pixels)." (3.1 Stacking)
   - fitting: _not stated_
   - validation: Median stacking repeated for all subsamples; trends unchanged though median dust masses systematically slightly lower  
  > "it should be however noted that the dust-mass trends observed in this analysis (with redshift, stellar mass and SFR) remain the same in the median stacking analyses." (4.2 Median stacking analysis)
4. **Estimate stack noise and set detections / upper limits**: Empty stacks from random source-free coordinates with the same stamp size and number of targets, 1000 realisations per subsample; standard deviation gives RMS; flux below 3 RMS replaced by a 3 sigma upper limit  
  > "This process is performed 1000 times for each subsample." (3.1 Stacking); "When the flux in the central region of the stack stamp is lower than 3 times its associated RMS" (3.1 Stacking)
   - software: LINESTACKER
   - fitting: _not stated_
   - validation: _not stated_
5. **Correct stacked flux for lensing magnification**: Divide the stacked flux by the average magnification of the subsample; alternative of correcting each stamp before stacking gives consistent fluxes  
  > "the final flux is hence computed as: $F_{final} = \frac{F_{stack} }{\overline{\mu}}$" (3.2 Magnification corrections); "The 1.2 mm fluxes derived in both cases are very consistent, with values overlapping within the error margins." (3.2 Magnification corrections)
   - assumption: Noise is independent of magnification so per-stamp correction would reduce stacking efficiency  
  > "the signal in each stack stamp consists of both the flux from the source, which is gravitationally magnified, and some noise, which is independent of the magnification." (3.2 Magnification corrections)
   - fitting: _not stated_
   - validation: Compared the two magnification-correction orderings  
  > "we hence repeated our analysis with this correction method." (3.2 Magnification corrections)
6. **Convert 1.2 mm flux to dust mass**: Single optically thin modified blackbody with CMB correction, using the Kovacs2010/Magnelli2020 equation  
  > "we use a single modified blackbody curve, under the approximation of an optically thin regime, following (cite: Kovacs2010) and (cite: Magnelli2020)" (3.3 Measuring M_dust)
   - parameter: beta = 1.8; kappa = 0.0431 m^2 kg^-1 at nu0 = 352.6 GHz  
  > "We used $\beta=1.8$, the Galactic dust emissivity index measurement from the *Planck* data (cite: Planck2011)" (3.3 Measuring M_dust); "We used $\kappa_{\nu_0}$=0.0431 m$^2$ kg$^{-1}$ with ${\nu_0}=352.6$ GHz (cite: Li2001; Magnelli2020)." (3.3 Measuring M_dust)
   - parameter: CMB flux correction ~1.03 at z~1 to ~1.31 at z~6; CMB dust-temperature heating ~3% at z=6  
  > "it yields an upward measurement to our results ranging from $\sim1.03$ at $z\sim1$ to $\sim1.31$ at $z\sim6$" (3.3 Measuring M_dust)
   - assumption: Mass-weighted dust temperature T_rest = 25 K at all redshifts  
  > "used a mass weighted dust temperature of $T_{\rm rest}=25$ K" (3.3 Measuring M_dust)
   - assumption: Flat LCDM, Omega_m = 0.3, Omega_Lambda = 0.7, H0 = 70  
  > "we assume a $\Lambda$CDM cosmology with $\Omega_m = 0.3$, $\Omega_\lambda = 0.7$ and $H_0=70$  km s$^{-1}$Mpc$^{-3}$" (1 Introduction)
   - fitting: _not stated_
   - validation: Sensitivity to beta and T quantified: beta=1.5 or 2.0 changes results by ~9% at z=1.5 and ~15% at z=5.5; T=40 K changes results by ~50% in highest redshift bin  
  > "choosing $\beta=1.5$ (or 2.0) would only modify our results by $\sim 9$% at $z=1.5$ and $\sim 15$% at $z=5.5$" (3.3 Measuring M_dust); "using $T=40$ K (instead of 25) in dust masses computation would change our results by $\sim$ 50% in the highest redshift bin" (5 Discussion)
7. **Propagate uncertainties on dust mass**: Bootstrap each subsample 1000 times, take 16th to 84th percentile and sum quadratically with stack RMS; propagate redshift percentile spread and a 20% magnification uncertainty  
  > "In each subsample, the dust mass is re-computed 1000 times, each time with a different sample, randomized from the original subsample without replacement" (3.4 Uncertainty computation); "that we sum quadratically with the stack RMS" (3.4 Uncertainty computation)
   - software: LINESTACKER
   - assumption: Adding bootstrap and RMS errors quadratically is an approximation that slightly over-estimates the error (they are correlated)  
  > "This is an approximation that should slightly over-estimate the error computation." (Footnote 1)
   - fitting: _not stated_
   - validation: Bootstrap distributions peak slightly below the original stack, interpreted as skew from individual detections  
  > "which can be easily explained from the presence of individual detections in the samples" (3.4 Uncertainty computation)
8. **Fit scaling relations of dust mass with M*, SFR and z**: Quadratic fits to detections only, ignoring upper limits, when at least 3 points are available  
  > "Fits are performed using detections only (ignoring upper limits), and only when the number of data points is $\geq 3$." (4.1 Mean stacking results)
   - fitting: _not stated_
   - validation: Results compared with models and literature stacks/detections  
  > "our data points are typically below other measurements (individual detections and stacks)" (4.1 Mean stacking results)
9. **Test robustness against quiescent galaxies**: Repeat stacking after removing sources with Delta(MS) < -0.5  
  > "In total, 2157 galaxies are removed from the sample, leading to a final size of 1946 after removing quiescent galaxies." (Appendix A)
   - software: LINESTACKER
   - fitting: _not stated_
   - validation: Overall trends confirmed; mass-selected dust masses rise, SFR-selected stable  
  > "In any event, the overall trends observed in the main analysis seem to be confirmed even when removing sources with $\Delta$MS$<-0.5$." (Appendix A)

## Software

- **CASA** 5.4.0 (cycle 6), 5.6.1 (cycle 7): Data reduction and calibration of ALCS data  
  > "The data were reduced and calibrated using the Common Astronomy Software Applications (cite: CASA) package version 5.4.0 for the 26 clusters observed in cycle 6 and v5.6.1 for the remaining clusters observed in cycle 7" (2.1 ALCS)
- **LINESTACKER** : Continuum stacking, empty-stack RMS and bootstrapping  
  > "Stacking was done using LINESTACKER (cite: Jolly2020), in single channel mode (to perform continuum stacking), on *uv*-tapered images" (3.1 Stacking)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Final stacked sample size | 4103 | not stated | sources | 1 | In total, our full sample finally adds up to a total of 4103 sources. |
| Average map RMS | 63 | not stated | uJy/beam | 0 | Average: 63 |
| Lowest stack standard deviation (z=1-2, lowest M* and SFR bins) | ~4.3e-3 | not stated | mJy/beam | 4 | reaches levels as low as $\sim4.3 \times 10^{-3}$ mJy per beam |
| Stacked flux range for detections (before magnification correction) | ~1.78e-2 to ~1.04 | not stated | mJy | 3 | $\sim1.78 \times 10^{-2}$ mJy and $\sim1.04$ mJy for stack detections |
| Range of securely extracted dust masses (S/N > 3, after magnification correction) | ~2.8e6 to ~2.56e8 | not stated | Msun | 6 | $\sim2.8 \times 10^6$ M$_{\odot}$ to $\sim2.56 \times 10^8$ M$_{\odot}$ (after magnification correction) |
| Mean dust mass, <z>=1.41, log<M*>=10.42 | 6.95e7 | 1.84e7 | Msun | 6 | $6.95\times10^{7}$ $\pm$ $1.84\times10^{7}$ |
| Mean dust mass, <z>=1.42, log<M*>=9.43 | 1.61e7 | 4.33e6 | Msun | 6 | $1.61\times10^{7}$ $\pm$ $4.33\times10^{6}$ |
| Mean dust mass, <z>=2.84, <SFR>=133 Msun/yr | 2.54e8 | 7.27e7 | Msun | 6 | $2.54\times10^{8}$ $\pm$ $7.27\times10^{7}$ |
| Fit M_dust(z) at fixed SFR 10<SFR<50: coefficient a | 10.5e7 | 1.6e7 | Msun | 8 | $10.5 \pm 1.6 \times 10^{7}$ |
| Fit M_dust(z) at fixed SFR 10<SFR<50: coefficient b | -1.1 | 0.2 | dimensionless | 8 | $-1.1 \pm 0.2$ |
| Fit M_dust(z) at fixed M* 10^9<M*<10^10: coefficient b | -1.8 | 0.7 | dimensionless | 8 | $-1.8 \pm 0.7$ |
| Galaxies removed when excluding Delta(MS) < -0.5 | 2157 (1946 remain) | not stated | sources | 9 | In total, 2157 galaxies are removed from the sample, leading to a final size of 1946 after removing quiescent galaxies. |

## Qualitative findings

- Average dust mass declines steadily with redshift; higher stellar mass or SFR gives higher dust mass  
  > "We observe a steady decline in the average dust mass with redshift." (abstract); "Moreover, sources with higher stellar mass or SFR have higher dust mass on average, allowing us to derive scaling relations." (abstract)
- Results agree with models at lower z but give lower dust mass than predicted at higher redshift  
  > "Our results are mostly in good agreement with models at $z\sim1$ – $3$, but indicate typically lower dust-mass than predicted at higher redshift." (abstract)
- Median stacks give systematically lower dust masses than mean stacks, same trends  
  > "The overall median dust masses derived through our stacking analyses are systematically slightly lower than the mean dust masses" (4.2 Median stacking analysis)

## Claim tuples

- H: Does the average dust mass of galaxies change with redshift from z=1 to 5? | E: Mean continuum stacking of ~4000 lensed galaxies in four redshift bins, converted to dust mass with a modified blackbody at T=25 K | R: Dust mass decreases with increasing redshift | F: Dust build-up in galaxies is a gradual process over cosmic time | **supported**
- H: Do dust mass scale with stellar mass and SFR? | E: Stacks split into stellar-mass and SFR bins within each redshift bin, with quadratic fits to detections | R: Dust mass increases with stellar mass and with SFR; SFR relation is clearer | F: SFR is a better dust mass tracer than stellar mass | **supported**
- H: Do quiescent galaxies bias the stacked dust masses low? | E: Repeated the stacking after removing sources with Delta(MS) < -0.5 | R: Dust masses in mass-selected stacks rise, especially at high stellar mass; SFR-selected stacks stable | F: Quiescent galaxies have lower dust content than star-forming ones at similar stellar mass | **supported**
- H: Do semi-analytical models reproduce the measured dust masses? | E: Compared measured dust masses with Popping2017, SHARK, Vijayan2019 and Triani2020 predictions | R: Decent agreement at z~1; models other than Vijayan2019 predict increasing dust mass with redshift while data show decrease | F: Models over-predict dust mass at high redshift relative to the data | **partially**

## Reasoning

- Why this data: Lensing plus stacking probes lower intrinsic dust luminosity than individual detections  
  > "With the help of both gravitational lensing and stacking, it is hence possible to push the limit of observations toward sources with lower intrinsic dust luminosity." (1 Introduction)
- Why this method: uv-tapered maps chosen to give homogeneous beam sizes for stacking; fixed T chosen for comparison with earlier studies  
  > "*uv*-tapered maps have been chosen over natural resolution maps to ensure beam-size homogeneity of the different images when stacking." (2.1 ALCS); "we decided to stick to a fixed value to allow easier comparison with similar previous studies" (3.3 Measuring M_dust)
- Alternative: Correcting each stamp for its magnification before stacking, rejected as primary because it down-scales noise inconsistently  
  > "By down-scaling the noise in each stamp by a different number (unrelated to the noise properties), one might effectively reduce the efficiency and reliability of the stacking analysis." (3.2 Magnification corrections)
- Alternative: Redshift-evolving dust temperature not adopted  
  > "While choosing an evolving dust temperature with redshift could seem more appropriate, we decided to stick to a fixed value" (3.3 Measuring M_dust)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust masses depend strongly on assumed dust temperature  
  > "our dust mass results are effectively highly dependent on the estimated dust temperature" (3.3 Measuring M_dust)
- Limitation (authors): z>3 bins overpopulated, so dust content at z>3 likely over-estimated; photometric redshift misclassification  
  > "As a consequence the dust content at $z>3$ is likely over-estimated." (5 Discussion)
- Limitation (authors): HST/Spitzer-based catalogue may miss the dustiest galaxies, biasing dust masses low  
  > "some of the most dusty galaxies may be missing, biasing the analysis toward lower averaged dust masses" (5 Discussion)
- Caveat (inferred, ours): Fixed T=25 K and Li and Draine opacity make absolute dust masses uncertain by factors of a few; trend with z is partly degenerate with the rest-frame wavelength shift
- Caveat (inferred, ours): Photometric-redshift outliers (~20% per Kokorev2022) and SMF over-density at z>4 could contaminate high-z bins
- Caveat (inferred, ours): Quadratic fit form and error treatment (non-independent errors summed in quadrature) are loosely specified; fits use few points
- Caveat (inferred, ours): Stacks mix individually detected and undetected sources, so mean dust mass is skewed by bright sources

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging/tclean parameters and calibrated tapered maps are not described beyond weighting, taper and pixel size
- Missing: LINESTACKER version and settings, and the catalogue version used for selection, are not given
- Missing: Fit functional form and procedure are not specified
- Data volume (inferred): Tens of GB: calibrated ALCS band-6 continuum maps of 33 clusters (plus archival Frontier Fields data) if reimaged from visibilities; a few GB if using released continuum images
- Score (inferred): 3/5, Stacking recipe, dust-mass equation, assumed parameters and numeric tables are given, but imaging settings, code version and fit form are missing, and the catalogue comes from another paper
- Rediscovery candidate: yes, ALMA data are archival projects, selection and stacking recipe is largely stated and main results are tabulated numbers (stack fluxes, dust masses); needs the Kokorev2022 catalogue and LINESTACKER.

## Links

- Method: (cite: Jolly2020) (LINESTACKER stacking and bootstrap routines)
- Method: (cite: KohnoALCS) (Full description of the ALCS survey)
- Companion: (cite: Guerrero) (Companion study of cluster and z<~1 field sources in the ALCS)
- Companion: (cite: Kokorev2022) (HST-IRAC source catalogue used for stacking)
- Related: ALMA Lensing Cluster Survey (ALCS)
- Related: ALMA Frontier Fields Survey
- Related: RELICS
- Related: CLASH
- Related: Frontier Fields
- Related: COSMOS2020

## Checks

```json
{
 "quotes": 110,
 "quotes_ok": 110,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 108,
  "stated": 73,
  "rate": 0.676
 },
 "evidence_ok": true
}
```
