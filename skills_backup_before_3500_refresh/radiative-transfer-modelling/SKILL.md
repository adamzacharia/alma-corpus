---
name: alma-radiative-transfer-modelling
description: "Build forward radiative transfer models of ALMA dust continuum and molecular line data (RADMC-3D, MCFOST, LIME, DALI and similar), turn them into synthetic observations, and compare them with the data the way published ALMA papers do. Use when fitting or interpreting disk, envelope, debris-belt, AGB-envelope, comet or planetary-atmosphere structure with a physical model, when deriving temperatures, gas masses, abundances, settling or turbulence from a model, when post-processing a simulation into synthetic ALMA images, or when testing whether an image feature is an interferometric artefact. Built from 274 ALMA papers (2012-2026)."
---

# Radiative transfer modelling of ALMA data

A radiative transfer (RT) model predicts what ALMA should see from an assumed physical structure (density,
temperature, dust properties, abundances, velocity field), so the fitted numbers are only as good as the
assumptions you froze. The two mistakes that matter most:
(1) reporting a hand-tuned or grid model as a unique measurement when the authors themselves report
degeneracies (gas mass x alpha_turb giving the same SED in 2016MNRAS.461..385B; optical thickness vs. true dust
scale height in 2025A&A...697A..64V; mass-loss rate, half-abundance radius, temperature and velocity profile in
2016A&A...586A...5M), and (2) comparing a sky model with interferometric data without reproducing the uv
coverage, which hides missing flux (2016A&A...586A...5M, 2014ApJ...796....1T, 2024A&A...686A.274V).

> Always report: code and version, grid and photon numbers, dust model (composition, size range, slope and the
> variable it refers to, opacity at the observed band, per dust or per gas mass), gas-to-dust ratio, abundance
> law with its denominator (per H2 or per H) plus freeze-out and photodissociation rules, LTE or non-LTE (with
> collision data), fixed geometry (d, i, PA), how the model was turned into visibilities or images (including
> primary-beam handling), and the fitting method. The cards show these are often missing.

## When to use

- Protoplanetary disks (162 of 274 pack papers are tagged protoplanetary_disks): dust surface density and
  settling (2025A&A...697A..64V, 2021AJ....161..238W), gas temperature and CO snow line
  (2013ApJ...774...16R, 2018A&A...609A..47P), turbulence (2015ApJ...813...99F, 2018ApJ...856..117F),
  molecular abundance laws (2017A&A...605A..21C, 2019A&A...623A.150V), gas masses from rare isotopologues
  (2019ApJ...882L..31B), gas surface densities from pressure-broadened CO line wings (2025ApJ...984L..19Y).
- Protostellar envelopes and young disks: luminosity and envelope structure (2018A&A...612A..72J,
  2019A&A...628A..27B), infall plus rotation (2015ApJ...812...27A, 2017ApJ...849...56A).
- Debris belts: ring radius, width, height and dust mass in the uv or image plane (2016MNRAS.460.2933M,
  2020MNRAS.497.2811K, 2025ApJ...990..145L).
- Evolved-star envelopes: mass-loss history and abundance profiles (2016A&A...586A...5M,
  2015ApJ...814..143A, 2020A&A...633A..13D).
- Planetary atmospheres: vertical profiles by line-by-line retrieval (2017Icar..286..289L, 2014ApJ...795L..30C).
- Comets: non-LTE Haser outflow models with jet geometry fitted to visibilities by least squares
  (SUBLIMED in 2025ApJ...986L..22R).
- Synthetic observations of hydro or MHD simulations (2020ApJ...898...10T, 2024ApJ...966..117X,
  2019ApJ...874...89C).
- Turning a non-detection into a model-based mass limit (2019MNRAS.488.1005P).

## When not to use

| Situation | Use instead |
|---|---|
| Optically thin continuum, you only need a mass | single-temperature mass formula (`dust-continuum-mass` skill); 2019A&A...623A.150V uses that formula even inside an RT study |
| One or a few lines, single-zone conditions (T_kin, n_H2, N) | RADEX-type slab or LVG fit (`non-lte-excitation`); e.g. RADEX with MultiNest in 2017A&A...604A...2S |
| Column density from many lines in LTE | rotational diagram (`rotational-diagram-lte`) |
| Only stellar mass or rotation law | kinematic fitting (`keplerian-disk-kinematics`); RT is overkill unless optical depth matters |
| Ring and gap radii only | parametric uv fitting (`uv-plane-fitting`, `disk-substructure-profiles`) |
| Galaxy rotation curves | tilted-ring or 3D kinematic tools (`galaxy-3d-kinematics`); 2017ApJ...850..180J used GIPSY ROTCUR/GALMOD |
| Source counts or completeness | injection-recovery with simobserve is enough (2020ApJS..251...14H, 2015A&A...584A..78C); no RT needed |

## Steps

1. **Pick the observable and the code.**
   - Dust temperature, continuum and scattered-light images: RADMC-3D or MCFOST (counts in Software).
   - Non-LTE lines in 3D: LIME, often on a RADMC-3D dust temperature (2018A&A...612A..72J) or on a
     published disk structure (2017A&A...605A..21C); RADMC-3D LVG mode also used (2024ApJ...966..117X).
   - Chemistry coupled to structure: DALI thermochemical models (2019A&A...623A.150V, 2017A&A...599A.113M).
   - 1D AGB shells: Monte Carlo code of Schoier and Olofsson (2016A&A...586A...5M).
   - Line polarisation: PORTAL on converged LIME output (2024A&A...686A.274V).
   - Planetary atmospheres: line-by-line spherical-layer codes (NEMESIS in 2014ApJ...795L..30C, custom in
     2017Icar..286..289L). Comets: SUBLIMED non-LTE coma models (2025ApJ...986L..22R).
2. **Fix what you can from outside the model.** Distance, inclination, PA, systemic velocity and stellar
   parameters are usually fixed from continuum fits or literature (2017A&A...605A..21C fixed i = 44 deg,
   PA = 133 deg, d = 122 pc; 2015ApJ...812...27A took position and PA from continuum; 2016MNRAS.460.2933M
   fixed the gas disk orientation to the dust fit). Every fixed value is a systematic; list them.
3. **Build the density structure** (defaults in the Parameter table).
   - Disks: power law with exponential taper, gamma = 1 is the usual choice (2016A&A...585A..58V,
     2018ApJ...854..177V, 2020ApJ...895L..18B).
   - Vertical structure: write the parameterization out, because papers use two forms. Height form:
     H(r) = H100 (r / 100 au)^beta with H100 about 10 au and beta about 1.1 (2019A&A...622A..75L,
     2019A&A...624A...7V, 2025A&A...697A..64V). Aspect-ratio form: h = H/r = h_c (r / r_c)^psi, e.g.
     (h/r)_c = 0.18, psi = 0.1 (2020ApJ...895L..18B); then beta = 1 + psi (general practice). Check which
     exponent a paper means before copying it: 2019ApJ...883...98Z grids h0 0.02-0.2 with psi 1-1.3, and
     2018A&A...612A..72J fixes flaring Psi = 0.25.
   - Cavities and gaps as depletion factors on gas and dust separately (2018ApJ...867L..14V,
     2019ApJ...879L...2M, 2017ApJ...836..201D).
   - Envelopes: Ulrich infall (2018ApJ...857...18S, 2020ApJ...902..141S), power law rho ~ r^-1.5
     (2019A&A...628A..27B), or a density plateau (2018A&A...612A..72J).
   - AGB winds: steady spherical outflow gives rho(r) = Mdot / (4 pi r^2 v(r)) (general practice), so
     rho ~ 1/r^2 needs both constant Mdot and constant velocity. 2016A&A...586A...5M quotes the 1/r^2 law while
     its velocity rises from 3 to 14.3 km/s; keep v(r) explicit for an accelerating wind. Add spirals or shells
     in 3D when the data show them (SHAPE plus LIME in 2020A&A...633A..13D).
4. **Choose the dust model.** A -3.5 slope is the most common stated choice: 27 of the 227 papers with
   assumption lines in the pack state it (my grep for -3.5/MRN/Dohnanyi), and only two state another slope in
   those lines. Say which variable the slope refers to: n(a) da ~ a^-q in grain radius is the usual meaning.
   A mass-spectrum exponent 11/6, n(m) ~ m^-11/6, is equivalent to n(a) ~ a^-3.5 for compact grains of fixed
   density (general practice); the 2018MNRAS.475.4924K card gives q = 11/6 without saying which variable, so
   do not compare it with radius slopes without checking. The opacity at the observed band follows from
   composition and a_max (see references/parameters.md). For settling, either two grain populations with mass
   fraction f_large and height ratio chi (f = 0.85, chi = 0.2 in 2018A&A...610A..24F and 2018ApJ...854..177V)
   or an alpha-driven settling prescription (2025A&A...697A..64V, 2021AJ....161..238W).
   - Turbulence from settling rests on prerequisites; state them. 2025A&A...697A..64V assumes rings are
     pressure maxima, grains are fragmentation limited (v_frag = 1 m/s) and vertical turbulence is dominant over
     or comparable to radial turbulence; it also fixes the grain size distribution and artificially enlarges
     the stellar radius to warm the models of GO Tau, GW Lup, HL Tau and Oph163131. If you cannot test these,
     quote the inferred turbulence as conditional on them.
5. **Set the temperature.** Either compute it with Monte Carlo dust RT (2018A&A...612A..72J,
   2024ApJ...966..117X) or impose a parametric T(r) = T0 (r/r0)^-q, most often q = 0.5
   (2019ApJ...883...22C, 2020ApJ...892...99C, 2025ApJ...984L..19Y). For CO lines, a two-layer
   midplane/atmosphere law is used when the vertical gradient matters (Tmid10 = 40 K, Tatm10 = 125 K in
   2018ApJ...852..122H; T_atm = 125 K at 10 au in 2021AJ....161...38O; Tatm/Tmid = 2 in 2019NatAs...3..314L).
   Gas temperature equal to dust temperature is the common assumption (2018A&A...609A..47P,
   2018ApJ...859..111H, 2024MNRAS.534.2904C).
6. **Set the gas abundances and excitation.**
   - Always state the denominator. CO/H2 and CO/H differ by a factor of 2 in fully molecular gas (general
     practice): 2017ApJ...851..132C gives 12CO/H = 7.5e-5 with H/H2 = 2, i.e. CO/H2 = 1.5e-4, and
     2024ApJ...966..117X gives 12CO/H = 1e-4.
   - CO/H2 = 1e-4 is the most common stated value: 18 of the 227 papers with assumption lines (my grep), e.g.
     2015ApJ...813...99F, 2017ApJ...835...17M, 2025ApJ...984L..21B. Others differ: CO/H2 = 7e-5 in
     2017ApJ...851...85B, 1e-6 in 2018ApJ...856..117F.
   - Freeze-out below 19-21 K (19 K in 2015ApJ...813...99F, 20 K in 2017ApJ...851...85B, 21 K in
     2025ApJ...984L..21B). Photodissociation where the shielding H2 column is BELOW 1e21 cm^-2
     (2017ApJ...851...85B, 2025ApJ...984L..21B); CO survives where the column is above it. Say how the column
     is integrated (the cards give only the threshold).
   - Isotopologues scaled by ISM ratios (CO/13CO = 69, CO/C18O = 557 in 2016ApJ...823L..18H,
     2017ApJ...851..132C). Isotope-selective photodissociation is not included in 2018ApJ...854..177V; say
     whether you include it.
   - LTE is the most commonly stated excitation assumption (39 of the 227 papers with assumption lines, my
     grep; about 10 papers anywhere in the aggregate lines mention non-LTE, LVG or collision rates). Switch to
     non-LTE (LIME, RADMC-3D LVG, DALI) for low-density gas, debris gas with electron collisions
     (2016MNRAS.460.2933M) or envelopes, and then check: infrared pumping (only partly included in
     2015ApJ...814..143A), how many levels you include (up to J = 30 plus the nu6 = 1 state in
     2015ApJ...814..143A; J = 41 in 2020A&A...633A..13D), whether collision rates are borrowed from another
     molecule (SiS-H2 rates for AlCl in 2021A&A...655A..80D; N2H+ and HCN rates for N2D+ and DCN in
     2017A&A...606A.125S), and whether the LVG approximation holds (it may not apply to the torus in
     2017A&A...605A..28D).
   - Mean molecular weight: mu = 2.37 for H2 plus He gas (10 papers in the aggregate lines, my grep, e.g.
     2012ApJ...757..129R, 2015ApJ...812...27A, 2017ApJ...846L..26W; 2.3 in 2021AJ....161..238W). Secondary
     CO-dominated debris gas uses mu = 14 (2020MNRAS.497.2811K, 2020ApJ...892...99C). Choose mu from the gas
     composition, since it sets pressure support and sound speed.
7. **Run the RT with enough photons and grid.** About 1e8 photon packages is the typical RADMC-3D or
   MCFOST choice for thermal and mm images (2019AJ....158...15P, 2020ApJ...891...48H, 2025ApJ...984L..57O).
   Budgets differ by task: 2024NatAs...8.1148U used 1e7 for the continuum, 1e9 for ALMA polarization and
   1e11 for near-IR scattered light; 2019A&A...627A.114K tested 1e5 to 1e9. Use the modified random walk in
   optically thick regions (2019A&A...627A.114K, 2019A&A...628A..27B, 2024ApJ...966..117X). Line models run
   on 5e4 to 2.5e5 grid points with 12 to 16 iterations (2017A&A...606A.125S, 2016A&A...587A.145B); LIME with
   1e5 points in 2020A&A...633A..13D. Iterate the dust opacity if it depends on temperature (two recursions
   in 2018A&A...612A..72J).
8. **Turn the model into what ALMA measured.**
   - Best: sample model visibilities at the observed uv points (vis_sample in 2017A&A...605A..21C and
     2025ApJ...986L..22R; uvsim in 2016MNRAS.460.2933M) and fit in the uv plane. Apply the primary beam to
     the model before sampling and match the spectral sampling (general practice).
   - Or simulate the observation with the real configuration and image it with the same settings as the data:
     CASA observing simulation with the same antenna configuration (2020ApJ...898...10T), simalma
     (2024ApJ...966..117X), or Fourier transforming the model with ft and imaging with tclean, then correcting
     the surface density iteratively (2025A&A...697A..64V).
   - Image-plane fits need consistent primary-beam handling, masks and a noise model.
     2025ApJ...990..145L fits a primary-beam-corrected image, reweights chi2 for correlated pixels and reports
     non-Gaussian noise near the minor axis; say how you handle each of these.
   - Beam convolution of the sky model is the cheapest and least faithful option (2019A&A...623A.150V
     convolved DALI images with a 0.3 arcsec Gaussian); it ignores missing flux.
   - For lines, check continuum subtraction: continuum oversubtraction or line blocking by dust may reduce
     line flux (2025A&A...693A.101T); compare subtracted and unsubtracted cubes, model dust attenuation where
     the dust is thick, and document regions you exclude (2017A&A...605A..21C excluded the inner 50 au partly
     because of dust optical depth).
9. **Compare and fit.** Choose a likelihood and say how correlated pixels or channels are handled (see
   Parameter table and Verification). The pack aggregate lists 40 fitting phrasings, one paper each, so these
   are phrasings, not paper frequencies. My keyword classification: 18 mention chi2 or chi-square (as a
   minimisation or a likelihood); 11 describe manual, by-eye, hand-tuned, qualitative or no formal fit (3 of
   these combine manual steps with MPFIT chi2, a chi2 check or an optimal-estimation retrieval); 7 use a
   sampler (5 emcee or MCMC, 1 MultiNest nested sampling, 1 walker-based run with the sampler unnamed);
   2 Levenberg-Marquardt; 2 optimal-estimation retrievals. The rest give priors, free parameters, a grid or an
   unnamed method ("method not stated"). Prefer a formal fit with a sampler (emcee is named in 37 papers in
   the Software aggregate) when you need uncertainties; use a grid when the model is too slow
   (2016A&A...586A...5M, 2017A&A...605A..21C).
10. **Report the systematics.** Repeat the fit with the main frozen assumptions varied (opacity, CO
    abundance, gas-to-dust, temperature law) and quote the spread. Papers that report only statistical
    errors warn that systematics can be larger (2016MNRAS.463L..74K). Include the flux scale: 2020ApJ...892...99C
    left calibration uncertainty out of its MCMC, while 2017Icar..286..289L tested a +-5% calibration change;
    add a flux-scale nuisance parameter or a rerun at +-5-10%.

## Parameter defaults and ranges

Fuller tables (dust opacities, CO chemistry, MCMC settings, simobserve inputs) are in references/parameters.md.
"Assumption papers" means the 227 distinct papers with lines in the pack's Assumptions aggregate; counts are my
grep of those lines unless marked otherwise.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Grain size distribution slope (n(a) da ~ a^-q, radius) | q = 3.5 | a^-3 (2018ApJ...866L...6C); p = 2.5 fixed, 3.5 tested (2024ApJ...971..129C); q = 11/6 with variable unstated (2018MNRAS.475.4924K) | 27 assumption papers state -3.5 | 2016MNRAS.460.2933M, 2019A&A...624A..33V, 2020ApJ...889...59P |
| Grain size range | ~0.03-0.1 um to 1 mm-1 cm | a_min 0.002 um (2 nm, 2020A&A...644A..11L) to 10 um (2018MNRAS.475.4924K); a_max 1 um (VY CMa, 2019A&A...627A.114K) to 1 cm | many | 2021AJ....161..238W (0.03-1000 um), 2016MNRAS.460.2933M (1.3 um-1 cm), 2018ApJ...860...82H (a_min 0.25 um) |
| Opacity at 1.3 mm (per dust) | 2.2-2.3 cm2/g | 0.95-3.95 cm2/g | about 10 papers at 2.2-2.31 (my count) | 2018ApJ...859..111H, 2019MNRAS.488.1005P, 2018MNRAS.474.4347C; 3.95 in 2018ApJ...857...87L |
| Gas-to-dust ratio (mass) | 100 | 33-300 | 28 assumption papers mention 100 (one is labelled "dust-to-gas mass ratio 100", see note) | 2024ApJ...966..117X, 2019A&A...624A...7V; 33 in 2019AJ....158...15P, 300 in 2019A&A...629A.146V |
| Surface density index gamma | 1 (tapered) | 0.6-1.5; prior 0-2 | >10 lines | 2018ApJ...854..177V, 2019ApJ...883...22C; 0.6 in 2018A&A...616A..88V; prior in 2018MNRAS.474.4347C |
| Characteristic radius R_c | 100-300 au | 10-600 au | many | 2015ApJ...798...85P (200 au), 2018A&A...616A..88V (250 au), 2017AJ....153..233F (600 au) |
| Scale height H(r) = H100 (r/100 au)^beta | H100 ~10 au, beta ~1.1 | H100 5-15 au; beta 1.0-1.2; aspect-ratio form psi = 0.1 means beta = 1.1 | ~6 lines | 2019A&A...622A..75L, 2024ApJ...966...59S, 2016ApJ...819..102V; psi in 2020ApJ...895L..18B |
| Settling (two populations) | f_large 0.85, chi 0.2 | f 0.85-0.99; chi 0.2-1.0 | 4 | 2018A&A...610A..24F, 2018ApJ...854..177V, 2019A&A...623A.150V, 2020A&A...638A..38T |
| Temperature power-law index q | 0.5 | 0.3-0.75 | >8 lines | 2017MNRAS.465.2595M, 2019ApJ...883...22C; 0.3 in 2015ApJ...798...85P; 0.65 tested in 2012ApJ...757..129R; 0.75 in 2017SciA....3E2935L |
| CO/H2 in warm disk gas (per H2) | 1e-4 | 1e-6 (2018ApJ...856..117F) to 1.5e-4 (2017ApJ...851..132C, from CO/H = 7.5e-5) | 18 assumption papers state 1e-4 | 2017ApJ...835...17M, 2018ApJ...859..111H; 7e-5 in 2017ApJ...851...85B |
| CO/H2 in AGB envelopes | 3e-4 to 6.5e-4 | | 4 | 3e-4 in 2024A&A...691A..57M, 4.3e-4 in 2016A&A...586A...5M, 6.5e-4 in 2020A&A...633A..13D and 2017A&A...605A..28D |
| CO freeze-out temperature | 19-21 K | 19-30 K | about 11 papers (my count) | 2015ApJ...813...99F (19 K), 2017ApJ...851...85B (20 K), 2018A&A...609A..47P (21 K), 2018A&A...612A..72J (30 K) |
| Mean molecular weight | 2.37 (H2 + He) | 2.3-2.37; 14 for CO-dominated debris gas | 10 papers mention 2.37 in aggregate lines | 2012ApJ...757..129R, 2017AJ....153..233F; 2.3 in 2021AJ....161..238W; 14 in 2020MNRAS.497.2811K |
| Disk microturbulence | 0.01-0.05 km/s or 0 | 0 to 0.2 km/s | ~10 | 2016ApJ...823L..18H (0.01), 2019NatAs...3.1109P (0.05), 2017ApJ...840...60B (0.2), 0 in 2015ApJ...812...27A |
| Envelope/wind microturbulence | 1 km/s | 0.5-3 km/s | 5 | 2024A&A...686A.274V, 2019A&A...629A.146V, 2018ApJ...855..113D |
| Photon packages (dust MC, thermal and mm images) | ~1e8 | 5e7 (2016MNRAS.461..385B) to 2e9 (2017ApJ...835L..11T); 1e5-1e9 tested in 2019A&A...627A.114K; 1e9 for ALMA polarization, 1e11 for NIR scattered light (2024NatAs...8.1148U) | 10 lines | 2024A&A...688A.102T, 2024ApJ...963..134Y |
| emcee walkers x steps | ~100 x 1000 | 24-500 walkers; 300 (2017MNRAS.465.2595M) to ~10,000 steps (2020MNRAS.497.2811K) | 16 papers give walkers in aggregate lines | 2017ApJ...839...86H, 2018MNRAS.474.4347C, 2025ApJ...984L..19Y |

Note on gas-to-dust: the 2018A&A...612A..72J card literally reads "Dust-to-gas mass ratio 100". That label is
probably inverted (a dust-to-gas ratio of 100 is unphysical for these envelopes) but the card does not settle
it; verify against the paper before citing it for either convention.

## Software

Counts and labels are copied from the pack aggregate "Software named in the matched steps", which lists
spelling variants as separate entries, so summing variants can double count a paper.

| Tool (aggregate label) | Count | Used for |
|---|---|---|
| radmc-3d (also radmc3d 9, radmc3dpy 4) | 98 | dust temperature, continuum and scattering images, LTE/LVG line cubes (2016MNRAS.460.2933M, 2024ApJ...966..117X) |
| casa | 49 | imaging and observing simulations |
| lime | 39 | non-LTE 3D line transfer (2017A&A...605A..21C, 2020A&A...633A..13D) |
| emcee | 37 | MCMC over model parameters (2020MNRAS.497.2811K, 2025ApJ...990..145L) |
| mcfost (also mcfost-python 2, pymcfost 2) | 34 | disk dust RT, settling, joint scattered light + mm (2021AJ....161..238W, 2025A&A...697A..64V) |
| dali | 32 | thermochemical disk models and grids (2019A&A...623A.150V, 2017A&A...599A.113M) |
| casa simobserve (also simobserve 2, casa simanalyze 3) | 29 | synthetic observations, filtering tests (2015ApJ...812...27A, 2019ApJ...874...89C) |
| vis_sample (also vis-sample 2) | 12 | model visibilities at observed uv points (2017A&A...605A..21C) |
| miriad | 8 | imaging of model visibilities (2018A&A...612A..72J) |
| radex (also pythonradex 2) | 6 | escape-probability slab checks (2015ApJ...806...17R, 2019MNRAS.485.2457H) |
| galario, diskjockey, uvsim | 3, 3, 2 | fast visibility sampling, disk fitting |
| Other RT codes | 2-4 each | hyperion 4, mollie 4, optool 4 (opacities), shape 3, shapemol 3, torus 2, rac2d 2, mcmax 2, ali code 2, Schoier and Olofsson Monte Carlo code 2 |
| Hydro codes feeding RT | 2-3 each | phantom 3, ramses 3, fargo3d 3, pluto 2 |

General practice (not from the pack): RADMC-3D and MCFOST are dust Monte Carlo codes with line modes;
LIME solves non-LTE level populations on an unstructured grid and needs LAMDA-format molecular data.

## Pitfalls

- **Non-unique models.** Authors state their model is not unique, not optimized or degenerate in
  2012ApJ...757..129R, 2013ApJ...774...16R, 2016A&A...586A...5M, 2018ApJ...859..111H (genetic-algorithm
  solution may not be unique) and 2024A&A...691A..57M; 2018A&A...612A..72J calls its match qualitative
  with no confidence intervals. Named degeneracies: gas mass x alpha_turb giving the same SED
  (2016MNRAS.461..385B); optical thickness vs. true dust scale height (2025A&A...697A..64V); mass-loss rate,
  half-abundance radius, temperature and velocity profile (2016A&A...586A...5M). General practice: also
  watch envelope mass vs. radius and gap width vs. depth, which trade off in most parametric fits.
- **Optically thick tracers do not give mass.** Masses become lower limits when emission is optically thick
  (2025NatAs...9.1833L, 2020ApJ...890..130T; dust masses likely underestimated in 2020ApJ...889...59P).
  General practice: 12CO is usually thick in disks, so use rarer isotopologues (13C17O in 2019ApJ...882L..31B).
- **Gas mass depends on the assumed CO abundance, but not always as 1/X_CO.** For an optically thin line at
  fixed excitation the inferred mass scales as 1/X_CO (general practice); from pressure-broadened line wings
  the gas surface density scales as X_CO^-0.5 (2025ApJ...984L..19Y). Otherwise vary X_CO and rerun the fit.
  Papers that set the carbon budget explicitly use [C]/[H] = 1.35e-4 (2017AJ....153..240A,
  2017A&A...599A.113M); lower carbon would hide gas.
- **Dust mass depends on composition and a_max** (2016MNRAS.460.2933M); kappa0 is uncertain by a factor of
  two (2015ApJ...808..102K) and dust opacity dominates the mass uncertainty in 2020ApJ...899...10T.
- **Scattering.** Some models switch it off at sub-mm (2015ApJ...812..126C, 2017ApJ...840...60B), but
  self-scattering lowers intensity and spectral index of thick disks (2019ApJ...877L..22L,
  2020ApJ...893..125U). Decide deliberately.
- **Missing flux and filtering.** Without ACA or TP, extended flux is lost (2016A&A...586A...5M,
  2018ApJ...859..111H, 2016PASJ...68...88K) and lines near systemic velocity are hard to model
  (2014ApJ...796....1T); a smooth model underestimates peak flux when extended structure is filtered
  (2019ApJ...874...89C); filtering inflated polarisation fractions by 2-3x (2024A&A...686A.274V).
- **Inconsistent physics between steps**, e.g. isothermal hydro vs. power-law RT temperature
  (2014ApJ...796....1T). General practice: a parametric structure need not be in hydrostatic or dynamical
  equilibrium; say so if you use it.
- **Cloud contamination** can prevent a gas mass constraint (2015ApJ...806L..22C); envelope contamination of
  disk emission is flagged in 2020ApJ...890..130T. General practice: check CO near the cloud velocity.
- **Continuum subtraction.** Oversubtraction or blocking may reduce line flux (2025A&A...693A.101T).
- **Errors that are too small.** Statistical errors only (2016MNRAS.463L..74K); true uncertainties much
  larger than formal ones (2021A&A...655A..80D); a grid search that does not characterize uncertainties
  (2017ApJ...839...86H); calibration uncertainty left out of the MCMC (2020ApJ...892...99C); unresolved inner
  regions excluded from the fit (2017A&A...605A..21C excluded <50 au).
- **Retrieval identifiability.** The HCN vertical profile is not unique given moderate optical thickness
  (2017Icar..286..289L) and a single line per species cannot constrain the HNC distribution
  (2014ApJ...795L..30C). Inspect averaging kernels and rerun with different a priori profiles before claiming
  resolved vertical structure (2017Icar..286..289L did both).
- **What cards flag as not stated.** For the RT itself, cards repeatedly note missing LIME grid and photon
  settings (2017A&A...605A..21C, 2012ApJ...757..129R), missing RADMC-3D photon count, grid and dust
  composition (2025ApJ...990..145L, 2019MNRAS.488.1005P), MCFOST setup (2025A&A...697A..64V) and MCMC priors
  and chain lengths (2016MNRAS.460.2933M, 2020MNRAS.497.2811K, 2015ApJ...812...27A). The pack aggregate of
  unstated settings is dominated by data reduction: CASA version (24), self-calibration intervals (11),
  line-free channels (10), image and cell size (10).

## Verification checks

What papers did:
- Continuum residuals consistent with noise, chi2 within 0.2% of an MEM model (2016MNRAS.460.2933M); for its
  CO the same paper only compares the model spectrum with half-disc spectra and finds a rough match. Flag
  >3 sigma residuals explicitly (2017A&A...605A..21C).
- Compare in several views at once: channel maps, PV diagrams, spectra, radial profiles
  (2012ApJ...757..129R, 2015ApJ...812...27A, 2020ApJ...898...10T).
- Cross-check with independent data: the SED (2018A&A...612A..72J), single-dish spectra
  (2016A&A...586A...5M), another band or epoch (the cycle-3-only refit in 2025ApJ...990..145L), scattered
  light (2021AJ....161..238W).
- Sampler convergence: chains longer than 50 autocorrelation times (2025ApJ...990..145L), effective sample
  size per parameter (2021AJ....161..238W).
- Goodness of fit: reduced chi2 near 1 (0.95 in 2017Icar..286..289L, 0.72 in 2015ApJ...812...27A); chi2
  likelihood corrected for correlated pixels (l_pix^2 / Omega_beam in 2025ApJ...990..145L) or for independent
  beams and channel correlation (2016MNRAS.460.2933M); full residual covariance (2021AJ....161..238W).
- Sensitivity tests on frozen assumptions: scale height changes flux <10% (2019MNRAS.488.1005P); 12m-only vs
  12m+ACA and distance tests (2024ApJ...966..117X); different uv coverage via 100 hour-angle realisations
  (2019ApJ...874...89C); compare with an earlier independent analysis (2020MNRAS.497.2811K); a priori
  profile, surface pressure and +-5% calibration tests with averaging kernels (2017Icar..286..289L).

What a careful referee adds:
- Rerun with 2-10x more photons or grid points and confirm the fitted parameters do not move.
- Inject the best-fit model into the real uv coverage plus noise and refit it to show the parameters are
  recovered (the simobserve tests above show the method).
- Vary opacity, CO/H2 (stating per H2 or per H), gas-to-dust, the temperature law and the flux scale one at a
  time and report the spread next to the statistical errors.
- For non-LTE models, show the result does not change when pumping, extra levels or alternative collision
  rates are included.
- Check that priors (uniform in cos i, log-uniform for masses as in 2021AJ....161..238W) are stated and do
  not drive the posterior.

## Source cards

All 274 papers are listed in references/sources.md. Some are off-topic for RT modelling and should be ignored:
regex hits on "synthetic", "simobserve" or "radiative transfer" in source-count, lensing, catalogue
completeness, SZ and extragalactic studies (e.g. 2015A&A...584A..78C, 2020ApJ...891...64F,
2020ApJS..251...14H, 2016PASJ...68...88K). I did not make a full exclusion list. The most informative cards:

- 2017A&A...605A..21C: LIME + vis_sample, abundance laws, visibility chi2 grid
- 2018A&A...612A..72J: RADMC-3D dust temperature feeding LIME; 3D envelope, disks, filament
- 2025A&A...697A..64V: MCFOST settling in 33 disks, ft + tclean, iterative surface-density fit
- 2021AJ....161..238W: joint HST + ALMA MCFOST MCMC with residual covariance
- 2016MNRAS.460.2933M: debris ring in uv plane; non-LTE CO with electron collisions
- 2020MNRAS.497.2811K: RADMC-3D + emcee on dirty images and cubes; mu = 14 debris gas
- 2025ApJ...990..145L: eccentric debris disk, correlated-pixel likelihood, convergence test
- 2015ApJ...813...99F: CO freeze-out at 19 K, photodissociation cut, LTE, mu = 2.37 in a turbulence study
- 2016MNRAS.461..385B: gas and dust modelling of HD 163296, Mgas x alpha_turb degeneracy
- 2018ApJ...854..177V: DALI settling defaults for transition disks
- 2019A&A...623A.150V: DALI CN rings, SED-constrained structure
- 2016A&A...586A...5M: 1D AGB shell grid, single-dish cross-check
- 2020A&A...633A..13D: SHAPE + LIME 3D AGB spiral, simalma
- 2024ApJ...966..117X: RADMC-3D LVG on MHD outflow, simalma tests
- 2015ApJ...812...27A: LTE disk MCMC plus infall models, simobserve filtering
- 2012ApJ...757..129R: LIME warp and non-Keplerian tests on TW Hya
- 2019ApJ...874...89C: simobserve tests of substructure as artefacts
- 2017Icar..286..289L: line-by-line retrieval with optimal estimation, averaging kernels
- 2025ApJ...986L..22R: SUBLIMED non-LTE comet coma fitted to visibilities
- 2024A&A...686A.274V: PORTAL line polarisation on LIME
- 2019MNRAS.488.1005P: RADMC-3D mass upper limits for circumplanetary disks
