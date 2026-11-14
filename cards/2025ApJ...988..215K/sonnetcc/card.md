# Timescales of Polycyclic Aromatic Hydrocarbon and Dust Continuum Emission from Gas Clouds Compared to Molecular Gas Cloud Lifetimes in PHANGS-JWST Galaxies

`2025ApJ...988..215K` | The Astrophysical Journal 2025 | first author: Kim, Jaeyeon | arXiv: 2506.10063 | DOI: 10.3847/1538-4357/ade443

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: How long do gas clouds emit in PAH/dust mid-IR (JWST 7.7, 10, 11.3 um) relative to H-alpha, and how do these time-scales compare with CO molecular cloud lifetimes in 17 PHANGS galaxies  
  > "we measure the PAH and dust continuum emission lifetimes of gas clouds across 17 nearby star-forming galaxies" (abstract); "In most galaxies, the mid-IR time-scale closely matches the molecular cloud lifetime measured with CO." (abstract)
- Target **17 PHANGS-JWST Cycle 1 star-forming galaxies (NGC 0628, 1087, 1300, 1365, 1385, 1433, 1512, 1566, 1672, 2835, 3351, 3627, 4254, 4303, 4321, 4535, 5068)**: coordinates _not stated_; z/distance 5-20 Mpc (per-galaxy distances in Table 1)  
  > "our sample is composed of 17 galaxies in total." (2 Observational Data); "across the range of distances of our galaxy sample ($5-20$ Mpc)" (2.1 Mid-IR bands); "Distance from (cite: anand21) and inclination and position angle from (cite: lang20)" (Table 1); distance from (cite: anand21)  
  > "our sample is composed of 17 galaxies in total." (2 Observational Data); "across the range of distances of our galaxy sample ($5-20$ Mpc)" (2.1 Mid-IR bands); "Distance from (cite: anand21) and inclination and position angle from (cite: lang20)" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.01161.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00886.L, 2018.1.01651.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA CO data processed as part of the PHANGS-ALMA survey (not observed for this paper)  
  > "This paper makes use of the following ALMA data, which have been processed as part of the PHANGS–ALMA survey:" (Acknowledgments); "the CO data is from PHANGS-ALMA (cite: leroy21_survey)" (5.2 Galaxies with decorrelation between CO and mid-IR emission)
- Line: CO not stated (not stated)
- Other facility **JWST/MIRI (PHANGS-JWST Cycle 1, GO 2107)**: F770W, F1000W, F1130W mid-IR images tracing PAH and dust continuum, from MAST  
  > "We use mid-IR emission at 7.7 $\mu$m, 10 $\mu$m, and 11.3 $\mu$m observed with F770W, F1000W, and F1130W filters on MIRI on board JWST" (2.1 Mid-IR bands); "The PHANGS-JWST Cycle 1 Treasury program (GO 2107, PI Lee; (cite: lee23; williams24))" (2 Observational Data)
- Other facility **VLT/MUSE (PHANGS-MUSE)**: H-alpha line maps (star formation tracer) from Gaussian fits to the H-alpha line in the copt cubes  
  > "we use H$\alpha$ line maps obtained by a Gaussian fit to the H$\alpha$ line, accounting for the stellar continuum and Balmer line absorption." (2.2 MUSE H$\alpha$)
- External data: CO-based GMC evolutionary time-scales (including the H-alpha emitting time-scale t_s used as reference time-scale t_ref) and CO fitted parameters for comparison  
  > "by using the duration of the H$\alpha$-bright phase ($t_{\rm s}$) as a reference time-scale ($t_{\rm ref}$) which is measured in (cite: kim22)" (3 Method); "We also show results using CO as the gas tracer for comparison from (cite: kim22)." (4.1) [from (cite: kim22)]
- External data: Galaxy global properties (stellar mass, SFR, molecular gas mass, CO luminosity) from PHANGS-ALMA  
  > "Global stellar mass, SFR, molecular gas mass, and integrated CO luminosity from PHANGS–ALMA (cite: leroy19; leroy21_survey)." (Table 1) [from (cite: leroy19; leroy21_survey)]
- External data: Galaxy distances  
  > "Distance from (cite: anand21) and inclination and position angle from (cite: lang20)" (Table 1) [from (cite: anand21)]
- External data: kpc-scale surface densities, pressure and GMC free-fall and crossing times  
  > "We include mass weighted averages of kpc-scale galaxy properties measured by (cite: sun22)." (5.1 Correlations between global galaxy properties and cloud evolutionary time-scales) [from (cite: sun22)]
- External data: PHANGS-ALMA GMC catalog (CPROPS) used for mass-weighted GMC property averages  
  > "using the GMC catalog generated using the CPROPS algorithm (cite: rosolowsky21) for PHANGS-ALMA (cite: leroy21_survey) galaxies" (5.1 Correlations between global galaxy properties and cloud evolutionary time-scales) [from (cite: rosolowsky21)]
- External data: Kpc-scale CO flux completeness c  
  > "the mass-weighted average of CO flux completeness on the kpc-scale ($c$; from (cite: leroy21_pipe) and (cite: sun22))" (5.1 Correlations between global galaxy properties and cloud evolutionary time-scales) [from (cite: leroy21_pipe); (cite: sun22)]
- External data: Star formation history used to check the SFR-constancy requirement  
  > "Using the SFR history measured by (cite: pessa23), we verify that this condition is satisfied." (Accuracy of our measurements) [from (cite: pessa23)]
- External data: Average PAH abundance of HII regions R_PAH,Neb  
  > "the average PAH abundance of HII regions ($R_{\rm PAH, Neb}$) from (cite: sutter24)" (5.5 PAH abundance and feedback duration) [from (cite: sutter24)]
- External data: HII region ionization parameters  
  > "The data points are color-coded according to the ionization parameter, which is estimated in (cite: GROVES_HIICAT)" (5.5 PAH abundance and feedback duration) [from (cite: GROVES_HIICAT)]
- External data: CO-to-F770W scaling relation  
  > "based on the correlation from (cite: chown24)" (5.2 Galaxies with decorrelation between CO and mid-IR emission) [from (cite: chown24)]
- Simulation/model as data: STARBURST99 model used (instantaneous star formation 5 Myr ago) to compute the minimum stellar mass matching the H-alpha sensitivity  
  > "We obtain the initial mass using the STARBURST99 model with an assumption that star formation was instantaneous 5 Myr ago." (Accuracy of our measurements)

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
- masking: Same masks as Kim et al. 2022 (bright regions, most galactic centers), plus extra masking of exceedingly bright peaks (a peak at least twice as luminous as the next brightest); analysis limited to JWST-MUSE overlap  
  > "we use the same masks as (cite: kim22) and apply additional masks if extremely bright regions are present in mid-IR observations" (2.3 Post-processing images); "defined as a peak being at least twice as luminous as the next brightest peak" (2.3 Post-processing images)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: JWST maps convolved to the coarser H-alpha (MUSE) resolution with a kernel to a circular Gaussian PSF, then regridded to the H-alpha pixel grid  
  > "We first convolve finer-resolution JWST observations to match the coarser resolution of the H$\alpha$ observations" (2.3 Post-processing images); "we use a kernel that transforms the JWST PSF to a circular Gaussian PSF, generated following (cite: aniano11)" (2.3 Post-processing images)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- H-alpha reference time-scale t_ref (t_s) for converting relative durations to Myr  
  > "by using the duration of the H$\alpha$-bright phase ($t_{\rm s}$) as a reference time-scale ($t_{\rm ref}$) which is measured in (cite: kim22)" (3 Method) [from (cite: kim22)]
- Masks of bright regions and galactic centers  
  > "we use the same masks as (cite: kim22) and apply additional masks if extremely bright regions are present in mid-IR observations" (2.3 Post-processing images) [from (cite: kim22)]
- Criterion for detecting exceedingly bright regions  
  > "We adopt the same criteria for detecting exceedingly bright regions as in (cite: kim22)" (2.3 Post-processing images) [from (cite: kim22)]
- Default values of the HEISENBERG parameters for error propagation and model fitting  
  > "For other parameters not listed here, related to error propagation and model fitting, we use the default values from (cite: kruijssen18)." (Table 2) [from (cite: kruijssen18)]
- Choice of n_lambda as lowest integer with <10% flux loss from compact emission  
  > "We adopt the lowest possible integer value of $n_{\lambda}$ for which the flux loss from the compact emission remains $<$10%, as recommended by (cite: hygate19)." (3 Method) [from (cite: hygate19)]
- Non-overlapping aperture Monte Carlo realizations (1000)  
  > "repeat this process 1000 times, following the description in (cite: kruijssen18)" (3 Method) [from (cite: kruijssen18)]
- JWST survey design and data reduction  
  > "For comprehensive explanations of the survey and the data reduction process, we refer readers to (cite: lee23) and (cite: williams24)." (2.1 Mid-IR bands) [from (cite: lee23); (cite: williams24)]
- MUSE survey and data reduction  
  > "Detailed explanations of the PHANGS-MUSE survey and data reduction can be found in (cite: emsellem22)." (2.2 MUSE H$\alpha$) [from (cite: emsellem22)]
- ALMA CO data and its processing (PHANGS-ALMA)  
  > "the CO data is from PHANGS-ALMA (cite: leroy21_survey)" (5.2 Galaxies with decorrelation between CO and mid-IR emission) [from (cite: leroy21_survey)]

### Not stated but needed to reproduce (our reading)

- CO transition, ALMA array configuration, beam and rms of the PHANGS-ALMA maps used (only the PHANGS-ALMA survey is cited)
- Which CO cubes/moment maps the CO time-scales of Kim et al. 2022 used, since the paper takes t_g^CO, t_fb^CO and t_ref from that work
- The exact bright-region and galactic-center masks inherited from Kim et al. 2022
- HEISENBERG version or git commit and the default error-propagation/fitting settings (sampler, priors, likelihood) referenced only as 'defaults from Kruijssen et al. 2018'
- Pixel scale and exact PSF-matched resolution maps for each galaxy beyond l_ap,min in Table 2
- Which MUSE data release and exact H-alpha map files were used
- How uncertainties on correlations (Spearman) were estimated

## Analysis recipe

1. **PSF-match and regrid JWST and MUSE maps**: Convolve finer-resolution JWST maps to the coarser H-alpha resolution (l_ap,min) with a Gaussian-target kernel and regrid to the H-alpha pixel grid  
  > "We then regrid these convolved maps to align with the pixel grid of the H$\alpha$ maps." (2.3 Post-processing images)
   - parameter: Matched resolution l_ap,min per galaxy listed in Table 2 (e.g. 29-145 pc)  
  > "where Table [2](#tab:input) lists the matched resolution ($l_{\rm ap, min}$)" (2.3 Post-processing images)
   - fitting: _not stated_
   - validation: _not stated_
2. **Mask bright peaks and galactic centers; restrict to overlap area**: Sort peaks by luminosity, mask all peaks above a gap where a peak is at least twice as luminous as the next, in any of the three mid-IR bands; restrict to JWST-MUSE overlap polygon  
  > "Whenever such a gap is identified, we mask all peaks that surpass the brightness of the next brightest peak." (2.3 Post-processing images); "we limit our analysis to areas where both JWST and MUSE observations overlap" (2.3 Post-processing images)
   - fitting: _not stated_
   - validation: Masking bright regions has negligible impact; results consistent within 1 sigma (Table 4)  
  > "Appendix [10](#app:masking) shows that masking bright regions has a negligible impact on the derived properties, with results consistent within the 1$\sigma$ uncertainty." (2.3 Post-processing images)
3. **Identify emission peaks in mid-IR and H-alpha maps**: CLUMPFIND contouring at steps delta log F over range Delta log F from the maximum flux; peaks below N_pix,min pixels discarded  
  > "using CLUMPFIND (cite: williams94). This algorithm detects peaks by contouring the data at multiple flux levels." (3 Method); "Peaks containing fewer than $N_{\rm pix, min}$ pixels are disregarded." (3 Method)
   - software: CLUMPFIND
   - parameter: Per-galaxy delta log F, Delta log F, N_pix,min given in Table 2  
  > "Main input parameters adopted in our analysis." (Table 2)
   - fitting: _not stated_
   - validation: Visually verified that all obvious emission peaks are identified  
  > "we have visually verified that all the obvious emission peaks are identified." (3 Method)
4. **Measure aperture-averaged mid-IR-to-H-alpha flux ratios vs aperture size**: Center apertures on each peak type, sum enclosed mid-IR and H-alpha flux, take the ratio; use 1000 Monte Carlo realizations of non-overlapping aperture samples  
  > "we sum the total enclosed mid-IR and H$\alpha$ flux across all apertures and compute their ratio" (3 Method); "we generate Monte Carlo realizations of non-overlapping aperture samples for each peak type and aperture size" (3 Method)
   - software: HEISENBERG
   - parameter: Aperture sizes from l_ap,min ~100 pc to l_ap,max ~3 kpc (per-galaxy values in Table 2); 1000 realizations  
  > "ranging from $\rm l_{ap,min}\approx 100\,pc$ to $\rm l_{ap,max}\approx 3\,kpc$" (3 Method); "repeat this process 1000 times, following the description in (cite: kruijssen18)" (3 Method)
   - fitting: _not stated_
   - validation: _not stated_
5. **Filter diffuse emission**: Gaussian high-pass filter in Fourier space removing emission on scales larger than n_lambda times the region separation length lambda; iterate until lambda changes by <5% for three consecutive runs  
  > "using a Gaussian high-pass filter in Fourier space, where $n_{\lambda}$ is the scaling factor" (3 Method); "defined as when the change in $\lambda$ is less than 5% for three consecutive runs" (3 Method)
   - software: HEISENBERG
   - parameter: n_lambda is the lowest integer with <10% flux loss from compact emission; n_lambda*lambda ~1.5 kpc  
  > "We adopt the lowest possible integer value of $n_{\lambda}$ for which the flux loss from the compact emission remains $<$10%, as recommended by (cite: hygate19)." (3 Method); "$n_{\lambda}\lambda\approx 1.5$ kpc" (4.5 Diffuse emission fractions)
   - assumption: Large-scale diffuse emission has a different physical origin from the compact star-forming structures  
  > "the diffuse components in mid-IR and H$\alpha$ maps often have a different physical origin from the compact star-forming structures we aim to trace" (3 Method)
   - fitting: _not stated_
   - validation: Diffuse fractions compared with Spitzer 8 um in M33, Belfiore et al. 2022 and Pathak et al. 2024  
  > "which agrees well with the diffuse emission fraction measured in *Spitzer* 8 $\mu$m observations of M33 obtained by separating discrete sources (cite: verley09)" (3 Method)
6. **Fit the analytical model to get t_g, t_fb and lambda**: Fit an analytic function of the relative flux ratio vs aperture size depending on mid-IR-bright, H-alpha-bright and overlap durations and region separation lambda; absolute scale set by t_ref = t_s from Kim et al. 2022  
  > "To these observed flux ratios, we fit an analytical function which depends on the relative durations of successive phases in the timeline of cloud evolution" (3 Method); "The analytical function is then described by three independent quantities" (3 Method)
   - software: HEISENBERG
   - parameter: t_ref per galaxy from Kim et al. 2022 (Table 2)  
  > "by using the duration of the H$\alpha$-bright phase ($t_{\rm s}$) as a reference time-scale ($t_{\rm ref}$) which is measured in (cite: kim22)" (3 Method)
   - assumption: Emission enclosed in an aperture originates solely from regions inside it  
  > "Our analytical model assumes that the emission enclosed in an aperture originates solely from regions inside it." (3 Method)
   - assumption: Mid-IR emission traces the gas column density  
  > "Assuming that mid-IR emission (7.7-11.3 $\mu$m) traces the gas column density" (6 Conclusions)
   - fitting: Sampler, priors and likelihood not given in this paper; defaults of HEISENBERG from Kruijssen et al. 2018  
  > "For other parameters not listed here, related to error propagation and model fitting, we use the default values from (cite: kruijssen18)." (Table 2)
   - validation: Checked the eleven accuracy requirements of Kruijssen et al. 2018; all satisfied except resolution requirement (lambda > 1.5 l_ap,min) in NGC 1365, 1512, 4321 (all bands) and NGC 1300, 2835 (7.7 um), so t_fb and lambda are upper limits there  
  > "(cite: kruijssen18) lists a set of requirements that our measurements have to satisfy in order to be considered accurate within 30% error." (Accuracy of our measurements); "we find that almost all of the the requirements are satisfied except for the condition (2)" (Accuracy of our measurements)
7. **Derive CO-dark mid-IR phase and feedback time-scale difference**: t_CO-dark = t_g^X - t_fb^X - (t_g^CO - t_fb^CO) and Delta t_fb,CO = t_fb^X - t_fb^CO, combining mid-IR results with the Kim et al. 2022 CO results  
  > "$t_{\rm CO-dark}^{X}=t_{\rm g}^{X}-t_{\rm fb}^{X}-(t_{\rm g}^{\rm CO}-t_{\rm fb}^{\rm CO})$" (4.2 Mid-IR emitting time-scale); "We measure the difference in the feedback time-scales between mid-IR bands and CO as $\Delta t_{\rm fb, CO}^{X}=t_{\rm fb}^{X}- t_{\rm fb}^{\rm CO}$" (4.3 Mid-IR and H$\alpha$ overlapping time-scale)
   - assumption: Detection of emission peaks is symmetric in terms of mass traced across tracers (for the CO-dark mass fraction)  
  > "Assuming that our detection of emission peaks is symmetric in terms of mass traced across different tracers" (4.3 Mid-IR and H$\alpha$ overlapping time-scale)
   - fitting: _not stated_
   - validation: _not stated_
8. **Correlate time-scales with galaxy and GMC properties**: Spearman rank correlations between measurements and galaxy/GMC properties; significance with Holm-Bonferroni effective p-value; residuals after linear regression against CO completeness or resolution to test biases  
  > "rank correlation coefficients computed between our measurements and the galaxy environmental properties described above" (5.1 Correlations between global galaxy properties and cloud evolutionary time-scales); "defined using the Holm-Bonferroni method" (5.1.2 Identification of statistically significant correlations); "We then used the residuals to represent the time-scale ratio after removing the dependence on completeness." (5.1.1 Theoretical expectations)
   - software: SciPy
   - parameter: p_ref = 0.05; N_corr ~ 15  
  > "where $p_{\rm ref}$ is the desired significance level (0.05)" (5.1.2 Identification of statistically significant correlations); "resulting in $N_{\rm corr} \approx 15$" (5.1.2 Identification of statistically significant correlations)
   - fitting: _not stated_
   - validation: With N_corr = 28 (all variables independent) correlations with t_g and f_diffuse would no longer be significant  
  > "if we assume all the variables are independent with $N_{\rm corr}=28$, the correlations with $t_{\rm g}^{\rm mid-IR}$ and $f_{\rm diffuse}^{\rm mid-IR}$ are no longer defined as statistically significant" (5.1.2 Identification of statistically significant correlations)

## Software

- **HEISENBERG** : Statistical method translating gas-to-SFR tracer flux ratio deviations into time-scales (the code formalizing the method)  
  > "we briefly describe the method (formalized in the HEISENBERG code" (3 Method)
- **CLUMPFIND** : Identification of emission peaks in mid-IR and H-alpha maps  
  > "we first identify emission peaks in both mid-IR and H$\alpha$ maps (at the highest PSF-matched resolution; $l_{\rm ap, min}$) using CLUMPFIND (cite: williams94)" (3 Method)
- **STARBURST99** : Initial stellar mass for the H-alpha sensitivity check  
  > "We obtain the initial mass using the STARBURST99 model with an assumption that star formation was instantaneous 5 Myr ago." (Accuracy of our measurements)
- **CPROPS** : Algorithm behind the PHANGS-ALMA GMC catalog from which GMC property averages were taken  
  > "using the GMC catalog generated using the CPROPS algorithm (cite: rosolowsky21) for PHANGS-ALMA (cite: leroy21_survey) galaxies" (5.1 Correlations between global galaxy properties and cloud evolutionary time-scales)
- **Astropy** : Named in the Software list; specific use not stated  
  > "Astropy (cite: astropy:2013; astropy:2018; astropy:2022), Clumpfind (cite: williams94), Heisenberg (cite: kruijssen18), Matplotlib (cite: Hunter07), SciPy (cite: scipy), seaborn (cite: seaborn), pandas (cite: pandas)" (Software)
- **Matplotlib** : Named in the Software list; specific use not stated  
  > "Astropy (cite: astropy:2013; astropy:2018; astropy:2022), Clumpfind (cite: williams94), Heisenberg (cite: kruijssen18), Matplotlib (cite: Hunter07), SciPy (cite: scipy), seaborn (cite: seaborn), pandas (cite: pandas)" (Software)
- **SciPy** : Named in the Software list; specific use not stated  
  > "Astropy (cite: astropy:2013; astropy:2018; astropy:2022), Clumpfind (cite: williams94), Heisenberg (cite: kruijssen18), Matplotlib (cite: Hunter07), SciPy (cite: scipy), seaborn (cite: seaborn), pandas (cite: pandas)" (Software)
- **seaborn** : Named in the Software list; specific use not stated  
  > "Astropy (cite: astropy:2013; astropy:2018; astropy:2022), Clumpfind (cite: williams94), Heisenberg (cite: kruijssen18), Matplotlib (cite: Hunter07), SciPy (cite: scipy), seaborn (cite: seaborn), pandas (cite: pandas)" (Software)
- **pandas** : Named in the Software list; specific use not stated  
  > "Astropy (cite: astropy:2013; astropy:2018; astropy:2022), Clumpfind (cite: williams94), Heisenberg (cite: kruijssen18), Matplotlib (cite: Hunter07), SciPy (cite: scipy), seaborn (cite: seaborn), pandas (cite: pandas)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mid-IR emitting time-scale t_g range (disk, excluding centers) | 10-30 Myr | not stated | Myr | 6 | We find that the mid-IR emitting time-scale of gas clouds in galaxy disks (excluding centers) ranges from 10 to 30 Myr. |
| Mean t_g at 7.7, 10, 11.3 um (average and 16-84% range) | 18, 18, 23 | 5, 4, 5 | Myr | 6 | The average and $16{-}84$% range for each mid-IR band are $18\pm5$ Myr, $18\pm4$ Myr, and $23\pm5$ Myr, for 7.7 $\mu$m, 10 $\mu$m, and 11.3 $\mu$m, respectively. |
| Mean feedback (overlap) time-scale t_fb at 7.7, 10, 11.3 um | 5.7, 5.8, 6.2 | 1.0, 1.2, 1.1 | Myr | 6 | with an average and 16-84% range of $5.7\pm1.0$ Myr, $5.8\pm1.2$ Myr, and $6.2\pm1.1$ Myr, for 7.7, 10, and 11.3 $\mu$m |
| Fraction of H-alpha emitting phase with associated mid-IR, t_fb/t_s | 70-80% | not stated | percent | 6 | with an average ratio $t_{\rm fb}^{\rm mid-IR}/t_{\rm s}$ of 70-80% |
| Difference in feedback time-scale, mid-IR minus CO (range across galaxies, 7.7 / 10 / 11.3 um) | 1.3-2.8 / 1.3-4.0 / 1.9-4.1 | not stated | Myr | 7 | We find the difference to range $1.3{-}2.8$ Myr, $1.3{-}4.0$ Myr, and $1.9{-}4.1$ Myr |
| Mean ratio t_g(mid-IR)/t_g(CO) at 7.7, 10, 11.3 um | 1.1, 1.1, 1.3 | 0.4, 0.3, 0.5 | dimensionless | 7 | being $1.1\pm0.4$, $1.1\pm0.3$, and $1.3\pm0.5$, for 7.7 $\mu$m, 10 $\mu$m, and 11.3 $\mu$m, respectively |
| Mean CO-dark mid-IR emitting phase t_CO-dark at 7.7, 10, 11.3 um | -3, -2, 3 | 6, 5, 5 | Myr | 7 | are $-3\pm6$ Myr, $-2\pm5$ Myr, and $3\pm5$ Myr, respectively, for 7.7, 10, and 11.3 $\mu$m. |
| Mean region separation length lambda at 7.7, 10, 11.3 um | 112, 128, 117 | 33, 33, 30 | pc | 6 | with their average and 16-84% range of $112\pm33$, $128\pm33$, and $117\pm30$ pc |
| Mid-IR diffuse emission fraction (mean over bands) | 60 | 10 | percent | 5 | are very similar among different wavelengths ($60\pm10\%$) |
| H-alpha diffuse emission fraction | 40-60% range, average 50-60% | not stated | percent | 5 | we find it to range from $40\%$ to $60$%, with an average of $50-60\%$ |
| Fraction of compact mid-IR emission in and near HII regions dark in CO | 30-70%, average ~45% | not stated | percent | 7 | $30{-}70\%$ of the compact mid-IR emission is dark in CO, with an average of $\sim 45\%$ |
| Ramp-up period t_g - t_fb of mid-IR emitting clouds | 5-30 Myr | not stated | Myr | 7 | The compact mid-IR emitting gas clouds experience a ramp-up period of $5-30$ Myr |
| Spearman rho of t_g(7.7um)/t_g(CO) vs metallicity | -0.7 | not stated | dimensionless | 8 | shows the tightest relation with metallicity with a correlation coefficient ($\rho$) of $-0.7$ |

## Qualitative findings

- Mid-IR emission overlaps H-alpha because HII-region radiation illuminates nearby PAHs and dust; overlap time-scale is the feedback time-scale at ~100 pc scales  
  > "Our measurements also show that mid-IR emitting phase ends before H$\alpha$" (4.3 Mid-IR and H$\alpha$ overlapping time-scale)
- Most galaxies show no mid-IR emitting phase dark in CO, i.e. compact mid-IR clouds quickly become CO-stable  
  > "This implies that once gas clouds assemble, being associated with compact mid-IR peaks, they immediately provide sufficient shielding for CO to become stable." (4.2 Mid-IR emitting time-scale)
- t_g^10um correlates strongly with the H-alpha flux density contrast epsilon_Halpha  
  > "we found a strong positive correlation between $t_{\rm g}^{\rm 10\mu m}$ and $\epsilon_{\rm H\alpha}$" (5.1.3 Interpreting the strong correlations)

## Claim tuples

- H: How long do gas clouds emit in mid-IR (PAH/dust) in galaxy disks | E: Apply the Kruijssen et al. 2018 time-scale method to F770W/F1000W/F1130W vs MUSE H-alpha for 17 galaxies | R: t_g = 10-30 Myr; mean 18+-5, 18+-4, 23+-5 Myr | F: Mid-IR emitting time-scale of gas clouds is 10-30 Myr | **supported**
- H: Does mid-IR emission persist during the stellar feedback (H-alpha) phase | E: Measure the mid-IR/H-alpha overlap time-scale t_fb | R: t_fb = 3-7 Myr, covering 70-80% of the H-alpha emitting phase | F: Mid-IR emission persists after star formation is detected in H-alpha because HII regions illuminate surrounding PAHs and dust | **supported**
- H: Does the mid-IR emitting time-scale match the CO molecular cloud lifetime, i.e. is there a CO-dark compact cloud phase | E: Compare t_g(mid-IR) with t_g(CO) from Kim et al. 2022 and compute t_CO-dark | R: Ratio 1.1+-0.4, 1.1+-0.3, 1.3+-0.5; t_CO-dark consistent with zero in most galaxies | F: Clouds with compact mid-IR emission quickly shield CO, in these molecular-gas-rich, near-solar-metallicity regions | **supported**
- H: Does the shape of the ISM around HII regions influence the mid-IR time-scale | E: Spearman correlations of time-scales with galaxy properties incl. epsilon_Halpha, with Holm-Bonferroni significance | R: Strong correlation of t_g^10um with epsilon_Halpha; other bands show similar but non-significant trends | F: Mid-IR time-scale is longer where HII regions are well defined with less structured background | **partially**
- H: Why do some galaxies have negative t_CO-dark | E: Map CO to F770W-predicted flux ratio (Chown et al. 2024 correlation) in NGC 1566 and NGC 4321 | R: Long ridges with unusually high CO-to-PAH ratios, not coincident with HII regions | F: CO-PAH decorrelation (possibly PAH coagulation or CO emissivity changes) yields negative t_CO-dark; cause unconfirmed | **partially**

## Reasoning

- Why this data: Mid-IR bands correlate best with cold gas and give the highest resolution and sensitivity view of neutral gas, including gas missed in CO  
  > "These mid-IR bands are known to best correlate with the cold gas" (2.1 Mid-IR bands); "currently provide the highest resolution and highest sensitivity view of the neutral gas distribution of the PHANGS-JWST galaxies" (2.1 Mid-IR bands)
- Why this method: Extends the established statistical method for GMC lifetimes to mid-IR tracers, for consistency with Kim et al. 2022  
  > "We characterize evolutionary time-scales from mid-IR emitting gas phase to HII regions by applying a robust statistical method (cite: kruijssen14; kruijssen18) to mid-IR and H$\alpha$ observations." (3 Method)
- Alternative: 21 um (F2100W) excluded because it traces dust in very high radiation fields, more associated with star-forming regions than cold gas  
  > "We do not include the dust continuum at 21 $\mu$m (F2100W) in our analysis" (2.1 Mid-IR bands)
- Alternative: Balmer-decrement extinction-corrected H-alpha tested for NGC 0628; time-scale changes within 1 sigma, not adopted for consistency with Kim et al. 2022  
  > "we do not use H$\alpha$ maps that have been corrected for the dust extinction using the Balmer decrement (cite: belfiore22)" (2.2 MUSE H$\alpha$)
- How they decided it was enough: _not stated_
- Limitation (authors): Mid-IR emission is influenced by column density, heating, and dust/PAH abundance, so the time-scale's physical interpretation is not trivial  
  > "Therefore, the physical interpretation of the mid-IR emitting time-scale is not trivial." (4.2 Mid-IR emitting time-scale)
- Limitation (authors): The method is flux weighted and biased toward bright mid-IR peaks near HII regions  
  > "our method is flux weighted, which naturally biases our measurements toward bright mid-IR emission peaks" (4.2 Mid-IR emitting time-scale)
- Limitation (authors): Trends of the mid-IR to CO time-scale ratio could be driven by differing CO sensitivity (flux completeness)  
  > "This raises the possibility that the observed trends may be biased by the shallow CO observations" (5.1.1 Theoretical expectations)
- Limitation (authors): lambda depends on resolution and is overestimated in poorly resolved galaxies  
  > "imply that $\lambda$ are overestimated in galaxies with a poor resolution" (5.1.2 Identification of statistically significant correlations)
- Caveat (inferred, ours): ALMA enters only through PHANGS-ALMA CO products and Kim et al. 2022 time-scales; the CO side is not re-derived here
- Caveat (inferred, ours): Small sample (17) and many correlation tests; significance depends on N_corr choice (15 vs 28)
- Caveat (inferred, ours): CO and JWST have different resolution and sensitivity, confounding the mid-IR vs CO comparison
- Caveat (inferred, ours): Time-scale uncertainties come from HEISENBERG defaults not restated in the paper

## Reproducibility

- Data public (paper): JWST data via MAST/STScI PHANGS HLSP page; ALMA data are public PHANGS-ALMA products (project codes listed)  
  > "Data can be accessed via <https://archive.stsci.edu/hlsp/phangs> or (cite: doi)" (footnote 4); "The observations are obtained from the Mikulski Archive for Space Telescope at the Space Telescope Science Institute" (2.1 Mid-IR bands)
- Products in archive: _not stated_
- Code: HEISENBERG code on GitHub (mustang-project/Heisenberg)  
  > "https://github.com/mustang-project/Heisenberg" (footnote 5)
- Missing: Kim et al. 2022 CO time-scales, masks and t_ref values (only t_ref given in Table 2)
- Missing: HEISENBERG version and non-listed default parameters
- Missing: Exact PHANGS-ALMA CO map products and MUSE map versions
- Missing: Fitting sampler/priors/likelihood
- Data volume (inferred): Roughly 10-50 GB: JWST MIRI F770W/F1000W/F1130W mosaics and MUSE H-alpha maps for 17 galaxies; no raw ALMA visibilities are reprocessed
- Score (inferred): 3/5, Public JWST/MUSE/PHANGS products, public HEISENBERG code, per-galaxy parameters in Table 2 and full numeric Table 3, but inherited CO results, masks, and fit defaults from Kim et al. 2022 and Kruijssen et al. 2018 are needed.
- Rediscovery candidate: no, ALMA data are peripheral (inherited CO time-scales and masks from another paper); a standalone redo needs Kim et al. 2022 products not given here.

## Links

- Method: (cite: kruijssen14); (cite: kruijssen18) (Statistical method and HEISENBERG code, including validation and accuracy requirements)
- Method: (cite: kim22) (CO-based GMC time-scales, t_ref, masks and bright-region criteria inherited here)
- Method: (cite: hygate19) (Recommendation for diffuse emission filter scale n_lambda)
- Method: (cite: lee23); (cite: williams24) (PHANGS-JWST survey and data reduction)
- Method: (cite: emsellem22) (PHANGS-MUSE survey and data reduction)
- Method: (cite: leroy21_survey) (PHANGS-ALMA CO survey)
- Companion: (cite: kim22) (Same method applied with CO for 54 galaxies; source of CO timeline)
- Companion: (cite: chown24) (CO vs PAH relation across PHANGS-JWST)
- Companion: (cite: leroy23) (Mid-IR, CO and H-alpha correlations in first four PHANGS-JWST galaxies)
- Companion: (cite: pathak24) (Fraction of mid-IR emission from HII regions vs diffuse)
- Related: PHANGS-ALMA
- Related: PHANGS-JWST Cycle 1 (GO 2107)
- Related: PHANGS-MUSE

## Checks

```json
{
 "quotes": 129,
 "quotes_ok": 129,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 7,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 118,
  "stated": 74,
  "rate": 0.627
 },
 "evidence_ok": true
}
```
