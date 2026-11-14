# Coincidence of a high-fluence blazar outburst with a PeV-energy neutrino event

`2016NatPh..12..807K` | Nature Physics 2016 | first author: Kadler, M. | arXiv: 1602.02012 | DOI: 10.1038/nphys3715

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: Is a PeV neutrino event (IC 35) associated with a major outburst of the blazar PKS B1424-418, and can blazars explain the PeV neutrino flux?  
  > "Here, we report that a major outburst of the blazar PKS B1424$-$418 occurred in temporal and positional coincidence with the third PeV-energy neutrino event (IC 35) detected by IceCube." (abstract)
- Target **PKS B1424-418**: coordinates not stated (Table 2: RA 217.0 deg, Dec -42.1 deg)  
  > "The dominant blazar in the field is PKS B1424$-$418 at redshift $z=1.522$(cite: Whi88) and classified as an FSRQ." (Coincidence of a PeV neutrino with a major blazar outburst); z/distance z = 1.522  
  > "The dominant blazar in the field is PKS B1424$-$418 at redshift $z=1.522$(cite: Whi88) and classified as an FSRQ." (Coincidence of a PeV neutrino with a major blazar outburst); distance from White et al. 1988 (cite: Whi88)  
  > "The dominant blazar in the field is PKS B1424$-$418 at redshift $z=1.522$(cite: Whi88) and classified as an FSRQ." (Coincidence of a PeV neutrino with a major blazar outburst)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Fermi/LAT**: gamma-ray light curves and spectra  
  > "For the analysis of *Fermi*/LAT $\gamma$-ray data, we used the *Fermi* Science Tools (v9r32p5) with the reprocessed Pass 7 data" (Fermi/LAT gamma-ray data analysis)
- Other facility **TANAMI/LBA VLBI**: 8.4 GHz VLBI images of the radio outburst  
  > "are based on observations on 2011 Nov 13, 2012 Sep 16, and 2013 Mar 14 with the Long Baseline Array (LBA) and associated telescopes" (VLBI Imaging)
- Other facility **Swift XRT/UVOT/BAT, INTEGRAL/IBIS, SMARTS, ATCA**: X-ray, UV, optical/IR, radio SED data  
  > "Swift*/XRT data were reduced with standard methods, using the most recent software packages (HEASOFT 6.15.1) and calibration databases." (Broadband SED)
- External data: IceCube IC 35 event properties and HESE effective areas  
  > "had an energy of $2004^{+236}_{-262}$ TeV and a median positional uncertainty of $R_{50}=15.9^\circ$" (Coincidence of a PeV neutrino with a major blazar outburst) [from Aartsen et al. 2014 (cite: Ice14)]
- External data: 2LAC catalog of gamma-ray AGN in IC 35 field  
  > "a total of 20 $\gamma$-ray-bright AGN were found in the $R_{50}$ field of IC 35" (Coincidence of a PeV neutrino with a major blazar outburst) [from Ackermann et al. 2011 (cite: 2lac)]

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

- VLBI data calibration and imaging  
  > "The data were calibrated and imaged following Ojha et al. (2010)(cite: Ojh10)." (VLBI Imaging) [from Ojha et al. (2010) (cite: Ojh10)]
- Neutrino event prediction technique  
  > "we applied the techniques that we developed for our analysis of the AGN in the fields of the first two PeV IceCube events." (Neutrino event prediction) [from Krauss et al. 2014 (cite: Kra14)]

### Not stated but needed to reproduce (our reading)

- ALMA project code, band, dates and calibration/flux values used in the SED are not given
- Which ALMA flux densities enter the SED fit

## Analysis recipe

1. **Build broadband SED**: Fit two log-parabolas to quasi-simultaneous multiwavelength data including ALMA  
  > "The broadband spectra were fit with two logarithmic parabolas(cite: Mas04) in order to parametrize the characteristic double humped structure." (Broadband SED)
   - software: ISIS
   - fitting: _not stated_
   - validation: _not stated_
2. **Predict maximum neutrino counts**: Integrate the SED and multiply by IceCube effective area over 988 days, scaled by f_th  
  > "where $F_\gamma$ is the $\gamma$-ray energy flux of all blazars located inside $\Omega$ integrated between 5 keV and 10 GeV" (The maximum-possible number of PeV neutrinos from blazars in the IC 35 field)
   - assumption: photo-hadronic model with F_gamma <~ F_nu; f_th = 0.5*0.5*0.05  
  > "$$\begin{equation}
f_\mathrm{th} = 0.5 \cdot 0.5 \cdot 0.05 \sim 0.0125 
\end{equation}$$" (Predicted all-sky count of PeV neutrinos from blazars and comparison to observation)
   - fitting: _not stated_
   - validation: Compared predicted ~4 all-sky events to 3 observed  
  > "Our model thus predicts $0.0125 \cdot 336 \sim 4$ events at PeV energies from the full southern sky" (Predicted all-sky count of PeV neutrinos from blazars and comparison to observation)

## Software

- **ALMA data** : Contributed to the quasi-simultaneous broadband SED (no details)  
  > "quasi-simultaneous data from *Fermi*/LAT, *Swift*/XRT, *Swift*/UVOT, SMARTS(cite: Bon12), ALMA, ATCA and the LBA." (Broadband SED)
- **ISIS** 1.6.2: VLBI noise/images and X-ray spectral fitting  
  > "we used the software package ISIS 1.6.2(cite: Hou00)" (VLBI Imaging)
- **Fermi Science Tools** v9r32p5: LAT gamma-ray analysis  
  > "we used the *Fermi* Science Tools (v9r32p5)" (Fermi/LAT $\gamma$-ray data analysis)
- **HEASOFT** 6.15.1: Swift/XRT reduction  
  > "using the most recent software packages (HEASOFT 6.15.1)" (Broadband SED)
- **DiFX** : VLBI correlation  
  > "Correlation of the data was performed with the DiFX correlator(cite: Del11)" (VLBI Imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gamma-ray fluence of PKS B1424-418, 2012 Jul 16-2013 Apr 30 | 30.5 | 0.3 (statistical) | cm^-2 | 0 | $F=(30.5\pm0.3)\,\mathrm{cm^{-2}}$ (the uncertainty is statistical only) |
| Maximum PeV neutrino count, IC 35 field | ~13 | not stated | events | 2 | N_{\nu,\mathrm{PeV}}^\mathrm{max}(\Omega_\mathrm{IC\,35}) \sim 13 |
| Chance coincidence probability | ~5 | not stated | % | 0 | The Poisson probability to observe one or more such coincidences is about 5%. |

## Qualitative findings


## Claim tuples

- H: The PKS B1424-418 outburst is associated with IC 35 | E: Fermi light curve, VLBI and SED-based neutrino estimate | R: N_max ~4.5 in the IceCube period, ~11% Poisson probability for the outburst; chance coincidence ~5% | F: A physical association is suggested | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No pre-defined statistical test, so the 5% chance probability is not formal  
  > "because of the lack of a pre-defined statistical test, we cannot formally use this value to test the hypothesis of a chance coincidence." (Calculation of chance coincidences)
- Caveat (inferred, ours): ALMA plays a trivial role; a posteriori statistics
- Caveat (inferred, ours): Model is simple with large systematic uncertainty

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA data details
- Data volume (inferred): Negligible for ALMA; Fermi data modest
- Score (inferred): 1/5, ALMA is only a supporting SED point and no details are given.
- Rediscovery candidate: no, ALMA data are unspecified and the main results are not ALMA-based.

## Links

- Method: Ojha et al. 2010 (cite: Ojh10) (TANAMI VLBI calibration/imaging)
- Companion: Krauss et al. 2014 (cite: Kra14) (Earlier TANAMI blazars in IC 14/IC 20 fields)
- Related: TANAMI
- Related: IceCube HESE
- Related: Fermi/LAT 2LAC

## Checks

```json
{
 "quotes": 26,
 "quotes_ok": 26,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 21,
  "rate": 0.333
 },
 "evidence_ok": true
}
```
