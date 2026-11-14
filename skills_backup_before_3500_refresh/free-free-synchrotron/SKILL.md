---
name: alma-free-free-synchrotron
description: "Separate thermal dust, free-free (bremsstrahlung) and synchrotron emission in ALMA continuum, and turn the separated components into physical quantities: free-free fraction, ionizing photon rate and SFR, HII region emission measure and density, electron temperature from radio recombination lines, ionized jet mass-loss rates, and synchrotron magnetic fields or spectral ages. Use when an ALMA band (often Band 3, but also Band 6/7 in HII regions and starbursts) may contain non-dust emission, when combining ALMA with VLA/ATCA cm data, when asked for a free-free or thermal fraction, an RRL-based Te, or whether a compact mm source is dust, an HII region, a jet or a synchrotron core. Built from 119 ALMA papers (2013-2026)."
---

# Separating free-free, synchrotron and dust continuum

Splits the mm/cm continuum into dust (S ∝ nu^(2+beta) only when optically thin AND on the Rayleigh-Jeans tail;
otherwise S ∝ kappa_nu B_nu(T_d), see 2018ApJ...853..171G, who qualify alpha = 3.75 this way), free-free (flat,
nu^-0.1, when optically thin; rising up to nu^2 when thick) and synchrotron (falling, nu^-0.5 to nu^-0.9), then uses
each piece for physics. The two mistakes that matter most: (1) assuming all ALMA continuum is dust, when the
decompositions of three starburst nuclei put Band 3 at 70-84% free-free (2016MNRAS.463..252B, 2015MNRAS.450L..80B,
2017ApJ...849...90S; model-dependent estimates for those sources, not a default for other galaxies) and 0.88 mm in
30 Dor clumps at 50-85% free-free (2025A&A...699A.369V); and (2) quoting a component fraction as if it were measured
when it is set by a fixed spectral index you chose (2015ApJ...813..118M, 2017ApJ...849...90S says its fit "is not
unique").

Counts below are from the `free-free-synchrotron` evidence pack: either its aggregates (said so) or my own count of
its per-paper lines. The pack was tagged by regex on words like "HII region" and "recombination", so roughly a dozen
of its 119 papers are off-topic for decomposition (for example HII-region metallicity gradients, 2020MNRAS.499..193K,
or molecular-ion abundances, 2019A&A...622A..26G). I ignored those when counting.

For alpha maps, the alpha-to-beta conversion and grain-growth arguments, use the `spectral-index` skill. This skill
only covers getting the non-dust part out first, and what the non-dust part tells you.

## When to use

- Band 3 (85-115 GHz) continuum of starbursts, galaxy nuclei or Galactic HII regions, where free-free can dominate
  (fractions above; the aggregates list 32 nearby_galaxies and 53 star_formation papers).
- Dust masses of cores, clumps or disks near massive stars or HII regions, where free-free must come off first
  (2024ApJ...967...15K, 2015A&A...577A..30A, 2019MNRAS.483.1624B, 2016ApJ...833L...6C).
- ALMA plus VLA/ATCA SEDs of protostars and disks, to find ionized jets or winds at 1-5 cm (2021A&A...653A.117B,
  2024A&A...684A.134R, 2017A&A...602A..19L, 2019ApJ...884...97L).
- Radio recombination lines (H29alpha to H42alpha) for Te, kinematics or ionizing photon rate
  (2016MNRAS.463..252B, 2015MNRAS.450L..80B, 2024ApJ...967...15K, 2018ApJ...864L..17G, 2014ApJ...791...95A).
- Star formation rates or Q_Lyc from mm free-free (2017ApJ...849...90S, 2018ApJ...869..126L, 2016ApJ...833L...6C).
- AGN cores, radio galaxies, SNRs and PWNe where ALMA sits on a synchrotron spectrum (2019A&A...621A..27F,
  2020A&A...634A...9M, 2020MNRAS.496.1834L, 2014ApJ...796...82Z, 2025A&A...699A..62J).
- Stellar flares and coronae (gyrosynchrotron) (2018ApJ...855L...2M, 2020ApJ...891...80M, 2019ApJ...881...33H).

## When not to use

| Situation | Use instead |
|---|---|
| You already know the emission is dust and want alpha or beta, or grain growth | `spectral-index` |
| Dust mass from a single band once free-free is removed (kappa, T, gas-to-dust) | `dust-continuum-mass` |
| Full far-IR to radio SED with T_dust, stellar mass, SFR (CIGALE, MAGPHYS, MR-MOOSE) | `sed-fitting` (radio modules are a small part of it; 2017A&A...606A..17M, 2021A&A...646A.127H) |
| GRB, TDE, FBOT or blazar afterglow synchrotron light curves | `variability-time-domain` (2018ApJ...862...94L, 2023NatAs...7...80U are in this pack but are shock modelling, not decomposition) |
| Solar chromosphere brightness temperatures (thermal free-free as an atmospheric probe) | treat as atmospheric inversion; this pack has 8 sun papers (aggregate), e.g. 2017A&A...605A..78A, 2018ApJ...863...96Y; the recipes below do not transfer |
| Continuum subtraction for line cubes | `continuum-subtraction` |
| You need the free-free model in the uv plane (sizes, offsets) | combine with `uv-plane-fitting` (2014ApJ...796...82Z subtracted templates with MIRIAD uvmodel) |

## Steps

1. **Decide which components can matter at your frequency.**
   - Goal: avoid both "all dust" and "all free-free" by default.
   - Evidence of the size of the effect: free-free is 84 ± 10% of 85.69 GHz in NGC 4945 (2016MNRAS.463..252B), 70 ± 10%
     of 99 GHz in NGC 253 (2015MNRAS.450L..80B), 0.72 of 93 GHz in NGC 1808 with synchrotron 0.22 and dust 0.06
     (2017ApJ...849...90S), 6.7 of 9.7 mJy at 870 um in II Zw 40 (2016ApJ...833L...6C, card), 47-100% at 32.9 GHz in
     5 of 16 OMC-2/3 protostars (2021A&A...653A.117B). Synchrotron and free-free were below 5% at 220 GHz in NGC 253
     (2016ApJ...821..112K).
   - In AGN-hosting radio galaxies synchrotron can reach ALMA bands; MR-MOOSE was run with synchrotron without a
     cutoff to get the maximum contribution (2019A&A...621A..27F).
   - If you have only one ALMA band and nothing at cm wavelengths, say the decomposition is assumed, not measured
     (2015ApJ...813...45L assumed 100% dust at 345 GHz and gave a factor-of-5 uncertainty).

2. **Build a matched multi-band SED.**
   - Goal: fluxes that measure the same structure in every band.
   - Method: every band needs (a) compatible spatial filtering, (b) a common resolution, (c) registered images on one
     grid, (d) the same apertures and (e) consistent flux units (Jy, not Jy/beam at different beams). Convolving and
     regridding fixes (b)-(c) but not missing flux; a matched uv range helps (a) but is not a guarantee when uv
     density differs. Examples: 2015ApJ...813..118M convolved 94.5 GHz to the 33 GHz beam and regridded (card,
     section 3.1); 2017MNRAS.467L.120M used a matched uv range of 40-610 klambda. Missing flux still bit
     2018ApJ...860....9M (knot D has no Band 3 limit because of the limited largest angular scale). State any
     remaining mismatch and which way it biases the slope.
   - Record per-band absolute calibration errors (3% at 33 GHz and 5% at 94.5 GHz in 2015ApJ...813..118M, card,
     section 2.4) and add them to the fit; 2021A&A...656A..46M notes its fit errors left the calibration term out.
   - For variable sources, use simultaneous epochs; 2019ApJ...881L...2B flagged an 868 GHz point taken four days
     away, longer than the source's variability coherence time.
   - Software: CASA (13 matched steps in the aggregates), `imfit` for compact components (2 in the aggregates;
     2024ESC.....8..665M fit two 2D Gaussians to a hot core and a UC HII region).

3. **Choose a decomposition method.** Six patterns appear in the pack (my reading of the excerpts):

   | Method | What it needs | Examples |
   |---|---|---|
   | Sum of power laws with all indices fixed, free amplitudes, least squares | 3+ bands spanning cm to submm | 2017ApJ...849...90S (alpha_s = -0.9, alpha_ff = -0.1, alpha_d = 3.8; the authors call the fit "not unique") |
   | Sum of power laws with a free synchrotron index | 3+ bands, enough low-frequency points to fit the slope | 2016MNRAS.463..252B (three components: synchrotron index free, free-free with a temperature-dependent Gaunt factor at Te 5000 K, dust index 4; Monte Carlo errors); 2015MNRAS.450L..80B refit an earlier SED letting the synchrotron slope vary |
   | Two-band per-pixel algebra | Band 3 + Band 6 maps, adopted beta | 2019MNRAS.483.1624B: S_B6 = S_d + S_ff and S_B3 = S_d (nu3/nu6)^(2+beta) + S_ff (nu3/nu6)^-0.1, solved per pixel with beta = 1.49 (the nu^(2+beta) form assumes optically thin Rayleigh-Jeans dust; for warm-dust-poor or cold regions use kappa_nu B_nu(T_d)) |
   | Extrapolate free-free from a cleaner tracer and subtract | a band or line where free-free dominates | 3 mm scaled to 870 um with index -0.118, assuming synchrotron and dust negligible at 3 mm (2016ApJ...833L...6C; index from the card, section 4.1); Brgamma to Halpha to free-free at 338.5 GHz (2025A&A...699A.369V); H29alpha-based free-free at 256 GHz removed before dust mass (2024ApJ...967...15K) |
   | Bayesian multi-component SED (MCMC) | many bands, priors | MR-MOOSE + emcee with AGN, modified blackbody and synchrotron (2019A&A...621A..27F); emcee with dust slabs plus free-free (2019ApJ...884...97L) |
   | Template subtraction in the uv plane | a high-resolution template band | scaled 44 GHz and Band 9 models removed with MIRIAD `uvmodel`, scaling tuned on the brighter lobe to avoid over-subtraction (2014ApJ...796...82Z; the authors found the double-subtracted images unusable because of errors, so propagate the template scaling uncertainty before reading anything into residual components) |

   Recommendation: use the fixed-index power-law sum only together with an index-sensitivity test (see Verification
   checks: refit with alpha_NT at least at -0.6 and -0.9, and Te at 5000 and 10000 K, and report how far the
   free-free fraction moves); use the per-pixel two-band method only with an independent check against cm data, as
   2019MNRAS.483.1624B did with ATCA 4.8/8.4 GHz (card, section 3.1: within 15 per cent in 30 Dor, N159W consistent,
   N159E about 4x too much free-free; they adopted the method anyway).

4. **Model the free-free component physically when it is resolved or optically thick.**
   - HII regions: fit the turnover frequency (tau = 1) and size with Te fixed at 10^4 K, then emission measure from
     tau = 1, and N_Lym from the 23 GHz flux compared with ZAMS tables, assuming a cylindrical homogeneous HII region
     at D = 3.25 kpc (2015A&A...577A..30A). With one band and a line, use Mezger-Henderson relations for n_e, EM,
     ionized mass and Lyman photons, assuming a spherical homogeneous region (2024ApJ...967...15K, whose quoted
     errors leave out the distance uncertainty and density gradients). State the geometry you assumed, and report how
     the derived n_e, EM, mass and photon rate shift with distance and with a density gradient, next to the formal
     errors.
   - Photoionized outflows: grid of isothermal bipolar cavity models with n ∝ r^-2, chi2 over Te (5e3-2e4 K),
     n0 (3e6-3e8 cm^-3), launch radius (30-300 au) and opening angle, fitted at 1.3 and 7 mm together
     (2019ApJ...886L...4Z; best Te about 10,000 K, model fluxes within 5%). The authors say the true opening angle and
     inclination are only weakly constrained.
   - Ionized shells: spherical shell radiative transfer, Ne and R fitted for Te = 1e4 to 2e4 K and DeltaR/R from
     0.05 to 1 (2014ApJ...791...95A). Good continuum fits were obtained for every Te and shell-width combination, so the
     continuum alone did not pick Te or geometry; the NLTE recombination lines did (Te about 1.7e4 K, DeltaR/R about
     0.1), and the authors note that departures from spherical symmetry would make the solution degenerate.
   - In general a good continuum fit does not determine geometry or temperature uniquely. Report the degeneracies
     (which parameter combinations fit equally well) and what extra constraint (lines, resolution, another band)
     broke them.
   - Ionized jets from YSOs: Reynolds (1986) jet model with T = 1e4 K, nu_m = 40 GHz, theta_min/theta_maj = 0.5,
     v_jet = 140 (M*/0.5 Msun)^0.5 km/s, jet perpendicular to the disk (2024A&A...684A.134R; median ionized to
     total mass-loss ratio 0.019).
   - Stellar winds: Te = 0.5 Teff with mean ionic mass, ionization and electron number per spectral class
     (2018A&A...617A.137F).
   - General practice (not from the pack): optically thin free-free tau_ff ≈ 3.28e-7 (Te/1e4 K)^-1.35
     (nu/GHz)^-2.1 (EM / pc cm^-6), so tau = 1 near 100 GHz needs EM of about 5e10 pc cm^-6 at 1e4 K. Check that
     your ALMA band is above the turnover before using the -0.1 index.

5. **Use recombination lines when you have them.**
   - Te from the line-to-continuum ratio after scaling the continuum by the free-free fraction (2016MNRAS.463..252B,
     84 ± 10%; 2015MNRAS.450L..80B, 0.70 ± 0.10). 2016MNRAS.463..252B states its emissivities: Storey and Hummer,
     case B and a fixed n_e = 1e3 cm^-3 (the 2015MNRAS.450L..80B excerpt does not give these settings; its card
     lists the emissivity values as not stated). Results: 5400 ± 600 K in NGC 4945 (2016MNRAS.463..252B),
     8094 ± 1534 K in a HC HII region (2024ApJ...967...15K).
   - Non-LTE and maser effects matter for compact, dense regions: 2014ApJ...791...95A fit H and He lines in NLTE
     (poorer fit for H40alpha and H42alpha); 2019ApJ...886L...4Z left H30alpha non-LTE modelling out; RRL masers
     are variable (2020ApJ...897L..33J).
   - Kinematics: H41alpha centroids with `pyspeckit` gave HII-region velocity dispersions, checked against earlier
     VLA velocities to within 5 km/s for every source in common except F10.37 (2018ApJ...864L..17G).
   - He+/H+ = 0.08 is the usual adopted value (4 papers, my count: 2019ApJ...871..185L, 2025A&A...694A.166C,
     2019NatAs...3..517Z, 2025A&A...699A.369V); 0.096 in 2024ApJ...967...15K.

6. **Convert free-free to ionizing photons, then (with stated assumptions) to SFR or stellar mass.**
   - Assume the band is free-free dominated (or scale by the fraction) and pick Te: 5000 K at 93 GHz in NGC 1808
     (2017ApJ...849...90S), 7000 K at 36 GHz with all 36 GHz emission taken as free-free (2018ApJ...869..126L),
     13000 K in II Zw 40 (2016ApJ...833L...6C).
   - General practice (Murphy et al. 2011 form, not quoted in the pack): Q(H0) ≈ 6.3e25 s^-1 (Te/1e4 K)^-0.45
     (nu/GHz)^0.1 (L_nu,ff / erg s^-1 Hz^-1). The Te dependence is weak, but state the Te you used.
   - What this Q is: the photon rate needed to keep the observed gas ionized, assuming ionization equilibrium (every
     ionizing photon absorbed by hydrogen inside the region). It is a lower limit on the stars' intrinsic production
     rate when photons escape or are absorbed by dust; 2020ApJ...903...29M flag photon escape in evolved regions. Any
     correction needs its own justification: 2016ApJ...833L...6C (card, step 2) estimated that 72% of Lyman continuum
     photons ionize hydrogen (Inoue et al. method), the rest being lost to dust, and corrected N_Lyc for that.
   - Q to SFR depends on the IMF and the star formation history, so name both. Options seen: SFR = 5.41e-54 Q
     (Msun/yr, Q in s^-1; Starburst99, 2016MNRAS.463..252B, card section 7.1); the Murphy et al. (2011) free-free
     calibration, used by 2017ApJ...849...90S (card), which in its usual form is SFR ≈ 4.6e-28 (Te/1e4 K)^-0.45
     (nu/GHz)^0.1 L_nu,ff (erg s^-1 Hz^-1), for a Kroupa IMF and constant star formation over 100 Myr (the formula is
     general practice, not quoted in the pack). Constant-SFR calibrations do not apply to a single young burst or
     to one HII region; there convert Q to stellar mass instead. 2018ApJ...869..126L used M* = Q0/4e46 Msun from a
     Starburst99 zero-age population of 1e6 Msun with a Kroupa IMF up to 100 Msun (card). The pack also has
     Chabrier-IMF work (2017A&A...606A..17M, 2021A&A...646A.127H), so check which IMF your comparison sample used.

7. **Model synchrotron when it is the science.**
   - Minimum-energy field: classical equipartition with c12 = 3.2e6 and k = 40, on pixels with alpha < -0.3 and
     > 5 sigma in both bands, as an upper limit if all emission is synchrotron (2019ApJ...886L...4Z, 15-17 mG).
     Self-absorbed coronae: an order-of-magnitude estimate with magnetic energy in equipartition with the photon field
     gave B of about 100-300 G and sizes of 100-200 R_g in one scenario among several tested (2025A&A...699A..62J);
     the authors say detailed SED modelling is needed to actually constrain B. Treat such numbers as
     scenario-dependent estimates.
   - Flat-spectrum components: 2014ApJ...796...82Z warn that equipartition B estimates for a flat-spectrum (PWN-like)
     component may be inaccurate. Propagate the template and scaling uncertainties from the subtraction (step 3)
     before interpreting any residual component.
   - Spectral ageing: CI and CI_OFF models in `SYNAGE++` with Jaffe-Perola losses, B fixed (2.6 uG for lobes),
     chosen by reduced chi2 (2020A&A...634A...9M). Break frequency plus remnant age gives B (2020MNRAS.496.1834L,
     3.9e-4 G).
   - Gyrosynchrotron flares: optically thin alpha = 1.22 - 0.9 delta (2018ApJ...855L...2M, delta = 3.32 ± 0.83;
     2020ApJ...891...80M, delta = 2.80 ± 0.06).
   - Thermal synchrotron (Sgr A*): one-zone uniform sphere of fixed 40 uas angular diameter with constant n, Te and B;
     emcee default sampler with logarithmic priors on n, Te and plasma beta (B follows from n and beta, so it has no
     independent prior), bounds Te >= Tb and 1e-3 < beta < 1e3; relativistic effects and radiative cooling neglected;
     refit without the Herschel points as a check (2019ApJ...881L...2B). State the fixed size and these
     approximations with the result.

8. **Hand the dust residual on.** Free-free subtracted fluxes go to `dust-continuum-mass` (2024ApJ...967...15K,
   2015A&A...577A..30A) and multi-band dust residuals to `spectral-index`.

## Parameter defaults and ranges

Counts are my count of pack lines (parameters, assumptions, excerpts), off-topic papers excluded. A longer per-paper
list is in `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Electron temperature Te (fixed) | 1e4 K | 5000-20000 K | 18 | 1e4: 2015A&A...577A..30A, 2024A&A...684A.134R, 2021A&A...656A..46M; 5000: 2016MNRAS.463..252B, 2017ApJ...849...90S; 8000: 2019ApJ...871..185L; 16000: 2017A&A...602A..19L |
| Optically thin free-free index | -0.1 | -0.118 to -0.1 | 7 | 2020A&A...640A..27V, 2019MNRAS.483.1624B, 2024A&A...687A.163B, 2025ApJ...991...53C |
| Partially thick jet or wind free-free index | 0.6 | 0.6-1 | 2 | 2017ApJ...840...32T (0.6), 2018MNRAS.478.2505I (1) |
| Synchrotron index (fixed) | -0.8 | -0.5 to -0.9 | 8 | -0.7: 2015ApJ...802...69B; -0.8: 2017A&A...606A..17M; -0.85: 2015ApJ...813..118M; -0.9: 2017ApJ...849...90S |
| Dust index in the decomposition | alpha_d 3.5-4 or beta 1.5-1.9 | alpha_d 2.3-4; beta 1-2.5 | 15 (any dust index adopted next to a free-free step) | alpha_d 4: 2016MNRAS.463..252B; 3.8: 2017ApJ...849...90S; beta 1.49: 2019MNRAS.483.1624B; beta 1.75: 2018ApJ...853..171G |
| He+/H+ | 0.08 | 0.08-0.096 | 5 | 2019NatAs...3..517Z, 2024ApJ...967...15K |
| n_e for RRL emissivities | 1e3 cm^-3, case B | n/a | 1 | 2016MNRAS.463..252B |
| Thermal fraction at 1.4 GHz (SED codes) | 0.1 | n/a | 1 | 2017A&A...606A..17M |
| Free-free fraction at Band 3 in the three starburst nuclei studied (model-dependent estimates, not a default) | n/a | 0.70-0.84 | 3 | 2016MNRAS.463..252B (free synchrotron index), 2015MNRAS.450L..80B, 2017ApJ...849...90S (fixed indices, "not unique") |
| MCMC setup | emcee, uniform or log priors | 84 walkers x 1500 steps, 500 burn-in; 128 chains | 4 (aggregate: emcee) | 2019ApJ...884...97L, 2018ApJ...862...94L |
| Uncertainty floor on all fitted points | 10% | n/a | 1 | 2018ApJ...862...94L |
| Error assigned to specific datasets or points | 10-20% | n/a | 2 | 2016MNRAS.463..252B (10% on two datasets), 2019ApJ...881L...2B (20% on the non-simultaneous 868 GHz point) |

## Software

From the pack aggregates ("software named in the matched steps"); real use is higher because many cards name software
only in the reduction section.

| Software | Count | Used for |
|---|---|---|
| CASA | 13 | calibration, imaging, flux extraction |
| CASA `imfit` | 2 | Gaussian fits to compact free-free and dust sources (2024ESC.....8..665M) |
| emcee | 4 | SED and afterglow MCMC (2019ApJ...884...97L, 2019ApJ...881L...2B, 2018ApJ...862...94L) |
| CLOUDY | 2 | HII + PDR photoionization grids (2025ApJ...990...29H, with BPASS) |
| Starburst99 | 2 | ionizing photon to stellar population conversion |
| MR-MOOSE | 1 | multi-resolution AGN + dust + synchrotron SED (2019A&A...621A..27F) |
| Hyper | 1 | modified blackbody fit after free-free removal (2015A&A...577A..30A) |
| SYNAGE++ | 1 | synchrotron spectral ageing (2020A&A...634A...9M) |
| MIRIAD `uvmodel`, `uvfit` | 1 | uv-plane template subtraction (2014ApJ...796...82Z) |
| pyspeckit | 1 | RRL fitting (2018ApJ...864L..17G) |
| linmix | 1 | regression of ionized vs total mass-loss rate (2024A&A...684A.134R) |
| astropy.modelling | 1 | Gaussian clump models before free-free subtraction (2025A&A...699A.369V) |
| MAGPHYS, CIGALE | 1 each | panchromatic SEDs with a radio module (2017A&A...606A..17M, 2021A&A...646A.127H) |

## Pitfalls

- **The fixed indices set the answer.** Changing alpha_NT from -0.85 to -0.6 moved the mean 33 GHz thermal fractions
  over the nucleus, Enuc. 1 and Enuc. 2 from 85/82/70% to 80/76/62% (2015ApJ...813..118M; the -0.6 test is in the pack,
  the numbers are quoted in the card, section 3.1). 2017ApJ...849...90S calls its three-component fit not unique;
  2017A&A...602A..19L says its SED models are degenerate. Report the fraction with the index range you tried.
- **Two bands cannot split three components.** This is general reasoning (two fluxes, three unknown amplitudes), and
  authors say it: 2018ApJ...869..126L list as a limitation (card) that with 36 and 350 GHz alone they cannot
  distinguish free-free contamination at 350 GHz from synchrotron at 36 GHz. Without an intermediate frequency,
  synchrotron steepening cannot be tested (2019A&A...621A..27F).
- **Optically thick free-free.** The turnover can lie above your data: the MM1a fit was least robust because flux
  may keep rising past 25 GHz (2015A&A...577A..30A). Hypercompact HII regions and jets do not follow -0.1.
- **The RRL Te depends on the free-free fraction.** With no correction Te rose to 5800-7100 K; with a 50% fraction it
  fell to 2500-3000 K (2015MNRAS.450L..80B).
- **Missing flux differs by band.** Extended emission resolved out at one band but not another fakes a spectral
  slope (2015ApJ...801...82H, 2018ApJ...860....9M, 2016ApJ...821..112K on different uv coverage per transition,
  2025A&A...699A.369V without Total Power).
- **Variability and non-simultaneous data.** Accretion and free-free measured at different times (2024A&A...684A.134R);
  older periastron spectra used because new low-frequency data were missing (2019PASJ...71L...3F).
- **Line contamination of the continuum.** RRLs and molecular lines inside the continuum window dominated flux
  accuracy in 2020ApJ...903...29M; STATCONT continuum was not optimal for weak lines (2021A&A...656A..46M).
- **Calibration systematics.** CASA versions before 5.0 overestimated 7m mosaic fluxes by about 8% in Band 6 and 2% in
  Band 3, uncorrected in 2019MNRAS.483.1624B; 2015MNRAS.450L..80B allows for unidentified amplitude errors;
  2015ApJ...802...69B needed a Tsys correction for Sgr A*.
- **Uniform temperatures overestimate free-free.** 2024A&A...687A.163B assumed 100 K everywhere and warns free-free
  may be overestimated.
- **Other non-dust emission at 20-40 GHz.** Spinning dust (nu_pk = 21 GHz) was needed for PDS 70 (2024ApJ...972..163L);
  2015ApJ...813..118M assumed AME negligible.
- **Thermal contamination of a synchrotron core.** The Fornax A core result holds only if thermal emission is below
  about 80% at 108 GHz (2020A&A...634A...9M).
- **Ignoring free-free in dust masses.** 2020ApJ...896...35J did not remove it at 1.2 mm; 2015ApJ...813...45L did not
  correct for synchrotron. 2020A&A...640A..27V tested it with indices 2.3 and -0.1 and found it negligible; do that test.
- **What cards say is missing.** Summing the "Settings cards flag as needed but not stated" entries across their
  phrasings: self-calibration solution intervals 17 listed occurrences, CASA or pipeline version 15, line-free
  channels 13 (3 + 3 + 2 + 2 + 2 + 1) and flux scale uncertainty or flux calibrator 7. These are listed occurrences;
  the pack does not say whether one paper appears under two phrasings. State all four.

## Verification checks

What the papers did:
- Vary Te (3000-10000 K) and the fixed indices and report how much the free-free fraction moves (2016MNRAS.463..252B,
  at most 10%); vary alpha_NT (2015ApJ...813..118M, -0.85 and -0.6).
- Compare a decomposed free-free map with an independent extrapolation from cm data: in 2019MNRAS.483.1624B (card,
  section 3.1) ATCA-extrapolated and decomposed free-free agreed within 15 per cent in 30 Dor (0.82 vs 0.97 Jy) but
  N159E had about 4x too much decomposed free-free.
- Test the free-free level against optical or near-IR hydrogen lines: Halpha limits (2014ApJ...796...82Z),
  Brgamma (2025A&A...699A.369V).
- Compare model images, spectral index maps, SED and profiles with the data, not only total flux
  (2019ApJ...886L...4Z, within 5%).
- Refit with an extra point or without a dataset: 43 GHz for MM1a (2015A&A...577A..30A); without Herschel
  (2019ApJ...881L...2B).
- Compare Te or kinematics with Milky Way or earlier values (2016MNRAS.463..252B, 2018ApJ...864L..17G).
- Check residuals against the noise after template subtraction (2014ApJ...796...82Z).
- Cross-check ionized mass-loss against an independent tracer ([OI] HVC in 2024A&A...684A.134R).

What a careful referee adds:
- Propagate per-band calibration errors into the fractions, not only fit errors.
- Show the uv range or beam matching used for every ratio.
- State whether each band is above the free-free turnover, and why.
- For RRL Te, give the continuum fraction, n_e and case assumed, and whether non-LTE was considered.
- Report results for at least two plausible synchrotron indices.
- Say whether Q is the equilibrium (recombination-supported) rate or a corrected intrinsic rate, and which IMF and
  star formation history any SFR assumes.

## Source cards

All 119 papers are listed in `references/sources.md`. The most informative for this technique:

- 2016MNRAS.463..252B: three-component SED decomposition (free synchrotron index) plus H42alpha Te, with sensitivity tests
- 2015MNRAS.450L..80B: H40alpha Te and the effect of the free-free fraction on it
- 2017ApJ...849...90S: fixed-index three-component least squares; SFR from 93 GHz free-free (Murphy et al. 2011)
- 2015ApJ...813..118M: VLA 33 GHz + ALMA 94.5 GHz thermal fractions and alpha_NT test
- 2019MNRAS.483.1624B: per-pixel Band 3/Band 6 free-free removal validated with ATCA
- 2016ApJ...833L...6C: 3 mm free-free extrapolated to 870 um, dust-only map
- 2025A&A...699A.369V: Brgamma-based free-free subtraction at 0.88 mm
- 2024ApJ...967...15K: H29alpha Te, Mezger-Henderson, free-free removed before dust mass
- 2015A&A...577A..30A: turnover-frequency fit, N_Lym, then dust SED
- 2019ApJ...886L...4Z: photoionized outflow model grid and equipartition B
- 2014ApJ...791...95A: ionized shell continuum and NLTE recombination lines
- 2021A&A...653A.117B: free-free identification in protostars from 32.9 GHz
- 2024A&A...684A.134R: jet free-free and ionized mass-loss rates in transition disks
- 2019ApJ...884...97L: emcee multi-component disk plus free-free SED
- 2019A&A...621A..27F: MR-MOOSE with synchrotron for radio galaxies
- 2020A&A...634A...9M: synchrotron spectral ageing with SYNAGE++
- 2014ApJ...796...82Z: uv-plane template subtraction for SN 1987A
- 2018ApJ...855L...2M: gyrosynchrotron index to electron index
- 2018ApJ...869..126L: free-free stellar masses and the two-band limitation
- 2020A&A...640A..27V: quick free-free contamination test for disk masses
