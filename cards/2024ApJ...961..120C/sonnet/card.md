# Brightest Cluster Galaxy Formation in the z = 4.3 Protocluster SPT 2349-56: Discovery of a Radio-loud Active Galactic Nucleus

`2024ApJ...961..120C` | The Astrophysical Journal 2024 | first author: Chapman, Scott C. | arXiv: 2301.01375 | DOI: 10.3847/1538-4357/ad0b77

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars, galaxy_clusters_and_sz
- Question: Do any of the ~30 submm galaxies in the z=4.3 protocluster SPT2349-56 host a radio-loud AGN, and what does it imply for feedback on the nascent ICM?  
  > "We have observed the $z\,{=}\,$4.3 protocluster SPT2349$-$56 with the Australia Telescope Compact Array (ATCA) with the aim of detecting radio-loud active galactic nuclei (AGN) amongst the ${\sim}\,$30 submillimeter (submm) galaxies (SMGs)" (abstract)
- Target **SPT2349-56**: coordinates _not stated_; z/distance z = 4.303 (6.88 kpc/arcsec at z=4.3)  
  > "A well characterized example of this is SPT2349$-$56, a protocluster system at $z\,{=}\,$4.303 (cite: Miller)." (1 Introduction); distance from Miller et al. 2018 (cite: Miller)  
  > "A well characterized example of this is SPT2349$-$56, a protocluster system at $z\,{=}\,$4.303 (cite: Miller)." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.01543.T, 2018.1.00058.S, 2021.1.01313.S
- bands: Band 4 (150 GHz), Band 6 (~230 GHz), Band 7 (345 GHz, previously published)  
  > "ALMA Band-4 imaging (150 GHz) was obtained under three different programs in Cycles 3, 6, and 8" (2.3 ALMA observations); "We also make use of previously-published Band 7 (345 GHz) ALMA Cycle 5 and 6 observations (cite: Hill20)." (2.3 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 4: C36-2/3 (Cycle 3), C43-6 (Cycle 6), C-6 (Cycle 8); Band 6: C-4  
  > "The array was in the C36-2/3 configuration with baselines ranging from 15 to 460 m" (2.3 ALMA observations); "used the C-4 array configuration with baselines of 15 to 784 m" (2.3 ALMA observations)
- baselines: _not stated_
- angular resolution: Band 4 natural-weighted beams 0.88", 0.28", 0.27"; Band 6 0.47"  
  > "giving a naturally-weighted synthesized beam size of 0.27$^{\prime\prime}$." (2.3 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 Mar 20; 2018 Oct 3; 2022 Jul 27; 2022 Sep 1  
  > "These observations, carried out on 2022, September 1, used the C-4 array configuration" (2.3 ALMA observations)
- pi or archival as stated: Programs led by Lacaille, Chapman, Canning; Band 7 data previously published (Hill20)  
  > "the Cycle 8 program (2021.1.01313.S; PI: R. Canning)" (2.3 ALMA observations)
- Line: CO 7-6 (806.652 GHz)
- Line: [C I] 2-1 (809.34 GHz)
- Line: para-H2O 2_11-2_02 (752.033 GHz)
- Line: CO 11-10 (1267.01 GHz)
- Line: CO 16-15 (1841.35 GHz)
- Other facility **ATCA**: Radio 2.2, 5.5, 9.0 GHz imaging; detection of 214 uJy source  
  > "SPT2349$-$56 was observed by the Australia Telescope Compact Array (ATCA) at 2.2, 5.5, and 9.0 GHz" (2.1 ATCA observations)
- Other facility **ASKAP (RACS)**: 888 MHz image, 4.6 sigma peak  
  > "The SPT2349$-$56 ATCA-detected source is not cataloged in the RACS, but we find a 4.6$\sigma$ peak approximately 5$^{\prime\prime}$ from the ATCA source" (2.2 ASKAP observations)
- External data: [C II] line fluxes, apertures, 350 GHz continuum, SFRs, S850, dust SED model for B, C, G  
  > "The same apertures used by (cite: Hill20) to extract \[C II\] line strengths and 350-GHz continuum flux densities were applied to sources B, C, and G" (2.3 ALMA observations) [from (cite: Hill20)]
- External data: [C II] half-light radii from Sersic fits, M200  
  > "we use the half-light radii from (cite: hill2022), estimated by fitting Sérsic profiles to the high-resolution ALMA \[C II\] moment 0 images" (3.3 [C II] kinematics) [from (cite: hill2022)]
- External data: H2O-SFR scaling relation  
  > "SFR\,[M_{\odot}\,yr^{-1}]} = (2.07 \pm 0.75)\,{\times}\,10^{-5} L_{\rm H_2O}" (3.3 Submm line properties) [from (cite: Jarugula2021)]
- External data: Radio-cavity power relation  
  > "\log P_{\rm cav} = (0.35 \pm0.07) \log L_{1.4} + (1.85 \pm0.10)" (4.1 Jet power) [from (cite: cavagnolo2010; osullivan2011; panessa2015)]
- External data: GOODS-N radio sample for comparison  
  > "the redshift versus radio power is shown using the 0.3 deg$^2$ GOODS-N VLA sample (cite: barger2017)" (3.2 Physical interpretation of ID1) [from (cite: barger2017)]

## Processing

### Calibration

- pipeline or manual: Standard observatory-supplied calibration script (ALMA); Miriad for ATCA  
  > "All the data were calibrated using the standard observatory-supplied calibration script." (2.3 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ATCA absolute calibration 5% at 2.2 and 5.5 GHz, 10% at 9.0 GHz  
  > "We estimate an absolute calibration uncertainty of $5\%$ at 2.2 and 5.5 GHz, and 10% at 9.0 GHz." (2.1 ATCA observations)
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "Imaging was done using the `CASA` task `tclean`, using Briggs weighting with a robust parameter of 0.5" (2.3 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 (ALMA); natural weighting (ATCA)  
  > "using Briggs weighting with a robust parameter of 0.5, and in all cases channel widths were averaged down to a common 15.625 MHz" (2.3 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: imcontsub after flagging line channels based on [C II] lines from Hill20  
  > "The continuum was subtracted using the task `imcontsub` after flagging all channels expected to contain line emission based on previously-detected \[C II\] lines given in (cite: Hill20)." (2.3 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 6 and 8 combined in uv; Cycle 3 imaged separately  
  > "The Cycle 6 and 8 observations covering the CO(7–6), \[C I\](2–1), and H$_2$O lines were combined in $uv$ space and then imaged together, while the Cycle 3 observation was imaged separately." (2.3 ALMA observations)
- smoothing: Cycle 6+8 cubes convolved to Cycle 3 resolution (~0.88")  
  > "The higher-resolution Cycle 6 and 8 data cubes were then convolved to match the resolution of the Cycle 3 data (about 0.88$^{\prime\prime}$)." (2.3 ALMA observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Apertures, [C II] line templates, continuum fluxes, dust SED model from Hill20  
  > "The same apertures used by (cite: Hill20) to extract \[C II\] line strengths and 350-GHz continuum flux densities were applied to sources B, C, and G" (2.3 ALMA observations) [from (cite: Hill20)]
- Cycle 5+6 uv-combined [C II] cubes  
  > "we use $uv$-combined Cycle 5 and 6 data cubes (described in (cite: Hill20)) to calculate the moment 2 maps" (3.3 [C II] kinematics) [from (cite: Hill20)]
- Virial dynamical mass relation  
  > "The dynamical masses were derived previously (cite: Rotermund21) from the unresolved velocity dispersions" (3.3 [C II] kinematics) [from (cite: Rotermund21)]
- Binding energy method  
  > "Following (cite: giodini2010), the binding energy is computed as" (4.1 Binding energy of the halo gas) [from (cite: giodini2010)]

### Not stated but needed to reproduce (our reading)

- ATCA Miriad flagging, calibrators, imaging parameters (cell, size, deconvolution)
- Line-free channel ranges used for continuum subtraction
- ALMA CASA version
- ATCA stacking procedure details
- Aperture definitions for B, C, G (in Hill20)
- Prior ranges and likelihood in emcee spectral-index fit
- Moment-map masking details beyond 4 sigma threshold and channel selection

## Analysis recipe

1. **Reduce and image ATCA and ASKAP data, detect radio sources**: Miriad calibration, natural-weighted inversion at 2.2/5.5/9 GHz; RACS 888 MHz cutout; source search around members and out to 1 Mpc  
  > "The data were edited, calibrated, and imaged using the `Miriad` package." (2.1 ATCA observations)
   - software: Miriad
   - parameter: ATCA RMS 27, 40, 53 uJy/beam; ASKAP RMS 189 uJy  
  > "RMS noise values of 27, 40, and 53 $\mu$Jy beam$^{-1}$, respectively." (2.1 ATCA observations)
   - fitting: _not stated_
   - validation: Compared ATCA/ASKAP astrometry for sources within 13 arcmin  
  > "We measured peak fluxes in both images for all sources within a 13$^{\prime}$ radius of SPT2349$-$56, measured their centroids, and calculated radial offsets for each." (Appendix A)
2. **Radio stacking of members**: Stack on ten brightest SMGs (excluding B,C,G) and on all 40 members  
  > "A radio stacking analysis on these remaining ten brightest SMGs finds (11.0$\pm$10.0)$\,\mu$Jy" (3.1)
   - assumption: FIR-radio correlation gives S2.2 ≈ 12 uJy for S850 = 5 mJy at z=4.3  
  > "would imply $S_{2.2}\,{\approx}\,12\,\mu$Jy for a $S_{850}\,{=}\,5$ mJy source at $z\,{=}\,$4.3." (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Radio spectral index and luminosity**: Index from ASKAP detection plus ATCA 2.2 GHz and 5.5/9 GHz non-detections; error propagation; emcee MCMC linear fit; K-correct to rest 1.4 GHz  
  > "The data was fit according to a linear function using a Markov Chain Monte Carlo algorithm (MCMC) implemented by the `emcee` package (cite: foreman2013)." (Appendix C)
   - software: emcee
   - assumption: S_nu ∝ nu^alpha; alpha=-0.8 for GOODS-N and for single-frequency lensed SMGs; H0=70, OmegaL=0.7, Om=0.3  
  > "This equation assumes $S_\nu\,{\propto}\,\nu^{\alpha}$, and we adopt a radio spectral index of $\alpha\,{=}\,-$0.8 (cite: ibar2010)" (3.2)
   - fitting: emcee MCMC linear fit; priors not stated  
  > "The data was fit according to a linear function using a Markov Chain Monte Carlo algorithm (MCMC) implemented by the `emcee` package" (Appendix C)
   - validation: Compared with FIR-radio correlation, GOODS-N and ALESS samples  
  > "Figure [3](#fig:distribution) also directly assesses the departure of SPT2349$-$56 from the radio-FIR correlation by plotting the luminosity ratio of 1.4 GHz to 350 GHz versus redshift" (Physical interpretation of ID1)
4. **ALMA line and continuum measurements for B, C, G**: Extract spectra with Hill20 apertures; integrate lines between ±2 sigma using [C II] profile as template; deblend CO(7-6)/[C I] and CO(16-15)/OH with Gaussian fits  
  > "we simultaneously fit single Gaussian profiles at the locations of the two lines, then subtract the best-fit \[C I\](2–1) model from the spectrum" (Appendix B)
   - software: CASA
   - parameter: Channels averaged to 15.625 MHz; continuum from line-free channels at 147 and 231 GHz  
  > "meaning they are at observed frequencies of 147 and 231 GHz, respectively." (Appendix B)
   - fitting: Gaussians; OH doublet amplitudes equal and width fixed to [C II]  
  > "we fix the width of each doublet component to be equal to the width of the \[C II\] line" (Appendix B)
   - validation: _not stated_
5. **[C II] kinematics and dynamical masses**: CASA immoments moment 0/1/2 maps; peak-to-peak velocity and central dispersion; disk and virial dynamical mass  
  > "We use the `CASA` task `immoments`, focusing on channels between $\pm3\sigma$ of the best-fit \[C II\] line, and masking pixels ${<}\,4$ times the RMS per channel." (3.3 [C II] kinematics)
   - software: CASA
   - assumption: <sin i> = pi/4 ≈ 0.79  
  > "We adopt a mean inclination suitable for a collection of randomly oriented disks of $\langle \sin(i) \rangle\,{=}\,\pi\,/\,4\,{\simeq}\,0.79$" (3.3 [C II] kinematics)
   - fitting: _not stated_
   - validation: Varied PA by ±10 deg and midpoint by 5 pixels: ±50 km/s in Vp-p, ±10 km/s in dispersion  
  > "results in a peak-to-peak velocity change of $\pm$50 km s$^{-1}$ and a central velocity dispersion change of $\pm$10 km s$^{-1}$" (3.3 [C II] kinematics)
6. **Test AGN indicators in submm lines (H2O, CO SLED, OH EW)**: H2O line vs S850 and SFR relation; CO SLED vs AGN/starburst templates; OH 163um equivalent width vs local galaxies  
  > "SLEDs are shown in Fig. [5](#fig:sled) from the available $J\,{=}$2, 4, 7, 11, and 16 transitions, and compared to AGN and starburst templates." (3.3 Submm line properties)
   - assumption: Dust T=40 K at z=4.3 gives S850 = 1 mJy ↔ 115 Msun/yr  
  > "a dust temperature of 40 K at a redshift of 4.3 means that $S_{850}\,{=}\,1$ mJy corresponds to 115 M$_{\odot}$ yr$^{-1}$" (3.3 Submm line properties)
   - fitting: _not stated_
   - validation: _not stated_
7. **Jet power, energy injection and halo binding energy**: P_cav from L1.4 relation; SN energy injection with eta=1, v=500 km/s; NFW binding energy with c from Maccio07, fgas=10%; MCMC for uncertainty  
  > "We adopt a typical 500  kms$^{-1}$ wind speed for the SN-driven outflows in each SPT2349$-$56 galaxy." (4.1)
   - parameter: tau = 100 Myr; M200 = 9e12 Msun; c = 7.9; R500 = 80 kpc  
  > "we find $c\,{=}\,7.9$, corresponding to $r_s\,{=}\,15$ kpc." (4.1 Binding energy of the halo gas)
   - assumption: Halo gas mass = 10% of halo mass  
  > "we will assume for SPT2349$-$56 a gas mass of 10% of the halo mass, or $9\,{\times}\,10^{11}$ M$_\odot$" (4.1 Binding energy of the halo gas)
   - fitting: MCMC propagating M200 and M200-c uncertainty; details not stated  
  > "where the uncertainty has been propagated from $M_{200}$ and the uncertainty in the $M_{200}$-$c$ scaling relation using a Markov chain Monte Carlo (MCMC) approach." (Binding energy of the halo gas)
   - validation: _not stated_

## Software

- **Miriad** : ATCA calibration and imaging  
  > "The data were edited, calibrated, and imaged using the `Miriad` package." (2.1 ATCA observations)
- **CASA** : tclean imaging, imcontsub, immoments  
  > "Imaging was done using the `CASA` task `tclean`" (2.3 ALMA observations)
- **emcee** : MCMC fit of radio spectral indices  
  > "implemented by the `emcee` package (cite: foreman2013)" (Appendix C)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ATCA 2.2 GHz flux density of central source | 214 | 8 sigma detection | uJy | 1 | There is one strong radio detection at 2.2 GHz ($S_{2.2}\,{=}\,214\,\mu$Jy) found near the SPT2349$-$56 core with ATCA (detected at 8$\sigma$) |
| Radio spectral index | -1.58 | 0.28 | dimensionless | 3 | The radio source ID1 has a steep spectrum with an index of $\alpha\,{=}\,-1.58\pm0.28$ |
| Rest-frame 1.4 GHz luminosity | 2.4e26 | 0.3e26 | W/Hz | 3 | L$_{1.4,\,{\rm rest}}\,{=}\,(2.4\pm$0.3)$\,{\times}\,10^{26}$ W Hz$^{-1}$ |
| Stack of ten brightest SMGs at 2.2 GHz | 11.0 | 10.0 | uJy | 2 | finds (11.0$\pm$10.0)$\,\mu$Jy |
| Stack of all 40 members | -5.0 | 5.8 | uJy | 2 | Stacking on all 40 known cluster members yields $-$5.0$\pm$5.8$\,\mu$Jy. |
| Cavity/jet power | 3.3e38 | 0.7e38 | W | 7 | yielding $P_{\rm cav}$ ${=}$ $(3.3\pm0.7)\times10^{38}$ W |
| SN kinetic energy injection rate | 3.3e38 | 1.1e38 | W | 7 | $\dot{E}_{\mathrm{kin}}\,{=}\,(3.3\pm1.1)\,{\times}\,10^{38}$ W |
| Mechanical energy over 100 Myr | 1.0e54 | 0.2e54 | J | 7 | $E_{\rm mech}\,{=}\,P_{\rm cav}\,{\times}\,\tau\,{=}\,(1.0\pm0.2)\,{\times}\,10^{54}$ J |
| Halo gas binding energy | 1.5e54 | +0.7/-1.4e54 | J | 7 | $E_\mathrm{binding}\,{=}\,(1.5_{-1.4}^{+0.7})\,{\times}\,10^{54}$ J |
| EW(OH 163um) of B and C | 0.076 (B), 0.095 (C) | not stated | um | 6 | The EW(163$\mu$m)$=$0.076$\mu$m and 0.095$\mu$m measured for B and C respectively are amongst the highest found locally. |
| Predicted L_X (2-10 keV) from radio | 1e38 | not stated | W | 7 | corresponds to $L_{X}\,{=}\,10^{38}$ W |

## Qualitative findings

- No other AGN signatures in CO SLEDs, [C II]/FIR, or optical spectra; B and C OH EW more Seyfert-like  
  > "None of the SMGs in SPT2349$-$56 show signs of AGN in any other diagnostics available to us" (abstract)

## Claim tuples

- H: Does SPT2349-56 host a radio-loud AGN? | E: ATCA 2.2/5.5/9 GHz plus ASKAP 888 MHz, compared to FIR-radio correlation | R: L1.4,rest = 2.4e26 W/Hz, ~100x above star-formation expectation; alpha=-1.58 | F: A radio-loud AGN in the forming BCG | **supported**
- H: Do other members host radio AGN? | E: Source search and stacking | R: Stacks of 10 brightest and all members are non-detections | F: Radio-loud AGN fraction among SMGs <10%, likely 3% | **supported**
- H: Can the AGN significantly feed back on the nascent ICM? | E: Estimate P_cav and compare with binding energy and SN input | R: E_mech ~1e54 J vs E_binding 1.5e54 J | F: Radio-loud AGN may provide strong feedback | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Radio continuum is an extinction-free AGN probe  
  > "Radio emission provides an extinction-free probe of AGN" (3.2)
- Alternative: Star-formation synchrotron rejected because spectrum too steep (alpha=-0.79 for SMGs)  
  > "The spectrum is too steep to be consistent with synchrotron radiation due to shock acceleration of cosmic ray electrons from supernovae" (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Radio resolution cannot identify which of B, C, G hosts the AGN; spectral index from only two points plus limits  
  > "the radio observations do not have sufficient spatial resolution to uniquely identify one of the three galaxies as the AGN" (3.3 Concluding remarks)
- Limitation (authors): 5 arcsec ATCA-ASKAP offset unexplained  
  > "While it’s not clear why the sources are offset, it appears more likely to be instrumental than physical" (3.1)
- Caveat (inferred, ours): ASKAP 4.6 sigma detection and non-detections drive the spectral index; low significance
- Caveat (inferred, ours): Gas fraction of 10% and mass loading eta=1 are assumed
- Caveat (inferred, ours): Inconsistent quoted uncertainties (alpha ±0.28 vs ±0.31; L2.2 ±0.56 vs ±0.3)
- Caveat (inferred, ours): ALMA is a supporting dataset; main result is ATCA/ASKAP

## Reproducibility

- Data public (paper): ALMA programs cited by code; ATCA and RACS data cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01543.T, ADS/JAO.ALMA#2018.1.00058.S" (acknowledgements)
- Products in archive: _not stated_
- Missing: Miriad ATCA reduction details
- Missing: Aperture definitions from Hill20
- Missing: CASA version and line-free channels
- Data volume (inferred): ~100 GB for the ALMA data; ATCA/ASKAP small
- Score (inferred): 3/5, Radio recipe is simple and numeric but ATCA processing details, stacking and ALMA aperture definitions are in other papers or unstated.
- Rediscovery candidate: no, Key results come from ATCA/ASKAP data with sparse processing details; ALMA is supporting.

## Links

- Method: (cite: Hill20) (ALMA [C II]/continuum data, apertures and SED)
- Companion: (cite: Miller) (Discovery of the SPT2349-56 protocluster)
- Companion: (cite: Rotermund21) (Dynamical masses and stellar properties)
- Companion: (cite: hill2022) ([C II] sizes, M200, stellar masses)
- Related: RACS
- Related: SPT-SMG sample
- Related: GOODS-N
- Related: ALESS

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.1.00273.S"
 ],
 "codes_printed_but_missing": [
  "2021.1.01010.P"
 ],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 56,
  "rate": 0.622
 },
 "evidence_ok": true
}
```
