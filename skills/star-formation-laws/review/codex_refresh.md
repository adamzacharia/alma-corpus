# Codex refresh review: star-formation-laws
VERDICT: FIX
REFRESH: PARTIAL

## Findings

- RR-01 | medium | stale | “alpha_HCN = 10 in 5 papers”; table count “7” | The rebuilt pack additionally lists `2017ApJ...850..170O: M_dense = 10 L'_HCN(1-0)`. Together with the five listed alpha_HCN = 10 papers and the separate 14 and 15 cases, this gives six and eight unique papers respectively. | Update Step 3, the count table and parameters.md to include this paper.

- RR-02 | medium | stale | S/N-cut count “9 (pack lines)” | The pack contains at least ten distinct sampling-cut papers: 2017ApJ...851...18L, 2019ApJ...884L..33L, 2021MNRAS.500.3802H, 2022MNRAS.514.5035L, 2024MNRAS.535.1533B, 2024ApJ...972..147C, 2022A&A...659A..46B, 2020MNRAS.496.5243H, 2023A&A...678A.183N and 2024ApJ...968...15L. | Recount using an explicit definition of eligible detection cuts and publish the counted bibcodes.

- RR-03 | medium | attribution | “0.90 to 1.23”; “0.87 to 0.73”; “CIGALE … 2024A&A...692A.215C” | The supplied rebuilt pack supports the alpha_CO prescriptions for 2024ApJ...976...88L and 2025ApJ...995..151Y, but supplies neither quoted slope comparison. Its entries for 2024A&A...692A.215C do not identify CIGALE. Aggregate software frequencies cannot establish individual assignments. | Restore verified paper-specific excerpts for these carried-over results and software assignments, or remove their unsupported specificity.

- RR-04 | medium | lost-fix | Step 2’s “5.53e-42” H-alpha coefficient | SR-22 required missing units to be marked explicitly. The pack’s 2024ApJ...976...88L line gives the coefficient without luminosity units; Step 2 implicitly inherits erg/s from the preceding calibration, while parameters.md correctly flags the omission. | Mark its luminosity units as absent from the pack and require paper verification before application; apply the same treatment to the 0.95e-10 IR coefficient.

- RR-05 | medium | science | “intrinsic Halpha/Paa 0.116” | parameters.md reproduces a suspect pack label from 2020A&A...643A..78M. The pack separately gives Halpha/Paalpha = 8.6 for 2026A&A...707A.144S; 0.116 is approximately its reciprocal. Both cannot describe the same intrinsic ratio. | Flag the source inconsistency; verify the original definition, then label 0.116 as Paalpha/Halpha if confirmed.

- RR-06 | medium | lost-fix | “samples with line-luminosity upper limits … are truncated” | This reintroduces the censoring/selection confusion addressed by SR-11. For 2020A&A...641A.155V, the pack states both an L_IR ≥ 10^8.5 Lsun selection and retained Flag=0.5 upper limits. Upper limits alone do not establish truncation. | Attribute truncation to the actual selection boundaries, and describe retained line upper limits separately as censoring.

- RR-07 | medium | science | “either refit the inverse relation with gas as the dependent variable” | With intrinsic scatter, inverse and forward conditional regressions estimate different relations; reciprocating the inverse slope does not generally recover the stated forward KS slope. | Prefer a generative likelihood handling gas-axis censoring, or explicitly report the inverse estimand and assumptions needed for conversion.

- RR-08 | medium | science | “Inclination: cos i …; 1/cos i …” | The pack repeats the 1/cos(i) convention for 2021MNRAS.500.3802H without resolving its application. Presenting both factors as interchangeable surface-density corrections is unsafe: thin-disk area deprojection uses A_face = A_proj/cos(i), hence Sigma_face = Sigma_proj cos(i). | Identify the corrected quantity for each convention and distinguish area, radius and surface-density corrections.

- RR-09 | medium | omission | High-redshift dust SFR and gas comparisons omit CMB checks | The pack explicitly includes CMB corrections in 2022ApJ...930...32C and 2020ApJ...902..112B, and gives the [CI] background-contrast correction at T_CMB = 21.5 K in 2021ApJ...921...97J. Negligibility is demonstrated specifically for SDP.81 in 2020MNRAS.494.5542R. | Add a check that both axes use appropriate CMB treatment; require justification when effects are neglected.

- RR-10 | medium | omission | “Swap the SFR tracer”; H40alpha calibration | Tracer timescales and applicability are missing. The pack’s 2020MNRAS.492.3194S assumes unchanged SF over 100 Myr to compare H-alpha and FIR; 2025ApJ...979..217S assumes continuous SF over 100 Myr. The H40alpha calibration requires a well-sampled IMF and steady massive-star formation at SFR ≥ 5 Msun/Myr (2022MNRAS.510.4998Z). | State these assumptions alongside tracer comparisons and include the H40alpha applicability threshold in parameters.md.

- RR-11 | medium | broken-edit | Sampling setups “range … to” the older endpoints | Step 4 and the defaults table omit larger samples already added to parameters.md: 1.5 kpc hexagons (2025A&A...700A.123M) and aperture diameters/boxes reaching 6.4 kpc (2023A&A...678A.183N), both explicit in the rebuilt pack. | Refresh the sampling ranges and separate pixel size, aperture diameter, spacing and beam resolution; do not substitute aperture maxima for beam resolution.

- RR-12 | low | omission | “SFE = … 1/t_dep” | The pack also uses observational “SFE” = L_IR/L'_CO in 2024ApJ...964...95S. That luminosity ratio is a proxy requiring SFR and gas conversions before inversion into a depletion time. | Add a definition-and-units check distinguishing physical SFE from luminosity-ratio proxies.

- RR-13 | low | length | SKILL.md exceeds approximately 300 lines | Long calibration inventories, software examples and repeated paper-specific results obscure the actionable workflow. | Move extended calibration examples, numerical inventories and software-use details to references/parameters.md; retain the workflow and essential safeguards.

## Notes
The description’s 414-paper count and listed software aggregate frequencies match the rebuilt pack.
Missing excerpt support does not establish that a paper’s claim is false; it prevents verification against this supplied pack.