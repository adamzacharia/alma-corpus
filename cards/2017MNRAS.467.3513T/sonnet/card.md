# On the dust and gas components of the z = 2.8 gravitationally lensed quasar host RX J0911.4+0551

`2017MNRAS.467.3513T` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Tuan-Anh, P. | arXiv: 1609.03271 | DOI: 10.1093/mnras/stx212

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Are the dust and gas components of the lensed quasar host RX J0911 compact and concentric with the quasar, and what are their sizes, using ALMA 358 GHz continuum plus PdBI CO(7-6) and HST lensing constraints?  
  > "The good knowledge of the lensing potential obtained from Hubble Space Telescope observations of the quasar makes a joint analysis of the three emissions possible." (abstract)
- Target **RX J0911.4+0551**: coordinates _not stated_; z/distance z = 2.8; 1 arcsec = 7.98 kpc  
  > "It is a $z=2.8$ quasar." (RX J0911 and its host galaxy); "this implies that an angular distance of 1 arcsec corresponds to a real distance of 7.98 kpc" (RX J0911 and its host galaxy); distance from LCDM H0=71, Omega_M=0.27, Omega_Lambda=0.73  
  > "It is a $z=2.8$ quasar." (RX J0911 and its host galaxy); "this implies that an angular distance of 1 arcsec corresponds to a real distance of 7.98 kpc" (RX J0911 and its host galaxy)

## Data provenance

- ALMA projects: 2011.0.00307.S
- bands: _not stated_
- frequencies and spectral setup: 358 GHz continuum over four frequency bands; CO(10-9) and CO(11-10) at 303.69 and 333.79 GHz  
  > "The continuum was observed at 358 GHz over four frequency bands for a total on-source time of 26 minutes." (New observations and data reduction); "CO(10-9) and CO(11-10), at respective frequencies of 303.69 and 333.79 GHz" (New observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 26 antennas (continuum); 16 antennas, Cycle 0 compact configuration (CO lines)  
  > "using 16 antennas with a maximum baseline of 126 m (ALMA cycle 0 compact configuration)" (New observations and data reduction)
- configurations: _not stated_
- baselines: max baseline ~370 m (continuum); 126 m (CO lines)  
  > "It made use of 26 antennas with a maximum baseline of $\sim$ 370 m" (New observations and data reduction)
- angular resolution: 0.55x0.51 arcsec^2 (continuum); ~1.5 arcsec (CO lines)  
  > "corresponding to a nearly circular beam of $0.55\times 0.51$ arcsec$^2$" (New observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: effective noise peak FWHM 0.39 mJy/beam; 165 uJy/beam effective noise used in fits  
  > "reveals an effective noise peak having a FWHM of 0.39 mJy beam$^{-1}$" (New observations and data reduction)
- time on source: 26 min continuum; 10 and 20 min for CO(10-9) and CO(11-10)  
  > "for on-source times of 10 and 20 minutes respectively" (New observations and data reduction)
- observing dates: 16 Nov 2012 (continuum); 15 Nov 2011 (CO lines)  
  > "They were observed on 15th November 2011" (New observations and data reduction)
- pi or archival as stated: Archival, PI A. Weiss  
  > "(PI A. Weiss)" (New observations and data reduction)
- Line: CO 10-9 (303.69 GHz (observed))
- Line: CO 11-10 (333.79 GHz (observed))
- Other facility **HST**: Images of quasar images and lens galaxy; lensing potential  
  > "The good knowledge of the lensing potential obtained from Hubble Space Telescope observations of the quasar" (abstract)
- Other facility **PdBI**: CO(7-6) data  
  > "They complement earlier Plateau de Bure Interferometer observations of the CO(7-6) emission." (abstract)
- External data: Lensing potential 1 and source position from HST fit  
  > "more precisely the lensing potential 1 of (cite: Tuananh2014), hereafter referred to as the potential" (Astrometry) [from (cite: Tuananh2014)]
- External data: PdBI CO(7-6) size, 129+-15 mas rms radius  
  > "129$\pm$15 mas (meaning 1.01$\pm$0.12 kpc or 2.6$\pm$0.3 kpc FWHM)" (RX J0911 and its host galaxy) [from (cite: Tuananh2013; Tuananh2014)]

## Processing

### Calibration

- pipeline or manual: Processed by ALMA staff (details not given)  
  > "We checked the good quality of the data reduction, including calibration." (New observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Data processed by ALMA staff; clean map used; quality checked  
  > "The data have been processed by the ALMA staff and are available in the form of a clean map of 256$\times$256 pixels" (New observations and data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.1x0.1 arcsec^2  
  > "a clean map of 256$\times$256 pixels of 0.1$\times$0.1 arcsec$^2$ each" (New observations and data reduction)
- image size: 256x256 pixels  
  > "a clean map of 256$\times$256 pixels" (New observations and data reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.55x0.51 arcsec^2  
  > "nearly circular beam of $0.55\times 0.51$ arcsec$^2$" (New observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Lensing potential and its HST best-fit parameters  
  > "more precisely the lensing potential 1 of (cite: Tuananh2014)" (Astrometry) [from (cite: Tuananh2014)]
- Position uncertainty of +-10 mas used for size error  
  > "The uncertainty attached to this measurement has been evaluated for an uncertainty of $\pm$10 mas of the source position in both $x$ and $y$ (cite: Tuananh2014)." (Measurement of the source sizes) [from (cite: Tuananh2014)]
- B/A flux ratio method for source size  
  > "As explained in (cite: Tuananh2014), an independent evaluation of the source size can be obtained from the ratio between the observed brightness of images B and A’s" (Measurement of the source sizes) [from (cite: Tuananh2014)]

### Not stated but needed to reproduce (our reading)

- Fitting code and minimiser used for map-plane and uv-plane fits
- Exact visibility weighting and which spectral windows/channels used for continuum
- How effective noise 165 uJy/beam relates to the 0.39 mJy/beam quoted
- Line-free channels and continuum scaling used for CO line continuum subtraction
- Flux scale uncertainty and flux calibrator
- Source-plane model details (pixelisation, magnification computation)
- PdBI data reduction details
- Exact A and B integration regions for B/A ratio

## Analysis recipe

1. **Fix astrometric offsets between HST, PdBI and ALMA frames**: Fit disc source centred on quasar to PdBI line (160 mas radius) and ALMA continuum (40 mas) data via HST lens model; cross-check direct ALMA-PdBI fit  
  > "obtain offsets (offsets 2) between the HST and ALMA reference frames from a best fit to the ALMA continuum data of a model using for the source a disc having a radius of 40 mas and centred on the quasar;" (Astrometry)
   - assumption: Quasar point source and CO(7-6) centre identical  
  > "assume that the quasar point source and the centre of the CO(7-6) line emission are identical;" (Astrometry)
   - fitting: _not stated_
   - validation: Direct vs indirect offsets agree to 15 mas in x and 6 mas in y  
  > "15 mas in $x$ and 6 mas in $y$, is merely a consistency cross-check" (Astrometry)
2. **Test concentricity of quasar, dust and gas**: Average flux along BA1 and BA3 roads, measure image separations, convert to source displacement with linearised lens response  
  > "We average the 358 GHz continuum flux over two roads along the BA1 and BA3 lines, each $\pm$0.3 arcsec wide" (Clean maps and concentricity of the sources)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit continuum source size on clean map**: Circular uniform disc or Gaussian source through lens model; chi2 vs rms radius rho  
  > "The fits are first made on the clean map, using as uncertainty 10% of the measured flux density added in quadrature to the 165 $\mu$Jy beam$^{-1}$ of effective noise" (Measurement of the source sizes)
   - assumption: Circular morphology, disc or Gaussian bracket reality  
  > "assume a circular morphology in the form of either a uniform disc or a Gaussian, two extreme configurations that may reasonably be thought to bracket reality" (Measurement of the source sizes)
   - fitting: chi2 minimisation (details not stated)  
  > "Table [\[Table3\]](#Table3) summarizes the result of the best fits and Figure [7](#fig7) displays the dependence of their $\chi^2$ on the source size" (Measurement of the source sizes)
   - validation: Compared to uv-plane and B/A results  
  > "Such agreement between results obtained by two completely independent methods brings additional confidence in their validity." (Measurement of the source sizes)
4. **Fit source size in uv plane**: Fit 76x10^3 complex visibilities; chi2/dof ~3.4  
  > "The fit is done over 76$\times$10$^3$ complex visibilities, meaning $152\times10^3$ degrees of freedom." (Measurement of the source sizes)
   - fitting: _not stated_
   - validation: Disc vs Gaussian give rho 32 and 40 mas  
  > "the respective $\rho$ values being 32 and 40 mas" (Measurement of the source sizes)
5. **Size from B/A flux ratio**: Compare measured B/A (11.6+-1.2%) with lens model predictions for disc and Gaussian sources  
  > "The present 358 GHz ALMA data give a B/A ratio of 11.6$\pm$1.2%." (Measurement of the source sizes)
   - fitting: _not stated_
   - validation: _not stated_
6. **Measure integrated continuum and CO line parameters**: Sum flux over A and B regions (9.4 beams); scale continuum, subtract from CO(10-9)/(11-10), fit Gaussians  
  > "Subtracting such contributions and fitting Gaussian profiles gives the results listed in Table" (Line parameters)
   - fitting: Gaussian line profiles  
  > "Subtracting such contributions and fitting Gaussian profiles gives the results listed in Table [\[Table4\]](#Table4)." (Line parameters)
   - validation: Observed frequencies agree with expectation within ~10 MHz  
  > "The observed frequency values are in excellent agreement with expectation within errors ($\sim$10 MHz)." (Line parameters)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust continuum FWHM | 0.76 | 0.04 (abstract) / 0.08 (text) | kpc | 5 | 0.76 $\pm$ 0.04 kpc FWHM |
| Final rms radius rho (continuum) | 38 | 4 | mas | 5 | we retain as final value of the size of the 358 GHz continuum emission $\rho=38\pm 4$ mas |
| rho from clean-map fit | 34 | 6 | mas | 3 | A same value of 34$\pm$6 mas (0.27$\pm$0.05 kpc) is obtained for $\rho$ |
| rho from uv-plane fit | 36 | 4 | mas | 4 | We therefore retain as a final result $\rho=36\pm 4$ mas |
| B/A ratio at 358 GHz | 11.6 | 1.2 | percent | 5 | The present 358 GHz ALMA data give a B/A ratio of 11.6$\pm$1.2%. |
| Gas/dust size ratio | 3.4 | 0.4 | dimensionless | 5 | It is 3.4$\pm$0.4 times smaller than the size of the CO(7-6) emission |
| Quasar-continuum concentricity limit | 40 mas (0.31 kpc) | upper limit | mas | 2 | the quasar and 358 GHz emissions are concentric within 40 mas, meaning 0.31 kpc |
| Quasar-CO(7-6) concentricity limit | 140 mas (1.10 kpc) | upper limit | mas | 2 | while the quasar and CO(7-6) emissions are concentric within 140 mas, meaning 1.10 kpc |
| Integrated continuum flux at 833 um | 31.7 | 0.5 | mJy | 6 | adds up to 31.7 mJy at an average wavelength of 833 $\mu$m |
| Mean CO line width | 107 | 20 | km/s | 6 | Averaging over the four measurements gives a common line width of 107$\pm$20 km s$^{-1}$. |
| CO(10-9) velocity-integrated flux | 4.5 | 1.0 | Jy km/s | 6 | CO(10-9) \[3\] / 303.48 / 22.7 $\pm$ 0.5 / 89$\pm$16/89$\pm$16 / 47$\pm$8 / 4.5$\pm$1.0 |
| CO(11-10) velocity-integrated flux | 2.5 | 0.9 | Jy km/s | 6 | CO(11-10) \[3\] / 333.80 / 27.5$\pm$0.5 / 113$\pm$30/102$\pm$28 / 24$\pm$5 / 2.5$\pm$0.9 |

## Qualitative findings

- Dust and gas are compact and concentric with the quasar, arguing against recent major mergers; detection of high-J CO suggests warmer/denser gas and possible AGN heating.  
  > "argues against any important and recent merger contribution" (Summary and discussion)

## Claim tuples

- H: Quasar, dust and gas are concentric | E: Image-separation analysis of ALMA 358 GHz and PdBI CO(7-6) | R: Concentric within 0.31 kpc (dust) and 1.10 kpc (gas) | F: No evidence for recent major merger | **supported**
- H: The dust source can be resolved and sized | E: Lens-model fits on map and uv plane plus B/A ratio | R: FWHM 0.76 kpc; 3.4 times smaller than CO(7-6) | F: Dust component more compact than gas | **supported**
- H: High-J CO lines are present with narrow width | E: Gaussian fits to CO(10-9) and CO(11-10) | R: Detections, mean FWHM 107+-20 km/s | F: Higher temperature/density, possible AGN contribution | **partially**

## Reasoning

- Why this data: ALMA gives high-sensitivity 358 GHz continuum, detecting image B clearly for the first time  
  > "For the first time, image B is clearly detected in the continuum" (Clean maps and concentricity of the sources)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO(10-9)/(11-10) resolution and sensitivity insufficient to resolve source; size uncertainty dominated by systematics; chi2/dof ~3.4 indicates underestimated errors.  
  > "the uncertainty on the source size is completely dominated by systematic effects" (Measurement of the source sizes)
- Caveat (inferred, ours): Size depends strongly on the lens model inherited from a PhD thesis
- Caveat (inferred, ours): Reported uncertainty on FWHM inconsistent (0.04 vs 0.08 kpc)
- Caveat (inferred, ours): No stated fitting code or visibility weighting
- Caveat (inferred, ours): Astrometric offsets between frames are large relative to source size
- Caveat (inferred, ours): Line widths from low S/N data

## Reproducibility

- Data public (paper): Public archive data  
  > "presently archived and open to public access" (New observations and data reduction)
- Products in archive: _not stated_
- Missing: Lens potential details beyond Table 2 and thesis
- Missing: Fitting code
- Missing: PdBI data
- Missing: HST positions of images
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Public data and many numbers, but fitting code, weights and inherited lens model are not specified.
- Rediscovery candidate: no, Depends on inherited lens model and PdBI/HST inputs not fully provided, and recipe incomplete.

## Links

- Companion: (cite: Tuananh2013) (Earlier PdBI CO(7-6) observations of RX J0911)
- Companion: (cite: Tuananh2014) (Lensing potential and source size analysis)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 41,
  "rate": 0.569
 },
 "evidence_ok": true
}
```
