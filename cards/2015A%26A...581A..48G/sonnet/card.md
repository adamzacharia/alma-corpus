# A 1.3 cm line survey toward Orion KL

`2015A&A...581A..48G` | Astronomy and Astrophysics 2015 | first author: Gong, Y. | arXiv: 1506.03235 | DOI: 10.1051/0004-6361/201526275

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What are the spectral characteristics of Orion KL in the 1.3 cm band, and where do the detected molecules originate spatially?  
  > "The main goal is to systematically study spectral characteristics of Orion KL in the $\lambda \sim 1.3$ cm band." (abstract)
- Target **Orion KL**: coordinates RA 05h35m14.17s, Dec -05d22m46.5s (J2000), Effelsberg pointing  
  > "is the closest high mass star formation region at a distance of 414$\pm$7  pc (cite: 2007A&A...474..515M)" (1 Introduction); "The telescope was pointed at $\alpha_{\rm J2000}=05^{\rm h}35^{\rm m}14.17^{\rm s}$, $\delta_{\rm J2000}=-05^{\circ}22^{\prime}46.5^{\prime\prime}$" (2.1 Observations with the Effelsberg-100m telescope); z/distance 414±7 pc  
  > "is the closest high mass star formation region at a distance of 414$\pm$7  pc (cite: 2007A&A...474..515M)" (1 Introduction); "The telescope was pointed at $\alpha_{\rm J2000}=05^{\rm h}35^{\rm m}14.17^{\rm s}$, $\delta_{\rm J2000}=-05^{\circ}22^{\prime}46.5^{\prime\prime}$" (2.1 Observations with the Effelsberg-100m telescope); distance from Menten et al. 2007  
  > "is the closest high mass star formation region at a distance of 414$\pm$7  pc (cite: 2007A&A...474..515M)" (1 Introduction); "The telescope was pointed at $\alpha_{\rm J2000}=05^{\rm h}35^{\rm m}14.17^{\rm s}$, $\delta_{\rm J2000}=-05^{\circ}22^{\prime}46.5^{\prime\prime}$" (2.1 Observations with the Effelsberg-100m telescope)

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: _not stated_
- frequencies and spectral setup: 214–247 GHz line survey; spectral resolution 0.488 MHz (~0.6 km/s at 230 GHz)  
  > "archival ALMA line survey data covering a frequency range of 214–247 GHz" (2.2 Archival data); "The spectral resolution is 0.488 MHz, which corresponds to $\sim$0.6 km s$^{-1}$ at 230 GHz." (2.2 Archival data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.9"×1.4" synthesized beam; primary beam ~30"  
  > "The synthesized beam size is 1.9$''$$\times$1.4$''$." (2.2 Archival data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 January 20 (SV phase)  
  > "The observations were carried out with 16 antennas on 2012 January 20, during ALMA’s science verification (SV) phase." (2.2 Archival data)
- pi or archival as stated: Archival ALMA science verification data, public  
  > "The data are available to the public and can be accessed from the ALMA-SV website" (2.2 Archival data)
- Line: NH2D 3_2,2 s - 3_1,2 a (216562.7 MHz)
- Line: HC3N 24-23 (218324.7 MHz)
- Line: OCS 18-17 (218903.4 MHz)
- Line: SO2 11_5,7-12_4,8 (229347.6 MHz)
- Other facility **Effelsberg-100m**: 1.3 cm (17.9–26.2 GHz) line survey, main dataset  
  > "It covers the frequency range between 17.9 GHz and 26.2 GHz, i.e., the radio “K-band”." (abstract)
- Other facility **VLA**: C band continuum data (project AY191A) for large-scale structure  
  > "we also make use of the VLA C band continuum data[^5] (project AY191A)" (2.2 Archival data)
- Other facility **SCUBA**: 850 μm dust emission  
  > "the SCUBA–850 $\mu$m dust emission (cite: 2008ApJS..175..277D)" (2.2 Archival data)
- External data: H2 column densities and source sizes per component  
  > "The H$_{2}$ column densities adopted in (cite: 2014ApJ...787..112C) are used to calculate fractional abundances of the detected molecules." (5.1) [from (cite: 2014ApJ...787..112C)]
- External data: IRAM-30m line data for flux-loss comparison (HC3N, OCS, SO2)  
  > "We make use of HC$_{3}$N (24–23) from (cite: 2013AA...559A..51E), OCS (18–17) from (cite: 2010AA...517A..96T), and SO$_{2}$ ($11_{5,7}-12_{4,8}$) from (cite: 2013AA...556A.143E)." (Appendix) [from Esplugues 2013a; Tercero 2010; Esplugues 2013b]
- External data: Departure coefficients b_n  
  > "Based on a table of the departure coefficients $b_{n}$ provided by (cite: 1979ApJS...39..633S)" (4.2 Radio recombination lines) [from (cite: 1979ApJS...39..633S)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA: Callisto (flux), J0607-085 (phase); Effelsberg: NGC7027 and 3C286  
  > "Callisto and the quasar J0607-085 were used as the flux and phase calibrator, respectively." (2.2 Archival data); "Strong continuum sources (mostly NGC7027 and 3C286) were used to calibrate the spectral line flux" (2.1 Observations with the Effelsberg-100m telescope)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "The CLEAN algorithm in the Common Astronomy Software Applications package (CASA) was used to deconvolve the images applying natural weighting." (2.2 Archival data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The CLEAN algorithm in the Common Astronomy Software Applications package (CASA) was used to deconvolve the images applying natural weighting." (2.2 Archival data)
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
- final beam: 1.9"×1.4"  
  > "The synthesized beam size is 1.9$''$$\times$1.4$''$." (2.2 Archival data)
- final rms: _not stated_

### Inherited from earlier work

- Same source size for all molecules with same origin; source sizes from Table 2 of Crockett et al.  
  > "Following previous studies (cite: 2013ApJ...777...85N; 2014ApJ...787..112C), we assume that all molecules with the same origin have the same source size to simplify the calculation." (5.1) [from (cite: 2013ApJ...777...85N; 2014ApJ...787..112C)]
- Likelihood threshold L>0.6 for chi2 analysis  
  > "Following previous $\chi^{2}$ studies (cite: 2014A&A...568A.122Z), we only take solutions with a likelihood $L>0.6$ into account" (5.3) [from (cite: 2014A&A...568A.122Z)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure for ALMA SV data
- Line-free channels / continuum subtraction and imaging parameters (cell, size, clean threshold)
- Choice of rotational temperatures for single-line molecules
- Exact baseline orders per spectrum and RFI flagged channels
- Which ALMA SV execution blocks/spectral windows were used

## Analysis recipe

1. **Reduce Effelsberg spectra and identify lines**: Baseline subtraction (4th–10th order) on sub-spectra, stitching, RFI flagging; 3σ lines identified with JPL/CDMS/splatalogue/Lovas; Gaussian/HFS fits  
  > "Fourth to tenth order baselines were subtracted from each spectrum with 2000 to 3000 channels" (2.1 Observations with the Effelsberg-100m telescope); "A line is identified as real if it exhibits a 3$\sigma$ feature in more than 3 adjacent raw channels." (4.1 Line identifications)
   - software: GILDAS, CLASS
   - fitting: Single Gaussian for RRLs; CLASS HFS fit for hyperfine molecules; least-square Gaussians otherwise  
  > "we used the HFS fitting routine embedded in CLASS to derive the observed properties (including the optical depth) while least-square fits of Gaussians are performed for the other molecular transitions." (4.1 Line identifications)
   - validation: _not stated_
2. **Locate spatial origin of molecules with ALMA maps**: Compare line velocities/widths with ALMA-SV channel maps of 11 transitions  
  > "spatial distributions of their corresponding transitions at higher frequencies obtained from the ALMA-SV data" (4.3 Molecular lines)
   - software: CASA
   - fitting: _not stated_
   - validation: Flux loss estimated vs IRAM-30m: ALMA recovers 89% HC3N, 57% OCS, 44% SO2  
  > "the ALMA-SV data can account for 89% of the HC$_{3}$N (24–23), 57% of the OCS (18–17), and 44% of the SO$_{2}$ ($11_{5,7}-12_{4,8}$) emission." (Appendix)
3. **Rotational diagrams for column densities**: LTE rotational diagram least-squares fits; fixed Trot for single-line molecules; beam-dilution correction  
  > "For molecules with at least two transitions, we use least-square fits to the rotational diagrams to derive their rotational temperatures and column densities." (5.1)
   - parameter: filling factor 0.06 for assumed 10" source size  
  > "If we take a filling factor of 0.06 (corresponding to an assumed source size of 10$''$)" (5.1)
   - assumption: Optically thin, LTE, free-free continuum of KL itself zero, ortho-to-para NH3 ratio of unity  
  > "the free-free continuum emission of Orion KL itself is simply assumed to be zero in the radiative transfer equation" (5.1)
   - fitting: least-squares  
  > "For molecules with at least two transitions, we use least-square fits to the rotational diagrams to derive their rotational temperatures and column densities." (Discussion, 5.1 Rotational temperatures, column densities and fractional abundances relative to H$_{2}$)
   - validation: Compared with literature single-dish results  
  > "we find that most of our results agree well with previous studies based on (sub)millimeter lines except for SO$_{2}$, CH$_{3}$CN, and HNCO." (5.1)
4. **Derive elemental and isotopic ratios**: He/H from H/He RRL integrated intensity pairs (sigma-weighted mean); 12C/13C from CH3OH/13CH3OH; 14N/15N from NH3/15NH3; D/H from NH2D/NH3  
  > "we take the sigma-weighted mean value as the He/H abundance ratio which is estimated to be (8.7$\pm$0.7)%." (5.2.1)
   - assumption: HII region same size as HeII region; A/E ratio unity for 13CH3OH  
  > "Assuming that the HII region has the same size as the HeII region" (5.2.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Non-LTE RADEX modelling of 15NH3**: RADEX grid in Tkin and n(H2), chi2 on line ratios, keep L>0.6  
  > "The modeled kinetic temperatures ($T_{\rm kin}$) range from 10 to 500 K with a step size of 5 K." (5.3)
   - software: RADEX
   - parameter: velocity gradient 350 km/s/pc; para-15NH3 abundance 8e-9; log n(H2) 3.0–9.0 step 0.1  
  > "we obtain a velocity gradient of 350 km s$^{-1}$ pc$^{-1}$" (5.3)
   - assumption: Spherical geometry, only CMB radiation field, 15NH3 collision rates same as 14NH3  
  > "its collision rates are taken to be the same as those of $^{14}$NH$_{3}$" (5.3)
   - fitting: chi2 minimization with likelihood L=exp(-chi2/2)/Lmax  
  > "we only take solutions with a likelihood $L>0.6$ into account" (5.3)
   - validation: Repeated with abundances 8e-10 and 8e-8  
  > "we carried out another RADEX modelling with two different $^{15}$NH$_{3}$ abundances of 8$\times 10^{-10}$ and 8$\times 10^{-8}$." (5.3)

## Software

- **GILDAS/CLASS/GreG** : Effelsberg data reduction and line fitting  
  > "the GILDAS[^3] software package including CLASS and GreG was employed" (2.1 Observations with the Effelsberg-100m telescope)
- **CASA** : CLEAN imaging of ALMA SV data  
  > "The CLEAN algorithm in the Common Astronomy Software Applications package (CASA) was used" (2.2 Archival data)
- **RADEX** : non-LTE modelling of 15NH3  
  > "we present a non-LTE analysis of $^{15}$NH$_{3}$ using the RADEX code (cite: 2007A&A...468..627V)" (5.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of spectral lines | 261 (164 RRLs, 97 molecular) | not stated | lines | 1 | The identified lines include 164 radio recombination lines (RRLs) and 97 molecular lines. |
| He/H | 8.7 | 0.7 | % | 4 | He/H = (8.7$\pm0.7$)% |
| 12C/13C | 63 | 17 | dimensionless | 4 | $^{12}$C/$^{13}$C =63$\pm$17 |
| 14N/15N | 100 | 51 | dimensionless | 4 | $^{14}$N/$^{15}$N =100$\pm$51 |
| D/H | 8.3e-3 | 4.5e-3 | dimensionless | 4 | D/H = (8.3$\pm$4.5)$\times$10$^{-3}$ |
| 15NH3 ortho-to-para ratio | 0.99 | 0.34 | dimensionless | 3 | The ortho-to-para ratio is estimated to be $0.99\pm0.34$ |
| RADEX colder solution Tkin (para metastable) | 95-150 K at n=10^7.2-10^8.0 cm^-3 | not stated | K | 5 | a colder group with $T_{\rm kin}=95-150$ K and $n_{\rm H_{2}}= 10^{7.2}-10^{8.0}$ cm$^{-3}$ |

## Qualitative findings

- Chemical differentiation: N-bearing molecules favoured in HC, O-bearing in CR  
  > "nitrogen-bearing molecules are favored in the HC while oxygen-bearing molecules are more predominant in the CR" (4.3.8)

## Claim tuples

- H: Do H and He RRLs show LTE and identical departure coefficients? | E: Compared RRL intensity ratios and 28 H/He pairs | R: Ratios consistent with LTE; small He/H dispersion | F: b_n nearly identical for H and He | **supported**
- H: Is the Hot Core externally heated? | E: RADEX non-LTE likelihood analysis of 15NH3 line ratios | R: Denser solutions have lower Tkin | F: Favors external heating of HC | **partially**
- H: Where do detected molecules originate? | E: Line velocities/widths plus ALMA-SV channel maps | R: Origins assigned to HC, HC(S), CR, plateau, MM4-6 | F: Chemical differentiation exists | **supported**

## Reasoning

- Why this data: ALMA maps used to address spatial origin of 1.3 cm molecules  
  > "to study the distribution of molecules detected by our 1.3 cm line survey" (2.2 Archival data)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA images lack short spacings, so only sensitive to small-scale structure  
  > "Since the ALMA images without short spacings are only sensitive to small-scale structure" (2.2 Archival data)
- Limitation (authors): Non-LTE model neglects IR pumping, so densities are upper limits  
  > "our modeling without excitation by the infrared radiation field only gives upper limits for the spatial density" (5.3)
- Caveat (inferred, ours): ALMA used only qualitatively; beam mismatch (40" vs 30" primary beam) and missing flux
- Caveat (inferred, ours): Assumed 10" source size drives column densities
- Caveat (inferred, ours): Many fixed Trot for single-line molecules

## Reproducibility

- Data public (paper): ALMA SV data public; Effelsberg data not stated as public  
  > "The data are available to the public and can be accessed from the ALMA-SV website" (2.2 Archival data)
- Products in archive: _not stated_
- Missing: Effelsberg raw data access
- Missing: ALMA imaging parameters and CASA version
- Data volume (inferred): Effelsberg spectra small; ALMA SV Orion KL ~tens to hundreds of GB
- Score (inferred): 3/5, ALMA part is minor and thinly described; main data from Effelsberg not obviously public.
- Rediscovery candidate: no, Main results rely on Effelsberg data; ALMA role is qualitative.

## Links

- Companion: (cite: 2014ApJ...787..112C) (Source sizes and H2 columns, previous ALMA-SV analysis)
- Companion: (cite: 2015A&A...574A..56G) (Same Effelsberg K-band survey method for IRC +10216)
- Related: ALMA Science Verification Orion KL
- Related: GBT PRIMOS

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 44,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
