# Review task: a REFRESHED ALMA agent skill against its rebuilt evidence pack

The skill below was first written from a ~1,600-paper corpus, reviewed, and fixed (the fix record is the
RECONCILIATION section). The corpus then grew to ~3,500 papers, the evidence pack was rebuilt, and a writer began
updating the skill to the new pack. The writer may have been cut off before finishing, so expect a mix: some
counts and ranges updated to the new pack, others still at the old values, and possibly a half-edited section.

Apply every check from the standard review (attribution, unsupported practice, scientific correctness, omissions,
usability: see below), and also these refresh checks:

A. **Stale or mixed numbers.** Paper counts, "used in N papers", common choices and ranges that do not match the
   NEW pack aggregates (the old corpus was about half the size, so old counts are usually roughly half). The
   description line's "Built from N ALMA papers" must match the pack.
B. **Lost fixes.** Any item the RECONCILIATION marks FIXED that the current skill has undone or reintroduced.
C. **Broken edits.** Duplicated sections, contradictory statements left from an unfinished rewrite, tables whose
   rows disagree with the text, dangling references.
D. **Length.** Over ~300 lines is a low-severity usability finding; say what could move to references/parameters.md.

Standard checks, in this order:
1. Attribution: every number, range, default, software attribution and "papers do X" claim that cites bibcodes is
   supported by the pack for those bibcodes; counts match the pack aggregates.
2. Unsupported practice presented as literature practice.
3. Scientific correctness: formulas, units, CASA task/parameter names and semantics, unsafe advice.
4. Omissions: important pitfalls, assumptions or validation checks clearly present in the pack but missing.
5. Usability: anything an agent would misread or could not act on.

You have no file access: everything you need is in this message.

Output format (Markdown, nothing else):

```
# Codex refresh review: <slug>
VERDICT: CLEAN | FIX
REFRESH: COMPLETE | PARTIAL   (PARTIAL if any section still carries old-pack numbers or an unfinished edit)
## Findings
- RR-01 | high|medium|low | <stale|lost-fix|broken-edit|length|attribution|unsupported|science|omission|usability> | <the claim, quoted briefly> | <problem, citing the pack line or bibcode> | <concrete fix>
- RR-02 | ...
## Notes
<at most 5 lines>
```

Use `VERDICT: CLEAN` only when there are no high or medium findings. Be specific and terse; do not restate the
skill. Do not invent pack content: when you say the pack contradicts a claim, cite the pack line.

=== SKILL.md (dust-continuum-mass) ===
---
name: alma-dust-continuum-mass
description: "Turn ALMA (sub)mm continuum flux into dust mass, gas mass, column density or an upper limit, with an opacity law, dust temperature, gas-to-dust ratio and distance chosen the way published ALMA papers choose them. Use when converting a continuum flux or brightness to a disk, core, clump, envelope, debris belt, circumstellar shell or galaxy dust/gas mass, when checking someone else's mass, or when stating mass upper limits for non-detections. Built from 915 ALMA papers (2012-2026)."
---

# Dust and gas masses from (sub)mm continuum

Measures the mass of emitting dust from a continuum flux density under the optically thin, isothermal assumption, then
(optionally) a gas mass through a gas-to-dust ratio. The answer is only as good as three assumed numbers: opacity
kappa_nu, dust temperature T_d, and gas-to-dust ratio. The two mistakes that matter most: (1) mixing an opacity quoted
**per gram of gas** with one quoted **per gram of dust** (a factor 100 error), and (2) applying the thin formula to
emission that is partly optically thick, which only gives a **lower limit** (2018A&A...619A.161C, 2015A&A...573L...1O,
2014ApJ...783L..13P). For disks, 2025A&A...693A.286S notes that optical depth and opacity effects can make thin dust
masses too low by up to a factor of about 7.

> Always report kappa_nu (with its reference frequency, beta and whether it is per dust or per gas mass),
> T_d, distance, gas-to-dust ratio, and the flux you used. A mass without these is not reproducible.

## When to use

- A detected continuum source (disk, core, clump, envelope, belt, shell, galaxy) and you need M_dust, M_gas, N(H2) or
  n(H2) from its flux or surface brightness.
- A non-detection: convert an n-sigma flux limit to a mass limit (3 sigma is the usual choice: 2015A&A...583A..66H,
  2019ApJ...875L...9W, 2017ApJ...842....8M; 2 sigma in 2024ApJ...963....1O; 5 x rms of a tapered image in
  2020MNRAS.499.5241C). Such a limit is an optically thin, assumed-size limit only (step 8).
- Population work: dust-mass distributions and M_dust vs M_star relations for disk surveys (2016ApJ...828...46A,
  2020A&A...633A.114S, 2025A&A...693A.286S, 2014ApJ...787...42C).
- Core and clump fragmentation studies needing core masses, densities and virial parameters (2020ApJ...894L..14L,
  2020ApJ...890...76N, 2019ApJ...871..185L, 2024ApJS..270....9X).
- Sanity-checking a mass quoted in a paper or produced by another tool.

## When not to use

| Situation | Use instead |
|---|---|
| Emission likely optically thick (bright compact disks, hot cores, inner envelopes, T_b close to T_d) | Radiative transfer model (RADMC-3D, MCFOST, DALI) or state the result as a lower limit (2015A&A...573L...1O, 2017A&A...604A...6S, 2026ApJ..1003..219W) |
| Disk structure, settling, gaps, gas and dust together | Full disk modelling: RADMC-3D (34 + 3 under "radmc3d" in the pack aggregates), DALI (23), MCFOST (22); a ProDiMo SED grid in 2025A&A...694A.295P; an optool/DSHARP RT grid in 2025A&A...696A.232G |
| High-z galaxy with good FIR photometry | SED fit (MAGPHYS 15, CIGALE 13, BAGPIPES 3 in the aggregates; STARDUST in 2024A&A...690A..55S) and use its dust mass, after reconciling its dust composition and opacity with yours (2025A&A...694A..82S divides CIGALE masses by 2; 2021ApJ...908...15S finds MAGPHYS masses a factor two below Draine and Li based ones), with the single-band mass as a cross-check |
| Gas mass where CO is detected and alpha_CO is defensible | CO-based mass, then compare with the dust route (2021A&A...652A..98G, 2018Sci...362.1034D); [CI] is another check (2021A&A...652A..66P) |
| Continuum dominated by free-free, synchrotron or stellar photosphere | Decompose first (SED with radio data); the dust formula on raw flux overestimates mass (2016A&A...591A..73G, 2017MNRAS.468L..87C, 2025A&A...694A.295P) |
| Extended emission resolved out by the interferometer | Combine with ACA/TP or single-dish, or quote the mass as a lower limit (2014ApJ...787...48X, 2024ApJ...968L..19F, 2017ApJ...835..213P) |

## Steps

1. **Define the emitting object and regime.** Decide the aperture or component (whole disk, ring, crescent, core,
   clump, belt, galaxy). Note whether you need dust mass, gas mass, column density or volume density; each needs extra
   inputs (gas-to-dust, mu, a size or thickness). Core extraction examples: astrodendro (2020ApJ...894L..14L),
   Clumpfind (2020ApJ...890...76N), both (2019ApJ...871..185L); 5 vs 3 papers in the aggregates, too few to rank. Size
   conventions differ: r = (A/pi)^0.5 (2020ApJ...894L..14L), geometric mean of Clumpfind semi-axes
   (2020ApJ...890...76N), R = (FWHM_maj FWHM_min)^0.5 / 2 x D (2024ApJ...961L..35M); state yours.
2. **Build a clean continuum flux.**
   - Image line-free continuum (CASA `tclean`, or GILDAS MAPPING; 2024A&A...691A.180F, 2021A&A...652A..98G). The cards
     rarely state which channels were line-free (more than 100 card flags across wordings in the pack), so record
     yours. Line contamination of continuum is a real limitation (2013ApJ...774L...7M).
   - Apply primary-beam correction before measuring flux (20 card flags for unstated PB-correction details).
   - Measure the flux: aperture inside a contour (5 sigma contour and 50% PB response in 2019ApJ...874...89C), 2D
     Gaussian with `imfit` (5 + 4 papers under two labels), or a uv-plane fit (`lmfit` in 2025ApJ...986L..22R;
     `uvmodelfit` check in 2024A&A...682A..61C).
   - Use the integrated flux density (Jy) for a mass. A peak in Jy/beam is a mass per beam; for surface brightness
     divide by the beam solid angle, Omega_beam = pi theta_maj theta_min / (4 ln 2) (general practice;
     2021ApJ...907...94C writes the same form). Take the noise locally from the PB-corrected map, not one global rms:
     noise rises toward the PB edge and can be enhanced locally (gap rms in 2024ApJ...974..102S).
   - Remove non-dust flux: stellar photosphere (F_dust = F_cen - F_star in 2013ApJ...762L..21M), free-free or
     synchrotron (2017MNRAS.468L..87C, 2016ApJ...821L..16C, 2016A&A...591A..73G; spectral indices 4.0 dust vs -0.15
     free-free in 2024ApJ...967..133S), compact companions or central sources by Gaussian subtraction
     (2014ApJ...796....1T).
3. **Choose the dust temperature** (Parameter table). The pack shows examples of each approach, not a ranking. My
   guidance (not a literature census): prefer a temperature measured for the same emitting component (SED fit, NH3 or
   line rotational temperature), then a luminosity or radiative-equilibrium scaling, then a fixed fiducial, and check
   the temperature applies to the dust you are weighing. Examples: SED fit with SciPy least squares
   (2020ApJ...890...76N), T_d from gas temperature (2014ApJ...797...27F, 2024ApJ...961L..35M from NH3; CH3OH
   excitation temperature in 2025ApJ...991...59B, 2026ApJ..1003..219W), luminosity scaling for disks
   (2016ApJ...819..102V, 2021A&A...653A..46V, 2025A&A...693A.286S), class by L/M with Monte Carlo ranges
   (2025A&A...701A.219N), radiative equilibrium at the belt radius for debris disks (2017ApJ...842....8M,
   2025A&A...693A.151M).
4. **Choose the opacity law** kappa_nu = kappa_0 (nu/nu_0)^beta. Pick the convention of the subfield you will be
   compared with (Parameter table, `references/parameters.md`), and check whether kappa_0 is per gram of dust or per
   gram of gas. Grain-size-dependent opacities (optool and dsharp_opac, 4 papers each in the aggregates) change the
   answer: 2021ApJ...923..121Y runs DSHARP and 2.3 (nu/230 GHz)^0.4 side by side; 2024ApJ...974..102S brackets 100 um
   vs 1 mm grains.
5. **Compute the mass** with the full Planck function (general practice; the Rayleigh-Jeans limit is poor at 20 K and
   230 GHz, where h nu / k is about 11 K; some papers still use RJ, e.g. 2024ApJ...974..257Z, 2025A&A...698A.165A):

   ```
   M_dust = F_nu d^2 / (kappa_nu B_nu(T_d))                       # optically thin, isothermal
   M_gas  = (gas-to-dust) x M_dust                                # or use kappa per gram of gas directly
   N(H2)  = I_nu / (mu_H2 m_H kappa_nu,gas B_nu(T_d))             # I_nu in surface brightness per sr
   n(H2)  = M_gas / ((4/3) pi r^3 mu_H2 m_H)                      # spherical mean, as in 2020ApJ...894L..14L
   ```

   mu_H2 is the mean mass per H2 molecule (2.8; 2019A&A...628A..27B, 2020ApJ...890...76N); do not substitute a mean
   mass per free particle (about 2.33 to 2.37, general practice) here. A third convention counts hydrogen nuclei: mu_H
   = 1.41 with a dust-to-gas ratio Z (2023MNRAS.525.2229M, 2026ApJ...998..277M); that gives N_H, not N(H2), so do not
   mix it with the mu_H2 form. The n(H2) line assumes a sphere of radius r (2020ApJ...894L..14L uses r = (A/pi)^0.5
   from the astrodendro area). Say so, and propagate the geometry: 2019ApJ...871..185L uses a flattened structure with
   an assumed thickness profile, and 2014ApJ...795L..25R quotes density as a lower limit because the core is
   unresolved. For an unresolved source, r is only an upper bound, so n(H2) is a lower bound.

   Sanity number: with kappa = 2.3 cm2/g at 1.3 mm and T_d = 20 K, 1 mJy at 140 pc is about 0.57 Earth masses of dust;
   2015A&A...583A..66H uses exactly M_dust = 0.566 [F_1300/mJy (d/140 pc)^2] M_earth. For high-z sources (general
   practice; check the convention of the paper you compare with):

   ```
   nu_rest = (1+z) nu_obs ;  T_CMB(z) = 2.725 K (1+z)
   M_dust  = F_nu,obs D_L^2 / [ (1+z) kappa(nu_rest) ( B_nu_rest(T_d(z)) - B_nu_rest(T_CMB(z)) ) ]
   ```

   The B(T_CMB) term is the contrast correction (dust is seen against the CMB). CMB heating is a separate correction
   that raises T_d(z) for cold dust; apply it only if your T_d is a z = 0 value. Size of the effect:
   2025A&A...693A.190J gives a CMB flux correction of about 1.03 at z ~ 1 rising to about 1.31 at z ~ 6, and heating
   of about 3% at z = 6; 2021A&A...652A..66P ignores heating (< 2%) at z = 6. CMB-corrected examples:
   2016ApJ...822...80S, 2017Natur.545..457D, 2025ApJ...993L..40S; 2020ApJ...892...66M uses the Kovacs-style thin
   equation with CMB correction. For lensed sources, use the intrinsic flux (divide by the magnification mu_L) and say
   which magnification applies to the dust: 2016ApJ...822...80S calls a single magnification a simplification, and
   2021ApJ...917...99Y uses mu = 4.53 for the continuum but 3.44 for [CII].
6. **Check optical depth.** Compare the peak intensity with what the dust at T_d would emit if thick. For an
   absorption-only isothermal slab with beam filling factor f and background T_bg (general practice, no scattering):

   ```
   tau = -ln[ 1 - Delta I_nu / ( f (B_nu(T_d) - B_nu(T_bg)) ) ]     # Delta I_nu = background-subtracted intensity
   ```

   Use the Planck intensity, not the Rayleigh-Jeans T_b ratio (RJ is poor at these T and nu). 2018A&A...619A.161C did
   a brightness-based check and found the crescent only marginally thin (tau about 0.4 even with T_d raised by 1.5),
   so called its masses lower limits. Where T_b exceeds the assumed T_d the emission is thick (2025ApJ...988..106H
   sets tau = 4 there). A low beam-averaged brightness does **not** prove the emission is thin: beam dilution (f << 1)
   or scattering can suppress the observed intensity of thick dust. Check the source is resolved before trusting f = 1
   (2016Sci...353.1519P flags beam dilution), and exclude or model scattering (2020A&A...644A..11L drops pixels with
   scattering or thick emission; 2019MNRAS.488.1005P includes anisotropic scattering in RT). If tau is not small,
   report a lower limit or move to RT modelling.
7. **Convert to gas, if needed.** Gas-to-dust 100 is the default (Parameter table); scale with metallicity for
   galaxies and the Magellanic Clouds (2020ApJ...892...66M, 2020ApJ...891..164S, 2017MNRAS.469.4683C; delta_GDR
   proportional to Z^-0.85 normalised to 100 at solar in 2021A&A...655A..42S; 100 x 10^(Z - Z_sun) in
   2020MNRAS.498.4109J). Say which gas phases the result covers: 2025ApJ...993L..40S ignores atomic gas,
   2024A&A...686A..64M includes it, 2021A&A...652A..66P takes 75% as molecular. A galaxy shortcut skips kappa and
   gas-to-dust: M_gas = L_850 / alpha_850 with T_d = 25 K (2024A&A...691A.248L, 2022A&A...664A..63X; values in
   `references/parameters.md`). Cross-check with CO where possible (2021A&A...652A..98G).
8. **Handle limits and samples.** Convert n-sigma limits with the same kappa and T. State the source size assumed: a
   point-source limit (2017ApJ...842....8M) uses the local rms per beam, while an extended source needs an aperture or
   model-dependent limit that grows with the area. A thin mass limit is conditional: compact optically thick material
   can hide more mass. 2017ApJ...842....8M converts its Fomalhaut b flux limit to a thin dust-mass limit or, if thick,
   to a clump-size limit; 2019MNRAS.488.1005P uses size-dependent RT models; 2020MNRAS.498.1319M assumes a disc larger
   than about 0.1 au because a smaller thick disc could hide more mass. Do not call a thin limit an upper bound on
   total mass without an optical-depth and size assumption. Other conventions: 3 sigma plus any positive flux
   (2016ApJ...827..142B), stacked limits (2025ApJ...990L..61C), SED non-detections entered as 1.5 +/- 1 sigma
   (2021ApJ...908...15S). For samples with non-detections use survival analysis (Kaplan-Meier in ASURV:
   2016ApJ...828...46A; lifelines with a bootstrapped log-normal fit: 2025A&A...693A.286S) or Bayesian regression with
   censored data (linmix: 2020A&A...633A.114S).
9. **Write the error budget** (Verification checks). Examples: 30% kappa, 15% flux calibration and about 10%
   temperature (2014ApJ...787...48X); gas-to-dust 28%, opacity 23%, flux about 14%, temperature about 20%, distance
   10% (2024ApJS..270....9X). Term ordering depends on the case; do not assume it. A budget of flux calibration alone
   understates the error (2024A&A...682A..61C says its quoted errors cover only 10% flux calibration while its inner
   mass may be off by up to about 5 from optical depth).

## Parameter defaults and ranges

Counts below are my own count of distinct bibcodes in the pack's "Key parameters" and "Assumptions" lines, which list
515 of the 915 papers (the lists are truncated), so they are lower bounds. Each count is a regex match on those lines,
then hand-checked to drop false hits (CO freeze-out thresholds, T_CMB, range-only mentions). Membership lists are in
`references/parameters.md`.

| Parameter | Common choice | Range seen | Papers (count) | Examples |
|---|---|---|---|---|
| Gas-to-dust (mass) | 100 | 30 to about 370 typical; 4594 in a metal-poor dwarf | 166 state 100 | 100: 2016ApJ...828...46A, 2020ApJ...894L..14L; 141: 2013ApJ...779...96T; 150 to 154: 2019A&A...621A.122B, 2015ApJ...813L..19J; 200: 2024A&A...681A..17D, 2025A&A...695L..15F; 90 +/- 25: 2014MNRAS.438.1267S; 300 (C-rich AGB): 2024A&A...686A.274V; LMC continuum N(H2) with dust-to-gas 0.0027 (gas-to-dust about 370), while the same paper's chemical model uses 300: 2020ApJ...891..164S; 30 in disks: 2023MNRAS.518.6092L; 4594: 2020ApJ...892..147S |
| T_d, disks and cores (fixed) | 20 K | 6 to 30 K for cold gas | 45 adopt 20 K for some sources | 2016ApJ...828...46A, 2025A&A...696A.232G, 2020ApJ...894L..14L; 15 K: 2018A&A...619A.161C, 2017ApJ...838..114K; 6 K: 2024ApJ...968L..19F; 10 K: 2016ApJ...823..160D; 30 K: 2026A&A...706A.214V |
| T_d, disks (scaled) | 25 K (L*/Lsun)^0.25 | exponent 0.17 to 0.25; 20 K fallback (2021A&A...653A..46V); no 10 K floor (2016ApJ...831..125P) | 7 use an L^0.25 scaling (one for a protostar) | 2016ApJ...819..102V, 2025A&A...693A.286S, 2025ApJ...994..214T, 2017ApJ...846...70P; RT-calibrated: 2020ApJ...892..111F |
| T_d, protostellar / hot cores | by class or line temperature | 20 / 50 / 100 K; up to 150 to 300 K | (see examples) | 2020A&A...635A...2S, 2018A&A...615A...9P, 2025A&A...701A.219N, 2022MNRAS.512.4419P, 2019A&A...628A..27B |
| T_d, high-z galaxies | 47 K, beta 1.6 (quasar hosts); 25 K mass-weighted (gas-mass work) | 25 K to 100 K (hot DOG) | 16 quote 47 K; 4 call 25 K mass-weighted | 47 K/1.6: 2016ApJ...816...37V, 2024ApJ...977..190X; mass-weighted 25 K: 2020ApJ...892...66M, 2025ApJ...993L..40S, 2025A&A...693A.190J; 25 K assumed: 2024ApJ...963....1O; 50-100 K: 2018Sci...362.1034D |
| T_d, debris belts | radiative equilibrium | 25 to 51 K | (see examples) | 2017ApJ...842....8M, 2025A&A...693A.151M, 2013ApJ...762L..21M |
| kappa, disks / debris (per dust) | 10 cm2/g at 1000 GHz, beta 1 (2.3 cm2/g at 230 GHz) | 2 to 3.5 cm2/g at 0.9 to 1.3 mm | 12 use the 1000 GHz form; 27 quote 2.3 cm2/g | 2016ApJ...828...46A, 2025A&A...693A.286S, 2017ApJ...842....8M, 2025A&A...696A.232G |
| kappa, disks, shallow beta | 2.3 cm2/g (nu/230 GHz)^0.4 | beta 0.4 | (see examples) | 2014ApJ...787...42C, 2016ApJ...831..125P, 2021A&A...656A.150P, 2024A&A...688A.149D |
| kappa, cores (OH94-type, per dust) | 0.9 cm2/g at 1.3 mm; 1.89 cm2/g at 870 um | 0.82 to 1.11 cm2/g at 1.3 mm | 25 quote 0.82 to 1.0 near 1.3 mm (a few omit the frequency); 7 quote 1.85 to 1.89 near 870 um | 2020ApJ...894L..14L, 2022MNRAS.512.4419P, 2024ApJS..270....9X, 2026ApJ...999..194I |
| kappa, per gas (includes 100) | 0.01 cm2/g at 230 GHz; 0.1 (nu/1000 GHz)^beta | 0.005 to 0.02 cm2/g near 1.3 mm | (see examples) | 2019ApJ...884...48C, 2018MNRAS.475..448T, 2025A&A...701A.219N, 2014ApJ...791...20R, 2024A&A...686A.122A |
| kappa, galaxies | 0.077 m2/kg at 850 um; 0.0431 m2/kg at 352.6 GHz; 2.64 m2/kg at 125 um | 0.04 to 0.15 m2/kg near 850 um | (see examples) | 2020ApJ...892...66M, 2025A&A...693A.190J, 2025A&A...701A.120P, 2025ApJ...993L..40S, 2014MNRAS.438.1267S |
| beta | 1 (disks, kappa normalised at 1000 GHz); 1.5 to 1.8 (cores, galaxies) | 0 to 2.2 | 21 use 1; 69 use 1.5 to 1.9 | 2016ApJ...828...46A; 2020ApJ...892...66M; 2016ApJ...833..209O; 0 to 0.5 in 2025NatAs...9.1176R |
| mu_H2 (mass per H2 molecule) | 2.8 for N(H2), n(H2) | 2.8 to 2.86 | 23 quote 2.8 (12 label it per H2 molecule) | mu_H2 = 2.8: 2019A&A...628A..27B, 2020ApJ...890...76N, 2024ApJ...961L..35M; mu = 2.8: 2024ApJ...962...13C |
| mu (other definitions) | not interchangeable with mu_H2 | 2.3 to 2.37; 1.41 per H | 12 quote 2.3 to 2.37; 4 quote mu_H = 1.41 | 2.33: 2019ApJ...884...48C, 2021ApJ...907...94C; 2.37: 2016ApJ...823..160D; 1.41: 2026ApJ...998..277M. The cards rarely say whether 2.3x is per free particle; check the paper before reusing it |
| Upper-limit significance | 3 sigma | 2 to 5 sigma | (see examples) | 2015A&A...583A..66H, 2019ApJ...875L...9W, 2024ApJ...963....1O, 2020MNRAS.499.5241C |

Longer lists by subfield (opacity normalisations, temperature prescriptions, gas-to-dust variants) and the count
membership lists are in `references/parameters.md`.

## Software

From the pack aggregates (software named in the matched steps of all 915 papers). Where two labels are listed
separately (RADMC-3D 34 + radmc3d 3, MCMax 5 + mcmax3d 3, linmix 5 + linmix_err 3, casa imfit 5 + imfit 4) the sum may
overcount papers; overlap between labels was not checked.

| Tool | Papers | What it is used for |
|---|---|---|
| CASA | 37 (+5 casa imfit, +4 imfit, +3 tclean) | continuum imaging, `imfit` Gaussian fluxes, `uvmodelfit`, simulated observations of models |
| RADMC-3D / radmc3d | 34 + 3 | dust RT; e.g. turning a flux limit into a disk mass limit (2019MNRAS.488.1005P, 2020MNRAS.498.1319M) |
| DALI | 23 | thermochemical disk models giving gas masses (2025A&A...693A.286S) |
| MCFOST | 22 | disk RT and SED fitting |
| emcee | 21 | MCMC for SED and visibility fits; upper limits as a likelihood penalty in 2021A&A...652A..66P |
| MAGPHYS | 15 | galaxy SED fits giving dust mass (fixed beta is a bias source per 2024MNRAS.535..729P) |
| CIGALE | 13 | galaxy SED fits incl. dust mass (2025ApJ...995L..63L, 2021A&A...654A..90L) |
| LIME | 9 | non-LTE line RT for envelopes and disks |
| lifelines, ASURV, linmix / linmix_err | 7, 4, 5 + 3 | censored statistics on dust-mass samples |
| GILDAS, MIRIAD; astrodendro, Clumpfind | 7, 5; 5, 3 | imaging outside CASA; core extraction |
| SciPy | 6 | modified blackbody least squares (2020ApJ...890...76N, 2025A&A...694A.295P) |
| optool, dsharp_opac, OpacityTool | 4, 4, 3 | grain-size-dependent opacities (2025A&A...696A.232G) |
| MCMax / mcmax3d, DUSTY, ProDiMo | 5 + 3, 4, 2 | disk and envelope RT or thermochemistry |

The pack does not establish a dominant implementation of the thin formula; the cards rarely name the code used for it.

## Pitfalls

- **Per gas vs per dust opacity.** Many cards quote kappa that already includes gas-to-dust 100 (2018MNRAS.475..448T
  says so explicitly; 2019ApJ...884...48C, 2025A&A...701A.219N, 2024A&A...686A.122A). Multiplying again by 100
  inflates gas mass 100x; using it as a dust opacity inflates dust mass 100x.
- **Units.** 1 m2/kg = 10 cm2/g (general). Galaxy papers quote m2/kg, disk papers cm2/g. Several cards print opacity
  units as g cm^-2 (2026A&A...706A.214V "units as printed", 2019ApJ...872...92F, 2025A&A...701A.219N); read these as
  cm2/g after checking the paper.
- **Optical depth.** Thin masses of bright compact sources are lower limits (2018A&A...619A.161C, 2015A&A...573L...1O,
  2017A&A...604A...6S, 2016ApJ...832..178V, 2014ApJ...783L..13P, 2026ApJ..1003..219W). A lower spectral index can come
  from optical depth, not grain growth (2018A&A...619A.161C). In SED fits the sign can flip: assuming thin dust when
  it is thick biases T_d low and M_dust high (2024A&A...684A..33K; 2022A&A...665L...7S allows a factor two
  overestimate).
- **Temperature dominates.** Factor 2 in T gives about factor 2 in mass (pack validation list); 2017ApJ...838..114K
  finds 10 K gives 2x higher and 25 K about 2x lower masses than 15 K; 2020ApJ...894L..14L finds 50 K lowers core
  masses 3x vs 20 K. 2020ApJ...894L..14L admits T_d at 2000 au is unknown. The isothermal assumption can bias masses
  either way, and papers state this differently: 2016MNRAS.457.4536W calls its masses upper limits because of the
  isothermal assumption; 2016ApJ...833L...6C says its dust mass may be underestimated because warm dust dominates the
  SED peak; 2024ApJ...976..241Y says its masses may be too low for starless condensations (25 K too warm) or too high
  for protostellar ones; see also 2017MNRAS.468L..87C.
- **Opacity uncertainty ranges from about 25% to a factor 3-5 in the papers that quote it.** About 25%
  (2021A&A...655A..98A, not propagated), 30% kappa giving 33% in mass (2021A&A...650A.202R), factor 2
  (2018ApJ...855...24P, 2015ApJ...808..102K, 2020ApJ...903...34A at least), factor 2-3 (2016A&A...593L..14F), factor 3
  between Hildebrand and OH94 (2014ApJ...796....1T), about 4 vs OH94 (2020ApJ...896...35J), factor 3-5 for a debris
  belt (2018ApJ...869...10M). Large grains can hide mass, so masses are lower limits (2015ApJ...808...69B,
  2016MNRAS.458L..29C, 2021NatAs...5..586Y). 2013ApJ...764L..14Z quotes its disk mass as a lower limit with a
  factor-five (total mass) uncertainty.
- **Gas-to-dust is not universal.** It rises at low metallicity (2020ApJ...892...66M, 2020ApJ...892..147S), differs
  for AGB and RSG envelopes (2024A&A...686A.274V, 2024A&A...681A..17D), comes out high in high-z quiescent galaxies
  (2025ApJ...993L..40S), and disk gas masses from dust conflict with CO by about 10x (2016ApJ...828...46A). Dust-based
  gas misses the atomic phase (2020ApJ...892...66M).
- **Resolved-out flux.** Interferometers miss extended emission: continuum interferometer-to-single-dish ratio 0.53 in
  2014ApJ...787...48X, up to about 50% of 333 GHz flux in 2017ApJ...835..213P, N(H2) 4x low in 2024ApJ...968L..19F.
  Line emission suffers the same way (CO example: only 43% of single-dish flux recovered in 2016ApJ...832..148V).
- **Point-source limits and local noise.** A limit quoted for a point source (2017ApJ...842....8M) does not apply to
  extended emission, and noise can be locally enhanced (gap rms in 2024ApJ...974..102S).
- **Lensing.** Apparent masses of lensed galaxies must be divided by the magnification; a single magnification is a
  simplification (2016ApJ...822...80S), and continuum and line magnifications can differ (2021ApJ...917...99Y).
- **SED masses on other conventions.** SED codes carry their own dust composition and opacity; reconcile before
  comparing (2025A&A...694A..82S divides CIGALE masses by 2; 2021ApJ...908...15S, MAGPHYS vs Draine and Li;
  2019PASJ...71...71H, the Dunne 2000 opacity doubles M_d).
- **Contaminating emission.** Free-free, synchrotron, the stellar photosphere and line emission all add to the
  continuum (2016A&A...591A..73G, 2013ApJ...762L..21M, 2013ApJ...774L...7M, 2021A&A...650A.142M).
- **Distance.** Mass scales as d^2; distance can dominate limit uncertainties (2015A&A...583A..66H) and disputed
  distances change masses (2014ApJ...791..108F, 2017A&A...603A..10B).
- **Core definition.** Core boundaries and thresholds change masses by 10-40% (2015MNRAS.449..715W) and are subjective
  (2013ApJ...779...96T, 2019ApJ...871..185L).
- **Unstated settings.** Cards most often flag as missing: CASA version (46, plus 40 under other wordings),
  self-calibration intervals (32 + 21 + 12 and smaller variants), line-free channels (21 + 18 + 15 + 15 + 12 and more
  under different wordings), flux-scale uncertainty (14 + 9 + 8 + 7), PB correction (12 + 8). State all of these.

## Verification checks

What the papers did:

- **Vary T_d and beta** and report the spread: T 15-35 K gives 25-50% systematic (2020ApJ...892...66M); 20-30 K
  (2018ApJ...854L...4R, 2016ApJ...833...12R); 1.5x T test of tau (2018A&A...619A.161C); 50 K and random-T appendix
  (2020ApJ...894L..14L); 40 and 70 K, beta 1.5 to 2.2 (2024ApJ...977..190X); 1000 Monte Carlo T draws per class
  (2025A&A...701A.219N); other T prescriptions repeated (2020A&A...633A.114S).
- **Vary the opacity** (Hildebrand vs OH94: 2014ApJ...796....1T) or bracket with grain size (100 um vs 1 mm grains:
  2024ApJ...974..102S; two opacity models: 2021ApJ...923..121Y). 2024Sci...383..988B folds both opacities and a 0.2
  dex optical-depth term into its mass interval.
- **Explicit error budget**: 30% kappa, 15% flux calibration, about 10% temperature (2014ApJ...787...48X); per-term
  budget in 2024ApJS..270....9X; mass about 40% and column density about 35% (2020ApJ...890...76N); 20% NOEMA and 10%
  ALMA flux calibration propagated (2025A&A...693A..49S).
- **Brightness-based optical depth check** (2018A&A...619A.161C, 2020ApJ...904..181L), with scattering or thick pixels
  excluded in 2020A&A...644A..11L.
- **Thin vs RT**: compare thin masses with an RT or thermochemical grid (2025A&A...694A.295P with ProDiMo;
  2025A&A...696A.232G with an optool/DSHARP grid, dropping disks at the grid edge with tau >> 5).
- **Independent mass**: CO-based gas mass (2021A&A...652A..98G median offset 0.23 dex; 2018Sci...362.1034D),
  [CI]-based gas mass (2021A&A...652A..66P), earlier ALMA or single-dish fluxes (2017ApJ...842....8M,
  2024ApJ...968L..19F), full SED fit as a sanity check (CIGALE in the aggregates).
- **Plausibility and completeness**: 2020ApJ...890L..14T rejected uncoated-grain opacities that gave a shell mass
  above the star's possible initial mass; injection-recovery for faint sources (2024ApJ...974..102S); KS tests on
  censored mass distributions (2025A&A...693A.286S).

What a careful referee adds:

- Recompute one mass from the quoted F_nu, d, kappa, T (the 0.57 Earth-mass sanity number above).
- Confirm the opacity is per dust or per gas and that gas-to-dust is applied once; check the mu convention.
- Confirm the flux is PB-corrected, line-free, and free of free-free and stellar flux.
- Compare the peak intensity with f B_nu(T_d) before accepting "optically thin", and check resolution (filling factor)
  and scattering: a low beam-averaged brightness alone is inconclusive.
- Check that mass limits state the assumed size and optical depth, and use the local PB-corrected noise.
- Check that limits use the same kappa and T as detections and that censored data are handled with survival analysis.
- At high z, check the CMB contrast term and which magnification was applied to the dust.

## Source cards

The full list with titles is in `references/sources.md` (generated). The most informative cards for this technique:

- 2016ApJ...828...46A: Lupus disk survey; T 20 K, 10 cm2/g at 1000 GHz, beta 1; ASURV.
- 2025A&A...693A.286S: IMTT vs Herbig disk masses; L-scaled T; lifelines, KS; masses may be low by up to ~7.
- 2025A&A...696A.232G: optool/DSHARP RT grid vs thin masses (2.3 cm2/g, 20 K); grid-edge disks dropped.
- 2015A&A...583A..66H: closed-form M_dust = 0.566 F (d/140)^2 M_earth; distance-dominated limits.
- 2018A&A...619A.161C: crescent mass, tau from T_b, lower limits.
- 2014ApJ...796....1T: component subtraction; Hildebrand vs OH94 factor 3.
- 2017ApJ...842....8M: Fomalhaut belt; radiative-equilibrium T; mass limit for a point source.
- 2025A&A...693A.151M: 74 debris belts; kappa 0.23 m2/kg at 1.33 mm; T(R) law.
- 2020ApJ...894L..14L: CMZ cores; OH94 0.899 cm2/g; T sensitivity appendix.
- 2024ApJS..270....9X: core masses with a per-term uncertainty budget; mu_H2 2.81; 1.89 cm2/g at 870 um.
- 2020ApJ...890...76N: clump SED for T and beta; core masses with 40% error.
- 2020ApJ...892...66M: ASPECS stacking; Kovacs thin formula, CMB, metallicity-dependent gas-to-dust.
- 2025A&A...693A.190J: CMB flux correction 1.03 to 1.31 from z ~ 1 to 6; mass-weighted 25 K.
- 2018Sci...362.1034D: hot DOG; 50-100 K bracket; dust vs CO gas.
- 2021A&A...652A..98G: GATOS tori; dust vs CO masses agree to 0.23 dex.
- 2014ApJ...787...48X: error budget; interferometer/single-dish ratio.
- 2020ApJ...891..164S: LMC hot core; dust-to-gas 0.0027 scaled by metallicity; three T values.
- 2020ApJ...890L..14T: AGB shell mass; plausibility rejects an opacity.
- 2015A&A...573L...1O: red supergiant dust; thin-limit lower limits; resolved-out flux.
- 2019MNRAS.488.1005P: RT conversion of flux limits to circumplanetary disk mass limits.
- 2024ApJ...974..102S: spectral index, grain-size-dependent kappa, injection-recovery.

=== references/parameters.md ===
# Parameter choices by subfield (dust-continuum-mass)

All values are copied from the evidence pack (`skills/packs/dust-continuum-mass.md`, 915 papers), "Key
parameters" and "Assumptions" lists. Those lists are truncated in the pack (515 of 915 papers appear), so
this is a sample, not a census. Rows added in the 3,500-paper refresh cite papers new to the pack.
Unit note (general): 1 m2/kg = 10 cm2/g. "per gas" means the opacity already includes a gas-to-dust ratio.

## Opacity normalisations

| Subfield | kappa_0 | nu_0 or lambda | beta | Per | Papers |
|---|---|---|---|---|---|
| Protoplanetary disks | 10 cm2/g | 1000 GHz | 1 | dust | 2016ApJ...828...46A, 2019A&A...623A.150V, 2019A&A...628A..85V, 2020A&A...640A..27V, 2018A&A...619A.161C, 2017AJ....153..240A, 2024A&A...684A.134R |
| Protoplanetary disks | 2.3 cm2/g | 230 GHz | 0.4 | dust | 2014ApJ...787...42C, 2017ApJ...846...70P, 2018ApJ...859...32P, 2018ApJ...869...17L, 2017ApJ...841L..11B, 2017A&A...597A..32V |
| Protoplanetary disks | 2.7 cm2/g | 885 um | 0.4 | dust | 2016ApJ...819..102V |
| Protoplanetary disks | 2 cm2/g | 890 um | n/a | dust | 2020A&A...633A.114S |
| Protoplanetary disks | 3.4 cm2/g | 880 um | n/a | dust | 2015ApJ...805L..17B, 2017ApJ...835...17M |
| Protoplanetary disks | 0.02 cm2/g | 0.89 to 1.3 mm | n/a | gas | 2014ApJ...791...20R, 2014Natur.514..600D |
| Disks, grain-size dependent | 0.42 / 1.9 cm2/g | 1.3 mm | n/a | dust (100 um / 1 mm grains) | 2024ApJ...974..102S |
| Disks, grain-size dependent | 0.4 / 1.9 / 1.0 cm2/g for a_max 0.1 / 1 / 10 mm | mm | n/a | dust | 2025ApJ...988..106H |
| Disks, DSHARP via optool (RT grid) | grains 0.05 um to 3 mm, full scattering | mm | n/a | dust | 2025A&A...696A.232G |
| Disks, two models side by side | DSHARP (s_max 0.1 mm) and 2.3 (nu/230 GHz)^0.4 | 230 GHz | 0.4 | dust | 2021ApJ...923..121Y |
| Disks | 2.7 cm2/g | 345 GHz | n/a | dust | 2025ApJ...994..214T |
| Debris disks | 2.3 cm2/g | 1.3 mm | n/a | dust | 2017ApJ...842....8M, 2018ApJ...869...75M |
| Debris disks | 0.23 m2/kg | 1.33 mm (from 1 m2/kg at 1000 GHz, linear) | 1 | dust | 2025A&A...693A.151M |
| Debris disks | 2.7 cm2/g | 1.3 mm | n/a | dust | 2013ApJ...762L..21M |
| White-dwarf debris | 1.7 cm2/g | 870 um | n/a | dust | 2014MNRAS.444.1821F |
| Dense cores (OH94) | 0.899 cm2/g | 1.3 mm | n/a | dust | 2020ApJ...894L..14L, 2018ApJ...853..160C, 2017ApJ...849...68S, 2018ApJ...869...59W |
| Dense cores (OH94) | 1.11 cm2/g | 230 GHz | n/a | dust | 2017A&A...604A...6S, 2019A&A...621A.122B |
| Dense cores | 0.9 cm2/g at 1.3 mm; pack quotes "(lambda/1.3 mm)^beta", which inverts the usual kappa proportional to nu^beta. Verify in the paper; for a positive beta use (1.3 mm/lambda)^beta | 1.3 mm | 1.5 | dust | 2016ApJ...833..209O |
| Cores (OH94 thin ice, 870 um) | 1.89 cm2/g | 870 um | n/a | dust | 2024ApJS..270....9X, 2024ApJ...962...13C, 2026ApJ...999..194I, 2026ApJ...998..277M |
| Cores (OH5, 3 mm) | 0.18 to 0.2 cm2/g | about 3 mm | n/a | dust | 2024ApJ...961L..35M, 2025ApJ...988...95D |
| Cores / clumps (Hildebrand) | 0.1 cm2/g | 1000 GHz | 0.5 to 1.8 | gas | 2016A&A...596A..88L, 2017A&A...600A.141K, 2018MNRAS.475..448T, 2021A&A...648A..41V |
| Cores / clumps | 0.01 cm2/g | 230 GHz | n/a | gas | 2019ApJ...884...48C, 2015ApJ...808..102K, 2014ApJ...789L...4T |
| Cores / clumps | 0.00899 cm2/g | 1.3 mm | n/a | gas | 2018ApJ...855...24P, 2019NatAs...3..517Z |
| Clumps by L/M class | 0.005 (printed as g cm^-2; includes gas-to-dust 100) | 1.3 mm | n/a | gas | 2025A&A...701A.219N |
| Cores / clumps (multi-temperature MBB fits) | 0.1 cm2/g per gas+dust | 300 um | 1.8 | gas | 2024A&A...687A.217D, 2024A&A...686A.122A |
| Galactic Centre clouds | 0.04 cm2/g (nu/505 GHz)^1.75 | 505 GHz | 1.75 | gas | 2015MNRAS.449..715W, 2016MNRAS.457.4536W |
| Galaxies (Li and Draine type) | 0.0431 m2/kg | 352.6 GHz | 1.8 | dust | 2020ApJ...892...66M |
| Galaxies | 0.0484 m2/kg | 850 um | 1.8 | dust | 2018Sci...362.1034D |
| Galaxies | 0.15 m2/kg | 870 um | n/a | dust | 2014MNRAS.438.1267S |
| Galaxies | 0.051 m2/kg | 500 um | 1.8 | dust | 2024ApJ...963....1O |
| Galaxies | 0.0865 m2/kg | 351 GHz | n/a | dust | 2021A&A...652A..98G |
| Galaxies | 0.0431 m2/kg | 352.6 GHz | 1.8 | dust | 2025A&A...693A.190J |
| Galaxies | 0.077 m2/kg | 850 um | n/a | dust | 2025A&A...701A.120P, 2022MNRAS.512.2426M, 2019MNRAS.482.3135B |
| Galaxies | 2.64 m2/kg | 2.4 THz (125 um) | 2.0 in 2025ApJ...993L..40S | dust | 2025ApJ...993L..40S, 2024A&A...684A..33K |
| Galaxies (RJ-tail calibration) | alpha_850 = 6.2e19 / 6.7e19 / 1e20 erg s^-1 Hz^-1 Msun^-1 per gas mass (T 25 K in the first two) | 850 um | 1.8 to 2 | gas | 2024A&A...691A.248L, 2022A&A...664A..63X, 2023MNRAS.524..923Z |
| Galaxies | 2.64 m2/kg | 125 um | 1.5 | dust | 2015ApJ...810...91H, 2019ApJ...881...63N |
| Dwarf galaxies | 1.6 m2/kg | 160 um | 1.7 | dust | 2017MNRAS.468L..87C |
| AGB / RSG envelopes | 7 cm2/g | mm | n/a | dust | 2018A&A...615A..28D, 2018A&A...616A..34H |
| AGB envelope (OH94 coated) | 1.8 cm2/g | mm | n/a | dust | 2020ApJ...890L..14T |
| Comet coma | 0.17 to 0.467 m2/kg | 233 GHz | n/a | dust | 2025ApJ...986L..22R |

## Temperature prescriptions

| Prescription | Papers |
|---|---|
| Fixed 20 K for all disks, not scaled with L* | 2016ApJ...828...46A |
| T = 25 K (L*/Lsun)^0.25 | 2016ApJ...819..102V, 2021A&A...653A..46V (20 K when L* unknown) |
| T = 25 K (L*/Lsun)^0.17 | 2017ApJ...846...70P |
| RT-calibrated: flaring angle 0.02, R_subl = 0.07 sqrt(L*) | 2020ApJ...892..111F, 2024A&A...684A.134R |
| T_d = [zeta L / (4 pi sigma r^2)]^(1/4), zeta = 0.02 at the source radius | 2024ApJ...974..102S |
| T_d = 38 K (r/100 au)^-0.4 (L_int/Lsun)^0.2 for protostellar disks | 2020A&A...644A..11L |
| T(R) = 278.3 L*^0.25 R^-0.5 (blackbody grains) for debris belts | 2025A&A...693A.151M |
| 20 K (no counterpart), 50 K (IR or radio counterpart), 100 K (hot core) | 2020A&A...635A...2S |
| 35 K with IR counterpart, 15 K without | 2018A&A...615A...9P |
| T by L/M: 20 K (L/M < 1), 35 K (1 to 10), max(21.1 (L/M)^0.22, 35 K) above 10 | 2024A&A...690A.185W |
| T_d = 43 (L/Lsun)^0.25 K | 2024A&A...690A..46S |
| T_f = 20 K (10-40) for L/M < 1, 30 K (10-50) for 1-10, 40 K (20-60) above 10; 1000 Monte Carlo runs | 2025A&A...701A.219N |
| T_d = CH3OH excitation / rotational temperature | 2025ApJ...991...59B, 2026ApJ..1003..219W |
| T_d = average COM rotational temperature (99 to 137 K) | 2022MNRAS.512.4419P |
| T_d = NH3 kinetic temperature (14.2, 22.6 K) | 2024ApJ...961L..35M |
| 30 K single temperature, argued because mass is dominated by the outer-radius temperature | 2026A&A...706A.214V |
| Disk T_d = T_b in the optically thick inner region | 2021ApJ...923..121Y |
| T_d = gas temperature from NH3 or line rotational temperature | 2014ApJ...797...27F, 2016ApJ...828..100F, 2020ApJ...890...76N |
| Clump SED fit for T_d and beta (22 K / 2.1 prestellar, 28 K / 1.6 protostellar) | 2020ApJ...890...76N |
| High-z: 47 K, beta 1.6 (quasar hosts) | 2016ApJ...816...37V, 2017Natur.545..457D, 2024ApJ...968....9W |
| High-z: mass-weighted 25 K | 2020ApJ...892...66M |
| High-z: assumed 25 K (not described as mass-weighted) | 2024ApJ...963....1O |
| High-z: 35 K, beta 1.5 | 2017ApJ...851..145M |
| High-z: mass-weighted 25 K | 2025ApJ...993L..40S, 2025A&A...693A.190J, 2019ApJ...880...15K |
| High-z: 47 K prior (sigma 5 K), 35 K for companions | 2021A&A...652A..66P |
| High-z: lower T bound set by T_CMB(z) | 2025A&A...695L..15F |

## Gas-to-dust variants

| Value | Context | Papers |
|---|---|---|
| 100 | default for disks, cores, many galaxies | 2016ApJ...828...46A, 2020ApJ...894L..14L, 2019A&A...628A..27B |
| 141 | Draine-type value for cores and clouds | 2013ApJ...779...96T, 2017MNRAS.464L..31H, 2018ApJ...853..160C |
| 150 to 154 | massive star formation, hot cores | 2017A&A...603A..10B, 2019A&A...621A.122B, 2015ApJ...813L..19J, 2019ApJ...871..170M |
| 90 +/- 25 | SMGs | 2014MNRAS.438.1267S, 2017ApJ...839...58S, 2018ApJ...859...12G |
| about 120 from 12+log(O/H) = 8.53 | metallicity-scaled galaxies | 2017MNRAS.469.4683C |
| 100 at solar metallicity, scaled with mass-metallicity relation | ASPECS stacks | 2020ApJ...892...66M |
| about 370 (dust-to-gas 0.0027 = Galactic 0.008 scaled by Z = 1/3) | LMC hot core, continuum N(H2) | 2020ApJ...891..164S |
| 300 | LMC, the same paper's gas-grain chemical model (a separate prescription) | 2020ApJ...891..164S |
| 300 / 167 | C-rich / O-rich AGB envelopes | 2024A&A...686A.274V |
| 40 | AGB wind model | 2017A&A...597A..99W |
| 200 | RSG envelopes; hot DOG at about 0.5 Z_sun | 2024A&A...681A..17D, 2025A&A...695L..15F |
| proportional to Z^-0.85, 100 at solar | metallicity-scaled galaxies | 2021A&A...655A..42S |
| 100 x 10^(Z - Z_sun) | metallicity-scaled galaxies | 2020MNRAS.498.4109J |
| dust-to-gas 0.0024 / 0.0016 / 0.002 (Z-scaled) | LMC / SMC hot cores | 2026ApJ...999..194I, 2023ApJ...946L..41S, 2021ApJ...922..206S |
| 316 | LMC protostars, same ratio applied to comparison sources | 2025ApJ...991...59B |
| 30 | disks (typical value quoted) | 2023MNRAS.518.6092L |
| 4594 +/- 2848 | extremely metal-poor dwarf DDO 70 | 2020ApJ...892..147S |
| 75 to 100, tuned to HD | TW Hya disk | 2015ApJ...799..204C |

## Count membership (for the SKILL.md parameter table)

Regex matches on the pack's "Key parameters" and "Assumptions" lines (515 of 915 papers), hand-checked.
Dropped as false hits: for 20 K, CO freeze-out or abundance thresholds, T_CMB, T_CO and range-only mentions
(2017ApJ...851...85B, 2021A&A...652A.128J, 2016ApJ...827..142B, 2015A&A...575L...5H, 2020ApJ...904L...6A,
2015ApJ...805...21C, 2018A&A...615A..83V, 2018ApJ...862..102S, 2026ApJ...998..277M, 2026A&A...709A.173M,
2015ApJ...798L..23K, 2023MNRAS.522.2384M, 2025ApJ...993L..40S); for 0.9 cm2/g, values at 3 mm, 870 um,
600 um or 340 GHz and unrelated 0.90 fractions; for L^0.25, the two debris-belt blackbody laws.

- Gas-to-dust 100 (or dust-to-gas 0.01) (166): 2012ApJ...761L..20R, 2013A&A...552L..10S, 2013A&A...557A.133D, 2013ApJ...774...39A, 2013PASJ...65L..14F, 2014A&A...569A..11S, 2014ApJ...783L..13P, 2014ApJ...784...82M, 2014ApJ...785...44M, 2014ApJ...787...42C, 2014ApJ...791...20R, 2014ApJ...791...42Z, 2014ApJ...791L...6W, 2014ApJ...795L..25R, 2014ApJ...796....1T, 2014Natur.514..600D, 2015A&A...575L...5H, 2015A&A...583A..66H, 2015ApJ...799..204C, 2015ApJ...801...82H, 2015ApJ...802..125R, 2015ApJ...805...21C, 2015ApJ...805L..17B, 2015ApJ...812..134H, 2015ApJ...814...22E, 2015MNRAS.447.1826Z, 2015MNRAS.449..715W, 2016ApJ...816...37V, 2016ApJ...827..142B, 2016ApJ...831..101B, 2016ApJ...832..110C, 2017A&A...601A...5H, 2017A&A...601L...3P, 2017A&A...602A..19L, 2017A&A...603A..92V, 2017A&A...604A..60B, 2017A&A...606A.121L, 2017A&A...608A..22A, 2017ApJ...835...17M, 2017ApJ...835..213P, 2017ApJ...836....8T, 2017ApJ...838..114K, 2017ApJ...849...25L, 2017ApJ...851...85B, 2017ApJ...851L..23C, 2017MNRAS.468..685Q, 2017MNRAS.469.2230M, 2018A&A...614A.113H, 2018A&A...615A..83V, 2018A&A...617A..89C, 2018A&A...618A.164S, 2018ApJ...854..177V, 2018ApJ...859..111H, 2018ApJ...863...19A, 2018ApJ...869..115S, 2018ApJ...869..126L, 2018ApJ...869L..22W, 2018MNRAS.475..448T, 2018MNRAS.480.4991G, 2018Sci...362.1034D, 2019A&A...622A..75L, 2019A&A...623A..77S, 2019A&A...624A...7V, 2019A&A...626A..93V, 2019A&A...628A..27B, 2019A&A...628A..85V, 2019A&A...629A..29J, 2019A&A...629A.136S, 2019ApJ...871....5T, 2019ApJ...871..185L, 2019ApJ...871..251P, 2019ApJ...872...70T, 2019ApJ...880..157D, 2019ApJ...881L..42C, 2019ApJ...884...48C, 2019ApJ...886..102S, 2019ApJ...887...79H, 2019MNRAS.483..806R, 2019MNRAS.488.1005P, 2020A&A...633A.114S, 2020A&A...636A..26H, 2020A&A...644A..84M, 2020ApJ...890...76N, 2020ApJ...890L..14T, 2020ApJ...892..152H, 2020ApJ...894L..14L, 2020ApJ...895L..18B, 2020ApJ...896...43W, 2020ApJ...903...50E, 2020ApJ...904...37W, 2020ApJ...904...77G, 2020ApJ...904...78S, 2020ApJ...904..181L, 2020ApJ...904L...6A, 2020ApJ...905...25G, 2020ApJS..251...14H, 2020MNRAS.491..758A, 2020MNRAS.492.4847L, 2020MNRAS.496..394R, 2020MNRAS.498.4109J, 2020NatAs...4..142L, 2021A&A...645A..49G, 2021A&A...646A...3L, 2021A&A...647A.118L, 2021A&A...648A..33M, 2021A&A...650A..37D, 2021A&A...650A.142M, 2021A&A...650A.202R, 2021A&A...652A..66P, 2021A&A...652A..98G, 2021ApJ...907...94C, 2021ApJ...908..250H, 2021ApJ...910...75L, 2021ApJ...918...76C, 2021ApJ...921...97J, 2021MNRAS.503...77W, 2021MNRAS.506.4175M, 2021MNRAS.507.1886F, 2022A&A...661A..53V, 2022A&A...662A...8M, 2022A&A...665L...7S, 2022MNRAS.510.4485R, 2022MNRAS.512.4419P, 2022MNRAS.515.5730K, 2023Ap&SS.368...33M, 2023MNRAS.522.2384M, 2023MNRAS.525.2229M, 2023MNRAS.525.6146W, 2024A&A...682A..61C, 2024A&A...684A.200G, 2024A&A...684L..12S, 2024A&A...687A.217D, 2024A&A...687A.299L, 2024AJ....167...75H, 2024AJ....168..151J, 2024ApJ...961L..35M, 2024ApJ...962...13C, 2024ApJ...967..133S, 2024ApJ...968...10F, 2024ApJ...968L..11G, 2024ApJ...971L..23L, 2024ApJ...972..115C, 2024ApJ...973..135H, 2024ApJ...974..257Z, 2024ApJ...976..241Y, 2024ApJS..270....9X, 2024MNRAS.532.1752R, 2024RAA....24f5011X, 2024Sci...383..988B, 2025A&A...693A.286S, 2025A&A...694A..86Y, 2025A&A...694A.295P, 2025A&A...698A.165A, 2025A&A...698L..16S, 2025A&A...701A.219N, 2025ApJ...984L..16G, 2025ApJ...988...95D, 2025ApJ...995L..75C, 2025NatAs...9.1176R, 2026A&A...705A..96M, 2026A&A...706A.214V, 2026A&A...709A.173M, 2026A&A...710A.238D, 2026AJ....171..368M, 2026ApJ..1003..219W, 2026ApJ..1004L...6D
- Fixed T_d = 20 K for at least some sources (45): 2014ApJ...784...82M, 2015ApJ...801...82H, 2015ApJ...805L..17B, 2015ApJ...806...35J, 2015ApJ...807L...4F, 2016ApJ...828...46A, 2016ApJ...831..125P, 2016ApJ...833L...6C, 2016PASJ...68L...7T, 2017ApJ...843...45K, 2018ApJ...863...19A, 2019A&A...626A..11C, 2019A&A...628A..85V, 2019A&A...632A..83S, 2019ApJ...872...92F, 2020A&A...633A.114S, 2020A&A...642A.164V, 2020ApJ...892..152H, 2020ApJ...894L..14L, 2020MNRAS.492.4847L, 2021A&A...648A..33M, 2021A&A...649A.122P, 2021A&A...650A..37D, 2021A&A...653L...9V, 2021A&A...656A.150P, 2021ApJ...922..206S, 2021MNRAS.501.2934C, 2021MNRAS.501.4317P, 2022A&A...661A..53V, 2022A&A...662A...8M, 2023A&A...674A..66Z, 2024A&A...682A..61C, 2024A&A...692A.155K, 2024ApJ...968L..11G, 2024ApJ...971..176H, 2024Sci...383..988B, 2025A&A...694A..86Y, 2025A&A...696A.232G, 2025A&A...698A.165A, 2025A&A...701A.219N, 2025ApJ...994..214T, 2025ApJ...995...16Z, 2025ApJS..280...33Y, 2025NatAs...9.1176R, 2026A&A...706A.214V
- kappa = 10 cm2/g at 1000 GHz (12): 2016ApJ...828...46A, 2018A&A...619A.161C, 2019A&A...628A..85V, 2020ApJ...892..111F, 2020MNRAS.492.4847L, 2021A&A...648A..33M, 2023A&A...675A.131T, 2025A&A...693A..49S, 2025A&A...693A.286S, 2025A&A...694A.295P, 2026A&A...706A...4R, 2026A&A...706A.214V
- kappa = 2.3 cm2/g (at 230 GHz / 1.3 mm unless noted) (27): 2014ApJ...787...42C, 2015ApJ...798L..23K, 2016ApJ...827..142B, 2016ApJ...831..125P, 2016Natur.538..483T, 2017ApJ...842....8M, 2017ApJ...849..123M, 2018ApJ...869...75M, 2019A&A...626A..11C, 2019ApJ...872...92F, 2019ApJ...875...87D, 2019ApJ...883..180H, 2019MNRAS.488.1005P, 2020A&A...640A..19T, 2020AJ....159..288M, 2021A&A...656A.150P, 2021AJ....162..235Y, 2021ApJ...923..121Y, 2021MNRAS.501.2934C, 2022A&A...661A..53V, 2023A&A...674A..66Z, 2024A&A...686A.206Y, 2024A&A...688A.149D, 2024ApJ...966...32E, 2025A&A...696A.232G, 2025A&A...703A..15M, 2025NatAs...9.1176R
- kappa about 0.9 cm2/g near 1.3 mm (OH94-type) (25): 2015ApJ...806...35J, 2016Natur.538..483T, 2018ApJ...867...43T, 2018ApJ...869...59W, 2019A&A...623A..77S, 2019ApJ...886..102S, 2019ApJ...887...79H, 2020ApJ...894L..14L, 2020ApJ...904...78S, 2020ApJS..251...14H, 2021ApJ...910..148M, 2021MNRAS.503...77W, 2022MNRAS.512.4419P, 2023Ap&SS.368...33M, 2023MNRAS.525.2229M, 2024A&A...684L..12S, 2024ApJ...971..176H, 2024ApJ...972..115C, 2024ApJ...976..241Y, 2024RAA....24f5011X, 2025A&A...694A..86Y, 2025A&A...698L..16S, 2025ApJS..280...33Y, 2026A&A...709A.173M, 2026AJ....171..368M
- kappa 1.85 to 1.89 cm2/g near 870 um (7): 2020ApJ...890...76N, 2024ApJ...962...13C, 2024ApJS..270....9X, 2025A&A...696A...7L, 2025ApJ...991...59B, 2026ApJ...998..277M, 2026ApJ...999..194I
- T_d scaled as L^0.25 (7): 2016ApJ...819..102V, 2016ApJ...827..142B, 2016ApJ...831..125P, 2020ApJ...904...78S, 2025A&A...693A.286S, 2025A&A...694A.295P, 2025ApJ...994..214T
- T_d = 47 K (high z) (16): 2016ApJ...816...37V, 2017ApJ...836....8T, 2017MNRAS.465.4390B, 2018ApJ...866..159V, 2018MNRAS.479.1154B, 2018PASJ...70...36I, 2019ApJ...881...63N, 2020ApJ...895...74N, 2020ApJ...903...34A, 2021A&A...652A..66P, 2021ApJ...908..235I, 2022MNRAS.510.4976A, 2024ApJ...977..190X, 2024ApJ...977L..46B, 2025A&A...694A.171M, 2025A&A...700A.277C
- T_d = 25 K called mass-weighted (4): 2019ApJ...880...15K, 2024A&A...686A..64M, 2025A&A...693A.190J, 2025ApJ...993L..40S
- beta = 1 (21): 2013ApJ...774...39A, 2014ApJ...789L...4T, 2014ApJ...793....1Y, 2016ApJ...828...46A, 2017ApJ...843...45K, 2018A&A...615A...9P, 2018A&A...619A.161C, 2018ApJ...863...19A, 2019A&A...628A..85V, 2020ApJ...892..111F, 2020MNRAS.492.4847L, 2020MNRAS.496..394R, 2021A&A...648A..33M, 2022A&A...661A..53V, 2023A&A...675A.131T, 2025A&A...693A..49S, 2025A&A...693A.286S, 2025A&A...694A.295P, 2025ApJ...995...16Z, 2026A&A...706A...4R, 2026A&A...706A.214V
- beta 1.5 to 1.9 (69): 2014ApJ...785..111W, 2014ApJ...792...34O, 2014ApJ...796...84R, 2015A&A...574A..19S, 2015ApJ...800...70S, 2015ApJ...810...91H, 2015MNRAS.452...54M, 2015Natur.519..327W, 2016ApJ...816...37V, 2016ApJ...819...82S, 2016ApJ...833L...6C, 2016PASJ...68..103F, 2017A&A...602A..19L, 2017ApJ...836....8T, 2017ApJ...849...14S, 2017ApJ...849...25L, 2017ApJ...851..145M, 2017MNRAS.465.4390B, 2017MNRAS.468L..87C, 2018ApJ...866..159V, 2018MNRAS.479.1154B, 2018NatAs...2...56Z, 2018PASJ...70...36I, 2018Sci...362.1034D, 2019ApJ...871..170M, 2019ApJ...874...27T, 2019ApJ...880...15K, 2019ApJ...880..157D, 2019MNRAS.482.3135B, 2020ApJ...892...66M, 2020ApJ...895...74N, 2020ApJ...896...93H, 2020ApJ...903...34A, 2020ApJ...904...77G, 2020ApJ...904...78S, 2020ApJ...904..181L, 2020ApJS..251...14H, 2020MNRAS.499.5241C, 2021A&A...648A..41V, 2021A&A...650A.153D, 2021A&A...650A.202R, 2021A&A...652A.128J, 2021A&A...654A..90L, 2021A&A...655A..42S, 2021ApJ...908...15S, 2021ApJ...908..235I, 2021MNRAS.503...77W, 2022A&A...662A...8M, 2022A&A...664A..63X, 2022MNRAS.510.4976A, 2022MNRAS.515.1751W, 2023Ap&SS.368...33M, 2023MNRAS.524..923Z, 2023MNRAS.525.2229M, 2024A&A...686A.122A, 2024A&A...687A.217D, 2024A&A...691A.248L, 2024ApJ...963....1O, 2024ApJ...964..146F, 2024ApJ...970...30M, 2024ApJ...977..190X, 2024ApJ...977L..46B, 2025A&A...693A.190J, 2025A&A...694A..86Y, 2025A&A...694A.171M, 2025A&A...695L..18M, 2025A&A...696A..33P, 2025ApJ...995..150K, 2026A&A...709A.173M
- mu = 2.8 to 2.86 (23): 2017A&A...604A..60B, 2018ApJ...869..115S, 2019A&A...628A..27B, 2019ApJ...886..102S, 2019MNRAS.483..806R, 2020ApJ...890...76N, 2020ApJ...892..152H, 2020ApJ...904..181L, 2020ApJS..251...14H, 2021A&A...650A.202R, 2022MNRAS.512.4419P, 2022MNRAS.515.5730K, 2023MNRAS.525.6146W, 2024ApJ...961L..35M, 2024ApJ...962...13C, 2024ApJ...968...10F, 2024ApJ...972..115C, 2024ApJ...976..241Y, 2024ApJS..270....9X, 2024RAA....24f5011X, 2025A&A...694A..86Y, 2025ApJ...988...95D, 2026ApJ..1004L...6D
-   of which labelled per H2 molecule (12): 2017A&A...604A..60B, 2019A&A...628A..27B, 2019ApJ...886..102S, 2020ApJ...890...76N, 2020ApJ...904..181L, 2020ApJS..251...14H, 2021A&A...650A.202R, 2023MNRAS.525.6146W, 2024ApJ...961L..35M, 2024ApJS..270....9X, 2024RAA....24f5011X, 2025A&A...694A..86Y
- mu = 2.3 to 2.37 (12): 2014A&A...569A..11S, 2016ApJ...823..160D, 2016PASJ...68L...7T, 2017A&A...606A.121L, 2017ApJ...849...25L, 2019A&A...628A...2B, 2019ApJ...884...48C, 2020A&A...644A..84M, 2021ApJ...907...94C, 2023MNRAS.518.6092L, 2024RAA....24f5011X, 2026A&A...705A.203W
- mu_H = 1.41 (per H) (4): 2023Ap&SS.368...33M, 2023MNRAS.525.2229M, 2026AJ....171..368M, 2026ApJ...998..277M

=== RECONCILIATION (first review, fixes to keep) ===
# Reconciliation: dust-continuum-mass
- SR-01 | FIXED | Split 2020ApJ...891..164S into dust-to-gas 0.0027 (gas-to-dust about 370) for continuum N(H2) and 300 for its chemical model (pack step 4 vs step 7), in both SKILL.md and parameters.md; range widened to "40 to about 370".
- SR-02 | FIXED | 2016ApJ...832..148V now labelled a CO missing-flux example (pack limitation is in "Distribution of Molecular Gas"); removed from the continuum resolved-out row; 2014ApJ...787...48X 0.53 ratio kept as the continuum example.
- SR-03 | FIXED | Step 9 now quotes the actual budget (30% kappa, 15% flux cal, about 10% T; 2014ApJ...787...48X) and says term ordering depends on the case.
- SR-04 | FIXED | 2013ApJ...764L..14Z moved out of the opacity bullet and described as a disk-mass lower limit with factor-five uncertainty; opacity range now "factor 2 to 3 in papers that quote it".
- SR-05 | FIXED | Removed the causal "warm dust dominates" link for 2016MNRAS.457.4536W; each paper's limitation now stated separately (upper limits from isothermal assumption vs 2016ApJ...833L...6C underestimate because warm dust dominates the SED peak).
- SR-06 | FIXED | "Mass-weighted" attributed only to 2020ApJ...892...66M; 2024ApJ...963....1O listed as an assumed 25 K in both files.
- SR-07 | FIXED | Temperature hierarchy relabelled as the skill author's guidance with a same-component requirement; astrodendro/Clumpfind given as examples (2020ApJ...894L..14L, 2020ApJ...890...76N, 2019ApJ...871..185L) with "pack does not show which is more common".
- SR-08 | FIXED | Replaced with "The pack does not establish a dominant implementation of the thin formula".
- SR-09 | FIXED | Replaced tau = -ln(1 - T_b/T_d) with the Planck-intensity absorption-only slab form including filling factor f and background, assumptions stated; 2018A&A...619A.161C described as a brightness-based check (tau about 0.4 at 1.5x T_d, per pack).
- SR-10 | FIXED | parameters.md row for 2016ApJ...833..209O now flags that the pack's "(lambda/1.3 mm)^beta" inverts kappa proportional to nu^beta and says to verify, giving (1.3 mm/lambda)^beta for positive beta.
- SR-11 | FIXED | Split into mu_H2 = 2.8 (13 distinct bibcodes quote 2.8, 6 label it mu_H2) and other mu 2.3 to 2.37 (8 bibcodes, definition rarely stated); counts made by matching mu values in the pack's parameter/assumption lines; step 5 warns not to substitute per-particle mu.
- SR-12 | FIXED | Added explicit high-z formula with nu_rest, T_CMB(z), (1+z) placement and B(T_d)-B(T_CMB) contrast term, and separated contrast correction from CMB heating (general practice, flagged as such).
- SR-13 | FIXED | Step 8 and When-to-use now state thin limits are conditional; compact thick material can evade them; cites 2017ApJ...842....8M thin-mass vs thick clump-size and 2019MNRAS.488.1005P RT.
- SR-14 | FIXED | Step 2 specifies integrated flux for mass, beam solid angle for surface brightness, local PB-corrected noise (2024ApJ...974..102S gap rms); step 8 and a pitfall cover point-source vs extended limits (2017ApJ...842....8M).
- SR-15 | FIXED | Step 6 and referee checks now require filling-factor/resolution and scattering checks and state low beam-averaged brightness is inconclusive (2016Sci...353.1519P, 2020A&A...644A..11L, 2019MNRAS.488.1005P).
- SR-16 | FIXED | n(H2) labelled a spherical mean with r definition; geometry uncertainty and unresolved-size bounds added (2019ApJ...871..185L, 2014ApJ...795L..25R).
- SR-17 | FIXED | Lensing correction added to step 5 and Pitfalls (divide by magnification; single magnification is a simplification, 2016ApJ...822...80S).
- SR-18 | FIXED | "When not to use" SED row and a pitfall now require reconciling SED dust conventions (2025A&A...694A..82S divides CIGALE masses by 2).
- Note (merged software totals) | FIXED | Software section states which rows are sums of label counts with unchecked overlap.

=== EVIDENCE PACK (dust-continuum-mass, rebuilt) ===
# Evidence pack: Dust and gas masses from (sub)mm continuum (`dust-continuum-mass`)

Scope: dust (and gas) masses from optically thin continuum flux: opacity law, temperature, gas-to-dust

Built from 915 non-held-out ALMA papers whose methods cards passed mechanical evidence verification (every quote below is verbatim from the paper). Years 2012-2026.
Matcher (regex over analysis steps): `dust mass|(?:gas|disk|disc|core|clump|envelope|total) mass\w* (?:from|using|via|based on) (?:the )?(?:\w+ )?(?:dust|continuum|mm|millimet|submm)|optically thin dust|gas[- ]to[- ]dust`
Tagging is by regex, so a few papers may be off-topic: ignore those.

## Aggregates over all papers

### Science fields
- star_formation: 445
- protoplanetary_disks: 321
- high_z_galaxies: 203
- astrochemistry: 199
- milky_way_ism: 123
- agn_and_quasars: 88
- nearby_galaxies: 69
- evolved_stars: 38
- exoplanets: 33
- debris_disks: 33
- stellar_physics: 32
- galaxy_clusters_and_sz: 13
- solar_system: 3
- transients: 3
- other: 2

### Software named in the matched steps
- casa: 37
- radmc-3d: 34
- dali: 23
- mcfost: 22
- emcee: 21
- magphys: 15
- cigale: 13
- lime: 9
- lifelines: 7
- gildas: 7
- scipy: 6
- mcmax: 5
- astrodendro: 5
- miriad: 5
- linmix: 5
- casa imfit: 5
- phantom: 5
- dusty: 4
- asurv: 4
- imfit: 4
- optool: 4
- dsharp_opac: 4
- moderato: 3
- linmix_err: 3
- opacitytool: 3
- tclean: 3
- bagpipes: 3
- clumpfind: 3
- mcmax3d: 3
- linestacker: 3
- torus: 3
- vis_sample: 3
- radmc3d: 3
- prodimo: 2
- sparx: 2
- cloudy: 2
- sonata: 2
- pymultinest: 2
- multinest: 2
- lmfit: 2

### Fitting methods (most common phrasings)
- 2D Gaussian (imfit): 2
- Gaussian fit: 2
- linmix: 2
- Linear regression in log-log, upper limits excluded: 1
- Grid SEDs fitted to data (fit metric not stated): 1
- SciPy curve_fit non-linear least squares with parameter bounds; weights = inverse flux errors; parameter errors from co…: 1
- Qualitative comparison of modeled and observed P-V morphology, especially the central waist and edge-brightening: 1
- Log-normal fit to cumulative distributions with bootstrap; priors/likelihood not stated: 1
- Linear gas-vs-dust radius relation fit; method not detailed: 1
- Log-normal fit to cumulative distributions: 1
- Grid search minimizing chi^2_SED: 1
- emcee with free M_dust, beta and T_dust (Gaussian prior); upper limits enter via a penalty term in the log-likelihood; …: 1
- chi-square minimization over CLOUDY grid (single PDR, single XDR, composite PDR+XDR): 1
- grid comparison, best fit by eye/ratios: 1
- Manual parameter tuning, no formal fit: 1
- template matching: 1
- chi2 minimisation; parameter uncertainties from varying each parameter until chi2 exceeds the critical value: 1
- Ellipsoidal nested sampling (PyMultiNest): 1
- Gaussian detection likelihood with an error-function upper-limit term; prior zero for T_dust < 60 K and X_H2O > 3 × 10^…: 1
- Grey-body range set by chi-squared twice the minimum; lower limits at 70 and 250 micron used as constraints: 1
- Chi-squared minimization and Bayesian likelihood probability distribution functions (PDFs): 1
- Forward modelling of uncontaminated CO line profile shape, width, two-horn separation, and peak flux; uncertainty propa…: 1
- Energy-balance SED fitting with CIGALE (Fritz et al. 2006 AGN models, Dale et al. 2014 SF templates): 1
- MCMC in visibility space; sampler, priors and likelihood not stated: 1
- lmfit; free torus scale k_t, dust temperature, dust mass and β; torus shape selected from templates.: 1
- Only M_dust free for the adopted J0129-0035 SED shape.: 1
- MCMC; priors not stated: 1
- SED: chi2 cutoff (chi2-chi2best)/Ndata<=3 median; best five Zhang&Tan models averaged: 1
- Visual inspection; errors from 5% calibration plus spectral rms: 1
- greybody fit; uncertainty region from twice minimum chi2; reduced chi2 1.44: 1
- analytic, no sampler: 1
- Varying cutoff sizes (a_min, a_max), power exponents (alpha, gamma), grain size a, porosity P, and total dust mass M_du…: 1
- Reconstruct dust mass and temperature posterior distributions: 1
- Least squares, chi2 comparison: 1
- MCMC for slope/intercept uncertainty, Gaussian errors: 1
- 2D Gaussian fit in the image plane; point-source fit to visibilities with uvmodelfit: 1
- emcee MCMC minimizing weighted chi^2 of visibilities and SED; best fit = median of walkers once steady; 1 sigma (68%) a…: 1
- SED fitting, mainly using ALMA mm-wavelength continuum flux densities for dust mass.: 1
- Vary total dust mass to match the mm-wavelength flux-density profile.: 1
- Posterior marginalization and expectation values within each grain-size family.: 1

### Validation checks used
- CH3CN temperatures broadly consistent with profile: 1
- Alternative T and H(r) and alternative catalogues: 1
- Tested with T_dust higher by factor 1.5 (tau ~0.4): 1
- Consistent with Sigma_gas from CO isotopologue modelling: 1
- Compared with ProDiMo and thin-disk estimates: 1
- Grid cannot fit NIR/MIR and ALMA simultaneously, so used only as a reference: 1
- Best-fit SEDs compared with data; best fit parameters often at bounds; B331 and B268 results bracketed as unreliable: 1
- Continuum brightness temperature 121 K compared with gas temperature above 300 K to assess continuum opacity: 1
- Compare K=3 observations with all four models; compare M4 predictions with all observed K components: 1
- Authors note dust masses may be underestimated by up to a factor of ~7 if emission is not optically thin or opacity is …: 1
- KS test p-values for dust masses and radii; 1 sigma confidence band on the cumulative distribution: 1
- Radius ratio repeated after removing four disks with difficult radii (GW Ori, HT Lup, SR 21, SU Aur); compared with Her…: 1
- Group I vs II compared with Herbig result; morphology check (cavities in group I): 1
- Compared with Mulders2021 efficiency argument: 1
- Checked model returned from fitting the entire SED (gave H_100 = 10 AU, all other parameters identical).: 1
- Range across three SED models adopted as uncertainty: 1
- Inclination uncertainty not included in M_dyn errors: 1
- Test alternative temperatures and emissivities.: 1
- Check whether accounting for HI changes the high-ratio interpretation in SIMBA.: 1
- Comparisons unchanged using z=0.5 or z=2 simulation outputs.: 1
- T_dust prior justified by literature and the H2O results; 35 K and 47 K priors give consistent results for companions (…: 1
- Composite fit compared with a single-XDR alternative; authors note more free parameters than data points and degeneraci…: 1
- CI-based molecular gas masses are consistent with dust-derived gas masses (75% molecular): 1
- Upper limits uncertainty dominated by distance: 1
- CO would be detected in 90% of models for other disks: 1
- Compared with Ossenkopf & Henning opacity (factor 3 higher masses): 1
- compared with dynamical mass and Herschel/Planck extrapolation: 1
- Visual comparison of PV diagrams; checked LIME level populations for no masing: 1
- UV-based SFR of 22 Msun/yr compared with FIR limit: 1
- Reduced chi2 <= 1.05 as 95 per cent confidence criterion: 1
- Compared with ALMA-based gas surface density estimate (rough, no uncertainty): 1
- Algorithm throughput by analytical forward modelling (NICMOS): 1
- Tested fixed alpha=0.75 and 0.1 and beta 1.6-2.4; Herschel flux split alternatives: 1
- Compare two- and three-component chi-squared; inspect 2D posterior degeneracies; select the fiducial model using ALMA m…: 1
- RMC 71 grey-body mass compared with the radiative-transfer literature value: 1
- 24 micron stacked photometry consistent with Riebel et al. stacked photometry: 1
- Verified that log M_dust > 3 threshold is exceeded for regions in NGC 6822 and Sextans A: 1
- Exclude pixels with chi^2 > mu(chi^2) + 3*sigma(chi^2) and pixels where median(M_dust) / std(M_dust) < 1: 1
- Compared observed CO outer radii against CO photodissociation predictions of Saberi et al. (2019); tested alternative v…: 1
- Tested excluding ALMA Band 7 from CIGALE fit (<3% change in AGN contribution), fitting with AGNfitter (<7% AGN contribu…: 1

### Key parameters and settings (bibcode: value)
- 2019ApJ...871..185L: 0 or 30 Msun central stellar mass
- 2019ApJ...871..185L: H(r)=0.05+0.3 sqrt(r/0.3) pc; T=30 K
- 2018A&A...619A.161C: d = 136 pc, T_dust = 15 K, kappa = 10 cm2/g at 1000 GHz, beta = 1
- 2018A&A...619A.161C: grain size ~3 x lambda
- 2018A&A...619A.161C: gap width ~20 au at ~68 au, alpha = 1e-3
- 2025A&A...694A.295P: kappa = kappa0 (nu/nu0)^beta with kappa0=10 cm2/g, nu0=1000 GHz, beta=1; T_dust = 25 (L/Lsun)^1/4 K (110-246 K); T_dust=150 K for serendipitous sources; d = 1.…
- 2025A&A...694A.295P: Grid 10x10x5: total mass 5e-4 to 5e-1 Msun, outer radius 20-500 au, inclination 15-75 deg; inner radius 11.2 au
- 2025A&A...694A.295P: Free: Sigma_i, q, r_turn, beta; fixed: R_i,dust, R_out, inclination, temperature exponent p=-1
- 2025A&A...694A.295P: R_out set to half the beam size of the image; dust inner radius at 1500 K sublimation temperature
- 2020ApJ...904..181L: Beam size 0.14 arcsec; molecular weight per hydrogen molecule 2.8
- 2020ApJ...904..181L: Circular aperture diameters: 0.5, 1.0 and 1.5 arcsec
- 2020ApJ...904..181L: M1: pure Keplerian, 20 M☉, 25 degree; M2: pure Keplerian, 4.76 M☉, 60 degree; Table 1 rounds the latter mass to 4.8 M☉
- 2020ApJ...904..181L: M3: Keplerian azimuthal motion around 4.76 M☉ at 60 degree, plus constant radial infall 2.5 km s^-1
- 2020ApJ...904..181L: M4: Ulrich accretion-flow velocity field; arbitrarily assumed centrifugal barrier 90 au
- 2020ApJ...904..181L: Surface-density profile r^-1.1; at 900 au M1 has 0.79 g cm^-2 and M2–M4 have 0.71 g cm^-2
- 2020ApJ...904..181L: Temperature: 430 K at r < 214 au; 430 (r/214)^-0.7 K at r ≥ 214 au
- 2020ApJ...904..181L: CH3CN abundance 2 × 10^-8; abundance truncated at radius 900 au; turbulent velocity 2 km s^-1
- 2025A&A...693A.286S: kappa_nu = 10 cm^2/g at 1000 GHz scaled as nu^beta with beta = 1
- 2025A&A...693A.286S: 10^5 bootstrap samples
- 2025A&A...693A.286S: Upper limits for IMTT disks mostly reach the maximum disk mass in the model grid
- 2025A&A...693A.286S: Both planet mass and minimum mass M sin i used; no detection method restriction
- 2023MNRAS.518.6092L: H_100 in [5, 10] AU (6 grid points); beta in [1.00, 1.15] (4 grid points); gamma in [0.3, 1.5] (7 grid points); M_dust in [10^-7, 10^-2] M_odot (11 grid points…
- 2023MNRAS.518.6092L: Fixed parameters: M_* = 0.58 M_odot, T_eff = 3792 K, L_* = 0.7 L_odot, R_in = 0.1 AU, R_out = 80 AU, R_gap = 33 AU, sigma = 27 AU, eta = 0.99, H_ratio = 0.2, D…
- 2023MNRAS.518.6092L: 160 wavelengths logarithmically distributed in [0.1, 10000 um]
- 2023MNRAS.518.6092L: Power-law interpolation range = [6 AU, 60 AU]
- 2023MNRAS.518.6092L: Mean molecular weight mu_m = 2.34
- 2016ApJ...816...37V: L_FIR 42.5–122.5 um; L_TIR 8–1000 um rest-frame
- 2016ApJ...816...37V: D=1.5x deconvolved size; i=25, 50 deg; 55 deg and 3±1 kpc for J2348–3054
- 2025ApJ...993L..40S: 0.5<z<1.5 for the stellar-mass comparison
- 2025ApJ...993L..40S: SFR adjustment ≈0.1–0.2 dex upward at log(Mstar/M⊙)>10
- 2025ApJ...993L..40S: r21: 0.8→1.0; Tdust: 25→20 K; αCO reduced by 4.4
- 2021A&A...652A..66P: box priors log Mdust > 0 and beta in (1, 2.5)
- 2021A&A...652A..66P: Gaussian prior on T_dust, mean 47 K, sigma 5 K
- 2021A&A...652A..66P: companions refit with T_dust prior centred on 35 K
- 2021A&A...652A..66P: nu_0 = 352.7 GHz for k_d(nu) = k_0 (nu/nu_0)^beta
- 2021A&A...652A..66P: gas-to-dust ratio 100
- 2021A&A...652A..66P: alpha_CO = 0.8 (K km/s pc^2)^-1
- 2021A&A...652A..66P: composite model W_PDR F_PDR + W_XDR F_XDR at N_H = 1e23
- 2021A&A...652A..66P: X[CI]/X[H2] = M_CI/(6 M_H2) = (8.4 +/- 3.5)e-5
- 2021A&A...652A..66P: chi(N) = 9.3e-5 for the minimum H+ mass
- 2015A&A...583A..66H: stellar mass 0.5 Msun; other parameters free
- 2014ApJ...796....1T: Td = 10-42 K, beta=0.5, kappa0.9mm=0.053 cm2/g, d=140 pc
- 2017ApJ...835..213P: Tgas=150 K, nH2=3e4 cm-3 fixed
- 2017ApJ...835..213P: Tdust=40 K, kappa(333 GHz)=0.28 cm2/g
- 2018A&A...614A.113H: radial velocity 1 km/s, turbulence 1 km/s, temperature power-law index -0.5
- 2014ApJ...796...84R: T_dust=30 K, beta=1.5 for dust mass limit
- 2024MNRAS.527.3559P: PA and i fixed to the HG values
- 2024MNRAS.527.3559P: Maximum grain size 1e4 micron, minimum 0.1 micron
- 2024MNRAS.527.3559P: Porosity grid 0.0 to 0.8 in steps of 0.2
- 2024MNRAS.527.3559P: Scattered-light best-fit parameters applied: P=0.6, q=3.0, r0=88 au, Delta r=30 au; dust mass then fitted to 1 Mearth
- 2024MNRAS.527.3559P: q=3.0, dust mass fixed to 1 Mearth in both scattered light and SED
- 2018ApJ...869...10M: NICMOS F160W: 69 modes, 125 reference images; SPHERE: 100 PCA modes, 610 images from 22 stars
- 2018MNRAS.479.1154B: log-uniform SFR 10-9000; uniform log f_nth 0.5-1.5; alpha 0.1-1.6
- 2021A&A...645A..49G: Three components; 24 fitted line and continuum quantities; 12 free physical parameters; sizes treated as derived
- 2021A&A...645A..49G: Add 15% Herschel and 10% ALMA systematic uncertainties in quadrature
- 2021A&A...655A..98A: kappa(850 um) = 1.7 cm^2 g^-1
- 2021A&A...655A..98A: Two absorption coefficients: kappa(850) of Sodroski et al. 1987 and the Gordon et al. 2014 kappa_160 = 9.6
- 2024MNRAS.535..729P: 3-sigma clipping for sky; 1'' cross-match radius for NGC 6822 stars; target PSF 25'' (41''/43'' for NGC 1566 and NGC 6822); resampled pixel scale 25'', 43'' (N…
- 2024MNRAS.535..729P: Posterior ranges: 5 < log M_*/M_sun < 11, -5 < log SFR/(M_sun yr^-1) < 1.5, 5 < log L_dust/L_sun < 10, 2 < log M_dust/M_sun < 7; T_dust warm 30–70 K, cold 15–2…
- 2024A&A...681A..17D: 150 shells logarithmically spaced from R_star to R_out (R_out = 350 R_star for F01, F13; 400 R_star for F02; 600 R_star for F03, F04)
- 2024A&A...681A..17D: Turbulent velocity v_turb = 3 km/s; wind velocity exponent beta = 0.5 (R_star to R_dust) and beta = 3 (beyond R_dust)
- 2021A&A...654A..90L: IR integration range = 8-1000 um; dust emissivity index beta = 1.8 for MBB test; radio spectral index alpha_r measured from 1.4/3/5.5/100 GHz data or fixed to …
- 2020MNRAS.498.1319M: BD expected at ~0.25'' separation towards the NE
- 2020MNRAS.498.1319M: Dust accretion rate onto BD from the debris disc ~4 kg/s using Bonsor et al. 2018 with corrected K_ej = 5.14e8
- 2020MNRAS.498.1319M: Gap depth fixed to 1
- 2020MNRAS.498.1319M: Vertical extent fixed to 5% of radius, uniform vertical mass distribution
- 2020MNRAS.498.1319M: r_min lower limit of 14 au; outer edge fixed at 250 au
- 2020MNRAS.498.1319M: Free parameters include disc inclination and PA, phase centre offsets, and position, size (2D Gaussian) and flux of a background SMG ~11.5'' to the SW; spectra…
- 2020MNRAS.498.1319M: Reported values are posterior medians with 16th and 84th percentile uncertainties
- 2024ApJ...977..190X: Fixed dust continuum size 0.9 × 0.7 kpc².
- 2024ApJ...977..190X: L_TIR integrated over 8–1000 μm; L_FIR over 42.5–122.5 μm.
- 2024ApJ...977..190X: β = 1.6; T_dust = 47 K; dust continuum size 1.2 × 1.0 kpc².
- 2015ApJ...800...70S: Td = 100 K (Arp 220), 25 K (NGC 6240); beta = 1.8
- 2020ApJ...891..164S: Td = 20, 60, 150 K tested; 60 K adopted
- 2026ApJ...998..277M: kappa_nu = 1.89 cm^2 g^-1 at 0.87 mm
- 2026ApJ...998..277M: Dust-to-gas mass ratio Z = 0.0027 and mean atomic mass per hydrogen mu = 1.41
- 2019MNRAS.483..806R: nu0=94 GHz; Tc=178 K (A), 181 K (B)
- 2019A&A...626A.126A: free-free contribution to ALMA 0.47-1.01 mJy, uncertainty +/-0.27 mJy added in quadrature
- 2013ApJ...777...92S: kappa(1.3mm)~1.5 cm2/g, gas-to-dust 200
- 2021NatAs...5..586Y: Divine-type distribution: alpha = 3.5, a_min = 1 um, a_max = 1 cm, peak a_p = 1 mm (area-weighted peak a_p' = 2.3 mm)
- 2021NatAs...5..586Y: Single effective dust size ~ 5 mm
- 2021NatAs...5..586Y: Aperture radius = 5"
- 2025A&A...694A..86Y: Mean sigma_v = 4.4 km/s
- 2025A&A...694A..86Y: Continuum limit 5 sigma = 0.2 mJy/beam at 226 GHz
- 2015MNRAS.449..715W: column density threshold 5 x 10^22 cm^-2
- 2015MNRAS.449..715W: k_nu = 0.04 cm2 g-1 (nu/505 GHz)^1.75
- 2020ApJ...894L..14L: T_dust = 20 K, R = 100, kappa = 0.899 cm2/g, d = 8.178 kpc
- 2013ApJ...762L..21M: kappa = 2.7 cm^2/g; outer belt T ≈ 25 K
- 2019MNRAS.488.1005P: slope -1; r_c = 0.4 or 0.04 R_Hill; minimum radius r_c/10; aspect ratio 0.1; 2 deg inclination to planet orbit
- 2019MNRAS.488.1005P: dust size 1 um to 1 cm, exponent -3.5; opacity 2.3 cm2/g at 1.3 mm
- 2019MNRAS.488.1005P: alpha = 1e-4 and 1e-3; disc temperature 40 K; dissipation 1 Myr; initial solid mass 1e-4 Mp
- 2021A&A...650A.153D: Herschel upper limits: average fluxes in BCG-centered apertures with sizes equal to the respective beams
- 2025ApJ...986L..22R: Tss=95±9 K (NEATM) or 60 K (CO)
- 2026MNRAS.548ag325W: Maximum shell velocity = 3500 km s^-1; radial density profile proportional to r^-2
- 2021A&A...650A..37D: dust temperature ~20 K
- 2024ApJ...963....1O: beta = 1.8, kappa_500um = 0.051 m^2/kg
- 2014MNRAS.444.1821F: kappa = 1.7 cm2/g at 870 um
- 2019A&A...623A..77S: H/R=0.1, inclination 10 deg, 20 Msun, CH3CN abundance 2e-8 at 500 au, grid 152x20
- 2019A&A...623A..77S: T = 279 K averaged from model between 10 and 2000 au
- 2016ApJ...831..125P: kappa = 2.3 cm2/g at 230 GHz, nu^0.4; d = 160 pc
- 2016ApJ...831..125P: Mass error = half of 68% range; ±0.1 dex for fixed-isochrone sources
- 2024A&A...682A..61C: Inner Gaussian extends 1.4 arcsec (2 sigma, 574 au)
- 2024A&A...682A..61C: uv-plane check: uvmodelfit point source, 16.1 mJy in B6 and 2.6 mJy in B3
- 2024A&A...682A..61C: d = 420 pc
- 2024A&A...682A..61C: Streamer: DSHARP kappa_1.3mm = 0.4 g/cm2; inner region: T = 20 K, kappa_1.3mm = 2.25 g/cm2
- 2024A&A...682A..61C: Dust-to-gas ratio 0.01; free-fall time ~50 kyr
- 2020ApJ...904...78S: beta ~ 1.78 for ALMA (870 micron)
- 2020ApJ...904...78S: beta ~ 1 for VLA (9 mm)
- 2020ApJ...904...78S: chi^2 weights w_vis = 0.5, w_SED = 1
- 2020ApJ...904...78S: Protostar temperature 4000 K; luminosity L* free
- 2020ApJ...904...78S: Dust: 60% silicate, 15% amorphous carbon, 25% porosity; minimum grain size 0.005 micron; envelope max grain 1 micron; disk max grain size and p (2.5-4.5) free
- 2020ApJ...904...78S: SMA visibilities not fit
- 2025ApJ...995...98D: r_c = 100 AU; gamma = 1.0; r_in = 0.055 AU; r_out ~1000 AU
- 2025ApJ...995...98D: Inclination 47.5°
- 2025ApJ...995...98D: gamma ~0.4; r_c ~300 AU; alpha_v ~10−3
- 2025ApJ...995...98D: r_drift = 300 AU; a_drift ~0.01 cm; u_frag = 750 cm s−1
- 2021A&A...648A..33M: Small-grain split: 10<a_max<200 micrometers; large-grain split: 200 micrometers<a_max<10 cm.
- 2021A&A...648A..33M: Optical-depth posterior marginalized over T_d.
- 2021A&A...648A..33M: Inner profile normalized to Sigma_d at 20 au; gamma explored between 1 and 1.5.
- 2017MNRAS.465.4390B: average of (T=47K, beta=1.6) and (T=41K, beta=1.95)
- 2025A&A...695L..15F: Flat priors 1e-2<A<33 kpc^2, 12.6<T_d<300 K, 1e6<M_d<1e10 Msun, 1<beta<3
- 2025A&A...695L..15F: Same flat priors on A, T_d, M_d, beta as the central-beam fit
- 2025A&A...695L..15F: Upper limit on A set by the beam area
- 2025A&A...695L..15F: Sigma_SFR = SFR/A with A the intrinsic emitting area from the fit
- 2023MNRAS.521.2962F: 1000 Monte-Carlo realizations fluctuating UV luminosity, IR size, and fluxes within 1-sigma Gaussian errors
- 2023MNRAS.521.2962F: Fixed clumpiness parameter log(xi_clp) = -1.02 +/- 0.41
- 2014ApJ...791L...6W: initial size 1 μm, alpha=2e-3, M*=2.4 Msun, dust mass 5e-4 Msun
- 2014ApJ...797...27F: kappa_0 = 0.1 cm2/g at 1000 GHz; beta 1.8 (SM1N), 0.4 (SM1) from SMA/ALMA
- 2019A&A...623A.153O: R_out = 3000 au, inclination 10 deg, Teff 8500 K, a_min 0.01 um, p = -3.5, silicate plus water ice
- 2026A&A...705A.203W: Fiducial ring: r0=75 au, σ=7.4 au, Σ0=0.12 g cm−2
- 2026A&A...705A.203W: Background: Σbg=6×10−3 g cm−2, peak 103 au, width 43 au
- 2026A&A...705A.203W: Dust: n(a)∼a−3.5, 0.8 μm–1 cm; material density 3.3 g cm−3
- 2026A&A...705A.203W: Fiducial 50 M⊕; low-mass 0.15, 2.5, 5 M⊕; high-mass 250 M⊕
- 2019ApJ...880..157D: Tex=100 K; Tdust=35-45 K; beta=1.6
- 2022A&A...659A..46B: 10 photometric bands (FUV to K) for stellar SED; 8 IR bands (WISE 22 um, MIPS 24, 70 um, PACS/SPIRE 100, 160, 250, 350, 500 um) for dust SED; 0.4 kpc elliptica…
- 2022A&A...665A..82O: Grain size distribution power-law index = -3.5, a_min = 0.001 um, a_max = 1.0 um; R_out = 10000 au; initial T_* = 2500 K; T_d(R_in) = 1000 K (for standard enve…
- 2022A&A...665A..82O: R_in = 4e14 cm; R_out = 3 * R_1/2; v_turb = 1 km s^-1; T_min = 7.5 K; 82 rotational levels (up to J=40, v=0 and v=1); ortho-to-para-H2 = 3
- 2024ApJ...962..196O: Nebular emission turned off
- 2026A&A...711A.159M: Spherical grains of radius 0.1 um; warm silicate optical properties from Suh (1999)
- 2021ApJ...908..235I: T_d = 47 K, beta = 1.6; L_FIR over 42.5-122.5 um, L_TIR over 8-1000 um
- 2023A&A...674A..66Z: kappa_nu = 4.9 cm^2/g at 340 GHz (0.88 mm), 2.3 cm^2/g at 230 GHz (1.3 mm), 0.33 cm^2/g at 33 GHz (0.9 cm), 0.10 cm^2/g at 10 GHz (3 cm), 0.06 cm^2/g at 6 GHz …
- 2023A&A...674A..66Z: T_dust = 20 K, kappa_nu = 2.3 cm^2 g^-1
- 2024ApJ...964...95S: κ850μm = 3.8 cm² g−1.
- 2019ApJ...881L..42C: F=0.2 mJy
- 2023Ap&SS.368...33M: Frequencies: 216.90, 218.31, 220.11, and 220.56 GHz
- 2026ApJ..1004L...6D: Integrated continuum flux density within the extraction beam
- 2026ApJ..1004L...6D: 20% NH2 uncertainty
- 2019A&A...628A..27B: Td = 150 K, mu_H2 = 2.8, D = 8.34 kpc
- 2023PSJ.....4..206R: Three compositions: crystalline olivine (Cry-Oli), amorphous olivine (Amo-Oli), amorphous pyroxene (Amo-Pyr)
- 2024ApJ...968L..11G: T = 20 K, kappa = 0.002 cm^2/g at 102 GHz and 0.018 cm^2/g at 350 GHz
- 2014ApJ...795L..25R: kappa_3mm = 0.27 cm2/g
- 2020ApJS..251...14H: kappa = 0.867 cm2/g at ~226 GHz; d = 8.178 kpc
- 2017A&A...606A.121L: Td = 50-200 K
- 2016ApJ...828...46A: T_dust = 20 K; kappa = 10 cm^2/g at 1000 GHz; beta = 1
- 2024A&A...687A.217D: 8 MBB components, 10-50 K
- 2024A&A...687A.217D: Opacity index fixed to beta = 1.8
- 2024A&A...687A.217D: 1.25'' pixels, 2.5'' synthetic resolution
- 2024A&A...687A.217D: Reference opacity kappa_300 = 0.1 cm2/g
- 2024A&A...687A.217D: Maximum 10 000 iterations
- 2024A&A...687A.217D: Dilution eta = 0 (internal default N_prior/N_states)
- 2024A&A...687A.217D: Cells of 60 px, overlap 40 px (50 px in some cases giving 7x7 mosaics)
- 2024A&A...687A.217D: High-pass option on, subtracting a constant background from model images at ground-based wavelengths
- 2024A&A...687A.217D: Temperature range lowered per region after a first run (example G012.80: 21-39 K)
- 2022A&A...662A...8M: d = 2 - 5.5 kpc; S^int_870μm > 25 Jy
- 2022A&A...662A...8M: robust = 0; spectral index α = 3.5; central frequencies ν_B6 = 228.965 GHz, ν_B3 = 100.713 GHz; FOV down to 15% primary beam sensitivity
- 2022A&A...662A...8M: Bright core flux threshold = 400 mJy * (3.9 kpc / d)^2
- 2026A&A...706A.214V: kappa(1000 GHz) = 10 (units as printed: g cm^-2), kappa proportional to nu^beta with beta = 1
- 2026A&A...706A.214V: 10% uncertainty from ALMA flux calibration
- 2026A&A...706A.214V: flaring angle phi = 0.02
- 2026A&A...706A.214V: RADMC-3D: outer radius 150 au, inner dust disk of 1 au depleted by delta_dust, scale height h(r)=h_c (r/r_c)^psi with psi = 0.15 and r_c = 50 au
- 2026A&A...706A.214V: 30 K cutoff (CO snowline values of 18-35 K in the literature; 22-30 K range shown in profiles)
- 2026A&A...706A.214V: 10% uncertainty from ALMA flux calibration; upper limit (total dust mass) used for WX Cha and Sz73
- 2022A&A...661A..53V: 16 galactic longitude bins (oversampled by factor of 2) for distance interpolation
- 2022A&A...661A..53V: OPTICS min_samples = 5, minimum reachability steepness xi = 0.05, minimum cluster size = 50 members of Class II or earlier
- 2022A&A...661A..53V: 10 longitudinal bins listed in Table (209.5 to 214.2 deg)
- 2019ApJ...874...27T: tau_SFH = 0.3 Gyr; M_tot = 2e10 Msun; (eta_WNM, eta_CNM, eta_MC) = (0.5, 0.3, 0.2)
- 2024ApJ...965..108U: Logarithmic: SFR, stellar mass, dust luminosity, dust mass
- 2024ApJ...965..108U: Linear: dust temperature, E(B−V), IRX, β, δ, bolometric AGN luminosity
- 2024ApJ...965..108U: Apply −0.37 dex to stellar masses of AS2UDS, ASAGAO, ALESS, ASPECS
- 2024ApJ...965..108U: Temperature comparison: Herschel detections over 2σ for ALCS, ASPECS, AS2UDS; well-sampled ALESS subset
- 2024ApJ...965..108U: Characteristic temperature Tdustpeak[K]=5099/λpeak[μm]; ALCS conversion approximately 1.7×Tdust
- 2020MNRAS.499.5241C: dust emissivity index beta = 1.8 fixed
- 2020MNRAS.499.5241C: upper limits for non-detections: 5 x r.m.s. of the tapered image
- 2014ApJ...791...20R: R_in = 0.05 AU; free parameters M_disk (Sigma_10AU), p, R_out
- 2014ApJ...791...20R: Grain size distribution n(a) ∝ a^3, amin 0.1 micron; T_ext = 10 K (5, 15 K tested); T ∝ R^-3/4 beyond R_thin
- 2015ApJ...814...22E: T_dust mass-weighted 111 K; opacity 1.48e-2 cm2/g; gas-to-dust 100
- 2017MNRAS.468L..87C: T_dust <= 14 K upper limit from PACS 160 um
- 2017A&A...601A...5H: 10^5 grid points plus 10^4 boundary points; inclination 82 deg
- 2026MNRAS.545f2150S: Ring radii = 20-100 au; ring width = 1 px (0.2 au)
- 2026MNRAS.545f2150S: Stellar effective temperatures T_eff = 7000 K, 7500 K, 8000 K
- 2019ApJ...875...87D: 50 walkers, 10^5 samples; 0.15 au per pixel
- 2018Sci...362.1034D: Tdust 50–100 K for W2246, 25–50 K for companions/extended
- 2022ApJ...928..150T: Ring aperture for HST continuum regression typically ~5 to 8 arcsec
- 2026A&A...707A..77H: M_dust,out = 0.01 x 10^([O/H]-[O/H]_sun) x M_mol,out with [O/H]_sun = 8.77
- 2024A&A...686A.274V: CW Leo dipole inclined 45 deg, PA 125 deg
- 2024A&A...686A.274V: turbulent velocity 1 km/s; gas mean particle mass 2.35 AMU
- 2021MNRAS.500.3667S: nu_0 = 3 THz (100 um) where tau = 1; beta = 2 fixed for HS 0810+2554; H1413+117 photometry > 300 GHz scaled by 0.8 for neighbour confusion
- 2021MNRAS.502.5390P: s_min, q_SED (fixed to 3.5 for HD 160305), M_dust, s_max = 10 cm (fixed), R_disc and Delta R_disc (fixed to resolved values), warm belt Delta R_disc/R_disc = 1…
- 2025Natur.641.1137B: r_31 = 0.8, r_71 = 0.2, alpha_CO = 0.8 M_sun (K km s^-1 pc^2)^-1; dust beta = 0.7, T_dust = 20 to 60 K.
- 2023MNRAS.525.2229M: T_d = 150 K for MM1 and MM3, 30.1 K for other cores
- 2023MNRAS.525.2229M: kappa_nu = 0.90 (nu/230 GHz)^beta cm2/g, beta ~ 1.7
- 2026ApJ...999..194I: kappa_nu = 1.89 cm^2 g^-1 at 870 um (thin ice mantles), dust-to-gas mass ratio Z = 0.0024, T_d = 150 K (range 80–180 K), core extent = 6.5 x 10^3 au
- 2017ApJ...849...25L: Td=35 K, beta=1.5 from SED; 100 K for MM4/7/8/11; 20 K for starless candidates
- 2019A&A...628A..85V: beta=1, kappa_1000GHz=10 cm2/g, T=20 K (30 K test), d=414 pc
- 2024ApJ...976..241Y: R_gd = 100
- 2024ApJ...976..241Y: kappa = 0.18 cm2/g at 3 mm
- 2024ApJ...976..241Y: T_dust = 25 K
- 2024ApJ...976..241Y: kappa_1.3mm = 0.899 cm2/g; T = 25 K; mu = 2.8
- 2023MNRAS.525.6146W: kappa(1.05 mm) = 1.45 cm2/g
- 2023MNRAS.525.6146W: MM1 T_dust = 163 K; MM2-MM5 T_dust = 15 and 24 K
- 2023MNRAS.525.6146W: sigma_obs = 0.58 +/- 0.03 km/s (mean across FWHM size of MM4); radius ~2000 AU
- 2025A&A...693A..49S: kappa = 10 cm2/g at 1000 GHz, power-law beta = 1
- 2025A&A...693A..49S: Flux calibration error 20% NOEMA, 10% ALMA propagated to mass error
- 2025A&A...693A..49S: Stars limited to 300-475 pc, projected distances only
- 2025A&A...693A..49S: Cutoff 10 pc (alternative 30 pc), no interstellar extinction
- 2021A&A...647A.118L: γ=1; ψ=0.1, 0.2, 0.3; h_c=0.1, 0.2 rad; R_c=60 au
- 2021A&A...647A.118L: M_gas=10^-5, 10^-4, 10^-3, 10^-2, 10^-1 M_sun
- 2021A&A...647A.118L: T Tauri: T_eff=4000 K, L_*=1 L_sun; Herbig Ae: T_eff=10000 K, L_*=10 L_sun
- 2021A&A...647A.118L: Accretion UV: 10000 K blackbody onto a 1 M_sun, 1.5 R_sun star; default accretion rate 10^-8 M_sun yr^-1
- 2021A&A...647A.118L: Fiducial: 10^-2 M_sun, ψ=0.2, h_c=0.1, T Tauri star
- 2026ApJ..1000..159M: β_dust = 2.0, κ_UV = 5.0 x 10^4 cm^2 g^-1, κ_0 = 30 cm^2 g^-1 at 100 µm, log ξ_cl = -1.0
- 2026ApJ..1000..159M: r_e,dust = r_e,UV (105 ± 9 pc for GHZ2, 260 ± 20 pc for GS-z14-0)
- 2026ApJ..1000..159M: Gravitational magnification µ = 1.3 (GHZ2) and µ = 1.17 (GS-z14-0)
- 2026ApJ..1000..159M: Star formation start redshift z = 20 (GHZ2) and z = 30 (GS-z14-0)
- 2026ApJ..1000..159M: Yield metallicity range = 10^-4 to 0.1 Z_sun
- 2026ApJ..1000..159M: Larson IMF with α = 1.35 and M_ch = 0.35 M_sun (and M_ch = 10 M_sun for top-heavy test), mass range 0.1-100 M_sun
- 2021A&A...655A..42S: Td = 25 K, beta = 1.8, kappa(450 um) = 1.3 cm2/g
- 2021A&A...655A..42S: r41 = 0.37 ± 0.12; alpha_CO = 4.5 ± 0.1 for Z/Zsun = 0.84 ± 0.02 (SGASJ0033-A); delta_GDR = 117; X[CI] = 1.3 ± 0.8 x 10^-5
- 2021A&A...655A..42S: gas-to-dust ratio: delta_GDR ∝ Z^gamma, normalised to 100 at solar, gamma = -0.85
- 2014ApJ...791...42Z: 150 LM runs; uncertainties from Hessian
- 2016PASJ...68...20S: kappa_352 = 0.43 cm2/g; T_d = 35 K; gas-to-dust 264 ± 68
- 2019A&A...629A.146V: d = 123 pc; R* = 4e13 cm; T* = 2330 K; Mdot = 2.7e-5 Msun/yr; vexp 5/11/14.5 km/s; microturbulence 1 km/s; gas-to-dust 300
- 2015MNRAS.452.2258D: kappa_850 = 0.077 m2/kg
- 2026A&A...705A.197Z: Fiducial scale heights and millimeter dust masses; stellar masses from Marino_2026.
- 2026A&A...705A.197Z: Perturbing-body eccentricity 0.03; bulk density 2.0 g/cm³.
- 2019MNRAS.486.5552B: p=-3.5, s_max=5 mm
- 2023ApJ...953..113L: Fitted wavelength range: 50-250 um
- 2020MNRAS.491..758A: T_dust = mean 30.8 K; K_d = 20 cm2/g; dust-to-gas 1:100
- 2024ApJ...971..176H: Clean threshold 2 x RMS, RMS ~0.18 mJy/beam
- 2024ApJ...971..176H: kappa = 0.9 g^-1 cm^2; T_dust from Klaas et al. 2010 per subregion (about 20 K)
- 2020ApJ...903...34A: Opacity kappa = 2.64 (nu_rest/(c/125 um))^beta m^2/kg
- 2021AJ....162..235Y: Disk emission spread over ~7 beams
- 2024ApJ...977L..46B: T_d = 47 K, beta = 1.6, integration over 8-1000 um
- 2014ApJ...787...48X: T=43.0 K, kappa_690GHz = 0.16 m2/kg, D=84 Mpc
- 2020A&A...644A..84M: flux 0.1 Jy at 99.0 GHz
- 2016ApJ...827..142B: upper limits = 3σ plus any positive flux
- 2024A&A...686A.122A: Flat prior on log(T); fixed beta = 1.8 with +-0.2 explored; kappa_300 = 0.1 cm2 g-1 per gas+dust mass
- 2024A&A...686A.122A: Eight modified blackbody components between 21 and 39 K; output resolution 2.5 arcsec; flux uncertainties 15% LABOCA, 20% SABOCA, 10% PACS, 7% SPIRE, 20% HAWC+…
- 2024A&A...686A.122A: d = 2.4 kpc; kappa_1.3mm = 0.01 (+0.005/-0.0033) cm2 g-1
- 2022MNRAS.512.4419P: Gas-to-dust mass ratio eta = 100
- 2022MNRAS.512.4419P: Mean molecular mass per H2 molecule mu = 2.8
- 2022MNRAS.512.4419P: Dust absorption coefficient kappa_nu = 0.899 cm^2 g^-1 at 1.3 mm
- 2024A&A...684A.200G: Mean dust temperature 50 K; κν(1.3 mm) = 0.02 cm^2/g.
- 2024A&A...684A.200G: Compare with κν(1.3 mm) ∼5–10 cm^2/g.
- 2024A&A...684A.200G: Inner radius 0.6 au; outer-component dust mass 2 × 10^-5 M⊙.
- 2024A&A...684A.200G: Model CS: 25% carbon grains; model Q: inner component of quantum-heated particles.
- 2021ApJ...908..250H: Free parameters r_cav1_large, r_cav2_small, h_small(100 au), M_disk
- 2021ApJ...908..250H: r_cav2_large fixed to 26 au from the visibility fit
- 2021ApJ...908..250H: q1 = -1.0, q2 = 4.5 (fiducial)
- 2021ApJ...908..250H: Scale height of large grains fixed at 1 au at 100 au; small grains varied to match 60-70 um flux
- 2021ApJ...908..250H: Large-grain mass fraction 0.9; accretion rate 1.3e-9 Msun/yr; inclination 75 deg
- 2024A&A...686A..64M: Template choice based on median redshift and ΔMS
- 2024A&A...686A..64M: Redshift-dependent dust-mass rescaling from Leroy et al. in prep
- 2024A&A...686A..64M: High-mass bin: 10^10–10^11 M⊙
- 2021ApJ...921...97J: 15% calibration/lensing error added in quadrature; upper limit on effective radius = 5000 pc (W) and 1300 pc (E)
- 2021ApJ...921...97J: F-test p-value < 0.05 for alpha_CO vs T_dust slope
- 2013A&A...557A.132M: h_small 0.08, h_large 0.06, h_main 0.1, h_tail 0.2, f_tail 0.05
- 2015ApJ...813L..19J: Td=190 K, gas-to-dust 154, kappa(1.21 mm)=0.24 cm2/g
- 2019ApJ...871..170M: Rgd=150, beta=1.5, Td=35 K, D=3.5 Mpc
- 2018A&A...614A..17B: Grain size 0.1 µm, density 1.8 g cm-3, condensation temperature 1500 K, Suh (2000) optical constants
- 2015Natur.519..327W: T = 35 K, βIR = 1.92, λ0 = 200 µm
- 2024AJ....168..142L: Free: minimum grain size, porosity, dust mass, PA, inclination, inner radius, outer radius and critical radius.
- 2019ApJ...872...92F: T_dust = 20 K; opacity 2.3 g cm^-2 at 1.3mm
- 2022MNRAS.509.2920N: 3 MGE Gaussian components for ISM (Table 3)
- 2023A&A...669A..56Q: Outflow C total mass = 0.05 M_sun; cold spot area = 2.8 x 10^23 cm^2; formation time = 50 yr
- 2026ApJ..1005...94N: Mask threshold = 0.5 sigma_RMS in unsmoothed cube (8 sigma_RMS in smoothed cube); integrated spectrum aperture = 6'' x 6''; PVD pseudo-slit width = 2 pixels (0…
- 2024AJ....167...94H: T* = 3500 K, R* ~ 7 AU
- 2021MNRAS.504.4123N: 6 Gaussian components for F547M PSF (Table 2); 7 Gaussian components for F547M stellar light (Table 3); central AGN mask r < 0.06''; M_H2(r <= 3'') = 2.7 x 10^…
- 2023Natur.622..251K: Dust temperature 100 K; grain size 0.1 um (1 um gives a similar spectrum)
- 2017ApJ...843...45K: aperture radius 9 arcsec (6300 au) for extended emission
- 2017A&A...602A..19L: β=1.75 fixed; Te=16000 K
- 2025ApJ...991...59B: Dust temperature = CH3OH rotational temperature
- 2025ApJ...991...59B: I_beam = mean intensity in area within 50% of the 1.2 mm peak contour; 870 um image regridded and smoothed to the 1.2 mm image
- 2025ApJ...991...59B: Dust opacity 1.89 cm^2/g at 870 um and 0.993 cm^2/g at 1.2 mm; gas-to-dust ratio 316
- 2025ApJ...991...59B: LMC and SMC abundances multiplied by 2 and 5; ST11 and N 132-14A abundances recalculated with the same gas-to-dust ratio (and H2 column from same method)
- 2021ApJ...907...94C: Omega = pi/(4.0 log 2) b_maj b_min
- 2021ApJ...907...94C: Column density evaluated only in the filament region used for field-strength estimation
- 2021ApJ...907...94C: Stokes I cutoffs: 900 microJy beam^-1 at 3 mm; 7.3 mJy beam^-1 at 1 mm
- 2025A&A...696A.232G: Grid: 12 dust masses 4e-6 to 5.1e-3 Msun, 12 radii 0.5 to 30 au, 12 stellar luminosities 0.0025 to 3 Lsun, log-uniform
- 2025A&A...696A.232G: Dust opacities from optool with DSHARP opacities, grain sizes 0.050 um to 3 mm, full scattering matrix
- 2025A&A...696A.232G: 28 disks with radii < 30 au fit within the grid and have known luminosity
- 2022ApJ...930L...3W: T_mean = 24 K for SR 12 c (integrated from 1.6 R_Jup to 5 au); T_mean = 29 K for PDS 70 c (integrated to 1 au); T_mean = 20 K for SR 12 AB
- 2022ApJ...930L...3W: Dust opacities: kappa_1mm = 3.63 cm^2 g^-1 and kappa_1um = 0.79 cm^2 g^-1
- 2022ApJ...930L...3W: Accretion rate = 10^(-11.08 +- 0.40) M_sun yr^-1; remaining lifetime = 3 Myr; CO channel rms = ~0.7 mJy beam^-1 per 1 km s^-1
- 2019ApJ...871...85L: uniform priors T_d>1 K, beta in [0.1,20], lambda0 in [1,400] um, alpha in [0.1,20]; extra 15% flux uncertainty
- 2025A&A...694A.218B: L_IR integrated between 8-1000 um
- 2025A&A...694A.218B: M*/Mdust = 50-100
- 2021ApJ...908...15S: BC03 stellar populations with Chabrier IMF; metallicity 0.2-2 solar; delayed exponential SFH with bursts; two-component Charlot & Fall attenuation
- 2021ApJ...908...15S: ALMA non-detections entered as 1.5 sigma +/- 1 sigma flux; dust-mass upper limit taken as 97.5th percentile of PDF; uncertainties are 16-84th percentiles
- 2021ApJ...908...15S: relation scatter 0.15 dex
- 2013Sci...340.1199V: emission area 2544 AU2; total flux 950 mJy; tau=0.43
- 2018ApJ...856..118H: L'CO(1-0)/L'CO(2-1)=1.2, alpha_CO(1-0)=4.36 (4.99–7.31 after metallicity correction)
- 2018A&A...615A..28D: Drift velocity forced below 20 km/s
- 2014ApJ...785..111W: Td=35 K, beta=1.8
- 2026A&A...706A...4R: T = 213 K at 4.7 au (Gaussian), 191 K at 5.9 au (power law)
- 2022MNRAS.510.4485R: <A_lambda> = 2.0 mag (central structure) and 1.7 mag (eastern patch)
- 2020ApJ...889...85H: Td ~150 K; kappa = 0.3 cm2/g at 350 GHz; gas-to-dust 77
- 2025ApJ...995L..63L: Umax=1e6, beta=2, gamma=0.01, 0.47<qPAH<4.6
- 2025A&A...700L..11S: Cold dust peak ~70 um, T ~50 K; spectral index alpha ~3 from ALMA flux to PACS 120 um
- 2021A&A...645A..33B: k_dust = 0.077 kg^-1 m^2 at 850 micron
- 2021A&A...645A..33B: Tdust in 40-75 K from SED fit
- 2019A&A...632A..83S: β=2; Tdust=20 K (50 K for source 1)
- 2016ApJ...819..102V: Disk mass 1e-4 to 1e-7 Msun in 7 log steps; Rout 100 au; Av 0-7; T* 2800-3200 K; R* 0.2-2 Rsun
- 2024RAA....24f5011X: gas-to-dust ratio 100
- 2024RAA....24f5011X: kappa = 1 cm2/g at ~230 GHz (Ossenkopf & Henning 1994, thin ice mantles)
- 2024RAA....24f5011X: eta = 2.4 for deconvolved size
- 2024RAA....24f5011X: mu_H2 = 2.81; mu_p = 2.37; channel width 1.34 km/s; m_H2CO = 30 m_H
- 2024RAA....24f5011X: 30 sources with line width > 7 km/s (outflow wings) assigned an averaged observed velocity dispersion of 1.66 km/s
- 2022MNRAS.515.5730K: threshold = 0.15 Jy/beam, contour spacing = 7 mJy/beam
- 2022MNRAS.515.5730K: Clumpfind threshold = 5 sigma (4.1e21 cm^-2), contour spacing = 3 sigma (sigma = 8.2e20 cm^-2)
- 2025ApJ...984L..16G: Radial domain 4–200 au; azimuth 0–2π; 1024 logarithmic radial cells and 3072 uniform azimuthal cells; open boundaries
- 2025ApJ...984L..16G: Initial planet radii 20, 42 and 90 au
- 2025ApJ...984L..16G: Planet 1 masses 1.3, 3.8, 6.3 MJ; Planets 2 and 3 masses 0.4, 1.3, 3.8 MJ
- 2025ApJ...984L..16G: 0.625 Myr; 5000 orbits at 25 au
- 2021ApJ...910...75L: R_t ~34+-5 au, R_o ~68+-10 au, h_s ~12+-2 au
- 2021ApJ...910...75L: rho_t ~3.0+-0.4e-15 g cm^-3, T_t ~65+-10 K
- 2018ApJ...868...75S: alpha fixed at 2; Umax = 10^6
- 2024A&A...684A..33K: Dust opacity kappa = kappa_nu0 (nu/nu0)^beta with nu0=c/125 um and kappa_nu0=2.64 m^2/kg
- 2024A&A...684A..33K: alpha_CO = 0.8 (K km/s pc^2)^-1, r_2,1 = 1
- 2024A&A...684A..33K: 25-60% of IR luminosity attributed to star formation for SFR
- 2022MNRAS.515.1751W: β_IR = 1.5 fixed; T_dust = 50 K fixed for sources with only upper limits; self-consistent opacity model (plus optically thin and fixed λ_0 = 200 μm variants)
- 2013A&A...557A.133D: Rc 110-140 AU step 5; gamma 0-2 step 0.1
- 2013ApJ...774...73I: kappa=0.62±0.1 cm2/g; x_d=1/339
- 2018ApJ...869...27V: starbursts/SMGs: alpha_CO=0.8, delta_GDR=30; 0.2 dex error on both
- 2016A&A...596A..50G: Fitted: luminosity, dust optical depth, dust temperature at inner radius
- 2025A&A...693A.151M: t0 = 10 Myr, delta = 13/3, epsilon = 1, D ~2e-8 Myr Mearth au^-13/3
- 2017ApJ...850L...6A: D_dust 1 cm, D_max 50 km
- 2020ApJ...896...43W: Continuum integrated intensity in model matched to observations
- 2020ApJ...890L..14T: S=267±25 mJy; Td=100 K; kappa=1.8 cm2/g
- 2024ApJ...963..103G: CO (3-2) channel map velocity range = 864.1–887.8 km s^-1; 3D-Barolo primary S/N = 5, secondary S/N = 3
- 2025A&A...699A..22M: inner radius 0.001-0.01 au; outer radius <= 2 au
- 2021A&A...652A..98G: T_dust=100 K; kappa_351GHz=0.0865 m^2/kg; gas-to-dust ~100; X_CO=2e20; 3-2/1-0 = 2.9 (tori), 0.7 (FOV), 2.0 (200 pc)
- 2019ApJ...884...48C: kappa_230GHz = 0.01 cm2/g (incl. gas-to-dust 100); mu=2.33
- 2017ApJ...851...85B: CO freeze-out below 20 K; photodissociation below 1e21 cm^-2 H2 column, or none
- 2017ApJ...851...85B: S/N >= 15 threshold for well-constrained R_dust
- 2025A&A...701A.219N: Wavelength = 1.3 mm (231.1 GHz), reference distance = 5.2 kpc
- 2025A&A...701A.219N: Reference temperatures: T_f = 20 K (10-40 K) for L/M < 1; T_f = 30 K (10-50 K) for 1 < L/M < 10; T_f = 40 K (20-60 K) for L/M > 10; 1000 MC runs
- 2020ApJ...904...77G: 220 GHz dust excess 119 mJy; 92 GHz upper limit 11 mJy
- 2020ApJ...904...77G: Accretion-rate comparison: 10^-5 M_sun yr^-1
- 2025A&A...698A.165A: d = 98 pc (Gaia DR3)
- 2025A&A...698A.165A: T = 20 K, kappa ~ 3 cm^2 g^-1
- 2025A&A...698A.165A: robust 0.5, 0.0 and -0.5 tested for the alpha map
- 2023A&A...677A..76P: 120 radial and 100 vertical grid points logarithmically spaced; two zones divided at 41 au, outer radius 130 au
- 2023A&A...677A..76P: a_min = 0.001 um, a_max = 3000 um, power index p = 3.9, alpha = 5e-3, H_0 = 10.61 au at r_0 = 100 au, beta = 1.14
- 2023A&A...677A..76P: Dust gap: 16 au to 41 au; inner disk: 0.04 au to 16 au; outer limit: 130 au
- 2024A&A...691A.248L: Detection threshold S/N >= 3; non-detections and z > 4 MIPS 24 um fluxes set to 5 sigma upper limits
- 2024A&A...691A.248L: Effective greybody emissivity beta = 1.5; T_dust^M restricted to S18 evolution +- 10 K when only 1 or 2 points are detected
- 2024A&A...691A.248L: Metallicity uncertainty = 0.2 dex; Scoville et al. (2016) parameters T_d = 25 K, alpha_850 = 6.2e19 erg s^-1 Hz^-1 Msun^-1; beta = 2 fixed in Eq. 20; area scal…
- 2022A&A...664A..63X: U_min = 0.1-50, alpha = 1-3, gamma = 0.0001-1, q_PAH = 0.47-7.32%
- 2015ApJ...801...82H: Tdust fixed to 100 K or 20 K
- 2018ApJ...869..126L: kappa = 1.9 cm2/g; DGR 1/100
- 2017ApJ...841..110S: Deconvolved half-power size ~2.3" at 3.3 mm (radius ~2.6e16 cm)
- 2025A&A...703A..15M: kappa_nu = 2.3 cm^2 g^-1
- 2020A&A...644A..59K: AV = 3 mag; gas-to-dust 124; WD Teff 20 and 60 kK; r=2''; d=0.7 kpc
- 2025AJ....169..230H: Continuum frequency = 249 GHz; integration area = 0.35 arcsec^2; angular distance from star = 1.93''
- 2019A&A...629A..29J: Initial Tav=100 K, icy/bare ratio 0.5, radius 56 au, gas-to-dust 100
- 2017ApJ...848L..11K: Disk radii 30-300 au; disk mass 0.013 M☉
- 2017ApJ...848L..11K: 10^6 particles; 3 MJup planet at 100 au; snapshots after 10 orbits
- 2024AJ....168..151J: Integrated Band 7 flux
- 2024AJ....168..151J: Average temperatures from Jiao_2022 where covered; otherwise Lombardi_2014 at 36″
- 2024AJ....168..151J: Alternative dust temperatures: 15 K and 10 K
- 2020ApJ...890...76N: Apertures of 27" (prestellar) and 20" (protostellar) radius
- 2020ApJ...890...76N: Core radius from geometric mean of Clumpfind semi-axes
- 2026A&A...705A..96M: Inner τ∝r^p with p=0 and −1.5; mass integration R=rc
- 2026A&A...705A..96M: Intensity-weighted temperatures: VLA1623 17 K; L1551 IRS5 44 K
- 2026A&A...705A..96M: Extrapolate κ3mm=1 cm² g⁻¹ to 223 GHz using β=1.1 for L1551, 1.37 for VLA1623
- 2021MNRAS.501.2934C: Azimuthal angles restricted to within 20 deg of the semi-major axis for highly inclined systems (ISO-Oph 37 and WSB 82); combined 0.03'' + 0.2'' image used bey…
- 2019MNRAS.482.3135B: 100 walkers, 500 steps, 100-step burn-in
- 2025A&A...693A.190J: beta = 1.8; kappa = 0.0431 m^2 kg^-1 at nu0 = 352.6 GHz
- 2025A&A...693A.190J: CMB flux correction ~1.03 at z~1 to ~1.31 at z~6; CMB dust-temperature heating ~3% at z=6
- 2023ApJ...952...48H: r_61 = 0.28 +0.04/-0.02, r_71 = 0.17 +0.02/-0.02
- 2023ApJ...952...48H: alpha_CO = 25 M_sun (K km s^-1 pc^2)^-1 (range 5 - 25 for Z = 0.2 - 0.8 Z_sun)
- 2023ApJ...952...48H: DGR ≈ (1.8 - 53) x 10^-4
- 2015ApJ...805L..17B: d = 145 pc; kappa(880 um) = 3.4 cm2/g
- 2017A&A...601L...3P: R = 35 pc; N_H2O = 2e18 or 8e18 x tau100; n_H2 = 3e4 cm-3; Tgas = 150 K
- 2017A&A...597A..99W: CO levels up to J=40, ground and first vibrationally excited states
- 2015A&A...574A..19S: β_IR = 1.5, alpha = 2.9, ν0 = 239.84 GHz
- 2018A&A...615A...9P: kappa = 0.0188 cm2/g at 1.3 mm (beta=1)
- 2018A&A...615A...9P: Td = 35 K with IR counterpart, 15 K without
- 2019ApJ...871....5T: r_pk=95 au, sigma_r=10 au, Sigma_d,0=1.84e-2 g cm^-2, h_d=9.8 au, a_max=1 mm, gas Sigma ~ r^-1 for 8-320 au, h_g=13.2 au (r/95 au)^1.25, gas-to-dust 100
- 2024ApJS..270....9X: η=2.4; R_core=θ_core×D
- 2025NatAs...9.1176R: Dust temperature 20 K (Normal, sigma 2.5 K in bootstrap); beta uniform 0 to 0.5; 1000 bootstrap draws; median and 16/84 percentiles reported
- 2025NatAs...9.1176R: kappa_230GHz = 2.3 cm2/g
- 2025NatAs...9.1176R: N = 1e6 particles; R_out = 50 au; R_in = 1.5 a_p; alpha_AV = 0.2, beta_AV = 2 (alpha_ss = 5e-3); disk mass 0.01 Msun; star 1.3 Msun; H/R = 0.1 at 100 au; grain…
- 2021MNRAS.501.4317P: T = 20 K; kappa_nu = 1.15 cm^2/g_dust (also stated as 2 cm^2/g in Sect. 4.2.3); D = 161.1 pc (HD 144668) and 221 pc (KK Oph)
- 2021MNRAS.501.4317P: Velocity integration range: 0 to 8 km/s; T = 20 K; partition function maximum level J = 40; 13CO relative abundance = 1.3e-6
- 2025ApJ...995..150K: rest wavelength 158 um
- 2025ApJ...995..150K: xi from 1.33 (zero metallicity) to 1.39 (solar)
- 2023MNRAS.523.4654T: Herschel SPIRE 350 and 500 um excluded because of blending
- 2017ApJ...849...81A: nu=353 GHz, D=3.5 Mpc, kappa=0.0865 m2/kg
- 2018A&A...616A..34H: stellar blackbody bandwidth 1.6 GHz around 230.5 GHz
- 2019A&A...626A..93V: Doppler b = 1 km/s; 20 abundance values per molecule; depletion factor 100
- 2019A&A...624A...7V: Free parameters per region: Rin, Rout, dust mass, H100au; beta fixed to 1.1; p = -1
- 2019A&A...624A...7V: Small grains 0.01-0.5 um, large grains 10-1000 um
- 2026AJ....171..368M: n_photons = 3x10^8, r_in = 20 AU, r_out = 4.5x10^3 AU, r_plat = 900 AU, p_env = 1.1
- 2021A&A...650A.202R: Dust opacity kappa = 1.71 cm2/g at the observed frequency (kappa_0 = 10 cm2/g at 250 um, beta = 1.5)
- 2021A&A...650A.202R: Gas-to-dust ratio 100; mu_H2 = 2.8
- 2021A&A...650A.202R: Mass uncertainty set to 33% (30% kappa variation gives 33% in mass)
- 2024ApJ...971L..23L: T_t ~26 K, q ~0.65, rho_t ~3.6e-16 g cm^-3
- 2024ApJ...971L..23L: kappa_0 ~0.12 and beta ~1.4 for the opacity law
- 2024ApJ...971L..23L: Toomre Q ~1 at R_t
- 2023A&A...675A.131T: Aperture radius = 1.625", nu = 277.51 GHz, T_dust = 28.2 K, kappa_nu = 2.8 cm^2 g^-1
- 2023A&A...675A.131T: Radial extent out to ~415 au; C18O used at <=50 au and >=350 au
- 2017A&A...602A..11P: Tex = 30 K
- 2026MNRAS.546f2284B: T_dust(z=0) = 50 K, beta_dust = 2.0, kappa_0 = 10.41 cm^2 g^-1 at nu_0 = 1900 GHz
- 2026MNRAS.546f2284B: f_mu = 4/3, tau_0 = 2.17 x 10^-8 (SMC), tau_1500 = 1.99 (beta_UV - beta_UV,intrinsic), beta_UV,intrinsic = -2.63, r_d = 100 pc (for REBELS-24 and GS-z9-3)
- 2022MNRAS.510.4976A: R_e = mean of deconvolved major and minor axes FWHM / 2; galaxy-averaged Sigma_SFR = (0.5 * SFR_IR) / (pi * R_e^2); peak Sigma_SFR = SFR_IR(peak) / (pi * a * b…
- 2016ApJ...833L...6C: kappa_870=0.9 cm2/g, beta=1.7; Tdust 33 K (Clouds C, W), 20 K (Cloud E)
- 2017A&A...603A..92V: a=0.1 micron, s=0.5, Td=Tg=100 K, n_g≈9e9 cm^-3
- 2017A&A...604A..60B: kappa0 = 1.6 cm2/g at 1.3 mm, beta = 1.2
- 2017MNRAS.468..685Q: Example 1: 10 000 points, 151 channels, 100 m s^-1 spectral resolution, 0.1 arcsec pixel size, 141 pixels
- 2017MNRAS.468..685Q: Benchmarking (Appendix B): 101 992 points in LIME, 191 shells in RATRAN, 71 channels, 100 m s^-1 resolution, pixel size 0.2 arcsec (and 0.02 arcsec test)
- 2024ApJ...962...13C: Dust absorption coefficient kappa = 1.89 cm2 g-1 at 870 um
- 2024ApJ...962...13C: Cold-core T_d equals the clump temperature (23-32 K)
- 2020A&A...636A..26H: q = 0.35, 0.4, 0.5; Sigma ~ R^-1
- 2024AJ....167...75H: Outer disk radius 300 au; inner radius of the outer disk 60 au; inner disk outer radius 1 au assumed
- 2024AJ....167...75H: Mass fraction of large dust grains 0.9 of total dust mass
- 2024AJ....167...75H: Scale height h proportional to r^p with p = 1.15; at r = 100 au h = 1 au (large grains) and 7 au (small grains)
- 2024AJ....167...75H: Viewing direction theta = 0 deg, phi = 60 deg (inclination 60 deg)
- 2020NatAs...4..142L: 6 free parameters: R_t, R_o, q, T_t, p, and n_t
- 2020NatAs...4..142L: Disk axis tilted ~18 deg from plane of sky
- 2017A&A...606A..17M: Starburst: Delta_MS > 3; MS: 1/3 < Delta_MS <= 3
- 2025ApJ...989..115T: nonparametric SFH with 6 bins and continuity prior; SFR averaged over 100 Myr
- 2025ApJ...989..115T: stellar metallicity Z = 0.02 (solar), Calzetti attenuation with power-law slope delta -0.7 to 0.4
- 2025ApJ...989..115T: Draine & Li dust emission with Umin all values above 5.0
- 2022MNRAS.512.2426M: Dust emissivity index beta = 2.0; integration range 3-1100 um
- 2014ApJ...787...42C: kappa=2.3 cm2/g at 230 GHz, beta=0.4, d=145 pc
- 2017A&A...608A..22A: dV=150 km/s
- 2018ApJ...859..111H: 500 walkers, 1000 iterations; uniform priors on Md, gamma, Rc, H100
- 2024ApJ...972..115C: Dust emissivity kappa = 1 cm2 g-1 at 230 GHz; gas-to-dust ratio 100
- 2024ApJ...972..115C: Temperature map extended to the 3 sigma dust contour assuming 30 K outside the model, then smoothed with a Savitzky-Golay filter with a window of one beam
- 2024ApJ...972..115C: MM3 H II region size 3.3'' x 2.5'' from Gaussian fit; Te = 1e4 K, ne = 3e6 cm-3; geometrical thickness as in density model
- 2020ApJ...896...35J: >7 sigma pixels, tau held at zero, NH3 abundance 10^-7.5
- 2024Sci...383..988B: Md=Fdust d²/[kν Bν(Td)].
- 2024Sci...383..988B: Inclination lower bound from disk thickness and radius: i≳90−arctan(Ed/2rd).
- 2023ApJ...948L...2Y: Area within 3-sigma contour = 291 au^2; mean flux density = 8.65e-5 Jy/beam
- 2020MNRAS.494.5542R: Uniform magnification adopted for 160 um to 1.3 mm continuum; Herschel 160-500 um emission assumed to follow the Band 8 surface brightness distribution
- 2020MNRAS.494.5542R: Resolved test of T_dust fixed to 60 K and 80 K, fitting only the normalization
- 2020MNRAS.494.5542R: FIR-bright region defined as Sigma_SFR >= 50 Msun/yr/kpc^2
- 2019ApJ...886..102S: kappa1.3mm = 0.9 cm2/g; T = clump Herschel dust temperature; R = 100; mu_H2=2.8
- 2019ApJ...882..160Q: epsilon tested at 1.0, 0.5, 0.1, 0.01, 0.001; alpha 0.00001–0.02
- 2025ApJ...988...95D: N(H2) = Sν Rgd / [μ mH Ω κν Bν(Tdust)]; Sν is total integrated continuum flux; Ω is beam solid angle.
- 2025ApJ...988...95D: Assumed N(H2) uncertainty 20%.
- 2020ApJ...903...50E: Tdust = 130 K
- 2020ApJ...903...50E: kappa = 1.9 cm2/g
- 2020ApJ...903...50E: DGR = 1/100
- 2026A&A...710A.238D: 32 walkers, 5000 steps after 1000 burn-in steps, repeated a second time around median values; radial step = 1/3 smoothed resolution starting from r = 11 au
- 2026A&A...710A.238D: 5000 bootstrap samples per radius; turbulent viscosity alpha_t sampled uniformly in 10^-4 <= alpha_t <= 10^-2
- 2021ApJ...923..121Y: T_d(r) = 360 (r / 1 au)^-0.5 K
- 2021ApJ...923..121Y: nu_1 = 218 GHz, nu_2 = 233 GHz
- 2017ApJ...837..182O: beta = 2.0; mid-IR slope alpha = 2.25
- 2025A&A...695L..18M: beta = 1.8 fixed; kappa_0 = 13.9 cm2/g; nu_ref = 2141 GHz
- 2025A&A...695L..18M: two free parameters: dust temperature and dust mass
- 2021MNRAS.505.4838L: BAGPIPES: constant SFH, stellar mass 10^6 to 10^12 M_sun, age 0.0 Gyr to age of Universe at z=6.07
- 2017A&A...608A..56G: kappa_349GHz ~ 0.09 m2/kg
- 2019A&A...626A..36D: n=1e6 cm-3 for MM4, MM7, MM8; n=1e5 cm-3 for MM1a, MM3a, MM9, MM6c, MM11a
- 2019A&A...622A..75L: Initial H100=10 au, beta=1.1, Mdust=2e-3 Msun, Lambda=0.2, fLGP=0.85, i=36 deg; R_out,LGP=200 au
- 2024ApJ...974..257Z: kappa = 0.0103 cm^2 g^-1, gas-to-dust 100, 1.2 mm
- 2024ApJ...974..257Z: D = 2.9 kpc; observing frequency 250 GHz, Rayleigh-Jeans
- 2020ApJ...905...25G: Beam area 0.033″×0.024″; τ=1 beam mass 0.36 M_sun
- 2024ApJ...970..114T: T_star = 4000 K, R_star = 7 R_sun
- 2024ApJ...970..114T: R_c = 78.9 AU, gamma = -0.2
- 2024ApJ...970..114T: Scale height h0 = 10 AU at 100 AU, flaring beta = 1.15
- 2024ApJ...970..114T: Gas mass normalized to M_g = 0.1 M_sun (gas-to-dust ratio ~10)
- 2017ApJ...846..108C: dark matter fraction 15%; <sin^2 i>=2/3; median sigma 154±5 km/s
- 2025A&A...701A.120P: κν = κ0(ν/ν0)^β; κν = 0.077 m² kg−1 at 850 μm.
- 2025A&A...701A.120P: Fiducial Tdust: 45 K quasar; 35 K MQN01-QC. SFRIR = 1.49 × 10−10 LFIR/L_sun.
- 2023MNRAS.524..923Z: r_32 = 0.5
- 2023MNRAS.524..923Z: alpha_CO = 4.4 M_sun K km s^-1 pc^2
- 2023MNRAS.524..923Z: beta = 1.8, alpha_850 = 1 x 10^20 erg s^-1 Hz^-1 M_sun^-1
- 2018MNRAS.474.3640M: XDR: 9 models, log n=[3.5-5.5], L(1-100 keV)=4e42 erg/s; shocks v=10-40 km/s, log n=3-6
- 2018A&A...615A..83V: Mstar=0.45 Msun fiducial (0.19 also tested), disk radius 125 AU
- 2024ApJ...961L..35M: Distance D = 3.0 kpc
- 2024ApJ...961L..35M: mu_H2 = 2.8; R_core = (FWHM_major x FWHM_minor)^(1/2)/2 x D
- 2021A&A...650A.142M: Rectangle centered on the HC Hii region, PA = 133°, 8000 × 2000 au
- 2021A&A...650A.142M: Free-free contribution ≥86 mJy
- 2025ApJ...995...16Z: 17 free parameters in total (13 model parameters plus 4 outlier/systematic-uncertainty parameters)
- 2025ApJ...995...16Z: photometry split into critical (2MASS and ALMA) and general (all other) groups
- 2025ApJ...995...16Z: Gaussian priors on M* and parallax centred on literature values; flat priors where literature values are absent
- 2025ApJ...995...16Z: Td = 20 K constant, flux at 1.3 mm (241 GHz), kappa = 2.41 cm^2 g^-1 with beta = 1
- 2021A&A...656A.150P: Integration annulus 1.1''-2.5'' in the SB-only image
- 2021A&A...656A.150P: kappa_nu = 2.3 (nu/230 GHz)^0.4 cm^2 g^-1
- 2021A&A...656A.150P: Dust mass uncertainty taken as 10%
- 2016A&A...596A..75S: kappa at 240um 5.17 cm2/g; 100um band excluded from MBB fit
- 2025ApJ...990L..61C: Representative per-source σ_rms = 22 μJy
- 2025ApJ...990L..61C: Stacked 3σ flux-density limit 10.8 μJy
- 2021ApJ...917...99Y: mu_[C II] = 3.44, mu_cont = 4.53
- 2021ApJ...917...99Y: 4 elliptical annuli with width R_eff = 0.136''
- 2019ApJ...872...70T: Mean dust temperatures 25, 27, 36 K; beta=0.93; kappa(1.1mm)=0.014 cm2/g
- 2017ApJ...851L..23C: 100 walkers, 500 steps
- 2026ApJ..1003..219W: Use resolved Tex where available; 189 K elsewhere
- 2021MNRAS.507.1886F: Briggs weighting robust=0.5
- 2024ApJ...973..135H: f_lg = 0.99 (model A) and 0.90 (model B)
- 2024ApJ...973..135H: Grain size distribution slope p = 3.5 (MRN)
- 2020ApJ...904...37W: Free parameters: total disk mass, characteristic radius Rc, surface-density exponent gamma, scale height ratio hc at 100 au
- 2020ApJ...904...37W: Equal weighting of the two datasets; 100x1000 link chains minus 100 each for burn-in; grains 0.1-10000 um
- 2018PASJ...70...36I: Td=47 K and 35 K, beta=1.6, kappa0=0.4 cm2/g at 250 GHz
- 2025A&A...694A.171M: T_dust = 47 K, beta = 1.6
- 2025A&A...694A.171M: L_FIR = 0.75 L_TIR for the adopted model
- 2022MNRAS.514.2346K: r_31 = 0.55 and r_31 = 1.0
- 2019A&A...626A..11C: kappa=2.3 cm2/g at 230 GHz; T_dust=20 K; d=154 pc
- 2019A&A...626A..11C: Only stars with M*>=0.1 Msun included
- 2025A&A...698L..16S: Tdust = 30 K, the median along the cavity walls
- 2025A&A...698L..16S: κ1.3mm = 0.9 cm² g−1
- 2021A&A...653A.129C: 32 spectral windows of 1 GHz each
- 2021A&A...653A.129C: Continuum uncertainty +/-1.2 K, 11% of the continuum level at the reference frequency 84.579 GHz, added to the fit errors
- 2024A&A...681A..82G: Psi = 0.14; disk size 110 au; dust mass 0.039 Msun; i = 46.7 deg, PA = 133.3 deg
- 2024A&A...681A..82G: i = 20 deg, PA = 99 deg; dust mass 0.11 (+0.08/-0.04) Msun from the multi-wavelength analysis
- 2020ApJ...904L...6A: Gas: Sigma_c = 15 g cm^-2, R_c = 100 au, gamma = 1, no gas gaps
- 2020ApJ...904L...6A: Large grains: gamma = 0.2, R_c = 1000 au; outer disk component from 93 au to 160 au; inner disk edge 0.1 au extending to 20 au
- 2026A&A...706A.174A: Magnification fixed to give intrinsic properties
- 2026A&A...706A.174A: Gas-to-dust mass ratio fixed at about 100 after an initial free fit
- 2018ApJ...869..115S: σv = 0.75 km/s; σθ = 5-17°; length 3'' (420 au); FWHM 0.96'' (134 au); median flux density 3.4 mJy/beam
- 2016ApJ...832..110C: MRN size distribution, 0.005 um min, max 1 um and 1 mm; 80% silicates + 20% graphite
- 2024ApJ...968...10F: d = 419 pc
- 2024ApJ...968...10F: kappa = 0.23 cm^2/g at 106 GHz (OH5)
- 2024ApJ...968...10F: mu = 2.80 for number density
- 2024A&A...687A.299L: flaring index psi = 0, scale height h_c = 0.1 at the characteristic radius
- 2024A&A...687A.299L: gas density lowered by 1e-5 inside the 15 au gas cavity and by 1e-2 between 15 and 20 au
- 2024A&A...687A.299L: grain sizes 5 nm to 1 um (small) and to 1 mm (large), MRN index -3.5
- 2024A&A...681A.110W: MS dust mass for ΔMS < 0.4; SB dust mass for ΔMS > 0.7; log-space interpolation between
- 2024A&A...681A.110W: log(Mmol) = log(Mdust) + 9.4 − 0.85 × (12 + log(O/H))
- 2024A&A...681A.110W: Metallicity: a above log(Mstar/M⊙) ≥ b(z), otherwise a − 0.087[log(Mstar/M⊙) − b(z)]²; a = 8.74; b(z) = 10.4 + 4.46 log(1+z) − 1.78[log(1+z)]²
- 2022A&A...665L...7S: Redshift fixed at z = 3.7 for integrated SED fit
- 2016PASJ...68..103F: Td 50-70 K, beta=1.7, kappa0=0.005 cm/g at 231 GHz
- 2019ApJ...874...89C: flux integrated within 5 sigma contour and 50% primary beam response: 42±2 mJy
- 2016ApJ...831..101B: Gas-to-dust mass ratio 100; dust size distribution power law exponent 3.5; cosmic ray rate ~1e-19 s^-1; models sampled at 5 Myr (TW Hya) and 1 Myr (DM Tau)
- 2024A&A...684L..12S: Dust temperature 30 K
- 2024A&A...684L..12S: Gas-to-dust ratio 100
- 2024A&A...684L..12S: kappa(1.3 mm) = 0.9 cm2 g-1
- 2020ApJ...892..152H: nu = 233 GHz, d = 200 pc, kappa = 2 cm2/g, Td = 20 K or 300 K
- 2025ApJ...995L..75C: 5e5 gas SPH particles; sink radius 0.5 au
- 2025ApJ...995L..75C: Sigma proportional to R^-1; alpha_ss = 0.005
- 2025ApJ...995L..75C: pericenter 1500 au; initial separation 10 r_peri (3 r_peri in Run 2); node PA 15 deg, inclination 90 deg
- 2025ApJ...995L..75C: 180 deg rotation about the z-axis applied to match observed morphology
- 2021A&A...649A.122P: Distance 137.5 pc
- 2021A&A...649A.122P: Dust temperatures of 20 K (constant), 14.7 K (luminosity relation) and about 30 K (radiative transfer midplane at 20 au) tried for optical depth
- 2019ApJ...881...63N: kappa=2.64 m2/kg at 125 um; T_dust=47 K
- 2024MNRAS.533.2966Q: alpha_850 = (6.17 +- 1.7)e19 erg/s/Hz/Msun
- 2024MNRAS.533.2966Q: k0 = 0.07 m^2 kg^-1
- 2021ApJ...914...36I: 20 klambda uv bins; FIR range 42.5-122.5 um; TIR range 8-1000 um
- 2018A&A...615A.141B: r_c=8500 au, q=0.77, T_c=146 K, nu=217 GHz, S_nu=3.10 Jy, n=2
- 2019A&A...629A..75B: kappa_HCO+ = 0.2; cavity gas eta = 0.2; kappa_H13CO+ = 2 (<200 au), 6 (>200 au)
- 2024ApJ...967..133S: T_dust = 130 K (~50% uncertainty)
- 2024ApJ...967..133S: kappa350 = 1.9 cm^2/g; D/G = 1/100
- 2024ApJ...967..133S: Spectral indices alpha = 4.0 (dust), -0.15 (free-free)
- 2026MNRAS.548ag641R: 1000 bootstrap realizations
- 2026MNRAS.548ag641R: Disc radial extent 2.5 to 4.6 au, inclination 26 deg, PA 16 deg, dust mass 5e-5 M_sun, stars placed 0.5 au above/below disc plane
- 2020ApJ...901..166V: κ_1.3mm = 2.25 cm^2 g^-1; T_dust = 30 K
- 2018NatAs...2...56Z: beta=1.8 (1.5 alternative); nu0=c/100 um
- 2025ApJ...987...61R: Photometry from 70 μm to 3038 μm (Table 1); FIR integrated over 42.5–122.5 μm, TIR over 8–1000 μm
- 2014ApJ...792L..25V: m_dust 6.6e-4 to 4.5e-2 Msun; eps_CS 3.5e-9 to 3.5e-11; delta 1 to 100
- 2017A&A...597A..17H: Td = 15 K; kappa = 0.01715 cm2/g at 340.8 GHz; D = 400 pc
- 2025MNRAS.539.3808U: kappa = 0.19 cm^2/g at 230 GHz
- 2025MNRAS.539.3808U: Distance 2.8 kpc
- 2020A&A...636A..67A: Tex 50-300 K for HNCO and NH2CHO, 70-400 K for H2CO; FWHM and vLSR constrained by Gaussian fits, vLSR free within ±0.5 km/s
- 2024A&A...692A.155K: Dust temperature 20 K (also mean Tb of 27 K for RW Aur A within R90%)
- 2024A&A...692A.155K: Aperture radii 0.6 arcsec (A) and 0.45 arcsec (B)
- 2020MNRAS.491.1335R: 10^7 photons for thermal Monte Carlo and imaging
- 2020MNRAS.491.1335R: 10 log-spaced grain size bins, 0.1 um to 1 mm
- 2019MNRAS.485.2092C: <U>=22; L_IR/Md factor 125; 0.15 dex systematic
- 2024MNRAS.535.1533B: T_d = 35 K, beta_dust = 2.0 for resolved Band 7 MBB; beta_dust = 2.0 for Herschel MBB fit
- 2022A&A...657A..25N: 4 rings of width 300 pc from 0 to 1.2 kpc; integration wavelength range 8 to 1000 um; observer-frame frequency 230 GHz
- 2017ApJ...838..114K: kappa=0.23 cm2/g at 107 GHz; T=15 K; d=140 pc; gas-to-dust 100
- 2018ApJ...854..177V: gas-to-dust ratio 100 in outer disk; f_ls=0.85, chi=0.2 fixed; outer grid radius 400 AU
- 2024AJ....167...72D: 3sigma contour threshold for fitting
- 2020A&A...640A..19T: kappa_9mm = 0.28 cm2/g (DIANA); kappa_1.3mm = 2.3 cm2/g; for Orion comparison kappa_1.3mm = 0.9
- 2020A&A...640A..19T: 0.3 MJ planet solid fraction 27.8 Mearth set at 18% of CDF
- 2024MNRAS.532.1752R: Surface density power law r^-1/2 from r_wall to 80 au; flaring h(r) ~ r^1.125; gas-to-dust ratio 100
- 2024MNRAS.532.1752R: Grain size distribution dn(a) ~ a^-3.5 da from 0.03 um to 3 mm; DIANA composition; DHS scattering/absorption
- 2024MNRAS.532.1752R: h_wall tested: 0.1, 0.2, 0.3, 0.4, 0.5, 0.75, 1 au; CIDA 9 surface density multipliers 0.5, 1, 5, 10; settling alpha = 1e-4, 1e-5 or none
- 2020ApJ...902L..33G: PA = 1.0 deg (E of N), i = 36.4 deg, centre from Gaia DR2 corrected for proper motion
- 2020ApJ...902L..33G: Ring radial ranges 0.3''-0.4'' (inner) and 0.4''-0.6'' (outer)
- 2017ApJ...841L..25T: Td=32 K, beta=2.2, kappa850=0.4-1.5
- 2025A&A...696A..33P: T_dust = 32 K, beta = 1.8; C5 and C2 excluded from dust masses
- 2020MNRAS.498.4192F: Intrinsic UV luminosities 10^11 and 10^12 L⊙; cloud radii 2 and 4 kpc.
- 2016ApJ...823..160D: T_D = 10 K, d = 150 pc, kappa=0.23 cm2/g, mu=2.37
- 2016A&A...585A..58V: Sigma(r) power law with exponential cutoff, gamma=1
- 2024A&A...682A..78V: Fν=0.396±0.079 Jy in a 1.4'' diameter aperture; frequency 340 GHz.
- 2024A&A...682A..78V: R100K∼100 au; Rap=205 au; density powerlaw index 1.7.
- 2024A&A...685A..53G: NIR: 1.2–4.5 μm; MIR: 4.5–22 μm; FIR: 22–450 μm
- 2024A&A...685A..53G: 10% NIR/FIR excess threshold for disk-type quadrants
- 2024A&A...685A..53G: Exclude HN Tau from statistical analysis because optical photometry cannot be fit with one extinction value
- 2020ApJ...905...89Y: Dust ring width deconvolved with the 0.19 arcsec 1-sigma beam width
- 2017ApJ...844..123F: L850/Mgas = (6.7±1.7)e19 erg/s/Hz/Msun; Mgas/Mdust = 140
- 2025ApJ...993..111W: log(SFR [M⊙ yr−1])=log(LIR [erg/s])−43.41.
- 2021ApJ...907...62R: Gas mass ratio taken as the CO(9-8) line flux ratio
- 2017MNRAS.466..213A: beta = 0.55, 1, 1.5; lambda0 18-25 um
- 2018ApJ...869L..46D: kappa_abs = 2.0 cm^2/g at 0.125 cm for a=0.1 cm
- 2025ApJS..280...33Y: T_dust: starless 20 K lower limit to clump average (upper limit); warm 30 K; evolved 100 K
- 2025ApJS..280...33Y: kappa = 0.9 cm2/g
- 2023MNRAS.522...56V: Detection threshold = 5 sigma per time bin; non-detection upper limit = 3 sigma (local rms); systematic variability threshold VF = 2
- 2025ApJ...984L..12B: Star: 1 Msun, radius 2 Rsun, 4000 K; 1e9 photons
- 2025ApJ...984L..12B: Dust size distribution dn/da proportional to a^-3.5 from 0.03 micron to 1 mm; dust mass 1% of gas mass
- 2025ApJ...984L..12B: Physical scaling: planet at 100 au, solar-mass star, total gas mass 0.01 Msun, source at 140 pc
- 2021A&A...646A...3L: Full parameter set (R_c, Sigma_c, M_disk, gamma, h_c, psi, chi, f_ls, L, M_star, i, d) listed in Table 1
- 2021A&A...646A...3L: R_subl = 0.05 AU
- 2021A&A...646A...3L: Gas-to-dust mass ratio 100
- 2021A&A...646A...3L: Grain size distribution proportional to a^-3.5 (MRN)
- 2025ApJ...988...19S: T_d = 60 K, beta_IR = 2.03
- 2025ApJ...988...19S: kappa_88 = 34.15 cm^-2 g^-1; L_IR integrated over 8-1000 um
- 2021MNRAS.505.1509S: Grid ranges: 0 < z < 4.5 (step 0.1), 0 < A_V < 2.5 mag (step 0.25 mag), 10 < T < 50 K (step 1 K); 5 fitted parameters (z, A_V, T, S_Opt/IR, S_FIR) with Delta c…
- 2014ApJ...788L..34P: mm dust mass 5e-4 Msun, 0.1x hydrostatic scale height
- 2019A&A...628A...2B: I = 29 mJy/beam, kappa = 1.0 cm2/g, mu = 2.33
- 2016A&A...595A.113S: p_warp = 0.2; inner disk misalignment 22 deg; zone 1 dust mass 2e-9 Msun; zone 2 dust mass 2e-11 Msun, epsilon=3
- 2024A&A...682A...2C: 230 GHz (Band 6), 330 GHz (Band 7)
- 2020ApJ...904..185O: 3 sigma threshold = 0.9 mJy/beam; pixel size = 0''.025
- 2024ApJ...974..102S: zeta = 0.02, L* = 0.25 Lsun, T_d=[zeta L/(4 pi sigma r^2)]^(1/4)
- 2021A&A...653L...9V: T_dust = 20 K; evaluated for r_CO at 22 K and 30 K
- 2025A&A...704A.158C: Natural weighting and uvtaper tested in tclean; A_V constrained between 1.8 and 5 in BAGPIPES energy-balance fit for UDS_56824
- 2020ApJ...896...93H: beta_d = 1.5; kappa0 = 10 cm2/g at 250 um
- 2019ApJ...877L..25M: T80au = 360 K
- 2018MNRAS.477..325B: gamma=0.8; R_gas ~ 3 R_c; two grain populations 5 nm-10 um and 10 um-0.3 mm; q=3; large/small mass ratio 30; settling 0.2 h_gas
- 2018MNRAS.477..325B: R_in=0.04 au, i=45 deg, Av=3.8, Rv=3.1, Lx=1e28 erg/s
- 2025A&A...696A...7L: kappa(870 um) = 1.89 cm2/g
- 2025A&A...696A...7L: Dust temperature taken from Chen et al. 2024
- 2021ApJ...918...76C: T_d = (25, 40, 100) K; nu_0 = 340 GHz; kappa_0 = 1.3 cm^2 g^-1; beta = alpha_dust - 2 = 2
- 2021ApJ...918...76C: Dust-to-gas ratio = 1:100 (also tested 1:300)
- 2024MNRAS.534.3576K: Grid of ~2500 models varying psi, h_c, Delta_g/d, chi, f, plus dust ring locations and gap depletion
- 2023MNRAS.518.4481L: 100 walkers, 1500 burn-in steps, 500 production steps
- 2023MNRAS.518.4481L: Reference radius R0 = 100 au; fixed parameters from Table 1
- 2024A&A...690A..55S: Exclude sources within 10'' of prior; >3 sigma detections, otherwise 3 sigma upper limits
- 2023MNRAS.521.5508H: r_2,1 = 0.88+-0.07, r_3,1 = 0.69+-0.12, r_4,1 = 0.52+-0.14, r_5,1 = 0.37+-0.15
- 2016Natur.538..483T: T_dust = 30 K disk, 40 K for IRS3B-c; kappa 0.899 or 2.3 cm2/g
- 2017A&A...599A.113M: Inclination 10 deg for i<70 deg or unknown; 80 deg otherwise
- 2024ApJ...976...29H: Beam size = 0.42''
- 2023A&A...680A.110C: 5 sigma threshold across all 4 bands; nu_1 = 85.2 GHz, nu_2 = 99.2 GHz
- 2025A&A...697A..64V: 30° wedge on major axis; 4 settling levels alpha_z,MCFOST 2e-4 to 0.2
- 2020MNRAS.496.2362P: 1e8 Monte Carlo photon packets; i = 26 deg, PA = -36 deg, distance 163 pc
- 2020MNRAS.496.2362P: Dust grain sizes 0.01 micron to 1 mm with m=3.5, giving kappa = 15 cm2/g at 1 mm
- 2018MNRAS.476.4383D: emissivity index fixed to 2.0; L_FIR integrated 3-1100 um
- 2025A&A...700A.277C: Tdust = 47 K baseline
- 2020ApJ...892...66M: beta=1.8; kappa=0.0431 m^2/kg at 352.6 GHz
- 2016ApJ...827...72S: F/Omega = 0.34 Jy/beam in 0.5" aperture
- 2019A&A...625A.118K: outer radius 0.3-0.7 R_H; T_irr,star = 19 K at 22 au; kappa 3.5 cm2/g
- 2026A&A...713A.167D: ν = 220.6 GHz (1.36 mm)
- 2023ApJ...946L..41S: kappa_nu = 1.94 cm^2 g^-1 at 850 um; dust-to-gas ratio Z = 0.0016; T_d = 50-100 K; source diameter = 0.13 pc; SMC metallicity = 0.2 Z_sun
- 2024A&A...682A..55M: 3σ contour threshold for integrated continuum flux and moment map creation
- 2021ApJ...908....8C: Initial parameters from Zhang19; CO depletion imposed at start; 13CO and C18O from CO/13CO=69, CO/C18O=570
- 2025A&A...694A..82S: tau_main=500 Myr; q_PAH=0.47; THIMF slope xi=1.8 adopted
- 2020ApJ...901...79A: 0.1 dex added in quadrature to MAGPHYS uncertainties
- 2019MNRAS.485..739M: T = 20-40 K; amax = 1 mm; kappa = 1.15 cm2/g
- 2026A&A...706A.256A: OH5 κν = 0.0092, 0.0141, and 0.0172 cm² g−1 at 233.0, 303.0, and 328.2 GHz.
- 2021A&A...648A..41V: kappa = 0.1(nu/1e12 Hz)^beta cm2/g; beta=1.8±0.2 default
- 2025MNRAS.538.2358S: Dustpy: r = 1-300 au (300 log cells), R_c = 160 au, gamma = 1, r_p = 42, 69, 101 au, A_1 = 1, A_2 = 5, A_3 = 3, alpha = 10^-4 or 10^-3, v_frag = 1 or 10 m s^-1…
- 2023NatAs...7...49C: Network from Bosman18/UMIST RATE12, most grain-surface reactions disregarded
- 2023NatAs...7...49C: C/O = 1-2 with small dust depleted by a factor of 10
- 2024ApJ...970...30M: T_dust = 25 K, beta = 1.8, kappa = 0.9 cm^2/g at rest 600 um
- 2020A&A...641A.155V: includes sources with L_IR>=10^8.5 Lsun and Flag=0.5 upper limits; excludes AGN-dominated galaxies and QSOs
- 2018ApJ...865..131L: kappa_1.3mm=0.014 cm2/g (beta=1.3); T_dust=16 K (30 K alternative)
- 2017ApJ...845...10F: kappa=1.1 cm2/g at 1.3 mm, beta=0.4, T_dust=30 K
- 2026AJ....172...75M: Detected magnetic field region = 2.5'' x 1.95''; 3 sigma flux threshold for CH3OH transitions
- 2021ApJ...922..206S: kappa_1200um = 1.07 cm^2 g^-1, kappa_870um = 1.90 cm^2 g^-1, Z = 0.002, T_d = 60 K (SMM1) and 20 K (SMM2)
- 2025ApJ...988..106H: tau estimated only for R > 5 au; tau = 4 set where brightness temperature exceeds dust temperature in the inner disk
- 2025ApJ...988..106H: kappa_abs = 0.4, 1.9, 1.0 cm2/g for a_max = 0.1, 1, 10 mm, n(a) ~ a^-3.5
- 2022A&A...668A..25V: Disk zones: Inner (0.21-3 AU), Mid (10-44 AU), Outer (47-70 AU), Extended (70-400 AU); Wind foot (0.21-30 AU), Wind horns (10-100 AU); wind grain sizes 0.01-1 …
- 2022A&A...668A..25V: Wind-foot dust mass varied from 1e-9 to 5e-7 M_sun; radial extent of wind foot varied from 10 to 70 AU (fixed at 30 AU)
- 2024ApJ...969...27B: 35 galaxies; 28 inside the MIRI/F560W footprint; z = 0.45–3.71
- 2021MNRAS.508.5259M: Continuum method: alpha_CO = 6.5 M_sun/(K km s^-1 pc^2), T_dust = 25-35 K; CO line method: L'_{J=5-4}/L'_{J=1-0} = 0.3-0.7, alpha_CO = 0.5-1 M_sun/(K km s^-1 p…
- 2019ApJ...872..176Z: S=1.05 Jy (E), 0.020 Jy (W)
- 2018AJ....155...54W: disk outer radii 10-200 au; central 100 au, 40 or 20 au for low-mass
- 2026MNRAS.551g1645K: nu = 250 GHz
- 2021ApJ...910..148M: T_dust = 20 and 40 K
- 2021ApJ...910..148M: kappa_1.3mm = 0.9 cm2/g; d = 392 pc
- 2025ApJ...994..214T: kappa = 2.7 cm^2/g at 345 GHz; T_dust = 20 K or 25 K (L*/Lsun)^0.25
- 2020ApJ...895L..18B: disk mass 0.12 Msun, Sigma_c=3 g/cm2, rc=320 AU, gamma=1.0, (h/r)c=0.18, psi=0.1, gas-to-dust 100
- 2017ApJ...851..145M: T_d = 35 K, beta_IR = 1.5
- 2025A&A...699A.324H: SFMS comparison from (cite: 2014ApJS..214...15S)
- 2020MNRAS.498.4109J: Scoville estimator applied to the four points with lambda_rest>250 um (lambda_obs>1664 um); GDR = 100 x 10^(Z-Zsun)
- 2018ApJ...867...43T: D~300 pc, Tdust=30 K, kappa=0.899
- 2019AJ....158...15P: n(s)∝s^-3.5, 1 µm-1 mm; 1e8 photon packages; D_z=10 alpha
- 2024ApJ...966...32E: d = 150 pc; kappa = 2.3 cm2 g-1 at 225 GHz; T0 = 43 K; L_bol = 1.6 Lsun split 50% each giving T_dust = 40.7 K
- 2021ApJ...907..108G: kappa = 0.176 cm2/g at 94 GHz
- 2024A&A...688A.149D: kappa_nu = 2.3 cm2/g x (nu/230 GHz)^0.4
- 2020A&A...642A.164V: Mdust = 1e-3 Msun (HM), 5e-5 Msun (LM); h_1mm = 0.7 au at 100 au (settled), 10 au (non-settled); outer radius 140 au; d=140 pc
- 2020A&A...642A.164V: T=20 K, kappa=3.4 cm2/g
- 2024ApJ...964..146F: Td = 60 K fiducial (+-30 K); beta_d = 1.8; L_IR over 8-1000 um
- 2022MNRAS.510.3734D: 4 degrees of freedom for optically thin two-component SED; 3 degrees of freedom for optically thick single-component SED; integration range 8-1000 um
- 2018ApJ...862..102S: Td 12 K (P2), 13 K (P3), 10–20 K (P1)
- 2018A&A...617A..28S: Mdisk 0.066 Msun, Mdot 5e-9 Msun/yr, alpha 0.01, Rout 800 au, Lx 1e31 erg/s, grain 0.1 um
- 2025SciA...11.6953M: min-value = 3 sigma(1.3 mm), min-delta = 1 sigma(1.3 mm), min-npix = N_beam
- 2020MNRAS.496..394R: nu0=230.61 GHz, kappa0=0.8 cm2/g, beta=1.0, gas-to-dust 100, r0=690 AU, 15% flux uncertainty
- 2024A&A...689L...5M: R = 40 au
- 2020ApJ...892..111F: flaring angle 0.02; R_sub=0.07 sqrt(L*) au; kappa 10 cm2/g at 1000 GHz, beta=1; assumed R_inner=5 au for unresolved
- 2024A&A...692A..22Z: alpha_CO 0.8 (starburst) and 3.6 (star-forming), also tested as single values for all sources
- 2021A&A...652A.128J: emissivity beta = 1.5; T_CMB ~ 20 K
- 2019A&A...626A..71A: kappa 0.87mm = 0.0175 cm2/g; d = 139 pc
- 2018A&A...616A..88V: Rc=250 AU, gamma=0.6, Mdisk fixed 0.1 Msun, h_c, psi, f_ls, chi grid
- 2026A&A...709A.173M: T = 10-20 K (cores #2, #5, #6), T = 20-30 K (cores #3, #7, #8, #9), T = 39 +/- 5 K (core #4)
- 2026A&A...709A.173M: kappa_219 = 0.9 cm^2 g^-1, beta = 1.7, gas-to-dust ratio = 100, D = 8.5 kpc, sigma = FWHM / 2.35
- ... 204 more

### Assumptions (bibcode: value)
- 2019ApJ...871..185L: Constant 30 K fiducial, or radial profile; optically thin; gas-to-dust 100; flattened rotating
- 2019ApJ...871..185L: kappa=0.6 cm2/g, gas-to-dust 100
- 2018A&A...619A.161C: Optically thin emission; T_dust = 15 K; kappa with beta=1
- 2018A&A...619A.161C: rho_pc = 1 g/cm3, St near unity
- 2025A&A...694A.295P: Optically thin, isothermal dust emission; flux purely dust (not valid for free-free dominated B331, B268)
- 2025A&A...694A.295P: DIANA-standard setup, gas-to-dust 100, central object B331
- 2025A&A...694A.295P: Ossenkopf & Henning opacities, n_H=1e8 cm-3, no ice mantles; dust-to-gas limit 1e-2
- 2025A&A...694A.295P: Literature dust masses use Eq. for Mdust, sometimes with different dust temperature assumptions
- 2020ApJ...904..181L: Dust temperature 300 K; mostly optically thin continuum at 0.14 arcsec
- 2020ApJ...904..181L: κν = κ250 μm (250 μm/λ)^β; κ250 μm = 0.1 cm^2 g^-1; β = 1.8; κν = 0.010 cm^2 g^-1
- 2020ApJ...904..181L: Gas-to-dust mass ratio 100; distance 1.78 kpc
- 2020ApJ...904..181L: Flattened two-dimensional structure; empirical column-density and temperature profiles; gas-to-dust ratio 100
- 2020ApJ...904..181L: LTE; no interferometric spatial filtering of model cubes
- 2020ApJ...904..181L: Neglect gas self-gravity in the gas-kinematic model calculations
- 2025A&A...693A.286S: Optically thin emission
- 2025A&A...693A.286S: T_dust scaled with stellar luminosity following Andrews et al. 2013 (25 K x (L/Lsun)^(1/4) in the paper's equation)
- 2025A&A...693A.286S: Stellar luminosities from Valegard2021 used for the dust mass
- 2025A&A...693A.286S: Log-normal underlying distribution; five NOEMA Herbig disks added to the Herbig comparison sample
- 2025A&A...693A.286S: ISM gas-to-dust ratio of 100 used as reference; planet-formation section assumes gas-to-dust 100
- 2025A&A...693A.286S: Heavy-element mass of the planet equals the dust mass needed to form it (Thorngren2016 relation); gas-to-dust ratio of 100 when comparing with disk gas
- 2023MNRAS.518.6092L: Passive stellar heating (accretion heating ignored)
- 2023MNRAS.518.6092L: 85% of total dust mass in midplane, 15% in surface layer; surface layer a_max = 1 um, a_min = 0.01 um, size distribution slope p = 3.5
- 2023MNRAS.518.6092L: DSHARP homogeneous sphere dust composition (20% water ice, 32% astronomical silicates, 8% troilite, 40% refractory organics; rho_dust = 1.675 g cm^-3) with Bru…
- 2023MNRAS.518.6092L: Uniform gas-to-dust mass ratio of 30 (and tested < 10 in the ring)
- 2016ApJ...816...37V: Td=47 K, beta=1.6, tau<<1 at lambda>40 um; Kroupa IMF; emission powered by star formation
- 2016ApJ...816...37V: Thin inclined disk; gas-to-dust ratio ~100
- 2025ApJ...993L..40S: κν0 = 2.64 m²/kg at ν0 = 2.4 THz; β = 2.0
- 2025ApJ...993L..40S: Mass-weighted Tdust = 25 K
- 2025ApJ...993L..40S: Flat ΛCDM; Ωm = 0.3; H0 = 68 km/s/Mpc
- 2025ApJ...993L..40S: Dust traces molecular H₂ only; ignore neutral atomic gas.
- 2025ApJ...993L..40S: Ignore neutral atomic gas in the fiducial gas-to-dust ratio.
- 2021A&A...652A..66P: optically thin dust emission
- 2021A&A...652A..66P: T_CMB ~19 K at z=6; the CMB heating correction to T_dust(z) is ignored (<2%)
- 2021A&A...652A..66P: IR luminosity dominated by star formation; Kroupa IMF
- 2021A&A...652A..66P: LCDM with H0 = 69.3 km/s/Mpc, Omega_m = 0.287
- 2021A&A...652A..66P: 75% of the dust-derived gas mass is molecular
- 2021A&A...652A..66P: T_ex = 30 K (50 K gives ~40% lower M_CI); LTE, optically thin, 2-level approximation
- 2015A&A...583A..66H: optically thin continuum at mm wavelengths
- 2015A&A...583A..66H: ISM gas-to-dust ratio 100 as reference
- 2014ApJ...796....1T: Gas-to-dust mass ratio of 100, dust opacity from Hildebrand 1983 with beta=0.5
- 2017ApJ...835..213P: gas-to-dust ratio 100 by mass
- 2017ApJ...835..213P: gas-to-dust 100; 80% of L_IR in starburst following sub-mm distribution
- 2018A&A...614A.113H: gas-to-dust mass ratio 100
- 2018A&A...614A.113H: 1 Msun central star
- 2014ApJ...796...84R: Chabrier IMF for SFR from L_FIR; LBG-2/3 share LBG-1 redshift and SED shape
- 2024MNRAS.527.3559P: Pure astronomical silicate, bulk density 3.3 g/cm3, porosity via Bruggeman EMT (Mie) or vacuum voids of 1/100 grain diameter (DDA)
- 2024MNRAS.527.3559P: Proper eccentricity of colliding planetesimals 0.1
- 2024MNRAS.527.3559P: Only the outer Kuiper-belt analogue modelled; inner warm belt not modelled with MODERATO
- 2024MNRAS.527.3559P: beta itself is unchanged by gas; only the grain orbits are
- 2018ApJ...869...10M: kappa = 1.7 g cm^-2
- 2018ApJ...869...10M: Optically thin dust
- 2018ApJ...869...10M: Dust mass fixed from ALMA flux; Ldust/L* = 2.6e-4
- 2018MNRAS.479.1154B: T_d=47 K, beta=1.6, alpha_ff=-0.1, optically thin Rayleigh-Jeans dust, kappa0=0.045 m^2/kg at 250 GHz
- 2018MNRAS.479.1154B: alpha_CO=0.8 Msun (K km/s pc^2)^-1; r31=1.0 where undetermined
- 2021A&A...645A..49G: Gas-to-dust mass ratio 100
- 2021A&A...655A..98A: Optically thin dust, so radiative transfer effects are negligible
- 2021A&A...655A..98A: LMC distance 49.97 kpc for all sources
- 2021A&A...655A..98A: Systematic kappa uncertainty of about 25% not propagated
- 2021A&A...655A..98A: Photosphere black body of fixed 3000 K; grey body with beta = 0; extinction with R_V = 3.1; optically thin dust (lower limit on mass)
- 2024MNRAS.535..729P: Schlafly & Finkbeiner (2011) dust reddening maps and Fitzpatrick et al. (2019) MW extinction curve; excluding SPIRE 500 um causes < 30% error in M_dust; region…
- 2024MNRAS.535..729P: Chabrier (2003) IMF, Bruzual & Charlot (2003) SPS, 0.2 < Z/Z_sun < 2, Charlot & Fall (2000) two-component dust attenuation, energy balance
- 2024A&A...681A..17D: Distance d = 6600 pc; gas kinetic temperature power law with epsilon = 0.6; silicate dust condensing at ~1750 K (R_dust = 3-4 R_star); gas-to-dust ratio r_gd =…
- 2021A&A...654A..90L: Kennicutt (1998) SFR calibration converted to Chabrier (2003) IMF by subtracting 0.23 dex; optically thin dust with beta = 1.8 for MBB test; no radio variabili…
- 2020MNRAS.498.1319M: Disc size >~0.1 au (a smaller, optically thick disc could hide more mass)
- 2020MNRAS.498.1319M: Accreted dust: 1 um radius grains, 3 g/cm3, accreted for 700 Myr
- 2020MNRAS.498.1319M: Dust mass counts only grains smaller than 1 cm, set by assumed opacities
- 2020MNRAS.498.1319M: Star modelled with Teff = 6500 K and R = 1.3 Rsun template spectrum
- 2024ApJ...977..190X: κν = κ0 (ν/ν0)^β; κ0 = 0.77 cm² g−1 at 353 GHz.
- 2024ApJ...977..190X: Include CMB dust heating.
- 2024ApJ...977..190X: ΛCDM: H0 = 70 km s−1 Mpc−1, Ωm = 0.3, ΩΛ = 0.7.
- 2024ApJ...977..190X: Kroupa IMF; SFR_IR/(M⊙ yr−1) = 3.88 × 10−44 L_TIR/(erg s−1).
- 2024ApJ...977..190X: J0129-0035 SFR is an upper limit because AGN contribution is unknown.
- 2015ApJ...800...70S: Optically thin dust, empirical dust-opacity/gas-to-dust absorbed in alpha_850um, uniform spherical/disk distribution for column density
- 2018MNRAS.475..448T: kappa=0.1 cm2/g (nu/THz)^beta, includes gas-to-dust 100
- 2020ApJ...891..164S: Dust-to-gas mass ratio 0.0027 (0.008 scaled by LMC Z~1/3); NH2/AV = 2.8e21; distance = LMC
- 2020ApJ...891..164S: LMC: Z=1/3, gas-to-dust 300, chi_uv=3
- 2026ApJ...998..277M: Optically thin dust continuum emission and thermal coupling between gas and dust (T_d = 10-20 K)
- 2026ApJ...998..277M: Spherical gas distribution with 0.1 pc diameter
- 2019MNRAS.483..806R: gas-to-dust 100; mu=2.8; kappa0 extrapolated from 0.009 cm2/g at 1 mm
- 2019A&A...626A.126A: kappa_850 = 1.7 cm^2/g, distance 49.97 kpc
- 2013ApJ...777...92S: power-law dust emissivity; ATCA non-detections rule out free-free
- 2021NatAs...5..586Y: Spherical grains; mass mixing ratio m_carb/m_sil = 0.5; compact dust density rho_CD = 2650 kg m^-3 (or porous P = 0.80 with rho_CD = 530 kg m^-3); dust velocit…
- 2021NatAs...5..586Y: rho_d = 2650 kg m^-3, v_d = 3 m s^-1, mean dust size <a> = 1 mm, geometrical albedo p_V = 0.04
- 2025A&A...694A..86Y: Gas-to-dust mass ratio 100
- 2025A&A...694A..86Y: T_dust = 20 K
- 2025A&A...694A..86Y: Dust opacity 0.817 cm2/g (beta = 1.5)
- 2025A&A...694A..86Y: mu_H2 = 2.8
- 2015MNRAS.449..715W: distance 8.4 kpc
- 2015MNRAS.449..715W: gas-to-dust ratio 100
- 2020ApJ...894L..14L: Optically thin dust, constant 20 K, gas-to-dust 100
- 2013ApJ...762L..21M: d = 9.91 pc; central peak is star plus dust
- 2019MNRAS.488.1005P: Disc inclination 30 deg from face on (beta Pic b 85 deg)
- 2019MNRAS.488.1005P: Star and planet luminosities heat dust; anisotropic scattering included
- 2019MNRAS.488.1005P: gas-to-dust 100; grain density 1 g/cm3
- 2021A&A...650A.153D: Exclude EMU compact flux because extended radio emission may contaminate it
- 2021A&A...650A.153D: Dust opacity power law; β=1.5
- 2021A&A...650A.153D: ν0=c/350 μm; κ0=0.192 m² kg−1
- 2025ApJ...986L..22R: Opacities 0.17-0.467 m2/kg; dust at equilibrium temperature
- 2026MNRAS.548ag325W: Dust has uniform temperature and negligible optical depth; ballistic expansion; r^-2 density profile
- 2020MNRAS.492.4847L: T=20 K; κ=10(ν/1000)^β GHz cm² g^-1; β=1
- 2020MNRAS.492.4847L: Gas-to-dust ratio 100:1; distance scaling d/3 kpc
- 2021A&A...650A..37D: typically adopted dust opacity, gas-to-dust mass ratio of 100, optically thin emission at 90 GHz
- 2024ApJ...963....1O: dust temperature 25 K
- 2020PASP..132i4501H: Optically thin dust with grain alignment by radiative torques, so inferred field orientation is frequency independent
- 2016ApJ...832..148V: Galactic V-band extinction curve, N_H = 2.05e21 tau_V
- 2014MNRAS.444.1821F: Optically thin, circular face-on thin ring
- 2014ApJ...785...44M: gas to dust ratio 100; R_e=2 kpc encloses half the mass; v_c=400 km/s
- 2019A&A...623A..77S: Gas-to-dust 100, dust opacity 1.0 cm2/g at 1.3 mm, dust and gas temperature equal, LTE
- 2019A&A...623A..77S: gas-to-dust 100, kappa 1.0 cm2/g at 1.3 mm (Ossenkopf1994), distance 4.6 kpc
- 2016ApJ...831..125P: Tdust = 20 K or 25 K (L/Lsun)^0.25; no 10 K floor
- 2024A&A...682A..61C: Optically thin dust and Rayleigh-Jeans: beta = alpha - 2
- 2024A&A...682A..61C: DSHARP opacity for ISM-like spectral index with n(a) proportional to a^-3.5
- 2024A&A...682A..61C: Quoted mass uncertainties reflect only a 10% flux calibration error; inner-region mass may be off by up to ~5 because it is optically thick
- 2024A&A...682A..61C: Whole streamer falls onto the inner system; rate is an upper estimate
- 2020ApJ...904...78S: Dust temperature 30 K for typical low-luminosity protostar, scaled by (L/Lsun)^0.25 to ~50 K for L_bol = 7.8 Lsun
- 2020ApJ...904...78S: Distance ~400 pc
- 2020ApJ...904...78S: Opacity kappa(1.3 mm) = 0.899 cm2/g (Ossenkopf & Henning thin ice mantles), scaled as (1.3 mm / lambda)^beta
- 2020ApJ...904...78S: Models constrain dust mass only; total mass quoted with gas-to-dust ratio of 100
- 2020ApJ...904...78S: Protostar mass used only to set the envelope density structure, not fit
- 2025ApJ...995...98D: Fixed gas-to-dust spatial coupling and constant dust-to-gas mass ratio
- 2025ApJ...995...98D: Long-wavelength emission likely optically thin
- 2025ApJ...995...98D: Fragmented mass redistributed to smaller grains at the same radius; grains above the drift threshold moved inside r_drift
- 2025ApJ...995...98D: Initial constant epsilon; dust boundary assumed shaped by radial drift
- 2021A&A...648A..33M: Toomre comparison: gas-to-dust ratios 100 and 10; stellar mass 0.6 M_sun; fitted expected temperature.
- 2021A&A...648A..33M: Gas mass ~0.05 M_sun from Herschel HD literature measurements.
- 2021A&A...648A..33M: Survey comparison assumes optically thin emission, kappa=10 cm^2 g^-1 at 1000 GHz, beta=1, T=20 K.
- 2017MNRAS.465.4390B: kappa0=0.045 m2/kg at 250 GHz
- 2017MNRAS.465.4390B: alpha_CO=0.8; gas-to-dust ratio 91
- 2025A&A...695L..15F: Gas-to-dust ratio 200 (hot DOG metallicity ~0.5 Zsun); kappa_850um = 0.0968 kg^-1 m^2 at 352.7 GHz
- 2025A&A...695L..15F: Flat LCDM, H0 = 70 km/s/Mpc, Omega_M = 0.3; lower T limit set by T_CMB at z=4.601
- 2025A&A...695L..15F: Same gas-to-dust ratio (200), kappa_850um and cosmology as step 3
- 2025A&A...695L..15F: SFR from L_IR following Kennicutt & Evans 2012; M_gas = M_d x gas-to-dust ratio 200
- 2023MNRAS.521.2962F: Radiative equilibrium in a clumpy sphere ISM with high density contrast (negligible interclump opacity)
- 2023MNRAS.521.2962F: Optically thin modified blackbody dust emission with fixed emissivity index beta = 2
- 2023MNRAS.521.2962F: Mass absorption coefficient kappa_UV = 5.0e4 cm^2/g and dust emissivity kappa_0 = 30 cm^2/g at 100 um
- 2023MNRAS.521.2962F: Cosmology (Omega_m, Omega_Lambda, h) = (0.3, 0.7, 0.7) and gravitational lensing magnification factors mu = 9.3 (A1689-zD1) and mu = 1.43 (MACS0416-Y1)
- 2023MNRAS.521.2962F: Constant ISM clumpiness log(xi_clp) = -1.02 +/- 0.41 across high-z star-forming galaxies
- 2014ApJ...791L...6W: kappa=10 cm2/g at 300 GHz, Tdust=60 K; 80 K and 40 K for inner/outer rings
- 2014ApJ...791L...6W: gas-to-dust 100; model extrapolated to 400 AU by power law
- 2014ApJ...797...27F: T_d = gas temperature; SM1N 16 K from NH3; SM1 >=30 K; d = 120 pc
- 2016ApJ...828...50K: kappa = 4.5 m2/kg; beta 1.71; T=33 K; distance 10 Mpc
- 2016ApJ...828...50K: virial equilibrium; delta_GDR=650; Delta A_V=0.7
- 2019A&A...623A.153O: Dust opacity 0.5 cm2/g, Td = 50 K for simple estimate; gas-to-dust 200 canonical
- 2014MNRAS.438.1267S: kappa_870 = 0.15 m^2 kg^-1
- 2014MNRAS.438.1267S: gas-to-dust ratio 90 ± 25; burst duration 250 Myr
- 2026A&A...705A.203W: Locally isothermal gas; T∼r−0.5; α-viscosity
- 2026A&A...705A.203W: Fiducial T0=38 K, h=0.07, μ=2.3
- 2026A&A...705A.203W: Vary gas mass while keeping other quantities, including dust mass, fixed
- 2017ApJ...842....8M: kappa = 2.3 cm^2/g at 1.3 mm; T ~48 K radiative equilibrium; D = 7.66 pc
- 2017ApJ...842....8M: Fomalhaut b at ~125 AU, T_dust ~51 K; stellar photospheric radius 1.842 Rsun
- 2019ApJ...880..157D: Optically thin [CII], LTE, C/H=2.95e-4, gas-to-dust 100 for comparison, Tdust=35 K adopted
- 2022A&A...659A..46B: Milky Way extinction curve; Q_ext = 2, rho_dust = 3 g cm^-3, a = 0.1 um; Bruzual & Charlot (2003) models, Chabrier (2003) IMF, Draine & Li (2007) dust models; …
- 2022A&A...665A..82O: Spherical symmetry; r^-2 density distribution (constant mass-loss rate and expansion velocity); astronomical silicate grains (cite: osseetal92); dust expansion…
- 2022A&A...665A..82O: Constant isotropic expansion and mass-loss rate; kinetic and dust temperature profiles from IK Tau (cite: ramsolof14); initial 12CO/H2 abundance f_i = 4e-4; ph…
- 2024ApJ...962..196O: Chabrier IMF, solar metallicity, delayed star formation history and dust extinction
- 2024ApJ...962..196O: Draine dust emission models; grain-density factor 0.81
- 2024ApJ...962..196O: Dust mass percentage 1%; most inner-disk gas molecular for warm-H2 percentages
- 2026A&A...711A.159M: Spherical dusty envelope; dust present only beyond condensation radius r_c with uniform gas-to-dust ratio; 20% uniform flux uncertainties
- 2021ApJ...908..235I: T_d = 35 K (local star-forming galaxies) would make luminosities ~2x smaller
- 2021ApJ...908..235I: SFR_TIR is an upper limit since all FIR emission is assumed to come from star formation (AGN contribution ignored)
- 2021ApJ...908..235I: kappa_nu = 0.4 (nu/250 GHz)^beta cm^2 g^-1
- 2023A&A...674A..66Z: Optically-thin, gas-depleted disks; grain size distribution from 0.1 to 100 um with power-law -3.5, porosity 0.25, carbonaceous mass/volume fraction 0.13/0.15
- 2023A&A...674A..66Z: Constant dust temperature of 20 K across all objects; stellar mass-luminosity relation M_* = L_*^0.25 for M_* > 0.43 M_sun and M_* = (L_*/0.23)^(1/2.3) for < 0…
- 2024ApJ...964...95S: κνrest = κ0(ν/ν0)^β.
- 2024ApJ...964...95S: For three objects without stellar masses, adopt Mstar = 10^10.3 M⊙ to obtain upper limits on fgas.
- 2014A&A...561A..49H: Galactic A_V=0.155 mag with Cardelli et al. curve; metallicity prior Gaussian around 0.0347 Zsun
- 2019ApJ...881L..42C: d=2.9 kpc, Tdust=15 K, gas-to-dust 100
- 2023Ap&SS.368...33M: Optically thin dust emission, dust temperature T_d = 150 K, mean atomic mass per hydrogen mu_H = 1.41, dust-to-gas mass ratio Z = 0.01
- 2023Ap&SS.368...33M: Dust opacity law kappa_nu = 0.90*(nu/230 GHz)^beta cm^2 g^-1 with beta ~ 1.7 (giving kappa_nu = 0.814, 0.823, 0.835, 0.838 cm^2 g^-1), and Rayleigh-Jeans appro…
- 2026ApJ..1004L...6D: Optically thin thermal dust emission
- 2026ApJ..1004L...6D: Gas-to-dust mass ratio Rgd = 100; mean molecular weight μ = 2.8
- 2026ApJ..1004L...6D: Tdust = 150 K following (cite: 2020NatAs...4.1170C); dust opacity from (cite: Bon19)
- 2019A&A...628A..27B: gas-to-dust ratio 100; Ossenkopf & Henning opacity without ice mantles, n=1e6
- 2018MNRAS.481.4931E: CO/H2 ~1e-3 (carbon-rich); oxygen-rich case gives 3.9e-2 Msun
- 2015A&A...573L...1O: a_g = 0.2 micron, rho_g = 3.5 g cm^-3, Q = 5.65e-4 (nu/274.6 GHz)^0.7, Tstar = 3490 K
- 2015A&A...573L...1O: Vd ~60 km/s, T = 200 K
- 2023PSJ.....4..206R: Weighted average treated as a lower limit on ejecta dust mass; crystalline favored
- 2024ApJ...968L..11G: Ossenkopf (1994) dust opacity, T=20 K, gas-to-dust mass ratio 100, D = 8 kpc
- 2014ApJ...795L..25R: gas to dust mass ratio of 100
- 2020ApJS..251...14H: gas-to-dust 100; mu_H2 = 2.8; beta = 1.75
- 2014Sci...343.1490D: opacity 0.15 m2/kg at 850 µm; T=85 K
- 2017A&A...606A.121L: kappa = 1.3 (1.2 mm) and 0.30 cm2/g (2.7 mm), dust-to-gas 0.01, mu=2.33, d=235 pc
- 2017A&A...606A.121L: Optically thin dust, LTE
- 2016ApJ...828...46A: T_dust=20 K, median for Taurus disks; not scaled with L*
- 2016ApJ...828...46A: T_dust=20 K; distances 145 pc (Upper Sco), 140 pc (Taurus); M*>0.1 Msun
- 2024A&A...687A.217D: Dust emission optically thin at all wavelengths
- 2024A&A...687A.217D: Gas-to-dust mass ratio of 100 (kappa_300 defined w.r.t. total mass)
- 2024A&A...687A.217D: X_H = 0.7, X_H2 = 1, Z_D = 0.01 for the H2 column density
- 2024A&A...687A.217D: Measurement noise is Gaussian
- 2022A&A...662A...8M: Optically thin thermal dust emission; κ_870μm = 0.0185 cm^2 g^-1; gas-to-dust ratio = 100; T_dust = 20 K (IR-quiet / Young), 25 K (Intermediate), 30 K (IR-brig…
- 2022A&A...662A...8M: Spectral index α = 3.5 corresponding to optically thin dust emission with emissivity index β = 1.5
- 2022A&A...662A...8M: Optically thin thermal dust emission; κ_1.3mm = 0.01 cm^2 g^-1; gas-to-dust ratio = 100; T_dust = 20 K for most cores and T_dust = 75 K for the 10 brightest co…
- 2026A&A...706A.214V: dust temperature 20 K and optically thin emission
- 2026A&A...706A.214V: gas-to-dust ratio 100; small (0.005-1 um) and large (0.005-1000 um) grain populations
- 2026A&A...706A.214V: 30 K is a reasonable single temperature because the dust mass is dominated by the temperature at the outer radius
- 2022A&A...661A..53V: Optically thin 225 GHz dust continuum emission
- 2022A&A...661A..53V: Effective dust temperature T_dust,eff = 20 K
- 2022A&A...661A..53V: Dust opacity kappa_230GHz = 2.3 cm^2 g^-1 with power-law index beta = 1
- 2022A&A...661A..53V: Gas-to-dust ratio of 100 and 1 Myr evolution timescale from Class I to Class II for mass loss rate estimate
- 2019ApJ...874...27T: T_dust = 50 K (40 K), beta = 1.5, kappa_d(850um) = 0.15 m^2/kg, nu0 = 353 GHz, mu_g = 1.43
- 2019ApJ...874...27T: Chabrier IMF; no parameter optimisation except baryon mass scaling
- 2024ApJ...965..108U: SFR averaged over the last 10 Myr; dust luminosity/mass exclude AGN-torus dust
- 2024ApJ...965..108U: Flat universe; H0=70.4 km s−1 Mpc−1; ΩM=0.272; errors 1σ unless specified
- 2024ApJ...965..108U: Characteristic temperature uses the dust-SED peak in Jy and is not intrinsic dust temperature
- 2020MNRAS.499.5241C: Chabrier IMF
- 2020MNRAS.499.5241C: template-based dust temperature uncertainty of about 5 K
- 2020MNRAS.499.5241C: gas-phase oxygen abundance as proxy for metallicity
- 2014ApJ...791...20R: Distance 140 pc; gas-to-dust ratio 100; kappa 0.02 cm2/g_gas at 0.89 mm
- 2015ApJ...814...22E: Constant infall rate, wind mass loss neglected
- 2017MNRAS.468L..87C: kappa160 = 1.6 m2/kg, beta = 1.7
- 2017A&A...601A...5H: Gas-to-dust 100; stellar blackbody 3500 K, 2500 Lsun; 12CO/H2 = 1e-4
- 2015ApJ...806..260F: Td = 45 ± 5 K; Milky Way-like dust opacities
- 2026MNRAS.545f2150S: Blackbody dust grains; optically thin thermal emission; distance D = 191 pc; stellar luminosity L = 60.0 L_odot; dust opacity kappa = 0.1 * 2.3 * (nu / 230e9)^…
- 2026MNRAS.545f2150S: Optically thin dust; single-temperature blackbody belt
- 2019ApJ...875...87D: opacity 2.3 cm^2/g; dust in blackbody equilibrium; L*=0.09 Lsun; d=9.725 pc; vertically isothermal
- 2018Sci...362.1034D: beta=1.8, kappa(850µm)=0.0484 m2/kg, gas-to-dust 100, alpha_CO,MW=4.6 and ULIRG=0.8
- 2022ApJ...928..150T: Galaxy SED does not change much across the galaxy when using red filter as stellar template
- 2020MNRAS.491.1174M: Constant optically thin dust formation for the linear extrapolation
- 2026A&A...707A..77H: Dust-to-gas mass ratio approximately constant across the outflow
- 2026A&A...707A..77H: Diffuse dust extinction is primarily due to dust mixed with the outflowing cold molecular gas
- 2026A&A...707A..77H: Redshifted outflow carries the same dust fraction as the blueshifted side when extrapolating to total dust mass
- 2024A&A...686A.274V: Spherically symmetric envelope expanding at constant velocity; amorphous carbon opacities (CW Leo), silicate (R Leo); gas-to-dust 300 (CW Leo), 167 (R Leo)
- 2021MNRAS.500.3667S: Salpeter IMF with Kennicutt (1998) conversion SFR = L_IR / (5.8e9 L_sun); dust mass opacity kappa_850 = 0.077 m^2 kg^-1; flat LambdaCDM (H0 = 67.8 km/s/Mpc, Om…
- 2021MNRAS.502.5390P: Compact spherical grains of pure astronomical silicate (Draine 2003) with bulk density 3.3 g/cm^3; Mie theory; sublimation temperature of 1300 K; warm and cold…
- 2025Natur.641.1137B: CO excitation ratios r_31 = 0.8, r_71 = 0.2; CO-to-H2 conversion factor alpha = 0.8 M_sun (K km s^-1 pc^2)^-1; gray body dust spectrum with beta = 0.7 and T = …
- 2015ApJ...799...11X: Same cold dust temperature (35 K) in central region; M_gas/M_dust = 10^2.0±0.2
- 2017ApJ...850L..30Y: Td = 50 K; kappa = 0.068 cm2/g
- 2023MNRAS.525.2229M: Dust-to-gas mass ratio Z = 0.01 and mu_H = 1.41
- 2023MNRAS.525.2229M: All continuum sources optically thin at 303.39 GHz
- 2026ApJ...999..194I: Optically thin dust emission at 870 um, dust coated by thin ice mantles, T_d = 150 K, and Z = 0.0024
- 2017MNRAS.469.2230M: Optically thin dust, kappa 0.009 cm2/g, gas-to-dust 100, Tdust=Tex=110 K
- 2016MNRAS.459.4518H: optically thin dust, distance 512±43 pc
- 2015A&A...576L..15O: D = 0.7 kpc, kappa230 = 0.5 cm2/g, Td = 45 K, dust-to-gas 200
- 2015A&A...576L..15O: f_C18O = 4e-7, f_CO = 2e-4, Trot = 30 K
- 2017ApJ...849...25L: gas-to-dust 100, kappa0=0.01 cm2/g at 230 GHz (Ossenkopf & Henning 1994), mu=2.37
- 2019A&A...628A..85V: Optically thin dust emission
- 2019A&A...628A..85V: Fiducial disk 20 Earth masses, 40 AU, gas-to-dust 100, 0.5 Myr exposure
- 2024ApJ...976..241Y: 3-mm emission optically thin and thermal dust
- 2024ApJ...976..241Y: Uniform density distribution for the filament
- 2024ApJ...976..241Y: Masses may be underestimated (25 K too high for non-YSO condensations; flux filtering) or overestimated for protostellar condensations (up to 50 K)
- 2023MNRAS.525.6146W: gas-to-dust mass ratio 100
- 2023MNRAS.525.6146W: dust temperature equals gas temperature
- 2023MNRAS.525.6146W: spherical geometry, mu_H2 = 2.8, radius = half the geometric mean of source sizes; D = 4 kpc
- 2023MNRAS.525.6146W: flat density profile (n = 0), T_dust equal to gas temperature, DCN mu = 28
- 2025A&A...693A..49S: Optically thin emission, likely the largest source of uncertainty
- 2025A&A...693A..49S: G0 unit of 1.6e-3 erg cm-2 s-1 (Habing)
- 2021A&A...647A.118L: Gas-to-dust ratio 100
- 2021A&A...647A.118L: Small grains 0.005–1 μm at gas scale height; large grains 1–1000 μm at χh, χ=0.2; f_large=0.99
- 2021A&A...647A.118L: External UV G_0≈2.7×10^-3 erg s^-1 cm^-2 between 6 and 13.6 eV; cosmic-ray ionization 5×10^-17 s^-1 per H2
- 2021A&A...647A.118L: X-rays: thermal radiation at 7×10^7 K, 1–100 keV, luminosity 10^30 erg s^-1; same prescription for T Tauri and Herbig models
- 2017ApJ...850....1R: kappa=2.64 m2/kg at 125 um; Chabrier IMF
- 2017ApJ...850....1R: alpha_CO = 0.8 Msun (K km/s pc2)^-1; r51=0.39
- 2026ApJ..1000..159M: Dust is in radiative thermal equilibrium, optically thin, with clumpy geometry, and has the same spatial extent as the UV stellar continuum (r_e,dust = r_e,UV)
- 2026ApJ..1000..159M: Exponentially rising SFH parameterization and Larson IMF
- 2021A&A...655A..42S: optically thin dust, lambda_rest > 250 um; flat LCDM with h=0.7, Om=0.3, OL=0.7
- 2021A&A...655A..42S: stellar metallicity from MegaSaura used as proxy for gas-phase metallicity; SGASJ1226-B assigned the metallicity of SGASJ1226-A
- 2021A&A...655A..42S: Tex = 30 K for [CI]
- 2014ApJ...791...42Z: Gas-to-dust 100, CO/H2 5e-5, Keplerian rotation M*=1 Msun, i=6 deg, T_CO power law, CO outer edge at 17 K
- 2013ApJ...774...39A: Td=30 K, gas-to-dust 100, kappa(3mm)=0.9 cm2/g, beta=1
- 2016PASJ...68...20S: 352 GHz dominated by cold dust; synchrotron and free-free neglected
- 2019A&A...629A.146V: Spherical envelope, constant expansion velocity, collisions with H2 only
- 2015MNRAS.452.2258D: gas to dust ratio 150
- 2026A&A...705A.197Z: Isotropic excitation; i_rms=e_rms/2; i_rms approximately sqrt(2) h_HWHM.
- 2026A&A...705A.197Z: Steady state; internal stirring, dynamical friction and efficient collisional damping; mass conserved in catastrophic collisions.
- 2026A&A...705A.197Z: Negligible dust mass relative to large bodies; gas omitted.
- 2019MNRAS.486.5552B: astro-silicates from Draine2003
- 2017ApJ...836....8T: Inclined rotating disk, v_circ = 0.75 FWHM/sin i; Td=47 K, beta=1.6; gas-to-dust 100
- 2023ApJ...953..113L: Single-temperature modified blackbody with dust mass absorption coefficient k_lambda0 = 0.29 m^2 kg^-1 at lambda_0 = 250 um
- 2020MNRAS.491..758A: Free-free emission negligible; dust emission optically thin (gamma = 1)
- 2024ApJ...971..176H: Dense GMCs expected to have GDR of 50-100 rather than 200; subregion A1a assumed to have the galaxy-integrated dust temperature
- 2024A&A...691L..14O: Optically thin dust so that polarized intensity traces dust distribution
- 2024A&A...691L..14O: Gas and grains kinematically coupled when inferring dust infall from H2O kinematics
- 2020ApJ...903...34A: T_dust = 47 K, beta = 1.6 fixed; low dust optical depth in Rayleigh-Jeans regime; dust mass has at least a factor of two systematic uncertainty from the opacit…
- 2021AJ....162..235Y: Dust opacity 2.3 cm^2 g^-1 (acknowledged to dominate the uncertainty)
- 2021AJ....162..235Y: Dust temperature 100 K (warm inner belt) or 40 K (cold outer belt)
- 2024ApJ...977L..46B: Mm continuum treated as cold dust to compute IR luminosity, dust mass and SFR_IR
- 2014ApJ...787...48X: R_pc=100 and 70% of L_IR inside radius
- 2016PASJ...68L...7T: Td=20 K, beta=2, Z/Z0=1, mu=2.3, d=8.5 kpc
- 2020A&A...644A..84M: Td = 150 K, beta = 2.0, k0 = 0.8 cm2/g at 220 GHz, mu = 2.33, gas-to-dust 100
- 2024ApJ...968L..19F: Td = Tgas = 6 K; kappa 1.21 cm2/g at 1.16 mm; dust-to-gas 0.008
- 2019ApJ...871..251P: grain radius 0.1 um, grain density 3 g/cm3, gas-to-dust 100, Q=2e-5 at 230 GHz, Td = rotation temperature
- 2018ApJ...869...59W: kappa=0.899 cm2/g, Tdust=15 K, d=140 pc
- 2018ApJ...869...59W: Envelope T=15 K, C18O abundance 4.8e-7, LTE optically thin
- 2016ApJ...827..142B: κ=2.3 cm2/g at 230 GHz, ∝ν^0.4; T_d=25 K (L*/Lsun)^0.25; d=145±20 pc
- 2016ApJ...827..142B: T_CO ≥20 K, inclination 60°, gas-to-dust 100, CO/H2 = 7e-5, disk radius 43.5 au
- 2024A&A...686A.122A: Optical-depth correction applied a posteriori raised the maximum field temperature from 39 K to 44 K; for the cores the correction was not applied before the s…
- 2024A&A...686A.122A: Dust opacity per unit gas+dust mass from Ossenkopf & Henning 1994; optical thickness correction applicable to the 10 densest cores (5 to 10% mass increase)
- 2022MNRAS.512.4419P: Optically thin dust continuum emission
- 2022MNRAS.512.4419P: Dust temperature equals average rotational temperature of COMs (thermal coupling at n_H2 > 10^6 cm^-3): 99 K (MM7), 134 K (MM8), 137 K (MM4), 100 K (MM11)
- 2022MNRAS.512.4419P: Dust grains with thin ice mantles at a gas density of 10^6 cm^-3
- 2024A&A...684A.200G: Optically thin emission.
- 2024A&A...684A.200G: Distance 650.9 ± 8.8 pc throughout.
- 2024A&A...684A.200G: Surface-density exponent -1.5; gas-to-dust ratio 100.
- 2024A&A...684A.200G: A_V = 0.5 mag; stellar parameters from Table 1.
- 2021ApJ...908..250H: Gas-to-dust mass ratio 100
- 2021ApJ...908..250H: Scale height exponent p = 1.25 with T proportional to r^-0.5; size distribution n(s) ~ s^-3.5
- 2018ApJ...869L..22W: optically thin dust emission; Kennicutt & Evans 2012 SFR calibration
- 2018ApJ...869L..22W: O/H=5.9e-4, most oxygen doubly ionized, gas-to-dust ~100, constant SFR
- 2024A&A...686A..64M: Schreiber2018 emissivity index β ∼1.5 applies to the sample
- 2024A&A...686A..64M: Derived gas mass includes molecular and atomic phases
- 2024A&A...686A..64M: Flat cosmology: ΩM = 0.3, Ωλ = 0.7, H0 = 70 km s−1 Mpc−1
- 2024A&A...686A..64M: S16 assumes constant δGDR and mass-weighted Tdust = 25 K
- 2021ApJ...921...97J: Uniform dust temperature; kappa_nu = 0.038 * (nu / 372.7 GHz)^beta_Td [m^2 kg^-1] from Draine (2003); beta_Td fixed to 2.0
- 2021ApJ...921...97J: GDMR = 100 for dust-based M_gas; Kroupa IMF with 0.2% O-type stars (10^49-51 erg over 5 Myr) and 7% supernova progenitors (10-40 M_sun, 10^51 erg each, <=1% ef…
- 2013A&A...557A.132M: Gas temperature equals mean dust temperature; [CO]/[H] ~1e-4; gas-to-dust 154
- 2015ApJ...813L..19J: Dust temperature 190 K from LTE modeling average
- 2019ApJ...871..170M: Thermal dust, optically thin; hydrogen dominated by H2
- 2018A&A...614A..17B: Optically thin dust, full gas-dust coupling
- 2015Natur.519..327W: dust temperature 35 K; optical depth unity at 200 µm
- 2024AJ....168..142L: Spherical grains; Mie scattering; azimuthally symmetric, optically thin disk; 1.65 microns.
- 2024AJ....168..142L: Scale height/radius = 0.055.
- 2019ApJ...872...92F: Optically thin emission; disk radius <16 au implied by unresolved emission at 101 pc; blackbody grains at 16 au have 20 K
- 2017ApJ...845L...5I: beta = 2, kappa_352GHz = 0.0865 m2/kg, Tdust = 150 K
- 2022MNRAS.509.2920N: 12CO(2-1)/12CO(1-0) = 0.8; X_CO = (1.0 +/- 0.3) x 10^20 cm^-2 (K km s^-1)^-1; M_HI / M_H2 = 0.5; M_dust = 10^6 M_sun; H2, HI, and dust all distributed as 12CO(…
- 2023A&A...669A..56Q: Gas-to-dust ratio = 200; constant mass distribution along the ejecta; momentum transfer rate of 1 g cm s^-1 per cm^2 per s for B = 3 G proportional to B_perp
- 2026ApJ..1005...94N: X_CO = 2 x 10^20 cm^-2 (K km s^-1)^-1, D_L = 107.2 Mpc, z = 0.024450, 12CO(2-1)/12CO(1-0) flux density ratio = 1, dust mass neglected
- 2024AJ....167...94H: Gas to dust ratio 200; dust optically thin for T_gr so masses for C and D are lower bounds
- 2021MNRAS.504.4123N: Starburst CO-to-H2 conversion factor X_CO = 1.0 +- 0.3 x 10^20 cm^-2 (K km s^-1)^-1; gas-to-dust ratio ~ 160; ISM distributed according to 12CO(1-0) and [CI](1…
- 2023Natur.622..251K: Collision at of order 10 au from the star, so dust at 100 K
- 2024A&A...682L...5G: Electron temperature of 10000 K; solar Ar/H and Ne/H from Asplund et al. (2021)
- 2024A&A...682L...5G: CO(3-2)/CO(1-0) ratio = 0.5-1 and alpha_CO = 0.8 M_sun [K km s^-1 pc^2]^-1
- 2014A&A...567A.125G: kappa_352GHz = 0.09 m^2/kg; gas-to-dust ratio ~60 from Draine et al. 2007 with 12+log(O/H)~8.8
- 2019ApJ...887...79H: gas-to-dust 100, kappa 0.9 cm2/g, Tdust 18±2 K, n=1.8, D=4.59 kpc, 30% uncertainty on R and kappa
- 2017ApJ...843...45K: d=700 pc, kappa850=0.17 m2/kg, T=50 K, beta=1 (central); 20 K, beta=2 (extended)
- 2017A&A...602A..19L: gas-to-dust ratio 100
- 2017A&A...602A..19L: gas-to-dust 100, d=353 pc; parameters degenerate
- 2025ApJ...991...59B: Dust and gas well coupled (Td ~ Tg ~ T), valid for n(H2) >~ 1e5 cm^-3
- 2025ApJ...991...59B: 870 um emission is thermal dust with little to no free-free contribution; for source E 1.2 mm used because no radio emission is detected there
- 2025ApJ...991...59B: Sources modelled as Gaussian profiles for deconvolved size
- 2025ApJ...991...59B: Simple metallicity scaling accounts for lower C, N, O abundances; detailed physicochemical modelling not done
- 2021ApJ...907...94C: Optically thin dust emission
- 2021ApJ...907...94C: kappa_nu = 0.01 cm^2 g^-1 at 1.3 mm; 2.6 × 10^-3 cm^2 g^-1 at 3 mm
- 2021ApJ...907...94C: Gas-to-dust ratio 100; mean molecular weight mu = 2.33
- 2021ApJ...907...94C: T_dust = 20–50 K for column densities; 25 K average for total masses
- 2025A&A...696A.232G: Dust surface density proportional to 1/r out to outer radius r_out, Gaussian vertical profile
- 2025A&A...696A.232G: Distance 160 pc, face-on inclination
- 2025A&A...696A.232G: Stellar effective temperature omitted because it has minimal impact on flux-derived dust mass
- 2025A&A...696A.232G: Optically thin mass uses kappa = 2.3 cm2/g and uniform T_dust = 20 K
- 2025A&A...696A.232G: Stellar luminosities from the stellar-parameters table; disks at the grid edge (binaries, tau >> 5) excluded as indeterminate
- 2022ApJ...930L...3W: Surface density Sigma(r) proportional to 1/r; spectral index of 2.2 for OTS 44 to scale 1.3 mm flux to 0.88 mm
- 2022ApJ...930L...3W: Constant accretion for 3 Myr; 12CO (3-2) emission is not absorbed by foreground clouds and CO is not heavily depleted onto grains
- 2019ApJ...871...85L: kappa = 2.64 m^2/kg at 125 um; Chabrier IMF
- 2025A&A...694A.218B: both galaxies share the integrated SED shape
- 2025A&A...694A.218B: M*/Mdust of high-z starbursts applies
- 2021ApJ...908...15S: dust mass absorption coefficient kappa_abs = 0.77 g^-1 cm^2 at 850 um; emissivity index beta = 1.5 for warm and 2 for cold components
- 2021ApJ...908...15S: M_gas includes both molecular and atomic hydrogen; magphys dust masses lower by factor two than Draine & Li based masses
- 2013Sci...340.1199V: Dust temperature 60 K; dust size distribution N(a)~a^-3.5; amorphous silicate spheres; gas/dust 100
- 2015ApJ...802..125R: T_dust = 20 ± 1 K, gas-to-dust 100, kappa_3mm = 0.27 cm2/g, beta = 1.2 ± 0.1
- 2018ApJ...856..118H: Td = 25 K; stellar-mass-dependent gas-to-dust ratio per Tacconi2018
- 2018A&A...615A..28D: Optically thin dust, opacity ~7 cm2/g, dust temperature 200-650 K (IK Tau) and 400-1530 K (R Dor)
- 2014ApJ...785..111W: dust-to-gas ratio 0.0052 (Draine 2007); H2/HI ~2
- 2026A&A...706A...4R: Opacity 10 cm^2/g at 1000 GHz scaled as nu^beta with beta=1, as in the earlier ALMA study; millimeter grains act as blackbodies
- 2017ApJ...849..123M: kappa = 2.3 cm2/g at 1.3 mm (scaled with nu^0.7); single SED-based T_dust
- 2019ApJ...887...74F: kappa_1THz=20 cm2/g; lambda_Edd=1; L'CO(5-4)/L'CO(3-2)=0.7
- 2022MNRAS.510.4485R: Milky Way B-band mass absorption coefficient Gamma_B = 8 x 10^-6 mag kpc^2 M_sun^-1; solar metallicity 12+log10(O/H) = 8.66 at gas-to-dust ratio of 100; neglec…
- 2020ApJ...889...85H: d = 3 kpc; optically thin; all emission thermal dust
- 2025ApJ...995L..63L: Chabrier IMF
- 2025A&A...700L..11S: Gas-to-dust ratio of 200; optically thin dust (alpha ~ 3); dust emission dominated by a cold detached component
- 2021A&A...645A..33B: Single dust temperature approximation (acknowledged as possible source of underestimated dust mass)
- 2020PASP..132h4401T: Dust mass lower limit assuming spherical grains, density 3.5 g/cm3, radius 1.0 um
- 2025A&A...696A..59P: Dust mass fraction in AGN-B equals 62%; M_dust/M_* = 0.02±0.01
- 2015ApJ...803...60S: kappa340 = 0.9 cm2/g (Draine & Lee), Td = 39.4 K
- 2019A&A...632A..83S: All 3.1 mm emission is optically thin dust; κ per unit mass of gas+dust
- 2016ApJ...819..102V: Astronomical silicates, amin 0.05 um, amax 1 mm, dn/da ~ a^-3.5, kappa 3.72 cm2/g at 885 um
- 2016ApJ...819..102V: kappa885 = 2.7 cm2/g, beta = 0.4, T=25 (L/Lsun)^0.25
- 2024RAA....24f5011X: dust temperature of each ACA source equals the H2CO kinetic temperature
- 2024RAA....24f5011X: distance uncertainty 20% and flux calibration uncertainty 10% included in mass errors
- 2022MNRAS.515.5730K: optically thin emission at 1.4 mm, dust temperature = 38 K, gas-to-dust ratio = 100, opacity per cloud mass = 0.3 cm^2/g for beta = 2 (or gas-to-dust ratio = 1…
- 2022MNRAS.515.5730K: mean molecular weight mu = 2.86, kappa_nu = 0.1 cm^2/g at 250 um, gas-to-dust ratio = 100, beta = 2.0, flux uncertainties = 15%
- 2025ApJ...984L..16G: Radially constant α=2×10−3; locally isothermal equation of state
- 2025ApJ...984L..16G: Initially perfectly mixed gas and dust; gas-to-dust ratio 100; a=0.14 mm; ρs=1.26 g cm−3
- 2025ApJ...984L..16G: Fixed radial locations, circular orbits, unchanged initial azimuthal angles
- 2021ApJ...910...75L: Gas to dust mass ratio of 100, gas of molecular hydrogen and atomic helium
- 2021ApJ...910...75L: Absorption opacity 1.9 cm^2 per gram of dust at 878 um (Q~1)
- 2021ApJ...910...75L: Inclination ~87 deg, nearside tilted slightly to the south
- 2021ApJ...910...75L: LTE radiative transfer
- 2024A&A...684A..33K: Optically thin dust at lambda>40 um (may bias T_dust low and M_dust high if thick)
- 2024A&A...684A..33K: ULIRG-like alpha_CO=0.8 (alpha_CO,tot = alpha_CO,intr / f_CMB with the CMB correction)
- 2024A&A...684A..33K: Dynamical masses taken at face value ('if the dynamical masses are reliable')
- 2022MNRAS.515.1751W: κ_ν,ref = 8.94 cm^2 g^-1 at λ_ref = 158 μm; clustering factor C = 1; Chabrier (2003) IMF for dust yields; Kennicutt & Evans (2012) SFR conversions
- 2022MNRAS.515.1751W: Zanella et al. (2018) calibration holds at z ~ 7
- 2013A&A...557A.133D: Astronomical silicates, size slope -3.5, max radius 1 mm; gas-to-dust 100; CO/H2 1e-4; LTE with Tgas=Tdust; Keplerian rotation
- 2018ApJ...869...27V: Fundamental Metallicity Relation for metallicities
- 2016A&A...596A..50G: Reference r_gd = 200; distance (50 kpc) assumed
- 2014A&A...562A..67G: kappa = 4.0 (nu/1.2 THz)^beta cm2/g, beta=2
- 2025A&A...693A.151M: T(R)=278.3 L^0.25 R^-0.5
- 2017ApJ...850L...6A: kappa_nu = 2 cm^2 g^-1; size distribution power-law index -3.5
- 2019ApJ...880....2W: alpha_CO=0.8 cool, 0.16 warm; gas-to-dust ratio 80
- 2020ApJ...896...43W: 12CO/13CO = 40; gas-to-dust 100; Ossenkopf & Henning dust opacities
- 2020ApJ...890L..14T: dust-to-gas ratio 100; Ossenkopf & Henning coated silicate grains
- 2024ApJ...963..103G: X_CO = (0.28–2) x 10^20 cm^-2 (K km s^-1)^-1; uniform HI distribution with N(HI) = (1.51 +/- 0.05) x 10^18 cm^-2; A_V = 4.81 x 10^-22 (N(HI) + 2N(H2)); kappa_3…
- 2025A&A...699A..22M: disk emits as a blackbody; gas-to-dust ratio 200; primary mass-loss rate 7.7e-7 Msun/yr
- 2021A&A...652A..98G: Galactic X_CO
- 2020AJ....159..288M: κν=2.3 cm2/g, grain temperature ~15 K at 140 au
- 2019ApJ...884...48C: Td 23 K (MM2), 27 K (MM3), 28 K (MM4), 25 K (MM6-8); d=5.5 kpc; optically thin
- 2017ApJ...851...85B: gas-to-dust 100, CO/H2 7e-5, shared temperature structure
- 2017ApJ...851...85B: Optically thin dust, constant midplane temperature in outer disk; opacity 4.94 cm2/g at 890 um
- 2025A&A...701A.219N: Dust opacity k_1.3 = 0.005 g cm^-2 including a gas-to-dust mass ratio of 100; log(L/M) = 1.20 log(SFE) + 3.28
- 2025A&A...701A.219N: Optically thin 1.3 mm dust emission, single temperature per clump based on L/M, distance D = 5.2 kpc, kappa_1.3 = 0.005 g cm^-2 (gas-to-dust ratio 100)
- 2020ApJ...904...77G: Homogeneous dust source; Ω≈3×10^-3 arcsec^2
- 2020ApJ...904...77G: κ_nu ∝ nu^β; β=1.7; κ_231GHz=0.00899 cm^2 gr^-1; gas-to-dust mass ratio 100
- 2020ApJ...904...77G: Dust temperature below sublimation temperature
- 2020ApJ...904...77G: Mean mass per electron μ_e=1.3 m_H for fully ionized HII and HeI region
- 2025A&A...698A.165A: Optically thin emission at scales much larger than 10 au
- 2025A&A...698A.165A: Rayleigh-Jeans Planck function
- 2025A&A...698A.165A: Gas-to-dust mass ratio of 100 in the Cieza relations
- 2025A&A...698A.165A: Optically thin dust in the Rayleigh-Jeans limit, alpha = beta + 2
- 2023A&A...677A..76P: Dust grains made of 19.2% carbon, 60.8% silicates, and 20% vacuum by volume; Dubrulle et al. (1995) dust settling; Gaussian vertical gas profile
- 2023A&A...677A..76P: Axisymmetric disk
- 2019PASJ...71...71H: kappa0 = 10 cm2 g-1 at 250 um (Hildebrand 1983); using Dunne 2000 doubles M_d
- 2019PASJ...71...71H: Clumps assumed to have same T_d, beta_d as whole system
- 2024A&A...691A.248L: M_gas ~ M_H2 holds for z > 0.4 (z < 0.4 excluded and supplemented with Saintonge et al. 2017 local data); PP04 N2 metallicity scale
- 2022A&A...664A..63X: Chabrier (2003) IMF, Draine (2014) dust model, Fritz (2006) AGN template
- 2022A&A...664A..63X: Helium correction factor of 1.36; PP04 metallicity scale with 0.15 dex uncertainty; RJ-tail parameters: beta = 1.8, T_d = 25 K, alpha_850 = 6.7e19 erg s^-1 Hz^…
- 2015A&A...575L...5H: gas-to-dust 100; CO abundance 1e-4 where Tdust>20 K; 12CO/13CO=76; Tgas=Tdust
- 2015ApJ...801...82H: kappa=0.1 cm2/g at 250 um, gas-to-dust 100, D=420 pc
- 2018ApJ...869..126L: Tdust 130 K (60-160 K range), kappa uncertain by factor ~2
- 2017ApJ...841..110S: Optically thin dust; 10% of stellar flux reddened to 900 K for disk case
- 2015ApJ...811..124S: kappa_870=0.077, delta_GDR=72, solar metallicity, gamma=1, 25% dark matter, CO(2-1) thermalized
- 2025A&A...703A..15M: Optically thin thermal emission at 1.33 mm dominated by large blackbody grains with T_BB(K) = 278 (L_*/L_sun)^0.25 (R_disk/au)^-0.5 (or T_BB = 60 K for HD 1319…
- 2018ApJ...869...75M: κ=2.3 cm2/g for belt, 1.3 cm2/g for halo micron grains
- 2018ApJ...866..159V: T_dust=47 K, beta=1.6, negligible dust optical depth, Kroupa IMF, all dust heated by star formation
- 2020ApJ...892..147S: kappa_160um=13.1 cm2/g; drop factor 2.5+-0.5
- 2026ApJ..1000..144T: Grain sizes 0.005–0.22 μm; specific grain mass density 3 g/cm^3.
- 2026ApJ..1000..144T: Graphite and silicate with equal absorption; size distribution proportional to a^−3.5.
- 2025AJ....169..230H: Optically thin mm continuum emission, dust temperature T = 150 K, and gas-to-dust ratio of 200.
- 2020ApJ...895...74N: Td = 47 K, beta = 1.6, kappa(850um)=0.077 m2/kg
- 2019A&A...629A..29J: gas-to-dust 100; bare-grain opacities; distance 200 pc
- 2017ApJ...848L..11K: Constant h/r = 0.05; surface density Σ ∝ r−1.5
- 2017ApJ...848L..11K: Fixed gas-to-dust ratio; relatively high viscosity α ≈ 0.01
- 2024AJ....168..151J: Single dust temperature; optically thin dust emission
- 2024AJ....168..151J: Gas-to-dust ratio η = 100
- 2024AJ....168..151J: Dust opacity 1.37 cm² g−1 at 1.0 mm for volume density 10^6 cm−3
- 2024AJ....168..151J: Distance 414 pc
- 2020ApJ...890...76N: Gas-to-dust ratio 100; kappa 1.85 cm2/g
- 2020ApJ...890...76N: Rgd=100; k100GHz=0.21 cm2/g; mu_H2=2.8; virial equilibrium for 0.71<alpha<1.4
- 2026A&A...705A..96M: κ3mm~1 cm² g⁻¹; gas-to-dust ratio=100
- 2026A&A...705A..96M: Literature protostellar masses; M*=1 M☉ when absent; equal component masses for binaries with only combined mass
- 2026A&A...705A..96M: Optically thin emission; gas-to-dust ratio=100
- 2021MNRAS.501.2934C: Dust opacity kappa_1.3mm = 2.3 cm^2 g^-1, dust temperature = 20 K, distance = 140 pc for targets without Gaia parallax, and low-resolution 1.3 mm fluxes used f…
- 2021MNRAS.501.2934C: All features in a given disc share the same center, position angle, and inclination; inner disc dust mass uses T = 20 K and kappa_1.3mm = 2.3 cm^2 g^-1
- 2019MNRAS.482.3135B: beta=1.8; kappa_850=0.077 m^2/kg
- 2025A&A...693A.190J: Mass-weighted dust temperature T_rest = 25 K at all redshifts
- 2025A&A...693A.190J: Flat LCDM, Omega_m = 0.3, Omega_Lambda = 0.7, H0 = 70
- 2025A&A...693A.190J: Adding bootstrap and RMS errors quadratically is an approximation that slightly over-estimates the error (they are correlated)
- 2023ApJ...952...48H: X[CI]/X[H2] ~ 1.6 x 10^-5 (and up to 10x higher conversion factor at low Z)
- 2023ApJ...952...48H: HII region contribution to [CII] is ~30% and CMB attenuation factor for [CII] is f_CMB = 0.5 - 1.0
- 2023ApJ...952...48H: Gas is predominantly in the molecular phase for the dust-based estimate
- 2015ApJ...805L..17B: T = 20 K for A; 10-20 K for B; gas-to-dust 100
- 2014A&A...569A..11S: kappa=1.75 cm2/g at 870 um, gas-to-dust 100, mu=2.3, D=2.19 kpc
- 2017A&A...601L...3P: Gas-to-dust ratio 100 by mass
- 2017A&A...597A..99W: [CO]/[H2]=1e-4, turbulent velocity 1 km/s, gas-to-dust 40, distance 4 kpc, constant isotropic smooth mass-loss
- 2015A&A...574A..19S: Td = 35 K adopted
- 2024A&A...686A.206Y: millimetre dust opacity 2.3 cm^2 g^-1
- 2019ApJ...883..180H: kappa=2.3(nu/230GHz)^beta cm2/g, beta=0.7; 12C/13C=77
- 2017A&A...605A.105C: Td=40-60 K, beta=2.0, kappa=0.45 (nu/250GHz)^beta cm2/g, continuum all dust
- 2020ApJ...903...94M: Tdust 22 K, gas-to-dust 300, kappa_1.3mm 1 cm2/g
- 2018A&A...615A...9P: distance 436 pc
- 2019ApJ...871....5T: Gas-to-dust mass ratio 100; CO abundance 1e-4; HCO+ 1e-9; turbulence 120 m/s; LTE
- 2019ApJ...871....5T: Temperature 180 K in cavity
- 2024ApJS..270....9X: Single dust temperature; all emission from optically thin dust
- 2024ApJS..270....9X: Gas-to-dust mass ratio 100; κν=1.89 cm2 g−1 at ~350 GHz
- 2024ApJS..270....9X: Thin ice mantles; MRN distribution; gas density 10^6 cm−3
- 2024ApJS..270....9X: Spherical cores; μH2=2.81
- 2024ApJS..270....9X: Uncertainties: gas-to-dust ratio 28%, opacity 23%, flux ~14%, temperature ~20%, distance 10%
- 2021MNRAS.503...77W: Optically thin 1.3 mm dust emission
- 2021MNRAS.503...77W: Dust opacity kappa_0 = 0.9 cm^2 g^-1 at 230 GHz and beta = 1.75
- 2021MNRAS.503...77W: Distance d = 8.1 kpc
- 2021MNRAS.503...77W: Gas-to-dust ratio = 100
- 2021MNRAS.503...77W: Dust temperature T = 22 K (and 167 K / 120 K for internally heated sources #1a / #1b)
- 2025NatAs...9.1176R: Optically thin emission, average dust temperature 20 K, power-law dust opacity; gas-to-dust ratio 100 used later for disk mass in simulations
- 2025NatAs...9.1176R: Gas-to-dust ratio 100, locally isothermal disk with T proportional to R^-0.5 and surface density proportional to R^-1
- 2021MNRAS.501.4317P: Optically thin millimetre dust emission, isothermal dust temperature of 20 K, maximum grain size around 1 mm
- 2021MNRAS.501.4317P: Local thermodynamic equilibrium (LTE), optically thin 13CO J=2-1 emission, gas temperature of 20 K, standard 13CO abundance of 1.3e-6
- 2018MNRAS.474.4039M: Galaxy fraction of Herschel flux = ALMA fraction 0.27
- 2025ApJ...995..150K: Dust mass absorption coefficient from Dunne et al. 2000, kappa = 0.77 (850 um/lambda_rest)^beta cm2/g
- 2025ApJ...995..150K: beta_IR = 1.5, T_dust = 40 K (also 35 and 45 K tabulated)
- 2025ApJ...995..150K: Atomic HI gas mass ignored
- 2025ApJ...995..150K: Solar 12+log(O/H)=8.69 and metal mass fraction 0.0134; primordial He fraction 0.2485
- 2023MNRAS.523.4654T: gas-to-dust ratio uses Jones et al. CO(2-1) gas mass with alpha_CO = 0.8 and r21 = 0.85
- 2023MNRAS.523.4654T: gas-to-dust ratio of 54.2 +/- 9.3 applied uniformly
- 2014Natur.514..600D: gas-to-dust 100, kappa(1.3 mm)=0.02 cm2/g
- 2015MNRAS.447.1826Z: gas-to-dust 100, D=2.9 kpc, Td=250 K (IRAS 16547), 150 K (W), kappa=0.015 cm2/g
- 2017ApJ...849...81A: T_dust = 25 K; all continuum is dust (free-free up to 20%)
- 2018A&A...616A..34H: kappa=7 cm2/g, mean dust temperature ~700 K (T radial power law index -0.5), dust-to-gas 2e-2, mass-loss 1.2e-7 Msun/yr, optically thin
- 2015MNRAS.452...54M: Dust temperature 27.6 K (beta=1.5) or 45 K; all sources at z=7 for CMB correction
- 2025A&A...698A.183D: kappa = 1.7 cm2/g (850 um/lambda)
- 2019A&A...626A..93V: Static velocity field; gas-to-dust 100; Ossenkopf & Henning dust opacities
- 2019A&A...624A...7V: Gas-to-dust ratio 100; astronomical silicates; dn(a) ∝ a^-3.5 da
- 2026AJ....171..368M: Source distance fixed at 1.78 kpc; AKARI, Herschel, and Spitzer/IRAC fluxes treated as upper limits
- 2026AJ....171..368M: Optically thin dust continuum; T_d = 150 K; mean molecular weight mu_H = 1.41; dust-to-gas ratio Z = 0.01; dust opacity kappa_nu = 0.90(nu/230 GHz)^beta cm^2 g…
- 2021A&A...650A.202R: T_dust = T_gas = 10 K (dust-gas coupling at high density); also re-done with T_H2D+ maps and T_min
- 2024ApJ...971L..23L: Purely thermal dust emission, LTE everywhere
- 2024ApJ...971L..23L: Gas to dust mass ratio ~100
- 2024ApJ...971L..23L: Density power-law index n = 2.5
- 2024ApJ...971L..23L: Dust opacity law kappa_lambda = kappa_0 (9.1 mm/lambda)^beta
- 2023A&A...675A.131T: Optically thin continuum emission; d = 157 pc; kappa_nu = 10 (nu / 1000 GHz)^beta cm^2 g^-1 with beta = 1; T_dust = 28.2 K
- 2023A&A...675A.131T: Optically thin emission; 12C/13C = 68 +/- 15; 16O/18O = 557 +/- 30; H2/12CO = 10^4; mean molecular weight = 2.4
- 2017A&A...602A..11P: CO 3-2/1-0 flux ratio = 9 (thermalised)
- 2026MNRAS.546f2284B: Optically-thin dust emission; flat Lambda-CDM cosmology with Omega_m = 0.315, Omega_Lambda = 0.685, h = 0.674
- 2026MNRAS.546f2284B: Gravitational lensing affects stellar and dust components equally (no differential lensing)
- 2026MNRAS.546f2284B: Homogeneous dusty sphere foreground screen geometry; dust-emitting radius equals optical size of the source
- 2022MNRAS.510.4976A: Opacity law kappa(nu) = 0.077 * (nu / 352 GHz)^beta m^2 kg^-2 with dust emissivity index beta = 1.6
- 2022MNRAS.510.4976A: T_dust = AGN dust temperature from Shanks et al. (2021) when available, otherwise 35 K for WHDF sources, and 47 K for z>6 quasars
- 2022MNRAS.510.4976A: Chabrier IMF and SFR_IR / (M_sun yr^-1) = 1.49e-10 * (L_IR / L_sun)
- 2022MNRAS.510.4976A: Eddington limit lower bound Sigma_SFR ~ 650 M_sun yr^-1 kpc^-2 assuming gas fraction f_gas = 1 and dust-to-gas ratio f_dg = 1/90
- 2014ApJ...784...82M: d=400 pc, kappa=0.034 cm2/g with gas-to-dust 100:1, T=20 K (40 K for massive stars)
- 2013ApJ...774L...7M: Td 400 K, equilibrium range 400-1000 K at 1" with L=7e5 Lsun
- 2016ApJ...833L...6C: LMC X_CO = 4.7e20 cm-2 (K km/s)-1; R31=7.4
- 2017A&A...603A..92V: gas-to-dust ratio 100
- 2015A&A...584A..99E: r6-5 = 13 (17-36 for wings), X_CO = 0.8, optically thin dust, kappa = 4.0 (nu/1.2 THz)^-2.0 cm2/g, T_dust = 45 K
- 2017A&A...604A..60B: Td=150 K, mu_H2=2.8, gas-to-dust 100
- 2017MNRAS.468..685Q: Gas-to-dust ratio of 100
- 2017MNRAS.468..685Q: Ideal gas law, infall velocity for spherical envelope, Keplerian rotation for disc, constant velocity parallel to outflow axis plus infall for outflow
- 2024ApJ...962...13C: Gas-to-dust ratio eta = 100
- 2024ApJ...962...13C: Mean particle weight mu = 2.8
- 2024ApJ...962...13C: Optically thin dust at 870 um
- 2024ApJ...962...13C: Distances from Table 1 (HI analysis, maser parallax, spectroscopy)
- 2020A&A...636A..26H: T_dust = 30 K, gas-to-dust 100, kappa 0.7-2.4 (204 GHz) and 2.2-5.0 (397 GHz) cm2/g
- 2020A&A...636A..26H: Disk mass 0.03 Msun, gas-to-dust 100, water 1e-4 where T>100 K, kappa 0.7 vs 2 cm2/g
- 2024AJ....167...75H: Gas-to-dust mass ratio of 100
- 2024AJ....167...75H: Gap between inner and outer disks is devoid of material
- 2024AJ....167...75H: Edge-on innermost disk excluded from the model
- 2020NatAs...4..142L: Vertical hydrostatic equilibrium with Keplerian rotation around M_* ~ 1.5 M_sun, and outer geometric thinning between R_t and R_o
- 2020NatAs...4..142L: Mass density rho = 1.4 n m_H2 (helium at solar abundance) and gas-to-dust mass ratio of 100
- 2020NatAs...4..142L: Dust opacity law kappa_nu = 0.1 (nu / 10^12 Hz)^beta cm^2 g^-1 with beta = 0.6 to 1.0, giving kappa_nu ~ 0.054 - 0.035 cm^2 g^-1 at 343 GHz
- 2017A&A...606A..17M: Flat LCDM, H0=70, Om=0.30
- 2025ApJ...989..115T: Chabrier IMF; BC03 stellar population with solar metallicity; Calzetti attenuation; Draine 2014 dust templates
- 2025ApJ...989..115T: Differential magnification negligible so quantities scale linearly with magnification
- 2022MNRAS.512.2426M: Flat LambdaCDM cosmology with h = 0.677 and Omega_m = 0.307
- 2022MNRAS.512.2426M: Dust mass absorption coefficient extrapolated from kappa_850 = 0.077 m^2 kg^-1 to 873 um, constant across sample
- 2022MNRAS.512.2426M: Kroupa IMF conversion log(SFR) = log(L_IR) - 43.41 assuming all IR emission is from star formation (no AGN contribution)
- 2014ApJ...787...42C: dust-to-gas ratio 0.01
- 2013ApJ...764L..14Z: kappa = 2.2 cm2/g, beta = 0.6, Td = 160 K, d = 120 pc
- 2017A&A...608A..22A: CO abundance 1e-5 to 1e-4
- 2017A&A...608A..22A: gas-to-dust ratio 100
- 2017ApJ...841..130A: kappa(343 GHz)=1.7 cm2/g; T=80+-10 K
- 2014ApJ...792...34O: Dwarf-galaxy T_dust=27.6 K, beta=1.5; Salpeter IMF; cosmology (0.3,0.7,0.7)
- 2018ApJ...863...19A: Optically thin, Tdust=20 K, kappa(850um)=0.035, beta=1, gas-to-dust 100 (mass)
- 2018ApJ...863...19A: LTE, gas T = dust T = 20 K, kappa(850um)=0.035, beta=1, gas-to-dust 100, mean molecular weight 2.37
- 2018ApJ...859..111H: Grain sizes 0.1 um to 3 mm, n(a)∝a^-3.5; 30% amorphous carbon/70% astrosilicate; kappa_1.3mm=2.2 cm2/g; Tstar=3859 K, R=0.8 Rsun; Rin 0.05 au; gas-to-dust 100
- 2024ApJ...972..115C: Optically thin dust emission; gas and dust in thermal equilibrium; mean molecular weight 2.8
- 2024ApJ...972..115C: Optically thin dust (gravitational energy a lower bound if thick); ideal gas for thermal energy; MM7 and MM9 excluded for lack of C33S coverage
- 2020ApJ...896...35J: kappa(1.21 mm)=0.24 cm2/g; g=154; d=4.2 kpc; OH94 opacity would lower masses by ~4
- 2020ApJ...896...35J: Optically thin NH3
- 2024Sci...383..988B: d=414 pc; Td=20 K; kν=0.034 cm² g−1.
- 2024Sci...383..988B: Gas-to-dust mass ratio 100.
- 2024Sci...383..988B: Optically thin 344 GHz emission.
- 2024Sci...383..988B: Mass interval incorporates 0.2 dex optical-depth uncertainty and both adopted opacity values.
- 2023ApJ...948L...2Y: Dust temperature = 100 K
- 2023ApJ...948L...2Y: Dust opacity = 3.5 cm^2/g at 870 um
- 2023ApJ...948L...2Y: Optically thin thermal dust emission
- 2017ApJ...837L..21L: magnification mu=1.8±0.3
- 2024ApJ...968...15L: T_dust = 33 K
- 2024ApJ...968...15L: kappa at 500 micron = 0.051 m^2/kg
- 2024ApJ...968...15L: Gas-to-dust ratio 35
- 2024ApJ...968...15L: Spatially varying gas-to-dust conversion factor is not modelled
- 2020MNRAS.494.5542R: Optically thin dust emission; uniform T_dust and beta; Salpeter IMF; CMB effects negligible (<=0.1 K, <=0.1 dex)
- 2013PASJ...65L..14F: gas-to-dust 100; T=36 K; distance 140 pc
- 2015ApJ...807L...4F: Dust temperature 20 K
- 2018MNRAS.480.4991G: kappa=0.294 cm2/g at 1 mm, Td=100 K, gas-to-dust 100, d=3.38 kpc
- 2015ApJ...810...91H: kappa_d(125 um)=2.64±0.29 m^2/kg, beta=1.5, T_dust=30-40 K
- 2019ApJ...886..102S: core temperature equals clump temperature; 30 K tested for protostellar cores
- 2019ApJ...882..160Q: Draine astronomical silicates and graphite, dust-to-gas 0.0065, n(a) ∝ a^-3.5 from 0.005 μm, large grains 1 mm within 0.1H
- 2025ApJ...988...95D: Optically thin dust emission.
- 2025ApJ...988...95D: Gas-to-dust mass ratio 100; μ = 2.8.
- 2025ApJ...988...95D: κν = 0.2 cm^2 g^-1 at ~3 mm, OH5 dust model.
- 2025ApJ...988...95D: Dust temperature equals average derived rotational temperature.
- 2020ApJ...903...50E: Optically thin dust emission (tau_350 ~0.02-0.10)
- 2026A&A...710A.238D: Power-law grain size distribution n(a) propto a^-q; Bruggeman and Maxwell-Garnett mixing rules for opacities; bulk densities 1.675, 0.503, 2.036, 0.611 g cm^-3…
- 2026A&A...710A.238D: Constant Sigma_d extrapolated inward from 11 au to 0 au for total dust mass calculation
- 2026A&A...710A.238D: Hydrostatic equilibrium and isothermal vertical structure for gas pressure; total g2d = 100 assumed for Elias 2-24; dynamical gas masses for IM Lup and DM Tau
- 2021ApJ...923..121Y: T_d(r) = T_br(r) in optically thick inner region (r < 5 au) with power-law index -0.5
- 2021ApJ...923..121Y: Two dust opacity models: DSHARP kappa_nu,I with s_max = 0.1 mm (Birnstiel et al. 2018) and conventional kappa_nu,II = 2.3 (nu/230 GHz)^0.4 cm^2 g^-1 (Beckwith …
- 2021ApJ...923..121Y: Gas-to-dust ratio Sigma_gas / Sigma_dust = 100 and stellar mass M_* = 2.19 M_sun for Toomre Q
- 2017ApJ...837..182O: Total IR luminosity due to star formation; Salpeter IMF; Kennicutt (1998) calibration
- 2025A&A...695L..18M: Dust emission optically thick in the inner center of the host; beta=1.8 equal to the median of z>5 samples; Draine (2003) opacity prescription; cosmology Omega…
- 2021MNRAS.505.4838L: H_0 = 70 km s^-1 Mpc^-1, Omega_m = 0.3, Omega_Lambda = 0.7
- 2021MNRAS.505.4838L: LTM model magnifications; dust temperature T_dust = 30 K (also tested 35 K for IRX and 85 K upper limit) and dust emissivity beta = 2.0; Chabrier IMF
- 2015ApJ...812..134H: Td = 50 K, gas-to-dust 100, kappa(345 GHz) = 1.5 cm2/g, distance 450 pc, optically thin
- 2013ApJ...779...96T: kappa_1.338mm = 5.95e-3 cm2/g, gas-to-dust 141, Td = 10+/-3 K, 20% distance error
- 2017A&A...608A..56G: Gas-to-dust ~60; optically thin dust; negligible HI; D=14 Mpc
- 2018A&A...618A.164S: kappa=0.33 cm2/g at 1 mm; gas-to-dust 100-200; alpha=0 for big grains; Lbol~7000 Lsun
- 2019A&A...626A..36D: distance 5.2 kpc; Td 100/35 K; Ossenkopf & Henning ice-mantle opacity
- 2019A&A...622A..75L: 75% silicate + 25% carbon, Mie opacities, a^-3.5 size distribution, amin 0.01 um, amax 3 mm (LGP), 2 um (SGP); gas-to-dust 100 initially
- 2024ApJ...974..257Z: Td = 150 K for IRAS 16547-E and -W
- 2024ApJ...974..257Z: Td = 50 K for the other sources
- 2024ApJ...974..257Z: Td = 16 K for the envelope, from the HN13C line
- 2020ApJ...905...25G: κ_227GHz=0.0083 cm² g^-1; includes gas-to-dust ratio 100
- 2020ApJ...905...25G: Td lower limits from peak continuum brightness or Tgas,min=200 K
- 2020ApJ...905...25G: Distance 5.4 kpc
- 2024ApJ...970..114T: Gas temperature equals dust temperature
- 2024ApJ...970..114T: Toroidal-dominated magnetic field
- 2023MNRAS.522.2384M: Isothermal conditions and optically thin dust emission
- 2023MNRAS.522.2384M: Dust opacity at 1.3 mm kappa_nu = 2.17 cm^2 g^-1
- 2023MNRAS.522.2384M: Dust temperature T_dust between 20 K and 50 K
- 2023MNRAS.522.2384M: Distance d = 131 pc
- 2023MNRAS.522.2384M: Gas-to-dust ratio of 100
- 2017ApJ...846..108C: Gas and stars share same half-light radius; constant velocity dispersion
- 2025A&A...701A.120P: CMB contrast correction.
- 2025A&A...701A.120P: Entire Balmer continuum absorbed and re-irradiated by optically thin dust; Kroupa IMF; unobscured star formation negligible for MQN01.
- 2023MNRAS.524..923Z: Flat LambdaCDM cosmology with Omega_m = 0.3, Omega_Lambda = 0.7, H_0 = 70 km s^-1 Mpc^-1; r_32 = 0.5; alpha_CO = 4.4 M_sun K km s^-1 pc^2; optically thin dust …
- 2014ApJ...783L..13P: T=35 K, gas-to-dust 100, kappa=10 cm^2/g at 450 um for mass
- 2014ApJ...783L..13P: a=1 mm, rho_s=1 g/cm3, Sigma=10 g/cm2, St~1e-2; gas T=50 K for sound speed
- 2014Natur.510..247H: kappa_d proportional to nu^beta, kappa_d(125 um)=26.4 cm2/g
- 2018MNRAS.474.3640M: Salpeter IMF 1-100 Msun, solar metallicity, continuous SF at 24 Msun/yr, gas-to-dust ratio ≈160, 1-D slab, log NH 19-23
- 2019A&A...629A.136S: gas-to-dust ratio ~100; T_d~160 K; emissivity ∝ ν^1
- 2018A&A...615A..83V: gas-to-dust 100, CO/H = 1e-4 where T>20 K, Tgas=Tdust
- 2017ApJ...835...17M: kappa=3.4 cm2/g at 870 um; T_dust=24 K (disk A), 18 K (at GQ Lup b); gas-to-dust 100 for total CPD mass
- 2024ApJ...961L..35M: Optically thin 3 mm emission in LTE
- 2024ApJ...961L..35M: T_dust = 14.2 K (MM1-C) and 22.6 K (MM1-E1) from NH3 gas kinetic temperature
- 2024ApJ...961L..35M: Gas-to-dust ratio 100
- 2024ApJ...961L..35M: kappa_nu = 0.18 cm2 g-1 (OH5 model)
- 2021A&A...650A.142M: Disk close to edge-on
- 2021A&A...650A.142M: Dust opacity 1 cm2 g−1 at 1.4 mm; gas-to-dust ratio 100; average dust temperature 200 K
- 2025ApJ...995...16Z: Dust composition and gas-to-dust ratio fixed; disk substructures not modeled
- 2025ApJ...995...16Z: Optically thin emission at the observing frequency
- 2021A&A...656A.150P: Optically thin emission with constant dust temperature T = 20 K
- 2021A&A...656A.150P: Midplane physical temperature of 20 K constant for the optical depth estimate
- 2016A&A...596A..75S: T~40K for ALMA-only dust mass
- 2025ApJ...990L..61C: Dust mass absorption coefficient from (cite: li01a); dust emissivity index β=2
- 2025ApJ...990L..61C: Cold dust temperatures ≲50 K are not expected given compact morphologies.
- 2025ApJ...990L..61C: Planck cosmology
- 2021ApJ...917...99Y: LambdaCDM cosmology with H0 = 70 km s^-1 Mpc^-1, Omega_M = 0.3, Omega_Lambda = 0.7
- 2021ApJ...917...99Y: Dust continuum traces molecular gas (for CO magnification) and SFR surface density
- 2015ApJ...799..204C: gas-to-dust ratio 100 for interstellar gas, adjusted to 75-100 to match HD
- 2014ApJ...789L...4T: Td = 10 K, beta = 1, kappa231GHz = 0.01 cm2/g, d = 140 pc
- 2016ApJ...821..112K: D=3.5 Mpc, Td=25 K for global disk
- 2017ApJ...835L..13S: excess emission is thermal dust; free-free negligible
- 2019ApJ...872...70T: Gas-to-dust ratio 100, tau≈1, spherical geometry for densities, distance 414 pc
- 2017ApJ...851L..23C: Gas-to-dust ratio 100, Andrews et al. 2010 parameterization
- 2026ApJ..1003..219W: Gas-to-dust mass ratio 100; distance 8.3 kpc
- 2026ApJ..1003..219W: κν = 1.99 cm2 g−1; grains without ice mantles at gas density 10^6 cm−3
- 2026ApJ..1003..219W: Tdust ≈ Tex from CH3OH
- 2026ApJ..1003..219W: Optically thin 1.3 mm emission; resulting mass is a lower limit
- 2021MNRAS.507.1886F: D = 778 pc
- 2021MNRAS.507.1886F: k_1.1mm = 0.0078 cm^2 g^-1, gas-to-dust ratio = 100, T_dust = 200 K
- 2024ApJ...973..135H: Gas-to-dust ratio fixed to 100
- 2024ApJ...973..135H: PAH abundance 0.1 x ISM; cosmic ray ionization rate 1e-18 s^-1
- 2024ApJ...973..135H: Axisymmetric disk; spiral structure not modelled
- 2020ApJ...904...37W: Gas-to-dust ratio 100:1
- 2020ApJ...904...37W: Dust opacities from OpacityTool with 60% amorphous silicates, 15% amorphous carbon, 25% porosity, Bruggeman mixing, hollow spheres maximum hollow ratio 0.8, si…
- 2025A&A...694A.171M: Optically thin dust; fixed T_dust and beta from literature
- 2025A&A...694A.171M: Cosmology H0=67.8, OmegaM=0.3, OmegaL=0.7
- 2022MNRAS.514.2346K: alpha_CO = 4.36 M_sun (K km s^-1 pc^2)^-1
- 2022MNRAS.514.2346K: M_HI approx M_mol, so delta_GDR * M_dust approx 2 * M_mol
- 2022MNRAS.514.2346K: Fundamental Mass Metallicity relation (Mannucci et al. 2010) rescaled to Pettini & Pagel (2004)
- 2015ApJ...798L..23K: Dust temperature ~10–20 K; opacity 2.3 cm^2/g at 1.3 mm
- 2015ApJ...806...35J: n_H2/n_CO = 2e4; XCO = 0.5e20; kappa 0.9 cm2/g; gas-to-dust 120; Td 20 K; distance 21.5 Mpc
- 2017ApJ...849...14S: alpha_d = 3.8 (optically thin dust, beta=1.8); alpha_p from 6–33 GHz
- 2018A&A...617A..89C: κ345GHz = 0.0185 g cm-2 (incl. gas-to-dust 100), β = 2, Td = 22 K for MDC
- 2025A&A...698L..16S: Icy-mantled grains at ∼10^6 cm−3
- 2025A&A...698L..16S: Dust-to-gas ratio of 100, as written
- 2025A&A...698L..16S: Line-of-sight length equals the B3 wall width, ∼250 au
- 2021A&A...653A.129C: Continuum brightness temperature follows a power law in frequency with alpha = 2 + beta for optically thin dust emission
- 2024A&A...681A..82G: Stellar parameters of HD163296: 2.04 Msun, 17 Lsun, 9332 K, 101 pc; DSHARP opacities via optool
- 2024A&A...681A..82G: Stellar properties from average Class I values: 1.55 Msun, 2.1 Rsun, 3700 K
- 2020ApJ...904L...6A: Global gas-to-dust ratio of 100; small grains (up to 1 micron) hold 1% of dust mass; pure astrosilicate
- 2020ApJ...904L...6A: CO abundance 1e-4 per H above 20 K dust temperature and 1e-10 per H below
- 2016ApJ...819...82S: kappa_d(125 um)=1.875 m2/kg, beta=1.5, T_dust=30 K
- 2026A&A...706A.174A: [CO]/[H2] fixed to a fiducial Milky Way value (log = -4.0)
- 2021MNRAS.504..928P: Optically thin approximation (tau_nu << 1); dust absorption coefficient k(nu_rest) = 5.1 (nu_rest / 1.2 THz)^beta cm^2 g^-1; factor of 2 upward correction for …
- 2021MNRAS.504..928P: alpha_CO = 3.6 M_sun (K km s^-1 pc^2)^-1; excitation ladder r_31 = 0.42 ± 0.07, r_21 = 0.76 ± 0.09; Helium factor 1.36; Leroy et al. (2011) GDR relation; Genze…
- 2015ApJ...805...21C: gas-to-dust 100, CO freeze-out at 20 K, H2/12CO = 1e4, LTE, Keplerian
- 2013A&A...552L..10S: kappa=0.5 cm2/g (nu/230.6 GHz), gas-to-dust 100, Td=100 K, d=2.19 kpc
- 2017ApJ...851...98T: kappa(850um)=0.383 cm2/g, T_dust=40 K
- 2017ApJ...851...98T: Flat cosmology H0=70, OmegaM=0.3, OmegaL=0.7
- 2018ApJ...869..115S: T = 30 K, kappa = 0.01112 cm2/g, gas-to-dust 100, mu = 2.8, cylinder geometry, Q=0.5
- 2016ApJ...832..110C: global gas-to-dust ratio 100; Teff 3900 K, R* 2.5 Rsun, M* 1 Msun
- 2024ApJ...968...10F: Dust temperature 10 K
- 2024ApJ...968...10F: Gas-to-dust ratio 100
- 2021MNRAS.506.4175M: Optically thin dust emission
- 2021MNRAS.506.4175M: Distance D = 1.76 kpc
- 2021MNRAS.506.4175M: Dust opacity kappa_nu = 0.33 cm^2 g^-1 at 230 GHz
- 2021MNRAS.506.4175M: Dust temperature T_d = 42 K for MM1-MM4 and 50 K for MM5-MM8
- 2021MNRAS.506.4175M: Gas-to-dust mass ratio = 100
- 2024A&A...687A.299L: global gas-to-dust mass ratio 100
- 2024A&A...687A.299L: disk inclination 41 deg
- 2024A&A...687A.299L: distance 108.1 pc
- 2020A&A...633A.114S: kappa(890um)=2 cm2/g, Tdust=20 K
- 2020A&A...633A.114S: Gas-to-dust ratio 100 for total disk mass
- 2019ApJ...880...15K: T_dust = 25 K mass-weighted
- 2019ApJ...880...15K: beta = 1.8, constant gas-to-dust ratio
- 2024A&A...681A.110W: ΔMS-dependent templates account for different MS/SB dust grain temperatures
- 2024A&A...681A.110W: Gas-phase metallicities follow the adopted redshift- and stellar-mass-dependent relation
- 2022A&A...665L...7S: All ALMA-detected sources share the same SED shape as the integrated SED (GN20 template)
- 2022A&A...665L...7S: Optically thick dust emission in HPC1001.a could overestimate dust mass by a factor of two (included in uncertainty)
- 2022A&A...665L...7S: Gas-to-dust ratio M_gas = 100 * M_dust with 20% metallicity uncertainty
- 2012ApJ...761L..20R: Sigma ∝ r^-1; inclination 70 deg; gas-to-dust ratio 100
- 2014ApJ...793....1Y: kappa1.3mm=0.023 cm2/g, beta=1, Tdust 55-25 K from the model
- 2016PASJ...68..103F: Lbol ≈ LFIR
- 2019ApJ...874...89C: Td = 6.5 K, kappa1.3mm = 0.009 cm2/g, D = 135 pc
- 2016ApJ...831..101B: Same TW Hya UV field used for both systems; 8:2 astrosilicate:graphite
- 2024A&A...684L..12S: Optically thin dust emission
- 2024A&A...684L..12S: Distance 130 pc
- 2020ApJ...892..152H: Gas-to-dust ratio 100; mean molecular weight 2.8
- 2020ApJ...892..152H: Constant opacity and dust mass density across the wall
- 2025ApJ...995L..75C: gas self-gravity neglected
- 2025ApJ...995L..75C: gas-to-dust ratio 100 for disk masses
- 2021A&A...649A.122P: Optically thin emission for the dust mass
- ... 576 more

### Limitations the authors admit
- 2019ApJ...871..185L: Source catalogue edits are subjective
- 2019ApJ...871..185L: Thickness H(r) cannot be measured; assumption oversimplified
- 2018A&A...619A.161C: Emission only marginally optically thin so masses are lower limits; large uncertainties in opacity and gas surface density
- 2018A&A...619A.161C: Spectral index decrease may be due to optical thickness rather than grain growth
- 2025A&A...694A.295P: Sample is small
- 2025A&A...694A.295P: Gas mass estimates depend heavily on the earlier CO bandhead fits
- 2025A&A...694A.295P: Number of serendipitous sources too small to be conclusive
- 2020ApJ...904..181L: Cooler outer temperatures and missing flux beyond 2 arcsec can increase inferred outer masses and flatten the density profile.
- 2020ApJ...904..181L: Several spectral components are blended, uncertain or unidentified.
- 2020ApJ...904..181L: Inclination is not well constrained observationally.
- 2020ApJ...904..181L: M4 specific angular momentum and centrifugal barrier are unknown; 90 au was chosen arbitrarily.
- 2020ApJ...904..181L: Resolution prevents identification of central substructure, small clumps and a putative inner disc.
- 2020ApJ...904..181L: Mass estimates depend on uncertain temperature, dust opacity and variable flux; gas and dust may be thermally decoupled during the burst.
- 2020ApJ...904..181L: The simulated pseudo-disc is smaller than the observed structure; the simulation omits magnetic fields.
- 2020ApJ...904..181L: Temporal variation and chemical differentiation require higher-sensitivity confirmation.
- 2025A&A...693A.286S: Upper limits on IMTT CO fluxes do not constrain gas masses; most limits reach the grid maximum
- 2025A&A...693A.286S: Resolved-structure fraction lower than Herbig, attributed to lower spatial resolution; lack of deep observations
- 2025A&A...693A.286S: Sample biased towards high accretors and brightest disks
- 2025A&A...693A.286S: Dust masses may be underestimated (optical depth, opacity), seen as high gas-to-dust ratios
- 2023MNRAS.518.6092L: The inner disk (R < 20 AU) is optically thick even at 2.9 mm, so the grain size there cannot be constrained by the spectral index and is fixed to 10 cm.
- 2023MNRAS.518.6092L: Fluctuations in the retrieved grain size profile occur on spatial scales smaller than the beam size (~20 AU), requiring future higher-resolution observations to confirm.
- 2023MNRAS.518.6092L: The amplitude and shape of the grain size discontinuity at the gap-ring boundary depend on the assumed dust opacity model.
- 2016ApJ...816...37V: Inclination and peak rotation velocity cannot be independently determined at current resolution
- 2016ApJ...816...37V: FIR/TIR luminosities strongly model dependent; more photometry needed
- 2025ApJ...993L..40S: Small CO-selected sample with uncertain representativeness
- 2025ApJ...993L..40S: UV+IR SFRs may overestimate true SFRs because old stars heat dust.
- 2025ApJ...993L..40S: Comparison-sample selection criteria vary and are not scrutinized in detail.
- 2025ApJ...993L..40S: αCO dominates CO excitation uncertainty; carbon abundance dominates reasonable [CI] excitation uncertainty.
- 2021A&A...652A..66P: Composite CO SLED fit has more free parameters than data points, so best-fit values are degenerate
- 2021A&A...652A..66P: T_dust cannot be constrained by the dust fit and follows the prior
- 2021A&A...652A..66P: Poor SED coverage gives only tentative dust constraints for PJ308-21
- 2021A&A...652A..66P: CO SLED errors are statistical only; the gas-to-dust ratio systematic is ignored
- 2021A&A...652A..66P: CLOUDY models are simple single-cloud models that cannot give a realistic picture of the ISM
- 2015A&A...583A..66H: Dust mass method has significant uncertainties; ages uncertain; binarity unconfirmed
- 2014ApJ...796....1T: Missing flux and outflow complicate other lines near systemic velocity; temperatures in hydrodynamics (isothermal 13.5 K) and radiative transfer (power law) are inconsistent.
- 2017ApJ...835..213P: ALMA may resolve out up to ~50% of 333 GHz flux
- 2017ApJ...835..213P: LVG solutions under-constrained
- 2018A&A...614A.113H: Parameters tuned visually; no statement on fit quality
- 2018A&A...614A.113H: Insufficient spatial resolution limits kinematics
- 2014ApJ...796...84R: Spatial resolution insufficient to resolve structure; higher resolution needed
- 2014ApJ...796...84R: Photometric uncertainties near the SED peak are large
- 2024MNRAS.527.3559P: Gas surface density is a rough estimate without uncertainties
- 2024MNRAS.527.3559P: Disc extent beyond 90 au uncertain because of low SNR
- 2024MNRAS.527.3559P: Inner disc poorly constrained by the low-resolution, nearly edge-on ALMA data
- 2018ApJ...869...10M: Low S/N ALMA data; belt width not conclusively resolved
- 2018ApJ...869...10M: Dust opacity uncertainty gives factor 3-5 in mass
- 2018ApJ...869...10M: NICMOS/SPHERE discrepancy possibly from non-Gaussian noise
- 2018MNRAS.479.1154B: J2315 SED and line ratios use blended flux from unresolved merger components
- 2018MNRAS.479.1154B: 3D-PDR lacks X-ray and mechanical heating
- 2021A&A...645A..49G: Some extra-nuclear contribution to the lowest-lying H2O lines is not excluded.
- 2021A&A...645A..49G: Core lines are saturated; core optical depth, abundance, mass, and size are uncertain.
- 2021A&A...645A..49G: The three-component geometry is schematic with sharp transitions.
- 2021A&A...645A..49G: Other molecular species favor disk tau_100 approximately 1.5–3, potentially higher than the fiducial H2O value.
- 2021A&A...645A..49G: Limited spatial resolution and beam smearing prevent more detailed nuclear velocity modeling.
- 2021A&A...645A..49G: High turbulence masks rotation and possible CO inflow at radii <= 1 arcsec.
- 2021A&A...645A..49G: Flow lines rely on four radial samples and interpolation and are not realistic gas orbits.
- 2021A&A...645A..49G: CO inflow rates are not corrected for feedback from the nuclear region.
- 2021A&A...645A..49G: OH119 profiles have significant modeling discrepancies; OH inflow rate is uncertain.
- 2021A&A...655A..98A: Dust masses may be lower limits because cooler dust may be missed
- 2021A&A...655A..98A: Systematic uncertainty of about 25% in kappa is not propagated into the dust mass
- 2021A&A...655A..98A: The fraction of massive stars that become LBVs is unconstrained and dominates the yield uncertainty
- 2024MNRAS.535..729P: Only one galaxy (Sextans A) is probed in the low-metallicity regime, and CO is not detected in it.
- 2024MNRAS.535..729P: MAGPHYS assumes a fixed dust emissivity index, which can introduce systematic biases in M_dust without longer-wavelength data.
- 2024MNRAS.535..729P: BEDE is a one-zone chemical and dust evolution model, which may not capture sub-galactic environmental variations (bars, spiral arms, local inflows/outflows) and suffers from parameter degeneracies (…
- 2024A&A...681A..17D: Small number statistics and sample bias towards the brightest/highest mass-loss RSGs in RSGC1 (only 5 of 14 RSGs detected in CO(2-1); Band 9 CO(6-5) was not observed, leaving only a single CO transit…
- 2024A&A...681A..17D: ISM CO contamination affects the blue-shifted velocities of the line profiles, and total CO envelope sizes are sensitivity-limited lower limits.
- 2024A&A...681A..17D: Terminal wind velocities derived from line widths can be sensitivity-limited lower limits.
- 2021A&A...654A..90L: The ALMA sample is biased towards heavily X-ray obscured (log N_H > 22), optical Type 2 AGN, and the upper end of the SFR distribution of the SUPER parent sample because of the FIR pre-selection.
- 2021A&A...654A..90L: Two of the eight targets (cid_1057 and cid_451) have low ALMA peak S/N (3.6 and 5.9), which is insufficient for reliable size measurements and spatially resolved analysis.
- 2021A&A...654A..90L: High-resolution ALMA observations (~0.2") may resolve out diffuse, extended FIR emission.
- 2021A&A...654A..90L: Using monochromatic 260 um continuum to map obscured SFR assumes negligible spatial variation in dust temperature and emissivity index beta, and lacks radiative transfer modelling of host-scale diffu…
- 2021A&A...654A..90L: SINFONI observations lack the S/N and spatial resolution for spatially resolved BPT diagnostics or Balmer decrement extinction corrections, and AO observations may miss extended line flux.
- 2021A&A...654A..90L: The FIR vs non-AGN size comparison is limited by small sample size and heterogeneity across literature surveys.
- 2021A&A...654A..90L: Star formation suppression occurring on spatial scales smaller than the ~2 kpc resolution or on different timescales cannot be ruled out.
- 2020MNRAS.498.1319M: Planet mass assumes the gap is empty at its centre; a shallower, broader gap would change the inferred width and mass
- 2020MNRAS.498.1319M: Frankenstein profiles lack a primary beam correction
- 2020MNRAS.498.1319M: Lower S/N makes gap width and depth comparison with other discs difficult
- 2020MNRAS.498.1319M: Derived planet masses must be taken with caution since the gap may be inherited or the planet may have migrated
- 2024ApJ...977..190X: J2054-0005 CO (8-7) and (10-9) linewidths have large fitting uncertainties.
- 2024ApJ...977..190X: J0129-0035 lacks Herschel data near the dust peak; temperature and derived quantities depend strongly on assumptions.
- 2024ApJ...977..190X: J2054-0005 torus/dust decomposition has degeneracy and uncertainty.
- 2024ApJ...977..190X: Available observations cannot simultaneously constrain all five PDR+XDR parameters.
- 2024ApJ...977..190X: Higher-J CO observations are needed to distinguish XDR from dense PDR excitation.
- 2024ApJ...977..190X: Comparison statistics require a larger sample with both CO and X-ray measurements.
- 2015ApJ...800...70S: Single dust temperature adopted; dust temperature not derivable from the data; masses uncertain by factor of 2.
- 2015ApJ...800...70S: Only ~15% of single-dish flux recovered in NGC 6240.
- 2018MNRAS.475..448T: Distance mismatch between GRS 1915+105 and IRAS source; jet power assumes constant power and density
- 2018MNRAS.475..448T: ALMA continuum lacks single-dish data so flux is underestimated
- 2020ApJ...891..164S: Infall not detected because no optically thick tracer; NH2 includes low-temperature components
- 2026ApJ...998..277M: Spectral resolution (0.86-1.1 km s^-1) is insufficient to clearly resolve hyperfine components of CN and CCH or potential multiple velocity components in the cores.
- 2026ApJ...998..277M: Some CH3OH transitions (especially 1_1-0_0 A+) and the H2CO transition are moderately to highly optically thick according to RADEX, making the H2CO column density a lower limit.
- 2026ApJ...998..277M: Derived molecular abundances can be affected by spatial filtering, excitation temperature assumptions, optical depth, and beam filling factors, while only dust temperature uncertainty (10-20 K) is fo…
- 2019MNRAS.483..806R: CH3OH and H2CO column densities are lower limits because lines are optically thick
- 2019MNRAS.483..806R: HCO Tex could not be determined since all four lines share Eup of 4 K
- 2019A&A...626A.126A: Lowest ALMA contour has low significance; only a third of observations completed; deeper data needed
- 2013ApJ...777...92S: 1.3 mm data S/N modest with sparse uv coverage; large fraction of CO(1-0) absorption resolved out
- 2021NatAs...5..586Y: Extended dust structures near the center in Bands 4 and 6 had too low SNR to be confirmed or included in the analysis.
- 2021NatAs...5..586Y: Larger pebbles (a >= 1 cm or dm-sized) emit less effectively at ALMA wavelengths and are not well constrained, making the dust mass loss rate and dust-to-gas ratio lower limits.
- 2021NatAs...5..586Y: CO rotational temperature is poorly constrained by the two transitions (1-sigma range 13-181 K), and spectral resolution was insufficient to measure the CO outflow velocity directly.
- 2021NatAs...5..586Y: Dust particles were assumed to be spherical because no accurate light-scattering solution exists for mm-sized irregular particles.
- 2021NatAs...5..586Y: Optical Af rho-based dust mass loss rates are only order-of-magnitude estimates because optical data preferentially probe micron-sized dust.
- 2025A&A...694A..86Y: The sample is not complete; only the most robust candidates were reported
- 2025A&A...694A..86Y: Without dust emission the H2 column density is unconstrained, so abundances are lower limits
- 2025A&A...694A..86Y: The nature and origin of the filaments need further multi-wavelength work
- 2025A&A...694A..86Y: Dust emission could be undetectable because of missing flux
- 2015MNRAS.449..715W: Mass estimates uncertain due to cloud boundary definition and a factor ~2 systematics; gas temperature measured only for G0.253
- 2020ApJ...894L..14L: Dust temperature at 2000 AU unknown, strongly affects masses
- 2020ApJ...894L..14L: Cannot tell whether cores are prestellar or protostellar
- 2013ApJ...762L..21M: Spectral index of central peak poorly constrained; inner belt interpretation needs higher resolution
- 2019MNRAS.488.1005P: System ages uncertain by ~50%
- 2019MNRAS.488.1005P: Gas (CO) not analysed
- 2021A&A...650A.153D: Chandra source counts do not constrain the ICM temperature distribution.
- 2021A&A...650A.153D: Most X-ray hardness structures have low significance.
- 2021A&A...650A.153D: Radio resolution, sparse sampling, and weak high-frequency detections prevent a detailed spectral-index map.
- 2021A&A...650A.153D: SZ masses may be biased by nonhydrostatic gas and mass–inner-slope degeneracy.
- 2021A&A...650A.153D: Limited spectral coverage leaves thermal and kinetic SZ strongly degenerate.
- 2021A&A...650A.153D: Interferometric filtering favors compact, low-mass pressure models and limits extrapolation to large scales.
- 2021A&A...650A.153D: Weak-lensing positional precision limits confidence in the southern gas–mass offset.
- 2021A&A...650A.153D: Dust mass and temperature require better high-frequency observations.
- 2025ApJ...986L..22R: Two-component model is a simplification of the dual-jet geometry; March 17 S/N lower

### Settings cards flag as needed but not stated
- casa version: 46
- self-calibration solution intervals and number of iterations: 32
- line-free channels and continuum subtraction method: 21
- self-calibration solution intervals: 21
- casa version and pipeline version: 20
- line-free channels used for continuum: 18
- line-free channels used for continuum subtraction: 15
- line-free channel ranges for continuum: 15
- flux scale uncertainty: 14
- self-calibration solution intervals and number of rounds: 12
- image size and cell size: 12
- line-free channels for continuum subtraction: 12
- primary beam correction details: 12
- line-free channels for uvcontsub: 9
- flux calibrator and flux scale uncertainty: 9
- moment map clipping thresholds: 9
- continuum subtraction and line-free channels: 8
- line-free channel selection: 8
- flux calibration uncertainty: 8
- line-free channel selection for continuum: 8
- primary-beam correction details: 8
- clean threshold, masks, cell and image size: 8
- casa version and whether the pipeline or manual calibration was used: 8
- casa version used for calibration and imaging: 7
- self-calibration, if any: 7
- flux calibrator and flux-scale uncertainty: 7
- line-free channels used for uvcontsub: 6
- cell size and image size: 6
- continuum subtraction method and line-free channels: 6
- line-free channel ranges for continuum subtraction: 6
- clean threshold, masks, image size and cell size: 6
- self-calibration solution intervals and reference antenna: 6
- source coordinates: 6
- line-free channel ranges for continuum and uvcontsub: 5
- uvmodelfit starting parameters: 5
- image size, cell size, clean threshold and masks: 5
- casa version used: 5
- self-calibration solution interval and reference antenna: 5
- self-calibration usage: 5
- line-free channel ranges used for continuum: 5

## Paper excerpts (40 of 915, chosen for detail and spread over fields/years)

### 2019ApJ...871..185L: Investigating Fragmentation of Gas Structures in OB Cluster-forming Molecular Clump G33.92+0.11 with 1000 au Resolution Observations of ALMA (2019; star_formation, milky_way_ism; observational_alma_primary)
- question: How do gas structures in the OB cluster-forming clump G33.92+0.11 fragment into YSO candidates, and is the fragmentation consistent with Toomre instability and Jeans lengths?
- step 3: Toomre Q
  - method: Enclosed gas mass from 225 GHz flux, assumed T(r); centrifugal balance; Q = kappa cs/(pi G Sigma) [Toomre instability: "We then estimate the enclosed gas mass in radius $r$ based on the observed 225 GHz flux and an assumed gas temperature profile $T(r)$"]
  - parameter: 0 or 30 Msun central stellar mass [Toomre instability: "(2) there is a total of 30 $M_{\odot}$ of stellar mass embedded at the center of the system."]
  - assumption: Constant 30 K fiducial, or radial profile; optically thin; gas-to-dust 100; flattened rotating [Toomre instability: "our fiducial analysis assumes a constant 30 K temperature across the entire source."]
  - validation: CH3CN temperatures broadly consistent with profile [Toomre instability: "These measurements are in general consistent with the temperature model described by Equation"]
- step 6: Compare linking lengths with Jeans lengths
  - method: Convert Tb at link midpoints to density with thickness profile H(r); compute Jeans lengths; compare with link lengths and regress log sqrt(Tb) vs log l [Spatial separations of young stellar ob…: "we convert $T_{b}^{\mbox{\scriptsize 225 GHz}}$ to gas volume density $\rho$ based on the assumed radial characteristic thickness profile $H(r)$"]
  - parameter: H(r)=0.05+0.3 sqrt(r/0.3) pc; T=30 K [Spatial separations of young stellar ob…: "H(r) [pc] = 0.05 + 0.3\times\sqrt{r [pc] / 0.3}."]
  - assumption: kappa=0.6 cm2/g, gas-to-dust 100 [Spatial separations of young stellar ob…: "assuming $\kappa_{\mbox{\scriptsize 225 GHz}}=$0.6 cm$^{2}$ g$^{-1}$ and gas to dust mass ratio 100"]
  - fitting: Linear regression in log-log, upper limits excluded [Spatial separations of young stellar ob…: "A linear regression of $\log{(\sqrt{T_{b}^{\mbox{\scriptsize 225 GHz}}})}$ and $\log{(\ell)}$ (without including upper limits)"]
  - validation: Alternative T and H(r) and alternative catalogues [Spatial separations of young stellar ob…: "for the catalogue directly given by `deodrogram` without any further edits, gives slopes of -0.54 and -0.52, respectively."]
- result: Regression slope log sqrt(Tb) vs log l, final catalogue = -0.68 ± not stated dimensionless [Spatial separations of young stellar ob…: "gives a slope of -0.68."]
- limitation (authors): Source catalogue edits are subjective [Identifying candidates of young stellar…: "Our edits to the identified source catalogue is subjective to some extent."]
- limitation (authors): Thickness H(r) cannot be measured; assumption oversimplified [Spatial separations of young stellar ob…: "This assumption of the thickness of gas structure is likely yet oversimplified."]
- not stated (card): Calibrator names and flux scale; Line-free channels used for uvcontsub; clean threshold, masks, niter; Weights used to combine ALMA and ACA data; Electron temperature/line width used for the H30alpha free-free model; Details of the CH3CN temperature fit; Dendrogram settings beyond thresholds, and exact manual source edits

### 2018A&A...619A.161C: Evidence for a massive dust-trapping vortex connected to spirals. Multi-wavelength analysis of the HD 135344B protoplanetary disk (2018; protoplanetary_disks; observational_alma_primary)
- question: What is the nature of the asymmetric mm-dust structure in the HD 135344B disk, and does it (a vortex) explain the scattered-light spirals without an outer planet?
- step 3: Estimate crescent and total dust mass and optical depth
  - method: Optically thin M = F d^2/(kappa B(T)); brightness temperature gives tau; surface density from tau/kappa [4.1 Dust mass: "Under the assumption of optically thin emission it is possible to convert the observed flux into dust mass."]
  - parameter: d = 136 pc, T_dust = 15 K, kappa = 10 cm2/g at 1000 GHz, beta = 1 [4.1 Dust mass: "where the distance $d=136\,\rm pc$, the dust temperature $T_{\rm dust}$ at the location of the asymmetry (i.e. $\sim80$ au) is assumed to be 15 K"]
  - assumption: Optically thin emission; T_dust = 15 K; kappa with beta=1 [4.1 Dust mass: "the dust grain opacity $\kappa_\nu$ is taken as $10\,\rm cm^2 g^{-1}$ at $1000\,\rm GHz$"]
  - validation: Tested with T_dust higher by factor 1.5 (tau ~0.4) [4.1 Dust mass: "The crescent remains only marginally optically thin even assuming $T_{\rm dust}$ higher by a factor of 1.5, with $\tau_\nu\sim 0.4$."]
- step 5: Measure azimuthal peak shift and width versus wavelength; infer gas surface density and gas-to-dust ratio
  - method: Compare fitted crescent theta_V and azimuthal widths across bands; invert Stokes number relation assuming St~1 to get Sigma_gas [4.3 Peak shift: "we can therefore invert Eq. [\[eq:st\]](#eq:st) and obtain an estimate of the gas surface density at the vortex location of $\Sigma_{\rm gas}\approx1\,\rm g\,cm^{-2}$"]
  - parameter: grain size ~3 x lambda [4.3 Peak shift: "grain size $\sim3\times\lambda$ (cite: 2006ApJ...636.1114D)"]
  - assumption: rho_pc = 1 g/cm3, St near unity [4.3 Peak shift: "Assuming a typical value of $\rho_{\rm pc}=1\rm \, g\, cm^{-3}$"]
  - validation: Consistent with Sigma_gas from CO isotopologue modelling [4.3 Peak shift: "This gas surface density is consistent with that obtained by (cite: vdm2016_isot) by modelling the emission from $^{13}$CO and C$^{18}$O."]
- step 6: Estimate vortex total mass and compare with planet scenarios
  - method: Dust mass ~50 Mearth times gas-to-dust ratio 1 or 10; gap-planet mass from gap width relation [5.2 Spirals launched by the vortex: "Assuming a value of 10 (cite: 2017ApJ...835..118M; 2017ApJ...850..115S), the total mass for the vortex is $M_{\rm vortex}\approx1.7\,M_{\rm Jupiter}$."]
  - parameter: gap width ~20 au at ~68 au, alpha = 1e-3 [5.1 Spirals launched by a planet: "a standard viscosity parameter $\alpha = 10^{-3}$"]
- result: Azimuthal shift of peak between Band 9 and Band 3 = ~50 ± not stated deg [4.3 Peak shift: "we observe a shift of $\sim50^\circ$ between the 1.5 mm grains (traced in Band 9) and 9 mm grains (traced in Band 3)"]
- result: Crescent dust mass Band 4 / Band 3 = 44 / 52 ± not stated Earth masses [4.1 Dust mass: "The calculated dust masses are $44\,\rm M_{\oplus}$ and $52\,\rm M_{\oplus}$ in Band 4 and Band 3, respectively."]
- result: Optical depth of crescent = ~0.5-0.6 ± not stated dimensionless [4.1 Dust mass: "gives an optical thickness $\tau_\nu$ of $\sim 0.5-0.6$ at 108 and 155 GHz"]
- result: Total flux density Band 3 / Band 4 = ~20.0 / ~42.7 ± not stated mJy [4.1 Dust mass: "The total flux densities in Band 3 and Band 4 are $\sim20.0\,\rm mJy$ and ${\sim42.7\,\rm mJy}$, respectively."]
- result: Central unresolved source flux (Band 4) = ~85 ± not stated uJy [4.1 Dust mass: "has a flux density of $\sim85\,\rm\mu Jy$"]
- result: Gas surface density at vortex = ~1 ± not stated g cm-2 [4.3 Peak shift: "$\Sigma_{\rm gas}\approx1\,\rm g\,cm^{-2}$"]
- result: Vortex total mass (gas-to-dust 1) = at least 0.3 ± not stated Jupiter masses [5.2 Spirals launched by the vortex: "gives a total vortex mass of at least $0.3\,M_{\rm Jupiter}$"]
- result: Vortex total mass (gas-to-dust 10) = 1.7 ± not stated Jupiter masses [5.2 Spirals launched by the vortex: "the total mass for the vortex is $M_{\rm vortex}\approx1.7\,M_{\rm Jupiter}$"]
- result: Gap-carving planet mass = ~0.2 ± not stated Jupiter masses [5.1 Spirals launched by a planet: "the derived mass for the gap-carving planet is only $\sim0.2\,\rm M_{\rm Jupiter}$"]
- limitation (authors): Emission only marginally optically thin so masses are lower limits; large uncertainties in opacity and gas surface density [4.1 Dust mass: "These numbers should be regarded as lower limits."]
- limitation (authors): Spectral index decrease may be due to optical thickness rather than grain growth [4.2 Spectral index distribution: "but can also be due to high optical thickness, or to a combination of both effects"]
- not stated (card): Self-calibration solution intervals, number of rounds and reference antenna; Line-free channels / continuum selection and any continuum subtraction for Band 3; CASA version and pipeline version; Cell size, image size, mask, clean threshold and number of iterations; MCMC priors and bounds, convergence criteria; meaning of '24000 likelihoods' vs steps; uv-weights and any rescaling used in GALARIO f…

### 2025A&A...694A.295P: ALMA detections of circumstellar disks in the giant H II region M17: Probing the intermediate- to high-mass pre-main-sequence population (2025; star_formation, protoplanetary_disks; observational_alma_primary)
- question: Do four intermediate- to high-mass (4-10 Msun) pre-main-sequence stars in M17 have detectable mm emission, and what are the dust and gas masses and origin of the emission (disk dust vs free-free)?
- step 5: Dust masses from optically thin continuum flux
  - method: M_dust = F d^2 / (kappa B(T_dust)) per band, with power-law opacity [3.3 Dust mass estimation: optically thi…: "Under this approximation the dust mass in the disk is given by (cite: beckwith1990):"]
  - parameter: kappa = kappa0 (nu/nu0)^beta with kappa0=10 cm2/g, nu0=1000 GHz, beta=1; T_dust = 25 (L/Lsun)^1/4 K (110-246 K); T_dust=150 K for serendipitous sources; d = 1.7 kpc [3.3 Dust mass estimation: optically thi…: "resulting in dust temperatures between $110~\rm K$ and $246~\rm K$ for the objects in"] [3.3 Dust mass estimation: optically thi…: "For the serendipitous detections, for which we do not know the stellar luminosities, we adopt $T_{\rm dust} = 150~\rm K$."]
  - assumption: Optically thin, isothermal dust emission; flux purely dust (not valid for free-free dominated B331, B268) [3.3 Dust mass estimation: optically thi…: "assuming optically thin dust emission from an isothermal disk"]
  - validation: Compared with ProDiMo and thin-disk estimates [4.2 Fit results and disk mass estimates: "lead to similar dust masses, that are at most an order of magnitude higher than the previous two estimates"]
- step 6: Compare with a ProDiMo model-grid of SEDs
  - method: Fit grid SEDs to photometry plus ALMA points for each target after swapping the stellar continuum [3.4 Disk mass estimation: ProDiMo model…: "We fitted the model SEDs to the available photometry and ALMA points for each of the four targets in the sample."]
  - software: ProDiMo
  - parameter: Grid 10x10x5: total mass 5e-4 to 5e-1 Msun, outer radius 20-500 au, inclination 15-75 deg; inner radius 11.2 au [3.4 Disk mass estimation: ProDiMo model…: "The grid consists of $10 \times 10 \times 5$ models with, respectively, total disk masses ranging from $5\times10^{-4}$ to $5\times10^{-1}$ $M_{\odot}$,"] [3.4 Disk mass estimation: ProDiMo model…: "outer radii from $20~\rm au$ to $500~\rm au$, and inclinations from $15^{\circ}$ to $75^{\circ}$"]
  - assumption: DIANA-standard setup, gas-to-dust 100, central object B331 [3.4 Disk mass estimation: ProDiMo model…: "In these models we used the DIANA-standard model setup with a gas to dust mass ratio of 100 (cite: woitke2016)."]
  - fitting: Grid SEDs fitted to data (fit metric not stated) [3.4 Disk mass estimation: ProDiMo model…: "We fitted the model SEDs to the available photometry and ALMA points for each of the four targets in the sample."]
  - validation: Grid cannot fit NIR/MIR and ALMA simultaneously, so used only as a reference [3.4 Disk mass estimation: ProDiMo model…: "Because the grid models are unable to fit the near- to mid-infrared photometry simultaneously with the ALMA points, and also provide little constraint on the disk mass, we use another disk model"]
- step 7: Gas/dust masses from extrapolation of CO bandhead results and thin-disk SED fits
  - method: (a) Extrapolate inner-disk CO column density with q=-1.5 out to R_out = half beam to get gas and dust mass; (b) fit SEDs with adapted P23 model with logistic dust-to-gas ratio [3.5.2 Extrapolation and fitting: "using the power law slope, $q = -1.5$, from the same fits"] [3.5.2 Extrapolation and fitting: "we fit an SED to the photometry and ALMA flux points using the P23 model with the described adaptations"]
  - software: P23 model, SciPy curve_fit, Kurucz model
  - parameter: Free: Sigma_i, q, r_turn, beta; fixed: R_i,dust, R_out, inclination, temperature exponent p=-1 [3.5.2 Extrapolation and fitting: "a temperature power law exponent which we fix to $p = -1$ based on exploratory fitting"] [3.5.2 Extrapolation and fitting: "We fit the initial column density $\Sigma_i$ (at $(R_i)_{\rm dust}$), power law exponent $q$, and the logistic function parameters $r_{\rm turn}$ and $\beta$"]
  - parameter: R_out set to half the beam size of the image; dust inner radius at 1500 K sublimation temperature [3.5.2 Extrapolation and fitting: "The outer radius, $R_{\rm out}$, is set to half the beam size of the image for each object"] [3.5.2 Extrapolation and fitting: "is defined as the point where the dust temperature reaches the dust sublimation temperature $\rm 1500~K$"]
  - assumption: Ossenkopf & Henning opacities, n_H=1e8 cm-3, no ice mantles; dust-to-gas limit 1e-2 [3.5.1 Model description: "we adopt $n_{\rm H}=10^8~\rm cm^{-3}$ and grains without ice mantles"] [3.5.2 Extrapolation and fitting: "we assume a constant dust-to-gas mass ratio $M_{\rm d}/M_{\rm g} = 10^{-2}$"]
  - fitting: SciPy curve_fit non-linear least squares with parameter bounds; weights = inverse flux errors; parameter errors from covariance matrix; no priors or sampler [3.5.2 Extrapolation and fitting: "from the SciPy module (cite: virtanen2020) is used to fit the data."] [3.5.2 Extrapolation and fitting: "The inverse of the errors on the flux are treated as weights and the errors on the fit parameters are calculated from the covariance matrix returned by the routine."]
  - validation: Best-fit SEDs compared with data; best fit parameters often at bounds; B331 and B268 results bracketed as unreliable [4.2 Fit results and disk mass estimates: "The results for B331 and B268 are placed between brackets, because the fitted ALMA Band 7 flux point is either likely dominated by free-free emission (B331) or an upper limit (B268)."]
- step 8: Compare disk dust masses with other populations
  - method: Compare Band 7 based dust masses with Lupus, Upper Sco, Herbig and ONC samples versus stellar mass, age, luminosity, radius; mean values and normalised age [5.2.1 Low-mass star forming regions and…: "because of the (possible) free-free contamination discussed earlier we use the (upper limits on the) dust masses based on the Band 7 flux."]
  - assumption: Literature dust masses use Eq. for Mdust, sometimes with different dust temperature assumptions [5.2.1 Low-mass star forming regions and…: "be it sometimes with different assumptions on the dust temperature than in this study"]
- result: Dust temperatures adopted for targets = 110-246 ± not stated K [3.3 Dust mass estimation: optically thi…: "resulting in dust temperatures between $110~\rm K$ and $246~\rm K$ for the objects in"]
- result: Dust mass B275, Band 6 and Band 7 = B6 2.2; B7 1.3 ± 0.2 (B6); 0.1 (B7) Mearth [Flux table: "$2.2 \pm 0.2$"]
- result: Dust mass B331 (free-free dominated, upper limit in practice), Band 6 and Band 7 = B6 8.1; B7 2.9 ± 0.8 (B6); 0.3 (B7) Mearth [Flux table: "$8.1 \pm 0.8$"]
- result: Dust mass B243, Band 6 and Band 7 = B6 2.0; B7 1.8 ± 0.3 (B6); 0.2 (B7) Mearth [Flux table: "$2.0\pm 0.3$"]
- result: Dust mass B268 (free-free dominated), Band 6 and Band 7 = B6 1.6; B7 < 0.81 ± 0.4 (B6) Mearth [Flux table: "$1.6 \pm 0.4$"]
- result: Best-fit ProDiMo total disk mass (all four targets; lowest in grid) = 5e-4 ± not stated Msun [3.4 Disk mass estimation: ProDiMo model…: "The best fit ProDiMo models are all the same, with parameters $M_{\rm tot} =5 \times 10^{-4}$ $M_{\odot}$ (lowest in grid)"]
- result: Best-fit ProDiMo outer radius = 233 ± not stated au [3.4 Disk mass estimation: ProDiMo model…: "outer radius $233~ \rm au$"]
- result: B275 extrapolated gas mass (CO bandhead, q=-1.5, D/G=1e-2) = 1.4e-4 ± +10/-1.2 (x1e-4) Msun [Disk mass table: "$1.4^{+10}_{-1.2}\times 10^{-4}$"]
- result: B243 extrapolated gas mass = 1.3e-4 ± +18/-1.2 (x1e-4) Msun [Disk mass table: "$1.3^{+18}_{-1.2}\times 10^{-4}$"]
- result: B275 thin-disk fit gas mass = 1.7e-3 ± +1.1/-0.9 (x1e-3) Msun [Disk mass table: "$1.7^{+1.1}_{-0.9}\times 10^{-3}$"]
- result: B275 thin-disk fit dust mass = 1.0 ± +0.5/-0.5 Mearth [Disk mass table: "$1.0^{+0.5}_{-0.5}$"]
- result: B243 thin-disk fit gas mass (upper limit on lower side) = 6.0e-4 ± +12 (x1e-4), lower limit marked as downward arrow Msun [Disk mass table: "$6.0^{+12}_{\downarrow}\times 10^{-4}$"]
- result: B243 thin-disk fit dust mass = 8.4e-1 ± +16 (x1e-1), lower side marked as downward arrow Mearth [Disk mass table: "$8.4^{+16}_{\downarrow}\times 10^{-1}$"]
- result: Mean dust mass of the M17 sample (and its standard deviation) = 1.7 ± sigma 0.82 Mearth [Table 6: "| M17 | 1.7 | 0.82 | 6.5 | 2.3 | 0.6$\pm$0.3 |"]
- limitation (authors): Sample is small [5.2.1 Low-mass star forming regions and…: "Compared to the other samples, our sample is small."]
- limitation (authors): Gas mass estimates depend heavily on the earlier CO bandhead fits [4.2 Fit results and disk mass estimates: "Of course, this does not change the fact that the estimation heavily relies on the adopted results from the CO bandhead fitting."]
- limitation (authors): Number of serendipitous sources too small to be conclusive [5.3 Serendipitous discovery of sources: "The number of sources is too small to be conclusive"]
- not stated (card): Imaging task and parameters (tclean/deconvolver, cell size, image size, niter, threshold, masks) and which ALMA products were used as starting point; Exact line-free channel ranges used for continuum averaging in each spectral window; Flux, bandpass and phase calibrators and whether archive-delivered products were re-run or used as is; imfit region/box, initial guesses and whether peak or integra…

### 2020ApJ...904..181L: ALMA View of the Infalling Envelope around a Massive Protostar in S255IR SMA1 (2020; star_formation, astrochemistry; observational_alma_primary)
- question: Characterize the gas around S255IR NIRS3/SMA1 and distinguish a Keplerian disc from a rotating infalling envelope.
- step 2: Measure continuum flux and derive gas column density and mass
  - method: Convert peak continuum intensity using Equation A.26 of (cite: Kauffmann08); integrate circular apertures and estimate enclosed masses and mean density. [Dust continuum, gas column density and …: "we translate this peak intensity $F^{\mbox{beam}}_{\nu}$ to a gas column density $N_{\mbox{\tiny H$_2$}}$ of 9.75 $\times$ 10$^{24}$ cm$^{-2}$ based on Equation A.26 in (cite: Kauffmann08)"] [Dust continuum, gas column density and …: "The integrated fluxes within larger circular apertures with diameters of 0.5$''$ ($\sim$ 900 au), 1.0$''$ ($\sim$ 1800 au), and 1.5$''$ ($\sim$ 2700 au) are 0.613 Jy, 0.932 Jy, and 1.08 Jy, respectively."]
  - parameter: Beam size 0.14 arcsec; molecular weight per hydrogen molecule 2.8 [Dust continuum, gas column density and …: "the beam size of 0.14$''$, $\mu_{\mbox{\tiny{H2}}}$ is the molecular weight per hydrogen molecule of 2.8"]
  - parameter: Circular aperture diameters: 0.5, 1.0 and 1.5 arcsec [Dust continuum, gas column density and …: "The integrated fluxes within larger circular apertures with diameters of 0.5$''$ ($\sim$ 900 au), 1.0$''$ ($\sim$ 1800 au), and 1.5$''$ ($\sim$ 2700 au) are 0.613 Jy, 0.932 Jy, and 1.08 Jy, respectively."]
  - assumption: Dust temperature 300 K; mostly optically thin continuum at 0.14 arcsec [Dust continuum, gas column density and …: "With the assumption of a dust temperature of 300 K"] [Dust continuum, gas column density and …: "the dust continuum emission, though with a non-negligible opacity, is mostly optically thin at this 0.14$''$ scale."]
  - assumption: κν = κ250 μm (250 μm/λ)^β; κ250 μm = 0.1 cm^2 g^-1; β = 1.8; κν = 0.010 cm^2 g^-1 [Dust continuum, gas column density and …: "Here, we adopt $\kappa_{\nu}$ of 0.010 cm$^{2}$g$^{-1}$"] [Dust continuum, gas column density and …: "$\kappa_{\nu} = \kappa_{250 \mu m} ({250 \mu m}/{\lambda})^{\beta}$"]
  - assumption: Gas-to-dust mass ratio 100; distance 1.78 kpc [Dust continuum, gas column density and …: "implicitly a gas-to-dust mass ratio of 100."] [Dust continuum, gas column density and …: "When the source distance of 1.78 kpc is taken into account"]
  - validation: Continuum brightness temperature 121 K compared with gas temperature above 300 K to assess continuum opacity [Dust continuum, gas column density and …: "the gas temperature is at a level above 300 K toward the peak"] [Dust continuum, gas column density and …: "the peak continuum intensity of 0.237 Jy Beam$^{-1}$"]
- step 7: Test rotating-disc and infalling-envelope models
  - method: Generate SPARX molecular-line cubes for M1–M4, convolve with CASA imsmooth, extract CASA impv diagrams and compare with observed CH3CN P-V structure. [Radiative transfer modeling: "The software package produces image cubes through radiative transfer calculations of molecular line radiation with input physical models."] [Radiative transfer modeling: "We further convolve these synthetic image cubes output by SPARX with the observing resolution (0.14$''$) using the *"imsmooth"* command in CASA and generate the model P-V diagrams with the CASA *"impv"* task."]
  - software: SPARX, CASA, imsmooth, impv
  - parameter: M1: pure Keplerian, 20 M☉, 25 degree; M2: pure Keplerian, 4.76 M☉, 60 degree; Table 1 rounds the latter mass to 4.8 M☉ [Radiative transfer modeling: "In toy Model 1 (M1) and Model 2 (M2), we assumed the emissions are from gas following pure Keplerian rotation."] [Radiative transfer modeling: "their central YSO masses and inclination angles being 20 M$_\odot$and 4.76 M$_\odot$, and 25 degree and 60 degree, respectively."]
  - parameter: M3: Keplerian azimuthal motion around 4.76 M☉ at 60 degree, plus constant radial infall 2.5 km s^-1 [Radiative transfer modeling: "around a central mass of 4.76 M$_\odot$at an inclination angle of 60 degree"] [Radiative transfer modeling: "also bears a radial infall velocity of 2.5 km s$^{-1}$at all radii."]
  - parameter: M4: Ulrich accretion-flow velocity field; arbitrarily assumed centrifugal barrier 90 au [Radiative transfer modeling: "another model (M4) in which the gas follows the accretion flow prescribed by (cite: Ulrich76)."] [Radiative transfer modeling: "For the purposing of testing, we assume arbitrarily its centrifugal barrier at a small radius of 90 au (or 0.05$''$)."]
  - parameter: Surface-density profile r^-1.1; at 900 au M1 has 0.79 g cm^-2 and M2–M4 have 0.71 g cm^-2 [Table 1: "$r^{-1.1}$"] [Table 1: "(0.79 g cm$^{-2}$)"]
  - parameter: Temperature: 430 K at r < 214 au; 430 (r/214)^-0.7 K at r ≥ 214 au [Table 1: "430~\mbox{K} & r < 214~\mbox{au}"] [Table 1: "430~(r/214)^{-0.7}~\mbox{K} & r \geq 214~\mbox{au}"]
  - parameter: CH3CN abundance 2 × 10^-8; abundance truncated at radius 900 au; turbulent velocity 2 km s^-1 [Radiative transfer modeling: "We then set a CH$_3$CN fractional abundance be $2\times 10^{-8}$"] [Radiative transfer modeling: "we truncate the CH$_3$CN abundance at a radius of 900 au"]
  - assumption: Flattened two-dimensional structure; empirical column-density and temperature profiles; gas-to-dust ratio 100 [Radiative transfer modeling: "we first assume that the emission originates from a flattened two-dimensional structure, possibly a disc or an envelope."] [Radiative transfer modeling: "For the molecular gas column density and temperature, we adopt the empirical profiles inferred in Section 3.3."]
  - assumption: LTE; no interferometric spatial filtering of model cubes [Radiative transfer modeling: "We carry out our calculations in the LTE regime since the observed transitions are most likely thermalized."] [Radiative transfer modeling: "no interferometric spatial filtering was applied to form the model cubes during this process"]
  - assumption: Neglect gas self-gravity in the gas-kinematic model calculations [Molecular gas mass estimates: "the subsequent model calculations of gas kinematics without considering their self-gravity should be reasonable."]
  - fitting: Qualitative comparison of modeled and observed P-V morphology, especially the central waist and edge-brightening [Radiative transfer modeling: "the central emission "waist" between the two ends at the two "quadrants" in the simulated P-V pattern is significant narrower than that of the observed emission."] [Radiative transfer modeling: "the emission is stronger on the "edges" of the "waist", similar to that in the observed pattern."]
  - validation: Compare K=3 observations with all four models; compare M4 predictions with all observed K components [Radiative transfer modeling: "we compare the observed $J=19-18, K=3$ emission features"] [Radiative transfer modeling: "the P-V diagram of the observed CH$_3$CN emission for all $K$ components in false color and the corresponding model emission in contours."]
- result: Peak 900 μm continuum intensity = 0.237 ± not stated Jy Beam^-1 [Dust continuum, gas column density and …: "the peak continuum intensity of 0.237 Jy Beam$^{-1}$"]
- result: Peak continuum brightness temperature = 121 ± not stated K [Dust continuum, gas column density and …: "a brightness temperature of 121 K"]
- result: Peak H2 column density from continuum at assumed 300 K = 9.75 × 10^24 ± not stated cm^-2 [Dust continuum, gas column density and …: "a gas column density $N_{\mbox{\tiny H$_2$}}$ of 9.75 $\times$ 10$^{24}$ cm$^{-2}$"]
- result: Gas mass enclosed within central 250 au = around 0.36 ± a factor of a few M☉ [Dust continuum, gas column density and …: "enclosed within the central 250 au a total mass of around 0.36 M$_\odot$"]
- result: Mean gas density in central 250 au = ∼6.6 × 10^9 ± not stated cm^-3 [Dust continuum, gas column density and …: "an average gas density of $\sim$ 6.6 $\times$ 10$^{9}$ cm$^{-3}$."]
- result: Continuum flux within 0.5 arcsec diameter = 0.613 ± not stated Jy [Dust continuum, gas column density and …: "The integrated fluxes within larger circular apertures with diameters of 0.5$''$ ($\sim$ 900 au), 1.0$''$ ($\sim$ 1800 au), and 1.5$''$ ($\sim$ 2700 au) are 0.613 Jy, 0.932 Jy, and 1.08 Jy, respectively."]
- result: Continuum flux within 1.0 arcsec diameter = 0.932 ± not stated Jy [Dust continuum, gas column density and …: "The integrated fluxes within larger circular apertures with diameters of 0.5$''$ ($\sim$ 900 au), 1.0$''$ ($\sim$ 1800 au), and 1.5$''$ ($\sim$ 2700 au) are 0.613 Jy, 0.932 Jy, and 1.08 Jy, respectively."]
- result: Continuum flux within 1.5 arcsec diameter = 1.08 ± not stated Jy [Dust continuum, gas column density and …: "The integrated fluxes within larger circular apertures with diameters of 0.5$''$ ($\sim$ 900 au), 1.0$''$ ($\sim$ 1800 au), and 1.5$''$ ($\sim$ 2700 au) are 0.613 Jy, 0.932 Jy, and 1.08 Jy, respectively."]
- result: Gas mass within 0.5 arcsec diameter = 0.930 ± a factor of a few M☉ [Dust continuum, gas column density and …: "The integrated fluxes within larger circular apertures with diameters of 0.5$''$ ($\sim$ 900 au), 1.0$''$ ($\sim$ 1800 au), and 1.5$''$ ($\sim$ 2700 au) are 0.613 Jy, 0.932 Jy, and 1.08 Jy, respectively."]
- result: Gas mass within 1.0 arcsec diameter = 1.41 ± a factor of a few M☉ [Dust continuum, gas column density and …: "The integrated fluxes within larger circular apertures with diameters of 0.5$''$ ($\sim$ 900 au), 1.0$''$ ($\sim$ 1800 au), and 1.5$''$ ($\sim$ 2700 au) are 0.613 Jy, 0.932 Jy, and 1.08 Jy, respectively."]
- result: Gas mass within 1.5 arcsec (∼2700 au) diameter = 1.64 ± a factor of a few M☉ [Summary: "a total gas mass of 1.64 M$_\odot$ within 1.5$''$ ($\sim$ 2700 au) immediately surrounding S255IR NIRS3 in the core."]
- limitation (authors): Cooler outer temperatures and missing flux beyond 2 arcsec can increase inferred outer masses and flatten the density profile. [Dust continuum, gas column density and …: "the averaged temperature over a larger area would likely be cooler"]
- limitation (authors): Several spectral components are blended, uncertain or unidentified. [Spectral features: "the CH$_3$CN $K$=0 and $K$=1 transitions are blended themselves."]
- limitation (authors): Inclination is not well constrained observationally. [Central YSO mass and the geometry of th…: "this angle in fact has not been very well constrained observationally."]
- not stated (card): CASA version and the observatory calibration script or pipeline version.; Calibrator identities, adopted flux models and flux-scale uncertainty; these are deferred to earlier papers.; Self-calibration solution intervals, phase/amplitude sequence, reference antenna, masks and acceptance criteria.; Continuum spectral windows, usable bandwidth and line-free channel selection.; Whether and how contin…

### 2025A&A...693A.286S: Intermediate mass T Tauri disk masses and a comparison to their Herbig disk descendants (2025; protoplanetary_disks, exoplanets; archival_reuse)
- question: Do disks around intermediate mass T Tauri (IMTT) stars, the precursors of Herbig stars, differ from Herbig disks in dust mass, gas mass, gas-to-dust ratio and radii, and what does this imply for planet formation around intermediate mass st…
- step 4: Derive dust masses from continuum flux
  - method: Hildebrand (1983) relation, optically thin emission: M_dust = F_nu d^2 / (kappa_nu B_nu(T_dust)) [Data selection and reduction: "using the relationship of (cite: Hildebrand1983) to directly relate the continuum emission to the dust mass, assuming optically thin emission"]
  - parameter: kappa_nu = 10 cm^2/g at 1000 GHz scaled as nu^beta with beta = 1 [Data selection and reduction: "such that it equals 10 cm$^2$ g$^{-1}$ at a frequency of 1000 GHz"] [Data selection and reduction: "The power-law index $\beta$ is assumed to be equal to 1."]
  - assumption: Optically thin emission [Data selection and reduction: "assuming optically thin emission"]
  - assumption: T_dust scaled with stellar luminosity following Andrews et al. 2013 (25 K x (L/Lsun)^(1/4) in the paper's equation) [Data selection and reduction: "The dust temperature is given by the relationship of (cite: Andrews2013), which scales the dust temperature by the stellar luminosity in solar luminosities via"]
  - assumption: Stellar luminosities from Valegard2021 used for the dust mass [Table of disk fluxes and radii (notes): "The dust masses were recalculated using the stellar luminosities of (cite: Valegard2021)."]
  - validation: Authors note dust masses may be underestimated by up to a factor of ~7 if emission is not optically thin or opacity is wrong [Gas masses and radii: "Recent works have indeed shown that dust masses can be underestimated by up to a factor of $\sim7$ due to these effects"]
- step 5: Build dust mass and radius distributions and compare with Herbig, Lupus, Upper Sco
  - method: Cumulative distributions with lifelines (handles upper limits), log-normal fit by bootstrapping 10^5 samples, two-sample KS test with scipy [Dust masses and radii: "We can obtain cumulative distributions from the dust masses using the `lifelines` package (cite: DavidsonPilon2021)"] [Dust masses and radii: "Using a Kolmogorov-Smirnov test using `scipy` (cite: 2020SciPy-NMeth), we can assess whether the distributions are sampled from the same underlying distribution."]
  - software: lifelines, scipy
  - parameter: 10^5 bootstrap samples [Dust masses and radii: "using a bootstrapping method with $10^5$ samples"]
  - assumption: Log-normal underlying distribution; five NOEMA Herbig disks added to the Herbig comparison sample [Dust masses and radii: "by fitting a log-normal distribution to the cumulative distributions"]
  - fitting: Log-normal fit to cumulative distributions with bootstrap; priors/likelihood not stated [Dust masses and radii: "fitting a log-normal distribution to the cumulative distributions using a bootstrapping method with $10^5$ samples"]
  - validation: KS test p-values for dust masses and radii; 1 sigma confidence band on the cumulative distribution [Dust masses and radii: "We obtain a $p$-value of 0.962"]
- step 7: Derive gas masses, gas-to-dust ratios and gas radii
  - method: Compare observed CO isotopologue disk integrated luminosities to DALI models, select models by disk and stellar parameters, and read off the disk gas mass; combine with dust mass for gas-to-dust; fit gas vs dust radius relation [Gas masses and radii: "we obtain the disk mass after selecting models based on the disk and stellar parameters in Table"] [Gas masses and radii: "Fitting a relationship through the scatter of the resolved disks we find a ratio of 2.8±0.2 between the gas and dust radius for the IMTT disks."]
  - software: DALI
  - parameter: Upper limits for IMTT disks mostly reach the maximum disk mass in the model grid [Gas masses and radii: "Hence, most have upper limits of the maximum disk mass in the model grid."]
  - assumption: ISM gas-to-dust ratio of 100 used as reference; planet-formation section assumes gas-to-dust 100 [Gas masses and radii: "all disks show gas-to-dust ratios of at least the ISM value of 100 or higher"]
  - fitting: Linear gas-vs-dust radius relation fit; method not detailed [Gas masses and radii: "Fitting a relationship through the scatter of the resolved disks"]
  - validation: Radius ratio repeated after removing four disks with difficult radii (GW Ori, HT Lup, SR 21, SU Aur); compared with Herbig disks and Trapman2019 drift limit [Gas masses and radii: "Removing these four disks results in a gas to dust radius ratio of 2.6±0.3"]
- step 8: Compare dust masses of group I and group II IMTT disks
  - method: Split IMTTs by Meeus group from Valegard2021, build cumulative distributions and log-normal fits as in step 5 [Evolution of Herbig disks: "As (cite: Valegard2021) has classified the IMTTs into group I and group II based on the (cite: Meeus2001) classification"]
  - software: lifelines
  - fitting: Log-normal fit to cumulative distributions [Evolution of Herbig disks: "Figure [11](#fig:cdf_dust_groups) presents the two cumulative mass distributions in the left panel, with the fitted log-normal probability distributions in the right panel."]
  - validation: Group I vs II compared with Herbig result; morphology check (cavities in group I) [Evolution of Herbig disks: "For the resolved disks, the group I disks indeed show cavities"]
- step 9: Compare disk dust and gas masses to exoplanet masses
  - method: Build exoplanet solid and envelope mass distribution from NASA Exoplanet Archive around stars with M >= 1.5 Msun, split by heavy-element mass relation, sum planets per star, normalise to occurrence rate 10.7% [Planet formation around intermediate ma…: "To obtain a distribution for the intermediate mass stars, we only include the planets around stars with a minimum mass of 1.5 $M_\odot$."] [Planet formation around intermediate ma…: "The number of stars hosting at least one giant planet is 10.7% (cite: Wolthoff2022), hence we again normalize the distribution so that it adds up to 10.7%."]
  - parameter: Both planet mass and minimum mass M sin i used; no detection method restriction [Planet formation around intermediate ma…: "we set no detection method and use both the planet mass $M_p$ and minimum planet mass $M_p\sin(i)$ in our distribution"]
  - assumption: Heavy-element mass of the planet equals the dust mass needed to form it (Thorngren2016 relation); gas-to-dust ratio of 100 when comparing with disk gas [Planet formation around intermediate ma…: "so we use the relationship from (cite: Thorngren2016) to obtain a heavy-element mass of the planet, and we assume that this is the dust mass necessary to form the planet"]
  - validation: Compared with Mulders2021 efficiency argument [Planet formation around intermediate ma…: "This is in line with what (cite: Mulders2021) finds."]
- result: KS test p-value, IMTT vs Herbig dust mass = 0.962 ± not stated dimensionless [Dust masses and radii: "We obtain a $p$-value of 0.962"]
- result: KS test p-value, IMTT vs Herbig dust radius = 0.860 ± not stated dimensionless [Dust masses and radii: "we cannot reject this null hypothesis based on the resulting $p$-value of 0.860"]
- result: Log-normal mean mu of IMTT dust mass distribution (log10 M/Mearth) = 1.19 ± +0.06/-0.07 log10(M/Mearth) [Table 1: "IMTTs | 1.19$^{+0.06}_{-0.07}$ | 0.58$^{+0.09}_{-0.08}$"]
- result: Log-normal sigma of IMTT dust mass distribution = 0.58 ± +0.09/-0.08 log10(M/Mearth) [Table 1: "IMTTs | 1.19$^{+0.06}_{-0.07}$ | 0.58$^{+0.09}_{-0.08}$"]
- result: Log-normal mu and sigma of Herbig dust mass distribution (with NOEMA disks) = mu 1.27, sigma 0.61 ± mu +0.05/-0.05; sigma +0.06/-0.06 log10(M/Mearth) [Table 1: "Herbigs | 1.27$^{+0.05}_{-0.05}$ | 0.61$^{+0.06}_{-0.06}$"]
- result: Gas mass distribution of IMTTs, Log10(Mdisk) = -1.88 ± ±0.87 Msun (log10) [Gas masses and radii: "We find a gas mass distribution of Log$_{10}$($M_\text{disk}$)=-1.88±0.87 $M_\odot$ for the IMTTs"]
- result: Gas mass distribution of Herbigs, Log10(Mdisk) = -1.55 ± ±0.46 Msun (log10) [Gas masses and radii: "compared to Log$_{10}$($M_\text{disk}$)=-1.55±0.46 $M_\odot$ for the Herbigs"]
- result: Gas-to-dust ratio distribution of IMTTs, Log10(Delta_g/d) = 2.21 ± ±0.37 dimensionless (log10) [Gas masses and radii: "with a distribution of Log$_{10}$($\Delta_{g/d}$)=2.21±0.37 for the IMTTs"]
- result: Gas-to-dust ratio distribution of Herbigs, Log10(Delta_g/d) = 2.48 ± ±0.38 dimensionless (log10) [Gas masses and radii: "compared to Log$_{10}$($\Delta_{g/d}$)=2.48±0.38 for the Herbigs"]
- result: Gas to dust radius ratio, IMTT disks = 2.8 ± ±0.2 dimensionless [Gas masses and radii: "we find a ratio of 2.8±0.2 between the gas and dust radius for the IMTT disks"]
- result: Gas to dust radius ratio, IMTT disks without four difficult disks = 2.6 ± ±0.3 dimensionless [Gas masses and radii: "Removing these four disks results in a gas to dust radius ratio of 2.6±0.3"]
- result: Gas to dust radius ratio, Herbig disks = 2.7 ± ±0.2 dimensionless [Gas masses and radii: "This is the same compared to the ratio of the Herbig disks of 2.7±0.2 within the uncertainties."]
- result: Fraction of disks detected in the first CO isotopologue line = 16 of 28 (57%) ± not stated disks [Gas images: "16 out of 28 (57%) for which data are available have a detection"]
- result: Log-normal mu and sigma, group I IMTT dust mass = mu 1.38, sigma 0.41 ± mu +0.13/-0.25; sigma +0.23/-0.15 log10(M/Mearth) [Table 2: "Group I | 1.38$^{+0.13}_{-0.25}$ | 0.41$^{+0.23}_{-0.15}$"]
- result: Log-normal mu and sigma, group II IMTT dust mass = mu 1.15, sigma 0.35 ± mu +0.08/-0.15; sigma +0.19/-0.14 log10(M/Mearth) [Table 2: "Group II | 1.15$^{+0.08}_{-0.15}$ | 0.35$^{+0.19}_{-0.14}$"]
- limitation (authors): Upper limits on IMTT CO fluxes do not constrain gas masses; most limits reach the grid maximum [Gas masses and radii: "the upper limits obtained for the IMTT disks are not"]
- limitation (authors): Resolved-structure fraction lower than Herbig, attributed to lower spatial resolution; lack of deep observations [Continuum images: "which is likely due to the lower spatial resolution of the data available in our work"]
- limitation (authors): Sample biased towards high accretors and brightest disks [Introduction: "the IMTT disks are likely biased towards the high accretors and brightest disks"]
- not stated (card): CASA version and whether archive pipeline products or manual calibration were used for the non-mosaic data; tclean parameters: robust/weighting, cell size, image size, niter, threshold, masks, uv taper, and the exact channel width per line; Line-free channels and fit order used in uvcontsub for each dataset; Self-calibration solution intervals actually used per target, spw combination, and S/N ac…

### 2023MNRAS.518.6092L: The radial profile of dust grain size in the protoplanetary disc of DS Tau (2023; protoplanetary_disks; archival_reuse)
- question: What is the radial profile of dust grain size in the protoplanetary disk of DS Tau, and how does it correlate with disk substructures?
- step 2: Fit the SED to determine representative disk geometry parameters
  - method: Run a grid of self-consistent two-layer flared disk radiative transfer models in RADMC-3D with isotropic scattering and constant midplane maximum grain size, minimizing chi^2_SED over the two ALMA wavelengths (and checking against the full… [Modeling setup: "Given the stellar parameters, dust density distribution and dust opacities, the code self-consistently computes the dust temperature using the Monte Carlo approach, and then simulates the SED and millimeter images."] [Fitting the SED: "First, we fit the SED to find a parameter set that is representative of the disk geometry."]
  - software: RADMC-3D
  - parameter: H_100 in [5, 10] AU (6 grid points); beta in [1.00, 1.15] (4 grid points); gamma in [0.3, 1.5] (7 grid points); M_dust in [10^-7, 10^-2] M_odot (11 grid points); a_max^mid in [10^3, 10^5] um (5 grid points) [Table 2: "$H_{100}$ [AU] | 7 | 5 | 10 | 6 | free"] [Table 2: "$\beta$ | 1.05 | 1.00 | 1.15 | 4 | free"]
  - parameter: Fixed parameters: M_* = 0.58 M_odot, T_eff = 3792 K, L_* = 0.7 L_odot, R_in = 0.1 AU, R_out = 80 AU, R_gap = 33 AU, sigma = 27 AU, eta = 0.99, H_ratio = 0.2, D = 158 pc [Table 2: "$M_{\star}\ [\mathrm M_{\odot}]$ | 0.58 | 0.58 | 0.58 | 1 | fixed"] [Disk model: "The scale height of the interior layer is given by $H_{\mathrm {ratio}}$, and we fixed it to 0.2, which is a typical value found by previous modeling works of protoplanetary disks (cite: 2011ApJ...732...42A; Liuy2022)."]
  - parameter: 160 wavelengths logarithmically distributed in [0.1, 10000 um] [Stellar heating: "The radiative transfer problem is solved self-consistently considering 160 wavelengths logarithmically distributed in the range of [0.1, 10000 $\mu$m]."]
  - assumption: Passive stellar heating (accretion heating ignored) [Stellar heating: "We assume that the DS Tau disk is passively heated by absorbing energy from the central star (cite: 1997ApJ...490..368C)."] [Stellar heating: "Therefore, we ignore the effect of accretion in the simulation."]
  - assumption: 85% of total dust mass in midplane, 15% in surface layer; surface layer a_max = 1 um, a_min = 0.01 um, size distribution slope p = 3.5 [Disk model: "Considering the settling model, we assume that $85\%$ of the total dust mass is concentrated in the midplane and $15\%$ in the surface layer."] [Dust model: "The grain size distribution follows the power-law ${N(a)}\,{\propto}\,a^{-3.5}, a\,{\in}\,[a_{\mathrm {min}},\ a_{\mathrm {max}}]$, where $a$ is the grain radius and ${N(a)}$ is the number of dust particles whose size is in the interval $[{a,\ a\,{+}\,da}]$. We fix the minimum dust size to $a_{\mathrm {min}}\,{=}\,0.0…"]
  - assumption: DSHARP homogeneous sphere dust composition (20% water ice, 32% astronomical silicates, 8% troilite, 40% refractory organics; rho_dust = 1.675 g cm^-3) with Bruggeman and Mie theory and isotropic scattering [Dust model: "We assume that the dust grains are homogeneous spheres, composed of 20% water ice, 32% astronomical silicates, 8% troilite, and 40% refractory organics, with an average density of $\rho_{\mathrm {dust}}\,{=}\,1.675 \,\mathrm g/\mathrm {cm}^{-3}$."] [Modeling setup: "Therefore, the option of isotropic scattering available in `RADMC-3D` is selected."]
  - fitting: Grid search minimizing chi^2_SED [Fitting the SED: "The best-fit model is identified as the one with the minimum $\chi^2_{\rm SED}$."]
  - validation: Checked model returned from fitting the entire SED (gave H_100 = 10 AU, all other parameters identical). [Fitting the SED: "We also checked the model that is returned from fitting the entire part of the SED, and found that all of the parameter values, except for $H_{100}=10\,{\rm AU}$, are identical to those of the best-fit model."]
- step 4: Estimate depleted dust mass in the gap and evaluate Toomre Q gravitational stability
  - method: Interpolate a smooth power-law dust surface density between R = 6 AU and R = 60 AU, integrate to find the pre-depletion dust mass, and subtract the best-fit dust mass. Compute the radial Toomre Q parameter from the midplane temperature and… [Potential for forming a ~ 3.5 M_Jup mas…: "The surface densities for $6\,{\le}\,{R}\,{\le}\,60\,{\rm AU}$ are parameterized by a power law that connects the best-fit surface densities at $R\,{=}\,6\,\rm{AU}$ and $R\,{=}\,60\,\rm{AU}$, and the surface densities outside the radius range of [6 AU, 60 AU] are set to the best-fit values."] [Gravitational instability: "We check whether the disk is gravitationally stable by using the Toomre $Q$ criterion"]
  - parameter: Power-law interpolation range = [6 AU, 60 AU] [Potential for forming a ~ 3.5 M_Jup mas…: "The surface densities for $6\,{\le}\,{R}\,{\le}\,60\,{\rm AU}$ are parameterized by a power law that connects the best-fit surface densities at $R\,{=}\,6\,\rm{AU}$ and $R\,{=}\,60\,\rm{AU}$, and the surface densities outside the radius range of [6 AU, 60 AU] are set to the best-fit values."]
  - parameter: Mean molecular weight mu_m = 2.34 [Gravitational instability: "The sound speed $c_{\mathrm {s}}\,{=}\,\sqrt{k_{\mathrm{B}} T / \mu_{m} m_{\rm{H}}}$ is calculated from the midplane temperature $T$, with a mean molecular weight $\mu_{m}\,{=}\,2.34$."]
  - assumption: Uniform gas-to-dust mass ratio of 30 (and tested < 10 in the ring) [Potential for forming a ~ 3.5 M_Jup mas…: "Taking the gas-to-dust mass ratio (typically ${\sim}\,30$ in protoplanetary disks) into account, the depleted mass is sufficient for forming a $3.5\,\mathrm M_{\mathrm {Jup}}$ mass planet."] [Gravitational instability: "To have the gas surface density $\Sigma_{\mathrm{g}}$, we simply scale the best-fit dust surface density by a gas-to-dust mass ratio of 30 that is assumed to be uniform in the entire disk."]
- result: Optically thin dust mass estimate = 6.3e-5 ± not stated M_odot [Fitting the SED: "Adopting a dust temperature of $T_{\rm dust}\,{=}\,20\,\rm{K}$, $M_{\mathrm {dust}}$ is estimated to be $6.3\,{\times}\, 10^{-5}\,M_{\odot}$."]
- result: Best-fit scale height at 100 AU (H_100) = 7 ± not stated AU [Fitting the SED: "The best-fit flaring index $\beta\,{=}\,1.05$ and scale height $H_{100}\,{=}\,7\,\rm{AU}$ are recorded in Table 2."]
- result: Best-fit flaring index (beta) = 1.05 ± not stated dimensionless [Fitting the SED: "The best-fit flaring index $\beta\,{=}\,1.05$ and scale height $H_{100}\,{=}\,7\,\rm{AU}$ are recorded in Table 2."]
- result: Best-fit SED surface density gradient (gamma) = 0.5 ± not stated dimensionless [Table 2: "$\gamma$ | 0.5 | 0.3 | 1.5 | 7 | free"]
- result: Best-fit SED total dust mass (M_dust) = 10^-3 ± not stated M_odot [Table 2: "$M_{\mathrm {dust}}$ [$\mathrm M_{\odot}$] | $10^{-3}$ | $10^{-7}$ | $10^{-2}$ | 11 | free"]
- result: Best-fit SED midplane maximum grain size (a_max^mid) = 10^4 ± not stated um [Table 2: "$a^{\mathrm {mid}}_{\mathrm {max}}$ [$\mu$m] | $10^4$ | $10^3$ | $10^5$ | 5 | free"]
- result: Depleted dust mass within the gap = 2 ± not stated M_Jup [Abstract: "Based on the best-fit model, we find that dust of ${\sim}\,2$ Jupiter masses has been depleted within the gap."]
- result: Toomre Q value in the ring region (assuming gas-to-dust ratio of 30) = 0.5 ± not stated dimensionless [Gravitational instability: "The $Q$ value is greater than unity at all radii, except for the ring region with $Q\,{\sim}\,0.5$."]
- limitation (authors): The inner disk (R < 20 AU) is optically thick even at 2.9 mm, so the grain size there cannot be constrained by the spectral index and is fixed to 10 cm. [Grid search for the maximum grain sizes…: "After many simulation tests, we found that this inner region is optically thick even at 2.9 mm, indicating that the grain size can no longer be constrained by the observed spectral index."]
- limitation (authors): Fluctuations in the retrieved grain size profile occur on spatial scales smaller than the beam size (~20 AU), requiring future higher-resolution observations to confirm. [Overview of the modeling results: "The $a^{\mathrm {mid}}_{\mathrm {max}}\,{-}\,R$ profile exhibits some fluctuations on spatial scales smaller than the beam size. Future high-resolution observations are desired to confirm their reality."]
- limitation (authors): The amplitude and shape of the grain size discontinuity at the gap-ring boundary depend on the assumed dust opacity model. [Abstract: "Moreover, our modeling also indicates that at the interface region between the gap and the ring, the grain size profile shows a discontinuity, with its amplitude dependent on the dust model adopted in the radiative transfer analysis."]
- not stated (card): Exact rms noise values (rms_nu) of the convolved Band 6 and Band 3 ALMA images used to calculate radial profile uncertainties; Position angle of the [0.13'', 0.09''] convolving Gaussian beam; Exact radial step size / ellipse spacing used when extracting observed radial intensity profiles; Spatial grid resolution (radial and vertical grid cells) and photon packet counts used in RADMC-3D Monte Carl…

### 2016ApJ...816...37V: Bright [C II] and Dust Emission in Three z &gt; 6.6 Quasar Host Galaxies Observed by ALMA (2016; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: What are the [C II] and FIR dust properties, kinematics and dynamical masses of three z>6.6 VIKING quasar hosts, and how do they relate to the quasars' black holes?
- step 3: Derive FIR/TIR luminosities, SFRs, dust masses
  - method: Scale modified black body (47 K, beta=1.6) and Arp 220/M82 templates to 158 um continuum; SFR from L_TIR (Murphy+11) and L_[CII] (De Looze+14); dust mass with kappa from Dunne+00 [3.1 [CII] and FIR emission: "SFR$_\mathrm{[CII]}$/$M_\ensuremath{\odot}$ yr$^{-1}$ = $3.0\times10^{-9}$ ($L_\mathrm{[CII]}$/$L_\ensuremath{\odot}$)$^{1.18}$, with an uncertainty of 0.4 dex."]
  - parameter: L_FIR 42.5–122.5 um; L_TIR 8–1000 um rest-frame [3.1 [CII] and FIR emission: "The total infrared luminosity ($L_{\mathrm{TIR}}$) was computed by integrating the continuum from 8 $\mu$m to 1000 $\mu$m in the rest-frame."]
  - assumption: Td=47 K, beta=1.6, tau<<1 at lambda>40 um; Kroupa IMF; emission powered by star formation [3.1 [CII] and FIR emission: "our modified black body model has a dust temperature of $T_d=47$ K and a dust emissivity power-law spectral index of $\beta=1.6$"]
  - validation: Range across three SED models adopted as uncertainty [3.1 [CII] and FIR emission: "We caution that the range of values of $L_{\mathrm{FIR}}$ and $L_{\mathrm{TIR}}$ for the VIKING quasar hosts presented here strongly depends on our choice of models"]
- step 6: Estimate dynamical masses and compare M_BH to M_dyn
  - method: M_dyn=1.16e5 v_circ^2 D with v_circ=0.75 FWHM/sin(i), i from axis ratio; compare with Kormendy & Ho relation [4.6 Dynamical mass estimates: "$M_\mathrm{dyn}=1.16\times10^5 v_\mathrm{circ}^2 D$ $M_\ensuremath{\odot}$"]
  - parameter: D=1.5x deconvolved size; i=25, 50 deg; 55 deg and 3±1 kpc for J2348–3054 [4.6 Dynamical mass estimates: "For the unresolved emission in the host of J2348–3054 we assume an extent of $3\pm1$ kpc."]
  - assumption: Thin inclined disk; gas-to-dust ratio ~100 [4.6 Dynamical mass estimates: "If we take the local gas-to-dust mass ratio of $\sim$100 (cite: dra07)"]
  - validation: Inclination uncertainty not included in M_dyn errors [4.6 Dynamical mass estimates: "The uncertainty in these dynamical masses does not include the uncertainties in the inclination angle."]
- result: Dynamical masses (J2348, J0109, J0305) = 7.2e10, 1.4e11, 4.1e10 ± 3.6e10, 0.4e11, 0.5e10 Msun [4.6 Dynamical mass estimates: "we calculate a dynamical mass of $(7.2\pm3.6)\times10^{10}$ $M_\ensuremath{\odot}$, $(1.4\pm0.4)\times10^{11}$ $M_\ensuremath{\odot}$, and $(4.1\pm0.5)\times10^{10}$ $M_\ensuremath{\odot}$"]
- result: Mean M_BH/M_dyn at 1e11 Msun = 1.9% (median 1.3%) vs local 0.49% ± not stated percent [4.6 Dynamical mass estimates: "We find a mean of 1.9% and a median of 1.3%, compared to the local value of $0.49^{+0.06}_{-0.05}$%."]
- limitation (authors): Inclination and peak rotation velocity cannot be independently determined at current resolution [4.4.1 Dynamical Modeling: "with the current data we cannot independently determine the inclination angle and the peak velocity and thus, ultimately, the dynamical mass."]
- limitation (authors): FIR/TIR luminosities strongly model dependent; more photometry needed [3.1 [CII] and FIR emission: "Additional far-infrared photometry is required to better constrain the shape of the infrared continuum and thus $L_{\mathrm{FIR}}$ and $L_{\mathrm{TIR}}$."]
- not stated (card): Exact CASA version and calibration/flagging details; Clean threshold, mask, niter, cell and image size; Which channels were treated as line-free and the velocity binning of cubes; Tilted-ring model parameters beyond those given (position angle, inclination grid, scale height, dispersion); Details of line-luminosity and SFR conversions (e.g. formulae for L_[CII]); Selection and values of literatur…

### 2025ApJ...993L..40S: Unusually High Gas-to-dust Ratios Observed in High-redshift Quiescent Galaxies (2025; high_z_galaxies; observational_alma_primary)
- question: Constrain molecular gas-to-dust ratios in z∼1 quiescent galaxies and test SIMBA predictions.
- step 5: Calculate dust masses
  - method: Calculate Mdust from continuum flux, luminosity distance, frequency-dependent dust absorption, and the Planck-function difference Bν(Tdust)−Bν(TCMB). [Dust and Gas Mass Calculations: "$\ensuremath{M_{\rm{dust}}}= \frac{S_{\nu_{\rm{obs}}} D_L^2}{\kappa_{\nu_{\rm{rest}}} (1+z)} (B_{\nu_{\rm{rest}}}(\ensuremath{\rm{T}_{\rm{dust}}}) - B_{\nu_{\rm{rest}}}(T_{\mathrm{CMB}}))^{-1}$"] [Dust and Gas Mass Calculations: "where $B_\nu(T)$ is the Planck function evaluated at temperature $T$ and $\kappa_\nu \equiv \kappa_{\nu_0} (\nu/\nu_0)^\beta$ is the dust absorption coefficient."]
  - assumption: κν0 = 2.64 m²/kg at ν0 = 2.4 THz; β = 2.0 [Dust and Gas Mass Calculations: "We adopt the emissivity of (cite: dunne03), with $\kappa_{\nu_0} = 2.64$ m$^2$/kg at $\nu_0 = 2.4$ THz varying with frequency with $\beta = 2.0$."]
  - assumption: Mass-weighted Tdust = 25 K [Dust and Gas Mass Calculations: "We assume a mass-weighted $\ensuremath{\rm{T}_{\rm{dust}}}= 25$ K"]
  - assumption: Flat ΛCDM; Ωm = 0.3; H0 = 68 km/s/Mpc [Introduction: "We use a flat $\Lambda$CDM cosmology with $\Omega_m=0.3$ and $H_0=68$ km/s Mpc$^{-1}$, as in SIMBA,"]
  - validation: Test alternative temperatures and emissivities. [Impact of Assumptions on Gas and Dust M…: "Lowering $\rm{T}_{\rm{dust}}$ from 25 to 20 K (cite: magdis21) only increases $M_{\rm{dust}}$ by a factor of $\approx$40%,"] [Impact of Assumptions on Gas and Dust M…: "We explored a number of different dust emissivity parameterizations from the literature to understand its impact (cite: hildebrand83; james02; dunne03; draine07; guillet18; hensley23)."]
- step 8: Derive gas-to-dust ratios and mass fractions
  - method: Calculate δGDR = MH₂/Mdust, fH₂ = MH₂/Mstar, and fdust = Mdust/Mstar; compare with sSFR and stellar mass. [Introduction: "$\ensuremath{\delta_{\rm{GDR}}}\equiv \ensuremath{M_{\rm{H}_2}}/\ensuremath{M_{\rm{dust}}}$"] [Gas and Dust Fractions: "$\ensuremath{f_{\rm{H}_2}}= \ensuremath{M_{\rm{H}_2}}/\ensuremath{M_{\rm{star}}}$, and $\ensuremath{f_{\rm{dust}}}= \ensuremath{M_{\rm{dust}}}/\ensuremath{M_{\rm{star}}}$"]
  - parameter: 0.5<z<1.5 for the stellar-mass comparison [Are Quiescent Galaxies Gas-Rich or Dust…: "now restricting the literature comparison sample to galaxies at $0.5 < z < 1.5$ to minimize redshift evolution."]
  - assumption: Dust traces molecular H₂ only; ignore neutral atomic gas. [SIMBA Simulation Products: "As in the observations, we assume that dust traces only molecular H$_2$ gas, ignoring neutral atomic gas."]
  - validation: Check whether accounting for HI changes the high-ratio interpretation in SIMBA. [Impact of Assumptions on Gas and Dust M…: "We verify that, at least in SIMBA, galaxies with abnormally high molecular $\delta_{\rm{GDR}}$ also have abnormally high total (HI$+$H$_2$) $\delta_{\rm{GDR}}$,"]
- step 9: Compare with SIMBA
  - method: Select massive galaxies from the z=1 snapshot; remove objects without dust, H₂, or metals; adjust SFRs and compare gas fractions, dust fractions, and gas-to-dust ratios. [SIMBA Simulation Products: "From the $z=1$ snapshot of the (100 $h^{-1}$ Mpc)$^3$ simulation box, we select massive galaxies with $\log(\ensuremath{M_{\rm{star}}}/\ensuremath{\rm{M}_\odot}) > 10$."] [SIMBA Simulation Products: "We remove any galaxies with no dust, H$_2$, or metals."]
  - software: SIMBA
  - parameter: SFR adjustment ≈0.1–0.2 dex upward at log(Mstar/M⊙)>10 [SIMBA Simulation Products: "At the high stellar masses $\log(\ensuremath{M_{\rm{star}}}/\ensuremath{\rm{M}_\odot}) > 10$ we consider here, this adjustment is small, a $\approx$0.1–0.2 dex upward revision to the SIMBA SFRs."]
  - assumption: Ignore neutral atomic gas in the fiducial gas-to-dust ratio. [SIMBA Simulation Products: "As in the observations, we assume that dust traces only molecular H$_2$ gas, ignoring neutral atomic gas."]
  - validation: Comparisons unchanged using z=0.5 or z=2 simulation outputs. [Gas and Dust Fractions: "The comparison to SIMBA would not change by using either the $z=0.5$ or $z=2$ simulation outputs"]
- step 10: Assess conversion-factor systematics
  - method: Vary CO excitation, dust temperature, αCO, dust emissivity, and inclusion of HI to assess whether standard gas-to-dust ratios can be recovered. [Impact of Assumptions on Gas and Dust M…: "Variations in the dust temperature $\rm{T}_{\rm{dust}}$ and CO excitation factor $r_{21}$ are the easiest to rule out,"] [Impact of Assumptions on Gas and Dust M…: "The CO–H$_2$ conversion factor is a much larger hammer at our disposal."]
  - parameter: r21: 0.8→1.0; Tdust: 25→20 K; αCO reduced by 4.4 [Impact of Assumptions on Gas and Dust M…: "Increasing $r_{21}$ from 0.8 to 1.0 (i.e. thermalized CO emission) would only decrease the CO(1–0) luminosity by 25%,"] [Impact of Assumptions on Gas and Dust M…: "Lowering $\rm{T}_{\rm{dust}}$ from 25 to 20 K (cite: magdis21) only increases $M_{\rm{dust}}$ by a factor of $\approx$40%,"]
- result: C022260 dust mass = <1.3 ± 2σ limit 10^7 M⊙ [Table 1: "C022260 & 09:59:16.38 & +02:33:41.8 & 1.240 & 11.50 & 3.6 & \<44 & \<1.3 & 10.6 & \>780"]
- result: C074512 dust mass = <1.1 ± 2σ limit 10^7 M⊙ [Table 1: "C074512 & 10:01:42.88 & +02:01:21.9 & 0.733 & 11.15 & 6.3 & \<42 & \<1.1 & 6.6 & \>610"]
- result: C110509 dust mass = <1.0 ± 2σ limit 10^7 M⊙ [Table 1: "C110509 & 10:01:04.44 & +02:04:37.2 & 0.667 & 11.34 & 6.5 & \<42 & \<1.0 & 8.2 & \>830"]
- result: C130284 dust mass = 3.3 ± not stated 10^7 M⊙ [Table 1: "C130284 & 10:00:13.78 & +02:19:37.0 & 0.602 & 11.18 & 6.8 & 150 & 3.3 & 10.0 & 300"]
- result: C132776 dust mass = 2.0 ± not stated 10^7 M⊙ [Table 1: "C132776 & 10:00:12.43 & +02:21:21.9 & 0.750 & 11.15 & 7.9 & 80 & 2.0 & 14.3 & 700"]
- result: Undetected-source stack dust mass = <0.7 ± 2σ limit 10^7 M⊙ [Table 1: "stack & — & — & 0.717 & 11.34 & 5.5 & \<28 & \<0.7 & 8.2 & \>1200"]
- result: C022260 molecular gas-to-dust ratio = >780 ± 2σ limit dimensionless [Table 1: "C022260 & 09:59:16.38 & +02:33:41.8 & 1.240 & 11.50 & 3.6 & \<44 & \<1.3 & 10.6 & \>780"]
- result: C074512 molecular gas-to-dust ratio = >610 ± 2σ limit dimensionless [Table 1: "C074512 & 10:01:42.88 & +02:01:21.9 & 0.733 & 11.15 & 6.3 & \<42 & \<1.1 & 6.6 & \>610"]
- result: C110509 molecular gas-to-dust ratio = >830 ± 2σ limit dimensionless [Table 1: "C110509 & 10:01:04.44 & +02:04:37.2 & 0.667 & 11.34 & 6.5 & \<42 & \<1.0 & 8.2 & \>830"]
- result: C130284 molecular gas-to-dust ratio = 300 ± ±70 dimensionless [Unusually High Gas-to-Dust Ratios Obser…: "Under our fiducial assumptions, the two galaxies with detected dust continuum, C130284 and C132776, have $\ensuremath{\delta_{\rm{GDR}}}= 300 \pm 70$ and $700 \pm 250$, respectively."]
- result: C132776 molecular gas-to-dust ratio = 700 ± ±250 dimensionless [Unusually High Gas-to-Dust Ratios Obser…: "Under our fiducial assumptions, the two galaxies with detected dust continuum, C130284 and C132776, have $\ensuremath{\delta_{\rm{GDR}}}= 300 \pm 70$ and $700 \pm 250$, respectively."]
- result: Undetected-source stack molecular gas-to-dust ratio = >1200 ± 2σ limit dimensionless [Table 1: "stack & — & — & 0.717 & 11.34 & 5.5 & \<28 & \<0.7 & 8.2 & \>1200"]
- result: ALMA.14 gas-to-dust ratio recalculated under fiducial assumptions = ≈100 ± not stated dimensionless [Unusually High Gas-to-Dust Ratios Obser…: "The only other quiescent galaxy detected in both gas and dust is ALMA.14 (cite: hayashi18); under our assumptions, we find $\ensuremath{\delta_{\rm{GDR}}}\approx 100$ for this source."]
- result: Dust-mass increase using Draine emissivity = ≈50 ± not stated % [Impact of Assumptions on Gas and Dust M…: "Of these, only the emissivity of (cite: draine07) increased the dust masses, by $\approx$50% compared to our fiducial assumption,"]
- limitation (authors): Small CO-selected sample with uncertain representativeness [Discussion and Conclusions: "It is not clear whether our target galaxies, preselected to have CO detections, are typical in their gas and/or dust properties."]
- limitation (authors): UV+IR SFRs may overestimate true SFRs because old stars heat dust. [Quiescent Galaxies and ALMA Observations: "We expect these to overestimate the true SFR because old stars can also contribute to the dust heating at low SFR"]
- not stated (card): Calibration pipeline or manual procedure, CASA version, flagging, calibrator identities, and absolute flux-scale uncertainty.; Exact spectral-window frequencies, channelization, effective continuum bandwidth, and channel selection.; Imaging task, deconvolution settings, stopping threshold, masks, cell size, image dimensions, and primary-beam treatment.; Exact aperture centers and random-aperture …

### 2021A&A...652A..66P: ALMA multiline survey of the ISM in two quasar host-companion galaxy pairs at z &gt; 6 (2021; high_z_galaxies, agn_and_quasars; observational_alma_primary)
- question: How do star formation and AGN activity shape the multiphase ISM (dust, ionized, atomic and molecular gas) in two z>6 quasar host galaxies and their nearby companion galaxies, from multi-line ALMA band 3-6 observations plus CLOUDY PDR/XDR m…
- step 3: Fit dust SEDs and derive L_FIR, L_TIR and SFR_IR
  - method: Optically thin modified blackbody with CMB contrast (da Cunha+2013) fitted to the continuum fluxes plus Decarli+2017 band 6 data; integrate over 40-400 um (FIR) and 8-1000 um (TIR); SFR_IR = 1.49e-10 L_TIR/Lsun [Dust properties: FIR continuum: "we modeled the continuum data with a modified black body taking into account the effect of the cosmic microwave background radiation"] [Dust properties: FIR continuum: "we estimated the total (TIR, $8-1000\,{\rm \mu m}$, (cite: Sanders+2003)) and FIR ($40-400\,{\rm \mu m}$, (cite: Helou+1988)) rest-frame luminosities"]
  - software: emcee
  - parameter: box priors log Mdust > 0 and beta in (1, 2.5) [Dust properties: FIR continuum: "We limited the parameter space by imposing box-like priors defined as $\log M_{\rm dust}[M_{\astrosun}] > 0$, and $\beta\in(1,2.5)$."]
  - parameter: Gaussian prior on T_dust, mean 47 K, sigma 5 K [Dust properties: FIR continuum: "we employed a relative tight Gaussian prior on $T_{\rm dust}$ with mean and standard deviation equal to $47\,{\rm K}$ and $5\,{\rm K}$, respectively"]
  - parameter: companions refit with T_dust prior centred on 35 K [Dust properties: FIR continuum: "we performed an additional fit centering the Gaussian dust temperature prior on $T_{\rm dust}=35\,{\rm K}$"]
  - parameter: nu_0 = 352.7 GHz for k_d(nu) = k_0 (nu/nu_0)^beta [Dust properties: FIR continuum: "where $\nu_0 = 352.7$ GHz, and $\beta$ is the dust spectral emissivity index"]
  - assumption: optically thin dust emission [Dust properties: FIR continuum: "by assuming optically thin dust emission (cite: Beelen+2006)"]
  - assumption: T_CMB ~19 K at z=6; the CMB heating correction to T_dust(z) is ignored (<2%) [Dust properties: FIR continuum: "is $T_{\rm CMB}\approx 19\, {\rm K}$ at $z=6$"] [Dust properties: FIR continuum: "Therefore, we ignore this correction."]
  - assumption: IR luminosity dominated by star formation; Kroupa IMF [Dust properties: FIR continuum: "The initial mass function (IMF) implicitly assumed in this $L_{\rm TIR}$ to ${\rm SFR}$ conversion is a Kroupa IMF"]
  - assumption: LCDM with H0 = 69.3 km/s/Mpc, Omega_m = 0.287 [Introduction: "Throughout the paper we assume a standard $\Lambda\rm{CDM}$ cosmology with $H_0=69.3\,\si{km\,s^{-1}Mpc^{-1}}$, $\Omega_{m}=0.287$"]
  - fitting: emcee with free M_dust, beta and T_dust (Gaussian prior); upper limits enter via a penalty term in the log-likelihood; sampler settings not stated [Dust properties: FIR continuum: "allowing $M_{\rm dust}$, and $\beta$ to freely vary during the fitting procedure"] [Dust properties: FIR continuum: "by inserting a penalty term in the log-likelihood function in the form $\mathcal{P}=-0.5[({\rm model}-{\rm data})/{\rm data}]^2$, if ${\rm model}>{\rm data}$, else $\mathcal{P}=0$"]
  - validation: T_dust prior justified by literature and the H2O results; 35 K and 47 K priors give consistent results for companions (within 1.5 sigma) [Dust properties: FIR continuum: "and also validated by the results obtained below for the water vapor lines"] [Dust properties: FIR continuum: "we obtained similar results that are consistent within $1.5\sigma$"]
- step 7: Build CO(1-0)-normalized SLEDs and fit with CLOUDY PDR+XDR models
  - method: Estimate L'CO(1-0) from dust mass, gas-to-dust ratio and alpha_CO; normalize measured CO lines; fit PDR, XDR and composite PDR+XDR CLOUDY models by minimizing chi-square [CO(1–0)–normalized SLEDs: "$L'_{\rm CO(1-0)} = M_{\rm dust} \, \delta_{\rm gdr}/\alpha_{\rm CO}$"] [CO SLED models: "our best-fit CLOUDY models of the CO SLED in PJ231-20 QSO obtained by minimizing $\chi^2$"]
  - software: CLOUDY
  - parameter: gas-to-dust ratio 100 [CO(1–0)–normalized SLEDs: "by adopting $\delta_{\rm gdr}= 100$"]
  - parameter: alpha_CO = 0.8 (K km/s pc^2)^-1 [CO(1–0)–normalized SLEDs: "by employing the typical value of $\alpha_{\rm CO} = 0.8\,({\rm K\, km\,s^{-1}\,pc^2})^{-1}$ (cite: Downes+1998)"]
  - parameter: composite model W_PDR F_PDR + W_XDR F_XDR at N_H = 1e23 [CO SLED models: "a composite (PDR+XDR) model in the form $W_{\rm PDR}F_{\rm CO}^{\rm PDR}(n_{\rm H}^{\rm PDR},G_0)+W_{\rm XDR}F_{\rm CO}^{\rm XDR}(n_{\rm H}^{\rm XDR},F_{\rm X})$"]
  - assumption: 75% of the dust-derived gas mass is molecular [CO(1–0)–normalized SLEDs: "assuming that $75\%$ of the dust-derived gas mass is in molecular form (cite: Riechers+2013; Wang+2016; Venemans+2017a)"]
  - fitting: chi-square minimization over CLOUDY grid (single PDR, single XDR, composite PDR+XDR) [CO SLED models: "our best-fit CLOUDY models of the CO SLED in PJ231-20 QSO obtained by minimizing $\chi^2$"]
  - validation: Composite fit compared with a single-XDR alternative; authors note more free parameters than data points and degeneracies [CO SLED models: "the number of free parameters is greater than data points, thus producing degeneracies in best-fit parameters."]
- step 9: Estimate mass budgets (CI, H2, minimum H+, dust-based gas)
  - method: CI mass from L'[CI] (Weiss+2003) with T_ex = 30 K; H2 mass from X[CI]/X[H2]; minimum H+ mass from [NII]205 (Ferkinhoff+2011); gas mass from dust mass and gas-to-dust ratio 70-100 [Mass budgets: "$M_{\rm CI}[M_{\astrosun}] = 4.566\times 10^{-4}Q(T_{\rm ex})\frac{1}{5}e^{62.5/T_{\rm ex}}L'_{\rm [CI]_{\rm 369\mu m}}$"] [Mass budgets: "adopting the local gas-to-dust ratio of $\delta_{\rm gdr}\sim70-100$ (cite: Draine+2007; Sandstrom+2013; Genzel+2015)"]
  - parameter: X[CI]/X[H2] = M_CI/(6 M_H2) = (8.4 +/- 3.5)e-5 [Mass budgets: "$X[{\rm CI}]/X[{\rm H_2}] = M_{\rm CI} / (6M_{\rm H_2}) = (8.4\pm3.5)\times 10^{-5}$"]
  - parameter: chi(N) = 9.3e-5 for the minimum H+ mass [Mass budgets: "$\chi({\rm N}) = 9.3\times10^{-5}$ (cite: Savage+1996)"]
  - assumption: T_ex = 30 K (50 K gives ~40% lower M_CI); LTE, optically thin, 2-level approximation [Mass budgets: "Assuming an excitation temperature of $T_{\rm ex}=30\,{\rm K}$ (cite: Walter+2011)"] [Mass budgets: "In the 2-level approximation, assuming local thermodynamical equilibrium (LTE) and in the optically thin limit and Rayleigh-Jeans regime"]
  - validation: CI-based molecular gas masses are consistent with dust-derived gas masses (75% molecular) [Mass budgets: "these values are consistent with those derived above from $M_{\rm CI}$ applying the CI-to-H$_2$ abundance ratio"]
- result: Dust masses of the four sources (range) = 0.5e8 - 0.5e9 ± not stated Msun [Summary and conclusions: "as reflected by the enormous amount of dust ($M_{\rm dust}\approx0.5\times10^8-0.5\times10^9\,M_{\astrosun}$) heated at relatively high temperature"]
- result: L_CO(1-0) estimate, PJ231-20 QSO = ~2.4e6 ± not stated Lsun [CO(1–0)–normalized SLEDs: "we find $L_{\rm CO(1-0)} \sim 2.4 \times 10^6\,L_{\astrosun}$ for PJ231-20 QSO"]
- result: L_CO(7-6)/L_CO(1-0), PJ231-20 QSO = 93 ± +13/-12 dimensionless [CO SLED models: "we measured $L_{\rm CO(7-6)}/L_{\rm CO(1-0)}=93_{-12}^{+13}$"]
- result: PDR and XDR weights in the composite CO SLED fit, PJ231-20 QSO = W_PDR = 0.90, W_XDR = 0.10 ± +/-0.04 each dimensionless [CO SLED models: "The best-fit model has $W_{\rm PDR}=0.90\pm0.04$ and $W_{\rm XDR}=0.10\pm0.04$"]
- result: Best-fit composite CO SLED parameters, PJ231-20 QSO = n_H(PDR) ~4e2 cm^-3, G0 ~1e5, n_H(XDR) ~5e5 cm^-3, F_X ~10 erg/s/cm^2 ± not stated cm^-3, Habing units, erg s^-1 cm^-2 [Summary and conclusions: "The best-fit PDR component indicates $n_{\rm H}^{\rm PDR}\sim4\times10^{2}\,{\rm cm^{-3}}$ and $G_0\sim1\times10^5$, while the XDR component is determined by $n_{\rm H}^{\rm XDR}\sim5\times10^5\,{\rm cm^{-3}}$ and $F_{\rm X}\sim 10\, {\rm erg\,s^{-1}\,cm^{-2}}$."]
- result: Neutral carbon mass, PJ231-20 QSO = 0.7e7 ± +/-0.3e7 Msun [Mass budgets: "we find for the PJ231-20 QSO a neutral carbon mass of $M_{\rm CI} = (0.7\pm0.3)\times10^7\,M_{\astrosun}$"]
- result: Molecular gas mass from CI, PJ231-20 QSO = 1.3e10 ± +1.1/-0.6 (x1e10) Msun [Mass budgets: "we obtain a molecular gas mass of $M_{\rm H_2} = 1.3^{+1.1}_{-0.6}\times10^{10}\,M_{\astrosun}$ for PJ231-20 QSO"]
- result: Minimum ionized hydrogen mass, PJ231-20 QSO host and companion = 4.1e8 (QSO), 1.8e8 (companion) ± +/-1.6e8 (QSO), +/-1.2e8 (companion) Msun [Mass budgets: "This gives $M_{\rm min}({\rm H^+})= (4.1\pm1.6)\times10^8\,M_{\astrosun}$, and $(1.8\pm1.2)\times10^8\,M_{\astrosun}$ for PJ231-20 QSO host and companion galaxy, respectively."]
- result: Dust-based gas mass, PJ231-20 QSO host and companion (gdr 70-100) = (3.6-5.1)e10 (QSO), (1.6-3.4)e10 (companion) ± range from gas-to-dust ratio choice Msun [Mass budgets: "we obtain (atomic and molecular) gas masses of $M_{\rm gas} = (3.6 - 5.1)\times 10^{10}\,M_{\astrosun}$ and $(1.6 - 3.4)\times 10^{10}\,M_{\astrosun}$ for the PJ231-20 QSO host and companion galaxy respectively"]
- limitation (authors): Composite CO SLED fit has more free parameters than data points, so best-fit values are degenerate [CO SLED models: "the number of free parameters is greater than data points, thus producing degeneracies in best-fit parameters."]
- limitation (authors): T_dust cannot be constrained by the dust fit and follows the prior [Dust properties: FIR continuum: "confirming that $T_{\rm dust}$ cannot be constrained with the fit."]
- limitation (authors): Poor SED coverage gives only tentative dust constraints for PJ308-21 [Dust properties: FIR continuum: "we found only tentative constraints on $M_{\rm dust}$ and $\beta$ due to the poor coverage of the dust spectral energy distributions (SEDs)"]
- not stated (card): Flux, bandpass and phase calibrators and pipeline version per execution block; whether archive products or a re-run pipeline were used; Spectral window layout and exact channel ranges of the line-free channels and the 'brightest pixel' positions used for spectra; Clean threshold in mJy/beam, number of iterations, image size, deconvolver and mask radii; emcee configuration (walkers, steps, burn-in…

### 2015A&A...583A..66H: Probing the final stages of protoplanetary disk evolution with ALMA (2015; protoplanetary_disks, debris_disks; observational_alma_primary)
- question: Are weak-line T Tauri stars with IR excess photoevaporating transition disks or young debris disks, based on their dust masses and CO content?
- step 2: Derive dust masses
  - method: M_dust = 0.566 [F(1300)/mJy (d/140 pc)^2] Mearth [3.1 Disk dust masses: "M_{\mathrm{dust}}=0.566 \times \left[ \dfrac{F_{\nu}(1300)}{mJy} \left( \dfrac{d}{140 pc} \right)^{2} \right] M_{\oplus}"]
  - assumption: optically thin continuum at mm wavelengths [3.1 Disk dust masses: "owing to continuum emission being optically thin at mm wavelengths, the dust mass can be estimated by a simple equation"]
  - validation: Upper limits uncertainty dominated by distance [3.1 Disk dust masses: "we quote the 3 sigma value as our upper limit, with this uncertainty being dominated by the uncertainty in the distance to the system."]
- step 3: Constrain gas-to-dust ratio from CO non-detection
  - method: compare 3 sigma limit of 90 mJy km/s to Williams & Best grid [3.2 12CO(2-1) non-detections: "would be readily detectable in $^{12}$CO(2-1) at our $3\sigma$ detection limit of 90 mJy km s$^{-1}$."]
  - parameter: stellar mass 0.5 Msun; other parameters free [3.2 12CO(2-1) non-detections: "We compare our results to this grid for a stellar mass of 0.5 M$_{\odot}$"]
  - assumption: ISM gas-to-dust ratio 100 as reference [3.2 12CO(2-1) non-detections: "an ISM gas-to-dust ratio of 100 would imply a gas mass of $\sim 1\,M_{\rm J}$"]
  - validation: CO would be detected in 90% of models for other disks [3.2 12CO(2-1) non-detections: "the CO emission would still be above our detection threshold for 90% of the models"]
- result: Dust mass system 17 = 2.09 ± 0.44 Mearth [Table 3: "| 17 | 1.813 | 2.09$\pm$0.44 | 0.10 | $2.6_{-0.5}^{+1.2}$ | 140 |"]
- result: Dust mass system 14 = 0.45 ± 0.13 Mearth [Table 3: "| 14 | 0.696 | 0.45$\pm$0.13 | 0.17 | $6.9_{-1.7}^{+2.8}$ | 80 |"]
- result: CO 3 sigma limit = 90 ± not stated mJy km/s [3.2 12CO(2-1) non-detections: "our $3\sigma$ detection limit of 90 mJy km s$^{-1}$"]
- limitation (authors): Dust mass method has significant uncertainties; ages uncertain; binarity unconfirmed [3.1 Disk dust masses: "This approach has significant uncertainties but is quite standard in the field"]
- not stated (card): Reduction software/CASA version and pipeline; Image size, cell size, clean masks and thresholds; Synthesized beams and per-source rms values; Channel width and velocity range for CO upper limit (90 mJy km/s); Point-source fit details; Photometry values and fitted blackbody parameters used for SEDs; Flux calibrator model/uncertainty; Extinction values used for de-reddening

### 2014ApJ...796....1T: Angular Momentum Exchange by Gravitational Torques and Infall in the Circumbinary Disk of the Protostellar System L1551 NE (2014; star_formation, protoplanetary_disks; observational_alma_primary)
- question: Do gravitational torques from the central binary drive angular momentum exchange and infall in the circumbinary disk of L1551 NE, as seen in non-axisymmetric dust features and gas velocities?
- step 2: Fit protostar components and derive disk masses
  - method: Gaussian fits to the two compact continuum components, subtract them to isolate the circumbinary disk, then compute masses from M=S d^2/(kappa B(T)) [3.1 0.9-mm Continuum: "we subtracted two Gaussian components with parameters derived from the fit to the two compact dust components"]
  - parameter: Td = 10-42 K, beta=0.5, kappa0.9mm=0.053 cm2/g, d=140 pc [3.1 0.9-mm Continuum: "With $T_{d}$ = 10 – 42 K and $\kappa_{0.9mm}$ = 0.053 cm$^{2}$ g$^{-1}$"]
  - assumption: Gas-to-dust mass ratio of 100, dust opacity from Hildebrand 1983 with beta=0.5 [3.1 0.9-mm Continuum: "on the assumption of a gas-to-dust mass ratio of 100"]
  - validation: Compared with Ossenkopf & Henning opacity (factor 3 higher masses) [3.1 0.9-mm Continuum: "Thus, adopting the dust mass opacity by Ossenkopf & Henning (1994) provides a factor 3 higher masses of the circumstellar and circumbinary disks."]
- result: Flux density of south-eastern compact component (Source A) = 0.35 ± not stated Jy [3.1 0.9-mm Continuum: "The south-eastern component has a flux density of 0.35 Jy"]
- result: Flux density of north-western compact component (Source B) = 0.17 ± not stated Jy [3.1 0.9-mm Continuum: "the north-western component a flux density of 0.17 Jy"]
- result: Circumbinary disk flux density = 0.47 ± not stated Jy [3.1 0.9-mm Continuum: "The flux density of the circumbinary disk in the 0.9 mm continuum as computed from Figure [1](#cont)d is 0.47 Jy"]
- result: Circumstellar disk mass of Source A = 0.005 - 0.044 ± range from Td 10-42 K Msun [3.1 0.9-mm Continuum: "a mass for the circumstellar disk of Source A is calculated to be $\sim$0.005 - 0.044 $M_{\odot}$"]
- result: Circumstellar disk mass of Source B = 0.003 - 0.022 ± range from Td 10-42 K Msun [3.1 0.9-mm Continuum: "that of Source B a mass of $\sim$0.003 - 0.022 $M_{\odot}$"]
- result: Circumbinary disk mass = 0.007 - 0.059 ± range from Td 10-42 K Msun [3.1 0.9-mm Continuum: "corresponding to a mass for the circumbinary disk of $\sim$0.007 - 0.059 $M_{\odot}$"]
- result: Dust mass opacity at 0.9 mm = 0.053 ± not stated cm2 g-1 [3.1 0.9-mm Continuum: "The dust mass opacity at 0.9 mm is then calculated to be $\kappa_{0.9mm}$ = 0.053 cm$^{2}$ g$^{-1}$."]
- limitation (authors): Missing flux and outflow complicate other lines near systemic velocity; temperatures in hydrodynamics (isothermal 13.5 K) and radiative transfer (power law) are inconsistent. [2 ALMA Observation and Data Reduction: "Closer to the systemic velocity, the spatial-kinematic structure in the other lines is complicated by the effects of missing flux as well as an outflow (see Appendix A)."]
- not stated (card): CASA version used for calibration and imaging; Clean threshold, mask, niter, cell and image size, and whether multiscale was used; Line-free channel ranges for continuum and constant continuum level; Details of the Keplerian subtraction implementation and Gaussian fit procedure; Simulation initial conditions, hydrodynamic code (SFUMATO modified) not public; simobserve inputs and noise settings; P…

### 2017ApJ...835..213P: The Dense Molecular Gas and Nuclear Activity in the ULIRG IRAS 13120-5453 (2017; nearby_galaxies, astrochemistry, agn_and_quasars; observational_alma_primary)
- question: What are the excitation, abundance and kinematics of dense gas tracers (HCN, HCO+, CS) in the ULIRG IRAS 13120-5453, and what do they imply for nuclear starburst/AGN activity and outflows?
- step 5: Model Herschel H2O lines for dust temperature
  - method: compare observed H2O line ratios to grid of radiative transfer models [4: "Our general approach to the modeling was to compare the observed ratios of various H$_{2}$O lines to a grid of models"]
  - parameter: Tgas=150 K, nH2=3e4 cm-3 fixed [4: "We used $T_{\mathrm{gas}}=150$ K and $n_{H_{2}}=3\times10^{4}$ cm$^{-3}$"]
  - assumption: gas-to-dust ratio 100 by mass [4: "We have adopted a gas-to-dust ratio of 100 by mass"]
  - fitting: grid comparison, best fit by eye/ratios [Water Emission in IRAS 13120–5453: "Our general approach to the modeling was to compare the observed ratios of various H$_{2}$O lines to a grid of models with varying $T_{\mathrm{dust}}$"]
- step 7: Continuum size, dust and ISM mass, Sigma_IR
  - method: 2D Gaussian fit to 333 GHz continuum; dust mass with kappa; Scoville2014 relation [6: "The distribution of the emission is well represented by a 2D Gaussian with a beam-deconvolved size (FWHM) of $0.86\ensuremath{''} \times 0.75\ensuremath{''}$"]
  - parameter: Tdust=40 K, kappa(333 GHz)=0.28 cm2/g [6: "$\kappa(333~\textnormal{GHz})=0.28$ cm$^{2}$ g$^{-1}$ (cite: Bianchi2013)"]
  - assumption: gas-to-dust 100; 80% of L_IR in starburst following sub-mm distribution [6: "If we assume a gas-to-dust ratio of 100 (cite: Wilson2008)"]
  - validation: compared with dynamical mass and Herschel/Planck extrapolation [Nuclear Continuum Emission: "This is comparable to the dynamical mass estimated from the HCN and HCO$^+$ kinematics (Section [5.1](#sec:dynamicalmass)) and implies $M_{ISM}/M_{dyn}\approx0.9$ within the central kpc."]
- result: best-fit H2O model Tdust = 40 ± range 40-60 K allowed K [4: "The best fit, which is also included in Figure [7](#fig:herschel), is achieved with $\tau_{100}=0.5$ $T_{\mathrm{dust}}=40$ K"]
- result: Sigma_IR,50 = 4.7e12 ± not stated Lsun kpc^-2 (as in table) [6: "We find $\Sigma_{IR,50}=4.7\times10^{12}$ kpc$^{-2}$."]
- result: dust mass from 333 GHz = 2.9e8 ± not stated Msun [6: "this implies a dust mass of $2.9\times10^{8}$"]
- limitation (authors): ALMA may resolve out up to ~50% of 333 GHz flux [6.1: "it suggests were are resolving out up to $\sim50\%$ of the 333 GHz flux with our ALMA observations."]
- limitation (authors): LVG solutions under-constrained [3.2.1: "While the solutions are under-constrained and so we cannot propose “best” values for the system"]
- not stated (card): Briggs robust value; line-free channels used for continuum subtraction; CASA version; clean threshold, cell and image size; how the 3D kinematic fit (GalPak3D) was parameterized; Herschel photometry values for the SED fits; velocity ranges defining outflow channels; region definitions for 1 kpc aperture spectra

### 2018A&A...614A.113H: ALMA detection of a tentative nearly edge-on rotating disk around the nearby AGB star R Doradus (2018; evolved_stars; observational_alma_primary)
- question: Does the spatial offset between blue and red shifted molecular emission in R Dor's inner wind indicate a compact rotating disk, and what are its properties and possible companion?
- step 3: Disk radiative transfer modelling
  - method: 3D NLTE LIME model of sub-Keplerian disk, passed through CASA observation simulation, compared to PV diagrams [3: "we aim to reproduce the observed three-dimensional emission distribution by assuming a differentially rotating disk."]
  - software: LIME, CASA
  - parameter: radial velocity 1 km/s, turbulence 1 km/s, temperature power-law index -0.5 [3: "The disk temperature is assumed to be a simple power-law with an index of $-$0.5."]
  - assumption: gas-to-dust mass ratio 100 [3: "with an assumed gas-to-dust mass ratio of 100"]
  - assumption: 1 Msun central star [3: "with a mass of 1 $\,{\rm M}_\odot$ (cite: Danilovich2017)"]
  - fitting: Manual parameter tuning, no formal fit [3.1: "whose values have been varied until a reasonable visual resemblance between the model and the data was achieved."]
  - validation: Visual comparison of PV diagrams; checked LIME level populations for no masing [3: "We found no indication that the optical depth $\tau$ has become negative at any position or iteration"]
- result: inner rim radius = 6 ± not stated AU [3: "corresponds to an inner rim location of $\sim$6 AU"]
- result: inclination = 110 ± 20 deg [3.2: "we assume an uncertainty of 20$^\circ$ on the inclination angle"]
- result: radial density power index p = -2.8 ± ~15% dimensionless [3.2: "we estimate an uncertainty on the slope of $\sim$15% or $p=-3\pm0.5$"]
- limitation (authors): Parameters tuned visually; no statement on fit quality [3.1: "Hence, we can make no statements about the quality of the ‘fit’."]
- limitation (authors): Insufficient spatial resolution limits kinematics [3.2: "the insufficient spatial resolution of the data imposes some important limitations on this analysis"]
- not stated (card): CASA version and imaging parameters (weighting, cell, deconvolution); continuum subtraction and line-free channels; flux calibrator names; LIME settings (number of grid points, photons) and CASA simulation configuration; exact stellar velocity/lsr used and PV extraction details; continuum peak position

### 2014ApJ...796...84R: ALMA Imaging of Gas and Dust in a Galaxy Protocluster at Redshift 5.3: [C II] Emission in "Typical" Galaxies and Dusty Starbursts ≈1 Billion Years after the Bi… (2014; high_z_galaxies; observational_alma_primary)
- question: What are the gas (CII, OH) and dust properties of the SMG AzTEC-3 and of 'typical' Lyman-break galaxies in the z=5.3 protocluster?
- step 4: Constrain FIR luminosity, SFR and dust mass of LBGs
  - method: Normalise nearby galaxy templates to Subaru i-band; integrate dwarf templates over 42.5-122.5 µm; scale to ALMA limit [3.4 SED, LBGs: "we thus integrated the dwarf galaxy templates over their infrared peaks."]
  - parameter: T_dust=30 K, beta=1.5 for dust mass limit [3.4 SED, LBGs: "Assuming a dust temperature of $T_{\rm dust}$=30 K and an opacity power law index of $\beta$=1.5"]
  - assumption: Chabrier IMF for SFR from L_FIR; LBG-2/3 share LBG-1 redshift and SED shape [3.5 Derivation of Further Galaxy Proper…: "We assume a Chabrier ((cite: cha03)) stellar initial mass function (IMF) to derive star formation rates from $L_{\rm FIR}$."]
  - fitting: template matching [Spectral Energy Distribution, Lyman-Bre…: "Given the detailed available photometry from COSMOS, we match galaxy templates to the observed SED of LBG-1"]
  - validation: UV-based SFR of 22 Msun/yr compared with FIR limit [4.2 LBGs: "This is comparable to the best SFR$_{\rm FIR}$ limit, and again consistent with low dust extinction."]
- result: LBG-1 FIR SFR upper limit = <18–54 ± not stated Msun/yr [abstract: "suggesting far-infrared SFRs of $<$18–54 $M_{\odot}$ yr$^{-1}$"]
- result: LBG-1 UV SFR = 22 ± not stated Msun/yr [4.2 LBGs: "This yields SFR$_{\rm UV}$=22 $M_{\odot}$ yr$^{-1}$."]
- limitation (authors): Spatial resolution insufficient to resolve structure; higher resolution needed [3.2 [CII] Line Emission: "Observations at higher spatial resolution are required to further resolve the detailed structure of the interstellar medium in this massive starburst galaxy."]
- limitation (authors): Photometric uncertainties near the SED peak are large [3.4 SED, AzTEC-3: "the uncertainties on the photometry close to the peak of the SED are $>$30%–50%"]
- not stated (card): CASA/AIPS versions; CLEAN mask, threshold, cell and image size; Line-free channels and continuum subtraction method; Which processing (AIPS vs CASA) produced the final maps and fluxes; Aperture/extraction regions for spectra of LBG components; MCMC priors on T_dust, alpha, lambda0 and run settings beyond beta prior; Which dwarf templates were used and their normalisation; Exact virial coefficient…

### 2024MNRAS.527.3559P: The debris disc of HD 131488: bringing together thermal emission and scattered light (2024; debris_disks; multi_facility_alma_minor)
- question: Can scattered light (SPHERE) and thermal emission (SED) of the CO-rich debris disc HD 131488 be fitted self-consistently with a semi-dynamical N-body model, and what does this imply for gas drag, porosity and size distribution
- step 4: Fit scattered light with semi-dynamical radiation-pressure models (Mie and DDA)
  - method: MODERATO dust-orbit models with free disc width, dust mass, size index q and porosity P, compared with IRDIS image by chi2 [4.3.2 Mie model: "We use the following free parameters: disc width $\Delta r$, dust mass $M_\text{d}$, size distribution index $q$, and dust porosity $P$."] [3 Theoretical Background: "In order to analyse the scattered light and thermal emission data of HD 131488, we make use of the MODERATO code"]
  - software: MODERATO
  - parameter: PA and i fixed to the HG values [4.3.2 Mie model: "We fix PA and $i$ to the values inferred from the HG approach to keep the fitting process fast."]
  - parameter: Maximum grain size 1e4 micron, minimum 0.1 micron [3.5.2 Maximum grain size and size distr…: "To account for most of the cases we will assume a maximum size of $10^4\mu$m"] [3.5.1 Minimum size: "we will not fix our size distribution to the blowout limit but to a size of 0.1 $\mu$m to account for the presence of those sub-blowout grains"]
  - parameter: Porosity grid 0.0 to 0.8 in steps of 0.2 [4.3.2 Mie model: "($0.0 \leq P \leq 0.8$ in steps of 0.2)"]
  - assumption: Pure astronomical silicate, bulk density 3.3 g/cm3, porosity via Bruggeman EMT (Mie) or vacuum voids of 1/100 grain diameter (DDA) [4.1 Stellar photosphere and dust compos…: "We assume a dust composition of pure astronomical silicate with a bulk density of 3.3 g/cm$^{3}$"] [3.3 Dust composition: "We assume the diameter of the vacuum inclusions (“voids”) to be as large as 1/100 of the grain diameter"]
  - assumption: Proper eccentricity of colliding planetesimals 0.1 [3.5.1 Minimum size: "we assume a proper eccentricity $\langle e\rangle$ of the colliding planetesimals of 0.1"]
  - fitting: chi2 minimisation; parameter uncertainties from varying each parameter until chi2 exceeds the critical value [4.2 Fitting approach: "Based on the best-fit parameter values we change each free parameter individually until the final $\chi^2$ gets larger than the critical value."]
  - validation: Reduced chi2 <= 1.05 as 95 per cent confidence criterion [4.2 Fitting approach: "In terms of a reduced $\chi^2$ this means a value of $\leq 1.05$ in our case."]
- step 5: Fit the SED / thermal emission to get the dust mass
  - method: SONATA two-component fit, then MODERATO with radiation pressure for the outer belt [4.4.2 Results: "In a first approach we use the SONATA code to fit a two component model to the observational data"] [4.4.2 Results: "In a second approach we use the MODERATO code which now includes the effects of radiation pressure."]
  - software: SONATA, MODERATO, ATLAS9
  - parameter: Scattered-light best-fit parameters applied: P=0.6, q=3.0, r0=88 au, Delta r=30 au; dust mass then fitted to 1 Mearth [4.4.2 Results: "we find that the observational data can be fitted when using a dust mass of $1\,M_\oplus$ instead of $5\,M_\oplus$"]
  - assumption: Only the outer Kuiper-belt analogue modelled; inner warm belt not modelled with MODERATO [4.4.2 Results: "Hence, we do not model a possible Asteroid belt analogue with MODERATO but only the outer Kuiper belt analogue"]
- step 6: Add gas drag to reconcile scattered-light and SED dust masses and derive gas surface density
  - method: Vary gas surface density; grains with Stokes number St<=1 retained by setting beta to zero [4.5 Combining SED and scattered light r…: "In a simple approach we vary the gas surface density and assume that particles for which the Stokes number is"] [4.5 Combining SED and scattered light r…: "are retained within the disc by setting the $\beta$ parameter to zero."]
  - software: MODERATO
  - parameter: q=3.0, dust mass fixed to 1 Mearth in both scattered light and SED [4.5 Combining SED and scattered light r…: "we need a surface density of $\Sigma = (2.0\pm0.1)\times 10^{-5}\,M_\oplus/$au$^2$ to fit both the SED and the scattered light data."]
  - assumption: beta itself is unchanged by gas; only the grain orbits are [4.5 Combining SED and scattered light r…: "We note that in reality $\beta$ is not changed by the presence of gas, but the grains’ orbits are."]
  - validation: Compared with ALMA-based gas surface density estimate (rough, no uncertainty) [4.5 Combining SED and scattered light r…: "this value is in agreement with expectations/estimates from ALMA observations."]
- result: Mie model size distribution index q = 3.0 ± +/- 0.1 dimensionless [4.3.2 Mie model: "The best-fitting size distribution index is $q=3.0\pm 0.1$."]
- result: Mie model dust mass (radiation pressure only) = 4.5 ± +/- 0.8 Mearth [4.3.2 Mie model: "we need a dust mass of $\sim4.5\pm0.8\,M_\oplus$ to fit the scattering flux density observed"]
- result: Best-fitting porosity (Mie) = 0.6 ± 0.0-0.4 not excluded dimensionless [4.3.2 Mie model: "We find a best fitting porosity of 0.6."]
- result: Parent belt width (asymmetric Gaussian, Mie) = 30 ± +/- 3 au [4.3.2 Mie model: "With this approach we find a best fitting disc width of ($30\pm3$) au"]
- result: DDA model size distribution index q and dust mass = q=3.0; M=4.4 ± q +/- 0.2; M +/- 0.7 q dimensionless; Mearth [4.3.3 DDA model: "The size distribution index is found as $q=3.0\pm 0.2$, and the dust mass as $M_\text{dust} \approx 4.4\pm0.7~M_\oplus$."]
- result: Blowout size, compact grains to P=0.8 (Mie) = 2.9 (compact) to ~11 (P=0.8) ± not stated micron [3.4.1 Radiation pressure parameter: "the blowout sizes vary between $2.9\,\mu\hbox{m}$ for compact grains and $\sim11\,\mu\hbox{m}$ for particles with a porosity of 0.8"]
- result: Dust mass from SED = 1.0 ± +/- 0.2 Mearth [4.4.2 Results: "We find a best-fitting model for a dust mass of $1.0\pm0.2~M_\oplus$"]
- result: Gas surface density needed to fit SED and scattered light = 2.0e-5 ± +/- 0.1e-5 Mearth au^-2 [4.5 Combining SED and scattered light r…: "we need a surface density of $\Sigma = (2.0\pm0.1)\times 10^{-5}\,M_\oplus/$au$^2$ to fit both the SED and the scattered light data."]
- limitation (authors): Gas surface density is a rough estimate without uncertainties [4.5 Combining SED and scattered light r…: "We note that this is a rough estimate without uncertainties as we do not have enough data on gas species present in the disc."]
- limitation (authors): Disc extent beyond 90 au uncertain because of low SNR [2.1 Radial profiles: "However, in this region the SNR is low so that the actual extent beyond 90 au remains uncertain."]
- limitation (authors): Inner disc poorly constrained by the low-resolution, nearly edge-on ALMA data [5.2.1 ALMA vs SPHERE: "Due to the low spatial resolution of the ALMA data and the nearly edge-on orientation of the disc, the region within 88 au is not well constrained at long wavelengths."]
- not stated (card): How the 1.65 mm (1652 micron) ALMA flux density marked 'This work' in Table 1 was measured, from which data, and with what imaging/aperture; ALMA array configuration, spectral setup, imaging parameters and calibration of the data used for the CO position-velocity diagram; How the CO position-velocity diagram was extracted (task, aperture width, channel range, beam); MODERATO code and its input gr…

### 2018ApJ...869...10M: Comprehensive Analysis of HD 105, A Young Solar System Analog (2018; debris_disks; archival_reuse)
- question: What are the stellar parameters, disc architecture, scattered-light albedo and dust properties of the young Solar analogue HD 105 and its debris disc?
- step 3: Derive dust mass
  - method: Optically thin M = F d^2 / (kappa B) [3.2.1 Disc architecture: "assuming that the disc is fully optically thin at 1.3 mm"]
  - assumption: kappa = 1.7 g cm^-2 [3.2.1 Disc architecture: "Assuming the dust opacity $\kappa$ is 1.7 gcm$^{-2}$"]
- step 5: Measure scattered-light radial profile and albedo
  - method: PSF subtraction (KLIP/PCA-RDI), elliptical-aperture averaging using ALMA geometry, throughput correction, albedo from Weinberger approximation [3.3.3 Combined modelling: "we obtain an albedo of 0.15 based on the NICMOS surface brightness (15 $\mu$Jy/arcsec$^{2}$), or 0.06 based on the SPHERE measurement"]
  - parameter: NICMOS F160W: 69 modes, 125 reference images; SPHERE: 100 PCA modes, 610 images from 22 stars [3.3.2 VLT/SPHERE: "We then selected 610 images from 22 stars most correlated with the ones from HD 105"]
  - assumption: Optically thin dust [3.3.3 Combined modelling: "Assuming optically thin dust, and using the approximation from (cite: 1999Weinberger)"]
  - validation: Algorithm throughput by analytical forward modelling (NICMOS) [3.3.1 HST/NICMOS: "We corrected our average profiles and uncertainties by estimating the algorithm throughput with analytical forward modeling."]
- step 6: Constrain grain size and composition from albedo
  - method: Hyperion radiative transfer for grain sizes 0.1-500 μm and silicate/ice mixtures [3.4 Constraints on the dust composition: "We test grain sizes from 0.1 to 500 $\mu$m, and dust compositions of pure astronomical silicate, and water ice:astronomical silicate mixtures"]
  - software: Hyperion
  - assumption: Dust mass fixed from ALMA flux; Ldust/L* = 2.6e-4 [3.4 Constraints on the dust composition: "For consistency, we keep the dust mass of the disc fixed to that calculated for HD 105 based on its ALMA mm flux."]
- result: Dust mass = 0.035 ± +0.013/-0.009 Earth masses [3.2.1 Disc architecture: "we calculate a mass of $0.035^{+0.013}_{-0.009}~$M$_{\oplus}$ for the dust"]
- result: Dust albedo (NICMOS) = 0.15 ± not stated dimensionless [3.3.3 Combined modelling: "we obtain an albedo of 0.15 based on the NICMOS surface brightness (15 $\mu$Jy/arcsec$^{2}$)"]
- result: Dust albedo (SPHERE) = 0.06 ± not stated dimensionless [3.3.3 Combined modelling: "or 0.06 based on the SPHERE measurement (5.9 $\mu$Jy/arcsec$^{2}$)"]
- limitation (authors): Low S/N ALMA data; belt width not conclusively resolved [3.2.1 Disc architecture: "The belt is perhaps marginally resolved in the ALMA image, but the quality of the data does not allow us to conclude that"]
- limitation (authors): Dust opacity uncertainty gives factor 3-5 in mass [3.2.1 Disc architecture: "which leads to an uncertainty in $M_{\rm dust}$ of a factor 3 to 5."]
- limitation (authors): NICMOS/SPHERE discrepancy possibly from non-Gaussian noise [3.3.2 VLT/SPHERE: "it can be seen in the reduced image that the noise is non-Gaussian."]
- not stated (card): Cell size and image size of the ALMA clean image; clean threshold, mask and iterations; Exact model-fit residual metric and error estimation for disc architecture; Line-free channels for uvcontsub; Dust temperature adopted for the mass calculation; Details of the CO non-LTE excitation conditions; SED fitting method, likelihood and how parameter errors were derived

### 2018MNRAS.479.1154B: The interstellar medium properties of heavily reddened quasarsand companions at z∼ 2.5 with ALMA and JVLA (2018; agn_and_quasars, high_z_galaxies; observational_alma_primary)
- question: What are the ISM excitation conditions and gas masses (from CO, CI and dust) of heavily reddened quasars and their millimetre-bright companions at z~2.5?
- step 3: Fit radio-to-FIR SED for SFR, non-thermal fraction, dust mass
  - method: Synchrotron + free-free + greybody composite fit with MultiNest [4.1: "Models are fit to the data using the Bayesian inference code MultiNest ((cite: Feroz:08)) in combination with the Python wrapper PyMultinest"]
  - software: MultiNest, PyMultiNest
  - parameter: log-uniform SFR 10-9000; uniform log f_nth 0.5-1.5; alpha 0.1-1.6 [4.1: "We assume a log-uniform prior for SFR (10-9000 M$_{\odot}$yr$^{-1}$) and uniform priors for log$_{10}f_{\rm nth}$ (0.5-1.5) and $\alpha$ (0.1-1.6)"]
  - assumption: T_d=47 K, beta=1.6, alpha_ff=-0.1, optically thin Rayleigh-Jeans dust, kappa0=0.045 m^2/kg at 250 GHz [4.1: "$\kappa_0$ is assumed to be 0.045 m$^2$ kg$^{-1}$ at $\nu_0$=250GHz"]
  - fitting: Ellipsoidal nested sampling (PyMultiNest) [4.1: "PyMultiNest explores the parameter space using ellipsoidal nested sampling"]
  - validation: Tested fixed alpha=0.75 and 0.1 and beta 1.6-2.4; Herschel flux split alternatives [4.1: "We have checked that dividing the *Herschel* flux according to the ratio of ALMA fluxes in the three galaxies does not affect the results significantly."]
- step 5: Derive atomic carbon mass and gas masses from CO, dust, CI
  - method: CO luminosity with alpha_CO=0.8, dust masses with gas-to-dust ratio 42-130, CI with X_CI=3e-5 and Q10=0.6 [4.3.3: "We assume a value of X$_{\rm{CI}}$=3$\times10^{-5}$, based on a template of M82"]
  - assumption: alpha_CO=0.8 Msun (K km/s pc^2)^-1; r31=1.0 where undetermined [Table 6: "Assuming r$_{31}$=1.0 when L$^{\prime}_{\rm{CO(3-2)}}>$L$^{\prime}_{\rm{CO(1-0)}}$ or there is no constraint on L$^{\prime}_{\rm{CO(1-0)}}$"]
- result: SFR ULASJ1234 = 1160 ± 120 Msun/yr [4.1: "SFRs of 1160$\pm$120 M$_\odot$ yr$^{-1}$ and 680$\pm$100 M$_\odot$yr$^{-1}$ for ULASJ1234 and ULASJ2315"]
- result: SFR ULASJ2315 = 680 ± 100 Msun/yr [4.1: "SFRs of 1160$\pm$120 M$_\odot$ yr$^{-1}$ and 680$\pm$100 M$_\odot$yr$^{-1}$"]
- result: synchrotron index alpha (J1234, J2315) = 0.9 and 0.4 ± 0.2 and 0.1 dimensionless [4.1: "$\alpha=0.9\pm0.2$ for ULASJ1234 and $\alpha=0.4\pm0.1$ in ULASJ2315"]
- result: log M_dust J1234, J2315 = 8.32, 8.09 ± not stated log Msun [4.1: "The new dust masses are log$_{10}$(M$_{\rm{dust}}$)=8.32 and 8.09 for ULASJ1234 and ULASJ2315 respectively."]
- result: M_CI ULASJ1234 = 4.9e6 ± 0.6e6 Msun [4.2.4: "We find $\rm{M}_{\rm{CI}}$= (4.9$\pm$0.6)$\times$10$^6$M$_\odot$ for ULASJ1234"]
- result: r31 ULASJ0123 = 1.4 ± 0.2 dimensionless [Table 6: "r$_{31}$ | 1.4$\pm$0.2"]
- limitation (authors): J2315 SED and line ratios use blended flux from unresolved merger components [4.1: "we again caution against over-interpretation of these numbers given the lack of constraints at the peak of the dust SED"]
- limitation (authors): 3D-PDR lacks X-ray and mechanical heating [4.2.3: "a caveat of our current modelling is that the 3D-PDR code does not include X-ray and mechanical heating"]
- not stated (card): Line-free channel ranges for uvcontsub; Clean threshold, cell size, image size, masking; Details of JVLA calibrators and flux scale; Exact velocity ranges for line fluxes and spectral extraction apertures; Band 3 data and Paper II measurements needed as inputs; 3D-PDR chemical network, line-ratio fitting likelihood and priors; MultiNest settings and likelihood details; Flux scale uncertainty for …

### 2021A&A...645A..49G: A proto-pseudobulge in ESO 320-G030 fed by a massive molecular inflow driven by a nuclear bar (2021; nearby_galaxies, star_formation, astrochemistry; archival_reuse)
- question: Infer the nuclear physical conditions and structure of ESO 320-G030, and test whether bar-driven molecular inflow feeds its nuclear starburst.
- step 4: Fit component sizes and infer parameter distributions
  - method: Search all core–disk–envelope combinations; minimize reduced chi-squared for solid angles; marginalize Bayesian posterior distributions for physical and derived parameters. [Minimizing chi_red^2: "We then consider all possible combinations, in a number of $2.2\times10^8$, that are obtained by taking 1 component of each group."] [Minimizing chi_red^2: "The minimization is performed by a standard procedure and yields both $R_j$ for each component of the combination and then the minimum $\chi_{\mathrm{red}}^2$."]
  - parameter: Three components; 24 fitted line and continuum quantities; 12 free physical parameters; sizes treated as derived [Minimizing chi_red^2: "$N_L=24$ is the number of H$_2$O lines and continuum flux densities that are fitted"] [Likelihood distributions: "Our model for ESO 320-G030 has a total of $N_f=12$ free physical parameters, ($T_{\mathrm{dust}}$, $\tau_{100}$, $N_{\mathrm{H2O}}$, $n_{\mathrm{H2}}$) for each of the 3 model components."]
  - parameter: Add 15% Herschel and 10% ALMA systematic uncertainties in quadrature [Minimizing chi_red^2: "we sum in quadrature the errors in Table [\[tab:obs\]](#tab:obs) and the systematic uncertanties of 15% and 10% for the *Herschel* and ALMA measurements, respectively."]
  - assumption: Gas-to-dust mass ratio 100 [Likelihood distributions: "which implicitly assumes a gas-to-dust ratio of 100 by mass."]
  - fitting: Gaussian detection likelihood with an error-function upper-limit term; prior zero for T_dust < 60 K and X_H2O > 3 × 10^-5, unity otherwise; no sampler named. [Likelihood distributions: "$N_d=23$ corresponds to the line and continuum detections and $N_u=1$ to the undetected H$_2$O $8_{18}-7_{07}$ line at 63.32 $\mu$m"] [Likelihood distributions: "we use the prior $P(\mathbf{a})=0$ whenever a model component with $T_{\mathrm{dust}}<60$ K and $X_{\mathrm{H2O}}>3\times10^{-5}$ is found, and $P(\mathbf{a})=1$ otherwise."]
  - validation: Compare two- and three-component chi-squared; inspect 2D posterior degeneracies; select the fiducial model using ALMA maps. [Results: "the minimum value of $\chi_{\mathrm{red}}^2$ significantly increases to 2.3 when only 2 components are used."] [Results: "Based on the superior comparison between the observed and model-predicted maps of the H$_2$O448 and 454 GHz continuum emission"]
- result: Fiducial reduced chi-squared = 1.098 ± not stated dimensionless [Results: "we have selected a specific model combination, with $\chi_{\mathrm{red}}^2=1.098$, as the fiducial model for detailed comparison with the data."]
- result: Best 10^3 three-component combinations: reduced chi-squared range = 1.0-1.4 ± not stated dimensionless [Results: "The values of $\chi_{\mathrm{red}}^2$ for the best-fit $10^3$ combinations are in the range $1.0-1.4$"]
- result: Two-component minimum reduced chi-squared = 2.3 ± not stated dimensionless [Results: "the minimum value of $\chi_{\mathrm{red}}^2$ significantly increases to 2.3 when only 2 components are used."]
- result: Core effective radius = approximately 12 ± not stated pc [Summary and limitations of the model: "an additional, very compact component with an effective radius of $\approx12$ pc"]
- result: Core radius range = 9-16 ± not stated pc [Discussion and conclusions: "We estimate a core radius of $R=9-16$ pc"]
- result: Core dust temperature = approximately 100 ± not stated K [Summary and limitations of the model: "very warm ($T_{\mathrm{dust}}\sim100$ K)"]
- result: Disk dust temperature = approximately 55 ± not stated K [H2O excitation, column densities, and a…: "The disk component, which has high $N_{\mathrm{H2O}}$ and is optically thick in the far-IR, nevertheless has a moderate $T_{\mathrm{dust}}\approx55$ K."]
- result: Disk optical depth at 100 micrometres = approximately 1.5 ± not stated dimensionless [The core, disk, and envelope components: "still optically thick in the far-IR ($\tau_{100}\approx1.5$"]
- result: Envelope radius = approximately 130-150 ± not stated pc [The core, disk, and envelope components: "is predicted to have a radius of $\sim130-150$ pc"]
- result: Envelope dust temperature = approximately 50 ± not stated K [The core, disk, and envelope components: "This “envelope component”, which is also moderately warm ($T_{\mathrm{dust}}\approx50$ K)"]
- result: Envelope H2O column density = approximately 10^17 ± not stated cm^-2 [H2O excitation, column densities, and a…: "The column densities $N_{\mathrm{H2O}}$ of the envelope and disk components are well defined and very different, $\sim10^{17}$ and $\sim10^{19}$ cm$^{-2}$ respectively"]
- result: Disk H2O column density = approximately 10^19 ± not stated cm^-2 [H2O excitation, column densities, and a…: "The column densities $N_{\mathrm{H2O}}$ of the envelope and disk components are well defined and very different, $\sim10^{17}$ and $\sim10^{19}$ cm$^{-2}$ respectively"]
- result: Core H2O column-density lower limit = approximately 10^20 ± lower limit cm^-2 [H2O excitation, column densities, and a…: "In the core component, only a lower limit for $N_{\mathrm{H2O}}$ of $\sim10^{20}$ cm$^{-2}$ is obtained."]
- result: Envelope H2O abundance relative to H nuclei = approximately 3 × 10^-7 ± not stated dimensionless [H2O excitation, column densities, and a…: "the resulting abundances $X_{\mathrm{H2O}}$ are $\sim3\times10^{-7}$ and $\sim10^{-5}$ for the envelope and the disk, respectively."]
- result: Disk H2O abundance relative to H nuclei = approximately 10^-5 ± not stated dimensionless [H2O excitation, column densities, and a…: "the resulting abundances $X_{\mathrm{H2O}}$ are $\sim3\times10^{-7}$ and $\sim10^{-5}$ for the envelope and the disk, respectively."]
- limitation (authors): Some extra-nuclear contribution to the lowest-lying H2O lines is not excluded. [The core, disk, and envelope components: "although some extra-nuclear contribution to the lowest-lying H$_2$O lines is not ruled out."]
- limitation (authors): Core lines are saturated; core optical depth, abundance, mass, and size are uncertain. [H2O excitation, column densities, and a…: "all lines -including the submillimeter H$_2$O448 transition- are saturated in this component."]
- limitation (authors): The three-component geometry is schematic with sharp transitions. [Additional remarks: "it is obviously very schematic with sharp edges and transitions from one component to the next."]
- not stated (card): ALMA CASA version, calibration scripts, flagging choices, calibrators, and any self-calibration history.; Exact spectral-window setup, continuum channel selections, and H2O448 continuum-subtraction procedure.; Imaging task, image dimensions, clean masks, stopping thresholds, deconvolver, and primary-beam treatment.; Coordinates, systemic-velocity definition, and the intended frequency-frame speci…

### 2021A&A...655A..98A: The contribution by luminous blue variable stars to the dust content of the Magellanic Clouds (2021; evolved_stars, stellar_physics, nearby_galaxies; multi_facility_alma_minor)
- question: How much dust do luminous blue variable stars (31 confirmed and candidate LBVs in the Magellanic Clouds) contribute, compared with low- and intermediate-mass evolved stars and the ISM dust budget
- step 5: Grey-body dust masses of individual stars
  - method: Grey-body fit of the infrared SED for LHA 120-S 119 and for RMC 71, HD 269216, RMC 81, RMC 40; beta fixed at 1.3 for three sources [5.1 Individual stars: "we thus fit the infrared SED with a greybody to derive the characteristic temperature, dust mass and $\beta$ parameter"] [5.1 Individual stars: "We fit these data by fixing the parameter $\beta$=1.3"]
  - parameter: kappa(850 um) = 1.7 cm^2 g^-1 [5.1 Individual stars: "an absorption coefficient value $\kappa_{\rm 850\mu m}$ of $\rm 1.7\, cm^{2}\, g^{-1}$"]
  - assumption: Optically thin dust, so radiative transfer effects are negligible [5.1 Individual stars: "For such sources we can assume that radiative transfer effects are negligible."]
  - assumption: LMC distance 49.97 kpc for all sources [5.1 Individual stars: "We assume a distance of $49.97\,\rm kpc$ for the LMC (cite: 2013Pietrzynski) for all sources."]
  - validation: RMC 71 grey-body mass compared with the radiative-transfer literature value [5.1 Individual stars: "we also fit the data of RMC 71 with a grey-body and find a dust mass which agrees with the literature value"]
- step 7: Fit the stacked SED for the integrated dust mass
  - method: Power law for winds and photosphere plus a grey body for the dust, mass from the best-fit flux at 850 micron [5.2 Stack analysis of LBVs in the LMC: "with a power law representing the sum of stellar winds and photospheres"] [5.2 Stack analysis of LBVs in the LMC: "The dust mass of the aggregate source is computed by assuming the flux density extracted from the best fit at $\rm 850\,\mu$m."]
  - parameter: Two absorption coefficients: kappa(850) of Sodroski et al. 1987 and the Gordon et al. 2014 kappa_160 = 9.6 [4.2 Total dust mass in the LMC: "Results are given for two different opacity values, as in (cite: 1987Sodroski) (SD87) and (cite: 2014Gordon) (GD14)."]
  - assumption: Systematic kappa uncertainty of about 25% not propagated [4.2 Total dust mass in the LMC: "The uncertainty of about $25\%$ in $\kappa_{\lambda}$ due to the systematic error is not taken into account."]
  - fitting: Grey-body range set by chi-squared twice the minimum; lower limits at 70 and 250 micron used as constraints [5.2 Stack analysis of LBVs in the LMC: "The grey shaded region represents all the grey-body components that fit the data producing a $\chi^2$ which is twice the minimum value of the best fit."]
- step 8: Stack extreme AGB stars for comparison
  - method: Same stacking on the Riebel et al. catalogue; 1342 extreme AGBs after removing ten sources; two-component fit [5.3 Stack analysis of other evolved sta…: "The final sample of extreme AGB stars from (cite: 2012Riebel) that we stacked comprises 1342 objects."]
  - assumption: Photosphere black body of fixed 3000 K; grey body with beta = 0; extinction with R_V = 3.1; optically thin dust (lower limit on mass) [5.3 Stack analysis of other evolved sta…: "We fitted the data with two components: a black body of fixed temperature (3000 K) describing the stellar photosphere, and a grey body with dust spectral index $\beta=0$."] [5.3 Stack analysis of other evolved sta…: "The dust mass derived from this fitting assumes that the dust is optically thin (at the wavelength at which $\kappa$ is defined), and thus must be considered a lower limit."]
  - validation: 24 micron stacked photometry consistent with Riebel et al. stacked photometry [5.3 Stack analysis of other evolved sta…: "we compared our photometry extracted from the stack image with the stacked photometry (cite: 2012Riebel) and found a consistent value"]
- result: Integrated dust mass of 18 LMC Class 1 and 2 LBVs (Gordon et al. 2014 kappa) = 0.11 ± +0.06/-0.03 Msun [abstract: "we derived an integrated dust mass of $0.11^{+0.06}_{-0.03}\,M_{\odot}$"]
- result: Average dust mass per LBV from the stack (Gordon et al. 2014 kappa) = 0.006 ± +0.003/-0.002 Msun [4.2 Total dust mass in the LMC: "and an average of $\langle M_{\rm dust}\rangle=0.006^{+0.003}_{-0.002}\, M"]
- result: Dust mass of LHA 120-S 119 (grey body) = 1.2e-2 ± +2.2/-0.7 (x 1e-2) Msun [Table 2: "$1.2^{+2.2}_{-0.7}$"]
- result: Integrated dust mass of 1342 extreme AGBs = 1.2e-4 ± +0.3/-0.4 (x 1e-4) Msun [Summary and conclusions: "The integrated dust mass from these sources is $1.2^{+0.3}_{-0.4}\times10^{-4}\,M_{\odot}$."]
- limitation (authors): Dust masses may be lower limits because cooler dust may be missed [6.2 Total dust mass in the LMC: "Additionally, the dust masses estimated here could be a lower limit, as cooler dust may have escaped the observations."]
- limitation (authors): Systematic uncertainty of about 25% in kappa is not propagated into the dust mass [6.2 Total dust mass in the LMC: "The uncertainty of about $25\%$ in $\kappa_{\lambda}$ due to the systematic error is not taken into account."]
- limitation (authors): The fraction of massive stars that become LBVs is unconstrained and dominates the yield uncertainty [6.2.2 Accounting for star formation his…: "A major uncertainty in this relation lies in the fraction of massive main-sequence stars that will become LBV stars"]
- not stated (card): ALMA/ACA calibration, imaging and measurement steps used for the RMC 14 upper limits (CASA version, pipeline or manual, weighting, cell size, mosaic imaging, primary beam correction, rms definition); Which ALMA execution blocks and array configurations were used for the Band 3 and Band 6 upper limits, and the angular resolution; Correction factors per filter applied to the stacked 2-D Gaussian fl…

### 2024MNRAS.535..729P: The spatially resolved relation between dust, gas, and metal abundance with the TYPHOON survey (2024; nearby_galaxies; archival_reuse)
- question: What is the spatially resolved relationship between the dust-to-gas mass ratio (DGR) and gas-phase metallicity (Z_gas) across a broad metallicity range in nearby galaxies at (sub-)kpc scales?
- step 3: Pre-process, convolve, and resample multi-wavelength images to common resolution
  - method: Correct photometry for MW foreground extinction, subtract sky background using IDL sky.pro, remove foreground stars from FUV to 24 um using PTS-7/8 (with Gaia DR3 and CMD cross-matching for NGC 6822), convolve all maps using Aniano et al. … [2.3.1 Sky background subtraction: "to remove sources from the image and derive a median value of the background levels of a given box size."] [2.3.2 Foreground star removal: "we utilize the PTS-7/8 [15] (Verstocken et al. 2020) software, the Python toolkit associated to the SKIRT radiative transfer code (Camps & Baes 2015; Camps & Baes 2020). We remove the foreground stars from the GALEX far-UV up to Spitzer 24 𝜇 m images."]
  - software: sky.pro, PTS-7/8, Aniano et al. (2011) IDL convolution code, SWARP
  - parameter: 3-sigma clipping for sky; 1'' cross-match radius for NGC 6822 stars; target PSF 25'' (41''/43'' for NGC 1566 and NGC 6822); resampled pixel scale 25'', 43'' (NGC 1566), 82.5'' (NGC 6822, 200 pc), 29.7'' (Sextans A, 200 pc) [2.3.2 Foreground star removal: "Allowing a maximum separation of 1 ′′ between corresponding sources in both catalogues enables us to classify MW stars located along the line of sight of NGC 6822,"] [2.3.3 Image convolution and resampling: "For the cases of NGC 6822 and Sextans A, as an exception, we resample the convolved multi-wavelength images including TYPHOON data into the physical resolution of 200 pc per pixel (i.e., 82.5 ′′ and 29.7 ′′, respectively)."]
  - assumption: Schlafly & Finkbeiner (2011) dust reddening maps and Fitzpatrick et al. (2019) MW extinction curve; excluding SPIRE 500 um causes < 30% error in M_dust; regions with log M_dust > 3 give reliable dust masses [2.2.2 UV, optical, and IR photometric i…: "All photometric data are extinction corrected for foreground MW dust using dust reddening maps [13] from Schlafly & Finkbeiner (2011) and assuming the MW extinction curve of Fitzpatrick et al. (2019)."] [2.3 Image processing: "However, excluding these images still allows us to reliably estimate the interstellar 𝑀 dust of a system, with < 30% of error from the dust mass estimated using far-IR bands including 500 𝜇 m (Aniano et al. 2012)."]
  - validation: Verified that log M_dust > 3 threshold is exceeded for regions in NGC 6822 and Sextans A [2.3.3 Image convolution and resampling: "This threshold is exceeded for the regions in NGC 6822 and Sextans A considered in this work."]
- step 4: Model spatially resolved SEDs to derive dust mass, stellar mass, and SFR
  - method: Fit multi-wavelength FUV to 350 um photometry in each spaxel using modified MAGPHYS with adjusted prior ranges for sub-galactic regions [3.1 SED modelling: MAGPHYS: "We use the MAGPHYS (Multi-wavelength Analysis of Galaxy Physical Properties) framework (da Cunha et al. 2008; Battisti et al. 2019) to perform spectral energy distribution (SED) modelling and derive various physical properties in a spatially resolved manner, including the 𝑀 ★, SFR, and 𝑀 dust ."] [3.1 SED modelling: MAGPHYS: "Specifically, we modify the code to allow lower 𝑀 ★ (5 < log 𝑀 ★ / 𝑀 ⊙ < 11), SFR (-5 < log SFR/ 𝑀 ⊙ yr −1 < 1.5), dust luminosity (5 < log 𝐿 dust / 𝐿 ⊙ < 10), and 𝑀 dust (2 < log 𝑀 dust / 𝑀 ⊙ < 7)."]
  - software: MAGPHYS
  - parameter: Posterior ranges: 5 < log M_*/M_sun < 11, -5 < log SFR/(M_sun yr^-1) < 1.5, 5 < log L_dust/L_sun < 10, 2 < log M_dust/M_sun < 7; T_dust warm 30–70 K, cold 15–25 K [3.1 SED modelling: MAGPHYS: "The infrared libraries are built with a sum of three components: Polycyclic aromatic hydrocarbons (PAHs), warm dust components ( 𝑇 dust of 30–70 K), and cold dust components ( 𝑇 dust of 15–25 K)."] [3.1 SED modelling: MAGPHYS: "Specifically, we modify the code to allow lower 𝑀 ★ (5 < log 𝑀 ★ / 𝑀 ⊙ < 11), SFR (-5 < log SFR/ 𝑀 ⊙ yr −1 < 1.5), dust luminosity (5 < log L dust / 𝐿 ⊙ < 10), and 𝑀 dust (2 < log 𝑀 dust / 𝑀 ⊙ < 7)."]
  - assumption: Chabrier (2003) IMF, Bruzual & Charlot (2003) SPS, 0.2 < Z/Z_sun < 2, Charlot & Fall (2000) two-component dust attenuation, energy balance [3.1 SED modelling: MAGPHYS: "The code builds optical libraries assuming the Chabrier initial mass function (IMF; Chabrier 2003), the stellar population synthesis model from Bruzual & Charlot (2003), and metallicity range from 0.2 < 𝑍 / 𝑍 ⊙ < 2 at the given redshift."] [3.1 SED modelling: MAGPHYS: "The dust attenuation effect is accounted for by considering two components: the birth cloud (age less than 10 Myr) and the surrounding ISM (age more than 10 Myr), using the prescription from Charlot & Fall (2000)."]
  - fitting: Chi-squared minimization and Bayesian likelihood probability distribution functions (PDFs) [3.1 SED modelling: MAGPHYS: "The code then compares the modelled SED with the observed SED, calculates 𝜒 2, and finds the best-fit combination of models. The probability distribution functions (PDFs) are calculated for individual physical parameters based on the likelihood distribution from the Bayesian approach."]
  - validation: Exclude pixels with chi^2 > mu(chi^2) + 3*sigma(chi^2) and pixels where median(M_dust) / std(M_dust) < 1 [3.1 SED modelling: MAGPHYS: "We exclude pixels with calculated 𝜒 2 values larger than 𝜇 ( 𝜒 2 ) + 3 × 𝜎 ( 𝜒 2 ), where 𝜇 ( 𝜒 2 ) and 𝜎 ( 𝜒 2 ) are the median and standard deviation, of the obtained 𝜒 2 distributions of individual galaxies."] [3.1 SED modelling: MAGPHYS: "To achieve this, we calculate the ratio between the median 𝑀 dust and the standard deviation (averaging the 16% and 84% percentiles) and exclude pixels with a ratio smaller than 1."]
- limitation (authors): Only one galaxy (Sextans A) is probed in the low-metallicity regime, and CO is not detected in it. [5.1.1 Emission vs. absorption line meth…: "Nonetheless, the fact that molecular gas has not been factored into the total 𝑀 gas for these regions and that only one galaxy has been considered can be problematic when concluding."]
- limitation (authors): MAGPHYS assumes a fixed dust emissivity index, which can introduce systematic biases in M_dust without longer-wavelength data. [5.1.1 Emission vs. absorption line meth…: "However, MAGPHYS (and most SED modelling codes) assume a fixed dust emissivity index (i.e., the slope of the RJ tail), and this can introduce systematic biases on the resulting 𝑀 dust values in the absence of longer wavelength data (Galliano et al. 2018)."]
- limitation (authors): BEDE is a one-zone chemical and dust evolution model, which may not capture sub-galactic environmental variations (bars, spiral arms, local inflows/outflows) and suffers from parameter degeneracies (IMF, SN yield tables, k_frag vs SN_red). [5.2.3 Caveats on our dust evolution mod…: "This model comparison has caveats such as the dust evolution model we utilized assumes one-zone chemical and dust evolution. Thus, it may not be suitable for spatially resolved studies"]
- not stated (card): 3D-Barolo masking parameters and S/N threshold used when extracting CO moment 0 maps for NGC 625, NGC 1705, NGC 5253, NGC 6822, and NGC 7793; How the three ALMA 7m pointings/beams (upper, middle, lower) for NGC 6822 were mosaicked or combined; Exact Gaussian kernel widths used to convolve ALMA CO and interferometric HI maps (which have synthesized Gaussian beams rather than standard camera PSFs) …

### 2024A&A...681A..17D: ALMA detection of CO rotational line emission in red supergiant stars of the massive young star cluster RSGC1. Determination of a new mass-loss rate prescripti… (2024; evolved_stars, stellar_physics; observational_alma_primary)
- question: What are the gas mass-loss rates and wind velocities of red supergiants in the open cluster RSGC1 from ALMA CO(2-1) observations, and what new mass-loss rate prescription can be derived for red supergiants?
- step 2: Retrieve terminal wind velocities and CO gas mass-loss rates via non-LTE radiative transfer modelling
  - method: Model the CO(2-1) line profiles using the 1D non-LTE radiative transfer code GASTRoNOoM (multi-level approximate Newton-Raphson operator) and ray-trace with a 0.75 arcsec circular model beam to derive v_inf and Mdot_CO for the 5 detected R… [3.1. Radiative transfer analysis of the…: "To retrieve the stellar wind parameters from the CO(2-1) line profiles, we used the non-local thermodynamic equilibrium (non-LTE) radiative transfer code GASTR O NO O M (Decin et al. 2006) based on a multi-level approximate Newton-Raphson (ANR) operator."] [3.1. Radiative transfer analysis of the…: "When ray-tracing the modelled circumstellar envelope (CSE), we used a circular model beam with the same extraction aperture (of 0′′.75 diameter) to allow direct comparisons."]
  - software: GASTRoNOoM
  - parameter: 150 shells logarithmically spaced from R_star to R_out (R_out = 350 R_star for F01, F13; 400 R_star for F02; 600 R_star for F03, F04) [3.1. Radiative transfer analysis of the…: "The modelled CSEs were divided into 150 shells, evenly spaced on a logarithmic scale from the stellar radius (R⋆) out to the outer envelope radius."] [3.1. Radiative transfer analysis of the…: "These considerations yield a CO envelope radius of ∼350 R⋆ for F01 and F13, of ∼400 R⋆ for F02, and of ∼600 R⋆ for F03 and F04."]
  - parameter: Turbulent velocity v_turb = 3 km/s; wind velocity exponent beta = 0.5 (R_star to R_dust) and beta = 3 (beyond R_dust) [3.1. Radiative transfer analysis of the…: "For the region between R⋆ and Rdust, β is assumed to be 1/2 (Decin et al. 2006); for the region beyond Rdust we follow the general conclusions from Khouri et al. (2014), Decin et al. (2020), and Gottlieb et al. (2022) that the value of β should be larger to represent the slowly accelerating flow in oxygen-rich winds. …"]
  - assumption: Distance d = 6600 pc; gas kinetic temperature power law with epsilon = 0.6; silicate dust condensing at ~1750 K (R_dust = 3-4 R_star); gas-to-dust ratio r_gd = 200; all photospheric carbon locked in CO giving [CO/H] = 8.9e-5 [3.1. Radiative transfer analysis of the…: "Given a distance of 6 600 pc to RSGC1 and stellar radii between 7.55×1013 – 1.04×1014 cm, this translates into a CO envelope radius of 250 < Rout < 650 R⋆."] [3.1. Radiative transfer analysis of the…: "For the latter, we assume silicates (Decin et al. 2006) that start condensing at a temperature of ∼1750 K, which translates into a dust condensation radius, Rdust, of 3–4 R⋆. To get the local mean radiation field at each radial point in the grid, we calculate the dust radiation field for a canonical gas-to-dust ratio …"]
  - fitting: Forward modelling of uncontaminated CO line profile shape, width, two-horn separation, and peak flux; uncertainty propagation via individual parameter perturbation (Table D.1) and analytical relation Eq. 9 of De Beck et al. (2010) [3.1. Radiative transfer analysis of the…: "However, if the terminal velocity increases, so does the width of the full line profile and of the width between the two horns in spatially resolved, optically thin line profiles. We therefore have used all these characteristics together to determine v∞."] [Appendix D: Uncertainty estimate on CO(…: "Contrary to Díaz-Luis et al. (2019), we do not add the individual uncertainties in (unweighted) quadrature, but use a proper error propagation based on Eq. 9 of De Beck et al. (2010) which weighs the sensitivity of each individual uncertainty."]
  - validation: Compared observed CO outer radii against CO photodissociation predictions of Saberi et al. (2019); tested alternative v_LSR and v_inf fits in Appendix C. [3.1. Radiative transfer analysis of the…: "The observed ALMA CO envelope radius of the four RSGC1 sources F01, F02, F03, and F04 is only lower by a factor ∼1.1 – 1.8 compared to what Saberi et al. (2019) predicted, which is a remarkable agreement given the fact that the values for r1/2 and α were calculated for a standard Draine (1978) interstellar radiation f…"]
- result: CO(2-1) mass-loss rate Mdot_CO of F01 = 2.0 ± factor ~1.4 10^-6 M_sun/yr [Table 1: "F01 5.42+0.12 −0.13 3450±127 M5 1450 117.5 3 8 2.0(e) 5.57+2.37 −2.17 0.25 0.22"]
- result: Terminal wind velocity v_inf of F01 = 8 ± ±3 km s^-1 [Table 1: "F01 5.42+0.12 −0.13 3450±127 M5 1450 117.5 3 8 2.0(e) 5.57+2.37 −2.17 0.25 0.22"]
- result: CO(2-1) mass-loss rate Mdot_CO of F02 = 1.8 ± factor ~1.4 10^-6 M_sun/yr [Table 1: "F02 5.56+0.12 −0.13 3660±127 M2 1500 120.5 3 10 1.8 5.18+2.72 −1.75 0.18 0.20"]
- result: Terminal wind velocity v_inf of F02 = 10 ± ±3 km s^-1 [Table 1: "F02 5.56+0.12 −0.13 3660±127 M2 1500 120.5 3 10 1.8 5.18+2.72 −1.75 0.18 0.20"]
- result: CO(2-1) mass-loss rate Mdot_CO of F03 = 3.2 ± factor ~1.4 10^-6 M_sun/yr [Table 1: "F03 5.24+0.12 −0.13 3450±127 M5 1200 123.5 3 13 3.2(e) 4.18+3.08 −0.84 0.25 0.17"]
- result: Terminal wind velocity v_inf of F03 = 13 ± ±3 km s^-1 [Table 1: "F03 5.24+0.12 −0.13 3450±127 M5 1200 123.5 3 13 3.2(e) 4.18+3.08 −0.84 0.25 0.17"]
- result: CO(2-1) mass-loss rate Mdot_CO of F04 = 4.0 ± factor ~1.4 10^-6 M_sun/yr [Table 1: "F04 5.32+0.11 −0.13 3752±117 M1 1100 123.5 3 15 4.0 − 0.27 −"]
- result: Terminal wind velocity v_inf of F04 = 15 ± ±3 km s^-1 [Table 1: "F04 5.32+0.11 −0.13 3752±117 M1 1100 123.5 3 15 4.0 − 0.27 −"]
- result: CO(2-1) mass-loss rate Mdot_CO of F13 = 42 ± factor ~1.4 10^-6 M_sun/yr [Table 1: "F13 5.45+0.12 −0.13 3590±45 M3(d) 1430 123.5 4 22 42 − 1.9 −"]
- result: Terminal wind velocity v_inf of F13 = 22 ± ±3 km s^-1 [Table 1: "F13 5.45+0.12 −0.13 3590±45 M3(d) 1430 123.5 4 22 42 − 1.9 −"]
- result: Upper limit on Mdot_CO for undetected RSGC1 RSGs = 7e-7 ± not stated M_sun/yr [3.1 Radiative transfer analysis of the …: "an upper limit on the mass-loss rate of _∼_ 7 _×_ 10 _[−]_ [7] M _⊙_ /yr is derived"]
- limitation (authors): Small number statistics and sample bias towards the brightest/highest mass-loss RSGs in RSGC1 (only 5 of 14 RSGs detected in CO(2-1); Band 9 CO(6-5) was not observed, leaving only a single CO transition that cannot constrain the radial tem… [2. Observations and data reduction: "We requested observations at both band 9, centred on the CO v=0 J=6-5 rotational line transition and band 6, centred on the CO v=0 J=2-1 rotational line transition, but only the latter were obtained."]
- limitation (authors): ISM CO contamination affects the blue-shifted velocities of the line profiles, and total CO envelope sizes are sensitivity-limited lower limits. [2. Observations and data reduction: "As visible both in the CO(2-1) channel maps (Fig. C.3–Fig. C.7) and line profiles, there is contamination by interstellar medium (ISM) emission at specific frequencies; see the dashed regions in Fig. 1."]
- limitation (authors): Terminal wind velocities derived from line widths can be sensitivity-limited lower limits. [3.1. Radiative transfer analysis of the…: "We note that terminal wind velocities determined solely from the half line width at zero intensity might be lower limits since it was shown by Decin et al. (2018) that line widths are sensitivity limited, and hence that in some cases higher signal-to-noise data could indicate higher v∞ values, and hence higher M˙ CO v…"]
- not stated (card): CASA version used for calibration and imaging; Imaging task (e.g. clean vs tclean), deconvolution algorithm, visibility weighting scheme (e.g. Briggs robust parameter), cell size, and image dimensions; Exact velocity/channel ranges integrated to create the CO(2-1) and SiO v=3 J=5-4 zeroth moment maps for each individual target; Exact dust optical constants and grain size distribution used in GAST…

### 2021A&A...654A..90L: SUPER. V. ALMA continuum observations of z ∼ 2 AGN and the elusive evidence of outflows influencing star formation (2021; agn_and_quasars, high_z_galaxies, star_formation; observational_alma_primary)
- question: What is the impact of AGN ionised outflows on obscured and unobscured star formation in z ~ 2 AGN host galaxies?
- step 3: Fit UV-to-FIR SEDs and quantify AGN and synchrotron contributions to 260 um flux
  - method: Fit UV-to-FIR photometry including ALMA Band 7 fluxes using CIGALE to derive M_star, SFR, and AGN torus contribution at rest-frame 260 um; cross-check with F_870um/F_24um diagnostic, a modified black-body (MBB) torus model, and radio-extra… [3.4. SED fits including the ALMA flux d…: "We use the same SED fitting approach used by Circosta et al. (2018) for the full SUPER sample, with the only difference that we include the ALMA band 7 photometry."] [5.1. Origin of the FIR ALMA Band 7 emis…: "As an alternative approach, we model the torus emission using a modified black-body (MBB) following the methodology described by Lani et al. (2017)."]
  - software: CIGALE, AGNfitter
  - parameter: IR integration range = 8-1000 um; dust emissivity index beta = 1.8 for MBB test; radio spectral index alpha_r measured from 1.4/3/5.5/100 GHz data or fixed to -0.7 [3.4. SED fits including the ALMA flux d…: "The SFRs are estimated from the infra-red (IR) luminosity, obtained by integrating the best-fit template SED in the rest-frame wavelength range 8-1000 µm, after removing the AGN contribution."] [5.1. Origin of the FIR ALMA Band 7 emis…: "We note that this equation assumes optically thin dust and we assume a dust emissivity index β = 1.8 for this test."]
  - assumption: Kennicutt (1998) SFR calibration converted to Chabrier (2003) IMF by subtracting 0.23 dex; optically thin dust with beta = 1.8 for MBB test; no radio variability between frequencies [3.4. SED fits including the ALMA flux d…: "The IR luminosity is converted to SFR using the Kennicutt (1998) calibration, converted from a Salpeter IMF to a Chabrier (2003) IMF by subtracting 0.23 dex (Bolzonella et al. 2010) 7 ."]
  - fitting: Energy-balance SED fitting with CIGALE (Fritz et al. 2006 AGN models, Dale et al. 2014 SF templates) [3.4. SED fits including the ALMA flux d…: "Circosta et al. (2018) performed the panchromatic (UV-to-FIR) SED fitting using the Code Investigating GALaxy Emission (CIGALE ; Burgarella et al. 2005; Noll et al. 2009; Boquien et al. 2019)."]
  - validation: Tested excluding ALMA Band 7 from CIGALE fit (<3% change in AGN contribution), fitting with AGNfitter (<7% AGN contribution), MBB torus model, and extreme synchrotron slope alpha_r = 0. [5.1. Origin of the FIR ALMA Band 7 emis…: "We test that excluding the ALMA points from the SED fit, the inferred AGN contributions vary by less than 3%. Additionally, we test that using a difference SED fitting code (AGNfitter, Calistro Rivera et al. 2016), the AGN contributions remain small (< 7%)."] [5.1 Origin of the FIR ALMA Band 7 emiss…: "excluding the ALMA points from the SED fit, the inferred AGN contributions vary by less than 3%. Additionally, we test that using a difference SED fitting code (AGNfitter, Calistro Rivera et al. 2016), the AGN contributions remain small"]
- result: AGN-heated dust contribution to rest-frame 260 um flux density (high S/N sample) = <= 4 ± not stated % [abstract: "From spectral energy distribution (SED) fitting, we find that the main contribution to the 260 µm flux density is dust heated by star formation, with ≤ 4% contribution from AGN-heated dust and ≤ 1% from synchrotron emission."]
- limitation (authors): The ALMA sample is biased towards heavily X-ray obscured (log N_H > 22), optical Type 2 AGN, and the upper end of the SFR distribution of the SUPER parent sample because of the FIR pre-selection. [2. Sample: "In summary, although the ALMA sample presented in this paper has bolometric luminosities which are representative of the parent sample, we are biased towards heavily obscured (high N H ) and Type 2 targets."]
- limitation (authors): Two of the eight targets (cid_1057 and cid_451) have low ALMA peak S/N (3.6 and 5.9), which is insufficient for reliable size measurements and spatially resolved analysis. [abstract: "The other two targets were detected with S/N of 3.6 and 5.9, which are insufficient for spatially resolved analysis."]
- limitation (authors): High-resolution ALMA observations (~0.2") may resolve out diffuse, extended FIR emission. [3.3.2. Flux densities: "Our high-resolution ALMA images are potentially missing some of the more diffuse emission, and therefore the measured flux densities cannot be considered as ‘total’ flux densities."]
- not stated (card): Exact frequency and bandwidth of the 4 spectral windows in ALMA Band 7 continuum setup; Image size (imsize) and deconvolver parameter in CASA tclean; Masking strategy used during tclean (e.g. auto-multithresh, manual clean boxes, or unmasked cleaning to 2xRMS); Whether primary beam correction was applied to the final cleaned images used for image-plane flux measurements

### 2020MNRAS.498.1319M: Insights into the planetary dynamics of HD 206893 with ALMA (2020; debris_disks, exoplanets; observational_alma_primary)
- question: What is the radial structure of the HD 206893 debris disc (is there a gap, asymmetry, CO gas, dust around the brown dwarf B), and what does it imply for the dynamics of the companions?
- step 4: Upper limit on dust around the brown dwarf B
  - method: Search for a point source at the expected BD position; 3 sigma flux limits converted to dust mass with radiative transfer [2.1.2 BD dust emission upper limit: "Nevertheless, we can place $3\sigma$ upper limits at 0.88 and 1.3 mm of 27 and 15 $\mu$Jy, respectively."] [2.1.2 BD dust emission upper limit: "Using the same radiative transfer tools as in (cite: Perez2019protolunar), we estimate a dust mass upper limit"]
  - parameter: BD expected at ~0.25'' separation towards the NE [2.1.2 BD dust emission upper limit: "We do not detect any emission arising from a point source towards the NE at the BD separation of $\sim0.25\ensuremath{''}$"]
  - parameter: Dust accretion rate onto BD from the debris disc ~4 kg/s using Bonsor et al. 2018 with corrected K_ej = 5.14e8 [2.1.2 BD dust emission upper limit: "We find that the BD could be accreting $\mu$m-sized dust at a rate of $\sim4$ kg s$^{-1}$."] [Footnote 5: "There is a typo in Table 1 in (cite: Bonsor2018) where $K_\mathrm{ej}$ should be $5.14\times10^{8}$ (private communication with Amy Bonsor)."]
  - assumption: Disc size >~0.1 au (a smaller, optically thick disc could hide more mass) [2.1.2 BD dust emission upper limit: "which is equivalent to a dust to planet ratio of $5\times10^{-8}$ for a disc with a size $\gtrsim0.1$ au"]
  - assumption: Accreted dust: 1 um radius grains, 3 g/cm3, accreted for 700 Myr [2.1.2 BD dust emission upper limit: "Assuming the accreted dust is all made of grains of 1 $\mu$m in radius, have a density of 3 g cm$^{-3}$, and have been accreted for 700 Myr"]
- step 6: Fit parametric gap disc model to visibilities
  - method: Two-power-law surface density with Gaussian gap, radiative transfer with RADMC-3D, MCMC fit in visibility space [3 Parametric axisymmetric disc model: "we fit a parametric disc model with a gap as in (cite: Marino2018hd107; Marino2019), combining radiative transfer simulations (cite: radmc3d) and an MCMC fitting procedure in the visibility space."]
  - software: RADMC-3D
  - parameter: Gap depth fixed to 1 [3 Parametric axisymmetric disc model: "here we fixed the gap depth to 1 (i.e. the surface density is zero at $r_\mathrm{g}$)"]
  - parameter: Vertical extent fixed to 5% of radius, uniform vertical mass distribution [3 Parametric axisymmetric disc model: "We thus choose to fix the vertical extent of the disc to 5% of the radius and use a uniform vertical mass distribution"]
  - parameter: r_min lower limit of 14 au; outer edge fixed at 250 au [3 Parametric axisymmetric disc model: "we impose a lower limit for $r_{\min}$ of 14 au"] [3 Parametric axisymmetric disc model: "we set a fixed outer edge of 250 au"]
  - parameter: Free parameters include disc inclination and PA, phase centre offsets, and position, size (2D Gaussian) and flux of a background SMG ~11.5'' to the SW; spectral index alpha free and uniform [3 Parametric axisymmetric disc model: "we also fit the disc inclination $i$ and position angle PA, and nuisance parameters such as phase center offsets, and the position, size (modelled as a 2D gaussian) and flux of a SMG"] [3 Parametric axisymmetric disc model: "which we leave as a free parameter that is uniform across the disc"]
  - parameter: Reported values are posterior medians with 16th and 84th percentile uncertainties [Table 1: "The quoted values correspond to the median, with uncertainties based on the 16th and 84th percentiles of the marginalised distributions."]
  - assumption: Dust mass counts only grains smaller than 1 cm, set by assumed opacities [3 Parametric axisymmetric disc model: "Note that this dust mass only includes the mass in grains smaller than 1 cm, which is set by the assumed dust opacities (cite: Marino2019)."]
  - assumption: Star modelled with Teff = 6500 K and R = 1.3 Rsun template spectrum [3 Parametric axisymmetric disc model: "The star is modelled with a template spectrum corresponding to an effective temperature of 6500 K and a radius of 1.3 $R_\odot$"]
  - fitting: MCMC in visibility space; sampler, priors and likelihood not stated [3 Parametric axisymmetric disc model: "an MCMC fitting procedure in the visibility space"]
  - validation: Residual maps show no residuals above 3 sigma within 200 au; model without a gap fails to reproduce visibility wiggles beyond 50 klambda [3.1 Results: "We do not find any residuals stronger than $3\sigma$ within 200 au."] [3.1 Results: "The model without a gap fails to reproduce the amplitude of the wiggles beyond 50 k$\lambda$."]
- result: 3 sigma upper limit on point-source flux at BD, 0.88 mm = 27 ± not stated uJy [2.1.2 BD dust emission upper limit: "we can place $3\sigma$ upper limits at 0.88 and 1.3 mm of 27 and 15 $\mu$Jy, respectively"]
- result: 3 sigma upper limit on point-source flux at BD, 1.3 mm = 15 ± not stated uJy [2.1.2 BD dust emission upper limit: "we can place $3\sigma$ upper limits at 0.88 and 1.3 mm of 27 and 15 $\mu$Jy, respectively"]
- result: Dust mass upper limit around B = 2e-4 ± not stated Earth masses [2.1.2 BD dust emission upper limit: "we estimate a dust mass upper limit of $2\times10^{-4}$ M$_\oplus$ ($2\times10^{-2}$ $M_\mathrm{moon}$)"]
- result: Total dust mass M_d = 0.031 ± 0.002 Earth masses [Table 1: "$0.031\pm0.002$ | total dust mass"]
- result: Disc inner radius r_min = 28 ± +5/-8 au [Table 1: "$28_{-8}^{+5}$ | disc inner radius"]
- result: Disc peak radius r_c = 114 ± +7/-5 au [3.1 Results: "we find that the disc dust density peaks at $r_\mathrm{c}=114^{+7}_{-5}$ au"]
- result: Inner surface density slope gamma_1 = 0.8 ± +-0.4 dimensionless [3.1 Results: "the surface density must increase moderately as $r^{0.8\pm0.4}$"]
- result: Outer surface density slope gamma_2 = -3.9 ± +0.5/-0.6 dimensionless [3.1 Results: "Exterior to that the disc surface density declines steeply as $r^{-3.9\pm0.5}$."]
- result: Gap centre radius r_g = 74 ± 3 au [3.1 Results: "we find that the gap center is well constrained to $74\pm3$ au"]
- result: Gap width w_g (FWHM) = 27 ± 5 au [3.1 Results: "The gap width is constrained to $27\pm5$ au."]
- result: Disc inclination from face-on = 40 ± 3 deg [3.1 Results: "The disc orientation is well constrained with $i=40\pm3\ensuremath{^\circ}$ and PA$=61\pm4\ensuremath{^\circ}$."]
- result: Disc position angle = 61 ± 4 deg [3.1 Results: "The disc orientation is well constrained with $i=40\pm3\ensuremath{^\circ}$ and PA$=61\pm4\ensuremath{^\circ}$."]
- result: Disc spectral index alpha (Table 1) = 2.54 ± 0.17 dimensionless [Table 1: "$2.54\pm0.17$ | disc spectral index"]
- result: Disc spectral index alpha (text value, differs slightly from Table 1) = 2.53 ± 0.16 dimensionless [3.1 Results: "The disc spectral index is found to be $2.53\pm0.16$"]
- result: Background SMG integrated flux at 0.88 mm = 1.5 ± not stated mJy [3.1 Results: "has an integrated flux of 1.5 mJy at 0.88 mm and 0.24 mJy at 1.3 mm"]
- limitation (authors): Planet mass assumes the gap is empty at its centre; a shallower, broader gap would change the inferred width and mass [3.1 Results: "A caveat in this interpretation is that we have assumed the gap is empty at its center."]
- limitation (authors): Frankenstein profiles lack a primary beam correction [2.1.1 Dust radial structure: "no primary beam correction is taken into account"]
- limitation (authors): Lower S/N makes gap width and depth comparison with other discs difficult [5.4 Are gaps common among exoKuiper bel…: "Given the lower S/N in HD 206893 observations, it is hard to compare the gap width and depth with the other two."]
- not stated (card): tclean parameters other than weighting and taper: deconvolver, cell size, image size, mask, threshold, niter; How the ACA and 12m data were combined for imaging and for the visibility fit (joint tclean or separate datasets); Which spectral windows were used for the continuum images, and whether the line window was flagged; Flux calibrator and calibrator-derived flux scale for each execution block…

### 2024ApJ...977..190X: Constraining the Excitation of Molecular Gas in Two Quasar-starburst Systems at z ∼ 6 (2024; agn_and_quasars, high_z_galaxies, star_formation; multi_facility_alma_minor)
- question: Constrain molecular gas excitation mechanisms, dust heating and star formation in two FIR luminous, less UV luminous quasars.
- step 3: Fit J2054-0005 dust and AGN emission
  - method: Fit Gτ-MBB plus each CAT3D template; select smallest χ² template; refine dust and torus normalization parameters. [Continuum Emission: "First, we separately fit the SED by combining the G$\tau$-MBB model with each torus template from the CAT3D model."] [Continuum Emission: "We identified the optimal torus template by choosing the one with the smallest $\chi^2$ value."]
  - software: lmfit, CAT3D
  - parameter: Fixed dust continuum size 0.9 × 0.7 kpc². [Continuum Emission: "using the dust continuum size ($0.9 \times 0.7 \, \rm kpc^2$) measured in (cite: Venemans2020) as a non-fitting parameter."]
  - parameter: L_TIR integrated over 8–1000 μm; L_FIR over 42.5–122.5 μm. [Continuum Emission: "$L_{\rm TIR}$ refers to the luminosity integrated from 8 to 1000 $\rm \mu m$, while $L_{\rm FIR}$ is integrated over the range from 42.5 to 122.5 $\rm \mu m$ (cite: Helou1985)."]
  - assumption: κν = κ0 (ν/ν0)^β; κ0 = 0.77 cm² g−1 at 353 GHz. [Continuum Emission: "$\kappa_{\nu} = \kappa_0 (\frac{\nu}{\nu_0})^{\beta}$ is the frequency-dependent dust opacity."] [Continuum Emission: "we adopt $\kappa_0 = 0.77\, \rm cm^2 \, g^{-1}$ at $\nu_0 = 353\, \rm GHz$"]
  - assumption: Include CMB dust heating. [Continuum Emission: "The dust heating from the cosmic microwave background (CMB) at the quasar redshift with a temperature of $T_{\rm CMB}(z)$ is also taken into account (cite: DaCunha2013)."]
  - assumption: ΛCDM: H0 = 70 km s−1 Mpc−1, Ωm = 0.3, ΩΛ = 0.7. [Introduction: "Throughout this work, we adopt a $\Lambda$CDM cosmology with $H_0 = 70 \rm \; km\, s^{-1}\, Mpc^{-1}$, $\Omega_{m}$=0.3, and $\Omega_{\Lambda}$=0.7."]
  - fitting: lmfit; free torus scale k_t, dust temperature, dust mass and β; torus shape selected from templates. [Continuum Emission: "using the Python lmfit package."] [Continuum Emission: "our free parameters included the torus component scale factor, $k_{\rm t}$, the torus SED shape determined by the selected template, along with the dust temperature $T_{\rm dust}$, dust mass $M_{\rm dust}$, and emissivity index $\beta$."]
  - validation: Compare fitted dust temperature and β with Hashimoto2019. [Continuum Emission: "While their $T_{\rm dust}$ is similar to ours, they found a lower $\beta$, which can be attributed to their assumption of thin optical depth and the limited number of data points used in their fit."]
- step 4: Fit J0129-0035 dust and derive SFRs
  - method: Fit dust mass with fixed temperature, β and size; derive TIR luminosity and SFR; vary temperature and β to assess sensitivity. [Continuum Emission: "Therefore, during our fitting procedure, the free parameter to fit is the dust mass $M_{\rm dust}$."] [Continuum Emission: "we also show the SED models adopting different values of $\beta$ and $T_{\rm dust}$"]
  - parameter: β = 1.6; T_dust = 47 K; dust continuum size 1.2 × 1.0 kpc². [Continuum Emission: "We adopted the graybody with $\beta = 1.6$ and $T_{\rm dust}= 47 \, \rm K$ that was often assumed in the previous optically thin model (cite: Beelen2006; Venemans2020)."] [Continuum Emission: "We use the size of the dust continuum ($1.2\times 1.0 \, \rm kpc^2$) measured in (cite: Venemans2020) as the galaxy size."]
  - assumption: Kroupa IMF; SFR_IR/(M⊙ yr−1) = 3.88 × 10−44 L_TIR/(erg s−1). [Continuum Emission: "Adopting a Kroupa IMF and the scaling relation ${\rm SFR_{\rm IR}} /({\rm M_{\odot}\, yr^{-1}})= 3.88 \times 10^{-44} L_{\rm TIR}/(\rm erg \, s^{-1})$ from (cite: Murphy2011)"]
  - assumption: J0129-0035 SFR is an upper limit because AGN contribution is unknown. [Continuum Emission: "However, due to the unknown AGN contribution, we considered this an upper limit for the real SFR."]
  - fitting: Only M_dust free for the adopted J0129-0035 SED shape. [Continuum Emission: "Therefore, during our fitting procedure, the free parameter to fit is the dust mass $M_{\rm dust}$."]
  - validation: Test T_dust = 40 and 70 K; at 40 K vary β from 1.5 to 2.2. [Continuum Emission: "with $T_{\rm dust}$ fixed to $40\rm \, K$, we obtained dust mass of $M_{\rm dust} = (6.1 \pm 0.2)\times 10^8 \rm \, M_{\odot}$, while with $T_{\rm dust} = 70 \rm \, K$"] [Continuum Emission: "fixed $T_{\rm dust}$ to $40\rm \, K$ and changed $\beta$ from 1.5 to 2.2"]
- result: J2054-0005 dust emissivity index β = 2.17 ± ± 0.09 dimensionless [Continuum Emission: "the G$\tau$-MBB model yielded parameters of $\beta = 2.17 \pm 0.09$"]
- result: J2054-0005 dust temperature = 52 ± ± 1 K [Continuum Emission: "a dust temperature $T_{\rm dust} = 52 \pm 1 \, \rm K$"]
- result: J2054-0005 dust mass = 1.3 × 10^8 ± ± 0.2 × 10^8 M⊙ [Continuum Emission: "a dust mass $M_{\rm dust} = (1.3 \pm 0.2) \times 10^8 \, M_{\odot}$."]
- result: J2054-0005 total infrared luminosity excluding AGN torus = 6.0 × 10^12 ± ± 1.1 × 10^12 L⊙ [Continuum Emission: "Our calculated total infrared luminosity is $L_{\rm TIR} = 6.0 \pm 1.1 \times 10^{12} \, \rm L_{\odot}$, which does not include the torus component heated by AGN."]
- result: J2054-0005 SFR = 896 ± ± 163 M⊙ yr−1 [Continuum Emission: "we estimated the SFR to be $896 \pm 163 \, \rm M_{\odot} \, yr^{-1}$"]
- result: J0129-0035 TIR luminosity with T_dust = 47 K and β = 1.6 = 4.9 × 10^12 ± ± 0.4 × 10^12 L⊙ [Continuum Emission: "With this assumption, we measured the TIR luminosity to be $L_{\rm TIR} = (4.9 \pm 0.4) \times 10^{12} \rm \, L_{\odot}$"]
- result: J0129-0035 dust mass with T_dust = 47 K and β = 1.6 = 3.9 × 10^8 ± ± 0.1 × 10^8 M⊙ [Continuum Emission: "the dust mass to be $M_{\rm dust} = (3.9 \pm 0.1)\times 10^8 \rm \, M_{\odot}$."]
- result: J0129-0035 SFR, considered an upper limit = 733 ± ± 59 M⊙ yr−1 [Continuum Emission: "The SFR estimated from $L_{\rm TIR}$ is $733 \pm 59\, \rm M_{\odot}\, yr^{-1}$."]
- result: J0129-0035 dust mass with T_dust = 40 K = 6.1 × 10^8 ± ± 0.2 × 10^8 M⊙ [Continuum Emission: "with $T_{\rm dust}$ fixed to $40\rm \, K$, we obtained dust mass of $M_{\rm dust} = (6.1 \pm 0.2)\times 10^8 \rm \, M_{\odot}$"]
- limitation (authors): J2054-0005 CO (8-7) and (10-9) linewidths have large fitting uncertainties. [J2054-0005: "The spectra of CO (8-7) and (10-9) have lower S/N compared to that of the other two transitions and the line widths determined by the fitting suffer large uncertainties."]
- limitation (authors): J0129-0035 lacks Herschel data near the dust peak; temperature and derived quantities depend strongly on assumptions. [Continuum Emission: "For J0129-0035, due to the lack of Herschel data at the dust emission peak, $T_{\rm dust}$ has significant uncertainty."]
- limitation (authors): J2054-0005 torus/dust decomposition has degeneracy and uncertainty. [Continuum Emission: "This method, despite its inherent degeneracy and uncertainty, was aimed primarily at quantifying the AGN’s relative contribution without needing to fit the torus’s specific parameters precisely."]
- not stated (card): ALMA calibration, imaging and measurement extraction procedures must be recovered from the cited source papers.; Mapping of project 2018.1.01289.S to specific ALMA targets and measurements.; Exact NOEMA line-free channels and imaging cell size, image size, masks and cleaning stopping criterion.; Line-profile MCMC sampler, prior widths and distributions, chain lengths, burn-in and convergence chec…

### 2015ApJ...800...70S: ALMA Imaging of HCN, CS, and Dust in Arp 220 and NGC 6240 (2015; nearby_galaxies, astrochemistry; observational_alma_primary)
- question: What are the ISM masses, nuclear disk kinematics and dense-gas excitation conditions in the nuclei of Arp 220 and NGC 6240, from ALMA dust continuum and HCN/CS imaging?
- step 3: Derive ISM masses from RJ dust continuum
  - method: Eq. 4 RJ-correction and empirical alpha_850um mass-flux relation using 347.6 GHz fluxes for Arp 220 and 693.5 GHz for NGC 6240 [Table 4: "ISM masses derived from the RJ continuum flux using Equation 4 with distances of 74 and 103 Mpc for Arp 220 and NGC 6240."]
  - parameter: Td = 100 K (Arp 220), 25 K (NGC 6240); beta = 1.8 [4. LONG WAVELENGTH DUST CONTINUUM AS A …: "For the Arp 220 nuclei we therefore use the 350 GHz fluxes and adopt T _d_ = 100 K."]
  - assumption: Optically thin dust, empirical dust-opacity/gas-to-dust absorbed in alpha_850um, uniform spherical/disk distribution for column density [4. LONG WAVELENGTH DUST CONTINUUM AS A …: "assuming a uniform, spherical distribution of ISM (see Table 4)."]
  - validation: Compared with CO-based masses; uncertain by factor of at most 2 [4. LONG WAVELENGTH DUST CONTINUUM AS A …: "we expect these estimates to be uncertain by a factor of at most 2 for the nuclear"]
- result: ISM mass Arp 220 East = 1.9e9 ± factor of at most 2 Msun [Table 4: "Arp 220 East 347.6 161 100 0.917 1.9"]
- result: ISM mass Arp 220 West = 4.2e9 ± factor of at most 2 Msun [Table 4: "Arp 220 West 347.6 342 100 0.917 4.2"]
- result: ISM mass NGC 6240 = 1.6e9 ± factor of at most 2 Msun [abstract: "1.6 _×_ 10 [9] M _⊙_ within radii of 69, 65 and 190 pc."]
- limitation (authors): Single dust temperature adopted; dust temperature not derivable from the data; masses uncertain by factor of 2. [4. LONG WAVELENGTH DUST CONTINUUM AS A …: "A good derivation of the dust temperature from the observations would require multiple spectral bands"]
- limitation (authors): Only ~15% of single-dish flux recovered in NGC 6240. [3.1. Continuum: "Here, the detected percentages are only _∼_ 15%."]
- not stated (card): Imaging parameters (tclean/clean weighting, robust, cell, image size, masks, deconvolver); CASA version and self-calibration solution intervals/reference antennas; Flux calibrator and bandpass/phase calibrators; Line-free channel ranges and polynomial order for continuum subtraction; Chi-square minimization algorithm details and uncertainties on disk model parameters (Table 5); Radial binning/ape…

### 2018MNRAS.475..448T: Mapping jet-ISM interactions in X-ray binaries with ALMA: a GRS 1915+105 case study (2018; milky_way_ism, star_formation; observational_alma_primary)
- question: Is IRAS 19132+1035 a site of interaction between the GRS 1915+105 jet and the ISM, and what do the molecular lines say about ISM conditions and jet power?
- step 2: Fit modified blackbody to SED for dust properties
  - method: MCMC fit of 22–1110 um spectrum with modified blackbody; ALMA flux excluded [4.1 Continuum Emission: "we fit (using a Markov Chain Monte Carlo (MCMC) algorithm) the broad-band sub-mm through IR (22–1110 $\mu$m; see Table [1](#table:mwemiss)) spectrum"]
  - assumption: kappa=0.1 cm2/g (nu/THz)^beta, includes gas-to-dust 100 [4.1 Continuum Emission: "Note that this value of the dust opacity includes a gas-to-dust ratio of 100 by mass."]
  - fitting: MCMC; priors not stated [Results, Continuum Emission from IRAS 1…: "we fit (using a Markov Chain Monte Carlo (MCMC) algorithm) the broad-band sub-mm through IR (22–1110 $\mu$m; see Table [1](#table:mwemiss)) spectrum, with the modified black-body function"]
- result: Dust temperature = 29.01 ± +0.14/-0.13 K [Table 2: "| $T_{\rm dust}$ | | $29.01^{+0.14}_{-0.13}$ | K |"]
- result: Dust emissivity index beta = 1.44 ± +0.03/-0.03 dimensionless [Table 2: "| $\beta$ | | $1.44^{+0.03}_{-0.03}$ | |"]
- result: Molecular mass from dust = 1200 ± +690/-450 Msun [Table 2: "| $M_{\mathrm{mol}}^a$ | | $1200^{+690}_{-450}$ | $M_\odot$ |"]
- limitation (authors): Distance mismatch between GRS 1915+105 and IRAS source; jet power assumes constant power and density [5.4 Constraints on jet properties: "We have also assumed a constant external density."]
- limitation (authors): ALMA continuum lacks single-dish data so flux is underestimated [4.1 Continuum Emission: "we do not recover all the flux from the region in these ALMA continuum observations"]
- not stated (card): Line-free channels and continuum velocity ranges for each line; Channel width/velocity resolution and cube spectral regridding used in final imaging; Clean thresholds, mask, and number of iterations; Final synthesized beams and rms noise per cube; Gaussian fit and MCMC setup (priors, sampler, walkers) for SED and line fits; Regions A-D coordinates and extraction apertures; Manual calibration deta…

### 2020ApJ...891..164S: Chemistry and Physics of a Low-metallicity Hot Core in the Large Magellanic Cloud (2020; astrochemistry, star_formation; observational_alma_primary)
- question: What are the chemical composition, physical structure and sulfur isotope ratios of a newly discovered hot molecular core around the high-mass YSO ST16 in the LMC, and how do its abundances compare with other LMC and Galactic hot cores?
- step 4: Derive H2 column density
  - method: Optically thin dust continuum at 870 and 1200 um; SED fits (Robitaille, Zhang & Tan); 9.7 um silicate depth; average adopted [4.3.4: "we use $N_{\mathrm{H_2}}$ = (5.6 $\pm$ 0.6) $\times$ 10$^{23}$ cm$^{-2}$ as a representative value"]
  - parameter: Td = 20, 60, 150 K tested; 60 K adopted [4.3.1: "We estimate $N_{\mathrm{H_2}}$ for three different dust temperatures, 20 K, 60 K, and 150 K"]
  - assumption: Dust-to-gas mass ratio 0.0027 (0.008 scaled by LMC Z~1/3); NH2/AV = 2.8e21; distance = LMC [4.3.1: "We use the dust-to-gas mass ratio of 0.0027 for the LMC, which is obtained by scaling the Galactic value of 0.008"]
  - fitting: SED: chi2 cutoff (chi2-chi2best)/Ndata<=3 median; best five Zhang&Tan models averaged [4.3.2: "We select the fit results which have $(\chi^2 - \chi^2_{best})/N_{data}$ $\leqq$ 3"]
  - validation: Consistency among methods [4.3.4: "consistent $N_{\mathrm{H_2}}$ values are obtained by different methods"]
- step 7: Astrochemical simulations
  - method: Gas-grain model with cold (1e5 yr, AV 1-5 mag), warm-up (5e4 yr, to 150 K, 6e6 cm-3, AV 100) and post-warm-up (1e5 yr) stages; LMC vs Galactic [Appendix: "The warm-up stage continues up to $t_h = 5 \times 10^4$ years in our model."]
  - assumption: LMC: Z=1/3, gas-to-dust 300, chi_uv=3 [Table 10: "Gas to dust ratio | 100 (MW), 300 (LMC)"]
- result: NH2 adopted = 5.6e23 ± 0.6e23 cm-2 [4.3.4: "we use $N_{\mathrm{H_2}}$ = (5.6 $\pm$ 0.6) $\times$ 10$^{23}$ cm$^{-2}$ as a representative value"]
- result: Gas number density = 3e6 ± not stated cm-3 [4.3.4: "we estimate the average gas number density to be $n_{\mathrm{H_2}}$ = 3 $\times$ 10$^6$ cm$^{-3}$ and the total gas mass to be 100 M$_{\ensuremath{\odot}}$"]
- result: Continuum 870 um = 10.55 ± 1.06 mJy/beam [4.3.1: "(10.55 $\pm$ 1.06) mJy/beam for 870 $\mu$m"]
- result: Continuum 1200 um = 3.37 ± 0.34 mJy/beam [4.3.1: "(3.37 $\pm$ 0.34) mJy/beam for 1200 $\mu$m"]
- limitation (authors): Infall not detected because no optically thick tracer; NH2 includes low-temperature components [5.5: "an infall motion is not seen in the present data, because we do not cover a fully optically thick molecular tracer in this work"]
- not stated (card): Line-free channel ranges for continuum and uvcontsub fit order; Image size, cell size, clean threshold, mask, niter; Which calibration pipeline version / manual scripts; Source spectral extraction aperture relative to line-fit method details (Gaussian fit software); Rotation-diagram fitting method and treatment of blends; Details of SED photometry compilation and fitting grid; Chemical network co…

### 2026ApJ...998..277M: ALMA Observations of Cold Methanol Gas in the Large Magellanic Cloud: N79 South Giant Molecular Cloud (2026; astrochemistry, star_formation, nearby_galaxies; observational_alma_primary)
- question: Investigate the physical and chemical properties, molecular abundances, and origin of cold CH$_3$OH gas in two dense molecular cloud cores (N79S-1 and N79S-2) offset from the SSC candidate H72.97-69.39 in the low-metallicity N79 region of …
- step 5: Derive H2 column densities, gas densities, masses, visual extinctions, and relative molecular abundances
  - method: Compute N(H2) from optically thin 0.87 mm dust continuum emission at T_d = 10, 13/15, and 20 K (averaging 10 K and 20 K values as final N(H2)), derive n(H2), gas mass, and A_V assuming a 0.1 pc spherical geometry, and divide molecular colu… [Column Density of H$_2$: "The H$_2$ column density ($N_{H_2}$) is estimated from the optically thin dust continuum emission using the following equation:"] [Column Density of H$_2$: "Assuming a source diameter of 0.1 pc and a spherical distribution of gas, the gas density and visual extinction are derived to be $n_{\mathrm{H_2}} = 1.85 \times 10^6$ cm$^{-3}$ and $A_V \sim 128$ mag for N79S-1, and $n_{\mathrm{H_2}} = 3.59 \times 10^6$ cm$^{-3}$ and $A_V \sim 196$ mag for N79S-2."]
  - parameter: kappa_nu = 1.89 cm^2 g^-1 at 0.87 mm [Column Density of H$_2$: "We use 0.87 mm (344.72671 GHz) continuum emission data and the mass absorption coefficient of 1.89 cm$^2$ g$^{-1}$ for 0.87 mm, assuming the Mathis-Rumpl-Nordsieck or MRN distribution with thin ice mantles at a gas density of 10$^5$ cm$^{-3}$ (cite: osse94)."]
  - parameter: Dust-to-gas mass ratio Z = 0.0027 and mean atomic mass per hydrogen mu = 1.41 [Column Density of H$_2$: "Here we use $\mu$ = 1.41 (cite: Cox00). In this work, we use the dust-to-gas mass ratio of 0.0027, which is derived from scaling the Galactic value of 0.008 by the metallicity of the LMC ($\sim$1/3 Z$\odot$) (cite: bern08)."]
  - assumption: Optically thin dust continuum emission and thermal coupling between gas and dust (T_d = 10-20 K) [Column Density of H$_2$: "The H$_2$ column density ($N_{H_2}$) is estimated from the optically thin dust continuum emission using the following equation:"] [Column Density of H$_2$: "Therefore, in the present source, we can consider gas and dust as thermally coupled."]
  - assumption: Spherical gas distribution with 0.1 pc diameter [Column Density of H$_2$: "Assuming a source diameter of 0.1 pc and a spherical distribution of gas, the gas density and visual extinction are derived to be $n_{\mathrm{H_2}} = 1.85 \times 10^6$ cm$^{-3}$ and $A_V \sim 128$ mag for N79S-1, and $n_{\mathrm{H_2}} = 3.59 \times 10^6$ cm$^{-3}$ and $A_V \sim 196$ mag for N79S-2."]
  - validation: Evaluated sensitivity of N(H2) to dust temperature between 10 K and 20 K [Column Density of H$_2$: "The calculated value of $N_{H_2}$ changes by a factor of approximately 3 when the dust temperature is adjusted from 10 K to 20 K."]
- result: H2 column density N_H2 (N79S-1) = 3.8e23 ± 2.0e23 cm^-2 [Table 3 notes: "In this study, we use $N_{H_2}$ = (3.8$\pm$2.0)$\times$ $10^{23}$ cm$^{-2}$ for N79S-1"]
- result: H2 column density N_H2 (N79S-2) = 7.4e23 ± 4.0e23 cm^-2 [Table 3 notes: "and $N_{H_2}$ = (7.4$\pm$4.0)$\times$ $10^{23}$ cm$^{-2}$ N79S-2 as a typical value"]
- result: H2 volume density n_H2 (N79S-1) = 1.85e6 ± not stated cm^-3 [Column Density of H$_2$: "Assuming a source diameter of 0.1 pc and a spherical distribution of gas, the gas density and visual extinction are derived to be $n_{\mathrm{H_2}} = 1.85 \times 10^6$ cm$^{-3}$ and $A_V \sim 128$ mag for N79S-1, and $n_{\mathrm{H_2}} = 3.59 \times 10^6$ cm$^{-3}$ and $A_V \sim 196$ mag for N79S-2."]
- result: H2 volume density n_H2 (N79S-2) = 3.59e6 ± not stated cm^-3 [Column Density of H$_2$: "Assuming a source diameter of 0.1 pc and a spherical distribution of gas, the gas density and visual extinction are derived to be $n_{\mathrm{H_2}} = 1.85 \times 10^6$ cm$^{-3}$ and $A_V \sim 128$ mag for N79S-1, and $n_{\mathrm{H_2}} = 3.59 \times 10^6$ cm$^{-3}$ and $A_V \sim 196$ mag for N79S-2."]
- result: Total gas mass (N79S-1) = 67 ± not stated M_sun [Physical Properties of N79S-1 and N79S-…: "The H$_2$ density corresponds to a total gas mass of 67 M$\odot$ for N79S-1 and 131 M$\odot$ for N79S-2."]
- result: Total gas mass (N79S-2) = 131 ± not stated M_sun [Physical Properties of N79S-1 and N79S-…: "The H$_2$ density corresponds to a total gas mass of 67 M$\odot$ for N79S-1 and 131 M$\odot$ for N79S-2."]
- result: CH3OH relative abundance N(CH3OH)/N(H2) (N79S-1) = 2.1e-9 ± 1.1e-9 dimensionless [Abstract: "The abundance of cold CH$_3$OH gas is estimated to be (2.1 $\pm$ 1.1)$\times$ 10$^{-9}$ at N79S-1 and (4.5 $\pm$2.5)$\times$ 10$^{-10}$ at N79S-2."]
- result: CH3OH relative abundance N(CH3OH)/N(H2) (N79S-2) = 4.5e-10 ± 2.5e-10 dimensionless [Abstract: "The abundance of cold CH$_3$OH gas is estimated to be (2.1 $\pm$ 1.1)$\times$ 10$^{-9}$ at N79S-1 and (4.5 $\pm$2.5)$\times$ 10$^{-10}$ at N79S-2."]
- limitation (authors): Spectral resolution (0.86-1.1 km s^-1) is insufficient to clearly resolve hyperfine components of CN and CCH or potential multiple velocity components in the cores. [Spectra Toward the CH$_3$OH Peak Positi…: "The transitions were not clearly resolved because of the low spectral resolution of the present spectra."]
- limitation (authors): Some CH3OH transitions (especially 1_1-0_0 A+) and the H2CO transition are moderately to highly optically thick according to RADEX, making the H2CO column density a lower limit. [Gas-phase Molecular Column Density: "Among these, three have optical depths of approximately 1, while the 1$_1$-0$_0$ A$^+$ line has a significantly higher optical depth of 5.3."]
- limitation (authors): Derived molecular abundances can be affected by spatial filtering, excitation temperature assumptions, optical depth, and beam filling factors, while only dust temperature uncertainty (10-20 K) is folded into N(H2). [Relative Molecular Abundance: "The derived abundances of the observed molecules may be significantly affected by several factors, including spatial filtering effects, assumptions about excitation temperature, optical depth, and beam filling factors. In this work, we consider only the temperature uncertainty when estimating H$_2$ column densities fr…"]
- not stated (card): Exact frequency or channel ranges selected as line-free for continuum imaging and uvcontsub; tclean stopping threshold, niter, cell size, image size, deconvolver, and masking strategy; Calibration and imaging parameters for the Cycle 7 CO(3-2) dataset (2019.1.01770.S); Collision partner rates and ortho/para H2 ratio assumed in RADEX non-LTE calculations; Partition function Q(T_rot) values or inte…

### 2019MNRAS.483..806R: First ALMA maps of HCO, an important precursor of complex organic molecules, towards IRAS 16293-2422 (2019; astrochemistry, star_formation; observational_alma_primary)
- question: Where and how is the formyl radical HCO formed in IRAS 16293-2422 (envelope gas-phase vs hot corino grain surface), and what is its role as precursor of H2CO, CH3OH and glycolaldehyde?
- step 1: Fit continuum level and derive N(H2)
  - method: Modified blackbody fit by visual inspection varying beta and tau_d0 over four spws; T_c fixed to CH3OH Tex; N(H2) from tau_d0 [7 Fit of the continuum level: "We tried multiple combinations of both parameters (some examples are shown in Figures [11](#fig-continuoA) and [12](#fig-continuoB)) and chose by visual inspection the solutions"]
  - software: MADCUBA
  - parameter: nu0=94 GHz; Tc=178 K (A), 181 K (B) [7 Fit of the continuum level: "assumed that $T_{\rm c}$ is equal to the excitation temperature derived from CH$_3$OH, 178 K and 181 K for sources A and B respectively"]
  - assumption: gas-to-dust 100; mu=2.8; kappa0 extrapolated from 0.009 cm2/g at 1 mm [3.1 Continuum: "In the calculation we assumed a gas-to-dust mass ratio of 100"]
  - fitting: Visual inspection; errors from 5% calibration plus spectral rms [7 Fit of the continuum level: "We assumed a flux density calibration error of $\pm$5$\%$"]
  - validation: Comparison with previous N(H2) estimates [3.1 Continuum: "These hydrogen column densities are in good agreement with previous estimates"]
- result: Dust beta, source A = 0.9 ± ±0.4 dimensionless [3.1 Continuum: "$\beta$=0.9$\pm$0.4 and $\tau_{d0}$=0.09$\substack{+0.01 \\ -0.01}$ for source A"]
- result: Dust beta, source B = 0.0 ± ±0.5 dimensionless [3.1 Continuum: "$\beta$=0.0$\pm$0.5 and $\tau_{d0}$=2.1$\substack{+0.6 \\ -0.4}$ for source B"]
- result: N(H2) source A = 4.4e24 ± not stated cm-2 [3.1 Continuum: "We obtained N(H2)=4.4$\times$10$^{24}$ cm$^{-2}$ and N(H2)=5.0$\times$10$^{25}$ cm$^{-2}$ for A and B, respectively."]
- result: N(H2) source B = 5.0e25 ± not stated cm-2 [3.1 Continuum: "We obtained N(H2)=4.4$\times$10$^{24}$ cm$^{-2}$ and N(H2)=5.0$\times$10$^{25}$ cm$^{-2}$ for A and B, respectively."]
- limitation (authors): CH3OH and H2CO column densities are lower limits because lines are optically thick [3.2.3: "the lines are not optically thin, and our estimates of the CH$_3$OH column densities should be considered as strict lower limits"]
- limitation (authors): HCO Tex could not be determined since all four lines share Eup of 4 K [3.2.3: "We were not able to derive the excitation temperature of HCO because the 4 detected lines of HCO share the same $E_{\rm up}$, 4 K."]
- not stated (card): CASA version and tclean/imaging parameters (weighting, robust, cell, image size, deconvolver, masks); Which channels were line-free for continuum subtraction; Whether archive calibration products or manual scripts were used; Chemical network updates and rate coefficients (details deferred to Vasyunin et al. in prep.); Details of the TIMASSS data reduction and matching to ALMA integration area; MA…

### 2019A&A...626A.126A: A massive nebula around the luminous blue variable star RMC 143 revealed by ALMA (2019; stellar_physics, evolved_stars; observational_alma_primary)
- question: Is RMC 143 an LBV, and what are the dust content, mass and ionization of its circumstellar nebula, using ALMA Band 7 together with ATCA, X-shooter and IR data?
- step 6: Fit dust greybody to SED and derive dust mass
  - method: Single-temperature greybody fit to MIPS24, PACS100/160 and ALMA photometry, plus photosphere and free-free components [8 SED of RMC 143: "we only fit the greybody to the MIPS24, PACS100+160, and ALMA photometry."]
  - software: PyAstronomy
  - parameter: free-free contribution to ALMA 0.47-1.01 mJy, uncertainty +/-0.27 mJy added in quadrature [8 SED of RMC 143: "The uncertainty on the free-free contribution of $\pm0.27\,\rm mJy$ was added in quadrature with the ALMA measurement error in the fit."]
  - assumption: kappa_850 = 1.7 cm^2/g, distance 49.97 kpc [8 SED of RMC 143: "A dust emissivity at $850\,\mu{\rm m}$ of $\kappa_{850}=1.7\rm\,cm^{2}\,g^{-1}$ and LMC distance of $49.97\,\rm kpc$ are assumed."]
  - fitting: greybody fit; uncertainty region from twice minimum chi2; reduced chi2 1.44 [8 SED of RMC 143: "The reduced $\chi^2$ of the fit is 1.44."]
- step 7: Derive total nebular mass and Stromgren radius
  - method: Multiply dust mass by gas-to-dust ratio; Stromgren radius from Doran et al. photon fluxes [9 Nebular mass: "we find a total nebular mass $M_{\rm TOT}$ for RMC$\,$143 of $11.0\pm{3.7}~M_{\odot}$, and assuming G/D=100 (more representative of our Galaxy) $M_{\rm TOT}=5.5\pm1.8~M_{\odot}$."]
- result: Dust temperature = 70.9 ± 8.9 K [8 SED of RMC 143: "$T_{\rm dust}=70.9\pm8.9\,{\rm K}$, $\beta=1.31\pm0.30$ and $M_{\rm dust}=0.055\pm0.018~M_\odot$"]
- result: Dust emissivity index beta = 1.31 ± 0.30 dimensionless [8 SED of RMC 143: "$T_{\rm dust}=70.9\pm8.9\,{\rm K}$, $\beta=1.31\pm0.30$ and $M_{\rm dust}=0.055\pm0.018~M_\odot$"]
- result: Dust mass = 0.055 ± 0.018 Msun [8 SED of RMC 143: "$T_{\rm dust}=70.9\pm8.9\,{\rm K}$, $\beta=1.31\pm0.30$ and $M_{\rm dust}=0.055\pm0.018~M_\odot$"]
- result: Total nebular mass (G/D=100) = 5.5 ± 1.8 Msun [9 Nebular mass: "assuming G/D=100 (more representative of our Galaxy) $M_{\rm TOT}=5.5\pm1.8~M_{\odot}$"]
- result: Total nebular mass (G/D=200) = 11.0 ± 3.7 Msun [9 Nebular mass: "we find a total nebular mass $M_{\rm TOT}$ for RMC$\,$143 of $11.0\pm{3.7}~M_{\odot}$"]
- limitation (authors): Lowest ALMA contour has low significance; only a third of observations completed; deeper data needed [3.1 ALMA: "The lowest contour does not have strong statistical significance, but appears to partially overlap with the H$\alpha$ emission."]
- not stated (card): CASA version and calibration scripts for the non-standard ALMA calibration; Calibrators used for ALMA bandpass, flux and phase; Cell size, image size, deconvolution and clean masking for the ALMA image; Primary beam correction details and aperture used to integrate the 2.5 mJy flux; Greybody fit code, priors and optimizer settings; Exact ATCA reprocessing steps; CMFGEN model grid and fit procedur…

### 2013ApJ...777...92S: ALMA Observations of the Coldest Place in the Universe: The Boomerang Nebula (2013; evolved_stars; observational_alma_primary)
- question: What is the structure of the ultra-cold Boomerang Nebula's molecular outflow, how does it relate to the visible-light nebula, and what do the mm continuum data say about the dust in the waist?
- step 5: Derive dust emissivity index, temperature, mass of waist
  - method: Fit 1.3/2.6 mm peak flux ratio with power-law emissivity; choose beta, T_d consistent with compact size r_d~2"; compute dust and total mass [Thermal Dust Emission from the Waist: "Since the continuum emission arises from a compact source with an observed value of $r_d\sim2{''}$, we conclude $\beta\sim0.6$ and $T_d\sim45$ K"]
  - parameter: kappa(1.3mm)~1.5 cm2/g, gas-to-dust 200 [Thermal Dust Emission from the Waist: "assuming a dust opacity of $\kappa(1.3mm)\sim1.5$ cm$^2$ g$^{-1}$ and the gas-to-dust ratio, $\delta=200$"]
  - assumption: power-law dust emissivity; ATCA non-detections rule out free-free [Thermal Dust Emission from the Waist: "so free-­free emission is unlikely to contribute to the 1.3 and 2.6 mm fluxes"]
  - fitting: analytic, no sampler [Discussion: Re-Heating of the Ultra-col…: "re-derive the radial dependence of the kinetic temperature and adiabatic cooling analytically."]
- result: 1.3 to 2.6 mm peak flux ratio = 5.7 ± not stated dimensionless [Thermal Dust Emission from the Waist: "$R=5.7$"]
- result: dust emissivity index beta = ~0.6 ± not stated dimensionless [Thermal Dust Emission from the Waist: "we conclude $\beta\sim0.6$ and $T_d\sim45$ K"]
- result: dust temperature = ~45 ± not stated K [Thermal Dust Emission from the Waist: "we conclude $\beta\sim0.6$ and $T_d\sim45$ K"]
- result: dust mass in waist = 3.5e-4 ± not stated Msun [Thermal Dust Emission from the Waist: "is $M_d\sim3.5\times10^{-4}$ $M_{\odot}$"]
- result: total mass of waist = 0.071 ± not stated Msun [Thermal Dust Emission from the Waist: "the total mass is $M\sim0.071$ $M_{\odot}$"]
- result: mass-loss rate of waist = 1.8e-4 ± not stated Msun/yr [Thermal Dust Emission from the Waist: "implying a mass-loss rate $\sim1.8\times10^{-4}$ $M_{\odot}$ yr$^{-1}$"]
- limitation (authors): 1.3 mm data S/N modest with sparse uv coverage; large fraction of CO(1-0) absorption resolved out [Thermal Dust Emission from the Waist: "although S/N is modest and 1.3 mm UV-coverage is still sparse"]
- not stated (card): Briggs robust value and clean parameters (image size, cell size, masks, threshold, niter); Line-free channels used for continuum subtraction; Continuum image weighting, taper and spectral windows used for 1.3 and 2.6 mm; How the S/N-modest 1.3 mm continuum was imaged and sparse uv coverage handled; Details of the dust SED fit (beam-matching, uncertainties on R); Feather parameters and SEST data p…

### 2021NatAs...5..586Y: Compact pebbles and the evolution of volatiles in the interstellar comet 2I/Borisov (2021; solar_system, protoplanetary_disks; observational_alma_primary)
- question: Characterize the dust particle properties (size, porosity, mass loss rate) and pre-perihelion CO gas production in the interstellar comet 2I/Borisov to understand its formation and volatile evolution.
- step 2: Model dust thermal SED and derive dust particle size, porosity, mass, and mass loss rate
  - method: Use Mie theory combined with Bruggeman effective medium theory to compute absorption cross sections C_abs(a, lambda), solve radiative equilibrium for grain temperature T(a, r_h), compute model flux density for single-sized grains and Divin… [Methods: "We use Mie theory combined with the Bruggman effective medium theory (cite: Bohren:1983) to calculate $C_{\rm abs}(a,\lambda)$, the absorption cross sections of spherical porous aggregates of radii $a$ at wavelength $\lambda$."] [Methods: "We have also modeled the SED in terms of the Divine-type cometary size distribution (cite: Divine1986) $dn/da\propto \left(1-a_{\rm min}/a\right)^{\gamma}\times\left(a_{\rm min}/a\right)^{\alpha}$ in the size range of $a_{\rm min}< a <a_{\rm max}$."]
  - parameter: Divine-type distribution: alpha = 3.5, a_min = 1 um, a_max = 1 cm, peak a_p = 1 mm (area-weighted peak a_p' = 2.3 mm) [Methods: "As illustrated in Fig. [2](#fig:sedmod)b, with $\alpha=3.5$ (see ref.(cite: Lasue2009)), $a_{\rm min}=1\,{\rm \mu m}$ and $a_{\rm max}=1\,{\rm cm}$, compact, spherical dust particles with a Divine-type size distribution peaking at $a_p=1\,{\rm mm}$ and a total dust mass of $M_{\rm dust}\approx2.57\times10^{8}\,{\rm kg…"]
  - parameter: Single effective dust size ~ 5 mm [Pebbles and volatile evolution in the i…: "Assuming an effective dust size of ${\sim\,}$5$\,{\rm mm}$, we obtained a total dust mass loss of $\approx2.81\times10^{8}\,{\rm kg}$ within the ALMA beam (see Fig. [2](#fig:sedmod))."]
  - assumption: Spherical grains; mass mixing ratio m_carb/m_sil = 0.5; compact dust density rho_CD = 2650 kg m^-3 (or porous P = 0.80 with rho_CD = 530 kg m^-3); dust velocity v_d = 3 m s^-1; nucleus bulk density = 500 kg m^-3 and radius r_n = 0.4 km. [Methods: "We adopt $m_{\rm carb}/m_{\rm sil}$ = 0.5, as implied from the mass spectrometry of the dust particles from 67P"] [Methods: "(for compact dust, $\rho_{\rm CD}\approx2,650 \,{\rm kg}\,{\rm m}^{-3}$; for porous dust of porosity $P=0.80$, $\rho_{\rm CD}\approx530\,{\rm kg}\,{\rm m}^{-3}$; see ref.(cite: Li2003))."]
  - fitting: Varying cutoff sizes (a_min, a_max), power exponents (alpha, gamma), grain size a, porosity P, and total dust mass M_dust to reproduce ALMA photometry [Methods: "By varying the lower and upper cutoff sizes ($a_{\rm min}$, $a_{\rm max}$) as well as the power exponents ($\alpha$, $\gamma$), close fits to the observed SED are achieved if the dust particles are predominantly mm-sized (or larger)."]
  - validation: Tested sensitivity to composition (pure silicate vs pure amorphous carbon) and compared single-size vs Divine-type size distributions [Methods: "Indeed, our calculations show that both pure silicate particles and pure amorphous carbon particles can reproduce the ALMA observations, provided that they are mm-sized (or larger) pebbles."]
- step 4: Measure optical coma reflectivity slope, Af rho, and optical dust mass loss rates from VLT/FORS2
  - method: Process FORS2 images in ESO MIDAS, calibrate photometry against Pan-STARRS and SDSS stars, measure magnitudes in a 5" radius circular aperture, convert R magnitudes to Af rho, and compute order-of-magnitude Q(dust). [Methods: "The data were processed in the standard way using ESO MIDAS software, as described in ref. (cite: Hainaut2019)."] [Methods: "The magnitudes measured using a $5^{\prime\prime}$ radius aperture are reported in Supplementary Table 2. The $R$ magnitudes are converted into $Af\rho$"]
  - software: ESO MIDAS
  - parameter: Aperture radius = 5" [Methods: "The magnitudes measured using a $5^{\prime\prime}$ radius aperture are reported in Supplementary Table 2."]
  - assumption: rho_d = 2650 kg m^-3, v_d = 3 m s^-1, mean dust size <a> = 1 mm, geometrical albedo p_V = 0.04 [Methods: "By taking $\rho_d=\rho_{\rm CD}\approx2,650\,{\rm kg}\,{\rm m}^{-3}$, $v_d=3\,{\rm m}\,{\rm s}^{-1}$, $\langle a\rangle=1\,{\rm mm}$, and $p_V=0.04$ (ref. (cite: Cremonese2020; Kim2020)), we derived the dust mass loss rates and listed them in Supplementary Table 2."]
- result: Compact dust particle radius lower limit (a) = >= 1 ± not stated mm [Pebbles and volatile evolution in the i…: "We found that very large, “pebble”-like *compact* particles of radii $a\lower.5ex\hbox{$\buildrel > \over \sim$}1\,{\rm mm}$ are required to reproduce the ALMA photometry."]
- result: Dust equilibrium temperature at r_h = 2.01 au = 197 ± not stated K [Pebbles and volatile evolution in the i…: "The dust particles attain an equilibrium temperature of $T\approx 197\,{\rm K}$ at ${r_h}=2.01\,{\rm au}$ and their emission spectra are blackbody-like (see Methods)."]
- result: Total dust mass within ALMA beam (single size a ~ 5 mm) = 2.81e8 ± not stated kg [Pebbles and volatile evolution in the i…: "Assuming an effective dust size of ${\sim\,}$5$\,{\rm mm}$, we obtained a total dust mass loss of $\approx2.81\times10^{8}\,{\rm kg}$ within the ALMA beam (see Fig. [2](#fig:sedmod))."]
- result: Total dust mass within ALMA beam (Divine-type size distribution peaking at a_p = 1 mm) = 2.57e8 ± not stated kg [Pebbles and volatile evolution in the i…: "Similar results were obtained if we considered the Divine-type dust size distribution which peaks at $a_p=1\,{\rm mm}$ and requires a total dust mass loss of $\approx2.57\times10^{8}\,{\rm kg}$ (see Methods)."]
- result: ALMA dust mass loss rate Q(dust) = ~200 ± not stated kg s^-1 [Pebbles and volatile evolution in the i…: "we obtained a beam crossing time $\tau$ ${\sim\,}1.36\times10^{6}\,{\rm s}$, in turn, a dust mass loss rate $Q({\rm dust})\sim200\,{\rm kg}\,{\rm s}^{-1}$."]
- result: Total dust mass lost between discovery and perihelion = 2.0e9 ± not stated kg [Pebbles and volatile evolution in the i…: "We therefore adopted a constant dust production rate of 200$\,{\rm kg}\,{\rm s}^{-1}$ and obtained the total mass loss of $2.0\times 10^{9}\,{\rm kg}$ during the period between the discovery and the arrival at the perihelion."]
- result: Eroded surface layer thickness of nucleus = >= 2 ± not stated m [Pebbles and volatile evolution in the i…: "we find that a layer of at least 2$\,{\rm m}$ was eroded from 2I/Borisov’s surface since it entered the inner Solar system in late August 2019 ."]
- result: Optical dust coma reflectivity slope S' = 9 ± 5 %/100 nm [Pebbles and volatile evolution in the i…: "Our spectroscopic and multi-band photometric observations with FORS show that the dust coma of 2I/Borisov appears slightly redder than the Sun in the optical with an average reflectivity $S^{\prime}=(9\pm5)\%/100\,{\rm nm}$"]
- limitation (authors): Extended dust structures near the center in Bands 4 and 6 had too low SNR to be confirmed or included in the analysis. [Methods: "However, due to the low signal-to-noise ratio of these features, we can not confirm the extended features are real features."]
- limitation (authors): Larger pebbles (a >= 1 cm or dm-sized) emit less effectively at ALMA wavelengths and are not well constrained, making the dust mass loss rate and dust-to-gas ratio lower limits. [Pebbles and volatile evolution in the i…: "Larger pebbles (e.g., $a\lower.5ex\hbox{$\buildrel > \over \sim$}1\,{\rm cm}$) emit less effectively at the ALMA bands and cannot be well constrained, therefore, our dust mass loss estimate is considered as a lower limit (see discussion in Methods)."]
- limitation (authors): CO rotational temperature is poorly constrained by the two transitions (1-sigma range 13-181 K), and spectral resolution was insufficient to measure the CO outflow velocity directly. [Pebbles and volatile evolution in the i…: "However, the temperature is not well constrained by the observations, with a ($1\sigma$) error range of ${\sim\,}$13–181$\,{\rm K}$."]
- not stated (card): tclean parameters: cell size, image size, deconvolver, stopping threshold, and masking strategy; Details of how the native Band 3 image (beam 4.05" x 2.83") was convolved to a smaller resolution element of 3.4" x 2.3" (whether imsmooth targetres or kernel convolution was used); Continuum subtraction parameters and line-free channel ranges for the CO spectral cubes; Exact number and coordinates of…

### 2025A&A...694A..86Y: ALMA observations of massive clouds in the central molecular zone: slim filaments tracing parsec-scale shocks (2025; milky_way_ism, astrochemistry, star_formation; observational_alma_primary)
- question: What is the origin of the widespread SiO and COM emission in the CMZ, and what are the newly found narrow SiO filaments (slim filaments) in two massive CMZ clouds
- step 7: Estimate turbulent, thermal, gravitational, magnetic and external pressures
  - method: P_turb = rho sigma_v^2 with density from the continuum-limit column density over the filament width; compare with thermal, gravity, magnetic and external pressure [4.1 A new class of filaments: "The turbulent pressure can be estimated using $P_{\rm turb}$ = $\rho\sigma_{v}^{2}$."] [4.1 A new class of filaments: "Assuming that the thickness along the line of sight is the same as the slim filament width of 0.024 pc"]
  - parameter: Mean sigma_v = 4.4 km/s [4.1 A new class of filaments: "We adopt a mean $\sigma_{v}$ value of 4.4 km s$^{-1}$"]
  - parameter: Continuum limit 5 sigma = 0.2 mJy/beam at 226 GHz [4.1 A new class of filaments: "Considering the dust emission at the 5$\sigma$ level of 0.2 mJy beam$^{-1}$"]
  - assumption: Gas-to-dust mass ratio 100 [4.1 A new class of filaments: "where $\eta$ = 100 is the assumed gas-to-dust mass ratio"]
  - assumption: T_dust = 20 K [4.1 A new class of filaments: "dust temperature $T_{\rm dust}$ = 20 K following (cite: kauffmann2017a)"]
  - assumption: Dust opacity 0.817 cm2/g (beta = 1.5) [4.1 A new class of filaments: "We adopt $\kappa_{\nu}$ = 0.817 cm$^{2}$g$^{-1}$"]
  - assumption: mu_H2 = 2.8 [4.1 A new class of filaments: "$\mu_{\rm H_{2}}$ = 2.8 is the mean molecular weight of the interstellar medium"]
- result: Upper limit on H2 column density from the continuum = 2.3e23 ± not stated cm^-2 [4.1 A new class of filaments: "the upper limit for the column density is calculated to be 2.3 $\times$ 10$^{23}$ cm$^{-2}$"]
- result: Upper limit on gas density n = 3.1e6 ± not stated cm^-3 [4.1 A new class of filaments: "the estimated upper limit of the density $n$ is approximately 3.1 $\times$ 10$^{6}$ cm$^{-3}$"]
- result: Turbulent pressure P_turb/k_B = 1.7e10 ± not stated K cm^-3 [4.1 A new class of filaments: "This yields a turbulent pressure $P_{\rm turb}$/$k_{\rm B}$ of approximately 1.7 $\times$ $10^{10}$ K cm$^{-3}$."]
- result: Thermal pressure P_th/k_B = 9.2e7 ± not stated K cm^-3 [4.1 A new class of filaments: "resulting in 9.2 $\times$ $10^{7}$ K cm$^{-3}$"]
- result: Gravitational pressure P_gravity/k_B = 1.3e8 ± not stated K cm^-3 [4.1 A new class of filaments: "$P_{\rm gravity}$/$k_{\rm B}$ of 1.3 $\times$ 10$^{8}$ K cm$^{-3}$"]
- result: Magnetic pressure P_mag/k_B (maximum, B = 0.48 mG) = 6.6e7 ± not stated K cm^-3 [4.1 A new class of filaments: "is about 6.6 $\times$ $10^{7}$ K cm$^{-3}$ for a magnetic strength of 0.48 mG"]
- result: External pressure P_ex/k_B = 2.6e8 ± not stated K cm^-3 [4.1 A new class of filaments: "the external pressure is calculated to be approximately 2.6 $\times$ 10$^{8}$ K cm$^{-3}$"]
- limitation (authors): The sample is not complete; only the most robust candidates were reported [2.1 Identification of the slim filaments: "We note that the identified slim filaments are by no means a complete sample of such objects in the surveyed clouds."]
- limitation (authors): Without dust emission the H2 column density is unconstrained, so abundances are lower limits [3.3 Relative Abundances of the Molecule…: "Consequently, we could only provide lower limits for molecular abundances and relative abundances between the molecules."]
- limitation (authors): The nature and origin of the filaments need further multi-wavelength work [4.2 Possible origin of the slim filamen…: "Future multi-wavelength investigations that better constrain excitation conditions and chemistry will help confirm the nature of these filaments."]
- not stated (card): Exact CASA version and calibration/pipeline route (only in Lu et al. 2020, 2021); tclean parameters: weighting/robust, cell size, image size, deconvolver, masks, line-free channels and continuum subtraction (inherited from earlier papers); Whether SiO integrated-intensity maps were primary-beam corrected, and the velocity range and moment-0 clipping used; Pixel scale needed to reproduce the FilFi…

### 2015MNRAS.449..715W: Tracing the conversion of gas into stars in Young Massive Cluster Progenitors (2015; milky_way_ism, star_formation; multi_facility_alma_minor)
- question: Are four extreme quiescent Galactic centre clouds gravitationally bound YMC progenitors, and is their gas distribution compact enough to form an Arches-like cluster?
- step 1: Dust mass and radius from HiGAL
  - method: Sum column density maps above 5e22 cm-2 threshold with mean molecular weight 2.8 mH; effective radius as geometric mean of axes [Dust Mass: "we estimate the dust masses of the clouds by assuming a mean molecular weight of 2.8m$_{H}$, multiplying each pixel by its physical area (assuming a distance of 8.4 kpc) and summing over the cloud area."]
  - parameter: column density threshold 5 x 10^22 cm^-2 [Dust Column Densities & Temperatures: "A column density threshold has been applied such that all pixels below 5 x 10$^{22}$ cm$^{-2}$ are masked."]
  - assumption: distance 8.4 kpc [Dust Mass: "assuming a distance of 8.4 kpc"]
  - validation: Mass vs threshold tested (5-10e22 changes mass by 10-40%); compared with Immer et al. and L12 [Dust Mass: "These estimates agree well with those found by (cite: Immer) and L12."]
- step 4: Mass surface density profiles and comparison with Sgr B2 and Arches
  - method: Enclosed mass in circular apertures; BGPS fluxes converted to mass with Kauffmann et al. relation at 20 K; stellar mass from UCHII OB stars with Kroupa IMF correction; SFE factor 1/3 [Discussion: "The dust temperature is assumed to be 20 K"]
  - parameter: k_nu = 0.04 cm2 g-1 (nu/505 GHz)^1.75 [Discussion: "k_{\nu} = 0.04 \rm ~ cm^{2} ~ g^{-1} \left(\frac{\nu}{505 ~ GHz}\right)^{1.75}"]
  - assumption: gas-to-dust ratio 100 [Discussion: "Note that this contains the explicit assumption that the gas-to-dust ratio is 100."]
- result: Dust masses of G0.253, d, e, f = 11.9, 7.6, 11.2, 7.3 x10^4 ± systematic factor ~2 Msun [Dust Mass: "We determine the masses of G0.253$+$0.016, ‘d’, ‘e’ and ‘f’ to be 11.9 x 10$^{4}$ M$_{\odot}$, 7.6 x 10$^{4}$ M$_{\odot}$, 11.2 x 10$^{4}$ M$_{\odot}$ and 7.3 x 10$^{4}$ M$_{\odot}$"]
- result: Effective radii G0.253, d, e, f = 2.9, 3.2, 2.4, 2.0 ± not stated pc [Radius: "We derive effective radii of 2.9 pc, 3.2 pc, 2.4 pc and 2.0 pc, respectively"]
- result: Radius enclosing 5e4 Msun (G0.253, d, e, f) = 1.0, 1.2, 0.8, 1.0 ± not stated pc [Radius: "1.0 pc, 1.2 pc, 0.8 pc and 1.0 pc, respectively for G0.253$+$0.016, ‘d’, ‘e’ and ‘f’"]
- result: Total stellar mass in Sgr B2 from 25 UCHII sources = ~3.5e3 ± not stated Msun [Discussion: "Taking all 25 sources in (cite: Gaume), we estimate a total stellar mass of $\sim$ 3.5 x 10$^{3}$ M$_{\odot}$."]
- limitation (authors): Mass estimates uncertain due to cloud boundary definition and a factor ~2 systematics; gas temperature measured only for G0.253 [Dust Mass: "We note that these mass estimates are necessarily uncertain due to the ambiguity involved in defining a distinct cloud area"]
- not stated (card): Coefficient k in the virial mass formula; ALMA calibration, imaging and feathering details (deferred to Rathborne et al. 2014b); Hanning smoothing and CASA fit procedure details for spectra; How cloud boundaries were drawn on the column-density maps; Aperture centres and radial bins for profiles

### 2020ApJ...894L..14L: ALMA Observations of Massive Clouds in the Central Molecular Zone: Jeans Fragmentation and Cluster Formation (2020; milky_way_ism, star_formation; observational_alma_primary)
- question: Do massive CMZ clouds contain hidden early-phase fragmentation into cores, and is it consistent with thermal Jeans fragmentation and with forming Arches/Quintuplet-like clusters?
- step 3: Derive core masses, radii, densities
  - method: Optically thin dust: M = R S d^2/(B(T) kappa); r=(A/pi)^0.5; n(H2)=M/(4 pi r^3/3)/(2.8 mH) [3.2 Physical Properties of the Cores: "The effective core radius $r_\text{c}$ is derived as $(A/\pi)^{1/2}$, where $A$ is the area of the core reported by *astrodendro*."]
  - parameter: T_dust = 20 K, R = 100, kappa = 0.899 cm2/g, d = 8.178 kpc [3.2 Physical Properties of the Cores: "we assumed a constant $T_\text{dust}$ of 20 K as a fiducial case"]
  - assumption: Optically thin dust, constant 20 K, gas-to-dust 100 [3.2 Physical Properties of the Cores: "Assuming optically thin dust emission, the core masses were derived as"]
  - validation: Tested 50 K, flux-dependent and random T_dust in appendix [Appendix: Impact of Varying Dust Temper…: "If we adopt a dust temperature of 50 K, the core masses would decrease by a factor of 3."]
- result: 5 sigma mass sensitivity = 0.3 ± not stated Msun per beam [3.2 Physical Properties of the Cores: "the 5$\sigma$ mass sensitivity is 0.3 $M_\odot$ per beam given a $T_\text{dust}$ of 20 K"]
- limitation (authors): Dust temperature at 2000 AU unknown, strongly affects masses [3.2 Physical Properties of the Cores: "$T_\text{dust}$ at 2000 AU scales is unclear."]
- limitation (authors): Cannot tell whether cores are prestellar or protostellar [3.2 Physical Properties of the Cores: "with the current data we cannot determine whether the cores have collapsed and are mostly protostellar"]
- not stated (card): Image size and phase centres per field; Line-free channel selection; Which execution blocks and calibrators were used; flux calibrator and flux uncertainty; Cleaning threshold, niter and masks; Exact astrodendro call details beyond min_value/min_delta/min_npix; Modifications made to FragMent; KDE settings for separation distributions; Primary beam correction details and mosaic pointing layout

### 2013ApJ...762L..21M: Millimeter Emission Structure in the First ALMA Image of the AU Mic Debris Disk (2013; debris_disks; observational_alma_primary)
- question: What is the millimeter emission structure of the AU Mic debris disk at 0.6" resolution, including the outer belt profile and a newly seen central peak?
- step 3: Estimate dust mass and temperature of central peak and outer belt
  - method: Optically thin dust emission F = kappa B(T) M / d^2 with astrosilicate opacity, n(a)∝a^-3.5, amin=0.2 um, amax 1 um–1 cm; max T constrained by IR SED [4.1 The Central Emission Peak: "we computed the maximum $T$ (and minimum $M_{\rm dust}$) consistent with both the observed millimeter flux density and the infrared SED."]
  - parameter: kappa = 2.7 cm^2/g; outer belt T ≈ 25 K [4.2 The Outer Dust Belt: "Adopting the opacity used in §4.1 ($\kappa_{\nu}$ = 2.7 cm$^2$ g$^{-1}$), and assuming $T \approx 25$ K (for 35-45 AU)"]
  - assumption: d = 9.91 pc; central peak is star plus dust [4.1 The Central Emission Peak: "We assume the central peak represents the combined emission from the star and dust, such that $F_{\rm dust} = F_{\rm cen} - F_{\ast} \approx 0.25$ mJy at 1.3 mm."]
- result: Inner belt dust mass = ~9e23 g (~1% lunar mass) ± not stated g [4.1 The Central Emission Peak: "The corresponding minimum $M_{\rm dust}$ is $\sim$$9 \times 10^{23}$ g, about 1% of the lunar mass."]
- result: Outer belt dust mass = 7e25 g ± not stated g [4.2 The Outer Dust Belt: "the dust mass of this outer belt is $7 \times 10^{25}$ g (cite: liu04b)"]
- limitation (authors): Spectral index of central peak poorly constrained; inner belt interpretation needs higher resolution [4.1 The Central Emission Peak: "Unfortunately, the spectral index ($\alpha_{\rm cen}$) constraints are not good enough to be diagnostic."]
- not stated (card): Flagging details and line/edge channels excluded beyond 'central 112 channels'; Cell size, image size, CLEAN mask and threshold; Neptune flux model used; Number of walkers and burn-in/convergence criteria; Model code (visibility generation) not released; Reweighting procedure details; Dust temperature adopted when computing belt mass from the 7.14 mJy flux in detail

### 2019MNRAS.488.1005P: Upper limits on protolunar disc masses using ALMA observations of directly imaged exoplanets (2019; exoplanets, protoplanetary_disks; observational_alma_primary)
- question: How much circumplanetary (protolunar) dust surrounds young directly-imaged exoplanets, and is it enough to form regular satellite systems (~1e-4 Mp)?
- step 2: Radiative transfer disc models to convert flux limit to dust mass limit
  - method: Viscous self-similar surface density disc, vary disc mass until model 1.3 mm flux equals 3 sigma limit, with radmc3d [3 CPD models: "we varied the disc mass until the 3$\sigma$ flux upper limit is matched for each disc"]
  - software: RADMC-3D
  - parameter: slope -1; r_c = 0.4 or 0.04 R_Hill; minimum radius r_c/10; aspect ratio 0.1; 2 deg inclination to planet orbit [3 CPD models: "A constant disc vertical aspect ratio of 0.1 is assumed."]
  - parameter: dust size 1 um to 1 cm, exponent -3.5; opacity 2.3 cm2/g at 1.3 mm [3 CPD models: "This yields an absorption opacity of 2.3 cm$^2$ g$^{-1}$ at 1.3 mm."]
  - assumption: Disc inclination 30 deg from face on (beta Pic b 85 deg) [3 CPD models: "we assumed disc inclinations of $30\deg$ from face on for all systems"]
  - assumption: Star and planet luminosities heat dust; anisotropic scattering included [3 CPD models: "The star and planet luminosities are included as energy sources that set the dust temperature."]
  - validation: Scale-height test for PZ Tel changes flux by <~10%; comparison with Ricci2017b limits [footnote 5: "found that a more realistic scale-height only affects the emitted fluxes by $\ensuremath{\lesssim}$10%"]
- step 3: Compare to viscous evolution model
  - method: alpha-disc similarity solution until 1 Myr then exponential decay with truncation at 0.4 R_Hill; compare dust mass vs age [4.1 Viscous evolution: "Therefore, for the evolution after 1 Myr instead we used equation 5 in (cite: Rosotti2018)"]
  - parameter: alpha = 1e-4 and 1e-3; disc temperature 40 K; dissipation 1 Myr; initial solid mass 1e-4 Mp [4.1 Viscous evolution: "The dashed and dotted lines represent models with $\alpha=10^{-4}$ and $10^{-3}$, respectively."]
  - assumption: gas-to-dust 100; grain density 1 g/cm3 [4.1 Viscous evolution: "gas-to-dust ratio of 100"]
- result: Mmax/Mp PZ Tel b (0.4 / 0.04 R_Hill) = 2.5e-7 / 2.0e-7 ± not stated dimensionless [Table 1: "2.5$\times$10$^{-7}$ | 2.0$\times$10$^{-7}$"]
- result: Mmax/Mp 51 Eri b (0.4 R_Hill) = 2.2e-6 ± not stated dimensionless [Table 1: "2.2$\times$10$^{-6}$"]
- result: Mmax/Mp AB Pic b (0.4 / 0.04 R_Hill) = 5.0e-6 / 2.4e-6 ± not stated dimensionless [Table 1: "5.0$\times$10$^{-6}$ | 2.4$\times$10$^{-6}$"]
- result: Mmax/Mp kappa And b (0.4 / 0.04 R_Hill) = 9.0e-7 / 1.4e-6 ± not stated dimensionless [Table 1: "9.0$\times$10$^{-7}$ | 1.4$\times$10$^{-6}$"]
- result: Dust opacity at 1.3 mm = 2.3 ± not stated cm2 g-1 [3 CPD models: "This yields an absorption opacity of 2.3 cm$^2$ g$^{-1}$ at 1.3 mm."]
- limitation (authors): System ages uncertain by ~50% [4.1 Viscous evolution: "the age of these systems is uncertain and could vary by $\sim$50%"]
- limitation (authors): Gas (CO) not analysed [2 Data description: "Searching for low-level gas in these systems is beyond the scope of this paper"]
- not stated (card): Which observing blocks and how many per target; target phase centres; Measured RMS values per target in uJy (only 3-sigma limits in table); Dust composition fractions and optical constants for astrosilicate, amorphous carbon, water ice; Dust grain internal density and scattering treatment details for radmc3d; Stellar and planetary luminosity inputs and grid resolution for RT; Number of photons an…

### 2021A&A...650A.153D: Multiwavelength view of SPT-CL J2106-5844. The radio galaxies and the thermal and relativistic plasmas in a massive galaxy cluster merger at z ≃ 1.13 (2021; galaxy_clusters_and_sz, agn_and_quasars; archival_reuse)
- question: Reconstruct the intracluster pressure distribution and investigate the merger and diffuse radio emission in SPT-CL J2106-5844.
- step 7: Constrain the central source spectrum and dust
  - method: Add ATCA compact-source fluxes to ALMA+ACA fits; fit spectral curvature, then add Herschel upper limits and fit power law plus modified blackbody. [Unresolved source: "we repeat the fit by including the flux measurements from the ATCA data at 2.1, 5.5, and 9 GHz."] [Unresolved source: "we extend the spectral model of the unresolved source to a modified power law, hence to fit for any potential spectral curvature at high frequency."]
  - parameter: Herschel upper limits: average fluxes in BCG-centered apertures with sizes equal to the respective beams [Unresolved source: "upper limits based on the average fluxes measured in each of the three *Herschel* bands within apertures centered on the BCG position and with size equal to the respective beams."]
  - assumption: Exclude EMU compact flux because extended radio emission may contaminate it [Unresolved source: "We do not consider here any information from the EMU observations as, at the EMU frequency, the extended radio structure may significantly contaminate the flux measured for the central source."]
  - assumption: Dust opacity power law; β=1.5 [Unresolved source: "For the dust opacity function, we consider a power-law form, $k_{\nu_{\textsc{rf}}}=k_{0}[(1+z)\nu/\nu_{0}]^{\beta}$"] [Unresolved source: "where the dust emission efficiency index is fixed to $\beta=1.5$ (cite: PlanckXLIII2016; Erler2018)."]
  - assumption: ν0=c/350 μm; κ0=0.192 m² kg−1 [Unresolved source: "We set the reference frequency to $\nu_0=c/350~\mathrm{\mu m}$"] [Unresolved source: "the typical value for the mass absorption coefficient at $350~\mathrm{\mu m}$ of $\kappa_{0}=0.192~\mathrm{m^{2}~kg^{-1}}$ (cite: Draine2003)."]
  - fitting: Reconstruct dust mass and temperature posterior distributions [Unresolved source: "the heavy degeneracy affecting the posterior probability distribution of the reconstructed mass and temperature."]
  - validation: Compare modified power-law and dust-model spectra; note disagreement in Band 3 and heavy mass–temperature degeneracy. [Unresolved source: "We observe a general agreement with the modified power law model, except for a discrepancy over ALMA’s Band 3 spectral window."] [Unresolved source: "the heavy degeneracy affecting the posterior probability distribution of the reconstructed mass and temperature."]
- result: BCG dust mass = 3.5 × 10^8 ± +2.3/-1.9 × 10^8 M⊙ [Unresolved source: "we measure values for the dust mass and temperature of $3.5\substack{+2.3\\-1.9}\cdot10^8~\mathrm{M_{\odot}}$ and $19.8\substack{+7.0\\-6.6}~\mathrm{K}$, respectively"]
- result: BCG dust temperature = 19.8 ± +7.0/-6.6 K [Unresolved source: "we measure values for the dust mass and temperature of $3.5\substack{+2.3\\-1.9}\cdot10^8~\mathrm{M_{\odot}}$ and $19.8\substack{+7.0\\-6.6}~\mathrm{K}$, respectively"]
- limitation (authors): Chandra source counts do not constrain the ICM temperature distribution. [Chandra: "The low number of source counts in the available *Chandra* data did not allow for deriving significant constraints on the temperature distribution of the ICM within SPT-CL J2106-5844."]
- limitation (authors): Most X-ray hardness structures have low significance. [Chandra: "aside from the bright core region, it is not possible to identify any structure with a significance higher than $2\sigma$."]
- limitation (authors): Radio resolution, sparse sampling, and weak high-frequency detections prevent a detailed spectral-index map. [Diffuse emission: "the different angular resolutions of the available radio data, combined with the severe sparsity and low significance of the observations at high frequencies, do not allow for building a detailed map of the spectral index distribution"]
- not stated (card): ALMA/ACA calibrated measurement-set release identifiers, calibration CASA/pipeline versions, and any additional flagging or averaging.; Exact visibility likelihood, visibility-weight treatment, and implementation of the 5% flux-calibration uncertainty.; Forward-model map grid, line-of-sight integration limits, primary-beam model, and frequency integration across spectral windows.; Numerical fixed…

### 2025ApJ...986L..22R: The First Detection of Molecular Activity in the Largest Known Oort Cloud Comet: ALMA Imaging of C/2014 UN271 (Bernardinelli─Bernstein) at 16.6 au from the Sun (2025; solar_system; observational_alma_primary)
- question: What are the molecular activity drivers, CO outgassing kinematics and continuum (nucleus/dust) properties of the distant active Oort cloud comet C/2014 UN271 at 16.6 au?
- step 5: Continuum visibility fits: nucleus size and dust coma mass
  - method: lmfit fits to 233 GHz visibilities with point source, point+1/rho coma, and fixed max coma; NEATM diameters; coma dust mass from flux with opacities [Continuum Modeling: "We used the `lmfit` package to perform least squares fits to the 233 GHz continuum visibilities"]
  - software: lmfit
  - parameter: Tss=95±9 K (NEATM) or 60 K (CO) [Continuum Modeling: "The resulting $T_{ss}$ is 95 $\pm$ 9 K on both dates."]
  - assumption: Opacities 0.17-0.467 m2/kg; dust at equilibrium temperature [Coma Dust Mass: "the derived opacities are in the range $1.70-4.67\times10^{-1}$ m$^2$ kg$^{-1}$"]
  - fitting: Least squares, chi2 comparison [5: "Based on $\chi^2$ analysis, our March 8 data are best fit by a 101–129 km nucleus"]
  - validation: Compared with Lellouch et al. nucleus size [5: "Overall, our values are in formal agreement with (cite: Lellouch2022) within 2$\sigma$."]
- result: Nucleus diameter range = 101-151 ± not stated km [5: "with nominal diameters ranging from 101 km – 151 km"]
- result: Dust coma mass March 8 = 0.44-1.2 ± 0.08-0.2 1e11 kg [Table 5: "$(0.44\pm0.08$)–$(1.2\pm0.2)$"]
- limitation (authors): Two-component model is a simplification of the dual-jet geometry; March 17 S/N lower [4.1.1: "Our two-component radiative transfer model is a simplification of this geometry"]
- not stated (card): Line-free channels and continuum subtraction method; Image pixel/cell size and image size; Exact spectral window frequencies and CO rest frequency; Initial guesses and bounds for lmfit fits; Choice of aperture/extraction for interferometric spectra fitted; Pipeline version; Calibrator catalog data used for polynomial fit details; Phase center coordinates

### 2026MNRAS.548ag325W: 3D insights into SN 1987A: ALMA observations compared to hydrodynamical explosion simulations (2026; transients, astrochemistry, milky_way_ism; observational_alma_primary)
- question: How do the three-dimensional spatial and velocity distributions of CO and SiO molecules in the ejecta of SN 1987A observed with ALMA compare with long-time 3D hydrodynamical supernova explosion simulations across different progenitor model…
- step 4: Estimate 3D dust mass-velocity distribution from ALMA Band 7 continuum
  - method: Using ALMA Band 7 continuum data (315 GHz), compute dust mass vs velocity under two approximations: (1) all dust velocities are in the plane of the sky; (2) ballistic expansion up to 3500 km s^-1 with dust density declining as r^-2 along t… [3D distribution of dust emission: "To estimate the effect this might have when comparing the observations to theory, we calculated the distribution of dust mass with velocity using ALMA band 7 continuum data"] [3D distribution of dust emission: "A simple limiting case then assumes that all dust velocities are in the plane of the sky."]
  - parameter: Maximum shell velocity = 3500 km s^-1; radial density profile proportional to r^-2 [3D distribution of dust emission: "At a given pixel position, if the dust shell is expanding with a velocity proportional to distance from the explosion point (ballistic expansion), then the dust velocities lie between the plane-of-sky velocity of the point and the maximum velocity of the shell, estimated at 3500 km s$^{-1}$."]
  - assumption: Dust has uniform temperature and negligible optical depth; ballistic expansion; r^-2 density profile [3D distribution of dust emission: "We assume that the dust is at a uniform temperature, and that its optical depth is negligible, such that the dust mass along a given line of sight is directly proportional to the observed flux."]
  - validation: Comparison of plane-of-sky limiting case with 1/r^2 line-of-sight velocity distribution [3D distribution of dust emission: "The left-hand panel assuming no velocity along the line of sight will systematically underestimate total velocities."]
- limitation (authors): SiO J=5-4 Epoch 2 cube is truncated at +2000 km s^-1 on the receding side due to insufficient spectral bandwidth. [Integrated line profiles: "it can also be seen that the SiO 5–4 data from the second epoch of observations (green line, bottom panel) is truncated on the far side at a velocity of +2000 kms$^{-1}$, due to the bandwidth not being sufficient to cover the entire range of velocities."]
- limitation (authors): High-velocity molecular emission in the ALMA cubes may be buried in noise or excluded by the spatial cut-off used to avoid contamination from the equatorial ring. [Summary and discussion: "Too high model predictions for the velocity could simply mean that the material is not detected, because it is either buried in the noise, or it is at such high velocities that the ejecta are excluded by the truncation of the data to avoid contamination from the ring of SN 1987A."]
- limitation (authors): Explosion energy and energy deposition timescale are free parameters in the approximate ray-by-ray neutrino transport scheme, and 56Ni yields have uncertainties due to the electron fraction Ye. [Summary and discussion: "Our approximate approach of the neutrino transport allows us to choose the explosion energy (and the energy deposition time scale) as a free parameter, and it is not calculated self-consistently."]
- not stated (card): Exact CASA and ALMA pipeline versions used for calibration and imaging; Specific frequency/channel ranges used as line-free channels for continuum subtraction; Deconvolver, weighting scheme (for 2017 SiO 5-4 and Epoch 1), masking, and threshold parameters in CASA clean; Exact coordinates of the four off-source regions outside the equatorial ring used to calculate the MAD noise threshold; How the …

## All papers in this technique

- 2012A&A...544L...7P (2012): The first ALMA view of IRAS 16293-2422. Direct detection of infall onto source B and high-resolution kinematics of source A
- 2012ApJ...761L..20R (2012): ALMA Observations of ρ-Oph 102: Grain Growth and Molecular Gas in the Disk around a Young Brown Dwarf
- 2013A&A...552L..10S (2013): A candidate circumbinary Keplerian disk in G35.20-0.74 N: A study with ALMA
- 2013A&A...557A.132M (2013): ALMA imaging of the CO snowline of the HD 163296 disk with DCO<SUP>+</SUP>
- 2013A&A...557A.133D (2013): Unveiling the gas-and-dust disk structure in HD 163296 using ALMA observations
- 2013ApJ...762L..21M (2013): Millimeter Emission Structure in the First ALMA Image of the AU Mic Debris Disk
- 2013ApJ...764L..14Z (2013): ALMA 690 GHz Observations of IRAS 16293-2422B: Infall in a Highly Optically Thick Disk
- 2013ApJ...774...39A (2013): ALMA Observations of the HH 46/47 Molecular Outflow
- 2013ApJ...774...73I (2013): ALMA Resolves 30 Doradus: Sub-parsec Molecular Cloud Structure near the Closest Super Star Cluster
- 2013ApJ...774L...7M (2013): ALMA Observations of the Massive Molecular Outflow G331.512-0.103
- 2013ApJ...777...92S (2013): ALMA Observations of the Coldest Place in the Universe: The Boomerang Nebula
- 2013ApJ...779...96T (2013): The Dynamics of Massive Starless Cores with ALMA
- 2013PASJ...65L..14F (2013): Local Enhancement of the Surface Density in the Protoplanetary Ring Surrounding HD 142527
- 2013Sci...340.1199V (2013): A Major Asymmetric Dust Trap in a Transition Disk
- 2014A&A...561A..49H (2014): ALMA observations of cool dust in a low-metallicity starburst, SBS 0335-052
- 2014A&A...562A..67G (2014): ALMA reveals a warm and compact starburst around a heavily obscured supermassive black hole at z = 4.75
- 2014A&A...566A..74L (2014): ALMA observations of the kinematics and chemistry of disc formation
- 2014A&A...567A.125G (2014): Molecular line emission in NGC 1068 imaged with ALMA. I. An AGN-driven outflow in the dense molecular gas
- 2014A&A...569A..11S (2014): A necklace of dense cores in the high-mass star forming region G35.20-0.74 N: ALMA observations
- 2014ApJ...783L..13P (2014): Large-scale Asymmetries in the Transitional Disks of SAO 206462 and SR 21
- 2014ApJ...784...82M (2014): ALMA Observations of the Orion Proplyds
- 2014ApJ...785...44M (2014): A 10<SUP>10</SUP> Solar Mass Flow of Molecular Gas in the A1835 Brightest Cluster Galaxy
- 2014ApJ...785..111W (2014): Properties of Submillimeter Galaxies in the CANDELS GOODS-South Field
- 2014ApJ...787...42C (2014): An ALMA Continuum Survey of Circumstellar Disks in the Upper Scorpius OB Association
- 2014ApJ...787...48X (2014): ALMA Observations of Warm Molecular Gas and Cold Dust in NGC 34
- 2014ApJ...788L..34P (2014): Resolved Images of the Protoplanetary Disk around HD 100546 with ALMA
- 2014ApJ...789L...4T (2014): ALMA Observations of a High-density Core in Taurus: Dynamical Gas Interaction at the Possible Site of a Multiple Star Formation
- 2014ApJ...791...20R (2014): Brown Dwarf Disks with ALMA
- 2014ApJ...791...42Z (2014): Comparison of the Dust and Gas Radial Structure in the Transition Disk [PZ99] J160421.7-213028
- 2014ApJ...791..108F (2014): Distributed Low-mass Star Formation in the IRDC G34.43+00.24
- 2014ApJ...791L...6W (2014): ALMA Hints at the Presence of two Companions in the Disk around HD 100546
- 2014ApJ...792...34O (2014): ALMA Observation of 158 μm [C II] Line and Dust Continuum of a z = 7 Normally Star-forming Galaxy in the Epoch of Reionization
- 2014ApJ...792L..25V (2014): Spatially Resolved HCN J = 4-3 and CS J = 7-6 Emission from the Disk around HD 142527
- 2014ApJ...793....1Y (2014): ALMA Observations of Infalling Flows toward the Keplerian Disk around the Class I Protostar L1489 IRS
- 2014ApJ...795L..25R (2014): Turbulence Sets the Initial Conditions for Star Formation in High-pressure Environments
- 2014ApJ...796....1T (2014): Angular Momentum Exchange by Gravitational Torques and Infall in the Circumbinary Disk of the Protostellar System L1551 NE
- 2014ApJ...796...84R (2014): ALMA Imaging of Gas and Dust in a Galaxy Protocluster at Redshift 5.3: [C II] Emission in "Typical" Galaxies and Dusty Starbursts ≈1 Billio…
- 2014ApJ...797...27F (2014): Revealing H<SUB>2</SUB>D<SUP>+</SUP> Depletion and Compact Structure in Starless and Protostellar Cores with ALMA
- 2014MNRAS.438.1267S (2014): An ALMA survey of sub-millimetre Galaxies in the Extended Chandra Deep Field South: the far-infrared properties of SMGs
- 2014MNRAS.444.1821F (2014): ALMA and Herschel observations of the prototype dusty and polluted white dwarf G29-38
- 2014Natur.510..247H (2014): Two γ-ray bursts from dusty regions with little molecular gas
- 2014Natur.514..600D (2014): Possible planet formation in the young, low-mass, multiple stellar system GG Tau A
- 2014Sci...343.1490D (2014): Molecular Gas Clumps from the Destruction of Icy Bodies in the β Pictoris Debris Disk
- 2015A&A...573L...1O (2015): ALMA observations of anisotropic dust mass loss in the inner circumstellar environment of the red supergiant VY Canis Majoris
- 2015A&A...574A..19S (2015): New constraints on dust emission and UV attenuation of z = 6.5-7.5 galaxies from millimeter observations
- 2015A&A...575L...5H (2015): High-resolution observations of the outer disk around T Chamaeleontis: the view from ALMA
- 2015A&A...576L..15O (2015): ALMA view of the circumstellar environment of the post-common-envelope-evolution binary system HD 101584
- 2015A&A...582L...5R (2015): An ALMA survey for disks orbiting low-mass stars in the TW Hya Association
- 2015A&A...583A..66H (2015): Probing the final stages of protoplanetary disk evolution with ALMA
- 2015A&A...584A..99E (2015): The Dragonfly Galaxy. II. ALMA unveils a triple merger and gas exchange in a hyper-luminous radio galaxy at z = 2
- 2015ApJ...798L..23K (2015): An ALMA Disk Mass for the Candidate Protoplanetary Companion to FW Tau
- 2015ApJ...798L..33H (2015): IRAS 16547-4247: A New Candidate of a Protocluster Unveiled with ALMA
- 2015ApJ...799...11X (2015): ALMA Observations of Warm Dense Gas in NGC 1614—Breaking of the Star Formation Law in the Central Kiloparsec
- 2015ApJ...799..204C (2015): Constraining the X-Ray and Cosmic-Ray Ionization Chemistry of the TW Hya Protoplanetary Disk: Evidence for a Sub-interstellar Cosmic-Ray Ra…
- 2015ApJ...800...70S (2015): ALMA Imaging of HCN, CS, and Dust in Arp 220 and NGC 6240
- 2015ApJ...801...82H (2015): ALMA Imaging of Millimeter/Submillimeter Continuum Emission in Orion KL
- 2015ApJ...802..125R (2015): A Cluster in the Making: ALMA Reveals the Initial Conditions for High-mass Cluster Formation
- 2015ApJ...803...60S (2015): ALMA Multi-line Observations of the IR-bright Merger VV 114
- 2015ApJ...804...37L (2015): ALMA Resolves the Spiraling Accretion Flow in the Luminous OB Cluster-forming Region G33.92+0.11
- 2015ApJ...804..141Z (2015): Fragmentation of Molecular Clumps and Formation of a Protocluster
- 2015ApJ...805...21C (2015): Gas Inside the 97 AU Cavity around the Transition Disk Sz 91
- 2015ApJ...805L..17B (2015): An ALMA Constraint on the GSC 6214-210 B Circum-Substellar Accretion Disk Mass
- 2015ApJ...806...35J (2015): The Physical Conditions in a Pre-super Star Cluster Molecular Cloud in the Antennae Galaxies
- 2015ApJ...806..260F (2015): Band-9 ALMA Observations of the [N II] 122 μm Line and FIR Continuum in Two High-z galaxies.
- 2015ApJ...807L...4F (2015): High-mass Star Formation Triggered by Collision between CO Filaments in N159 West in the Large Magellanic Cloud
- 2015ApJ...808...69B (2015): ALMA Observations of the Largest Proto-Planetary Disk in the Orion Nebula, 114-426: A CO Silhouette
- 2015ApJ...808..102K (2015): Resolving Protoplanetary Disks at Millimeter Wavelengths with CARMA
- 2015ApJ...810...91H (2015): Optical-Infrared Properties of Faint 1.3 mm Sources Detected with ALMA
- 2015ApJ...811..124S (2015): Sub-kiloparsec Imaging of Cool Molecular Gas in Two Strongly Lensed Dusty, Star-forming Galaxies
- 2015ApJ...812..126C (2015): A Compact Concentration of Large Grains in the HD 142527 Protoplanetary Dust Trap
- 2015ApJ...812..129Y (2015): No Keplerian Disk &gt;10 AU Around the Protostar B335: Magnetic Braking or Young Age?
- 2015ApJ...812..134H (2015): The Early ALMA View of the FU Ori Outburst System
- 2015ApJ...813L..19J (2015): A Keplerian-like Disk around the Forming O-type Star AFGL 4176
- 2015ApJ...814...22E (2015): Detection of Infall in the Protostar B335 with ALMA
- 2015MNRAS.447.1826Z (2015): ALMA reveals a candidate hot and compact disc around the O-type protostar IRAS 16547-4247
- 2015MNRAS.449..715W (2015): Tracing the conversion of gas into stars in Young Massive Cluster Progenitors
- 2015MNRAS.452...54M (2015): The assembly of `normal' galaxies at z ∼ 7 probed by ALMA
- 2015MNRAS.452.2258D (2015): Revealing the complex nature of the strong gravitationally lensed system H-ATLAS J090311.6+003906 using ALMA
- 2015Natur.519..327W (2015): A dusty, normal galaxy in the epoch of reionization
- 2015PASJ...67..122M (2015): Significant gas-to-dust ratio asymmetry and variation in the disk of HD 142527 and the indication of gas depletion
- 2016A&A...585A..58V (2016): Resolved gas cavities in transitional disks inferred from CO isotopologs with ALMA
- 2016A&A...590A..33P (2016): Constraining the physical structure of the inner few 100 AU scales of deeply embedded low-mass protostars
- 2016A&A...591A..73G (2016): ALMA finds dew drops in the dusty spider's web
- 2016A&A...593A.111T (2016): Brown dwarf disks with ALMA: Evidence for truncated dust disks in Ophiuchus
- 2016A&A...593L..14F (2016): Magnetically regulated fragmentation of a massive, dense, and turbulent clump
- 2016A&A...595A.113S (2016): Shadows cast on the transition disk of HD 135344B. Multiwavelength VLT/SPHERE polarimetric differential imaging
- 2016A&A...596A..50G (2016): The ALMA detection of CO rotational line emission in AGB stars in the Large Magellanic Cloud
- 2016A&A...596A..75S (2016): Characterizing elusive, faint dusty star-forming galaxies: a lensed, optically undetected ALMA galaxy at z 3.3
- 2016A&A...596A..88L (2016): ALMA observations of the <ASTROBJ>Th 28</ASTROBJ> protostellar disk. A new example of counter-rotation between disk and optical jet
- 2016ApJ...816...37V (2016): Bright [C II] and Dust Emission in Three z &gt; 6.6 Quasar Host Galaxies Observed by ALMA
- 2016ApJ...819...82S (2016): Properties of the Interstellar Medium in Star-Forming Galaxies at z ~ 1.4 Revealed with ALMA
- 2016ApJ...819..102V (2016): Dust Masses of Disks around 8 Brown Dwarfs and Very Low-mass Stars in Upper Sco OB1 and Ophiuchus
- 2016ApJ...819L...7N (2016): ALMA Observations of a Gap and a Ring in the Protoplanetary Disk around TW Hya
- 2016ApJ...821..112K (2016): SMA Observations of the Extended <SUP>12</SUP>CO(J = 6-5) Emission in the Starburst Galaxy NGC 253
- 2016ApJ...821L..16C (2016): The VLA View of the HL Tau Disk: Disk Mass, Grain Evolution, and Early Planet Formation
- 2016ApJ...822...80S (2016): The Redshift Distribution of Dusty Star-forming Galaxies from the SPT Survey
- 2016ApJ...823..160D (2016): An ALMA Search for Substructure, Fragmentation, and Hidden Protostars in Starless Cores in Chamaeleon I
- 2016ApJ...823L..12G (2016): ALMA Resolves the Torus of NGC 1068: Continuum and Molecular Line Emission
- 2016ApJ...825L..15C (2016): Interferometric Mapping of Magnetic Fields: The ALMA View of the Massive Star-forming Clump W43-MM1
- 2016ApJ...825L..16M (2016): Protoplanetary Disks in the Hostile Environment of Carina
- 2016ApJ...826...16E (2016): Protoplanetary Disks in the Orion OMC1 Region Imaged with ALMA
- 2016ApJ...826...26T (2016): Revealing a Detailed Mass Distribution of a High-density Core MC27/L1521F in Taurus with ALMA
- 2016ApJ...827...72S (2016): The Detection of a Hot Molecular Core in the Large Magellanic Cloud with ALMA
- 2016ApJ...827..133L (2016): Star Formation and Feedback: A Molecular Outflow-Prestellar Core Interaction in L1689N
- 2016ApJ...827..142B (2016): ALMA Observations of Circumstellar Disks in the Upper Scorpius OB Association
- 2016ApJ...828...46A (2016): ALMA Survey of Lupus Protoplanetary Disks. I. Dust and Gas Masses
- 2016ApJ...828...50K (2016): The Molecular Clouds Fueling A 1/5 Solar Metallicity Starburst
- 2016ApJ...828..100F (2016): Outflow Detection in a 70 μm Dark High-Mass Core
- 2016ApJ...830L..16B (2016): Misaligned Disks in the Binary Protostar IRS 43
- 2016ApJ...831..101B (2016): Hydrocarbon Emission Rings in Protoplanetary Disks Induced by Dust Evolution
- 2016ApJ...831..125P (2016): A Steeper than Linear Disk Mass-Stellar Mass Scaling Relation
- 2016ApJ...831..200W (2016): ALMA Reveals the Anatomy of the mm-sized Dust and Molecular Gas in the HD 97048 Disk
- 2016ApJ...832..110C (2016): The Coupled Physical Structure of Gas and Dust in the IM Lup Protoplanetary Disk
- 2016ApJ...832..148V (2016): Molecular Gas Along a Bright Hα Filament in 2A 0335+096 Revealed by ALMA
- 2016ApJ...832..158Z (2016): ALMA Cycle 1 Observations of the HH46/47 Molecular Outflow: Structure, Entrainment, and Core Impact
- 2016ApJ...832..178V (2016): Vortices and Spirals in the HD135344B Transition Disk
- 2016ApJ...832..187B (2016): The Massive Protostellar Cluster NGC 6334I at 220 au Resolution: Discovery of Further Multiplicity, Diversity, and a Hot Multi-core
- 2016ApJ...833...12R (2016): VLA and ALMA Imaging of Intense Galaxy-wide Star Formation in z ∼ 2 Galaxies
- 2016ApJ...833...68A (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Continuum Number Counts, Resolved 1.2 mm Extragalactic Background, and Proper…
- 2016ApJ...833...70D (2016): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Molecular Gas Reservoirs in High-redshift Galaxies
- 2016ApJ...833..103H (2016): Kiloparsec-scale Dust Disks in High-redshift Luminous Submillimeter Galaxies
- 2016ApJ...833..209O (2016): Dense Core Properties in the Infrared Dark Cloud G14.225-0.506 Revealed by ALMA
- 2016ApJ...833..219P (2016): ALMA Observations of Orion Source I at 350 and 660 GHz
- 2016ApJ...833L...6C (2016): ALMA Reveals Potential Localized Dust Enrichment from Massive Star Clusters in II Zw 40
- 2016MNRAS.457.4536W (2016): Comparing young massive clusters and their progenitor clouds in the Milky Way
- 2016MNRAS.458L..29C (2016): A ring-like concentration of mm-sized particles in Sz 91
- 2016MNRAS.459.4518H (2016): The detection of dust around NN Ser
- 2016Natur.538..483T (2016): A triple protostar system formed via fragmentation of a gravitationally unstable disk
- 2016PASJ...68...20S (2016): Spatially resolved radio-to-far-infrared SED of the luminous merger remnant NGC 1614 with ALMA and VLA
- 2016PASJ...68..103F (2016): A massive dense gas cloud close to the nucleus of the Seyfert galaxy NGC 1068
- 2016PASJ...68L...7T (2016): Galactic center mini-spiral by ALMA: Possible origin of the central cluster
- 2016Sci...353.1519P (2016): Spiral density waves in a young protoplanetary disk
- 2017A&A...597A..17H (2017): A search for pre- and proto-brown dwarfs in the dark cloud Barnard 30 with ALMA
- 2017A&A...597A..32V (2017): Cavity and other radial substructures in the disk around HD 97048
- 2017A&A...597A..99W (2017): ALMA Compact Array observations of the Fried Egg nebula. Evidence for large-scale asymmetric mass-loss from the yellow hypergiant IRAS 1716…
- 2017A&A...599A.101V (2017): Robustness of N<SUB>2</SUB>H<SUP>+</SUP> as tracer of the CO snowline
- 2017A&A...599A.113M (2017): Lupus disks with faint CO isotopologues: low gas/dust or high carbon depletion?
- 2017A&A...600A..72F (2017): ALMA unveils rings and gaps in the protoplanetary system <ASTROBJ>HD 169142</ASTROBJ>: signatures of two giant protoplanets
- 2017A&A...600A.141K (2017): Resolving the fragmentation of high line-mass filaments with ALMA: the integral shaped filament in Orion A
- 2017A&A...600L...3C (2017): Planck's dusty GEMS. III. A massive lensing galaxy with a bottom-heavy stellar initial mass function at z = 1.5
- 2017A&A...600L..10C (2017): ALMA survey of massive cluster progenitors from ATLASGAL. Limited fragmentation at the early evolutionary stage of massive clumps
- 2017A&A...601A...5H (2017): ALMA observations of the nearby AGB star L<SUB>2</SUB> Puppis. II. Gas disk properties derived from <SUP>12</SUP>CO and <SUP>13</SUP>CO J =…
- 2017A&A...601L...3P (2017): First detection of the 448 GHz H<SUB>2</SUB>O transition in space
- 2017A&A...602A..11P (2017): ALMA reveals starburst-like interstellar medium conditions in a compact star-forming galaxy at z 2 using [CI] and CO
- 2017A&A...602A..19L (2017): A concordant scenario to explain FU Orionis from deep centimeter and millimeter interferometric observations
- 2017A&A...602A..59C (2017): Chasing discs around O-type (proto)stars: Evidence from ALMA observations
- 2017A&A...603A..10B (2017): Fragmentation and disk formation in high-mass star formation: The ALMA view of G351.77-0.54 at 0.06'' resolution
- 2017A&A...603A..92V (2017): Magnetically aligned dust and SiO maser polarisation in the envelope of the red supergiant VY Canis Majoris
- 2017A&A...603A.133A (2017): Chemical segregation in hot cores with disk candidates. An investigation with ALMA
- 2017A&A...604A...6S (2017): The physical and chemical structure of Sagittarius B2. II. Continuum millimeter emission of Sgr B2(M) and Sgr B2(N) with ALMA
- 2017A&A...604A..60B (2017): Exploring molecular complexity with ALMA (EMoCA): Detection of three new hot cores in Sagittarius B2(N)
- 2017A&A...605A.105C (2017): AGN feedback on molecular gas reservoirs in quasars at z 2.4
- 2017A&A...606A..17M (2017): An ALMA survey of submillimetre galaxies in the COSMOS field: Physical properties derived from energy balance spectral energy distribution …
- 2017A&A...606A..88T (2017): Physical properties of dusty protoplanetary disks in Lupus: evidence for viscous evolution?
- 2017A&A...606A.121L (2017): Complex organics in IRAS 4A revisited with ALMA and PdBI: Striking contrast between two neighbouring protostellar cores
- 2017A&A...607A..55V (2017): An 80 au cavity in the disk around HD 34282
- 2017A&A...608A..22A (2017): Luminous, pc-scale CO 6-5 emission in the obscured nucleus of NGC 1377
- 2017A&A...608A..56G (2017): ALMA imaging of C<SUB>2</SUB>H emission in the disk of <ASTROBJ>NGC 1068</ASTROBJ>
- 2017AJ....153..240A (2017): An ALMA Survey of Protoplanetary Disks in the σ Orionis Cluster
- 2017AJ....154...24R (2017): ALMA Observations of the Young Substellar Binary System 2M1207
- 2017AJ....154..234W (2017): An Explanation of the Very Low Radio Flux of Young Planet-mass Companions
- 2017ApJ...834..178Y (2017): Signs of Early-stage Disk Growth Revealed with ALMA
- 2017ApJ...835...17M (2017): ALMA Measurements of Circumstellar Material in the GQ Lup System
- 2017ApJ...835..108S (2017): Kinematic Structure of Molecular Gas around High-mass YSO, Papillon Nebula, in N159 East in the Large Magellanic Cloud: A New Perspective w…
- 2017ApJ...835..213P (2017): The Dense Molecular Gas and Nuclear Activity in the ULIRG IRAS 13120-5453
- 2017ApJ...835..228T (2017): A Surface Density Perturbation in the TW Hydrae Disk at 95 au Traced by Molecular Emission
- 2017ApJ...835L..11T (2017): Grand-design Spiral Arms in a Young Forming Circumstellar Disk
- 2017ApJ...835L..13S (2017): ALMA Observations of the Water Fountain Pre-planetary Nebula IRAS 16342-3814: High-velocity Bipolar Jets and an Expanding Torus
- 2017ApJ...835L..23I (2017): Evidence for a Dusty Dark Dwarf Galaxy in the Quadruple Lens MG 0414+0534
- 2017ApJ...836....8T (2017): ALMA Observations Show Major Mergers Among the Host Galaxies of Fast-growing, High-redshift Supermassive Black Holes
- 2017ApJ...836...30G (2017): Nitrogen Fractionation in Protoplanetary Disks from the H<SUP>13</SUP>CN/HC<SUP>15</SUP>N Ratio
- 2017ApJ...836..223W (2017): An ALMA and MagAO Study of the Substellar Companion GQ Lup B*
- 2017ApJ...837...86T (2017): Spiral Arms, Infall, and Misalignment of the Circumbinary Disk from the Circumstellar Disks in the Protostellar Binary System L1551 NE
- 2017ApJ...837..146V (2017): The Compact, ∼1 kpc Host Galaxy of a Quasar at a Redshift of 7.1
- 2017ApJ...837..182O (2017): ALMACAL II: Extreme Star Formation Rate Densities in Dusty Starbursts Revealed by ALMA 20 mas Resolution Imaging
- 2017ApJ...837L..21L (2017): Dust in the Reionization Era: ALMA Observations of a z = 8.38 Gravitationally Lensed Galaxy
- 2017ApJ...838..114K (2017): ALMA Observations of Starless Core Substructure in Ophiuchus
- 2017ApJ...839...58S (2017): The SCUBA-2 Cosmology Legacy Survey: Multi-wavelength Properties of ALMA-identified Submillimeter Galaxies in UKIDSS UDS
- 2017ApJ...839...99P (2017): A Multi-wavelength Analysis of Dust and Gas in the SR 24S Transition Disk
- 2017ApJ...839L..24M (2017): On the Origin of the Spiral Morphology in the Elias 2-27 Circumstellar Disk
- 2017ApJ...840...60B (2017): A Close-up View of the Young Circumbinary Disk HD 142527
- 2017ApJ...841..110S (2017): The Coldest Place in the Universe: Probing the Ultra-cold Outflow and Dusty Disk in the Boomerang Nebula
- 2017ApJ...841..130A (2017): The Luminous Blue Variable RMC 127 as Seen with ALMA and ATCA
- 2017ApJ...841L..11B (2017): First Millimeter Detection of the Disk around a Young, Isolated, Planetary-mass Object
- 2017ApJ...841L..25T (2017): Rotating Starburst Cores in Massive Galaxies at z = 2.5
- 2017ApJ...842....8M (2017): A Complete ALMA Map of the Fomalhaut Debris Disk
- 2017ApJ...842...92G (2017): Thermal Feedback in the High-mass Star- and Cluster-forming Region W51
- 2017ApJ...843...45K (2017): Mass Transport from the Envelope to the Disk of V346 Nor: A Case Study for the Luminosity Problem in an FUor-type Young Eruptive Star
- 2017ApJ...844...99L (2017): An ALMA Survey of CO Isotopologue Emission from Protoplanetary Disks in Chamaeleon I
- 2017ApJ...844..123F (2017): The Circumgalactic Medium of Submillimeter Galaxies. II. Unobscured QSOs within Dusty Starbursts and QSO Sightlines with Impact Parameters …
- 2017ApJ...845...10F (2017): Strongly Misaligned Triple System in SR 24 Revealed by ALMA
- 2017ApJ...845..175J (2017): Galaxy Formation through Filamentary Accretion at z = 6.1
- 2017ApJ...845L...5I (2017): On the Disappearance of a Cold Molecular Torus around the Low-luminosity Active Galactic Nucleus of NGC 1097
- 2017ApJ...846...70P (2017): Millimeter Spectral Indices and Dust Trapping By Planets in Brown Dwarf Disks
- 2017ApJ...846..108C (2017): A Spatially Resolved Study of Cold Dust, Molecular Gas, H II Regions, and Stars in the z = 2.12 Submillimeter Galaxy ALESS67.1
- 2017ApJ...846L..26W (2017): An ALMA Dynamical Mass Estimate of the Proposed Planetary-mass Companion FW Tau C
- 2017ApJ...847...92H (2017): ALMA Observations of Dust Polarization and Molecular Line Emission from the Class 0 Protostellar Source Serpens SMM1
- 2017ApJ...847..108W (2017): Discovery of Striking Difference of Molecular-emission-line Richness in the Potential Proto-binary System NGC 2264 CMM3
- 2017ApJ...848L..11K (2017): Dust-trapping Vortices and a Potentially Planet-triggered Spiral Wake in the Pre-transitional Disk of V1247 Orionis
- 2017ApJ...849...14S (2017): Resolved Structure of the Arp 220 Nuclei at λ ≈ 3 mm
- 2017ApJ...849...25L (2017): ALMA Reveals Sequential High-mass Star Formation in the G9.62+0.19 Complex
- 2017ApJ...849...68S (2017): Very Large Array Ammonia Observations of the HH 111/HH 121 Protostellar System: A Detection of a New Source with a Peculiar Chemistry
- 2017ApJ...849...81A (2017): Diverse Nuclear Star-forming Activities in the Heart of NGC 253 Resolved with 10-pc-scale ALMA Images
- 2017ApJ...849..123M (2017): Molecular Gas in Debris Disks around Young A-type Stars
- 2017ApJ...850....1R (2017): Rise of the Titans: A Dusty, Hyper-luminous “870 μm Riser” Galaxy at z ∼ 6
- 2017ApJ...850L...2A (2017): ALMA Observations of SMM11 Reveal an Extremely Young Protostar in Serpens Main Cluster
- 2017ApJ...850L...6A (2017): ALMA Discovery of Dust Belts around Proxima Centauri
- 2017ApJ...850L..30Y (2017): ALMA Detection of Bipolar Outflows: Evidence for Low-mass Star Formation within 1 pc of Sgr A*
- 2017ApJ...851...83C (2017): Protoplanetary Disks in ρ Ophiuchus as Seen from ALMA
- 2017ApJ...851...85B (2017): Measurement of Circumstellar Disk Sizes in the Upper Scorpius OB Association with ALMA
- 2017ApJ...851...98T (2017): No Sign of Strong Molecular Gas Outflow in an Infrared-bright Dust-obscured Galaxy with Strong Ionized-gas Outflow
- 2017ApJ...851..145M (2017): ALMA Reveals Metals yet No Dust within Multiple Components in CR7
- 2017ApJ...851L..23C (2017): ALMA Observations of Elias 2-24: A Protoplanetary Disk with Multiple Gaps in the Ophiuchus Molecular Cloud
- 2017ApJ...851L..40B (2017): Spatially Resolved Kinematics in the Central 1 kpc of a Compact Star-forming Galaxy at z ∼2.3 from ALMA CO Observations
- 2017MNRAS.464L..31H (2017): Unveiling the early-stage anatomy of a protocluster hub with ALMA
- 2017MNRAS.465..834Z (2017): The ALMA early science view of FUor/EXor objects - I. Through the looking-glass of V2775 Ori
- 2017MNRAS.465.4390B (2017): The discovery of gas-rich, dusty starbursts in luminous reddened quasars at z ∼ 2.5 with ALMA
- 2017MNRAS.466..138K (2017): A merger in the dusty, z = 7.5 galaxy A1689-zD1?
- 2017MNRAS.466..213A (2017): New ATCA, ALMA and VISIR observations of the candidate LBV SK -67 266 (S61): the nebular mass from modelling 3D density distributions
- 2017MNRAS.467L.120M (2017): The ALMA view of W33A: a spiral filament feeding the candidate disc in MM1-Main
- 2017MNRAS.468..685Q (2017): Modelling the 3D physical structure of astrophysical sources with gass
- 2017MNRAS.468.3468G (2017): Molecular gas on large circumgalactic scales at z = 3.47
- 2017MNRAS.468.3694C (2017): Simultaneous low- and high-mass star formation in a massive protocluster: ALMA observations of G11.92-0.61<SUP>★</SUP>
- 2017MNRAS.468L..87C (2017): New ALMA constraints on the star-forming interstellar medium at low metallicity: a 50 pc view of the blue compact dwarf galaxy SBS 0335-052
- 2017MNRAS.469.2230M (2017): Detection of methyl isocyanate (CH<SUB>3</SUB>NCO) in a solar-type protostar
- 2017MNRAS.469.4683C (2017): ALMA constraints on star-forming gas in a prototypical z = 1.5 clumpy galaxy: the dearth of CO(5-4) emission from UV-bright clumps
- 2017NatAs...1E.130Z (2017): Mass inventory of the giant-planet formation zone in a solar nebula analogue
- 2017NatAs...1E.172L (2017): Formation of wide binaries by turbulent fragmentation
- 2017Natur.545..457D (2017): Rapidly star-forming galaxies adjacent to quasars at redshifts exceeding 6
- 2017PASJ...69...34S (2017): Detailed modeling of dust distribution in the disk of HD 142527
- 2018A&A...610A..24F (2018): ALMA continuum observations of the protoplanetary disk AS 209. Evidence of multiple gaps opened by a single planet
- 2018A&A...611A..22S (2018): Jekyll &amp; Hyde: quiescence and extreme obscuration in a pair of massive galaxies 1.5 Gyr after the Big Bang
- 2018A&A...611A..99K (2018): The evolution of young HII regions. I. Continuum emission and internal dynamics
- 2018A&A...614A..17B (2018): Modelling the carbon AGB star R Sculptoris. Constraining the dust properties in the detached shell based on far-infrared and sub-millimeter…
- 2018A&A...614A..26A (2018): Chemistry of a newly detected circumbinary disk in Ophiuchus
- 2018A&A...614A..64B (2018): Magnetic fields at the onset of high-mass star formation
- 2018A&A...614A.106C (2018): Probing midplane CO abundance and gas temperature with DCO<SUP>+</SUP> in the protoplanetary disk around HD 169142
- 2018A&A...614A.113H (2018): ALMA detection of a tentative nearly edge-on rotating disk around the nearby AGB star R Doradus
- 2018A&A...615A...9P (2018): Distribution of Serpens South protostars revealed with ALMA
- 2018A&A...615A..28D (2018): ALMA spectral line and imaging survey of a low and a high mass-loss rate AGB star between 335 and 362 GHz
- 2018A&A...615A..83V (2018): Unveiling the physical conditions of the youngest disks. A warm embedded disk in L1527
- 2018A&A...615A..94F (2018): Fragmentation properties of massive protocluster gas clumps: an ALMA study
- 2018A&A...615A..95P (2018): Resolved millimeter-dust continuum cavity around the very low mass young star CIDA 1
- 2018A&A...615A.141B (2018): Accelerating infall and rotational spin-up in the hot molecular core G31.41+0.31
- 2018A&A...615L..10M (2018): Unlocking the secrets of the midplane gas and dust distribution in the young hybrid disc HD 141569
- 2018A&A...616A..34H (2018): An unusual face-on spiral in the wind of the M-type AGB star EP Aquarii
- 2018A&A...616A..66M (2018): The feedback of an HC HII region on its parental molecular core. The case of core A1 in the star-forming region G24.78+0.08
- 2018A&A...616A..88V (2018): V1094 Scorpii: A rare giant multi-ringed disk around a T Tauri star
- 2018A&A...616A.100Y (2018): Stellar masses and disk properties of Lupus young stellar objects traced by velocity-aligned stacked ALMA <SUP>13</SUP>CO and C<SUP>18</SUP…
- 2018A&A...616A.110E (2018): Starbursts in and out of the star-formation main sequence
- 2018A&A...616L..10F (2018): ALMA observations of RCW 120 Fragmentation at 0.01 pc scale&amp;star
- 2018A&A...617A..28S (2018): Chemistry in disks. XI. Sulfur-bearing species as tracers of protoplanetary disk physics and chemistry: the DM Tau case
- 2018A&A...617A..89C (2018): Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). I. Indication for a centrifugal barrier in the enviro…
- 2018A&A...618A.164S (2018): Through the magnifying glass: ALMA acute viewing of the intricate nebular architecture of OH 231.8+4.2
- 2018A&A...619A.161C (2018): Evidence for a massive dust-trapping vortex connected to spirals. Multi-wavelength analysis of the HD 135344B protoplanetary disk
- 2018A&A...620A..31M (2018): Chasing discs around O-type (proto)stars. ALMA evidence for an SiO disc and disc wind from G17.64+0.16
- 2018AJ....155...54W (2018): The Taurus Boundary of Stellar/Substellar (TBOSS) Survey. II. Disk Masses from ALMA Continuum Observations
- 2018AJ....156..239Z (2018): ALMA Reveals a Collision between Protostellar Outflows in BHR 71
- 2018ApJ...852..122H (2018): CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations
- 2018ApJ...853..160C (2018): The Core Mass Function in the Massive Protocluster G286.21+0.17 Revealed by ALMA
- 2018ApJ...853..162B (2018): The Complex Morphology of the Young Disk MWC 758: Spirals and Dust Clumps around a Large Cavity
- 2018ApJ...853..171G (2018): Distributed Star Formation throughout the Galactic Center Cloud Sgr B2
- 2018ApJ...853..179T (2018): PHIBSS: Unified Scaling Relations of Gas Depletion Time and Molecular Gas Fractions
- 2018ApJ...854...15H (2018): Probing Episodic Accretion in Very Low Luminosity Objects
- 2018ApJ...854..177V (2018): New Insights into the Nature of Transition Disks from a Complete Disk Survey of the Lupus Star-forming Region
- 2018ApJ...854L...4R (2018): Cospatial Star Formation and Supermassive Black Hole Growth in z ∼ 3 Galaxies: Evidence for In Situ Co-evolution
- 2018ApJ...855...24P (2018): Thermal Jeans Fragmentation within ∼1000 au in OMC-1S
- 2018ApJ...856..118H (2018): Molecular Gas Reservoirs in Cluster Galaxies at z = 1.46
- 2018ApJ...856..121G (2018): Starburst to Quiescent from HST/ALMA: Stars and Dust Unveil Minor Mergers in Submillimeter Galaxies at z ∼ 4.5
- 2018ApJ...856..147O (2018): Gravitationally Unstable Condensations Revealed by ALMA in the TUKH122 Prestellar Core in the Orion A Cloud
- 2018ApJ...859...12G (2018): The Dust and [C II] Morphologies of Redshift ∼4.5 Sub-millimeter Galaxies at ∼200 pc Resolution: The Absence of Large Clumps in the Interst…
- 2018ApJ...859...32P (2018): Homogeneous Analysis of the Dust Morphology of Transition Disks Observed with ALMA: Investigating Dust Trapping and the Origin of the Cavit…
- 2018ApJ...859...35G (2018): The Dual Role of Starbursts and Active Galactic Nuclei in Driving Extreme Molecular Outflows
- 2018ApJ...859..103W (2018): Extended Millimeter Emission in the HD 141569 Circumstellar Disk Detected with ALMA
- 2018ApJ...859..111H (2018): The Circumstellar Disk and Asymmetric Outflow of the EX Lup Outburst System
- 2018ApJ...860...77E (2018): Protoplanetary Disk Properties in the Orion Nebula Cluster: Initial Results from Deep, High-resolution ALMA Observations
- 2018ApJ...860L..13P (2018): Kinematic Evidence for an Embedded Protoplanet in a Circumstellar Disk
- 2018ApJ...861...14C (2018): Infall Signatures in a Prestellar Core Embedded in the High-mass 70 μm Dark IRDC G331.372-00.116
- 2018ApJ...861...43P (2018): Hidden in Plain Sight: A Massive, Dusty Starburst in a Galaxy Protocluster at z = 5.7 in the COSMOS Field
- 2018ApJ...861...91H (2018): ALMA Observations of Polarized 872 μm Dust Emission from the Protostellar Systems VLA 1623 and L1527
- 2018ApJ...862..102S (2018): A Multiline Study of a High-mass Young Stellar Object in the Small Magellanic Cloud with ALMA: The Detection of Methanol Gas at 0.2 Solar M…
- 2018ApJ...862..105L (2018): The Core Mass Function across Galactic Environments. II. Infrared Dark Cloud Clumps
- 2018ApJ...862L...2F (2018): First Detection of the Simplest Organic Acid in a Protoplanetary Disk
- 2018ApJ...863...19A (2018): The Distinct Evolutionary Nature of Two Class 0 Protostars in Serpens Main SMM4
- 2018ApJ...863...61L (2018): An ALMA Survey of Faint Disks in the Chamaeleon I Star-forming Region: Why Are Some Class II Disks so Faint?
- 2018ApJ...864...76Z (2018): Rotation in the NGC 1333 IRAS 4C Outflow
- 2018ApJ...864L..25O (2018): The Co-evolution of Disks and Stars in Embedded Stages: The Case of the Very-low-mass Protostar IRAS 15398-3359
- 2018ApJ...865..131L (2018): High-resolution ALMA Study of the Proto-brown-dwarf Candidate L328-IRS
- 2018ApJ...866..159V (2018): Dust Emission in an Accretion-rate-limited Sample of z ≳ 6 Quasars
- 2018ApJ...867...43T (2018): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Perseus Protostars. VI. Characterizing the Formation Mechanism for Close Mult…
- 2018ApJ...867...94K (2018): Zooming in to Massive Star Birth
- 2018ApJ...868...75S (2018): Concurrent Starbursts in Molecular Gas Disks within a Pair of Colliding Galaxies at z = 1.52
- 2018ApJ...868L...3M (2018): ALMA Reveals a Misaligned Inner Gas Disk inside the Large Cavity of a Transitional Disk
- 2018ApJ...868L...5K (2018): A Spatially Resolved au-scale Inner Disk around DM Tau
- 2018ApJ...869...10M (2018): Comprehensive Analysis of HD 105, A Young Solar System Analog
- 2018ApJ...869...17L (2018): Gaps and Rings in an ALMA Survey of Disks in the Taurus Star-forming Region
- 2018ApJ...869...27V (2018): A Survey of Atomic Carbon [C I] in High-redshift Main-sequence Galaxies
- 2018ApJ...869...59W (2018): Physical and Chemical Conditions of the Protostellar Envelope and the Protoplanetary Disk in HL Tau
- 2018ApJ...869...75M (2018): ALMA Detection of Extended Millimeter Halos in the HD 32297 and HD 61005 Debris Disks
- 2018ApJ...869..115S (2018): Dust Polarization toward Embedded Protostars in Ophiuchus with ALMA. II. IRAS 16293-2422
- 2018ApJ...869..126L (2018): Forming Super Star Clusters in the Central Starburst of NGC 253
- 2018ApJ...869L..22W (2018): No Evidence for Enhanced [O III] 88 μm Emission in a z ∼ 6 Quasar Compared to Its Companion Starbursting Galaxy
- 2018ApJ...869L..24I (2018): G11.92-0.61 MM 1: A Fragmented Keplerian Disk Surrounding a Proto-O Star
- 2018ApJ...869L..46D (2018): The Disk Substructures at High Angular Resolution Project (DSHARP). VI. Dust Trapping in Thin-ringed Protoplanetary Disks
- 2018MNRAS.473..879P (2018): The ALMA early science view of FUor/EXor objects - IV. Misaligned outflows in the complex star-forming environment of V1647 Ori and McNeil'…
- 2018MNRAS.474.3640M (2018): CO excitation in the Seyfert galaxy NGC 34: stars, shock or AGN driven?
- 2018MNRAS.474.4039M (2018): ALMA + VLT observations of a damped Lyman-α absorbing galaxy: massive, wide CO emission, gas-rich but with very low SFR
- 2018MNRAS.474.4347C (2018): The ALMA early science view of FUor/EXor objects - V. Continuum disc masses and sizes
- 2018MNRAS.475..248C (2018): VALES - IV. Exploring the transition of star formation efficiencies between normal and starburst galaxies using APEX/SEPIA Band-5 and ALMA …
- 2018MNRAS.475..448T (2018): Mapping jet-ISM interactions in X-ray binaries with ALMA: a GRS 1915+105 case study
- 2018MNRAS.475.5322S (2018): Deuterated formaldehyde in the low-mass protostar HH212
- 2018MNRAS.476.4383D (2018): Modelling high-resolution ALMA observations of strongly lensed highly star-forming galaxies detected by Herschel
- 2018MNRAS.477..325B (2018): The extremely truncated circumstellar disc of V410 X-ray 1: a precursor to TRAPPIST-1?
- 2018MNRAS.477.5104C (2018): An inner warp in the DoAr 44 T Tauri transition disc
- 2018MNRAS.478.2505I (2018): Radiative transfer modelling of W33A MM1: 3D structure and dynamics of a complex massive star-forming region
- 2018MNRAS.478.3674R (2018): ALMA survey of circumstellar discs in the young stellar cluster IC 348
- 2018MNRAS.479..703C (2018): Merger-driven star formation activity in Cl J1449+0856 at z = 1.99 as seen by ALMA and JVLA
- 2018MNRAS.479.1154B (2018): The interstellar medium properties of heavily reddened quasarsand companions at z∼ 2.5 with ALMA and JVLA
- 2018MNRAS.480.4991G (2018): ALMA imaging of the nascent planetary nebula IRAS 15103-5754
- 2018MNRAS.481.4931E (2018): ALMA reveals the aftermath of a white dwarf-brown dwarf merger in CK Vulpeculae
- 2018NatAs...2...56Z (2018): A dusty star-forming galaxy at z = 6 revealed by strong gravitational lensing
- 2018NatAs...2..646H (2018): Evidence for the start of planet formation in a young circumstellar disk
- 2018Natur.553...51M (2018): Galaxy growth in a massive halo in the first billion years of cosmic history
- 2018Natur.557..392H (2018): The onset of star formation 250 million years after the Big Bang
- 2018Natur.560..613T (2018): The gravitationally unstable gas disk of a starburst galaxy 12 billion years ago
- 2018PASJ...70...36I (2018): Subaru High-z Exploration of Low-Luminosity Quasars (SHELLQs). III. Star formation properties of the host galaxies at z ≳ 6 studied with AL…
- 2018PASJ...70L...6K (2018): A high dust emissivity index β for a CO-faint galaxy in a filamentary Lyα nebula at z = 3.1
- 2018Sci...362.1034D (2018): The multiple merger assembly of a hyperluminous obscured quasar at redshift 4.6
- 2019A&A...621A.122B (2019): High-mass star formation at sub-50 au scales
- 2019A&A...622A..75L (2019): Ring structure in the MWC 480 disk revealed by ALMA
- 2019A&A...622A..99L (2019): Lack of high-mass pre-stellar cores in the starless MDCs of NGC 6334
- 2019A&A...622A.206M (2019): A 10-M<SUB>☉</SUB> YSO with a Keplerian disk and a nonthermal radio jet
- 2019A&A...623A..77S (2019): Discovery of a sub-Keplerian disk with jet around a 20 M<SUB>☉</SUB> young star. ALMA observations of G023.01-00.41
- 2019A&A...623A.150V (2019): The ALMA Lupus protoplanetary disk survey: evidence for compact gas disks and molecular rings from CN
- 2019A&A...623A.153O (2019): HD 101584: circumstellar characteristics and evolutionary status
- 2019A&A...623L...8B (2019): Unveiling a cluster of protostellar disks around the massive protostar GGD 27 MM1
- 2019A&A...624A...7V (2019): Spatial segregation of dust grains in transition disks. SPHERE observations of 2MASS J16083070-3828268 and RXJ1852.3-3700
- 2019A&A...624A..33V (2019): ALMA study of the HD 100453 AB system and the tidal interaction of the companion with the disk
- 2019A&A...625A.118K (2019): Highly structured disk around the planet host PDS 70 revealed by high-angular resolution observations with ALMA
- 2019A&A...626A..11C (2019): ALMA survey of Class II protoplanetary disks in Corona Australis: a young region with low disk masses
- 2019A&A...626A..36D (2019): ALMA reveals the magnetic field evolution in the high-mass star forming complex G9.62+0.19
- 2019A&A...626A..71A (2019): Physical and chemical fingerprint of protostellar disc formation
- 2019A&A...626A..93V (2019): The ALMA-PILS survey: gas dynamics in IRAS 16293-2422 and the connection between its two protostars
- 2019A&A...626A.126A (2019): A massive nebula around the luminous blue variable star RMC 143 revealed by ALMA
- 2019A&A...627L...6M (2019): Substructures in the Keplerian disc around the O-type (proto-)star G17.64+0.16
- 2019A&A...628A...2B (2019): Molecular complexity on disc scales uncovered by ALMA. Chemical composition of the high-mass protostar AFGL 4176
- 2019A&A...628A...6S (2019): The physical and chemical structure of Sagittarius B2. IV. Converging filaments in the high-mass cluster forming region Sgr B2(N)
- 2019A&A...628A..27B (2019): The complex chemistry of hot cores in Sgr B2(N): influence of cosmic-ray ionization and thermal history
- 2019A&A...628A..85V (2019): Disk masses in the Orion Molecular Cloud-2: distinguishing time and environment
- 2019A&A...629A..29J (2019): Organic chemistry in the innermost, infalling envelope of the Class 0 protostar L483
- 2019A&A...629A..75B (2019): First detections of H<SUP>13</SUP>CO<SUP>+</SUP> and HC<SUP>15</SUP>N in the disk around HD 97048. Evidence for a cold gas reservoir in the…
- 2019A&A...629A.136S (2019): A rotating fast bipolar wind and disk system around the B[e]-type star MWC 922
- 2019A&A...629A.146V (2019): IRC + 10°216 mass loss properties through the study of λ3 mm emission. Large spatial scale distribution of SiO, SiS, and CS
- 2019A&A...631A..64B (2019): Kinematics around the B335 protostar down to au scales
- 2019A&A...632A..57C (2019): Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). II. Complex organic molecules and heavy water in shoc…
- 2019A&A...632A..83S (2019): Probing fragmentation and velocity sub-structure in the massive NGC 6334 filament with ALMA
- 2019AJ....157..237R (2019): Constraints on a Putative Planet Sculpting the V4046 Sagittarii Circumbinary Disk
- 2019AJ....158...15P (2019): Dust Unveils the Formation of a Mini-Neptune Planet in a Protoplanetary Ring
- 2019ApJ...870...81T (2019): The Formation Conditions of the Wide Binary Class 0 Protostars within BHR 71
- 2019ApJ...871....5T (2019): The Flared Gas Structure of the Transitional Disk around Sz 91
- 2019ApJ...871...85L (2019): The ISM Properties and Gas Kinematics of a Redshift 3 Massive Dusty Star-forming Galaxy
- 2019ApJ...871..170M (2019): Fire in the Heart: A Characterization of the High Kinetic Temperatures and Heating Sources in the Nucleus of NGC 253
- 2019ApJ...871..185L (2019): Investigating Fragmentation of Gas Structures in OB Cluster-forming Molecular Clump G33.92+0.11 with 1000 au Resolution Observations of ALMA
- 2019ApJ...871..221M (2019): A Very Compact Extremely High Velocity Flow toward MMS 5/OMC-3 Revealed with ALMA
- 2019ApJ...871..251P (2019): ALMA Observations of Ethyl Formate toward Orion KL
- 2019ApJ...872...70T (2019): ALMA High Angular Resolution Polarization Study: An Extremely Young Class 0 Source, OMC-3/MMS 6
- 2019ApJ...872...92F (2019): The Planet Formation Potential around a 45 Myr Old Accreting M Dwarf
- 2019ApJ...872..112V (2019): Protoplanetary Disk Rings and Gaps across Ages and Luminosities
- 2019ApJ...872..117G (2019): Confirming Herschel Candidate Protoclusters from ALMA/VLA CO Observations
- 2019ApJ...872..176Z (2019): An Asymmetric Keplerian Disk Surrounding the O-type Protostar IRAS 16547-4247
- 2019ApJ...872..196S (2019): Implications of a Hot Atmosphere/Corino from ALMA Observations toward NGC 1333 IRAS 4A1
- 2019ApJ...872..200H (2019): ALMA Observations of the Massive Molecular Outflow G331.512-0.103. II. Physical Properties, Kinematics, and Geometry Modeling
- 2019ApJ...873...73Z (2019): An Ordered Envelope-Disk Transition in the Massive Protostellar Source G339.88-1.26
- 2019ApJ...873L..19B (2019): Extremely Low Molecular Gas Content in a Compact, Quiescent Galaxy at z = 1.522
- 2019ApJ...874...27T (2019): Detection of the Far-infrared [O III] and Dust Emission in a Galaxy at Redshift 8.312: Early Metal Enrichment in the Heart of the Reionizat…
- 2019ApJ...874...89C (2019): The Central 1000 au of a Pre-stellar Core Revealed with ALMA. I. 1.3 mm Continuum Observations
- 2019ApJ...874..120F (2019): New Insights into the Physical Conditions and Internal Structure of a Candidate Proto-globular Cluster
- 2019ApJ...875...62Y (2019): ALMA Observations of Layered Structures due to CO Selective Dissociation in the ρ Ophiuchi A Plane-parallel PDR
- 2019ApJ...875...87D (2019): The Mass of Stirring Bodies in the AU Mic Debris Disk Inferred from Resolved Vertical Structure
- 2019ApJ...875L...9W (2019): The Ophiuchus DIsk Survey Employing ALMA (ODISEA): Disk Dust Mass Distributions across Protostellar Evolutionary Classes
- 2019ApJ...877..100Y (2019): A Tight Relation between Spiral Arm Pitch Angle and Protoplanetary Disk Mass
- 2019ApJ...877L..25M (2019): The First Bird’s-eye View of a Gravitationally Unstable Accretion Disk in High-mass Star Formation
- 2019ApJ...878...16P (2019): An Inner Disk in the Large Gap of the Transition Disk SR 24S
- 2019ApJ...878...83W (2019): Evolution of the Gas Mass Fraction of Progenitors to Today’s Massive Galaxies: ALMA Observations in the CANDELS GOODS-S Field
- 2019ApJ...878L...8T (2019): Discovery of An au-scale Excess in Millimeter Emission from the Protoplanetary Disk around TW Hya
- 2019ApJ...879...25K (2019): Highly Ordered and Pinched Magnetic Fields in the Class 0 Protobinary System L1448 IRS 2
- 2019ApJ...879L...2M (2019): PDS 70: A Transition Disk Sculpted by a Single Planet
- 2019ApJ...879L..25I (2019): Detection of Continuum Submillimeter Emission Associated with Candidate Protoplanets
- 2019ApJ...880....2W (2019): Spatially Resolved Interstellar Medium and Highly Excited Dense Molecular Gas in the Most Luminous Quasar at z = 6.327
- 2019ApJ...880...15K (2019): The Molecular Gas Reservoirs of z ∼ 2 Galaxies: A Comparison of CO(1-0) and Dust-based Molecular Gas Masses
- 2019ApJ...880..157D (2019): ALMA and HST Kiloparsec-scale Imaging of a Quasar-galaxy Merger at Z ≈ 6.2
- 2019ApJ...881...63N (2019): An ALMA Multiline Survey of the Interstellar Medium of the Redshift 7.5 Quasar Host Galaxy J1342+0928
- 2019ApJ...881..112O (2019): Sulfur-bearing Species Tracing the Disk/Envelope System in the Class I Protostellar Source Elias 29
- 2019ApJ...881L..42C (2019): Interstellar Plunging Waves: ALMA Resolves the Physical Structure of Nonstationary MHD Shocks
- 2019ApJ...882....1L (2019): CO and Fine-structure Lines Reveal Low Metallicity in a Stellar-mass-rich Galaxy at z ∼ 1?
- 2019ApJ...882..160Q (2019): Probing CO and N<SUB>2</SUB> Snow Surfaces in Protoplanetary Disks with N<SUB>2</SUB>H<SUP>+</SUP> Emission
- 2019ApJ...882L...4C (2019): Resolved ALMA Continuum Image of the Circumbinary Ring and Circumstellar Disks in the L1551 IRS 5 System
- 2019ApJ...883...98Z (2019): Systematic Variations of CO Gas Abundance with Radius in Gas-rich Protoplanetary Disks
- 2019ApJ...883..180H (2019): First Subarcsecond Submillimeter-wave [C I] Image of 49 Ceti with ALMA
- 2019ApJ...884...48C (2019): The Seven Most Massive Clumps in W43-Main as Seen by ALMA: Dynamical Equilibrium and Magnetic Fields
- 2019ApJ...884L..41B (2019): An Ideal Testbed for Planet-Disk Interaction: Two Giant Protoplanets in Resonance Shaping the PDS 70 Protoplanetary Disk
- 2019ApJ...885..106L (2019): Characterizing Magnetic Field Morphologies in Three Serpens Protostellar Cores with ALMA
- 2019ApJ...886...51C (2019): High Angular Resolution ALMA Images of Dust and Molecules in the SN 1987A Ejecta
- 2019ApJ...886..102S (2019): The ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES). I. Pilot Survey: Clump Fragmentation
- 2019ApJ...886L...4Z (2019): Discovery of a Photoionized Bipolar Outflow toward the Massive Protostar G45.47+0.05
- 2019ApJ...887...55C (2019): Physical Characterization of an Unlensed, Dusty Star-forming Galaxy at z = 5.85
- 2019ApJ...887...74F (2019): ALMA Reveals a Gas-rich, Maximum Starburst in the Hyperluminous, Dust-obscured Quasar W0533-3401 at z ∼ 2.9
- 2019ApJ...887...79H (2019): The Interaction between the Supernova Remnant W41 and the Filamentary Infrared Dark Cloud G23.33-0.30
- 2019ApJ...887..144J (2019): Discovery of Four Apparently Cold Dusty Galaxies at z = 3.62-5.85 in the COSMOS Field: Direct Evidence of Cosmic Microwave Background Impac…
- 2019ApJS..245....2S (2019): Dust Polarization toward Embedded Protostars in Ophiuchus with ALMA. III. Survey Overview
- 2019MNRAS.482..698C (2019): The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - I: project description and continuum images at 28 au resolution
- 2019MNRAS.482.3135B (2019): The relationship between dust and [C I] at z = 1 and beyond
- 2019MNRAS.482.4617S (2019): ALMA observations of massive molecular gas reservoirs in dusty early-type galaxies
- 2019MNRAS.483..806R (2019): First ALMA maps of HCO, an important precursor of complex organic molecules, towards IRAS 16293-2422
- 2019MNRAS.485..739M (2019): Asymmetric mid-plane gas in ALMA images of HD 100546
- 2019MNRAS.485.2092C (2019): Suppressed CO emission and high G/D ratios in z = 2 galaxies with sub-solar gas-phase metallicity
- 2019MNRAS.486..283B (2019): Young massive star cluster formation in the Galactic Centre is driven by global gravitational collapse of high-mass molecular clouds
- 2019MNRAS.486.4114R (2019): ALMA reveals a pseudo-disc in a proto-brown dwarf
- 2019MNRAS.486.5552B (2019): Sub-millimetre non-contaminated detection of the disc around TWA 7 by ALMA
- 2019MNRAS.488.1005P (2019): Upper limits on protolunar disc masses using ALMA observations of directly imaged exoplanets
- 2019NatAs...3..230K (2019): A circumbinary protoplanetary disk in a polar configuration
- 2019NatAs...3..278K (2019): Publisher Correction: A circumbinary protoplanetary disk in a polar configuration
- 2019NatAs...3..314L (2019): The ice composition in the disk around V883 Ori revealed by its stellar outburst
- 2019NatAs...3..517Z (2019): Dynamics of a massive binary at birth
- 2019PASJ...71...71H (2019): Big Three Dragons: A z = 7.15 Lyman-break galaxy detected in [O III] 88 μm, [C II] 158 μm, and dust continuum with ALMA
- 2019PASJ...71...73T (2019): A centrally concentrated sub-solar-mass starless core in the Taurus L1495 filamentary complex
- 2019PASJ...71..111I (2019): Subaru High-z Exploration of Low-Luminosity Quasars (SHELLQs). VIII. A less biased view of the early co-evolution of black holes and host g…
- 2019Sci...366...90A (2019): Gas flow and accretion via spiral streamers and circumstellar disks in a young binary protostar
- 2020A&A...633A.114S (2020): Demographics of disks around young very low-mass stars and brown dwarfs in Lupus
- 2020A&A...633A.126B (2020): The dynamically young outflow of the Class 0 protostar Cha-MMS1
- 2020A&A...634L..11J (2020): Spiral arms and instability within the AFGL 4176 mm1 disc
- 2020A&A...635A...2S (2020): Physical properties of the star-forming clusters in NGC 6334. A study of the continuum dust emission with ALMA
- 2020A&A...635A..94D (2020): An ALMA/NOEMA study of gas dissipation and dust evolution in the 5 Myr-old HD 141569A hybrid disc
- 2020A&A...636A..26H (2020): Missing water in Class I protostellar disks
- 2020A&A...636A..37D (2020): Dust and gas content of high-redshift galaxies hosting obscured AGN in the Chandra Deep Field-South
- 2020A&A...636A..67A (2020): Exploring the formation pathways of formamide. Near young O-type stars
- 2020A&A...638A..38T (2020): Constraining the radial drift of millimeter-sized grains in the protoplanetary disks in Lupus
- 2020A&A...639A.121F (2020): Annular substructures in the transition disks around LkCa 15 and J1610
- 2020A&A...640A..19T (2020): Dust masses of young disks: constraining the initial solid reservoir for planet formation
- 2020A&A...640A..27V (2020): Protoplanetary disk masses in NGC 2024: Evidence for two populations
- 2020A&A...640L...8U (2020): ALMA Deep Field in SSA22. A near-infrared-dark submillimeter galaxy at z = 4.0
- 2020A&A...641A.155V (2020): CO emission in distant galaxies on and above the main sequence
- 2020A&A...642A.164V (2020): Observations of edge-on protoplanetary disks with ALMA. I. Results from continuum data
- 2020A&A...643A..30F (2020): GOODS-ALMA: The slow downfall of star formation in z = 2-3 massive galaxies
- 2020A&A...644A..11L (2020): A statistical analysis of dust polarization properties in ALMA observations of Class 0 protostellar cores
- 2020A&A...644A..59K (2020): Molecular remnant of Nova 1670 (CK Vulpeculae). I. Properties and enigmatic origin of the gas
- 2020A&A...644A..84M (2020): The GUAPOS project: G31.41+0.31 Unbiased ALMA sPectral Observational Survey. I. Isomers of C<SUB>2</SUB>H<SUB>4</SUB>O<SUB>2</SUB>
- 2020A&A...644A.119P (2020): ALMA chemical survey of disk-outflow sources in Taurus (ALMA-DOT). III. The interplay between gas and dust in the protoplanetary disk of DG…
- 2020AJ....159...62C (2020): ALMA Observations of the Extraordinary Carina Pillars: HH 901/902
- 2020AJ....159..118U (2020): Near-infrared Imaging of a Spiral in the CQ Tau Disk
- 2020AJ....159..229W (2020): ALMA 0.88 mm Survey of Disks around Planetary-mass Companions
- 2020AJ....159..288M (2020): The Big Sibling of AU Mic: A Cold Dust-rich Debris Disk around CP-72 2713 in the β Pic Moving Group
- 2020AJ....160..248A (2020): An ALMA Survey of λ Orionis Disks: From Supernovae to Planet Formation
- 2020ApJ...888L...4T (2020): Long-lived Dust Rings around HD 169142
- 2020ApJ...889...20L (2020): The Circumstellar Environment around the Embedded Protostar EC 53
- 2020ApJ...889...43Z (2020): Dense Cores, Filaments, and Outflows in the S255IR Region of High-mass Star Formation
- 2020ApJ...889...85H (2020): Evolution from Spherical AGB Wind to Multipolar Outflow in Pre-planetary Nebula IRAS 17150-3224
- 2020ApJ...889..140Y (2020): High-resolution Near-infrared Polarimetry and Submillimeter Imaging of FS Tau A: Possible Streamers in Misaligned Circumbinary Disk System
- 2020ApJ...890...24V (2020): The Properties of the Interstellar Medium of Galaxies across Time as Traced by the Neutral Atomic Carbon [C I]
- 2020ApJ...890...76N (2020): ALMA Observations of Two Massive and Dense MALT90 Clumps
- 2020ApJ...890..129K (2020): Detection of Irregular, Submillimeter Opaque Structures in the Orion Molecular Clouds: Protostars within 10,000 yr of Formation?
- 2020ApJ...890..130T (2020): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. II. A Statistical Characterization of Class 0 and Class I P…
- 2020ApJ...890L..14T (2020): Shaping the Envelope of the Asymptotic Giant Branch Star W43A with a Collimated Fast Jet
- 2020ApJ...891...48H (2020): A Multifrequency ALMA Characterization of Substructures in the GM Aur Protoplanetary Disk
- 2020ApJ...891...61Y (2020): Constraining the Infalling Envelope Models of Embedded Protostars: BHR 71 and Its Hot Corino
- 2020ApJ...891..113R (2020): Effect of Feedback of Massive Stars in the Fragmentation, Distribution, and Kinematics of the Gas in Two Star-forming Regions in the Carina…
- 2020ApJ...891..164S (2020): Chemistry and Physics of a Low-metallicity Hot Core in the Large Magellanic Cloud
- 2020ApJ...892...42H (2020): ALMA CO Observations of the Host Galaxies of Long-duration Gamma-Ray Bursts. I. Molecular Gas Scaling Relations
- 2020ApJ...892...66M (2020): The ALMA Spectroscopic Survey in the HUDF: The Cosmic Dust and Gas Mass Densities in Galaxies up to z ∼ 3
- 2020ApJ...892..111F (2020): Dust-depleted Inner Disks in a Large Sample of Transition Disks through Long-baseline ALMA Observations
- 2020ApJ...892..147S (2020): Oversized Gas Clumps in an Extremely Metal-poor Molecular Cloud Revealed by ALMA's Parsec-scale Maps
- 2020ApJ...892..152H (2020): Understanding the Origin of the Magnetic Field Morphology in the Wide-binary Protostellar System BHR 71
- 2020ApJ...893..125U (2020): Scattering-induced Intensity Reduction: Large Mass Content with Small Grains in the Inner Region of the TW Hya disk
- 2020ApJ...894L..14L (2020): ALMA Observations of Massive Clouds in the Central Molecular Zone: Jeans Fragmentation and Cluster Formation
- 2020ApJ...895...74N (2020): ALMA Observations of Quasar Host Galaxies at z ≃ 4.8
- 2020ApJ...895..119T (2020): ALMA ACA and Nobeyama Observations of Two Orion Cores in Deuterated Molecular Lines
- 2020ApJ...895..142L (2020): Magnetic Fields in the Early Stages of Massive Star Formation as Revealed by ALMA
- 2020ApJ...895L..18B (2020): GW Ori: Interactions between a Triple-star System and Its Circumtriple Disk in Action
- 2020ApJ...895L..46L (2020): Hints of a Population of Solar System Analog Planets from ALMA
- 2020ApJ...896...35J (2020): A Detailed View of the Circumstellar Environment and Disk of the Forming O-star AFGL 4176
- 2020ApJ...896...43W (2020): Arp 220: New Observational Insights into the Structure and Kinematics of the Nuclear Molecular Disks and Surrounding Gas
- 2020ApJ...896...93H (2020): Large Population of ALMA Galaxies at z &gt; 6 with Very High [O III] 88 μm to [C II] 158 μm Flux Ratios: Evidence of Extremely High Ionizat…
- 2020ApJ...896..110L (2020): ALMA Observations of NGC 6334S. I. Forming Massive Stars and Clusters in Subsonic and Transonic Filamentary Clouds
- 2020ApJ...896..127K (2020): Multiple Outflows in the High-mass Cluster-forming Region G25.82-0.17
- 2020ApJ...897...59M (2020): Orbital and Mass Constraints of the Young Binary System IRAS 16293-2422 A
- 2020ApJ...897L..33J (2020): The Ionized Warped Disk and Disk Wind of the Massive Protostar Monoceros R2-IRS2 Seen with ALMA
- 2020ApJ...898...10T (2020): Circumbinary Disks of the Protostellar Binary Systems in the L1551 Region
- 2020ApJ...898...36L (2020): Dual-wavelength ALMA Observations of Dust Rings in Protoplanetary Disks
- 2020ApJ...898...97B (2020): An Evolutionary Study of Volatile Chemistry in Protoplanetary Disks
- 2020ApJ...898..133L (2020): Emergence of an Ultrared, Ultramassive Galaxy Cluster Core at z = 4
- 2020ApJ...898..140H (2020): Large-scale CO Spiral Arms and Complex Kinematics Associated with the T Tauri Star RU Lup
- 2020ApJ...899...37K (2020): A Comparison of the Stellar, CO, and Dust-continuum Emission from Three Star-forming HUDF Galaxies at z ∼ 2
- 2020ApJ...900....7H (2020): ALMA Observations of Young Eruptive Stars: Continuum Disk Sizes and Molecular Outflows
- 2020ApJ...900...81O (2020): Solving Grain Size Inconsistency between ALMA Polarization and VLA Continuum in the Ophiuchus IRS 48 Protoplanetary Disk
- 2020ApJ...900L...2T (2020): Salt, Hot Water, and Silicon Compounds Tracing Massive Twin Disks
- 2020ApJ...901...79A (2020): The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: The Nature of the Faintest Dusty Star-forming Galaxies
- 2020ApJ...901..166V (2020): Temperature Structures of Embedded Disks: Young Disks in Taurus Are Warm
- 2020ApJ...902...78R (2020): The Complete Redshift Distribution of Dusty Star-forming Galaxies from the SPT-SZ Survey
- 2020ApJ...902..141S (2020): The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars. III. Substructures in Protostellar Disks
- 2020ApJ...902L..33G (2020): A Tale of Two Transition Disks: ALMA Long-baseline Observations of ISO-Oph 2 Reveal Two Closely Packed Nonaxisymmetric Rings and a ∼2 au Ca…
- 2020ApJ...903...34A (2020): Probing the Nature of High-redshift Weak Emission Line Quasars: A Young Quasar with a Starburst Host Galaxy
- 2020ApJ...903...50E (2020): Super Star Clusters in the Central Starburst of NGC 4945
- 2020ApJ...903...94M (2020): ALMA Observations of Giant Molecular Clouds in M33. II. Triggered High-mass Star Formation by Multiple Gas Colliding Events at the NGC 604 …
- 2020ApJ...904...37W (2020): ALMA and VLA Observations of EX Lupi in Its Quiescent State
- 2020ApJ...904...77G (2020): A Photoionized Accretion Disk around a Young High-mass Star
- 2020ApJ...904...78S (2020): Constraining the Chemical Signatures and the Outburst Mechanism of the Class 0 Protostar HOPS 383
- 2020ApJ...904..125S (2020): Spiral-arm Substructures in the Asymmetrical Dust Rings of the Circumstellar Disk MWC 758
- 2020ApJ...904..168B (2020): Gravity and Rotation Drag the Magnetic Field in High-mass Star Formation
- 2020ApJ...904..181L (2020): ALMA View of the Infalling Envelope around a Massive Protostar in S255IR SMA1
- 2020ApJ...904..185O (2020): Substructures in the Disk-forming Region of the Class 0 Low-mass Protostellar Source IRAS 16293-2422 Source A on a 10 au Scale
- 2020ApJ...904L...6A (2020): A Case of Simultaneous Star and Planet Formation
- 2020ApJ...905...25G (2020): Multidirectional Mass Accretion and Collimated Outflows on Scales of 100-2000 au in Early Stages of High-mass Protostars
- 2020ApJ...905...89Y (2020): Kinematical Signs of Dust Trapping and Feedback in a Local Pressure Bump in the Protoplanetary Disk around HD 142527 Revealed with ALMA
- 2020ApJS..251...14H (2020): CMZoom. II. Catalog of Compact Submillimeter Dust Continuum Sources in the Milky Way's Central Molecular Zone
- 2020MNRAS.491..758A (2020): CO in the C1 globule of the Helix nebula with ALMA
- 2020MNRAS.491.1174M (2020): Circumstellar CO J = 3→2 detected around the evolving metal-poor ([Fe/H] ≈ -1.15 dex) AGB star RU Vulpeculae
- 2020MNRAS.491.1335R (2020): Spiral arms in the protoplanetary disc HD100453 detected with ALMA: evidence for binary-disc interaction and a vertical temperature gradient
- 2020MNRAS.492.4847L (2020): VVV-WIT-01: highly obscured classical nova or protostellar collision?
- 2020MNRAS.493.4294B (2020): ALMA uncovers the [C II] emission and warm dust continuum in a z = 8.31 Lyman break galaxy
- 2020MNRAS.494.3828D (2020): An ALMA survey of the SCUBA-2 CLS UDS field: physical properties of 707 sub-millimetre galaxies
- 2020MNRAS.494.5542R (2020): Full of Orions: a 200-pc mapping of the interstellar medium in the redshift-3 lensed dusty star-forming galaxy SDP.81
- 2020MNRAS.496..394R (2020): Illuminating a tadpole's metamorphosis II: observing the ongoing transformation with ALMA
- 2020MNRAS.496.1834L (2020): Atacama Compact Array observations of the pulsar-wind nebula of SNR 0540-69.3
- 2020MNRAS.496.2362P (2020): Binary-induced spiral arms inside the disc cavity of AB Aurigae
- 2020MNRAS.496.5089Z (2020): The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - II. The effect of stellar multiplicity on disc properties
- 2020MNRAS.497.5454I (2020): Multiwavelength investigation of extended green object G19.88-0.53: revealing a protocluster
- 2020MNRAS.498.1319M (2020): Insights into the planetary dynamics of HD 206893 with ALMA
- 2020MNRAS.498.4109J (2020): Gas and star formation from HD and dust emission in a strongly lensed galaxy
- 2020MNRAS.498.4192F (2020): ALMA characterizes the dust temperature of z ∼ 5.5 star-forming galaxies
- 2020MNRAS.498.4256C (2020): The observational impact of dust trapping in self-gravitating discs
- 2020MNRAS.499.2015T (2020): Planet migration, resonant locking, and accretion streams in PDS 70: comparing models and data
- 2020MNRAS.499.5241C (2020): A kpc-scale-resolved study of unobscured and obscured star formation activity in normal galaxies at z = 1.5 and 2.2 from ALMA and HiZELS
- 2020NatAs...4..142L (2020): Spiral structures in an embedded protostellar disk driven by envelope accretion
- 2020NatAs...4..670A (2020): Infalling gas in a Lyman-α blob
- 2020PASP..132h4401T (2020): Herschel Observations of Disks around Late-type Stars
- 2020PASP..132i4501H (2020): Characterizing the Accuracy of ALMA Linear-polarization Mosaics
- 2021A&A...645A..33B (2021): The WISSH quasars project. IX. Cold gas content and environment of luminous QSOs at z ∼ 2.4-4.7
- 2021A&A...645A..49G (2021): A proto-pseudobulge in ESO 320-G030 fed by a massive molecular inflow driven by a nuclear bar
- 2021A&A...646A...3L (2021): Chemically tracing the water snowline in protoplanetary disks with HCO<SUP>+</SUP>
- 2021A&A...646A..25Z (2021): H II regions and high-mass starless clump candidates. II. Fragmentation and induced star formation at 0.025 pc scale: an ALMA continuum stu…
- 2021A&A...647A.118L (2021): Exploring HNC and HCN line emission as probes of the protoplanetary disk temperature
- 2021A&A...648A..33M (2021): Characterizing the dust content of disk substructures in TW Hydrae
- 2021A&A...648A..41V (2021): Outflows, envelopes, and disks as evolutionary indicators in Lupus young stellar objects
- 2021A&A...649A..19S (2021): Measuring the ratio of the gas and dust emission radii of protoplanetary disks in the Lupus star-forming region
- 2021A&A...649A.122P (2021): A bright inner disk and structures in the transition disk around the very low-mass star CIDA 1
- 2021A&A...650A..37D (2021): A search for signatures of interactions of X-ray binary outflows with their environments with ALMA
- 2021A&A...650A.142M (2021): The ionized heart of a molecular disk. ALMA observations of the hyper-compact HII region G24.78+0.08 A1
- 2021A&A...650A.153D (2021): Multiwavelength view of SPT-CL J2106-5844. The radio galaxies and the thermal and relativistic plasmas in a massive galaxy cluster merger a…
- 2021A&A...650A.202R (2021): Identification of pre-stellar cores in high-mass star forming clumps via H<SUB>2</SUB>D<SUP>+</SUP> observations with ALMA
- 2021A&A...652A..66P (2021): ALMA multiline survey of the ISM in two quasar host-companion galaxy pairs at z &gt; 6
- 2021A&A...652A..98G (2021): The Galaxy Activity, Torus, and Outflow Survey (GATOS). I. ALMA images of dusty molecular tori in Seyfert galaxies
- 2021A&A...652A.128J (2021): ALMA Lensing Cluster Survey: A spectral stacking analysis of [C II] in lensed z ∼ 6 galaxies
- 2021A&A...653A..46V (2021): Probing protoplanetary disk evolution in the Chamaeleon II region
- 2021A&A...653A.129C (2021): The GUAPOS project. II. A comprehensive study of peptide-like bond molecules
- 2021A&A...653L...9V (2021): If you like C/O variations, you should have put a ring on it
- 2021A&A...654A..90L (2021): SUPER. V. ALMA continuum observations of z ∼ 2 AGN and the elusive evidence of outflows influencing star formation
- 2021A&A...655A..42S (2021): Molecular gas budget and characterization of intermediate-mass star-forming galaxies at z ≈ 2-3
- 2021A&A...655A..72S (2021): Physical conditions in the warped accretion disk of a massive star. 349 GHz ALMA observations of G023.01‒00.41
- 2021A&A...655A..98A (2021): The contribution by luminous blue variable stars to the dust content of the Magellanic Clouds
- 2021A&A...656A.150P (2021): Constraining the properties of the potential embedded planets in the disk around HD 100546
- 2021AJ....161..238W (2021): The Anatomy of an Unusual Edge-on Protoplanetary Disk. I. Dust Settling in a Cold Disk
- 2021AJ....162..235Y (2021): A Radiatively Driven Wind from the η Tel Debris Disk
- 2021ApJ...907...62R (2021): Rise of the Titans: Gas Excitation and Feedback in a Binary Hyperluminous Dusty Starburst Galaxy at z ∼ 6
- 2021ApJ...907...94C (2021): The Explosion in Orion-KL as Seen by Mosaicking the Magnetic Field with ALMA
- 2021ApJ...907..108G (2021): Identification of Methyl Isocyanate and Other Complex Organic Molecules in a Hot Molecular Core, G31.41+0.31
- 2021ApJ...907L..15S (2021): ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP): Detection of Extremely High-density Compact Structure of Prestellar Cores and M…
- 2021ApJ...908....8C (2021): The TW Hya Rosetta Stone Project. III. Resolving the Gaseous Thermal Profile of the Disk
- 2021ApJ...908...15S (2021): Dust, Gas, and Metal Content in Star-forming Galaxies at z ∼ 3.3 Revealed with ALMA and Near-IR Spectroscopy
- 2021ApJ...908..163M (2021): Extremely Low Molecular Gas Content in the Vicinity of a Red Nugget Galaxy at z = 1.91
- 2021ApJ...908..192S (2021): ALMA 1.3 mm Survey of Lensed Submillimeter Galaxies Selected by Herschel: Discovery of Spatially Extended SMGs and Implications
- 2021ApJ...908..235I (2021): Subaru High-z Exploration of Low-luminosity Quasars (SHELLQs). XII. Extended [C II] Structure (Merger or Outflow) in a z = 6.72 Red Quasar
- 2021ApJ...908..250H (2021): ALMA Observations of the Inner Cavity in the Protoplanetary Disk around Sz 84
- 2021ApJ...909..212K (2021): ALMA Observation of the Protoplanetary Disk around WW Cha: Faint Double-peaked Ring and Asymmetric Structure
- 2021ApJ...910...75L (2021): What Produces Dust Polarization in the HH 212 Protostellar Disk at 878 μm: Dust Self-scattering or Dichroic Extinction?
- 2021ApJ...910..148M (2021): Revealing a Centrally Condensed Structure in OMC-3/MMS 3 with ALMA High-resolution Observations
- 2021ApJ...912L...7L (2021): A Low-mass Cold and Quiescent Core Population in a Massive Star Protocluster
- 2021ApJ...914...36I (2021): Subaru High-z Exploration of Low-luminosity Quasars (SHELLQs). XIII. Large-scale Feedback and Star Formation in a Low-luminosity Quasar at …
- 2021ApJ...916...97Y (2021): No Impact of Core-scale Magnetic Field, Turbulence, or Velocity Gradient on Sizes of Protostellar Disks in Orion A
- 2021ApJ...917...99Y (2021): ALMA Observations of the Sub-kpc Structure of the Host Galaxy of a z = 6.5 Lensed Quasar: A Rotationally Supported Hyper-Starburst System a…
- 2021ApJ...918...69U (2021): ALMA Observations of Lyα Blob 1: Multiple Major Mergers and Widely Distributed Interstellar Media
- 2021ApJ...918...76C (2021): Toward a More Complex Understanding of Natal Super Star Clusters with Multiwavelength Observations
- 2021ApJ...921...97J (2021): Molecular Line Observations in Two Dusty Star-forming Galaxies at z = 6.9
- 2021ApJ...922..206S (2021): The Detection of a Hot Molecular Core in the Extreme Outer Galaxy
- 2021ApJ...923..121Y (2021): ALMA Super-resolution Imaging of T Tau: r = 12 au Gap in the Compact Dust Disk around T Tau N
- 2021MNRAS.500.3667S (2021): The rocky road to quiescence: compaction and quenching of quasar host galaxies at z ∼ 2
- 2021MNRAS.501.2305Z (2021): The effect of stellar multiplicity on protoplanetary discs: a near-infrared survey of the Lupus star-forming region
- 2021MNRAS.501.2934C (2021): The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - III. The evolution of substructures in massive discs at 3-5 au resolution
- 2021MNRAS.501.4317P (2021): Planet formation in intermediate-separation binary systems
- 2021MNRAS.502.5390P (2021): A ∼75 per cent occurrence rate of debris discs around F stars in the β Pic moving group
- 2021MNRAS.503...77W (2021): Star formation in 'the Brick': ALMA reveals an active protocluster in the Galactic centre cloud G0.253+0.016
- 2021MNRAS.504..928P (2021): Unveiling the nature of 11 dusty star-forming galaxies at the peak of cosmic star formation history
- 2021MNRAS.504.4123N (2021): Black hole mass measurement using ALMA observations of [CI] and CO emissions in the Seyfert 1 galaxy NGC 7469
- 2021MNRAS.505.1509S (2021): The nature of sub-millimetre galaxies I: a comparison of AGN and star-forming galaxy SED fits
- 2021MNRAS.505.4838L (2021): ALMA Lensing Cluster Survey: a strongly lensed multiply imaged dusty system at z ≥ 6
- 2021MNRAS.506.4175M (2021): Massive protocluster of a periodic maser source G188.95+0.89
- 2021MNRAS.507.1886F (2021): Probing the kinematics and chemistry of the hot core Mon R2 IRS 3 using ALMA observations
- 2021MNRAS.508.4639Z (2021): ATOMS: ALMA Three-millimeter Observations of Massive Star-forming regions-VI. On the formation of the 'L' type filament in G286.21+0.17
- 2021MNRAS.508.5259M (2021): An ACA 1 mm survey of HzRGs in the ELAIS-S1: survey description and first results
- 2021NatAs...5..586Y (2021): Compact pebbles and the evolution of volatiles in the interstellar comet 2I/Borisov
- 2021PASJ...73..205T (2021): ALMA view of the Galactic super star cluster RCW 38 at 270 au resolution
- 2022A&A...657A..25N (2022): Radial profiles of lensed z ∼ 1 galaxies on sub-kiloparsec scales
- 2022A&A...659A..46B (2022): A Virgo Environmental Survey Tracing Ionised Gas Emission (VESTIGE). XII. Ionised gas emission in the inner regions of lenticular galaxies
- 2022A&A...661A..53V (2022): Survey of Orion Disks with ALMA (SODA). I. Cloud-level demographics of 873 protoplanetary disks
- 2022A&A...662A...8M (2022): ALMA-IMF. I. Investigating the origin of stellar masses: Introduction to the Large Program and first results
- 2022A&A...662A.121R (2022): Observational constraints on gas disc sizes in the protoplanetary discs of multiple systems in the Taurus region
- 2022A&A...664A..63X (2022): Starbursts with suppressed velocity dispersion revealed in a forming cluster at z = 2.51
- 2022A&A...665A..82O (2022): CO line observations of OH/IR stars in the inner Galactic Bulge: Characteristics of stars at the tip of the AGB
- 2022A&A...665L...7S (2022): A galaxy group candidate at z ≈ 3.7 in the COSMOS field
- 2022A&A...668A..25V (2022): Disk Evolution Study Through Imaging of Nearby Young Stars (DESTINYS): Scattered light detection of a possible disk wind in RY Tau
- 2022A&A...668L...4G (2022): The uncertain interstellar medium of high-redshift quiescent galaxies: Impact of methodology
- 2022ApJ...928..150T (2022): Probing Multiphase Gas in Local Massive Elliptical Galaxies via Multiwavelength Observations
- 2022ApJ...930L...3W (2022): ALMA Discovery of a Disk around the Planetary-mass Companion SR 12 c
- 2022MNRAS.509..748W (2022): ALMA observations of the Extended Green Object G19.01-0.03 - I. A Keplerian disc in a massive protostellar system
- 2022MNRAS.509.2920N (2022): The MBHBM<SUP>⋆</SUP> Project - II. Molecular gas kinematics in the lenticular galaxy NGC 3593 reveal a supermassive black hole
- 2022MNRAS.510.3734D (2022): A high-resolution investigation of the multiphase ISM in a galaxy during the first two billion years
- 2022MNRAS.510.4485R (2022): The AGN fuelling/feedback cycle in nearby radio galaxies - IV. Molecular gas conditions and jet-ISM interaction in NGC 3100
- 2022MNRAS.510.4976A (2022): The nature of sub-millimetre galaxies II: an ALMA comparison of SMG dust heating mechanisms
- 2022MNRAS.512.2426M (2022): Modelling high-resolution ALMA observations of strongly lensed dusty star-forming galaxies detected by Herschel
- 2022MNRAS.512.4419P (2022): ATOMS: ALMA Three-millimeter Observations of Massive Star-forming regions - X. Chemical differentiation among the massive cores in G9.62+0.…
- 2022MNRAS.514..578W (2022): The initial conditions for young massive cluster formation in the Galactic Centre: convergence of large-scale gas flows
- 2022MNRAS.514.2346K (2022): CO excitation and line energy distributions in gas-selected galaxies
- 2022MNRAS.515.1751W (2022): Dual constraints with ALMA: new [O III] 88-μm and dust-continuum observations reveal the ISM conditions of luminous LBGs at z 7
- 2022MNRAS.515.5730K (2022): Investigating star-formation activity towards the southern H II region RCW 42
- 2023A&A...669A..56Q (2023): History of two mass loss processes in VY CMa. Fast outflows carving older ejecta
- 2023A&A...669A..90C (2023): Magnetically regulated collapse in the B335 protostar?. II. Observational constraints on gas ionization and magnetic field coupling
- 2023A&A...673A.157D (2023): A comprehensive view of the interstellar medium in a quasar host galaxy at z ≈ 6.4
- 2023A&A...674A..66Z (2023): New constraints on the presence of debris disks around G 196-3 B and VHS J125601.92-125723.9 b
- 2023A&A...674A..75N (2023): ALMA-IMF. V. Prestellar and protostellar core populations in the W43 cloud complex
- 2023A&A...675A.131T (2023): Investigating the asymmetric chemistry in the disk around the young star HD 142527
- 2023A&A...677A..76P (2023): Constraining the gas distribution in the PDS 70 disc as a method to assess the effect of planet-disc interactions
- 2023A&A...680A.110C (2023): Radio outburst from a massive (proto)star. II. A portrait in space and time of the expanding radio jet from S255IR NIRS 3
- 2023Ap&SS.368...33M (2023): Identification of interstellar cyanamide towards the hot molecular core G358.93─0.03 MM1
- 2023ApJ...945...69R (2023): Updated Measurements of [O III] 88 μm, [C II] 158 μm, and Dust Continuum Emission from a z = 7.2 Galaxy
- 2023ApJ...946L..41S (2023): The Detection of Hot Molecular Cores in the Small Magellanic Cloud
- 2023ApJ...948L...2Y (2023): Eccentric Dust Ring in the IRS 48 Transition Disk
- 2023ApJ...952...48H (2023): Big Three Dragons: Molecular Gas in a Bright Lyman-break Galaxy at z = 7.15
- 2023ApJ...953..113L (2023): The Magnetic Fields of Starburst Galaxies. I. Identification and Characterization of the Thermal Polarization in the Galactic Disk and Outf…
- 2023ApJ...956L..35Z (2023): One, Two, Three ... An Explosive Outflow in IRAS 12326-6245 Revealed by ALMA
- 2023ApJ...956L..45G (2023): An SiO Toroid and Wide-angle Outflow Associated with the Massive Protostar W75N(B)-VLA2
- 2023ApJ...958...98F (2023): Early Planet Formation in Embedded Disks (eDisk). XII. Accretion Streamers, Protoplanetary Disk, and Outflow in the Class I Source Oph IRS …
- 2023MNRAS.518.4481L (2023): Dynamical mass measurements of two protoplanetary discs
- 2023MNRAS.518.6092L (2023): The radial profile of dust grain size in the protoplanetary disc of DS Tau
- 2023MNRAS.521.2962F (2023): Estimating dust temperature and Far-IR luminosity of high-redshift galaxies using ALMA single-band continuum observations
- 2023MNRAS.521.5508H (2023): Bright extragalactic ALMA redshift survey (BEARS) III: detailed study of emission lines from 71 Herschel targets
- 2023MNRAS.522...56V (2023): A systematic survey of millimetre-wavelength flaring variability of young stellar objects in the Orion Nebula Cluster
- 2023MNRAS.522.2384M (2023): FAUST - VIII. The protostellar disc of VLA 1623-2417W and its streamers imaged by ALMA
- 2023MNRAS.522.3719L (2023): Evidence of high-mass star formation through multiscale mass accretion in hub-filament-system clouds
- 2023MNRAS.523.4654T (2023): Spatially resolved dust properties and quasar-galaxy decomposition of a hyper-luminous infrared galaxy at z = 4.4
- 2023MNRAS.523.4970N (2023): Resolving the binary components of the outbursting protostar HBC 494 with ALMA
- 2023MNRAS.523.5388M (2023): AFGL 5180 and AFGL 6366S: sites of hub-filament systems at the opposite edges of a filamentary cloud
- 2023MNRAS.524..923Z (2023): The large molecular gas fraction of post-starburst galaxies at z &gt; 1
- 2023MNRAS.525.2229M (2023): Identification of the simplest sugar-like molecule glycolaldehyde towards the hot molecular core G358.93-0.03 MM1
- 2023MNRAS.525.6146W (2023): ALMA observations of the Extended Green Object G19.01-0.03 - II. A massive protostar with typical chemical abundances surrounded by four lo…
- 2023MNRAS.526.2077A (2023): Radio-continuum decrements associated to shadowing from the central warp in transition disc DoAr 44
- 2023MNRAS.526.4402B (2023): Fragmentation and dynamics of dense gas structures in the proximity of massive young stellar object W42-MME
- 2023MNRAS.526L..41P (2023): Kinematic and thermal signatures of the directly imaged protoplanet candidate around Elias 2-24
- 2023NatAs...7...49C (2023): UV-driven chemistry as a signpost of late-stage planet formation
- 2023NatAs...7..684K (2023): Azimuthal C/O variations in a planet-forming disk
- 2023Natur.622..251K (2023): A planetary collision afterglow and transit of the resultant debris cloud
- 2023PASJ...75..120F (2023): Twisted magnetic field in star formation processes of L1521 F revealed by submillimeter dual-band polarimetry using the James Clerk Maxwell…
- 2023PASJ...75.1105K (2023): Kinematic signatures of a low-mass planet with a moderately inclined orbit in a protoplanetary disk
- 2023PSJ.....4..206R (2023): ALMA Observations of the DART Impact: Characterizing the Ejecta at Submillimeter Wavelengths
- 2024A&A...681A..17D (2024): ALMA detection of CO rotational line emission in red supergiant stars of the massive young star cluster RSGC1. Determination of a new mass-…
- 2024A&A...681A..82G (2024): IRAS4A1: Multiwavelength continuum analysis of a very flared Class 0 disk
- 2024A&A...681A.110W (2024): A<SUP>3</SUP>COSMOS: Dissecting the gas content of star-forming galaxies across the main sequence at 1.2 ≤ z &lt; 1.6
- 2024A&A...682A...2C (2024): Near-infrared observations of outflows and young stellar objects in the massive star-forming region AFGL 5180
- 2024A&A...682A..24A (2024): The ALMA Reionization Era Bright Emission Line Survey: The molecular gas content of galaxies at z 7
- 2024A&A...682A..55M (2024): High-resolution ALMA observations of compact discs in the wide-binary system Sz 65 and Sz 66
- 2024A&A...682A..56Z (2024): Exploring the dust grain size and polarization mechanism in the hot and massive Class 0 disk IRAS 16293-2422 B
- 2024A&A...682A..61C (2024): A dusty streamer infalling onto the disk of a class I protostar. ALMA dual-band constraints on grain properties and the mass-infall rate
- 2024A&A...682A..78V (2024): JOYS+: Mid-infrared detection of gas-phase SO<SUB>2</SUB> emission in a low-mass protostar. The case of NGC 1333 IRAS 2A: Hot core or accre…
- 2024A&A...682L...5G (2024): Structures Of Dust and gAs (SODA): Constraining the innermost dust properties of II Zw96 with JWST observations of H<SUB>2</SUB>O and CO
- 2024A&A...683A.141R (2024): AB Aur, a Rosetta stone for studies of planet formation. III. Continuum observations at 2 and 7 mm
- 2024A&A...684A..33K (2024): The cold molecular gas in z ≳ 6 quasar host galaxies
- 2024A&A...684A.134R (2024): Correlation between accretion rate and free-free emission in protoplanetary disks. A multiwavelength analysis of central mm/cm emission in …
- 2024A&A...684A.200G (2024): The GRAVITY young stellar object survey. XIII. Tracing the time-variable asymmetric disk structure in the inner AU of the Herbig star HD 98…
- 2024A&A...684L..12S (2024): FAUST. XIII. Dusty cavity and molecular shock driven by IRS7B in the Corona Australis cluster
- 2024A&A...685A..52G (2024): The SPHERE view of the Chamaeleon I star-forming region. The full census of planet-forming disks with GTO and DESTINYS programs
- 2024A&A...685A..53G (2024): The SPHERE view of the Taurus star-forming region. The full census of planet-forming disks with GTO and DESTINYS programs
- 2024A&A...685A..54V (2024): Disk Evolution Study Through Imaging of Nearby Young Stars (DESTINYS): The SPHERE view of the Orion star-forming region
- 2024A&A...686A...9M (2024): Rotation curves in protoplanetary disks with thermal stratification. Physical model and observational evidence in MAPS disks
- 2024A&A...686A..64M (2024): Measuring the gas reservoirs in 10<SUP>8</SUP> &lt; M<SUB>⋆</SUB> &lt; 10<SUP>11</SUP> M<SUB>☉</SUB> galaxies at 1 ≤ z ≤ 3
- 2024A&A...686A.120U (2024): Vertical and radial distribution of atomic carbon in HD 163296
- 2024A&A...686A.122A (2024): ALMA-IMF. X. The core population in the evolved W33-Main (G012.80) protocluster
- 2024A&A...686A.146Z (2024): Gas inflows from cloud to core scales in G332.83-0.55: Hierarchical hub-filament structures and tide-regulated gravitational collapse
- 2024A&A...686A.206Y (2024): First ALMA observations of the HD 105211 debris disc: A warm dust component close to a gigayear-old star
- 2024A&A...686A.274V (2024): Molecular line polarisation from the circumstellar envelopes of asymptotic giant branch stars
- 2024A&A...686A.298G (2024): Into the thick of it: ALMA 0.45 mm observations of HL Tau at a resolution of 2 au
- 2024A&A...686L..13D (2024): FAUST. XV. A disc wind mapped by CH<SUB>3</SUB>OH and SiO in the inner 300 au of the NGC 1333 IRAS 4A2 protostar
- 2024A&A...687A.163B (2024): ALMA-IMF. XI. The sample of hot core candidates: A rich population of young high-mass protostars unveiled by the emission of methyl formate
- 2024A&A...687A.217D (2024): ALMA-IMF. XII. Point-process mapping of 15 massive protoclusters
- 2024A&A...687A.299L (2024): Chemistry across dust and gas gaps in protoplanetary disks. Modelling the co-spatial molecular rings in the HD 100546 disk
- 2024A&A...687A.308S (2024): Constraining the stellar masses and origin of the protostellar VLA 1623 system
- 2024A&A...688A...3H (2024): High-mass star formation across the Large Magellanic Cloud: I. Chemical properties and hot molecular cores observed with ALMA at 1.2 mm
- 2024A&A...688A.102T (2024): Orbital dynamics in the GG Tau A system: Investigating its enigmatic disc
- 2024A&A...688A.149D (2024): Disk Evolution Study Through Imaging of Nearby Young Stars (DESTINYS): PDS 111, an old T Tauri star with a young-looking disk
- 2024A&A...689A..85G (2024): MINDS: A multi-instrument investigation into the molecule-rich JWST-MIRI spectrum of the DF Tau binary system
- 2024A&A...689A.104D (2024): From traffic jams to roadblocks: The outer regions of TW Hya with ALMA Band 8
- 2024A&A...689A.283L (2024): ALMA reveals a dust-obscured galaxy merger at cosmic noon
- 2024A&A...689L...5M (2024): FAUST: XVIII. Evidence of annular substructure in a very young Class 0 disk
- 2024A&A...690A..46S (2024): Early Planet Formation in Embedded Disks (eDisk): XVI. Asymmetric dust disk driving a multicomponent molecular outflow in the young Class 0…
- 2024A&A...690A..55S (2024): NOEMA formIng Cluster survEy (NICE): Characterizing eight massive galaxy groups at 1.5 &lt; z &lt; 4 in the COSMOS field
- 2024A&A...690A.185W (2024): Dynamical accretion flows: ALMAGAL: Flows along filamentary structures in high-mass star-forming clusters
- 2024A&A...691A.180F (2024): CHEMOUT: CHEMical complexity in star-forming regions of the OUTer Galaxy: IV. ALMA observations of organic species at a galactocentric radi…
- 2024A&A...691A.248L (2024): The role of stellar mass in the cosmic history of star formation as seen by Herschel and ALMA
- 2024A&A...691L..14O (2024): Contemporaneous high-angular-resolution imaging of the AGB star W Hya in vibrationally excited H<SUB>2</SUB>O lines and visible polarized l…
- 2024A&A...692A..22Z (2024): ASW<SUP>2</SUP>DF: Census of the obscured star formation in a galaxy cluster in formation at z = 2.2
- 2024A&A...692A.155K (2024): Binary orbit and disks properties of the RW Aur system using ALMA observations
- 2024A&A...692A.215C (2024): Molecular gas budget of strongly magnified low-mass star-forming galaxies at cosmic noon
- 2024AJ....167...72D (2024): ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP): Molecular Jets and Episodic Accretion in Protostars
- 2024AJ....167...75H (2024): Shadowing in the Protoplanetary Disk of ZZ Tau IRS with HST
- 2024AJ....167...94H (2024): The Hidden Clumps in VY CMa Uncovered by the Atacama Large Millimeter/submillimeter Array
- 2024AJ....168..142L (2024): Gemini Planet Imager Observations of a Resolved Low-inclination Debris Disk around HD 156623
- 2024AJ....168..151J (2024): Absence of High-mass Prestellar Cores in the Orion Giant Molecular Cloud
- 2024ApJ...961....4B (2024): Protostellar Cores in Sagittarius B2 N and M
- 2024ApJ...961..228S (2024): Ring Gap Structure around Class I Protostar WL 17
- 2024ApJ...961L..35M (2024): The ALMA-QUARKS Survey: Detection of Two Extremely Dense Substructures in a Massive Prestellar Core
- 2024ApJ...962...13C (2024): ALMA High-resolution Spectral Survey of Thioformaldehyde (H<SUB>2</SUB>CS) toward Massive Protoclusters
- 2024ApJ...962...48J (2024): Thermal Properties of the Hot Core Population in Sagittarius B2 Deep South.
- 2024ApJ...962..196O (2024): Radio Jet Feedback on the Inner Disk of Virgo Spiral Galaxy Messier 58
- 2024ApJ...963....1O (2024): "Beads-on-a-string" Star Formation Tied to One of the Most Powerful Active Galactic Nucleus Outbursts Observed in a Cool-core Galaxy Cluster
- 2024ApJ...963..103G (2024): The ALMA View of Positive Black Hole Feedback in the Dwarf Galaxy Henize 2─10
- 2024ApJ...963..134Y (2024): Turbulent Vortex with Moderate Dust Settling Probed by Scattering-induced Polarization in the IRS 48 System
- 2024ApJ...964...48T (2024): An Extremely Young Protostellar Core, MMS 1/OMC-3: Episodic Mass Ejection History Traced by the Micro SiO Jet
- 2024ApJ...964...95S (2024): Physical Properties of Hyperluminous, Dust-obscured Quasars at z ∼ 3: Multiwavelength Spectral Energy Distribution Analysis and Cold Gas Co…
- 2024ApJ...964..146F (2024): JWST and ALMA Multiple-line Study in and around a Galaxy at z = 8.496: Optical to Far-Infrared Line Ratios and the Onset of an Outflow Prom…
- 2024ApJ...965...99T (2024): Discovery of Asymmetric Spike-like Structures of the 10 au Disk around the Very Low-luminosity Protostar Embedded in the Taurus Dense Core …
- 2024ApJ...965..108U (2024): ALMA Lensing Cluster Survey: Full Spectral Energy Distribution Analysis of z ∼ 0.5─6 Lensed Galaxies Detected with millimeter Observations
- 2024ApJ...966...32E (2024): Early Planet Formation in Embedded Disks (eDisk). XIII. Aligned Disks with Nonsettled Dust around the Newly Resolved Class 0 Protobinary R …
- 2024ApJ...966...59S (2024): Small and Large Dust Cavities in Disks around Mid-M Stars in Taurus
- 2024ApJ...966...84A (2024): Molecular Gas Tracers in Young and Old Protoplanetary Disks
- 2024ApJ...966..117X (2024): Disk Wind Feedback from High-mass Protostars. III. Synthetic CO Line Emission
- 2024ApJ...966..120L (2024): Dark Dragon Breaks Magnetic Chain: Dynamical Substructures of IRDC G28.34 Form in Supported Environments
- 2024ApJ...966..171M (2024): The ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES). XI. Statistical Study of Early Fragmentation
- 2024ApJ...967...15K (2024): Infall Motions in the Hot Core Associated with the Hypercompact H II Region G345.0061+01.794 B
- 2024ApJ...967..133S (2024): Hidden Gems on a Ring: Infant Massive Clusters and Their Formation Timeline Unveiled by ALMA, HST, and JWST in NGC 3351
- 2024ApJ...968....9W (2024): A Spatially Resolved [C II] Survey of 31 z ∼ 7 Massive Galaxies Hosting Luminous Quasars
- 2024ApJ...968...10F (2024): An ALMA Search for Substructure and Fragmentation in Starless Cores in Orion B North
- 2024ApJ...968...15L (2024): JWST and ALMA Discern the Assembly of Structural and Obscured Components in a High-redshift Starburst Galaxy
- 2024ApJ...968L..11G (2024): A Broad Line-width, Compact, Millimeter-bright Molecular Emission Line Source near the Galactic Center
- 2024ApJ...968L..19F (2024): Deep Search for Phosphine in a Prestellar Core
- 2024ApJ...969...27B (2024): MIDIS: JWST/MIRI Reveals the Stellar Structure of ALMA-selected Galaxies in the Hubble Ultra Deep Field at Cosmic Noon
- 2024ApJ...970...30M (2024): First Constraints on the Interstellar Medium Conditions of a Low-mass, Highly Obscured z = 4.27 Main-sequence Galaxy
- 2024ApJ...970..114T (2024): Evidence of Grain Alignment by Magnetically Enhanced Radiative Torques from Multiwavelength Dust Polarization Modeling of HL Tau
- 2024ApJ...970..137G (2024): The Empirical and Radiative Transfer Hybrid (EaRTH) Disk Model: Merging Analyses of Protoplanetary Dust Disk Mineralogy and Structure
- 2024ApJ...971..129C (2024): A Dust-trapping Ring in the Planet-hosting Disk of Elias 2-24
- 2024ApJ...971..176H (2024): Unraveling the Mystery of the Low CO-to-H<SUB>2</SUB> Conversion Factor in Starburst Galaxies: RADEX Modeling of the Antennae
- 2024ApJ...971L..23L (2024): Polarization Substructure in the Spiral-dominated HH 111 Disk: Evidence for Grain Growth
- 2024ApJ...972..115C (2024): MagMaR III—Resisting the Pressure, Is the Magnetic Field Overwhelmed in NGC6334I?
- 2024ApJ...972L...6S (2024): Magnetic Fields in Massive Star-forming Regions (MagMaR): Unveiling an Hourglass Magnetic Field in G333.46─0.16 Using ALMA
- 2024ApJ...973...42B (2024): Resolving Twin Jets and Twin Disks with JWST and ALMA: The Young WL 20 Multiple System
- 2024ApJ...973..135H (2024): Constraints on the Gas-phase C/O Ratio of DR Tau's Outer Disk from CS, SO, and C<SUB>2</SUB>H Observations
- 2024ApJ...974..102S (2024): Hints of Planet Formation Signatures in a Large-cavity Disk Studied in the AGE-PRO ALMA Large Program
- 2024ApJ...974..145S (2024): UNCOVER NIRSpec/PRISM Spectroscopy Unveils Evidence of Early Core Formation in a Massive, Centrally Dusty Quiescent Galaxy at z <SUB>spec</…
- 2024ApJ...974..257Z (2024): Magnetic Fields in Massive Star-forming Regions (MagMaR). IV. Tracing the Magnetic Fields in the O-type Protostellar System IRAS 16547─4247
- 2024ApJ...974..306S (2024): Constraints on the Physical Origin of Large Cavities in Transition Disks from Multiwavelength Dust Continuum Emission
- 2024ApJ...974L..25D (2024): Asymmetric Dust Accumulation of the PDS 70 Disk Revealed by ALMA Band 3 Observations
- 2024ApJ...975..235V (2024): JWST Imaging of Edge-on Protoplanetary Disks. III. Drastic Morphological Transformation Across the Mid-infrared in Oph163131
- 2024ApJ...976...29H (2024): ALMASOP. The Localized and Chemically Rich Features near the Bases of the Protostellar Jet in HOPS 87
- 2024ApJ...976..241Y (2024): The ALMA-QUARKS Survey: Fibers' Role in Star Formation Unveiled in an Intermediate-mass Protocluster Region of the Vela D Cloud
- 2024ApJ...977..190X (2024): Constraining the Excitation of Molecular Gas in Two Quasar-starburst Systems at z ∼ 6
- 2024ApJ...977..198L (2024): The SUPERCOLD-CGM Survey. II. [C I](1─0) Emission and the Physical Conditions of Cold Gas in Enormous Lyα Nebulae at z ∼ 2
- 2024ApJ...977L..46B (2024): [C II] Properties and Far-infrared Variability of a z = 7 Blazar
- 2024ApJS..270....9X (2024): The ALMA Survey of Star Formation and Evolution in Massive Protoclusters with Blue Profiles (ASSEMBLE): Core Growth, Cluster Contraction, a…
- 2024BSRSL..93..601H (2024): Influence of Mid-infrared Galactic Bubble on Surroundings: A Case Study on IRAS 16489-4431
- 2024MNRAS.527.3559P (2024): The debris disc of HD 131488: bringing together thermal emission and scattered light
- 2024MNRAS.529.3601R (2024): Observations of spiral and streamer on a candidate proto-brown dwarf
- 2024MNRAS.529L...1J (2024): New constraints on the molecular gas content of a z 8 galaxy from JVLA CO(J = 2-1) observations
- 2024MNRAS.530.4887W (2024): Little evolution of dust emissivity in bright infrared galaxies from 2 &lt; z &lt; 6
- 2024MNRAS.532.1752R (2024): Inner walls or vortices? Crescent-shaped asymmetries in ALMA observations of protoplanetary discs
- 2024MNRAS.533.2966Q (2024): ALMA follow-up of 3000 red-Herschel galaxies: the nature of extreme submillimetre galaxies
- 2024MNRAS.534.3576K (2024): Volatile composition of the HD 169142 disc and its embedded planet
- 2024MNRAS.535..729P (2024): The spatially resolved relation between dust, gas, and metal abundance with the TYPHOON survey
- 2024MNRAS.535.1533B (2024): A novel high-z submm galaxy efficient line survey in ALMA Bands 3 through 8 - an ANGELS pilot
- 2024NatAs...8..587F (2024): Resolved ALMA observations of water in the inner astronomical units of the HL Tau disk
- 2024RAA....24f5008M (2024): Study of Complex Nitrogen and Oxygen-bearing Molecules toward the High-mass Protostar IRAS 18089─1732
- 2024RAA....24f5011X (2024): The ALMA-QUARKS Survey. II. The ACA 1.3 mm Continuum Source Catalog and the Assembly of Dense Gas in Massive Star-Forming Clumps
- 2024Sci...383..988B (2024): A far-ultraviolet─driven photoevaporation flow observed in a protoplanetary disk
- 2025A&A...693A..17D (2025): Unveiling dust, molecular gas, and high star-formation efficiency in extremely UV bright star-forming galaxies at z ∼ 2.1─3.6
- 2025A&A...693A..49S (2025): A complete Herbig disk mass survey in Orion
- 2025A&A...693A.151M (2025): REsolved ALMA and SMA Observations of Nearby Stars (REASONS): A population of 74 resolved planetesimal belts at millimetre wavelengths
- 2025A&A...693A.190J (2025): ALMA Lensing Cluster Survey: Dust mass measurements as a function of redshift, stellar mass, and star formation rate from z = 1 to z = 5
- 2025A&A...693A.286S (2025): Intermediate mass T Tauri disk masses and a comparison to their Herbig disk descendants
- 2025A&A...693A.309S (2025): Behind the dust veil: A panchromatic view of an optically dark galaxy at z = 4.82
- 2025A&A...694A..82S (2025): The ALPINE-ALMA [CII] Survey: Unveiling the baryon evolution in the interstellar medium of z ∼ 5 star-forming galaxies
- 2025A&A...694A..86Y (2025): ALMA observations of massive clouds in the central molecular zone: slim filaments tracing parsec-scale shocks
- 2025A&A...694A..92B (2025): Protostellar Outflows at the EarliesT Stages (POETS) VI. Evidence of disk-wind in G11.92-0.61 MM1
- 2025A&A...694A.166C (2025): The ALMA-ATOMS survey: Vibrationally excited HC<SUB>3</SUB>N lines in hot cores
- 2025A&A...694A.171M (2025): The host galaxies of radio-loud quasars at z &gt; 5 with ALMA
- 2025A&A...694A.215F (2025): ALMA observations of super-early galaxies: Attenuation-free model predictions
- 2025A&A...694A.218B (2025): Revealing the hidden cosmic feast: A z = 4.3 galaxy group hosting two optically dark, efficiently star-forming galaxies
- 2025A&A...694A.295P (2025): ALMA detections of circumstellar disks in the giant H II region M17: Probing the intermediate- to high-mass pre-main-sequence population
- 2025A&A...695A..23S (2025): Molecular gas and dust properties in z &gt; 7 quasar hosts
- 2025A&A...695A..51B (2025): Hierarchical accretion flow from the G351 infrared dark filament to its central cores
- 2025A&A...695A.257R (2025): Survey of Orion Disks with ALMA (SODA): III. Disks in wide binary systems in L1641 and L1647
- 2025A&A...695L..15F (2025): Spatially resolved dust properties over 50 kpc in a hyperluminous galaxy merger at z = 4.6
- 2025A&A...695L..18M (2025): ALMA 360 parsec, high-frequency observations reveal warm dust in the center of a z = 6.9 quasar
- 2025A&A...696A...7L (2025): ALMA observations of CH<SUB>3</SUB>COCH<SUB>3</SUB> and the related species CH<SUB>3</SUB>CHO, CH<SUB>3</SUB>OH, and C<SUB>2</SUB>H<SUB>5</…
- 2025A&A...696A..33P (2025): The MUSE Ultra Deep Field (MUDF): VII. Probing high-redshift gas structures in the surroundings of ALMA-identified massive dusty galaxies
- 2025A&A...696A..59P (2025): GA-NIFS: High number of dual active galactic nuclei at z ∼ 3
- 2025A&A...696A.150S (2025): ALMAGAL: II. The ALMA evolutionary study of high-mass protocluster formation in the Galaxy: ALMA data processing and pipeline
- 2025A&A...696A.151C (2025): ALMAGAL: III. Compact source catalog: Fragmentation statistics and physical evolution of the core population
- 2025A&A...696A.232G (2025): A high-resolution survey of protoplanetary disks in Lupus and the nature of compact disks
- 2025A&A...697A..64V (2025): Turbulence in protoplanetary disks: A systematic analysis of dust settling in 33 disks
- 2025A&A...698A.165A (2025): Confirmation of a ring structure in the disk around MP Mus (PDS 66) with ALMA Band 7 observations
- 2025A&A...698A.183D (2025): Dust populations from 30 to 1000 au in the debris disk of HD 120326: Panchromatic view with VLT/SPHERE, ALMA, and HST/STIS
- 2025A&A...698A.231P (2025): Vertical CO surfaces as a probe for protoplanetary disk mass and carbon depletion
- 2025A&A...698L..16S (2025): FAUST: XXIV. Large dust grains in the protostellar outflow cavity walls of the Class I binary L1551 IRS5
- 2025A&A...699A..22M (2025): An accreting dwarf star orbiting the S-type giant star π<SUP>1</SUP> Gru
- 2025A&A...699A.324H (2025): ADF22+: A declining faint end in the far-infrared luminosity function in the SSA22 protocluster at z = 3.09
- 2025A&A...699A.369V (2025): Dense clumps survive in the vicinity of R136 in 30 Doradus
- 2025A&A...699A.373F (2025): Inner disc and circumplanetary material in the PDS 70 system: Insights from multi-epoch, multi-frequency ALMA observations
- 2025A&A...700A.235H (2025): CAMPOS: II. The onset of protostellar disk substructures and planet formation
- 2025A&A...700A.277C (2025): Dust emission from the bulk of galaxies in the Epoch of Reionisation
- 2025A&A...700L..11S (2025): Stephenson 2 DFK 52: Discovery of an exotic red supergiant in the massive stellar cluster RSGC2
- 2025A&A...701A.120P (2025): ALMA survey of a massive node of the Cosmic Web at z ∼ 3: II. A dynamically cold and massive disk galaxy in the proximity of a hyper-lumino…
- 2025A&A...701A.203S (2025): Multi-scale radiative-transfer model of the protoplanetary disc DoAr 44
- 2025A&A...701A.219N (2025): The Rosetta Stone project: III. ALMA synthetic observations of fragmentation in high-mass star-forming clumps
- 2025A&A...703A..15M (2025): Discovery of carbon monoxide emission from five debris disks around young A-type stars
- 2025A&A...704A.158C (2025): Pushing JWST to the extremes: Search and scrutiny of bright galaxy candidates at z ≃ 15─30
- 2025AJ....169..230H (2025): The Infrared-bright SW Knots in the Complex Ejecta of VY CMa
- 2025ApJ...984L..12B (2025): exoALMA. VII. Benchmarking Hydrodynamics and Radiative Transfer Codes
- 2025ApJ...984L..15P (2025): exoALMA. X. Channel Maps Reveal Complex <SUP>12</SUP>CO Abundance Distributions and a Variety of Kinematic Structures with Evidence for Emb…
- 2025ApJ...984L..16G (2025): exoALMA. XI. ALMA Observations and Hydrodynamic Models of LkCa 15: Implications for Planetary Mass Companions in the Dust Continuum Cavity
- 2025ApJ...984L..17L (2025): exoALMA. XII. Weighing and Sizing exoALMA Disks with Rotation Curve Modelling
- 2025ApJ...984L..18T (2025): exoALMA. XIII. Gas Masses from N<SUB>2</SUB>H<SUP>+</SUP> and C<SUP>18</SUP>O: A Comparison of Measurement Techniques for Protoplanetary Ga…
- 2025ApJ...984L..58H (2025): ALMASOP: Detection of Turbulence-induced Mass Assembly Shocks in Starless Cores
- 2025ApJ...985..226W (2025): A Multiwavelength Study of the Dynamic Environment Surrounding the FUor V960 Mon
- 2025ApJ...985L...8U (2025): ADF22-WEB: Detection of a Molecular Gas Reservoir in a Massive Quiescent Galaxy Located in a z ≍ 3 Protocluster Core
- 2025ApJ...986L..11S (2025): Hints of Disk Substructure in the First Brown Dwarf with a Dynamical Mass Constraint
- 2025ApJ...986L..22R (2025): The First Detection of Molecular Activity in the Largest Known Oort Cloud Comet: ALMA Imaging of C/2014 UN271 (Bernardinelli─Bernstein) at …
- 2025ApJ...987...61R (2025): Resolved ALMA [C II] 158 μm Observations at Cosmic Noon: Interstellar Medium Structure and Dynamics of the Starbursting QSO SDSS J1000
- 2025ApJ...987...77J (2025): Why is the Star Formation Rate Proportional to Dense Gas Mass?
- 2025ApJ...988...19S (2025): Detection of [O III]<SUB>88 μm</SUB> in JADES-GS-z14-0 at z = 14.1793
- 2025ApJ...988...95D (2025): An ALMA Study of Molecular Complexity in the Hot Core G336.99-00.03 MM1
- 2025ApJ...988..106H (2025): Grand Design Spiral Arms in the Compact, Embedded Protoplanetary Disk of Haro 6-13
- 2025ApJ...988..182N (2025): A Large-scale Ring Galaxy at z = 2.2 Revealed by JWST/NIRCam: Kinematic Observations and Analytical Modelling
- 2025ApJ...989....1Z (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). I. Program Overview and Summary of First Results
- 2025ApJ...989....3D (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). III. Dust and Gas Disk Properties in the Lupus Star-forming Region
- 2025ApJ...989....6K (2025): The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). VI. Comparison of Dust Evolution Models to AGE-PRO Observations
- 2025ApJ...989..115T (2025): ALMA Lensing Cluster Survey: Physical Characterization of Near-infrared-dark Intrinsically Faint ALMA Sources at z = 2─4
- 2025ApJ...990...80K (2025): Key Physical Parameters Influencing Fragmentation and Multiplicity in Dense Cores of Orion A
- 2025ApJ...990..166D (2025): Quenching through Tidal Gas Removal: Molecular Gas and Star Formation in Tidal Tails of z ∼ 0.7 Post-starburst Galaxies
- 2025ApJ...990..173C (2025): LZ-STAR Survey: Low-metallicity Star Formation Survey of Sh2-284. I. Ordered Massive Star Formation in the Outer Galaxy
- 2025ApJ...990L..61C (2025): An Upper Limit of 10<SUP>6</SUP> M<SUB>⊙</SUB> in Dust from ALMA Observations in 60 Little Red Dots
- 2025ApJ...991...59B (2025): ALMA Observations of Molecular Complexity in the Large Magellanic Cloud: Probing the Star-forming Region N 160
- 2025ApJ...992...18P (2025): Early Planet Formation in Embedded Disks (eDisk). XXII. Keplerian Disk, Disk Structures, and Jets/Outflows in the Class 0 Protostar IRAS 04…
- 2025ApJ...992...55T (2025): Extended and Compact Ortho-H<SUB>2</SUB>D<SUP>+</SUP> Structures Close to the Moment of Star Formation: Evidence from ALMA-ACA Observations…
- 2025ApJ...992L..15L (2025): A Dense Molecular Ringlike Structure in Gaseous CO Depletion Region G34.74−0.12
- 2025ApJ...993...90S (2025): ALMA High-resolution Observation for the Transitional Disk Around IRAS 04125+2902
- 2025ApJ...993..111W (2025): A Multiwavelength Study of ELAN Environments (AMUSE<SUP>2</SUP>): The Impact of Dense Environment on Massive Dusty Star-forming Galaxies at…
- 2025ApJ...993..120H (2025): Early Planet Formation in Embedded Disks (eDisk). XVII. A Compact but Structured Keplerian Disk and Large-scale Streamers Revealed in the C…
- 2025ApJ...993..200C (2025): The Hourglass-shaped Magnetic Fields and Dust Filaments in the HH 211 Protostellar Envelope
- 2025ApJ...993L..40S (2025): Unusually High Gas-to-dust Ratios Observed in High-redshift Quiescent Galaxies
- 2025ApJ...994..214T (2025): Dynamical Masses for 23 Pre-main-sequence Stars in Upper Scorpius: A Critical Test of Stellar Evolutionary Models
- 2025ApJ...994..225N (2025): Unveiling Stellar Feedback and Cloud Structure in the ρ Ophiuchi-A Region Using ALMA and JWST: Discovery of Substellar Cores, C<SUP>18</SUP…
- 2025ApJ...994..233Y (2025): ALMA-IMF. XX. Core Fragmentation in the W51 High-mass Star-forming Region
- 2025ApJ...995...16Z (2025): Measuring Dust Masses of Protoplanetary Disks in Serpens and L1641/L1647 with ALMA
- 2025ApJ...995...98D (2025): DiskMINT: Self-consistent Thermochemical Disk Models with Radially Varying Gas and Dust—Application to the Massive, CO-Rich Disk of IM Lup
- 2025ApJ...995..150K (2025): Comprehensive JWST+ALMA Study on the Extended Lyα Emitters, Himiko, and CR7 at z ∼ 7: Blue Major Merger Systems in Stark Contrast to Submil…
- 2025ApJ...995..193Y (2025): The ALMA-QUARKS Survey: Evidence of a Candidate High-mass Prestellar Core Aside a Bright-rimmed Cloud IRAS 18290-0924
- 2025ApJ...995..219F (2025): PASSAGES: The Discovery of a Strongly Lensed Protocluster Core Candidate at Cosmic Noon
- 2025ApJ...995L..63L (2025): ALMA Reveals Diverse Dust-to-gas Mass Ratios and Quenching Modes in Old Quiescent Galaxies
- 2025ApJ...995L..75C (2025): A Bridge between Young Stars Formed by Gravitational Interaction
- 2025ApJS..280...33Y (2025): The ALMA-QUARKS Survey. III. Clump-to-core Fragmentation and Searches for High-mass Starless Cores
- 2025MNRAS.538.2358S (2025): High angular resolution evidence of dust traps from deep ALMA Band 3 observations of LkCa15
- 2025MNRAS.539.3808U (2025): Physical properties and gas kinematics of massive star forming region G328.24−0.55
- 2025MNRAS.543.2723P (2025): Observational constraints on evolution of dust disc properties in Upper Scorpius
- 2025NatAs...9.1176R (2025): A young gas giant and hidden substructures in a protoplanetary disk
- 2025NatAs...9.1553F (2025): Primordial rotating disk composed of at least 15 dense star-forming clumps at cosmic dawn
- 2025NatAs...9.1833L (2025): Detection of a septuple stellar system in formation via disk fragmentation
- 2025Natur.641.1137B (2025): Quasar radiation transforms the gas in a merging companion galaxy
- 2025PASP..137j3001V (2025): An Introduction to Dust Evolution and Vertical Transport in Protoplanetary Disks
- 2025SciA...11.4512O (2025): Massive extended streamers feed high-mass young stars
- 2025SciA...11.6953M (2025): A misaligned protostellar disk fed by gas streamers in a barred spiral-like massive dense core
- 2026A&A...705A..96M (2026): FAUST: XXVIII. High-resolution ALMA observations of Class 0/I disks: Structure, optical depths, and temperatures
- 2026A&A...705A.100E (2026): ALMAGAL: V. Relations between the core populations and the parent clump physical properties
- 2026A&A...705A.197Z (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): III. The vertical structure of debris disks
- 2026A&A...705A.203W (2026): The ALMA survey to Resolve exoKuiper belt Substructures (ARKS): IX. Gas-driven origin for the continuum arc in the debris disc of HD121617
- 2026A&A...706A...4R (2026): Resolving the terrestrial planet-forming region of HD 172555 with ALMA: I. Post-impact dust distribution
- 2026A&A...706A.174A (2026): Hiding behind a curtain of dust: Gas and dust properties of an ultra-luminous strongly-lensed z = 3.75 galaxy behind the Milky Way disc
- 2026A&A...706A.214V (2026): Observational evidence for a possible link between PAH emission and dust trap locations in protoplanetary disks
- 2026A&A...706A.248T (2026): Interaction of the central jet with the surrounding gas in the protostellar outflow from IRAS 04166+2706
- 2026A&A...706A.256A (2026): Characterizing the physical and chemical properties of the Class I protostellar system Oph-IRS 44: Binarity, infalling streamers, and accre…
- 2026A&A...706A.285C (2026): Infrared emission from z ∼ 6.5 quasar host galaxies: a direct estimate of dust physical properties
- 2026A&A...707A..77H (2026): Massive dusty multiphase outflow in local merger shows no sign of slowing on kiloparsec scales
- 2026A&A...709A.173M (2026): ALMAGAL: VIII. Early phases of triggered star formation in source AG286.0716─1.8229
- 2026A&A...710A.238D (2026): Dust characterization of halos: The extended emission in protoplanetary disks
- 2026A&A...710L..10C (2026): Hourly radio variability of PDS 70c from time-differential photometry
- 2026A&A...711A.159M (2026): The formation radius of HCN in O-rich asymptotic giant branch stars
- 2026A&A...713A.149V (2026): Challenges in probing turbulent and magnetic support in cores: The W43-MM1 protocluster case study
- 2026A&A...713A.167D (2026): The dynamical environment of the high-mass star-forming region G28.288-0.364
- 2026AJ....171..368M (2026): Digging into the Massive Protostar S255IR NIRS3: A Study of Nitrogen-bearing Molecules and Their Prebiotic Chemistry
- 2026AJ....172...75M (2026): ALMA Observations of Magnetic Fields in the Massive Star-forming Region IRAS 18360-0537
- 2026AJ....172..108L (2026): Formation of a Protostellar Multiple System via Rotational Fragmentation
- 2026ApJ...997..155M (2026): The ALMA Survey of 70 µm Dark High-mass Clumps in Early Stages (ASHES). XIII. Core Mass Function, Lifetime, and Growth of Prestellar Cores
- 2026ApJ...997..218A (2026): Tentative Detection of Neutral Gas in a Little Red Dot at z = 4.46
- 2026ApJ...998..277M (2026): ALMA Observations of Cold Methanol Gas in the Large Magellanic Cloud: N79 South Giant Molecular Cloud
- 2026ApJ...999..194I (2026): Digging into the Chemical Complexity in the Outer Galaxy: A Hot Molecular Core in Sh 2-283
- 2026ApJ..1000..144T (2026): Active Galactic Nucleus Feedback and the Development of Dusty Multiphase Gas in X-Ray Emitting Elliptical Galaxies
- 2026ApJ..1000..159M (2026): Low Dust Mass and High Star Formation Efficiency at z &gt; 12 from Deep ALMA Observations
- 2026ApJ..1001..120X (2026): Disk Wind Feedback from High-mass Protostars. V. Application of Multimodal Machine Learning to Characterize Outflow Properties
- 2026ApJ..1001..131C (2026): MAGAZ3NE: Far-IR and Radio Insights into the Nature and Properties of Ultramassive Galaxies at z ≳ 3
- 2026ApJ..1003..206S (2026): The Identification of Two JWST/NIRCam-dark Starburst Galaxies at z = 6.6 with ALMA
- 2026ApJ..1003..219W (2026): The Keplerian Disk, Envelope, and Streamers Surrounding an Early O-type Protostar in the Sagittarius C Cloud of the Central Molecular Zone
- 2026ApJ..1004..114V (2026): JWST's PEARLS: A Clumpy Ring Galaxy at z = 4.0148
- 2026ApJ..1004L...6D (2026): First Interstellar Detection of Methyl Carbamate: A New Observational Anchor for Glycine Chemistry
- 2026ApJ..1005...94N (2026): Dynamical Evidence for a Billion Solar-mass Black Hole in Galaxy NGC 4061 from ALMA <SUP>12</SUP>CO(2─1) Kinematics
- 2026ApJ..1005..142S (2026): Survival of Molecular Complexity under Recent Supernova Feedback: Detection of Hot Cores in RX J1713.7−3946
- 2026ApJS..282...64S (2026): Magellanic Outflow and Chemistry Survey (MAGOS): Hot Cores in the LMC
- 2026MNRAS.545f2150S (2026): HD 44892: the youngest (or oldest?) gas-harbouring debris disc around an intermediate-mass star
- 2026MNRAS.546f2284B (2026): Probing infrared eXcess to investigate early-Universe dust (PIXIEDust)
- 2026MNRAS.548ag325W (2026): 3D insights into SN 1987A: ALMA observations compared to hydrodynamical explosion simulations
- 2026MNRAS.548ag641R (2026): Large dust grains and a possible dust trap in the polar circumbinary disc of HD 98800B
- 2026MNRAS.551g1645K (2026): A high-velocity SiO jet from S255N SMA3
