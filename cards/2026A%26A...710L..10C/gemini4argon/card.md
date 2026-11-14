# Hourly radio variability of PDS 70c from time-differential photometry

`2026A&A...710L..10C` | Astronomy and Astrophysics 2026 | first author: Casassus, Simon | arXiv: 2604.24991 | DOI: 10.1051/0004-6361/202659553

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Whether the ALMA Band 7 (~343 GHz) continuum emission from the accreting protoplanet PDS 70c is time-variable on hourly to daily timescales, and what variability constrains about the radio emission mechanism.  
  > "The radio emission mechanisms from accreting protoplanets, and their variability, link observations and physical properties. We revisit the variability of the $\sim$343\,GHz (ALMA Band 7) flux density from PDS\,70c ($F_{\rm B7}$)." (abstract); "We then discuss the expected timescales of the radio variability of PDS\,70c for relevant emission mechanisms (Sect.\,3)." (Introduction)
- Target **PDS 70**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **PDS 70c**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (~343 GHz)  
  > "We revisit the variability of the $\sim$343\,GHz (ALMA Band 7) flux density from PDS\,70c ($F_{\rm B7}$)." (abstract)
- frequencies and spectral setup: 3 continuum spectral windows time-averaged to 6.06 s and binned into 8 channels (IB17)  
  > "In brief, the 3 continuum spectral windows were time-averaged to 6.06\,s, and binned into 8 channels." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~50 to ~60 mas; naturally-weighted beam 0.09'' x 0.08'' (IB17); restored beams 64x41, 63x50, 64x58, 62x46 mas (IB17)  
  > "| IB17$^{a}$ | $\sim$60 | $106\pm19$$^{a}$ | 2017 |" (Table 1); "| LB19$^{b}$ | $\sim$50 | $118\pm24$$^{c}$ | 2019 |" (Table 1); "naturally-weighted beam of $0.09\ensuremath{''}\times 0.08\ensuremath{''}$." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
- max recoverable scale: _not stated_
- sensitivity: IB17 noise: 44 uJy (2 Dec), 51 uJy (3 Dec), 65 uJy (6 Dec), 30 uJy (All)  
  > "| 2/12/2017 | $64 \times 41$ | 44 | $147\pm44$ |" (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "| All | $62 \times 46$ | 30 | $172\pm30$ |" (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
- time on source: IB17: three ~1 h EBs; LB19: three EBs each ~1h15m long; IB23: EBs with integrations of over 2 h  
  > "In images of the 2017 ALMA dataset, with three $\sim$1\,h EBs, PDS\,70c was detected only on 6 December 2017" (abstract); "The deep IB23 dataset spanned six\,months in nine EBs with integrations of over 2\,h, while the IB17 EBs are 1\,h long." (Time-differential photometry); "We applied differential photometry to the LB19 Band\,7 dataset (cite: Benisty2021ApJ...916L...2B), which was acquired in 3 EBs, two from 27/7/2019, and one from 30/7/2019, and each $\sim$\,1h15m long." (Application to deep Band 7 data)
- observing dates: IB17: 2, 3, and 6 December 2017; LB19: 27/7/2019 and 30/7/2019; IB23: 2023 (spanning six months, including 2/6/2023)  
  > "It turns out that IB17 is composed of three EBs, dated 2, 3, and 6 December." (Introduction); "We applied differential photometry to the LB19 Band\,7 dataset (cite: Benisty2021ApJ...916L...2B), which was acquired in 3 EBs, two from 27/7/2019, and one from 30/7/2019, and each $\sim$\,1h15m long." (Application to deep Band 7 data); "The reference EB was chosen as 2/6/2023, as it was acquired under the best conditions." (Application to deep Band 7 data)
- pi or archival as stated: _not stated_
- External data: Previous Band 7 flux density measurement for IB17: 106 +/- 19 uJy  
  > "| IB17$^{a}$ | $\sim$60 | $106\pm19$$^{a}$ | 2017 |" (Table 1) [from Isella2019ApJ...879L..25I; Benisty2021ApJ...916L...2B]
- External data: Previous Band 7 flux density measurement for LB19: 118 +/- 24 uJy  
  > "| LB19$^{b}$ | $\sim$50 | $118\pm24$$^{c}$ | 2019 |" (Table 1) [from Benisty2021ApJ...916L...2B]
- External data: Previous Band 7 flux density measurement for IB23: 121 +/- 13 uJy  
  > "| IB23$^{d}$ | $\sim$60 | $121\pm13$$^{d}$ | 2023 |" (Table 1) [from Dominguez2025AA...702A..18D]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% rms nominal calibration uncertainty in ALMA Band 7  
  > "An offset in flux scale of $\sim$20% is consistent with the nominal calibration uncertainty in ALMA Band\,7, of $\sim10\%$ rms" (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
- self calibration: Automatic self-calibration with snow package: single iteration in amplitude and phase with solution interval limited to a single scan (~50 s), improving peak S/N from 55 to 115  
  > "Following alignment, we concatenated the data into a single measurement set, and applied the `snow` package for automatic self calibration (cite: Carcamo2018A&C....22...16C)." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "However, a single iteration in amplitude and phase self-calibration, with a solution interval limited to a single scan (roughly 50\,s), improved the peak S/N from 55 to 115." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)

### Imaging

- task: gpu-uvmem  
  > "Once self-calibrated, each EB was split for separate imaging with ` gpu-uvmem`, in pure-$\chi^2$ reconstructions (i.e. without entropy regularization, but truncating the optimization at 10 iterations)." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
- deconvolver: pure-chi^2 reconstructions without entropy regularization, truncated at 10 iterations  
  > "Once self-calibrated, each EB was split for separate imaging with ` gpu-uvmem`, in pure-$\chi^2$ reconstructions (i.e. without entropy regularization, but truncating the optimization at 10 iterations)." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
- weighting robust: Briggs weights with robustness parameter r = 0.3 for restored model images; natural weights used in uv-plane residual analysis  
  > "The (non-parametric) model images were restored using Briggs weights with a robustness parameter $r=0.3$." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "We can compute the gridded visibilities, in natural weights, for both the concatenated dataset, $\tilde{V}_{\rm conc}$, with weights $W_{\rm conc}$, and in each individual EB, $\tilde{V}_{\rm EB}$, with weights $W_{\rm EB}$." (Gridded $uv$-plane time-differential photometry)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied in uv-plane point-source photometry via primary-beam attenuation factor A(x_0)  
  > "where $\vec{u}_{l}$ is the $uv$-plane position for datum $V^R_{l}$ and $\mathcal{A}(\vec{x_\circ})$ is the primary-beam attenuation." (Time-differential photometry)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: IB17 (r=0.3): 64 x 41 mas (2/12/2017), 63 x 50 mas (3/12/2017), 64 x 58 mas (6/12/2017), 62 x 46 mas (All); naturally-weighted beam: 0.09'' x 0.08''  
  > "| 2/12/2017 | $64 \times 41$ | 44 | $147\pm44$ |" (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "| All | $62 \times 46$ | 30 | $172\pm30$ |" (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "naturally-weighted beam of $0.09\ensuremath{''}\times 0.08\ensuremath{''}$." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
- final rms: IB17 (r=0.3): 44 uJy (2/12/2017), 51 uJy (3/12/2017), 65 uJy (6/12/2017), 30 uJy (All)  
  > "| 2/12/2017 | $64 \times 41$ | 44 | $147\pm44$ |" (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "| 6/12/2017 | $64 \times 58$ | 65 | $370\pm65$ |" (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "| All | $62 \times 46$ | 30 | $172\pm30$ |" (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)

### Inherited from earlier work

- Description of the IB17 ALMA dataset, alignment of EBs and imaging  
  > "Description of the IB17 ALMA dataset, alignment of EBs and imaging follow from (cite: CasassusCarcamo2022MNRAS.513.5790C), (cite: Casassus2023MNRAS.526.1545C), and references therein." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset) [from CasassusCarcamo2022MNRAS.513.5790C; Casassus2023MNRAS.526.1545C]
- Least-squares minimisation formula for point-source photometry in visibility residuals  
  > "Least-squares minimisation yields (cite: CasassusCarcamo2022MNRAS.513.5790C):" (Time-differential photometry) [from CasassusCarcamo2022MNRAS.513.5790C]
- Gridded visibility subtraction scheme in visalign  
  > "In an extension of the scheme used in the `visalign` package (cite: CasassusCarcamo2022MNRAS.513.5790C), the residuals are" (Gridded $uv$-plane time-differential photometry) [from CasassusCarcamo2022MNRAS.513.5790C]

### Not stated but needed to reproduce (our reading)

- ALMA project codes for IB17, LB19, and IB23 datasets
- CASA version and initial calibration pipeline version
- Image pixel size (cell size) and image dimensions used in gpu-uvmem and gridded visibility analysis
- Exact coordinates of PDS 70c (x_0) derived from the 6 December Gaussian fit
- Parameters passed to CASA statwt task
- Why only 7 of the 9 EBs in IB23 were used in the differential photometry analysis

## Analysis recipe

1. **Time and channel averaging, multi-epoch visibility alignment, and self-calibration**: Time-average continuum spectral windows to 6.06 s and bin into 8 channels; align individual EBs (or 20 min sub-EBs for IB23) in position and flux scale to a reference EB using VisAlign; concatenate aligned EBs and apply automatic phase and amplitude self-calibration using snow; recalculate visibility weights from root-mean-square dispersion using CASA statwt.  
  > "In brief, the 3 continuum spectral windows were time-averaged to 6.06\,s, and binned into 8 channels. Individual EBs from 3 and 6 December 2017 were then aligned to the first EB, from 2 December, using the ` VisAlign` package" (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "Following alignment, we concatenated the data into a single measurement set, and applied the `snow` package for automatic self calibration (cite: Carcamo2018A&C....22...16C)." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "This can be overcome with the replacement of the original weights by the root-mean-square dispersion of each visibility datum, taken over all individual integrations, as performed with the `CASA` task `statwt`." (Time-differential photometry)
   - software: CASA, mstransform, VisAlign, snow, statwt
   - parameter: time averaging = 6.06 s, channel binning = 8 channels  
  > "In brief, the 3 continuum spectral windows were time-averaged to 6.06\,s, and binned into 8 channels." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
   - parameter: self-calibration solution interval = single scan (~50 s), 1 iteration of amplitude and phase  
  > "However, a single iteration in amplitude and phase self-calibration, with a solution interval limited to a single scan (roughly 50\,s), improved the peak S/N from 55 to 115." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
   - fitting: _not stated_
   - validation: Additional imaging run after statwt to check dynamic range did not deteriorate; visual inspection of single-EB residual dirty maps to verify close-to-thermal residuals.  
  > "An additional imaging run is in order after the application `statwt`, to check that it did not appreciably deteriorate dynamic range." (Time-differential photometry); "The application of both EB alignment (with `VisAlign`), along with amplitude and phase self-calibration, allowed reaching close to thermal residuals in the 2017 dataset, as illustrated in Fig.\,3." (Residual maps on single EBs and impact of alignment and self-calibration)
2. **Image-plane reconstruction and photometry of individual EBs and concatenated IB17 dataset**: Split self-calibrated measurement set into individual EBs and reconstruct non-parametric model images with gpu-uvmem in pure-chi^2 mode, restore with Briggs r=0.3 weights, and measure PDS 70c flux density via forced peak intensity, beam fitting, and elliptical Gaussian fitting.  
  > "Once self-calibrated, each EB was split for separate imaging with ` gpu-uvmem`, in pure-$\chi^2$ reconstructions (i.e. without entropy regularization, but truncating the optimization at 10 iterations)." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "The (non-parametric) model images were restored using Briggs weights with a robustness parameter $r=0.3$." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "Since the source is known to exist, rather than assigning zero flux density we reported, in Table\,[\[table:IB17\]](#table:IB17), the specific intensity at the expected position." (Individual EB imaging of IB17)
   - software: gpu-uvmem
   - parameter: 10 iterations truncation, no entropy regularization, Briggs robust r = 0.3  
  > "Once self-calibrated, each EB was split for separate imaging with ` gpu-uvmem`, in pure-$\chi^2$ reconstructions (i.e. without entropy regularization, but truncating the optimization at 10 iterations)." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset); "The (non-parametric) model images were restored using Briggs weights with a robustness parameter $r=0.3$." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
   - assumption: Known source position from 6 December elliptical Gaussian fit used for forced photometry on non-detection dates  
  > "Since the source is known to exist, rather than assigning zero flux density we reported, in Table\,[\[table:IB17\]](#table:IB17), the specific intensity at the expected position." (Individual EB imaging of IB17)
   - fitting: Peak intensity readout, beam fit (assuming unresolved source), and elliptical Gaussian fit  
  > "The elliptical Gaussian fits were carried out following two strategies: 1- by fitting a beam, assuming that the source is unresolved, and 2- by fitting an elliptical Gaussian." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
   - validation: Comparison of joint 3-EB flux density with original discovery measurement by Isella et al. (2019), finding consistency at 1.8 sigma.  
  > "$\langle F_{\rm B7} \rangle$ is consistent, at 1.8$\sigma$, with the value reported by (cite: Isella2019ApJ...879L..25I)." (Individual EB imaging of IB17)
3. **Time-differential point-source photometry in the uv-plane**: Subtract model visibilities of the concatenated dataset from each EB (or 20-min sub-EB), then fit a point source fixed at the position of PDS 70c in the visibility residuals via least-squares minimisation. Estimate uncertainties via visibility weights (post-statwt) and via spatial scatter at N=120 random positions along a projected circular orbit matching PDS 70c.  
  > "Our method is to fit a point source, fixed at the location of PDS\,70c ($\vec{x_\circ}$, obtained with an elliptical Gaussian fit to 6 December), in the visibility residuals $V^R$, after subtraction of the model visibilities calculated from the model image that best fits the concatenated dataset." (Time-differential photometry); "At a given epoch we applied Eq.\,[\[eq:PS\]](#eq:PS) at $N = 120$ random positions, and took the dispersion of the resulting $N$ flux densities as a measure of its uncertainty." (Time-differential photometry); "In an attempt to pick-up fine-grained variability, we split the seven EBs from IB23 in six equal intervals, each $\sim$20\,min long, and aligned the resulting “sub-EBs” using `VisAlign`." (Application to deep Band 7 data)
   - software: VisAlign
   - parameter: N = 120 random positions along projected circular orbit of PDS 70c (excluding within one natural-weight beam of PDS 70c)  
  > "At a given epoch we applied Eq.\,[\[eq:PS\]](#eq:PS) at $N = 120$ random positions, and took the dispersion of the resulting $N$ flux densities as a measure of its uncertainty." (Time-differential photometry); "Given that the source in consideration is approximately a simple ring, we chose to place the random positions along a projected circular orbit matching that of PDS\,70c (but excluding the position of PDS\,70c within one natural-weight beam)." (Time-differential photometry)
   - parameter: 20 min sub-EB intervals (6 equal intervals per EB for 7 EBs in IB23, 41 degrees of freedom)  
  > "In an attempt to pick-up fine-grained variability, we split the seven EBs from IB23 in six equal intervals, each $\sim$20\,min long, and aligned the resulting “sub-EBs” using `VisAlign`." (Application to deep Band 7 data); "The fine-grained measurements of $\Delta F_{\rm B7}$ shown in Fig.\,6 seem to be indicative of variability, as the reduced $\chi^2$ is 1.67 (with 41 degrees of freedom)." (Application to deep Band 7 data)
   - assumption: Flat spectral index across the band and fixed point-source position x_0  
  > "Both approaches yield similar results for a flat spectral index (Fig.\,3)." (Time-differential photometry)
   - fitting: Analytic least-squares minimisation for point-source flux density in visibility residuals; chi^2 test for constancy and quadratic noise addition to bring reduced chi^2 to unity for intrinsic scatter sigma_int with bootstrapped uncertainties  
  > "Least-squares minimisation yields (cite: CasassusCarcamo2022MNRAS.513.5790C):" (Time-differential photometry); "The intrinsic variability of PDS\,70c, $\sigma_{\rm int}$, can be estimated as an additional source of noise, added in quadrature to each measurement of $\Delta F_{\rm B7}(t)$, such that the reduced $\chi^2$ of the PDS\,70c time-series is brought down to unity." (Application to deep Band 7 data)
   - validation: Cross-check against gridded visibility subtraction dirty maps; injection of three synthetic constant control point-sources at symmetric positions relative to disk axes to test false variability.  
  > "As a test on the significance of the variability of PDS\,70c, we injected three synthetic and constant point-sources in the concatenated dataset, at symmetric positions from PDS\,70c relative to the disk minor and major axis." (Time-differential photometry); "The dirty images of the variable signal in each EB can be used as a consistency test between the photometry in the raw and gridded approaches." (Gridded $uv$-plane time-differential photometry)
4. **Analytical radiative diffusion timescale modeling of circumplanetary environment**: Calculate the Rosseland radiative diffusion timescale tau_d = M_env * kappa_R / (c * L) for a cubic box of side L containing environment mass M_env with Rosseland opacity kappa_R, and constrain M_env or L required to match hourly variability (tau_d = 1 h).  
  > "We distributed the mass in the planetary environment $M_{\rm env}$, in a cubic box with side $L$, representing the linear size of a CPD or of an envelope." (Discussion); "Then the diffusion timescale is $\tau_d = M_{\rm env} \,\kappa_R / (c \, L)$." (Discussion); "If $M_{\rm env} = 0.07 M_{\rm Jup}$, $L = 0.1$\,au, and $\kappa_R = 0.1\,$cm$^2$\,g$^{-1}$, then $\tau_d = 3.5\,{\rm d}$. Fixing $\tau_d = 1$\,h would require a box with side $L = \kappa_R \times M_{\rm env} / (c \times \tau_d) \sim 8$\,au" (Discussion)
   - parameter: L = 0.1 au, kappa_R = 0.1 cm^2 g^-1, M_env = 0.07 M_Jup  
  > "If $M_{\rm env} = 0.07 M_{\rm Jup}$, $L = 0.1$\,au, and $\kappa_R = 0.1\,$cm$^2$\,g$^{-1}$, then $\tau_d = 3.5\,{\rm d}$." (Discussion)
   - assumption: Optically thick medium with energy transfer via Rosseland diffusion in a cubic box of side L; gas-to-dust ratio of 100; planet-to-CPD mass ratio of 10^-2  
  > "Assuming energy transfer in an optically thick medium via Rosseland diffusion, the typical photon mean-free-path is $l_R = 1/ (\kappa_R \, \rho)$, where $\kappa_R$ is the Rosseland opacity and $\rho$ is the mass density." (Discussion); "An environment mass of $M_{\rm env} \sim 0.07 M_{\rm Jup}$, for a planet-to-CPD mass ratio of $10^{-2}$ (cite: Wang2021AJ....161..148W), is in practice an upper limit." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data handling, time and channel averaging via mstransform, and visibility weight recalculation via statwt  
  > "However, perhaps as a result of a bug in the handling of `CASA` tasks (which we attribute to intensive calls to the `mstransform` task, combining both time and channel averaging), the EB from 6 December was missing." (Introduction); "This can be overcome with the replacement of the original weights by the root-mean-square dispersion of each visibility datum, taken over all individual integrations, as performed with the `CASA` task `statwt`." (Time-differential photometry)
- **mstransform** : Time and channel averaging of measurement sets  
  > "However, perhaps as a result of a bug in the handling of `CASA` tasks (which we attribute to intensive calls to the `mstransform` task, combining both time and channel averaging), the EB from 6 December was missing." (Introduction)
- **statwt** : Replacing original visibility weights by the root-mean-square dispersion of each visibility datum over integrations  
  > "This can be overcome with the replacement of the original weights by the root-mean-square dispersion of each visibility datum, taken over all individual integrations, as performed with the `CASA` task `statwt`." (Time-differential photometry)
- **VisAlign** : Multi-epoch visibility alignment in position and amplitude scale, and gridded visibility differencing  
  > "chose PDS\,70 as an example source to test an original scheme for multi-epoch visibility alignment (the `VisAlign` package), and apply automatic self-calibration (with the `snow` package)." (Introduction); "Individual EBs from 3 and 6 December 2017 were then aligned to the first EB, from 2 December, using the ` VisAlign` package, including a correction for visibility amplitudes $\alpha_R$." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
- **snow** : Automatic phase and amplitude self-calibration  
  > "Following alignment, we concatenated the data into a single measurement set, and applied the `snow` package for automatic self calibration (cite: Carcamo2018A&C....22...16C)." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
- **gpu-uvmem** : Non-parametric pure-chi^2 image reconstruction of individual EBs and concatenated dataset  
  > "Once self-calibrated, each EB was split for separate imaging with ` gpu-uvmem`, in pure-$\chi^2$ reconstructions (i.e. without entropy regularization, but truncating the optimization at 10 iterations)." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IB17 joint 3-EB peak flux density <F_B7> | 172 | 30 | uJy | 2 | Its flux density, given by the peak intensity at the position of the point source in restored maps, is $\langle F_{\rm B7}\rangle = 172\pm30$\,$\mu$Jy, where the average represents a joint measurement over all 3 EBs. |
| IB17 joint 3-EB beam-fit flux density | 250 | 30 | uJy | 2 | / All / $62 \times 46$ / 30 / $172\pm30$ / $250\pm30$ / |
| IB17 2 December 2017 forced peak intensity F_B7 | 147 | 44 | uJy | 2 | / 2/12/2017 / $64 \times 41$ / 44 / $147\pm44$ / |
| IB17 3 December 2017 forced peak intensity F_B7 | 94 | 51 | uJy | 2 | / 3/12/2017 / $63 \times 50$ / 51 / $94\pm51$ / |
| IB17 6 December 2017 peak flux density F_B7 | 370 | 65 | uJy | 2 | The source is, however, quite conspicuous in 6 December, at $370\pm\,65\,\mu$Jy or $\sim$5.7\,$\sigma$ (as given by the peak specific intensity). |
| IB17 6 December 2017 beam-fit flux density | 502 | 65 | uJy | 2 | / 6/12/2017 / $64 \times 58$ / 65 / $370\pm65$ / $502\pm65$ / $878\pm210$ / |
| IB17 6 December 2017 Gaussian-fit flux density | 878 | 210 | uJy | 2 | / 6/12/2017 / $64 \times 58$ / 65 / $370\pm65$ / $502\pm65$ / $878\pm210$ / |
| IB17 image-plane flux rise from 3 to 6 December 2017 | 276 | 82.6 | uJy | 2 | The $F_{\rm B7}$ measurement on 6 December is roughly twice the average value of $\langle F_{\rm B7}\rangle$, and the difference between 3 and 6 December is $276\pm82.6$\,$\mu$Jy and significant at 3.3$\,\sigma$. |
| IB17 image-plane percentage flux rise from 3 to 6 December 2017 | 228 | 69 | % | 2 | In images of the 2017 ALMA dataset, with three $\sim$1\,h EBs, PDS\,70c was detected only on 6 December 2017, where $F_{\rm B7}$ rose by $228\%\pm69\%$ (3.3$\sigma$). |
| IB17 uv-plane differential flux rise from 3 to 6 December 2017 | 206 | 56 | uJy | 3 | The result is summarised in Fig.\,2, where we see that $F_{\rm B7}$ is consistent between 2 and 3 December, but rises by $206\pm56\,\mu$Jy from 3 to 6 December, which is significant at 3.7$\,\sigma$. |
| IB17 uv-plane percentage flux rise from 3 to 6 December 2017 | 170 | 46 | % | 3 | Time-differential photometry confirms a rise by $170\%\pm46\%$ (3.7$\sigma$).; Fixing $F_{\rm B7}$ to the value for IB23 in Table\,1, this rise corresponds to $170\%\pm46\%$. |
| IB17 largest variation in synthetic control point sources | 122 | 56 | uJy | 3 | Using the uncertainties inferred from the spatial scatter, as for PDS\,70c, the largest variation in $\Delta F_{\rm B7}(t)$ for the synthetic point-sources is $122\pm 56$\,$\mu$Jy, or 2.2\,$\sigma$. |
| IB23 full-EB weighted-average residual flux density Delta F_B7 | 0.2 | 8 | uJy | 3 | The weighted-average residual flux density is $\Delta F_{\rm B7} = 0.2\pm 8$\,$\mu$Jy, with a weighted scatter of 18\,$\mu$Jy, which represents $\sim$15% of the flux density reported by (cite: Dominguez2025AA...702A..18D). |
| IB23 full-EB weighted scatter | 18 | not stated | uJy | 3 | The weighted-average residual flux density is $\Delta F_{\rm B7} = 0.2\pm 8$\,$\mu$Jy, with a weighted scatter of 18\,$\mu$Jy, which represents $\sim$15% of the flux density reported by (cite: Dominguez2025AA...702A..18D). |
| IB23 20-min interval reduced chi^2 for PDS 70c | 1.67 | not stated | dimensionless | 3 | The fine-grained measurements of $\Delta F_{\rm B7}$ shown in Fig.\,6 seem to be indicative of variability, as the reduced $\chi^2$ is 1.67 (with 41 degrees of freedom). |
| IB23 20-min interval weighted scatter sigma_s | 13 | 2 | uJy | 3 | The weighted scatter is $\sigma_s = 13\pm2\,\mu$Jy, with bootstrapped uncertainties. |
| IB23 20-min interval intrinsic rms variability sigma_int | 59 | 25 | uJy | 3 | The intrinsic rms variability of PDS\,70c is $\sigma_{\rm int} = 59\pm25\,\mu$Jy.; In this case we find $\sigma_{\rm int} = 59\pm25\,\mu$Jy, with bootstrapped uncertainties. |
| IB23 20-min interval intrinsic dispersion percentage | 49 | 21 | % | 3 | However, $F_{\rm B7}(t)$ shows some scatter when splitting the deep 2023 EBs in 20\,min intervals, with a $\chi^2$ test significant at 2.6\,$\sigma$, and an intrinsic dispersion of $49\%\pm21\%$.; Fixing $F_{\rm B7}$ to the value for IB23 in Table\,1, this scatter corresponds to $49\%\pm21\%$. |
| Diffusion timescale tau_d for M_env = 0.07 M_Jup, L = 0.1 au, kappa_R = 0.1 cm^2 g^-1 | 3.5 | not stated | d | 4 | If $M_{\rm env} = 0.07 M_{\rm Jup}$, $L = 0.1$\,au, and $\kappa_R = 0.1\,$cm$^2$\,g$^{-1}$, then $\tau_d = 3.5\,{\rm d}$. |
| Environment mass M_env required for 1 h diffusion timescale | 8e-4 | not stated | M_Jup | 4 | Alternatively, the environment mass would have to be reduced to $M_{\rm env} = 8\times 10^{-4} M_{\rm Jup}$ to match an hourly variability. |
| Planet-to-environment mass ratio required for hourly thermal variability | <10^-4 | not stated | dimensionless | 4 | A planet-to-environment mass ratio $<10^{-4}$ is required to avoid smoothing by radiative diffusion if the signal is due to thermal emission from the environment. |

## Qualitative findings

- The previous non-detection of PDS 70c in the 2017 dataset by Casassus & Carcamo (2022) was caused by a missing execution block from 6 December 2017 due to a CASA mstransform task bug; including 6 December restores agreement with Isella et al. (2019).  
  > "However, perhaps as a result of a bug in the handling of `CASA` tasks (which we attribute to intensive calls to the `mstransform` task, combining both time and channel averaging), the EB from 6 December was missing. As shown below, the inclusion of 6 December brings $F_{\rm B7}$ in agreement with the original report by (cite: Isella2019ApJ...879L..25I)." (Introduction)
- In the 2017 dataset, PDS 70c is undetected in the 2 and 3 December EBs but is strongly detected on 6 December, showing a tentative flux rise over days or hours.  
  > "Imaging of individual ($\sim$1\,h) execution blocks (EBs) in the 2017 Band\,7 observations of PDS\,70 shows that PDS\,70c is conspicuous on 6 December 2017, but undetectable in both 2 and 3 December." (Conclusions)
- Neither LB19 nor IB23 shows detectable variability when evaluated across full execution blocks (~1h15m to >2h), but splitting IB23 into 20-minute intervals reveals tentative (2.6 sigma) intrinsic scatter of ~50%, suggesting hourly variability that averages out over longer integrations.  
  > "Neither LB19 nor IB23 present detectable variability among EBs." (Time-differential photometry); "These results tentatively suggest that the radio signal from PDS\,70c is variable by $\sim 50\%\pm 21\%$ on timescales of hours, but that its variability is averaged out on longer timescales." (Conclusions)
- Hourly variability that averages out over longer timescales favors H I free-free emission from an accretion shock on a circumplanetary disk surface over thermal emission from the bulk circumplanetary environment.  
  > "The radio variability of PDS\,70c, observed over hours but averaged out on longer timescales, is indeed expected if the signal is due to H\,i free-free from an accretion shock on a circum-planetary disk surface." (abstract); "We conclude for a tentative detection of hourly variability, which favours an accretion shock at the CPD surface as the origin of the signal (Sect.\,4)." (Introduction)

## Claim tuples

- H: The discrepancy between the non-detection of PDS 70c in IB17 by Casassus & Carcamo (2022) and other Band 7 measurements was due to multi-year variability. | E: Re-analyzed the complete IB17 dataset including the previously missing 6 December 2017 execution block, performing joint and individual EB imaging and uv-plane time-differential photometry. | R: The joint 3-EB flux density is <F_B7> = 172 +/- 30 uJy (consistent with Isella et al. 2019 at 1.8 sigma), while individual EBs show non-detections on 2 and 3 December and a 370 +/- 65 uJy detection on 6 December (a rise of 228% +/- 69% in images and 170% +/- 46% in uv-plane differential photometry). | F: The multi-year variability claim is refuted; the 6 December EB was accidentally omitted previously, and the true variability in IB17 occurred over days or hours between 3 and 6 December 2017. | **refuted**
- H: The Band 7 flux density of PDS 70c varies on short timescales (minutes to hours) that are averaged out in longer (>2 h) execution blocks. | E: Applied uv-plane time-differential photometry to full EBs (~2 h) of the 2023 IB23 dataset and to 20-minute sub-EB intervals, comparing against three synthetic constant control point sources. | R: Full 2 h EBs show constant flux within ~15% scatter (reduced chi^2 = 0.6), whereas 20-min intervals show a reduced chi^2 of 1.67 (2.6 sigma significance) with an intrinsic rms scatter of 59 +/- 25 uJy (49% +/- 21%), while synthetic control sources yield reduced chi^2 of 1.29-1.36 (~1.4 sigma). | F: There is tentative evidence that PDS 70c varies by ~50% on hourly timescales while averaging to a steady value over longer integrations. | **partially**
- H: Hourly radio variability of PDS 70c is produced by H I free-free emission from an accretion shock at the CPD surface rather than thermal radiation from the bulk circumplanetary environment. | E: Compared the observed hourly variability timescale against hydrodynamical shock predictions and analytical Rosseland radiative diffusion timescales tau_d = M_env * kappa_R / (c * L) for the bulk environment. | R: A standard CPD environment mass of 0.07 M_Jup with L = 0.1 au and kappa_R = 0.1 cm^2 g^-1 gives tau_d = 3.5 days; matching a 1 h diffusion time requires reducing M_env to 8e-4 M_Jup (environment-to-planet mass ratio < 10^-4), whereas CPD surface shock models naturally fluctuate on hourly timescales with instantaneous radiative transfer. | F: The hourly variability favors H I free-free emission from a CPD surface accretion shock, unless the bulk environment mass is < 10^-4 of the planetary mass. | **supported**

## Reasoning

- Why this data: ALMA Band 7 datasets of PDS 70 (IB17, LB19, IB23) provide multi-epoch high-resolution observations of the only embedded protoplanet candidate known to have a radio counterpart, enabling a revisit of earlier conflicting variability claims.  
  > "Among these candidates, only PDS\,70c is known to have a radio counterpart (cite: Isella2019ApJ...879L..25I; Benisty2021ApJ...916L...2B; Fasano2025A&A...699A.373F; Dominguez2025AA...702A..18D)." (Introduction); "We revised the analysis of (cite: CasassusCarcamo2022MNRAS.513.5790C) with the goal to resolve the discrepancy with all other measurements of $F_{\rm B7}$." (Introduction)
- Why this method: Time-differential photometry in the uv-plane after subtracting the concatenated model image avoids the sensitivity loss of uniform/Briggs weighting and the systematic confusion with the outer dust ring that affects natural-weight restored images.  
  > "But this approach requires giving artificially more weight to the longer baselines, overriding error propagation at the expense of sensitivity. In other words, with natural weights the uncertainties would be lower, but the source would no longer be isolated from the outer ring (Fig.\,1), thus introducing systematic errors." (Time-differential photometry); "Time-differential photometry allows the extraction of the relative variations of $F_{\rm B7}$ in the $uv$-plane, at higher significance than in the restored images, where the source is confused with the outer ring." (Conclusions)
- Alternative: Gridded visibility differential photometry (bypasses model image subtraction, but collapses spectral information and depends on gridding scheme; used as a consistency check rather than primary method).  
  > "As shown in Appendix 7, the gridded approach bypasses the model image, but it collapses the spectral information, and depends on the gridding scheme. Since the model image is used anyway in the self-calibration procedure, we opted for photometric extraction on the raw data." (Time-differential photometry)
- Alternative: Image-plane elliptical Gaussian and beam fitting (beam fitting biased toward larger flux densities due to extended low-level emission; elliptical Gaussian fitting sensitive to zoom box and impossible in the concatenated dataset where PDS 70c connects to the ring).  
  > "Fitting a beam resulted in a bias for larger flux densities to account for extended low-level emission. Fitting an elliptical Gaussian was sensitive on the definition of the zoomed region around PDS\,70c, and turned out to be impossible in the case of the concatenated dataset, where the source is connected to the ring." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
- Alternative: Phase-only self-calibration (did not yield improvements in S/N compared to amplitude and phase self-calibration).  
  > "Phase-only self-calibration did not yield improvements." (Alignment, self-calibration and image-plane $F_{\rm B7}$ measurements in the IB17 dataset)
- How they decided it was enough: _not stated_
- Limitation (authors): Residuals in single EBs are not perfectly thermal due to noisy antenna gains from short (50 s) amplitude self-calibration intervals (varying up to ~100% rms), making the variability detection tentative.  
  > "Since the residuals in single EBs are not perfectly thermal, this estimate is tentative." (Conclusions); "Amplitude self-calibration of the IB17 dataset required short solution intervals, down to a single scan or 50\,s. As a result, the derived antenna gains can be fairly noisy. We found the resulting gains vary strongly, up to $\sim$100% rms." (Residual maps on single EBs and impact of alignment and self-calibration)
- Limitation (authors): Splitting observations into shorter integrations (20 min) to probe fine-grained variability results in noisier individual measurements.  
  > "The difficulty in observing fine-grained time variability is that splitting into shorter integrations results in noisier measurements." (Time-differential photometry)
- Limitation (authors): Non-thermal residuals from rapidly varying antenna gains are not fully captured by the spatial scatter along the PDS 70c orbit because that region is largely devoid of extended signal.  
  > "Also, such non-thermal residuals would not be accounted for in the spatial scatter along the orbit of PDS\,70c, since that region is approximately devoid of signal." (Application to deep Band 7 data)
- Caveat (inferred, ours): Amplitude self-calibration on 50 s scan intervals with ~100% rms gain variations risks absorbing real flux variations or injecting artificial variability into embedded point sources.
- Caveat (inferred, ours): The 20-minute sub-EB variability in IB23 is only 2.6 sigma (reduced chi^2 = 1.67 vs 1.29-1.36 for constant control sources), which is marginal given the non-thermal residual systematics.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Exact astrometric offset/position x_0 of PDS 70c used for fixed-position forced and uv-plane photometry
- Missing: Version numbers and configuration parameters for custom packages VisAlign, snow, and gpu-uvmem
- Missing: ALMA project codes and specific EB UIDs (especially which 7 of the 9 EBs in IB23 were selected)
- Data volume (inferred): ~10-50 GB (three Band 7 datasets, time-averaged to 6.06 s and binned to 8 channels per spw)
- Score (inferred): 65/5, The mathematical formulation for uv-plane differential photometry, EB alignment offsets, self-calibration solution intervals, and imaging weighting/iteration settings are clearly documented, and the archival datasets are well known in the literature. However, reproduction relies on specialized custom packages (VisAlign, snow, gpu-uvmem) without version numbers or configuration scripts, and the exact target coordinates x_0 and specific subset of 7 IB23 EBs are not explicitly listed.
- Rediscovery candidate: yes, Public archival ALMA Band 7 datasets of PDS 70 with quantitative flux density, differential variability, and chi^2 answer keys that can be tested using visibility-domain photometry.

## Links

- Method: CasassusCarcamo2022MNRAS.513.5790C (Introduces the VisAlign package for multi-epoch visibility alignment and the uv-plane point-source photometry formalism)
- Method: Casassus2023MNRAS.526.1545C (Details the alignment, self-calibration, and imaging methodology applied to the PDS 70 IB17 dataset)
- Method: Carcamo2018A&C....22...16C (Describes the gpu-uvmem and snow automatic self-calibration/imaging framework)
- Companion: Dominguez2025AA...702A..18D (Presents the IB23 dataset and multi-frequency radio spectrum analysis of PDS 70c that this paper builds upon)

## Checks

```json
{
 "quotes": 125,
 "quotes_ok": 125,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 8,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.A.00006.S",
  "2018.A.00030.S",
  "2022.1.01477.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 21,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 57,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
