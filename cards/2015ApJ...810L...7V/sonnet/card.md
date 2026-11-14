# A Concentration of Centimeter-sized Grains in the Ophiuchus IRS 48 Dust Trap

`2015ApJ...810L...7V` | The Astrophysical Journal Letters 2015 | first author: van der Marel, N. | arXiv: 1508.01003 | DOI: 10.1088/2041-8205/810/1/L7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Are centimeter-sized grains more azimuthally concentrated than millimeter-sized grains in the Oph IRS 48 dust trap, as predicted by dust trapping?  
  > "The distributions of dust emission at 450 $\mu$m and 0.9 cm are compared and we aim to provide confirmation of the dust trap scenario in a transitional disk." (Introduction)
- Target **Oph IRS 48**: coordinates 16h27m37.185s -24d30m35.39s  
  > "The stellar position was set to 16$^h$27$^m$37$^s$.185 -24$^{\circ}$30’35$\ensuremath{''}$39, taken from a Keplerian model fit to the CO isotopologue data" (Results); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00100.S
- bands: ALMA Band 9 (680 GHz); VLA Ka band (34 GHz)  
  > "VLA) Ka band (34 GHz or 0.9 cm) and ALMA Cycle 2 Band 9 (680 GHz or 0.45 mm)" (abstract)
- frequencies and spectral setup: ALMA: four spectral windows of 1920 channels, centered 661, 659, 675 (937.5 MHz each) and 672 GHz (1875 MHz)  
  > "three windows have a bandwidth of 937.5 MHz, centered on 661, 659 and 675 GHz, the fourth spectral window was centered on 672 GHz with a bandwidth of 1875 MHz." (Observations)
- continuum bandwidth: ALMA ~4.7 GHz; VLA 8 GHz  
  > "The total continuum bandwidth was $\sim$4.7 GHz." (Observations)
- arrays: _not stated_
- configurations: ALMA C34-3; VLA CnB and B  
  > "using the VLA in the CnB and B configurations in January-February 2015" (Observations)
- baselines: VLA 75 to 8700 m  
  > "with baselines ranging from 75 to 8700 m" (Observations)
- angular resolution: ALMA 0.19x0.15 arcsec; VLA 0.46x0.26 arcsec  
  > "| ALMA | 680 | 4.7 | 0$\ensuremath{''}$19$\times$0$\ensuremath{''}$15 | 79$^{\circ}$ | 1000 | 190 | 0.6 |" (Table 1)
- max recoverable scale: 5 arcsec for VLA CnB  
  > "the largest angular scales recovered by the CnB observation is 5"" (Results)
- sensitivity: rms 0.6 mJy/beam (ALMA); 3.5 uJy/beam (VLA)  
  > "| VLA | 34 | 8.0 | 0$\ensuremath{''}$46$\times$0$\ensuremath{''}$26 | 21$^{\circ}$ | 251$\times10^{-3}$ | 138$\times10^{-3}$ | 3.5$\times10^{-3}$ |" (Table 1)
- time on source: ALMA 52 min; VLA 1.25 h per block x3  
  > "The total on-source integration time was 52 minutes." (Observations)
- observing dates: ALMA July 2014; VLA Jan-Feb 2015  
  > "obtained using ALMA in Cycle 2 in July 2014 in the C34-3 configuration" (Observations)
- pi or archival as stated: _not stated_
- Other facility **VLA**: 34 GHz continuum, program 14B-115  
  > "as part of program 14B-115" (Observations)
- External data: SMA 230 GHz and 345 GHz disk-integrated fluxes (50 and 160 mJy)  
  > "The fluxes are 50$\pm$7.5, 160$\pm$24 and 1000$\pm$200 mJy respectively, taken from (cite: Brown2012b) and this work" (Discussion and summary) [from (cite: Brown2012b)]
- External data: Physical disk model dust temperature 60 K at 60 AU  
  > "calculated physical dust temperature of 60 K (at 60 AU radius in a physical disk model, (cite: Bruderer2014))" (Discussion and summary) [from (cite: Bruderer2014)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA J1517-243; VLA 3C286  
  > "The flux was calibrated using J1517-243, the bandpass with J1427-4206 and the phase with J1626-2951." (Observations)
- flux scale uncertainty: ALMA 20%; VLA 10%  
  > "The flux calibration uncertainty is 20%." (Observations)
- self calibration: ALMA data self-calibrated  
  > "The data were self-calibrated and imaged using Briggs weighting with a robust parameter of 0.5." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5 (both)  
  > "imaged using Briggs weighting with a robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: ALMA data restored with VLA beam/convolved to VLA synthesized beam for comparison  
  > "the ALMA data were convolved with the same synthesized beam as the VLA observations" (Discussion and summary)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Fourth-power Gaussian intensity model  
  > "fit to a two-dimensional fourth power Gaussian intensity profile $I(r,\phi)$ (cite: vanderMarel2013)" (Results) [from (cite: vanderMarel2013)]
- Stellar position from Keplerian fit to CO isotopologue data  
  > "taken from a Keplerian model fit to the CO isotopologue data from the same ALMA data set (van der Marel et al. submitted)" (Results) [from van der Marel et al. submitted]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration pipeline/manual details
- Self-calibration solution intervals and reference
- Image size and cell size, clean masks, number of iterations
- Channels used for continuum
- Gaussian fit grid ranges
- How spectral index errors and beta were computed in detail
- Distance adopted

## Analysis recipe

1. **Image continuum**: Briggs-weighted imaging of ALMA and VLA; ALMA also restored with VLA beam  
  > "The calibrated data were concatenated and imaged using Briggs weighting with a robust parameter of 0.5." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Simulated VLA observation of ALMA image; compared flux with earlier DnC data  
  > "we have simulated the ALMA image as if observed by the VLA by sampling the ALMA image on the VLA visibilities" (Results)
2. **Fit azimuthal/radial intensity model**: Fourth-power Gaussian model fit in uv-plane at both frequencies  
  > "The fitting is performed in the $uv$-plane, with the model visibilities sampled onto the observed spatial frequencies." (Results)
   - parameter: Grid steps 1 degree and 1 AU  
  > "we use $\chi^2$ minimization over a grid of $\phi_c,\phi_w,r_c$ and $r_w$ with steps of 1$^{\circ}$ and 1 AU" (Results)
   - fitting: chi^2 grid minimization; errors from rescaling reduced chi^2 to 1  
  > "The errors are estimated by rescaling the reduced $\chi^2$ to 1." (Results)
   - validation: Residuals inspected; 85% of structure recovered  
  > "as still more than 85% of the structure is recovered by the Gaussian intensity equation" (Results)
3. **Estimate optical depth at 680 GHz**: Planck equation with isothermal beam-filling emission at 60 K  
  > "we assume that the peak millimeter emission originates from an isothermal area $\Omega_{\rm beam}$ (sr) of the beam size with $T_{\rm dust}$=60 K." (Discussion and summary)
   - assumption: T_dust = 60 K  
  > "with $T_{\rm dust}$=60 K" (Discussion and summary)
   - fitting: _not stated_
   - validation: _not stated_
4. **Spectral index and beta maps**: Spectral index from beam-matched ALMA and VLA images and integrated fluxes; beta from tau at both frequencies  
  > "$\beta$ can be calculated as a function of position by calculating $\tau_{\nu}$ at both frequencies at different positions, assuming $T_{\rm dust}$=60 K" (Discussion and summary)
   - assumption: T_dust 60 K uniform; 200 K and 24 K tested  
  > "for $T_{\rm dust}$=200 K in the center, $\beta=0.6\pm0.1$" (Discussion and summary)
   - fitting: _not stated_
   - validation: Alpha error from SNR  
  > "The error in spectral index across the image is calculated based on the signal-to-noise ratio" (Discussion and summary)

## Software

- **CASA** : imfit to check VLA source is marginally resolved  
  > "Deconvolution using CASA imfit reveals that the source is marginally resolved." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring radius r_c | 61 | 2 | AU | 2 | $r_c$=61($\pm$ 2) AU, $r_w$=14($\pm$2) AU |
| Azimuthal width phi_w 680 GHz | 41 | 4 | degrees | 2 | $\phi_w$=41($\pm$4)$^{\circ}$ for the 680 GHz |
| Azimuthal width phi_w 34 GHz | 18 | 7 | degrees | 2 | $\phi_w$=18($\pm$7)$^{\circ}$ for the 34 GHz continuum |
| Width ratio mm/cm | 2.3 | 0.9 | dimensionless | 2 | azimuthal width of the centimeter emission is 2.3($\pm$0.9) times narrower than the millimeter emission |
| tau at 680 GHz | 0.5 | not stated | dimensionless | 3 | For the peak flux of 189 mJy, $\tau_{680GHz}$=0.5 |
| Integrated spectral slope 34-680 GHz | 2.84 | 0.06 | dimensionless | 4 | gives a spectral slope of $\alpha = 2.84 \pm 0.06 |
| Spectral index center to wings | 2.6 to 3.3 | 0.08 / 0.15 | dimensionless | 4 | $\alpha$ increases from 2.6$\pm$0.08 in the center to 3.3$\pm$0.15 in the outer wings |
| Stellar point source flux at 34 GHz | 36 | 10 sigma detection | uJy/beam | 1 | a peak flux of 36 $\mu$Jy beam$^{-1}$ (10$\sigma$) |
| beta center / outer (60 K) | 0.7 / 1.3 | 0.1 / 0.3 | dimensionless | 4 | We find $\beta\sim0.7\pm0.1$ in the center and $\beta\sim1.3\pm0.3$ in the outer parts |

## Qualitative findings

- 34 GHz emission is more azimuthally concentrated than 680 GHz and not a filtering effect; 34 GHz also shows a point source at the star, likely ionized gas.  
  > "The 34 GHz continuum emission peaks at the same location, but is much more azimuthally concentrated." (Results)

## Claim tuples

- H: Larger grains are more azimuthally concentrated than smaller ones in the IRS 48 trap | E: Fit intensity model to ALMA 680 GHz and VLA 34 GHz images | R: Azimuthal width ratio 2.3±0.9 | F: Supports dust trapping of cm-sized grains, subject to optical depth and temperature assumptions | **partially**
- H: Spectral index varies across the trap | E: Beam-matched alpha map | R: alpha 2.6 in center to 3.3 in wings | F: Consistent with more large particles in center | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Spatial filtering and sensitivity effects ruled out; low temperature hiding narrow mm concentration considered unlikely.  
  > "Spatial filtering can be ruled out as an explanation for the different azimuthal extents" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Optical depth at 680 GHz cannot be measured independently of temperature.  
  > "The optical depth $\tau_{680GHz}$ cannot be measured independently from the temperature with the available data." (Discussion and summary)
- Caveat (inferred, ours): Intensity model leaves 15% residual flux
- Caveat (inferred, ours): Beam mismatch between VLA and ALMA
- Caveat (inferred, ours): Only one VLA width with large uncertainty (±7 deg)
- Caveat (inferred, ours): Uniform temperature assumption

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: VLA data calibration details
- Missing: Fit code not released
- Data volume (inferred): ALMA Band 9 single track ~ tens of GB; VLA 3 blocks ~ 100+ GB
- Score (inferred): 3/5, Data identified, fit method clear, but processing parameters and VLA project access are sparse.
- Rediscovery candidate: no, Needs VLA data and unspecified processing details.

## Links

- Method: (cite: vanderMarel2013) (Intensity model and earlier Band 9 data)
- Companion: van der Marel et al. submitted (CO isotopologue data and stellar position)

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 37,
  "rate": 0.552
 },
 "evidence_ok": true
}
```
