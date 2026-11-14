# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020AJ....160..205N\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version October 27, 2020
Typeset using L [A] TEX **manuscript** style in AASTeX63


**Detection** **of** **Cyclopropenylidene** **on** **Titan** **with** **ALMA**


Conor [A.](http://orcid.org/0000-0001-9540-9121) Nixon, [1] [Alexander](http://orcid.org/0000-0002-8178-1042) E. Thelen, [2, 1,] _[ ∗]_ Martin [A.](http://orcid.org/0000-0001-8233-2436) Cordiner, [3, 1] [Zbigniew](http://orcid.org/0000-0002-2570-3154) Kisiel, [4]

Steven B. Charnley, [1] Edward [M.](http://orcid.org/0000-0003-3799-9033) Molter, [5] Joseph [Serigano,](http://orcid.org/0000-0003-3849-5064) [6] Patrick [G.](http://orcid.org/0000-0002-6772-384X) J. Irwin, [7]

Nicholas [A.](http://orcid.org/0000-0003-3108-5775) Teanby, [8] and [Yi-Jehng](http://orcid.org/0000-0002-4336-0730) Kuan [9, 10]


1 _Solar_ _System_ _Exploration_ _Division,_ _NASA_ _Goddard_ _Space_ _Flight_ _Center,_ _Greenbelt,_ _MD_ _20771,_ _USA._


2 _Universities_ _Space_ _Research_ _Association,_ _Columbia,_ _MD_ _21046,_ _USA_


3 _Catholic_ _University_ _of_ _America,_ _Washington,_ _DC_ _20064,_ _USA_


4 _Institute_ _of_ _Physics,_ _Polish_ _Academy_ _of_ _Sciences,_ _Al._ _Lotnik´ow_ _32/46,_ _02-668_ _Warszawa,_ _Poland._


5 _Department_ _of_ _Astronomy,_ _University_ _of_ _California,_ _Berkeley,_ _CA_ _94720,_ _USA._


6 _Department_ _of_ _Earth_ _and_ _Planetary_ _Sciences,_ _Johns_ _Hopkins_ _University,_ _Baltimore,_ _MD_ _21218,_ _USA._


7 _Atmospheric,_ _Oceanic,_ _and_ _Planetary_ _Physics,_ _Clarendon_ _Laboratory,_ _University_ _of_ _Oxford,_ _Parks_ _Road,_ _Oxford,_


_OX1_ _3PU,_ _UK._


8 _School_ _of_ _Earth_ _Sciences,_ _University_ _of_ _Bristol,_ _Wills_ _Memorial_ _Building,_ _Queens_ _Road,_ _Bristol,_ _BS8_ _1RJ,_ _UK._


9 _Department_ _of_ _Earth_ _Sciences,_ _National_ _Taiwan_ _Normal_ _University,_ _Taipei_ _116,_ _Taiwan,_ _ROC._


10 _Institute_ _of_ _Astronomy_ _and_ _Astrophysics,_ _Academia_ _Sinica,_ _Taipei_ _106,_ _Taiwan,_ _ROC._


(Received 22 April 2020; Revised 14 August 2020; Accepted 7 September 2020)


Submitted to The Astronomical Journal


ABSTRACT


We report the first detection on Titan of the small cyclic molecule cyclopropenyli

dene (c-C 3 H 2 ) from high sensitivity spectroscopic observations made with the Atacama


Large Millimeter/sub-millimeter Array (ALMA). Multiple lines of cyclopropenylidene


were detected in two separate datasets: _∼_ 251 GHz in 2016 (Band 6) and _∼_ 352 GHz


Corresponding author: Conor A. Nixon
[conor.a.nixon@nasa.gov](mailto: conor.a.nixon@nasa.gov)

2 Nixon et al.


in 2017 (Band 7). Modeling of these emissions indicates abundances of 0.50 _±_ 0.14


ppb (2016) and 0.28 _±_ 0.08 (2017) for a 350-km step model, which may either sig

nify a decrease in abundance, or a mean value of 0.33 _±_ 0.07 ppb. Inferred column


abundances are 3–5 _×_ 10 [12] cm _[−]_ [2] in 2016 and 1–2 _×_ 10 [12] cm _[−]_ [2] in 2017, similar to pho

tochemical model predictions. Previously the C 3 H [+] 3 [ion] [has] [been] [measured] [in] [Titan’s]


ionosphere by Cassini’s Ion and Neutral Mass Spectrometer (INMS), but the neutral


(unprotonated) species has not been detected until now, and aromatic versus aliphatic


structure could not be determined by the INMS. Our work therefore represents the first


unambiguous detection of cyclopropenylidene, the second known cyclic molecule in Ti

tan’s atmosphere along with benzene (C 6 H 6 ) and the first time this molecule has been


detected in a planetary atmosphere. We also searched for the N-heterocycle molecules


pyridine and pyrimidine finding non-detections in both cases, and determining 2- _σ_ upper


limits of 1.15 ppb (c-C 5 H 5 N) and 0.85 ppb (c-C 4 H 4 N 2 ) for uniform abundances above


300 km. These new results on cyclic molecules provide fresh constraints on photochem

ical pathways in Titan’s atmosphere, and will require new modeling and experimental


work to fully understand the implications for complex molecule formation.


_Keywords:_ TBD


1. INTRODUCTION


Saturn’s moon Titan exhibits the most complex chemistry of any known planetary atmosphere other


than the Earth. The reducing chemical environment, composed primarily of methane and nitrogen


gases (Niemann et al. 2010), produces a rich array of organic molecules when activated by solar UV


photons or Saturn magnetospheric electrons (Vuitton et al. 2019). Many of these daughter species


are hydrocarbons (C _x_ H _y_ ) or nitriles (C _x_ H _y_ (CN) _z_ ), however several oxygen compounds have also been


detected (CO, CO 2, H 2 O), apparently due to an influx of external OH and O [+] from Enceladus (H¨orst


_∗_ NASA Post-Doctoral Program Fellow

Detection of Cyclopropenylidene on Titan 3


et al. 2008), and several other light gases including H 2 (from methane destruction), and the noble


gases Ar and Ne.


Prior to the Cassini mission, most of our knowledge about Titan’s atmospheric composition had


come from remote sensing spectroscopy. While CH 4 and N 2 were detected at short wavelengths


(Kuiper 1944; Broadfoot et al. 1981), most other gases were first seen in the infrared. These include


the detections of C 2 H 6, C 2 H 2, C 2 H 4 and CO using ground-based telescopes (Gillett et al. 1973; Gillett


1975; Lutz et al. 1983); the Voyager 1 IRIS (Infrared Interferometer-Spectrometer) detections of H 2,


C 3 H 4, C 3 H 8, C 4 H 2, HCN, HC 3 N, C 2 N 2 and CO 2 (Hanel et al. 1981; Maguire et al. 1981; Kunde et al.


1981; Samuelson et al. 1981; Samuelson et al. 1983); as well as later detections with ISO (Infrared


Space Observatory) of H 2 O and C 6 H 6 (Coustenis et al. 1998, 2003). A notable exception was the


detection of CH 3 CN by Bezard et al. (1992) at sub-millimeter wavelengths using the IRAM 30 m


telescope at Pico Veleta.


This paradigm changed substantially with the Cassini-Huygens mission, which carried mass spec

trometers on both the orbiter and the probe (Niemann et al. 2002; Young et al. 2004; Waite et al.


2004), able to sample the composition of Titan’s atmosphere _in_ _situ_ for the first time. Modeling of


these mass spectra revealed a plethora of ion and neutral species (Waite et al. 2005; Hartle et al.


2006; Vuitton et al. 2007, 2009; Cui et al. 2009; Bell et al. 2010a,b; Westlake et al. 2011), although in


many cases exact molecular identification remained elusive, due to the inability of mass spectra alone


to elucidate molecular structure. One new positive identification was made in the infrared using


Cassini’s CIRS instrument (Composite Infrared Spectrometer, Flasar et al. 2004), of propene (C 3 H 6,


Nixon et al. 2013b). Shortly after the end of the Cassini mission, a further infrared detection was


made using TEXES (the Texas Echelon-cross-Echelle Spectrograph) (Lacy et al. 2002) at NASA’s


Infrared Telescope Facility (IRTF): namely propadiene (CH 2 CCH 2, Lombardo et al. 2019), an isomer


of propyne (C 3 H 4 ).


The newest tool for probing Titan’s atmospheric composition has been ALMA (the Atacama Large


Millimeter/submillimeter Array: Baars 2002; Lellouch 2007), a powerful interferometer array that


started science observations in 2011. At millimeter (mm) and submillimeter (sub-mm) wavelengths

4 Nixon et al.


rotational transitions of molecules are accessible, which have proved vital for probing the chemistry


of astrophysical objects such as dense molecular clouds. Using early data from ALMA two further


nitrile (cyanide) species were soon conclusively identified in Titan’s atmosphere: propionitrile (ethyl


cyanide, C 2 H 5 CN, Cordiner et al. 2015) and acrylonitrile (vinyl cyanide, C 2 H 3 CN, Palmer et al. 2017),


as well as many isotopologues of previously detected species including CO, HCN, HC 3 N, CH 3 CN and


CH 4 (Serigano et al. 2016; Molter et al. 2016; Palmer et al. 2017; Cordiner et al. 2018; Thelen et al.


2019a; Iino et al. 2020).


Besides making new chemical detections, observations of Titan from Cassini and ALMA have


mapped the spatial and temporal evolution of the gas distributions, revealing complex structure such


as polar jets, and seasonal changes of unexpected rapidity: see B´ezard et al. (2014); H¨orst (2017) for


detailed reviews. In parallel with observations, photochemical modeling of Titan’s atmosphere has


also progressed rapidly to explain the observed gas abundance distributions, and to make predictions


for target species likely to be detectable. See for example recent work by Krasnopolsky (2009, 2010,


2012); H´ebrard et al. (2013); Krasnopolsky (2014); Dobrijevic et al. (2014); Loison et al. (2015);


Willacy et al. (2016); Vuitton et al. (2019).


In 2016 and 2017 we conducted high sensitivity observations with ALMA, with the goal of searching


for new molecules in Titan’s atmosphere, including the N-heterocyclic molecules pyridine (c-C 5 H 5 N)


and pyrimidine (c-C 4 H 4 N 2 ). N-heterocycles have a strong importance to astrobiology since these


form the backbone rings for the nucleobases of DNA and RNA. Neither of these molecules were


detected, and upper limits on their abundances determined instead. However, we did make a first


detection on Titan of cyclopropenylidene, a small cyclic hydrocarbon molecule that has previously


been detected in astrophysical sources but not in a planetary atmosphere.


This paper is organized as follows. In Section 2 we describe the observations and data reduction,


and in Section 3 the data modeling process. In Section 4 we show the results, followed by a discussion


in Section 5 and conclusions in Section 6.


2. OBSERVATIONS

Detection of Cyclopropenylidene on Titan 5


Observations of Titan were completed during March 2–4 2016 in Band 6 (ALMA Project Code


2015.1.00423.S) and on May 8th and 16th 2017 in Band 7 (ALMA Project Code 2016.A.00014.S),


see Table 1. In addition, part of a third dataset was used to obtain a CO J=2 _→_ 1 observation of


Titan in 2016 for retrieval of the disk-averaged temperature profile. In this independent dataset


(ALMA 2015.1.00512.S, observed April 1st 2016) Titan was observed as a flux calibration target for


an astrophysical investigation. Details of spectral windows (Spw) analyzed in this paper are given in


Table 2.


For dataset 2015.1.00423.S the data were provided in calibrated form (bandpass, phase and flux


calibrated), and subsequently post-processed using the Common Astronomy Software Applications


(CASA) package Version 4.7.2-REL (r39762, March 8th 2017) to provide rest-velocity correction


( `cvel` ) and ephemeris update ( `fixplanets` ). Lastly the data were concatenated and then deconvolved


(‘cleaned’) in CASA using the H¨ogbom algorithm, with a cell size of 0.1 _[′′]_ and a threshold of 10 mJy,


and a final restoring beam size of 0.87 _[′′]_ _×_ 0.72 _[′′]_


For the 2016 CO dataset (ALMA 2015.1.00512.S) the data were reduced in CASA Version 5.6.1-8


using the ALMA pipeline script prepared by the Joint ALMA Observatory staff, with the exception


of the removal of the `hifa` `fluxcalflag` task so that Titan’s atmospheric CO J=2 _→_ 1 emission line


at 230538 GHz was not flagged out. Data were deconvolved with the CASA `clean` task, using the


H¨ogbom algorithm with an image size = 128 _×_ 128 pixels, where pixels were set to 0.2 _[′′]_ _×_ 0.2 _[′′]_ . The


resulting synthesized beam had FWHM (Full Width to Half Maximum) = 0.92 _[′′]_ _×_ 0.81 _[′′]_, comparable


to Titan’s angular size at the time of observing.


The data reduction of the 2017 data (2016.A.00014.S) has already been described in Cordiner et al.


(2019). In addition, the bandpass solution interval was increased to 10 channels (2.44 MHz) to further


improve the S/N and aid in the detection of weak spectral lines (Yamaki et al., 2012).


Disk-averaged spectra from all observations were extracted from an integrated region defined by a


circular pixel mask set to contain 90% of Titan’s continuum flux, as in Lai et al. (2017).


3. MODELING

6 Nixon et al.


**Table** **1.** Details of ALMA Observations Of Titan


Date Start End _t_        - ∆ _v_ _[†]_ ∆ _f_ _[‡]_ Beam Position Angular Sub-Earth


(UT) (UT) (mins) (km s _[−]_ [1] ) (MHz) Size Angle Diameter ( _[′′]_ ) Latitude


_Project_ _Code_ _2015.1.00423.S_


02-Mar-2016 09:44 10:57 43 -28.37 24.13 0.87 _[′′]_ _×_ 0.75 _[′′]_ 89.145 _[◦]_ 0.71 26.28


02-Mar-2016 11:03 12:14 43 -28.34 24.01 0.91 _[′′]_ _×_ 0.73 _[′′]_ 95.155 _[◦]_ 0.71 26.28


04-Mar-2016 09:43 10:55 43 -32.18 27.37 0.87 _[′′]_ _×_ 0.64 _[′′]_ 79.815 _[◦]_ 0.71 26.28


_Project_ _Code_ _2015.1.00512.S_


01-Apr-2016 08:22 08:24 2 -22.32 17.12 0.92 _[′′]_ _×_ 0.81 _[′′]_ -83.247 _[◦]_ 0.74 26.24


_Project_ _Code_ _2016.A.00014.S_


08-May-2017 08:49 09:07 18 -19.28 22.24 0.18 _[′′]_ _×_ 0.15 _[′′]_ -80.950 _[◦]_ 0.77 26.41


16-May-2017 05:34 07:12 98 -13.61 15.97 0.28 _[′′]_ _×_ 0.19 _[′′]_ -73.549 _[◦]_ 0.77 26.48


        - Time spent on source.


_†_ =
Topocentric velocity (negative approaching).


_‡_ Frequency doppler shift (positive = blue-shifted).


Modeling was accomplished using the NEMESIS program (Irwin et al. 2008), which has previously


been successfully applied to model ALMA spectra of Titan (e.g. Cordiner et al. 2015; Molter et al.


2016; Serigano et al. 2016; Palmer et al. 2017; Lai et al. 2017; Teanby et al. 2018; Thelen et al. 2018,


2019a,b). The NEMESIS fitting algorithm uses a Bayesian optimal estimation technique as described


by Rodgers (2000), which seeks to minimize a ‘cost function’ similar to a _χ_ [2] figure of merit, which


penalizes the solution according to the square deviation of both the solution vector from the original _a_


_priori_ state, and also the model spectrum from the data. Marquart-Levenberg minimization is used to


descend a downhill trajectory of the cost function until satisfactory convergence is reached (solution


changing by _<_ 0.1%). ALMA spectra were rescaled to radiance units before being input to NEMESIS,


and then modeled using a weighted average of spectra calculated at 35 emission angles from disk


center to 1200 km altitude (3775 km radius), as described in Teanby et al. (2013), Appendix A.

Detection of Cyclopropenylidene on Titan 7


**Table** **2.** Details of observation spectral windows


Spw Freq. Range (MHz) ∆ _f_ _[†]_ (MHz) _n_ channels Molecule _f_ 0 (MHz) Transition


_Project_ _Code_ _2015.1.00423.S_


0 249570–250050 0.244 1920 c-C 4 H 4 N 2 249820 _J_ ”=39, _[b]_ _R_ -band


1 251260–251740 0.244 1920 c-C 5 H 5 N 251510 _J_ ”=41, _[a]_ _R_ -band


2 261900–262380 0.244 1920 c-C 4 H 4 N 2 262150 _J_ ”=41, _[b]_ _R_ -band


3 263090–263570 0.244 1920 c-C 5 H 5 N 263340 _J_ ”=43, _[a]_ _R_ -band


_Project_ _Code_ _2015.1.00512.S_


4 230322       - 230791 0.244 1920 CO 230538 _J_ = 2 _→_ 1


_Project_ _Code_ _2016.A.00014.S_


5 344212-346085 0.977 1920 CO 345796 _J_ = 3 _→_ 2


6 351281-352219 0.244 3840 C 2 H 3 CN — multiple


_†_ Channel spacing: spectral resolution is twice the channel spacing.


Spectral line data for most molecules were taken from the CDMS catalog (M¨uller et al. 2001, 2005,


`https://cdms.astro.uni-koeln.de)`, which is a compilation of transition information from the


published literature. These include: HCN (Ahrens et al. 2002; Fuchs et al. 2004; Cazzoli & Puzzarini


2005; Maiwald et al. 2000), CO (Winnewisser et al. 1997; Goorvitch 1994), CH 3 CN (Kukolich et al.


1973; Kukolich 1982; Boucher et al. 1977; Cazzoli & Puzzarini 2006), C 2 H 3 CN (M¨uller et al. 2008),


c-C 4 H 4 N 2 (Kisiel et al. 1999) and c-C 3 H 2 (Bogey et al. 1986; Vrtilek et al. 1987; Lovas 1992), in

cluding their isotopes. The rotational spectrum of c-C 5 H 5 N was calculated by refitting the primary


spectroscopic data from Heineking et al. (1986); Wlodarczak et al. (1988). For C 2 H 5 CN, we used a


new, more complete spectral line list that included not only rotations in the ground vibrational state,


but also in the first three vibrational states as described in Kisiel et al. (2020).


Collision-induced opacity for relevant molecular pairs was computed using published formalisms


and publicly-available FORTRAN codes as follows: N 2 –N 2 (Borysow, A. & Frommhold, L. 1986a);


N 2 –CH 4 (Borysow, A. & Tang, C. 1993); CH 4 –CH 4 (Borysow, A. & Frommhold, L. 1987); N 2 –H 2

8 Nixon et al.


(Borysow, A. & Frommhold, L. 1986b); CH 4 –H 2 (Borysow, A. & Frommhold, L. 1986c); H 2 –H 2


(Borysow, A. 1991).


3.1. _Temperature_ _Retrievals_


Firstly, the spectral lines of CO (Spw 4 & 5) were fitted using a model that allowed continuous


variation of the temperature profile between 100–500 km, while CO was fixed at a constant mixing


fraction of 49.6 ppm as determined by Serigano et al. (2016). The _a_ _priori_ temperature profile was


constructed by interpolating measurements from the Huygens Atmospheric Structure Instrument


(HASI) and Cassini radio science observations to Titan’s sub-observer latitude ( _∼_ 26 _[◦]_ ) below 100 km


(Fulchignoni et al. 2005; Schinder et al. 2012), and disk-averaged retrieval results from 2015 ALMA


observations of Titan (Thelen et al. 2018) were used at altitudes _>_ 100 km. Temperature _a_ _priori_


errors were set to 5 K in all atmospheric layers (0–1200 km), which allowed NEMESIS to obtain a fit


to the data while limiting artificial vertical structure (ill-conditioning) in the retrieved temperature


profile. Different frequency offsets from the line center sounded to different atmospheric depths


(altitudes, or pressure levels), as shown by the contribution functions in Fig. 1. The _a_ _priori_ and


final retrieved temperature profiles are also indicated.


3.2. _Spectral_ _windows_ _1_ _and_ _6:_ _Discovery_ _of_ _Cyclopropenylidene_


Next Spw 1 [1] was modeled to fit visible lines of known molecules: C 2 H 5 CN and C 2 H 3 CN. The


temperature profile was fixed at the earlier retrieved profile from Spw 4 for 2016. Various gas profile


types were investigated for the nitriles, adjusting the profiles to achieve best fits.


We first tried using minimalist ‘step’ functions (uniform volume mixing ratio above a fixed pressure


level, and zero below) for the vertical distribution of each gas. From previous experience (e.g. Cordiner


et al. 2015; Lai et al. 2017) we found that these worked well for trace (low abundance) nitriles in the


ALMA spectrum where there is little information that can be obtained about the vertical profile. For


C 2 H 3 CN we adopted a step altitude at 300 km. For C 2 H 5 CN, there was sufficient sensitivity to the


1 Window 0 was not included in this study. This region contains isotopic lines of CH 3 C 15 N, the analysis of which will


be reported elsewhere. See also recent work on this isotopologue by Iino et al. (2020)

Detection of Cyclopropenylidene on Titan 9


**Figure** **1.** Temperature retrievals for (a) CO 2 _→_ 1 in 2016 and (b) CO 3 _→_ 2 in 2017. Blue dot-dash lines:


_a_ _priori_ temperature profiles. Red solid line: retrieved profiles, with shaded (grey) retrieval error indicated.


Normalized contribution functions at different frequencies are also shown (thin solid black lines).


altitude of the step to affect the quality of the fit, which was determined from Spw 1 and thereafter


fixed at 250 km (see Appendix A). Initial fitting is shown in Fig. 2.


Having fitted the features of the known nitrile gases as well as possible, we proceeded to try adding


additional gases to the model in an attempt to detect any weak lines due to a new species, including


_i_ -butanenitrile and _n_ -butanenitrile (C 3 H 7 CN), propynenitrile (cyanodiacetylene, HC 5 N) and others,


using lines from the JPL catalog (Pickett et al. 1998, `https://spec.jpl.nasa.gov)` . In both Spw


1 and 6, we found a significant improvement to the model fit after introducing the gas c-C 3 H 2


(cyclopropenylidene) using spectroscopic lines from CDMS originally determined by Bogey et al.


(1986); Vrtilek et al. (1987) with a trial step function model with a step at 300 km, or higher.

10 Nixon et al.


**Figure** **2.** Best fit models for Spw 1 (a) and Spw 6 (b) using previously known gases only. Gas profiles


were step function models for C 2 H 5 CN (250 km) and C 2 H 3 CN (300 km). Residuals after fitting are shown


in panels (c) and (d). Frequencies have been corrected to rest velocity frame.


In Spw 1 two significant lines were detected at 251314.3 MHz (blend of 7 0 _,_ 7 _→_ 6 1 _,_ 6 and 7 1 _,_ 7 _→_ 6 0 _,_ 6


transitions) and 251527.3 MHz (6 2 _,_ 5 _→_ 5 1 _,_ 4 ), as shown in Fig. 3. We note that these two emissions


are the strongest expected spectral features of c-C 3 H 2 in Spw 1, and show close to the expected


proportions of relative intensities.


Similarly, in Spw 6, despite the noise level being higher in ALMA Band 7 than in Band 6 (Spw


1), we made two further detections of lines of c-C 3 H 2 : 351781.6 MHz (blend of the 10 1 _,_ 10 _→_ 9 0 _,_ 9 and


10 0 _,_ 10 _→_ 9 1 _,_ 9 doublet), 351965.9 MHz (blend of 9 1 _,_ 8 _→_ 8 2 _,_ 7 and 9 2 _,_ 8 _→_ 8 1 _,_ 7 doublet), see Fig. 4.


To further test the detection of c-C 3 H 2, we calculated a ∆ _χ_ [2] curve for different amounts of the gas


in a forward model, using a step function at 350 km. In this case, _χ_ [2] = Σ _ν_ [( _S_ _ν_ _−_ _I_ _ν_ ) _/σ_ _ν_ ] [2] is a metric

Detection of Cyclopropenylidene on Titan 11


**Figure** **3.** Modeling of Spw 1 showing expanded scale of regions where detected c-C 3 H 2 lines are present:


blend of 7 0 _,_ 7 _→_ 6 1 _,_ 6 and 7 1 _,_ 7 _→_ 6 0 _,_ 6 transitions at 251314.3 MHz, and 6 2 _,_ 5 _→_ 5 1 _,_ 4 single transition at 251527.3


MHz. Blue: C 2 H 5 CN model only. Red: model with C 2 H 5 CN and c-C 3 H 2 . Frequencies have been corrected


to rest velocity frame.


of spectral goodness-of-fit, where _S_ _ν_ is the data spectrum, _I_ _ν_ is the model spectrum, and _σ_ _ν_ is the


spectral noise estimate. However, note that this is not the same definition as the more commonly


used ‘reduced chi-square’ metric: _χ_ [2] _/n_, where _n_ is the number of spectral points minus the number of


degrees of freedom (model parameters). In this case therefore a good fit occurs when _χ_ [2] _≃_ _n_ (rather


than _χ_ [2] _/n ≃_ 1). We then define ∆ _χ_ [2] as the improvement to _χ_ [2] for various model trial abundances:

12 Nixon et al.


**Figure** **4.** Modeling of Spw 6 showing expanded scale of regions where detected c-C 3 H 2 lines are present:


blend of 10 1 _,_ 10 _→_ 9 0 _,_ 9 and 10 0 _,_ 10 _→_ 9 1 _,_ 9 doublet at 351781.6 MHz, and blend of 9 1 _,_ 8 _→_ 8 2 _,_ 7 and 9 2 _,_ 8 _→_ 8 1 _,_ 7


doublet at 351965.9 MHz. Blue: C 2 H 5 CN model only. Red: model with C 2 H 5 CN and c-C 3 H 2 . Frequencies


have been corrected to rest velocity frame.


∆ _χ_ [2] = _χ_ _q_ [2] _−_ _χ_ 0 [2], where _χ_ 0 [2] denotes the best-fit model in absence of the trial gas, and _χ_ [2] _q_ [is the same]


metric when an amount _q_ of the trial gas is present in the model (Teanby et al. 2009; Nixon et al.


2010, 2013a; Teanby et al. 2018). An improved fit results in a ∆ _χ_ [2] that decreases below zero, and


worsening fit results in ∆ _χ_ [2] that increases above zero.

Detection of Cyclopropenylidene on Titan 13


Results are shown in Fig. 5. A strong minimum is seen for a volume mixing ratio _q_ = 0 _._ 5 ppb in



Band 6, with ∆ _χ_ [2] reaching -21.24 indicating a _√_



21 _._ 24 =4.6 _σ_ significance to the result. For Band



7, a minimum is reached at mole fraction _q_ = 0 _._ 25 ppb with ∆ _χ_ [2] = -18.69 (4.3 _σ_ ). Both results are


significant, although the mixing ratio determined in each case is somewhat different (but consistent


within error bars, as shown later in Section 4). The combined significance of the detection is 6.3 _σ_ .


**Figure** **5.** Change in _χ_ [2] (∆ _χ_ [2] ) for various trial abundances of c-C 3 H 2 using a 350 km step model. (a)


Band 6, showing a 4.6- _σ_ minimum at a volume mixing ratio (VMR) of 0.50 ppb. (a) Band 7, showing a


4.3- _σ_ minimum at a volume mixing ratio (VMR) of 0.25 ppb.


Retrieved abundances for c-C 3 H 2 with various profiles are described in Section 4.


3.3. _Spectral_ _windows_ _2_ _and_ _3:_ _Search_ _for_ _pyridine_ _and_ _pyrimidine_


Fitting for Spw 2 & 3 was accomplished by initially using the retrieved temperature profile from


Spw 4, and also scaling a 250-km step model for C 2 H 5 CN and 300=km step model for C 2 H 3 CN. In

14 Nixon et al.


**Figure** **6.** Best fit models for Spw 2 and 3. In Spw 2 (panel (a), and residual in panel (c)) we see a single


strong line of C 2 H 5 CN at 262183.8 (29 4 _,_ 25 _→_ 28 4 _,_ 24 ), while in Spw 3 (panel (b), and residual in panel (d))


we detect C 2 H 3 CN at 263403.7 MHz (28 2 _,_ 27 _→_ 27 2 _,_ 26 ), and C 2 H 5 CN at 263516.2 MHz (30 2 _,_ 29 _→_ 29 2 _,_ 28 ).


Frequencies have been corrected to rest velocity frame.


addition, we included HCN which contributed a continuum slope in these windows due to the wings


of the strong 3 _→_ 2 line at 265886 MHz whose line center lies outside the bandpass. Then, 300-km


step model profiles models for c-C 5 H 5 N (Spw 2) and c-C 4 H 4 N 2 (Spw 3) were introduced, but resulted


in no significant improvement to the fit as measured by a reduced _χ_ [2] test. Instead, upper limits


for c-C 5 H 5 N and c-C 4 H 4 N 2 were determined instead (see Section 4.) The final fit for these spectral


windows is shown in Fig. 6.


4. RESULTS


4.1. _Retrieval_ _errors_

Detection of Cyclopropenylidene on Titan 15


The propagation of errors in the retrieval process follows the formalism described in Irwin et al.


(2008), and further elaborated in Section 3.5 of Nixon et al. (2008) (hereafter N08). This includes a


combination of _a_ _priori_ and measurement error (Eq. 1 of N08), with the error from the earlier tem

perature propagated as additional measurement error (Eq. 2 of N08). In addition, we needed to make


a further error allowance for apodization, which reduces independent information in the spectrum.


Due to the Hanning apodization applied during the Fourier Transform, neighboring spectral channels


become correlated, and the signal-to-noise in our retrieval will be overestimated by a factor equal


to the square root of the number of channels per resolution element - two channels per resolution


element for Hanning apodization. At the same time, there is a small gain of 1.095 from averaging


information across two successive correlated channels [2], so the final error bars are increased by a



factor _√_



2 _/_ 1 _._ 095 = 1 _._ 291. This factor has also been applied to correspondingly reduce the detection



significances ( _σ_ levels) throughout the paper.


4.2. _Cyclopropenylidene_


We initially fitted the c-C 3 H 2 emissions with a step function model, where the gas abundance was


zero below a ‘step’ altitude and a uniform value above. The overall profile was then scaled to achieve


a best fit. The effect of changing the altitude of the step was also explored, since lower steps increased


pressure broadening of the lines that became greater than the observed line widths.


We also investigated a more realistic gas profile, with an abundance decreasing downwards to


a condensation altitude, by using a four-parameter gradient model. This model was defined by


two ( _p, q_ ) (pressure, mixing ratio) co-ordinates defining a straight-line, logarithmically decreasing


VMR between ( _p_ _u_ _, q_ _u_ ) (upper point) and ( _p_ _l_ _, q_ _l_ ) (lower point). Above _p_ _u_ the VMR was assumed


constant at _q_ _u_ and below _p_ _l_ the VMR dropped to zero. The upper pressure level was set to be


_p_ _u_ = (5 _._ 0 _±_ 2 _._ 0) _×_ 10 _[−]_ [11] bar, or approximately 1100 km, the altitude of the INMS measurements


of the C 3 H 2 H [+] (protonated) ion. The initial value for the abundance at this altitude was set to be


_q_ _u_ = (3 _._ 4 _±_ 1 _._ 0) _×_ 10 _[−]_ [6] in line with the INMS ion measurements (Vuitton et al. 2007). The initial


2 ALMA technical notes: https://help.almascience.org/index.php?/Knowledgebase/Article/View/29

16 Nixon et al.


value for the lower point was set to be: _p_ _l_ = (1 _._ 0 _±_ 0 _._ 5) _×_ 10 _[−]_ [4] bar, _q_ _l_ = (2 _._ 0 _±_ 1 _._ 9) _×_ 10 _[−]_ [9], a pressure


level corresponding to approximately 300 km, and allowing a lenient variation of abundance.


Scaled step function solutions for c-C 3 H 2 from Window 1 (Band 6) and Window 6 (Band 7) are


shown in Fig. 7, along with best fit gradient model profiles. Numerical results are given in Table 3.


Retrievals for cyclopropenylidene showed low sensitivity to the altitude of the step, with a weak


minimum at 300–400 km. The resulting abundances and columns were slightly different in 2016 and


2017. For a step function of 350 km we obtained a VMR of 0.50 _±_ 0.14 ppb and column abundance of


3.5 _×_ 10 [12] cm _[−]_ [2] in 2016, but somewhat lower VMR (0.28 _±_ 0.08) and column abundance (1.5 _×_ 10 [12] )


in 2017. This implies either (a) that the global abundance had decreased from 2016 to 2017, or, (b)


if the real abundance was constant, then a mean value of 0.33 _±_ 0.07 ppb for the 350 km step profile.


**Table** **3.** Retrieved column abundances and volume mixing ratios (VMRs) at 600 km for different c-C 3 H 2


models.


Band Species Model _χ_ [2] /n VMR Col. Abund.


(ppb @ 600 km) (molecule cm _[−]_ [2] )


6 c-C 3 H 2 Gradient model 0.9843 3.788 2.649 _×_ 10 [12]


6 c-C 3 H 2 400 km step 0.9839 1.012 _±_ 0.386 2.824 _×_ 10 [12]


6 c-C 3 H 2 350 km step 0.9838 0.495 _±_ 0.142 3.487 _×_ 10 [12]


6 c-C 3 H 2 300 km step 0.9841 0.278 _±_ 0.054 4.875 _×_ 10 [12]


7 c-C 3 H 2 Gradient model 0.9791 1.867 1.197 _×_ 10 [12]


7 c-C 3 H 2 400 km step 0.9789 0.537 _±_ 0.223 1.175 _×_ 10 [12]


7 c-C 3 H 2 350 km step 0.9800 0.279 _±_ 0.084 1.541 _×_ 10 [12]


7 c-C 3 H 2 300 km step 0.9829 0.122 _±_ 0.031 1.702 _×_ 10 [12]

Detection of Cyclopropenylidene on Titan 17


**Figure** **7.** Retrieved profiles of c-C 3 H 2 for different models. (a) Band 6 data, 2016. (b) Band 7 data, 2017.


Retrieved parameters for the gradient model retrievals in 2016 and 2017 are shown in Table 4, along


with parameters for a weighted mean profile of both years.


4.3. _Pyridine_ _and_ _pyrimidine_


Upper limits for c-C 5 H 5 N and c-C 4 H 4 N 2 were determined using the ∆ _χ_ [2] method outlined for c

C 3 H 2 in Section 3.2. In this case, the 1, 2 and 3- _σ_ upper limits are indicated at the trial abundances


where the ∆ _χ_ [2] reaches +1, +4, and +9 respectively (Nixon et al. 2012). Results are shown in Fig. 8


and Table 5. A shallow minimum was detected for c-C 5 H 5 N, however the spectrum does not show


obvious emissions consistent with expected spectral lines, therefore we believe this to be likely due


to random spectral noise (although worthy of a more sensitive follow-up observation to be sure).

18 Nixon et al.


**Table** **4.** Retrieved parameters for c-C 3 H 2 gradient model fits


_p_ _u_ (bar) _q_ _u_ _p_ _l_ (bar) _q_ _l_


_Band_ _6_


_a_ _priori_ (5.0 _±_ 2.0) _×_ 10 _[−]_ [11] (3.4 _±_ 1.0) _×_ 10 _[−]_ [6] (1.0 _±_ 0.5) _×_ 10 _[−]_ [4] (2.0 _±_ 1.9) _×_ 10 _[−]_ [9]


Retrieved (4.4 _±_ 2.2) _×_ 10 _[−]_ [11] (3.1 _±_ 1.2) _×_ 10 _[−]_ [6] (4.7 _±_ 2.9) _×_ 10 _[−]_ [5] (5.4 _±_ 3.7) _×_ 10 _[−]_ [11]


_Band_ _7_


_a_ _priori_ (5.0 _±_ 2.0) _×_ 10 _[−]_ [11] (3.4 _±_ 1.0) _×_ 10 _[−]_ [6] (1.0 _±_ 0.5) _×_ 10 _[−]_ [4] (2.0 _±_ 1.9) _×_ 10 _[−]_ [9]


Retrieved (4.3 _±_ 2.2) _×_ 10 _[−]_ [11] (3.1 _±_ 1.2) _×_ 10 _[−]_ [6] (3.8 _±_ 2.3) _×_ 10 _[−]_ [5] (2.1 _±_ 1.7) _×_ 10 _[−]_ [11]


_Band_ _6_ _&_ _7_


Combined (4.3 _±_ 1.6) _×_ 10 _[−]_ [11] (3.1 _±_ 0.8) _×_ 10 _[−]_ [6] (4.1 _±_ 1.8) _×_ 10 _[−]_ [5] (2.6 _±_ 1.5) _×_ 10 _[−]_ [11]


**Table** **5.** Upper limits for undetected nitrogen heterocycle molecules in Titan’s atmosphere


Name p ( _µ_ bar) Freq. (MHz) NEF _[†]_ (mJy) 1- _σ_ VMR _[‡]_ 2- _σ_ VMR _[‡]_ 3- _σ_ VMR _[‡]_


c-C 4 H 4 N 2 0.020 262143 0.34 0.663 0.854 1.042


c-C 5 H 5 N 0.020 263331 0.29 1.046 1.153 1.356


_†_ Noise Equivalent Flux. _‡_ Volume Mixing Ratio (mole fraction) in ppb.


5. DISCUSSION


5.1. _Cyclopropenylidene_


The molecule cyclopropenylidene (c-C 3 H 2 ) was discovered in the interstellar medium (ISM) by


Thaddeus et al. (1985) through extensive laboratory and theoretical analysis to unearth the origin of


several prominent, but previously unidentified lines seen on radio astronomical spectra. Following this


discovery, the molecule has been found to be ubiquitous in the galaxy (Fosse et al. 2001) and easily


detectable due to the relatively large dipole of 3.43(2) D (Kanata et al. 1987) caused by the unpaired


electrons on the bivalent carbon atom. In addition, c-C 3 H 2 is a light molecule with a small partition


function, which also works in favor of detection. One of its linear isomers, propadienylidene (H 2 CCC,

Detection of Cyclopropenylidene on Titan 19


**Figure** **8.** Upper limit determination for nitrogen heterocycle molecules. (a) Data (black) and example


spectrum (cyan) for c-C 4 H 4 N 2 showing missing spectral band location. (b) ∆ _χ_ [2] curve for various trial


abundances for c-C 4 H 4 N 2 . (c) Data (black) and example spectrum (magenta) for c-C 5 H 5 N showing missing


spectral band location. (d) ∆ _χ_ [2] curve for various trial abundances for c-C 5 H 5 N. Vertical dashed lines on


(b) and (d) indicate the 1, 2, and 3- _σ_ upper abundance limits at ∆ _χ_ [2] = +1 _,_ +4 _,_ +9.


see Fig. 9) has since been detected in the ISM (Cernicharo et al. 1991) while propynylidene (HCCCH)


has not been observed. Note that propadienylidene is higher in energy than cyclopropenylidene, and


therefore metastable, so that the observed ratio of ten or more for c-C 3 H 2 /H 2 CCC is expected.


The Cassini INMS instrument measured peaks at _m/z_ 38 and 39 in samples of Titan’s upper


atmosphere that were attributed to the presence of C 3 H [+] 2 [and] [various] [isomers] [of] [C] [3] [H] [+] 3 [(][Vuitton]


et al. 2006; Vuitton et al. 2007). Although the molecular structure was not directly measurable,

20 Nixon et al.


modeling of the mass spectrum implied ion number densities of 0.0016 cm _[−]_ [3] (C 3 H [+] 2 [),] [34] [cm] _[−]_ [3] [(c-]


C 3 H [+] 3 [)] [and] [1.6] [cm] _[−]_ [3] [(l-C] [3] [H] [+] 3 [)] [respectively.] [Determining] [the] [ratio] [of] [l-C] [3] [H] [+] 3 [/c-C] [3] [H] [+] 3 [was] [deemed] [to]


be of major importance by Vuitton et al. (2007) (and the subject of laboratory investigation), since


the linear propargyl ion is able to react to form heavier species, including possibly benzene (Wilson


& Atreya 2004), while the cyclopropenylidene ion is essentially a terminal species, leading to c-C 3 H 2 .

# C H C H C H C H
### 3 2 3 4 3 6 3 8

#### Propadienylidene Propyne Propene Propane

#### Cyclopropenylidene Propadiene Cyclopropane


**Figure** **9.** Structures of C 3 H _x_ molecules. Green lettering = detected in Titan’s atmosphere. Red lettering


= undetected. Molecule graphics: wikimedia commons.


Various mechanisms have been proposed for the formation of c-C 3 H 2 and it is not clear at present


which mechanisms are the most important. In the original work of Thaddeus et al. (1985) on


the ISM detection, cyclopropenylidene was produced by dissociative electron recombination of the


cyclopropenylium cation, c-C 3 H [+] 3 [:]


c _−_ C 3 H 3+ + e _−_ _→_ c _−_ C 3 H 2 + H (1)


while c-C 3 H [+] 3 [is] [produced] [from] [C] [2] [H] [2] [in] [two] [steps.] [First] [the] [fast] [ion-molecule] [reaction:]

Detection of Cyclopropenylidene on Titan 21


C [+] + C 2 H 2 _→_ c _−_ C 3 H [+] + H (2)


followed by the slower radiative association (hydrogenation):


c _−_ C 3 H [+] + H 2 _→_ c _−_ C 3 H [+] 3 (3)


Alternatively the C 3 H [+] 3 [ion] [has] [been] [proposed] [to] [be] [produced] [from] [acetylene] [via] [many] [other]


possible ion molecule reactions by Vuitton et al. (2019), for example:


CH [+] 3 [+ C] [2] [H] [2] _[→]_ [C] [3] [H] [+] 3 [+ H] [2] (4)


C 2 H [+] 5 [+ C] [2] [H] [2] _[→]_ [C] [3] [H] [+] 3 [+ CH] [4] (5)


Walch (1995); Guadagnini et al. (1998) investigated the reactions of CH( _X_ [2] Π) (methylidyne) with


C 2 H 2, predicting that various isomers of both C 3 H 3 and C 3 H 2 can result. From this point, several


outcomes are possible: the products can stabilize into a less-reactive species, such as c-C 3 H 2, or else


can undergo further reactions to form heavier hydrocarbons. In particular, it was noted that both


C 3 H 3 and C 3 H 2 can dimerize, forming benzene (C 6 H 6 ) and _para_ -benzene (C 6 H 4 ) respectively, and


therefore C 3 H 3 and C 3 H 2 are important stepping stones to polycyclic aromatic hydrocarbons (PAHs).


The work of Canosa et al. (1997) further clarified pathways to formation of C 3 H 2 from reactions of


the methylidine radical (CH) with unsaturated C 2 H _x_ hydrocarbons, such as:


CH + C 2 H 2 _→_ C 3 H 2 + H _,_ or (6)


CH + C 2 H 4 _→_ C 3 H 3 + H 2 (7)


In the above reactions, CH is envisaged to add to the carbon-carbon double or triple bond. C 3 H 3


can be converted to C 3 H 2 by hydrogen loss through photodissociation (e.g. H´ebrard et al. 2013):


C 3 H 3 + h _ν_ _→_ C 3 H 2 + H (8)

22 Nixon et al.


The C 3 H radical may also result from the methylidine insertion reactions, which can lead to C 3 H 2


via several steps, first charge transfer:


H [+] + C 3 H _→_ C 3 H [+] + H (9)


followed by hydrogenation (3) and then dissociative recombination (1) as before. Subsequently,


Canosa et al. (2007) showed that C 2 reactions may also be important, e.g,:


C 2 + C 3 H 8 _→_ C 3 H 2 + C 2 H 6 (10)


as used in the photochemical model of Krasnopolsky (2009). The branching ratios between aliphatic


and aromatic pathways in many of these reactions, especially at low temperatures, are important


and often poorly known.


In Fig. 10 we compare our retrieved gradient models to photochemical model predictions of H´ebrard


et al. (2013) and Vuitton et al. (2019). In fact, the models arrive at a column abundance rather similar


to our retrieved amount of _∼_ 10 [12] cm _[−]_ [2] . It is difficult to pronounce whether the differences in the


vertical profile shape are significant or not, since we have very little constraint on this at present.


5.2. _Pyridine_ _and_ _pyrimidine_


The astrobiologically important species pyridine (c-C 5 H 5 N) and pyrimidine (c-C 4 H 4 N 2 ) are


nitrogen-containing heterocyclic ring molecules resembling a benzene ring with either one or two


of the C-H members replaced by a nitrogen atom. Pyrimidine in particular is of significant biological


importance since it forms the backbone ring structure of several key biological molecules - specifi

cally the nucleobases uracil (in RNA), cytosine (in RNA and DNA) and thymine (in DNA). These


molecules can potentially be formed from pyrimidine after the chemical substitution of functional


groups (-NH 2, -CH 3 and =O) in place of hydrogen, as indicated in Fig. 11. Indeed, laboratory ex

periments (Nuevo et al. 2014) have shown that UV irradiation of pyrimidine in the presence of H 2 O,


CH 4, CH 3 OH and NH 3 can form uracil and cytosine - but not the more complex thymine - a possible


clue as to why thymine appears only in DNA but not RNA, and further evidence that RNA may

Detection of Cyclopropenylidene on Titan 23


**Figure** **10.** Retrieved gas abundance profiles for c-C 3 H 2 in Band 6 and Band 7 using the gradient model


compared to published photochemical models. Column abundances (N) are in molecule cm _[−]_ [2] .


have preceded DNA. Similar processes may be taking place in space, including the atmosphere of


Titan. Indeed, laboratory simulations of Titan’s atmosphere, using multiple experimental techniques


such as GC-MS (gas chromatograph mass spectroscopy), pyrolysis mass spectroscopy, Raman and


reflectance spectroscopy etc have been successful in positively identifying the nitrogen heterocycles


(Khare et al. 1984; Ehrenfreund et al. 1995).


To date, neither pyridine nor pyrimidine have been detected in astrophysical sources, despite


searches in molecular clouds (Simon & Simon 1973; Kuan et al. 2003, 2004; Cordiner et al. 2017;


McGuire et al. 2018) and in the envelopes of evolved stars (Charnley et al. 2005), although pyridine


and quinoline (2-membered N-heterocycle rings) derivatives have been found in meteorite samples


(e.g. Stoks & Schwartz 1982; Martins 2018). Peeters et al. (2005) have shown that these molecules

24 Nixon et al.


Known to exist on Titan Potentially exist in Titan’s atmosphere


**Benzene** **Pyridine** **Pyrimidine**


**Thymine** **Cytosine**


hydrogen


carbon

nitrogen



Addition of functional

side-groups


**Uracil**



oxygen



**Nucleobases of DNA (2 of 4)**



**Nucleobases of RNA (2 of 4)**



**Figure** **11.** Importance of nitrogen heterocycle molecules such as pyridine and pyrimidine to astrobiology:


detection of such species would indicate a possible route to creation of nucleobases of DNA and RNA.


Individual molecule graphics from wikimedia commons.


are relatively unstable against UV irradiation compared to benzene, but could survive for 10–100s


of years in dense clouds where UV flux is attenuated, and therefore potentially in Titan’s thick


atmosphere.


The potential presence of the nitrogen heterocyclic molecules pyridine and pyrimidine in Titan’s


atmosphere may be inferred from the detection of C 5 H 5 NH [+] and C 4 H 4 N 2 H [+] ions in Cassini mass


spectra (Vuitton et al. 2007) at _m/z_ 80 and 81 (seen in their Fig. 2). As with the hydrocarbons, the


elucidation of structure from the mass spectra alone is not possible, therefore for example protonated


forms of branched acyclic molecules such as penta-2,4-dienenitrile or 2-methylene-3-butenenitrile


could be responsible for the mass 80 peak instead.

Detection of Cyclopropenylidene on Titan 25


Formation pathways for the N-heterocycles are currently quite uncertain. For example, Fondren


et al. (2007) suggest that efficient ion-molecule association reactions with HCN could form pyridine


and pyrimidine from smaller ions:


C 4 H [+] 4 [+ HCN] _[ →]_ [C] [5] [H] [5] [N] [+] [ + h] _[ν]_ (11)


C 3 H 3 N [+] + HCN _→_ C 4 H 4 N [+] 2 [+ h] _[ν]_ (12)


A more exotic mechanism for the formation of pyridine through ring expansion of pyrrole by methyli

dyne has been observed in the gas phase by Soorkia et al. (2010):


CH + C 4 H 5 N _→_ C 5 H 5 N + H (13)


More recently, Balucani et al. (2019) has investigated a pathway to pyridine that begins with an


attack on C 6 H 6 by N( [2] D), leading to a chain of unstable intermediate products that may decay to


c-C 5 H 5 N.


The relative importance of these various channels is highly uncertain at the present time, leading to


difficulties in incorporating these molecules into photochemical models. For example Krasnopolsky


(2009) included just one hypothetical formation pathway for pyridine by the radical-molecule reaction:


C 3 N + C 2 H 6 _→_ C 5 H 5 N + H (14)


while in (Loison et al. 2015) only the aliphatic isomer C 2 H 5 C 3 N is discussed.


Our analysis indicates 2- _σ_ upper limits of _∼_ 1 _._ 15 ppb and _∼_ 0 _._ 85 ppb for c-C 5 H 5 N and c-C 4 H 4 N 2


respectively (constant profile above 300 km), which may in future be used to place some constraints


on photochemical models as these become more sophisticated and add more detailed treatment of


cyclic molecule formation.


6. CONCLUSIONS


We report the first detection of c-C 3 H 2 (cyclopropenylidene) on Titan in two datasets: Band 6


spectra from 2016 and Band 7 data from 2017, detecting at least 2 emissions in each case. The

26 Nixon et al.


derived abundances are 0.50 _±_ 0.14 ppb in 2016 and 0.28 _±_ 0.08 in 2017 for a 350-km step model,


which are in agreement at the margins of their 1- _σ_ errors, or alternatively may indicate a real decrease


in abundance. Derived column abundances are 3–5 _×_ 10 [12] cm _[−]_ [2] in 2016 and 1–2 _×_ 10 [12] cm _[−]_ [2] in 2017,


in good agreement with photochemical models. This presence of cyclopropenylidene is of substantial


significance to Titan’s atmospheric chemistry, since insertion reactions of methylidyne (CH) into


C 2 H 2 and other unsaturated hydrocarbons can lead to formation of C 3 H 2 and C 3 H 3 isomers. These


in turn may be stepping stones to benzene and _para_ -benzene, and larger aromatic PAH molecules.


Following preliminary evidence from Cassini mass spectra, we also searched for the N-heterocyclic


molecules pyridine and pyrimidine in Titan’s atmosphere, with a null result. By modeling of ALMA


spectra at 262–263 GHz we have determined 2- _σ_ upper limits of 1.15 and 0.85 ppb for c-C 5 H 5 N and


c-C 4 H 4 N 2 respectively. We have detected ground state lines of C 2 H 3 CN and C 2 H 5 CN as previously


seen in Titan’s atmosphere, and also vibrationally excited rotational transitions of C 2 H 5 CN. The


C 2 H 5 CN emissions are well-fitted using a 250 km ‘step’ model as noted by previous authors, and


we find a best-fit abundance of 5.0 _±_ 0.1 ppb similar to previous work. Our modeling indicates


that there is unlikely to be substantial amounts of C 2 H 5 CN below 250 km, in contrast to existing


photochemical models.


The discovery of cyclopropenylidene for the first time in a dense planetary atmosphere therefore


opens up new directions for research in the chemistry of the reducing atmospheres of the outer


planets, and especially PAH and haze formation.


ACKNOWLEDGMENTS


C.A.N. and M.A.C. received support for this work through NASA’s Solar System Observations


(SSO) Program. C.A.N. and A.E.T. were also funded by NASA’s Astrobiology Program. M.A.C.


was supported by the National Science Foundation under Grant No. AST-1616306. PGJI and NAT


are funded by the UK Science and Technology Facilities Council.


This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00423.S,


2015.1.00512.S, 2016.A.00014.S. ALMA is a partnership of ESO (representing its member states),

Detection of Cyclopropenylidene on Titan 27


NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and


KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observa

tory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is


a facility of the National Science Foundation operated under cooperative agreement by Associated


Universities, Inc.


APPENDIX


A. PROPIONITRILE


A.1. _Modeling_


In Spw 1, sufficiently strong lines of C 2 H 5 CN were seen that there was noticeable pressure-induced


line broadening, allowing an optimum altitude for a step function model to be determined. Fig. 12


shows the effect of changing the step function altitude for C 2 H 5 CN.


The goodness of fit for all models is compared in Table 6. The best-fit solution for C 2 H 5 CN is a


step function at 250 km with a uniform VMR of 5.0 _±_ 0.07 ppb and column abundance 2.2 _×_ 10 [14]


cm _[−]_ [2] . A comparison of retrieved profiles can be seen in Fig. 13(a).


**Table** **6.** Retrieved column abundances and volume mixing ratios (VMRs) at 600 km for different model


types for C 2 H 5 CN.


Species Model _χ_ [2] _/n_ VMR Col. Abund


(ppb @ 600 km) (molecule cm _[−]_ [2] )


C 2 H 5 CN Gradient model 1.051 31.957 1.3475 _×_ 10 [14]


C 2 H 5 CN 300 km step 1.035 8.545 _±_ 0.252 1.5004 _×_ 10 [14]


C 2 H 5 CN 250 km step 1.002 5.040 _±_ 0.095 2.2378 _×_ 10 [14]


C 2 H 5 CN 200 km step 1.159 2.749 _±_ 0.030 3.5703 _×_ 10 [14]

28 Nixon et al.


**Figure** **12.** Spectral fitting of strong C 2 H 5 CN lines in Spw 1 using ‘step’ models at different altitudes


(panels (a) and (b)), and residual after fitting (panels (c) and (d)). Frequencies have been corrected to rest


velocity frame.


**Table** **7.** Retrieved parameters for gradient model fits


Gas _p_ _u_ (bar) _q_ _u_ _p_ _l_ (bar) _q_ _l_


C 2 H 5 CN _a_ _priori_ (5 _._ 0 _±_ 2 _._ 0) _×_ 10 _[−]_ [11] (5 _._ 0 _±_ 1 _._ 0) _×_ 10 _[−]_ [7] (1 _._ 0 _±_ 0 _._ 5) _×_ 10 _[−]_ [4] (2 _._ 0 _±_ 1 _._ 9) _×_ 10 _[−]_ [9]


C 2 H 5 CN Retrieved (4 _._ 7 _±_ 2 _._ 4) _×_ 10 _[−]_ [11] (4 _._ 8 _±_ 1 _._ 3) _×_ 10 _[−]_ [7] (1 _._ 1 _±_ 0 _._ 6) _×_ 10 _[−]_ [4] (4 _._ 3 _±_ 0 _._ 9) _×_ 10 _[−]_ [9]


A gradient model was also tested, using similar initial conditions to those used for c-C 3 H 2, as


described in Section 3.2, except that the initial abundance at the 1100 km altitude was set to


_q_ _u_ = (5 _._ 0 _±_ 1 _._ 0) _×_ 10 _[−]_ [7] in line with the INMS measurement of C 2 H 5 CNH [+] . Initial and retrieved


parameters for the C 2 H 5 CN gradient model are given in Table 7.

Detection of Cyclopropenylidene on Titan 29


**Figure** **13.** (a) Retrieved model profiles for C 2 H 5 CN. (b) Comparison between gradient model for C 2 H 5 CN


and published photochemical model profiles.


A list of the ground-state and vibrationally excited lines detected in Spw 1 is given in Table 8.


In the next section the implications of the results for C 2 H 5 CN are discussed.


A.2. _Discussion:_ _C_ 2 _H_ 5 _CN_


The ion C 2 H 5 CNH [+] was inferred from early Cassini INMS mass spectra of Titan’s upper atmo

sphere (e.g. Vuitton et al. 2007), and the first identification of ethyl cyanide (propionitrile) in the


neutral atmosphere was achieved using ALMA by Cordiner et al. (2015). Nitrile molecules have a


large molecular dipole ( _∼_ 4.0 D for small nitriles, equivalent to 70% of an equivalent ionic bond),


causing them to have strong rotational spectra. This was undoubtedly a reason why methyl cyanide


(acetonitrile, CH 3 CN) was first detected at sub-millimeter wavelengths (Bezard et al. 1992), and


despite intensive searching has yet to be detected in the infrared (Nixon et al. 2010).

30 Nixon et al.


**Table** **8.** Lines of C 2 H 5 CN detected in Spw 1


Species Freq. (MHz) Transition _[a]_ _v_ _[b]_ _E_ _u_ (K)

C 2 H 5 CN 251271.3 30 6 _,_ 24 -30 5 _,_ 25 0 240
C 2 H 5 CN 251278.7 28 18 _,_ -27 18 _,_ 0 533
C 2 H 5 CN 251284.2 28 16 _,_ -27 16 _,_ 2 776
C 2 H 5 CN 251289.1 28 12 _,_ -27 12 _,_ 1 624
C 2 H 5 CN 251297.1 28 11 _,_ -27 11 _,_ 1 600
C 2 H 5 CN 251302.3 28 13 _,_ -27 13 _,_ 1 651
C 2 H 5 CN 251331.4 28 14 _,_ -27 14 _,_ 1 680
C 2 H 5 CN 251335.9 28 10 _,_ -27 10 _,_ 1 577
C 2 H 5 CN 251365.8 28 19 _,_ -27 19 _,_ 0 573
C 2 H 5 CN 251373.2 28 15 _,_ -27 15 _,_ 1 712
C 2 H 5 CN 251404.3 28 6 _,_ 23 -27 6 _,_ 22 3 751
C 2 H 5 CN 251409.4 28 6 _,_ 22 -27 6 _,_ 21 3 751
C 2 H 5 CN 251419.7 28 9 _,_ -27 9 _,_ 1 557
C 2 H 5 CN 251425.6 28 16 _,_ -27 16 _,_ 1 744
C 2 H 5 CN 251459.0 28 20 _,_ -27 20 _,_ 0 616
C 2 H 5 CN 251487.2 28 17 _,_ -27 17 _,_ 1 780
C 2 H 5 CN 251501.0 28 5 _,_ 24 -27 5 _,_ 23 0 203
C 2 H 5 CN 251517.7 28 8 _,_ -27 8 _,_ 1 539
C 2 H 5 CN 251520.6 28 6 _,_ 23 -27 6 _,_ 22 2 524
C 2 H 5 CN 251522.9 28 6 _,_ 22 -27 6 _,_ 21 2 524
C 2 H 5 CN 251558.1 28 21 _,_ -27 21 _,_ 0 661
C 2 H 5 CN 251560.2 28 6 _,_ 23 -27 6 _,_ 22 1 509
C 2 H 5 CN 251561.2 28 6 _,_ 22 -27 6 _,_ 21 1 509
C 2 H 5 CN 251570.0 31 6 _,_ 26 -31 5 _,_ 27 0 253
C 2 H 5 CN 251607.1 28 5 _,_ 23 -27 5 _,_ 22 0 202
C 2 H 5 CN 251652.3 28 5 _,_ 24 -27 5 _,_ 23 2 511
C 2 H 5 CN 251661.0 10 4 _,_ 7 -9 3 _,_ 6 0 41
C 2 H 5 CN 251668.8 28 4 _,_ 25 -27 4 _,_ 24 0 193
C 2 H 5 CN 251691.0 28 5 _,_ 24 -27 5 _,_ 23 3 739
C 2 H 5 CN 251713.6 28 5 _,_ 23 -27 5 _,_ 22 2 511
C 2 H 5 CN 251728.7 10 4 _,_ 6 -9 3 _,_ 7 0 41


_a_ Rotational energy levels are labeled with _J, K_ _a_ _, K_ _c_, and omission of _K_ _c_ identifies a degenerate spectroscopic


doublet in which _K_ _c_ = _J_ _−_ _K_ _a_ and _K_ _c_ = _J_ _−_ _K_ _a_ + 1.


_b_ Vibrational species: 0: ground state (Brauer et al. 2009), 1: _v_ 13 = 1 (Kisiel et al. 2020), 2: _v_ 21 = 1 (Kisiel


et al. 2020), 3: _v_ 20 = 1 (Daly et al. 2013).

Detection of Cyclopropenylidene on Titan 31


The detection of C 2 H 5 CN by Cordiner et al. (2015) in ALMA Band 6 data at _∼_ 220–240 GHz was


close to the region observed in this work, with an abundance of _∼_ 9 ppb (300 km step model) derived


from disk-averaged observations in July 2012. Several years later, follow-up work by Palmer et al.


(2017) also in Band 6 near 230 GHz determined a disk-average abundance of 7.2 _±_ 0.29 ppb for early


2014, while Lai et al. (2017) measured 7.37 _±_ 0.32 ppb from April 2015 data in Band 7 near 348 GHz.


Our measurement of 8.5 _±_ 0.2 ppb (using a directly comparable 300 km step model) based on 2016


data falls in the mid-range of the previous measurements, and indicates that the global abundance


was not changing substantially in this period.


The vertical profile of propionitrile (as a global average) remains problematic. As pointed out by


Cordiner et al. (2015) and also by Lai et al. (2017), photochemical models typically over-estimate


the abundance of this gas compared to retrieved abundances (see Fig. 13 (b)), especially in the lower


stratosphere, indicating a possible missing loss mechanism. The model which best replicates the


data is that of Willacy et al. (2016) (Model C), which includes loss by condensation, sedimentation


and haze formation. Despite the abundance at 100–300 km appearing significantly too high, the


column abundance of _∼_ 10 [14] cm _[−]_ [2] is of the same order of magnitude as our results. Other models


(Loison et al. 2015; Vuitton et al. 2019) substantially overestimate the column by a factor of _∼_ 100,


by continuing significant gas mixing fractions down to the tropopause.


REFERENCES



Ahrens, V., Lewen, F., Takano, S., et al. 2002, Z.
Naturforschung A, 57, 669

Baars, J. M. 2002, IEEE Xplore

Balucani, N., Pacifici, L., Skouteris, D., et al.
2019, Lecture Notes in Computer Science, 316

Bell, J. M., Bougher, S. W., Waite, J. H., et al.
2010a, Journal of Geophysical Research
(Planets), 115, E12002
Bell, J. M., Bougher, S. W., Waite, Jr., J. H.,
et al. 2010b, Journal of Geophysical Research
(Planets), 115, 12018
Bezard, B., Marten, A., & Paubert, G. 1992,

IAUC



B´ezard, B., Yelle, R. V., & Nixon, C. A. 2014,
Titan, 158
Bogey, M., Demuynck, C., & Destombes, J. 1986,
Chemical Physics Letters, 125, 383
Borysow, A. 1991, Icarus, 92, 273
Borysow, A., & Frommhold, L. 1986a, The
Astrophysical journal, 311, 1043
—. 1986b, The Astrophysical journal, 303, 495
—. 1986c, The Astrophysical journal, 304, 849
—. 1987, The Astrophysical journal, 318, 940
Borysow, A., & Tang, C. 1993, Icarus, 105, 175
Boucher, D., Burie, J., Demaison, J., et al. 1977,
Journal of Molecular Spectroscopy, 64, 290

32 Nixon et al.



Brauer, C. S., Pearson, J. C., Drouin, B. J., & Yu,
S. 2009, The Astrophysical Journal Supplement
Series, 184, 133
Broadfoot, A., Sandel, B. R., Shemansky, D.,
et al. 1981, Science, 212, 206
Canosa, A., P´aramo, A., Picard], S. D. L., &
Sims, I. R. 2007, Icarus, 187, 558
Canosa, A., Sims, I. R., Travers, D., Smith, I.
W. M., & Rowe, B. R. 1997, ˚a, 323, 644
Cazzoli, G., & Puzzarini, C. 2005, Journal of
Molecular Spectroscopy, 233, 280
—. 2006, Journal of Molecular Spectroscopy, 240,
153

Cernicharo, J., Gottlieb, C. A., Guelin, M., et al.
1991, The Astrophysical Journal, 368, L39
Charnley, S. B., Kuan, Y.-J., Huang, H.-C., et al.
2005, Advances in Space Research, 36, 137
Cordiner, M. A., Charnley, S. B., Kisiel, Z.,
McGuire, B. A., & Kuan, Y.-J. 2017, The
Astrophysical Journal, 850, 187
Cordiner, M. A., Nixon, C. A., Charnley, S. B.,
et al. 2018, The Astrophysical Journal, 859, L15
Cordiner, M. A., Teanby, N. A., Nixon, C. A.,
et al. 2019, The Astronomical Journal, 158, 76
Cordiner, M. A., Palmer, M. Y., Nixon, C. A.,
et al. 2015, ApJL, 800, L14
Coustenis, A., Salama, A., Schulz, B., et al. 2003,
Icarus, 161, 383
Coustenis, A., Salama, A., Lellouch, E., et al.
1998, Astron. and Astrophys., 336, L85
Cui, J., Yelle, R. V., Vuitton, V., et al. 2009,
Icarus, 200, 581
Daly, A. M., Berm´udez, C., L´opez, A., et al. 2013,
The Astrophysical Journal, 768, 81
Dobrijevic, M., H´ebrard, E., Loison, J., &
Hickson, K. 2014, Icarus, 228, 324
Ehrenfreund, P., Boon, J., Commandeur, J., et al.
1995, Advances in Space Research, 15, 335
Flasar, F. M., Kunde, V. G., Achterberg, R. K.,
et al. 2004, Nature, 427, 132
Fondren, L. D., McLain, J., Jackson, D. M.,
Adams, N. G., & Babcock, L. M. 2007,
International Journal of Mass Spectrometry,
265, 60
Fosse, D., Cernicharo, J., Gerin, M., & Cox, P.
2001, The Astrophysical Journal, 552, 168
Fuchs, U., Br¨unken, S., Fuchs, G. W., et al. 2004,
Z. Naturforschung A, 59, 861



Fulchignoni, M., Ferri, F., Angrilli, F., et al. 2005,
Nature, 438, 785
Gillett, F. C. 1975, The Astrophysical Journal,
201, L41
Gillett, F. C., Forrest, W. J., & Merrill, K. M.
1973, The Astrophysical Journal, 184, L93
Goorvitch, D. 1994, The Astrophysical Journal
Supplement Series, 95, 535
Guadagnini, R., Schatz, G. C., & Walch, S. P.
1998, The Journal of Physical Chemistry A,
102, 5857
Hanel, R., Conrath, B., Flasar, F. M., et al. 1981,
Science, 212, 192
Hartle, R. E., Sittler, E. C., Neubauer, F. M.,
et al. 2006, Planet. Space Sci., 54, 1211
H´ebrard, E., Dobrijevic, M., Loison, J. C., et al.
2013, A&A, 552, A132
Heineking, N., Dreizler, H., & Schwarz, R. 1986,
Zeitschrift f¨ur Naturforschung A, 41, 1210
H¨orst, S. M. 2017, Journal of Geophysical
Research: Planets, 122, 432
H¨orst, S. M., Vuitton, V., & Yelle, R. V. 2008,
Journal of Geophysical Research (Planets), 113,
E10006

Iino, T., Sagawa, H., & Tsukagoshi, T. 2020, The
Astrophysical Journal, 890, 95
Irwin, P. G. J., Teanby, N. A., de Kok, R., et al.
2008, J. Quant. Spectr. Rad. Trans., 109, 1136
Kanata, H., Yamamoto, S., & Saito, S. 1987,
Chemical Physics Letters, 140, 221
Khare, B., Sagan, C., Thompson, W., et al. 1984,
Advances in Space Research, 4, 59
Kisiel, Z., Nixon, C. A., Cordiner, M. A., Thelen,
A. E., & Charnley, S. B. 2020, J. Mol. Sectrosc.,
372

Kisiel, Z., Pszcz´o�lkowski, L., L´opez, J. C., et al.
1999, Journal of Molecular Spectroscopy, 195,
332

Krasnopolsky, V. A. 2009, Icarus, 201, 226
—. 2010, Planet. Space Sci., 58, 1507
Krasnopolsky, V. A. 2012, Planetary and Space
Science, 73, 318
—. 2014, Icarus, 236, 83
Kuan, Y.-J., Charnley, S. B., Huang, H.-C., et al.
2004, Advances in Space Research, 33, 31
Kuan, Y.-J., Yan, C.-H., Charnley, S. B., et al.
2003, Monthly Notices of the Royal
Astronomical Society, 345, 650
Kuiper, G. P. 1944, ApJ, 100, 378

Detection of Cyclopropenylidene on Titan 33



Kukolich, S. G. 1982, The Journal of Chemical
Physics, 76, 97
Kukolich, S. G., Ruben, D. J., Wang, J. H. S., &
Williams, J. R. 1973, The Journal of Chemical
Physics, 58, 3155
Kunde, V. G., Aikin, A. C., Hanel, R. A., et al.
1981, Nature, 292, 686
Lacy, J. H., Richter, M. J., Greathouse, T. K.,
Jaffe, D. T., & Zhu, Q. 2002, Publications of the
Astronomical Society of the Pacific, 114, 153
Lai, J. C.-Y., Cordiner, M. A., Nixon, C. A., et al.
2017, The Astronomical Journal, 154, 206
Lellouch, E. 2007, Astrophysics and Space
Science, 313, 175
Loison, J., H´ebrard, E., Dobrijevic, M., et al.
2015, Icarus, 247, 218
Lombardo, N. A., Nixon, C. A., Achterberg,
R. K., et al. 2019, Icarus, 317, 454
Lovas, F. J. 1992, Journal of Physical and
Chemical Reference Data, 21, 181
Lutz, B. L., de Bergh, C., & Owen, T. 1983,
Science, 220, 1374
Maguire, W. C., Hanel, R. A., Jennings, D. E.,
Kunde, V. G., & Samuelson, R. E. 1981,
Nature, 292, 683
Maiwald, F., Lewen, F., Ahrens, V., et al. 2000,
Journal of Molecular Spectroscopy, 202, 166
Martins, Z. 2018, Life, 8, 28
McGuire, B., Burkhardt, A., Kalenskii, S., et al.
2018, Science, 359, 202
Molter, E. M., Nixon, C. A., Cordiner, M. A.,
et al. 2016, The Astronomical Journal, 152, 42
M¨uller, H. S., Belloche, A., Menten, K. M.,
Comito, C., & Schilke, P. 2008, Journal of
Molecular Spectroscopy, 251, 319, special issue
dedicated to the pioneering work of Drs.
Edward A. Cohen and Herbert M. Pickett on

spectroscopy relevant to the Earth’s atmosphere
and astrophysics
M¨uller, H. S., Schl¨oder, F., Stutzki, J., &
Winnewisser, G. 2005, Journal of Molecular
Structure, 742, 215
M¨uller, H. S. P., Thorwirth, S., Roth, D. A., &
Winnewisser, G. 2001, ˚a, 370, L49
Niemann, H. B., Atreya, S. K., Bauer, S. J., et al.
2002, Space Science Reviews, 104, 553
Niemann, H. B., Atreya, S. K., Demick, J. E.,
et al. 2010, Journal of Geophysical Research
(Planets), 115, 12006



Nixon, C. A., Teanby, N. A., Irwin, P., & H¨orst,
S. M. 2013a, Icarus, 224, 253
Nixon, C. A., Achterberg, R. K., Vinatier, S.,
et al. 2008, Icarus, 195, 778
Nixon, C. A., Achterberg, R. K., Teanby, N. A.,
et al. 2010, Faraday Discussions, 147, 65
Nixon, C. A., Temelso, B., Vinatier, S., et al.
2012, Astrophys. J., 749, 159
Nixon, C. A., Jennings, D. E., B´ezard, B., et al.
2013b, ApJL, 776, L14
Nuevo, M., Materese, C. K., & Sandford, S. A.
2014, The Astrophysical Journal, 793, 125
Palmer, M. Y., Cordiner, M. A., Nixon, C. A.,
et al. 2017, Science Advances, 3, e1700022
Peeters, Z., Botta, O., Charnley, S. B., et al. 2005,
˚a, 433, 583
Pickett, H. M., Poynter, R. L., Cohen, E. A., et al.
1998, Journal of Quantitative Spectroscopy and
Radiative Transfer, 60, 883
Rodgers, C. D. 2000, Series on Atmospheric,
Oceanic and Planetary Physics,
doi:10.1142/3171
Samuelson, R. E., Hanel, R. A., Kunde, V. G., &
Maguire, W. C. 1981, Nature, 292, 688
Samuelson, R. E., Maguire, W. C., Hanel, R. A.,
et al. 1983, J. Geophys. Res., 88, 8709
Schinder, P. J., Flasar, F. M., Marouf, E. A., et al.
2012, Icarus, 221, 1020
Serigano, J., Nixon, C. A., Cordiner, M. A., et al.
2016, The Astrophysical Journal, 821, L8
Simon, M. N., & Simon, M. 1973, The
Astrophysical Journal, 184, 757
Soorkia, S., Taatjes, C. A., Osborn, D. L., et al.
2010, Physical Chemistry Chemical Physics, 12,
8750

Stoks, P. G., & Schwartz, A. W. 1982, Geochimica
et Cosmochimica Acta, 46, 309
Teanby, N., Irwin, P., Nixon, C., et al. 2013,
Planetary and Space Science, 75, 136
Teanby, N. A., Irwin, P. G. J., de Kok, R., et al.
2009, Icarus, 202, 620
Teanby, N. A., Cordiner, M. A., Nixon, C. A.,
et al. 2018, The Astronomical Journal, 155, 251
Thaddeus, P., Vrtilek, J. M., & Gottlieb, C. A.
1985, The Astrophysical Journal, 299, L63
Thelen, A. E., Nixon, C. A., Cordiner, M. A.,
et al. 2019a, The Astronomical Journal, 157, 219
Thelen, A. E., Nixon, C., Chanover, N., et al.
2018, Icarus, 307, 380

34 Nixon et al.



—. 2019b, Icarus, 319, 417
Vrtilek, J. M., Gottlieb, C. A., & Thaddeus, P.
1987, The Astrophysical journal, 314, 716
Vuitton, V., Yelle, R. V., & Anicich (Retired),
V. G. 2006, The Astrophysical Journal, 647,
L175

Vuitton, V., Yelle, R. V., Klippenstein, S. J.,
H¨orst, S. M., & Lavvas, P. 2019, Icarus
Vuitton, V., Yelle, R. V., & Lavvas, P. 2009,
Royal Society of London Philosophical
Transactions Series A, 367, 729
Vuitton, V., Yelle, R. V., & McEwan, M. J. 2007,
Icarus, 191, 722
Waite, J. H., Lewis, W. S., Kasprzak, W. T., et al.
2004, SSRv, 114, 113
Waite, J. H., Niemann, H., Yelle, R. V., et al.
2005, Science, 308, 982
Walch, S. P. 1995, The Journal of Chemical
Physics, 103, 7064



Westlake, J. H., Bell, J. M., Waite, Jr., J. H.,
et al. 2011, Journal of Geophysical Research
(Space Physics), 116, A03318

Willacy, K., Allen, M., & Yung, Y. 2016, The
Astrophysical Journal, 829, 79

Wilson, E. H., & Atreya, S. K. 2004, Journal of
Geophysical Research (Planets), 109, 6002

Winnewisser, G., Belov, S., Klaus, T., & Schieder,
R. 1997, Journal of Molecular Spectroscopy,

184, 468

Wlodarczak, G., Martinache, L., Demaison, J., &
Van Eijck, B. P. 1988, Journal of Molecular
Spectroscopy, 127, 200

Young, D. T., Berthelier, J. J., Blanc, M., et al.
2004, Space Science Reviews, 114, 1


</paper>

## Items to check

```json
[
 {
  "path": "processing.imaging.deconvolver.evidence[0]",
  "value": "Högbom",
  "failed_quote": "deconvolved (‘cleaned’) in CASA using the Högbom algorithm, with a cell size of 0.1 ′′ and a threshold of 10 mJy"
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "Delta chi-square significance",
  "failed_quote": "(no quote given)"
 }
]
```
