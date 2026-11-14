---
name: alma-toomre-stability
description: "Compute and interpret the Toomre Q stability parameter from ALMA data, for protoplanetary and massive-protostar disks (dust or gas surface density, temperature, Keplerian rotation) and for galaxy gas disks (rotation curve, velocity dispersion, CO or [CII] gas mass). Use when a task asks whether a disk is gravitationally unstable, needs a Q map or radial Q profile, uses Q as a prior or upper limit on surface density, or interprets spirals, clumps or fragments as gravitational instability. Built from 51 ALMA papers (2014-2025), 46 of them on topic."
---
# Toomre Q stability from ALMA data

Q = (velocity support) x (epicyclic frequency) / (pi G Sigma). ALMA gives Sigma (continuum or line), the
rotation (Keplerian mass or rotation curve) and sometimes the dispersion; the temperature or dispersion and the
mass conversion (dust opacity, gas-to-dust ratio, alpha_CO or alpha_[CII]) are usually assumed. The two mistakes
that matter most: (1) quoting a single Q without saying it inherits every mass, temperature and rotation-model
assumption (one disk moves from Q = 0.4 to 5 between 20 K and 100 K, 2018ApJ...864L..25O, card); (2) treating Q < 1 as a sharp line
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
     2019MNRAS.485..739M and 2016MNRAS.461..385B, card), or pressure-broadened CO line wings (2025ApJ...984L..19Y), or a
     kinematic self-gravity fit (2024ApJ...970..153A). That fit imposes a minimum-Q (gravitationally stable) prior
     (2024ApJ...970..153A), so a Q computed afterwards from its Sigma is prior-dependent: carry the prior into the
     result and never present that Q as independent evidence of stability.
   - Opacity bookkeeping: state for every opacity whether it is absorption or extinction, at which frequency, and
     per gram of dust or per gram of gas (dust + gas); apply the gas-to-dust factor exactly once. Of the opacity laws
     in the pack only 2018ApJ...861...91H states its basis (a total opacity of 0.034 cm2/g after assuming
     gas-to-dust 100, card); the basis of 2016ApJ...818..158A and 2018ApJ...864L..25O is not established.
   - For a quick global number, papers use the disk mass directly: Q ~ 2 (M*/Md)(H/R) (2020ApJ...890..130T) or
     Q = c_s kappa / (pi G mean Sigma) with flaring angle 0.02 (2019ApJ...877..100Y).
   - Software: the pack rarely names the code that computes Q; named tools are dsharp_opac for opacities
     (2020ApJ...891...48H, aggregate 1) and RADMC-3D (2016Sci...353.1519P, aggregate 1). Recommendation (not pack
     practice): compute Sigma and Q in a small NumPy script on the image grid.
2. **Set the temperature (sound speed).** c_s = sqrt(k T / (mu m_H)) with mu the mean mass per free particle,
   2.3 (2017A&A...603A..10B). Do not confuse it with the mass per H2 molecule (about 2.8 by general practice) used
   to turn an H2 column into Sigma; 2019A&A...627L...6M uses mu = 2.3 for that conversion and 2025A&A...693A..76C
   assumes mu = 2.8 without the pack saying which role it plays. State each convention.
   Choices seen: constant 30 K (2019ApJ...871..185L, 2018ApJ...861...91H, 2020ApJ...893..125U), 15 K
   (2018ApJ...852..122H), a model midplane profile (2020MNRAS.493L.108B, 2020ApJ...891...48H), a power law
   T ~ r^-0.4 (2017A&A...603A..10B, 2019A&A...627L...6M) or R^-0.46 (2020ApJ...890..130T), or line rotation
   temperatures T_rot from CH3CN (2017A&A...603A..10B, 2025A&A...693A..76C).
3. **Set kappa.** For a Keplerian disk kappa = Omega = sqrt(G M / r^3) (2025NatAs...9.1833L), where M is the
   total gravitating mass inside r. The central mass comes from Keplerian fits or assumptions: 1.7 Msun HL Tau
   (2020MNRAS.493L.108B), 10 Msun (2017A&A...603A..10B, 2019ApJ...877L..25M), 7.6 Msun enclosed
   (2025NatAs...9.1833L), 0.25 Msun fiducial (2020ApJ...890..130T). In a massive clump with no clear star,
   2019ApJ...871..185L takes the enclosed gas mass from the 225 GHz flux, adds 0 or 30 Msun of embedded stellar mass,
   and gets the rotation from centrifugal balance; the 0/30 Msun bracket is the stellar term only, so the gas
   self-gravity stays in M and kappa never goes to zero. Validate the rotation model before trusting Q: in
   2018ApJ...864L..25O the Keplerian mass may be an upper limit or apparent value because of non-Keplerian gravity
   and unresolved material.
4. **Compute Q = c_s kappa / (pi G Sigma)** per pixel (2017A&A...603A..10B, 2019A&A...627L...6M,
   2025NatAs...9.1833L, 2019ApJ...877L..25M) or per annulus (2020MNRAS.493L.108B, 2024ApJ...966..119L).
   Sample the inputs to get a Q distribution (1e6 draws of Sigma_d and T in 2024ApJ...971..129C).
5. **Compare with a threshold and with morphology.** Report where Q falls below the adopted threshold (see the
   table), and check against spirals, clumps or fragments (2019ApJ...877L..25M clumps; 2024ApJ...966..119L
   spiral fits, where only the southern arm fits a spiral, the northern arm does not, and the authors say velocity
   resolution and S/N are too low to examine arm kinematics robustly). Absence of spirals is weaker evidence:
   2025ApJ...984L..19Y says it is "suggesting" stability and then assumes Q > 1 to get X_CO > 7e-4, so that bound is
   conditional on the assumption, not a demonstrated Q.
6. **Bracket the assumptions** (see Verification checks): temperature, opacity index, free-free removal, magnetic
   support.

### Galaxy gas disks

1. **Gas surface density.** From CO with alpha_CO (2025ApJ...995..151Y, 2017A&A...604A.117C,
   2017ApJ...845..170B). Record the observed transition, the excitation ratio to CO(1-0) and the alpha_CO
   convention (per K km/s pc2 of CO(1-0), with or without helium): 2017A&A...604A.117C says alpha_CO and r43/10
   make Sigma uncertain by a few tenths of a dex, and the CO(2-1) to CO(1-0) ratio used in 2021A&A...655A..25Z is
   flagged as not stated. Or from [CII] with alpha_[CII] = 31 Msun/Lsun (2025NatAs...9.1553F), or by splitting a total
   gas mass by the [CII] flux map (2019ApJ...870...80L, 2014A&A...565A..59D). Pixel maps use moment 0
   (2021A&A...655A..25Z).
2. **Rotation and kappa.** Tilted-ring fits with 3DBarolo (2025NatAs...9.1553F, 2019ApJ...870...80L; aggregate 2
   counting both spellings), an arctangent model (2018MNRAS.476..122V), or a disk model of the velocity field
   (2015ApJ...806L..17S). Write kappa = a V/R. General practice: kappa^2 = 2 (V/R)^2 (1 + d ln V / d ln R), so
   a = 1 Keplerian, sqrt(2) flat, sqrt(3) for d ln V / d ln R = 1/2, 2 solid body. Better, derive a from the
   fitted rotation curve; the values below are the papers' adopted factors. Seen: a = sqrt(3) (2015ApJ...806L..17S,
   2019ApJ...870...80L), sqrt(2) flat curve (2014A&A...565A..59D), a = 1 inside 1.1 arcsec and 1.4 beyond
   (2021A&A...655A..25Z), a = 2 (2017A&A...604A.117C), a = 1 (2016ApJ...823...68S).
3. **Velocity dispersion.** From moment 2 per pixel (2021A&A...655A..25Z), non-parametric sigma(R) from 3DBarolo
   (2025NatAs...9.1553F), the minimum observed sigma_LOS in place of c_s (2017ApJ...845..170B), or assumed:
   5 km/s for dwarfs (2025ApJ...995..151Y), 6 km/s (2019Natur.569..519K), 8 km/s canonical alternative
   (2018MNRAS.476..122V), 30-35 km/s for a z ~ 3 disk (2015ApJ...806L..17S). Record the channel width and spectral
   response and say how instrumental broadening was removed (2019A&A...631A..91G is flagged for not stating
   sigma_instr); a dispersion near the channel width is an upper limit, not an intrinsic value.
4. **Compute Q_gas = sigma kappa / (pi G Sigma_gas)** per pixel (2021A&A...655A..25Z, 2014A&A...565A..59D,
   2025NatAs...9.1553F), as a radial profile (2025NatAs...9.1553F), or averaged within R = 3 scale lengths
   (2020Natur.581..269N). Where stars matter, use a two-component Q_tot: 2025ApJ...995..151Y uses the Romeo and
   Wiegert (2011) approximation, a thick-disk calculation with Q_g from H2 only, sigma_g = 5 km/s, sigma_star,r =
   30 km/s and sigma_z/sigma_r = 0.6 for stars, 1 for gas. Inputs you also need: the stellar surface density
   Sigma_star (for example from a near-IR image and a mass-to-light ratio) and kappa from the rotation curve (the
   pack flags that paper for not stating its rotation-curve values). General practice (Romeo and Wiegert 2011):
   Q_i = kappa sigma_i / (pi G Sigma_i); thickness factor T_i = 0.8 + 0.7 (sigma_z/sigma_r)_i; weight
   W = 2 sigma_star sigma_g / (sigma_star^2 + sigma_g^2); 1/Q_tot = W/(T_star Q_star) + 1/(T_g Q_g) if
   T_star Q_star >= T_g Q_g, else 1/(T_star Q_star) + W/(T_g Q_g). State which gas phases enter Sigma_g.
5. **Mask beam-smeared regions** (central 0.3 arcsec excluded in 2021A&A...655A..25Z) and compare with clumps,
   Jeans length (L_J = pi sigma^2 / (8 G Sigma_gas), 2015ApJ...806L..17S) or the star formation law.

## Parameter defaults and ranges

| Parameter | Common choice | Range seen | Papers (count, from pack) | Examples |
|---|---|---|---|---|
| Instability threshold | Q < 1 to 2 | Q < 1 (cap), < 1.5, < 1.7, < 2 | 10 state one | 2018ApJ...869L..47Z (Q = 1 cap), 2015ApJ...808..102K (1.5), 2020MNRAS.493L.108B (1.7), 2025NatAs...9.1833L (1-2), 2024ApJ...971..129C (Q > 2 stable) |
| Gas-to-dust ratio, assumed (disks) | 100 | 100 | 8 use 100 (my count of pack lines) | 2016Sci...353.1519P, 2024ApJ...971..129C, 2019ApJ...871..185L, 2019ApJ...877..100Y |
| Gas-to-dust ratio, inferred or adopted from a mass comparison | none | ~260 (adopted for Q, card); 70-400 at the ring peak | 2 | 2019ApJ...882L..31B (260, card), 2025ApJ...984L..19Y (70-400) |
| Gas-to-dust bound from stability | none | maximum 27 in a ring, from Q > 2 | 1 | 2024ApJ...971..129C |
| Gas-to-dust, high-z cross-check | ~1e3 | one paper | 1 | 2025NatAs...9.1553F |
| Dust opacity, mm | ~2-3 cm2/g per gram dust near 1 mm | 9.2e-2 (Band 3) to 3.3 cm2/g | 5 | 2016Sci...353.1519P (2.3 at 1.3 mm), 2019ApJ...877..100Y (3), 2018ApJ...852..122H (3.3 at 290 GHz), 2020ApJ...893..125U (9.2e-2 Band 3) |
| Opacity laws, mass basis to check | power law | 0.01 cm2/g at 230 GHz, beta 0.729; 10 (nu/1 THz)^beta / 100, beta 1; 6.8e-4 at 1.2 mm | 3 | 2018ApJ...861...91H (total opacity after g/d 100, card); 2016ApJ...818..158A and 2018ApJ...864L..25O (dust or gas basis not established) |
| Disk temperature | 30 K constant or a power law | 15 K to 200 K; T ~ r^-0.4 to r^-0.46; T_rot | 11 | 2019ApJ...871..185L, 2018ApJ...852..122H, 2017A&A...603A..10B, 2020ApJ...890..130T |
| Mean mass per free particle (sound speed) | 2.3 | one paper | 1 | 2017A&A...603A..10B |
| Mass per particle for column to Sigma | 2.3 | 2.3; 2.8 with role not stated | 2 | 2019A&A...627L...6M (2.3), 2025A&A...693A..76C (2.8) |
| Epicyclic factor a (galaxies), adopted | sqrt(3) or sqrt(2) | 1 to 2 | 6 | 2015ApJ...806L..17S, 2014A&A...565A..59D, 2021A&A...655A..25Z, 2017A&A...604A.117C |
| Gas dispersion (galaxies, if assumed) | measured moment 2 | 5-35 km/s | 4 | 2025ApJ...995..151Y, 2019Natur.569..519K, 2018MNRAS.476..122V, 2015ApJ...806L..17S |
| Stellar dispersion (Q_tot) | 30 km/s | one paper | 1 | 2025ApJ...995..151Y |
| alpha_[CII] | 31 Msun/Lsun | one paper | 1 | 2025NatAs...9.1553F |
| Q prior in kinematic fits | minimum-Q prior | emcee, 64 walkers, 25,000 steps | 1 | 2024ApJ...970..153A |
| Particle-disk setup (not a measurement) | Q = 1, 1e6 particles | | 2 | 2019A&A...623A..79C, 2025A&A...693A.311P |

Reported Q values (useful as sanity ranges, more in `references/parameters.md`). High-z [CII]/CO disks, each a
different kind of number: component means 0.02 and 0.03 with maxima 0.06 and 0.13 (2019ApJ...870...80L, upper
limits from sigma_r), radially averaged 0.2-0.3 (2025NatAs...9.1553F), 0.30 +/- 0.10 (2015ApJ...806L..17S), disk
average 0.58 +/- 0.15 (2014A&A...565A..59D), disk average within 3 scale lengths 0.96 +/- 0.30
(2020Natur.581..269N); a z = 0.654 lensed quasar host gives 1.07 (2018A&A...613A..34P, card); dwarfs 0.9 to 1.5
(2025ApJ...995..151Y); Mrk 509 0.5 to 10 (2021A&A...655A..25Z); HL Tau minimum 1.1 at 77 au
(2020MNRAS.493L.108B); massive-protostar disks 0.4 to 4 (2019ApJ...877L..25M, 2017A&A...603A..10B,
2019A&A...627L...6M).

## Software

The cards rarely name the code that computes Q itself; it is a formula applied to maps in custom scripts. Named
tools (aggregate counts over all 51 papers, each 1 unless noted):

| Tool | Used for | Papers |
|---|---|---|
| CASA | not named in the matched Q steps (aggregate 0); the pack does not show which tool made the input maps | none |
| 3DBarolo / 3D-Barolo | rotation curve V(R), sigma(R) for galaxy Q (2 papers, two spellings) | 2025NatAs...9.1553F, 2019ApJ...870...80L |
| emcee | kinematic disk-mass fit with a minimum-Q prior | 2024ApJ...970..153A |
| RADMC-3D | radiative transfer for temperature, Sigma, optical depth before Q | 2016Sci...353.1519P |
| dsharp_opac | DSHARP opacities for optical depth and grain size | 2020ApJ...891...48H |
| Cprops | GMC catalogue compared with the Toomre length | 2019Natur.569..519K |
| XCLASS (card note) | pixel T_rot maps used as temperature | 2017A&A...603A..10B |
| scikit-learn, NetworkX, FragMent | cluster statistics in an off-topic paper | 2020A&A...635A...2S |

Recommendation (not pack practice): write Q as a small numpy function over the Sigma, T (or sigma) and radius maps on the same grid,
with deprojected radius, and keep every assumed constant as a named input so it can be bracketed.

## Pitfalls

- **Mass is the dominant error.** Opacity uncertain by a factor of 10 (2018ApJ...869L..46D), kappa0 by a factor of
  two (2015ApJ...808..102K); disk masses are the largest uncertainty and the gas-to-dust ratio is unconstrained
  (2019ApJ...877..100Y). Q scales as 1/Sigma, so it inherits all of this.
- **Optical depth and missing flux make Sigma a lower limit, so Q an upper limit** (2025NatAs...9.1833L,
  2017A&A...603A..10B where more than 99% of extended flux is filtered, 2020ApJ...890..130T). Say which way the
  bias goes.
- **The opposite bias also happens.** A Keplerian mass can be an upper limit or an apparent value because of
  non-Keplerian gravity and unresolved material (2018ApJ...864L..25O), which moves kappa and Q the other way.
  Validate the rotation model (PV diagram or channel-map residuals) before interpreting Q.
- **Priors and assumptions are not results.** A Sigma fitted under a minimum-Q prior (2024ApJ...970..153A) or a
  bound derived by assuming Q > 1 (2025ApJ...984L..19Y) cannot then be used to show the disk is stable.
- **Temperature choice moves Q a lot.** Q from 0.4 to 5 for 20-100 K (2018ApJ...864L..25O, card; its mass is
  itself flagged as possibly apparent, see below); a steeper
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
  spiral shape fits (2024ApJ...966..119L: southern arm fits, northern does not, kinematics not robust at that
  velocity resolution and S/N); comparison with simulations (2019ApJ...877L..25M).
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
- 2025ApJ...984L..19Y: assumed Q > 1 used to bound X_CO (conditional bound).
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
