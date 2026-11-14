# The Formation Conditions of the Wide Binary Class 0 Protostars within BHR 71

`2019ApJ...870...81T` | The Astrophysical Journal 2019 | first author: Tobin, John J. | arXiv: 1811.03059 | DOI: 10.3847/1538-4357/aaef87

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: What physical process (rotational vs turbulent fragmentation) formed the wide Class 0 binary IRS1/IRS2 in BHR71?  
  > "With this dataset, we aim to determine what physical process(es) lead to the formation of at least two protostars in this system." (Introduction)
- Target **BHR71 IRS1 and IRS2**: coordinates _not stated_; z/distance 200 pc  
  > "two Class 0 protostars (cite: andre1993) separated by $\sim$16$''$ (3200 AU; 200 pc distance)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00518.S
- bands: Band 6, central tuning 225 GHz  
  > "The observations were conducted in band 6, with a central tuning frequency of 225 GHz." (2.3 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array, ACA, Total Power  
  > "BHR71 was observed by the ALMA 12m array, the ALMA Compact Array (ACA), and the Total Power Array (TPA)" (2.3 ALMA Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: C18O 1.7x1.5 arcsec; continuum 1.3x1.2 arcsec  
  > "Continuum | 232.5 | 14.6, 18.8 | ... | 0.00087 Jy beam$^{-1}$ | 1.3$\times$1.2 | Y" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~62 s per mosaic point (12m); ACA 12.3 min on-source  
  > "Each mosaic point was observed for $\sim$62 seconds" (2.3 ALMA Observations)
- observing dates: ACA 2014 May 19; 12m 2015 Jan 17; TP 2015 May 2  
  > "The 12m array observations were conducted on 2015 January 17 in a 14-point rectangular mosaic" (2.3 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: C18O J=2-1 (219.560354 GHz)
- Line: N2D+ J=3-2 (231.321828 GHz)
- Line: 13CO J=2-1 (220.398684 GHz)
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **Parkes**: NH3 (1,1) map, 60 arcsec beam  
  > "The usable surface of the Parkes dish is 55m at 1.3 cm, resulting in a beam size of $\sim$60$''$" (2.1 Parkes Radio Telescope)
- Other facility **ATCA**: NH3 and 1.3 cm continuum  
  > "BHR71 was observed with ATCA during 2012 in the EW367 configuration and H214 configuration, project C2665." (2.2 ATCA Observations)
- Other facility **Herschel**: PACS/SPIRE photometry 70-500 um  
  > "We obtained the *Herschel* observations toward BHR71 as part of the program OT1_jtobin_1." (2.6 Herschel)
- Other facility **Spitzer**: IRAC/MIPS/IRS data  
  > "BHR71 was observed with the *Spitzer Space Telescope* using the IRAC (cite: fazio2004), MIPS (cite: rieke2004), and IRS instruments (cite: houck2004)." (2.5 Spitzer)
- External data: MIPS 24 um photometry and 3 mm flux  
  > "The MIPS 24 $\mu$m photometry for IRS1 and IRS2 were presented in (cite: chen2008)" (2.5 Spitzer) [from (cite: chen2008)]
- External data: Envelope mass 4.6 Msun within 0.05 pc from 8 um extinction  
  > "an envelope mass of $\sim$4.6 M$_{\ensuremath{\odot}}$ determined for the radius of 0.05 pc from 8 $\mu$m extinction from (cite: tobin2010)" (5.1) [from (cite: tobin2010)]

## Processing

### Calibration

- pipeline or manual: 12m manual calibration by NAASC; ACA pipeline; both with reduction scripts  
  > "The observations were manually calibrated by T. Hunter at the North American ALMA Science Center (NAASC) using CASA version 4.3.1" (2.3 ALMA Observations)
- casa version: 4.3.1 (12m, TP), 4.2.2 (ACA), imaging 4.4, combination 4.6.0  
  > "The data were then imaged using the *clean* task in CASA 4.4." (2.3 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-cal on continuum, applied to line basebands  
  > "We performed both phase and amplitude self-calibration on the data." (2.3 ALMA Observations)

### Imaging

- task: CASA clean, interactive  
  > "We used interactive cleaning for the continuum and spectral line cubes." (2.3 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Manual masks per channel  
  > "we manually drew masks around the emission in each velocity channel" (2.3 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m+ACA concat, then feather with TP following CASA M100 guide  
  > "We then followed the CASA guide for M100 to combine the 12m+ACA and TPA data using the *feather* task." (2.3 ALMA Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: continuum 0.00087 Jy/beam; C18O 0.029 Jy/beam  
  > "Continuum | 232.5 | 14.6, 18.8 | ... | 0.00087 Jy beam$^{-1}$" (Table 1)

### Inherited from earlier work

- Combination procedure for 12m+ACA+TP  
  > "We then combined the $^{12}$CO, $^{13}$CO, C$^{18}$O, and N$_2$D$^+$ data using the methods outlined in the CASA guide for M100" (2.3 ALMA Observations) [from CASA guide for M100]
- IRAC photometry method  
  > "using same the methods outlined for the protostar BHR7-MMS in (cite: tobin2018)" (2.5 Spitzer) [from (cite: tobin2018)]

### Not stated but needed to reproduce (our reading)

- clean weighting/robust, cell and image size
- multiscale/threshold settings
- self-cal solints and reference
- continuum-free channels / continuum subtraction
- flux calibrator for ALMA
- CLASS hyperfine fit settings
- moment-map clipping thresholds
- target coordinates

## Analysis recipe

1. **Continuum flux and mass**: Sigma-clipped 3 sigma map, circular apertures; optically thin dust mass  
  > "we generated a sigma-clipped map, where pixels below the 3$\sigma$ level ($\sigma$=0.68 mJy) are set to zero" (3.2)
   - software: CASA
   - assumption: kappa1.3mm 0.899 cm2/g (Ossenkopf & Henning), gas:dust 100, Td 20 K (34 K for IRS1 alt.)  
  > "We assume a dust temperature of 20 K for IRS1 and IRS2" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
2. **Line kinematics**: Hyperfine fits of N2D+ in CLASS; moment maps, high-velocity integrated maps and PV cuts for C18O  
  > "The kinematic structure is derived from the N$_2$D$^+$ data using the CLASS hyperfine fitting routines" (4.2)
   - software: CLASS
   - fitting: single-component hyperfine fit  
  > "These appear in the hyperfine fits as broader linewidth because a single velocity component is adopted in the fitting process." (Hyperfine Fits)
   - validation: two-component fit tested in one region  
  > "When we include a second component to the fit, we do find that the linewidths are indeed lower for each velocity component." (Hyperfine Fits)
3. **Rotational support beta_rot**: beta_rot = 55.2 R^3 M^-1 vgrad^2 following Chen et al. 2007  
  > "We follow the method outlined by (cite: chen2007) which calculates the rotational energy" (5.1)
   - assumption: angular momentum conserved from 1.2 km/s/pc core gradient; p=1.5  
  > "we assume that angular momentum is conserved and the velocity gradient is more rapid at a radius 0.016 pc." (5.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2, 4.3.1, 4.4, 4.6.0: calibration, clean, concat, feather, Gaussian fits  
  > "We used the *clean* task to image the combined dataset in the same manner as the individual datasets." (2.3 ALMA Observations)
- **CLASS/GILDAS** : NH3 and N2D+ hyperfine fitting  
  > "The FITS cube was then ingested into CLASS, which is part of the GILDAS" (2.1 Parkes Radio Telescope)
- **MIRIAD** : ATCA calibration and imaging  
  > "The data were calibrated and edited using the Australian Telescope National Facility (ATNF) version of the MIRIAD software package" (2.2 ATCA Observations)
- **starfinder** : Herschel PSF photometry  
  > "We used the IDL program *starfinder* (cite: diolaiti2000) to perform PSF photometry." (2.6 Herschel)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IRS1 Lbol | 14.7 | not stated | Lsun | 0 | IRS1, has L$_{\rm bol}$=14.7 L$_{\ensuremath{\odot}}$ and a bolometric temperature (T$_{\rm bol}$) = 68 K |
| IRS2 Lbol | 1.7 | not stated | Lsun | 0 | IRS2 has L$_{\rm bol}$ = 1.7 L$_{\ensuremath{\odot}}$ and T$_{\rm bol}$=38 K |
| ALMA 1.3 mm flux IRS1 | 1.28 | 0.01 | Jy | 1 | measuring a flux density of 1.28$\pm$0.01 Jy |
| ALMA 1.3 mm flux IRS2 | 0.12 | 0.005 | Jy | 1 | measuring a flux density of 0.12$\pm$0.005 Jy |
| Combined mass (IRS1 at 34 K) | 0.7 | not stated | Msun | 1 | making the combined mass 0.7 M$_{\ensuremath{\odot}}$ considering the likely higher temperature for IRS1 |
| Outflow PA IRS1, IRS2 | 174, -31 | not stated | deg | 0 | we measure outflow position angles of 174$^\circ$ and -31$^\circ$ for IRS1 and IRS2, respectively |
| beta_rot upper limit at 3200 AU | 0.006 | not stated | dimensionless | 3 | we calculate an upper limit to $\beta_{\rm rot}$ = 0.006 |
| Parkes velocity gradient | 1.2 | not stated | km/s/pc | 0 | The resulting velocity gradient orthogonal to the outflow direction is 1.2 km s$^{-1}$ pc$^{-1}$ |

## Qualitative findings

- C18O rotation on <1000 AU scales is in opposite directions around IRS1 and IRS2, with same systemic velocity  
  > "the C$^{18}$O kinematics reveal that the rotation on scales $<$1000 AU around IRS1 and IRS2 are in *opposite* directions." (abstract)

## Claim tuples

- H: Was the binary formed by rotational fragmentation? | E: Parkes/ATCA/ALMA kinematics and beta_rot | R: beta_rot<=0.006; opposite rotation; no velocity offset | F: Rotational fragmentation unlikely | **supported**
- H: Was it turbulent fragmentation? | E: Comparison with simulations and disordered velocity fields | R: consistent but not proven | F: Turbulent fragmentation most likely | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Thermal Jeans fragmentation not clearly favored (Jeans length ~8400 AU)  
  > "Thus, thermal Jeans fragmentation is not clearly a favored mechanism on its own to form the binary system" (5.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow influence and line-of-sight geometry make interpretation uncertain; higher resolution/sensitivity needed  
  > "A factor of 2-4 increases in both sensitivity and resolution would solidify this result." (5.4)
- Caveat (inferred, ours): Rotation directions from C18O at ~1.5 arcsec resolution with short integration
- Caveat (inferred, ours): Single-component hyperfine fits despite two components
- Caveat (inferred, ours): Mass assumptions (T, kappa) uncertain
- Caveat (inferred, ours): beta_rot is an upper limit extrapolated assuming angular momentum conservation

## Reproducibility

- Data public (paper): ALMA project code given; ALMA data cited with ADS/JAO  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00518.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: line-free channels
- Missing: self-cal parameters
- Missing: CLASS fit settings
- Missing: target coordinates
- Data volume (inferred): ~50-100 GB (12m+ACA+TP, 4 lines)
- Score (inferred): 4/5, ALMA data identified and steps described, but imaging parameters mostly missing and multi-facility.
- Rediscovery candidate: no, Interactive cleaning and many unstated parameters; key results depend on non-ALMA data.

## Links

- Method: (cite: chen2007) (beta_rot formula)
- Method: (cite: tobin2013) (N2D+ hyperfine fitting)
- Companion: (cite: chen2008) (earlier ATCA/Spitzer study of BHR71)
- Related: cores2disks
- Related: HOPS

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 37,
  "rate": 0.536
 },
 "evidence_ok": true
}
```
