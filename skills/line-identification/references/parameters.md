# Line identification: per-paper settings from the evidence pack

Every value below is taken from the `line-identification` evidence pack (verified card quotes). Blank or
missing settings mean the card did not state them.

## Detection and selection rules

| Paper | Detection rule | Transition or blend rule | Lines used / found |
|---|---|---|---|
| 2018A&A...615A..28D | continuous emission above 3x local off-source channel rms | soft-parabola fit to expose blends; manual inspection; masers excluded | 168 lines (IK Tau), 197 (R Dor), 66 unidentified |
| 2025A&A...694A.166C | above 3 sigma, velocity near systemic | at least three lines per vibrational state to fit | HC3N* in 52 of 60 hot cores |
| 2020A&A...644A..84M | above 3 rms (one of three rules) | Eu < 250 K for the main fit; blending criteria | 25 MF, 12 GA, 14 AA lines |
| 2020ApJ...896...35J | above 5 sigma in 0.5" radius aperture mean spectrum | simultaneous SLSQP Gaussian fits | 203 lines, 25 molecules |
| 2024ESC.....8..665M | above 5 sigma | non-blended lines checked with JPL and Splatalogue | 6 non-blended lines |
| 2025NatAs...9.1476C | contiguous channels above 2 sigma, peak above 3 sigma | | |
| 2020ApJ...893..101L | above 4 sigma in matched-filter response | Keplerian templates from 12CO, 13CO, C18O, DCO+, H13CO+, H2CO, N2H+, CS | 14 species |
| 2019ApJ...871..170M | above 2 sigma; 1-sigma mask on model Gaussian | | |
| 2015ApJ...803...97S | | NB if contaminant weaker than about 10% of the target | 84, 68, 62 lines in vt = 0, 1, 2 |
| 2018A&A...616A..90C | | only optically thin lines, tau < 0.2 | |
| 2017A&A...604L...2F | | Eup up to about 400 K, Aij >= 1e-4 s^-1 | |
| 2019ApJ...872..196S | match at 3 sigma | Aij >= 1e-5 s^-1 | |
| 2024AJ....167...66Y | | Aul >= 1e-8 s^-1, Eu <= 1000 K | |
| 2019A&A...628A..10B | visual inspection of full-band model | H-alpha contamination checked | 9 clearly detected urea lines |
| 2016ApJ...830L..37I | | CDMS and JPL at v_sys 8.34 km/s | 31 lines assigned |
| 2025ApJS..276...49J | ~3700 lines above 3 sigma | species kept when all modelled lines match, then visual check | 23 COM species; ~20% lines unidentified |

## LTE model settings used to check identifications

| Paper | Software | Tex / Trot | Width | Source size | Other |
|---|---|---|---|---|---|
| 2018A&A...616A..90C | CASSIS grid, reduced chi2 | 90-300 K grid | 1.8-2.4 (A), 0.8-1.2 (B) km/s | 0.5" | N 1e13-1e17 cm^-2; continuum as background |
| 2019NatAs...3..314L | XCLASS, MAGIX | 120 K | 2 km/s fixed | 0.6" | CH3OH = 13CH3OH x 60 |
| 2025ApJS..276...49J | XCLASS | 120 K | 3 km/s | filling factor 0.384 | N 5e12-5e18 cm^-2 in 35 steps |
| 2019A&A...628A..10B | Weeds | 160 K | 5.0 km/s | 2" for all species | visual optimization |
| 2020ApJ...896...35J | CASSIS | 160 K (CH3OH reference) | 5 km/s | 0.5" | N_H2 4e25 cm^-2, abundance 1e-8, v_LSR -52 km/s |
| 2024ESC.....8..665M | CASSIS LTE-RADEX, least squares | fit: 250 K; +/- 25 K in the abstract, +/- 35 K in Sec. 3.2 (inconsistent in the paper, unresolved in the card) | fit: 5.2 +/- 0.8 km/s | 1.3" | Tbg 2.73 K, Tc 0, v_sys 97 km/s |
| 2024IJAsB..23...14M | CASSIS MCMC | fit: 210.5 +/- 32.8 K | | 23.75" extraction circle (radius or diameter not stated) | v_LSR 68.50 km/s, 2nd-order baseline |
| 2025A&A...694A.166C | XCLASS | free | free | free (deconvolved core size) | same abundance for all vibrational states |
| 2020MNRAS.492.1180R | MADCUBA-AUTOFIT, Levenberg-Marquardt | fixed 5 K (PN, PO), 34 K (SO) | free | | single transitions; N varies x2.1-2.5 over 5-50 K |
| 2017MNRAS.469.2230M | | | 1.1 km/s | 0.5" | LTE |
| 2019A&A...631A..64B | CASSIS grid | fit: 220 +/- 20 K | | 0.15" | non-detections must not be produced |
| 2016ApJ...830L..37I | | 100 K | Gaussian fit | | LTE justified by n ~ 5e8 cm^-3 |
| 2019ApJ...882..118X | Turner 1991 thermalized spectra | | | negligible beam dilution | Tbg 11.5, 27.4, 33.9, 43.1 K by band |
| 2017A&A...598A..53D | Gaussian sum per hyperfine component | | FWHM grid 0.5-25 km/s, step 0.5 | | same FWHM for all HFS components |
| 2014Sci...345.1584B | Weeds | free | free | free | 5 parameters incl. velocity offset |
