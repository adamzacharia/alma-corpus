# The Molecular Wind in the Nearest Seyfert Galaxy Circinus Revealed by ALMA

`2016ApJ...832..142Z` | The Astrophysical Journal 2016 | first author: Zschaechner, Laura K. | arXiv: 1609.06316 | DOI: 10.3847/0004-637X/832/2/142

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Is there a molecular outflow in Circinus, and what are its mass, outflow rate and energetics compared with other AGN- and starburst-driven outflows?  
  > "we see indications of outflowing molecular gas at velocities consistent with the ionized outflow." (abstract)
- Target **Circinus galaxy**: coordinates pointing center 14h 13m 09.9s, -65d 20m 21.0s  
  > "At an adopted distance of 4.2 Mpc (1"$=$20.4 pc, (cite: 2009AJ....138..323T))" (The Circinus Galaxy); "Pointing Center" (Table 1); z/distance 4.2 Mpc  
  > "At an adopted distance of 4.2 Mpc (1"$=$20.4 pc, (cite: 2009AJ....138..323T))" (The Circinus Galaxy); "Pointing Center" (Table 1); distance from Tully et al. 2009 (cite: 2009AJ....138..323T)  
  > "At an adopted distance of 4.2 Mpc (1"$=$20.4 pc, (cite: 2009AJ....138..323T))" (The Circinus Galaxy); "Pointing Center" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00247.S
- bands: _not stated_
- frequencies and spectral setup: 99.8–103.5 and 111.9–115.7 GHz; 4 SPWs; 2.5–3 km/s velocity resolution  
  > "The velocity resolution of our data is 2.5–3 km s$^{-1}$ over this frequency range." (2 Observations & Data Reduction); "Frequencies Covered" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 12-m array (7-pointing mosaic), ACA (3-pointing mosaic), Total Power  
  > "Our observational setup consisted of a 7-pointing mosaic with the 12-meter array, a 3-pointing mosaic for the ALMA Compact Array (ACA), and single-pointing Total Power TP observations." (2 Observations & Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2–3" (40–60 pc)  
  > "Spatial Resolution/Beam Size" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: CO(1-0) cube rms 5.4 mJy/beam; CN cubes 2.8–3.3 mJy/beam  
  > "(CO (1–0) line cube)                    | 5.4 mJy beam$^{-1}$" (Table 1)
- time on source: _not stated_
- observing dates: ACA 2014 Jul 2, Aug 10, Aug 11; 12-m 2014 Dec 27; TP 2015 Jan 14–31  
  > "Observation Dates$-$12-meter Array      |         2014 Dec 27" (Table 1)
- pi or archival as stated: PI: Zschaechner (own program)  
  > "ALMA data are from programme ID: ADS/JAO.ALMA#2013.1.00247.S, PI: Zschaechner." (2 Observations & Data Reduction)
- Line: CO (1–0) (115.27120 GHz)
- Line: CN (1–0) J=1/2 and J=3/2 hyperfine groups (113.123–113.191 and 113.488–113.520 GHz)
- Line: C17O (1–0) (112.359 GHz)
- Other facility **VLT/MUSE**: Halpha IFU data of ionized outflow for comparison  
  > "Integral–field spectroscopic data of the Circinus galaxy were collected during March 11th, 2015 with the Multi Unit Spectroscopic Explorer" (2 Observations & Data Reduction)
- External data: SFR 4.7 Msun/yr from L_TIR  
  > "We adopt the value of 4.7 M$_{\odot}$ yr$^{-1}$ calculated by (cite: 2008ApJ...686..155Z) using the total infrared luminosity" (4.1.5 Molecular Outflow Parameters) [from (cite: 2008ApJ...686..155Z)]
- External data: alpha_CO values 0.34, 0.8 (outflow) and 4.3 (disk)  
  > "Using the $\alpha_{CO}$ conversion factor of 0.34 M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ put forth in (cite: 2013ARA&A..51..207B)" (4.1.5 Molecular Outflow Parameters) [from (cite: 2013ARA&A..51..207B)]
- External data: Optical outflow velocity 180 km/s  
  > "the optical velocities (180 km s$^{-1}$) as seen in (cite: 1997ApJ...479L.105V)" (4.1.5 Molecular Outflow Parameters) [from (cite: 1997ApJ...479L.105V)]
- External data: Comparison sample of molecular outflows (kinetic power, momentum rates, L_AGN)  
  > "We directly duplicate Figure 12 from that work here with the addition of Circinus" (5.1 Energetics) [from (cite: 2014A&A...562A..21C)]

## Processing

### Calibration

- pipeline or manual: ACA: ALMA staff scripts with minor adjustments; 12-m: ALMA pipeline  
  > "Initial calibration utilized the scripts provided by the ALMA staff for the ACA data and the ALMA pipeline for the 12-meter data." (2 Observations & Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ACA Mars; 12-m Ceres  
  > "Calibrators 12-m - Flux                 |               Ceres" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: one iteration of phase-only self-cal on 12-m data; amplitude self-cal not used  
  > "Amplitude self-calibration was attempted but yielded no clear improvement and was not used." (2 Observations & Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural and Briggs robust 0.5  
  > "Cubes were created using both natural and Briggs weighting (cite: 1995PhDT.......125B) with a robust parameter of 0.5" (2 Observations & Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 3 sigma masks from natural cubes; 6 sigma for CO(1-0); cleaned to 4 sigma  
  > "the final Briggs-weighted cube was cleaned down to 4$\sigma$" (2 Observations & Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: cubes combined with Total Power using FEATHER  
  > "The cubes were then combined with data from the total power array using `FEATHER`." (2 Observations & Data Reduction)
- smoothing: _not stated_
- final beam: ~3x2" natural; 2.7x2.1" CO(1-0) Briggs  
  > "2.7$\times$2.1" for the CO (1–0) Briggs-weighted cube" (2 Observations & Data Reduction)
- final rms: 5.4 mJy/beam (CO(1-0) cube)  
  > "(CO (1–0) line cube)                    | 5.4 mJy beam$^{-1}$" (Table 1)

### Inherited from earlier work

- Moment maps made with SoFiA-type software to retain faint emission  
  > "Moment maps are created using software described in (cite: 2015MNRAS.448.1922S) in order to retain faint emission." (3 The Data) [from (cite: 2015MNRAS.448.1922S)]
- Outflow rate formula as for NGC 253  
  > "As was also done in (cite: 2013Natur.499..450B) for the case of NGC 253, we use the following formula based on the morphology of the outflow" (4.1.5 Molecular Outflow Parameters) [from (cite: 2013Natur.499..450B)]
- Tilted-ring modeling procedure described in earlier papers  
  > "A more detailed description of the modeling process can be found in (cite: 2012ApJ...760...37Z), (cite: 2013A&A...554A.125G), and (cite: 2015ApJ...808..153Z) among others." (Appendix) [from (cite: 2012ApJ...760...37Z), (cite: 2013A&A...554A.125G), (cite: 2015ApJ...808..153Z)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum subtraction method
- Cell and image size, clean scales, and deconvolver
- CASA version and pipeline version
- Flux scale uncertainty
- Exact boxes for overdense region, NW cloud, far W cloud, northern stripe
- Moment-map clipping thresholds
- Exact TiRiFiC ring parameters and fit procedure
- Total power scaling factor used in feathering

## Analysis recipe

1. **Calibrate and image cubes**: ALMA scripts/pipeline calibration, phase self-cal, natural and Briggs cubes cleaned with masks, feathered with TP  
  > "Minor phase errors in the final cubes were eliminated via a single iteration of phase-only self-calibration on the 12-meter data." (2 Observations & Data Reduction)
   - software: CASA, FEATHER
   - parameter: robust = 0.5; 6 sigma mask, clean to 4 sigma for CO(1-0)  
  > "required a 6$\sigma$ mask (based on the naturally-weighted cube) to remove artefacts." (2 Observations & Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps and identify outflow candidates**: Moment maps, dispersion profile, comparison with MUSE Halpha channel maps  
  > "The molecular outflow itself is most readily seen as an increase in velocity dispersion." (3 The Data)
   - software: SoFiA-style moment software
   - fitting: _not stated_
   - validation: _not stated_
3. **Isolate outflow with four approaches**: flux excess vs azimuthally opposite region; mirrored velocity-field residual; TiRiFiC disk model subtraction; spectral analysis  
  > "To isolate potential outflowing material, we use four approaches" (4.1 The Molecular Outflow in Circinus)
   - software: TiRiFiC
   - parameter: disk inclination 65 deg, PA 210 deg, dispersion 15 km/s, scale height 4"  
  > "65$^{\circ}$ is found to be the best fit throughout the disk." (Appendix)
   - assumption: All excess emission in the restricted region is outflow  
  > "we assume that any anomalous or over-dense gas in this restricted region is indeed part of the molecular outflow." (4.1 The Molecular Outflow in Circinus)
   - fitting: tilted-ring modeling, halves modeled separately; fit by eye of PV diagrams  
  > "Due to asymmetries, we model the approaching and receding halves of the galaxy separately." (Appendix)
   - validation: Models compared to data via residual moment maps; third method judged unreliable for mass  
  > "Ultimately, a reliable outflow mass cannot be derived from this method in the case of Circinus." (4.1.5 Molecular Outflow Parameters)
4. **Derive outflow masses and rates**: CO luminosity to mass with alpha_CO; Mdot = 2 alpha_CO L_CO v_w tan i / r_w  
  > "$$\begin{equation}
\dot{M}=\frac{2\alpha_{CO}L_{CO}v_{w}\tan{i}}{r_{w}}\label{equation_outflow}
\end{equation}$$" (4.1.5 Molecular Outflow Parameters)
   - parameter: v_w 150 km/s (lower), 180 km/s (upper); alpha_CO 0.34 to 0.8  
  > "We also assume a higher $\alpha_{CO}$ of 0.8 M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ for an optically-thick case." (4.1.5 Molecular Outflow Parameters)
   - assumption: outflow cone perpendicular to disk inclination of 65 deg  
  > "for simplicity we assume it is perpendicular to the disk inclination of 65$^{\circ}$." (4.1.5 Molecular Outflow Parameters)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute energetics and compare with literature**: Kinetic power 0.5 v^2 Mdot and momentum rate v Mdot compared with Cicone et al. 2014 relations  
  > "The kinetic power ($P_{kin, OF}=\frac{1}{2}v^2\dot{M}_{H_{2}, OF}$) and momentum rate ($v\dot{M}_{H_{2}, OF}$)" (4.1.5 Molecular Outflow Parameters)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging  
  > "Calibration of the ALMA data was done using the Common Astronomy Software Application (CASA)." (2 Observations & Data Reduction)
- **FEATHER** : combining interferometer cubes with total power  
  > "The cubes were then combined with data from the total power array using `FEATHER`." (2 Observations & Data Reduction)
- **TiRiFiC** : tilted-ring disk models  
  > "We employ tilted-ring modeling (cite: 1974ApJ...193..309R) to characterize the properties of the main disk using the Tilted Ring Fitting code" (Appendix)
- **MUSE data reduction pipeline** 1.0.1: reducing MUSE data  
  > "The MUSE data reduction pipeline (version 1.0.1) was used to perform standard steps of the data processing" (2 Observations & Data Reduction)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO luminosity of outflow in overdense region | 3.8e6 | not stated | K km/s pc^2 | 4 | The CO luminosity associated with the outflow in the overdense region is 3.8$\times$10$^{6}$ K km s$^{-1}$ pc$^{2}$. |
| Molecular mass, overdense region (alpha_CO=0.34) | 1.6e6 | not stated | Msun | 4 | we obtain a molecular mass of 1.6$\times$10$^{6}$ M$_{\odot}$ |
| NW cloud molecular mass | 2.1e5 | ~30% in L_CO | Msun | 4 | its molecular mass to be 2.1$\times$10$^{5}$ M$_{\odot}$ |
| Total outflowing molecular mass | 1.5e5–5.1e6 | not stated | Msun | 4 | We constrain the mass of the outflowing molecular gas to be 1.5$\times$10$^{5}$ –5.1$\times$10$^{6}$ M$_{\odot}$ |
| Molecular outflow rate, overdense region | 3.0 (lower), 8.3 (upper) | not stated | Msun/yr | 4 | we determine a molecular mass outflow rate of 3.0 M$_{\odot}$ yr$^{-1}$ in the overdense region. |
| Total molecular outflow rate | 0.35–12.3 | not stated | Msun/yr | 4 | yielding a molecular outflow rate of 0.35–12.3 M$_{\odot}$ yr$^{-1}$ |
| Molecular disk mass within ~1.5 kpc | 2.9e8 | 8.7e7 | Msun | 4 | 2.9$\times$10$^{8}$$\pm$8.7$\times$10$^{7}$ M$_{\odot}$ |
| Kinetic power of outflow | 1.0e39–1.1e41 | not stated | erg/s | 5 | 1.0$\times$10$^{39}$–1.1$\times$10$^{41}$ erg s$^{-1}$ |
| Momentum rate | 2.0e32–1.3e34 | not stated | g cm s^-2 | 5 | 2.0$\times$10$^{32}$–1.3$\times$10$^{34}$ g cm s$^{-2}$ |

## Qualitative findings

- Outflow cannot be cleanly separated from disk, bar and spiral arms; molecular gas is not outflow-dominated  
  > "the molecular gas is clearly not outflow-dominated" (4.1.2 Outflow Extraction via Inspection of Asymmetries in the Velocity Field)
- Outflowing gas likely reaccreted since velocity is below escape velocity  
  > "with the outflow velocity being substantially less than the escape velocity, the molecular gas will most likely be reaccreted." (4.1.5 Molecular Outflow Parameters)

## Claim tuples

- H: Does Circinus host a molecular outflow matching its ionized outflow? | E: CO(1-0) moment maps, channel maps, spectra compared with MUSE Halpha | R: Overdense region with 30–50 km/s dispersion and NW cloud blue-shifted up to ~150 km/s | F: Indications of molecular outflow at velocities consistent with the ionized outflow, though ambiguous | **partially**
- H: Is the molecular outflow rate comparable to the SFR? | E: Mass and rate from CO excess flux with alpha_CO 0.34–0.8 | R: 0.35–12.3 Msun/yr versus SFR 4.7 Msun/yr | F: Comparable, so outflow may affect star formation | **supported**
- H: Does Circinus follow the Cicone et al. 2014 outflow trends? | E: Compare kinetic power and momentum rate with L_AGN and L_bol | R: Consistent with P_kin vs L_AGN linear relation, momentum rate vs L_bol like starbursts; low relative to high L_AGN/L_bol | F: Partly consistent with trends | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Mass-related values from the flux-excess method; velocities from spectra, since disk subtraction removes outflow sharing disk velocities  
  > "we use the numerical values derived using the first method for the mass-related quantities" (4.1.5 Molecular Outflow Parameters)
- Alternative: Mirrored-velocity residuals and kinematic-model subtraction rejected as sources of outflow mass  
  > "The second method provides no quantifiable results" (4.1.5 Molecular Outflow Parameters)
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow, bar and spiral arms degenerate; resolution of 2–3" limits comparison and detail  
  > "the outflow cannot be easily separated from disk material" (4.1 The Molecular Outflow in Circinus)
- Limitation (authors): Far W cloud needs higher resolution or more CO transitions to confirm  
  > "additional observations at either higher resolution or more CO transitions are necessary to confirm whether it is indeed part of the outflow." (3.1 Likely Outflowing Molecular Gas)
- Caveat (inferred, ours): Mass range depends strongly on assumed alpha_CO and on attributing all excess flux to outflow
- Caveat (inferred, ours): Outflow geometry (perpendicular to disk, 65 deg) is a simplification
- Caveat (inferred, ours): Region boxes are chosen by eye
- Caveat (inferred, ours): No uncertainties for several luminosities

## Reproducibility

- Data public (paper): Program ID given; public availability not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00247.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Region definitions and boxes
- Missing: CASA version and imaging parameters
- Missing: TiRiFiC final parameter files
- Data volume (inferred): ~100–300 GB raw for 12m+ACA+TP; cubes tens of GB
- Score (inferred): 3/5, Data identified and recipe broadly described, but regions, imaging details and versions are missing and key results depend on assumptions.
- Rediscovery candidate: no, Main mass and rate numbers depend on hand-selected regions and assumed alpha_CO and velocities; imaging details missing.

## Links

- Method: (cite: 2007A&A...468..731J) (TiRiFiC tilted-ring code)
- Method: (cite: 2015MNRAS.448.1922S) (moment map software)
- Companion: (cite: 2014A&A...562A..21C) (comparison sample of molecular outflows)
- Companion: (cite: 2013Natur.499..450B) (outflow rate formula applied to NGC 253)
- Related: MUSE programme 094.B-0321(A)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 50,
  "rate": 0.617
 },
 "evidence_ok": true
}
```
