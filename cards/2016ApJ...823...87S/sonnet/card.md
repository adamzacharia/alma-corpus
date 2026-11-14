# The Dense Gas in the Largest Molecular Complexes of the Antennae: HCN and HCO<SUP>+</SUP> Observations of NGC 4038/39 Using ALMA

`2016ApJ...823...87S` | The Astrophysical Journal 2016 | first author: Schirm, Maximilien R. P. | arXiv: 1604.00426 | DOI: 10.3847/0004-637X/823/2/87

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, astrochemistry
- Question: How do dense gas fraction (HCN/CO) and dense-tracer line ratios (HNC/HCN, HCN/HCO+) vary among the brightest regions of the Antennae, and what do they imply about pressure, mechanical heating and cosmic rays?  
  > "We find that the ratio of $L_{\mathrm{HCN}}/L_{\mathrm{CO}}$, which traces the dense molecular gas fraction, is greater in the two nuclei" (abstract)
- Target **NGC 4038/39 (Antennae)**: coordinates Pointing 1: 12h01m51.7763s, -18d52m02.892s; pointing 2: 12h01m54.5945s, -18d52m50.891s  
  > "We adopt a distance to NGC 4038/39 of $D = 22 \ensuremath{\, \mathrm{Mpc}}$ (cite: schweizer2008), corresponding to an angular scale of $107 \ensuremath{\, \mathrm{pc/''}}$." (1 Introduction); z/distance D = 22 Mpc; z = 0.005477  
  > "We adopt a distance to NGC 4038/39 of $D = 22 \ensuremath{\, \mathrm{Mpc}}$ (cite: schweizer2008), corresponding to an angular scale of $107 \ensuremath{\, \mathrm{pc/''}}$." (1 Introduction); distance from Schweizer et al. 2008  
  > "We adopt a distance to NGC 4038/39 of $D = 22 \ensuremath{\, \mathrm{Mpc}}$ (cite: schweizer2008), corresponding to an angular scale of $107 \ensuremath{\, \mathrm{pc/''}}$." (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00185.S
- bands: Band 3  
  > "Band 3 was used, with one spectral window set to observe both $\ensuremath{\mathrm{HCN}}$ and $\ensuremath{\mathrm{HCO^+}}$ simultaneously." (2 Observations)
- frequencies and spectral setup: Two 1875 MHz line windows (0.488 MHz channels; HCN+HCO+, HNC); two 2000 MHz continuum windows at 101.0 and 102.875 GHz (15.625 MHz channels)  
  > "The two remaining spectral windows were centred at $101.0 \ensuremath{\, \mathrm{GHz}}$ and $102.875 \ensuremath{\, \mathrm{GHz}}$ to observe the continuum emission across the Antennae." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C32-4  
  > "The antenna array configuration was C32-4." (2 Observations)
- baselines: _not stated_
- angular resolution: 1.86'' x 1.52'' (HCN native); 4.91'' x 3.15'' tapered  
  > "$1.86'' \times 1.52'', -79.8^\circ$ for the $\ensuremath{\mathrm{HCN}}$ line" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: sigma = 0.55 mJy/beam (native, 5 km/s channels); 0.8 mJy/beam tapered  
  > "($\sigma = 0.55 \ensuremath{\, \mathrm{mJy \ beam^{-1}}}$)" (2 Observations)
- time on source: 20356 seconds total, two pointings  
  > "with a total on-source integration time of $20356 \ensuremath{\, \mathrm{seconds}}$" (2 Observations)
- observing dates: March 2013 and April 2014, ALMA Cycle 1  
  > "in March, 2013 and April, 2014 as part of ALMA Cycle-1" (2 Observations)
- pi or archival as stated: _not stated_
- Line: HCN J=1-0 (not stated)
- Line: HCO+ J=1-0 (not stated)
- Line: HNC J=1-0 (not stated)
- Other facility **OVRO (CO J=1-0)**: CO J=1-0 map used for ratios and beam matching  
  > "we create dirty and clean data cubes to match the beam of the $\ensuremath{\mathrm{CO}}$ $J=1-0$ data cube from (cite: wilson2000; wilson2003)." (2 Observations)
- External data: CO J=1-0 interferometric map and cloud catalogue; region definitions (SGMCs, velocities)  
  > "(cite: wilson2000) identified and isolated the 7 brightest regions in their $\ensuremath{\mathrm{CO}}$ $J=1-0$ map of the Antennae using the clump identification algorithm CLFIND" (3 The brightest regions) [from (cite: wilson2000; wilson2003)]
- External data: Single-dish HCN J=1-0 luminosity for comparison  
  > "They calculate a total $\ensuremath{\mathrm{HCN}}$ $J=1-0$ luminosity of $0.8 \times 10^{8} \ensuremath{\, \mathrm{K \ km \ s^{-1} \ pc^{2}}}$" (2 Observations) [from (cite: gao2001)]
- External data: PDR models with mechanical heating for HNC/HCN  
  > "We compare our measured ratio to the PDR models with mechanical heating from (cite: kazandjian2015)." (5.4) [from (cite: kazandjian2015)]

## Processing

### Calibration

- pipeline or manual: PI-delivered calibration script run  
  > "We start by running the script provided to the PI as part of the data delivery in order to calibrate the *uv*-datasets" (2 Observations)
- casa version: CASA 4.2  
  > "We reduce these data using the Common Astronomy Software Applications package version 4.2." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (amplitude); J1215-1731 phase; bandpass J1256-0547, J1246-2547, J1130-1449  
  > "while J1215-1731 was used as the phase calibrator and Titan was used as the amplitude calibrator throughout." (2 Observations)
- flux scale uncertainty: 5% for ALMA Band 3 Cycle 1  
  > "The calibration uncertainty for ALMA band 3 in Cycle 1 is $5\%$ (see text)" (Table 1)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "when using Briggs weighting with robust $= 0.5$" (2 Observations)
- uv taper: 5.0'' x 2.0'', 1.45 deg  
  > "We set the *uv*-taper on the outer baselines to $5.0''\times 2.0'', 1.45^\circ$" (2 Observations)
- cell size: 0.3''; channel width 5 km/s  
  > "with a channel width of $5 \ensuremath{\, \mathrm{km \ s^{-1}}}$ and cell size of $0.3''$" (2 Observations)
- image size: _not stated_
- masking: clean boxes around >5 sigma emission in dirty cubes; clean to 2 sigma (1.1 mJy/beam)  
  > "We clean down to a threshold of $1.1 \ensuremath{\, \mathrm{mJy \ beam^{-1}}}$, corresponding to $2\sigma$ in both dirty data cubes" (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: first order polynomial fit to line-free channels with uvcontsub  
  > "We subtract the background continuum emission by fitting a first order polynomial to the line-free channels of each spectral window using the `uvcontsub` task." (2 Observations)
- line free channels: _not stated_
- primary beam correction: applied to moment-0 maps  
  > "we correct all of our $\ensuremath{\mathrm{HCN}}$, $\ensuremath{\mathrm{HCO^+}}$, and $\ensuremath{\mathrm{HNC}}$ moment-0 maps for the primary beam." (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: HCN native beam 1.86''x1.52'' applied to HCO+; tapered 4.91''x3.15'', 1.45 deg  
  > "We set the restoring beam for the $\ensuremath{\mathrm{HCN}}$ and $\ensuremath{\mathrm{HCO^+}}$ transitions to the $\ensuremath{\mathrm{HCN}}$ beam" (2 Observations)
- final rms: 0.55 mJy/beam native; 0.8 mJy/beam tapered  
  > "($\sigma = 0.8 \ensuremath{\, \mathrm{mJy \ beam^{-1}}}$)" (2 Observations)

### Inherited from earlier work

- CO J=1-0 map, its primary beam correction and 20% calibration uncertainty  
  > "The calibration uncertainty of the $\ensuremath{\mathrm{CO}}$ $J=1-0$ map is $20 \%$ (cite: wilson2003)." (2 Observations) [from (cite: wilson2003)]
- Luminosity conversion formula  
  > "convert them to luminosities using the following formula (cite: wilson2008)" (4.1) [from (cite: wilson2008)]
- SGMC velocity ranges (Vlsr, FWHM) for separating SGMC 3, 4, 5  
  > "Using the measured local standard of rest velocity ($V_{lsr}$) along with the velocity widths ($\Delta V_{FWHM}$) from (cite: wilson2000)" (3) [from (cite: wilson2000)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- Velocity ranges for moment maps
- Aperture shapes/positions for each region
- Number of clean iterations / deconvolver
- Rest frequencies adopted
- Which observing nights used which calibrators
- Primary beam correction method details

## Analysis recipe

1. **Calibrate and image line cubes**: PI calibration script, uvcontsub, Briggs-weighted clean with boxes; second tapered set matched to CO beam  
  > "We create dirty data-cubes for each of the $\ensuremath{\mathrm{HCN}}$, $\ensuremath{\mathrm{HCO^+}}$, and $\ensuremath{\mathrm{HNC}}$ $J=1-0$ transitions with a channel width of $5 \ensuremath{\, \mathrm{km \ s^{-1}}}$" (2 Observations)
   - software: CASA
   - parameter: robust 0.5; 5 km/s; 0.3'' cells; taper 5.0''x2.0''  
  > "We use the same channel width and cell size as before, and draw clean boxes around $5\sigma$ emission." (2 Observations)
   - fitting: _not stated_
   - validation: Compared total HCN luminosity to single-dish; recover ~90%  
  > "This comparison suggests that we recover $\sim 90\%$ of the total $\ensuremath{\mathrm{HCN}}$ emission in our ALMA observations." (2 Observations)
2. **Make primary-beam-corrected moment-0 maps**: Moment-0 including emission above 2 sigma; uncertainty sqrt(Nchan) sigma dv per pixel  
  > "We create moment maps including emission above $2\sigma$." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure fluxes in elliptical apertures and convert to luminosities**: Elliptical apertures on 9 regions in CO-resolution moment-0 maps; L' formula from Wilson 2008  
  > "We place elliptical apertures around each of the 9 brightest regions to measure the total $\ensuremath{\mathrm{HCN}}$, $\ensuremath{\mathrm{HNC}}$, $\ensuremath{\mathrm{HCO^+}}$, and $\ensuremath{\mathrm{CO}}$ fluxes" (3 The brightest regions)
   - assumption: D_L = 22 Mpc, z = 0.005477  
  > "$D_L=22\ensuremath{\, \mathrm{Mpc}}$ is the distance" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute line ratios and compare with PDR models**: Luminosity ratios per region; pixel ratio maps with 3 sigma cut; HNC/HCN compared to Kazandjian 2015 mechanical-heating models  
  > "In addition, we include only pixels with a $3\sigma$ detection of both molecular transitions in the moment-0 maps." (4 Line Ratios)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2: calibration, uvcontsub, imaging, moments  
  > "We reduce these data using the Common Astronomy Software Applications package version 4.2." (2 Observations)
- **CPROPS** : size of pre-SSC (from Johnson 2015)  
  > "the size of pre-SSC as measured using the CPROPS program (cite: rosolowsky2006) is $\sim 0.66'' \times 0.55''$" (3)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L_HCN/L_CO NGC 4038 | 0.083 | 0.001 | dimensionless | 4 | $0.083 \pm 0.001$ |
| L_HCN/L_CO NGC 4039 | 0.068 | 0.004 | dimensionless | 4 | $0.068 \pm 0.004$ |
| L_HNC/L_HCN range | 0.25-0.38 | not stated | dimensionless | 4 | ranging from $\sim 0.25 - 0.38$ |
| L_HCN/L_HCO+ NGC 4038 | 1.019 | 0.008 | dimensionless | 4 | $1.019 \pm 0.008$ |
| HCN flux NGC 4038 | 14.32 | 0.08 | Jy km/s | 3 | $14.32 \pm 0.08$ |
| Fraction of HCN emission in bright regions | ~68% | not stated | percent | 3 | $\sim 68
\%$ of the total $\ensuremath{\mathrm{HCN}}$ emission originates from the brightest regions of the Antennae |

## Qualitative findings

- HNC/HCN consistent with mechanical heating >5% of PDR surface heating  
  > "Our measured line ratios are consistent with at least some ($>5\%$) contribution of mechanical heating towards the total heating budget" (5.4)

## Claim tuples

- H: Dense gas fraction is higher in nuclei than overlap region | E: HCN/CO luminosity ratios in 9 regions | R: 0.083 and 0.068 in nuclei vs <0.053 elsewhere | F: Higher pressure from stellar potential in nuclei | **supported**
- H: Mechanical heating affects HNC/HCN | E: Compare ratios to Kazandjian 2015 PDR models | R: HNC/HCN 0.25-0.38, varies <1.5x | F: Mechanical heating >=5% of PDR surface heating | **supported**
- H: Cosmic ray rate explains lower HCN/HCO+ in overlap region | E: Compare ratio to supernova surface density | R: No clear trend; NGC 4039 inconsistent | F: Possible but unconfirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): HNC is weak; 2 sigma clipping a larger fraction of peak; CO interferometric map misses flux  
  > "Line ratios involving the $\ensuremath{\mathrm{HNC}}$ line may be somewhat more uncertain as this is the weakest line" (2 Observations)
- Caveat (inferred, ours): Mechanical heating inference relies on a single model grid
- Caveat (inferred, ours): CO missing flux (~65% recovered) biases HCN/CO
- Caveat (inferred, ours): No excitation analysis; ratios degenerate with excitation and abundance

## Reproducibility

- Data public (paper): ALMA data cited by project code 2012.1.00185.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00185.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CO J=1-0 OVRO cube
- Missing: aperture definitions
- Missing: line-free channel ranges
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Imaging parameters mostly given but apertures, channel ranges and CO data are not.
- Rediscovery candidate: no, Needs the external OVRO CO map and unspecified apertures.

## Links

- Method: (cite: wilson2008) (Luminosity formula)
- Companion: (cite: schirm2014) (CO non-LTE analysis of the Antennae)
- Companion: (cite: wilson2003) (CO J=1-0 map and cloud catalogue)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 43,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
