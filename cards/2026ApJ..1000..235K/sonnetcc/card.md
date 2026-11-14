# Forecasting the Observable Rates of Gravitationally Lensed Supernovae for the PASSAGES Dusty Starbursts

`2026ApJ..1000..235K` | The Astrophysical Journal 2026 | first author: Kamieneski, Patrick S. | arXiv: 2510.00923 | DOI: 10.3847/1538-4357/ae459e

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, transients, cosmology
- Question: Can a targeted search of lensed hyperluminous infrared dusty starbursts (the PASSAGES sample) yield high rates of gravitationally lensed supernovae suitable for time-delay cosmography?  
  > "the merits of a targeted strategy focused on lensed hyperluminous infrared galaxies among the most rapidly star-forming galaxies known in the Universe." (abstract)
- Target **PASSAGES lensed DSFG sample (21 objects used)**: coordinates _not stated_; z/distance z ~ 1.1 - 3.5 (per-object z_s in Table 1)  
  > "we have attempted to forecast the rates of glSNe that might be reasonably observed for a set of 21 dusty star-forming galaxies from the PASSAGES sample, spanning $z\approx 1.1 - 3.5$." (Summary); distance from _not stated_
- Target **PJ1127+42 (G165.7+67.0 field)**: coordinates _not stated_; z/distance z = 2.24  
  > "For the pair of DSFGs PJ1127+42 at $z=2.24$ (comprising Arcs 1abc, 3abc, 4abc, and 6abc lensed by the G165.7+67.0 cluster)" (3.1 / 2.4 Adopting a fraction of unobscured SFR); distance from _not stated_
- Target **PJ0116-24**: coordinates _not stated_; z/distance z = 2.13  
  > "for PJ0116-24 ($z=2.13$)" (2.4 Adopting a fraction of unobscured SFR); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01518.S, 2017.1.01214.S, 2016.1.00048.S, 2019.1.01636.S
- bands: ALMA 1 mm dust continuum (VLA 6 GHz / 5 cm for northern sources not covered by ALMA)  
  > "we rely on the 1mm dust continuum observed with the Atacama Large Millimeter/submillimeter Array (ALMA), by which we apportion the total IR SED-derived SFR" (ALMA 1mm continuum and VLA 6 GHz)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA theta ~ 0.4 - 0.8 arcsec; VLA theta ~ 0.3 - 0.7 arcsec  
  > "The achieved resolutions for the ALMA and VLA observations ranged from $\theta \approx 0.4 - 0.8\ensuremath{''}$ and $\theta \approx 0.3 - 0.7\ensuremath{''}$, respectively." (ALMA 1mm continuum and VLA 6 GHz)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLA (A-configuration, 6 GHz)**: 6 GHz (5 cm) continuum images used in place of ALMA for northern-declination sources  
  > "For northern-declination sources not covered in these observations, we instead use 6 GHz (5 cm) continuum imaging from the" (ALMA 1mm continuum and VLA 6 GHz); "Very Large Array in A-configuration, with angular resolutions relatively close to the ALMA images." (ALMA 1mm continuum and VLA 6 GHz)
- Other facility **Planck (PASSAGES selection)**: parent sample selection of lensed DSFGs  
  > "Planck All-Sky Survey to Analyze Gravitationally-lensed Extreme Starbursts (PASSAGES)" (abstract)
- Other facility **HST Frontier Fields lens models (MAST)**: public lens models used to estimate Einstein radii of literature glSN hosts  
  > "using the publicly-available Frontier Fields lens models (cite: Lotz:2017aa)" (5.2 / 3.4 Identifying candidates with the longest median time delay)
- External data: Total IR SED-derived SFRs for PASSAGES targets  
  > "we apportion the total IR SED-derived SFR (primarily from (cite: Harrington:2016aa; Berman:2022aa))" (ALMA 1mm continuum and VLA 6 GHz) [from (cite: Harrington:2016aa; Berman:2022aa)]
- External data: SFR and magnification mu estimates per target (Table 1)  
  > "for SFR and $\mu$ estimates: (1) (cite: Liu:2024ae); (2) (cite: Kamieneski:2024aa) (3) (cite: Berman:2022aa)" (Table 1) [from (cite: Liu:2024ae); (cite: Kamieneski:2024aa); (cite: Berman:2022aa); (cite: Harrington:2016aa); (cite: Foo:2025aa); (cite: Wang:2024ab); (cite: Kamieneski:2024ac)]
- External data: Balmer decrement E(B-V) = 0.85 +/- 0.25 for PJ1127+42 (NIRSpec)  
  > "(cite: Frye:2024aa) found a value of $E(B-V) = 0.85 \pm 0.25$ through NIRSpec observations" (2.4 Adopting a fraction of unobscured SFR) [from (cite: Frye:2024aa)]
- External data: Balmer decrement E(B-V) = 0.95 +/- 0.13 for PJ0116-24 (VLT/ERIS)  
  > "(cite: Liu:2024ae) derived a color excess through Balmer decrement of $E(B-V) = 0.95 \pm 0.13$ with VLT/ERIS observations" (2.4 Adopting a fraction of unobscured SFR) [from (cite: Liu:2024ae)]
- External data: SN Ia rate parameterization R_Ia(M*, SFR)  
  > "(cite: Smith:2012aa) included a power law for both terms in their bivariate parameterization, favoring" (3.2 Estimating the rate of Type Ia SNe) [from (cite: Smith:2012aa)]
- External data: Stellar masses of the G165 DSFG pair from JWST  
  > "yield stellar masses of ${\rm log}_{10} M_\star \approx 10.2$ and 10.3 (cite: Frye:2024aa; Kamieneski:2024ac)" (3.2 Estimating the rate of Type Ia SNe) [from (cite: Frye:2024aa; Kamieneski:2024ac)]
- External data: Lens models used for median and maximum time delays  
  > "Median (and maximum) time delays for PASSAGES objects derived in this work (unless otherwise noted), using lens models from the supplied references." (Table 2) [from Table 2 references (cite: Kamieneski:2024aa), (cite: Amodeo:2018aa), (cite: Foo:2025aa), (cite: Wang:2024ab), (cite: Frye:2024aa), (cite: Diaz-Sanchez:2017aa)]
- Simulation/model as data: Published lens models (LENSTOOL-based for PASSAGES) giving magnification, caustics, multiplicity and time delays  
  > "their similarity to the LENSTOOL models used for the PASSAGES objects" (Table 2); "Median (and maximum) time delays for PASSAGES objects derived in this work (unless otherwise noted), using lens models from the supplied references." (Table 2)

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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA and VLA observations, data reduction and imaging are described in the earlier PASSAGES paper  
  > "These observations are described in detail in Sections 2.4 and 2.5 of (cite: Kamieneski:2024aa), with images shown in their Figure 2." (ALMA 1mm continuum and VLA 6 GHz) [from Sections 2.4 and 2.5 of (cite: Kamieneski:2024aa)]
- Total IR SED-derived SFR per target  
  > "we apportion the total IR SED-derived SFR (primarily from (cite: Harrington:2016aa; Berman:2022aa))" (ALMA 1mm continuum and VLA 6 GHz) [from (cite: Harrington:2016aa; Berman:2022aa)]
- Magnifications and lens models taken from earlier papers  
  > "The apparent rates, $\mu$SFR, and magnifications $\mu$ are retrieved from the references given in Table" (3.1 Computing expected intrinsic and observer-frame rates of CCSNe) [from Table 1 references]

### Not stated but needed to reproduce (our reading)

- Which ALMA project, band, array configuration and spectral setup apply to each target (deferred to Kamieneski et al. 2024a)
- Calibration, imaging and self-calibration choices for the 1 mm ALMA images (CASA version, robust, cell, masks)
- The lens models and the procedure that turns the model caustics plus the continuum map into per-pixel multiplicity N_i,j (grid, source-plane mapping, noise masking, how undetected or non-ALMA targets were treated)
- Exact stellar masses and Delta MS values adopted per target for R_Ia (only limits and a procedure are given)
- How the median and maximum lens-model time delays were computed (code, image sets, treatment of demagnified images)
- Which sample members enter the Spearman test (two targets have no delay estimates) and how errors are used
- Machine-readable per-target tables

## Analysis recipe

1. **Compute effective image multiplicity N_eff from ALMA/VLA continuum and lens model**: Weight the lens-model image multiplicity by the star-formation distribution, using the 1 mm dust continuum (or 6 GHz VLA) as the map of SFR  
  > "which is the average multiplicity weighted by the distribution of star formation." (2.2 Determining the expected value of image multiplicity); "we rely on the 1mm dust continuum observed with the Atacama Large Millimeter/submillimeter Array (ALMA), by which we apportion the total IR SED-derived SFR" (ALMA 1mm continuum and VLA 6 GHz)
   - software: LENSTOOL (lens models)
   - parameter: pixel-based N_eff = sum(N_ij SFR_ij) / sum(SFR_ij)  
  > "where SFR$_{i,j}$ and $N_{i,j}$ are the star formation rate and multiplicity, respectively, at pixel $(i,j)$." (2.2 Determining the expected value of image multiplicity)
   - parameter: fractional uncertainty on N_eff = 20%  
  > "we adopt a conservative fractional uncertainty[^3] of 20% on $\mathcal{N}_{\rm eff}$." (ALMA 1mm continuum and VLA 6 GHz)
   - assumption: Dust (or radio) continuum surface brightness traces the 2D probability density of supernovae  
  > "Since the star formation is likely dominated by the obscured mode probed by SFR$_{\rm IR}$, the distribution $\Sigma_{\rm SFR_{\rm IR}}$ is our best estimate of the 2d probability density function of core-collapse supernovae" (ALMA 1mm continuum and VLA 6 GHz)
   - fitting: _not stated_
   - validation: _not stated_
2. **Adopt an unobscured star-formation fraction**: Direct Balmer-decrement estimates for two targets, an assumed 20 +/- 10% for the rest  
  > "for objects without these Balmer decrement measurements at present, we adopt a range of $f_{\rm unobsc} = 20\pm 10\%$" (2.4 Adopting a fraction of unobscured SFR)
   - parameter: f_unobsc ~ 31% for PJ1127+42 arcs  
  > "this gives $f_{\rm unobsc} \approx 31\%$." (2.4 Adopting a fraction of unobscured SFR)
   - parameter: f_unobsc ~ 32% for PJ0116-24  
  > "and ${\rm SFR}_{\rm H\alpha,corr} = 470 \pm 60~M_\odot ~{\rm yr}^{-1}$ and $f_{\rm unobsc} \approx 32\%$." (2.4 Adopting a fraction of unobscured SFR)
   - assumption: Calzetti attenuation law and case B recombination for the Balmer decrement correction  
  > "for case B recombination (cite: Osterbrock:2006aa)." (2.4 Adopting a fraction of unobscured SFR)
   - fitting: _not stated_
   - validation: Compared with Lyman-continuum escape fractions and Balmer-decrement studies of other DSFGs  
  > "this fraction of 20% has some precedent." (2.4 Adopting a fraction of unobscured SFR)
3. **Convert SFR to intrinsic core-collapse SN rate**: R_CC = k_CC x SFR with k_CC from a Kroupa IMF integrated over 8-50 Msun progenitors  
  > "the core-collapse rate is linearly related to the rate of star formation," (3.1 Computing expected intrinsic and observer-frame rates of CCSNe); "As the SFR estimates used in this work are based on a (cite: Kroupa:2001aa) IMF, we adopt a value of $k_{\rm CC}=0.0104~M_\odot^{-1}$." (3.1 Computing expected intrinsic and observer-frame rates of CCSNe)
   - parameter: k_CC = 0.0104 per Msun (Kroupa IMF)  
  > "we adopt a value of $k_{\rm CC}=0.0104~M_\odot^{-1}$." (3.1 Computing expected intrinsic and observer-frame rates of CCSNe)
   - assumption: Fiducial LCDM cosmology Om=0.3, OL=0.7, H0=70  
  > "Throughout, we adopt a fiducial $\Lambda$CDM concordance cosmology of $\Omega_m = 0.3$, $\Omega_\Lambda = 0.7$, and $H_0 = 70~{\rm km~s}^{-1}~{\rm Mpc}^{-1}$." (Introduction)
   - fitting: _not stated_
   - validation: Consistent with the optically-thick regime of the Mattila & Meikle FIR relation  
  > "This is consistent with the optically-thick regime ($\epsilon \approx 1$) of equation 5 of (cite: Mattila:2001aa)" (3.1 Computing expected intrinsic and observer-frame rates of CCSNe)
4. **Estimate intrinsic SN Ia rate**: Use the Smith et al. (2012) bivariate mass plus SFR relation, with stellar-mass limits from the star-forming main sequence  
  > "For our purposes, we consider it justifiable to use the (cite: Smith:2012aa)" (3.2 Estimating the rate of Type Ia SNe); "along with the total SFRs inferred from the IR, in order to derive lower limits in $M_\star$." (Appendix: Estimating Type Ia supernova rates robustly without stellar mass measurements)
   - parameter: Delta MS < 0.9 dex upper limit on sSFR (Speagle et al. 2014 main sequence)  
  > "We can use this upper limit in sSFR of 0.9 dex above the main sequence (computed according to (cite: Speagle:2014aa))," (Appendix: Estimating Type Ia supernova rates robustly without stellar mass measurements)
   - assumption: Dependence on M* is subdominant to SFR in the star-forming regime  
  > "However, ultimately the dependence of Equation" (3.2 Estimating the rate of Type Ia SNe)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute observable SN image rates**: Multiply intrinsic rate by f_unobsc, N_eff and time dilation (1+z)^-1  
  > "$\mathcal{R}_{\rm Ia,obs} \equiv f_{\rm unobsc} \cdot R_{\rm Ia} \cdot \mathcal{N}_{\rm eff} \cdot (1+z)^{-1}$" (3.2 Estimating the rate of Type Ia SNe)
   - assumption: Gives a maximum recoverable fraction, not a detectable fraction for any campaign  
  > "This does not quantify the fraction of supernovae that could be detectable in any observational campaign" (3.1 Computing expected intrinsic and observer-frame rates of CCSNe)
   - fitting: _not stated_
   - validation: Compared with Mantynen et al. 2025 undetectable fractions in local LIRGs  
  > "Using our formulation, this would suggest $f_{\rm unobsc} = 34^{+14.6}_{-8.6}\%$." (3.1 Computing expected intrinsic and observer-frame rates of CCSNe)
6. **Relate lens-model median time delay to Einstein radius**: Equivalent Einstein radius per target, lens-model median delay of the first-arriving images, rank correlation  
  > "which is the radius of the smallest circle centered on the peak of lensing convergence $\kappa$ that contains an average $\langle \kappa \rangle < 1$" (3.4 Identifying candidates with the longest median time delay); "Median (and maximum) time delays for PASSAGES objects derived in this work (unless otherwise noted), using lens models from the supplied references." (Table 2)
   - software: LENSTOOL
   - fitting: _not stated_
   - validation: Spearman rank correlation coefficient 0.89  
  > "there is a clear strong correlation between $t_d$ and $\theta_E$ (Spearman’s rank correlation coefficient $\rho = 0.89$, with high significance $p\ll 0.01$)" (3.4 Identifying candidates with the longest median time delay)
7. **Fit power-law of median delay versus physical Einstein radius**: Power-law fit of median delay (dilated to lens redshift) against R_Ein in kpc, compared with the SIS maximum-delay bound  
  > "$\widetilde{t_d} \propto (R_{\rm Ein})^{1.53 \pm 0.16}$, slightly shallower than the prediction for the" (Appendix: The connection between typical time delays and image separations)
   - fitting: _not stated_
   - validation: Lens-model maximum delays stay below the SIS bound  
  > "We observe that the maximum model-predicted time delays $t_d$ remain below ${\rm max}(\Delta t_{ij})$." (Appendix: The connection between typical time delays and image separations)

## Software

- **CASA** : listed in the Software section; specific use not stated  
  > "blobcat (cite: Hales:2012aa), casa (cite: McMullin:2007aa), LENSTOOL (cite: Kneib:1993aa; Kneib:1996aa; Jullo:2007aa; Jullo:2009aa)" (Software)
- **blobcat** : listed in the Software section; specific use not stated  
  > "blobcat (cite: Hales:2012aa), casa (cite: McMullin:2007aa), LENSTOOL (cite: Kneib:1993aa; Kneib:1996aa; Jullo:2007aa; Jullo:2009aa)" (Software)
- **LENSTOOL** : lens models of the PASSAGES objects (magnifications, multiplicity, delays)  
  > "their similarity to the LENSTOOL models used for the PASSAGES objects" (Table 2)
- **Ned Wright’s Cosmology Calculator** : listed in the Software section; cosmological distances implied  
  > "Ned Wright’s Cosmology Calculator (cite: Wright:2006aa)" (Software)
- **JWST Exposure Time Calculator** : estimate of JWST/NIRCam sensitivity for a hypothetical detection  
  > "Sensitivity is estimated with the JWST Exposure Time Calculator (cite: Pontoppidan:2016aa)." (3.3 Predicting the rate of independent supernova events)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Intrinsic core-collapse SN rate R_CC range (21 PASSAGES targets) | 1.8 - 65 (median 11) | not stated | yr^-1 | 3 | we estimate a range of intrinsic rates $R_{\rm CC} \approx {1.8 - 65}~{\rm yr}^{-1}$ (core-collapse; median $11~{\rm yr}^{-1}$) |
| Intrinsic SN Ia rate R_Ia range | 0.2 - 6.4 (median 1.1) | not stated | yr^-1 | 4 | $R_{\rm Ia} \approx {0.2 - 6.4}~{\rm yr}^{-1}$ (Type Ia; median $1.1~{\rm yr}^{-1}$) |
| Observable CCSN image rate range | 0.4 - 8.0 (median 2.3) | not stated | yr^-1 | 5 | with observable rates $\mathcal{R}_{\rm CC} \approx {0.4 - 8.0}~{\rm yr}^{-1}$ (median $2.3~{\rm yr}^{-1}$) |
| Observable SN Ia image rate range | 0.2 - 3.9 (median 1.1) | not stated | yr^-1 | 5 | $\mathcal{R}_{\rm Ia} \approx {0.2 - 3.9}~{\rm yr}^{-1}$ (median $1.1~{\rm yr}^{-1}$) |
| Time-dilated CCSN rate R_CC/(1+z) range | 0.8 - 20 (median 3.5) | not stated | yr^-1 | 5 | we find ranges of $0.8 - 20~{\rm yr}^{-1}$ (median $3.5~{\rm yr}^{-1}$) |
| Time-dilated SN Ia rate R_Ia/(1+z) range | 0.1 - 2.0 (median 0.3) | not stated | yr^-1 | 5 | and $0.1 - 2.0~{\rm yr}^{-1}$ (median $0.3~{\rm yr}^{-1}$) |
| Fraction of sample with N_eff > 2 | 90% | not stated | percent | 1 | the vast majority ($90\%$) of objects in the full sample have an expected value of multiplicity, $\mathcal{N}_{\rm eff} > 2$ |
| Unobscured fraction f_unobsc, PJ1127+42 Arc 1 | ~31 | not stated | percent | 2 | this gives $f_{\rm unobsc} \approx 31\%$. |
| Unobscured fraction f_unobsc, PJ0116-24 | ~32 | not stated | percent | 2 | and ${\rm SFR}_{\rm H\alpha,corr} = 470 \pm 60~M_\odot ~{\rm yr}^{-1}$ and $f_{\rm unobsc} \approx 32\%$. |
| Spearman rank correlation, median delay vs Einstein radius | 0.89 | p << 0.01 | dimensionless | 6 | (Spearman’s rank correlation coefficient $\rho = 0.89$, with high significance $p\ll 0.01$) |
| Power-law slope of median delay vs R_Ein | 1.53 | 0.16 | dimensionless | 7 | $\widetilde{t_d} \propto (R_{\rm Ein})^{1.53 \pm 0.16}$, slightly shallower than the prediction for the |
| Einstein radius, PJ1127+42 DSFG arc (z=2.24) | 10.7 | 1.1 | arcsec | 6 | we measure $\theta_{\rm Ein} = 10.7\ensuremath{''} \pm 1.1\ensuremath{''}$ for the $z=2.24$ DSFG arc on the southwest side of the cluster, |
| Einstein radius, SN H0pe arc (z=1.78) | 21.1 | 0.5 | arcsec | 6 | and $21.1\ensuremath{''} \pm 0.5\ensuremath{''}$ for the $z=1.78$ arc hosting SN H0pe on the northeast side. |

## Qualitative findings

- Time dilation reduction of observable rate is approximately offset by multiple-imaging boost  
  > "This particularly emphasizes our finding that the decrement in observable rate due to redshift time dilation is approximately counteracted by the boost provided by multiple imaging." (3.2 Estimating the rate of Type Ia SNe)
- PASSAGES targets lie well above Frontier Fields arcs in SN rate  
  > "Most are even $>2$ dex above typical arcs in the Frontier Fields" (3.3 Predicting the rate of independent supernova events)

## Claim tuples

- H: Lensed HyLIRGs in PASSAGES have extraordinarily high intrinsic and observable SN rates | E: Scale lens-model-corrected IR SFRs to SN rates with k_CC and the Smith et al. relation, then apply f_unobsc, N_eff and time dilation | R: R_CC 1.8-65 per yr and R_Ia 0.2-6.4 per yr intrinsic; observable medians 2.3 and 1.1 per yr | F: Targeted monitoring of PASSAGES targets can deliver many more lensed SN opportunities than blind strategies | **supported**
- H: Einstein radius predicts typical lensing time delay | E: Compare lens-model median delays with equivalent Einstein radii for PASSAGES and known glSN hosts | R: Spearman rho = 0.89 and median delay scales as R_Ein^1.53 | F: Large-theta_E cluster lenses are the best targets for long delays | **supported**
- H: Multiple imaging offsets cosmological time dilation of the observable SN rate | E: Compare R_obs, R_obs/f_unobsc and intrinsic rates as functions of redshift | R: Observable rates rise with redshift, driven by higher SFRs, with N_eff roughly constant | F: Decrement from (1+z)^-1 is approximately counteracted by multiple imaging | **supported**
- H: A JWST monitoring campaign of PASSAGES fields would detect lensed SNe | E: Illustrative control-time estimate for 3 epochs of one month each in 18 fields; no mock campaign | R: ~0.5 detections per field and ~9 CCSNe across 18 fields | F: Campaign is feasible but depends on dust attenuation and control time | **partially**

## Reasoning

- Why this data: 1 mm dust continuum (or 6 GHz radio) is used to map the SFR distribution for N_eff  
  > "To infer a map of SFR to compute $\mathcal{N}_{\rm eff}$ with the information available for the majority of PASSAGES, we rely on the 1mm dust continuum" (ALMA 1mm continuum and VLA 6 GHz)
- Why this method: Obscured star formation traced by IR is the best proxy for the supernova spatial distribution  
  > "Since the star formation is likely dominated by the obscured mode probed by SFR$_{\rm IR}$, the distribution $\Sigma_{\rm SFR_{\rm IR}}$ is our best estimate of the 2d probability density function of core-collapse supernovae" (ALMA 1mm continuum and VLA 6 GHz)
- Alternative: Salpeter IMF gives k_CC = 0.0070 per Msun (Kroupa adopted)  
  > "for a (cite: Salpeter:1955aa) IMF[^5], this yields $k_{\rm CC} = 0.0070~M_\odot^{-1}$" (3.1 Computing expected intrinsic and observer-frame rates of CCSNe)
- How they decided it was enough: _not stated_
- Limitation (authors): No mock observing campaign; control time not modelled  
  > "We do not simulate a mock observing campaign in this work, but simply remark that" (3.3 Predicting the rate of independent supernova events)
- Limitation (authors): Stellar masses unconstrained for most targets  
  > "Unfortunately, the stellar masses for the majority of the PASSAGES DSFGs remain unconstrained" (3.2 Estimating the rate of Type Ia SNe)
- Limitation (authors): SN Ia calibration unconstrained for starbursts with log sSFR > -9  
  > "this calibration is unconstrained for starburst galaxies with log(sSFR) $> -9$." (3.2 Estimating the rate of Type Ia SNe)
- Limitation (authors): Observable rate is a maximum recoverable fraction, not a detection forecast  
  > "This does not quantify the fraction of supernovae that could be detectable in any observational campaign" (3.1 Computing expected intrinsic and observer-frame rates of CCSNe)
- Caveat (inferred, ours): The ALMA role is a distribution weight; all numeric rates depend far more on literature SFRs, magnifications and the assumed f_unobsc = 20 +/- 10% than on the ALMA images.
- Caveat (inferred, ours): N_eff uncertainty is a rough 20% rule of thumb rather than propagated from the lens-model posteriors.
- Caveat (inferred, ours): Caustic positions come from lens models of mixed quality, some unpublished (in prep.).
- Caveat (inferred, ours): No test of the time-delay forecast against measured delays other than known glSNe.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA processing parameters (in Kamieneski et al. 2024a)
- Missing: Per-target N_eff derivation and lens models (some in prep.)
- Missing: Stellar masses adopted for R_Ia
- Missing: Time-delay computation details
- Data volume (inferred): Rate tables can be recomputed from published inputs with negligible data; redoing N_eff needs four ALMA projects' 1 mm images (likely a few GB) plus lens models.
- Score (inferred): 3/5, Equations, constants and per-target numeric tables are given, so the rate arithmetic is reproducible, but N_eff and delays need lens models and maps from earlier papers and the ALMA processing is not given here.
- Rediscovery candidate: no, ALMA is a minor input and the main results depend on lens models and literature SFRs not fully specified in this paper.

## Links

- Method: (cite: Kamieneski:2024aa) (Describes the ALMA and VLA observations and processing (Sections 2.4 and 2.5))
- Method: (cite: Harrington:2016aa; Berman:2022aa) (Source of total IR SED-derived SFRs)
- Method: (cite: Smith:2012aa) (SN Ia rate relation used)
- Companion: (cite: Frye:2024aa) (G165 field, SN H0pe and Balmer decrement for PJ1127+42)
- Companion: (cite: Kamieneski:2024ac) (Lens model and stellar masses for G165)
- Companion: (cite: Liu:2024ae) (PJ0116-24 SFR, mass and Balmer decrement)
- Companion: (cite: Foo:2025aa) (PJ0846+15 SFR, magnification and lens model)
- Related: PASSAGES (Planck All-Sky Survey to Analyze Gravitationally-lensed Extreme Starbursts)
- Related: HST Frontier Fields

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 107,
  "stated": 57,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
