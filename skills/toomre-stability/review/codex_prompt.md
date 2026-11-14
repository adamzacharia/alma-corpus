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

=== SKILL.md (toomre-stability) ===
---
name: alma-toomre-stability
description: "Compute and interpret the Toomre Q stability parameter from ALMA data, for protoplanetary and massive-protostar disks (dust or gas surface density, temperature, Keplerian rotation) and for galaxy gas disks (rotation curve, velocity dispersion, CO or [CII] gas mass). Use when a task asks whether a disk is gravitationally unstable, needs a Q map or radial Q profile, uses Q as a prior or upper limit on surface density, or interprets spirals, clumps or fragments as gravitational instability. Built from 51 ALMA papers (2014-2025), 46 of them on topic."
---
# Toomre Q stability from ALMA data

Q = (velocity support) x (epicyclic frequency) / (pi G Sigma). ALMA gives Sigma (continuum or line), the
rotation (Keplerian mass or rotation curve) and sometimes the dispersion; the temperature or dispersion and the
mass conversion (dust opacity, gas-to-dust ratio, alpha_CO or alpha_[CII]) are usually assumed. The two mistakes
that matter most: (1) quoting a single Q without saying it inherits every mass and temperature assumption (one
disk moves from Q = 0.4 to 5 between 20 K and 100 K, 2018ApJ...864L..25O); (2) treating Q < 1 as a sharp line
when the papers use thresholds from 1 to 2 and report uncertainties of 50% to a factor of two (2025NatAs...9.1833L,
2015ApJ...806...17R).

Counts below are from the evidence pack (51 papers, my count of its lines unless marked "aggregate"). Of the 51,
3 are off-topic and ignored: 2020A&A...635A...2S and 2019A&A...623L...8B use the Cartwright-Whitworth cluster
"Q parameter" (a spatial statistic, not Toomre), and 2021A&A...656A..60A uses "Toomre disks" only as a mass
component in a rotation-curve model. Two more (2019A&A...623A..79C, 2025A&A...693A.311P) only set Q = 1 in
particle simulations used to fit black hole masses.

## When to use

- A resolved circumstellar disk (Class 0/I/II, or around a massive protostar) and the question is whether it is
  gravitationally unstable, can fragment, or can drive spirals: 27 papers in the pack (20 low-mass disks, 7
  massive-protostar disks or clumps).
- A rotating gas disk in a galaxy (nearby nucleus, early-type circumnuclear disk, dwarf, lensed or high-z
  [CII]/CO disk) and the question is whether clumps or star formation follow from instability: 19 papers.
- Q used as a constraint rather than a result: a stability prior or cap on gas surface density
  (2024ApJ...970..153A, 2018ApJ...869L..47Z, 2024ApJ...971..129C, 2018ApJ...869L..46D), a lower limit on the CO
  abundance (2025ApJ...984L..19Y), or an upper limit on velocity dispersion (2019ApJ...876..130H).

## When not to use

- The "Q parameter" of a star or core cluster (mean MST edge length over mean separation): that is a clustering
  statistic (2020A&A...635A...2S, 2019A&A...623L...8B). Use a cluster-structure / core-extraction workflow.
- Mass modelling of a rotation curve where "Toomre disk" names a potential (2021A&A...656A..60A): use galaxy
  kinematics / mass-model workflows.
- The disk is unresolved or barely resolved: papers that tried say Sigma or the flux distribution cannot be
  measured (2016ApJ...827...81I, 2014A&A...565A..59D). Report a disk-averaged Q at most, with the caveat.
- Filament fragmentation: compare spacing and mass per length with cylinder fragmentation instead; the one paper
  that weighed disk vs filament ran both tests (2014A&A...569A..11S).
- Black hole mass fitting: Q = 1 is only a particle-disk setting there (2019A&A...623A..79C,
  2025A&A...693A.311P); use a gas-dynamics / SMBH workflow.

## Steps

### Circumstellar disks (protoplanetary and massive protostars)

1. **Get Sigma(r) or a Sigma map.** Goal: total (gas) surface density.
   - From dust continuum: optically thin conversion with an assumed opacity and temperature, times a gas-to-dust
     ratio (100 in 8 pack papers, e.g. 2019ApJ...871..185L, 2016Sci...353.1519P, 2024ApJ...971..129C,
     2020ApJ...890..130T). Some papers model optical depth and scattering first (2020ApJ...893..125U, RADMC-3D in
     2016Sci...353.1519P).
   - From gas: rare isotopologues (13C17O in 2020MNRAS.493L.108B and 2019ApJ...882L..31B; C18O in
     2019MNRAS.485..739M and 2016MNRAS.461..385B), or pressure-broadened CO line wings (2025ApJ...984L..19Y), or a
     kinematic self-gravity fit (2024ApJ...970..153A).
   - For a quick global number, papers use the disk mass directly: Q ~ 2 (M*/Md)(H/R) (2020ApJ...890..130T) or
     Q = c_s kappa / (pi G mean Sigma) with flaring angle 0.02 (2019ApJ...877..100Y).
   - Software: CASA images, then custom scripts; dsharp_opac for opacities (2020ApJ...891...48H, aggregate 1).
2. **Set the temperature (sound speed).** c_s = sqrt(k T / (mu m_H)), mu = 2.3 (2017A&A...603A..10B).
   Choices seen: constant 30 K (2019ApJ...871..185L, 2018ApJ...861...91H, 2020ApJ...893..125U), 15 K
   (2018ApJ...852..122H), a model midplane profile (2020MNRAS.493L.108B, 2020ApJ...891...48H), a power law
   T ~ r^-0.4 (2017A&A...603A..10B, 2019A&A...627L...6M) or R^-0.46 (2020ApJ...890..130T), or line rotation
   temperatures T_rot from CH3CN (2017A&A...603A..10B, 2025A&A...693A..76C).
3. **Set kappa.** For a Keplerian disk kappa = Omega = sqrt(G M / r^3) (2025NatAs...9.1833L). The central mass comes
   from Keplerian fits or assumptions: 1.7 Msun HL Tau (2020MNRAS.493L.108B), 10 Msun (2017A&A...603A..10B,
   2019ApJ...877L..25M), 7.6 Msun enclosed (2025NatAs...9.1833L), 0.25 Msun fiducial (2020ApJ...890..130T). In a
   massive clump with no clear star, bracket it (0 or 30 Msun in 2019ApJ...871..185L).
4. **Compute Q = c_s kappa / (pi G Sigma)** per pixel (2017A&A...603A..10B, 2019A&A...627L...6M,
   2025NatAs...9.1833L, 2019ApJ...877L..25M) or per annulus (2020MNRAS.493L.108B, 2024ApJ...966..119L).
   Sample the inputs to get a Q distribution (1e6 draws of Sigma_d and T in 2024ApJ...971..129C).
5. **Compare with a threshold and with morphology.** Report where Q falls below the adopted threshold (see the
   table), and check against spirals, clumps or fragments (2019ApJ...877L..25M clumps; 2024ApJ...966..119L
   spiral fits; 2025ApJ...984L..19Y no spirals, so stable).
6. **Bracket the assumptions** (see Verification checks): temperature, opacity index, free-free removal, magnetic
   support.

### Galaxy gas disks

1. **Gas surface density.** From CO with alpha_CO (2025ApJ...995..151Y, 2017A&A...604A.117C,
   2017ApJ...845..170B), from [CII] with alpha_[CII] = 31 Msun/Lsun (2025NatAs...9.1553F), or by splitting a total
   gas mass by the [CII] flux map (2019ApJ...870...80L, 2014A&A...565A..59D). Pixel maps use moment 0
   (2021A&A...655A..25Z).
2. **Rotation and kappa.** Tilted-ring fits with 3DBarolo (2025NatAs...9.1553F, 2019ApJ...870...80L; aggregate 2
   counting both spellings), an arctangent model (2018MNRAS.476..122V), or a disk model of the velocity field
   (2015ApJ...806L..17S). Write kappa = a V/R. General practice (Genzel-type parametrisation): a = 1 Keplerian,
   sqrt(2) flat, sqrt(3) solid body, 2 uniform density. Seen: a = sqrt(3) (2015ApJ...806L..17S,
   2019ApJ...870...80L), sqrt(2) flat curve (2014A&A...565A..59D), a = 1 inside 1.1 arcsec and 1.4 beyond
   (2021A&A...655A..25Z), a = 2 (2017A&A...604A.117C), a = 1 (2016ApJ...823...68S).
3. **Velocity dispersion.** From moment 2 per pixel (2021A&A...655A..25Z), non-parametric sigma(R) from 3DBarolo
   (2025NatAs...9.1553F), the minimum observed sigma_LOS in place of c_s (2017ApJ...845..170B), or assumed:
   5 km/s for dwarfs (2025ApJ...995..151Y), 6 km/s (2019Natur.569..519K), 8 km/s canonical alternative
   (2018MNRAS.476..122V), 30-35 km/s for a z ~ 3 disk (2015ApJ...806L..17S).
4. **Compute Q_gas = sigma kappa / (pi G Sigma_gas)** per pixel (2021A&A...655A..25Z, 2014A&A...565A..59D,
   2025NatAs...9.1553F), as a radial profile (2025NatAs...9.1553F), or averaged within R = 3 scale lengths
   (2020Natur.581..269N). Where stars matter, use a two-component Q_tot (Romeo and Wiegert 2011 approximation)
   with sigma_z/sigma_r = 0.6 for stars and 1 for gas (2025ApJ...995..151Y).
5. **Mask beam-smeared regions** (central 0.3 arcsec excluded in 2021A&A...655A..25Z) and compare with clumps,
   Jeans length (L_J = pi sigma^2 / (8 G Sigma_gas), 2015ApJ...806L..17S) or the star formation law.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count, from pack) | Examples |
|---|---|---|---|---|
| Instability threshold | Q < 1 to 2 | Q < 1 (cap), < 1.5, < 1.7, < 2 | 10 state one | 2018ApJ...869L..47Z (Q = 1 cap), 2015ApJ...808..102K (1.5), 2020MNRAS.493L.108B (1.7), 2025NatAs...9.1833L (1-2), 2024ApJ...971..129C (Q > 2 stable) |
| Gas-to-dust ratio (disks) | 100 | 100 to ~260; ~1e3 for a high-z check | 8 use 100 | 2016Sci...353.1519P, 2024ApJ...971..129C, 2019ApJ...882L..31B (260, card), 2025NatAs...9.1553F (1e3) |
| Dust opacity, mm | ~2-3 cm2/g per gram dust near 1 mm | 9.2e-2 (Band 3) to 3.3 cm2/g | 5 | 2016Sci...353.1519P (2.3 at 1.3 mm), 2019ApJ...877..100Y (3), 2018ApJ...852..122H (3.3 at 290 GHz), 2020ApJ...893..125U (9.2e-2 Band 3) |
| Opacity per gram of gas | power law | 0.01 cm2/g at 230 GHz, beta 0.729; 10 (nu/1 THz)^beta / 100, beta 1; 6.8e-4 at 1.2 mm | 3 | 2016ApJ...818..158A, 2018ApJ...861...91H, 2018ApJ...864L..25O |
| Disk temperature | 30 K constant or a power law | 15 K to 200 K; T ~ r^-0.4 to r^-0.46; T_rot | 11 | 2019ApJ...871..185L, 2018ApJ...852..122H, 2017A&A...603A..10B, 2020ApJ...890..130T |
| Mean molecular weight | 2.3 | 2.3-2.8 | 3 | 2017A&A...603A..10B, 2019A&A...627L...6M, 2025A&A...693A..76C (2.8) |
| Epicyclic factor a (galaxies) | sqrt(3) or sqrt(2) | 1 to 2 | 6 | 2015ApJ...806L..17S, 2014A&A...565A..59D, 2021A&A...655A..25Z, 2017A&A...604A.117C |
| Gas dispersion (galaxies, if assumed) | measured moment 2 | 5-35 km/s | 4 | 2025ApJ...995..151Y, 2019Natur.569..519K, 2018MNRAS.476..122V, 2015ApJ...806L..17S |
| Stellar dispersion (Q_tot) | 30 km/s | one paper | 1 | 2025ApJ...995..151Y |
| alpha_[CII] | 31 Msun/Lsun | one paper | 1 | 2025NatAs...9.1553F |
| Q prior in kinematic fits | minimum-Q prior | emcee, 64 walkers, 25,000 steps | 1 | 2024ApJ...970..153A |
| Particle-disk setup (not a measurement) | Q = 1, 1e6 particles | | 2 | 2019A&A...623A..79C, 2025A&A...693A.311P |

Reported Q values (useful as sanity ranges, more in `references/parameters.md`): high-z [CII]/CO disks 0.02 to
1.07 (2019ApJ...870...80L, 2025NatAs...9.1553F, 2015ApJ...806L..17S, 2020Natur.581..269N); dwarfs 0.9 to 1.5
(2025ApJ...995..151Y); Mrk 509 0.5 to 10 (2021A&A...655A..25Z); HL Tau minimum 1.1 at 77 au
(2020MNRAS.493L.108B); massive-protostar disks 0.4 to 4 (2019ApJ...877L..25M, 2017A&A...603A..10B,
2019A&A...627L...6M).

## Software

The cards rarely name the code that computes Q itself; it is a formula applied to maps in custom scripts. Named
tools (aggregate counts over all 51 papers, each 1 unless noted):

| Tool | Used for | Papers |
|---|---|---|
| CASA (tclean, moments) | images and moment 0/2 maps that feed Sigma and sigma | implicit in most; settings rarely stated |
| 3DBarolo / 3D-Barolo | rotation curve V(R), sigma(R) for galaxy Q (2 papers, two spellings) | 2025NatAs...9.1553F, 2019ApJ...870...80L |
| emcee | kinematic disk-mass fit with a minimum-Q prior | 2024ApJ...970..153A |
| RADMC-3D | radiative transfer for temperature, Sigma, optical depth before Q | 2016Sci...353.1519P |
| dsharp_opac | DSHARP opacities for optical depth and grain size | 2020ApJ...891...48H |
| Cprops | GMC catalogue compared with the Toomre length | 2019Natur.569..519K |
| XCLASS (card note) | pixel T_rot maps used as temperature | 2017A&A...603A..10B |
| scikit-learn, NetworkX, FragMent | cluster statistics in an off-topic paper | 2020A&A...635A...2S |

Recommendation: write Q as a small numpy function over the Sigma, T (or sigma) and radius maps on the same grid,
with deprojected radius, and keep every assumed constant as a named input so it can be bracketed.

## Pitfalls

- **Mass is the dominant error.** Opacity uncertain by a factor of 10 (2018ApJ...869L..46D), kappa0 by a factor of
  two (2015ApJ...808..102K); disk masses are the largest uncertainty and the gas-to-dust ratio is unconstrained
  (2019ApJ...877..100Y). Q scales as 1/Sigma, so it inherits all of this.
- **Optical depth and missing flux make Sigma a lower limit, so Q an upper limit** (2025NatAs...9.1833L,
  2017A&A...603A..10B where more than 99% of extended flux is filtered, 2020ApJ...890..130T). Say which way the
  bias goes.
- **Temperature choice moves Q a lot.** Q from 0.4 to 5 for 20-100 K (2018ApJ...864L..25O, card); a steeper
  temperature profile or optical depth would lower Q (2019A&A...627L...6M); temperatures are often assumed, not
  measured (2020A&A...635A...2S notes the same problem for masses).
- **Opacity index beta.** The major uncertainty of Q in 2019ApJ...877L..25M: minimum Q 0.9 for beta = 1 vs 0.4 for
  beta = 2.
- **Gas tracers.** CO/H2 ratio, freeze-out, optical depth and isotope ratios (2020MNRAS.493L.108B); absolute Sigma
  scales as X_CO^-0.5 in the line-wing method (2025ApJ...984L..19Y); alpha_CO in early-type galaxies
  (2017ApJ...845..170B) and in dwarfs (2025ApJ...995..151Y); a single mid-J CO line (2016ApJ...827...34O).
- **Dispersion is not sound speed.** Observed sigma includes beam smearing (2017ApJ...845..170B), is an upper limit
  in edge-on geometry (2018MNRAS.476..122V), and using sigma_r gives an upper limit on Q (2019ApJ...870...80L).
- **Free-free contamination** in massive protostars changes the continuum Sigma (2019A&A...627L...6M).
- **Envelope contamination** in Class 0/I disks inflates mass (2020ApJ...890..130T).
- **Thickness and geometry.** H(r) cannot be measured and is assumed (2019ApJ...871..185L); inclination not
  corrected (2017A&A...604A.117C); dark matter or bulge neglected (2019A&A...631A..91G, 2025A&A...693A.311P).
- **Azimuthal averaging** of non-axisymmetric disks biases kinematic masses (2024ApJ...970..153A); 1 arcsec beams
  dilute azimuthal variations (2019MNRAS.485..739M).
- **Lensed sources.** Magnification systematics up to ~25% (2025NatAs...9.1553F).
- **Settings cards flag as not stated** (aggregate): line-free channels for continuum subtraction (5),
  self-calibration intervals (3), cell and image size (2), flux calibration uncertainty (2), moment clipping
  thresholds (2). Cards also note the Q setup itself is often unstated: temperature and surface density details
  for the Q curve (2024ApJ...966..119L), the per-pixel kappa and inclination (2017A&A...603A..10B), the [CII] to
  Sigma conversion and aperture (2014A&A...565A..59D). State all of these.

## Verification checks

What the papers did:

- **Bracket the temperature**: three temperature prescriptions treated as bounds on the real Q
  (2017A&A...603A..10B); check model temperature against CH3CN (2019ApJ...871..185L).
- **Bracket the contamination**: Q for minimal and maximal free-free removal (2019A&A...627L...6M); screen
  envelope-contaminated sources by image inspection (2020ApJ...890..130T).
- **Propagate errors**: 54% Q uncertainty (2025NatAs...9.1833L); stability survives errors in k1, Sigma,
  inclination (2 deg) and sigma (1 km/s) (2017ApJ...845..170B); factor-two uncertainty stated (2015ApJ...806...17R).
- **Extra support terms**: magnetic correction with plasma beta 10 to 1e4 changed minimum Q by about 5%
  (2020MNRAS.493L.108B).
- **Use the bias direction**: if sigma_r overestimates turbulence, Q is an upper limit and Q << 1 is robust
  (2019ApJ...870...80L).
- **Independent mass checks**: gas mass vs Mdyn minus M* and dust-based mass (2025NatAs...9.1553F); enclosed
  dynamical mass vs gas mass from another paper (2015ApJ...806...17R).
- **Physical consistency**: Toomre upper limits vs Jeans lower limits on dispersion (2019ApJ...876..130H);
  spiral shape fits (2024ApJ...966..119L); comparison with simulations (2019ApJ...877L..25M).
- **Exclude beam-smeared pixels** (2021A&A...655A..25Z).

What a careful referee adds (recommendations, not pack practice):

- Report Q with the full input list: Sigma tracer and conversion, T or sigma, central mass, inclination, distance,
  threshold used.
- Show the Q map next to a Sigma S/N map and the beam; mask pixels below about 3 sigma and inside one beam of the
  center.
- Recompute Q at the two ends of each dominant assumption (opacity or alpha_CO, T, gas-to-dust) and state whether
  the stability verdict changes.
- If Sigma is from optically thin dust and the peak brightness temperature approaches the assumed T, treat Sigma as
  a lower limit and Q as an upper limit.

## Source cards

Full list with titles: `references/sources.md` (generated). Most informative for this technique:

- 2017A&A...603A..10B: per-pixel Q map with three temperature prescriptions as bounds.
- 2020MNRAS.493L.108B: radial Q from 13C17O gas mass, threshold 1.7, magnetic check.
- 2019ApJ...877L..25M: face-on massive disk, Q vs beta, clumps.
- 2019A&A...627L...6M: O-star disk Q map with free-free brackets.
- 2025NatAs...9.1833L: Keplerian Q map, 54% uncertainty, fragmentation.
- 2019ApJ...871..185L: clump Q with 0 vs 30 Msun central mass and temperature checks.
- 2020ApJ...890..130T: survey-scale Q ~ 2 (M*/Md)(H/R) for Class 0/I disks.
- 2024ApJ...971..129C: Monte Carlo Q profile, Q > 2 as stability floor.
- 2024ApJ...970..153A: minimum-Q prior in an emcee kinematic disk-mass fit.
- 2025ApJ...984L..19Y: Q > 1 used to bound X_CO.
- 2018ApJ...869L..47Z: Q = 1 as a cap on gas surface density for planet masses.
- 2024ApJ...966..119L: Q for current vs pre-outburst temperature.
- 2021A&A...655A..25Z: pixel Q_gas from moments 0 and 2 with a radius-dependent a.
- 2025ApJ...995..151Y: two-component Q_tot for dwarfs.
- 2017ApJ...845..170B: minimum sigma_LOS as c_s and error propagation.
- 2025NatAs...9.1553F: 3DBarolo Q profile and 2D map at z = 6.
- 2019ApJ...870...80L: Q upper limits from sigma_r in a z = 5.7 merger.
- 2015ApJ...806L..17S: Q plus Jeans length in a lensed z = 3 disk.
- 2014A&A...565A..59D: per-pixel Q with [CII] as Sigma proxy.
- 2020Natur.581..269N: disk-averaged Q within 3 scale lengths.

=== references/parameters.md ===
# Toomre Q: inputs and reported values per paper

From the `toomre-stability` evidence pack. Values marked "(card)" were read from that paper's methods card to
settle a detail the pack summarised. Off-topic papers (cluster Q statistic, Toomre-disk mass components) are left
out.

## Circumstellar disks

| Paper | Sigma source | Temperature | Central mass | Threshold / use | Reported Q |
|---|---|---|---|---|---|
| 2017A&A...603A..10B | continuum per pixel | T_rot; 200 K; T ~ r^-0.4 (1400 K at 10 AU) | 10 Msun Keplerian | map | min > ~1.5 (power-law T) |
| 2019A&A...627L...6M | column density x mu m_H, mu = 2.3 | T ~ R^-0.4 anchored to O star | Keplerian | map, min/max free-free | 2-4 in ring at 65-97 au |
| 2019ApJ...877L..25M | continuum, beta = 1 or 2 | not stated in pack | 10 Msun Keplerian | map | min 0.9 (beta 1), 0.4 (beta 2) |
| 2025NatAs...9.1833L | disk mass 2.71 Msun | T maps | 7.6 Msun enclosed | Q < 1-2 unstable | uncertainty 54% |
| 2019ApJ...871..185L | 225 GHz flux, g/d 100 | 30 K fiducial or profile | 0 or 30 Msun | radial | (fragmentation test) |
| 2025A&A...693A..76C | CH3CN Ncol, X = 1e-9, mu = 2.8 | Tk = T_rot | 12 Msun | analytic | (toy model) |
| 2020MNRAS.493L.108B | 13C17O gas + dust | model midplane | 1.7 Msun | Q < ~1.7 | min 1.1 at 77 au; Q < 1.7 at 50-110 au |
| 2019ApJ...882L..31B | 13C17O gas, g/d ~260 (card) | model midplane | Gaia-distance mass | radial | min ~6 at ~110 au (card) |
| 2019MNRAS.485..739M | C18O gas, lower limit | | | radial | min ~24 at ~80 au (card) |
| 2016MNRAS.461..385B | C18O gas within 90 au, H/r ~0.1 | model | | Q = 1 | well above 1 |
| 2018ApJ...852..122H | dust, kappa 3.3 cm2/g at 290 GHz, g/d 100 | 15 K | | check | |
| 2016Sci...353.1519P | RADMC-3D, kappa 2.3 cm2/g at 1.3 mm, g/d 100 | RT model | | | |
| 2018ApJ...861...91H | kappa = 10 (nu/1 THz)^1 cm2/g / 100 | 30 K | 0.15 Msun | | ~1.8 at 85 au (card) |
| 2018ApJ...864L..25O | kappa 6.8e-4 cm2/g at 1.2 mm | 20-100 K | Keplerian | | 0.4 (20 K) to 5 (100 K) (card) |
| 2019ApJ...877..100Y | 880 um flux, kappa 3 cm2/g, g/d 100 | irradiated, phi = 0.02 | | mean Q | |
| 2020ApJ...890..130T | dust mass x 100 | T ~ R^-0.46 | 0.25 Msun fiducial | Q ~ 2 (M*/Md)(H/R) | |
| 2020ApJ...893..125U | DSHARP kappa_abs 9.2e-2 cm2/g Band 3 | 30 K | 0.8 Msun | | |
| 2015ApJ...808..102K | fitted Sigma(r) | fitted midplane | Keplerian | Q < ~1.5 unstable | |
| 2016ApJ...818..158A | kappa0 = 0.01 cm2/g at 230 GHz, beta 0.729 | | | Sigma_g,min from Q plus cooling | |
| 2024ApJ...966..119L | | current vs pre-burst (snowline 4 au) | | Q < 2 | > 2 now (~7 at 200 au); < 2 at r < 100 au pre-burst |
| 2024ApJ...971..129C | 1e6 draws of Sigma_d, T; g/d 100 | sampled | | Q > 2 stable | max g/d 27 in ring |
| 2018ApJ...869L..46D | dust trap model | estimated | | Q > 2 caps Sigma_g | |
| 2018ApJ...869L..47Z | outer-disk dust Sigma | | | Q = 1 caps Sigma_g | |
| 2024ApJ...970..153A | kinematic self-gravity | fitted | fitted | min Q prior | Md/M* = 7 +/- 1% (MWC 480) |
| 2025ApJ...984L..19Y | CO line wings | | | Q > 1 at peak | X_CO > 7e-4 |

## Galaxy gas disks

| Paper | Sigma source | Dispersion | kappa / rotation | Reported Q |
|---|---|---|---|---|
| 2014A&A...565A..59D | [CII] luminosity proxy | measured | sqrt(2) V/r, flat | 0.58 +/- 0.15 average |
| 2015ApJ...806L..17S | Sigma_gas 4 +/- 1e9 Msun/kpc^2 | 30-35 km/s | sqrt(3) Vmax/R | 0.30 +/- 0.10 |
| 2016ApJ...827...34O | CO gas mass | measured | disk + halo model | ~0.22, ~0.35 (card) |
| 2017A&A...604A.117C | 1e4 Msun/pc^2 | measured | a = 2 | 1.0 +/- 0.3 |
| 2018A&A...613A..34P | Mdyn minus 30% DM and stars | measured | i = 54 deg | 1.07 (card) |
| 2019A&A...631A..91G | f_gas | sigma0 | Q = sqrt(2) sigma0/(vrot fgas) | ~0.6 |
| 2019ApJ...870...80L | M_g = 1.5e11 Msun split by [CII] | sigma_r (upper limit) | sqrt(3) v_r/r, 3D-Barolo | mean 0.02-0.03, max 0.13 |
| 2020Natur.581..269N | molecular mass | measured | within R = 3 R_d | 0.96 +/- 0.30 |
| 2025NatAs...9.1553F | [CII], alpha 31 Msun/Lsun | 3DBarolo sigma(R) | 3DBarolo V(R) | 0.2-0.3 |
| 2015ApJ...806...17R | warm CO gas | sigma as c_s | 135 km/s rotation | ~1.5, factor two |
| 2016ApJ...823...68S | molecular | sigma_mol | alpha = 1 | |
| 2017ApJ...845..170B | CO, alpha_CO | min sigma_LOS | k1/sin i | stable |
| 2018MNRAS.476..122V | CO | measured or 8 km/s | arctangent model | mostly > 1 (card) |
| 2021A&A...655A..25Z | moment 0 | moment 2 | a = 1 (< 1.1 arcsec), 1.4 beyond | 0.5-10 |
| 2025ApJ...995..151Y | H2 only | gas 5 km/s, stars 30 km/s | rotation curve | Q_tot 0.9-1.5 |
| 2019ApJ...876..130H | global Sigma_SFR | inferred | flat curve | sigma < 70-160 km/s from Q < 1 |

=== EVIDENCE PACK (toomre-stability) ===
# Evidence pack: Gravitational stability of disks (Toomre Q) (`toomre-stability`)

Scope: Toomre Q maps for gas/dust disks and galaxies

Built from 51 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2014-2025.
Matcher (regex over analysis steps): `toomre|\bq parameter|gravitational(?:ly)? (?:un)?stab|disk instability|disc instability`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- protoplanetary_disks: 23
- star_formation: 16
- nearby_galaxies: 12
- high_z_galaxies: 10
- agn_and_quasars: 7
- astrochemistry: 5
- milky_way_ism: 4
- galaxy_clusters_and_sz: 1

### Software named in the matched steps
- emcee: 1
- dsharp_opac: 1
- scikit-learn: 1
- networkx: 1
- fragment: 1
- 3dbarolo: 1
- radmc-3d: 1
- cprops: 1
- 3d-barolo: 1

### Fitting methods (most common phrasings)
- Least-squares grid exploration; best fit a compromise between PV diagram and velocity dispersion map: 1
- Gaussian likelihood with nuisance f_vphi; emcee: 1
- Dark matter as free parameter to fit V(R): 1
- Q uncertainty from 100 random 20% subsamples with Gaussian fit: 1

### Validation checks used
- Compared to 1-D numerical drift-diffusion model of a planet gap: 1
- CH3CN temperatures broadly consistent with profile: 1
- Method tested on NGC 1672; no-BH model compared: 1
- Simulated curves compared to observed CO and [O II] curves: 1
- Injection/recovery on fiducial models; MWC 480 compared with Zhang+21 and Martire+24 Sigma profiles: 1
- Alternative formulae from Birnstiel 2018 and Zhu 2019 give similar results; McClure temperature structure tested: 1
- Cross-check of number of clusters with elbow and silhouette: 1
- Uncertainty 54% propagated: 1
- Mgas consistent with Mdyn-Mstar and dust-based estimates; factor-2 uncertainty acknowledged: 1
- Compared with FWHM-based v_rot of 300 +/- 50 km/s: 1
- Compared with gas mass 1.1e9 Msun from Paper I: 1
- Three temperature approaches bracket real Q: 1
- Compared with Mdot_BH and nuclear mass flow: 1
- Toomre upper limits marginally consistent with Jeans lower limits: 1
- Magnetic-field correction checked with beta_p ~10 to 10^4: 1
- central 0.3 arcsec excluded for beam smearing: 1
- Envelope-contaminated candidates screened by image inspection: 1
- compared with Cesaroni et al. 1999 accretion rate: 1
- Model reproduces azimuthally averaged radial profile: 1
- Compared with simulations of Meyer et al. 2018: 1
- Southern arm well fit, northern not; shape ambiguous: 1
- Consistency check with assumed mass, kinematics, asymmetry, depth: 1
- Computed for minimal and maximal free-free removal: 1
- Stability persists with uncertainties in k1, Sigma, i (2 deg) and sigma (1 km/s): 1
- Using sigma_r gives upper limit on Q so Q<<1 is robust: 1
- compared against Panic2017 models: 1
- Disk+halo model is degenerate as rotation curve does not turn over: 1

### Key parameters and settings (bibcode: value)
- 2018ApJ...869L..46D: Sc=1; xi_dust=1.67 g/cm^3; example a=0.02 cm
- 2019ApJ...871..185L: 0 or 30 Msun central stellar mass
- 2019A&A...623A..79C: 1 million particles, Toomre Q=1, nuclear region 120 pc diameter
- 2019A&A...631A..91G: Snake: M*=4.0e10, R*=3.8 kpc, H*=0.5 kpc, f_mol=0.20, R_mol=0.75 kpc, H_mol=0.1 kpc, R_ion=6.1 kpc, H_ion=1-3 kpc, Q=0.6, i=70 deg
- 2024ApJ...970..153A: 64 walkers, 25,000 steps; priors p~U(0,2), gamma~U(0,6), rt logistic soft bound (600 au for MWC 480), min Q prior
- 2020ApJ...891...48H: p = 3.5, 2.5, 1.5; a_min = 0.1 um; Td = 30 K (B40), 18 K (B84)
- 2021A&A...656A..60A: corotation at ~1.2 bar radius
- 2020A&A...635A...2S: TPCF with 10000 random instances per cluster
- 2025ApJ...995..151Y: sigma_g = 5 km/s; sigma_star,r = 30 km/s
- 2025NatAs...9.1553F: alpha_[CII]=31 Msun/Lsun
- 2020Natur.581..269N: R = 3 exponential scale lengths = 4.2 kpc
- 2015ApJ...808..102K: Q<~1.5 unstable
- 2018ApJ...852..122H: kappa=3.3 cm2/g at 290 GHz; gas-to-dust 100; T=15 K for Q
- 2017A&A...603A..10B: T = T_rot; T = 200 K; T ∝ r^-0.4 with 1400 K at 10 AU
- 2016ApJ...827...81I: n_H2 = 1e6 cm^-3, log(Hx/nH) = -27.5, c_s ~1 km/s, Toomre Q=1
- 2024ApJ...971..129C: rho_m=1.675 g/cm3, Q>2 for stability
- 2020MNRAS.493L.108B: instability threshold Q<~1.7
- 2021A&A...655A..25Z: a=1 up to R=1.1 arcsec, a=1.4 beyond
- 2025A&A...693A.311P: cube dimensions (250, 250, 60); 10 km/s channels
- 2015ApJ...806L..17S: kappa = a Vmax/R with a = sqrt3; sigma_r = 30–35 km/s; Sigma_gas = 4±1e9 Msun kpc^2
- 2017A&A...604A.117C: R1=700 pc, R2=600 pc; Sigma_gas=1e4 Msun/pc2; a=2
- 2019ApJ...877..100Y: flaring angle phi = 0.02
- 2016MNRAS.461..385B: H/r~0.1, tau_dyn(90 au)~100 yr
- 2019A&A...623L...8B: 20 bins, Δs = 2 arcsec; cluster radius 20 arcsec


### Assumptions (bibcode: value)
- 2018ApJ...869L..46D: Perfect trapping, fixed Gaussian pressure bump, no back-reaction
- 2019ApJ...871..185L: Constant 30 K fiducial, or radial profile; optically thin; gas-to-dust 100; flattened rotating
- 2019A&A...623A..79C: Axisymmetric disks only; bar/spiral perturbations neglected
- 2019A&A...631A..91G: Dark matter and bulge neglected; Toomre Q=sqrt2 sigma0/(vrot fgas)
- 2024ApJ...970..153A: Axisymmetry, no radial/vertical flows, gravitationally stable disk (min Q prior)
- 2020ApJ...891...48H: Midplane temperature from Macías et al. 2018; DSHARP opacities; gas-to-dust ratio 100 for Toomre Q
- 2021A&A...656A..60A: parameters not unique
- 2025NatAs...9.1833L: Q<1-2 unstable
- 2025ApJ...995..151Y: Q_g from H2 only; sigma_z/sigma_r = 0.6 stars, 1 gas
- 2014A&A...565A..59D: [CII] traces molecular gas kinematics
- 2025NatAs...9.1553F: Dark matter negligible in dynamical mass; gas-to-dust ~1e3 for cross-check
- 2020Natur.581..269N: Spherical mass distribution (30% uncertainty added)
- 2015ApJ...806...17R: Inclination 50 deg for upper mass
- 2015ApJ...808..102K: Keplerian rotation; Haro 6-13 accretion rate assumed 1.0e-7 Msun/yr
- 2018ApJ...852..122H: Vertically isothermal mm dust; ISM beta upper limit 1.7
- 2017A&A...603A..10B: Keplerian rotation around 10 Msun
- 2016ApJ...827...81I: Dense gas uniformly distributed in CND; r_out = HWHM of H2 1-0 S(1) disk; uncertainty set by M_dense/M_BH
- 2019ApJ...876..130H: gas disk dominates over stellar component; radius = HWHM of ALMA emission along major axis
- 2024ApJ...971..129C: Sigma_g/Sigma_d=100 for Q profile
- 2020MNRAS.493L.108B: Stellar mass 1.7 Msun
- 2020ApJ...890..130T: T ∝ R^-0.46 from models
- 2025A&A...693A..76C: X_CH3CN=1e-9, mu=2.8, thermal sigma_v, Tk=Trot
- 2025A&A...693A.311P: axisymmetric homogeneous thin gas disk, negligible dark matter, H_gas/R_gas<0.1
- 2016Sci...353.1519P: gas-to-dust ratio 100; kappa 2.4 cm2/g (RT), 2.3 cm2/g (Toomre Q)
- 2019ApJ...877L..25M: 50% of accreting mass goes to outflow
- 2019Natur.569..519K: gas velocity dispersion 6 km/s from M33 HI
- 2017A&A...604A.117C: velocity gradients trace rotation of a disk; inclination not corrected
- 2024ApJ...966..119L: Pre-burst snowline at 4 au
- 2020ApJ...893..125U: kappa_abs(Band 3)=9.2e-2 cm2/g; T=30 K; stellar mass 0.8 Msun
- 2018ApJ...869L..47Z: GI limit with Toomre Q=1 caps gas surface density; preferred alpha=1e-3 and DSD1
- 2019A&A...627L...6M: Optically thin; steeper T profile or optical depth would lower Q
- 2019ApJ...870...80L: [CII] traces gas; M_g=1.5e11 Msun; a=sqrt(3); sigma_r used as upper limit on turbulent dispersion
- 2025ApJ...984L..19Y: Disk gravitationally stable (no spirals)
- 2019ApJ...877..100Y: dust opacity 3 cm2 g-1, gas-to-dust ratio 100
- 2018ApJ...861...91H: kappa = 10 (nu/1 THz)^beta cm2/g, beta=1, gas-to-dust 100, Td = 30 K, central mass 0.15 Msun
- 2018MNRAS.476..122V: Canonical σ=8 km/s alternative; eccentricity 0.2
- 2018A&A...613A..34P: gas virialized; inclination 54 deg from axial ratio
- 2018ApJ...864L..25O: kappa = 6.8e-4 cm2/g at 1.2 mm; T = 20-100 K
- 2019ApJ...882L..31B: constant accretion rate over disk lifetime; all accreted mass once in disk
- 2016ApJ...818..158A: kappa0=0.01 cm2/g, nu0=230 GHz, beta=0.729


### Limitations the authors admit
- 2018ApJ...869L..46D: Dust opacity uncertain by a factor of 10; temperature only estimated
- 2018ApJ...869L..46D: Results not definitive; starting point for more complex modeling
- 2019ApJ...871..185L: Source catalogue edits are subjective
- 2019ApJ...871..185L: Thickness H(r) cannot be measured; assumption oversimplified
- 2019A&A...623A..79C: Non-circular motions in barred galaxies not modelled; torus decoupling and missing flux add uncertainty
- 2019A&A...631A..91G: A521 lacks resolution along the major axis, so differences may be hidden
- 2024ApJ...970..153A: Non-axisymmetric substructure, flows, warps, magnetic pressure and 2D temperature uncertainty could bias results
- 2020ApJ...891...48H: Temperature, flux calibration and degeneracies prevent precise grain size measurements
- 2021A&A...656A..60A: Missing flux ~40-50% due to lack of single-dish data.
- 2021A&A...656A..60A: Mass model parameters are degenerate.
- 2020A&A...635A...2S: Temperatures assumed rather than measured; unresolved multiplicity biases CMF
- 2020A&A...635A...2S: Low number statistics limit Q-parameter conclusions
- 2025NatAs...9.1833L: Masses are lower limits due to optical depth and missing flux
- 2025NatAs...9.1833L: Secondary disks cannot be confirmed with current sensitivity and resolution
- 2025ApJ...995..151Y: Constant Galactic alpha_CO adds systematic uncertainty; no resolved metallicity
- 2025ApJ...995..151Y: Two galaxies have slopes from only two CO data points
- 2014A&A...565A..59D: Disk barely resolved so flux distribution and dynamical mass uncertain
- 2025NatAs...9.1553F: Magnification systematic uncertainty up to ~25%
- 2025NatAs...9.1553F: Clump number may increase with better data; ALMA beam larger than clumps so gas mass only for 7 clumps
- 2020Natur.581..269N: Unresolved JVLA only probes total molecular mass within ~15 kpc beam
- 2015ApJ...806...17R: Warm-gas mass per nucleus uses global Herschel ratio
- 2015ApJ...808..102K: Inner radii unreliable due to resolution and decoherence; constant beta assumed; kappa0 uncertain by factor two
- 2014A&A...569A..11S: Extended emission resolved out; H13CO+ linewidths are lower limits; missing flux affects abundances.
- 2014ApJ...784...78R: Cannot tell whether gas lies in front of or behind the BCG
- 2018ApJ...852..122H: Models are not optimal; dust modeling and multi-line fitting deferred; perturbed temperature model not physically self-consistent
- 2018ApJ...852..122H: Absolute alpha uncertain by ~0.4 from flux calibration
- 2017A&A...603A..10B: Mass estimates are lower limits due to optical depth and >99% flux filtered out
- 2017A&A...603A..10B: Central mass cannot be determined from pv diagrams
- 2016ApJ...827...81I: Small, inhomogeneous samples; tentative results; fixed eta and uncertainties not fully included
- 2016ApJ...827...81I: Most CNDs unresolved so Sigma_dense not measured
- 2019ApJ...876..130H: Single dust temperature assumed across sources, affecting Sigma_SFR maps
- 2019ApJ...876..130H: Interpretations require kinematic confirmation; small sample
- 2024ApJ...971..129C: Only two bands constrain four parameters; priors needed; porosity unconstrained
- 2020MNRAS.493L.108B: Gas mass depends on CO/H2 ratio, possible freeze-out, optical thickness and isotope ratios; precise effects need dedicated modelling.
- 2021A&A...655A..25Z: Nuclear region barely resolved; higher resolution needed
- 2021A&A...655A..25Z: Cannot discriminate consecutive episodes from a decelerating wind
- 2020ApJ...890..130T: Optically thick emission yields mass underestimates; envelope contamination possible; Gaussian radius biases
- 2025A&A...693A..76C: Disk model is a toy proof of concept; H2CO method unreliable near the star
- 2025A&A...693A.311P: One network per galaxy; simulations lack bars, clumps and misalignments; uncertainties not physical
- 2015ApJ...806L..17S: The pressure estimate has considerable uncertainty
- 2016Sci...353.1519P: Contrast values are lower limits because of possible beam dilution and higher optical depth.
- 2019ApJ...877L..25M: Beta uncertainty dominates Q; kinematic model not finely fitted; larger-scale envelope resolved out
- 2019Natur.569..519K: Extinction correction might underestimate attenuation toward GMC density peaks
- 2019Natur.569..519K: eps_sf and eta_fb depend on CO-to-H2 and Halpha-to-SFR conversion factors
- 2017A&A...604A.117C: alpha_CO and r43/10 make gas surface densities uncertain by a few tenths of a dex.
- 2017A&A...604A.117C: 27% of expected continuum flux missed.
- 2024ApJ...966..119L: Velocity resolution and S/N are too low to robustly examine arm kinematics and spirals
- 2020ApJ...893..125U: Flux calibration uncertainties may be larger than official values; absolute opacity is uncertain.
- 2018ApJ...869L..47Z: Gap profiles fitted at fixed 1000 orbits; dust feedback ignored
- 2018ApJ...869L..47Z: Occurrence rates are upper limits since gaps may not be planetary
- 2019A&A...627L...6M: Free-free contamination is uncertain so the inner ring is speculative
- 2017ApJ...845..170B: Gas masses subject to large systematic uncertainty from unknown alpha_CO in ETGs
- 2017ApJ...845..170B: Beam smearing contributes to observed line widths
- 2019ApJ...870...80L: Constant dust temperature assumed, uncertainty within factor ~2
- 2025ApJ...984L..19Y: CO/H2 ratio uncertain; absolute gas surface density scales as X_CO^-0.5
- 2025ApJ...984L..19Y: Dust opacity model uncertainty affects gas-to-dust ratio; limited spatial resolution
- 2019ApJ...877..100Y: Disk masses are the largest uncertainty; gas-to-dust ratio unconstrained
- 2018ApJ...861...91H: VLA 1623 sources lie outside the inner 1/3 of the primary beam where polarimetry is considered reliable.
- 2018ApJ...861...91H: CB disk size may be a lower limit due to maximum recoverable scale.
- 2018MNRAS.476..122V: Edge-on geometry gives degenerate, upper-limit velocity dispersions
- 2018A&A...613A..34P: SED fit limited by differential magnification precision and lack of short-wavelength data
- 2019MNRAS.485..739M: Gas mass is a lower limit because C18O/CO abundance could differ from ISM values.
- 2019MNRAS.485..739M: Resolution of ~1 arcsec dilutes azimuthal variations.
- 2018ApJ...864L..25O: Mass may be an upper limit or apparent value because of non-Keplerian gravity and unresolved material
- 2016ApJ...823...68S: Missing short spacings; fluxes are lower limits; outflow mass highly uncertain
- 2016ApJ...827...34O: Gas mass from a single mid-J CO line is highly uncertain; low-J CO needed
- 2016MNRAS.461..385B: Not a single best-fit model; outer disc emission over-predicted; SED modelling degenerate
- 2019A&A...623L...8B: Masses are lower limits due to optically thin assumption
- 2019A&A...623L...8B: Sample incomplete; faint small disks cannot be excluded
- 2019ApJ...882L..31B: Model assumes smooth radial gas density; gas mass is a lower limit due to isotope-selective photodissociation and carbon depletion
- 2016ApJ...818..158A: Only 17 of 780 baselines exceed 10 km; images could be improved

### Settings cards flag as needed but not stated
- line-free channels used for continuum subtraction: 5
- self-calibration solution intervals and number of iterations: 3
- self-calibration solution intervals: 3
- cell and image size: 2
- flux calibration uncertainty: 2
- moment-map clipping thresholds: 2
- casa version and pipeline version: 2
- exact radial profile data files and per-source geometry (pa, center) used: 1
- alma project code, observing dates, configurations in this paper: 1
- imaging parameters (robust, tclean settings) of dsharp images: 1
- exact prior ranges and likelihood form for the emcee fit: 1
- opacity table for dsharp model vs grain size for a_max limits: 1
- parameters of the 1-d evolution code (grid, code name) and w_max definition per ring details: 1
- calibrator names and flux scale: 1
- line-free channels used for uvcontsub: 1
- clean threshold, masks, niter: 1
- weights used to combine alma and aca data: 1
- electron temperature/line width used for the h30alpha free-free model: 1
- details of the ch3cn temperature fit: 1
- dendrogram settings beyond thresholds, and exact manual source edits: 1
- clean threshold, number of iterations, and deconvolver: 1
- details of the ellipse fits used to define torus size and the integration region: 1
- exact grid of bh masses and inclinations explored, and the compromise criterion between pv and disp…: 1
- which archival cycle-0 data and which configurations were combined for each galaxy: 1
- self-calibration and calibrator names: 1
- primary distances/inclinations per galaxy used in models: 1
- code for particle simulations not given: 1
- line-free channels / continuum subtraction and clean thresholds: 1
- exact casa version and pipeline version: 1
- velocity-axis reference used for moment maps and moment masking details: 1
- annulus widths, aperture definitions, and toomre-based velocity dispersion setup of the simulation …: 1
- instrumental broadening values sigma_instr for alma and muse: 1
- dessauges-zavadsky et al. gas masses/fractions: 1
- flux calibrators and flux scale uncertainty: 1
- exact maps data product versions/urls for mwc 480 cubes: 1
- mwc 480 priors for layer 2/3 beyond statement of same procedure; priors for stellar luminosity etc.: 1
- details of the exponentially tapered temperature fits and bilinear interpolation: 1
- csalt package is in preparation; mock-cube settings partly unspecified: 1
- gap parameters were manually tuned without a fitting procedure: 1
- number of posterior draws n2/n3 for mwc 480 layer 4 beyond 1000 draws: 1

## Paper excerpts (40 of 51, chosen for detail and spread over fields/years)

### 2018ApJ...869L..46D: The Disk Substructures at High Angular Resolution Project (DSHARP). VI. Dust Trapping in Thin-ringed Protoplanetary Disks (2018; protoplanetary_disks; large_program_or_survey)
- question: Are the narrow high-contrast dust rings in DSHARP disks caused by dust trapping in radial pressure bumps, and what does this constrain about turbulence and grain size?
- step 4: Constrain trapping parameters (alpha/St, w, Sigma_g, grain size)
  - method: Analytic steady-state Gaussian trap model w_d=w(1+psi^-2)^-1/2; alpha/St=[(w/w_d)^2-1]^-1 for w_min and w_max; Toomre Q>2 upper limit on Sigma_g [5.3 Application to the observed rings: "\frac{\alpha_{\mathrm{turb}}}{\mathrm{St}} \equiv \psi^{2} = \left[\left(\frac{w}{w_{\mathrm{d}}}\right)^2-1\right]^{-1}"]
  - parameter: Sc=1; xi_dust=1.67 g/cm^3; example a=0.02 cm [5.3 Application to the observed rings: "the average material density of the dust aggregates is $\xi_{\mathrm{dust}}\simeq 1.67{}\,\mathrm{g}/\mathrm{cm}^3$"]
  - assumption: Perfect trapping, fixed Gaussian pressure bump, no back-reaction [5 The rings as dust traps: "The pressure bump is assumed to be so strong that the dust trapping in these rings is perfect: no dust escapes."]
  - validation: Compared to 1-D numerical drift-diffusion model of a planet gap [6 Planet gaps: "We see that the width of the numerical profile of the dust surface density is more or less consistent with the analytic result"]
- result: Minimum w_d/w (AS 209 ring 1, w=w_max) = 0.17 ± not stated dimensionless [Conclusions: "we find that the strongest dust trapping occurs in AS 209, with $w_d/w$ ratios of 0.17 and 0.21 for rings 1 and 2, respectively."]
- result: Grain-size upper limits from opacity = 1 cm to half a meter ± not stated cm [Conclusions: "from opacity arguments we can put strong upper limits on the grain size of 1 cm to half a meter, depending on the ring."]
- limitation (authors): Dust opacity uncertain by a factor of 10; temperature only estimated [4.1 Optically thin approximation: "can easily be wrong by a factor of $10$ upward or downward, with correspondingly large changes in the derived dust mass"]
- limitation (authors): Results not definitive; starting point for more complex modeling [7.3 Caveats of the models: "This paper is therefore not meant to give definitive numbers or conclusions."]
- not stated (card): Exact radial profile data files and per-source geometry (PA, center) used; ALMA project code, observing dates, configurations in this paper; Imaging parameters (robust, tclean settings) of DSHARP images; Exact prior ranges and likelihood form for the emcee fit; Opacity table for DSHARP model vs grain size for a_max limits; Parameters of the 1-D evolution code (grid, code name) and w_max definitio…

### 2019ApJ...871..185L: Investigating Fragmentation of Gas Structures in OB Cluster-forming Molecular Clump G33.92+0.11 with 1000 au Resolution Observations of ALMA (2019; star_formation, milky_way_ism; observational_alma_primary)
- question: How do gas structures in the OB cluster-forming clump G33.92+0.11 fragment into YSO candidates, and is the fragmentation consistent with Toomre instability and Jeans lengths?
- step 3: Toomre Q
  - method: Enclosed gas mass from 225 GHz flux, assumed T(r); centrifugal balance; Q = kappa cs/(pi G Sigma) [Toomre instability: "We then estimate the enclosed gas mass in radius $r$ based on the observed 225 GHz flux and an assumed gas temperature profile $T(r)$"]
  - parameter: 0 or 30 Msun central stellar mass [Toomre instability: "(2) there is a total of 30 $M_{\odot}$ of stellar mass embedded at the center of the system."]
  - assumption: Constant 30 K fiducial, or radial profile; optically thin; gas-to-dust 100; flattened rotating [Toomre instability: "our fiducial analysis assumes a constant 30 K temperature across the entire source."]
  - validation: CH3CN temperatures broadly consistent with profile [Toomre instability: "These measurements are in general consistent with the temperature model described by Equation"]
- limitation (authors): Source catalogue edits are subjective [Identifying candidates of young stellar…: "Our edits to the identified source catalogue is subjective to some extent."]
- limitation (authors): Thickness H(r) cannot be measured; assumption oversimplified [Spatial separations of young stellar ob…: "This assumption of the thickness of gas structure is likely yet oversimplified."]
- not stated (card): Calibrator names and flux scale; Line-free channels used for uvcontsub; clean threshold, masks, niter; Weights used to combine ALMA and ACA data; Electron temperature/line width used for the H30alpha free-free model; Details of the CH3CN temperature fit; Dendrogram settings beyond thresholds, and exact manual source edits

### 2019A&A...623A..79C: ALMA observations of molecular tori around massive black holes (2019; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: Do nearby Seyfert galaxies host molecular tori resolved by high-resolution ALMA CO(3-2), what are their properties, and what black hole masses follow from the gas kinematics?
- step 5: Fit BH mass from gas dynamics
  - method: Particle disk simulations projected into model cubes normalized to observed moment 0; vary BH mass and torus inclination (about a dozen values each); minimize weighted least squares over PV diagram, moments and cube [4.4.2 Fitting the PV diagrams: "The criterion is then to minimize the quantity: $\sum\limits_{pix} w (F_{obs}-F_{mod})^2 / \sum\limits_{pix} w F_{obs}^2$"]
  - parameter: 1 million particles, Toomre Q=1, nuclear region 120 pc diameter [4.4.2 Fitting the PV diagrams: "We used typically one million particles to ensure sufficient statistics."]
  - assumption: Axisymmetric disks only; bar/spiral perturbations neglected [4.4.2 Fitting the PV diagrams: "It should be noted that we simulate only axisymmetric disks."]
  - fitting: Least-squares grid exploration; best fit a compromise between PV diagram and velocity dispersion map [4.4.2 Fitting the PV diagrams: "The best fit must therefore be a compromise between the PV diagram and the velocity dispersion map."]
  - validation: Method tested on NGC 1672; no-BH model compared [4.4.2 Fitting the PV diagrams: "We tested the methodology on the most regular PV diagram obtained, that of NGC 1672"]
- result: BH masses from gas dynamics, NGC 613 = 7.57 ± .15 log Msun [Table 6: "| N 613 | 6.87$\pm$.27 | 7.60$\pm$.35 | (1) | 7.57$\pm$.15 | 42.1 |"]
- result: BH mass from gas dynamics, NGC 1672 = 7.70 ± .1 log Msun [Table 6: "| N1672 | 7.08$\pm$.9 | 6.00$\pm$.6 | (6) | 7.70$\pm$.1 | 39.3 |"]
- result: BH mass range from gas dynamics = 4e6 to 5e7 ± not stated Msun [4.4.3 Summary of results on black hole …: "The black hole masses obtained are between 4 x 10$^6$ and 5 x 10$^7$ M$_\odot$"]
- limitation (authors): Non-circular motions in barred galaxies not modelled; torus decoupling and missing flux add uncertainty [5.3 Black hole masses: "We postpone to further work the simulation of the non-circular motions in these barred galaxies, including both small and large scale."]
- not stated (card): Line-free channels used for continuum subtraction; CLEAN threshold, number of iterations, and deconvolver; Details of the ellipse fits used to define torus size and the integration region; Exact grid of BH masses and inclinations explored, and the compromise criterion between PV and dispersion fits; Which archival cycle-0 data and which configurations were combined for each galaxy; Self-calibrati…

### 2019A&A...631A..91G: Towards sub-kpc scale kinematics of molecular and ionized gas of star-forming galaxies at z ∼ 1 (2019; high_z_galaxies; observational_alma_primary)
- question: Do molecular (CO) and ionized ([O II]) gas rotation curves and velocity dispersions differ in two lensed z~1 galaxies, and can disk geometry (radius, thickness) explain it?
- step 5: Model rotation curves with particle disks
  - method: Stellar and gas Miyamoto-Nagai disks of particles in equilibrium; project at inclination, average LOS velocities, smooth to observed resolution, extract along major axis; vary R_gas, H_gas and resolution H*tan(i) [5.1 Model: "we assume an inclination and then produce a 2D velocity map by taking the average velocity of the particles along the line of sight in each spatial element."]
  - parameter: Snake: M*=4.0e10, R*=3.8 kpc, H*=0.5 kpc, f_mol=0.20, R_mol=0.75 kpc, H_mol=0.1 kpc, R_ion=6.1 kpc, H_ion=1-3 kpc, Q=0.6, i=70 deg [Table 2: "| $H_{mol}$ \[kpc\] | 0.1 |"]
  - assumption: Dark matter and bulge neglected; Toomre Q=sqrt2 sigma0/(vrot fgas) [6.1: "Given that we are observing only the baryon-dominated central parts of a relatively massive galaxy, the contribution from the dark matter is negligible."]
  - validation: Simulated curves compared to observed CO and [O II] curves [6.1: "The simulations are in very good agreement with the observed rotation curves."]
- result: Molecular effective radius, Snake = 0.75 ± +0.26/-0.07 kpc [6.1: "we measure the molecular effective radius to be $R_{mol}=0.75^{+0.26}_{-0.07}$ kpc"]
- result: Ionized effective radius, Snake = 6.1 ± +1.4/-1.0 kpc [6.1: "$R_{ion}=6.1^{+1.4}_{-1.0}$ kpc for the ionized gas disk"]
- result: Stellar effective radius, Snake = 3.8 ± 0.7 kpc [6.1: "We measure a stellar effective radius of $R_\star=3.8\pm0.7$ kpc"]
- result: Toomre Q, Snake = ~0.6 ± not stated dimensionless [6.1: "We, therefore, get $Q\sim0.6$ for both the molecular and ionized gas disks"]
- result: R_mol and R_ion, A521 = 5.8 and 6.5 ± 1.0 and 1.2 kpc [6.2: "($R_{mol} = 5.8\pm 1.0$ kpc) with respect to $[$O II$]$ ($R_{ion} = 6.5\pm 1.2$ kpc)"]
- result: Ionized gas mass, Snake = 2.0e7 ± 0.2e7 Msun [6.1: "We estimate the ionized gas mass to be $(2.0\pm0.2)\times10^7 M_\odot$"]
- limitation (authors): A521 lacks resolution along the major axis, so differences may be hidden [3.1: "The lack of spatial resolution can easily prevent to see a difference between two rotation curves."]
- not stated (card): Line-free channels / continuum subtraction and clean thresholds; Exact CASA version and pipeline version; Cell and image size; Velocity-axis reference used for moment maps and moment masking details; Annulus widths, aperture definitions, and Toomre-based velocity dispersion setup of the simulation code (code not named); Instrumental broadening values sigma_instr for ALMA and MUSE; Dessauges-Zavad…

### 2024ApJ...970..153A: On Kinematic Measurements of Self-gravity in Protoplanetary Disks (2024; protoplanetary_disks; observational_alma_primary)
- question: How accurately and precisely can disk gas masses be measured from the kinematic (self-gravity) signature in resolved CO line data, tested by injection/recovery on synthetic data and demonstrated on MWC 480
- step 5: Layer 4 inference of Md, M*, Sigma parameters
  - method: Fit v_phi model (stellar + pressure + self-gravity) to extracted profiles with emcee; joint 12CO+13CO for MWC 480 [6.3 Demonstration with ALMA Data: MWC 4…: "we then performed the `Layer 4` inference for *both lines* jointly"]
  - software: emcee
  - parameter: 64 walkers, 25,000 steps; priors p~U(0,2), gamma~U(0,6), rt logistic soft bound (600 au for MWC 480), min Q prior [5.3: "again using `emcee` and 64 walkers for 25,000 steps"]
  - assumption: Axisymmetry, no radial/vertical flows, gravitationally stable disk (min Q prior) [4: "This framework assumes the disk structure and kinematics are axisymmetric, and that no external contributions"]
  - fitting: Gaussian likelihood with nuisance f_vphi; emcee [4.4 Layer 4: Kinematics: "where $f_{\tt vphi}$ is a nuisance parameter to account for any under-estimated scatter"]
  - validation: Injection/recovery on fiducial models; MWC 480 compared with Zhang+21 and Martire+24 Sigma profiles [6.3 Demonstration with ALMA Data: MWC 4…: "The general agreement between these independent techniques is striking"]
- result: MWC 480 disk mass Md = 0.13 ± +0.04/-0.01 Msun [Table 3: "0.13 $^{+0.04}_{-0.01}$"]
- result: MWC 480 stellar mass = 2.09 ± +0.06/-0.04 Msun [Table 3: "2.09 $^{+0.06}_{-0.04}$"]
- result: MWC 480 Md/M* = 7 ± ±1 percent [6.3 Demonstration with ALMA Data: MWC 4…: "we inferred a mass ratio $M_{\rm d} / M_\ast = 7\pm1$%"]
- result: MWC 480 taper radius rt = 124 ± +99/-21 au [Table 3: "124 $^{+99}_{-21}$"]
- result: MWC 480 gamma = 1.1 ± +0.3/-0.1 dimensionless [Table 3: "1.1 $^{+0.3}_{-0.1}$"]
- result: Md bias in simulations (full inference) = <~20% ± not stated percent [5.3: "biases for these parameters are $\lesssim$ 2% and $\lesssim$ 20%, respectively"]
- limitation (authors): Non-axisymmetric substructure, flows, warps, magnetic pressure and 2D temperature uncertainty could bias results [6.2 Caveats and Potential: "the azimuthal averaging used in this analysis framework *will* generate artificial $v_\phi(r)$ structures that can bias the $M_{\rm d}$ inference"]
- not stated (card): Exact MAPS data product versions/URLs for MWC 480 cubes; MWC 480 priors for Layer 2/3 beyond statement of same procedure; priors for stellar luminosity etc.; Details of the exponentially tapered temperature fits and bilinear interpolation; csalt package is in preparation; mock-cube settings partly unspecified; Gap parameters were manually tuned without a fitting procedure; Number of posterior dra…

### 2020ApJ...891...48H: A Multifrequency ALMA Characterization of Substructures in the GM Aur Protoplanetary Disk (2020; protoplanetary_disks; observational_alma_primary)
- question: What are the dust substructures, spectral index variations, optical depths and gas cavity of the GM Aur disk at high resolution in Bands 4 and 6?
- step 4: Optical depth and grain size constraints
  - method: tau_nominal = -ln(1 - I/B(T)); beta from tau ratio; emergent intensity with scattering via analytic slab approximation [4.2.2. Constraints on dust grain sizes: "we can use the τ nominal values measured from the 1.1 and 2.1 mm surface brightness models to estimate β in optically thin parts of the disk."]
  - software: dsharp_opac
  - parameter: p = 3.5, 2.5, 1.5; a_min = 0.1 um; Td = 30 K (B40), 18 K (B84) [4.2.2. Constraints on dust grain sizes: "fix the minimum grain size at 0.1 µ m"]
  - assumption: Midplane temperature from Macías et al. 2018; DSHARP opacities; gas-to-dust ratio 100 for Toomre Q [4.2.2. Constraints on dust grain sizes: "assuming the standard gas-to-dust ratio of 100 and a stellar mass of 1.32 M ⊙"]
  - validation: Alternative formulae from Birnstiel 2018 and Zhu 2019 give similar results; McClure temperature structure tested [4.2.2. Constraints on dust grain sizes: "Similar results are obtained using formulae based on the Eddington-Barbier approximation from Birnstiel et al. (2018) and Zhu et al. (2019)."]
- result: Peak nominal optical depth B40 and B84 at 1.1 mm = 0.94 and 0.70 ± not stated dimensionless [4.2.1. Constraints on optical depths: "( τ nominal = 0 . 94 and 0 . 70, respectively)"]
- limitation (authors): Temperature, flux calibration and degeneracies prevent precise grain size measurements [4.2.2. Constraints on dust grain sizes: "the aim of this section is to comment on which regions of parameter space are consistent with the observations rather than to provide precise measurements."]
- not stated (card): Line-free channels flagged for Band 6 continuum; Self-calibration solution intervals and number of iterations; Gaussian taper parameters for the HCO+ cube; CLEAN thresholds and image size/cell size; Exact visibility binning and weight handling code for the MCMC fits; Which data reduction scripts were used (not released)

### 2021A&A...656A..60A: Black hole feeding and star formation in NGC 1808 (2021; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: How is the AGN of NGC 1808 fed, and how do star formation and feedback behave in the central few hundred pc, based on the kinematics of the molecular gas?
- step 6: Rotation curve mass model and resonances
  - method: Fit mass components (Plummer bulge/dark matter, Toomre disk, BH) to HI and Halpha rotation curve to derive Omega, kappa and Lindblad resonances [4.4 Lindblad resonances: "We use Plummer spheres for spherical components, bulge and dark matter, and Toomre disks for the 2D ones."]
  - parameter: corotation at ~1.2 bar radius [4.4 Lindblad resonances: "We have placed the corotation at $\sim$1.2 bar radius"]
  - assumption: parameters not unique [4.4 Lindblad resonances: "the parameters are not unique and just a realistic representation of the potential"]
  - fitting: Dark matter as free parameter to fit V(R) [4.4 Lindblad resonances: "The dark matter component is the free parameter to better fit the rotation curve V(R)"]
- limitation (authors): Missing flux ~40-50% due to lack of single-dish data. [3.3 CO luminosity and H2 mass: "Our rather smaller value derived with the ALMA high resolution observations is due to lack of single-dish observations to detect weak extended emission"]
- limitation (authors): Mass model parameters are degenerate. [4.4 Lindblad resonances: "Given the freedom and the degeneracy to distribute all mass components"]
- not stated (card): Line-free channels used for continuum; Robust/taper and cell/image size in GILDAS; Clean masks and stopping thresholds; Rest frequencies and velocity frame for the cubes; Tilted-ring fit initialization, ring widths beyond 0.3'' and 3DBarolo parameters; Aperture positions/fluxes for KS regions and Pa-alpha extinction values; Mass model parameter fitting details; Treatment of missing-flux correctio…

### 2020A&A...635A...2S: Physical properties of the star-forming clusters in NGC 6334. A study of the continuum dust emission with ALMA (2020; star_formation, milky_way_ism; observational_alma_primary)
- question: What are the core mass function, spatial distribution of cores and mass segregation in the star-forming clusters of NGC 6334, and how do they relate to cluster evolutionary stage and fragmentation physics?
- step 4: Identify clusters and measure spatial structure
  - method: Seven scikit-learn clustering algorithms with K=4 from elbow and silhouette analysis; membership by vote (>=60%); MST, Q parameter, nearest-neighbour KDEs, two-point correlation function [4.1 Cluster identification: "If this value is lower than 60%, we consider that we can not assign the corresponding core to one of the clusters."]
  - software: scikit-learn, NetworkX, FragMent
  - parameter: TPCF with 10000 random instances per cluster [4.2 Spatial structure of the clusters i…: "We compute the random separation distributions ($DR(r)$ and $RR(r)$) by producing 10 000 instances of randomly placed points for each cluster"]
  - fitting: Q uncertainty from 100 random 20% subsamples with Gaussian fit [4 Clusters in NGC 6334: "Repeating this process 100 times, we obtained a distribution of the measured values of $Q$."]
  - validation: Cross-check of number of clusters with elbow and silhouette [4.1 Cluster identification: "both methods suggest that the number of clusters in our region is between 2 and 6, with $K=4$ the most probable value."]
- result: Q parameter, whole region = 0.60 ± 0.1 dimensionless [4 Clusters in NGC 6334: "we obtain $Q=0.60\pm0.1$"]
- limitation (authors): Temperatures assumed rather than measured; unresolved multiplicity biases CMF [5.1 Core mass function: "the measured slope can be biased due to the uncertainty in temperature determination and the unresolved multiplicity in the massive cores."]
- limitation (authors): Low number statistics limit Q-parameter conclusions [4.2 Spatial structure of the clusters i…: "the total number of sources in that cluster (10) limits the conclusions that can be derived from this analysis."]
- not stated (card): Line-free channel ranges used for continuum; tclean multiscale scales, image size, masking and threshold; Self-calibration solution intervals; SExtractor parameters beyond thresholds (filter, mesh size); Hyperparameters of the seven scikit-learn clustering algorithms; How the SExtractor flux was corrected for ACA/combined images and which image (super-resolution vs combined) was used for the cata…

### 2025NatAs...9.1833L: Detection of a septuple stellar system in formation via disk fragmentation (2025; star_formation; observational_alma_primary)
- question: Can disk fragmentation in a gravitationally unstable disk form an extreme high-order (septuple) protostellar system in the high-mass region NGC 6334IN?
- step 6: Toomre Q maps
  - method: Q = c_s kappa/(pi G Sigma) with Keplerian kappa from M_cl=7.6 Msun, Sigma from disk mass 2.71 Msun, T maps [Calculation of the Toomre $Q$ parameter: "$\kappa$ is epicyclic frequency that is equivalent to the angular velocity $\Omega$ = $\sqrt{GM/r^3}$ in the case of a Keplerian disk."]
  - assumption: Q<1-2 unstable [Calculation of the Toomre $Q$ parameter: "The disk becomes unstable against axisymmetric gravitational stability if $Q <$ 1–2"]
  - validation: Uncertainty 54% propagated [Calculation of the Toomre $Q$ parameter: "Then the uncertainty in the Toomre $Q$ parameter is estimated to be 54%."]
- result: Toomre Q uncertainty = 54% ± not stated percent [Calculation of the Toomre $Q$ parameter: "Then the uncertainty in the Toomre $Q$ parameter is estimated to be 54%."]
- limitation (authors): Masses are lower limits due to optical depth and missing flux [Main text: "The derived masses are considered as lower limits due to the optical depth effects and missing flux in the interferometric data."]
- limitation (authors): Secondary disks cannot be confirmed with current sensitivity and resolution [Gas properties around the septuple syst…: "Higher resolution and sensitivity observations are needed to confirm the presence of individual secondary disks around the condensations."]
- not stated (card): Line-free channel ranges for continuum; Image size and cell size, clean threshold and masks for tclean; Exact XCLASS fitting setup (priors, column density/linewidth ranges, source size); 3DBarolo parameters (ring radii, widths, masks, fixed/free parameters); Which line-free channels and uv range exact for imfit preselection (units of uv cut given as '>1.3 km'); Rest frequencies of lines; Radiativ…

### 2025ApJ...995..151Y: Molecular Gas and Star Formation in Dwarf Galaxies Observed by the Atacama Large Millimeter/submillimeter Array (2025; nearby_galaxies; archival_reuse)
- question: Do dwarf galaxies follow the molecular star formation law of massive spirals, and is their star formation regulated by gravitational stability (Toomre Q)?
- step 6: Compute Toomre Q_tot
  - method: Two-component thick-disk Q from gas and stars [3.3 Gravitational Instability: "The total $Q$ parameter ($Q_{\rm tot}$) is calculated using the approximation given by (cite: 2011MNRAS.416.1191R)"]
  - parameter: sigma_g = 5 km/s; sigma_star,r = 30 km/s [3.3 Gravitational Instability: "We adopt $\sigma_g = 5$ km s$^{-1}$, a representative value for dwarf galaxies"]
  - assumption: Q_g from H2 only; sigma_z/sigma_r = 0.6 stars, 1 gas [3.3 Gravitational Instability: "we compute $Q_{\rm g}$ using only $\Sigma_{\rm H_2}$"]
- result: Q_tot range = 0.9 to 1.5 ± not stated dimensionless [3.3 Gravitational Instability: "The $Q_{\rm tot}$ values range from 0.9 to 1.5"]
- limitation (authors): Constant Galactic alpha_CO adds systematic uncertainty; no resolved metallicity [3.2 Molecular SFL: "We note that the adopted $\alpha_{\rm CO}$ introduces an additional systematic uncertainty."]
- limitation (authors): Two galaxies have slopes from only two CO data points [3.2 Molecular SFL: "the slope estimates rely on only two central data points where CO is significantly detected"]
- not stated (card): Spectral setup and observing details (dates, configurations, time on source); Imaging cell size, image size, channel width, clean threshold, masks; Line-free channels and whether continuum was subtracted; Moment map generation method; Radial profile center and exact annulus handling, and how fits were done (weighting); Rotation curve values used for kappa; How the 7.5'' convolution kernel was set…

### 2014A&A...565A..59D: ALMA resolves turbulent, rotating [CII] emission in a young starburst galaxy at z = 4.8 (2014; high_z_galaxies; observational_alma_primary)
- question: What are the spatial distribution and kinematics of [CII] and rest-frame far-infrared emission in the z=4.76 SMG ALESS 73.1, and what do they imply for its dynamical mass, stability and metallicity?
- step 4: Toomre Q map
  - method: Q = sqrt2 sigma V /(pi r G Sigma) per pixel using [CII] luminosity as proxy for Sigma, flat rotation curve [3.4 Stability of the disk: "using the [Cii] luminosity distribution as a proxy to determine $\Sigma$"]
  - assumption: [CII] traces molecular gas kinematics [3.4 Stability of the disk: "We therefore assume that the [Cii] emission traces well the kinematics of the underlying star-forming molecular gas component"]
- result: average Toomre Q = 0.58 ± 0.15 dimensionless [3.4 Stability of the disk: "The average $Q$ over the disk is 0.58$\pm$0.15"]
- limitation (authors): Disk barely resolved so flux distribution and dynamical mass uncertain [3.2 [Cii] velocity analysis: "as we barely spatially resolve the flux distribution within the disk, we cannot distinguish which flux distribution is more appropriate"]
- not stated (card): Whether archive or self-produced calibration; CASA version; Line-free channels and continuum/line mask; Cell size, image size, clean threshold; Initial guess and fitting details of the dynamical model code (Gnerucci-type) and priors; MCMC priors and likelihood for M_dyn-i; KinMS_fit setup (unpublished); Toomre Q aperture and weighting choices; [CII]-to-gas-surface-density conversion; Details of t…

### 2025NatAs...9.1553F: Primordial rotating disk composed of at least 15 dense star-forming clumps at cosmic dawn (2025; high_z_galaxies; observational_alma_primary)
- question: How do the internal clumpy substructure and the underlying gas dynamics of a lensed young galaxy at z=6.072 relate, and how does this compare with simulations?
- step 3: Derive gas mass and Toomre Q
  - method: [C II] luminosity to Mgas with alpha=31; Q=kappa sigma/(pi G Sigma_gas) radial profile from 3DBarolo plus pixel-by-pixel 2D map [10. Toomre Q parameter: "First, we derived the radial profile of the Toomre $Q$ parameter by employing non-parametric radial profiles of the best-fit $V(R)$ and $\sigma(R)$"]
  - software: 3DBarolo
  - parameter: alpha_[CII]=31 Msun/Lsun [10. Toomre Q parameter: "conversion factor of $\alpha_{\rm [CII]}=31\,M_{\odot}/L_{\odot}$"]
  - assumption: Dark matter negligible in dynamical mass; gas-to-dust ~1e3 for cross-check [10. Toomre Q parameter: "assuming that the dark matter contribution is negligible"]
  - validation: Mgas consistent with Mdyn-Mstar and dust-based estimates; factor-2 uncertainty acknowledged [10. Toomre Q parameter: "This is in excellent agreement with the $M_{\rm gas}$ estimate of $1.1^{+0.4}_{-0.1}\times10^{9}\,M_{\odot}$"]
- result: Toomre Q (radially averaged) = 0.2-0.3 ± not stated dimensionless [10. Toomre Q parameter: "Toomre $Q$ parameter in a range of $\simeq$ 0.2–0.3"]
- result: Gas mass from [C II] = 1.1e9 ± +0.4/-0.1 Msun [Extended Data Table 3: "$1.1^{+0.4}_{-0.1}\times10^{9}$"]
- result: Dynamical mass within 2 re = 1.7e9 ± +0.7/-0.8 Msun [10. Toomre Q parameter: "$M_{\rm dyn}=1.7^{+0.7}_{-0.8}\times10^{9}\,M_{\odot}$"]
- limitation (authors): Magnification systematic uncertainty up to ~25% [4. Lens model: "we conclude that the magnification uncertainty in this study does not exceed $\sim$25%"]
- limitation (authors): Clump number may increase with better data; ALMA beam larger than clumps so gas mass only for 7 clumps [7. Properties of the individual star-fo…: "while this number could be increased with further high-resolution observations in the future"]
- not stated (card): Line-free channels and frequency range used for continuum fit; Source-plane reconstruction algorithm details and resulting cube pixel scale; 3DBarolo parameter file settings (ring widths, normalization details, masking thresholds); Calibrators and flux-scale uncertainty for ALMA data; Exact SExtractor/GALFIT convergence setup and PSF used for GALFIT; How [C II] luminosity per pixel was derived fr…

### 2020Natur.581..269N: A cold, massive, rotating disk galaxy 1.5 billion years after the Big Bang (2020; high_z_galaxies; observational_alma_primary)
- question: Is the absorption-selected galaxy DLA0817g at z=4.26 a rotationally supported cold disk, and what are its dynamical and molecular masses?
- step 4: Derive rotation curves, dynamical mass, Toomre Q
  - method: Mean-velocity and peak-velocity rotation curves; Mdyn = 2.32e5 v^2 R; Q averaged over R=3Rd [Dynamical Mass Estimate.: "$M_{\rm dyn}(R)$ = 2.32 $\times$ 10$^{5} v_{\rm rot}(R)^2 R$"]
  - parameter: R = 3 exponential scale lengths = 4.2 kpc [Dynamical Mass Estimate.: "we will assume the extent of the galaxy to be three times the exponential scale length of the modeled emission"]
  - assumption: Spherical mass distribution (30% uncertainty added) [Dynamical Mass Estimate.: "the mass distribution is implicitly assumed to be spherical"]
  - validation: Compared with FWHM-based v_rot of 300 +/- 50 km/s [Dynamical Mass Estimate.: "we get a rotational velocity of 300 $\pm$ 50 km s$^{-1}$"]
- result: Dynamical mass = 7.2e10 ± 2.3e10 Msun [Dynamical Mass Estimate.: "$M_{\rm dyn}$ = (7.2 $\pm$ 2.3) $\times$ 10$^{10} M_\odot$"]
- result: Disk-averaged Toomre Q = 0.96 ± 0.30 dimensionless [Toomre-$Q$ Parameter.: "This yields $\bar{Q} = 0.96 \pm 0.30$ for DLA0817g."]
- limitation (authors): Unresolved JVLA only probes total molecular mass within ~15 kpc beam [main text: "the unresolved JVLA observations can only probe the total molecular mass within the beam of the JVLA observations"]
- not stated (card): Line-free channel ranges for continuum and uvcontsub order; tclean cell size, image size, masks, cleaning threshold, iterations; MCMC priors, walker number, chain length, convergence criteria; Channel range used for the velocity-integrated [C II] map; Radial bin sizes for rotation curves; JVLA calibrators and imaging details; Flux-scale uncertainty for ALMA

### 2015ApJ...806...17R: Morphology and Kinematics of Warm Molecular Gas in the Nuclear Region of Arp 220 as Revealed by ALMA (2015; nearby_galaxies, milky_way_ism; observational_alma_primary)
- question: What are the morphology and kinematics of the warm (CO J=6-5) molecular gas in the two nuclei of Arp 220, and what energy source heats it?
- step 4: Dynamical mass and Toomre Q
  - method: Rotation and dispersion in quadrature for M_dyn within 220 pc; Toomre Q with sigma as sound speed [5 Dynamical Mass and Disk Stability: "Adding the asymptotic rotation velocity (135 km s$^{-1}$) and velocity dispersion (85 km s$^{-1}$) in quadrature"]
  - assumption: Inclination 50 deg for upper mass [Dynamical Mass and Disk Stability: "where the larger number is obtained by correcting the rotation velocity (but not the velocity dispersion) for an inclination of $50^\circ$"]
  - validation: Compared with gas mass 1.1e9 Msun from Paper I [Dynamical Mass and Disk Stability: "this enclosed mass is in agreement with the total molecular gas mass of $1.1 \times 10^{9}$ derived in Paper I from the continuum emission"]
- result: Eastern nucleus dynamical mass within 220 pc = 1.6-2.9e9 ± not stated Msun [5: "we derive a dynamical mass within $r = 220$ pc of $M_\mathrm{tot}\sim 1.6 - 2.9 \times 10^9 M_\odot$"]
- result: Toomre Q eastern nucleus = ~1.5 ± factor of two dimensionless [5: "we find $Q\sim 1.5$; this number should be regarded as uncertain by at least a factor of two"]
- limitation (authors): Warm-gas mass per nucleus uses global Herschel ratio [footnote 5: "our mass estimate for the warm molecular gas for the individual nuclei should be used with caution"]
- not stated (card): Clean thresholds, iteration counts and clean box definitions; Cell size and image size; Line-free channels used for continuum subtraction; Self-calibration solution intervals; Robust/weighting details beyond natural vs uniform; Optimization method for choosing kinematic model parameters (apparently by eye); Rotation curve tabulation for model; Moment-map clipping thresholds; Data cube product not…

### 2015ApJ...808..102K: Resolving Protoplanetary Disks at Millimeter Wavelengths with CARMA (2015; protoplanetary_disks; observational_alma_primary)
- question: What are the physical properties of six Taurus protoplanetary disks from CARMA 1.3 and 2.7 mm visibilities, and does a flared power-law or flared viscous accretion disk model fit better?
- step 6: correlations, Toomre Q and alpha
  - method: Pearson correlation among fitted properties; Toomre Q profile from midplane temperature and surface density; alpha from accretion rate [5.5 Correlations among Properties: "We calculated correlations between the constrained physical properties"]
  - parameter: Q<~1.5 unstable [5.6 Disk Substructures: "regions of $Q \lesssim 1.5$ are gravitationally unstable"]
  - assumption: Keplerian rotation; Haro 6-13 accretion rate assumed 1.0e-7 Msun/yr [5.6 Disk Substructures: "We assumed the accretion rate of Haro 6-13, which has not been reported, as a typical value of $1.0\times 10^{-7}~\textrm{M}_\ensuremath{\odot}~ \textrm{year}^{-1}$."]
- result: beta vs Mdisk correlation = 0.84 ± not stated dimensionless [Table 6: "$\beta$ | 1.00 | **0.84** |"]
- limitation (authors): Inner radii unreliable due to resolution and decoherence; constant beta assumed; kappa0 uncertain by factor two [4.3 Model Parameters: "fitted values can be model-dependent and are likely unreliable due to systematic uncertainties in the observation, primarily the resolution."]
- not stated (card): Fitting code is not named or released; MCMC proposal widths, number of steps, burn-in and annealing schedule not given; Prior ranges for the free parameters; Stellar luminosities and masses adopted in RADMC-3D and photon numbers; Exact flux calibrator fluxes and which tracks were combined per target; Opacity law at infrared wavelengths used in RADMC-3D; Details of how inner radius and center offs…

### 2014A&A...569A..11S: A necklace of dense cores in the high-mass star forming region G35.20-0.74 N: ALMA observations (2014; star_formation, astrochemistry; observational_alma_primary)
- question: What is the fragmentation, kinematics, hot-core chemistry and outflow content of the elongated dense structure in the high-mass star forming region G35.20N, and is it a 1D filament or an edge-on disk-like 'pancake'?
- step 7: Test filament vs pancake
  - method: Toomre Q and cylinder fragmentation spacing/critical mass per length [Nature of the elongated structure: "In practice, one sees that a value of $\Delta V=0.7$ km s$^{-1}$ is required for the theoretical expression to match the observed spacing between the cores"]
- result: Critical line mass vs measured = ~40 critical vs ~200 measured ± not stated Msun/pc [Nature of the elongated structure: "this line width of 0.7 km s$^{-1}$ results in a critical mass per unit length of $\sim$40 $M_{\ensuremath{\odot}}$ pc$^{-1}$, while the measured mass per unit length in our filament is $\sim$200 $M_{\ensuremath{\odot}}$ pc$^{-1}$"]
- limitation (authors): Extended emission resolved out; H13CO+ linewidths are lower limits; missing flux affects abundances. [Dynamical status of the cores: "We note, however, that extended structures are heavily resolved out in our observations."]
- not stated (card): CASA version and calibration (pipeline vs manual) details; line-free channel selection for continuum; clean threshold, mask, cell and image size, deconvolver; myXCLASS fit initial guesses, parameter bounds, and fitting algorithm settings; exact SiO outflow momentum computation inputs; line used for tapered maps' beam

### 2014ApJ...784...78R: Massive Molecular Gas Flows in the A1664 Brightest Cluster Galaxy (2014; galaxy_clusters_and_sz, nearby_galaxies; observational_alma_primary)
- question: What are the mass, kinematics and origin (inflow, outflow or merger) of the molecular gas in the Abell 1664 BCG?
- step 5: Assess origin (merger, inflow, outflow) via energetics and Toomre Q
  - method: Compare outflow energy with radiation pressure, supernova and AGN mechanical power; Toomre Q for putative disk [4.4.1: "Mechanical winds from supernovae are therefore insufficient to accelerate the molecular gas."]
- limitation (authors): Cannot tell whether gas lies in front of or behind the BCG [4.4: "we cannot distinguish between an inflow of gas located behind the BCG and an outflow of gas located in front of the BCG."]
- not stated (card): Line-free channels and continuum subtraction method/order; Image size, cell size, clean threshold and iterations; Channel binning used for spectra; Spectral extraction details and baseline fitting; Flux calibration uncertainty; Pixel/region definitions for clumps A, B and HVS sub-regions; PV slice widths; Luminosity distance value used

### 2018ApJ...852..122H: CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations (2018; protoplanetary_disks, astrochemistry; archival_reuse)
- question: What are the CO and dust properties (CO column density structure, spectral index/grain sizes) in the TW Hya disk at high angular resolution?
- step 5: Constrain grain size / optical depth from spectral index
  - method: Solve alpha(tau, beta, Td) with emission model, limits on tau from brightness temperature and Td<=30 K; Toomre Q stability check [Radial Variation in Grain Sizes: "The dust temperature is likely no more than 30 K in the gaps and rings beyond a radius of 25 AU"]
  - parameter: kappa=3.3 cm2/g at 290 GHz; gas-to-dust 100; T=15 K for Q [Optical Depth Variations: "Assuming an ISM gas-to-dust ratio of 100"]
  - assumption: Vertically isothermal mm dust; ISM beta upper limit 1.7 [Radial Variation in Grain Sizes: "the upper limit on $\beta$ should be the ISM value of $\approx1.7$ (cite: 2006ApJ...636.1114D), when no grain growth has occurred."]
- result: Lower limit on optical depth in gaps/rings outside 25 AU at 290 GHz = >~0.25 ± not stated dimensionless [Radial Variation in Grain Sizes: "this suggests that $\tau\gtrapprox 0.25$ at 290 GHz in the gaps and rings outside 25 AU"]
- limitation (authors): Models are not optimal; dust modeling and multi-line fitting deferred; perturbed temperature model not physically self-consistent [A “Perturbed Temperature" Model: "this model is not physically self-consistent"]
- limitation (authors): Absolute alpha uncertain by ~0.4 from flux calibration [The Spectral Index Between 1.3 mm and 8…: "A $\sim10\%$ flux uncertainty in each band would correspond to an uncertainty in the overall offset of $\Delta \alpha\sim0.4$"]
- not stated (card): Self-calibration solution intervals and number of iterations; Line-free channel ranges for continuum and uvcontsub; Image size and cell size for clean/tclean; clean thresholds and number of iterations; Exact spectral windows used per program; Procedure for how model parameters were chosen beyond 'some experimentation' (no fit/goodness metric); Radial bin and deprojection details for profiles

### 2017A&A...603A..10B: Fragmentation and disk formation in high-mass star formation: The ALMA view of G351.77-0.54 at 0.06'' resolution (2017; star_formation, astrochemistry; observational_alma_primary)
- question: How does the high-mass hot core G351.77-0.54 fragment, and what are the kinematics, temperature structure and gravitational stability of its central disk-like structure at 0.06'' resolution?
- step 6: Toomre Q map
  - method: Q = c_s kappa/(pi G Sigma) per pixel with Keplerian Omega for 10 Msun, Sigma from the continuum; three temperature prescriptions [4.4: "we estimate the Toomre $Q$ parameter for the whole rotating structure around the main source #1 calculating the sound speed $c_s=\sqrt{kT/(2.3m_H)}$"]
  - parameter: T = T_rot; T = 200 K; T ∝ r^-0.4 with 1400 K at 10 AU [4.4: "we use a dust temperature distribution with an approximate dust sublimation temperature of 1400 K at 10 AU"]
  - assumption: Keplerian rotation around 10 Msun [4.4: "using the Keplerian velocity $\Omega$ around a 10 M$_{\odot}$ star"]
  - validation: Three temperature approaches bracket real Q [4.4: "we can consider these Toomre $Q$ maps as the bracketing values for the real physical Toomre $Q$ values in this region."]
- result: Toomre Q minimum, T∝r^-0.4 case = >~1.5 ± not stated dimensionless [4.4: "even the lowest values in the map derived with the temperature distribution are greater than $\sim$1.5"]
- limitation (authors): Mass estimates are lower limits due to optical depth and >99% flux filtered out [3.1: "indicates that more than 99% of the extended flux is filtered out by our extended baseline ALMA data"]
- limitation (authors): Central mass cannot be determined from pv diagrams [4.2: "Hence, determining the exact mass of the central object unfortunately remains difficult."]
- not stated (card): Channel/line selection and fitting ranges, priors and initial parameters for XCLASS pixel-by-pixel fits; Image size, cell size, deconvolver, masks and clean threshold; Self-calibration and flux-scale uncertainty details; Continuum frequency used for the 438 um image (collapsed channels list); How the Toomre Q uncertainties/epicyclic frequency were computed per pixel and inclination; Exact pv-cut …

### 2016ApJ...827...81I: Do Circumnuclear Dense Gas Disks Drive Mass Accretion onto Supermassive Black Holes? (2016; nearby_galaxies, agn_and_quasars; multi_facility_alma_minor)
- question: Is the mass of dense molecular gas (from HCN(1-0)) in ~100 pc circumnuclear disks correlated with the black hole mass accretion rate in Seyfert galaxies, and does the scale of the gas matter?
- step 5: compare with SN-driven accretion model
  - method: Reduced Kawakatu & Wada equation for uniform disk; r_in,eff = max[r_X, r_Q]; Mdot_acc compared to Mdot_BH and Mdot_BH+Mdot_wind for four sources [Comparison with observations: "Using these two radii, we regard the *effective* innermost radius as $r_{\rm in,eff} = {\rm max}[r_{\rm X}, r_{\rm Q}]$."]
  - parameter: n_H2 = 1e6 cm^-3, log(Hx/nH) = -27.5, c_s ~1 km/s, Toomre Q=1 [Comparison with observations: "A gas volume density of $n_{\rm H_2} = 10^6$ cm$^{-3}$"]
  - assumption: Dense gas uniformly distributed in CND; r_out = HWHM of H2 1-0 S(1) disk; uncertainty set by M_dense/M_BH [Comparison with observations: "we simply assume that the dense gas is uniformly distributed within a CND"]
  - validation: Compared with Mdot_BH and nuclear mass flow [Other components of the mass budget$-$g…: "both NGC 7469 and NGC 4051 show good agreement of $\dot{M}_{\rm CND} \sim \dot{M}_{\rm nuclear}$"]
- result: log Mdot_acc NGC 7469 = -1.20 ± 0.30 log Msun/yr [Table 4: "| NGC 7469 | 30.8 | 2.2 | 0.84 | 1.19/260 | 2 | 6.0$\times$10$^{-9}$ | -1.20$\pm$0.30 | -1.22 | 5 |"]
- limitation (authors): Small, inhomogeneous samples; tentative results; fixed eta and uncertainties not fully included [Other components of the mass budget$-$g…: "our results are tentative due to the small sample size, and are based on simplified assumptions"]
- limitation (authors): Most CNDs unresolved so Sigma_dense not measured [Comparison with observations: "most of the CNDs are not resolved spatially at the HCN($1-0$) emission line, so we cannot measure $\Sigma_{\rm dense}$ directly"]
- not stated (card): Velocity ranges for moment-0 integration for NGC 4579 and NGC 7469; Line-free channels and continuum selection for NGC 4579 and NGC 7469; Image size and cell size for NGC 4579 cube; NGC 7469 ALMA data processing (unpublished); linmix_err random seed and convergence checks; How upper limits were handled in the Spearman correlation; Exact references for SFR and wind rates per source (numbered refs …

### 2019ApJ...876..130H: ALMA Reveals Potential Evidence for Spiral Arms, Bars, and Rings in High-redshift Submillimeter Galaxies (2019; high_z_galaxies; observational_alma_primary)
- question: Does sub-kpc-resolution 870 um continuum imaging of ALESS SMGs reveal substructure (clumps, bars, rings, spiral arms), and what does it imply for star formation rate density relative to the Eddington limit?
- step 6: Velocity dispersion constraints (Jeans, Toomre)
  - method: Jeans length equal to largest clump size gives lower limit; Toomre Q<1 with flat-rotation-curve epicyclic frequency gives upper limit; gas surface density from global Sigma_SFR [4.3 Evidence for interaction, bars, rin…: "we derive upper limits for the one-dimensional velocity dispersion of the potentially barred sources of $\sigma_{\rm r} \lesssim$ 70–160 km s$^{-1}$"]
  - assumption: gas disk dominates over stellar component; radius = HWHM of ALMA emission along major axis [4.3 Evidence for interaction, bars, rin…: "Here we assume that the gas disk dominates over the stellar component."]
  - validation: Toomre upper limits marginally consistent with Jeans lower limits [4.3 Evidence for interaction, bars, rin…: "these Toomre-based upper limits are consistent, albeit marginally, with the lower limits derived from equating the sizes of the largest ‘clumps’ observed to the Jeans length"]
- result: Toomre velocity dispersion upper limits = <70–160 ± not stated km/s [Table 5: "| ALESS 76.1 | $>$100 | $<$160 |"]
- limitation (authors): Single dust temperature assumed across sources, affecting Sigma_SFR maps [4.1 The intensity of the star formation: "One important caveat in the above analysis is the previously stated assumption of a single dust temperature across the sources."]
- limitation (authors): Interpretations require kinematic confirmation; small sample [Summary: "a larger sample size is important for moving beyond the handful of submillimeter-brightest sources studied here"]
- not stated (card): multi-scale clean scale values; clean threshold/niter and mask definitions per source; image size and cell size; weighting and taper details for 0.07" and 0.05" maps; the SFR values for each source needed for Sigma_SFR maps (da Cunha et al. in prep); dust-to-gas ratio source (referred to as 'same as above' but not given); Toomre/Jeans calculation details (gas surface density conversion, kappa); g…

### 2024ApJ...971..129C: A Dust-trapping Ring in the Planet-hosting Disk of Elias 2-24 (2024; protoplanetary_disks; observational_alma_primary)
- question: Is the bright ring at 78 au in the planet-hosting disk Elias 24 a dust trap, and what are the dust properties, turbulence and gas-to-dust ratio there?
- step 6: Toomre Q, Stokes number and gas-to-dust ratio
  - method: Sample 1e6 draws of Sigma_d and T; compute Q and St assuming Sigma_g=100 Sigma_d; derive Sigma_g/Sigma_d in ring from tau, St and alpha/St with Q>2 stability [4.3: "we combine the probability distributions of $\Sigma_d$ and $T(r)$ by taking $10^6$ random samples from both at each radius value."]
  - parameter: rho_m=1.675 g/cm3, Q>2 for stability [4.4: "We constrain the lowest allowable Stokes number by requiring that the disk be gavitationally stable ($Q > 2$)."]
  - assumption: Sigma_g/Sigma_d=100 for Q profile [4.3: "$\Sigma_g(r) = 100 \ \Sigma_d(r)$ is the local gas surface density"]
- result: Max Sigma_g/Sigma_d in ring = 27 ± not stated dimensionless [5.2: "we estimate a maximum gas-to-dust ratio of 27"]
- limitation (authors): Only two bands constrain four parameters; priors needed; porosity unconstrained [4.2: "we only have 2 bands with which to constrain the 4 model parameters"]
- not stated (card): tclean multiscale scales, image size, cell size, mask details; Which 3 mm SPWs/channels for continuum and any line-free selection; Model grids, sampling of the marginal probability (grid resolution, number of points) in the radiative transfer fit; Exact 1.3 mm CLEAN parameters (in DSHARP paper); Exact self-calibration reference antenna, SNR thresholds; Fitting of Gaussian to ring: fitting method …

### 2020MNRAS.493L.108B: <SUP>13</SUP>C<SUP>17</SUP>O suggests gravitational instability in the HL Tau disc (2020; protoplanetary_disks; observational_alma_primary)
- question: How much gas mass does the HL Tau disc contain when traced by the rare isotopologue 13C17O, and is the disc gravitationally unstable?
- step 4: Compute Toomre Q profile
  - method: Q = cs kappa/(pi G Sigma) with cs from Tmid, Keplerian kappa, M*=1.7 Msun, Sigma of gas and dust [5.2: "where $c_s$ is the sound speed of the gas (calculated from T$_{\rm mid}$)"]
  - parameter: instability threshold Q<~1.7 [5.2: "Regions of the disc with $Q \lesssim 1.7$ will be susceptible to gravitational instability"]
  - assumption: Stellar mass 1.7 Msun [5.2: "we assume a central star mass of 1.7 M$_{\odot}$"]
  - validation: Magnetic-field correction checked with beta_p ~10 to 10^4 [5.2: "Such values do not alter our minimum Toomre $Q$ value by more than $\sim$5 per cent"]
- result: Minimum Toomre Q = 1.1 at r = 77 au ± +0.5/-0.2 dimensionless [5.2: "with minimum $Q = 1.1_{-0.2}^{+0.5}$ at $r = 77$ au"]
- result: Unstable region (Q<1.7) = 50–110 ± not stated au [5.2: "gravitationally unstable ($Q<1.7$) from approximately 50–110 au"]
- limitation (authors): Gas mass depends on CO/H2 ratio, possible freeze-out, optical thickness and isotope ratios; precise effects need dedicated modelling. [4.2: "The precise magnitude of these effects cannot be determined without dedicated modelling of the HL Tau disc."]
- not stated (card): CASA version-specific calibration scripts/pipeline and self-calibration solints; Disc position angle and inclination values and Keplerian mask parameters; Line-free channels used for continuum subtraction; Clean threshold, cell and image size, robust/weighting; Method for deriving radial profiles (annuli, bin widths, deprojection) and integrated-intensity error propagation; Moment-map clipping de…

### 2021A&A...655A..25Z: The IBISCO survey. I. Multiphase discs and winds in the Seyfert galaxy Markarian 509 (2021; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the molecular gas content, disc kinematics, stability and molecular winds in the Seyfert 1.5 galaxy Mrk 509, and are the winds AGN- or SN-driven?
- step 4: Dynamical mass and Toomre Q map
  - method: M_dyn = r v_rot^2/2G; Q_gas = a v_rot sigma/(pi R G Sigma_gas) pixel by pixel from moments 0 and 2 [6 Discussion: "The velocity dispersion and $\Sigma_{gas}$ are calculated pixel by pixel from the moment 2 and 0 maps, respectively; the radius $R$ is deprojected."]
  - parameter: a=1 up to R=1.1 arcsec, a=1.4 beyond [6 Discussion: "We adopt $a$=1 up to $R$=1.1 arcsec, where the rotation curve is steep, and $a$=1.4 at larger radii."]
  - validation: central 0.3 arcsec excluded for beam smearing [6 Discussion: "excluding the central region of 0.3 arcsec radius, to avoid the beam-smearing effect"]
- result: Dynamical mass = 2.0e10 ± 1.1e10 Msun [6 Discussion: "$M_{dyn}$ = (2.0 $\pm$ 1.1) $\times$ $10^{10}$ $\mathrm{M_{\odot}}$ within a $\sim$2.6 kpc radius"]
- result: Molecular gas fraction = ~5 ± not stated % [6 Discussion: "is then $\mu \sim 5 \%$"]
- result: Toomre Q_gas range = 0.5-10 ± not stated dimensionless [6 Discussion: "We find values that range from $Q_{gas}\approx$ 0.5 up to 10"]
- result: Star formation efficiency = 6.2e-9 ± not stated 1/yr [6 Discussion: "$SFE = SFR/M_{H_2} = 6.2 \times 10^{-9} \rm yr^{-1}$"]
- limitation (authors): Nuclear region barely resolved; higher resolution needed [4 Molecular Discs: "We note that observations with higher angular resolution would be required to better assess the kinematic properties in this region."]
- limitation (authors): Cannot discriminate consecutive episodes from a decelerating wind [5 Molecular Wind: "Current data cannot discriminate between these two scenarios."]
- not stated (card): Spectral windows, channel widths and line-free channel ranges used for continuum; Regions/masks used to extract spectra A and B and how v98 and S_CO were measured; 3DBarolo parameters (rings, widths, mask, normalisation, fitting settings); Boundaries of the clean mask; Conversion of CO(2-1) to CO(1-0) (r21) used for alpha_CO; Catalog photometry for SED fit; How uncertainties on M_dyn were propaga…

### 2020ApJ...890..130T: The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. II. A Statistical Characterization of Class 0 and Class I Protostellar Disks (2020; star_formation, protoplanetary_disks; large_program_or_survey)
- question: What are the dust disk radii and masses of Class 0, Class I and Flat Spectrum protostars in Orion, and how do they evolve and compare with Class II disks, regions and simulations?
- step 5: Gravitational stability (Toomre Q) estimates
  - method: Q≈2(M*/Md)(H/R) with fiducial M*=0.25 Msun, gas-to-dust 100 [4.4 Potential for Gravitationally Unsta…: "we multiply the derived dust disk mass by 100, the gas-to-dust ratio in the interstellar medium"]
  - assumption: T ∝ R^-0.46 from models [4.4 Potential for Gravitationally Unsta…: "the relationship that T $\propto$ R$_{disk}^{-0.46}$"]
  - validation: Envelope-contaminated candidates screened by image inspection [4.4 Potential for Gravitationally Unsta…: "HOPS-317-B, HOPS-402, HOPS-400-B, HOPS-87, HOPS-403, HOPS-398, and HOPS-404 are likely to have significant envelope contamination"]
- limitation (authors): Optically thick emission yields mass underestimates; envelope contamination possible; Gaussian radius biases [2.4 Data Analysis: "If the dust emission is not optically thin, then the masses will be lower limits."]
- not stated (card): Line-free channel selection and exact continuum spectral-window flagging; Exact imaging mask/threshold, niter, image size and cell size; Which source flux/size entries were taken as upper limits and detection criteria for fitting imfit regions; Distance-estimation neural network training details/hyperparameters; Full Appendix B model parameters (inclination/hour angle simulation process) for repr…

### 2025A&A...693A..76C: Dissecting the disk and the jet of a massive (proto)star: An ALMA view of IRAS 20126+4104 (2025; star_formation, protoplanetary_disks; observational_alma_primary)
- question: What are the physical and kinematical structure of the disk and jet of the massive (proto)star IRAS 20126+4104?
- step 6: Accretion rate, Toomre Q, axis angle
  - method: Analytic formulae using Ncol and Trot profiles [Discussion: "For $\mbox{$M_{\rm s}$}$=12 $M_\odot$, $R_{\rm d}$=0.3$''$=490 au, $A$=0.42 (see Sect. [4.2.4](#smodd)), and $X_{\rm CH_3CN}$=$10^{-9}$"]
  - assumption: X_CH3CN=1e-9, mu=2.8, thermal sigma_v, Tk=Trot [Discussion: "we further assume $T_{\rm K}$=$\mbox{$T_{\rm rot}$}$"]
  - validation: compared with Cesaroni et al. 1999 accretion rate [5 Discussion: "a value in reasonable agreement with that obtained by Cesaroni et al. ((cite: cesa99)) from the millimeter continuum emission and the spread in peak velocity among different CH$_3$CN lines"]
- result: Accretion rate = 1.7e-3 ± not stated Msun/yr [Discussion: "we obtain $\dot{M}_{\rm acc}\simeq1.7\times10^{-3}~M_\odot$ yr$^{-1}$"]
- result: Angle between disk and jet axes = 33 ± not stated deg [Discussion: "$\arccos(\hat{e}_{\rm j}\cdot\hat{e}_{\rm d})\simeq33\ensuremath{^\circ}$"]
- limitation (authors): Disk model is a toy proof of concept; H2CO method unreliable near the star [A model for the disk: "The model is intended to be a proof of concept"]
- not stated (card): ALMA/CASA version; line-free channel ranges; spectral resolution and channel width of cubes; cell and image size; rest frequencies and spectroscopy source for lines; ranges for eta, Trot, Ncol grid search; H2CO Trot/Ncol conversion details; parameter ranges for disk model fit; how many 2017 configurations/baselines

### 2025A&A...693A.311P: The Galaxy Activity, Torus, and Outflow Survey (GATOS): VI. Black hole mass estimation using machine learning (2025; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: Can supervised CNNs trained on simulated gas-disk cubes estimate black hole masses from ALMA CO(3-2) position-velocity diagrams or first-moment maps of seven GATOS Seyferts?
- step 2: Simulate training cubes
  - method: Gas particle disk (10^6 particles, Toomre Q=1) in galaxy+BH potential, projected with fixed IA/PA, smoothed to beam, normalised by observed moment-0 map; parameters drawn uniformly [4.2 Numerical simulations: "To ensure sufficient statistics, we fixed the number of particles at $10^6$."] [4.2 Numerical simulations: "we normalized the model cube pixel by pixel in the 2D projection using the zeroth moment map of the CO observations."]
  - parameter: cube dimensions (250, 250, 60); 10 km/s channels [4.2 Numerical simulations: "resulting in a cube of dimensions (250, 250, 60) for each simulation."]
  - assumption: axisymmetric homogeneous thin gas disk, negligible dark matter, H_gas/R_gas<0.1 [4.2 Numerical simulations: "we choose to keep the ratio $H_{\mathrm{gas}}/R_{\mathrm{gas}}<0.1$."]
- limitation (authors): One network per galaxy; simulations lack bars, clumps and misalignments; uncertainties not physical [7 Conclusion: "a key limitation of this work is that we trained and applied the NNs on one galaxy at a time."]
- not stated (card): ALMA project codes, calibration and imaging details (CASA version, robust, beam, rms) for the cubes; Which ALMA cubes/products were used and how they were obtained; Moment-map clipping thresholds and PVD slit width and position angle; Distances adopted per galaxy; Parameter ranges for the uniform sampling of simulations (only best-fit values tabulated); Random seeds, number of dropout inferences'…

### 2015ApJ...806L..17S: ALMA Resolves the Properties of Star-forming Regions in a Dense Gas Disk at z ∼ 3 (2015; high_z_galaxies, star_formation; archival_reuse)
- question: Do star-forming regions in the dense gas disk of lensed galaxy SDP 81 follow local GMC scaling relations (Larson's relations), and what ISM pressure explains any offsets?
- step 3: Disk dynamics, Toomre Q and Jeans length
  - method: Disk model of the CO(5-4) velocity field gives inclination and Mdyn; Q = sigma_r kappa / (pi G Sigma_gas); L_J = pi sigma_r^2 / 8 G Sigma_gas [Analysis & Discussion: "L$_{\rm J}$ = $\pi\sigma_{\rm r}^2/8 G \Sigma_{\rm gas}$"]
  - parameter: kappa = a Vmax/R with a = sqrt3; sigma_r = 30–35 km/s; Sigma_gas = 4±1e9 Msun kpc^2 [Analysis & Discussion: "$\sigma_{\rm r}$ = 30–35 km s$^{-1}$ we estimate L$_{\rm J}$ = 130$_{-60}^{+200}$ pc."]
- result: Inclination-corrected rotation speed = 320 ± 20 km/s [abstract: "$v_{\rm rot}$ = 320 $\pm$ 20 km s$^{-1}$"]
- result: Dynamical mass within 1.5 kpc = 3.5e10 ± 1.0e10 Msun [abstract: "M$_{\rm dyn}$ = (3.5 $\pm$ 1.0) $\times$ 10$^{10}$ M$_{\odot}$ within a radius of 1.5 kpc"]
- result: Toomre Q = 0.30 ± 0.10 dimensionless [abstract: "$Q$ = 0.30 $\pm$ 0.10"]
- result: Jeans length = 130 ± +200/-60 pc [Analysis & Discussion: "L$_{\rm J}$ = 130$_{-60}^{+200}$ pc"]
- result: Disk inclination = 40 ± 5 deg [Analysis & Discussion: "inclination of $\theta$ = 40 $\pm$ 5$^\circ$"]
- limitation (authors): The pressure estimate has considerable uncertainty [Analysis & Discussion: "although we caution this value has considerable uncertainty"]
- not stated (card): CASA version and calibration/imaging details (deferred to Vlahakis15); Source-plane reconstruction code and lens model parameters; Velocity dispersion map construction and clump sigma extraction details; Local background definition for the 5-sigma clump criterion; Gaussian fit procedure and PSF deconvolution for sizes; Sigma_gas and the gas mass used in the Q and pressure calculations

### 2016Sci...353.1519P: Spiral density waves in a young protoplanetary disk (2016; protoplanetary_disks; observational_alma_primary)
- question: Does the Elias 2-27 disk show spiral density waves in the midplane, traced by optically thin 1.3 mm dust emission, and what drives them?
- step 3: Estimate optical depth and Toomre Q
  - method: Radiative transfer of azimuthally averaged profile with adopted surface density [Radiative Transfer Model: "We performed radiative transfer calculations using RADMC3D (*26*) in order to compute the dust temperature and surface density, as well as the optical depth"]
  - software: RADMC-3D
  - assumption: gas-to-dust ratio 100; kappa 2.4 cm2/g (RT), 2.3 cm2/g (Toomre Q) [Estimation of Toomre Q: "For a dust mass opacity of $\kappa_{1.3mm} = 2.3$ cm$^2$ g$^{-1}$, commonly used in the literature (*41*)"]
  - validation: Model reproduces azimuthally averaged radial profile [main text: "This model reproduces the azimuthally averaged radial profile of the observed ALMA 1.3 mm continuum emission"]
- result: Optical depth at 100 AU = 0.1 (0.02 at 300 AU) ± not stated dimensionless [main text: "$\tau=0.1$ at $R=100$ AU, decreasing to $\tau=0.02$ at $R=300$ AU"]
- limitation (authors): Contrast values are lower limits because of possible beam dilution and higher optical depth. [main text: "Thus, the contrast values measured for NW and SE are lower limits."]
- not stated (card): Self-calibration solution intervals and number of iterations; Clean mask, threshold, cell and image size, multiscale scales; CASA version; Initial model for self-cal and flux scale uncertainty; Settings of the unsharp-mask/background profile functional form and MCMC priors, walkers, steps; Line-free channels and continuum subtraction for CO; RADMC-3D setup (grid, stellar parameters, dust composit…

### 2019ApJ...877L..25M: The First Bird’s-eye View of a Gravitationally Unstable Accretion Disk in High-mass Star Formation (2019; star_formation; observational_alma_primary)
- question: What is the structure, mass and gravitational stability of the innermost accretion disk and infalling envelope around the nearly face-on high-mass protostar G353.273+0.641?
- step 5: Infall/accretion rate, age, Toomre Q, clumps
  - method: Infall time from equation of motion; Q=cs*kappa/(pi G Sigma) with Keplerian 10 Msun; clumps from Sigma>1e25 cm-2 [Toomre's Q parameter: "Toomre’s $Q$ parameter is expressed as, $$\begin{eqnarray*} Q = \frac{c_{\rm s}\kappa}{\pi G\Sigma}, \end{eqnarray*}$$"]
  - assumption: 50% of accreting mass goes to outflow [Accretion rate: "because 50% of accreting mass could be converted to the outflow in case of high-mass star-formation"]
  - validation: Compared with simulations of Meyer et al. 2018 [Gravitational stability: "The latter value is comparable to that reported in (cite: 2018MNRAS.473.3615M) again."]
- result: Accretion rate onto star = 3e-3 or higher ± not stated Msun/yr [Accretion rate: "3$\times$ 10$^{-3}$ M$_{\odot}$ yr$^{-1}$ or higher"]
- result: Minimum Toomre Q (beta=1) = 0.9 ± not stated dimensionless [Gravitational stability: "the minimum $Q$ reaches 0.9 around the eastern local peak"]
- result: Minimum Q (beta=2) = 0.4 ± not stated dimensionless [Gravitational stability: "Recalculated $Q$ values are 0.9 (average), 0.4 (minimum), and 2.0 (maximum)"]
- result: Clump masses (beta=1) = 0.04 and 0.09 ± not stated Msun [Clump mass: "The clump masses were estimated to be 0.04 and 0.09 M$_{\ensuremath{\odot}}$"]
- limitation (authors): Beta uncertainty dominates Q; kinematic model not finely fitted; larger-scale envelope resolved out [Gravitational stability: "The major uncertainty of $Q$ in this study originates from the uncertainty of the dust opacity index $\beta$"]
- not stated (card): tclean parameters (weighting/robust, deconvolver, cell, image size, masks); line-free channels for continuum subtraction; calibrator list other than flux calibrator and pipeline version; line stacking procedure details (velocity alignment, weighting); flaring angle and model fit procedure (done by eye); elliptical Gaussian fit procedure; RADEX input details beyond T and linewidth

### 2019Natur.569..519K: Fast and inefficient star formation due to short-lived molecular clouds and rapid feedback (2019; nearby_galaxies, star_formation, milky_way_ism; observational_alma_primary)
- question: Why does the gas depletion time exceed the GMC dynamical time by two orders of magnitude: slow, efficient star formation over many dynamical times, or fast, inefficient star formation with rapid GMC dispersal?
- step 6: Compare with theoretical feedback timescales and cloud properties
  - method: Cprops cloud identification; compare to free-fall, crossing, SN, photoionisation, wind, radiation pressure timescales and Toomre length / scale height [Methods: "Molecular clouds are identified and their macroscopic properties determined from the ALMA+ACA data using an updated version of the Cprops code"]
  - software: Cprops
  - assumption: gas velocity dispersion 6 km/s from M33 HI [Methods: "The gas velocity dispersion is assumed to be $6~{\rm km}~{\rm s}^{-1}$"]
- limitation (authors): Extinction correction might underestimate attenuation toward GMC density peaks [Methods: "It might underestimate the attenuation towards the GMC density peaks, where the surface density is $>20~{\rm M}_\odot~{\rm pc}^{-2}$."]
- limitation (authors): eps_sf and eta_fb depend on CO-to-H2 and Halpha-to-SFR conversion factors [Methods: "Due to their dependence on $t_{\rm dep}$, the quantities $\epsilon_{\rm sf}$ and $\eta_{\rm fb}$ are sensitive to absolute scaling factors"]
- not stated (card): Which ALMA execution blocks/MOUS were used and the pipeline version used; CASA clean parameters: cell size, image size, masking, niter; Details of the modified total power pipeline and how feathering was done; Image-cube moment/masking used to make the CO map fed to Heisenberg; Heisenberg code is not public (available on request); Exact reference parameters in Kruijssen 2018 Tables 1-2 not reprod…

### 2017A&A...604A.117C: Planck's dusty GEMS. IV. Star formation and feedback in a maximum starburst at z = 3 seen at 60-pc resolution (2017; high_z_galaxies; observational_alma_primary)
- question: How intense can star formation be in a maximal starburst at z=3, and is it self-regulated by feedback (radiation pressure, supernovae and winds) as seen on ~60 pc scales?
- step 4: Dynamical mass and Toomre Q
  - method: M_dyn = v^2 R/G with v = dv/2 sin i; Toomre Q from Genzel+14 parametrization [4.1: "we can provide dynamical mass estimates by setting $M_{dyn}= v^2 R / G$"]
  - parameter: R1=700 pc, R2=600 pc; Sigma_gas=1e4 Msun/pc2; a=2 [4.1: "with intrinsic sizes $R_1 = 700$ pc and $R_2 =600$ pc for regions 1 and 2"]
  - assumption: velocity gradients trace rotation of a disk; inclination not corrected [4.1: "If these gradients approximately sample gravitational motion within a rotating disk"]
- result: Toomre Q = 1.0 ± 0.3 dimensionless [4.2: "This gives $Q=1.0\pm0.3$."]
- limitation (authors): alpha_CO and r43/10 make gas surface densities uncertain by a few tenths of a dex. [5.2: "make gas mass surface density estimates uncertain by a few tenths of a dex"]
- limitation (authors): 27% of expected continuum flux missed. [3.1: "Most of the missing flux is likely to be in the extended diffuse regions"]
- not stated (card): Line-free channels and continuum subtraction method for the cube; Image size, cell size and clean threshold; Flux calibrator and calibration pipeline/CASA version; Details of per-pixel Gaussian fitting (S/N cut, initial guesses); Lens model files and magnification maps; How pixel-by-pixel SFR and gas surface densities were mapped to source plane; Averaging/masking used for Clumpfind beyond thresh…

### 2024ApJ...966..119L: ALMA Spectral Survey of an Eruptive Young Star, V883 Ori (ASSAY). I. What Triggered the Current Episode of Eruption? (2024; protoplanetary_disks, star_formation, astrochemistry; observational_alma_primary)
- question: What triggered the current eruption of V883 Ori, as seen in the morphology and kinematics of molecular lines from the envelope and disk?
- step 5: Spiral fitting and Toomre Q
  - method: Fit HCN peak positions with logarithmic and Archimedean spirals; compute Q for current and pre-burst temperature [4.1: "the logarithmic spiral with $R=R_0 e^{a\theta}$, developed by the gravitational instability and the Archimedean spiral with $R=R_0 + b\theta$"]
  - assumption: Pre-burst snowline at 4 au [4.1: "If the snowline was located at 4 au, then $Q < 2$ at $r < 100$ au and $Q \sim 3.5$ at 200 au"]
  - validation: Southern arm well fit, northern not; shape ambiguous [4.1: "The northern arm does not reveal a spiral profile, while the southern arm is well-fit."]
- result: Toomre Q (current) = >2 at all radii, ~7 at 200 au ± not stated dimensionless [4.1: "it is greater than 2 at all radii and $\sim$7 at 200 au"]
- result: Toomre Q (pre-burst, snowline at 4 au) = <2 at r<100 au, ~3.5 at 200 au ± not stated dimensionless [4.1: "then $Q < 2$ at $r < 100$ au and $Q \sim 3.5$ at 200 au"]
- limitation (authors): Velocity resolution and S/N are too low to robustly examine arm kinematics and spirals [4.1: "the velocity resolution of our data is not high enough to robustly examine the kinematics of the large arm-like structures beyond the disk."]
- not stated (card): tclean parameters: cell size, image size, masks, deconvolver, threshold, niter; Channel width/velocity regridding for moment maps; Which channels were line-free per SPW; Self-calibration solution intervals; Disk geometry for the PV cuts and the spiral-arm peak positions; Temperature profile and surface density details for Q curves; How the 1'' aperture spectra were extracted and corrected; Detail…

### 2020ApJ...893..125U: Scattering-induced Intensity Reduction: Large Mass Content with Small Grains in the Inner Region of the TW Hya disk (2020; protoplanetary_disks; archival_reuse)
- question: Does dust scattering reduce the observed mm continuum intensity in the inner (<~10 au) TW Hya disk, and what dust mass and grain size does this imply?
- step 4: Derive dust mass and implications
  - method: Convert tau10 to surface density with kappa_B3; integrate within 10 au; Toomre Q and fragmentation alpha estimates [4.3 Disk masses: "the inner region ($<10$ au) of the TW Hya disk has a total dust mass of $150M_{\oplus}$"]
  - assumption: kappa_abs(Band 3)=9.2e-2 cm2/g; T=30 K; stellar mass 0.8 Msun [4.1 Dependence on the opacity model: "The DSHARP opacity we use has an absorption opacity of $9.2\times10^{-2}\,{\rm cm^{2}\,g^{-1}}$ at the wavelength of Band 3"]
- result: Dust surface density at 10 au = 10 ± not stated g cm^-2 [4.1 Dependence on the opacity model: "meaning that the dust surface density needs to be $10\,{\rm g\,cm^{-2}}$ at 10 au"]
- result: Dust mass within 10 au = 150 ± not stated Earth masses [4.3 Disk masses: "the inner region ($<10$ au) of the TW Hya disk has a total dust mass of $150M_{\oplus}$"]
- result: Dust-to-gas ratio at 10 au (vs Zhang2017 gas) = 0.4 ± not stated dimensionless [4.3 Disk masses: "the dust-to-gas mass ratio is 0.4 at 10 au"]
- limitation (authors): Flux calibration uncertainties may be larger than official values; absolute opacity is uncertain. [2.2 SED analysis: "We confirmed that the actual uncertainty might be potentially larger than the official value but has little impact on our conclusion."]
- not stated (card): Stellar luminosity/heating setup and how T10 is imposed in RADMC-3D (photon numbers, grid); CASA version and pipeline version; Self-calibration parameters and CLEAN settings for Band 3 and 9 (masks, thresholds, cell size); Exact Band 3 and 9 execution blocks used; Fit procedure: models compared by eye, no quantitative statistic; Gas scale height and treatment of vertical temperature structure

### 2018ApJ...869L..47Z: The Disk Substructures at High Angular Resolution Project (DSHARP). VII. The Planet-Disk Interactions Interpretation (2018; protoplanetary_disks; theory_or_simulation_compared_to_alma)
- question: What planet masses and orbits could explain the gaps and rings in the DSHARP disks, and what young wide-orbit planet population results if the gaps are planet-induced?
- step 4: Infer planet masses for DSHARP gaps
  - method: Measure observed gap widths, estimate gas surface density from outer-disk dust surface density, compute Stokes number, use width-K' relation, break degeneracy with h/r and alpha [Planet Properties: "Third, with known $\Sigma_{g,0}$ and the assumed dust size distribution, we can calculate $St_{max}$ and use the $\Delta$-$K'$ relationship"]
  - assumption: GI limit with Toomre Q=1 caps gas surface density; preferred alpha=1e-3 and DSD1 [Planet Properties: "we prefer $M_{p,am3}$ with DSD1 size distribution."]
  - validation: Consistency check with assumed mass, kinematics, asymmetry, depth [Planet Properties: "We can also do a consistency check with the derived $M_p$."]
- result: Occurrence rate of >5 MJ planets beyond 5-10 au = 1/18 (6%) ± not stated percent [Young Planet Population: "the occurrence rate for $>$5 $M_J$ planets beyond 5-10 au is 1/18 or 6%."]
- result: Occurrence rate of 0.2-5 MJ planets beyond 5-10 au = 8/18 (44%) ± not stated percent [Young Planet Population: "The occurrence rate for 0.2 $M_J\lesssim M_p\lesssim$ 5 $M_J$ planets beyond 5-10 au is 8/18 or 44%"]
- result: HD 143006 22 au gap planet mass (alpha=1e-3, DSD1) = 19.91 ± not stated M_Jup [Table 3: "HD 143006 | 1.78 | 22 | 0.62"]
- limitation (authors): Gap profiles fitted at fixed 1000 orbits; dust feedback ignored [Caveats: "Another major caveat in this work is that we fit the gap profiles at 1000 planetary orbits."]
- limitation (authors): Occurrence rates are upper limits since gaps may not be planetary [Young Planet Population: "our derived planet occurrence rates should be considered as the upper limits."]
- not stated (card): Exact Dusty FARGO-ADSG code version and setup files; Random seeds for the super-particle initial conditions; Details of the by-eye matching for narrow gaps; Exact gap identification and edge measurements in the observed profiles

### 2019A&A...627L...6M: Substructures in the Keplerian disc around the O-type (proto-)star G17.64+0.16 (2019; star_formation, protoplanetary_disks; observational_alma_primary)
- question: Does the disc around the O-type (proto)star G17.64+0.16 show substructure, Keplerian rotation, and gravitational stability when resolved at ~20 mas (~40 au)?
- step 5: Toomre Q map
  - method: Q = c_s kappa/(pi G Sigma); Sigma from column density times mu m_H, mu=2.3; T(R) propto R^-0.4 anchored to a 45 Msun O star [4.2 Disc stability: "The temperature of the disc is calculated using $T(R)\propto (R/R_0)^{-0.4}$ (cite: Whitney2003)"]
  - assumption: Optically thin; steeper T profile or optical depth would lower Q [4.2 Disc stability: "If we use a steeper temperature profile (cite: Brinch2010) the temperature in the disc is below 150 K"]
  - validation: Computed for minimal and maximal free-free removal [4.2 Disc stability: "Toomre Q maps for G17.64 where the minimal and maximal free-free contamination is removed"]
- result: Toomre Q in ring (65-97 au) = 2 to 4 ± not stated dimensionless [4.2 Disc stability: "has the lowest Toomre Q values, between 2 and 4"]
- limitation (authors): Free-free contamination is uncertain so the inner ring is speculative [3.1 Continuum emission: "Although speculative, because the free-free contamination is uncertain, we tentatively reveal an enhanced inner ring"]
- not stated (card): CLEAN threshold, masks, cell and image sizes, deconvolver; Line-free channels used for continuum subtraction; Exact point-source flux subtracted in the visibility domain for the min/max free-free cases; Model parameters of the PV disc model (velocity/density laws, line width) and code; Column density map details and conversion to Sigma; Flux calibrator and flux-scale uncertainty

### 2017ApJ...845..170B: ALMA Observations of Circumnuclear Disks in Early-type Galaxies: <SUP>12</SUP>CO(2-1) and Continuum Properties (2017; nearby_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the molecular gas (CO(2-1)) and continuum properties of circumnuclear dust disks in nearby early-type galaxies, and which are good candidates for ALMA black hole mass measurements?
- step 6: Toomre Q stability
  - method: Q = c_s kappa/(pi G Sigma) with c_s replaced by minimum observed sigma_LOS and v_c from k1/sin i [3.1.4 Molecular Gas Stability: "We therefore replace $c_s$ with the minimum observed $\sigma_{\rm LOS}$ for each disk."]
  - validation: Stability persists with uncertainties in k1, Sigma, i (2 deg) and sigma (1 km/s) [3.1.4 Molecular Gas Stability: "this formal stability measure persists after we include the uncertainties in $k_1$ and $\Sigma_{\rm gas}$"]
- limitation (authors): Gas masses subject to large systematic uncertainty from unknown alpha_CO in ETGs [3.1.2 Surface Brightness and Mass Profi…: "Given the large scatter in $\alpha_{\rm CO}$, the derived gas masses are subject to potentially large systematic uncertainties."]
- limitation (authors): Beam smearing contributes to observed line widths [3.1.1 Line Profile Fitting: "portions of the lowest observed $\sigma_{\rm LOS}$ values are still the result of beam smearing."]
- not stated (card): Image sizes, cell sizes and clean masks/thresholds per target; Line-free channels used for uv continuum subtraction; Self-calibration solution intervals and reference models; Exact CASA version assigned to each dataset; Voronoi target S/N for binning; Kinemetry fitting settings (radial grid, harmonic orders); Initial guesses for uv-plane point-source modeling; Which CASA task options were used (e…

### 2019ApJ...870...80L: Spatially Resolved [C II] Emission in SPT0346-52: A Hyper-starburst Galaxy Merger at z ∼ 5.7 (2019; high_z_galaxies; observational_alma_primary)
- question: What is the source-plane structure and kinematics of the lensed DSFG SPT0346-52 in [CII] and dust continuum, and does the [CII] deficit hold on sub-kpc scales?
- step 6: Toomre Q
  - method: Q = sigma_r * sqrt(3) v_r/r / (pi G Sigma_gas); v_r from 3D-Barolo tilted-ring fits of velocity fields; Sigma_gas from M_g split by [CII] flux [5.2: "These velocity fields were then fit using the 2D tilted ring modeling in 3D-Barolo (cite: bbarolo)."]
  - software: 3D-Barolo
  - assumption: [CII] traces gas; M_g=1.5e11 Msun; a=sqrt(3); sigma_r used as upper limit on turbulent dispersion [5.2: "To calculate the gas surface density, $\Sigma_{\rm gas}$, we assume the \[CII\] emission traces the gas."]
  - validation: Using sigma_r gives upper limit on Q so Q<<1 is robust [5.2: "Thus, the result that $Q\ll 1$ everywhere and the disks are gravitationally unstable does not depend on this substitution."]
- result: Mean Toomre Q blue component = 0.03 (max 0.13) ± not stated dimensionless [5.2: "$\bar{Q}=0.03$ and a maximum value of $Q_{\rm max}=0.13$"]
- result: Mean Toomre Q red component = 0.02 (max 0.06) ± not stated dimensionless [5.2: "$\bar{Q}=0.02$ and $Q_{\rm max}=0.06$"]
- limitation (authors): Constant dust temperature assumed, uncertainty within factor ~2 [4.1: "the variation caused by variable dust temperatures in the galaxy is within a factor of $\sim 2$."]
- not stated (card): Image size, cell size, clean masks/threshold and number of iterations; Line-free channels for UVCONTSUB and continuum bandwidth; RIPPLES source pixel grid size, priors and MCMC settings; Value of regularization lambda for the [CII] cube; Spectral windows and which data were combined for the reconstruction; Dust-continuum frequency/flux scale and amplitude calibration uncertainty; Rest frequency o…

### 2025ApJ...984L..19Y: exoALMA. XIV. Gas Surface Densities in the RX J1604.3−2130 A Disk from Pressure-broadened CO Line Wings (2025; protoplanetary_disks; observational_alma_primary)
- question: What is the radial gas surface density and midplane pressure profile of the J1604 transition disk, derived from pressure-broadened CO J=3-2 line wings, and what does it imply for dust trapping, turbulence and planet formation?
- step 5: Constrain X_CO and peak gas surface density via Toomre Q and literature range
  - method: Require Q>1 at gas peak and combine with 1e-6<X_CO<1e-3 [4.1 Gas surface density profile: "If we assume $Q > 1$ at the peak of the gas surface density, we can obtain $X_{\rm CO} > 7 \times 10^{-4}$."]
  - assumption: Disk gravitationally stable (no spirals) [4.1 Gas surface density profile: "there is no significant asymmetric structure such as a spiral arm in the J1604 disk, suggesting the disk is gravitationally stable"]
- result: Peak gas surface density (conclusion) = 18-44 ± not stated g cm^-2 [4.1 Gas surface density profile: "we conclude the peak gas surface density of $18-44\ {\rm g\ cm^{-2}}$ with $1.6 \times 10^{-4} < X_{\rm CO} < 10^{-3}$"]
- result: Gas mass within 50<r<110 au = 0.05-0.1 ± not stated Msun [4.1 Gas surface density profile: "gas mass within $50<r<110$ au of $0.05-0.1\ {\rm M_\odot}$"]
- result: Gas-to-dust ratio at ring peak = 70-400 ± not stated dimensionless [4.1 Gas surface density profile: "we estimate the gas-to-dust surface density ratio at the dust surface density peak to be $70-400$"]
- result: Planet mass from gap depth = 0.1-2 ± not stated Mjup [4.1 Gas surface density profile: "we can estimate the mass of the planet of $0.1-2\ M_{\rm jup}$ for a range of turbulence parameter $\alpha = 10^{-4}-10^{-2}$"]
- limitation (authors): CO/H2 ratio uncertain; absolute gas surface density scales as X_CO^-0.5 [6 Summary: "We note that the CO/H$_2$ ratio remains uncertain in this study."]
- limitation (authors): Dust opacity model uncertainty affects gas-to-dust ratio; limited spatial resolution [4.4 Caveats: "there might be a large uncertainty in the dust opacity model."]
- not stated (card): Exact exoALMA CO cube parameters (robust, taper, continuum subtraction) are only by reference to Loomis et al.; Likelihood and noise definition for the CO spectral fit (per-channel noise estimate, fit velocity range) not specified; Which radii/annuli spacing used for fits and how radial profiles are averaged/errors defined; Band 7 continuum image details and absolute flux handling; Details of Too…

### 2019ApJ...877..100Y: A Tight Relation between Spiral Arm Pitch Angle and Protoplanetary Disk Mass (2019; protoplanetary_disks; archival_reuse)
- question: How does the pitch angle of the dominant spiral Fourier mode in protoplanetary disks depend on disk properties, especially disk mass?
- step 4: Derive disk masses and Toomre Q
  - method: Convert 880 um flux to mass; estimate mean Q from irradiated Keplerian disk [Data: "The mean $Q$ is derived as $Q=c_s\kappa/\pi G \overline{\Sigma}$"]
  - parameter: flaring angle phi = 0.02 [Data: "where $\phi$, set to 0.02 for simplicity, is the flaring angle"]
  - assumption: dust opacity 3 cm2 g-1, gas-to-dust ratio 100 [Data: "assuming a dust opacity of $\kappa$ = 3 cm$^2$ g$^{-1}$ and a gas-to-dust mass ratio of 100"]
- limitation (authors): Disk masses are the largest uncertainty; gas-to-dust ratio unconstrained [Results and Discussion: "The largest source of uncertainty in Equation (2) lies in the disk masses."]
- not stated (card): Which DSHARP continuum image products (beam, weighting) were used; Radial boundaries r_in and r_out chosen for each disk; Number of Fourier modes m and range of p sampled; Distances used to convert arcsec to AU; Fitting method for the log relation and Pearson rho; Gaussian star-removal parameters for HT Lup

## All papers in this technique

- 2014A&A...565A..59D (2014): ALMA resolves turbulent, rotating [CII] emission in a young starburst galaxy at z = 4.8
- 2014A&A...569A..11S (2014): A necklace of dense cores in the high-mass star forming region G35.20-0.74 N: ALMA observations
- 2014ApJ...784...78R (2014): Massive Molecular Gas Flows in the A1664 Brightest Cluster Galaxy
- 2015ApJ...806...17R (2015): Morphology and Kinematics of Warm Molecular Gas in the Nuclear Region of Arp 220 as Revealed by ALMA
- 2015ApJ...806L..17S (2015): ALMA Resolves the Properties of Star-forming Regions in a Dense Gas Disk at z ∼ 3
- 2015ApJ...808..102K (2015): Resolving Protoplanetary Disks at Millimeter Wavelengths with CARMA
- 2016ApJ...818..158A (2016): Planetary System Formation in the Protoplanetary Disk around HL Tauri
- 2016ApJ...823...68S (2016): Gas Dynamics and Outflow in the Barred Starburst Galaxy NGC 1808 Revealed with ALMA
- 2016ApJ...827...34O (2016): Witnessing the Birth of the Red Sequence: ALMA High-resolution Imaging of [C II] and Dust in Two Interacting Ultra-red Starbursts at z = 4.…
- 2016ApJ...827...81I (2016): Do Circumnuclear Dense Gas Disks Drive Mass Accretion onto Supermassive Black Holes?
- 2016MNRAS.461..385B (2016): Determining the mid-plane conditions of circumstellar discs using gas and dust modelling: a study of HD 163296
- 2016Sci...353.1519P (2016): Spiral density waves in a young protoplanetary disk
- 2017A&A...603A..10B (2017): Fragmentation and disk formation in high-mass star formation: The ALMA view of G351.77-0.54 at 0.06'' resolution
- 2017A&A...604A.117C (2017): Planck's dusty GEMS. IV. Star formation and feedback in a maximum starburst at z = 3 seen at 60-pc resolution
- 2017ApJ...845..170B (2017): ALMA Observations of Circumnuclear Disks in Early-type Galaxies: <SUP>12</SUP>CO(2-1) and Continuum Properties
- 2018A&A...613A..34P (2018): ALMA view of RX J1131-1231: Sub-kpc CO (2-1) mapping of a molecular disk in a lensed star-forming quasar host galaxy
- 2018ApJ...852..122H (2018): CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations
- 2018ApJ...861...91H (2018): ALMA Observations of Polarized 872 μm Dust Emission from the Protostellar Systems VLA 1623 and L1527
- 2018ApJ...864L..25O (2018): The Co-evolution of Disks and Stars in Embedded Stages: The Case of the Very-low-mass Protostar IRAS 15398-3359
- 2018ApJ...869L..46D (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). VI. Dust Trapping in Thin-ringed Protoplanetary Disks
- 2018ApJ...869L..47Z (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). VII. The Planet-Disk Interactions Interpretation
- 2018MNRAS.476..122V (2018): An ALMA view of star formation efficiency suppression in early-type galaxies after gas-rich minor mergers
- 2019A&A...623A..79C (2019): ALMA observations of molecular tori around massive black holes
- 2019A&A...623L...8B (2019): Unveiling a cluster of protostellar disks around the massive protostar GGD 27 MM1
- 2019A&A...627L...6M (2019): Substructures in the Keplerian disc around the O-type (proto-)star G17.64+0.16
- 2019A&A...631A..91G (2019): Towards sub-kpc scale kinematics of molecular and ionized gas of star-forming galaxies at z ∼ 1
- 2019ApJ...870...80L (2019): Spatially Resolved [C II] Emission in SPT0346-52: A Hyper-starburst Galaxy Merger at z ∼ 5.7
- 2019ApJ...871..185L (2019): Investigating Fragmentation of Gas Structures in OB Cluster-forming Molecular Clump G33.92+0.11 with 1000 au Resolution Observations of ALMA
- 2019ApJ...876..130H (2019): ALMA Reveals Potential Evidence for Spiral Arms, Bars, and Rings in High-redshift Submillimeter Galaxies
- 2019ApJ...877..100Y (2019): A Tight Relation between Spiral Arm Pitch Angle and Protoplanetary Disk Mass
- 2019ApJ...877L..25M (2019): The First Bird’s-eye View of a Gravitationally Unstable Accretion Disk in High-mass Star Formation
- 2019ApJ...882L..31B (2019): The First Detection of <SUP>13</SUP>C<SUP>17</SUP>O in a Protoplanetary Disk: A Robust Tracer of Disk Gas Mass
- 2019MNRAS.485..739M (2019): Asymmetric mid-plane gas in ALMA images of HD 100546
- 2019Natur.569..519K (2019): Fast and inefficient star formation due to short-lived molecular clouds and rapid feedback
- 2020A&A...635A...2S (2020): Physical properties of the star-forming clusters in NGC 6334. A study of the continuum dust emission with ALMA
- 2020ApJ...890..130T (2020): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. II. A Statistical Characterization of Class 0 and Class I P…
- 2020ApJ...891...48H (2020): A Multifrequency ALMA Characterization of Substructures in the GM Aur Protoplanetary Disk
- 2020ApJ...893..125U (2020): Scattering-induced Intensity Reduction: Large Mass Content with Small Grains in the Inner Region of the TW Hya disk
- 2020MNRAS.493L.108B (2020): <SUP>13</SUP>C<SUP>17</SUP>O suggests gravitational instability in the HL Tau disc
- 2020Natur.581..269N (2020): A cold, massive, rotating disk galaxy 1.5 billion years after the Big Bang
- 2021A&A...655A..25Z (2021): The IBISCO survey. I. Multiphase discs and winds in the Seyfert galaxy Markarian 509
- 2021A&A...656A..60A (2021): Black hole feeding and star formation in NGC 1808
- 2024ApJ...966..119L (2024): ALMA Spectral Survey of an Eruptive Young Star, V883 Ori (ASSAY). I. What Triggered the Current Episode of Eruption?
- 2024ApJ...970..153A (2024): On Kinematic Measurements of Self-gravity in Protoplanetary Disks
- 2024ApJ...971..129C (2024): A Dust-trapping Ring in the Planet-hosting Disk of Elias 2-24
- 2025A&A...693A..76C (2025): Dissecting the disk and the jet of a massive (proto)star: An ALMA view of IRAS 20126+4104
- 2025A&A...693A.311P (2025): The Galaxy Activity, Torus, and Outflow Survey (GATOS): VI. Black hole mass estimation using machine learning
- 2025ApJ...984L..19Y (2025): exoALMA. XIV. Gas Surface Densities in the RX J1604.3−2130 A Disk from Pressure-broadened CO Line Wings
- 2025ApJ...995..151Y (2025): Molecular Gas and Star Formation in Dwarf Galaxies Observed by the Atacama Large Millimeter/submillimeter Array
- 2025NatAs...9.1553F (2025): Primordial rotating disk composed of at least 15 dense star-forming clumps at cosmic dawn
- 2025NatAs...9.1833L (2025): Detection of a septuple stellar system in formation via disk fragmentation
