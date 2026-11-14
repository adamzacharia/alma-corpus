---
name: alma-gas-mass-co-conversion
description: "Turn ALMA CO, [CI], 13CO or dust-continuum measurements into molecular gas masses, surface densities, gas fractions and depletion times, choosing the excitation correction (r_J1), conversion factor (alpha_CO / X_CO, X_CI, CO/H2 abundance) and helium convention the way published ALMA papers do. Use when converting a line flux to L' and M_H2, picking alpha_CO for a galaxy, nucleus, outflow or low-metallicity region, converting mid-J CO to CO(1-0), using [CI] or the Rayleigh-Jeans dust continuum as a gas tracer, stating gas-mass limits for non-detections, or checking someone else's gas mass. Built from 360 ALMA papers (2012-2026)."
---

# Molecular gas masses from CO, [CI] or dust

Converts a line (or continuum) measurement into H2 or total molecular mass:
M_mol = alpha x L'_CO(1-0), with L'_CO(1-0) = L'_CO(J-J-1) / r_J1. Two assumed numbers carry nearly all
of the uncertainty: the conversion factor (alpha_CO, X_CO, X_CI or CO/H2) and, for J>1, the excitation ratio
r_J1. The mistakes that matter most: (1) mixing conventions (alpha_CO with or without helium, alpha_CO for
CO(1-0) applied to CO(2-1), a flux-density ratio used where a brightness-temperature ratio is needed), each a
factor 1.36 to 9 error; (2) using a Galactic alpha_CO where it may not apply (starbursts, nuclei, outflows,
low metallicity). Papers state this moves masses by a factor 5.5 (2019ApJ...879...75H) or up to an order of
magnitude (2015MNRAS.448.2224C); the ratio of the two common conventions, 4.35/0.8, is itself about 5.4.

> Always report: the line and flux used, r_J1 (and that it is a brightness-temperature ratio), alpha_CO with
> units and whether it includes helium (x1.36), the distance/cosmology, magnification if lensed, and the
> recovered-flux fraction. A gas mass without these is not reproducible.

Notation: r_J1 = T_b(J-J-1) / T_b(1-0) = L'_CO(J-J-1) / L'_CO(1-0) (brightness-temperature or L' ratio, upper
line over CO(1-0)). r21 = 2-1 over 1-0, r31 = 3-2 over 1-0, r71 = 7-6 over 1-0, and so on.

## When to use

- A detected CO line (any J) in a galaxy, nucleus, cluster BCG, quasar host or GMC and you need L', M_H2,
  Sigma_H2, f_gas or t_dep (e.g. 2018ApJ...865...13T, 2019ApJ...887...74F, 2025ApJ...985..194P).
- Only a mid-J line (CO 3-2 to 7-6) is available at high z and you must correct to CO(1-0)
  (2018Natur.556..469M, 2024A&A...691A.178B, 2020A&A...636A..37D).
- [CI](1-0) or [CI](2-1) as an independent H2 tracer, or to calibrate alpha_CO (2017MNRAS.466.2825B,
  2018ApJ...863..143C, 2021A&A...645A.120F, 2024ApJ...977..198L, 2016A&A...591A..73G).
- Rayleigh-Jeans dust continuum as a gas-mass proxy for faint or high-z sources (2014ApJ...783...84S,
  2017A&A...606A..17M, 2026ApJ..1001..131C).
- Non-detections: an n-sigma line-flux limit turned into a gas-mass limit (2019PASJ...71...40T,
  2024ApJ...977..198L, 2020ApJ...897L..19M).
- Measuring alpha_CO itself from dust, dynamics, [CI], 13CO or LVG modelling (2024ApJ...964...18C,
  2015ApJ...812L..23S, 2017ApJ...848..101V, 2026ApJ..1003..231W).

## When not to use

| Situation | Use instead |
|---|---|
| Protoplanetary disk gas mass | Thermochemical or RT disk models (radmc-3d 5, dali 2 papers in the pack aggregate); CO/H2 = 1e-4 is a lower-limit assumption since CO depletion raises masses (2016ApJ...828...46A); pressure-broadened line wings in 2025ApJ...984L..19Y |
| Protostellar or AGB outflow / shell mass from 12CO | Column-density route with Tex and CO/H2 abundance (2021A&A...648A..41V, 2018MNRAS.481.4931E), or N = X_CO W_CO then M = mu m_H A N with mu = 2.8 per H2 (2024ApJ...961..228S); treat as lower limits (2021A&A...648A..41V, 2024ApJ...961..228S) |
| Optically thick 12CO where 13CO/C18O are detected | LTE isotopologue column density (2017ApJ...848..101V, 2024ApJ...964..166K, 2015ApJ...798...85P) |
| Excitation, density, temperature of the gas | Non-LTE modelling: radex (10 papers), molpop-cep (2), despotic (2), or PDR Toolbox / 3d-pdr / cloudy for [CI] and [CII] |
| Dense-gas mass | HCN with alpha_HCN about 10 (2015ApJ...815..103B, 2018ApJ...858...90G; range 6-40 in 2019ApJS..241...19I) |
| Dust mass itself | the dust-continuum-mass skill; this skill only uses dust as a gas proxy |

## Steps

1. **Measure a clean line flux S dv (Jy km/s).**
   - Primary-beam-corrected cube; spectrum from an aperture enclosing all >=3 sigma emission
     (2018ApJ...865...13T polygon aperture, 2024ApJ...963....1O elliptical aperture).
   - Validate the continuum subtraction before trusting the line: inspect the continuum fit, the line-free
     channel ranges and residual baselines. 2018MNRAS.479.5440L found uv-plane subtraction over-subtracted
     the continuum and switched to image-plane subtraction. Line-free channels are the setting cards most
     often flag as unstated (see Pitfalls), so record yours.
   - Fit Gaussians (PySpecKit in 2018ApJ...865...13T and 2024ApJ...963....1O; LMFIT with tied redshift and
     width across lines in 2020ApJ...902..109B; up to four tied Gaussians per box in 2018ApJ...863..143C) and
     check against direct channel summation (within 1.4 x FWHM in 2020ApJ...902..109B; 20 and 40 km/s
     binning in 2018ApJ...865...13T).
   - Compare with single-dish or lower-resolution flux. Examples in the pack: [CI] 34 +/- 15% below Herschel
     (2018ApJ...863..143C); 40-50% missing CO(3-2) against SEST, masses corrected for 45%
     (2021A&A...656A..60A); PdBI recovering about 80% of CO(1-0) in 2014A&A...567A.125G. Several papers
     state missing flux without a number (2017ApJ...835..278S, 2019A&A...632A..33A, 2021A&A...648A..41V).
     If you cannot correct, call the mass a lower limit (2017ApJ...837...60B).
   - Non-detection: 2024ApJ...977..198L used 3 x RMS_channel x sqrt(dv_channel x FWHM) on a peak-pixel
     spectrum, so RMS_channel there is the per-channel noise of that one-beam spectrum (Jy/beam). For a
     larger aperture, measure the rms of the aperture-integrated spectrum directly (line-free channels or
     off-source apertures of the same shape), or scale the per-beam noise by the number of independent beams
     as 2020ApJ...897L..19M did (N_box pixels over N_beam pixels per beam). Use the primary-beam-corrected
     noise at the source position, and account for channel correlation when channels are narrower than the
     spectral resolution (general practice). Take the assumed width from another line
     (2017MNRAS.466.2825B used the sample mean, 410 km/s; 2019PASJ...71...40T used 5 sigma and 400 km/s;
     2020ApJ...897L..19M used the CO(4-3) FWHM of 96 km/s).
2. **Compute the line luminosity** (general practice, Solomon and Vanden Bout form, used e.g. by
   2019ApJ...887...74F and 2025ApJ...985..194P):

   ```
   L'_line [K km/s pc^2] = 3.25e7 * S dv [Jy km/s] * nu_obs^-2 [GHz] * D_L^2 [Mpc] * (1+z)^-3
   L'_CO(1-0)            = L'_CO(J-J-1) / r_J1          # r_J1 = brightness-temperature (L') ratio
   M_mol                 = alpha_CO * L'_CO(1-0)        # alpha_CO in Msun (K km/s pc^2)^-1
   ```

   For nearby sources the equivalent L_CO = 2453 S dv D^2 is used (2019BAAA...61..134V). The X_CO form
   M_mol = 1.05e4 (X_CO/2e20) (1+z)^-1 S dv D_L^2 for CO(1-0) (2014ApJ...784...78R; general Bolatto et al.
   form) is helium-inclusive: the 1.05e4 coefficient already contains the 1.36 factor. For H2 only, divide
   by 1.36 (about 7.7e3); never multiply this form by 1.36 again. Divide by the magnification for lensed
   sources (2017MNRAS.466.2825B).
3. **Correct to CO(1-0)** with r_J1 (Parameter table). Prefer a measured ratio in the same aperture
   (2018ApJ...863..143C measured r21 per component; 2020ApJ...889....9M per region). Otherwise adopt a
   population ratio and say so (2024A&A...691A.178B used AGN-specific r21=0.68, r31=0.59, r41=0.37 and a
   different set for the control sample).
4. **Choose alpha_CO** (Parameter table). Environment sets the candidate values, not an automatic answer:
   papers adopt a Galactic value for metal-rich disks and about 0.8 for ULIRGs and mergers (for example
   4.8 below L_FIR = 1e11 Lsun and 0.8 for U/LIRGs in 2014ApJS..214....1U), a metallicity-dependent
   prescription when Z is known to be low, and an explicit range for outflows. Measured values often fall
   between: 2.1 +/- 1.2 for the NGC 6240 outflow from [CI] (2018ApJ...863..143C), 0.6 and 1.6 from dynamics
   at z~1.6 (2015ApJ...812L..23S); Seyfert tori use Galactic X_CO (2021A&A...652A..98G). State why you
   picked a value, and when the environment is ambiguous give masses for both candidate values
   (2014ApJ...787...48X, 2018Sci...362.1034D). Decide helium once: alpha_CO = 4.3-4.4 includes the 1.36
   factor (2020MNRAS.495.3840M, 2020MNRAS.499..193K, 2024MNRAS.527.9343L); X_CO = 2e20 in N(H2) = X_CO W_CO
   does not, and papers that go from N(H2) to mass add 1.36 explicitly (2018ApJ...853..149S,
   2021A&A...652A..98G). That addition is already built into the 1.05e4 form of Step 2.
   2017ApJ...848L...7C deliberately uses 3.2 without helium.
5. **Cross-check with a second tracer if you have one.**
   - [CI](1-0), optically thin LTE (general Papadopoulos and Greve form):
     `M_H2 = 1375.8 D_L^2 (1+z)^-1 (X_CI/1e-5)^-1 (A10/1e-7)^-1 Q10^-1 S_CI(1-0) dv` with A10 = 7.93e-8 s^-1
     and X_CI = 3e-5 as the usual choices (2017MNRAS.466.2825B, 2018ApJ...863..143C, 2021A&A...645A.120F).
     Q10 depends on the [CI] excitation temperature: Tex = 30 K is adopted in 2017MNRAS.466.2825B and
     2018ApJ...863..143C; 2024ApJ...977..198L uses Q10 = 0.457 at Tex = 29.1 K; 2021A&A...645A.120F instead
     adopts a median Q10 = 0.48 without quoting a Tex (its 40 K is the dust temperature of its continuum
     cross-check, not a [CI] Tex).
   - [CI](2-1): the same form with the 2-1 constants (general Papadopoulos and Greve form):
     `M_H2 = 1375.8 D_L^2 (1+z)^-1 (X_CI/1e-5)^-1 (A21/1e-7)^-1 Q21^-1 S_CI(2-1) dv`, with
     A21 = 2.68e-7 s^-1 and Q21 = 0.57 in 2016A&A...591A..73G. Q21 is far more temperature-sensitive than
     Q10: 2024A&A...685A.138V tested Q21 = 0.05-0.4, so state Tex and propagate its range.
   - Dust RJ continuum: M_mol = L_nu(850 um rest) / alpha_850, alpha_850 = 6.7e19 erg/s/Hz/Msun calibrated
     at Td = 25 K, beta = 1.8 (2017A&A...606A..17M, 2024ApJ...977..251H, 2019MNRAS.482.3135B); apply a
     temperature correction when Td differs (2026ApJ..1001..131C). This calibration carries a Galactic
     alpha_CO = 6.5 (2017A&A...602L...9M), so compare like with like. It was calibrated on high-stellar-mass
     galaxies and does not probe low metallicity (2016ApJ...820...83S): validate before using it on dwarfs
     or low-Z systems. Remove non-dust continuum first: 2024ApJ...977..198L subtracted a synchrotron power
     law for one QSO and could not for another; if you cannot constrain it, propagate it or call the dust
     mass an upper limit.
   - 13CO LTE: N(13CO) from Tex (from optically thick 12CO) and tau, then H2/13CO = 1.4e6 to 5e6
     (2024ApJ...964..166K, 2016ApJ...831...32N, 2024ApJ...966...51G); alpha_CO = M_LTE / L'_CO(1-0)
     (2017ApJ...848..101V got 2.26). Use matched apertures and velocity components for both lines, test the
     13CO opacity (2017ApJ...848..101V applied a finite-opacity correction) and the shared Tex and filling
     factor assumptions (it used Tex = 15 K, filling factor 0.1), and remember the LTE mass traces only part
     of the total molecular mass (2017ApJ...848..101V says so), so the derived alpha_CO is a lower bound.
6. **Derive the quantities you need.** Sigma_H2 with a cos i deprojection (2025ApJ...995..151Y); in nearby
   disks Sigma_H2 = 4.2 I_CO(1-0) with helium (2019A&A...623A..66B). f_gas = M_gas/(M_gas+M*)
   (2019ApJ...887...74F, 2015ApJ...812L..23S, 2025ApJ...985..194P); t_dep = M_gas/SFR (2014ApJ...783...84S).
   Add H I from a measurement when you have one. Assumed values are sample-specific: H2/HI = 0.3 for the
   total gas fraction in 2020ApJ...889....9M, HI = 50% of H2 only for the local calibration sample of
   2014ApJ...783...84S, M_H2/M_HI = 5 in 2020A&A...636A..37D. Justify any assumed ratio for your population.
7. **Write the error budget.** Statistical flux error plus flux-calibration error in quadrature (10% in
   2016ApJ...828...46A; 5% in 2025ApJ...988..162D, 2025ApJ...990..221M; 30% conservative for ACA Band 8 in
   2020ApJ...897L..19M), then the systematic alpha_CO and r_J1 terms stated separately (0.3 dex added on
   M_mol in 2018ApJ...853..195W; 50% in 2019Natur.569..519K and 2025A&A...698A.296R; +/-0.20 dex in
   2021A&A...652A..98G). 2024ApJ...964..166K set its uncertainties from an assumed 10% error on observed
   flux plus a factor-four variation of X_CO in starbursts.

## Parameter defaults and ranges

Counts are my own regex count over the pack's "Key parameters" and "Assumptions" lines (345 of the 360
papers appear there), after dropping clearly off-topic hits (for example an X-ray binary jet paper and a
regex false match on "z=4.3"). They are approximate lower bounds: a paper that states its alpha_CO only in
prose outside those lines is not counted. The 3.6 and 4.6 rows were recounted on the rebuilt pack by listing
every line with an alpha_CO of that value and reading its population. Longer per-population lists are in
`references/parameters.md`. Units: alpha in Msun (K km/s pc^2)^-1, X_CO in cm^-2 (K km/s)^-1.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| alpha_CO, Galactic (incl. He) | 4.3-4.4 | 4.3, 4.35, 4.36, 4.4 used interchangeably | about 60 | 2017ApJ...835..278S, 2021A&A...656A..60A, 2020MNRAS.495.3840M, 2025ApJ...990..221M |
| alpha_CO 4.6 (older Galactic / disk value) | 4.6 | | 10 adopt it: 9 for Galactic, disk or tidal gas, 1 for SMGs; 2 more quote 0.8-4.6 | 2018MNRAS.478.3120A, 2019MNRAS.485.1595P, 2021AN....342.1160P, 2020MNRAS.497.2771M (disks; 0.8 for mergers); SMGs: 2014ApJ...783...84S |
| X_CO, Galactic (no He) | 2e20 | 1.8e20 to 4.7e20 | about 38 at 2e20 | 2014ApJ...784...78R, 2018ApJ...865...13T, 2024ApJ...963....1O; 3e20: 2020MNRAS.496.4061D; 4e20: 2017ApJ...843..136E; 4.7e20 stated as Galactic: 2017ApJ...846...73T |
| alpha_CO, ULIRG / merger / starburst | 0.8 | 0.6 to 1.5 | about 39 at 0.8 | 2017ApJ...843...18V, 2018Natur.556..469M, 2019ApJ...887...74F, 2024ApJ...977..198L; 1.0: 2018Natur.553...51M; 1.1: 2015ApJ...812L..23S |
| alpha_CO, high-z star-forming galaxies | 3.6 | | 10 (7 of them ASPECS/HUDF papers) | 2016ApJ...833...69D, 2019ApJ...882..137P, 2020ApJ...902..109B, 2024A&A...691A.178B, 2016NatAs...1E...3P |
| alpha_CO, Scoville convention | 6.5 (from X_CO = 3e20 with He) | | 8 | 2016ApJ...820...83S, 2017A&A...606A..17M, 2018ApJ...860..111D |
| alpha_CO, low metallicity | scale with Z | 8 to 110 (CO 2-1 at 110) | about 25 mention metallicity | 4.35 Z'^-1.6 (2021A&A...656A.133Q, 2025A&A...698A.296R); 4.35 (Z/Zsun)^-1 (2019Natur.569..519K); 17 at 12+log(O/H)=8.3 (2025A&A...700A.165B); 110 +/- 30 (2017ApJ...835..278S) |
| alpha_CO, outflows | 0.8, with optically thin 0.3-0.34 as lower bound | 0.25 to 3.4 | (see examples) | 2015A&A...580A...1M, 2018ApJ...863..143C (measured 2.1 +/- 1.2), 2019MNRAS.489.1927S, 2017A&A...608A..38O |
| r21 = T_b(2-1)/T_b(1-0) | 0.7-0.8 | 0.6 to 1.0 in disks and LIRGs; 1.1-1.4 in nuclei and outflows; 2.2-2.5 adopted for the NGC 1068 CND and torus | about 65 state a 2-1/1-0 ratio | 0.7: 2018ApJ...860..172S, 2018ApJ...861L..18U; 0.8: 2021ApJ...908...54W, 2017MNRAS.466.2825B; 1: 2017ApJ...835..278S; 1.4 (outflow): 2018ApJ...863..143C; 2.2-2.5: 2019A&A...632A..61G |
| r31 = T_b(3-2)/T_b(1-0) | 0.5-0.8 | 0.27 to 0.8 in galaxies; 2.0 to 2.9 adopted for AGN tori (stated as brightness-temperature ratios) | about 39 state an r_J1 for J>=3 | 0.8: 2019ApJ...887...74F, 2024ApJ...963....1O; 0.66: 2016NatAs...1E...3P; 0.42: 2019ApJ...882..136A; 0.27: 2021A&A...656A..60A; 2.0-2.9: 2021A&A...652A..98G, 2019A&A...632A..61G |
| r41 = T_b(4-3)/T_b(1-0); r43 = T_b(4-3)/T_b(3-2) | 0.4-0.45 (r41) | 0.31 to 0.91 | (see examples) | r41 0.41: 2018Natur.556..469M, 2018PASJ...70L...6K; 0.87 (QSO): 2024ApJ...977..198L; r43 0.91 and 0.46: 2019MNRAS.487.4305S |
| r51, r54 (5-4 over 4-3), r61, r71 | SLED of a comparison population | r54 0.28; r51 0.23 (MS) to 0.6 (SB); r61 0.34 (SMG) to 0.64 (QSO); r71 0.16 (SMG) to 0.48 (QSO) | (see examples) | 2018MNRAS.477.4380S, 2017MNRAS.469.4683C, 2020A&A...636A..37D |
| X_CI = [CI]/H2 | 3e-5 | 1e-5 to 8.4e-5 | 8 at 3e-5 | 2017MNRAS.466.2825B, 2018ApJ...863..143C, 2021A&A...645A.120F; 1.5e-5: 2021ApJ...908..163M; 8.4e-5: 2024ApJ...977..198L |
| Tex for [CI] | 30 K | 29.1 to 30 K where stated | 5 at 30 K | 2017MNRAS.466.2825B, 2018ApJ...863..143C, 2020ApJ...902..109B, 2019ApJ...887..144J, 2017ApJ...845..154V; 29.1 K: 2024ApJ...977..198L |
| Q10 | 0.48-0.6 | 0.35 to 0.6 | (see examples) | 0.48 (adopted median): 2021A&A...645A.120F; 0.5: 2018ApJ...866L..12G; 0.6: 2017MNRAS.466.2825B; 0.35: 2019MNRAS.482.3135B |
| Q21, A21 for [CI](2-1) | Q21 0.57, A21 2.68e-7 s^-1 | Q21 0.05 to 0.4 tested | 2 | 2016A&A...591A..73G, 2024A&A...685A.138V |
| alpha_[CI] | 7.3-9.4 | | 2 | 2020ApJ...897L..19M, 2018ApJ...863..143C |
| CO/H2 abundance (Galactic sources, disks) | 1e-4 | 1.6e-5 (LMC) to 7e-4 | about 22 | 2021A&A...648A..41V, 2017ApJ...846L..26W; 2e-4: 2021A&A...646A...1K; 1.6e-5: 2019PASJ...71...44H |
| Helium factor on H2 mass | x1.36 | 1.36 to 1.41 | about 29 state it | 1.36: 2018ApJ...853..149S, 2021ApJ...908..163M; 1.41: 2016ApJ...823...68S |
| Mean molecular weight | mu_H2 = 2.76-2.8 (mass per H2 molecule, multiply m_H by mu_H2 x N(H2)); mu_p = 2.37 (mass per free particle, for number densities and pressure) | | (see examples) | mu 2.8 per H2: 2024ApJ...961..228S; 2.37: 2017ApJ...846L..26W |
| alpha_850 (dust RJ) | 6.7e19 erg/s/Hz/Msun | 0.79e20 to 1.0e20 in the original calibration | 6 | 2017A&A...606A..17M, 2017ApJ...844..123F, 2014ApJ...783...84S |
| Line-detection threshold | 3 sigma | 3 to 5 sigma | (see examples) | 2020ApJ...902..109B, 2024ApJ...977..198L; 5 sigma: 2019PASJ...71...40T |

## Software

From the rebuilt pack's software aggregate (software named in matched steps of all 360 papers; names
lower-cased there, and I merged obvious aliases, noted in the table). The conversion itself is nearly always
custom code; the packages below do flux extraction, excitation modelling or cloud catalogues.

| Tool | Papers | What it is used for |
|---|---|---|
| casa | 25 | imaging, moment maps, flux extraction |
| radex (+ pyradex, radex_emcee) | 10 (+1, +1) | non-LTE excitation, Tex, tau, N(CO); e.g. outflow streamer densities (2017ApJ...837...60B), dark-gas X_CO (2020ApJ...889L...4L) |
| emcee | 9 | MCMC for line-ratio, disk and regression fits (2024A&A...691A.178B) |
| radmc-3d, dali | 5, 2 | disk models where a gas mass is a model parameter (2018ApJ...854..130W) |
| magphys | 4 | stellar masses and SFRs for f_gas and t_dep |
| 3dbarolo, kinms, galmod, tirific | 4, 2, 1, 1 | dynamical masses compared with gas masses (2018MNRAS.479.5440L) |
| cprops, astrodendro | 4, 2 | cloud decomposition before per-cloud luminous masses (2017ApJ...835..278S) |
| PDR Toolbox (pdrtoolbox 2, pdr toolbox 2, pdrt 1, photodissociation region toolbox 1), 3d-pdr, cloudy, despotic, molpop-cep | 6 entries, 1, 3, 2, 2 | [CI]/CO/[CII] ratios to density and UV field (2020ApJ...902..109B, 2017MNRAS.466.2825B, 2020ApJ...897L..19M) |
| lmfit, pyspeckit | 2, 2 | Gaussian line fits |
| linmix_err.pro | 1 | censored Bayesian regression of alpha_CO trends (2018ApJ...863..143C) |
| miriad | 3 | imaging outside CASA; GILDAS is named in three excerpt cards (e.g. 2021A&A...652A..98G) but not in the aggregate |

## Pitfalls

- **Helium double counting.** 4.35 already includes 1.36; X_CO = 2e20 in N(H2) does not; the 1.05e4 mass
  form of Step 2 does. Check each literature value: 2016NatSR...626896A excludes helium, 2017ApJ...848L...7C
  uses 3.2 without helium, 2020ApJ...902..109B divides M_mol by 1.36 to get M_H2.
- **alpha_CO per transition.** alpha_CO(2-1) = alpha_CO(1-0)/r21: 4.35, 6.25 and 17.4 for 1-0, 2-1, 3-2 in
  2018ApJ...860..172S; 6.2 for 2-1 in 2018ApJ...868L..38G; 9.3 vs 4.2 measured in 2024ApJ...964...18C.
  Never apply a (1-0) factor to an uncorrected higher-J luminosity.
- **Flux ratio vs brightness ratio.** Several cards quote CO(2-1)/CO(1-0) of about 3 (2018ApJ...865...13T,
  2019ApJ...887..149B, 2020A&A...641A.151S) or 3-2/1-0 of 9 (2017A&A...602A..11P): these are flux-density
  ratios. In general, S_J/S_1 = r_J1 x (nu_J/nu_1)^2, so r_J1 = (S_J/S_1) / J^2 for CO (4 for 2-1, 9 for
  3-2). Since L'_CO(1-0) = L'_CO(J) / r_J1, using the flux ratio in place of r_J1 underestimates
  L'_CO(1-0), and the mass, by a factor 4 (2-1) or 9 (3-2).
- **Galactic alpha_CO in starbursts or nuclei.** Papers state the Galactic value would raise masses by 5.5
  (2019ApJ...879...75H) or that X_CO may be overestimated by up to an order of magnitude
  (2015MNRAS.448.2224C). Nuclear values of 1/4 Galactic in 2014A&A...567A.125G and 2019A&A...632A..33A.
  The 6.5 (Scoville) versus 0.8 conventions in 2017A&A...606A..17M and 2016A&A...594A..81P differ by a
  factor of about 8 by calculation, not by a statement in those papers.
- **Mid-J only.** The SLED shape is a large assumed term: CO(5-4)/CO(1-0) = 0.23 carries a factor-2
  uncertainty in 2016ApJ...819...82S, and r61 and r71 differ by factors 2-3 between SMG and QSO SLEDs in
  2020A&A...636A..37D. Test alternative excitation corrections as 2015ApJ...812L..23S did, and include the
  SLED term in the error budget.
- **Missing short spacings.** Interferometric masses can be well below single-dish (Step 1). Check recovery
  both against single-dish and against a lower-resolution interferometric image where you have one.
- **Continuum subtraction.** Over-subtraction in the uv plane removes line flux (2018MNRAS.479.5440L).
  Inspect continuum fits and residual baselines before accepting a flux.
- **CMB at high z.** Not correcting can bias masses low by about 2x (2018ApJ...856...72O); half the intrinsic
  flux missed in 2017MNRAS.466..138K; estimated <~15% and ignored in 2019ApJ...882..138D. State which.
- **Low metallicity and CO-dark gas.** CO misses H2 at low Z; 2016A&A...586A..45S applies a CO-dark
  correction; dark-gas X_CO of 14e20 in 2020ApJ...889L...4L. The metallicity of the ionised gas may not be
  that of the molecular gas (2015ApJ...812L..23S), or is unknown at the ALMA position (2016A&A...586A..45S).
- **[CI] assumptions.** Masses scale as 1/X_CI and depend on Tex through Q10 (and much more strongly through
  Q21 for [CI](2-1)); 2021A&A...645A.120F notes its errors exclude X_CI, Q10 and A10; 2020ApJ...897L..19M
  found [CI] an order of magnitude below the CO relation. [CI] can be optically thick (tau about 10 in
  2019ApJ...885L..39H).
- **Lensing.** 2017MNRAS.466.2825B lists differential lensing as possible (its lens models come from dust
  and are applied to [CI]) and discusses why it likely does not change its [CI] gas masses much;
  2018A&A...620A.115B assumes differential lensing negligible. State the assumption, and do not reuse a
  dust-based magnification for line ratios without saying so.
- **Optically thin limits.** Masses may be an order of magnitude lower if 12CO is optically thin
  (2014ApJ...797...90S); a single thick line underestimates disk mass (2017ApJ...846L..26W).
- **Unstated settings** most often flagged by the cards: CASA version (24), line-free channels and continuum
  subtraction (20, plus 12 + 12 under other wordings), CASA and pipeline version (14), flux calibrator and
  flux-scale uncertainty (14), PB correction (7 + 7). The cards rarely state whether alpha_CO includes
  helium or which aperture the r_J1 was measured in.

## Verification checks

What the papers did:

- **Single-dish flux comparison** (2018ApJ...863..143C consistent CO fluxes; 2021A&A...656A..60A 40-50%
  missing).
- **Independent tracers compared**: three-tracer comparison ([CI], CO(4-3), dust) in 2024ApJ...977..198L,
  which warns the comparison is hampered by large parameter uncertainties. Documented agreement: dust vs CO
  median 0.23 dex in 2021A&A...652A..98G; LTE vs X_CO masses KS p = 0.52 in 2024ApJ...964..166K;
  dust-based [CI] abundance matches the CO-based one in 2020ApJ...902..109B. Comparisons without a stated
  agreement level: [CI] vs continuum in 2021A&A...645A.120F, C17O vs X_CO in 2015ApJ...801...63M.
- **Dynamical mass budget**: compare gas plus stars with M_dyn inside the same radius. 2018MNRAS.479.5440L
  found M_bar = (3.4 +/- 2.0)e11 Msun against M_dyn = (0.9 +/- 0.3)e11 at 4 kpc and (1.8 +/- 0.6)e11 when
  extrapolated to 8 kpc, so the budget is only consistent at the larger radius; 2015ApJ...812L..23S derived
  alpha_CO from dynamical masses; 2019MNRAS.486.2366M used MH2 < Mdyn as a prior. Match the enclosed radii
  before using M_dyn as a ceiling.
- **Vary the assumptions** and report the spread: excitation corrections (2015ApJ...812L..23S), r43 0.91 and
  0.46 (2019MNRAS.487.4305S), r13 1 and 1.35 (2021A&A...656A..60A), alpha_CO 0.35 to 4.35
  (2025ApJ...992L...7S), D/M 0.1 to 1 (2024ApJ...964...18C).
- **Environment check for alpha_CO**: metallicity from the mass-metallicity relation and BPT
  (2015ApJ...812L..23S); Schmidt-Kennicutt placement (2014ApJ...784...78R).
- **Extraction robustness**: binning and weighting (2024ApJ...963....1O found 0.88-2.5 Jy km/s with natural
  weighting depending on binning, so state your choice); fit vs direct sum (2020ApJ...902..109B).
- **Continuum contamination**: synchrotron subtracted before using dust as a tracer (2024ApJ...977..198L).
- **Gas-to-dust sanity**: 944 +/- 77 in 2019ApJ...887...74F and about 30 with alpha_CO = 0.8 vs about 95 at
  solar in 2019ApJ...877L..38R show how alpha_CO choices surface as odd gas-to-dust ratios.

What a careful referee adds:

- Recompute L' and M from the quoted S dv, nu_obs, D_L, z, r_J1 and alpha_CO; check units and helium.
- Confirm r_J1 is a brightness-temperature ratio measured in matched apertures and matched uv coverage
  (general practice; 2024ApJ...964..166K notes its mass comparison depends on R21 and resolution
  differences).
- Ask for masses at both Galactic and ULIRG alpha_CO when the environment is ambiguous
  (2014ApJ...787...48X, 2018Sci...362.1034D quote both).
- Check that limits use the same width, r_J1 and alpha_CO as detections, and that the limit's rms belongs to
  the aperture used.

## Source cards

Full list with titles: `references/sources.md`. Most informative for this technique:

- 2018ApJ...863..143C: [CI] + CO(1-0) alpha_CO for outflow and quiescent gas, per-box decomposition.
- 2017MNRAS.466.2825B: [CI](1-0) H2 masses at z~4, implied alpha_CO = 2.0 +/- 1.0.
- 2024ApJ...964...18C: resolved dust-based alpha_CO in 37 galaxies, Sigma_star dependence.
- 2017ApJ...835..278S: low-metallicity alpha_CO from dust in NGC 6822, CPROPS clumps.
- 2017ApJ...848..101V: 13CO LTE mass and alpha_CO in a BCG.
- 2015ApJ...812L..23S: alpha_CO from dynamical masses at z~1.6.
- 2020ApJ...902..109B: ASPECS CO SLEDs and [CI] abundances.
- 2024ApJ...977..198L: three-tracer gas masses and CGM [CI].
- 2021A&A...645A.120F: [CI] mass with continuum cross-check.
- 2021A&A...652A..98G: dust vs CO masses in Seyfert tori.
- 2014ApJ...783...84S: alpha_850 RJ dust calibration.
- 2024ApJ...964..166K: LTE vs X_CO masses in the Antennae.
- 2018ApJ...860..172S: alpha_CO per transition.
- 2014A&A...567A.125G: dust-matched X_CO in NGC 1068 nucleus.
- 2021A&A...656A..60A: missing-flux correction of nuclear masses.
- 2025ApJ...985..194P: stacked CO(2-1), metallicity-dependent alpha_CO.
- 2024A&A...691A.178B: AGN-specific r_J1 and censored fits.
- 2018ApJ...865...13T: aperture Gaussian fit, X_CO form, binning check.
- 2017ApJ...843...18V: outflow mass with ULIRG alpha_CO.
- 2020ApJ...897L..19M: [CI]-faint galaxy, [CI] limit vs CO mass.
- 2018MNRAS.479.5440L: continuum over-subtraction check and dynamical mass budget.
- 2025ApJ...984L..19Y: disk surface density scaling with X_CO.
