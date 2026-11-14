# High-dimensional Statistical Analysis and Its Application to an ALMA Map of NGC 253

`2024ApJS..271...44T` | The Astrophysical Journal Supplement Series 2024 | first author: Takeuchi, Tsutomu T. | arXiv: 2203.04535 | DOI: 10.3847/1538-4365/ad2517

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: nearby_galaxies, other
- Question: Whether high-dimensional PCA methods (NRPCA and A-SPCA) can analyze an HDLSS ALMA spectral map of NGC 253 and extract rotation and outflow information objectively.  
  > "We apply two representative methods in the high-dimensional statistical analysis methods, the noise-reduction principal component analysis (NRPCA) and automatic sparse principal component analysis (A-SPCA), to a spectroscopic map of a nearby archetype starburst galaxy NGC 253" (abstract)
- Target **NGC 253**: coordinates _not stated_; z/distance 3.5 Mpc; z = 0.000811  
  > "Our target galaxy, NGC 253, is a nearby barred spiral galaxy at a distance of $3.5\;\mbox{Mpc}$, i.e., $1''$ corresponds to $17\; \mbox{pc}$ (cite: 2005MNRAS.361..330R)." (3 Data); distance from Rekola et al. 2005 (distance); Kamphuis et al. 2015 (redshift)  
  > "Our target galaxy, NGC 253, is a nearby barred spiral galaxy at a distance of $3.5\;\mbox{Mpc}$, i.e., $1''$ corresponds to $17\; \mbox{pc}$ (cite: 2005MNRAS.361..330R)." (3 Data)

## Data provenance

- ALMA projects: 2013.1.00735.S, 2013.1.00099.S
- bands: Band 7 (340–365 GHz, ~0.85 mm)  
  > "They obtained the 340–365 GHz ($\lambda \simeq 0.85$ mm) spectra covering a total frequency range of 11 GHz" (3.1 ALMA map of NGC 253)
- frequencies and spectral setup: 340.2–343.4 and 352.5–355.7 GHz (2013.1.00735.S); 350.6–352.4 and 362.2–365.2 GHz (2013.1.00099.S)  
  > "The observations cover the frequency range of 340.2–343.4 GHz and 352.5–355.7 GHz for 2013.1.00735.S, and 350.6–352.4 GHz and 362.2–365.2 GHz are covered by 2013.1.00099.S." (3.1 ALMA map of NGC 253)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.45'' x 0.3'' (8 pc x 5 pc)  
  > "The synthesized beam size of the final images is $0.\hspace{-0.5mm}''45 \times 0.\hspace{-0.5mm}''3$, which corresponds to $8 \;\mbox{pc} \times 5\;\mbox{pc}$" (3.1 ALMA map of NGC 253)
- max recoverable scale: _not stated_
- sensitivity: rms 1.0–2.4 mJy/beam at 5.0 km/s resolution  
  > "With a velocity resolution of $5.0\;\mbox{km\,s}^{-1}$, the rms noise levels are $1.0\mbox{--}2.4\; \mbox{mJy\,beam}^{-1}$." (3.1 ALMA map of NGC 253)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Data from Ando et al. 2017 (A17); PIs Nakanishi and Mangum  
  > "two projects in the ALMA Cycle 2 observations: 2013.1.00735.S (PI: Nakanishi) and 2013.1.00099.S (PI: Mangum)" (3.1 ALMA map of NGC 253)
- Line: HCN 4–3 (not stated)
- Line: HNC 4–3 (not stated)
- Line: CS 7–6 (not stated)
- External data: ALMA Band 7 NGC 253 spectral map (image cube)  
  > "The data used in this work is a spectroscopic map of a nearby archetype starburst galaxy NGC 253, obtained by A17, at Band 7." (3.1 ALMA map of NGC 253) [from Ando et al. 2017 (cite: 2017ApJ...849...81A)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.1 and 4.2.2  
  > "Data reduction is conducted with Common Astronomy Software Applications (cite: 2007ASPC..376..127M), versions 4.2.1 and 4.2.2." (3.1 ALMA map of NGC 253)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "The uncertainty of the flux calibration in ALMA Band 7 observations is $\sim 10$ % according to the ALMA Cycle 2 Proposer’s Guide." (3.1 ALMA map of NGC 253)
- self calibration: _not stated_

### Imaging

- task: clean  
  > "The image of the central region of NGC 253 was created by using task `clean`." (3.1 ALMA map of NGC 253)
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
- final beam: 0.45'' x 0.3''  
  > "The synthesized beam size of the final images is $0.\hspace{-0.5mm}''45 \times 0.\hspace{-0.5mm}''3$" (3.1 ALMA map of NGC 253)
- final rms: 1.0–2.4 mJy/beam  
  > "the rms noise levels are $1.0\mbox{--}2.4\; \mbox{mJy\,beam}^{-1}$." (3.1 ALMA map of NGC 253)

### Inherited from earlier work

- Calibration, imaging and the original 864x864x2248 cube come from A17  
  > "The A17 original map consists of $864 \times 864$ points in the spatial domain (R.A and dec.), and 2248 components along the frequency domain" (3.1 ALMA map of NGC 253) [from Ando et al. 2017 (cite: 2017ApJ...849...81A)]
- NRPCA method, estimation of number of spikes m, and A-SPCA method  
  > "Estimation of $m$ is given by (cite: AY18)." (2.2.2 NRPCA) [from Yata & Aoshima 2012; 2018; 2022]

### Not stated but needed to reproduce (our reading)

- Imaging details (robust, cell size, deconvolver, continuum subtraction) are only in A17
- Exact method for estimating m and how many PCs were retained
- Exact regridding and Doppler shift implementation, and the systemic velocity used
- Code for NRPCA and A-SPCA not named or released
- Threshold I > 1.0 Jy/beam unit and the integration definition are ambiguous
- Spatial pixel ordering details for vectorizing 2D map

## Analysis recipe

1. **Regrid map to independent pixels and mask low signal**: Regridded spatially using the equivalent circular beam of 0.37''; kept pixels with total frequency-integrated intensity I > 1.0, leaving n = 231  
  > "The equivalent circular beam size corresponding to the elliptical beam of $0.\hspace{-0.5mm}''45 \times 0.\hspace{-0.5mm}''3$ is $0.\hspace{-0.5mm}''37$. We used this effective beam size to regrid the image map." (3.1 ALMA map of NGC 253)
   - parameter: 230 x 230 pixels after regridding; n = 231 pixels retained  
  > "The number of remaining pixels $n$ is 231." (3.1 ALMA map of NGC 253)
   - fitting: _not stated_
   - validation: _not stated_
2. **Doppler-shift correction**: Gaussian fits to HCN(4–3), HNC(4–3), CS(7–6) line centers; averaged shifts and shifted spectra to rest; kept common frequency range, d = 1971  
  > "We determined the amount of the shift by averaging the shifts obtained from three lines." (3.2 Doppler shifts)
   - fitting: Gaussian line fits  
  > "We made a Gaussian fit to three prominent emission lines HCN(4–3), HNC(4–3), and CS(7–6)" (3.2 Doppler shifts)
   - validation: Corrected HCN line centers agree with the rest frequency (Fig. 21)  
  > "we see that the line center agree with its restframe frequency" (Doppler shift correction of a line: example)
3. **Apply NRPCA and A-SPCA to original and Doppler-corrected data**: NRPCA via dual covariance with noise-reduced eigenvalues; A-SPCA thresholds eigenvectors with omega = 1/2; 2D map vectorized by sorting along RA then dec  
  > "In this paper, we set $\omega=1/2$" (2.2.3 A-SPCA)
   - parameter: omega = 1/2 (obtained by simulations)  
  > "The value of $\omega=1/2$ was obtained by simulations." (Footnote 13)
   - fitting: _not stated_
   - validation: Spiked eigenvalue distribution; comparison with directly measured velocity field, and with literature outflow (SW streamer); comparison of traditional vs NR eigenvalues  
  > "the position of the root of the SW streamer precisely agrees with the region with negative PC3" (5.2 Map of PCs)

## Software

- **CASA** 4.2.1 and 4.2.2: Data reduction and imaging (task clean)  
  > "Data reduction is conducted with Common Astronomy Software Applications (cite: 2007ASPC..376..127M), versions 4.2.1 and 4.2.2." (3.1 ALMA map of NGC 253)
- **astropy** : listed in software section, use not specified  
  > "astropy (cite: astropy2013; 2018AJ....156..123A), casa (cite: 2007ASPC..376..127M), topcat (cite: 2005ASPC..347...29T)" (Software)
- **TOPCAT** : listed in software section, use not specified  
  > "astropy (cite: astropy2013; 2018AJ....156..123A), casa (cite: 2007ASPC..376..127M), topcat (cite: 2005ASPC..347...29T)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of samples n | 231 | not stated | pixels | 1 | i.e., $n = 231$ and $d = 1971$, and clearly $n \ll d$. |
| Data dimension d | 1971 | not stated | channels | 2 | i.e., $n = 231$ and $d = 1971$, and clearly $n \ll d$. |
| Contribution of PC1+PC2 (original data) | > 50 | not stated | percent | 3 | the contribution of the 1st and 2nd PCs is $> 50$ % |
| Elements per PC in A-SPCA | ~5–20 | not stated | elements | 3 | Each PC consists of $\sim 5\mbox{--}20$ elements, much fewer than $d$. |

## Qualitative findings

- PC1 traces line intensity and PC2 traces rotation in the original data; after Doppler correction PC2 traces small-scale (~10 pc) outflow, PC3/4 blueshifted flow matching the SW streamer root, and PC5 redshifted distortion.  
  > "We find that the negative PC3 region agrees well with the root of the molecular outflow, named “SW streamer”." (6 Conclusion)

## Claim tuples

- H: High-dimensional PCA works on an HDLSS ALMA spectral map with line shifts and broadening | E: Applied NRPCA and A-SPCA to the original NGC 253 map | R: Spiked eigenvalues; PC1 tracks intensity, PC2 tracks rotation; HCN and HNC features control PCs | F: The method works for spectral maps | **supported**
- H: The method can extract outflow information after removing systemic rotation | E: Applied to Doppler-corrected map and compared PC3 map to literature | R: Negative-PC3 region coincides with the SW streamer root | F: PCA extracts the outflow objectively | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Traditional PCA is unreliable for n << d data; NRPCA reduces the noise bias and avoids prior knowledge of line frequencies.  
  > "While some frequency regions are considered to contain no information, we proceeded extracting information not by traditional procedure, but by an objective statistical method without a prior information." (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Neighboring spectral channels are not independent due to line broadening, and continuum is not treated.  
  > "Then, the information carried by each spectral resolution unit is not independent" (3.3 Spectral map as HDLSS data)
- Caveat (inferred, ours): Mainly qualitative comparison with literature outflow, no quantitative test
- Caveat (inferred, ours): Spatial pixels are correlated and i.i.d. assumption is not satisfied
- Caveat (inferred, ours): Frequency gaps and Doppler cropping lose spectral information
- Caveat (inferred, ours): No uncertainty on PCs

## Reproducibility

- Data public (paper): Data are ALMA Cycle 2 projects with codes given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA${\#}$2013.1.00099.S, ADS/JAO.ALMA$\#$2013.1.00735.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: A17 imaging parameters and cube
- Missing: NRPCA/A-SPCA implementation
- Missing: Systemic velocity value used and Doppler details
- Data volume (inferred): ~10-100 GB raw; processed cube a few GB
- Score (inferred): 3/5, Data are identifiable, but cube generation is inherited from A17 and the algorithm code and parameters are incomplete; results are mostly qualitative.
- Rediscovery candidate: no, Main results are qualitative PC maps and spectral features, not numeric, and the recipe is incomplete.

## Links

- Method: Yata & Aoshima 2012 (cite: YATA2012193) (NRPCA method)
- Method: Yata & Aoshima 2022 (cite: YATA2022) (A-SPCA method)
- Method: Aoshima & Yata 2018 (cite: AY18) (Estimation of number of spikes m)
- Companion: Ando et al. 2017 (cite: 2017ApJ...849...81A) (Source of the ALMA NGC 253 spectral map)
- Related: ALCHEMI

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 31,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
