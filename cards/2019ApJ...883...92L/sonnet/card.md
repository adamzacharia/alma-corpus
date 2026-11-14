# A Radio-to-millimeter Census of Star-forming Galaxies in Protocluster 4C 23.56 at z = 2.5: Global and Local Gas Kinematics

`2019ApJ...883...92L` | The Astrophysical Journal 2019 | first author: Lee, Minju M. | arXiv: 1909.02028 | DOI: 10.3847/1538-4357/ab3b5b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, star_formation
- Question: Do star-forming galaxies in the z=2.5 protocluster 4C 23.56 differ from field galaxies in CO gas kinematics (line widths, sizes), and what is the protocluster halo mass and merger state?  
  > "In this paper, we aim to provide quantitative measurements of the kinematic properties of typical star-forming galaxies with higher angular resolution imaging by focusing on the same HAEs in the well-characterized protocluster 4C 23.56 at $z=2.5$." (1 Introduction)
- Target **Protocluster 4C 23.56 (HAEs)**: coordinates HAE positions in Table 1, e.g. HAE 16 21:07:14.642 +23:31:15.593  
  > "We assume $H_0 = 67.8$ ${\rm km\,s^{-1}\,Mpc^{-1}}$, $\Omega_0 = 0.308$, and $\Omega_{\Lambda} = 0.692$ (cite: PlanckCollaboration2015)." (Introduction); z/distance z_proto = 2.4874 (biweight, CO)  
  > "We assume $H_0 = 67.8$ ${\rm km\,s^{-1}\,Mpc^{-1}}$, $\Omega_0 = 0.308$, and $\Omega_{\Lambda} = 0.692$ (cite: PlanckCollaboration2015)." (Introduction); distance from CO (4–3) and CO (3–2) redshifts from this work  
  > "We assume $H_0 = 67.8$ ${\rm km\,s^{-1}\,Mpc^{-1}}$, $\Omega_0 = 0.308$, and $\Omega_{\Lambda} = 0.692$ (cite: PlanckCollaboration2015)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00152.S
- bands: Band 4 (CO 4–3; 2 mm continuum)  
  > "We used ALMA Band 4 receivers to obtain the redshifted CO (4–3) emission" (2.1 ALMA Band 4 observations)
- frequencies and spectral setup: 4 SPWs; one FDM with 7.82 MHz channels (~17.7 km/s), 1.875 GHz bandwidth; three TDM 2.0 GHz at 15.6 MHz  
  > "One SPW was set in the Frequency-Division Mode (FDM) to detect the redshifted CO (4–3) line by having a channel width of 7.82 MHz ($\sim$ 17.7 km s$^{-1}$) and a total bandwidth of 1.875 GHz." (2.1 ALMA Band 4 observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-6, 38 or 39 antennas, baselines 15 m–3.1 km  
  > "baseline length ($L_{\rm baseline}$) between 15 m and 3.1 km (C40-6 configuration" (2.1 ALMA Band 4 observations)
- baselines: _not stated_
- angular resolution: 0.52"x0.32" (natural); 0.74"x0.58" tapered  
  > "The synthesized beam is $0''.52\times0''.32$" (2.1 ALMA Band 4 observations)
- max recoverable scale: _not stated_
- sensitivity: 0.14 mJy/beam at 80 km/s  
  > "The typical noise level in the final image is 0.14 mJy beam$^{-1}$ at 80 km s$^{-1}$." (2.1 ALMA Band 4 observations)
- time on source: 2.7 hr total, ~1.4 hr per pointing (two pointings)  
  > "The total on-source time ($T_{\rm integ.}$) was 2.7 hr with the two-pointing observations, thus $\simeq$ 1.4 hr per pointing." (2.1 ALMA Band 4 observations)
- observing dates: _not stated_
- pi or archival as stated: PI Minju Lee  
  > "ID : ADS/JAO.ALMA #2015.1.00152.S, PI : Minju Lee" (2.1 ALMA Band 4 observations)
- Line: CO 4–3 (not stated)
- Other facility **ALMA CO (3–2) and 1.1 mm (previous program)**: CO (3–2) cubes reanalysed; 1.1 mm continuum for PA_geo  
  > "We reanalyzed our CO (3–2) images to have a common spectral resolution with the CO (4–3) images" (2.3 Reanalysis for the CO (3–2) data)
- Other facility **Subaru (MOIRCS, IRCS)**: Halpha redshifts, NIR imaging, AO images  
  > "have H$\alpha$ redshifts from Subaru grism spectroscopy" (3.1 Detection of CO (4–3))
- External data: CO line widths and luminosities of protocluster galaxies  
  > "For protocluster galaxies, we obtained the measurements from (cite: Aravena2012; Casasola2013; Ivison2013; Tadaki2014b; Chapman2015; Rudnick2017; Dannerbauer2017; Hayashi2017; Noble2017; Noble2019; Wang2018; Coogan2018; Tadaki2019a; Gomez-Guijarro2019)." (5.2 CO line widths) [from Aravena2012; Casasola2013; Ivison2013; Tadaki2014b; Chapman2015; Rudnick2017; Dannerbauer2017; Hayashi2017; Noble2017; Noble2019; Wang2018; Coogan2018; Tadaki2019a; Gomez-Guijarro2019]
- External data: Field galaxy CO sample  
  > "We compiled the field data points from (cite: Tacconi2013; Daddi2015; Bourne2019) and (cite: Aravena2019)." (5.2 CO line widths) [from Tacconi2013; Daddi2015; Bourne2019; Aravena2019]

## Processing

### Calibration

- pipeline or manual: EA-ARC pipeline script plus manual Tsys outlier flagging  
  > "Then additional flagging of $T_{\rm sys}$ outliers was applied manually" (2.1 ALMA Band 4 observations)
- casa version: CASA 4.7.0 (calibration), 5.1.2 (imaging)  
  > "version 4.7.0 and 5.1.2 for the calibration of visibility data and imaging, respectively." (2.1 ALMA Band 4 observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2025+3343 (flux), J2148+0657 (bandpass); phase J2114+2832  
  > "Two quasars, J2148+0657 and J2025+3343 were chosen for bandpass and flux calibration, respectively." (2.1 ALMA Band 4 observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean; uvcontsub for continuum subtraction  
  > "Images were produced by $\mathtt{CASA}$ task $\mathtt{tclean}$ and deconvolved down to the 2$\sigma$ noise level." (2.1 ALMA Band 4 observations)
- deconvolver: _not stated_
- weighting robust: natural weighting for original image  
  > "we call this lower resolution image the “tapered" image and the natural-weighted image the “original" image." (2.2 Detection criteria)
- uv taper: uvtaper 0.5" giving 0.74"x0.58" beam  
  > "with a parameter of $0''.5$ to produce a synthesized beam of $0''.74\times0''.58$" (2.2 Detection criteria)
- cell size: _not stated_
- image size: _not stated_
- masking: circular regions of radius 3x beam size at HAE positions  
  > "Clean masks were created based on the positions of HAEs, using circular regions with a radius of 3$\times$ the beam size." (2.1 ALMA Band 4 observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "All images were analyzed after subtracting the continuum emission using $\mathtt{uvcontsub}$." (2.1 ALMA Band 4 observations)
- line free channels: _not stated_
- primary beam correction: primary-beam-corrected images used for measurements  
  > "We used the primary-beam-corrected images for all these measurements." (3.1 Detection of CO (4–3))
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.52"x0.32"  
  > "The synthesized beam is $0''.52\times0''.32$" (2.1 ALMA Band 4 observations)
- final rms: 0.14 mJy/beam at 80 km/s  
  > "The typical noise level in the final image is 0.14 mJy beam$^{-1}$ at 80 km s$^{-1}$." (2.1 ALMA Band 4 observations)

### Inherited from earlier work

- CO (3–2) calibration details and two-step detection criteria  
  > "The details of the calibration are given in ." (2.3 Reanalysis for the CO (3–2) data) [from Paper I (cite: minju2017a)]
- Noise estimate for peak line intensity  
  > "The noise estimate for the peak line intensity is based on the calculation after taking into account the channel noise and integrating velocity range, following (cite: Hainline2004)." (2.2 Detection criteria) [from Hainline2004]

### Not stated but needed to reproduce (our reading)

- tclean robust/weighting for natural image, cell and image size
- line-free channels for uvcontsub and fit order
- flux scale uncertainty
- exact spectral cube velocity frame/rest frequency
- how literature CO samples were homogenized and sample tables
- GalPaK3D priors and bounds besides Vmax
- how L'CO and gas fractions of HAEs were derived

## Analysis recipe

1. **Calibrate and image CO (4–3) cubes**: Pipeline calibration with manual Tsys flagging; tclean at 80 km/s, natural and uv-tapered; uvcontsub  
  > "We made final images using the recalibrated data sets after flagging." (2.1 ALMA Band 4 observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Images without continuum subtraction checked for continuum misidentified as broad line  
  > "Images without continuum subtraction were also investigated to test whether the continuum has been misidentified as a (broad) line detection." (2.1 ALMA Band 4 observations)
2. **Detect CO (4–3) and measure line properties**: Two-step criteria: peak-intensity S/N>=4.5, then peak flux >=3.5 sigma or two channels >2.5 sigma; imfit 2D Gaussian with 0.7" aperture; 1D Gaussian spectral fit  
  > "(a) the signal-to-noise (S/N) ratio of the peak of the velocity-integrated intensity ($I_{\rm CO43,peak}$) is equal to or greater than 4.5" (2.2 Detection criteria)
   - software: CASA imfit
   - parameter: search radius 1.0" around HAE; integration range up to 2000 km/s, central shift up to ±1800 km/s  
  > "We investigated a velocity-integration range as large as 2000 km s$^{-1}$ with a shift in the central velocity of up to $\pm 1800$ km s$^{-1}$" (2.2 Detection criteria)
   - fitting: one-component Gaussian for spectra  
  > "The listed line widths and the redshifts are estimated from a one-component Gaussian-model fitting with errors from the fitting and the assumed spectral resolution." (3.1 Detection of CO (4–3))
   - validation: Compared with tapered CO (3–2) at matched resolution; astrodendro false-positive test  
  > "We investigated the chances of false-positive detection using $\mathtt{astrodendro}$" (3.3 Subcomponents)
3. **Protocluster halo mass from velocity dispersion**: Biweight mean redshift, LOS velocities, biweight and gapper dispersions; halo mass from Finn2005 and Evrard2008 relations; clump masses for EC/WC  
  > "We finally derive the halo mass of the protocluster from the derived velocity dispersion, using two different calculations used in (cite: Finn2005) and (cite: Evrard2008)." (4.1 Overall halo estimates)
   - assumption: virialization (upper limit for unvirialized system)  
  > "Under the assumption of virialization, velocity dispersion offers a rough measure of the halo mass of the protocluster." (4.1 Overall halo estimates)
   - fitting: _not stated_
   - validation: two dispersion estimators agree; CO-only vs all redshifts  
  > "With 12 CO-detections, individual estimates agree well with each other within the errors." (4.1 Overall halo estimates)
4. **Compare CO line widths and L'CO with protocluster and field samples**: FWHM converted to v_rot via FWHM*sqrt(3/(8 ln2)); L'CO(1-0) via R1J ratios 1.2,1.8,2.4 for J=2,3,4; compare medians  
  > "We assumed the line luminosity ratio of $R1J (=L'_{\rm CO1-0}/L'_{\rm COJ-(J-1)}) = 1.2, 1.8,$ and $2.4$ for $J= 2,3, {\rm and}~4$, respectively" (5.2 CO line widths)
   - assumption: isotropic virial estimate of circular velocity for unresolved sources  
  > "taking the isotropic virial estimate of the circular velocity (FWHM$\times \sqrt{3/(8\ln{2}})$" (5.2 CO line widths)
   - fitting: _not stated_
   - validation: _not stated_
5. **Kinematic modelling of HAE 16**: GalPaK3D MCMC with tanh and mass velocity profiles on 40 km/s cube; exponential disk n=1; 25,000-55,000 iterations  
  > "We used GalPaK$^{3D}$ ((cite: Bouche2015), version 1.8.8), which implements the Bayesian-based Markov Chain Monte Carlo (MCMC) calculation to estimate parameters and corrects the beam-smearing effect." (8 GalPak3D modeling)
   - software: GalPaK3D
   - fitting: MCMC, random_scale 7–15, Vmax bound up to 1500 km/s  
  > "The number of samplings (i.e., iteration) used for the model construction is 25,000 at first and increased to as high as 55,000 if necessary." (8 GalPak3D modeling)
   - validation: reduced chi2 ~1.37 for both profiles  
  > "the MCMC chains are converged with the reduced $\chi^{2}$ value of $\chi^{2}_{\rm reduced} \approx 1.37$ for both profiles" (8 GalPak3D modeling)

## Software

- **CASA** 4.7.0 (calibration), 5.1.2 (imaging): calibration, tclean, uvcontsub, imfit, uvmodelfit  
  > "We used $\mathtt{CASA}$ ((cite: McMullin2007)) version 4.7.0 and 5.1.2 for the calibration of visibility data and imaging, respectively." (2.1 ALMA Band 4 observations)
- **astrodendro** : false-positive test  
  > "We investigated the chances of false-positive detection using $\mathtt{astrodendro}$" (3.3 Subcomponents)
- **GalPaK3D** 1.8.8: 3D kinematic modelling of HAE 16  
  > "We used GalPaK$^{3D}$ ((cite: Bouche2015), version 1.8.8)" (8 GalPak3D modeling)
- **Astropy** : listed in software  
  > "CASA (cite: McMullin2007) , Astropy (cite: astropy)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CO (4–3) detected HAEs | 11 of 16 | not stated | galaxies | 2 | A total of 11 HAEs are detected in the CO (4–3) line, out of the 16 targeted. |
| Protocluster redshift (CO biweight) | 2.4874 | not stated | dimensionless | 3 | the protocluster redshift is defined as $\bar{z}_{\rm BI, CO} = 2.4874$ |
| LOS velocity dispersion (biweight) | 421 | ±148 | km/s | 3 | $\sigma_{\rm los, CO} = 421\pm148$ (biweight) and $365\pm 128$ (gapper) km s$^{-1}$ |
| Protocluster halo mass log(Mcl/Msun) | 13.4-13.6 | not stated | dex | 3 | The range of halo masses from these two methods is $\log{(M_{\rm cl}/M_{\odot})} =$13.4-13.6 |
| Median CO FWHM, 4C 23.56 vs other protoclusters | 433 vs 422 | not stated | km/s | 4 | the median value for the 4C 23.56 protocluster galaxies is 433 km s$^{-1}$, compared to 422 km s$^{-1}$ for other protocluster galaxies |
| Median v_rot protocluster vs field | 304 vs 192 | not stated | km/s | 4 | ($v_{\rm rot, pc}$= 304 km s$^{-1}$) compared to the field galaxies ($v_{\rm rot, fd}$= 192 km s$^{-1}$) |
| HAE 16 Vmax/sigma0 (tanh; mass) | 5.7; 3.6 | ±1.0; ±0.4 | dimensionless | 5 | $v/\sigma_0$ / $5.7 \pm 1.0$ |
| HAE 16 Toomre Q | 0.3-0.5 | not stated | dimensionless | 5 | gives $Q_{\rm gas}\ll 1$, ranging between $0.3$ and $0.5$ |

## Qualitative findings

- Protocluster composed of two merging groups (East and West clumps)  
  > "The small difference implies two galaxy groups in a merging phase within the protocluster." (4.2 Halo mass of individual substructures)

## Claim tuples

- H: Do CO (4–3) and CO (3–2) detections agree? | E: Matched spatial/spectral resolution comparison for six galaxies | R: Redshifts consistent within |Δz|<=0.0017; FWHM consistent | F: Detections confirmed | **supported**
- H: Will the protocluster evolve into a Virgo-like cluster? | E: Velocity dispersion based halo mass | R: log M=13.4-13.6 | F: Likely Virgo-like progenitor | **partially**
- H: Protocluster galaxies have broader CO lines than field galaxies | E: Compare medians with literature samples | R: v_rot 304 vs 192 km/s; L'CO similar | F: Broader lines attributed to unresolved mergers and/or compact gas | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small samples, inhomogeneous literature selection, virialization assumption  
  > "with caveats of inhomogeneous selection and small sample sizes" (5.2 CO line widths)
- Caveat (inferred, ours): Literature samples inhomogeneous; fixed excitation ratios
- Caveat (inferred, ours): Halo mass from ~12 redshifts with large errors
- Caveat (inferred, ours): Line-width difference may reflect inclination or selection

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: robust/cell/image size
- Missing: line-free channels
- Missing: compiled literature table
- Missing: GalPaK3D priors
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data identified and detection method clear, but imaging parameters and literature compilation not fully given.
- Rediscovery candidate: no, Key imaging settings and literature compilation not fully stated.

## Links

- Method: Bouche2015 (GalPaK3D)
- Method: Hainline2004 (noise estimate)
- Companion: minju2017a (Paper I: CO (3–2) observations)
- Related: PHIBSS
- Related: SINS/zC-SINF
- Related: ZFIRE

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 73,
  "stated": 48,
  "rate": 0.658
 },
 "evidence_ok": true
}
```
