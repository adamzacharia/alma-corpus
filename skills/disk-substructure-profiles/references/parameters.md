# Parameter details for disk substructure profiles

Values are copied from the evidence pack (`packs/disk-substructure-profiles.md`: key-parameter, assumption and
excerpt sections), except where a line says "card" (read from that paper's card to settle a detail). Only
on-topic disk papers are used; the excluded papers are listed at the end.

## Samplers and fit settings (parametric profile, ring, belt and ellipse fits)

| Paper | Model | Sampler settings | Priors / notes |
|---|---|---|---|
| 2018ApJ...869...17L | central Gaussian or tapered power law + Gaussian rings (uv) | emcee, 100 walkers, 5000 steps, burn-in about 2000, second run of 5000, posterior from last 1000 | uniform +-20 deg i and PA, +-0.5 arcsec offsets; grid 0.0001-4 arcsec step 0.001 |
| 2020ApJ...898...36L | Gaussian or tapered power law + Gaussian rings (uv) | emcee, 100 walkers, 5000 steps, last 1000 used | logF [6,11] Jy/sr, sigma [0,0.2 arcsec], ring centres +-0.05 arcsec; marginal peaks, 68% intervals |
| 2020ApJ...891...48H | delta + Gaussian rings, 21 parameters (uv, vis_sample) | emcee, 96 walkers, 20,000 steps, 10,000 burn-in | weights scaled down by 2.667; Gaussian priors on PA, i, offsets |
| 2024A&A...689A.104D | central Gaussian + 2 Gaussian rings, 10 parameters (uv, galario) | emcee, 80 walkers, 10,000 steps after 2000 burn-in | log I in [-7,2], R2 in [1.16,1.66] arcsec, offsets [-2,2] arcsec; i=5.8 deg, PA=151.6 deg fixed |
| 2018ApJ...869L..42H | 5-parameter ellipse to ring/gap extrema | emcee, 30 walkers, 20,000 steps, 500 burn-in | uniform dx, dy, r0 (-4.5, 4.5 arcsec), ln sigma^2 (-15, -5) |
| 2018ApJ...869L..44K | 6 free parameters | emcee, 250 walkers, burn-in 1000 and 500 steps, 1500 sampling steps | unsharp mask 66 mas FWHM, weight 0.95 |
| 2018ApJ...869L..46D | Gaussian ring, domain chosen by eye | 100 walkers, 500 steps, last 250 used | profile errors multiplied by sqrt(70) (not a visibility-weight correction) |
| 2018A&A...616A..88V | Gaussian x cosine, up to n=4, 13 parameters (uv binned 10 klambda) | pymc MCMC | i, PA, centre initialised from imfit; rho ranges at least 100 klambda wide |
| 2018A&A...610A..24F | multi-gap model (uv binned 30 klambda) | 80 chains, 45,000 steps after 5000 burn-in | axisymmetric, flat priors; i=35, PA=86 fixed |
| 2018A&A...619A.161C | 9 parameters + centre + i, PA fixed 62 deg | 120 walkers, 24,000 likelihoods | gap width about 20 au at about 68 au |
| 2018ApJ...865...37M | Gaussian rings per ring a_i, sigma_i, x_i | not stated in pack | free i, PA, dRA, dDEC |
| 2018ApJ...869L..48G | 23 ring + 4 geometry parameters | not stated in pack | uv points 10-10,000 klambda in 10 klambda steps; rings chosen by visual inspection |
| 2019ApJ...878...16P | Gaussian ring + inner disk | 200 walkers, 2000 steps | r_peak 10-80 au, sigma 1-50 au, A 0-1, sigma_inner 0.1-10 au, F_total 0-3 Jy |
| 2017ApJ...839...99P | surface brightness model | 1000 walkers, 4000 steps, burn-in about 1000 | radial grid 1-500 au in 0.1 au steps |
| 2018ApJ...859...32P | transition disk morphology | last 700 steps used | radial grid 0-500 au in 0.5 au steps |
| 2024ApJ...966...59S | Nuker + point source | 50 walkers, 10,000 steps; model pixel 3 mas | log10 alpha U(0,2), beta U(0,10), gamma about U(-3,2); point flux U(0,1) mJy; inclination prior proportional to sin i |
| 2020ApJ...895..126H | disk size fits | 70 walkers, 100,000 steps | uniform priors |
| 2020ApJ...902..141S | analytic rings/asymmetries (uv, galario) | dynesty nested sampling, uniform priors | weights x about 0.25; Bayes factors between models |
| 2024ApJ...976..132H | central Gaussian + N Gaussian rings (uv) | pyro SVI, Adam, learning rate 0.02, 15,000 iterations, 2000 posterior samples; posterior approximated as multivariate normal | Gaussian priors on log A, log sigma, r_i, i, z0, phi, PA, offsets; weight rescaling factor f typically about 2 (direction not defined in the pack) |
| 2025MNRAS.543.2723P | 7 parameters (f0, sigma_r, R_peak, inc, PA, dRA, dDec) | 8 walkers per parameter, 30,000 steps then final 10,000 | structured if R_peak > 0.05 arcsec |
| 2025ApJ...993...85Y | outer ring + arc | 100 walkers, 500 steps, 250 burn-in | PA sampling 10 deg, 3 sigma threshold |
| 2019ApJ...881...84S | debris belt | 1024 walkers, 12,500 steps, 2500 burn-in | |
| 2025ApJ...984L..19Y | 8 free parameters | 24 walkers, 5000 steps, median of last 4200 | |
| 2017MNRAS.466.4201W | debris ring + point source (image plane) | Metropolis-Hastings, 3 chains, 100,000 links thinned by 10 | flat priors; sigma = 374 uJy |

## frank (non-parametric) settings

| Paper | alpha | w_smooth | N | Rmax | Other |
|---|---|---|---|---|---|
| 2024A&A...689A.104D | 1.05, 1.2, 1.3 tested; 1.3 preferred | 1e-1, 1e-4 tested; 1e-4 preferred | 300 | 5.0 arcsec | p0 = 1e-35; logNormal fit preferred; 20 mJy point source subtracted first |
| 2024ApJ...971..129C | 1.3 | 0.1 | 300 | 2.1 arcsec | p0 = 1e-15 Jy^2 |
| 2025ApJ...986L..11S | 1.20 | 1e-3 | 400 | 4 R_out | |
| 2024ApJ...974..102S | 1.05 | 1e-4 | | | |
| 2026ApJ..1001..124M | 1.3 | 0.01 | 400 | 3 arcsec | |

## Profile extraction (image plane)

| Paper | Bin width / sampling | Geometry | Error per bin |
|---|---|---|---|
| 2020ApJ...891...48H | 1 au annuli | PA 57.17 deg, i 53.21 deg | |
| 2018ApJ...869L..42H | 1 au annuli (card) | from ellipse fits or imfit | |
| 2018MNRAS.475.5296D | a quarter of the linear resolution | | |
| 2024ApJ...965..147B | 1/4 beam FWHM (about 80 mas), weights proportional to r^2 | centre offset (-52, -155) mas | |
| 2019ApJ...880...69Y | 0.05 arcsec bin width; innermost bin radius = beam 0.1 arcsec (14 au) | | |
| 2018ApJ...864..133T | 4 au annuli | | |
| 2018A&A...615L..10M | 0.12 arcsec (13CO, 1.3 mm), 0.15 arcsec (12CO) | PA -9 deg, i 55 deg | |
| 2017ApJ...838...97M | rings of beam width | i 13 deg, PA 5 deg | |
| 2024A&A...689A.104D | annuli, equivalent radius = mean of points in the bin | | rms/(2 sqrt(n)); n is not defined in the pack or the card, so do not reuse without the paper's definition |
| 2019ApJ...883...71C | annuli | i 46.72 deg, PA 138.02 deg | rms/(Omega_ring/Omega_beam)^0.5 |
| 2018ApJ...869L..43H | spiral peaks every 6-18 deg in azimuth, depending on radius | per-disk PA and i | |
| 2025A&A...697A..64V | 30 deg wedge on the major axis; six 30 deg wedges for azimuthal cuts | inclinations from literature | good models: chi2 <= 8 and Hausdorff metric <= 1.2 |
| 2024ApJ...963..134Y | wedge 0.25-0.6 arcsec radial, 60-150 deg azimuthal in the disk frame | i 50 deg, PA 100 deg | |
| 2019AJ....157..237R | 20 deg wedge opening angle | | |
| 2013ApJ...777L..25M | ring maxima along cuts every 10 deg, ellipse fit; aperture 2.8 arcsec | intrinsically circular ring | azimuthal scatter vs emission-free ellipses |

## Thermal, opacity and interpretation assumptions

| Quantity | Values seen | Papers |
|---|---|---|
| Dust opacity at about 1.3 mm (mass) | 2 cm2/g; 2.3 cm2/g; 2.254 cm2/g; 0.43 cm2/g absorption (DSHARP, amax 0.1 mm) | 2024ApJ...961..228S, 2020A&A...644A.119P, 2024A&A...689A..85G, 2024ApJ...976..132H |
| Dust temperature (mass) | 20 K; 60 K disk-wide with 80 K (inner ring) and 40 K (outer ring); about 10 K for a debris belt | 2024ApJ...961..228S, 2025ApJ...993...90S, 2014ApJ...791L...6W, 2017ApJ...850L...6A |
| Passive disk temperature | flaring angle 0.02, mu 2.33, L* scaled; flaring angle 0.05 | 2024ApJ...971..129C, 2018ApJ...869...17L |
| Continuum optical depth | tau_d = -ln(1 - I/(B(T_d) - B(T_bg))), T_bg 2.73 K, T_d from a disk temperature model | 2019ApJ...880...69Y |
| Spectral index | alpha = log(I1/I0)/log(nu1/nu0); the 2016Natur.535..258C pack line inverts the frequency ratio | 2020ApJ...891...48H |
| Flux calibration | 10% absolute per band; DSHARP relative flux scales agree within 5% (relative only) | 2020ApJ...891...48H, 2018A&A...616A..88V, 2024A&A...689A.104D; 2018ApJ...869L..41A |
| Gas-to-dust ratio | 100 | 2024ApJ...961..228S, 2018A&A...616A..88V, 2020ApJ...898...36L |
| Turbulence alpha | 1e-3 (planet masses, dust evolution); 1e-4 or 1e-2 bracket | 2024ApJ...976..132H, 2020ApJ...898...36L, 2018ApJ...869...17L |
| Pressure scale height uncertainty | about 25% | 2024ApJ...976..132H |
| Trapping width limits | w_max 17.1 au (ring to gap), w_min = h_p 5.15 au | 2024ApJ...971..129C |
| Gas width bounds for alpha/St | w_g,min = H_g (from temperature); w_g,max = ring peak to deepest point of the gap inside the ring; w_d = Gaussian width of the model dust surface-density ring | 2025A&A...697A..64V |
| Snowline temperatures | N2 12-15 K, CO 23-28 K, clathrate 41-46 K; N2 13.5, CO 25.5, CH4 29, CO2 66, NH3 80 K | 2018ApJ...869...17L, 2019ApJ...872..112V |
| Planet from gap | "gap radius corresponds to 4 R_Hill" (gap size observable not defined in the pack); normalized gap-ring distance 0.2-0.3 (Rosotti diagnostic); gap width 5 Hill radii; Kanagawa gas-gap depth 4-8 (unperturbed / gap HCO+ column, constant abundance 17-37 au, vertically isothermal) with M* 2.1 Msun, T 60 K, alpha 1e-3 | 2018ApJ...869...17L, 2016A&A...586A..99H, 2019ApJ...880...69Y |
| Planet-gap simulations | planet at 33 au, q = 0.002, alpha 1e-3, vfrag 10 m/s; Mp 0.4-3 MJ range | 2020ApJ...898...36L, 2019A&A...622A..75L |

## Debris belts (when the disk is a debris disk)

| Paper | Model | Key settings |
|---|---|---|
| 2015ApJ...798..124R | single power law, power law with gap, double power law (uv) | model image 2048x2048 of 0.015 arcsec; flux scaled as nu^(2+beta), beta 0.4; primary beam 24.3 arcsec applied |
| 2019AJ....158..162F | constant surface density ring + Gaussian sources, 23 parameters | blackbody grains, opacity 2.3 cm2/g; eccentricity from projected offset |
| 2017ApJ...842....8M | eccentric belt: R_belt, width, flux, e_f, e_p, omega_f, offsets | natural weighting, rms 14 uJy/beam; negligible vertical thickness |
| 2016MNRAS.460L..10B | power-law belt, 6 free parameters | 120 walkers, 2500 steps; sigma scaled by sqrt(beam area in pixels) |
| 2020MNRAS.497.2811K | Gaussian ring with RADMC-3D, dirty-image fit | 100 walkers, 1000 steps after burn-in; kappa about 1.3 cm2/g |
| 2025A&A...693A.151M | Gaussian radial profile | h fixed to 0.03 unless vertically constrained; T proportional to r^-0.5 |
| 2026ApJ..1004..182H | rave non-parametric + frank | gap injection to find the widest hidden gap |
| 2013ApJ...777L..25M | DEBRA optically thin model on 7 klambda deprojected bins | grid over Rin, Rout, p, smin; smax 3000 um |

## Excluded as off-topic (52 papers)

Tagged by the regex but not disk substructure work; left out of every count in the skill:
2013ApJ...774L...7M, 2014ApJ...787...48X, 2014ApJ...796..131O, 2014MNRAS.444.1821F, 2016ApJ...823...26E,
2016ApJ...826...26T, 2016MNRAS.460..627K, 2016MNRAS.461.4276D, 2016Natur.540..406B, 2017A&A...607L...6T,
2017ApJ...835..278S, 2017ApJ...840...72L, 2017ApJ...843...83W, 2017MNRAS.464L..31H, 2017MNRAS.469.3347M,
2018A&A...615A.141B, 2018A&A...617A.120M, 2018A&A...618A.120L, 2018ApJ...858...90G, 2018ApJ...860..119G,
2018ApJ...869..126L, 2018ApJ...869..158F, 2019ApJ...871..185L, 2019ApJ...872..200H, 2019ApJ...874...89C,
2019ApJ...875...24C, 2019ApJ...875...62Y, 2019ApJ...882...31A, 2019ApJ...885...82L, 2019ApJ...886...14F,
2019ApJ...886L...4Z, 2019NatAs...3..517Z, 2020A&A...633A.126B, 2020A&A...644A..11L, 2020ApJ...894...76W,
2020ApJ...894L..14L, 2020ApJ...896..127K, 2020ApJ...899...10T, 2020MNRAS.497.3504T, 2021A&A...648A..41V,
2021A&A...656A.133Q, 2021ApJ...907L..15S, 2023ApJ...956L..16T, 2023PASJ...75..225M, 2024A&A...690A.375S,
2024A&A...690A.376S, 2024ApJ...967...15K, 2024MNRAS.534..683Z, 2025A&A...700A.188C, 2025ApJ...992L..15L,
2025SciA...11.4512O, 2026ApJ..1001L...1T.
