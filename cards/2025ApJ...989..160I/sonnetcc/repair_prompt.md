# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...989..160I\sonnetcc\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# MIDIS: MIRI uncovers *Virgil*, the first Little Red Dot with clear detection of its host galaxy at $z\simeq 6.6$

## Abstract

We present *Virgil*, a MIRI extremely red object (MERO) detected with the F1000W filter as part of the MIRI Deep Imaging Survey (MIDIS) observations of the Hubble Ultra Deep Field (HUDF). *Virgil* is a Lyman-$\alpha$ emitter (LAE) at $z_{spec} = 6.6312\pm 0.0019$ (from VLT/MUSE) with a rest-frame UV-to-optical spectral energy distribution (SED) typical of LAEs at similar redshifts. However, MIRI observations reveal an unexpected extremely red color at rest-frame near-infrared wavelengths, $\rm F444W - F1000W = 2.33 \pm 0.06$.

Such steep rise in the near-infrared, completely missed without MIRI imaging, is poorly reproduced by models including only stellar populations and hints towards the presence of an Active Galactic Nucleus (AGN).

According to the shape of its overall SED, *Virgil* belongs to the recently discovered population of Little Red Dots (LRDs) but displays an extended rest-frame UV-optical wavelengths morphology following a 2D-Sérsic profile with average index $n = 0.93^{+0.85}_{-0.31}$ and $r_e = 0.49^{+0.05}_{-0.11}$ pkpc. Only at MIRI wavelengths *Virgil* is unresolved due to the coarser PSF. We also estimate a bolometric luminosity $L_{\rm AGN, bol} = (8.9 - 11)\times 10^{44}\rm~erg~s^{-1}$ and a supermassive black hole mass $M_{\rm BH} = (7 - 9)\times 10^6\rm ~ M_\odot$ (if $\lambda_{\rm Edd} = 1$) in agreement with recently reported values for LRDs. This discovery demonstrates the crucial importance of deep MIRI surveys to reveal the true nature and properties of high-$z$ galaxies that otherwise would be misinterpreted and raises the question of how common *Virgil*-like objects could be in the early Universe.

# Introduction

Since the release of its first observations in July 2022, JWST has been opening up a new window on studying the early Universe (cite: Gardner+23), both by giving us exceptional details on known high-z sources (cite: Bunker+23; Maiolino+23; Colina+23) and revealing the presence of new galaxies (cite: Atek+23a; Atek+23b; Casey+23a; Robertson+23), some of which are high-z ($z>10$) candidates (cite: Iani+22; Rodighiero+23; Gandolfi+25) while others are spectroscopically confirmed (e.g., (cite: Curtis_Lake+23; Bunker+23; Wang+23; Castellano+24)).

Thanks to JWST new galaxy populations have also been discovered, e.g. galaxies with very high equivalent width emission lines (cite: Rinaldi+23a; Boyett+24; vanMierlo+23; Alvarez-Marquez+24) and the enigmatic class of the so-called “Little Red Dots” (cite: Labbe+23b; Matthee+24; Barro+23; Kokorev+24; Langeroodi2023c; Perez-Gonzalez+24a), i.e. compact sources with distinct spectral energy distributions showing clear Lyman and Balmer breaks and a characteristic “v-shaped” SED (in the $\lambda$ – $f_\lambda$ plane) implying blue rest-frame UV-to-optical colors and red optical-to-infrared colors. Their nature is still under strong debate (cite: Labbe+23b; Li+24; Inayoshi+24; Bellovary+25).

In this context, the Mid-Infrared Instrument (cite: Rieke+15; Wright+15; Wright+23) on JWST and, in particular, its imager (cite: Bouchet+15; Dicken+24) is allowing us to unfold the intermediate/high-redshift Universe by enabling us to study galaxies in the wavelength range from $5.6\;\mu$m through $25.5\;\mu$m at an unprecedented spatial resolution and sensitivity (cite: Rigby+23). Among its numerous results, MIRIM has been crucial in revealing previously undetected faint galaxies (cite: Kirckpatrick+23; Barro+23; Akins+23; Perez-Gonzalez+24a), uncovering a large population of obscured AGNs (cite: Yang+23), and characterising the physical properties of distant galaxies in great detail (cite: Colina+23; Alvarez-Marquez+23), including their morphologies (cite: Boogaard+23; Costantin+24; Gillman+24). MIRI also has a unique role in the study of early galaxies. By leveraging the deepest image of the Universe at $5.6~\mu$m (cite: Ostlin+25), (cite: Rinaldi+23a) inferred for the first time the presence of H$\alpha$ emission in individual galaxies at $z\approx 7-9$ via broad-band photometric excess.

Thanks to its capabilities, MIRIM holds the promise to reveal and constrain the rest-frame optical-NIR properties of galaxies at $z > 2$ and further push for the discovery and study of the class of “Extremely Red Objects” (cite: Elston+88; Graham+96; Caputi+04), i.e. sources displaying a large (red) color between bands probing their rest-frame optical and near-infrared emission (cite: Elston+88).

In this regard, particularly remarkable is the recent discovery of the first ERO detected thanks to MIRI imaging at 10 $\mu$m by (cite: Perez-Gonzalez+24b): with a F444W - F1000W $>$ 3.5 color, this object represented the first MIRI Extremely Red Object (MERO) reported in the era of JWST.

In this paper, we present and study *Virgil*, a MERO found in the MIRI Deep Imaging Survey (cite: Ostlin+25) F1000W imaging ($\alpha$(J2000.0) = 03:32:37.9370 (hours); $\delta$(J2000.0) = -27:47:10.712 (degrees)). The source is clearly detected in the NIRCam bands and it has been already catalogued in both JADES DR2 and VLT/MUSE catalogs (cite: Bacon+23; Rieke+23). *Virgil* is a Lyman-$\alpha$ emitter (LAE) at $z_{spec} = 6.6312 \pm 0.0019$. that shows an extremely red color between 4.4 and 10 $\mu$m and is also red with respect to the bluest MIRI band (F560W), as revealed by MIDIS F560W imaging (cite: Ostlin+25). Without the MIRIM coverage, this unexpected property of *Virgil* would have been completely missed, thus leaving us with a partial and biased knowledge of it.

This paper is organized as follows. In §[2](#sec:data) we briefly describe the datasets used and in particular the MIDIS 10 $\mu$m MIRI imaging and the ancillary HST and JWST NIRCam and MIRI observations. All the HST and JWST observations can be found in the Mikulski Archive for Space Telescopes (MAST[^1])[^2]. In §[3](#sec:virgil) we describe the identification of *Virgil*, the assessment of its redshift, the decontamination of its light from the nearby LAE at $z\simeq 4.77$, the analysis of its morphology, and the extraction of its multi-wavelength photometry. In §[4](#sec:discussion) we discuss the possible nature and the importance of MIRI imaging for the detection and characterisation of such an object. Finally, we summarise our findings and present our conclusions in §[5](#sec:conclusions).

Throughout the paper, we assume a flat $\Lambda$-CDM cosmology with $\Omega_{M} = 0.3$, $\Omega_{\Lambda} = 0.7$, and a Hubble constant $\rm H_{0} = 70\;km\,s^{-1}\,Mpc^{-1}$. According to this cosmology, the luminosity distance of our target is $D_{\rm L} = 64.8$ Gpc and the age of the universe at its redshift was about 0.8 Gyr. We adopt the AB magnitudes (cite: Oke+83). All stellar mass and SFR estimations assume a universal Chabrier initial mass function (cite: Chabrier+03). Finally, unless differently stated, we report the average 5$\sigma$ depth for point-like sources of the available NIRCam and MIRI imaging of the MIDIS area as measured in circular apertures of r = 0.2$''$ (NIRCam) and r = 0.3$''$ (MIRI) as outlined by (cite: Ostlin+25) and taking into account effects of pixel correlation as explained in (cite: Fruchter+02). The depth estimates are not corrected for aperture.

# Datasets

## MIRI F1000W data

MIRI data in the F1000W filter were taken as part of *The MIRI Deep Imaging Survey* (MIDIS, PID: 1283; PI: G. Östlin; (cite: Ostlin+25)) in December 2023. The observation consisted of 11 exposures, each with 100 groups and 7 integrations, for a total on-source exposure time of 30.8 ks, centered on the Hubble Ultra Deep Field (cite: Beckwith+06). The dithering pattern was set to large-size cycling, with the 11 exposures taken in different positions on the sky separated by up to 10$''$. This dithering pattern, with no repeated positions, was selected since it was found to be crucial for the detection of faint sources, such as *Virgil*, and their distinction from detector artifacts.

A detailed description of the reduction of the MIRI data is presented in (cite: Perez-Gonzalez+24b). Briefly, a super-background strategy is used to build background maps for every single image using all the other exposures (since they were taken during the same campaign), which results in a very homogeneous background (in terms of level and noise). Known sources are masked to avoid biasing the determination of the very local background in the super-background frame. Our final F1000W image, reduced with a 60 milliarcsec pixel-scale, presents an average 5$\sigma$ depth of 26.4 mag. We present the MIDIS F1000W data in Figure [1](#fig:midis) (top panels) as the red channel of an RGB image built in combination with the NIRCam long-wavelength channels F277W and F356W.

![image](figures/MIDIS_Virgil_v2.png)\
![image](figures/Virgil_stamps.pdf)

## Ancillary data

We complement our MIRI observations at 10 $\mu$m with a rich set of photometric and spectroscopic data publicly available. In particular, we extend our dataset including more MIRI observations, HST and JWST/NIRCam filters, the Atacama Large Millimeter/submillimeter Array (ALMA) surveys and deep optical integral field spectroscopy by the Multi Unit Spectroscopic Explorer (MUSE) at the Very Large Telescope (VLT). We briefly summarise these ancillary datasets in the following sections.

### Additional MIRI data

We combine the recently acquired MIDIS F1000W data with the F560W ultra-deep observations also carried out by MIDIS in December 2022 and January 2023. A thorough description of this dataset is presented in (cite: Ostlin+25). These observations consist of $\sim41$ hours on source taken in the HUDF, reaching a 5$\sigma$ depth of 28.6 mag. We add to the MIDIS observations the publicly available MIRI data gathered by the *Systematic Mid-infrared Instrument Legacy Extragalactic Survey* (cite: Lyu+23; Rieke+24; Alberts+24) in the F770W, F1280W, F1500W, F1800W, F2100W and F2550W bands. We reduce the SMILES images following the same methodology applied to the MIDIS dataset and obtain images with a 5$\sigma$ depth of about 26.2 (F770W), 25.0 (F1280W), 24.9 (F1500W), 24.1 (F1800W), 23.6 (F2100W) and 21.8 (F2550W) mag, respectively.

### NIRCam data

We complement the MIRI data with NIRCam imaging taken by *The JWST Advanced Deep Extragalactic Survey* (cite: 2023arXiv230602465E), Data Release 2 ((cite: 2023arXiv231012340E)), which includes also observations from the *JWST Extragalactic Medium-band Survey* (cite: 2023ApJS..268...64W) and *The First Reionization Epoch Spectroscopically Complete Observations* (cite: 2023MNRAS.525.2864O). This dataset provides a total of 14 bands from 0.9 to 4.8 $\mu$m (F090W, F115W, F150W, F182M, F200W, F210M, F277W, F335M, F356W, F410M, F430M, F444W, F460M, F480M) with 5$\sigma$ depths ranging from 30.5 to 30.9 mag.

### HST data

We obtain all the HST images over the HUDF from the Hubble Legacy Field GOODS-S (cite: Whitaker+19). The HLF-GOODS-S provides 13 HST bands covering a wide range of wavelengths (0.2$-$1.6$\mu$m), from the UV (WFC3/ UVIS F225W, F275W, and F336W filters), optical (ACS/ WFC F435W, F606W, F775W, F814W, and F850LP filters), to near-infrared (WFC3/IR F098M, F105W, F125W, F140W and F160W filters). In this paper, we only made use of the deepest ones (i.e., F435W, F606W, F775W, F814W, F850LP, F105W, F125W, F140W, F160W). We refer the reader to (cite: Whitaker+19) for more detailed information on these observations.[^3]

### MUSE data

The HUDF has been extensively studied with MUSE (cite: 2010SPIE.7735E..08B) at VLT as part of the MOSAIC and UDF-10 fields (GTO programs 094.A- 0289(B), 095.A-0010(A), 096.A-0045(A) and 096.A- 0045(B), PI: R. Bacon) and the most recent MXDF observations (GTO Large Program 1101.A-0127, PI: R. Bacon). These observations cover a spectral wavelength range between 4750 - 9350 Å with a spectral resolving power (R) that varies from 1770 (4800 Å) to 3590 (9300 Å) and have a PSF (at 7750 Å), that can be described by a Moffat function (cite: Moffat+69) that varies from FWHM = 0.45$''$ and $\beta = 1.89$ (MXDF), to FWHM = 0.60$''$ and $\beta = 2.80$ (UDF-10), and to FWHM = 0.63$''$ and $\beta$ = 2.80 (MOSAIC), see (cite: Bacon+23) and their Table 4. In the MIDIS area, these observations have exceeded total exposure times of 140 hours, although the distribution of the depth in flux is not uniform across the whole area. More details about the HUDF MUSE surveys can be found in (cite: Bacon+17; 2023A&A...670A...4B). In our study we use the fully reduced MUSE datacubes for the MOSAIC + UDF-10 and MXDF programs, as well as the catalog of detected sources and corresponding redshifts presented in (cite: Bacon+23).[^4]

### ALMA data

The Atacama Large Millimeter/submillimeter Array (ALMA) Spectroscopic Survey in the Hubble Ultra Deep Field (ASPECS) is a Cycle 4 Large Program over a 4.6 arcmin$^{2}$ scan at 1.2 mm (cite: Decarli+20; gonzalez-lopez2020) and 3.0 mm (cite: Decarli+19; gonzalez-lopez2019). The ultra-deep 1.2 mm data reaches an rms sensitivity of 9.3 $\mu$Jy/beam, with beam dimensions of $1.5\ensuremath{''}\times1.1\ensuremath{''}$. The 3.0 mm data reaches 1.4 $\mu$Jy/beam, with a $1.8\ensuremath{''}\times1.5\ensuremath{''}$ beam. We download the fully reduced ALMA images from the official ASPECS website.[^5]

# Selection and properties of the MIRI extremely red Object *Virgil*

In this paper, we present *Virgil* ($\alpha$(J2000.0) = 03:32:37.9370 (hours); $\delta$(J2000.0) = -27:47:10.712 (degrees)), a source in the deep MIDIS F1000W image of the HUDF, which is counterpart to a LAE at $z=6.6312$ from MUSE/VLT (§[3.2](#sec:redshift)). Despite being already known from shorter wavelength data (cite: Bacon+23; 2023ApJS..269...16R; 2023arXiv231012340E), new important insights on the nature of this object come from the new deep MIRI observations at 10 $\mu$m. In particular, *Virgil* displays an extreme F444W $-$ F1000W red color ($\geq 2$) that classifies it as an ERO. Since the ERO nature of this source can only be determined with MIRI, we refer to it as MERO.

## Identification of the MERO *Virgil*

Motivated by the recently reported discovery of the MERO *Cerberus* found in the MIDIS field (cite: Perez-Gonzalez+24b), we decide to further scout the MIDIS area to discover additional MIRI red objects. To do so, we make use of the SEXTRACTOR software (cite: 1996A&AS..117..393B) directly using the MIRI/F1000W map as detection image. We follow the hot-mode extraction described in (cite: 2013ApJS..206...10G), which is particularly effective for detecting extremely faint sources and construct a photometric MIRI/F1000W catalog based on the SEXTRACTOR magnitude estimates `MAG_AUTO`. We cross-match our catalog (using a 0.2$''$ search radius) to the official JADES DR2 catalog published by (cite: 2023arXiv231012340E) to only consider those sources showing a red F444W - F1000W color ($\rm F444W - F1000W \geq 1.5$) and a robust F1000W detection (S/N$~ \geq 5$). The reddest object we find in our sample displays a $\rm F444W - F1000W = 2.33 \pm 0.06$. We name this MERO *Virgil*, to acknowledge the fact that it is very close in projection to *Cerberus* (separation $\delta \approx$ 2.3$''$).

An RGB image of the source built with NIRCam and MIRI data is presented in the top right panel of Figure [1](#fig:midis), together with a series of postage stamps showing *Virgil* from 0.7 to 21$\mu$m.

## Redshift assessment of *Virgil*

In the JADES DR2 catalog (cite: Eisenstein+23), *Virgil* is listed with `ID 206038` and a photometric redshift $z_{phot} \approx 6.62$. This redshift estimate agrees with the fact that our source appears to be a NIRCam F090W drop out, see the cutouts presented in Figure [1](#fig:midis).

However, to better constrain the properties of our target, we investigate if we can derive a spectroscopic redshift $z_{spec}$ from the available MUSE observations. In fact, based on the $z_{phot}$ reported by the JADES DR2 catalog, the MUSE data should cover *Virgil*’s rest-frame UV emission. Therefore, we look for the possible presence of emission lines, and in particular, of the Ly$\alpha$ line in the MUSE cube. To do so, we extract the MUSE 1D spectrum at the coordinates of our target within circular apertures of different sizes ($r = ~$0.4$''$, 0.8$''$). Despite being strongly contaminated by the extended rest-frame UV emission of a close-by LAE at $z_{\rm spec} \simeq 4.77$ (cite: Bacon+23), in the MUSE 1D spectrum we find a spectral feature appearing only at the position of the MIRI extremely red object. This line cannot be explained by any known emission line in the UV spectrum of galaxies at $z = 4.77$ and falls at the expected wavelength of the Ly$\alpha$ at $z \simeq 6.63$ (i.e. $\approx 9280$ Å, see right panel of Figure [2](#fig:muse)). The classification of this spectral feature as *Virgil*’s Ly$\alpha$ is in agreement with the publicly available catalog of MUSE-detected sources by (cite: Bacon+23). Particularly, (cite: Bacon+23) list this source (`ID 7699`) as an LAE at a spectroscopic redshift $z_{spec} = 6.6312\pm 0.0019$ (`quality_flag = 2`, i.e. good confidence[^6]) with a Ly$\alpha$ flux $F({\rm Ly\alpha}) \approx 1.6 \times 10^{-18}~{\rm erg~s^{-1} cm^{-2}}$ (corresponding to a Ly$\alpha$ luminosity $L(\rm Lya) \approx 8.1 \times 10^{41}\rm~ erg ~s^{-1}$) and S/N $\approx 8$. Therefore, we assume $z_{spec} = 6.6312\pm 0.0019$ as *Virgil*’s redshift for the rest of our analysis.

Nonetheless, given the wealth of recent spectroscopic campaigns in the HUDF, we also verify if our target had been observed by the FRESCO (PID: 1895; PI: P. Oesch, (cite: Oesch+23)), the NGDEEP (PID: 2079; PI: Finkelstein, (cite: Bagley+24)) and JADES surveys.

Unfortunately, our target is not detected in FRESCO’s NIRCam Wide Field Slitless Spectroscopy (WFSS) observations[^7], nor in the NGDEEP’s NIRISS WFSS observations[^8]. Finally, the NIRSpec Micro Shutter Array (MSA) observations from JADES (cite: DEugenio+24) in HUDF did not cover the area of our target.

![image](figures/lya_pseudo-nb.pdf) ![image](figures/lya_muse_spec.pdf)

## Removal of *Virgil*’s contaminant

In the JADES DR2 catalog, *Virgil*’s contaminant at $z \approx 4.77$ ((cite: Bacon+23); see also (cite: Matthee+22)) turns out to be constituted by two sources: `ID 285736` and `ID 206035`. With respect to *Virgil*’s location, `ID 285736` is about 0.4$''$ away while `ID 206035` has a separation of 0.7$''$ both in the south-east direction.

To avoid the contamination of *Virgil*’s photometry due to this extended lower redshift LAE, we model and subtract its contribution at all wavelengths. To do so, we resort to the galaxy morphology modeling tool ASTROPHOT (cite: Stone+23). With ASTROPHOT, we model `ID 285736` and `ID 206035` with single Sérsic profiles while masking *Virgil*.

From the first results, we find that to improve the quality of the residuals in several filters, it is necessary to introduce an optional third Sérsic component between `ID 285736` and `ID 206035`, see also (cite: Matthee+22). In Figure [3](#fig:degraded_ima), we present the residuals of the best-fit models obtained with ASTROPHOT for some of the available NIRCam and MIRI filters.

![](figures/virgil_psfmatched_supernew.png)

## *Virgil*’s morphology

After the removal of *Virgil*’s contaminant and before extracting its photometry (see §[3.3](#sec:decontamination)), we briefly investigate *Virgil*’s morphology.

At NIRCam wavelengths our target is clearly elongated in the south-west direction and features a tail that seems to end up in a (faint) clump (*Beatrix*; $\alpha$(J2000.0) = 03:32:37.8844 (hours); $\delta$(J2000.0) = -27:47:10.979) that can be detected at several NIRCam wavelengths but is completely missing in the MIRI imaging, see Figure [3](#fig:degraded_ima). On the basis of the current data, it is difficult to assess whether *Beatrix* is a clump of *Virgil* or a different object at a different redshift (see §[3.5](#sec:photometry)). However, if confirmed at Virgil’s redshift, the separation between *Virgil* and *Beatrix* ($\delta \approx ~$0.75$''$) would correspond to a projected distance of about 4 pkpc and, considering its point-like nature, a size $r \lesssim 0.''06 \simeq 0.3$ pkpc.

After masking *Beatrix* and other close-by sources, the extracted surface brightness profile shows that *Virgil* is an extended object at wavelengths $\lambda < 7~\mu$m, while at 7.7 and 10 $\mu$m, it is unresolved due to the coarser MIRI PSF . This is confirmed by the extraction of *Virgil*’s radial surface brightness profile and its comparison with the PSF trend in the different NIRCam and MIRI filters, see Figure [4](#fig:sb-profile).

If we fit a Sérsic profile (cite: Sersic+63) to the SB radial profiles of the different broad-band NIRCam and MIRI filters covering *Virgil*’s rest-frame optical emission (i.e. F200W, F277W, F444W, F560W), we find a median value of the Sérsic index $n = 0.93^{+0.85}_{-0.31}$ (16th and 84th percentiles) and an effective radius $r_e \simeq 0.''09^{+0.01}_{-0.02} = 0.49^{+0.05}_{-0.11}\rm~pkpc$ (16th and 84th percentiles). Both parameters are in agreement with the expected values of galaxy sizes and Sérsic indices at $z \simeq 6$ (cite: Sun+24).

![](figures/sb_profile-virgil.pdf)

## Extraction of *Virgil*’s photometry

After having removed the lower redshift interloper from all the 31 available HST (ACS and WFC3) and JWST (NIRCam and MIRI) bands, we extract *Virgil*’s photometry in the wavelength range 0.4 – 25 $\mu$m with SEP (cite: Barbary+17), a PYTHON version of SEXTRACTOR (cite: Bertin+96). However, at the longest MIRI wavelengths ($> 15~\mu$m), the available imaging is too shallow to detect *Virgil*. Also after stacking together all the different MIRI bands available above 15 $\mu$m (i.e. F1800W, F2100W, F2550W) we fail to detect our target. Hence, above 15 $\mu$m we make use of the 3$\sigma$ upper limits on the flux density.

We extract Virgil photometry $\leq 15~\mu$m within `Kron apertures` (cite: Kron+80), allowing the Kron parameters to vary from filter to filter and replicating standard SEXTRACTOR settings, i.e. $K = 2.5$ and a minimum radius $r = 1.75\ensuremath{''}$. Then, we correct the extracted fluxes to account for the missing flux outside the Kron aperture. To do so, we compute the fraction of the missing light outside the Kron apertures (cite: Whitaker+11; Weaver+23a; Kokorev+24) in comparison to the curve of growth of the different PSFs. For the JWST filters, we employ the PSF models by WebbPSF (cite: Perrin+14), while for HST we resort to the curve of encircled energy reported by STScI[^9]. We finally correct for Galactic extinction. Following (cite: Iani+24), we obtain the Galactic extinction corrections assuming the color excess reported on the IRSA webpage[^10] at *Virgil*’s coordinates (cite: Schlafly+11) and, for all filters with an effective wavelength $\lambda_{\rm eff} < 1.25~\rm \mu m$, applying the (cite: fitzpatrick+99) extinction law, while at longer wavelengths ($1.25 \leq \lambda_{\rm eff} < 8~\rm \mu m$), resorting to the (cite: indebetouw+05) law. The correction factors for Galactic extinction are, however, quite negligible ($< 3\%$).

As in the case of SEXTRACTOR (cite: Sonnett+13), SEP tends to underestimate the errors on the fluxes. To derive more reliable errors, we estimate them drawing in each filter 1000 random Kron apertures on the sky region around *Virgil* ($6''\times 6''$) and, after having masked all the close-by sources, measuring their fluxes. We then take the standard deviation of all the different measurements taking into account effects of pixel correlation (cite: Fruchter+02). Similarly to the fluxes, we also correct the errors to total flux and Galactic extinction. Finally, we impose as a minimum error on the photometry a value of 0.05 mag for all bands. We present *Virgil*’s photometry in Table [\[tab:photo_virgil\]](#tab:photo_virgil).

In addition to HST and JWST imaging, we search for detection of *Virgil* at (sub-)millimeter wavelengths leveraging on the available deep ASPECS ALMA dust continuum imaging at 1.2 and 3.0 mm. By carefully inspecting these maps, *Virgil* is not detected at either wavelengths, see Figure [5](#fig:alma). This finding implies 3$\sigma$ upper limits on the flux density at 1.2 mm and 3.0 mm of 27.9 $\mu$Jy and 4.2 $\mu$Jy, respectively (cite: Boogaard+23; Perez-Gonzalez+24b).

![image](figures/MIRIM-Virgil-ASPECS-Band6-6as.png) ![image](figures/MIRIM-Virgil-ASPECS-Band3-6as.png)

To assess the quality of our photometry on the images cleaned for the contaminant, we decide to test if, by running Spectral Energy Distribution (SED) fitting codes on our photometry, we retrieve photometric redshifts in agreement with the spectroscopic redshift from MUSE. To this purpose, we employ both EAZY (cite: Brammer+08) and CIGALE (cite: Burgarella+05; Noll+09; Boquien+19). For Eazy, we adopt the v1.3 templates, which include a dusty galaxy with a high-equivalent width emission line spectrum, as well as new models for LRDs and high-redshift AGN+torus recently added based on JWST data (cite: Killi+23).

We do not impose any prior and work with minimum $\chi^{2}$ photometric redshift estimates in the redshift range $z = 0-20$ and consider *Virgil*’s photometry up to 10 $\mu$m. For CIGALE, we run it only considering stellar templates and HST + JWST/NIRCam photometry, thus excluding the red upturn of our target’s photometry. We use the same setting as presented in § [3.7](#sec:sed). According to both codes, the probability distribution of the photometric redshifts (PDZ) is uniquely determined (one single narrow peak) to be at $6.61\pm 0.02$ (EAZY) and $6.68 \pm 0.23$ (CIGALE). Overall, we find a very good agreement with the spectroscopic estimate from MUSE.

In addition to *Virgil*, we extract the photometry for *Beatrix* following the same methodology as presented above. Our aim is to understand if we can assess the redshift of this object and discern if it is part of *Virgil* (clump) or a source at a different redshift. Due to the faintness of the source, however, we can only detect *Beatrix* in few HST and JWST/NIRCam bands. On the derived photometry, we run both EAZY and CIGALE. Both codes return a multi-peaked PDZ. Interestingly, one of the peaks falls at *Virgil*’s redshift and another one corresponds to the redshift of the contaminant LAE at $z \simeq 4.77$. The other peaks, however, suggest even lower redshift solutions ($z_{phot} < 2$). Due to the limited dataset available and the fact that we are not sure about its redshift, we do not further investigate this object.

|             |        |           |                |
|:------------|:------:|:---------:|:--------------:|
| Instrument  | Filter | $f_{\nu}$ | err($f_{\nu}$) |
|             |        |  \[nJy\]  |    \[nJy\]     |
| JWST/NIRCam | F090W  |   12.86   |      2.25      |
| HST/ACS_WFC | F850LP |   3.38    |      2.70      |
| HST/WFC3_IR | F105W  |   22.07   |      1.95      |
| JWST/NIRCam | F115W  |   30.54   |      2.00      |
| HST/WFC3_IR | F125W  |   27.06   |      2.51      |
| HST/WFC3_IR | F140W  |   22.90   |      2.59      |
| JWST/NIRCam | F150W  |   28.92   |      1.85      |
| HST/WFC3_IR | F160W  |   28.52   |      2.82      |
| JWST/NIRCam | F182M  |   24.63   |      2.65      |
| JWST/NIRCam | F200W  |   30.32   |      2.04      |
| JWST/NIRCam | F210M  |   36.70   |      3.10      |
| JWST/NIRCam | F277W  |   40.11   |      1.85      |
| JWST/NIRCam | F335M  |   38.88   |      2.26      |
| JWST/NIRCam | F356W  |   93.84   |      4.32      |
| JWST/NIRCam | F410M  |   37.01   |      1.89      |
| JWST/NIRCam | F430M  |   37.79   |      4.80      |
| JWST/NIRCam | F444W  |   49.33   |      2.27      |
| JWST/NIRCam | F460M  |   46.99   |      6.25      |
| JWST/NIRCam | F480M  |   67.58   |      7.91      |
| JWST/MIRI   | F560W  |  107.70   |      3.03      |
| JWST/MIRI   | F770W  |  248.20   |     30.13      |
| JWST/MIRI   | F1000W |  399.10   |     23.79      |
| JWST/MIRI   | F1280W |  382.70   |     161.10     |
| JWST/MIRI   | F1500W |  379.50   |     296.20     |

: Photometry of *Virgil*

Table notes: In the above table, we report the photometry of *Virgil* as extracted after the modeling of the $z = 4.77$ LAE contaminant (see §[3.3](#sec:decontamination)). The table is limited to only those bands where it was possible to detect *Virgil*.

## Possible galaxy - galaxy lensing effect on *Virgil*

Due to the closeness of the contaminant to *Virgil* and the extended and stretched morphology of our target, we investigate if *Virgil* could be affected by a galaxy - galaxy lensing effect (cite: Matthee+17). To estimate the magnification of *Virgil* by the foreground LAE we resort to the usage of the LENSTRONOMY software (cite: Birrer+18). The measured stellar masses of the two components of the foreground LAE are $M_\star \simeq 10^{8.3}\rm~M_\odot$ and $10^{8.6}\rm~M_\odot$ (cite: Eisenstein+23) for the objects located 0.4$''$ and 0.7$''$ from *Virgil*, respectively. The two components are located 0.32$''$, or about 2.1 pkpc from each other at $z = 4.77$. The separations involved are sufficiently large that the lensing model is mostly unaffected by assumptions on the mass profile of the lensing galaxies; the Einstein radius is $\sim 5$ mas using a point-mass approximation, and $\lesssim 20$ mas when assuming extended mass distributions (maximized using an ellipsoid configuration). This configuration results in a magnification $< 5$% of *Virgil* even under extreme assumptions for the total-mass-to-stellar-mass ratios of 10 for both foreground galaxies. Due to the minimum value of the retrieved magnification, we do not consider corrections for lensing in the following analysis.

## Spectral energy distribution analysis of *Virgil*

After having extracted its decontaminated photometry, we try to reproduce *Virgil*’s observed SED with different SED fitting codes, namely, CIGALE , Bagpipes (cite: Carnall+18), prospector (cite: Johnson+21), and synthesizer-AGN (cite: Perez-Gonzalez+03; Perez-Gonzalez+08; Perez-Gonzalez+24a).

Due to *Virgil*’s red F444W - F1000W color, we decide to run the codes both excluding and considering the presence of an AGN (see § [4](#sec:discussion)). For the SED fitting, we consider all the photometry available, including the ALMA upper limits at 1.2 and 3mm.

We first employ CIGALE assuming a delayed exponentially declining SFH (delayed-$\tau$ model) modelled with two stellar populations. We adopt the stellar populations models with both solar and sub-solar metallicity ($Z = 0.2 Z_\odot$), and the Chabrier IMF. We include nebular continuum and emission lines using solar and sub-solar metallicity and allowing the electron density $n_e$ and ionisation parameter $U$ to assume values of $n_e = 10, 100, 1000\rm~cm^{-3}$ and $\log_{10}(U) = -2,-1$, respectively. For the dust attenuation, we adopt while for the far-IR emission, we resort to the (cite: Draine+14) models. We add the AGN emission using the SKIRTOR models (cite: Stalevski+12; Stalevski+16) following the initial parameters suggested by (cite: Yang+23) but allowing for the presence of both a Type I (unobscured) and 2 (obscured) AGN.

As a second SED-fitting code, we run Bagpipes, a stellar population synthesis modeling package built on the spectral library with the 2016 version of the MILES library (cite: Falcon-Barroso+11). The code uses a (cite: Kroupa+01) IMF, adopts the dust attenuation curve and includes nebular emission lines. The ionisation parameter $\log_{10}(U)$ is set to vary between $(-4,\, -2)$. The SFH is set to two components delayed-$\tau$ model and we included an AGN component as in (cite: Carnall+23).

For prospector we adopt the setup described in detail in (cite: Langeroodi+23) and (cite: Langeroodi+23b). In brief, we use 5 temporal bins to model the star-formation history non-parametrically while applying the continuity prior from (cite: Leja+19). The nebular emission is modelled using the CLOUDY (cite: Chatzikos+23) templates compiled in (cite: Byler+17), while the gas-phase metallicity, stellar metallicity, and ionization parameters are modelled as free parameters. We model the dust attenuation using the two-component model of (cite: Kriek+13), where one component affects the entire galaxy and the other models the additional reddening at the birthplace of young stars.

Finally, we run synthesizer-AGN. The code assumes that the SED can be modelled with a composite stellar population (cite: Perez-Gonzalez+03; Perez-Gonzalez+08) and AGN emission coming from the accretion disk and the dusty torus (cite: Perez-Gonzalez+24a). The stellar emission includes a young and a more evolved star formation event, each one described by a delayed exponential function with timescales between 1 Myr and 1 Gyr, and with ages from 1 Myr up to the age of the Universe at the redshift of the source. The attenuation of the emission from each stellar population is independent and described by the law, with A(V) values ranging from 0 to 10 mag for each population, considered to have completely independent attenuation. The stellar emission is described by the models, assuming a Chabrier IMF with stellar mass limits between 0.1 and 100 M$_\odot$, and the nebular emission is also considered (cite: Perez-Gonzalez+03). The AGN emission is modelled with a QSO average spectrum (cite: Vanden-Berk+01; Glikman+06). The dust emission from the AGN is modelled with the self-consistent templates of AGN tori presented in (cite: Siebenmorgen+15).

We present and discuss the results derived from the different SED-fitting codes in §[4](#sec:discussion).

![](figures/best_fit_sed_blue.png)

![image](figures/best_fit_sed_noagn.png)\
![image](figures/best_fit_sed_agn.png)

# Discussion

## *Virgil*’s properties without MIRI

As a first step, we decide to investigate *Virgil*’s properties based only on its HST and JWST/NIRCam photometry, i.e. limiting our study to wavelengths $< 5~\mu$m.

The SED of *Virgil* reveals a rest-frame blue UV continuum. Following (cite: Castellano+12), by fitting a power law to the observed fluxes ($f_\lambda \propto \lambda^{\beta_{\rm UV}+2}$), we estimate a UV continuum slope of $\beta_{\rm UV} = -2.1 \pm 0.3$ and an absolute UV magnitude at 1500Å M(UV) $=-19.1\pm 0.1$ mag. Both parameters are well in agreement with what was recently found for other LAEs at similar redshifts (cite: Iani+24) and suggest negligible effects due to dust extinction (cite: Meurer+99). If we convert the M(UV) into SFR following the prescription by (cite: Kennicutt+12), we find an SFR(UV)$~\simeq 1.7~\rm M_\odot~yr^{-1}$ (not corrected for dust extinction).

At optical wavelengths, *Virgil*’s SED is characterised by a clear photometric excess in the F356W band (F335M $-$ F356W $=0.96 \pm 0.08$). Due to *Virgil*’s redshift (i.e., $z_{spec} = 6.6312 \pm 0.0019$), this excess can be explained as the direct consequence of a strong H$\beta$ + \[O III\]$\lambda\lambda4959,5007$ (\[O III\], hereafter) emission line complex entering the F356W filter. If we assume the continuum below H$\beta$ + \[O III\] as the average value between the F356W adjoining filters F335M and F410M and apply the prescriptions by (cite: Marmol-Queralto+16), we can convert the photometric excess in F356W into the rest-frame equivalent width EW$_0$ of the line complex. From our photometry, we estimate EW$_0({\rm H}\beta + [$O III$]) \approx 560$ Å. This value is in good agreement with recent literature for emitters at $z \gtrsim 6$ (cite: Endsley+21; Prieto-Lyon+23; Rinaldi+23a; Matthee+23; Caputi+24). We highlight that an increase in flux is also observed in the NIRCam longest wavelength filter, e.g. F460M $-$ F480M $= 0.39 \pm 0.19$. At *Virgil*’s redshift and without the information coming from the MIRI imaging, this flux excess could be easily ascribed to the H$\alpha$ emission line entering the F480M filter. In fact, medium band filters are known for their heightened sensitivity to strong emission lines (cite: Papovich+23; Rinaldi+23a; Caputi+24).

Hence, by limiting the analysis of *Virgil* at rest-frame wavelengths $\leq 0.65~\mu$m, the observed SED of *Virgil* is well represented by a typical LAEs’ SED with strong optical emission lines (cite: Ouchi+20). This is also confirmed by our runs with SED fitting codes only considering the available photometry below the MIRI/F560W imaging. In this case, all codes model *Virgil* as a young ($\leq 100$ Myr) star-forming ($\rm SFR = 1 - 2~ M_\odot~yr^{-1}$) low-mass galaxy ($M_\star \simeq 10^{8.0-8.5}\rm ~M_\odot$) with low dust content ($\rm A_V \leq 0.8$ mag), see Figure [6](#fig:sed_blue).

## *Virgil*’s full SED

The distinctive feature of *Virgil* lies in its pronounced increase in brightness beyond 0.6 $\mu$m rest-frame (4.8 $\mu$m observed-frame), leading to a notable upturn in its SED at near-IR wavelengths. By fitting a power law ($f_\lambda \propto \lambda^{\alpha_{\rm NIR}}$) to the observed fluxes in the wavelength range $4 - 10\mu$m (observed), we find a spectral index $\alpha_{\rm NIR} = 2.8 \pm 0.1$. While the increase in the reddest NIRCam medium band filters F460M and F480M could be potentially caused by the presence of a strong H$\alpha$ + \[N II\]$\lambda\lambda6548,6584$ line complex (cite: Papovich+23), the steep rising MIRI SED from 0.7 $\mu$m (F560W) up to 1.3 $\mu$m (F1000W) rest-frame cannot be solely explained by strong emission lines. In fact, although at $z = 6.6312$ the Paschen-$\beta$ (Pa$\beta$) emission line enters the F1000W band, atomic physics predicts that the Pa$\beta$ intensity is about 1/20 of the H$\alpha$ line (cite: Osterbrock+06). Besides, F1000W is a very wide band, with an effective width of about 17000 Å. Hence, for a galaxy at *Virgil*’s redshift, already an excess of 0.1 mag in F1000W would imply a rest-frame equivalent width for the emission line of about 200 Å, i.e. roughly 1/3 of what we estimate for the H$\beta$ + \[O III\] complex. Based on our previous best SED fitting models (see § [4.1](#sec:short_sed) and Figure [6](#fig:sed_blue)), we would expect an excess of more than 2.0 mag with respect to the models’ continuum in F1000W, thus implying an unrealistically strong Pa$\beta$ line. A similar reasoning can be applied to *Virgil*’s detection (S/N $\approx 5$) in F770W (effective width of about 18300 Å), with a flux $\approx$ 2.5 times higher than what we detect in F560W (F560W - F770W $= 1.01 \pm 0.23$).

Having excluded that the red upturn is driven by strong emission lines, we fit *Virgil*’s observed photometry (including the ALMA upper limits at 1.2 and 3mm) in a two-fold way: assuming that its SED is uniquely due to the contribution of stellar populations and the ISM, and adding the effects of an AGN. In fact, *Virgil*’s SED steep rise at the rest-frame near-IR domain of galaxy spectra could be the sign of an AGN dusty torus (cite: Hickox+18).

### Only Stellar Populations models

When implementing only stellar populations (see Table [\[tab:sed-no-agn\]](#tab:sed-no-agn)), in general, we struggle to reproduce *Virgil*’s overall SED and behaviour at the MIRI wavelengths. The only code that can reproduce *Virgil*’s photometry and its red MIRI slope with solely stellar populations is synthesizer-AGN ($\chi^2_{\it red} = 6.9$) thanks to a combination of two sub-solar ($Z \simeq 0.4 Z_\odot$) young populations (6, 26 Myr old) with very different extinctions ($A_V = 0.5, 4.0$ mag) and combined with a very strong contribution from the nebular continuum, see Figure [7](#fig:virgil_sed) (top panel). Due to the presence of the heavily attenuated second stellar component, the total mass of *Virgil* retrieved by synthesizer-AGN is $\rm M_\star = 10^{9.7\pm 0.1}~M_\odot$. From the best-fit model, we also derive a total $\rm SFR(UV) \approx 69~M_\odot~ yr^{-1}$ (corrected for dust extinction). This solution would suggest a scenario for *Virgil* as a dusty starburst galaxy. In this case, the blue and red components of the SED would arise from different parts of the galaxy. The relatively small angular size of *Virgil* together with the coarser MIRI resolution and the presence of the lower redshift contaminant (§[3.3](#sec:decontamination)) prevent us, however, from further investigating this scenario based on the currently available data. Nonetheless, we highlight that in this scenario, classical templates of dust emission (cite: Chary+01) with dust temperatures $T_{\rm dust} = 20 - 30$ K dominating the dust mass would not comply with the ALMA upper limits for a total absorbed energy of $L_{\rm dust} \approx 10^{11.5}\rm~L_\odot$. Only assuming models with higher dust temperatures (cite: Siebenmorgen+07; Schreiber+18; Sommovigo+20; Sommovigo+22) would allow to meet the upper limits at wavelengths $> 1$ mm, see Figure [8](#fig:sed_dust_component).

The flexibility of synthesizer-AGN in finding such best-fit result is hardly retrievable with the other SED-fitting codes at our disposal and which struggle to return good best-fit models ($\chi^2_{\it red} \gtrsim 20$), failing in reproducing the photometry at the MIRI wavelengths. In this context, CIGALE, Bagpipes and prospector find very similar best-fit parameters, i.e. $M_\star \simeq  10^9\rm ~M_\odot$, $\rm SFR \simeq 3~ M_\ensuremath{\odot}~ yr^{-1}$, $A_V \leq 0.8\rm~ mag$ and a mass-weighted age of about 300 Myr.

Interestingly, if we try to fit a graybody emission ($f_\lambda \propto \lambda^{-\beta -3} /(e^{\frac{hc}{\lambda k_{\rm B} T}}-1)$, e.g. (cite: Caputi+13)) to the residuals of the MIRI datapoints, i.e. after subtracting the best-fit models derived by these three different codes to the observed photometry, we find a graybody temperature $T = 1762^{+177}_{-143}\rm~ K$ (if we assume $\beta = 1.5$). Such high value of the graybody temperature is comparable to the typical values for the sublimation of dust (cite: Temple+21) and is hardly reconciliable with heating due to normal stellar activity (cite: DeRossi+18; Sommovigo+20).

![](figures/best_fit_dust_decomp.png)

### Stellar Populations and AGN models

To improve the best-fit models, we consider adding an AGN component to the fits. As a first step, we verify if *Virgil* is an already known AGN in the literature. To this purpose, we look for possible counterparts of *Virgil* in the available AGN catalogs in HUDF based on both observations by Chandra (cite: Luo+17; Evans+20) and XMM-Newton (cite: Ranalli+13) but find no X-ray counterpart.

To assess if *Virgil* is a weak X-ray emitter and its absence in the X-ray catalogs is not merely due to the depth of the available Chandra and XMM-Newton observations, we estimate an upper limit over its rest-frame X-ray to optical-UV ratio $\alpha_{\rm ox} = -\log_{10}[L({\rm 2keV}) / L({\rm 2500 \AA})]/2.605$ (cite: Tananbaum+79; Lusso+10). While we derive *Virgil’s* luminosity at 2500Å  $L({\rm 2500 \AA})$ directly from the available JWST/NIRCam photometry ($L({\rm 2500 \AA}) \approx 1.98 \times 10^{28}\rm~erg/s/Hz$), we infer the luminosity at 2keV $L({\rm 2keV})$ by considering three times the limiting flux of the deepest X-ray observations (i.e. Chandra) in the soft band (0.5 - 2 keV) for the XDF (cite: Luo+17) and obtain $L_{\rm 2keV} \approx 3.48 \times 10^{25}\rm~erg/s/Hz$. These estimates imply $\alpha_{\rm ox} \gtrsim 1.25$, a range of values for which the rest-frame UV emission of the galaxy dominates over the X-rays, thus confirming the intrinsic weak X-ray nature of *Virgil*.

In addition to the X-ray-based catalogs of AGN, we searched for possible counterparts for *Virgil* in the catalog by (cite: Lyu+22), which extended AGN detection in the HUDF by analysing galaxies’ rest-frame optical to mid-infrared emission. We also examined the recently released AGN catalog by (cite: Lyu+24), based solely on MIRI imaging from the SMILES program. In both cases, no previously identified AGN is found at the coordinates of our target.

As a result of our SED-fitting runs on the whole available photometry (ALMA upper limits included), we find that all codes prefer the SED solution implementing an AGN to the case of only stellar populations, delivering better quality fits (i.e. lower $\chi^2_{\rm red}$), see Figure [7](#fig:virgil_sed) (bottom panel) and Table [\[tab:sed-agn\]](#tab:sed-agn). In this case, the best-fits are provided by synthesizer-AGN ($\chi2_{\rm red} = 5.4$) and CIGALE ($\chi2_{\rm red} = 6.9$). For synthesizer-AGN, the best-fit indicates a total stellar mass $\rm M_\star \simeq 10^{8.2}~M_\odot$ with two young stellar populations: a 1 Myr old stellar population with a metallicity $Z = 0.2~\rm Z_\odot$ and $A_V = 0.5$, and a 25 Myr old stellar population of solar metallicity and $A_V = 0.9$. The smaller stellar mass of this run with respect to the no-AGN case is due to the dominant contribution at the NIR wavelengths of the AGN component.

In the case of CIGALE, *Virgil*’s best-fit has a stellar mass of $\rm M_\star \simeq 10^{8.5 \pm 0.2}~M_\odot$ and is reproduced with a young (3 Myr) and an older (300 Myr) stellar population with solar metallicities and $A_V = 0.8$. Also for CIGALE, the AGN dominates at the longest MIRI wavelengths , see Figure [9](#fig:sed_agn_component).

We further investigate the properties of the eventual AGN hosted in *Virgil* by estimating its bolometric luminosity $L_{\rm AGN,bol}$ and supermassive black-hole mass $M_{\rm BH}$. Following (cite: Kaspi+00), we derive $L_{\rm AGN,bol}$ from the monochromatic luminosity at 5100Å (corrected for dust extinction) $L$(5100Å) as $L_{\rm AGN, bol} \approx 9 \cdot \lambda \cdot L$(5100Å). In the case of *Virgil*, the estimated luminosity at 5100Å is $L(\rm 5100\AA) \approx 2.9 \times 10^{39}\rm~ erg~s^{-1}~\AA^{-1}$ . However, according to our best-fit with CIGALE, at 5100Å (rest-frame) the AGN contributes only to 40 percent of the observed emission. Besides, the AGN’s dust attenuation is $A(5100{\rm \AA}) \approx 3.3\rm~mag$. Therefore, correcting for AGN contribution and dust obscuration, we estimate $L_{\rm AGN}({\rm 5100\AA}) \approx 2.4 \times 10^{40}\rm~ erg~s^{-1}~\AA^{-1}$ that converts into an $L_{\rm AGN,bol} \approx 1.1 \times 10^{45}\rm~ erg~s^{-1}$. We recover similar values also when considering the best-fit results from SYNTHESIZER-AGN: $L_{\rm AGN}({\rm 5100\AA}) \approx 1.9 \times 10^{40}\rm~ erg~s^{-1}~\AA^{-1}$ and $L_{\rm AGN,bol} \approx 8.9 \times 10^{44}\rm~ erg~s^{-1}$. By comparing the so-derived AGN bolometric luminosity to the Eddington luminosity $L_{\rm Edd}$ (cite: Eddington+26), we can infer $M_{\rm BH}$ via the relation $M_{\rm BH} = 7.9 \times 10^{-39} \times (L_{\rm AGN,bol} / \lambda_{\rm Edd})$, where $\lambda_{\rm Edd}$ is the Eddington ratio.

Considering typical values for the Eddington ratio $\lambda_{\rm Edd} = 0.1 - 1$, the range of values we obtain for the mass of the supermassive black hole of our target varies from $M_{\rm BH} \approx (7 - 9)\times 10^6\rm~ M_\odot$ ($\lambda_{\rm Edd} = 1$) to $M_{\rm BH} \approx (7 - 9) \times 10^7\rm~ M_\odot$ ($\lambda_{\rm Edd} = 0.1$). These estimates are in good agreement with the values of bolometric luminosity of AGNs at $z > 4$ recently studied with JWST (cite: Greene+24; Furtak+24; Kokorev+23; Matthee+24).

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Code | $\chi^2_{\rm red}$ | $\log_{10}(\rm M_\star)$ | $\rm A_{V, main}$ | Age$_{\rm main}$ | $\rm A_{V, young}$ | Age$_{\rm young}$ | Age$_{\rm mass-weighted}$ | SFR$_{\rm 100Myr}$ |
|  |  | $\log_{10}(\rm [M_\odot])$ | \[mag\] | \[Myr\] | \[mag\] | \[Myr\] | \[Myr\] | \[M$_\odot~\rm yr^{-1}$\] |
| SYNTHESIZER-AGN | 6.5 | $9.71 \pm 0.10$ | $4.00 \pm 0.1$ | $26 \pm 4$ | $0.50 \pm 0.01$ | $6 \pm 1$ | $32^{+9}_{-7}$ | \- |
| CIGALE | 19.4 | $8.95 \pm 0.08$ | $0.81 \pm 0.04$ | $304 \pm 223$ | \- | $3 \pm 1$ | $275 \pm 104$ | $2.60 \pm 0.87$ |
| BAGPIPES | 20.6 | $8.74^{+0.38}_{-0.12}$ | $0.73^{+0.05}_{-0.09}$ | $720^{+70}_{-230}$ | \- | $20^{+2}_{-1}$ | $220^{+370}_{-130}$ | $3.42^{+0.67}_{-1.35}$ |
| PROSPECTOR | 25.1 | $9.01^{+0.03}_{-0.16}$ | $0.12^{+0.02}_{-0.01}$ | \- | \- | \- | $367^{+51}_{-33}$ | $2.53^{+0.51}_{-1.90}$ |

: Stellar SED properties of *Virgil* - only stars

Table notes: In the above table, we report the main physical properties of *Virgil* as derived from the different SED fitting codes adopted in our study: SYNTHESIZER-AGN, CIGALE, BAGPIPES, and PROSPECTOR. In this table, we present the results derived when considering only the contribution of stellar populations to the overall *Virgil*’s SED. Specifically, we report the logarithm of the stellar mass $\log_{10}(\rm M_\star)$, the extinction of the main stellar component $\rm A_{V,main}$ and its age Age$_{\rm main}$, the extinction of the young stellar component $\rm A_{V,young}$ and its age Age$_{\rm young}$, the mass-weighted age of the overall galaxy $\rm Age_{mass-weighted}$ and its average star formation rate over the last 100 Myr SFR$_{\rm 100Myr}$. We leave an empty entry for parameters where the codes do not provide an estimate.

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Code | $\chi^2_{\rm red}$ | $\log_{10}(\rm M_\star)$ | $\rm A_{V, main}$ | Age$_{\rm main}$ | $\rm A_{V, young}$ | Age$_{\rm young}$ | Age$_{\rm mass-weighted}$ | SFR$_{\rm 100Myr}$ |
|  |  | $\log_{10}(\rm [M_\odot])$ | \[mag\] | \[Myr\] | \[mag\] | \[Myr\] | \[Myr\] | \[M$_\odot~\rm yr^{-1}$\] |
| synthesizer-AGN | 5.4 | $8.19 \pm 0.07$ | $0.90\pm 0.10$ | $2.5 \pm 0.5$ | $0.46 \pm 0.03$ | $1 \pm 0.5$ | $0.8^{+0.8}_{-0.2}$ | \- |
| cigale | 6.9 | $8.50 \pm 0.02$ | $0.83 \pm 0.04$ | $662 \pm 230$ | \- | $1.5 \pm 0.5$ | $309 \pm 121$ | $0.88 \pm 0.04$ |
| bagpipes | 12.1 | $10.25^{+0.04}_{-0.05}$ | $3.57^{+0.18}_{-0.17}$ | $790^{+20}_{-30}$ | \- | $260^{+20}_{-60}$ | $640^{+20}_{-110}$ | \- |
| prospector | 23.4 | $8.77^{+0.06}_{-0.11}$ | $0.11^{+0.01}_{-0.02}$ | \- | \- | \- | $284^{+31}_{-32}$ | $2.50^{+0.53}_{-1.75}$ |

: Stellar SED properties of *Virgil* - stars & AGN

Table notes: As in Table [\[tab:sed-no-agn\]](#tab:sed-no-agn), we report the main physical properties of *Virgil* as derived from the different SED fitting codes adopted in our study. In this table, we present the results derived when adding to the contribution of stellar populations also an AGN component.

### *Virgil*, an LRD?

The flat rest-frame UV and the red NIR colors of *Virgil* revealed by our multi-wavelength dataset (HST, JWST NIRCam and MIRI) are similar to the “v-shaped” SED (in the $\lambda - f_{\lambda}$ plane) of the recently discovered population of LRDs (cite: Labbe+23b; Furtak+23; Kokorev+24; Perez-Gonzalez+24b; Akins+24; Matthee+24). Despite the rapid emergence of LRDs in the literature over the past two years, their nature and unusual SEDs remain largely unexplained. Proposed explanations suggest a complex interplay between AGN activity, stellar populations, and dust (cite: Labbe+23b; Li+24; Inayoshi+24). While this debate continues, the detection of broad Balmer lines (e.g., H$\alpha$, H$\beta$) in some LRDs has been interpreted as strong evidence for AGN activity, implying accretion onto supermassive black holes (cite: Furtak+23b; Fujimoto+23; Greene+24; Killi+23; Kokorev+23; Matthee+24).

Following (cite: Kokorev+24), *Virgil*’s photometry complies with most of the color criteria used to characterise LRDs at $z > 6$. In particular, for *Virgil* we find:

- F150W - F200W $= 0.05 \pm 0.10~ (< 0.8)$;

- F277W - F356W $= 0.92 \pm 0.07~  (> 0.6)$;

- F277W - F444W $= 0.22 \pm 0.07~ (> 0.7)$;

- F115W - F200W $= -0.01\pm 0.10~ (> -0.5)$;

where the values in parentheses indicate the selection criteria from (cite: Kokorev+24), designed to identify “v-shaped” SEDs while minimizing contamination from brown dwarfs (particularly the F115W - F200W condition). The only discrepancy is *Virgil*’s F277W - F444W color, which appears bluer than expected for LRDs. However, at the specific redshift of our target ($z = 6.63124$), this could be explained by the positioning of the filters relative to strong nebular lines. The F444W filter probes wavelengths redward of \[O III\] and blueward of H$\alpha$. At the wavelengths of these strong optical emission lines, the transmission drops below 5%, making the F444W quite robustly probe the optical continuum without significant contamination from such strong transitions. This may result in a bluer color. Indeed, replacing F444W with the adjacent MIRI filter F560W reveals a significantly redder color: F277W - F560W $= 1.10 \pm 0.06$.

At rest-frame UV wavelengths, *Virgil* meets the brown dwarf rejection criteria from (cite: Kokorev+24). However, it does not strictly comply with the F150W - F200W color threshold proposed by (cite: Langeroodi2023c), who suggests that objects with F150W - F200W  $< 0.25$ are typically brown dwarfs. Nonetheless, *Virgil*’s F277W - F444W color places it outside the region occupied by brown dwarfs in the F277W - F444W vs. F150W - F200W diagram (see Figure 13 of (cite: Langeroodi2023c)). Additionally, its extended morphology further rules out the brown dwarf hypothesis.

The estimate of the compactness parameter ($c = f(r=0.2\ensuremath{''})/f(r=0.1\ensuremath{''})$ with fluxes properly corrected for aperture) derived from the F444W image after removing contamination from the nearby LAE (see §[3.3](#sec:decontamination)) yields $c_{\rm F444W} \approx 1.5$, thus satisfying the LRD compactness criterion $c_{\rm F444W} < 1.7$.

Despite not fully meeting the LRDs’ F277W - F444W color, *Virgil* complies with all the other LRD criteria adopted in the recent literature. This shows that our target is likely to be the first LRD with a detectable host galaxy from rest-frame UV-to-optical wavelengths (see § [3.4](#sec:morphology)). In this regard, (cite: Killi+23) already reported an LRD at $z \approx 4.5$ with a slightly more extended rest-frame UV morphology than previously assumed for this class of sources. Furthermore, following our discovery of *Virgil*, additional LRDs have been identified with extended and more complex UV morphologies than simple PSF-like profiles (cite: Rinaldi+25). *Virgil*, however, would be the first LRD with a clear detection of its host galaxy, having a resolved morphology down to its rest-frame optical wavelengths. Overall, these findings suggest a broader diversity among LRDs than initially anticipated.

To further corroborate *Virgil*’s resemblance to LRDs, we compare its photometry to empirical SEDs derived from stacked LRDs, including the average SED of 20 MIRI-detected LRDs in the HUDF (cite: Perez-Gonzalez+24a) and the “maximal” SED from stacking 500 LRDs in the COSMOS-Webb field (cite: Akins+24) (see Figure [10](#fig:empirical_models)). After redshifting these empirical SEDs to $z = 6.63124$ and normalizing their fluxes to match *Virgil*’s photometry, we find a strong agreement at rest-frame optical/NIR wavelengths. However, at shorter wavelengths (rest-frame UV), the empirical SEDs lie below *Virgil*’s observed photometry. This could be the wavelength regime where *Virgil*’s underlying stellar emission could contribute more to its overall emission, suggesting that its stronger UV emission could be mainly attributed to young stellar populations as also found from our SED fitting (see § [3.7](#sec:sed)).

We also compare *Virgil*’s photometry with the NIRCam/MSA spectra of two LRDs detected in the HUDF (cite: Rinaldi+25). The best match is with GS197348 (cite: Bunker+23; Rinaldi+25), which closely reproduces *Virgil*’s SED, even at rest-frame UV wavelengths. This further highlights that while LRDs share similar optical/NIR properties, their UV emission can vary significantly from object to object.

Interestingly, *Virgil*’s non-detection in X-rays (§[4.2](#sec:full_sed)) is consistent with recent findings for LRDs (cite: Yue+24; Ananna+24). Similarly, also the non-detection at far-infrared wavelengths (ALMA upper limits) is in agreement with general LRD findings (cite: Labbe+23b; Perez-Gonzalez+24a; Williams+24).

Once again, we emphasize the critical role of MIRI data in this classification. Without MIRI imaging, identifying *Virgil* as a “v-shaped” object would have been impossible. In addition, we highlight that existing LRD selection criteria (based solely on NIRCam photometry) extend only to rest-frame optical wavelengths near H$\alpha$ at $z > 6$. This means that they miss the rising NIR red continuum of LRDs and are susceptible to contamination from strong line-emitters (cite: Hainline+25). Incorporating MIRI data is therefore essential for robustly identifying this population at $z > 6$.

![](figures/best_fit_sed_decomp.png)

![](figures/best_fit_sed_lrds.pdf)

## The impact of long-wavelengths MIRI filters

A final remark comes from the information that we can obtain thanks to the presence of the longest MIRI wavelengths (i.e. F1280W, F1500W). Despite the shallower depth of the available imaging above 10 $\mu$m, we find that the steep rise observed up to F1000W could tend to flatten at longer wavelengths (above the rest-frame 1.6 $\mu$m). Interestingly, such flattening of the SED was also reported in the average trend of the MIRI-detected LRDs by (cite: Williams+24) and (cite: Perez-Gonzalez+24a). Also (cite: Wang+24) revealed an unexpected flattening at rest-frame wavelengths 0.7 - 5 $\mu$m in their spectro-photometric study of an LRD at $z \approx 3.1$. The origin of this flattening is still debated but, in the AGN scenario, one possible explanation (cite: Wang+24) could be a lack of torus emission as in the case of hot-dust-deficient AGNs (cite: Jiang+10; Lyu+17; Son+23).

Due to the higher redshift of our target, we have a hint of flattening only from the F1280W and F1500W filters, probing the rest-frame 1.6 - 2 $\mu$m wavelength range. We retrieve an estimate of the flux in F1280W (S/N $\approx 2.4$) and F1500W (S/N $\approx 1.3$) that imply colors of F1000W - F1280W $= 0.1 \pm 0.2$ and F1000W - F1500W $= 0.1 \pm 0.3$. The shallower depth of the available MIRI filters $\lambda > 18~\mu$m prevents us from robustly confirming the flattening on a longer wavelength range. Deeper F1800W and F2100W imaging would be necessary to extend this finding up to $3 \mu$m (rest-frame).

We underline how, if the flattening trend is confirmed, without any information at these wavelengths the SED codes would tend to prefer models that keep on rising thus over-predicting the flux at the longest wavelengths and overestimating the importance of the AGN dust torus, see Figure [11](#fig:sedmiri_short). This further underlines the importance of conducting deep MIRI imaging above the 10 $\mu$m even if challenged by the less sensitivity of the MIRI instrument at such wavelengths.

![](figures/best_fit_sed_agn_short.png)

# Summary and Conclusions

In this paper, we have presented the analysis of *Virgil*, a MIRI extremely red object (MERO) detected with the F1000W filter as part of the MIRI Deep Imaging Survey (MIDIS) observations of the Hubble Ultra Deep Field. *Virgil* is a Ly$\alpha$ emitter at $z = 6.63124 \pm 0.00188$ (VLT/MUSE, (cite: Bacon+23)) showing a red F444W - F1000W $= 2.33\pm0.06$ color.

At NIRCam wavelengths, *Virgil* presents an elongated morphology in the south-west direction and features a tail that ends up in a (faint) compact source (*Beatrix*; $\alpha$(J2000.0) = 03:32:37.8844 (hours); $\delta$(J2000.0) = -27:47:10.979). With the current data, it is, however, difficult to assess if this compact object is a clump of *Virgil*, a clump of a nearby ($\delta$ = 0.4$''$ - 0.7$''$) foreground ($z \simeq 4.77$) LAE (cite: Matthee+22) , or a different source. By modeling the rest-frame UV-optical morphology of *Virgil* with a Sérsic profile we find a best-fit Sérsic index $n = 0.93^{+0.85}_{-0.31}$ and an effective radius $r_e = 0.49^{+0.05}_{-0.11}$ pkpc in agreement with the values recently reported for other galaxies at similar redshifts (cite: Sun+24). At MIRI wavelengths $> 7\mu$m, the morphology of *Virgil* is dominated by the MIRI PSF.

The extracted photometry of *Virgil* shows a blue UV continuum ($\beta_{\rm UV} = -2.1 \pm 0.3$), the presence of strong emission lines (flux excess of the F356W band corresponding to the H$\beta$ + \[O III\] complex) and a steep rising SED from 0.7 to 1.3 $\mu$m (rest-frame). SED fitting models considering only stellar populations struggle to explain *Virgil*’s behaviour at MIRI wavelengths. The best-fit model suggest that *Virgil*’ SED originates from two components: an extremely young (6 Myr) and unobscured stellar population dominating the blue wavelengths, and another young (26 Myr) stellar population strongly affected by extinction (A$_V = 4$ mag) that is responsible for most of the light at red wavelengths. In agreement with recent papers on LRDs (cite: Williams+24; Perez-Gonzalez+24a; Barro+23), in this scenario the bulk of the dust re-emitting the absorbed light at rest-frame UV and optical wavelengths should be hotter than 60 - 70 K to comply with the ALMA upper limits. This temperature is significantly higher than the one typically adopted for SED fitting (cite: Chary+01). In this case, *Virgil* could be similar to a dusty starburst. The small angular size of *Virgil* together with the coarser MIRI resolution hamper us from deriving if the two populations are located in different parts of the galaxy. All the other codes fail to reproduce the steep and rising MIRI photometry.

Such red rising part of *Virgil*’s SED could hint at the presence of a (dust-obscured) AGN. Despite extensive searches, no AGN counterparts are found in existing multi-wavelength catalogs (cite: Ranalli+13; Luo+17; Evans+20; Lyu+22; Lyu+24). However, when implementing an AGN contribution to the SED, all the SED-fitting codes adopted deliver significantly improved best-fit models. Assuming the presence of an AGN, we estimate a bolometric luminosity $L_{\rm bol, AGN} \approx (8.9 - 11) \times 10^{44}\rm~ erg~s^{-1}$, and an $M_{\rm BH} = (7 - 9)\times 10^6\rm~M_\odot$ (if $\lambda_{\rm Edd} = 1$). These estimates agree with those reported in the recent literature targeting reddened AGNs at $z > 4$ (cite: Kokorev+23; Scholtz+23; Matthee+24; Furtak+24; Rinaldi+25). Nonetheless, with the currently available data is difficult to fully rule out one of the proposed scenarios. We cannot even exclude that the two conditions (dusty starburst and AGN) could be true at the same time, i.e. not too differently from what was recently reported for the GN20 galaxy at $z = 4.05$ (cite: Colina+23; Bik+24; Crespo+24; Ubler+23).

*Virgil*’s flat rest-frame UV and red NIR colors and, in general, the shape of its SED, suggest that our target belongs to the recently discovered population of LRDs (cite: Labbe+23b; Kokorev+24; Perez-Gonzalez+24a). This is further confirmed by the comparison of *Virgil*’ SED with the recently reported empirical SED (cite: Perez-Gonzalez+24a; Akins+24) and the actual spectra of other LRDs (cite: Rinaldi+25). However, the extended morphology of *Virgil* at UV-to-optical wavelengths makes it the first LRD for which we can clearly detect the host galaxy.

Despite the richness of the photometric dataset available, deeper MIRI long-wavelength observations in combination with a rest-frame optical and near-infrared spectroscopic follow-up (cite: Wang+24; Tacchella+24; Li+24) appear to be fundamental to properly assess the nature of *Virgil*.

All in all, our findings show the power of MIRI imaging in unveiling the complexity of this galaxy’s nature. For our target, MIRI provides a fundamental piece of information that would be otherwise completely missed without imaging at such long wavelengths. This discovery opens up to the question of how many objects like *Virgil* there are in the Universe. If a systematic search for similar objects in deep MIRI surveys would reveal several *Virgil*-like objects and their AGN-nature is confirmed, this discovery could potentially bring us to reassess (once more) the role of AGN to the reionization. In addition to a more general importance of MIRI in the characterisation of galaxy properties, this study also advocates for the importance of conducting deep and extended MIRI surveys at $\lambda > 10~\mu$m wavelengths, a regime that results in being crucial in correctly determining the physical properties of galaxies and unveiling their hidden components. In fact, the absence of MIRI long-wavelength photometry (even in the case of upper limits) biases us to overestimate the contribution of AGN in the SED of such objects.

# Acknowledgments

The authors thank R. Cooper, G. Yang, V. Kokorev, D. Wen, C. Williams, H. Übler for useful discussions and comments.

E.I. and K.I.C. acknowledge funding from the Netherlands Research School for Astronomy (NOVA). K.I.C. acknowledges funding from the Dutch Research Council (NWO) through the award of the Vici Grant VI.C.212.036. A.A.-H. acknowledges support from grant PID2021-124665NB-I00 funded by MCIN/AEI/10.13039/ 501100011033 and by “ERDF A way of making Europe”. P.G.P-G. acknowledges support from grant PID2022-139567NB-I00 funded by Spanish Ministerio de Ciencia e Innovación MCIN/AEI/10.13039/501100011033, FEDER *Una manera de hacer Europa*. J.A.-M., A.C.-G. and L. Colina, acknowledge support by grant PIB2021-127718NB-100 from the Spanish Ministry of Science and Innovation/State Agency of Research MCIN/AEI/10.13039/501100011033 and by “ERDF A way of making Europe”. L. Colina thanks the support from the Cosmic Dawn Center received during visits to DAWN as international associate. L. Costantin acknowledges support by grants PIB2021-127718NB-100 and PID2022-139567NB-I00 from the Spanish Ministry of Science and Innovation/State Agency of Research MCIN/AEI/10.13039/501100011033 and by “ERDF A way of making Europe”. T.R.G acknowledges support from the Carlsberg Foundation (grant no CF20-0534). S.G. acknowledges financial support from the Cosmic Dawn Center (DAWN), funded by the Danish National Research Foundation (DNRF) under grant No. 140. This work was supported by research grants (VIL16599, VIL54489) from VILLUM FONDEN. J.P.P. and T.V.T. acknowledge financial support from the UK Science and Technology Facilities Council, and the UK Space Agency.

This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with programs GO #1963, GO #1895 and GTO #1283. The authors acknowledge the team led by coPIs C. Williams, M. Maseda and S. Tacchella, and PI P. Oesch, for developing their respective observing programs with a zero-exclusive-access period. Also based on observations made with the NASA/ESA Hubble Space Telescope obtained from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5–26555. The work presented here is the effort of the entire MIRI team and the enthusiasm within the MIRI partnership is a significant factor in its success. MIRI draws on the scientific and technical expertise of the following organisations: Ames Research Center, USA; Airbus Defence and Space, UK; CEA-Irfu, Saclay, France; Centre Spatial de Liège, Belgium; Consejo Superior de Investigaciones Cientı́ficas, Spain; Carl Zeiss Optronics, Germany; Chalmers University of Technology, Sweden; Danish Space Research Institute, Denmark; Dublin Institute for Advanced Studies, Ireland; European Space Agency, Netherlands; ETCA, Belgium; ETH Zurich, Switzerland; Goddard Space Flight Center, USA; Institute d’Astrophysique Spatiale, France; Instituto Nacional de Técnica Aeroespacial, Spain; Institute for Astronomy, Edinburgh, UK; Jet Propulsion Laboratory, USA; Laboratoire d’Astrophysique de Marseille (LAM), France; Leiden University, Netherlands; Lockheed Advanced Technology Center (USA); NOVA Opt-IR group at Dwingeloo, Netherlands; Northrop Grumman, USA; Max-Planck Institut für Astronomie (MPIA), Heidelberg, Germany; Laboratoire d’Etudes Spatiales et d’Instrumentation en Astrophysique (LESIA), France; Paul Scherrer Institut, Switzerland; Raytheon Vision Systems, USA; RUAG Aerospace, Switzerland; Rutherford Appleton Laboratory (RAL Space), UK; Space Telescope Science Institute, USA; Toegepast-Natuurwetenschappelijk Onderzoek (TNO-TPD), Netherlands; UK Astronomy Technology Centre, UK; University College London, UK; University of Amsterdam, Netherlands; University of Arizona, USA; University of Cardiff, UK; University of Cologne, Germany; University of Ghent; University of Groningen, Netherlands; University of Leicester, UK; University of Leuven, Belgium; University of Stockholm, Sweden; Utah State University, USA.

For the purpose of open access, the author has applied a Creative Commons Attribution (CC BY) licence to the Author Accepted Manuscript version arising from this submission.

# Facilities

*VLT*, *HST*, *JWST*, *ALMA* .

# Software

ASTROPY (cite: astropy:2013; astropy:2018; astropy:2022), NUMPY (cite: Harris+20), PANDAS (cite: McKinney+10; reback2020pandas) PHOTUTILS (cite: Bradley+22), SCIPY (cite: Virtanen+20), WEBBPSF (cite: Perrin+14), SOURCE EXTRACTOR (cite: Bertin+96), LENSTRONOMY (cite: Birrer+18), SEP (cite: Barbary+17), LEPHARE (cite: Ilbert+06; LePHARE),

EAZY (cite: Brammer+08), BAGPIPES (cite: Carnall+18), CIGALE (cite: Burgarella+05; Noll+09; Boquien+19), PROSPECTOR (cite: Johnson+21), SYNTHESIZER-AGN (cite: Perez-Gonzalez+03; Perez-Gonzalez+08), ASTROPHOT (cite: Stone+23), TOPCAT (cite: Taylor+11).

natexlab

(ref: Akins+23) Akins, H. B., Casey, C. M., Allen, N., et al. 2023, ApJ, 956, 61, doi: [`10.3847/1538-4357/acef21`](http://doi.org/10.3847/1538-4357/acef21)

(ref: Akins+24) Akins, H. B., Casey, C. M., Lambrides, E., et al. 2024, arXiv e-prints, arXiv:2406.10341. [`https://arxiv.org/abs/2406.10341`](https://arxiv.org/abs/2406.10341)

(ref: Alberts+24) Alberts, S., Lyu, J., Shivaei, I., et al. 2024, ApJ, 976, 224, doi: [`10.3847/1538-4357/ad7396`](http://doi.org/10.3847/1538-4357/ad7396)

(ref: Alvarez-Marquez+24) Álvarez-Márquez, J., Colina, L., Crespo Gómez, A., et al. 2023a, arXiv e-prints, arXiv:2309.06319, doi: [`10.48550/arXiv.2309.06319`](http://doi.org/10.48550/arXiv.2309.06319)

(ref: Alvarez-Marquez+23) —. 2023b, arXiv e-prints, arXiv:2309.06319, doi: [`10.48550/arXiv.2309.06319`](http://doi.org/10.48550/arXiv.2309.06319)

(ref: Ananna+24) Ananna, T. T., Bogdán, Á., Kovács, O. E., Natarajan, P., & Hickox, R. C. 2024, arXiv e-prints, arXiv:2404.19010, doi: [`10.48550/arXiv.2404.19010`](http://doi.org/10.48550/arXiv.2404.19010)

(ref: LePHARE) Arnouts, S., & Ilbert, O. 2011, LePHARE: Photometric Analysis for Redshift Estimate, Astrophysics Source Code Library, record ascl:1108.009

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: astropy:2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, apj, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Atek+23a) Atek, H., Shuntov, M., Furtak, L. J., et al. 2023a, MNRAS, 519, 1201, doi: [`10.1093/mnras/stac3144`](http://doi.org/10.1093/mnras/stac3144)

(ref: Atek+23b) Atek, H., Chemerynska, I., Wang, B., et al. 2023b, MNRAS, 524, 5486, doi: [`10.1093/mnras/stad1998`](http://doi.org/10.1093/mnras/stad1998)

(ref: 2010SPIE.7735E..08B) Bacon, R., Accardo, M., Adjali, L., et al. 2010, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7735, Ground-based and Airborne Instrumentation for Astronomy III, ed. I. S. McLean, S. K. Ramsay, & H. Takami, 773508, doi: [`10.1117/12.856027`](http://doi.org/10.1117/12.856027)

(ref: Bacon+17) Bacon, R., Conseil, S., Mary, D., et al. 2017, A&A, 608, A1, doi: [`10.1051/0004-6361/201730833`](http://doi.org/10.1051/0004-6361/201730833)

(ref: Bacon+23) Bacon, R., Brinchmann, J., Conseil, S., et al. 2023a, A&A, 670, A4, doi: [`10.1051/0004-6361/202244187`](http://doi.org/10.1051/0004-6361/202244187)

(ref: 2023A&A...670A...4B) —. 2023b, A&A, 670, A4, doi: [`10.1051/0004-6361/202244187`](http://doi.org/10.1051/0004-6361/202244187)

(ref: Bagley+24) Bagley, M. B., Pirzkal, N., Finkelstein, S. L., et al. 2024, ApJL, 965, L6, doi: [`10.3847/2041-8213/ad2f31`](http://doi.org/10.3847/2041-8213/ad2f31)

(ref: Barbary+17) Barbary, K., Boone, K., Craig, M., Deil, C., & Rose, B. 2017, kbarbary/sep: v1.0.2, v1.0.2, Zenodo, doi: [`10.5281/zenodo.896928`](http://doi.org/10.5281/zenodo.896928)

(ref: Barro+23) Barro, G., Perez-Gonzalez, P. G., Kocevski, D. D., et al. 2023, arXiv e-prints, arXiv:2305.14418, doi: [`10.48550/arXiv.2305.14418`](http://doi.org/10.48550/arXiv.2305.14418)

(ref: Beckwith+06) Beckwith, S. V. W., Stiavelli, M., Koekemoer, A. M., et al. 2006, AJ, 132, 1729, doi: [`10.1086/507302`](http://doi.org/10.1086/507302)

(ref: Bellovary+25) Bellovary, J. 2025, arXiv e-prints, arXiv:2501.03309, doi: [`10.48550/arXiv.2501.03309`](http://doi.org/10.48550/arXiv.2501.03309)

(ref: 1996A&AS..117..393B) Bertin, E., & Arnouts, S. 1996a, A&AS, 117, 393, doi: [`10.1051/aas:1996164`](http://doi.org/10.1051/aas:1996164)

(ref: Bertin+96) —. 1996b, A&AS, 117, 393, doi: [`10.1051/aas:1996164`](http://doi.org/10.1051/aas:1996164)

(ref: Bik+24) Bik, A., Álvarez-Márquez, J., Colina, L., et al. 2024, A&A, 686, A3, doi: [`10.1051/0004-6361/202348845`](http://doi.org/10.1051/0004-6361/202348845)

(ref: Birrer+18) Birrer, S., & Amara, A. 2018, Physics of the Dark Universe, 22, 189, doi: [`10.1016/j.dark.2018.11.002`](http://doi.org/10.1016/j.dark.2018.11.002)

(ref: Boogaard+23) Boogaard, L. A., Gillman, S., Melinder, J., et al. 2023, arXiv e-prints, arXiv:2308.16895, doi: [`10.48550/arXiv.2308.16895`](http://doi.org/10.48550/arXiv.2308.16895)

(ref: Boquien+19) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103, doi: [`10.1051/0004-6361/201834156`](http://doi.org/10.1051/0004-6361/201834156)

(ref: Bouchet+15) Bouchet, P., Garcı́a-Marı́n, M., Lagage, P. O., et al. 2015, PASP, 127, 612, doi: [`10.1086/682254`](http://doi.org/10.1086/682254)

(ref: Boyett+24) Boyett, K., Bunker, A. J., Curtis-Lake, E., et al. 2024, arXiv e-prints, arXiv:2401.16934, doi: [`10.48550/arXiv.2401.16934`](http://doi.org/10.48550/arXiv.2401.16934)

(ref: Bradley+22) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2022, astropy/photutils: 1.5.0, 1.5.0, Zenodo, doi: [`10.5281/zenodo.6825092`](http://doi.org/10.5281/zenodo.6825092)

(ref: Brammer+08) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503, doi: [`10.1086/591786`](http://doi.org/10.1086/591786)

(ref: Bruzual+03) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000, doi: [`10.1046/j.1365-8711.2003.06897.x`](http://doi.org/10.1046/j.1365-8711.2003.06897.x)

(ref: Bunker+23) Bunker, A. J., Saxena, A., Cameron, A. J., et al. 2023, A&A, 677, A88, doi: [`10.1051/0004-6361/202346159`](http://doi.org/10.1051/0004-6361/202346159)

(ref: Burgarella+05) Burgarella, D., Buat, V., & Iglesias-Páramo, J. 2005, MNRAS, 360, 1413, doi: [`10.1111/j.1365-2966.2005.09131.x`](http://doi.org/10.1111/j.1365-2966.2005.09131.x)

(ref: Byler+17) Byler, N., Dalcanton, J. J., Conroy, C., & Johnson, B. D. 2017, ApJ, 840, 44, doi: [`10.3847/1538-4357/aa6c66`](http://doi.org/10.3847/1538-4357/aa6c66)

(ref: Calzetti+00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: Caputi+13) Caputi, K. I. 2013, ApJ, 768, 103, doi: [`10.1088/0004-637X/768/2/103`](http://doi.org/10.1088/0004-637X/768/2/103)

(ref: Caputi+04) Caputi, K. I., Dunlop, J. S., McLure, R. J., & Roche, N. D. 2004, MNRAS, 353, 30, doi: [`10.1111/j.1365-2966.2004.08044.x`](http://doi.org/10.1111/j.1365-2966.2004.08044.x)

(ref: Caputi+24) Caputi, K. I., Rinaldi, P., Iani, E., et al. 2024, ApJ, 969, 159, doi: [`10.3847/1538-4357/ad4eb2`](http://doi.org/10.3847/1538-4357/ad4eb2)

(ref: Carnall+18) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379, doi: [`10.1093/mnras/sty2169`](http://doi.org/10.1093/mnras/sty2169)

(ref: Carnall+23) Carnall, A. C., McLure, R. J., Dunlop, J. S., et al. 2023, Nature, 619, 716, doi: [`10.1038/s41586-023-06158-6`](http://doi.org/10.1038/s41586-023-06158-6)

(ref: Casey+23a) Casey, C. M., Akins, H. B., Shuntov, M., et al. 2023, arXiv e-prints, arXiv:2308.10932, doi: [`10.48550/arXiv.2308.10932`](http://doi.org/10.48550/arXiv.2308.10932)

(ref: Castellano+12) Castellano, M., Fontana, A., Grazian, A., et al. 2012, A&A, 540, A39, doi: [`10.1051/0004-6361/201118050`](http://doi.org/10.1051/0004-6361/201118050)

(ref: Castellano+24) Castellano, M., Napolitano, L., Fontana, A., et al. 2024, arXiv e-prints, arXiv:2403.10238, doi: [`10.48550/arXiv.2403.10238`](http://doi.org/10.48550/arXiv.2403.10238)

(ref: Chabrier+03) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Chary+01) Chary, R., & Elbaz, D. 2001, ApJ, 556, 562, doi: [`10.1086/321609`](http://doi.org/10.1086/321609)

(ref: Chatzikos+23) Chatzikos, M., Bianchi, S., Camilloni, F., et al. 2023, , 59, 327, doi: [`10.22201/ia.01851101p.2023.59.02.12`](http://doi.org/10.22201/ia.01851101p.2023.59.02.12)

(ref: Colina+23) Colina, L., Crespo Gómez, A., Álvarez-Márquez, J., et al. 2023, A&A, 673, L6, doi: [`10.1051/0004-6361/202346535`](http://doi.org/10.1051/0004-6361/202346535)

(ref: Costantin+24) Costantin, L., Gillman, S., Boogaard, L. A., et al. 2024, arXiv e-prints, arXiv:2407.00153, doi: [`10.48550/arXiv.2407.00153`](http://doi.org/10.48550/arXiv.2407.00153)

(ref: Crespo+24) Crespo, D., González-Nuevo, J., Bonavera, L., Cueli, M. M., & Casas, J. M. 2024, A&A, 684, A109, doi: [`10.1051/0004-6361/202347426`](http://doi.org/10.1051/0004-6361/202347426)

(ref: Curtis_Lake+23) Curtis-Lake, E., Carniani, S., Cameron, A., et al. 2023, Nature Astronomy, 7, 622, doi: [`10.1038/s41550-023-01918-w`](http://doi.org/10.1038/s41550-023-01918-w)

(ref: DeRossi+18) De Rossi, M. E., Rieke, G. H., Shivaei, I., Bromm, V., & Lyu, J. 2018, ApJ, 869, 4, doi: [`10.3847/1538-4357/aaebf8`](http://doi.org/10.3847/1538-4357/aaebf8)

(ref: Decarli+19) Decarli, R., Walter, F., Gónzalez-López, J., et al. 2019, ApJ, 882, 138, doi: [`10.3847/1538-4357/ab30fe`](http://doi.org/10.3847/1538-4357/ab30fe)

(ref: Decarli+20) Decarli, R., Aravena, M., Boogaard, L., et al. 2020, ApJ, 902, 110, doi: [`10.3847/1538-4357/abaa3b`](http://doi.org/10.3847/1538-4357/abaa3b)

(ref: DEugenio+24) D’Eugenio, F., Cameron, A. J., Scholtz, J., et al. 2024, arXiv e-prints, arXiv:2404.06531, doi: [`10.48550/arXiv.2404.06531`](http://doi.org/10.48550/arXiv.2404.06531)

(ref: Dicken+24) Dicken, D., Garcı́a Marı́n, M., Shivaei, I., et al. 2024, arXiv e-prints, arXiv:2403.16686, doi: [`10.48550/arXiv.2403.16686`](http://doi.org/10.48550/arXiv.2403.16686)

(ref: Draine+14) Draine, B. T., Aniano, G., Krause, O., et al. 2014, ApJ, 780, 172, doi: [`10.1088/0004-637X/780/2/172`](http://doi.org/10.1088/0004-637X/780/2/172)

(ref: Eddington+26) Eddington, A. S. 1926, The Internal Constitution of the Stars

(ref: 2023arXiv230602465E) Eisenstein, D. J., Willott, C., Alberts, S., et al. 2023a, arXiv e-prints, arXiv:2306.02465, doi: [`10.48550/arXiv.2306.02465`](http://doi.org/10.48550/arXiv.2306.02465)

(ref: 2023arXiv231012340E) Eisenstein, D. J., Johnson, B. D., Robertson, B., et al. 2023b, arXiv e-prints, arXiv:2310.12340, doi: [`10.48550/arXiv.2310.12340`](http://doi.org/10.48550/arXiv.2310.12340)

(ref: Eisenstein+23) Eisenstein, D. J., Willott, C., Alberts, S., et al. 2023c, arXiv e-prints, arXiv:2306.02465, doi: [`10.48550/arXiv.2306.02465`](http://doi.org/10.48550/arXiv.2306.02465)

(ref: Elston+88) Elston, R., Rieke, G. H., & Rieke, M. J. 1988, ApJL, 331, L77, doi: [`10.1086/185239`](http://doi.org/10.1086/185239)

(ref: Endsley+21) Endsley, R., Stark, D. P., Chevallard, J., & Charlot, S. 2021, MNRAS, 500, 5229, doi: [`10.1093/mnras/staa3370`](http://doi.org/10.1093/mnras/staa3370)

(ref: Evans+20) Evans, I. N., Primini, F. A., Miller, J. B., et al. 2020, in American Astronomical Society Meeting Abstracts, Vol. 235, American Astronomical Society Meeting Abstracts #235, 154.05

(ref: Falcon-Barroso+11) Falcón-Barroso, J., Sánchez-Blázquez, P., Vazdekis, A., et al. 2011, A&A, 532, A95, doi: [`10.1051/0004-6361/201116842`](http://doi.org/10.1051/0004-6361/201116842)

(ref: fitzpatrick+99) Fitzpatrick, E. L. 1999, PASP, 111, 63, doi: [`10.1086/316293`](http://doi.org/10.1086/316293)

(ref: Fruchter+02) Fruchter, A. S., & Hook, R. N. 2002, PASP, 114, 144, doi: [`10.1086/338393`](http://doi.org/10.1086/338393)

(ref: Fujimoto+23) Fujimoto, S., Wang, B., Weaver, J., et al. 2023, arXiv e-prints, arXiv:2308.11609, doi: [`10.48550/arXiv.2308.11609`](http://doi.org/10.48550/arXiv.2308.11609)

(ref: Furtak+23) Furtak, L. J., Zitrin, A., Plat, A., et al. 2023a, ApJ, 952, 142, doi: [`10.3847/1538-4357/acdc9d`](http://doi.org/10.3847/1538-4357/acdc9d)

(ref: Furtak+23b) Furtak, L. J., Labbé, I., Zitrin, A., et al. 2023b, arXiv e-prints, arXiv:2308.05735, doi: [`10.48550/arXiv.2308.05735`](http://doi.org/10.48550/arXiv.2308.05735)

(ref: Furtak+24) —. 2024, Nature, 628, 57, doi: [`10.1038/s41586-024-07184-8`](http://doi.org/10.1038/s41586-024-07184-8)

(ref: 2013ApJS..206...10G) Galametz, A., Grazian, A., Fontana, A., et al. 2013, ApJS, 206, 10, doi: [`10.1088/0067-0049/206/2/10`](http://doi.org/10.1088/0067-0049/206/2/10)

(ref: Gandolfi+25) Gandolfi, G., Rodighiero, G., Bisigello, L., et al. 2025, arXiv e-prints, arXiv:2502.02637. [`https://arxiv.org/abs/2502.02637`](https://arxiv.org/abs/2502.02637)

(ref: Gardner+23) Gardner, J. P., Mather, J. C., Abbott, R., et al. 2023, PASP, 135, 068001, doi: [`10.1088/1538-3873/acd1b5`](http://doi.org/10.1088/1538-3873/acd1b5)

(ref: Gillman+24) Gillman, S., Smail, I., Gullberg, B., et al. 2024, A&A, 691, A299, doi: [`10.1051/0004-6361/202451006`](http://doi.org/10.1051/0004-6361/202451006)

(ref: Glikman+06) Glikman, E., Helfand, D. J., & White, R. L. 2006, ApJ, 640, 579, doi: [`10.1086/500098`](http://doi.org/10.1086/500098)

(ref: gonzalez-lopez2019) González-López, J., Decarli, R., Pavesi, R., et al. 2019, ApJ, 882, 139, doi: [`10.3847/1538-4357/ab3105`](http://doi.org/10.3847/1538-4357/ab3105)

(ref: gonzalez-lopez2020) González-López, J., Novak, M., Decarli, R., et al. 2020, ApJ, 897, 91, doi: [`10.3847/1538-4357/ab765b`](http://doi.org/10.3847/1538-4357/ab765b)

(ref: Graham+96) Graham, J. R., & Dey, A. 1996, ApJ, 471, 720, doi: [`10.1086/178000`](http://doi.org/10.1086/178000)

(ref: Greene+24) Greene, J. E., Labbe, I., Goulding, A. D., et al. 2024, ApJ, 964, 39, doi: [`10.3847/1538-4357/ad1e5f`](http://doi.org/10.3847/1538-4357/ad1e5f)

(ref: Hainline+25) Hainline, K. N., Maiolino, R., Juodžbalis, I., et al. 2025, ApJ, 979, 138, doi: [`10.3847/1538-4357/ad9920`](http://doi.org/10.3847/1538-4357/ad9920)

(ref: Harris+20) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Hickox+18) Hickox, R. C., & Alexander, D. M. 2018, ARA&A, 56, 625, doi: [`10.1146/annurev-astro-081817-051803`](http://doi.org/10.1146/annurev-astro-081817-051803)

(ref: Iani+22) Iani, E., Caputi, K. I., Rinaldi, P., & Kokorev, V. I. 2022, ApJL, 940, L24, doi: [`10.3847/2041-8213/aca014`](http://doi.org/10.3847/2041-8213/aca014)

(ref: Iani+24) Iani, E., Caputi, K. I., Rinaldi, P., et al. 2024, ApJ, 963, 97, doi: [`10.3847/1538-4357/ad15f6`](http://doi.org/10.3847/1538-4357/ad15f6)

(ref: Ilbert+06) Ilbert, O., Arnouts, S., McCracken, H. J., et al. 2006, A&A, 457, 841, doi: [`10.1051/0004-6361:20065138`](http://doi.org/10.1051/0004-6361:20065138)

(ref: Inayoshi+24) Inayoshi, K., & Ichikawa, K. 2024, ApJL, 973, L49, doi: [`10.3847/2041-8213/ad74e2`](http://doi.org/10.3847/2041-8213/ad74e2)

(ref: indebetouw+05) Indebetouw, R., Mathis, J. S., Babler, B. L., et al. 2005, ApJ, 619, 931, doi: [`10.1086/426679`](http://doi.org/10.1086/426679)

(ref: Jiang+10) Jiang, L., Fan, X., Brandt, W. N., et al. 2010, Nature, 464, 380, doi: [`10.1038/nature08877`](http://doi.org/10.1038/nature08877)

(ref: Johnson+21) Johnson, B. D., Leja, J., Conroy, C., & Speagle, J. S. 2021, ApJS, 254, 22, doi: [`10.3847/1538-4365/abef67`](http://doi.org/10.3847/1538-4365/abef67)

(ref: Kaspi+00) Kaspi, S., Smith, P. S., Netzer, H., et al. 2000, ApJ, 533, 631, doi: [`10.1086/308704`](http://doi.org/10.1086/308704)

(ref: Kennicutt+12) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: Killi+23) Killi, M., Watson, D., Brammer, G., et al. 2023, arXiv e-prints, arXiv:2312.03065, doi: [`10.48550/arXiv.2312.03065`](http://doi.org/10.48550/arXiv.2312.03065)

(ref: Kirckpatrick+23) Kirkpatrick, A., Yang, G., Le Bail, A., et al. 2023, ApJL, 959, L7, doi: [`10.3847/2041-8213/ad0b14`](http://doi.org/10.3847/2041-8213/ad0b14)

(ref: Kokorev+23) Kokorev, V., Fujimoto, S., Labbe, I., et al. 2023, ApJL, 957, L7, doi: [`10.3847/2041-8213/ad037a`](http://doi.org/10.3847/2041-8213/ad037a)

(ref: Kokorev+24) Kokorev, V., Caputi, K. I., Greene, J. E., et al. 2024, arXiv e-prints, arXiv:2401.09981, doi: [`10.48550/arXiv.2401.09981`](http://doi.org/10.48550/arXiv.2401.09981)

(ref: Kriek+13) Kriek, M., & Conroy, C. 2013, ApJL, 775, L16, doi: [`10.1088/2041-8205/775/1/L16`](http://doi.org/10.1088/2041-8205/775/1/L16)

(ref: Kron+80) Kron, R. G. 1980, ApJS, 43, 305, doi: [`10.1086/190669`](http://doi.org/10.1086/190669)

(ref: Kroupa+01) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: Labbe+23b) Labbe, I., Greene, J. E., Bezanson, R., et al. 2023, arXiv e-prints, arXiv:2306.07320, doi: [`10.48550/arXiv.2306.07320`](http://doi.org/10.48550/arXiv.2306.07320)

(ref: Langeroodi2023c) Langeroodi, D., & Hjorth, J. 2023a, ApJL, 957, L27, doi: [`10.3847/2041-8213/acfeec`](http://doi.org/10.3847/2041-8213/acfeec)

(ref: Langeroodi+23b) —. 2023b, arXiv e-prints, arXiv:2307.06336, doi: [`10.48550/arXiv.2307.06336`](http://doi.org/10.48550/arXiv.2307.06336)

(ref: Langeroodi+23) Langeroodi, D., Hjorth, J., Chen, W., et al. 2023, ApJ, 957, 39, doi: [`10.3847/1538-4357/acdbc1`](http://doi.org/10.3847/1538-4357/acdbc1)

(ref: Leja+19) Leja, J., Carnall, A. C., Johnson, B. D., Conroy, C., & Speagle, J. S. 2019, ApJ, 876, 3, doi: [`10.3847/1538-4357/ab133c`](http://doi.org/10.3847/1538-4357/ab133c)

(ref: Li+24) Li, Y., Leja, J., Johnson, B. D., Tacchella, S., & Naidu, R. P. 2024, arXiv e-prints, arXiv:2404.02333, doi: [`10.48550/arXiv.2404.02333`](http://doi.org/10.48550/arXiv.2404.02333)

(ref: Luo+17) Luo, B., Brandt, W. N., Xue, Y. Q., et al. 2017, ApJS, 228, 2, doi: [`10.3847/1538-4365/228/1/2`](http://doi.org/10.3847/1538-4365/228/1/2)

(ref: Lusso+10) Lusso, E., Comastri, A., Vignali, C., et al. 2010, A&A, 512, A34, doi: [`10.1051/0004-6361/200913298`](http://doi.org/10.1051/0004-6361/200913298)

(ref: Lyu+22) Lyu, J., Alberts, S., Rieke, G. H., & Rujopakarn, W. 2022, ApJ, 941, 191, doi: [`10.3847/1538-4357/ac9e5d`](http://doi.org/10.3847/1538-4357/ac9e5d)

(ref: Lyu+17) Lyu, J., Rieke, G. H., & Shi, Y. 2017, The Astrophysical Journal, 835, 257, doi: [`10.3847/1538-4357/835/2/257`](http://doi.org/10.3847/1538-4357/835/2/257)

(ref: Lyu+23) Lyu, J., Alberts, S., Rieke, G. H., et al. 2023, arXiv e-prints, arXiv:2310.12330, doi: [`10.48550/arXiv.2310.12330`](http://doi.org/10.48550/arXiv.2310.12330)

(ref: Lyu+24) —. 2024, ApJ, 966, 229, doi: [`10.3847/1538-4357/ad3643`](http://doi.org/10.3847/1538-4357/ad3643)

(ref: Maiolino+23) Maiolino, R., Uebler, H., Perna, M., et al. 2023, arXiv e-prints, arXiv:2306.00953, doi: [`10.48550/arXiv.2306.00953`](http://doi.org/10.48550/arXiv.2306.00953)

(ref: Marmol-Queralto+16) Mármol-Queraltó, E., McLure, R. J., Cullen, F., et al. 2016, MNRAS, 460, 3587, doi: [`10.1093/mnras/stw1212`](http://doi.org/10.1093/mnras/stw1212)

(ref: Matthee+23) Matthee, J., Mackenzie, R., Simcoe, R. A., et al. 2023, ApJ, 950, 67, doi: [`10.3847/1538-4357/acc846`](http://doi.org/10.3847/1538-4357/acc846)

(ref: Matthee+17) Matthee, J., Sobral, D., Darvish, B., et al. 2017, MNRAS, 472, 772, doi: [`10.1093/mnras/stx2061`](http://doi.org/10.1093/mnras/stx2061)

(ref: Matthee+22) Matthee, J., Feltre, A., Maseda, M., et al. 2022, A&A, 660, A10, doi: [`10.1051/0004-6361/202142187`](http://doi.org/10.1051/0004-6361/202142187)

(ref: Matthee+24) Matthee, J., Naidu, R. P., Brammer, G., et al. 2024, ApJ, 963, 129, doi: [`10.3847/1538-4357/ad2345`](http://doi.org/10.3847/1538-4357/ad2345)

(ref: Meurer+99) Meurer, G. R., Heckman, T. M., & Calzetti, D. 1999, ApJ, 521, 64, doi: [`10.1086/307523`](http://doi.org/10.1086/307523)

(ref: Moffat+69) Moffat, A. F. J. 1969, A&A, 3, 455

(ref: Noll+09) Noll, S., Burgarella, D., Giovannoli, E., et al. 2009, A&A, 507, 1793, doi: [`10.1051/0004-6361/200912497`](http://doi.org/10.1051/0004-6361/200912497)

(ref: 2023MNRAS.525.2864O) Oesch, P. A., Brammer, G., Naidu, R. P., et al. 2023a, MNRAS, 525, 2864, doi: [`10.1093/mnras/stad2411`](http://doi.org/10.1093/mnras/stad2411)

(ref: Oesch+23) —. 2023b, arXiv e-prints, arXiv:2304.02026, doi: [`10.48550/arXiv.2304.02026`](http://doi.org/10.48550/arXiv.2304.02026)

(ref: Oke+83) Oke, J. B., & Gunn, J. E. 1983, ApJ, 266, 713, doi: [`10.1086/160817`](http://doi.org/10.1086/160817)

(ref: Osterbrock+06) Osterbrock, D. E., & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and active galactic nuclei

(ref: Ostlin+25) Östlin, G., Pérez-González, P. G., Melinder, J., et al. 2024, arXiv e-prints, arXiv:2411.19686, doi: [`10.48550/arXiv.2411.19686`](http://doi.org/10.48550/arXiv.2411.19686)

(ref: Ouchi+20) Ouchi, M., Ono, Y., & Shibuya, T. 2020, ARA&A, 58, 617, doi: [`10.1146/annurev-astro-032620-021859`](http://doi.org/10.1146/annurev-astro-032620-021859)

(ref: reback2020pandas) pandas development team, T. 2020, pandas-dev/pandas: Pandas, latest, Zenodo, doi: [`10.5281/zenodo.3509134`](http://doi.org/10.5281/zenodo.3509134)

(ref: Papovich+23) Papovich, C., Cole, J. W., Yang, G., et al. 2023, ApJL, 949, L18, doi: [`10.3847/2041-8213/acc948`](http://doi.org/10.3847/2041-8213/acc948)

(ref: Perez-Gonzalez+03) Pérez-González, P. G., Gil de Paz, A., Zamorano, J., et al. 2003, MNRAS, 338, 508, doi: [`10.1046/j.1365-8711.2003.06077.x`](http://doi.org/10.1046/j.1365-8711.2003.06077.x)

(ref: Perez-Gonzalez+08) Pérez-González, P. G., Rieke, G. H., Villar, V., et al. 2008, ApJ, 675, 234, doi: [`10.1086/523690`](http://doi.org/10.1086/523690)

(ref: Perez-Gonzalez+24a) Pérez-González, P. G., Barro, G., Rieke, G. H., et al. 2024a, arXiv e-prints, arXiv:2401.08782, doi: [`10.48550/arXiv.2401.08782`](http://doi.org/10.48550/arXiv.2401.08782)

(ref: Perez-Gonzalez+24b) Pérez-González, P. G., Rinaldi, P., Caputi, K. I., et al. 2024b, arXiv e-prints, arXiv:2402.16942, doi: [`10.48550/arXiv.2402.16942`](http://doi.org/10.48550/arXiv.2402.16942)

(ref: Perrin+14) Perrin, M. D., Sivaramakrishnan, A., Lajoie, C.-P., et al. 2014, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9143, Space Telescopes and Instrumentation 2014: Optical, Infrared, and Millimeter Wave, ed. J. Oschmann, Jacobus M., M. Clampin, G. G. Fazio, & H. A. MacEwen, 91433X, doi: [`10.1117/12.2056689`](http://doi.org/10.1117/12.2056689)

(ref: Prieto-Lyon+23) Prieto-Lyon, G., Strait, V., Mason, C. A., et al. 2023, A&A, 672, A186, doi: [`10.1051/0004-6361/202245532`](http://doi.org/10.1051/0004-6361/202245532)

(ref: Ranalli+13) Ranalli, P., Comastri, A., Vignali, C., et al. 2013, A&A, 555, A42, doi: [`10.1051/0004-6361/201321211`](http://doi.org/10.1051/0004-6361/201321211)

(ref: Rieke+24) Rieke, G. H., Alberts, S., Shivaei, I., et al. 2024, ApJ, 975, 83, doi: [`10.3847/1538-4357/ad6cd2`](http://doi.org/10.3847/1538-4357/ad6cd2)

(ref: Rieke+15) Rieke, G. H., Wright, G. S., Böker, T., et al. 2015, PASP, 127, 584, doi: [`10.1086/682252`](http://doi.org/10.1086/682252)

(ref: Rieke+23) Rieke, M., & the JADES Collaboration. 2023, arXiv e-prints, arXiv:2306.02466, doi: [`10.48550/arXiv.2306.02466`](http://doi.org/10.48550/arXiv.2306.02466)

(ref: 2023ApJS..269...16R) Rieke, M. J., Robertson, B., Tacchella, S., et al. 2023, ApJS, 269, 16, doi: [`10.3847/1538-4365/acf44d`](http://doi.org/10.3847/1538-4365/acf44d)

(ref: Rigby+23) Rigby, J., Perrin, M., McElwain, M., et al. 2023, PASP, 135, 048001, doi: [`10.1088/1538-3873/acb293`](http://doi.org/10.1088/1538-3873/acb293)

(ref: Rinaldi+23a) Rinaldi, P., Caputi, K. I., Costantin, L., et al. 2023, ApJ, 952, 143, doi: [`10.3847/1538-4357/acdc27`](http://doi.org/10.3847/1538-4357/acdc27)

(ref: Rinaldi+25) Rinaldi, P., Bonaventura, N., Rieke, G. H., et al. 2024, arXiv e-prints, arXiv:2411.14383, doi: [`10.48550/arXiv.2411.14383`](http://doi.org/10.48550/arXiv.2411.14383)

(ref: Robertson+23) Robertson, B. E., Tacchella, S., Johnson, B. D., et al. 2023, Nature Astronomy, 7, 611, doi: [`10.1038/s41550-023-01921-1`](http://doi.org/10.1038/s41550-023-01921-1)

(ref: Rodighiero+23) Rodighiero, G., Bisigello, L., Iani, E., et al. 2023, MNRAS, 518, L19, doi: [`10.1093/mnrasl/slac115`](http://doi.org/10.1093/mnrasl/slac115)

(ref: Schlafly+11) Schlafly, E. F., & Finkbeiner, D. P. 2011, ApJ, 737, 103, doi: [`10.1088/0004-637X/737/2/103`](http://doi.org/10.1088/0004-637X/737/2/103)

(ref: Scholtz+23) Scholtz, J., Maiolino, R., D’Eugenio, F., et al. 2023, arXiv e-prints, arXiv:2311.18731, doi: [`10.48550/arXiv.2311.18731`](http://doi.org/10.48550/arXiv.2311.18731)

(ref: Schreiber+18) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30, doi: [`10.1051/0004-6361/201731506`](http://doi.org/10.1051/0004-6361/201731506)

(ref: Sersic+63) Sérsic, J. L. 1963, Boletin de la Asociacion Argentina de Astronomia La Plata Argentina, 6, 41

(ref: Siebenmorgen+15) Siebenmorgen, R., Heymann, F., & Efstathiou, A. 2015, A&A, 583, A120, doi: [`10.1051/0004-6361/201526034`](http://doi.org/10.1051/0004-6361/201526034)

(ref: Siebenmorgen+07) Siebenmorgen, R., & Krügel, E. 2007, A&A, 461, 445, doi: [`10.1051/0004-6361:20065700`](http://doi.org/10.1051/0004-6361:20065700)

(ref: Sommovigo+20) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2020, MNRAS, 497, 956, doi: [`10.1093/mnras/staa1959`](http://doi.org/10.1093/mnras/staa1959)

(ref: Sommovigo+22) —. 2022, MNRAS, 513, 3122, doi: [`10.1093/mnras/stac302`](http://doi.org/10.1093/mnras/stac302)

(ref: Son+23) Son, S., Kim, M., & Ho, L. C. 2023, The Astrophysical Journal, 953, 175, doi: [`10.3847/1538-4357/ace165`](http://doi.org/10.3847/1538-4357/ace165)

(ref: Sonnett+13) Sonnett, S., Meech, K., Jedicke, R., et al. 2013, PASP, 125, 456, doi: [`10.1086/670593`](http://doi.org/10.1086/670593)

(ref: Stalevski+12) Stalevski, M., Fritz, J., Baes, M., Nakos, T., & Popović, L. Č. 2012, MNRAS, 420, 2756, doi: [`10.1111/j.1365-2966.2011.19775.x`](http://doi.org/10.1111/j.1365-2966.2011.19775.x)

(ref: Stalevski+16) Stalevski, M., Ricci, C., Ueda, Y., et al. 2016, MNRAS, 458, 2288, doi: [`10.1093/mnras/stw444`](http://doi.org/10.1093/mnras/stw444)

(ref: Stone+23) Stone, C. J., Courteau, S., Cuillandre, J.-C., et al. 2023, MNRAS, doi: [`10.1093/mnras/stad2477`](http://doi.org/10.1093/mnras/stad2477)

(ref: Sun+24) Sun, W., Ho, L. C., Zhuang, M.-Y., et al. 2024, ApJ, 960, 104, doi: [`10.3847/1538-4357/acf1f6`](http://doi.org/10.3847/1538-4357/acf1f6)

(ref: Tacchella+24) Tacchella, S., McClymont, W., Scholtz, J., et al. 2024, arXiv e-prints, arXiv:2404.02194, doi: [`10.48550/arXiv.2404.02194`](http://doi.org/10.48550/arXiv.2404.02194)

(ref: Tananbaum+79) Tananbaum, H., Avni, Y., Branduardi, G., et al. 1979, ApJL, 234, L9, doi: [`10.1086/183100`](http://doi.org/10.1086/183100)

(ref: Taylor+11) Taylor, M. 2011, TOPCAT: Tool for OPerations on Catalogues And Tables, Astrophysics Source Code Library, record ascl:1101.010. [`http://ascl.net/1101.010`](http://ascl.net/1101.010)

(ref: Temple+21) Temple, M. J., Banerji, M., Hewett, P. C., Rankine, A. L., & Richards, G. T. 2021, MNRAS, 501, 3061, doi: [`10.1093/mnras/staa3842`](http://doi.org/10.1093/mnras/staa3842)

(ref: Ubler+23) Übler, H., Maiolino, R., Curtis-Lake, E., et al. 2023, A&A, 677, A145, doi: [`10.1051/0004-6361/202346137`](http://doi.org/10.1051/0004-6361/202346137)

(ref: vanMierlo+23) van Mierlo, S. E., Caputi, K. I., Ashby, M. L. N., et al. 2023, arXiv e-prints, arXiv:2311.17764, doi: [`10.48550/arXiv.2311.17764`](http://doi.org/10.48550/arXiv.2311.17764)

(ref: Vanden-Berk+01) Vanden Berk, D. E., Richards, G. T., Bauer, A., et al. 2001, AJ, 122, 549, doi: [`10.1086/321167`](http://doi.org/10.1086/321167)

(ref: Virtanen+20) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Wang+23) Wang, B., Fujimoto, S., Labbé, I., et al. 2023, ApJL, 957, L34, doi: [`10.3847/2041-8213/acfe07`](http://doi.org/10.3847/2041-8213/acfe07)

(ref: Wang+24) Wang, B., de Graaff, A., Davies, R. L., et al. 2024, arXiv e-prints, arXiv:2403.02304, doi: [`10.48550/arXiv.2403.02304`](http://doi.org/10.48550/arXiv.2403.02304)

(ref: Weaver+23a) Weaver, J. R., Zalesky, L., Kokorev, V., et al. 2023, ApJS, 269, 20, doi: [`10.3847/1538-4365/acf850`](http://doi.org/10.3847/1538-4365/acf850)

(ref: McKinney+10) Wes McKinney. 2010, in Proceedings of the 9th Python in Science Conference, ed. Stéfan van der Walt & Jarrod Millman, 56 – 61, doi: [`10.25080/Majora-92bf1922-00a`](http://doi.org/10.25080/Majora-92bf1922-00a)

(ref: Whitaker+11) Whitaker, K. E., Labbé, I., van Dokkum, P. G., et al. 2011, ApJ, 735, 86, doi: [`10.1088/0004-637X/735/2/86`](http://doi.org/10.1088/0004-637X/735/2/86)

(ref: Whitaker+19) Whitaker, K. E., Ashas, M., Illingworth, G., et al. 2019, ApJS, 244, 16, doi: [`10.3847/1538-4365/ab3853`](http://doi.org/10.3847/1538-4365/ab3853)

(ref: 2023ApJS..268...64W) Williams, C. C., Tacchella, S., Maseda, M. V., et al. 2023, ApJS, 268, 64, doi: [`10.3847/1538-4365/acf130`](http://doi.org/10.3847/1538-4365/acf130)

(ref: Williams+24) Williams, C. C., Alberts, S., Ji, Z., et al. 2024, ApJ, 968, 34, doi: [`10.3847/1538-4357/ad3f17`](http://doi.org/10.3847/1538-4357/ad3f17)

(ref: Wright+15) Wright, G. S., Wright, D., Goodson, G. B., et al. 2015, PASP, 127, 595, doi: [`10.1086/682253`](http://doi.org/10.1086/682253)

(ref: Wright+23) Wright, G. S., Rieke, G. H., Glasse, A., et al. 2023, PASP, 135, 048003, doi: [`10.1088/1538-3873/acbe66`](http://doi.org/10.1088/1538-3873/acbe66)

(ref: Yang+23) Yang, G., Caputi, K. I., Papovich, C., et al. 2023, ApJL, 950, L5, doi: [`10.3847/2041-8213/acd639`](http://doi.org/10.3847/2041-8213/acd639)

(ref: Yue+24) Yue, M., Eilers, A.-C., Ananna, T. T., et al. 2024, ApJL, 974, L26, doi: [`10.3847/2041-8213/ad7eba`](http://doi.org/10.3847/2041-8213/ad7eba)

[^1]: <https://mast.stsci.edu/portal/Mashup/Clients/Mast/Portal.html>

[^2]: The HST and JWST observations can be found at the following DOIs: [10.17909/t91019](https://doi.org/10.17909/t91019), [10.17909/fsc4-dt61](https://doi.org/10.17909/fsc4-dt61), [10.17909/gdyc-7g80](https://doi.org/10.17909/gdyc-7g80), [10.17909/8tdj-8n28](https://doi.org/10.17909/8tdj-8n28), [10.17909/et3f-zd57](https://doi.org/10.17909/et3f-zd57), [10.17909/5txh-pj89](https://doi.org/10.17909/5txh-pj89), [10.17909/bjk7-qh92](https://doi.org/10.17909/bjk7-qh92).

[^3]: The HLF-GOODS-S imaging is available at [https://archive.stsci.edu/ prepds/hlf/](https://archive.stsci.edu/ prepds/hlf/);

[^4]: The MUSE cubes can be obtained at [https://amused.univ- lyon1.fr/project/UDF/HUDF/](https://amused.univ- lyon1.fr/project/UDF/HUDF/);

[^5]: The ASPECS images are available at <https://almascience.org/alma-data/lp/ASPECS>;

[^6]: An LAE with `quality_flag = 2` has a Ly$\alpha$ S/N $> 5$ and a width and asymmetry compatible with typical Ly$\alpha$ line shapes (cite: Bacon+23);

[^7]: The FRESCO line sensitivity (estimated for compact sources and integrated over the full extent of the line) is $\approx 2 \times 10^{-18}~\rm erg~s^{-1} cm^{-2}$ at 5$\sigma$ (cite: Oesch+23);

[^8]: The NGDEEP spectroscopy was carried out in the F115W, F150W and F200W filters reaching 5$\sigma$ integrated emission line limits of 1.2, 1.3 and 1.5$\times 10^{-18}\rm ~erg~s^{-1}~cm^2$, respectively (cite: Bagley+24);

[^9]: The encircled energy curves are available at <https://www.stsci.edu/hst/instrumentation/>;

[^10]: [https://irsa.ipac.caltech.edu/applications/ DUST/](https://irsa.ipac.caltech.edu/applications/ DUST/);

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[9].key_parameters[0].evidence[1]",
  "value": "Graybody fit with beta = 1.5; continuum under Hbeta+[OIII] taken as mean of F335M and F410M",
  "failed_quote": "If we assume the continuum below H$\\beta$ + [O III]$\\lambda\\lambda4959,5007$"
 }
]
```
