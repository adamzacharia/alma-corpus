# The dynamically young outflow of the Class 0 protostar Cha-MMS1

`2020A&A...633A.126B` | Astronomy and Astrophysics 2020 | first author: Busch, L. A. | arXiv: 1911.11194 | DOI: 10.1051/0004-6361/201936432

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does Cha-MMS1 drive a slow compact outflow as predicted for a first hydrostatic core, or is it a young Class 0 protostar?  
  > "Our goal is to test this hypothesis by searching for a slow, compact outflow driven by Cha-MMS1 that would match the predictions of MHD simulations for this short phase of star formation." (abstract)
- Target **Cha-MMS1**: coordinates 11h06m33.13s, -77°23'35.1" (J2000, phase centre)  
  > "The field was centred at ($\alpha, \delta$)$_{\rm J2000}$= ($11^{\rm h}06^{\rm m}33{s}13, -77^\circ23\ensuremath{'}35.1\ensuremath{''}$)" (2.1 Observations); "at a distance of 192 pc (cite: Dzib18)" (Introduction); z/distance 192 pc  
  > "The field was centred at ($\alpha, \delta$)$_{\rm J2000}$= ($11^{\rm h}06^{\rm m}33{s}13, -77^\circ23\ensuremath{'}35.1\ensuremath{''}$)" (2.1 Observations); "at a distance of 192 pc (cite: Dzib18)" (Introduction); distance from Dzib18  
  > "The field was centred at ($\alpha, \delta$)$_{\rm J2000}$= ($11^{\rm h}06^{\rm m}33{s}13, -77^\circ23\ensuremath{'}35.1\ensuremath{''}$)" (2.1 Observations); "at a distance of 192 pc (cite: Dzib18)" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7, tuned to 345.8 GHz  
  > "The Band 7 receiver was tuned to 345.8 GHz." (2.1 Observations)
- frequencies and spectral setup: Four SPWs: two continuum (331.6–333.6, 342.8–344.8 GHz, 15.6 MHz resolution) and two narrow (330.47–330.70, 345.66–345.90 GHz, 122.1 kHz) for 13CO and CO  
  > "two broadband ones for the continuum emission covering the frequency ranges 331.6–333.6 GHz and 342.8–344.8 GHz with a spectral resolution of 15.6 MHz" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Two configurations in Cycle 3, baselines up to 310 m and up to 700 m  
  > "with baselines up to 310 m for the first configuration and up to 700 m for the second one" (2.1 Observations)
- baselines: _not stated_
- angular resolution: 0.58"x0.37" (CO), 0.62"x0.41" (13CO), 0.59"x0.38" (continuum)  
  > "The synthesized beams (HPBW) are $0.58\ensuremath{''} \times 0.37\ensuremath{''}$, $0.62\ensuremath{''} \times 0.41\ensuremath{''}$, and $0.59\ensuremath{''} \times 0.38\ensuremath{''}$" (2.2 Data reduction and imaging)
- max recoverable scale: about 7"  
  > "The shortest baselines of 15–17 m imply a maximum recoverable scale of about 7$\ensuremath{''}$." (2.1 Observations)
- sensitivity: rms 3.6 mJy/beam (CO), 4.7 mJy/beam (13CO) per channel; 0.053 mJy/beam continuum  
  > "The imaged data has an rms of 3.6 mJy/beam and 4.7 mJy/beam per channel for CO 3–2 and $^{13}$CO 3–2, respectively, and 0.053 mJy/beam for the continuum emission." (2.2 Data reduction and imaging)
- time on source: _not stated_
- observing dates: 2015-12-29, 2015-12-30, 2016-06-16, 2016-06-17, 2016-06-18 (five sessions)  
  > "| 1     | 2015-12-29   | 08:42                 | 40                | 15–310      | 34                  | 0.4       | 1       | 2       | 3       |   | 1.0                 | 0.80                | 9            |" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO 3–2 (345795.9899 MHz)
- Line: 13CO 3–2 (330587.9653 MHz)
- Other facility **APEX**: Single-dish CO 3–2 maps from Belloche06 for large-scale comparison  
  > "Figure [1](#fig:co_int_map)c shows CO 3–2 integrated intensity maps obtained on larger scales with the single-dish APEX telescope reported by (cite: Belloche06)." (3.2 Morphology of the outflow)
- External data: Systemic velocity 4.43 km/s  
  > "$\varv_\mathrm{sys}= 4.43$ km s$^{-1}$ (cite: Belloche06)" (3.2 Detection of a fast outflow) [from Belloche06]
- External data: Envelope mass 2.36 Msun (rescaled to 192 pc)  
  > "the mass of the envelope derived by (cite: Belloche11) is 2.36 $M_\odot$ in a (rescaled) radius of 4800 au" (4.1 Continuum emission) [from Belloche11]
- External data: Internal luminosity rescaled to 0.13–0.29 Lsun  
  > "We correct their values for the most recent distance of Cha-MMS1 and find $L_\mathrm{int} = 0.13-0.29~L_\odot$." (4.6 Comparison to other Class 0 and Class I outflows) [from Tsitali13]
- External data: Comparison sample of outflow properties (momentum force, Lbol, Menv)  
  > "Figure [7](#fig:vdM) shows recent results of vdM13 where they combined data from various studies." (4.6 Comparison to other Class 0 and Class I outflows) [from van der Marel et al. 2013 (vdM13)]

## Processing

### Calibration

- pipeline or manual: JAO-provided calibration procedures for bandpass, amplitude, phase  
  > "We used the procedures provided by the Joint ALMA Observatory to apply the bandpass, amplitude, and phase calibrations." (2.2 Data reduction and imaging)
- casa version: CASA 4.5.0 (first config), 4.5.3 (second); 4.7.1 for imaging  
  > "version 4.5.0 for the first configuration and version 4.5.3 for the second one" (2.2 Data reduction and imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, after merging five datasets (CASA 4.7.1)  
  > "The imaging was done with the CASA task *clean* with *Briggs* weighting" (2.2 Data reduction and imaging)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "a *robust* parameter of 0.5" (2.2 Data reduction and imaging)
- uv taper: _not stated_
- cell size: 0.07"  
  > "a pixel size of 0.07$\ensuremath{''}$" (2.2 Data reduction and imaging)
- image size: 512 x 512 pixels  
  > "We produced cubes and images with $512 \times 512$ pixels" (2.2 Data reduction and imaging)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, polynomial order 1  
  > "with the CASA task *uvcontsub*, with a polynomial fit of order 1" (2.2 Data reduction and imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: GILDAS/CLASS smooth box  
  > "The smoothing was done using the *smooth box* command of the GILDAS/CLASS software" (2.2 Data reduction and imaging)
- final beam: 0.58"x0.37" PA 47° (CO)  
  > "with position angles East from North of 47$^{\circ}$, 48$^{\circ}$, and 47$^{\circ}$, respectively" (2.2 Data reduction and imaging)
- final rms: 3.6 mJy/beam CO; 4.7 13CO; 0.053 continuum  
  > "0.053 mJy/beam for the continuum emission" (2.2 Data reduction and imaging)

### Inherited from earlier work

- Dust opacity and conversion to gas mass  
  > "Following Appendix B.4 of (cite: Belloche11), we assume a dust mass opacity $\kappa_{\rm 345~GHz} = 0.02$ cm$^2$ g$^{-1}$ of gas" (3.1 Continuum emission) [from Belloche11]
- Intensity-to-mass conversion factor K and CO abundance  
  > "The calculation of $K$ is adopted from (cite: vdM13) (hereafter vdM13)" (3.6 Outflow mass) [from vdM13]
- Missing-material and hidden-atomic-gas correction factors and perpendicular method  
  > "we apply two correction factors introduced by (cite: Downes07) (hereafter DC07)" (3.6 Outflow mass) [from Downes07]
- vmax method and inclination correction factors  
  > "we apply a correction factor from (cite: Cabrit92) which depends on inclination" (3.8.2 vmax method) [from Cabrit92]

### Not stated but needed to reproduce (our reading)

- ALMA project code not printed in paper
- Clean mask and iteration details
- Line-free channels for uvcontsub
- Primary-beam correction and flux-scale uncertainty
- Whether the pipeline or manual calibration scripts were used
- Exact velocity channel ranges per pixel for the 13CO/12CO switch
- Beam-matching between configurations in merging

## Analysis recipe

1. **Fit continuum and derive envelope mass / disk limit**: Elliptical Gaussian fit to visibilities per sideband; mass from flux assuming optically thin dust  
  > "We performed an elliptical Gaussian fit in the uv plane in order to derive the peak position, size, and flux density of the compact emission." (3.1 Continuum emission)
   - software: GILDAS/MAPPING uv_fit
   - parameter: kappa 345GHz = 0.02 cm2/g gas; Tdust ~30 K  
  > "we expect a dust temperature on the order of 30 K at a radius of 55 au" (3.1 Continuum emission)
   - assumption: Optically thin continuum; distance 192 pc  
  > "provided the continuum emission is optically thin" (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: Brightness temperature ~1 K much smaller than dust T confirms optically thin  
  > "thus confirms that the dust emission is still optically thin at the scales traced here with ALMA" (3.1 Continuum emission)
2. **Identify outflow, integration limits and velocities**: CO integrated intensity maps, channel maps smoothed over 8 channels, PV diagrams along outflow axes  
  > "The outer integration limits are determined by investigating the CO data cube containing spectra smoothed over eight channels (after imaging)." (3.2 Detection of a fast outflow)
   - software: GILDAS/CLASS
   - parameter: vsys = 4.43 km/s; inner limits 3.4 and 5.5 km/s  
  > "with values of 3.4 km s$^{-1}$ and 5.5 km s$^{-1}$ for the blue- and redshifted emission, respectively" (3.2 Detection of a fast outflow)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate inclination and deproject velocities**: Geometric opening angle of NE red lobe gives inclination range; minimum inclination used to deproject  
  > "By using geometry, we determine $\theta = 22^\circ \pm 3^\circ$ for the more extended northeastern redshifted lobe which we adopt for both lobes." (3.4 Inclination of the outflow)
   - assumption: Same opening angle for both lobes  
  > "which we adopt for both lobes" (3.4 Inclination of the outflow)
   - fitting: _not stated_
   - validation: _not stated_
4. **Optical depth of CO from CO/13CO ratio**: Intensity ratio with isotopic ratio X=77 to derive tau12  
  > "with $\tau_{13}=\tau_{12}/X$ where $X$ is the local ISM $^{12}$CO/$^{13}$CO isotopic ratio equal to 77 (cite: Wilson94)" (3.5 Optical depth)
   - parameter: 13CO smoothed over four channels; 3σ thresholds  
  > "we average the $^{13}$CO wing emission over four channels and use the smoothed spectra down to 3$\sigma$" (3.5 Optical depth)
   - fitting: _not stated_
   - validation: _not stated_
5. **Outflow mass and momentum**: Sum over pixels of optical-depth-corrected 13CO then 12CO integrated intensity times K, with DC07 corrections; tau12 = 5 or thin  
  > "Here, we apply the correction $F^{12}_\tau$ assuming the two cases of either optically thin ($\tau_\mathrm{12}<<1$) or thick emission ($\tau_\mathrm{12}=5$)." (3.6 Outflow mass)
   - parameter: K = 5.07e-10 Msun s K-1 km-1  
  > "$K=5.07\times10^{-10}~M_\odot$ s K$^{-1}$ km$^{-1}$ is the conversion factor from intensity to mass" (3.6 Outflow mass)
   - assumption: Tex = 30 K; CO abundance 8.3e-5 relative to H2  
  > "we assume an excitation temperature of 30 K and a CO abundance of $8.3\times 10^{-5}$ relative to H$_2$ (vdM13)" (3.6 Outflow mass)
   - fitting: _not stated_
   - validation: Using only 12CO underestimates masses and momenta by factors 1.1–5  
  > "We tested that using only $^{12}$CO yields masses and momenta underestimated by factors 1.1–5 depending on the lobe." (Footnote 4)
6. **Dynamical age and momentum force**: Perpendicular method t=W/(3<v>) and vmax method t=R/vmax, with inclination corrections  
  > "t_\mathrm{perp} = \frac{W_\mathrm{lobe}}{3\left\langle \varv^\prime \right\rangle}" (3.8.1 Perpendicular Method)
   - assumption: Cabrit92 correction for i=70° in vmax method  
  > "We take the correction factor for $i=70^\circ$ which is the highest inclination given." (3.8.2 vmax method)
   - fitting: _not stated_
   - validation: Compared with B1b-N, B1b-S, GF 9-2 and Class 0 sample  
  > "To make a meaningful comparison with the results of vdM13, we have calculated the momentum force using the $\varv_\mathrm{max}$ method" (4.6 Comparison to other Class 0 and Class I outflows)

## Software

- **CASA** 4.5.0, 4.5.3, 4.7.1: Calibration, uvcontsub, and clean imaging  
  > "The data was calibrated with the Common Astronomy Software Applications package (CASA)" (2.2 Data reduction and imaging)
- **GILDAS/MAPPING** : uv_fit elliptical Gaussian fit of continuum  
  > "We used the task uv_fit of the GILDAS/MAPPING software" (3.1 Continuum emission)
- **GILDAS/CLASS** : Spectral smoothing (smooth box)  
  > "The smoothing was done using the *smooth box* command of the GILDAS/CLASS software" (2.2 Data reduction and imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum Gaussian FWHM | 0.61" x 0.57" | ±0.01", ±0.02" | arcsec | 1 | $(0.61\ensuremath{''} \pm 0.01\ensuremath{''}) \times (0.57\ensuremath{''} \pm 0.02\ensuremath{''})$ |
| Continuum flux density (lower / upper sideband) | 24.0 / 25.1 | ±0.1 each | mJy | 1 | $24.0 \pm 0.1$ mJy and $25.1 \pm 0.1$ mJy in the lower and upper sidebands |
| Continuum (envelope) gas mass | 2.7e-3 | not stated | Msun | 1 | we obtain a mass of $2.7 \times 10^{-3}$ $M_\odot$ |
| Disk radius upper limit | 55 | not stated | au | 1 | we derive an upper limit of 55 au to its radius |
| Outflow opening angle | 22 | ±3 | deg | 3 | $\theta = 22^\circ \pm 3^\circ$ |
| Inclination range | 79–101 | not stated | deg | 3 | the inclination angle of Cha-MMS1 is in the range $79^\circ < i < 101^\circ$ |
| Max deprojected velocity (blue / red) | 55.2 / 91.0 | not stated | km/s | 3 | we find maximum deprojected velocities of 55.2 km s$^{-1}$ for the blueshifted emission and 91.0 km s$^{-1}$ for the redshifted emission |
| Observed outflow mass NE lobe | (0.3–1.0)e-4 | range from optical depth | Msun | 5 | $M_\mathrm{obs}=(0.3-1.0)\times 10^{-4}~M_\odot$ and $(1.0-1.7)\times 10^{-4}~M_\odot$ for the NE and SW lobes |
| Observed outflow mass SW lobe | (1.0–1.7)e-4 | range from optical depth | Msun | 5 | $M_\mathrm{obs}=(0.3-1.0)\times 10^{-4}~M_\odot$ and $(1.0-1.7)\times 10^{-4}~M_\odot$ for the NE and SW lobes |
| vmax dynamical age NE / SW | 3100 / 2500 | upper limits | yr | 6 | which yields 3100 yr and 2500 yr for the NE and SW lobes, respectively |
| Perpendicular dynamical age | 100–300 (max 400 after correction) | not stated | yr | 6 | The results span a range of 100–300 yr depending on the lobe and optical depth. |
| Corrected momentum force, perpendicular method NE | (2.0–21.6)e-6 | range | Msun km/s/yr | 6 | $F_\mathrm{corr} = (2.0-21.6)\times10^{-6}~M_\odot$ km s$^{-1}$ yr$^{-1}$ |
| Optical depth tau12 at inner blue limit | ~15 | not stated | dimensionless | 4 | At the inner integration limit, the optical depth is still at $\sim$15 for the blueshifted emission |

## Qualitative findings

- Bipolar outflow roughly parallel to filament, axis near the plane of the sky, with episodic bullets and a kinked SW lobe  
  > "We report the detection of a bipolar outflow emanating from the central core, along a (projected) direction roughly parallel to the filament" (abstract)
- No disk detected in continuum; compact emission is inner envelope  
  > "we conclude that the dust component of diameter $\sim$110 au detected with ALMA must represent the inner parts of the collapsing envelope" (4.1 Continuum emission)

## Claim tuples

- H: Cha-MMS1 is a first hydrostatic core with a slow compact outflow | E: ALMA CO and 13CO 3–2 mapping of outflow kinematics | R: Outflow velocities up to ~17 km/s observed, >90 km/s deprojected | F: Velocities incompatible with FHSC; Cha-MMS1 is a young Class 0 protostar | **supported**
- H: Cha-MMS1 outflow is young and weak compared to other Class 0 sources | E: Mass, momentum, dynamical age and momentum force from CO/13CO | R: Dynamical age 200–3000 yr; momentum force 1–2 orders of magnitude below other Class 0 | F: One of the youngest Class 0 protostars, outflow not yet at full power | **supported**
- H: A disk is present around Cha-MMS1 | E: uv-plane Gaussian fit of continuum | R: No disk detected; radius < ~55 au | F: Continuum traces inner envelope | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Perpendicular method preferred because it depends weakly on inclination  
  > "which, according to the authors, provides the most accurate results compared to other methods introduced in their paper because it has no strong dependence on inclination" (3.8 Age and momentum force of the outflow)
- Alternative: Explanations for SW lobe kink: jet deflection by dense material, precession, second outflow from other sources (IRS 4, IRS 6, IRS 2) considered  
  > "Another possibility for the morphology of the SW lobe is that there is a second outflow driven by a different source." (4.5 The surroundings of Cha-MMS1)
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination uncertain; vmax-method momentum force only a lower limit; opacity corrections uncertain  
  > "Hence, we obtain only a lower limit for the momentum force." (B.2 Momentum force)
- Limitation (authors): Possible contamination from IRS 4 outflow and spatial filtering  
  > "While the emission of the IRS 4 outflow may in principle contaminate our observations" (B.5 Contamination from IRS 4)
- Caveat (inferred, ours): Result depends on uncertain inclination and bullet-vs-bulk velocity assumption
- Caveat (inferred, ours): Outflow mass strongly depends on tau12 assumption and Tex=30 K
- Caveat (inferred, ours): Possible 12CO contamination from IRS 4 and filtered ambient emission
- Caveat (inferred, ours): No ALMA project code given

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Reduced datacubes at CDS  
  > "The reduced datacubes are available at the CDS via anonymous ftp" (Footnote 1)
- Missing: Project code and scheduling block details in text
- Missing: Clean mask and iteration settings
- Missing: Exact 13CO/12CO threshold per-pixel implementation
- Missing: Line-free channels for uvcontsub
- Data volume (inferred): ~50-150 GB raw for five execution blocks of Band 7 12-m data
- Score (inferred): 3/5, Imaging parameters and analysis equations are mostly given, but project code, masks and some processing details are missing.
- Rediscovery candidate: no, Project code not printed in paper and several processing details unstated, although archive links to 2015.1.00528.S; results depend on many assumptions.

## Links

- Method: van der Marel et al. 2013 (vdM13) (Outflow mass and momentum force methodology)
- Method: Downes & Cabrit 2007 (DC07) (Perpendicular method and correction factors)
- Method: Cabrit & Bertout 1992 (vmax method and inclination corrections)
- Companion: Belloche et al. 2006 / 2011; Tsitali et al. 2013 (Previous observations and properties of Cha-MMS1)
- Related: ALMA Cycle 3 project linked by archive: 2015.1.00528.S

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00528.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 57,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
