# Uncovering the structure and kinematics of the ionized core of M 2-9 with ALMA

`2024A&A...692A.151S` | Astronomy and Astrophysics 2024 | first author: Sánchez Contreras, C. | arXiv: 2411.03825 | DOI: 10.1051/0004-6361/202451669

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the structure, kinematics and physical conditions of the nascent compact ionized core (wind/jet) of the pPN/yPN candidate M 2-9, probed at 1 and 3 mm continuum and the H30alpha and H39alpha mRRLs down to ~0.03 arcsec?  
  > "In this work, we present an ALMA-based study of the nascent compact ionized region at the center of the pPN/yPN candidate M 2-9." (Introduction)
- Target **M 2-9**: coordinates RA 17h05m37.9668s, Dec -10d08m32.65s (J2000), peak of the 3 mm continuum  
  > "The peak surface brightness of the 3 mm continuum is located at coordinates R.A.=17$^{\rm h}$05$^{\rm m}$37.9668s and Dec.=$-$10$^\circ$08$'$32$.\!\!^{\prime\prime}$65 (J2000)" (Continuum emission); "In this study, we adopt a distance of 650 pc for M 2-9, which is based on the analysis of the proper motions of the optical knots by (cite: sch97)" (M 2-9); z/distance 650 pc (literature range 50 pc to 3 kpc)  
  > "The peak surface brightness of the 3 mm continuum is located at coordinates R.A.=17$^{\rm h}$05$^{\rm m}$37.9668s and Dec.=$-$10$^\circ$08$'$32$.\!\!^{\prime\prime}$65 (J2000)" (Continuum emission); "In this study, we adopt a distance of 650 pc for M 2-9, which is based on the analysis of the proper motions of the optical knots by (cite: sch97)" (M 2-9); distance from proper motions of optical knots (cite: sch97) and spatio-kinematics of the molecular rings (cite: cc12)  
  > "The peak surface brightness of the 3 mm continuum is located at coordinates R.A.=17$^{\rm h}$05$^{\rm m}$37.9668s and Dec.=$-$10$^\circ$08$'$32$.\!\!^{\prime\prime}$65 (J2000)" (Continuum emission); "In this study, we adopt a distance of 650 pc for M 2-9, which is based on the analysis of the proper motions of the optical knots by (cite: sch97)" (M 2-9)

## Data provenance

- ALMA projects: 2016.1.00161.S, 2017.1.00376.S
- bands: Band 3 (3 mm) and Band 6 (1 mm), twelve SPWs  
  > "The observations were carried out in Band 3 (3 mm) and Band 6 (1 mm), with a total of twelve different spectral windows (SPWs) dedicated to mapping the emission of various mRRLs (and CO lines) as well as the continuum" (Observations and data reduction)
- frequencies and spectral setup: 12 SPWs, see Table 1 (Band 3 centers 95.350-110.201 GHz; Band 6 centers 215.400-232.900 GHz; channel widths 0.3-3 km/s)  
  > "Central frequency, bandwidth, velocity resolution, detected spectral lines and continuum fluxes in the different spectral windows (SPWs)." (Table 1)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array, 45-50 antennas  
  > "The observations utilized 45-50 antennas, with baselines ranging from 41.4 m to 16.2 km for Band 3, and from 113.0 m to 13.9 km for Band 6." (Observations and data reduction)
- configurations: _not stated_
- baselines: 41.4 m to 16.2 km (Band 3); 113.0 m to 13.9 km (Band 6)  
  > "with baselines ranging from 41.4 m to 16.2 km for Band 3, and from 113.0 m to 13.9 km for Band 6." (Observations and data reduction)
- angular resolution: ~40x30 mas at 1 mm; ~90x60 mas at 3 mm  
  > "resulting in angular resolutions of $\sim$40$\times$30 mas at 1 mm and $\sim$90$\times$60 mas at 3 mm" (Observations and data reduction)
- max recoverable scale: ~0.8 arcsec (3 mm), ~0.7 arcsec (1 mm)  
  > "The maximum recoverable scale (MRS) of the observations is $\sim$0$.\!\!^{\prime\prime}$8 and $\sim$0$.\!\!^{\prime\prime}$7 at 3 and 1 mm, respectively." (Observations and data reduction)
- sensitivity: continuum rms ~25-85 uJy/beam (Band 3) and ~60-100 uJy/beam (Band 6); cube rms ~1 mJy/beam (1 mm) and 0.80 mJy/beam (3 mm) at 3 km/s  
  > "The rms noise level range in the continuum maps is $\sim$25-85 $\mu$Jy beam$^{-1}$ and $\sim$60-100 $\mu$Jy beam$^{-1}$ for the individual SPWs within Band 3 and Band 6, respectively." (Observations and data reduction); "The typical rms noise level per channel of our spectral cubes is $\sigma$$\sim$1 mJy beam$^{-1}$ (1 mm) and 0.80 mJy beam$^{-1}$ (3 mm) at 3 km s$^{-1}$ resolution." (Observations and data reduction)
- time on source: about 49 min (Band 3), 33 min (Band 6)  
  > "The total time spent on the science target, M 2-9, was about 49 min in Band 3 and 33 min in Band 6." (Observations and data reduction)
- observing dates: Band 3 on 2017-10-15; Band 6 on 2017-11-12 (two execution blocks of ~1.5 and ~1.1 hr)  
  > "The Band 3 and Band 6 observations were conducted separately in two different execution blocks, with a duration of approximately 1.5 and 1.1 hr, in October and November 2017, respectively." (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: H (mRRL) H30alpha (231.900 GHz (Table 2))
- Line: H (mRRL) H39alpha (106.737 GHz (Table 2))
- Line: He (mRRL) He30alpha (231.995 GHz (Table 2))
- Line: H (mRRL) H55gamma (109.536 GHz (Table 2))
- Line: 12CO J=2-1 (230.538 GHz (Table 1 SPW center))
- Line: 13CO J=1-0 (not stated)
- Other facility **IRAM-30 m**: earlier single-dish H30alpha and H39alpha mRRL spectra (CSC17) compared with the ALMA profiles  
  > "A recent pilot study of millimeter radio recombination lines (mRRLs) in a sample of pPNe/yPNe with the IRAM-30 m radiotelescope (cite: san17)" (Introduction)
- Other facility **JVLA**: 7 mm continuum maps (last observed 2006) used for comparison of the C-shaped curvature  
  > "The orientation of the C-shaped curvature in our maps is the same as in the JVLA maps of the 7 mm-continuum emission last observed in 2006 (cite: dlF22)." (Continuum emission)
- Other facility **VLTI/MIDI**: mid-IR interferometry confirming a compact disk (cite: lyk11)  
  > "was further supported by (cite: lyk11), who used mid-IR interferometry to confirm the presence of a compact disk" (Spectral energy distribution: free-free and dust continuum emission)
- External data: Input physical model of M 2-9 from the single-dish study CSC17 (their Table 4), used as the starting model  
  > "began by employing the identical physical model utilized by CSC17 (see their Table 4)." (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission) [from CSC17 (cite: san17)]
- External data: Non-LTE departure coefficients b_n (Case B tables)  
  > "are obtained from the tables provided by (cite: sto95) for Case B." (The non-ETL free-free continuum and mRRL radiative transfer code) [from Storey & Hummer 1995 (cite: sto95)]
- External data: Distance of 650 pc  
  > "In this study, we adopt a distance of 650 pc for M 2-9, which is based on the analysis of the proper motions of the optical knots by (cite: sch97)" (M 2-9) [from (cite: sch97); (cite: cc12)]
- External data: Inclination of ~17 deg to the line of sight from the CO rings  
  > "inclined by $i$$\sim$17$^\circ$ with respect to the line of sight" (M 2-9) [from (cite: cc12; cc17)]
- External data: Mid-IR image of an unresolved central core (compact dust component, ~260 K fit)  
  > "the mid-IR images of M 2-9 reported by (cite: smg05) revealed the presence of an unresolved central core" (Spectral energy distribution: free-free and dust continuum emission) [from Smith & Gehrz 2005 (cite: smg05)]
- External data: CO-to-H2 abundance X_CO = 2e-4 adopted for the absorbing layers  
  > "which is typical of O-rich sources (cite: ram18)" (Disk physical conditions) [from (cite: ram18)]
- External data: Grid of early B-type star model atmospheres (Lyman continuum output) used to compare with the required N_LyC  
  > "This value has been compared with the Lyman continuum output rate from the grid of model atmospheres of early B-type stars by (cite: lan07) to investigate the central ionizing source." (Ionizing central source) [from Lanz & Hubeny 2007 (cite: lan07)]
- Simulation/model as data: Synthetic ALMA-like cubes of the CSC17 single-dish model (93 GHz continuum, H30alpha, H39alpha) compared with the ALMA data  
  > "we show synthetic ALMA-like cubes representing emission from 93 GHz free-free continuum" (Comparison of CSC17 model for M 2-9 with new ALMA maps)

## Processing

### Calibration

- pipeline or manual: automated ALMA pipeline initial calibration, followed by self-calibration  
  > "An initial calibration of the data was performed using the automated ALMA pipeline of the Common Astronomy Software Applications" (Observations and data reduction)
- casa version: CASA 4.7.2 and 5.1.1  
  > "versions 4.7.2 and 5.1.1" (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J 1751+0939: 1.95 Jy at 108.970 GHz and 1.38 Jy at 231.845 GHz, spectral index -0.294  
  > "The flux density adopted for J 1751+0939 is 1.95 Jy at 108.970 GHz" (Observations and data reduction); "and and 1.38 Jy at 231.845 GHz with the same spectral index." (Observations and data reduction)
- flux scale uncertainty: ~10%  
  > "The absolute calibration uncertainties, estimated at around 10%, were determined by comparing" (Observations and data reduction)
- self calibration: self-calibration with an initial source model from the standard calibration, done in GILDAS MAPPING  
  > "we self-calibrated our data using the initial model of the source derived from the standard calibration to improve the sensitivity and fidelity of the images." (Observations and data reduction); "Self-calibration as well as image restoration and deconvolution was done using the GILDAS" (Observations and data reduction)

### Imaging

- task: GILDAS MAPPING (restoration and deconvolution)  
  > "Self-calibration as well as image restoration and deconvolution was done using the GILDAS" (Observations and data reduction)
- deconvolver: Hogbom  
  > "using the Hogbom deconvolution method with a robust weighting scheme" (Observations and data reduction)
- weighting robust: robust threshold = 0.5 in MAPPING  
  > "We used a value of 0.5 for the threshold of the robust weighting in MAPPING." (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum of the SPW containing the line subtracted from that SPW  
  > "Line emission cubes were constructed by subtracting the corresponding continuum data from each SPW, specifically subtracting the continuum of the SPW containing the specific line of interest." (Observations and data reduction)
- line free channels: line-free channels identified from calibrated data, used to make continuum images of each of the 12 SPWs (ranges not given)  
  > "Continuum images were generated for each of the 12 SPWs by utilizing line-free channels." (Observations and data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: continuum maps also restored with a circular beam of 40 mas at 1 mm and 3 mm  
  > "Continuum maps with a circular restoring beam of half power beam width (HPBW) of 40 mas at 1 mm and 3 mm were also created to facilitate a better comparison between the two images." (Observations and data reduction)
- final beam: ~40x30 mas (1 mm), ~90x60 mas (3 mm)  
  > "resulting in angular resolutions of $\sim$40$\times$30 mas at 1 mm and $\sim$90$\times$60 mas at 3 mm" (Observations and data reduction)
- final rms: cube rms ~1 mJy/beam (1 mm), 0.80 mJy/beam (3 mm) at 3 km/s; continuum rms ~25-85 uJy/beam (Band 3), ~60-100 uJy/beam (Band 6)  
  > "The typical rms noise level per channel of our spectral cubes is $\sigma$$\sim$1 mJy beam$^{-1}$ (1 mm) and 0.80 mJy beam$^{-1}$ (3 mm) at 3 km s$^{-1}$ resolution." (Observations and data reduction)

### Inherited from earlier work

- Starting physical model for the non-LTE modeling is the single-dish CSC17 model  
  > "began by employing the identical physical model utilized by CSC17 (see their Table 4)." (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission) [from CSC17 (cite: san17)]
- Adopted distance of 650 pc chosen to allow direct comparison with CSC17  
  > "This distance choice allows for a direct comparison with the study conducted by CSC17 on the nascent ionized core of M 2-9." (M 2-9) [from CSC17 (cite: san17)]
- Method for constraining excitation temperature and opacity from the CO absorption follows the NaCl absorption analysis of OH 231.8+4.2  
  > "As shown in detail, for example, by (cite: san22) in their analysis of the compact NaCl absorption feature observed at the central rotating disk of the post-AGB nebula" (Disk physical conditions) [from (cite: san22)]
- Free-free Gaunt factor formulation taken from earlier work  
  > "Following (cite: bae13), the Gaunt factor for free-free transitions is calculated in the following way:" (The non-ETL free-free continuum and mRRL radiative transfer code) [from (cite: bae13)]
- Formula for the Lyman continuum photon rate from free-free flux  
  > "As is well known (cite: con16), the number of Lyman continuum photons emitted per second" (Ionizing central source) [from (cite: con16)]

### Not stated but needed to reproduce (our reading)

- GILDAS MAPPING parameters: cell size, image size, clean mask, number of iterations or threshold, uv-range and what robust threshold 0.5 means numerically
- Self-calibration details: solution intervals, number of iterations, amplitude versus phase, and the initial model used
- Line-free channel ranges per SPW and the order or degree of continuum subtraction
- Which execution blocks, MOUS and SPWs belong to each of the two project codes, and the pipeline version
- Flagging applied after the ALMA pipeline and whether archive pipeline products or a re-run were used
- How the source-integrated line profiles were extracted (aperture or mask) and the Gaussian fitting setup
- How the SED decomposition (free-free plus ~200-300 K dust with emissivity 0.2-0.5) was fitted, and its error estimation
- Co3RaL source code, grid setup and exact functional forms (C-shaped horn curvature, position angle, step functions) of the final model
- The ~300 trial models and the criterion for a reasonable match (no quantitative goodness of fit)
- RADEX inputs for the CO absorption (kinetic temperature, background, collision partner, line width treatment)
- Rest frequencies adopted for each line and the velocity reference frame used for the cubes

## Analysis recipe

1. **calibrate and self-calibrate the visibilities**: ALMA pipeline calibration in CASA, then self-calibration with an initial source model in GILDAS MAPPING  
  > "we self-calibrated our data using the initial model of the source derived from the standard calibration to improve the sensitivity and fidelity of the images." (Observations and data reduction)
   - software: CASA, GILDAS MAPPING
   - parameter: flux calibrator J 1751+0939 adopted at 1.95 Jy at 108.970 GHz  
  > "The flux density adopted for J 1751+0939 is 1.95 Jy at 108.970 GHz" (Observations and data reduction)
   - assumption: no significant complex large-scale structure, so a point-like initial model is adequate for self-calibration  
  > "the absence of significant/complex large-scale structure in M 2-9 in our observations" (Observations and data reduction)
   - fitting: _not stated_
   - validation: calibration uncertainty (~10%) from comparing continuum fluxes of phase, check and flux calibrators before and after self-calibration with pipeline values  
  > "The absolute calibration uncertainties, estimated at around 10%, were determined by comparing" (Observations and data reduction)
2. **image the continuum and mRRL/CO cubes and measure fluxes and line parameters**: continuum maps per SPW from line-free channels; continuum flux integrated in a circular aperture; line cubes continuum-subtracted; Gaussian fits to source-integrated line profiles  
  > "Flux measurements of the continuum emission for each SPW were obtained integrating the surface brightness within a circular aperture" (Observations and data reduction); "Line parameters from Gaussian fitting to the source-integrated profiles of the mRRLs in this study." (Table 2)
   - software: GILDAS MAPPING
   - parameter: aperture radius 0.25 arcsec  
  > "with a radius of 0$.\!\!^{\prime\prime}$25 fully enclosing the continuum source" (Observations and data reduction)
   - parameter: Hogbom deconvolution with robust weighting (threshold 0.5)  
  > "using the Hogbom deconvolution method with a robust weighting scheme" (Observations and data reduction)
   - fitting: Gaussian fits (sampler, priors, likelihood not stated)  
  > "Line parameters from Gaussian fitting to the source-integrated profiles of the mRRLs in this study." (Table 2)
   - validation: _not stated_
3. **fit the mm SED and separate free-free from dust**: power-law fit to the 1-3 mm fluxes; then a combination of ~200-300 K dust plus a free-free power law, with the ~260 K compact-disk dust subtracted from the total  
  > "Under the assumption that a fraction of the mm-continuum flux observed with ALMA originates from the warm" (Spectral energy distribution: free-free and dust continuum emission)
   - parameter: spectral index 0.92 +/- 0.1 for the ALMA band fluxes; free-free component index 0.89  
  > "yields $S_\nu$ $\propto$ $\nu^{0.92\pm 0.1}$" (Spectral energy distribution: free-free and dust continuum emission); "a free-free component that varies as $S_\nu$ $\propto$ $\nu^{0.89}$" (Spectral energy distribution: free-free and dust continuum emission)
   - assumption: compact warm (~260 K) disk contributes to the mm continuum and is not affected by interferometric flux loss  
  > "Unlike the emission from the extended dust structures mentioned in the previous paragraph, the emission from this compact disk is not expected to be affected by interferometric flux losses in our ALMA maps." (Spectral energy distribution: free-free and dust continuum emission)
   - fitting: _not stated_
   - validation: described as a rough estimate; compared with single-dish fluxes (about 20% flux loss) and with the cm-wavelength continuum  
  > "is subject to uncertainties and should be considered as a rough estimate" (Spectral energy distribution: free-free and dust continuum emission)
4. **model the ionized wind with non-LTE 3D radiative transfer**: forward modeling of continuum and H30alpha/H39alpha cubes with Co3RaL, starting from the CSC17 model and adjusting parameters by hand to match the ALMA maps, PV diagrams and SED  
  > "To obtain an improved model that fits these new details, we progressively adjusted the parameters of the input model" (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission)
   - software: Co3RaL
   - parameter: Te ~ 15000 K, constant  
  > "The value deduced $T_{\rm e}$$\sim$15000 K" (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission)
   - parameter: inclination i = 12 deg (models around 17 deg examined)  
  > "with the most successful models having an inclination of $i$=12$^\circ$" (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission)
   - parameter: R_out ~ 40 au, R_eq ~ 8 au  
  > "a much narrower bipolar structure (particularly an outer radius value of $R_{\rm out}$$\sim$40 au)" (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission); "a narrow waist at the base of the wind ($R_{\rm eq}$$\sim$8 au)" (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission)
   - parameter: high-velocity shells: velocity rises from ~70 to ~90 km/s; ~10 km/s inside ~15 au  
  > "within the HVSs, the velocity rises from $\sim$70 to $\sim$90 km s$^{-1}$" (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission)
   - assumption: constant electron temperature across the wind  
  > "To simplify, we maintain a constant value for the electron temperature throughout the various regions of the wind." (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission)
   - assumption: distance 650 pc  
  > "In this study, we adopt a distance of 650 pc for M 2-9" (M 2-9)
   - assumption: constant rotation velocity because resolution cannot distinguish Keplerian from momentum-conserving profiles  
  > "Since the angular resolution of the data does not allow us to distinguish between Keplerian or momentum conservation velocity profiles" (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission)
   - assumption: no turbulent line broadening  
  > "turbulence velocity dispersion is not considered as an additional form of line broadening" (The non-ETL free-free continuum and mRRL radiative transfer code)
   - fitting: manual iterative adjustment; no sampler, priors or likelihood  
  > "until a reasonable match was achieved between the model predictions and the data" (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission)
   - validation: Co3RaL benchmarked against MORELI with identical inputs; the authors state no comprehensive parameter-space study was done  
  > "This comparison serves as a mutual benchmarking exercise of both codes." (Comparison of Co3RaL with MORELI); "Although a comprehensive parameter space study has not been performed and is beyond the scope of this paper" (Model caveats and final modeling remarks)
5. **derive disk conditions from the CO absorption**: compare on-source absorption brightness, off-source emission and continuum peak to get Tex and tau; RADEX for N_CO; scale to N_H2 with an assumed abundance; infall mass from the redshift of the absorption  
  > "the presence of absorption enables constraining the excitation temperature and opacity of the absorption line observed." (Disk physical conditions); "we used the on-line version of the non-LTE line radiative transfer code RADEX" (Disk physical conditions)
   - software: RADEX
   - parameter: Tex <~ 330 K, tau ~ 0.16  
  > "we deduce $T_{\rm ex}$$\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$330 K and $\tau$$\sim$0.16." (Disk physical conditions)
   - assumption: X_CO = 2e-4 (O-rich), likely overestimated by photodissociation  
  > "which is typical of O-rich sources (cite: ram18)" (Disk physical conditions)
   - assumption: gas falls in from near zero velocity from far beyond the infall radius  
  > "assuming that the gas started falling with (near) zero velocity from a point much far beyond the observed infall radius." (Disk kinematics)
   - assumption: average disk density similar to OH 231.8+4.2 disk (n_H2 ~ 1e8 cm-3)  
  > "Assuming the average density of both disks is similar" (Disk physical conditions)
   - fitting: _not stated_
   - validation: alternative rotation explanation for the redshift tested and rejected (implies >30 Msun)  
  > "Such a high velocity would imply an unreasonably massive central object, exceeding 30 $M_{\odot}$." (Disk kinematics)
6. **constrain the ionizing source**: compute the Lyman continuum photon rate from the free-free flux and compare with B-star and WD model atmospheres  
  > "can be computed using the measured value of the free-free continuum flux" (Ionizing central source)
   - parameter: free-free continuum 102.80 mJy at 95.3 GHz after subtracting the 260 K dust  
  > "a free-free continuum of 102.80 mJy at 95.3 GHz" (Ionizing central source)
   - assumption: Te ~ 15000 K, d = 650 pc  
  > "For an electron temperature of" (Ionizing central source)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2 and 5.1.1: automated ALMA pipeline initial calibration  
  > "An initial calibration of the data was performed using the automated ALMA pipeline of the Common Astronomy Software Applications" (Observations and data reduction)
- **GILDAS MAPPING** : self-calibration, image restoration and deconvolution  
  > "Self-calibration as well as image restoration and deconvolution was done using the GILDAS" (Observations and data reduction)
- **Co3RaL** : non-LTE 3D radiative transfer modeling of free-free continuum and mRRLs (authors' own code)  
  > "is a C-based code designed to calculate the intensity of the free-free continuum and recombination line emission originating from an ionised nebula." (The non-ETL free-free continuum and mRRL radiative transfer code)
- **MORELI** : code used by CSC17 for the single-dish model; benchmarked against Co3RaL  
  > "MORELI is the code used in the analysis by CSC17 (cite: bae13)." (Footnote 6)
- **RADEX** : CO column density from the CO absorption (on-line version)  
  > "we used the on-line version of the non-LTE line radiative transfer code RADEX" (Disk physical conditions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum spectral index (1-3 mm) | 0.92 | +/-0.1 | dimensionless | 3 | yields $S_\nu$ $\propto$ $\nu^{0.92\pm 0.1}$ |
| Free-free component spectral index | 0.89 | not stated | dimensionless | 3 | a free-free component that varies as $S_\nu$ $\propto$ $\nu^{0.89}$ |
| Interferometric flux loss relative to single-dish mm fluxes | ~20 | not stated | percent | 3 | reveals flux losses of approximately 20% in our high-resolution interferometric measurements |
| H30alpha line parameters (Freq, integrated flux, V_LSR, FWHM, peak) | 231.900 GHz; 13.3 Jy km/s; 73.0 km/s; 44.9 km/s; 280 mJy | +/-0.3; +/-0.4; +/-0.9; +/-5 | GHz; Jy km/s; km/s; km/s; mJy | 2 | H30$\alpha$ / 231.900 / 13.3$\pm$0.3 / 73.0$\pm$0.4 / 44.9$\pm$0.9 / 280$\pm$5 |
| H39alpha line parameters (Freq, integrated flux, V_LSR, FWHM, peak) | 106.737 GHz; 2.07 Jy km/s; 75.1 km/s; 54.0 km/s; 36 mJy | +/-0.08; +/-0.7; +/-1.7; +/-1 | GHz; Jy km/s; km/s; km/s; mJy | 2 | H39$\alpha$ / 106.737 / 2.07$\pm$0.08 / 75.1$\pm$0.7 / 54.0$\pm$1.7 / 36$\pm$1 |
| He30alpha line parameters (Freq, integrated flux, V_LSR, FWHM, peak) | 231.995 GHz; 0.96 Jy km/s; 71.5 km/s; 44 km/s; 20 mJy | +/-0.07; +/-1.0; +/-3; +/-1 | GHz; Jy km/s; km/s; km/s; mJy | 2 | He30$\alpha$ / 231.995 / 0.96$\pm$0.07 / 71.5$\pm$1.0 / 44$\pm$3 / 20$\pm$1 |
| H55gamma line parameters (Freq, integrated flux, V_LSR, FWHM, peak) | 109.536 GHz; 0.17 Jy km/s; 78 km/s; 50 km/s; 3.3 mJy | +/-0.05; +/-4; +/-10; +/-0.6 | GHz; Jy km/s; km/s; km/s; mJy | 2 | H55$\gamma$ / 109.536 / 0.17$\pm$0.05 / 78$\pm$4 / 50$\pm$10 / 3.3$\pm$0.6 |
| Change of H30alpha brightness relative to IRAM-30 m | factor ~2.2 in line flux, ~1.6 in peak intensity | not stated | dimensionless | 2 | a notable increase in brightness (by a factor of $\sim$2.2 in line flux and $\sim$1.6 in line peak intensity) |
| Average velocity gradient of the inner ionized wind | ~1150 | not stated | km/s per arcsec | 2 | is $\nabla \upsilon$$\sim$1150km s$^{-1}$ arcsec$^{-1}$ |
| H30alpha emission extent along the axis (3 sigma, deconvolved) | ~0.07 arcsec (~45 au at 650 pc) | not stated | arcsec | 2 | extends along the axis to a radial distance of $\sim$0$.\!\!^{\prime\prime}$07 ($\sim$45au at $d$=650pc) from the center |
| 3 mm continuum dimensions | 0.4 x 0.13 arcsec (260 x 85 au) | not stated | arcsec | 2 | with dimensions of 0$.\!\!^{\prime\prime}$4$\times$0$.\!\!^{\prime\prime}$13 (260$\times$85 au at $d$=650 pc) at 3 mm |
| Electron temperature of the ionized wind (model) | ~15000 | ~15-20% | K | 4 | The value deduced $T_{\rm e}$$\sim$15000 K |
| Ionized mass of the model wind | ~4e-6 | factor <~2-3 | Msun | 4 | $M_{\rm ion}$$\sim$4$\times 10^{\rm -6}$ $M_{\odot}$ |
| Average mass-loss rate of the ionized wind (model) | ~7e-7 | factor <~2-3 | Msun/yr | 4 | the average mass-loss rate implied from the model is $\dot{M}$$\sim$7$\times 10^{\rm -7}$ $M_{\odot}$ yr$^{-1}$ |
| Model wind inclination | 12 | not stated | deg | 4 | with the most successful models having an inclination of $i$=12$^\circ$ |
| Model wind outer radius and equatorial radius | R_out ~40 au; R_eq ~8 au | not stated | au | 4 | a much narrower bipolar structure (particularly an outer radius value of $R_{\rm out}$$\sim$40 au); a narrow waist at the base of the wind ($R_{\rm eq}$$\sim$8 au) |
| Velocity in the high-velocity shells | rises from ~70 to ~90 | not stated | km/s | 4 | within the HVSs, the velocity rises from $\sim$70 to $\sim$90 km s$^{-1}$ |
| Central system mass range from rotation and infall | 0.4 to 2 | not stated | Msun | 5 | but it is likely in the range of 0.4 to 2 $M_{\odot}$ |
| CO absorption excitation temperature and opacity | Tex <~330 K; tau ~0.16 | not stated | K; dimensionless | 5 | we deduce $T_{\rm ex}$$\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$330 K and $\tau$$\sim$0.16. |
| CO column density of the absorbing layers | <~6e17 | not stated | cm-2 | 5 | imply a CO column density of $N_{\rm CO}$$\raisebox{-.4ex}{$\stackrel{<}{\scriptstyle \sim}$}$6$\times 10^{\rm 17}$ $\,$cm$^{\rm -2}$ |
| Total H2 column density of the absorbing layers | ~3e21 | not stated | cm-2 | 5 | we derive a total column density of $N_{\rm H_2}$$\sim$3$\times 10^{\rm 21}$$\,$cm$^{\rm -2}$ |
| Equatorial disk mass | >2e-6 | lower limit | Msun | 5 | A lower limit to the mass of the disk of $>$2$\times 10^{\rm -6}$ $M_{\odot}$ is deduced. |
| Equatorial disk radius | ~50 | not stated | au | 5 | disk with a radius of $\sim$50 au |
| Deprojected redshift of CO absorption relative to the mRRL centroid | ~6.2 | not stated | km/s | 5 | The redshift of the CO absorption feature by $\sim$6.2 km s$^{-1}$ (deprojected velocity adopting $i$=17$^\circ$) |
| Central mass from infall at 27-38 au | ~0.7 | lower limit | Msun | 5 | would imply a central mass of $\sim$0.7 $M_{\odot}$ |
| Central mass if infall starts from ~50 au | ~2.0 | upper limit | Msun | 5 | then the central mass would be $\sim$2.0 $M_{\odot}$ |
| Lyman continuum photon rate | log N_LyC ~ 43.8 | not stated | s-1 | 6 | we calculate a Lyman continuum photon rate of log$N_{\rm LyC}$$\sim$43.8 s$^{-1}$ |
| Effective temperature of the ionizing star accounting for N_LyC | ~25 | not stated | kK | 6 | We find that a star with an effective temperature of around $T_{\rm eff}$$\sim$25 kK |

## Qualitative findings

- The ionized wind is collimated and shows a C-shaped curvature at 3 mm consistent with 7 mm JVLA maps taken 11 yr earlier  
  > "The ionized wind is collimated and displays a C-shaped curvature at 3 mm consistent with previous observations taken 11 yr earlier at 7 mm." (Summary and conclusions)
- The 1 mm continuum has a broad-waisted morphology perpendicular to the lobes, attributed to dust in an equatorial disk  
  > "The 1 mm-continuum map reveals a broad-waisted morphology oriented perpendicularly to the wind lobes, which is plausibly the counterpart of the compact" (Summary and conclusions)
- Short kinematic age of the wind explains year-scale mRRL profile changes  
  > "The ionized wind has a short kinematical age, including regions of less than a year old, explaining changes in the mRRL profiles on similar year-long timescales." (Summary and conclusions)

## Claim tuples

- H: Is the mm continuum of M 2-9 dominated by free-free emission from the ionized core, with a dust contribution? | E: 1 mm and 3 mm continuum imaging, SED power-law fit and free-free plus dust decomposition | R: Spectral index 0.92+/-0.1 (free-free component 0.89); 1 mm map shows a broad waist absent in H30alpha | F: Predominantly free-free emission from an ionized wind with a minor dust contribution from a warm compact disk | **supported**
- H: Does the ionized core host a compact, collimated, fast jet with structured density and velocity? | E: H30alpha and H39alpha cubes and PV diagrams, compared with non-LTE Co3RaL models | R: S-shaped axial PV diagrams requiring dense high-velocity shells at ~15-30 au with ~70-90 km/s; model Te ~15000 K, Mdot ~7e-7 Msun/yr | F: A compact bent jet with velocities up to ~80 km/s and non-uniform density | **supported**
- H: Is there an equatorial disk around the ionized wind? | E: CO and 13CO absorption against the continuum, the 1 mm broad waist, and RADEX analysis | R: narrow redshifted CO absorption offset north by ~0.012 arcsec; Tex <~330 K, tau ~0.16; disk radius ~50 au, mass >2e-6 Msun | F: A likely circumbinary equatorial disk with gas infall toward the center | **supported**
- H: Has the wind changed between the 2015 IRAM-30 m and the 2017 ALMA observations? | E: Compare ALMA source-integrated H30alpha and H39alpha profiles with IRAM-30 m profiles | R: H30alpha flux up by a factor ~2.2, profiles broader, new broad wings | F: The wind has become faster and its physical conditions changed on ~2 yr timescales | **supported**
- H: Is a hot (white dwarf) companion needed to ionize the nebula? | E: N_LyC from the free-free flux compared with B-star and WD model atmospheres | R: log N_LyC ~43.8 matches Teff ~25 kK, L ~600 Lsun; a WD would need Teff > 50000 K | F: No need to invoke a hotter companion; a WD companion is not ruled out | **partially**

## Reasoning

- Why this data: mRRLs probe the deepest regions of pPNe/yPNe with minimal dust extinction, where the fast winds are launched  
  > "shows that mRRLs are optimal tracers to probe the deepest regions at the heart" (Introduction)
- Why this method: Non-LTE modeling was used because the new data deviate from LTE expectations; self-calibration was used because of high S/N and no complex large-scale structure  
  > "has not been run under the LTE approximation but in non-LTE." (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission); "the absence of significant/complex large-scale structure in M 2-9 in our observations" (Observations and data reduction)
- Alternative: Alternative velocity laws inside the high-velocity shells (including constant velocity) gave a poorer match  
  > "Within the HVSs, we explored alternative velocity functions that varied in steepness (including constant velocity), but these produced a poorer match to the data." (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission)
- Alternative: A single smooth density power law cannot reproduce the S-shape of the axial PV diagrams  
  > "Without these dense shells (i.e. with a unique, smooth density power-law) is not possible to reproduce the S-shape of the axial position-velocity diagrams" (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission)
- How they decided it was enough: model parameters were adjusted until a reasonable match with the data was reached, keeping the parameter count low  
  > "until a reasonable match was achieved between the model predictions and the data" (Non-LTE radiative transfer modeling of mRRL and free-free continuum emission)
- Limitation (authors): Model is probably not unique; more complex geometries and profiles cannot be dismissed  
  > "is probably not unique and that more intricate geometries, kinematics, and density and temperature profiles (e.g. latitude-dependent) cannot be dismissed as possibilities." (Model caveats and final modeling remarks)
- Limitation (authors): No comprehensive parameter space study was performed  
  > "Although a comprehensive parameter space study has not been performed and is beyond the scope of this paper" (Model caveats and final modeling remarks)
- Limitation (authors): Model fails to reproduce the H30alpha profile asymmetry  
  > "One shortcoming of our model is its failure to predict the asymmetry in the" (Model caveats and final modeling remarks)
- Limitation (authors): Continuum SED decomposition is only a rough estimate  
  > "is subject to uncertainties and should be considered as a rough estimate" (Spectral energy distribution: free-free and dust continuum emission)
- Limitation (authors): Distance to M 2-9 is highly uncertain  
  > "The distance to M 2-9 is highly uncertain, with values ranging from 50 pc to 3 kpc in the literature (cite: san17)." (M 2-9)
- Caveat (inferred, ours): Key physical results (Mdot, Mion, central mass, luminosity) scale with the adopted 650 pc distance, which spans a factor of 60 in the literature
- Caveat (inferred, ours): Model tuned by hand with ~300 trials and no formal fit statistic or uncertainty from a fit; degeneracies between density, pressure broadening and size are acknowledged
- Caveat (inferred, ours): Observed N_CO sign is quoted as both upper and lower limit in different sections
- Caveat (inferred, ours): Disk detection rests on a single narrow absorption feature at ~0.012 arcsec offset, below the beam size, plus the 1 mm waist
- Caveat (inferred, ours): Flux loss of ~20% and MRS of 0.7-0.8 arcsec may bias the dust versus free-free decomposition
- Caveat (inferred, ours): Only one epoch per band; variability claim relies on a 2015 single-dish comparison with a different resolution

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Co3RaL code and final model input files are not stated as released
- Missing: GILDAS MAPPING scripts and self-calibration settings
- Missing: Line-free channel ranges, cell and image sizes, clean masks
- Missing: Explicit SPW to project-code mapping
- Missing: Procedure and statistics of the SED decomposition and the Gaussian line fits
- Data volume (inferred): Tens of GB (two execution blocks of ~1.5 and ~1.1 hr, 12 SPWs, baselines up to 16 km); only about 10-20 GB if just the two science targets' calibrated MS are retained
- Score (inferred): 3/5, Score on a 1-5 scale. Observational setup, calibrators and several final numbers are well documented, but imaging and self-calibration parameters are sparse, the key model uses an unreleased custom code tuned by hand, and no archive product status is given.
- Rediscovery candidate: no, Line fluxes, widths and continuum fluxes could be redone from archive data, but the central model results depend on unreleased Co3RaL and hand-tuned parameters, and the imaging and self-calibration recipe is incomplete; public status of the data is not stated.

## Links

- Method: Sanchez Contreras et al. 2017, A&A 603, A67 (cite: san17) (CSC17 single-dish mRRL study and the starting model for the M 2-9 ionized wind)
- Method: Baez-Rubio et al. 2013 (cite: bae13) (MORELI code, Gaunt factors and pressure-broadening expressions used in Co3RaL)
- Method: Sanchez Contreras et al. 2022 (cite: san22) (Method for constraining Tex and opacity from a compact absorption feature)
- Method: Storey & Hummer 1995 (cite: sto95) (Departure coefficients b_n for non-LTE recombination lines)
- Companion: Castro-Carrizo et al. 2012 (cite: cc12) and 2017 (cite: cc17) (CO rings and hourglass of M 2-9 that fix the inclination and kinematics)
- Companion: de la Fuente et al. 2022 (cite: dlF22) (multi-epoch 23-43 GHz continuum showing the C-shaped curvature)
- Companion: Sanchez Contreras et al. 2019 (cite: san19) (ALMA mRRL study of the rotating bipolar wind and disk in MWC 922)
- Companion: Lykou et al. 2011 (cite: lyk11) (mid-IR interferometry of the compact central disk)
- Related: ALMA 2016.1.00161.S
- Related: ALMA 2017.1.00376.S

## Checks

```json
{
 "quotes": 147,
 "quotes_ok": 147,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 28,
 "numeric_problems": 0,
 "fill": {
  "facts": 112,
  "stated": 92,
  "rate": 0.821
 },
 "evidence_ok": true
}
```
