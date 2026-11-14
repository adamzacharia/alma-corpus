# A major asymmetric ice trap in a planet-forming disk. II. Prominent SO and SO<SUB>2</SUB> pointing to C/O &lt; 1

`2021A&A...651L...6B` | Astronomy and Astrophysics 2021 | first author: Booth, Alice S. | arXiv: 2104.08908 | DOI: 10.1051/0004-6361/202141057

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What S-bearing molecules are present in the Oph-IRS 48 dust-trap disk, what is their origin (ice sublimation vs gas-phase), and what do CS/SO ratios imply for the gas C/O?  
  > "Here we present the first measurements of and in a disk that can be directly linked to an ice trap." (Introduction)
- Target **Oph-IRS 48**: coordinates ICRS 16h27m37.1797s, -24d30m35.480s (Gaia DR2 position at time of Cycle 5 observations)  
  > "Oph-IRS 48 is a 2.0 M$_{\odot}$ Herbig A0 source located at 134 pc in the $\rho$ Ophiuchus star forming region" (Introduction); "the central position is set to ICRS 16h27m37.1797s, -24$^{\circ}$30’35.480"" (Observations); z/distance 134 pc  
  > "Oph-IRS 48 is a 2.0 M$_{\odot}$ Herbig A0 source located at 134 pc in the $\rho$ Ophiuchus star forming region" (Introduction); "the central position is set to ICRS 16h27m37.1797s, -24$^{\circ}$30’35.480"" (Observations); distance from (cite: 2012ApJ...744..116B; Gaia2018)  
  > "Oph-IRS 48 is a 2.0 M$_{\odot}$ Herbig A0 source located at 134 pc in the $\rho$ Ophiuchus star forming region" (Introduction); "the central position is set to ICRS 16h27m37.1797s, -24$^{\circ}$30’35.480"" (Observations)

## Data provenance

- ALMA projects: 2013.1.00100.S, 2017.1.00834.S
- bands: Band 7  
  > "We utilise two sets of Band 7 observations of Oph-IRS 48 taken with the Atacama Large Millimeter/submillimeter Array (ALMA) during Cycles 2 and 5." (Observations)
- frequencies and spectral setup: Cycle 2 channel width 122 kHz (≈0.23 km/s); Cycle 5 channel width 1953 kHz (≈1.7 km/s)  
  > "have native channel width of 122 kHz or $\approx$0.23 km s$^{-1}$ and a spatial resolution of $\approx$0.2$''$." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Cycle 2 ≈0.2''; Cycle 5 ≈0.5''  
  > "These line data all have a channel width of 1953 kHz or $\approx$1.7 km s$^{-1}$ and a spatial resolution of $\approx$0.5$''$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Cycle 2: June and August 2015; Cycle 5: August 2018  
  > "The Cycle 5 program 2017.1.00834.S (PI: Adriana Pohl) was taken in August 2018." (Observations)
- pi or archival as stated: Cycle 2 PI van der Marel; Cycle 5 PI Pohl (data from Ohashi et al. 2020)  
  > "The Cycle 2 program 2013.1.00100.S (PI: Nienke van der Marel)" (Observations)
- Line: CS 7-6 (342.8828503 GHz)
- Line: SO not stated in text (329.3854770 GHz)
- Line: SO2 three lines (351.2572233, 351.8738732, 362.1582327 GHz)
- Other facility **Herschel/PACS**: Non-detections of OH and another species in IRS 48 (literature)  
  > "Interestingly *Herschel*/PACS reported non-detections of both OH and in the IRS-48 disk" (5.2)
- External data: 0.9 mm higher-resolution dust continuum image and 5σ extent used as emitting area  
  > "we assume the line emitting area to be the same as the 5$\sigma$ extent of the 0.9 mm dust emission from (cite: Francis2020)" (Analysis) [from (cite: Francis2020)]
- External data: NH column density at 60 au of 1.6e22 cm-2 from IRS 48 disk model  
  > "The ${N_{\mathrm{H}}}$ column density at 60 au from the IRS 48 disk model is $1.6\times10^{22}$ $\mathrm{cm^{-2}}$" (5.1) [from (cite: Bruderer2014; vanderMarel2016-isot)]
- External data: Line frequencies, Einstein A, Eup, gu from CDMS  
  > "are taken from the Cologne Database for Molecular Spectroscopy (CDMS)" (Table 1) [from (cite: 2005JMoSt.742..215M)]
- External data: 32S/34S isotope ratio of 22  
  > "compared to the value of 22 for the / isotope ratio" (Analysis) [from (cite: 1999RPPh...62..143W)]
- External data: Refractory sulphur fraction ≈89±8%  
  > "The bulk of the elemental sulphur in protoplanetary disks is thought to be in refractory materials ($\approx$89$\pm$8$\%$)" (5.1) [from (cite: 2019ApJ...885..114K)]

## Processing

### Calibration

- pipeline or manual: Cycle 2 calibrated with provided calibration scripts; Cycle 5 calibration as in Ohashi et al. 2020  
  > "were taken June and August 2015 and were calibated using using the provided calibration scripts." (Observations); "For full details on the data calibration see (cite: Ohashi2020) where the continuum polarization data are presented." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% ALMA flux calibration error  
  > "is listed in Table [\[line_list\]](#line_list) with a 10% ALMA flux calibration error." (Analysis)
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "All of the lines were imaged using CASA `tCLEAN` with robust weighting of 0.5" (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "All of the lines were imaged using CASA `tCLEAN` with robust weighting of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask, i=50 deg, PA=100 deg, M*=2.0 Msun, d=134 pc  
  > "a Keplerian mask (with an inclination angle of 50$^{\circ}$ and position angle of 100$^{\circ}$, (cite: 2021AJ....161...33V)) and stellar mass of 2.0 M$_{\odot}$ and distance of 134 pc" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cycle 2 SO line imaged at 1.7 km/s to reduce rms and match Cycle 5 resolution  
  > "To reduce the per channel rms and thus increase the signal-to-noise the Cycle 2 SO - line was imaged at 1.7 km s$^{-1}$." (Observations)
- final beam: 0.20''x0.16'' (Cycle 2); 0.55''x0.44'' / 0.53''x0.42'' (Cycle 5)  
  > "0.55$''$$\times$0.44$''$ (80$^{\circ}$)" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Cycle 5 data calibration details  
  > "For full details on the data calibration see (cite: Ohashi2020) where the continuum polarization data are presented." (Observations) [from (cite: Ohashi2020)]
- Emitting area assumption same as Paper I  
  > "This is the same approach as in Paper I and is an area of 1.2$\times10^{-11}$ steradians." (Analysis) [from Paper I (cite: vanderMarel2021)]
- Upper limit on CS flux propagated from channel-map rms  
  > "was propagated from the rms noise in the channel maps following the method in (cite: 2019A&A...623A.124C)" (Observations) [from (cite: 2019A&A...623A.124C)]
- Opacity-corrected rotational diagram method  
  > "Following the method outlined in (cite: 1999ApJ...517..209G) and applied to disks (cite: 2018ApJ...859..131L)" (Analysis) [from (cite: 1999ApJ...517..209G; 2018ApJ...859..131L)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Line-free channels and continuum subtraction details
- Cell size, image size, clean threshold, niter
- Which isotopologue/species columns and labels are lost in the text (chemical formulae stripped)
- Self-calibration status
- Partition function and rotational diagram fit details
- Exact Keplerian mask width/ parameters
- Beam-averaged vs. flux aperture definitions for radial/azimuthal profiles

## Analysis recipe

1. **Image lines**: tclean with robust 0.5 and Keplerian mask; Cycle 2 SO rebinned to 1.7 km/s  
  > "All of the lines were imaged using CASA `tCLEAN` with robust weighting of 0.5" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Detection >3σ over 3 consecutive channels  
  > "robustly detected ($>3\sigma$ emission over 3 consecutive channels)" (Observations)
2. **Radial and azimuthal profiles**: Radial profiles averaged over 100-260 deg wedge; azimuthal profiles from de-projected ellipse at ≈70 au (and ≈90 au for SO); compared with 0.9 mm dust  
  > "The radial profiles for the dust and molecular lines were averaged over a wedge from 100$^{\circ}$ to 260$^{\circ}$ relative to the north minor axis" (Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Disk-integrated fluxes**: Extract from channel maps using Keplerian mask; 3σ CS upper limit  
  > "The total disk integrated line flux was extracted from the channel maps using a Keplerian mask" (Analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Column densities**: Opacity-corrected rotational diagram for SO2 (Trot≈100 K); other species at Tex 50, 100, 150 K; LTE  
  > "we construct an opacity-corrected rotational diagram for the resulting in a rotational temperature of $\approx$100 K." (Analysis); "We also calculate column densities for , and assuming an excitation temperature of 50, 100 and 150 K." (Analysis)
   - assumption: Emitting area 1.2e-11 sr (5σ extent of 0.9 mm dust); LTE; 32S/34S = 22  
  > "This is the same approach as in Paper I and is an area of 1.2$\times10^{-11}$ steradians." (Analysis)
   - fitting: _not stated_
   - validation: Optical depth check via isotopologue ratio (2 vs 22) and brightness temperature (~7 K, beam dilution)  
  > "We find that this results a low temperature with a peak of $\approx$7 K." (Analysis)
5. **Volatile S budget and C/O**: Sum SO and SO2 columns divided by NH(60 au) to get S/H; compare CS/SO with chemical models  
  > "This results in a S/H ratio of 4.6-10.0$\times10^{-7}$" (5.1)
   - assumption: NH = 1.6e22 cm-2 at 60 au from disk model  
  > "The ${N_{\mathrm{H}}}$ column density at 60 au from the IRS 48 disk model is $1.6\times10^{22}$ $\mathrm{cm^{-2}}$" (5.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : tclean imaging  
  > "All of the lines were imaged using CASA `tCLEAN`" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| S/H from SO and SO2 | 4.6-10.0e-7 | not stated | dimensionless | 5 | This results in a S/H ratio of 4.6-10.0$\times10^{-7}$ |
| SO2 rotational temperature | ≈100 | not stated | K | 4 | resulting in a rotational temperature of $\approx$100 K |
| CS/SO ratio | <0.01 | not stated | dimensionless | 4 | The ratio of CS/SO is $<$0.01 |
| SO/SO2 ratio | 1.5-1.8 | not stated | dimensionless | 4 | We derive a / ratio of 1.5-1.8 |
| Peak brightness temperature of SO2 line | ≈7 | not stated | K | 4 | We find that this results a low temperature with a peak of $\approx$7 K. |

## Qualitative findings

- SO2 clearly detected; first robust detection in a Class II disk; S-species co-spatial with the asymmetric dust trap  
  > "This is the first robust detection of and the isotopologue in a Class II disk." (Conclusions)

## Claim tuples

- H: Sulphur species trace ice sublimation at the dust trap | E: Compare SO/SO2 maps and profiles with 0.9 mm dust | R: Emission is asymmetric and peaks in the dust trap region | F: Gas-phase SO and SO2 likely from sublimation of ices at cavity edge | **partially**
- H: Volatile S accounted for by SO and SO2 | E: Column densities / NH | R: S/H 4.6-10.0e-7 | F: 15-100% of expected volatile S budget | **supported**
- H: CS/SO traces gas C/O | E: CS upper limit vs SO | R: CS/SO <0.01 | F: C/O <1, likely solar | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gas-phase formation via S+OH considered but OH not detected by Herschel  
  > "Therefore gas phase formation of and requires sufficient OH in the disk atmosphere." (5.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Column densities inversely proportional to assumed emitting area, so may be lower limits  
  > "as the inferred column densities are inversely proportional to the assumed emitting area our results may be a conservative lower limit" (Analysis)
- Caveat (inferred, ours): Low resolution (0.5'') and unresolved emission
- Caveat (inferred, ours): Emitting area assumption and fixed Tex drive column density
- Caveat (inferred, ours): C/O inference rests on comparison with models for other disks
- Caveat (inferred, ours): SO and SO2 lines at different resolutions

## Reproducibility

- Data public (paper): Project codes given; ALMA archive data  
  > "This paper makes use of the following ALMA data: 2013.1.00100.S, 2017.1.00834.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Line-free channels and clean parameters
- Missing: Rotational diagram fitting details
- Missing: Continuum images from Francis & van der Marel 2020 and Ohashi 2020
- Data volume (inferred): ~50-200 GB
- Score (inferred): 5/5, Public data and basic recipe, but many imaging and fit details are missing.
- Rediscovery candidate: no, Recipe lacks key imaging and fitting parameters and relies on external products.

## Links

- Method: (cite: 1999ApJ...517..209G) (Rotational diagram method)
- Method: (cite: Ohashi2020) (Cycle 5 calibration)
- Companion: (cite: vanderMarel2021) (Paper I)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 40,
  "rate": 0.541
 },
 "evidence_ok": true
}
```
