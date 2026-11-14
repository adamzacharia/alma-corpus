# ALMA Observations of the Protostar L1527 IRS: Probing Details of the Disk and the Envelope Structures

`2017ApJ...849...56A` | The Astrophysical Journal 2017 | first author: Aso, Yusuke | arXiv: 1707.08697 | DOI: 10.3847/1538-4357/aa8264

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Can the disk and envelope around the protostar L1527 IRS be distinguished kinematically and geometrically, and what are their structures?  
  > "The question of whether disks and envelopes in protostellar systems can be distinguished from each other by detailed observations of protostellar disks is therefore critical." (INTRODUCTION)
- Target **L1527 IRS**: coordinates RA(J2000)=04h39m53.90s, Dec=+26d03m10.0s (map center)  
  > "L1527 IRS, located in one of the closest star-forming regions, the Taurus Molecular Cloud ($d=140$ pc)" (INTRODUCTION); "The coordinates of the map center during the observations were $\alpha {\rm (J2000)}=04^{\rm h}39^{\rm m}53.90s,\ \delta {\rm (J2000)}=26^{\circ}03\ensuremath{'} 10.00\ensuremath{''}$." (2 ALMA OBSERVATIONS AND DATA REDUCTION); z/distance 140 pc  
  > "L1527 IRS, located in one of the closest star-forming regions, the Taurus Molecular Cloud ($d=140$ pc)" (INTRODUCTION); "The coordinates of the map center during the observations were $\alpha {\rm (J2000)}=04^{\rm h}39^{\rm m}53.90s,\ \delta {\rm (J2000)}=26^{\circ}03\ensuremath{'} 10.00\ensuremath{''}$." (2 ALMA OBSERVATIONS AND DATA REDUCTION); distance from Taurus Molecular Cloud distance, adopted  
  > "L1527 IRS, located in one of the closest star-forming regions, the Taurus Molecular Cloud ($d=140$ pc)" (INTRODUCTION); "The coordinates of the map center during the observations were $\alpha {\rm (J2000)}=04^{\rm h}39^{\rm m}53.90s,\ \delta {\rm (J2000)}=26^{\circ}03\ensuremath{'} 10.00\ensuremath{''}$." (2 ALMA OBSERVATIONS AND DATA REDUCTION)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (220 GHz)  
  > "C$^{18}$O $J=2-1$ line and 220 GHz continuum emission in Band 6 were observed" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: Frequency Division Mode, two spectral windows, 3840 channels each, 234 MHz bandwidth  
  > "we configured the correlator in Frequency Division Mode for two spectral windows. Each spectral window has 3840 channels covering 234 MHz bandwidth." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: ~234 MHz  
  > "The total bandwidth of the continuum map is $\sim234$ MHz." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- arrays: 34 antennas in first track, one flagged in second  
  > "Thirty-four antennas were used in the first track, while one antenna was flagged in the latter track." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- configurations: _not stated_
- baselines: 17-648 m (13-474 kλ)  
  > "The antenna configuration covers projected baseline length from 17 to 648 m (13-474 k$\lambda$ in $uv$-distance at the frequency of C$^{18}$O $J=2-1$)." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- angular resolution: 0.50''x0.40'' (C18O), 0.47''x0.37'' (continuum)  
  > "The synthesized beam sizes of the CLEANed maps are $0.50\ensuremath{''}\times 0.40\ensuremath{''}$ for the C$^{18}$O line, and $0.47\ensuremath{''}\times 0.37\ensuremath{''}$ for the continuum emission." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- max recoverable scale: 7.1'' (>50% flux resolved out beyond this), ~990 AU  
  > "This minimum baseline resolves out more than 50% of the flux when a structure is extended more than $7.1\ensuremath{''}$" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- sensitivity: 1 sigma 0.2 mJy/beam (continuum), 2.6 mJy/beam (C18O)  
  > "| 1$\sigma$                 | 0.2 ${\rm mJy~beam^{-1}}$                                        | 2.6 ${\rm mJy~beam^{-1}}$" (Table 1)
- time on source: 6.9+6.7 = 14 minutes  
  > "were observed for 6.9$+$6.7$=$14 minutes (on source)" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- observing dates: 2014 July 20, two tracks  
  > "We observed our target, L1527 IRS, during Cycle 1 using ALMA on 2014 July 20." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: Project 2012.1.00647.S (P.I. N. Ohashi)  
  > "ADS/JAO.ALMA2012.1.00647.S (P.I. N. Ohashi)" (Acknowledgments)
- Line: C18O J=2-1 (219.560358 GHz)
- External data: Dust opacity kappa(220 GHz)=0.031 cm^2/g (from kappa(850um)=0.035, beta=0.25), dust temperature 30 K for mass estimate  
  > "by assuming a dust opacity of $\kappa(220\ {\rm GHz})=0.031\ {\rm cm}^{2}\,{\rm g}^{-1}$ (cite: to2013), a dust temperature of 30 K (cite: to2013)" (3.1 220 GHz Continuum) [from (cite: to2013)]
- External data: Inclination 85 deg and eastern side near  
  > "The inclination angle of the dust disk/envelope is fixed at $i=85^{\circ}$ and the eastern side is on the near side for the observers (cite: oy2015)." (4.2.2 Model fitting) [from (cite: to2008), (cite: to2013), (cite: oy2015)]
- External data: Distance 140 pc, Lbol=2.0 Lsun, Tbol=44 K  
  > "has bolometric luminosity $L_{\rm bol}=2.0\ L_{\odot}$ and bolometric temperature $T_{\rm bol}=44$ K (cite: kr2012)" (INTRODUCTION) [from (cite: kr2012)]
- External data: ISM C18O abundance 5.0e-7  
  > "the value in interstellar medium (ISM), $5.0\times 10^{-7}$ (cite: la1994; jo2005; wi.ro1994)" (5.2 Structures of the C18O gas disk) [from (cite: la1994; jo2005; wi.ro1994)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013, J0510+1800  
  > "| Flux calibrator           | J0423$-$013, J0510$+$1800" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on continuum with clean, gaincal, applycal; table applied to C18O  
  > "We performed self-calibration for the continuum observations using tasks ($clean$, $gaincal$, and $applycal$) in Common Astronomy Software Applications (CASA)" (2 ALMA OBSERVATIONS AND DATA REDUCTION)

### Imaging

- task: CASA fixvis to shift phase center, then Fourier transform and CLEAN  
  > "the phase center of the observed visibilities was shifted from the original phase center with $fixvis$ in CASA" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- deconvolver: _not stated_
- weighting robust: superuniform weighting with npixel=2  
  > "we adopted superuniform weighting with $npixel=2$ and binned two frequency channels" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 12''x12'' CLEAN box centered on map center, threshold 3 sigma  
  > "We set a $12\ensuremath{''} \times 12\ensuremath{''}$ area centered on the map center as a CLEAN box with a threshold of $3\sigma$." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- multiscale scales: _not stated_
- continuum subtraction: Emission-free channels in lower sideband used for continuum map  
  > "Emission-free channels in the lower side band are used to make the continuum map centered at 220 GHz." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Two channels binned; 122 kHz = 0.17 km/s  
  > "the resultant frequency resolution in this paper is 122 kHz, corresponding to 0.17 ${\rm km~s^{-1}}$" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- final beam: 0.50''x0.40'' (P.A. 3.1 deg) C18O; 0.47''x0.37'' (P.A. -0.4 deg) continuum  
  > "| Synthesized beam (P.A.)   | $0.47\ensuremath{''} \times 0.37\ensuremath{''}\ (-0.4^{\circ})$ | $0.50\ensuremath{''}\times 0.40\ensuremath{''}\ (3.1^{\circ})$" (Table 1)
- final rms: 0.2 mJy/beam continuum; 2.6 mJy/beam C18O  
  > "| 1$\sigma$                 | 0.2 ${\rm mJy~beam^{-1}}$                                        | 2.6 ${\rm mJy~beam^{-1}}$" (Table 1)

### Inherited from earlier work

- Rotation-profile measurement method (intensity-weighted mean position in PV diagram, double power-law fit)  
  > "The method used in this section to obtain the radial profile of rotational velocity is based on the analyses presented by (cite: ye2013) and also explained by (cite: aso2015) in detail." (4.1 Rotation Profile) [from (cite: ye2013); (cite: aso2015)]
- Visibility model code  
  > "We used the code described in (cite: oh2014)." (4.2.2 Model fitting) [from (cite: oh2014)]
- Correction factor 0.760 for underestimated Keplerian radius due to low minor-axis resolution  
  > "In their notation, the correction factor is a constant, 0.760, when Keplerian disk radius $R_{o}$ is smaller than $\lesssim 480$ AU" (4.1 Rotation Profile) [from (cite: aso2015)]
- Disk model basis and fixed temperature profile  
  > "the model we use in this section is based on a standard disk model (cite: du1994) but modified to express a flattened dust envelope as well as a dust disk" (4.2.2 Model fitting) [from (cite: du1994); (cite: to2013)]

### Not stated but needed to reproduce (our reading)

- Exact self-calibration solution intervals, number of iterations and reference antenna
- Calibration pipeline/manual choice and CASA version
- Line-free channels used for continuum and continuum subtraction method
- Image cell size and image size, number of clean iterations
- MCMC settings (sampler, priors, chain length)
- Details of the radiative transfer code used to produce model images
- Flux density scale uncertainty
- How PV cut width and positional errors were set
- Exact definition of uv averaging and the 1089 visibility points

## Analysis recipe

1. **Measure continuum size and flux**: 2D Gaussian fit to the continuum image  
  > "Its deconvolved size derived from a 2D Gaussian fitting is $531\pm 2\ {\rm mas}\times 150\pm2\ {\rm mas},\ {\rm P.A.}=1.5^{\circ}\pm 0.2^{\circ}$." (3.1 220 GHz Continuum)
   - software: CASA
   - assumption: Optically thin, isothermal 30 K dust, kappa(220 GHz)=0.031 cm2/g, g/d=100  
  > "By assuming that the dust continuum emission is optically thin and dust temperature is isothermal, total mass can be calculated with the total flux density (cite: an2005)." (3.1 220 GHz Continuum)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive rotation profile and Keplerian mass/radius**: Intensity-weighted mean positions per channel from major-axis PV diagram, fit with double power law in log R-log V  
  > "The data points in the $\log R-\log V$ plane are, therefore, fitted by a double power-law function with four free parameters" (4.1 Rotation Profile)
   - parameter: Pixels above 5 sigma used; V_LSR=5.8 km/s; distance 140 pc; i=85 deg  
  > "Pixels having intensity more than $5\sigma$ are used to calculate the sum." (4.1 Rotation Profile)
   - assumption: Distance 140 pc; inclination 85 deg  
  > "by assuming that the distance of L1527 IRS is 140 pc" (4.1 Rotation Profile)
   - fitting: chi2 fit of double power law (Rb,Vb,pin,pout); compared with single power law  
  > "For comparison, $\chi ^{2}$ fitting with a single power function is also performed, where $V_{b}$ is fixed at $2.31\ {\rm km~s^{-1}}$." (4.1 Rotation Profile)
   - validation: Reduced chi2 1.6 (double) vs 4.0 (single); systemic velocity left free confirms 5.8 km/s  
  > "giving a reasonable reduced $\chi ^{2}$ of 1.6." (4.1 Rotation Profile)
3. **Fit continuum visibilities with disk+envelope model**: chi2 fitting of non-azimuthally-averaged visibilities with a 12-parameter model (6 free), synthetic visibilities via simobserve and listvis  
  > "After a model image was calculated from the radiative transfer, model visibility was obtained by synthetic observations through the CASA tasks $simobserve$ and $listvis$." (4.2.2 Model fitting)
   - software: CASA, simobserve, listvis
   - parameter: Free: Mdisk, Rout, p, Sdamp, H1, h; fixed: i=85 deg, Rin=0.1 AU, T1=403.5 K, q=0.5, kappa=0.031, g/d=100; outer radius 1000 AU  
  > "| Fixed | $i$ | $R_{in}$ | $T_{1}$ | $q$ | $\kappa (220\ {\rm GHz})$ | g/d |" (Table 2)
   - assumption: LTE, vertically isothermal, same density power-law index for disk and envelope  
  > "Our model adopts the same power-law index of density for both disk and envelope" (4.2.2 Model fitting)
   - fitting: Reduced chi2 minimization using 1089 visibility points; uncertainties from range where chi2 < min+1; MCMC used to find minimum  
  > "We also used the Markov Chain Monte Carlo method to find the minimum $\chi ^{2}$ efficiently." (4.2.2 Model fitting)
   - validation: Best-fit reduced chi2 5.6; image-space comparison and residuals; models with Sdamp=0 and 1 compared  
  > "The reduced $\chi ^{2}$ of the best-fit model is 5.6, which corresponds to a residual of $\sim 2.4\sigma$ on average in the $uv$-space." (4.2.2 Model fitting)
4. **Test hydrostatic equilibrium and origin of density jump**: Compare model scale height at Rout with HSEQ value; isothermal shock condition Sdamp = cs^2/ur^2  
  > "the isothermal shock condition is $S_{\rm damp}=\rho _{\rm env}/\rho _{\rm disk}=c_{s}^{2}/u_{r}^{2}$" (5.1 Possible Origin of the Surface Density Jump)
   - assumption: M*=0.45 Msun, T=44 K, mean molecular weight 2.37 mH; infall velocity = alpha times free fall  
  > "a mean molecular weight is $2.37\ m_{\rm H}$" (4.2.2 Model fitting)
   - fitting: _not stated_
   - validation: Envelope density compared with Kenyon et al. 1993 and Tobin et al. 2013  
  > "This indicates that the envelope density in the best-fit model is also reasonable when compared with other observations." (5.1 Possible Origin of the Surface Density Jump)
5. **Model C18O moment 0 map**: 3D radiative transfer C18O cubes using the dust best-fit structure plus observed rotation and infall, convolved with beam, compared in moment 0 within 1'' and |V|>2.0 km/s  
  > "comparisons between C$^{18}$O models and observations should be made only within a radius of $1\ensuremath{''}$." (5.2 Structures of the C18O gas disk)
   - parameter: Constant abundance 4e-8 nominal; alternative ISM abundance 5e-7 at 80-88 AU and 2.8e-8 elsewhere  
  > "the ISM abundance (cite: la1994; jo2005; wi.ro1994) at 80$\leq R\leq$88 AU and a lower constant abundance of $2.8\times 10^{-8}$ elsewhere" (5.2 Structures of the C18O gas disk)
   - assumption: Gas and dust well coupled; rotation break at 74 AU, density jump at 84 AU  
  > "we adopt 74 AU as the radius where the rotation profile has a break even though the geometrical boundary between the disk and the envelope is set at 84 AU in radius" (5.2 Structures of the C18O gas disk)
   - fitting: Manual comparison of abundance profiles; no formal fit  
  > "Note that neither a higher nor a lower constant value than $4.0\times 10^{-8}$ of the C$^{18}$O abundance improves the model." (Structures of the C$^{18}$O gas disk)
   - validation: Residual of moment 0 maps (9 sigma for constant abundance)  
  > "significant residuals at 9$\sigma$ level are left" (5.2 Structures of the C18O gas disk)

## Software

- **CASA** : Self-calibration, fixvis, imaging/CLEAN, simobserve and listvis synthetic observations  
  > "All the mapping process was carried out with CASA." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- **MIRIAD** : listed in Software section only; use not described  
  > "CASA, MIRIAD, IDL" (Software)
- **IDL** : listed in Software section only; use not described  
  > "CASA, MIRIAD, IDL" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum deconvolved size (major x minor) | 531 x 150 mas, P.A.=1.5 deg | ±2 mas, ±2 mas, ±0.2 deg | mas | 1 | $531\pm 2\ {\rm mas}\times 150\pm2\ {\rm mas},\ {\rm P.A.}=1.5^{\circ}\pm 0.2^{\circ}$ |
| Continuum total flux density (Gaussian) | 164.6 | 0.5 | mJy | 1 | $101.4\pm 0.2\ {\rm mJy~beam^{-1}}$ and $164.6\pm 0.5\ {\rm mJy}$ |
| Gas mass from continuum | ~0.013 | not stated | Msun | 1 | correspond to a mass of $M_{\rm gas}\sim 0.013\ M_{\ensuremath{\odot}}$ |
| Rotation double power-law inner index p_in | 0.50 | 0.05 | dimensionless | 2 | $(R_{b},V_{b},p_{\rm in},p_{\rm out})=(56\pm 2\ {\rm AU}, 2.31\pm 0.07\ {\rm km~s^{-1}},0.50\pm 0.05, 1.22\pm 0.04)$ |
| Rotation outer index p_out | 1.22 | 0.04 | dimensionless | 2 | $(R_{b},V_{b},p_{\rm in},p_{\rm out})=(56\pm 2\ {\rm AU}, 2.31\pm 0.07\ {\rm km~s^{-1}},0.50\pm 0.05, 1.22\pm 0.04)$ |
| Break radius / break velocity | 56 AU / 2.31 km/s | ±2 AU / ±0.07 km/s | AU; km/s | 2 | $(56\pm 2\ {\rm AU}, 2.31\pm 0.07\ {\rm km~s^{-1}} |
| Keplerian disk radius (corrected) | ~74 | not stated | AU | 2 | the Keplerian disk radius is estimated to be $\sim 74$ AU |
| Central protostellar mass | ~0.45 | not stated | Msun | 2 | $M_{*}\sim 0.45\ M_{\ensuremath{\odot}}$ |
| Model Rout | 84 | +16/-24 | AU | 3 | $84^{+16}_{-24}$ AU |
| Damping factor Sdamp | 0.19 | +0.03/-0.09 | dimensionless | 3 | The damping factor $S_{\rm damp}=0.19^{+0.03}_{-0.09}$ |
| Surface density power-law index p | 1.7 | +0.1/-0.3 | dimensionless | 3 | $p=1.7^{+0.1}_{-0.3}$ |
| Scale height index h | 1.2 | ±0.1 | dimensionless | 3 | $h=1.2^{+0.1}_{-0.1}$ |
| Disk mass | 1.3e-2 | +0.3/-0.4 e-2 | Msun | 3 | $1.3^{+0.3}_{-0.4}\times 10^{-2}\ M_{\ensuremath{\odot}}$ |
| Reduced chi2 of best-fit visibility model | 5.6 | not stated | dimensionless | 3 | The reduced $\chi ^{2}$ of the best-fit model is 5.6 |
| Model scale height at Rout vs HSEQ | ~20 vs ~15 | not stated | AU | 4 | The scale height of the best-fit model at $R=R_{\rm out}$ is calculated to be $\sim 20$ AU while the scale height of a disk in HSEQ is estimated to be $\sim 15$ AU |
| Required infall coefficient alpha | ~0.3 | not stated | dimensionless | 4 | In order to explain $S_{\rm damp}=0.19$, $\alpha$ should be $\sim 0.3$ |

## Qualitative findings

- Keplerian rotation in inner region and angular-momentum-conserving rotation in outer envelope  
  > "The best-fit inner power-law index is almost equal to Keplerian rotation law ($p=1/2$)" (4.1 Rotation Profile)
- C18O observations reproduced by dust-derived structure with freeze-out and localized desorption  
  > "C$^{18}$O observations can be reproduced by the same geometrical structures derived from the dust observations, with possible C$^{18}$O freeze-out and localized C$^{18}$O desorption." (abstract)

## Claim tuples

- H: Disk and envelope can be kinematically distinguished | E: Double power-law fit to C18O PV rotation profile | R: p_in=0.50, p_out=1.22, break ~56 AU | F: Keplerian disk radius ~74 AU, M*~0.45 Msun | **supported**
- H: Disk and envelope can be geometrically distinguished by a density jump | E: chi2 fit of continuum visibilities without azimuthal averaging | R: Sdamp=0.19, Rout=84 AU | F: Density jump of ~5 at a radius consistent with the kinematic disk radius | **supported**
- H: The disk is in hydrostatic equilibrium | E: Compare fitted h and scale height at Rout with HSEQ | R: h=1.2 vs 1.25; H~20 AU vs ~15 AU | F: Disk is most probably in HSEQ | **supported**
- H: Density jump arises from accretion shock | E: Isothermal shock condition with infall velocity fraction alpha | R: alpha~0.3, consistent with 0.25-0.5 from Ohashi et al. 2014 | F: Mass accretion is a possible origin | **partially**
- H: Dust-derived structure also reproduces C18O emission | E: C18O radiative transfer models with different abundance profiles | R: Constant abundance leaves 9 sigma residual; locally enhanced profile with lower inner abundance reproduces | F: Requires freeze-out/conversion and local desorption | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Fit visibilities directly without azimuthal averaging to avoid imaging non-linear effects and preserve non-spherical structure  
  > "we have performed direct model fitting to the observed continuum visibility data, which is free from any non-linear effects associated with interferometric imaging." (4.2.1 Continuum Visibility distribution)
- Alternative: Single power-law rotation fit rejected (reduced chi2 4.0 vs 1.6); Gaussian and power-law visibility profiles rejected; opacity jump alternative judged small  
  > "These reduced $\chi^{2}$ suggest that the radial profile of rotational velocity is characterized by the double power function better than any single power function." (4.1 Rotation Profile)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution not high enough to resolve vertical structures; temperature profile fixed and vertically isothermal; abundance constraints weak  
  > "because our angular resolution is not high enough to resolve vertical structures of the disk, the radial temperature profile we adopted is vertically isothermal." (4.2.2 Model fitting)
- Caveat (inferred, ours): Best-fit reduced chi2 of 5.6 indicates imperfect fit; uncertainties from delta chi2=1 may be underestimated given this
- Caveat (inferred, ours): Temperature profile fixed, so degeneracies with density structure not explored
- Caveat (inferred, ours): Continuum subtraction artifacts affect C18O maps and PV
- Caveat (inferred, ours): Uncertainty on inferred density jump depends on fixed opacity and inclination
- Caveat (inferred, ours): C18O abundance profile is ad hoc

## Reproducibility

- Data public (paper): Project 2012.1.00647.S cited in acknowledgments (data use acknowledgment)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA2012.1.00647.S (P.I. N. Ohashi)." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Model code (from Ohashi et al. 2014) and radiative transfer code not specified
- Missing: Self-calibration parameters
- Missing: MCMC details
- Missing: Cell/image size and clean iterations
- Data volume (inferred): ~10-50 GB raw for one Band 6 FDM execution block pair
- Score (inferred): 3/5, Data are single ALMA project with clear imaging choices, but the visibility modeling code is inherited and several processing details are missing.
- Rediscovery candidate: no, Visibility model code is from earlier work and not specified, so full recipe cannot be redone from this paper alone.

## Links

- Method: Aso et al. 2015 (cite: aso2015) (Rotation profile method and correction factor)
- Method: Ohashi et al. 2014 (cite: oh2014) (Visibility model code and Cycle 0 analysis)
- Method: Yen et al. 2013 (cite: ye2013) (Rotation profile analysis)
- Companion: Ohashi et al. 2014 (cite: oh2014) (Cycle 0 ALMA observations of L1527 IRS)
- Companion: Tobin et al. 2013 (cite: to2013) (Source model, opacity, temperature)

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00647.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 61,
  "rate": 0.753
 },
 "evidence_ok": true
}
```
