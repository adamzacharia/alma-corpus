# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2014ApJ...796...96B\gemini38f\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# ALMA Observations of the Host Galaxy of GRB 090423 at $z=8.23$: Deep Limits on Obscured Star Formation 630 Million Years After the Big Bang

## Abstract

We present rest-frame far-infrared (FIR) and optical observations of the host galaxy of GRB 090423 at $z=8.23$ from the Atacama Large Millimeter Array (ALMA) and the *Spitzer Space Telescope*, respectively. The host remains undetected to $3\sigma$ limits of $F_\nu(222\,{\rm GHz})\lesssim 33$ $\mu$Jy and $F_\nu(3.6\,{\rm \mu m})\lesssim 81$ nJy. The FIR limit is about 20 times fainter than the luminosity of the local ULIRG Arp 220, and comparable to the local starburst M 82. Comparing to model spectral energy distributions we place a limit on the IR luminosity of $L_{\rm IR}(8-1000{\rm \,\mu m})\lesssim 3\times 10^{10}$ L$_\odot$, corresponding to a limit on the obscured star formation rate of ${\rm SFR_{\rm IR}} \lesssim 5$ M$_\odot$ yr$^{-1}$; for comparison, the limit on the unobscured star formation rate from *Hubble Space Telescope* rest-frame UV observations is ${\rm
    SFR_{UV}}\lesssim 1$ M$_\odot$ yr$^{-1}$. We also place a limit on the host galaxy stellar mass of $M_*\lesssim 5\times 10^7$ M$_\odot$ (for a stellar population age of 100 Myr and constant star formation rate). Finally, we compare our millimeter observations to those of field galaxies at $z\gtrsim 4$ (Lyman break galaxies, Ly$\alpha$ emitters, and submillimeter galaxies), and find that our limit on the FIR luminosity is the most constraining to date, although the field galaxies have much larger rest-frame UV/optical luminosities than the host of GRB 090423 by virtue of their selection techniques. We conclude that GRB host galaxies at $z\gtrsim 4$, especially those with measured interstellar medium metallicities from afterglow spectroscopy, are an attractive sample for future ALMA studies of high redshift obscured star formation.

Harvard-Smithsonian Center for Astrophysics, 60 Garden Street, Cambridge, MA 02138, USA

Spitzer Science Center, California Institute of Technology, MC 220-6, 1200 East California Boulevard, Pasadena, CA 91125, USA

Department of Physics and Astronomy, University of Leicester, University Road, Leicester LE1 7RH, UK

Department of Physics, University of Warwick, Gibbet Hill Road, Coventry CV4 7AL, UK

CASA, University of Colorado UCB 389, Boulder, CO 80309, USA

# Introduction

Thanks to their extreme brightness, gamma-ray bursts (GRBs) can be utilized as powerful probes of star and galaxy formation at high redshift, including during the epoch of reionization (e.g., (cite: tkk+06; tfl+09; tlf+12; cbf+13; cbf+14)). In particular, spectroscopy of the optical/near-IR afterglow emission can provide an unambiguous and precise spectroscopic redshift, as well as a measurement of the host galaxy interstellar medium (ISM) properties *independent of the host galaxy brightness* (e.g., (cite: tkk+06; cbf+13)). This unique insight can then be combined with multi-wavelength photometric follow-up of the host galaxies to study properties such as their stellar mass and star formation activity (e.g., (cite: lbc11; tlf+12)).

In contrast, direct galaxy studies at these redshifts rely either on photometric redshifts (the Ly$\alpha$ break technique; LBGs), and are therefore limited to bright objects usually with no subsequent spectroscopic confirmation (e.g., (cite: sbm03; bse+04; mrp+05; bib+06; oms+09; bio+11; mdd+11; vpf+11; oom+12; fpd+13)), or on narrow-band Ly$\alpha$ imaging (Ly$\alpha$ emitters; LAEs), which also requires subsequent spectroscopic confirmation (e.g., (cite: ktk+03; iok+06; hcb+10; osf+10; sko+12)). In the case of LAEs, the reliance on Ly$\alpha$ emission may also inhibit detections during the epoch of reionization due to significant scattering and absorption of Ly$\alpha$ photons by the neutral intergalactic medium; the same effect also inhibits the success of LBG spectroscopic confirmation, which also relies on detection of the Ly$\alpha$ line. Similarly, the reliance on rest-frame UV and Ly$\alpha$ emission bias both the LBG and LAE selection against dusty environments. Moreover, for both LBGs and LAEs, measurements of the ISM properties are beyond the reach of current instrumentation since the relevant rest-frame optical emission lines are redshifted into the mid-IR. An alternative technique of submillimeter color selection has also led to the identification of a few high redshift submillimeter-bright galaxies (SMGs), with spectroscopic confirmation via CO and \[C II\] emission lines (e.g., (cite: wdc+12; rbc+13)). However, these extremely luminous and highly star forming galaxies are exceedingly rare and do not shed light on the bulk of the galaxy population. Thus, spectroscopically-confirmed GRB host galaxies at high redshift provide an attractive sample for multi-wavelength follow-up observations.

In this context, the advent of the Atacama Large Millimeter Array (ALMA) makes it possible for the first time to probe obscured star formation in high-redshift galaxies to a sensitivity level of only a few M$_\odot$ yr$^{-1}$, or an integrated IR luminosity of $L_{\rm
  IR}\sim 10^{10}$ L$_\odot$. Previously, only rare SMGs with $L_{\rm
  IR}\gtrsim 10^{12}$ L$_\odot$ (ultra-luminous infrared galaxies; ULIRGs) and correspondingly high star formation rates of $\sim 10^3$ M$_\odot$ yr$^{-1}$ were accessible (e.g., (cite: ckn+11; crr+12; wdc+12; rbc+13)). In the long term, ALMA observations of GRB host galaxies with measured ISM metallicities will shed light on the relations between metallicity, dust content, and obscured star formation at redshifts that are inaccessible with other techniques (i.e., $z\gtrsim 4$). This will also provide a comparison with the rest-frame FIR properties of LBGs and LAEs, although none have been individually detected to date at $z\gtrsim 4$ (e.g., (cite: oeo+13; owo+14)).

Here, we present deep ALMA observations of the host galaxy of the most distant spectroscopically-confirmed burst to date – GRB 090423 at $z=8.23$ (cite: sdc+09; tfl+09). The observations are aimed at reaching a rest-frame FIR luminosity level below that of a luminous infrared galaxy (LIRG: $L_{IR}=10^{11}$ L$_\odot$). We also present *Spitzer Space Telescope* rest-frame optical observations to constrain the stellar mass of the host galaxy. The ALMA and *Spitzer* observations and data analysis are described in §[2](#sec:obs). In §[3](#sec:prop) we use the data to constrain the host galaxy properties, while in §[4](#sec:comp) we compare these results to millimeter studies of LAEs, LBGs, and SMGs at $z\gtrsim 4$.

# Observations

The discovery and redshift determination of GRB 090423 are presented in (cite: tfl+09), who find $z=8.23^{+0.06}_{-0.07}$. The position of the afterglow is R.A. = 09$^{\rm h}$55$^{\rm m}$33.29$^{\rm s}$, Decl. = $+18^\circ 08'57.8''$ (J2000) with an uncertainty of about $0''.1$ in each coordinate. The host galaxy was previously observed with the *Hubble Space Telescope* Wide-field Camera 3 ( *HST*/WFC3) in the F110W and F160W filters, leading to non-detections (cite: tlf+12). It was also observed with the Australia Telescope Compact Array (ATCA), yielding non-detections of rest-frame 850 $\mu$m continuum emission and CO (3-2) emission (cite: sbt+11). The continuum limits are summarized in Table [1](#tab:data).

## Atacama Large Millimeter Array

ALMA band 6 (222 GHz) observations were carried out with $25-28$ 12-m diameter antennas in five observing blocks spread over 12 days on 2013 November 18, 21, and 30 UT (Cycle 1). The 2 GHz wide spectral windows were set to central frequencies of 213, 215, 229 and 231 GHz. The total on-source integration time was 163 min after data flagging. We performed data calibration and imaging using the Common Astronomy Software Application (CASA). The gain calibration utilized J 0854+2006, while bandpass calibration utilized one of J 0522$-$3627, J 0538$-$4405, J 1037$-$2934, or J 1058+0133 in each observing block. Absolute flux calibration was performed using observations of the solar system objects Ceres, Ganymede, or Pallas. We found some minor variations in the resulting fluxes of J 0854+2006 between the observing blocks, likely due to the use of asteroids, which have uncertain flux models. We therefore used Ganymede when possible and Ceres to determine and manually set the flux for J 0854+2006 in each epoch. The overall uncertainty in the absolute flux calibration is about $10\%$.

The resulting combined continuum map (natural weighting without primary beam correction) has an rms noise of $11$ $\mu$Jy beam$^{-1}$ for a synthesized beam size (full-width at half maximum) of $1''.0\times 0''.80$ (Figure [1](#fig:image)). No source is detected at the location of GRB 090423 (with a flux density at the source location of $-4\pm 11$ $\mu$Jy), leading an upper limit of $F_\nu(222\,{\rm
  GHz})\lesssim 33$ $\mu$Jy ($3\sigma$; Table [1](#tab:data)).

## *Spitzer Space Telescope*

*Spitzer* observations were obtained during the warm mission (DDT Program 538) with the Infrared Array Camera (IRAC) at $3.6$ $\mu$m on 2010 January 26 and 27 UT. Each observation consisted of 650 100-s frames ($93.6$ s on source), for a combined on-source time of $33.8$ hr. We analyzed the data using the Great Observatories Origins Deep Survey (GOODS) pipeline, including corrections for bright star image artifacts (muxbleed and pulldown) with dark and sky background subtraction. We carried out astrometric alignment utilizing stars in common with the Sloan Digital Survey Survey database, and created a combined mosaic of the individual frames on a $0.4''\times 0.4''$ pixel grid. We also produced a pair of split images, each with half of the frames, and used the difference in these split images to produce a noise map. The resulting uncertainty is about 2 times higher than that derived from pure pixel statistics in the vicinity of the source.

We do not detect significant emission at the location of GRB 090423 (Figure [1](#fig:image)). There is no evidence for significant source confusion at this location, in agreement with the *HST*/WFC3 images of the field (cite: tlf+12). From the noise maps, we find that the $1\sigma$ point source sensitivity at the location of GRB 090423 is 27 nJy. Photometry in a $1.2"$ radius aperture yields a $3.6$ $\mu$m flux density of $26\pm 27$ nJy, after aperture corrections. We therefore place an upper limit on the brightness of the host of $F_\nu(3.6\,{\rm \mu m}\lesssim 81$nJy ($3\sigma$; Table [1](#tab:data)).

# Host Galaxy Properties: IR Luminosity, Obscured Star Formation Rate, and Stellar Mass

The host galaxy of GRB 090423 remains undetected in our ALMA and *Spitzer* observations. The flux density limits are plotted in the left panel of Figure [2](#fig:seds). Converted to rest-frame spectral luminosity, the non-detections correspond to $L_\nu(145\,{\rm \mu
  m})\lesssim 3.1\times 10^{31}$ erg s$^{-1}$ Hz$^{-1}$ and $L_\nu(0.39\,{\rm \mu m})\lesssim 7.6\times 10^{28}$ erg s$^{-1}$ Hz$^{-1}$, respectively (right panel of Figure [2](#fig:seds), and Table [1](#tab:data)).

Also shown in Figure [2](#fig:seds) are the spectral energy distributions (SEDs) of several local galaxies redshifted to $z=8.23$: the ULIRG Arp 220, the starburst M 82, the low metallicity dwarf galaxy I Zw 18, and the host galaxy of GRB 980425 ($d=40$ Mpc; (cite: mhp+14)). Our ALMA non-detection corresponds to a luminosity that is about 20 times fainter than that of Arp 220 and about 1.6 times higher than that of M 82. We also provide a comparison with the galaxy templates of (cite: raw+09), which are based on eleven local star forming LIRGs and ULIRGs, and find that the ALMA non-detection corresponds to $L_{\rm IR}\lesssim 3\times 10^{10}$ L$_\odot$.

For the Arp 220 template, the ALMA non-detection provides a much more stringent limit than the HST and *Spitzer* limits, which only rule out a luminosity comparable to that of Arp 220. The ALMA constraints are also more stringent for the M 82 template, although only by about a factor of 2. For an Sd galaxy template from the Spitzer Wide-area InfraRed Extragalactic survey (SWIRE) library, the ALMA, *HST*, and *Spitzer* data all place comparable limits on the host SED. On the other hand, for the I Zw 18 template, which has weak FIR emission, the *HST* limits place a much more stringent constraint than the ALMA data, by about a factor of 600. The same is true for the GRB 980425 host galaxy template, which is about 15 times fainter than the ALMA limit when scaled to the *HST* limits.

Using the standard modified blackbody SED of dust emission, with a dust temperature range of $T_{\rm dust}\approx 30-50$ K and $\beta\approx 1.5-2$ (e.g., (cite: sss+14)), the ALMA non-detection corresponds to an upper limit on the integrated IR luminosity of $L_{\rm IR}(8-1000\, {\rm \mu m})\lesssim (2-5)\times 10^{10}$ L$_\odot$; the lower bound on the blackbody temperature is set by the cosmic microwave background temperature $T_{\rm CMB}(z=8.23)\approx
25$ K (cite: dgw+13). The IR luminosity upper limit is thus a few times lower than the scale for a LIRG, and agrees well with the comparison to the (cite: raw+09) templates. The limit on the integrated IR luminosity corresponds to an upper bound on the obscured star formation rate (cite: ken98; cwh+10), of ${\rm SFR}_{\rm IR}\lesssim 3-5$ M$_\odot$ yr$^{-1}$. For comparison, the limit on the *unobscured* star formation rate from the *HST* rest-frame UV non-detection is ${\rm SFR}_{\rm UV}
\lesssim 1.2$ M$_\odot$ yr$^{-1}$.

We also place an upper bound on the host galaxy stellar mass using the *HST* and *Spitzer* upper limits. Utilizing the (cite: bc03) stellar population synthesis models with a constant star formation rate, a Salpeter IMF, a metallicity of $0.2$ Z$_\odot$, and no dust extinction, we find that for a stellar population age of $10-100$ Myr (typical of GRB host galaxies; (cite: sgl09; lb10)) the limit on the host stellar mass is $M_*\lesssim (1-5)\times 10^7$ M$_\odot$. The inferred host galaxy properties are summarized in Table [2](#tab:host).

# Comparison to Millimeter Observations of Field Galaxies at $z\gtrsim 4$

To place the non-detection of the host galaxy of GRB 090423 in the context of millimeter studies of high-redshift galaxies, we summarize below previous observational efforts to detect and study distant LAEs, LBGs, and SMGs; the information is summarized in Figure [3](#fig:gals). We first note that, at present, ALMA observations of only two other galaxies with spectroscopic redshifts of $z\gtrsim 6$ have been published: the LAEs “Himiko” at $z=6.595$ (cite: oeo+13; owo+14) and IOK-1 at $z=6.96$ (cite: owo+14). Neither source was detected, with resulting $3\sigma$ flux density limits of $F_\nu(259\,{\rm GHz})
\lesssim 52$ and $F_\nu(232\,{\rm GHz})\lesssim 63$ $\mu$Jy, respectively. The flux density and integrated IR luminosity limits for these two LAEs are shallower than those achieved in our observations; see Figure [3](#fig:gals). However, it is important to note that Himiko and IOK-1 are significantly more luminous than the host of GRB 090423 in the rest-frame UV and optical, by a factor of $\gtrsim 30$ (Figure [2](#fig:seds)), with inferred unobscured star formation rates of $\approx 25-30$ M$_\odot$ yr$^{-1}$ (cite: oeo+13; owo+14). Thus, in terms of the ratio of FIR to UV luminosity, the limits for Himiko and IOK-1 are more constraining than those for the host of GRB 090423.

Beyond the ALMA observations of $z\gtrsim 6$ galaxies, there are shallower observations from other millimeter facilities. (cite: bsp+07) observed the lensed LAE HCM 6A at $z=6.56$ with the Plateau de Bure Interferometer and placed a limit of $L_{\rm
  IR}\lesssim 2.1\times 10^{11}$ L$_\odot$. (cite: grd+14) used the Combined Array for Research in Millimeter-wave Astronomy to place limits on two LAEs at $z=6.541$ and $z=6.554$ of $\lesssim 1.0\times
10^{12}$ and $2.1\times 10^{12}$ L$_\odot$, respectively. (cite: rbc+13) used a wide range of facilities to study the bright SMG HFLS 3 at $z=6.337$, discovered in the Herschel Multi-tiered Extragalactic Survey, and found $L_{\rm IR} \approx 2.9\times 10^{13}$ L$_\odot$. Thus, the only galaxy at $z\gtrsim 6$ detected in the millimeter band to date is a hyper-luminous infrared galaxy (Figure [3](#fig:gals)).

Expanding the redshift range down to $z=4$, only a few galaxies with spectroscopic redshifts have been detected with ALMA, all of which are bright SMGs (Figure [3](#fig:gals)). (cite: sks+12) detected two SMGs in ALMA observations of the LABOCA Extended Chandra Deep Field-South Survey, with \[C II\]$\lambda 157.74$ $\mu$m detections indicating redshifts of $z=4.419$ and $z=4.444$, and resulting IR luminosities of $2\times 10^{12}$ L$_\odot$. (cite: wwc+12) and (cite: crw+13) presented continuum and \[C II\] line emission from the SMG and two LAEs associated with the AGN/SMG system BRI 1202-0725 at $z=4.70$, with luminosities of $1.2\times 10^{13}$ L$_\odot$ (SMG), $\gtrsim 3.6\times 10^{11}$ L$_\odot$ (Ly$\alpha$-1), and $1.7\times
10^{12}$ L$_\odot$ (Ly$\alpha$-2). (cite: hmf+13) detected two strongly lensed SMGs at $z=4.224$ and $z=5.656$, found in South Pole Telescope data, with intrinsic IR luminosities of about $3.8\times
10^{12}$ and $3.7\times 10^{13}$ L$_\odot$, respectively. (cite: wcd+14) detected an SMG at $z=4.762$, first identified in LABOCA observations of the Extended Chandra Deep Field, with $L_{\rm
  IR}\approx 1.3\times 10^{13}$. (cite: rcc+14) detected the SMG AzTEC-3 at $z=5.299$ with $L_{\rm IR}\approx 1.7\times 10^{13}$ L$_\odot$, and placed a limit on an LBG in the same field at a similar redshift of $z=5.295$ of $L_{\rm IR}\lesssim 5.3 \times 10^{11}$ L$_\odot$.

In addition to the ALMA observations, (cite: ckn+11) studied ID 141, a lensed galaxy at $z=4.243$ from the Herschel Astrophysical Terahertz Large Area Survey, and inferred $L_{\rm IR}\approx (3-8)\times
10^{12}$ L$_\odot$; the range of values accounts for the unknown lensing magnification factor. (cite: crr+12) discovered and studied a lensed SMG at $z=5.243$ from the Herschel Lensing Survey with $L_{\rm
  IR}\approx 10^{13}$ L$_\odot$. (cite: wdc+12) determined a redshift of $z=5.183$ for the SMG HDF 850.1 based on CO and \[C II\] line emission, leading to $L_{\rm IR} \approx 8.7\times 10^{12}$ L$_\odot$. (cite: dbs+12) used stacked MAMBO-2 observations of $z\sim 5$ LBGs to place a limit on their mean luminosity of $L_{\rm IR}\lesssim 3\times
10^{11}$ L$_\odot$, while (cite: cga+14) used stacked SCUBA-2 observations of $z\sim 4.8$ LBGs to find a mean luminosity of $L_{\rm
  IR}\sim 10^{12}$ L$_\odot$ (based on a $3.8\sigma$ detection at 850 $\mu$m).

Finally, two other GRB host galaxies at lower redshifts have been observed with ALMA (cite: wch+12). The host of GRB 021004 at $z=2.330$ was not detected, with a resulting limit of $L_{\rm IR}
\lesssim 3\times 10^{11}$ L$_\odot$ (${\rm SFR_{IR}}\lesssim 50$ M$_\odot$ yr$^{-1}$). The host of the dusty GRB 080607 at $z=3.036$ was marginally detected ($3.4\sigma$) with a resulting luminosity of $(2.4-4.5)\times 10^{11}$ L$_\odot$ (${\rm SFR_{IR}}\approx 40-80$ M$_\odot$ yr$^{-1}$). Prior to ALMA, a few GRB host galaxies at $z\lesssim 2$ were detected in the submillimeter and radio bands (cite: bkf01; fbm+02; bck+03; mhp+14; sod+14), some with inferred IR luminosities that exceed that of Arp 220. However, most GRB host galaxies were not detected at a comparable level to Arp 220 or fainter (cite: bck+03; tbb+04; ptl+06; pp13), ruling out a dominant ULIRG host population.

Thus, in comparison to the previous studies of $z\gtrsim 4$ spectroscopically-confirmed field galaxies, as well as other GRB host galaxies, our ALMA observations of the host of GRB 090423 represent the deepest limit to date in terms of flux density, spectral luminosity, and integrated IR luminosity (Figure [3](#fig:gals)).

# Conclusions

We present ALMA and *Spitzer* observations of the host galaxy of GRB 090423 at $z=8.23$, the highest redshift spectroscopically-confirmed galaxy observed with these facilities to date. The host galaxy remains undetected at rest-frame wavelength of $145$ $\mu$m (ALMA) and $0.39$ $\mu$m (*Spitzer*). The resulting limit on the integrated IR luminosity is $L_{\rm IR}\lesssim 3\times 10^{10}$ L$_\odot$, corresponding to $\lesssim 5$ M$_\odot$ yr$^{-1}$ of obscured star formation; scaling the SED of the low metallicity dwarf galaxy I Zw 18 relaxes the star formation rate upper limit to $\lesssim
100$ M$_\odot$ yr$^{-1}$. In addition, based on the *Spitzer* and *HST* non-detections we place a limit on the host galaxy stellar mass of $M_*\lesssim 5\times 10^7$ M$_\odot$ (100 Myr old stellar population with constant star formation rate). The limit on the unobscured star formation rate based on *HST* rest-frame UV observations is $\lesssim 1.2$ M$_\odot$ yr$^{-1}$.

We additionally compare our ALMA non-detection to millimeter observations of spectroscopically-confirmed galaxies at $z\gtrsim 4$ (undertaken with ALMA and other facilities) and show that the limit on the host of GRB 090423 is the deepest to date compared to any published observations. At this redshift range only SMGs have been convincingly detected, while individual LBGs and LAEs have so far escaped detection even with ALMA (a marginal detection of LBGs at $z\sim 4.8$ in stacked SCUBA-2 observations has been reported by (cite: cga+14)). The only comparable limits to ours are based on ALMA observations of two LAEs at $z=6.595$ and $z=6.96$.

It is quite remarkable that we were able to reach a brightness limit of about 20 times lower than Arp 220 (and comparable to M 82) at $z=8.23$ in only 3 hours of on-source time and with a subset of the ALMA antennas. On the other hand, if typical high redshift galaxies have SEDs similar to the local dwarf I Zw 18 or the host galaxy of GRB 980425, then much deeper ALMA observations will be required to detect their FIR emission. Still, looking forward we anticipate that ALMA observations of GRB host galaxies will be highly desirable and productive, especially targeting spectroscopically-confirmed hosts at $z\gtrsim 4$ with detailed ISM metallicity measurements, a unique sample among high-redshift galaxies.

# Acknowledgments

The Berger GRB group at Harvard is supported in part by the National Science Foundation under Grant AST-1107973. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00953.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This work is based in part on observations made with the Spitzer Space Telescope, which is operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with NASA.

*Facilities:* ALMA, Spitzer (IRAC)

(ref: bck+03) Berger, E., Cowie, L. L., Kulkarni, S. R., Frail, D. A., Aussel, H., & Barger, A. J. 2003, ApJ, 588, 99

(ref: bkf01) Berger, E., Kulkarni, S. R., & Frail, D. A. 2001, ApJ, 560, 652

(ref: bsp+07) Boone, F., Schaerer, D., Pelló, R., Combes, F., & Egami, E. 2007, A&A, 475, 513

(ref: bib+06) Bouwens, R. J., Illingworth, G. D., Blakeslee, J. P., & Franx, M. 2006, ApJ, 653, 53

(ref: bio+11) Bouwens, R. J., et al. 2011, ApJ, 737, 90

(ref: bc03) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000

(ref: bse+04) Bunker, A. J., Stanway, E. R., Ellis, R. S., & McMahon, R. G. 2004, MNRAS, 355, 374

(ref: cwh+10) Calzetti, D., et al. 2010, ApJ, 714, 1256

(ref: crw+13) Carilli, C. L., Riechers, D., Walter, F., Maiolino, R., Wagg, J., Lentati, L., McMahon, R., & Wolfe, A. 2013, ApJ, 763, 120

(ref: cbf+14) Chornock, R., Berger, E., Fox, D. B., Fong, W., Laskar, T., & Roth, K. C. 2014, ArXiv e-prints

(ref: cbf+13) Chornock, R., Berger, E., Fox, D. B., Lunnan, R., Drout, M. R., Fong, W.-f., Laskar, T., & Roth, K. C. 2013, ApJ, 774, 26

(ref: crr+12) Combes, F., et al. 2012, A&A, 538, L4

(ref: cga+14) Coppin, K. E. K., et al. 2014, ArXiv e-prints

(ref: ckn+11) Cox, P., et al. 2011, ApJ, 740, 63

(ref: dgw+13) da Cunha, E., et al. 2013, ApJ, 766, 13

(ref: dbs+12) Davies, L. J. M., Bremer, M. N., Stanway, E. R., Mannering, E., Lehnert, M. D., & Omont, A. 2012, MNRAS, 425, 153

(ref: fpd+13) Finkelstein, S. L., et al. 2013, Nature, 502, 524

(ref: fbm+02) Frail, D. A., et al. 2002, ApJ, 565, 829

(ref: grd+14) González-López, J., et al. 2014, ApJ, 784, 99

(ref: hmf+13) Hezaveh, Y. D., et al. 2013, ApJ, 767, 132

(ref: hcb+10) Hu, E. M., Cowie, L. L., Barger, A. J., Capak, P., Kakazu, Y., & Trouille, L. 2010, ApJ, 725, 394

(ref: iok+06) Iye, M., et al. 2006, Nature, 443, 186

(ref: ken98) Kennicutt, R. C., Jr. 1998, ARA&A, 36, 189

(ref: ktk+03) Kodaira, K., et al. 2003, PASJ, 55, L17

(ref: lbc11) Laskar, T., Berger, E., & Chary, R.-R. 2011, ApJ, 739, 1

(ref: lb10) Leibler, C. N., & Berger, E. 2010, ApJ, 725, 1202

(ref: mrp+05) Malhotra, S., et al. 2005, ApJ, 626, 666

(ref: mdd+11) McLure, R. J., et al. 2011, MNRAS, 418, 2074

(ref: mhp+14) Michałowski, M. J., et al. 2014, A&A, 562, A70

(ref: oom+12) Ono, Y., et al. 2012, ApJ, 744, 83

(ref: owo+14) Ota, K., et al. 2014, ArXiv e-prints

(ref: oeo+13) Ouchi, M., et al. 2013, ApJ, 778, 102

(ref: oms+09) Ouchi, M., et al. 2009, ApJ, 706, 1136

(ref: osf+10) Ouchi, M., et al. 2010, ApJ, 723, 869

(ref: pp13) Perley, D. A., & Perley, R. A. 2013, ApJ, 778, 172

(ref: ptl+06) Priddey, R. S., Tanvir, N. R., Levan, A. J., Fruchter, A. S., Kouveliotou, C., Smith, I. A., & Wijers, R. A. M. J. 2006, MNRAS, 369, 1189

(ref: rbc+13) Riechers, D. A., et al. 2013, Nature, 496, 329

(ref: rcc+14) Riechers, D. A., et al. 2014, ArXiv e-prints

(ref: raw+09) Rieke, G. H., Alonso-Herrero, A., Weiner, B. J., Pérez-González, P. G., Blaylock, M., Donley, J. L., & Marcillac, D. 2009, ApJ, 692, 556

(ref: sdc+09) Salvaterra, R., et al. 2009, Nature, 461, 1258

(ref: sgl09) Savaglio, S., Glazebrook, K., & Le Borgne, D. 2009, ApJ, 691, 182

(ref: sko+12) Shibuya, T., Kashikawa, N., Ota, K., Iye, M., Ouchi, M., Furusawa, H., Shimasaku, K., & Hattori, T. 2012, ApJ, 752, 114

(ref: sbt+11) Stanway, E. R., Bremer, M. N., Tanvir, N. R., Levan, A. J., & Davies, L. J. M. 2011, MNRAS, 410, 1496

(ref: sbm03) Stanway, E. R., Bunker, A. J., & McMahon, R. G. 2003, MNRAS, 342, 439

(ref: sks+12) Swinbank, A. M., et al. 2012, MNRAS, 427, 1066

(ref: sss+14) Swinbank, A. M., et al. 2014, MNRAS, 438, 1267

(ref: sod+14) Symeonidis, M., et al. 2014, ArXiv e-prints

(ref: tbb+04) Tanvir, N. R., et al. 2004, MNRAS, 352, 1073

(ref: tfl+09) Tanvir, N. R., et al. 2009, Nature, 461, 1254

(ref: tlf+12) Tanvir, N. R., et al. 2012, ApJ, 754, 46

(ref: tkk+06) Totani, T., Kawai, N., Kosugi, G., Aoki, K., Yamada, T., Iye, M., Ohta, K., & Hattori, T. 2006, PASJ, 58, 485

(ref: vpf+11) Vanzella, E., et al. 2011, ApJL, 730, L35

(ref: wwc+12) Wagg, J., et al. 2012, ApJL, 752, L30

(ref: wdc+12) Walter, F., et al. 2012, Nature, 486, 233

(ref: wch+12) Wang, W.-H., Chen, H.-W., & Huang, K.-Y. 2012, ApJL, 761, L32

(ref: wcd+14) Wiklind, T., et al. 2014, ApJ, 785, 111

|  |  |  |  |  |
|:---|:---|:---|:---|:---|
| Instrument | $\lambda_{\rm obs}$ | $F_\nu\,^a$ | $L_\nu\,^a$ | Reference |
|  |  | ($\mu$Jy) | (erg s$^{-1}$ Hz$^{-1}$) |  |
| ATCA | 0.79 cm | $\lesssim 9.3$ | $\lesssim 8.7\times 10^{30}$ | Stanway et al. 2011 |
| ALMA | 0.14 cm | $\lesssim 33$ | $\lesssim 3.1\times 10^{31}$ | This paper |
| *Spitzer*/IRAC | 3.6 $\mu$m | $\lesssim 8.1\times 10^{-2}$ | $\lesssim 7.6\times 10^{28}$ | This paper |
| *HST*/WFC3 | 1.54 $\mu$m | $\lesssim 9.1\times 10^{-3}$ | $\lesssim 8.6\times 10^{27}$ | Tanvir et al. 2012 |
| *HST*/WFC3 | 1.25 $\mu$m | $\lesssim 6.0\times 10^{-3}$ | $\lesssim 5.6\times 10^{27}$ | Tanvir et al. 2012 |

: Observations of the Host Galaxy of GRB 090423 

Table notes: $^a$ Limits are $3\sigma$.

| Parameter            | Value                                    |
|:---------------------|:-----------------------------------------|
| $L_{\rm IR}\,^a$     | $\lesssim (2-5)\times 10^{10}$ L$_\odot$ |
| ${\rm SFR_{IR}}\,^a$ | $\lesssim 3-5$ M$_\odot$ yr$^{-1}$       |
| ${\rm SFR_{UV}}\,^b$ | $\lesssim 1.2$ M$_\odot$ yr$^{-1}$       |
| $M_*\,^c$            | $\lesssim (1-5)\times 10^7$ M$_\odot$    |

: Inferred Properties of the Host Galaxy of GRB 090423 

Table notes: $^a$ Assuming $T_{\rm dust}\approx 30-50$ K and $\beta\approx 1.5-2$.\
$^b$ Assuming $A_V^{\rm host}=0$ mag.\
$^c$ Assuming a stellar population age of $10-100$ Myr, constant star formation rate, Salpeter IMF, $Z=0.2$ Z$_\odot$, and $A_V^{\rm
    host}=0$ mag.

![](fig1.eps)

![image](fig2a.ps) ![image](fig2b.ps)

![](fig3.ps)

</paper>

## Items to check

```json
[
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "1''.0 x 0''.80",
  "failed_quote": "The resulting combined continuum map (natural weighting without primary beam correction) has an rms noise of 11 muJy beam^{-1} for a synthesized beam size (full-width at half maximum) of 1''.0 x 0''.80"
 },
 {
  "path": "data.sensitivity.evidence[0]",
  "value": "11 muJy beam^-1 rms noise",
  "failed_quote": "The resulting combined continuum map (natural weighting without primary beam correction) has an rms noise of 11 muJy beam^{-1} for a synthesized beam size (full-width at half maximum) of 1''.0 x 0''.80"
 },
 {
  "path": "data.other_facilities[0].provided.evidence[1]",
  "value": "3.6 um warm mission DDT observations (Program 538) yielding an upper limit of F_nu(3.6 um) < 81 nJy (3-sigma)",
  "failed_quote": "We therefore place an upper limit on the brightness of the host of F_nu(3.6 mu m < 81 nJy (3sigma; Table 1)."
 },
 {
  "path": "data.simulations_or_models_as_data[1].evidence[0]",
  "value": "Bruzual & Charlot (2003) stellar population synthesis models",
  "failed_quote": "Utilizing the (cite: bc03) stellar population synthesis models with a constant star formation rate, a Salpeter IMF, a metallicity of 0.2 Z_odot, and no dust extinction"
 },
 {
  "path": "processing.imaging.weighting_robust.evidence[0]",
  "value": "natural weighting",
  "failed_quote": "The resulting combined continuum map (natural weighting without primary beam correction) has an rms noise of 11 muJy beam^{-1}"
 },
 {
  "path": "processing.imaging.primary_beam_correction.evidence[0]",
  "value": "without primary beam correction",
  "failed_quote": "The resulting combined continuum map (natural weighting without primary beam correction) has an rms noise of 11 muJy beam^{-1}"
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "1''.0 x 0''.80 FWHM",
  "failed_quote": "for a synthesized beam size (full-width at half maximum) of 1''.0 x 0''.80 (Figure 1)."
 },
 {
  "path": "processing.imaging.final_rms.evidence[0]",
  "value": "11 muJy beam^-1",
  "failed_quote": "The resulting combined continuum map (natural weighting without primary beam correction) has an rms noise of 11 muJy beam^{-1} for a synthesized beam size (full-width at half maximum) of 1''.0 x 0''.80"
 },
 {
  "path": "processing.inherited[0].what.evidence[0]",
  "value": "SFR to IR luminosity calibration relation",
  "failed_quote": "The limit on the integrated IR luminosity corresponds to an upper bound on the obscured star formation rate (cite: ken98; cwh+10), of SFR_IR <= 3-5 M_odot yr^{-1}."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Stellar population age assumptions typical of GRB host galaxies (10-100 Myr)",
  "failed_quote": "for a stellar population age of 10-100 Myr (typical of GRB host galaxies; (cite: sgl09; lb10)) the limit on the host stellar mass is M_* <= (1-5) x 10^7 M_odot."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Calibrated gain, bandpass, and absolute flux manually setting J 0854+2006 flux via Ganymede/Ceres, then imaged combined continuum using natural weighting",
  "failed_quote": "The resulting combined continuum map (natural weighting without primary beam correction) has an rms noise of 11 muJy beam^{-1} for a synthesized beam size (full-width at half maximum) of 1''.0 x 0''.80"
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[1]",
  "value": "Natural weighting, beam 1''.0 x 0''.80, center frequency ~222 GHz",
  "failed_quote": "The resulting combined continuum map (natural weighting without primary beam correction) has an rms noise of 11 muJy beam^{-1} for a synthesized beam size (full-width at half maximum) of 1''.0 x 0''.80"
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Measured point-source flux density at the known afterglow coordinates and derived 3-sigma upper limit",
  "failed_quote": "No source is detected at the location of GRB 090423 (with a flux density at the source location of -4 +/- 11 muJy), leading an upper limit of F_nu(222 GHz) <= 33 muJy (3sigma; Table 1)."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[1]",
  "value": "Position R.A. = 09h55m33.29s, Decl. = +18°08'57.8'' (J2000), 3-sigma detection threshold",
  "failed_quote": "leading an upper limit of F_nu(222 GHz) <= 33 muJy (3sigma; Table 1)."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "Host galaxy is coincident with GRB afterglow position",
  "failed_quote": "No source is detected at the location of GRB 090423 (with a flux density at the source location of -4 +/- 11 muJy)"
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Modeled dust emission using modified blackbody SED and template comparison (Rieke et al. 2009; Arp 220, M 82) to compute L_IR(8-1000 um), then converted to SFR_IR",
  "failed_quote": "Using the standard modified blackbody SED of dust emission, with a dust temperature range of T_dust approx 30-50 K and beta approx 1.5-2 (e.g., (cite: sss+14)), the ALMA non-detection corresponds to an upper limit on the integrated IR luminosity of L_IR(8-1000 mu m) <= (2-5) x 10^10 L_odot"
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Modeled dust emission using modified blackbody SED and template comparison (Rieke et al. 2009; Arp 220, M 82) to compute L_IR(8-1000 um), then converted to SFR_IR",
  "failed_quote": "The limit on the integrated IR luminosity corresponds to an upper bound on the obscured star formation rate (cite: ken98; cwh+10), of SFR_IR <= 3-5 M_odot yr^{-1}."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "T_dust = 30-50 K, beta = 1.5-2, T_CMB(z=8.23) approx 25 K",
  "failed_quote": "with a dust temperature range of T_dust approx 30-50 K and beta approx 1.5-2 (e.g., (cite: sss+14)), the ALMA non-detection corresponds to an upper limit on the integrated IR luminosity of L_IR(8-1000 mu m) <= (2-5) x 10^10 L_odot; the lower bound on the blackbody temperature is set by the cosmic microwave background temperature T_CMB(z=8.23) approx 25 K"
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Kennicutt (1998) / Calzetti et al. (2010) SFR_IR calibrations",
  "failed_quote": "The limit on the integrated IR luminosity corresponds to an upper bound on the obscured star formation rate (cite: ken98; cwh+10), of SFR_IR <= 3-5 M_odot yr^{-1}."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Bruzual & Charlot (2003) population synthesis modeling fitting Spitzer 3.6 um and HST upper limits",
  "failed_quote": "Utilizing the (cite: bc03) stellar population synthesis models with a constant star formation rate, a Salpeter IMF, a metallicity of 0.2 Z_odot, and no dust extinction, we find that for a stellar population age of 10-100 Myr (typical of GRB host galaxies; (cite: sgl09; lb10)) the limit on the host stellar mass is M_* <= (1-5) x 10^7 M_odot."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "Constant SFR, Salpeter IMF, Z = 0.2 Z_sun, age = 10-100 Myr, A_V = 0 mag",
  "failed_quote": "Utilizing the (cite: bc03) stellar population synthesis models with a constant star formation rate, a Salpeter IMF, a metallicity of 0.2 Z_odot, and no dust extinction, we find that for a stellar population age of 10-100 Myr"
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[1]",
  "value": "Constant SFR, Salpeter IMF, Z = 0.2 Z_sun, age = 10-100 Myr, A_V = 0 mag",
  "failed_quote": "Assuming a stellar population age of 10-100 Myr, constant star formation rate, Salpeter IMF, Z=0.2 Z_odot, and A_V^{rm host}=0 mag."
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Negligible dust extinction in UV/optical (A_V = 0 mag)",
  "failed_quote": "Assuming a stellar population age of 10-100 Myr, constant star formation rate, Salpeter IMF, Z=0.2 Z_odot, and A_V^{rm host}=0 mag."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "ALMA 222 GHz continuum flux density at GRB location = -4 muJy",
  "failed_quote": "No source is detected at the location of GRB 090423 (with a flux density at the source location of -4 +/- 11 muJy)"
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "ALMA 222 GHz 3-sigma continuum upper limit = 33 muJy",
  "failed_quote": "leading an upper limit of F_nu(222 GHz) <= 33 muJy (3sigma; Table 1)."
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Rest-frame 145 um spectral luminosity upper limit = 3.1e31 erg s^-1 Hz^-1",
  "failed_quote": "Converted to rest-frame spectral luminosity, the non-detections correspond to L_nu(145 mu m) <= 3.1 x 10^31 erg s^{-1} Hz^{-1}"
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "Spitzer 3.6 um 3-sigma flux density upper limit = 81 nJy",
  "failed_quote": "We therefore place an upper limit on the brightness of the host of F_nu(3.6 mu m <= 81 nJy (3sigma; Table 1)."
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "Integrated IR luminosity L_IR (8-1000 um) limit = 2e10-5e10 L_sun",
  "failed_quote": "L_IR | <= (2-5) x 10^10 L_odot"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Obscured star formation rate SFR_IR limit = 3-5 M_sun yr^-1",
  "failed_quote": "SFR_IR | <= 3-5 M_odot yr^{-1}"
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Host galaxy stellar mass M_* limit = 1e7-5e7 M_sun",
  "failed_quote": "M_* | <= (1-5) x 10^7 M_odot"
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "The host galaxy of GRB 090423 at z=8.23 remains undetected in 222 GHz ALMA continuum and 3.6 um Spitzer imaging.",
  "failed_quote": "The host remains undetected to 3sigma limits of F_nu(222 GHz) <= 33 muJy and F_nu(3.6 mu m) <= 81 nJy."
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "The ALMA FIR luminosity limit is about 20 times fainter than Arp 220 and comparable to M 82, placing the most constraining FIR limit on a z > 4 galaxy to date.",
  "failed_quote": "we compare our millimeter observations to those of field galaxies at z >= 4 (Lyman break galaxies, Lya emitters, and submillimeter galaxies), and find that our limit on the FIR luminosity is the most constraining to date"
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "The host galaxy is not a ULIRG or LIRG; obscured star formation is constrained to SFR_IR <= 3-5 M_sun yr^-1.",
  "failed_quote": "The IR luminosity upper limit is thus a few times lower than the scale for a LIRG, and agrees well with the comparison to the (cite: raw+09) templates. The limit on the integrated IR luminosity corresponds to an upper bound on the obscured star formation rate (cite: ken98; cwh+10), of SFR_IR <= 3-5 M_odot yr^{-1}."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "The host galaxy stellar mass is constrained to M_* <= (1-5) x 10^7 M_sun for stellar population ages of 10-100 Myr.",
  "failed_quote": "we find that for a stellar population age of 10-100 Myr (typical of GRB host galaxies; (cite: sgl09; lb10)) the limit on the host stellar mass is M_* <= (1-5) x 10^7 M_odot."
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "Band 6 continuum probes the rest-frame ~145 um FIR dust peak at z=8.23, reaching sensitivity below LIRG luminosities.",
  "failed_quote": "The observations are aimed at reaching a rest-frame FIR luminosity level below that of a luminous infrared galaxy (LIRG: L_{IR}=10^{11} L_odot)."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "If high-redshift galaxies have SEDs resembling low-metallicity dwarf galaxies like I Zw 18 or GRB 980425 host, FIR limits relax significantly (SFR_IR <= 100 M_sun yr^-1), requiring much deeper observations.",
  "failed_quote": "scaling the SED of the low metallicity dwarf galaxy I Zw 18 relaxes the star formation rate upper limit to <= 100 M_odot yr^{-1}."
 }
]
```
