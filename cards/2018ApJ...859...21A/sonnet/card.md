# ALMA Survey of Lupus Protoplanetary Disks. II. Gas Disk Radii

`2018ApJ...859...21A` | The Astrophysical Journal 2018 | first author: Ansdell, M. | arXiv: 1803.05923 | DOI: 10.3847/1538-4357/aab890

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: What are the gas disk radii of Lupus disks relative to dust radii, and what do Band 6 continuum and CO data imply for viscosity, grain growth and disk masses?  
  > "enabling measurements of gas disk radii for 22 Lupus disks; we find that gas disks are universally larger than mm dust disks by a factor of two on average" (abstract)
- Target **Lupus protoplanetary disks (95 sources, Lupus I-IV)**: coordinates per-source RA/Dec in Table 1  
  > "As in Paper I, we assume that Lupus III is located at 200 pc, while the other clouds are slightly closer at 150 pc." (2 LUPUS SAMPLE); z/distance 150 pc (Lupus I, II, IV); 200 pc (Lupus III)  
  > "As in Paper I, we assume that Lupus III is located at 200 pc, while the other clouds are slightly closer at 150 pc." (2 LUPUS SAMPLE); distance from as in Paper I (Ansdell 2016)  
  > "As in Paper I, we assume that Lupus III is located at 200 pc, while the other clouds are slightly closer at 150 pc." (2 LUPUS SAMPLE)

## Data provenance

- ALMA projects: 2015.1.00222.S, 2016.1.01239.S, 2013.1.00226.S, 2013.1.01020.S
- bands: Band 6 (1.33 mm)  
  > "We present ALMA Band 6 observations" (abstract)
- frequencies and spectral setup: Cycle 3: continuum SPWs at 234.28 and 216.47 GHz (mean 225.66 GHz); 12CO, 13CO, C18O J=2-1 windows at 230.51, 220.38, 219.54 GHz, 0.24 MHz channels  
  > "These spectral windows were centered on 230.51, 220.38, and 219.54 GHz, respectively, with bandwidths of 0.12 GHz, channel widths of 0.24 MHz, and velocity resolutions of 0.16 km s$^{-1}$." (3 ALMA OBSERVATIONS)
- continuum bandwidth: 2.00 and 1.88 GHz windows  
  > "The continuum spectral windows were centered on 234.28 and 216.47 GHz with bandwidths of 2.00 and 1.88 GHz, respectively" (3 ALMA OBSERVATIONS)
- arrays: 12-m array, 58 antennas (Cycle 3), 44 antennas (Cycle 4)  
  > "using 58 12-m antennas on baselines of 15–1110 m and 15–2483 m, respectively." (3 ALMA OBSERVATIONS)
- configurations: _not stated_
- baselines: Cycle 3: 15–1110 m and 15–2483 m; Cycle 4: 2600–16700 m  
  > "The Band 6 array configuration used 44 12-m antennas on baselines of 2600–16700 m." (3 ALMA OBSERVATIONS)
- angular resolution: ~0.25 arcsec; Cycle 3 beam 0.25x0.24 arcsec, Cycle 4 0.25x0.21 arcsec  
  > "The average continuum beam size is 0.25$\times$0.24 arcsec (36$\times$38 au at 150 pc) for our Cycle 3 observations" (4.1 1.33 mm Continuum Emission)
- max recoverable scale: _not stated_
- sensitivity: median continuum rms 0.10 mJy/beam (Cycle 3), 0.08 (Cycle 4); median 3sigma 0.30 mJy  
  > "On-source integration times were 1.2 min per target for a median continuum rms of 0.10 mJy beam$^{-1}$." (3 ALMA OBSERVATIONS)
- time on source: 1.2 min per target (Cycle 3); 2.7 min (Cycle 4)  
  > "On-source integration times were 2.7 min for a median rms of 0.08 mJy beam$^{-1}$." (3 ALMA OBSERVATIONS)
- observing dates: 24 July and 8 September 2016; 7 July 2017  
  > "on 24 July and 8 September 2016" (3 ALMA OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **VLT/X-Shooter**: stellar properties (masses, Teff, L) via cited works  
  > "evolutionary models with stellar effective temperatures ($T_{\rm eff}$) and luminosities ($L_{\star}$) estimated from VLT/X-Shooter spectra" (2 LUPUS SAMPLE)
- Other facility **ALMA Band 7 (Paper I)**: 890 um continuum for spectral indices and gas masses  
  > "By combining our 1.33 mm continuum fluxes with our previous 890 $\mu$m continuum observations" (abstract)
- Other facility **Hubble/ACS**: public optical image of J16070384-3911113 edge-on disk  
  > "publicly available Hubble/ACS optical image (Proposal ID: 14212; PI: Stapelfeldt)" (5.5.2 Secondary Sources)
- External data: Stellar masses for 76 sources  
  > "we provide stellar masses ($M_{\star}$) from (cite: 2014A&A...561A...2A) and (cite: 2017A&A...600A..20A)" (2 LUPUS SAMPLE) [from (cite: 2014A&A...561A...2A); (cite: 2017A&A...600A..20A)]
- External data: Disk PA and inclination  
  > "these values are mostly taken from (cite: 2017A&A...606A..88T)" (5.1 Disk Radii) [from (cite: 2017A&A...606A..88T); transition disks (cite: 2018arXiv180106154V)]
- External data: Band 7 continuum and 13CO/C18O data and WB14 gas mass model grid  
  > "following the methods of (cite: 2014ApJ...788...59W) and (cite: 2016ApJ...828...46A)" (5.2.2 Gas Masses) [from (cite: 2014ApJ...788...59W); (cite: 2016ApJ...828...46A)]
- External data: Mean Lupus RV 2.8±4.2 km/s  
  > "($\overline{\rm RV} = 2.8 \pm 4.2$ km s$^{-1}$), as derived for Lupus protoplanetary disks in (cite: 2017A&A...602A..33F)" (4.2 Line Emission) [from (cite: 2017A&A...602A..33F)]
- External data: Stellar accretion rates for alpha_visc  
  > "he took $M_{\star}$ and $\dot{M}_{\rm acc}$ from (cite: 2014A&A...561A...2A) and (cite: 2017A&A...600A..20A)" (6.3 Viscous Disk Evolution) [from (cite: 2014A&A...561A...2A); (cite: 2017A&A...600A..20A)]
- Simulation/model as data: Updated Facchini et al. 2017 DALI dust-evolution models (M*=0.5 Msun, Mdisk=1e-4 Msun, Rc=50 au) used to compare Rgas/Rdust  
  > "we update the (cite: 2017A&A...605A..16F) models using $M_{\star} = 0.5$ $M_{\odot}$, $T_{\star} = 4700$ K" (6.2 Dust Radial Drift?)

## Processing

### Calibration

- pipeline or manual: NRAO pipeline calibration; archival data re-run with provided pipeline scripts  
  > "Data were pipeline calibrated by NRAO and included flux, bandpass, and gain calibrations." (3 ALMA OBSERVATIONS)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Cycle 3: J1517-2422 (flux, bandpass), J1610-3958 (gain); Cycle 4: J1427-4206, J1517-2422, J1610-3958  
  > "Flux and bandpass calibrations used observations of J1517-2422 and gain calibrations used observations of J1610-3958." (3 ALMA OBSERVATIONS)
- flux scale uncertainty: 10%  
  > "We estimate an absolute flux calibration error of 10% based on variations in the flux calibrators." (3 ALMA OBSERVATIONS)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust +0.5 (continuum and lines); -1.0 for resolved structure sources  
  > "cleaning with a Briggs robust weighting parameter of $+0.5$; we use $-1.0$ when sources exhibit resolved structure" (4.1 1.33 mm Continuum Emission)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian masking of 12CO channel maps for zero-moment maps  
  > "we also re-construct the zero-moment maps using a “Keplerian masking" technique to increase the signal-to-noise ratio" (5.1 Disk Radii)
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted before cleaning line channel maps  
  > "by subtracting the continuum and cleaning with a Briggs robust weighting parameter of $+0.5$" (4.2 Line Emission)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.25x0.24 arcsec (Cycle 3), 0.25x0.21 arcsec (Cycle 4)  
  > "0.25$\times$0.21 arcsec (36$\times$32 au at 150 pc) for our Cycle 4 observations" (4.1 1.33 mm Continuum Emission)
- final rms: per-source rms from 4–9 arcsec annulus (Table 1)  
  > "derived from a 4–9$^{\prime\prime}$ radius annulus centered on the fitted or expected source position" (4.1 1.33 mm Continuum Emission)

### Inherited from earlier work

- Distances: Lupus III 200 pc, others 150 pc  
  > "As in Paper I, we assume that Lupus III is located at 200 pc" (2 LUPUS SAMPLE) [from Paper I (cite: 2016ApJ...828...46A)]
- Keplerian masking technique details  
  > "see the Appendixes in (cite: 2017A&A...606A.125S) and Trapman et al., in prep, for detailed descriptions of the Keplerian masking technique" (5.1 Disk Radii) [from (cite: 2017A&A...606A.125S); Trapman et al., in prep]
- Gas mass derivation using WB14 grids  
  > "Here we apply the same method to derive bulk gas masses using our Band 6 observations" (5.2.2 Gas Masses) [from (cite: 2014ApJ...788...59W); Paper I]
- Monte Carlo treatment of unknown stellar masses in Mdust-M* fit  
  > "Using the same Monte Carlo method from Paper I to account for the 19 sources with unknown stellar masses" (5.2.1 Dust Masses) [from Paper I (cite: 2016ApJ...828...46A)]
- Dust mass assumptions (Tdust=20 K, kappa, beta=1)  
  > "We take the dust grain opacity, $\kappa_{\nu}$, as 10 cm$^{2}$ g$^{-1}$ at 1000 GHz and use an opacity power-law index of $\beta_{\rm d} =1.0$" (5.2.1 Dust Masses) [from (cite: 1990AJ.....99..924B); (cite: 2005ApJ...631.1134A)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, deconvolver, threshold/niter for tclean
- CASA/pipeline version
- Line-free channels and velocity ranges per source for continuum subtraction and moment maps
- Keplerian mask parameters (mask width, stellar mass/inclination inputs, SNR clip)
- Band 7 fluxes used for alpha_mm (van Terwisga in prep)
- Details of WB14 model grid matching and luminosity conversions
- Stellar accretion rates per source and Td, mu used in alpha_visc
- Sensitivity of Rgas to noise treatment in curve-of-growth (aperture steps)

## Analysis recipe

1. **Image continuum and measure fluxes**: Continuum images via channel averaging and cleaning; flux from uvmodelfit elliptical Gaussian (point source if a/sigma<5); aperture photometry for resolved sources  
  > "We primarily measure continuum flux densities by fitting elliptical Gaussians to the visibility data with *uvmodelfit* in CASA." (4.1 1.33 mm Continuum Emission)
   - software: CASA, uvmodelfit
   - parameter: robust +0.5 or -1.0  
  > "Briggs robust weighting parameter of $+0.5$; we use $-1.0$ when sources exhibit resolved structure" (4.1 1.33 mm Continuum Emission)
   - fitting: Uncertainties scaled by sqrt of reduced chi2  
  > "We scale the uncertainties on the fitted parameters by the square root of the reduced $\chi^{2}$ value of the fit." (4.1 1.33 mm Continuum Emission)
   - validation: _not stated_
2. **Measure CO line fluxes**: Zero-moment maps from velocity channels with emission; aperture photometry; upper limits 3x uncertainty  
  > "Zero-moment maps are created by integrating over the velocity channels showing line emission above the noise." (4.2 Line Emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure dust and gas radii with Keplerian masking**: Curve-of-growth with elliptical apertures to 90% of total flux on continuum and Keplerian-masked 12CO zero-moment maps  
  > "successively larger photometric apertures are applied until the measured flux is 90% of the total flux" (5.1 Disk Radii)
   - parameter: PA and i from Tazzari 2017 / van der Marel 2018  
  > "these values are mostly taken from (cite: 2017A&A...606A..88T)" (5.1 Disk Radii)
   - fitting: _not stated_
   - validation: Compared Rdust to Rout of Tazzari 2017 (ratio 1.06, sd 0.37); tested 68% threshold and circular apertures  
  > "the average ratio is 1.06 with a standard deviation of 0.37." (5.1 Disk Radii)
4. **Derive dust and gas masses and fit Mdust-M***: Optically thin isothermal Mdust; gas mass from WB14 grid matching of 13CO and C18O; Kelly (2007) Bayesian linear regression  
  > "we also fit the $M_{\rm dust}$–$M_{\star}$ relation using the Bayesian linear regression method of (cite: 2007ApJ...665.1489K)" (5.2.1 Dust Masses)
   - software: linmix (Kelly 2007 method)
   - assumption: Tdust=20 K, kappa=10 cm2/g at 1000 GHz, beta=1.0, optically thin  
  > "characteristic dust temperature of $T_{\rm dust}=20$ K" (5.2.1 Dust Masses)
   - fitting: Bayesian linear regression with upper limits, errors on both axes, intrinsic scatter  
  > "to take into account upper limits, error bars on both axes, and intrinsic scatter in the data" (5.2.1 Dust Masses)
   - validation: Compared with Band 7 results from Paper I  
  > "These fitted parameters are nearly identical to (and well within the errors of) those derived from our Band 7 observations in Paper I." (5.2.1 Dust Masses)
5. **Stack non-detections**: Center images on expected positions, normalize to 150 pc, circular aperture photometry on stacks  
  > "Before stacking the non-detections, we center each image on the expected source location and normalize the flux to 150 pc." (5.3 Stacked Analysis)
   - fitting: _not stated_
   - validation: Checked average offsets of detections smaller than beam  
  > "both smaller than the beam size" (5.3 Stacked Analysis)
6. **Compute spectral index alpha_mm and alpha_visc**: alpha_mm from 890 um and 1.33 mm fluxes with propagated errors; alpha_visc from Mdot/Md * mu/(kT) * Omega r^2 using r=Rgas; piecewise linear fit and Spearman test  
  > "calculate uncertainties by propagating the errors on the flux measurements, which include both the statistical error and the 10% flux calibration uncertainty" (6.1 Dust Grain Growth)
   - assumption: Md = 100 Mdust, Td = 20 K (following Rafikov 2017)  
  > "He assumed $M_{\rm d} = 100~M_{\rm dust}$" (6.3 Viscous Disk Evolution)
   - fitting: Piecewise linear fit of alpha_mm vs log F  
  > "we fit the data with a piecewise linear relation" (6.1 Dust Grain Growth)
   - validation: Spearman rank test; sensitivity limits shown  
  > "which gives a probability of no correlation of $p = 0.005$" (6.1 Dust Grain Growth)
7. **Limit optically thick emission radius**: Integrate blackbody flux from Rsub to Rthick with T from stellar luminosity until matching central peak flux  
  > "We then integrate outwards until we match the observed central peak flux density in a beam centered on the stellar position" (6.4 Limits on the size of optically thick emission)
   - assumption: Tsub=1500 K; <cos i>=2/pi for unresolved disks  
  > "we use a mean value of $\langle \cos\,i\rangle = 2/\pi$" (6.4 Limits on the size of optically thick emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : uvmodelfit visibility fitting of continuum fluxes  
  > "fitting elliptical Gaussians to the visibility data with *uvmodelfit* in CASA" (4.1 1.33 mm Continuum Emission)
- **DALI** : thermo-chemical models (Facchini 2017) updated for Lupus-like disks  
  > "combined the dust evolution models from (cite: 2015ApJ...813L..14B) with the thermo-chemical code DALI" (6.2 Dust Radial Drift?)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean Rgas/Rdust | 1.96 | 0.04 | dimensionless | 3 | by an average factor of $1.96\pm0.04$ |
| Continuum detections | 71 of 95 | not stated | sources | 1 | Of the 95 sources, 71 are detected with $>3\sigma$ significance |
| Mdust-M* relation slope | 1.8 | 0.3 | dimensionless | 4 | {\rm log} (M_{\rm dust} ) = 1.3 (\pm0.2) + 1.8 (\pm0.3)  \times {\rm log} (M_{\star}) |
| Median alpha_mm (excl. resolved TDs) | 2.25 | not stated | dimensionless | 6 | The median $\alpha_{\rm mm}$ value is 2.25 |
| alpha_visc range | 0.0003 to 0.09 | not stated | dimensionless | 6 | from $0.0003$ to $0.09$ |
| Median Rthick (detections) | 3.8 | not stated | au | 7 | with a median of 3.8 au for the detected disks |
| Stacked continuum non-detections | 0.00 | 0.04 | mJy | 5 | we measure a mean signal of $0.00\pm0.04$ mJy |

## Qualitative findings

- Gas disks are universally larger than dust disks; due to optically thick CO and dust growth/drift  
  > "gas disks are universally larger than mm dust disks by a factor of two on average" (abstract)

## Claim tuples

- H: Are gas disks larger than dust disks across a population? | E: Curve-of-growth radii from continuum and Keplerian-masked 12CO for 22 disks | R: Rgas/Rdust = 1.96±0.04, robust to 68% threshold and circular apertures | F: Gas disks universally larger, from optical depth plus growth and drift | **supported**
- H: Is alpha_mm dependent on disk mass? | E: Combine Band 6 and Band 7 fluxes for 70 disks | R: Anti-correlation for low-mass disks, flattening near 2 above ~5 Earth masses | F: May indicate faster grain growth or larger optically thick regions | **partially**
- H: Do disks show viscous evolution signatures via alpha_visc? | E: alpha_visc with Rgas for 22 disks | R: Broad distribution 0.0003–0.09, no correlations | F: Viscous quasi-steady state not established; sample small and biased | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Keplerian masking boosts SNR of faint outer 12CO  
  > "Masking the pixels outside of these regions in each velocity channel therefore enhances the SNR in the final integrated zero-moment map." (5.1 Disk Radii)
- How they decided it was enough: _not stated_
- Limitation (authors): Disks with measured radii are a small sample biased to the highest-mass disks  
  > "these sub-samples of resolved Lupus disks are not only small, but also heavily biased towards the highest-mass disks" (6.3 Viscous Disk Evolution)
- Limitation (authors): Models lack kinematics and observational noise  
  > "the models currently do not include simulated observational noise, which can affect the measured radii" (6.2 Dust Radial Drift?)
- Caveat (inferred, ours): Rgas by curve-of-growth is sensitive to noise and masking
- Caveat (inferred, ours): Single-temperature dust mass and WB14 gas masses carry large systematic uncertainty
- Caveat (inferred, ours): Optical depth versus drift not separated

## Reproducibility

- Data public (paper): Data in ALMA archive with listed IDs  
  > "have Band 6 continuum observations as well as $^{12}$CO, $^{13}$CO, and C$^{18}$O $J=2$–1 line observations in the ALMA archive" (3 ALMA OBSERVATIONS)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: Keplerian masking code and parameters
- Missing: Band 7 data products and stellar accretion rates
- Missing: Gas mass model grid details
- Data volume (inferred): ~100–300 GB raw for four projects
- Score (inferred): 3/5, Data public and flux/radius methods clear, but masking, imaging details and external inputs are incomplete.
- Rediscovery candidate: no, Keplerian masking details are deferred to in-prep work and key inputs come from other papers.

## Links

- Method: (cite: 2017A&A...606A.125S) (Keplerian masking technique)
- Method: (cite: 2014ApJ...788...59W) (gas mass model grid)
- Method: (cite: 2007ApJ...665.1489K) (Bayesian linear regression)
- Companion: (cite: 2016ApJ...828...46A) (Paper I, Band 7 Lupus survey)
- Companion: (cite: 2017A&A...606A..88T) (Band 7 disk modeling providing PA, inclination)
- Companion: (cite: 2018arXiv180106154V) (Lupus transition disks)
- Related: ALMA Lupus survey Paper I (Band 7)

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 61,
  "rate": 0.693
 },
 "evidence_ok": true
}
```
