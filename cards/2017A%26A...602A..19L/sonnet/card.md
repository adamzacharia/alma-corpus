# A concordant scenario to explain FU Orionis from deep centimeter and millimeter interferometric observations

`2017A&A...602A..19L` | Astronomy and Astrophysics 2017 | first author: Liu, Hauyu Baobab | arXiv: 1701.06531 | DOI: 10.1051/0004-6361/201630263

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the properties (size, spectral indices, dust and gas mass) of the disks around FU Ori and FU Ori S, constrained with ~25 au resolution centimeter and millimeter observations?  
  > "The aim of this work is to constrain properties of the disk around the archetype FU Orionis object, FU Ori, with as good as $\sim$25 au resolution." (abstract)
- Target **FU Ori**: coordinates RA 05h45m22.368s, Dec +09d04m12.25s (J2000)  
  > "we assume the distance of FU Ori to be $d$$\sim$353($^{+81}_{-56}$) pc, according to the parallax measurement published in the first data release of the Gaia space telescope" (Introduction); z/distance ~353 pc  
  > "we assume the distance of FU Ori to be $d$$\sim$353($^{+81}_{-56}$) pc, according to the parallax measurement published in the first data release of the Gaia space telescope" (Introduction); distance from Gaia DR1 parallax (Gaia Collaboration 2016)  
  > "we assume the distance of FU Ori to be $d$$\sim$353($^{+81}_{-56}$) pc, according to the parallax measurement published in the first data release of the Gaia space telescope" (Introduction)
- Target **FU Ori S**: coordinates RA 05h45m22.377s, Dec +09d04m11.77s (J2000)  
  > "FU Ori S is presently considered as a $\sim$1 $M_{\odot}$ pre-main sequence star (Wang et al. 2004)." (3 Results); z/distance ~353 pc  
  > "FU Ori S is presently considered as a $\sim$1 $M_{\odot}$ pre-main sequence star (Wang et al. 2004)." (3 Results); distance from Gaia DR1 parallax assumed for FU Ori  
  > "FU Ori S is presently considered as a $\sim$1 $M_{\odot}$ pre-main sequence star (Wang et al. 2004)." (3 Results)

## Data provenance

- ALMA projects: 2011.0.00548.S
- bands: _not stated_
- frequencies and spectral setup: Archival ALMA 346 GHz flux taken from Hales et al. 2015; paper's own new data are JVLA 33 and 9 GHz and SMA 224 and 272 GHz  
  > "Taken from Hales et al. (2015)." (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: ALMA (Hales et al. 2015): 15-384 m, 17-440 kλ  
  > "The ALMA observations of Hales et al. (2015) covers the projected baseline lengths of 15-384 meter, which corresponds to 17-440 $k\lambda$." (footnote 3)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA 346 GHz: 2012 Dec 02  
  > "| 345.784$^{3}$ | 2012Dec02 |" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **JVLA Ka band (29-37 GHz) and X band (8-10 GHz)**: Ka A-array 0.08 arcsec imaging resolving two compact sources; X band non-detection with 3σ limit 14 μJy  
  > "The JVLA 8-10 GHz observations show no significant detection, which constrained the 3$\sigma$ upper limit to 14 $\mu$Jy for both sources." (3 Results)
- Other facility **SMA 224 GHz and 272 GHz**: Millimeter continuum fluxes; 272 GHz are archival data (PI Bourke)  
  > "We retrieved the archival SMA 1.2 mm observations taken in the compact array configuration on 2008 December 06 (PI: Tyler Bourke)." (2.2.2 272 GHz)
- Other facility **Subaru-HiCIAO**: 1.6 μm polarization image for overlay (previous work)  
  > "An overlay of the JVLA 33 GHz image with the previous Subaru High Contrast Instrument for the Subaru Next Generation Adaptive Optics (HiCIAO) 1.6 $\mu$m polarization intensity image (Liu et al. 2016b) is presented" (3 Results)
- External data: ALMA 346 GHz fluxes of FU Ori (50.1 mJy) and FU Ori S (21.2 mJy)  
  > "Taken from Hales et al. (2015)." (Table 1) [from Hales et al. (2015)]
- External data: Bolometric luminosity of FU Ori 139 Lsun  
  > "a measured bolometric luminosity of 139 $L_\odot$ (Zhu et al. 2007) for FU Ori" (3 Results) [from Zhu et al. 2007]
- External data: Dust opacity and index assumptions for mass limits  
  > "We consider three generic assumptions of dust opacity and opacity index which are motivated by Draine et al. (2006)" (Appendix) [from Draine et al. 2006]

## Processing

### Calibration

- pipeline or manual: JVLA calibrated manually in CASA; SMA with MIR IDL  
  > "We manually followed the standard data calibration strategy using the Common Astronomy Software Applications (CASA; McMullin et al. 2007) package, release 4.7.0-1." (2.1.1 Ka band)
- casa version: CASA 4.7.0-1 (JVLA data)  
  > "Passband, complex gain, and absolute flux calibrations were carried out manually using CASA release 4.7.0-1." (2.1.2 X band)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C147 (JVLA)  
  > "We observed the bright quasar 3C147 for passband and absolute flux calibrations." (2.1.1 Ka band)
- flux scale uncertainty: ~15-20% for SMA and ALMA  
  > "A typical absolute flux calibration accuracy can be $\sim$15-20% for SMA observations." (2.2.1 224 GHz)
- self calibration: _not stated_

### Imaging

- task: CASA clean (multi-frequency); Miriad for SMA  
  > "We generated images using the CASA task `clean`." (2.1.1 Ka band)
- deconvolver: _not stated_
- weighting robust: Briggs Robust=2 (X band and SMA 224 GHz)  
  > "Using Briggs Robust=2 weighting yielded a $\theta_{\mbox{\tiny{maj}}}$$\times$$\theta_{\mbox{\tiny{min}}}$=0$\ensuremath{''}$31$\times$0$\ensuremath{''}$23 (P.A.=-41$^{\circ}$) synthesized beam." (2.1.2 X band)
- uv taper: _not stated_
- cell size: 0.01 arcsec (Ka band)  
  > "The image size is 6000 pixels in each dimension, and the pixel size is 0$\ensuremath{''}$01." (2.1.1 Ka band)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: Ka 3.6 μJy/beam; X 4.7 μJy/beam; SMA 224 GHz 1.6 mJy/beam  
  > "Stokes I rms noise level of $\sim$3.6 $\mu$Jy beam$^{-1}$." (2.1.1 Ka band)

### Inherited from earlier work

- SMA 224 GHz observation details  
  > "The details of these SMA observations have been summarized in Table 1 of Liu et al. (2016a)." (2.2.1 224 GHz) [from Liu et al. (2016a)]
- Dust opacity assumptions  
  > "We consider three generic assumptions of dust opacity and opacity index which are motivated by Draine et al. (2006)" (Appendix) [from Draine et al. (2006)]

### Not stated but needed to reproduce (our reading)

- ALMA data processing and calibration used for the 346 GHz flux (taken from Hales et al. 2015)
- Clean threshold, masking and niter for JVLA imaging
- SED model fitting procedure: how parameters of Table were chosen (apparently by hand)
- Uncertainties on SED model parameters
- Details of the 224 GHz SMA observations (in Liu et al. 2016a)

## Analysis recipe

1. **Image JVLA and SMA continuum and measure fluxes**: Multi-frequency clean of JVLA data; Miriad imaging of SMA; fluxes in Table 1  
  > "we performed multi-frequency `clean` jointly for all observed spectral windows" (2.1.1 Ka band)
   - software: CASA, Miriad
   - fitting: _not stated_
   - validation: Noise consistent with theoretical level  
  > "The measured noise level is consistent with the theoretical noise level." (2.1.1 Ka band)
2. **Measure source sizes and spectral indices**: 2D Gaussian fits for deconvolved sizes; least-squares power-law fits with bootstrapping for α  
  > "In the end, $\alpha$ and its error were determined by the mean and standard deviations of the fittings to 10,000 independent realizations of perturbed fluxes." (3 Results)
   - assumption: distance 353 pc  
  > "Assuming a distance of 353 pc, the deconvolved size scales of FU Ori and FU Ori S" (3 Results)
   - fitting: Least squares with 10,000 bootstrap realizations  
  > "We performed Least Square fittings to determine their spectral indices ($\alpha$)." (3 Results)
   - validation: _not stated_
3. **Lower-limit masses assuming optically thick dust**: τ(33 GHz)=1 with three Draine opacity cases, within deconvolved Gaussian areas  
  > "The required $\Sigma$ value to yield optical depth $\tau_{\mbox{\tiny{33 GHz}}}$$=$1 are 7.7 g cm$^{-2}$, 10 g cm$^{-2}$, and 14 g cm$^{-2}$, respectively." (Appendix)
   - assumption: gas-to-dust ratio 100  
  > "Assuming an interstellar gas-to-dust mass ratio of 100, the derived lower limit of overall gas mass is in the range of 8.6-17$\times$10$^{-3}$ $M_{\odot}$." (Appendix)
   - fitting: _not stated_
   - validation: _not stated_
4. **Three-component SED model (free-free + thick dust + thin dust)**: Co-add free-free and two modified black body components; parameters set by hand to match fluxes and X-band limit  
  > "the overall fluxes for each of FU Ori and FU Ori S at all frequencies were evaluated by simply co-adding the fluxes of a free-free emission component, an optically thicker dust thermal emission component, and an optically thinner dust component." (4.1 Fiducial SED model)
   - parameter: β=1.75 fixed; Te=16000 K  
  > "We fix the dust opacity index to $\beta$=1.75" (4.1 Fiducial SED model)
   - assumption: gas-to-dust 100, d=353 pc; parameters degenerate  
  > "the parameters $\kappa_{\mbox{\tiny{230 GHz}}}$$\Sigma$, $T$, and $\Omega$ are degenerated." (4.1 Fiducial SED model)
   - fitting: not a formal fit  
  > "Our present models do not uniquely explain the measured fluxes, but serve as simplified cases" (4.1 Fiducial SED model)
   - validation: Compared with fluxes and X-band limits  
  > "can result in $\alpha$$<$2.0 at 29-37 GHz and a rapidly dropping overall flux toward lower frequency such that it cannot be detected by sensitive JVLA X band observations at 8-10 GHz." (Discussion, Fiducial SED model)

## Software

- **CASA** 4.7.0-1: JVLA calibration and imaging  
  > "release 4.7.0-1" (2.1.1 Ka band)
- **MIR IDL** : SMA calibration  
  > "were carried out using the MIR IDL software package (Qi 2003)" (2.2.1 224 GHz)
- **Miriad** : SMA continuum imaging  
  > "were performed using the Miriad software package (Sault et al. 1995)" (2.2.1 224 GHz)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| JVLA 33 GHz flux FU Ori | 206 | 4.3 | μJy | 1 | / 32.991 / 2016Oct06/2016Oct11 / 206$\pm$4.3 (FU Ori) / |
| JVLA 33 GHz flux FU Ori S | 104 | 5.6 | μJy | 1 | /  /  / 104$\pm$5.6 (FU Ori S) / |
| Spectral index 29-37 GHz FU Ori | 1.56 | 0.47 | dimensionless | 2 | which are 1.56$\pm$0.47 and 1.43$\pm$0.72, respectively. |
| Spectral index 29-37 GHz FU Ori S | 1.43 | 0.72 | dimensionless | 2 | which are 1.56$\pm$0.47 and 1.43$\pm$0.72, respectively. |
| Joint spectral index all data | 2.3 | 0.06 | dimensionless | 2 | yielded $\alpha$=2.3$\pm$0.06 for both sources. |
| Gas mass lower limit (optically thick) | 8.6-17e-3 | not stated | Msun | 3 | the derived lower limit of overall gas mass is in the range of 8.6-17$\times$10$^{-3}$ $M_{\odot}$. |
| Brightness temperature 33 GHz FU Ori | 210 (+81/-51) | +81/-51 | K | 2 | $T_{\mbox{\tiny{B, 33 GHz}}}^{\mbox{\tiny{FU Ori}}}$$\sim$210$_{-51}^{+81}$ K |
| X-band 3σ upper limit | 14 | not stated | μJy | 1 | constrained the 3$\sigma$ upper limit to 14 $\mu$Jy for both sources. |

## Qualitative findings

- No evidence for thermal radio jet; expected flux is a factor of 90 above the limit  
  > "This is a factor of 90 above the 3-$\sigma$ upper limit of 0.014 mJy obtained by us." (3 Results)

## Claim tuples

- H: Is a radio jet present in FU Ori? | E: JVLA 8-10 GHz deep imaging | R: No detection, 3σ<14 μJy vs expected 1.24 mJy | F: Jet emission strongly suppressed | **supported**
- H: Are the disks resolved and compact at 33 GHz? | E: JVLA A-array Ka imaging and 2D Gaussian fits | R: Two compact sources with radii of a few au | F: Compact sources much smaller than the gaseous disk | **supported**
- H: Disk mass sufficient for gravitational instability | E: Three-component SED modeling | R: Gas mass up to a fraction of a solar mass | F: Mass adequate for GI, though models are degenerate | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Time variability or missing short spacings explain the varying spectral index; free-free alone rejected as the X-band flux would exceed the limit  
  > "Since these observations were separated in time by several years, we also cannot rule out the interpretation by time varying (sub)millimeter fluxes." (3 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): SED models are degenerate and non-unique  
  > "Our present models do not uniquely explain the measured fluxes, but serve as simplified cases for qualitatively comprehending the observational results." (4.1 Fiducial SED model)
- Caveat (inferred, ours): Different uv coverages and epochs make the SED comparison ambiguous
- Caveat (inferred, ours): SED model parameters were hand-chosen with no formal uncertainties
- Caveat (inferred, ours): ALMA data used only as a literature flux

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Model fitting procedure
- Missing: SMA 224 GHz observing details (in another paper)
- Missing: ALMA flux measurement details
- Data volume (inferred): JVLA Ka data likely hundreds of GB; ALMA part small
- Score (inferred): 3/5, ALMA is only a literature flux point and the SED modeling is not formal, though the JVLA recipe is largely described.
- Rediscovery candidate: no, Main data are JVLA and SMA, not ALMA; the model is hand-tuned.

## Links

- Companion: Hales et al. (2015) (Source of the ALMA 346 GHz fluxes)
- Companion: Liu et al. (2016a) (SMA 224 GHz observation details)
- Companion: Liu et al. (2016b) (Subaru-HiCIAO polarization image)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 76,
  "stated": 44,
  "rate": 0.579
 },
 "evidence_ok": true
}
```
