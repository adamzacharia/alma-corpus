# Chemical modelling: per-paper setup values

Every row comes from the evidence pack's "Key parameters", "Assumptions" and excerpt lines for this
technique. Values found only in the methods card of a pack paper (`cards/<bibcode>/sonnet/card.md`, read
during review) are marked "card". Blank cells mean neither states the value for that paper.

Density convention: nH = total hydrogen nuclei, n(H2) = molecular hydrogen, plain n = the source does not
say which. Model abundances are gas phase unless marked otherwise.

## Hot cores, hot corinos and complex organics

| Bibcode | Code | Physical history | Cosmic-ray rate (s^-1) | Other fixed inputs | Compared quantity |
|---|---|---|---|---|---|
| 2014Sci...345.1584B | MAGICKAL | free-fall collapse nH 3000 to 2e8 cm^-3, static warm-up to 400 K | | radical-site bias toward secondary carbon; other rates and binding energies identical between isomers | i/n propyl cyanide, model peak T vs Trot |
| 2016A&A...587A..92M | MAGICKAL | collapse then warm-up 8 to 400 K, nH 2e8 | | min dust T 8 K; S 8e-8; E_b CH3SH 5534 K, C2H5SH 6230 K | CH3SH/C2H5SH ratio |
| 2017A&A...601A..48G | MAGICKAL (three-phase) | free-fall collapse, warm-up 8 to 400 K at three timescales | 1.3e-17 | nH 2e8 post-collapse; 0.1 um grains | i/n ratios, ice abundances |
| 2017A&A...601A..49B | MAGICKAL | cold collapse then warm-up 8 to 400 K, intermediate timescale | | nH 2e8; min dust T 8 K; E_b CH3NCO 3575 K, CH3NHCHO 6281 K | ratios to HNCO |
| 2019A&A...628A..10B | MAGICKAL | cold collapse, warm-up to 200 K in 5e4, 2e5 or 1e6 yr | 1.3e-17 | E_des CH3NCO 6486 K, N-methylformamide 7386 K | peak gas-phase ratios |
| 2019A&A...628A..27B | MAGICKAL | 18 models per source: 6 CRIR x 3 Tmin | 1.3e-17 to 1.3e-14 | ISRF 1 G0; 1333 species, 13374 reactions | source-to-source abundance pattern |
| 2016ApJ...825...79S | NAUTILUS (card) | collapse plus warm-up, four models A to D (card) | | physical model after the Garrod 2013 fast warm-up (card) | CH2NH abundance |
| 2017MNRAS.469.2230M | UCL_CHEM (three-phase) | constant n(H2) 5e8 (the paper says H2 gas density), T 10 to 110 K over 1e5 yr | | | CH3NCO abundance; L1544 upper limits |
| 2024ESC.....8..665M | UCLCHEM (two-phase) | Phase I nH 300 to 1e8 at 10 K; Phase II 10 to 300 K at 1e8 | 1.3e-17 | initial Av 2; sticking 1; solar O, C, N, He; Si, S, Cl, Mg, P, F depleted by 100 | peak NH2CN 5.12e-10 at about 3.8e5 yr, on the grain (grain-surface value, compared with the observed gas-phase abundance) |
| 2020ApJ...891..164S | gas-grain | cold 1e5 yr (Av 1 to 5), warm-up 5e4 yr to 150 K at 6e6 cm^-3 (Av 100), post-warm-up 1e5 yr | | LMC Z = 1/3, gas-to-dust 300, chi_UV 3 | LMC vs Galactic hot core |
| 2019ESC.....3.2088S | Taquet et al. model | fixed conditions, ices injected at t = 0 | 3e-17 | n_H2 5e7, T 150 K | CH3OCH3/CH3OH, HCOOCH3/CH3OH |
| 2024A&A...691A.180F | UCLCHEM (static grid, 65536 models) | isothermal constant-density cloud, R 0.5 pc | gridded | Av 1 mag at edge; gas-to-dust 100; 12C/13C = 10^1.8; ratios at 1e6 yr | column-density ratios, 50 lowest MSE |

## Cold clouds, prestellar cores and protostellar envelopes

| Bibcode | Code | Setup | Cosmic-ray rate (s^-1) | Other | Compared quantity |
|---|---|---|---|---|---|
| 2024A&A...687A.233M | NAUTILUS | homogeneous gas, density 2.5e4, 10 K gas and dust, Av 10 | 1.3e-17 | | H2NCO upper limit |
| 2024ApJ...968L..19F | three-phase rate equations | 1e5 yr (3e4 and 1e6 yr tested); volatile P 2.57e-7 to 2.57e-9 | 3e-17 | chemical desorption 4% (2 and 8% tested); photodesorption 1e-3 | PH3 limit to volatile P < 5e-9 |
| 2015ApJ...803...70S | gas-grain | constant T 10, 30, 100 K; n 1e4 or 1e6; o/p H2 0.01 and 0.001 | 2.6e-17 | Av 10 | DNC/HNC |
| 2018A&A...617A.120M | analytic steady-state H2D+/DCO+ network + RATRAN | T_sub 20 to 40 K, n_de 1e5 to 1e8, X[CO] 1e-7 to 1e-4 | 1.26e-17 | H2 o/p lower limit 1e-3 | DCO+ radial profile, by eye |
| 2025ApJ...992...55T | network + LIME (LTE) | static collapse-model profiles, 2e5 yr | | | o-H2D+ brightness, qualitative |
| 2019A&A...624L...5P | gas-phase deuteration network | start D2CO/H2CO about 0.01, NH2D/NH3 about 0.3, n 1e5, 150 K | 1e-15 | low extinction | drop of D ratios in 500 to 1000 yr |

## Protoplanetary disks

| Bibcode | Code | Structure | Cosmic-ray rate (s^-1) | Other fixed inputs | Age |
|---|---|---|---|---|---|
| 2016ApJ...831..101B | Du and Bergin + Monte Carlo RT | three-component dust disk; parametrised C and O depletion | about 1e-19 (attenuation 96 g cm^-2) | gas-to-dust 100; size index 3.5; TW Hya UV field for both disks; 8:2 astrosilicate:graphite | 5 Myr (TW Hya), 1 Myr (DM Tau) |
| 2015ApJ...810..112O | gas-grain + LIME | generic T Tauri disk, static | 1e-20 test | CO E_b 1150 K (1000 K tested); CO photodesorption 7e-3 | 300 kyr |
| 2017A&A...599A.101V | reduced network (SciPy odeint) on DALI structure + LIME (card) | TW Hya | 1.2e-17 (1e-19, 5e-17 variants) | CO, N2 E_b 855, 800 K and sticking 0.9, 0.85 (card); gas-phase CO and N2 formation ignored | to 1e6 yr (card) |
| 2017ApJ...835..228T | ALCHEMIC + LIME + simobserve (card) | Gorti et al. fiducial, Gaussian surface-density dips (card) | 1.3e-17 | grain radius 7 um | 1 Myr (card) |
| 2018A&A...617A..28S | ALCHEMIC | 1+1D; Mdisk 0.066 Msun, Mdot 5e-9 Msun/yr, alpha 0.01, Rout 800 au, Lx 1e31 erg/s | | 0.1 um grains; gas-to-dust 100; Tgas = Tdust; C/O 0.46, 1.0, 1.2 | 5 Myr |
| 2018ApJ...859..131L | disk chemistry (5970 reactions, 600 species) + RADMC-3D line transfer + vis_sample (card) | SED and HD constrained TW Hya model (card) | | d 59.5 pc, PA 155 deg, i 8 deg, M* 0.8 Msun | 1 Myr (card) |
| 2019ApJ...876...72L | NAUTILUS v1.1 (three-phase) | 1+1D parametric; Md 0.18 and 0.03 Msun, Rc 100 au | | 0D cloud initial conditions; S 8e-8; 0.1 um grains; dust-to-mass 0.01; Tgas = Tdust | 1 Myr |
| 2019ApJ...883...98Z | RAC2D | smooth profiles, no substructure | 1.36e-18 (standard), 1.36e-17 (high) | CO 1.4e-4 per H; CO/C18O 570, CO/13CO 69; gas-to-dust 100 | 1 Myr |
| 2019ApJ...875...96N | disk chemical model + modified 1D RATRAN | HD 163296 | | water OPR 3; 16O/18O 560; kappa_mm 1.0 cm2/g scaled x1 to x10 | |
| 2024JKAS...57..163L | PURE-C one-point | n 2.2e10 (inner), 6.0e7 (outer); UV 0; quiescent then burst | 1e-17 | KIDA barriers 2000 K and 1130 K tested | |
| 2024RAA....24g5017M | NAUTILUS; RADMC3D for dust temperature only | 1 Myr cloud stage (10 K, nH 2e4, Av 15), then parametrised disk, two-layer gas T | 1.3e-17 | C/O 0.5 to 1.5 | 1e7 yr |
| 2021A&A...651L...6B | literature models | NH 1.6e22 cm^-2 at 60 au from disk model | | | CS/SO, S/H 4.6 to 10.0e-7 |

Disk thermo-chemical models used for structure or gas mass (variant):

| Bibcode | Code | What was varied | Fixed inputs | Fit |
|---|---|---|---|---|
| 2016A&A...585A..58V | DALI | surface density, gas-to-dust, outer radius, cavity radius, delta | Sigma(r) power law with exponential cutoff, gamma 1; gas and dust share the profile | by eye; radii within 5 au, delta within an order of magnitude |
| 2019ApJ...871..107F | DALI | Sigma_c, gamma, R_c, then delta_gap, delta_ring | gaps at 54 to 70 and 87 to 119 au; C, O 1.35e-4, 2.88e-4 | parametric grid; best delta_gap 0.1 |
| 2025ApJ...989....1Z | DALI grid | 13CO, C18O, N2H+ (or C17O) fluxes plus 1.3 mm continuum | gas mass: thermo-chemical grid (its parameters not stated); dust mass: separate optically thin continuum estimate with kappa 2.3 (nu/230 GHz) cm2/g and average Tdust 20 K (not the DALI temperature structure); xCO 1e-4 for Ophiuchus | grid comparison |

## Envelopes of evolved stars

| Bibcode | Code | Setup | Cosmic-ray rate (s^-1) | Other |
|---|---|---|---|---|
| 2019A&A...629A.146V | gas-phase photochemistry, about 8000 reactions | expansion from 2e14 cm | 1.2e-17 | NH/Av 1.5 times lower than classical; SiS photodissociation set equal to SiO |
| 2017A&A...601A...4A | Meudon PDR code | isotropic expansion from 2e14 cm, Draine field | 1.2e-17 | d 123 pc; C2H2 8e-5, HCN 4e-5 relative to H2 |
| 2015ApJ...814..143A | UMIST + KIDA network | initial radius 2e14 cm; N2 4e-5; clumpy variant | 1.2e-17 | |
| 2018A&A...612L..11S | UCL_CHEM-type CSE model + mcp | spherical, uniform expansion, ISRF only | | Mdot 2.5e-7 Msun/yr, v_exp 2.5 km/s, 12CO/H2 5e-4, 13CO/H2 5e-5 |
| 2021A&A...655A..80D | RATE12 + Al chemistry (Gaussian 16, MESMER) | 1D | | H35Cl/H37Cl 2.4; transition states tuned within 6 kJ/mol |
| 2016A&A...592A..76D | analytic NaCl gas-grain partitioning (accretion, thermal and photodesorption), not photodissociation shells | n_H 1e8 at about 10 R*; T_b 5000, 10000, 15000 K | | dust-to-gas 0.002; grains 0.005 to 0.25 um; S = 1; solar Cl 3.2e-7 |

## Diffuse and extragalactic gas

| Bibcode | Code | Setup | Notes |
|---|---|---|---|
| 2019A&A...622A..26G | analytic steady state | HOC+/H2O and CF+/HF with Langevin or enhanced capture rates | C+ main carbon carrier and electron source |
| 2017A&A...608A..96L | NAUTILUS gas-phase, nuclear-spin network (card) | nH 2e2 to 2e4, T 10 to 100 K (card) | Av 1 to 3 mag; 0.1 um grains; dust-to-gas 1% |
| 2025A&A...696A..31G | Chempl static and PDR; UCLCHEM C-type shocks | PDR fiducial T 500 K, n 1e3; shock preshock density 1e3 | Tdust = Tgas in static models |
