# Outflow from Outer-arm Starburst in a Grazing Collision between Galaxies

`2020AJ....159..180K` | The Astronomical Journal 2020 | first author: Kaufman, Michele | arXiv: 2003.08827 | DOI: 10.3847/1538-3881/ab7b7f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What powers the starburst clump Feature i on an outer arm of NGC 2207, is there a molecular outflow behind its opaque dust cone, and how did the clump originate in the grazing collision?  
  > "We then combine these observations with previous radio to X-ray data in order to study the outflow and determine the energy source(s) in this intriguing, partly obscured star-forming region." (Introduction)
- Target **Feature i in NGC 2207**: coordinates radio peak RA, Dec (J2000) = 06 16 15.865, -21 22 02.77  
  > "we adopt a distance of $35 \pm 2.5$ Mpc for NGC 2207 with a Hubble constant $H$ = 73 km s$^{-1}$ Mpc$^{-1}$ and corrected for infall toward Virgo." (Introduction); "R.A., decl. (J2000) = 06 16 15.865, $-21$ 22 02.77" (Overview and Previous Results); z/distance 35 ± 2.5 Mpc (1" = 170 pc)  
  > "we adopt a distance of $35 \pm 2.5$ Mpc for NGC 2207 with a Hubble constant $H$ = 73 km s$^{-1}$ Mpc$^{-1}$ and corrected for infall toward Virgo." (Introduction); "R.A., decl. (J2000) = 06 16 15.865, $-21$ 22 02.77" (Overview and Previous Results); distance from NED, H = 73 km/s/Mpc, Virgo infall corrected  
  > "we adopt a distance of $35 \pm 2.5$ Mpc for NGC 2207 with a Hubble constant $H$ = 73 km s$^{-1}$ Mpc$^{-1}$ and corrected for infall toward Virgo." (Introduction); "R.A., decl. (J2000) = 06 16 15.865, $-21$ 22 02.77" (Overview and Previous Results)

## Data provenance

- ALMA projects: 2012.1.00357.S, 2013.1.00041.S
- bands: 88-106 GHz continuum; CO(1-0) at 114.195 GHz; HCN/HCO+ near 88 GHz  
  > "Central $\nu$ (GHz) | 114.195 | 87.830 | 87.823 | 88.390 | 88.382" (Table 2)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 0.52 GHz (88), 3.9 GHz (100), 6 GHz (106.4)  
  > "Bandwidth | 0.52 GHz | 3.9 GHz | 6 GHz" (Table 4)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: 15" for CO Cycle 2; 11-12.5" (2014) and 17-20" (2015) for HCN/HCO+  
  > "The maximum recoverable scale is $15''$, which exceeds the size of Feature i." (4.1)
- sensitivity: _not stated_
- time on source: CO 72 min; HCN/HCO+ 36 min (2014) and 72 min (2015)  
  > "Time on Source | 72 min | 36 min | 72 min | 36 min | 72 min" (Table 2)
- observing dates: CO Cycle 2 2015-05-15; HCN/HCO+ 2014-08-30 and 2015-06-07; Cycle 1 CO 2014-04-03  
  > "Date Observed | 2015-05-15 | 2014-08-30 | 2015-06-07 | 2014-08-30 | 2015-06-07" (Table 2)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.271202 GHz)
- Line: HCN 1-0 (88.631601 GHz)
- Line: HCO+ 1-0 (89.188526 GHz)
- Other facility **Gemini NIFS**: K-band IFU spectra (Br gamma, H2, He I lines) of the core  
  > "On 2017 Feb 15, *K*-band spectra were taken of the core of Feature i with Gemini’s NIFS integral field spectrograph" (Near-IR K-band Spectra)
- Other facility **VLA**: radio continuum and H I data  
  > "VLA 4.86 GHz | 2001-04-14" (Table 1)
- Other facility **HST, Spitzer, Chandra**: optical, 8/24 um and X-ray data from earlier work  
  > "Spitzer 8 $\mu$m  | 2005-02-22" (Table 1)
- External data: Central star complex mass 2e6 Msun and age 0.6 Myr from HST  
  > "has a mass of $2 \times 10^6$ $M_{\ensuremath{\odot}}$, an age of 0.6 Myr (cite: elmegreen17)" (2.2) [from (cite: elmegreen17)]
- External data: Encounter models: disk inclination 35±5 deg  
  > "the central disk of NGC 2207 has an inclination $i$= $35\ensuremath{^\circ} \pm 5\ensuremath{^\circ}$" (5) [from (cite: elmegreen95b; struck05)]
- External data: SFR of Feature i from Hα and 24 um  
  > "find the SFR of Feature i is 1.7 $M_{\ensuremath{\odot}}$ yr$^{-1}$ from the H$\alpha$ and 24 $\mu$m luminosities" (8.3) [from (cite: smith14)]

## Processing

### Calibration

- pipeline or manual: ALMA Data Reduction Team pipeline calibration and flagging  
  > "Using the pipeline with CASA 4.2.2 software, the ALMA Data Reduction Team did the calibration and flagging" (4.1)
- casa version: CASA 4.2.2  
  > "Using the pipeline with CASA 4.2.2 software" (4.1)
- pipeline version: Pipeline-Cycle 2-R1-B (HCN/HCO+)  
  > "Using the Pipeline-Cycle 2-R1-B and CASA 4.2.2 software" (4.1)
- archive products used as is: _not stated_
- flux calibrator: Callisto (CO); Ganymede, Mars (HCN/HCO+)  
  > "Flux Calibrator | Callisto | Ganymede | Mars | Ganymede | Mars" (Table 2)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs R=0.5 for CO and 106 GHz; natural for HCN, HCO+, 88 and 100 GHz  
  > "Weighting | Briggs R = 0.5 | Briggs R = 0.5 | Natural | Natural" (Table 3)
- uv taper: _not stated_
- cell size: 0.2" CO; 0.3" HCN/HCO+; 0.1" or 0.2" continuum  
  > "Pixel size | $0.2''$ | $0.2''$ | $0.3''$ | $0.3''$" (Table 3)
- image size: _not stated_
- masking: Cube convolved to 3" (2" for HCO+), clipped at 2.5 (2 for HCO+) times rms, kept if in at least 2 adjacent channels; used as blanking mask  
  > "convolved the cube before correction for primary-beam attenuation to $3''$ resolution, clipped it at 2.5 times its rms noise" (4.1)
- multiscale scales: _not stated_
- continuum subtraction: 88 GHz continuum from line-free channels of the HCO+ cube  
  > "we made a continuum map at 88 GHz from the line-free channels in the HCO$^+$ cube" (4.1)
- line free channels: _not stated_
- primary beam correction: applied before moment maps after masking  
  > "after correcting for primary beam attenuation, we calculated the moment maps" (4.1)
- array combination: Cycle 1 plus Cycle 2 CO data combined into CO Combined cube  
  > "We also combined our lower resolution ALMA Cycle 1 CO data (listed in Table 1) with our Cycle 2 CO data" (4.1)
- smoothing: _not stated_
- final beam: CO Cycle 2 1.37"x1.04"; CO Combined 1.82"x1.33"; HCO+ 1.26"x1.00"  
  > "PSF (HPBW) | $1.37'' \times 1.04''$ | $1.82'' \times 1.33''$ | $1.22'' \times 0.95''$ | $1.26'' \times 1.00''$" (Table 3)
- final rms: _not stated_

### Inherited from earlier work

- Calibration, flagging and cleaning of cubes done by ALMA Data Reduction Team; Cycle 1/2 data recalibrated by ALMA staff  
  > "We thank Jonathan Westcott for his contribution in obtaining the re-calibrated ALMA uv-data for Cycles 1 and 2" (Acknowledgments) [from ALMA Data Reduction Team]
- Same IMF and Lyman continuum prediction as Sternberg et al.  
  > "Models by (cite: sternberg03) predict a Lyman continuum rate $N_{\rm Lyc}$ = $2 \times 10^{53}$ s$^{-1}$" (6.2) [from (cite: sternberg03)]

### Not stated but needed to reproduce (our reading)

- Exact CLEAN threshold, niter and mask used by the ALMA Data Reduction Team
- Cycle 1 CO observation details (project mapping, calibration) and combination procedure
- Line-free channels for the continuum maps
- AIPS version and tasks used
- Which project code corresponds to which dataset
- Procedure for the Gaussian fits and primary beam correction values

## Analysis recipe

1. **Calibrate and image ALMA data**: Pipeline calibration and imaging by ALMA team; CO Cycle 1+2 combination; masked moment maps in AIPS  
  > "For subsequent analysis, we used the AIPS software package." (4.1)
   - software: CASA, AIPS
   - parameter: Briggs R=0.5 for CO; 2.5 sigma mask on 3" smoothed cube  
  > "Weighting | Briggs R = 0.5 | Briggs R = 0.5 | Natural | Natural" (Table 3)
   - fitting: _not stated_
   - validation: Inspected pipeline CO cube, saw no problems  
  > "Inspecting this, we saw no problems." (4.1)
2. **Derive molecular column density and extinction**: Convert CO to N(H2) with Galactic X_CO, convert to Av with standard relation, compare with dark cone extinction  
  > "With the standard Galactic relation between neutral hydrogen column density and $A_{\rm v}$ (cite: bohlin78)" (4.1)
   - assumption: X_CO = 1.8±0.3e20 H2 cm-2 (K km/s)-1; gas symmetric about midplane for midplane Av  
  > "We therefore adopt the standard value $X_{\rm CO}$ = $1.8 \pm 0.3 \times 10^{20}$ H$_2$ cm$^{-2}$ (K km s$^{-1})^{-1}$" (Introduction)
   - fitting: _not stated_
   - validation: Several Av indicators compared in Table 5  
  > "all three types of methods in Table 5 are consistent with $A_{\rm v}$= 3 - 3.5 mag to the midplane." (4.1)
3. **Measure outflow kinematics and mass**: Moment maps, position-velocity diagrams along dark cone, components A and B relative to disk velocity 2784 km/s; sum CO emission at v<=2774 km/s in SW quadrant for mass  
  > "we restrict our measurement to emission with velocities $\leq$ 2774 km s$^{-1}$ in the CO Cycle 2 cube and sum the emission in the quadrant southwest of the radio peak." (7.3)
   - assumption: Outflow perpendicular to disk; inclination 35 deg, v_z = v_outflow/cos i; helium factor 1.36  
  > "$v_z$ = $v_{\rm outflow}/\cos i_{\rm feati}$ is the component of the outflow velocity perpendicular to this disk" (7.2)
   - fitting: _not stated_
   - validation: _not stated_
4. **Energetics and SFR requirement**: Compute E_kin, require SNe at 0.1% efficiency, one SN per 100 Msun, compare with observed SFR  
  > "A standard IMF gives about one supernova for every 100 $M_{\ensuremath{\odot}}$ of stars formed" (7.3)
   - assumption: 0.1% of SN energy becomes bulk kinetic energy; integrated over 10 Myr  
  > "Only about 0.1% of the energy of a supernova remains as $E_{\rm kin}$ of bulk motions" (7.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit 2D Gaussians to continuum and derive spectral index and free-free components**: Gaussian plus flat baseline fits; spectral index from convolved 88-106 GHz maps; Condon (1992) free-free relation to Br gamma  
  > "the fit consists of a single Gaussian plus a flat baseline" (6.3)
   - assumption: Te = 5000 K favored  
  > "We rule out $T_e \geq 10^4$ K" (6.3)
   - fitting: 2D Gaussian fits  
  > "lists the results of two-dimensional Gaussian fits to the continuum emission from the Feature i core at various frequencies" (Radio and mm-wave Continuum)
   - validation: _not stated_

## Software

- **CASA** 4.2.2: ALMA pipeline calibration, flagging and imaging  
  > "Using the pipeline with CASA 4.2.2 software" (4.1)
- **AIPS** : masking, moment maps and subsequent analysis of CO data  
  > "For subsequent analysis, we used the AIPS software package." (4.1)
- **pyraf / Gemini nifs package** : NIFS data reduction  
  > "reduced in a standard manner within the pyraf environment using the Gemini nifs package" (Near-IR K-band Spectra)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Approaching outflow v_z | 16 | not stated | km/s | 3 | An associated approaching CO outflow has $v_z \sim 16$ km s$^{-1}$ |
| Receding outflow v_z | 28 | not stated | km/s | 3 | A receding CO outflow on the far side with $v_z \sim 28$ km s$^{-1}$ |
| Outflow molecular mass (dark cone) | 8e6 | not stated | Msun | 3 | this gives $M({\rm H}_2)$ = $8 \times 10^6$ $M_{\ensuremath{\odot}}$ |
| Kinetic energy of dark cone | 2e52 | not stated | erg | 4 | the estimated kinetic energy of bulk motion $E_{\rm kin}$ = $2 \times 10^{52}$ ergs for the dark cone |
| Mean N(H2) in 1.6" core aperture | 1.41e22 | 0.04e22 | cm-2 | 2 | the mean value of $N(\rm {H}_2$) is $(1.41 \pm 0.04) \times 10^{22}$ molecules cm$^{-2}$ |
| 88-106 GHz spectral index of core | -0.2 | 0.7 | dimensionless | 5 | find an 88 GHz to 106 GHz spectral index $\alpha = - 0.2 \pm 0.7$ |
| 100 GHz core flux density | 1.45 | 0.07 | mJy | 5 | 100 GHz / $1.45 \pm 0.07$ |
| HCO+/CO surface brightness ratio in core | 0.044 | not stated | dimensionless | 0 | the ratio $I({\rm HCO}^+)$/$I$(CO) = 0.044 in the Feature i core |
| HCN/CO upper limit in core | 0.05 | not stated | dimensionless | 0 | This gives an upper limit to the surface brightness ratio $I$(HCN)/mean $I$(CO) of 0.05. |
| CO FWHM at radio peak | 42 | 1 | km/s | 3 | the FWHM line-width corrected for the velocity resolution is $42 \pm 1$ km s$^{-1}$ |

## Qualitative findings

- CO column density explains the dark cone extinction only if the gas is mostly on the near side of the disk.  
  > "The implication is that almost all of the gas in this part of the dark dust cone must be on the near side" (4.2)
- HCN is not detected in the core; HCO+ lies opposite the dark cone.  
  > "No HCN emission was detected in Feature i." (4.1)

## Claim tuples

- H: Is the CO along the dark dust cone an outflow perpendicular to the disk? | E: Compared CO velocities along the cone to the disk velocity using the velocity field and PV diagram | R: Cone gas is blueshifted by 11-16 km/s relative to the disk, and there is a redshifted component on the opposite side | F: An approaching and a receding molecular outflow are present | **supported**
- H: Can star formation in the core power the outflow? | E: Compared required SNe energy with the SFR | R: Need SFR > 0.2 Msun/yr over 10 Myr versus observed ~1.5-1.7 Msun/yr | F: Star formation can supply the energy | **supported**
- H: Does the 100 GHz continuum come from dust or free-free? | E: Spectral index between 88 and 106 GHz and Br gamma comparison | R: alpha = -0.2±0.7, at least 67% optically thin free-free | F: Free-free dominates plus nonthermal | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Standard X_CO adopted since metallicity is near solar  
  > "so metallicity close to solar. We therefore adopt the standard value" (Introduction)
- Alternative: Reduced starburst X_CO rejected for the dark cone because the extinction requires standard value  
  > "is not appreciably reduced from the standard value" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass of the receding outflow unknown; disk warp not ruled out; nonthermal sources other than supernovae not ruled out  
  > "We have not ruled out the possibility that nonthermal sources other than supernovae may also contribute to the mechanical energy." (7.3)
- Caveat (inferred, ours): Outflow velocities are low (~10-30 km/s) and could be non-circular motions in the arm, especially the redshifted side
- Caveat (inferred, ours): Perpendicular-to-disk geometry and inclination are assumed from simulations
- Caveat (inferred, ours): HCO+ detection is low S/N (3.7)
- Caveat (inferred, ours): Origin scenario is speculative

## Reproducibility

- Data public (paper): ALMA data cited by project code in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00357.S and ADS/JAO.ALMA#2013.1.00041.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Cycle 1 CO observation details
- Missing: AIPS procedures and version
- Missing: Exact clean parameters
- Data volume (inferred): tens of GB raw for the three ALMA datasets
- Score (inferred): 3/5, Public ALMA data and key numbers given, but processing details are thin and the recipe is largely hand analysis.
- Rediscovery candidate: no, The recipe is incomplete (AIPS steps, Cycle 1 data details) and several results depend on assumed geometry.

## Links

- Companion: (cite: elmegreen16) (Earlier ALMA CO of Feature i and gas masses and SFR)
- Companion: (cite: elmegreen17) (HST star complexes and CO of Feature i)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 78,
  "stated": 50,
  "rate": 0.641
 },
 "evidence_ok": true
}
```
