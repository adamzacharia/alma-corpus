# Discovery of Shocked Molecular Clouds Associated with the Shell-type Supernova Remnant RX J0046.5-7308 in the Small Magellanic Cloud

`2019ApJ...881...85S` | The Astrophysical Journal 2019 | first author: Sano, H. | arXiv: 1904.04836 | DOI: 10.3847/1538-4357/ab2ade

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism, other
- Question: Are molecular and atomic clouds physically associated with the SMC shell-type SNR RX J0046.5-7308, and what are the SNR age, progenitor type and GMC LIRS 36A conditions?  
  > "we report the first detection of molecular clouds and atomic gas associated with the SMC SNR RX J0046.5$-$7308 using the ASTE, Mopra, and ASKAP." (Introduction)
- Target **RX J0046.5-7308 (SNR B0044-73.4, DEM S32) and GMC LIRS 36A**: coordinates LIRS 36 center 00h46m41.50s, -73d06m00s (J2000)  
  > "centered at the GMC LIRS 36 \[($\alpha_\mathrm{J2000}$, $\delta_\mathrm{J2000}$) $=$ ($00^\mathrm{h}46^\mathrm{m}41$$''$$50$, $-73\ensuremath{^\circ}06\ensuremath{'}00''$)\]" (2.1 CO); "$\sim60$ kpc for the SMC, (cite: 2005MNRAS.357..304H)" (Introduction); z/distance ~60 kpc (SMC)  
  > "centered at the GMC LIRS 36 \[($\alpha_\mathrm{J2000}$, $\delta_\mathrm{J2000}$) $=$ ($00^\mathrm{h}46^\mathrm{m}41$$''$$50$, $-73\ensuremath{^\circ}06\ensuremath{'}00''$)\]" (2.1 CO); "$\sim60$ kpc for the SMC, (cite: 2005MNRAS.357..304H)" (Introduction); distance from Hilditch et al. 2005 (cite: 2005MNRAS.357..304H)  
  > "centered at the GMC LIRS 36 \[($\alpha_\mathrm{J2000}$, $\delta_\mathrm{J2000}$) $=$ ($00^\mathrm{h}46^\mathrm{m}41$$''$$50$, $-73\ensuremath{^\circ}06\ensuremath{'}00''$)\]" (2.1 CO); "$\sim60$ kpc for the SMC, (cite: 2005MNRAS.357..304H)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00196.S
- bands: Band 3 (86–116 GHz) and Band 6 (211–275 GHz)  
  > "ALMA Band 3 (86–116 GHz) and Band 6 (211–275 GHz)" (2.1 CO)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: three antennas of the total power (TP) array, OTF mapping  
  > "were conducted in June and 2016 August using three antennas of a total power (TP) array." (2.1 CO)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~29.1'' (12CO 2-1), ~30.3'' (13CO 2-1)  
  > "The beam size is $\sim$$29.1''$ for $^{12}$CO($J$ = 2–1) and is $\sim$$30.3''$ for $^{13}$CO($J$ = 2–1)" (2.1 CO)
- max recoverable scale: _not stated_
- sensitivity: ~0.011 K (12CO) and ~0.014 K (13CO) at 0.32 km/s  
  > "are $\sim$0.011 K and $\sim$0.014 K at the velocity resolution of 0.32 km s$^{-1}$, respectively." (2.1 CO)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival, PI J. Roman-Duval  
  > "we used archival CO datasets obtained with ALMA" (2.1 CO)
- Line: 12CO J=2-1 (230.538000 GHz)
- Line: 13CO J=2-1 (220.398684 GHz)
- Other facility **ASTE 10 m**: 12CO(3-2) map  
  > "Observations of $^{12}$CO($J$ = 3–2) line emission at 345.795990 GHz were carried out during 2014 August by using the ASTE 10 m radio telescope" (2.1 CO)
- Other facility **Mopra 22 m**: 12CO(1-0) map  
  > "using the Mopra 22 m radio telescope of the Commonwealth Scientific and Industrial Research Organization (CSIRO)" (2.1 CO)
- Other facility **ASKAP**: HI data  
  > "The Hi data were obtained using the ASKAP" (2.2 Hi)
- Other facility **Chandra**: archival X-ray imaging and spectra  
  > "We used archival X-ray data obtained by using *Chandra*" (2.3 X-rays)
- External data: HI data cubes from ASKAP  
  > "We used Hi data published by (cite: 2018NatAs...2..901M) and (cite: 2019MNRAS.483..392D)." (2.2 Hi) [from (cite: 2018NatAs...2..901M); (cite: 2019MNRAS.483..392D)]
- External data: X_CO = 7.5e20 (K km/s)^-1 cm^-2  
  > "we used $X_\mathrm{CO} = 7.5 \times 10^{20}$ (K km s$^{-1}$)$^{-1}$ cm$^{-2}$ (cite: 2017ApJ...844...98M)" (3.2) [from (cite: 2017ApJ...844...98M)]
- External data: SMC abundances for X-ray fits  
  > "The other elements were fixed to the SMC values in the literature (cite: 2019AJ....157...50D)." (3.6) [from (cite: 2019AJ....157...50D)]

## Processing

### Calibration

- pipeline or manual: archive pipeline product dataset used  
  > "We utilized the product dataset through the pipeline processes" (2.1 CO)
- casa version: CASA 4.5.3  
  > "package version 4.5.3 with the Pipeline version r36660" (2.1 CO)
- pipeline version: r36660 (Pipeline-Cycle3-R4-B)  
  > "Pipeline version r36660 (Pipeline-Cycle3-R4-B)" (2.1 CO)
- archive products used as is: yes, pipeline product  
  > "We utilized the product dataset through the pipeline processes" (2.1 CO)
- flux calibrator: _not stated_
- flux scale uncertainty: relative calibration error 3% (ALMA), 5% (ASTE)  
  > "assuming the relative calibration error of $3\%$ for the ALMA data and $5\%$ for the ASTE data" (3.3)
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
- smoothing: spectra smoothed to ~30'' beam of ALMA 13CO  
  > "Each spectrum was smoothed to match the beam size of the ALMA $^{13}$CO($J$ = 2–1) data" (3.3)
- final beam: ~29.1'' / 30.3''  
  > "The beam size is $\sim$$29.1''$ for $^{12}$CO($J$ = 2–1)" (2.1 CO)
- final rms: 0.011 K and 0.014 K  
  > "$\sim$0.011 K and $\sim$0.014 K at the velocity resolution of 0.32 km s$^{-1}$" (2.1 CO)

### Inherited from earlier work

- Abundance ratios [12CO/H2]=8e-6 and [12CO/13CO]=35 adopted from earlier GMC studies  
  > "following the previous GMC studies of SMC N27 and N83C (cite: 1999A&A...344..817H; 2017ApJ...844...98M)" (3.3) [from (cite: 1999A&A...344..817H; 2017ApJ...844...98M)]
- LVG method  
  > "we performed the large velocity gradient (LVG) analysis (cite: 1974ApJ...189..441G; 1974ApJ...187L..67S)" (3.3) [from (cite: 1974ApJ...189..441G; 1974ApJ...187L..67S)]

### Not stated but needed to reproduce (our reading)

- LVG code and its grid ranges for n(H2) and Tkin
- How ALMA TP cubes were regridded, continuum-subtracted and how line intensities were measured
- Spectrum extraction region for LIRS 36A
- Whether ALMA K scale uses main-beam efficiency
- How asymmetric uncertainties were derived from the ratio constraints

## Analysis recipe

1. **Measure CO line ratios toward LIRS 36A**: Smooth ASTE and ALMA spectra to ~30'' and take intensity ratios  
  > "Each spectrum was smoothed to match the beam size of the ALMA $^{13}$CO($J$ = 2–1) data ($\Delta\theta \sim$$30''$)." (3.3)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive n(H2) and Tkin by LVG**: LVG analysis of three line ratios with fixed X/(dv/dr)  
  > "we adopt $X/(dv/dr) = 4 \times 10^{-5}$ (km s$^{-1}$ pc$^{-1}$)$^{-1}$" (3.3)
   - parameter: dv/dr = 1.2 km/s / 5.4 pc = 0.22 km/s/pc  
  > "$dv/dr$ = 1.2 km s$^{-1}$ / 5.4 pc = 0.22 km s$^{-1}$ pc$^{-1}$" (3.3)
   - assumption: [12CO/H2]=8e-6, [12CO/13CO]=35  
  > "\[$^{12}$CO/H$_2$\] $= 8 \times 10^{-6}$ and \[$^{12}$CO/$^{13}$CO\] = 35" (3.3)
   - fitting: Intersection of ratio curves with 1 sigma noise and calibration errors  
  > "The errors—as shown in shaded areas for each ratio—are estimated with a $1\sigma$ noise level for each spectrum" (3.3)
   - validation: Roughly consistent with Nikolic et al. 2007  
  > "which are roughly consistent with previous studies (cite: 2007AA...471..561N)" (3.3)

## Software

- **CASA** 4.5.3: ALMA pipeline processing  
  > "package version 4.5.3 with the Pipeline version r36660" (2.1 CO)
- **CIAO** 4.10: Chandra data reduction and imaging  
  > "software version 4.10 with CALDB 4.7.8 for data reduction and imaging" (2.3 X-rays)
- **XSPEC** 12.10.0e: X-ray spectral fits  
  > "All X-ray spectral fits are performed with XSPEC version 12.10.0e." (2.3 X-rays)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| n(H2) of LIRS 36A | 1500 | +600/-300 | cm^-3 | 2 | $n$(H$_2) = 1500^{+600}_{-300}$ cm$^{-3}$ |
| Tkin of LIRS 36A | 72 | +50/-37 | K | 2 | $T_\mathrm{kin} = 72^{+50}_{-37}$ K |
| R_CO32/CO21 | 0.86 | not stated | dimensionless | 1 | (hereafter $R_\mathrm{CO32/CO21}$) $\sim$0.86 |
| R_13CO21/CO21 | 0.17 | not stated | dimensionless | 1 | (hereafter $R_\mathrm{13CO21/CO21}$) $\sim$0.17 |
| SNR dynamical age | 26000 | +1000/-2000 | yr | 0 | $t_\mathrm{dyn} = 26000_{-2000}^{+1000}$ yr |

## Qualitative findings

- Eight CO clouds along X-ray shell; clouds A, B, F, G show R(3-2/1-0)>1.2 and are shock-heated  
  > "The four molecular clouds A, B, F, and G show high intensity ratios of $R_\mathrm{CO32/CO10} > 1.2$ without infrared sources and/or massive stars." (5 Conclusions)

## Claim tuples

- H: GMC LIRS 36A is heated by UV from LIN 78 rather than the SNR | E: LVG analysis with ALMA 12CO/13CO(2-1) and ASTE 12CO(3-2) | R: n=1500 cm^-3, Tkin=72 K | F: High Tkin is due to the massive exciting star LIN 78 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): LVG solution has large uncertainties and few constraints
- Caveat (inferred, ours): Total-power data at ~30'' beam smooths cloud structure
- Caveat (inferred, ours): LVG and heating-source interpretation not tested against alternatives

## Reproducibility

- Data public (paper): archival ALMA data from project 2015.1.00196.S  
  > "we used archival CO datasets obtained with ALMA" (2.1 CO)
- Products in archive: _not stated_
- Missing: LVG code and grid
- Missing: ALMA spectrum extraction details
- Data volume (inferred): ~1-5 GB (TP cubes)
- Score (inferred): 3/5, ALMA part is small and LVG settings are loosely specified, though data are public.
- Rediscovery candidate: no, LVG recipe lacks code and parameter details.

## Links

- Companion: (cite: 2007AA...471..561N) (Previous LIRS 36 physical conditions)
- Related: MAGMA-SMC

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 64,
  "stated": 37,
  "rate": 0.578
 },
 "evidence_ok": true
}
```
