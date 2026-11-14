# XLSSC 122 caught in the act of growing up: Spatially resolved SZ observations of a z = 1.98 galaxy cluster

`2024A&A...689A..41V` | Astronomy and Astrophysics 2024 | first author: van Marrewijk, J. | arXiv: 2310.06120 | DOI: 10.1051/0004-6361/202348213

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz
- Question: What are the dynamical state and morphology of the ICM of the z=1.98 cluster XLSSC 122, as traced by resolved SZ observations?  
  > "We study the dynamical state and morphology of the $z=1.98$ galaxy cluster XLSSC 122 with high-resolution observations ($\approx 5 \ensuremath{''}$) of the ICM through the Sunyaev-Zeldovich (SZ) effect." (abstract)
- Target **XLSSC 122**: coordinates RA 2°17′44.2128″, Dec -3°45′31.68″  
  > "The cluster can be found at an RA and Dec of 2°17′44.2128″ , -3°45′31.68″ ." (2 Observations of XLSSC 122); "found the average spectroscopic redshift to be $z=1.98$." (2 Observations of XLSSC 122); z/distance z = 1.98  
  > "The cluster can be found at an RA and Dec of 2°17′44.2128″ , -3°45′31.68″ ." (2 Observations of XLSSC 122); "found the average spectroscopic redshift to be $z=1.98$." (2 Observations of XLSSC 122); distance from HST WFC3 spectroscopy of 37 members (Willis2020)  
  > "The cluster can be found at an RA and Dec of 2°17′44.2128″ , -3°45′31.68″ ." (2 Observations of XLSSC 122); "found the average spectroscopic redshift to be $z=1.98$." (2 Observations of XLSSC 122)

## Data provenance

- ALMA projects: 2016.1.00698.S, 2018.1.00478.S
- bands: ALMA/ACA Band 3 (SZ); ALMA Band 4 (point-source contamination)  
  > "archival yet unpublished ALMA and ACA Band 3 observations" (2.1 The Atacama Large Millimeter/Submillimeter Array); "we make use of ancillary ALMA Band 4 observations" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- frequencies and spectral setup: Band 3 SPWs 89.51–91.50, 91.45–93.44, 101.51–103.49, 103.51–105.49 GHz, continuum mode  
  > "89.51–91.50, 91.45–93.44, 101.51–103.49, and 103.51–105.49 GHz, observed in continuum mode" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- continuum bandwidth: _not stated_
- arrays: 12m array and 7m ACA, mosaics of 11 (ALMA) and 5 (ACA) pointings  
  > "with the ACA observations consisting of five pointings and the ALMA observations consisting of 11" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ACA 11'', ALMA 2''; tapered to 5'' for figures  
  > "with an angular resolution of $11\ensuremath{''}$ and $2\ensuremath{''}$, respectively" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- max recoverable scale: ACA 77'', ALMA 23'' per pointing  
  > "The maximum recoverable scales of the ACA and ALMA observations are $77\ensuremath{''}$ and $23\ensuremath{''}$ per pointing." (2.1 The Atacama Large Millimeter/Submillimeter Array)
- sensitivity: ACA 0.24 and ALMA 0.037 mJy/beam per pointing (central); Band 4 ~0.024 mJy/beam  
  > "reach a central continuum sensitivity of $0.24$ and $0.037$ mJy beam$^{-1}$ per pointing" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- time on source: ACA 3.9 h, ALMA 0.42 h  
  > "The total on-source time for the ACA and ALMA observations are 3.9 and 0.42 hours, respectively." (2.1 The Atacama Large Millimeter/Submillimeter Array)
- observing dates: ALMA 2016-10-22, ACA 2017-01-06, Band 4 2019-01-18  
  > "made on 2016-10-22 and 2017-01-06, respectively" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- pi or archival as stated: Archival, unpublished; PI A. Mantz (Band 3), J. Zavala (Band 4)  
  > "archival yet unpublished ALMA and ACA Band 3 observations" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- Other facility **ACT DR6**: 100 and 150 GHz maps for large-scale SZ flux  
  > "we use ACT maps at 100 and 150 GHz from DR6" (2.2 The Atacama Cosmology Telescope)
- Other facility **XMM-Newton**: X-ray surface brightness comparison  
  > "we henceforth only rely on the *XMM-Newton* observations." (2.3 Auxiliary)
- Other facility **Chandra**: archival X-ray, ~200 counts, not used for analysis  
  > "higher-resolution *Chandra* observations only collected $\approx 200$ source counts in 182.2 ksec" (2.3 Auxiliary)
- Other facility **HST**: optical imaging and member redshifts  
  > "the deep optical *~~HST~~* ~~-imaging~~ from (cite: Willis2020)" (2.3 Auxiliary)
- External data: Cluster member spectroscopic redshifts (Gold sample) for velocity dispersion  
  > "We used the cluster members in (cite: Willis2020) that were labeled as the “Gold” standard to derive the velocity dispersion." (7 Mass estimates) [from (cite: Willis2020)]
- External data: Averaged gNFW shape parameters for UPP/MD/CC profiles  
  > "we will freeze the shape parameters ($\alpha$, $\beta$, $\gamma$, and $c_{500}$) of the derived classifications at the averaged values derived from (cite: Arnaud2010) and (cite: McDonald2014)" (1.1 Pressure Profiles) [from (cite: Arnaud2010); (cite: McDonald2014)]
- External data: Global X-ray temperature kT = 5.0 keV and CARMA Y500 and offset  
  > "using an X-ray spectroscopic temperature of $kT = 5.0$ keV" (7 Mass estimates) [from (cite: Mantz2018)]

## Processing

### Calibration

- pipeline or manual: Band 3: calibrated MS from EU ARC calibrated measurement set service; Band 4: standard CASA pipeline  
  > "calibrated datasets were obtained through the calibrated measurement set service (cite: Petry2020) of the European ALMA Regional Center using CASA 5.4.0." (2.1 The Atacama Large Millimeter/Submillimeter Array); "reduced via the standard CASA 5.4.0 pipeline" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- casa version: CASA 5.4.0  
  > "using CASA 5.4.0" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5% calibration uncertainty; marginalized via Gaussian priors on per-dataset amplitude scale  
  > "any relativistic corrections fall within the calibration uncertainty of the ALMA and ACA observations ($\sim5\%$)" (1.2 The thermal Sunyaev-Zeldovich effect)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: tapered to 5'' FWHM beam for displayed maps  
  > "are tapered[^1] to have a beam with an FWHM of $5\ensuremath{''}$" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- cell size: _not stated_
- image size: _not stated_
- masking: Higher-frequency half of the SPW removed where bright lines from two interloper galaxies fall  
  > "we removed the higher-frequency half of the corresponding spectral window before continuum modeling" (4 Interloper and cluster member removal)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Modeling in uv-plane with each pointing modeled individually, combined at likelihood level; joint ALMA+ACA imaged map for display  
  > "we model each pointing individually and correct for the primary beam attenuation per field. The fields are combined at the likelihood level" (3.2 Visibility-based modeling of the ICM)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- uv-space Bayesian forward-modeling approach  
  > "Herewe rely on a *uv*-space Bayesian approach based on the work of (cite: DiMascolo2019a)." (3.2 Visibility-based modeling of the ICM) [from (cite: DiMascolo2019a)]
- ACT inter-map covariance estimation  
  > "we estimate inter-map covariance matrices using similar procedures to (cite: madhavacheril2020atacama)" (3.3 Joint likelihood modeling) [from (cite: madhavacheril2020atacama)]
- Pressure profile formalism and mass scaling  
  > "This formalism was introduced by (cite: Arnaud2010)" (1.1 Pressure Profiles) [from (cite: Arnaud2010); gNFW from (cite: Nagai2007)]
- Dynamical mass methodology  
  > "we adopt the methodology described in (cite: 2022A&A...659A.126A)" (7 Mass estimates) [from (cite: 2022A&A...659A.126A)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA/ACA uv-selection, channel binning and weights used in the visibility fits
- dynesty settings (live points, bounding, sampling)
- Exact ACT DR6 map products, beams, transfer functions and cutout size
- Tapering and tclean parameters for display images
- How evidence-weighted mass average across models is computed
- Y-to-M500 conversion implementation details
- Band 4 point-source model details and line-channel ranges removed

## Analysis recipe

1. **Model compact-source contamination**: Fit point-source models (RA, Dec, amplitude, spectral slope, calibration scales) jointly to Band 3 and Band 4 in the uv-plane with lower uv-cut of 11 kλ; subtract bright source before SZ modeling  
  > "with a lower *uv*-cut of 11 k$\lambda$ to exclude extended emission." (4 Interloper and cluster member removal)
   - software: dynesty
   - assumption: Unresolved sources are point-like with first-order polynomial spectral behaviour  
  > "Unresolved, compact sources are modeled using point-like (Dirac delta) emission models with a first-order polynomial to describe their spectral behavior." (4 Interloper and cluster member removal)
   - fitting: _not stated_
   - validation: No further sources found in posterior  
  > "we found no other region with a significant detection in the posterior distribution of the modeled parameters" (4 Interloper and cluster member removal)
2. **Single-component ICM forward modeling**: gNFW (theoretical) and A10/M14 template (empirical) pressure models integrated to Compton y, converted to SZ brightness per band, Fourier transformed, sampled at data uv-points with primary beam; Gaussian likelihood on unbinned visibilities; ACT likelihood added  
  > "We then apply the ALMA and ACA transfer function to the model to account for the missing baselines and compute the likelihood of the resulting model on the unbinned visibilities" (3 Methodology)
   - software: dynesty
   - parameter: Mostly flat priors; Gaussian priors on calibration and redshift  
  > "we mainly use flat priors except for the calibration and redshift uncertainty parameters which we marginalize over." (3.3 Joint likelihood modeling)
   - parameter: Evidence convergence threshold Δln B = 0.01  
  > "set to $\Delta\ln\mathcal{B}=0.01$" (3.3 Joint likelihood modeling)
   - assumption: Cosmology Planck2014_XIII, H0=67.7, Om=0.307; non-relativistic SZ (relativistic corrections neglected)  
  > "$H_0=67.7$ kms$^{-1}$Mpc$^{-1}$ and $\Omega_{\rm m} = 0.307$" (1 Introduction)
   - assumption: ACT and ALMA+ACA likelihoods independent  
  > "Hence, we assume no covariance between the ACA+ALMA observations and the ACT maps." (3.3 Joint likelihood modeling)
   - fitting: Static nested sampling with dynesty; significance from Bayes factor against null model  
  > "The implementation uses the static nested sampling method implemented in the `dynesty` package" (3.2 Visibility-based modeling of the ICM)
   - validation: Residual maps in uv plane; Bayes factor comparisons  
  > "The residuals in Figure [1] are obtained by subtracting the model in the visibility plane from the data." (5.1.1 The theoretical formalism)
3. **Image reconstruction (clean-like)**: Subtract best-fit likelihood-weighted gNFW model from visibilities, image residuals, add back model smoothed to 5'' and primary-beam attenuated  
  > "we add the imaged residuals (shown on the right panel of Fig. [1]) to the likelihood-weighted model, which is smoothed with the synthesized beam ($5\ensuremath{''}$)" (6.1 Cleaned image reconstruction)
   - fitting: _not stated_
   - validation: _not stated_
4. **Two-component modeling**: Two gNFW components (shape frozen to A10-UPP) with ordered declination prior; spherical and elliptical, with and without ACT  
  > "we used an ordered prior on the declinations of the centroids of the two SZ components" (6.2 Modeling asymmetric pressure distributions)
   - software: dynesty
   - fitting: Nested sampling, Bayes evidence relative to single-component fit  
  > "The latter translates to a Bayesian evidence difference of 6.6 with respect to the best single elliptical gNFW model, indicating a tentative $3.6\sigma$ detection of the second component" (Two component ICM modeling, Modeling asymmetric pressure distributions)
   - validation: Compared with cleaned image contours  
  > "we plot the contours from the cleaned image reconstruction" (6.2 Modeling asymmetric pressure distributions)
5. **Derive SZ and dynamical masses**: Evidence-weighted average of empirical-formalism masses (ALMA+ACA+ACT); velocity dispersion biweight of 32 members with Munari scaling, converted to M500 with colossus  
  > "Our SZ mass is calculated by taking the evidence-weighted average of the mass estimates from the empirical formalism runs" (7 Mass estimates)
   - software: colossus
   - parameter: A = 1177.0 km/s, alpha = 0.364  
  > "with $A = 1177.0$ km s$^{-1}$ and $\alpha = 0.364$" (7 Mass estimates)
   - assumption: Local scaling relations of Arnaud2010 used for Y to M500  
  > "we make use of local scaling relations from (cite: Arnaud2010) to convert $Y_{\rm 500,c}$ to an SZ-derived halo mass" (7 Mass estimates)
   - fitting: _not stated_
   - validation: Compared with X-ray, CARMA, ACT catalog masses  
  > "We also quote the derived cluster mass of XLSSC 122 as reported in the ACT cluster catalog (cite: Hilton2021)." (Mass estimates)
6. **Pseudo-temperature map**: Ratio of SZ flux over sqrt of X-ray surface brightness at ~5'' resolution  
  > "taking the ratio of the SZ flux over the square root of the X-ray surface brightness" (8.2 Thermodynamical implications)
   - assumption: Constant temperature along line of sight  
  > "under the assumption of constant temperature along the line of sight" (8.2 Thermodynamical implications)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0: calibration/reduction of ALMA and ACA data  
  > "using CASA 5.4.0" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- **dynesty** v2.1.0: static nested sampling and Bayesian evidence  
  > "static nested sampling method implemented in the `dynesty` package" (3.2 Visibility-based modeling of the ICM)
- **ciao** : Chandra reprocessing and merging  
  > "merge the *Chandra* observations into a flux-corrected image using the `ciao` tools" (2.3 Auxiliary)
- **colossus** : M200c to M500c conversion  
  > "as implemented by the `colossus` package" (7 Mass estimates)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SZ detection significance, ALMA+ACA | ~10.9–11.2 | not stated | sigma | 2 | we detect the SZ effect at $\sim10.9-11.2\sigma$ in the ACA+ALMA data |
| SZ detection significance, ALMA+ACA+ACT | 15 | not stated | sigma | 2 | which increases to $15\sigma$ when ACT observations are included |
| M500,c (SZ) | 1.66e14 | +0.23/-0.20 e14 | Msun | 5 | $M_{500,\mathrm{c}} = 1.66^{+0.23}_{-0.20} \times 10^{14}~\rm M_\odot$ |
| Eccentricity (ALMA+ACA+ACT) | 0.46 | +0.12/-0.16 | dimensionless | 2 | likelihood-weighted average of $e=0.46^{+0.12}_{-0.16}$ |
| Second component evidence, ALMA+ACA | Δln Z = 6.6 (3.6 sigma) | not stated | dimensionless | 4 | indicating a tentative $3.6\sigma$ detection of the second component |
| Second component evidence, with ACT | Δln Z = 3.0 (2.4 sigma) | not stated | dimensionless | 4 | (with the latter equivalent to a tentative $2.4\sigma$ preference) |
| Velocity dispersion sigma200,c | 1014 | 169 | km/s | 5 | We found a $\sigma_{200,\mathrm{c}} = 1014~\pm169$ km s$^{-1}$ |
| log10 M500,c dynamical | 14.69 | +0.13/-0.18 | log Msun | 5 | $\log_{10} M_{500,\mathrm{c}}^{\mathrm{dyn}} = 14.69^{+0.13}_{-0.18}~\rm M_\odot$ |
| Y(<r500,c) A10-MD | 2.0e-5 | +0.6/-0.4 e-5 | Mpc^2 | 2 | we find $Y(<r_{500,\mathrm{c}}) = 2.0^{+0.6}_{-0.4} \times 10^{-5}~\textnormal{Mpc}^2$ |
| SZ peak offset from BCG/X-ray peak | 10'' (80 kpc) | 1'' (7 kpc) | arcsec | 2 | offset from the BCG and the peak of the X-ray emission by $10\ensuremath{''}\pm 1\ensuremath{''}$ ($80\pm7$ kpc) |

## Qualitative findings

- Pressure profile consistent with local morphologically disturbed or distant relaxed templates; SZ better aligned with X-ray than CARMA suggested  
  > "In contrast to the previous works, we find better agreement between the SZ effect signal and the X-ray emission as well as the cluster member distribution." (abstract)
- SZ-derived mass lower than velocity-dispersion mass by ~2.5x  
  > "We find lower SZ-derived mass estimates than what is expected from the velocity-dispersion measurement ($\sim\times2.5$)." (7 Mass estimates)

## Claim tuples

- H: Is XLSSC 122 relaxed or dynamically disturbed? | E: Forward-model template pressure profiles to ALMA+ACA+ACT and compare Bayes evidence | R: A10-MD, M14-UPP and M14-CC preferred over others; e=0.46 | F: Cluster is non-cool-core relative to local, but disturbed/assembling | **supported**
- H: Is there a second SZ component? | E: Two-component gNFW models in uv-plane | R: Δln Z=6.6 (3.6σ) ALMA+ACA; 3.0 (2.4σ) with ACT | F: Tentative infalling group/filament in southeast | **partially**
- H: Does ALMA+ACA resolve the SZ-X-ray offset claimed with CARMA? | E: Compare SZ centroid with X-ray and BCG | R: SZ peak offset 10'' from X-ray peak, far less than CARMA's 35'' | F: Better agreement between SZ and X-ray | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-plane modeling avoids deconvolution issues and handles missing short baselines via parametric profile  
  > "Modeling in the *uv*-plane avoids issues related to the deconvolution of interferometric data" (3.2 Visibility-based modeling of the ICM)
- Alternative: Chandra data not used because of too few photons; only XMM-Newton used  
  > "Therefore, to study the diffuse ICM in XLSSC 122 from the X-ray perspective, we henceforth only rely on the *XMM-Newton* observations." (2.3 Auxiliary)
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of short baselines makes beta–P0 degeneracy and template discrimination weak; gNFW poorly suited for filaments  
  > "the lack of short baselines in the ALMA+ACA observations explains why the mass estimates vary between models" (5.1.2 The empirical formalism)
- Caveat (inferred, ours): Second-component detection is tentative and model dependent
- Caveat (inferred, ours): Mass relies on local scaling relations and ACT-dominated flux constraint
- Caveat (inferred, ours): Pseudo-temperature map relies on low-count X-ray data with isothermal-LOS assumption

## Reproducibility

- Data public (paper): Archival ALMA data obtained through ESO calibrated MS service  
  > "calibrated datasets were obtained through the calibrated measurement set service (cite: Petry2020)" (2.1 The Atacama Large Millimeter/Submillimeter Array)
- Products in archive: _not stated_
- Missing: Custom forward-modeling code not stated as released
- Missing: ACT DR6 cluster-region maps and covariance products
- Missing: Sampler configuration
- Data volume (inferred): ~tens of GB (ALMA+ACA Band 3 mosaics plus Band 4 and ACT cutouts)
- Score (inferred): 3/5, ALMA data public and method described, but custom code and ACT products are not specified or released.
- Rediscovery candidate: no, Requires unreleased custom uv-forward-modeling code and ACT maps.

## Links

- Method: (cite: DiMascolo2019a) (uv-plane Bayesian forward modeling approach)
- Method: (cite: Arnaud2010) (universal pressure profile and mass scaling)
- Companion: (cite: Mantz2018) (previous CARMA+X-ray analysis of XLSSC 122)
- Companion: (cite: DiMascolo2023) (ALMA+ACA SZ of Spiderweb for comparison)
- Related: ACT DR6
- Related: XXL survey

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 60,
  "rate": 0.682
 },
 "evidence_ok": true
}
```
