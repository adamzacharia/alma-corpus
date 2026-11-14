# The ice composition in the disk around V883 Ori revealed by its stellar outburst

`2019NatAs...3..314L` | Nature Astronomy 2019 | first author: Lee, Jeong-Eun | arXiv: 1809.00353 | DOI: 10.1038/s41550-018-0680-0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry, star_formation
- Question: Can the outburst-driven expansion of the snow line in V883 Ori reveal the ice composition (COM abundances) of the disk midplane, and how does it compare with hot corinos and comets?  
  > "This result suggests that outbursting young stars can provide a special opportunity to study the ice composition of material directly related to planet formation." (abstract)
- Target **V883 Ori**: coordinates 05h38m18.10s, -07d02m26.0s (J2000 phase center)  
  > "We therefore adopt the median distance to the nearby stars in L1641 of 388 pc for V883 Ori." (Methods); "The phase center was at $(\alpha, \delta)_{J2000}=(05^{h}38^{m}18.10^{s}, -07\mbox{$^\circ$}02'26.0'')$" (Methods); z/distance 388 pc  
  > "We therefore adopt the median distance to the nearby stars in L1641 of 388 pc for V883 Ori." (Methods); "The phase center was at $(\alpha, \delta)_{J2000}=(05^{h}38^{m}18.10^{s}, -07\mbox{$^\circ$}02'26.0'')$" (Methods); distance from median Gaia DR2 distance of L1641 members near V883 Ori  
  > "We therefore adopt the median distance to the nearby stars in L1641 of 388 pc for V883 Ori." (Methods); "The phase center was at $(\alpha, \delta)_{J2000}=(05^{h}38^{m}18.10^{s}, -07\mbox{$^\circ$}02'26.0'')$" (Methods)

## Data provenance

- ALMA projects: 2016.1.00728.S, 2017.1.01066.T
- bands: Band 7  
  > "with ALMA in Band 7 on 8 September 2017 with a resolution of $\sim 0.03\mbox{$^{\prime \prime}$}$" (main text)
- frequencies and spectral setup: Cycle 4: one window at 334.3955 GHz, 93.75 MHz bandwidth, 488 kHz resolution; Cycle 5: ten windows, 468.75 or 117.19 MHz wide, 282 kHz resolution  
  > "a spectral window was centered at 334.3955GHz (HDO 3$_{3,1}$-4$_{2,2}$) with a bandwidth of 93.75 MHz and spectral resolution of 488 kHz" (Methods); "Their bandwidths were 468.75 MHz or 117.19 MHz and their spectral resolution was 282 kHz ($\sim$0.2 km s$^{-1}$)." (Methods)
- continuum bandwidth: _not stated_
- arrays: Forty-seven (Cycle 4) and forty-five (Cycle 5) 12-m antennas  
  > "Forty-five 12-m antennas were used" (Methods)
- configurations: _not stated_
- baselines: Cycle 4: 21 m to 10.6 km; Cycle 5: 15 m to 1.4 km  
  > "baselines in the range from 21 m ($\simeq$24 k$\lambda$) to 10.6 km ($\simeq$11900 k$\lambda$)" (Methods); "baselines in the range from 15 m ($\simeq$17 k$\lambda$) to 1.4 km ($\simeq$1578 k$\lambda$)" (Methods)
- angular resolution: 0.043"x0.025" (Cycle 4, robust 0.5); 0.23"x0.17" (Cycle 5, robust 0)  
  > "synthesized beam size of $0.23\mbox{$^{\prime \prime}$}\times 0.17\mbox{$^{\prime \prime}$}$ (PA=$65.7^{\circ}$)" (Methods)
- max recoverable scale: _not stated_
- sensitivity: RMS 4 mJy/beam (Cycle 4 lines, tapered); 7-8 mJy/beam (Cycle 5 lines)  
  > "the RMS noise level for the molecular lines is 7$\sim$8 mJy beam$^{-1}$." (Methods)
- time on source: Cycle 4: 15.6 min total; Cycle 5: 44.53 min total  
  > "the total observing time was 15.6 minutes" (Methods); "The total observing time was 44.53 minutes." (Methods)
- observing dates: 2017 Sep 8 (Cycle 4); 2018 Feb 21 (Cycle 5)  
  > "on 2017 Sep. 8 and during Cycle 5 (2017.1.01066.T, PI: Jeong-Eun Lee) on 2018 Feb. 21" (Methods)
- pi or archival as stated: Cycle 4 PI Lucas Cieza; Cycle 5 PI Jeong-Eun Lee  
  > "during Cycle 4 (2016.1.00728.S, PI: Lucas Cieza)" (Methods)
- Line: 13CH3OH 12(11)-12(12) and others (not stated)
- Line: HDO 3(3,1)-4(2,2) (334.3955 GHz)
- Other facility **Gaia DR2**: parallaxes of L1641 members to derive distance 388 pc  
  > "This set of stars has a distance of $388$ pc and a standard deviation of 16 pc" (Methods)
- External data: Stellar mass 1.2 Msun, midplane snow line, source velocity 4.3 km/s, T_mid(0.1")=100 K  
  > "The source velocity is 4.3 km s$^{-1}$(cite: Cieza2016)." (Methods) [from (cite: Cieza2016)]
- External data: Dust absorption opacity at 1.3 mm of 2.2 cm2/g and Tatm/Tmid=2  
  > "dust absorption opacity at 1.3 mm ($2.2~{\rm cm^2 g^{-1}}$)(cite: Cieza2018)" (Methods) [from (cite: Cieza2018)]
- External data: Elemental 12C/13C = 60  
  > "multiplied by the elemental abundance of $^{12}$C/$^{13}$C$=60$(cite: Langer1993)" (Methods) [from (cite: Langer1993)]
- External data: COM abundances in IRAS 16293B and comets for comparison  
  > "higher than those in the hot corino IRAS 16293 B(cite: Jorgensen2016; Lykke2017; Calcutt2018b)" (main text) [from (cite: Jorgensen2016; Lykke2017; Calcutt2018b; LeRoy2015)]

## Processing

### Calibration

- pipeline or manual: standard data reduction in CASA  
  > "We carried out the standard data reduction using CASA 4.7.2 (for Cycle 4) and 5.1.1 (for Cycle 5)" (Methods)
- casa version: CASA 4.7.2 (Cycle 4), 5.1.1 (Cycle 5)  
  > "CASA 4.7.2 (for Cycle 4) and 5.1.1 (for Cycle 5)" (Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Cycle 4: J0423-0120; Cycle 5: J0510+1800  
  > "J0423-0120 for flux calibration" (Methods); "J0510+1800 was used for bandpass and flux calibration" (Methods)
- flux scale uncertainty: 10% absolute calibration error  
  > "The observational uncertainty is dominated by the absolute calibration error of 10 %." (Methods)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Cycle 4 robust = 0.5; Cycle 5 robust = 0.0  
  > "when Briggs weighting (robust = 0.0) is adopted" (Methods)
- uv taper: 1000 klambda for Cycle 4 lines; none for Cycle 5  
  > "Briggs weighting with a uv-taper of 1000 k$\lambda$ was used for the molecular lines" (Methods); "We did not use a uv-taper for the Cycle 5 data." (Methods)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.125"x0.108" PA 75.0 (Cycle 4 tapered)  
  > "a resolution ($0.125\mbox{$^{\prime \prime}$}\times 0.108\mbox{$^{\prime \prime}$}$, PA=$75.0^{\circ}$)" (Methods)
- final rms: 4 mJy/beam (Cycle 4); 7-8 mJy/beam (Cycle 5)  
  > "The root mean square (RMS) noise level of the molecular lines is 4 mJy beam$^{-1}$." (Methods)

### Inherited from earlier work

- Disk parameters (stellar mass, snow line, source velocity, T_mid at 0.1")  
  > "We adopt $T_{\rm mid} (0.1\mbox{$^{\prime \prime}$}) = 100$ K (ref. (cite: Cieza2016))" (Methods) [from (cite: Cieza2016)]
- Line velocity shifting to source velocity to reduce blending  
  > "is shifted to the source velocity to reduce the line blending(cite: Yen2016)" (Methods) [from (cite: Yen2016)]
- Vertical temperature prescription  
  > "we follow the vertical gradient prescription of an irradiated disk model(cite: Dartois2003; Andrews2011)" (Methods) [from (cite: Dartois2003; Andrews2011)]
- Band 6/7 spectral index from continuum images  
  > "(Cassasus et al. in prep.)" (Methods) [from Cassasus et al. in prep.]

### Not stated but needed to reproduce (our reading)

- Which continuum image (Band 6) and its reduction were used for the radiative transfer fit
- CASA task parameters (tclean deconvolver, cell/image size, masks, niter, threshold)
- Line-free channels and continuum subtraction method
- Self-calibration details
- Moment map clipping thresholds
- XCLASS/MAGIX fit priors and ranges
- Supplementary Tables 1 and 3 line lists partially incomplete
- Beam used for the Cycle 5 high-res images and final image rms of continuum

## Analysis recipe

1. **Calibrate and image data**: Standard CASA reduction; Briggs imaging, tapered for Cycle 4 lines  
  > "We carried out the standard data reduction using CASA 4.7.2 (for Cycle 4) and 5.1.1 (for Cycle 5)" (Methods)
   - software: CASA
   - parameter: Cycle 4 uv-taper 1000 klambda, robust 0.5; Cycle 5 robust 0.0  
  > "Briggs weighting with a uv-taper of 1000 k$\lambda$ was used for the molecular lines" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
2. **Determine distance**: Median distance of 47 Gaia DR2 L1641 members near V883 Ori  
  > "yields 47 stars with parallaxes accurate to at least 5%" (Methods)
   - assumption: V883 Ori Gaia parallax unreliable, so cluster distance adopted  
  > "the Gaia DR2 catalog flags the astrometric solution of V883 Ori as unreliable" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit COM column densities in spectra**: Extract spectra in 0.6" circular aperture, shift to source velocity, fit LTE model with XCLASS/MAGIX  
  > "all lines were extracted with the circular aperture of 0.6$^{\prime \prime}$" (Methods)
   - software: XCLASS, MAGIX, CDMS, JPL
   - parameter: FWHM fixed at 2 km/s, Tex = 120 K, emission size 0.6"  
  > "All lines are assumed to be Gaussian profiles with a FWHM fixed at 2 km s$^{-1}$" (Methods); "The excitation temperature of 120 K is adopted from the disk model below" (Methods)
   - assumption: LTE; CH3OH column = 13CH3OH x 60  
  > "we assume that the true column density of CH$_3$OH is the column density of $^{13}$CH$_3$OH multiplied by the elemental abundance of $^{12}$C/$^{13}$C$=60$" (Methods)
   - fitting: MAGIX optimisation; errors include 10% calibration and fit error  
  > "The error of the column density is calculated by taking absolute calibration uncertainty and fitting error into consideration." (Methods)
   - validation: Compared with rotation diagram of 13CH3OH (factor 7.6 difference explained by continuum opacity)  
  > "The derived column density of $^{13}$CH$_3$OH is larger than that from the excitation diagram (Supplementary Figure 1) by a factor of 7.6." (Methods)
4. **Derive disk temperature and density structure (Models A and B)**: Solve dust continuum radiative transfer on Band 6 high-res image for N_H2(r) and Tmid(r); Model B adds isothermal accretion-heated midplane inside snow line  
  > "To find $N_{\rm H_2}(r)$ and $T_{\rm mid}(r)$, we solve a dust continuum radiative transfer for the high resolution ALMA continuum image at Band 6" (Methods)
   - parameter: Tmid(r>0.1")=100 K x sqrt(0.1"/r); gamma=1.5; H/r=0.1; kappa 2.2 cm2/g at 1.3 mm  
  > "Here, we adopt $\gamma = 1.5$, a typical power index of the surface density profile in the disk" (Methods)
   - assumption: gas-to-dust ratio 100; Tatm/Tmid = 2; beta = 1; gas and dust temperatures equal  
  > "We assume that the gas to dust mass ratio is constant as 100 over the entire disk." (Methods)
   - fitting: _not stated_
   - validation: _not stated_
5. **Model 13CH3OH line emission and compare with high-res radial profile**: LTE line radiative transfer with sublimation at 80 K, smoothed to 0.11" resolution; midplane contribution via zero-abundance in |z|<=H  
  > "The sublimation temperature of $^{13}$CH$_3$OH, which fits the radial intensity profile, was 80 K" (Methods)
   - parameter: X_mol = 4e-9 above 80 K; FWHM 2 km/s  
  > "We adopted $\Delta V=2$ km s$^{-1}$, which is the average value over all lines, and $X_{\rm mol}=4\times 10^{-9}$" (Methods)
   - fitting: X_mol and sublimation temperature tuned by hand to match peak and radial profile  
  > "$X_{\rm mol}=4\times 10^{-9}$, which reproduces the observed peak intensity" (Methods)
   - validation: Compared with observed radial profile; Models A and B cannot be discriminated  
  > "Observations with higher spatial resolution and better sensitivity are needed to discriminate between these two models." (main text)

## Software

- **CASA** 4.7.2 and 5.1.1: data reduction  
  > "We carried out the standard data reduction using CASA 4.7.2 (for Cycle 4) and 5.1.1 (for Cycle 5)" (Methods)
- **XCLASS** : LTE spectral line fitting  
  > "fit the spectra using the eXtended CASA Line Analysis Software Suite (XCLASS)" (Methods)
- **MAGIX** : optimizing the XCLASS fit  
  > "we used MAGIX (Modeling and Analysis Generic Interface for eXternal numerical codes)(cite: Moller2013) to optimize the fit" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excitation temperature 13CH3OH | 91.5 | 3.5 | K | 3 | We find excitation temperatures for $^{13}$CH$_3$OH of 91.5 $\pm$ 3.5 K |
| Excitation temperature CH3OCHO | 103.3 | 34.9 | K | 3 | for CH$_3$OCHO of 103.3 $\pm$ 34.9 K |
| 13CH3OH column density | 5.26e16 | +0.53/-0.55e16 | cm-2 | 3 | $^{13}$CH$_{3}$OH & 5.26$_{-0.55}^{+0.53}$ $\times$ 10$^{16}$ |
| CH3OCHO column density | 2.37e17 | +/-0.24e17 | cm-2 | 3 | CH$_{3}$OCHO & 2.37$_{-0.24}^{+0.24}$ $\times$ 10$^{17}$ |
| CH3COCH3 column density | 4.32e16 | +0.45/-0.46e16 | cm-2 | 3 | Acetone & CH$_{3}$COCH$_{3}$ & 4.32 $_{-0.46}^{+0.45}$ $\times$ 10$^{16}$ |
| CH3CN/CH3OH ratio | 7.76e-4 | not stated | dimensionless | 3 | 7.76$\times$ 10$^{-4}$ |
| CH3OH abundance w.r.t. H2 | 2e-7 | not stated | dimensionless | 3 | is then $2\times 10^{-7}$, which is in reasonable agreement with the recent study |
| Distance | 388 pc (scatter 16 pc) | 16 pc std | pc | 2 | This set of stars has a distance of $388$ pc and a standard deviation of 16 pc |
| Midplane water snow line radius | 39 | not stated | AU | 2 | the midplane snow line is located at 39 AU rather than 42 AU |
| 13CH3OH sublimation temperature fit | 80 | not stated | K | 5 | was 80 K, as marked with the white dashed line in Figure 4(d) |
| D/H and 13C/12C ratios of CH3OH | 0.16 and 0.13 | not stated | dimensionless | 3 | The D/H and $^{13}$C/$^{12}$C ratios of CH$_3$OH are 0.16 and 0.13 |

## Qualitative findings

- COM emission forms a ring around the water snow line, peaking at 0.1-0.2" and decreasing inside it  
  > "The $^{13}$CH$_3$OH emission arises only between 0.1$\mbox{$^{\prime \prime}$}$-0.2$^{\prime \prime}$" (main text)
- CH3CHO, CH3OCHO and CH3COCH3 robustly detected for the first time in protoplanetary disks  
  > "which are robustly detected for the first time in protoplanetary disks (Figure 1)" (main text)

## Claim tuples

- H: The outburst sublimates COMs so that their gas-phase abundances trace the ice composition | E: Band 7 spectra at 0.2" resolution and fitting with XCLASS | R: Abundances 1e3-1e5 times higher than in non-bursting disk gas | F: Observations probe thermal sublimation of COMs | **supported**
- H: COM ratios in V883 Ori resemble hot corinos and comets | E: Compared column density ratios to CH3OH with IRAS 16293B and comet 67P | R: CH3COCH3, CH3CHO, CH3OCHO higher than IRAS 16293B by 4-16x; CH3CN lower | F: Reasonable agreement with comets except CH3CN; chemistry continues in disk | **partially**
- H: Heating model (irradiation only vs plus accretion) explains the radial profile | E: Models A and B compared with high-res 13CH3OH image | R: Model A reproduces the decrease inside the snow line; B declines more steeply | F: Current data cannot discriminate | **partially**

## Reasoning

- Why this data: Two resolutions: high for continuum and snow line, lower for COM emission  
  > "designed to measure COM emission" (main text)
- Why this method: _not stated_
- Alternative: Gaia DR2 parallax distance of 270 pc rejected as unreliable  
  > "Moreover, the Gaia DR2 catalog flags the astrometric solution of V883 Ori as unreliable" (Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): XCLASS fit is imperfect; CH3OH lines likely optically thick, requiring 2-D modelling postponed  
  > "The XCLASS fitting of the spectra in Figure 1 is not perfect" (Methods)
- Caveat (inferred, ours): Single-temperature, single-aperture LTE fits ignore spatial structure
- Caveat (inferred, ours): CH3OH column inferred from 13CH3OH with assumed 12C/13C = 60
- Caveat (inferred, ours): Ring emission could reflect continuum optical depth rather than abundance
- Caveat (inferred, ours): Models tuned by hand without uncertainties

## Reproducibility

- Data public (paper): Data downloadable from ALMA archive  
  > "which could be downloaded from the ALMA archive (https://almascience.nao.ac.jp/aq/) with project codes 2016.1.00728.S and 2017.1.01066.T" (Data availability)
- Products in archive: _not stated_
- Missing: tclean parameters and masks
- Missing: line-free channels
- Missing: Band 6 continuum image details
- Missing: XCLASS fitting setup details
- Data volume (inferred): ~100-300 GB raw for two short executions
- Score (inferred): 3/5, Public data and many parameters given, but imaging details and model fitting are only loosely specified.
- Rediscovery candidate: yes, Public data and a described XCLASS fit with numeric column densities, though imaging details are missing.

## Links

- Method: (cite: Moller2017) (XCLASS)
- Method: (cite: Moller2013) (MAGIX)
- Companion: (cite: Cieza2016) (discovery of the water snow line in V883 Ori with ALMA)
- Companion: (cite: vantHoff2018) (independent detection of CH3CHO and CH3OCHO in V883 Ori)

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 55,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
