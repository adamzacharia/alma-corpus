---
name: alma-chemical-modelling
description: "Compare observed ALMA molecular abundances, abundance ratios, column densities or line images with astrochemical kinetics models: gas-grain codes (MAGICKAL, NAUTILUS, UCLCHEM, ALCHEMIC, PURE-C, Chempl), disk thermo-chemical codes (DALI, RAC2D, the Du and Bergin code), and gas-phase circumstellar-envelope or PDR models (RATE12-based CSE models, Meudon PDR), then post-process with LIME, RATRAN, RADMC-3D or mcp. Use when a task asks whether a formation route explains a detected molecule, what cosmic-ray rate, warm-up history, C/O or elemental depletion a source needs, where a snowline or photodissociation front sits, or when checking someone else's model-to-data comparison. Built from 46 ALMA papers (2014-2025)."
---

# Astrochemical modelling compared to ALMA lines

Runs a time-dependent chemical network on an assumed physical history (cloud collapse then warm-up, a
static disk structure, or an expanding envelope) and asks whether the predicted abundances, ratios or
synthetic line images match what ALMA measured. The two mistakes that matter most: comparing a model
abundance with an observed one whose H2 column, emitting area or excitation is itself uncertain by a factor
of a few (so "agreement" inside a factor 3 to 10 means little), and reading physical conclusions from a
model that was never fitted, only run once on generic inputs. State the free parameters you varied and
the agreement tolerance you used before claiming a match.

Counts below are from the evidence pack for this technique (46 papers). Aggregate counts (software,
fitting, validation) are the pack's own and cover all 46. My scope decision, not a pack verdict: the DG Tau
disk-wind paper (2018A&A...620L...1G) is treated as off-topic, because its card says it only uses a
published thermo-chemical temperature structure to place an escape-temperature layer (card); my hand
counts in the parameter table never include it. Three more use disk thermo-chemical models to infer gas
structure or gas mass rather than abundances (2016A&A...585A..58V, 2019ApJ...871..107F,
2025ApJ...989....1Z); they are included as a variant. Claims marked "(card)" come from the methods card of
a pack paper, not from the pack text.

Density convention used throughout: nH is total hydrogen nuclei, n(H2) is molecular hydrogen, plain n
means the pack does not say which. For fully molecular gas nH = 2 n(H2) (general practice). Abundances are
likewise quoted per H or per H2 as the paper states; convert before comparing.

## When to use

- A newly detected or tentatively detected molecule needs a formation route: add the candidate reactions
  to a gas-grain network and compare the peak model abundance or ratio with the observed one (urea in
  2019A&A...628A..10B, N-methylformamide in 2017A&A...601A..49B, cyanamide in 2024ESC.....8..665M, CH3NCO
  in 2017MNRAS.469.2230M, alkanethiols in 2016A&A...587A..92M, iso-propyl cyanide in 2014Sci...345.1584B).
- Hot-core or hot-corino abundance patterns that may encode the thermal history or cosmic-ray rate: run a
  grid over those parameters (18 MAGICKAL models per source over cosmic-ray rate and minimum dust
  temperature in 2019A&A...628A..27B).
- Disk line emission whose radial morphology (rings, dips, snowlines) may be chemical: thermo-chemical
  model plus line radiative transfer (C2H rings in 2016ApJ...831..101B, DCO+ double rings in
  2015ApJ...810..112O, N2H+ as CO snowline tracer in 2017A&A...599A.101V, radial CO depletion in
  2019ApJ...883...98Z, sulfur species in 2018A&A...617A..28S and 2019ApJ...876...72L).
- Elemental budgets: an upper limit on volatile P from a PH3 limit (2024ApJ...968L..19F), C/O from CS/SO
  (2018A&A...617A..28S, 2021A&A...651L...6B, 2024RAA....24g5017M).
- Circumstellar envelopes of AGB stars: photodissociation radii and daughter-species shells
  (2019A&A...629A.146V, 2017A&A...601A...4A, 2015ApJ...814..143A, 2018A&A...612L..11S,
  2021A&A...655A..80D).
- Gas-grain partitioning in a red supergiant wind: an analytic NaCl model of accretion, thermal
  desorption and photodesorption with binding energies of 5000, 10000 and 15000 K (2016A&A...592A..76D).
- Diffuse and extragalactic gas: steady-state formulae for molecular ions (2019A&A...622A..26G), ortho/para
  ratios with a nuclear-spin network (2017A&A...608A..96L), PDR versus shock models for HCNH+ in NGC 253
  (2025A&A...696A..31G), low-metallicity hot cores (2020ApJ...891..164S, 2019ESC.....3.2088S).

## When not to use

- You still need the observed column densities, Trot or Tex: do that first with the
  **rotational-diagram-lte** skill (LTE, rotation diagrams, XCLASS, MADCUBA, Weeds, CASSIS) or the
  **non-lte-excitation** skill (RADEX, LVG grids). This skill starts from their outputs.
- The H2 column or gas mass behind the abundance denominator: **dust-continuum-mass** or
  **gas-mass-co-conversion**.
- Isotope ratios as the science result (12C/13C, D/H fractionation measured from lines): **isotopic-ratios**.
- Fitting disk temperature or density structure to visibilities with no chemistry: **radiative-transfer-modelling**
  or **uv-plane-fitting**.
- Assigning lines: **line-identification**. Envelope chemistry tied to mass-loss history in AGB stars may
  overlap with **evolved-star-envelopes**.

## Steps

1. **Fix the observational quantities to compare.**
   - Goal: model-comparable numbers with honest errors.
   - Method: abundances X = N(mol)/N(H2) at defined positions (2020ApJ...898...54T), ratios to a reference
     species such as HNCO (2017A&A...601A..49B) or CH3OH (2019ESC.....3.2088S, 2024A&A...691A.180F),
     disk-averaged columns (2018A&A...617A..28S), or radial intensity profiles and line images
     (2015ApJ...810..112O, 2019ApJ...883...98Z). A ratio removes the common N(H2) denominator
     algebraically, but only if both species come from the same emitting region, aperture and column
     convention. Differences in source size, excitation and opacity do not cancel: filling factors were
     uncertain in 2019ApJ...876...72L and columns scale with the assumed emitting area in
     2021A&A...651L...6B. Propagate those differential errors into the ratio.
   - Watch the denominator: dust may be optically thick so N(H2) is a lower limit and abundances upper
     limits (2017MNRAS.469.2230M); resolved-out continuum can lower N(H2) (2024ApJ...968L..19F); columns
     scale inversely with the assumed emitting area (2021A&A...651L...6B).
2. **Choose the model class for the environment.**
   - Hot cores and corinos: two-stage collapse plus warm-up gas-grain model (MAGICKAL in 2014Sci...345.1584B,
     2016A&A...587A..92M, 2017A&A...601A..48G, 2017A&A...601A..49B, 2019A&A...628A..10B,
     2019A&A...628A..27B; UCLCHEM in 2024ESC.....8..665M and 2017MNRAS.469.2230M; NAUTILUS in
     2016ApJ...825...79S, card).
   - Cold clouds and prestellar cores: static gas-grain or three-phase rate-equation model at fixed density
     (NAUTILUS in 2024A&A...687A.233M; three-phase model at 1e5 yr in 2024ApJ...968L..19F; static UCLCHEM grid
     in 2024A&A...691A.180F).
   - Disks: chemistry on a 1+1D or 2D physical structure, then line radiative transfer (ALCHEMIC in
     2018A&A...617A..28S and 2017ApJ...835..228T, the latter per its card; NAUTILUS in 2019ApJ...876...72L and 2024RAA....24g5017M;
     RAC2D in 2019ApJ...883...98Z; DALI in 2016A&A...585A..58V, 2019ApJ...871..107F, 2025ApJ...989....1Z;
     Du and Bergin code in 2016ApJ...831..101B). A one-point model at midplane conditions is a cheaper
     option for ratio questions (PURE-C in 2024JKAS...57..163L).
   - Envelopes of evolved stars: gas-phase photochemistry in a uniformly expanding shell (about 8000
     reactions in 2019A&A...629A.146V; UMIST and KIDA network in 2015ApJ...814..143A; Meudon PDR code in
     2017A&A...601A...4A; RATE12 extended with Al chemistry in 2021A&A...655A..80D).
   - Extragalactic and diffuse gas: static, PDR and C-type shock models (Chempl and UCLCHEM in
     2025A&A...696A..31G) or analytic steady state (2019A&A...622A..26G, 2018A&A...617A.120M).
3. **Set the physical history and fixed inputs.**
   - Goal: inputs taken from the observations where possible, defaults otherwise, every one written down.
   - Method: see the parameter table below and `references/parameters.md`. Typical hot-core history:
     free-fall collapse from nH 3000 to 2e8 cm^-3, then static warm-up to 400 K (2014Sci...345.1584B), with
     8 K minimum dust temperature (2017A&A...601A..49B, 2016A&A...587A..92M). Disk structure comes from
     an SED or HD-constrained model of the same source (2018ApJ...859..131L, card) or a published
     fiducial (2017ApJ...835..228T, card).
   - Gas and dust temperature: equal temperatures are a common simplification in static cloud models
     (2025A&A...696A..31G, static models only), cold homogeneous gas (2024A&A...687A.233M) and 1+1D disk
     models (2019ApJ...876...72L, 2018A&A...617A..28S), but 2024RAA....24g5017M uses a separate two-layer
     gas temperature over a RADMC3D dust temperature. Justify thermal coupling for the layer that emits
     the line before setting Tgas = Tdust.
4. **Add or modify the chemistry under test.**
   - Method: add reactions and binding energies for the new species (CH3NCO 3575 K and CH3NHCHO 6281 K in
     2017A&A...601A..49B; CH3SH 5534 K, same as methanol, and C2H5SH 6230 K in 2016A&A...587A..92M; NH2 + CN
     on grains in 2024ESC.....8..665M). Where rates are unknown, papers either borrow an analogue (SiS
     photodissociation set equal to SiO in 2019A&A...629A.146V) or compute them (Gaussian 16 and MESMER
     RRKM rates in 2021A&A...655A..80D).
   - Run the network with and without the new route so the comparison isolates it.
5. **Run a small grid, not one model.**
   - Method: vary the parameters the observations cannot pin: warm-up timescale (5e4, 2e5, 1e6 yr to
     200 K in 2019A&A...628A..10B), cosmic-ray rate (1.3e-17 to 1.3e-14 s^-1 in 2019A&A...628A..27B),
     barriers (KIDA values in 2024JKAS...57..163L, high CN-addition barriers in 2017A&A...601A..48G), C/O
     (0.5 to 1.5 in 2024RAA....24g5017M), volatile P (2.57e-7 to 2.57e-9 in 2024ApJ...968L..19F). Large
     grids: 65536 static UCLCHEM models in 2024A&A...691A.180F.
6. **Extract model quantities that match the observable.**
   - Hot cores: peak gas-phase abundance during warm-up and the temperature where it peaks
     (2019A&A...628A..10B); compare peak temperatures with the observed Trot (2014Sci...345.1584B).
     Check the phase of the model number: the NH2CN maximum of 5.12e-10 at about 3.8e5 yr in
     2024ESC.....8..665M is "on the grain", yet it was compared with the observed (gas-phase)
     abundance. Only a documented gas-phase prediction should be compared with a gas-phase observation.
   - Static models: ratios at a chosen time (1e6 yr in 2024A&A...691A.180F, 1e5 yr in 2024ApJ...968L..19F)
     and show the result holds at other times (3e4 and 1e6 yr in 2024ApJ...968L..19F).
   - Disks: model column-density medians over the observed radial range (100 to 800 au in
     2018A&A...617A..28S), or synthetic images convolved to the observed beam (2019ApJ...871..107F).
     Beam matching alone does not reproduce interferometric spatial filtering or beam dilution (both
     flagged in 2025A&A...696A..31G); where large-scale emission matters, sample the model like the
     data (CASA simobserve with the same array configuration in 2017ApJ...835..228T, card;
     vis_sample in 2018ApJ...859..131L, card) and extract spectra with the same aperture.
   - Rare isotopologues: papers whose network has no fractionation divide the main-isotopologue output
     by a fixed ISM ratio, X(rare) = X(main)/R (CO/C18O = 570, CO/13CO = 69 in 2019ApJ...883...98Z;
     factors 500 and 70 for C18O and H13CO+ in 2015ApJ...810..112O). This is an approximation: leaving
     fractionation out of the network does not mean the source lacks it, and isotope-selective
     photodissociation contributed about 10 to 20% of the C18O intensity inside the AS 209 gaps
     (2019ApJ...871..107F). Bound that effect before reading depletion or gas structure from a rare
     isotopologue.
7. **Radiative transfer and simulated observation (disks, envelopes, cores).**
   - Method: LIME (2015ApJ...810..112O, 2017A&A...599A.101V in LTE to save CPU per its card,
     2025ApJ...992...55T), RATRAN (2018A&A...617A.120M, 2019ApJ...875...96N), RAC2D LTE ray tracing
     (2019ApJ...883...98Z), RADMC-3D line transfer plus vis_sample simulated ALMA observations
     (2018ApJ...859..131L, card), LIME plus CASA simobserve with the same array configuration
     (2017ApJ...835..228T, card), DALI channel maps convolved with the observed beam
     (2019ApJ...871..107F), non-LTE mcp for envelopes (2018A&A...612L..11S).
   - Excitation inputs: check that collisional rate coefficients exist for the species (none were
     available for PH3-H2 in 2024ApJ...968L..19F) and whether infrared pumping matters (only partly
     included in 2015ApJ...814..143A; uncertain for C4H, C6H and C3N in 2017A&A...601A...4A). State the
     excitation assumption you fell back on and how far it limits the abundance you infer.
8. **Compare and judge.**
   - What papers do: by eye or heuristic (2016ApJ...831..101B, 2018A&A...617A.120M, 2016A&A...585A..58V),
     a parametric grid without a formal statistic (2019ApJ...871..107F), ranking by mean squared error with
     the 50 lowest-MSE models kept (2024A&A...691A.180F), scaling a model abundance profile until the
     lines best reproduce the data without overpredicting the non-detections (2021A&A...655A..80D). No
     fit of chemical-network inputs by chi2 or MCMC is documented in the pack's excerpts or aggregates
     (the method summaries are incomplete, so this is not proof that none exists);
     2016A&A...585A..58V says explicitly it used neither because the models were too slow and had too
     many parameters.
   - Upper limits and identifiability: treat non-detections as inequality constraints, as
     2021A&A...655A..80D did. When the data cannot separate models, report the allowed range rather
     than a best value: 2024RAA....24g5017M could not determine a best-fitting C/O, and
     2018A&A...617A..28S could not constrain C/O more accurately because SO and SO2 were not detected.
   - Recommendation: report the tolerance up front (see Verification checks) and list which species the
     best model misses and by how much.

## Parameter defaults and ranges

Counts are my hand count of distinct pack bibcodes whose parameter, assumption or excerpt lines state the
setting (not of all 46 papers); where a bibcode's value comes only from its methods card it is marked
"card" and still counted. Longer per-paper table: `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| H2 cosmic-ray ionisation rate, clouds, cores, hot cores | 1.3e-17 s^-1 | 1.26e-17 to 3e-17 | 9 | 2017A&A...601A..48G, 2019A&A...628A..10B, 2024ESC.....8..665M, 2015ApJ...803...70S, 2024ApJ...968L..19F |
| Cosmic-ray rate, envelopes of evolved stars | 1.2e-17 s^-1 | 1.2e-17 | 3 | 2019A&A...629A.146V, 2017A&A...601A...4A, 2015ApJ...814..143A |
| Cosmic-ray rate, disks | standard 1e-17 to 1.3e-17, or reduced to 1e-19 to 1.36e-18 s^-1 | 1e-20 (test) to 5e-17 | 7 | 2017ApJ...835..228T, 2024RAA....24g5017M, 2016ApJ...831..101B, 2019ApJ...883...98Z, 2015ApJ...810..112O, 2017A&A...599A.101V |
| Cosmic-ray rate, enhanced environments | grid | 1e-15 to 1.3e-14 | 2 | 2019A&A...628A..27B, 2019A&A...624L...5P |
| Post-collapse or warm-phase density, hot core | nH 2e8 cm^-3 (4 MAGICKAL papers) | nH 1e8 to 2e8; n(H2) 5e7 and 5e8; n 6e6 (convention not stated) | 8 | nH: 2014Sci...345.1584B, 2016A&A...587A..92M, 2017A&A...601A..48G, 2017A&A...601A..49B, 2024ESC.....8..665M; n(H2): 2017MNRAS.469.2230M, 2019ESC.....3.2088S; n: 2020ApJ...891..164S |
| Warm-up end temperature | 400 K (MAGICKAL) | 110 to 400 K | 8 | 2014Sci...345.1584B, 2019A&A...628A..10B, 2024ESC.....8..665M, 2017MNRAS.469.2230M |
| Warm-up timescale | intermediate | 5e4 to 1e6 yr | 4 | 2019A&A...628A..10B, 2017A&A...601A..49B, 2020ApJ...891..164S, 2017MNRAS.469.2230M |
| Minimum dust temperature (collapse) | 8 K | fixed at 8 K, or gridded | 3 | 2017A&A...601A..49B, 2016A&A...587A..92M, 2019A&A...628A..27B |
| Cold-cloud stage | 10 K, nH 2e4 to 2.5e4, Av 10 to 15 | | 2 | 2024RAA....24g5017M, 2024A&A...687A.233M |
| Disk model age | 1 Myr | 300 kyr to 5 Myr (1e7 yr in one case) | 9 (6 pack, 3 card) | pack: 2016ApJ...831..101B, 2015ApJ...810..112O, 2018A&A...617A..28S, 2019ApJ...876...72L, 2019ApJ...883...98Z, 2024RAA....24g5017M; card: 2017A&A...599A.101V, 2017ApJ...835..228T, 2018ApJ...859..131L |
| Grain radius | 0.1 um single size | 0.005 to 7 um | 6 | 2017A&A...601A..48G, 2019ApJ...876...72L, 2018A&A...617A..28S, 2017ApJ...835..228T |
| Gas-to-dust mass ratio | 100 | 100 to 500 (300 for the LMC, 0.002 dust-to-gas in an RSG wind) | 8 | 2018A&A...617A..28S, 2019ApJ...883...98Z, 2024A&A...691A.180F, 2016A&A...592A..76D |
| Sulfur elemental abundance | depleted, 8e-8 | | 2 | 2016A&A...587A..92M, 2019ApJ...876...72L |
| C/O | solar-like 0.46 | 0.46 to 1.5 | 3 | 2018A&A...617A..28S, 2024RAA....24g5017M, 2021A&A...651L...6B |
| CO binding energy | 855 to 1150 K | 855 to 1150 K | 2 | 2015ApJ...810..112O (1150 K, 1000 K tested), 2017A&A...599A.101V (855 K, N2 800 K, card) |
| Photodesorption yield (species-specific) | no common value | CO 7e-3; P-bearing species 1e-3 per UV photon | 2 | 2015ApJ...810..112O (CO), 2024ApJ...968L..19F (P species) |
| Chemical desorption probability (one reaction with atomic H) | 4% | 2 to 8% tested | 1 | 2024ApJ...968L..19F |
| Sticking probability | 1 | 0.85 to 1 | 3 | 2024ESC.....8..665M, 2016A&A...592A..76D, 2017A&A...599A.101V (CO 0.9, N2 0.85, card) |
| Gas and dust temperature | equal in static, cold or 1+1D models | two-layer gas T over RADMC3D dust T in one disk | 5 | equal: 2025A&A...696A..31G (static models only), 2019ApJ...876...72L, 2018A&A...617A..28S, 2024A&A...687A.233M; decoupled: 2024RAA....24g5017M |

Surface-process values are tied to the species or reaction they were set for. Do not apply the CO
photodesorption yield, the P-species yield or the 4% chemical desorption to a whole network without a
reason.

## Software

Counts are from the pack aggregate "Software named in the matched steps" (one paper can name several; tool
names differ in spelling, so UCLCHEM appears as uclchem 3, ucl_chem 1 and a UCL_CHEM-type CSE model 1).

| Tool | Used for | Count | Examples |
|---|---|---|---|
| MAGICKAL | three-phase gas-grain collapse plus warm-up, hot-core COMs | 6 | 2014Sci...345.1584B, 2019A&A...628A..10B, 2019A&A...628A..27B |
| NAUTILUS | gas-grain and three-phase models for clouds, hot cores and disks; gas-phase nuclear-spin network | 5 | 2019ApJ...876...72L, 2024RAA....24g5017M, 2024A&A...687A.233M, 2017A&A...608A..96L (card) |
| UCLCHEM / UCL_CHEM | two-phase warm-up, static grids, C-type shocks | 3 + 1 + 1 | 2024ESC.....8..665M, 2024A&A...691A.180F, 2025A&A...696A..31G, 2017MNRAS.469.2230M |
| DALI | 2D disk thermo-chemistry and line images | 3 | 2016A&A...585A..58V, 2019ApJ...871..107F, 2025ApJ...989....1Z |
| ALCHEMIC | disk gas-grain chemistry on 1+1D structure | 2 | 2018A&A...617A..28S, 2017ApJ...835..228T (card) |
| RAC2D, Du and Bergin code | 2D time-dependent disk chemistry | 1, 1 | 2019ApJ...883...98Z, 2016ApJ...831..101B |
| PURE-C, Chempl | one-point or static models | 1, 1 | 2024JKAS...57..163L, 2025A&A...696A..31G |
| RATE12 / Meudon PDR | envelope gas-phase photochemistry | 1, 1 | 2021A&A...655A..80D, 2017A&A...601A...4A |
| Gaussian 16, MESMER | new reaction rates from quantum chemistry and RRKM | 1, 1 | 2021A&A...655A..80D |
| SciPy odeint | reduced network solved directly | 1 | 2017A&A...599A.101V (card) |
| LIME, RATRAN, mcp | line radiative transfer of model abundances | 2, 2, 1 | 2015ApJ...810..112O, 2025ApJ...992...55T, 2019ApJ...875...96N, 2018A&A...617A.120M, 2018A&A...612L..11S |
| RADMC-3D | 2 software mentions (radmc3d 1, radmc-3d 1), two different uses: dust temperature for a chemical model (2024RAA....24g5017M) and line transfer of model abundances (2018ApJ...859..131L, card) | 2 | 2024RAA....24g5017M, 2018ApJ...859..131L |
| vis_sample | simulated ALMA visibilities from a model image | 1 | 2018ApJ...859..131L (card) |

Code versions, network files and full initial abundances are rarely given: the cards flag MAGICKAL network
files (2017A&A...601A..49B), UCLCHEM version and warm-up exponent (2024ESC.....8..665M), PURE-C network
(2024JKAS...57..163L) and RAC2D configuration (2019ApJ...883...98Z) as not stated.

## Pitfalls

- **Generic model, specific source.** Models not tuned to the target allow only qualitative comparison
  (2015ApJ...810..112O, 2019ApJ...876...72L, 2025ApJ...992...55T). Say so instead of quoting best-fit
  physics.
- **Order-of-magnitude misses are common.** NH2CHO and CH3CONH2 overproduced by more than 10
  (2017A&A...601A..49B); NH2CHO underproduced by 10 (2017MNRAS.469.2230M); CH3CN in IRC+10216 underestimated
  by more than two orders of magnitude (2015ApJ...814..143A); iso/normal propyl cyanide 2.2 in the model
  against 0.4 observed (2014Sci...345.1584B); CH3SH/C2H5SH 3.1 against more than 21 (2016A&A...587A..92M);
  LMC CH3OCH3/CH3OH about 0.01 against 0.1 to 0.2 (2019ESC.....3.2088S). Report misses for every species
  in the comparison set, not only the hits.
- **Static models for dynamic sources.** No single static model fits all ratios in WB670
  (2024A&A...691A.180F); ages are unreliable when every source shares one accretion history
  (2019A&A...628A..27B); a one-point model cannot speak to ring structure or absolute columns
  (2024JKAS...57..163L).
- **Observed side errors.** Tex fixed to one species for all (2024A&A...691A.180F, N_tot uncertain up to
  a factor 2); Tex-N degeneracy of a factor about 2 (2020A&A...644A..84M); possibly thick lines
  (2020ApJ...898...54T, 2019ApJ...876...72L); unidentified blends (2020A&A...644A..84M). Fix these with the
  upstream skills before blaming the network.
- **Poorly constrained inputs.** Cosmic-ray rate (2017A&A...601A..48G), available sulfur
  (2018A&A...617A..28S), binding energies borrowed from analogues (2016A&A...587A..92M), and one species'
  binding energy can differ between papers (CH3NCO 3575 K in 2017A&A...601A..49B against 6486 K in
  2019A&A...628A..10B).
- **Geometry.** Spherical or 1D models miss arcs and asymmetries (2017A&A...601A...4A,
  2021A&A...655A..80D, which notes the true uncertainties are much larger than formal ones); smooth disk
  profiles ignore substructure (2019ApJ...883...98Z); 2D temperature structure limits disk fits
  (2019ApJ...871..107F).
- **Wrong phase or wrong normalisation.** A grain-surface model peak compared with a gas-phase
  observation (2024ESC.....8..665M, see Steps), or n(H2) read as nH (2017MNRAS.469.2230M states a
  constant H2 density of 5e8 cm^-3), shifts the comparison by a factor 2 or more. Abundances are quoted
  per H (CO 1.4e-4 in 2019ApJ...883...98Z; volatile P limit in 2024ApJ...968L..19F) or per H2
  (2017A&A...601A...4A, 2021A&A...655A..80D); convert before comparing.
- **Omitted chemistry behind a tracer.** The N2H+ snowline model of 2017A&A...599A.101V ignores
  gas-phase CO and N2 formation and underpredicts emission beyond about 60 au. Before reading a CO
  snowline location from N2H+, check whether such omitted formation chemistry moves the predicted
  emission peak.
- **Excitation and observing effects mistaken for chemistry.** Missing collisional data
  (2024ApJ...968L..19F), partial infrared pumping (2015ApJ...814..143A, 2017A&A...601A...4A), spatial
  filtering of large-scale emission and neglected beam dilution (2025A&A...696A..31G) all change the
  intensity a model must match.
- **Thin data.** Single lines make density and abundance degenerate (2019A&A...629A.146V); only five clean
  lines kept a detection tentative (2017A&A...601A..49B); executed time was about 20% of the request in
  2019ApJ...875...96N.
- **Unstated settings.** Beyond the imaging items flagged in most cards (continuum subtraction, CASA
  version, self-calibration), the cards flag chemical network details, best-fit criteria and initial
  conditions as not stated (2016ApJ...831..101B, 2024ESC.....8..665M, 2017A&A...601A..48G,
  2019A&A...622A..26G). Publish the network, initial abundances and grid.

## Verification checks

What the papers did:
- State a numeric tolerance: within a factor 1.5 (2016ApJ...831..101B; fall-off radii in
  2019A&A...629A.146V), within a factor of a few (2019ApJ...876...72L), modelling uncertainties of a
  factor 3 to 10 (2018A&A...617A..28S), density and delta within an order of magnitude and radii within
  5 au from a small grid (2016A&A...585A..58V).
- Robustness to the parameters you fixed: other model times and desorption probabilities
  (2024ApJ...968L..19F), KIDA barriers, UV and cosmic-ray changes (2024JKAS...57..163L), high activation
  barriers (2017A&A...601A..48G), binding energy, structure and cosmic-ray rate (2015ApJ...810..112O),
  gas-to-dust about 3000 (2024A&A...691A.180F), ten times the gas mass (2016ApJ...831..101B).
- Independent checks of the physical model: peak model temperatures against observed Trot
  (2014Sci...345.1584B); snowline positions against the literature (2019ApJ...883...98Z); CO single-dish
  lines reproduced before trusting CI (2018A&A...612L..11S); a null model (no gas gaps cannot reproduce
  C18O in 2019ApJ...871..107F).
- Cross-checks of the chemistry: steady state confirmed by a time-dependent run (2017A&A...599A.101V,
  card); agreement with an analytic model (2017A&A...608A..96L, card); reproducing cold-core upper limits as well as
  the hot-corino value (2017MNRAS.469.2230M); rates tuned only inside the quantum-chemistry uncertainty of
  6 kJ/mol (2021A&A...655A..80D).

What a careful referee adds (recommendation, not pack evidence): show model-to-observed ratios for every
species in one figure, including the misses; propagate the N(H2) and Tex systematics into the observed
side; show that the conclusion survives the full grid rather than one favoured model; and say which
inputs were tuned to the data and which were defaults. Also check that the model quantity is the same
phase (gas, not ice) and normalisation (per H or per H2) as the observed one; that synthetic images
went through the same spatial filtering, beam and extraction aperture as the data, with missing flux
and differential beam dilution assessed (the limitation 2025A&A...696A..31G admits); that collisional
data and pumping were available for the excitation model; and that non-detections are kept as upper
limits and not overpredicted (2021A&A...655A..80D).

## Source cards

All 46 papers are listed in `references/sources.md`. Most informative for this technique:

- 2019A&A...628A..10B: MAGICKAL warm-up timescales, peak-abundance comparison for urea
- 2019A&A...628A..27B: cosmic-ray rate and minimum dust temperature grid across Sgr B2(N) hot cores
- 2017A&A...601A..48G: branched-chain chemistry, high-barrier robustness test
- 2014Sci...345.1584B: collapse plus warm-up, model peak temperatures against Trot
- 2024ESC.....8..665M: UCLCHEM two-phase model with a new grain reaction
- 2024A&A...691A.180F: 65536-model static UCLCHEM grid ranked by MSE, outer Galaxy
- 2024ApJ...968L..19F: elemental P limit with time and desorption tests
- 2024JKAS...57..163L: one-point PURE-C model of HCN/HNC with barrier tests
- 2018A&A...617A..28S: ALCHEMIC disk grid, C/O from sulfur species, factor 3 to 10 tolerance
- 2019ApJ...876...72L: NAUTILUS 1+1D disk models of CS and H2CS
- 2019ApJ...883...98Z: RAC2D radial CO depletion, cosmic-ray tests
- 2015ApJ...810..112O: DCO+ double rings, small parameter study with LIME
- 2016ApJ...831..101B: C2H rings from C and O depletion, factor 1.5 agreement
- 2017A&A...599A.101V: reduced N2H+ network, binding energies (card), steady-state check, outer-disk
  underprediction
- 2019ApJ...871..107F: DALI grid for gas gaps convolved to the beam
- 2019A&A...629A.146V: envelope photochemistry and fall-off radii
- 2021A&A...655A..80D: RATE12 extended with computed Al rates
- 2018A&A...612L..11S: envelope chemistry fed into non-LTE mcp
- 2025A&A...696A..31G: static, PDR and shock models for HCNH+ in NGC 253
- 2017A&A...608A..96L: nuclear-spin network for H2Cl+ ortho/para
- 2018A&A...617A.120M: analytic DCO+ network with RATRAN, by-eye profile fit
- 2017MNRAS.469.2230M: UCL_CHEM hot corino with cold-core upper-limit check
