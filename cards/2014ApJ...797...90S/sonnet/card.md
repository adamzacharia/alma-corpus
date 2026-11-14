# An Infrared-luminous Merger with Two Bipolar Molecular Outflows: ALMA and SMA Observations of NGC 3256

`2014ApJ...797...90S` | The Astrophysical Journal 2014 | first author: Sakamoto, Kazushi | arXiv: 1403.7117 | DOI: 10.1088/0004-637X/797/2/90

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the structure of the molecular gas around the two merger nuclei of NGC 3256, and the nature and driver of its high-velocity molecular gas (outflows)?  
  > "We aimed at the structure and properties of the molecular gas around the luminous merger nuclei including the high-velocity molecular gas." (Introduction)
- Target **NGC 3256**: coordinates RA 10h27m51.23s, Dec -43d54m16.6s (J2000, midpoint of the two nuclei)  
  > "NGC 3256 is an infrared-luminous merger with a bolometric luminosity of $L_{\rm bol}=4\times 10^{11} L_{\odot}$ ($D = 35$ Mpc" (Introduction); "Adopted galaxy distance (cite: Sanders03)." (Table 1); z/distance D = 35 Mpc; Vsys = 2775 km/s  
  > "NGC 3256 is an infrared-luminous merger with a bolometric luminosity of $L_{\rm bol}=4\times 10^{11} L_{\odot}$ ($D = 35$ Mpc" (Introduction); "Adopted galaxy distance (cite: Sanders03)." (Table 1); distance from Sanders et al. 2003  
  > "NGC 3256 is an infrared-luminous merger with a bolometric luminosity of $L_{\rm bol}=4\times 10^{11} L_{\odot}$ ($D = 35$ Mpc" (Introduction); "Adopted galaxy distance (cite: Sanders03)." (Table 1)

## Data provenance

- ALMA projects: 2011.0.00002.SV, 2011.0.00525.S
- bands: Band 3 (3 mm) and Band 7 (0.85 mm); SMA 1.3 mm  
  > "We observed in the 3 mm band (Band 3) and the 0.85 mm band (Band 7) each in two array configurations" (2.1 ALMA)
- frequencies and spectral setup: Band 7: 0.488 MHz channels, ~3.5 GHz per sideband; CSV Band 3 15.6 MHz channels  
  > "We used a correlator setup having 0.488 MHz channel spacing and about 3.5 GHz continuous coverage in each sideband." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, up to 23  
  > "using up to twenty-three 12 m-diameter antennas" (2.1 ALMA)
- configurations: _not stated_
- baselines: 15 m to about 370 m (Cycle 0); CSV 12-90 m  
  > "jointly covering projected baselines between 15 m and about 370 m" (2.1 ALMA)
- angular resolution: ~1'' CO(1-0), 0.8'' CO(2-1), 0.5'' CO(3-2)  
  > "up to about 1$''$ for CO(1–0), 0.8$''$ for CO(2–1), and 0.5$''$ for CO(3–2)" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~3 hr CSV; 29-34 min per Cycle 0 Band 3 execution  
  > "had about the same on-source integration time of 3 hr as our Cycle 0 observations" (2.1 ALMA)
- observing dates: 2011-2012 (Cycle 0); SMA new data 2008  
  > "Our ALMA observations in Cycle 0 were made in 2011–2012" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (115.2712 GHz)
- Line: CO J=3-2 (345.7960 GHz)
- Line: CN N=1-0 (113.4949 / 113.1688 GHz)
- Line: HCO+ J=4-3 (356.7342 GHz)
- Line: CH3CCH 6_0-5_0 (102.5480 GHz)
- Other facility **SMA**: 1.3 mm CO(2-1) and 13CO(2-1) data, 12.9 hr on-source  
  > "increasing the maximum projected baseline from 179 m to 509 m and doubling the total on-source time from 6.9 hr to 12.9 hr" (2.2 SMA)
- Other facility **HST**: optical images compared with CO  
  > "Figures 17 and 18 compare our CO images with multi-color HST images of NGC 3256." (3.4.1 HST Optical Images)
- Other facility **Spitzer**: archival IRAC images  
  > "archival infrared images of NGC 3256 taken with the Spitzer Space Telescope Infrared Array Camera" (3.4.3 Spitzer Infrared Images)
- External data: VLA 6 and 3.6 cm radio continuum images and nuclear positions  
  > "We adopt radio positions for the two merger nuclei" (2.3 Conventions) [from (cite: Neff03)]
- External data: Star formation rates of the nuclei (~15 and ~6 Msun/yr) from IR SED modeling  
  > "estimated the star formation rates of the northern and southern nuclei to be $\sim$15 and $\sim$6 $M_\odot$yr$^{-1}$, respectively" (5.3 Significance of the Outflows) [from (cite: Lira08)]
- External data: Single-dish CO(1-0) flux with 43'' beam used for recovered-flux check  
  > "recovered 76–87% of the single-dish flux measured with a 43$''$ beam (FWHM) by (cite: Aalto95)" (2.1 ALMA) [from (cite: Aalto95)]

## Processing

### Calibration

- pipeline or manual: Calibrated from raw data in a uniform manner with CASA  
  > "All ALMA data were calibrated from the raw data[^3] in a uniform manner using the CASA[^4] reduction package versions 4.0 and 4.1." (2.1 ALMA)
- casa version: CASA 4.0 and 4.1  
  > "using the CASA[^4] reduction package versions 4.0 and 4.1" (2.1 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Butler-JPL-Horizons 2012 model for Titan and Mars  
  > "we used the ‘Butler-JPL-Horizons 2012’ model for Titan and Mars in our flux calibration" (2.1 ALMA)
- flux scale uncertainty: ~10% calibration uncertainty (CO 2-1/1-0 ratio)  
  > "4.0 with $\sim$10% calibration uncertainty" (3.2.4)
- self calibration: _not stated_

### Imaging

- task: Imaging in CASA  
  > "Imaging and basic data analysis were also made in CASA." (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0, natural, or tapered depending on dataset  
  > "br= Briggs with `robust = 0`, na = natural, tp = tapered." (Table 5 notes)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: u-v domain for CSV+Cycle 0; image domain for the rest  
  > "The continuum has been subtracted from our line data in the $u$–$v$ domain for the CSV$+$Cycle 0 data and in the image domain for the rest." (2.1 ALMA)
- line free channels: Continuum from line-free channels after inspecting line widths; for high-velocity maps >750 (400) km/s from Vsys for CO (CN)  
  > "Continuum was determined more than 750 (400) km s$^{-1}$ away from $V_{\rm sys}$ for the CO (CN) lines" (3.3.1)
- primary beam correction: Fluxes corrected for primary beam (and mosaic) response, not for missing flux  
  > "These are corrected for the primary beam (and mosaic) responses but not for any missing flux in the interferometric data." (3.2.4)
- array combination: CSV and Cycle 0 Band 3 combined as a mosaic  
  > "The CSV and Cycle 0 data were combined as a mosaic because of the pointing offset." (2.1 ALMA)
- smoothing: Spectral binning to 4, 10, 20 MHz (Cycle 0 B3), 15.6 MHz (CSV+C0), 10 and 30 MHz (B7); u-v tapering for high-velocity maps  
  > "we binned our data to spectral resolutions of 4, 10, and 20 MHz for Cycle 0 Band 3, 15.6 MHz for the combined CSV$+$Cycle 0 data in Band 3" (2.1 ALMA)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SMA data reduced with same steps as the earlier SMA paper using MIR  
  > "The data were reduced with the same steps as before using the MIR reduction package." (2.2 SMA) [from (cite: Sakamoto06)]
- Systemic velocity 2775 km/s adopted  
  > "Systemic velocity of the merger in radio-definition with respect to the LSR ((cite: Sakamoto06))." (Table 1) [from (cite: Sakamoto06)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum and per-line continuum subtraction
- Clean thresholds, masks, cell and image sizes, number of iterations
- Self-calibration (if any) and flagging details
- Exact moment-map cutoffs
- Velocity-field fitting method and software for p.a./inclination
- Gaussian spectral fit details and aperture definitions
- Whether the CASA pipeline or manual scripts were used

## Analysis recipe

1. **Calibrate and image continuum and lines**: CASA calibration from raw data; imaging of Cycle 0 and CSV data with natural, Briggs robust=0, and tapered weighting; continuum subtraction  
  > "Imaging and basic data analysis were also made in CASA." (2.1 ALMA)
   - software: CASA
   - parameter: Briggs robust = 0, natural, tapered  
  > "br= Briggs with `robust = 0`, na = natural, tp = tapered." (Table 5 notes)
   - fitting: _not stated_
   - validation: Recovered 76-87% of single-dish CO(1-0) flux (Cycle 0), 91-97% (CSV+Cycle 0)  
  > "We recovered 91–97% of the single-dish CO(1–0) flux in the cubes made from the CSV$+$Cycle 0 data." (2.1 ALMA)
2. **Continuum spectral indices**: Compare single-sideband continuum images with common resolution and u-v coverage in USB and LSB  
  > "We measured the spectral slope of the continuum emission at 2.8 mm and 0.86 mm by comparing the data in the upper and lower sidebands" (3.1 Continuum)
   - fitting: _not stated_
   - validation: _not stated_
3. **Gas mass and surface density from CO**: Convert CO(1-0) flux to H2 mass with fiducial X_CO and He correction  
  > "We estimate the mass of molecular gas using the CO(1–0) to H$_2$ mass conversion factor" (3.2.4)
   - assumption: X_CO = 1e20 cm-2 (K km/s)-1 (X20=1), 36% He mass contribution; alpha_CO = 2.2 X20 Msun/pc2 per K km/s  
  > "$\mbox{$\alpha_{\rm CO}$}\equiv \Sigma_{\rm mol} / I_{\rm CO(1-0)} = 2.2 \mbox{$X_{20}$}$" (3.2.4)
   - fitting: _not stated_
   - validation: Gas-to-dynamical mass ratios ~10% judged reasonable for X20=1  
  > "The reasonable gas mass fractions on the order of 10%, however, suggest that the gas masses above are probably not very wrong." (4.7)
4. **Nuclear disk geometry and dynamical masses**: Fit velocity field for p.a. and inclination; dynamical mass from line-of-sight rotation velocity from PV diagrams and inclination; mass ratio from FWHM ratio  
  > "We fitted the velocity field to estimate the kinematical major axis to be at ${\rm p.a.} \approx 75\ensuremath{^\circ}$ and the disk inclination to be $i \approx 30\ensuremath{^\circ}$" (3.2.2 Velocity Field)
   - assumption: Southern disk inclination ~80 deg (70-85)  
  > "We estimate the most likely inclination of the southern molecular jet (and the southern nuclear disk) to be about 80$^\circ$" (5.2.3 Inclination Correction)
   - fitting: _not stated_
   - validation: Consistency with HI results of English et al. 2003  
  > "The configuration suggested above is consistent with what (cite: English03) estimated from their H I imaging of the merger." (4.5)
5. **High-velocity gas flux, mass, outflow rate**: Integrate channels offset >~224 km/s from Vsys; split mass between nuclei via blueshifted fractions; outflow rate = mass / (extent / deprojected velocity)  
  > "The mass of high-velocity molecular gas associated with each nucleus is estimated to be $6.3\times10^7 \mbox{$X_{20}$}\, \mbox{$M_\odot$}$ for the northern nucleus" (3.3.3)
   - assumption: X20=1 for outflow; outflow axis perpendicular to nuclear disk; same inclination as disk  
  > "We assumed for this the outflow axis to have the same inclination as the northern nuclear disk" (5.1.2)
   - fitting: _not stated_
   - validation: Rejected continuum-subtraction error, line blending and correlator response as origin of wings  
  > "We regard our detection of these high-velocity emission components as robust for the following reasons." (3.3.5)

## Software

- **CASA** 4.0 and 4.1: calibration, imaging and analysis of ALMA data  
  > "using the CASA[^4] reduction package versions 4.0 and 4.1" (2.1 ALMA)
- **MIR** : SMA data reduction  
  > "The data were reduced with the same steps as before using the MIR reduction package." (2.2 SMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Northern outflow mass outflow rate | 60 X20 | lower limit | Msun/yr | 5 | We estimate the outflow rate from the northern nucleus to be $\dot{M}_{N} \approx 60 \mbox{$X_{20}$}$ $M_\odot$ yr$^{-1}$. |
| Southern outflow mass outflow rate (i=80 deg) | 50 X20 | not stated | Msun/yr | 5 | estimated to be $\dot{M}_{S} \approx 50 \mbox{$X_{20}$}$ and $25 \mbox{$X_{20}$}$ $M_\odot$ yr$^{-1}$ for $i_{\rm S, outflow} = 80\ensuremath{^\circ}$ and 70$^\circ$ |
| High-velocity molecular gas mass | 8.8e7 X20 | not stated | Msun | 5 | $8.8\times10^7 \mbox{$X_{20}$}\, \mbox{$M_\odot$}$ from the high-velocity CO(1–0) line flux |
| Molecular mass within r<=10'' | 7e9 X20 | not stated | Msun | 3 | $\mbox{$M_{\rm mol}$}(r \leq 10\ensuremath{''} ) = 7\times10^{9} \mbox{$X_{20}$}\, \mbox{$M_\odot$}$ |
| Peak surface density at S nucleus (80 pc) | 6e3 X20 | 0.5 dex | Msun/pc2 | 3 | $\Sigma_{\rm mol}({\rm S}) = 6\times 10^3 \mbox{$X_{20}$}$ $M_\odot$pc$^{-2}$ |
| Northern nucleus inclination | 30 | not stated | deg | 4 | the disk inclination to be $i \approx 30\ensuremath{^\circ}$ |
| Continuum spectral index, central 20'' at 0.86 mm | +3.00 | not stated | dimensionless | 2 | B7 / U / 354.236 / 122.2 / 13.2 / 9.6 / 1 / $+3.00$ / $+3.72$ / $+1.56$ |
| Mdyn(N)/Mdyn(S) | 2.5 | ±1 | dimensionless | 4 | we suggest $\mbox{$M_{\rm dyn}$}({\rm N})/\mbox{$M_{\rm dyn}$}({\rm S}) \sim 2.5$ with an error up to $\pm 1$ |
| CO(2-1)/CO(1-0) flux ratio at ~3'' | 4.0 | ~10% calibration | dimensionless | 3 | 4.0 with $\sim$10% calibration uncertainty |
| Southern outflow maximum deprojected velocity (i=80 deg) | 2600 | not stated | km/s | 5 | as large as 2600 km s$^{-1}$ ($= 450\, \mbox{km s$^{-1}$}/\cos 80\ensuremath{^\circ}$) |

## Qualitative findings

- Both nuclei have compact molecular nuclear disks; N is nearly face-on, S nearly edge-on  
  > "while one at the northern nucleus is nearly face-on the other at the southern nucleus is almost edge-on" (abstract)
- CN(1-0) detected in the high-velocity gas, first in a galactic outflow  
  > "The CN detection in a galactic outflow is for the first time to our knowledge." (7 Conclusions)

## Claim tuples

- H: Is the high-velocity gas a single outflow or two? | E: CO(1-0) and CO(3-2) channel maps and PV diagrams at high resolution | R: High-velocity emission separates into a wide pole-on component on N nucleus and a collimated N-S component around S nucleus | F: Each nucleus drives its own bipolar molecular outflow | **supported**
- H: Are the outflows significant relative to star formation? | E: Compute outflow rates from high-velocity CO mass and crossing time | R: 60 and 50 Msun/yr (X20=1) versus SFR ~50 | F: Outflows compare to or exceed total SFR, though dependent on X_CO | **partially**
- H: What drives the southern outflow? | E: Compare CO with VLA 3.6 cm spurs, AGN constraints, and kinematics | R: CO tips coincide with radio spurs; no bright submm core | F: Plausibly an AGN radio jet from a recently dimmed AGN, not proven | **partially**

## Reasoning

- Why this data: Earlier CSV data showed broader wings but structure unconstrained; ALMA gives higher resolution and sensitivity  
  > "its structure was still largely unconstrained" (Introduction)
- Why this method: _not stated_
- Alternative: Rotation around S nucleus, and tidal feature, rejected as origin of the S high-velocity gas  
  > "This model is not favored because it makes the bipolar structures much larger than the base nuclear disk." (5 Two Outflows)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass estimates depend on uncertain X_CO; may be an order of magnitude lower if optically thin  
  > "Because most outflow parameters in Table 8 depend on $X_{20}$, followup studies on the physical and chemical properties of the high-velocity gas are highly desired." (7 Discussion and Conclusions)
- Caveat (inferred, ours): Outflow rates rely on a single assumed X_CO and uncertain inclination
- Caveat (inferred, ours): Southern inclination is indirectly constrained
- Caveat (inferred, ours): Missing flux in Band 7 not quantified
- Caveat (inferred, ours): AGN-jet driver interpretation is circumstantial

## Reproducibility

- Data public (paper): ALMA data cited by project codes (CSV and Cycle 0); public status not explicitly stated  
  > "This paper made use of the following ALMA data: ADS/JAO.ALMA#2011.0.00002.SV and ADS/JAO.ALMA#2011.0.00525.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Detailed imaging parameters (clean masks, thresholds, cell and image sizes)
- Missing: Line-free channel ranges
- Missing: Velocity-field fitting procedure
- Missing: SMA data are not in the ALMA archive
- Data volume (inferred): Tens to ~100 GB raw for Cycle 0 B3+B7 plus CSV
- Score (inferred): 3/5, Public ALMA data and clear arithmetic for derived quantities, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Imaging and fitting recipe is incomplete and key results depend on assumed geometry and X_CO.

## Links

- Companion: (cite: Sakamoto06) (Earlier SMA discovery of the CO wings in NGC 3256)
- Companion: (cite: Sakamoto13a) (ALMA CSV data showing broader CO wings)
- Related: ALMA Cycle 0
- Related: ALMA Commissioning and Science Verification

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 51,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
