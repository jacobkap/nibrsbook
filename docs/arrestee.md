---
always_allow_html: true
header-includes:
- \usepackage{pdflscape}
- \usepackage{booktabs}
---

# Arrestee, Group B Arrestee, and Window Arrestee Segment  {#arrestee}





The Arrestee Segment has information on the person arrested in an incident and has a number of variables that look at same as in previous segments but with subtle differences. This segment covers the arrestee's age, sex, and race, ethnicity, and residency status (of the city, not as a United States citizen). Age, sex, and race are also in the Offender Segment but can differ as not all offenders are arrested. It also says the crime the arrestee was arrested for (which in some cases is different than the crime committed in the offense since an arrest can clear multiple incidents), the weapon carried during the arrest (which may be different than the weapon used during the offense) and if this weapon (if it is a firearm) was an automatic weapon. There are a few completely new variables including the date of the arrest and the type of arrest. The type of arrest is simply whether the person was arrested by police who viewed the crime, if the arrest followed an arrest warrant or a previous arrest (i.e. arrested for a different crime and then police find out you also committed this one so they consider you arrested for this one too), and whether the person was cited by police and ordered to appear in court but not formally taken into custody. Finally, for juvenile arrestees it says whether arrestees were "handled within the department" which means they were released without formal sanctions or were "referred to other authorities" such as juvenile or criminal court, a welfare agency, or probation or parole department (for those on probation or parole). 

This chapter also covers the Group B Arrestee Segment and the Window Arrestee Segment. The Arrestee Segment covers arrests for Group A offenses and there are corresponding Offense, Offender, and Victim segments for these incidents. Group B offenses, however, only have information about the arrest so incidents in this segment do not have any corresponding segments with it. Since Group B only has arrests without any associated incident, instead of the incident number variable like other segments have, this segment has an "arrest transaction incident number" which works the same as a normal incident number. Likewise, the Window Arrestee Segment isn't associated with any other segments as the "window" part means that they are only partial reports. The Window Arrestee Segment has the same variables as the normal Arrestee Segment but also has 10 variables on each of the offenses committed (up to 10 offenses) during the incident. This is really to try to provide a bit of information that you'd otherwise get from the other segments but don't since this is a window segment.

For the rest of this chapter I'll be using examples from the Arrestee Segment and not the Group B Arrestee (except for a table showing each Group B offense) or the Window Arrestee Segment. 

## Important variables

In addition to the variables detailed below this, segment has the traditional agency and incident identifiers: the ORI code, the agency state, the year of this data, and the incident number. It also has an "arrestee sequence number" which is an identifier for an arrestee in an incident since incidents can have multiple people arrested. This is just the number of each arrestee and to my knowledge is not associated with how involved the arrestee is. Being the 1st arrestee, for example, doesn't mean that individual played a greater role in the crime than the 2nd arrestee.

### Crimes arrested for

This segment tells us which offense the arrestee was arrested for. There are a couple of caveats with this data. First, there can be up to 10 crimes per incident but this segment only tells you the most serious offense (based on the agency's decision of which is most serious). This can be solved partially by merging this segment with the Offense Segment and getting all of the offenses related to the incident. It's only partially solved because the crime the person is arrested for may not necessarily be the crime involved in the incident. This is because a person can be arrested for a certain crime (e.g. shoplifting) and then the police find out that there are also responsible for a more serious crime (e.g. aggravated assault). Their arrest crime is shoplifting and they'll be associated with the incident for the aggravated assault.

One interesting part of this segment is that while it's associated with Group A offenses, as someone may be arrested for a crime other than the crime in the incident, arrests can include Group B offenses. So the Group B Arrestee Segment can really be thought of as an arrest for a Group B offense where the arrestee isn't associated with a previous Group A incident (other than ones that already led to an arrest since that incident would then be considered clear and the present arrest won't be associated with it). We'll look first at the crimes people were arrested for in the main Arrestee Segment, which includes both Group A and Group B offenses as possible arrest crimes, and then at the Group B Arrestee Segment which only includes Group B offenses.

#### Arrestee Segment arrest crimes

Table \@ref(tab:arresteeCrime) shows the number and percent of arrests for all arrests associated with a Group A crime incident. Perhaps unsurprising, drug crimes are the most common arrest making up a quarter of all arrests (30% when including drug equipment crimes). Simple assault (assault without a weapon or without seriously injuring the victim) is the next most common at 19% of arrests, and aggravated assault is the 4th most common arrest crime at 6.3% of arrests. Theft, which NIBRS breaks into a number of subcategories of theft such as shoplifting and "all other larceny" is among the most common arrest crimes, making up ranks 3 and 6 of the top 6, as well as several other subcategories later on. The remaining crimes are all relatively rare, consisting of under 5% of arrests each. This is due to how the top crimes are broad categories (e.g. drug offenses ranges from simple possession to large scale sales but is all grouped into "drug/narcotic violations" here) while other crimes are specific (e.g. purse-snatching is a very specific form of theft).  


Table: (\#tab:arresteeCrime)The number and percent of arrests for Group A crimes for all arrests reported to NIBRS in 2019.

|Crime Category                                      | \# of Offenses| \% of Offenses|
|:---------------------------------------------------|--------------:|--------------:|
|Drug/Narcotic Violations                            |        523,732|        25.82\%|
|Simple Assault                                      |        385,695|        19.02\%|
|Shoplifting                                         |        228,355|        11.26\%|
|Aggravated Assault                                  |        127,192|         6.27\%|
|All Other Larceny                                   |        104,244|         5.14\%|
|Drug Equipment Violations                           |         95,730|         4.72\%|
|Destruction/Damage/Vandalism of Property            |         69,153|         3.41\%|
|Burglary/Breaking And Entering                      |         56,613|         2.79\%|
|Intimidation                                        |         52,972|         2.61\%|
|Weapon Law Violations                               |         51,907|         2.56\%|
|All Other Offenses                                  |         49,288|         2.43\%|
|Stolen Property Offenses (Receiving, Selling, Etc.) |         32,953|         1.62\%|
|Motor Vehicle Theft                                 |         28,489|         1.40\%|
|Robbery                                             |         25,590|         1.26\%|
|False Pretenses/Swindle/Confidence Game             |         23,183|         1.14\%|
|Theft From Motor Vehicle                            |         18,780|         0.93\%|
|Counterfeiting/Forgery                              |         18,022|         0.89\%|
|Theft From Building                                 |         15,899|         0.78\%|
|Disorderly Conduct                                  |         11,413|         0.56\%|
|Driving Under The Influence                         |         10,084|         0.50\%|
|Impersonation                                       |          9,429|         0.46\%|
|Kidnapping/Abduction                                |          8,941|         0.44\%|
|Credit Card/Atm Fraud                               |          6,846|         0.34\%|
|Fondling (Incident Liberties/Child Molest)          |          6,659|         0.33\%|
|Trespass of Real Property                           |          6,439|         0.32\%|
|Rape                                                |          6,406|         0.32\%|
|Embezzlement                                        |          6,327|         0.31\%|
|Prostitution                                        |          5,492|         0.27\%|
|Murder/Nonnegligent Manslaughter                    |          4,788|         0.24\%|
|Liquor Law Violations                               |          4,267|         0.21\%|
|Identity Theft                                      |          3,802|         0.19\%|
|Drunkenness                                         |          3,753|         0.19\%|
|Pocket-Picking                                      |          3,137|         0.15\%|
|Pornography/Obscene Material                        |          3,055|         0.15\%|
|Arson                                               |          3,016|         0.15\%|
|Family Offenses, Nonviolent                         |          2,498|         0.12\%|
|Theft of Motor Vehicle Parts/Accessories            |          2,026|         0.10\%|
|Animal Cruelty                                      |          1,852|         0.09\%|
|Assisting Or Promoting Prostitution                 |          1,442|         0.07\%|
|Sodomy                                              |          1,374|         0.07\%|
|Statutory Rape                                      |          1,137|         0.06\%|
|Purse-Snatching                                     |            866|         0.04\%|
|Curfew/Loitering/Vagrancy Violations                |            840|         0.04\%|
|Sexual Assault With An Object                       |            647|         0.03\%|
|Purchasing Prostitution                             |            609|         0.03\%|
|Theft From Coin-Operated Machine Or Device          |            426|         0.02\%|
|Negligent Manslaughter                              |            327|         0.02\%|
|Operating/Promoting/Assisting Gambling              |            262|         0.01\%|
|Betting/Wagering                                    |            262|         0.01\%|
|Extortion/Blackmail                                 |            254|         0.01\%|
|Welfare Fraud                                       |            241|         0.01\%|
|Human Trafficking - Commercial Sex Acts             |            232|         0.01\%|
|Bribery                                             |            230|         0.01\%|
|Bad Checks                                          |            210|         0.01\%|
|Wire Fraud                                          |            180|         0.01\%|
|Incest                                              |            150|         0.01\%|
|Runaway                                             |             90|         0.00\%|
|Gambling Equipment Violations                       |             89|         0.00\%|
|Hacking/Computer Invasion                           |             66|         0.00\%|
|Peeping Tom                                         |             39|         0.00\%|
|Human Trafficking - Involuntary Servitude           |             27|         0.00\%|
|Sports Tampering                                    |              1|         0.00\%|
|Total                                               |      2,028,028|          100\%|

#### Group B Segment arrest crimes

Table \@ref(tab:GroupBarresteeCrime) shows the number and percent of arrests for all arrests associated with a Group B crime incident. The offense categories overlap with Table \@ref(tab:arresteeCrime) but these are for separate arrests, a single arrest cannot be in both segments. Unhelpfully, the most common Group B offense is "All other offenses" which means that it's a crime that isn't covered in either the Group A or the Group B crime categories. However, this can also include Group A or Group B crimes if they are not completed. So an attempted or a conspiracy to commit a Group A or B crime can go in this category. At 57% of Group B arrests, this very vague category covers a huge amount of arrests. The next most common Group B arrest is driving under the influence of drugs or alcohol, and this occurred in 18.4% - or 352k times - of arrests.

Trespassing makes up 5.7% of arrests and this is unlawfully entering someone's property, including a building. The difference between this and burglary is that this is entering without any intent to commit theft or a felony. Disorderly conduct is a broad category ranging from indecent exposure (which should be its own sex offense but isn't for some reason) to "profanity" and noise violations, and it makes up 6.2% of arrests. So be cautious with this offense as it ranges from very minor to quite serious and there's no distinguishing what actually happened. Drunkenness and liquor law violations make up 6% and 3.6% of arrests, respectively. The difference is that drunkenness is when someone is seriously drunk in public (to the point where they can't control their own body) and liquor law violations are about illegal making or selling of liquor. So basically bootlegging, selling alcohol without a license (or to people not allowed to drink, like minors), or avoiding paying tax on alcohol sales. "Family Offenses, Nonviolent" is also a rather vague category and includes "nonviolent abuse" (which I guess means emotional abusive) as well as neglecting the child in a few different ways like not paying alimony and deserting the child. Since these are arrests, the actions have to reach the level of criminal behavior, simply being an awful parent (or even leaving the child, as long as they have another adult to watch them) is not this offense. Runaways is an offense that only applies to people under age 18. The remaining categories are all rare and none are more than 1% of arrests.


Table: (\#tab:GroupBarresteeCrime)The number and percent of arrests for Group B crimes for all arrests reported to NIBRS in 2019.

|Crime Category                       | \# of Offenses| \% of Offenses|
|:------------------------------------|--------------:|--------------:|
|All Other Offenses                   |      1,095,755|        57.26\%|
|Driving Under The Influence          |        351,926|        18.39\%|
|Disorderly Conduct                   |        117,707|         6.15\%|
|Drunkenness                          |        116,343|         6.08\%|
|Trespass of Real Property            |        108,546|         5.67\%|
|Liquor Law Violations                |         68,862|         3.60\%|
|Family Offenses, Nonviolent          |         31,251|         1.63\%|
|Runaway                              |          9,535|         0.50\%|
|Curfew/Loitering/Vagrancy Violations |          9,360|         0.49\%|
|Bad Checks                           |          3,911|         0.20\%|
|Peeping Tom                          |            414|         0.02\%|
|Total                                |      1,913,610|          100\%|

### Arrest date

For each arrest we know the exact date of the arrest. As with the incident date, there is evidence that when agencies don't know the exact arrest date, they put down the first of the month. However, this is far less of a problem than with the incident date, likely because since the agency is doing the arresting they know exactly when they do it. Instead of looking at arrests by day of the month, we'll use both the arrest date and the incident date to look at how long it takes for crimes to get solved. 

Figure \@ref(fig:arrestsDaysUntilArrest) shows how long it takes for arrests to be made. The shortest time is zero days which means the arrest and the incident happened on the same day and the longest is 461 days after the incident. About 76.5% of arrests happen on the same day as the incident while 6.6% happen on the next day. 1.4% happen the following day and 1% on the day after this. This trend of a lower probability of the case being solved as the time from the incident increases continues throughout the figure. Including dates up to 461 days is a bit ridiculous since it's impossible to see trends among the early dates other than zero days, but it's a good demonstration of how massively concentrated arrests are that occur on the same day of the incident. The lesson here is that if an arrest isn't made on the day of the incident (such as at the scene of the crime), it's very unlikely that'll it'll be made at all (and most crimes never lead to an arrest). 

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arrestsDaysUntilArrest-1.png" alt="The distribution of the number of days from the incident to the arrest date. In 2019 the maximum days from incident to arrest was 461 days. Zero days means that the arrest occurred on the same day as the incident." width="90%" />
<p class="caption">(\#fig:arrestsDaysUntilArrest)The distribution of the number of days from the incident to the arrest date. In 2019 the maximum days from incident to arrest was 461 days. Zero days means that the arrest occurred on the same day as the incident.</p>
</div>

Figure \@ref(fig:arrestsDaysUntilArrestBarplot) groups the larger number of days together to make it easier to see trends early after the incident. Here we can see much better how the percent of arrests move quickly downwards after zero days. 

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arrestsDaysUntilArrestBarplot-1.png" alt="The number of days from the incident to the arrest date. Values over 10 days are grouped to better see the distribution for arrests that took fewer than 10 days. Zero days means that the arrest occurred on the same day as the incident." width="90%" />
<p class="caption">(\#fig:arrestsDaysUntilArrestBarplot)The number of days from the incident to the arrest date. Values over 10 days are grouped to better see the distribution for arrests that took fewer than 10 days. Zero days means that the arrest occurred on the same day as the incident.</p>
</div>

### Weapons

In the Offense Segment we get info on what weapon (if any) was used during the crime. Here, we see what weapon the person arrested was carrying *when they were arrested.* There is probably a very large overlap here, especially given that the vast majority of arrests happen on the same day as the offense, so probably happen at the scene of the crime (and we'll see exactly which ones do happen there later on in this chapter). Compared to the weapons covered in the Offense Segment - see Section \@ref(offenseWeapons) for more - the weapons here are only a narrow subset, and cover mostly firearms. This is partly because the most common "weapon" in the Offense Segment is that the offender used their body as a weapon (e.g. punching, kicking) and everyone arrested has a body so it doesn't make sense to count that as a weapon. Each arrestee can carry up to two weapons, but we'll only look at the first weapon for the below graphs. Please note that this is weapons found on the arrestee, and doesn't mean that they used the weapon during the arrest. 

Figure \@ref(fig:arresteeWeapon) shows the breakdown in the weapon carried by the arrestee during the arrest. In 94% of arrests, the arrestee was not carrying any weapon. Since this graph shows arrests for all crimes, it makes a good deal of sense. Most crimes are non-violent so we'd expect those people to not carry a weapon. Since so few arrestees have weapons, we'll look at the breakdown among those who were carrying a weapon in Figure \@ref(fig:arresteeWeaponArmed). 

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arresteeWeapon-1.png" alt="The weapon found on the arrestee for all arrestees reported in 2019." width="90%" />
<p class="caption">(\#fig:arresteeWeapon)The weapon found on the arrestee for all arrestees reported in 2019.</p>
</div>

To see the weapons carried when the arrestee had a weapon, Figure \@ref(fig:arresteeWeaponArmed) shows the breakdown in which weapon they carried. About 43.8% of people arrested who had a weapon were carrying a handgun followed by 30% with some kind of "lethal cutting instrument" like a knife. While rifles, and especially "assault rifles", are what people (and especially politicians and the media) focus on when talking about violent crime, handguns are actually the most common gun to be used in a crime so it makes sense that handguns are the most frequently found weapon. "Firearm (type not stated)"  basically means that the type of firearm used is unknown so can belong in one of the firearm categories and makes up 9% of weapons. Blunt instruments (including bats, clubs, and brass knuckles) follow at 6.9% of weapons. And the remaining weapons included are "other firearm" (so any other than ones specified) at 5.8%, rifle at 2.3%, and shotgun at 2%. 

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arresteeWeaponArmed-1.png" alt="The distribution of weapon usage for all arrestees in 2019 who were arrested with a weapon (i.e. excludes unarmed arrestees)." width="90%" />
<p class="caption">(\#fig:arresteeWeaponArmed)The distribution of weapon usage for all arrestees in 2019 who were arrested with a weapon (i.e. excludes unarmed arrestees).</p>
</div>

### Automatic weapons

This variable tells you if the weapon the arrestee was carrying was a gun whether that gun was fully automatic. To be clear, this means that when you pull the trigger once the gun will fire multiple bullets. Semi-automatic firearms are not automatic firearms. The Offense Segment also has a variable indicating if the offender used an automatic weapon but there they didn't necessarily recover the gun so it's much less reliable than in this segment where the police have the gun and are able to test it.^[It's not clear whether they actually test it or simply go by the design of the gun, such as if the model allows for fully automatic firing.] The percent of guns that are fully automatic are fairly similar between the weapons seized at arrest, as shown in Figure \@ref(fig:arresteeAutomaticWeapon) and those used in the offense as shown in Figure \@ref(fig:offenseAutomaticWeapon) in Chapter \@ref(offenseSegment). Figure \@ref(fig:arresteeAutomaticWeapon) shows that about 5.6% of rifles seized by police during an arrest were fully automatic. About 4.9% of handguns are automatic while "firearm (type not stated) are automatic in 4.3% of cases. Shotguns and  "other firearm" category are the least likely to be automatic at about 2.5% and 1.1% of weapons, respectively. 

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arresteeAutomaticWeapon-1.png" alt="The percent of firearms the arrestee was carrying that were fully automatic, for arrestees in 2019." width="90%" />
<p class="caption">(\#fig:arresteeAutomaticWeapon)The percent of firearms the arrestee was carrying that were fully automatic, for arrestees in 2019.</p>
</div>

### Type of arrest

While arrests are sometimes talked about as if they are a homogeneous group (likely in big part because UCR data doesn't differentiate types of arrests), NIBRS data breaks them down into three different types of arrests. Figure \@ref(fig:arresteeTypeOfArrest) shows the distribution in the type of arrest for all arrestees in the 2019 NIBRS data. The most common type is "On-View" which means that the person is arrested at the scene by an officer. For example, if police respond to a bank robbery and nab the robbers as they run out of the bank, this is an on-view arrest. On-view arrests make up the majority - 50.9% - of arrests.

The next type of arrest is a "warrant/previous incident report" and this makes up 26.8% of arrests. In these cases the police had an arrest warrant and found the person and arrested them based on that warrant. This also includes when a person is arrested and found to have been involved in previous incidents. Then these previous incidents would be considered cleared from this single arrest. In these cases NIBRS has an indicator variable, called the "multiple arrestee indicator" to tell us that this individual is responsible for multiple incidents cleared so we avoid counting them twice (as their demographics will be the same each time). In this variable it says "count arrestee" if this is their only arrest or if this is the first arrest that is counted in cases where multiple incidents are cleared by the arrest, and "multiple" otherwise. 

Finally, people can get a "summoned/cited" arrest which isn't really an arrest at all. This is when they are given a subpoena that says that must go to court to be tried for a crime, but they are not formally arrested and taken into police custody (i.e. they are never handcuffed, taken to a police precinct or to jail). About 22.2% of arrests are this form of arrest.

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arresteeTypeOfArrest-1.png" alt="The distribution of arrests by type of arrest. Previous Incident Report includes cases where an individual was arrested for a separate crime and are then reported as also arrested for this incident." width="90%" />
<p class="caption">(\#fig:arresteeTypeOfArrest)The distribution of arrests by type of arrest. Previous Incident Report includes cases where an individual was arrested for a separate crime and are then reported as also arrested for this incident.</p>
</div>

### Disposition for juvenile arrestees

For juvenile arrestees - those under age 18 *at the time of the arrest* (and, by definition they'd also be under age 18 during the incident) - there is some information about the outcome of the arrest.^[There are a few people older than 18 with this variable but it's so rare that I think that they're just incorrectly inputted ages.] There are two possible outcomes (which NIBRS calls "dispositions"): being referred to other (that is, other than the arresting agency) authorities or handled within the arresting agency. Figure \@ref(fig:arresteeJuvenileDisposition) shows this breakdown and being referred to other authorities is the most common outcome at 72.6% of juvenile arrests. This is a very broad category and the "other authorities" can range from juvenile or adult court (so the police recommend that they be prosecuted) to welfare agencies and being sent to other police agencies (such as if they committed a crime elsewhere and are being extradited). The other category, being handled within the department, means that the police release the juvenile without any formal action taken (but they may give the juvenile a warning). In these cases the juvenile is released to an adult (including but not limited to family members or guardians) and the case is essentially dropped. In about 0.001% of juvenile arrests the disposition is unknown.^[A juvenile can potentially get multiple dispositions, such as if they're initially released but later the police recommend them for prosecution. It's not clear which outcome is recorded in these cases. In UCR data, however, only the initial disposition is recorded so that is likely how it also is in NIBRS.] 

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arresteeJuvenileDisposition-1.png" alt="For juvenile arrestees (under age 18), the distribution of case outcomes." width="90%" />
<p class="caption">(\#fig:arresteeJuvenileDisposition)For juvenile arrestees (under age 18), the distribution of case outcomes.</p>
</div>

### Demographics

This segment provides several variables related to who the arrestee is. Age, race, and sex overlap with the Offender Segment but this segment also adds ethnicity and whether they live in the jurisdiction of the agency (i.e. the city the police patrols) they were arrested by.

#### Residence status

The first variable we'll look at is the residence status for the arrestee. This is residence in the jurisdiction that arrested them and it has nothing to do with residence status or citizenship status in the United States. People tend to commit crimes (and are the victims of crimes) very close to where they live, so this provides some evidence for that. We don't know where the arrestee lives, but know if they live in the jurisdiction or not. This is useful because some areas (e.g. Las Vegas, Washington DC, urban city centers where people commute to work) likely have a lot more people moving into those areas during the day but who live else compared to places like rural towns or suburbs. So it's helpful to be able to distinguish locals arrested with people who may be tourists or come into town just to commit the crime.^[In a ridealong I was on a woman who lived over an hour from the city I was in was caught shoplifting clothes.] 

One thing to be cautious about is that residence status may be an imprecise measure of where someone actually lives. How it's defined may differ by agency which could affect comparability across agencies. For example, if it's defined as official residence (such as address on a driver's license) that may be incorrect for a sizable share of the population (e.g. many college students live far from where their driver's license address is).^[One another ridealong a man from Florida was arrested for stealing from a local store (in California).] If residence status is based on asking the arrestee, they may of course lie to the police. There's also the question of how to label people who are truly transient such as homeless people who may move from city to city. The FBI defines residence as their legal permanent address though it's unclear how that is handled for people without this info and when people live permanently in a different spot than their legal address.  

Figure \@ref(fig:arresteeResidenceStatus) shows the percent of arrestees in 2019 who were residents or not (or whose status was unknown) of the jurisdiction that arrested them. Most people were arrested near where they live, with 56.9% of arrestees being residents, compared with 23.3% not being residents. However, about one-fifth of arrestees had an unknown residence status so the percents of resident and non-resident may change dramatically if we didn't have any unknowns. 

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arresteeResidenceStatus-1.png" alt="The distribution of residence status for all arrestees reported to NIBRS in 2019. Residence status is residence in the arresting agency's jurisdiction (e.g. do you live in the city you were arrested in?). It is unrelated to citizenship or immigration status." width="90%" />
<p class="caption">(\#fig:arresteeResidenceStatus)The distribution of residence status for all arrestees reported to NIBRS in 2019. Residence status is residence in the arresting agency's jurisdiction (e.g. do you live in the city you were arrested in?). It is unrelated to citizenship or immigration status.</p>
</div>

#### Age

This variable is the age at the arrest, which may be different than age during the crime. As in the Offender Segment we are given the exact age (in years) but agencies can input a range of possible ages with the FBI giving us the average of this range (rounding down, not to the nearest integer) in the data. In Figure \@ref(fig:offenderAge) in the Offense Segment, this can be seen in the sudden spikes in the percent of offenders of a certain age and that some of the most common ages are divisible by five (e.g. 20, 25, 30). There are also far fewer unknown ages in this data with only 0.1% of arrestees having a missing age. This is reasonable as a person arrested is present for the police to learn their age from something like a driver's license or past criminal records, or estimate the age by looking at the arrestee. Like in the Offender Segment, age as a specific year is cutoff at 98 with all older ages grouped simply as "over 98 years old".

Figure \@ref(fig:arresteeAge) shows the percent of arrestees at every age available. Relative to Figure \@ref(fig:offenderAge), this graph is far smoother, indicating that there was less estimating ages and more knowing the actual age. While the trend is the same for both of these graphs, the arrestee data doesn't have any odd spikes with certain ages. Age we see that the percent of people arrested increases as they age, peaking in the early twenties before declining and then peaking age even higher in the late 20s. After this, there is a long steady decline as the arrestee ages.     

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arresteeAge-1.png" alt="The age of all arrestees reported in the 2019 NIBRS data." width="90%" />
<p class="caption">(\#fig:arresteeAge)The age of all arrestees reported in the 2019 NIBRS data.</p>
</div>

#### Sex

We also know the sex of the arrestee. The only options for this variable are male and female and there is never missing data so the police always choose one of these two choices. There is no option for transgender or any other identity. Figure \@ref(fig:arresteeSex) shows the distribution of arrestees by sex. The vast majority, 70.5% of arrestees are male and the remaining 29.5% are female. This is a higher rate of female arrestees than you might expect - past research has found that crime is largely a male-phenomenon, even greater than found here (though "crime" in most criminology research is only murder or violent index crimes) - and that's because there are differences in sex involvement by type of crime. For rape, as an example, 97.8% of arrestees in 2019 were male. Shoplifting was an even 50% split between female and male arrestees.

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arresteeSex-1.png" alt="The sex of all arrestees reported in the 2019 NIBRS data." width="90%" />
<p class="caption">(\#fig:arresteeSex)The sex of all arrestees reported in the 2019 NIBRS data.</p>
</div>

#### Race

For each arrestee we know their race, with possible races being White, Black, American Indian/Alaskan Native, Asian, and Native Hawaiian/Pacific Islander. Unlike sex, the police can say that the race is unknown.^[I've been told that measuring race at all is itself racist so should never been done, even in research. This from a group of people who also said they have no need to actually evaluate police racial bias properly (i.e. using a regression with control variables) since they already knew the answer. If you agree with this, please don't ever do research on anything, you'll do it poorly.] As each arrestee is visible to the police, and can self-report race or provide official records (e.g. criminal history or jail admission data) which may say their race, there is far less uncertainty for arrestee race than offender race where 38.5% of the data is missing. As with any measure of race there is still some degree of uncertainty since people's race are not always obvious and may not fit tidily into each of the mutually exclusive groups available in NIBRS data (e.g. there is no option for mixed race). 

Figure \@ref(fig:arresteeRace) shows the breakdown for the races of each arrestee. White arrestees are most common at 64.2% of arrestees, following by Black arrestees at 29.8%. Only 3.1% of arrestees have an unknown race. The remaining small share of arrestees is made up of American Indian/Alaskan Native at 1.6%, Asian at 1%, and Native Hawaiian/Pacific Islander at 0.3% of arrestees.

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arresteeRace-1.png" alt="The race of all arrestees reported in the 2019 NIBRS data." width="90%" />
<p class="caption">(\#fig:arresteeRace)The race of all arrestees reported in the 2019 NIBRS data.</p>
</div>

#### Ethnicity

Finally, there is data on the race of the arrestee so we know if they are Hispanic or not. Ethnicity is so poorly used in the UCR data (e.g. UCR stopped collecting it for arrests for most years available and most agencies still don't report it) that I recommended in the [UCR book](https://ucrbook.com/) against ever using it. For NIBRS, there is far less data missing so it's not as much of a problem to use ethnicity as it is with UCR data. The issue remains as to what agencies are actually reporting this data or in which scenarios this variable is reported or not even in agencies that generally do report it. 

Ethnicity is an optional variable so agencies are never required to report it. This means that there's a greater chance that it'll be used only in non-random situations (which would make the data biased in some unknown way). There's also the question of reliability of the ethnicity data. Someone being Hispanic or not is likely just what the arrestees calls themselves or what the arresting officer perceives them to be. Both are important ways of measuring ethnicity but get at different things. Perception is more important for studies of bias, self-identification for differences among groups of people such as arrest rates by ethnicity. And the subjectivity of who is classified as Hispanic means that this measurement may differ by agency and by officer, making it imprecise.

Figure \@ref(fig:arresteeEthnicity) shows the breakdown in arrests by arrestee ethnicity. Most arrestees - 72.5% - are not Hispanic. Only 10% are reported to be Hispanic but an even higher percent of arrestees - 16.8% - have an unknown ethnicity so the true percent or Hispanic or non-Hispanic arrestee may be different than shown here. 

<div class="figure" style="text-align: center">
<img src="arrestee_files/figure-html/arresteeEthnicity-1.png" alt="The ethnicity of all arrestees reported in the 2019 NIBRS data." width="90%" />
<p class="caption">(\#fig:arresteeEthnicity)The ethnicity of all arrestees reported in the 2019 NIBRS data.</p>
</div>
