# Measuring the <SUP>34</SUP>S and <SUP>33</SUP>S Isotopic Ratios of Volatile Sulfur during Planet Formation

`2024ApJ...975...72B` | The Astrophysical Journal 2024 | first author: Booth, Alice S. | arXiv: 2409.03885 | DOI: 10.3847/1538-4357/ad7817

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the combined 34S and 33S isotope ratios of SO (and the 18O limit) in the Oph-IRS 48 planet-forming disk, and are they consistent with solar system values?  
  > "Using ALMA observations of the SO and isotopologues in the nearby, molecule-rich disk around the young star Oph-IRS 48 we present the first constraints on the combined / and / isotope ratios in a planet-forming disk." (abstract); "Together these observations show that we should not assume solar isotopic values for disk sulfur reservoirs" (abstract)
- Target **Oph-IRS 48**: coordinates _not stated_; z/distance 135 pc  
  > "Oph-IRS 48 is a nearby (135 pc), young Herbig Ae star" (Introduction); distance from cited alongside Brown et al. 2012 and Gaia Collaboration 2018 (Gaia2018)  
  > "Oph-IRS 48 is a nearby (135 pc), young Herbig Ae star" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00834.S, 2021.1.00738.S
- bands: _not stated_
- frequencies and spectral setup: Lines of SO and isotopologues spanning about 337.2 to 362.2 GHz (Table 1); 0.9 mm continuum also shown  
  > "337.1986199" (Table 1); "362.1582327" (Table 1); "the integrated intensity maps of sulfur isotopologues in the Oph IRS 48 disk and the 0.9 mm continuum emission" (Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: about 0.45 arcsec beam (2017.1.00834.S data); about 0.3 arcsec beam (2021.1.00738.S data)  
  > "and a Briggs robust weighting of 0.5 resulting in a $\approx$0.45$\ensuremath{''}$ beam" (Methods); "with a Briggs robust weighting of 0.5 resulting in a $\approx$0.3$\ensuremath{''}$ beam" (Methods)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Programs 2017.1.00834.S (PI Adriana Pohl) and 2021.1.00738.S (PI Alice S. Booth); data first presented in earlier papers  
  > "from the programs 2017.1.00834.S (PI: Adriana Pohl) and 2021.1.00738.S (PI: Alice S. Booth)" (Methods); "The former were first presented in" (Methods)
- Line: SO J=3_3-3_2 (optically thinnest detected transition, used for the SO column density) (not stated)
- Line: SO isotopologues (species names missing in the converted text) see Table 1; two lines each for the isotopologues used, one line tentatively detected in one channel (not stated)
- Other facility **Cologne Database for Molecular Spectroscopy (CDMS)**: Line properties and partition functions of each isotopologue  
  > "The various line properties and partition functions of each isotopologue are taken from the Cologne Database for Molecular Spectroscopy" (Methods)
- External data: SO and isotopologue line properties and partition functions from CDMS  
  > "The various line properties and partition functions of each isotopologue are taken from the Cologne Database for Molecular Spectroscopy" (Methods) [from CDMS: (cite: 2001A&A...370L..49M; 2005JMoSt.742..215M; 2016JMoSp.327...95E) with data from (cite: 1985JPCRD..14..395L; 1992ApJ...399..325L; 1996JMoSp.180..197K)]
- External data: V-CDT standard isotope ratios (22.64, 126.9, 498.7) used for the delta values  
  > "The standard ratios used are 22.64 for /, 126.9 for / and 498.7 for /" (Methods) [from (cite: 2001GeCoA..65.2433D; 2001RCMS...15..501W)]
- External data: Local ISM ratio of 550 for one of the ratios  
  > "These differ slightly from the local ISM ratios, where in particular, / is 550" (Methods) [from (cite: 1994ARA&A..32..191W)]
- External data: Rotational temperature of about 60 K at the emission peak, from a rotation diagram of a companion molecule (species name missing in text); adopted as the fiducial temperature  
  > "find that the rotational temperature for to be very well constrained to $\approx$60 K at the emission peak." (Methods) [from Temmink et al. 2024 (in prep.)]
- External data: Detections and integrated intensity maps of SO and isotopologues  
  > "we use the integrated intensity maps from these works" (Methods) [from (cite: 2021A&A...651L...6B) and (cite: Booth2023_irs48)]

## Processing

### Calibration

- pipeline or manual: 2017.1.00834.S pipeline calibrated by Ohashi et al. 2020; 2021.1.00738.S self-calibrated (phase and amplitude)  
  > "The 2017.1.00834.S data were pipeline calibrated by" (Methods); "The 2021.1.00738.S data were self-calibrated (both phase and amplitude) and imaged with CASA task" (Methods)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: 2021.1.00738.S: phase and amplitude self-calibration (solints not stated)  
  > "The 2021.1.00738.S data were self-calibrated (both phase and amplitude) and imaged with CASA task" (Methods)

### Imaging

- task: CASA tclean  
  > "imaged these data with CASA task" (Methods); "The 2021.1.00738.S data were self-calibrated (both phase and amplitude) and imaged with CASA task" (Methods)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (both datasets)  
  > "and a Briggs robust weighting of 0.5 resulting in a" (Methods); "with a Briggs robust weighting of 0.5 resulting in a" (Methods)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian masks used for all integrated intensity maps  
  > "All integrated intensity maps were generated using Keplerian masks" (Methods)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: about 0.45 arcsec (2017.1.00834.S); about 0.3 arcsec (2021.1.00738.S); Table 1 gives per-line beams, e.g. 0.34 x 0.28 arcsec  
  > "and a Briggs robust weighting of 0.5 resulting in a $\approx$0.45$\ensuremath{''}$ beam" (Methods); "with a Briggs robust weighting of 0.5 resulting in a $\approx$0.3$\ensuremath{''}$ beam" (Methods)
- final rms: _not stated_

### Inherited from earlier work

- Data calibration, line identification and imaging steps are described in the earlier papers  
  > "In the above referenced works, the data calibration, line identification and imaging steps are described in full detail." (Methods) [from (cite: 2021A&A...651L...5V), (cite: 2021A&A...651L...6B), (cite: Booth2023_irs48)]
- 2017.1.00834.S pipeline calibration done by an earlier paper  
  > "The 2017.1.00834.S data were pipeline calibrated by" (Methods) [from (cite: 2020ApJ...900...81O)]
- 2017.1.00834.S imaging (velocity resolution 1.7 km/s, robust 0.5) done in an earlier paper  
  > "imaged these data with CASA task" (Methods) [from (cite: 2021A&A...651L...6B)]
- 2021.1.00738.S self-calibration and imaging (0.9 km/s, robust 0.5), cited to an earlier paper  
  > "The 2021.1.00738.S data were self-calibrated (both phase and amplitude) and imaged with CASA task" (Methods) [from (cite: 2021A&A...651L...5V); (cite: Booth2023_irs48)]
- The tentatively detected line was imaged in the same manner as the other lines from the 2021.1.00738.S data set  
  > "This line was imaged in the same manner as the other lines from" (Methods) [from (cite: Booth2023_irs48)]
- Integrated intensity maps of SO and isotopologues are taken from earlier papers  
  > "we use the integrated intensity maps from these works" (Methods) [from (cite: 2021A&A...651L...6B) and (cite: Booth2023_irs48)]
- Optically thin LTE column density method  
  > "Under the typical assumptions of optically thin line emission and local thermodynamic equilibrium" (Methods) [from (cite: 2018ApJ...859..131L)]

### Not stated but needed to reproduce (our reading)

- CASA version used for tclean
- Line-free channels, continuum subtraction method and cell/image sizes for the cubes
- Keplerian mask parameters (stellar mass, inclination, position angle, mask width) and how channels were summed into integrated intensity maps
- Self-calibration solution intervals and reference antennas for 2021.1.00738.S, and flux/bandpass/phase calibrators for both datasets
- Which molecule each row of Tables 1 and 2 belongs to (species names are missing in the paper text provided), and the exact peak-pixel positions used
- How the Jy/beam km/s peak intensity was converted to column density (beam dilution, filling factor, line profile treatment) and the formula used
- How asymmetric uncertainties on delta and the limits (>500, upper limit from the one-channel S/N 4 line) were propagated
- Per-line rms values used for the limit, and the channel range for the tentatively detected line

## Analysis recipe

1. **Obtain integrated intensity maps**: Use calibrated and imaged cubes from two ALMA programs; integrated intensity maps built with Keplerian masks; peak integrated flux taken from each map  
  > "All integrated intensity maps were generated using Keplerian masks" (Methods); "From these integrated intensity maps, we take the peak integrated flux and use this to calculate the molecular column density traced by each of the isotopologues." (Results)
   - software: CASA tclean, keplerian_mask
   - parameter: Briggs robust 0.5; velocity resolution 1.7 km/s (2017.1.00834.S) and 0.9 km/s (2021.1.00738.S)  
  > "at a velocity resolution of 1.7 km s" (Methods); "at a velocity resolution of 0.9 km s" (Methods)
   - parameter: Map errors are the rms of line-free regions of the images without Keplerian masking  
  > "where these errors are a measure of the root mean square noise (rms) of the line-free regions of the images without Keplerian masking." (Methods)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive peak column densities of SO and isotopologues vs excitation temperature**: Optically thin LTE column density from peak integrated intensity, using CDMS line data and partition functions  
  > "we estimate the peak column density traced by the SO and isotopologues detected in the Oph-IRS 48 disk." (Methods); "Under the typical assumptions of optically thin line emission and local thermodynamic equilibrium" (Methods)
   - software: CDMS
   - parameter: Excitation temperatures 30 to 150 K in steps of 10 K; fiducial 60 K  
  > "We calculate these column densities at a range of excitation temperatures (30 to 150 K in steps of 10 K)" (Methods); "When adopting our fiducial temperature of 60 K" (Results)
   - parameter: SO column density from the J=3_3-3_2 line only; two-line average for the other isotopologues  
  > "In this work, we only use the optically thinnest transition detected ($J=3_3-3_2$) as a measure of the SO column density." (Methods); "For and two lines of each are detected and we take the average column density traced by these lines at each temperature." (Methods)
   - parameter: Column density errors propagated from the integrated intensity map errors  
  > "The errors in the peak column densities are propagated from the errors in the integrated intensity maps" (Methods)
   - assumption: Optically thin emission and LTE  
  > "Under the typical assumptions of optically thin line emission and local thermodynamic equilibrium" (Methods)
   - assumption: SO traces the same warm gas as a companion molecule with rotational temperature about 60 K (no independent SO temperature)  
  > "we expect them to trace the same gas temperature." (Methods); "we cannot make an independent temperature measurement to confirm this" (Methods)
   - assumption: Temperature range 30-150 K bounded below by the midplane mm dust brightness temperature (minimum 30 K) and above by the optically thick CO isotopologue brightness temperature (>=100 K)  
  > "The lower limit of this range is informed by the brightness temperature of the midplane millimeter dust which is at a minimum of 30 K" (Methods)
   - fitting: _not stated_
   - validation: Peak column densities compared with averaged column densities over the whole emitting region; ratios agree within 1 sigma. SO J=3_3-3_2 optical depth about 0.1  
  > "find that the resulting isotope ratios, the key result of this paper, are within the quoted 1 $\sigma$ errors." (Results); "The SO $J=3_3-3_2$ transition is optically thin with $\tau \approx 0.1$" (Results)
3. **Compute isotope ratios and deviations from V-CDT**: Ratios of column densities at each temperature; delta values in per mille relative to V-CDT standard ratios  
  > "we also calculate the deviation of our ratios relative to the Vienna Canyon Diablo Troilite (V-CDT)." (Methods); "The standard ratios used are 22.64 for /, 126.9 for / and 498.7 for /" (Methods)
   - parameter: Tabulated at 30, 60 and 100 K and shown for the full temperature range  
  > "corresponding isotopic ratios, and deviations from V-CDT at 30, 60 and 100 K are listed in Table" (Results)
   - assumption: V-CDT chosen as the standard because it is the most common one for comets and meteorites; local ISM ratio of 550 differs slightly  
  > "This is the most common isotopic standard used in comet and meteorite studies." (Methods)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare disk isotope ratios with solar system and other disk values**: Compare ratios as a function of temperature with V-CDT, comets (67P/C-G), meteorite SiC grains and other disks  
  > "we show a comparison of the isotope ratios measured in comets to Class II disks for a variety of simple species." (Discussion); "The ratios we measure do vary as a function of the assumed gas temperature" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Imaging with the tclean task  
  > "The 2021.1.00738.S data were self-calibrated (both phase and amplitude) and imaged with CASA task" (Methods)
- **keplerian_mask** 1.0: Keplerian masks for integrated intensity maps  
  > "All integrated intensity maps were generated using Keplerian masks" (Methods)
- **Astropy, IPython, Jupyter, Matplotlib, NumPy** : Additional software packages, specific use not stated  
  > "This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Optical depth of SO J=3_3-3_2 | 0.1 (approx.) | not stated | dimensionless | 2 | The SO $J=3_3-3_2$ transition is optically thin with $\tau \approx 0.1$ |
| Isotope ratio traced in SO, Table 2 row 1 (V-CDT 22.64), 60 K | 34 | +/-4 | dimensionless | 3 | we find that traced in SO line emission, the Oph-IRS 48 disk is depleted in both and with /=$34\pm4$ and /=$290\pm60$. |
| Isotope ratio traced in SO, Table 2 row 1 (V-CDT 22.64), 30 K | 13 | +/-1 | dimensionless | 3 | $13\pm1$ |
| Isotope ratio traced in SO, Table 2 row 1 (V-CDT 22.64), 100 K | 50 | +/-6.0 | dimensionless | 3 | $50\pm6.0$ |
| Isotope ratio traced in SO, Table 2 row 3 (V-CDT 126.9), 60 K | 290 | +/-60 | dimensionless | 3 | we find that traced in SO line emission, the Oph-IRS 48 disk is depleted in both and with /=$34\pm4$ and /=$290\pm60$. |
| Isotope ratio traced in SO, Table 2 row 3 (V-CDT 126.9), 30 K | 120 | +/-25 | dimensionless | 3 | $120\pm25$ |
| Lower limit on the isotope ratio from SO, Table 2 row 4 (V-CDT 498.7), 60 K | >500 | not stated | dimensionless | 3 | The / lower limit from SO of $>$500 is consistent with the V-CDT value. |
| Isotope ratio in Table 2 row 2 (V-CDT 22.64), 60 K, enhanced | 5.2 | +/-0.6 | dimensionless | 3 | $5.2\pm0.6$; The apparent factor $\approx$4 enhancement of in is an extreme outlier in all cases, but this may be due to beam diluted and optically thick emission. |
| Peak column density, Table 2 row 1, 60 K (molecule name missing in text) | 3.6e15 | +/-0.3e15 | cm^-2 | 2 | 3.6$\pm0.3\times10^{15}$ |
| Delta value, Table 2 row 1, 60 K | -340 | +90/-70 | per mille | 3 | -340$^{+90}_{-70}$ |
| Delta value, Table 2 row 3, 60 K | -559 | +120/-80 | per mille | 3 | -559$^{+120}_{-80}$ |
| Delta value, Table 2 row 2, 60 K | 3350 | +250/-170 | per mille | 3 | 3350$^{+250}_{-170}$ |
| S/N of the tentatively detected line (one 0.9 km/s channel) | 4 | not stated | dimensionless | 1 | we tentatively detect this line in one velocity channel (0.9 km $\mathrm{s^{-1}}$) at a signal-to-noise ratio of 4. |

## Qualitative findings

- At temperatures below about 50 K the ratios in SO are consistent with V-CDT; at 60 K and above they are anomalous relative to V-CDT and cometary values  
  > "At temperatures of 60 K and above the isotope ratios for sulfur are anomalous when compared to the V-CDT and cometary values." (Discussion)
- The sulfur reservoir currently observed in the disk is primarily in the form of SO  
  > "The currently observed volatile sulfur reservoir in the Oph-IRS 48 disk is primarily in the form of SO." (Discussion)

## Claim tuples

- H: Is volatile sulfur in the Oph-IRS 48 disk isotopically solar? | E: LTE column densities of SO and isotopologues from peak integrated intensity at 30-150 K, ratios compared with V-CDT | R: At 60 K two of the ratios are 34+/-4 and 290+/-60 against V-CDT values of 22.64 and 126.9 | F: Assuming warm (60 K or above) gas, SO is depleted in heavy sulfur isotopes relative to solar system values | **supported**
- H: Do the SO ratios depend on the assumed gas temperature? | E: Column densities computed for 30 to 150 K in 10 K steps | R: Ratios increase with temperature and match V-CDT below about 50 K | F: Cool gas would make the ratios consistent with comets and solar system bodies, so an independent SO temperature is needed | **supported**
- H: Can the oxygen isotope ratio of SO be constrained and is it solar? | E: Tentative one-channel detection of the rarer isotopologue treated as an upper limit on its abundance | R: Lower limit on the ratio >500 at 60 K, consistent with V-CDT 498.7 | F: No sign of oxygen isotope fractionation for warm gas | **partially**
- H: Is the heavier isotopologue of a second sulfur molecule enhanced? | E: Ratio from the second molecule's lines (species name missing in text) | R: Ratio of 5.2+/-0.6 at 60 K against a standard of 22.64 | F: Tentative enhancement that requires optically thinner transitions to confirm | **partially**

## Reasoning

- Why this data: Oph-IRS 48 has the most observed volatile sulfur, so is the most promising disk for sulfur isotope ratios  
  > "The disk with the most observed volatile sulfur, and therefore the source with the most promise for measuring isotopic ratios of sulfur, is the Oph-IRS 48 disk." (Introduction)
- Why this method: Temperature range chosen from dust brightness temperature, CO isotopologue brightness temperature and rotational temperatures of other molecules; fiducial 60 K from a companion molecule  
  > "The lower limit of this range is informed by the brightness temperature of the midplane millimeter dust which is at a minimum of 30 K" (Methods); "we explore a range of higher and lower gas temperatures to see how sensitive the inferred isotopic ratios is to this assumption." (Methods)
- Alternative: A cooler gas reservoir cannot be ruled out; it would bring the SO sulfur ratios in line with comets and other solar system bodies  
  > "However, we cannot completely rule out a cooler gas reservoir, which would put the SO sulfur ratios more in line with comets and other solar system bodies." (abstract)
- Alternative: Optical depth of SO J=3_3-3_2 rejected as the cause of the anomalous ratios  
  > "optical depth cannot explain the anomalous" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): No independent SO temperature; only three SO lines and two are too optically thick for a rotation diagram  
  > "we cannot make an independent temperature measurement to confirm this" (Methods); "do not allow for a rotation diagram analysis" (Methods)
- Limitation (authors): The 18O-bearing line is only tentatively detected in one channel, so only an abundance upper limit is derived  
  > "A robust detection would require 3$\sigma$ emission over $>$3 channels to confirm." (Methods)
- Limitation (authors): Dust optical depth may hide gas below the dust surface and bias column densities low  
  > "There are also possible limitations in the current data due to dust optical depth that will require longer wavelength observations to assess." (Conclusion)
- Limitation (authors): Ratios depend on assumed binding energies and the adopted gas temperature  
  > "this relies heavily on the adopted gas temperature." (Conclusion)
- Caveat (inferred, ours): Single-pixel peak column densities, optically thin LTE assumption and a single shared temperature for all isotopologues; no beam dilution or radiative transfer modelling.
- Caveat (inferred, ours): Species names are lost in the supplied text, so table rows cannot be mapped to molecules without the original paper.
- Caveat (inferred, ours): The key 60 K temperature comes from an unpublished companion paper (in prep.).
- Caveat (inferred, ours): Hyperfine-blended lines and optical depth of the main isotopologue are not modelled.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging cubes and integrated intensity maps are only described in earlier papers; the maps are not provided here
- Missing: Exact peak positions, column density formula details and uncertainty propagation for delta values
- Missing: Temmink et al. in prep. temperature analysis
- Missing: Species assignment of Table 1 and Table 2 rows
- Data volume (inferred): Roughly 10-50 GB of raw ALMA data for two Band 7 style programs (not stated in the paper); derived maps are small
- Score (inferred): 3/5, Two ALMA programs are named and the column density and ratio calculation is simple, but calibration and imaging are inherited from earlier papers, several settings are missing and the key temperature is from unpublished work.
- Rediscovery candidate: no, Imaging and integrated-intensity maps depend on other papers, the data being public is not stated, and species names in the tables are not recoverable from the text.

## Links

- Method: (cite: 2021A&A...651L...6B) Booth et al. 2021 (Imaging and detection of 2017.1.00834.S lines)
- Method: (cite: 2021A&A...651L...5V) van der Marel et al. 2021 (First presentation of the data and 2021.1.00738.S imaging cited here)
- Method: (cite: Booth2023_irs48) Booth, Temmink et al. 2024 (Presents the 2021.1.00738.S data and integrated intensity maps)
- Method: (cite: 2020ApJ...900...81O) Ohashi et al. 2020 (Pipeline calibration of 2017.1.00834.S)
- Companion: Temmink et al. 2024 (in prep.) (Rotational temperature of about 60 K used as the fiducial temperature)
- Related: 2017.1.00834.S
- Related: 2021.1.00738.S

## Checks

```json
{
 "quotes": 100,
 "quotes_ok": 100,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 53,
  "rate": 0.596
 },
 "evidence_ok": true
}
```
