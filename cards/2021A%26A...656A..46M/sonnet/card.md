# ALCHEMI, an ALMA Comprehensive High-resolution Extragalactic Molecular Inventory. Survey presentation and first results from the ACA array

`2021A&A...656A..46M` | Astronomy and Astrophysics 2021 | first author: Martín, S. | arXiv: 2109.08638 | DOI: 10.1051/0004-6361/202141567

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What is the molecular richness of the central molecular zone of NGC 253, probed by an unbiased ALMA spectral scan, and what do ACA 15'' spectra reveal about its chemistry, vibrational emission, organics and isotopic ratios?  
  > "Unveiling the molecular richness of the central region of the prototypical nearby starburst galaxy NGC 253 at an unprecedented combination of sensitivity, spatial resolution, and frequency coverage." (abstract)
- Target **NGC 253 CMZ**: coordinates 00h47m33.26s, -25d17m17.7s (ICRS phase center)  
  > "The nominal phase center of the observations is $\alpha=00^h47^m33.26^s$, $\delta=-25^\circ17'17.7''$ (ICRS)." (2 Observations); "1.6$''$ ($\sim 28$ pc) resolution" (abstract); z/distance 1.6'' ~ 28 pc (implies ~3.5 Mpc); distance not explicitly given  
  > "The nominal phase center of the observations is $\alpha=00^h47^m33.26^s$, $\delta=-25^\circ17'17.7''$ (ICRS)." (2 Observations); "1.6$''$ ($\sim 28$ pc) resolution" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00161.L, 2018.1.00162.S
- bands: Bands 3, 4, 5, 6, 7  
  > "with ALMA in frequency Bands 3, 4, 6, and 7 as part of the Cycle 5 Large Program 2017.1.00161.L." (2 Observations)
- frequencies and spectral setup: 84.2-373.2 GHz, 47 tunings each with four 1.875 GHz spectral windows; native resolution 0.977 MHz  
  > "The full data set results in a rest-frequency coverage between 84.2 and 373.2 GHz, with 47 individual tunings, each composed of four 1.875 GHz spectral windows from two receiver sidebands." (2.1 Frequency setup); "The native spectral resolution was 0.977 MHz" (2.1 Frequency setup)
- continuum bandwidth: _not stated_
- arrays: 12 m array and ACA 7 m (Morita) array  
  > "includes data obtained with both the main (12 m) and Morita (ACA 7 m) arrays." (1.3 The ALCHEMI survey)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6'' common beam (12m+7m); 15'' for ACA-only; 4'' for Band 3 12m compact  
  > "Data were imaged with a common restoring beam of $4''$ and $15''$, respectively, for these two compact array configurations." (3.2 Imaging)
- max recoverable scale: 15''  
  > "ALCHEMI targeted an MRS of $15''$ across its entire frequency coverage." (2.3 Maximum recoverable scales)
- sensitivity: Target 50, 50, 40, 30, 30 mK in 10 km/s channels (Bands 3-7); ACA rms 1.8-19.4 mJy/beam, average 7.8  
  > "The targeted brightness temperature sensitivity of the survey was 50, 50, 40, 30, and 30 mK in 10 $\rm km\,s^{-1}$ channels across ALMA Bands 3, 4, 5, 6, and 7, respectively." (2.2 Sensitivity); "sensitivities range between 1.8 and 19.4 mJy beam$^{-1}$ across the survey, with an average RMS of 7.8 mJy beam$^{-1}$ and a median of 7.5 mJy beam$^{-1}$." (4 ACA Data)
- time on source: 101.5 hours total, 38.8 h with 12 m  
  > "A total of 101.5 hours of integration time on source were acquired, 38.8 hours of which were obtained with the 12 m array." (2 Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel**: High-frequency continuum used to fit the dust temperature  
  > "The dust temperature was fit to the data in Fig. [5](#fig.continuumSED) using Herschel observations (with no aperture correction applied) at high frequencies" (4.1 Continuum emission)
- External data: Dust mass opacity kappa0=0.1 cm2/g at 250 GHz  
  > "$\kappa_{0}=$ 0.1 cm$^{2}$ g$^{-1}$ and $\nu_{0}=$250 GHz (cite: Cao2019)" (4.1 Continuum emission) [from (cite: Cao2019)]
- External data: Spectroscopic parameters from CDMS and JPL catalogs  
  > "are extracted from the CDMS (cite: Muller2001; Muller2005; Endres2016) and JPL (cite: Pickett1998) catalogs." (4.2.2 Line identification and LTE modeling) [from (cite: Muller2001; Muller2005; Endres2016; Pickett1998)]
- External data: Galactic hot-core Sgr B2(N) L_vib/L_IR = 4.2e-8  
  > "that of $4.2\times10^{-8}$ measured towards the Galactic Center hot core Sgr B2(N)" (5.2 Vibrational emission) [from (cite: Rolffs2011)]
- External data: Galactic Center GMC and hot core COM abundances relative to methanol  
  > "in the context of the Galactic Center GMCs observed by (cite: Requena-Torres2006) and the Galactic hot cores from (cite: Ikeda2001)" (5.3 Organic Molecules) [from (cite: Requena-Torres2006; Ikeda2001)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline for all but a couple of scheduling blocks; calibration by ALMA staff  
  > "Calibration and data quality assessment were performed by ALMA staff. For all but a couple of scheduling blocks the ALMA calibration pipeline was used." (3 Data calibration, equalization, and imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Various quasars e.g. J0006-0623, J0522-3627, J2258-2758 (Table 3)  
  > "J0006$-$0623" (Table 3)
- flux scale uncertainty: 15% conservative absolute flux uncertainty recommended  
  > "we recommend the usage of a conservative 15% uncertainty for the absolute flux calibration within the ALCHEMI image cubes" (8.2 Absolute Flux Calibration Uncertainty)
- self calibration: Not applied; flux self-calibration via overlapping channels used for amplitude scaling instead  
  > "the data in this article and the data that will initially be publicly released from this ALMA large program will not include self-calibration." (3.4 Self-calibration)

### Imaging

- task: CASA tclean per spectral window, then imsmooth  
  > "the CASA task *tclean* was used to produce image cubes of each tuning spectral windows." (3.2 Imaging)
- deconvolver: hogbom  
  > "The *hogbom* deconvolver function was used for all spectral windows." (3.2 Imaging)
- weighting robust: Briggs robust 0.5 for most; some tunings use 0.4, 0.25, 0.0, -2.0 with uvrange cuts  
  > "Robust (Briggs) weighting was used with a robust parameter of 0.5 for most spectral windows." (3.2 Imaging)
- uv taper: _not stated_
- cell size: 7m: 0.4 arcsec; 12m and 12m+7m: 0.15 arcsec  
  > "7m Array observations used $cell=0.4$ arcsec and $imsize=[320,320]$ pixels for all frequency bands" (3.2 Imaging)
- image size: 7m: [320,320]; 12m: [800,800],[800,720],[720,648],[640,512],[640,512] for Bands 3-7  
  > "imsize=$\[800,800\], \[800,720\], \[720,648\], \[640,512\], and \[640,512\] for Bands 3 through 7, respectively" (3.2 Imaging)
- masking: Automasking; threshold from pre-determined line-free rms for windows with strong lines, else nsigma=2  
  > "For spectral windows which did not contain strong spectral lines, the *tclean* parameter *nsigma=2* was set, and the *threshold* parameter was left unset." (3.2 Imaging)
- multiscale scales: _not stated_
- continuum subtraction: Per-pixel image-plane subtraction with STATCONT, sigma-clipping with default parameter  
  > "Sigma-clipping continuum determination was used with the default parameter (cite: Sanchez-Monge2018)." (3.3 Continuum subtraction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m+7m combined cubes for Bands 4-7; ACA-only cubes at 15''  
  > "Combined (12m compact plus extended configurations in Band 3 or 12-m plus 7-m array data for higher frequency bands" (2.2 Sensitivity)
- smoothing: imsmooth to circular Gaussian beam of 1.6''; bin to ~8-9 km/s channels  
  > "Post-imaging convolution using the CASA task *imsmooth* was therefore performed to produce final image cubes with a fixed Gaussian circular beam of $1.6''$." (3.2 Imaging)
- final beam: 1.6'' (28 pc); 15'' for ACA  
  > "a common final spatial resolution of $1.6''$ (28 pc) was selected" (3.2 Imaging)
- final rms: 0.18-5.0 mJy/beam (mean 1.4, median 1.0) in 8-9 km/s channels  
  > "the flux density RMS noise ranges from 0.18 to 5.0 mJy beam$^{-1}$, with average flux density sensitivity of 1.4 mJy beam$^{-1}$ and median of 1.0 mJy beam$^{-1}$." (2.2 Sensitivity)

### Inherited from earlier work

- Flux self-calibration technique using overlapping tunings  
  > "This technique, originally developed for other ALMA spectral scans, is referred to as “flux self-calibration” (cite: Sakamoto2021)." (3.1.1 Overlapping channels alignment) [from (cite: Sakamoto2021)]
- Continuum determination with STATCONT  
  > "continuum emission was statistically derived from each individual spectral window using STATCONT (cite: Sanchez-Monge2018)" (3.3 Continuum subtraction) [from (cite: Sanchez-Monge2018)]
- LTE fitting method with MADCUBA  
  > "using MADCUBA[^3] (cite: Martin2019a)" (4.2.2 Line identification and LTE modeling) [from (cite: Martin2019a)]
- Source size of 5'' assumed from higher-resolution observations  
  > "we assumed a circular Gaussian equivalent source size of $5''$, based on available higher resolution observations (cite: Meier2015; Martin2019)" (4.2.2 Line identification and LTE modeling) [from (cite: Meier2015; Martin2019)]

### Not stated but needed to reproduce (our reading)

- Explicit line-free channels or STATCONT settings per spectral window
- Exact MADCUBA fit settings (algorithm options, mask choices per molecule)
- CASA version used for processing
- tclean threshold values per spectral window
- Distance to NGC 253 adopted
- Observing dates and per-execution details
- Pixel/spectral window data selection for line subsets used in each species fit

## Analysis recipe

1. **Equalize relative flux scale across tunings**: Solve r_ij=a_i/a_j from overlapping channel amplitude ratios at TH2 position with least squares and mean(a_i)=1; apply via gencal  
  > "We used the constraint mean(a$_i$) = 1 to set the overall scale of the solutions, resulting in the flux self-calibration rescaling factors listed in Table [2](#tab.observingsetup)." (3.1.1 Overlapping channels alignment)
   - software: CASA gencal
   - parameter: Reference position TH2 alpha=00h47m33.182s, delta=-25d17m17.148s (J2000)  
  > "The spectra extracted from the TH2 position ($\alpha_{J2000}=00^h47^m33.182^s$, $\delta_{J2000}=-25^\circ17'17.148''$; (cite: Lenc2006))" (3.1.1 Overlapping channels alignment)
   - assumption: Reference emission compact and non-variable  
  > "as long as it is reasonably spatially compact and presents no time variability over the observation period." (3.1.1 Overlapping channels alignment)
   - fitting: _not stated_
   - validation: Continuum-level alignment with third-order polynomial gave 2.5% scatter in residual factors  
  > "we find that the standard deviation of the new scaling factors is $2.5\%$ across all bands" (3.1.2 Continuum level alignment)
2. **Image cubes and subtract continuum**: Bin to common velocity resolution, tclean each spectral window, convolve to common beam, subtract continuum per pixel with STATCONT  
  > "all measurement sets were binned to a common velocity scale." (3.2 Imaging)
   - software: CASA tclean, CASA imsmooth, STATCONT
   - parameter: Binning 3, 5, 6, 8, 10 MHz for Bands 3-7; robust 0.5 mostly  
  > "binning to frequency resolutions of 3, 5, 6, 8, and 10 MHz for Bands 3, 4, 5, 6, and 7, respectively" (3.2 Imaging)
   - fitting: _not stated_
   - validation: Per-pixel continuum estimation tested; continuum overestimated in noisy regions  
  > "we observe that the continuum appears slightly overestimated in the regions of spectra with higher noise levels." (3.3 Continuum subtraction)
3. **Fit continuum SED**: Grey-body dust plus free-free and synchrotron fitted to STATCONT continuum at the analysis pixel, with Herschel at high frequencies  
  > "fits well to a grey-body with dust temperature $T_d=42\pm1$ K, mass $M_d=8.0\pm0.2\times10^5$ M$_\odot$, emissivity $\beta=1.9$" (4.1 Continuum emission)
   - parameter: kappa0=0.1 cm2/g at 250 GHz; T_e=1e4 K; SFR=2.5 Msun/yr  
  > "plus a free-free component to account for the lower frequency emission with SFR=2.5 M$_\odot$ yr$^{-1}$ and $T_e=10^4$ K (cite: DeZotti2019)." (4.1 Continuum emission)
   - assumption: Beta=1.9 emissivity law  
  > "emissivity $\beta=1.9$ (i.e., $S\propto\nu^{3.9}$)" (4.1 Continuum emission)
   - fitting: _not stated_
   - validation: Compared with Perez-Beaupuits 2018 cold component of 37 K and mass 1e6 Msun  
  > "finding good agreement with the cold component fit of 37 K by (cite: Perez-Beaupuits2018)." (4.1 Continuum emission)
4. **Measure line contribution to continuum**: Average continuum-subtracted flux divided by total average flux per band  
  > "we calculated the average flux density over the continuum subtracted spectrum and divided it by the observed average flux density (continuum plus line emission) over the same band." (4.1.1 Line contribution)
   - fitting: _not stated_
   - validation: Compared with Arp 220 28% result  
  > "The 40-GHz-wide spectral scan at 1.3 mm toward the ULIRG Arp 220, reported a line contribution to the total observed flux of $\sim28$%" (4.1.1 Line contribution)
5. **Extract 15'' spectrum and fit LTE model per species**: Extract spectrum from the pixel at average of peak positions of 16 bright moment 0 maps; fit single-Gaussian LTE synthetic spectra per molecule with all transitions at once  
  > "The spectra analyzed in this article were extracted from the pixel at position $\alpha_{J2000}=00^h47^m33.10^s$, $\delta_{J2000}=-25^\circ17'18.1''$" (4.2.1 Selected sample position)
   - software: MADCUBA
   - parameter: Source size 5'' (10'' for 12C16O); fixed v_LSR=230 km/s, FWHM=150 km/s, Tex=15 K when unconstrained  
  > "parameters were fixed to $v_{LSR}=230$ $\rm km\,s^{-1}$  and $\Delta~v_{1/2}=150$ $\rm km\,s^{-1}$" (4.2.2 Line identification and LTE modeling); "the excitation temperature was set to $T_{ex}$=15 K" (4.2.2 Line identification and LTE modeling)
   - parameter: Detection criterion: all unblended transitions above 5 sigma in model detected and fit converged  
  > "A species has been considered detected if all the detectable transitions above $5~\sigma$ (according to the LTE model), which are not blended with brighter transitions, are detected in our data." (4.2.2 Line identification and LTE modeling)
   - assumption: LTE, single Gaussian component, column density linear in source solid angle  
  > "the modeling described here will consider a single Gaussian emission profile" (4.2.2 Line identification and LTE modeling)
   - fitting: MADCUBA least-squares fit; only statistical uncertainties reported  
  > "reported uncertainties do not include calibration uncertainties but statistical uncertainty on the fit to the spectra." (4.2.2 Line identification and LTE modeling)
   - validation: Residuals inspected against full-spectrum model; non-LTE deviations identified; extra criteria for new detections  
  > "any bright emission line predicted by the LTE model should be consistent with the observed spectra and no big outliers should be present." (9.1 Fitting details of newly detected species)
6. **Derive isotopic ratios and opacity effects**: Column density ratios of isotopologue pairs; effect of source size tested on HCO+; CN hyperfine multi-component LTE models  
  > "Table [6](#tab.isotopicratios) shows the isotopic ratios derived from the column densities fitted to all detected isotopologue pairs" (5.4 Isotopic ratios)
   - software: MADCUBA
   - parameter: CO isotopologues recalculated for 10'' source size  
  > "the emission of $^{13}$CO and C$^{18}$O fits were recalculated for an equivalent source size of $10''$." (5.4 Isotopic ratios)
   - fitting: _not stated_
   - validation: Compared with literature ratios in Table 8  
  > "Table [8](#tab.isotopicratiosliterature) compiles all isotopic ratios reported in the literature towards NGC 253." (5.4 Isotopic ratios)
7. **Vibrational emission and proto-SSC fraction**: Gaussian fits to v2=1f transitions, L_vib/L_IR compared with Sgr B2(N) value  
  > "Assuming that vibrational emission is mostly contributed by Sgr B2(N)-like hot cores, this comparison results in a $\sim3\%$ level" (5.2.2 Vibrational emission as tracer)
   - parameter: line width 150 km/s; LTE Tex=300 K for display  
  > "considers a line width of 150 $\rm km\,s^{-1}$, similar to that fitted to most rotational transitions." (Table notes)
   - assumption: L_IR = 2.1e10 Lsun  
  > "$L_{\rm IR}=2.1\times10^{10}\,L_\odot$" (1.2 NGC 253)
   - fitting: _not stated_
   - validation: Consistent with Rico-Villas 2020 ~3%  
  > "this estimate is consistent with the contribution from proto-SSCs of $\sim 3\%$ derived by (cite: Rico-Villas2020)" (5.2.2 Vibrational emission as tracer)
8. **Organic abundances relative to methanol**: C2H5OH and HCOOH relative to CH3OH; H2 from C18O with 18O/16O=100 and CO/H2~8e-5  
  > "assuming $\rm ^{18}O/^{16}O=100$ (as derived in Sect. [5.4.2](#sec.isotopologuesOxygen)) and CO/H$_2\sim 8\times10^{-5}$ (cite: Frerking1982), which yields $N_{\rm H_2}=3.1\times10^{23}~\rm cm^{-2}$" (5.3 Organic Molecules)
   - software: MADCUBA
   - assumption: Factor of 2 uncertainty in H2  
  > "We included a conservative factor of 2 uncertainty in the H$_2$ determination" (5.3 Organic Molecules)
   - fitting: _not stated_
   - validation: Compared with GC GMCs and hot cores  
  > "The comparison in Fig. [12](#fig.complexmolecules) shows that the averaged abundances towards NGC 253 are on the high end of GMC measurements" (5.3 Organic Molecules)

## Software

- **CASA** : tclean imaging, imsmooth, imstat, gencal  
  > "the CASA task *tclean* was used to produce image cubes of each tuning spectral windows." (3.2 Imaging)
- **STATCONT** : Per-pixel continuum determination and subtraction  
  > "using STATCONT (cite: Sanchez-Monge2018) to derive and subtract the continuum on a per pixel basis from each image cube." (3.3 Continuum subtraction)
- **MADCUBA** 6.0 (07/05/2018): LTE line identification and fitting  
  > "MADCUBA VERSION 6.0 (07/05/2018)." (footnote 3)
- **astroquery** : Extract calibrator information from the ALMA archive  
  > "Information in this table extracted from the ALMA archive using `a`stroquery (cite: Ginsburg2019)." (Table 3 notes)
- **astropy** : Appendix analysis and diagrams  
  > "Analysis and diagrams in these appendices make extensive use of `a`stropy" (footnote 4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of species detected (firm or tentative) | 78 | not stated | species | 5 | only 78 species are considered firmly or tentatively detected, accounting for 1790 transitions |
| Dust temperature | 42 | 1 | K | 3 | dust temperature $T_d=42\pm1$ K, mass $M_d=8.0\pm0.2\times10^5$ M$_\odot$ |
| Dust mass | 8.0e5 | 0.2e5 | Msun | 3 | mass $M_d=8.0\pm0.2\times10^5$ M$_\odot$ |
| Line contribution to continuum, 50 GHz bins | 5.3 to 36.6 | not stated | % | 4 | / $325-375$ / 2488 / 909 / 36.6 / 6.5 / |
| 12C/13C from bright high dipole moment species (weighted) | 22 | 2 | dimensionless | 6 | is $22\pm2$. |
| 16O/18O from HCO+ | 100 | 20 | dimensionless | 6 | Our $\rm ^{16}O/^{18}O$ ratio of $100\pm20$ measured with HCO$^+$ |
| 16O/18O from 13CO/13C18O | 520 | 60 | dimensionless | 6 | / $520\pm60$     / $^{13}$CO/ $^{13}$C$^{18}$O / |
| 14N/15N weighted average | 170 | 20 | dimensionless | 6 | are consistent with a weighted average of $170\pm20$ |
| 32S/34S (CS) | 9.7 | 0.5 | dimensionless | 6 | ratios measured with both CS and SO ($9.7\pm0.5$ and $14\pm4$, respectively) |
| 28Si/29Si | 9 | 2 | dimensionless | 6 | the ratio $\rm ^{28}Si/^{29}Si$=$9\pm2$ |
| L_vib/L_IR from HCN 3-2 v2=1f | 1.4e-9 | not stated | dimensionless | 7 | / HCN $3-2$ / 267.199 / $53\pm11$ / 8.5 / $6.08\pm0.07$ / $120\pm20$ / 28.9 / 1.4 / |
| Proto-SSC contribution to IR luminosity | ~3 | not stated | % | 7 | this comparison results in a $\sim3\%$ level as a proxy to the contribution from proto-SSCs to the global infrared luminosity in NGC 253. |
| C2H5OH/CH3OH abundance | 1.1e-1 | 0.4e-1 | dimensionless | 8 | abundances of $\rm C_2H_5OH$ ($1.1\pm0.4\times10^{-1}$) and HCOOH ($2.8\pm1.0\times10^{-2}$) relative to CH$_3$OH |
| N_H2 toward the sample position | 3.1e23 | factor of 2 | cm^-2 | 8 | which yields $N_{\rm H_2}=3.1\times10^{23}~\rm cm^{-2}$ |

## Qualitative findings

- First extragalactic detections of C2H5OH, HOCN, HC3HO and several rare isotopologues  
  > "We report the first extragalactic detections of C$_2$H$_5$OH, HOCN, HC$_3$HO, and several rare isotopologues." (abstract)
- Vibrationally excited HCN, HNC and HC3N detected at low resolution but not HCO+  
  > "while we do not detect it for HCO$^+$." (abstract)

## Claim tuples

- H: Does a wideband ACA spectral scan of the NGC 253 CMZ reveal a rich molecular inventory? | E: LTE modelling per species of the 15'' spectrum at 125-373 GHz | R: 78 species detected plus recombination lines | F: Rich chemistry detectable even at 15'' resolution; includes first extragalactic detections | **supported**
- H: Is vibrational emission a proxy for proto-SSC contribution and indicative of carbon-rich chemistry? | E: Measured vibrational HCN, HNC, HCO+ and L_vib/L_IR compared with Sgr B2(N) | R: HCO+ vibrational not detected; ~3% contribution | F: High temperature carbon-rich chemistry suggested; tentative proxy | **partially**
- H: Do isotopic ratios in NGC 253 reflect multiple ISM components? | E: Column density ratios of isotopologue pairs | R: High dipole moment species agree with Galactic CMZ; 13C18O-derived ratios factor ~5 larger | F: Multiple components with different nucleosynthesis enrichment | **supported**
- H: Are organic molecule abundances like Galactic GMCs or hot cores? | E: C2H5OH and HCOOH relative to CH3OH compared with Galactic Center GMCs and hot cores | R: On the high end of GMCs, similar to hot cores | F: Hot-core chemistry may contribute significantly | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Per-species LTE modelling is more robust than per-transition identification and handles blending  
  > "Therefore, line identification is done per molecule and not per transition, which is more robust and makes use of the broad frequency coverage in this work." (4.2.2 Line identification and LTE modeling)
- Alternative: uv-plane continuum subtraction rejected as inefficient for 188 cubes  
  > "it would be inefficient to subtract the continuum in the $uv$ plane from the individual 188 data cubes constituting the ALCHEMI measurement set." (3.3 Continuum subtraction)
- Alternative: Two-component Gaussian fit not used as it adds little significance  
  > "the use of a multi-Gaussian fit to the overall spectrum adds little significance to the results" (4.2.2 Line identification and LTE modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Calibration uncertainty not included in fit uncertainties; line flux scaling anomalies in some tunings  
  > "only the statistical uncertainty in the fits due the noise in the spectra are considered and not the absolute flux calibration uncertainty mentioned above" (3.1 Flux calibration accuracy)
- Limitation (authors): STATCONT continuum subtraction not optimal for lines near noise level  
  > "continuum subtraction is seen not to be optimal for spectral lines close to the noise level." (3.3 Continuum subtraction)
- Caveat (inferred, ours): Single-component LTE with assumed 5'' source size makes column densities and ratios model dependent
- Caveat (inferred, ours): Opacity and source-size degeneracy affects isotopic ratios by up to a factor of 2
- Caveat (inferred, ours): Single sample position at 15'' averages multiple components
- Caveat (inferred, ours): Many fixed parameters (Tex, v, width) for faint species
- Caveat (inferred, ours): Continuum per-pixel subtraction can bias faint lines

## Reproducibility

- Data public (paper): Data to be publicly released from the ALMA large program (without self-calibration)  
  > "the data that will initially be publicly released from this ALMA large program will not include self-calibration." (3.4 Self-calibration)
- Products in archive: _not stated_
- Missing: Per-species MADCUBA input files and masks
- Missing: Exact CASA version and pipeline version
- Missing: Per-spw tclean thresholds
- Missing: Distance adopted
- Data volume (inferred): Very large (hundreds of GB to TB for full survey; ACA subset ~tens of GB)
- Score (inferred): 5/5, Imaging and calibration are well described and data are public, but MADCUBA fitting is human-supervised with many unrecorded choices and the raw volume is large.
- Rediscovery candidate: no, Large dataset and human-supervised LTE fitting with unstated per-species choices make exact redo difficult, though numeric results exist.

## Links

- Method: (cite: Sakamoto2021) (Flux self-calibration technique using overlapping tunings)
- Method: (cite: Martin2019a) (MADCUBA LTE fitting)
- Method: (cite: Sanchez-Monge2018) (STATCONT continuum determination)
- Companion: (cite: Martin2019) (Higher-resolution CO isotopologue ratios in NGC 253)
- Companion: (cite: Rico-Villas2020) (Vibrational HC3N and proto-SSCs in NGC 253)
- Related: ALCHEMI (2017.1.00161.L, 2018.1.00162.S)

## Checks

```json
{
 "quotes": 103,
 "quotes_ok": 103,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 76,
  "rate": 0.768
 },
 "evidence_ok": true
}
```
