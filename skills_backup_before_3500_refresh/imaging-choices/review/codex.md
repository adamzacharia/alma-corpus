# Codex review: imaging-choices
VERDICT: FIX

## Findings

- SR-01 | high | attribution | “key-parameter list … 2012–2018”; “390 papers”; “432 papers listed” | The supplied key-parameter section includes 2019–2026 entries, including 2026A&A...705A.198M, and ends with “... 1236 more.” The stated chronological subset and its counting denominator are not established by the pack. | Remove the claimed period and frequency tables, or supply a reproducible list of included bibcodes, exclusions and counting rules.

- SR-02 | medium | attribution | “Pack aggregates” software counts | The software aggregate explicitly gives `tclean: 71`, `uvcontsub: 11`, `casa clean: 8`, `clean: 7`, `imfit: 6`, `casa imfit: 8`, and `feather: 5`; the skill reports different values. The pack gives `miriad: 27`, without the claimed 20/7 spelling split. | Copy the aggregate labels and counts exactly; do not imply that overlapping software labels count distinct papers.

- SR-03 | medium | attribution | “7 at about 2x rms … whole pack” | At least 11 distinct supplied entries support approximately 2σ cleaning: the six bibcodes in Step 7, plus 2017ApJ...846..108C, 2018Sci...362.1034D, 2018Icar..307..380T, 2024ApJ...962....1S and 2025ApJ...990L..31B. The claimed seventh example, 2015ApJ...814...22E, has no threshold evidence here. | Recount unique supported papers and remove the unsupported example; establish the denominator before calling this the most common threshold.

- SR-04 | medium | attribution | “Range seen 0.5 … to 4 sigma”; taper, cell and iteration ranges | Supplied counterexamples include cleaning to ~5σ (2025A&A...697A..64V), a 0.010″ taper (2021A&A...654A..35B), 18.75 kλ tapering (2024ApJ...977..198L), 1.5 Mλ tapering (2023PASJ...75..424O), 0.0037″ cells (2024ApJ...961..228S), 1″ pixels (2020ApJ...899...10T), and four million iterations (2018ApJ...867..166S). | Correct the ranges or label them explicitly as selected examples rather than pack-wide extrema.

- SR-05 | medium | attribution | “Hogbom; natural” for both threshold-table examples | `references/parameters.md` labels 2017ApJ...839...43O natural, but its pack entry explicitly states “Briggs parameter 0.5.” | Assign robust 0.5 to that paper and separate the two papers’ weighting descriptions.

- SR-06 | medium | attribution | “off-topic papers … excluded from … citations” | Step 3 nevertheless cites 2016ApJ...821..112K for a common 4.2″×2.1″ beam. The supplied entry is only a title identifying **SMA observations**; it supplies neither that beam nor an ALMA imaging method. | Remove this example or clearly identify it as external-facility context with additional evidence.

- SR-07 | high | attribution | Numerous specific settings attributed to title-only entries | The pack supplies no relevant methods for, among others, the robust choices attributed to 2016ApJ...823...68S and 2016ApJ...828...46A; beam matching in 2018A&A...619A.161C; 27–1310 kλ in 2018A&A...616A..56A; >160 kλ in 2017A&A...597A..32V; the dirty-imaging claims for 2016ApJ...823L..10W, 2016ApJ...833...12R and 2016ApJ...819...82S; and the clipping percentages in 2017ApJ...851...18L. Their titles establish no such settings. | Remove these attributions or obtain supporting methods evidence. Audit every remaining title-only citation using the same rule.

- SR-08 | medium | attribution | “Values copied from the evidence pack” | The supplied pack does not contain the tabulated scales for 2017ApJ...836..223W, 2017ApJ...840...60B, 2017ApJ...837L..29H or 2016ApJ...831L..12K; nor the thresholds attributed to 2015ApJ...814...22E, 2018A&A...620A.115B, 2017ApJ...835...98U, 2017ApJ...843L..35W or 2018A&A...619A..39F. | Delete unsupported parameter rows or provide their evidence; presence in the bibliography is insufficient.

- SR-09 | medium | unsupported | “usually get different weighting”; “reverse … rare”; “most line cubes”; “mostly European groups” | The pack provides examples, not the classified denominators needed for these prevalence claims or evidence for the geographic characterization. Likewise, it supplies no `npixels=2` setting. | Use “examples include,” remove geographic speculation, and remove unsupported parameter defaults.

- SR-10 | high | science | “Taper … 0.27″ … (2020MNRAS.493.4294B)” | The pack specifically describes this as “Gaussian 0.27″ FWHM (**convolution of natural maps**).” Presenting it as a visibility-taper setting conflates two different operations. | Describe it as image smoothing; do not translate it into a `tclean uvtaper` value without additional evidence.

- SR-11 | high | science | “share uv range **or** a common restoring beam” | Neither condition alone establishes comparable spatial response: equal uv limits can yield different beams, while equal restoring beams can conceal different spatial filtering. The pack explicitly distinguishes missing extended flux (2020ApJ...898..146M) from angular-resolution matching. | Require a common final beam and assess comparable uv sampling and recoverable scales; also match spectral resolution for channel-based line ratios.

- SR-12 | medium | science | “Taper … to recover extended flux” | This needs an explicit boundary: tapering can reveal sampled low-surface-brightness emission but cannot supply missing short spacings. The pack records missing flux despite 7m+12m multiscale imaging (2016PASJ...68...88K) and model-dependent extrapolation to zero spacing (2020ApJ...898..146M). | State this distinction and require short-spacing data or a qualified model-based estimate when total flux remains unsampled.

- SR-13 | medium | science | “Clark is the older equivalent” | Clark and Högbom are distinct CLEAN implementations, not interchangeable names or an old/current pair. The pack explicitly documents Clark in modern `tclean` imaging (2023PSJ.....4..142C). | Describe Clark as another point-component CLEAN algorithm and retain its actual task/deconvolver attribution.

- SR-14 | medium | science | “Widths comparable to the beam are upper limits” | This overgeneralizes the cited limitation. 2020ApJ...888L..28S says the actual width “may be narrower”; 2018MNRAS.475.4924K reports fitted sub-beam vertical structure cautiously. Beam comparability alone does not make every fitted intrinsic width an upper limit. | Distinguish observed widths, deconvolved widths and unresolved limits; require uncertainty and model validation for marginally resolved measurements.

- SR-15 | medium | omission | “`niter` … until threshold” | Reaching an iteration limit does not establish that the requested threshold was reached. The pack explicitly says some combined 12CO channels were not cleaned to threshold (2019A&A...631A..64B). | Inspect stopping reasons and channel residuals; record channels that remain above threshold.

- SR-16 | medium | omission | “Keplerian masks for disk lines” | The cited ARKS procedure assumes gas is co-located with dust and near-Keplerian (2026A&A...705A.198M). Those assumptions are missing from the recommendation. | State the geometry and kinematic priors; compare with a broader mask and inspect excluded emission before interpreting non-detections or unusual velocities.

- SR-17 | medium | omission | “mtmfs … spectral index”; matched-band checks | The pack includes intensity selection above 5σ and an absolute spectral-index uncertainty of ~0.4 from flux calibration (2018ApJ...852..122H). Neither safeguard accompanies the spectral-index guidance. | Require an intensity/uncertainty mask and propagate inter-band flux-scale uncertainty separately from image noise.

- SR-18 | medium | omission | Flux measurements and residual verification | Residual scaling is explicitly present in 2018ApJ...867..166S, and JvM factors are listed for 2024ApJ...974..102S. The skill omits the different beam units of restored CLEAN components and residuals, which can bias fluxes. | Add a check for residual-flux significance and dirty/clean beam normalization; document whether residual scaling is needed and applied.

- SR-19 | medium | omission | “Run the checks” before trusting measurements | The pack flags neglected beam correlations (2020MNRAS.496.4061D), correlated noise (2019ApJ...881...10B), and costs requiring independent samples (2023PSJ.....4..142C). No corresponding uncertainty check appears. | Account for correlated pixels in aperture errors and image-plane likelihoods; do not count pixels as independent measurements.

- SR-20 | medium | usability | Beam/arcsecond scale recipes; historical `outertaper` | An agent is never explicitly told that CASA `tclean scales` uses pixels, or how historical angular scales and `clean outertaper` map to current inputs. Direct copying can change scales by large factors or fail. | Give the conversion `scale_pixels = scale_angle / cell_angle`, a valid `uvtaper` example, and distinguish taper input width from the achieved restoring beam.

## Notes
The goal-based structure and many detailed-excerpt summaries are useful.
The main defects are unsupported precision, incorrect counting scope, and unqualified operational shortcuts.
A bibliography entry is not methods evidence; distinguish unsupported claims from claims contradicted by supplied settings.