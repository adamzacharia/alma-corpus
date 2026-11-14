---
name: alma-stacking
description: "Stack ALMA data on known positions, redshifts or velocity fields to measure the average signal of sources or lines too faint to detect one by one: image-plane and uv-plane continuum stacks, redshift-aligned spectral stacks, Keplerian velocity-aligned stacks in disks, velocity-field stacks inside galaxies, and multi-transition line stacks, with weighting, upper limits and significance tests. Use when the user asks for a mean or median flux, gas or dust mass of an undetected sample, a stacked spectrum, a broad-wing or outflow search, a weak line in a disk, a stacked upper limit, or which stacking tool and weights to use. Built from 118 ALMA papers (2013-2026)."
---

# Stacking undetected sources and faint lines

Stacking adds many noisy measurements that share a known position, redshift or velocity pattern so that the
average signal rises above the noise, roughly as sqrt(N) for independent noise (general practice). In the ALMA
literature it serves two different goals: an average flux or mass for a sample that is mostly undetected, and a
higher-S/N spectrum of one source in which the signal is spread over many pixels or transitions. The two mistakes
that matter most: claiming a stacked detection without an empirical noise test (random-position, off-line or
mock stacks), and reading a weighted mean as the sample average when a few high-weight or bright sources
dominate it (2020A&A...633A.160C).

Counts below are from the evidence pack (`skills/packs/stacking.md`, 118 papers). Where a count is my own tally
of the pack lines, it says so. I left out papers that look off-topic for ALMA stacking from their pack lines or
titles: HST or JWST PSF and image stacking (2025A&A...700A.285W, 2026A&A...705L..14D, 2025ApJ...988..135M,
2026A&A...706A...9Z), optical/NIR spectral stacking (2026ApJ..1000..308W), and a satellite-orbit paper where
"stacked" means concatenating epochs (2017ApJ...839L..15G, see Steps 3f).

## When to use

Pack science fields: high_z_galaxies 72, protoplanetary_disks 28, astrochemistry 23, nearby_galaxies 18,
star_formation 14, agn_and_quasars 13, galaxy_clusters_and_sz 12 (aggregate counts; a paper can carry several).

- **Average continuum of a catalogue-selected sample** (colour-, mass-, UV- or NIR-selected galaxies) in deep or
  archival maps: ALESS colour-selected galaxies (2014ApJ...780..115D), NIR-selected objects (2016ApJ...833..195W),
  H-band selected galaxies for cosmic dust and gas densities (2020ApJ...892...66M), 1580 undetected LBGs
  (2020A&A...633A.160C), mass-complete 4<z<5 samples (2024A&A...688A..55M), undetected disks in a cluster
  (2020A&A...640A..27V).
- **Average line flux or upper limit for CO-undetected galaxies**: passive galaxies (2018ApJ...860..103S,
  2021ApJ...908...54W), cluster members (2018ApJ...856..118H, 2025ApJ...985..194P, 2018ApJ...853..195W),
  low-metallicity galaxies (2019MNRAS.485.2092C).
- **Faint spectral features across a sample**: broad [CII] wings as outflow tracers in quasars
  (2019A&A...630A..59B, 2019A&A...631A..78S, 2026ApJ..1000..312Z), faint lines in a template spectrum of lensed
  DSFGs (2014ApJ...785..149S, which did not correct for differential magnification; see Pitfalls).
- **Weak lines in a rotating disk**: shift spectra by the projected Keplerian velocity before summing
  (2016ApJ...832..204Y, 2018A&A...616A.100Y, 2021ApJ...908...46B, 2019ApJ...880...69Y, 2024ApJ...965..147B,
  2025ApJ...984L..19Y, 2026A&A...705A.198M).
- **Faint isotopologues inside resolved galaxies**: shift each spaxel by the 12CO velocity field and co-add
  (2025MNRAS.541.4031D with STACKARATOR).
- **Resolved line ratios across galaxies**: a spectrally stacked CO(2-1)/CO(1-0) ratio reported next to the
  area-weighted median and the ratio of sums of S/N>5 sightlines (2025ApJ...988..162D, PyStructure and PyStacker).
- **Many transitions of one species**: co-add maps or spectra of unblended lines with similar morphology
  (2019ApJ...871..112X, 2017A&A...607L...5Q, 2017A&A...601A...4A, 2017ApJ...843...27L, 2016ApJ...823L..10W,
  2019ApJ...877L..25M), or different molecules that share the same rotation (2021ApJ...908...46B).
- **A moving target with a predicted position**: shift images to the ephemeris position and sum
  (2018AJ....156..164B).

## When not to use

- **The sources are individually detected at useful S/N and you want per-source values.** Measure each one with
  `uv-plane-fitting` or `source-extraction-counts`. If you want the mean of the whole sample, stack all members,
  detected and undetected (2018ApJ...860..103S averaged the inverted images of its targets for the continuum stack);
  a stack of only the non-detections is a conditional mean of the faint subset and is biased low if reported as the
  sample mean. Detections can also be stacked on their own to validate the method (2018ApJ...860..103S,
  2018ApJ...856..118H) or to get an average morphology (2018ApJ...861....7F, 33 ASAGAO sources).
- **You need the distribution, not the mean.** A stack gives one number per bin. 2015MNRAS.453L..83M fit a
  log-normal SFR distribution with a hierarchical model and only compared its linear mean with mean-stacked
  Herschel maps. Use `stats` for survival analysis or hierarchical fits.
- **The sample is physically heterogeneous in the quantity you stack.** 2014ApJ...785..149S found no single
  model fits its stacked template (chi2 min 10.4 for 3 dof) and names the heterogeneous sample as the cause;
  2019A&A...630A..59B notes stacking dilutes outflow orientations. Split into bins first, or do not stack.
- **The disk geometry is unknown or the disk is thick or highly inclined.** Keplerian alignment assumes a thin
  disk with known inclination and PA (2016ApJ...832..204Y, 2021ApJ...908...46B); highly inclined disks can give
  overestimated masses (2021ApJ...908...46B). Use `keplerian-disk-kinematics` to get the geometry first.
- **Combining epochs or arrays of one source to make a deeper image** is concatenation and imaging, not stacking
  of undetected sources (2017ApJ...839L..15G used `fixplanet` and natural weighting). Use `imaging-choices` or
  `array-combination`.

## Steps

1. **Define the sample and the bins.** Goal: a sample whose members plausibly share the quantity you average.
   - Select on external catalogues with explicit cuts: M*>1e9 Msun, z<4, F160W<27.5 AB, and >3.5" from the five
     brightest detections (2016ApJ...833...68A); mass and main-sequence-offset groups LM logM<10, HM-aMS
     logM>10 and DeltaMS>-0.3, HM-bMS DeltaMS<-0.3 (2025ApJ...985..194P); 5 beta, 9 mass and 3 z bins
     (2020A&A...633A.160C); redshift bins 0.3-0.6 ... 2.3-3.2 with cumulative mass thresholds stepping down
     0.5 dex from 1e11 Msun (2020ApJ...892...66M); four L[CII] bins split at z=5 (2020A&A...643A...2B).
   - Remove sources that would dominate or contaminate: beta outliers, sources near >=4 sigma detections,
     pbcor<0.5, multiple images (2020A&A...633A.160C); the two most massive galaxies (2016ApJ...819...82S); one
     quasar (2026ApJ..1000..312Z); ALMA primary targets within 3", tested both ways (2024A&A...688A..55M).
   - Write the cuts down; "exact stacking procedure and weights" and "stacking procedure details" are among the
     settings the cards flag as not stated (2 papers each, pack aggregate).

2. **Prepare the data so the inputs are comparable.** Goal: same units, frame, resolution and clean of
   unrelated flux.
   - Correct astrometry before cutting stamps: a fixed offset dRA=+0.076", dDec=-0.279" (2020ApJ...892...66M),
     a 0.3" declination phase rotation of all stacked datasets (2016MNRAS.462.1192L), ~1.4" astrometric
     corrections of moment-0 maps (2020MNRAS.497.2771M).
   - Remove or mask bright unrelated sources: subtract a clean model of the bright sources from the visibilities,
     leaving out every clean component within 1" of a stacking position so the targets' own emission is protected
     (2016MNRAS.462.1192L, CASA 4.4, clean depth 1.8 mJy/beam, cell 0.2"); mask non-target continuum detections
     (2020A&A...643A...2B); mask detections before stacking 122 non-detections (2020A&A...640A..27V). A residual
     map with detections subtracted is a reasonable base for stamps of undetected sources (my recommendation; the
     2020ApJ...892...66M card summary describes this, but its quoted text only gives the 20" stamp size).
   - Handle the primary beam (A = PB response, 0-1). Keep only area with PB coverage >75% (2020ApJ...892...66M).
     Two documented routes: PB-correct each stamp, then weight-average with weights equal to the inverse square of
     the PB correction, i.e. A^2 (2014ApJ...780..115D); or stack non-PB-corrected maps with weights from each
     map's rms (2021ApJ...908...54W, 400 km/s channel maps). Weighting alone does not restore attenuated flux:
     on uncorrected data d_i either correct the result for the PB or use the response-normalized estimator
     S = sum(A_i d_i / sigma_i^2) / sum(A_i^2 / sigma_i^2), which for equal sigma_i is the first route (general
     practice). In the uv plane 2016MNRAS.462.1192L weighted visibilities by PB attenuation squared.
   - For spectra: put every spectrum in the rest frame and on one channel grid (50 km/s, 2025ApJ...985..194P;
     60 km/s bins, 2026ApJ..1000..312Z), or rebin so each line FWHM spans the same number of channels
     (FWHM_min=270 km/s, 2019A&A...631A..78S). Drop channels with atmospheric transmission <0.5
     (2019A&A...630A..59B).
   - Propagate redshift and linewidth uncertainties through the alignment: 2019MNRAS.485.2092C resampled redshift
     displacements and linewidths with MCMC and found a negligible effect on its stacked line fluxes. That result
     does not transfer; rerun the test for your sample and check recovered widths, fluxes and wings.
   - Optionally scale each input to a common physical quantity before stacking: visibilities rescaled to
     rest-frame 150 um luminosity with the Bethermin et al. 2017 template using CASA `gencal`/`applycal`
     (2024A&A...688A..55M); individual dust mass maps (2019MNRAS.485.2092C); peak-normalized spectra
     (2026ApJ..1000..312Z, 2020ApJ...905...85S).

3. **Stack in the domain that fits the data.** Goal: the average with the noise handled correctly.
   - a. **Image plane, continuum.** Weighted average of aligned postage stamps (2014ApJ...780..115D, also median;
     2016ApJ...833..195W; 2020A&A...643A...2B; 2018ApJ...860..103S simply averaged inverted images). Weighted
     co-add pixel by pixel (2019MNRAS.485.2092C).
   - b. **uv plane, continuum.** Phase-shift visibilities to each position and average with weights, then image
     (2016MNRAS.462.1192L with PB-attenuation-squared weights; 2018ApJ...861....7F; 2020A&A...633A.160C with
     STACKER and four weight schemes; 2024A&A...688A..55M concatenating per mass bin, `tclean`, central pixel).
     uv stacking lets you flag short baselines (<18.2 m or <21 m, 2016MNRAS.462.1192L) and fit sizes in the uv
     plane.
   - c. **Spectral stacks of galaxies.** Inverse-variance weighted mean using line-free channel rms
     (2025ApJ...985..194P), per-channel 1/sigma^2 (2019A&A...630A..59B), on a 500 km/s grid and 600 km/s line
     channels (2014ApJ...785..149S). 1D spectra and 3D cubes pixel by pixel with weights 1, 1/sigma_rms^2 and
     1/S_peak (2019A&A...631A..78S, Line Stacker). For line non-detections, collapse to one wide channel: 400 km/s
     (2021ApJ...908...54W, 2018ApJ...856..118H), the mean FWZP of 753 km/s (2019MNRAS.485.2092C), 700-800 km/s
     (2020ApJ...902..109B).
   - d. **Keplerian velocity-aligned stacks in disks.** Shift each pixel's spectrum by
     -v_kep(r) cos(phi) sin(i) and sum over annuli or the whole disk (2024ApJ...965..147B with GoFish;
     2016ApJ...832..204Y; 2018A&A...616A.100Y). Get v_LOS per annulus from a velocity map (bettermoments, eddy)
     when the geometry is uncertain (2025ApJ...984L..19Y). To fit M* and Vsys, grid-search for the parameters
     that maximize the S/N of the aligned stack (2018A&A...616A.100Y; 2021ApJ...908...46B; 2019ApJ...880...69Y).
     For gas-poor disks, stack in both rotation directions (2026A&A...705A.198M). Inspect the spectra first and
     mask absorption or contaminated channels; if part of the disk is contaminated, use a clean sector and test it:
     2019ApJ...880...69Y masked absorption channels and used only the blueshifted region (PA 48-228 deg) in its
     M*/Vsys search.
   - e. **Velocity-field stacks inside galaxies.** Shift every 12CO-detected spaxel by the 12CO moment-1
     velocity and co-add, globally, in elliptical radial apertures, or by quadrant (2025MNRAS.541.4031D,
     STACKARATOR).
   - f. **Multi-transition and moving-target stacks.** Inverse-variance weighted stack of moment-8 peak-intensity
     maps of uncontaminated transitions (2019ApJ...871..112X); noise-weighted mean of cubes of different molecules (2021ApJ...908...46B); uv-domain
     concatenation of three lines after velocity regridding (2016ApJ...823L..10W). Shift to the predicted
     satellite position and sum (2018AJ....156..164B).

4. **Measure the stacked signal.** Goal: a flux that does not depend on an unchecked size assumption.
   - Unresolved continuum: peak or central pixel (2024A&A...688A..55M, 2D Gaussian as cross-check); small
     aperture with a dirty-beam aperture correction assuming unresolved sources (2016ApJ...833..195W, 0.5"
     diameter, card section 3.3). Point-source uv fits per galaxy then a weighted mean (2019MNRAS.485.2092C, GILDAS `uv_fit`).
   - Possibly resolved: aperture S/N>=5 then 2D Gaussian with free widths, else aperture flux
     (2020ApJ...892...66M); Sersic fit with galfit on the stacked image plus uvmultifit check
     (2018ApJ...861....7F); uv-domain Gaussian size (2016MNRAS.462.1192L). Compare peak and extended flux:
     2017ApJ...834..135T found 0.42 mJy extra within a 2.0" aperture.
   - Spectra: Gaussian fit with nested sampling and bootstrap channel errors (2025ApJ...985..194P, dynesty);
     single vs double Gaussian by BIC with MCMC (2025MNRAS.541.4031D, GAStimator); narrow plus broad Gaussian
     (2026ApJ..1000..312Z, 2019A&A...631A..78S).
   - Integration windows depend on what you measure. Total line flux: within twice the FWHM line width
     (2018A&A...616A.100Y) or over V*+-5 sigma of a Gaussian fit (2026A&A...705A.198M). The S/N statistic maximized
     in a Keplerian grid search: integrated intensity within the 1 sigma Gaussian width (2021ApJ...908...46B); this
     is an optimization statistic, not a total flux. Line ratios: both lines integrated over the same 1 sigma window
     (2019ApJ...880...69Y). Give the window bounds; a +-1 sigma window holds about 68% of a Gaussian line's flux,
     so correct for the missed fraction if you quote a total (general practice).

5. **Estimate the noise empirically.** Goal: an uncertainty that includes confusion and non-Gaussian noise.
   - Random positions: N random positions per sample, the random stack repeated 50 times (2014ApJ...780..115D);
     100 empty positions
     (2019A&A...630A..59B); blank-sky stacks and p-values (2018ApJ...853..195W); randomized galaxy positions give
     only non-detections (2020ApJ...892...66M, card); random shifts give 0.02% chance, 3.5 sigma
     (2018AJ....156..164B).
   - Off-line windows and shuffles: 1000 random off-line windows of the fitted FWZI (2025MNRAS.541.4031D);
     7 km/s noisy windows, bootstrapped (2026A&A...705A.198M); 3000 channel shufflings at a line-free frequency
     (2014ApJ...785..149S); rescale errors so Var(S/sigma)=1 in line-free channels (2019MNRAS.485.2092C).
   - Bootstrap over the sample, which adds population variance: 100 realizations (2024A&A...688A..55M), 1000
     (2026ApJ..1000..312Z); also 2020A&A...643A...2B and 2017A&A...599A.134S. 2018ApJ...853..195W bootstrapped
     its PACS, ALMA continuum, ATCA and ALMA spectral stacks; the 5000 resamplings it states are for PACS.
   - Carry the flux-scale uncertainty separately from the thermal noise: 5% flux calibration uncertainty in the
     error propagation (2025ApJ...988..162D), 20% systematic flux uncertainty (2018A&A...616A.100Y). A calibration
     error shared by inputs from the same data set does not average down with N; add it after stacking and note
     any correlation between inputs (general practice).

6. **Convert to physical quantities and report limits.** Goal: a mean property with its assumptions explicit.
   - Upper limits are mostly 3 sigma: 6 of the 7 papers whose pack excerpts state a stacked limit with its level
     (my tally of the excerpt method and result lines: 2019MNRAS.485.2092C, 2018ApJ...860..103S,
     2021ApJ...908...54W, 2020A&A...640A..27V, 2018ApJ...853..195W, 2026A&A...705A.198M); 2018ApJ...856..118H used
     5 sigma. State which.
   - Say which estimand each number is: a mean of individual quantities (2020A&A...633A.160C stacked IRX as the
     mean of individual IRX values), a weighted mean, a median, or a ratio of stacked measurements. They differ:
     2025ApJ...988..162D reports R21 as an area-weighted median 0.64, a ratio of sums 0.70 and a stacked ratio
     0.71.
   - The conversion carries assumptions that apply to the stack as a whole: one Tdust for all sources
     (2017A&A...599A.134S, 40 K; 2018ApJ...860..103S, 25 K with kappa_235GHz=0.42 cm2/g and GDR=100), a fixed
     alpha_CO (2020MNRAS.497.2771M, 4.6 and 0.8), the mean redshift of the stack (2021ApJ...908...54W, z=1.476).
     Use `dust-continuum-mass` and `gas-mass-co-conversion` for the formulas.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count, my tally of pack lines) | Examples |
|---|---|---|---|---|
| Spectral stack weights | inverse variance (1/sigma^2) | equal, 1/sigma^2, 1/S_peak | 6 (my tally of excerpt method lines) | 2025ApJ...985..194P, 2019A&A...630A..59B, 2014ApJ...785..149S, 2026ApJ..1000..312Z, 2021ApJ...908...46B (cubes of several molecules), 2019A&A...631A..78S |
| Transition-map stack weights | inverse variance per transition | (one example) | 1 | 2019ApJ...871..112X (moment-8 peak-intensity maps, not spectra) |
| Continuum stack weights | PB-attenuation based | PB^2; PB^2 x F_UV^2; PB^2 x mu^2; equal | 3 (my tally) | 2014ApJ...780..115D, 2016MNRAS.462.1192L, 2020A&A...633A.160C |
| Mean vs median | weighted mean | mean and median both reported | 1 does both | 2014ApJ...780..115D |
| Channel for individual line widths (input, before stacking) | 20 km/s | (one example) | 1 | 2020MNRAS.497.2771M |
| Stack channel grid | 50-60 km/s | 50, 60, 125 km/s (3D cube stack); 500 km/s grid for a wide template | 5 (my tally) | 2025ApJ...985..194P (50), 2026ApJ..1000..312Z (60), 2019A&A...631A..78S (60, mean after rebinning), 2020MNRAS.497.2771M (125), 2014ApJ...785..149S (500) |
| Collapsed line channel or integration width | 400 km/s | 400-800 km/s; mean FWZP 753 km/s; 600 km/s line-centred channels | 5 (my tally) | 2021ApJ...908...54W, 2018ApJ...856..118H, 2020ApJ...902..109B, 2019MNRAS.485.2092C, 2014ApJ...785..149S (600) |
| Upper-limit level | 3 sigma | 3-5 sigma | 7 (my tally of excerpts stating a stacked limit with its level) | 3 sigma: 2019MNRAS.485.2092C, 2018ApJ...860..103S, 2021ApJ...908...54W, 2020A&A...640A..27V, 2018ApJ...853..195W, 2026A&A...705A.198M; 5 sigma: 2018ApJ...856..118H |
| Stacked line detection rule | study-specific; validate on blank or mock stacks | peak >4 sigma and >=3 channels >3 sigma within the 2 sigma Gaussian width; reject peak <4 sigma or width <3 channels; S/N>3 in the central 600 km/s channel | 3 (plus 1 bare criterion) | 2018A&A...616A.100Y, 2021ApJ...908...46B, 2014ApJ...785..149S; 2015ApJ...811L...3T states only a "2 sigma detection criterion" |
| Random-stack repetitions | (one example) | 50 | 1 | 2014ApJ...780..115D |
| Empty positions stacked | (one example) | 100 | 1 | 2019A&A...630A..59B |
| Off-line or shuffled spectral windows | (examples) | 1000 off-line windows; 3000 channel shufflings | 2 | 2025MNRAS.541.4031D (1000), 2014ApJ...785..149S (3000) |
| Bootstrap resamplings (ALMA stacks) | 100-1000 | 100; 1000 | 2 | 2024A&A...688A..55M (100), 2026ApJ..1000..312Z (1000); 5000 is stated only for PACS in 2018ApJ...853..195W |
| Keplerian annulus width | 1/4 beam | 1/4 beam; 0.05"; half beam | 5 | 2024ApJ...965..147B, 2026A&A...705A.198M, 2025ApJ...984L..19Y, 2019ApJ...880...69Y, 2018A&A...616A.100Y |
| Keplerian grid (M*, PA, i, Vsys) | one study's grid, as an example | M* 0.1-3 Msun step 0.1; i 5-85 deg step 5; PA 0-355 deg step 5; Vsys 1.7-6.3 km/s step 0.1 | 1 | 2018A&A...616A.100Y |
| Protection radius when subtracting bright sources | 1" around each stacking position | (one example) | 1 | 2016MNRAS.462.1192L |
| Exclusion of stacking positions near bright sources | mask or drop | within 3" of ALMA primary targets (tested both ways); >3.5" from the five brightest detections; near >=4 sigma detections; detections masked | 4 | 2024A&A...688A..55M, 2016ApJ...833...68A, 2020A&A...633A.160C, 2020A&A...640A..27V |
| Primary-beam cut | drop low-PB area | pbcor<0.5 removed; PB coverage >75% | 2 | 2020A&A...633A.160C, 2020ApJ...892...66M |
| Stamp size | 20-30" square | 20"x20"; 30"x30" | 2 | 2020ApJ...892...66M (20", card section 4.2), 2020MNRAS.497.2771M (30") |
| Aperture or extraction region | (no common choice) | 0.5" diameter to 10" radius | 5 | 2016ApJ...833..195W (0.5" diameter, card), 2019A&A...631A..78S (2" integration area, convention not stated), 2017ApJ...834..135T (2.0" aperture, not stated), 2026A&A...705A.163H (4" aperture, best S/N, not stated), 2017MNRAS.466...49J (10" radius) |

## Software

Aggregate counts of software named in the matched steps (pack; a paper can name several):

| Software | Count | Used for |
|---|---|---|
| CASA | 13 (plus `imfit` 2, `tclean`, `split`, `concat`, `statwt`, `immoments` 1 each) | imaging stacks, uv concatenation, phase shifts, rescaling with `gencal`/`applycal` (2024A&A...688A..55M) |
| stacker / STACKER | 9 (plus pystacker 1) | uv-plane and image stacking of continuum (2020A&A...633A.160C, 2024A&A...688A..55M, 2018ApJ...861....7F, 2015ApJ...810..133I, 2020MNRAS.497.2771M) |
| GoFish | 7 | Keplerian shifted-and-stacked disk spectra and radial profiles (2024ApJ...965..147B, 2026A&A...705A.198M) |
| galfit | 7 | Sersic or Gaussian fits to stacked images (2018ApJ...861....7F, 2019MNRAS.485.2092C); some counts come from off-topic HST/JWST steps |
| GILDAS | 6 | `uv_fit` point-source fluxes, line stacks (2019MNRAS.485.2092C, 2017A&A...607L...5Q) |
| Line Stacker | 3 | 1D/3D [CII] stacks, rebinning, sub-sample search (2019A&A...631A..78S) |
| eddy, bettermoments | 3, 2 | velocity maps and per-annulus v_LOS for azimuthal stacking (2025ApJ...984L..19Y) |
| STACKARATOR | 2 | velocity-field spaxel stacking in nearby galaxies (2025MNRAS.541.4031D) |
| cstack | 2 | named in the aggregates; the excerpts do not show how it was used |
| dynesty, GAStimator, lmfit | 1, 1, 2 | fitting stacked lines (2025ApJ...985..194P, 2025MNRAS.541.4031D) |
| uvmultifit | 1 | uv-plane size fit as cross-check (2018ApJ...861....7F) |
| PyStacker, PyStructure | 1 each | resolved line-ratio stacks (2025ApJ...988..162D) |

Custom, unreleased stacking code is common: the cards flag it for 2018A&A...616A.100Y, 2020MNRAS.497.2771M,
2016MNRAS.462.1192L, and Line Stacker was "in prep" for 2019A&A...631A..78S. Recommendation: use a released tool
(stacker, GoFish, STACKARATOR) or publish your script, and record weights and positions.

## Pitfalls

- **Weighted means follow the high-weight sources.** "our stacked result can be biased toward the candidates
  with the highest weights" (2020A&A...633A.160C). Run equal-weight and weighted stacks and report both, as that
  paper (four schemes) and 2019A&A...631A..78S (three schemes) did.
- **Selecting a sub-sample on the stack you then test.** 2019A&A...631A..78S built a "max sub-sample" from
  10 000 random subsets and found the excess rose from 1.1-1.5 sigma (full sample, 3D) to 1.2-2.5 sigma; its own
  mocks without outflows gave a >2 sigma broad excess in 2-5% of straightforward stacks and a >0.4 sigma excess in
  14-17%. Treat a few-sigma broad wing as unconfirmed unless mocks, jackknife and random-sample stacks support it
  (2026ApJ..1000..312Z: <2% chance from random non-BAL stacks).
- **A statistically real broad wing can still have another physical cause.** 2019A&A...631A..78S assumed a single
  broad Gaussian, notes the broad emission could come from interacting galaxies, and cannot detect low-velocity
  outflows; 2019ApJ...887..107F notes faint continuum or satellites could mimic a broad wing; 2026ApJ..1000..312Z
  cannot separate AGN- from star-formation-driven outflows. Check for companions, test other profile shapes, and
  state the velocity range the data cover.
- **Lensed samples.** 2014ApJ...785..149S did not account for differential magnification in its template; it can
  distort stacked line ratios and the physical conditions inferred from them. State how magnification enters
  the weights (2020A&A...633A.160C ran a PB^2 x mu^2 scheme as one of four) and whether you correct for it.
- **Resolved emission in a peak or small aperture.** Aperture corrections that assume point sources
  (2016ApJ...833..195W; 2019MNRAS.485.2092C assumed a PSF response) underestimate extended flux; 2017ApJ...834..135T
  found residual flux outside the half-light radius. Sizes measured at SNR<10 are biased high
  (2017ApJ...844..123F). Bright-source subtraction can be incomplete on the shortest baselines
  (2016MNRAS.462.1192L).
- **Astrometric and positional errors smear the stack.** Correct offsets first (Step 2). A phase-centre
  rounding error may have dropped ~11 galaxies at primary-beam edges in 2019MNRAS.487.4648S.
- **Interferometric filtering.** Stacks inherit the missing short spacings of each input: 2019A&A...630A..59B
  cannot exclude more extended [CII] emission missed by the data.
- **Keplerian stacking depends on the geometry.** Mass can be overestimated for fluxes below ~400 mJy km/s and
  inclination is poorly constrained (2018A&A...616A.100Y); the enhancement drops inside the beam and needs an
  accurate Vk (2016ApJ...832..204Y); radial-profile errors may be underestimated inside the beam
  (2024A&A...689A..65R); line width at the inner radius is overestimated (2019ApJ...880...69Y).
- **One conversion for a mixed sample.** Common Tdust or template, fixed alpha_CO and a mean redshift turn a
  stacked flux into a mass only for a "typical" member; authors flag alpha_CO uncertainty of a factor >=2
  (2021ApJ...908...54W), template inaccuracy for outliers (2020A&A...643A...2B), and samples too small to separate
  trends (2019MNRAS.485.2092C, five galaxies).
- **Selection bias in the input catalogue.** Optical or NIR selection misses heavily obscured galaxies
  (2024A&A...688A..55M, 2017A&A...599A.134S, 2016ApJ...833..195W, 2018ApJ...853..195W); low-mass bins may be
  incomplete (2020A&A...633A.160C).
- **Settings papers leave out** (pack aggregate of "not stated" flags in the matched papers): CASA version 8,
  image and cell size 5, line-free channels and continuum subtraction 4 or more under several phrasings, flux
  calibrator and flux-scale uncertainty 4, exact stacking procedure and weights 2, stacking procedure details 2,
  exact bootstrap settings 1. Report all of these.

## Verification checks

Checks the papers ran (pack lines):

- **Null stacks are consistent with zero**: random-position stacks (2014ApJ...780..115D), empty positions with
  spurious S/N ~0.4 (2019A&A...630A..59B), blank-sky p>0.1 (2018ApJ...853..195W), 30 blank-field synthetic images
  give no detections (2018A&A...616A.100Y).
- **Stack the detected sources and recover their known fluxes**: CO-detected sources (2018ApJ...860..103S,
  2018ApJ...856..118H), 12 robust DSFGs at 39.1 sigma with equal weights (2020A&A...633A.160C), all SMGs giving
  4.2+-0.14 mJy and 0.4" consistent with the literature (2016MNRAS.462.1192L).
- **Injection tests**: inserted and stacked point sources to measure stacking bias (2016MNRAS.462.1192L);
  simulated clumpy sources (three 0.7 mJy clumps each) stacked the same way, recovered 2.3+-0.2 mJy vs 2.1 mJy
  input (2016MNRAS.462.1192L); artificial point sources of 0.005-0.2 mJy with no systematic bias
  (2016ApJ...833..195W, card); 700 noise realizations of model cubes (2021ApJ...908...46B); 10 000 noise-only and broad-component
  mocks (2019A&A...631A..78S).
- **Jackknife and leave-one-out**: no single galaxy drives the result (2019MNRAS.485.2092C); excluding one BAL
  quasar at a time (2026ApJ..1000..312Z); 1000 jackknife stacks without 5 sources change the mean luminosity by
  ~11% (2019A&A...630A..59B); broad-component parameters stay within 20% (2019A&A...631A..78S).
- **Alternative methods agree**: two independent stacking routines (2014ApJ...780..115D); moment-0, 3D and uv
  stacking compared (2020MNRAS.497.2771M, which picked moment-0 for highest 13CO S/N); central pixel vs 2D
  Gaussian (2024A&A...688A..55M); galfit vs uvmultifit (2018ApJ...861....7F); other continuum-subtraction and
  stacking variants (2020ApJ...905...85S); stacked vs summed 12CO flux (2025MNRAS.541.4031D).
- **Cut and parameter sensitivity**: DeltaMS<0 instead of -0.3 (2025ApJ...985..194P); with and without ALMA
  primary targets (2024A&A...688A..55M); mergers excluded (2020A&A...643A...2B); inclinations 1-11 deg and
  quadrant stacks (2025ApJ...984L..19Y); stricter BIC difference >10 (2025MNRAS.541.4031D).

What a careful referee adds (my recommendation, following the checks above): report the number of inputs per bin
and the expected sqrt(N) noise next to the measured stack noise; show equal-weight and weighted results; give the
null-stack distribution, not only its mean; show the stacked image or spectrum with the beam; and state whether
the significance includes population variance (bootstrap over sources) or only thermal noise; and list the
flux-calibration systematic separately (Step 5).

## Source cards

All 118 papers are listed in `references/sources.md`. The most informative for this technique:

- 2014ApJ...780..115D: image stacks, PB weights, mean and median, random-position noise, two routines.
- 2016MNRAS.462.1192L: uv stacking, bright-source subtraction, short-baseline flags, injection tests.
- 2020A&A...633A.160C: STACKER with four weighting schemes, selection cuts, weight bias caveat.
- 2024A&A...688A..55M: luminosity-rescaled uv stacks, bootstrap, primary-target test.
- 2020ApJ...892...66M: mass-threshold stacks, astrometric offset, PB cut, adaptive flux measurement.
- 2016ApJ...833..195W: NIR-selected image stacks, aperture correction, EBL.
- 2018ApJ...861....7F: uv-stacked morphology, galfit and uvmultifit.
- 2019MNRAS.485.2092C: uv_fit fluxes, weighted spectral and dust-map stacks, error rescaling, jackknife.
- 2018ApJ...860..103S: continuum and CO stacks of passive galaxies, detected-source validation.
- 2025ApJ...985..194P: inverse-variance CO stacks by main-sequence group, dynesty fit.
- 2019A&A...631A..78S: Line Stacker, weightings, sub-sample selection risks, mock false-positive rates.
- 2019A&A...630A..59B: variance-weighted [CII] stacks, empty-position and jackknife tests.
- 2026ApJ..1000..312Z: normalized [CII] stacks, bootstrap, jackknife, random-stack significance.
- 2014ApJ...785..149S: template spectrum, line-centred stacks, channel-shuffle false rate.
- 2016ApJ...832..204Y: the Keplerian velocity-aligned stacking method.
- 2018A&A...616A.100Y: S/N-maximizing grid search, detection rule, blank-field and model tests.
- 2021ApJ...908...46B: multi-molecule stacks, dynamical masses, 700 synthetic cubes.
- 2024ApJ...965..147B: GoFish annular stacks with r^2 weights.
- 2026A&A...705A.198M: stacking for gas-free debris discs, bootstrapped noise windows.
- 2025MNRAS.541.4031D: STACKARATOR velocity-field stacks, BIC model choice, off-line noise.
- 2025ApJ...984L..19Y: azimuthal stacking with eddy, geometry robustness.
- 2018AJ....156..164B: shift-and-sum on a predicted position, random-shift significance.
