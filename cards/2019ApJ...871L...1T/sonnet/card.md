# Indication of Another Intermediate-mass Black Hole in the Galactic Center

`2019ApJ...871L...1T` | The Astrophysical Journal Letters 2019 | first author: Takekawa, Shunya | arXiv: 1812.10733 | DOI: 10.3847/2041-8213/aafb07

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, stellar_physics
- Question: Does the high-velocity compact cloud HCN-0.009-0.044 contain gas orbiting an invisible massive object, such as an intermediate-mass black hole?  
  > "This Letter reports on the results of high-resolution observations of HCN–0.009–0.044 with the Atacama Large Millimeter/submillimeter Array (ALMA)" (Introduction)
- Target **HCN–0.009–0.044**: coordinates (l, b) = (-0.009°, -0.044°)  
  > "centered at $(l,\ b)=(-0.009\ensuremath{^\circ},\ -0.044\ensuremath{^\circ})$" (Observations); "The distance to the Galactic center is assumed to be $D=8$ kpc." (Introduction); z/distance 8 kpc (assumed Galactic center distance)  
  > "centered at $(l,\ b)=(-0.009\ensuremath{^\circ},\ -0.044\ensuremath{^\circ})$" (Observations); "The distance to the Galactic center is assumed to be $D=8$ kpc." (Introduction); distance from assumed  
  > "centered at $(l,\ b)=(-0.009\ensuremath{^\circ},\ -0.044\ensuremath{^\circ})$" (Observations); "The distance to the Galactic center is assumed to be $D=8$ kpc." (Introduction)

## Data provenance

- ALMA projects: 2017.1.01557.S
- bands: _not stated_
- frequencies and spectral setup: HCN, HCO+, CS windows of 1, 0.5, 2 GHz bandwidth, 1.953 MHz channels  
  > "The bandwidths of the spectral windows for the HCN, HCO$^+$, and CS observations were respectively 1, 0.5, and 2 GHz with 1.953-MHz channel widths." (Observations)
- continuum bandwidth: _not stated_
- arrays: Eleven 7-m and forty-six 12-m antennas  
  > "Eleven 7-m antennas and forty-six 12-m antennas were used" (Observations)
- configurations: 12-m: C43-2  
  > "The 12-m array configuration was C43-2 with baseline lengths of 15–314 m." (Observations)
- baselines: 15–314 m (12-m)  
  > "The 12-m array configuration was C43-2 with baseline lengths of 15–314 m." (Observations)
- angular resolution: 0.87''x0.71'' at 354.5 GHz  
  > "$0.87''\times 0.71''$ with a position angle (PA) of $-31.6^\circ$ at 354.5 GHz" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 7 mJy/beam per cube channel  
  > "The root mean square (rms) noise level of the image cubes was 7 mJy beam$^{-1}$." (Observations)
- time on source: 43.34 min (7-m), 9.27 min (12-m)  
  > "The on-source times were 43.34 and 9.27 min for the 7-m and 12-m array observations, respectively." (Observations)
- observing dates: May 13–14, 2018  
  > "were performed on May 13–14, 2018." (Observations)
- pi or archival as stated: _not stated_
- Line: HCN J=4–3 (354.5 GHz)
- Line: HCO+ J=4–3 (353.6 GHz)
- Line: CS J=7–6 (342.9 GHz)
- Other facility **HST**: Pa-alpha 1.87 um image  
  > "Pα recombination line at 1.87 $\mu$m obtained through the Hubble Space Telescope (cite: dong11)" (Indication of an IMBH)
- External data: 5.5 GHz diffuse continuum image for radio upper limit  
  > "Diffuse continuum emission at 5.5 GHz (cite: zhao13; zhao16) overlaps with HCN–0.009–0.044" (Indication of an IMBH) [from (cite: zhao13; zhao16)]
- External data: X-ray 0.5–8 keV image upper limit  
  > "the X-ray image at 0.5–8 keV (cite: muno09) provides an upper limit X-ray luminosity" (Indication of an IMBH) [from (cite: muno09)]
- External data: HST Pa-alpha image  
  > "Pα recombination line at 1.87 $\mu$m obtained through the Hubble Space Telescope (cite: dong11)" (Indication of an IMBH) [from (cite: dong11)]

## Processing

### Calibration

- pipeline or manual: EA ARC calibration script, standard manner in CASA  
  > "The calibration was performed with the calibration script provided by the East Asian ALMA Regional Center." (Observations)
- casa version: 5.1.2-4  
  > "(version 5.1.2-4)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924–2914  
  > "J1924–2914 and J1517–2422 were observed as the flux and bandpass calibrators." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "The synthesized images were created using the task ‘tclean’" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: 0.5'' spatial grid; 2 km/s velocity grid  
  > "The spatial and velocity grid width of the resultant image cubes were 0.5$''$ and 2 km s$^{-1}$, respectively." (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "The visibility data were split into spectral lines and continuum emissions through the task ‘uvcontsub’." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 7-m and 12-m data used together (method not stated)  
  > "which was covered with 7 and 23 pointings of the 7-m and 12-m arrays, respectively" (Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 7 mJy/beam  
  > "The root mean square (rms) noise level of the image cubes was 7 mJy beam$^{-1}$." (Observations)

### Inherited from earlier work

- Orbital fitting procedure  
  > "we performed orbital fittings to the observed data with the similar procedure as done for the Sgr A West by Zhao et al. (2009)" (Keplerian Model) [from Zhao et al. (2009)]
- LTE mass with Tex = 22 K, optically thin  
  > "assuming the local thermodynamic equilibrium (LTE) with an excitation temperature of 22 K in the optically thin limit (cite: takekawa17)" (Spatial/Velocity Structure and Physical Condition) [from (cite: takekawa17)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for uvcontsub and fit order
- Cleaning threshold, masks, and niter
- How 7-m and 12-m data were combined
- Exact loci points chosen for orbit fitting
- Uncertainty estimation method for the orbital parameters
- Calibration script version and flux scale accuracy
- Image sizes and primary beam correction

## Analysis recipe

1. **Image line cubes and continuum**: uvcontsub then tclean with Briggs weighting  
  > "The synthesized images were created using the task ‘tclean’ with Briggs weighting with a robust parameter of 0.5." (Observations)
   - software: CASA
   - parameter: robust 0.5; 0.5'' pixels; 2 km/s channels  
  > "The spatial and velocity grid width of the resultant image cubes were 0.5$''$ and 2 km s$^{-1}$, respectively." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate LTE gas masses**: LTE, optically thin HCN  
  > "assuming the local thermodynamic equilibrium (LTE) with an excitation temperature of 22 K in the optically thin limit" (Spatial/Velocity Structure and Physical Condition)
   - assumption: Tex = 22 K; [HCN]/[H2] = 4.8e-8  
  > "a fractional abundance of $\rm [HCN]/[H_2] = 4.8\times 10^{-8}$ (cite: tanaka09; oka11)" (Spatial/Velocity Structure and Physical Condition)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Keplerian orbital geometry**: Least-square fit of orbits to chosen loci of Balloon and Stream  
  > "we determined three-dimensional orbital parameters ($a$, $e$, $\Omega$, $\omega$, $i$) for the orbital geometries of the Balloon and Stream by least-square fitting to the loci we chose" (Keplerian Model)
   - assumption: Dynamical center at (l,b,R) = (-0.0096°, -0.0451°, 8 kpc)  
  > "Assuming the dynamical center at $(l,\ b, \ R) = (-0.0096^\circ,\ -0.0451^\circ,\ \rm 8\ kpc)$" (Keplerian Model)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit central mass and systemic velocity**: Chi-square minimization of modeled V_Z against moment-1 velocities smoothed to 3'' FWHM  
  > "we fitted the modeled velocities $V_Z$ to the observed velocities on the orbits of the Balloon and Stream with free parameters of $M_{\rm dyn}$ and $V_{\rm dyn}$ through a chi-square ($\chi^2$) minimization approach" (Keplerian Model)
   - fitting: _not stated_
   - validation: confidence contours of M_dyn vs V_dyn  
  > "Figure 3(d) shows the confidence level contours as a function of $M_{\rm dyn}$ and $V_{\rm dyn}$." (Keplerian Model)

## Software

- **CASA** 5.1.2-4: calibration, uvcontsub, tclean imaging  
  > "We calibrated and reduced the data by using the Common Astronomy Software Applications (CASA) software package (version 5.1.2-4)" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Central mass M_dyn | 3.2e4 | ±0.6e4 | Msun | 4 | $M_{\rm dyn} = (3.2\pm0.6) \times 10^4$ $M_\odot$ |
| V_dyn | -49.5 | +1.0/-0.7 | km/s | 4 | $V_{\rm dyn} = -49.5^{+1.0}_{-0.7}$ km s$^{-1}$ |
| Balloon semi-major axis | 0.20 | 0.02 | pc | 3 | Semi-major axis, $a$ / $0.20 \pm 0.02$ pc / $0.54 \pm 0.15$ pc |
| Balloon LTE mass | 6 | not stated | Msun | 2 | $M_{\rm LTE} \sim 6$ $M_\odot$, 1 $M_\odot$ and 0.1 $M_\odot$, respectively |
| Upper limit radio luminosity | 2e28 | not stated | erg/s | 0 | provides an upper limit radio luminosity of $\sim 2\times 10^{28}$ erg s$^{-1}$ for the putative IMBH |

## Qualitative findings

- HCN–0.009–0.044 resolves into a Balloon, Stream and ultra-compact clump with velocity gradients; Pa-alpha emission lies inside the Balloon orbit.  
  > "HCN–0.009–0.044 is resolved into several components." (Spatial/Velocity Structure and Physical Condition)

## Claim tuples

- H: Balloon and Stream orbit a common dark massive object | E: Keplerian orbit fits to ALMA HCN moment-1 kinematics | R: M_dyn = (3.2±0.6)e4 Msun with two Keplerian orbits | F: A likely IMBH sits within the cloud | **supported**
- H: The central mass could be a star cluster | E: Density comparison and X-ray/radio limits | R: Density exceeds M15 core, no luminous counterpart, X-ray limit consistent with Fundamental Plane | F: An IMBH is the most promising candidate | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Supernova-cloud interaction and cloud-cloud collision rejected because no expanding motion or V-shaped pattern is seen.  
  > "exhibits neither expanding motion indicative of a supernova–cloud interaction" (Origin of HCN–0.009–0.044)
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination double degeneracy; UCC broad velocity not explained by Keplerian model.  
  > "Note that there remains a double degeneracy in the inclination angle." (Keplerian Model)
- Caveat (inferred, ours): Loci for fits were hand-chosen, so uncertainties may be underestimated
- Caveat (inferred, ours): Distance to the cloud is assumed, not measured
- Caveat (inferred, ours): Only two orbits are fitted to a few points; a distributed mass is not excluded

## Reproducibility

- Data public (paper): Archive data cited by project code only  
  > "ADS/JAO.ALMA#2017.1.01557.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Selected loci coordinates
- Missing: Clean parameters
- Missing: Orbit-fitting code
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public data and the main steps are described, but loci selection and fitting details are missing.
- Rediscovery candidate: no, The orbit fit depends on hand-selected loci that are not given.

## Links

- Method: Zhao et al. (2009) (orbital fitting procedure)
- Companion: Takekawa et al. 2017 (cite: takekawa17) (discovery of HCN–0.009–0.044 with JCMT)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
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
  "facts": 68,
  "stated": 40,
  "rate": 0.588
 },
 "evidence_ok": true
}
```
