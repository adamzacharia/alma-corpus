# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2012A%26A...547L...3G\gemini38f\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# ALMA and VLA observations of recombination lines and continuum toward the Becklin-Neugebauer object in Orion

Compared to their centimeter-wavelength counterparts, millimeter recombination lines (RLs) are intrinsically brighter and are free of pressure broadening. We report observations of RLs (H$30\alpha$ at 231.9 GHz, H$53\alpha$ at 42.9 GHz) and the millimeter and centimeter continuum toward the Becklin-Neugebauer (BN) object in Orion, obtained from the Atacama Large Millimeter/submillimeter Array (ALMA) Science Verification archive and the Very Large Array (VLA). The RL emission appears to be arising from the slowly-moving, dense ($N_e=8.4\times10^6$ cm$^{-3}$) base of the ionized envelope around BN. This ionized gas has a relatively low electron temperature ($T_e<4900$ K) and small ($<<10$ km s$^{-1}$) bulk motions. Comparing our continuum measurements with previous (non)detections, it is possible that BN has large flux variations in the millimeter. However, dedicated observations with a uniform setup are needed to confirm this. From the H$30\alpha$ line, the central line-of-sight LSR velocity of BN is 26.3 km s$^{-1}$.

# Introduction

Understanding the nature of the radio sources in the Orion BN/KL region is important because these sources exhibit significant diverging proper motions that may trace the recent ($\sim 500$ yr ago) disintegration of a compact cluster of young massive stars (cite: rodriguez05; gomez08; goddi11b). This past interaction may also have caused the explosive outflow seen in vibrationally-excited H$_2$ and CO lines (cite: zapata09; bally11; nissen12).

In particular, observing hydrogen recombination lines (RLs) can be used to obtain the line-of-sight velocities of the radio sources, which are needed to complement the proper-motion information. Millimeter (mm) RLs are in principle better suited to giving the central velocity of the system because they are more optically thin, much less pressure broadened, and intrinsically brighter than centimeter (cm) lines (cite: gs02; peters12). However, longer wavelength lines are a valuable complement because they are sensitive to the gas density. By observing multiple RL transitions, hints to the structure of the ionized nebula can be obtained even in unresolved observations (cite: kzk08; gm09).

In this paper we report our findings in the recently released Science Verification (SV) data taken toward Orion BN/KL with the Atacama Large Millimeter/submillimeter Array (ALMA). We also report on previous RL observations obtained with the Very Large Array (VLA), as well as on the continuum obtained with both interferometers.

# Data

Orion BN/KL was observed on January 19, 2012 with ALMA as part of the SV program. In this paper we make use of the fully calibrated visibilities released on April 12, 2012. The data consisted of 20 different spectral windows covering the frequency range from 213.72 GHz to 246.62 GHz. Each spectral window had a uniform spectral resolution of 0.488 MHz ($\sim0.6$ km s$^{-1}$) and was observed for an on-source time of $\sim 15$ minutes. The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 k$\lambda$ to 269 k$\lambda$. The pointing center was $\alpha_\mathrm{J2000}=05^\mathrm{h}~35^\mathrm{m}~14\rlap.{^\mathrm{s}}35$, $\delta_\mathrm{J2000}=-05^\circ~22'~35\rlap.{''}0$.

The absolute amplitude scale was derived from observations of Callisto and Mars. The phase calibrator was J0607–085. We imaged the phase calibrator and measured a flux density of $S=1.40$ Jy. The SMA data base[^1] reports flux densities for J0607–085 within ten days of the ALMA observation: $S_\mathrm{09Jan2012}=1.25\pm0.06$ Jy, $S_\mathrm{27Jan2012}=1.37\pm0.07$ Jy. From this, we estimate that the amplitude scale of the ALMA observations is accurate to $\sim 10~\%$. The processing was done in CASA versions 3.3.0 and 3.4.0.

We also present archival Very Large Array[^2] (VLA) data. The H$53\alpha$ ($\nu_0=42.95197$ GHz) B-array observations have been previously presented by (cite: rodriguez09b) (project AR635).

Finally, several epochs of continuum observations at 8.4 GHz in the A configuration were processed using standard methods in the AIPS software. In all epochs 1331+305 was used as amplitude calibrator with an adopted flux density of 5.21 Jy. The epochs, project codes, phase calibrators, and their bootstrapped flux densities are given in Table [1](#t1).

|             |         |            |                   |
|:-----------:|:-------:|:----------:|:-----------------:|
|    Epoch    | Project |   Phase    | Bootstrapped flux |
|             |         | calibrator |  density \[Jy\]   |
| 06 Sep 1991 |  AM335  |  0530+135  |   $1.77\pm0.04$   |
| 29 Apr 1994 |  AM442  |  0501–019  |   $2.38\pm0.01$   |
| 22 Jul 1995 |  AM494  |  0541–056  |   $1.97\pm0.14$   |
| 21 Nov 1996 |  AM543  |  0501–019  |   $1.51\pm0.01$   |
| 11 Jan 1997 |  AM543  |  0501–019  |   $1.45\pm0.01$   |
| 13 Nov 2000 |  AM668  |  0541–056  |   $1.11\pm0.01$   |
| 12 May 2006 |  AR593  |  0541–056  |   $1.39\pm0.01$   |

: VLA calibrators at 8.4 GHz

# Results

Continuum subtraction was done in the u-v domain by carefully selecting the line-free channels in each spectral window and fitting a linear spectral baseline. Continuum images from different spectral windows are consistent with each other, indicating a low contamination from unaccounted line emission.

All the spectral windows were imaged with a threefold purpose: to detect the H$30\alpha$ RL in the BN/KL radio sources (I, BN, and n), to detect molecular emission from BN, and to make a continuum image. Whereas we succeeded in detecting the RL in BN, it was not detected elsewhere. Also, no molecular emission was detected from BN. We present maps that have not been corrected for primary beam attenuation. The corrected fluxes are quoted in the text and tables.

## Continuum.

The low declination of Orion BN/KL, as well as the bright, extended emission dominated by the “hot core” (HC), limit the dynamic range of synthesis imaging and complicate the detection of weak sources in this field at (sub)mm wavelengths. Figure [1](#f1_continuum) shows a deep continuum image from the ALMA data obtained by co-adding the line-free continuum visibilities from all spectral windows. The average frequency (wavelength) in this map is 230.17 GHz (1.30 mm). The dynamic range in this image is determined by limitations in the u-v coverage, and it is in the range of $\sim 10$ to 15 mJy. Our continuum map is $\sim\times 2$ deeper than the released continuum image[^3], and similar in quality to the CARMA 1.3-mm map reported by (cite: fs08).

The centimeter radio source I (cite: reid07; goddi11b) is only $\sim 0\rlap.{''}7$ from the 1.3-mm peak of the HC, which has an extension of $\sim 8\rlap.{''}6 \times 3\rlap.{''}2$ (see Fig. [1](#f1_continuum)). Therefore, the continuum emission of source I cannot be resolved from the HC in arcsecond-resolution images (cite: beuther05; goddi11a). The BN object, as traced by its cm continuum, is $\sim 6\rlap.{''}7$ from the hot-core continuum peak. In the map shown in Fig. [1](#f1_continuum) we detect BN with a peak intensity of 55 mJy beam$^{-1}$ (112 mJy beam$^{-1}$ when primary beam attenuation is taken into account). However, it is still at the intensity level of some of the extended emission.

![](f1.eps)

To disentangle the compact continuum emission from the extended emission in the field, we made cleaned maps after removing the short baselines. This degradation of the u-v coverage produces artifacts (closely-spaced sidelobes) close to source I and the HC, and we refrained from using this part of the image. However, at the position of BN, where emission is fainter, the restricted u-v coverage effectively removes the extended emission around BN. We found that a minimum baseline length of $\approx 100$ k$\lambda$ gives optimal results, filtering out the emission on scales $>1\rlap.{''}4$. Figure [2](#f2_continuum) shows this continuum map around BN. The noise is $\times 5$ lower than in Fig. 1 ($\sim 3$ mJy). The 1.3-mm flux density of BN in this image is 62 mJy. After primary beam correction, the flux density of BN is $S_\mathrm{1.3mm}=126$ mJy.

We note that the flux density for BN is the same, within $20~\%$, regardless of the u-v coverage restriction applied. A faint compact source with primary beam corrected flux $S_\mathrm{1.3mm}=26$ mJy is also detected $4\rlap.{''}3$ south of BN. This newly detected source is possibly associated with the extended mid-infrared sources IRc6 and IRc6 N (cite: shuping04).

![](f2.eps)

It is possible that BN is variable in the (sub)mm continuum. While our detection of BN is consistent with the 218 GHz flux of $S=150\pm50$ mJy (from OVRO observations in 1993 and 1994) reported by (cite: plambeck95) and (cite: blake96), (cite: fs08) do not detect BN at 231 GHz down to a $3\sigma$ level of $\sim 34$ mJy (CARMA observations in 2007). However, the significance of these variations can be affected by the inhomogeneity of the mm observations. We have reprocessed three epochs of VLA archival data at 3.6 cm (8.4 GHz) to look for possible variations in the continuum emission from BN. Table [2](#t2) lists the measured 3.6-cm fluxes, together with the four epochs reported by (cite: zapata04), also at 3.6 cm, and the available 1-mm band measurements. Based on this data set, the 3.6-cm flux is quite stable (within $30~\%$ of the maximum value).

| Epoch | S$_\mathrm{3.6cm}$ \[mJy\] | S$_\mathrm{1.3mm}$ \[mJy\] | Notes |
|:--:|:--:|:--:|:--:|
| 06 Sep 1991 | $4.61\pm0.20$ | – | a |
| Nov 1993 to Feb 1994 | – | $150\pm50$ | b |
| 29 Apr 1994 | $3.73\pm0.04$ | – | c |
| 22 Jul 1995 | $3.36\pm0.3$ | – | c |
| 21 Nov 1996 | $3.43\pm0.1$ | – | c |
| 11 Jan 1997 | $3.90\pm0.07$ | – | c |
| 13 Nov 2000 | $3.83\pm0.14$ | – | a |
| 12 May 2006 | $4.78\pm0.11$ | – | a |
| Mar 2007 | – | $<34$ | d |
| 19 Jan 2012 | – | $126\pm14$ | e |

: BN fluxes.

Table notes: a: VLA-A archival data, HPBW$\approx0\rlap.{''}3$ (this paper). b: OVRO observations at 218 GHz, HPBW$=1\rlap.{''}5 \times 1\rlap.{''}0$ (cite: plambeck95; blake96). c: VLA-A, HPBW$\approx0\rlap.{''}3$ (cite: zapata04). d: CARMA observations at 231 GHz, HPBW$=2\rlap.{''}5 \times 0\rlap.{''}8$ (cite: fs08). e: ALMA SV data, HPBW$=1\rlap.{''}3 \times 0\rlap.{''}6$ (this paper). The error is determined by variations in the obtained flux with different apertures in the $B_\mathrm{min}=100$ k$\lambda$ map. The flux density has been corrected for primary beam attenuation.

## Recombination lines

We report the first detection of mm RL emission toward the BN object. We also searched for H$30\alpha$ emission in the rest of the Orion BN/KL field, in particular from sources I and n, without success. Just as with the continuum, the proximity of source I to the HC contaminates any emission from the relatively faint RL with brighter, more extended molecular lines with rest frequencies within a few MHz of the H$30\alpha$ line. Figure 3 shows the H30$\alpha$ and the H53$\alpha$ (cite: rodriguez09b) spectra toward BN. The line parameters are summarized in Table [3](#t3). Figure 4 shows the velocity-integrated intensity maps (moment 0) for both lines. Similar to the mm continuum, the H30$\alpha$ map uses only baselines with length $> 100$ k$\lambda$[^4].

![](f3.eps)

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Transition | $\nu_\mathrm{rest}$ | $S_\mathrm{peak}$ | $v_\mathrm{LSR,peak}$ | FWHM |
|  | \[GHz\] | \[mJy\] | \[km s$^{-1}$\] | \[km s$^{-1}$\] |
| H$30\alpha$ | 231.9009 | $181\pm14$ | $26.3\pm0.5$ | $15.4\pm1.3$ |
| H$53\alpha$ | 42.95197 | $9.9\pm1.1$ | $19.8\pm2.1$ | $39.0\pm5.0$ |

: Recombination line parameters.

Table notes: From Gaussian fits to the spectra shown in Fig. 3 using an aperture adjusted to the emitting area shown in Fig. 4.

The H$30\alpha$ line is narrower than the H$53\alpha$ line, and it is redshifted by a few km s$^{-1}$. This behavior has been observed in hypercompact HII regions around embedded young massive stars (cite: kzk08; gm09). Although BN is not deeply embedded in molecular gas, the same interpretation seems to apply: that the difference in linewidth is caused by the action of “pressure” broadening from particle collisions in the low-frequency line, whereas the velocity differences are caused by optical depth effects. In an outflowing gas where the denser part is closer to the central star, the optically thinner, higher frequency line will trace the centermost gas from both the front and the back sides of the nebula. In contrast, the optically thicker, lower frequency line, will trace gas farther away from the central star, mainly from the front (blueshifted) side of the nebula (cite: kzk08). Therefore, the H$30\alpha$ line should give a better estimation of the line-of-sight velocity of the star inside the BN nebula, $v_\mathrm{LSR}\mathrm{(BN)}=26.3\pm0.5$ km s$^{-1}$.

![](f4.eps)

The total RL width ($\Delta v$) has contributions from thermal broadening ($\Delta v_\mathrm{th}$), dynamical broadening from macroscopic gas motions ($\Delta v_\mathrm{dy}$), and pressure broadening ($\Delta v_\mathrm{pr}$). We elaborate this aspect in Appendix A. The line FWHM of the combined profile is given by (cite: gm09):

$$\begin{equation}
\Delta v \approx  0.534\Delta v_\mathrm{pr} +(\Delta v_\mathrm{dy}^2 + 
\Delta v_\mathrm{th}^2 + 0.217\Delta v_\mathrm{pr}^2)^{1/2}. 
\end{equation}$$

The H30$\alpha$ line is only broadened thermally and by dynamical motions ($\Delta v_\mathrm{pr}<0.6$ km s$^{-1}$ from equation A.4). Also, in the BN object this line appears to be too narrow (15.4 km s$^{-1}$) even for pure thermal broadening at $T_e=10^4$ K (equation A.2). Therefore, for the gas traced by the H30$\alpha$ line, $T_e$ is at most 4900 K, and the bulk gas motions are constrained to be much smaller than the thermal width. Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is $N_e=8.4\times10^6$ cm$^{-3}$.

Non-LTE effects and dust opacity may play a role for (sub)mm RLs. In Appendix B we show that the RLs in BN are reasonably close to LTE and that it is possible that dust in the line-of-sight makes a considerable contribution to the 1.3-mm continuum.

# Discussion

One possible explanation for the differences in the mm fluxes that have been reported for BN is that they are, at least partially, caused by systematic errors in the measurements. All the compiled cm fluxes are measured with the VLA A-array, which has an absolute flux-scale uncertainty of a few percent, while the flux scale of mm interferometers is known to be only accurate to within $\sim 10~\%$[^5]. Differences in u-v coverage may also mimic flux variations, but since the continuum emission from BN is less than one arcsecond in size, this effect should not be important. Indeed, the flux that we recover from BN is the same within $\sim 20~\%$ for different u-v restrictions, (see Section 3.1). Alternatively, if BN is variable in the mm, it could be caused by the sudden recombination of dense gas (cite: osterbrock89). We emphasize that only dedicated multiepoch observations with a uniform setup can clarify this issue.

The BN object is known to be a young star with a mass $M_\star \approx 10~M_\odot$ (cite: rodriguez05). In the absence of other forces (e.g., wind acceleration mechanisms), this mass is enough to gravitationally confine ionized hydrogen within a radius of $\approx 55$ AU (cite: keto07). If the H30$\alpha$ is emitted within a volume as small as the radio continuum (cite: rodriguez09b), this could explain the lack of bulk motions in this RL. The H53$\alpha$ line appears to be tracing gas that is outflowing toward us with a velocity $\sim 6.5$ km s$^{-1}$ blueshifted with respect to the systemic. Infrared and optical RLs have also been detected toward BN and extend to velocities $>100$ km s$^{-1}$ (cite: scoville83). However, these RLs are significantly affected by obscuration and non-LTE effects, so they may trace gas from a different volume than the radio and (sub)mm RLs.

# Conclusions

We report the first detection of 1.3 mm RL (H30$\alpha$) emission toward Orion from the BN object. The mm RL appears to be arising from the dense ($N_e=8.4\times10^6$ cm$^{-3}$), static (bulk motions $<<10$ km s$^{-1}$) base of the ionized nebula around the central massive star in BN, whose line-of-sight LSR velocity is now estimated to be $v_\mathrm{LSR}\mathrm{(BN)}=26.3\pm0.5$ km s$^{-1}$. Compared to the H$30\alpha$ line, the optically thicker H$53\alpha$ seems to trace gas outflowing toward us at $\sim 6.5$ km s$^{-1}$.

Dedicated ALMA observations at subarcsecond resolution would be able to detect RL emission from the rest of the Orion BN/KL sources, to obtain their 3D velocities by combining them with the available proper motion measurements, and to quantify their possible flux variations.

# Acknowledgements

R.G.-M. and C.G. acknowledge funding from the European Community’s Seventh Framework Programme (/FP7/2007-2013/) under grant agreement No. 229517R. L.F.R. acknowledges the support of DGAPA, UNAM, and CONACyT (Mexico). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00009.SV. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The authors are grateful to the ALMA staff for doing the observations and calibrating the data. The referee, Dr. T. L. Wilson, and the editor, Dr. M. Walmsley, provided prompt and useful comments to this manuscript. The authors also thank Dr. Richard Plambeck for providing corrections.

26 natexlab

(ref: bally11) Bally, J., Cunningham, N. J., Moeckel, N., et al. 2011, ApJ, 727, 113

(ref: beuther05) Beuther, H., Zhang, Q., Greenhill, L. J., et al. 2005, ApJ, 632, 355

(ref: blake96) Blake, G. A., Mundy, L. G., Carlstrom, J. E., et al. 1996, ApJL, 472, L49

(ref: fs08) Friedel, D. N. & Snyder, L. E. 2008, ApJ, 672, 962

(ref: gm09) Galván-Madrid, R., Keto, E., Zhang, Q., et al. 2009, ApJ, 706, 1036

(ref: goddi11a) Goddi, C., Greenhill, L. J., Humphreys, E. M. L., Chandler, C. J., & Matthews, L. D. 2011a, ApJL, 739, L13

(ref: goddi11b) Goddi, C., Humphreys, E. M. L., Greenhill, L. J., Chandler, C. J., & Matthews, L. D. 2011b, ApJ, 728, 15

(ref: gomez08) Gómez, L., Rodrı́guez, L. F., Loinard, L., et al. 2008, ApJ, 685, 333

(ref: gs02) Gordon, M. A. & Sorochenko, R. L., eds. 2002, Astrophysics and Space Science Library, Vol. 282, Radio Recombination Lines. Their Physics and Astronomical Applications

(ref: js11) Jiménez-Serra, I., Martı́n-Pintado, J., Báez-Rubio, A., Patel, N., & Thum, C. 2011, ApJL, 732, L27

(ref: keto07) Keto, E. 2007, ApJ, 666, 976

(ref: kzk08) Keto, E., Zhang, Q., & Kurtz, S. 2008, ApJ, 672, 423

(ref: nissen12) Nissen, H. D., Cunningham, N. J., Gustafsson, M., et al. 2012, A&A, 540, A119

(ref: osterbrock89) Osterbrock, D. E. 1989, Astrophysics of gaseous nebulae and active galactic nuclei

(ref: peters12) Peters, T., Longmore, S. N., & Dullemond, C. P. 2012, MNRAS, 425, 2352

(ref: plambeck95) Plambeck, R. L., Wright, M. C. H., Mundy, L. G., & Looney, L. W. 1995, ApJL, 455, L189

(ref: reid07) Reid, M. J., Menten, K. M., Greenhill, L. J., & Chandler, C. J. 2007, ApJ, 664, 950

(ref: rodriguez05) Rodrı́guez, L. F., Poveda, A., Lizano, S., & Allen, C. 2005, ApJL, 627, L65

(ref: rodriguez09b) Rodrı́guez, L. F., Zapata, L. A., & Ho, P. T. P. 2009, ApJ, 692, 162

(ref: scoville83) Scoville, N., Kleinmann, S. G., Hall, D. N. B., & Ridgway, S. T. 1983, ApJ, 275, 201

(ref: shuping04) Shuping, R. Y., Morris, M., & Bally, J. 2004, AJ, 128, 363

(ref: smirnov84) Smirnov, G. T., Sorochenko, R. L., & Pankonin, V. 1984, A&A, 135, 116

(ref: walmsley90) Walmsley, C. M. 1990, A&AS, 82, 201

(ref: toolsofradio) Wilson, T. L., Rohlfs, K., & Hüttemeister, S. 2009, Tools of Radio Astronomy (Springer-Verlag)

(ref: zapata04) Zapata, L. A., Rodrı́guez, L. F., Kurtz, S. E., & O’Dell, C. R. 2004, AJ, 127, 2252

(ref: zapata09) Zapata, L. A., Schmid-Burgk, J., Ho, P. T. P., Rodrı́guez, L. F., & Menten, K. M. 2009, ApJL, 704, L45

# Linewidth of recombination lines

RLs are broadened by several mechanisms: a natural broadening from the quantum uncertainty $\Delta E$ of the energy level $E$, a thermal/microturbulence Gaussian broadening from the motions of the emitting particles and of parcels of gas that are much smaller than the beam, the Stark (or “pressure”) broadening from the perturbation of the atomic energy levels by the electric field of neighboring charged particles, and a dynamical broadening from bulk flows (e.g., infall, rotation, outflow) in the gas. A detailed discussion of these processes and the physics of RLs can be found in (cite: gs02).

For $n > 20$ (where H$n\alpha$ is a $n+1 \rightarrow n$ transition), the natural linewidth in velocity units is

$$\begin{equation}
\Delta v_\mathrm{N} \approx 1.2 \times 10^{-6} c \frac{\ln (n+1)}{(n+1)^2}, 
\end{equation}$$

where $c$ is the speed of light. For H30$\alpha$ and H53$\alpha$, $\Delta v_\mathrm{N}$ is $1.3 \times 10^{-3}$ km s$^{-1}$ and $0.5 \times 10^{-3}$ km s$^{-1}$, respectively. The natural broadening is negligible for radio and (sub)mm RLs.

The thermal distributions of velocities of both the individual particles and small pockets of gas (“microturbulence”) produce a Gaussian contribution to the broadening. Neglecting microturbulence, the thermal FWHM is

$$\begin{equation}
\Delta v_\mathrm{th} = \biggl ( 8 \ln 2 \frac{k_\mathrm{B} T_e}{m_\mathrm{H}} \biggr )^{1/2},  
\end{equation}$$

where $k_\mathrm{B}$ is the Boltzmann constant, $m_\mathrm{H}$ is the hydrogen-atom mass, and it is assumed that all the gas is thermalized to the electron temperature $T_e$. For a pure-hydrogen gas with $T_e=9000$ K, $\Delta v_\mathrm{th}=20.3$ km s$^{-1}$.

The pressure broadening has a Lorentzian shape, and it increases with density and quantum number. Collisions with ions and electrons make different contributions. The contribution from ions has the form (cite: gs02)

$$\begin{equation}
\Delta v_\mathrm{pr,i} \approx \biggl ( N_i \frac{c}{\nu_0}  \biggr ) 
(0.06 + 2.5\times10^{-4}T_e) \biggl ( \frac{n+1}{100} \biggr )^{\gamma_i} 
\biggl ( 1 + \frac{2.8 \Delta n}{n+1} \biggr ), 
\end{equation}$$

where $\gamma_i = 6-2.7\times10^{-5} T_e -0.13(n+1)/100$. For $T_e=9000$ K and $N_i=10^7$ cm$^{-3}$, the H$30\alpha$ line is virtually free from ion broadening (0.04 km s$^{-1}$, and decreases close to linearly with decreasing $T_e$), whereas the H$53\alpha$ line is broadened by 5.1 km s$^{-1}$.

The collisions with electrons dominate the collisions with ions under most conditions. They produce a broadening of width (cite: smirnov84):

$$\begin{equation}
\Delta v_\mathrm{pr,e} \approx \biggl ( 8.2N_e \frac{c}{\nu_0}  \biggr ) 
 \biggl ( \frac{n+1}{100} \biggr )^{4.5} 
\biggl ( 1 + \frac{2.25 \Delta n}{n+1} \biggr ).  
\end{equation}$$

For $N_e=10^7$ cm$^{-3}$, the electron broadenings for the H53$\alpha$ and H$30\alpha$ are $\approx 37.3$ km s$^{-1}$ and 0.6 km s$^{-1}$, respectively.

Finally, the last source of broadening is bulk motions ($\Delta v_\mathrm{dy}$) of the ionized gas, which may be in the form of outflows/winds, infall/accretion, and/or rotation. For unresolved observations, the method outlined here permits estimating the magnitude of these motions from the nonthermal linewidth of the line that is free of pressure broadening. Of course, ideally one wishes to spatially resolve these motions. ALMA in its Cycle 1 is now able to resolve the ionized-gas motions in sources as faint as $\sim 10$ mJy at the line peak at subarcsecond resolution.

Including all the contributions to the broadening, the total linewidth will have a Voigt profile with FWHM given by equation (1) in the text.

# cm and (sub)mm recombination lines

Here we discuss the advantages and limitations that cm and (sub)mm RLs have compared to each other. The cm lines are intrinsically fainter and optically thicker, and can be partially absorbed by the relatively high continuum opacity at their wavelengths (cite: toolsofradio). A possible drawback of (sub)mm RLs is that the free-free continuum may be contaminated by dust emission. Another problem is that they are out of LTE more easily than cm lines, so their interpretation may require careful modeling (cite: js11; peters12). As shown below, our simple LTE interpretation seems to be reasonable, but it is possible that a significant fraction of the 1.3-mm continuum comes from dust in the line of sight.

Let $b_n$ be the ratio of the population of level $n$ to its LTE population. Then the actual line absorption coefficient $\kappa_\mathrm{L}$ is related to the LTE coefficient $\kappa_\mathrm{L,LTE}$ by (cite: gs02)

$$\begin{equation}
\kappa_\mathrm{L} = \kappa_\mathrm{L,LTE} b_n \beta_n, 
\end{equation}$$

with

$$\begin{equation}
\beta_n\approx \frac{b_{n+1}}{b_n} \biggl ( 1-\frac{k_\mathrm{B}T_e}{h\nu} \frac{d \ln b_{n+1}}{dn} 
\Delta n \biggr). 
\end{equation}$$

While $0<b_n<1$ expresses the non-LTE level depopulation, $\beta_n$ can be negative when there are conditions for maser amplification.

In the optically-thin case ($\tau_\mathrm{C,1.3mm}\sim0.08$ from the data), the non-LTE corrected line intensity $I_\mathrm{L}$ is (cite: gs02)

$$\begin{equation}
I_\mathrm{L} \approx I_\mathrm{L,LTE}b_{n+1}(1-\tau_\mathrm{C}\beta/2). 
\end{equation}$$

Using the tabulated values in the calculations of (cite: walmsley90), $b_{30}\approx 0.98$ and $\beta_{30} \sim -1.5$ for a density $N_e=10^7$ cm$^{-3}$. Therefore, the intensity of the H$30\alpha$ line is only amplified by $\sim 3~\%$. The H$53\alpha$ is even closer to LTE, with $b_{53}\approx 0.999$ and $\beta_{53} \sim 0.5$.

Sub(mm) RLs are more opticaly thin and intrinsically brighter than cm RLs. For a given $T_e$ and $N_e$, and in the Rayleigh-Jeans regime ($h\nu << k_\mathrm{B} T_e$), the line absorption coefficient decreases linearly with frequency $\kappa_\mathrm{L} \propto \nu^{-1}$, so the LTE line emission coefficient $j_\mathrm{L}=\kappa_\mathrm{L}B_\nu(T_e) \propto \nu$. Similarly, the continuum absorption coefficient $\kappa_\mathrm{C} \propto \nu^{-2.1}$, so the LTE continuum emissivity $j_\mathrm{C} \propto \nu^{-0.1}$. Therefore, in the optically thin regime, the line-to-continuum ratio increases almost linearly with frequency $S_\mathrm{L} \Delta v /S_\mathrm{C} \propto \nu^{1.1}$. Under these assumptions, the expected ratio of the H30$\alpha$ to H$53\alpha$ line-to-continuum ratios is 6.4. However, the observed value is 1.6. If we assume that only $\sim 32$ mJy of the 1.3-mm continuum are due to free-free then the line-to-continuum ratio would increase to the expected value. This suggests that dust contributes a significant fraction to the (sub)mm continuum of BN. However, it is known (and we have confirmed this with the ALMA data set) that BN is not embedded in dense molecular gas. Therefore, it is unlikely that this line-of-sight dust arises in a dense core around BN.

[^1]: http://sma1.sma.hawaii.edu/callist/callist.html/

[^2]: The National Radio Astronomy Observatory is operated by Associated Universities, Inc. under cooperative agreement with the National Science Foundation.

[^3]: http://almascience.eso.org/alma-data/science-verification

[^4]: The H30$\alpha$ line is also detected in maps that use the complete baseline range, but bright molecular emission from the HC centered at $\sim 10$ MHz blueshifted with respect to the RL creates sidelobes that are for the most part removed by taking only the longest baselines.

[^5]: http://www.vla.nrao.edu/astro/calib/manual/, http://haneul.astro.illinois.edu/$\sim$wkwon/CARMA/fluxcal/

</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].coordinates.evidence[0]",
  "value": "05h 35m 14.35s, -05d 22' 35.0\"",
  "failed_quote": "The pointing center was alpha_J2000=05h 35m 14.35s, delta_J2000=-05d 22m 35.0s."
 },
 {
  "path": "science.targets[1].coordinates.evidence[0]",
  "value": "~6.7\" from the hot-core continuum peak",
  "failed_quote": "The BN object, as traced by its cm continuum, is ~6.7\" from the hot-core continuum peak."
 },
 {
  "path": "science.question.evidence[0]",
  "value": "What are the line-of-sight velocity, physical conditions, and continuum properties of the ionized gas around the Becklin-Neugebauer (BN) object in Orion using millimeter recombination lines and continuum?",
  "failed_quote": "We report observations of RLs (H30alpha at 231.9 GHz, H53alpha at 42.9 GHz) and the millimeter and centimeter continuum toward the Becklin-Neugebauer (BN) object in Orion"
 },
 {
  "path": "data.lines_targeted[0].evidence[0]",
  "value": "H",
  "failed_quote": "H30alpha | 231.9009"
 },
 {
  "path": "data.lines_targeted[1].evidence[0]",
  "value": "H",
  "failed_quote": "The H53alpha (nu_0=42.95197 GHz) B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)."
 },
 {
  "path": "data.arrays.evidence[0]",
  "value": "16 12-m antennas",
  "failed_quote": "The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 klambda to 269 klambda."
 },
 {
  "path": "data.configurations.evidence[0]",
  "value": "compact configuration",
  "failed_quote": "The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 klambda to 269 klambda."
 },
 {
  "path": "data.baselines.evidence[0]",
  "value": "15 klambda to 269 klambda",
  "failed_quote": "The array used 16 12-m antennas in a compact configuration with baselines in the range of 15 klambda to 269 klambda."
 },
 {
  "path": "data.angular_resolution.evidence[0]",
  "value": "1.3\" x 0.6\"",
  "failed_quote": "ALMA SV data, HPBW=1.3\" x 0.6\" (this paper)."
 },
 {
  "path": "data.max_recoverable_scale.evidence[0]",
  "value": "scales >1.4\" filtered out with B_min=100 klambda",
  "failed_quote": "We found that a minimum baseline length of approx 100 klambda gives optimal results, filtering out the emission on scales >1.4\"."
 },
 {
  "path": "data.sensitivity.evidence[1]",
  "value": "~10 to 15 mJy in full map; ~3 mJy with B_min = 100 klambda",
  "failed_quote": "The noise is x 5 lower than in Fig. 1 (~ 3 mJy)."
 },
 {
  "path": "data.other_facilities[0].provided.evidence[0]",
  "value": "Archival H53alpha B-array data (project AR635) and 8.4 GHz continuum A-array data across multiple epochs (1991, 2000, 2006)",
  "failed_quote": "We also present archival Very Large Array (VLA) data. The H53alpha (nu_0=42.95197 GHz) B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)."
 },
 {
  "path": "data.other_facilities[1].provided.evidence[0]",
  "value": "Calibrator database flux densities for J0607-085",
  "failed_quote": "The SMA data base reports flux densities for J0607–085 within ten days of the ALMA observation: S_09Jan2012=1.25+-0.06 Jy, S_27Jan2012=1.37+-0.07 Jy."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "VLA 8.4 GHz continuum flux measurements of BN from 1994 to 1997",
  "failed_quote": "VLA-A, HPBW~0.3\" (cite: zapata04)."
 },
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "OVRO 218 GHz continuum flux measurement from 1993-1994",
  "failed_quote": "OVRO observations at 218 GHz, HPBW=1.5\" x 1.0\" (cite: plambeck95; blake96)."
 },
 {
  "path": "data.external_data_from_literature[2].what.evidence[0]",
  "value": "CARMA 231 GHz continuum upper limit from March 2007",
  "failed_quote": "CARMA observations at 231 GHz, HPBW=2.5\" x 0.8\" (cite: fs08)."
 },
 {
  "path": "data.external_data_from_literature[3].what.evidence[0]",
  "value": "VLA H53alpha B-array data",
  "failed_quote": "The H53alpha (nu_0=42.95197 GHz) B-array observations have been previously presented by (cite: rodriguez09b) (project AR635)."
 },
 {
  "path": "processing.calibration.flux_scale_uncertainty.evidence[0]",
  "value": "~10 %",
  "failed_quote": "From this, we estimate that the amplitude scale of the ALMA observations is accurate to ~ 10 %."
 },
 {
  "path": "processing.imaging.final_beam.evidence[0]",
  "value": "1.3\" x 0.6\"",
  "failed_quote": "ALMA SV data, HPBW=1.3\" x 0.6\" (this paper)."
 },
 {
  "path": "processing.imaging.final_rms.evidence[0]",
  "value": "~3 mJy with B_min=100 klambda; ~10 to 15 mJy full map",
  "failed_quote": "The noise is x 5 lower than in Fig. 1 (~ 3 mJy)."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Formula for deriving average electron density from RLs",
  "failed_quote": "Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is N_e=8.4x10^6 cm^-3."
 },
 {
  "path": "analysis_steps[1].method.evidence[1]",
  "value": "Deconvolution with clean after filtering out short baselines (< 100 klambda)",
  "failed_quote": "We found that a minimum baseline length of approx 100 klambda gives optimal results, filtering out the emission on scales >1.4\"."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "B_min approx 100 klambda",
  "failed_quote": "We found that a minimum baseline length of approx 100 klambda gives optimal results, filtering out the emission on scales >1.4\"."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "baselines > 100 klambda used for H30alpha",
  "failed_quote": "Similar to the mm continuum, the H30alpha map uses only baselines with length > 100 klambda."
 },
 {
  "path": "analysis_steps[3].method.evidence[0]",
  "value": "Deconvolving thermal, dynamical, and pressure broadening contributions using analytic formulae",
  "failed_quote": "The H30alpha line is only broadened thermally and by dynamical motions (Delta v_pr<0.6 km s^-1 from equation A.4)."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Deconvolving thermal, dynamical, and pressure broadening contributions using analytic formulae",
  "failed_quote": "Therefore, for the gas traced by the H30alpha line, T_e is at most 4900 K, and the bulk gas motions are constrained to be much smaller than the thermal width. Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is N_e=8.4x10^6 cm^-3."
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "T_e <= 4900 K, N_e = 8.4 x 10^6 cm^-3",
  "failed_quote": "Therefore, for the gas traced by the H30alpha line, T_e is at most 4900 K, and the bulk gas motions are constrained to be much smaller than the thermal width. Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is N_e=8.4x10^6 cm^-3."
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "Non-LTE calculations showing H30alpha line is amplified by only ~3% and H53alpha is even closer to LTE",
  "failed_quote": "Therefore, the intensity of the H30alpha line is only amplified by ~ 3 %. The H53alpha is even closer to LTE, with b_53 approx 0.999 and beta_53 ~ 0.5."
 },
 {
  "path": "results_numeric[0].evidence[0]",
  "value": "ALMA 1.3-mm continuum flux density of BN (primary beam corrected) = 126 mJy",
  "failed_quote": "19 Jan 2012 | – | 126+-14 | e"
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "H30alpha peak flux density of BN = 181 mJy",
  "failed_quote": "H30alpha | 231.9009 | 181+-14 | 26.3+-0.5 | 15.4+-1.3"
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "H30alpha peak LSR velocity of BN = 26.3 km s^-1",
  "failed_quote": "H30alpha | 231.9009 | 181+-14 | 26.3+-0.5 | 15.4+-1.3"
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "H30alpha FWHM linewidth of BN = 15.4 km s^-1",
  "failed_quote": "H30alpha | 231.9009 | 181+-14 | 26.3+-0.5 | 15.4+-1.3"
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "H53alpha peak flux density of BN = 9.9 mJy",
  "failed_quote": "H53alpha | 42.95197 | 9.9+-1.1 | 19.8+-2.1 | 39.0+-5.0"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "H53alpha peak LSR velocity of BN = 19.8 km s^-1",
  "failed_quote": "H53alpha | 42.95197 | 9.9+-1.1 | 19.8+-2.1 | 39.0+-5.0"
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "H53alpha FWHM linewidth of BN = 39.0 km s^-1",
  "failed_quote": "H53alpha | 42.95197 | 9.9+-1.1 | 19.8+-2.1 | 39.0+-5.0"
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Derived electron density Ne = 8.4x10^6 cm^-3",
  "failed_quote": "Finally, using equation 3 of (cite: kzk08), the average electron density traced by these RLs is N_e=8.4x10^6 cm^-3."
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "Upper limit on electron temperature Te = 4900 K",
  "failed_quote": "Therefore, for the gas traced by the H30alpha line, T_e is at most 4900 K, and the bulk gas motions are constrained to be much smaller than the thermal width."
 },
 {
  "path": "findings_qualitative[1].evidence[0]",
  "value": "The H30alpha line is narrower and redshifted relative to H53alpha, consistent with pressure broadening in H53alpha and optical depth effects in an outflowing ionized envelope",
  "failed_quote": "The H30alpha line is narrower than the H53alpha line, and it is redshifted by a few km s^-1. This behavior has been observed in hypercompact HII regions around embedded young massive stars"
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "H30alpha is virtually free of pressure broadening and traces the dense, static base of the ionized nebula, giving a systemic velocity v_LSR(BN) = 26.3 +- 0.5 km s^-1",
  "failed_quote": "Therefore, the H30alpha line should give a better estimation of the line-of-sight velocity of the star inside the BN nebula, v_LSR(BN)=26.3+-0.5 km s^-1."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "The electron temperature is Te <= 4900 K, bulk motions are << 10 km s^-1, and average electron density is 8.4 x 10^6 cm^-3",
  "failed_quote": "Therefore, for the gas traced by the H30alpha line, T_e is at most 4900 K, and the bulk gas motions are constrained to be much smaller than the thermal width."
 },
 {
  "path": "reasoning.why_this_method.evidence[0]",
  "value": "Excluding baselines shorter than 100 klambda filters out confusing extended emission from the hot core to isolate BN",
  "failed_quote": "We found that a minimum baseline length of approx 100 klambda gives optimal results, filtering out the emission on scales >1.4\"."
 },
 {
  "path": "reasoning.alternatives_considered_or_rejected[0].evidence[0]",
  "value": "Considered using the full baseline range for imaging BN and H30alpha, but rejected for primary analysis because extended emission and sidelobes from the hot core create contamination",
  "failed_quote": "The H30alpha line is also detected in maps that use the complete baseline range, but bright molecular emission from the HC centered at ~ 10 MHz blueshifted with respect to the RL creates sidelobes that are for the most part removed by taking only the longest baselines."
 }
]
```
