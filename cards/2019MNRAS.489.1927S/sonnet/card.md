# Testing the blast-wave AGN feedback scenario in MCG-03-58-007

`2019MNRAS.489.1927S` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Sirressi, M. | arXiv: 1906.00985 | DOI: 10.1093/mnras/stz2249

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Does the molecular gas in MCG-03-58-007 show a momentum-boosted outflow, as expected from energy-conserving blast-wave AGN feedback, given its X-ray UFO?  
  > "We compare the momentum rate ($\dot{P}$) and kinetic power ($\dot{E}$) of such putative molecular outflow with that of the X-ray UFO" (abstract)
- Target **MCG-03-58-007**: coordinates RA 22h49m37.16s, Dec -19d16'26.4" (CO peak)  
  > "a local ($z=0.03236\pm0.00002$, this work) AGN" (abstract); "The peak emission is located at RA = $22h\,49m\,37.16s\,\pm\,0.07\,s$" (2.3 Modelling of the main rotating disk); z/distance z = 0.03236 ± 0.00002; 1" = 0.67 kpc  
  > "a local ($z=0.03236\pm0.00002$, this work) AGN" (abstract); "The peak emission is located at RA = $22h\,49m\,37.16s\,\pm\,0.07\,s$" (2.3 Modelling of the main rotating disk); distance from redshift refined from CO(1-0) rotation curve centroid (this work)  
  > "a local ($z=0.03236\pm0.00002$, this work) AGN" (abstract); "The peak emission is located at RA = $22h\,49m\,37.16s\,\pm\,0.07\,s$" (2.3 Modelling of the main rotating disk)

## Data provenance

- ALMA projects: 2016.1.00694.S
- bands: Band 3  
  > "We observed MCG-03-58-007 with ALMA Band 3 during Cycle 4" (1.2 ALMA observations)
- frequencies and spectral setup: 4 spws; CO(1-0) spw at 111.682 GHz (1.875 GHz wide, 1.95 MHz res); CN spw at 109.952 GHz; two lower-sideband continuum spws of 2 GHz at 97.952 and 99.807 GHz  
  > "we placed one spectral window centred at $\nu_{obs}=111.682\,\rm GHz$ for detecting the CO J=1-0" (1.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 12-m, 40 antennas  
  > "We used a compact configuration of 40 12-m antennas" (1.2 ALMA observations)
- configurations: C40-1  
  > "Array configuration     | C40-1" (Table 1)
- baselines: _not stated_
- angular resolution: 3.3" x 2.0" (2.2 x 1.3 kpc)  
  > "The final synthesized beam has an average size of $3.3\ensuremath{''}$ x $2.0\ensuremath{''}$" (1.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 2.2 mJy/beam per 5.2 km/s channel  
  > "The achieved rms sensitivity is $2.2\,\rm mJy / beam / 5.2\,\rm km\,s^{-1}$" (1.2 ALMA observations)
- time on source: 7.4 min in text; 6.70 min in Table 1  
  > "with an on-source time of $\rm 7.4\,min$" (1.2 ALMA observations); "On-source time          | $\rm 6.70\,min$" (Table 1)
- observing dates: 11 March 2017  
  > "The observations were carried out on 11 March 2017" (1.2 ALMA observations)
- pi or archival as stated: PI P. Severgnini, Cycle 4  
  > "Project code: 2016.1.00694.S, PI: P. Severgnini" (1.2 ALMA observations)
- Line: CO J=1-0 (not stated)
- Line: CN N=1-0 doublet (not stated)
- Other facility **Suzaku, XMM-Newton, NuSTAR**: X-ray UFO properties (from literature)  
  > "Follow-up XMM-Newton and NuSTAR observations in 2015 confirmed the presence of the $v_1=0.1c$ zone of the wind" (1.1 The target galaxy)
- Other facility **6dF**: optical spectrum showing blue-shifted [OIII] wings  
  > "the 6dF optical spectrum (cite: jones20096df) of MCG-03-58-007 shows blue-shifted wings" (3.1 Case I)
- External data: X-ray UFO energetics (Edot 2.4e44 erg/s, pdot 2e35, Mdot 1.5 Msun/yr)  
  > "The kinetic power of the persistent component of the wind is $\dot{E}_{k1} \sim 2.4\cdot10^{44}\,\rm erg\,s^{-1}$" (1.1 The target galaxy) [from (cite: braito2018new)]
- External data: SFR = 20.1±0.9 Msun/yr and L_IR  
  > "A star formation rate of SFR=$20.1\pm0.9\,\rm M_{\odot}~yr^{-1}$ was estimated by" (1.1 The target galaxy) [from (cite: Gruppioni201610.1093/mnras/stw577)]
- External data: alpha_CO = 3.1±2.1 average of nearby star-forming galaxies  
  > "Such conversion factor is the average of the values calculated in nearby star-forming galaxies by (cite: Sandstrom2013ApJ...777....5S)" (2.2 Morphology) [from (cite: Sandstrom2013ApJ...777....5S)]
- External data: outflow alpha_CO = 2.1 (NGC 6240)  
  > "which is the value calculated by (cite: Cicone2018ApJ...863..143C) for the molecular outflow of NGC 6240" (3.1 Case I) [from (cite: Cicone2018ApJ...863..143C)]
- External data: earlier redshift z=0.03220 and SEST CO frequency  
  > "older redshift of $z=0.03220$ measured by (cite: Strong2004MNRAS.353.1151S)" (2.1) [from (cite: Strong2004MNRAS.353.1151S)]
- External data: L_CO-SFR correlation for local SF galaxies  
  > "we use the $L_{CO}-SFR$ correlation computed for a sample of local SF galaxies (cite: Cicone+17)" (3.1.2 The role of SF feedback) [from (cite: Cicone+17)]
- External data: SF wind and SN output predictions  
  > "Using the theoretical predictions of the stellar winds and SNe output in the ISM (cite: Veilleux2005ARA&A..43..769V)" (3.1.2 The role of SF feedback) [from (cite: Veilleux2005ARA&A..43..769V)]

## Processing

### Calibration

- pipeline or manual: calibration pipeline  
  > "The calibration pipeline was launched with CASA version 4.7, to produce the visibility files." (1.2 ALMA observations)
- casa version: pipeline CASA 4.7; reduction/analysis CASA 5.4  
  > "The data reduction and analysis were performed with CASA version 5.4." (1.2 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (calibrators J2258-2758, Uranus, J2236-1433 for flux, bandpass, phase)  
  > "Three calibrators (J2258-2758, Uranus, J2236-1433) were used for fixing the flux density scale" (1.2 ALMA observations)
- flux scale uncertainty: 6%  
  > "The uncertainty on the total flux is dominated by the ALMA calibration error of 6%." (Table 2 caption)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "The CO(1-0) line emission image was deconvolved using the `TCLEAN` task with Briggs weighting (robust = 0.0)." (1.2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.0  
  > "Briggs weighting (robust = 0.0)" (1.2 ALMA observations)
- uv taper: _not stated_
- cell size: 0.2"  
  > "a pixel size of 0.2$\ensuremath{''}$" (1.2 ALMA observations)
- image size: _not stated_
- masking: automask (per-channel)  
  > "we ultimately used the `AUTOMASK` parameter" (1.2 ALMA observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on visibilities  
  > "The 3-mm continuum emission was subtracted using the task `UVCONTSUB` from the *uv* visibilities." (2.1)
- line free channels: -2500 to -500 and 500 to 2500 km/s  
  > "corresponding to velocities (-2500, -500) $\rm km\,s^{-1}$ and (500, 2500) $\rm km\,s^{-1}$" (2.1)
- primary beam correction: included in cleaning  
  > "The primary beam correction was included in the cleaning task" (1.2 ALMA observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 3.3" x 2.0"  
  > "Synthesized beam        | $3.3\ensuremath{''} x 2.0\ensuremath{''}$" (Table 1)
- final rms: 2.2 mJy/beam per 5.2 km/s  
  > "Rms sensitivity         | $2.2\,\rm mJy / beam / 5.2\,\rm km\,s^{-1}$" (Table 1)

### Inherited from earlier work

- 3D BAROLO 5% residual-increase error criterion is the software default  
  > "The variation of 5% is the default value chosen by the authors of the software Barolo 3D" (2.3) [from (cite: DiTeodoro2015MNRAS.451.3021D)]
- Gas mass computed with the formula of Solomon & Vanden Bout  
  > "using the formula given by (cite: solomon2005molecular)" (2.2) [from (cite: solomon2005molecular)]

### Not stated but needed to reproduce (our reading)

- tclean niter/threshold details, deconvolver, image size
- Spectral window used for the line imaging cube and exact velocity gridding (rest frequency)
- 3D BAROLO parameter file (free parameters, VDISP, normalization, mask settings, thickness)
- Gaussian fitting details of the multi-component CO spectrum
- Details of SFR(r<2 kpc) scaling from L_CO
- Formula/line luminosity conversion details and uncertainty propagation

## Analysis recipe

1. **Continuum subtraction and redshift refinement**: uvcontsub using line-free channels; centroid of CO PV rotation curve taken as systemic velocity  
  > "By setting the centroid of the CO(1-0) rotation curve equal to the systemic velocity of the galaxy, we obtain a new redshift estimate" (2.1)
   - software: CASA
   - parameter: PV axis PA = 42 deg  
  > "extracted along an axis with a Position Angle (PA) of 42$^\circ$" (2.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Total CO spectrum and molecular gas mass**: Multi-Gaussian fit of spectrum in a 25" aperture; Solomon formula with alpha_CO = 3.1±2.1  
  > "we modelled the spectrum with multiple Gaussian functions to measure the total flux and luminosity of the CO(1-0) line" (2.2)
   - parameter: circular aperture 25"  
  > "extracted from a circular aperture of $25\ensuremath{''}$" (2.2)
   - assumption: alpha_CO = 3.1±2.1 Msun (K km/s pc^2)^-1; H0=70  
  > "CO-to-$\rm H_2$ conversion factor of $\alpha_{CO}=3.1\pm2.1" (2.2)
   - fitting: Gaussian components, 6 fitted  
  > "For this reason we modelled the spectrum with multiple Gaussian functions to measure the total flux and luminosity of the CO(1-0) line." (2.2 Morphology of the CO line emission)
   - validation: _not stated_
3. **Model the rotating disk**: 3D BAROLO fit of thin rotating disk with 8 rings, geometry (i, PA, centre) fixed from moment maps  
  > "we used 8 rings of 1.34 kpc width, which is comparable with the angular resolution scale of the ALMA data" (2.3)
   - software: 3D BAROLO, CASA imsubimage
   - parameter: i = 37±10 deg, PA = 42 deg  
  > "We derived a value of $i=37\pm10\,\rm deg$" (2.3)
   - parameter: fit pixels with S/N >~ 3  
  > "The fitting was performed considering only pixels with a S/N$\gtrsim3$." (2.3)
   - assumption: geometrically thin disk dominated by pure rotation  
  > "all the emitting material of the galaxy is confined to a geometrically thin disk and its kinematics is dominated by pure rotational motion" (2.3)
   - fitting: 3D BAROLO minimisation; errors from 5% increase of residuals function  
  > "The error on each parameter is taken as the variation that produces an increase of 5$\%$ in the residuals function." (2.3)
   - validation: data vs model moment maps and PV diagrams compared  
  > "Figure [7](#fig:data-model_Maps) shows the comparison between the data (left-column panels) and the best-fit model" (2.3)
4. **Subtract disk and characterise residuals**: Subtract model cube; integrate residuals over (-222,-148) and (121,195) km/s; fit Gaussians to red/blue spectra  
  > "obtained by integrating the residual flux over the spectral ranges $(-222,-148)\,\rm km\,s^{-1}$ and $(121,195)\,\rm km\,s^{-1}$" (2.4)
   - software: CASA
   - fitting: Gaussian fits to residual spectra  
  > "We modelled both spectra with a Gaussian and computed the fluxes in Table" (2.4 The CO(1-0) residual emission)
   - validation: _not stated_
5. **Outflow energetics and comparison with X-ray UFO**: Biconical model, tau_dyn=R/v_out, Mdot=M/tau, Pdot=Mdot v, Edot=0.5 Mdot v^2; ratios to UFO  
  > "The dynamical time of the outflow is calculated as $\tau_{dyn} = R/v_{out}$" (3.1)
   - assumption: cone axis at 45 deg to line of sight; alpha_CO^out = 2.1 (range 0.8-3.4)  
  > "assuming for simplicity that the axes of the model cones form an angle of 45$^\circ$ with the line of sight" (3.1)
   - fitting: _not stated_
   - validation: SF contribution tested via scaled SFR and SN power  
  > "we find that SF activity can trigger a mass-loss rate of $\dot{M}_{SF}=2.7\,\rm M_{\odot}\,yr^{-1}$ within a radius of 2 kpc" (3.1.2)

## Software

- **CASA** 4.7 (pipeline), 5.4 (analysis): calibration, tclean imaging, uvcontsub, imsubimage  
  > "The data reduction and analysis were performed with CASA version 5.4." (1.2 ALMA observations)
- **3D BAROLO** : rotating disk modelling  
  > "We used the software 3D-Based Analysis of Rotating Object via Line Observations (3D BAROLO)" (2.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Redshift | 0.03236 | 0.00002 | dimensionless | 1 | we obtain a new redshift estimate of $z=0.03236\pm0.00002$ |
| 3-mm continuum flux density | 0.60 | 0.10 | mJy | 1 | We measure a continuum flux density of $0.60\pm0.10$ mJy at $\nu_{obs}=99\,\rm GHz$. |
| Total CO(1-0) flux | 65 | 4 | Jy km/s | 2 | 65 $\pm$ 4 |
| Total molecular gas mass | 9e9 (alpha_CO/3.1) | 6e9 | Msun | 2 | $M_{H2}\simeq(9 \pm 6)\frac{\alpha_{CO}}{3.1} \cdot 10^9\,\rm M_{\odot}$ |
| Disk CO(1-0) flux | 50 | 3 | Jy km/s | 3 | $S^{\rm disk}_{\rm CO}=50\pm3\,\rm Jy\,km\,s^{-1}$ |
| Disk fraction of total CO | 78 | not stated | percent | 3 | This corresponds to 78$\%$ of the total molecular gas traced by the CO(1-0) emission detected by ALMA. |
| Disk inclination | 37 | 10 | deg | 3 | $i=37\pm10\,\rm deg$ |
| Residual red flux | 2.39 | 0.14 | Jy km/s | 4 | Red / 157 $\pm$ 5 / 2.39 $\pm$ 0.14 |
| Residual blue flux | 3.07 | 0.18 | Jy km/s | 4 | Blue / -182 $\pm$ 5 / 3.07 $\pm$ 0.18 |
| Outflow mass-loss rate | 54 (alpha_CO/2.1) | not stated | Msun/yr | 5 | $54\frac{\alpha_{CO}}{2.1}$ |
| Outflow momentum rate | 8e34 | not stated | g cm s^-2 | 5 | $8\cdot 10^{34}$ |
| Outflow kinetic power | 1.0e42 | not stated | erg/s | 5 | $1.0 \cdot 10^{42}$ |
| Pdot_mol/Pdot_UFO | ~0.4 | not stated | dimensionless | 5 | The ratio between the momentum rates of the two outflows is $\dot{P}_{mol}/\dot{P}_{UFO}\sim0.4$. |
| Edot_mol/Edot_UFO | ~4e-3 | not stated | dimensionless | 5 | $\dot{E}_{mol}/\dot{E}_{UFO}\sim4\cdot10^{-3}$ |
| SFR within 2 kpc | 10 | 5 | Msun/yr | 5 | SFR$(r<2\,\rm kpc) = 10 \pm 5\,\rm M_{\odot}\,yr^{-1}$ |

## Qualitative findings

- CO(1-0) is dominated by a galaxy-size rotating disk; no high-velocity (>250 km/s) CO emission detected  
  > "At the sensitivity of our data, we do not detect any signature of very high-velocity molecular outflows ($v>250$ km s$^{-1}$)." (4)

## Claim tuples

- H: Is there a momentum-boosted molecular outflow driven by the X-ray UFO? | E: Subtract 3D BAROLO disk model and derive outflow energetics from the residuals | R: Pdot ratio ~0.4, Edot ratio ~4e-3 | F: Rules out momentum-boosted energy-conserving outflow | **supported**
- H: Is the residual CO a low-velocity outflow or a rotating structure? | E: Compare outflow and CND interpretations | R: Structure 10-100x larger and more massive than typical CNDs | F: Outflow favoured but rotating structure not excluded | **partially**

## Reasoning

- Why this data: Moderate SFR plus powerful X-ray UFO makes AGN feedback dominant over SF, enabling test of blast-wave models  
  > "hence we expect AGN feedback processes to dominate over SF feedback" (Introduction)
- Why this method: _not stated_
- Alternative: Purely SF-driven outflow would need a high coupling efficiency; radiation pressure and radio jet alternatives not testable/less favoured  
  > "Hence, the energetics of the putative outflow would be hard to reconcile with a purely star formation-driven feedback process." (3.1.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Low spatial resolution prevents constraining geometry of the residual structure  
  > "The limited spatial resolution of the ALMA data does not allow us to constrain the geometry of this structure;" (3.2)
- Limitation (authors): No formal error on outflow alpha_CO  
  > "We cannot quote a formal statistical error for the $\alpha^{out}_{CO}$ parameter" (3.1)
- Caveat (inferred, ours): Residuals depend on thin-disk model; imperfect subtraction may mimic outflow
- Caveat (inferred, ours): Very short integration and coarse beam; outflow geometry assumed (45 deg)
- Caveat (inferred, ours): Large alpha_CO uncertainty propagates to ratios
- Caveat (inferred, ours): Inconsistent on-source time (7.4 vs 6.7 min)

## Reproducibility

- Data public (paper): Project code and acknowledgement given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00694.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: 3D BAROLO parameter settings
- Missing: tclean niter/image size details
- Missing: Gaussian fit initial guesses
- Data volume (inferred): ~5-20 GB raw (single short Band 3 execution)
- Score (inferred): 3/5, Single archival-style dataset with clear imaging and analysis steps, but key 3D BAROLO and tclean settings are missing.
- Rediscovery candidate: yes, Single short ALMA dataset with a mostly specified recipe and numeric results (disk flux, residual fluxes, energetics).

## Links

- Method: (cite: DiTeodoro2015MNRAS.451.3021D) (3D BAROLO disk fitting)
- Companion: (cite: braito2018new) (X-ray UFO properties in this source)

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 62,
  "rate": 0.756
 },
 "evidence_ok": true
}
```
