# ALMA twenty-six arcmin<SUP>2</SUP> survey of GOODS-S at one millimeter (ASAGAO): Source catalog and number counts

`2018PASJ...70..105H` | Publications of the Astronomical Society of Japan 2018 | first author: Hatsukade, Bunyo | arXiv: 1808.04502 | DOI: 10.1093/pasj/psy104

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Build the ASAGAO 1.2 mm source catalog, number counts and IR luminosity functions to measure the resolved EBL fraction and obscured star formation at z~2  
  > "The primary goal of this survey is to obtain a census of galaxies with $L_{\rm IR} \gtrsim 3 \times 10^{11}$ $L_{\odot}$ or SFR $\gtrsim 50$ $M_{\odot}$ yr$^{-1}$" (Introduction)
- Target **GOODS-S field (ASAGAO region)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00098.S, 2012.1.00173.S, 2015.1.00543.S
- bands: Band 6 (1.2 mm)  
  > "ALMA band 6 observations of the GOODS-S field were conducted in September 02–29, 2016" (2.1 Observations)
- frequencies and spectral setup: Two tunings at 262.56 GHz and 253.56 GHz; TDM; 4 spws of 2000 MHz (15.625 MHz x 128 channels) each  
  > "The center frequencies of the tunings are 262.56 GHz (1.14 mm) and 253.56 GHz (1.18 mm)" (2.1 Observations); "a spectral window (spw) was placed for each baseband with a bandwidth of 2000 MHz (15.625 MHz $\times$ 128 channels)" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-6, 37 execution blocks  
  > "The observations were done in 37 execution blocks in the C40-6 array configuration" (2.1 Observations)
- baselines: 15.065 m to 1770-3247 m  
  > "with a minimum baseline length of 15.065 m and a maximum baseline length ranging from 1770 m to 3247 m" (2.1 Observations)
- angular resolution: 0.51" x 0.45" (ASAGAO, 250 kλ taper); 0.59" x 0.53" (combined)  
  > "a synthesized beam size of $0.59\ensuremath{''} \times 0.53\ensuremath{''}$" (abstract)
- max recoverable scale: ~1.2 arcsec  
  > "maximum recoverable scale of $\theta_{\rm MRS} \approx 1.2\ensuremath{''}$" (2.1 Observations)
- sensitivity: 1σ ~61 µJy/beam (ASAGAO); ~30 µJy/beam combined deep region  
  > "$1\sigma \sim 30$ $\mu$Jy beam$^{-1}$ for a deep region with a 250 k$\lambda$-taper" (abstract)
- time on source: 45 h total; 29 h on source  
  > "The total observing time is 45 hours, and the on-source integration time is 29 hours." (2.1 Observations)
- observing dates: September 02–29, 2016  
  > "conducted in September 02–29, 2016 for the Cycle 3 program" (2.1 Observations)
- pi or archival as stated: _not stated_
- Other facility **ZFOURGE (FourStar)**: Ks-band counterparts and redshifts  
  > "We identify $K_S$-band selected sources from the catalog of the `FourStar` galaxy evolution survey" (5.1 IR Luminosity Function of ASAGAO Sources)
- Other facility **VLA 5 cm**: astrometry check  
  > "the positions of the 5$\sigma$ sources are cross-matched with sources detected in the VLA 5-cm survey" (4.2 Astrometry)
- External data: HUDF 1.3 mm and GOODS-ALMA 1.1 mm archival uv data combined with ASAGAO  
  > "The archival data sets of HUDF (cite: dunl17) and GOODS-ALMA (cite: fran18) are combined to the original ASAGAO data" (2.4 Combined Map) [from (cite: dunl17); (cite: fran18)]
- External data: Redshifts and IR luminosities from SED fitting  
  > "The counterpart identification and SED fitting are described in detail in (cite: yama18), and here we just give a brief explanation." (5.1 IR Luminosity Function of ASAGAO Sources) [from (cite: yama18)]
- External data: EBL at 1.2 mm from Planck  
  > "The EBL at 1.2 mm (243 GHz) is estimated from the measurements by the *Planck* satellite (cite: plan14)" (3.4 Contribution to Extragalactic Background Light) [from (cite: plan14)]
- External data: LFs and number counts from other works for comparison and fits  
  > "In figure [7](#fig:lf), we plot their data points and the best-fitting function determined in the redshift bin of $1.5 < z < 2.5$" (5.2 Comparison with Previous Studies) [from (cite: kopr17)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-4008 and J2357-5311  
  > "J0334$-$4008 and J2357$-$5311 were observed as flux calibrators." (2.1 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 250 kλ (also untapered and 160 kλ)  
  > "We adopt an $uv$-taper of 250 k$\lambda$ to weight extended components" (2.4 Combined Map)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Data averaged to 32 channels (0.5 GHz) and 10.08 s  
  > "we average the data in frequency and time directions with 32 channels ($\Delta \nu = 0.5$ GHz) and 10.08 sec, respectively" (2.2 Data Reduction)
- final beam: 0.59" x 0.53" combined, 250 kλ taper  
  > "which gives a final synthesized beam size of $0.59\ensuremath{''} \times 0.53\ensuremath{''}$" (2.4 Combined Map)
- final rms: _not stated_

### Inherited from earlier work

- Combined map made with same imaging parameters as the original ASAGAO map (parameters in a section not included in text)  
  > "The combined map was produced with CASA with the same parameters adopted in Sec [\[subsec:reduction\]]" (2.4 Combined Map) [from Sec. 2.2 (subsec:reduction)]
- Counterpart identification and SED fitting  
  > "The counterpart identification and SED fitting are described in detail in (cite: yama18)" (5.1 IR Luminosity Function of ASAGAO Sources) [from (cite: yama18)]
- Vmax with nonuniform noise  
  > "Following the description of (cite: nova17), where they construct radio LFs taking into account a nonuniform noise in their radio maps" (5.1 IR Luminosity Function of ASAGAO Sources) [from (cite: nova17)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (robust, deconvolver, cell, image size, masking, threshold)
- CASA version and calibration procedure
- BANE/Aegean parameters
- fit procedure and priors for Schechter fits
- SED-based S_i(z) details
- coordinates of the field centre

## Analysis recipe

1. **Image and combine data**: Average in frequency and time, relabel J2000 to ICRS for Cycle 1-2 data, combine with archival data, image with CASA with 250 kλ taper  
  > "we relabel the coordinates of Cycle 1 and 2 data from J2000.0 to the International Celestial Reference System (ICRS) by using a CASA script offered by the ALMA project" (2.4 Combined Map)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect sources and measure fluxes**: Aegean source finder on signal map with BANE noise estimation; 2D elliptical Gaussian fits; Sint = Speak ab/(θmaj θmin)  
  > "We adopt the source-finding algorithm called Aegean (cite: hanc12; hanc18), which achieves high reliability and completeness performance for radio maps." (3.1 Source Detection)
   - software: Aegean, BANE
   - parameter: Detection threshold peak SN >= 4.5 (25 sources at >=5σ)  
  > "We find 25 (45) sources with a peak SN of $\ge$5$\sigma$ ($\ge$4.5$\sigma$)." (3.1 Source Detection)
   - fitting: 2D elliptical Gaussian  
  > "The detected sources are fitted with a 2D elliptical Gaussian to estimate the source size and integrated flux density." (Source Catalog, Source Detection)
   - validation: Negative-peak counts for spurious sources; radio cross-match for astrometry  
  > "The actual number of negative peaks in the combined map is 1 at $\ge$5$\sigma$ and 8 at 4.5–5$\sigma$." (3.1 Source Detection)
3. **Completeness and flux boosting**: Inject 30000 artificial Gaussian sources (0.05-2 mJy, convolving beam 0.01-0.5") and recover  
  > "We input 30000 artificial sources into the signal map one at a time, each with an integrated flux density randomly selected from 0.05–2 mJy" (4.1 Completeness and Flux Boosting)
   - fitting: _not stated_
   - validation: _not stated_
4. **Number counts and EBL fraction**: dN/dS corrected for spurious fraction, effective area, completeness; Poisson errors (Gehrels); Schechter fit; integrate and compare with Planck EBL  
  > "The differential number counts obtained in this study and previous studies are fitted to a Schechter function" (4.2 1.2mm Number Counts)
   - assumption: Modified blackbody beta=1.5, T=35 K, z=2 for scaling 870 µm to 1.2 mm  
  > "Here we assume a modified black body with a dust emissivity index of $\beta = 1.5$, dust temperature of 35 K, and $z = 2$." (4.2 1.2mm Number Counts)
   - fitting: _not stated_
   - validation: Compared with previous ALMA number counts  
  > "We find that our number counts are consistent with those of the previous ALMA blank-field surveys." (Number Counts, Comparison with Previous ALMA Studies)
5. **IR luminosity functions and SFRD**: Vmax method with 5σ sources with ZFOURGE counterparts; Schechter fit at 1.5<z<2.5 together with Koprowski+17; SFRD via Kennicutt 1998 relation  
  > "To construct the LFs, we adopt the $V_{\rm max}$ method (cite: schm68)." (5.1 IR Luminosity Function of ASAGAO Sources)
   - software: magphys
   - parameter: Δlog L = 0.6; bins 1.0<z<2.0, 1.5<z<2.5, 2.0<z<3.0  
  > "We adopt a luminosity bin width of $\Delta\log{(L)} = 0.6$." (5.1 IR Luminosity Function of ASAGAO Sources)
   - assumption: Chabrier IMF; H0=70, OmegaM=0.3, OmegaL=0.7  
  > "we adopt a cosmology with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm{M}}=0.3$, and $\Omega_{\Lambda}=0.7$" (Introduction)
   - fitting: Schechter function fit; method not further specified  
  > "We fit the IR LFs at $1.5 < z < 2.5$ obtained from the ASAGAO sources and the results of (cite: kopr17) with a Schechter function of the form of equation" (Luminosity Function, Comparison with Previous Studies)
   - validation: Compared with Koprowski+17 and Herschel LFs  
  > "We find that the ASAGAO LFs are consistent with those of (cite: kopr17) within the errors, supporting the evolution of LFs derived in (cite: kopr17)" (Luminosity Function, Comparison with Previous Studies)

## Software

- **CASA** : Imaging and ICRS relabel of data  
  > "The combined map was produced with CASA with the same parameters" (2.4 Combined Map)
- **Aegean** : Source finding  
  > "We adopt the source-finding algorithm called Aegean (cite: hanc12; hanc18)" (3.1 Source Detection)
- **BANE** : Background and noise estimation  
  > "The background and noise estimation are done with the BANE package" (3.1 Source Detection)
- **magphys** : SED fitting for IR luminosities  
  > "SED fitting with the magphys model (cite: dacu08; dacu15) is performed." (5.1 IR Luminosity Function of ASAGAO Sources)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of sources at >=5σ | 25 | not stated | sources | 2 | We find 25 (45) sources with a peak SN of $\ge$5$\sigma$ ($\ge$4.5$\sigma$). |
| Number of sources at >=4.5σ | 45 | not stated | sources | 2 | We find 25 (45) sources with a peak SN of $\ge$5$\sigma$ ($\ge$4.5$\sigma$). |
| Integrated counts at S1.2mm>135 µJy | 7.7 | +1.7/-1.2 | Jy deg^-2 | 4 | yields $7.7^{+1.7}_{-1.2}$ Jy deg$^{-2}$ ($S_{\rm 1.2mm} > 135$ $\mu$Jy) |
| EBL at 1.2 mm (Planck interpolation) | 15.1 | 0.59 | Jy deg^-2 | 4 | the EBL at 1.2 mm is calculated to be $15.1 \pm 0.59$ Jy deg$^{-2}$ |
| Resolved EBL fraction | 52 | +11/-8 | % | 4 | We find that $52^{+11}_{-8}$% of the EBL at 1.2 mm is resolved into discrete sources in the ASAGAO map. |
| Completeness at SN=4.5 | 60 | not stated | % | 3 | The completeness is 60% at SN $= 4.5$, and 100% at SN $\gtrsim 7$. |
| Faint-end slope alpha of IR LF at 1.5<z<2.5 | -0.22 | 0.28 | dimensionless | 5 | The derived spectral slope of $\alpha = -0.22 \pm 0.28$ is flatter than $\alpha = -0.4$ |
| SFRD from integrated LF down to log L_IR=11.78 | 7.2e-2 | +3.0/-1.9 (x10^-2) | Msun yr^-1 Mpc^-3 | 5 | gives a SFRD of $7.2^{+3.0}_{-1.9} \times 10^{-2}$ $M_{\odot}$ yr$^{-1}$ Mpc$^{-3}$ |

## Qualitative findings

- ASAGAO number counts consistent with previous ALMA blank-field surveys  
  > "We find that our number counts are consistent with those of the previous ALMA blank-field surveys." (3.3 Comparison with Previous ALMA Studies)

## Claim tuples

- H: What fraction of the 1.2 mm EBL is resolved at ~0.1 mJy? | E: Integrate ASAGAO differential number counts and compare with Planck EBL | R: 52 +11/-8 % resolved at S>135 µJy | F: About half of the EBL is resolved into discrete sources | **supported**
- H: Do ASAGAO IR LFs agree with earlier results and the claimed evolution? | E: Vmax LFs in three z bins compared with Koprowski+17 | R: Consistent within errors | F: Supports positive luminosity and negative density evolution, though uncertainties are large | **partially**
- H: How much of the z~2 cosmic SFRD is from sources with log LIR>~11.8? | E: Integrate best-fit LF and convert to SFRD | R: SFRD 7.2e-2 Msun/yr/Mpc^3, ≈60–90% of total | F: Obscured star formation dominates z~2 SFRD | **supported**

## Reasoning

- Why this data: Contiguous blank-field survey avoids biases of serendipitous source samples  
  > "It is necessary to conduct “unbiased” surveys in a contiguous field rather than collecting discrete fields in order to obtain a census on the population of faint submm sources." (Introduction)
- Why this method: _not stated_
- Alternative: ASPECS data not combined because its synthesized beam is very different  
  > "We do not use the data set of ASPECS, where the synthesized beam size ($1.68\ensuremath{''} \times 0.92\ensuremath{''}$) is largely different" (2.3 ALMA Archival Data)
- How they decided it was enough: _not stated_
- Limitation (authors): Small LF sample and limited luminosity coverage prevent discussion of evolution  
  > "the large uncertainties of our LFs due to the small sample size and the limited coverage of IR luminosity do not allow us to further discuss the density/luminosity evolution" (5.2 Comparison with Previous Studies)
- Caveat (inferred, ours): Completeness depends on assumed source size distribution
- Caveat (inferred, ours): Only 5σ sources with Ks counterparts used for LFs, so incompleteness at high z
- Caveat (inferred, ours): Spurious fraction from negative peaks assumes symmetric noise

## Reproducibility

- Data public (paper): Archival ALMA data used with project codes given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00098.S, #2012.1.00173.S, and #2015.1.00543.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean parameters
- Missing: CASA version
- Missing: Aegean/BANE settings
- Missing: LF fit details
- Missing: SED fit outputs (Yamaguchi+18)
- Data volume (inferred): ~1-3 TB raw for three projects
- Score (inferred): 3/5, Data public and methods outlined, but imaging parameters are deferred to an omitted section and key fit details are missing.
- Rediscovery candidate: no, Imaging recipe incomplete and LF relies on external SED results.

## Links

- Method: (cite: hanc12; hanc18) (Aegean source finder)
- Method: (cite: nova17) (Vmax with nonuniform noise)
- Companion: (cite: yama18) (Multiwavelength counterparts and SED fitting)
- Companion: (cite: ueda18) (X-ray AGN properties)
- Companion: (cite: fuji18) (Morphology of ASAGAO sources)
- Related: HUDF ALMA survey
- Related: GOODS-ALMA
- Related: ASPECS
- Related: SXDF-ALMA

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 46,
  "rate": 0.59
 },
 "evidence_ok": true
}
```
