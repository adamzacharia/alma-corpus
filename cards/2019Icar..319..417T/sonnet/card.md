# Abundance measurements of Titan's stratospheric HCN, HC<SUB>3</SUB>N, C<SUB>3</SUB>H<SUB>4</SUB>, and CH<SUB>3</SUB>CN from ALMA observations

`2019Icar..319..417T` | Icarus 2019 | first author: Thelen, Alexander E. | arXiv: 1809.10873 | DOI: 10.1016/j.icarus.2018.09.023

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: solar_system
- Question: What are the vertical abundance profiles of HCN, HC3N, C3H4 and CH3CN in Titan's stratosphere in three independent latitude regions from 2012 to 2015, and what do they imply about Titan's circulation?  
  > "we derive vertical abundance profiles of four of Titan’s trace atmospheric species from the same 3 independent spatial regions across Titan’s disk during the same epoch (2012 to 2015)" (abstract)
- Target **Titan**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00724.S, 2011.0.00820.S, 2012.1.00377.S, 2012.1.00225.S, 2012.1.00453.S, 2013.1.00220.S, 2013.1.00111.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam sizes ~0.2-0.5''  
  > "spatially resolved (beam sizes $\sim0.2-0.5''$) ALMA flux calibration data from 2012 to 2015" (Conclusions)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 to 2015 (see Table 1)  
  > "05 Jun 2012" (Table 1)
- pi or archival as stated: Archival flux calibration data of Titan from ALMA archive  
  > "We utilize flux calibration data of Titan from the ALMA science archive" (Observations)
- Line: HC15N 8–7 (688.273 GHz)
- Line: HC3N 40–39 (363.785 GHz)
- Line: CH3CN 16–15 (K ladder) (294.212-294.302 GHz)
- Line: H13CN 8–7 (690.552 GHz)
- Line: C3H4 18–17 (K ladder) (307.489-307.583 GHz)
- Other facility **Cassini/CIRS**: Temperature profiles for 2013 and comparison abundances  
  > "we elected to use more contemporary temperature profiles obtained during the T89 and T91 *Cassini* flybys" (Spectral Modeling and Retrieval Methodology)
- External data: Disk-averaged HCN abundance profile used to model isotopologues  
  > "fitting H$^{13}$CN and HC$^{15}$N lines using the HCN profile found by (cite: molter_16)" (4.2 HCN) [from (cite: molter_16)]
- External data: Tropospheric temperatures from Cassini radio science  
  > "Using accurate troposphere temperatures from *Cassini* radio science measurements ((cite: schinder_12)" (Spectral Modeling and Retrieval Methodology) [from (cite: schinder_12)]
- External data: Molecular line data  
  > "Molecular line data were obtained from the HITRAN 2016[^3] and CDMS[^4] catalogues" (Spectral Modeling and Retrieval Methodology) [from (cite: gordon_17; muller_05)]
- External data: Titan stratospheric temperature profiles from ALMA  
  > "Both spatially resolved and disk-averaged temperature profiles from Paper I were used to model 2012, 2014, and 2015 spectra" (Spectral Modeling and Retrieval Methodology) [from (cite: thelen_18)]
- Simulation/model as data: A priori profiles from photochemical models (Loison 2015, Dobrijevic 2018) and earlier sub-mm observations  
  > "the model results from (cite: loison_15) up to 1200 km; the model by (cite: dobrijevic_18)" (4.3 CH3CN)

## Processing

### Calibration

- pipeline or manual: JAO data reduction scripts modified to avoid flagging strong Titan lines, following Paper I  
  > "This includes the modification of data reduction scripts provided by the Joint ALMA observatory to avoid the flagging (removal) of strong atmospheric lines from Titan’s atmosphere" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: scaling factors below 5% of continuum flux, within expected calibration uncertainty  
  > "reduced these scaling factors to below $5\%$ of the continuum flux, within the expected calibration uncertainty level" (Spectral Modeling and Retrieval Methodology)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural or Briggs weighting (Briggs for some datasets; robust not given)  
  > "\*Denotes resolution obtained through Briggs weighting as opposed to Natural." (Table 1)
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

- Data reduction, imaging and disk-averaged spectrum extraction  
  > "follow the procedures in Paper I to reduce and calibrate datasets" (Observations) [from Paper I (cite: thelen_18)]
- Spatial region selection of non-overlapping beam footprints  
  > "As in Paper I, spatially resolved spectra were extracted from regions where ALMA ‘beam-footprints’ do not overlap" (Observations) [from Paper I (cite: thelen_18)]
- Atmospheric modeling and synthetic spectra generation  
  > "were carried out in a similar fashion to Paper I" (Spectral Modeling and Retrieval Methodology) [from Paper I; (cite: teanby_13)]
- CO line model parameters  
  > "so those lines were included in the model using the parameters given in Paper I" (4.2 HCN) [from Paper I]

### Not stated but needed to reproduce (our reading)

- Briggs robust values for the datasets using it
- Exact JAO script modifications and CASA version
- Continuum subtraction and line-free channels
- Exact extraction apertures/latitude footprints per dataset
- Numerical retrieved abundance profiles and a priori profile values
- Scaling factor values per dataset
- Exact NEMESIS configuration (grid, field-of-view weights)

## Analysis recipe

1. **Reduce and image archival Titan data, extract spectra**: Modified JAO scripts, imaging per Paper I, disk-averaged and three-region spectra extracted from non-overlapping beam footprints  
  > "general imaging procedures, and the extraction of disk-averaged spectra" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Retrieve vertical abundance profiles**: NEMESIS line-by-line optimal estimation with fixed temperature profiles, multiple field-of-view points, continuum scaling factor  
  > "We employed the Non-Linear Optimal Estimator for Multivariate Spectra Analysis (NEMESIS) radiative transfer code in line-by-line mode" (Spectral Modeling and Retrieval Methodology)
   - software: NEMESIS
   - parameter: A priori errors 100%; correlation length 1.5 scale heights (3.0 for HCN isotopologues)  
  > "*A priori* vertical profiles were taken with 100$\%$ errors at all altitudes and correlation lengths were set to 1.5 scale heights" (Spectral Modeling and Retrieval Methodology)
   - parameter: Retrieval 0-1200 km; results reported 50-550 km; 37-44 FOV points  
  > "many field-of-view averaging points (37-44) are required to model disk-averaged data" (Spectral Modeling and Retrieval Methodology)
   - assumption: HCN from isotopologues with 12C/13C = 89.8, 14N/15N = 72.2; condensation below ~80 km; broadening Gamma=0.1 cm-1/bar, alpha=0.75 for HC3N and C3H4  
  > "applied a constant scaling factor ($^{12}$C/$^{13}$C = 89.8, $^{14}$N/$^{15}$N = 72.2) to determine the HCN abundances" (4.2 HCN)
   - fitting: chi^2 minimization optimal estimation (NEMESIS)  
  > "contribute little to the $\chi^2$ minimization of data and model discrepancies" (Spectral Modeling and Retrieval Methodology)
   - validation: Tested multiple a priori profiles; temperature perturbations of 5 K gave <20% abundance change; compared with Cassini/CIRS and models  
  > "variations of temperature on order 5 K or less resulted in abundance variations \< 20$\%$" (Spectral Modeling and Retrieval Methodology)
3. **Compare regions and epochs, interpret circulation**: Compare North/Center/South profiles over time and with integrated moment 0 maps and CIRS  
  > "When plotting profiles from each spatial region over time" (Spatial and Temporal Variations)
   - fitting: _not stated_
   - validation: Comparison with Cassini/CIRS and photochemical models  
  > "We validated our results using contemporaneous *Cassini*/CIRS data" (Conclusions)

## Software

- **NEMESIS** : Radiative transfer and abundance retrieval  
  > "We employed the Non-Linear Optimal Estimator for Multivariate Spectra Analysis (NEMESIS) radiative transfer code in line-by-line mode" (Spectral Modeling and Retrieval Methodology)
- **HITRAN 2016** 2016: Molecular line data  
  > "Molecular line data were obtained from the HITRAN 2016" (Spectral Modeling and Retrieval Methodology)
- **CDMS** : Molecular line data  
  > "HITRAN 2016[^3] and CDMS[^4] catalogues" (Spectral Modeling and Retrieval Methodology)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN north enhancement vs Center near 0.1 mbar in 2015 | ~16 | not stated | dimensionless | 3 | which is $\sim$16 times greater than the abundance at lower northern latitudes (Center) and a factor of 7 greater than the south |
| HC3N North/South enhancement vs Center, 2013 to 2015 | North 50 to 75; South 34 to 61 | not stated | dimensionless | 3 | they increase from a factor of 50 and 34 to 75 and 61 compared to the center from 2013 to 2015 |
| C3H4 North enhancement vs Center, 2014 and 2015 | 5–6 | not stated | dimensionless | 3 | enhancement of C$_3$H$_4$ at mid-northern latitudes with factors of 5–6 greater than the Center retrievals in 2014 and 2015 |
| CH3CN North enhancement vs Center near 1 mbar | 3–6.5 | not stated | dimensionless | 3 | increasing by a factor of 3–6.5 compared to the Center near 1 mbar |
| CH3CN relative to Cassini CIRS upper limit at 0.27 mbar | ~5 times lower | not stated | dimensionless | 3 | We find CH$_3$CN to be a factor of $\sim5$ less than the upper limit found by (cite: nixon_10) |

## Qualitative findings

- All four molecules are enhanced in the North (often South) relative to Center; retrieved temporal trends indicate continued north-to-south circulation and subsidence at the south pole.  
  > "All four molecules display enhancements in the North (and often the South) compared to Center" (Conclusions)

## Claim tuples

- H: ALMA flux calibration data can yield spatially resolved abundance profiles of Titan's minor species | E: NEMESIS retrievals for three latitude regions, 2012–2015 | R: Profiles comparable to Cassini/CIRS and previous observations, with polar enhancements muted by large beams | F: ALMA is viable for post-Cassini monitoring | **supported**
- H: Abundances show temporal changes tracing circulation | E: Compared regional profiles over years | R: Increases of southern HCN, HC3N, C3H4 at altitude; Center decreases | F: Evidence for subsidence at the south pole | **partially**

## Reasoning

- Why this data: Datasets chosen by spatial resolution and date, nearest to the Paper I data  
  > "Datasets were chosen based on spatial resolution and observation date" (Observations)
- Why this method: _not stated_
- Alternative: Fractional scale height profiles rejected in favour of continuous retrievals  
  > "we find that spectral fits are improved by using continuous abundance retrievals" (4.1 HC3N and C3H4)
- How they decided it was enough: _not stated_
- Limitation (authors): Large beams average latitudes; HC3N optically thick at poles; low sensitivity above ~400 km  
  > "HC$_3$N, which is optically thick at the poles where the molecule has been observed to be greatly enhanced" (Conclusions)
- Caveat (inferred, ours): Retrieved profiles adhere to a priori at edges of sensitivity
- Caveat (inferred, ours): Temperature held fixed, not retrieved jointly
- Caveat (inferred, ours): Different epochs use different molecules/datasets, confounding temporal trends

## Reproducibility

- Data public (paper): Data from ALMA science archive  
  > "We utilize flux calibration data of Titan from the ALMA science archive" (Observations)
- Products in archive: _not stated_
- Missing: Numeric retrieved profiles
- Missing: Temperature profiles from Paper I and CIRS private communication
- Missing: Detailed imaging parameters
- Data volume (inferred): ~100-300 GB for ten archival datasets
- Score (inferred): 3/5, Public data and named code, but many settings inherited from Paper I and results largely graphical.
- Rediscovery candidate: no, Results are mostly profile plots and ratios, and the recipe depends on Paper I and private temperature data.

## Links

- Method: (cite: thelen_18) (Paper I: reduction, imaging, temperature profiles)
- Method: (cite: irwin_08) (NEMESIS)
- Method: (cite: molter_16) (HCN profile and isotopologue approach)
- Companion: (cite: thelen_18) (Temperatures from the same data)
- Related: Cassini/CIRS

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 7,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 34,
  "rate": 0.479
 },
 "evidence_ok": true
}
```
