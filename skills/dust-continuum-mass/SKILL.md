---
name: alma-dust-continuum-mass
description: "Turn ALMA (sub)mm continuum flux into dust mass, gas mass, column density or an upper limit, with an opacity law, dust temperature, gas-to-dust ratio and distance chosen the way published ALMA papers choose them. Use when converting a continuum flux or brightness to a disk, core, clump, envelope, debris belt, circumstellar shell or galaxy dust/gas mass, when checking someone else's mass, or when stating mass upper limits for non-detections. Built from 915 ALMA papers (2012-2026)."
---

# Dust and gas masses from (sub)mm continuum

Measures the mass of emitting dust from a continuum flux density under the optically thin, isothermal assumption, then
(optionally) a gas mass through a gas-to-dust ratio. The answer is only as good as three assumed numbers: opacity
kappa_nu, dust temperature T_d, and gas-to-dust ratio. The two mistakes that matter most: (1) mixing an opacity quoted
**per gram of gas** with one quoted **per gram of dust** (a factor 100 error), and (2) applying the thin formula to
emission that is partly optically thick, which only gives a **lower limit** (2018A&A...619A.161C, 2015A&A...573L...1O,
2014ApJ...783L..13P). For disks, 2025A&A...693A.286S notes that optical depth and opacity effects can make thin dust
masses too low by up to a factor of about 7.

> Always report kappa_nu (with its reference frequency, beta and whether it is per dust or per gas mass),
> T_d, distance, gas-to-dust ratio, and the flux you used. A mass without these is not reproducible.

## When to use

- A detected continuum source (disk, core, clump, envelope, belt, shell, galaxy) and you need M_dust, M_gas, N(H2) or
  n(H2) from its flux or surface brightness.
- A non-detection: convert an n-sigma flux limit to a mass limit. This skill's working default is 3 sigma (examples:
  2015A&A...583A..66H, 2019ApJ...875L...9W, 2017ApJ...842....8M); the pack has no frequency count, and others use 2
  sigma (2025ApJ...993L..40S; 2024ApJ...963....1O (card)) or 5 x rms of a tapered image (2020MNRAS.499.5241C). State
  the significance. Such a limit is an optically thin, assumed-size limit only (step 8).
- Population work: dust-mass distributions and M_dust vs M_star relations for disk surveys (2016ApJ...828...46A,
  2020A&A...633A.114S, 2025A&A...693A.286S, 2014ApJ...787...42C).
- Core and clump fragmentation studies needing core masses, densities and virial parameters (2020ApJ...894L..14L,
  2020ApJ...890...76N, 2019ApJ...871..185L, 2024ApJS..270....9X).
- Sanity-checking a mass quoted in a paper or produced by another tool.

## When not to use

| Situation | Use instead |
|---|---|
| Emission likely optically thick (bright compact disks, hot cores, inner envelopes, T_b close to T_d) | Radiative transfer model (RADMC-3D, MCFOST, DALI) or state the result as a lower limit (2015A&A...573L...1O, 2017A&A...604A...6S, 2026ApJ..1003..219W) |
| Disk structure, settling, gaps, gas and dust together | Full disk modelling: RADMC-3D (34 + 3 under "radmc3d" in the pack aggregates), DALI (23), MCFOST (22); a ProDiMo SED grid in 2025A&A...694A.295P; an optool/DSHARP RT grid in 2025A&A...696A.232G |
| High-z galaxy with good FIR photometry | SED fit (MAGPHYS 15, CIGALE 13, BAGPIPES 3 in the aggregates; STARDUST in 2024A&A...690A..55S) and use its dust mass, after reconciling its dust composition and opacity with yours (2025A&A...694A..82S divides CIGALE masses by 2; 2021ApJ...908...15S finds MAGPHYS masses a factor two below Draine and Li based ones), with the single-band mass as a cross-check |
| Gas mass where CO is detected and alpha_CO is defensible | CO-based mass, then compare with the dust route (2021A&A...652A..98G, 2018Sci...362.1034D); [CI] is another check (2021A&A...652A..66P) |
| Continuum dominated by free-free, synchrotron or stellar photosphere | Decompose first (SED with radio data); the dust formula on raw flux overestimates mass (2016A&A...591A..73G, 2017MNRAS.468L..87C, 2025A&A...694A.295P) |
| Extended emission resolved out by the interferometer | Combine with ACA/TP or single-dish, or quote the mass as a lower limit (2014ApJ...787...48X, 2024ApJ...968L..19F, 2017ApJ...835..213P) |

## Steps

1. **Define the emitting object and regime.** Decide the aperture or component (whole disk, ring, crescent, core,
   clump, belt, galaxy). Note whether you need dust mass, gas mass, column density or volume density; each needs extra
   inputs (gas-to-dust, mu, a size or thickness). Core extraction examples: astrodendro (2020ApJ...894L..14L),
   Clumpfind (2020ApJ...890...76N), both (2019ApJ...871..185L); 5 vs 3 papers in the aggregates, too few to rank. Size
   conventions differ: r = (A/pi)^0.5 (2020ApJ...894L..14L), geometric mean of Clumpfind semi-axes
   (2020ApJ...890...76N), R = (FWHM_maj FWHM_min)^0.5 / 2 x D (2024ApJ...961L..35M); state yours.
2. **Build a clean continuum flux.**
   - Image line-free continuum (CASA `tclean`, or GILDAS MAPPING; 2024A&A...691A.180F, 2021A&A...652A..98G). The cards
     rarely state which channels were line-free (more than 100 card flags across wordings in the pack), so record
     yours. Line contamination of continuum is a real limitation (2013ApJ...774L...7M).
   - Apply primary-beam correction before measuring flux (20 card flags for unstated PB-correction details).
   - Measure the flux: aperture inside a contour (5 sigma contour and 50% PB response in 2019ApJ...874...89C), 2D
     Gaussian with `imfit` (5 + 4 papers under two labels), or a uv-plane fit (`lmfit` in 2025ApJ...986L..22R;
     `uvmodelfit` check in 2024A&A...682A..61C).
   - Use the integrated flux density (Jy) for a mass. A peak in Jy/beam is a mass per beam; for surface brightness
     divide by the beam solid angle, Omega_beam = pi theta_maj theta_min / (4 ln 2) (general practice;
     2021ApJ...907...94C writes the same form). Take the noise locally from the PB-corrected map, not one global rms:
     noise rises toward the PB edge and can be enhanced locally (gap rms in 2024ApJ...974..102S).
   - Remove non-dust flux: stellar photosphere (F_dust = F_cen - F_star in 2013ApJ...762L..21M), free-free or
     synchrotron (2017MNRAS.468L..87C, 2016ApJ...821L..16C, 2016A&A...591A..73G; spectral indices 4.0 dust vs -0.15
     free-free in 2024ApJ...967..133S), compact companions or central sources by Gaussian subtraction
     (2014ApJ...796....1T).
3. **Choose the dust temperature** (Parameter table). The pack shows examples of each approach, not a ranking. My
   guidance (not a literature census): prefer a temperature measured for the same emitting component (SED fit, NH3 or
   line rotational temperature), then a luminosity or radiative-equilibrium scaling, then a fixed fiducial, and check
   the temperature applies to the dust you are weighing. Examples: clump SED fit with SciPy least squares
   (2020ApJ...890...76N (card)), T_d from gas temperature (2014ApJ...797...27F, 2024ApJ...961L..35M from NH3; CH3OH
   excitation temperature in 2025ApJ...991...59B, 2026ApJ..1003..219W). A gas temperature stands in for T_d only if
   gas and dust are thermally coupled: justify it by density (2025ApJ...991...59B assumes coupling for n(H2) >~ 1e5
   cm^-3; 2022MNRAS.512.4419P for n_H2 > 1e6 cm^-3) and watch for decoupling (2020ApJ...904..181L warns gas and dust
   may decouple during a burst). Luminosity scaling for disks
   (2016ApJ...819..102V, 2021A&A...653A..46V, 2025A&A...693A.286S), class by L/M with Monte Carlo ranges
   (2025A&A...701A.219N), radiative equilibrium at the belt radius for debris disks (2017ApJ...842....8M,
   2025A&A...693A.151M).
4. **Choose the opacity law** kappa_nu = kappa_0 (nu/nu_0)^beta. Pick the convention of the subfield you will be
   compared with (Parameter table, `references/parameters.md`), and check whether kappa_0 is per gram of dust or per
   gram of gas. Grain-size-dependent opacities (optool and dsharp_opac, 4 papers each in the aggregates) change the
   answer: 2021ApJ...923..121Y runs DSHARP and 2.3 (nu/230 GHz)^0.4 side by side; 2024ApJ...974..102S brackets 100 um
   vs 1 mm grains.
5. **Compute the mass** with the full Planck function (general practice; the Rayleigh-Jeans limit is poor at 20 K and
   230 GHz, where h nu / k is about 11 K; some papers still use RJ, e.g. 2024ApJ...974..257Z, 2025A&A...698A.165A).
   RJ overestimates B_nu (Planck/RJ = x/(e^x - 1) = 0.75 at 230 GHz and 20 K, x = h nu/kT), so RJ masses come out
   about 25% LOW at these values. Check one number by hand: 50 mJy at 1.3 mm from 160 pc, 20 K, kappa = 2.3 cm2/g
   gives about 37 Earth masses (general practice); an answer off by 10x usually means mJy was converted wrongly
   (1 mJy = 1e-26 erg s^-1 cm^-2 Hz^-1):

   ```
   M_dust = F_nu d^2 / (kappa_nu B_nu(T_d))                       # optically thin, isothermal
   M_gas  = (gas-to-dust) x M_dust                                # or use kappa per gram of gas directly
   N(H2)  = I_nu / (mu_H2 m_H kappa_nu,gas B_nu(T_d))             # I_nu in surface brightness per sr
   n(H2)  = M_gas / ((4/3) pi r^3 mu_H2 m_H)                      # spherical mean, as in 2020ApJ...894L..14L
   ```

   mu_H2 is the mean mass per H2 molecule (2.8; 2019A&A...628A..27B, 2020ApJ...890...76N); do not substitute a mean
   mass per free particle (about 2.33 to 2.37, general practice) here. A third convention uses the mean mass per
   hydrogen atom, mu_H = 1.41 (2023MNRAS.525.2229M; 2026ApJ...998..277M uses it with dust-to-gas 0.0027 and still
   reports N(H2)). For molecular hydrogen, mu_H2 = 2 mu_H (general), so a per-H form gives N(H2) only if the factor of
   two is in the denominator; read each paper's complete expression before reusing its numbers. The n(H2) line assumes a sphere of radius r (2020ApJ...894L..14L uses r = (A/pi)^0.5
   from the astrodendro area). Say so, and propagate the geometry: 2019ApJ...871..185L uses a flattened structure with
   an assumed thickness profile, and 2014ApJ...795L..25R quotes density as a lower limit because the core is
   unresolved. For an unresolved source, r is only an upper bound, so n(H2) is a lower bound.

   Sanity number: with kappa = 2.3 cm2/g at 1.3 mm and T_d = 20 K, 1 mJy at 140 pc is about 0.57 Earth masses of dust;
   2015A&A...583A..66H uses exactly M_dust = 0.566 [F_1300/mJy (d/140 pc)^2] M_earth. For high-z sources (general
   practice; check the convention of the paper you compare with):

   ```
   nu_rest = (1+z) nu_obs ;  T_CMB(z) = 2.725 K (1+z)
   M_dust  = F_nu,obs D_L^2 / [ (1+z) kappa(nu_rest) ( B_nu_rest(T_d(z)) - B_nu_rest(T_CMB(z)) ) ]
   ```

   The B(T_CMB) term is the contrast correction (dust is seen against the CMB). CMB heating is a separate correction
   that raises T_d(z) for cold dust; apply it only if your T_d is a z = 0 value. Size of the effect:
   2025A&A...693A.190J gives a CMB flux correction of about 1.03 at z ~ 1 rising to about 1.31 at z ~ 6, and heating
   of about 3% at z = 6; 2021A&A...652A..66P ignores heating (< 2%) at z = 6. CMB-corrected examples:
   2016ApJ...822...80S, 2017Natur.545..457D, 2025ApJ...993L..40S; 2020ApJ...892...66M uses the Kovacs-style thin
   equation with CMB correction. For lensed sources, use the intrinsic flux (divide by the magnification mu_L) and say
   which magnification applies to the dust: 2016ApJ...822...80S calls a single magnification a simplification, and
   2021ApJ...917...99Y uses mu = 4.53 for the continuum but 3.44 for [CII].
6. **Check optical depth.** Compare the peak intensity with what the dust at T_d would emit if thick. For an
   absorption-only isothermal slab with beam filling factor f and background T_bg (general practice, no scattering):

   ```
   tau = -ln[ 1 - Delta I_nu / ( f (B_nu(T_d) - B_nu(T_bg)) ) ]     # Delta I_nu = background-subtracted intensity
   ```

   Use the Planck intensity, not the Rayleigh-Jeans T_b ratio (RJ is poor at these T and nu). 2018A&A...619A.161C did
   a brightness-based check and found the crescent only marginally thin (tau about 0.4 even with T_d raised by 1.5),
   so called its masses lower limits. In this slab model the intensity can never exceed f B_nu(T_d), so a brightness
   above it means the temperature or emission model is wrong, not that tau is large: revisit T_d, contamination
   (free-free, lines) and the brightness convention before assigning any tau. 2025ApJ...988..106H imposes tau = 4
   where T_b exceeds T_d as a convention; treat that as a modelling choice, not a measurement. A low beam-averaged brightness does **not** prove the emission is thin: beam dilution (f << 1)
   or scattering can suppress the observed intensity of thick dust. Check the source is resolved before trusting f = 1
   (2016Sci...353.1519P flags beam dilution), and exclude or model scattering (2020A&A...644A..11L drops pixels with
   scattering or thick emission; 2019MNRAS.488.1005P includes anisotropic scattering in RT). If tau is not small,
   report a lower limit or move to RT modelling.
7. **Convert to gas, if needed.** Gas-to-dust 100 is the default (Parameter table); scale with metallicity for
   galaxies and the Magellanic Clouds (2020ApJ...892...66M, 2020ApJ...891..164S, 2017MNRAS.469.4683C; delta_GDR
   proportional to Z^-0.85 normalised to 100 at solar in 2021A&A...655A..42S). 2020MNRAS.498.4109J prints "GDR = 100 x
   10^(Z-Zsun)"; the pack does not define Z, and if Z is a log metallicity this form falls with lower Z, opposite to
   the trend above, so verify it in the paper before use. Phase coverage depends on the gas-to-dust calibration:
   2025ApJ...993L..40S counts molecular gas only, 2024A&A...686A..64M and 2021A&A...652A..66P derive atomic plus
   molecular gas (the latter then takes 75% as molecular). Say which phases your result covers. A galaxy shortcut
   skips kappa and gas-to-dust: M_gas = L_850 / alpha_850 with T_d = 25 K (2024A&A...691A.248L,
   2022A&A...664A..63X; values in `references/parameters.md`). L_850 is the rest-frame 850 um spectral luminosity,
   extrapolated from the observed band along the RJ tail; papers apply it only to points with lambda_rest > 250 um
   (2020MNRAS.498.4109J, 2021A&A...655A..42S). Document the extrapolation and do not use it outside that regime.
   Cross-check with CO where possible (2021A&A...652A..98G).
8. **Handle limits and samples.** Convert n-sigma limits with the same kappa and T. State the source size assumed: a
   point-source limit (2017ApJ...842....8M) uses the local rms per beam, while an extended source needs an aperture or
   model-dependent limit that grows with the area. A thin mass limit is conditional: compact optically thick material
   can hide more mass. 2017ApJ...842....8M converts its Fomalhaut b flux limit to a thin dust-mass limit or, if thick,
   to a clump-size limit; 2019MNRAS.488.1005P uses size-dependent RT models; 2020MNRAS.498.1319M assumes a disc larger
   than about 0.1 au because a smaller thick disc could hide more mass. Do not call a thin limit an upper bound on
   total mass without an optical-depth and size assumption. Other conventions: 3 sigma plus any positive flux
   (2016ApJ...827..142B), stacked limits (2025ApJ...990L..61C), SED non-detections entered as 1.5 +/- 1 sigma
   (2021ApJ...908...15S). For samples with non-detections use survival analysis (Kaplan-Meier in ASURV:
   2016ApJ...828...46A; lifelines with a bootstrapped log-normal fit: 2025A&A...693A.286S) or Bayesian regression with
   censored data (linmix: 2020A&A...633A.114S).
9. **Write the error budget** (examples under Verification checks; 2024ApJS..270....9X lists gas-to-dust 28%,
   opacity 23%, temperature about 20%, flux about 14%, distance 10%). Term ordering depends on the case. Flux
   calibration alone understates the error (2024A&A...682A..61C: inner mass off by up to about 5 from optical depth).

## Parameter defaults and ranges

Counts are my own: distinct bibcodes from a regex over the pack's "Key parameters" and "Assumptions" lines (515 of
915 papers listed, so lower bounds), hand-checked to drop false hits. Membership lists: `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Gas-to-dust (mass) | 100 | 30 to about 370 typical; 4594 in a metal-poor dwarf (card) | 166 state 100 | 100: 2016ApJ...828...46A, 2020ApJ...894L..14L; 141: 2013ApJ...779...96T; 150 to 154: 2019A&A...621A.122B; 200: 2024A&A...681A..17D; 300 (C-rich AGB): 2024A&A...686A.274V; about 370 (LMC): 2020ApJ...891..164S; 30 in disks: 2023MNRAS.518.6092L; 4594 +/- 2848: 2020ApJ...892..147S (card); more in `references/parameters.md` |
| T_d, disks and cores (fixed) | 20 K | 6 to 30 K for cold gas | 47 adopt 20 K for some sources | 2016ApJ...828...46A, 2025A&A...696A.232G, 2020ApJ...894L..14L, 2017ApJ...849...25L (starless candidates), 2022A&A...662A...8M (most cores); 15 K: 2018A&A...619A.161C; 6 K: 2024ApJ...968L..19F; 10 K: 2016ApJ...823..160D; 30 K: 2026A&A...706A.214V |
| T_d, disks (scaled) | 25 K (L*/Lsun)^0.25 | exponent 0.17 to 0.25; 20 K fallback (2021A&A...653A..46V); no 10 K floor (2016ApJ...831..125P) | 7 use an L^0.25 scaling (one for a protostar) | 2016ApJ...819..102V, 2025A&A...693A.286S, 2025ApJ...994..214T, 2017ApJ...846...70P; RT-calibrated: 2020ApJ...892..111F |
| T_d, protostellar / hot cores | by class or line temperature | 20 / 50 / 100 K; up to 150 to 300 K | (see examples) | 2020A&A...635A...2S, 2018A&A...615A...9P, 2025A&A...701A.219N, 2022MNRAS.512.4419P, 2019A&A...628A..27B |
| T_d, high-z galaxies | 47 K, beta 1.6 (quasar hosts); 25 K mass-weighted (gas-mass work) | 25 K to 100 K (hot DOG) | 16 quote 47 K; 4 call 25 K mass-weighted | 47 K/1.6: 2016ApJ...816...37V, 2024ApJ...977..190X; mass-weighted 25 K: 2020ApJ...892...66M, 2025ApJ...993L..40S, 2025A&A...693A.190J; 25 K assumed: 2024ApJ...963....1O; 50-100 K: 2018Sci...362.1034D |
| T_d, debris belts | radiative equilibrium | 25 to 51 K (radiative-equilibrium examples); fixed 40 K / 100 K for cold / warm belts in 2021AJ....162..235Y | (see examples) | 2017ApJ...842....8M, 2025A&A...693A.151M, 2013ApJ...762L..21M, 2021AJ....162..235Y |
| kappa, disks / debris (per dust) | 10 cm2/g at 1000 GHz, beta 1 (2.3 cm2/g at 230 GHz) | 1.1 to 3.5 cm2/g at 0.9 to 1.3 mm | 12 use the 1000 GHz form; 27 quote 2.3 cm2/g | 2016ApJ...828...46A, 2025A&A...693A.286S, 2017ApJ...842....8M, 2025A&A...696A.232G; low end: 1.1 cm2/g at 1.3 mm (2017ApJ...845...10F), 1.15 cm2/g (2021MNRAS.501.4317P) |
| kappa, disks, shallow beta | 2.3 cm2/g (nu/230 GHz)^0.4 | beta 0.4 | (see examples) | 2014ApJ...787...42C, 2016ApJ...831..125P, 2021A&A...656A.150P, 2024A&A...688A.149D |
| kappa, cores (OH94-type, per dust) | 0.9 cm2/g at 1.3 mm; 1.89 cm2/g at 870 um | 0.82 to 1.11 cm2/g at 1.3 mm | 25 quote 0.82 to 1.0 near 1.3 mm (a few omit the frequency); 7 quote 1.85 to 1.89 near 870 um | 2020ApJ...894L..14L, 2022MNRAS.512.4419P, 2024ApJS..270....9X, 2026ApJ...999..194I |
| kappa, per gas (includes 100) | 0.01 cm2/g at 230 GHz; 0.1 (nu/1000 GHz)^beta | 0.005 to 0.02 cm2/g near 1.3 mm | (see examples) | 2019ApJ...884...48C, 2018MNRAS.475..448T, 2025A&A...701A.219N, 2014ApJ...791...20R, 2024A&A...686A.122A |
| kappa, galaxies | 0.077 m2/kg at 850 um; 0.0431 m2/kg at 352.6 GHz; 2.64 m2/kg at 125 um | 0.04 to 0.15 m2/kg near 850 um | (see examples) | 2020ApJ...892...66M, 2025A&A...693A.190J, 2025A&A...701A.120P, 2025ApJ...993L..40S, 2014MNRAS.438.1267S |
| beta | 1 (disks, kappa normalised at 1000 GHz); 1.5 to 1.8 (cores, galaxies) | 0 to 2.2 | 21 use 1; 69 use 1.5 to 1.9 | 2016ApJ...828...46A; 2020ApJ...892...66M; 2016ApJ...833..209O; 0 to 0.5 in 2025NatAs...9.1176R |
| mu_H2 (mass per H2 molecule) | 2.8 for N(H2), n(H2) | 2.8 to 2.86 | 23 quote 2.8 to 2.86 (20 exactly 2.8, two 2.81, one 2.86); 13 explicitly identify the H2 convention | mu_H2 = 2.8: 2019A&A...628A..27B, 2020ApJ...890...76N, 2024ApJ...961L..35M; mu = 2.8: 2024ApJ...962...13C |
| mu (other definitions) | not interchangeable with mu_H2 | 2.3 to 2.37; 1.41 per H | 12 quote 2.3 to 2.37; 4 quote mu_H = 1.41 | 2.33: 2019ApJ...884...48C, 2021ApJ...907...94C; 2.37: 2016ApJ...823..160D; 1.41: 2026ApJ...998..277M. The cards rarely say whether 2.3x is per free particle; check the paper before reusing it |
| Upper-limit significance | 3 sigma (skill default, not a census) | 2 to 5 sigma | (no count) | 3: 2015A&A...583A..66H, 2019ApJ...875L...9W; 2: 2025ApJ...993L..40S, 2024ApJ...963....1O (card); 5 x rms: 2020MNRAS.499.5241C |

## Software

Counts from the pack aggregates (software named in the matched steps of all 915 papers). The full table with uses and
label splits is in `references/parameters.md`. Sums of two labels (RADMC-3D + radmc3d) may double count.

- Imaging and flux: CASA 37 (`tclean`, `imfit`, `uvmodelfit`), GILDAS 7, MIRIAD 5.
- RT and thermochemistry: RADMC-3D 34 (+3 as radmc3d), DALI 23, MCFOST 22, LIME 9, MCMax 5 (+3 mcmax3d), DUSTY 4,
  ProDiMo 2. Flux limits to disk mass limits with RADMC-3D: 2019MNRAS.488.1005P, 2020MNRAS.498.1319M.
- Fitting: emcee 21 (upper limits as a likelihood penalty in 2021A&A...652A..66P); SciPy 6 (clump modified-blackbody
  least squares in 2020ApJ...890...76N (card); `curve_fit` of an adapted P23 disk SED model with column-density and
  logistic dust-to-gas parameters, not a plain modified blackbody, in 2025A&A...694A.295P).
- Galaxy SEDs: MAGPHYS 15, CIGALE 13 (reconcile their dust conventions first; Pitfalls).
- Censored statistics: lifelines 7, linmix 5 (+3 linmix_err), ASURV 4. Core extraction: astrodendro 5, Clumpfind 3.
- Opacities: optool 4, dsharp_opac 4, OpacityTool 3 (2025A&A...696A.232G).

The pack does not establish a dominant implementation of the thin formula; the cards rarely name the code used for it.

## Pitfalls

- **Per gas vs per dust opacity.** Many cards quote kappa that already includes gas-to-dust 100 (2018MNRAS.475..448T
  says so explicitly; 2019ApJ...884...48C, 2025A&A...701A.219N, 2024A&A...686A.122A). Multiplying again by 100
  inflates gas mass 100x; using it as a dust opacity inflates dust mass 100x.
- **Units.** 1 m2/kg = 10 cm2/g (general). Galaxy papers quote m2/kg, disk papers cm2/g. Several cards print opacity
  units as g cm^-2 (2026A&A...706A.214V "units as printed", 2019ApJ...872...92F, 2025A&A...701A.219N); read these as
  cm2/g after checking the paper.
- **Optical depth.** Thin masses of bright compact sources are lower limits (2018A&A...619A.161C, 2015A&A...573L...1O,
  2017A&A...604A...6S, 2016ApJ...832..178V, 2014ApJ...783L..13P, 2026ApJ..1003..219W). A lower spectral index can come
  from optical depth, not grain growth (2018A&A...619A.161C). In SED fits the sign can flip: assuming thin dust when
  it is thick biases T_d low and M_dust high (2024A&A...684A..33K; 2022A&A...665L...7S allows a factor two
  overestimate). 2013ApJ...764L..14Z quotes its disk mass as a lower limit with a factor-five (total mass)
  uncertainty.
- **Temperature dominates, more so for cold dust.** Mass scales as 1/T only in the Rayleigh-Jeans limit (h nu << k T,
  general); at 10 to 20 K and ALMA frequencies use the full Planck function. 2026ApJ...998..277M finds N(H2) changes
  by about a factor 3 between 10 and 20 K; 2017ApJ...838..114K finds 10 K gives 2x higher and 25 K about 2x lower
  masses than 15 K; 2020ApJ...894L..14L finds 50 K lowers core masses 3x vs 20 K. The isothermal assumption can bias
  masses either way (2016MNRAS.457.4536W calls its masses upper limits; 2016ApJ...833L...6C says warm dust dominating
  the SED peak may make its mass too low; 2024ApJ...976..241Y: too low for starless, too high for protostellar).
- **Opacity uncertainty ranges from about 25% to a factor 3-5 in the papers that quote it** (examples in
  `references/parameters.md`). Large grains can hide mass, so masses are lower limits (2015ApJ...808...69B,
  2016MNRAS.458L..29C, 2021NatAs...5..586Y).
- **Gas-to-dust is not universal.** It rises at low metallicity (2020ApJ...892...66M, 2020ApJ...892..147S), differs
  for AGB and RSG envelopes (2024A&A...686A.274V, 2024A&A...681A..17D), comes out high in high-z quiescent galaxies
  (2025ApJ...993L..40S), and disk gas masses from dust conflict with CO by about 10x (2016ApJ...828...46A). Whether
  the dust-based gas includes atomic gas depends on the calibration (molecular only in 2025ApJ...993L..40S; atomic plus
  molecular in 2024A&A...686A..64M).
- **Resolved-out flux.** Interferometers miss extended emission: continuum interferometer-to-single-dish ratio 0.53 in
  2014ApJ...787...48X, up to about 50% of 333 GHz flux in 2017ApJ...835..213P, N(H2) 4x low in 2024ApJ...968L..19F.
  Line emission suffers the same way (CO example: only 43% of single-dish flux recovered in 2016ApJ...832..148V).
- **SED masses on other conventions.** SED codes carry their own dust composition and opacity; reconcile before
  comparing (2025A&A...694A..82S divides CIGALE masses by 2; 2021ApJ...908...15S, MAGPHYS vs Draine and Li;
  2019PASJ...71...71H, the Dunne 2000 opacity doubles M_d).
- **Contaminating emission.** Free-free, synchrotron, the stellar photosphere and line emission all add to the
  continuum (2016A&A...591A..73G, 2013ApJ...762L..21M, 2013ApJ...774L...7M, 2021A&A...650A.142M).
- **Distance.** Mass scales as d^2; distance can dominate limit uncertainties (2015A&A...583A..66H) and disputed
  distances change masses (2014ApJ...791..108F, 2017A&A...603A..10B).
- **Core definition.** Core boundaries and thresholds change masses by 10-40% (2015MNRAS.449..715W) and are subjective
  (2013ApJ...779...96T, 2019ApJ...871..185L).
- **Unstated settings.** Cards most often flag as missing the CASA version, self-calibration intervals, line-free
  channels, flux-scale uncertainty and PB correction (counts in `references/parameters.md`). State all of these.

## Verification checks

What the papers did:

- **Vary T_d and beta** and report the spread: T 15-35 K gives 25-50% systematic (2020ApJ...892...66M); 20-30 K
  (2018ApJ...854L...4R, 2016ApJ...833...12R); 1.5x T test of tau (2018A&A...619A.161C); 50 K and random-T appendix
  (2020ApJ...894L..14L); 40 and 70 K, beta 1.5 to 2.2 (2024ApJ...977..190X); 1000 Monte Carlo T draws per class
  (2025A&A...701A.219N); other T prescriptions repeated (2020A&A...633A.114S).
- **Vary the opacity** (Hildebrand vs OH94: 2014ApJ...796....1T) or bracket with grain size (100 um vs 1 mm grains:
  2024ApJ...974..102S; two opacity models: 2021ApJ...923..121Y). 2024Sci...383..988B folds both opacities and a 0.2
  dex optical-depth term into its mass interval.
- **Explicit error budget**: 30% kappa, 15% flux calibration, about 10% temperature (2014ApJ...787...48X); per-term
  budget in 2024ApJS..270....9X; mass about 40% and column density about 35% (2020ApJ...890...76N); 20% NOEMA and 10%
  ALMA flux calibration propagated (2025A&A...693A..49S).
- **Brightness-based optical depth check** (2018A&A...619A.161C, 2020ApJ...904..181L), with scattering or thick pixels
  excluded in 2020A&A...644A..11L.
- **Thin vs RT**: compare thin masses with an RT or thermochemical grid (2025A&A...694A.295P with ProDiMo;
  2025A&A...696A.232G with an optool/DSHARP grid, dropping disks at the grid edge with tau >> 5).
- **Independent mass**: CO-based gas mass (2021A&A...652A..98G median offset 0.23 dex; 2018Sci...362.1034D),
  [CI]-based gas mass (2021A&A...652A..66P), earlier ALMA or single-dish fluxes (2017ApJ...842....8M,
  2024ApJ...968L..19F), full SED fit as a sanity check (CIGALE in the aggregates).
- **Plausibility and completeness**: 2020ApJ...890L..14T rejected uncoated-grain opacities that gave a shell mass
  above the star's possible initial mass; injection-recovery for faint sources (2024ApJ...974..102S).
  2025A&A...693A.286S builds lifelines cumulative distributions (which handle upper limits) and separately runs an
  ordinary SciPy KS test; a plain KS test is not censor-aware, so for samples with limits use a censored two-sample
  test (general practice) or the survival-analysis tools in step 8.

What a careful referee adds:

- Recompute one mass from the quoted F_nu, d, kappa, T (the 0.57 Earth-mass sanity number above).
- Confirm the opacity is per dust or per gas and that gas-to-dust is applied once; check the mu convention.
- Confirm the flux is PB-corrected, line-free, and free of free-free and stellar flux.
- Compare the peak intensity with f B_nu(T_d) before accepting "optically thin", and check resolution (filling factor)
  and scattering: a low beam-averaged brightness alone is inconclusive.
- Check that mass limits state the assumed size and optical depth, and use the local PB-corrected noise.
- Check that limits use the same kappa and T as detections and that censored data are handled with survival analysis.
- At high z, check the CMB contrast term and which magnification was applied to the dust.

## Source cards

The full list with titles is in `references/sources.md` (generated). The most informative cards for this technique:

- 2016ApJ...828...46A: Lupus disk survey; T 20 K, 10 cm2/g at 1000 GHz, beta 1; ASURV.
- 2025A&A...693A.286S: IMTT vs Herbig disk masses; L-scaled T; lifelines, plain KS; masses may be low by up to ~7.
- 2025A&A...696A.232G: optool/DSHARP RT grid vs thin masses (2.3 cm2/g, 20 K); grid-edge disks dropped.
- 2015A&A...583A..66H: closed-form M_dust = 0.566 F (d/140)^2 M_earth; distance-dominated limits.
- 2018A&A...619A.161C: crescent mass, tau from T_b, lower limits.
- 2017ApJ...842....8M: Fomalhaut belt; radiative-equilibrium T; mass limit for a point source.
- 2025A&A...693A.151M: 74 debris belts; kappa 0.23 m2/kg at 1.33 mm; T(R) law.
- 2020ApJ...894L..14L: CMZ cores; OH94 0.899 cm2/g; T sensitivity appendix.
- 2024ApJS..270....9X: core masses with a per-term uncertainty budget; mu_H2 2.81; 1.89 cm2/g at 870 um.
- 2020ApJ...890...76N: clump SED for T and beta; core masses with 40% error.
- 2020ApJ...892...66M: ASPECS stacking; Kovacs thin formula, CMB, metallicity-dependent gas-to-dust.
- 2018Sci...362.1034D: hot DOG; 50-100 K bracket; dust vs CO gas.
- 2014ApJ...787...48X: error budget; interferometer/single-dish ratio.
- 2020ApJ...891..164S: LMC hot core; dust-to-gas 0.0027 scaled by metallicity; three T values.
- 2019MNRAS.488.1005P: RT conversion of flux limits to circumplanetary disk mass limits.
- 2024ApJ...974..102S: spectral index, grain-size-dependent kappa, injection-recovery.
