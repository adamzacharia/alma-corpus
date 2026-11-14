# Reconstructing the EUV Spectrum of Star-forming Regions from Millimeter Recombination Lines of H I, He I, and He II

`2020ApJ...903...29M` | The Astrophysical Journal 2020 | first author: Murchikova, Lena | arXiv: 2006.15153 | DOI: 10.3847/1538-4357/abb67c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Can the EUV spectrum (13.6-54.4 eV slope and above) of star-forming regions be reconstructed from mm recombination lines H30a, He30a and He+48a, and does it agree with Starburst99 and BPASS models?  
  > "We compare the inferred values of the EUV spectral slopes with the values expected for a purely single stellar evolution model (Starburst99) and the Binary Population and Spectral Synthesis code (BPASS)." (abstract)
- Target **G330.9536**: coordinates 16:09:52.60 -51:54:55  
  > "G330.9536 | 16:09:52.60 | -51:54:55 |  5.5 kpc" (Table 1); z/distance 5.5 kpc  
  > "G330.9536 | 16:09:52.60 | -51:54:55 |  5.5 kpc" (Table 1); distance from _not stated_
- Target **G332.8254**: coordinates 16:20:11.00 -50:53:16  
  > "G332.8254 | 16:20:11.00 | -50:53:16 |  4.4 kpc" (Table 1); z/distance 4.4 kpc  
  > "G332.8254 | 16:20:11.00 | -50:53:16 |  4.4 kpc" (Table 1); distance from _not stated_
- Target **Sgr B2(M)**: coordinates 17:47:20.15 -28:23:05  
  > "SgrB2(M)  | 17:47:20.15 | -28:23:05 |  8.3 kpc" (Table 1); z/distance 8.3 kpc  
  > "SgrB2(M)  | 17:47:20.15 | -28:23:05 |  8.3 kpc" (Table 1); distance from _not stated_
- Target **G328.8076**: coordinates 15:55:48.60 -52:43:07  
  > "G328.8076 | 15:55:48.60 | -52:43:07 | 11.7 kpc" (Table 1); z/distance 11.7 kpc  
  > "G328.8076 | 15:55:48.60 | -52:43:07 | 11.7 kpc" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00111.S, 2016.1.01015.S
- bands: Band 6  
  > "were observed simultaneously in one tuning of ALMA in Band 6 with two spectrometers with a velocity resolution of $2.5 \, \mathrm{km \, s^{-1}}.$" (3 Observations and Data reduction)
- frequencies and spectral setup: Line windows with 2.5 km/s resolution; three continuum windows at 232.8, 232.3, 229.9 GHz with 40 km/s resolution  
  > "The other three spectral windows were set to observe the continuum at 232.8 GHz, 232.3 GHz and 229.9 GHz with a velocity resolution of 40 $\mathrm{km \, s^{-1}}.$" (3 Observations and Data reduction)
- continuum bandwidth: _not stated_
- arrays: 38, 30 antennas (Cycle 2); 47-50 antennas (Cycle 4)  
  > "on June 16, 2015 (Sgr B2(M)) with 30 antennas and achieved resolution $0.53'' \times 0.47''.$" (3 Observations and Data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Cycle 2: 0.53''x0.47'' (1.24''x0.93'' for the first Sgr B2(M) run); Cycle 4: ~0.3''x0.28''  
  > "The achieved resolution was $\sim 0.3''\times 0.28''.$" (3 Observations and Data reduction)
- max recoverable scale: ~3.5'' (Cycle 4)  
  > "Maximum recoverable scale of the emission is $\sim 3.5''.$" (3 Observations and Data reduction)
- sensitivity: Cycle 2: 2 mJy/beam; Cycle 4: 0.4 mJy/beam in a 10 km/s channel  
  > "Achieved sensitivity is 0.4 mJy/beam in a 10 $\mathrm{km \, s^{-1}}$ velocity channel in each source." (3 Observations and Data reduction)
- time on source: Cycle 2: 9 min per G-source, 18 min Sgr B2(M); Cycle 4: ~120 min per target  
  > "The exposure times on target were 9 min on each of the G-sources and 18 minutes total on Sgr B2(M)." (3 Observations and Data reduction); "The total exposure time on each target was $\sim$120 min." (3 Observations and Data reduction)
- observing dates: Cycle 2: 2015 Apr 23, Apr 24, Apr 27, Jun 16; Cycle 4: 2017 May 6, 7, 8  
  > "The observations of G330.9536 and G332.8254 in ALMA Cycle 4 were conducted on May 6 and 8, 2017 with 47 antennas and May 7, 2017 with 50 antennas." (3 Observations and Data reduction)
- pi or archival as stated: _not stated_
- Line: HI H30alpha n=31->30 (231.901 GHz)
- Line: HeI He30alpha n=31->30 (231.995 GHz)
- Line: HeII He+48alpha n=49->48 (230.713 GHz)
- External data: Line emissivities of H30a, He+48a at n~1e4 cm-3, T~1e4 K  
  > "are (cite: sto95a; sto95):" (2 Theory) [from Storey & Hummer 1995 (cite: sto95a; sto95)]
- External data: Effective charge Z_eff=1.0002 for He30a emissivity scaling  
  > "assume $Z_\mathrm{eff}= 1.0002$ for the effective charge of the nucleus (cite: Towle96)" (2 Theory) [from Towle96]
- External data: Target selection and classification of the ultra-compact HII regions  
  > "The three ultra-compact HII regions are taken from the survey of (cite: 2010MNRAS.405.1560M)." (3 Observations and Data reduction) [from 2010MNRAS.405.1560M]
- Simulation/model as data: Starburst99 v7.0.1 and BPASS v2.2.1 instantaneous 1e3 Msun starburst spectra, Z=0.02 (Z=0.014 for Geneva v00/v40)  
  > "We compare this observational result with model spectra of an instantaneous $10^3 M_{\odot}$ starburst obtained with (i) Starburst99 v7.0.1" (5 Discussion)

## Processing

### Calibration

- pipeline or manual: Cycle 2: NAASC staff scripts; Cycle 4: ALMA pipeline script from NAASC  
  > "We used the calibration and data reduction scripts prepared by the staff at North American ALMA Science Center (NAASC) in Charlottesville, Virginia." (3 Observations and Data reduction); "For calibration and data reduction we used the script automatically generated by the ALMA pipeline provided by the NAASC." (3 Observations and Data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean (Cycle 4); CASA CLEAN (Cycle 2)  
  > "We imaged the data using the task `tclean` in CASA." (3 Observations and Data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: Cycle 2: 0.08''; Cycle 4: 0.028''  
  > "The images created were $500\times 500$ pixel with the pixel size $0.08''.$" (3 Observations and Data reduction)
- image size: Cycle 2: 500x500 pix; Cycle 4: 1000x1000 pix  
  > "The images created were $1000\times 1000$ pixel with the pixel size $0.028''.$" (3 Observations and Data reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA using carefully identified line-free channels  
  > "we performed subtraction of the continuum in the uv-plane with the `uvcontsub` task in CASA using the identified channels" (4 Data analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Theory of recombination line emission measures and emissivity scaling  
  > "we can use scaling relation $\varepsilon_{\mathrm{He}\, \mathrm{n}\alpha }(T,n) \simeq Z_\mathrm{eff}^{17/3} \varepsilon_{\mathrm{H}\mathrm{n}\alpha }(T,n)$ derived in SM13 Appendix C" (2 Theory) [from Scoville & Murchikova 2013 (cite: 2013ApJ...779...75S)]

### Not stated but needed to reproduce (our reading)

- tclean weighting/robust, deconvolver, threshold, masking
- CASA version
- line-free channel ranges used for uvcontsub
- exact extraction regions (coordinates/sizes) for sub-regions
- Gaussian/Voigt fitting setup and code
- flux calibrator and flux scale uncertainty
- how He+48a upper limits were computed (confidence level)
- BPASS/Starburst99 input parameters (IMF, etc.)
- how <gamma> and its 0.4 uncertainty were averaged

## Analysis recipe

1. **Image and subtract continuum**: Image with CASA, identify line-free channels, uv-plane continuum subtraction to get line and continuum cubes  
  > "Then we performed subtraction of the continuum in the uv-plane with the `uvcontsub` task in CASA using the identified channels to obtain separate continuum and line images" (4 Data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract spectra and fit recombination lines**: Spectra from sub-regions and tot_H30a region; fit Gaussian/Voigt profiles to get V, DeltaV and integrated flux, excluding molecular lines; HI fitted first and subtracted when HeI sits on its wing  
  > "we fitted the spectra with a combination of Gaussian and Voigt profiles and then used the fit to extract central velocity ($V$) of the H30$\alpha$ and He30$\alpha$ lines" (4 Data analysis)
   - fitting: Gaussian and Voigt profile fits  
  > "we fitted the spectra with a combination of Gaussian and Voigt profiles" (4 Data analysis)
   - validation: _not stated_
3. **He+48a flux limit**: Assume V and width equal to He30a and fit the expected profile to uncontaminated data points  
  > "we use the width and the velocity of He30$\alpha$ lines to obtain the expected He$^+$48$\alpha$ profile which we then fit under the uncontaminated spectral data points" (4 Data analysis)
   - assumption: V(He+48a)=V(H30a)~V(He30a); DeltaV(He+48a)=DeltaV(He30a)  
  > "we assume that $V_\mathrm{He^+48\alpha } = V_\mathrm{H30\alpha } \simeq V_\mathrm{He30\alpha }$ and $\Delta V_\mathrm{He^+48\alpha } = \Delta V_\mathrm{He30\alpha }.$" (4 Data analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive EM, Q and EUV slopes**: Convert line fluxes to emission measures (eq. SdVtoEM), then to Q0,Q1,Q2 via recombination coefficients, then solve for gamma, L0, gamma_2 of a broken power law  
  > "Using eq. [\[a\]] we can solve for $\gamma$, which we then substitute it into the rest of the equations to find $L_0, \, L_2$ and $\gamma_2,$" (2 Theory)
   - assumption: Radiation equilibrium, no EUV photon escape, no photon stealing by lower-threshold species; T=1e4 K  
  > "we assume (i) that the gas is in a radiation equilibrium, so that the number of recombinations of each ion species is equal to the number of ionizations" (Appendix)
   - fitting: _not stated_
   - validation: Error propagation: ~4% on gamma for Cycle 4, ~10% Sgr B2(M); ~20% true uncertainty due to approximate equations  
  > "Since the equations are approximate, we expect the true uncertainties on the derived spectral parameters to be $\sim 20 \%.$" (4 Data analysis)
5. **Compare with population synthesis models**: Compare gamma and Q with Starburst99 v7.0.1 and BPASS v2.2.1 (binary and single) for 1e3 Msun instantaneous starburst as a function of age  
  > "We scale the simulations to $10^3 M_{\odot}$ so that the production rate of $h\nu > 13.6 \, \mathrm{eV}$ photons ($Q_0$) predicted by the models is similar to the observed values" (5 Discussion)
   - software: Starburst99, BPASS
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Imaging, CLEAN/tclean, uvcontsub  
  > "We imaged and CLEANed the data using the Common Astronomy Software Applications package (CASA)." (3 Observations and Data reduction)
- **Starburst99** v7.0.1: Model EUV spectra for comparison  
  > "We use BPASS v2.2.1 and Starburst 99 v7.0.1." (1 Introduction)
- **BPASS** v2.2.1: Binary and single star model EUV spectra for comparison  
  > "We use BPASS v2.2.1 and Starburst 99 v7.0.1." (1 Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| EUV spectral slope gamma (13.6-54.4 eV) | 4.5 | 0.4 | dimensionless | 4 | $L_{\nu}\propto \nu^{-4.5 \pm 0.4}.$ |
| gamma_2 (>54.4 eV) | >15 | lower limit | dimensionless | 4 | where $\gamma_2>15$ |
| gamma, G330.9536 tot_H30a | 4.3 | not stated | dimensionless | 4 | tot$_\mathrm{H30\alpha }$ / 7.01 / -89.7 / 35.2 / 485.04 / 12.93 / 33.49 |
| gamma, G328.8076 | ~7.5 | unreliable | dimensionless | 4 | The spectral slope $\gamma$ obtained for G328.8076 is $\sim 7.5$. |
| model slope for <7 Myr starburst | ~3 | not stated | dimensionless | 5 | $\gamma_\mathrm{sin} \simeq \gamma_\mathrm{bin} \simeq 3$ |
| temperatures from continuum+line | 5,000-12,000 | highly uncertain | K | 2 | The temperature estimates for the observed extraction regions obtained this way are between 5,000 K to 12,000 K |

## Qualitative findings

- All four regions show similar EUV slopes irrespective of evolutionary stage; HeII recombination line not detected in any target.  
  > "The HeII recombination line was not detected in any of our targets." (4 Data analysis)

## Claim tuples

- H: mm H/He recombination lines can reconstruct EUV spectral slopes | E: ALMA Band 6 observations of H30a, He30a, He+48a in four HII regions | R: gamma = 4.5 +/- 0.4 in all reliable regions | F: Technique yields EUV spectral slopes | **supported**
- H: Observed slopes match Starburst99 and BPASS | E: Compare gamma with model slopes vs age | R: Observed slopes steeper than ~3 for <7 Myr; between models for older ages | F: Observations differ from models; binary fraction possibly lower than in BPASS | **supported**
- H: Metallicity could explain the discrepancy | E: Vary BPASS metallicity | R: Variations obvious but insufficient | F: Metallicity alone cannot account for it | **supported**

## Reasoning

- Why this data: Lines chosen to be observable simultaneously in ALMA Band 6 and avoid molecular line confusion  
  > "H30$\alpha ,$ He30$\alpha ,$ and He$^+48\alpha$ lines can be observed simultaneously with ALMA Band 6 making them our preferred choice." (3 Observations and Data reduction)
- Why this method: _not stated_
- Alternative: Ages of all regions being the same (~2.5 Myr) was ruled out  
  > "We rule out this possibility." (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Molecular line contamination dominates flux accuracy; G328.8076 slope unreliable; ages unknown; photon escape in evolved regions  
  > "The accuracy of determining $[S\Delta V],$ $V$ and $\Delta V$ is dominated by molecular lines contamination, which is hard to quantify." (4 Data analysis)
- Caveat (inferred, ours): Sub-regions of the same HII region treated as independent probes
- Caveat (inferred, ours): Slope uncertainty dominated by model assumptions, not propagated statistically
- Caveat (inferred, ours): Dust absorption of EUV photons and photon stealing neglected
- Caveat (inferred, ours): Only three sources give reliable slopes; age unknown so model comparison is ambiguous

## Reproducibility

- Data public (paper): Project codes given in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00111.S and ADS/JAO.ALMA#2016.1.01015.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: tclean parameters
- Missing: line-free channels
- Missing: extraction region definitions
- Missing: CASA version
- Data volume (inferred): ~50-100 GB raw for two projects
- Score (inferred): 3/5, Analytic equations are fully given and data available, but imaging parameters and extraction regions are unspecified.
- Rediscovery candidate: yes, Public data, explicit equations, and numeric results in Table 1, though imaging details are loosely specified.

## Links

- Method: Scoville & Murchikova 2013 (cite: 2013ApJ...779...75S) (Theory of mm recombination lines as EUV probes)
- Related: Starburst99
- Related: BPASS

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 44,
  "rate": 0.55
 },
 "evidence_ok": true
}
```
