# Checks catalogue (claim-verification)

Long form of the checks in `SKILL.md`, grouped by the kind of claim they protect. Every row is a practice seen
in the evidence pack; bibcodes are examples, not a complete list. "Pack count" figures are my keyword counts
over the 545 listed validation and stopping lines of the pack (lines are normalised card phrasings, so a count
is a floor on how often the idea appears, not a census of 3455 papers).

## A. Is the signal real? (detections, tentative lines, faint compact sources)

| Check | Protects against | How papers ran it | Bibcodes |
|---|---|---|---|
| Inverted (negative) image or cube search | Noise peaks counted as sources; non-Gaussian noise tails | Run the same finder on the data multiplied by -1; set the threshold where negatives vanish or where the positive/negative excess implies a stated purity | 2018ApJ...853..195W, 2021ApJ...907..122M (zero negatives beyond -6.2 sigma in 184 inverted cubes), 2023ApJ...953...75H (S/N 5.2, purity 83%), 2025A&A...699A.324H (peak S/N > 4.2), 2020MNRAS.495.3124H (positive peaks above the most significant negative peak) |
| Spurious-fraction curve | A threshold chosen by habit rather than by the data | Differential spurious fraction vs S/N; pick the S/N where it reaches 50% and quote the cumulative spurious fraction | 2019ApJS..244...40L (5.40 blind, 4.35 with prior positions, cumulative spurious 8-12%) |
| Expected-false-detection target | Many independent beams or channels producing chance peaks | Choose S/N so the expected number of false detections over the whole survey is below 1 | 2021ApJ...908..192S (S/N 4), 2026A&A...706A.236M (lowest negative peak and <1 expected false detection), 2026ApJ...999...47L (pixel S/N normal to 5 sigma; 100 mock noise maps give 0.7 false detections) |
| Look-elsewhere trial count | Quoting a local significance after scanning many channels or line widths | Count independent trials in the spectral scan and convert to a global spurious probability | 2021NatAs...5..319P (47 trials, 1.7e-4 for an integrated S/N 6.2 broad component) |
| Mock or bootstrap sources | Finder thresholds whose purity is unknown | Inject thousands of mock sources or bootstrap visibilities; classify a source only at a stated confidence | 2022MNRAS.515.3126I (PyBDSF pSNR 3.3, iSNR 2.0 for 95% purity; 20,000 mocks), 2021MNRAS.508.5259M (2000 visibility bootstraps; >4.2 sigma reliable) |
| Repeat per execution block or epoch | Single-EB artefacts, calibration glitches | Require the source in every EB, or in independent epochs or instruments | 2020MNRAS.498.4635D (all EBs plus negative-image checks), 2025MNRAS.543..862V (both ALMA images plus a NOEMA detection near 4 sigma), 2013ApJ...762L..21M (central peak persists in four observations) |
| Consecutive channels | Single-channel spikes | Require several adjacent significant channels | 2013AJ....146...91I (feature spans several consecutive spectral elements), 2024AJ....168..151J (five consecutive channels), 2025A&A...699L..11V (>=5 rms channels with adjacent spaxels) |
| Side-lobe screening | Sidelobes of a bright source read as companions | Drop candidates in the sidelobe pattern of a bright source; check residuals for dirty-beam patterns | 2014ApJ...795....5O, 2021A&A...654A..37D |
| Known-position threshold | Using a blind threshold where a prior position exists, or the reverse | Lower threshold only when the position is fixed in advance | 2024PSJ.....5..221C (3 sigma at a known location), 2023ApJ...956..135W (3 sigma in imaging or matched filtering), 2019ApJS..244...40L (prior vs blind thresholds) |
| Multiple transitions (molecules) | Misidentified or blended single lines | Require several unblended transitions matching a model; reject models that predict lines not seen | 2025A&A...702A..35D (>=5 unblended lines >=3 sigma), 2026ApJ..1004L...6D (ten unblended, seven >3 sigma), 2024MNRAS.533.1143M (35 lines >5 sigma, no missing strong lines), 2024A&A...687A...8M (300 K model rejected by missing lines) |
| Alternative carriers and line IDs | Wrong molecule or wrong redshift | Search catalogues for other carriers; test other line IDs with companion lines | 2014A&A...569L...5M (MADEX, CDMS, JPL), 2016A&A...589L...5M, 2014ApJ...781L..39T, 2013ApJ...767...88W, 2024A&A...690L..16J (three lines for an unambiguous redshift) |
| Extraction position test | A detection that exists only at the chosen pixel | Repeat the fit at many nearby positions | 2026ApJ..1004L...6D (70 offset positions, columns within an order of magnitude) |

## B. Is the number right? (fluxes, sizes, masses, temperatures)

| Check | Protects against | How papers ran it | Bibcodes |
|---|---|---|---|
| Single-dish or compact-array flux comparison | Interferometric spatial filtering | Ratio of ALMA to single-dish or ACA flux over matched coverage | 2018ApJ...857...19F (median 0.63 vs APEX), 2024NatAs...8..308D (CO 66% resolved out, SiN fully recovered), 2025ApJ...995..108J (only after checking both cover the full line width), 2021ApJ...908L..43N (near-unity ACA ratio, 12 m alone kept) |
| Curve of growth | Aperture too small or too big | Grow the aperture or taper until flux plateaus | 2020ApJ...903...34A, 2023MNRAS.524.1775H, 2021A&A...654L...8C, 2026A&A...709A.216U, 2025ApJ...993L..40S |
| Independent estimator | Method-specific bias | Same quantity from two tools or domains | 2018MNRAS.481.1976Z (CASA uvmodelfit vs main fit; PSF model underestimates extended flux), 2014A&A...562A..67G (GILDAS cross-check of a ~3.4 sigma extension), 2017MNRAS.469.3200B (visibility refit, flux 0.6% higher), 2016ApJ...832..143F (Fourier vs beam-in-fit widths) |
| Injection-recovery of sizes and fluxes | Flux boosting, size bias at low S/N | Simulated visibilities with matched noise; quote the S/N where recovery is reliable | 2021ApJ...908..192S (10-15 sets per source), 2024A&A...690A.197M (1500 sources for 4.4-5.5 sigma sizes), 2015ApJ...808...36M (artificial disks injected into visibilities), 2024ApJS..275...36F (photometry agrees with input down to SNR 8) |
| S/N floor for resolved quantities | Sizes from barely detected sources | Set the floor from simulations | 2015ApJ...799...81S (SNR >= 10), 2021A&A...654A..90L (peak S/N 8-10), 2024MNRAS.533.3098A (mock S/N 8 because 4 is too low), 2025A&A...696A.202S (S/N > 9) |
| Noise vs expectation | Hidden artefacts or bad weighting | Compare image rms to the sensitivity calculator or theoretical noise | 2020ApJ...905...25G, 2020ApJS..247...15S |
| Assumption sweep | One adopted Tex, beta, alpha_CO or rate driving the result | Re-run with alternatives and report the change | 2021A&A...645A..21G (ULIRG alpha_CO), 2020NatAs...4..861C (collision rates x0.1-10 change Q by 2%; Tkin 20-70 K by <8%), 2017ApJ...849...25L (flux errors 5-20%, beta 1-2), 2014A&A...570A..28V (12C/13C), 2013A&A...557A.132M (alternative disk model) |
| Resolution matching | Differences that are resolution artefacts | Smooth to the comparison sample's resolution and redo | 2018ApJ...857...19F (to 40 pc, 2 km/s), 2021A&A...654A..37D (common 0.5 arcsec taper) |
| Flux-scale consistency between datasets | Calibration offsets mimicking variability | Flux ratio between datasets, calibrator monitoring | 2024AJ....167..232T (0.999 +/- 0.006), 2018A&A...617A.129K (2.2% between days; 18% drop over 11 months put on calibration), 2025A&A...703A.110S (calibrators vs AMAPOLA) |

## C. Is this model preferred, and is it unique?

| Check | Protects against | How papers ran it | Bibcodes |
|---|---|---|---|
| Information criterion with a fixed threshold | Adding components because they lower chi2 | Delta BIC > 10, AIC difference >~ 10, ln evidence ratio >= 5, DIC difference > 10 | 2025ApJ...985..243B, 2024ApJ...965..108U, 2024A&A...689L...5M, 2024ApJ...971...17F, 2021PSJ.....2..105T |
| Criteria agreement | Criterion-dependent choices | Require agreement of 2 of 3 statistics, or report when AIC and BIC differ | 2025MNRAS.538.3001T, 2026A&A...705A.197Z |
| Residual-driven component adding | Under- or over-fitting | Add a component when residuals exceed 5 sigma, stop below 3 sigma | 2022PASJ...74.1429T, 2024MNRAS.533..771R, 2021MNRAS.503.1174K (>=3.5 sigma residuals), 2021A&A...645A..21G (>3 sigma residuals) |
| Overfitting signs | Fits tuned to noise | Reduced chi2 well below 1; negative residual features | 2020MNRAS.496.4405H, 2025ApJ...995..108J |
| Prior and data-subset robustness | A component carried by priors or a subset | Refit with other priors and data subsets | 2021A&A...650A.153D, 2021A&A...652A..66P (varied priors and starting points) |
| Sampler convergence | Unconverged posteriors | N/tau > 50 or > 100, R-hat < 1.01 and ESS > 300, seed change, longer run | 2021AJ....162..235Y, 2023ApJ...950...75I, 2024ApJ...974..145S, 2023MNRAS.525.6146W |
| Correlated-noise likelihood | Uncertainties too small from correlated visibilities or pixels | Rescale the likelihood | 2021MNRAS.504.4123N (by sqrt(2N)) |
| Second sampler or method | Sampler-specific answers | Repeat with another sampler or nonparametric tool | 2024A&A...688A.130H, 2026A&A...705A.197Z (parametric vs frank and rave), 2025A&A...700L...5G (multiple starts) |
| Cross-validation for regularised imaging | Hand-tuned hyperparameters | k-fold CV on a parameter grid | 2021ApJ...923..121Y (10-fold, 5x5 grid), 2025ApJ...984L..14Z |
| Simulated recovery of the structure | Structures created by the method | Recover a known synthetic model | 2024A&A...685A.142Y, 2025A&A...699A.279D, 2026ApJ..1000L..14B |

## D. Is the interpretation the only one? (alternatives, populations)

| Check | Protects against | How papers ran it | Bibcodes |
|---|---|---|---|
| Kinematic argument | Outflow vs rotation vs infall confusion | Gradient orientation vs jet; speeds vs escape velocity | 2013A&A...552L..10S, 2015ApJ...812...27A, 2021A&A...645A..21G |
| Energetics or timescale argument | Mechanisms that cannot supply the energy | Required energy, temperature or mass vs available | 2012ApJ...760L..25E, 2013A&A...555A..73K, 2015MNRAS.447.1826Z, 2017ApJ...849...25L |
| Instrumental alternatives | Calibration or imaging artefacts read as physics | List and test instrument effects | 2016A&A...593A..44L (beam squint, gain drift, decoherence), 2015PASJ...67...72T (band-incoherent clumps as phase artefacts), 2021A&A...645A..21G (instrumental line wings) |
| Filtering vs absence | Missing flux read as missing gas | Test resolved-out explanations | 2015ApJ...803...70S, 2015ApJ...810L...7V, 2015A&A...584A..42A |
| Shared-variable or aperture test for correlations | Correlations built into the axes | Mock data with the same selection; partial correlations | 2021ApJ...908..192S, 2025ApJ...995..108J, 2018ApJ...857...19F (1e4 random clouds) |
| Normalisation test | Trends driven by a third variable | Normalise and see if the trend survives | 2018ApJ...853..195W (radius trend vanishes per unit mass) |
| Null and resampling tests | Correlations from a few objects or chance | 10,000-realisation nulls; jackknife; drop 30% 500 times | 2020ApJ...903..124B, 2022A&A...660A..14R, 2026A&A...705A.209L |
| Pre-registered binning | p-hacking through bin choice | Bin only on physically motivated parameters | 2026MNRAS.546f2284B |
| S/N degradation | Conclusions that hinge on data depth | Degrade the cubes and rerun | 2024MNRAS.528.6768H |
