# ALMA Observation of 158 μm [C II] Line and Dust Continuum of a z = 7 Normally Star-forming Galaxy in the Epoch of Reionization

`2014ApJ...792...34O` | The Astrophysical Journal 2014 | first author: Ota, Kazuaki | arXiv: 1405.5387 | DOI: 10.1088/0004-637X/792/1/34

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the [CII] line and FIR dust continuum properties (dust mass, IR luminosity, obscured SFR) of a normal z=6.96 LAE, IOK-1, and how does it compare with other galaxy populations?  
  > "Motivated by this, we conducted a [CII] line and FIR continuum observation of such a galaxy with ALMA." (1 Introduction)
- Target **IOK-1 (z=6.96 LAE)**: coordinates _not stated_; z/distance z=6.96 (from Lyα)  
  > "We observed IOK-1 by targeting its [CII] line redshifted to $z=6.96$ measured from Ly$\alpha$ emission" (2 Observation); distance from Lyα redshift (Iye06; Ota08)  
  > "We observed IOK-1 by targeting its [CII] line redshifted to $z=6.96$ measured from Ly$\alpha$ emission" (2 Observation)
- Target **Himiko (z=6.595 LAE, public ALMA data re-analysed)**: coordinates _not stated_; z/distance z=6.595  
  > "we have re-calibrated, flagged, and imaged the public Himiko ALMA Cycle 0 data." (3.1 FIR Continuum Properties); distance from Ouchi13  
  > "we have re-calibrated, flagged, and imaged the public Himiko ALMA Cycle 0 data." (3.1 FIR Continuum Properties)

## Data provenance

- ALMA projects: 2011.0.00767.S, 2011.0.00115.S
- bands: Band 6 (1.26 mm, 238.76 GHz observed)  
  > "(1.26 mm, 238.76 GHz in the observer’s frame or 157.74 $\mu$m, 1900.54 GHz at rest frame)" (2 Observation)
- frequencies and spectral setup: Four 2 GHz SPWs (1.875 GHz usable), TDM, centered 223.76, 225.76, 238.76, 240.76 GHz; 15.6 MHz channels = 40 km/s  
  > "with central frequencies of 223.76, 225.76, 238.76 and 240.76 GHz." (2 Observation); "The channel spacing of the TDM mode is 15.6 MHz, and this gives a spectral resolution of 40 km s$^{-1}$." (2 Observation)
- continuum bandwidth: _not stated_
- arrays: Cycle 0 Extended Array, 19–24 12-m antennas  
  > "We used the ALMA band 6 with the Extended Array consisting of 19–24 12-m diameter antennas" (2 Observation)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.1" x 0.75" (natural); 1.5" x 1.2" with 100 kλ taper  
  > "The resolutions (synthesized beam sizes) of [CII] line and FIR continuum images presented here are $1.1\ensuremath{''} \times 0.75\ensuremath{''}$." (2 Observation)
- max recoverable scale: _not stated_
- sensitivity: 215 µJy/beam per 40 km/s channel; 18 µJy/beam continuum (7.5 GHz) at native resolution; 240 and 21 µJy/beam at 1.5"x1.2"  
  > "$\sigma_{\rm line} =$ 215 $\mu$Jy beam$^{-1}$ per TDM channel (40 km s$^{-1}$) and $\sigma_{\rm cont} =$ 18 $\mu$Jy beam$^{-1}$ for 7.5 GHz bandwidth" (2 Observation)
- time on source: 2.7 hours  
  > "We obtained 2.7 hours of on-source integration." (2 Observation)
- observing dates: 15 June, 15 and 27 July, 29 November 2012  
  > "on 15 June, 15 and 27 July and 29 November 2012 during the Cycle 0 period." (2 Observation)
- pi or archival as stated: _not stated_
- Line: [CII] 2P3/2 -> 2P1/2 (1900.54 GHz)
- Other facility **Subaru Suprime-Cam**: Optical BVRi'z'y photometry for SED; NB973 Lyα image  
  > "Subaru Telescope Suprime-Cam $BVRi'z'y$ bands (cite: Ota08; Ota10b; Jiang13)" (3.1.2 Spectral Energy Distribution)
- Other facility **HST WFC3**: F110W, F125W, F160W photometry  
  > "F110W, F125W and F160W bands (cite: Cai11; Jiang13)" (3.1.2 Spectral Energy Distribution)
- Other facility **Spitzer IRAC**: 3.6–8.0 µm photometry  
  > "IRAC) 3.6, 4.5, 5.8 and 8.0 $\mu$m bands (cite: Ota10b)" (3.1.2 Spectral Energy Distribution)
- Other facility **Herschel SPIRE**: 250/350/500 µm non-detections  
  > "IOK-1 is not detected in any of the SPIRE bands" (3.1.2 Spectral Energy Distribution)
- External data: Local galaxy template SEDs (Arp 220, M82, M51, NGC 6946)  
  > "Arp 220, M82, M51, NGC 6946 (the left panel in Figure [2](#SED_IOK-1)) taken from (cite: Silva98)" (3.1.2 Spectral Energy Distribution) [from (cite: Silva98)]
- External data: Dwarf/irregular templates and dust temperature/beta (average 27.6 K, beta=1.5)  
  > "$T_{\rm dust}^{z=0}=27.6$ K and $\beta=1.5$, the average values of 17 local dwarf and irregular galaxies" (3.1.3 Dust Mass, IR Luminosity and Dust-obscured SFR) [from (cite: Skibba11), (cite: Dale07)]
- External data: UV-derived SFR of IOK-1 = 23.9 Msun/yr  
  > "(cite: Jiang13) estimated the SFR of IOK-1 to be SFR$_{\rm UV} \sim 23.9$ $M_{\odot}$yr$^{-1}$" (3.1.3 Dust Mass, IR Luminosity and Dust-obscured SFR) [from (cite: Jiang13)]

## Processing

### Calibration

- pipeline or manual: CASA data reduction; details not given  
  > "We carried out data reduction with the Common Astronomy Software Applications (CASA)." (2 Observation)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C279 for one execution block, Titan for the other three; J1310+323 phase, 3C279 bandpass  
  > "The flux density was scaled with the observation data of 3C279 (J1256-057) for one of the four execution blocks and Titan for the rest of three execution blocks." (2 Observation)
- flux scale uncertainty: ~10%  
  > "The typical flux uncertainties in the millimeter regime are $\sim 10$%." (2 Observation)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using ‘natural’ weighting" (2 Observation)
- uv taper: 100 kλ taper giving 1.5"x1.2" beam  
  > "through tapering with a 100 k$\lambda$ taper" (3.1 FIR Continuum Properties)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 21 µJy/beam continuum; 240 µJy/beam per 40 km/s channel at 1.5"x1.2"  
  > "As the rms of this map is $\sigma_{\rm cont}=21$ $\mu$Jy beam$^{-1}$" (3.1 FIR Continuum Properties)

### Inherited from earlier work

- CMB correction applied following da Cunha et al. formalism, with M_nu computed per González-López prescription  
  > "but following the prescription given by (cite: Gonzalez-Lopez14) to calculate the factor $M_{\nu}$ as follows." (3.1.2 Spectral Energy Distribution) [from (cite: daCunha13); (cite: Gonzalez-Lopez14)]
- Dust mass absorption coefficient kappa=0.77 (850um/lambda)^beta cm2/g  
  > "from Dunne et al. (2000) with the rest frame wavelength of $\lambda_{\rm rest}=158$ $\mu$m." (3.1.3 Dust Mass, IR Luminosity and Dust-obscured SFR) [from Dunne et al. (2000)]
- Line luminosity formula  
  > "$L_{\rm line}=1.04 \times 10^{-3} F_{\rm line}\nu_{\rm rest}(1+z)^{-1}D_{\rm L}^2$" (Table 1) [from (cite: Walter12b)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual scripts were used
- Flagging details and bandpass/phase solution intervals
- Which execution blocks of each project were combined
- Clean parameters (cell, image size, masks, iterations, continuum line-free channels)
- Pixel-based rms measurement regions and how the 3-sigma limits were derived
- Exact procedure for MBB scaling to the SED peak for template galaxies
- Himiko data reduction details (project code, calibration, flagging)

## Analysis recipe

1. **Calibrate and image continuum and [CII] cubes**: CASA reduction, natural weighting, 100 kλ taper to 1.5"x1.2"  
  > "Finally, we imaged the [CII] line and FIR continuum, using ‘natural’ weighting" (2 Observation)
   - software: CASA
   - parameter: 40 km/s channels; 7.5 GHz continuum bandwidth  
  > "for 7.5 GHz bandwidth (4 SPWs $\times$ 1.875 GHz)" (2 Observation)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive 3-sigma continuum and [CII] limits**: Non-detection; 3 sigma upper limits from tapered map rms  
  > "the $3\sigma$ upper limit on 1.26 mm FIR continuum of IOK-1 is $F_{\nu/(1+z)}^{\rm obs} < 63$ $\mu$Jy." (3.1 FIR Continuum Properties)
   - software: CASA
   - assumption: [CII] line width of 40 km/s  
  > "We assumed a line width of $\Delta v = 40$ km s$^{-1}$." (3.2 [CII] Line Properties)
   - fitting: _not stated_
   - validation: Width consistent with ~50 km/s FWHM simulated by González-López/Vallini  
  > "our assumption of $\Delta v = 40$ km s$^{-1}$ for calculating the [CII] line luminosity upper limit is reasonable." (3.2 [CII] Line Properties)
3. **Compare SED with local galaxy templates incl. CMB effects**: Shift templates to z=6.96, normalise to F125W, apply CMB heating and background corrections (Eqs. 1-7)  
  > "normalize them to the rest frame UV continuum flux density redward of Ly$\alpha$ (the *HST*/F125W band flux)" (3.1.2 Spectral Energy Distribution)
   - assumption: Template T_dust and beta from literature (e.g. Arp 220 66.7 K, 1.83)  
  > "$T_{\rm dust}^{z=0}=66.7$ K and $\beta=1.83$ for Arp 220" (3.1.2 Spectral Energy Distribution)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive dust mass, L_FIR, L_IR, SFR_dust limits**: Scale MBB (T=27.6 K, beta=1.5) to CMB-corrected limit; integrate 42.5–122.5 µm and 8–1000 µm; Kennicutt98 SFR  
  > "SFR$_{\rm dust}= 1.73 \times 10^{-10} L_{\rm IR}$ $[L_{\odot}]$" (3.1.3 Dust Mass, IR Luminosity and Dust-obscured SFR)
   - assumption: Dwarf-galaxy T_dust=27.6 K, beta=1.5; Salpeter IMF; cosmology (0.3,0.7,0.7)  
  > "$(\Omega_m, \Omega_{\Lambda}, h)=(0.3, 0.7, 0.7)$" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Place IOK-1 and other LAEs in L_[CII]-SFR and L_[CII]/L_FIR-L_FIR diagrams**: Compare limits with literature relations (De Looze11) and populations  
  > "By using the local star-forming galaxy correlation derived by (cite: DeLooze11), the [CII] luminosity limit of IOK-1 converts to SFR of $\sim 2.5$ $M_{\odot}$yr$^{-1}$" (3.2.1 [CII] Line and SFRs of High Redshift LAEs)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA data reduction and imaging  
  > "We carried out data reduction with the Common Astronomy Software Applications (CASA)." (2 Observation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3σ continuum limit (1.26 mm) | <63 | not stated | µJy | 2 | $<63$ |
| 3σ [CII] flux density limit (40 km/s) | <720 | not stated | µJy | 2 | the $3\sigma$ upper limit on [CII] line flux density of IOK-1 is 720 $\mu$Jy beam$^{-1}$ over a channel width of 40 km s$^{-1}$ |
| L_[CII] | <3.4e7 | not stated | Lsun | 2 | $L_{\rm [CII]} < 3.4 \times 10^7 L_{\odot}$ |
| M_dust (CMB-corrected) | <6.4e7 | not stated | Msun | 4 | intrinsic dust mass $M_{\rm dust} < 6.4 \times 10^7 M_{\odot}$ |
| L_FIR (42.5–122.5 µm) | <3.7e10 | not stated | Lsun | 4 | $L_{\rm FIR} < 3.7\times 10^{10} L_{\odot}$ (42.5–122.5 $\mu$m) |
| L_IR (8–1000 µm) | <5.7e10 | not stated | Lsun | 4 | $L_{\rm IR} < 5.7 \times 10^{10} L_{\odot}$ (8–1000 $\mu$m) |
| SFR_dust | <10.0 | not stated | Msun/yr | 4 | SFR$_{\rm dust} < 10.0$ $M_{\odot}$yr$^{-1}$ |
| Obscured fraction of star formation | <29 | not stated | % | 4 | $f_{\rm obscured}=$ SFR$_{\rm dust}/$SFR$_{\rm total} < 29$% of star formation is obscured by dust in IOK-1. |
| CMB correction factor C_nu M_nu | 0.76 | not stated | dimensionless | 3 | a factor of $C_{\nu}M_{\nu}=0.76$ lower |
| Marginal [CII] peak redshift | 6.9585 | not stated | dimensionless | 2 | the redshift based on its peak is $z_{\rm [CII]}=6.9585$ |

## Qualitative findings

- IOK-1 SED resembles local dwarf/irregular galaxies, not highly dusty galaxies  
  > "suggests that IOK-1 is similar to local dwarf/irregular galaxies in SED shape rather than highly dusty/obscured galaxies" (abstract)

## Claim tuples

- H: Is IOK-1 a dusty/obscured system? | E: ALMA 1.26 mm continuum compared with templates including CMB effects | R: Undetected; 3σ <63 µJy | F: IOK-1 is similar to local dwarfs/irregulars; <29% of SF obscured | **supported**
- H: Does IOK-1 follow local [CII]–SFR relation? | E: Compare [CII] limit with SFR range | R: L_[CII] limit implies SFR~2.5 vs 23.9–33.8 | F: LAEs at reionization have lower gas/dust enrichment than local star-forming galaxies, or different PDR/ISM | **partially**

## Reasoning

- Why this data: IOK-1 chosen as a spectroscopically confirmed z~7 LAE with rich ancillary data  
  > "we have a wealth of ancillary data availaible for this galaxy" (1 Introduction)
- Why this method: _not stated_
- Alternative: 3σ feature at 238.805 GHz treated as non-detection because marginal  
  > "Hence, in this paper, we consider it a non-detection" (3.2 [CII] Line Properties)
- How they decided it was enough: _not stated_
- Limitation (authors): Single object; may not be representative of LAE population  
  > "results obtained from the analysis of them might not be representative" (4 Summary and Conclusion)
- Caveat (inferred, ours): Dust limits depend strongly on assumed T_dust and beta
- Caveat (inferred, ours): Marginal 3σ [CII] feature treated as non-detection; line width assumed 40 km/s
- Caveat (inferred, ours): Comparison samples use heterogeneous sensitivities and methods

## Reproducibility

- Data public (paper): Himiko data described as public Cycle 0 data; IOK-1 codes given in acknowledgments  
  > "we have re-calibrated, flagged, and imaged the public Himiko ALMA Cycle 0 data." (3.1 FIR Continuum Properties)
- Products in archive: _not stated_
- Missing: CASA version and scripts
- Missing: Imaging parameters
- Missing: Which project corresponds to Himiko
- Missing: Template SED fitting details
- Data volume (inferred): ~20-50 GB raw for four Cycle 0 execution blocks
- Score (inferred): 3/5, Public Cycle 0 data and analytic recipe with explicit numbers, but CASA reduction and imaging parameters are largely unstated.
- Rediscovery candidate: yes, Data public, results numeric limits derived from formulae; reasonably redoable.

## Links

- Method: (cite: daCunha13) (CMB effects on dust continuum)
- Method: (cite: Gonzalez-Lopez14) (CMB correction prescription for M_nu)
- Companion: (cite: Walter12b) (Previous PdBI limits on IOK-1)
- Companion: (cite: Ouchi13) (ALMA observation of Himiko)
- Related: Herschel-ATLAS
- Related: KINGFISH

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 44,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
