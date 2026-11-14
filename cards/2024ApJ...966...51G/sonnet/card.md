# The Size─Linewidth Relation and Signatures of Feedback from Quiescent to Active Star Forming Regions in the LMC

`2024ApJ...966...51G` | The Astrophysical Journal 2024 | first author: Green, Alex | arXiv: 2403.09594 | DOI: 10.3847/1538-4357/ad31a4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: How does stellar feedback affect the size-linewidth relation and virial state of CO clumps in nine LMC GMCs, compared with gravity-driven explanations?  
  > "To investigate the effects of stellar feedback on the gravitational state of giant molecular clouds (GMCs), we study $^{12}$CO and $^{13}$CO ALMA maps of nine GMCs distributed throughout the Large Magellanic Cloud (LMC)" (abstract)
- Target **Nine LMC GMCs (30Dor, A439, GMC1, GMC104, N59C, N159E, N159W, N55, PCC)**: coordinates Mosaic centers in Table 1 (e.g. 30Dor 5:38:36 -69:05:27)  
  > "working at a common resolution of 3.5 arcseconds (0.85 pc at the LMC distance of 50 kpc)" (abstract); "| 30Dor | (2-1) | 5:38:36 | -69:05:27 | 34.147 |" (Table 1); z/distance 50 kpc  
  > "working at a common resolution of 3.5 arcseconds (0.85 pc at the LMC distance of 50 kpc)" (abstract); "| 30Dor | (2-1) | 5:38:36 | -69:05:27 | 34.147 |" (Table 1); distance from Pietrzynski et al. 2019  
  > "working at a common resolution of 3.5 arcseconds (0.85 pc at the LMC distance of 50 kpc)" (abstract); "| 30Dor | (2-1) | 5:38:36 | -69:05:27 | 34.147 |" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00554.S, 2013.1.00214.S, 2013.1.00832.S, 2016.1.00193.S, 2019.1.00843.S
- bands: Band 3 (J=1-0) and Band 6 (J=2-1)  
  > "in either the J = 1 – 0 (ALMA Band 3) or J = 2 – 1 (ALMA Band 6) transition." (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Matched to 3.5 arcsec (0.85 pc); native beams 0.84-3.5 arcsec  
  > "We match all the observations to a common channel resolution of 200 m s$^{-1}$ and spatial resolution of 3.5$''$." (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
- max recoverable scale: _not stated_
- sensitivity: Cubes matched to common noise level per line; T_rms,12 0.664-1.240 K, T_rms,13 0.245-0.337 K  
  > "We match all of the spectral cubes of a given line to a common noise level." (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Published/archival ALMA observations from earlier papers  
  > "We base this study on published Atacama Large Millimeter/submillimeter Array (ALMA) $^{12}$CO and $^{13}$CO observations." (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
- Line: 12CO J=1-0 and J=2-1 (not stated)
- Line: 13CO J=1-0 and J=2-1 (not stated)
- Other facility **Spitzer SAGE (IRAC 8 micron)**: 8 micron star-formation tracer  
  > "$8\ensuremath{\mu}m$ band observations from the SAGE IRAC Spitzer survey" (2.3 IR and Optical Star Formation Indicators)
- Other facility **MCELS**: Continuum-subtracted Halpha at 5 arcsec  
  > "Continuum-subtracted H$\alpha$ data with 5$''$ resolution from the Magellanic Clouds Emission-Line Survey" (2.3 IR and Optical Star Formation Indicators)
- Other facility **Herschel dust model (Utomo et al. 2019)**: Dust temperature map used to derive radiation-field energy density  
  > "We use the modified blackbody model in (cite: utomo_resolved_2019), derived from *Herschel Space Observatory* observations, for dust temperature ($T_d$)." (2.3 IR and Optical Star Formation Indicators)
- External data: Reduced ALMA CO cubes of A439, GMC1, GMC104, N59C, PCC  
  > "Observations of A439, GMC1, GMC104, N59C in (1 – 0) and PCC in (2 – 1) were obtained from (cite: wong_relations_2019)" (2.1 Resolution-Matching Archival 12CO and 13CO Observations) [from (cite: wong_relations_2019)]
- External data: 30 Doradus 2-1 cubes  
  > "and 30 Doradus in (2 – 1) from (cite: wong_30_2022)" (2.1 Resolution-Matching Archival 12CO and 13CO Observations) [from (cite: wong_30_2022)]
- External data: N159E and N159W cubes  
  > "N159E and N159W in (2 – 1) from (cite: fukui_high-mass_2015) and (cite: saigo_kinematic_2017)" (2.1 Resolution-Matching Archival 12CO and 13CO Observations) [from (cite: fukui_high-mass_2015); (cite: saigo_kinematic_2017)]
- External data: N55 1-0 cubes  
  > "N55 in (1 – 0) from (cite: 2018ApJ...853..175N)" (2.1 Resolution-Matching Archival 12CO and 13CO Observations) [from (cite: 2018ApJ...853..175N)]
- External data: Dust temperature model, beta=1.8, 13 pc resolution  
  > "The map has 13 pc resolution, and, following (cite: chiang_spatially_2018), uses a fixed value of emissivity ($\beta=1.8$)" (2.3 IR and Optical Star Formation Indicators) [from (cite: utomo_resolved_2019)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: maskmoment dilated masks, defaults except snr_hi_minch = 2 and minbeam = 2  
  > "We use the default masking parameters except `snr_hi_minch = 2` and `minbeam = 2`" (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Convolved to 3.5 arcsec beam and 200 m/s channels; Gaussian noise added to match noise  
  > "This scaled cube is then added to the image cubes." (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
- final beam: 3.5 arcsec  
  > "We match all the observations to a common channel resolution of 200 m s$^{-1}$ and spatial resolution of 3.5$''$." (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
- final rms: _not stated_

### Inherited from earlier work

- Line-width deconvolution in quadrature  
  > "We remove this response by performing deconvolution-in-quadrature of the linewidth, following (cite: rosolowsky_bias-free_2006)" (2.1 Resolution-Matching Archival 12CO and 13CO Observations) [from (cite: rosolowsky_bias-free_2006)]
- Spectral response correction for channel correlation  
  > "We use the spectral response prescribed by (cite: leroy_portrait_2016) to account for correlations in adjacent channels" (2.1 Resolution-Matching Archival 12CO and 13CO Observations) [from (cite: leroy_portrait_2016)]
- LTE analysis and abundance N(H2)/N(13CO)=3e6  
  > "We follow the local thermodynamic equilibrium (LTE) analysis conducted in (cite: wong_alma_2017) and (cite: wong_relations_2019)." (2.4 12CO- and 13CO-Based Clump Properties) [from (cite: wong_alma_2017); (cite: wong_relations_2019)]
- Bijection dendrogram approach  
  > "introduce a “bijection" approach for dendrogram decomposition which we follow" (2.2 Segmenting CO Emission) [from (cite: 2008ApJ...679.1338R)]
- R_21 = 0.8 constant line ratio  
  > "adopting a constant line ratio $R_{21} = 0.8$ as in (cite: wong_relations_2019)" (2.4 12CO- and 13CO-Based Clump Properties) [from (cite: wong_relations_2019)]

### Not stated but needed to reproduce (our reading)

- Exact native data products and which project code maps to which cloud
- How the original cubes were calibrated/imaged (taken from earlier papers)
- SCIMES parameters other than save_isol_leaves (e.g. criterion, similarity kernel)
- Exact LTE equations, excitation temperature handling and opacity solution
- Fiducial relation citation (reference elided in text)
- ODR weighting details and the confidence interval method
- Edge channels used for noise estimation and regridding/convolution kernels

## Analysis recipe

1. **Match resolution and noise of archival cubes**: Convolve to 3.5 arcsec and 200 m/s; add convolved Gaussian noise to reach common max noise per line  
  > "We convolve a cube of Gaussian noise ($\sigma_{\text{GN}}$) with the beam and normalize it to have an RMS of $\sqrt{\sigma_{\text{target}}^2 - \sigma_{\text{GN}}^2}$." (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
   - software: astropy
   - parameter: noise from mad_std in 20 edge channels  
  > "in 20 edge channels of each cloud" (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Segment emission into dendrogram and clumps**: astrodendro on masked cubes, bootstrap errors, SCIMES clustering with isolated leaves, size cut  
  > "we use the Spectral Clustering for Molecular Emission Segmentation (*SCIMES*)[^4] algorithm to gather structures into “clumps,"" (2.2 Segmenting CO Emission)
   - software: astrodendro, SCIMES, maskmoment, SpectralCubeTools
   - parameter: min_value 3 sigma_MAD, min_npix two beams, min_delta 2.5 sigma_MAD  
  > "We require that two local emission peaks must have a difference of at least 2.5$\sigma_{\text{MAD}}$ to be considered independent leaves (`min_delta`)." (2.2 Segmenting CO Emission)
   - parameter: R = 1.91 sqrt(sigma_maj sigma_min); bootstrapping 100 iterations; minimum 5% fractional uncertainty  
  > "We use bootstrapping with 100 iterations." (2.2 Segmenting CO Emission); "We impose a minimum fractional uncertainty of 5% on the measured properties of the dendrogram structures." (2.2 Segmenting CO Emission)
   - parameter: Remove clumps with minor axis < sqrt(2) beam width  
  > "We impose a cut that removes clumps with minor axis less than $\sqrt{2}$ times the beam width." (2.2 Segmenting CO Emission)
   - fitting: _not stated_
   - validation: Errors robust after ~100 realizations; noise-addition method consistent with bootstrapping  
  > "We find that errors are robust after $\sim100$ realizations of a structure." (2.2 Segmenting CO Emission)
3. **Derive clump masses, virial parameters, LTE columns**: M_lum from X_CO, LTE 13CO mass, M_vir=5 sigma^2 R/G, alpha=M_vir/M_lum  
  > "The virial parameter $$\begin{equation}
 \label{eq:virial_parameter}
 \alpha = \frac{M_{\text{vir}}}{M_{\text{lum}}}
\end{equation}$$" (2.4 12CO- and 13CO-Based Clump Properties)
   - parameter: X(1-0)=2.4, X(2-1)=3 with R21=0.8  
  > "with $X(\text{J = 1 -- 0}) = 2.4$ (cite: hughes_physical_2010), $X(\text{J = 2 -- 1}) = 3$" (2.4 12CO- and 13CO-Based Clump Properties)
   - assumption: Same Tex for 12CO and 13CO from 12CO; N(H2)/N(13CO)=3e6; spherical virialized clumps; distance 50 kpc  
  > "It is assumed that both the $^{12}$CO and $^{13}$CO lines for a given transition have the same excitation temperature" (2.4 12CO- and 13CO-Based Clump Properties)
   - fitting: _not stated_
   - validation: Tested variable R21 from 8 micron; no significant effect  
  > "Because this prescription of $R_{21}$ does not significantly impact our results, we proceed with the analysis using the uniform value of $R_{21}$." (2.4 12CO- and 13CO-Based Clump Properties)
4. **Measure clump-averaged star-formation tracers**: Project dendrogram masks to sky and average 8um, Halpha, and u_nu (from Td) maps; noise-addition uncertainties  
  > "we project the maximum extent of the dendrogram structure boundaries at any velocity channel onto the sky, and then calculate the average of each star-formation tracer map in this mask." (2.4 Star-Formation Tracer-Based Clump Properties and Uncertainties)
   - parameter: u_nu = 8.65e-13 (Td/18 K)^(4+beta) erg cm^-3, beta=1.8  
  > "is $$\begin{equation}
 \label{eq:u_nu}
 u_{\nu} = 8.65\times 10^{-13} \left(\frac{T_d}{18\text{K}}\right)^{4+\beta} \text{ erg cm}^{-3}
 \end{equation}$$" (2.3 IR and Optical Star Formation Indicators)
   - assumption: No Halpha extinction correction; dust in thermal equilibrium  
  > "so we do not employ this method in our study and note that the SFR may be underestimated by ignoring extinction effects." (2.3 IR and Optical Star Formation Indicators)
   - fitting: _not stated_
   - validation: Compared Td from Gordon 2014 and Utomo 2019 models; nearly linear  
  > "We find a nearly linear relationship between $T_d$ from the two models in our sample" (2.3 IR and Optical Star Formation Indicators)
5. **Fit size-linewidth relation and correlate nu0 and alpha_vir with tracers**: ODR fits of log sigma vs log R and of log nu0 = m(X-X0); report scatter and Pearson rho  
  > "we perform orthogonal distance regression (ODR) using the $\textit{scipy.odr}$ package" (3.2 Size-linewidth relation fits)
   - software: scipy.odr
   - parameter: fiducial relation sigma_v = 0.72 (R/pc)^0.5 km/s  
  > "$\sigma_v = 0.72 \left(R/\text{pc}\right)^{0.5} \text{ km s}^{-1}$, hereafter the “fiducial relation”" (3.2 Size-linewidth relation fits)
   - fitting: ODR weighting by uncertainties in both variables  
  > "the ODR fits weight data by the inverse square of the uncertainty for both the independent and dependent variables" (3.3 Fitting star-formation tracers and gas properties)
   - validation: Repeated with residuals from best-fit relation (Appendix); tested opacity via mean tau13  
  > "we investigate the robustness of this correlation analysis to the assumed size-linewidth relation by referencing the linewidth to the fitted rather than fiducial relation." (Appendix A)

## Software

- **astrodendro** : Dendrogram segmentation of PPV cubes  
  > "`astrodendro`[^3] is a Python package which segments position-position-velocity (PPV) data into hierarchical structures" (2.2 Segmenting CO Emission)
- **SCIMES** : Spectral clustering of dendrogram into clumps  
  > "we use the Spectral Clustering for Molecular Emission Segmentation (*SCIMES*)[^4] algorithm to gather structures into “clumps,"" (2.2 Segmenting CO Emission)
- **maskmoment** : Dilated signal masks  
  > "We mask the signal using dilated masks produced using the `maskmoment`[^2] package." (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
- **SpectralCubeTools** : Channel-to-channel correlation coefficient  
  > "The channel-to-channel correlation coefficient is calculated using the `SpectralCubeTools`[^1] package" (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
- **scipy.odr** : Orthogonal distance regression fits  
  > "we perform orthogonal distance regression (ODR) using the $\textit{scipy.odr}$ package" (3.2 Size-linewidth relation fits)
- **astropy** : mad_std noise estimation and general use  
  > "(`astropy.stats.mad_std`)" (2.1 Resolution-Matching Archival 12CO and 13CO Observations)
- **APLpy** : Plotting  
  > "APLpy, an open-source plotting package for Python" (Conclusions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO size-linewidth slope | 0.35 | 0.09 | dimensionless | 5 | \log \left(\frac{\sigma_v}{\text{km s}^{-1}}\right) = \left( 0.35\pm 0.09\right) \log \left(\frac{R}{\text{pc}}\right) -  0.04\pm 0.05, |
| 13CO size-linewidth slope | 2.29 | 0.78 | dimensionless | 5 | \log \left(\frac{\sigma_v}{\text{km s}^{-1}}\right) = \left( 2.29\pm 0.78\right) \log \left(\frac{R}{\text{pc}}\right) - 0.95 \pm 0.35, |
| Number of clumps (12CO / 13CO) | 117 / 50 | not stated | clumps | 2 | 117 clumps among all of the GMCs in our sample in CO, 50 in $^{13}$CO |
| 12CO log nu0 vs log 8um: slope and rho | m=0.27, rho=0.74 | 0.02 (slope) | dimensionless | 5 | / 0.27 $\pm$ 0.02 / 1.57 $\pm$ 0.06   / 0.16          / 4.79                        / 0.74   / |
| 12CO log nu0 vs log Sigma: slope and rho | m=0.66, rho=0.58 | 0.06 (slope) | dimensionless | 5 | / 0.66 $\pm$ 0.06 / 2.25 $\pm$ 0.04   / 0.24          / 7.18                        / 0.58   / |
| Scatter of 12CO clumps from fiducial relation | 0.24 | not stated | dex | 5 | ($\varepsilon = 0.24$ dex) |
| Mass fraction in 12CO clumps below virial / between virial and equipartition / above equipartition | 31% / 29% / 5% | not stated | percent of total mass | 3 | In $^{12}$CO, 31% of the total mass of the 9 clouds is in clumps below virial equilibrium, 29% is in clumps between virial equilibrium and equipartition, and 5% is in clumps above equipartition. |
| Fraction of total CO mass in clumps (12CO / 13CO) | 65% / 74% | not stated | percent | 2 | the $^{12}$CO clumps contain 65% of the total mass traced by $^{12}$CO and the $^{13}$CO clumps contain 74% of the total mass traced by $^{13}$CO |

## Qualitative findings

- Star-formation tracers explain more of the variance in linewidth normalization than surface density.  
  > "We find that star-formation tracers explain more of the variance in the residuals of the size-linewidth relation than the molecular surface density can due to higher correlation coefficients and lower RMS scatter." (Conclusions)
- Excess linewidths are not explained by opacity broadening.  
  > "We do not find evidence that the observed offsets in linewidth from the size-linewidth relation can be explained by broadened linewidths from optically-thick regions." (Conclusions)

## Claim tuples

- H: Stellar feedback contributes to clump linewidths beyond gravity-driven models | E: Correlate log nu0 residuals from fiducial relation with 8um, Halpha, u_nu, and Sigma | R: All three tracers have rho>0.5 and lower scatter than Sigma fits | F: Feedback likely injects energy at parsec scales | **supported**
- H: Clumps lie at a single virial parameter | E: Compute alpha_vir and compare with tracers | R: Clumps span an order of magnitude in alpha_vir with weak correlation with tracers | F: Gravity-only models do not explain the clumps; link to feedback is only suggestive | **partially**
- H: Opacity broadening causes excess linewidth | E: Correlate mean 13CO optical depth with nu0 | R: Uncorrelated (|rho|<0.2) | F: Opacity broadening does not account for the excess | **supported**

## Reasoning

- Why this data: Extend Wong et al. 2019 sample and include new 30 Dor data to cover a large range of CO brightness  
  > "we assemble a matched, high-resolution sample of nine clouds in the LMC, covering a large range of CO brightness" (Introduction)
- Why this method: _not stated_
- Alternative: Variable R21 prescription from 8um rejected for minor impact  
  > "Because this prescription of $R_{21}$ does not significantly impact our results, we proceed with the analysis using the uniform value of $R_{21}$." (2.4 12CO- and 13CO-Based Clump Properties)
- Alternative: Halpha extinction correction not applied due to coarse reddening maps  
  > "These coarse reddening maps may not be representative of the extinction in GMCs, so we do not employ this method in our study" (2.3 IR and Optical Star Formation Indicators)
- How they decided it was enough: _not stated_
- Limitation (authors): LTE assumptions, possibly optically thin 12CO; sensitivity limited to several Msun/pc^2  
  > "the effects of optically thin $^{12}$CO on our mass estimates remains uncertain." (4.3 Caveats and future directions)
- Limitation (authors): 8um may trace gas column rather than star formation at these scales  
  > "These results indicate that $8\ensuremath{\mu}m$ could be preferentially tracing molecular gas column densities over star formation" (2.3 IR and Optical Star Formation Indicators)
- Caveat (inferred, ours): Correlation does not establish causation; tracers and linewidth may share hidden drivers
- Caveat (inferred, ours): Coarse 13 pc dust model resolution versus parsec-scale clumps
- Caveat (inferred, ours): Heterogeneous native data combined; noise injection alters data
- Caveat (inferred, ours): Clump-averaged correlation with clump definitions depending on SCIMES settings

## Reproducibility

- Data public (paper): Archival ALMA data; published cubes  
  > "we describe the archival ALMA observations of CO and ancillary observations of star-formation tracers" (1 Introduction)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Reduced cubes from earlier papers or recalibration recipe
- Missing: SCIMES settings and LTE details
- Missing: Code for noise matching and fits
- Data volume (inferred): Tens of GB (reduced cubes of nine mosaics from published products); much more if recalibrated from raw data
- Score (inferred): 3/5, Data public and many parameters given, but SCIMES and LTE details and reliance on previously reduced cubes leave gaps.
- Rediscovery candidate: no, Recipe relies on other papers' reduced cubes and unstated SCIMES/LTE settings, though results are numeric.

## Links

- Method: (cite: rosolowsky_bias-free_2006) (Bias-free property measurement and bootstrap errors)
- Method: (cite: leroy_portrait_2016) (Spectral response correction)
- Method: (cite: colombo_graph-based_2015) (SCIMES algorithm)
- Companion: (cite: wong_relations_2019) (Source of LTE method and cubes for five clouds)
- Companion: (cite: wong_30_2022) (30 Doradus ALMA data)
- Companion: (cite: wong_alma_2017) (Earlier LMC size-linewidth study of PCC)
- Related: SAGE
- Related: MCELS

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 58,
  "rate": 0.617
 },
 "evidence_ok": true
}
```
