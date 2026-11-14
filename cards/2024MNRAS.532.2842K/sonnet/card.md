# MeerKAT observations of starburst galaxies and AGNs within the core of XMMXCS J2215.9-1738 at z = 1.46

`2024MNRAS.532.2842K` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Klutse, D. Y. | arXiv: 2407.03667 | DOI: 10.1093/mnras/stae1640

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, high_z_galaxies, galaxy_clusters_and_sz
- Question: What are the star formation and AGN populations in the core of the z=1.46 cluster J2215, as seen in MeerKAT 1.3 GHz radio data combined with archival data?  
  > "We combine our radio observation with archival optical and infrared data to investigate the star formation and AGN population within $R_{200}$ ($R =$ 0.8 Mpc) of the cluster centre." (abstract)
- Target **XMMXCS J2215.9-1738**: coordinates RA 22h15m58.5s, Dec 17°38'02"  
  > "XMMXCS J2215.9-1738 at $z = 1.46$ (subsequently J2215, located at R.A. $=$ 22h 15m 58.5s and Dec. $=17^{\circ} 38^{\prime} 02^{\prime \prime}$ )" (1 INTRODUCTION); z/distance z = 1.46  
  > "XMMXCS J2215.9-1738 at $z = 1.46$ (subsequently J2215, located at R.A. $=$ 22h 15m 58.5s and Dec. $=17^{\circ} 38^{\prime} 02^{\prime \prime}$ )" (1 INTRODUCTION); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00575.S
- bands: ALMA Band 6 CO(5-4) archival data (Stach et al. 2017) and Band 3 CO(2-1) (Hayashi et al. 2017)  
  > "The CO($J=$5–4) observations of the core of the J2215 were carried out by (cite: 2017ApJStach)" (2.3 Archival Multi-Wavelength Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 6: 0.66" x 0.47" (PA 78 deg)  
  > "The six pointing observations yielded a synthesized beam size of $0. 66^{\prime \prime} \times 0. 47^{\prime \prime}$ (PA $=78^{\circ}$)." (2.3 Archival Multi-Wavelength Observations)
- max recoverable scale: _not stated_
- sensitivity: Band 6 mosaic rms 48 uJy/beam  
  > "The rms noise recorded for the final mosaicked image was 48 $\mu$Jy beam $^{-1}$." (2.3 Archival Multi-Wavelength Observations)
- time on source: _not stated_
- observing dates: Band 6: 19 June 2016; Band 3: May 2016  
  > "using forty-two 12 m antennae on June 19 2016" (2.3 Archival Multi-Wavelength Observations)
- pi or archival as stated: _not stated_
- Line: CO J=5-4 (not stated)
- Other facility **MeerKAT**: Primary 1.3 GHz L-band continuum image, rms about 3.5 uJy/beam  
  > "an rms noise level of $\approx$ 3.5 $\mu$Jy beam$^{-1}$" (2.2 Data Processing)
- Other facility **HST/ACS, Subaru/MOIRCS, Spitzer IRAC/MIPS, Herschel PACS, SCUBA-2, JVLA**: Archival optical to far-IR photometry and morphologies for SED fitting and classification  
  > "we made use of archival images, photometry or catalogues from sub-millimetre/far infra-red data from the Sub-millimetre Common User Bolometer Array 2, SCUBA-2" (2.3 Archival Multi-Wavelength Observations)
- External data: Photometric redshift and morphology catalogues of J2215  
  > "The photometric redshift catalogue from (cite: 2009ApHilton) was used in this work." (2.4 Photometric Redshifts) [from (cite: 2009ApHilton)]
- External data: Spectroscopic redshift catalogue  
  > "spectroscopic (cite: 2010ApJHilton) redshift catalogues of J2215" (3.2 Cluster Membership Classification) [from (cite: 2010ApJHilton)]
- External data: Cluster mass 3e14 Msun  
  > "adopting a cluster mass M$_{\rm{cl}}$ of $3~\times$ 10$^{14}$ M$_{\odot}$ from (cite: 2015ApJMa)" (7.3 Mass–Normalized Integrated SFR) [from (cite: 2015ApJMa)]

## Processing

### Calibration

- pipeline or manual: MeerKAT data reduced with OXKAT (CASA, WSCLEAN, CUBICAL, DDFACET, KILLMS); ALMA data not reprocessed  
  > "Data reduction was performed using a semi-automated pipeline, OXKAT" (2.2 Data Processing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: MeerKAT: J1939-6342, Stevens-Reynolds 2016 scale  
  > "J1939-6342 was used as the primary calibrator" (2.1 MeerKAT Observations)
- flux scale uncertainty: _not stated_
- self calibration: One round of phase then amplitude self-calibration (MeerKAT)  
  > "conducted one round of phase and then amplitude self-calibration" (2.2 Data Processing)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs -0.3 (MeerKAT)  
  > "a cell size of 1.1 arcsecs, and a Briggs weighting of $-0.3$" (2.2 Data Processing)
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
- final beam: 6.01" x 5.26", PA -10.4 deg (MeerKAT)  
  > "synthesized beam size of $6.01\ensuremath{''} \times 5.26\ensuremath{''}$" (2.2 Data Processing)
- final rms: _not stated_

### Inherited from earlier work

- ALMA Band 6 data acquisition and reduction  
  > "Detailed information on the data acquisition and reduction process can be found in (cite: 2017ApJStach)." (2.3 Archival Multi-Wavelength Observations) [from (cite: 2017ApJStach)]
- ALMA Band 3 reduction with CASA standard pipeline  
  > "Data reduction and processing were done using CASA with a standard pipeline." (2.3 Archival Multi-Wavelength Observations) [from (cite: 2017ApJHayashi)]

### Not stated but needed to reproduce (our reading)

- ALMA data are only quoted from earlier papers and not used in the analysis; no ALMA processing details given
- CIGALE input photometry details and fluxes not tabulated

## Analysis recipe


## Software

- **CASA** : FIXVIS and FLAGDATA in MeerKAT reduction  
  > "re-phased to the correct position via the CASA (cite: 2007McMullin) task FIXVIS" (2.2 Data Processing)
- **CIGALE** V2022.0: SED fitting for infrared luminosity and stellar mass  
  > "We performed SED fitting using `CIGALE V2022.0` (cite: 2022ApJYang) to derive the far-IR luminosity values of the cluster members." (3.3 SED Fitting with CIGALE)
- **PyBDSF** : Source extraction from MeerKAT image  
  > "using the Python Blob Detector and Source Finder (cite: 2015Mohan)" (3.1 MeerKAT Source Detection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated SFR within R200 | 1700 | ±330 | Msun/yr | 0 | we estimated an integrated star formation rate (SFR) value of 1700 $\pm$ 330 M$_{\odot}$yr$^{-1}$ within $R_{200}$ |
| Mass-normalized integrated SFR | 570e-14 | ±110e-14 | 1/yr | 0 | $(570 \pm 110) \times 10^{-14}$ yr$^{-1}$ |

## Qualitative findings


## Claim tuples

- H: Does J2215 host strong star formation and AGN activity in its core? | E: Classified 24 MeerKAT-detected members with radio luminosity, qIR and IRAC colours | R: 12 SFGs, 6 ISFGs, 6 AGN | F: The cluster is actively star-forming with a high AGN fraction | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA plays no analytic role
- Caveat (inferred, ours): Radio SFRs are blended at 6" resolution

## Reproducibility

- Data public (paper): MeerKAT data in SARAO archive, proposal SCI-20190418-MH-01  
  > "The data are associated with proposal ID SCI-20190418-MH-01." (DATA AVAILABILITY)
- Products in archive: _not stated_
- Missing: Use of ALMA data is minimal, so nothing to reproduce from ALMA
- Data volume (inferred): about 5 TB MeerKAT; ALMA negligible
- Score (inferred): 2/5, ALMA only supporting archival context.
- Rediscovery candidate: no, Main data are MeerKAT, and ALMA is not central.

## Links

- Companion: (cite: 2017ApJStach) (Source of ALMA Band 6 data)

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 53,
  "stated": 23,
  "rate": 0.434
 },
 "evidence_ok": true
}
```
