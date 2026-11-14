# Searching for trans ethyl methyl ether in Orion KL⋆

`2015A&A...582L...1T` | Astronomy and Astrophysics 2015 | first author: Tercero, B. | arXiv: 1509.00179 | DOI: 10.1051/0004-6361/201526255

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Is trans ethyl methyl ether (tEME), and the isomer gauche-trans n-propanol, present in Orion KL, and how are related saturated O-bearing species distributed?  
  > "In this Letter, we report on the tentative detection of tEME towards the compact ridge (CR) of Orion KL." (Introduction)
- Target **Orion KL (IRc2 / compact ridge)**: coordinates ALMA centre 05h35m14.35s, -05d22m35.00s (J2000)  
  > "The observations were centred on coordinates: $\alpha$$_{J2000}$ = 05$^h$35$^m$14$\mbox{\rlap{.}$^s$}$35, $\delta$$_{J2000}$ = $-$05$^{\circ}$22$'$35$\mbox{\rlap{.}$''$}$00." (Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: Band 6 (213.715-246.627 GHz)  
  > "The observations were carried out with 16 antennas of 12 m in Band 6 (213.715-246.627 GHz)." (Observations)
- frequencies and spectral setup: Spectral resolution 0.488 MHz (0.64 km/s)  
  > "Spectral resolution was 0.488 MHz corresponding to a velocity resolution of 0.64 km s$^{-1}$." (Observations)
- continuum bandwidth: _not stated_
- arrays: 16 antennas of 12 m  
  > "The observations were carried out with 16 antennas of 12 m in Band 6 (213.715-246.627 GHz)." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.00x1.48 arcsec (PA 176) at 214.0 GHz to 1.75x1.29 arcsec (PA 164) at 246.4 GHz  
  > "The synthesized beam ranged from 2$\mbox{\rlap{.}$''$}$00$\times$1$\mbox{\rlap{.}$''$}$48 with a PA of 176$^{\circ}$ at 214.0 GHz" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: January 2012  
  > "The ALMA Science Verification (SV) data[^4] were taken in January 2012 towards the IRc2 region in Orion." (Observations)
- pi or archival as stated: ALMA Science Verification data  
  > "The ALMA Science Verification (SV) data[^4] were taken in January 2012 towards the IRc2 region in Orion." (Observations)
- Line: trans ethyl methyl ether (tEME) b-type transitions, Eup up to 300 K, Sij>=1 (not stated)
- Line: Gt-n-propanol lines at 236.138 and 244.765 GHz used for map (236.138 and 244.765 GHz)
- Other facility **IRAM 30m**: 3, 2, 1 mm line survey of Orion KL (new data Aug 2013, Mar 2014)  
  > "New data of the IRAM 30m telescope, which complement and improve those of (cite: Tercero2010), were collected in August 2013 and March 2014 towards Orion KL" (Observations)
- External data: tEME frequency predictions  
  > "Frequency predictions from (cite: Fuchs2003) and dipole moments" (3.1 Search for trans Ethyl Methyl Ether) [from Fuchs2003]
- External data: tEME dipole moments  
  > "measured by (cite: Hayashi1975) of tEME were implemented in MADEX" (3.1 Search for trans Ethyl Methyl Ether) [from Hayashi1975]
- External data: Gt-n-propanol line frequencies  
  > "All lines of Gt-CH$_3$CH$_2$CH$_2$OH, an isomer of C$_3$H$_8$O (as well as tEME), reported by (cite: Maeda2006)" (3.2 Search for gauche-trans-n-propanol) [from Maeda2006]
- External data: Gt-n-propanol dipole moments  
  > "from (cite: Abdurakhmanov1969) were used to derive its rotational constants" (3.2 Search for gauche-trans-n-propanol) [from Abdurakhmanov1969]
- External data: 12C/13C = 45  
  > "$^{12}$C/$^{13}$C = 45 (cite: Tercero2010)" (Table 1) [from Tercero2010]

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

- task: Line maps cleaned with HOGBOM algorithm after visibilities exported to GILDAS  
  > "The line maps were cleaned using the HOGBOM algorithm (cite: Hogbom1974)." (Observations)
- deconvolver: Hogbom  
  > "The line maps were cleaned using the HOGBOM algorithm (cite: Hogbom1974)." (Observations)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- IRAM 30m survey data and previous data set  
  > "see (cite: Tercero2010) and (cite: Lopez2014), for information about the previous data set" (Observations) [from Tercero2010; Lopez2014]
- Comparison maps of MF, DME, methanol, ethanol from SMA+IRAM 30m  
  > "the following discussion is also based on the maps shown in Fig. 5 of Feng et al. (2015; maps performed mixing SMA and IRAM 30m data)" (4 Discussion) [from Feng2015]

### Not stated but needed to reproduce (our reading)

- Calibration steps/CASA version and calibrators for SV data (archive SV products presumably used)
- Weighting/robust, cell and image size, clean threshold/masks
- Continuum subtraction and line-free channels
- Image rms/noise levels
- MADEX model details (not public in paper) and how column densities fitted by eye
- Exact velocity ranges and channels for tEME map
- Column density derivation for DME, MF, methanol, ethanol (from other works)

## Analysis recipe

1. **Process ALMA SV data and image**: CASA initial processing, visibilities exported to GILDAS, line maps cleaned with Hogbom  
  > "The CASA software[^5] was used for initial processing and then the visibilities were exported to the GILDAS package." (Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and model tEME emission**: Average spectrum over 5x5 pixels around the DME emission peak (Position A); model with MADEX under LTE  
  > "we extracted the averaged spectrum over 5$\times$5 pixels (1$''$$\times$1$''$) around the CH$_3$OCH$_3$ emission peak of the CR component (Position A" (3.1 Search for trans Ethyl Methyl Ether)
   - software: MADEX
   - parameter: source size 3", vLSR +7.5 km/s, dv 2.0 km/s, TK 100±20 K  
  > "The assumed parameters are a source size of 3$''$, $v$$_{LSR}$ = +7.5 km s$^{-1}$, $\Delta$$v$ = 2.0 km s$^{-1}$, and $T_K$ = 100$\pm$20 K." (3.1 Search for trans Ethyl Methyl Ether)
   - assumption: LTE  
  > "Using MADEX and assuming local thermodynamic equilibrium (LTE), we obtain $N_{g.s.}$(tEME) $\leq$ (4.0$\pm$0.8)$\times$10$^{15}$ cm$^{-2}$." (3.1 Search for trans Ethyl Methyl Ether)
   - fitting: Fit by eye of all available lines  
  > "we obtained them by fitting all available lines by eye" (3.1 Search for trans Ethyl Methyl Ether)
   - validation: Count of unblended lines and comparison with IRAM 30m model  
  > "At least 46 lines (45% of the detectable lines) shown in Fig. [3](#fig_alma_todo) are free of blending" (3.1 Search for trans Ethyl Methyl Ether)
3. **Model tEME and Gt-n-propanol in IRAM 30m data and Gt-n-propanol in ALMA**: MADEX LTE synthetic spectra compared with data at survey and Positions A/B  
  > "We conducted the search for Gt-n-propanol in the ALMA SV data at two different positions" (3.2 Search for gauche-trans-n-propanol)
   - software: MADEX
   - fitting: _not stated_
   - validation: _not stated_
4. **Map species distributions and compare**: Averaged line emission maps (e.g. 6-9 km/s for propanol) and compared with other species and Feng et al. maps; derive column densities and ratios  
  > "To perform the ALMA map, we averaged the emission between $v$$_{LSR}$ 6 and 9 km s$^{-1}$ of two lines" (3.2 Search for gauche-trans-n-propanol)
   - fitting: _not stated_
   - validation: Comparison with SMA+30m maps  
  > "For MF, DME, and methanol the spatial distribution and the position of the emission peaks are in agreement with those of the maps presented in this work" (4 Discussion)

## Software

- **CASA** : initial processing of ALMA SV data  
  > "The CASA software[^5] was used for initial processing" (Observations)
- **GILDAS** : IRAM 30m reduction and ALMA imaging  
  > "The data were reduced using the GILDAS package[^3]." (Observations)
- **MADEX** : LTE modelling of line emission  
  > "implemented in MADEX (cite: Cernicharo2012) to model the emission of this species" (3.1 Search for trans Ethyl Methyl Ether)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(tEME) ALMA, Position A | <=4.0e15 | ±0.8e15 | cm^-2 | 2 | we obtain $N_{g.s.}$(tEME) $\leq$ (4.0$\pm$0.8)$\times$10$^{15}$ cm$^{-2}$ |
| N(tEME) IRAM 30m | 9e15 | ±3e15 | cm^-2 | 3 | a column density of (9$\pm$3)$\times$10$^{15}$ cm$^{-2}$ for the ground state (g.s.) of tEME |
| N(Gt-n-propanol) ALMA Position B | <=1.0e15 | ±0.2e15 | cm^-2 | 3 | $N_{g.s}$ $\leq$ (1.0$\pm$0.2$)\times$10$^{15}$ cm$^{-2}$ |
| DME/tEME | >=150 | not stated | dimensionless | 4 | DME/tEME $\geq$ 150 |
| MetOH/EtOH | ~45 | not stated | dimensionless | 4 | MetOH/EtOH $\simeq$ 45 |

## Qualitative findings

- tEME emission arises mainly from the compact ridge (like ethyl formate); Gt-n-propanol peaks at the ethanol position in the south hot core.  
  > "Whereas tEME seems to mainly arises from the CR component (as well as EF) \[Position A\], emission from Gt-n-propanol could be located at the south hot core" (4 Discussion)

## Claim tuples

- H: tEME is present in Orion KL compact ridge | E: LTE modelling of ALMA SV and IRAM 30m spectra | R: 46 unblended lines at expected velocity; N<=4e15 cm-2 | F: Tentative detection of tEME | **partially**
- H: Unidentified lines belong to Gt-n-propanol | E: MADEX model at Position B in ALMA and 30m | R: Strongest features detected; N<=1e15 cm-2 | F: Lines assigned to Gt-n-propanol | **supported**

## Reasoning

- Why this data: ALMA drastically reduces confusion limit relative to single dish  
  > "The advantage of ALMA with respect to single dish telescope data (see below) is the drastic reduction of the confusion limit." (3.1 Search for trans Ethyl Methyl Ether)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Detection of tEME is tentative; many lines blended  
  > "further analysis exploring new available ALMA data and modelling all the molecular content of the CR is needed" (3.1 Search for trans Ethyl Methyl Ether)
- Caveat (inferred, ours): Fit by eye with no formal uncertainty or significance
- Caveat (inferred, ours): Upper limits and detection claims conflict (N given as <=)
- Caveat (inferred, ours): No full-molecular-content model of blends
- Caveat (inferred, ours): Flux filtering by ALMA not quantified

## Reproducibility

- Data public (paper): ALMA SV data publicly available at almascience URL  
  > "http://almascience.eso.org/almadata/sciver/OrionKLBand6/" (footnote 4)
- Products in archive: _not stated_
- Missing: MADEX line catalog/model files
- Missing: Imaging parameters
- Missing: Position A/B coordinates
- Data volume (inferred): ~tens of GB (SV Band 6 spectral scan)
- Score (inferred): 3/5, Public data, but sparse processing and by-eye modelling with unavailable code.
- Rediscovery candidate: no, Recipe incomplete and by-eye fits.

## Links

- Method: Cernicharo2012 (MADEX code)
- Companion: Tercero2010 (IRAM 30m Orion KL survey)
- Companion: Carroll2015 (tEME upper limits in other hot cores)
- Related: ALMA Science Verification Orion KL Band 6

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 34,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
