# uv-plane fitting: longer parameter tables

All values from the `uv-plane-fitting` evidence pack ("Key parameters and settings" and excerpts). Counts are
my own count of pack lines.

## MCMC chain settings stated in the pack

| Paper | Walkers | Steps | Burn-in / kept | Notes |
|---|---|---|---|---|
| 2016A&A...591A.108O | 200 | 2000 | 500 burn-in | alpha_in fixed 5 |
| 2017ApJ...839...99P | 1000 | 4000 | ~1000 burn-in | radial grid 1-500 au, 0.1 au steps |
| 2017ApJ...843..150F | 80 | 1000 | first 500 | |
| 2017MNRAS.465.2595M | 50-180 | 300-1000 | | 3 min / 2 GHz averaging |
| 2018A&A...610A..24F | 80 | 45000 | after 5000 | |
| 2018ApJ...859..111H | 500 | 1000 | | uniform priors on Md, gamma, Rc, H100 |
| 2018ApJ...866L...6C | 120 | 50e3 | after 30e3 | |
| 2018ApJ...868L...5K | 100 | 500 + 500 | 500 burn-in | 11 free parameters, flat priors |
| 2018ApJ...869...17L | 100 | 5000 (+5000) | last 1000 | uniform +-20 deg i/PA, +-0.5'' offsets |
| 2018ApJ...869...75M | 100 | 10000 | | |
| 2018MNRAS.474.4347C | ~100 | 1000 | | uniform priors with listed bounds |
| 2018MNRAS.475.4924K | 40 | 1000 | ~100 | statwt, reweighting 1/2.5 |
| 2019A&A...626L...2F | 90 | 18000 | after 2000 | uniform priors |
| 2019A&A...628A..95M | 150-400 | 20000-31000 | | 1 or 2 disks |
| 2019ApJ...873...50D | 1000 chains | 1000 extra | 1000 burn-in | |
| 2019ApJ...875...87D | 50 | 1e5 samples in total (not steps per walker) | | 0.15 au per pixel |
| 2019ApJ...877L..32M | 100 | 10000 | | |
| 2019ApJ...878...16P | 200 | 2000 | | uniform priors with bounds |
| 2019ApJ...881...84S | 1024 | 1.25e4 | 2.5e3 | |
| 2019ApJ...882...49L | 100 | 5000 | <1000; last 1000 | |
| 2019NatAs...3..278K | 64 | 1000 | after 1000 | 2048 px of 4.6 mas |
| 2020A&A...633A.114S | 200 | 20000 | | |
| 2020ApJ...889...59P | 240 | 2000 | | |
| 2020ApJ...891...48H | 96 | 20000 | 10000 | weights /2.667 |
| 2020ApJ...895..126H | 70 | 100000 | 100 x 1000 | uniform priors |
| 2020ApJ...895L..18B | 144 chains | 15000 | 10000 incl. | |
| 2020ApJ...898...36L | 100 | 5000 | last 1000 | |
| 2020ApJ...898..146M | 40 (star fits); 10 x N_free (belt fits) | 2000 | | free weight scaling |
| 2024A&A...689A.104D | 80 | 10000 | after 2000 | |
| 2024ApJ...966...59S | 50 | 10000 | | Nuker priors; sin i |
| 2025A&A...693A.151M | 10 x N_free | >= 1000 | | weight rescaling free |
| 2025A&A...700A.188C | 120 | 25000 | | uniform priors |
| 2025ApJ...986L..11S | 192 (8 x N_free); 100 | ~1e4 + 1e4; 10000 | | flat priors |
| 2025ApJ...993...90S | 32 | 1000 | | initialised from SpM cos i and PA |
| 2025MNRAS.543.2723P | 8 per parameter | 30000 | final 10000 | 7 free parameters |
| 2018ApJ...865...37M | not stated | 30000 iterations | last 5000 used | chains started around a Levenberg-Marquardt fit |

Other chain types: 10,000-240,000 iterations with 5,000 burn-in (2017A&A...597A..41G); 10 chains of 100,000
links, acceptance ~26% (2017MNRAS.466.4201W); ~10^6 MCMC trials (2013ApJ...762L..21M). These lengths are
historical examples; let convergence diagnostics set your run length.

Non-MCMC samplers and optimisers: dynesty nested sampling (2020ApJ...902..141S); Adam optimiser, learning
rate 0.02, 15,000 iterations, 2000 posterior samples (2024ApJ...976..132H); Levenberg-Marquardt or SIMPLEX
(2014A&A...563A.136M); lmfit least squares (2025ApJ...986L..22R); `uvmodelfit` up to 20 iterations
(2020ApJ...899...55A).

## Geometry handling

| Choice | Examples |
|---|---|
| i and PA fixed from continuum or an earlier fit | 2019ApJ...882..160Q, 2018ApJ...868L...5K, 2018ApJ...865...37M (from step 3), 2024NatAs...8..587F |
| i and PA free with offsets | 2018ApJ...865...37M, 2016MNRAS.460.2933M, 2025MNRAS.543.2723P |
| Inclination from Gaussian axis ratio, i = arccos(minor/major) | 2024ApJ...963..164R, 2019ApJ...871..100H, 2016ApJ...828...46A |
| Centre fixed from imfit | 2020ApJ...900....1F |
| Positions fixed, only fluxes free (linear fit) | 2016A&A...593A..61M, 2019ApJ...873L..19B, 2014A&A...563A.136M (step 2) |
| Relative positions bounded by VLBI astrometry (10 mas) | 2014A&A...563A.136M |
| Point-source model if size/uncertainty < 5 | 2016ApJ...828...46A |

## Fixed physical inputs in image-based models

| Paper | Fixed values |
|---|---|
| 2017MNRAS.465.2595M | kappa_abs = 3.8 cm2/g at 0.88 mm; T(r) = 42 (r/150 AU)^-0.5 K |
| 2016MNRAS.460.2933M | kappa_abs = 1.1 cm2/g at 1.3 mm; h lower limit 0.03 |
| 2020ApJ...898..146M | h = 0.03; T proportional to r^-0.5; optically thin |
| 2025A&A...693A.151M | h = 0.03 unless constrained; blackbody grains |
| 2015ApJ...798..124R | flux scaled as nu^(2+beta), beta = 0.4; optically thin, axisymmetric |
| 2020ApJ...891...48H | p = 3.5, a_max = 1 mm; 512 x 1024 x 64 RADMC-3D cells, 10^8 photons |
| 2017ApJ...846L..26W | X_CO = 1e-4, mu = 2.37, r_in = 0.1 au, distance 140 pc with 20 pc added in quadrature |
| 2018ApJ...856..117F | free: T_atm0, T_mid0, q_atm, R_c, i, dv_turb; fixed: M*, distance, CO abundance, PA, v_sys, offset |
| 2020ApJ...895..109F | T_mid0 fixed from the literature, with PA, gamma = 1, Z_q0 and masses; T_atm0, q, R_c, i, dv_turb, R_in, v_sys free |
| 2017A&A...605A..21C | i = 44 deg, PA = 133 deg, d = 122 pc; Tc grid 12-36 K in 2 K steps |
