# Nuclear Spectral Energy Distributions of Luminous Infrared Galaxies

`2025ApJ...988..185G` | The Astrophysical Journal 2025 | first author: Gao, Tianmu | arXiv: 2504.16971 | DOI: 10.3847/1538-4357/add0b2

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How do nuclear (100-150 pc) SEDs, AGN fraction and X-ray properties of nearby (U)LIRGs vary with merger stage and infrared luminosity, and how do dual nuclei differ?  
  > "To address the questions of when and how AGN get triggered via the merger mechanism, we target local luminous and ultraluminous infrared galaxies" (Introduction)
- Target **23 GOALS (U)LIRGs hosting 28 nuclei (e.g., Arp 220, NGC 6240, IRAS 07251-0248, IRAS F12112+0305, IRAS F14348-1447)**: coordinates RA/Dec listed per galaxy in Table 1  
  > "Column 4: Luminosity distance in Mpc ($H_{0}=70\,\rm km\,s^{-1}\,Mpc^{-1}$)" (Table 1); z/distance D_L = 69.1-399.7 Mpc (Table 1)  
  > "Column 4: Luminosity distance in Mpc ($H_{0}=70\,\rm km\,s^{-1}\,Mpc^{-1}$)" (Table 1); distance from Table 1 luminosity distances, H0 = 70 km/s/Mpc  
  > "Column 4: Luminosity distance in Mpc ($H_{0}=70\,\rm km\,s^{-1}\,Mpc^{-1}$)" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00077.S, 2012.1.01022.S, 2013.1.01165.S, 2015.1.00102.S, 2015.1.00708.S, 2015.1.00804.S, 2015.1.01439.S, 2015.1.01448.S, 2016.1.00051.S, 2016.1.00140.S, 2016.1.00991.S, 2016.1.01385.S, 2017.1.00022.S, 2017.1.00255.S, 2017.1.00395.S, 2017.1.00759.S, 2017.1.01085.S, 2017.1.01235.S, 2018.1.00279.S, 2018.1.00486.S, 2018.1.00699.S, 2018.1.01123.S, 2018.1.01344.S, 2019.1.00027.S, 2019.1.00811.S
- bands: Mainly Band 7, 6, 5, 3; a few galaxies also Bands 10, 9, 8, 4  
  > "Our archival data set mainly consisted of ALMA cubes taken in Band 7 (275-373 GHz), Band 6 (211-275 GHz), Band 5 (163-211 GHz) and Band 3 (84-116 GHz)" (3.4 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: selected observations with angular scales of 0.5" or better  
  > "we selected those observations with angular scales of 0.5$''$ (matching that of *Chandra*) or better for our study" (3.4 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 to 2019  
  > "All of the ALMA data used in this project were taken between 2016 and 2019." (3.4 ALMA)
- pi or archival as stated: archival  
  > "using sub-arcsecond resolution archival data from ALMA, Keck, *HST*, and *Chandra*" (Introduction)
- Other facility **Chandra**: 0.5-10 keV nuclear X-ray photometry and spectra, 1" aperture  
  > "we choose to extract nuclear photometry from a $1^{\prime\prime}$-radius aperture" (3.1 Chandra)
- Other facility **HST**: UV to near-IR nuclear photometry (ACS, NICMOS, WFC3)  
  > "The mostly science-ready *HST* data we gathered from MAST comprise of $F435W$ and $F814W$ images taken with ACS" (3.2 HST)
- Other facility **Keck/NIRC2**: near-infrared AO imaging (J, H, Ks, Kp)  
  > "near-infrared *(J, H, K$_s$, and K$_p$)*, raw NIRC2 science and calibration frames for our galaxies" (3.3 Keck)
- Other facility **VLT, Gemini, Subaru, IRAS, Spitzer, JWST**: mid-infrared nuclear fluxes or upper limits  
  > "mid-infrared fluxes from *IRAS* and *Spitzer*/MIPS at 12, 24 and 25 $\rm\mu m$ (cite: 2003Sanders; 2012U) have been incorporated as upper limits in our analysis" (3.5 Miscellaneous Mid-infrared Data)
- External data: Intrinsic 2-10 keV X-ray luminosities from NuSTAR for some galaxies  
  > "we obtained the intrinsic 2$-$10 keV X-ray luminosity for some of our galaxies from (cite: 2021Ricci), using data from the *NuSTAR*." (3.1 Chandra) [from (cite: 2021Ricci)]
- External data: Mid-infrared N/Q band nuclear fluxes for eight galaxies  
  > "have archival mid-infrared N band ($\sim$11 $\rm \mu$m) and/or Q band ($\sim$18 $\rm \mu$m) imaging data from (cite: 2014Asmus)" (3.5 Miscellaneous Mid-infrared Data) [from (cite: 2014Asmus)]
- External data: JWST MIRI fluxes for II Zw 096  
  > "For II Zw 096, we have incorporated the flux measurements from *JWST* MIRI F560W, F770W, and F1500W provided by (cite: 2022Inami)." (3.5 Miscellaneous Mid-infrared Data) [from (cite: 2022Inami)]
- External data: Merger stage and nuclear separation  
  > "Column 5: Merger stage (cite: 2011Haan; 2013Kim); Column 6: Nuclear separation $d_\mathrm{nuc}$ in kpc (cite: 2013Kim)" (Table 1) [from (cite: 2011Haan; 2013Kim)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA beam-corrected continuum images used; no reprocessing described  
  > "we used the beam-corrected 880- and 1300-$\mu$m dust continuum images to locate the SMBHs in the galaxies" (3.4 ALMA)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Merger stage classification  
  > "The merger stage classification is adopted from (cite: 2011Haan) and (cite: 2013Kim)" (2 Sample) [from (cite: 2011Haan; 2013Kim)]
- Treatment of polar-dust E(B-V) values 0 and 0.8  
  > "we followed the treatment presented in (cite: 2021Paspaliaris), which modeled a similar sample of local (U)LIRGs and adopted 0 and 0.8 as the values for this parameter" (4.2 SED Modeling) [from (cite: 2021Paspaliaris)]
- Burst ages 1 and 5 Myr  
  > "We set the possible values for the age of the burst to 1.0 and 5.0 Myrs, as mentioned in (cite: 2013Inami)." (4.2 SED Modeling) [from (cite: 2013Inami)]

### Not stated but needed to reproduce (our reading)

- ALMA project-to-galaxy/band mapping and which products were used
- ALMA image processing details (CASA version, imaging parameters, beam sizes per image)
- ALMA flux calibration uncertainties and how photometric errors were set
- Which galaxies' aperture sizes were converted to upper limits for ALMA
- X-CIGALE fitting settings beyond the grid (error treatment, upper-limit handling, X-CIGALE version details)
- Exact definition of the AGN fraction bins and statistics used for median SEDs
- Software versions for photutils, X-CIGALE

## Analysis recipe

1. **locate nuclei with ALMA**: ALMA 880 and 1300 um continuum used as absolute nuclear coordinates for all wavelengths  
  > "the ALMA locations were taken as the absolute coordinates for the nuclei to be measured across all multiwavelengths" (3.4 ALMA)
   - fitting: _not stated_
   - validation: visual inspection of multiwavelength images  
  > "with visual inspection of all the multiwavelengh images for all the individual systems" (Archival Data, ALMA)
2. **aperture photometry**: Circular apertures of 100 pc (z<0.05) or 150 pc (z>0.05); ALMA beam FWHM used if aperture smaller than beam, giving upper limits  
  > "If the chosen aperture size was smaller than the beam size of ALMA, then we instead used its FWHM for the size of the aperture and therefore reported the resulting flux as an upper limit" (4.1 Aperture Photometry)
   - software: photutils, TinyTim
   - parameter: r = 0.106-0.284" (100 pc) and 0.102-0.133" (150 pc)  
  > "we adopted an aperture size of $r =0.106\ensuremath{''}-0.284\ensuremath{''}$, equivalent to a physical scale of 100 pc" (4.1 Aperture Photometry)
   - fitting: _not stated_
   - validation: _not stated_
3. **SED fitting**: X-CIGALE with BC03/Salpeter, delayed SFH plus burst, modified Calzetti attenuation, Dale2014 dust, SKIRTOR AGN, X-ray module  
  > "we generated SEDs with the nuclear photometry and modeled them using X-CIGALE (cite: 2022Yang)" (4.2 SED Modeling)
   - software: X-CIGALE
   - parameter: Parameter grid in Table 6 (e.g., AGN fraction 0-0.99, alpha_OX -1.9 to -1.1, polar E(B-V) 0 and 0.8)  
  > "Colour excess for the extinction in the polar direction (mag) | 0, 0.8" (Table 6)
   - assumption: Salpeter IMF  
  > "The stellar component is built based on the (cite: 2003Bruzual) population synthesis model with the (cite: 1955Salpeter) initial mass function (IMF)." (4.2 SED Modeling)
   - fitting: _not stated_
   - validation: Mock analysis appendix; refit of IRAS F05189-2524 without upper limits  
  > "their reliability is primarily limited by the lack of high-resolution mid- to far-infrared data, as indicated in Appendix [10](#sec:appendix_mock_analysis)" (Best-fitting Results)
4. **X-ray spectral fitting and X-ray vs IR comparison**: APEC plus power-law (zphabs, Gaussian Fe K) fits to Chandra nuclear spectra; compare L_SX, L_HX and hardness ratios with nuclear L_IR  
  > "the soft X-ray spectra were fitted using single temperature plasma model APEC (cite: 2001Smith), while the hard X-ray spectra were fitted with a power-law model." (3.1 Chandra)
   - software: CIAO, HEASOFT/XSPEC
   - parameter: kT fixed to 0.7 keV for poor data; NH free 10^22.5-10^25 cm^-2 or fixed 10^23 for ~10 counts  
  > "the neutral hydrogen column density of this redshifted absorption component was allowed to vary freely between $10^{22.5}<N_{\rm H}<10^{25}\,\rm cm^{-2}$" (3.1 Chandra)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **X-CIGALE** CIGALE v2022.1: SED modeling  
  > "The improvements in CIGALE v2022.1 are mainly related to the anisotropy of AGN X-ray emission" (4.2 SED Modeling)
- **photutils** : aperture photometry  
  > "We extracted photometry from the flux-calibrated, multiwavelength images using the Python `photutils` package (cite: 2020photutils)." (4.1 Aperture Photometry)
- **CIAO** 4.11: Chandra data reduction  
  > "The data reduction was performed using the *Chandra* data analysis package CIAO version 4.11" (3.1 Chandra)
- **HEASOFT** 6.25: X-ray spectral fitting  
  > "and HEASOFT version 6.25 (cite: 1996Xspec)" (3.1 Chandra)
- **DrizzlePac** 3.1.8: HST redrizzling  
  > "re-drizzled using DrizzlePac version 3.1.8" (3.2 HST)
- **KAI** : NIRC2 data reduction  
  > "Keck AO Imaging (KAI) data reduction pipeline (cite: 2022lu)" (3.3 Keck)
- **TinyTim** : HST PSF aperture corrections  
  > "we determined the appropriate aperture corrections using TinyTim-simulated PSFs (cite: 1993Krist)" (4.1 Aperture Photometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Aperture radius for IRAS 07251-0248 | 0.1 (164 pc) | not stated | arcsec | 2 | we elected to use an aperture size of $r = 0.1\ensuremath{''}$, equivalent to 164 pc for this galaxy |
| Maximum time to nuclear coalescence for four dual systems | ~340 | not stated | Myr | 0 | the maximum time for transitioning from their current state to final nuclei coalescence is $\sim$340 Myrs |
| Nuclear L_AGN IRAS 07251-0248W | 14.99 | 9.51 | 10^10 Lsun | 3 | IRAS 07251-0248W / $28.2\pm35.7$ / $1.52\pm0.82$ / $1.18\pm0.94$ / $0.35\pm0.34$ / $1.95\pm1.91$ / $14.99\pm9.51$ |

## Qualitative findings

- Nuclear SEDs of dual nuclei pairs are distinct.  
  > "The SEDs for these resolved pairs are distinct" (abstract)

## Claim tuples

- H: AGN contribution varies with merger stage | E: Median nuclear SEDs binned by interaction class | R: Low AGN contribution in early-stage mergers, enhanced in late and post-merger stages | F: AGN fraction enhanced in later stages | **partially**
- H: Nuclear X-ray properties differ from global | E: Compared nuclear L_SX, L_HX and HR with global values | R: Nuclear regions have higher hardness ratios than hosts | F: Hard X-ray emission is more nucleated | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of high-resolution mid- to far-infrared data limits reliability of derived properties; near-IR PSFs unresolved for some.  
  > "their reliability is primarily limited by the lack of high-resolution mid- to far-infrared data" (Table 7)
- Caveat (inferred, ours): Small, archival-selected sample
- Caveat (inferred, ours): Many mid/far-IR points are upper limits so AGN fractions are degenerate
- Caveat (inferred, ours): ALMA excess emission and low-frequency fit issues
- Caveat (inferred, ours): Stage 5-6 AGN trend not clearly significant

## Reproducibility

- Data public (paper): Archival data from ALMA, Chandra, MAST, KOA  
  > "The multiwavelength data have been from the *Chandra* Data Archive (CDA)" (3 Archival Data)
- Products in archive: _not stated_
- Missing: ALMA imaging details
- Missing: X-CIGALE error and upper-limit configuration
- Missing: Photometry error budget
- Data volume (inferred): Large (hundreds of GB to TB across 25 ALMA projects plus HST, Chandra, Keck)
- Score (inferred): 4/5, Public data and a full X-CIGALE grid are given, but ALMA processing and several fit settings are unstated.
- Rediscovery candidate: no, Multi-facility pipeline with incomplete ALMA recipe; results largely qualitative.

## Links

- Method: (cite: 2022Yang) (X-CIGALE SED fitting code)
- Companion: (cite: 2021Paspaliaris) (global CIGALE SED modeling of (U)LIRGs)
- Companion: (cite: 2023Yamada) (global X-ray to radio SED decomposition of GOALS (U)LIRGs)
- Related: GOALS

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 25,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 40,
  "rate": 0.506
 },
 "evidence_ok": true
}
```
