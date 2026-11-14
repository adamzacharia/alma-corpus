# Per-paper simulation setups (from the hydro-simulation-comparison pack)

Values are copied from the pack's key-parameter, assumption and excerpt lines. Off-topic paper excluded:
2018MNRAS.474.5105B. "-" means the pack does not give it.

## Planet-disk, SPH (PHANTOM unless noted)

| Bibcode | Star / disk | Viscosity, h/r | Dust | Particles, run length | Post-processing |
|---|---|---|---|---|---|
| 2019NatAs...3.1109P | 2.4 Msun, 185 pc, gas 1e-2 Msun, 40-700 au | alpha_SS ~1e-3, h/r 0.06 at 40 au, vertically isothermal | 11 bins 1.5625-1600 um, dust-to-gas 1/100 | 2e6, 800 orbits; planets 1 MJup at 30 au, 1-5 MJup at 130 au | MCFOST, 13CO 7e-7, turbulence 50 m/s, 50 m/s channels binned and Hanning smoothed |
| 2025ApJ...984L..15P | disk 5e-3 Msun, inner radius 5 au, no self-gravity | alpha_av 0.2, H/R 0.1 at 50 au, gamma 0.8 | gas only in hydro; RT astrosilicate 0.03-1000 um, gas-to-dust 100 | 1e6 initial, 20 orbits, then each particle split into 13 (1.3e7) for 2 more orbits; planet accretion radius 0.125 Hill | MCFOST, 12CO 1e-4 rel. H, depleted below 20 K by a free factor |
| 2023MNRAS.526L..41P | 1.5 Msun, 140 pc, disk 0.01 Msun | H/R 0.1 at 50 au | 11 sizes 1 um-1 mm | 1e6, 100 orbits; planets 1-10 MJup at 65 au | MCFOST, Tgas = Tdust, LTE, zero turbulence |
| 2020ApJ...888L...4T | 1.65 Msun, 5-150 au, gas ~1e-2 Msun, dust 1.2e-4 Msun | alpha_SS 0.005, locally isothermal | 1 mm | 1e6; two migrating, accreting planets; match at 160 orbits | - |
| 2019A&A...622A..75L | MWC 480 | alpha_AV ~0.15 (alpha_SS ~5e-3), locally isothermal | one-fluid, dust-to-gas 0.01-0.2 | 5e5; planets 0.4-2 MJ at 85-120 au | RADMC-3D profile comparison, by eye |
| 2018MNRAS.475.5296D | Elias 24, 1-180 au | alpha_AV 0.1 (alpha_SS ~0.003), vertically isothermal | 1 mm, dust-to-gas 0.1 | 1e6; migrating, accreting planet; snapshot by eye | RADMC-3D, CASA simulator |
| 2024A&A...688A.102T | GG Tau A triple, Rout 800 au, disk 0.12 Msun | alpha_SS 0.005, T = 20 K (R/300 au)^-0.9 | 1 mm, dust-to-gas 0.01 | 1e6, up to 3000/1500 orbits | MCFOST |
| 2020MNRAS.499.3837G | HD 100453, disk 0.003 Msun, 12-60 au, Sigma ~ R^-1 | alpha_SS 5e-3, H/R 0.05 at 12 au | gas, then gas + 11 grain sizes | seven candidate orbital configurations of the companion; rewind runs (final orientation checked after 10 orbits) | MCFOST |
| 2020MNRAS.499.3857N | HD 100453 inner companion | alpha 5e-3 | dust and gas well coupled | planets 5, 10, 20 MJ at 10, 15, 20 au | inner edge at 10% of max Sigma |
| 2020ApJ...895L..18B | GW Ori, 0.1 Msun, 40-400 au | alpha_AV 0.31, h/r 0.05, locally isothermal | - | 1e6 | - |
| 2024MNRAS.534.2904C | primary 2 Msun; HD 142527 rescaled to 1.8 Msun, x3.8 length | p = 1, q_T = 0.25, locally isothermal | gas only | 5e6 | MCFOST; eddy, bettermoments |
| 2017ApJ...839L..24M | 0.5 Msun, 10-400 au (SPH code not named) | alpha_SPH 0.1-1.0, beta_SPH = 2 alpha_SPH, flux-limited diffusion | well mixed | 2.5e5 | RADMC-3D at 1.3 mm, 0.005-1000 um, slope -3.5 |
| 2019A&A...624A..33V | MA 1.7, MB 0.3 Msun, a = 120 au, disk 0.003 Msun, 12-96 au | alpha_SS 5e-3, H/r 0.05 | 1 mm | - | - |
| 2019NatAs...3..278K | polar circumbinary disk | - | - | 3e5 | - |

## Planet-disk, grid codes

| Bibcode | Code | Grid, domain | Viscosity, h/r | Dust, run length |
|---|---|---|---|---|
| 2015ApJ...809...93D | FARGO (2-fluid) | 256x256, 1-500 au | alpha 0.001, T = 221 (r/AU)^-1/2 K | 1 mm, dust-to-gas 0.9%, Sc = 1, Epstein drag, no feedback |
| 2016PASJ...68...43K | FARGO (2D) | 1024x2048, R/Rp 0.4-4.0, smoothing 0.6 hp | grid over Mp, h/R, alpha | 1e4-1e5 orbits; runs calibrate the gap-width formula listed below |
| 2016ApJ...819..134B | FARGO (2-fluid) | - | alpha 1e-4, (H/R)p 0.1, Sigma ~ R^-1 | 0.1 um-5.3 mm, a^-3.5, 3 g cm^-3; 100 orbits |
| 2018ApJ...869L..47Z | Dusty FARGO-ADSG | - | h/r 0.05, 0.07, 0.1; alpha 1e-4, 1e-3, 1e-2; q 3.3e-5 to 3.3e-3 (45 runs) | Lagrangian dust, Sc = 1, rho_p 1 g cm^-3; 1000 orbits |
| 2019AJ....158...15P | Dusty FARGO-ADSG | 900x1200, 35-105 au | alpha 1e-5, h/r 0.033 at 69 au, 8 K at 70 au | 200,000 particles 10 um-3 mm |
| 2018ApJ...857...87L | LA-COMPASS | 1024x768, 10-500 au | h = 0.05 (r/r0)^0.25, radially varying alpha (1e-5 inner, 7.5e-3 outer) | 0.15 mm; 1000 orbits; >100 runs |
| 2019ApJ...871..107F | FARGO-3D (2D) | 1766 log x 4096, 19-285 au | inviscid, h/r 0.1 (R/100 au)^0.225 | 0.2 and 0.3 MJup at 95 au; 1000 orbits |
| 2018ApJ...866L...6C | FARGO3D (2D, dust) | 350x512, 5.6-378 au | alpha 0.014, disk 20 MJ within 200 au | fragmentation 10 m/s, dust-to-gas 0.01, a^-3 |
| 2019ApJ...879L...2M | PEnGUIn | 960x1944, 5-100 au, 20 cells per H at 22 au | alpha0 0.001, Sigma0 3.86 g cm^-2 | migrating, accreting planet from 10 Earth masses; 4.6 Myr |
| 2026ApJ..1003..215F | FARGO3D (2D, 5 dust fluids) | 504x1170 | alpha 1e-4, h/r 0.05-0.07 | Stokes 0.002-0.2, dust-to-gas 0.01; 0.5-2 M_iso; 1500 orbits |
| 2017ApJ...846...70P | - | 512x950, 0.2-6 r_p | h0 0.14, flaring 0.25, disk 2 MJup | brown dwarf disks |
| 2019A&A...625A.118K | FARGO3D (3D) | - | alpha 1e-3, gas 0.003 Msun, vertically isothermal | 2, 5, 10 MJup; 1000 orbits; RADMC3D, 12CO 1e-4, 30 m/s, simobserve |
| 2023PASJ...75.1105K | Athena++ (3D spherical) | 192x80x640, r 0.4-3.0 R0 | alpha 1e-3, H0 0.07 and 0.1 | inclined planet, no migration |
| 2021A&A...654A..35B | PLUTO (3D gas), FARGO3D (2D gas+dust) | - | - | RADMC-3D, optool, CASA simobserve/tclean |

## Other systems

| Bibcode | System | Code and setup |
|---|---|---|
| 2014ApJ...796....1T | L1551 NE protobinary | SFUMATO AMR, box 1740 AU, finest cell 0.85 AU, sink 3.4 AU, n_inj 1.5e5 cm^-3, T 13.5 K, ~20 binary orbits |
| 2020ApJ...898...10T | L1551 IRS 5 | SFUMATO isothermal (100 K), LTE RT with X(C18O) 5.1e-7, simobserve, snapshot at 58.7 periods |
| 2024A&A...691A..57M | R Aql AGB triple | PHANTOM + REBOUND; M1 1.6, M2 0.4 Msun, ai 5 au, ao 35 au, Mdot 1.1e-6 Msun/yr, gamma 1.2, mu 2.38 |
| 2012Natur.490..232M | R Scl | GADGET-2 binary wind, LIME, CASA simdata, inclination 90 deg |
| 2020A&A...633A..13D | pi1 Gru | ESI-GADGET e = 0 and 0.8, LIME |
| 2020MNRAS.494.2131F | NGC 1300 bar | ENZO AMR, pattern speed 20 km/s/kpc, cooling and heating |
| 2025ApJ...984L..21B | VSI/MRI/GI disks | RADMC-3D via fargo2radmc3d, 12CO/H2 1e-4, freeze-out below 21 K and photodissociation below 1e21 cm^-2 (factor 1e-5), i 5-60 deg, 26 m/s, 140 pc |
| 2024A&A...682A..56Z | IRAS 16293 B SPH disk | RADMC-3D full Stokes, Synthesizer, carbon sublimation 300 K, ~1e10 photons |

## Scaling-relation papers

No new simulation, except 2016PASJ...68...43K, which first runs its own FARGO grid (above) and then applies
the resulting formula to HL Tau.

| Bibcode | Relation and inputs |
|---|---|
| 2016PASJ...68...43K | gap width formula calibrated on its own FARGO runs; applied with tau_unp = 9.5 (R/1 AU)^-0.4; alpha 1e-3, beta 1.5, M* 1 Msun |
| 2017ApJ...851L..23C | gap width = 4-8 R_Hill, M* 1.0 Msun, gaps fully evacuated |
| 2025ApJ...986L..11S | Hill radius with k = 4-8, alpha < 0.01, one planet per gap |
| 2018ApJ...869...17L | gap radius = 4 R_Hill; Rosotti diagnostic with alpha 1e-4 or 1e-2, rescaled by stellar mass |
| 2016A&A...586A..99H | gap width = 5 Hill radii |
| 2019ApJ...880...69Y | Kanagawa depth formula, depth 4-8, M* 2.1 Msun, T 60 K, alpha 1e-3 |
| 2024ApJ...976..132H | Zhang et al. 2018 relations, kappa_abs 0.43 cm^2/g, amax 0.1 mm, alpha 1e-3 |
| 2015ApJ...798..124R | chaotic / crossing zone width for a debris-disk gap |
| 2018A&A...619A.161C | gap width ~20 au at ~68 au, alpha 1e-3 |
