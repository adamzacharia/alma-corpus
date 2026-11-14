# Codex review: core-extraction-cmf
VERDICT: FIX

## Findings

- SR-01 | high | attribution | “a single 20 K is the most common default … 2020ApJS..251...14H” | That card uses 20 K for completeness simulations; step 4 derives catalog properties using Herschel temperatures. Its quoted factor-two systematic uncertainty comes from opacity, not temperature. | Separate simulation and catalog temperatures; correct the temperature count and uncertainty attribution.

- SR-02 | medium | attribution | “v1.140127 with default parameters … 2018A&A...618L...5N” | The pack supports defaults and a 2″ maximum structure size for 2018A&A...616L..10F. It supplies neither the version nor defaults for 2018A&A...618L...5N. | Retain the supported F-paper settings; mark the other version/settings as unavailable.

- SR-03 | medium | attribution | “kappa … mu = 2.33 … 2018A&A...618L...5N”; “0.899 … gas-to-dust 150”; “0.0060–0.01 (gas)” | Those N-paper values, the 2024A&A...690A.185W opacity/ratio, and the 0.0060 endpoint attributed through 2018ApJ...855L..25K are absent from the pack. | Remove these attributions and unsupported range endpoints. Retain 2019ApJ...884...48C as the documented 0.01 cm²/g example.

- SR-04 | medium | attribution | “PPMAP maps”; “temperature set by clump L/M”; “Hi-GAL temperatures changed results by ~5–10%” | The pack does not document these temperature prescriptions/results for 2018A&A...618L...5N, 2024A&A...690A.185W or 2026A&A...705A.100E. It also does not establish parent-clump temperatures for 2018A&A...616L..10F. | Remove or mark these claims as unsupported by this pack.

- SR-05 | medium | attribution | “uv-tapers from 100 to 200 klambda”; “4 sigma … 2 sigma (card)” | The supplied 2021ApJ...907L..15S entry contains neither taper values nor extraction thresholds. | Remove these numerical settings and their contribution to frequency counts.

- SR-06 | medium | attribution | “same split in 2019ApJ...871..185L”; “imfit … 2020ApJ...896..110L” | The pack does not establish that PB workflow for the former, or imfit, finder seeding, extra >5σ sources, or 40 pixels ≈ one beam for the latter. | Retain only their documented settings; label the remaining details unavailable.

- SR-07 | medium | attribution | “2026A&A...705A.100E … 90% flux 0.95 mJy (card)” | No such completeness value appears in the supplied pack; its limitation only says sensitivity can make core counts lower limits. | Remove the numerical limit.

- SR-08 | medium | attribution | “clumpfind … Range seen: 2–8 sigma / 1–4 sigma” | This table claims to count on-topic core papers. The documented 8σ/4σ settings belong to GMC extraction in 2017PASJ...69...18T; the 1σ increment belongs to the companion search in 2018PASJ...70...36I. | Recompute the range using an explicit on-topic paper list, separating absolute-flux settings.

- SR-09 | medium | attribution | “min_npix … 1 beam: 4 … fixed 5–74 px: 4” | The pack gives five explicit fixed counts: 15, 40, 60, 5 and 74 pixels. Reclassifying 40 pixels as one beam requires a conversion absent from 2020ApJ...896..110L. | Count supported pixel and beam-area settings separately; publish the membership behind each count.

- SR-10 | medium | attribution | “Completeness injections … 5”; “binned/cumulative: 4” | Four cited papers explicitly describe injection recovery; 2018ApJ...853..160C supplies flux/number corrections without an injection method here. Likewise, 2020A&A...635A...2S states a power-law fit without establishing a binned/cumulative implementation. | Distinguish documented methods from unspecified ones and revise the counts.

- SR-11 | high | attribution | “Reported high-mass slope (dN/dlogM) … 0.64–1.6 … 6” | The pack explicitly labels 2020ApJ...890...76N as dN/dM ∝ M^−1.33 and 2019ApJ...872..121U as dN/dM ∝ M^−α, including α = 1.48. These cannot be pooled unchanged with logarithmic slopes. | Tabulate native conventions and convert explicitly: the quoted examples become logarithmic exponents −0.33 and −0.48. Do not infer a convention correction from resemblance to Salpeter.

- SR-12 | medium | attribution | “clumpfind there is a peak finder only … 2017A&A...604A.117C” | That card describes 3D cube segmentation and reassembly of clumps into lens images, not peak finding alone. | Explain the different physical scale and lens reconstruction requirement without mischaracterizing the algorithm’s role.

- SR-13 | low | unsupported | “papers often apply [corrections] loosely or not at all”; “The modern default” | The cited S and B cards document bias/completeness corrections. The regex-selected pack does not establish community-wide adoption or frequency of inadequate correction. | Replace these generalizations with specific, supported examples.

- SR-14 | high | science | “Line cubes” followed by “Convert to mass. Optically thin modified blackbody” | The workflow includes line-selected cores but provides only a dust-continuum mass conversion. The 2019ApJ...872..121U card instead flags abundance uncertainty up to a factor of two and missing excitation-assignment details. | Branch explicitly: use dust masses from a matched continuum map, or document a separate line excitation, opacity, abundance and column-to-mass calculation.

- SR-15 | high | usability | “set … min_npix in units of … beam area”; “3 x theta_beam” | `min_npix` requires a pixel/voxel count. Beam area needs conversion, while the 2018ApJ...856..147O wording is dimensionally ambiguous and does not establish “3 beams.” | Give the beam-area-to-pixel conversion for 2D maps, distinguish voxel counts for cubes, and mark the ambiguous setting unresolved.

- SR-16 | medium | science | “with N^1/2 weights” | The 2016ApJ...833..209O excerpt identifies √N as the counting uncertainty. Passing √N as a least-squares weight reverses the intended weighting. | State σ_N = √N and specify whether the fitting API expects uncertainties, inverse uncertainties or inverse variances.

- SR-17 | medium | science | “M_vir = 210 r dv²” | Units and linewidth definition are missing; substituting velocity dispersion for FWHM changes the result by approximately 5.55. | Write M_vir/M☉ = 210(R/pc)(Δv_FWHM/[km s⁻¹])². Define σ separately in the 5σ²R/G expression.

- SR-18 | medium | attribution | “A 3 sigma mass limit … is lower than the 90% completeness mass” | The 2020ApJ...890...76N card supplies sensitivity limits only, with no measured 90% completeness comparison. For 2020ApJ...894L..14L, the pack distinguishes ~2 M☉ at the 30% PB selection from ~5 M☉ with the >5σ selection, specifically for the 20 km/s cloud. | Remove the unsupported comparison and attach completeness limits to their cloud and selection criteria.

- SR-19 | medium | omission | “Optional: virial state” | The cited 2020ApJ...894...87C card requires thermal-corrected dispersion, uses a = 5/4 and α_cr = 2a, and reports factor-2.5 systematic uncertainty that prevents a firm virial classification. These qualifications are missing. | Add those assumptions and uncertainty limits; also state the magnetic-field omission documented by 2016ApJ...833..209O.

- SR-20 | medium | omission | “Always report … mass formula inputs” | The pack repeatedly flags missing flux calibration/scale uncertainty, CASA/pipeline versions and imaging settings. The skill records only part of this provenance and omits a flux-scale uncertainty requirement. | Require calibration uncertainty and its propagation, processing versions, and relevant imaging settings.

- SR-21 | medium | usability | “Flux: sum within the leaf/clump” | A literal sum of Jy/beam pixels is not integrated flux; the pack also includes MJy/sr maps, which need a different conversion. | Specify unit-aware integration: multiply Jy/beam sums by pixel area/beam area, or surface-brightness sums by pixel solid angle.

## Notes
The main extraction examples and software aggregate counts are largely faithful.
Several details labelled “card” are absent from the supplied evidence and cannot be verified here.
Preserve native slope conventions and distinguish empirical examples from recommended defaults.