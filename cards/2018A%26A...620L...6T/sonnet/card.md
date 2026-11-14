# Chemical segregation of complex organic O-bearing species in Orion KL

`2018A&A...620L...6T` | Astronomy and Astrophysics 2018 | first author: Tercero, B. | arXiv: 1811.08765 | DOI: 10.1051/0004-6361/201834417

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: How are complex O-bearing organic molecules spatially distributed among Orion KL components (compact ridge vs hot core south), and what does this imply for their chemistry?  
  > "The identification of several O-bearing COMs in Orion KL allows us to investigate the spatial distribution of similar species" (Introduction)
- Target **Orion KL (IRc2 region)**: coordinates RA 05h35m14.35s, Dec -05d22m35.00s (J2000), phase centre  
  > "The observations were centred on $\upalpha_{\rm J2000}$ = 05$^{\rm h}$ 35$^{\rm m}$ 14.35$^{\rm s}$, $\updelta_{\rm J2000}$ = $-$05$^{\circ}$ 22$'$ 35.00$''$." (Observations); "Orion BN/KL (Becklin-Neugebauer / Kleinmann-Low) is the closest high-mass star-forming region ($\sim$ 400 pc;" (Introduction); z/distance ~400 pc  
  > "The observations were centred on $\upalpha_{\rm J2000}$ = 05$^{\rm h}$ 35$^{\rm m}$ 14.35$^{\rm s}$, $\updelta_{\rm J2000}$ = $-$05$^{\circ}$ 22$'$ 35.00$''$." (Observations); "Orion BN/KL (Becklin-Neugebauer / Kleinmann-Low) is the closest high-mass star-forming region ($\sim$ 400 pc;" (Introduction); distance from Grossschedl_2018; Kounkel_2017; Menten_2007  
  > "The observations were centred on $\upalpha_{\rm J2000}$ = 05$^{\rm h}$ 35$^{\rm m}$ 14.35$^{\rm s}$, $\updelta_{\rm J2000}$ = $-$05$^{\circ}$ 22$'$ 35.00$''$." (Observations); "Orion BN/KL (Becklin-Neugebauer / Kleinmann-Low) is the closest high-mass star-forming region ($\sim$ 400 pc;" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: Band 6  
  > "in the frequency range from 213.715 GHz to 246.627 GHz (Band 6)" (Observations)
- frequencies and spectral setup: 213.715-246.627 GHz; resolution 0.488 MHz (~0.64 km/s)  
  > "Spectral resolution was 0.488 MHz ($\sim$ 0.64 km s$^{-1}$ in the observed frequency range)." (Observations)
- continuum bandwidth: _not stated_
- arrays: 16 antennas of 12 m  
  > "The observations were carried out with 16 antennas of 12 m" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.00"x1.48" (PA 176) at 214.0 GHz to 1.75"x1.29" (PA 164) at 246.4 GHz  
  > "The synthesised beam ranged from 2.00$''$ $\times$ 1.48$''$ with a position angle (PA) of 176$^{\circ}$ at 214.0 GHz" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: January 2012  
  > "were taken in January 2012 towards the IRc2 region in Orion" (Observations)
- pi or archival as stated: ALMA Science Verification data  
  > "The ALMA Science Verification (SV) data[^2] were taken in January 2012" (Observations)
- Line: 13CH3OH 8(4,4)-9(3,7) A; 5(-2,4)-4(-2,3) E (215722.475; 236062.000 MHz)
- Line: HCOOCH3 10(4,6)-9(3,7) A; 27(-9,18)-27(-8,19) E (221717.125; 222367.071 MHz)
- Line: CH3OCH3 14(1,13)-13(2,12); 24(4,21)-24(3,22) (226346-226348; 225202-225205 MHz)
- Line: OHCH2CH2OH 23(9,15)-22(9,14) ag; 23(2,22)-22(2,21) ag (242947.990; 228752.776 MHz)
- Line: CH3OCH2OH 22(10,12)-21(10,11); 23(4,19)-22(4,18) (229025.777; 246243.055 MHz)
- External data: N(H2) = 8.2e23, 2.4e24, 1.8e24 cm-2 at HKKH 11 (MF), HKKH 8 (EG), HKKH 9 (ET), from SED fitting with Td=100 K  
  > "We adopted the $N$(H$_2$) values of 8.2 $\times$ 10$^{23}$, 2.4 $\times$ 10$^{24}$, and 1.8 $\times$ 10$^{24}$ cm$^{-2}$ derived by (cite: Hirota_2015)" (Results) [from (cite: Hirota_2015)]
- External data: Continuum source positions HKKH 8, 9, 11 at 245 and 339 GHz  
  > "coincide with three continuum sources found by (cite: Hirota_2015) at 245 GHz and 339 GHz" (Results) [from (cite: Hirota_2015)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Maps cleaned in GILDAS with HOGBOM algorithm  
  > "The line maps were cleaned using the HOGBOM algorithm (cite: Hogbom_1974)." (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Subtracted in maps by selecting line-free channels  
  > "The continuum emission was subtracted in the maps by carefully selecting line-free channels." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.00"x1.48" to 1.75"x1.29"  
  > "to 1.75$''$ $\times$ 1.29$''$ with a PA of 164$^{\circ}$ at 246.4 GHz" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Fixed Trot = 150 K based on previous works  
  > "we relied on previous works (see e.g. (cite: Tercero_2015; Cernicharo_2016)) to fix the rotational temperature at 150 K" (Determination of column densities) [from (cite: Tercero_2015; Cernicharo_2016)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction
- Weighting/robust, cell and image size, clean threshold and masks
- Calibration details and CASA version (archival SV products)
- Line widths and radial velocities adopted per component in MADEX models (in a table not reproduced)
- Integration velocity intervals for maps
- Final rms of maps
- Final column density values and abundances (in table/figure not in text)

## Analysis recipe

1. **Make integrated line maps**: Two unblended transitions per species integrated and overlaid (colour and contours); HOGBOM cleaning in GILDAS  
  > "we selected two transitions of each of these species that arise free of blending with other species in the Orion KL cores" (Results)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Coincidence of emission peaks between the two lines  
  > "We note the coincidence in the emission peaks between colour and contour scales for most of the species" (Results)
2. **Derive column densities at MF, EG, ET peaks**: Averaged spectrum over 5x5 pixels (1"x1") fitted with MADEX LTE synthetic spectra, varying column density  
  > "we extracted an averaged spectrum over 5 $\times$ 5 pixels (1$''$$\times$1$''$) around the emission peaks" (Determination of column densities)
   - software: MADEX
   - parameter: Trot fixed 150 K; extra components at 250 K and 50 K when needed  
  > "we introduced a hotter (at 250 K) and/or colder (at 50 K) component to properly fit all unblended lines" (Determination of column densities)
   - assumption: LTE; source size 3"; uniform line width and velocity  
  > "Owing to the lack of collisional rates for most of the studied species, we used the local thermodynamic equilibrium (LTE) approximation." (Determination of column densities)
   - fitting: Manual adjustment of column density to agree with line intensities within ~30%; upper limit if fewer than five unblended lines  
  > "We marked as the upper limit the column density results obtained with less than five unblended lines." (Determination of column densities)
   - validation: Mismatched lines checked for blends  
  > "Lines for which this condition was not fulfilled were revised searching for possible blendings with features from other molecular species." (Determination of column densities)
3. **Compute molecular abundances**: Column densities divided by adopted N(H2) at each peak  
  > "Molecular abundances for each species in the different positions were calculated using the derived column densities" (Results)
   - assumption: N(H2) from Hirota et al. 2015 with dust temperature 100 K  
  > "using a dust temperature of 100 K and a modified blackbody fitting of the spectral energy distribution (SED)" (Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Initial processing  
  > "The CASA software[^3] was used for initial processing" (Observations)
- **GILDAS** : Further analysis, imaging  
  > "then the visibilities were exported to the GILDAS package[^4] for further analysis" (Observations)
- **MADEX** : LTE radiative transfer modelling for column densities  
  > "We used the MADEX[^5] radiative transfer code (cite: Cernicharo_2012) to derive physical parameters and column densities" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Separation of EG and ET emission peaks in hot core south | ~1.6 | not stated | arcsec | 1 | We distinguished two locations separated by about $\sim$1.6$''$ for the main emission peaks in the hot core south |

## Qualitative findings

- Species A-G (ether-bearing C-O-C) peak at the compact ridge; H-N (C-O-H bearing) lack compact ridge emission and peak in hot core south  
  > "the molecules on the left (panels A–G) present the bulk of the emission at the position of the compact ridge (crosses)" (Results)
- First detection of methoxymethanol in Orion  
  > "We have detected methoxymethanol for the first time in Orion" (Results)

## Claim tuples

- H: O-bearing COMs are chemically segregated by functional group | E: Mapped two transitions of 14 species in ALMA SV data and derived abundances at three peaks | R: C-O-C species peak at compact ridge, C-O-H species at hot core south; abundances follow same trend | F: Segregation reflects different precursor radicals (CH3O vs CH2OH) and chemistry/shock history | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No short-spacing data, so extended emission is incomplete  
  > "Despite the lack of short spacing data required for completion of the possible extended emission of some of these species" (Results)
- Caveat (inferred, ours): LTE with fixed Trot=150 K and manual intensity matching, no formal uncertainties
- Caveat (inferred, ours): Abundances rely on N(H2) from another paper at different resolution
- Caveat (inferred, ours): Mechanistic interpretations are speculative

## Reproducibility

- Data public (paper): ALMA SV data publicly available at the cited web page  
  > "http://almascience.eso.org/almadata/sciver/OrionKLBand6/" (footnote 2)
- Products in archive: _not stated_
- Missing: Column density table values
- Missing: Imaging parameters
- Missing: MADEX is a collaboration code with line parameters not given
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and clear approach, but imaging parameters and fitted values are not in the text and fitting is manual.
- Rediscovery candidate: no, Key numeric results (column densities) not given in text and the fitting is by eye with specialised code.

## Links

- Method: (cite: Cernicharo_2012) (MADEX code)
- Companion: (cite: Cernicharo_2016) (Previous detections and parameters for COMs in Orion KL)
- Companion: (cite: Hirota_2015) (Continuum sources and N(H2))
- Related: ALMA Science Verification Orion KL Band 6

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 1,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 32,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
