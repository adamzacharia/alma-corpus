# Revealing dust-obscured star formation in CLJ1449+0856, a cluster at z = 2

`2019MNRAS.486.4304S` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Smith, C. M. A. | arXiv: 1904.07246 | DOI: 10.1093/mnras/stz1090

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, high_z_galaxies, galaxy_clusters_and_sz
- Question: How much dust-obscured star formation is there in the z=2 cluster CLJ1449 out to 3 Mpc, and is the SFR-density relation reversed?  
  > "This indicates that there is indeed a reversal in the star formation/density relation in CLJ1449." (abstract)
- Target **CL J1449+0856 (CLJ1449)**: coordinates RA=222.3083 Dec=8.9392  
  > "CL J1449+0856 (hereafter CLJ1449, RA= 222.3083 Dec=8.9392) is one of the highest redshift, fully virialized, mature X-ray emitting clusters known." (Introduction); "Follow up spectroscopy confirmed the redshift of the cluster to be $z=1.99$, making it one of the most distant clusters discovered ((cite: 2013Gobat))." (Introduction); z/distance z=1.99  
  > "CL J1449+0856 (hereafter CLJ1449, RA= 222.3083 Dec=8.9392) is one of the highest redshift, fully virialized, mature X-ray emitting clusters known." (Introduction); "Follow up spectroscopy confirmed the redshift of the cluster to be $z=1.99$, making it one of the most distant clusters discovered ((cite: 2013Gobat))." (Introduction); distance from spectroscopy, (cite: 2013Gobat)  
  > "CL J1449+0856 (hereafter CLJ1449, RA= 222.3083 Dec=8.9392) is one of the highest redshift, fully virialized, mature X-ray emitting clusters known." (Introduction); "Follow up spectroscopy confirmed the redshift of the cluster to be $z=1.99$, making it one of the most distant clusters discovered ((cite: 2013Gobat))." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00885.S
- bands: 870 um  
  > "As part of cycle 1 the central area of the cluster was observed at 870 $\mu$m using ALMA" (2.3 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1 arcsec  
  > "The map reaches a noise of 70 $\mu$Jy beam$^{-1}$ and has a resolution of $\sim$1 arcsec." (2.3 ALMA)
- max recoverable scale: _not stated_
- sensitivity: 70 uJy/beam  
  > "The map reaches a noise of 70 $\mu$Jy beam$^{-1}$ and has a resolution of $\sim$1 arcsec." (2.3 ALMA)
- time on source: 2.5 hours  
  > "The cluster was observed for 2.5 hours and only covers a small area (0.3 arcmin$^{2}$)." (2.3 ALMA)
- observing dates: _not stated_
- pi or archival as stated: Archival, PI Strazzullo, from ALMA ESO science archive  
  > "The data was acquired from the ALMA ESO science archive" (2.3 ALMA)
- Other facility **JCMT SCUBA-2**: New 450 and 850 um maps  
  > "A total integration time of 8 hours was performed using 3 arcmin daisy scans" (2.1 SCUBA-2)
- Other facility **Herschel PACS/SPIRE**: Archival 100-500 um maps  
  > "we have used publicly available data from both the Photoconductor Array Camera and Spectrometer" (2.2 Herschel)
- Other facility **JVLA S band**: 3 GHz positions for 319 radio sources used as XID+ priors  
  > "We identified 319 significant sources in the radio map (within the same area of the SCUBA-2 maps)" (3.2 De-Blending Sub-mm Images)
- Other facility **Spitzer IRAC, Subaru, VLT**: Optical-MIR photometry for photo-z and SED fitting  
  > "This resulted in a 13 band catalogue spanning from U band ($\sim$ 0.3 $\mu$m) to 8 $\mu$m." (4 Redshift Determination)
- External data: 11 ALMA 870 um source positions in the cluster core, and spectroscopic redshifts of nine of them  
  > "For the central region we use the ALMA map and the 11 sources detected at 870 $\mu$m by ." (3.2 De-Blending Sub-mm Images) [from (cite: 2018Coogan) / (cite: 2018Strazzullo)]
- External data: Field SFR density expectation and main-sequence relation  
  > "expected value for field galaxies ($\sim$0.1 M$_{\odot}$ yr$^{-1}$Mpc$^{-3}$, (cite: 2014Madau))" (5.1 Radial Variations) [from (cite: 2014Madau); (cite: 2014Sargent)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
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

- ALMA source positions and spectroscopic redshifts taken from earlier cluster-core work, not re-derived  
  > "For the central region we use the ALMA map and the 11 sources detected at 870 $\mu$m by ." (3.2 De-Blending Sub-mm Images) [from (cite: 2018Coogan)]
- CIGALE settings follow HELP, with redshift free for photo-z and fixed at 2 for SFRs  
  > "We decided to use the same parameters used in the Herschel Extragalactic Legacy Project (HELP, (cite: 2016Vaccari))." (4.2 Photometric Redshifts Including Sub-mm Data) [from (cite: 2016Vaccari)]
- Mass-normalised SFR method  
  > "we follow the same methodology outlined in (cite: 2012Popesso)" (5.3 Mass Normalised Star Formation Rate) [from (cite: 2012Popesso)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, imaging parameters and the map used as XID+ prior are not given
- ALMA source positions and fluxes (from Coogan/Strazzullo) not tabulated
- XID+ priors and modified SCUBA-2 implementation not specified
- Full CIGALE module parameter grid not given here
- Radio source catalogue not provided

## Analysis recipe

1. **Detect SCUBA-2 850 um sources**: SEXTRACTOR on the matched-filtered map, S/N>4, threshold set by fake-source injections in a jackknife map  
  > "Therefore a S/N cut of 4 was selected." (3 Source Identification)
   - software: SEXTRACTOR, PICARD
   - fitting: _not stated_
   - validation: Fake-source completeness and false-detection test  
  > "At a S/N of 4 there was only 1 fake source, which is expected in a map of this size with Gaussian fluctuations." (3 Source Identification)
2. **De-blend Herschel and SCUBA-2 fluxes**: XID+ using ALMA sources (centre) and JVLA 3 GHz sources as positional priors  
  > "These sources were then passed through XID+ to obtain fluxes for both the PACS and SPIRE maps." (3.2 De-Blending Sub-mm Images)
   - software: XID+
   - fitting: Bayesian posterior exploration (XID+)  
  > "explores the full posterior function to extract fluxes from confused maps" (3.2 De-Blending Sub-mm Images)
   - validation: _not stated_
3. **Associate radio counterparts**: Poissonian P within 15 arcsec; reliable P<=0.05, tentative 0.05-0.1  
  > "we considered a reliable match to have a $P$ $\leq$ 0.05 and a tentative match to have 0.05$\leq P\leq$0.1." (3.3 Association With Radio Sources)
   - fitting: _not stated_
   - validation: _not stated_
4. **Photometric redshifts and membership**: EAZY and CIGALE with free z; members within 1.6<z<2.4 (2 sigma of ~0.2 scatter vs spectroscopic z)  
  > "any galaxy with a redshift between 1.6 and 2.4 is considered to be potentially in the cluster" (4.3 Cluster Membership)
   - software: EAZY, CIGALE
   - fitting: _not stated_
   - validation: Compared with spectroscopic redshifts of nine central ALMA sources  
  > "The only sources that had spectral redshifts are nine of the central ALMA sources" (4.3 Cluster Membership)
5. **SFRs and stellar masses**: CIGALE SED fit with redshift fixed at 2  
  > "Again the same settings as above were used, this time however the redshift was fixed at 2 for all galaxies." (5 Star Forming Properties Of CLJ1449)
   - software: CIGALE
   - assumption: Redshift fixed at 2 for all members  
  > "the redshift was fixed at 2 for all galaxies" (5 Star Forming Properties Of CLJ1449)
   - fitting: _not stated_
   - validation: _not stated_
6. **Radial SFR density**: Sum SFR in 0.5 Mpc bins to 3 Mpc and divide by bin volume; also cosmological volume 1.6<z<2.4 beyond 1 Mpc  
  > "We summed up the SFRs in each radial bin, and normalise it by the volume of the bin." (5.1 Radial Variations)
   - fitting: _not stated_
   - validation: Two extreme volume normalisations bracket interloper contamination  
  > "We do note that the two volumes we have normalised by are the two extreme cases." (5.1 Radial Variations)

## Software

- **XID+** : De-blending Herschel and SCUBA-2 maps  
  > "we used the Bayesian inference tool XID+" (3.2 De-Blending Sub-mm Images)
- **CIGALE** : Photo-z, SFR and stellar mass SED fitting  
  > "we use The Code Investigating GALaxy Emission (CIGALE" (4.2 Photometric Redshifts Including Sub-mm Data)
- **EAZY** : Optical/NIR photometric redshifts  
  > "we first used the template fitting code EAZY" (4.1 Photometric Redshifts Using Optical and NIR Data)
- **SMURF** : SCUBA-2 map making  
  > "Dynamic Iterative Map Maker (DIMM) within the Sub-mm User Reduction Facility (SMURF" (2.1 SCUBA-2)
- **SEXTRACTOR** : Source extraction  
  > "SEXTRACTOR ((cite: 1996Bertin)) was then used to extract these sources." (3 Source Identification)
- **AIPS** : JVLA reduction  
  > "reduced using NRAO’s Astronomical Image Processing System (AIPS)" (2.4 JVLA - S Band)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SCUBA-2 850 um sources S/N>4 | 32 | not stated | sources | 1 | In the SCUBA-2 850 $\mu$m map we detected 32 sources that have a S/N greater than 4 |
| Central 0.5 Mpc total SFR | 800 | 200 | Msun/yr | 6 | total SFR of 800 $\pm$ 200 M$_{\odot}$ yr$^{-1}$ |
| Central SFR density | 1.2e4 | 0.3e4 | Msun/yr/Mpc^3 | 6 | (1.2 $\pm$ 0.3)$\times$10$^{4}$ M$_{\odot}$yr$^{-1}$Mpc$^{-3}$ |
| Integrated SFR within 1 Mpc | 1800 | 300 | Msun/yr | 6 | total integrated SFR ($\Sigma$SFR) of 1800 $\pm$ 300 M$_{\odot}$yr$^{-1}$ |
| Central SFR if 850J not member | 440 | 160 | Msun/yr | 6 | decreases to 440 $\pm$ 160 M$_{\odot}$ yr$^{-1}$ |
| Member SFR range | 20-1600, median 168 | not stated | Msun/yr | 5 | We find SFRs between 20-1600 M$_{\odot}$ yr$^{-1}$ with a median value of 168 M$_{\odot}$ yr$^{-1}$. |

## Qualitative findings

- Most members lie on the z~2 main sequence, with some 2-3x above.  
  > "we find that the majority of galaxies within the cluster do not deviate from the expected main sequence" (5.2 Star Formation Rate vs Stellar Mass)

## Claim tuples

- H: The SFR-density relation is reversed in CLJ1449 | E: SFR density from deblended FIR/submm photometry and CIGALE in radial bins | R: Central SFRD ~1.2e4 Msun/yr/Mpc^3, ~5 orders above field | F: Reversal of the SF-density relation | **supported**
- H: Elevated SFR density extends to 3 Mpc | E: Normalise by cluster volume vs cosmological volume beyond 1 Mpc | R: Falls to field values with cosmological volume | F: Elevation possible but uncertain due to redshift ambiguity | **partially**

## Reasoning

- Why this data: ALMA resolution can resolve confused sources unresolved by SCUBA-2  
  > "the higher resolution means that we will be able to detect confused source members that cannot be resolved in the SCUBA-2 images" (2.3 ALMA)
- Why this method: _not stated_
- Alternative: Modified black-body fitting rejected in favour of CIGALE because of large FIR/submm uncertainties  
  > "we obtained better constraints using CIGALE" (5 Star Forming Properties Of CLJ1449)
- How they decided it was enough: _not stated_
- Limitation (authors): Redshift fixed at 2 and photo-z uncertainty may contaminate SFRs for outer sources  
  > "This indicates that there is a high chance of significant contamination in our sample" (5.1 Radial Variations)
- Caveat (inferred, ours): Membership relies on photo-zs with scatter ~0.2 and incomplete NIR coverage
- Caveat (inferred, ours): SFRs are fit at fixed z=2 even for tentative members
- Caveat (inferred, ours): Deblended fluxes have large uncertainties

## Reproducibility

- Data public (paper): ALMA, Herschel and JVLA data from public archives  
  > "The data was acquired from the ALMA ESO science archive" (2.3 ALMA)
- Products in archive: _not stated_
- Missing: Radio catalogue and ALMA prior positions
- Missing: XID+ SCUBA-2 modification
- Missing: Proprietary optical/NIR maps
- Missing: CIGALE parameter grid
- Data volume (inferred): Tens of GB (ALMA small; Herschel, JVLA, SCUBA-2 maps in addition)
- Score (inferred): 2/5, ALMA plays a supporting role; many ancillary and unreleased inputs and incomplete settings.
- Rediscovery candidate: no, The recipe depends on non-ALMA data and unreleased catalogues, and many settings are missing.

## Links

- Method: (cite: 2017Hurley) (XID+ de-blending)
- Method: (cite: 2018Boquien) (CIGALE)
- Companion: (cite: 2018Coogan) (ALMA/JVLA study of the cluster core)
- Companion: (cite: 2018Strazzullo) (ALMA/JVLA study of the cluster core)
- Related: HELP
- Related: S2CLS

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
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
  "facts": 80,
  "stated": 40,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
