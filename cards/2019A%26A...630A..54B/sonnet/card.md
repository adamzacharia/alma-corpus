# ALMA resolves the hourglass magnetic field in G31.41+0.31

`2019A&A...630A..54B` | Astronomy and Astrophysics 2019 | first author: Beltrán, M. T. | arXiv: 1908.01597 | DOI: 10.1051/0004-6361/201935701

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the magnetic field morphology and strength in the hot molecular core G31.41+0.31 at ~0.2'' resolution, and does the field prevent fragmentation and collapse?  
  > "To better establish the role that the magnetic field plays in the collapse of G31.41+0.31, we carried out Atacama Large Millimeter/submillimeter Array (ALMA) observations of the polarized dust continuum emission at 1.3 mm" (abstract)
- Target **G31.41+0.31**: coordinates RA(J2000)=18h47m34.308s, Dec(J2000)=-01d12m45.90s (phase center)  
  > "New parallax observations (Reid et al., in prep) have located this high-mass star-forming region much closer, at 3.7 kpc." (1 Introduction); "The phase reference center of the observations is $\alpha$(J2000)$=18^{\rm h}\,47^{\rm m}\,34.308s$, $\delta$(J2000)$=-01^\circ\,12^\prime\,45.90\ensuremath{''}$." (2 Observations); z/distance 3.7 kpc  
  > "New parallax observations (Reid et al., in prep) have located this high-mass star-forming region much closer, at 3.7 kpc." (1 Introduction); "The phase reference center of the observations is $\alpha$(J2000)$=18^{\rm h}\,47^{\rm m}\,34.308s$, $\delta$(J2000)$=-01^\circ\,12^\prime\,45.90\ensuremath{''}$." (2 Observations); distance from parallax observations (Reid et al., in prep)  
  > "New parallax observations (Reid et al., in prep) have located this high-mass star-forming region much closer, at 3.7 kpc." (1 Introduction); "The phase reference center of the observations is $\alpha$(J2000)$=18^{\rm h}\,47^{\rm m}\,34.308s$, $\delta$(J2000)$=-01^\circ\,12^\prime\,45.90\ensuremath{''}$." (2 Observations)

## Data provenance

- ALMA projects: 2015.1.00072.S
- bands: Band 6, centered at 233 GHz  
  > "The observations were performed in Band 6 centered at 233 GHz and with the array in the C40–5 configuration." (2 Observations)
- frequencies and spectral setup: four 2 GHz spectral windows of 64 channels each (TDM, 31.25 MHz per channel), full polarization  
  > "a spectral setup with four 2 GHz spectral windows of 64 channels each (TDM mode with 31.25 MHz resolution per channel)" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-5  
  > "the array in the C40–5 configuration" (2 Observations)
- baselines: ~17 to 2647 m  
  > "The baselines of the observations range from $\sim$17 to 2647 m." (2 Observations)
- angular resolution: 0.28'' x 0.20'' at PA -60 deg (~875 au)  
  > "The resulting synthesized CLEANed beam of the maps is $0.28\ensuremath{''}\times0.20\ensuremath{''}$ at a position angle PA of $-60^\circ$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 1.2 mJy/beam (Stokes I); 22 uJy/beam (Q, U)  
  > "The rms noise of the maps is 1.2 mJy beam$^{-1}$ for Stokes $I$ and 22 $\mu$Jy beam$^{-1}$ for Stokes $Q$ and $U$." (2 Observations)
- time on source: _not stated_
- observing dates: July 12, 2017 (Cycle 4), two execution blocks  
  > "carried out with ALMA in Cycle 4 on July 12, 2017" (2 Observations)
- pi or archival as stated: PI M. Beltrán  
  > "as part of project 2015.1.00072.S (P.I.: M. Beltrán)" (2 Observations)
- Other facility **ALMA 1.4 mm (BEL18)**: Dust continuum flux at 217 GHz, CH3CN line widths, mass, temperature profile, SiO outflows  
  > "computed from the line width $\Delta V$ of the CH$_3$CN observations of BEL18" (4.2 Magnetic field strength estimate)
- Other facility **SMA 870 um**: Previous 1'' polarization observations (GIR09) for comparison  
  > "$1''$ angular resolution dust polarization observations carried out at 870 $\mu$m with the Submillimeter Array (SMA) reveal" (1 Introduction)
- External data: Dust continuum flux inside 5 sigma at 217 GHz of 3.75 Jy, used to estimate line contamination  
  > "The dust continuum emission inside the $5\sigma$ contour level at 217 GHz is 3.75 Jy." (3.1 Continuum emission) [from Beltrán et al. (cite: beltran18)]
- External data: Core mass 120 Msun at 7.9 kpc (~26 Msun at 3.7 kpc) within R=1.1''  
  > "We note that the mass of 120 $M_\ensuremath{\odot}$ of BEL18 was estimated for a distance of 7.9 kpc." (4.2 Magnetic field strength estimate) [from Beltrán et al. (cite: beltran18)]
- External data: Temperature profile of the core used in the model; mean 250 K  
  > "We assumed the temperature profile modeled by BEL18" (4.1 Modeling the magnetic field) [from Beltrán et al. (cite: beltran18)]
- External data: Mass-to-flux ratio values and flux-tube correction factor 1.4 for toroid models  
  > "(see Table 1 of Li & Shu (cite: li96))" (4.1 Modeling the magnetic field) [from Li & Shu (cite: li96)]
- External data: Dust absorption coefficient kappa=0.008 cm2/g at 217 GHz  
  > "a dust absorption coefficient per unit mass $\kappa_\nu=0.008$ cm$^2$g$^{-1}$ at 217 GHz (Ossenkopf & Henning (cite: ossenkopf94))" (5.4.2 The NE core) [from Ossenkopf & Henning (cite: ossenkopf94)]
- Simulation/model as data: Synthetic Stokes I,Q,U maps from DustPol (ARTIST/LIME) of a magnetostatic singular toroid with poloidal plus toroidal field, passed through simobserve/simanalyze with the observed configuration  
  > "which are straightforwardly used as an input for the tasks `simobserve` and `simanalyze` of CASA, adopting the same antenna configuration of the observing runs" (4.1 Modeling the magnetic field)

## Processing

### Calibration

- pipeline or manual: Data calibrated with CASA; details not given  
  > "The data were calibrated and imaged using the CASA[^1] software package" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasar J1751+0939 (flux and bandpass); J1851+0035 phase; J1924-2914 for instrumental polarization  
  > "Phase calibration was performed on quasar J1851+0035, while flux and bandpass calibrations were performed on quasar J1751+0939." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: Tried but not applied; no improvement  
  > "Therefore, the data presented here have not been self-calibrated." (2 Observations)

### Imaging

- task: CLEAN in CASA; further imaging/analysis in GILDAS  
  > "The final maps were created using the CLEAN task with natural weighting." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The final maps were created using the CLEAN task with natural weighting." (2 Observations)
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
- final beam: 0.28'' x 0.20'', PA -60 deg  
  > "$0.28\ensuremath{''}\times0.20\ensuremath{''}$ at a position angle PA of $-60^\circ$" (2 Observations)
- final rms: 1.2 mJy/beam (I), 22 uJy/beam (Q,U)  
  > "1.2 mJy beam$^{-1}$ for Stokes $I$ and 22 $\mu$Jy beam$^{-1}$ for Stokes $Q$ and $U$" (2 Observations)

### Inherited from earlier work

- Temperature profile, mass, CH3CN line widths, outflow maps and 217 GHz continuum taken from BEL18  
  > "We assumed the temperature profile modeled by BEL18" (4.1 Modeling the magnetic field) [from Beltrán et al. (cite: beltran18)]
- Toroidal force-free field component added following Padovani et al. 2013  
  > "Following Padovani et al. ((cite: padovani13)), we added a toroidal force-free component of the magnetic field" (4.1 Modeling the magnetic field) [from Padovani et al. (cite: padovani13)]
- DCF correction factor xi=0.5  
  > "where $\xi=0.5$ is a correction factor derived from turbulent cloud simulations (Ostriker et al. (cite: ostriker01))" (4.2 Magnetic field strength estimate) [from Ostriker et al. (cite: ostriker01)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure (pipeline vs manual), instrumental polarization calibration details
- CLEAN masks, iterations, threshold, cell and image size
- How the continuum was extracted from the TDM spectral windows (line-free channels)
- Polarization debiasing and Stokes thresholds used for the vector selection
- Pixel sampling and number of angles in the chi-squared test; grid steps in inclination and position angle
- LIME/DustPol settings (grid, density normalization, dust opacity)
- Exact CH3CN line-width measurement positions

## Analysis recipe

1. **Image Stokes I, Q, U and derive polarization quantities**: CLEAN imaging with natural weighting; P=sqrt(Q^2+U^2), p=P/I, psi=0.5 arctan(U/Q); segments rotated 90 deg for B field  
  > "we derived the linear polarization intensity, $P=\sqrt{Q^2+U^2}$, the fractional linear polarization, $p=P/I$, and the polarization position angle" (2 Observations)
   - software: CASA, GILDAS
   - assumption: Polarization from magnetically aligned dust grains  
  > "Assuming that the polarization is produced by magnetically aligned dust grains" (2 Observations)
   - fitting: _not stated_
   - validation: Self-calibration tested but not helpful; scattering ruled out by comparison with SMA 870 um pattern and polarization fractions  
  > "We performed self-calibration using the total intensity (Stokes $I$) image as a model but the images did not improve and we decided not to apply it." (Observations)
2. **Estimate line contamination of Stokes I flux**: Scale 217 GHz continuum flux of BEL18 to 233 GHz with S~nu^(2+beta), beta=1 and 2, compare with measured flux  
  > "We used two different values of the dust emissivity index, $\beta=1$ and 2, and estimated a dust continuum emission flux of 4.64 and 4.98 Jy, respectively." (3.1 Continuum emission)
   - assumption: beta=1 and 2  
  > "We used two different values of the dust emissivity index, $\beta=1$ and 2" (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit magnetostatic toroid model to polarization angles**: DustPol models for grid of lambda (1.63, 2.66, 8.38), b0, phi, i; synthetic maps via simobserve/simanalyze; chi-squared on polarization angles within 5 sigma contour  
  > "For each combination of $\lambda$, $b_0$, $\varphi$, and $i$, we performed a chi-squared test for the difference between the observed and the modeled polarization angles within the $5\sigma$ contour" (4.1 Modeling the magnetic field)
   - software: DustPol/ARTIST, LIME, CASA
   - parameter: effective sound speed 1.4 km/s  
  > "we set the effective sound speed to 1.4 km s$^{-1}$" (4.1 Modeling the magnetic field)
   - assumption: Isothermal model, axially symmetric singular toroid; temperature profile from BEL18  
  > "The model is isothermal, and the value of the sound speed provides the scaling for both the density and the magnetic field strength." (4.1 Modeling the magnetic field)
   - fitting: Reduced chi-squared grid; 1 sigma errors from the method of Lampton et al. 1976  
  > "The $1\sigma$ errors have been estimated using the method of Lampton et al. ((cite: lampton76))." (4.1 Modeling the magnetic field)
   - validation: lambda=8.38 discarded because G31 is optically thick; constant temperature 250 K tested; b0>0.1 discarded  
  > "This allowed us to discard the case $\lambda=8.38$, since we know that G31 is optically thick toward the center (BEL18)." (4.1 Modeling the magnetic field)
4. **Estimate B strength with DCF method**: B_pos = xi*sigma_los/dpsi_int*sqrt(4 pi rho); dispersion from Gaussian fits to residual histogram (4 deg bins) in 15 sigma region; B=B_pos/cos i  
  > "Our modeling provides the inclination with respect to the plane of the sky, $i$, which allows us to estimate the total magnetic field strength as $B=B_{\rm pos}/\cos i \simeq8$–13 mG" (4.2 Magnetic field strength estimate)
   - parameter: sigma_los=2.1 km/s from DeltaV~5 km/s; n=1.4e7 cm-3; R=1.1''; sigma_psi=27.6 and 17.3 deg  
  > "Using $\Delta V\simeq5$ km s$^{-1}$, the value of $\sigma_{\rm los}$ is 2.1 km s$^{-1}$." (4.2 Magnetic field strength estimate)
   - assumption: Distance 3.7 kpc, spherical symmetry, xi=0.5  
  > "Assuming a distance of 3.7 kpc, the mass of the Main core is $\sim$26 $M_\ensuremath{\odot}$" (4.2 Magnetic field strength estimate)
   - fitting: Gaussian fits to residual distribution, full and limited to +-45 deg  
  > "A Gaussian fit over the whole distribution of residuals gives an average value of $0.6^\circ \pm 27.6^\circ$." (Magnetic field strength estimate)
   - validation: Compared with GIR09 B_pos corrected for distance (~20 mG for i=-45 deg)  
  > "GIR09 have estimated a value of $B_{\rm pos}$ of $\sim 14$ mG (corrected for a distance of 3.7 kpc)" (4.2 Magnetic field strength estimate)
5. **Derive mass-to-flux ratio**: lambda=2 pi G^0.5 M/Phi with Phi=pi R^2 B; M = 26 Msun core + 20 Msun star; times 1.4 correction  
  > "We then multiply the latter by a correcting factor equal to 1.4 (Li & Shu (cite: li96)) to obtain $\lambda\sim 1.4$–$2.2$, slightly supercritical." (4.2 Magnetic field strength estimate)
   - assumption: Bolometric luminosity 4.4e4 Lsun from a single main-sequence star of ~20 Msun (O8.5-O9)  
  > "then the mass of such star would be of $\sim$20 $M_\ensuremath{\odot}$, corresponding to an O8.5–O9 star" (4.2 Magnetic field strength estimate)
   - fitting: _not stated_
   - validation: Consistent with model lambda=2.66  
  > "we believe that the mass-to-flux ratio computed from the observations is consistent with $\lambda=2.66$ assumed for the model" (4.2 Magnetic field strength estimate)

## Software

- **CASA** : Calibration, imaging (CLEAN), simobserve/simanalyze of model maps  
  > "The data were calibrated and imaged using the CASA[^1] software package" (2 Observations)
- **GILDAS** : Further imaging and analysis  
  > "Further imaging and analysis were done with the GILDAS[^2] software package." (2 Observations)
- **DustPol (ARTIST)** : Model polarized dust emission of magnetized toroid  
  > "we used the *DustPol* module of the ARTIST package (Padovani et al. (cite: padovani12)) to model the magnetic field morphology" (4.1 Modeling the magnetic field)
- **LIME** : Radiative transfer ray-tracing underlying DustPol  
  > "The *DustPol* module is an extension to the Line Modeling Engine (LIME) radiative transfer code" (4.1 Modeling the magnetic field)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total flux inside 5 sigma contour (Stokes I) | 6.86 | 0.06 | Jy | 1 | is $6.86 \pm 0.06$ Jy, while the peak flux is $369 \pm 1$ mJy beam$^{-1}$ |
| Peak Stokes I flux | 369 | 1 | mJy/beam | 1 | the peak flux is $369 \pm 1$ mJy beam$^{-1}$ |
| Line contamination of Stokes I flux | 48% (beta=1), 38% (beta=2) | not stated | percent | 2 | the line contamination of the total flux at 233 GHz would be of 48% for $\beta=1$ and 38% for $\beta=2$ |
| Polarization fraction range in HMC | 0.1 to 13 | not stated | percent | 1 | The polarization fraction in the HMC ranges from 0.1% to 13%. |
| Maximum polarized flux | 2.4 | not stated | mJy/beam | 1 | with a maximum polarized flux of 2.4 mJy beam$^{-1}$ |
| Best-fit inclination | -45 | +3/-4 | deg | 3 | the best model is given by $\lambda=2.66$, $i=-{45^\circ}_{-4^\circ}^{+3^\circ}$ |
| Best-fit magnetic axis position angle | -44 | +6/-4 | deg | 3 | $\varphi=-{44^\circ}_{-4^\circ}^{+6^\circ}$ |
| Residual dispersion sigma_psi | 27.6 (full) and 17.3 (limited to +-45 deg) | not stated | deg | 4 | the standard deviations on the polarization angle dispersion from the two Gaussian fits, $\sigma_\psi$, are $27.6^\circ$ and $17.3^\circ$ |
| Total magnetic field strength | 8-13 | not stated | mG | 4 | $B=B_{\rm pos}/\cos i \simeq8$–13 mG, for an intrinsic dispersion of $27.6^\circ$ and $17.3^\circ$, respectively |
| Mass-to-flux ratio lambda | 1.4-2.2 | not stated | dimensionless | 5 | to obtain $\lambda\sim 1.4$–$2.2$, slightly supercritical |
| Alfven velocity | 3-5 | not stated | km/s | 5 | we obtain an Alfvén velocity in the range 3–5 km s$^{-1}$ |
| Turbulent to uniform field ratio dB/B | ~0.7 and ~1 | not stated | dimensionless | 4 | we obtain $\delta B/B\sim0.7$ and $\sim1$, for $\delta\psi= 17.3^\circ$ and $27.6^\circ$, respectively |
| NE core mass | 3-6.5 | not stated | Msun | 0 | we obtain a mass of the core $M_{\rm NE}\simeq3$–6.5 $M_\odot$ |

## Qualitative findings

- Hourglass-shaped field is confirmed down to <1000 au scales and is perpendicular to the NE-SW velocity gradient, supporting rotation over the outflow interpretation  
  > "it supports the hypothesis that the velocity gradient is due to rotation and discards the molecular outflow scenario proposed by Araya et al." (5.2 Confirming the rotating toroid model)
- Field deviates from model near embedded sources, NE core and outflow walls  
  > "our model fails to properly describe the magnetic field close to the center of the Main core, around the NE core, and at the northern and southwestern edges of the Main core" (5.4 Perturbation of the magnetic field)

## Claim tuples

- H: The field in G31 is an hourglass consistent with a magnetized toroid | E: Fit DustPol toroid models to ALMA 1.3 mm polarization angles | R: Best model lambda=2.66, i=-45 deg, phi=-44 deg, b0<=0.1 | F: Field is nearly poloidal and hourglass-shaped down to <1000 au | **supported**
- H: The NE-SW velocity gradient is due to rotation | E: Compare field axis orientation with velocity gradient | R: Field axis perpendicular to gradient | F: Gradient is rotation, with little effect on the field | **supported**
- H: The core is magnetically supercritical | E: DCF field strength and mass-to-flux ratio | R: B~8-13 mG, lambda=1.4-2.2 | F: Slightly supercritical; field does not prevent fragmentation and collapse | **supported**

## Reasoning

- Why this data: Four times higher resolution than previous SMA data, comparable to separation of embedded centimeter sources  
  > "which is four times higher than that of previous (sub)millimeter observations (GIR09) and is similar to the separation of the centimeter continuum sources" (1 Introduction)
- Why this method: _not stated_
- Alternative: Dust self-scattering rejected as origin of polarization since pattern matches 870 um SMA and fractions reach 4-5%  
  > "This suggests that the polarization observations are likely tracing the emission of magnetically-aligned grains and are not affected by dust scattering" (3.2 Polarized emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Stokes I flux is an upper limit because of line contamination; polarization fractions are lower limits  
  > "the polarization fraction has to be taken as a lower limit" (3.2 Polarized emission)
- Limitation (authors): Mass-to-flux ratio is a lower limit because the core mass and stellar content may be underestimated  
  > "the observed value of the mass-to-flux ratio should be taken as a lower limit" (4.2 Magnetic field strength estimate)
- Caveat (inferred, ours): Model lacks turbulent component, so residual dispersion is large and DCF dispersions are bracketed by two Gaussian-fit choices
- Caveat (inferred, ours): Only three lambda values were sampled, and distance changed from 7.9 to 3.7 kpc, which affects mass and flux
- Caveat (inferred, ours): Single-star mass assumption and spherical geometry affect lambda
- Caveat (inferred, ours): TDM spectral resolution contaminates Stokes I, affecting polarization fractions

## Reproducibility

- Data public (paper): ALMA project 2015.1.00072.S acknowledged; public status not stated  
  > "This paper makes use of the ALMA data ADS/JAO.ALMA#2015.1.00072.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and polarization calibration script
- Missing: CLEAN parameters and masks
- Missing: DustPol model grid details and BEL18 temperature/density inputs
- Data volume (inferred): ~10-50 GB (two execution blocks, full polarization, 4 spw TDM)
- Score (inferred): 3/5, Data identified and the modeling approach is clear, but calibration and imaging details and model settings are sparse, and the DustPol model depends on external inputs.
- Rediscovery candidate: no, Recipe is incomplete for the CASA reduction and the modeling pipeline (DustPol/LIME with BEL18 inputs), though results are numeric.

## Links

- Method: Padovani et al. (cite: padovani12) (DustPol module for polarized dust emission modeling)
- Method: Padovani et al. (cite: padovani13) (Toroidal field component added to the toroid model)
- Method: Li & Shu (cite: li96) (Magnetostatic singular toroid model)
- Companion: Girart et al. (cite: girart09) (Previous SMA 870 um polarization observations of G31)
- Companion: Beltrán et al. (cite: beltran18) (ALMA 1.4 mm continuum and line observations of G31 used for inputs)
- Related: ALMA project 2016.1.00223 (PI M. Beltrán), 0.08'' observations at 1.4 and 3.5 mm

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 59,
  "rate": 0.694
 },
 "evidence_ok": true
}
```
