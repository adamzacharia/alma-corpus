# Parameter reference for `alma-sed-fitting`

All values are copied from the evidence pack (`skills/packs/sed-fitting.md`) with the bibcode that used them.
They are what papers assumed, not recommendations; quote the one you adopt with its source. Rows marked
"(earlier pack)" were checked against the first-round pack; the current pack lists those papers only in its paper
list, so they are examples, not counted.

## Integration ranges (how counted)

Rule: a paper counts for a range if a parameter/assumption line names that wavelength interval as an integration
or definition range, whatever label it uses (L_IR, L_FIR, TIR, "FIR integration range"). Regex over the pack's
parameter/assumption lines for "8 ... 1000 um" variants gave 20 bibcodes; 2018ApJ...853..195W only uses
L_IR(8-1000 um) in a conversion, leaving 19 that integrate over 8-1000 um.

| Range | Count | Papers |
|---|---|---|
| 8-1000 um | 19 | 2017ApJ...836....8T (TIR), 2018ApJ...869...27V, 2018MNRAS.478.3721S, 2018MNRAS.481.1976Z, 2019MNRAS.488.1180S, 2020MNRAS.496..875R (labelled L_FIR), 2020MNRAS.496.4405H, 2021A&A...654A..90L, 2021ApJ...908..235I (TIR), 2021ApJ...909..204F (labelled FIR), 2022A&A...657A..25N, 2022ApJ...941...47S (labelled FIR), 2024A&A...681A.110W, 2024A&A...689A.220T, 2024ApJ...977L..46B, 2024MNRAS.530.4887W, 2025A&A...694A.218B, 2025ApJ...987L..37W, 2026ApJ..1003..206S |
| 42.5-122.5 um | 4 | 2017ApJ...836....8T, 2021ApJ...908..235I (lists); 2020MNRAS.498.4192F, 2014ApJ...796...84R (excerpts) |
| 3-1100 um | 1 (+1 conversion) | 2020MNRAS.498.4192F; conversion only in 2018ApJ...853..195W |

## Photometric calibration floors

| Instrument / band | Value | Type | Paper |
|---|---|---|---|
| ALMA (all bands) | 10% | systematic, added in quadrature | 2024MNRAS.530.4887W, 2021ApJ...918...76C, 2022MNRAS.509..748W, 2020PASA...37...26D |
| ALMA Bands 3, 4 / 6, 7 / 8, 9 | 5% / 10% / 20% | absolute flux, band-dependent | 2024ApJ...974..306S |
| ALMA 0.45, 0.9, 1.3, 7 mm / 2.1 mm | 10% / 5% | flux calibration | 2024A&A...686A.298G |
| PACS / SPIRE / SCUBA-2 / LABOCA / SPT | 7% / 5.5% / 5% / 12% / 7% | calibration, in quadrature | 2024MNRAS.530.4887W |
| LABOCA / SABOCA / PACS / SPIRE / HAWC+ | 15% / 20% / 10% / 7% / 20% | flux uncertainty | 2024A&A...686A.122A |
| HAWC+ | 10% relative; 15 +/- 7% above PACS on a comparison source | relative calibration | 2024A&A...688A...8W |
| Herschel | 20% | flux uncertainty | 2018A&A...616A.127R |
| VLA < 15 GHz / >= 15 GHz | 5% / 15% | systematic | 2021ApJ...918...76C |
| SMA, CARMA | 15% | systematic | 2022MNRAS.509..748W |
| PACS / other bands | 7% / 10% | calibration (earlier pack) | 2016ApJ...822...80S |

ALMA band dependence (5-20% within ALMA) is separate from differences between instruments; give both.

Colour corrections seen: Herschel corrections assuming an MBB with beta = 2 (2024A&A...687A.217D); SPIRE
colour/aperture corrections iterated with a power-law SED from 250 and 350 um fluxes (2023MNRAS.519.5807D); IRAC
aperture corrections (2020MNRAS.496..875R).

## Counting rules for the SKILL.md table

Regex over the pack's parameter/assumption lines (lines 154-1559), distinct bibcodes: "47 K" with "1.6" on the same
line (10 hits, 9 after dropping 2024ApJ...972..116I, which adopts 35 K and only mentions 47 K); "35 K" (15); beta followed by "=" or "fixed at" and 2/2.0, 1.6, 1.5, 1.8 (27, 16, 16, 15); kappa
0.077 m2/kg or 0.77 cm2/g at 850 um (5: 2014A&A...562A..70M, 2021A&A...645A..33B, 2021MNRAS.500.3667S,
2024MNRAS.530.4887W, 2024ApJ...972..116I); gas-to-dust or dust-to-gas with 100 / 0.01 / 1:100 (30); z = 2.5 with
a redshift context (4); "CMB" (12); "Kennicutt" (13); Chabrier / Salpeter / Kroupa (61 / 20 / 14). Regex counts
can miss unusual phrasings; treat them as lower bounds.

## Dust opacity normalizations

Mass basis matters. "Dust" means kappa is per gram of dust, so the MBB normalization gives M_dust and a gas mass
needs a gas-to-dust ratio. "Gas+dust" means kappa already includes the gas (the normalization gives total gas
mass); never multiply by a gas-to-dust ratio again. Where the pack does not state the basis, the column says how
it was judged. Keep each paper's reference wavelength; convert with (nu/nu0)^beta and a stated beta if needed.

| kappa | Reference wavelength | Basis | Papers |
|---|---|---|---|
| 0.077 m2/kg (= 0.77 cm2/g) | 850 um / 352-353 GHz | dust (general practice for this value) | 2014A&A...562A..70M, 2021A&A...645A..33B, 2021MNRAS.500.3667S, 2024MNRAS.530.4887W, 2024ApJ...972..116I (5, current pack); 2016ApJ...827...34O, 2018ApJ...854...97D, 2019ApJ...881..124M, 2019MNRAS.482.3135B, 2025ApJ...995..219F, 2026ApJ..1002L..28Y (earlier pack) |
| 0.0968 m2/kg | 850 um / 352.7 GHz | dust (gas-to-dust 200 listed separately) | 2025A&A...695L..15F |
| 0.45 cm2/g | 250 GHz | not stated; optically thick fit | 2024A&A...689A.220T |
| 0.077 m2/kg | 870 um | dust (general practice) | 2015ApJ...811..124S |
| 0.15 m2/kg | 850 um / 353 GHz (Draine 2003) | dust | 2019ApJ...874...27T, 2020MNRAS.493.4294B |
| 0.15 m2/kg | 870 um | dust | 2014MNRAS.438.1267S |
| 0.0484 m2/kg | 850 um | dust (gas-to-dust 100 listed separately) | 2018Sci...362.1034D |
| 0.383 cm2/g (= 0.0383 m2/kg) | 850 um | not stated | 2017ApJ...851...98T |
| 2.64 m2/kg | 125 um | dust (general practice) | 2015ApJ...810...91H, 2019ApJ...871...85L, 2019ApJ...876...91H, 2019ApJ...881...63N |
| 1.875 m2/kg | 125 um | dust (general practice) | 2016ApJ...819...82S |
| 0.09 m2/kg | 352 GHz | dust (gas-to-dust ~60 listed separately) | 2014A&A...567A.125G |
| 0.045 m2/kg | 250 GHz | not stated | 2017MNRAS.465.4390B |
| 0.4 cm2/g | 250 GHz | not stated | 2018PASJ...70...36I |
| 0.1 cm2/g x (nu / 1 THz)^beta | 1 THz | gas+dust, stated ("includes gas-to-dust 100") | 2018MNRAS.475..448T |
| 0.1 cm2/g x (nu / 1 THz)^beta | 1 THz | not stated | 2018ApJ...866..141K |
| 0.1 cm2/g x (250 um / lambda)^beta | 250 um | check: gas-to-dust 100 is listed with it | 2015ApJ...801...82H, 2020ApJ...896..127K |
| 0.9 cm2/g | 230 GHz | dust (dust-to-gas 0.01 listed separately) | 2021A&A...653A.117B |
| 0.899 cm2/g | 1.3 mm | dust (gas-to-dust 150 listed separately) | 2024A&A...690A.185W |
| 1.7 cm2/g x (850 um / lambda) | 850 um, debris disks | dust | 2025A&A...698A.183D |
| 1.7 cm2/g (= 0.17 m2/kg) | 850 um | dust; LMC evolved-star nebulae | 2019A&A...626A.126A, 2021A&A...655A..98A (about 25% kappa uncertainty not propagated) |
| 1.7 cm2/g | 343 GHz | dust | 2017ApJ...841..130A |

At 850 um / 352-353 GHz the pack's values span 0.0383-0.15 m2/kg in galaxy fits and reach 0.17 m2/kg in the
stellar-nebula and debris-disk papers (2019A&A...626A.126A, 2021A&A...655A..98A, 2025A&A...698A.183D).

Factor-2 effects: Dunne et al. 2000 vs Hildebrand 1983 doubles M_d (2019PASJ...71...71H); CIGALE dust masses
halved to match Draine07 opacities (2025A&A...694A..82S).

## Fixed (T_dust, beta) pairs by context

| Context | T_dust | beta | Papers |
|---|---|---|---|
| Quasar hosts and companions (current pack lines, 9) | 47 K | 1.6 | 2013ApJ...773...44W, 2018MNRAS.479.1154B, 2019ApJ...879..117K, 2019MNRAS.488.1180S, 2020ApJ...903...34A, 2021ApJ...908..235I, 2024ApJ...977..190X, 2024ApJ...977L..46B, 2026MNRAS.546ag167S |
| z > 5.7 quasar hosts (earlier pack) | 47 K | 1.6 | 2013ApJ...770...13W, 2016ApJ...816...37V, 2017Natur.545..457D, 2018ApJ...854...97D, 2019ApJ...874L..30V, 2020ApJ...904..130V |
| z ~ 2 Lya nebulae (quasar-hosting) | 47 K | 1.6 | 2024ApJ...977..198L |
| z ~ 2.5 reddened quasars | 41 K / 47 K | 1.95 / 1.6, averaged | 2017MNRAS.465.4390B |
| Count scaling between bands (SMGs at z = 2.5) | 35 K | 1.5 | 2015ApJ...806L..25S, 2017ApJ...835...98U, 2018PASJ...70...65U, 2019MNRAS.487.4648S |
| SMGs, single band | 35 K | 1.8 | 2017ApJ...850...83F, 2019ApJ...887..107F, 2025ApJS..278...45F |
| z ~ 4.75 starburst, general opacity | 58.5 +/- 5.3 K (fit) | 2 (fixed), lambda_0 = 200 um | 2014A&A...562A..67G |
| Hot DOG / companions | 50-100 K / 25-50 K | 1.8 | 2018Sci...362.1034D |
| Debris disk, no far-IR data | break-wavelength law, lambda0 = 100 um | 0.65 | 2025A&A...703A..15M |
| Debris disk, cold / warm belt | break-wavelength law, lambda0 = 380 / 160 um | 2.3 / ~0 | 2024A&A...686A.206Y |
| LMC evolved-star dust | grey body | 0 | 2021A&A...655A..98A |
| Rayleigh-Jeans gas-mass method | 25 K | 1.8 | 2016ApJ...833...68A, 2017ApJ...844..123F, 2020ApJ...901...79A |
| Cluster BCG upper limit | 25 K | 1.8 | 2024ApJ...963....1O |
| Galactic clumps by L/M | 20 K (L/M<1), 35 K (1-10), max(21.1 (L/M)^0.22, 35 K) | n/a | 2024A&A...690A.185W |
| Galactic Center cloud column density | 20 K | 1.2 +/- 0.1 | 2014ApJ...795L..25R |
| Orion KL compact sources | 100 K or 20 K | free | 2015ApJ...801...82H |

## Fitted results seen (for sanity checking your own)

| Object type | T_dust | beta | Paper |
|---|---|---|---|
| NGC 1068 CND | 46 +/- 3 K | 1.7 +/- 0.2 | 2014A&A...567A.125G |
| NGC 253 CMZ | 42 +/- 1 K | 1.9 (fixed) | 2021A&A...656A..46M |
| Galactic cloud near GRS 1915+105 | 29.0 K | 1.44 +/- 0.03 | 2018MNRAS.475..448T |
| z ~ 3.3 lensed SMG | 37 (+4/-3) K | 2 (fixed) | 2016A&A...596A..75S |
| QSO / star-forming companion | 24 +/- 6 K / 16 +/- 3 K | (MR-MOOSE) | 2020MNRAS.493.3744F |
| Obscured quasar warm component | 81 K (cold fixed 35 K) | 1.5 | 2014ApJ...790..160S |
| z ~ 3 starburst, beta grid | best 39 +/- 2 K | 2.5 (best of 1.5/2/2.5) | 2018MNRAS.477.4380S |

## SFR and luminosity conversions

| Conversion | IMF | Papers |
|---|---|---|
| SFR = 1.40e-10 L'_IR, L'_IR = star-forming part (AGN removed; 1.40e-10 x (1-0.59) x 1.34e13 Lsun = 770 Msun/yr, their SFR, my arithmetic) | Chabrier | 2024ApJ...962....1S |
| SFR_IR = 1.40e-10 L_IR | Chabrier | 2025A&A...698A.204H |
| SFR = 1.0e-10 L_IR (Kennicutt98) | Chabrier | 2017ApJ...844..123F |
| SFR = 1.09e-10 L_IR, after subtracting a 20% AGN share | Chabrier | 2018ApJ...853...24U |
| SFR = 1.65 Msun/yr x L_IR / 1e10 Lsun | Chabrier | 2018ApJ...853..195W |
| SFR = 1.72e-10 L_IR,SF, then /1.5 to Kroupa | Salpeter | 2019A&A...621A..27F |
| SFR = 1.73e-10 L_IR | Salpeter | 2026A&A...705A..39P |
| SFR = 1.8e-10 L_IR | Salpeter | 2020ApJ...892..119M |
| Salpeter-based SFR divided by 1.8 for Chabrier | | 2017A&A...604A.117C |
| L_TIR = 1.41 L_FIR | | 2020ApJ...904..130V |
| L_bol / L_FIR = 1.91 | | 2018ApJ...867..140L |
| L_TIR(3-1100 um) ~ 1.1 L_IR(8-1000 um) | | 2018ApJ...853..195W |
| MBB underestimates L_FIR by ~20% | | 2017ApJ...844L..10S |
| <U> = L_IR / (125 M_dust) | | 2020A&A...641A.155V, 2019MNRAS.485.2092C |

## Panchromatic code settings seen

| Code | Setting | Paper |
|---|---|---|
| CIGALE | delayed SFH, BC03, nebular, modified-starburst attenuation, DL2014, SKIRTOR, radio (q_IR 2.4-2.7, alpha 0.7) | 2026ApJ..1001..131C |
| CIGALE | delayed SFH, DL07, Fritz AGN, metallicity half solar, torus optical depth 2 | 2024ApJ...962....1S |
| CIGALE | double-exponential SFH, Calzetti, DL2014, Fritz torus | 2018ApJ...859...35G |
| CIGALE | AGN fraction grid 0-0.99, polar E(B-V) 0 and 0.8 | 2025ApJ...988..185G |
| CIGALE | extreme f_AGN fits redone with U fixed to the redshift average (30% variation) | 2021A&A...654A.165V |
| DL model (in an SED code) | Umax = 1e6, beta = 2, gamma = 0.01, 0.47 < qPAH < 4.6 | 2025ApJ...995L..63L |
| MAGPHYS | high-z version, BC03 | 2016ApJ...833..112S |
| MAGPHYS | 0.1 dex added in quadrature to outputs | 2020ApJ...901...79A |
| MAGPHYS | 26 filters U to IRAC 8 um plus ALMA 1.2 mm, no Herschel | 2016ApJ...833...68A |
| sed3fit | radio q Gaussian prior mean 2.34, sigma 0.25 | 2018ApJ...864...60M |
| Radio component | q_FIR centred at 2.34 (sigma 0.25), thermal fraction 0.1, synchrotron nu^-0.8 | 2017A&A...606A..17M |

## MCMC settings seen

Fixed walker/step counts do not show convergence; check autocorrelation time or effective sample size and chain
plots (general practice). Only dust or disk fits are listed (the 2020A&A...633A.160C 100 x 2500 run fits the
UV-continuum slope, not dust).

| Walkers x steps | Burn-in | Free parameters (as the pack states) | Paper |
|---|---|---|---|
| 50 x 1e6 | 1e4 | beta fixed 1.8 | 2017ApJ...839...58S |
| about 100 x 1000 | about 100 | debris disk model | 2017ApJ...839...86H |
| 100 x 500 | 100 | beta=1.8 listed; free set not stated | 2019MNRAS.482.3135B |
| 84 x 1500 | 500 | FU Ori disk model | 2019ApJ...884...97L |
| 24 x 5000 | median from last 4200 | disk gas model | 2025ApJ...984L..19Y |

## Priors seen (MBB fits)

| Prior | Paper |
|---|---|
| uniform T > 1 K, beta 0.1-20 (also lambda_0, alpha) | 2019ApJ...871...85L (earlier pack) |
| beta limited to 0-2 to bound T | 2021A&A...653A.117B |
| T < 100 K observed-frame (multiply by (1+z) for rest frame), beta < 3 | 2014A&A...568A..92M (earlier pack) |
| flat T, Gaussian beta 1.8 +/- 0.5 | 2020MNRAS.498.4192F |
| flat T 20-50 K, beta 0.5-4 | 2024MNRAS.530.4887W |
| flat 1e-2 < A < 33 kpc2, 12.6 < T_d < 300 K, 1e6 < M_d < 1e10 Msun, 1 < beta < 3; A capped by beam area | 2025A&A...695L..15F |
| T 10-100 K default, 30-50 K adopted for AGN-leakage test | 2024ApJ...964...95S |

## IR templates seen

| Template | Use | Paper |
|---|---|---|
| Chary & Elbaz 2001 | luminosity-dependent, used without rescaling | 2021ApJ...915...46C |
| Chary & Elbaz 2001 | scaled to the ALMA flux (earlier pack) | 2012ApJ...761L..32W |
| Bethermin 2017 | scaled; MS vs starburst by main-sequence offset | 2020A&A...643A...2B (earlier pack), 2024A&A...681A.110W |
| Schreiber 2018 | scaled | 2021A&A...652A..30S (earlier pack) |
| Kirkpatrick 2015 | scaled | 2018ApJ...853..195W |
| Magdis 2012 via STARDUST | after super-deblending | 2024A&A...690A..55S (earlier pack) |
| several libraries compared | template systematics | 2019MNRAS.486..560S (earlier pack) |

## SFR averaging timescales

| Timescale | Paper |
|---|---|
| last 10 Myr (CIGALE) | 2024ApJ...965..108U |
| last 100 Myr SFH average (BayeSED) | 2024ApJ...964...95S |
| 100 Myr (nonparametric SFH, continuity prior) | 2025ApJ...989..115T |
| 100 Myr average "current SFR" | 2024PASA...41..114S |
| instantaneous (GalaPy) | 2025A&A...699A.183H |
| constant SF over 100 Myr behind SFR_IR ~ 1.1e-10 L_FIR (Kroupa) | 2021A&A...652A.128J |

## Single-band sensitivity ranges (T_d) by population

Conditional tests, not full bounds; keep T_d above T_CMB(z) = 2.73 (1+z) K.

| Population | Range | Paper |
|---|---|---|
| SMGs | 25-45 K around 35 K | SKILL.md table |
| z > 4 star-forming galaxies | 35-55 K around 45 K | 2021A&A...646A..26B |
| quasar hosts | 41-60 K around 47 K, beta 1.6-1.95 | 2017MNRAS.465.4390B (earlier pack) |
| quasar hosts | 30-50 K | 2019MNRAS.488.1180S |
| hot or very luminous systems | 50-100 K | 2018Sci...362.1034D |
| luminous QSOs | 40 vs 80 K gives 50% lower / 2x higher L_IR | 2021A&A...645A..33B |
| z-dependent relation | 30-65 K | 2020A&A...633A.160C (earlier pack) |
