# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2015PASJ...67...93H\gemini38f\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588

Institute of Astronomy, University of Tokyo, 2-21-1 Osawa, Mitaka, Tokyo 181-0015 The Graduate University for Advanced Studies (SOKENDAI), 2-21-1 Osawa, Mitaka, Tokyo 181-8588 Research Center for the Early Universe, University of Tokyo, 7-3-1 Hongo, Bunkyo-ku, Tokyo 113-0033 Department of Physics, University of Tokyo, 7-3-1 Hongo, Bunkyo-ku, Tokyo 113-0033 Kavli Institute for the Physics and Mathematics of the Universe (Kavli IPMU, WPI), University of Tokyo, Chiba 277-8583

NAOJ Fellow

# Abstract

We present spatially-resolved properties of molecular gas and dust in a gravitationally-lensed submillimeter galaxy H-ATLAS J090311.6$+$003906 (SDP.81) at $z=3.042$ revealed by the Atacama Large Millimeter/submillimeter Array (ALMA). We identified 14 molecular clumps in the CO(5–4) line data. The surface density of molecular gas ($\Sigma_{\rm H_2}$) and star-formation rate ($\Sigma_{\rm SFR}$) of the clumps are more than three orders of magnitude higher than those found in local spiral galaxies. The clumps are placed in the ‘burst’ sequence in the $\Sigma_{\rm H_2}$–$\Sigma_{\rm SFR}$ plane, suggesting that $z \sim 3$ molecular clumps follow the star-formation law derived for local starburst galaxies. With our gravitational lens model, the positions in the source plane are derived for the molecular clumps, dust clumps, and stellar components identified in the *Hubble Space Telescope* image. The molecular and dust clumps are confined within a $\sim$2 kpc region, while the spatial extent of the stellar components is as large as $\sim$6 kpc and offset toward the west. The molecular clumps have a systematic velocity gradient in the north-south direction, which may indicate a rotating gas disk. One possible scenario is that the components of molecular gas, dust, and stars are distributed in a several-kpc scale rotating disk, and the stellar emission is heavily obscured by dust in the central star-forming region. Alternatively, SDP.81 can be explained by a merging system, where dusty starbursts occur in the region where the two galaxies collide, surrounded by tidal features traced in the stellar components.

# Introduction

Deep and wide-field submillimeter surveys have uncovered dust-obscured star-forming galaxies at high redshift (referred to as submillimeter galaxies; SMGs) (e.g., (cite: blai02), for a review). SMGs have intense star-forming activity with star-formation rates (SFRs) of a few 100–1000 $M_{\odot}$ yr$^{-1}$, which could be triggered by gas-rich galaxy mergers (e.g., (cite: tacc06)). SMGs and local ultra-luminous infrared galaxies (ULIRGs) are known to be on the same relation on the molecular gas mass–far infrared (FIR) luminosity plane ($M_{\rm H_2}$–$L_{\rm FIR}$) or molecular gas surface density–SFR surface density plane ($\Sigma_{\rm H_2}$–$\Sigma_{\rm SFR}$), so-called ‘burst sequence’, high above that of ‘normal’ star-forming galaxies at local and $z \sim 1$–3 universe (cite: dadd10; genz10). Spatially resolved observations of molecular gas in SMGs are essential to investigate the star-forming properties. However, only a handful of studies exists (e.g., (cite: swin10; shar13; rawl14; hodg15)) due to the limited spatial resolution and sensitivity of existing instruments.

Gravitational lensing is a powerful tool to probe the physical properties of distant galaxies in detail because of its magnification effect. The gravitational lensing caused by a foreground massive galaxy or cluster of galaxies has been used to probe dusty star-forming galaxies at high-redshifts (e.g., (cite: smai97; smai02; negr10; viei13)). (cite: swin10) discovered a $z = 2.3$ SMG (SMM J2135$-$0102) which is lensed by a $z = 0.3$ foreground galaxy cluster with the magnification factor of $\mu = 32.5$, allowing them to examine the properties of the SMG at 100 pc scale.

H-ATLAS J090311.6$+$003906 (SDP.81) is one of the brightest sources discovered in the *Herschel* Astrophysical Terahertz Large Area Survey (HATLAS) (cite: eale10). Multi-wavelength follow-up observations have shown that SDP.81 is an SMG at $z = 3.042 \pm 0.001$ that is gravitationally lensed by a foreground massive elliptical galaxy at $z = 0.2999 \pm 0.0002$ (cite: negr10; negr14). Corrected for the gravitational lensing magnification factor of $\mu = 11$ (cite: buss13), SDP.81 has an intrinsic FIR luminosity of $L_{\rm FIR} = 5 \times 10^{12}$ $L_{\odot}$ and a SFR of $\sim$500 $M_{\odot}$ yr$^{-1}$. Recently, the Atacama Large Millimeter/submillimeter Array (ALMA) observed SDP.81 at 1–2 mm in the Science Verification observations with an angular resolution up to 0.03$''$ (which corresponds to $\sim$200 pc at $z=3.042$), offering an excellent opportunity to study the spatially-resolved properties of an SMG.

In this Letter, we present the properties of SDP.81 revealed by the high-angular resolution observations with ALMA. Throughout the paper, we adopt a cosmology with $H_0=72$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm{M}}=0.26$, and $\Omega_{\Lambda}=0.74$, and $1''$ corresponds to 7.78 kpc at $z=3.042$.

# Data

## ALMA Data

We used the calibrated data set publicly available through the ALMA Science Portal. The details of observations and data reduction are described in (cite: alma15a) and (cite: alma15b). SDP.81 was observed as part of Science Verification of the ALMA Long Baseline Campaign in October, 2014, at Band 4 (151 GHz, or 2.0 mm), Band 6 (236 GHz, or 1.3 mm), and Band 7 (290 GHz, or 1.0 mm) with the baseline lengths of $\sim$5–15 km and with 31–36 antennas.

![](figure1.eps)

## *HST* Data

We made use of the archival data of *HST*/Wide Field Camera 3 (WFC3) taken by (cite: negr14). We retrieved the calibrated, flat-fielded individual exposure frames of WFC3 with the F160W filter ($H$-band) from the archive, and then coadded them by ourselves using the iraf MultiDrizzle package. The final pixel scale was set to 0.064$''$ to improve the resolution and quality of the image. We calibrated the coordinates of the image using the catalog data from the Data Release 12 of the Sloan Digital Sky Survey (SDSS). We used 46 SDSS sources located in the image to derive the astrometric fit using iraf. The rms error to the fit is 0.085$''$ in right ascension and 0.100$''$ in declination. We checked that the coordinates of the foreground lens galaxy in the SDSS catalog match the coordinates of the continuum emission detected in Band 4, 6, and 7 (cite: alma15b) within 0.015$''$. The offset between the center of the foreground lens and the ALMA continuum emission is smaller than the ALMA beamsize, showing the consistency of astrometry between the *HST* and ALMA images (Figure [\[fig:image\]](#fig:image)c).

We used the software galfit (cite: peng02) to deblend the background lensed source from the foreground lens galaxy. According to (cite: negr14), two Sérsic profiles were simultaneously fitted to the foreground lens galaxy to cleanly subtract it. As a result, the brighter component of the foreground lens galaxy has the Sérsic index of $n=4.42$ (elliptical), while the fainter component has the index of $n=1.03$ (exponential). The profiles are consistent with those obtained by (cite: negr14). The stellar arc structure seen in the lens-subtracted image shown in Figure [\[fig:image\]](#fig:image)d is similar to the arcs seen in the ALMA CO line and continuum images, but they are clearly offset toward the west.

# Lens Model

The analysis of gravitational lensing was conducted by (cite: tamu15) using the glafic software package (cite: ogur10). The lens model was constructed by identifying the knots which were common in all three continuum images at 1.0, 1.3 and 2.0 mm. The lensed images are explained by the best-fit mass model with a mass profile of an isothermal ellipsoid with a 400-pc core. The core radius of the isothermal ellipsoid agrees well with that of the stellar light in the *HST*/WFC3 image, and the position of the predicted mass centroid is consistent with that of the emission detected in the ALMA continuum images. (cite: tamu15) found that the continuum emission has a power-law spectral index of $-0.64 \pm 0.1$ from 1.0 mm to 20 cm, and it is likely that the non-thermal emission arises from an active galactic nucleus of the lens galaxy. This lens model is used to compute the positions on the source plane (Section [3.2](#sec:sdp81)).

# Molecular Clumps

## Clump Identification

We identified molecular clumps by using the line cube (spectral resolution of 21 km s$^{-1}$) and the velocity-integrated intensity map of CO(5–4). We first searched for the peak positions with $\ge$3.5$\sigma$ in the velocity-integrated intensity map created by including pixels above 1.5$\sigma$ in the line cube. We then used the clumpfind package (cite: will94) to search for clumps in the line cube. We identified 14 molecular clumps along the arcs detected by both methods (Figure [\[fig:image\]](#fig:image)a). The positions, magnification factors, and mean velocities are shown in Table [\[tab:property\]](#tab:property). We caution here that the gravitational lensing can possibly produce two (or multiple) clumps in the image plane that are in fact the same clump in the source plane. However, because of the low SN, it may be difficult to identify all of the multiples in the CO(5–4) image. We use the positions in image plane and source plane, and the mean velocities, as a guide to identify multiple images, and we suggest that clumps 1 and 13 and clumps 4 and 5 are possibly counter images of the same source.

If the clumps are spatially resolved with the ALMA beam, the transverse direction should be more extended than the radial direction. We found that some of the clumps do not appear to be extended in the transverse direction, and it is likely that they are unresolved. In order to measure the size of the clumps, higher angular resolution observations are needed.

The magnification of the four clumps close to the critical curve (ID 4, 5, 7, and 8) is large ($>$100) and varies significantly within each clump. It is possible that they have properties with different physical scales compared to the other clumps, and we exclude these clumps in the discussion of star formation properties. Except for the four clumps, the intrinsic spatial scale is roughly a few 100 pc in the source plane after correcting for the magnification factor and assuming that the clumps are spatially resolved.

## Surface densities of molecular gas and SFR

We derived the surface density of the molecular gas and the SFR in order to investigate the intrinsic properties of SDP.81. We assume that there is no significant difference in the distribution of CO and dust emission within the measured region for each clump, and thus the effect of differential magnification (e.g., (cite: blai99; serj12; heza12)) is negligible. Because the distribution of molecular clouds or star-forming regions smaller than the beamsize is unknown, we assume a filling factor of unity in this study. We note that the filling factor might be less than unity if they are not spatially resolved.

We used regions above 2$\sigma$ in the CO(5–4) velocity-integrated map for conducting photometry and estimating the physical quantities of each clump. The photometry of dust continuum was conducted on the 1.0 mm image in the same regions used for the CO photometry. The CO luminosity of each clump was calculated from $L'_{\rm CO} = 3.25 \times 10^7 S_{\rm CO}\Delta v \nu_{\rm obs}^{-2} D_{\rm L}^2 (1+z)^{-3}$ (cite: solo05), where $S_{\rm CO}\Delta v$ is the velocity-integrated intensity in Jy km s$^{-1}$, $\nu_{\rm obs}$ is the observed line frequency in GHz, and $D_{\rm L}$ is the luminosity distance in Mpc. The error of $S_{\rm CO}\Delta v$ is calculated by using the equation of (cite: hain04). We used a CO line ratio of CO(5–4)/CO(1–0) $= 0.3$ (cite: alma15b). The molecular gas mass is derived from $M_{\rm H_2} = \alpha_{\rm CO} L'_{\rm CO(1-0)}$, where $\alpha_{\rm CO}$ is the CO-to-molecular gas mass conversion factor including He mass. We adopted a conversion factor of $\alpha_{\rm CO} = 0.8$ $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$, the standard value for ULIRGs (cite: down98). The FIR luminosity and dust mass were derived from $L_{\rm FIR} = 4\pi M_{\rm dust} \int_0^{\infty} \kappa_d(\nu_{\rm{rest}})B(\nu_{\rm{rest}}, T_{\rm dust}) d\nu$, and from $M_{\rm dust}=S_{\rm{obs}}D_L^2/[(1+z)\kappa_d(\nu_{\rm{rest}})B(\nu_{\rm{rest}}, T_{\rm dust})]$ (cite: debr03), where $\kappa_d(\nu_{\rm{rest}})$ is the dust mass absorption coefficient, $\nu_{\rm{rest}}$ is the rest-frame frequency, $T_{\rm dust}$ is the dust temperature, $B(\nu_{\rm{rest}}, T_{\rm dust})$ is the Planck blackbody function, and $S_{\rm{obs}}$ is the observed flux density. We assume that the absorption coefficient varies as $\kappa_d \propto \nu^{\beta}$ and the emissivity index lies between 1 and 2 (e.g., (cite: hild83)), and adopt $\kappa_d(125\ \mu m) = 2.64 \pm 0.29$ m$^2$ kg$^{-1}$ (cite: dunn03) and $\beta = 1.5$. The dust temperature of $T_{\rm dust} = 39.3$ K was derived by (cite: negr14) for the integrated value of SDP.81, which is comparable to high-redshift ULIRGs and SMGs (e.g., (cite: kova06; syme13)). We adopted the dust temperature for each clump. The SFR was derived from SFR $= 1.72 \times 10^{-10} L_{\rm FIR}$ (cite: kenn98a). The derived surface densities of molecular gas and SFR are shown in Table [\[tab:property\]](#tab:property).

Note: ID 1 and 13, and ID 4 and 5 are possibly counter images of the same source. $^a$ Right ascension and declination of the ALMA peak positions in the image plane (J2000); $^b$ Right ascension and declination in the source plane (J2000); $^c$ Mean, minimum, and maximum magnification factors measured within the region of each clump; $^d$ Mean velocity measured within the region of each clump; $^e$ Molecular gas surface density; $^f$ SFR surface density.

# Discussion

## Star-formation Properties

The surface density of molecular gas and SFR for the molecular clumps are plotted in Figure [1](#fig:sk). The magnification varies with each clump, and a clump with a larger magnification traces an intrinsically fainter one. We reiterate that the magnification correction is not necessary when discussing the surface density of molecular gas and SFR, because the gravitational lensing conserves the surface brightness for the identified clumps. The molecular clumps of SDP.81 traced in this study have surface densities that are more than three orders of magnitude higher than those of local spiral galaxies, and they are similar to those of the $\sim$100 pc scale clumps of the spatially-resolved SMG SMM J21352 (cite: thom15). We note that the four clumps with high magnification ($>$100; Section [2.1](#sec:id)) which are not presented in Figure [1](#fig:sk) share the same region with the other clumps. The SFR density ranges between 100–300 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$, which is lower than the Eddington-limited star formation (maximum starburst; (cite: elme99)) (cite: ryba15). It is known that local star-forming galaxies follow a relation in the $\Sigma_{\rm H_2}$–$\Sigma_{\rm SFR}$ plane (Schmidt–Kennicutt relation; (cite: schm59; kenn98a)), and it is extended to include higher redshift sources (e.g., (cite: genz10)). The clumps of SDP.81 are located in the ‘burst’ sequence (cite: dadd10) with a gas depletion time scale of $\sim$100 Myr, suggesting active star-forming activity in the clumps. If we adopt the Galactic conversion factor ($\alpha_{\rm CO} = 4.3 M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$; (cite: bola13)), these clumps are located on the sequence of normal star-forming galaxies. Note that if the filling factor is less than unity, the data points in Figure [1](#fig:sk) will shift to the upper-right direction. Regardless of the exact location of these clumps in the $\Sigma_{\rm H_2}$–$\Sigma_{\rm SFR}$ plane, the derived $\Sigma_{\rm SFR}/\Sigma_{\rm H_2}$ ratios are consistent with the values found in the Milky Way clumps (e.g., (cite: heid10; evan14)), suggesting that the star-formation law can be applied to molecular clumps at $z \sim 3$.

![](figure2.eps)

## The Nature of SDP.81

By using our lens model (cite: tamu15) and the glafic software, we determined the positions of molecular clumps on the source plane (Figure [2](#fig:source-plane)). The clumps are distributed over a 2 kpc area, and they overlap with the dust clumps identified in (cite: tamu15). We also derived the source-plane positions for the brighter points of the stellar components shown as crosses in Figure [\[fig:image\]](#fig:image)d. The points are selected so that the relative correspondence of the stellar components between the image plane and the source plane is easily visualized. The stellar components traced in this study are distributed over $\sim$6 kpc in the NE-SW direction, which is consistent with the result of (cite: dye14), and offset from the molecular gas and dust clumps toward the west. Since the lensing model of (cite: tamu15) includes the contribution from the stellar emission detected in the *HST* image, we argue that the extension of the stellar emission is real and not due to the lens model being based on the clumps of ALMA images. We note that, since the main aim of this study is to check the positional correlation between molecular gas/dust and stars, we only computed the position of the components marked in Figure [\[fig:image\]](#fig:image)d, and the spatial extent of each component is not taken into account.

The mean velocity of each molecular clump measured in the image plane is shown in color in Figure [2](#fig:source-plane) (top). A velocity gradient with a peak-to-peak value of $\sim$300 km s$^{-1}$ in the north-south direction can be seen, which could indicate a rotating gas disk. In Figure [2](#fig:source-plane) (bottom), the molecular gas surface density is shown in color scale. The molecular gas surface density appears to be higher in the central part of the molecular/dust ‘diskf and decreasing toward the edge, although the uncertainty is large.

What is the nature of SDP.81? One possible scenario is that the components of molecular gas, dust, and stars are distributed in a several-kpc scale rotating disk, and the stellar emission is heavily obscured by dust in the central star-forming region. This is qualitatively consistent with the $z=4.05$ SMG GN20, where an offset of rest-frame UV-emitting region by 4 kpc from a region with CO and dust emission has been found (cite: iono06; hodg15). Alternatively, SDP.81 may be a merging system, where dusty starbursts occur in the interface between the two colliding galaxies while the tidal features are widely extended. A similar large scale velocity gradient is seen in a recent ALMA CO(3–2) image of the Antennae Galaxies ((cite: whit14)). The CO(5–4) line we used in this study has a relatively high critical density ($10^{5}$ cm$^{-3}$) and it may not trace the gas of the entire disk. Future observations of the lower transition CO lines will allow us to study the detailed distribution and kinematics of the diffuse gas, providing further insights to the exact nature of SDP.81.

![](figure3.eps)

We are grateful to Rie Miura and Alasdair Thomson for providing data. We thank the referee for helpful comments and suggestions. BH is supported by JSPS KAKENHI Grant Number 15K17616. YT is supported by KAKENHI (No. 25103503). DI is supported by the 2015 Inamori Research Grants Program. YM is supported by KAKENHI (No. 20647268). MH is supported by Research Fellowship for Young Scientists from the Japan Society of the Promotion of Science (JSPS). MO is supported in part by World Premier International Research Center Initiative (WPI Initiative), MEXT, Japan and Grant-in-Aid for Scientific Research from the JSPS (26800093). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00016.SV. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Data analysis were in part carried out on common use data analysis computer system at the Astronomy Data Center, ADC, of the National Astronomical Observatory of Japan.

(ref: alma15a) ALMA Partnership, Fomalont, E. B., Vlahakis, C., et al. 2015, arXiv:1504.04877 (ref: alma15b) ALMA Partnership, Vlahakis, C., Hunter, T. R., et al. 2015b, arXiv:1503.02652 (ref: bigi10) Bigiel, F., Leroy, A., Walter, F., et al. 2010, AJ, 140, 1194 (ref: blai99) Blain, A. W. 1999, MNRAS, 304, 669 (ref: blai02) Blain, A. W., Smail, I., Ivison, R. J., Kneib, J.-P., & Frayer, D. T. 2002, Phys. Rep., 369, 111 (ref: bola13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207 (ref: both10) Bothwell, M. S., Chapman, S. C., Tacconi, L., et al. 2010, MNRAS, 405, 219 (ref: buss13) Bussmann, R. S., Pérez-Fournon, I., Amber, S., et al. 2013, ApJ, 779, 25 (ref: dadd10) Daddi, E., Elbaz, D., Walter, F., et al. 2010, ApJL, 714, L118 (ref: debr03) De Breuck, C., Neri, R., Morganti, R., et al. 2003, A&A, 401, 911

(ref: dunn03) Dunne, L., Eales, S. A., & Edmunds, M. G. 2003, MNRAS, 341, 589 (ref: down98) Downes, D., & Solomon, P. M. 1998, ApJ, 507, 615 (ref: dye14) Dye, S., Negrello, M., Hopwood, R., et al. 2014, MNRAS, 440, 2013 (ref: eale10) Eales, S., Dunne, L., Clements, D., et al. 2010, PASP, 122, 499 (ref: elme99) Elmegreen, B. G. 1999, ApJ, 517, 103 (ref: evan14) Evans, N. J., II, Heiderman, A., & Vutisalchavakul, N. 2014, ApJ, 782, 114 (ref: genz10) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091 (ref: hain04) Hainline, L. J., Scoville, N. Z., Yun, M. S., et al. 2004, ApJ, 609, 61 (ref: heid10) Heiderman, A., Evans, N. J., II, Allen, L. E., Huard, T., & Heyer, M. 2010, ApJ, 723, 1019 (ref: heza12) Hezaveh, Y. D., Marrone, D. P., & Holder, G. P. 2012, ApJ, 761, 20 (ref: hild83) Hildebrand, R. H. 1983, QJRAS, 24, 267 (ref: hodg15) Hodge, J. A., Riechers, D., Decarli, R., et al. 2015, ApJL, 798, LL18 (ref: hugh97) Hughes, D. H., Dunlop, J. S., & Rawlings, S. 1997, MNRAS, 289, 766 (ref: iono06) Iono, D., Peck, A. B., Pope, A., et al. 2006, ApJL, 640, L1 (ref: kenn98a) Kennicutt, R. C., Jr. 1998a, ApJ, 498, 541 (ref: kenn98b) Kennicutt, R. C., Jr. 1998b, ARA&A, 36, 189 (ref: kova06) Kovács, A., Chapman, S. C., Dowell, C. D., et al. 2006, ApJ, 650, 592 (ref: mcmu07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Data Analysis Software and Systems XVI, 376, 127 (ref: miur14) Miura, R. E., Kohno, K., Tosaki, T., et al. 2014, ApJ, 788, 167 (ref: negr10) Negrello, M., Hopwood, R., De Zotti, G., et al. 2010, Science, 330, 800 (ref: negr14) Negrello, M., Hopwood, R., Dye, S., et al. 2014, MNRAS, 440, 1999 (ref: ogur10) Oguri, M. 2010, PASJ, 62, 1017 (ref: peng02) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002, AJ, 124, 266 (ref: rawl14) Rawle, T. D., Egami, E., Bussmann, R. S., et al. 2014, ApJ, 783, 59 (ref: ryba15) Rybak, M., McKean, J. P., Vegetti, S., Andreani, P., & White, S. D. M. 2015, arXiv:1503.02025 (ref: schm59) Schmidt, M. 1959, ApJ, 129, 243 (ref: serj12) Serjeant, S. 2012, MNRAS, 424, 2429 (ref: shar13) Sharon, C. E., Baker, A. J., Harris, A. I., & Thomson, A. P. 2013, ApJ, 765, 6 (ref: smai97) Smail, I., Ivison, R. J. & Blain, A. W. 1997, ApJ, 490, 5& Keel, W. C. 2004, ApJ, 617, 64 (ref: smai02) Smail, I., Ivison, R. J., Blain, A. W., & Kneib, J.-P. 2002, MNRAS, 331, 495 (ref: solo05) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677 (ref: swin10) Swinbank, A. M., Smail, I., Longmore, S., et al. 2010, Nature, 464, 733 (ref: syme13) Symeonidis, M., Vaccari, M., Berta, S., et al. 2013, MNRAS, 431, 2317 (ref: tacc06) Tacconi, L. J., et al. 2006, ApJ, 640, 228 (ref: tacc08) Tacconi, L. J., Genzel, R., Smail, I., et al. 2008, ApJ, 680, 246 (ref: tamu15) Tamura, Y., et al. 2015, PASJ, in press (arXiv:1503.07605) (ref: thom15) Thomson, A. P., Ivison, R. J., Owen, F. N., et al. 2015, MNRAS, 448, 1874 (ref: viei13) Vieira, J. D., Marrone, D. P., Chapman, S. C., et al. 2013, Nature, 495, 344 (ref: will94) Williams, J. P., de Geus, E. J., & Blitz, L. 1994, ApJ, 428, 693 (ref: whit14) Whitmore, B. C., et al., 2014, ApJ, 795, 156

</paper>

## Items to check

```json
[
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Two Sersic profile model fitting approach for foreground lens galaxy subtraction",
  "failed_quote": "According to (cite: negr14), two Sersic profiles were simultaneously fitted to the foreground lens galaxy to cleanly subtract it."
 },
 {
  "path": "processing.inherited[3].what.evidence[0]",
  "value": "Standard ULIRG CO-to-H2 conversion factor alpha_CO = 0.8 M_sun (K km s^-1 pc^2)^-1",
  "failed_quote": "We adopted a conversion factor of alpha_CO = 0.8 M_sun (K km s^-1 pc^2)^-1, the standard value for ULIRGs (cite: down98)."
 },
 {
  "path": "processing.inherited[4].what.evidence[0]",
  "value": "Dust mass absorption coefficient kappa_d(125 um) = 2.64 m^2 kg^-1",
  "failed_quote": "adopt kappa_d(125 \\mu m) = 2.64 \\pm 0.29 m^2 kg^-1 (cite: dunn03) and \beta = 1.5."
 },
 {
  "path": "processing.inherited[5].what.evidence[0]",
  "value": "SFR conversion factor SFR = 1.72 x 10^-10 L_FIR",
  "failed_quote": "The SFR was derived from SFR = 1.72 x 10^-10 L_FIR (cite: kenn98a)."
 },
 {
  "path": "analysis_steps[0].assumptions[0].evidence[0]",
  "value": "Foreground lens galaxy light profile is well described by two Sersic components",
  "failed_quote": "According to (cite: negr14), two Sersic profiles were simultaneously fitted to the foreground lens galaxy to cleanly subtract it."
 },
 {
  "path": "analysis_steps[0].fitting.evidence[0]",
  "value": "Simultaneous two-component Sersic fitting in galfit",
  "failed_quote": "two Sersic profiles were simultaneously fitted to the foreground lens galaxy to cleanly subtract it."
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Identify peaks >=3.5 sigma in CO(5-4) velocity-integrated map (created with >1.5 sigma line cube pixels) and run clumpfind on the 21 km s^-1 line cube, retaining 14 clumps detected by both methods",
  "failed_quote": "We first searched for the peak positions with >=3.5sigma in the velocity-integrated intensity map created by including pixels above 1.5sigma in the line cube. We then used the clumpfind package (cite: will94) to search for clumps in the line cube. We identified 14 molecular clumps along the arcs detected by both methods"
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "3.5 sigma integrated map threshold, 1.5 sigma line cube threshold, 21 km s^-1 spectral resolution",
  "failed_quote": "using the line cube (spectral resolution of 21 km s^-1) and the velocity-integrated intensity map of CO(5-4). We first searched for the peak positions with >=3.5sigma in the velocity-integrated intensity map created by including pixels above 1.5sigma in the line cube."
 },
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "Clumps along the arcs identified by both integrated map peaks and 3D clumpfind represent physical or magnified clump structures",
  "failed_quote": "We identified 14 molecular clumps along the arcs detected by both methods (Figure [fig:image]a)."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Perform photometry in regions >2 sigma in CO(5-4) moment-0 map on both CO and 1.0 mm continuum; compute CO luminosity, molecular gas mass, FIR luminosity, dust mass, SFR, and corresponding surface densities",
  "failed_quote": "We used regions above 2sigma in the CO(5-4) velocity-integrated map for conducting photometry and estimating the physical quantities of each clump. The photometry of dust continuum was conducted on the 1.0 mm image in the same regions used for the CO photometry."
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "SFR surface density range of clumps = 100-300 M_sun yr^-1 kpc^-2",
  "failed_quote": "The SFR density ranges between 100-300 M_sun yr^-1 kpc^-2, which is lower than the Eddington-limited star formation"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Gas depletion time scale = 100 Myr",
  "failed_quote": "The clumps of SDP.81 are located in the 'burst' sequence (cite: dadd10) with a gas depletion time scale of ~100 Myr, suggesting active star-forming activity in the clumps."
 },
 {
  "path": "findings_qualitative[0].evidence[0]",
  "value": "Molecular gas surface density and SFR surface density in SDP.81 clumps are more than three orders of magnitude higher than in local spirals and follow the starburst sequence.",
  "failed_quote": "The surface density of molecular gas (Sigma_H2) and star-formation rate (Sigma_SFR) of the clumps are more than three orders of magnitude higher than those found in local spiral galaxies. The clumps are placed in the 'burst' sequence in the Sigma_H2-Sigma_SFR plane"
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "The star-formation law derived for local starburst galaxies is applicable to molecular clumps at z ~ 3",
  "failed_quote": "Regardless of the exact location of these clumps in the Sigma_H2-Sigma_SFR plane, the derived Sigma_SFR/Sigma_H2 ratios are consistent with the values found in the Milky Way clumps (e.g., (cite: heid10; evan14)), suggesting that the star-formation law can be applied to molecular clumps at z ~ 3."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "SDP.81 exhibits a spatial decoupling between dust/gas star-forming clumps and extended stellar light, consistent with either a heavily dust-obscured rotating disk center or a galaxy merger with tidal features",
  "failed_quote": "One possible scenario is that the components of molecular gas, dust, and stars are distributed in a several-kpc scale rotating disk, and the stellar emission is heavily obscured by dust in the central star-forming region. Alternatively, SDP.81 may be a merging system"
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Galactic alpha_CO = 4.3 was considered, which would place clumps on the normal star-forming galaxy sequence instead of the burst sequence",
  "failed_quote": "If we adopt the Galactic conversion factor (alpha_CO = 4.3 M_sun (K km s^-1 pc^2)^-1; (cite: bola13)), these clumps are located on the sequence of normal star-forming galaxies."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[1].evidence[0]",
  "value": "Rotating disk scenario vs. galaxy merger scenario for explaining the velocity gradient and gas/stellar spatial offset",
  "failed_quote": "One possible scenario is that the components of molecular gas, dust, and stars are distributed in a several-kpc scale rotating disk, and the stellar emission is heavily obscured by dust in the central star-forming region. Alternatively, SDP.81 may be a merging system"
 }
]
```
