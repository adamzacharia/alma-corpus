# Measuring 60 pc-scale Star Formation Rate of the Nearby Seyfert Galaxy NGC 1068 with ALMA, HST, VLT/MUSE, and VLA

`2024ApJ...974..243N` | The Astrophysical Journal 2024 | first author: Nagashima, Yuzuki | arXiv: 2407.15931 | DOI: 10.3847/1538-4357/ad6312

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, agn_and_quasars
- Question: What is the 55 pc-scale star formation rate (SFR) and electron temperature of the NGC 1068 molecular gas disk when ALMA 100 GHz free-free continuum and HST Pa-alpha are cross-calibrated while correcting for extinction, AGN contamination and diffuse ionized gas (DIG)?  
  > "We present an SFR calibration for the entire molecular gas disk of the nearby Seyfert galaxy NGC 1068" (abstract); "Because the two tracers can be assumed to come from the same ionized gas ISM in galaxies, two SFR maps should agree with each other if all the other corrections and assumptions work" (3.4.1 Estimating electron temperature)
- Target **NGC 1068**: coordinates _not stated_; z/distance D_L = 13.97 Mpc, z = 0.0038 (z = 0.003793 in Section 3.2.4); 1.0 arcsec = 72 pc  
  > "$D_{\rm L}$ $=$ 13.97 Mpc, z $\simeq$ 0.0038; 1.0$''$ $=$ 72 pc; (cite: Anand2021)" (1 Introduction); distance from Anand2021  
  > "$D_{\rm L}$ $=$ 13.97 Mpc, z $\simeq$ 0.0038; 1.0$''$ $=$ 72 pc; (cite: Anand2021)" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00061.S, 2012.1.00657.S, 2013.1.00055.S, 2013.1.00060.S, 2013.1.00111.S, 2013.1.00188.S, 2013.1.00221.S, 2013.1.00279.S, 2015.1.00960.S, 2016.1.00023.S, 2016.1.00052.S, 2016.1.00232.S, 2017.1.01666.S, 2018.1.00037.S, 2018.1.01506.S, 2018.1.01684.S, 2019.1.00130.S, 2021.2.00049.S
- bands: Band 3 (84-116 GHz, ~3 mm; reference 99.7015 GHz) and Band 6 (reference 260.5180 GHz)  
  > "This results in extremely wide-band observations covering nearly the entire Band 3 coverage from 84 GHz to 116 GHz (i.e., $\lambda$ = 3 mm)." (2.1.1 Band 3 Continuum); "We set the reference frequency to 260.5180 GHz when imaging with the mtmfs mode (hereafter 261 GHz continuum)." (2.1.2 Band 6 Continuum)
- frequencies and spectral setup: Band 3 imaging spectral scans covering 84-116 GHz; Band 6 7-m spectral scan mostly covering 211-275 GHz  
  > "that mostly covers between 211 GHz and 275 GHz to recover extended structures possibly missed by the archival 12-m data" (2.1.2 Band 6 Continuum)
- continuum bandwidth: _not stated_
- arrays: 12-m array and 7-m array (Band 3); 12-m archival projects plus 7-m (Band 6)  
  > "we utilized ten projects publicly available in the ALMA archive that cover the Band 3 frequency coverage with the 12-m or 7-m array" (2.1.1 Band 3 Continuum); "We collected eight Band 6 projects that employed the 12-m array from the archive" (2.1.2 Band 6 Continuum)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Original synthesized beam 0.76 x 0.66 arcsec (99.7 GHz) and 0.44 x 0.42 arcsec (260.5 GHz); convolved to 0.8 arcsec (55 pc) round beam  
  > "0.76 $\times$ 0.66" (Table 1); "0.44 $\times$ 0.42" (Table 1); "we convolve all the ALMA and VLA maps to a round beam with 0.8$''$" (2.3 Hexagonal sampling)
- max recoverable scale: _not stated_
- sensitivity: RMS per pixel 0.01 mJy/beam and per hexagon 0.1 mJy/beam at 99.7 GHz; 0.07 and 0.6 mJy/beam at 260.5 GHz (text elsewhere also quotes 0.9 mJy/beam for the 100 GHz sensitivity)  
  > "the image RMS of our ALMA 100 GHz continuum map (0.1 mJy beam$^{-1}$)" (Appendix: Negligible contamination of DIG for free-free continuum); "which is well below the sensitivity (0.9 mJy beam$^{-1}$)" (3.3.3 Evaluating the effect of diffuse ionized gas on 100 GHz continuum)
- time on source: Band 3: 24.9 hours (12-m) and 26.3 hours (7-m) total integration  
  > "Total integration time with the 12-m array and the 7-m array are 24.9 hours and 26.3 hours, respectively." (2.1.1 Band 3 Continuum)
- observing dates: _not stated_
- pi or archival as stated: Own Band 3 12-m (2013.1.00279.S, PI Nakajima) and 7-m (2021.2.00049.S, PI Saito) scans plus publicly available archival projects in Band 3 and Band 6  
  > "To further gain sensitivity, we utilized ten projects publicly available in the ALMA archive" (2.1.1 Band 3 Continuum); "We collected eight Band 6 projects that employed the 12-m array from the archive" (2.1.2 Band 6 Continuum)
- Line: H I (Pa-alpha, HST, not ALMA) Pa-alpha (1.875 micron (18756 Angstrom per Table 2))
- Other facility **HST (NICMOS)**: Drizzled and processed Pa-alpha line map (provided by M. Sanchez-Garcia, private communication)  
  > "We use the drizzled and processed *HST* Pa$\alpha$ map which is provided by" (2.2.1 HST Data); "(private communication)" (2.2.1 HST Data)
- Other facility **VLT/MUSE**: Archival IFU data cube (program 094.B-0321(A)) for Halpha and [S II] lines; 2800 s integration; seeing ~0.8 arcsec  
  > "program ID: 094.B-0321 (A), PI: Marconi" (2.2.2 MUSE Data); "The total integration time of the data used is 2800 s." (2.2.2 MUSE Data)
- Other facility **VLA**: 14.9 GHz (Ku-band) radio continuum map, BnA configuration, 0.41 arcsec resolution, 0.157 mJy/beam sensitivity, used to mask the AGN radio jet  
  > "We downloaded a 14.9 GHz (Ku-band) radio continuum map taken by VLA from the NRAO Data Archive." (2.2.3 VLA Data); "The achieved spatial resolution is 0.41$''$ and the achieved sensitivity is 0.157 mJy beam$^{-1}$." (2.2.3 VLA Data)
- External data: Extinction (A_V) map and [S II]9069,9532/[S II]6717,6731 ratio map of NGC 1068 from the MAGNUM survey  
  > "as well as publicly available $\mbox{\rm [S II]}\lambda\lambda$9069,9532/$\mbox{\rm [S II]}\lambda\lambda$6717,6731 ratio map and dust extinction map (cite: Mingozzi19)" (2.2.2 MUSE Data) [from Mingozzi19]
- External data: Calibrated HST Pa-alpha map  
  > "The details of the data properties and data reduction can be found in (cite: Garcia-Burrillo14) and (cite: Sanchez-Garcia22)." (2.2.1 HST Data) [from Garcia-Burrillo14; Sanchez-Garcia22]
- External data: Luminosity distance 13.97 Mpc and redshift  
  > "z is the source redshift ($=$ 0.003793), and $D_{\rm L}$ is the source luminosity distance ($=$ 13.97 Mpc; (cite: Anand2021))" (3.2.4 Converting from Pa-alpha to SFR) [from Anand2021]
- External data: Pa-alpha emissivity list used for the epsilon(Te) relation  
  > "based on the list in (cite: StoreyandHummer95), we employ the following relation between $\epsilon$ and $T_{\rm e}$ for Pa$\alpha$" (3.2.4 Converting from Pa-alpha to SFR) [from StoreyandHummer95]
- External data: alpha_B(Te) interpolated relation  
  > "We use an interpolated relation between $\alpha_{\rm B}$ and $T_{\rm e}$ described in (cite: Michiyama20)" (3.2.4 Converting from Pa-alpha to SFR) [from Michiyama20]
- External data: SFR-to-ionizing-photon conversion coefficient (STARBURST99, Kroupa IMF)  
  > "were calculated using STARBURST99 (cite: Leitherer99)" (3.2.4 Converting from Pa-alpha to SFR) [from Leitherer99; Bendo16]
- External data: Minimum Halpha flux f0 for an H II region (3.25e-15 erg s-1 cm-1) used in the DIG correction  
  > "The minimum value of H$\alpha$ intensity ($f_0$) at which a H II region can exist in each pixel defined by (cite: Kaplan16)" (Appendix: DIG correction to the Pa-alpha) [from Kaplan16]
- External data: Calzetti extinction law used to rescale R_V from 3.1 to 4.05  
  > "which was made by assuming a (cite: Calzetti00) extinction law with $R_{V}$ $=$ 3.1" (3.2.2 Correcting for dust extinction) [from Calzetti00]
- External data: Spectral index of -0.8 for synchrotron emission  
  > "due to its relatively shallower spectral index of $-$0.8 (cite: Condon92; Gallimore04)" (3.2.1 Masking AGN radio jet) [from Condon92; Gallimore04]
- External data: Rayleigh-Jeans dust spectral index of 4 for the cold-dust extrapolation  
  > "This index is a typical value for the Rayleigh-Jeans tail of nearby starburst galaxies (cite: Murphy11; Saito16)." (3.3.1 Removing cold dust continuum) [from Murphy11; Saito16]
- External data: 8 micron based total SFR of 3.1 +/- 0.1 Msun/yr in the starburst ring (Salpeter IMF), used for comparison  
  > "they measured a total SFR of 3.1 $\pm$ 0.1 $M_{\odot}$ yr$^{-1}$ in the starburst ring of NGC 1068" (4.1 Reliability of this SFR prescription) [from Tsai12]
- External data: Salpeter-to-Kroupa conversion factor 1.6  
  > "we scale the SFR derived in (cite: Tsai12) by Salpeter-to-Kroupa conversion factor 1.6 (cite: Marchesini09)" (4.1 Reliability of this SFR prescription) [from Marchesini09]
- External data: Te measurements for NGC 253 (3900 +/- 300 K) and NGC 4945 (5400 +/- 600 K) used for comparison  
  > "$3900\pm300$$^b$" (Table 4); "$5400\pm600$$^c$" (Table 4) [from Bendo15 (NGC 253); Bendo16 (NGC 4945)]

## Processing

### Calibration

- pipeline or manual: Observatory-provided calibration pipeline  
  > "Following (cite: Saito22a) and (cite: Saito22b), we performed calibration with the observatory-provided calibration pipeline (cite: Hunter23)" (2.1.1 Band 3 Continuum)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Nominal ALMA Band 6 flux accuracy 10%  
  > "This factor is smaller than the nominal flux accuracy of the ALMA Band 6 data (10%)" (3.3.1 Removing cold dust continuum)
- self calibration: _not stated_

### Imaging

- task: CASA tclean, multi-term (multi-scale) multi-frequency synthesis (mtmfs); imaging through the PHANGS-ALMA imaging pipeline  
  > "We performed the continuum imaging with multi-term (multi-scale) multi-frequency synthesis (mtmfs; (cite: Rau11)) using `CASA tclean`." (2.1.1 Band 3 Continuum); "imaging with the `PHANGS-ALMA imaging pipeline` (cite: Leroy21a)" (2.1.1 Band 3 Continuum)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 55 pc (0.8 arcsec) hexagonal pixels after regridding  
  > "The size of each hexagon is set to be 0.8$''$ which minimizes the pixel-to-pixel correlation due to the beam oversampling when imaging." (2.3 Hexagonal sampling)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Cold dust at 100 GHz removed by extrapolating the 261 GHz map with spectral index 4 (not a line continuum subtraction)  
  > "with a fixed spectral index of 4 and subtract it from the 100 GHz map." (3.3.1 Removing cold dust continuum)
- line free channels: Channels contaminated by strong molecular lines (as reported in Saito22b and Nakajima23) removed before continuum imaging; Band 3 reference frequency 99.7015 GHz near the middle of the line-free range  
  > "Spectral channels contaminated by strong molecular lines reported in (cite: Saito22b) and (cite: Nakajima23) are removed before imaging the continuum." (2.1.1 Band 3 Continuum); "The reference frequency is set to be 99.7015 GHz, which is nearly the middle of the line-free frequency range." (2.1.1 Band 3 Continuum)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: All ALMA and VLA maps convolved to a round 0.8 arcsec beam before hexagonal regridding  
  > "we convolve all the ALMA and VLA maps to a round beam with 0.8$''$" (2.3 Hexagonal sampling)
- final beam: 0.8 arcsec round beam (55 pc)  
  > "Major and minor axes of the original synthesized beam in full width at half maximum (FWHM) before convolution to 55 pc ($=$0.8$''$)." (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Calibration and imaging pipelines/procedures follow earlier NGC 1068 papers  
  > "Following (cite: Saito22a) and (cite: Saito22b), we performed calibration with the observatory-provided calibration pipeline (cite: Hunter23)" (2.1.1 Band 3 Continuum) [from (cite: Saito22a); (cite: Saito22b)]
- Band 6 calibration and imaging same as Band 3  
  > "We performed basically the same calibration and imaging procedures for the Band 3 data." (2.1.2 Band 6 Continuum) [from Section 2.1.1 (Band 3 procedure)]
- Strong molecular-line channels removed before continuum imaging  
  > "Spectral channels contaminated by strong molecular lines reported in (cite: Saito22b) and (cite: Nakajima23) are removed before imaging the continuum." (2.1.1 Band 3 Continuum) [from (cite: Saito22b); (cite: Nakajima23)]
- Hexagonal close-packed grid sampling  
  > "(cite: Brok21; Saito22b)" (2.3 Hexagonal sampling) [from (cite: Brok21); (cite: Saito22b)]
- HST Pa-alpha data properties and data reduction  
  > "The details of the data properties and data reduction can be found in (cite: Garcia-Burrillo14) and (cite: Sanchez-Garcia22)." (2.2.1 HST Data) [from (cite: Garcia-Burrillo14); (cite: Sanchez-Garcia22)]
- DIG correction method  
  > "We follow the DIG correction method described in (cite: Kaplan16)." (3.2.3 Correcting for diffuse ionized gas) [from (cite: Kaplan16); (cite: Kreckel16)]
- Pa-alpha to SFR prescription  
  > "In this study, we follow the prescription described in (cite: Bendo16)." (3.2.4 Converting from Pa-alpha to SFR) [from (cite: Bendo16)]
- Free-free to SFR prescription  
  > "Following (cite: Michiyama20), free-free-based SFR (SFR$_{\rm FFC}$) can be expressed as," (3.3.2 Converting from free-free to SFR) [from (cite: Michiyama20)]
- BPT pixel classification of AGN-affected pixels  
  > "we diagnosed it with a BPT diagram on a pixel-by-pixel basis (cite: Mingozzi19)" (3.2.5 Possible AGN contamination) [from (cite: Mingozzi19)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: niter, threshold, multiscale scales, nterms, weighting/robust, cell and image size, masking, gridder
- Which specific channels were flagged as line-contaminated for each project (the list lives in Saito22b and Nakajima23)
- How the 12-m and 7-m data and the many archival projects were combined, weighted and flux-scale aligned (PHANGS-ALMA pipeline settings, feathering or joint deconvolution)
- CASA and ALMA pipeline versions, and PHANGS pipeline version
- ALMA array configurations, baselines, maximum recoverable scale and observing dates for each project
- The calibrated HST Pa-alpha map was a private communication; the exact flux calibration and continuum subtraction are only referenced to Garcia-Burillo14 and Sanchez-Garcia22
- The value of the DIG exponent beta in the [S II]/H-alpha fit and how C_DIG was converted to a per-hexagon correction
- How per-hexagon and total SFR uncertainties (e.g. +/-15%) were derived; the 0.9 mJy/beam versus 0.1 mJy/beam sensitivity inconsistency is not resolved
- Hexagonal grid center, orientation and treatment of partially covered hexagons; how the 5 sigma VLA mask and the 3 sigma S/N clipping were jointly applied for each tracer
- Rest frequency and flux units used when converting HST Pa-alpha map to L_RL; treatment of the 261 GHz non-detections in the cold-dust subtraction beyond skipping them

## Analysis recipe

1. **Image Band 3 and Band 6 continuum**: Calibrate with the observatory pipeline, then image continuum with mtmfs tclean in the PHANGS-ALMA pipeline after removing line-contaminated channels; reference frequencies 99.7015 GHz and 260.5180 GHz  
  > "We performed the continuum imaging with multi-term (multi-scale) multi-frequency synthesis (mtmfs; (cite: Rau11)) using `CASA tclean`." (2.1.1 Band 3 Continuum); "We performed basically the same calibration and imaging procedures for the Band 3 data." (2.1.2 Band 6 Continuum)
   - software: CASA, PHANGS-ALMA pipeline, ALMA pipeline
   - parameter: Reference frequency 99.7015 GHz (Band 3) and 260.5180 GHz (Band 6)  
  > "The reference frequency is set to be 99.7015 GHz" (2.1.1 Band 3 Continuum); "We set the reference frequency to 260.5180 GHz when imaging with the mtmfs mode" (2.1.2 Band 6 Continuum)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract MUSE line maps**: Spectral extraction and measurement of MUSE cube with Astropy and Specutils  
  > "Spectral extraction and measurement are performed using `Astropy` (cite: Astropy13; Astropy18; Astropy22) and `Specutils` (cite: Earl23)." (2.2.2 MUSE Data)
   - software: Astropy, Specutils
   - fitting: _not stated_
   - validation: _not stated_
3. **Convolve and resample all maps onto a 55 pc hexagonal grid**: Convolve ALMA and VLA maps to a round 0.8 arcsec beam, average pixels over each 0.8 arcsec hexagon, clip at S/N 3; MUSE and HST maps used as is  
  > "We perform this hexagonal regridding by averaging pixels over each hexagon." (2.3 Hexagonal sampling); "Then, clipping based on signal-to-noise ratio (at an S/N of 3) is done for further analyses." (2.3 Hexagonal sampling)
   - software: radio-beam, spectral-cube
   - parameter: Hexagon size 0.8 arcsec = 55 pc  
  > "The size of each hexagon is set to be 0.8$''$" (2.3 Hexagonal sampling)
   - parameter: Typical rms evaluated at signal-free hexagons of each map  
  > "We evaluate the typical rms at signal-free hexagons of each map." (2.3 Hexagonal sampling)
   - fitting: _not stated_
   - validation: Hexagon rms taken as sqrt(N) times pixel rms; log-normal SFR histogram compared between pixel and hexagon bases to check no sampling bias  
  > "We confirmed this by comparing the histograms of $L_{\rm RL}$ in the pixel bases and hexagon bases" (Appendix: SFR distribution)
4. **Mask AGN radio jet and central synchrotron**: Exclude hexagons detected above 5 sigma in the VLA 14.9 GHz map and mask the central r~0.8 kpc  
  > "Practically, we exclude hexagons detected with more than 5 sigma in the entire VLA 14.9 GHz continuum map" (3.2.1 Masking AGN radio jet); "Therefore, we decided to mask the central r$\sim$0.8 kpc from further SFR analyses." (3.2.1 Masking AGN radio jet)
   - parameter: 5 sigma threshold on VLA 14.9 GHz  
  > "we exclude hexagons detected with more than 5 sigma in the entire VLA 14.9 GHz continuum map" (3.2.1 Masking AGN radio jet)
   - assumption: Synchrotron spectral index -0.8; synchrotron in the starburst ring <0.40 mJy at 100 GHz (<19% of the 3 sigma flux), thus negligible  
  > "using a spectral index of $\alpha$ = -0.8" (3.2.1 Masking AGN radio jet); "Therefore, we conclude that synchrotron emission has negligible influence on the derivation of the free-free flux at the starburst ring." (3.2.1 Masking AGN radio jet)
   - fitting: _not stated_
   - validation: Photometry of inner and outer regions (Table 1) and BPT classification of AGN-affected pixels  
  > "However, the photometric measurements (Table [1](#table:PhotometryCenterOuter)) imply that the effect of the synchrotron emission on the 100 GHz data is negligible in the starburst ring." (3.2.1 Masking AGN radio jet)
5. **Correct Pa-alpha for dust extinction**: Use the MAGNUM A_V map recalculated with R_V = 4.05 under the Calzetti law, convert to A at 1.875 micron  
  > "In our study, we recalculated the $A_{V}$ map by using $R_{V}$ $=$ 4.05" (3.2.2 Correcting for dust extinction); "We derive A$_{\lambda 1.875}$/$A_V$ of 0.145 by extrapolating $A_V$ from $R_V$=3.1 to $R_V$=4.05." (Appendix: Extinction correction for Pa-alpha)
   - parameter: R_V = 4.05 (original map R_V = 3.1, H-beta/H-alpha = 2.86); A(1.875 um)/A_V = 0.145  
  > "They assumed the selective extinction $R_V$ $=$ 3.1 and H$\beta$/H$\alpha$ $=$ 2.86." (Appendix: Extinction correction for Pa-alpha)
   - assumption: Calzetti extinction law; original map assumed fixed electron temperature 1e5 K  
  > "a fixed electron temperature $=$ 10$^5$ K" (3.2.2 Correcting for dust extinction)
   - fitting: _not stated_
   - validation: A_1.875/A_V agrees with Piqueras13 central V-band value; correction changes pixel values by <~0.2 dex and total flux by ~25%  
  > "The accuracy of this value is confirmed by its agreement with the value derived by (cite: Piqueras13)" (Appendix: Extinction correction for Pa-alpha); "although it changes the total flux by $\simeq$25%" (3.2.2 Correcting for dust extinction)
6. **Correct Pa-alpha for diffuse ionized gas**: [S II]/H-alpha versus H-alpha flux method (Kaplan16, Kreckel16) to derive a DIG fraction per hexagon and subtract the DIG contribution  
  > "After creating the DIG fraction map (Figure [7](#Fig:rdig_fig7)), we apply this correction to the extinction-corrected Pa$\alpha$ map to subtract the DIG contribution." (3.2.3 Correcting for diffuse ionized gas); "We use the prescription proposed in (cite: Kaplan16) and (cite: Kreckel16)." (Appendix: DIG correction to the Pa-alpha)
   - parameter: f0 = 3.25e-15 erg s-1 cm-1 (minimum H-alpha flux for an H II region, from Kaplan16)  
  > "was 3.25 $\times$ 10$^{-15}$ erg s$^{-1}$ cm$^{-1}$" (Appendix: DIG correction to the Pa-alpha)
   - assumption: Pure H II regions have strong H-alpha emission; low-ionization (high [S II]/H-alpha) gas is DIG  
  > "In this method, the data showing the strong intensity of H$\alpha$ emission are defined as pure H II regions" (Appendix: DIG correction to the Pa-alpha)
   - fitting: _not stated_
   - validation: DIG-corrected map shows much less extended low surface brightness structure  
  > "The DIG-corrected map shows much less extended, low surface brightness structures implying that the method works as expected." (3.2.3 Correcting for diffuse ionized gas)
7. **Convert corrected Pa-alpha to SFR as a function of Te**: Ionizing photon rate Q from case-B alpha_B(Te) and Pa-alpha emissivity epsilon(Te), SFR = 5.41e-54 Q; L_RL from Solomon05  
  > "This equation expresses that the Pa$\alpha$-based SFR has a dependence of $T_{\rm e}^{0.26}$." (3.2.4 Converting from Pa-alpha to SFR); "We calculate $L_{\rm{RL}}$ by using the equation in (cite: Solomon05)" (3.2.4 Converting from Pa-alpha to SFR)
   - parameter: n_e = 1e3 cm-3; alpha_B = 3.63e-10 Te^-0.79; epsilon = 6.37e-24 Te^-1.05; D_L = 13.97 Mpc; z = 0.003793  
  > "With fixing $n_{\rm e}$ to be 10$^3$ cm$^{-3}$" (3.2.4 Converting from Pa-alpha to SFR); "z is the source redshift ($=$ 0.003793)" (3.2.4 Converting from Pa-alpha to SFR)
   - assumption: Kroupa IMF  
  > "We use the Kroupa IMF (cite: Kroupa01)" (3.2.4 Converting from Pa-alpha to SFR)
   - assumption: Case-B recombination  
  > "With the case-B recombination assumption (cite: BakerandMenzel38)" (3.2.4 Converting from Pa-alpha to SFR)
   - fitting: _not stated_
   - validation: Conversion coefficient can vary by a factor of two with assumptions and star formation history  
  > "We note that the conversion coefficient can vary by a factor of two depending on assumed parameters and star formation history (cite: Bendo15)." (3.2.4 Converting from Pa-alpha to SFR)
8. **Subtract cold dust from the 100 GHz continuum**: Extrapolate the 261 GHz map to 100 GHz with a fixed spectral index of 4 and subtract; no subtraction where 261 GHz is undetected; result treated as free-free map  
  > "we derive the expected cold dust flux map at 100 GHz by extrapolating the ALMA 261 GHz continuum map" (3.3.1 Removing cold dust continuum); "We regard the dust-subtracted 100 GHz map as a free-free continuum map hereafter." (3.3.1 Removing cold dust continuum)
   - parameter: Spectral index 4 (3.8 tested)  
  > "with a fixed spectral index of 4 and subtract it from the 100 GHz map." (3.3.1 Removing cold dust continuum)
   - assumption: Remaining emission after masking is free of synchrotron; DIG free-free is below sensitivity  
  > "The remaining pixels are free from contamination by synchrotron emission." (3.3.1 Removing cold dust continuum)
   - fitting: _not stated_
   - validation: Pixel-by-pixel comparison before/after subtraction: total flux changes by 13 +/- 1%; slope 3.8 changes cold dust flux by ~4%  
  > "The difference in the total flux is 13$\pm$1 %" (3.3.1 Removing cold dust continuum); "if we assume a shallower Rayleigh-Jeans slope of 3.8 instead, the total flux of the cold dust component at 100 GHz increases by $\simeq$4%" (3.3.1 Removing cold dust continuum)
9. **Convert free-free continuum to SFR as a function of Te**: SFR_FFC from Michiyama20 with Gaunt factor g_ff(Te, nu) and alpha_B(Te); no DIG correction because DIG free-free is expected well below the 100 GHz sensitivity  
  > "Following (cite: Michiyama20), free-free-based SFR (SFR$_{\rm FFC}$) can be expressed as," (3.3.2 Converting from free-free to SFR); "This is because our 100 GHz continuum map is not sensitive enough to detect free-free continuum from the DIG of NGC 1068." (3.3.3 Evaluating the effect of diffuse ionized gas on 100 GHz continuum)
   - parameter: Ionic charge Z = 1; g_ff varies by up to ~1.4 for 3000 K < Te < 10000 K  
  > "where Z is the ionic charge ($=$ 1)" (3.3.2 Converting from free-free to SFR)
   - assumption: Expected peak DIG free-free at 100 GHz is 0.01 microJy/beam from Pa-alpha-based EM_DIG with Milky Way DIG Te 6000-10000 K, n_e ~0.05 cm-3 and scale height ~1000 pc  
  > "The typical $T_{\rm e}$ for the DIG in the Milky Way is estimated to be 6000–10000 K" (Appendix: Negligible contamination of DIG for free-free continuum)
   - fitting: _not stated_
   - validation: Free-free map shows much less extended structure than the Pa-alpha or H-alpha maps  
  > "the free-free continuum map shows much less extended structures compared to the original Pa$\alpha$ map or H$\alpha$ map that contains the DIG components" (3.3.3 Evaluating the effect of diffuse ionized gas on 100 GHz continuum)
10. **Derive the single best electron temperature**: Regress Pa-alpha-based SFR against free-free-based SFR with slope fixed to unity; scan Te from 500 to 30000 K and find where the fitted intercept is zero; run for DIG-corrected (case 1) and uncorrected (case 2) Pa-alpha  
  > "In practice, we perform a least-squares regression with a fixed slope of unity for a scatter plot between the Pa$\alpha$-based SFR map and the free-free-based SFR map" (3.4.1 Estimating electron temperature); "The searched $T_{\rm e}$ range is between 500 and 30000 K." (3.4.1 Estimating electron temperature)
   - parameter: Te search range 500-30000 K; fitting error bar of the intercept taken as the intercept error and propagated to Te  
  > "We regard the fitting error bar as the error of the intercept." (3.4.1 Estimating electron temperature)
   - assumption: Both tracers arise from the same ionized gas, so the two SFR maps agree if corrections and Te are right  
  > "Because the two tracers can be assumed to come from the same ionized gas ISM in galaxies, two SFR maps should agree with each other" (3.4.1 Estimating electron temperature)
   - fitting: Weighted least squares, slope fixed to 1, weights w_i = 1/sigma_i with sigma_i^2 = sigma_x^2/x^2 + sigma_y^2/y^2; no sampler or priors  
  > "When fitting, we weight data point located at ($x_{i}$, $y_{i}$) with" (3.4.1 Estimating electron temperature)
   - validation: Case 2b with matched pixels shows the DIG effect is not due to pixel number; per-hexagon Te fits (>=6 neighbours) give implausible Te spread and affirm using a single Te  
  > "Therefore, we concluded that the difference between case 1 and case 2 is not due to the difference in the number of pixels but is an actual trend due to the DIG correction." (3.4.2 Applying the best Te and calclating SFR); "This result affirms the advantage of estimating a single $T_{\rm e}$ in the starburst ring." (Appendix: Spatial distribution of electron temperature)
11. **Compute SFR maps and total SFR**: Apply best-fit Te to the Pa-alpha map to build Sigma_SFR maps and sum over detected hexagons for case 1 and case 2  
  > "we make $\Sigma_{\mathrm{SFR}}$ maps in the entire starburst ring of NGC 1068 (Figure [13](#Fig:SFRs_fig13)) by applying the best-fitted $T_{\rm e}$" (3.4.2 Applying the best Te and calclating SFR)
   - fitting: _not stated_
   - validation: Case 2b matched-pixel check: Te = 2820 K and SFR = 5.7 +/- 1.2 Msun/yr  
  > "We get $T_{\rm e}$ $=$ 2820 K, SFR $=$ 5.7 $\pm$ 1.2 $M_{\odot}$ yr$^{-1}$ in this case." (3.4.2 Applying the best Te and calclating SFR)
12. **Compare with 8 micron SFR and other galaxies**: Scale Tsai12 8 micron SFR from Salpeter to Kroupa IMF and compare totals; compare Te with NGC 253 and NGC 4945 vs R/R25  
  > "This results in a total SFR of 2.0 $\pm$ 0.1 $M_{\odot}$ yr$^{-1}$, which is roughly two-thirds of our total SFR value." (4.1 Reliability of this SFR prescription)
   - parameter: Salpeter-to-Kroupa factor 1.6  
  > "Salpeter-to-Kroupa conversion factor 1.6 (cite: Marchesini09)" (4.1 Reliability of this SFR prescription)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA (tclean, mtmfs)** : Continuum imaging with multi-term multi-frequency synthesis  
  > "using `CASA tclean`" (2.1.1 Band 3 Continuum)
- **ALMA Interferometric Pipeline** : Observatory-provided calibration  
  > "`ALMA Interferometric Pipeline`" (Software); "observatory-provided calibration pipeline (cite: Hunter23)" (2.1.1 Band 3 Continuum)
- **PHANGS-ALMA imaging pipeline** : Imaging of the calibrated ALMA data  
  > "imaging with the `PHANGS-ALMA imaging pipeline` (cite: Leroy21a)" (2.1.1 Band 3 Continuum)
- **Astropy** : MUSE spectral extraction and measurement  
  > "Spectral extraction and measurement are performed using `Astropy` (cite: Astropy13; Astropy18; Astropy22)" (2.2.2 MUSE Data)
- **Specutils** : MUSE spectral extraction and measurement  
  > "and `Specutils` (cite: Earl23)" (2.2.2 MUSE Data)
- **STARBURST99** : Calculation of the SFR-to-ionizing-photon conversion coefficient (cited from earlier work)  
  > "were calculated using STARBURST99 (cite: Leitherer99)" (3.2.4 Converting from Pa-alpha to SFR)
- **NumPy** : Listed in Software section; specific use not stated  
  > "`NumPy` (cite: Harris20)" (Software)
- **SciPy** : Listed in Software section; specific use not stated  
  > "`SciPy` (cite: Virtanen20)" (Software)
- **spectral-cube** : Listed in Software section; specific use not stated  
  > "`spectral-cube` (cite: Ginsburg19)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit Te, DIG-corrected (case 1) | 6690 | +360/-340 | K | 10 | we derived $T_{\rm e}$ $=$ 6690$^{+360}_{-340}$ K (3510$^{+120}_{-110}$ K) |
| Best-fit Te, DIG-uncorrected (case 2) | 3510 | +120/-110 | K | 10 | we derived $T_{\rm e}$ $=$ 6690$^{+360}_{-340}$ K (3510$^{+120}_{-110}$ K) |
| Total SFR, DIG-corrected (case 1) | 3.2 | 0.5 | Msun/yr | 11 | The total SFR is 3.2 $\pm$ 0.5 $M_{\odot}$ yr$^{-1}$ for case 1 and 9.1 $\pm$ 1.4 $M_{\odot}$ yr$^{-1}$ for case 2 |
| Total SFR, DIG-uncorrected (case 2) | 9.1 | 1.4 | Msun/yr | 11 | The total SFR is 3.2 $\pm$ 0.5 $M_{\odot}$ yr$^{-1}$ for case 1 and 9.1 $\pm$ 1.4 $M_{\odot}$ yr$^{-1}$ for case 2 |
| Te and total SFR, matched-pixel DIG-uncorrected (case 2b) | Te = 2820 K; SFR = 5.7 | SFR +/-1.2 (Te error not stated) | K; Msun/yr | 11 | We get $T_{\rm e}$ $=$ 2820 K, SFR $=$ 5.7 $\pm$ 1.2 $M_{\odot}$ yr$^{-1}$ in this case. |
| Change in total 100 GHz flux from cold-dust subtraction | 13 | 1 | percent | 8 | The difference in the total flux is 13$\pm$1 % |
| Change in total Pa-alpha flux from extinction correction | ~25 | not stated | percent | 5 | although it changes the total flux by $\simeq$25% |
| A(1.875 micron)/A_V for R_V = 4.05 | 0.145 | not stated | dimensionless | 5 | We derive A$_{\lambda 1.875}$/$A_V$ of 0.145 by extrapolating $A_V$ from $R_V$=3.1 to $R_V$=4.05. |
| 100 GHz flux, r < 0.8 kpc | 0.111 | 0.005 (statistical only) | Jy | 1 | 0.111$\pm$0.005 |
| 100 GHz flux, r > 0.8 kpc | 0.021 | 0.001 (statistical only) | Jy | 1 | 0.021$\pm$0.001 |
| 261 GHz flux, r > 0.8 kpc | 0.119 | 0.012 (statistical only) | Jy | 1 | 0.119$\pm$0.012 |
| Expected synchrotron flux at 100 GHz in the starburst ring (upper limit) | <0.40 | not stated | mJy | 4 | we estimated the expected flux of the synchrotron continuum at 100 GHz to be $<$0.40 mJy |
| Expected peak DIG free-free flux at 100 GHz | 0.01 | not stated | microJy/beam | 9 | The expected peak DIG flux at 100 GHz is 0.01 $\mu$Jy beam$^{-1}$ |
| Tsai12 8 micron total SFR rescaled to Kroupa IMF | 2.0 | 0.1 | Msun/yr | 12 | This results in a total SFR of 2.0 $\pm$ 0.1 $M_{\odot}$ yr$^{-1}$ |
| Number of detected hexagons: DIG-corrected / DIG-uncorrected SFR maps | 864 / 1548 | not stated | hexagons | 11 | / DIG-corrected case / 6690$^{+360}_{-340}$ / 3.2$\pm$0.5 / 46.7$\pm$7.0 / 0.6$\pm$0.1 / 0.002$\pm$0.0005 / 864 /; / DIG-uncorrected case / 3510$^{+120}_{-110}$ / 9.1$\pm$1.4 / 47.1$\pm$7.1 / 1.2$\pm$0.2 / 0.25$\pm$0.09 / 1548 / |

## Qualitative findings

- Accounting for DIG reduces the total SFR to about one-third of the uncorrected value and raises Te  
  > "When correcting for DIG, $T_{\rm e}$ increases and the total SFR decreases." (3.4.2 Applying the best Te and calclating SFR)
- High SFR around the southern bar-end and the corotation radius  
  > "We confirmed high SFR around the southern bar-end and the corotation radius, which is consistent with the previous SFR measurements." (abstract)
- Te differences among NGC 253, NGC 4945 and NGC 1068 may relate to the negative metallicity gradient rather than the mass-metallicity relation  
  > "suggests that the difference in $T_{\rm e}$ among the sample galaxies is related to the negative metallicity gradient rather than the mass-metallicity relation" (5 Summary)

## Claim tuples

- H: Does neglecting DIG bias the SFR of the NGC 1068 disk from ionized-gas tracers? | E: Cross-calibrate ALMA 100 GHz free-free and HST Pa-alpha SFR maps with and without the [S II]/H-alpha DIG correction, solving for a single Te | R: Total SFR 3.2 +/- 0.5 Msun/yr with DIG correction versus 9.1 +/- 1.4 Msun/yr without; Te 6690 K versus 3510 K | F: DIG correction is essential; the uncorrected SFR is about three times larger | **supported**
- H: Is synchrotron contamination negligible for the free-free derivation in the starburst ring (r > 0.8 kpc)? | E: Extrapolate the VLA 14.9 GHz 3 sigma limit to 100 GHz with index -0.8 and compare with 100 GHz detectable flux; mask the central 0.8 kpc | R: Expected synchrotron <0.40 mJy, <19% of the 3 sigma 100 GHz flux | F: Synchrotron has negligible influence in the ring; only cold dust is subtracted | **supported**
- H: Is the DIG contribution to the 100 GHz continuum negligible? | E: Predict free-free from DIG using Pa-alpha-based EM and Milky Way DIG properties | R: Expected peak DIG flux 0.01 microJy/beam, far below the map RMS | F: No DIG correction is needed for the free-free map | **supported**
- H: Does the new SFR agree with the 8 micron SFR of Tsai12? | E: Rescale the 8 micron total SFR to a Kroupa IMF and compare with the DIG-corrected total | R: Our total SFR exceeds the 8 micron based SFR by a factor of 1.5 (2.0 versus 3.2 Msun/yr) | F: The discrepancy is attributed to different prescriptions and timescales, not demonstrated directly | **partially**
- H: Is star formation enhanced at the bar ends and corotation radius? | E: Inspect the DIG-corrected Sigma_SFR map | R: High Sigma_SFR outside the bar end and a blob at the northern tip of the eastern spiral arm with H II regions in HST | F: Consistent with prior NGC 1068 observations of bar-end star formation | **supported**
- H: What drives the Te differences among NGC 253, NGC 4945 and NGC 1068? | E: Compare Te, stellar mass and R/R25 across the three galaxies measured with a recombination line plus free-free | R: Te rises with R/R25 (3900, 5400, 6690 K) | F: A negative metallicity gradient is a plausible explanation, but not confirmed | **partially**

## Reasoning

- Why this data: Free-free continuum is observable by ALMA and free of dust extinction, complementing the dust-affected Pa-alpha; archival data were stacked to gain sensitivity  
  > "Conversely, thermal bremsstrahlung (free-free radiation) is observable by ALMA at millimeter wavelengths and is free from dust extinction" (1 Introduction); "To further gain sensitivity, we utilized ten projects publicly available in the ALMA archive" (2.1.1 Band 3 Continuum)
- Why this method: Complementary tracers offset each other's weaknesses and constrain otherwise unknown parameters such as Te  
  > "A key approach is using complementary tracers, e.g., hydrogen recombination lines and thermal bremsstrahlung emission (cite: Bendo15)." (1 Introduction)
- Alternative: Per-hexagon Te fitting (with >=6 neighbouring hexagons) rejected because it gave theoretically implausible Te above 15000 K or below 4000 K  
  > "These extreme values are theoretically difficult to explain." (Appendix: Spatial distribution of electron temperature)
- Alternative: Keeping R_V = 3.1 for the extinction correction rejected as it gives unrealistic Pa-alpha intensities  
  > "If $R_V$ remains at 3.1, the corrected Pa$\alpha$ intensity becomes unrealistic for some pixels." (Appendix: Extinction correction for Pa-alpha)
- Alternative: Removing synchrotron from the central region by SED fitting not done  
  > "This is because we can not accurately remove the contamination by synchrotron emission due to the lack of a sufficient number of SED data points." (3.2.1 Masking AGN radio jet)
- How they decided it was enough: _not stated_
- Limitation (authors): The cold-dust spectral index is fixed; more high-frequency data points are needed  
  > "This could be further investigated by adding more data points to the higher frequency regime." (3.3.1 Removing cold dust continuum)
- Limitation (authors): Photometry table errors are statistical only  
  > "We only consider the statistical noise in this table." (Table 3)
- Limitation (authors): Origin of Te variation among galaxies not established  
  > "it is unclear whether the radial metallicity gradient can fully explain the variations" (4.3 Comparing electron temperature with other galaxies)
- Caveat (inferred, ours): Paper gives two different 100 GHz sensitivities (0.9 mJy/beam in Section 3.3.3 versus 0.1 mJy/beam in the appendix)
- Caveat (inferred, ours): Single global Te assumed for the whole ring; derived value depends strongly on the DIG correction method and its threshold choices
- Caveat (inferred, ours): Pa-alpha map is a private-communication product; uncertainties in HST continuum subtraction and absolute flux (25% extinction effect is comparable) feed directly into Te
- Caveat (inferred, ours): Cold-dust slope fixed at 4 and no free-free spectral index fit; no true uncertainty on SFR beyond fit errors
- Caveat (inferred, ours): Stacking many archival projects of different configurations and flux calibrations without stated cross-calibration
- Caveat (inferred, ours): DIG-corrected case-1 N_hex (864) differs from case 2 (1548); case 2b only partly isolates DIG effect

## Reproducibility

- Data public (paper): ALMA projects are public archive data; MUSE cube from the ESO archive; VLA map from the NRAO archive; HST Pa-alpha map via private communication  
  > "we utilized ten projects publicly available in the ALMA archive" (2.1.1 Band 3 Continuum); "We downloaded the MUSE data cube from the ESO archive" (2.2.2 MUSE Data); "We downloaded a 14.9 GHz (Ku-band) radio continuum map taken by VLA from the NRAO Data Archive." (2.2.3 VLA Data)
- Products in archive: _not stated_
- Missing: tclean and PHANGS-ALMA pipeline settings and software versions
- Missing: Line-contaminated channel lists per project
- Missing: Combination/weighting of 12-m, 7-m and archival datasets
- Missing: Calibrated HST Pa-alpha map (private communication)
- Missing: DIG fit parameters (beta) and exact hexagon grid definition
- Missing: Source code for the SFR/Te regression
- Data volume (inferred): Large: 18 ALMA projects (12-m and 7-m, Band 3 and Band 6 spectral scans, ~51 h in Band 3) plus MUSE cube; likely several hundred GB to a few TB of raw/calibrated data
- Score (inferred): 3/5, ALMA data are public and equations/parameters for the SFR and Te derivation are largely given, but imaging parameters, channel lists, array combination, DIG fit parameters and the HST Pa-alpha map are not fully specified or public.
- Rediscovery candidate: no, Key ancillary input (HST Pa-alpha map) was provided privately and the imaging recipe for combining 18 projects is incomplete, though the main results (SFR, Te) are numeric.

## Links

- Method: Leroy21a (PHANGS-ALMA imaging pipeline used for continuum imaging)
- Method: Hunter23 (Observatory-provided calibration pipeline)
- Method: Kaplan16; Kreckel16 ([S II]/H-alpha DIG correction method)
- Method: Bendo16; Michiyama20 (SFR prescriptions for recombination lines and free-free continuum and the Te cross-calibration concept)
- Method: Calzetti00 (Extinction law used to recompute A_V for R_V = 4.05)
- Method: Rau11 (mtmfs imaging algorithm)
- Companion: Saito22a; Saito22b (Earlier NGC 1068 ALMA work whose calibration, imaging and line-channel selection are followed)
- Companion: Nakajima23 (Band 3 12-m spectral scan (2013.1.00279.S) and strong-line channel list)
- Companion: Garcia-Burrillo14; Sanchez-Garcia22 (HST Pa-alpha map and its reduction)
- Companion: Mingozzi19 (MUSE-based extinction and [S II] ratio maps and BPT classification)
- Related: PHANGS-ALMA
- Related: MAGNUM survey
- Related: NRAO VLA Archive Survey (NVAS)

## Checks

```json
{
 "quotes": 182,
 "quotes_ok": 182,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 18,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 141,
  "stated": 105,
  "rate": 0.745
 },
 "evidence_ok": true
}
```
