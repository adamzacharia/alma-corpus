---
name: alma-radiative-transfer-modelling
description: "Build forward radiative transfer models of ALMA dust continuum and molecular line data (RADMC-3D, MCFOST, LIME, DALI, RATRAN and similar), turn them into synthetic observations, and compare them with the data the way published ALMA papers do. Use when fitting or interpreting disk, envelope, debris-belt, AGB-envelope, comet, galaxy-nucleus or planetary-atmosphere structure with a physical model, when deriving temperatures, gas masses, abundances, settling or turbulence from a model, when post-processing a simulation into synthetic ALMA images, or when testing whether an image feature is an interferometric artefact. Built from 656 ALMA papers (2012-2026)."
---

# Radiative transfer modelling of ALMA data

A radiative transfer (RT) model predicts what ALMA should see from an assumed physical structure (density,
temperature, dust, abundances, velocity field), so the fitted numbers are only as good as the assumptions you
froze. The two mistakes that matter most: (1) reporting a hand-tuned or grid model as a unique measurement when
the authors themselves report degeneracies (gas mass x alpha_turb giving the same SED in 2016MNRAS.461..385B;
optical thickness vs. dust scale height in 2025A&A...697A..64V; "thermochemical fits are not unique" in
2024A&A...687A.299L), and (2) comparing a sky model with interferometric data without reproducing the uv
coverage, which hides missing flux (2016A&A...586A...5M, 2014ApJ...796....1T, 2024A&A...686A.274V).

> Always report: code and version, grid and photon numbers, dust model (composition, size range, slope and the
> variable it refers to, opacity at the observed band, per dust or per gas mass), gas-to-dust ratio, abundance
> law with its denominator (per H2, per H nuclei, or by mass) plus freeze-out and photodissociation rules,
> mean molecular weight and the particle mix it assumes, LTE or non-LTE (collision data and source), the
> background radiation field (CMB at the source redshift), fixed geometry (d, i, PA), how the model became
> visibilities or images (including primary-beam handling), and the fitting method. Cards show these are often
> missing.

## When to use

- Protoplanetary disks (321 of the 656 pack papers are tagged protoplanetary_disks, pack aggregate): dust
  surface density and settling (2025A&A...697A..64V, 2021AJ....161..238W), hydrostatic structure
  (2019ApJ...881..108J), CO snow line (2013ApJ...774...16R, 2018A&A...609A..47P), turbulence
  (2016MNRAS.461..385B), abundance laws and rings in gapped disks (2017A&A...605A..21C, 2024A&A...687A.299L),
  line-ratio temperature probes (2021A&A...647A.118L), gas masses from rare isotopologues
  (2019ApJ...882L..31B (card)), gas surface densities from pressure-broadened CO wings (2025ApJ...984L..19Y).
- Protostellar envelopes and young disks: envelope structure (2018A&A...612A..72J, 2019A&A...628A..27B), disk +
  Ulrich envelope fits to visibilities and SED (2020ApJ...904...78S), infall plus rotation (2015ApJ...812...27A,
  2025ApJ...995L...7L).
- Debris belts: ring radius, width, height and dust mass (2016MNRAS.460.2933M, 2020MNRAS.497.2811K,
  2020MNRAS.498.1319M, 2025ApJ...990..145L); joint scattered light + SED (2024AJ....168..142L).
- Evolved-star envelopes: mass-loss history and abundance profiles (2016A&A...586A...5M, 2015ApJ...814..143A,
  2020A&A...633A..13D), molecule formation radii (2026A&A...711A.159M).
- Planetary atmospheres (2017Icar..286..289L), comets (cometary LIME in 2020NatAs...4..861C; SUBLIMED in
  2025ApJ...986L..22R), galaxy nuclei (non-LTE LIME in 2020ApJ...896...43W) and lensed dusty galaxies (LVG with
  a lognormal density PDF in 2026A&A...706A.174A).
- Synthetic observations of hydro or MHD simulations (2020ApJ...898...10T, 2024ApJ...966..117X,
  2019ApJ...874...89C), and model-based mass limits from non-detections (2019MNRAS.488.1005P).

## When not to use

| Situation | Use instead |
|---|---|
| Optically thin continuum, only a mass needed | single-temperature mass formula (`dust-continuum-mass`); 2019A&A...623A.150V uses it inside an RT study |
| One or a few lines, single-zone conditions | RADEX-type slab or LVG fit (`non-lte-excitation`); RADEX + MultiNest in 2017A&A...604A...2S |
| Column density from many lines in LTE | rotational diagram (`rotational-diagram-lte`) |
| Only stellar mass or rotation law | kinematic fitting (`keplerian-disk-kinematics`) unless optical depth matters |
| Ring and gap radii only | parametric uv fitting (`uv-plane-fitting`, `disk-substructure-profiles`) |
| Galaxy rotation curves | 3D kinematic tools (`galaxy-3d-kinematics`); GalPaK3D in 2021ApJ...909...84U |
| Source counts, completeness, SZ missing flux | injection-recovery with simobserve (2020PASJ...72...33K); no RT needed |
| Horizon-scale GRMHD imaging | GR ray tracing (ipole, RAPTOR in 2019ApJ...875L...5E; ipole + dynesty in 2024A&A...685A.142Y) |

## Steps

1. **Pick the observable and the code.** Dust temperature, continuum and scattered light: RADMC-3D or MCFOST;
   pdspy wraps RADMC-3D for visibility + SED fits (2020ApJ...904...78S); opacities from optool, often DSHARP
   (2024A&A...681A..82G). Non-LTE lines in 3D: LIME, often on a RADMC-3D dust temperature (2018A&A...612A..72J);
   RADMC-3D LVG mode (2024ApJ...966..117X). Chemistry coupled to structure: DALI (2019A&A...623A.150V,
   2024A&A...687A.299L, 2021A&A...647A.118L); Meudon PDR code for illuminated surfaces (2021A&A...647A..10G).
   1D AGB shells: DUSTY for dust, RATRAN for CO, an LVG code for HCN (2026A&A...711A.159M). Line polarisation:
   PORTAL on LIME output (2024A&A...686A.274V). Cores: LOC (2025A&A...700A.141H). Atmospheres: NEMESIS
   (2015ApJ...800L..14C, 2025PSJ.....6..286M). Counts per code are in Software.
2. **Fix what you can from outside the model.** d, i, PA, v_sys and stellar parameters usually come from
   continuum fits or literature (gas orientation fixed to the dust fit in 2016MNRAS.460.2933M). List them.
3. **Build the density structure** (ranges in the Parameter table and references/parameters.md).
   - Disks: tapered power law; gamma = 1 is a frequent illustrative start (2018ApJ...854..177V,
     2020ApJ...900....7H, 2019A&A...622A..75L), but grids span 0-2 (2013A&A...557A.133D). Check the sign
     convention: 2019ApJ...881..108J quotes gamma = -0.15.
   - Vertical structure: write the form out. Height form H(r) = H100 (r/100 au)^beta (H100 = 10 au with beta
     1.1 in 2019A&A...622A..75L and 1.15 in 2016ApJ...816...25P); aspect-ratio form h = H/r = h_c (r/r_c)^psi
     (h_c = 0.1, psi = 0.1-0.3 in 2021A&A...647A.118L); beta = 1 + psi (general practice). Some papers call
     the height exponent psi or p (psi = 1.15 in 2015ApJ...805...21C; p = 1.25 in 2021ApJ...908..250H), so
     check which exponent is meant before copying it.
   - Hydrostatic structure: iterate RT and hydrostatic equilibrium until T converges (within 3% in
     2019ApJ...881..108J) or say the scale height is not updated (2015ApJ...808..102K).
   - Cavities and gaps: separate gas and dust depletion (gas lowered by 1e-5 inside 15 au in
     2024A&A...687A.299L); say whether small dust follows the gas. Envelopes: Ulrich infall
     (2020ApJ...904...78S), rho ~ r^-1.5 (2019A&A...628A..27B) or a plateau (2018A&A...612A..72J).
   - AGB winds: rho(r) = Mdot / (4 pi r^2 v(r)) (general practice), so rho ~ r^-2 needs constant Mdot and v.
     2016A&A...586A...5M quotes r^-2 while v rises from 3 to 14.3 km/s; keep v(r) explicit. Add spirals or
     shells in 3D when the data show them (SHAPE plus LIME in 2020A&A...633A..13D).
4. **Choose the dust model.** A -3.5 size slope is the most common stated choice (45 of the 431 aggregate
   papers, count method under the Parameter table); others use q = 3 (2018MNRAS.477..325B) or fit it (2.5-4.5 in
   2020ApJ...904...78S). Define the variable: n(a) da ~ a^-q in grain radius. n(m) ~ m^-11/6 equals
   n(a) ~ a^-3.5 for compact grains of fixed density (general practice); 2018MNRAS.475.4924K gives q = 11/6
   without the variable, so check before comparing. Name the dust model (DSHARP, DIANA, astrosilicate) and give
   the opacity at the observed band (examples in references/parameters.md). Separate searched size ranges from
   fixed regional values (2018ApJ...869...10M grids a_min; 2023MNRAS.518.6092L fixes a_max = 10 cm only in the
   inner midplane).
   - Settling: two populations with mass fraction f_large and height ratio chi (f = 0.85, chi = 0.2 in
     2014A&A...562A..26B and 2018ApJ...854..177V; f = 0.99 in 2021A&A...647A.118L) or alpha-driven
     H_d = H_g (1 + St/alpha)^-1/2 (2025ApJ...984L..16G, 2025A&A...697A..64V).
   - Turbulence from settling is conditional. 2025A&A...697A..64V assumes rings are pressure maxima,
     fragmentation-limited grains (v_frag = 1 m/s) and vertical turbulence comparable to or above radial, fixes
     the size distribution and enlarges the stellar radius for four disks. Quote turbulence as conditional on
     such assumptions if you cannot test them.
5. **Set the temperature and the radiation field.** Compute T with Monte Carlo dust RT (2018A&A...612A..72J),
   iterate gas heating and cooling (DALI in 2021A&A...647A.118L), or impose T(r) = T0 (r/r0)^-q. q = 0.5 is a
   frequent illustrative start (2017ApJ...849...56A, 2020ApJ...900....7H; fitted 0.5 +- 0.1 in
   2025ApJ...995L...7L); seen from 0.2 (2014ApJ...796....1T) to 0.75 (2017SciA....3E2935L). For CO, separate
   midplane and atmosphere temperatures when the vertical gradient matters (Tatm/Tmid = 2 in
   2019NatAs...3..314L). T_gas = T_dust is the common assumption (2018A&A...609A..47P, 2026ApJ..1001..120X).
   - State the background field. Use T_CMB = 2.73 (1 + z) K for distant sources (2019ApJ...873...50D; 19.2 K
     at z = 6.02 in 2022PASJ...74.1429T). General practice: it lowers line and continuum contrast and sets a
     floor on T_ex.
   - Chemistry-based thermometers depend on the UV field, initial C/O and the network: 2021A&A...647A.118L
     assumes equal HCN and HNC photodissociation rates although HNC's may be twice as high. Run sensitivity
     tests on those before reading a line ratio as a temperature.
6. **Set the gas abundances and excitation.** Values in references/parameters.md.
   - Name the denominator. n_H = n(H) + 2 n(H2) counts H nuclei (2021A&A...647A..10G), so in fully molecular gas
     n_H ~ 2 n(H2) and CO/H2 = 2 x CO/H (general practice). Keep mass ratios apart: the 2019ApJ...881..108J value
     1.4e-4 is "in mass" and is not a number abundance.
   - CO abundance 1e-4 is the most common stated disk value (about 21 aggregate papers, method under the
     table), e.g. 2013A&A...557A.133D, 2018ApJ...859..111H, 2024A&A...687A.311A; number values range from 5e-5
     (2014ApJ...791...42Z) to 2e-4 (H2/CO = 5000 in 2014ApJ...792...68S). AGB envelopes use 2e-4 to 6.5e-4
     (2026A&A...711A.159M, 2020A&A...633A..13D).
   - Freeze-out: 20 K is the usual threshold (2018ApJ...859..111H, 2024A&A...687A.311A); 17 K
     (2014ApJ...792...68S) to 30 K in an envelope (2018A&A...612A..72J); grid 10-40 K in 2013A&A...557A.133D.
   - Photodissociation: CO is removed where the shielding column is below a threshold (1e21 cm^-2 of H2 in
     2017ApJ...851...85B; 2.0e20 H nuclei in 2019ApJ...881..108J; CO columns 1e18-1e20 tested in
     2016MNRAS.461..385B). State value, species and how the column is integrated.
   - Missing chemistry biases rings: omitting water photodesorption overpredicts HCO+ in the gap
     (2024A&A...687A.299L). State the chemical age or initial state and the network.
   - Isotopologues by ISM ratios (CO/13CO = 69, CO/C18O = 570 in 2019ApJ...883...98Z; 62 and 500 in
     2024ApJ...966..117X). Say whether isotope-selective photodissociation is included (not in
     2018ApJ...854..177V).
   - Excitation: 68 aggregate papers state LTE, 22 mention non-LTE, LVG, statistical equilibrium or collision
     rates (my regex). Use non-LTE for low-density gas, subthermal outer disks (2021A&A...647A.118L), debris gas
     with electron collisions (2016MNRAS.460.2933M), comae (2020NatAs...4..861C) and envelopes. Then check
     infrared pumping (partly included in 2015ApJ...814..143A), the level set (41 rotational levels in each of
     five vibrational states in 2026A&A...711A.159M), borrowed or scaled collision rates (2021A&A...655A..80D,
     2021A&A...647A..10G), the rate set itself (old vs. new CH3OH rates move E/A from 0.85-2.84 to 0.25-1.26 in
     2025A&A...699A..70H), and LVG validity (2017A&A...605A..28D).
   - Hyperfine and overlapping lines: say how they are treated when opacity is appreciable. 2025A&A...700A.141H
     assumes LTE between hyperfine components and leaves out overlap; 2025A&A...693A.160M uses an average source
     function for overlap; MOLLIE models HCN hyperfine optical depths in 2024MNRAS.532L..36R.
   - Mean molecular weight: give the particle mix. mu = 2.37 per particle for H2 + He (2012ApJ...757..129R,
     2025ApJ...994..214T); about 2.8 per H2 (2024ApJ...976...29H); mu_H = 1.41 (2026AJ....171..368M). Debris-gas
     papers adopt mu = 14 (2020MNRAS.497.2811K, 2020ApJ...892...99C; 14 or 2.3 tested in 2026A&A...705A.202M)
     without the cards stating the mix. General practice: pure CO gives mu ~ 28 and an equal-number C + O atomic
     mix gives ~14, so derive mu from the composition you assume.
7. **Run the RT with enough photons and grid.** Visible pack examples for thermal and mm images cluster near
   1e8 photon packages (2024ApJ...966..117X, 2026A&A...705A.203W) and run from 5e7 (2016MNRAS.461..385B) to
   1.6e9 (2025ApJ...989L..43Y); these are examples, not the full range. Budgets differ by task: 3e8 for
   temperature and images but 1e7 for the SED in 2021ApJ...909..212K; 1e7 for continuum and 1e9 for ALMA
   polarization in 2024NatAs...8.1148U (card); 1e5-1e9 tested in 2019A&A...627A.114K. Use the modified random
   walk in thick regions (2024ApJ...966..117X). LIME runs on 1e5 grid points (2017A&A...605A.126R).
8. **Turn the model into what ALMA measured.**
   - Best: sample model visibilities at the observed uv points (vis_sample in 2017A&A...605A..21C; uvsim in
     2016MNRAS.460.2933M; Fourier transform of RADMC-3D images in 2020ApJ...904...78S) and fit in the uv plane.
     Apply the primary beam and match the spectral sampling first (general practice).
   - Or simulate with the real configuration and image like the data: simalma (2024ApJ...966..117X),
     simobserve with the science hour angle and configuration (2020NatAs...4..861C), or ft + tclean with an
     iterative surface-density correction (2025A&A...697A..64V).
   - Measure the filtering: up to 20% of flux filtered in 2026A&A...711A.159M; I_out = c1 I_in + c0 with
     c1 = 0.94 +- 0.02 over simobserve noise realisations in 2020PASJ...72...33K.
   - Image-plane fits need primary-beam handling, masks and a noise model: 2025ApJ...990..145L fits a
     PB-corrected image, reweights chi2 for correlated pixels and reports non-Gaussian noise.
   - Beam convolution of the sky model is cheapest and ignores missing flux (2019A&A...623A.150V).
   - Lines: continuum oversubtraction or line blocking by dust can cut line flux (2025A&A...693A.101T); compare
     subtracted and unsubtracted cubes and document excluded regions (inner 50 au in 2017A&A...605A..21C).
   - Joint visibility + SED fits need explicit weights (w_vis = 0.5, w_SED = 1 in 2020ApJ...904...78S).
9. **Compare and fit.** Choose a likelihood and say how correlated pixels or channels are handled. The pack's
   fitting aggregate has 40 distinct phrasings and 43 occurrences; by my keyword rule (references/parameters.md)
   10 phrasings use a sampler, 12 occurrences use chi2 or chi2 grids, 7 are manual or by-eye. These are
   phrasings, not paper frequencies. Use a sampler (emcee is named in 73 matched steps) when you need
   uncertainties, and a grid when the model is slow (4096 RADMC-3D models in 2019ApJ...881..108J; about 2500
   DALI models in 2024MNRAS.534.3576K).
10. **Report the systematics.** Rerun with frozen assumptions varied (opacity, CO abundance, gas-to-dust, T law,
    collision rates, background field) and quote the spread: CO abundance x2 in 2026A&A...711A.159M; one
    parameter at a time in 2024A&A...687A.299L. In 2020NatAs...4..861C, at nominal electron scaling x_ne = 1.0,
    T_kin from 20 to 70 K changes production rates by <8%; at x_ne = 0.2 HCN is more sensitive (1.2e24 s^-1 at
    20 K vs. a nominal 7.0e23 s^-1). Include the flux scale: 2020ApJ...892...99C left it out of the MCMC,
    2017Icar..286..289L tested +-5%.

## Parameter defaults and ranges

Common choices are illustrative starting values, not modes, unless a count is given. Counts are distinct papers
among the 431 with lines in the pack's Key parameters or Assumptions aggregates (both truncated, 312 and 167 rows
not shown, so counts are lower bounds), from my regex over those lines. Fuller tables, all example bibcodes and
sampler, opacity and simobserve settings are in references/parameters.md.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Size slope q, n(a) ~ a^-q | 3.5 | 2.5-4.5 (fitted or gridded) | 45 state -3.5 | 2016MNRAS.460.2933M, 2018ApJ...869...10M |
| Grain size range | 0.005-0.1 um to 1-3 mm | a_min 0.001 um (2022A&A...665A..82O) to 20.5 um (top of a grid, 2018ApJ...869...10M); a_max 1 um (2019A&A...627A.114K) to 10 cm (fixed inner midplane, 2023MNRAS.518.6092L) | many | 2025A&A...697A..64V, 2021AJ....161..238W |
| Opacity at 1.3 mm (per dust) | 2.2-2.3 cm2/g | 0.95-3.95 cm2/g | 8 give 2.2-2.31 | 2018ApJ...859..111H, 2019MNRAS.488.1005P |
| Gas-to-dust (mass) | 100 | ~10 (2024ApJ...970..114T) to 300 (2019A&A...629A.146V) | 59 mention 100 | 2024ApJ...966..117X, 2021A&A...647A.118L |
| Surface density index gamma | 1 (tapered) | 0-2 (grid, 2013A&A...557A.133D); signs differ | >10 | 2018ApJ...854..177V, 2023MNRAS.518.6092L |
| Characteristic radius R_c | 50-300 au | 15 (2021A&A...647A.118L) to 320 au (2020ApJ...895L..18B (card)) | >15 | 2025ApJ...984L..16G, 2024AJ....167...77D |
| Scale height H100, beta | ~10 au, ~1.1 | H100 5-15 au, beta 1.0-1.2 (2024ApJ...966...59S (card)); height exponent 1.25 (2021ApJ...908..250H) | ~10 | 2019A&A...622A..75L, 2013A&A...557A.133D |
| Temperature index q | 0.5 | 0.2 (2014ApJ...796....1T) to 0.75 (2017SciA....3E2935L) | >8 | 2017ApJ...849...56A, 2020ApJ...900....7H |
| CO abundance, disks (number, per H2) | 1e-4 | 5e-5 (2014ApJ...791...42Z) to 2e-4 (H2/CO = 5000, 2014ApJ...792...68S); 1.4e-4 by mass (2019ApJ...881..108J) is not comparable | ~21 | 2018ApJ...859..111H, 2024A&A...687A.311A |
| CO abundance, AGB envelopes | 2e-4 to 6.5e-4 | up to 1e-3 (2020A&A...640A.133R, 2024A&A...687A.112M) | >6 | 2026A&A...711A.159M, 2016A&A...586A...5M |
| CO freeze-out temperature | 20 K | 17-30 K; grid 10-40 K | 13 mention freeze-out | 2014ApJ...792...68S, 2018A&A...612A..72J |
| Mean molecular weight | 2.37 per particle (H2 + He) | 2.3-2.8 by convention; 14 adopted for debris gas | 15 give a value | 2012ApJ...757..129R, 2020MNRAS.497.2811K |
| Background temperature | 2.73 K locally | 2.73 (1 + z) K, e.g. 19.2 K at z = 6.02 | 15 mention CMB or T_bg | 2019ApJ...873...50D, 2022PASJ...74.1429T |
| Disk microturbulence | 0-0.05 km/s | 0-0.3 km/s (grid, 2013A&A...557A.133D) | ~8 | 2015ApJ...812...27A, 2017ApJ...839...86H |
| Envelope/wind turbulence | 1 km/s | 0.5 (2024A&A...687A.112M) to 3 km/s (2024A&A...681A..17D); radial 11 to 1 km/s (2020MNRAS.494.1323D) | >6 | 2024A&A...686A.274V, 2017A&A...597A..99W |
| Photon packages (thermal, mm) | ~1e8 (examples) | 5e7 to 1.6e9 seen; 1e6-1e7 for images or SEDs | ~12 lines | 2024ApJ...966..117X, 2021ApJ...909..212K |
| emcee walkers x steps | ~100 x 1000 | 16 (2024AJ....168..142L) to 500 walkers (2018ApJ...859..111H); 300 to ~10,000 steps | 22 give walkers | 2017ApJ...839...86H, 2020MNRAS.497.2811K |

Turbulence linewidths: say whether the value is a Doppler b, a dispersion or a FWHM (2024ApJ...966L..13D quotes
FWHM). Gas-to-dust note: the 2018A&A...612A..72J card reads "Dust-to-gas mass ratio 100", probably an inverted
label; verify before citing it.

## Software

Counts from the pack aggregate "Software named in the matched steps" (matched analysis steps, not papers;
spelling variants are separate entries, so do not sum them). Full list in references/parameters.md.

| Tool | Steps | Used for |
|---|---|---|
| radmc-3d (also radmc3d 16, radmc 6, radmc3dpy 5) | 215 | dust temperature, continuum, scattering, LTE/LVG lines (2016MNRAS.460.2933M, 2024ApJ...966..117X) |
| casa (also tclean 15) | 106 | imaging and observing simulations |
| lime | 83 | non-LTE 3D lines (2017A&A...605A..21C, 2020NatAs...4..861C) |
| dali | 80 | thermochemical disk models (2019A&A...623A.150V, 2024A&A...687A.299L) |
| mcfost | 77 | disk dust RT, settling, scattered light + mm (2021AJ....161..238W, 2025A&A...697A..64V) |
| emcee | 73 | MCMC over model parameters (2020MNRAS.497.2811K, 2025ApJ...990..145L) |
| casa simobserve (also simobserve 23) | 43 | synthetic observations, filtering tests (2015ApJ...812...27A, 2019ApJ...874...89C) |
| radex (also spectralradex 6) | 29 | slab excitation checks (2025A&A...699A..70H) |
| vis_sample, galario, optool | 20, 16, 14 | model visibilities at observed uv points (2017A&A...605A..21C); dust opacities (2024A&A...681A..82G) |
| ratran, mollie, nemesis | 9, 5, 4 | 1D non-LTE lines (2026A&A...711A.159M); hyperfine lines (2024MNRAS.532L..36R); atmospheres |

## Pitfalls

- **Non-unique models.** Stated as not unique, not optimized or degenerate in 2012ApJ...757..129R,
  2013ApJ...774...16R, 2016A&A...586A...5M, 2018ApJ...859..111H and 2024A&A...687A.299L; 2018A&A...612A..72J
  calls its match qualitative. Named degeneracies: Mgas x alpha_turb (2016MNRAS.461..385B), optical thickness
  vs. scale height (2025A&A...697A..64V), mass-loss rate vs. abundance radius, temperature and velocity
  (2016A&A...586A...5M), scattered-light geometry vs. grain properties (2024AJ....168..142L).
- **Geometry too simple.** 1D models of asymmetric emission (2026A&A...711A.159M); single power laws leaving
  50% residuals inside 1 arcsec (2025ApJ...995L...7L). Show residual maps.
- **Optical depth weakens mass constraints.** Thin-emission mass estimates become lower limits when emission is
  thick (2025NatAs...9.1833L (card), 2020ApJ...890..130T; analytic masses in 2020ApJ...904...78S; dust masses
  likely underestimated in 2020ApJ...889...59P). A full RT fit can still constrain mass from a thick line
  (12CO models in 2019ApJ...881..108J), but only under its temperature, structure and CO/H2 assumptions. Rarer
  isotopologues help (13C17O in 2019ApJ...882L..31B (card)). At cm wavelengths remove free-free first (57% of
  the 9 mm flux in 2020ApJ...904...78S).
- **Gas mass vs. CO abundance.** 1/X_CO only for a thin line at fixed excitation (general practice); X_CO^-0.5
  from pressure-broadened wings (2025ApJ...984L..19Y). Otherwise vary X_CO and refit (2019ApJ...881..108J).
- **Dust mass and scattering.** Mass depends on composition, a_max and kappa (2016MNRAS.460.2933M); kappa0 is
  uncertain by a factor of two (2015ApJ...808..102K). Scattering is off at sub-mm in some models
  (2019A&A...628A..27B), but thick scattering can push the spectral index below 2 (2021ApJ...909..212K); say
  if isotropic, Henyey-Greenstein or full matrix (2025A&A...696A.232G).
- **Missing flux.** Without ACA or TP extended flux is lost (2016A&A...586A...5M, 2018ApJ...859..111H); a small
  MRS filters [C I] at large radii (2024A&A...687A.299L); filtering inflated polarisation fractions 2-3x
  (2024A&A...686A.274V); a smooth model underestimates peak flux (2019ApJ...874...89C).
- **Other traps.** Inconsistent physics between steps (isothermal hydro vs. power-law RT temperature in
  2014ApJ...796....1T); cloud contamination blocking a gas mass (2015ApJ...806L..22C); T_kin outside the
  collision-rate grid gets clamped (2025A&A...699A..70H).
- **Errors too small.** Statistical errors only (2016MNRAS.463L..74K, 2025A&A...700A.141H); local-optimum
  stability, not a posterior (2024NatAs...8..765L); retrievals not unique (HCN in 2017Icar..286..289L; one line
  cannot constrain HNC in 2014ApJ...795L..30C), so inspect averaging kernels and vary the a priori profile.
- **What cards flag as not stated.** LIME grid, photon and collision-file settings (2012ApJ...757..129R,
  2020ApJ...896...43W), unreleased RT code (2018A&A...612A..72J), MCFOST input files and prior bounds
  (2024AJ....168..142L). The pack aggregate of unstated settings is led by CASA version (39) and
  self-calibration intervals (20).

## Verification checks

What papers did:
- Residuals consistent with noise (2016MNRAS.460.2933M continuum; its CO only roughly matches half-disc
  spectra). Show a simpler model fails: no-gap model misses visibility wiggles (2020MNRAS.498.1319M); chi2 heat
  maps plus high- and low-mass channel maps (2019ApJ...881..108J).
- Compare channel maps, PV diagrams with residuals, spectra and radial profiles (2015ApJ...812...27A,
  2025ApJ...995L...7L); cross-check with the SED, single-dish spectra or scattered light (2020ApJ...904...78S,
  2016A&A...586A...5M, 2021AJ....161..238W).
- Sampler convergence: >50 autocorrelation times (2025ApJ...990..145L); a second sampler (Nautilus vs.
  UltraNest in 2025A&A...699A..70H). Reduced chi2 near 1 (0.72 in 2015ApJ...812...27A, 1.11 in
  2024AJ....168..142L), with correlated pixels accounted for (2025ApJ...990..145L).
- Sensitivity tests: scale height changes flux <10% (2019MNRAS.488.1005P); f_large 0.9-0.99 no change
  (2021A&A...647A.118L); 12m-only vs. 12m+ACA (2024ApJ...966..117X); 100 hour-angle realisations
  (2019ApJ...874...89C); recover a synthetic data set first (2024A&A...685A.142Y).

What a careful referee adds:
- Rerun with 2-10x more photons or grid points; inject the best fit into the real uv coverage plus noise and
  refit. Vary opacity, CO abundance (with denominator), gas-to-dust, T law, background field and flux scale one
  at a time; report the spread beside the statistical errors.
- For non-LTE, show stability to pumping, extra levels, hyperfine treatment and alternative rates. Check priors
  are stated and no parameter sits on a bound (2024AJ....168..142L).

## Source cards

All 656 papers are in references/sources.md; many are off-topic regex hits (source counts, lensing, SZ, solar,
horizon-scale, e.g. 2020PASJ...72...33K, 2019ApJ...875L...5E). The most informative cards:

- 2017A&A...605A..21C: LIME + vis_sample, abundance laws, visibility chi2 grid
- 2018A&A...612A..72J: RADMC-3D temperature feeding LIME; 3D envelope and disks
- 2019ApJ...881..108J: hydrostatic iteration, 4096-model grid, photodissociation per H nuclei
- 2024A&A...687A.299L: DALI gapped-disk chemistry, one-at-a-time variations
- 2021A&A...647A.118L: DALI HNC/HCN temperature probe, settling test
- 2025A&A...697A..64V: MCFOST settling in 33 disks, ft + tclean
- 2024AJ....168..142L: MCFOST MCMC, scattered light + SED, prior-bound warnings
- 2020ApJ...904...78S: RADMC-3D + pdspy + emcee, free-free correction
- 2016MNRAS.460.2933M: debris ring in uv plane; non-LTE CO with electrons
- 2025ApJ...990..145L: correlated-pixel likelihood, convergence test
- 2016A&A...586A...5M: 1D AGB shell grid, single-dish cross-check
- 2026A&A...711A.159M: DUSTY + RATRAN + LVG, measured filtering
- 2020NatAs...4..861C: cometary LIME, excitation tests
- 2017Icar..286..289L: optimal-estimation retrieval, averaging kernels
