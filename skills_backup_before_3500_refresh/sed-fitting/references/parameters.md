# Parameter reference for `alma-sed-fitting`

All values are copied from the evidence pack (`skills/packs/sed-fitting.md`) with the bibcode that used them.
They are what papers assumed, not recommendations; quote the one you adopt with its source.

## Dust opacity normalizations

Mass basis matters. "Dust" means kappa is per gram of dust, so the MBB normalization gives M_dust and a gas mass
needs a gas-to-dust ratio. "Gas+dust" means kappa already includes the gas (the normalization gives total gas
mass); never multiply by a gas-to-dust ratio again. Where the pack does not state the basis, the column says how
it was judged. Keep each paper's reference wavelength; convert with (nu/nu0)^beta and a stated beta if needed.

| kappa | Reference wavelength | Basis | Papers |
|---|---|---|---|
| 0.077 m2/kg (= 0.77 cm2/g) | 850 um / 352 GHz | dust (general practice for this value) | 2016ApJ...827...34O, 2018ApJ...854...97D, 2019ApJ...881..124M, 2019MNRAS.482.3135B, 2025ApJ...995..219F, 2026ApJ..1002L..28Y (6, my count) |
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
| 1.7 cm2/g x (850 um / lambda) | debris disks | dust | 2025A&A...698A.183D |

At exactly 850 um / 352-353 GHz the pack's values span 0.0383-0.15 m2/kg.

Factor-2 effects: Dunne et al. 2000 vs Hildebrand 1983 doubles M_d (2019PASJ...71...71H); CIGALE dust masses
halved to match Draine07 opacities (2025A&A...694A..82S).

## Fixed (T_dust, beta) pairs by context

| Context | T_dust | beta | Papers |
|---|---|---|---|
| z > 5.7 quasar hosts and companion galaxies | 47 K | 1.6 | 2013ApJ...770...13W, 2016ApJ...816...37V, 2017Natur.545..457D, 2018ApJ...854...97D, 2019ApJ...874L..30V, 2020ApJ...904..130V |
| z ~ 2 Lya nebulae (quasar-hosting) | 47 K | 1.6 | 2024ApJ...977..198L |
| z ~ 2.5 reddened quasars | 41 K / 47 K | 1.95 / 1.6, averaged | 2017MNRAS.465.4390B |
| Count scaling between bands (SMGs at z = 2.5) | 35 K | 1.5 | 2015ApJ...806L..25S, 2017ApJ...835...98U, 2018PASJ...70...65U, 2019MNRAS.487.4648S |
| SMGs, single band | 35 K | 1.8 | 2017ApJ...850...83F, 2019ApJ...887..107F, 2025ApJS..278...45F |
| z ~ 4.75 starburst, general opacity | 58.5 +/- 5.3 K (fit) | 2 (fixed), lambda_0 = 200 um | 2014A&A...562A..67G |
| Hot DOG / companions | 50-100 K / 25-50 K | 1.8 | 2018Sci...362.1034D |
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
