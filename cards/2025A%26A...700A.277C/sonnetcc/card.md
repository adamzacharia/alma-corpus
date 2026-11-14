# Dust emission from the bulk of galaxies in the Epoch of Reionisation

`2025A&A...700A.277C` | Astronomy and Astrophysics 2025 | first author: Ciesla, L. | arXiv: 2412.02557 | DOI: 10.1051/0004-6361/202453278

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Constrain the dust emission and attenuation properties of the bulk of JWST-selected (JADES) galaxies at 6<z<12 by stacking archival ALMA band 6 and 7 data and using the stacks as FIR constraints in UV-to-FIR SED modelling  
  > "In this work, we aim at constraining the dust properties of galaxies at $6<z<12$ by making the most of the A$^3$COSMOS database in the JADES/GOODS-South field." (abstract)
- Target **JADES galaxies at 6<z<12 in the Hubble Ultra Deep Field / GOODS-South (4464 of the 5974 galaxies at 6<z<7 covered by ALMA)**: coordinates _not stated_; z/distance 6<z<12 (photometric redshifts, spectroscopic when available)  
  > "This criterion results in a subsample of 8810 galaxies with redshifts between 6 and 12, 6000 of them between 6 and 7." (2.1 Sample selection); "Photometric redshifts available in the JADES catalogue are computed with the code" (2.1 Sample selection); "Out of the 5974 galaxies in our $6<z<7$ sample, 4464 are covered by one or multiple ALMA pointings" (3 ALMA stacking of JADES galaxies); distance from JADES catalogue photometric redshifts (EAZY); spectroscopic redshifts for 0.6% of the 6<z<7 sample  
  > "This criterion results in a subsample of 8810 galaxies with redshifts between 6 and 12, 6000 of them between 6 and 7." (2.1 Sample selection); "Photometric redshifts available in the JADES catalogue are computed with the code" (2.1 Sample selection); "Out of the 5974 galaxies in our $6<z<7$ sample, 4464 are covered by one or multiple ALMA pointings" (3 ALMA stacking of JADES galaxies)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 and Band 7  
  > "choosing ALMA images from bands 6 ($\sim$243 GHz) and 7 ($\sim$324 GHz)" (3 ALMA stacking of JADES galaxies)
- frequencies and spectral setup: ~243 GHz (Band 6) and ~324 GHz (Band 7) continuum images, fluxes renormalised to a common 1.1 mm observed wavelength  
  > "choosing ALMA images from bands 6 ($\sim$243 GHz) and 7 ($\sim$324 GHz)" (3 ALMA stacking of JADES galaxies); "to a common 1.1 mm observed wavelength using the star-forming galaxy SED template of (cite: Bethermin12)." (3 ALMA stacking of JADES galaxies)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: heterogeneous across the many archival pointings  
  > "it was impractical to stack them in the $uv$-domain in order to deal with the heterogeneity in angular resolution" (3 ALMA stacking of JADES galaxies)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data from the A3GOODSS database, part of A3COSMOS  
  > "We used the A$^3$GOODSS ALMA archival database, part of the A$^3$COSMOS database (cite: Liu19; Adscheid24), to perform a stacking analysis on our galaxy sample" (3 ALMA stacking of JADES galaxies)
- Other facility **JWST (NIRCam, JADES and JEMS surveys)**: Photometry and photometric redshifts used to select the sample and fit SEDs (nine broad and five medium NIRCam bands)  
  > "This catalogue combines nine broad and five medium JWST/NIRCam bands from the JADES and JEMS (cite: Williams23) surveys, respectively, and existing HST imaging, for a total of 23 photometric bands." (2.1 Sample selection)
- Other facility **HST**: Existing HST imaging included in the 23-band photometric catalogue  
  > "and existing HST imaging, for a total of 23 photometric bands." (2.1 Sample selection)
- Other facility **Dawn JWST Archive**: Check for spectroscopic data: 37 NIRSpec spectra found, 9 galaxies with z_spec<5.5 excluded  
  > "We also checked for spectroscopic data through the Dawn JWST Archive" (2.1 Sample selection); "find 37 NIRSpec spectra." (2.1 Sample selection)
- External data: JADES photometric catalogue (KRON apertures), redshifts and photometry  
  > "In this work we use the photometry catalogue made from KRON apertures." (2.1 Sample selection) [from Rieke23; Eisenstein23b; Robertson24 (cite: Rieke23; Eisenstein23b; Robertson24)]
- External data: A3GOODSS/A3COSMOS ALMA archival images used for the stacking  
  > "We used the A$^3$GOODSS ALMA archival database, part of the A$^3$COSMOS database (cite: Liu19; Adscheid24), to perform a stacking analysis on our galaxy sample" (3 ALMA stacking of JADES galaxies) [from (cite: Liu19; Adscheid24)]
- External data: Star-forming galaxy SED template used to renormalise ALMA fluxes to 1.1 mm  
  > "to a common 1.1 mm observed wavelength using the star-forming galaxy SED template of (cite: Bethermin12)." (3 ALMA stacking of JADES galaxies) [from (cite: Bethermin12)]
- External data: Dust emission library with PAH fraction and dust temperature as free parameters  
  > "To model the IR emission, we use the dust library of (cite: Schreiber18) that has two free parameters." (2.2 SED modelling with CIGALE) [from (cite: Schreiber18)]
- External data: Dust temperature of 47 K, set following REBELS results  
  > "following the results of (cite: Sommovigo22) from REBELS galaxies, we set it to 47 K" (2.2 SED modelling with CIGALE) [from (cite: Sommovigo22)]
- External data: Stacked REBELS, ALPINE and other literature measurements used for comparison and in the beta-MUV, LIR-MUV fits  
  > "Combining our measurement to the stack estimates from REBELS (cite: Bowler24), (cite: Austin24), and (cite: RobertsBorsani24), we obtain the following relation from a linear regression fit:" (4 Dust attenuation properties); "as well as those from the ALPINE sample at $z\sim5.5$ from (cite: Khusanova21)." (4 Dust attenuation properties) [from Bowler24; Austin24; RobertsBorsani24; Khusanova21]
- External data: CMB-effect correction to LIR as a function of redshift for Tdust=40 K  
  > "(cite: DaCunha13) demonstrated that for $T_{\rm dust}=40$ K, the $L_{\mathrm{IR}}$ is under-estimated by -0.018, -0.019, -0.045, and -0.070 dex at $z=$6, 7, 9, and 10, respectively." (6.1 Evolution of beta) [from (cite: DaCunha13)]
- External data: AV versus inverse sSFR relation from NIRSpec spectra (gamma=0.67+-0.2 cm2 g-1; slope 0.58+-0.12) used for comparison  
  > "They obtained $\gamma=0.67\pm0.2$ cm$^2$g$^{-1}$, 30 times lower than the value expected if the entire SN dust yield were preserved in the ISM" (6.2 Dust formation in early galaxies) [from (cite: Langeroodi24)]
- Simulation/model as data: Mock analysis: CIGALE best-fit SED convolved with the JADES+ALMA filters, noise added, refit with CIGALE, to test recovery of parameters  
  > "We took the best fit SED, convolved it in the JADES+ALMA set of filters, added noise to the photometry. We ran again `CIGALE` on the mock photometry." (6.2 Dust formation in early galaxies)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Archival A3GOODSS/A3COSMOS database images used; no calibration or pipeline details given  
  > "We used the A$^3$GOODSS ALMA archival database, part of the A$^3$COSMOS database (cite: Liu19; Adscheid24), to perform a stacking analysis on our galaxy sample" (3 ALMA stacking of JADES galaxies)
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
- primary beam correction: primary beam-corrected flux densities measured from the central pixel at each source position; sources within primary beam attenuation >0.5  
  > "only primary beam-corrected flux densities measured from the central pixel at each source position." (3 ALMA stacking of JADES galaxies); "are covered by one or multiple ALMA pointings (i.e., within an area of a primary beam attenuation $>0.5$)" (3 ALMA stacking of JADES galaxies)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CIGALE fitting setup (non-parametric SFH library, parameters)  
  > "The fitting set up of `CIGALE` is the same than the one tested and used in (cite: Ciesla24) which adopts a non-parametric star formation history (SFH) specifically tailored for early galaxies." (2.2 SED modelling with CIGALE) [from (cite: Ciesla24)]
- Sample selection criterion: S/N>3 in at least 3 JWST filters  
  > "As in (cite: Ciesla24), we impose each galaxy to be detected with a signal-to-noise (S/N) higher 3 in at least 3 JWST filters." (2.1 Sample selection) [from (cite: Ciesla24)]
- JADES data reduction, photometry procedures and redshift estimates  
  > "We refer to (cite: Rieke23), (cite: Eisenstein23b), and (cite: Robertson24) for more details on the data reduction process, photometry procedures, and redshift estimates." (2.1 Sample selection) [from (cite: Rieke23; Eisenstein23b; Robertson24)]
- Dust temperature fixed at 47 K, following REBELS results  
  > "following the results of (cite: Sommovigo22) from REBELS galaxies, we set it to 47 K" (2.2 SED modelling with CIGALE) [from (cite: Sommovigo22)]
- PAH fraction fixed to 3%, the Schreiber et al. estimate at z~3  
  > "Therefore we choose to fix this input parameter to 3% which corresponds to the estimate of (cite: Schreiber18) at $z\sim3$" (2.2 SED modelling with CIGALE) [from (cite: Schreiber18)]
- Stacking in image/flux domain rather than uv domain to handle heterogeneous angular resolution  
  > "it was impractical to stack them in the $uv$-domain in order to deal with the heterogeneity in angular resolution" (3 ALMA stacking of JADES galaxies) [from (cite: Wang22; Wang24; Magnelli24)]
- Mock-analysis test of SED modelling  
  > "First we checked if the flatter slope that we observe is due to the SED modelling by performing a mock analysis (cite: Buat15; Ciesla17; Boquien19)." (6.2 Dust formation in early galaxies) [from (cite: Buat15; Ciesla17; Boquien19)]

### Not stated but needed to reproduce (our reading)

- CIGALE version and full list of modules/parameter grids beyond the summary table (e.g. Schreiber18 module settings, attenuation parameters not in the table)
- Which A3GOODSS/A3COSMOS images, ALMA project codes and per-pointing noise maps were used, and the calibration/imaging used to make them
- How the pixel RMS noise sigma_i was measured and how bin upper limits (3 sigma) were derived from the stack
- Redshift assumed for each galaxy when renormalising the flux to 1.1 mm with the Bethermin12 template, and the template version
- JADES catalogue version/IDs and the exact list of 4464 galaxies and their bin assignments
- Exact beam-size criterion implementation and how multiple pointings of the same source were combined
- Details of the weights used to derive bin physical properties and of the Delta-BIC test
- Treatment of ALMA flux assignment to individual galaxies and the exact 8810 -> 5974 -> 4464 sample bookkeeping

## Analysis recipe

1. **select the JADES sample**: Select galaxies at 6<z<12 from the JADES catalogue with S/N>3 in at least 3 JWST filters; exclude galaxies with z_spec<5.5  
  > "This criterion results in a subsample of 8810 galaxies with redshifts between 6 and 12, 6000 of them between 6 and 7." (2.1 Sample selection); "9 of them are galaxies with $z_{spec}<5.5$, we exclude them from our analysis." (2.1 Sample selection)
   - software: EAZY
   - parameter: S/N>3 in at least 3 JWST filters  
  > "we impose each galaxy to be detected with a signal-to-noise (S/N) higher 3 in at least 3 JWST filters." (2.1 Sample selection)
   - assumption: Full sample used without photo-z PDF quality cuts  
  > "However, in the following, we consider the full galaxy sample." (2.1 Sample selection)
   - fitting: _not stated_
   - validation: Repeating the analysis with Cole23 photo-z quality criteria gives no strong impact  
  > "we find no strong impact on our results, a conclusion also reached by (cite: Cole23)." (2.1 Sample selection)
2. **UV-to-NIR SED fit to derive MUV, stellar mass, SFR, beta**: CIGALE run on the HST+JWST photometry with a non-parametric SFH library, BC03 stellar populations, Calzetti00 attenuation and the Schreiber18 dust emission model; select galaxies with reduced chi2 no larger than 4  
  > "on the HST+JWST set of data, probing the UV to NIR restframe wavelength range." (2.2 SED modelling with CIGALE); "We select galaxies with a reduced $\chi^2$ no larger than 4, removing 26 galaxies" (2.2 SED modelling with CIGALE)
   - software: CIGALE
   - parameter: Tdust fixed to 47 K; PAH fraction fixed to 3%  
  > "following the results of (cite: Sommovigo22) from REBELS galaxies, we set it to 47 K" (2.2 SED modelling with CIGALE); "Therefore we choose to fix this input parameter to 3% which corresponds to the estimate of (cite: Schreiber18) at $z\sim3$" (2.2 SED modelling with CIGALE)
   - assumption: Salpeter IMF, WMAP7 cosmology, Calzetti00 dust attenuation law, energy balance between UV-optical absorption and IR emission  
  > "Throughout the paper, we use a (cite: Salpeter55) initial mass function and WMAP7 cosmology (cite: Komatsu11)." (1 Introduction); "assumes energy balance: the energy absorbed in the UV-optical is re-emitted in the IR." (2.2 SED modelling with CIGALE)
   - fitting: Likelihoods computed from chi2; galaxy properties are likelihood-weighted means with likelihood-weighted standard deviations as uncertainties; upper limits (3 sigma) included in the fit  
  > "To estimate the physical properties, the models are fitted to the observations and the likelihoods are computed from the $\chi^2$." (2.2 SED modelling with CIGALE); "In this work, we take 3$\sigma$ observational uncertainties as the upper limits." (2.2 SED modelling with CIGALE)
   - validation: Relies on the Ciesla24 demonstration that stellar mass and SFR are well constrained with the same filter set  
  > "As we are using the same combination of filters, we rely on their results." (2.2 SED modelling with CIGALE)
3. **stack ALMA flux densities in bins of MUV and stellar mass**: Measure primary beam-corrected flux densities from the central pixel at each source position in images with beams >=0.2 arcsec (sources treated as unresolved), renormalise to 1.1 mm with an SED template and take the noise-weighted mean  
  > "only primary beam-corrected flux densities measured from the central pixel at each source position." (3 ALMA stacking of JADES galaxies); "The final stacked flux density is the noise-weighted mean of all individual flux densities" (3 ALMA stacking of JADES galaxies)
   - parameter: Four MUV bins (-22<MUV<-20, -20<MUV<-19, -19<MUV<-18, -18<MUV<-17) and three stellar-mass bins (8-9, 9-10, 10-11 in log M*)  
  > "We first binned galaxies by UV magnitude in four bins: $-22<M_{\mathrm{UV}}<-20$ mag, $-20<M_{\mathrm{UV}}<-19$ mag, $-19<M_{\mathrm{UV}}<-18$ mag, and $-18<M_{\mathrm{UV}}<-17$ mag." (3 ALMA stacking of JADES galaxies); "by bins of stellar mass ($8<\log M_\star/M_\odot<9$, $9<\log M_\star/M_\odot<10$, and $10<\log M_\star/M_\odot<11$)" (3 ALMA stacking of JADES galaxies)
   - assumption: Galaxies are compact at ~1 mm and spatially unresolved at resolutions >=0.2 arcsec, so S_peak = S_total  
  > "so that $S_{\rm peak}=S_{total}$." (3 ALMA stacking of JADES galaxies)
   - assumption: ALMA-optical astrometric offsets are not an issue  
  > "JWST astrometry are tied to Gaia and should therefore be better." (3 ALMA stacking of JADES galaxies)
   - fitting: _not stated_
   - validation: Redshift, stellar mass, UV luminosity and UV slope distributions of the ALMA-covered sample are indistinguishable (Kolmogorov-Smirnov test) from the parent sample  
  > "redshift, stellar mass, UV luminosity, and UV spectral slope distributions that are indistinguishable (Kolmogorov-Smirnov test) from those of their parent sample of 5974 galaxies." (3 ALMA stacking of JADES galaxies)
4. **refit SEDs with the ALMA stacks as FIR constraints**: Rerun CIGALE assigning each galaxy the stacked 1.1 mm flux density of its MUV (or stellar-mass) bin from the first run  
  > "We attribute to each galaxy the ALMA flux density obtained from stacking according to the derived UV magnitude of the first `CIGALE` run." (5 Impact of the ALMA constraint)
   - software: CIGALE
   - parameter: Tdust = 47 K baseline  
  > "following the results of (cite: Sommovigo22) from REBELS galaxies, we set it to 47 K" (2.2 SED modelling with CIGALE)
   - assumption: One ALMA point (rest-frame 137-157 um) only, so dust mass cannot be constrained  
  > "We cannot constrain the dust mass of the galaxies of our sample since we only have one ALMA data point probing the 137-157 $\mu$m rest-frame emission." (3 ALMA stacking of JADES galaxies)
   - fitting: Same CIGALE likelihood-weighted procedure with upper limits included  
  > "One important aspect to note is that upper limits are taken into account in the fitting procedure (cite: Boquien19)." (2.2 SED modelling with CIGALE)
   - validation: Comparison of stellar mass, SFR, A_FUV and beta with and without ALMA  
  > "we compare in Fig. [4](#fig:comps) the stellar masses, SFRs, FUV attenuations, and UV continuum $\beta$ slopes obtained with and without the ALMA constraint." (5 Impact of the ALMA constraint)
5. **derive bin properties and scaling relations (beta-MUV, LIR-MUV, IRX-beta, IRX-M*)**: Medians and 25th/75th percentiles of the physical properties per bin; upper limits on bin medians from a normal-distribution fit and 84% z-score; linear regressions combining the JADES stacks with REBELS, ALPINE and other literature stacks  
  > "by fitting a normal distribution to the data and determining the z-score at 84$\%$ confidence level." (4 Dust attenuation properties); "A fit to the REBELS+ALPINE stacked signals combined with our two highest UV magnitude bins yields the following relation:" (4 Dust attenuation properties)
   - parameter: delta (attenuation-curve slope) fixed to 0  
  > "Therefore, we kept $\delta$ fixed to 0 (no modification of the attenuation curve)." (4.1 IRX versus beta)
   - assumption: IRX compared with Calzetti00 relation with beta0=-2.3 and Reddy18 starburst and SMC relations with beta0=-2.6  
  > "our estimates are compatible with both a (cite: Calzetti00) with $\beta_0=-2.3$ and (cite: Reddy18) relations (starbursts and SMC, using $\beta_0=-2.6$)." (4.1 IRX versus beta)
   - fitting: Linear regression fits (no sampler or priors stated)  
  > "we obtain the following relation from a linear regression fit:" (4 Dust attenuation properties)
   - validation: Delta-BIC test of letting delta free: significant improvement for only 3.7% of the sample  
  > "proved to be statistically significant for only 3.7$\%$ of the sample." (4.1 IRX versus beta)
6. **test dust temperature assumption**: Rerun CIGALE fixing Tdust to 30, 33, 36, 39, 42, 45 and 47 K and compare LIR, IRX-M* and IRX-beta  
  > "We show the results of the SED modelling run for each dust temperature assumption (30, 33, 36, 39, 42, 45, and 47 K)." (4.3 Impact of dust temperature assumption)
   - software: CIGALE
   - parameter: Tdust range 30-47 K; 30 K is REBELS-32 temperature (39 K) minus 9 K lower error  
  > "We thus only decrease T$_{\mathrm{dust}}$ from the original assumption (47 K) down to a minimum value of 30 K" (4.3 Impact of dust temperature assumption)
   - assumption: REBELS temperatures taken as the maximum Tdust for the sample  
  > "we consider the dust temperature of REBELS galaxies determined by (cite: Sommovigo22) to be the maximum dust temperature for our galaxies." (4.3 Impact of dust temperature assumption)
   - fitting: _not stated_
   - validation: Temperatures above ~36 K give similar LIR  
  > "However, temperatures higher than $\sim$36 K result in similar $L_{\mathrm{IR}}$." (4.3 Impact of dust temperature assumption)
7. **extend stacking and SED modelling to z>7 and study beta and LIR evolution**: Same ALMA stacking and SED modelling at 7<z<9 and 9<z<12 with Tdust=47 K; LIR corrected for the CMB effect using DaCunha13  
  > "We then perform the same SED modelling procedure on the $z>7$ sources as for the $6<z<7$ redshift bin, assuming the same dust temperature of $T_{\rm dust}=$47 K." (5 Infrared constraints at z>7); "We thus correct our $L_{\mathrm{IR}}$ measurement accordingly in Fig. [13](#fig:lirz) where we show them as a function of redshift." (6.1 Evolution of beta)
   - software: CIGALE
   - assumption: Intrinsic UV slope beta0 limited at the blue end to -2.77 by the SFH library  
  > "in our case this value is defined by the lowest intrinsic value allowed by our model: $\beta_0=-2.77$." (6.1 Evolution of beta)
   - fitting: _not stated_
   - validation: Fraction of galaxies at the lowest beta0 (15% overall; 5% at z=9-12) checked to show beta trend is not driven by the model limit  
  > "only 15$\%$ of the galaxies select the lowest possible value of $\beta_0$." (6.1 Evolution of beta)
8. **fit the AV versus inverse sSFR relation and test it with a mock analysis**: Linear fit of log AV vs log sSFR^-1 for the 6<z<12 sample binned by beta; mock CIGALE analysis, higher Tdust (60 K at 9<z<12) and a UV-NIR-only run used to test the slope  
  > "we show the V-band attenuation as a function of the inverse sSFR for the whole sample ($6<z<12$) binned by UV slope $\beta$" (6.2 Dust formation in early galaxies); "We thus test the impact of increasing the assumption on T$_{\rm dust}$ for galaxies in the $9<z<12$ to 60 K" (6.2 Dust formation in early galaxies)
   - software: CIGALE
   - fitting: _not stated_
   - validation: Mock analysis: sSFR^-1 recovered with a 60% systematic overestimate, AV underestimated by -0.4 mag  
  > "sSFR$^{-1}$ is recovered within errorbars with a systematic overestimate (60%) and that A$_{\rm V}$ is systematically underestimated by -0.4 mag." (6.2 Dust formation in early galaxies)

## Software

- **CIGALE** : UV-to-FIR SED modelling with energy balance, with and without the ALMA constraints  
  > "assumes energy balance: the energy absorbed in the UV-optical is re-emitted in the IR." (2.2 SED modelling with CIGALE)
- **EAZY** : Photometric redshifts available in the JADES catalogue  
  > "Photometric redshifts available in the JADES catalogue are computed with the code" (2.1 Sample selection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stacked 1.1 mm flux density, -22<MUV<-20 (6<z<7) | 5.4 | 3.7 | uJy | 3 | each galaxy with a UV magnitude within $-22<M_{\mathrm{UV}}<-20$ is attributed a S$_{1.1\,mm}$ of 5.4$\pm$3.7 $\mu$Jy. |
| Stacked 1.1 mm flux density, -20<MUV<-19 (6<z<7) | 5.2 | 3.0 | uJy | 3 | 5.2$\pm$3.0 |
| Stacked flux density, -19<MUV<-18 (6<z<7) | <4.8 | not stated | uJy | 3 | $<$4.8 |
| Stacked flux density, 9<log M*<10 (6<z<7) | 8.7 | 3.8 | uJy | 3 | 8.7$\pm$3.8 |
| Stacked flux density, 10<log M*<11 (6<z<7) | 38.5 | 29.0 | uJy | 3 | 38.5$\pm$29.0 |
| 3 sigma upper limit on stacked flux, 8<log M*<9 (6<z<7) | 2.5 | not stated | uJy | 3 | results in a 3$\sigma$ upper limit of 2.5 $\mu$Jy. |
| Number of 6<z<7 galaxies covered by ALMA | 4464 of 5974 | not stated | galaxies | 3 | Out of the 5974 galaxies in our $6<z<7$ sample, 4464 are covered by one or multiple ALMA pointings |
| Median SFR difference with vs without ALMA for log M*>8 galaxies | -0.37 | not stated | dex | 4 | with a median difference of -0.37 dex |
| Median A_FUV difference with vs without ALMA for the most massive sources | -0.49 | not stated | mag | 4 | with a median value of -0.49 mag |
| Example galaxy (z=6.78, MUV=-20.5) AV with ALMA constraint | 0.3 (1.1 without ALMA) | not stated | mag | 4 | Using ALMA stacked measurement as a constraint, the A$_{\rm V}$ decreases to 0.3 mag. |
| beta vs MUV relation (combined with REBELS, Austin24, Roberts-Borsani24 stacks) | beta = -0.08 x MUV - 3.70 | slope +-0.03, intercept +-0.11 | dimensionless | 5 | \beta = -0.08\pm0.03 \times M_{\mathrm{UV}} -3.70\pm0.11. |
| LIR vs MUV relation (REBELS+ALPINE stacks plus two brightest JADES bins) | log(LIR/Lsun) = -0.31 x MUV + 4.31 | slope +-0.05, intercept +-0.42 | dimensionless | 5 | \log \left(L_{\mathrm{IR}}/L_{\odot}\right) = -0.31\pm0.05 \times M_{\mathrm{UV}} + 4.31\pm0.42. |
| Overestimate of LIR by the bright-end relation at MUV=-18.4 and -17.4 | 0.45 and 0.56 | not stated | dex | 5 | overestimates the $L_{\mathrm{IR}}$ by 0.45 dex and 0.56 dex, respectively. |
| Median beta of the 6<z<7 sample (with ALMA) | -2.25 | not stated | dimensionless | 5 | our sample has relatively blue $\beta$ with a median value of -2.25. |
| Fraction of sample for which a free delta slope significantly improves the fit (Delta-BIC) | 3.7 | not stated | percent | 5 | proved to be statistically significant for only 3.7$\%$ of the sample. |
| Median beta at z~12 | -2.14 | 0.21 | dimensionless | 7 | we find a median value of -2.14$\pm$0.21 which is slightly redder. |
| Slope and intercept of log AV vs log sSFR^-1 relation | slope 0.61, intercept -0.30 | slope +-0.05, intercept +-0.03 | dimensionless | 8 | \log A_{\mathrm{V}} = (0.61\pm0.05) \times \log \mathrm{sSFR}^{-1} - (0.30\pm0.03). |
| AV-sSFR^-1 slope with Tdust=60 K at 9<z<12 | 0.63 | 0.05 | dimensionless | 8 | We obtain a slope of 0.63$\pm$0.05 |
| AV-sSFR^-1 slope from UV-NIR-only run, reddest beta bin discarded | 0.91 | 0.17 | dimensionless | 8 | We obtain a slope of 0.91$\pm$0.17 if we discard the reddest $\beta$ bin |

## Qualitative findings

- ALMA stacks give tentative signals for MUV<-19 and log M*>9 galaxies at 6<z<7 and upper limits for fainter, lower-mass and z>7 sources  
  > "We obtain tentative signals for the brightest UV galaxies ($M_{\mathrm{UV}}<-19$ mag) as well as for the most massive ones ($\log M_\star/M_\odot>9$) at $6<z<7$" (abstract)
- Positions of the JADES z~6.5 sample on IRX-beta and IRX-M* are consistent with ALPINE and REBELS, suggesting similar dust composition and content  
  > "suggesting that the dust composition and content of our mass-selected sample are similar to these UV-selected galaxies." (abstract)
- Using ALMA constraints lowers SFR and FUV attenuation for log M*>8 galaxies, indicating biases in SED-derived properties without FIR constraints  
  > "This comparison suggests the evidence of biases when estimating the physical properties of $z>6$ galaxies without FIR constraints." (5 Impact of the ALMA constraint)

## Claim tuples

- H: Does FIR information from ALMA stacks change the SED-derived properties of 6<z<7 galaxies? | E: CIGALE run on the JADES galaxies with and without the stacked 1.1 mm flux densities as constraints | R: SFR lower by -0.37 dex and A_FUV lower by -0.49 mag for log M*>8 galaxies, with slightly higher stellar masses and older ages | F: SED modelling without FIR constraints biases the properties of z>6 galaxies | **supported**
- H: Does the LIR-MUV relation hold at fainter UV magnitudes? | E: ALMA stacks in MUV bins compared with an extrapolation of the REBELS+ALPINE relation | R: Relation overestimates LIR by 0.45 and 0.56 dex at MUV=-18.4 and -17.4 | F: Possible breakdown of the LIR-MUV relation at MUV>-19, tentative | **partially**
- H: Do mass-selected z~6.5 galaxies show dust properties different from UV-selected samples? | E: Place the stacked bins on the IRX-beta and IRX-M* diagrams | R: Points are compatible with Calzetti00 (beta0=-2.3) and Reddy18 relations and with REBELS; no clear break-down of the Calzetti00 relation at z>6; IRX-M* only weakly constrained | F: Dust composition and content similar to UV-selected samples; no fundamental evolution | **partially**
- H: Does beta evolve with redshift over 6<z<12 in the bulk of galaxies? | E: SED-derived beta for the sample at 6<z<7, 7<z<9 and 9<z<12, with a test of the beta0 lower limit of the SFH library | R: Only 15% of galaxies select the lowest beta0; median beta at z~12 is -2.14+-0.21 | F: No clear evolution of beta with redshift, consistent with Topping24 at faint MUV | **supported**
- H: Does the AV versus sSFR^-1 relation of Langeroodi24 hold for photometric SED-based estimates? | E: Fit log AV vs log sSFR^-1 for 6<z<12 galaxies binned by beta, with mock, Tdust and no-ALMA tests | R: Linear relation confirmed with slope 0.61+-0.05 (flatter than Langeroodi24); the UV-NIR-only run agrees with Langeroodi24 | F: The flatter slope is caused by including ALMA constraints; dust production tracks star formation | **supported**

## Reasoning

- Why this data: Archival A3COSMOS data allow statistics and redshift reach beyond UV-selected samples by stacking JADES galaxies  
  > "The goal of this work is to extend these studies in terms of statistics but also redshift with a statistical analysis using the A$^3$COSMOS (A$^3$GOODSS) archival data" (1 Introduction)
- Why this method: uv-domain stacking impractical for so many heterogeneous pointings; stack in the flux domain instead  
  > "Because of this large number of galaxies, it was impractical to stack them in the $uv$-domain" (3 ALMA stacking of JADES galaxies)
- Alternative: uv-domain stacking rejected as impractical  
  > "it was impractical to stack them in the $uv$-domain in order to deal with the heterogeneity in angular resolution" (3 ALMA stacking of JADES galaxies)
- Alternative: Free attenuation-curve slope delta tested but kept fixed to 0 as the fit improved significantly for only 3.7% of the sample  
  > "In our process, we tested letting the $\delta$ slope of the attenuation curve free, like in (cite: Boquien22)." (4.1 IRX versus beta)
- Alternative: Photo-z quality criteria of Cole23 tested; not applied since no strong impact  
  > "we find no strong impact on our results, a conclusion also reached by (cite: Cole23)." (2.1 Sample selection)
- How they decided it was enough: _not stated_
- Limitation (authors): Only one ALMA data point, so dust mass cannot be constrained and LIR depends strongly on the assumed IR SED shape  
  > "However, with only one flux measurement in the IR, the $L_{\mathrm{IR}}$ strongly depends on the assumption taken on the IR SED shape." (4.3 Impact of dust temperature assumption)
- Limitation (authors): Most bins are only upper limits; stack signals are tentative  
  > "We obtain tentative signals for the brightest UV galaxies" (abstract)
- Limitation (authors): Most massive bin contains only 4 galaxies and is subject to statistical variation  
  > "but this bin contains only 4 galaxies and is thus more subject to statistical variations." (4.3 Impact of dust temperature assumption)
- Limitation (authors): SED modelling cannot reach beta bluer than the lowest intrinsic beta0 of the model  
  > "there is a caveat in using SED modelling to measure $\beta$ as models are limited to a given $\beta$ value toward the blue side of the distribution" (6.1 Evolution of beta)
- Caveat (inferred, ours): Stacked fluxes are assigned back to individual galaxies by MUV or mass bin, so the ALMA constraint is not independent per galaxy
- Caveat (inferred, ours): Dust temperature fixed at 47 K drives LIR for most bins; only partly tested down to 30 K
- Caveat (inferred, ours): Many stacks are upper limits, so scaling-relation conclusions (LIR-MUV break, IRX-M*) are weakly constrained
- Caveat (inferred, ours): Central-pixel stacking of heterogeneous archival images assumes unresolved sources and depends on the 1.1 mm template and photo-z accuracy

## Reproducibility

- Data public (paper): Archival ALMA data from the A3COSMOS/A3GOODSS database; JADES data public via the survey release  
  > "We used the A$^3$GOODSS ALMA archival database, part of the A$^3$COSMOS database (cite: Liu19; Adscheid24), to perform a stacking analysis on our galaxy sample" (3 ALMA stacking of JADES galaxies)
- Products in archive: _not stated_
- Missing: List of ALMA pointings/images/project codes used from A3GOODSS
- Missing: Per-galaxy catalogue and bin assignments
- Missing: Full CIGALE configuration file and version
- Missing: Noise estimation details and the redshift/template handling in the 1.1 mm renormalisation
- Data volume (inferred): Uses A3COSMOS/A3GOODSS pre-made images and catalogues rather than raw ALMA data; likely tens of GB of images plus the JADES catalogue
- Score (inferred): 3/5, Public archival ALMA database and JADES catalogue plus a clear stacking recipe and numeric stacks, but no project codes, image selection, noise estimation details or CIGALE version/config are given
- Rediscovery candidate: no, Image selection, noise handling and full CIGALE configuration are not specified, so the stacks and SED results cannot be redone from the text alone

## Links

- Method: Ciesla24 (cite: Ciesla24) (Source of the CIGALE setup and non-parametric SFH library)
- Method: Boquien19 (cite: Boquien19) (CIGALE SED modelling code)
- Method: Liu19; Adscheid24 (cite: Liu19; Adscheid24) (A3COSMOS database)
- Method: Schreiber18 (cite: Schreiber18) (Dust emission library used in the SED modelling)
- Method: Bethermin12 (cite: Bethermin12) (SED template used for renormalising ALMA fluxes to 1.1 mm)
- Companion: Magnelli24 (cite: Magnelli24) (A3COSMOS stacking of a mass-selected sample at 4<z<5)
- Companion: Bowler24 (cite: Bowler24) (REBELS stacked properties at z~7 used for comparison)
- Companion: Langeroodi24 (cite: Langeroodi24) (AV versus inverse sSFR relation compared with)
- Companion: Topping24 (cite: Topping24) (beta-MUV relation and evolution compared with)
- Related: A3COSMOS
- Related: JADES
- Related: JEMS
- Related: REBELS
- Related: ALPINE
- Related: SERENADE
- Related: ALMA-CRISTAL

## Checks

```json
{
 "quotes": 120,
 "quotes_ok": 120,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00173.S",
  "2012.1.00775.S",
  "2012.1.00869.S",
  "2012.1.00983.S",
  "2013.1.00718.S",
  "2013.1.00884.S",
  "2013.1.01271.S",
  "2013.1.01292.S",
  "2015.1.00039.S",
  "2015.1.00098.S",
  "2015.1.00543.S",
  "2015.1.00821.S",
  "2015.1.00870.S",
  "2015.1.01096.S",
  "2015.1.01379.S",
  "2015.1.01447.S",
  "2015.A.00009.S",
  "2016.1.00324.L",
  "2016.1.00721.S",
  "2016.1.01240.S",
  "2017.1.00190.S",
  "2017.1.00428.L",
  "2017.1.00755.S",
  "2017.1.01027.S",
  "2018.1.00164.S",
  "2018.1.00567.S",
  "2018.1.01044.S",
  "2019.1.01528.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 112,
  "stated": 76,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
