# Review task: an ALMA agent skill against its evidence pack

You are reviewing a skill file (SKILL.md, plus an optional parameters table) that another model wrote from the
EVIDENCE PACK below. The pack is built from methods cards of published ALMA papers; every quote in it was
mechanically verified against the paper text. The skill will be given to research agents that analyse ALMA data,
so wrong defaults or misattributed practice cause real errors. You have no file access: everything you need is in
this message.

Check, in this order:

1. **Attribution.** Every number, range, default, software attribution and "papers do X" claim that cites
   bibcodes: does the pack support it for those bibcodes? Flag claims the pack contradicts, claims cited to a paper
   whose pack entry says something else, and counts that do not match the pack aggregates.
2. **Unsupported practice.** Statements presented as literature practice with no support in the pack. (General
   background marked as general practice is fine if it is correct.)
3. **Scientific correctness.** Wrong formulas, wrong units, wrong CASA task/parameter names or semantics, unsafe
   advice, or a recommendation that contradicts the evidence.
4. **Omissions.** Important pitfalls, assumptions or validation checks that are clearly present in the pack (for
   example in "Limitations the authors admit" or "Settings cards flag as needed but not stated") but missing from
   the skill.
5. **Usability.** Anything an agent would misread or could not act on.

Output format (Markdown, nothing else):

```
# Codex review: <slug>
VERDICT: CLEAN | FIX
## Findings
- SR-01 | high|medium|low | <attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- SR-02 | ...
## Notes
<at most 5 lines: overall quality, anything the writer should know>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (stacking) ===
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
  DSFGs (2014ApJ...785..149S).
- **Weak lines in a rotating disk**: shift spectra by the projected Keplerian velocity before summing
  (2016ApJ...832..204Y, 2018A&A...616A.100Y, 2021ApJ...908...46B, 2019ApJ...880...69Y, 2024ApJ...965..147B,
  2025ApJ...984L..19Y, 2026A&A...705A.198M).
- **Faint isotopologues inside resolved galaxies**: shift each spaxel by the 12CO velocity field and co-add
  (2025MNRAS.541.4031D with STACKARATOR; 2025ApJ...988..162D with PyStacker).
- **Many transitions of one species**: co-add maps or spectra of unblended lines with similar morphology
  (2019ApJ...871..112X, 2017A&A...607L...5Q, 2017A&A...601A...4A, 2017ApJ...843...27L, 2016ApJ...823L..10W,
  2019ApJ...877L..25M), or different molecules that share the same rotation (2021ApJ...908...46B).
- **A moving target with a predicted position**: shift images to the ephemeris position and sum
  (2018AJ....156..164B).

## When not to use

- **The sources are individually detected at useful S/N.** Measure each one; stack only the non-detections or use
  the detections to validate the stack (2018ApJ...860..103S, 2018ApJ...856..118H). Use `uv-plane-fitting` or
  `source-extraction-counts`.
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
   - Remove or mask bright unrelated sources: subtract the clean model of bright sources, excluding any within
     1" of a stacking position, from the visibilities (2016MNRAS.462.1192L, CASA 4.4, clean depth 1.8 mJy/beam,
     cell 0.2"); mask non-target continuum detections (2020A&A...643A...2B); mask detections before stacking 122
     non-detections (2020A&A...640A..27V); cut stamps from the residual map for undetected sources
     (2020ApJ...892...66M, card).
   - Handle the primary beam: keep only area with PB coverage >75% (2020ApJ...892...66M); stack non-PB-corrected
     maps and carry the PB in the weights (2014ApJ...780..115D scales stamps by PB attenuation then weights;
     2021ApJ...908...54W stacks non-PB-corrected channel maps).
   - For spectra: put every spectrum in the rest frame and on one channel grid (50 km/s, 2025ApJ...985..194P;
     60 km/s bins, 2026ApJ..1000..312Z), or rebin so each line FWHM spans the same number of channels
     (FWHM_min=270 km/s, 2019A&A...631A..78S). Drop channels with atmospheric transmission <0.5
     (2019A&A...630A..59B).
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
     For gas-poor disks, stack in both rotation directions (2026A&A...705A.198M).
   - e. **Velocity-field stacks inside galaxies.** Shift every 12CO-detected spaxel by the 12CO moment-1
     velocity and co-add, globally, in elliptical radial apertures, or by quadrant (2025MNRAS.541.4031D,
     STACKARATOR).
   - f. **Multi-transition and moving-target stacks.** Inverse-variance weights per transition
     (2019ApJ...871..112X); noise-weighted mean of cubes of different molecules (2021ApJ...908...46B); uv-domain
     concatenation of three lines after velocity regridding (2016ApJ...823L..10W). Shift to the predicted
     satellite position and sum (2018AJ....156..164B).

4. **Measure the stacked signal.** Goal: a flux that does not depend on an unchecked size assumption.
   - Unresolved continuum: peak or central pixel (2024A&A...688A..55M, 2D Gaussian as cross-check); small
     aperture with a dirty-beam aperture correction assuming point sources (2016ApJ...833..195W, 0.5" diameter,
     card). Point-source uv fits per galaxy then a weighted mean (2019MNRAS.485.2092C, GILDAS `uv_fit`).
   - Possibly resolved: aperture S/N>=5 then 2D Gaussian with free widths, else aperture flux
     (2020ApJ...892...66M); Sersic fit with galfit on the stacked image plus uvmultifit check
     (2018ApJ...861....7F); uv-domain Gaussian size (2016MNRAS.462.1192L). Compare peak and extended flux:
     2017ApJ...834..135T found 0.42 mJy extra within a 2.0" aperture.
   - Spectra: Gaussian fit with nested sampling and bootstrap channel errors (2025ApJ...985..194P, dynesty);
     single vs double Gaussian by BIC with MCMC (2025MNRAS.541.4031D, GAStimator); narrow plus broad Gaussian
     (2026ApJ..1000..312Z, 2019A&A...631A..78S). Integrate within twice the FWHM (2018A&A...616A.100Y), within
     the 1 sigma Gaussian width (2019ApJ...880...69Y, 2021ApJ...908...46B), or over V*+-5 sigma
     (2026A&A...705A.198M).

5. **Estimate the noise empirically.** Goal: an uncertainty that includes confusion and non-Gaussian noise.
   - Random positions: N random positions per sample, 50 iterations (2014ApJ...780..115D); 100 empty positions
     (2019A&A...630A..59B); blank-sky stacks and p-values (2018ApJ...853..195W); randomized galaxy positions give
     only non-detections (2020ApJ...892...66M, card); random shifts give 0.02% chance, 3.5 sigma
     (2018AJ....156..164B).
   - Off-line windows and shuffles: 1000 random off-line windows of the fitted FWZI (2025MNRAS.541.4031D);
     7 km/s noisy windows, bootstrapped (2026A&A...705A.198M); 3000 channel shufflings at a line-free frequency
     (2014ApJ...785..149S); rescale errors so Var(S/sigma)=1 in line-free channels (2019MNRAS.485.2092C).
   - Bootstrap over the sample, which adds population variance: 100 realizations (2024A&A...688A..55M), 1000
     (2026ApJ..1000..312Z), 5000 (2018ApJ...853..195W); also 2020A&A...643A...2B and 2017A&A...599A.134S.

6. **Convert to physical quantities and report limits.** Goal: a mean property with its assumptions explicit.
   - Upper limits are mostly 3 sigma (2019MNRAS.485.2092C, 2018ApJ...860..103S, 2021ApJ...908...54W,
     2020A&A...640A..27V, 2018ApJ...853..195W); 2018ApJ...856..118H used 5 sigma. State which.
   - The conversion carries assumptions that apply to the stack as a whole: one Tdust for all sources
     (2017A&A...599A.134S, 40 K; 2018ApJ...860..103S, 25 K with kappa_235GHz=0.42 cm2/g and GDR=100), a fixed
     alpha_CO (2020MNRAS.497.2771M, 4.6 and 0.8), the mean redshift of the stack (2021ApJ...908...54W, z=1.476).
     Use `dust-continuum-mass` and `gas-mass-co-conversion` for the formulas.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count, my tally of pack lines) | Examples |
|---|---|---|---|---|
| Spectral stack weights | inverse variance (1/sigma^2) | equal, 1/sigma^2, 1/S_peak | 7 (my tally) | 2025ApJ...985..194P, 2019A&A...630A..59B, 2014ApJ...785..149S, 2026ApJ..1000..312Z, 2019ApJ...871..112X, 2021ApJ...908...46B, 2019A&A...631A..78S |
| Continuum stack weights | PB-attenuation based | PB^2; PB^2 x F_UV^2; PB^2 x mu^2; equal | 3 (my tally) | 2014ApJ...780..115D, 2016MNRAS.462.1192L, 2020A&A...633A.160C |
| Mean vs median | weighted mean | mean and median both reported | 1 does both | 2014ApJ...780..115D |
| Stacked spectral channel | 50-60 km/s | 20-125 km/s | 4 | 2025ApJ...985..194P (50), 2026ApJ..1000..312Z (60), 2019A&A...631A..78S (60), 2020MNRAS.497.2771M (125 for 3D) |
| Collapsed width for line upper limits | 400 km/s | 400-800 km/s; mean FWZP | 4 | 2021ApJ...908...54W, 2018ApJ...856..118H, 2020ApJ...902..109B, 2019MNRAS.485.2092C |
| Upper-limit level | 3 sigma | 3-5 sigma | 6 | 2019MNRAS.485.2092C, 2018ApJ...860..103S, 2021ApJ...908...54W, 2018ApJ...856..118H (5) |
| Stacked line detection rule | peak >4 sigma and >=3 channels >3 sigma | central-channel S/N>3; 2 sigma | 4 | 2018A&A...616A.100Y, 2021ApJ...908...46B, 2014ApJ...785..149S, 2015ApJ...811L...3T (2 sigma) |
| Random-position iterations | 50-100 | 50-1000 | 3 | 2014ApJ...780..115D (50), 2019A&A...630A..59B (100), 2025MNRAS.541.4031D (1000 off-line) |
| Bootstrap resamplings | 1000 | 100-5000 | 3 | 2024A&A...688A..55M (100), 2026ApJ..1000..312Z (1000), 2018ApJ...853..195W (5000) |
| Keplerian annulus width | 1/4 beam | 1/4 beam; 0.05"; half beam | 5 | 2024ApJ...965..147B, 2026A&A...705A.198M, 2025ApJ...984L..19Y, 2019ApJ...880...69Y, 2018A&A...616A.100Y |
| Keplerian grid (M*, PA, i, Vsys) | M* 0.1-3 Msun step 0.1; i 5-85 deg step 5 | PA 0-355 deg step 5; Vsys step 0.1 km/s | 1 | 2018A&A...616A.100Y |
| Bright-source exclusion | mask or subtract detections | 1"; 3"; 3.5" from bright sources | 4 | 2016MNRAS.462.1192L, 2024A&A...688A..55M, 2016ApJ...833...68A, 2020A&A...640A..27V |
| Primary-beam cut | drop low-PB area | pbcor<0.5 removed; PB coverage >75% | 2 | 2020A&A...633A.160C, 2020ApJ...892...66M |
| Stamp / aperture | stamp 20-30" | aperture 0.5" to 10" | 6 | 2020MNRAS.497.2771M (30" stamps), 2016ApJ...833..195W (0.5"), 2019A&A...631A..78S (2"), 2017ApJ...834..135T (2"), 2026A&A...705A.163H (4", best S/N), 2017MNRAS.466...49J (10") |

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
- **Injection tests**: inserted point sources (2016MNRAS.462.1192L, recovered 2.3+-0.2 vs 2.1 mJy input in
  simulations); 700 noise realizations of model cubes (2021ApJ...908...46B); 10 000 noise-only and broad-component
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
the significance includes population variance (bootstrap over sources) or only thermal noise.

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

=== EVIDENCE PACK (stacking) ===
# Evidence pack: Stacking undetected sources (image or uv plane) (`stacking`)

Scope: stacking in image or uv space, weighting and uncertainty estimation

Built from 118 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2013-2026.
Matcher (regex over analysis steps): `\bstack`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- high_z_galaxies: 72
- protoplanetary_disks: 28
- astrochemistry: 23
- nearby_galaxies: 18
- star_formation: 14
- agn_and_quasars: 13
- galaxy_clusters_and_sz: 12
- evolved_stars: 2
- solar_system: 2
- cosmology: 2
- milky_way_ism: 2
- stellar_physics: 1
- debris_disks: 1
- exoplanets: 1

### Software named in the matched steps
- casa: 13
- stacker: 9
- galfit: 7
- gofish: 7
- gildas: 6
- line stacker: 3
- eddy: 3
- stackarator: 2
- casa imfit: 2
- bettermoments: 2
- galight: 2
- lmfit: 2
- sextractor: 2
- cstack: 2
- dynesty: 1
- gastimator: 1
- custom stacking code: 1
- casa immoments: 1
- casa split: 1
- casa tclean: 1
- madex: 1
- casa 4.4: 1
- casa sm: 1
- eddy.linecube: 1
- pystacker: 1
- pystructure: 1
- lenstronomy: 1
- l.a.cosmic: 1
- uvmultifit: 1
- lime: 1
- q3dfit: 1
- concat: 1
- visible: 1
- casa cvel2: 1
- casa concat: 1
- casa statwt: 1
- art2: 1
- cloudy: 1
- gadget-3: 1
- gildas/class: 1

### Fitting methods (most common phrasings)
- Linear fit between literature median and stacked limit: 1
- S/N-maximization grid search; Gaussian fits to stacked spectra: 1
- chi2 of templates; MBB with beta=1.8 shown for information: 1
- Uniform prior on amplitude, Gaussian priors on centroid (sigma=63.7 km/s at 0) and FWHM (300±31 LM, 365±21 HM-aMS, 407±…: 1
- Gaussian fits to line peaks: 1
- MCMC gaussian fits, model selection by BIC: 1
- Grid search; Gaussian fit to aligned spectrum, S/N of Gaussian-weighted integrated intensity: 1
- 2D Gaussian: 1
- 1D Gaussian for line width then 2D Gaussian in central channel (3D): 1
- two-Gaussian model; uncertainties from bootstrap realizations; optimizer not stated: 1
- One- and two-component Gaussian fits; chi2 improvement and excess significance from residuals summed within ±800 km/s: 1
- Abundance profile adjusted by hand/iteratively; high-S/N profile fit mandatory, low-S/N reasonable: 1
- MCMC orbit fit: 1
- Gaussian fit to stacked spectrum for centroid/width: 1
- chi2 minimization, weights sigma^-2: 1
- S/N maximization of velocity-aligned stacked spectra; uncertainty from data noise only: 1
- Gaussian fits: 1
- 2D Gaussian fits as cross-check: 1
- galight MCMC: 1
- Single linear fit to the linear PV structures in methanol and deuterated methanol: 1
- galfit chi-square; errors by bootstrap: 1
- Best by-eye fit: 1
- [C II] fit with LMFIT in same masks: 1
- three Sersic kernel: 1
- If S/N>=5 in 0.6xFWHM aperture, 2D Gaussian fit with free amplitude and widths; else total flux in 1.0xFWHM aperture; n…: 1
- GALFIT Levenberg–Marquardt least squares: 1
- Gaussian Process via celerite; radial profile also modelled as GP: 1
- 1 sigma interval of posterior distribution: 1
- Linear fit to detected stacks for IRX-Mstar: 1
- SED chi2 fit; reduced chi2 1.3: 1
- Function fit to median offsets in S/N bins with sqrt(2) radial correction: 1
- Galfit PSF fits in 5x5 arcsec box; Sersic index fixed to 1 in comparison fits: 1
- chi2 over template/amplitude grid, flat priors: 1
- Levenberg-Marquardt; uncertainties from LM procedure: 1
- dA_UV/dbeta constrained by comparing stacks to IRX=10^{0.4(dA/dbeta)(beta+2.23)}-1: 1
- four Gaussians for Halpha and [NII]: 1

### Validation checks used
- Jackknife; O3N2 comparison: 1
- MCMC redshift displacement and linewidth resampling show negligible effect: 1
- CASA, GILDAS and GALFIT fluxes previously verified consistent: 1
- Jackknife on V580: 1
- Tested on 30 blank-field synthetic images (no detections), 3 bright sources vs PV diagram analysis, and 24 model disks: 1
- Compared with Ansdell16 fluxes: 1
- Two independent stacking routines gave consistent results: 1
- Random-stack mean consistent with zero: 1
- Compared with dust temperatures from other studies: 1
- ALESS medians >4-sigma outliers vs field bootstrap: 1
- Bootstrap errors: 1
- Bootstrap errors; mergers excluded as test: 1
- results insensitive to using DeltaMS<0 as the bMS cut: 1
- JvM correction 1% flux difference; radii varied to maximise S/N: 1
- Recovered sample-average line flux by stacking only CO-detected sources: 1
- Compared stacked 12CO flux with Brown2021 summed flux: 1
- Tested stricter BIC difference >10; results unchanged: 1
- Compared masses from individual lines; 80% agree within 1 sigma: 1
- Synthetic DALI cubes; 700 noise realisations: 1
- Monte Carlo systematic errors; comparison with 3D and uv stacking: 1
- Moment-0 chosen as it gives highest 13CO SNR: 1
- image-plane cube stacking gives 4.48 sigma for BAL; random 5-quasar non-BAL stacks give <2% chance of S/N>=4.4: 1
- jackknife, FWHM split, velocity-normalized stacks, M1450 split: 1
- Mock stacking without outflow: >2 sigma broad excess in 2-5% of straightforward stacks, none without noise: 1
- Noise-only and broad-component mock stacks (10 000 iterations): 1
- Leave-one-out stacks; min sub-sample shows no outflow; broad parameters stay within 20%: 1
- 2 mm maps show the same hollow shell: 1
- Random-shift experiment gives 3.5 sigma significance: 1
- Uncertainties by bootstrapping in noise-only regions: 1
- Stellar velocity of HD 121617 compared with independent measurement, consistent within 3 sigma: 1
- Blank-sky stacks and p-values: 1
- Consistency of maps across Eu range: 1
- Compared to mean-stacked Herschel 160 um results: 1
- Bias test with inserted point sources: 1
- Stacked all SMGs: Gaussian fit gives 4.2±0.14 mJy and 0.4±0.06 arcsec, consistent with Simpson et al. 2015: 1
- Compared to Tacconi et al. 2013 main sequence: 1
- Recovered flux 2.3±0.2 mJy vs input 2.1 mJy: 1
- Compared with previous 1.8 Msun from 13CO/C18O PV diagram; added a few percent for emitting height: 1
- Imfit ellipticity bias tested by Monte Carlo: 1
- Binomial statistics for the detection rate; v50 alternative gives 7/11: 1

### Key parameters and settings (bibcode: value)
- 2019MNRAS.485.2092C: [NII] ratio fixed to 3.05; 1000 Monte Carlo stacked spectra
- 2019MNRAS.485.2092C: Stack velocity width 753±22 km/s; errors scaled so Var(S/sigma)=1 in line-free channels
- 2019MNRAS.485.2092C: <U>=22; L_IR/Md factor 125; 0.15 dex systematic
- 2019MNRAS.485.2092C: Metallicities normalised to MW-mass z~0 galaxy (Mstar=5.7e10)
- 2018A&A...616A.100Y: M* 0.1-3 Msun (0.1 steps); PA 0-355 deg (5); i 5-85 deg (5); Vsys 1.7-6.3 km/s (0.1)
- 2018A&A...616A.100Y: detection: peak >4 sigma and >=3 channels above 3 sigma within 2 sigma Gaussian width
- 2018A&A...616A.100Y: C18O detection above 4 sigma; 20% systematic flux uncertainty
- 2014ApJ...780..115D: flux cuts of 3.6, 1.8, 1.2 mJy; z>1 subsample; smoothing to 1.6'' circular beam test
- 2014ApJ...780..115D: T_dust=12-60 K, beta=1.4-2.0 range
- 2025ApJ...985..194P: LM: logM<10; HM-aMS: logM>10, DeltaMS>-0.3; HM-bMS: logM>10, DeltaMS<-0.3
- 2025ApJ...985..194P: Priors: centroid in (-300,300) km/s, amplitude in (0,1.5) mJy, FWHM in (0.01,500) km/s
- 2024ApJ...965..147B: Annulus width 1/4 beam FWHM (~80 mas); weights proportional to r^2; centre offset (-52, -155) mas
- 2018ApJ...860..103S: Dust-based M_H2: kappa_235GHz=0.42 cm2/g, Tdust=25 K, GDR=100
- 2021ApJ...908...46B: initial R = 1 arcsec, iterate until disk radius (95% flux) changes <10%; reject peak S/N <4 sigma or width <3 channels
- 2020MNRAS.497.2771M: 12CO line widths measured at 20 km/s channels
- 2026ApJ..1000..312Z: 5 BAL and 11 non-BAL spectra; J0056+2241 excluded
- 2019ApJ...877L..25M: M_in = 12 Msun; inclination 8 deg; flaring angle ~35 deg
- 2019A&A...631A..78S: FWHM_min = 270 km/s; mean stacked channel width 60 km/s
- 2019A&A...631A..78S: 3-D spectra extracted over 2" region
- 2018ApJ...853..195W: 5000 bootstrap resamplings for PACS
- 2016MNRAS.462.1192L: clean depth 1.8 mJy/beam, cell 0.2 arcsec
- 2016MNRAS.462.1192L: flag baselines <18.2 m (sBzK, DRG) and <21 m (K20, ERO)
- 2019ApJ...880...69Y: free parameters M_star, V_sys; PA 138 deg, i 47 deg fixed
- 2019ApJ...880...69Y: radial bin width 0.05"; innermost radius = beam 0.1" (14 au)
- 2024A&A...688A..55M: SED template of Bethermin et al. 2017; gencal and applycal; three mass bins
- 2025ApJ...984L..19Y: annulus width 0.05"; i = 6.0 deg fixed
- 2025ApJ...988..162D: 5% flux calibration uncertainty included in Gaussian error propagation
- 2021ApJ...908...54W: mean z=1.476; 400 km/s bins
- 2025A&A...700A.285W: uniform priors 0.01''<Reff<4.0'', 0.3<n<9; innermost 0.2'' masked
- 2019A&A...630A..59B: n=48; channels with atmospheric transmission <0.5 excluded
- 2018ApJ...861....7F: sky fixed at 0; center fixed at image center
- 2018ApJ...861....7F: dt = depletion time (~640 and 210 Myr) or ~1.0 Gyr
- 2016ApJ...823L..10W: layers z/r<=0.1, 0.1-0.2, 0.2-0.3
- 2014ApJ...785..149S: 500 km/s grid; 600 km/s line channels
- 2020A&A...633A.160C: 5 beta bins, 9 mass bins, 3 z bins
- 2026ApJ..1000..308W: [O II] doublet ratio fixed to unity; [O III] and [N II] doublets fixed to 1/3
- 2024A&A...689A..65R: Filter mask outer radius 1 arcsec (218 GHz) and 2 arcsec (244 GHz)
- 2026A&A...705A.163H: 4 arcsec aperture chosen as best SNR
- 2018ApJ...856...14L: robust 0.5, taper 0.03 arcsec, 0.848 km/s channels
- 2016ApJ...832..204Y: Radial ranges R<300 AU (DCO+, H2CO), R<200 AU (DCN), 100<R<300 AU (N2D+)
- 2020ApJ...892...66M: Offset dRA=+0.076", dDec=-0.279"; PB coverage >75% (2.27 arcmin^2)
- 2020ApJ...892...66M: Redshift bins 0.3-0.6, 0.6-1.0, 1.0-1.6, 1.6-2.3, 2.3-3.2; mass thresholds from 1e11 down in 0.5 dex steps
- 2025ApJ...988..135M: F150W position angle tied to F444W; sources <26 mag within 3'' fit simultaneously
- 2017MNRAS.466...49J: 10" radius aperture for ALMA galaxies; 50" for M51
- 2016ApJ...833..195W: 2D Gaussian fit of stacked m3.6<23 image gave FWHM 0.76'' x 0.43''
- 2018ApJ...868..113T: three cases: flared, thin, flared without continuum subtraction
- 2020ApJ...902..109B: channel width 700 km/s (z~1.2), 800 km/s (z~2.5)
- 2019MNRAS.487.4648S: photon index Gamma=1.7; bolometric correction 15; efficiency 0.1
- 2020ApJS..247...61F: Requires z_IS+wind from at least three absorption lines and no -99 flag
- 2018MNRAS.473.1909G: Parameter ranges in Table 2
- 2015ApJ...811L...3T: 2 sigma detection criterion
- 2017A&A...599A.134S: IR8=8; bootstrap uncertainties
- 2017ApJ...844..123F: Sigma_SMG = 92 deg^-2, N_QSO = 1,100
- 2017MNRAS.469.4683C: Assumed clump line FWHM 100 km/s; mean clump FWHM 0.18 arcsec for stack
- 2018A&A...617A..28S: i = -34 deg, PA = 27 deg, d = 140 pc, M* = 0.55 Msun
- 2016ApJ...833...68A: M*>1e9 Msun, z<4, F850LP and F160W <27.5 AB, within/above main sequence with 0.5 dex scatter, >3.5'' from five brightest detections
- 2017ApJ...842L..21N: 105 templates × 10^4 amplitudes (0–100)
- 2019ApJ...876L..13S: Ring 0.8'' to 2''
- 2018ApJ...853...24U: Galactic NH = 8.8e19 cm^-2; Gamma fixed 1.9 if apparent Gamma<1.9
- 2016ApJ...819...82S: two most massive galaxies excluded
- 2019MNRAS.490.4956G: compact Reff fixed to 0.10''; extended Reff ~0.5''
- 2019ApJ...879...54L: segmentation threshold 1.5-3 times background rms
- 2017ApJ...834..135T: S_extra = 0.42 mJy within 2.0" aperture, 4.3 sigma


### Assumptions (bibcode: value)
- 2019MNRAS.485.2092C: Galaxies unresolved (PSF response)
- 2019MNRAS.485.2092C: Dust temperature as in z=2 MS template
- 2019MNRAS.485.2092C: Gas dominated by molecular gas at z=2
- 2018A&A...616A.100Y: geometrically thin Keplerian disk; stellar position at continuum center; distances 150/200 pc
- 2018A&A...616A.100Y: 13CO and C18O trace the same regions
- 2014ApJ...780..115D: all maps have same depth within ~20%
- 2014ApJ...780..115D: maps are mostly source-free
- 2014ApJ...780..115D: Chabrier IMF
- 2020A&A...643A...2B: Bethermin2017 template with no evolution above z~4 (<U>=50)
- 2020A&A...643A...2B: kappa_IR=1.02e-10, kappa_FUV=1.47e-10 Msun/yr/Lsun (Chabrier IMF)
- 2025ApJ...985..194P: SFMS scatter 0.3 dex
- 2024ApJ...965..147B: 13CCH radial profile follows C2H
- 2021ApJ...908...46B: Different molecules follow same Keplerian rotation; scale-height effect small (<3%)
- 2021ApJ...908...46B: Geometrically thin disk
- 2020MNRAS.497.2771M: LCDM H0=70, OmegaM=0.3, OmegaL=0.7; Chabrier IMF; alpha_CO 4.6 (B,D) and 0.8 (mergers)
- 2019ApJ...877L..25M: axisymmetric counterclockwise rotation, no outflow contribution
- 2017A&A...607L...5Q: LTE (Tex=TK); spherical emission; no IR pumping
- 2026A&A...705A.198M: Keplerian rotation, CO co-located with dust
- 2026A&A...705A.198M: LTE with Tex equal to peak brightness temperature; tau12CO=77 from ISM 12C/13C
- 2016MNRAS.462.1192L: Chabrier IMF; L_IR 8-1000 micron
- 2019ApJ...880...69Y: geometrically thin disk
- 2019ApJ...880...69Y: (3-2) and (1-0) trace the same volume; ratio constant within each bin
- 2015ApJ...810..133I: Average ALESS SMG template valid at z>3 (Td=32 K)
- 2020ApJ...905...85S: systemic redshift from [CII] (5 sources) or S/N-weighted stacked CO lines
- 2025ApJ...984L..19Y: Line wings identical along azimuth
- 2018ApJ...861....7F: constant SFR, no radial motions of stars
- 2016ApJ...823L..10W: LTE; Kama et al. disk structure
- 2026ApJ..1000..308W: Case B Halpha/Hbeta=2.86, Calzetti curve, f=0.56
- 2019ApJ...887..107F: z=6.01 average, 1''=5.7 kpc
- 2016ApJ...832..204Y: Geometrically thin disk, Keplerian rotation
- 2015Natur.522..455C: Meurer relation typical of z<3; SMC-like dust model
- 2016ApJ...833..195W: Sources unresolved for aperture correction
- 2016ApJ...833..195W: Optically faint population is 41% of faint-end EBL
- 2014ApJ...783...84S: alpha850 = 1.0e20 erg/s/Hz/Msun, beta=1.8, Td=25 K
- 2024RAA....24g5017M: Inclination 46.7, PA 133.3, M*=2 Msun, d=101 pc
- 2019A&A...623A..66B: same conversion factor as in Observations
- 2019MNRAS.487.4648S: z=2.5, Td=35 K, beta=1.5
- 2019A&A...624L...7V: inclination i~5 deg
- 2014ApJ...788..125S: M_H distribution not bimodal; undetected sources lie at z>2.5
- 2018MNRAS.473.1909G: One satellite per beam; halo occupation model
- 2024ApJ...961..120C: FIR-radio correlation gives S2.2 ≈ 12 uJy for S850 = 5 mJy at z=4.3
- 2017A&A...599A.134S: Single T_dust=40 K for all galaxies; Kennicutt 1998 SFR conversion; Salpeter IMF
- 2017ApJ...844..123F: Poisson distribution of random positions
- 2018A&A...620A.152F: sources point-like in 0.60 arcsec mosaic
- 2017ApJ...844...99L: C18O has same velocity range as 13CO
- 2017ApJ...842L..21N: Chabrier IMF
- 2017ApJ...834..135T: residual flux originates outside the half-light radius
- 2019ApJ...881...63N: Same FWHM as [CII] for all lines
- 2018A&A...618A..85S: T_dust ~ 40 K at z~3.5


### Limitations the authors admit
- 2019MNRAS.485.2092C: Gas masses rely on assumed MS SFE; effect of MS offset cannot be dissected with five galaxies
- 2018A&A...616A.100Y: Stellar mass can be overestimated for fluxes ≲400 mJy km/s; inclination poorly constrained
- 2014ApJ...780..115D: Photometric redshift uncertainties large; physical association flag may be a by-product of similar redshift distributions
- 2020A&A...643A...2B: Stacked-SED sample selection imperfect; conversion may be inaccurate for outliers
- 2025ApJ...985..194P: T18 is not calibrated below the SFMS; limited metallicity info; 6 of 10 HM-bMS CO-undetected galaxies have SFRs constrained only by HerMES upper limits
- 2024ApJ...965..147B: Models do not fully match observations; CO enrichment only 50 vs 20
- 2018ApJ...860..103S: Small sample of 8; alpha_CO systematic uncertainty ~50%; SFR from 24um may be overestimated up to ~2x
- 2025MNRAS.541.4031D: Small comparison samples and degeneracy between optical depth and abundance
- 2021ApJ...908...46B: Accuracy limited by S/N; high-mass bin has only six stars; highly inclined disks may be overestimated
- 2020MNRAS.497.2771M: Optical depth not accounted; 12CO/13CO luminosity ratios are lower limits to abundance ratios; degeneracy between starburst age and top-heavy IMF
- 2026ApJ..1000..312Z: Cannot disentangle AGN- vs star formation-driven outflows
- 2019ApJ...877L..25M: Beta uncertainty dominates Q; kinematic model not finely fitted; larger-scale envelope resolved out
- 2019A&A...631A..78S: Assumes a single broad Gaussian outflow profile; broad emission could be from interacting galaxies; low-velocity outflows not detectable
- 2017A&A...607L...5Q: LTE assumption may overestimate NaCN abundance; IR pumping not considered
- 2018AJ....156..164B: Dysnomia detection is weak and needs robust detection at multiple locations
- 2026A&A...705A.198M: Optically thick masses are lower limits; inner radii are upper limits; degeneracy thick/thin needs radiative transfer
- 2018ApJ...853..195W: Optical selection of members may bias the star-forming census; small samples of CO detections.
- 2019ApJ...871..112X: AcA morphology cannot be accurately determined due to few transitions and spatial contamination
- 2019ApJ...871..112X: Spectral simulation parameters chosen subjectively
- 2015MNRAS.453L..83M: Log-normal is not a literal description of the true AGN distribution
- 2021A&A...652A..98G: Common T_dust adopted for all sources; mass estimates depend on assumed conversion factors
- 2021A&A...652A..98G: Spectral index maps only possible for 3 sources
- 2021A&A...652A..98G: Small-number statistics for orientation and correlations
- 2016MNRAS.462.1192L: GEMS z-band less deep, possibly underestimating stellar sizes; bright source subtraction incomplete on shortest baselines
- 2019ApJ...880...69Y: Spiral velocities depend on the assumed mid-plane location and conserved angular momentum
- 2019ApJ...880...69Y: Inner-radius line width overestimated, so column density, Tex and tau at the inner radius may be underestimated
- 2015ApJ...810..133I: Large Sigma_SFR uncertainties for ~0.1" sources; only 13 sources; redshifts mostly lower limits
- 2020ApJ...905...85S: Limited ALMA bandwidth prevents detection of redshifted P Cygni emission and caps vmax
- 2020ApJ...905...85S: Conservative classification is S/N dependent and may exclude weak outflows
- 2024A&A...688A..55M: Sample may miss optically-dark heavily attenuated galaxies; ALMA primary targets bias the MS normalization
- 2025ApJ...984L..19Y: CO/H2 ratio uncertain; absolute gas surface density scales as X_CO^-0.5
- 2025ApJ...984L..19Y: Dust opacity model uncertainty affects gas-to-dust ratio; limited spatial resolution
- 2018ApJ...856..118H: Gas mass may be overestimated by ~1.5 if cluster galaxies are more metal-rich
- 2018ApJ...856..118H: Patchy Band 7 coverage so number density is a lower limit
- 2025ApJ...988..162D: Small sample; individual outliers can affect galaxy-to-galaxy trends
- 2025ApJ...988..162D: Metallicity covers only ~0.25 dex and 8 galaxies
- 2020A&A...640A..27V: Stellar mass differences and binarity cannot be accounted for in the comparison
- 2020A&A...640A..27V: Kaplan-Meier assumption of nondetection independence not met at low masses
- 2021ApJ...908...54W: Mostly upper limits on M_H2 and SFR preclude robust depletion time measurement
- 2021ApJ...908...54W: alpha_CO uncertainty of factor >=2
- 2025A&A...700A.285W: Torque method unvalidated by simulations, configuration likely unstable
- 2025A&A...700A.285W: Mass of young component is poorly constrained from single UV band; closed-box and alpha_CO assumptions
- 2017ApJ...843...27L: Tex is poorly constrained because data points are scattered at low S/N; may be underestimated by factor ~2
- 2017ApJ...843...27L: Disk is optically thick in dust so molecules near the midplane cannot be probed
- 2019A&A...630A..59B: Interferometric data may miss extended diffuse emission; stacking dilutes orientations
- 2017A&A...601A...4A: Spherical isotropic model cannot reproduce arcs; comparison only first order; IR pumping uncertain for C4H, C6H, C3N
- 2017ApJ...839L..15G: Single-wavelength measurement prevents fitting eta
- 2018ApJ...861....7F: Cannot distinguish n~1 vs 4 beyond r>0.4"
- 2016ApJ...823L..10W: Low S/N precludes detailed modeling; vertical location unconstrained
- 2014ApJ...785..149S: Single-component modelling of a heterogeneous sample; no single model fits (chi2 min 10.4 for 3 dof); degeneracies remain; differential magnification not accounted
- 2020A&A...633A.160C: Stellar masses below ~10^8.5 Msun likely incomplete; selection biases at low mass
- 2020A&A...633A.160C: Stacked values biased toward high-weight sources
- 2026ApJ..1000..308W: Small sample; results to be treated with caution
- 2024A&A...689A..65R: Radial profile uncertainties may be underestimated inside the beam
- 2019ApJ...874...53B: Large stellar mass uncertainties reduce significance of f_gas trend; merger fraction differences not significant
- 2026A&A...705A.163H: Fixed alpha_CO makes H2 limits uncertain; CO-to-H2 uncertainty may dominate
- 2026A&A...705A.163H: Comparison samples heterogeneous with different selection effects
- 2021A&A...645A.145G: Moderate resolution and symmetry assumption limit z/r accuracy; optical thinness uncertain
- 2020MNRAS.495.3840M: alpha_CO may be a factor of a few lower in the bar, so Sigma_mol could be overestimated
- 2020MNRAS.495.3840M: SFR below 1e-3 Msun/yr/kpc2 should be considered upper limits
- 2024ApJ...970....9B: The BAL gas density cannot be constrained, so the radius and energetics span wide ranges
- 2024ApJ...970....9B: The triangle-shaped blueshifted region may be a tidal feature
- 2018ApJ...856...14L: PV ellipses are poorly defined and eye-fitted; southern kinematics not fitted; decrease in specific angular momentum is uncertain.
- 2019ApJ...887..107F: Faint AGN or past AGN activity cannot be ruled out; faint continuum or satellites could mimic the broad wing
- 2016ApJ...832..204Y: Enhancement is lower at radii smaller than the beam, and depends on accurate Vk
- 2015Natur.522..455C: Dynamical masses very uncertain due to low spatial resolution
- 2020ApJ...892...66M: Pencil-beam survey affected by cosmic variance (~42-58%)
- 2020ApJ...892...66M: Dust-based gas may be biased against atomic phase; low-metallicity GDR relation uncertain
- 2025ApJ...988..135M: Visual merger classifications are subjective and may miss minor mergers.
- 2025ApJ...988..135M: Stellar masses depend on the assumed attenuation curve (~0.4 dex).
- 2026ApJ..1003...64Y: T and N degenerate; mostly optically thick; only lower limits; low S/N
- 2017MNRAS.466...49J: 12C/13C ratio uncertain by factor ~2
- 2024ApJ...966..228R: Small number of galaxies with individual metallicities limits environment comparison
- 2020ApJ...894...74B: Cloud contamination and low S/N limit Keplerian modeling
- 2020ApJ...894...74B: Individual source distances uncertain; dynamical mass scales linearly with distance
- 2016ApJ...833..195W: Low S/N prevents meaningful size constraint; EBL values are upper limits; stacked sample misses optically faint sources
- 2018ApJ...868..113T: Resolution (~29 au) leaves velocity features unresolved, underestimating depth
- 2018ApJ...868..113T: Cannot disentangle pressure gradient from stellar mass; pressure scaling depends on assumed density
- 2014ApJ...783...84S: Pathfinder, small samples, only most massive galaxies; results preliminary
- 2020ApJ...902..109B: PDR results only qualitative; small sample; selection effects cannot be fully excluded
- 2026A&A...706A...9Z: Small sample from a single protocluster; tentative conclusions
- 2024RAA....24g5017M: Cannot determine best-fit C/O due to observational limitations
- 2019A&A...623A..66B: FUV resolution of 100 pc prevents knowing radiation field per cloud
- 2025ApJ...995L..63L: delta_DGR concerns H2 only, ignoring atomic HI
- 2025ApJ...995L..63L: Mdust uncertain due to assumed Tdust and unknown AGN presence
- 2019MNRAS.487.4648S: Phase-centre rounding error may have missed ~11 galaxies at primary beam edges
- 2019A&A...624L...7V: Continuum polarisation low S/N and no other wavelengths, so nature is beyond scope
- 2014ApJ...788..125S: Stellar masses have systematic uncertainties up to 5x because SFHs are unconstrained
- 2020ApJS..247...61F: Spitzer blending can overestimate stellar masses; about one-third have contaminated Spitzer photometry
- 2020ApJS..247...61F: f-factor is the largest uncertainty in the Halpha measurement
- 2025ApJS..278...45F: 1-2 sources may be spurious; no completeness correction for IRLF; z>9 detections marginal
- 2025ApJ...989....3D: Radii are image-plane and not beam-deconvolved, so upper limits for unresolved disks
- 2025ApJ...989....3D: Gas mass uncertainties assigned manually from sparse model tracks
- 2017ApJ...836L..29J: Nucleosynthesis not a general explanation given the Milky Way 12C/13C trend
- 2018MNRAS.473.1909G: ALMA data quality insufficient for individual line profile analysis
- 2018MNRAS.473.1909G: Stack of 9 galaxies compared with a single simulated galaxy
- 2018ApJ...859...21A: Disks with measured radii are a small sample biased to the highest-mass disks
- 2018ApJ...859...21A: Models lack kinematics and observational noise
- 2015ApJ...811L...3T: Gas masses depend on dust opacity, dust-to-gas ratio and temperature assumptions
- 2020MNRAS.491.4724F: IR SED shape/dust temperature could change slope; low-mass stacks only upper limits
- 2024ApJ...961..120C: Radio resolution cannot identify which of B, C, G hosts the AGN; spectral index from only two points plus limits
- 2024ApJ...961..120C: 5 arcsec ATCA-ASKAP offset unexplained
- 2026A&A...705L..14D: Model parameters may be degenerate, e.g. p and h
- 2017A&A...599A.134S: Sample likely biased against heavily obscured H-dropout galaxies
- 2019MNRAS.482..698C: Fluxes should be taken with caution because of mixed photometry methods; 10% calibration uncertainty
- 2019MNRAS.482..698C: Dust masses may be underestimated (optically thick) or overestimated (higher temperature)
- 2019MNRAS.482..698C: Sample B not observed successfully; sample incomplete
- 2013ApJ...768...91H: Some reliability estimates are lower limits; several maps are poor quality due to low elevation observations.
- 2020ApJ...901...74T: Half-mass radius may be overestimated due to dust extinction; JWST 3-4 um needed.
- 2020ApJ...901...74T: Sample is rest-optically selected; optically dark galaxies may be missed.
- 2025ApJ...994....4A: Small sample, N2 selection bias toward high metallicity and high gas fraction
- 2025ApJ...994....4A: Metallicity calibration differs from that of the FMR
- 2017ApJ...844..123F: Redshifts of non-QSO SMGs unknown (assumed 2.5), making their results less reliable
- 2017ApJ...844..123F: Size measurements at SNR<10 are biased high
- 2017ApJ...844..123F: Duty cycle is an upper limit since no BH accretion assumed in SMGs without QSOs
- 2017AJ....153..240A: Many upper limits, uncertain stellar properties; gas masses could be underestimated by carbon depletion
- 2014MNRAS.442..577T: Small number of SMGs per age bin makes correlations weak; upper-limit spectral indices boost L1.4GHz and lower q_IR
- 2021A&A...652A..30S: ALMA data not deep enough to confirm or reject 39% of observed candidates; SFR depends on IR template
- 2024A&A...692A.215C: Scatter in r31 and r41 relations adds systematic errors
- 2018MNRAS.481.1631B: L_FIR depends on assumed dust temperature and SED from a single 1.3 mm point; beta errors are large

### Settings cards flag as needed but not stated
- casa version: 8
- image size and cell size: 5
- line-free channels and continuum subtraction method: 4
- line-free channels for continuum subtraction: 4
- flux calibrator and flux scale uncertainty: 4
- casa/pipeline version: 3
- line-free channels used for continuum subtraction: 3
- self-calibration solution intervals: 3
- casa version and calibration details: 3
- continuum subtraction and line-free channels: 2
- line-free channel ranges per source: 2
- flux calibrators and flux-scale uncertainty: 2
- exact stacking procedure and weights: 2
- primary-beam correction details: 2
- flux calibrators and flux scale uncertainty: 2
- image size and cell size for tclean: 2
- continuum subtraction method and line-free channels: 2
- stacking procedure details: 2
- clean threshold, cell and image size: 2
- calibration details, casa version, imaging parameters (weighting, cleaning) for alma/vla data (defe…: 1
- spectral channel widths and line-free channel selection: 1
- exact sfe prescription parameters and sargent 2014 equation 5 values: 1
- gildas uv_fit settings and neighbour source models: 1
- galfit setup for 870um mosaic: 1
- code for the stacking/alignment and s/n search (not released): 1
- exact clean parameters (image size, cell, threshold, masks): 1
- exact outlier-trimming rule for s/n distribution: 1
- model-grid details for the luminosity-weighted gas mass averaging: 1
- dust mass conversion details (taken from ansdell16/miotello17): 1
- casa version and calibration details (in hodge et al. 2013): 1
- calibrated aless image products/primary beam models used: 1
- exact positions of pointings and catalog cross-match details: 1
- fitting method/priors for the modified blackbody and how spire+344 ghz points were weighted: 1
- redshifts used for each galaxy in sed fits: 1
- radio stacking details (map weighting, median stack procedure): 1
- procedure for rescaling sfrd by aless excess: 1
- exact casa version used for pipeline and tclean: 1
- number of clean iterations/mask specifics, spectral cube channelization for final cubes: 1
- exact bootstrap settings for stacking and error bars: 1
- line-free channel ranges per source (only rule given): 1

## Paper excerpts (40 of 118, chosen for detail and spread over fields/years)

### 2019MNRAS.485.2092C: Suppressed CO emission and high G/D ratios in z = 2 galaxies with sub-solar gas-phase metallicity (2019; high_z_galaxies, galaxy_clusters_and_sz; observational_alma_primary)
- question: How do molecular gas, dust and star formation relate in sub-solar metallicity galaxies at z~2, and how do alpha_CO and G/D depend on metallicity?
- step 1: Derive metallicities
  - method: N2 diagnostic with PP04 calibration on MOIRCS spectra; stacked via simultaneous Gaussian fit and Monte Carlo resampling [3.1 Gas phase metallicity measurements: "We derive oxygen abundances with the N2 = log$_{10}$([NII]6583/H$\alpha$) diagnostic and the (cite: ref:M.Pettini2004) calibration"]
  - parameter: [NII] ratio fixed to 3.05; 1000 Monte Carlo stacked spectra [3.1 Gas phase metallicity measurements: "the ratio of the line fluxes between the two [NII] lines must be equal to 3.05"]
  - validation: Jackknife; O3N2 comparison [3.1 Gas phase metallicity measurements: "We verified through a jackknifing analysis that our results are not heavily biased by individual galaxies"]
- step 2: Measure CO line fluxes and stack
  - method: Point-source fits in uv plane at optical positions, visibilities collapsed over Halpha-derived 90% flux width; weighted mean stack [2.2 CO spectroscopy and dust continuum …: "Line fluxes were measured directly in the uv-visibility plane with the GILDAS task `uv_fit`."]
  - software: GILDAS
  - parameter: Stack velocity width 753±22 km/s; errors scaled so Var(S/sigma)=1 in line-free channels [3.2: "calculate the stacked line fluxes over the mean FWZP linewidth of the individual galaxies, $\Delta$v=753$\pm$22kms$^{-1}$"]
  - assumption: Galaxies unresolved (PSF response) [2.2 CO spectroscopy and dust continuum …: "all spectra were extracted assuming a point spread function (PSF) response"]
  - validation: MCMC redshift displacement and linewidth resampling show negligible effect [3.2: "The effect of this on the output stacked line fluxes is negligible."]
- step 3: Measure continuum, dust masses and stack
  - method: 870um fluxes with GALFIT on dirty images; 2mm in uv plane; flux converted to Md with Magdis template; weighted combination; image-plane stack of dust mass maps [3.3 Dust continuum emission: "All of these individual dust maps were then stacked in the image plane, by performing a weighted co-add of the images at each pixel position."]
  - software: GALFIT, GILDAS
  - parameter: <U>=22; L_IR/Md factor 125; 0.15 dex systematic [3.3 Dust continuum emission: "our assumed value of $\langle$U$\rangle$=22"]
  - assumption: Dust temperature as in z=2 MS template [3.3 Dust continuum emission: "As we cannot constrain the temperature of the dust with these data"]
  - validation: CASA, GILDAS and GALFIT fluxes previously verified consistent [2.2 CO spectroscopy and dust continuum …: "continuum fluxes measured with Common Astronomy Software Applications"]
- step 4: Derive gas masses, alpha_CO and G/D limits
  - method: Mmol = SFR/SFE with integrated KS law (Sargent 2014 eq. 5); alpha_CO = Mmol/L'CO; G/D ~ Mmol/Md; log-slope fits against metallicity on normalised scale [3.4 Molecular gas masses: "we assume that SFE increases smoothly with distance above the MS"]
  - parameter: Metallicities normalised to MW-mass z~0 galaxy (Mstar=5.7e10) [4.2: "We normalise all metallicities by the metallicity Z$_{M_{\star}(MW, z=0)}$ of a z$\sim$0 Milky-Way-like galaxy"]
  - assumption: Gas dominated by molecular gas at z=2 [4.2.2: "the gas phase in our galaxies at z=2 is dominated by molecular gas"]
  - fitting: Linear fit between literature median and stacked limit [4.2.1: "We perform a linear fit between the median $\alpha_{\rm CO}$ and metallicity of the z$>$1 galaxies"]
  - validation: Jackknife on V580 [4.2.2: "We verify through jackknife analysis that this stacked G/D ratio is not strongly driven by the G/D of V580."]
- result: Stacked metallicity = 8.34 ± ±0.13 12+log(O/H) PP04 N2 [3.1 Gas phase metallicity measurements: "We find a weighted-average, stacked metallicity value Z=8.34$\pm$0.13."]
- result: Stacked CO[4-3] flux = <47 ± 3 sigma limit mJy km/s [3.2: "We therefore place a 3$\sigma$ upper limit on the stacked CO[4-3] line flux of $<$47mJy kms$^{-1}$"]
- result: Stacked CO[1-0] flux = <20 ± 3 sigma limit mJy km/s [3.2: "In the stacked CO[1-0] spectrum, we find a 3$\sigma$ upper limit of $<$20mJy kms$^{-1}$."]
- result: Stacked dust mass = <7.4e7 ± 3 sigma limit Msun [3.3 Dust continuum emission: "M$_{d}<$7.4$\times$10$^{7}$ M$_{\odot}$"]
- result: alpha_CO slope vs metallicity = <-0.8 ± lower limit dimensionless [4.2.1: "We find a lower limit on the dependence with metallicity of $Z^{-0.8}$"]
- result: G/D slope vs metallicity = <-2.2 ± lower limit dimensionless [4.2.2: "We find a lower limit on the slope between our stacked G/D limit and the median (cite: ref:A.Saintonge2013) value of -2.2"]
- result: Stacked alpha_CO relative to MW = >2.4 ± lower limit factor [4.3.1: "our stacked $\alpha_{\rm CO}$ limit lies a factor $>$2.4 above the MW value $\alpha_{\rm CO}$=4.4"]
- limitation (authors): Gas masses rely on assumed MS SFE; effect of MS offset cannot be dissected with five galaxies [4.2.2: "the effect of main-sequence offset on ISM scaling relations cannot be dissected with the number of galaxies studied in this paper"]
- not stated (card): Calibration details, CASA version, imaging parameters (weighting, cleaning) for ALMA/VLA data (deferred to Coogan 2018); Spectral channel widths and line-free channel selection; Exact SFE prescription parameters and Sargent 2014 equation 5 values; GILDAS uv_fit settings and neighbour source models; GALFIT setup for 870um mosaic

### 2018A&A...616A.100Y: Stellar masses and disk properties of Lupus young stellar objects traced by velocity-aligned stacked ALMA <SUP>13</SUP>CO and C<SUP>18</SUP>O spectra (2018; protoplanetary_disks; archival_reuse)
- question: Can velocity-aligned stacking of 13CO and C18O (3-2) data from the ALMA Lupus survey yield more detections, dynamical stellar masses, disk orientations and gas masses, and how do gas masses relate to dust masses and accretion rates?
- step 2: Grid search with velocity-aligned stacking for M*, PA, i, Vsys
  - method: Shift spectra by projected Keplerian velocities, integrate within 1 arcsec de-projected radius, maximize S/N of Gaussian-weighted integrated intensity; uncertainties from parameter ranges giving consistent line profiles [Method: "we searched for the parameter set that maximized the S/N ratios of the aligned stacked spectra"]
  - parameter: M* 0.1-3 Msun (0.1 steps); PA 0-355 deg (5); i 5-85 deg (5); Vsys 1.7-6.3 km/s (0.1) [Method: "$5\ensuremath{^\circ} \leq i \leq 85\ensuremath{^\circ}$ in steps of 5$\ensuremath{^\circ}$"]
  - parameter: detection: peak >4 sigma and >=3 channels above 3 sigma within 2 sigma Gaussian width [Method: "the peak intensity of the best-aligned stacked spectrum is above 4$\sigma$ and (2) there are at least three channels above 3$\sigma$ within the 2$\sigma$ Gaussian line width."]
  - assumption: geometrically thin Keplerian disk; stellar position at continuum center; distances 150/200 pc [Method: "the assumption that its disk traced by the $^{13}$CO and C$^{18}$O (3–2) lines is geometrically thin"]
  - fitting: S/N-maximization grid search; Gaussian fits to stacked spectra [Method: "Then, we searched for the parameter set that maximized the S/N ratios of the aligned stacked spectra, and adopted this parameter set as our measurements of $M_\star$, PA, $i$, and $V_{\rm sys}$ of that source."]
  - validation: Tested on 30 blank-field synthetic images (no detections), 3 bright sources vs PV diagram analysis, and 24 model disks [Method: "We have tested the method on 30 synthetic ALMA images of a blank field"]
- step 3: Measure fluxes
  - method: Apply best parameters; stack in radial bins (half-beam steps) to find detected radius (2 sigma); integrate within twice the FWHM line width; apply same to C18O [Measured Stellar Mass and Disk Properti…: "we measured the total integrated flux within twice of the FWHM line widths in the aligned stacked spectra."]
  - parameter: C18O detection above 4 sigma; 20% systematic flux uncertainty [Measured Stellar Mass and Disk Properti…: "We define that the C$^{18}$O emission is detected when the integrated flux is above the 4$\sigma$ threshold."]
  - assumption: 13CO and C18O trace the same regions [Measured Stellar Mass and Disk Properti…: "we assume that the $^{13}$CO and C$^{18}$O lines trace the same regions"]
  - validation: Compared with Ansdell16 fluxes [Measured Stellar Mass and Disk Properti…: "the mean difference is 10%"]
- result: 13CO detections = 41 of 88 ± not stated disks [abstract: "We obtain $^{13}$CO detections in 41 disks and C$^{18}$O detections in 18 disks"]
- result: Mean dynamical vs spectroscopic mass difference (16 sources) = 0.15 ± not stated Msun [Discussion: "The mean difference between the dynamical and spectroscopic stellar masses in this subsample is 0.15 $M_\ensuremath{\odot}$."]
- result: Mean inclination difference vs continuum (23 disks) = 15 ± not stated deg [Measured Stellar Mass and Disk Properti…: "The mean difference of the disk inclination, $i$, measured from our method and from the continuum emission is 15$^\circ$"]
- limitation (authors): Stellar mass can be overestimated for fluxes ≲400 mJy km/s; inclination poorly constrained [Demonstration with models: "when the total flux is as low as 400 mJy km s$^{-1}$, $M_\star$ can be overestimated"]
- not stated (card): Code for the stacking/alignment and S/N search (not released); Exact clean parameters (image size, cell, threshold, masks); Continuum subtraction and line-free channels; Exact outlier-trimming rule for S/N distribution; Model-grid details for the luminosity-weighted gas mass averaging; Dust mass conversion details (taken from Ansdell16/Miotello17)

### 2014ApJ...780..115D: An ALMA Survey of Sub-millimeter Galaxies in the Extended Chandra Deep Field South: Sub-millimeter Properties of Color-selected Galaxies (2014; high_z_galaxies; archival_reuse)
- question: What are the sub-mm (344 GHz) properties, dust SEDs and SFRs of optical/NIR color-selected galaxies (K-selected, sBzK, ERO, DRG) in ALESS fields, as measured by stacking ALMA data?
- step 2: Stack ALMA 344 GHz postage stamps
  - method: Cut stamps, primary-beam correct, weighted average (weights = inverse square of PB correction); also median stacks [4.1 Method: "We align all the postage stamps, scale them to account for the primary beam attenuation computed at step #2, and then weight-average them."]
  - parameter: flux cuts of 3.6, 1.8, 1.2 mJy; z>1 subsample; smoothing to 1.6'' circular beam test [4.1 Method: "We then progressively lower the flux cutoff to $S_{\nu}$(344 GHz)=$1.8$ mJy and $S_{\nu}$(344 GHz)=$1.2$ mJy, and repeat the experiment."]
  - assumption: all maps have same depth within ~20% [Footnote 4: "Our working assumption is that all the maps have the same depth, which is true to within $\sim20$ % accuracy"]
  - validation: Two independent stacking routines gave consistent results [4.1 Method: "The analysis is repeated with two different stacking routines, developed independently within our collaboration, finding consistent results."]
- step 3: Estimate stacking uncertainties
  - method: Stack N random positions per sample, 50 iterations; rms of stacked fluxes = noise [4.2 Estimate of uncertainties: "We perform 50 iterations, in order to gauge the variance of the random stacks."]
  - assumption: maps are mostly source-free [4.2 Estimate of uncertainties: "The assumption here is that the maps are mostly “source-free”"]
  - validation: Random-stack mean consistent with zero [4.2 Estimate of uncertainties: "we have verified that the average stacked values in the random iterations are always consistent with zero."]
- step 4: Stack SPIRE maps and fit dust SED, derive L_IR and SFR
  - method: Stack deblended SPIRE residual maps at z>1; fit modified blackbody; integrate 8-1000 um; SFR from Genzel+10 relation [5.2 Herschel/SPIRE stacks: "We fit the observed SEDs as modified black bodies $S_\nu \propto \nu^{\beta} B_\nu(T_{\rm dust})$"]
  - parameter: T_dust=12-60 K, beta=1.4-2.0 range [5.2 Herschel/SPIRE stacks: "$T_{\rm dust}=12-60$ K is the dust temperature, and $\beta=1.4-2.0$ sets the frequency dependence of the dust opacity"]
  - assumption: Chabrier IMF [5.2 Herschel/SPIRE stacks: "This conversion implicitly assumes a (cite: chabrier03) initial mass function."]
  - validation: Compared with dust temperatures from other studies [5.2 Herschel/SPIRE stacks: "These values are in agreement with the findings of similar studies"]
- step 5: Test ALESS-field bias with radio stacks, clustering and redshift distributions
  - method: KS tests, Monte-Carlo clustering, 1.4 GHz median stacks, bootstrapping of field medians [5.3.3 Radio fluxes: "This bootstrapping approach allows us to evaluate whether the discrepancy between the general field and ALESS-covered galaxies can be explained as an accidentally-bright realization"]
  - validation: ALESS medians >4-sigma outliers vs field bootstrap [5.3.3 Radio fluxes: "represent $>4$-$\sigma$ outliers compared with the distribution of median stack values derived from bootstrapping the field sample."]
- result: Stacked 344 GHz flux, sBzK (all) = 1.88 ± 0.11 mJy [Table 1: "| sBzK | 22 | 1.88 | 0.15 | 0.11 |"]
- result: Stacked 344 GHz flux, K_Vega<20 (all) = 0.78 ± 0.06 mJy [Table 1: "| $K_{\rm Vega}<20$ | 100 | 0.78 | 0.06 | 0.06 |"]
- result: Stacked 344 GHz flux, DRG (all) = 1.77 ± 0.12 mJy [Table 1: "| DRG | 20 | 1.77 | 0.13 | 0.12 |"]
- result: Stacked 344 GHz flux, ERO (all) = 1.11 ± 0.10 mJy [Table 1: "| ERO | 26 | 1.11 | 0.09 | 0.10 |"]
- result: Dust temperature, K<20 z>1 = 32 ± +7/-2 K [Table 2: "$32_{-2}^{+7}$"]
- result: SFR, ERO z>1 = 140 ± +70/-40 Msun/yr [Table 2: "$140_{-40}^{+70}$"]
- result: SFR, sBzK z>1 = 74 ± +17/-19 Msun/yr [Table 2: "$74_{-19}^{+17}$"]
- result: Dust emissivity index beta = 1.6 ± not stated dimensionless [5.2 Herschel/SPIRE stacks: "We find $\beta=1.6$ and $T_{\rm dust}\approx 30$ K in all the cases."]
- result: ALESS 1.4 GHz median stack K<20 = 10.0 ± 1.0 uJy [Table 3: "| $K_{\rm Vega}<20$ | $10.0 \pm1.0$ | $9.8 \pm1.0$ | $9.1 \pm1.0$ | $8.2 \pm1.0$ | $3.94\pm0.16$ | $2.5\pm0.3$ |"]
- limitation (authors): Photometric redshift uncertainties large; physical association flag may be a by-product of similar redshift distributions [5.3.4 Physical association vs. chance p…: "We note however that the uncertainties in the photometric redshifts used in this test are large."]
- not stated (card): CASA version and calibration details (in Hodge et al. 2013); Calibrated ALESS image products/primary beam models used; Exact positions of pointings and catalog cross-match details; Fitting method/priors for the modified blackbody and how SPIRE+344 GHz points were weighted; Redshifts used for each galaxy in SED fits; Radio stacking details (map weighting, median stack procedure); Procedure for res…

### 2020A&A...643A...2B: The ALPINE-ALMA [CII] survey: Data processing, catalogs, and statistical source properties (2020; high_z_galaxies; large_program_or_survey)
- question: Process the ALPINE ALMA band-7 data into continuum and [CII] catalogs and derive basic dust and [CII] properties, number counts and redshift distribution of serendipitous continuum sources
- step 6: Derive 158 um continuum to L_IR conversion via Herschel stacking
  - method: Mean stacking of SFR>10 Msun/yr COSMOS sources at 4<z<5 and 5<z<6; fit templates with free normalization [4.3: "We renormalized the templates to fit the data. This is the only free parameter in our analysis."]
  - assumption: Bethermin2017 template with no evolution above z~4 (<U>=50) [4.3: "Above this redshift, no evolution is assumed ($\langle U \rangle$ = 50)."]
  - fitting: chi2 of templates; MBB with beta=1.8 shown for information [4.3: "a modified blackbody with a fixed $\beta$ of 1.8, but a free amplitude and temperature"]
  - validation: Bootstrap errors [4.2: "The uncertainties were derived using a bootstrap technique that takes into account both the photometric noise (instrumental and confusion) and the population variance."]
- step 8: Stack continuum by [CII] luminosity to get SFR-L[CII]
  - method: Image-plane stacking in four L[CII] bins and z<5 / z>5, aperture photometry, SFR_tot=SFR_IR+SFR_UV [7.5: "We then stacked the continuum of all the sources of a given luminosity bin in image space after masking the continuum nontarget detections."]
  - assumption: kappa_IR=1.02e-10, kappa_FUV=1.47e-10 Msun/yr/Lsun (Chabrier IMF) [7.5: "their values are 1.02$\times$10$^{-10}$ M$_\odot$yr$^{-1}$L$_\odot^{-1}$ and 1.47$\times$10$^{-10}$ M$_\odot$yr$^{-1}$L$_\odot^{-1}$, respectively."]
  - validation: Bootstrap errors; mergers excluded as test [7.5: "we tested if this excess could be caused by merging systems by excluding objects classified as merger (type=2)"]
- result: L_158um / L_IR = 0.093 ± not stated dimensionless [Conclusion: "(L$_{158\,\mu m}$ = 0.093 L$_{\rm IR}$)"]
- limitation (authors): Stacked-SED sample selection imperfect; conversion may be inaccurate for outliers [4.4 Caveats: "The derived conversion factors could thus be largely inaccurate for outliers with extreme dusty SEDs."]
- not stated (card): Exact CASA version used for pipeline and tclean; Number of clean iterations/mask specifics, spectral cube channelization for final cubes; Exact bootstrap settings for stacking and error bars; Line-free channel ranges per source (only rule given); Exact catalog of manual spw fixes; Details of uv-fit and stacking in unpublished companion papers

### 2025ApJ...985..194P: Traversing the Star-forming Main Sequence with Molecular Gas Stacks of z ∼ 1.6 Cluster Galaxies (2025; high_z_galaxies, galaxy_clusters_and_sz; observational_alma_primary)
- question: Do z~1.6 cluster galaxies, including those at low mass and well below the star-forming main sequence, have molecular gas fractions that differ from coeval field galaxies, as measured with stacked CO(2-1)?
- step 4: Group and stack spectra
  - method: Shift to rest frame, interpolate to 50 km/s, inverse-variance weighted stacks in LM, HM-aMS, HM-bMS groups and CO-detected/undetected subsets [Spectral Stacking: "stack the spectra in each grouping with inverse-variance weighting according to their line-free channel-to-channel rms"]
  - parameter: LM: logM<10; HM-aMS: logM>10, DeltaMS>-0.3; HM-bMS: logM>10, DeltaMS<-0.3 [Spectral Stacking: "The remaining galaxies that are above log($M_{*}/M_{\odot}) > 10.0$ and more than 0.3 dex below the SFMS are considered part of the High Mass-below SFMS grouping"]
  - assumption: SFMS scatter 0.3 dex [Spectral Stacking: "we adopt a scatter of 0.3 dex on the SFMS"]
  - validation: results insensitive to using DeltaMS<0 as the bMS cut [Spectral Stacking: "our results are insensitive to adjusting the below Main Sequence classification to any measurement below the Main Sequence ($<$0 dex offset)"]
- step 6: Fit Gaussian line to stacks
  - method: Nested sampling Gaussian fit with bootstrap channel errors; non-parametric SNR [Bayesian Fitting of Stacked Spectra: "We model a Gaussian emission line using the `dynesty` package (cite: 2020MNRAS.493.3132S) to perform nested sampling fits"]
  - software: dynesty
  - parameter: Priors: centroid in (-300,300) km/s, amplitude in (0,1.5) mJy, FWHM in (0.01,500) km/s [Bayesian Fitting of Stacked Spectra: "velocity centroid $\in$ (-300,300) km s$^{-1}$; centroid amplitude $\in$ (0.00, 1.50) mJy; FWHM $\in$ (0.01,500) km s$^{-1}$"]
  - fitting: Uniform prior on amplitude, Gaussian priors on centroid (sigma=63.7 km/s at 0) and FWHM (300±31 LM, 365±21 HM-aMS, 407±61 HM-bMS km/s) [Bayesian Fitting of Stacked Spectra: "We assign a uniform prior to the amplitude parameter, and Gaussian priors to the centroid and FWHM parameters."]
- limitation (authors): T18 is not calibrated below the SFMS; limited metallicity info; 6 of 10 HM-bMS CO-undetected galaxies have SFRs constrained only by HerMES upper limits [Comparison of CO-detected to CO-undetec…: "the T18 field scaling relation is primarily calibrated for galaxies on or above the SFMS at this redshift"]
- not stated (card): Stellar mass-metallicity relation and alpha_CO prescription details used (T18 form); CIGALE module parameters (tau, age grids, etc.); Line-free channel ranges for continuum subtraction; Per-galaxy stellar masses, SFRs, DeltaMS, redshifts; Cube image sizes and clean mask definitions; Spectral extraction aperture sizes per galaxy and exact aperture formula; Numeric flux scale uncertainty; Metallici…

### 2024ApJ...965..147B: The Carbon Isotopic Ratio and Planet Formation (2024; protoplanetary_disks, astrochemistry; archival_reuse)
- question: What is the 12C/13C ratio in C2H in the TW Hya disk, does it differ from that in CO, and can thermochemical models with isotopic fractionation produce two separate carbon isotopic reservoirs?
- step 2: Extract 13CCH stacked spectrum
  - method: Shift spectra by Keplerian velocity, stack in annuli 0.52-1.68 arcsec weighted by area, integrate [2.2 $^{13}$CCH: "the spectrum in each pixel was shifted to the systemic velocity by applying a shift of $\delta v(r,\,\phi) = -v_{\rm kep}(r) \, \cos \phi \, \sin i$"]
  - software: GoFish
  - parameter: Annulus width 1/4 beam FWHM (~80 mas); weights proportional to r^2; centre offset (-52, -155) mas [2.2 $^{13}$CCH: "As each annulus has a fixed width of 1/4 of the beam FWHM (${\sim}~80~{\rm mas}$), the weights are simply proportional to $r^2$."]
  - assumption: 13CCH radial profile follows C2H [2.2 $^{13}$CCH: "Assuming that the radial emission profile of $^{13}$CCH follows that of C$_2$H"]
  - fitting: Gaussian fits to line peaks [2.2 $^{13}$CCH: "From Gaussian fits to the line, the peak intensity values for the bright annulus region"]
  - validation: JvM correction 1% flux difference; radii varied to maximise S/N [2.2 $^{13}$CCH: "The integrated flux density was not found to substantially vary compared to the native data, finding only a 1% difference."]
- result: 13CCH integrated flux, bright annulus = 56.9 ± 14.1 mJy km/s [2.2 $^{13}$CCH: "yields an integrated flux of $56.9 \pm 14.1~{\rm mJy~km\,s^{-1}}$"]
- limitation (authors): Models do not fully match observations; CO enrichment only 50 vs 20 [5.2: "Our models also do not fully match observations."]
- not stated (card): Image size, cell size, deconvolver, threshold and masking for CLEAN of 13CCH; Line-free channels used for self-calibration and solint; Rest frequencies and hyperfine line parameters; Velocity integration limits for line fluxes; Flux calibrator flux values; Full DALI chemical network files and grid setup

### 2018ApJ...860..103S: Molecular Gas Contents and Scaling Relations for Massive, Passive Galaxies at Intermediate Redshifts from the LEGA-C Survey (2018; nearby_galaxies, high_z_galaxies; observational_alma_primary)
- question: Do gas scaling relations derived from star-forming galaxies extend to passive galaxies at z~0.7, and what are their molecular gas contents and kinematics?
- step 5: Stack continuum and CO
  - method: Average image-plane inverted images/cubes of targets (continuum and CO at known redshifts) [2.4.1 2 mm Continuum Stack: "we opt to simply average together inverted images of the targets rather than perform this analysis in the Fourier plane"]
  - parameter: Dust-based M_H2: kappa_235GHz=0.42 cm2/g, Tdust=25 K, GDR=100 [2.4.1 2 mm Continuum Stack: "a dust temperature $\ensuremath{T_{\rm{dust}}}= 25$ K, and a gas-to-dust ratio typical of solar metallicity systems, $\ensuremath{\delta_{\rm{GDR}}}= 100$"]
  - validation: Recovered sample-average line flux by stacking only CO-detected sources [2.4.2 CO Spectral Stack: "We have also verified that this procedure accurately recovers the sample-average line flux by stacking only the sources individually detected in CO."]
- result: 2 mm continuum stack (all) = 17 ± 5 uJy [2.4.1 2 mm Continuum Stack: "a faint source with $\ensuremath{S_\mathrm{2mm}}= 17 \pm 5$ $\mu\rm{Jy}$ is detected"]
- result: 2 mm stack of CO-detected = 23 ± 7 uJy [2.4.1 2 mm Continuum Stack: "The CO-detected sources are detected in the 2 mm continuum stack with $\ensuremath{S_\mathrm{2mm}}= 23 \pm 7$ $\mu\rm{Jy}$"]
- result: Dust-based mean M_H2 of CO-detected = 8.8e9 ± not stated Msun [2.4.1 2 mm Continuum Stack: "we find an average molecular gas mass for the CO-detected sources of $8.8 \times 10^9$ $\rm{M}_\odot$"]
- result: CO stack of non-detections L'CO(2-1) upper limit (3 sigma) = <5.8e8 ± not stated K km/s pc^2 [2.4.2 CO Spectral Stack: "$\ensuremath{\rm{L}_{\rm{CO(2-1)}}'}< 5.8 \times 10^8$ K $\rm{km\,s}^{-1}$ pc$^2$"]
- result: Stack of non-detections M_H2 limit = <3.2e9 ± not stated Msun [2.4.2 CO Spectral Stack: "this is equivalent to $\ensuremath{M_{\rm{H}_2}}< 3.2 \times 10^9$ $\rm{M}_\odot$"]
- result: Stack of non-detections f_H2 limit = <0.016 ± not stated dimensionless [2.4.2 CO Spectral Stack: "the resulting upper limit on the gas fraction of these passive sources is $\ensuremath{f_{\rm{H}_2}}=\ensuremath{M_{\rm{H}_2}}/\ensuremath{M_{\rm{star}}}<0.016$"]
- limitation (authors): Small sample of 8; alpha_CO systematic uncertainty ~50%; SFR from 24um may be overestimated up to ~2x [3.1 Basic Gas Properties: "With only 8 target galaxies in total, we cannot draw strong conclusions on this point."]
- not stated (card): CASA/pipeline version; Line-free channels and continuum subtraction method; Image size, cell size, and clean parameters; Exact tool and procedure for point-source visibility fitting; Gaussian line-fit procedure details; Stacking weights and procedure; Per-target SFRs/stellar masses from DR2 catalog; Rest frequency of CO(2-1) used and flux scale uncertainty

### 2025MNRAS.541.4031D: VERTICO ─ IX. Signatures of environmental processing of the gas in Virgo cluster spiral galaxies through mapping of CO isotopologues (2025; nearby_galaxies, galaxy_clusters_and_sz; large_program_or_survey)
- question: How do 13CO and C18O emission and line ratios in Virgo cluster spirals vary with galaxy properties, and what do they imply about environmental processing of the molecular gas?
- step 2: Stack cubes globally with STACKARATOR
  - method: Shift spectra of every 12CO-detected spaxel by 12CO moment-1 velocity and co-add [2.3 STACKARATOR: "we shift the spectra from every $^{12}$CO(2-1) detected spaxel within each galaxy to a common velocity reference according to the $^{12}$CO(2-1) moment one"]
  - software: STACKARATOR
  - validation: Compared stacked 12CO flux with Brown2021 summed flux [3.2 Stacked global detections: "The integrated intensities closely follow the one-to-one black dashed line"]
- step 3: Fit stacked lines and estimate uncertainties
  - method: Single vs double gaussian (same centre) fitted with MCMC; double only if BIC lower; flux by integrating model; errors from 1000 random off-line window sums [2.3 STACKARATOR: "We sum the stacked spectrum at 1000 randomly chosen off-line locations using a window the same width as the best fit gaussian full-width at zero intensity."]
  - software: GAStimator
  - fitting: MCMC gaussian fits, model selection by BIC [2.3 STACKARATOR: "These models are fitted to the data using Markov chain Monte Carlo (MCMC) fitting code GASTIMATOR"]
  - validation: Tested stricter BIC difference >10; results unchanged [2.3 STACKARATOR: "We tested if more stringent criteria (e.g. the difference in the BIC values needing to be $>10$) improved the fits, but this did not significantly change our results."]
- step 4: Radial and quadrant stacking
  - method: Stack in concentric elliptical beam-width apertures, and in quadrants toward/away from HI tails [3.7 Tailed galaxies: "we stack quadrants of each galaxy towards and away from the direction of the H tail"]
  - software: STACKARATOR
- result: Range of 12CO/13CO global ratios = 10-43 ± not stated dimensionless [3.3: "ranging from 10 – 43"]
- result: C18O global detections = 9 galaxies in Sec 3.2 (8 in Sec 3.8) ± not stated galaxies [3.2: "C$^{18}$O, on the other hand, was detected in 9 galaxies."]
- limitation (authors): Small comparison samples and degeneracy between optical depth and abundance [4.3: "While the scenario described above cannot be proven with the existing data (due to the degeneracy with abundance variations)"]
- not stated (card): Calibration pipeline/CASA versions and imaging parameters (robust, channel width) for VERTICO cubes; GAStimator priors, initial guesses, chain length; Radial aperture count and widths, and S/N criteria for radial bin detections; Conversion of Jy km/s to K km/s used for ratios; Definition of detection threshold in stacks beyond 5 sigma; LTSFIT settings; Anderson-Darling test implementation; Stack-…

### 2021ApJ...908...46B: Dynamical Stellar Masses of Pre-main-sequence Stars in Lupus and Taurus Obtained with ALMA Surveys in Comparison with Stellar Evolutionary Models (2021; protoplanetary_disks, star_formation, stellar_physics; archival_reuse)
- question: Do spectroscopic stellar masses from PMS evolutionary models agree with dynamical masses measured from Keplerian rotation of disks in Lupus and Taurus, as a function of stellar mass?
- step 2: Stack molecular lines
  - method: Noise-weighted mean of cubes of different transitions/molecules [4.1 Stacking Molecular-Line Data: "The image cubes were combined by calculating the noise weighted mean of them."]
  - assumption: Different molecules follow same Keplerian rotation; scale-height effect small (<3%) [4.1 Stacking Molecular-Line Data: "because different molecules in a disk are expected to follow the same Keplerian rotation"]
  - validation: Compared masses from individual lines; 80% agree within 1 sigma [5.3 Measurements with Individual Lines: "80% of the measurements from different line data agree on a level better than 1$\sigma$"]
- step 3: Measure dynamical stellar mass
  - method: Maximise S/N of velocity-aligned stacked spectrum over M* and vsys with i, PA, position, distance fixed [4.2 Measuring Stellar Mass: "Thus, there are only two unknown parameters, $M_{\star}$ and $v_{sys}$ in our analysis."]
  - parameter: initial R = 1 arcsec, iterate until disk radius (95% flux) changes <10%; reject peak S/N <4 sigma or width <3 channels [4.2 Measuring Stellar Mass: "any velocity aligned stacked spectrum with the S/N at its peak below 4$\sigma$ or with its line width narrower than three times the channel width was excluded"]
  - assumption: Geometrically thin disk [4.2 Measuring Stellar Mass: "we adopted the assumption of a geometrically thin disk structure."]
  - fitting: Grid search; Gaussian fit to aligned spectrum, S/N of Gaussian-weighted integrated intensity [4.2 Measuring Stellar Mass: "we first fitted a Gaussian line profile to the velocity aligned stacked spectrum, and calculated the S/N of the integrated intensity within a 1$\sigma$ Gaussian line width."]
  - validation: Synthetic DALI cubes; 700 noise realisations [4.4 Robustness and Potential Bias: "we generated 700 synthetic ALMA data cubes from the disk models and included different random noise during the imaging simulations."]
- result: Number of dynamical mass measurements = 45 of 67 ± not stated stars [abstract: "measured the stellar masses of 45 out of 67 PMS stars from the Keplerian rotation in their circumstellar disks"]
- result: Sz83 inclination from 13CO = 16.0 ± +6/-4 deg [Table: "| Sz83 | 15:56:42.29 | -37:49:15.82 | 16.0$^{+6.0}_{-4.0}$ | 120.0$\pm15.0$ | 160 |"]
- limitation (authors): Accuracy limited by S/N; high-mass bin has only six stars; highly inclined disks may be overestimated [Comparison with Literature (Discussion): "Nevertheless, the accuracy of our dynamical mass measurements is limited by the S/N of the data."]
- not stated (card): Image size and cell size; Line-free channel ranges per source; Clean threshold, masks, number of iterations; Exact velocity grid and search steps for M* and vsys; How stellar models were interpolated to derive spectroscopic masses; Flux calibration details and per-source continuum subtraction order; Code for the alignment analysis not released

### 2020MNRAS.497.2771M: VALES VI: ISM enrichment in star-forming galaxies up to z ∼ 0.2 using <SUP>12</SUP>CO(1-0), <SUP>13</SUP>CO(1-0), and C<SUP>18</SUP>O(1-0) line luminosity rati… (2020; nearby_galaxies; observational_alma_primary)
- question: How do the 12CO/13CO and 13CO/C18O line luminosity ratios of low-z star-forming galaxies depend on global galaxy properties (SFR, SFE, LIR, morphology), probing ISM enrichment?
- step 2: Moment-0 stacking and flux extraction
  - method: Align moment-0 maps with astrometric corrections (~1.4") and stack with custom code; fit 2D Gaussian (FWHM 4.5", point-like) on 30"x30" stamps [3.1.1 2D-moment-0 stacking: "To extract velocity integrated line flux densities from the stacked signals, we create $30"\times30"$ stamps and model the sources with a 2D Gaussian profile"]
  - software: CASA immoments, custom stacking code
  - parameter: 12CO line widths measured at 20 km/s channels [3.1.1 2D-moment-0 stacking: "we measure $^{12}$CO line widths using 20 km s$^{-1}$ channel for all galaxies"]
  - fitting: 2D Gaussian [2D-moment-0 stacking: "we create $30"\times30"$ stamps and model the sources with a 2D Gaussian profile, assuming that the stacked signals are point-like with a FWHM of 4.5$''$."]
  - validation: Monte Carlo systematic errors; comparison with 3D and uv stacking [Systematic Errors: "we ran Monte-Carlo simulations using data cubes with the same physical scales (pixel size, synthesised beam, primary beam) as those covered by the ALMA Band-3 observations."]
- step 3: Compare 3D and uv stacking
  - method: 3D channel-by-channel stacking at optimal 125 km/s channel; uv stacking with stacker on averaged-channel uv data; compare SNR [3.1.2 3D-image stacking: "we decided to use a common spectral channel width of 125 km s$^{-1}$ for $^{12}$CO, $^{13}$CO and C$^{18}$O"]
  - software: CASA tclean, CASA split, stacker
  - fitting: 1D Gaussian for line width then 2D Gaussian in central channel (3D) [3D-image stacking: "we fitted a 1D Gaussian profile to obtain the global stacked velocity line width FWHM$_{f}$ (see Fig. [2](#fig:3DStack-Scheme1) lower panel). Hence, we took the central channel"]
  - validation: Moment-0 chosen as it gives highest 13CO SNR [3.3 differences between the stacking ap…: "we decide to use the 2D (moment-0) approach to measure values, as this method yields the highest $^{13}$CO stacked SNRs"]
- step 5: Compute luminosities and ratios for subsamples
  - method: L' = 3.25e7 S dv nu_obs^-2 D_L^2 (1+z)^-3; Monte Carlo over flux errors and redshift distribution for CI; stack subsamples by morphology, LIR, SFR, SFE, Sigma [3.3 Luminosity measurements: "we have used a Monte Carlo simulation considering that the error from the velocity integrated line flux density measurements is normally distributed"]
  - assumption: LCDM H0=70, OmegaM=0.3, OmegaL=0.7; Chabrier IMF; alpha_CO 4.6 (B,D) and 0.8 (mergers) [4.1.2 The star-formation activity: "$\alpha_{\text{CO}}=4.6$ K km s$^{-1}$ pc$^{2}$ for B and D dominated galaxies and $\alpha_{\text{CO}}=0.8$ K km s$^{-1}$ pc$^{2}$ for mergers/interacting galaxies"]
- result: Average L'(12CO)/L'(13CO), all 27 galaxies = 16.1 ± 2.5 dimensionless [4.1.1: "Using all of the 27 galaxies, we find an average $L'$ ($^{12}$CO )/$L'$ ($^{13}$CO) line luminosity ratio of 16.1$\pm$2.5."]
- result: Average L'(13CO)/L'(C18O), 24 galaxies = 2.5 ± 0.6 dimensionless [4.2: "The average $L'$ ($^{13}$CO )/$L'$ (C$^{18}$O) line luminosity ratio found is 2.5$\pm$0.6"]
- result: L'(12CO)/L'(13CO) for mergers = 22.1 ± 8.6 dimensionless [Table (morphology): "| 4 | M | 3 | 22.1 $\pm$ 8.6 | 34 $\pm$ 6.9 | 9.6 $\pm$ 0.8 | 11.5 $\pm$ 0.2 |"]
- result: Stacked 13CO SNR (moment-0) = 15.1 ± not stated dimensionless [Table 2: "| $^{13}$CO | 15.1 | 12.9 | 9.5 | |"]
- limitation (authors): Optical depth not accounted; 12CO/13CO luminosity ratios are lower limits to abundance ratios; degeneracy between starburst age and top-heavy IMF [5.1: "the $L'$ ($^{12}$CO )/$L'$ ($^{13}$CO) luminosity ratios reported here should be taken as a lower limit of the $^{12}$CO/$^{13}$CO abundance ratio"]
- not stated (card): Custom stacking code is not released; weighting (mean vs median, weights) for moment-0 stacking not specified; Exact channel selection and line-free channels; continuum subtraction method not stated; Astrometric offsets per galaxy and 12CO velocity offsets not tabulated; Primary beam correction and image size/cell size not stated; Details of uv stacking (stacker settings, weights); Moment-0 flux-…

### 2026ApJ..1000..312Z: A Potential Link between Nuclear Winds and Cold Gas Outflows on Kiloparsec Scales in Reionization-era Quasars (2026; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Are nuclear winds (BALs) in z~5.5 quasars connected to kpc-scale cold gas outflows traced by broad [C ii] wings in stacked profiles?
- step 3: Stack [C II] spectra
  - method: Normalize by peak flux, shift to systemic redshift, inverse-variance weighted mean in 60 km/s bins; 1000 bootstraps for variance [3 Stacked [C II] Spectra: "we normalize each spectrum by its peak flux, shift the [C ii] emission line to the systemic redshift, and compute the mean stack in velocity space"]
  - parameter: 5 BAL and 11 non-BAL spectra; J0056+2241 excluded [3 Stacked [C II] Spectra: "We create stacked [C ii] spectra for the five strong BAL quasars and eleven non-BAL quasars, respectively."]
  - validation: image-plane cube stacking gives 4.48 sigma for BAL; random 5-quasar non-BAL stacks give <2% chance of S/N>=4.4 [4.3 Intrinsic Properties: "we find that the cumulative probability of randomly obtaining a broad wing with a significance equal to or greater than S/N = 4.4 is less than 2%"]
- step 4: Fit two-component Gaussian to stacks
  - method: Narrow (sigma<500 km/s, center fixed at 0) plus broad (sigma>500 km/s, free center); uncertainties from bootstrap [3 Stacked [C II] Spectra: "The narrow component’s line center is fixed at $\Delta v = 0$, while the broad component’s center is allowed to vary."]
  - fitting: two-Gaussian model; uncertainties from bootstrap realizations; optimizer not stated [3 Stacked [C II] Spectra: "We derive uncertainties in the fit parameters based on the stacked fluxes across the bootstrap realizations."]
  - validation: jackknife, FWHM split, velocity-normalized stacks, M1450 split [4.4 Robustness: "we performed jackknife tests by excluding one BAL quasar at a time and re-stacking the remaining four."]
- result: BAL stack broad component velocity offset = -2.1e2 ± +1.3/-0.7 e2 km/s [3 Stacked [C II] Spectra: "$\Delta v_{\rm b} = -2.1_{-0.7}^{+1.3}\times 10^2 \, \rm km\,s^{-1}$"]
- result: BAL stack broad component FWHM = 1.18e3 ± +0.39/-0.35 e3 km/s [3 Stacked [C II] Spectra: "a FWHM of $1.18_{-0.35}^{+0.39} \times 10^3 \, \rm km\,s^{-1}$"]
- result: BAL broad wing significance = 4.45 ± not stated sigma [3 Stacked [C II] Spectra: "detected with a mean signal-to-noise ratio of 4.45 within its FWHM"]
- result: Narrow component FWHM, BAL vs non-BAL stacks = 320 vs 430 ± not stated km/s [3 Stacked [C II] Spectra: "($\rm FWHM = 3.2\times10^2\,km\,s^{-1}$) than that of the non-BAL case ($\rm FWHM = 4.3\times10^2\,km\,s^{-1}$)"]
- limitation (authors): Cannot disentangle AGN- vs star formation-driven outflows [4.1 Nuclear Winds: "we caution that our stacking analysis cannot unambiguously disentangle AGN- and star formation-driven outflows."]
- not stated (card): Cell size, image size, and channel width of cubes; Line-free channel ranges per source; Flux calibrators and flux-scale uncertainty; Exact BAL BI0 continuum fitting details and ESI spectra reduced products; How peak normalization and significance (mean S/N within FWHM) are computed; Initial guesses/bounds for the two-Gaussian fit beyond sigma limit; Details of how L_[CII] of broad component is co…

### 2019ApJ...877L..25M: The First Bird’s-eye View of a Gravitationally Unstable Accretion Disk in High-mass Star Formation (2019; star_formation; observational_alma_primary)
- question: What is the structure, mass and gravitational stability of the innermost accretion disk and infalling envelope around the nearly face-on high-mass protostar G353.273+0.641?
- step 3: Envelope kinematics from CH3OH
  - method: Stack hot CH3OH lines, make PV diagram, compare with infalling rotating envelope model with fixed l and enclosed mass [CH3OH lines and infalling rotating enve…: "The specific angular momentum $l$ is also fixed to 2.4$\times$10$^{21}$ cm$^{2}$ s$^{-1}$, in order to have the centrifugal radius of 250 au"]
  - software: CASA
  - parameter: M_in = 12 Msun; inclination 8 deg; flaring angle ~35 deg [CH3OH lines and infalling rotating enve…: "$M_{\rm in}$ is the enclosed mass that is fixed to 12 M$_{\ensuremath{\odot}}$"]
  - assumption: axisymmetric counterclockwise rotation, no outflow contribution [CH3OH lines and infalling rotating enve…: "We assume that the envelope is rotating counterclockwise and purely axisymmetric."]
- limitation (authors): Beta uncertainty dominates Q; kinematic model not finely fitted; larger-scale envelope resolved out [Gravitational stability: "The major uncertainty of $Q$ in this study originates from the uncertainty of the dust opacity index $\beta$"]
- not stated (card): tclean parameters (weighting/robust, deconvolver, cell, image size, masks); line-free channels for continuum subtraction; calibrator list other than flux calibrator and pipeline version; line stacking procedure details (velocity alignment, weighting); flaring angle and model fit procedure (done by eye); elliptical Gaussian fit procedure; RADEX input details beyond T and linewidth

### 2019A&A...631A..78S: A spectral stacking analysis to search for faint outflow signatures in z ∼ 6 quasars (2019; agn_and_quasars, high_z_galaxies; archival_reuse)
- question: Is there a faint broad high-velocity [C II] component indicating outflows in the stacked spectra and cubes of z~6 quasars?
- step 3: Velocity re-binning to common FWHM
  - method: Rebin channels so each [CII] FWHM covers same number of channels, normalised to narrowest line [4.1 Velocity re-binning: "$cw_{rebin}\,=\,cw_{orig}\,\times\,\rm FWHM_{orig}/FWHM_{min}$"]
  - software: Line Stacker
  - parameter: FWHM_min = 270 km/s; mean stacked channel width 60 km/s [4.1 Velocity re-binning: "the channel width of the stacked spectrum is taken as the mean channel width of all the individual spectra once re-binned, for our sample that corresponds to 60 km s$^{\rm -1}$"]
  - validation: Mock stacking without outflow: >2 sigma broad excess in 2-5% of straightforward stacks, none without noise [6.1 Spectral line stacking methods: "excess emission due to a broad component is found at $>2\sigma$ 2-5% of the time"]
- step 4: Stack spectra (1-D) and cubes (3-D) with three weightings
  - method: Stack extracted spectra from >2 sigma moment-0 region, and full cubes pixel by pixel; weights 1, 1/sigma_rms^2, 1/S_peak [4.2 1-D and 3-D stacking: "The cubes are then stacked pixel by pixel in order to create the stacked cube."]
  - software: Line Stacker
  - parameter: 3-D spectra extracted over 2" region [5.1 Stacking the full sample: "we use a larger integration area (2$^{\prime\prime}$)"]
  - fitting: One- and two-component Gaussian fits; chi2 improvement and excess significance from residuals summed within ±800 km/s [5.1 Stacking the full sample: "we subtract the single component fit from the spectrum, and take the sum of the residuals within $\pm800$ km/s."]
  - validation: Noise-only and broad-component mock stacks (10 000 iterations) [5.3 Testing the feasibility: "14-17% of the iterations return a $>0.4\sigma$ excess signal in the stacked lines"]
- step 5: Select max/min sub-samples
  - method: 10 000 random sub-sets of 3-25 sources; integrate line-free channels (>2 FWHM) at radii 0.2-3"; rank sources by summed grades; max sub-sample above mean rank [5.2 A sub-sample with outflow signatures: "The sub-sample selection is done by randomly selecting sub-sets of $n$ sources, where $n$ is in the range 3$-$25, and repeated 10 000 times."]
  - software: Line Stacker
  - validation: Leave-one-out stacks; min sub-sample shows no outflow; broad parameters stay within 20% [5.2 A sub-sample with outflow signatures: "the FWHM, $S_{\rm peak}$ values of the broad component remain within 20% of those found for the stack of the complete *max sub-sample*"]
- result: Excess significance, full sample, 3-D stack = 1.1-1.5 ± not stated sigma [5.1 Stacking the full sample: "we calculate the significance of the excess emission to be 1.1–1.5$\sigma$"]
- result: Excess significance, full sample, 1-D stack = 0.4-0.7 ± not stated sigma [5.1 Stacking the full sample: "We find a significance of 0.4–0.7$\sigma$, depending on the weighting scheme used"]
- result: Excess significance, max sub-sample, 3-D = 1.2-2.5 ± not stated sigma [5.2 A sub-sample with outflow signatures: "the significance of excess emission rises to 1.2–2.5$\sigma$"]
- result: Number of sources in max sub-sample = 12 ± not stated sources [5.2 A sub-sample with outflow signatures: "The *max sub-sample* consists of 12 sources"]
- result: Broad component FWHM, max sub-sample 3-D, w=1 = 986 ± ±210 km/s [Table 3D results: "| $w=1$ | $6.14\pm0.69$ | $305\pm36$ | $2.0\pm0.3$ | $-1\pm10$ | $1.87\pm0.68$ | $986\pm210$ |"]
- result: False detection probability of >0.4 sigma excess in no-outflow mocks = 14-17 ± not stated % [5.3 Testing the feasibility: "14-17% of the iterations return a $>0.4\sigma$ excess signal in the stacked lines"]
- limitation (authors): Assumes a single broad Gaussian outflow profile; broad emission could be from interacting galaxies; low-velocity outflows not detectable [5.2 A sub-sample with outflow signatures: "we have assumed that the outflow emission signature has the spectral profile of a single broad Gaussian"]
- not stated (card): Line Stacker code is 'Jolly et al. in prep' and not released; Line-free channel ranges for uvcontsub and fit orders; Exact manual calibration scripts, flagging and which sources were recalibrated; How sigma significance of excess emission is normalised; Fitting method and starting guesses for the two-Gaussian fit; Grade definition and exact threshold details of sub-sample ranking; Exact moment-0 …

### 2017A&A...607L...5Q: Clues to NaCN formation (2017; evolved_stars, astrochemistry; observational_alma_primary)
- question: Where is NaCN distributed in the envelope of IRC +10216, what is its abundance profile, and is it formed from NaCl + CN?
- step 2: Stack NaCN lines
  - method: Stack NaCN 3 mm lines; smooth high-res maps to 5 km/s [2 Observations and NaCN distribution: "we stacked the emission from the NaCN lines presented in Table."]
  - software: GILDAS
  - validation: 2 mm maps show the same hollow shell [2 Observations and NaCN distribution: "show the very same structure, confirming the presence of the hollow shell mentioned above"]
- step 3: Fit abundance profile
  - method: LTE multi-shell model with ray tracing and beam convolution, fit to azimuthally averaged stacked intensity profiles (low and high resolution simultaneously) [3 NaCN modeling: "we used a local thermodynamical equilibrium (LTE) multi-shell approach carried out with the MADEX code (cite: MADEX) to reproduce the observations."]
  - software: MADEX
  - assumption: LTE (Tex=TK); spherical emission; no IR pumping [3 NaCN modeling: "we assumed that the emission distribution is mainly spherical."]
  - fitting: Abundance profile adjusted by hand/iteratively; high-S/N profile fit mandatory, low-S/N reasonable [3 NaCN modeling: "A good fitting of the high S/N emission profile was mandatory, while a reasonable fit of the low S/N profile was enough."]
- result: Radius where NaCN abundance rises = 3e15 ± not stated cm [Results: "we found that NaCN arises at a radius of $3\times10^{15}$ cm."]
- result: Inner hole radius in NaCN brightness = ~1.5 ± not stated arcsec [Discussion: "reveal a small inner hole with a radius $\sim$ 1.5$''$ in the brightness distribution of NaCN"]
- limitation (authors): LTE assumption may overestimate NaCN abundance; IR pumping not considered [Results: "we might expect non-LTE modeling to derive lower values of $T_\mathrm{ex}$ and therefore higher level populations, higher intensities, and lower abundances"]
- not stated (card): CASA version and calibrators; GILDAS clean parameters (weights, cell, image size, mask); Exact stacking procedure and weights; Line-free channels for continuum subtraction; Fitting method and goodness criterion for abundance profile; Full density/temperature profiles and mass-loss rate; Abundance profile values; IRAM 30m merging details

### 2018AJ....156..164B: Medium-sized Satellites of Large Kuiper Belt Objects (2018; solar_system; observational_alma_primary)
- question: What are the sizes and albedos of Dysnomia (Eris) and Vanth (Orcus), and do they fit the small icy collisional-satellite paradigm?
- step 2: Predict Dysnomia position and stack
  - method: Update orbit with HST data (circular fit), predict positions at ALMA epochs, shift images to predicted position and sum [4 Eris-Dysnomia: "we shift all three images to be centered on the predicted position of Dysnomia and sum them (Figure 2)."]
  - fitting: MCMC orbit fit [4 Eris-Dysnomia: "so for the final fit we constrain the orbit to be purely circular (Fig 4)."]
  - validation: Random-shift experiment gives 3.5 sigma significance [4 Eris-Dysnomia: "We find values as high as the 0.13 mJy of Dysnomia only 0.02% of the time, corresponding to a 3.5$\sigma$ likelihood that the detection is indeed Dysnomia."]
- result: Dysnomia stacked flux density = 0.13 ± ±0.03 mJy [4 Eris-Dysnomia: "A source with a flux density of 0.13$\pm$0.03 mJy appears 16 mas from the expected position"]
- result: Dysnomia detection significance = 3.5 ± not stated sigma [abstract: "we find a 3.5$\sigma$ detection of Dysnomia by stacking all of the data on the known position of the satellite"]
- limitation (authors): Dysnomia detection is weak and needs robust detection at multiple locations [Discussion: "robust detection at multiple locations are desired"]
- not stated (card): Phase calibrators, flux calibrator, and antenna numbers/baselines; AIPS imaging parameters (cell, image size, clean depth); Decorrelation correction factors per observation; MCMC sampler details, priors, chain lengths; Beaming parameter priors; Distances/heliocentric geometry for thermal model

### 2026A&A...705A.198M: The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): IV. CO gas imaging and overview (2026; debris_disks, astrochemistry; large_program_or_survey)
- question: What is the spectro-spatial distribution, optical depth and mass of CO gas in ARKS debris discs, and is CO detectable in the 13 discs without previous detections?
- step 3: Spectra and radial profiles, 12CO/13CO ratio
  - method: Gofish spectra and shifted-stacked radial profiles in 1/4-beam elliptical annuli; on-sky profiles for edge-on discs; ratio where 13CO >2 sigma [3.2 Spectral and radial profiles: "we split the disc emission into concentric elliptical annuli, $\frac{1}{4}$ of the beam’s major axis wide"]
  - software: GoFish
  - validation: Uncertainties by bootstrapping in noise-only regions [3.2 Spectral and radial profiles: "This region-drawing and averaging (bootstrapping) was repeated many times in different parts of the image"]
- step 4: Search for CO in gas-free discs by stacking
  - method: Spectro-spatial shifting/stacking of dirty cubes in both rotation directions; 3 sigma upper limits from 7 km/s bootstrapped windows [3.5 Flux and mass: "We spectrally integrated over 7 km s$^{-1}$ wide noisy regions, located in random regions of each spectrum"]
  - software: GoFish
  - assumption: Keplerian rotation, CO co-located with dust [3.3 stacking: "under the assumption of Keplerian rotation and that the CO emission is co-located with the dust emission"]
- step 5: Line fluxes and CO masses
  - method: Integrate stacked spectrum over V*±5 sigma (Gaussian fit); box integration for edge-on; optically thin LTE mass and tau=77 scaling [3.4 Flux and mass: "We set the limits of integration to $V_{*} \pm 5~\sigma$."]
  - software: GoFish
  - assumption: LTE with Tex equal to peak brightness temperature; tau12CO=77 from ISM 12C/13C [3.4 Flux and mass: "we calculate this assuming local thermodynamic equilibrium (LTE) and a CO excitation temperature equal to the peak-brightness temperature measured"]
  - fitting: Gaussian fit to stacked spectrum for centroid/width [3.3 stacking: "we fitted a Gaussian to the spectro-spatially stacked spectra"]
  - validation: Stellar velocity of HD 121617 compared with independent measurement, consistent within 3 sigma [3.3 stacking: "We found the two measured velocities to be consistent within $3~\sigma$ of each other."]
- result: 12CO J=3-2 integrated flux HD 9672 = 8.9 ± 0.9 Jy km/s [Table: "| HD 9672 | $3$ | 8.9 $\pm$ 0.9 | 3.0 $\pm$ 0.3"]
- result: 12CO integrated flux HD 32297 = 3.7 ± 0.4 Jy km/s [Table: "| HD 32297 | $68$ | 3.7 $\pm$ 0.4"]
- result: 12CO integrated flux HD 121617 = 3.6 ± 0.4 Jy km/s [Table: "| HD 121617 | $28$ | 3.6 $\pm$ 0.4"]
- result: 12CO integrated flux HD 131488 = 2.7 ± 0.3 Jy km/s [Table: "| HD 131488 | $6$ | 2.7 $\pm$ 0.3"]
- result: 12CO integrated flux HD 131835 = 1.9 ± 0.2 Jy km/s [Table: "| HD 131835 | $21$ | 1.9 $\pm$ 0.2"]
- result: Optically thin 12CO mass range = ~1-6e-4 ± not stated Earth masses [3.4 Flux and mass: "These values (Table [\[tab:linefluxesofgas\]](#tab:linefluxesofgas)) are of order $\sim1-6\times10^{-4}$ M$_{\oplus}$."]
- result: 12CO/13CO intensity ratio at 12CO peak = ~2.0-5.5 ± ±6%-33% dimensionless [3.2 Spectral and radial profiles: "intensity ratios at the radial $^{12}$CO intensity peaks of each system are $\sim 2.0 - 5.5$"]
- result: Velocity-based upper limits on 12CO inner radius = 3-68 ± not stated au [5 Conclusions: "We calculated velocity-based upper limits to the inner disc radii of $3 - 68$ au."]
- limitation (authors): Optically thick masses are lower limits; inner radii are upper limits; degeneracy thick/thin needs radiative transfer [4.2: "To break this degeneracy, radiative transfer modelling needs to be carried out"]
- not stated (card): Line-free channels / continuum subtraction approach for the line cubes; Exact nbeams and C value for each system; Clean mask thresholds and RMS estimation region; Which Measurement Sets / execution blocks per target; Gofish annulus/aperture radii used for each spectrum; Excitation temperatures per disc used in mass calculation

### 2018ApJ...853..195W: Herschel and ALMA Observations of Massive SZE-selected Clusters (2018; galaxy_clusters_and_sz, high_z_galaxies; observational_alma_primary)
- question: How do star formation, cold gas and dust, and AGN content of galaxies in massive SZE-selected clusters at 0.3<z<1.1 depend on redshift and clustercentric radius, and compare to field galaxies?
- step 5: Stack non-detections
  - method: Bootstrap stacking of PACS, ALMA continuum, ATCA and ALMA spectra at member positions with 4 MAD outlier cut; compare to blank-sky [4.1 Herschel/PACS continuum stacking: "We use bootstrapping (with replacement) to calculate stacking uncertainties or confidence intervals."]
  - parameter: 5000 bootstrap resamplings for PACS [4.1 Herschel/PACS continuum stacking: "(with 5000 resampling iterations)"]
  - validation: Blank-sky stacks and p-values [4.1 Herschel/PACS continuum stacking: "In every case, $p > 0.1$"]
- result: Stacked ISM mass limit J0102 / J0546 (3 sigma) = log M_ISM < 10.0 / < 9.9 ± not stated Msun [4.2 ALMA continuum stacking: "$\log (M_{\rm ISM}/M_\ensuremath{\odot}) < 10.0$ for J0102 and $\log (M_{\rm ISM}/M_\ensuremath{\odot}) < 9.9$ for J0546"]
- result: Stacked molecular gas mass limit (CO+[CI]) = log M_mol < 9.8 ± not stated Msun [4.4 ALMA spectral stacking: "$\log (M_{\rm mol}/M_\ensuremath{\odot}) < 9.8$ in both J0102 and J0546"]
- limitation (authors): Optical selection of members may bias the star-forming census; small samples of CO detections. [5.3 Biases from optical selection of cl…: "we have grounds for concern that our optical selection induces a general bias in our search for dust-obscured galaxies"]
- not stated (card): Which CASA clean parameters (cell size, image size, niter, threshold, mosaic gridder, masks) were used; Line-free channels used for continuum subtraction; Exact flagging/pipeline modifications beyond edge-channel flagging; Self-calibration was or was not applied; SoFiA parameter files beyond SNR 5 and 3x3 smoothing; Moment-zero channel ranges per source; Primary-beam correction details; Number of…

### 2019ApJ...871..112X: ALMA Observations of the Spatial Distribution of Three C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB> Isomers toward Sgr B2(N) (2019; astrochemistry, star_formation; archival_reuse)
- question: How do the spatial distributions and abundances of the three C2H4O2 isomers (glycolaldehyde, acetic acid, methyl formate) compare toward Sgr B2(N), using a uniform ALMA Band 3 data set and a quantitative selection of uncontaminated transit…
- step 4: Make transition maps and stacked chemical maps
  - method: Moment-8 peak intensity maps over 59-68 (low) and 70-75 km/s (high) for MF/GLA, 59-67 km/s for AcA; stack with inverse-variance weights [4.1: "For the low-velocity component, the integrated velocity range is 59-68 $\mathrm{km\ s^{-1}}$ while for the high-velocity component, the range is 70-75 $\mathrm{km\ s^{-1}}$."] [4.2: "In the stacking process, we used the inverse-variance weighting for each transition, where the variance is the square of the noise of each data cube."]
  - software: CASA
  - validation: Consistency of maps across Eu range [4.2: "Because the uncontaminated transitions covering an extensive range of upper-state energies show similar morphology, the effect of excitation conditions is ruled out"]
- result: Separation MF1-MF2 = 3.8 ± not stated arcsec [4.2: "which are connected with each other over a distance of $3.8 \ensuremath{''}$"]
- result: Separation MF3-MF4 = 8.1 ± not stated arcsec [4.2: "are separated by around $8.1 \ensuremath{''}$"]
- result: GLA2 north of GLA1 = 5.9 ± not stated arcsec [4.2: "GLA2 is $\sim 5.9 \ensuremath{''}$ north of GLA1."]
- limitation (authors): AcA morphology cannot be accurately determined due to few transitions and spatial contamination [4.1: "the morphology of AcA cannot be accurately determined based on the limited number and the spatial contamination of the transition maps."]
- limitation (authors): Spectral simulation parameters chosen subjectively [3.1: "we find that though subjective the single-excitation temperature simulations yield the most consistent fit"]
- not stated (card): Calibration details (CASA version, calibrators, flux scale) are only in Belloche et al. 2016; Continuum channel ranges per SPW not listed; Image size and deconvolution settings (niter, threshold, masks) not given; Aperture/pixel used to extract the LMH spectrum is given only as beam size and centroid; the Python simulation code is not released; Primary beam correction and how moment-8 maps were m…

### 2015MNRAS.453L..83M: ALMA and Herschel reveal that X-ray-selected AGN and main-sequence galaxies have different star formation rate distributions (2015; nearby_galaxies, agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: Do X-ray selected AGN hosts have the same SFR distribution relative to the main sequence as normal star-forming galaxies?
- step 5: compute linear-mean R_MS and compare with stacking
  - method: Monte-Carlo sampling of mu and sigma posteriors to compute linear mean [5 Interpretation: "calculating the linear mean of our log-normal distributions, taking a Monte-Carlo approach to sample the $\mu$ and $\sigma$ PDs"]
  - validation: Compared to mean-stacked Herschel 160 um results [5 Interpretation: "broadly consistent with the linear means calculated by mean-stacking *Herschel* 160 ${\rm \mu m}$ maps at the positions of our AGN"]
- result: Linear-mean <R_MS> low-z = 0.99 ± +0.23/-0.16 dimensionless [5 Interpretation: "$0.99^{+0.23}_{-0.16}$ and $1.09^{+0.47}_{-0.25}$ for our low-*z* and high-*z* samples, respectively"]
- result: Linear-mean <R_MS> high-z = 1.09 ± +0.47/-0.25 dimensionless [5 Interpretation: "$0.99^{+0.23}_{-0.16}$ and $1.09^{+0.47}_{-0.25}$ for our low-*z* and high-*z* samples, respectively"]
- limitation (authors): Log-normal is not a literal description of the true AGN distribution [4.2 Parameterising an X-ray AGN SFR dis…: "is not to be taken as a literal description of the true AGN $R_{\rm MS}$ distribution"]
- not stated (card): CASA version and calibration/imaging procedure (pipeline vs manual, weighting, cell, beam); Archive reduced products or how visibilities were calibrated for GILDAS uv_fit; Source positions/priors used in uv_fit and which sources were point vs Gaussian; Prior forms and widths, chain length and convergence criteria for the hierarchical MCMC; How upper limits and L_IR uncertainties enter the likelih…

### 2021A&A...652A..98G: The Galaxy Activity, Torus, and Outflow Survey (GATOS). I. ALMA images of dusty molecular tori in Seyfert galaxies (2021; agn_and_quasars, nearby_galaxies; large_program_or_survey)
- question: What are the sizes, orientations, masses and gas properties of dusty molecular tori in nearby Seyferts, and does AGN feedback leave an imprint on the radial distribution of molecular gas?
- step 6: Line ratios CO/HCO+ at AGN positions
  - method: Compare velocity-integrated CO(3-2) and HCO+(4-3) at AGN and stacked spectra [6: "The fairly low CO/HCO$^+$ velocity-integrated intensity ratios measured towards the AGN in these sources, $\sim2.8-5.7$"]
- result: CO/HCO+ ratios towards AGN (bright HCO+ sources) = 2.8-5.7 (4.9 stacked) ± not stated dimensionless [6: "$\sim2.8-5.7$ ($\sim4.9$ from the stacked spectra)"]
- limitation (authors): Common T_dust adopted for all sources; mass estimates depend on assumed conversion factors [4.4: "In the absence of estimates for each galaxy, we were constrained to adopt a common $T_{\rm dust}$ for all sources"]
- limitation (authors): Spectral index maps only possible for 3 sources [4.3: "meaningful spectral index maps cannot be obtained for the rest of the GATOS galaxies"]
- limitation (authors): Small-number statistics for orientation and correlations [4.5: "Within the limits imposed by the sparse statistics"]
- not stated (card): Exact line-free channels / velocity masks per target; CASA version and pipeline details, calibrators; Cell size, image size, deconvolution and cleaning thresholds in GILDAS; How CO/dust masses were integrated (apertures, noise masks); Details of the 1D-Gaussian strip fits (initial guesses); Subtraction of point source in spectral index maps and beam matching details; XSPEC fit priors/start values…

### 2016MNRAS.462.1192L: Estimating sizes of faint, distant galaxies in the submillimetre regime (2016; high_z_galaxies; archival_reuse)
- question: What are the typical sizes and flux densities of z~2 star-forming galaxies (DRG, ERO, sBzK, K20) measured by uv-stacking ALESS ALMA 344 GHz data with uv-domain model fitting?
- step 2: Subtract bright unrelated sources
  - method: Clean model from each pointing, excluding sources within 1 arcsec of stacking positions, subtracted from uv data; weights recalculated from scatter [4.1 Removing bright sources: "A model for the bright sources is built from the clean model, excluding all sources within 1$''$ of a stacking position."]
  - software: CASA 4.4
  - parameter: clean depth 1.8 mJy/beam, cell 0.2 arcsec [4.1 Removing bright sources: "cleaned down to a depth 1.8 mJy/beam"]
  - validation: Bias test with inserted point sources [Robustness of the stacked data: "By inserting and stacking point sources in the ALESS data, using the method described in section [4.4](#sec:uncertainties), we evaluate biases in the stacking result."]
- step 3: uv-stack samples
  - method: Weighted average of visibilities phase-shifted to source positions, weights = primary beam attenuation squared; astrometry shifted by 0.3 arcsec in dec [6.1 Astrometry: "all stacked datasets were phase rotated with 0$.\!\!^{\prime\prime}$3 in declination."]
  - parameter: flag baselines <18.2 m (sBzK, DRG) and <21 m (K20, ERO) [6.2 Robustness of the stacked data: "we flag all baseline shorter than $18.2\,\mathrm{m}$ for the sBzK and DRG samples"]
  - validation: Stacked all SMGs: Gaussian fit gives 4.2±0.14 mJy and 0.4±0.06 arcsec, consistent with Simpson et al. 2015 [6.2 Robustness of the stacked data: "This agrees well with (cite: simpson2015), which found typical sizes (FWHM) of SMGs between 0$.\!\!^{\prime\prime}$3 and 0$.\!\!^{\prime\prime}$4."]
- step 7: Fit dust SED and derive SFR
  - method: Modified blackbody with beta fixed 1.6, free T and L_IR, chi2 fit using stacked ALMA and Herschel SPIRE; SFR=1.3e-10 L_IR [6.4 Star-formation rates: "The value of $\beta$ is fixed to 1.6."]
  - assumption: Chabrier IMF; L_IR 8-1000 micron [6.4 Star-formation rates: "The total IR luminosity ($L_\mathrm{IR}$) is calculated between 8 $\mu$m and 1000 $\mu$m"]
  - fitting: chi2 minimization, weights sigma^-2 [Star-formation rates: "The dust emission is fitted using a $\chi^2$ minimization, with two free parameters, $T$ and $L_\mathrm{IR}$. The value of $\beta$ is fixed to 1.6. Each data point is weighted by $\sigma^{-2}$."]
  - validation: Compared to Tacconi et al. 2013 main sequence [Star-formation rates: "The measured values fall close to the best-fit “main sequence” for star-forming galaxies at similar redshifts, (e.g. the (cite: tacconi2013) parametrization for comparison)."]
- step 8: Simulate morphologies
  - method: Simulated clumpy model (3 clumps, 0.7 mJy each) and HST z-band-based model on ALESS and Cycle 3 C36-5 uv-coverage; stack identically [5.1 Clumpy morphology: "For each source in the sample we generate 3 clumps, i.e., 3 point sources."]
  - software: CASA sm
  - validation: Recovered flux 2.3±0.2 mJy vs input 2.1 mJy [Simulations: "The Gaussian model recovers an average flux density for the stacked sources of $2.3\pm0.2$ mJy, compared to the input flux density for the simulation of 2.1 mJy per source."]
- result: sBzK SFR = 86 ± 14 Msun/yr [Table 2: "sBzK & $6.7\pm1.1$ & $27\pm2$ & $86\pm14$"]
- result: DRG SFR = 102 ± 20 Msun/yr [Table 2: "DRG & $7.8\pm1.6$ & $28\pm2$ & $102\pm20$"]
- result: Simulated clumpy flux with ALESS baselines = 2.3 ± 0.2 mJy [6.4 Simulations: "The Gaussian model recovers an average flux density for the stacked sources of $2.3\pm0.2$ mJy"]
- limitation (authors): GEMS z-band less deep, possibly underestimating stellar sizes; bright source subtraction incomplete on shortest baselines [7.3: "As such is possible that we are missing low flux surface density emission, and underestimating the size of these galaxies."]
- not stated (card): Calibration details of ALESS data (pipeline/manual, CASA version of calibration, flux scale); Exact catalogue source positions and sample membership lists; Source code of the uv-stacking implementation; Details of visibility weight recalculation bin sizes; Minimizer starting values; Herschel SPIRE flux values for SED fits

### 2019ApJ...880...69Y: HL Tau Disk in HCO<SUP>+</SUP> (3-2) and (1-0) with ALMA: Gas Density, Temperature, Gap, and One-arm Spiral (2019; protoplanetary_disks, star_formation; observational_alma_primary)
- question: Does the HL Tau disk show HCO+ gas gaps coincident with the dust gaps, and what are the gas kinematics, density, temperature and surrounding spiral structure?
- step 2: Measure stellar mass and systemic velocity
  - method: Search for the Keplerian velocity pattern maximizing the S/N of the velocity-aligned stacked spectra, with absorption channels masked and only the blueshifted region (PA 48-228 deg) used [Analysis, Stellar mass and systemic vel…: "$M_\star$ and $V_{\rm sys}$ can be estimated by searching for a velocity pattern of Keplerian rotation that maximizes the S/N of the velocity-aligned stacked spectra"]
  - parameter: free parameters M_star, V_sys; PA 138 deg, i 47 deg fixed [4.1 Stellar mass and systemic velocity: "The free parameters in the analysis are $M_\star$ and $V_{\rm sys}$."]
  - assumption: geometrically thin disk [4.1 Stellar mass and systemic velocity: "The velocity patterns of Keplerian rotation were computed with the assumption of a geometrically thin disk."]
  - fitting: S/N maximization of velocity-aligned stacked spectra; uncertainty from data noise only [4.1 Stellar mass and systemic velocity: "These estimated uncertainties in $M_\star$ and $V_{\rm sys}$ only include the uncertainty due to the noise in the data."]
  - validation: Compared with previous 1.8 Msun from 13CO/C18O PV diagram; added a few percent for emitting height [4.1 Stellar mass and systemic velocity: "we estimate $M_\star$ to be 2.1$\pm$0.2 $M_\odot$."]
- step 3: Radial profiles of HCO+ (3-2) and (3-2)/(1-0) intensity ratio
  - method: Velocity-aligned stacked spectra in radial bins, Gaussian fits to (3-2), integrate both lines within 1 sigma line width, ratio in K km/s [4.2 HCO+ density and temperature profil…: "we integrated the velocity-aligned stacked spectra of the HCO$^+$ (3–2) and (1–0) emission over the channels within the 1$\sigma$ Gaussian line width from the centroid velocity"]
  - parameter: radial bin width 0.05"; innermost radius = beam 0.1" (14 au) [4.2 HCO+ density and temperature profil…: "The radius of the innermost bin is adopted to be the beam size of 0.1$''$ (14 au)"]
  - assumption: (3-2) and (1-0) trace the same volume; ratio constant within each bin [4.2 HCO+ density and temperature profil…: "we assume that the HCO$^+$ (3–2) and (1–0) emission lines trace the same volume in the HL Tau disk"]
  - fitting: Gaussian fits [Analysis, HCO$^+$ density and temperatu…: "For each radial bin, we fitted a Gaussian line profile to the velocity-aligned stacked spectrum of the HCO$^+$ (3–2) emission."]
- result: Stellar mass = 2.1 ± 0.2 Msun [abstract: "the stellar mass is estimated to be 2.1$\pm$0.2 $M_\ensuremath{\odot}$ with a disk inclination angle of 47$\ensuremath{^\circ}$"]
- result: Systemic velocity V_LSR = 7.14 ± 0.03 km/s [4.1 Stellar mass and systemic velocity: "$V_{\rm LSR}$ of 7.14$\pm$0.03 km s$^{-1}$"]
- limitation (authors): Spiral velocities depend on the assumed mid-plane location and conserved angular momentum [4.3 kinematics of the one-arm spiral: "If the spiral structure is not in the disk mid-plane or the angular momentum is not conserved, the derived profiles of the infalling and rotational velocities are not valid."]
- limitation (authors): Inner-radius line width overestimated, so column density, Tex and tau at the inner radius may be underestimated [4.2 HCO+ density and temperature profil…: "the column density, $T_{\rm ex}$, and $\tau_{\rm g}$ at the inner radius can be underestimated."]
- not stated (card): Self-calibration solution intervals and number of iterations; Line-free channels for uvcontsub and fit order; tclean cell size, image size, masks and clean threshold; Exact radial bin centers and the numeric inputs for each bin; Details of the absorption masks per radial bin; Keplerian masking parameters for the HCO+ (1-0) moment map; Spiral peak positions used in the fit; Uncertainties on the fi…

### 2015ApJ...810..133I: Compact Starbursts in z ∼ 3-6 Submillimeter Galaxies Revealed by ALMA (2015; high_z_galaxies; observational_alma_primary)
- question: Are the starburst regions of z~3-6 SMGs compact enough to be progenitors of z~2 compact quiescent galaxies, as measured by ALMA 1100-um continuum sizes?
- step 1: Select sample and estimate redshifts
  - method: 13 of 17 sources with S/N>=10 selected with z_phot>=2.8 or IRAC-faint (F4.5>=22.75 mAB) and detected in <=4 bands; minimum z from 4.5um-z relation; stacked radio/mm colour gives z=4.0 [2 AzTEC-selected z>~3 SMGs: "we analyse here only the 13 (out of 17) sources that have photometric redshifts $z_{\rm phot}\geq2.8$"]
  - assumption: Average ALESS SMG template valid at z>3 (Td=32 K) [2 AzTEC-selected z>~3 SMGs: "Here we are assuming that this template is also valid at $z\gtrsim3$–4."]
- step 4: Check with long-baseline high-res images and stacking
  - method: Image 200-1200 klambda data, imfit, compare image flux with visibility flux at 200 klambda; stack visibilities of faint sources [3.2 Ancillary long-baseline data: "we compare fluxes measured using imfit on the high-res ALMA images with fluxes expected at a $uv$-distance of $\geq200$ k$\lambda$"]
  - software: CASA imfit, stacker
  - validation: Imfit ellipticity bias tested by Monte Carlo [3.2 Ancillary long-baseline data: "imfit tends to return major/minor axis ratio of $<1$ even for input axis ratio of 1"]
- result: Median SFR = 340 ± +12/-13 Msun/yr [2 AzTEC-selected z>~3 SMGs: "340$^{+12}_{-13}$ M$_{\odot}$ yr$^{-1}$"]
- result: Image/visibility flux ratio at 200 klambda = 1.07 ± +0.08/-0.09 dimensionless [3.2 Ancillary long-baseline data: "F_{\rm image, 200\,k\lambda} = 1.07^{+0.08}_{-0.09} \times F_{\rm visibility, 200\,k\lambda}"]
- result: Stacked radio/mm photometric redshift = 4.0 ± +/-0.4 dimensionless [2 AzTEC-selected z>~3 SMGs: "we expect a photometric redshift, $z=4.0^{+0.4}_{-0.4}$"]
- limitation (authors): Large Sigma_SFR uncertainties for ~0.1" sources; only 13 sources; redshifts mostly lower limits [6 Surface SFR density: "This large uncertainty comes from the limit of size measurement in our data set."]
- not stated (card): CASA version and calibration procedure (manual vs pipeline), calibrators and flux scale; Clean parameters: weighting/robust, cell size, image size, masks, threshold; Exact model fitting of uv-amp plots (binning, fit parameter errors, uv range); Details of the size-correction probability map from simulations; Mock source parameter grid and noise generation; Conversion from L_IR/SFR (SED template, …

### 2020ApJ...905...85S: Ubiquitous Molecular Outflows in z &gt; 4 Massive, Dusty Galaxies. I. Sample Overview and Clumpy Structure in Molecular Outflows on 500 pc Scales (2020; high_z_galaxies; observational_alma_primary)
- question: How common are molecular outflows (traced by OH 119 um absorption) in z>4 lensed dusty star-forming galaxies, and what is their spatial structure on ~500 pc scales?
- step 3: Classify outflow vs not
  - method: Outflow if OH absorption is more blueshifted than detected [CII] or CO emission; compared with v50<-50 km/s criterion [3.2 Molecular Outflow Classification: "we define a source as containing an outflow if it shows OH absorption more blueshifted than the detected \[CII\] or CO emission, which we expect to be a conservative definition."]
  - assumption: systemic redshift from [CII] (5 sources) or S/N-weighted stacked CO lines [2.3 Ancillary Data: "we instead stack the spectra of all available transitions of CO for each source, weighted by the S/N of each line."]
  - validation: Binomial statistics for the detection rate; v50 alternative gives 7/11 [3.2 Molecular Outflow Classification: "would still result in 7/11 sources being classified as showing outflows"]
- step 6: Search for [CII] high-velocity wings and stack
  - method: Compare OH and [CII] profiles for four sources; stack [CII] after linear continuum subtraction excluding |v|<500 km/s, regridding and peak normalizing [5.2 [CII] is Not a Reliable Molecular O…: "We construct this stack by subtracting a linear continuum from the integrated spectrum of each source excluding velocities $|v| < 500$ $\rm{km\,s}^{-1}$"]
  - validation: Tried other stacking and continuum subtraction methods; result insensitive [5.2 [CII] is Not a Reliable Molecular O…: "We tried a variety of other stacking procedures and continuum subtraction methods and found that our result is not sensitive to these details"]
- result: Outflow detection rate = 8/11 (73%) ± ±13% percent [4.1 Molecular Outflow Detection Rate: "Assuming binomial statistics, the outflow detection rate is 73$\pm$13%."]
- result: Implied biconical opening angle = ~150 ± not stated degrees [4.1 Molecular Outflow Detection Rate: "our detection rate would correspond to an opening angle of $\sim$150$^\circ$"]
- limitation (authors): Limited ALMA bandwidth prevents detection of redshifted P Cygni emission and caps vmax [4.1 Molecular Outflow Detection Rate: "our ability to detect redshifted emission as in the classic P Cygni profile is limited due to the small ALMA bandwidth"]
- limitation (authors): Conservative classification is S/N dependent and may exclude weak outflows [3.2 Molecular Outflow Classification: "This definition has the drawback of being signal-to-noise dependent, which may exclude weak outflows"]
- not stated (card): CASA version and pipeline versions per cycle; Line-free channel ranges and continuum-subtraction method for each source; Cell size, image size, clean masks and exact tclean parameters; Self-calibration solution intervals per source and exact flux/bandpass/phase calibrators; MCMC settings (sampler, priors, chain lengths) for lens models; visilens/ripples configuration; Pixel grid sizes in source a…

### 2024A&A...688A..55M: A<SUP>3</SUP>COSMOS: Measuring the cosmic dust-attenuated star formation rate density at 4 &lt; z &lt; 5 (2024; high_z_galaxies; archival_reuse)
- question: What are the mean dust-attenuated properties (L_IR, SFR_IR, IRX relations) of mass-complete star-forming galaxies at 4<z<5, and what is the dust-attenuated cosmic SFRD?
- step 2: Stack ALMA visibilities in uv domain
  - method: Rescale visibility amplitudes to rest-frame 150 um luminosity with SED template, shift phase centres to galaxy positions, concat per stellar mass bin, tclean, read central pixel [4.1 Methods: "Finally, we measured the stacked $L_{\rm 150}^{\rm rest}$ (i.e., $\langle L_{\rm 150}^{\rm rest}\rangle$) using the central pixel value"]
  - software: CASA, STACKER
  - parameter: SED template of Bethermin et al. 2017; gencal and applycal; three mass bins [4.1 Methods: "by using the redshift of the source, the SED template of (cite: Bethermin.2017) and the CASA tasks `gencal` and `applycal`"]
  - fitting: 2D Gaussian fits as cross-check [4.1 Methods: "using instead 2D Gaussian fits at the phase center of the stacked images gave consistent $\langle L_{\rm 150}^{\rm rest}\rangle$ measurements"]
  - validation: Bootstrap, 100 realizations with replacement [4.1 Methods: "we made 100 realizations of the stacking analysis, using for each realization a different sample, drawn from the original one"]
- step 5: Fit IRX–beta, IRX–M*, SFR–M* relations
  - method: Compare stack points with Meurer/Overzier relations; linear fit of log IRX vs log M*; fit MS normalization of Schreiber 2015 [5.1 IRX: "A linear fit to our data points yields the following IRX–$M_\ast$"]
  - validation: Stacks with and without ALMA primary targets (within 3'') [3 Sample: "we therefore investigate the impact on our results of including or excluding these ALMA primary targets in our stacks"]
- result: IRX–M* fit including primary targets: slope and intercept = slope 1.1, intercept 0.67 ± +0.4/-0.4; +0.13/-0.14 dimensionless [5.1 IRX: "{\rm log_{10}\,IRX} = 1.1^{+0.4}_{-0.4}\times{\rm log_{10}}\,\Biggl(\,\frac{M_\ast}{10^{10}M_{\odot}}\Biggr)+0.67^{+0.13}_{-0.14}"]
- result: Fiducial IRX–M* relation = slope 1.45, intercept 0.56 ± not stated dimensionless [5.1 IRX: "{\rm log_{10}\,IRX} = 1.45\times{\rm log_{10}}\,\Biggl(\,\frac{M_\ast}{10^{10}M_{\odot}}\Biggr)+0.56"]
- limitation (authors): Sample may miss optically-dark heavily attenuated galaxies; ALMA primary targets bias the MS normalization [3 Sample: "this sample may still miss part of the population of optically-dark galaxies that are heavily dust attenuated"]
- not stated (card): Which individual A3COSMOS measurement sets and fields were used (the paper prints no project codes); CASA version; Image size, cell size, and tclean mask details; Exact weighting scheme for stacked visibilities beyond visibility counts; Parameters of the Schechter+power-law SMF fit and Monte Carlo setup; Details of the linear fit of IRX–M* and priors; How MS and IRX–M* uncertainties were propagat…

### 2025ApJ...984L..19Y: exoALMA. XIV. Gas Surface Densities in the RX J1604.3−2130 A Disk from Pressure-broadened CO Line Wings (2025; protoplanetary_disks; observational_alma_primary)
- question: What is the radial gas surface density and midplane pressure profile of the J1604 transition disk, derived from pressure-broadened CO J=3-2 line wings, and what does it imply for dust trapping, turbulence and planet formation?
- step 2: Azimuthally stack CO spectra
  - method: Velocity map from bettermoments, Keplerian fit with eddy for geometry, per-annulus fit of v_LOS vs azimuth, shift spectra and average over azimuth [3.1 Stacked spectra: "The original spectra are then shifted by the derived line-of-sight velocities."]
  - software: bettermoments, eddy, eddy.linecube
  - parameter: annulus width 0.05"; i = 6.0 deg fixed [3.1 Stacked spectra: "we pick up an annulus with a radial width of $0.05\ensuremath{''}$"]
  - assumption: Line wings identical along azimuth [3.1 Stacked spectra: "When stacking the spectra, we make the assumption that the line wings are identical along the azimuthal direction."]
  - validation: Tested inclinations 1, 4, 8, 11 deg and quadrant stacking; no significant difference [Appendix: CO line stacking: "As a result, no significant difference is observed, which means that our analysis is robust for the uncertainty in the geometrical parameters."]
- limitation (authors): CO/H2 ratio uncertain; absolute gas surface density scales as X_CO^-0.5 [6 Summary: "We note that the CO/H$_2$ ratio remains uncertain in this study."]
- limitation (authors): Dust opacity model uncertainty affects gas-to-dust ratio; limited spatial resolution [4.4 Caveats: "there might be a large uncertainty in the dust opacity model."]
- not stated (card): Exact exoALMA CO cube parameters (robust, taper, continuum subtraction) are only by reference to Loomis et al.; Likelihood and noise definition for the CO spectral fit (per-channel noise estimate, fit velocity range) not specified; Which radii/annuli spacing used for fits and how radial profiles are averaged/errors defined; Band 7 continuum image details and absolute flux handling; Details of Too…

### 2018ApJ...856..118H: Molecular Gas Reservoirs in Cluster Galaxies at z = 1.46 (2018; nearby_galaxies, high_z_galaxies, galaxy_clusters_and_sz; observational_alma_primary)
- question: How large are molecular gas reservoirs, gas fractions and depletion times of galaxies in the z=1.46 cluster XMMXCS J2215.9-1738 compared with field scaling relations, and how much gas remains in quiescent core galaxies?
- step 7: Stack Band 3 spectra of quiescent and star-forming galaxies
  - method: Stack spectroscopically confirmed members within 0.5 R200 shifted to rest frame; 5 sigma upper limits from 400 km/s intensity map [4.3 Molecular gas reservoirs of quiesce…: "Using the intensity map integrated in velocity by 400 km s$^{-1}$, the average CO(2–1) line flux and the 5$\sigma$ upper limit flux are estimated"]
  - validation: Procedure checked by stacking individually detected galaxies [4.3 Molecular gas reservoirs of quiesce…: "we make sure the validity of our procedure by stacking the data for the member galaxies with CO(2–1) detected individually."]
- result: Quiescent stack gas mass upper limit = <0.93e10 ± 5 sigma limit Msun [Table 3: "$<$0.93"]
- result: Quiescent stack gas fraction upper limit = <0.08 ± 5 sigma limit dimensionless [4.3 Molecular gas reservoirs of quiesce…: "the gas fraction of $<$ 0.08 and the depletion time scale of $<$ 9.8 Gyr"]
- result: Quiescent stack depletion time upper limit = <9.8 ± 5 sigma limit Gyr [4.3 Molecular gas reservoirs of quiesce…: "the gas fraction of $<$ 0.08 and the depletion time scale of $<$ 9.8 Gyr"]
- limitation (authors): Gas mass may be overestimated by ~1.5 if cluster galaxies are more metal-rich [4.1 Comparison with the scaling relatio…: "This can result in the overestimation of molecular mass by a factor of $\sim1.5$"]
- limitation (authors): Patchy Band 7 coverage so number density is a lower limit [2.2 ALMA Band 7: "the number density would be a lower limit"]
- not stated (card): Which ALMA execution blocks, CASA version and pipeline version were used; Band 7 cell size, image size, and mask details; Flux calibrator and flux scale uncertainty; Stacking procedure details (weights, rest-frame shift, velocity width); Exact Scoville2016 equation parameters and gas-to-dust ratio function; SED-fit fastpp configuration beyond the grid ranges; Tapered-map photometry choice per sou…

### 2025ApJ...988..162D: Constraining Resolved Extragalactic R<SUB>21</SUB> Variation with Well-calibrated ALMA Observations (2025; nearby_galaxies; observational_alma_primary)
- question: How does the CO(2-1)/CO(1-0) line ratio R21 vary between and within nearby galaxies at 1.7 kpc resolution, using well calibrated ALMA data, and how does it depend on SFR surface density, radius, specific SFR and metallicity?
- step 4: Measure R21 per sightline and averages
  - method: R21 = W_CO(2-1)/W_CO(1-0) for S/N>5 sightlines; average via area-weighted median, ratio-of-sums, and spectrally stacked ratio [3.1: "we include those sightlines for which both the CO(1-0) and CO(2-1) integrated intensities exceed a S/N${>}$5."]
  - software: PyStructure, PyStacker
  - parameter: 5% flux calibration uncertainty included in Gaussian error propagation [3.1: "which incorporates the channel rms and a flux calibration uncertainty of 5%"]
  - validation: Compared survey permutations (COMING, EMPIRE, NROATLAS, HERACLES, PHANGS, ALMA) [4.3: "we present the distribution of line ratio values per sightline for different combinations of surveys"]
- result: Sample-wide resolved median R21 = 0.64 ± +0.16/-0.14 (16-84th percentile) dimensionless [4.1.1: "$\langle \ensuremath{R_{21}}\rangle=0.64^{+0.16}_{-0.14}$"]
- result: Ratio-of-sums R21 = 0.70 ± ±0.05 dimensionless [4.1.1: "$\langle \ensuremath{R_{21}}\rangle_{\Sigma}=0.70^{+0.05}_{-0.05}$"]
- result: Stacked R21 = 0.71 ± ±0.05 dimensionless [4.1.1: "$\langle \ensuremath{R_{21}}\rangle_{\rm stacked}=0.71^{+0.05}_{-0.05}$"]
- result: Central (r<=2 kpc) R21 = 0.75 ± +0.09/-0.12 dimensionless [4.1.1: "$\langle \ensuremath{R_{21}}\rangle_{\rm center}=0.75^{+0.09}_{-0.12}$"]
- limitation (authors): Small sample; individual outliers can affect galaxy-to-galaxy trends [4.1.1: "Given the small number of galaxies within our sample, we caution, however, that individual outliers can affect the observed trends."]
- limitation (authors): Metallicity covers only ~0.25 dex and 8 galaxies [4.1.2: "we only cover a small dynamical range of metallicities (${\sim}$0.25 dex)"]
- not stated (card): Exact bin edges and bin widths for r_gal, SFR surface density, sSFR and metallicity; Regression method for binned fits and how the uncertainties on m and q were derived; Details of the fit to all sightlines (slope 0.11) and treatment of uncertainties; Spectral setup, channel width and line-free channels for the CO(1-0) cubes; Robust weighting, cell size and image size used by the PHANGS pipeline;…

### 2020A&A...640A..27V: Protoplanetary disk masses in NGC 2024: Evidence for two populations (2020; protoplanetary_disks, star_formation; observational_alma_primary)
- question: How does external photoevaporation and environment affect the dust masses of disks across the young NGC 2024 cluster, compared with other star-forming regions?
- step 4: Search for new sources and stack nondetections
  - method: Blind search for >4.8σ peaks checked in both images; weighted stack of 122 nondetections with detections masked [3.2.3 Point sources without near infrar…: "These sources were first identified by performing a blind search for $>4.8\,\sigma$ peaks in the data"]
  - validation: 4.8σ chosen to give <1 expected false positive (0.6) [3.2.3 Point sources without near infrar…: "we expect less than one false positive given the number of independent beams in the full image (0.6 on average)."]
- result: Stacked nondetection 3σ limit = 20 uJy (<0.96 M_Mars) ± not stated uJy [3.2.4 Stacking analysis of nondetections: "The resulting $3\sigma$ mass limit for the stacked sources is $20\,\mu$Jy, or $< 0.96\,M_{\text{Mars}}$."]
- limitation (authors): Stellar mass differences and binarity cannot be accounted for in the comparison [4.2 Comparison to other star-forming re…: "we cannot take into account possible differences in stellar masses, even though these may be significant"]
- limitation (authors): Kaplan-Meier assumption of nondetection independence not met at low masses [3.2 Dust masses of NGC 2024 disks: "The third requirement is not met"]
- not stated (card): tclean cell size, image size, deconvolver, threshold and masks; Line-free channels flagged; Self-calibration solution intervals and reference antenna; Details of aperture photometry (aperture size, background); Which Kaplan-Meier implementation was used; How spectral indices of IRS 2 and IRC 101 were computed; CASA calibration pipeline version and manual vs pipeline calibration

### 2021ApJ...908...54W: ALMA Measures Rapidly Depleted Molecular Gas Reservoirs in Massive Quiescent Galaxies at z ∼ 1.5 (2021; nearby_galaxies, high_z_galaxies; observational_alma_primary)
- question: How much molecular gas (CO(2–1)) do massive quiescent galaxies at z~1.5 retain, and what does this imply for quenching, depletion times and models?
- step 4: Stack the five non-detections
  - method: weighted mean of 400 km/s channel maps (non-PB-corrected) at CO(2–1) rest frequency of each galaxy [2.4 Stack of non-detections in CO(2–1): "We calculate the weighted average (mean) to account for the slight differences in map rms"]
  - parameter: mean z=1.476; 400 km/s bins [2.4 Stack of non-detections in CO(2–1): "We use the mean redshift of the non-detected galaxies ($<z>$=1.476)"]
- result: Stack f_H2 (3sigma) = <1.6 ± not stated % [2.4 Stack of non-detections in CO(2–1): "this puts a 3$\sigma$ upper limit on the molecular gas fraction of 1.6%"]
- result: Stack M_H2 (3sigma) = <4.7e9 ± not stated Msun [2.4 Stack of non-detections in CO(2–1): "$M_{\rm{H_{2}}}$$<4.7\times10^{9}$$\rm{M}_\odot$(3$\sigma$)"]
- result: Stack rms = 25.6 ± not stated uJy/beam [2.4 Stack of non-detections in CO(2–1): "an rms noise limit of 25.6$\mu$Jy/beam for the 400 km/s channel width of the stack"]
- limitation (authors): Mostly upper limits on M_H2 and SFR preclude robust depletion time measurement [4.2 Timescales for gas consumption or d…: "our dataset precludes a robust measurement of (current) depletion times"]
- limitation (authors): alpha_CO uncertainty of factor >=2 [2.3 Molecular gas measurements: "a factor of $\gtrsim$2 uncertainty due to the assumed value of the CO-H$_{2}$ conversion factor"]
- not stated (card): Exact tclean/CASA version and task parameters (robust, niter, threshold per source); Precise line-free channels and continuum subtraction method; Positions of offset sources fixed in uvmultifit for 22260 and 34879; Exact velocity widths used per galaxy for upper limits; Prospector configuration details beyond default priors; Model parameters for the bathtub and toy-model calculations; SIMBA selec…

### 2025A&A...700A.285W: Gravitational torques from lopsided young stellar component sustain high black hole accretion rates in NGC 4593 (2025; agn_and_quasars, nearby_galaxies; observational_alma_primary)
- question: What secular mechanism drives high SMBH accretion rates in NGC 4593, from kpc-scale gas down to the SMBH sphere of influence?
- step 6: Decompose HST UV image
  - method: PSF subtraction using stacked standard-star PSFs and single-Sérsic fit of diffuse component with galight [3.6.1 Photometric decomposition: "we employed the open-source software `galight` [^4] (cite: Ding:2020), which uses the two-dimensional image modelling provided by `lenstronomy`"]
  - software: galight, lenstronomy, L.A.Cosmic
  - parameter: uniform priors 0.01''<Reff<4.0'', 0.3<n<9; innermost 0.2'' masked [3.6.1 Photometric decomposition: "Uniform priors were applied to the effective radius $0.01\ensuremath{''} < R_{\rm eff} < 4.0\ensuremath{''}$"]
  - fitting: galight MCMC [3.6.1 Photometric decomposition: "derived from `galight`’s Markov chain Monte Carlo decomposition"]
  - validation: Feature persists with different PSF subsets and 90° rotation [3.6.1 Photometric decomposition: "the extended feature near the centre persists."]
- result: Offset of young stellar component from AGN = 258 ± 14 pc [5 Summary and conclusions: "offset from the AGN by $258 \pm 14 \,{\rm pc}$"]
- limitation (authors): Torque method unvalidated by simulations, configuration likely unstable [3.7.2 Torques from the young stellar co…: "First, the configuration is likely unstable over time."]
- limitation (authors): Mass of young component is poorly constrained from single UV band; closed-box and alpha_CO assumptions [3.6.2 Mass of the young stellar compone…: "Thus, we were limited to a flux measurement in the F330W filter."]
- not stated (card): CASA tclean parameters (cell, image size, mask, niter, threshold), line-free channels, and rest frequency; ALMA calibration/pipeline version and flux calibrator details for both programs; Whether CASA was used for the joint imaging of the combined cube; KinMS_fitter prior ranges, number of walkers and burn-in; skySampler settings; Aperture and masks used to measure total CO flux and M_mol; Spiral…

### 2017ApJ...843...27L: Formation and Atmosphere of Complex Organic Molecules of the HH 212 Protostellar Disk (2017; star_formation, astrochemistry; observational_alma_primary)
- question: Where does a Keplerian disk form inside the infalling-rotating envelope of HH 212, and do the complex organic molecules trace the disk atmosphere (formed in the disk) or a rapidly infalling warm inner envelope?
- step 3: Map COM emission and PV structure in the disk atmosphere
  - method: Stack lines of the same molecule for integrated-intensity maps; PV cuts parallel and perpendicular to the disk plane [3.2 Tracing Disk Atmosphere with COMs: "Since the emission morphology is similar, the maps of the same molecule are stacked together to make a map with a higher S/N ratio."]
  - fitting: Single linear fit to the linear PV structures in methanol and deuterated methanol [3.2 Tracing Disk Atmosphere with COMs: "which are obtained from a single linear fit to the linear PV structures seen in both methanol and deuterated methanol"]
- limitation (authors): Tex is poorly constrained because data points are scattered at low S/N; may be underestimated by factor ~2 [3.4 Physical condition in the disk atmo…: "Since the data points are scattered due to the low S/N ratio, the fitting results have a big uncertainty in excitation temperature."]
- limitation (authors): Disk is optically thick in dust so molecules near the midplane cannot be probed [Conclusions: "Whether such molecules exist closer to the disk midplane cannot be determined for the nearly edge-on disk of HH 212 that is optically thick in dust continuum."]
- not stated (card): CASA version and whether archive or manual calibration scripts were used; Self-calibration details and how Cycle 1 and 3 data were aligned/combined; Line-free channels and continuum subtraction method; Cell size, image size, deconvolver, masks, cleaning thresholds; Beam sizes and position angles for each map; Details of the line stacking and integration velocity ranges; How the model PV boundarie…

### 2019A&A...630A..59B: Widespread QSO-driven outflows in the early Universe (2019; agn_and_quasars, high_z_galaxies; archival_reuse)
- question: Do high-z QSOs show faint broad [CII] wings tracing cold outflows, detectable by stacking archival ALMA [CII] data?
- step 3: Stack spectra and cubes
  - method: Variance-weighted stack with weights 1/sigma^2 per channel after aligning at [CII] rest frequency and centering on continuum peak; both 1D spectra and 3D cubes [Methods: "We applied a standard variance-weighted stacking, i.e. we used a weighting factor $w_{\rm j,k}=1/\sigma_{\rm j,k}^2$"]
  - parameter: n=48; channels with atmospheric transmission <0.5 excluded [Methods: "We did not include in the stack spectral regions corresponding to an atmospheric transmission $<0.5$ for a 1 mm precipitable water vapour."]
  - validation: Stacks of 100 empty positions gave spurious SNR ~0.4; 1000 jackknife stacks excluding 5 sources gave ~11% mean luminosity variation [Methods: "This resulted into an average spurious signal-to-noise ratio of $\sim0.4$ for the stack of the total sample."]
- step 5: Size of outflow from stacked cube
  - method: Beam-deconvolved half-light radius of |v|>400 km/s map [4.4 Stacked Cube: "We derived a beam-deconvolved half light radius $R_{\rm out} = \sqrt{(R_{\rm 50\%}^2 - R_{\rm beam}^2})\sim 0.60$ arcsec"]
  - validation: Repeated with cubes tapered to 1.2 arcsec [4.4 Stacked Cube: "we derived a beam-corrected half light radius $R_{\rm out}^{\rm taper} \sim 4.6$ kpc"]
- result: Outflow radius R_out = ~3.5 ± not stated kpc [4.4 Stacked Cube: "$R_{\rm out}$ corresponds to $\sim3.5$ kpc at $\langle z_{\rm stack}\rangle$."]
- result: Sensitivity improvement vs Cicone15 J1148+5251 = ~14 ± not stated dimensionless [4.1 Stacked spectrum: "a factor of $\sim14$ lower than that of the J1148$+$5251 observations of (cite: Cicone15)"]
- limitation (authors): Interferometric data may miss extended diffuse emission; stacking dilutes orientations [Conclusions: "we cannot exclude that additional, more extended emission is present but missed by the interferometric data used for the stacking."]
- not stated (card): List of the 48 QSOs with per-source flux scaling/calibration corrections (table not in text); Exact clean threshold and iteration count per source; Which sources were calibrated manually vs pipeline; Exact aperture definition/centering and handling of channels with partial coverage; Initial guesses for the Gaussian fits; How the 100 empty positions were chosen; Fruchter&Hook-based cube regridding…

### 2017A&A...601A...4A: Growth of carbon chains in IRC +10216 mapped with ALMA (2017; evolved_stars, astrochemistry; observational_alma_primary)
- question: How do linear carbon chains (polyynes and cyanopolyynes) form and grow in the envelope of the C-star IRC +10216, and where are they located radially?
- step 1: Map line emission of carbon chains
  - method: Merge ALMA compact+extended data with IRAM 30m after continuum subtraction; map channel at Vsys averaged over 3 km/s; stack 19 C6H lines using compact data only [2 Observations: "stacked the maps of a selected list of 19 lines, all free of blending and observed with a sufficient quality"]
  - validation: Compared different transitions of same species (Appendix) [Appendix: Emission maps in different ro…: "Here we present the emission maps of each individual line and discuss whether the different lines of a given species have brightness distributions significantly different among them"]
- result: Shell width (overall) = 5-10 ± not stated arcsec [abstract: "a hollow, 5-10$''$ wide, spherical shell located at a radius of 10-20$''$ from the star"]
- result: Sub-shell width = 1-2 ± not stated arcsec [abstract: "thinner sub-shells which are 1-2$''$ wide and not fully concentric"]
- limitation (authors): Spherical isotropic model cannot reproduce arcs; comparison only first order; IR pumping uncertain for C4H, C6H, C3N [5 Discussion: "the comparison between the calculated and observed emission distributions can only be done to first order, and not at the sub-arcsecond level"]
- not stated (card): ALMA/CASA calibration and imaging procedure, versions, weighting, cell/image size; Details of merging with IRAM 30m data; Line-free channels and continuum subtraction method; Exact synthesized beams and rms for C6H stacked map and list of 19 C6H lines; Method of azimuthal averaging and strip extraction; Chemical network files and IR pumping parameters for full reproduction; Flux calibrator and ca…

### 2017ApJ...839L..15G: Discovery and Physical Characterization of a Large Scattered Disk Object at 92 au (2017; solar_system; multi_facility_alma_minor)
- question: What are the orbit, size and albedo of the newly discovered distant TNO 2014 UZ224, using DES discovery data and ALMA thermal emission?
- step 1: Stack and image ALMA continuum
  - method: Stack five calibrated data sets with fixplanet, CLEAN with natural weighting [Measurement of Thermal Emission, Size, …: "The calibrated visibilities of five data sets were then stacked to align the position using the `fixplanet` command."]
  - software: CASA
- limitation (authors): Single-wavelength measurement prevents fitting eta [Measurement of Thermal Emission, Size, …: "However this is not possible with a single-wavelength measurement"]
- not stated (card): Cell size, image size, number of iterations and clean threshold; Ephemeris used and how the five data sets were stacked (fixplanet parameters); Image rms; Number of Monte Carlo draws' flux input values (optical flux uncertainty) and solar V magnitude; Self-calibration status

### 2018ApJ...861....7F: ALMA 26 Arcmin<SUP>2</SUP> Survey of GOODS-S at One Millimeter (ASAGAO): Average Morphology of High-z Dusty Star-forming Galaxies in an Exponential Disk (n ≃ 1) (2018; high_z_galaxies; observational_alma_primary)
- question: What are the average rest-frame FIR Sérsic index and effective radius of faint dusty star-forming galaxies at z=1-3, and how do they compare with the rest-frame optical morphology and with compact quiescent galaxies?
- step 4: Stack 33 z=1-3 sources in uv plane
  - method: visibility stacking centered on LR peak positions [3.4 Visibility-based Stacking: "we use only 33 ASAGAO sources that are located at $z=1-3$ for the stacking"]
  - software: stacker
  - validation: 29 sigma peak [3.4 Visibility-based Stacking: "shows a 29$\sigma$ significance level"]
- step 5: Fit Sérsic profile to stack
  - method: galfit on 1.6"x1.6" HR map with synthesized beam image as PSF; cross-check with uvmultifit at n=1 [3.5 n_FIR and R_e,FIR Measurements: "We adopt $n=1$, $R_{\rm e}=0.2\ensuremath{''}$, total flux density of 1.0 mJy, axis ratio of 1.0, and position angle of 0 deg as initial parameters"]
  - software: galfit, uvmultifit
  - parameter: sky fixed at 0; center fixed at image center [3.5 n_FIR and R_e,FIR Measurements: "where the sky value is fixed at 0. The source center is fixed at the image center."]
  - fitting: galfit chi-square; errors by bootstrap [3.5 n_FIR and R_e,FIR Measurements: "where the errors are evaluated by the bootstrap method"]
  - validation: uvmultifit Re=0.10"+-0.03" consistent [3.5 n_FIR and R_e,FIR Measurements: "The best-fit $R_{\rm e,FIR}$ is estimated to be $0.10\ensuremath{''}\pm0.03\ensuremath{''}$"]
- step 8: Archive bright SMG sizes
  - method: galfit individually, no stacking correction [3.6 Additional Sample from Archive: "The $n_{\rm FIR}$ and $R_{\rm e, FIR}$ values are individually estimated with galfit in the same manner as the stacked source"]
  - software: galfit
- step 10: Model evolution to compact quiescent galaxies
  - method: Sum of Sigma Mstar and Sigma SFR(UV+FIR) x dt; HST F606W stacking for UV profile [5.2 Evolutions of Size and Morphology: "estimated from the sum of the $\Sigma M_{\rm star}$ and $\Sigma$SFR$_{\rm UV+FIR}$$\times$$\Delta t$"]
  - software: galfit
  - parameter: dt = depletion time (~640 and 210 Myr) or ~1.0 Gyr [5.2 Evolutions of Size and Morphology: "The depletion times are estimated to be $\sim$ 640 and 210 ${\rm Myr}$ for the high-$z$ LIRGs and ULIRGs, respectively."]
  - assumption: constant SFR, no radial motions of stars [5.2 Evolutions of Size and Morphology: "Assuming a constant SFR during a time scale $\Delta t$ and no radial motions of the stars"]
  - validation: compared with z~1-2 quiescent galaxy distributions [5.2 Evolutions of Size and Morphology: "For comparison, the distributions of $z\sim2-3$ star-forming and $z\sim1$$-$2 quiescent galaxies are also presented with the blue and black shaded regions, respectively."]
- result: Stack n_FIR (galfit, uncorrected) = 0.96 ± 0.10 dimensionless [3.5 n_FIR and R_e,FIR Measurements: "$n_{\rm FIR}=0.96\pm0.10$ and $R_{\rm e,FIR}=0.11\ensuremath{''}\pm0.02\ensuremath{''}$"]
- result: Archive sample median n_FIR = 1.1 ± 0.3 dimensionless [3.6 Additional Sample from Archive: "$n_{\rm FIR}=1.1\pm0.3$ and $R_{\rm e, FIR}=1.3\pm0.8$ kpc"]
- result: Archive sample median R_e,FIR = 1.3 ± 0.8 kpc [3.6 Additional Sample from Archive: "$n_{\rm FIR}=1.1\pm0.3$ and $R_{\rm e, FIR}=1.3\pm0.8$ kpc"]
- result: Stack S/N = 29 ± not stated sigma [3.4 Visibility-based Stacking: "shows a 29$\sigma$ significance level"]
- limitation (authors): Cannot distinguish n~1 vs 4 beyond r>0.4" [3.5 n_FIR and R_e,FIR Measurements: "one cannot conclude whether $n_{\rm FIR}\sim1$ or $n_{\rm FIR}\sim4$ is preferable in the range of radius $r>0.4\ensuremath{''}$"]
- not stated (card): Robust/weighting details and channel selection for continuum imaging; calibration pipeline/CASA version; Which archive projects map to which of the 12 additional sources; Bootstrap details for galfit errors and exact MC correction tables; Self-calibration and flux scale details; gas fraction and SFR/Mstar profile model details for evolution calculation; Stacker settings and weighting

### 2016ApJ...823L..10W: First Detection of Gas-phase Methanol in a Protoplanetary Disk (2016; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: Is gas-phase methanol present in the TW Hya protoplanetary disk, and what are its abundance and radial location?
- step 2: Stack three B7 methanol lines in uv domain
  - method: Concatenate after velocity regridding and image with natural weighting [OBSERVATIONS: "imaged using CLEAN with natural weighting (i.e., “stacked” in the uv domain)"]
  - software: CASA
- step 3: Model abundance and location
  - method: Grid of LIME LTE models varying inner/outer radius (10 AU steps), abundance and vertical layer; compare stacked line profile and channel maps [Constraining the methanol abundance: "A small grid of models were run in which the inner and outer radius of the emission were varied (in steps of 10 AU)"]
  - software: LIME
  - parameter: layers z/r<=0.1, 0.1-0.2, 0.2-0.3 [Constraining the methanol abundance: "$z/r \le 0.1$, $0.1 \le z/r \le 0.2$, and $0.2 \le z/r \le 0.3$"]
  - assumption: LTE; Kama et al. disk structure [Constraining the methanol abundance: "assuming LTE"]
  - fitting: Best by-eye fit [Constraining the methanol abundance: "The results for the best “by-eye” fit to the data"]
  - validation: Models reproduce B6 non-detection [Constraining the methanol abundance: "reproduce the non-detection in the B6 data"]
- result: Peak S/N of stacked B7 emission = 5.5 ± not stated sigma [OBSERVATIONS: "reaching a peak S/N of $5.5\sigma$"]
- result: Fiducial midplane CH3OH abundance (30-100 AU ring) = 2.8e-12 ± ~20% relative to H2 [Constraining the methanol abundance: "with a fractional abundance of $2.8\times10^{-12}$ relative to"]
- result: Abundance in 0.1<z/r<0.2 and 0.2<z/r<0.3 = 8.0e-12; 4.4e-11 ± not stated relative to H2 [Constraining the methanol abundance: "fractional abundances of $8.0\times10^{-12}$ and $4.4\times10^{-11}$"]
- result: Peak column density at 30 AU = 3-6e12 ± not stated cm^-2 [Constraining the methanol abundance: "peak column density of $\approx 3 - 6 \times 10^{12}$ cm$^{-2}$ at 30 AU"]
- result: Stacked line peak flux density = 33 ± rms 6.5 mJy [Detection of gas-phase methanol: "The peak flux density for the stacked line profile is 33 mJy and the rms noise is 6.5 mJy"]
- limitation (authors): Low S/N precludes detailed modeling; vertical location unconstrained [Constraining the methanol abundance: "The low S/N of the B7 detection precludes more detailed modeling."]
- not stated (card): Line-free channels and continuum subtraction method; Image size and cell size; Which B7 transitions are stacked beyond approximate frequencies; velocity regridding details; Aperture/mask for spectrum extraction beyond the 3 sigma continuum contour; LIME settings (photons, grid) and methanol temperature/excitation assumptions; Exact fit criterion (by eye)

### 2014ApJ...785..149S: The Rest-frame Submillimeter Spectrum of High-redshift, Dusty, Star-forming Galaxies (2014; high_z_galaxies, astrochemistry; archival_reuse)
- question: What is the average rest-frame 250-770 GHz spectrum of lensed SPT dusty star-forming galaxies, and what ISM conditions do its faint lines (13CO, HCN, HNC, HCO+, CN) imply?
- step 3: Build template and line-centred stacked spectra
  - method: Inverse-variance weighted average on a 500 km/s grid (240-780 GHz) and in 600 km/s channels centred on each target line; detection if central channel S/N>3 [3 Stacking Methods: "We classify a line as detected if the line flux in the 0 km/s channel has $S/N > 3$."]
  - parameter: 500 km/s grid; 600 km/s line channels [3 Stacking Methods: "The grid is constructed with 500 km/s spacing"]
  - validation: Monte Carlo of 3000 channel shufflings at line-free 513 GHz shows Gaussian noise; <0.3 false detections expected [3 Stacking Methods: "we expect $<0.3$ false detections in the $\sim$100 line frequencies we search."]
- result: Stacked 13CO(3-2) L' = 12.8 ± 3.6 1e9 K km/s pc^2 [Table 2: "$^{13}$CO(3-2) | 330.5880 | 5 | **12.8 $\boldsymbol{\pm}$ 3.6**"]
- result: Stacked 13CO(4-3) L' = 12.6 ± 3.0 1e9 K km/s pc^2 [Table 2: "$^{13}$CO(4-3) | 440.7652 | 9 | **12.6 $\boldsymbol{\pm}$ 3.0**"]
- result: Stacked HCN(4-3) L' = 13.4 ± 3.2 1e9 K km/s pc^2 [Table 2: "HCN(4-3) | 354.5055 | 6 | **13.4 $\boldsymbol{\pm}$ 3.2**"]
- result: Average CCH L' per transition = 7.8 ± 1.9 1e9 K km/s pc^2 [Table 3: "CCH | 6 | 34 | **7.8 $\boldsymbol{\pm}$ 1.9**"]
- result: Average CH L' per transition = 11.3 ± 3.4 1e9 K km/s pc^2 [Table 3: "CH | 2 | 20 | **11.3 $\boldsymbol{\pm}$ 3.4**"]
- result: L'HCN(4-3)/L'CO(1-0) = 0.045 ± not stated dimensionless [5.2: "we find $L^{'}_\mathrm{HCN}(4-3) / L^{'}_\mathrm{CO}(1-0) = 0.045$"]
- limitation (authors): Single-component modelling of a heterogeneous sample; no single model fits (chi2 min 10.4 for 3 dof); degeneracies remain; differential magnification not accounted [4.1: "This likely reflects the simplicity of the modeling procedure, which represents a heterogeneous collection of galaxies as a single, homogeneous gas component of simple geometry."]
- not stated (card): Calibrator names and flux scale uncertainty of the Cycle 0 data; CASA version and exact calibration scripts; Per-source SED fit parameters and photometry used for 1.4 mm scaling; Exact interpolation scheme onto the 500 km/s grid; RADEX grid sampling steps, likelihood and posterior/marginalisation details, K_vir cutoff; Source coordinates; Which sources are included for each line, beyond N_sources…

### 2020A&A...633A.160C: The ALMA Frontier Fields Survey. V. ALMA Stacking of Lyman-Break Galaxies in Abell 2744, Abell 370, Abell S1063, MACSJ0416.1-2403 and MACSJ1149.5+2223 (2020; high_z_galaxies, galaxy_clusters_and_sz; large_program_or_survey)
- question: What are the IR properties and IR excess (IRX) of UV-selected LBGs at z~2-8 behind five Frontier Fields clusters, individually and via stacking, and how do they compare with IRX-beta and IRX-M* relations?
- step 5: Select stacking sample
  - method: Remove beta outliers, sources near >=4 sigma detections, pbcor<0.5, the 2 detections, multiple images, low mass, redshift mismatches [3.1 Target final sample: "We summarize our selection criteria in Table [1](#tab:filter), which resulted in a sample of $1580$ undetected LBG candidates to stack"]
- step 6: Stack ALMA uv data and IRX
  - method: STACKER uv-stacking with four weights (equal, pbcor^2, pbcor^2*F_UV^2, pbcor^2*mu^2) in bins of beta, M*, z; IRX stacked as mean of individual IRX; upper limits from stacked peak + n x error [3.2 Stacking: "We adopted four different weighting schemes for the stacking code and further analysis"]
  - software: STACKER
  - parameter: 5 beta bins, 9 mass bins, 3 z bins [3.2 Stacking: "With UV-slope, targets were stacked in five bins and, for stellar mass, in nine bins."]
  - validation: Test stacking of 12 robustly detected DSFGs recovers 39.1 sigma etc. [Appendix A: "yields stacked detections of 39.1–$\sigma$, 37.3–$\sigma$, 29.9–$\sigma$, and 7.1–$\sigma$, for equal, $pbcor$, $F_{\mathrm{UV}}$, and $\mu$-weighting"]
- result: LBG candidates analysed = 1582 ± not stated sources [2.2 LBG candidates: "we investigate the properties of the $1582$ candidates located within the FoVs of five ALMA-observed FFs."]
- result: Undetected LBGs stacked = 1580 ± not stated sources [3.1 Target final sample: "which resulted in a sample of $1580$ undetected LBG candidates to stack"]
- result: Best stacked bin S/N (227 F_UV-weighted, 4<=z<7, -2<=beta<-1, natural) = 4.24 ± not stated dimensionless [4.2 Stacking results: "$227$ $F_{\mathrm{UV}}$-weighted sources in the range $4.0 {\leq} z {<} 7.0$ and $-2.0 {\leq} \beta {<} {-}1.0$ with $\mathrm{S/N}_{\mathrm{peak}}^{\mathrm{stack}} {=} 4.24$"]
- result: Lowest stacked rms = ~5 ± not stated uJy [4.2 Stacking results: "we achieve stacked $rms$ values as low as $\approx$5 $\mu$Jy"]
- limitation (authors): Stellar masses below ~10^8.5 Msun likely incomplete; selection biases at low mass [5.1.5 M-beta correlation: "we could have strong selection effects that bias the resulting fitted relations at low stellar masses."]
- limitation (authors): Stacked values biased toward high-weight sources [3.3 Considerations on stacking weighting: "our stacked result can be biased toward the candidates with the highest weights."]
- not stated (card): CLEAN parameters (robust/threshold/niter/cell/image size, masking) for the mosaic images; Exact B19 LBG catalog (in prep) needed to reproduce the sample; Dust temperature formula parameters and SED normalization details; STACKER run parameters; Flux calibrators and flux scale uncertainty; Exact bin assignment of the 4.0>=z<=7.0 boundary and how 1580 vs 1582 sources were handled; Weights/treatment…

### 2026ApJ..1000..308W: The ALPINE-CRISTAL-JWST Survey: Chemical Abundance Comparison between the ISM and CGM of Main-sequence Galaxies at z = 4─6 (2026; high_z_galaxies; multi_facility_alma_minor)
- question: Do the chemical abundances (strong optical line ratios) of the ISM (<~3 kpc) and CGM (~5-10 kpc) differ in main-sequence galaxies at z=4-6?
- step 2: Fit emission lines in stacked spectra
  - method: Single Gaussian fits per line with q3dfit; 100 Monte Carlo cube realizations for uncertainties; extinction correction using Balmer decrement [3.2 Spectral fitting: "To obtain the uncertainties of the fitted quantities, a Monte Carlo (MC) procedure was adopted where we generated $100$ realizations of the data cubes"]
  - software: q3dfit, LMFIT
  - parameter: [O II] doublet ratio fixed to unity; [O III] and [N II] doublets fixed to 1/3 [3.2 Spectral fitting: "We further fix the doublet line ratio of $F_{\rm [\textup{O\,\textsc{\lowercase{iii}}}]\lambda4959}/F_{\rm [\textup{O\,\textsc{\lowercase{iii}}}]\lambda5007}$"]
  - assumption: Case B Halpha/Hbeta=2.86, Calzetti curve, f=0.56 [3.2 Spectral fitting: "by applying a case B ratio of $2.86$ (cite: Cardelli_1989) and a Calzetti attenuation curve (cite: Calzetti_2000)"]
  - fitting: [C II] fit with LMFIT in same masks [3.2 Spectral fitting: "The \[C II\] emission observed by ALMA is extracted in the same ISM and CGM masks and fit in a similar way using `LMFIT`"]
  - validation: G235M vs G395M fluxes compared (~6% difference) [3.2 Spectral fitting: "we find that the ones from G395M are higher by $\sim6\%$."]
- limitation (authors): Small sample; results to be treated with caution [4.1 Statistical tests: "Due to the relatively small sample, we note that the results should be treated with caution."]
- not stated (card): ALMA calibration, CASA version, and imaging parameters (cell, size, masks, continuum subtraction); Exact ISM/CGM mask definitions per galaxy and merger cuts; q3dfit configuration (fixed redshifts and widths, continuum model); Per-galaxy fluxes and ratios table; Cloudy input files and detailed settings

## All papers in this technique

- 2013ApJ...768...91H (2013): An ALMA Survey of Submillimeter Galaxies in the Extended Chandra Deep Field South: Source Catalog and Multiplicity
- 2014ApJ...780..115D (2014): An ALMA Survey of Sub-millimeter Galaxies in the Extended Chandra Deep Field South: Sub-millimeter Properties of Color-selected Galaxies
- 2014ApJ...783...84S (2014): The Evolution of Interstellar Medium Mass Probed by Dust Emission: ALMA Observations at z = 0.3-2
- 2014ApJ...785..149S (2014): The Rest-frame Submillimeter Spectrum of High-redshift, Dusty, Star-forming Galaxies
- 2014ApJ...788..125S (2014): An ALMA Survey of Submillimeter Galaxies in the Extended Chandra Deep Field South: The Redshift Distribution and Evolution of Submillimeter…
- 2014MNRAS.442..577T (2014): An ALMA survey of submillimetre galaxies in the Extended Chandra Deep Field South: radio properties and the far-infrared/radio correlation
- 2015ApJ...810..133I (2015): Compact Starbursts in z ∼ 3-6 Submillimeter Galaxies Revealed by ALMA
- 2015ApJ...811L...3T (2015): SXDF-ALMA 1.5 arcmin<SUP>2</SUP> Deep Survey: A Compact Dusty Star-forming Galaxy at z = 2.5
- 2015MNRAS.453L..83M (2015): ALMA and Herschel reveal that X-ray-selected AGN and main-sequence galaxies have different star formation rate distributions
- 2015Natur.522..455C (2015): Galaxies at redshifts 5 to 6 with systematically low dust content and high [C II] emission
- 2016ApJ...819...82S (2016): Properties of the Interstellar Medium in Star-Forming Galaxies at z ~ 1.4 Revealed with ALMA
- 2016ApJ...820...83S (2016): ISM Masses and the Star formation Law at Z = 1 to 6: ALMA Observations of Dust Continuum in 145 Galaxies in the COSMOS Survey Field
- 2016ApJ...823L..10W (2016): First Detection of Gas-phase Methanol in a Protoplanetary Disk
- 2016ApJ...828...46A (2016): ALMA Survey of Lupus Protoplanetary Disks. I. Dust and Gas Masses
- 2016ApJ...831..101B (2016): Hydrocarbon Emission Rings in Protoplanetary Disks Induced by Dust Evolution
- 2016ApJ...832..204Y (2016): Stacking Spectra in Protoplanetary Disks: Detecting Intensity Profiles from Hidden Molecular Lines in HD 163296
- 2016ApJ...833...68A (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Continuum Number Counts, Resolved 1.2 mm Extragalactic Background, and Proper…
- 2016ApJ...833...72B (2016): ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: The Infrared Excess of UV-Selected z = 2-10 Galaxies as a Function of UV-Continuu…
- 2016ApJ...833..195W (2016): The SXDF-ALMA 2-arcmin<SUP>2</SUP> Deep Survey: Stacking Rest-frame Near-infrared Selected Objects
- 2016MNRAS.462.1192L (2016): Estimating sizes of faint, distant galaxies in the submillimetre regime
- 2017A&A...599A.134S (2017): The ALMA Redshift 4 Survey (AR4S). I. The massive end of the z = 4 main sequence of galaxies
- 2017A&A...601A...4A (2017): Growth of carbon chains in IRC +10216 mapped with ALMA
- 2017A&A...607L...5Q (2017): Clues to NaCN formation
- 2017AJ....153..240A (2017): An ALMA Survey of Protoplanetary Disks in the σ Orionis Cluster
- 2017ApJ...834..135T (2017): Bulge-forming Galaxies with an Extended Rotating Disk at z ~ 2
- 2017ApJ...836L..29J (2017): <SUP>13</SUP>CO/C<SUP>18</SUP>O Gradients across the Disks of Nearby Spiral Galaxies
- 2017ApJ...839L..15G (2017): Discovery and Physical Characterization of a Large Scattered Disk Object at 92 au
- 2017ApJ...840..101C (2017): Near-infrared MOSFIRE Spectra of Dusty Star-forming Galaxies at 0.2 &lt; z &lt; 4
- 2017ApJ...842L..21N (2017): ALMA Observations of Gas-rich Galaxies in z ∼ 1.6 Galaxy Clusters: Evidence for Higher Gas Fractions in High-density Environments
- 2017ApJ...843...27L (2017): Formation and Atmosphere of Complex Organic Molecules of the HH 212 Protostellar Disk
- 2017ApJ...844...99L (2017): An ALMA Survey of CO Isotopologue Emission from Protoplanetary Disks in Chamaeleon I
- 2017ApJ...844..123F (2017): The Circumgalactic Medium of Submillimeter Galaxies. II. Unobscured QSOs within Dusty Starbursts and QSO Sightlines with Impact Parameters …
- 2017ApJ...850..178A (2017): Deep Submillimeter and Radio Observations in the SSA22 Field. I. Powering Sources and the Lyα Escape Fraction of Lyα Blobs
- 2017MNRAS.466...49J (2017): Optical depth estimates and effective critical densities of dense gas tracers in the inner parts of nearby galaxy discs
- 2017MNRAS.466..861D (2017): A deep ALMA image of the Hubble Ultra Deep Field
- 2017MNRAS.468.3468G (2017): Molecular gas on large circumgalactic scales at z = 3.47
- 2017MNRAS.469.4683C (2017): ALMA constraints on star-forming gas in a prototypical z = 1.5 clumpy galaxy: the dearth of CO(5-4) emission from UV-bright clumps
- 2018A&A...616A.100Y (2018): Stellar masses and disk properties of Lupus young stellar objects traced by velocity-aligned stacked ALMA <SUP>13</SUP>CO and C<SUP>18</SUP…
- 2018A&A...617A..28S (2018): Chemistry in disks. XI. Sulfur-bearing species as tracers of protoplanetary disk physics and chemistry: the DM Tau case
- 2018A&A...618A..85S (2018): Near infrared spectroscopy and star-formation histories of 3 ≤ z ≤ 4 quiescent galaxies
- 2018A&A...620A.152F (2018): GOODS-ALMA: 1.1 mm galaxy survey. I. Source catalog and optically dark galaxies
- 2018AJ....156..164B (2018): Medium-sized Satellites of Large Kuiper Belt Objects
- 2018ApJ...853...24U (2018): ALMA 26 arcmin<SUP>2</SUP> Survey of GOODS-S at One-millimeter (ASAGAO): X-Ray AGN Properties of Millimeter-selected Galaxies
- 2018ApJ...853..195W (2018): Herschel and ALMA Observations of Massive SZE-selected Clusters
- 2018ApJ...854...97D (2018): An ALMA [C II] Survey of 27 Quasars at z &gt; 5.94
- 2018ApJ...856...14L (2018): A 100 au Wide Bipolar Rotating Shell Emanating from the HH 212 Protostellar Disk: A Disk Wind?
- 2018ApJ...856..118H (2018): Molecular Gas Reservoirs in Cluster Galaxies at z = 1.46
- 2018ApJ...859...21A (2018): ALMA Survey of Lupus Protoplanetary Disks. II. Gas Disk Radii
- 2018ApJ...860..103S (2018): Molecular Gas Contents and Scaling Relations for Massive, Passive Galaxies at Intermediate Redshifts from the LEGA-C Survey
- 2018ApJ...861....7F (2018): ALMA 26 Arcmin<SUP>2</SUP> Survey of GOODS-S at One Millimeter (ASAGAO): Average Morphology of High-z Dusty Star-forming Galaxies in an Exp…
- 2018ApJ...862L...2F (2018): First Detection of the Simplest Organic Acid in a Protoplanetary Disk
- 2018ApJ...868..113T (2018): Evidence for a Vertical Dependence on the Pressure Structure in AS 209
- 2018MNRAS.473.1909G (2018): ALMA suggests outflows in z ∼ 5.5 galaxies
- 2018MNRAS.481.1631B (2018): Obscured star formation in bright z ≃ 7 Lyman-break galaxies
- 2018PASJ...70...65U (2018): ALMA deep field in SSA22: Survey design and source catalog of a 20 arcmin<SUP>2</SUP> survey at 1.1 mm
- 2019A&A...623A..66B (2019): ALMA CO(2-1) observations in the XUV disk of M83
- 2019A&A...623A.124C (2019): Upper limits on CH<SUB>3</SUB>OH in the HD 163296 protoplanetary disk. Evidence for a low gas-phase CH<SUB>3</SUB>OH-to-H<SUB>2</SUB>CO rat…
- 2019A&A...624L...7V (2019): Stringent limits on the magnetic field strength in the disc of TW Hya. ALMA observations of CN polarisation
- 2019A&A...630A..59B (2019): Widespread QSO-driven outflows in the early Universe
- 2019A&A...631A..78S (2019): A spectral stacking analysis to search for faint outflow signatures in z ∼ 6 quasars
- 2019ApJ...871..109P (2019): Multiband Optical and Near-Infrared Properties of Faint Submillimeter Galaxies with Serendipitous ALMA Detections
- 2019ApJ...871..112X (2019): ALMA Observations of the Spatial Distribution of Three C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB> Isomers toward Sgr B2(N)
- 2019ApJ...874...53B (2019): Environmental Effect on the Interstellar Medium in Galaxies across the Cosmic Web at z = 0.73
- 2019ApJ...876L..13S (2019): Line Ratios Reveal N<SUB>2</SUB>H<SUP>+</SUP> Emission Originates above the Midplane in TW Hydrae
- 2019ApJ...877L..25M (2019): The First Bird’s-eye View of a Gravitationally Unstable Accretion Disk in High-mass Star Formation
- 2019ApJ...878...73Y (2019): ALMA 26 arcmin<SUP>2</SUP> Survey of GOODS-S at 1 mm (ASAGAO): Near-infrared-dark Faint ALMA Sources
- 2019ApJ...879...54L (2019): Revealing the Stellar Mass and Dust Distributions of Submillimeter Galaxies at Redshift 2
- 2019ApJ...880...69Y (2019): HL Tau Disk in HCO<SUP>+</SUP> (3-2) and (1-0) with ALMA: Gas Density, Temperature, Gap, and One-arm Spiral
- 2019ApJ...881...63N (2019): An ALMA Multiline Survey of the Interstellar Medium of the Redshift 7.5 Quasar Host Galaxy J1342+0928
- 2019ApJ...887..107F (2019): First Identification of 10 kpc [C II] 158 μm Halos around Star-forming Galaxies at z = 5-7
- 2019ApJ...887..183Z (2019): On the Gas Content, Star Formation Efficiency, and Environmental Quenching of Massive Galaxies in Protoclusters at z ≈ 2.0-2.5
- 2019MNRAS.482..698C (2019): The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - I: project description and continuum images at 28 au resolution
- 2019MNRAS.485.2092C (2019): Suppressed CO emission and high G/D ratios in z = 2 galaxies with sub-solar gas-phase metallicity
- 2019MNRAS.486..560S (2019): Passive galaxies in the early Universe: ALMA confirmation of z ∼ 3-5 candidates in the CANDELS GOODS-South field
- 2019MNRAS.487.4648S (2019): An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: source catalogue and properties
- 2019MNRAS.490.4956G (2019): An ALMA survey of the SCUBA-2 Cosmology Legacy Survey UKIDSS/UDS field: high-resolution dust continuum morphologies and the link between su…
- 2020A&A...633A.160C (2020): The ALMA Frontier Fields Survey. V. ALMA Stacking of Lyman-Break Galaxies in Abell 2744, Abell 370, Abell S1063, MACSJ0416.1-2403 and MACSJ…
- 2020A&A...640A..27V (2020): Protoplanetary disk masses in NGC 2024: Evidence for two populations
- 2020A&A...643A...2B (2020): The ALPINE-ALMA [CII] survey: Data processing, catalogs, and statistical source properties
- 2020ApJ...892...66M (2020): The ALMA Spectroscopic Survey in the HUDF: The Cosmic Dust and Gas Mass Densities in Galaxies up to z ∼ 3
- 2020ApJ...894...74B (2020): Protoplanetary Disks in the Orion Nebula Cluster: Gas-disk Morphologies and Kinematics as Seen with ALMA
- 2020ApJ...901...74T (2020): Structural Evolution in Massive Galaxies at z ∼ 2
- 2020ApJ...902..109B (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: CO Excitation and Atomic Carbon in Star-forming Galaxies at z = 1-3
- 2020ApJ...905...85S (2020): Ubiquitous Molecular Outflows in z &gt; 4 Massive, Dusty Galaxies. I. Sample Overview and Clumpy Structure in Molecular Outflows on 500 pc …
- 2020ApJS..247...61F (2020): The ALPINE-ALMA [C II] Survey: Multiwavelength Ancillary Data and Basic Physical Measurements
- 2020MNRAS.491.4724F (2020): A3COSMOS: the dust attenuation of star-forming galaxies at z = 2.5-4.0 from the COSMOS-ALMA archive
- 2020MNRAS.495.3840M (2020): A large amount of diffuse molecular gases in the bar of the strongly barred galaxy NGC 1300: cause of the low star formation efficiency
- 2020MNRAS.497.2771M (2020): VALES VI: ISM enrichment in star-forming galaxies up to z ∼ 0.2 using <SUP>12</SUP>CO(1-0), <SUP>13</SUP>CO(1-0), and C<SUP>18</SUP>O(1-0) …
- 2021A&A...645A.145G (2021): ALMA chemical survey of disk-outflow sources in Taurus (ALMA-DOT). V. Sample, overview, and demography of disk molecular emission
- 2021A&A...652A..30S (2021): The emergence of passive galaxies in the early Universe
- 2021A&A...652A..98G (2021): The Galaxy Activity, Torus, and Outflow Survey (GATOS). I. ALMA images of dusty molecular tori in Seyfert galaxies
- 2021ApJ...908...46B (2021): Dynamical Stellar Masses of Pre-main-sequence Stars in Lupus and Taurus Obtained with ALMA Surveys in Comparison with Stellar Evolutionary …
- 2021ApJ...908...54W (2021): ALMA Measures Rapidly Depleted Molecular Gas Reservoirs in Massive Quiescent Galaxies at z ∼ 1.5
- 2024A&A...688A..55M (2024): A<SUP>3</SUP>COSMOS: Measuring the cosmic dust-attenuated star formation rate density at 4 &lt; z &lt; 5
- 2024A&A...689A..65R (2024): ALMA high-resolution observations unveil planet formation shaping molecular emission in the PDS 70 disk
- 2024A&A...692A.215C (2024): Molecular gas budget of strongly magnified low-mass star-forming galaxies at cosmic noon
- 2024ApJ...961..120C (2024): Brightest Cluster Galaxy Formation in the z = 4.3 Protocluster SPT 2349-56: Discovery of a Radio-loud Active Galactic Nucleus
- 2024ApJ...965..147B (2024): The Carbon Isotopic Ratio and Planet Formation
- 2024ApJ...966..228R (2024): The MUSE Ultra Deep Field (MUDF). V. Characterizing the Mass─Metallicity Relation for Low-mass Galaxies at z ∼ 1─2
- 2024ApJ...970....9B (2024): Multiphase Black Hole Feedback and a Bright [C II] Halo in a LoBAL Quasar at z ∼ 6.6
- 2024RAA....24g5017M (2024): Investigating Sulfur Chemistry in the HD163296 Disk
- 2025A&A...700A.285W (2025): Gravitational torques from lopsided young stellar component sustain high black hole accretion rates in NGC 4593
- 2025ApJ...984L..19Y (2025): exoALMA. XIV. Gas Surface Densities in the RX J1604.3−2130 A Disk from Pressure-broadened CO Line Wings
- 2025ApJ...985..194P (2025): Traversing the Star-forming Main Sequence with Molecular Gas Stacks of z ∼ 1.6 Cluster Galaxies
- 2025ApJ...988..135M (2025): The Physical Properties and Morphologies of Faint Dusty Star-forming Galaxies Identified with JWST
- 2025ApJ...988..162D (2025): Constraining Resolved Extragalactic R<SUB>21</SUB> Variation with Well-calibrated ALMA Observations
- 2025ApJ...989....3D (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). III. Dust and Gas Disk Properties in the Lupus Star-forming Region
- 2025ApJ...994....4A (2025): Enhanced Gas-phase Metallicities and Suppressed Outflows for Galaxies in a Rich Cluster Core at Cosmic Noon
- 2025ApJ...995L..63L (2025): ALMA Reveals Diverse Dust-to-gas Mass Ratios and Quenching Modes in Old Quiescent Galaxies
- 2025ApJS..278...45F (2025): DUALZ—Deep UNCOVER-ALMA Legacy High-Z Survey
- 2025MNRAS.541.4031D (2025): VERTICO ─ IX. Signatures of environmental processing of the gas in Virgo cluster spiral galaxies through mapping of CO isotopologues
- 2026A&A...705A.163H (2026): CHILES: X. Molecular and atomic gas at intermediate redshift
- 2026A&A...705A.198M (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): IV. CO gas imaging and overview
- 2026A&A...705L..14D (2026): The near-infrared silhouette of the Flying Saucer edge-on disc revealed by the JWST JEDIce program
- 2026A&A...706A...9Z (2026): JWST reveals extended stellar disks for ALMA-bright dusty star-forming galaxies in the Spiderweb protocluster
- 2026ApJ..1000..308W (2026): The ALPINE-CRISTAL-JWST Survey: Chemical Abundance Comparison between the ISM and CGM of Main-sequence Galaxies at z = 4─6
- 2026ApJ..1000..312Z (2026): A Potential Link between Nuclear Winds and Cold Gas Outflows on Kiloparsec Scales in Reionization-era Quasars
- 2026ApJ..1003...64Y (2026): Compact Hydrogen Sulfide Emission Indicates Sulfur-bearing Ice Sublimation in the Inner Disk of HD 163296
