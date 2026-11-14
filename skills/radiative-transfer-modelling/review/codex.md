# Codex review: radiative-transfer-modelling
VERDICT: FIX

## Findings

- SR-01 | medium | attribution | “RADMC-3D … 94”; “vis_sample … 11”; “MIRIAD … 7” | The Software aggregate gives radmc-3d **98**, radmc3d **9**, vis_sample **12**, and miriad **8**. It lists mcfost **34**, without the asserted case split; RADMC, HOCHUNK3D and SPARX are absent from that aggregate. | Reproduce the aggregate’s labels and counts exactly; remove unsupported variants and entries.

- SR-02 | medium | attribution | “of 39 listed fitting phrasings, about 25 describe by-eye, manual or no formal fit” | The Fitting methods aggregate contains **40** entries. It does not support classifying approximately 25 as manual or lacking a formal fit; entries include optimizers, retrievals and priors without naming their algorithms. | Recount with explicit classification rules, distinguish unspecified methods from manual methods, and identify these as phrasing entries rather than paper frequencies.

- SR-03 | high | attribution | “gas masses from rare isotopologues … 2025ApJ...984L..19Y” | That paper concerns **pressure-broadened CO line wings**, as its pack title states; its limitation specifies gas surface density scaling as X_CO^-0.5. | Retain 2019ApJ...882L..31B for rare isotopologues; describe 2025ApJ...984L..19Y separately as pressure-broadening inference.

- SR-04 | medium | attribution | “Planetary atmospheres and comets: vertical profiles by line-by-line retrieval … 2025ApJ...986L..22R” | That excerpt describes SUBLIMED non-LTE **Haser outflow models**, jet geometry and visibility least squares, rather than atmospheric vertical-profile retrieval. | Separate cometary outflow modelling from planetary atmospheric retrieval.

- SR-05 | medium | attribution | “simulate … with CASA simobserve/simalma … 2025A&A...697A..64V” | The cited excerpt specifies **ft + tclean**, followed by iterative surface-density corrections. It does not attribute this workflow to simobserve or simalma. | Describe its actual visibility-generation route; retain the simulator attribution for papers that explicitly used those tasks.

- SR-06 | medium | attribution | “CO/H2 = 1e-4 … 2017ApJ...851...85B” | That paper’s Assumptions entry gives **CO/H2 = 7e-5**, with freeze-out below 20 K and alternative photodissociation treatments. | Attach its actual abundance to the example; cite an unambiguous 1e-4 entry for that fiducial.

- SR-07 | medium | attribution | “Gas-to-dust ratio … 100 … 2018A&A...612A..72J” | That card literally labels its value **“Dust-to-gas mass ratio 100.”** The skill silently reverses the label. This appears to be a pack ambiguity, rather than safe evidence for either convention. | Flag the inversion for verification and use an unambiguous gas-to-dust entry, such as 2024ApJ...966..117X, as support for 100.

- SR-08 | medium | attribution | “a_min 0.005–10 um”; photons “2e5–2e9”; sampler steps “500–10,000” | The pack includes **a_min = 2 nm = 0.002 um** (2020A&A...644A..11L), **1e5 photons** (2019A&A...627A.114K), and **300–1000 steps** (2017MNRAS.465.2595M). | Correct the ranges or explicitly restrict them to a named subset; distinguish thermal and image/scattering photon budgets.

- SR-09 | medium | attribution | “Residual maps and channel-by-channel residuals consistent with noise (2016MNRAS.460.2933M)” | The excerpt supports continuum residuals consistent with noise. Its gas validation says the model spectrum **roughly** matches the observed profile; it does not establish noise-consistent residuals in every channel. | Separate the continuum residual check from the gas-spectrum comparison.

- SR-10 | medium | unsupported | “Named degeneracies: atmosphere temperature vs. emitting height and q vs. R_c … envelope mass vs. radius … gap width vs. depth” | These specific degeneracies are not supplied for 2015ApJ...813...99F, 2017ApJ...840L..12S or 2017ApJ...851L..23C. The pack explicitly supports the Mgas × alpha_turb and optical-thickness/height examples. | Retain supported examples; remove the other literature attributions or label them as general modelling considerations.

- SR-11 | medium | unsupported | “Many authors say their model is not unique or not optimized … 2016ApJ...820...54K, 2017ApJ...836..201D, 2017A&A...607L...6T” | These entries do not supply that admission. For 2016ApJ...820...54K, the supplied statement is **model uncertainty ±50%**. Explicit non-uniqueness is supplied for 2012ApJ...757..129R and 2013ApJ...774...16R. | Restrict the attributed admission to supported papers.

- SR-12 | medium | unsupported | “12CO and often SO are thick”; “Cloud contamination”; “parametric structure … not dynamically consistent” | The cited pack entries do not establish optical thickness for 2013Natur.493..191C/2014ApJ...796..131O, cloud contamination for 2017AJ....153..233F/2017ApJ...851..132C, or dynamical inconsistency for 2015ApJ...811...92C. | Remove unsupported paper attributions; retain physically appropriate cautions as explicitly general practice.

- SR-13 | medium | unsupported | “opacity … factor of 2–3”; “single-band dust cannot fix the opacity”; missing-flux citations to 2017A&A...597A..27S and 2016A&A...593A..92B | Those particular claims are absent from the cited entries. The pack supports a **factor-two** opacity uncertainty in 2015ApJ...808..102K and missing flux in 2016A&A...586A...5M. | Use the supported values and citations; distinguish general inference from reported author limitations.

- SR-14 | medium | unsupported | “near universal”; “LTE dominates the pack”; “Isotope-selective photodissociation is often omitted”; “About 8 are off-topic” | Counts of reporting lines do not establish prevalence across 274 papers. The pack explicitly identifies one isotope-selective-photodissociation omission, and gives no eight-paper exclusion tally. | Replace prevalence claims with documented examples; provide a reproducible denominator and exclusion list before stating frequencies.

- SR-15 | high | science | “photodissociation above a column threshold” | This reverses the shielding criterion explicitly given for 2017ApJ...851...85B and 2025ApJ...984L..21B: photodissociation occurs **below 1e21 cm^-2 H2 column**. The shorthand “above” also occurs in the pack’s 2015ApJ...813...99F summary, so that wording needs disambiguation. | Define the shielding column and its integration direction; reduce CO where that column is below the adopted threshold.

- SR-16 | high | science | “CO/H2 (disk), lower … 7.5e-5 per H” | The table mixes abundance denominators. For 2017ApJ...851..132C, the pack explicitly gives CO/H = 7.5e-5 and H/H2 = 2, implying **CO/H2 = 1.5e-4**, which is above 1e-4. | Move this value to the per-H row or convert it explicitly; require every abundance and shielding threshold to state its denominator.

- SR-17 | high | science | “Gas mass scales inversely with the assumed CO abundance” | This is conditional, rather than universal. The pack explicitly gives **gas surface density ∝ X_CO^-0.5** for 2025ApJ...984L..19Y. Optical depth, excitation and model structure can change the response. | Limit inverse scaling to the appropriate optically thin, fixed-excitation conversion; otherwise vary abundance and rerun the inference.

- SR-18 | medium | science | “constant mass loss gives rho ~ 1/r^2” | Steady spherical continuity gives **rho = Mdot/[4πr²v(r)]**. Constant velocity is also required for r^-2; 2016A&A...586A...5M explicitly includes acceleration from 3 to 14.3 km/s. | State the constant-velocity condition and retain v(r) when modelling an accelerating wind.

- SR-19 | medium | science | Grain-radius slope alternatives include “q = 11/6” | The pack gives q = 11/6 for 2018MNRAS.475.4924K without defining its distribution variable. It cannot safely be compared directly with dn/da ∝ a^-3.5. A mass-spectrum exponent 11/6 would reproduce that radius slope for compact grains. | Define the distribution variable and sign convention before comparing or converting exponents.

- SR-20 | medium | science | “Mean molecular weight … 2.37”; range “2.3–2.37” | The broad skill includes secondary debris gas, yet 2020MNRAS.497.2811K and 2020ApJ...892...99C explicitly use **mu = 14**. Applying 2.37 there changes pressure support and sound speeds. | Scope 2.37 to the adopted H2/He mixture; specify mu’s definition and choose it from the gas composition.

- SR-21 | medium | omission | “sample model visibilities at the observed uv points” | This alone does not specify primary-beam treatment, masks or the corresponding noise model. The 2025ApJ...990..145L excerpt fits a **primary-beam-corrected image** and flags non-Gaussian noise near the minor axis. | Require consistent primary-beam handling, spatial noise/weights and masks, alongside matched spectral sampling and imaging.

- SR-22 | medium | omission | Line-modelling workflow omits continuum oversubtraction/blocking | The limitation for 2025A&A...693A.101T explicitly warns that these effects can reduce line flux; 2017A&A...605A..21C excludes the inner region partly because of dust optical depth. | Check subtracted versus unsubtracted cubes, model dust attenuation where relevant, and document excluded opaque regions.

- SR-23 | medium | omission | Non-LTE selection focuses on density and code choice | The pack flags incomplete IR pumping (2015ApJ...814..143A), surrogate collision rates (2021A&A...655A..80D; 2017A&A...606A.125S), and possible **LVG failure in a torus** (2017A&A...605A..28D). | Add checks for pumping, included energy levels, collision partners/rate validity, and applicability of the LVG approximation.

- SR-24 | medium | omission | Settling models are offered for deriving turbulence without their physical prerequisites | 2025A&A...697A..64V assumes pressure maxima, fragmentation-limited grains and vertical turbulence comparable to or exceeding radial turbulence. It also fixes the grain distribution and adjusts stellar heating for several sources. | State these prerequisites and heating adjustments; qualify inferred turbulence when they are untested.

- SR-25 | medium | omission | Systematics checks omit flux calibration and retrieval identifiability | 2020ApJ...892...99C explicitly excludes calibration uncertainty from its MCMC; 2017Icar..286..289L tests ±5% calibration, a priori profiles and averaging kernels. Its HCN profile is non-unique, as is the single-line interpretation in 2014ApJ...795L..30C. | Include flux-scale sensitivity or nuisance parameters; for atmospheric retrievals, inspect averaging kernels and prior sensitivity before reporting resolved vertical structure.

- SR-26 | medium | usability | “Scale height … beta”; “h0 … psi” | The tables mix dimensional heights, aspect ratios and differently defined flaring exponents without equations. The pack includes H ∝ r^1.1 and aspect-ratio conventions with psi = 0.1 (2025A&A...697A..64V; 2020ApJ...895L..18B). | Define each parameterization explicitly; where h = H/r ∝ r^psi, state that the height exponent is beta = 1 + psi.

## Notes
The workflow covers many valuable validation and systematic-error checks.
The main repairs are attribution fidelity, abundance conventions and qualifications on transferable defaults.
Preserve ambiguities in the supplied cards explicitly rather than silently resolving them.