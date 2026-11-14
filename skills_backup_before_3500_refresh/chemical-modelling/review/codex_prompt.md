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

=== SKILL.md (chemical-modelling) ===
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

Counts below are from the evidence pack for this technique (46 papers). One of them (2018, DG Tau disk
wind) only borrows a thermo-chemical temperature structure and is off-topic, so on-topic counts are out of
45. Three more use disk thermo-chemical models to infer gas structure or gas mass rather than abundances
(2016A&A...585A..58V, 2019ApJ...871..107F, 2025ApJ...989....1Z); they are included as a variant.

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
- Circumstellar envelopes of AGB stars and supergiants: photodissociation radii and daughter-species
  shells (2019A&A...629A.146V, 2017A&A...601A...4A, 2015ApJ...814..143A, 2018A&A...612L..11S,
  2021A&A...655A..80D, 2016A&A...592A..76D).
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
     (2015ApJ...810..112O, 2019ApJ...883...98Z). Ratios cancel the H2 column and beam-filling errors that
     dominate absolute abundances; most COM papers compare ratios for that reason.
   - Watch the denominator: dust may be optically thick so N(H2) is a lower limit and abundances upper
     limits (2017MNRAS.469.2230M); resolved-out continuum can lower N(H2) (2024ApJ...968L..19F); columns
     scale inversely with the assumed emitting area (2021A&A...651L...6B).
2. **Choose the model class for the environment.**
   - Hot cores and corinos: two-stage collapse plus warm-up gas-grain model (MAGICKAL in 2014Sci...345.1584B,
     2016A&A...587A..92M, 2017A&A...601A..48G, 2017A&A...601A..49B, 2019A&A...628A..10B,
     2019A&A...628A..27B; UCLCHEM in 2024ESC.....8..665M and 2017MNRAS.469.2230M; NAUTILUS in
     2016ApJ...825...79S).
   - Cold clouds and prestellar cores: static gas-grain or three-phase rate-equation model at fixed density
     (NAUTILUS in 2024A&A...687A.233M; three-phase model at 1e5 yr in 2024ApJ...968L..19F; static UCLCHEM grid
     in 2024A&A...691A.180F).
   - Disks: chemistry on a 1+1D or 2D physical structure, then line radiative transfer (ALCHEMIC in
     2018A&A...617A..28S and 2017ApJ...835..228T; NAUTILUS in 2019ApJ...876...72L and 2024RAA....24g5017M;
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
     an SED or HD-constrained model of the same source (2018ApJ...859..131L) or a published fiducial
     (2017ApJ...835..228T).
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
     (2019A&A...628A..10B, 2024ESC.....8..665M); compare peak temperatures with the observed Trot
     (2014Sci...345.1584B).
   - Static models: ratios at a chosen time (1e6 yr in 2024A&A...691A.180F, 1e5 yr in 2024ApJ...968L..19F)
     and show the result holds at other times (3e4 and 1e6 yr in 2024ApJ...968L..19F).
   - Disks: model column-density medians over the observed radial range (100 to 800 au in
     2018A&A...617A..28S), or synthetic images convolved to the observed beam. Scale main-isotopologue
     output by ISM isotope ratios when the network has no fractionation (CO/C18O = 570, CO/13CO = 69 in
     2019ApJ...883...98Z; factors 500 and 70 for C18O and H13CO+ in 2015ApJ...810..112O).
7. **Radiative transfer and simulated observation (disks, envelopes, cores).**
   - Method: LIME (2015ApJ...810..112O, 2017A&A...599A.101V in LTE to save CPU, 2025ApJ...992...55T), RATRAN
     (2018A&A...617A.120M, 2019ApJ...875...96N), RAC2D LTE ray tracing (2019ApJ...883...98Z), RADMC-3D plus
     simulated ALMA observations (2018ApJ...859..131L), LIME plus CASA simobserve with the same array
     configuration (2017ApJ...835..228T), DALI channel maps convolved with the observed beam
     (2019ApJ...871..107F), non-LTE mcp for envelopes (2018A&A...612L..11S).
8. **Compare and judge.**
   - What papers do: by eye or heuristic (2016ApJ...831..101B, 2018A&A...617A.120M, 2016A&A...585A..58V),
     a parametric grid without a formal statistic (2019ApJ...871..107F), ranking by mean squared error with
     the 50 lowest-MSE models kept (2024A&A...691A.180F), scaling a model abundance profile until the
     lines fit (2021A&A...655A..80D). No paper in the pack fits the chemical-network inputs with chi2 or
     MCMC; 2016A&A...585A..58V says the models were too slow and had too many parameters.
   - Recommendation: report the tolerance up front (see Verification checks) and list which species the
     best model misses and by how much.

## Parameter defaults and ranges

Counts are my count of distinct pack bibcodes whose parameter, assumption or excerpt lines state the
setting (not of all 46 papers). Longer per-paper table: `references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| H2 cosmic-ray ionisation rate, clouds, cores, hot cores | 1.3e-17 s^-1 | 1.26e-17 to 3e-17 | 9 | 2017A&A...601A..48G, 2019A&A...628A..10B, 2024ESC.....8..665M, 2015ApJ...803...70S, 2024ApJ...968L..19F |
| Cosmic-ray rate, envelopes of evolved stars | 1.2e-17 s^-1 | 1.2e-17 | 3 | 2019A&A...629A.146V, 2017A&A...601A...4A, 2015ApJ...814..143A |
| Cosmic-ray rate, disks | standard 1e-17 to 1.3e-17, or reduced to 1e-19 to 1.36e-18 s^-1 | 1e-20 (test) to 5e-17 | 7 | 2017ApJ...835..228T, 2024RAA....24g5017M, 2016ApJ...831..101B, 2019ApJ...883...98Z, 2015ApJ...810..112O, 2017A&A...599A.101V |
| Cosmic-ray rate, enhanced environments | grid | 1e-15 to 1.3e-14 | 2 | 2019A&A...628A..27B, 2019A&A...624L...5P |
| Post-collapse density, hot core | nH 2e8 cm^-3 | 6e6 to 5e8 | 8 | 2017A&A...601A..48G, 2017A&A...601A..49B, 2024ESC.....8..665M, 2017MNRAS.469.2230M |
| Warm-up end temperature | 400 K (MAGICKAL) | 110 to 400 K | 8 | 2014Sci...345.1584B, 2019A&A...628A..10B, 2024ESC.....8..665M, 2017MNRAS.469.2230M |
| Warm-up timescale | intermediate | 5e4 to 1e6 yr | 4 | 2019A&A...628A..10B, 2017A&A...601A..49B, 2020ApJ...891..164S, 2017MNRAS.469.2230M |
| Minimum dust temperature (collapse) | 8 K | fixed at 8 K, or gridded | 3 | 2017A&A...601A..49B, 2016A&A...587A..92M, 2019A&A...628A..27B |
| Cold-cloud stage | 10 K, nH 2e4 to 2.5e4, Av 10 to 15 | | 2 | 2024RAA....24g5017M, 2024A&A...687A.233M |
| Disk model age | 1 Myr | 300 kyr to 5 Myr (1e7 yr in one case) | 8 | 2019ApJ...876...72L, 2019ApJ...883...98Z, 2018ApJ...859..131L, 2018A&A...617A..28S |
| Grain radius | 0.1 um single size | 0.005 to 7 um | 6 | 2017A&A...601A..48G, 2019ApJ...876...72L, 2018A&A...617A..28S, 2017ApJ...835..228T |
| Gas-to-dust mass ratio | 100 | 100 to 500 (300 for the LMC, 0.002 dust-to-gas in an RSG wind) | 8 | 2018A&A...617A..28S, 2019ApJ...883...98Z, 2024A&A...691A.180F, 2016A&A...592A..76D |
| Sulfur elemental abundance | depleted, 8e-8 | | 2 | 2016A&A...587A..92M, 2019ApJ...876...72L |
| C/O | solar-like 0.46 | 0.46 to 1.5 | 3 | 2018A&A...617A..28S, 2024RAA....24g5017M, 2021A&A...651L...6B |
| CO binding energy | 855 to 1150 K | 855 to 1150 K | 2 | 2015ApJ...810..112O, 2017A&A...599A.101V |
| Photodesorption yield | 1e-3 per UV photon | 1e-3 to 7e-3 | 2 | 2024ApJ...968L..19F, 2015ApJ...810..112O |
| Chemical desorption probability | 4% | 2 to 8% tested | 1 | 2024ApJ...968L..19F |
| Sticking probability | 1 | 0.85 to 1 | 3 | 2024ESC.....8..665M, 2016A&A...592A..76D, 2017A&A...599A.101V |
| Gas and dust temperature | equal | | 4 | 2025A&A...696A..31G, 2019ApJ...876...72L, 2018A&A...617A..28S, 2024A&A...687A.233M |

## Software

Counts are from the pack aggregate "Software named in the matched steps" (one paper can name several; tool
names differ in spelling, so UCLCHEM appears as uclchem 3, ucl_chem 1 and a UCL_CHEM-type CSE model 1).

| Tool | Used for | Count | Examples |
|---|---|---|---|
| MAGICKAL | three-phase gas-grain collapse plus warm-up, hot-core COMs | 6 | 2014Sci...345.1584B, 2019A&A...628A..10B, 2019A&A...628A..27B |
| NAUTILUS | gas-grain and three-phase models for clouds, hot cores and disks; gas-phase nuclear-spin network | 5 | 2019ApJ...876...72L, 2024RAA....24g5017M, 2017A&A...608A..96L |
| UCLCHEM / UCL_CHEM | two-phase warm-up, static grids, C-type shocks | 3 + 1 + 1 | 2024ESC.....8..665M, 2024A&A...691A.180F, 2025A&A...696A..31G, 2017MNRAS.469.2230M |
| DALI | 2D disk thermo-chemistry and line images | 3 | 2016A&A...585A..58V, 2019ApJ...871..107F, 2025ApJ...989....1Z |
| ALCHEMIC | disk gas-grain chemistry on 1+1D structure | 2 | 2018A&A...617A..28S, 2017ApJ...835..228T |
| RAC2D, Du and Bergin code | 2D time-dependent disk chemistry | 1, 1 | 2019ApJ...883...98Z, 2016ApJ...831..101B |
| PURE-C, Chempl | one-point or static models | 1, 1 | 2024JKAS...57..163L, 2025A&A...696A..31G |
| RATE12 / Meudon PDR | envelope gas-phase photochemistry | 1, 1 | 2021A&A...655A..80D, 2017A&A...601A...4A |
| Gaussian 16, MESMER | new reaction rates from quantum chemistry and RRKM | 1, 1 | 2021A&A...655A..80D |
| SciPy odeint | reduced network solved directly | 1 | 2017A&A...599A.101V |
| LIME, RATRAN, RADMC-3D, mcp | line radiative transfer of model abundances | 2, 2, 2, 1 | 2015ApJ...810..112O, 2019ApJ...875...96N, 2018ApJ...859..131L, 2018A&A...612L..11S |

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
- Cross-checks of the chemistry: steady state confirmed by a time-dependent run (2017A&A...599A.101V);
  agreement with an analytic model (2017A&A...608A..96L); reproducing cold-core upper limits as well as
  the hot-corino value (2017MNRAS.469.2230M); rates tuned only inside the quantum-chemistry uncertainty of
  6 kJ/mol (2021A&A...655A..80D).

What a careful referee adds (recommendation, not pack evidence): show model-to-observed ratios for every
species in one figure, including the misses; propagate the N(H2) and Tex systematics into the observed
side; show that the conclusion survives the full grid rather than one favoured model; and say which
inputs were tuned to the data and which were defaults.

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
- 2017A&A...599A.101V: reduced N2H+ network, binding energies, steady-state check
- 2019ApJ...871..107F: DALI grid for gas gaps convolved to the beam
- 2019A&A...629A.146V: envelope photochemistry and fall-off radii
- 2021A&A...655A..80D: RATE12 extended with computed Al rates
- 2018A&A...612L..11S: envelope chemistry fed into non-LTE mcp
- 2025A&A...696A..31G: static, PDR and shock models for HCNH+ in NGC 253
- 2017A&A...608A..96L: nuclear-spin network for H2Cl+ ortho/para
- 2018A&A...617A.120M: analytic DCO+ network with RATRAN, by-eye profile fit
- 2017MNRAS.469.2230M: UCL_CHEM hot corino with cold-core upper-limit check

=== references/parameters.md ===
# Chemical modelling: per-paper setup values

Every row comes from the evidence pack's "Key parameters", "Assumptions" and excerpt lines for this
technique (one row from a methods card of a pack paper, marked "card"). Blank cells mean the pack does not
state the value for that paper.

## Hot cores, hot corinos and complex organics

| Bibcode | Code | Physical history | Cosmic-ray rate (s^-1) | Other fixed inputs | Compared quantity |
|---|---|---|---|---|---|
| 2014Sci...345.1584B | MAGICKAL | free-fall collapse nH 3000 to 2e8 cm^-3, static warm-up to 400 K | | radical-site bias toward secondary carbon; other rates and binding energies identical between isomers | i/n propyl cyanide, model peak T vs Trot |
| 2016A&A...587A..92M | MAGICKAL | collapse then warm-up 8 to 400 K, nH 2e8 | | min dust T 8 K; S 8e-8; E_b CH3SH 5534 K, C2H5SH 6230 K | CH3SH/C2H5SH ratio |
| 2017A&A...601A..48G | MAGICKAL (three-phase) | free-fall collapse, warm-up 8 to 400 K at three timescales | 1.3e-17 | nH 2e8 post-collapse; 0.1 um grains | i/n ratios, ice abundances |
| 2017A&A...601A..49B | MAGICKAL | cold collapse then warm-up 8 to 400 K, intermediate timescale | | nH 2e8; min dust T 8 K; E_b CH3NCO 3575 K, CH3NHCHO 6281 K | ratios to HNCO |
| 2019A&A...628A..10B | MAGICKAL | cold collapse, warm-up to 200 K in 5e4, 2e5 or 1e6 yr | 1.3e-17 | E_des CH3NCO 6486 K, N-methylformamide 7386 K | peak gas-phase ratios |
| 2019A&A...628A..27B | MAGICKAL | 18 models per source: 6 CRIR x 3 Tmin | 1.3e-17 to 1.3e-14 | ISRF 1 G0; 1333 species, 13374 reactions | source-to-source abundance pattern |
| 2016ApJ...825...79S | NAUTILUS | collapse plus warm-up, four models A to D (card) | | physical model after the Garrod 2013 fast warm-up (card) | CH2NH abundance |
| 2017MNRAS.469.2230M | UCL_CHEM (three-phase) | nH 5e8 constant, T 10 to 110 K over 1e5 yr | | | CH3NCO abundance; L1544 upper limits |
| 2024ESC.....8..665M | UCLCHEM (two-phase) | Phase I nH 300 to 1e8 at 10 K; Phase II 10 to 300 K at 1e8 | 1.3e-17 | initial Av 2; sticking 1; solar O, C, N, He; Si, S, Cl, Mg, P, F depleted by 100 | peak NH2CN 5.12e-10 at about 3.8e5 yr |
| 2020ApJ...891..164S | gas-grain | cold 1e5 yr (Av 1 to 5), warm-up 5e4 yr to 150 K at 6e6 cm^-3 (Av 100), post-warm-up 1e5 yr | | LMC Z = 1/3, gas-to-dust 300, chi_UV 3 | LMC vs Galactic hot core |
| 2019ESC.....3.2088S | Taquet et al. model | fixed conditions, ices injected at t = 0 | 3e-17 | n_H2 5e7, T 150 K | CH3OCH3/CH3OH, HCOOCH3/CH3OH |
| 2024A&A...691A.180F | UCLCHEM (static grid, 65536 models) | isothermal constant-density cloud, R 0.5 pc | gridded | Av 1 mag at edge; gas-to-dust 100; 12C/13C = 10^1.8; ratios at 1e6 yr | column-density ratios, 50 lowest MSE |

## Cold clouds, prestellar cores and protostellar envelopes

| Bibcode | Code | Setup | Cosmic-ray rate (s^-1) | Other | Compared quantity |
|---|---|---|---|---|---|
| 2024A&A...687A.233M | NAUTILUS | homogeneous gas, density 2.5e4, 10 K gas and dust, Av 10 | 1.3e-17 | | H2NCO upper limit |
| 2024ApJ...968L..19F | three-phase rate equations | 1e5 yr (3e4 and 1e6 yr tested); volatile P 2.57e-7 to 2.57e-9 | 3e-17 | chemical desorption 4% (2 and 8% tested); photodesorption 1e-3 | PH3 limit to volatile P < 5e-9 |
| 2015ApJ...803...70S | gas-grain | constant T 10, 30, 100 K; n 1e4 or 1e6; o/p H2 0.01 and 0.001 | 2.6e-17 | Av 10 | DNC/HNC |
| 2018A&A...617A.120M | analytic steady-state H2D+/DCO+ network + RATRAN | T_sub 20 to 40 K, n_de 1e5 to 1e8, X[CO] 1e-7 to 1e-4 | 1.26e-17 | H2 o/p lower limit 1e-3 | DCO+ radial profile, by eye |
| 2025ApJ...992...55T | network + LIME (LTE) | static collapse-model profiles, 2e5 yr | | | o-H2D+ brightness, qualitative |
| 2019A&A...624L...5P | gas-phase deuteration network | start D2CO/H2CO about 0.01, NH2D/NH3 about 0.3, n 1e5, 150 K | 1e-15 | low extinction | drop of D ratios in 500 to 1000 yr |

## Protoplanetary disks

| Bibcode | Code | Structure | Cosmic-ray rate (s^-1) | Other fixed inputs | Age |
|---|---|---|---|---|---|
| 2016ApJ...831..101B | Du and Bergin + Monte Carlo RT | three-component dust disk; parametrised C and O depletion | about 1e-19 (attenuation 96 g cm^-2) | gas-to-dust 100; size index 3.5; TW Hya UV field for both disks; 8:2 astrosilicate:graphite | 5 Myr (TW Hya), 1 Myr (DM Tau) |
| 2015ApJ...810..112O | gas-grain + LIME | generic T Tauri disk, static | 1e-20 test | CO E_b 1150 K (1000 K tested); CO photodesorption 7e-3 | 300 kyr |
| 2017A&A...599A.101V | reduced network (SciPy odeint) on DALI structure + LIME | TW Hya | 1.2e-17 (1e-19, 5e-17 variants) | CO, N2 E_b 855, 800 K and sticking 0.9, 0.85 (card) | to 1e6 yr |
| 2017ApJ...835..228T | ALCHEMIC + LIME + simobserve | Gorti et al. fiducial, Gaussian surface-density dips | 1.3e-17 | grain radius 7 um | 1 Myr |
| 2018A&A...617A..28S | ALCHEMIC | 1+1D; Mdisk 0.066 Msun, Mdot 5e-9 Msun/yr, alpha 0.01, Rout 800 au, Lx 1e31 erg/s | | 0.1 um grains; gas-to-dust 100; Tgas = Tdust; C/O 0.46, 1.0, 1.2 | 5 Myr |
| 2018ApJ...859..131L | disk chemistry (5970 reactions, 600 species) + RADMC-3D | SED and HD constrained TW Hya model | | d 59.5 pc, PA 155 deg, i 8 deg, M* 0.8 Msun | 1 Myr |
| 2019ApJ...876...72L | NAUTILUS v1.1 (three-phase) | 1+1D parametric; Md 0.18 and 0.03 Msun, Rc 100 au | | 0D cloud initial conditions; S 8e-8; 0.1 um grains; dust-to-mass 0.01; Tgas = Tdust | 1 Myr |
| 2019ApJ...883...98Z | RAC2D | smooth profiles, no substructure | 1.36e-18 (standard), 1.36e-17 (high) | CO 1.4e-4 per H; CO/C18O 570, CO/13CO 69; gas-to-dust 100 | 1 Myr |
| 2019ApJ...875...96N | disk chemical model + modified 1D RATRAN | HD 163296 | | water OPR 3; 16O/18O 560; kappa_mm 1.0 cm2/g scaled x1 to x10 | |
| 2024JKAS...57..163L | PURE-C one-point | n 2.2e10 (inner), 6.0e7 (outer); UV 0; quiescent then burst | 1e-17 | KIDA barriers 2000 K and 1130 K tested | |
| 2024RAA....24g5017M | NAUTILUS + RADMC3D | 1 Myr cloud stage (10 K, nH 2e4, Av 15), then parametrised disk, two-layer gas T | 1.3e-17 | C/O 0.5 to 1.5 | 1e7 yr |
| 2021A&A...651L...6B | literature models | NH 1.6e22 cm^-2 at 60 au from disk model | | | CS/SO, S/H 4.6 to 10.0e-7 |

Disk thermo-chemical models used for structure or gas mass (variant):

| Bibcode | Code | What was varied | Fixed inputs | Fit |
|---|---|---|---|---|
| 2016A&A...585A..58V | DALI | surface density, gas-to-dust, outer radius, cavity radius, delta | Sigma(r) power law with exponential cutoff, gamma 1; gas and dust share the profile | by eye; radii within 5 au, delta within an order of magnitude |
| 2019ApJ...871..107F | DALI | Sigma_c, gamma, R_c, then delta_gap, delta_ring | gaps at 54 to 70 and 87 to 119 au; C, O 1.35e-4, 2.88e-4 | parametric grid; best delta_gap 0.1 |
| 2025ApJ...989....1Z | DALI grid | 13CO, C18O, N2H+ (or C17O) fluxes plus 1.3 mm continuum | kappa 2.3 (nu/230 GHz) cm2/g, Tdust 20 K; xCO 1e-4 for Ophiuchus | grid comparison |

## Envelopes of evolved stars

| Bibcode | Code | Setup | Cosmic-ray rate (s^-1) | Other |
|---|---|---|---|---|
| 2019A&A...629A.146V | gas-phase photochemistry, about 8000 reactions | expansion from 2e14 cm | 1.2e-17 | NH/Av 1.5 times lower than classical; SiS photodissociation set equal to SiO |
| 2017A&A...601A...4A | Meudon PDR code | isotropic expansion from 2e14 cm, Draine field | 1.2e-17 | d 123 pc; C2H2 8e-5, HCN 4e-5 relative to H2 |
| 2015ApJ...814..143A | UMIST + KIDA network | initial radius 2e14 cm; N2 4e-5; clumpy variant | 1.2e-17 | |
| 2018A&A...612L..11S | UCL_CHEM-type CSE model + mcp | spherical, uniform expansion, ISRF only | | Mdot 2.5e-7 Msun/yr, v_exp 2.5 km/s, 12CO/H2 5e-4, 13CO/H2 5e-5 |
| 2021A&A...655A..80D | RATE12 + Al chemistry (Gaussian 16, MESMER) | 1D | | H35Cl/H37Cl 2.4; transition states tuned within 6 kJ/mol |
| 2016A&A...592A..76D | analytic accretion, thermal and photodesorption | n_H 1e8 at about 10 R*; T_b 5000, 10000, 15000 K | | dust-to-gas 0.002; grains 0.005 to 0.25 um; S = 1; solar Cl 3.2e-7 |

## Diffuse and extragalactic gas

| Bibcode | Code | Setup | Notes |
|---|---|---|---|
| 2019A&A...622A..26G | analytic steady state | HOC+/H2O and CF+/HF with Langevin or enhanced capture rates | C+ main carbon carrier and electron source |
| 2017A&A...608A..96L | NAUTILUS gas-phase, nuclear-spin network | nH 2e2 to 2e4, T 10 to 100 K | Av 1 to 3 mag; 0.1 um grains; dust-to-gas 1% |
| 2025A&A...696A..31G | Chempl static and PDR; UCLCHEM C-type shocks | PDR fiducial T 500 K, n 1e3; shock preshock density 1e3 | Tdust = Tgas in static models |

=== EVIDENCE PACK (chemical-modelling) ===
# Evidence pack: Astrochemical modelling compared to ALMA lines (`chemical-modelling`)

Scope: chemical kinetics models compared to observed abundances

Built from 46 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2014-2025.
Matcher (regex over analysis steps): `chemical (?:model|network|code)|nautilus|ucl_chem|uclchem|magickal|astrochem|gas[- ]grain|reaction network`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- astrochemistry: 44
- star_formation: 22
- protoplanetary_disks: 17
- evolved_stars: 6
- milky_way_ism: 5
- nearby_galaxies: 1

### Software named in the matched steps
- magickal: 6
- nautilus: 5
- uclchem: 3
- dali: 3
- ratran: 2
- lime: 2
- alchemic: 2
- monte carlo radiative transfer (dullemond et al. 2002): 1
- du & bergin thermo-chemical code: 1
- pure-c: 1
- chempl: 1
- rate12 chemical model: 1
- gaussian 16: 1
- mesmer: 1
- radmc3d: 1
- ucl_chem-type cse chemical model (mcelroy13): 1
- mcp: 1
- meudon pdr code: 1
- rac2d: 1
- ucl_chem: 1
- vis_sample: 1
- radmc-3d: 1
- scipy odeint: 1

### Fitting methods (most common phrasings)
- Parameters chosen heuristically, no formal fit: 1
- Grid sampled over density, T, zeta, F_UV, initial O and C abundances; ranking by MSE: 1
- By-eye fit of radial profile: 1
- Parametric grid study, no formal fit statistic stated: 1
- By eye; no chi2 or MCMC: 1

### Validation checks used
- Predicted emission matches observations within a factor of 1.5; test with 10x higher gas mass: 1
- Model abundance ratios compared with observed ratios: 1
- Compared fall-off radii with observations and RT results: 1
- Compared modelled peak abundance with observed abundance and with Garrod et al. 2022: 1
- Compared with observed ratios; tested high (KIDA) barriers, UV and CR variations: 1
- Test with gas-to-dust ~3000 at low and high density: 1
- Consistency with DCO+ results of VLA 1623 in Murillo et al. 2015 and with line-ratio temperatures: 1
- Small parameter study of binding energy, density/temperature structure, and cosmic ionization rate: 1
- Compared with observed abundances and HCN/HNC abundances from Behrens et al. 2024: 1
- Transition state heights adjusted within 6 kJ/mol to match observations: 1
- Compared model peak temperatures with observed rotation temperature and abundance ratios: 1
- Models without gas gaps cannot reproduce the C18O profile: 1
- Modeled peak abundance ratios compared with observed column density ratios: 1
- Compared qualitatively with ALMA detection of NaCl at 1.22'': 1
- Conclusion holds for 3e4 yr and 1e6 yr; desorption probability 2% and 8% tested: 1
- Compared column densities to Le Gal et al. 2021 LTE values and upper limits: 1
- Qualitative only; absolute intensities not matched: 1
- Small model grid with different cavity radii and delta values; uncertainty within 5 AU and an order of magnitude: 1
- Compared model ice abundances and i:n ratio with observations; tested high CN-addition barriers: 1
- CO(2-1,3-2,4-3) JCMT lines reasonably reproduced: 1
- Model column densities, temperatures and profiles compared with observations: 1
- Compared to observed radial brightness: 1
- Model CO snowline locations compared with literature: 1
- Modeling uncertainties of factor ~3-10 considered: 1
- Compared model CH3OCH3/CH3OH and HCOOCH3/CH3OH ratios with N113 observations: 1
- Compared with observed abundances and L1544 upper limits: 1
- Model-derived NT, Trot compared to observed within errors: 1
- Compared with analytic OPR0 model: 1
- Steady state checked time-dependently: 1

### Key parameters and settings (bibcode: value)
- 2016ApJ...831..101B: Gas-to-dust mass ratio 100; dust size distribution power law exponent 3.5; cosmic ray rate ~1e-19 s^-1; models sampled at 5 Myr (TW Hya) and 1 Myr (DM Tau)
- 2017A&A...601A..49B: nH = 2e8 cm-3, 8 K minimum dust temperature, intermediate warm-up timescale
- 2019A&A...629A.146V: cosmic-ray ionisation rate 1.2e-17 s-1; NH/Av 1.5 times lower than classical; initial radius 2e14 cm
- 2024ESC.....8..665M: Phase I: nH 300 to 1e8 cm^-3 at 10 K; Phase II: 10 to 300 K at 1e8 cm^-3; CR rate 1.3e-17 s^-1; initial Av = 2
- 2024JKAS...57..163L: n=2.2e10 (inner), 6.0e7 cm-3 (outer); CR 1e-17 s-1 fiducial
- 2024A&A...691A.180F: R=0.5 pc, Av=1 mag, gas-to-dust 100, 12C/13C=10^1.8
- 2018A&A...617A.120M: T_sub = 20–40 K, n_de = 1e5–1e8 cm-3, X[CO] = 1e-7–1e-4
- 2015ApJ...810..112O: CO binding energy 1150 K (1000 K tested); CO photodesorption yield 7e-3; cosmic ray ionization rate lowered to 1e-20 s-1 test
- 2025A&A...696A..31G: PDR fiducial T=500 K, n=10^3 cm-3; shock preshock density 10^3 cm-3
- 2021A&A...655A..80D: H35Cl/H37Cl fixed to 2.4
- 2015ApJ...803...70S: Cosmic-ray ionization rate 2.6e-17 s-1; Av = 10 mag
- 2019ApJ...871..107F: gaps at 54-70 au and 87-119 au, ring at 70-87 au; same delta in both gaps
- 2016A&A...587A..92M: nH = 2e8 cm-3, min dust T 8 K, sulfur abundance 8e-8
- 2016A&A...592A..76D: n_H = 1e8 cm^-3 at ~10 R*, S=1, F_FUV Y_PD = 3e5
- 2024ApJ...968L..19F: Chemical desorption probability 4%; xi = 3e-17 s^-1
- 2019A&A...624L...5P: cosmic ionization rate 1e-15 s-1, low extinction
- 2016A&A...585A..58V: Sigma(r) power law with exponential cutoff, gamma=1
- 2017A&A...601A..48G: n_H = 2e8 cm-3 post-collapse; zeta = 1.3e-17 s-1; 0.1 micron grains
- 2018A&A...612L..11S: mass-loss 2.5e-7 Msun/yr, v_exp 2.5 km/s, 12CO/H2=5e-4, 13CO/H2=5e-5
- 2024A&A...687A.233M: density 2.5e4 cm-3, 10 K, Av 10 mag, zeta 1.3e-17 s-1
- 2019ApJ...876...72L: Disk parameters in Table 3 (e.g. Md=0.18 and 0.03 Msun, Rc=100 au)
- 2019A&A...628A..10B: zeta = 1.3e-17 s-1; warm-up to 200 K in 5e4, 2e5 or 1e6 yr
- 2019ApJ...883...98Z: zeta_CR = 1.36e-18 (standard) and 1.36e-17 s^-1 (high); gamma ±0.2 tests
- 2019A&A...628A..27B: CRIR 1.3e-17 to 1.3e-14 s-1; ISRF 1 G0
- 2018A&A...617A..28S: Mdisk 0.066 Msun, Mdot 5e-9 Msun/yr, alpha 0.01, Rout 800 au, Lx 1e31 erg/s, grain 0.1 um
- 2019ESC.....3.2088S: n_H2 = 5e7 cm-3, T=150 K, zeta = 3e-17 s-1
- 2019ApJ...875...96N: OPR=3, 16O/18O=560, kappa_mm original 1.0 cm2/g
- 2017MNRAS.469.2230M: nH 5e8 cm-3, T 10 to 110 K over 1e5 yr
- 2017A&A...599A.101V: zeta = 1.2e-17 s-1 fiducial; 1e-19 and 5e-17 variants
- 2017ApJ...835..228T: CRP ionization 1.3e-17 s^-1; grain radius 7 µm


### Assumptions (bibcode: value)
- 2016ApJ...831..101B: Same TW Hya UV field used for both systems; 8:2 astrosilicate:graphite
- 2017A&A...601A..49B: Binding energies 3575 K (CH3NCO) and 6281 K (CH3NHCHO) estimated
- 2019A&A...629A.146V: SiS photo-dissociation rate assumed equal to SiO
- 2024ESC.....8..665M: Sticking probability unity; solar abundances for O, C, N, He (Asplund 2009); Si, S, Cl, Mg, P, F depleted by 100
- 2024JKAS...57..163L: UV fully shielded in midplane; CR uniform; burst only affects temperature
- 2024A&A...691A.180F: Isothermal constant-density static cloud
- 2018A&A...617A.120M: cosmic-ray ionization rate 1.26e-17 s-1; ortho-to-para H2 lower limit 1e-3; sources centred on and dominated by A
- 2020ApJ...891..164S: LMC: Z=1/3, gas-to-dust 300, chi_uv=3
- 2015ApJ...810..112O: CO and HCO+ densities scaled by 500 and 70 for C18O and H13CO+ (ISM 16O/18O, 12C/13C)
- 2025A&A...696A..31G: Dust temperature equal to gas temperature in static models
- 2014Sci...345.1584B: Radical-site bias favoring secondary carbon; other rates and binding energies identical between isomers
- 2021A&A...651L...6B: NH = 1.6e22 cm-2 at 60 au from disk model
- 2019A&A...622A..26G: C+ main carbon carrier and electron source
- 2019ApJ...871..107F: Small grain surface density follows large grains; elemental C and O abundances 1.35e-4 and 2.88e-4
- 2016A&A...587A..92M: CH3SH binding energy same as methanol (5534 K); C2H5SH 6230 K
- 2016A&A...592A..76D: Dust-to-gas mass ratio 0.002; grain sizes 0.005-0.25 micron; solar Cl abundance 3.2e-7
- 2024ApJ...968L..19F: Photodesorption yield 1e-3 per UV photon for P species
- 2024RAA....24g5017M: Cloud stage: T=10 K, nH=2e4 cm-3, Av=15, zeta=1.3e-17 s-1
- 2025ApJ...992...55T: static physical structure at each radius, 2e5 yr
- 2016A&A...585A..58V: Gas and dust follow same density profile with varying gas-to-dust ratio
- 2017A&A...601A..48G: Canonical cosmic-ray ionization rate 1.3e-17 s-1
- 2018A&A...612L..11S: Spherical uniformly expanding envelope, ISRF only external UV
- 2025ApJ...989....1Z: kappa = 2.3 (nu/230 GHz) cm2/g, Tdust = 20 K; ISM xCO=1e-4 for Ophiuchus
- 2019ApJ...876...72L: Dust temperature equals gas temperature; dust-to-mass ratio 0.01; 0.1 micron grains; low S abundance 8e-8
- 2019A&A...628A..10B: E_des(CH3NCO)=6486 K, N-methylformamide 7386 K
- 2017A&A...601A...4A: Distance 123 pc; C2H2 and HCN abundances 8e-5 and 4e-5 relative to H2
- 2019ApJ...883...98Z: Initial CO abundance 1.4e-4 relative to H; CO/C18O=570, CO/13CO=69; no isotopologue fractionation
- 2018A&A...617A..28S: Equal gas and dust temperatures; gas-to-dust 100
- 2018ApJ...859..131L: Distance 59.5 pc, PA 155 deg, inclination 8 deg, M*=0.8 Msun
- 2017A&A...608A..96L: One to three magnitudes of visual extinction; dust grain radius 0.1 micron; dust-to-gas 1%


### Limitations the authors admit
- 2016ApJ...831..101B: Depletion parameterization is somewhat arbitrary; DM Tau inner hole not modelled; outer ring sharpness not matched
- 2017A&A...601A..49B: Only five clean lines, so detection tentative
- 2017A&A...601A..49B: Models overproduce NH2CHO and CH3CONH2 by more than an order of magnitude
- 2019A&A...629A.146V: Model based on single line for SiO and CS, two for SiS; degeneracy between density and abundance
- 2024ESC.....8..665M: Coarse resolution; morphology cannot be determined
- 2024JKAS...57..163L: Simple one-point model; no 2D ring structure or absolute column densities; lines may be optically thick
- 2024A&A...691A.180F: Tex fixed to CH3OH value for all species; N_tot uncertain up to factor 2
- 2024A&A...691A.180F: Static models cannot reproduce all ratios; dynamical models needed
- 2018A&A...617A.120M: Simple chemical model cannot explain inner DCO+ 5-4 emission; single physical profile adopted
- 2020ApJ...891..164S: Infall not detected because no optically thick tracer; NH2 includes low-temperature components
- 2020ApJ...898...54T: Low velocity resolution (3 km/s) hindered line identification and Gaussian fitting; CH3CN optical thickness cannot be ruled out
- 2015ApJ...810..112O: Model is not tuned to IM Lup, so no quantitative comparison is possible
- 2015ApJ...810..112O: Outer-ring intensity is model dependent and may vary from disk to disk
- 2025A&A...696A..31G: Gas temperatures poorly constrained by HCNH+; large-scale emission filtered; beam dilution neglected
- 2021A&A...655A..80D: 1D model cannot account for 3D asymmetry; true uncertainties much larger than formal ones
- 2014Sci...345.1584B: Preliminary LTE model not fully optimized for ALMA; abundance uncertainties exclude free-free contamination and dust property uncertainties
- 2021A&A...651L...6B: Column densities inversely proportional to assumed emitting area, so may be lower limits
- 2015ApJ...803...70S: Higher resolution observations needed for the hot core
- 2019A&A...622A..26G: CF+ and C3H+ lines are weak and contaminated; Galactic center abundances cannot be determined absolutely
- 2015ApJ...814..143A: Smooth spherical shell model does not reproduce fine structure; infrared pumping only partly included
- 2019ApJ...871..107F: Model does not fully reproduce observations because of 2D temperature structure uncertainties
- 2019ApJ...871..107F: Insufficient sensitivity to see the co-rotation bump
- 2016A&A...587A..92M: Model not accurate enough, particularly for CH3SH, to support or dismiss the Orion KL ethanethiol detection
- 2016A&A...592A..76D: Only 16-20 antennas; cannot prove either scenario
- 2024ApJ...968L..19F: Collisional rate coefficients for PH3-H2 unavailable; extended continuum emission resolved out may explain lower N(H2)
- 2024RAA....24g5017M: Cannot determine best-fit C/O due to observational limitations
- 2025ApJ...992...55T: MC 35-mm detection marginal; model absolute intensities not matched
- 2020A&A...644A..84M: Tex-Ntot degeneracy for AA gives a factor ~2 uncertainty on Ntot
- 2020A&A...644A..84M: Some MF transitions under-reproduced; unidentified blends possible
- 2021ApJ...908..108F: Model does not reproduce C18O self-absorption at the protostar
- 2017A&A...601A..48G: Cosmic-ray ionization rate poorly constrained; full sensitivity study left for future
- 2018A&A...612L..11S: Single-dish data cannot constrain the complex outflow; the CSE model is crude
- 2025ApJ...989....1Z: Medians are of survivors; survival bias not accounted in medians; absolute ages model-dependent; regions assumed to share initial conditions
- 2019ApJ...876...72L: Low resolution and S/N cannot distinguish optically thick CS from isotopic enhancement or beam dilution; LTE and filling factor assumptions uncertain
- 2019ApJ...876...72L: Models simplistic: no X-rays, grain growth, LkCa 15 inner cavity; not tuned
- 2019A&A...628A..10B: Line-continuum splitting is preliminary with unexplained baseline artifacts
- 2017A&A...601A...4A: Spherical isotropic model cannot reproduce arcs; comparison only first order; IR pumping uncertain for C4H, C6H, C3N
- 2019ApJ...883...98Z: Small-scale substructures ignored; smooth density profiles used
- 2019ApJ...883...98Z: Gas-to-dust ratio fixed at 100; gas mass uncertainty considered not crucial
- 2019A&A...628A..27B: Ages unreliable because the same accretion history is assumed for all sources; no CR attenuation.
- 2018A&A...617A..28S: C/O cannot be constrained more accurately due to non-detections and poorly known available sulfur
- 2019ESC.....3.2088S: N159W-S ALMA analysis is preliminary, so no physical parameters given
- 2019ApJ...875...96N: Observation time was ~20% of the requested time, insufficient to test the model
- 2017MNRAS.469.2230M: H2 column is a lower limit, so abundances are upper limits as dust may be optically thick
- 2017MNRAS.469.2230M: NH2CHO underproduced by model by factor 10
- 2018ApJ...859..131L: Limited spatial resolution prevents robust quantitative comparison of gas-phase vs grain-surface contributions
- 2017A&A...608A..96L: A more efficient thermalization route may be missed.
- 2017A&A...599A.101V: Model underpredicts emission beyond ~60 AU; gas-phase formation of CO and N2 ignored
- 2016ApJ...825...79S: Large error in G31.41+0.3 abundance due to scatter in rotation diagram
- 2017ApJ...835..228T: Models do not fully reproduce observed profiles; fiducial model was fit to integrated intensities
- 2018A&A...620L...1G: Flaring index of the relevant layer is unknown, making quantitative estimates challenging

### Settings cards flag as needed but not stated
- continuum subtraction and line-free channels: 4
- casa version: 4
- line-free channels for continuum subtraction: 4
- self-calibration solution intervals and number of rounds: 2
- line-free channels used for continuum subtraction: 2
- line-free channels and continuum subtraction details: 2
- self-calibration solution intervals: 2
- line-free channels / continuum subtraction method: 1
- image size, cell size, clean threshold, masks: 1
- details of stacking and ring-fitting for position angle and inclination: 1
- chemical network and reaction rate details of the du & bergin model: 1
- exact criteria for the 'best-fit' models (no fitting algorithm): 1
- coordinates of targets: 1
- imaging and calibration parameters (casa version, weighting, spectral extraction position/aperture)…: 1
- coordinates and distance of sgr b2(n2) not given here: 1
- details of the full lte model of all other molecules needed to remove contamination: 1
- uncertainties on lte column densities not tabulated: 1
- network files for magickal not provided: 1
- continuum-free/line-free channels and continuum subtraction method: 1
- cell size, image size, clean masks and iteration thresholds: 1
- exact azimuthal-average procedure and fit goodness criterion for abundance profiles: 1
- abundance profile values as a function of radius (only in figure): 1
- details of the uvshort merging scaling: 1
- spectral window assignments per track and time on source: 1
- radiative transfer code is not named or released: 1
- line-free channels for continuum and uvcontsub: 1
- tclean robust, cell size, image size, masking, threshold: 1
- self-calibration solints and number of iterations: 1
- spectral window frequency/channel details and rest frequency for velocity: 1
- uclchem version, warm-up timescale and exponent n, initial abundances, dust/grain parameters: 1
- whether the 250±25 k or 250±35 k uncertainty is correct (text is inconsistent): 1
- how lte line widths and velocity were fixed or fitted in cassis: 1
- casa version and calibration/imaging details (deferred to lee et al. 2024a): 1
- moment-0 integration velocity range and masking: 1
- pure-c code availability and exact reduced network file: 1
- method for deriving the 1.6±0.6 ratio (aperture, peak pixel, uncertainty): 1
- dust/gas temperature and grain parameters in chemical model: 1
- clean parameters in gildas (iterations, threshold, masks, pixel size, image size): 1
- continuum-free channels and continuum subtraction method: 1
- spectral line extraction regions definition (regions 1-7 are drawn roughly by eye): 1

## Paper excerpts (40 of 46, chosen for detail and spread over fields/years)

### 2016ApJ...831..101B: Hydrocarbon Emission Rings in Protoplanetary Disks Induced by Dust Evolution (2016; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: Why do C2H (and c-C3H2) emission rings appear at the edge of the mm-dust (pebble) disk in TW Hya and DM Tau, and what physical/chemical conditions (UV field, C/O) are needed to produce them?
- step 4: Thermo-chemical modelling of rings
  - method: Three-component dust disk models (inner, sub-mm, UV-dominated), uniform C/O tests, then parametrized C and O depletion; compare simulated N=4-3 emission to observations [5.1 Source Specific Models: "The “best-fit” emission images of for both disks are shown in Fig. [9](#fig:best)."]
  - software: Du & Bergin thermo-chemical code, Monte Carlo radiative transfer (Dullemond et al. 2002)
  - parameter: Gas-to-dust mass ratio 100; dust size distribution power law exponent 3.5; cosmic ray rate ~1e-19 s^-1; models sampled at 5 Myr (TW Hya) and 1 Myr (DM Tau) [Physical and Chemical Models: "Thus we have run our models with a rate that is reduced compared to the interstellar medium by two orders of magnitude ($\sim 10^{-19}$ s$^{-1}$, with an attenuation parameter of 96 g/cm$^2$)."]
  - assumption: Same TW Hya UV field used for both systems; 8:2 astrosilicate:graphite [4 Physical and Chemical Models: "we use the TW Hya radiation field for both systems"]
  - fitting: Parameters chosen heuristically, no formal fit [Appendix A: "The parameters are chosen heuristically for each disk to investigate what C and O distribution best reproduce the observed C$_2$H observations."]
  - validation: Predicted emission matches observations within a factor of 1.5; test with 10x higher gas mass [5.1.1 TW Hya: "the predicted emission distribution shown in Fig. [9](#fig:best) matches observations within a factor of 1.5."]
- limitation (authors): Depletion parameterization is somewhat arbitrary; DM Tau inner hole not modelled; outer ring sharpness not matched [5.1 Source Specific Models: "This parameterization is somewhat arbitrary"]
- not stated (card): Line-free channels / continuum subtraction method; Self-calibration solution intervals and number of rounds; Image size, cell size, clean threshold, masks; Details of stacking and ring-fitting for position angle and inclination; Chemical network and reaction rate details of the Du & Bergin model; Exact criteria for the 'best-fit' models (no fitting algorithm); Coordinates of targets

### 2017A&A...601A..49B: Rotational spectroscopy, tentative interstellar detection, and chemical modeling of N-methylformamide (2017; astrochemistry, star_formation; observational_alma_primary)
- question: Can improved laboratory rotational spectroscopy of trans N-methylformamide enable its detection toward Sgr B2(N2) in the ALMA EMoCA survey, and how can its abundance relative to related molecules be explained by chemical modelling?
- step 6: Chemical kinetics modelling
  - method: MAGICKAL gas-grain model with cold collapse then warm-up 8-400 K, varying activation energies of NH + CO and H + CH3NCO [5 Chemical modelling: "we use the chemical kinetics model *MAGICKAL* (Garrod 2013) with an expanded gas-grain chemical network."]
  - software: MAGICKAL
  - parameter: nH = 2e8 cm-3, 8 K minimum dust temperature, intermediate warm-up timescale [5 Chemical modelling: "we use the intermediate warm-up timescale, which generally produces the best match between models and observed abundances"]
  - assumption: Binding energies 3575 K (CH3NCO) and 6281 K (CH3NHCHO) estimated [5 Chemical modelling: "Binding energy values for CH$_3$NCO and CH$_3$NHCHO are 3575 K and 6281 K, respectively"]
  - validation: Model abundance ratios compared with observed ratios [5.1 Model results: "Table [\[RTG-tab5\]](#RTG-tab5) shows ratios of the abundances of the main molecules with that of HNCO"]
- limitation (authors): Only five clean lines, so detection tentative [4.2 Tentative detection of N-methylform…: "Given the small number of clearly detected lines, we consider our detection of CH$_3$NHCHO as tentative rather than secure."]
- limitation (authors): Models overproduce NH2CHO and CH3CONH2 by more than an order of magnitude [5.1 Model results: "all four models produce an overabundance of NH$_2$CHO and CH$_3$CONH$_2$ by more than an order of magnitude"]
- not stated (card): Imaging and calibration parameters (CASA version, weighting, spectral extraction position/aperture) not given; only in Belloche et al. 2016; Coordinates and distance of Sgr B2(N2) not given here; Details of the full LTE model of all other molecules needed to remove contamination; Uncertainties on LTE column densities not tabulated; Network files for MAGICKAL not provided

### 2019A&A...629A.146V: IRC + 10°216 mass loss properties through the study of λ3 mm emission. Large spatial scale distribution of SiO, SiS, and CS (2019; evolved_stars, astrochemistry; observational_alma_primary)
- question: What are the large-scale spatial distribution and radial abundance profiles of SiO, SiS and CS in the envelope of IRC+10216, and what do they say about its mass-loss history and photo-dissociation?
- step 4: Chemical model of photo-dissociation
  - method: Gas-phase photo-induced chemistry network (~8000 reactions) with parent abundances updated from step 3 [Chemistry: "The chemical network encompasses about 8 000 gas-phase, photo-induced, and cosmic-ray reactions"]
  - parameter: cosmic-ray ionisation rate 1.2e-17 s-1; NH/Av 1.5 times lower than classical; initial radius 2e14 cm [Chemistry: "The adopted cosmic-ray ionisation rate of H$_2$ is 1.2$\times$10$^{-17}$ s$^{-1}$ (cite: agu06)."]
  - assumption: SiS photo-dissociation rate assumed equal to SiO [Chemistry: "In the case of SiS, there are no estimates of its photo-dissociation rate, thus as an educated guess, we assumed the same value than that of SiO."]
  - validation: Compared fall-off radii with observations and RT results [Chemistry: "these predictions are on average below a factor of 1.5, being the fall-off distances of the chemical models larger than the observational measurements"]
- limitation (authors): Model based on single line for SiO and CS, two for SiS; degeneracy between density and abundance [Radiative transfer modelling: "our study is based solely on the analysis of just a single line in the cases of SiO and CS, and two lines in the case of SiS"]
- not stated (card): Continuum-free/line-free channels and continuum subtraction method; Cell size, image size, clean masks and iteration thresholds; Exact azimuthal-average procedure and fit goodness criterion for abundance profiles; Abundance profile values as a function of radius (only in figure); Details of the UVSHORT merging scaling; Spectral window assignments per track and time on source; Radiative transfer c…

### 2024ESC.....8..665M: Detection and Chemical Modeling of Complex Prebiotic Molecule Cyanamide in the Hot Molecular Core G31.41 + 0.31 (2024; astrochemistry, star_formation; archival_reuse)
- question: Is cyanamide (NH2CN) present in the hot molecular core G31.41+0.31, what are its column density and abundance, and how is it formed (grain-surface NH2 + CN)?
- step 6: chemical modelling
  - method: Two-phase warm-up model with UCLCHEM with added NH2 + CN grain reaction [4.3 New chemical modelling: "We computed a two-phase warm-up chemical model to determine the abundance and possible formation mechanisms of ."]
  - software: UCLCHEM
  - parameter: Phase I: nH 300 to 1e8 cm^-3 at 10 K; Phase II: 10 to 300 K at 1e8 cm^-3; CR rate 1.3e-17 s^-1; initial Av = 2 [4.3 New chemical modelling: "the temperature raised from 10 to 300 K with a constant gas density of 1$\times$10$^{8}$ cm$^{-3}$"]
  - assumption: Sticking probability unity; solar abundances for O, C, N, He (Asplund 2009); Si, S, Cl, Mg, P, F depleted by 100 [4.3 New chemical modelling: "we assumed the sticking probability to be unity"]
  - validation: Compared modelled peak abundance with observed abundance and with Garrod et al. 2022 [4.4 Comparision between observed and mo…: "This result indicates that the estimated abundance of towards the G31.41+0.31 is nearly similar to the modelled abundance of ."]
- result: Modelled peak NH2CN abundance = 5.12e-10 ± not stated dimensionless [4.3 New chemical modelling: "The maximum modelled abundance of NH$_{2}$CN reaches 5.12$\times$10$^{-10}$ on the grain at the time of $\sim$3.8$\times$10$^{5}$ yr"]
- limitation (authors): Coarse resolution; morphology cannot be determined [3.3 Spatial distribution: "Therefore, understanding the morphology of NH$_{2}$CN from the spatial distribution maps towards G31.41+0.31 is not possible."]
- not stated (card): Line-free channels for continuum and uvcontsub; tclean robust, cell size, image size, masking, threshold; Self-calibration solints and number of iterations; Spectral window frequency/channel details and rest frequency for velocity; UCLCHEM version, warm-up timescale and exponent n, initial abundances, dust/grain parameters; Whether the 250±25 K or 250±35 K uncertainty is correct (text is inconsis…

### 2024JKAS...57..163L: HCN and HNC in the Disk of an Outbursting Young Star, V883 Ori (2024; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: Can a one-point chemical model of the disk midplane reproduce the observed HCN/HNC abundance ratio in the inner and outer rings of V883 Ori, and what controls it?
- step 4: Run one-point chemical model for inner and outer ring
  - method: Time-dependent chemistry at fixed density, temperature, CR, UV=0, quiescent then burst phase; vary barriers, UV and CR [3.1 Chemistry: "The subroutine for chemical calculations can solve the chemical evolution in a specific physical condition of the density and temperature of gas and dust, cosmic ionization rate, and UV flux."]
  - software: PURE-C
  - parameter: n=2.2e10 (inner), 6.0e7 cm-3 (outer); CR 1e-17 s-1 fiducial [3.2 Physical conditions: "$2.2\times 10^{10}$ cm$^{-3}$ and $6.0\times 10^7$ cm$^{-3}$, respectively"]
  - assumption: UV fully shielded in midplane; CR uniform; burst only affects temperature [3.2 Physical conditions: "We assume that the accretion burst only affects the disk temperature, without altering the density structure."]
  - validation: Compared with observed ratios; tested high (KIDA) barriers, UV and CR variations [5.1 Effect of barrier energies in react…: "The barrier energies from KIDA (cite: Wakelam2012), which are 2000 K for [\[reacH\]](#reacH) and 1130 K for [\[reacO\]](#reacO), were tested."]
- result: Modeled HCN/HNC ratio, outer ring = ~2 ± not stated dimensionless [4.1 Abundances: "the HCN/HNC abundance ratio remains at the low level of $\sim$2"]
- limitation (authors): Simple one-point model; no 2D ring structure or absolute column densities; lines may be optically thick [3 Model: "We do not intend to reproduce the 2D ring structures observed in the HCN and HNC emission or the absolute column densities of the molecules."]
- not stated (card): CASA version and calibration/imaging details (deferred to Lee et al. 2024a); Moment-0 integration velocity range and masking; Continuum subtraction and line-free channels; PURE-C code availability and exact reduced network file; Method for deriving the 1.6±0.6 ratio (aperture, peak pixel, uncertainty); Dust/gas temperature and grain parameters in chemical model

### 2024A&A...691A.180F: CHEMOUT: CHEMical complexity in star-forming regions of the OUTer Galaxy: IV. ALMA observations of organic species at a galactocentric radius of 23 kpc (2024; star_formation, astrochemistry, milky_way_ism; observational_alma_primary)
- question: What are the spatially resolved molecular emission and abundances of organics in the outer-Galaxy star-forming region WB670 at R_GC 23.4 kpc, and do chemical models reproduce them?
- step 5: Chemical modelling comparison
  - method: UCLCHEM static grid of 65536 models; compare column density ratios at 1e6 yr; select 50 lowest-MSE models [5.4 Chemical modelling: "the 50 models with the lowest Mean Squared Error (MSE) are chosen."]
  - software: UCLCHEM
  - parameter: R=0.5 pc, Av=1 mag, gas-to-dust 100, 12C/13C=10^1.8 [5.4 Chemical modelling: "Each of the models is ran with an edge visual extinction of $A_v=1.0$ mag, and molecular ratios are computed at $10^6$ years."]
  - assumption: Isothermal constant-density static cloud [5.4 Chemical modelling: "We considered a "static model", namely an isothermal cloud at constant density with a radius of $R=0.5$ pc"]
  - fitting: Grid sampled over density, T, zeta, F_UV, initial O and C abundances; ranking by MSE [Table: "| Density $n_\mathrm{H}\;(\mathrm{cm}^{-3})$ | $1 \times 10^3$ | $1 \times 10^7$ | log |"]
  - validation: Test with gas-to-dust ~3000 at low and high density [5.4 Chemical modelling: "In the low density case, the results do not show any significant differences."]
- result: Best-model temperature range = 20-45 ± not stated K [5.4 Chemical modelling: "temperatures from 20 to 45 K, radiation fields lower than 5 Habing"]
- limitation (authors): Tex fixed to CH3OH value for all species; N_tot uncertain up to factor 2 [4.2: "$N_{\rm tot}$ can vary up to a factor 2 depending on the species."]
- limitation (authors): Static models cannot reproduce all ratios; dynamical models needed [5.4 Chemical modelling: "Overall, it is very unlikely to find a model that fits all ratios well."]
- not stated (card): Clean parameters in GILDAS (iterations, threshold, masks, pixel size, image size); Continuum-free channels and continuum subtraction method; Spectral line extraction regions definition (regions 1-7 are drawn roughly by eye); Exact beam sizes per band; Which spws used for continuum and total bandwidth; UCLCHEM version, network and initial conditions beyond the table; Details of MSE ratio computati…

### 2018A&A...617A.120M: Tracing the cold and warm physico-chemical structure of deeply embedded protostars: IRAS 16293-2422 vs. VLA 1623-2417 (2018; star_formation, astrochemistry; observational_alma_primary)
- question: What factors determine the cold and warm chemical structure of two Class 0 protostars, IRAS 16293-2422 and VLA 1623-2417, as seen in key molecular tracers?
- step 2: Model DCO+ peak position with chemical network
  - method: Steady-state analytic H2D+/DCO+ network with CO freeze-out drop abundance, passed through RATRAN to synthetic cubes, temperature/density profiles scaled by arbitrary factors [4.1.1: "a simple steady-state, analytic chemical network that accounts for the basic reactions leading to the production and destruction of is used."]
  - software: RATRAN
  - parameter: T_sub = 20–40 K, n_de = 1e5–1e8 cm-3, X[CO] = 1e-7–1e-4 [4.1.1: "we explore the parameter ranges of $T_{\rm sub}$ = 20–40 K, $n_{\rm de}$ = 10$^{5}$–10$^{8}$ cm$^{-3}$ and $X[\ce{CO}]$ = 10$^{-7}$ – 10$^{-4}$."]
  - assumption: cosmic-ray ionization rate 1.26e-17 s-1; ortho-to-para H2 lower limit 1e-3; sources centred on and dominated by A [4.1.1: "The ortho-to-para ratio is set to have a lower limit of 10$^{-3}$ at low temperatures"]
  - fitting: By-eye fit of radial profile [4.1.1: "A by eye fit of the chemical model to the observations is used to constrain the decrease in the temperature profile"]
  - validation: Consistency with DCO+ results of VLA 1623 in Murillo et al. 2015 and with line-ratio temperatures [4.1.2: "This temperature is consistent with the chemical modelling of the peak position."]
- result: Temperature reduction factor, VLA 1623 = 1.5 ± 0.2 dimensionless [4.1.1: "The factor is constrained to be 1.5+/-0.2 for VLA 1623 and 3.0+/-0.2 for IRAS 16293."]
- result: Temperature reduction factor, IRAS 16293 = 3.0 ± 0.2 dimensionless [4.1.1: "The factor is constrained to be 1.5+/-0.2 for VLA 1623 and 3.0+/-0.2 for IRAS 16293."]
- limitation (authors): Simple chemical model cannot explain inner DCO+ 5-4 emission; single physical profile adopted [4.1.1: "our simple chemical model cannot fully explain the inner part of the 5–4 emission"]
- not stated (card): CASA version and calibration/imaging details for VLA 1623 Cycle 0 and Cycle 2 data; Weighting, robust, cell and image size, and CLEAN parameters; Continuum subtraction method and line-free channels; Moment-map integration velocity ranges and masks; Exact RADEX grid ranges and how uncertainties on temperature were derived; Details of by-eye model fitting, including the chemical network settings (i…

### 2020ApJ...891..164S: Chemistry and Physics of a Low-metallicity Hot Core in the Large Magellanic Cloud (2020; astrochemistry, star_formation; observational_alma_primary)
- question: What are the chemical composition, physical structure and sulfur isotope ratios of a newly discovered hot molecular core around the high-mass YSO ST16 in the LMC, and how do its abundances compare with other LMC and Galactic hot cores?
- step 7: Astrochemical simulations
  - method: Gas-grain model with cold (1e5 yr, AV 1-5 mag), warm-up (5e4 yr, to 150 K, 6e6 cm-3, AV 100) and post-warm-up (1e5 yr) stages; LMC vs Galactic [Appendix: "The warm-up stage continues up to $t_h = 5 \times 10^4$ years in our model."]
  - assumption: LMC: Z=1/3, gas-to-dust 300, chi_uv=3 [Table 10: "Gas to dust ratio | 100 (MW), 300 (LMC)"]
- limitation (authors): Infall not detected because no optically thick tracer; NH2 includes low-temperature components [5.5: "an infall motion is not seen in the present data, because we do not cover a fully optically thick molecular tracer in this work"]
- not stated (card): Line-free channel ranges for continuum and uvcontsub fit order; Image size, cell size, clean threshold, mask, niter; Which calibration pipeline version / manual scripts; Source spectral extraction aperture relative to line-fit method details (Gaussian fit software); Rotation-diagram fitting method and treatment of blends; Details of SED photometry compilation and fitting grid; Chemical network co…

### 2020ApJ...898...54T: Chemical Composition in the IRAS 16562-3959 High-mass Star-forming Region (2020; star_formation, astrochemistry; archival_reuse)
- question: What is the chemical composition of the three cores in the IRAS 16562-3959 G345.5+1.47 MYSO region, how is H2CO formed, and what causes the 33SO ring around the HC HII region?
- step 6: Fractional abundances and comparison with models
  - method: X = N(mol)/N(H2) at Cores B and C; compared with Nautilus model results [4.1 Comparison of the Chemical Composit…: "We derived fractional abundances, $X$(molecules)=$N$(molecules)/$N_{\rm{H}_{2}}$, of each species toward Cores B and C"]
- limitation (authors): Low velocity resolution (3 km/s) hindered line identification and Gaussian fitting; CH3CN optical thickness cannot be ruled out [3.3 Spectra toward the three cores: "Since the velocity resolution of the final spectra of Figure [6](#fig:line1) is low (3 km s$^{-1}$), some lines could not be identified without ambiguity."]
- not stated (card): tclean cell size, image size, niter, threshold, masks; line-free channels used for imcontsub; CASA version and pipeline version; flux calibrator and flux scale uncertainty; velocity range used for moment zero maps; CASSIS MCMC settings (iterations, priors, chain length); Core A free-free-subtracted continuum flux value used in N(H2)

### 2015ApJ...810..112O: Double DCO<SUP>+</SUP> Rings Reveal CO Ice Desorption in the Outer Disk Around IM Lup (2015; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: Where is CO ice desorbed in the IM Lup disk, as traced by the DCO+ emission morphology compared with C18O and H13CO+ and a disk chemistry model?
- step 3: Model disk chemistry and compare to observed profiles
  - method: Time-dependent gas-grain chemistry (300 kyr) on a generic T Tauri disk, LIME line emission, radial profiles compared qualitatively [4.1 Model Description: "integrating a time-dependent system of gas and grain surface rate equations for 300 kyr, assuming the physical structure is static"]
  - software: LIME
  - parameter: CO binding energy 1150 K (1000 K tested); CO photodesorption yield 7e-3; cosmic ray ionization rate lowered to 1e-20 s-1 test [4.1 Model Description: "The CO photodesorption yield is set to $7\times10^{-3}$ (cite: Fayolle13)."]
  - assumption: CO and HCO+ densities scaled by 500 and 70 for C18O and H13CO+ (ISM 16O/18O, 12C/13C) [4.2 Model Results and Comparison to Obs…: "we have scaled the calculated CO and HCO$^+$ densities by factors of 500 and 70, respectively"]
  - validation: Small parameter study of binding energy, density/temperature structure, and cosmic ionization rate [4.1 Model Description: "we performed a small parameter study where we varied the CO binding energy, the disk density and temperature structure, and the cosmic ionization rate."]
- limitation (authors): Model is not tuned to IM Lup, so no quantitative comparison is possible [4.1 Model Description: "The differences in temperature and density structure clearly precludes any quantitative comparison between the model and data."]
- limitation (authors): Outer-ring intensity is model dependent and may vary from disk to disk [Discussion: "the expected intensity of the second DCO$^+$ ring *is* model dependent."]
- not stated (card): Line-free channels used for continuum subtraction; Self-calibration solution intervals and reference SPWs; CLEAN threshold, cell size, image size; Which SPW/channels were used for the continuum image; Integration velocity range and radial bin widths of the profiles; LIME setup (grid, inclination, beam convolution); Model parameters not given (full chemistry network inputs, the small parameter-stu…

### 2025A&A...696A..31G: Shock-induced HCNH<SUP>+</SUP> abundance enhancement in the heart of the starburst galaxy NGC 253 unveiled by ALCHEMI (2025; nearby_galaxies, astrochemistry; archival_reuse)
- question: What are the physical conditions and HCNH+ abundances in the CMZ of NGC 253 from multiple HCNH+ transitions, and what chemistry explains the abundances?
- step 6: astrochemical modeling (static, PDR, shock)
  - method: Chempl static and PDR models; UCLCHEM two-phase C-type shock models, varying T, density, Av, G0, zeta, shock velocity [4.3 Shocks: "we employed the UCLCHEM[^14] code (cite: 2017AJ....154...38H) to run shock models."]
  - software: Chempl, UCLCHEM
  - parameter: PDR fiducial T=500 K, n=10^3 cm-3; shock preshock density 10^3 cm-3 [4.2 PDRs: "we used $T_{\rm k}=$500 K and a gas density of 10$^{3}$ cm$^{-3}$ as our fiducial parameters in the PDR models"]
  - assumption: Dust temperature equal to gas temperature in static models [4.1 Static clouds: "In these models, dust temperatures are assumed to be equal to gas temperatures."]
  - validation: Compared with observed abundances and HCN/HNC abundances from Behrens et al. 2024 [4.3 Shocks: "We also compared the HCN and HNC abundances derived from (cite: 2024ApJ...977...38B) with our shock models."]
- limitation (authors): Gas temperatures poorly constrained by HCNH+; large-scale emission filtered; beam dilution neglected [3.3.2 Non-LTE modeling: "whereas the gas temperatures are less precisely determined"]
- not stated (card): Exact ALCHEMI cube versions and file names, and channel velocity resolution used; Mask expansion sizes in spatial and spectral dimensions; Spectral extraction apertures for the GMC spectra; MCMC prior on line width and how line widths/integrated-intensity ratios enter the likelihood; RADEX background temperature; Chempl/UCLCHEM input parameter grids and run times; Convergence diagnostics for MCMC…

### 2021A&A...655A..80D: ATOMIUM: halide molecules around the S-type AGB star W Aquilae (2021; evolved_stars, astrochemistry; observational_alma_primary)
- question: What are the abundances and spatial distributions of AlCl and AlF around the S-type AGB star W Aql, and of HCl and HF from PACS, and what do they imply for chemistry and F/Cl enrichment?
- step 3: HCl and HF abundances from PACS
  - method: Scale chemical-model radial abundance profile until RT model matches PACS lines without overpredicting non-detections [4.3 Radial distribution of HCl and HF f…: "we find the best fitting model by scaling the radial abundance distribution until the model lines best reproduce the observed data."]
  - software: RATE12 chemical model
  - parameter: H35Cl/H37Cl fixed to 2.4 [5.3.1 HCl: "We also fixed the H$^{35}$Cl/H$^{37}$Cl abundance ratio to 2.4"]
- step 4: Chemistry of AlF and AlCl
  - method: Extend chemical network with Al reactions, rates from G4 and MESMER RRKM calculations, compare rates with expansion rate [6.5 Chemistry of AlCl and AlF: "we extended the Rate12 chemical model by including reactions describing the chemistry of aluminium"]
  - software: Gaussian 16, MESMER
  - validation: Transition state heights adjusted within 6 kJ/mol to match observations [11 Supplementary information: "The rate coefficients for R1 to R6 were adjusted by varying the heights of the transition states within the expected uncertainty of the G4 level of theory (6 kJ mol$^{-1}$)"]
- result: HF abundance upper limit = <=1e-8 ± not stated relative to H2 [5.3.2 HF: "We find an upper limit on the HF abundance of $\leq1\times 10^{-8}$ relative to $\mathrm{H}_2$."]
- limitation (authors): 1D model cannot account for 3D asymmetry; true uncertainties much larger than formal ones [5.4 Model uncertainties: "This means that our actual uncertainties are much larger than the formal uncertainties and cannot easily be quantified."]
- not stated (card): Calibration and combination procedure, CASA version and weighting/robust values; Cell size, image size and continuum subtraction details; Noise levels of the combined cubes; The ALI code is not named or released; Details of the chi-square fitting procedure and grid steps

### 2014Sci...345.1584B: Detection of a branched alkyl molecule in the interstellar medium: iso-propyl cyanide (2014; astrochemistry, star_formation; observational_alma_primary)
- question: Can a branched alkyl molecule (iso-propyl cyanide) be detected in the ISM, and how does its abundance compare with its straight-chain isomer and with chemical model predictions?
- step 7: Simulate hot-core chemistry
  - method: MAGICKAL: free-fall collapse to nH 2e8 cm-3, then static warm-up to 400 K, modified rate equations [Astrochemical numerical simulations: "The first is a free-fall collapse from a total hydrogen density, $n_{\rm H}$, of 3000 to $2 \times 10^8$ cm$^{-3}$."]
  - software: MAGICKAL
  - assumption: Radical-site bias favoring secondary carbon; other rates and binding energies identical between isomers [Astrochemical numerical simulations: "All other rates and binding energies are assumed to be identical between the *i*-PrCN and *n*-PrCN forms."]
  - validation: Compared model peak temperatures with observed rotation temperature and abundance ratios [main text: "This agrees well with the rotation temperatures that we determine from observational data for these molecules."]
- result: Model i-PrCN/n-PrCN peak ratio = 2.2 ± not stated dimensionless [main text: "they show a slight bias toward *i*-PrCN production (2.2:1), rather than the observed bias toward *n*-PrCN (0.4:1)."]
- limitation (authors): Preliminary LTE model not fully optimized for ALMA; abundance uncertainties exclude free-free contamination and dust property uncertainties [Line identification and spectral modeli…: "This model has not been fully optimized for ALMA yet but it is already sufficiently reliable to allow for detecting new molecules in the ALMA spectra."]
- not stated (card): Exact line-free channel ranges used for continuum subtraction; CLEAN parameters (weighting/robust, cell size, image size, masks, threshold); Which spectral line and reference antenna/solint used for self-calibration; Full list and frequencies of i-PrCN and n-PrCN transitions used in population diagrams; Weeds LTE parameters for all other molecules in the preliminary model; Details of free-free co…

### 2021A&A...651L...6B: A major asymmetric ice trap in a planet-forming disk. II. Prominent SO and SO<SUB>2</SUB> pointing to C/O &lt; 1 (2021; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: What S-bearing molecules are present in the Oph-IRS 48 dust-trap disk, what is their origin (ice sublimation vs gas-phase), and what do CS/SO ratios imply for the gas C/O?
- step 5: Volatile S budget and C/O
  - method: Sum SO and SO2 columns divided by NH(60 au) to get S/H; compare CS/SO with chemical models [5.1: "This results in a S/H ratio of 4.6-10.0$\times10^{-7}$"]
  - assumption: NH = 1.6e22 cm-2 at 60 au from disk model [5.1: "The ${N_{\mathrm{H}}}$ column density at 60 au from the IRS 48 disk model is $1.6\times10^{22}$ $\mathrm{cm^{-2}}$"]
- result: S/H from SO and SO2 = 4.6-10.0e-7 ± not stated dimensionless [5.1: "This results in a S/H ratio of 4.6-10.0$\times10^{-7}$"]
- limitation (authors): Column densities inversely proportional to assumed emitting area, so may be lower limits [Analysis: "as the inferred column densities are inversely proportional to the assumed emitting area our results may be a conservative lower limit"]
- not stated (card): CASA version; Line-free channels and continuum subtraction details; Cell size, image size, clean threshold, niter; Which isotopologue/species columns and labels are lost in the text (chemical formulae stripped); Self-calibration status; Partition function and rotational diagram fit details; Exact Keplerian mask width/ parameters; Beam-averaged vs. flux aperture definitions for radial/azimuthal pr…

### 2015ApJ...803...70S: ALMA Observations of the IRDC Clump G34.43+00.24 MM3: DNC/HNC Ratio (2015; star_formation, astrochemistry; observational_alma_primary)
- question: What is the DNC/HNC abundance ratio at high resolution in the IRDC clump G34.43+00.24 MM3, and why does it differ from the single-dish value?
- step 3: Compare with chemical models
  - method: Gas-grain model with constant temperature (10, 30, 100 K), density 1e4 or 1e6 cm-3, and temperature-rise cases; o/p H2 0.01 and 0.001 [4.4 Comparison with Chemical Model Calc…: "We thus calculate models with the initial o/p ratio of 0.01 and 0.001."]
  - parameter: Cosmic-ray ionization rate 2.6e-17 s-1; Av = 10 mag [4.4 Comparison with Chemical Model Calc…: "The cosmic ray ionization rate is set to be 2.6$\times$10$^{-17}$ s$^{-1}$ (van der Tak & van Dishoeck 2000)."]
- limitation (authors): Higher resolution observations needed for the hot core [4.4 Comparison with Chemical Model Calc…: "higher angular resolution observations would be necessary"]
- not stated (card): CASA version and calibration/imaging parameters (task, weighting, robust, cell, size); Continuum subtraction and line-free channels; Integration windows for moment maps and spectra; Excitation/column density formulae and line parameters used; Chemical model initial abundances and full parameters; Band 6 details only in Paper I

### 2019A&A...622A..26G: Molecular ion abundances in the diffuse ISM: CF<SUP>+</SUP>, HCO<SUP>+</SUP>, HOC<SUP>+</SUP>, and C<SUB>3</SUB>H<SUP>+</SUP> (2019; milky_way_ism, astrochemistry; observational_alma_primary)
- question: Can HCO+, HOC+ and CF+ (and C3H+) absorption serve as probes of diffuse molecular hydrogen, and what are their abundances relative to H2 and implications for chemistry?
- step 6: Steady-state chemical model comparison
  - method: Analytic steady-state formulae for HOC+/H2O and CF+/HF with Langevin or enhanced capture rates [Chemistry: "the ratios of the HOC$^+$ and H$_2$O abundances at steady state can be written"]
  - assumption: C+ main carbon carrier and electron source [Chemistry: "We further assume that C$^+$ is the main carrier of carbon and all electrons are provided by C$^+$"]
- limitation (authors): CF+ and C3H+ lines are weak and contaminated; Galactic center abundances cannot be determined absolutely [Summary and conclusions: "Absolute abundances cannot be determined in the central molecular zone because the relative abundances of the usual H$_2$-tracers (CH, HF, etc) have not been established in this region"]
- not stated (card): CASA version and calibration/imaging parameters (weighting, cell, masks); Exact line-free channels / continuum level choice per window; Pixels and weights used for averaged spectra; Herschel HF/H2O/CH spectra reduction and velocity alignment; Uncertainty estimation for column densities and fit errors; Parameter values (x_C, f(H2), T) used in chemical model figures

### 2015ApJ...814..143A: The Peculiar Distribution of CH3CN in IRC +10216 Seen by ALMA (2015; evolved_stars, astrochemistry; observational_alma_primary)
- question: Where is CH3CN distributed in the envelope of IRC +10216 at sub-arcsec resolution, and where is it formed?
- step 4: Compare with standard gas-phase chemical model
  - method: Gas-phase network from UMIST and KIDA; initial radius 2e14 cm; N2 abundance 4e-5; cosmic-ray ionization rate 1.2e-17 s-1; clumpy variant [3 Chemical model: "Here we have constructed a standard chemical model using a gas phase reaction network built up from the databases UMIST and KIDA"]
- result: Chemical model underestimate of CH3CN abundance = > two orders of magnitude ± not stated dimensionless [3 Chemical model: "Our chemical model underestimates the abundance of CH$_3$CN by more than two orders of magnitude"]
- limitation (authors): Smooth spherical shell model does not reproduce fine structure; infrared pumping only partly included [2 Excitation and radiative transfer mod…: "Our model of a smooth hollow spherical shell does not aim at reproducing these fine details"]
- not stated (card): Channel ranges used for continuum subtraction; Clean mask/iteration count, weighting, cell and image size; How 30m and ALMA data were merged in GILDAS; CASA version; Description of the LVG code and fitting procedure for the abundance profile (no goodness-of-fit); Phase center coordinates

### 2019ApJ...871..107F: Gas Density Perturbations Induced by One or More Forming Planets in the AS 209 Protoplanetary Disk as Seen with ALMA (2019; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: Is the gas surface density perturbed in the AS 209 disk gaps, as traced by optically thin C18O and DCO+, consistent with forming planet(s)?
- step 4: Thermochemical modelling of gas gaps
  - method: Grid of DALI models varying Sigma_c,gas, gamma_gas, R_c,gas, then delta_gap and delta_ring; synthetic channel maps convolved with the observed beam, collapsed to moment maps and compared with the radial profiles [Model description: "The data-model comparison is performed in the image plane: DALI creates synthetic channel maps which are then convolved with a Gaussian beam of the same size as the beam of the observations"]
  - software: DALI
  - parameter: gaps at 54-70 au and 87-119 au, ring at 70-87 au; same delta in both gaps [Model description: "\delta_{gap} & \text{for R $\in$ [54\,au, 70\,au] $\&$ [87\,au, 119\,au]}"]
  - assumption: Small grain surface density follows large grains; elemental C and O abundances 1.35e-4 and 2.88e-4 [Model description: "the surface density profile of the small grains population is assumed to follow that of the large grains"] [Footnote 1: "we assumed the following standard elemental abundances of carbon and oxygen of 1.35$\times$10$^{-4}$ and 2.88$\times$10$^{-4}$, respectively."]
  - fitting: Parametric grid study, no formal fit statistic stated [Gas gaps thermochemical Modelling: "we have only performed a simple parametric study of the gas perturbation as described below"]
  - validation: Models without gas gaps cannot reproduce the C18O profile [Modelling results: "Indeed, without gas gaps, our model cannot reproduce the C$^{18}$O profile"]
- result: Gas surface density scaling in gaps = about 0.1-0.2 ± not stated dimensionless [Modelling results: "by applying a scaling factor of about 0.1–0.2 compared to the unperturbed profile"]
- result: Best-fit grid values (gamma_gas, R_c,gas, delta_gap, delta_ring) = 0.2, 120 au, 0.1, 0.4 ± grid step only mixed [Table 2: "| $\delta_{gap}$ | **0.1**, 0.2, 0.3, 0.4 | $\Sigma_{gas}$ scaling factor for the gaps |"]
- result: Isotope-selective photodissociation contribution to C18O in gaps = 10-20% ± not stated % [Modelling results: "contributed to about 10–20$\%$ on the observed C$^{18}$O intensity inside the gaps"]
- limitation (authors): Model does not fully reproduce observations because of 2D temperature structure uncertainties [Modelling results: "our present modelling does not fully reproduce the observations because of uncertainties on the 2D temperature structure"]
- limitation (authors): Insufficient sensitivity to see the co-rotation bump [Comparison with hydrodynamical simulati…: "This feature is not seen in our data because we do not have sufficient sensitivity."]
- not stated (card): Self-calibration solution intervals, number of rounds, and reference models; Line-free channels and continuum subtraction details; CLEAN mask, threshold, cell and image size; Gas-to-dust mass ratio and Sigma_c,gas values for the DALI grid; Statistic used to compare model and data (best values appear chosen by eye); Radial profile bin width and averaging method; Cycle 2 and Cycle 4 data weighting …

### 2016A&A...587A..92M: Exploring molecular complexity with ALMA (EMoCA): Alkanethiols and alkanols in Sagittarius B2(N2) (2016; astrochemistry, star_formation, milky_way_ism; observational_alma_primary)
- question: What are the relative abundances of alkanethiols and alkanols in the hot core Sgr B2(N2), and can a new chemical network with alkanethiol reactions explain them?
- step 3: Astrochemical modelling of alkanethiols
  - method: Gas-grain kinetics with cold collapse then warm-up 8-400 K, new thiol reactions [5 Astrochemical modeling: "using the kinetics model MAGICKAL (cite: 3steps2heaven_2013)"]
  - software: MAGICKAL
  - parameter: nH = 2e8 cm-3, min dust T 8 K, sulfur abundance 8e-8 [5 Astrochemical modeling: "a standard, depleted sulfur abundance of $8 \times 10^{-8}$ is used"]
  - assumption: CH3SH binding energy same as methanol (5534 K); C2H5SH 6230 K [5 Astrochemical modeling: "In the case of C$_2$H$_5$SH, a binding energy of 6230 K is used"]
  - validation: Modeled peak abundance ratios compared with observed column density ratios [5.2 Discussion of modeling: "A modeled ratio of CH$_3$SH/C$_2$H$_5$SH = 3.1 is obtained, compared with the observed value of $>21$."]
- result: Modeled CH3SH/C2H5SH = 3.1 ± not stated dimensionless [abstract: "The modeled ratio CH$_3$SH/C$_2$H$_5$SH = 3.1 is lower than the observed value of $\gtrsim 21$"]
- limitation (authors): Model not accurate enough, particularly for CH3SH, to support or dismiss the Orion KL ethanethiol detection [Discussion: "Unfortunately, our model calculations are not accurate enough, in particular for CH$_3$SH, to support or dismiss the reported C$_2$H$_5$SH detection in Orion KL."]
- not stated (card): Array configurations, beam, rms, spectral resolution, calibration and imaging parameters (only in companion paper); Source coordinates and distance/systemic velocity; How source sizes were fitted and LTE fitting software (not named); Line widths and velocity offsets per species beyond table values; Chemical network file and full reaction rates

### 2016A&A...592A..76D: ALMA-resolved salt emission traces the chemical footprint and inner wind morphology of VY Canis Majoris (2016; evolved_stars, astrochemistry; archival_reuse)
- question: What is the inner-wind density structure of the red supergiant VY CMa, and how do gaseous NaCl and dust interact chemically, as traced by spatially resolved NaCl emission?
- step 3: Model NaCl gas-grain chemistry
  - method: Simplified network of accretion, thermal desorption and photodesorption; analytic steady-state solution for T_b = 5000, 10000, 15000 K [4.1.2: "we have decided to study the evolution of the NaCl abundance for three different values of the surface binding energies: 5 000 K, 10 000 K, and 15 000 K."]
  - parameter: n_H = 1e8 cm^-3 at ~10 R*, S=1, F_FUV Y_PD = 3e5 [4.1.2: "a hydrogen number density of $1\times10^8$ cm$^{-3}$ is reached at $\sim$10 R$_{\star}$"]
  - assumption: Dust-to-gas mass ratio 0.002; grain sizes 0.005-0.25 micron; solar Cl abundance 3.2e-7 [4.1.1: "For a dust-to-gas mass ratio of 0.002 (cite: Decin2006A&A...456..549D), $K$ is $\sim$2.8$\times10^{-26}$ cm$^{2.5}$ per H atom"]
  - validation: Compared qualitatively with ALMA detection of NaCl at 1.22'' [Discussion, NaCl gas-grain chemistry: "The ALMA data clearly show gaseous NaCl emission around 1.22$^{\prime\prime}$ in the south-western extension, at a place where also scattering by dust grains peaks"]
- result: Turn-over T_b/T_d for gaseous fraction = ~50 ± not stated dimensionless [4.1.2: "The turn-over point is around $T_b/T_d \sim 50$"]
- result: Gaseous NaCl fraction at low dust temperature = ~10% ± not stated percent [4.1.2: "only about 10% of the NaCl abundance resides in the gas phase at low dust temperatures"]
- limitation (authors): Only 16-20 antennas; cannot prove either scenario [5 Conclusions: "The present data, obtained with only 16–20 ALMA antennas, can not prove the validity of both scenarios"]
- not stated (card): CASA version and reduction/imaging details (task, weighting, robust, cell, image size, masking, deconvolver); Line-free channels for continuum subtraction; Whether archival SV calibrated products were used as is; Procedure for correcting the 325 GHz blends; Integration limits for moment-zero maps; Dust temperature profile and Y_PD assumptions of the chemical network beyond the quoted ones

### 2024ApJ...968L..19F: Deep Search for Phosphine in a Prestellar Core (2024; astrochemistry, star_formation; observational_alma_primary)
- question: Can gas-phase PH3 be detected in the prestellar core L1544, and what does its abundance imply for the volatile phosphorus elemental abundance?
- step 5: Gas-ice chemical modeling to constrain volatile P
  - method: Rate-equation three-phase model at 1e5 yr, varying volatile P elemental abundance from 2.57e-7 to 2.57e-9; gas-phase PH3 scales with P abundance [4.2 Model results: "The gas-phase abundance is almost proportional to the assumed total volatile P elemental abundance in all four models."]
  - parameter: Chemical desorption probability 4%; xi = 3e-17 s^-1 [4.1 Model description: "The chemical desorption probability of upon reaction between and atomic H is set to 4 %"]
  - assumption: Photodesorption yield 1e-3 per UV photon for P species [4.1 Model description: "We assume the yield of 10$^{-3}$ per incident UV photon for all P-bearing species."]
  - validation: Conclusion holds for 3e4 yr and 1e6 yr; desorption probability 2% and 8% tested [4.2 Model results: "We confirmed that this conclusion holds, even if a different time other than 10$^5$ yr ($3\times 10^4$ yr or 10$^6$ yr) is chosen."]
- result: Volatile P elemental abundance upper limit = 5e-9 ± not stated relative to H [4.2 Model results: "the volatile P elemental abundance in L1544 is less than $5\times10^{-9}$"]
- limitation (authors): Collisional rate coefficients for PH3-H2 unavailable; extended continuum emission resolved out may explain lower N(H2) [Appendix: H2 column density: "The contribution from the largely-extended ($>$25") continuum emission that was resolved out in the ACA observations may account for the above discrepancy."]
- not stated (card): Line-free channels used for continuum and uvcontsub; Image size, cell size, clean threshold/niter; Calibrators and pipeline version; Flux scale uncertainty; Full P chemical network reaction list and rate parameters (partly in Furuya 2023 submitted); Spectral rms in K converted from Jy/beam details

### 2024RAA....24g5017M: Investigating Sulfur Chemistry in the HD163296 Disk (2024; protoplanetary_disks, astrochemistry; archival_reuse)
- question: Detect and image CS 7-6 in the HD 163296 disk and use Nautilus chemical models to study sulfur chemistry and the C/O ratio
- step 4: Chemical modeling
  - method: Nautilus three-phase model run for 1 Myr cloud stage then 1e7 yr disk with parametrized disk, RADMC3D dust temperature, two-layer gas temperature; vary C/O 0.5-1.5 [3.2: "we simulated the chemical composition of the disk for $10^7$ years using a cosmic-ray ionization rate of $\rm 1.3\times10^{-17}\,s^{-1}$."]
  - software: Nautilus, RADMC3D
  - assumption: Cloud stage: T=10 K, nH=2e4 cm-3, Av=15, zeta=1.3e-17 s-1 [3.1: "a grain and gas temperature of 10 K, the gas density of $\rm n_H= 2\times10^4\,cm^{-3}$, the visual extinction of 15 mag"]
  - validation: Compared column densities to Le Gal et al. 2021 LTE values and upper limits [5.1: "We compared the model results against existing observationally deduced fractional column densities"]
- limitation (authors): Cannot determine best-fit C/O due to observational limitations [5.2: "Due to observational limitations, we are unable to determine the best fitting model for the C/O ratio in the HD 163296 disk."]
- not stated (card): Line-free channels for continuum subtraction; tclean multiscale scales, image size, cell size, niter/threshold; Keplerian mask parameters (width, rms threshold); bettermoments clip/mask details and GoFish settings; Number of Gaussian components and initial guesses; Nautilus run setup, final sizes of grain/dust, C/O variation implementation; CASA/pipeline version

### 2025ApJ...992...55T: Extended and Compact Ortho-H<SUB>2</SUB>D<SUP>+</SUP> Structures Close to the Moment of Star Formation: Evidence from ALMA-ACA Observations in Taurus (2025; star_formation, astrochemistry; observational_alma_primary)
- question: Can ortho-H2D+ (1_10-1_11) trace the dense centers of cores at stages around the onset of star formation (prestellar L1544, first-core candidate MC 35-mm, Class 0 VeLLO MC 27), and where does its emission arise?
- step 4: Chemical + radiative transfer modelling
  - method: Chemical network on static collapse-model profiles, then LIME LTE to compute o-H2D+ brightness [4 Discussion: "LTE radiative transfer simulations were performed with LIME code (cite: Brinch_2010) to compute the ortho-H$_2$D$^+$ peak brightness temperature distribution."]
  - software: LIME
  - assumption: static physical structure at each radius, 2e5 yr [4 Discussion: "we assumed a static physical structure"]
  - validation: Qualitative only; absolute intensities not matched [4 Discussion: "the absolute values of H$_2$D$^+$ intensity do not necessarily match the present observations."]
- limitation (authors): MC 35-mm detection marginal; model absolute intensities not matched [3 Results: "This suggests that, even if the emission is real, it is confined to a very narrow range both spatially and in velocity."]
- not stated (card): Calibration approach (pipeline vs manual), flux calibrators and flux uncertainty; Multiscale scales, cell and image size; Continuum subtraction and line-free channels; Mask definitions for MC 35-mm; Phase centers/coordinates of targets; TP imaging procedure; Chemical network initial conditions and LIME setup; Integrated intensity velocity ranges

### 2019A&A...624L...5P: The complexity of Orion: an ALMA view. III. The explosion impact (2019; star_formation, astrochemistry; observational_alma_primary)
- question: How does the 550-year-old explosion in Orion KL affect the spatial and velocity distribution of different molecular species, and what does this imply for their gas-phase chemistry?
- step 3: Test gas-phase destruction of deuterated species
  - method: Gas-phase chemical model with deuteration network, starting from deuterium-rich gas [Discussion: "Starting from a gas rich in deuterated species (D$_2$CO/H$_2$CO $\approx$ 0.01 and NH$_2$D/NH$_3$ $\approx$ 0.3) at a density of 1 $\times$ 10$^{5}$ cm$^{-3}$, a temperature of 150 K"]
  - parameter: cosmic ionization rate 1e-15 s-1, low extinction [Discussion: "low extinction to the ISRF and a harsh environment (approximated by a cosmic ionization rate $\zeta$ of 1 $\times$ 10$^{-15}$ s$^{-1}$)"]
- result: D2CO/H2CO ratio drop in 500-1000 yr = factor 3 to 40 ± not stated dimensionless [Discussion: "we found that the D$_2$CO/H$_2$CO ratio drops by a factor of 3 to 40 in 500 to 1000 years"]
- result: NH2D/NH3 ratio drop in 500 yr = factor 6 to 200 ± not stated dimensionless [Discussion: "while the NH$_2$D/NH$_3$ ratio drops by a factor 6 to 200 in 500 years, and the abundance of NH$_2$D itself decreases by a factor 20 to 5000"]
- not stated (card): Calibration and imaging procedures (CASA version, weighting, cleaning, continuum subtraction) are all deferred to Paper I; Beam size and rms of the channel maps; Channel width and velocity resolution of the maps; How the continuum was separated from line emission; Chemical model details (initial abundances, network, code) beyond the few listed parameters; Method for the spatial velocity cuts

### 2020A&A...644A..84M: The GUAPOS project: G31.41+0.31 Unbiased ALMA sPectral Observational Survey. I. Isomers of C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB> (2020; astrochemistry, star_formation; observational_alma_primary)
- question: Which C2H4O2 isomers (methyl formate, glycolaldehyde, acetic acid) are detected in the hot core G31.41+0.31, with what abundances and emission sizes, and what do they imply for formation pathways?
- step 6: Compare with literature sources and chemical models
  - method: Compare abundances and column density ratios with other sources and published chemical model predictions [5.1 Comparison with other sources: "Figure [9] shows the abundances with respect to H$_2$ (upper panel) and the column density ratios (lower panel)"]
- limitation (authors): Tex-Ntot degeneracy for AA gives a factor ~2 uncertainty on Ntot [4.2 Acetic Acid: "with an uncertainty on $N_{\rm{tot}}$ of a factor $\sim2$"]
- limitation (authors): Some MF transitions under-reproduced; unidentified blends possible [4.1 Methyl Formate: "we cannot exclude that some of these transitions may also be blended with still unidentified molecular species"]
- not stated (card): Whether the archive pipeline or manual calibration and CASA version were used; Exact tclean parameters (deconvolver, niter, threshold, masks, image size); How the beam was matched to 1.2'' (imsmooth/restoringbeam details); STATCONT parameters; XCLASS optimizer algorithm, start values, iterations and the preliminary-fit FWHM/vLSR procedure; Exact fit frequency ranges and line lists (only in append…

### 2021ApJ...908..108F: Physical and Chemical Structure of the Disk and Envelope of the Class 0/I Protostar L1527 (2021; star_formation, astrochemistry, protoplanetary_disks; multi_facility_alma_minor)
- question: Can a coupled dynamical, radiative-transfer and gas-grain chemical model (RadChemT) reproduce the observed C18O, 12CO and N2H+ line emission, PV diagrams and SED of the Class 0/I protostar L1527?
- step 2: Time-dependent chemistry
  - method: Point-model UMIST RATE12 network with gas-grain reactions per cell [2.3 Chemical model: "Our chemical network is taken from the UMIST database, RATE12"]
- limitation (authors): Model does not reproduce C18O self-absorption at the protostar [4.5.2: "our model does not currently reproduce the self-absorption feature"]
- not stated (card): ALMA calibration/CASA version and imaging recipe (robust, deconvolver); Continuum subtraction and line-free channels; How the PV cut was extracted and model offset/normalization; Chemistry code name/version and HOCHUNK3D setup files

### 2016A&A...585A..58V: Resolved gas cavities in transitional disks inferred from CO isotopologs with ALMA (2016; protoplanetary_disks; observational_alma_primary)
- question: What are the size, depth and shape of the gas cavity inside the dust cavities of four transition disks, and what do they imply for embedded planets and disk viscosity?
- step 2: Fit physical-chemical model to CO isotopologs by eye
  - method: Adopt prior dust structure; vary surface density, gas-to-dust ratio, outer radius, cavity radius and delta parameters in DALI to match spectra, intensity maps and cuts, including isotope-selective photodissociation [3.2 Model-fitting approach: "we used the initial dust structure model and only varied a small number of parameters to fit the CO emission by eye by subsequent adjustments of the surface density, gas-to-dust ratio, outer radius, and the $\delta$ parameters"]
  - software: DALI
  - parameter: Sigma(r) power law with exponential cutoff, gamma=1 [3.1 Physical model: "The surface density $\Sigma(r)$ is assumed to be a radial power-law with an exponential cut-off following the time-dependent viscosity disk model $\nu \sim r^{\gamma}$ with $\gamma=1$"]
  - assumption: Gas and dust follow same density profile with varying gas-to-dust ratio [3.1 Physical model: "The gas and dust follow the same density profile, but the gas-to-dust ratio is varied throughout the disk"]
  - fitting: By eye; no chi2 or MCMC [3.2 Model-fitting approach: "We did not use a $\chi^2$ or Markov chain Monte Carlo (MCMC) method because the computational time of the models is too long and the number of parameters too large."]
  - validation: Small model grid with different cavity radii and delta values; uncertainty within 5 AU and an order of magnitude [3.2 Model-fitting approach: "the density and $\delta$ parameters are estimated to be within an order of magnitude and the radial parameters to within 5 AU based on a small model grid"]
- result: HD135344B gas cavity radius = 30 ± ≲5 AU AU [4.1 Results for individual targets: "The modeling constrains the gas cavity radius to 30 AU (dust cavity radius is 40 AU), and the drop is $2\cdot10^{-4}$"]
- result: DoAr44 gas cavity radius = 16 ± ≲5 AU AU [4.1 Results for individual targets: "still show a gas cavity that is only half the size of the dust cavity: 16 AU"]
- result: IRS48 gas cavity radius = 25 ± ≲5 AU AU [4.1 Results for individual targets: "The gas cavity radius is found to be 25 instead of the 20 AU found by (cite: Bruderer2014)"]
- result: HD135344B delta_gas2 = 2e-4 ± within an order of magnitude dimensionless [Table 2: "| density | $\Sigma_c$ (g cm$^{-2}$) | 120 | 400 | 60 | 0.5 |"]
- not stated (card): Self-calibration solution intervals and reference antenna; Clean masks, thresholds, line-free channels and continuum subtraction method; Full DALI input parameters (stellar UV, dust composition, abundances, isotope ratios); Model grids tried and how fit quality was judged; Model fits not released

### 2017A&A...601A..48G: Exploring molecular complexity with ALMA (EMoCA): Simulations of branched carbon-chain chemistry in Sgr B2(N) (2017; astrochemistry, star_formation; theory_or_simulation_compared_to_alma)
- question: Explain the observed i:n ratio of propyl cyanide in Sgr B2(N2), predict abundances of the four butyl cyanide isomers and alkanes up to pentane, and test for n-butyl cyanide in EMoCA data
- step 1: Run collapse and warm-up chemical models
  - method: MAGICKAL three-phase rate-equation model with free-fall collapse then warm-up from 8 to 400 K at three timescales [2.1 Physical model: "The physical model consists of two stages: free-fall collapse, followed by a dynamically-static warm-up."]
  - software: MAGICKAL
  - parameter: n_H = 2e8 cm-3 post-collapse; zeta = 1.3e-17 s-1; 0.1 micron grains [2.1 Physical model: "A post-collapse gas density of $n_{\mathrm{H}} = 2 \times 10^{8}$ cm$^{-3}$ is assumed"]
  - assumption: Canonical cosmic-ray ionization rate 1.3e-17 s-1 [2.1 Physical model: "A canonical cosmic-ray ionization rate of $\zeta$ = $1.3 \times 10^{-17}$ s$^{-1}$ is assumed"]
  - validation: Compared model ice abundances and i:n ratio with observations; tested high CN-addition barriers [3.6 High activation-energy models: "In order to test the dependence of the model results on these barriers, we re-ran the collapse model and the three subsequent warm-up models"]
- result: Model i/n propyl cyanide, medium warm-up low EA = 0.24 ± not stated dimensionless [Table 7: "C$_3$H$_7$CN, $i$ / $n$ | | 3.0 | | 0.45 | | 0.24 | | 0.17 | | 1.8 | | 1.5"]
- limitation (authors): Cosmic-ray ionization rate poorly constrained; full sensitivity study left for future [5 Discussion: "the cosmic-ray ionization rate for Sgr B2(N2) is poorly constrained by observations"]
- not stated (card): EMoCA data reduction, line-survey spectral setup and calibration details are not given; Fitting/LTE modelling details (spectral modelling software, linewidth, rms) for the n-C4H9CN upper limit; Full MAGICKAL code and network files, and ODE solver settings; Warm-up timescale values for fast/medium/slow in this paper

### 2018A&A...612L..11S: Detection of CI line emission towards the oxygen-rich AGB star omi Ceti (2018; evolved_stars, astrochemistry; multi_facility_alma_minor)
- question: Is CI emission present in the envelope of the O-rich AGB star omi Cet, and does it trace external ISRF dissociation or internal UV from the binary companion?
- step 2: Shell chemistry plus non-LTE RT model
  - method: Chemical model gives 12C and 13C abundance profiles used as input to Monte Carlo non-LTE RT [4.1.1 The circumstellar model: "We used the $^{12}$C and $^{13}$C abundance distributions that are shown in Fig. [3](#Chemi) as input files in the mcp."]
  - software: mcp, UCL_CHEM-type CSE chemical model (McElroy13)
  - parameter: mass-loss 2.5e-7 Msun/yr, v_exp 2.5 km/s, 12CO/H2=5e-4, 13CO/H2=5e-5 [Chemical modelling results: "We assumed the initial fractional abundances of $^{12}$CO/H$_2$=5$\times$10$^{-4}$ reported for omi Cet (RS01)"]
  - assumption: Spherical uniformly expanding envelope, ISRF only external UV [4.1.1 The circumstellar model: "we assume a uniformly expanding spherical envelope which is formed due to a constant mass-loss"]
  - validation: CO(2-1,3-2,4-3) JCMT lines reasonably reproduced [4.1.1 The circumstellar model: "Although the model reasonably reproduces the CO observations"]
- result: Peak CI abundance in shell model = 2.4e-5 ± not stated dimensionless [abstract: "a peak atomic fractional abundance of 2.4 $\times$ 10$^{-5}$"]
- limitation (authors): Single-dish data cannot constrain the complex outflow; the CSE model is crude [4.1.1 The circumstellar model: "it is not possible to constrain the complex outflow around omi Cet based on the single-dish observations"]
- not stated (card): ALMA calibration, CASA version and imaging parameters for the CO(3-2) data; How the two ALMA projects were combined; Channel width and rms of the ALMA map; Source coordinates; Chemical network details (Saberi et al. in prep); How the 0.2 arcsec emitting radius was measured from the map; Baseline polynomial fitting windows and spectral resolution of APEX data

### 2024A&A...687A.233M: Unveiling the gas phase H<SUB>2</SUB>NCO radical: Laboratory rotational spectroscopy and interstellar searches in the direction of IRAS 16293-2422 (2024; astrochemistry, star_formation; multi_facility_alma_minor)
- question: Can the gas-phase rotational spectrum of the H2NCO radical be measured in the laboratory and used to search for the radical toward IRAS 16293-2422 in PILS data?
- step 2: Compare abundance limit with chemical model
  - method: Compare upper limit with Nautilus model abundances [Astrochemical implications: "we compare the upper limit derived above to the calculated abundance obtained using the model"]
  - software: Nautilus
  - parameter: density 2.5e4 cm-3, 10 K, Av 10 mag, zeta 1.3e-17 s-1 [Astrochemical implications: "homogeneous gas with a density equal to $2.5\times10^4$ cm$^{-3}$; temperature of 10 K for both gas and dust"]
- not stated (card): Exact offset coordinates of the extraction position; ALMA calibration and imaging details of the PILS data (in Jorgensen2016); Noise rms used for upper limits and the criteria for the limits; Beam-dilution treatment; Whether the 12 m and ACA data were combined

### 2025ApJ...989....1Z: The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). I. Program Overview and Summary of First Results (2025; protoplanetary_disks, astrochemistry; large_program_or_survey)
- question: How do gas disk mass and size evolve over the lifetime of protoplanetary disks, and what do they imply for disk evolution mechanisms?
- step 5: Derive gas and dust masses
  - method: Compare 13CO, C18O, N2H+ (Class II) or C17O (Oph) fluxes and 1.3 mm continuum with thermo-chemical model grid; dust mass from optically thin continuum [4.3: "we estimate the gas disk masses by comparing the $^{13}$CO, C$^{18}$O, and N$_2$H$^+$ line fluxes, along with the 1.3 mm continuum fluxes, to a large grid of thermo-chemical models"]
  - software: DALI
  - assumption: kappa = 2.3 (nu/230 GHz) cm2/g, Tdust = 20 K; ISM xCO=1e-4 for Ophiuchus [4.3: "assuming a dust opacity of $\kappa_\nu=2.3~(\nu/230\,{\rm GHz})\,$cm$^2$ g$^{-1}$ and an average dust temperature of 20 K"]
- limitation (authors): Medians are of survivors; survival bias not accounted in medians; absolute ages model-dependent; regions assumed to share initial conditions [6: "The median values, listed in Table [4](#tab:median), do not take into consideration survival bias"]
- not stated (card): Per-source robust values for self-calibration (0.5-1.0 range only); Exact solint sequence and SNR criteria per source; Line-free channels and continuum-flagging details per source; Keplerian mask parameters and R_max per disk (in companion papers); Thermo-chemical model grid parameters for gas masses; Individual line fluxes and uncertainties; CLEAN thresholds/mask details and Ophiuchus Keplerian-…

### 2019ApJ...876...72L: Sulfur Chemistry in Protoplanetary Disks: CS and H<SUB>2</SUB>CS (2019; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: What are the nature, distribution and abundance of sulfur-bearing molecules (CS, isotopologues, H2CS) in protoplanetary disks, and can disk chemistry models reproduce them?
- step 6: Disk chemistry modeling and comparison to observed column densities
  - method: Nautilus v1.1 three-phase gas-grain 1+1D models with parametric physical structure, 0D cloud initial conditions, sulfur abundance 8e-8, 1 Myr [4.2 Chemical modeling: "We ran the disk chemistry models for one million years."]
  - software: Nautilus
  - parameter: Disk parameters in Table 3 (e.g. Md=0.18 and 0.03 Msun, Rc=100 au) [Table 3: "| Disk mass: $M_{\rm{d}}$ ($M_\odot$) | 0.18 | 0.03 |"]
  - assumption: Dust temperature equals gas temperature; dust-to-mass ratio 0.01; 0.1 micron grains; low S abundance 8e-8 [4.1.1 Temperature profile: "The dust temperature is assumed equal to that of the gas."] [4.2 Chemical modeling: "A dust-to-mass ratio of 0.01 is assumed, with spherical grains of $0.1~\mu$m single radius size."]
  - validation: Model column densities, temperatures and profiles compared with observations [4.3 Model results: "Across the disks, the model predictions are generally within a factor of a few for both MWC 480 and LkCa 15"]
- limitation (authors): Low resolution and S/N cannot distinguish optically thick CS from isotopic enhancement or beam dilution; LTE and filling factor assumptions uncertain [abstract: "Additional lines and higher spatial resolution observations are needed to distinguish between these scenarios."]
- limitation (authors): Models simplistic: no X-rays, grain growth, LkCa 15 inner cavity; not tuned [5.1 Model predictions vs observations: "we do not include LkCa15’s wide inner cavity (cite: alencar2018) in the LkCa disk structure."]
- not stated (card): Line-free channels and channel width/velocity range used for continuum subtraction and imaging; Image size, cell size, and CLEAN iteration limits; Self-calibration solution intervals and number of rounds; Integration velocity range and exact Keplerian mask padding for flux extraction; Beam/size of the uv-taper applied to 12CS; Gaussian line width Δv_FWHM and filling factor adopted in the rotation…

### 2019A&A...628A..10B: Re-exploring Molecular Complexity with ALMA (ReMoCA): interstellar detection of urea (2019; astrochemistry, star_formation; observational_alma_primary)
- question: Is urea detected toward the hot cores of Sgr B2(N) in the ReMoCA ALMA survey, and how does its abundance compare with related COMs and chemical models?
- step 7: Chemical modeling
  - method: MAGICKAL cold collapse then warm-up (fast, medium, slow); compare peak gas-phase abundances with observed ratios [5 Chemical modeling: "we used the astrochemical kinetics code MAGICKAL (cite: Garrod13)"]
  - software: MAGICKAL
  - parameter: zeta = 1.3e-17 s-1; warm-up to 200 K in 5e4, 2e5 or 1e6 yr [5 Chemical modeling: "The cosmic-ray ionization rate is held at the canonical value, $\zeta$=$1.3 \times 10^{-17}$ s$^{-1}$."]
  - assumption: E_des(CH3NCO)=6486 K, N-methylformamide 7386 K [5 Chemical modeling: "to give $E_{\mathrm{des}}$(CH$_3$NCO) = $E_{\mathrm{des}}$(CH$_3$NC) + $E_{\mathrm{des}}$(O) = 6486 K"]
- limitation (authors): Line-continuum splitting is preliminary with unexplained baseline artifacts [2.2 Data reduction: "the splitting of the line and continuum emission performed so far is still preliminary and we plan to improve it in the future."]
- not stated (card): Pipeline/QA details and flux calibrator names and flux scale uncertainty; Which line was used for self-calibration in each setup; Exact channel masks for continuum determination; Clean thresholds, masks and iteration counts; Full list of molecules/parameters in the full Weeds model; Uncertainties on LTE column densities; Urea spectroscopic line list (Medvedev et al. in prep.); Details of the MAGI…

### 2017A&A...601A...4A: Growth of carbon chains in IRC +10216 mapped with ALMA (2017; evolved_stars, astrochemistry; observational_alma_primary)
- question: How do linear carbon chains (polyynes and cyanopolyynes) form and grow in the envelope of the C-star IRC +10216, and where are they located radially?
- step 3: Chemical model of the expanding envelope
  - method: Gas-phase kinetic model, isotropic expansion from 2e14 cm, UV illumination by Draine field, NH/AV reduced 1.5x, cosmic ray rate 1.2e-17 s-1 [4.1 Chemical model: "The adopted cosmic-ray ionization rate of H$_2$ is $1.2\times10^{-17}$ s$^{-1}$"]
  - software: Meudon PDR code
  - assumption: Distance 123 pc; C2H2 and HCN abundances 8e-5 and 4e-5 relative to H2 [4.1 Chemical model: "the adopted abundances relative to H$_2$ are $8\times10^{-5}$ and $4\times10^{-5}$, respectively"]
  - validation: Compared to observed radial brightness [Discussion: "A comparison between the observed and calculated $\lambda$ 3 mm emission distributions of carbon chains allows us to draw conclusions about the formation mechanism of carbon chains in IRC +10216."]
- limitation (authors): Spherical isotropic model cannot reproduce arcs; comparison only first order; IR pumping uncertain for C4H, C6H, C3N [5 Discussion: "the comparison between the calculated and observed emission distributions can only be done to first order, and not at the sub-arcsecond level"]
- not stated (card): ALMA/CASA calibration and imaging procedure, versions, weighting, cell/image size; Details of merging with IRAM 30m data; Line-free channels and continuum subtraction method; Exact synthesized beams and rms for C6H stacked map and list of 19 C6H lines; Method of azimuthal averaging and strip extraction; Chemical network files and IR pumping parameters for full reproduction; Flux calibrator and ca…

### 2019ApJ...883...98Z: Systematic Variations of CO Gas Abundance with Radius in Gas-rich Protoplanetary Disks (2019; protoplanetary_disks, astrochemistry; archival_reuse)
- question: Does the CO gas abundance vary with radius in four well-studied protoplanetary disks, and do chemical processing or dust evolution (pebble settling and drifting) explain it?
- step 4: Run thermo-chemical models and synthesize line images
  - method: RAC2D 2D time-dependent chemistry for 1 Myr, LTE ray tracing, convolution to observed resolution [3.3 The numerical methods: "we compute line images using the ray-tracing module of RAC2D, assuming an LTE condition."]
  - software: RAC2D
  - parameter: zeta_CR = 1.36e-18 (standard) and 1.36e-17 s^-1 (high); gamma ±0.2 tests [3.4 Parameter Tests: "we run two sets of models: a set of standard models with a $\zeta_{\rm CR}=1.36\times10^{-18}$ s$^{-1}$ and the other set with a high CR rate of 1.36$\times10^{-17}$ s$^{-1}$."]
  - assumption: Initial CO abundance 1.4e-4 relative to H; CO/C18O=570, CO/13CO=69; no isotopologue fractionation [3.3 The numerical methods: "We rescale the output CO abundance by the local ISM ratios of CO/$^{13}$CO= 69, and CO/C$^{18}$O=570"]
  - validation: Model CO snowline locations compared with literature [4.1 results: "the mid-plane CO snowline locations are consistent with existing observational constraints"]
- result: CO gas column depletion in high-CR models, DM Tau and TW Hya, 10-100 AU = 5-20 ± not stated dimensionless [4.2: "Models of DM Tau and TW Hya show substantial CO gas depletions between 10-100 AU, by a factor of 5-20 after 1 Myr."]
- result: Fraction of CO converted in standard models = <10% ± not stated percent [4.1: "In these models, less than 10% of total CO (gas+ice) have been converted to other carbon carriers after 1 Myr."]
- limitation (authors): Small-scale substructures ignored; smooth density profiles used [3.2.1 Disk parameters: "We also ignore small-scale substructures in these disks"]
- limitation (authors): Gas-to-dust ratio fixed at 100; gas mass uncertainty considered not crucial [3.2.1 Disk parameters: "For simplicity, we use a gas-to-dust (small+large) mass ratio of 100 for all four disks."]
- not stated (card): Rest frequencies and spectral windows used; Line-free channel ranges for continuum and self-cal solution intervals; Image size, cell size, masking, and clean thresholds; CASA versions for the archive calibration; Method for assigning best depletion factor at each radius (fit metric, radial binning, uncertainties); Stellar UV spectrum and luminosity details; Full RAC2D configuration and code avail…

### 2019A&A...628A..27B: The complex chemistry of hot cores in Sgr B2(N): influence of cosmic-ray ionization and thermal history (2019; astrochemistry, star_formation, milky_way_ism; archival_reuse)
- question: What physical history and environmental conditions (cosmic-ray ionization rate, minimum prestellar dust temperature) explain the chemical differences among the Sgr B2(N2-N5) hot cores?
- step 7: run chemical model grid
  - method: MAGICKAL, 18 models per source (6 CRIR x 3 Tmin), 1333 species, 13374 reactions [3.2 The chemical models: "For each hot core we run a grid of 18 models, one for each set of physical parameters (CRIR and $T_{\rm min}$"]
  - software: MAGICKAL
  - parameter: CRIR 1.3e-17 to 1.3e-14 s-1; ISRF 1 G0 [Chemical modeling, The chemical models: "We run chemical simulations using CRIRs ranging from the standard value $\zeta^{\rm H_2}_0$ = 1.3$\times$10$^{-17}$ s$^{-1}$ to 1000$\times \zeta^{\rm H_2}_0$ = 1.3$\times$10$^{-14}$ s$^{-1}$."]
- limitation (authors): Ages unreliable because the same accretion history is assumed for all sources; no CR attenuation. [5.5 Limitations: "The estimated $t_{\rm source}$ values are unlikely to be accurate"]
- not stated (card): CASA/pipeline version and calibration details (deferred to Belloche et al. 2016); line-free channels used for baseline subtraction; continuum flux densities of N2, N4, N5 and free-free correction values; exact fitted Weeds parameters for N2 and fit procedure details; MAGICKAL code access and exact fitted accretion-rate relation Mdot(t)

### 2018A&A...617A..28S: Chemistry in disks. XI. Sulfur-bearing species as tracers of protoplanetary disk physics and chemistry: the DM Tau case (2018; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: What are the sulfur-bearing molecule abundances in the DM Tau disk, and how sensitive is sulfur chemistry to physical and chemical conditions (e.g. C/O)?
- step 5: Chemical modeling and comparison
  - method: ALCHEMIC gas-grain chemistry on 1+1D disk model, 5 Myr; parameter grid; median column densities at 100-800 au compared with observations [Results: "medians of these column densities were computed at radii between 100 and 800 au and compared with the best-fit disk-averaged quantities derived with RADEX"]
  - software: ALCHEMIC
  - parameter: Mdisk 0.066 Msun, Mdot 5e-9 Msun/yr, alpha 0.01, Rout 800 au, Lx 1e31 erg/s, grain 0.1 um [Disk physical structure: "an outer radius of $800$ au, an accretion rate of $5\times10^{-9}\mathrm{M}_\odot$ yr$^{-1}$, a viscosity parameter $\alpha = 0.01$"]
  - assumption: Equal gas and dust temperatures; gas-to-dust 100 [Disk physical structure: "where equal gas and dust temperatures are assumed"]
  - validation: Modeling uncertainties of factor ~3-10 considered [Impact of C/O ratios: "taking modeling uncertainties of a factor of $\sim 3-10$ into account"]
- result: Modeled CS/SO at C/O=1.2 = 282 ± not stated dimensionless [Impact of C/O ratios: "the modeled CS/SO ratio increases from the “standard” low value of $\approx 0.026$ (C/O $=0.46$) to the values of 13 (C/O $=1.0$) and 282 (C/O $=1.2$)"]
- limitation (authors): C/O cannot be constrained more accurately due to non-detections and poorly known available sulfur [Comparison with previous studies of sul…: "We cannot constrain the C/O ratio in the molecular layer more accurately due to the non-detection of SO and SO$_{2}$"]
- not stated (card): Continuum self-calibration solint and number of iterations; Line-free channels and continuum fit order for uv continuum subtraction; Clean threshold, cell and image size; Velocity-channel stacking details for SO, SO2, OCS pairs; DiskFit priors and MCMC settings; Flux calibrator flux values and ALMA data processing script; Exact definition of median column density comparison and chemical model run…

### 2019ESC.....3.2088S: Complex Organic Molecules in Star-Forming Regions of the Magellanic Clouds (2019; astrochemistry, star_formation; multi_facility_alma_minor)
- question: What is known about complex organic molecules in Magellanic Cloud star-forming regions, and how do observations compare with chemical models?
- step 3: Hot core model calculation for LMC/SMC ices
  - method: Taquet et al. dynamical-chemical model with fixed physical conditions and instant ice injection, ice abundances scaled by elemental depletions [5.2.2: "the physical conditions are fixed in time and the ices are injected instantaneously into the hot gas at $t=0$"]
  - parameter: n_H2 = 5e7 cm-3, T=150 K, zeta = 3e-17 s-1 [5.2.2: "$n_{\rm H_2} = 5 \times 10^7$ cm$^{-3}$, $T$=150 K, and a cosmic-ray ionization rate $\zeta = 3\times10^{-17}$ s$^{-1}$"]
  - validation: Compared model CH3OCH3/CH3OH and HCOOCH3/CH3OH ratios with N113 observations [5.2.2: "the observed CH$_3$OCH$_3$/CH$_3$OH ratios in A1 ($\sim$0.1) and B3 ($\sim$0.2) are about an order of magnitude higher than the calculated values ($\sim$0.01)"]
- result: Model CH3OCH3/CH3OH vs observed in LMC = model ~0.01 vs observed ~0.1 (A1), ~0.2 (B3) ± not stated dimensionless [5.2.2: "the observed CH$_3$OCH$_3$/CH$_3$OH ratios in A1 ($\sim$0.1) and B3 ($\sim$0.2) are about an order of magnitude higher than the calculated values ($\sim$0.01)"]
- limitation (authors): N159W-S ALMA analysis is preliminary, so no physical parameters given [4.2.1: "Since the analysis of the ALMA data is preliminary, we do not provide physical parameters for N159W–S"]
- not stated (card): Image size and cell size; Line-free channel ranges; Mask and clean threshold; Spectral resolution of the cube; LTE fitting method and software for N159W-S; Phase and bandpass calibrator details beyond names; Continuum subtraction method

### 2019ApJ...875...96N: Dust Continuum Emission and the Upper Limit Fluxes of Submillimeter Water Lines of the Protoplanetary Disk around HD 163296 Observed by ALMA (2019; protoplanetary_disks, astrochemistry; observational_alma_primary)
- question: Can sub-millimeter water line upper limits toward HD 163296 constrain the mm dust opacity and the extent of the hot water vapor region / H2O snowline position?
- step 3: Model line profiles with varying dust opacity and water-vapor outer edge
  - method: Modified 1D RATRAN with disk chemical model; dust opacity x1, 2, 3, 10; outer edge 5, 8, 11, 14, 20 au; dust continuum subtracted [3.1 Upper limit of the water line fluxes: "We calculate the model line profiles with different dust opacity values and different outer edges of the region with a high water vapor abundance."]
  - software: RATRAN
  - parameter: OPR=3, 16O/18O=560, kappa_mm original 1.0 cm2/g [3.1 Upper limit of the water line fluxes: "We set the isotope ratio of oxygen $^{16}$O/$^{18}$O to 560 throughout the disk"]
- limitation (authors): Observation time was ~20% of the requested time, insufficient to test the model [3.1 Upper limit of the water line fluxes: "the observation time executed (20% of our proposed time in our Cycle 3 proposal) was not enough to test our model."]
- not stated (card): Self-calibration solution intervals, number of iterations and references; Line-free channels / continuum subtraction method for spectral cubes; Cell size, image size, masks, clean threshold; Number of ACA execution blocks and relative weighting in combination; Source position, PA used for the Keplerian filter and aperture center; How rms of peak flux density was measured for 3 sigma limits; Spect…

### 2017MNRAS.469.2230M: Detection of methyl isocyanate (CH<SUB>3</SUB>NCO) in a solar-type protostar (2017; astrochemistry, star_formation; archival_reuse)
- question: Is methyl isocyanate (CH3NCO) present in the solar-type protostar IRAS16293-2422 B, what are its abundance and ratios to HNCO and NH2CHO, and how is it formed?
- step 5: Chemical modelling
  - method: Three-phase UCL_CHEM gas-grain model with added CH3NCO, HNCO routes [4: "The physical conditions and the chemical composition of the IRAS16293 B hot corino were modelled using a three phase model."]
  - software: UCL_CHEM
  - parameter: nH 5e8 cm-3, T 10 to 110 K over 1e5 yr [4: "assuming a constant H$_2$ gas density ($5\times10^{8}$ cm$^{-3}$) while gradually increasing the gas temperature from 10$\,$K to 110$\,$K during the first 10$^5$ yrs"]
  - validation: Compared with observed abundances and L1544 upper limits [4: "our model perfectly reproduces the upper limits of CH$_3$NCO measured in cold cores such as L1544"]
- result: Model CH3NCO abundance = 6.0e-10 ± not stated dimensionless [4: "a predicted abundance for CH$_3$NCO of \[CH$_3$NCO\]=$6.0\times10^{-10}$"]
- limitation (authors): H2 column is a lower limit, so abundances are upper limits as dust may be optically thick [3.1: "We however caution that this value should be considered as a lower limit since dust may be optically thick even at these low frequencies."]
- limitation (authors): NH2CHO underproduced by model by factor 10 [4: "the abundance of NH$_2$CHO is underproduced by a factor of 10"]
- not stated (card): CASA version and imaging parameters (weighting, robust, cell, image size, deconvolver); Line-free channels used for continuum subtraction; Per-dataset imaging details and which datasets cover which lines; MADCUBAIJ fitting settings (parameter priors, velocity, fit method); Whether catalogs entries (JPL vs CDMS) used for CH3NCO; Details of chemical model grid, best-fit age and parameter sampling

## All papers in this technique

- 2014Sci...345.1584B (2014): Detection of a branched alkyl molecule in the interstellar medium: iso-propyl cyanide
- 2015ApJ...803...70S (2015): ALMA Observations of the IRDC Clump G34.43+00.24 MM3: DNC/HNC Ratio
- 2015ApJ...810..112O (2015): Double DCO<SUP>+</SUP> Rings Reveal CO Ice Desorption in the Outer Disk Around IM Lup
- 2015ApJ...814..143A (2015): The Peculiar Distribution of CH3CN in IRC +10216 Seen by ALMA
- 2016A&A...585A..58V (2016): Resolved gas cavities in transitional disks inferred from CO isotopologs with ALMA
- 2016A&A...587A..92M (2016): Exploring molecular complexity with ALMA (EMoCA): Alkanethiols and alkanols in Sagittarius B2(N2)
- 2016A&A...592A..76D (2016): ALMA-resolved salt emission traces the chemical footprint and inner wind morphology of VY Canis Majoris
- 2016ApJ...825...79S (2016): Survey Observations of a Possible Glycine Precursor, Methanimine (CH2NH)
- 2016ApJ...831..101B (2016): Hydrocarbon Emission Rings in Protoplanetary Disks Induced by Dust Evolution
- 2017A&A...599A.101V (2017): Robustness of N<SUB>2</SUB>H<SUP>+</SUP> as tracer of the CO snowline
- 2017A&A...601A...4A (2017): Growth of carbon chains in IRC +10216 mapped with ALMA
- 2017A&A...601A..48G (2017): Exploring molecular complexity with ALMA (EMoCA): Simulations of branched carbon-chain chemistry in Sgr B2(N)
- 2017A&A...601A..49B (2017): Rotational spectroscopy, tentative interstellar detection, and chemical modeling of N-methylformamide
- 2017A&A...608A..96L (2017): The ortho-to-para ratio of H<SUB>2</SUB>Cl<SUP>+</SUP>: Quasi-classical trajectory calculations and new simulations in light of new observa…
- 2017ApJ...835..228T (2017): A Surface Density Perturbation in the TW Hydrae Disk at 95 au Traced by Molecular Emission
- 2017MNRAS.469.2230M (2017): Detection of methyl isocyanate (CH<SUB>3</SUB>NCO) in a solar-type protostar
- 2018A&A...612L..11S (2018): Detection of CI line emission towards the oxygen-rich AGB star omi Ceti
- 2018A&A...617A..28S (2018): Chemistry in disks. XI. Sulfur-bearing species as tracers of protoplanetary disk physics and chemistry: the DM Tau case
- 2018A&A...617A.120M (2018): Tracing the cold and warm physico-chemical structure of deeply embedded protostars: IRAS 16293-2422 vs. VLA 1623-2417
- 2018A&A...620L...1G (2018): ALMA detects a radial disk wind in DG Tauri
- 2018ApJ...859..131L (2018): The Distribution and Excitation of CH<SUB>3</SUB>CN in a Solar Nebula Analog
- 2019A&A...622A..26G (2019): Molecular ion abundances in the diffuse ISM: CF<SUP>+</SUP>, HCO<SUP>+</SUP>, HOC<SUP>+</SUP>, and C<SUB>3</SUB>H<SUP>+</SUP>
- 2019A&A...624L...5P (2019): The complexity of Orion: an ALMA view. III. The explosion impact
- 2019A&A...628A..10B (2019): Re-exploring Molecular Complexity with ALMA (ReMoCA): interstellar detection of urea
- 2019A&A...628A..27B (2019): The complex chemistry of hot cores in Sgr B2(N): influence of cosmic-ray ionization and thermal history
- 2019A&A...629A.146V (2019): IRC + 10°216 mass loss properties through the study of λ3 mm emission. Large spatial scale distribution of SiO, SiS, and CS
- 2019ApJ...871..107F (2019): Gas Density Perturbations Induced by One or More Forming Planets in the AS 209 Protoplanetary Disk as Seen with ALMA
- 2019ApJ...875...96N (2019): Dust Continuum Emission and the Upper Limit Fluxes of Submillimeter Water Lines of the Protoplanetary Disk around HD 163296 Observed by ALMA
- 2019ApJ...876...72L (2019): Sulfur Chemistry in Protoplanetary Disks: CS and H<SUB>2</SUB>CS
- 2019ApJ...883...98Z (2019): Systematic Variations of CO Gas Abundance with Radius in Gas-rich Protoplanetary Disks
- 2019ESC.....3.2088S (2019): Complex Organic Molecules in Star-Forming Regions of the Magellanic Clouds
- 2020A&A...644A..84M (2020): The GUAPOS project: G31.41+0.31 Unbiased ALMA sPectral Observational Survey. I. Isomers of C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB>
- 2020ApJ...891..164S (2020): Chemistry and Physics of a Low-metallicity Hot Core in the Large Magellanic Cloud
- 2020ApJ...898...54T (2020): Chemical Composition in the IRAS 16562-3959 High-mass Star-forming Region
- 2021A&A...651L...6B (2021): A major asymmetric ice trap in a planet-forming disk. II. Prominent SO and SO<SUB>2</SUB> pointing to C/O &lt; 1
- 2021A&A...655A..80D (2021): ATOMIUM: halide molecules around the S-type AGB star W Aquilae
- 2021ApJ...908..108F (2021): Physical and Chemical Structure of the Disk and Envelope of the Class 0/I Protostar L1527
- 2024A&A...687A.233M (2024): Unveiling the gas phase H<SUB>2</SUB>NCO radical: Laboratory rotational spectroscopy and interstellar searches in the direction of IRAS 162…
- 2024A&A...691A.180F (2024): CHEMOUT: CHEMical complexity in star-forming regions of the OUTer Galaxy: IV. ALMA observations of organic species at a galactocentric radi…
- 2024ApJ...968L..19F (2024): Deep Search for Phosphine in a Prestellar Core
- 2024ESC.....8..665M (2024): Detection and Chemical Modeling of Complex Prebiotic Molecule Cyanamide in the Hot Molecular Core G31.41 + 0.31
- 2024JKAS...57..163L (2024): HCN and HNC in the Disk of an Outbursting Young Star, V883 Ori
- 2024RAA....24g5017M (2024): Investigating Sulfur Chemistry in the HD163296 Disk
- 2025A&A...696A..31G (2025): Shock-induced HCNH<SUP>+</SUP> abundance enhancement in the heart of the starburst galaxy NGC 253 unveiled by ALCHEMI
- 2025ApJ...989....1Z (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). I. Program Overview and Summary of First Results
- 2025ApJ...992...55T (2025): Extended and Compact Ortho-H<SUB>2</SUB>D<SUP>+</SUP> Structures Close to the Moment of Star Formation: Evidence from ALMA-ACA Observations…
