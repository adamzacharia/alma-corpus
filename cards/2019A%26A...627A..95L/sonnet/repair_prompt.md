# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019A%26A...627A..95L\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. 00227X ⃝c ESO 2022
March 24, 2022

## **Standing in the shadow of dark gas: ALMA observations of** **absorption from dark CO in the molecular DNM of Chamaeleon**


H. Liszt [1] and M. Gerin [2] and I. Grenier [3]


1 National Radio Astronomy Observatory, 520 Edgemont Road, Charlottesville, VA, USA 22903 e-mail: `hliszt@nrao.edu`
2 LERMA, Observatoire de Paris, PSL Research University, CNRS Sorbonne Universit´es, UPMC Univ. Paris 06, Ecole Normale
Sup´erieure, F-75005 Paris, France e-mail: `maryvonne.gerin@ens.fr`
3 AIM, CEA-IRFU/CNRS/Universit´e Paris Diderot, D´epartement d’Astrophysique, CEA, Saclay, 91191, Gif-sur-Yvette, France email: `isabelle.grenier@cea.fr`


received March 24, 2022


**ABSTRACT**


_Context._ We previously detected 89.2 GHz J=1-0 HCO [+] absorption in 12 directions lacking detected CO emission in the outskirts
of the Chamaeleon cloud complex and toward one sightline with integrated CO emission W CO = 2.4 K-km s [−][1] . Eight sightlines had
a much larger mean column density of dark neutral medium (DNM) - gas not represented in H I or CO emission - and were found
to have much higher mean molecular column density. The five other sightlines had little or no DNM and were found to have much
smaller but still detectable N(HCO [+] ).
_Aims._ To determine the CO column density along previously-observed Chamaeleon sightlines and to determine why CO emission
was not detected in directions where molecular gas is present.
_Methods._ We took [12] CO J=1-0 absorption profiles toward five sightlines having higher DNM and HCO [+] column densities and one
sightline with smaller N(DNM) and N(HCO [+] ). We converted the integrated HCO [+] optical depths to N(H 2 ) in the weak-excitation limit
using N(HCO [+] )/N(H 2 ) = 3 × 10 [−][9] and converted the integrated CO optical depths Υ CO to CO column density using the relationship
N(CO) = 1.861 × 10 [15] cm [−][2] Υ CO1.131 found along comparable lines of sight that were previously studied in J=1-0 and J=2-1 CO
absorption and emission.
_Results._ CO absorption was detected along the five sightlines in the higher-DNM group, with CO column densities 4 × 10 [13] cm [−][2] [<] ∼
N(CO) ∼ [<] 10 [15] cm [−][2] that are generally below the detectability limit of CO emission surveys.
_Conclusions._ In the outskirts of the Chamaeleon complex, the presence of molecular DNM resulted primarily from small CO column
densities at the onset of CO formation around the HI/H 2 transition in diffuse molecular gas. CO relative abundances N(CO)/H 2
<∼ 2 × 10 [−][6] in the outskirts of Chamaeleon are comparable to those seen in UV absorption toward early-type stars, including in
Chamaeleon.



**Key words.** interstellar medium – abundances; Chamaeleon


**1.** **Introduction**


The total gas column densities that are jointly traced by dust
and by cosmic-ray interactions exhibit large excesses over those
inferred from HI and CO line emission in galactic molecular
cloud complexes (Grenier et al., 2005), including in Chamaeleon
(Planck Collaboration et al., 2015). In a recent paper (Liszt et al.,
2018) (Paper I) we sought evidence of a hidden molecular gas
reservoir in Chamaeleon. We presented observations of absorption from λ3 mm J=1-0 lines HCO [+], HCN, and C 2 H toward thirteen compact extragalactic continuum sources seen against the
outskirts of the Chamaeleon cloud complex. We detected HCO [+]
absorption in all directions even though CO emission was firmly
detected in only one of these.
Taking an abundance ratio N(HCO [+] )/N(H 2 ) = 3 × 10 [−][9] we
compared the inferred column densities of H 2 to those of the
dark neutral medium (DNM), the gas inferred to be present from
maps of sub-mm dust opacity and gamma-ray emissivity (Planck
Collaboration et al., 2015; Remy et al., 2018) but not apparently
represented in λ21 cm HI or λ2.6mm CO line emission. We
found that gas in the outskirts of Chamaeleon was mostly atomic


_Send o_ ff _print requests to_ : H. S. Liszt
_Correspondence to_ : hliszt@nrao.edu



(H I rather than H 2 ) but that the DNM was mostly molecular, resulting from failure of the integrated CO J=1-0 emission W CO to
represent the true amount of molecular hydrogen when using a
standard CO-H 2 conversion factor N(H 2 )/W CO = 2 × 10 [20] cm [−][2]
(K-km s [−][1] ) [−][1] . Saturation of the HI emission profile might have
contributed significantly to N(DNM) in three directions but did
not create the need for the DNM.

Here we ask why CO emission did not represent the molecular gas component adequately: perhaps as the result of inadequate rotational excitation of the CO, or perhaps as the result of
there being only very small CO column densities at the onset of
CO formation around the H I - H 2 transition. In the present work
we observed λ2.6 mm J=1-0 CO absorption toward six of the
thirteen sources observed in our earlier paper, five in the group
of eight directions showing more DNM and H 2, and (because it
was convenient) one direction in the group of five showing little
or no DNM and much smaller but still non-zero N(HCO [+] ). The
integrated CO optical depths are converted to CO column density using the tight relationship defined along comparable lines
of sight previously studied in CO J=1-0 and J=2-1 absorption
and emission by Liszt & Lucas (1998).

The organization of this paper is as follows. In Sect. 2 we
discuss the new and existing observational material that is pre

1

Liszt, Grenier, Gerin: Standing in the shadow of the dark CO



sented here and give the background of the integrated optical
depth - column density conversion for the CO J=1-0 absorption
profiles. Sect. 3 presents the results of this work and, in Sect. 4,
drawing on earlier studies of the excitation of CO, we show that
the failure of CO emission to represent N(H 2 ) is due to small CO
column densities N(CO) and relative abundances N(CO)/N(H 2 )
that are familiar from studies of UV absorption at comparable
reddening E(B-V). Sect. 5 slightly extends the DNM analysis of
Paper I using direct UV absorption measurements of N(H 2 ) and
N(CO) toward a handful of stars seen toward Chamaeleon and
Sect. 6 is a summary.


**2.** **Observations, data reduction and optical depth -**
**column density conversion**


_2.1._ _Conventions_


In this work, N(H) is the column density of H-nuclei in neutral
atomic and molecular form, N(H) = N(H I)+2N(H 2 ). We denote the observed, integrated J=1-0 optical depths of the J=1-0
CO and HCO [+] transitions as Υ CO = � τ 0,1 (CO) dv and Υ HCO [+]
= � τ 0,1 (HCO [+] ) dv. Velocities presented with the spectra are
measured with respect to the kinematic definition of the Local
Standard of Rest.


_2.2._ _New ALMA absorption measurements_


We observed the J=1-0 lines of [12] CO and [12] CN in absorption
toward the six continuum sources whose line of sight properties
are given in Table 1; the resulting CO line profiles are shown in
Figs. 1 and 2. The work was conducted under ALMA Cycle 5
project 2017.1.00227.S whose pipeline data products were delivered in 2018 February. The spectra discussed here were extracted from the pipeline-processed, continuum-subtracted data
cubes at the pixel of peak continuum flux in the continuum map
made from each spectral window, and divided by the continuum
flux in the continuum map at that pixel. No (further) baselining of any of the spectra was performed. Fluxes at 115.3 GHz
ranged from 0.13 Jy for J1224 and 0.140 for J0942 to 1.68 Jy
for J1058: several of the sources were considerably dimmer than
in our Cycle 4 HCO [+] observations. Each spectrum consisted of
1919 semi-independent channels spaced by 30.503 kHz corresponding to 0.079 km s [−][1] at the 115.271 GHz rest frequency of
12 CO. The channel spacing is half the spectral resolution. CN
was very tentatively detected in one direction, toward J1224, and
will not be further discussed here.


_2.3._ _Other observational data at radio and UV wavelengths_


In Table 1 we quote the integrated HCO [+] optical depths from
Paper I and the optically thin H I column densities derived from
Galactic All-Sky Survey (GASS) III λ21 cm H I emission spectra (Kalberla & Haud, 2015). Column densities of HCO [+] are
taken from Paper I as derived assuming rotational excitation in
equilibrium with the cosmic microwave background, N(HCO [+] )
= 1.10 × 10 [12] cm [−][2] Υ HCO [+] for a permanent dipole moment
µ = 3.89 Debye. Fig. 1 shows the NANTEN CO J=1-0 emission spectra used by Planck Collaboration et al. (2015) to derive
the column density of DNM along with the CO and HCO [+] absorption profiles taken during the course of our work that are
shown in more detail in Fig. 2.
Fig. 3 shows the N(CO)-Υ CO relation derived from the prior
observations of J=1-0 and J=2-1 CO emission and absorption


2



by Liszt & Lucas (1998): this is used to convert our new measurements of Υ CO to N(CO) as discussed in Sect. 4.1. Fig. 4
compares CO and H 2 column densities at radio and UV wavelengths using the results of Burgh et al. (2007), Sonnentrucker
et al. (2007) and Sheffer et al. (2008).


_2.4._ _Reddening and dust optical depth_


The 6 [′] resolution dust-emission maps scaled to optical reddening E(B-V) by Schlegel et al. (1998) are used in Tables 1 and 4
. These reddening values can be converted to Planck 353 GHz
dust optical depth τ 353 with errors of order ±6% using the relationship established by Planck Collaboration et al. (2014) between τ 353 and reddening determined photometrically toward
quasars, E(B-V)/τ 353 = (1.49 ± 0.03) × 10 [4] mag.


_2.5._ _Conversion from integrated optical depth to column_
_density for CO_


Here we measure the integral of the optical depth of the CO
J=1-0 transition Υ CO and additional assumptions are required
to convert this to total CO column density. Most generally, the
integrated optical depth of the [12] CO J,J+1 transitions are related
to the column densities in rotational levels J and J+1 and the
Einstein B-coefficients as

τ _J_, _J_ +1 _d_ ν = ( _h_ ν/ _c_ )[ _N_ _J_ _B_ _J_, _J_ +1 − _N_ _J_ +1 _B_ _J_ +1, _J_ ] (1 _a_ )
�


For a linear rotor like CO with a permanent dipole moment
µ = 0.11 Debye (1 Debye = 10 [−][18] esu) this can be recast as


_N_ _J_ = [(] ( [2] _J_ _[J]_ + [ +] 1) [ 1][)] (µ/0.611.61 _D_ ×) [2] 10(1 − [14] exp(cm [−] − [2] τ _h_ _J_ ν/, _J_ + _k_ 1 T ex )) (1 _b_ )


where � τ _J_, _J_ +1 dv is in units of km s [−][1] and T ex is the excitation temperature between levels _J_ and _J_ + 1, _N_ _J_ +1 / _N_ _J_ =
( _g_ _J_ +1 / _g_ _J_ ) exp(− _h_ ν/ _k_ T ex ) and _g_ _J_ = 2 _J_ + 1.
CO excitation temperatures are directly observed in diffuse molecular gas toward early-type stars (Burgh et al., 2007;
Sonnentrucker et al., 2007; Sheffer et al., 2008) and for the J=10 transition these are typically in the range 3-5 K (see Fig. 5
of Liszt (2007) and Table 2 of Goldsmith (2013)). Similar values are inferred for gas observed in mm-wave CO absorption
(Liszt & Lucas, 1998). In the simple case of LTE at a single excitation temperature T ex for all J, the total column density can
be written N(CO) = b Υ CO, leading to b = 1.071 × 10 [15] cm [−][2]
(km s [−][1] ) [−][1] for T ex = 2.73K (the lower limit). Other cases include b = 1.381 × 10 [15] cm [−][2] (km s [−][1] ) [−][1] for T ex = 3.5 K,
b = 1.614 × 10 [15] cm [−][2] (km s [−][1] ) [−][1] for T ex = 4 K and b =
1.871 × 10 [15] cm [−][2] (km s [−][1] ) [−][1] for T ex = 4.5 K.
Here we convert the observed values of CO J=1-0 optical depths to column density using the earlier results of Liszt
& Lucas (1998) who determined N(CO) along similar sightlines using J=1-0 and J=2-1 observations of CO in absorption and emission. Their results for the integrated J=1-0 optical depths and CO column densities are very well represented
with a slightly super-linear power-law regression fit as discussed
in Sect. 4.1. Given the numerical examples in the preceding
paragraph, this is roughly equivalent to assuming an excitation
temperature of 4.4-4.5 K for the stronger lines observed here
(Table 1). An excitation temperature of at least 4.0 K is required
to produce a 1 K brightness in CO J=1-0 emission although a

Liszt, Grenier, Gerin: Standing in the shadow of the dark CO


**Fig. 1.** ALMA results in the Chamaeleon complex. Center: RGB image with N(HI) in blue, N(DNM) in green and Nanten CO emission brightness
in red. The locations of the 13 ALMA sources studied in Paper 1 are marked as squares, hatched for the 5 directions where CO absorption was
detected in this work. The positions of 8 stars with measured values of N(H 2 ) and N(CO) in UV absorption (Table 3) are marked by x’s. Shown
around the outside are HCO [+] (grey, shaded) and CO (red) absorption and CO emission profiles (blue) from NANTEN on a different vertical scale
as noted at right in each outer panel. CO absorption was not observed toward J1723 and was sought but not detected or plotted toward B1251.



smaller excitation temperature can produce an integrated brightness W CO - 1 K-km s [−][1] with a sufficiently wide line.
As discussed by Liszt & Lucas (1998) and Liszt & Pety
(2012), the excitation temperature of the CO J=1-0 transition
scales directly as the ambient thermal pressure of H 2 and increases with τ 0,1 . With a J=1-0 excitation temperature of 4.5 K
the implied partial pressures of H 2 are n(H 2 )T K = 5.8 × 10 [3] and
4typical values for the di.0 × 10 [3] cm [−][3] K for τ 0,1 ff(CO)use ISM sampled in C I by Jenkins & = 0 and 1, respectively. These are
Tripp (2011).


_2.6._ _The relative abundance of_ HCO [+]


As in Paper I we use the relative abundance N(HCO [+] )/N(H 2 )
= 3 × 10 [−][9] to derive N(H 2 ), the HCO [+] /H 2 ratio being assumed
to be constant in the gas. This value originates in the tight relationships that exist between HCO [+] and OH (Liszt & Lucas,
1996, 2000) or CH (Gerin et al., 2019), both of which are directly
measured in optical/UV absorption spectra to have fixed abundances relative to H 2 (Liszt, 2007; Sonnentrucker et al., 2007;
Sheffer et al., 2008; Weselak et al., 2009, 2010). The overall un


certainty in the abundance of HCO [+] relative to H 2 was estimated
by Gerin et al. (2019) to be ±0.2 dex; see their Table 4 giving
relative abundances and uncertainties for a variety of molecules
used as proxies for H 2 at radio/sub-mm wavelengths.


**3.** **Observational results**


General properties of the sightlines observed here are given in
Table 1, including HCO [+] and CO optical depths integrated over
the velocity range of the HCO [+] absorption. Table 2 relates derived values of N(CO), N(HCO [+] ) and N(H 2 ) as shown in Figs.
4 and 5. Table 3 shows gaussian decompositions of the CO profiles in those cases where it is justified, compared with the profile
integral and results of gaussian decomposition of the HCO [+] profiles.
Figure 1 is a finding chart for the thirteen sources observed
in HCO [+] absorption, showing their placement on the sky with
respect to the distributions of N(H I), N(DNM) and and the integrated CO brightness W CO as derived by Planck Collaboration
et al. (2015). Sightlines toward 6 of these were observed in CO,
and CO and HCO [+] profiles in these directions are shown in pan

3

Liszt, Grenier, Gerin: Standing in the shadow of the dark CO



|Col1|Col2|
|---|---|
|**J1058**||
|||
|||
|||


**0** **5** **10**

|J1224|Col2|
|---|---|
|||
|||



**0** **5** **10**

**VLSR (KM S** **[-1]** **)**



**0.1**

**0.0**

**-0.1**

**-0.2**

**-0.3**

**-0.4**

**-0.5**

**-0.6**


**0.1**


**0.0**


**-0.1**



**0.05**


**0.00**


**-0.05**


**-0.10**


**0.0**


**-0.5**



**0.2**

**0.1**

**0.0**

**-0.1**

**-0.2**

**-0.3**

**-0.4**

**-0.5**


**0.1**


**0.0**


**-0.1**


**-0.2**


**-0.3**


**-0.4**


**-0.5**


**-0.6**



|Col1|Col2|
|---|---|
|**J0942**||
|||
|||
|||
|||
|||
|||
|||


**0** **5** **10**

|Col1|Col2|
|---|---|
|**J1145**||
|||
|||
|||
|||
|||
|||
|||



**0** **5** **10**

**VLSR (KM S** **[-1]** **)**



|Col1|Col2|
|---|---|
|**J1136**||
|||
|||
|||
|||
|||
|||
|||


|0|5 10|
|---|---|
|||
|**B1251**||
|||
|||


**0** **5** **10**

**VLSR (KM S** **[-1]** **)**



**Fig. 2.** ALMA HCO [+] and [12] CO absorption profiles for the six sources observed here. The HCO [+] profile from Paper I is shown shaded in grey, the
12 CO J=1-0 profile from this work is shown in red.



**10**


**1**


**0.1**



**0.1** **1** **10**

⌡ [⌠] [τ] **[0,1]** **[(CO) dv [km s-1]]**



**Fig. 3.** The relationship between integrated CO J=1-0 optical depth
and N(CO) for the data of Liszt & Lucas (1998) who observed J=10 and J=2-1 CO emission and absorption along comparable sightlines.
The power-law fit is N(CO) = 1.861 × 10 [15] cm [−][2] Υ CO1.131 where Υ CO
= � τ 0,1 (CO dv in units of km s [−][1] .


els arranged around the periphery of the chart along with profiles
toward J1723 that has detectable CO emission but was not observed in CO absorption in this work.


4



HCO [+] and CO absorption profiles are shown in Fig. 2 for all
the sources observed here. CO absorption was detected along all
five of sightlines in the high-DNM group and not toward B1251.
The sightline to J0942 has the strongest integrated CO absorption in total but the strongest single feature is at 4 km s [−][1] toward
J1224. The detection of very weak CO absorption toward J1058
was only possible because of its very strong continuum flux.
The relative abundances of N(CO) and N(H 2 ) are known to
have very wide variations resulting from their sensitivity to resonant photodissocation (Fig. 4) so it is not surprising that the
ratio of the integrated CO and HCO [+] optical depths ranges from
0.7 to 7 among the sightlines measured here (Tables 1 and 3).
A mild surprise is that CO absorption is so weak in the blueshifted component having much stronger HCO [+] absorption toward J0942. The NANTEN spectrum toward J0942 (Fig. 1) suggested the possible presence of CO emission overlapping the
HCO [+] absorption and with stronger emission to the blue, in the
same sense as that of the HCO [+] absorption. This work shows
that the CO column density in the blue-shifted component toward J0942 is too small to support a CO detection in emission.


**4.** **CO and** H 2 **column densities, CO brightness and**
**CO-** H 2 **conversion factor**


_4.1._ Υ CO _, N(CO) and_ W CO


Figure 3 shows the data of Liszt & Lucas (1998) leading to the
regression relation that we use to convert the CO J=1-0 integrated optical depth Υ CO to column density N(CO) as discussed
in Sect. 2.5.

Liszt, Grenier, Gerin: Standing in the shadow of the dark CO



**6**


**4**


**2**


**0**



**10** **[16]**


**10** **[15]**


**10** **[14]**


**10** **[13]**











**10** **[12]**

|Col1|Col2|
|---|---|
||UV absorption<br>Liszt&Lucas 1998<br>This work<br>Chamaeleon stars|

**10** **[19]** **10** **[20]** **10** **[21]**






|10-5<br>02 0<br>< 2 x 1 02 0<br>X C O 2 x 1|Col2|
|---|---|
|||
|10-6<br>XCO ><br>LisztLucas9~~8~~<br>This work<br>J0942 blue<br>J0942 red<br>J1058<br>J1136<br>J1145<br>J1224<br>B1251|10-6<br>XCO ><br>LisztLucas9~~8~~<br>This work<br>J0942 blue<br>J0942 red<br>J1058<br>J1136<br>J1145<br>J1224<br>B1251|



**N(H2) [cm** **[-2]** **]**


**Fig. 4.** H 2 and CO column densities from UV and radio absorption spectra. Shown are UV absorption line measurements from Sonnentrucker
et al. (2007), Burgh et al. (2007) and Sheffer et al. (2008) (downwardpointing triangles), mm-wave results from Liszt & Lucas (1998) (small
orange circles), and results from this work (green filled squares).
Some informative upper limits to UV measurements are shown in red.
The mm-wave results assume N(H 2 ) = N(HCO [+] )/3 × 10 [−][9] and the
present results use Eqn. 2 to derive N(CO). UV absorption sightlines
in Chamaeleon are marked by blue asterisks, see Table 4. Grey dashed
lines show the locii of relative abundances N(CO)/N(H 2 ) as indicated.
Only sighlines with N(CO) > 10 [15] cm [−][2] are observable in present widefield CO emission surveys.


1.131
N(CO) = 1.861 × 10 [15] cm [−][2] Υ CO (2)


Table 2 gives the results of using Eqn. 2 and N(H 2 ) =
N(HCO [+] )/3 × 10 [−][9] to derive N(CO) and N(H 2 ) from our mmwave CO and HCO [+] absorption measurements. As a check on
this procedure, Fig. 4 compares the present and prior mm-wave
results for N(CO) and N(H 2 ) with the larger sample of direct UV
absorption line measurements of Sonnentrucker et al. (2007),
Burgh et al. (2007) and Sheffer et al. (2008). Results for UV
sightlines in the Chamaeleon region are noted in Fig. 4 (see Table
4) and are not exceptional.
The mm-wave results appear typical, not outliers, lending confidence to the assumed relative abundance of HCO [+]
that was used to derive N(H 2 ). The mean relative abundance
<N(CO)/N(H 2 )>≃ 2.2−2.5×10 [−][6] for the lines of sight observed
here (Table 2) is very small compared to the expected fractional
abundance of free gas-phase carbon, N(C)/N(H) ≃ 1.6 × 10 [−][4]
(Sofia et al., 2004), but still larger than found along many of
the sightlines represented by UV absorption in Fig. 4. The older
mm-wave results of Liszt & Lucas (1998) have CO and H 2 column densities toward the upper ends of their respective distributions in Fig. 4, and stronger [13] CO fractionation than is typically
the case for the UV measurements (Liszt, 2017).
In Fig. 5 we compare N(CO) and N(HCO [+] ) from the present
work with those in the earlier study of CO in emission and
absorption (Liszt & Lucas, 1998). The smaller sample of new
data lacks individual features with column densities N(CO) 2 × 10 [15] cm [−][2] or N(HCO [+] ) - 1.5 × 10 [12] cm [−][2] as found in the
older data but results for the two datasets largely overlap.



**0.0** **0.5** **1.0** **1.5** **2.0**

**N(HCO** **[+]** **)/10** **[12]** **cm** **[-2]**


**Fig. 5.** CO and HCO [+] column densities. Shown are results from this
work (larger green filled squares) and the earlier observations of Liszt
& Lucas (1998) (small orange circles). Integrated CO J=1-0 optical depths Υ CO have been converted to CO column density using
the relationship between Υ CO and N(CO) shown in Fig. 3, N(CO)
= 1.861 × 10 [15] cm [−][2] Υ CO1.131 . Grey dashed shaded lines show fiducial values N(CO)/N(H 2 ) = 10 [−][6] and 10 [−][5] assuming N(HCO [+] )/N(H 2 )
= 3 × 10 [−][9] . The broad grey line at N(CO)/N(H 2 ) = 5 × 10 [−][6] divides the
plot area into regions where X CO is larger or smaller than 2 × 10 [20] H 2
(K-km s [−][1] ) [−][1] . The red dash-dotted line at N(CO) = 10 [15] cm [−][2] shows the
CO column density at which the integrated J=1-0 emission brightness
W CO = 1 K-km s [−][1] .


_4.2._ _The implied CO-_ H 2 _conversion factor_


Also plotted in Fig. 5 are dashed lines corresponding to relative abundances N(CO)/N(H 2 ) = 10 [−][6] and 10 [−][5], which follow directly from the relative abundance N(HCO [+] )/N(H 2 ) =
3 × 10 [−][9] . An implied CO-H 2 conversion factor can be derived
when it is recognized that the integrated J=1-0 emission profile brightness W CO is related to N(CO) as W CO /(1 K-km s [−][1] ) =
N(CO)/10 [15] cm [−][2] over a wide range of hydrogen number density in diffuse molecular gas (Liszt, 2007, 2017), maintaining a
high degree of linearity up to brightnesses W CO ∼ [<] 5 − 10 Kkm s [−][1] . In this case the CO-H 2 conversion factor depends only
on the relative abundance N(CO)/N(H 2 ) and the relative abundance N(CO)/N(H 2 ) = 5×10 [−][6] divides Fig. 5 (and the rest of the
very local Universe) into regions where the CO-H 2 conversion
factor is larger or smaller than 2 × 10 [20] cm [−][2] (K-km s [−][1] ) [−][1] . That
this value of the CO-H 2 conversion factor is reached at such low
CO/H 2 relative abundances is a consequence of the very high
brightnesses per molecule that occur when the rotational excitation is so strongly sub-thermal (Goldreich & Kwan, 1974; Liszt
et al., 2010).
Only in the red-shifted component toward J0942 is the
implied CO-H 2 conversion factor N(H 2 )/W CO below 2 ×
10 [20] H 2 cm [−][2] (K-km s [−][1] ) [−][1] . We did not observe CO absorption
toward J1723, but consideration of the detected CO emission and
HCO [+] absorption in this direction (Fig. 2) provides an interesting point of comparison. Directly integrating over the separate
velocity ranges of the two kinematic components results in CO
integrated brightnesses of W CO = 0.90±0.14 and 1.36±0.14 Kkm s [−][1] and HCO [+] integrated optical depths Υ HCO [+] = 0.70±0.03


5

Liszt, Grenier, Gerin: Standing in the shadow of the dark CO



**1.0**


**0.5**

|Col1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||
|||||||



Liszt&Lucas 1998

**0.0**


**0.0** **0.5** **1.0** **1.5**

**HCO** **[+]** **FWHM [km s** **[-1]** **]**


**Fig. 6.** CO and HCO [+] line profile FWHM. Shown are results from this
work (larger green filled squares) and the earlier observations of Liszt
& Lucas (1998) (small orange circles). The dashed gray line represents
equality of the FWHM.


**6**


**4**


**2**


**0**


**-0.6** **-0.4** **-0.2** **0.0** **0.2** **0.4** **0.6**

**V(HCO** **[+]** **) - V(CO) [km s** **[-1]** **]**


**Fig. 7.** Distribution of velocity differences between HCO [+] and CO kinematic components from this work and the earlier observations of Liszt
& Lucas (1998). The mean difference and its dispersion are 0.10 km s [−][1]
± 0.40 km s [−][1] .


and 0.81±0.03 km s [−][1] . Converting Υ HCO [+] to N(HCO [+] ) and
N(H 2 ) = N(HCO [+] )/3 × 10 [−][9] leads to CO-H 2 conversion factors
N(H 2 )/W CO = 2.8±0.5 and 2.2±0.2×10 [20] H 2 cm [−][2] (K-km s [−][1] ) [−][1]
or N(H 2 )/W CO = 2.4 ± 0.3 × 10 [20] H 2 cm [−][2] (K-km s [−][1] ) [−][1] overall.


_4.3._ _Kinematics of CO absorption features_


In Figs. 4 and 5 we showed that the column densities of CO
and HCO [+] in the outskirts of Chamaeleon are like those previously observed along random lines of sight through the diffuse
ISM generally and the same is true of the linewidths. In Table


6



3 we show the results of gaussian decomposition of the HCO [+]
and CO line profiles that are shown in Fig. 2. In some cases
the superior signal/noise of the HCO [+] measurements allows fitting of wings and closely-separated components that is not feasible in CO. The plotted results represent only those features
that can be identified and associated in both species and have
been corrected by quadrature differencing of the FWHM and velocity resolution. The FWHM linewidths for CO are systematically smaller than those of HCO [+] as shown in Fig. 6. The unweighted mean linewidths for the combined sample of new and
old data are 0.87 ± 0.24 km s [−][1] for HCO [+] and 0.72 ± 0.22 km s [−][1]
for CO. This is not necessarily expected since CO forms from
the recombination of HCO [+] in diffuse molecular gas (Glassgold
& Langer, 1976; Liszt, 2007; Visser et al., 2009) and is initially cospatial with parent HCO [+] molecules. HCO [+] and OH
profiles do not show comparable differences (Liszt & Lucas,
2000). However, recombination of HCO [+] to CO is sensitive to
temperature while survival of the CO molecules after formation depends on shielding by H 2, dust and other CO molecules
(Draine & Bertoldi, 1996; Visser et al., 2009; Sternberg et al.,
2014; Liszt, 2015),raising the possibility that regions with differing N(HCO [+] )/N(CO) exist within the gas and are superposed
along the line of sight (Godard et al., 2009).
Linewidth differences among other chemical species are
well-known in diffuse molecular gas. In optical spectra there is a
sequence CH [+], CH, CN from broader to narrower lines (Lambert
et al., 1990; Crane et al., 1995; Pan et al., 2005) perhaps extending further to CO Pan et al. (2005). At mm-wavelengths, CN absorption lines are narrower than those of HCN and HNC (Liszt
& Lucas, 2001; Godard et al., 2010) from which CN forms by
photodissociation, and all the CN-bearing species have narrower
lines than in HCO [+] . CH [+] lines are typically much wider than
those of other molecules, presumably because the formation of
CH [+] occurs through the strongly endothermic reaction of C [+] and
H 2 . HCO [+] may keep a memory of this excess kinetic energy seen
in the CH [+] linewidth because it is such a close daughter product
of CH [+] (Godard et al., 2014).
Linewidth differences could arise as the result of the interplay between chemistry and gas dynamics in the diffuse molecular gas but not because CO molecules in the line wings of mmwave absorption profiles are more susceptible to photodissociation. The shielding and self-shielding of H 2 and CO arise from
the continuous opacity of dust and the wings of strongly-damped
H 2 and CO electronic transitions at the column densities needed
to form the observed amounts of CO, and the Doppler velocity distribution of CO or H 2 molecules is not important to their
survival.

In Paper I we noted a kinematic segregration in the
Chamaeleon gas in the sense that the directions with less DNM
and small N(H 2 ) were seen in HCO [+] only at v ∼ [<] 2km s [−][1] while
the material with velocities 2 - 6 km s [−][1] had the preponderance
of the HCN absorption, stronger H I emission and much more
DNM and H 2 . We suggested that this might indicate the presence of slow shocks in the region. The CO data in Chamaeleon
are too limited to draw firm conclusions but Fig. 7 shows a histogram of the distribution of line centroid velocity differences
between HCO [+] and CO for the new and old data. The mean difference is 0.1 km s [−][1], with a dispersion of .4 km s [−][1], indicating
at most a very small systematic shift, and a small but physically
significant dispersion.
Dynamical processes are important for the formation
chemistry of the molecules we observe, most obviously for
HCO [+] whose observed abundance in diffuse molecular gas
N(HCO [+] )/N(H 2 ) = 3 × 10 [−][9] is nearly 100 times higher than

Liszt, Grenier, Gerin: Standing in the shadow of the dark CO



would be expected from Langevin rates for the reaction of C [+]
+ OH with their observed column densities (Van Dishoeck &
Black, 1986). Flower & Pineau des Forets (1998) and Lesaffre
et al. (2013) discussd how a collection of slow shocks in magnetized diffuse gas could produce CH [+], HCO [+] and CO. Most
models that boost the CH [+] and/or HCO [+] chemistry in diffuse gas
tap the energy of an ion-neutral drift Valdivia et al. (2017) which
has a broad distribution ranging from 0.01 to 1 km/s. Visser et al.
(2009) drew on an earlier model of Federman et al. (1996), calculating molecular abundances at a suprathermal effective temperature determined by an Alven velocity of 3.5 km s [−][1] .
Forms in localized regions (vortices) where turbulent energy
is dissipated and the ion-neutral drift is maximum.
The turbulent dissipation region (TDR) model of diffuse
cloud chemistry (Godard et al., 2014) draws on earlier work
(Falgarone et al., 1995; Joulain et al., 1998; Pety & Falgarone,
2000) and forms CH [+] and HCO [+] in highly localized regions
(vortices) where turbulent energy is dissipated and the ionneutral drift is maximum. HCO [+] subsequently relaxes and accumulates at the observed abundance in ambient gas where it thermalizes and recombines to CO. CO is subsequently fractionated
by C [+] exchange at ambient kinetic temperature (Liszt, 2017) and
both HCO [+] and CO are observed with a degree of rotational excitation that is characteristic of the typical thermal pressures for
the diffuse interstellar medium at large (Jenkins & Tripp, 2011),
as noted in Sect. 2.5. In such a model HCO [+] recombines to CO
more rapidly as it thermalizes, and the HCO [+] -CO linewidth difference is presumably a collateral effect.
Comparable linewidth differences are expected between
HCO [+] and other species that form by the recombination of ions,
for instance HCN, HNC and CN that form from recombination
of the as-yet undetected species HCNH [+] . Godard et al. (2010)
observed smaller linewidths in HCN and HNC compared to
HCO [+] (Liszt & Lucas (2001) did not), and there is general agreement that the smallest linewidths have generally been observed
in CN. We sought but did not detect CN except marginally toward J1224. The difference in the velocity profiles therefore appear to be related to the interplay of chemical and dynamical
processes controlling the formation of molecules. To explore further the origin of the difference in velocity profiles more data are
needed in specific regions where the large-scale orientation of
the gas flows and magnetic field are homogeneous.


**5.** **Molecular, missing, and CO-dark gas**


In Paper I we showed that HCO [+] absorption lines traced important H 2 reservoirs extending several parsecs beyond the CObright parts of the Chamaeleon molecular clouds. The H 2 column densities inferred from the HCO [+] data for a standard abundance ratio N(HCO [+] )/N(H 2 ) = 3 × 10 [−][9] could substantially account for the excess gas along the eight sight lines with large
DNM column densities N(DNM) ∼ [>] 2 × 10 [20] cm [−][2] : diffuse H 2
partially contributed to the DNM toward three directions and
fully explained the DNM toward the five densest directions. In
this section we extend some of the analysis from Paper I using
an expanded, hybrid sample based on direct UV absorption measurements of N(H 2 ) and N(CO).
In Figs. 1 and 4 we noted the existence of UV absorption
measurements of N(H 2 ) and N(CO) toward stars of widelyvarying distance seen toward Chamaeleon (Table 4). The nearer
of these stars could in principle lie in front of some portion of
the Chamaeleon gas but N(H 2 ) is actually relatively high for
the nearer objects. To complement the modest sample of sightlines observed with ALMA, we extracted the HI and DNM col


umn densities and mm-wave CO brightness W(CO) toward these
stars and combined this information with that for the mm-wave
sightlines to produce Fig. 8 (like Fig. 6 in Paper I). In Fig 8 we
compare the total hydrogen column density obtained from the
dust and gamma-ray data (the x-axis) to the total hydrogen column density N(HI)+2N(H 2 ) derived with and without the use
of CO emission. In the left panel N(H 2 ) = X [0] CO [W] [CO] [,] [while] [at]
right N(H 2 ) is measured indirectly from HCO [+] absorption lines
for our ALMA data (circles) or directly from UV H 2 absorption lines (crosses). The error bars on N(H 2 ) at right assume
±25% errors in N(H 2 ) from the UV data and ±58% errors on
the N(HCO [+] )/N(H 2 ) ratio (Liszt & Gerin, 2016)).
The colour coding with DNM column density shows that diffuse H 2 can fully account for the DNM column densities over a
range varying by at least a factor of six. One can also note from
the difference in column density scales between the total and
DNM gas that the broad atomic envelopes of the clouds contribute more gas along those sight lines than the diffuse H 2 reservoirs. As in Paper 1 we infer that the DNM is mostly molecular
while the gas overall is atomic, for the lines of sight we studied
outside the CO-bright portions of the Chamaeleon complex.


**6.** **Summary**


MM-wave CO absorption line measurements are well-suited to
detecting or constraining the properties of dark medium and dark
CO. The CO absorption measurements performed here answer
the question of why the CO emission fails to represent N(H 2 )
reliably in the outskirts of Chamaeleon. CO column densities
and CO relative abundances are small in diffuse molecular gas
around the HI → H 2 transition as the result of the CO chemistry
at moderate reddening.
In Paper I we detected mm-wave J=1-0 absorption from
HCO [+] and, less commonly, C 2 H and HCN, against thirteen compact extragalactic continuum sources seen toward the outskirts
of the Chamaeleon HII region-molecular cloud complex. Only
one of these directions (J1723) had a firm detection of CO J=10 emission. Eight of the thirteen directions comprised a group
with higher column densities of dark neutral medium and, as we
showed, much higher molecular column densities. Converting
the N(HCO [+] ) to N(H 2 ) with N(HCO [+] )/N ( H 2 ) = 3 × 10 [−][9] we
found that the DNM was mostly molecular even while the gas as
a whole (in the observed directions) was predominantly atomic,
with H-nuclei in atomic form.
In this work we observed CO J=1-0 absorption lines toward
six of the thirteen sightlines from Paper I, five of them in the
higher-DNM group (Table 1 and Fig. 1). All five of these directions were detected in CO absorption (Fig. 2). Using a conversion between integrated J=1-0 optical depth and CO column density derived earlier from observations of J=1-0 and
J=2-1 absorption and emission along comparable sightlines (see
Eqn 2 and Fig. 3, and Sect. 4) the observed CO column densities were found to lie in the range 4 × 10 [13] cm [−][2] [<] ∼ N(CO)
<∼ 1.2 × 10 [15] cm [−][2] . This is generally below the expected limit
of detectability of extant CO emission surveys given that an integrated CO brightness of W CO = 1 K-km s [−][1] corresponds to
N(CO) = 10 [15] cm [−][2] in diffuse molecular gas (Sect. 4.2). As
noted in Paper 1, the Planck CO emission foreground maps are,
lamentably, hashed in the directions we observe, presumably as
the result of point-source removal.
The ratio of J=1-0 integrated optical depths in CO and
HCO [+] varies by almost an order of magnitude (Table 1 and 2).
Comparably-wide relative abundance variations are typical of
sightlines at moderate reddening seen in UV absorption (Fig. 4)


7

Liszt, Grenier, Gerin: Standing in the shadow of the dark CO


### 20 15 10 5


### 20 15 10 5


### 0 5 10 15 20

2
N H [10 [20] cm ]


### 0 5 10 15 20

2
N H [10 [20] cm ]


### 0.0 1.3 2.6 3.9 5.2 6.5

2
N H [DNM] in 10 [20] cm


**Fig. 8.** Comparison of total column density of H-nuclei N(H) derived from the DNM analysis and from observable column densities. The variable
plotted along the horizontal axis, N(H) = N(H I)| cham +N(DNM)+2W CO X [0] CO [, is the quantity fitted in the global DNM analysis (Planck Collaboration]
et al., 2015) and is the same in both panels. The vertical axis in each panel is the inferred total hydrogen column density N(H) = N(H I)| cham +2N(H 2 )
but with N(H 2 ) taken differently at left and right. At left, N(H) is calculated with N(H 2 ) = W CO X [0] CO [.] [At] [right,] [N(H)] [is] [calculated] [with] [N(H] [2] [)] [=]
N(HCO [+] )/3 × 10 [−][9] for the sightlines observed in HCO [+] absorption, or using actual measured N(H 2 ) for the stars with measured N(H 2 ) and N(CO)
(see Fig. 4 and Table 4). The error bars assume ±25% errors in N(H 2 ) from UV absorption and ±58% errors in the N(HCO [+] )/N(H 2 ) ratio. Stars
are marked by crosses and mm-wave targets by filled circles, and all sightlines are color-coded according to N(DNM) as shown at bottom.



owing to the sensitivity of H 2 and CO column densities to selfand mutual shielding and shielding by dust. To check on the conversions we employed to derive N(H 2 ) and N(CO) we compared
the radio- and UV-determined CO and H 2 column densities in
Fig. 4, finding the two types of measurements to yield consistent
determinations of the run of CO and H 2 column density.
In Fig. 5 we compared N(CO) and N(HCO [+] ) for the new
and existing mm-wave CO absorption measurements, leaving
the conversion to N(H 2 ) implicit. The datasets are consistent and
there is nothing unusual about the Chamaeleon measurements,
although they lack sightlines with HCO [+] and CO column densities as high as some of those seen earlier (this is also apparent in
Fig. 4). Given the equivalence of CO brightness and column density W CO ≃ N(CO)/10 [15] cm [−][2] in the diffuse molecular gas, the
CO-H 2 conversion factor N(H 2 )/W CO is linearly proportional to
the CO relative abundance, and N(H 2 )/W CO ≤ 2 × 10 [20] H 2 cm [−][2]
(K-km s [−][1] ) [−][1] only when N(CO)/N(H 2 ) ≥ 5 × 10 [−][6] . This is more
than twice the mean value observed here: only the red-shifted
line toward J0942 has a CO relative abundance high enough
that the implied CO-H 2 conversion factor is below N(H 2 )/W CO
= 2 × 10 [20] H 2 cm [−][2] (K-km s [−][1] ) [−][1] (see Table 2 and Fig. 5). High
values of the CO-H 2 conversion factor N(H 2 )/W CO were also inferred in Paper 1 based on the limits to the CO brightness.
The mm-wave CO absorption line chemistry has not been revisited in the 20 years since the observations of Liszt & Lucas
(1998), which is somewhat surprising given the kind of information that is returned. For this reason, and owing to the modest
number of sightlines we studied, we somewhat extended the discussion beyond the Chamaeleon region to a more general comparison of CO with HCO [+] and H 2 . Beyond the column densi

8



ties and abundances shown in Fig. 4 and 5, we noted (Fig. 6,
Table 3) that the CO FWHM linewidths are consistently about
20% smaller than those seen in the progenitor HCO [+] molecule
(0.72 ± 0.22 km s [−][1] and 0.87 ± 0.24 km s [−][1] respectively). A comparable difference is seen in CN-bearing species when compared
with HCO [+] . There is also a ±0.4 km s [−][1] dispersion in the difference of the centroid velocities of HCO [+] and CO (Fig. 7).
In Sect. 4 we discussed how the abundances and kinematics of
HCO [+], CO and other molecules arise from gas dynamical processes that enhance the formation rate of progenitor ions like
CH [+] and HCO [+] and create inhomogeneities that cause linewidth
differences.
In Sect. 8 we revisited part of the DNM analysis of Paper I,
using a hybrid sample whereby we augmented the ALMA observations with the directly-determined H 2 and CO column densities measured in UV absorption toward 8 bright stars seen toward the Chamaeleon region. As in Paper I we concluded that
the DNM in the outskirts of the Chamaeleon complex is mostly
molecular, with most H-nuclei in H 2, while the gas overall is
primarily atomic.
CO absorption profiles provide more information than just
the column density, and consideration of a wider range of CO
absorption line observations should help to elucidate the formation of molecules and the presence of DNM and the “dark” gas
whose shadows we explored in this work.


_Acknowledgements._ This paper makes use of the following new ALMA data:
ADS/JAO.ALMA#2017.1.00227.S . ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated

Liszt, Grenier, Gerin: Standing in the shadow of the dark CO


**Table 1.** Sightline and velocity-integrated spectral line properties


Source α(J2000) δ(J2000) _l_ _b_ E(B-V) _[a]_ N(H I) _[b]_ Υ HCO + _[c]_ _S_ 115 σ _l_ / _c_ _[d]_ Υ CO _[c]_

hh.mmssss dd.mmssss o o mag 10 [20] cm [−][2] km s [−][1] Jy km s [−][1]

J0942-7731 09.424275 -77.311158 293.321 -18.329 0.33 9.1 1.142(0.067) _[e]_ 0.140 0.126 0.855(0.133)
J1058-8003 10.584331 -80.035416 298.010 -18.288 0.15 6.0 0.201(0.009) 1.684 0.010 0.034(0.008)
J1136-6827 11.360210 -68.270609 296.070 -6.590 0.47 21.7 1.241(0.035) 0.344 0.054 0.396(0.047)
J1145-6954 11.455362 -69.540179 297.316 -7.747 0.38 16.8 0.870(0.031) 0.517 0.034 0.125(0.025)
J1224-8313 12.245438 -83.131010 302.095 -20.391 0.26 8.7 0.945(0.044) 0.132 0.122 0.679(0.137)
B1251-7138 12.545983 -71.381840 303.213 -8.769 0.28 17.0 0.139(0.027) 0.323 0.055 <0.131 _[f]_

_a_ Schlegel et al. (1998)
_b_
N(H I) = � T B dv × 1.823 × 10 [18] cm [−][2] from the Gass III H I profile (Kalberla & Haud, 2015)
_c_ Υ HCO + and Υ CO are the integrated J=1-0 optical depth in units of km s −1

_d_ line/continuum rms at zero optical depth in the 2x oversampled spectrum
_e_ Quantities in parenthesis are the standard deviation
_f_ Upper limit is 3σ


**Table 2.** HCO [+] H 2 and CO column densities


Source v 0 N(HCO [+] ) _[a]_ N(H 2 ) _[b]_ N(CO) _[c]_ N(CO)/N(H 2 )
km s [−][1] 10 [12] cm [−][2] 10 [20] cm [−][2] 10 [15] cm [−][2] 10 [−][6]

J0942 4.5 0.64(0.02) _[d]_ 2.35 0.37(0.11) 1.56
6.0 0.48(0.02) 1.76 1.07(0.16) 6.08
J1058 3.2 0.22(0.04) 0.74 0.04(0.01) 0.55
J1136 0.6 1.48(0.04) 4.55 0.65(0.07) 1.42
J1145 2.5 0.96(0.03) 3.19 0.18(0.03) 0.56
J1224 4.0 1.04(0.05) 3.47 1.20(0.26) 3.45
B1251 1.7 0.15(0.03) 0.51 < 0.18 _[e]_ < 3.66 _[e]_

mean _[f]_ 3.4(1.8) 0.80(0.45) 2.68(1.35) 0.59(0.47) 2.27(2.15)
mean _[g]_ 3.2(1.8) 0.71(0.48) 2.37(1.48) 0.53(0.46) 2.47(2.02)
_a_ N(HCO + )= 1.10 × 10 12 cm −2 I HCO +
_b_ + −9
N(H 2 ) = N(HCO )/3 × 10

_c_ N(CO)= 1.861 × 10 15 cm −2 I 1CO.131
_d_ quantities in parentheses are the standard deviation
_e_ upper limits are 3σ
_f_ for the six components with CO detections
_g_ including B1251 at the upper limit



by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is
a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.
This work was supported by the French program Physique et Chimie du
Milieu Interstellaire (PCMI) funded by the Conseil National de la Recherche
Scientifique (CNRS) and Centre National dEtudes Spatiales (CNES). HSL is
grateful to the hospitality of the Observatoire de Paris and La Clemence (1204
CH Geneva) during the initial drafting of this manuscript. We thank the referee
for helpful comments that served to clarify the discussion.


**References**


Burgh, E. B., France, K., & McCandliss, S. R. 2007, Astroph. J., 658, 446
Crane, P., Lambert, D. L., & Sheffer, Y. 1995, ApJ Supp. Ser., 99, 107
Draine, B. T. & Bertoldi, F. 1996, Astroph. J., 468, 269
Falgarone, E., Pineau Des Forˆets, G., & Roueff, E. 1995, A&A, 300, 870
Federman, S. R., Rawlings, J. M. C., Taylor, S. D., & Williams, D. A. 1996,
MNRAS, 279, L41
Flower, D. R. & Pineau des Forets, G. 1998, MNRAS, 297, 1182
Gerin, M., Liszt, H., Neufeld, D., Godard, B., Sonnentrucker, P., Pety, J., &
Roueff, E. 2019, A&A, 622, A26
Glassgold, A. E. & Langer, W. D. 1976, Astroph. J., 206, 85
Godard, B., Falgarone, E., Gerin, M., Hily-Blant, P., & de Luca, M. 2010, A&A,
520, A20
Godard, B., Falgarone, E., & Pineau Des Forˆets, G. 2009, A&A, 495, 847
Godard, B., Falgarone, E., & Pineau des Forˆets, G. 2014, A&A, 570, A27
Goldreich, P. & Kwan, J. 1974, Astroph. J., 189, 441
Goldsmith, P. F. 2013, Astroph. J., 774, 134
Grenier, I. A., Casandjian, J.-M., & Terrier, R. 2005, Science, 307, 1292
Jenkins, E. B. & Tripp, T. M. 2011, Astroph. J., 734, 65
Joulain, K., Falgarone, E., Des Forets, G. P., & Flower, D. 1998, A&A, 340, 241



Kalberla, P. M. W. & Haud, U. 2015, A&A, 578, A78
Lambert, D. L., Sheffer, Y., & Crane, P. 1990, ApJ, 359, L19
Lesaffre, P., Pineau des Forˆets, G., Godard, B., Guillard, P., Boulanger, F., &
Falgarone, E. 2013, A&A, 550, A106
Liszt, H., Gerin, M., & Grenier, I. 2018, A&A, 617, A54
Liszt, H. & Lucas, R. 2001, A&A, 370, 576
Liszt, H. S. 2007, A&A, 476, 291
—. 2015, Astroph. J., 799, 66
—. 2017, Astroph. J., 835, 138
Liszt, H. S. & Gerin, M. 2016, A&A, 585, A80
Liszt, H. S. & Lucas, R. 1996, A&A, 314, 917
—. 1998, A&A, 339, 561
—. 2000, A&A, 355, 333
Liszt, H. S. & Pety, J. 2012, A&A, 541, A58
Liszt, H. S., Pety, J., & Lucas, R. 2010, A&A, 518, A45+
Pan, K., Federman, S. R., Sheffer, Y., & Andersson, B.-G. 2005, Astroph. J., 633,
986
Pety, J. & Falgarone, E. 2000, A&A, 356, 279 [´]
Planck Collaboration, Abergel, A., Ade, P. A. R., Aghanim, N., Alves,
M. I. R., Aniano, G., Armitage-Caplan, C., Arnaud, M., Ashdown, M., AtrioBarandela, F., & et al. 2014, A&A, 571, A11
Planck Collaboration, Fermi Collaboration, Ade, P. A. R., Aghanim, N., Aniano,
G., Arnaud, M., & Ashdown, M. 2015, A&A, 582, A31
Remy, Q., Grenier, I. A., Marshall, D. J., & Casandjian, J. M. 2018, A&A, 611,
A51
Schlegel, D. J., Finkbeiner, D. P., & Davis, M. 1998, Astroph. J., 500, 525
Sheffer, Y., Rogers, M., Federman, S. R., Abel, N. P., Gredel, R., Lambert, D. L.,
& Shaw, G. 2008, Astroph. J., 687, 1075
Sofia, U. J., Lauroesch, J. T., Meyer, D. M., & Cartledge, S. I. B. 2004, Astroph.
J., 605, 272


9

Liszt, Grenier, Gerin: Standing in the shadow of the dark CO


**Table 3.** Gaussian decomposition of HCO [+] and CO absorption


HCO [+] HCO [+] HCO [+] HCO [+] CO CO CO CO

Source v 0 τ 0 FWHM Υ HCO + v 0 τ 0 FWHM Υ CO
km s [−][1] km s [−][1] km s [−][1] km s [−][1] km s [−][1] km s [−][1]


J0942 4.478 0.634 0.846 0.571 4.494 0.347 0.368 0.136

± 0.029 0.046 0.069 0.040 0.056 0.118 0.128 0.043

6.045 0.402 1.009 0.432 5.766 0.568 1.046 0.632

± 0.040 0.035 0.098 0.036 0.064 0.086 0.149 0.085

J1058 3.236 0.134 1.409 0.201

± 0.014 0.003 0.035 0.004

J1136 0.607 1.100 0.938 1.098 0.449 0.507 0.704 0.380

± 0.007 0.022 0.017 0.019 0.022 0.038 0.048 0.025

1.880 0.104 0.684 0.076

± 0.042 0.011 0.101 0.009

J1145 2.501 0.938 0.809 0.808 2.426 0.171 0.701 0.128

± 0.009 0.030 0.019 0.021 0.042 0.022 0.097 0.016

J1224 3.741 0.127 2.261 0.307

± 0.149 0.025 0.287 0.047

4.218 0.979 0.643 0.670 4.215 0.975 0.481 0.500

± 0.012 0.068 0.028 0.036 0.057 0.169 0.113 0.094


**Table 4.** Stars toward Chamaeleon studied in UV absorption _[a]_


Star l b distance E(B-V) ∗ E(B-V) SFD _[b]_ N(H 2 ) N(CO)
HD/CPD o o pc mag mag 10 [20] cm [−][2] 10 [14] cm [−][2]

-69 1743 303.71 -7.35 4700 0.30 0.29 1.00 0.12

93237 297.18 -18.39 310 0.09 0.11 0.63 0.25

94454 295.60 -14.73 330 0.18 0.31 5.75 2.00

96675 296.62 -14.57 160 0.30 0.64 7.24 19.1

99872 296.69 -10.62 230 0.36 0.38 3.31 4.47

102065 _[c]_ 300.03 -18.00 170 0.17 0.38 3.63 0.49

116852 _[c]_ 304.08 -16.13 4800 0.21 0.22 0.68 0.20

203532 309.46 -31.74 250 0.28 0.34 5.00 45.71
_a_ Stellar quantities from Sheffer et al. (2008)
_b_ Reddening from Schlegel et al. (1998)
_c_ Also observed by Burgh et al. (2007)


Sonnentrucker, P., Welty, D. E., Thorburn, J. A., & York, D. G. 2007, ApJ Supp.
Ser., 168, 58
Sternberg, A., Le Petit, F., Roueff, E., & Le Bourlot, J. 2014, Astroph. J., 790,
10
Valdivia, V., Godard, B., Hennebelle, P., Gerin, M., Lesaffre, P., & Le Bourlot, J.
2017, A&A, 600, A114
Van Dishoeck, E. F. & Black, J. H. 1986, ApJ Supp. Ser., 62, 109
Visser, R., van Dishoeck, E. F., & Black, J. H. 2009, A&A, 503, 323
Weselak, T., Galazutdinov, G., Beletsky, Y., & Krełowski, J. 2009, A&A, 499,
783
Weselak, T., Galazutdinov, G. A., Beletsky, Y., & Krełowski, J. 2010, MNRAS,
402, 1991


10


</paper>

## Items to check

```json
[
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "Mean N(CO)/N(H2) (six components) = 2.27 1e-6",
  "failed_quote": "mean f for the six components with CO detections 3.4(1.8) 0.80(0.45) 2.68(1.35) 0.59(0.47) 2.27(2.15)"
 }
]
```
