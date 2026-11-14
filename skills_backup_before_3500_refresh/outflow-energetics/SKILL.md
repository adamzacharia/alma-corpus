---
name: alma-outflow-energetics
description: "Measure outflow mass, momentum, kinetic energy, dynamical age, mass outflow rate, momentum flux, kinetic power and mass loading from ALMA line data, for protostellar molecular outflows (CO isotopologues, SiO, HC3N, H2CO) and for galaxy/AGN outflows (CO, [CII], [CI], OH and H2O absorption, plus ionized lines). Use when turning red/blue line wings or a broad component into energetics, choosing Tex, abundance, alpha_CO, geometry factor, radius, velocity and inclination, comparing outflow power with L_bol, L_AGN, SFR or supernova budgets, or refereeing such numbers. Built from 97 ALMA papers (2013-2026)."
---

# Outflow energetics (mass, momentum, energy, rates)

Converts line emission (or absorption) at velocities offset from systemic into an outflow mass, then combines
mass with a velocity and a size to get momentum, energy, a dynamical time and rates. Two communities do this
with different conventions, so keep them apart:
**protostellar outflows** (per-channel LTE column density from CO or another tracer, sums over velocity, solar
masses of 1e-7 to a few) and **galaxy/AGN outflows** (alpha_CO or a [CII] relation applied to a broad
component, Mdot = C M v / R, compared with L_AGN/c and SFR).

The mistakes that matter most:
1. **Most protostellar results are lower limits, but not all results, and the direction depends on the
   assumption.** Protostellar authors call M, P, E lower limits because opacity is not corrected, low-velocity
   gas hides in the cloud channels, flux is resolved out or the field of view is smaller than the flow
   (2021A&A...648A..41V, 2019A&A...632A.101T, 2017MNRAS.465..834Z, 2016ApJ...821L...3T). Going the other way,
   2024A&A...686A..46E calls its molecular outflow quantities upper limits because a bar cannot be excluded,
   and 2014ApJ...797...90S says its X_CO-based masses could be an order of magnitude lower if the gas is
   optically thin. State per quantity which bound applies and why. On simulated disk winds the true mass
   outflow rate was about 7 times and the momentum rate about 200 times the value recovered from synthetic
   12CO(2-1) ALMA data, with wide variation and an inclination dependence (2024ApJ...966..117X); these are
   model-specific recovery ratios, not general correction factors (see Pitfalls).
2. **The conversion factor and geometry dominate the error budget, not the flux.** alpha_CO can be lower by
   ~2.4 or higher by ~5.5 (2018ApJ...859...35G); the OH abundance dominates OH-based rates
   (2024ApJ...962....1S); the factor C in Mdot = C M v/R changes the rate by 3 between a thin shell and a
   uniformly filled cone (2014ApJ...790..160S vs 2019A&A...630A..59B).

> Always report: tracer and transition, velocity ranges per lobe (and what was excluded around systemic),
> S/N threshold, Tex, abundance or alpha_CO (with line ratio if not CO 1-0), opacity treatment, inclination
> value and its convention, radius/length and velocity definitions, the Mdot formula and its geometry factor,
> whether the band covers the full wings, and which numbers are lower or upper limits and why. The cards
> flag line-free channels and continuum subtraction as not stated in 20+ entries and "mass-weighted
> velocity calculation details" and outflow velocity ranges as missing (pack aggregates).

Counts below come from my own count of the pack's "Key parameters" and "Assumptions" lines unless marked
"pack aggregates". Population counts come from my classification of all 97 papers in the pack's paper list
by title and excerpt (enumerated in `references/parameters.md`): 34 protostellar outflow papers, 49 galaxy/AGN
papers (a few only mention an outflow), 6 evolved-star or stellar-wind papers (for example 2017ApJ...841..130A,
2018A&A...614A..58B), and 8 other Galactic papers off-topic for outflow energetics (dense cores, hot cores,
disk-size studies, Sgr A*). The per-paper tables in `references/parameters.md` are selected examples, not the
basis for these counts.

## When to use

- Protostellar: red/blue CO lobes around a protostar, and you need M, P, E, t_dyn, Mdot, outflow force
  (2016ApJ...832..158Z, 2021A&A...648A..41V, 2020A&A...633A.126B, 2025A&A...699A.382M).
- Survey-scale outflow catalogues correlated with clump mass or luminosity (2025ApJ...987..197H: 45 HC3N
  outflows in 146 sources, log-log fits of M_out against L_bol and M_clump).
- Ejection history from knots in a PV diagram (2015Natur.527...70P: 22 knots, dynamical times 100-6000 yr).
- Galaxy/AGN: broad CO wings or residuals after a rotation model, and you need Mdot, Pdot, Edot, momentum boost
  and mass loading (2018ApJ...859...35G, 2014A&A...567A.125G, 2024A&A...686A..46E, 2020ApJ...901..151S).
- High-z quasars and starbursts with broad [CII] wings, single or stacked (2019A&A...630A..59B,
  2025ApJ...990L..31B, 2024ApJ...970....9B), or OH 119 um / H2O absorption (2018Sci...361.1016S,
  2024ApJ...962....1S, 2019A&A...632L...7J).
- Multiphase comparisons of molecular and ionized outflows (2024A&A...686A..46E, 2025A&A...695A...6P).

## When not to use

| Situation | Use instead |
|---|---|
| Only need the outflow morphology, PA, opening angle | Moment maps of red/blue lobes and PV cuts (opening angle at 1000 au projected in 2021A&A...648A..41V) |
| Broad emission could be rotation, a bar, a merger or tidal gas | Model the disk first (3DBarolo is named in 2 matched steps, pack aggregates; used in 2020A&A...641A.151S) and treat only residuals as outflow. 2024A&A...686A..46E calls its molecular values upper limits because a bar cannot be excluded; 2024ApJ...970....9B notes a blueshifted region may be tidal |
| Mass-loss rate of an evolved star or a stellar wind from continuum or recombination lines | Wind models specific to that case (Reynolds-type collimated wind in 2017ApJ...841..130A); out of scope here |
| Rotation or angular momentum of the flow | 3D or PV kinematic modelling; angular momentum from these sums is "highly uncertain" (2020A&A...634L..12D) or an upper limit (2016ApJ...832..158Z) |
| You cannot tell inflow from outflow (gas in front of or behind the source) | Say so and give both; 2014ApJ...784...78R could not distinguish them |

## Steps

### A. Common front end

1. **Define the outflow emission.** Continuum-subtracted cube, primary-beam corrected. Choose velocity ranges per
   lobe from channel maps or PV diagrams and exclude cloud/systemic channels:
   - protostellar: |v - v0| > 3.5 km/s (2020MNRAS.496..394R); line-of-sight 3-50 km/s cut in simulations
     (2024ApJ...966..117X); per-lobe ranges such as blue 1.5-4.25 and red 4.5-7.0 km/s (2017MNRAS.468.3266R);
     cloud-velocity channels excluded (2021A&A...648A..41V, 2025ApJ...987..197H).
   - galaxies: channels > ~224 km/s from Vsys (2014ApJ...797...90S); outside residual velocity [-50,+50] km/s
     after subtracting the rotation curve (2014A&A...567A.125G); > 3 sigma in at least 4 contiguous 30 km/s
     channels over -1000 to -250 km/s (2019A&A...628A.118B).
2. **Set a significance mask, and say whether it is per channel or on the integrated map.** Per channel:
   > 3 sigma in at least 4 contiguous channels (2019A&A...628A.118B); primary-beam-corrected emission > 3 sigma
   in each channel within primary-beam response > 0.2 (card of 2019ApJ...873...73Z, section 5.2); channels
   above 5 sigma (2017MNRAS.468.3266R). On integrated (moment) maps: 3 sigma lobe maps (2021A&A...648A..41V).
   Per-lobe 5 sigma outflow masks, map type not given in the pack (2025ApJ...987..197H). How the primary-beam cutoff and a position-dependent noise were
   chosen is not explained in the pack; if you use a cutoff, state it and use the primary-beam-corrected noise.
3. **Check the spectral coverage.** Make sure the band covers the full wings before reporting a velocity
   range. The pack has a lower-limit rate from limited velocity coverage (2014A&A...567A.125G), CO(3-2) only
   partially covering field and velocity range (2021AN....342.1160P) and a bandwidth too narrow to detect the
   broad component (2019A&A...632A..66O). Label truncated-wing measurements as such.
4. **Decide the inclination and its convention before computing anything** (see Pitfalls).

### B. Protostellar outflows (per-channel LTE)

5. **Column density per channel and pixel.** Optically thin LTE from the line brightness, with one Tex, and
   Tbg = 2.7 K (2021A&A...648A..41V, 2024ApJ...966..117X). General practice (not from the pack): for
   continuum-subtracted brightness of an optically thin line in LTE,
   N_u = (8 pi k nu^2 / (h c^3 A_ul)) integral(T_B dv) x J_nu(Tex) / [J_nu(Tex) - J_nu(Tbg)], with
   J_nu(T) = (h nu / k) / (exp(h nu / k T) - 1), then N_tot = N_u Q(Tex) exp(E_u / k Tex) / g_u. Keep units
   consistent (dv in cm/s with cgs constants). The background term matters when J_nu(Tex) is not much larger
   than J_nu(Tbg), which depends on Tex and frequency, not on how bright the observed line is.
6. **Opacity.** Correct 12CO with 13CO: 2020A&A...634L..12D applies a 12CO optical-depth correction from 13CO
   with 12CO/13CO = 65, giving a range "depending on the opacity hypothesis"; 2017MNRAS.468.3266R reports
   13CO-corrected 12CO masses but says the correction "must be taken with caution"; 2020A&A...633A.126B uses
   13CO and finds 12CO alone underestimates masses and momenta by factors 1.1-5. Alternatively take the
   highest column among detected isotopologues per pixel (2016ApJ...832..158Z). 2017MNRAS.465..834Z adopts
   12CO/13CO = 62 but could not apply an optical-depth correction and calls its values lower limits;
   2018MNRAS.473..879P adopts the same 62, and the pack does not say how it was used. Without a correction,
   say the values are lower limits.
7. **Mass.** M = m_per_H2 x sum(N_tracer / X_tracer) x A_pix, with X_tracer the tracer abundance relative to
   H2. CO/H2 = 1e-4 (or H2/CO = 1e4) is the usual choice: 12 papers in my count of the pack's key-parameter and
   assumption lines (for example 2016ApJ...832..158Z, 2021A&A...648A..41V, 2024ApJ...963...72O); other
   tracers need their own abundance (HC3N 5e-9 in 2025ApJ...987..197H; H2CO 1e-10 in 2025A&A...695A.236L; SiO
   1e-8 to 1e-7 in 2018A&A...615A.141B). Keep the mean-weight definitions apart (general practice):
   - per H2 molecule, including helium: mu = 2.8 (2015ApJ...811L...4Z, 2025ApJ...987..197H,
     2019A&A...632A.101T) or 2.76 (2021A&A...648A..41V); m_per_H2 = mu m_H, about 4.7e-24 g for mu = 2.8.
   - per H nucleus: mu = 1.4 (2024ApJ...966..117X) or 1.36 (2018Sci...361.1016S); use with N_H, not N(H2).
   - per free particle: mu_g = 2.3 in 2025A&A...699A.382M (the paper calls it the mean atomic weight of the
     gas); this is not a mass per H2.
   - 2016ApJ...832..158Z and 2019ApJ...873...73Z quote "2.34e-24 g per H2". That is less than the mass of one
     H2 molecule (about 3.35e-24 g) and equals 1.4 m_H, a mass per H nucleus. Treat the quoted label as a
     source inconsistency and do not reuse it as a mass per H2.
8. **Momentum and energy.** P = sum M_v |v - v_sys|, E = 1/2 sum M_v (v - v_sys)^2, summed over channels
   (2017MNRAS.465..834Z uses the Perez et al. 2015 per-channel formalism). Characteristic velocity
   v_flow = P/M (2017MNRAS.468.3266R). Deproject or state that you did not.
9. **Dynamical time and rates.** t_dyn = lobe length / velocity: maximum velocity with R = R_obs/sin i,
   V = V_max/cos i (2013ApJ...775L..31S); length over mass-weighted mean LOS velocity
   (2024ApJ...966..117X); R / v_exp (2025A&A...699A.382M). Then Mdot = M/t_dyn and the outflow force
   F = Pdot = P/t_dyn = Mdot v (general practice). 2019A&A...632A.101T prints its M7 force as
   "F_out = Mdot / R_lobe x v_max"; with Mdot a mass per time this has units of mass/time^2, not force, so
   do not reuse that expression until its numerator is checked against the paper (dimensionally,
   M v_max^2 / R_lobe would be a force). Low-velocity correction following Margulis 1985 as cited
   (2020MNRAS.496..394R).
10. **Optional: mass spectrum.** 2016ApJ...832..158Z fits m(v) proportional to v^-gamma and reports
    gamma = -3.43 (red) and -2.78 (blue). Taken literally that form would make mass rise with velocity, so the
    paper is internally inconsistent in sign. Read the slopes as m(v) proportional to v^s with s = -3.43 and
    -2.78 (mass falling with velocity), and state your own sign convention. Two power laws in
    2019ApJ...873...73Z.
11. **Compare** with single-dish or literature values for the same source (2019A&A...632A.101T vs single-dish,
    consistent within a factor of few; 2021A&A...648A..41V vs Bjerkeli+2016 and Dunham+2014) and with
    Lbol / Menv trends (van der Marel 2013 comparison in 2020A&A...633A.126B).

### C. Galaxy and AGN outflows

5. **Isolate the outflow flux.** Broad Gaussian component in a spectral fit (2019A&A...630A..59B,
   2025ApJ...990L..31B fits per pixel), or residuals after a disk model (2020A&A...641A.151S with 3DBarolo,
   2014A&A...567A.125G after subtracting the projected rotation curve, 2021AN....342.1160P).
6. **Gas mass.**
   - CO: convert to CO(1-0) with a line ratio (r31 = 0.7, range 0.4-1, in 2024A&A...686A..46E; CO(2-1)/(1-0) = 1
     in 2018MNRAS.475L..52S and 2019A&A...628A..65A; from the systemic emission in 2019A&A...628A.118B), then
     M = alpha_CO L'_CO. alpha_CO = 0.8 Msun (K km/s pc^2)^-1 is the most common single choice (6 papers in my
     count of key-parameter and assumption lines: 2018ApJ...859...35G, 2019A&A...628A.118B, 2017ApJ...843...18V,
     2018MNRAS.475L..52S, 2021AN....342.1160P, and 2021A&A...655A..25Z for its optically thick case). Galactic
     X_CO = 2e20 when the host is not a merger or LIRG (2024A&A...686A..46E). Optically thin limit alpha_CO
     0.25-0.34 (2017A&A...608A..38O, 2016ApJ...832..142Z).
   - [CII]: atomic mass from the Hailey-Dunsheath et al. 2010 relation with X_C+ = 1.4e-4 (2024ApJ...970....9B,
     2013ApJ...763..120C) or ~1e-4 (2019A&A...630A..59B), T = 200 K, n >> n_crit, giving a lower limit.
     2019A&A...630A..59B also assumes a PDR fraction of 0.7: state which fraction of the broad [CII]
     luminosity you assign to the emitting phase, and give the total [CII] luminosity separately.
     T = 100-1000 K changes the mass by only 20% (2024ApJ...970....9B, 2019A&A...630A..59B).
   - [CI]: [C]/[H2] ~ 1.5e-3 (2018PASJ...70L...1M); 2018ApJ...863..143C falls back to an outflow alpha_CO of
     2.1 +/- 1.2 where [CI] is not detected.
   - OH 119 um absorption: optically thin LTE column from equivalent width, converted to H2 through OH/H2,
     Tex = 50-100 K, OH/H2 = 5e-7 to 5e-6 (2024ApJ...962....1S, 2018Sci...361.1016S).
   - H2O absorption: 2019A&A...632L...7J fits a spherical shell with a constant mass outflow rate in MultiNest,
     assuming negligible emission, unit aperture and R_CONT/R_IN ratios, and chi_H2O ~ 1e-6. The authors say the
     shell thickness is unconstrained and the loading factor poorly constrained; quote the fit as a model-
     dependent range (100-900 Msun/yr there), not a single rate.
   - Excitation modelling of several lines: 2018ApJ...868...95M uses a Bayesian RADEX analysis but warns that
     four lines constrain five parameters, the posteriors are broad and a single-phase model is not
     appropriate; 2017A&A...608A..38O flags a Tkin-n degeneracy and the same single-component problem. Check
     the degeneracy and do not treat one fitted conversion factor as uniquely determined.
   - Ionized phase: M = mu m_H L / (gamma n_e), where L is the extinction-corrected outflow (broad) line
     luminosity and gamma the line emissivity at the adopted temperature and abundance. State the extinction
     correction, temperature, metallicity or abundance, and density. 2024A&A...686A..46E uses broad [OIII]
     corrected with the Cardelli law (R_V = 3.1) and intrinsic Ha/Hb = 3.1, mu = 1.4 and n_e from log U;
     2025A&A...695A...6P assumes n_e = 200 cm^-3 and Z = 0.5 Zsun.
7. **Velocity.** v_out = |Delta v| + FWHM_broad/2 (2019A&A...630A..59B), v_max = |v_mom1| + 2 sigma
   (2025ApJ...990L..31B, 2025A&A...695A...6P), v98 (2019A&A...628A.118B), mass-weighted mean of red and blue
   wings without inclination correction (2018ApJ...859...35G), or deprojected (217 km/s projected to 515 km/s
   in 2024A&A...684L..11G).
8. **Radius.** Half the red-blue peak separation (2018ApJ...859...35G), maximum extent or bulk scale
   (2024ApJ...970....9B), beam radius at the centre (2025ApJ...990L..31B), a deliberately conservative value
   (R_out = 7 kpc in 2017ApJ...843...18V).
9. **Rates.** Mdot = C M v / R with:

   | Geometry | C | Papers |
   |---|---|---|
   | Thin shell, averaged over the outflow lifetime | 1 | 2024A&A...686A..46E, 2019A&A...630A..59B, 2017ApJ...843...18V, 2020A&A...633A.127F, 2024ApJ...962....1S |
   | Sphere or cone uniformly filled (uniform density), constant velocity | 3 | 2014ApJ...790..160S ("continuous and volume filling"), 2020A&A...641A.151S, 2014A&A...567A.125G (uniformly filled, with tan alpha) |
   | Solid-angle fraction | Omega f | 2025ApJ...990L..31B (Omega ~ 1/2, f ~ 1) |
   | Cylinder of height h_z | 1 (R = h_z) | 2020ApJ...901..151S (h_z = 1 kpc, constant velocity, uniform density, "conservative") |
   | Mass / age, age = l / V | 1 | 2018ApJ...868...95M, 2014ApJ...797...90S |

   C = 3 needs the uniform-density filled volume, not just constant velocity. The thin-shell M v / R is a
   lifetime average; the instantaneous rate through a shell of thickness Delta R is M v / Delta R
   (general practice), larger by R / Delta R. Say which one you quote.
   Then Pdot = Mdot v, Edot = 1/2 Mdot v^2 (2017ApJ...843...18V, 2019A&A...630A..59B); 2020A&A...633A.127F
   writes L_kin = 1/2 M V^3 / d.
10. **Interpret.** Momentum boost against the luminosity the paper names: Pdot/(L_AGN/c) = 53 in
    2018ApJ...859...35G and 1.5-3 in 2017ApJ...843...18V; Pdot/(L_bol/c) ~ 3 in 2014ApJ...790..160S (equal
    to L_AGN/c only if the quasar dominates L_bol; say so if you make that identification). Edot/L_AGN or L_bol
    (0.15-0.40% in 2017ApJ...843...18V, ~0.5% in 2025ApJ...990L..31B), mass loading eta = Mdot/SFR (~2 in
    2020ApJ...901..151S, 2.2 in 2024ApJ...962....1S), supernova power 7e41 x SFR and the ~1% starburst ratio
    (2018ApJ...868...95M), and scaling relations with L_bol (Fiore et al. 2017 in 2019A&A...628A.118B;
    Mdot-L_AGN in 2020A&A...641A.151S).

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Tex, protostellar outflow lines | 50 K, or bracket two values | adopted 10-100 K; 250, 300 and 700 K tested for EHV jets in 2019A&A...632A.101T | 19 papers state an adopted value (my count: 16 in key-parameter/assumption lines plus 3 in excerpt methods) | 15 & 50 K 2016ApJ...832..158Z; 25 & 100 K 2021A&A...648A..41V; 20 & 50 K 2017MNRAS.468.3266R; 100 K 2020MNRAS.496..394R; 10 K 2015ApJ...811L...4Z |
| CO/H2 | 1e-4 | 8.3e-5 to 1e-4 | 12 at 1e-4 (my count) | 2016A&A...587A.145B; 8.3e-5 2020A&A...633A.126B; H2/CO 1.2e4 2019A&A...632A.101T |
| 12CO/13CO | 62-65 | 60-65 | 4 | 2017MNRAS.465..834Z, 2020A&A...634L..12D, 2018PASJ...70L...1M (60) |
| mu per H2 molecule | 2.8 | 2.76-2.8 | 6 at 2.8 (my count of key-parameter/assumption lines) | 2025ApJ...987..197H, 2019A&A...632A.101T; 2.76 2021A&A...648A..41V |
| mu per H nucleus | 1.4 | 1.36-1.4 | 4 at 1.4 (my count) | 2024ApJ...966..117X, 2024A&A...686A..46E, 2024ApJ...970....9B; 1.36 2018Sci...361.1016S |
| mu per free particle | 2.3 | | 1 | 2025A&A...699A.382M (not a mass per H2) |
| Inclination (protostellar) | taken from disk or assumed | 20-70 deg | ~8 correct, ~5 do not (my count) | 40 deg 2016ApJ...832..158Z; 45 deg 2013ApJ...775L..31S; 20 deg 2016A&A...587A.145B; none 2017MNRAS.468.3266R |
| alpha_CO (outflow) | 0.8 | 0.25-4.6 | 6 at 0.8 (my count) | 2018ApJ...859...35G; 1.1 2020A&A...641A.151S; 2.1 (0.8-3.4) 2019MNRAS.489.1927S; Galactic 2024A&A...686A..46E |
| CO line ratio to 1-0 | 1 for 2-1; 0.7 for 3-2 | r31 0.4-1 | 6 | 2024A&A...686A..46E, 2019A&A...632A..33A (0.82), 2018MNRAS.475L..52S |
| X_C+ ([CII]) | 1.4e-4 or 1e-4 | 1e-4 to 1.4e-4 | 5 | 2024ApJ...970....9B, 2019A&A...631A..78S, 2026ApJ..1000..312Z |
| T ([CII]) | 200 K, n >> n_crit | 200 K to 1e4 K (maximal case) | 5 | 2025ApJ...990L..31B; 1e4 K 2025A&A...695A...6P |
| OH/H2 | 5e-7 to 5e-6 | | 2 | 2024ApJ...962....1S, 2018Sci...361.1016S |
| Geometry factor C | 1 | 1-3 | see table above | 2014ApJ...790..160S |
| Covering factor, molecular OH absorption (thin shell) | no single default | 0.3-0.8 | 2 | f = 0.3 2024ApJ...962....1S; f_cov ~0.8 2018Sci...361.1016S |
| Global covering, ionized BAL wind | no single default | | 1 | Omega = 0.2 2024ApJ...970....9B (BAL calculation only) |
| Solid angle, [CII] emission outflow | no single default | | 1 | Omega ~ 1/2, f ~ 1 2025ApJ...990L..31B |

Longer per-paper lists, including tracer abundances, radii and velocities, are in `references/parameters.md`.

## Software

The pack aggregates name very little software for this step; in most matched steps the software is not
specified:
3DBarolo 2, PyNeb 2, CASA 1, MultiNest 1, PyMultiNest 1, MADCUBA (SLIM) 1, PFT code 1, emcee 1, DysmalPy 1,
RADEX 1.

| Task | Tool | Papers |
|---|---|---|
| Disk model to isolate non-circular gas | 3DBarolo | 2020A&A...641A.151S |
| Outflow H2O absorption model fit | MultiNest / PyMultiNest | 2019A&A...632L...7J |
| LTE fit of an integrated outflow line; flux-tracing mass-loss rate | MADCUBA SLIM; PFT code | 2025A&A...699A.382M |
| Ionized-gas diagnostics (task not given in the excerpts) | PyNeb | 2 papers (pack aggregates) |
| Excitation of outflow gas from several lines | RADEX (Bayesian) | 2018ApJ...868...95M |
| Synthetic observations of simulated outflows | simalma (CASA) | 2024ApJ...966..117X |

## Pitfalls

- **Inclination convention.** Papers measure i from the line of sight (R = R_obs/sin i, V = V_max/cos i in
  2013ApJ...775L..31S; tau_dyn = D/V (cos i/sin i) in 2015Natur.527...70P) or from the plane of the sky
  (i = 20 deg with respect to the plane of the sky in 2016A&A...587A.145B). Say which. Near-pole-on or
  near-edge-on values blow up: 450 km/s / cos 80 deg = 2600 km/s (2014ApJ...797...90S).
- **No inclination correction is common** (2017MNRAS.468.3266R, 2025A&A...695A.236L, 2019A&A...632A.101T;
  2020MNRAS.496..394R derives i <= 62.5 deg but does not apply it). With i from the line of sight and the
  2013ApJ...775L..31S corrections (R = R_obs/sin i, V = V_obs/cos i), the true velocity is never below the
  projected one, so uncorrected P and E are low for a purely axial flow, but t_true = (R_obs/V_obs) cot i
  can be larger or smaller than the projected age (larger for i < 45 deg, smaller for i > 45 deg), and the
  rates move accordingly. Give the inclination dependence instead of a blanket bound. Keep an author's
  lower-limit statement only with its own reason: 2017MNRAS.468.3266R calls its kinematic age a lower limit
  because only the ALMA extent was used.
- **Single Tex** "is a large source of uncertainty" (2020MNRAS.496..394R); Tex = 50 K lowers the mass by ~40%
  relative to 100 K there; Tex brackets give a factor ~2.5 (2021A&A...648A..41V). Some authors pick the Tex
  that minimizes mass (17 K in 2016ApJ...821L...3T).
- **Hidden low-velocity gas**: it is "next to impossible" to separate from the cloud (2025ApJ...987..197H).
  Simulations show total mass is 24 times the mass in the 3-50 km/s window on average (2024ApJ...966..117X).
- **Missing flux and field of view**: MRS smaller than the cavities (2017MNRAS.468.3266R), outflows truncated by
  the field (2025A&A...699A.382M, 2024ApJ...961..228S), extended [CII] missed by interferometers
  (2019A&A...630A..59B); 2019ApJ...873...73Z applies literature correction factors of 10 (mass) and 8 (momentum)
  for opacity and missing flux.
- **Simulation recovery ratios are not transferable correction factors.** 2024ApJ...966..117X finds true/recovered
  ratios of about 7 (mass outflow rate; about 10 at 60-70 deg) and about 200 (momentum rate; about 100 at
  ~60 deg) with wide variation, from one 60 Msun core evolutionary sequence with PDR effects ignored. It then
  applies separate corrections of 10 (mass rate) and 200 (momentum rate) to three observed sources. Quote these
  as that model's results, not as factors to apply to other outflows.
- **Method choice for rates changes answers by more than an order of magnitude**: 1.8e-6 Msun/yr from M/t_dyn
  versus 4.2e-8 Msun/yr from the PFT code for the same flow (2025A&A...699A.382M).
- **Galaxy conversion factors**: at fixed line luminosity or tracer column (other assumptions fixed), mass and
  rate scale as Mdot proportional to alpha_CO, but inversely with tracer abundance: Mdot proportional to
  X_C+^-1 or (OH/H2)^-1 (the OH column is converted to H2 through OH/H2 in 2024ApJ...962....1S); 2018Sci...361.1016S
  quotes a systematic factor of at least 2, possibly 10; 2014ApJ...797...90S says masses could be an order of
  magnitude lower if optically thin.
- **Outflow vs other kinematics**: bars (2024A&A...686A..46E), tidal features (2024ApJ...970....9B),
  interacting companions (2019A&A...631A..78S), disk overlap (2019A&A...632A..66O) mimic or contaminate outflows.
  Driver attribution (AGN vs star formation) often cannot be settled (2026ApJ..1000..312Z).
- **Stacks** dilute orientations and compare a mean to individual objects (2019A&A...630A..59B,
  2018MNRAS.473.1909G).
- **Not stated in the cards** (pack aggregates): continuum subtraction and line-free channels (the most frequent
  gap), CASA version (7 + others), self-calibration, primary-beam correction, flux-scale uncertainty, moment
  clipping thresholds, and for this step "how the outflow flux was separated from the disk" and the velocity
  ranges per lobe. The cards rarely state the deprojection convention explicitly.

## Verification checks

What the papers did:
- Bracket the dominant assumption and quote the spread: two Tex values (2016ApJ...832..158Z,
  2021A&A...648A..41V), r31 = 0.4-1 and X_CO = (0.8-2)e20 (2024A&A...686A..46E), alpha_CO factors 2.4/5.5
  (2018ApJ...859...35G), opening angle +/- 20 deg (2025ApJ...990L..31B).
- Compare with independent data: single-dish outflow force (2019A&A...632A.101T), SMA flux 64 Jy km/s
  (2020A&A...634L..12D), OH-based rates (2017ApJ...843...18V), an empirical equivalent-width relation
  (2024ApJ...962....1S), a second tracer (CS gives almost the same results in 2013ApJ...775L..31S; dense-gas p-v
  diagrams in 2014A&A...567A.125G).
- Check the dynamical age against an independent age (34 yr optical bubble in 2015ApJ...811L...4Z).
- Rule out artefacts for the wings: continuum-subtraction errors, line blending, correlator response
  (2014ApJ...797...90S).
- Energy and momentum budget against drivers: SN, stellar radiation and AGN radiation pressure
  (2021AN....342.1160P); literature momentum limits for AGN and starburst winds and L_Edd/c
  (2024A&A...684L..11G).
- Test recovered vs true quantities on simulations (2024ApJ...966..117X).

What a careful referee adds:
- Recompute one lobe by hand from the quoted flux, Tex, abundance, distance and area; rates are easy to get
  wrong by the factor C or by mixing projected and deprojected values.
- Ask whether M, P, E and t_dyn use the same inclination and the same velocity reference (v_sys source:
  C18O Gaussian fits in 2019ApJ...887..209A).
- Check the maximum recoverable scale against the lobe size and ask for total-power or ACA data if flux is
  missing.
- Require labelled lower and upper limits rather than a single number with no error.

## Source cards

All 97 papers are listed in `references/sources.md`. Most informative for this technique:

Protostellar: 2016ApJ...832..158Z, 2021A&A...648A..41V, 2024ApJ...966..117X, 2020A&A...633A.126B,
2019A&A...632A.101T, 2025A&A...699A.382M, 2025ApJ...987..197H, 2017MNRAS.468.3266R, 2020MNRAS.496..394R,
2020A&A...634L..12D, 2019ApJ...873...73Z, 2015Natur.527...70P.

Galaxy/AGN: 2018ApJ...859...35G, 2014A&A...567A.125G, 2024A&A...686A..46E, 2017ApJ...843...18V,
2019A&A...630A..59B, 2025ApJ...990L..31B, 2024ApJ...970....9B, 2024ApJ...962....1S, 2018Sci...361.1016S,
2020ApJ...901..151S, 2014ApJ...790..160S, 2018ApJ...868...95M.
