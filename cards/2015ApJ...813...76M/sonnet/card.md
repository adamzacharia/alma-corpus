# Compact Dust Concentration in the MWC 758 Protoplanetary Disk

`2015ApJ...813...76M` | The Astrophysical Journal 2015 | first author: Marino, S. | arXiv: 1505.06732 | DOI: 10.1088/0004-637X/813/1/76

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Do the VLA Ka and ALMA Band 7 continuum maps of MWC 758 show grain-size segregation consistent with dust trapping in a vortex or pressure maximum?  
  > "We analyse new VLA Ka & Ku observations and we compare with ALMA archival data to study the distribution of dust grains and search for evidence of grain size segregation due to dust trapping." (Introduction)
- Target **MWC 758**: coordinates RA 05h30m27.530s, Dec +25d19m57.082s (J2000)  
  > "|    RA (J2000)    | $05^{h} \ 30^{m} \ 27.530^{s}$ |     \(1\)      |
|   DEC (J2000)    | $+25^{\circ} \ 19'\  57.082''$ |" (Table 1); "|   DEC (J2000)    | $+25^{\circ} \ 19'\  57.082''$ |     \(1\)      |" (Table 1); z/distance 279 (+94/-58) pc  
  > "The revised *Hipparcos* parallax data put the star at a distance of $279^{+94}_{-58}$ pc (cite: vanLeeuwen2007)" (Introduction); "|     Distance     |      $279^{+94}_{-58}$ pc      |     \(1\)      |" (Table 1); distance from revised Hipparcos parallax (van Leeuwen 2007)  
  > "The revised *Hipparcos* parallax data put the star at a distance of $279^{+94}_{-58}$ pc (cite: vanLeeuwen2007)" (Introduction); "\(1\) (cite: vanLeeuwen2007)" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00320.S
- bands: ALMA Band 7 (~337 GHz); VLA Ka (~33 GHz) and Ku (~15 GHz)  
  > "VLA Ka ($\sim$33 GHz) & Ku ($\sim$15 GHz) and ALMA Band 7 ($\sim$337 GHz) data" (2 Observations and Imaging)
- frequencies and spectral setup: 4 spectral windows centred at 337.773, 344.469, 332.488, 330.565 GHz, 384 channels, FDM  
  > "4 spectral windows divided in 384 channels, centered at 337.773 GHz with a total bandwidth of 234.363 MHz" (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: 29 12-m antennas  
  > "The observations were carried with 29 antennas of 12 meter diameter." (2.2 ALMA)
- configurations: _not stated_
- baselines: ALMA 15-375 m  
  > "The minimum and maximum projected baselines were 15 and 375 m" (2.2 ALMA)
- angular resolution: MEM model 0.31''x0.18''; restored Clean beam 0.64''x0.40''  
  > "The model image has an approximate resolution of $0.31''\times0.18''$, derived from the response to a point source." (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: ALMA restored image noise 1.3 mJy/beam  
  > "a peak intensity of 55.0 mJy beam $^{-1}$ and a noise level of 1.3 mJy beam$^{-1}$" (2.2 ALMA)
- time on source: ALMA 12 min  
  > "the total time on source was 12 min" (2.2 ALMA)
- observing dates: ALMA: August and October 2012  
  > "The observations were conducted over two nights in August and October of 2012." (2.2 ALMA)
- pi or archival as stated: archival, project 2011.0.00320.S (Chapillon et al. 2015 in prep)  
  > "ALMA archival data in Band 7 of MWC 758 from the project 2011.0.00320.S (cite: Chapillon2015)" (2.2 ALMA)
- Line: CO J=3-2 (flagged) (337.79599 GHz)
- Line: 13CO J=3-2 (flagged) (330.58797 GHz)
- Other facility **VLA**: new Ka and Ku continuum observations (project 13B-273)  
  > "The VLA observations form part of the project VLA 13B-273." (2.1 VLA)
- Other facility **VLT SPHERE/IRDIS**: public Y-band PDI scattered light data  
  > "publicly available VLT SPHERE/IRDIS PDI (polarimetric differential imaging) data (cite: Benisty2015)" (3.5 Comparison with SPHERE PDI data)
- External data: 230 GHz flux used for the 230-337 GHz spectral index  
  > "Data from (cite: Chapillon2008)." (Table 2) [from Chapillon2008]
- External data: Stellar mass, inclination, PA  
  > "(cite: Isella2010) determined a stellar mass of $2.0 \pm 0.2
M_{\odot}$ and a disk orientation with an inclination ($i$) of $21\pm2^{\circ}$ and a position angle (PA) of $65 \pm 7^{\circ}$" (Introduction) [from Isella2010]
- Simulation/model as data: Parametric non-axisymmetric vortex disk model computed with RADMC-3D, compared with ALMA/VLA images and SED  
  > "We develop a parametric non-axisymmetric disk model, inspired by the steady state vortex solution to the gas and dust distribution described in (cite: Lyra2013)" (3.4 Parametric non-axisymmetric model)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: VLA: 3c138 primary flux calibrator; J0547+2721 phase calibrator  
  > "3c138 was used as primary flux calibrator, while J0547+2721 was used as phase calibrator" (2.1 VLA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: uvmem (maximum entropy) deconvolution; restored by adding residual dirty map and convolving with Clean beam  
  > "The deconvolved model images are ’restored’ by adding the dirty map of the residuals of uvmem and convolving with a Clean beam characteristic of natural or briggs weighting." (2 Observations and Imaging)
- deconvolver: _not stated_
- weighting robust: natural for VLA; briggs for ALMA (robust not stated)  
  > "the beam size is $0.23''\times0.22''$ with natural weights" (2.1.1 VLA images)
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
- final beam: ALMA restored 0.64''x0.40''; VLA Ka 0.23''x0.22'' (natural)  
  > "convolving with a Clean beam of size $0.64''\times0.40''$ characteristic of *briggs* weighting" (2.2 ALMA)
- final rms: ALMA 1.3 mJy/beam; VLA Ka 6.6 uJy/beam; Ku 4.1 uJy/beam  
  > "The Ka image presents a noise level ($\sigma$) of 6.6 $\mu$Jy beam$^{-1}$" (2.1.1 VLA images)

### Inherited from earlier work

- Vortex steady-state density solution (eq. 64) and scale function f(chi)  
  > "We add the vortex steady state solution described by eq. 64 in L$^2$13" (3.4 Parametric non-axisymmetric model) [from Lyra & Lin 2013 (cite: Lyra2013)]
- Vortex frequency omega_V from Goodman-Narayan-Goldreich solution  
  > "To compute $\omega_V$ we use the Goodman-Narayan-Goldreich solution (cite: Goodman1987)." (3.4 Parametric non-axisymmetric model) [from Goodman1987]
- SPHERE PDI reduction similar to Avenhaus et al. 2014 appendix  
  > "The polarized flux was calculated and instrumental effects accounted for in a way similar to that described in the Appendix of (cite: Avenhaus2014)." (3.5 Comparison with SPHERE PDI data) [from Avenhaus2014]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size and image size for ALMA
- uvmem regularization/entropy settings and weights
- ALMA calibration details and CASA version, flux calibrator
- VLA calibration software and flux scale accuracy
- Line-free channels / continuum selection beyond flagging CO lines
- Chapillon et al. 2015 calibration details (in prep)
- Sigma_c normalization and exact grain size bins of the 7 outer dust species
- How spectral index uncertainties were computed

## Analysis recipe

1. **Image VLA and ALMA continuum**: MEM deconvolution with uvmem; restored images with Clean beam  
  > "The image synthesis was carried out using a non-parametric least-squares modeling technique with a regularization term called entropy" (2 Observations and Imaging)
   - software: uvmem
   - fitting: _not stated_
   - validation: simulated VLA observations of 337 GHz model show no flux loss (620±27 vs 609 uJy)  
  > "This is consistent with the scaled model flux of 609 $\mu$Jy within the estimated errors." (2.1.2 Flux loss)
2. **Spectral indices and flux**: alpha = log(I2/I1)/log(nu2/nu1) between bands and intra-band  
  > "defined as $\alpha_{\nu_1}^{\nu_{2}}=\log(I_2/I_1)/\log(\nu_2/\nu_1)$" (3.1 Spectral trends)
   - assumption: free-free spectral index 0.5-1.0 for stellar emission  
  > "Assuming a spectral index between 0.5 and 1.0 from free-free emission" (3.1 Spectral trends)
   - fitting: point source fit to Ku channels  
  > "computed from a point source fit to the Ku data at the different channels" (3.1 Spectral trends)
   - validation: _not stated_
3. **Compare compactness at matched resolution**: Convolve star-subtracted VLA Ka image with ALMA Clean beam; compare solid angle within 0.85 peak contour  
  > "we convolved the restored VLA Ka image with the ALMA Clean synthetic beam of size $0.64''\times0.40''$ after subtracting the stellar emission." (3.3 ALMA and VLA Ka map at the same resolution level)
   - fitting: _not stated_
   - validation: _not stated_
4. **Parametric vortex disk model and radiative transfer**: Axisymmetric background plus vortex density with extended size r_s; 9 dust species; RADMC-3D images and SED; simulated observations with same uv coverage  
  > "We implement the model using 9 dust species in total" (3.4 Parametric non-axisymmetric model)
   - software: RADMC-3D 0.39
   - parameter: chi=5, delta_t=3e-3, r_c=120 au, gamma=-2.0, r_s=3  
  > "We set $r_c=120.0$ au and $\gamma=-2.0$" (3.4 Parametric non-axisymmetric model)
   - assumption: total gas mass 0.1 M*; grain size distribution index -3.5; Mie opacities with amorphous carbon and astronomical silicate  
  > "The total gas mass in the disk is 0.1 $M_{\ast}$." (3.4 Parametric non-axisymmetric model)
   - fitting: manual parameter selection to match ALMA restored image, VLA, SED; no formal fit  
  > "We set $r_s=3$ to have a good match between the restored ALMA image and the model image convolved with the synthetic ALMA beam" (3.4 Parametric non-axisymmetric model)
   - validation: compare simulated observations and model SED with data  
  > "we present the model SED that matches roughly the observations" (3.4 Parametric non-axisymmetric model)

## Software

- **uvmem** : MEM image synthesis of VLA and ALMA data  
  > "We call the whole algorithm and code *uvmem*" (2 Observations and Imaging)
- **RADMC-3D** 0.39: radiative transfer model images and SED  
  > "computed using RADMC-3D version 0.39" (3.4 Parametric non-axisymmetric model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA Band 7 restored total flux | 210 | ±5 | mJy | 1 | the total flux is $210\pm5$ mJy |
| VLA Ka flux within 1" radius | 366 | ±49 | uJy | 1 | $366\pm49 \mu$Jy and $289\pm33\mu$Jy after subtracting the stellar emission |
| Ka-band to Band 7 spectral index of northern clump | 3.1 | ±0.1 | dimensionless | 2 | $\alpha_{Ka}^{B7}=3.1\pm0.1$ |
| Solid angle in 0.85 peak contour, degraded VLA vs ALMA | 0.09 vs 0.23 | not stated | arcsec^2 | 3 | 0.09 arcsec$^2$, while it is 0.23 arcsec$^2$ in the ALMA map |
| Dust mass inside vortex boundary (model) | ~45 | not stated | Earth masses | 4 | the inferred dust mass inside the vortex boundary is $\sim45$ $M_{\ensuremath{\oplus}}$ |

## Qualitative findings

- VLA Ka northern clump is more compact than ALMA emission at same location, consistent with dust trapping; ALMA decrement matches SPHERE shadowed region  
  > "The compactness of the Ka emission is expected in the context of dust trapping, as big grains are trapped more easily than smaller grains in gas pressure maxima." (abstract)

## Claim tuples

- H: Large grains are more concentrated than mm grains in the NW clump | E: Compare VLA Ka and ALMA B7 at matched resolution | R: Solid angle 0.09 vs 0.23 arcsec^2 | F: Consistent with dust trapping | **supported**
- H: A steady-state vortex model reproduces the ALMA asymmetry | E: RADMC-3D vortex model | R: Required artificially extended vortex (r_s=3); second vortex needed for southern extension | F: Single standard vortex insufficient | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Temperature asymmetry from shadowing, or an accreting companion, as alternative to dust trapping  
  > "The compact emission in the VLA Ka data could also be explained by a companion object, e.g. a forming planet accreting material." (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA data lack resolution to resolve the disk like the VLA  
  > "However, in the ALMA maps the disk is not as resolved as in the VLA data." (5 Conclusions)
- Caveat (inferred, ours): Only one ALMA execution set with 12 min; low resolution
- Caveat (inferred, ours): Model fitted by eye, no formal fit or uncertainties
- Caveat (inferred, ours): Vortex extended artificially
- Caveat (inferred, ours): VLA clump detected at modest S/N

## Reproducibility

- Data public (paper): ALMA archival; SPHERE publicly available  
  > "we made use of ALMA archival data in Band 7" (2.2 ALMA)
- Products in archive: _not stated_
- Missing: uvmem code and settings
- Missing: ALMA calibration details
- Missing: full model parameter set
- Data volume (inferred): ~5-10 GB for ALMA; VLA data additional
- Score (inferred): 3/5, Public ALMA data, but the custom MEM code and manual model tuning limit exact reproduction.
- Rediscovery candidate: no, Depends on uvmem and VLA data; model matching was done by eye.

## Links

- Method: Lyra & Lin 2013 (cite: Lyra2013) (vortex steady-state solution)
- Companion: Chapillon 2015 (cite: Chapillon2015) (original ALMA observations)
- Companion: Isella 2010 (cite: Isella2010) (earlier mm observations)
- Related: VLA 13B-273

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 71,
  "stated": 43,
  "rate": 0.606
 },
 "evidence_ok": true
}
```
