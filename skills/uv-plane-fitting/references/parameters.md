# uv-plane fitting: longer parameter tables

All values from the `uv-plane-fitting` evidence pack ("Key parameters and settings" and excerpts). Counts are
my own count of pack lines. The pack was rebuilt from 638 papers (2026-10-30 refresh); rows added then are
marked (new). Some older rows come from the earlier 278-paper pack and are still in that paper's card even
where the rebuilt pack shows fewer lines per paper.

## MCMC chain settings stated in the pack

Steps are per walker unless the row says "total" or the paper did not say. Burn-in is separate from the
sampling steps only where the row says "+"; otherwise the paper's wording is kept.

| Paper | Walkers | Steps (per walker unless noted) | Burn-in / kept | Notes |
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
| 2019ApJ...874..136S (new) | 200 | ~5000 after burn-in | | autocorrelation time ~1000 steps; walkers with chi2 - chi2_min > 44 dropped |
| 2020MNRAS.492..572A (new) | 120 | 5000 | | acceptance fraction 0.2-0.5 |
| 2021ApJ...909..212K (new) | 100 | 1000 | 1000 burn-in | 16-parameter profile fit to binned real visibilities, < 2000 klambda |
| 2021MNRAS.506.1978L (new) | 120-180 (10 x N_free) | 600-1600 | 250-1000 | three belt models, 12-18 parameters |
| 2021A&A...649A.122P (new) | not stated | > 250000 after convergence (per walker or total not stated) | | galario pixel 0.2 mas; 16th/84th percentiles |
| 2024A&A...688A.149D (new) | 136 (8 x N_free) | 5000 burn-in + 6000 sampling | 5000 burn-in discarded; 6000 x 136 = 816,000 samples kept | 2048 px of 4 mas |
| 2025A&A...701A.203S (new) | 32, then 64 | 1e4, then 1e5 | 30% | two-stage run |
| 2025A&A...699A.373F (new) | 100, then 250 | ~1e3, then 1e4 | 25% | preliminary then fiducial run; same scheme in 2026A&A...709A.174F (120 walkers, 2e4) |
| 2025ApJ...988..106H (new) | 24 | 15000 | 1000 | flat priors, cos i in [0,1] |
| 2026A&A...705A.197Z (new) | 64 (more than 2 x N_free) | ~1500 | visual convergence | >= 1e5 samples after convergence; walkers 5 sigma below max log-likelihood dropped |
| 2026MNRAS.552g1700S (new) | 104 (8 x 13) | 8000 | | geometry fixed from Band 6; 1024 px of 10 mas |

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
| Recentre on a uvmodelfit Gaussian with fixvis, then test the centre by shifting it +-2 mas and minimising the imaginary-image RMS (new) | 2021ApJ...909..212K |
| Phase centre from the high-resolution image peak with fixvis (new) | 2020MNRAS.492.3194S |
| One intensity model for five epochs, separate centre and free flux scale per epoch, one epoch fixed to 1 (new) | 2024A&A...692A.155K |
| Strict position priors so each source in a multiple is fitted separately (new) | 2024A&A...687A.308S |
| Radius, inclination and PA priors normal with sd 3% of Herschel values (new) | 2025MNRAS.541...71M |
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

## Further parameter rows (moved from SKILL.md)

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Time averaging | <= 3 min with small uv shift, or 10-30 s | 10 s to 10 min | 8 | 2017MNRAS.465.2595M, 2018Sci...361.1016S, 2019ApJ...873...50D, 2024A&A...692A.155K (24 s), 2021A&A...645A..33B (30 s) |
| uv binning for profiles | 10-50 klambda bins | 5-150 klambda | about 12 | 2014ApJ...791L...6W (10), 2019ApJ...876..112R (5-50 tested), 2020MNRAS.492.3194S (50), 2016ApJ...828L..21K (150); bin errors as azimuthal std / sqrt(N) (2021ApJ...909..212K) |
| Model image | >= 1024 px, pixel well below beam | 256-4096 px; 0.2 mas to 0.02'' | about 10 | 2015ApJ...798..124R (2048 x 0.015''), 2024MNRAS.532.1752R (2048-4096 px), 2025MNRAS.543.2723P (256 x 0.02''); 4 mas checked against 2 mas (2024A&A...692A.155K) |
| frank hyperparameters | alpha 1.05-1.3, w_smooth 1e-4 to 1e-1 | alpha 1.05-1.4; N 300-400; Rmax 2'', 5'' or 4 R_out | 7 (my count of pack lines giving frank settings) | 2025ApJ...986L..11S, 2024A&A...689A.104D, 2024ApJ...974..306S, 2024A&A...682A..55M, 2025ApJ...990L..70L (alpha 1.4) |
| frank geometry uncertainty | perturb i, PA, offsets over repeated fits | 500 runs; 1 deg on i and PA, 1/3 beam major axis on offsets | 1 | 2025ApJ...986L..11S |
| Minimum resolvable size | theta_min = 0.88 theta_beam / sqrt(S/N) | | 1 | 2020A&A...643A..53F |
| Astrometric systematic | added in quadrature to MCMC position errors | 5% of the beam | 1 | 2025Natur.642..905L |

Time-averaging examples: 3 min and 2 GHz bins (2017MNRAS.465.2595M); up to 3 min with uv separation < 10 m
(2018Sci...361.1016S); up to 10 min with uv separation < 15 m (2019ApJ...873...50D); 10 s and four channels per
SPW (2018MNRAS.475.4924K, 2024A&A...686A.206Y); 24 s and one channel per SPW (2024A&A...692A.155K); 30 s
(2021A&A...645A..33B).

## Flux-scale uncertainties stated in the pack (ALMA papers)

My count of pack parameter/assumption lines that name a paper and give a flux-scale percentage, VLBI-only papers
(2020A&A...636A..62K, 2026A&A...710A..63L) excluded: 11 papers.

| Paper | Flux-scale uncertainty |
|---|---|
| 2016A&A...596A..75S | 10%, added in quadrature |
| 2021A&A...653A.117B | 10% |
| 2025A&A...703A..15M | 10%, added in quadrature |
| 2020ApJ...894...76W | ~10% |
| 2016ApJ...829....6W | 10% (dominates the flux error) |
| 2022ApJ...930L...3W | 10% |
| 2022ApJ...926..159I | <= 10% |
| 2023A&A...676A...4C | 10% Band 7; 5% Bands 3, 4, 6 |
| 2023PSJ.....4..142C | 5% |
| 2025PSJ.....6..183C | 5%, included in the Tb uncertainty |
| 2021PSJ.....2....3M | ~5% ALMA (3-7% for the VLA data) |

## Belt vertical aspect ratio conventions

h = H/R, but H differs: 2026A&A...705A.196H fixes h_HWHM = 0.015 by default; 2026A&A...705A.197Z uses a vertical
Gaussian with H_sigma proportional to radius; 2021MNRAS.502.5390P and 2024ApJ...962..166W use Gaussian vertical
profiles with constant h. For a Gaussian, HWHM = sqrt(2 ln 2) sigma = 1.177 sigma (general practice), so convert
before comparing h values across papers.

## Validation examples (moved from SKILL.md)

- **Injection and Monte Carlo tests**: 26,600 artificial sources to correct flux/size bias in S/N bins
  (2017ApJ...850...83F, card); mock sources giving Delta FWHM = +-0.2'' at S/N 5, +-0.1'' at 10, +-0.05'' at 15
  (2020ApJ...901...74T); injected elliptical Gaussians and disks (2015ApJ...808...36M); mock SZ shocks
  (2016ApJ...829L..23B); simobserve Gaussians fitted with `uvmodelfit` recovered sizes within 20% only for
  0.1-0.4'' resolution, which set the archival sample (2020ApJ...888...44C); simulated visibilities from a
  template recovered the input spectral index (2026A&A...707A.255C).
- **Stacked residuals and numerics**: stack visibilities and test the shortest uv bin of the residuals for a
  faint extended component (1.2 sigma at 20 klambda, not a detection, 2025A&A...693A.237I); halve the model
  pixel and check the result holds (2024A&A...692A.155K).
- **Sub-band consistency**: flare candidates kept only if lower and upper sideband fluxes agreed within 20%
  (2022ApJ...939L...6B); separate fits to the upper and lower halves of Band 6 gave similar residual patterns
  (2021ApJ...909..212K).
- **Independent data or methods**: ACA data left out of the fit still matched (2020ApJ...902..141S);
  image-plane imfit or Gaussian fit cross-checks (2024A&A...685A..80Z compared five flux methods;
  `uvmodelfit` sizes ~2% below imfit and GALFIT ~10% above in 2020ApJ...888...44C);
  agreement with earlier measurements (2018ApJ...855L...2M, 2023PSJ.....4..142C, 2017ApJ...850...83F).
