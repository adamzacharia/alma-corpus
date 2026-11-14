# SXDF-ALMA 2 arcmin<SUP>2</SUP> deep survey: Resolving and characterizing the infrared extragalactic background light down to 0.5 mJy

`2016PASJ...68...82Y` | Publications of the Astronomical Society of Japan 2016 | first author: Yamaguchi, Yuki | arXiv: 1607.02331 | DOI: 10.1093/pasj/psw073

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, cosmology
- Question: What do the faint 1.1 mm ALMA sources in a 2 arcmin^2 field contribute to the infrared extragalactic background light and cosmic SFRD, and what are their stellar and star-forming properties (main sequence vs starburst)?  
  > "However, it is not understood whether faint SMGs are on or above the main sequence because the stellar masses of these faint SMGs have not yet been measured." (Introduction)
- Target **SXDF-UDS-CANDELS field (SXDF-ALMA1-5)**: coordinates not stated (blank in text)  
  > "The 2 arcmin$^2$ map of the SXDF-UDS-CANDELS field was obtained at 274 GHz (or 1.1 mm; Band 6)." (2.1 ALMA observations and source identifications); z/distance z_photo ~1.3-2.5; ALMA1 and 2 narrowband z=2.53±0.02  
  > "The 2 arcmin$^2$ map of the SXDF-UDS-CANDELS field was obtained at 274 GHz (or 1.1 mm; Band 6)." (2.1 ALMA observations and source identifications); distance from EAZY photometric redshifts; Halpha narrowband redshifts (Tadaki et al. 2013)  
  > "The 2 arcmin$^2$ map of the SXDF-UDS-CANDELS field was obtained at 274 GHz (or 1.1 mm; Band 6)." (2.1 ALMA observations and source identifications)

## Data provenance

- ALMA projects: 2012.1.00756.S
- bands: Band 6 (1.1 mm, 274 GHz)  
  > "obtained at 274 GHz (or 1.1 mm; Band 6)" (2.1 ALMA observations and source identifications)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: close to C32-4; 19 pointings; 30-32 antennas  
  > "30–32 antennas were employed, and the array was close to the C32-4 configuration" (2.1 ALMA observations and source identifications)
- baselines: 20-650 m  
  > "which has minimum and maximum baselines of 20 and 650 m, respectively" (2.1 ALMA observations and source identifications)
- angular resolution: 0.53 x 0.41 arcsec (natural weighting)  
  > "the synthesized beam is 0.53 arcsec $\times$ 0.41 arcsec" (2.1 ALMA observations and source identifications)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma 0.048-0.061 mJy/beam, typical 0.055  
  > "the typical noise level was 0.055 mJy beam$^{-1}$" (2.1 ALMA observations and source identifications)
- time on source: _not stated_
- observing dates: July 17 and 18, 2014 (Cycle 1)  
  > "The ALMA observations were carried out on July 17 and 18, 2014 (Cycle 1)." (2.1 ALMA observations and source identifications)
- pi or archival as stated: _not stated_
- Other facility **Subaru, VLT/HAWK-I, HST, Spitzer, Herschel, VLA/JVLA, XMM-Newton**: Archival optical-to-radio photometry for counterparts  
  > "we used archival optical-to-near-infrared images collected by ground-based and space-borne facilities" (2.2 Optical-to-near-infrared images)
- External data: Narrowband Halpha redshifts of ALMA1 and 2 (z=2.53±0.02)  
  > "having narrowband redshifts of $z=2.53\pm0.02$" (3.1) [from (cite: tadaki2013)]
- External data: Total COBE infrared EBL value used for fractions  
  > "obtained by (cite: fixsen1998) using the COsmic Background Explore (COBE) satellite" (5.1) [from (cite: fixsen1998)]
- External data: Herschel infrared SFRD for comparison  
  > "average infrared SFRD at $0.9<z<3.6$ as estimated by *Herschel* (cite: brugarella2013)" (5.2) [from (cite: brugarella2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2258-279 and J0238+166 (phase J0215-0222, bandpass J0241-0815)  
  > "The flux was calibrated with J2258-279 and J0238+166." (2.1)
- flux scale uncertainty: 10% for Band 6  
  > "The absolute calibration accuracy for Cycle 1 is 10% for Band 6" (2.1)
- self calibration: _not stated_

### Imaging

- task: CLEAN (Högbom) in CASA  
  > "The map was processed with the `CLEAN` algorithm (cite: hogdom1974) using natural weighting." (2.1)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting" (2.1)
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

- ALMA data details, source extraction (S/N>5) and fluxes  
  > "the details will be given in a subsequent paper (cite: tadaki2015; kohno2016; hatsukade2016)" (2.1) [from (cite: kohno2016); (cite: hatsukade2016)]
- Aperture correction procedure  
  > "We corrected the aperture correction using the same procedure described by (cite: ono2010)." (3.1) [from (cite: ono2010)]
- tau>=300 Myr in FAST fitting  
  > "Following the recipe presented by (cite: wuyts2011), we used the $e$-folding timescale of SFRs $\tau\geq300$ Myr for fitting." (4.1.2) [from (cite: wuyts2011)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details (pipeline vs manual)
- Imaging parameters: cell, image size, masking, clean threshold, continuum channels
- Source extraction and flux measurement method for 1.1 mm total fluxes (deferred to Kohno et al.)
- Primary-beam correction details
- FAST grid parameters
- Source coordinates
- How EBL contribution uncertainty was computed beyond Poisson

## Analysis recipe

1. **Image ALMA map and extract sources**: CLEAN with natural weighting; sources with S/N>5 extracted  
  > "we extracted five significant sources with a signal-to-noise ratio of S/N $> 5$ (cite: kohno2016)" (2.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Multi-wavelength photometry of counterparts**: PSF-match to 1 arcsec Gaussian (IRAC to 2.2 arcsec); 2 arcsec aperture photometry with aperture correction to 5 arcsec; HIPE for SPIRE; JMFIT for radio  
  > "we performed optical-to-near-infrared photometry with a 2 arcsec diameter aperture at the position of the ALMA sources using the `IRAF` task `APPHOT`." (3.1)
   - software: IRAF, SDFRED, HIPE, AIPS
   - fitting: _not stated_
   - validation: _not stated_
3. **Photometric redshifts**: HYPERZ and EAZY chi2 fitting, z=0-7, Av=0-5, Calzetti law, BC93/BC03 templates  
  > "The redshift range was set to $z=$ 0–7. Extinction is considered with the range of $A_{\rm V}=$ 0–5 mag in increments of 0.5 mag" (4.1.1)
   - software: HYPERZ, EAZY
   - fitting: chi2 minimization; 99% confidence intervals from posterior  
  > "Throughout this paper, we use the 99% confidence intervals to represent the uncertainty of the photometric redshift estimates" (4.1.1)
   - validation: HYPERZ and EAZY agreed within errors; consistent with narrowband z for ALMA1, 2  
  > "The photometric redshifts estimated by `HYPERZ` and `EAZY` agreed within the errors" (4.1.1)
4. **Stellar masses**: FAST SED fitting with BC03, solar metallicity, Chabrier IMF, Calzetti, exponentially declining SFH; ALMA3 from rest-frame H-band M/L=0.15  
  > "Here, we assumed the Chabrier initial mass function (cite: chabrier2003), the Calzetti extinction law, and exponentially declining star formation histories." (4.1.2)
   - software: FAST
   - assumption: M*/L_H = 0.15 Msun/Lsun for ALMA3  
  > "Here, we adopted the average value $M_*/L_H = 0.15\ \MO\ \LO^{-1}$ of these two extreme cases." (4.1.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **LIR and SFR**: Dale & Helou templates scaled to 1.1 mm flux, integrated 8-1000 um, averaged over Tdust 20-35 K; SFR_UV+IR via Kennicutt  
  > "We assumed the dust temperatures $T_\mathrm{dust}$ = 20–35 K (for SXDF-ALMA4, $T_\mathrm{dust}$ = 20–30 K; see Appendix for details) and an emissivity index $\beta=1.5$" (4.2)
   - assumption: Tdust 20-35 K (ALMA4: 20-30 K), beta=1.5  
  > "an emissivity index $\beta=1.5$" (4.2)
   - fitting: _not stated_
   - validation: Arp220 and Pope et al. SMG templates gave values within uncertainties; PACS upper limits constrain Tdust  
  > "We found that the obtained values were within the uncertainties presented in table" (4.2)
6. **EBL and SFRD contribution**: Sum 1.1 mm fluxes over 2 arcmin^2; Poisson errors (Gehrels 1986); compare to COBE (Fixsen); SFRD for 1<z<4 with Vcom ~1.9e4 Mpc^3  
  > "Because of the numbers of our sources, we used the Poisson uncertainty values presented by (cite: gehrels1986)." (5.1)
   - assumption: ALMA sources in 1<z<4  
  > "We simply assume that the ALMA sources lie in the redshift interval of $1<z<4$" (5.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA data processing  
  > "The data were processed with the Common Astronomy Software Application (cite: mcmullin2007)." (2.1)
- **IRAF** : PSF matching (GAUSS), aperture photometry (APPHOT)  
  > "images were PSF-matched using the `IRAF` task `GAUSS`." (3.1)
- **HYPERZ** : photometric redshifts  
  > "we used two different SED fitting codes: `HYPERZ` (cite: bolzonella2000) and `EAZY` (cite: brammer2008)" (4.1.1)
- **EAZY** : photometric redshifts  
  > "we used two different SED fitting codes: `HYPERZ` (cite: bolzonella2000) and `EAZY` (cite: brammer2008)" (4.1.1)
- **FAST** : stellar mass SED fitting  
  > "done by using the `FAST` code (cite: kriek2009)" (4.1.2)
- **HIPE** : SPIRE photometry with sourceExtractorSussextractor  
  > "we used the *Herschel* Interactive Processing Environment (cite: ott2010) to perform the `sourceExtractorSussextractor` task" (3.2)
- **AIPS** : JMFIT Gaussian fitting of radio fluxes  
  > "by using the Astronomical Image Processing System (cite: van1996) to perform the `JMFIT` task" (3.2)
- **SDFRED** : flux uncertainties via LIMITMAG  
  > "by using the `SDFRED` (cite: yagi2002; ouchi2004) task `LIMITMAG`" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| EBL contribution of all five ALMA sources | 10 | +6/-4 | Jy deg^-2 | 6 | estimated to be$\sim$ $10^{+6}_{-4}$ Jy deg$^{-2}$, which corresponds to $\sim 40^{+24}_{-16}\%$ |
| EBL contribution of ALMA3-5 | 4.1 | +5.4/-3.0 | Jy deg^-2 | 6 | $\sim$ $4.1^{+5.4}_{-3.0}$ Jy deg$^{-2}$, which corresponds to $\sim 16^{+22}_{-12}\%$ |
| Infrared SFRD of ALMA3-5, 1<z<4 | (0.3-2)e-2 | not stated | Msun/yr/Mpc^3 | 6 | is estimated to be $\sim$ (0.3–2) $\times10^{-2}$ $\MO$ yr$^{-1}$ Mpc$^{-3}$ |
| z_photo (EAZY) SXDF-ALMA4 | 1.33 | +0.10/-0.16 | dimensionless | 3 | $1.33^{+0.10}_{-0.16}$ |
| M* of SXDF-ALMA1 | 9.5e10 | +2.8/-7.3 (e10) | Msun | 4 | $9.5^{+2.8}_{-7.3}$ |
| sSFR of SXDF-ALMA4 | 0.8 | +0.6/-0.6 | Gyr^-1 | 5 | $0.8^{+0.6}_{-0.6}$ |

## Qualitative findings

- ALMA1, 2, 4, 5 lie on the main sequence; ALMA3 is optically/NIR faint and may be a low-mass starburst  
  > "This figure shows that SXDF-ALMA1, 2, 4, and 5 are located in the main sequence." (5.3)

## Claim tuples

- H: Faint SMGs contribute substantially to the IR EBL | E: Summed 1.1 mm flux of ALMA sources excluding the bright AzTEC SMG | R: 4.1 Jy/deg^2, ~16% of EBL | F: Contribution as large as that of bright SMGs, with large uncertainty from small area | **partially**
- H: Faint SMGs are main-sequence or starburst galaxies | E: SED fits for M*, UV+IR SFR | R: M* 3.5-9.5e10, SFR 30-200, sSFR 0.8-2 Gyr^-1 | F: Four sources are main-sequence galaxies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Wide blank-field deep ALMA survey needed instead of lensing surveys with small volume  
  > "it is still necessary to obtain wide ($> 1$ arcmin$^2$) and deep (1$\sigma\lesssim$ 0.1 mJy) blank/unlensed field surveys" (1 Introduction)
- Alternative: Did not use Skelton et al. photometry for ALMA1/2 to keep a uniform procedure  
  > "We did not use their photometry because we preferred comparing all of the ALMA sources in the same manner." (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Small area, cosmic variance, field selected to include a bright SMG; LIR from a single 1.1 mm point has large systematics  
  > "Although our survey area was small and may have been affected by cosmic variance" (5.1)
- Caveat (inferred, ours): Only five sources; EBL fractions have huge Poisson errors
- Caveat (inferred, ours): LIR from one band with assumed Tdust
- Caveat (inferred, ours): Photometric redshifts poorly constrained for some sources
- Caveat (inferred, ours): SPIRE blending

## Reproducibility

- Data public (paper): Optical-to-radio data from public archives; ALMA data project cited  
  > "we summarize mid-infrared to radio images, which we retrieved from public archives." (2.3)
- Products in archive: _not stated_
- Missing: ALMA imaging details and source catalog in companion papers
- Missing: VLA/JVLA radio data in preparation papers
- Missing: CASA version
- Data volume (inferred): tens of GB for ALMA Band 6 19-pointing mosaic, plus archival images
- Score (inferred): 3/5, Photometry and SED recipes are described, but ALMA processing is deferred to companion papers.
- Rediscovery candidate: no, ALMA imaging recipe is incomplete and radio data are unpublished.

## Links

- Method: (cite: kohno2016) (ALMA data details and source extraction)
- Method: (cite: hatsukade2016) (ALMA map noise, completeness)
- Companion: (cite: tadaki2015) (Earlier ALMA study of ALMA1 and 2)
- Related: SXDF-UDS-CANDELS
- Related: HerMES
- Related: SpUDS
- Related: ALESS

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 46,
  "rate": 0.561
 },
 "evidence_ok": true
}
```
