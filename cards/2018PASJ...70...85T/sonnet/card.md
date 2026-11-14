# ALMA view of the circumnuclear disk of the Galactic Center: tidally disrupted molecular clouds falling to the Galactic Center

`2018PASJ...70...85T` | Publications of the Astronomical Society of Japan 2018 | first author: Tsuboi, Masato | arXiv: 1806.10246 | DOI: 10.1093/pasj/psy080

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism
- Question: What are the size, kinematics and molecular gas mass of the Galactic Center CND, and what anomalous molecular clouds in its surroundings are feeding it?  
  > "The more detailed gas kinematics of the wider area including the CND must provide key information to address the issues above mentioned." (Introduction)
- Target **Circum-Nuclear Disk (CND) of Sgr A***: coordinates _not stated_; z/distance 8 kpc  
  > "The distance to the Galactic Center is assumed to be 8 kpc in this paper" (Introduction); distance from assumed, e.g. Ghez; Gillessen; Schodel2009; Boehle  
  > "The distance to the Galactic Center is assumed to be 8 kpc in this paper" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00080.S, 2012.1.00543.S
- bands: _not stated_
- frequencies and spectral setup: Original velocity resolution 1.7 km/s (488 kHz); lines near 86-98 GHz  
  > "The original velocity resolution is $1.7$ km s$^{-1}$(488 kHz)." (Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m array 136-pointing mosaic plus 7-m array (ACA) 68-pointing mosaic  
  > "We have produced a 136 pointing mosaic of the 12-m array and a 68 pointing mosaic of the 7-m array (ACA)" (Observation and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: (2.3''-2.5'')x(1.6''-1.8''), PA~-30 deg, natural weighting; CS 7-6: 4.3''x2.7''  
  > "The resultant maps have angular resolutions of $(2.3\ensuremath{''}-2.5\ensuremath{''})\times (1.6\ensuremath{''}-1.8\ensuremath{''}), PA\sim-30^\circ$ using “natural weighting"" (Observation and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: ~0.002 Jy/beam x 5 km/s, or ~0.35 K km/s  
  > "The rms noise levels of the resultant maps are $\sim0.002$ Jy/beam $\times$ 5 km s$^{-1}$ or $\sim 0.35$ K km s$^{-1}$." (Observation and Data Reduction)
- time on source: _not stated_
- observing dates: time span of one year and seven months  
  > "Because the observation has a large time span of one year and seven months" (Observation and Data Reduction)
- pi or archival as stated: CS 7-6 data are archival from JVO portal; the main data are PI Tsuboi  
  > "obtained from the JVO portal of NAOJ (ALMA#2012.1.00543.S)" (Observation and Data Reduction)
- Line: CS J=2-1 (97.980953 GHz)
- Line: SiO v=0 J=2-1 (86.846995 GHz)
- Line: H13CO+ J=1-0 (86.754288 GHz)
- Line: C34S J=2-1 (96.41950 GHz)
- Line: CH3OH 2_{1,1}-1_{1,0} A-- (97.582808 GHz)
- Line: CS J=7-6 (342.882857 GHz)
- Line: H42alpha recombination line (85.6884 GHz)
- Other facility **JCMT**: 670 GHz continuum map for comparison  
  > "the continuum map at 670 GHz by JCMT for comparison" (Results)
- External data: 100 GHz continuum map tracing the GCMS (contours in Fig. 1)  
  > "The contours in the figure show the continuum emission at 100 GHz, which mainly traces the GCMS" (Results) [from (cite: Tsuboi2016)]
- External data: H13CO+ fractional abundance 4e-10 for the CND  
  > "$X\mathrm{(H^{13}CO^{+} )}=4\times10^{-10}$ ((cite: Amo))" (Table 1) [from (cite: Amo)]
- External data: CND kinetic temperatures ~200 K (log N~4.5) and 300-500 K  
  > "the moderately dense molecular gas in the CND with $\log{N_\mathrm{H_2}}\sim4.5$ has the kinetic temperatures of $T_{\mathrm{K}}\sim200$ K" (4.2 Physical Properties) [from (cite: Requena-Torres12)]
- External data: Magnetic field B~4 mG from OH maser Zeeman effect  
  > "The magnetic field strength around the CND is as strong as $B\sim 4$ mG" (4.4) [from (cite: Yusef-Zadeh1996)]

## Processing

### Calibration

- pipeline or manual: calibration and imaging with CASA (details not given)  
  > "The calibration and imaging of the data were performed by CASA (cite: McMullin)." (Observation and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, Neptune and Mars  
  > "The flux density scale was determined using Titan, Neptune and Mars." (Observation and Data Reduction)
- flux scale uncertainty: as large as 15 %  
  > "the flux uncertainty is as large as 15 %" (Observation and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using “natural weighting" sampling on the spatial frequency ($u-v$) plane" (Observation and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m and 7-m mosaics both observed; combination method not stated  
  > "We have produced a 136 pointing mosaic of the 12-m array and a 68 pointing mosaic of the 7-m array (ACA)" (Observation and Data Reduction)
- smoothing: spectral line images made with dV = 5 km/s (channel maps 10 km/s wide)  
  > "We made the spectral line images with $\Delta V=5$ km s$^{-1}$ of the emission lines mentioned above." (Observation and Data Reduction)
- final beam: _not stated_
- final rms: ~0.002 Jy/beam per 5 km/s  
  > "The rms noise levels of the resultant maps are $\sim0.002$ Jy/beam $\times$ 5 km s$^{-1}$" (Observation and Data Reduction)

### Inherited from earlier work

- Full data and 50MC analysis deferred to another paper  
  > "We will present the full data of the observation and the analysis about 50MC in another coming paper (Uehara et al. submitted)." (Observation and Data Reduction) [from Uehara et al. submitted (cite: Uehara)]
- H42alpha ionized gas kinematics of the mini-spiral taken from earlier work  
  > "The similar velocity shift has been observed for the WA in the H42$\alpha$ emission line (e.g. (cite: Tsuboi2017))." (3.2) [from (cite: Tsuboi2017)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (cell, image size, mask, threshold, deconvolver)
- How 12-m and ACA data were combined and primary-beam corrected
- Continuum subtraction method and line-free channels
- CASA version
- Procedure for selecting CND components (white ellipse/parallelogram) in channel maps
- Table 1 mass for AA/AB/AC: regions used and integration limits
- RADEX input grids (line width, collider, column density per velocity gradient)
- Which data volumes/execution blocks of 2012.1.00080.S were used

## Analysis recipe

1. **Make line cubes and moment maps**: CASA imaging with natural weighting, 5 km/s channels; moment 0 integrated -150 to 150 km/s; channel maps 10 km/s wide  
  > "The integrated velocity range of the panels is $V_{\mathrm{LSR}}=-150$ to $150$ km s$^{-1}$." (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive CND geometry and kinematics**: Radii from moment 0 and channel maps; rotation and radial velocity from major-axis position-velocity diagrams; Keplerian orbit overlaid  
  > "The enclosed mass of $4.3\times10^6$M$_\odot$ reproduces the observed position-velocity diagrams." (4.1)
   - parameter: inclination i~30±5 deg from aspect ratio; Vrot~100/cos i, Vrad~20/cos i  
  > "$V_{\mathrm{rot}}\sim\frac{100}{\cos i} =115\pm10$ km s$^{-1}$ and $V_\mathrm{rad}\sim\frac{20}{\cos i}=23\pm5$ km s$^{-1}$" (4.1)
   - fitting: _not stated_
   - validation: consistency with previous observations  
  > "The derived values are consistent with those in the previous observations" (4.1)
3. **Estimate density and excitation with LVG**: RADEX LVG for CS 2-1 and 7-6 at TK=200 K, comparing observed peak brightness temperatures  
  > "We calculate the brightness and excitation temperatures of the CS $J=2-1$ and CS $J=7-6$ emission lines using the RADEX LVG program (cite: VanderTak)" (4.2)
   - software: RADEX
   - assumption: TK=200 K; X(CS)=1e-8; DeltaV=50 km/s; Tex(CS 2-1)=TK  
  > "Assuming that the CS fractional abundance and the velocity width of the CS emission line are $X(\mathrm{CS})=10^{-8}$ and $\Delta V=50$ km s$^{-1}$" (4.2)
   - fitting: _not stated_
   - validation: LVG column density consistent with LTE value  
  > "This is consistent with the typical molecular column density based on the LVG model" (4.3.1)
4. **Derive LTE gas masses**: Optical depth from CS/C34S ratio, optical-depth correction, LTE column density and mass summed over CND/anomalies  
  > "the optical thickness of the CS emission line $\tau$, is estimated from the line intensity ratio of the CS and C$^{34}$S emission lines" (4.3.1)
   - assumption: CS/C34S = 22.35, equal filling factors and Tex, mu=2.8, X(CS)=1e-8, A21=2.2e-5 s-1  
  > "$\frac{X(\mathrm{CS})}{X(\mathrm{C^{34}S})}=22.35$" (4.3.1)
   - fitting: _not stated_
   - validation: cross-check with CS 7-6 and H13CO+ masses  
  > "the consistency in the derived gas masses from the CS and H$^{13}$CO$^{+}$ observations suggests" (4.3.2)

## Software

- **CASA** : calibration, imaging and analysis  
  > "The calibration and imaging of the data were performed by CASA (cite: McMullin)." (Observation and Data Reduction)
- **RADEX** : LVG excitation/brightness temperature models for CS  
  > "using the RADEX LVG program (cite: VanderTak)" (4.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CND inner radius | 1.5 | not stated | pc | 2 | $R_{\mathrm{in}}\sim1.5$ and $R_{\mathrm{out}}\sim2$ pc |
| CND outer radius | 2 | not stated | pc | 2 | $R_{\mathrm{in}}\sim1.5$ and $R_{\mathrm{out}}\sim2$ pc |
| CND inclination | 30 | ±5 | deg | 2 | The inclination angle of the CND is estimated to be $i\sim30\pm5^{\circ}$ |
| CND rotation velocity | 115 | ±10 | km/s | 2 | $V_{\mathrm{rot}}\sim\frac{100}{\cos i} =115\pm10$ km s$^{-1}$ |
| CND radial velocity | 23 | ±5 | km/s | 2 | $V_\mathrm{rad}\sim\frac{20}{\cos i}=23\pm5$ km s$^{-1}$ |
| Enclosed mass reproducing PV diagrams | 4.3e6 | not stated | Msun | 2 | The enclosed mass of $4.3\times10^6$M$_\odot$ reproduces the observed position-velocity diagrams. |
| CND mean H2 density (LVG) | 2.2e5 | not stated | cm^-3 | 3 | $n_{\mathrm{H_2}}\sim 2.2\times10^5$ cm$^{-3}$ |
| CS 7-6 excitation temperature in CND | 18-25 | not stated | K | 3 | $T_{\mathrm{ex}}$(CS $J=7-6$)$=18-25$ K |
| CS 2-1 optical depth, CND | 0.63 | not stated | dimensionless | 4 | $\bar{\tau}\mathrm{(CND)}\sim0.63$ |
| LTE mass of CND from CS 2-1 | 3.1e4 (Tex/200) | not stated | Msun | 4 | $M{\mathrm{_{LTE}(CND)}}=3.1\times10^4(T_{\mathrm{ex}}/200)M_\odot$ |
| LTE mass of CND from H13CO+ | 1.5e4 (Tex/200) | not stated | Msun | 4 | $M_{\mathrm{LTE}}=1.5\times10^4(T_\mathrm{ex}/200) M_\odot$ |
| LTE mass of Anomaly A | 1.3e4 (Tex/200) | not stated | Msun | 4 | $1.3\times10^4(T_{\mathrm{ex}}/200)$ |
| Alfven velocity in AA | 15-20 | not stated | km/s | 0 | The Alfvén velocity is estimated to be $V_\mathrm{A}\sim15-20$ km s$^{-1}$. |

## Qualitative findings

- AA lies adjacent to the Western Arc but rotates opposite to the CND, indicating a cloud falling in and tidally disrupted.  
  > "However, the cloud is seen to rotate in the opposite direction to the CND." (abstract)
- AB connects to the tip of the Eastern Arm with matching velocity to the ionized gas.  
  > "The velocity of this cloud is consistent with that of the ionized gas in the EA." (abstract)

## Claim tuples

- H: What are the CND size, kinematics and mass? | E: Moment, channel and PV analysis of CS, SiO, H13CO+ and CS 7-6, plus LTE mass | R: Rin~1.5 pc, Rout~2 pc, Vrot~115, Vrad~23 km/s, M_LTE~3e4 Msun | F: Consistent with previous observations but with a smaller outer radius | **supported**
- H: Do anomalous clouds feed the CND? | E: Channel maps, CH3OH/SiO shock tracers, comparison to H42alpha | R: AA and AB connect to CND/EA, with velocities inconsistent with CND rotation (AA) or matching ionized EA (AB) | F: AA and AB are infalling, tidally disrupted clouds | **partially**

## Reasoning

- Why this data: Low-J lines trace outer lower-excitation gas; ALMA sensitivity and field cover CND and surroundings  
  > "the molecular gas in the outer region would be detected better in low-$J$ molecular emission lines because of their lower excitation" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Tex for anomalies may be lower than 200 K, so masses are uncertain; flux uncertainty 15%  
  > "However, the excitation temperature for these components may be lower than $T_{\mathrm{ex}}=200$ K (see figure 10b)." (4.3.1)
- Caveat (inferred, ours): Infall interpretation rests on projected morphology and velocity; no 3D orbit modelling
- Caveat (inferred, ours): Kinematic parameters read by eye from PV diagrams without fits or uncertainties from a fit
- Caveat (inferred, ours): Assumed Tex, abundances and equal filling factor dominate mass uncertainty
- Caveat (inferred, ours): Mass from CS 2-1 differs by 2x from other tracers

## Reproducibility

- Data public (paper): CS 7-6 data retrieved from JVO portal; both projects cited by code  
  > "The later data are retrieved from the JVO portal (http://jvo.nao.ac.jp/portal) operated by the National Astronomical Observatory of Japan (NAOJ)." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Explicit component-selection regions
- Missing: RADEX grid settings
- Data volume (inferred): Large: ~200-pointing mosaics (12-m+ACA) at 5 lines plus archival Band 7 mosaic; hundreds of GB raw
- Score (inferred): 3/5, Data public and formulas for masses given, but imaging and selection details are missing and kinematics are by-eye.
- Rediscovery candidate: no, Processing recipe incomplete and key results depend on by-eye component selection.

## Links

- Method: (cite: VanderTak) (RADEX LVG code)
- Method: (cite: McMullin) (CASA)
- Companion: Uehara et al. submitted (cite: Uehara) (Full data and 50MC analysis)
- Companion: (cite: Tsuboi2017) (H42alpha mini-spiral kinematics)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 70,
  "stated": 40,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
