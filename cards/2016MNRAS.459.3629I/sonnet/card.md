# ALMA observations of the submillimetre hydrogen recombination line from the type 2 active nucleus of NGC 1068

`2016MNRAS.459.3629I` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Izumi, Takuma | arXiv: 1602.07316 | DOI: 10.1093/mnras/stw324

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Can the broad (BLR) and narrow H26alpha submm recombination line be detected toward the type 2 AGN of NGC 1068 with ALMA, and what BLR clouds could emit it?  
  > "It is therefore the time to test the detectability of submm-RLs of the BLR-origin with the actual ALMA data." (Introduction)
- Target **NGC 1068**: coordinates RA 02h42m40.710s, Dec -00d00m47.938s (J2000), 6 cm position  
  > "towards the centre of NGC 1068 ($D$ = 14.4 Mpc; (cite: 1988ngc..book.....T))" (Introduction); "the location of the AGN is set to ($\alpha_{\rm J2000.0}$, $\delta_{\rm J2000.0}$ = 02$^{\rm h}$42$^{\rm m}$40$s$710, $-$00$^\circ$00$'$47$\ensuremath{''}$938)" (Data analysis); z/distance D = 14.4 Mpc; Vsys = 1137 km/s  
  > "towards the centre of NGC 1068 ($D$ = 14.4 Mpc; (cite: 1988ngc..book.....T))" (Introduction); "the location of the AGN is set to ($\alpha_{\rm J2000.0}$, $\delta_{\rm J2000.0}$ = 02$^{\rm h}$42$^{\rm m}$40$s$710, $-$00$^\circ$00$'$47$\ensuremath{''}$938)" (Data analysis); distance from Tully 1988 (cite: 1988ngc..book.....T)  
  > "towards the centre of NGC 1068 ($D$ = 14.4 Mpc; (cite: 1988ngc..book.....T))" (Introduction); "the location of the AGN is set to ($\alpha_{\rm J2000.0}$, $\delta_{\rm J2000.0}$ = 02$^{\rm h}$42$^{\rm m}$40$s$710, $-$00$^\circ$00$'$47$\ensuremath{''}$938)" (Data analysis)

## Data provenance

- ALMA projects: 2013.1.00188.S
- bands: _not stated_
- frequencies and spectral setup: 4 spws of 1.875 GHz each (Spw 0,1 USB; Spw 2,3 LSB), ~7.5 GHz total; LSB covers red side of H26alpha, USB HNC(4-3)  
  > "Each of four spectral windows (Spw 0, 1 = USB and Spw 2, 3 = LSB) has a bandwidth of 1.875 GHz, which yields $\sim$ 7.5 GHz width in total." (Data analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21.4 to 783.5 m (25.0 to 914.2 klambda at 350 GHz)  
  > "The baseline length spans from 21.4 to 783.5 m, which corresponds to the $uv$ range of 25.0 to 914.2 k$\lambda$ at 350 GHz." (Data analysis)
- angular resolution: 0.37 x 0.31 arcsec (26 x 22 pc)  
  > "$\theta_{\rm maj}$ $\times$ $\theta_{\rm min}$ = 0.37 arcsec $\times$ 0.31 arcsec" (Data analysis)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma = 0.42 mJy/beam at 50 km/s (LSB); 0.19 mJy/beam (USB continuum)  
  > "The 1$\sigma$ sensitivity is 0.42 mJy beam$^{-1}$ at d$V$ = 50 km s$^{-1}$ for the LSB" (Data analysis)
- time on source: ~35 min  
  > "The total on-source time was $\sim$ 35 min." (Data analysis)
- observing dates: 2015 June 15  
  > "We observed NGC 1068 with ALMA on 2015 June 15 with 37 antennas" (Data analysis)
- pi or archival as stated: Cycle 2 science program, PI M. Imanishi  
  > "as a Cycle 2 science program (ID = 2013.1.00188.S, PI: M. Imanishi)" (Data analysis)
- Line: H26alpha H i recombination line (353.62 GHz)
- Line: HNC J=4-3 (362.63 GHz)
- External data: Recombination-line departure coefficients and optical depth parameter Omega for H26alpha (Case-B model)  
  > "we adopted the model-calculated parameters of H i RLs under the Case-B condition by (cite: 1995MNRAS.272...41S) as our best estimate at first." (Discussion) [from (cite: 1995MNRAS.272...41S)]
- External data: Inner dust radius of NGC 7469 ~100 light-days from reverberation mapping  
  > "the reverberation mapping by (cite: 2014ApJ...788..159K) revealed that $r_{\rm in}$ of NGC 7469 is $\sim$ 100 light-days" (Discussion) [from (cite: 2014ApJ...788..159K)]
- External data: Areal covering factor f_a ~0.1 of BLRs  
  > "simple speculation on the equivalent width of Ly$\alpha$ yields $f_a$ $\sim$ 0.1 ((cite: 1997iagn.book.....P)) in BLRs" (Discussion) [from (cite: 1997iagn.book.....P)]

## Processing

### Calibration

- pipeline or manual: Standard manner reduction in CASA; calibrators J0224+0659 (bandpass), J0239+0416 (phase), Ceres (flux)  
  > "The bandpass, phase, and flux were calibrated with J0224+0659, J0239+0416, and Ceres, respectively." (Data analysis)
- casa version: CASA 4.3.0  
  > "conducted with `CASA` version 4.3.0 ((cite: 2007ASPC..376..127M)) in standard manners" (Data analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres  
  > "The bandpass, phase, and flux were calibrated with J0224+0659, J0239+0416, and Ceres, respectively." (Data analysis)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "All images were reconstructed by the `CASA` task `CLEAN`." (Data analysis)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: None for LSB; continuum level estimated from USB  
  > "Therefore, we show the spectrum of the LSB without continuum subtraction in this work." (Data analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 120 channels binned from 0.42 km/s to ~50 km/s  
  > "120 channels were binned to improve the signal-to-noise ratio, which resulted in the final velocity resolution of d$V$ $\sim$ 50 km s$^{-1}$" (Data analysis)
- final beam: 0.37 x 0.31 arcsec  
  > "$\theta_{\rm maj}$ $\times$ $\theta_{\rm min}$ = 0.37 arcsec $\times$ 0.31 arcsec" (Data analysis)
- final rms: 0.42 mJy/beam (LSB, 50 km/s); 0.19 mJy/beam (USB continuum)  
  > "whereas 1$\sigma$ = 0.19 mJy beam$^{-1}$ for the USB continuum emission" (Data analysis)

### Inherited from earlier work

- AGN position defined from high-resolution 6 cm interferometry  
  > "which is defined by high-resolution interferometric observations at 6 cm (e.g., (cite: 2004ApJ...613..794G))" (Data analysis) [from (cite: 2004ApJ...613..794G)]
- Component slopes for continuum extrapolation (3.5, -0.15, -1.0) taken as typical  
  > "Assuming typical slopes ($\alpha$) of the flux scaling ($flux$ $\propto$ $\nu^\alpha$) that are 3.5, $-$0.15, $-$1.0 for the above three components, respectively (e.g., (cite: 2011piim.book.....D))" (Results) [from (cite: 2011piim.book.....D)]

### Not stated but needed to reproduce (our reading)

- Robust/weighting, cell and image size, clean threshold and masks for CLEAN
- Whether pipeline or manual calibration was used
- Aperture size for spectrum extraction at AGN position
- Channel range of USB continuum and how line-free channels were chosen
- Details of the extension of Case-B model to Ne > 1e8
- Flux calibration uncertainty

## Analysis recipe

1. **Reduce and image data**: Standard CASA calibration and CLEAN imaging; LSB binned to 50 km/s  
  > "The reduction, calibration, and subsequent analysis were conducted with `CASA` version 4.3.0 ((cite: 2007ASPC..376..127M)) in standard manners." (Data analysis)
   - software: CASA
   - parameter: dV ~ 50 km/s  
  > "resulted in the final velocity resolution of d$V$ $\sim$ 50 km s$^{-1}$" (Data analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate LSB continuum level from USB**: Decompose USB continuum into dust 50%, free-free 25%, synchrotron 25% and scale with spectral indices 3.5, -0.15, -1.0  
  > "we estimate the LSB continuum level to be 11.26 mJy beam$^{-1}$." (Results)
   - assumption: Component fractions and spectral indices as above  
  > "thermal dust emission from both the dusty torus and the extended cold dust (50 per cent contribution to the total USB emission)" (Results)
   - fitting: _not stated_
   - validation: Varying free-free to synchrotron ratio changes estimate only slightly  
  > "Note that varying the free$-$free to synchrotron ratio only slightly modify this estimation" (Results)
3. **Search LSB spectrum for H26alpha and set upper limit**: Extract spectrum at AGN position with single aperture; compare excess to 3 sigma  
  > "this excess in each channel is still below the 3$\sigma$ limit of our observations (1.26 mJy beam$^{-1}$)" (Results)
   - software: CASA
   - assumption: Integrated limit assumes Gaussian profile with FWHM 3000 km/s  
  > "The integrated intensity was calculated by assuming the Gaussian profile with the FWHM of 3000 km s$^{-1}$" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model BLR cloud line and continuum optical depth and expected flux**: LTE line and free-free optical depths for Ne=1e9, Te=1e4 K, L=20 Rsun; line-to-continuum ratio; scale to NGC 1068 with covering factor and r_in  
  > "we obtain an optical depth of H26$\alpha$ as $\tau_{\rm H26\alpha}$ $\sim$ 3.4" (Discussion)
   - parameter: Ne=Np=1e9 cm^-3, Te=1e4 K, L=4.5e-7 pc, f_a~0.1, r_in~0.13 pc  
  > "$N_e$ = $N_p$ = 10$^9$ cm$^{-3}$, $T_e$ = 10$^4$ K, and $L$ = 20 r$_\odot$ = 4.5 $\times$ 10$^{-7}$ pc" (Discussion)
   - assumption: LTE, uniform density and temperature clouds, stimulated emission by non-thermal background neglected  
  > "A potential contamination due to stimulated emission caused by the background non-thermal radiation is neglected for simplicity." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.0: Reduction, calibration, CLEAN imaging and analysis  
  > "The reduction, calibration, and subsequent analysis were conducted with `CASA` version 4.3.0" (Data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| USB continuum peak (364 GHz) | 11.72 | not stated | mJy/beam | 1 | peaks at the precise AGN position (11.72 mJy beam$^{-1}$) |
| Estimated LSB continuum level | 11.26 | 0.19 | mJy/beam | 2 | Continuum (USB) / 363.98 / 11.26$\pm$0.19 |
| H26alpha 3 sigma peak upper limit | <1.26 | not stated | mJy/beam | 3 | H26$\alpha$ (red side) / 353.62 / $<$1.26 |
| H26alpha integrated intensity upper limit | <4.02 | not stated | Jy/beam km/s | 3 | $<$4.02 |
| H26alpha line optical depth (Ne=1e9) | ~3.4 | not stated | dimensionless | 4 | $\tau_{\rm H26\alpha}$ $\sim$ 3.4, i.e., the line emission is (moderately) optically thick in this case. |
| Free-free optical depth at 350 GHz | ~0.65 | not stated | dimensionless | 4 | we obtain $\tau_{\rm ff}$ $\sim$ 0.65 at 350 GHz for the BLR emission |
| Expected total BLR H26alpha flux | ~0.011 | not stated | Jy km/s | 4 | $$\begin{equation}
   S_{\rm H26\alpha,cl} \times \frac{f_a \pi r^2_{\rm in}}{\pi (10 {\rm r}_\odot)^2} \sim 0.011 ~\rm{Jy~km~s^{-1}}, 
    \label{eq7}
\end{equation}$$ |
| NLR volume-filling factor upper limit | <5e-3 | not stated | dimensionless | 4 | that factor is estimated to be $<$ 5 $\times$ 10$^{-3}$ |

## Qualitative findings

- BLR clouds with Ne~1e9 cm^-3 dominate broad submm-RL flux; other densities are too optically thick or thin  
  > "BLR clouds with $N_e$ $\sim$ 10$^9$ cm$^{-3}$ would be the dominant contributor to the H$n\alpha$ flux." (Discussion)

## Claim tuples

- H: Is broad or narrow H26alpha detectable toward NGC 1068 with ALMA? | E: Cycle 2 Band 7 spectrum at AGN position with estimated continuum | R: Excess below 3 sigma of 1.26 mJy/beam | F: Non-detection, not conclusive given continuum uncertainty | **supported**
- H: Which BLR clouds can emit submm-RLs and can they be detected? | E: LTE optical depth and line-to-continuum calculations | R: Expected flux ~0.011 Jy/km/s, peak a few to 10 microJy | F: Detection impractical even with ALMA | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Submm-RLs avoid dust extinction and maser amplification, enabling BLR probes of obscured AGN  
  > "we considered that submillimetre H i RLs (submm-RLs, hereafter) would provide a way as they do not suffer from dust extinction." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): LSB covers only part of the broad line, so continuum level is highly uncertain  
  > "Continuum subtraction can be problematic in the LSB because all channels would contain the BLR component due to the limited band width." (Data analysis)
- Caveat (inferred, ours): Continuum level assumption (50/25/25 split) drives the marginal excess
- Caveat (inferred, ours): Single uniform-cloud model with no uncertainties
- Caveat (inferred, ours): Non-detection result cannot constrain much

## Reproducibility

- Data public (paper): Data from ALMA project 2013.1.00188.S acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00188.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: Aperture for spectrum
- Missing: Exact model grids extended beyond Ne=1e8
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Single dataset and simple analysis, but imaging parameters and aperture are missing.
- Rediscovery candidate: no, Main result is a non-detection with an assumed continuum; imaging details are missing.

## Links

- Method: (cite: 1995MNRAS.272...41S) (Case-B H i recombination line model parameters)
- Companion: (cite: 2013ApJ...767..xxx Scoville & Murchikova 2013) (Predicted detectable submm-RL and free-free from NLRs)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 68,
  "stated": 39,
  "rate": 0.574
 },
 "evidence_ok": true
}
```
