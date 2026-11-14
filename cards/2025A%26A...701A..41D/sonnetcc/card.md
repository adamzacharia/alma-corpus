# Millimeter emission from supermassive black hole coronae

`2025A&A...701A..41D` | Astronomy and Astrophysics 2025 | first author: del Palacio, S. | arXiv: 2504.07762 | DOI: 10.1051/0004-6361/202554936

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: agn_and_quasars
- Question: Provide a framework to derive physical properties of SMBH coronae by modelling radio-to-far-infrared SEDs, including the mm synchrotron emission, and test it on a sample of radio-quiet AGN  
  > "We intend to provide a framework to derive physical information of SMBH coronae by modelling their spectral energy distribution (SED) from radio to far infrared frequencies." (abstract)
- Target **GRS 1734-292**: coordinates _not stated_; z/distance 84 Mpc (z=0.021)  
  > "This galaxy is located at a distance of 84 Mpc ($z=0.021$) and is a known hard X-ray source" (B.1 GRS 1734-292); "We adopt a value of $M_\mathrm{BH}=10^{7.84}$ M$_\odot$(cite: Mejia-Restrepo2022)." (B.1 GRS 1734-292); distance from _not stated_
- Target **IC 4329A**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **MCG-06-30-15**: coordinates _not stated_; z/distance D = 34 Mpc  
  > "This RQ-AGN is located at a distance of $D=34$ Mpc" (B.3 MCG-06-30-15); distance from _not stated_
- Target **MCG+08-11-11**: coordinates _not stated_; z/distance z = 0.02  
  > "This LIRG source is located at $z=0.02$ and hosts an SMBH with a mass of $\log{M_\mathrm{BH}} = 7.81$ (cite: Koss2017)." (B.4 MCG+08-11-11); distance from _not stated_
- Target **NGC 985**: coordinates _not stated_; z/distance D ~ 190 Mpc  
  > "This galaxy located at $D\approx 190$ Mpc hosts an SMBH with $M_\mathrm{BH} = 2.2\times 10^8$ M$_\odot$(cite: Inoue2018)." (B.5 NGC 985); distance from _not stated_
- Target **NGC 1068**: coordinates _not stated_; z/distance D ~ 14.6 Mpc (z=0.0033)  
  > "This galaxy is located at $D \approx 14.6$ Mpc ($z=0.0033$)" (B.6 NGC 1068); distance from _not stated_
- Target **NGC 3227**: coordinates _not stated_; z/distance D ~ 23 Mpc  
  > "This galaxy located at $D\approx 23$ Mpc (cite: Ricci2023) hosts a $M_\mathrm{BH} = 4.2\times 10^7$ M$_\odot$ SMBH (cite: Behar2015)." (B.7 NGC 3227); distance from (cite: Ricci2023)  
  > "This galaxy located at $D\approx 23$ Mpc (cite: Ricci2023) hosts a $M_\mathrm{BH} = 4.2\times 10^7$ M$_\odot$ SMBH (cite: Behar2015)." (B.7 NGC 3227)

## Data provenance

- ALMA projects: 2017.1.00236.S, 2019.1.00618.S, 2019.1.01230.S, 2015.1.01047.S, 2023.1.00121.S, 2021.1.00812.S
- bands: Band 3 named for the GRS 1734-292 high-flux epoch; B6-8 and B9-10 named for flux-systematics grouping; per-source bands not stated  
  > "when there are only observations at ALMA B3" (B.1 GRS 1734-292); "except for ALMA observations at B6–8 (212–500 GHz) and B9–10 (600–900 GHz), for which it is 10% and 20%, respectively" (2.2 Parameter fitting)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beam-matched data used whenever possible, even at the cost of angular resolution; coarse-resolution points used only as upper limits  
  > "we use beam-matched data whenever possible, even if that requires compromising angular resolution" (2.2 Parameter fitting)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Non-simultaneous datasets spanning typically several years  
  > "As such, the datasets are non-simultaneous, with typical timespans of several years." (B Source sample)
- pi or archival as stated: Combination of archival and proprietary observations  
  > "The fluxes reported in this work are a combination of archival and proprietary observations." (B Source sample)
- Other facility **VLA (archival, NVAS)**: Archival VLA flux densities for the sample sources  
  > "we search for archival data with the Karl G. Jansky Very Large Array (VLA)" (3.3 Analysis of the sample sources)
- Other facility **VLASS / NVSS / RACS via CIRADA cutout service**: Archival survey cutouts used for additional flux densities  
  > "in particular the VLASS (cite: Lacy2020), NVSS (cite: NVSS), and RACS (cite: Hale2021)" (3.3 Analysis of the sample sources)
- Other facility **LoTSS (LOFAR) and RACS (ASKAP)**: Surveys highlighted among archives used  
  > "we highlight the LoTSS survey with LOFAR (cite: Shimwell2017), the RACS survey with ASKAP (cite: Hale2021)" (B Source sample)
- External data: Published flux densities for all sources (bibliographic search); per-source tables give the references  
  > "For all sources, we do a detailed bibliographic search for published flux densities" (3.3 Analysis of the sample sources) [from various, listed in the Table 1-7 captions]
- External data: IC 4329A SED dataset taken from Inoue & Doi 2018 Table 1  
  > "fit our model to the same dataset presented in Table 1 of (cite: Inoue2018)" (B.2 IC 4329A) [from (cite: Inoue2018)]
- External data: GRS 1734-292 SMBH mass  
  > "We adopt a value of $M_\mathrm{BH}=10^{7.84}$ M$_\odot$(cite: Mejia-Restrepo2022)." (B.1 GRS 1734-292) [from (cite: Mejia-Restrepo2022)]
- External data: GRS 1734-292 corona tau_T and kT_c from X-ray data  
  > "we fix $\tau_\mathrm{T}=2.98$ and $k T_\mathrm{c} = 12$ keV, as derived by (cite: Tortosa2017)" (B.1 GRS 1734-292) [from (cite: Tortosa2017)]
- External data: NGC 1068 SMBH mass  
  > "hosts an SMBH with $M_\mathrm{BH} = (1.66\pm0.01)\times10^7$ M$_\odot$(cite: Gallimore2024)" (B.6 NGC 1068) [from (cite: Gallimore2024)]
- External data: T_c(tau_T) relation used when no direct X-ray determination exists  
  > "we adopt the parameterisation for $T_\mathrm{c}(\tau_\mathrm{T})$ from (cite: Tortosa2018)" (2.2 Parameter fitting) [from (cite: Tortosa2018)]
- External data: Correlation between 100-GHz luminosity and 14-150 keV luminosity used to predict X-ray luminosities  
  > "into the correlation from (cite: Ricci2023) between the 100-GHz luminosity and the 14–150 keV luminosity" (B Source sample) [from (cite: Ricci2023)]
- External data: Empirical M_BH - mm luminosity correlation compared with the model  
  > "We compare our correlation with the empirical one reported by (cite: Ruffa2024)." (3.4 M_BH-L_220GHz correlation modelling) [from (cite: Ruffa2024)]
- Simulation/model as data: One-zone spherical hybrid thermal plus non-thermal corona synchrotron model, plus phenomenological free-free, diffuse synchrotron and dust components  
  > "We developed a corona emission model based on the one-zone model presented by (cite: Inoue2019), in which the corona is a hybrid plasma with a thermal and a non-thermal particle population." (2.1 Corona emission)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Systematic error fraction f_sys = 5% for all observations, 10% for ALMA B6-8 (212-500 GHz), 20% for ALMA B9-10 (600-900 GHz)  
  > "The factor $f_\mathrm{sys}$ is fixed to 5% for all observations" (2.2 Parameter fitting); "except for ALMA observations at B6–8 (212–500 GHz) and B9–10 (600–900 GHz), for which it is 10% and 20%, respectively" (2.2 Parameter fitting)
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

- Non-thermal electron population definition and minimum Lorentz factor  
  > "Following (cite: Margalit2021), for the non-thermal population we define a minimum Lorentz factor" (2.1 Corona emission) [from (cite: Margalit2021)]
- Proton-to-electron energy ratio xi_e,p fixed to 40  
  > "we fix $\xi_\mathrm{e,p}=40$ (cite: Merten2017)" (2.1 Corona emission) [from (cite: Merten2017)]
- IC 4329A synchrotron index alpha_sy fixed to -0.59  
  > "we therefore fix $\alpha_\mathrm{sy}=-0.59$ as in (cite: Inoue2018)" (B.2 IC 4329A) [from (cite: Inoue2018)]
- GRS 1734-292 alpha_sy fixed to 0.75 and f-f component removed  
  > "we simply opt to remove the f–f component and to fix $\alpha_\mathrm{sy}=0.75$ as in (cite: Michiyama2024)" (B.1 GRS 1734-292) [from (cite: Michiyama2024)]
- NGC 985 kT_c = 29 keV and tau_T = 3.5  
  > "Following (cite: Inoue2018), we also fix $kT_\mathrm{c}=29$ keV and $\tau_\mathrm{T}=3.5$." (B.5 NGC 985) [from (cite: Inoue2018)]
- Dust contribution assumed not significant at mm wavelengths for MCG-06-30-15  
  > "Following (cite: Kawamuro2022), we assume that the dust contribution is not significant at mm wavelengths" (B.3 MCG-06-30-15) [from (cite: Kawamuro2022)]
- NGC 1068 fluxes reproduced from the earlier SED paper  
  > "For completeness, we reproduce the fluxes from their work in Table" (B.6 NGC 1068) [from (cite: Mutie2025)]

### Not stated but needed to reproduce (our reading)

- Which ALMA project and which execution blocks or spectral windows feed each ALMA flux point in Tables 1-7 (project codes are only listed in the acknowledgements)
- CASA or pipeline version, calibration and imaging settings (robust, tapering, uv range, cell and image size) for the ALMA flux extraction
- The Gaussian-fit region, fitting setup and error treatment used in CARTA for each archival image
- VLA, VLASS, NVSS and RACS project or epoch identifiers and exact cutout parameters
- bilby/emcee settings: number of walkers, steps, burn-in, convergence criteria, exact prior shapes, and the likelihood treatment of upper and lower limits
- Numeric value of the arbitrarily low fixed dust normalisation for MCG-06-30-15 and the fixed or fitted values of A_ff, A_sy, A_d per source
- Whether the coronal fits were run per band or on merged spectral windows (frequency points appear to be binned) and how the sub-band flux values were produced
- Source coordinates and the exact extraction apertures for each source

## Analysis recipe

1. **Compile SED flux densities and classify as fit points, upper limits or lower limits**: Published and archival flux densities collected; low-resolution points treated as upper limits and much higher resolution points as lower limits with a 1-sigma margin; archival image fluxes measured with a Gaussian fit in CARTA; systematic errors added in quadrature  
  > "For all sources, we do a detailed bibliographic search for published flux densities" (3.3 Analysis of the sample sources); "We used CARTA" (B Source sample); "we consider them only as strict lower limits (LLs) of the total flux density" (2.2 Parameter fitting)
   - software: CARTA
   - parameter: S_UL = S + dS and S_LL = S - dS  
  > "for a measured flux of $S_\nu \pm \Delta S_\nu$, we choose $S_\mathrm{UL} = S_\nu + \Delta S_\nu$ and $S_\mathrm{LL} = S_\nu - \Delta S_\nu$" (2.2 Parameter fitting)
   - parameter: f_sys = 5% (10% ALMA B6-8, 20% ALMA B9-10)  
  > "The factor $f_\mathrm{sys}$ is fixed to 5% for all observations" (2.2 Parameter fitting)
   - assumption: Coronal emission is point-like and the other galactic components are extended and inhomogeneous, so flux cannot be scaled with beam size  
  > "The corona is extremely compact, so its emission should be point-like in all observations." (2.2 Parameter fitting)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit the multi-component SED with the corona model**: Total SED = corona + free-free + diffuse synchrotron + dust, fitted with Bilby using the emcee MCMC sampler; fits done in log for quantities spanning orders of magnitude; epsilon_B tied to delta and T_c tied to tau_T when no X-ray determination  
  > "for fitting the SED using the standard sampler for Markov Chain Monte Carlo" (2.2 Parameter fitting); "We note that for quantities that can span several orders of magnitude, we fit the logarithm of the quantity." (2.2 Parameter fitting)
   - software: Bilby, emcee, astropy, Margalit & Quataert thermal-synchrotron code, sed_fitter_BHcorona
   - parameter: Fixed per source: M_BH, and often tau_T, kT_c, p, alpha_sy, beta, nu_tau1 (e.g. beta = 1.78, nu_tau1 = 800 GHz for GRS 1734-292)  
  > "so we fix $\beta=1.78$ and $\nu_{\tau_1}=800$ GHz" (B.1 GRS 1734-292)
   - parameter: Free parameters mainly r_c and log delta; parameter ranges listed in the Table of model parameters  
  > "We summarise all the model parameters and the range of values that they can take in Table" (2.2 Parameter fitting)
   - assumption: eta = 1 (equipartition between non-thermal particles and magnetic field), xi_e,p = 40, so epsilon_B = 41 delta  
  > "We additionally fix $\eta=1$, corresponding to an energy equipartition condition between non-thermal particles and magnetic fields." (2.1 Corona emission); "In this way, we remove a free parameter by the condition $\epsilon_B = 41 \, \delta$." (2.1 Corona emission)
   - assumption: Corona treated as a spherical one-zone region, components independent and summed; f-f absorption, AME and dust absorption of the corona neglected  
  > "We assume that these components are independent of each other and that the total emission is simply the sum of all components." (2 Emission model); "We thus neglect this effect in our model fitting." (2 Emission model)
   - assumption: Luminosity distance from Planck18 cosmology in astropy  
  > "to convert $z$ to a luminosity distance" (2.1 Corona emission)
   - fitting: Bilby with emcee MCMC; errors are 16th-84th percentile of the posterior; priors given in the parameter table (ranges); likelihood form not stated  
  > "the quoted errorbars correspond to the 16th–84th percentile range" (2.2 Parameter fitting)
   - validation: Sizes checked against an analytic estimate of Shablovinskaya et al. 2024, and results checked against Inoue & Doi 2018 with the same fixed parameters  
  > "we verified that the sizes derived with this approach agree well with the simple analytical estimate from Eq. 4 in (cite: Shablovinskaya2024)" (2.2 Parameter fitting); "we confirmed that our results are consistent with those reported by (cite: Inoue2018) when fixing the same parameters as in their work" (2.2 Parameter fitting)
3. **Derive magnetic field, sigma, peak properties and predicted X-ray luminosities**: From the fitted r_c and delta, compute B, sigma, nu_p, S_p, L_c; predict 14-150 keV luminosity by inserting the model 100-GHz luminosity into the Ricci et al. 2023 correlation (Kawamuro et al. 2022 for NGC 1068)  
  > "into the correlation from (cite: Ricci2023) between the 100-GHz luminosity and the 14–150 keV luminosity" (B Source sample); "we estimate the hard X-ray luminosity using the relation from (cite: Kawamuro2022)" (B.6 NGC 1068)
   - assumption: The total 100-GHz luminosity is used, not only the coronal part, to stay consistent with the Ricci et al. correlation  
  > "we prefer to keep consistency with how the correlations in (cite: Ricci2023) were derived, in which the total emission at 100 GHz was used" (B Source sample)
   - fitting: _not stated_
   - validation: _not stated_
4. **Explore parameter dependence of the corona SED**: Vary one parameter at a time around a reference case, then with tied parameters, then vary M_BH and redshift (mu = 10)  
  > "First, we vary one parameter at a time." (3.1 Parameter exploration)
   - parameter: Reference case: D = 100 Mpc, M_BH = 1e8 Msun, tau_T = 0.25, kT_c = 166 keV, r_c = 140, epsilon_B = 1.0, delta = 0.01, p = 2.7  
  > "$D = 100$ Mpc, $M_\mathrm{BH} = 10^8$ M$_\odot$, $\tau_\mathrm{T}=0.25$, $kT_\mathrm{c}=166$ keV, $r_\mathrm{c}=140$, $\epsilon_B=1.0$, $\delta=0.01$, and $p=2.7$" (3.1 Parameter exploration)
   - fitting: _not stated_
   - validation: _not stated_
5. **Model the M_BH versus 220 GHz luminosity correlation**: Compute model coronal emission at rest-frame 220 GHz over a range of M_BH and overlay on the empirical correlation of Ruffa et al. 2024, varying delta and r_c  
  > "we can use our corona emission model to calculate the corona emission at a rest-frame frequency of 220 GHz" (3.4 M_BH-L_220GHz correlation modelling)
   - fitting: _not stated_
   - validation: Qualitative comparison with the spread of the observed correlation  
  > "we can broadly explain the spread on the observed correlation when taking into account the parameter space available in $\delta$ and $r_\mathrm{c}$" (3.4 M_BH-L_220GHz correlation modelling)

## Software

- **Bilby** : SED fitting framework  
  > "for fitting the SED using the standard sampler for Markov Chain Monte Carlo" (2.2 Parameter fitting)
- **emcee** : MCMC sampler used within Bilby  
  > "for fitting the SED using the standard sampler for Markov Chain Monte Carlo" (2.2 Parameter fitting)
- **astropy (Planck18)** : Converting redshift to luminosity distance  
  > "to convert $z$ to a luminosity distance" (2.1 Corona emission)
- **CARTA** : Measuring flux densities by fitting a Gaussian profile  
  > "to obtain the flux density fitting a Gaussian profile" (B Source sample)
- **Margalit & Quataert thermal-synchrotron code** : Computing the synchrotron SED of the hybrid plasma corona  
  > "We therefore use the numerical code from (cite: Margalit2021)" (2.1 Corona emission)
- **sed_fitter_BHcorona** : Authors' code computing the total SED and fitting it  
  > "that calculates the total SED from the physical coronal model, together with the phenomenological components" (2.2 Parameter fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| GRS 1734-292 corona radius r_c | 112 | +/-14 | R_g | 2 | We obtain $r_\mathrm{c}=112 \pm 14$ ($R_\mathrm{c}\approx0.5$ ld) |
| GRS 1734-292 log delta | -1.74 | +/-0.13 | dimensionless | 2 | $\log{\delta}=-1.74 \pm 0.13$ |
| GRS 1734-292 corona peak frequency | 130 | +/-14 | GHz | 3 | the corona peaks at $\nu_\mathrm{p} = 130 \pm 14$ GHz with a peak flux density of $S_\mathrm{p} = 0.91 \pm 0.11$ mJy |
| GRS 1734-292 corona peak flux density | 0.91 | +/-0.11 | mJy | 3 | $S_\mathrm{p} = 0.91 \pm 0.11$ mJy |
| GRS 1734-292 r_c in the higher-flux epoch (delta fixed) | 178 | +/-9 | R_g | 2 | the fit yields $r_\mathrm{c}=178 \pm 9$ |
| IC 4329A corona radius r_c | 261 | +141/-45 | R_g | 2 | We obtain $r_\mathrm{c}=261^{+141}_{-45}$ and $\log{\delta}=-2.25^{+0.24}_{-0.48}$ |
| IC 4329A log delta | -2.25 | +0.24/-0.48 | dimensionless | 2 | $\log{\delta}=-2.25^{+0.24}_{-0.48}$ |
| IC 4329A corona peak frequency | 90 | +/-20 | GHz | 3 | The corona component peaks at $\nu_\mathrm{p} = 90\pm20$ GHz, with a peak flux density of $S_\mathrm{p} = 4.2\pm1.1$ mJy |
| MCG-06-30-15 corona radius r_c | 115 | +/-6 | R_g | 2 | We obtain $r_\mathrm{c}=115\pm6$ ($R_\mathrm{c}\approx 0.13$ ld) and $\log{\delta}=-1.98 \pm 0.06$ |
| MCG-06-30-15 log delta | -1.98 | +/-0.06 | dimensionless | 2 | $\log{\delta}=-1.98 \pm 0.06$ |
| MCG-06-30-15 corona peak frequency | 133 | +/-6 | GHz | 3 | The corona component peaks at $\nu_\mathrm{p} = 133\pm6$ GHz, with a peak flux density of $S_\mathrm{p} = 0.64\pm0.06$ mJy |
| NGC 985 corona radius r_c | 111 | +33/-14 | R_g | 2 | $r_\mathrm{c}=111^{+33}_{-14}$ ($R_\mathrm{c}\approx 1.4$ ld) and $\log{\delta}=-2.03^{+0.13}_{-0.22}$ |
| NGC 985 log delta | -2.03 | +0.13/-0.22 | dimensionless | 2 | $\log{\delta}=-2.03^{+0.13}_{-0.22}$ |
| NGC 985 corona peak frequency | 100 | +/-15 | GHz | 3 | The corona SED component peaks at $\nu_\mathrm{p} = 100\pm15$ GHz, with a peak flux density of $S_\mathrm{p} = 1.4\pm0.2$ mJy |
| NGC 1068 corona radius r_c | 67.5 | +/-5.5 | R_g | 2 | We obtain $r_\mathrm{c}=67.5 \pm 5.5$ ($R_\mathrm{c}\approx 0.065$ ld) and $\log{\delta}=-0.98 \pm 0.13$ |
| NGC 1068 log delta | -0.98 | +/-0.13 | dimensionless | 2 | $\log{\delta}=-0.98 \pm 0.13$ |
| NGC 1068 corona peak frequency | 568 | +/-55 | GHz | 3 | The corona SED peaks at $\nu_\mathrm{p} \simeq 568 \pm 55$ GHz, with a peak flux density of $S_\mathrm{p} = 10.1\pm1.9$ mJy |
| NGC 3227 corona radius r_c | 67 | +48/-26 | R_g | 2 | $r_\mathrm{c}=67^{+48}_{-26}$ ($R_\mathrm{c}\approx 0.06$ ld) and $\log{\delta}=-2.07^{+0.56}_{-0.48}$ |
| NGC 3227 log delta | -2.07 | +0.56/-0.48 | dimensionless | 2 | $\log{\delta}=-2.07^{+0.56}_{-0.48}$ |
| NGC 3227 corona peak frequency | 233 | +/-91 | GHz | 3 | The corona SED component peak is very poorly constrained at $\nu_\mathrm{p} = 233 \pm 91$ GHz, with a peak flux density of $S_\mathrm{p} = 0.94\pm0.48$ mJy |
| Sample median corona radius r_c | 133 | not stated | R_g | 2 | with median values of $r_\mathrm{c} \approx 133$ and $\log{\delta} \approx -1.86$ ($\delta \approx 1.4$%) |
| Sample median log delta | -1.86 (delta ~ 1.4%) | not stated | dimensionless | 2 | $\log{\delta} \approx -1.86$ ($\delta \approx 1.4$%) |
| Corona magnetic field range and median | 10-150 G, median ~20 G | not stated | G | 3 | The derived values of $B$ range between 10–150 G, with a median of $\approx$20 G. |
| sigma parameter range | 0.01-1, mean <~0.1 | not stated | dimensionless | 3 | values of $\sigma$ ranging between 0.01–1, with a mean value of $\lesssim$0.1 |
| Predicted dependence of corona peak frequency on black hole mass | nu_p proportional to M_BH^-0.37 | not stated | dimensionless | 4 | $\nu_\mathrm{p} \propto M_\mathrm{BH}^{-0.37}$ |
| Luminosity at which the M_BH-L_220 correlation changes slope | ~1e39 | not stated | erg s^-1 | 5 | a slope change in the correlation at $\nu L_\nu \sim 10^{39}$ erg s$^{-1}$ |

## Qualitative findings

- Thermal electrons alone cannot explain the mm emission for kT_c below 200 keV; non-thermal electrons dominate for kT_c < 300 keV  
  > "The non-thermal electrons completely dominate the emission for $k T_\mathrm{c} < 300$ keV." (Appendix A)
- The sizes inferred from the mm observations are consistently larger than those from X-ray observations  
  > "we note that the sizes inferred from the mm observations are consistently larger than the ones inferred from X-ray observations" (4 Discussion)
- Lensed high-z sources at z>1 are too faint for ALMA but are SKA-Mid candidates  
  > "thus making their observation unfeasible for ALMA" (3.2 Studying sources at high redshift)

## Claim tuples

- H: Do the mm SEDs of SMBH coronae require a hybrid thermal plus non-thermal plasma, and what sizes and non-thermal fractions result? | E: Fit a one-zone hybrid corona plus galactic components to the radio-to-FIR SEDs of six radio-quiet AGN with Bilby/emcee | R: r_c ~ 60-250, delta ~ 10^-3 to 10^-1 (median ~1.4%), B 10-150 G | F: mm emission is consistent with non-thermal energy density ~0.5-10% of the thermal plasma, near-equipartition magnetic fields and coronae of 60-250 R_g | **supported**
- H: Can the model reproduce the observed M_BH versus mm luminosity correlation? | E: Compute 220-GHz coronal luminosity over a range of M_BH for ranges of delta and r_c and compare with Ruffa et al. 2024 | R: The spread of the observed correlation is broadly explained, with a predicted slope change near 1e39 erg/s | F: A physical connection underlying the correlation is supported but needs larger samples | **partially**
- H: Is the corona peak frequency anticorrelated with M_BH? | E: Plot fitted nu_p versus M_BH for the sample sources | R: A hint of anticorrelation with a very small sample | F: Consistent with the model prediction but not firmly established | **partially**
- H: Can coronal emission of lensed high-z quasars be detected? | E: Compute corona SEDs for M_BH = 1e9 Msun and mu = 10 at different redshifts | R: For z>1 the peak is below 40 GHz and flux density below 0.1 mJy | F: Not feasible for ALMA but SKA-Mid could detect such sources up to z ~ 4 in ~1 h | **supported**
- H: Could thermal electrons alone produce the mm synchrotron emission? | E: Compute SEDs for kT_c from 200 to 400 keV with and without a small non-thermal fraction | R: Thermal synchrotron is faint and non-thermal electrons dominate below 300 keV | F: Scenarios with kT_c < 200 keV and delta > 1e-3 are far more promising | **supported**

## Reasoning

- Why this data: Sample includes all sources with reported strong indications of coronal activity plus two with high-resolution radio-cm to sub-mm data  
  > "that includes all sources for which strong indications of coronal activity have been reported in the literature" (3.3 Analysis of the sample sources)
- Why this method: Beam-matched data are used because the compact corona is point-like while other components are extended  
  > "For this reason, we use beam-matched data whenever possible, even if that requires compromising angular resolution." (2.2 Parameter fitting)
- Alternative: No anomalous microwave emission component included  
  > "For this reason, we do not include an AME emission component in our model." (2 Emission model)
- Alternative: Free-free absorption of the diffuse synchrotron not modelled to avoid extra free parameters  
  > "We refrain from including such effects in our model as it would introduce additional free parameters that do not assist us in our main goal" (2 Emission model)
- Alternative: Fitting p for MCG-06-30-15 hits the prior limit so p is fixed to 2.1  
  > "trying to fit the spectral index $p$ leads to a solution that hits the hard limit on the priors, and we thus fix $p=2.1$" (B.3 MCG-06-30-15)
- How they decided it was enough: _not stated_
- Limitation (authors): Datasets are non-simultaneous over several years  
  > "As such, the datasets are non-simultaneous, with typical timespans of several years." (B Source sample)
- Limitation (authors): One-zone homogeneous corona is most likely an oversimplification  
  > "Even though the assumption of a homogeneous emitter is most likely an oversimplification" (4 Discussion)
- Limitation (authors): MCG+08-11-11 corona SED poorly constrained so no robust fit  
  > "The corona SED is, unfortunately, very poorly constrained, and a robust fit cannot be addressed at this stage" (B.4 MCG+08-11-11)
- Limitation (authors): NGC 3227 corona properties only loosely constrained  
  > "the properties of the corona are only loosely constrained" (B.7 NGC 3227)
- Caveat (inferred, ours): Fluxes mix beam sizes and epochs, and UL/LL classification by resolution is a judgement that affects the fits
- Caveat (inferred, ours): Many parameters (p, alpha_sy, tau_T, kT_c, beta, nu_tau1, mass) are fixed per source, so uncertainties on r_c and delta are conditional on these choices
- Caveat (inferred, ours): Sample is only six fitted sources, so population statements (median r_c, delta, M_BH correlation) are weak
- Caveat (inferred, ours): ALMA flux extraction (CARTA Gaussian fits) is not documented, so ALMA systematics beyond the nominal f_sys are unknown

## Reproducibility

- Data public (paper): Combination of archival and proprietary observations; ALMA project codes listed in the acknowledgements  
  > "The fluxes reported in this work are a combination of archival and proprietary observations." (B Source sample)
- Products in archive: _not stated_
- Code: https://github.com/santimda/sed_fitter_BHcorona  
  > "https://github.com/santimda/sed_fitter_BHcorona" (Footnote 4)
- Missing: Mapping of ALMA projects to individual flux points and the reduction or image-based flux extraction settings
- Missing: emcee/bilby run configuration and likelihood treatment of limits
- Missing: Dust normalisation and other nuisance-parameter values fixed per source
- Missing: Coordinates and extraction regions for archival VLA/VLASS/RACS/ALMA photometry
- Data volume (inferred): Fit inputs (flux tables) are tiny; re-extracting the ALMA fluxes from six projects would need tens to hundreds of GB of archive products
- Score (inferred): 3/5, Fit code is public and flux tables with fit/limit flags are printed with posteriors, but the ALMA flux extraction, sampler settings and several fixed nuisance values are not given and some data are proprietary
- Rediscovery candidate: no, Fitted results are numeric and code is public, but ALMA flux extraction is undocumented and part of the data are proprietary or from literature

## Links

- Method: (cite: Margalit2021) (Numerical code for synchrotron SED of a hybrid thermal plus non-thermal plasma)
- Method: (cite: Inoue2019) (One-zone hybrid corona model on which the model is based)
- Companion: (cite: Shablovinskaya2024) (Earlier use of the same code on IC 4329A)
- Companion: (cite: Mutie2025) (Earlier use of the same code and matched-resolution SED of NGC 1068)
- Companion: (cite: Ruffa2024) (Empirical M_BH versus mm flux correlation compared with the model)
- Related: VLASS
- Related: NVSS
- Related: RACS
- Related: LoTSS
- Related: CIRADA cutout service

## Checks

```json
{
 "quotes": 119,
 "quotes_ok": 119,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 26,
 "numeric_problems": 0,
 "fill": {
  "facts": 122,
  "stated": 70,
  "rate": 0.574
 },
 "evidence_ok": true
}
```
