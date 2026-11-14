# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020NatAs...4..142L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
## **Spiral Structures in an Embedded Protostellar Disk Driven** **by Envelope Accretion**

Chin-Fei Lee [1][,][2][∗], Zhi-Yun Li [3], & Neal J. Turner [4]


1 Academia Sinica Institute of Astronomy and Astrophysics, P.O. Box 23-141, Taipei 106, Taiwan


2 Graduate Institute of Astronomy and Astrophysics, National Taiwan University, No. 1, Sec. 4,


Roosevelt Road, Taipei 10617, Taiwan


3 Astronomy Department, University of Virginia, Charlottesville, VA 22904, USA


4 Jet Propulsion Laboratory, California Institute of Technology, Pasadena, CA 91109, USA


Hydrodynamical simulations show that a pair of spiral arms can form in the disk around a


rapidly-growing young star and that the arms are crucial in transporting angular momentum


as the disk accretes material from the surrounding envelope [1–4] . Here we report the detection


of a pair of symmetric spiral structures in a protostellar disk, supporting the formation of


spiral arms in the disk around a forming star. The HH 111 VLA 1 source is a young Class I


source embedded in a massive infalling protostellar envelope and is actively accreting, driving


the prominent HH 111 jet. Previous observations showed a ring of shock emission around


the disk’s outer edge [5], indicating accretion of the envelope material onto the disk at a high


rate. Now with ALMA observations of thermal emission from dust particles, we detect a pair


of spiral arms extending from the inner region to the disk’s outer edge, similar to that seen


in many simulations [1–4] . Additionally, the disk is massive, with Toomre’s Q parameter near


unity in the outer parts where the spiral structures are detected, supporting the notion that


1

envelope accretion is driving the outer disk gravitationally unstable. In our observations,


another source, HH 111 VLA 2, is spatially resolved for the first time, showing a disk-like


structure with a diameter of ∼ 26 au and an orientation nearly orthogonal to that of the HH


111 VLA 1 disk.


Spiral structures have been recently detected at (sub)millimeter wavelengths in protoplane

tary disks whose protostellar envelopes have fully or partly dispersed [6–9] . These systems are in the


late stages of their stars’ growth, when planets are supposed to form. The spirals in most of these


systems have m = 2 symmetry and trail relative to the disk rotation. The fact that systems are seen


mostly with m = 2 structures could be due to observational bias since higher modes are harder


to resolve [10] . Unlike the spirals detected in near-infrared and optical images that trace scattered


star light, the (sub)millimeter spirals are thermal emission from dust that has settled closer to the


midplane of the disk where the bulk of the mass resides, allowing us to investigate how the spirals


are excited. The spirals could be induced by stellar or substellar companions, and thus potentially


be linked to planet formation [6–10] . The spirals in some systems may be driven by global gravita

tional instability (GI) [8,11,12], in which the disks are massive enough that their self-gravity overcomes


the thermal pressure and shear [13,14] . Some of the spirals may be driven by both a companion and


GI [11,12] .


These spiral structures in protoplanetary disks near the end of star formation naturally raise


the question of whether spiral structures can also appear in the early embedded phase of star for

mation when gas and dust from the surrounding molecular cloud core are still infalling onto the


2

disk. Indeed, a prominent spiral structure has been detected in the younger, Class 0 system L1448


IRS3B [15] . This is a triple system with a close binary at the center of the disk and a tertiary source


in the outer disk. The disk in this system appears to have recently undergone GI, inducing the


prominent spiral structure centered on the close binary with the third source located along the spi

ral structure in the outer disk [15] . The prominent spiral structure has apparently led to the formation


of the tertiary source through disk fragmentation. When the disk gas has a cooling time shorter


than about half the orbital period, the cooling can drive the disk toward instability and the collapse


of one or more fragments to form new gravitationally-bound bodies [2,14] . Another potential example


is the Class I binary system BHB07-11, where spiral-like structures are detected in dust continuum


emission, although apparently in the inner protostellar envelope outside the compact circumbinary


disk [16] .


Interestingly, many simulations have also shown that a pair of symmetric spiral structures can


appear in the main protostellar mass accretion phase [1–4], starting from the Class 0 and persisting to


the end of the Class I phase [17] . Unlike the spiral structure detected in L1448 IRS3B [15], these are


symmetric and play a critical role in transferring orbital angular momentum from the inner to the


outer disk, allowing accretion even in the absence of other forms of angular momentum transport


such as magneto-rotational instability or a disk wind [18] . In this paper, we report the detection of


a pair of symmetric spiral structures in the protostellar disk of an embedded Class I source, in


support of this possibility.


The HH 111 VLA 1 source is located in Orion at a distance of 400 pc. With a bolometric


3

temperature of only 78 K [19], it is a Class I source and therefore young. It is still deeply embedded


in a massive infalling envelope [5,20], and is both actively accreting and driving the prominent HH


111 jet that has a length of ∼ 6.7 pc (at the remeasured distance) [21] . A rotating disk is detected


toward the center with a radius of ∼ 200 au [5,20,22] producing polarized dust continuum emission [23] .


The central star has a mass M ∗ ∼ 1.5 ± 0.5M ⊙ [5,20,22] . The infall rate in the envelope towards the


[(][20][)]
center is estimated at ∼ 4.2 × 10 [−][6] M ⊙ yr [−][1] . Assuming mass flows at the same rate in the disk


where ∼ 30% of the flow is diverted into the jet and wind [24,25], the stellar accretion rate would be


˙ ˙
M ∗ ∼ 2.9 × 10 [−][6] M ⊙ yr [−][1], resulting in an accretion age M ∗ /M ∗ ∼ 5 × 10 [5] yrs. Another source


VLA 2 is also detected at a projected distance of ∼ 1200 au to the west, forming a wide binary


with the VLA 1 source.


Figure 1 presents our ALMA 343 GHz continuum map towards the two VLA sources at 0 [′′] . 04


(16 au) resolution, showing the thermal dust emission around them. The emission around the VLA


2 source is spatially resolved for the first time, appearing as a disklike structure, with a Gaussian


deconvolved size (diameter) of 0 [′′] . 064 (25.6 au) along the major axis at position angle 118.3 [◦] . Since


this disklike structure is roughly perpendicular to another jet, HH 121, the VLA 2 source likely


drives the HH 121 jet, as suggested by observations of the CO outflow [26] . Note that the VLA 2


disklike structure is nearly orthogonal to the VLA 1 disk, indicating the two components of this


wide protobinary system are strongly misaligned.


The VLA 1 source powers the prominent HH 111 jet directed east-west, as indicated by the


red and blue arrows. The surrounding emission shows a spatially resolved disk perpendicular to


4

the HH 111 jet, with its near side tilted to the southeast. To better see the disk structure, we rotate


the disk to align its major axis with the vertical (Fig. 1b). As can be seen, the disk has a radius of


∼ 0 [′′] . 4 (160 au), where the rotation was previously found to be roughly Keplerian in C [18] O [(][5][)] . The


aspect ratio of the disk structure is ∼ 0.3, indicating that the disk axis is inclined by ∼ 18 [◦] to the


−
plane of the sky, closely aligned with the HH 111 jet, which has an inclination angle of 13 [◦] 19 [◦]


(after the proper motion is updated for the new distance) [27] .


Figure 1c shows the map deprojected by the inclination angle, revealing a roundish compact


core and a pair of faint spiral structures in the outer disk. In order to better see the spirals, we


first made an annularly averaged map of the continuum (see Figure 2b) then subtracted it from the


deprojected map [9] . Figure 2c shows the difference map, which clearly shows a pair of symmetric


spiral structures labeled “NE” and “SW” extending from within ∼ 0 [′′] . 1 (40 au) of the central source


to the outer edge of the disk. To guide the eye, the emission peaks of the spirals are marked with


green circles. As discussed in Methods, the positions of these emission peaks are obtained from


Gaussian fits to the emission intensity in the radial direction. The spiral structures trail the rotation


of the disk measured in molecular lines [5] . Near the central source, two barlike structures connect


to the inner ends of the spiral structures. Since they are not clearly seen in the original map, these


could be artifacts of the deprojection of the central region, which is spatially unresolved in the


observation.


Two popular mechanisms have been proposed to account for the spiral structures in proto

planetary disks [6,8] . One is the global GI due to the self-gravity of the disk itself, which can produce


5

a pair of symmetric, logarithmic spiral arms with a constant pitch angle [12] . The other is a planet or


a stellar companion, which can also induce one or more spirals but with the pitch angle increasing


towards the location of the planet or companion [12,28] .


Here we explore these two possibilities for the spiral arms in the deeply-embedded VLA 1


protostellar disk by studying their pitch angles. Figure 3 shows the two spiral arms, NE and SW,


in polar coordinates, with R the radius and θ the polar angle. The data points correspond to the


emission peaks in Figure 2c. We fitted the points with the two spiral shapes, one logarithmic with


R = R 0 exp [aθ] and the other Archimedean with R = R 0 + bθ, where b is the increase rate of


the spiral radius with the angle, using the nonlinear least-squares Marquardt-Levenberg algorithm.


Tables 1 and 2 list the fitting results with these two spiral structures. Based on the χ [2] values, it


appears that the SW arm is slightly better fitted by a logarithmic shape, while the NE arm is slightly


better fitted by an Archimedean shape. The pitch angle is ∼ 16 [◦] for the SW arm and ∼ 13 [◦] for the


NE arm, both of which are similar to the pitch angle of the spirals in Elias 2-27 (∼ 16 [◦] ) [8] . Since


neither shape fits both arms best, higher-resolution and deeper observations are needed to better


distinguish these two possibilities.


Within the uncertainties of the current observations, the spiral structures in the VLA 1 disk


are consistent with the logarithmic pattern expected from a global GI. The spiral structures are


roughly symmetric and can be traced down to similar distance on opposite sides of the central


source, also as expected for a global GI. Simulations of gravitationally unstable disks appear ca

pable of reproducing the general morphology of the spiral structures in the VLA 1 disk [10,17] . For


6

example, in the simulations of Tomida et al. (2017) [17], the disk has a central core and an outer


pair of symmetric spiral arms appearing in the outer part of the disk, resembling Figure 2c. In

terestingly, in their simulations the spiral structures disappear and reform every few rotations as


the disk accretes mass from the envelope and becomes unstable again. Such recurrent spiral arms


first appear in the Class 0 phase and persist until accretion declines towards the end of the Class


I phase. Spirals are expected to disappear soon after accretion has stopped [29] . Accretion of enve

lope material onto the disk may trigger the development of spiral structures [30] and push power into


lower-m modes [4] even in non-self-gravitating disks.


Such recurrent spiral arms can also appear in the VLA 1 disk because the central source is still


young and in the Class I phase. The source is deeply embedded in an envelope with a mass of ∼ 0.6


M ⊙, extending out to ∼ 7000 au from the VLA 1 source [5,20] . The envelope is spiraling in towards


the disk at a rate of ∼ 4.2 × 10 [−][6] M ⊙ yr [−][1(][20][)] . This high infall rate is consistent with fast accretion


within the disk through GI-driven spirals that transport angular momentum efficiently [31,32] . In


addition, a ring of envelope-disk accretion shock emission from the SO molecule has been detected


around the outer edge of the disk [5], providing strong evidence for mass accretion from the envelope


onto the disk. Moreover, as discussed in Methods, the millimeter continuum emission from the


VLA 1 disk can be reasonably fitted with a simple flared disk model. The fit indicates the VLA 1


disk has a relatively high mass of 0.33-0.50 M ⊙, or 22%-33% of the protostellar mass. Therefore,


the resulting Toomre’s Q value is less than 1.5 for the outer part of the disk with a radius ∼> 100 au


(Supplementary Figure 3), further supporting the possibility of global non-axisymmetric GI as the


driver for the spiral arms [33] . If GI is occurring in the massive VLA 1 disk, it must play an important


7

role in facilitating accretion by transporting angular momentum outward [17] .


The spirals in the VLA 1 disk could instead be raised by a planet or companion. Our fit of


the Archimedean form to the spirals indicates the pitch angle increases inwards to ∼ 40 au (0 [′′] . 1),


where we would thus expect the planet or companion to be located and to clear a gap in the disk.


However, since the disk seems to be too massive for a planet to open a gap detectable at the current


resolution [34], observations at higher resolution are needed to search for a gap and check for this


scenario. In addition, since it has been suggested that the spiral arms in Elias 2-27 are due to a


so-far undetected external companion in the disk plane [11], it is natural to ask whether the spiral


arms in the VLA 1 disk can also be driven by an external companion. One possibility is VLA 2,


but we believe this is not likely to be the driver because the disk of VLA 1 is highly inclined with


respect to the plane of the sky, being nearly edge-on. If VLA 2 lies on the disk plane of VLA 1,


it would have to be located at a distance much larger than its projected separation of ∼ 1, 200 au,


which would greatly reduce its gravitational influence on the VLA 1 disk. If VLA 2 is located far


from the VLA 1 disk plane, in addition to inducing spiral arms it should warp the disk. No sign


of warping is detected in our continuum observations; higher resolution continuum and especially


line observations are desirable to put tighter constraints on any disk warping. Another possibility is


a putative stellar companion of ∼ 1M ⊙, inferred to lie at a distance of ∼ 186 au from VLA 1 based


on the wiggling of the HH 111 jet and counterjet [35] . However, such a massive young star should


have a disk detectable with our sensitive ALMA continuum observation if it is at an evolutionary


stage similar to that of VLA 1, yet nothing is seen. Further observations are needed to check the


possibility that a companion in a suitable position has been missed.


8

1. Bate, M. R. Collapse of a Molecular Cloud Core to Stellar Densities: The First Three

dimensional Calculations. Astrophys. J. Lett. 508, L95-L98 (1998)


2. Rice, W. K. M., Armitage, P. J., Bate, M. R., & Bonnell, I. A. The effect of cooling on the


global stability of self-gravitating protoplanetary discs. Mon. Not. R. Astron. Soc. 339, 1025

1030 (2003)


3. Tomida, K., Machida, M. N., Saigo, K., Tomisaka, K., & Matsumoto, T. Exposed Long-lifetime


First Core: A New Model of First Cores Based on Radiation Hydrodynamics. Astrophys. J.


Lett. 725, L239-L244 (2010)


4. Harsono, D., Alexander, R. D., & Levin, Y. Global gravitational instabilities in discs with infall.


Mon. Not. R. Astron. Soc. 413, 423-433 (2011)


5. Lee, C.-F., Hwang, H.-C., & Li, Z.-Y. Angular Momentum Loss in the Envelope-Disk Tran

sition Region of the HH 111 Protostellar System: Evidence for Magnetic Braking?. Astrophys.


J. 826, 213 (2016)


6. P´erez, L. M., Carpenter, J. M., Andrews, S. M., et al. Spiral density waves in a young proto

planetary disk. Science 353, 1519-1521 (2016)


7. Andrews, S. M., Huang, J., P´erez, L. M., et al. The Disk Substructures at High Angular Res

olution Project (DSHARP). I. Motivation, Sample, Calibration, and Overview. Astrophys. J.


Lett. 869, L41 (2018)


9

8. Huang, J., Andrews, S. M., P´erez, L. M., et al. The Disk Substructures at High Angular Reso

lution Project (DSHARP). III. Spiral Structures in the Millimeter Continuum of the Elias 27, IM


Lup, and WaOph 6 Disks. Astrophys. J. Lett. 869, L43 (2018)


9. Kurtovic, N. T., P´erez, L. M., Benisty, M., et al. The Disk Substructures at High Angular Res

olution Project (DSHARP). IV. Characterizing Substructures and Interactions in Disks around


Multiple Star Systems. Astrophys. J. Lett. 869, L44 (2018)


10. Hall, C., Rice, K., Dipierro, G., Forgan, D., Harries, T., & Alexander, R. Is the spiral morphol

ogy of the Elias 2-27 circumstellar disc due to gravitational instability?. Mon. Not. R. Astron.


Soc. 477, 1004-1014 (2018)


11. Meru, F., Juh´asz, A., Ilee, J. D., Clarke, C. J., Rosotti, G. P., & Booth, R. A. On the Origin of


the Spiral Morphology in the Elias 2-27 Circumstellar Disk. Astrophys. J. Lett. 839, L24 (2017)


12. Forgan, D. H., Ilee, J. D., & Meru, F. Are Elias 2-27’s Spiral Arms Driven by Self-gravity, or


by a Companion? A Comparative Spiral Morphology Study. Astrophys. J. Lett. 860, L5 (2018)


13. Toomre, A. On the gravitational stability of a disk of stars. Astrophys. J. 139, 1217-1238 (1964)


14. Gammie, C. F. Nonlinear Outcome of Gravitational Instability in Cooling, Gaseous Disks.


Astrophys. J. 553, 174-183 (2001)


15. Tobin, J. J., Kratter, K. M., Persson, M. V., et al. A triple protostar system formed via frag

mentation of a gravitationally unstable disk. Nature 538, 483-486 (2016)


10

16. Alves, F. O., Girart, J. M., Caselli, P., Franco, G. A. P., Zhao, B., Vlemmings, W. H. T., Evans,


M. G., & Ricci, L. Molecular outflow launched beyond the disk edge. Astron. Astrophys. 603, L3


(2017)


17. Tomida, K., Machida, M. N., Hosokawa, T., Sakurai, Y., & Lin, C. H. Grand-design Spiral


Arms in a Young Forming Circumstellar Disk. Astrophys. J. Lett. 835, L11 (2017)


18. Turner, N. J., Fromang, S., Gammie, C., Klahr, H., Lesur, G., Wardle, M., & Bai, X.-N. in


Protostars and Planets VI, (eds Beuther, H. et al.) 411-432 (Univ. Arizona Press, 2014)


19. Froebrich, D. Which Are the Youngest Protostars? Determining Properties of Confirmed and


Candidate Class 0 Sources by Broadband Photometry. Astrophys. J. Suppl. 156, 169-177 (2005)


20. Lee, C.-F. A Change of Rotation Profile in the Envelope in the HH 111 Protostellar System:


A Transition to a Disk?. Astrophys. J. 725, 712-720 (2010)


21. Reipurth, B., Bally, J., & Devine, D. Giant Herbig-Haro Flows. Astron. J. 114, 2708 (1997)


22. Lee, C.-F. A Rotating Disk in the HH 111 Protostellar System. Astrophys. J. 741, 62 (2011)


23. Lee, C.-F., Li, Z.-Y., Ching, T.-C., Lai, S.-P., & Yang, H. ALMA Dust Polarization Observa

tions of Two Young Edge-on Protostellar Disks. Astrophys. J. 854, 56 (2018)


24. Shu, F. H., Najita, J. R., Shang, H., and Li, Z.-Y. in Protostars and Planets IV, (eds Mannings,


V. et al.) 789-814 (Univ. Arizona Press, 2000)


25. Konigl, A. & Pudritz, R. E. in Protostars and Planets IV, (eds Mannings, V. et al.) 759-787


(Univ. Arizona Press, 2000)


11

26. Sewiło, M., Wiseman, J., Indebetouw, R., Charnley, S. B., Pineda, J. E., Lindberg, J. E., & Qin,


S.-L. Very Large Array Ammonia Observations of the HH 111/HH 121 Protostellar System: A


Detection of a New Source with a Peculiar Chemistry. Astrophys. J. 849, 68 (2017)


27. Reipurth, B., Raga, A. C., & Heathcote, S. Structure and Kinematics of the HH 111 Jet.


Astrophys. J. 392, 145 (1992)


28. Bae, J., & Zhu, Z. Planet-driven Spiral Arms in Protoplanetary Disks. II. Implications. Astro

phys. J. 859, 119 (2018)


29. Hall, C., Dong, R., Rice, K., Harries, T. J., Najita, J., Alexander, R., & Brittain, S. The Tem

poral Requirements of Directly Observing Self-gravitating Spiral Waves in Protoplanetary Disks


with ALMA. Astrophys. J. 871, 228 (2019)


30. Hennebelle, P., Lesur, G., & Fromang, S. Spiral-driven accretion in protoplanetary discs. II.


Self-similar solutions. Astron. Astrophys. 590, A22 (2016)


31. Dong, R., Hall, C., Rice, K., & Chiang, E. Spiral Arms in Gravitationally Unstable Protoplan

etary Disks as Imaged in Scattered Light. Astrophys. J. Lett. 812, L32 (2015)


32. Hall, C., Forgan, D., Rice, K., Harries, T. J., Klaassen, P. D., & Biller, B. Directly observing


continuum emission from self-gravitating spiral waves. Mon. Not. R. Astron. Soc. 458, 306-318


(2016)


33. Durisen, R. H., Boss, A. P., Mayer, L., Nelson, A. F., Quinn, T., & Rice, W. K. M. in Protostars


and Planets V (eds Reipurth, B. et al.) 607-622 (Univ. Arizona Press, 2007)


12

34. Baruteau, C., & Masset, F. Type I Planetary Migration in a Self-Gravitating Disk. Astrophys.


J. 678, 483-497 (2008)


35. Noriega-Crespo, A., Raga, A. C., Lora, V., Stapelfeldt, K. R., & Carey, S. J. The Precession of


the Herbig-Haro 111 Flow in the Infrared. Astrophys. J. Lett. 732, L16-L20 (2011)


Correspondence and requests for materials should be addressed to C.-F.L.


Acknowledgements This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00037.S


and 2017.1.00044.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS


(Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooper

ation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.


C.-F.L. acknowledges grants from the Ministry of Science and Technology of Taiwan (MoST 107-2119-M

001-040-MY3) and the Academia Sinica (Investigator Award AS-IA-108-M01). Z.-Y.L. is supported in part


by NSF grants AST-1716259, 1815784 and 1910106 and NASA grant 80NSSC18K1095. N.J.T.’s contribu

tion was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under contract with


NASA and with the support of NASA grant 17-XRP17 2-0081.


Author Contributions C.-F. Lee led the project, analysis, discussion, and drafted the manuscript. Z.-Y.


Li and N. J. Turner commented on the manuscript and participated in the discussion.


Competing interests The authors declare no competing financial interests.


13

14

Figure 1. The 343 GHz continuum map towards the VLA 1 and 2 sources. The peak posi

tions are ICRS α (2000) = 05 [h] 51 [m] 46 [s] .2537, δ (2000) = +02 [◦] 48 [′] 29 [′′] . 643 and α (2000) = 05 [h] 51 [m] 46 [s] .0665,


δ (2000) = +02 [◦] 48 [′] 30 [′′] . 815, respectively for the VLA 1 and VLA 2 sources. The synthesized beam


has a size of 0 [′′] . 050×0 [′′] . 036. Blue and red arrows in panel (a) indicate the orientations of the


blueshifted (western) and redshifted (eastern) components of the HH 111 jet, respectively, emanat

ing from the VLA 1 source. The inset is a zoom-in towards the VLA 2 source, with white lines


marking the major axis of the continuum emission. Panel (b) shows a zoom-in on the disk around


the VLA 1 source, rotated so the major axis is vertical. Panel (c) shows the VLA 1 disk deprojected


by the inclination angle. Blue and red curved arrows show the direction of the disk rotation.


Figure 2. The spiral structure in the disk around the VLA 1 source. Panel (a) is the same


as Figure 1c and shows the disk deprojected. In panel (b), the structure is annularly averaged.


15

Panel (c) shows the map obtained by subtracting the annular mean map from the deprojected map,


revealing the underlying spiral features NE and SW, which have intensities ∼ 5-20% of the local


annular average. Blue and red curved arrows again show the direction of the disk rotation. Green


open circles mark the emission peaks of the spirals, outlining the spiral features.


Figure 3. Two fits to each of the two spiral features in the VLA 1 disk. The NE and SW arm


are offset vertically for clarity. Error bars show the arms’ widths as measured by the Gaussians


that best fit the emission intensities along rays from the central source. Each arm is fit in turn with


a logarithmic (solid black curve) and an Archimedean spiral (dashed black curve).


16

**Table 1.** Best-Fit Logarithmic Spirals


Arm R 0 a χ [2] Pitch Angle


(arcsecond) (radian [−][1] ) (Degree)


SW 0 [′′] . 132±0 [′′] . 003 0.288±0.010 2.07 16.1 [◦] ±0.6 [◦]


NE 0 [′′] . 077±0 [′′] . 004 0.222±0.011 2.88 12.5 [◦] ±0.6 [◦]


**Table 2.** Best-Fit Archimedean Spirals


Arm R 0 b χ [2] Pitch Angle [†]


(arcsecond) (arcsecond radian [−][1] ) (Degree)


SW 0 [′′] . 132±0 [′′] . 005 0.061±0.003 3.77 23.4 [◦] ±1.2 [◦] − 8.8 [◦] ±0.4 [◦]


NE −0 [′′] . 011±0 [′′] . 008 0.050±0.002 1.41 19.1 [◦] ±0.8 [◦] − 7.2 [◦] ±0.4 [◦]


- : Pitch Angle decreases from 60 au (0 [′′] . 15) to 160 au (0 [′′] . 4)


17

Methods


Observations We observed the HH 111 VLA 1 system with ALMA in Band 7 at ∼ 343 GHz in


Cycle 5 (Project ID: 2017.1.00044S). Three observations were carried out in C43-8 configuration


using 47 antennas, two on 2017 November 28 and one on 2017 December 1, with a total time of


∼ 109 minutes on target. The projected baseline lengths were ∼ 60-8550 meters. One pointing


centered at the VLA 1 source was used. The primary beam (field of view) had a size of ∼ 17 [′′] . 8,


covering both the VLA 1 and VLA 2 sources. The correlator was set to have four continuum


windows, centered at 336.5, 338.5, 348.5, and 350.5 GHz for a total bandwidth of ∼ 8 GHz. The


maximum recoverable size (MRS) was 0 [′′] . 54. In order to restore a larger size scale, we combined


these observations with our previous Cycle 3 observations [23], which had the same correlator setup


but a larger MRS of ∼ 1 [′′] . 4. Thus, there is no noticeable missing flux in our maps of the disks


around the two VLA sources, which have a size ∼< 1 [′′] .


The CASA 5.1.1 package was used to calibrate the uv data obtained from our observa

tions. Quasar J0510+1800 was observed as a passband calibrator and a flux calibrator, and quasar


J0552+0313 (a flux of ∼ 0.24±0.10 Jy) was observed as a gain calibrator. We also performed a


phase-only self-calibration to improve the map fidelity. As mentioned above, we combined our


observations with our previous Cycle 3 observations to avoid any missing flux for the disks. We


used a super-uniform weighting with a robust factor of 0.25. The resulting synthesized beam (res

olution) has a size of 0 [′′] . 050×0 [′′] . 036 at a position angle (P.A.) of ∼ 55 [◦] . The rms noise level is ∼


∼
0.10 mJy beam [−][1] ( 0.58 K).


18

Spiral Structures Supplementary Figure 1 shows the spiral structures in the HH 111 VLA 1


disk presented in Figure 2c. We locate the emission peak positions of the spirals by fitting by eye


a Gaussian to their emission intensity in the difference map cut along lines of constant position


angle every 10 [◦] . Contours are also plotted outlining the spiral arms. The uncertainties in the peak


positions are shown by radial error bars, marking the width at half maximum.


Disk Model Here we derive the properties of the VLA 1 disk in order to investigate the origin


of the spiral structures. We adopt a parametrized flared disk model, the same as that used to


reproduce the disk emission in the well-resolved Class 0 disk in HH 212 [36] . In this model, the


disk is axisymmetric, with its physical parameters specified in cylindrical coordinates. It has a


temperature


T = T t ( [R] ) [−][q] (1)

R t


where R is the cylindrical radius, R t is a representative radius to be defined below, T t is the tem

perature at R t, and q is the temperature power-law index. The model disk is in vertical hydrostatic


equilibrium, with the number density of molecular hydrogen decreasing as a Gaussian in height


above the midplane so




[R] − [z] [2]

) [−][p] exp(
R t 2h



n = n t ( [R]



(2)
2h [2] [)]



where n t is the number density of molecular hydrogen in the midplane at R t, p is the density


19

power-law index, and h is the scale height. The mass density is then ρ = 1.4nm H 2, accounting for


helium at solar abundance relative to hydrogen.


In vertical hydrostatic equilibrium, the scale height h comes from




[c] [s] ∝ [R] [−][q/][2]

v R [−][1][/][2]
φ



h
R [∼] v [c] [s]




[=][ R] [(1][−][q][)][/][2] (3)
R [−][1][/][2]



where the isothermal sound speed c s ∝ T [1][/][2] ∝ R [−][q/][2] . The rotation speed v φ is Keplerian and


thus given by v φ = � GM ∗ /R, where the protostellar mass M ∗ ∼ 1.5 M ⊙, as found from the


C [18] O gas kinematics [5,20] . With this scale height, increasing monotonically in radius, we failed to


fit the observed thinning of the disk near its outer edge. Thus, as in HH 212, we assume the disk


to be geometrically thinner near its outer edge. This could come from self-shielding reducing the


temperature and thus the scale height in the outermost parts [37] . Therefore, we define R t to be the


radius beyond which the scale height decreases towards the outer radius of the disk R o . Thus, the


scale height becomes



(4)



h(R) ∼ h t







( R [R] t [)] [1+(1][−][q][)][/][2] if R < R t,



1 − [3]
� 4



4 [3] [(] R [R][−] − [R] R [t]



R o [−] −R [t] t [)] [2] if R t ≤ R ≤ R o



where h t ∼ v [c] φ [s] [(] ( [R] R [t] t [)] ) [R] [t] [ is the scale height at][ R] [t] [ and][ h][ =][ h] [t] [/][2][ at][ R][ =][ R] [o] [.]


For the dust continuum emission of the disk, we assume the dust opacity law


20

ν
κ ν = 0.1 � 10 [12] Hz



β
cm [2] g [−][1] (5)
�



which has been used before for circumstellar disks in Taurus [38] . Here β is the dust opacity spectral


index and κ ν the opacity per gram of gas and dust for a gas-to-dust mass ratio of 100. The β value


is uncertain, affecting the disk mass needed to produce the observed total flux. To be inclusive, we


consider values ranging from 0.6 as in the young HH 212 protostellar disk [36] to 1.0 as in protoplan

etary disks [38,39] . Therefore, we have κ ν ∼ 0.054 − 0.035 cm [2] g [−][1] at the observing frequency of


343 GHz.


To compute the dust emission, we tilt the model disk so its axis is ∼ 18 [◦] from the plane of


the sky, as estimated from the observed aspect ratio. We then compute the dust emission assuming


local thermodynamic equilibrium, and integrate along a grid of lines of sight the local emission


that is attenuated by the optical depth, as done before for the HH 212 disk [36] . We then convolve the


resulting map with the telescope’s beam, producing a model map to be compared with the observed


map at the same resolution.


Supplementary Figure 2 shows our best-fit continuum map. The model has 6 free parame

ters: R t, R o, q, T t, p, and n t . In our fit, R t ∼ 0 [′′] . 4 (160 au), consistent with the observed radius


of the disk, and R o ∼ 0 [′′] . 5 (200 au) in order to produce the faint emission in the outer edge. The


temperature power-law index q ∼ 0.55 ± 0.11, similar to that found in protoplanetary disks in


Ophiuchus [39] . With T t ∼ 68 ± 13 K, the resulting scale height h t is approximately 0 [′′] . 068±0 [′′] . 007


(∼ 27±3 au) at R t . For the density, we have p ∼ 1.5 ± 0.4 and n t ∼ (6.0 − 9.3) × 10 [9] cm [−][3] corre

21

sponding to the range of opacities κ ∼ 0.054 − 0.035 cm [2] g [−][1] . As can be seen in Supplementary


Figure 2a, the model emission contours (red) can roughly match the observed emission contours


(black with a gray-scaled image) of the continuum. Since the model is axisymmetric and does not


include any spiral structures, we can not fit the non-axisymmetries. However, since the residuals


are reasonably small (Supplementary Figure 2b), the model adequately describes the radial struc

ture. In addition, as can be seen in Supplementary Figure 2c, since the model disk emission is


mostly optically thick along the major axis, the temperature in our model is well constrained. In


our model, the disk has a surface density



Σ = 1.4 m H 2



2h t
� − [√] √2h



−√



n dz (6)
2h t



and a mass


R o
M D = Σ 2π R dR ∼ (0.33 − 0.50) M ⊙ (7)
�


which is ∼ 22%−33% of the protostellar mass. Thus the disk is relatively massive.


Supplementary Figure 3 shows the model’s stability against GI as measured by Toomre’s Q


parameter


Q ∼ [c] [s] [Ω] (8)

πGΣ


22

where Ω= [v] R [φ] [is the angular velocity of the disk.] [As can be seen,][ Q][ is less than 1.5 for][ R] ∼ [>][ 0] [′′] [.][ 25]


(100 au), indicating that the disk is gravitationally unstable in its outer half. Since the dust opacity


is uncertain, further observations are needed to confirm the instability and check whether the inner


part is also gravitationally unstable.


If the Q parameter at a given location were much less than unity, the scale height there would


be dominated by the local self-gravity rather than the tidal gravity of the central star. The scale


height would then be roughly [40] :


c [2] s
h s ∼ (9)
πGΣ [∼] [Qh]


The scale height would be significantly less than h. However, in our model, the Q parameter is of


order unity or larger, and the effect of self-gravity on the scale height is moderate (at most a factor


of 2).


Data availability. This letter makes use of the following ALMA data: ADS/JAO. ALMA2015.1.00037.S


and 2017.1.00044.S. The data that support the plots within this paper and other findings of this


study are available from the corresponding author upon reasonable request.


36. Lee, C.-F., Li, Z.-Y., Ho, P. T. P., Hirano, N., Zhang, Q., & Shang, H. First detection of


equatorial dark dust lane in a protostellar disk at submillimeter wavelength. Sci. Adv. 3, e1602935


(2017)


23

37. Dullemond, C. P., & Dominik, C. Flaring vs. self-shadowed disks: The SEDs of Herbig Ae/Be


stars. Astron. Astrophys. 417, 159-168 (2004)


38. Beckwith, S. V. W., Sargent, A. I., Chini, R. S., & Guesten, R. A Survey for Circumstellar


Disks around Young Stellar Objects. Astron. J. 99, 924-945 (1990)


39. Andrews, S. M., Wilner, D. J., Hughes, A. M., Qi, C., & Dullemond, C. P. Protoplanetary Disk


Structures in Ophiuchus. Astrophys. J. 700, 1502-1523 (2009)


40. Spitzer, L. The Dynamics of the Interstellar Medium. III. Galactic Distribution. Astrophys.


J. 95, 329-344 (1942)


24


</paper>

## Items to check

```json
[
 {
  "path": "science.question.evidence[0]",
  "value": "Whether spiral structures can appear in the early embedded phase of star formation in a protostellar disk accreting from an infalling envelope, and what mechanism drives them.",
  "failed_quote": "These spiral structures in protoplanetary disks near the end of star formation naturally raise the question of whether spiral structures can also appear in the early embedded phase of star formation when gas and dust from the surrounding molecular cloud core are still infalling onto the disk."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "Bolometric temperature of HH 111 VLA 1 (78 K)",
  "failed_quote": "With a bolometric temperature of only 78 K [19], it is a Class I source and therefore young."
 },
 {
  "path": "processing.inherited[2].what.evidence[0]",
  "value": "Dust opacity law kappa_nu = 0.1 (nu / 10^12 Hz)^beta cm^2 g^-1 and beta range 0.6 to 1.0",
  "failed_quote": "For the dust continuum emission of the disk, we assume the dust opacity law κ ν = 0.1 (ν / 10^12 Hz)^β cm^2 g^-1 (5) which has been used before for circumstellar disks in Taurus [38] ."
 },
 {
  "path": "analysis_steps[3].method.evidence[2]",
  "value": "Construct axisymmetric parametrized flared disk model with outer thinning, compute LTE radiative transfer integrated along lines of sight tilted by ~18 deg, convolve with telescope beam to fit observed continuum map, and integrate surface density to obtain disk mass and Toomre Q profile",
  "failed_quote": "Supplementary Figure 3 shows the model’s stability against GI as measured by Toomre’s Q parameter Q ∼ c_s Ω / (πGΣ) (8)"
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[1]",
  "value": "Vertical hydrostatic equilibrium with Keplerian rotation around M_* ~ 1.5 M_sun, and outer geometric thinning between R_t and R_o",
  "failed_quote": "The rotation speed v φ is Keplerian and thus given by v φ =  GM ∗ /R, where the protostellar mass M ∗ ∼ 1.5 M ⊙, as found from the C [18] O gas kinematics [5,20] ."
 },
 {
  "path": "results_numeric[19].evidence[0]",
  "value": "Disk model density power-law index p = 1.5 dimensionless",
  "failed_quote": "For the density, we have p ∼ 1.5 ± 0.4 and n t ∼ (6.0 − 9.3) × 10 [9] cm [−][3] corresponding to the range of opacities κ ∼ 0.054 − 0.035 cm [2] g [−][1] ."
 },
 {
  "path": "results_numeric[20].evidence[0]",
  "value": "Disk model midplane number density n_t at R_t = 6.0 - 9.3 10^9 cm^-3",
  "failed_quote": "For the density, we have p ∼ 1.5 ± 0.4 and n t ∼ (6.0 − 9.3) × 10 [9] cm [−][3] corresponding to the range of opacities κ ∼ 0.054 − 0.035 cm [2] g [−][1] ."
 },
 {
  "path": "results_numeric[21].evidence[0]",
  "value": "HH 111 VLA 1 disk mass M_D = 0.33 - 0.50 M_sun",
  "failed_quote": "and a mass M_D = integral(Sigma 2 pi R dR) ~ (0.33 - 0.50) M_sun (7) which is ∼ 22%−33% of the protostellar mass."
 },
 {
  "path": "results_numeric[22].evidence[0]",
  "value": "HH 111 VLA 1 disk-to-star mass ratio = 22 - 33 %",
  "failed_quote": "and a mass M_D = integral(Sigma 2 pi R dR) ~ (0.33 - 0.50) M_sun (7) which is ∼ 22%−33% of the protostellar mass."
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "The spiral structures and high disk mass (low Toomre Q) support global gravitational instability fed by envelope accretion as the driver of the spiral arms.",
  "failed_quote": "Additionally, the disk is massive, with Toomre’s Q parameter near unity in the outer parts where the spiral structures are detected, supporting the notion that envelope accretion is driving the outer disk gravitationally unstable."
 }
]
```
