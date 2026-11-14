---
name: alma-variability-time-domain
description: "Measure and interpret time variability and motion in ALMA data: light curves from seconds to years, stellar and AGN flares, periodicity and power spectra, cross-band time lags, multi-epoch flux comparisons, proper motions of knots, clumps, masers and stars, and proper-motion correction before combining epochs. Use when the user asks whether a source varied, wants a light curve, flare or periodicity analysis, a DCF lag, a proper motion or ejection age, or needs to merge ALMA data taken years apart. Built from 90 ALMA papers (2014-2026)."
---

# Time-domain and variability analysis

This technique turns ALMA data into flux (or polarization, or position) as a function of time, then asks whether
the change is real and what it means: flares, periodic signals, lags between bands, knot or clump motions.
Two mistakes dominate. First, calling calibration drift, a beam change or a change in uv coverage "variability":
several papers check a calibrator, check source or field source on the same timescale, and residual check-source
variability can itself set the systematic uncertainty (~5% in 2015A&A...576A..41B). Second, quoting periodogram
significance against white noise: for Sgr A* at 340 GHz the same peaks drop from ~25.4 and ~12.7 sigma to ~2.9
and ~0.9 sigma once red noise is simulated (2026ApJ..1003L..17Y).

Counts below are from the evidence pack (`skills/packs/variability-time-domain.md`, 90 papers). The pack's regex
also catches "flared disk", "variable alpha_CO", "a_max variable" and similar, so a large share of the 90 papers
(mostly protoplanetary disk and GMC papers, e.g. 2014ApJ...791...20R, 2018ApJ...869L..42H, 2024ApJ...976...88L)
are off-topic, and a few only assume the source does not vary (2016A&A...593A..44L, 2016A&A...593L..19M,
2021A&A...656A..46M). That split is my reading of titles and pack lines, not a verified per-paper ledger, so no
exact counts are given for it. Software counts are the pack aggregates, which include the off-topic papers.
Claims marked "(card)" come from a single paper's methods card, not from the pack excerpts.

## When to use

- A compact source may vary within one execution: M dwarf flares (2018ApJ...855L...2M, 2020ApJ...891...80M),
  brown dwarf pulses (2020A&A...642A..96P), ultracool dwarf flares (2019ApJ...881...33H), Sgr A* minute-scale
  variability (2025ApJ...994..256Y, 2026ApJ..1003L..17Y, 2025ApJ...987..152R).
- Flux comparison across epochs: blazars and AGN cores (2016A&A...586A..70L, 2020A&A...636A..62K,
  2026ApJ..1004..126K), GRB afterglows (2023NatAs...7...80U, 2018ApJ...862...94L, 2019ApJ...878L..26L),
  supernova remnants of decades (2019ApJ...870...59S), water lines against older single-dish data
  (2017A&A...602A..42K). Only after the matched-response check in step 4.
- Positions at two or more epochs: jet knots (2015ApJ...805..186L), evolved-star clumps (2024AJ....167...94H),
  masers (2021ApJ...908..175C, 2018ApJ...866...87B, 2014PASJ...66..106H), runaway stars (2020ApJ...889..178B),
  protostars (2018ApJ...859..165S), background-source tests (2024RMxAA..60..355R, 2019ApJ...878L...8T).
- Combining ALMA data from different cycles on a nearby star with large proper motion (2019A&A...625A.118K,
  2020ApJ...895L...2N, 2015ApJ...798..124R, 2017ApJ...840...32T, 2025ApJ...993..120H).
- Linking outflow knots to accretion bursts seen in a light curve (2024ApJ...961..108K, 2024ApJ...964...48T), or
  modelling a knot train with an assumed periodic ejection history (2019ApJ...874...31W).

## When not to use

- Spectral index or SED work from data at different dates: treat variability as a caveat, not as the
  measurement. Papers that build non-simultaneous spectra say so (2016A&A...593L..19M, 2024ApJ...970...56P).
  Use `spectral-index` or `free-free-synchrotron`.
- Flux-scale equalization between tunings of a steady source (2021A&A...656A..46M uses gencal on a
  non-variable reference). That is calibration; see `self-calibration`.
- Resolved kinematics of disks, envelopes or galaxies ("flared" surfaces, rotation). The regex catches them but
  they are static problems: use `keplerian-disk-kinematics`, `envelope-kinematics-pv`, `galaxy-3d-kinematics`.
- Absolute astrometry at the sub-arcsecond level from data not designed for it: ALMA images showed 1-2 arcsec
  offsets from ICRS in one project (2016A&A...594A.107K). Use relative positions against a reference in the
  same field, or check positional accuracy on a secondary calibrator (~0.03 arcsec in 2017ApJ...840...32T, card).

## Steps

1. **Set the timescale and select data.**
   - Goal: match bin size to the physics and to the sensitivity per bin.
   - Method: seconds for stellar flares (2 s `uvmodelfit` fits in the flare scan of 2018ApJ...855L...2M, card;
     5 s bins in 2020ApJ...891...80M, card; 30 s images in 2020A&A...642A..96P); ~1 min for Sgr A*
     (2026ApJ..1003L..17Y, 2025ApJ...994..256Y); per scan for flare searches (~7 min ALMA scans in
     2019ApJ...881...33H; 6-8 min between phase calibrations in 2020ApJ...894...76W, card; five per-scan images
     in 2024ApJ...970...56P); per execution block for days to weeks (2026ApJ..1004..126K); years for proper
     motions (2015 vs 2021 in 2024AJ....167...94H).
   - Archival selection: 2025ApJ...994..256Y required the Sgr A* field, 230 GHz, resolution below 1 arcsec and
     more than 1 h integration, and found 12 projects (card).
2. **Calibrate every epoch the same way, with separate flux and astrometry branches.**
   - Flux branch: scriptForPI or pipeline per execution, then phase-only self-calibration on bright targets.
     Both Sgr A* periodicity papers used iterative phase-only self-calibration; 2025ApJ...994..256Y started with
     `solint='inf'` and shortened to `int` (card; 2026ApJ..1003L..17Y, card). 2018A&A...619A..40M did phase and
     amplitude self-calibration and reports it "still worked" despite the variability (card), without a
     recovery test in the pack.
   - General practice: amplitude self-calibration against a constant model can absorb intrinsic variability or
     change its normalization, whatever the solution interval. Prefer phase-only for flux-variability work. Use
     amplitude self-calibration only with a time-variable source model and a recovery test (inject a known
     light curve, or show a field or check source is unchanged), and state which was done.
   - Astrometry branch: target self-calibration moves the source toward the model position and can erase
     absolute position information or register epochs differently. Measure positions on data calibrated
     against an external phase calibrator, or measure motions relative to a reference in the same field
     (continuum peak in 2015ApJ...805..186L; reference maser in 2021ApJ...908..175C) and document how the
     registration was validated.
   - Software: CASA (17 papers in the pack aggregate), AIPS (4; used for UVSUB and light curves in
     2018A&A...619A..40M, card), GILDAS (2).
3. **Measure flux per time bin.**
   - Point-source fit to visibilities with CASA `uvmodelfit` (2018ApJ...855L...2M, 2020ApJ...891...80M,
     2020ApJ...894...76W; all card).
   - `tclean` snapshot images plus `imfit` (2025ApJ...994..256Y, card).
   - Average visibilities per scan on long baselines (>150 klambda) with errors from the amplitude spread
     (2015A&A...576A..41B).
   - Flux in a beam-shaped region of each short-bin image (2020A&A...642A..96P).
   - Remove other emission first: image only baselines >100 klambda to drop the disk (2020ApJ...891...80M,
     card); `fixvis` to the target, subtract other sources' models, then average (2024ApJ...970...56P);
     subtract a variable core with UVSUB (2018A&A...619A..40M, card).
   - Polarization of flares without polarization calibration: fit XX and YY separately (2020ApJ...891...80M,
     2018ApJ...855L...2M; cards). General practice: with I = (XX+YY)/2, |XX-YY|/(XX+YY) = |Q'|/I, where Q' is
     Stokes Q in the feed frame. Q' mixes sky Q and U as the parallactic angle changes, so it is a lower bound
     on the total linear polarization fraction (both cards call |Q/I| a lower limit). With a long track, fit the
     XX/YY ratio against parallactic angle instead (2016A&A...593A..44L); 2020ApJ...891...80M used a quiescent
     parallactic-angle fit to bound instrumental polarization at ~1% (card).
4. **Check that the variation is not instrumental.**
   - Calibrator or check source on the same timescale: no variability in calibrator fluxes imaged on the
     flare timescale (2018ApJ...855L...2M, card; gain calibrator in 2020ApJ...891...80M, card), phase
     calibrator within a few percent (2024ApJ...970...56P), check-source variability sets ~5% flux
     uncertainty (2015A&A...576A..41B). 2020ApJ...894...76W compared per-scan stellar fluxes with a field
     background source that it assumed constant (pack assumption; card).
   - Matched spatial response for epoch-to-epoch comparisons: use compatible uv coverage, recoverable angular
     scale, frequency selection, beam and extraction aperture. One ALMA flux was lower than a published value
     because ACA data were not included (2024RMxAA..60..355R); combining whole-band data was less robust
     because of beam changes and interpolation (2019ApJ...870...59S); ALMA recovered a median 63% of APEX flux
     in 2018ApJ...857...19F, so interferometer vs single-dish comparisons need the same care.
   - Beam systematics: compare the light-curve power spectrum with that of the beam size and reject coincident
     peaks (2026ApJ..1004..126K).
5. **Quantify variability.**
   - Excess variance of per-scan fluxes (2018ApJ...855L...2M, 0.017 +/- 0.030 for quiescent Proxima, card).
   - Variability index VI = (Smax - Smin)/(Smax + Smin) per band (2016A&A...586A..70L, card, after Ciaramella
     et al. 2004); with sparse sampling it is a lower limit (same paper, pack).
   - Null test: the distribution of short-bin fluxes is Gaussian with zero mean and RMS matching image noise
     (82 vs 88 uJy, 2020A&A...642A..96P).
   - Structure function SF^2(tau) = <(RM(t+tau) - RM(t))^2> for rotation-measure variability
     (2018ApJ...868..101B, card). First check each RM fit: the largest fitted RMs were suspect because of phase
     wrapping, poor fits and calibration errors at low polarization (same paper, pack); 2018ApJ...868..101B used
     calibrators to set systematic limits on RM (card).
   - Fourier power spectrum with bootstrap errors (2015ApJ...802...69B; 1000 bootstrap realizations against a
     constant-flux simulation with normally distributed per-EB errors in 2026ApJ..1004..126K).
   - Periodicity: generalized Lomb-Scargle with false-alarm probability from simulated light curves
     (2026ApJ..1003L..17Y, 10^5 curves with red plus white noise; 2025ApJ...994..256Y, 10^5 red-noise curves
     after linear detrending, card). Choose and justify the null for the source and sampling (red noise for
     Sgr A*; constant flux with Gaussian errors in 2026ApJ..1004..126K) and test correlated noise where it is
     plausible.
   - FAP resolution: N simulations resolve an empirical FAP down to only about 1/N. 10^5 curves reach about
     1e-5, enough for the 3 sigma threshold of 1.35e-3 (2026ApJ..1003L..17Y) but not for 2.9e-7 (5 sigma,
     2025ApJ...994..256Y, card). For a 5 sigma claim use well over 10^7 simulations or a fitted tail that you
     validate; the card does not say how 2025ApJ...994..256Y reached FAP < 1.8e-7.
   - Smoothing splines through Q and U before differentiating (2025ApJ...987..152R,
     `scipy.interpolate.UnivariateSpline`): split the light curve into segments at gaps >= 1.8 min, fit each
     segment, trim edge points, and report sensitivity to the discrete settings tested (kappa in {3,4,5},
     sigma in {0.1,0.5}, n_T in {0,1,2,3}).
   - Solar oscillations: per-pixel power spectra fit with a log-normal plus linear-in-ln(nu) model
     (2021A&A...652A..92N). Coarse resolution and correlated pixels make the observed p-mode rms a lower limit
     (same paper), so do not treat pixels as independent when averaging or computing errors.
6. **Cross-band lags and event rates.**
   - Discrete correlation function with a Gaussian fit to the peak (2020A&A...636A..62K: c = -105 +/- 4 d for
     the 7 d LAT binning and -112 +/- 6 d for 30 d; the card reads this as ALMA 3 mm lagging the gamma rays by
     105-112 d). Always state which band leads and the sign convention. ZDCF (2015A&A...576A..41B, where
     zero-lag spikes prevented a lag).
   - Flare rates from small numbers with Gehrels 95% intervals (2020ApJ...891...80M, card: ~20 events/day,
     95% range 3.6-63 for AU Mic).
7. **Model the time behaviour.**
   - Flares: spectral index across sidebands, then the optically thin gyrosynchrotron relation
     alpha = 1.22 - 0.9 delta for the electron index (2018ApJ...855L...2M gives delta = 3.32 +/- 0.83, card).
   - Non-detections: 2019ApJ...881...33H turns a 3 sigma flux limit (10.6 uJy) into an emitting-region size
     bound (<= 0.02 R_J) only under assumed gyrosynchrotron physics (B = 600 G, delta = 2, d = 12.45 pc). The
     size bound is conditional on those assumptions, and the authors note non-detections cannot identify the
     emission mechanism.
   - GRB afterglows: broken power-law light curve (2023NatAs...7...80U), forward shock with jet-break factor
     (2019ApJ...884L..58U), reverse-shock components (2018ApJ...862...94L, 2019ApJ...878L..26L), off-axis
     templates (2017ApJ...850L..21K).
   - Sgr A* periodicity: Doppler-boosted hotspot fit by least squares, then MCMC (2025ApJ...994..256Y, card).
     Its GR ray-tracing runs (a* = 0, 0.998; hotspot radius 0.5, 1.0 rg) differed from the Doppler model by
     <2% of the amplitude (card), but the fit itself neglects GR and finite hotspot size, does not model
     hotspot evolution, reports statistical errors only and leaves spin unconstrained (pack). Treat the
     geometry as model-dependent.
   - Blazars: Doppler factor from a cubic spline through variable-binned light curves (2019MNRAS.490.5300D).
8. **Proper motions.**
   - Fit positions per epoch, simultaneously for all components: 2D Gaussians with CASA `imfit`
     (2024AJ....167...94H); align maps on continuum peaks after convolving to a common resolution
     (2015ApJ...805..186L); measure relative to a reference maser (2021ApJ...908..175C).
   - Position error per epoch: about beam/(S/N) (2024AJ....167...94H, citing ALMA memo 620) or
     FWHM/(I/sigma_I) (2018ApJ...859..165S). Sub-beam shifts can be measured this way; a motion claim needs
     these errors plus registration and calibration systematics. 2019ApJ...871..100H could not exclude a
     calibration issue for its 0.046 arcsec offset (beam 0.1-0.15 arcsec).
   - Galactic sources: v_t = 4.74 mu[arcsec/yr] d[pc] km/s (general practice); 2015ApJ...805..186L takes the
     jet as in the sky plane so v_t is the jet speed. Ages = distance/velocity with no acceleration
     (2024AJ....167...94H, acceleration effect 5-10%).
   - Cosmological jets: use apparent speed beta_app = mu D_A (1+z)/c with the angular-diameter distance
     (general practice), not the pc formula; 2020A&A...636A..62K converts 0.59 mas/yr to ~6.0 c for 3C 273.
   - Association tests: compare the observed shift with the expected stellar proper motion (0.6 arcsec expected
     vs <=0.03 arcsec observed in 2024RMxAA..60..355R; Band 7 two years earlier in 2019ApJ...878L...8T).
9. **Correct proper motion before combining epochs.**
   - CASA `fixplanet` to the expected coordinates at a reference date (2020ApJ...895L...2N); shift the phase
     center of the older data (2019A&A...625A.118K); adjust visibility phases (2015ApJ...798..124R); correct
     proper motion and shift to epoch 2000.0, then analyse in GILDAS (2017ApJ...840...32T, card).
10. **Episodic ejection histories.** Kinematic ages of knots compared with an infrared or submm light curve
    (2024ApJ...961..108K with a WISE/NEOWISE 4.6 um light curve, card; 2024ApJ...964...48T with an ~8 yr JCMT
    850 um light curve, card). 2019ApJ...874...31W instead models the knot train with an ejection periodicity
    of ~93 yr estimated from the knot spacing, with no light-curve comparison.

## Parameter defaults and ranges

Documented examples from the pack and cards; the "common choice" column is what the listed papers did, not a
validated default.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Time bin, stellar flares | per scan to find, seconds to resolve | 2 s - ~7 min | 5 | 2018ApJ...855L...2M (2 s, card), 2020ApJ...891...80M (5 s, card), 2020A&A...642A..96P (30 s), 2019ApJ...881...33H (~7 min) |
| Time bin, Sgr A* | ~1 min | ~1 min | 2 | 2026ApJ..1003L..17Y, 2025ApJ...994..256Y |
| Per-scan flux checks (ALMA) | scan between phase calibrations | ~6-8 min | 2 | 2019ApJ...881...33H (~7 min), 2020ApJ...894...76W (6-8 min, card) |
| Long-baseline cut to isolate a point source | >100-150 klambda | 100-150 klambda | 2 | 2020ApJ...891...80M (card), 2015A&A...576A..41B |
| Periodicity threshold | FAP from simulations | FAP < 1.35e-3 (3 sigma) to < 2.9e-7 (5 sigma) | 2 | 2026ApJ..1003L..17Y, 2025ApJ...994..256Y (card) |
| Noise model for the null | chosen per source | PSD f^-2 or f^-2.20 plus white noise; constant flux with Gaussian per-EB errors | 3 | 2026ApJ..1003L..17Y (f^-2), 2025ApJ...994..256Y (f^-2.20, card), 2026ApJ..1004..126K |
| Number of simulated light curves | 10^5 for red-noise FAP | 10^3 - 10^5 | 3 | 2026ApJ..1004..126K (1000 bootstrap), 2026ApJ..1003L..17Y, 2025ApJ...994..256Y (card) |
| Epoch spacing (paper calls it "frequency resolution") | mean time between epochs | ~3 d | 1 | 2026ApJ..1004..126K |
| DCF bin | matched to light-curve binning | 12 d, 33 d | 1 | 2020A&A...636A..62K |
| Flux-scale uncertainty adopted | ~10% | ~5% - ~20% | 4 | 2015A&A...576A..41B (~5%, from check source), 2020ApJ...894...76W (~10%, card), 2020A&A...636A..62K (10%, VLBA), 2016A&A...593A..44L (~20%) |
| Residual relative scaling scatter after alignment | not an adopted uncertainty | 2.5% | 1 | 2021A&A...656A..46M |
| Upper limit on flux in a bin | 3 sigma | 3 sigma | 2 | 2020A&A...642A..96P (264 uJy per 30 s), 2019ApJ...881...33H (110 uJy per scan) |
| Position error per epoch | beam/(S/N) | beam/(S/N); ~1/10 beam for VLBA | 3 | 2024AJ....167...94H, 2018ApJ...859..165S, 2020A&A...636A..62K |
| Smoothing spline (Q, U) | discrete grid, report sensitivity | kappa {3,4,5}, sigma {0.1,0.5}, n_T {0,1,2,3}; split at gaps >= 1.8 min | 1 | 2025ApJ...987..152R |
| Solar PSD fit range | min chi2 over a grid | 2-4 mHz to 30-50 mHz | 1 | 2021A&A...652A..92N |

Paper counts are my count of the bibcodes in each row.

On the epoch-spacing row: 2026ApJ..1004..126K calls ~3 d its "frequency resolution", but days are a time unit.
Mean epoch spacing sets the cadence (and so the highest usable frequency), the Fourier frequency resolution is
about 1/(total baseline), and the period uncertainty depends on both and on S/N (general practice). Report all
three separately.

## Software

Pack aggregates (all 90 papers, so they include off-topic ones):

| Software | Count | Used for |
|---|---|---|
| CASA | 17 | calibration, per-bin imaging, `uvmodelfit` (2 as "casa uvmodelfit" + 1 as "uvmodelfit"), `imfit` (2), `tclean` (2), `fixvis` (1), `fixplanet` (1), `gencal` (1) |
| AIPS | 4 | light curves and UVSUB core subtraction in 2018A&A...619A..40M (card); the pack does not show the others |
| GILDAS | 2 | analysis after CASA calibration (2017ApJ...840...32T, card) |
| Fermi ScienceTools / gtlike | 2 / 1 | gamma-ray light curves for ALMA comparisons (2020A&A...636A..62K, 2019MNRAS.490.5300D) |
| Difmap | 1 | VLBA Gaussian component fits for jet proper motions (2020A&A...636A..62K) |
| ZDCF | 1 | cross-correlation of light curves (2015A&A...576A..41B) |
| scipy | 1 | smoothing splines for polarized light curves (2025ApJ...987..152R) |
| CIAO 4.9 | 1 | Chandra data alongside ALMA (2019PASJ...71...68K, off-topic for this skill) |
| Swift burst analyser, pymultinest | 1 each | GRB multiwavelength modelling (pack aggregate) |

RADMC-3D (5), emcee (4), eddy (3) and bettermoments (2) in the aggregate come mostly from off-topic disk papers.
The cards rarely state which Lomb-Scargle or DCF implementation was used.

## Pitfalls

- **Calibration masquerading as variability.** Absolute flux was uncertain by ~20% when Titan scans were
  flagged (2016A&A...593A..44L); ALMA lacked Tsys on Sgr A* and needed a correction (2015ApJ...802...69B); flux
  calibration uncertainty is often left out of fit errors (2021A&A...656A..46M).
- **Mismatched spatial response.** Different arrays, uv coverage or beams change the recovered flux
  (2024RMxAA..60..355R, 2019ApJ...870...59S, 2026ApJ..1004..126K).
- **Amplitude self-calibration on a variable target** can remove or rescale the signal (general practice; see
  step 2). Target self-calibration also compromises absolute positions for proper motions.
- **Wrong null model.** White-noise significance overstated Sgr A* peaks by an order of magnitude
  (2026ApJ..1003L..17Y). Published PSD slopes are examples, not defaults.
- **Simulation-limited FAP.** A 5 sigma FAP needs far more than 10^5 simulations (step 5).
- **Many trials.** 2025ApJ...994..256Y found significant periodicity in 3 of 77 light curves (card); the card
  notes the look-elsewhere effect over the 77 curves was not accounted for (card's inference).
- **Flux correlated with beam size** is a systematic (2026ApJ..1004..126K).
- **Non-simultaneous data.** Spectra and multiwavelength polarimetry from different dates limit conclusions
  (2016A&A...593L..19M, 2019ApJ...884L..58U, 2024ApJ...970...56P, 2025MNRAS.540..364A).
- **Sampling.** Short observations can miss flares (2019ApJ...881...33H); a single few-hour epoch limits
  conclusions (2020A&A...642A..96P, 2018A&A...619A..40M); a single track and coarse cadence
  (2015A&A...576A..41B); irregular sparse sampling makes VI a lower limit (2016A&A...586A..70L); limited
  duration makes decay timescales approximate (2026ApJ..1003L..17Y); the true flare timescale is unknown with
  no simultaneous data (2019ApJ...871...72M); sensitivity only to timescales longer than ~5 yr
  (2024ApJ...964...48T).
- **Gaps.** Zero-filled gaps lower measured power; 2021A&A...652A..92N applied correction factors 0.6 (Band 6)
  and 0.7 (Band 3). Separately, its p-mode rms is a lower limit because of coarse resolution and correlated
  pixels.
- **Zero-lag spikes** in correlation functions of simultaneous data can prevent lag estimates
  (2015A&A...576A..41B).
- **Rotation measures.** The largest fitted RMs can be phase-wrap or low-polarization artefacts
  (2018ApJ...868..101B).
- **Astrometry.** A sub-beam offset could not be separated from a calibration issue in 2019ApJ...871..100H;
  complex maser distributions bias proper motions (2021ApJ...908..175C). As a general check, two epochs taken
  in different array configurations (or with different instruments) can carry registration systematics; the
  2018ApJ...866...87B card raises this as its own inference about VLA maser epochs.
- **Polarization of flares.** With only XX and YY, |Q/I| is a feed-frame lower limit (2020ApJ...891...80M);
  single-epoch polarization assumes a non-variable source (2016A&A...593A..44L).
- **Not stated.** Across the pack, cards most often flag missing CASA version (6), self-calibration solution
  intervals (5), source coordinates (4), `uvmodelfit` starting parameters (3) and flux scale uncertainty (2+2).
  The cards rarely state how flux was extracted per time bin (e.g. 2018ApJ...855L...2M, 2024RMxAA..60..355R).
  Report all of these.

## Verification checks

What the papers did:
- Calibrator or check-source behaviour on the variability timescale (2018ApJ...855L...2M, 2020ApJ...891...80M,
  2024ApJ...970...56P); residual check-source variability used to set the flux uncertainty
  (2015A&A...576A..41B).
- Short-bin flux RMS equals the per-bin image noise (2020A&A...642A..96P).
- Simulated-light-curve FAP (2026ApJ..1003L..17Y, 2025ApJ...994..256Y) and beam-size power spectrum
  comparison (2026ApJ..1004..126K).
- Vary DCF binning and repeat on a time subset (2020A&A...636A..62K).
- Compare integrated flux with earlier publications (101 +/- 9 vs 106 +/- 12 uJy, 2018ApJ...855L...2M, card;
  3.7 vs 3.5 mJy, 2020ApJ...895L...2N).
- Repeat on antenna subsets (DA-only, DV-only, with and without PM antennas, 2016A&A...593A..44L).
- Instrumental polarization bounded from a quiescent parallactic-angle fit (~1%, 2020ApJ...891...80M, card).
- Residual images after the position fits reach the noise (0.4 and 0.2 mJy, 2024AJ....167...94H); test the
  no-acceleration assumption (5-10%, same paper).
- Propagated ephemeris matches independent positions to 0.025-0.029 arcsec (2016A&A...594A.107K); secondary
  calibrator offsets set ~0.03 arcsec positional accuracy (2017ApJ...840...32T, card).
- GR ray tracing for a few spin and hotspot-size cases differs from the Doppler model by <2% of the amplitude
  (2025ApJ...994..256Y, card); this checks the light-curve shape, not the full physical model.

What a careful referee adds:
- Show the calibrator and a field source on the same light-curve plot with identical binning.
- For epoch comparisons, show matched uv range, beam and aperture, or image all epochs with a common uv cut.
- Report the flux-scale uncertainty separately from the statistical error and state whether it cancels in
  relative (within-execution) variability.
- For periodicity, give the number of light curves and trial frequencies, the null model and its parameters,
  the number of simulations, and test a second noise model.
- For lags, state which band leads and the sign convention.
- For proper motions, show that the reference frame (continuum peak, maser, star) is itself stationary and that
  positions were not set by target self-calibration.

## Source cards

Full list: `references/sources.md` (90 papers, many off-topic). Most informative for this technique:

- 2018ApJ...855L...2M: Proxima flare, 2 s `uvmodelfit` bins, excess variance, |Q/I|
- 2020ApJ...891...80M: AU Mic flares, 5 s bins, >100 klambda, Gehrels rates
- 2020A&A...642A..96P: 30 s images, Gaussian null test, 3 sigma pulse limit
- 2019ApJ...881...33H: per-scan flare search, conditional gyrosynchrotron limits
- 2020ApJ...894...76W: per-scan `uvmodelfit` compared with a background source
- 2024ApJ...970...56P: `fixvis`, per-scan images, phase-calibrator check
- 2015A&A...576A..41B: long-baseline per-scan fluxes, check source, ZDCF
- 2015ApJ...802...69B: Sgr A* monitoring, bootstrap power spectrum
- 2026ApJ..1003L..17Y: GLS with red-noise FAP
- 2025ApJ...994..256Y: archival Sgr A* periodicity, hotspot model
- 2025ApJ...987..152R: Q-U spline analysis
- 2026ApJ..1004..126K: per-EB power spectrum, beam systematics
- 2016A&A...586A..70L: blazar variability index
- 2018ApJ...868..101B: RM structure function and RM fit reliability
- 2020A&A...636A..62K: DCF lag ALMA vs Fermi, VLBA proper motions
- 2023NatAs...7...80U: GRB light-curve break
- 2021A&A...652A..92N: solar oscillation power spectra
- 2024AJ....167...94H: clump proper motions, ages
- 2015ApJ...805..186L: knot proper motion from SMA vs ALMA
- 2021ApJ...908..175C: maser proper motions relative to a reference
- 2024RMxAA..60..355R: proper-motion association test, missing-ACA flux caveat
- 2020ApJ...895L...2N: `fixplanet` before combining epochs
- 2024ApJ...961..108K: ejection dating against a light curve
