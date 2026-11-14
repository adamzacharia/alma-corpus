---
name: alma-gas-mass-co-conversion
description: "Turn ALMA CO, [CI], 13CO or dust-continuum measurements into molecular gas masses, surface densities, gas fractions and depletion times, choosing the excitation correction (r_J1), conversion factor (alpha_CO / X_CO, X_CI, CO/H2 abundance) and helium convention the way published ALMA papers do. Use when converting a line flux to L' and M_H2, picking alpha_CO for a galaxy, nucleus, outflow or low-metallicity region, converting mid-J CO to CO(1-0), using [CI] or the Rayleigh-Jeans dust continuum as a gas tracer, stating gas-mass limits for non-detections, or checking someone else's gas mass. Built from 876 ALMA papers (2012-2026)."
---

# Molecular gas masses from CO, [CI] or dust

Converts a line (or continuum) measurement into H2 or total molecular mass:
M_mol = alpha x L'_CO(1-0), with L'_CO(1-0) = L'_CO(J-J-1) / r_J1. Two assumed numbers carry nearly all
of the uncertainty: the conversion factor (alpha_CO, X_CO, X_CI or CO/H2) and, for J>1, the excitation ratio
r_J1. The mistakes that matter most: (1) mixing conventions (alpha_CO with or without helium, alpha_CO for
CO(1-0) applied to CO(2-1), a flux-density ratio used where a brightness-temperature ratio is needed), each a
factor 1.36 to 9 error; (2) using a Galactic alpha_CO where it may not apply (starbursts, nuclei, outflows,
low metallicity). Papers state this moves masses by a factor 5.5 (2019ApJ...879...75H (card)) or up to an
order of magnitude (2015MNRAS.448.2224C); the ratio of the two common conventions, 4.35/0.8, is about 5.4.

> Always report: the line and flux used, r_J1 (and that it is a brightness-temperature ratio), alpha_CO with
> units and whether it includes helium (x1.36), the distance/cosmology, magnification if lensed, and the
> recovered-flux fraction. A gas mass without these is not reproducible.

Notation: r_J1 = T_b(J-J-1) / T_b(1-0) = L'_CO(J-J-1) / L'_CO(1-0) (upper line over CO(1-0)). r21 = 2-1
over 1-0, r31 = 3-2 over 1-0, r43 = 4-3 over 3-2, and so on. A bibcode marked "(card)" has no line in the
rebuilt pack; the claim was checked in that paper's methods card.

## When to use

- A detected CO line (any J) in a galaxy, nucleus, cluster BCG, quasar host or GMC and you need L', M_H2,
  Sigma_H2, f_gas or t_dep (e.g. 2018ApJ...865...13T, 2019ApJ...887...74F, 2025ApJ...985..194P).
- Only a mid-J line (CO 3-2 to 7-6) is available at high z and you must correct to CO(1-0)
  (2018Natur.556..469M (card), 2024A&A...691A.178B, 2020A&A...636A..37D (card)).
- [CI](1-0) or [CI](2-1) as an independent H2 tracer, or to calibrate alpha_CO (2017MNRAS.466.2825B,
  2018ApJ...863..143C, 2021A&A...645A.120F, 2024ApJ...977..198L, 2016A&A...591A..73G).
- Rayleigh-Jeans dust continuum as a gas-mass proxy for faint or high-z sources (2014ApJ...783...84S,
  2017A&A...606A..17M (card), 2026ApJ..1001..131C (card)).
- Non-detections: an n-sigma line-flux limit turned into a gas-mass limit (2019PASJ...71...40T (card),
  2024ApJ...977..198L, 2020ApJ...897L..19M).
- Measuring alpha_CO itself from dust, dynamics, [CI], 13CO, per-pixel RADEX or LVG modelling
  (2024ApJ...964...18C, 2015ApJ...812L..23S, 2017ApJ...848..101V, 2024ApJ...971..176H,
  2026ApJ..1003..231W (card)), or from a known mass in the Galactic centre (2025ApJ...995L..51G).

## When not to use

| Situation | Use instead |
|---|---|
| Protoplanetary disk gas mass | Thermochemical or RT disk models (radmc-3d 7, dali 7 papers in the pack aggregate); CO/H2 = 1e-4 is a lower-limit assumption since CO depletion raises masses (2016ApJ...828...46A); pressure-broadened line wings in 2025ApJ...984L..19Y |
| Protostellar or AGB outflow / shell mass from 12CO | Column-density route with Tex and CO/H2 abundance (2021A&A...648A..41V, 2018MNRAS.481.4931E), or N = X_CO W_CO then M = mu m_H A N with mu = 2.8 per H2 (2024ApJ...961..228S); treat as lower limits |
| Optically thick 12CO where 13CO/C18O are detected | LTE isotopologue column density (2017ApJ...848..101V, 2024ApJ...964..166K, 2015ApJ...798...85P) |
| Excitation, density, temperature of the gas | Non-LTE modelling: radex (26 papers in the aggregate, myradex 3); PDR Toolbox (8 entries), cloudy (8) or 3d-pdr (2017MNRAS.466.2825B) for [CI] and [CII] |
| Dense-gas mass | HCN with alpha_HCN about 10 (2015ApJ...815..103B (card), 2018ApJ...858...90G; range 6-40 in 2019ApJS..241...19I (card)) |
| Dust mass itself | the dust-continuum-mass skill; this skill only uses dust as a gas proxy |

## Steps

1. **Measure a clean line flux S dv (Jy km/s).**
   - Primary-beam-corrected cube. Choose the aperture or mask and say why: a polygon or elliptical aperture
     around all >=3 sigma emission (2018ApJ...865...13T, 2024ApJ...963....1O (card)), a broad mask built for
     completeness (2021A&A...650A.134P), or a mask made from a smoothed cube and applied to the original
     (2024MNRAS.528.6768H). None of these is a universal rule. Check the choice with a curve of growth
     (2 x beam FWHM in 2025ApJ...987..158F) and measure the noise with the same aperture at random
     positions (30 in 2021ApJ...909..181L).
   - Validate the continuum subtraction: inspect the continuum fit, line-free channels and residual
     baselines. 2018MNRAS.479.5440L found uv-plane subtraction over-subtracted and switched to the image
     plane (imcontsub fitorder = 0 in 2021ApJ...909..181L); 2025ApJ...987..158F imaged the line-free
     channels of the subtracted cubes. Record your line-free channels.
   - Fit Gaussians (PySpecKit in 2018ApJ...865...13T and 2024ApJ...963....1O (card); LMFIT with tied
     redshift and width in 2020ApJ...902..109B; up to four tied Gaussians per box in 2018ApJ...863..143C) and
     check against direct channel summation (within 1.4 x FWHM in 2020ApJ...902..109B (card)).
   - Compare with single-dish or lower-resolution flux: [CI] 34 +/- 15% below Herschel (2018ApJ...863..143C);
     40-50% missing CO(3-2) against SEST, masses corrected for 45% (2021A&A...656A..60A (card)); PdBI
     recovering about 80% of CO(1-0) (2014A&A...567A.125G (card)); 30-57% recovered in outflow lobes
     (2024ApJ...969L...6Z); no missing CO(1-0) against NRO (2024A&A...689A..67G). If you cannot correct,
     call the mass a lower limit (2017ApJ...837...60B).
   - Non-detection: 2024ApJ...977..198L used 3 x RMS_channel x sqrt(dv_channel x FWHM) on a peak-pixel
     (one-beam) spectrum, so RMS_channel is the per-channel noise of that spectrum (Jy/beam). For a larger
     aperture, prefer the rms of the aperture-integrated spectrum measured directly (line-free channels or
     off-source apertures of the same shape). If you must scale, use
     sigma_ap ~ sigma_beam x sqrt(N_box / N_beam), with N_box the pixels in the aperture and N_beam the
     pixels per beam (2020ApJ...897L..19M: N_box = 3990, N_beam = 247); this assumes noise independent
     between beams and uniform across the aperture. Use primary-beam-corrected noise and account for channel
     correlation (general practice). Take the width from another line (CO(4-3) FWHM 96 km/s in
     2020ApJ...897L..19M; 5 sigma over 400 km/s in 2019PASJ...71...40T (card)).
2. **Compute the line luminosity** (Solomon and Vanden Bout form, used e.g. by 2019ApJ...887...74F):

   ```
   L'_line [K km/s pc^2] = 3.25e7 * S dv [Jy km/s] * nu_obs^-2 [GHz] * D_L^2 [Mpc] * (1+z)^-3
   L'_CO(1-0)            = L'_CO(J-J-1) / r_J1          # r_J1 = brightness-temperature (L') ratio
   M_mol                 = alpha_CO * L'_CO(1-0)        # alpha_CO in Msun (K km/s pc^2)^-1
   ```

   The X_CO form M_mol = 1.05e4 (X_CO/2e20) (1+z)^-1 S dv D_L^2 for CO(1-0) (2014ApJ...784...78R) is
   helium-inclusive: for H2 only divide by 1.36 (about 7.7e3); never multiply it by 1.36 again. Divide by
   the magnification for lensed sources (2017MNRAS.466.2825B).
3. **Correct to CO(1-0)** with r_J1 (table below). Prefer a measured ratio in the same aperture
   (2018ApJ...863..143C per component; 2020ApJ...889....9M per region). Otherwise adopt a population ratio
   and say so (2024A&A...691A.178B: AGN r21 = 0.68, r31 = 0.59, r41 = 0.37, a different set for controls).
   Do not default to r_J1 = 1 without a reason: 2025A&A...699A..83A assumed R_J1 = 1 for its QSO2 masses
   yet measured an integrated R32 of 0.22-0.75 in the same sample. At high z, decide on the CMB:
   2024A&A...684A..33K divided alpha_CO by f_CMB (0.53-0.56 for CO(2-1) at z~6-7).
4. **Choose alpha_CO** (table below). Environment sets candidate values, not an automatic answer: a
   Galactic value for metal-rich disks, about 0.8 for ULIRGs and mergers (4.8 below L_FIR = 1e11 Lsun and
   0.8 for U/LIRGs in 2014ApJS..214....1U), a metallicity-dependent prescription when Z is known to be low,
   an explicit range for outflows. Measured values often fall between: 2.1 +/- 1.2 for the NGC 6240 outflow
   from [CI] (2018ApJ...863..143C), 0.6 and 1.6 from dynamics at z~1.6, averaged to 1.1 for the unresolved
   sources (2015ApJ...812L..23S (card)); Seyfert tori use Galactic X_CO (2021A&A...652A..98G). State why
   you picked a value, and when the environment is ambiguous give masses for both (2014ApJ...787...48X
   (card), 2018Sci...362.1034D).
   - Decide helium once: alpha_CO = 4.3-4.4 includes 1.36 (2020MNRAS.495.3840M (card), 2024MNRAS.527.9343L
     (card)); X_CO = 2e20 in N(H2) = X_CO W_CO does not, and papers going from N(H2) to mass add 1.36
     (2018ApJ...853..149S (card), 2021A&A...652A..98G). 2017ApJ...848L...7C (card) uses 3.2 without helium,
     2020MNRAS.495.1760O uses 3.6 without helium, 2025A&A...694A.218B multiplies 0.8 by 1.36.
   - Metallicity recipes differ (Z'^-1.6, Accurso 2017, Genzel 2015, Bolatto eq. 31; list in
     `references/parameters.md`). Name the recipe and the O/H calibration.
   - Non-LTE route: alpha_CO = 1.36 m_H2 N_CO Phi_bf / (x_CO I_CO(1-0)) per pixel from a RADEX grid fit to
     CO and 13CO lines (about 1.1 in the Antennae, 2024ApJ...971..176H; 0.9-1.5 in the NGC 1614 ring vs
     2.4-3.5 from dynamics, 2014ApJ...796L..15S). Both assume x_CO = 3e-4, which the fit cannot constrain.
     Before trusting it: rescale the column and intensity to the measured linewidth, correct the posterior
     for the alpha_CO prior the grid imposes, drop pixels at grid edges or with poor fits, and note that
     only pixels with the needed 13CO detections enter (steps in `references/parameters.md`).
   - A nuclear location alone does not justify a low alpha_CO: the Galactic centre CND gives 4.5 +/- 2.5
     from a known mass (2025ApJ...995L..51G).
5. **Cross-check with a second tracer if you have one.**
   - [CI](1-0), optically thin LTE (Papadopoulos and Greve form):
     `M_mol = 1375.8 D_L^2 (1+z)^-1 (X_CI/1e-5)^-1 (A10/1e-7)^-1 Q10^-1 S_CI(1-0) dv` with
     A10 = 7.93e-8 s^-1 and X_CI = 3e-5 as the usual choices (2017MNRAS.466.2825B, 2018ApJ...863..143C,
     2021A&A...645A.120F). By my calculation (nu_rest = 492.16 GHz) this equals 1.36 times the H2-only form
     `M_H2 = 9.51e-5 / (X_CI Q10) L'_CI(1-0)` of 2025ApJ...987..158F, so it includes helium; for H2 only,
     divide it by 1.36 (coefficient about 1012) or use the 9.51e-5 form. 2021ApJ...909..181L writes
     mu = 1.36 into its [CI] equation.
   - Q10 depends on the [CI] excitation temperature: Tex = 30 K in 2017MNRAS.466.2825B and
     2018ApJ...863..143C; Q10 = 0.457 at 29.1 K in 2024ApJ...977..198L; 2021A&A...645A.120F adopts a median
     Q10 = 0.48 (its 40 K is a dust temperature). Q10 cannot be measured without both [CI] lines, so it is
     assumed (Q10 = 0.35 in 2021ApJ...909..181L).
   - Pick X_CI and alpha_CO as a pair: [CI] plus CO only constrain their product. 2025ApJ...987..158F finds
     X_CI x alpha_CO = 5.1e-5 (median, 0.12 dex scatter), so X_CI = 5.1e-5 goes with alpha_CO = 1 and, by
     calculation, about 1.4e-5 with alpha_CO = 3.6. 2023ApJ...953...75H uses matched sets (3.6,
     X_CI = 10^-4.8, Q10 = 0.35 for normal galaxies).
   - [CI](2-1): the same form with the 2-1 constants, also helium-inclusive:
     `M_mol = 1375.8 D_L^2 (1+z)^-1 (X_CI/1e-5)^-1 (A21/1e-7)^-1 Q21^-1 S_CI(2-1) dv`, with
     A21 = 2.68e-7 s^-1 and Q21 = 0.57 in 2016A&A...591A..73G. Q21 is far more temperature-sensitive than
     Q10 (2024A&A...685A.138V (card) tested 0.05-0.4); better, derive it from an LVG fit to the CO ladder
     (Q21 = 0.13 +/- 0.05 for the BCG and 0.03 +/- 0.02 for the tail in 2024A&A...689A..67G).
   - Dust RJ continuum: M_mol = L_nu(850 um rest) / alpha_850, alpha_850 = 6.7e19 erg/s/Hz/Msun calibrated
     at Td = 25 K, beta = 1.8 (2016ApJ...820...83S, 2017ApJ...837..150S, 2017A&A...606A..17M (card)).
     Before using it, check (a) the observed point is at lambda_rest > 250 um (2020MNRAS.498.4109J applied
     the estimator only to such points), (b) the emission is optically thin RJ (2025ApJ...987..158F assumes
     this for its 3 mm continuum), and (c) say how you got L_nu(850 um rest): the assumed Td and beta, or an
     SED fit, plus the temperature correction B_nu(850, 25 K)/B_nu(850, Td) (2026ApJ..1001..131C (card)
     took L_850 from a CIGALE fit). The calibration carries a Galactic alpha_CO = 6.5 (2016ApJ...820...83S,
     2017ApJ...837..150S); against CO at alpha_CO = 1, SMGs give alpha_850 = 2.4e20 in 2025ApJ...987..158F.
     It was calibrated on high-stellar-mass galaxies, not low metallicity (2016ApJ...820...83S): validate
     before using it on dwarfs. Remove non-dust continuum first (2024ApJ...977..198L subtracted synchrotron
     for one QSO and could not for another); if you cannot, propagate it or call the mass an upper limit.
   - 13CO LTE: N(13CO) from Tex (from optically thick 12CO) and tau, then H2/13CO = 1.4e6 to 5e6
     (2024ApJ...964..166K, 2016ApJ...831...32N, 2024ApJ...966...51G (card)); alpha_CO = M_LTE / L'_CO(1-0)
     (2.26 in 2017ApJ...848..101V). Use matched apertures and velocity components, test the 13CO opacity and
     the shared Tex and filling-factor assumptions (2017ApJ...848..101V used Tex = 15 K, filling factor 0.1
     and a finite-opacity correction). 2017ApJ...848..101V says its LTE mass traces only part of the total
     molecular mass in that BCG; whether an LTE alpha_CO is a lower bound for your source depends on the
     abundance, opacity and excitation you adopt, so state it as conditional, not guaranteed.
6. **Derive the quantities you need.** Sigma_H2 with a cos i deprojection (2025ApJ...995..151Y (card)); in
   nearby disks Sigma_H2 = 4.2 I_CO(1-0) with helium (2019A&A...623A..66B). f_gas = M_gas/(M_gas+M*)
   (2019ApJ...887...74F, 2025ApJ...985..194P); t_dep = M_gas/SFR (2014ApJ...783...84S). Add H I from a
   measurement when you have one. Assumed ratios are sample-specific (H2/HI = 0.3 in 2020ApJ...889....9M;
   HI = 50% of H2 only for the local calibration sample of 2014ApJ...783...84S; HI = H2/5 in
   2020A&A...636A..37D (card)). Justify any assumed ratio for your population.
7. **Write the error budget.** Statistical flux error plus flux-calibration error in quadrature (10% in
   2016ApJ...828...46A; 5% in 2023A&A...673A..46B; 30% conservative for ACA Band 8 in 2020ApJ...897L..19M).
   Include distance (L scales as D^2; median distance uncertainty about 7% in 2022MNRAS.510.4998Z) and, for
   lensed sources, magnification uncertainty when they are material. Then state the systematic alpha_CO
   and r_J1 terms separately (0.3 dex added on M_mol in 2018ApJ...853..195W; 50% on alpha_CO/R21 in
   2025A&A...698A.296R (card); +/-0.20 dex in 2021A&A...652A..98G; 0.5 dex on alpha_CO = 0.86 in
   2014ApJ...790..160S). Say which terms are left out: 2018ApJ...869...27V excludes gas-mass systematics,
   2025A&A...694A.218B leaves its r41 = 1 assumption unaccounted.

## Parameter defaults and ranges

Counts are distinct bibcodes among the pack's printed "Key parameters" and "Assumptions" entries (700 each,
340 and 352 distinct bibcodes, 450 combined of 876 papers; both lists are truncated), matched by regex, so
they are lower bounds. Method, full ranges and longer example lists: `references/parameters.md`.

| Parameter | Common choice | Range seen | Count | Examples |
|---|---|---|---|---|
| alpha_CO, Galactic (incl. He) | 4.3-4.4 | 4.3, 4.35, 4.36, 4.4 used interchangeably | 46 | 2017ApJ...835..278S, 2021A&A...656A..60A, 2023A&A...673A..46B (4.3 +/- 1.3) |
| X_CO, Galactic (no He) | 2e20 | 1.8e20 to 4.7e20 | 39 | 2014ApJ...784...78R, 2018ApJ...865...13T, 2024ApJ...963....1O; 4.7e20: 2017ApJ...846...73T (card) |
| alpha_CO, ULIRG / merger / SMG / QSO | 0.8 | 0.6 to 1.5 | 46 | 2017ApJ...843...18V, 2024ApJ...977..198L; 1.0: 2025ApJ...987..158F; 1.1: 2019ApJ...881...43K |
| alpha_CO, high-z star-forming | 3.6 | 3.6 to 10.8 scaled with M* | 10 | 2020ApJ...902..109B, 2023ApJ...953...75H, 2020ApJ...902..113I (3.6/7.2/10.8) |
| alpha_CO, Scoville | 6.5 | | 2 | 2016ApJ...820...83S, 2017ApJ...837..150S |
| alpha_CO, low Z | scale with Z | 8 to 110 | | 4.35 Z'^-1.6 (2021A&A...650A.134P); 17 at 12+log(O/H)=8.3 (2025A&A...700A.165B (card)) |
| alpha_CO, outflows | 0.8; thin 0.34 lower bound | 0.13 to 3.4 | | 2018ApJ...863..143C (2.1 +/- 1.2), 2018A&A...612A..29B (0.13-0.8), 2018ApJ...867..111Z (0.34) |
| r21 | 0.7-0.8 | 0.4 to 1.2 ordinary; 1.12-1.4 nuclei/outflows; 3-4 optically thin; 2.2-2.5 adopted for an AGN CND/torus | 70 | 2020MNRAS.498.1560J (0.4-1.2), 2018ApJ...863..143C (1.4), 2018ApJ...867..111Z (3-4), 2019A&A...632A..61G (card) |
| r31 | 0.5-0.8 | 0.27 to 1.0 in galaxies; 2.0-2.9 adopted for AGN tori | 38 | 2021A&A...656A..60A (0.27), 2022MNRAS.514.2346K (0.55, 1.0), 2021A&A...652A..98G |
| r41 | 0.4-0.6 | 0.22 (CGM tail) to 1 (QSO) | 15 | 2024A&A...689A..67G (0.22), 2018Natur.556..469M (0.41, card), 2020MNRAS.493.3744F (1) |
| r43 | 0.6-0.91 | 0.46 to 0.91 | | 2019MNRAS.487.4305S (card) |
| r61, r71 | comparison SLED | 2020A&A...636A..37D (card) SLEDs: r61 0.34/0.64, r71 0.16/0.48 (SMG/QSO); adopted r71 0.1 to 0.65 | | 2025A&A...695A..23S (r61 0.92, r71 0.65), 2026ApJ...997..218A (r71 0.60 or 0.1) |
| X_CI | 3e-5 | 1e-5 to 8.4e-5 | 10 at 3e-5 | 2017MNRAS.466.2825B, 2021A&A...645A.120F; 8.4e-5: 2024ApJ...977..198L |
| [CI] Tex | 30 K | 25 to 31.8 K | | 25 K: 2025ApJ...993L..40S; 31.8 K: 2025A&A...696A..83A; 26 K adopted from literature with the ratio 0.47: 2021A&A...654L...8C |
| Q10 | 0.46-0.48 | 0.35 to 0.6 | | 2021A&A...645A.120F, 2025ApJ...987..158F, 2021ApJ...909..181L |
| CO/H2 | 1e-4 | 1.6e-5 to 7e-4 (clouds, disks); 1e-3 in C-rich merger ejecta | 23 | 2021A&A...648A..41V, 2019PASJ...71...44H, 2018MNRAS.481.4931E |
| Helium factor | x1.36 | | 32 | 2018ApJ...853..149S (card), 2021ApJ...909..181L |
| alpha_850 | 6.7e19 erg/s/Hz/Msun | 6.7e19 to 1e20; 2.2e20-2.4e20 for SMGs with alpha_CO = 1 | 5 | 2017ApJ...837..150S, 2017ApJ...844..123F, 2022ApJ...929..100K, 2023MNRAS.524..923Z, 2025A&A...694A.218B |

## Software

The conversion is nearly always custom code. The pack's aggregate names casa (79), radex (26),
emcee (23), cprops (15), linmix (11), PDR Toolbox and cloudy (8 each) and pyspeckit (3) for extraction,
excitation and cloud work; the table with aliases is in `references/parameters.md`.

## Pitfalls

- **Helium double counting.** 4.35 already includes 1.36; X_CO = 2e20 in N(H2) does not; the 1.05e4 form
  of Step 2 and the 1375.8 [CI] forms of Step 5 do. Check each paper: 2016NatSR...626896A (card) excludes
  helium, 2020ApJ...902..109B divides M_mol by 1.36 to get M_H2, 2022MNRAS.517..632L states its
  X_CO = 2e20 includes helium.
- **alpha_CO per transition.** alpha_CO(2-1) = alpha_CO(1-0)/r21: 4.35, 6.25 and 17.4 for 1-0, 2-1, 3-2 in
  2018ApJ...860..172S (card); 6.2 for 2-1 in 2018ApJ...868L..38G; 9.3 vs 4.2 measured in 2024ApJ...964...18C.
- **Flux ratio vs brightness ratio.** 2018ApJ...865...13T assumes CO(2-1)/CO(1-0) = 3.2 and
  2017A&A...602A..11P a 3-2/1-0 flux ratio of 9: these are flux-density ratios. S_J/S_1 = r_J1 x J^2 for
  CO, so using the flux ratio as r_J1 underestimates L'_CO(1-0), and the mass, by 4 (2-1) or 9 (3-2).
  Cluster papers adopt S(2-1)/S(1-0) = 3.2 and S(3-2)/S(1-0) = 7.2 "in flux density scale"
  (2023PASJ...75..925F, 2024ApJ...964...29F), which is r21 = r31 = 0.8.
- **Ratio direction.** R_13 = 1.9 in 2021ApJ...909..181L and R14 = 1.1 in 2025A&A...696A..83A are 1-0 over
  the higher line; 2025A&A...694A.218B writes r41 = L'(1-0)/L'(4-3). A ratio above 1 is an inverse ratio,
  a flux-density ratio, optically thin gas or a genuinely super-thermal value; find out which.
- **Galactic alpha_CO in starbursts or nuclei.** Nuclear values of 1/4 Galactic in 2014A&A...567A.125G and
  2019A&A...632A..33A. The 6.5 (Scoville, 2016ApJ...820...83S) and about 0.8 (2016A&A...594A..81P (card)
  uses 0.78) conventions differ by a factor of about 8 by calculation, not by a statement in those papers.
- **Model-dependent alpha_CO.** RADEX alpha_CO scales as 1/x_CO, which 2024ApJ...971..176H says the
  modelling cannot constrain (factor-of-3 per-pixel uncertainty). An optically thick reference cloud can
  overestimate alpha_CO by a factor of a few (2025ApJ...995L..51G).
- **Mid-J only.** The SLED shape is a large assumed term: CO(5-4)/CO(1-0) = 0.23 carries a factor-2
  uncertainty in 2016ApJ...819...82S (card), r61 and r71 differ by factors 2-3 between the SMG and QSO SLEDs
  of 2020A&A...636A..37D (card), and adopted r71 runs from 0.1 to 0.65 (2026ApJ...997..218A,
  2025A&A...695A..23S). Test alternatives (2015ApJ...812L..23S (card)) and budget the SLED term.
- **Missing short spacings and continuum subtraction.** Interferometric masses can be well below
  single-dish (Step 1); uv-plane over-subtraction removes line flux (2018MNRAS.479.5440L).
- **CMB at high z.** Not correcting can bias masses low by about 2x (2018ApJ...856...72O); 2017MNRAS.466..138K
  (card) assumes half the intrinsic flux is missed. RADEX models in 2025ApJ...987..158F show the CMB can
  lower L'[CI]/L'CO by up to about 30% and change cold-gas masses by up to 70%. State your f_CMB.
- **Low metallicity and CO-dark gas.** 2016A&A...586A..45S (card) applies a CO-dark correction; dark-gas
  X_CO of 14e20 in 2020ApJ...889L...4L (card). Ionised-gas metallicity may not be that of the molecular gas
  (2015ApJ...812L..23S (card)).
- **[CI] assumptions.** Masses scale as 1/X_CI and depend on Tex through Q10 (much more strongly through Q21);
  2021A&A...645A.120F notes its errors exclude X_CI, Q10 and A10; 2020ApJ...897L..19M found [CI] an order
  of magnitude below the CO relation; [CI] can be optically thick (tau about 10 in 2019ApJ...885L..39H).
- **Lensing.** 2017MNRAS.466.2825B discusses differential lensing (dust-based lens models applied to [CI]);
  2018A&A...620A.115B (card) assumes it negligible. Do not reuse a dust magnification for line ratios
  without saying so.
- **Optically thin limits and blends.** Masses may be an order of magnitude lower if 12CO is optically thin
  (2014ApJ...797...90S). Unresolved companions likely inflate [CI] fluxes in two SMGs of 2025ApJ...987..158F.
- **Unstated settings** most often flagged by the cards (rebuilt aggregate): CASA version (40), continuum
  subtraction and line-free channels (24, plus several other wordings), flux calibrator and flux-scale
  uncertainty (19), self-calibration intervals (16). Cards rarely state whether alpha_CO includes helium or
  which aperture r_J1 was measured in.

## Verification checks

What the papers did:

- **Single-dish flux comparison** (2018ApJ...863..143C; 2024A&A...689A..67G NRO 45 m vs ALMA consistent;
  2021A&A...656A..60A 40-50% missing).
- **Independent tracers compared**: three tracers ([CI], CO(4-3), dust) in 2024ApJ...977..198L, which warns
  of large parameter uncertainties. Documented agreement: dust vs CO median 0.23 dex in 2021A&A...652A..98G;
  LTE vs X_CO masses KS p = 0.52 in 2024ApJ...964..166K; [CI] vs CO(3-2) -0.14 dex and [CI] vs dust
  0.02 dex in 2021ApJ...909..181L. Check the tracers see the same gas (CO/[CI] line-width ratio
  1.0 +/- 0.1 in 2025ApJ...987..158F).
- **Dynamical mass budget**: 2018MNRAS.479.5440L found M_bar = (3.4 +/- 2.0)e11 Msun against
  M_dyn = (0.9 +/- 0.3)e11 at 4 kpc and (1.8 +/- 0.6)e11 at 8 kpc; 2024ApJ...970...30M set the maximum
  alpha_CO from M_dyn. Match the enclosed radii before using M_dyn as a ceiling.
- **Vary the assumptions** and report the spread: r43 0.91 and 0.46 (2019MNRAS.487.4305S (card)), alpha_CO
  0.35 to 4.35 (2025ApJ...992L...7S (card)), constant vs metallicity-dependent alpha_CO
  (2021A&A...650A.134P), Q21 limit (about 30% in 2024A&A...689A..67G), region size (2023A&A...673A..46B).
- **Extraction robustness**: 2024ApJ...963....1O (card) got 0.88-2.5 Jy km/s with natural weighting
  depending on binning; fit vs direct sum (2020ApJ...902..109B).
- **Gas-to-dust sanity**: about 30 with alpha_CO = 0.8 vs about 95 at solar in 2019ApJ...877L..38R (card);
  2024ApJ...971..176H used a gas-to-dust ratio of about 100 to support its x_CO.

What a careful referee adds:

- Recompute L' and M from the quoted S dv, nu_obs, D_L, z, r_J1 and alpha_CO; check units and helium.
- Confirm r_J1 is a brightness-temperature ratio from matched apertures and uv coverage (general
  practice; 2024ApJ...964..166K notes its comparison depends on R21 and resolution differences).
- Ask for masses at both Galactic and ULIRG alpha_CO when the environment is ambiguous.
- Check that limits use the same width, r_J1 and alpha_CO as detections, and that the rms belongs to the
  aperture used.

## Source cards

Full list: `references/sources.md`. Most informative here: 2018ApJ...863..143C ([CI] alpha_CO for outflow
and quiescent gas), 2017MNRAS.466.2825B ([CI] masses at z~4), 2024ApJ...964...18C (resolved dust alpha_CO),
2017ApJ...848..101V (13CO LTE in a BCG), 2015ApJ...812L..23S (dynamical alpha_CO), 2024ApJ...977..198L
(three tracers), 2021ApJ...909..181L ([CI], CO(3-2), dust in a protocluster), 2024ApJ...971..176H
(per-pixel RADEX alpha_CO), 2025ApJ...987..158F ([CI] vs CO cross-calibration, alpha_850, CMB),
2024A&A...689A..67G ([CI](2-1) with LVG Q21), 2025ApJ...995L..51G (Galactic centre alpha_CO),
2018MNRAS.479.5440L (continuum check and mass budget), 2014ApJ...783...84S (alpha_850 calibration).
