# Multiple molecular outflows and fragmentation in the IRDC core G34.43+00.24 MM1

`2021A&A...649A.139I` | Astronomy and Astrophysics 2021 | first author: Isequilla, N. L. | arXiv: 2103.04965 | DOI: 10.1051/0004-6361/202039974

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: Is the hot molecular core G34–MM1 fragmented, and which sources drive its molecular outflows?  
  > "we present a kinematic and morphological study of the hot molecular core G34–MM1 in order to characterize in detail its internal structure." (1 Introduction)
- Target **G34–MM1 (IRDC G34.43+00.24)**: coordinates HCO+ condensation centred at RA = 18:53:18.0, DEC = +1:25:27.0  
  > "IRDC G34.43+00.24 (hereafter IRDC G34) is a filamentary infrared dark cloud located at a kinematic distance of about 3.6 kpc (cite: tang19)" (2 Presentation of the region); z/distance 3.6 kpc  
  > "IRDC G34.43+00.24 (hereafter IRDC G34) is a filamentary infrared dark cloud located at a kinematic distance of about 3.6 kpc (cite: tang19)" (2 Presentation of the region); distance from kinematic distance, Tang et al. 2019  
  > "IRDC G34.43+00.24 (hereafter IRDC G34) is a filamentary infrared dark cloud located at a kinematic distance of about 3.6 kpc (cite: tang19)" (2 Presentation of the region)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: Data cubes centred at 93 and 334 GHz  
  > "Data cubes with central frequencies at 93 and 334 GHz were obtained from the ALMA Science Archive" (3 Data)
- continuum bandwidth: _not stated_
- arrays: 12 m array  
  > "in the 12 m array in both cases" (3 Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.8x0.7 arcsec at 334 GHz; 2.1x1.4 arcsec at 93 GHz continuum  
  > "| Cont. 334 GHz | 0.8 $\times$ 0.7 | 15$\times$15 | \- | 10 |" (Table 1)
- max recoverable scale: 14.5 arcsec (93 GHz), 6.7 arcsec (334 GHz)  
  > "The maximum recoverable scales at 93 and 334 GHz are 14.5 and 6.7 arcsec, respectively." (3 Data)
- sensitivity: rms: 0.3 mJy/beam (93 GHz cont), 5.0 (HCO+), 10 (334 GHz cont), 15 (12CO)  
  > "| $^{12}$CO J=3–2 | 0.8 $\times$ 0.7 | 15$\times$15 | 0.9 | 15 |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival; PIs Rosero and Csengri  
  > "PIs: Rosero, V., and Csengri, T., respectively" (3 Data)
- Line: HCO+ J=1–0 (not stated)
- Line: 12CO J=3–2 (not stated)
- Other facility **Spitzer / ATLASGAL**: Context image and 870 um contours (Fig. 1)  
  > "The green contours represent the continuum emission at 870 $\mu$m obtained from ATLASGAL." (2 Presentation of the region)
- External data: Radio continuum flux densities at 4.9 and 25.5 GHz, spectral index +0.7  
  > "estimated a total flux density of about 0.4 and 1.5 mJy at 4.9 GHz ($\lambda \sim$ 6 cm) and 25.5 GHz ($\lambda \sim$ 1.3 cm), respectively, with a spectral index of $+$0.7" (4.1) [from Rosero et al. 2016 (cite: rosero16)]
- External data: Flux densities 56.8 mJy at 3 mm and 0.7 mJy at 6 cm  
  > "estimated a total flux density of 56.8 and 0.7 mJy at 3 mm and 6 cm, respectively" (4.1) [from Shepherd et al. 2004 (cite: shepherd04)]

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.8x0.7 arcsec at 334 GHz; 1.9x1.4 arcsec HCO+  
  > "| Cont. 334 GHz | 0.8 $\times$ 0.7 | 15$\times$15 | \- | 10 |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- CO-to-H2 conversion N(H2)=2.0e20 W(12CO)  
  > "following (cite: bertsch93), we calculate the H$_2$ column density from:" (4.3.1) [from (cite: bertsch93)]

### Not stated but needed to reproduce (our reading)

- Whether archive-delivered calibrated products or re-calibration were used
- Imaging parameters (weighting, robust, cleaning, masks)
- Continuum subtraction and line-free channels
- Rest frequencies and the velocity range used for 12CO outflow integration beyond quoted limits
- Noise thresholds for outflow masks
- How 12CO J=1-0 conversion applied to J=3-2 (line ratio)

## Analysis recipe

1. **Continuum imaging and ionized-gas contribution**: Inspect continuum at 93 and 334 GHz; estimate free-free contribution within one beam using Rosero et al. spectral index  
  > "we estimated a flux density (related to the emission of the ionized gas) of about 3 mJy for both frequencies." (4.1)
   - software: CASA
   - assumption: Turnover frequency of 100 GHz  
  > "Assuming that the turn over frequency of the radio continuum emission for these young HII regions can reach the 100 GHz" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify outflows and subcores from line cubes**: Integrated maps of HCO+ and 12CO in velocity intervals  
  > "a three-colour image of the HCO$^+$ J=1–0 integrated over three velocity intervals: \[43, 53\], \[53, 63\], and \[63, 73\] km s$^{-1}$" (4.2)
   - software: CASA
   - fitting: _not stated_
   - validation: Peak position shifts of subcores checked across velocity ranges  
  > "the position of the peaks of SC2 and SC3 does not shift, in more than a beam, throughout their velocity range" (5 Discussion)
3. **Outflow mass, momentum, energy**: N(H2) from W(12CO), Jy/beam to K conversion, sum over lobe beams  
  > "Summation was performed over all beam positions belonging to the lobes shown in Fig. [8]" (4.3.1)
   - assumption: mu=2.8, 25% helium; distance 3.6 kpc  
  > "assumed to be 2.8 by taking into account a relative helium abundance of 25 %" (4.3.1)
   - fitting: _not stated_
   - validation: Compared with ALMA outflow studies  
  > "A comparison of our results with those presented in recent works carried out with ALMA" (5 Discussion)

## Software

- **CASA** 5.4.1: handle and analyse data  
  > "The Common Astronomy Software Applications (CASA) 5.4.1 was used to handle and analyse the data." (3 Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MM1–E outflow blue lobe mass | 4.1 | not stated | Msun | 3 | /             Mass (${\rm M_{\odot}}$)             /   0.8    /    4.1    / |
| MM1–E outflow red lobe mass | 0.8 | not stated | Msun | 3 | /             Mass (${\rm M_{\odot}}$)             /   0.8    /    4.1    / |
| Dynamical age red/blue lobe | 1.6 / 1.7 | not stated | 10^3 yr | 3 | /            Dynamical age (10$^3$ yrs)            /   1.6    /    1.7    / |
| Ionized gas flux at 93 and 334 GHz | about 3 mJy | not stated | mJy | 1 | we estimated a flux density (related to the emission of the ionized gas) of about 3 mJy for both frequencies. |
| Subcore average size / separation | 0.02 / 0.03 | not stated | pc | 2 | The average size of these subcores is about 0.02 pc and the average spatial separation among them is about 0.03 pc. |

## Qualitative findings

- Two perpendicular outflows arise from MM1–A in HCO+  
  > "clearly indicates the presence of two perpendicular outflows arising from MM1–A" (4.2)

## Claim tuples

- H: G34–MM1 is fragmented | E: 93 and 334 GHz continuum and 12CO J=3–2 maps | R: MM1–A to E condensations and subcores SC1–SC4 | F: Fragmentation at two spatial scales | **supported**
- H: MM1–E drives an outflow | E: 12CO J=3–2 integrated over -10 to +50 and +65 to +105 km/s | R: Filaments OF1 and OF2; M~5 Msun, E~6e46 erg | F: Young massive energetic outflow | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: OF1/OF2 could be filaments converging onto MM1–E rather than outflows  
  > "we can not discard the possibility that gaseous structures OF1 and OF2, indeed correspond to filaments of molecular gas converging to MM1–E" (4.3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): MM1–E only marginally detected at 334 GHz  
  > "this dust condensation is marginally detected at 334 GHz" (4.3.1)
- Caveat (inferred, ours): Outflow masses use a Galactic CO-to-H2 factor for 12CO J=3-2 with no opacity or excitation correction
- Caveat (inferred, ours): Optically thick, self-absorbed 12CO and missing flux from limited recoverable scale
- Caveat (inferred, ours): Subcores identified by eye in a single velocity range
- Caveat (inferred, ours): Competitive accretion conclusion weakly constrained

## Reproducibility

- Data public (paper): Data from ALMA Science Archive  
  > "were obtained from the ALMA Science Archive" (3 Data)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Velocity ranges and masks for subcore identification
- Missing: Line-ratio treatment
- Data volume (inferred): ~20-50 GB
- Score (inferred): 4/5, Public data and simple formulae, but imaging and calibration details are absent.
- Rediscovery candidate: no, Imaging recipe incomplete and results largely morphological.

## Links

- Method: Bertsch et al. 1993 (cite: bertsch93) (CO-to-H2 conversion)
- Companion: Shepherd et al. 2007 (cite: shepherd07) (Earlier detection of two perpendicular outflows)
- Companion: Rosero et al. 2016 (cite: rosero16) (Radio continuum data)
- Related: ATLASGAL

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00960.S",
  "2015.1.00369.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 27,
  "rate": 0.435
 },
 "evidence_ok": true
}
```
