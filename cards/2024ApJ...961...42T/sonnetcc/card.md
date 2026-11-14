# Star Formation Efficiency in Nearby Galaxies Revealed with a New CO-to-H<SUB>2</SUB> Conversion Factor Prescription

`2024ApJ...961...42T` | The Astrophysical Journal 2024 | first author: Teng, Yu-Hsuan | arXiv: 2310.16037 | DOI: 10.3847/1538-4357/ad10ae

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: How does the CO-to-H2 conversion factor (alpha_CO) depend on local CO velocity dispersion at 150 pc scales, and how does a velocity-dispersion-based alpha_CO prescription change the star formation efficiency (depletion time) in centers and disks of 65 PHANGS galaxies  
  > "we investigate the dependence of $\alpha_\mathrm{CO}$ on local CO velocity dispersion at 150 pc scales using a new set of dust-based $\alpha_\mathrm{CO}$ measurements" (abstract); "Based on this prescription, we estimate the SFE in a sample of 65 galaxies from the PHANGS–ALMA survey." (abstract)
- Target **65 PHANGS-ALMA galaxies (12 with dust-based alpha_CO)**: coordinates _not stated_; z/distance Per-galaxy distances in Table 1 column Dist. [Mpc] (e.g. 3.7 Mpc for NGC5128, 23.6 Mpc for NGC3507)  
  > "In their sample, 8 barred and 4 non-barred galaxies from PHANGS have dust-based $\alpha_\mathrm{CO}$ measurements" (2.2 Dust-based alpha_CO Measurements); "NGC5128 & 0 & 3.7 & 45.3 & 32.2" (Table 1); "NGC3507 & 1 & 23.6 & 21.7 & 55.8" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.00803.S, 2013.1.01161.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00766.S, 2017.1.00886.L, 2018.1.01321.S, 2018.1.01651.S, 2018.A.00062.S
- bands: _not stated_
- frequencies and spectral setup: PHANGS CO data velocity resolution ~2.5 km/s  
  > "which is the velocity resolution of the PHANGS CO data" (Footnote 2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO(2–1) beam sizes of 150 pc or smaller  
  > "This sample from PHANGS has high-resolution CO(2–1) data with beam sizes of 150 pc or smaller." (2.1 PHANGS Datasets)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS–ALMA survey data via the Sun et al. (2022) database; ALMA data listed in the acknowledgments  
  > "assembled multi-wavelength measurements of 80 galaxies from the PHANGS–ALMA survey" (2.1 PHANGS Datasets); "This paper makes use of the following ALMA data:" (Acknowledgments)
- Line: CO J=2-1 (data); J=1-0 (alpha_CO convention, converted with R21 = 0.65) (not stated)
- Other facility **WISE**: data products used in the work (specific quantity not stated in this paper)  
  > "This work is based in part on data products from the Wide-field Infrared Survey Explorer" (Acknowledgments)
- Other facility **Herschel**: listed under Facilities; role not described in this paper  
  > "ALMA, WISE, Herschel, VLA" (Facilities)
- Other facility **VLA**: listed under Facilities; role not described in this paper  
  > "ALMA, WISE, Herschel, VLA" (Facilities)
- External data: Database of multi-wavelength measurements in 1.5 kpc hexagonal apertures (velocity dispersion at 150 pc, CO(2–1) intensity, Sigma_star, Sigma_SFR, metallicity)  
  > "leveraging a database developed by (cite: 2022AJ....164...43S)" (2.1 PHANGS Datasets); "we extract multiple physical quantities in matched hexagonal apertures with fixed sizes of 1.5 kpc" (2.1 PHANGS Datasets) [from (cite: 2022AJ....164...43S)]
- External data: Dust-based alpha_CO measurements at 2 kpc resolution for 41 galaxies (12 PHANGS galaxies used)  
  > "The authors assumed a constant dust-to-metals ratio to constrain the total gas mass with dust and metallicity measurements." (2.2 Dust-based alpha_CO Measurements); "which have dust-inferred $\alpha_\mathrm{CO}$ values at kpc scales (from (cite: 2023arXiv231100407C)" (1 Introduction) [from (cite: 2023arXiv231100407C)]
- External data: Stellar bar classification of PHANGS galaxies  
  > "we adopt the classification of stellar bars for PHANGS galaxies (cite: 2021A&A...656A.133Q)" (2.1 PHANGS Datasets) [from (cite: 2021A&A...656A.133Q)]
- External data: PG16S (S-calibration) gas-phase metallicity used for the 12 galaxies with dust-based alpha_CO  
  > "is based on the S-calibration in (cite: 2016MNRAS.457.3678P)" (2.2 Dust-based alpha_CO Measurements) [from (cite: 2016MNRAS.457.3678P)]
- External data: Purely metallicity-dependent alpha_CO prescription used for comparison  
  > "the purely metallicity-dependent $\alpha_\mathrm{CO}$ prescription from (cite: 2017MNRAS.464.3315A)" (3.2 Comparison to Previous Literature) [from (cite: 2017MNRAS.464.3315A)]
- External data: Tentative alpha_CO prescription combining metallicity and stellar mass surface density, used for comparison (author citation marker missing in the paper text)  
  > "also suggested a tentative prescription" (3.2 Comparison to Previous Literature) [from citation marker not preserved in the paper text]

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
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: CO(2–1) beam sizes of 150 pc or smaller (PHANGS data)  
  > "high-resolution CO(2–1) data with beam sizes of 150 pc or smaller" (2.1 PHANGS Datasets)
- final rms: _not stated_

### Inherited from earlier work

- Correction of PHANGS quantities for galaxy inclination and data sensitivity limits  
  > "All these quantities are corrected for the effects of galaxy inclination and data sensitivity limits (see (cite: 2022AJ....164...43S) for more details)." (2.1 PHANGS Datasets) [from (cite: 2022AJ....164...43S)]
- Metallicity calibration of the PHANGS dataset (PP04 O3N2)  
  > "and calibrated based on (cite: 2004MNRAS.348L..59P)" (2.1 PHANGS Datasets) [from (cite: 2004MNRAS.348L..59P)]
- alpha_CO(2-1) measurements derived from the PHANGS CO(2–1) data  
  > "The $\alpha_\mathrm{CO}$ measurements in were derived based on the PHANGS CO(2–1) data" (2.2 Dust-based alpha_CO Measurements) [from (cite: 2023arXiv231100407C), cited as the source of the dust-based alpha_CO]
- Velocity dispersion at 90 and 150 pc scales does not vary strongly  
  > "Because $\Delta v$ does not vary strongly between 90 and 150 pc scales (cite: 2022AJ....164...43S)" (3.1 A Velocity Dispersion-based alpha_CO Prescription) [from (cite: 2022AJ....164...43S)]

### Not stated but needed to reproduce (our reading)

- Exact file/version of the Sun et al. (2022) PHANGS database and the Chiang et al. (2023) alpha_CO table used
- How the 2 kpc alpha_CO pixels were matched to 1.5 kpc hexagonal apertures in the nearest-neighbor matching (matching radius, tie handling)
- Initial guesses and any weights or bounds passed to curve_fit
- Exact threshold values applied to the completeness cut in the fit (stated only as ~3 km/s in velocity dispersion and Z' >~ 0.6)
- How the mean/median depletion times of centers and disks are aggregated (per hexagon or per galaxy) and how the percentile ranges are computed
- Which SFR tracer and calibration lies behind Sigma_SFR (not described in this paper)
- The citation and exact form of the Sigma_star-dependent prescription (citation marker is missing in the text)
- How the four tested prescriptions (MW, metallicity-based, Sigma_star plus metallicity, this work) are implemented for all 65 galaxies, including the PG16S/PP04 conversion for the Accurso et al. prescription
- How the 1.5 kpc aperture size relates to the ~2 kpc central aperture used for 'center' in footnote 3

## Analysis recipe

1. **Assemble PHANGS measurements in 1.5 kpc apertures**: Extract velocity dispersion, CO(2–1) intensity, stellar mass surface density, SFR surface density and metallicity from the Sun et al. database in matched hexagonal apertures  
  > "we extract multiple physical quantities in matched hexagonal apertures with fixed sizes of 1.5 kpc" (2.1 PHANGS Datasets)
   - parameter: Sample: 65 galaxies, the overlap of the bar classification and the Sun et al. database  
  > "which is the overlap between (cite: 2021A&A...656A.133Q) and (cite: 2022AJ....164...43S)" (2.1 PHANGS Datasets)
   - parameter: Centers: central ~2 kpc-sized aperture at R_gal=0; disks are the remaining measurements  
  > "refers to the central $\sim$2 kpc-sized aperture at $R_\mathrm{gal}$=0" (Footnote 3)
   - fitting: _not stated_
   - validation: _not stated_
2. **Match dust-based alpha_CO to velocity dispersion and define the complete regime**: Nearest-neighbor matching of 2 kpc alpha_CO measurements to the intensity-weighted 150 pc velocity dispersion averaged over 1.5 kpc apertures; completeness per bin as fraction of pixels with reliable alpha_CO  
  > "we use nearest-neighbor matching to relate the $\alpha_\mathrm{CO}$ measurements at 2-kpc scales with the velocity dispersion which is measured at 150-pc scale" (3.1 A Velocity Dispersion-based alpha_CO Prescription); "we calculate for each parameter bin the number of pixels with reliable $\alpha_\mathrm{CO}$ measurements divided by the number of pixels with measured $\Delta v$ or $Z'$" (2.2 Dust-based alpha_CO Measurements)
   - parameter: alpha_CO data coverage insufficient for velocity dispersion below ~3 km/s; metallicity completeness drops below Z' ~0.6  
  > "This means that our $\alpha_\mathrm{CO}$ data coverage is insufficient to accurately represent regions with $\Delta v \lesssim 3$ km s$^{-1}$." (2.2 Dust-based alpha_CO Measurements)
   - assumption: CO(2–1)/(1–0) ratio R21 = 0.65 used to convert alpha_CO(2-1) to alpha_CO(1-0)  
  > "by assuming a CO(2–1)/(1–0) ratio ($R_{21}$) of 0.65" (2.2 Dust-based alpha_CO Measurements)
   - fitting: _not stated_
   - validation: Checked that using a SFR-dependent R21 does not change results qualitatively  
  > "we have checked that using such $\alpha_\mathrm{CO}$ does not change any of our results qualitatively" (2.2 Dust-based alpha_CO Measurements)
3. **Fit alpha_CO versus velocity dispersion power law**: Least-squares fit in log-log space of the complete-regime data (~1600 points from 12 galaxies) with scipy curve_fit  
  > "we conduct a least-squares fitting in log-log space based on the remaining $\sim$1600 data points, using the `curve_fit` function in `scipy.optimize`" (3.1 A Velocity Dispersion-based alpha_CO Prescription)
   - software: scipy
   - parameter: Fit: log alpha_CO = -0.81 log <dv>_150pc + 1.05 (alpha_CO in Msun (K km/s pc^2)^-1, dv in km/s)  
  > "\log \alpha_\mathrm{CO} = -0.81\ \log \langle \Delta v \rangle_\mathrm{150pc} + 1.05" (3.1 A Velocity Dispersion-based alpha_CO Prescription)
   - fitting: Ordinary least squares via curve_fit, no priors or sampler  
  > "$\sigma \sim 0.12$ dex, and the standard deviation error returned by `curve_fit` is $\pm$0.02 for both the fitted slope and intercept" (3.1 A Velocity Dispersion-based alpha_CO Prescription)
   - validation: Fit consistent with binned medians; similar fit for six galaxies at 90 pc scale; agrees with earlier fit on three barred galaxy centers  
  > "and is consistent with the trend of the binned $\alpha_\mathrm{CO}$ medians" (3.1 A Velocity Dispersion-based alpha_CO Prescription); "we also find a similar best-fit relation (dotted line) for six of those galaxies where $\langle \Delta v \rangle_\mathrm{90pc}$ is available" (3.1 A Velocity Dispersion-based alpha_CO Prescription)
4. **Compare with metallicity- and Sigma_star-based prescriptions**: Fit alpha_CO versus Z', compare residuals of each fit against the other variable, and compare predictions of the two prescriptions on PHANGS galaxies using kpc-scale Z' and Sigma_star  
  > "we relate the residuals of each $\alpha_\mathrm{CO}$ fit with $Z'$ or $\langle \Delta v \rangle_\mathrm{150pc}$" (3.2 Comparison to Previous Literature); "using kpc-scale $Z'$ and $\Sigma_\mathrm{star}$" (3.2 Comparison to Previous Literature)
   - assumption: Sigma_mol neglected in the Sigma_star-based prescription because Sigma_mol << Sigma_star  
  > "we neglect $\Sigma_\mathrm{mol}$ in Equation" (3.2 Comparison to Previous Literature)
   - assumption: PG16S-based Z' for the 12 galaxies; PP04-based Z' across the full sample  
  > "we use the PP04-based $Z'$ when implementing metallicity-dependent $\alpha_\mathrm{CO}$ prescriptions across the full sample for consistency" (2.2 Dust-based alpha_CO Measurements)
   - fitting: _not stated_
   - validation: No trend between residuals of the velocity-dispersion fit and metallicity; residuals of the metallicity fit decrease with velocity dispersion  
  > "Above the completeness limit, we find no trend between the residuals from the $\Delta v$ prescription and metallicity." (3.2 Comparison to Previous Literature)
5. **Derive depletion times in the 12 galaxy centers**: t_dep = Sigma_mol / Sigma_SFR = alpha_CO * I_CO / Sigma_SFR using measured alpha_CO versus MW alpha_CO  
  > "t_\mathrm{dep} = \Sigma_\mathrm{mol}\ /\ \Sigma_\mathrm{SFR} = \alpha_\mathrm{CO} \cdot I_\mathrm{CO}\ /\ \Sigma_\mathrm{SFR}" (3.3 Star Formation Efficiency in Galaxy Centers); "we derive $t_\mathrm{dep}$ for the 12 galaxy centers with $\alpha_\mathrm{CO}$ measurements" (3.3 Star Formation Efficiency in Galaxy Centers)
   - assumption: Standard MW alpha_CO of 4.35 (6.7 for alpha_CO(2-1)) Msun (K km/s pc^2)^-1  
  > "the standard MW $\alpha_\mathrm{CO}$ of 4.35 (or 6.7 in terms of $\alpha_\mathrm{CO(2-1)}$)" (3.3 Star Formation Efficiency in Galaxy Centers)
   - fitting: _not stated_
   - validation: _not stated_
6. **Apply prescriptions to all 65 galaxies and compare t_dep**: Compute Sigma_mol and t_dep with four alpha_CO prescriptions (MW, metallicity-based, Sigma_star-based, this work) and compare distributions in barred/non-barred centers and disks, plus the molecular Kennicutt-Schmidt relation  
  > "we investigate the impact of different $\alpha_\mathrm{CO}$ prescriptions on SFE or $t_\mathrm{dep}$ in the centers and disks of barred and non-barred galaxies" (3.4 Systematic Impact on Star Formation Efficiency); "All four prescriptions tested in this work show similar $t_\mathrm{dep}$ of 2–3 Gyr" (4 Conclusions)
   - parameter: Measurements at 1.5 kpc scale across all 65 galaxies  
  > "across all 65 galaxies measured at the 1.5-kpc scale" (3.4 Systematic Impact on Star Formation Efficiency)
   - fitting: _not stated_
   - validation: Short t_dep in barred centers compared with simulations of bar-driven inflow  
  > "Such a short time scale is supported by recent simulations of galaxy centers including effects from bar-driven inflows" (3.4 Systematic Impact on Star Formation Efficiency)

## Software

- **scipy** : curve_fit least-squares power-law fit of alpha_CO versus velocity dispersion  
  > "using the `curve_fit` function in `scipy.optimize`" (3.1 A Velocity Dispersion-based alpha_CO Prescription)
- **numpy** : _not stated_
- **astropy** : _not stated_
- **matplotlib** : _not stated_
- **ipython** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Slope of log alpha_CO versus log <dv>_150pc | -0.81 | ±0.02 | dimensionless | 3 | \log \alpha_\mathrm{CO} = -0.81\ \log \langle \Delta v \rangle_\mathrm{150pc} + 1.05; the standard deviation error returned by `curve_fit` is $\pm$0.02 for both the fitted slope and intercept |
| Intercept of log alpha_CO versus log <dv>_150pc | 1.05 | ±0.02 | log10 of Msun (K km/s pc^2)^-1 | 3 | \log \alpha_\mathrm{CO} = -0.81\ \log \langle \Delta v \rangle_\mathrm{150pc} + 1.05 |
| Scatter of alpha_CO about the velocity dispersion fit | ~0.12 | not stated | dex | 3 | $\sigma \sim 0.12$ dex, and the standard deviation error returned by `curve_fit` is $\pm$0.02 for both the fitted slope and intercept |
| Scatter of alpha_CO with metallicity Z' | 0.3 | not stated | dex | 4 | the scatter of the observed $\alpha_\mathrm{CO}$ is $\sigma \sim$0.1 dex with $\langle \Delta v \rangle_\mathrm{150pc}$ and 0.3 dex with $Z'$ |
| Scatter between velocity-dispersion-based and Sigma_star-based alpha_CO predictions | ~0.5 | not stated | dex | 4 | the two prescriptions show an overall match with a $\sim$0.5 dex scatter |
| Median t_dep of 12 barred centers with measured alpha_CO | 0.6 | not stated | Gyr | 5 | the median $t_\mathrm{dep}$ of barred and non-barred centers becomes 0.6 Gyr and 2.0 Gyr, respectively |
| Median t_dep of 12 non-barred centers with measured alpha_CO | 2.0 | not stated | Gyr | 5 | the median $t_\mathrm{dep}$ of barred and non-barred centers becomes 0.6 Gyr and 2.0 Gyr, respectively |
| Ratio of median t_dep with MW alpha_CO to that with measured alpha_CO (12 centers) | 4–5 | not stated | dimensionless | 5 | the median $t_\mathrm{dep}$ with the MW $\alpha_\mathrm{CO}$ is 4–5 times longer than that with the measured $\alpha_\mathrm{CO}$ |
| Mean/median t_dep in barred galaxy centers (65 galaxies, this prescription) | ~700 | 16th–84th percentile 0.3–1.6 Gyr | Myr | 6 | the mean/median of $t_\mathrm{dep}$ in barred galaxy centers ($\sim$700 Myr) being 3 times shorter than in non-barred centers (${\sim}2.1$ Gyr); The 16th–84th percentile ranges for $t_\mathrm{dep}$ in barred and non-barred centers is 0.3–1.6 and 0.8–3.6 Gyr, respectively. |
| Mean/median t_dep in non-barred galaxy centers (65 galaxies, this prescription) | ~2.1 | 16th–84th percentile 0.8–3.6 Gyr | Gyr | 6 | the mean/median of $t_\mathrm{dep}$ in barred galaxy centers ($\sim$700 Myr) being 3 times shorter than in non-barred centers (${\sim}2.1$ Gyr); The 16th–84th percentile ranges for $t_\mathrm{dep}$ in barred and non-barred centers is 0.3–1.6 and 0.8–3.6 Gyr, respectively. |
| Median t_dep in barred centers (conclusions form) | 0.7 | +0.9/-0.4 | Gyr | 6 | median $t_\mathrm{dep}$ (0.7$^{+0.9}_{-0.4}$ Gyr) being 3 times shorter than in non-barred galaxy centers (2.1$^{+1.5}_{-1.3}$ Gyr) |
| Median t_dep in non-barred centers (conclusions form) | 2.1 | +1.5/-1.3 | Gyr | 6 | median $t_\mathrm{dep}$ (0.7$^{+0.9}_{-0.4}$ Gyr) being 3 times shorter than in non-barred galaxy centers (2.1$^{+1.5}_{-1.3}$ Gyr) |
| Median t_dep in disks for all four prescriptions | 2–3 | not stated | Gyr | 6 | the median of $t_\mathrm{dep}$ remains consistent at 2–3 Gyr across all four prescriptions |
| Median Sigma_mol of barred centers relative to non-barred centers, MW-like alpha_CO | 3 times higher | not stated | dimensionless | 6 | the median $\Sigma_\mathrm{mol}$ of barred centers is 3 times higher than that of non-barred centers if using a MW-like $\alpha_\mathrm{CO}$ |
| Median Sigma_mol of barred centers relative to non-barred centers, this prescription | 1.3 times higher | not stated | dimensionless | 6 | our $\alpha_\mathrm{CO}$ prescription results in only 1.3 times higher $\Sigma_\mathrm{mol}$ in barred centers |

## Qualitative findings

- Velocity dispersion is a tracer of alpha_CO variations in both centers and disks; the metallicity trend in this regime may come from the correlation between Z' and velocity dispersion  
  > "We have checked that the $\alpha_\mathrm{CO}$ correlation with $Z'$ seen in this regime may come from the correlation between $Z'$ and $\Delta v$" (3.2 Comparison to Previous Literature)
- Adopting MW alpha_CO may overestimate Sigma_mol in galaxy centers by a factor of 5  
  > "may overall be overestimated by a factor of 5 with the MW $\alpha_\mathrm{CO}$" (3.4 Systematic Impact on Star Formation Efficiency)

## Claim tuples

- H: Local CO velocity dispersion at ~150 pc traces alpha_CO variations across galaxy centers and disks | E: Match dust-based alpha_CO (12 PHANGS galaxies) to 150 pc velocity dispersion and fit a log-log power law in the complete regime | R: Inverse power law with slope -0.81 and 0.12 dex scatter | F: Velocity dispersion is useful for predicting alpha_CO; prescription valid for Z' above 0.6 and velocity dispersion above ~3 km/s | **supported**
- H: A velocity-dispersion prescription predicts alpha_CO better than metallicity-based prescriptions | E: Compare scatter and residual trends of velocity-dispersion and metallicity fits | R: Scatter 0.1 dex versus 0.3 dex; metallicity-fit residuals decrease with velocity dispersion | F: Significant improvement over metallicity-dependent prescriptions | **supported**
- H: SFE differs between barred and non-barred galaxy centers when alpha_CO variations are accounted for | E: Compute t_dep in centers of 65 PHANGS galaxies with four alpha_CO prescriptions | R: t_dep ~700 Myr in barred centers versus ~2.1 Gyr in non-barred centers with this prescription; other prescriptions differ by < 0.2 dex | F: Barred centers have 3 times shorter depletion time (higher SFE) | **supported**
- H: Disk depletion times depend on the alpha_CO prescription | E: Compare disk t_dep across four prescriptions | R: Median t_dep remains 2–3 Gyr for all prescriptions | F: Disk depletion time is insensitive to the prescription | **supported**
- H: High star formation activity in barred centers is due to gas accumulation alone | E: Compare Sigma_mol and t_dep between barred and non-barred centers under MW and new alpha_CO | R: Median Sigma_mol of barred centers 1.3 times higher with the new prescription (3 times with MW alpha_CO) | F: Enhanced SFE, not only more gas, drives activity in barred centers | **supported**

## Reasoning

- Why this data: PHANGS sample has CO(2–1) data with beam sizes of 150 pc or smaller, matching the scale of the velocity dispersion  
  > "This sample from PHANGS has high-resolution CO(2–1) data with beam sizes of 150 pc or smaller." (2.1 PHANGS Datasets)
- Why this method: Velocity dispersion can be obtained directly from CO data, so no ancillary multi-band data are needed to estimate alpha_CO  
  > "Another advantage is that $\Delta v$ can be directly obtained from the CO data." (3.2 Comparison to Previous Literature)
- Alternative: SFR-dependent R21 alpha_CO(1-0) did not change results qualitatively (trend could be 30–40% shallower)  
  > "we have checked that using such $\alpha_\mathrm{CO}$ does not change any of our results qualitatively" (2.2 Dust-based alpha_CO Measurements)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO data coverage insufficient for velocity dispersion below ~3 km/s  
  > "This means that our $\alpha_\mathrm{CO}$ data coverage is insufficient to accurately represent regions with $\Delta v \lesssim 3$ km s$^{-1}$." (2.2 Dust-based alpha_CO Measurements)
- Limitation (authors): Prescription calibrated on CO(2–1) velocity dispersion, may differ for higher-J CO lines  
  > "We remind readers that our prescription is calibrated to $\langle \Delta v \rangle_\mathrm{150pc}$ in CO (2–1)" (3.2 Comparison to Previous Literature)
- Limitation (authors): Metallicity effects included in the velocity-dispersion prescription may only hold for MW-like star-forming disk galaxies as in PHANGS  
  > "might only be true in the context of MW-like star-forming disk galaxies as represented by the PHANGS sample" (4 Discussion)
- Caveat (inferred, ours): The prescription is calibrated on only 12 galaxies (8 barred, 4 non-barred), then applied to 65 galaxies including extrapolation in environments poorly sampled
- Caveat (inferred, ours): Dust-based alpha_CO assumes a constant dust-to-metals ratio and is measured at 2 kpc but applied at 1.5 kpc apertures
- Caveat (inferred, ours): Depletion times depend directly on the calibrated alpha_CO, so barred-versus-non-barred contrast partly inherits the calibration; no propagated uncertainty on the prescription is reported
- Caveat (inferred, ours): Fixed R21 = 0.65 affects the normalisation of alpha_CO and t_dep

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Exact files of the PHANGS aperture database and the dust-based alpha_CO table
- Missing: Details of the nearest-neighbor matching and the curve_fit setup
- Missing: Implementation of the comparison prescriptions across the 65 galaxies
- Missing: No code or data release is stated in the paper
- Data volume (inferred): Small: derived tables of 1.5 kpc aperture measurements for 65 galaxies plus ~2000 matched alpha_CO pixels (MB scale); no raw ALMA visibilities are reprocessed
- Score (inferred): 3/5, Inputs are published PHANGS products and the fit is a simple power law with numeric results, but data location, matching details and comparison prescription implementations are not given in this paper.
- Rediscovery candidate: yes, PHANGS-ALMA derived products and the dust-based alpha_CO measurements are public published works; the main fit and depletion-time results are numeric and the analysis is a simple fit, though matching details must be inferred.

## Links

- Method: (cite: 2022AJ....164...43S) (Source of the PHANGS multi-wavelength aperture database, velocity dispersion at 150 pc and corrections)
- Method: (cite: 2021ApJS..257...43L) (PHANGS-ALMA survey CO(2–1) data)
- Method: (cite: 2023arXiv231100407C) (Dust-based alpha_CO measurements used for calibration)
- Companion: (cite: 2022ApJ...925...72T) (Earlier multi-CO isotopologue alpha_CO study in galaxy centers)
- Companion: (cite: 2023ApJ...950..119T) (Earlier alpha_CO versus line width relation in three barred galaxy centers)
- Related: PHANGS-ALMA

## Checks

```json
{
 "quotes": 96,
 "quotes_ok": 96,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 11,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 48,
  "rate": 0.511
 },
 "evidence_ok": true
}
```
