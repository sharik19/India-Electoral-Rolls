### India's Electoral Rolls (2024–25), SIR Rolls & Deleted Voter Records (2025–26)

------------------------------------------------------------------------

This repository contains the documentation for the parsed and analyzable voter records available via [Harvard Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/YNEY6G). It looks less like a repository at the moment. In the future, I will update this repository with the scripts used for downloading the rolls and subsequent text extraction using Surya-OCR. You can request access to this dataset using the following [Google Form](https://forms.gle/26spnRXCsYEoP1uQ7). Before using the dataset, I strongly recommend carefully reading the documentation (including the codebook) available [here](https://github.com/sharik19/India-Electoral-Rolls/blob/main/Documentation_India_Electoral_Rolls_SL.pdf). It will make your job easier and save me from answering issues already covered in the documentation.

I have now released parsed, analyzable files for the electoral rolls of 10 states and Delhi, the SIR rolls of Uttar Pradesh, Karnataka and Gujarat, and deleted voters' records (ASDD lists) from the SIR draft stage of five of them. I plan on regularly updating the dataset with voter records from more states, depending on resource availability.

If you use this dataset, please cite it appropriately. A suggested format is:\
**Sharik Laliwala. 2026. "India's Electoral Rolls (2024–25), SIR Rolls & Deleted Voter Records (2025–26)." Harvard Dataverse.** **DOI: <https://doi.org/10.7910/DVN/YNEY6G>.**

Although it is already stated in the Google Form, I am reiterating two critical points here:

1\. This dataset is not meant for commercial usage that may lead to potential monetary benefits (telemarketing, political consultancy, etc.).

2\. If you are approved to access this dataset, you should not share it with anyone else (unless their details have been specified in the Google Form). You can direct them to the form to request access if they wish to use the dataset. This is absolutely necessary for the ethical use of this dataset.

------------------------------------------------------------------------

Here's more on what is available on the Dataverse and how it is organized:

#### Voter Records: Electoral Rolls (2024–25)

| State | Year | No. of Assembly Constituencies (AC) | No. of Polling Stations (PS) / Parts | Mean Voters in a PS |
|:------------|:------------|:--------------|:--------------|:--------------|
| Andhra Pradesh | 2024 (Lok Sabha election) | 175 | 46,164 | \~938 |
| Bihar | 2024 (Lok Sabha election) | 243 | 76,390 | \~1,006 |
| Chhattisgarh | 2024 (Lok Sabha election) | 90 | 24,104 | \~872 |
| Delhi | 2025 (Vidhan Sabha election) | 70 | 13,033 | \~1,202 |
| Gujarat | 2025 (final roll published in January 2025) | 182 | 50,948 | \~992 |
| Haryana | 2024 (Vidhan Sabha election) | 90 | 20,626 | \~987 |
| Himachal Pradesh | 2024 (Lok Sabha election) | 68 | 7,990 | \~714 |
| Karnataka | 2024 (Lok Sabha election) | 224 | 58,571 | \~942 |
| Madhya Pradesh | 2024 (Lok Sabha election) | 230 | 63,346 | \~886 |
| Maharashtra | 2024 (Vidhan Sabha election) | 287 (of 288) | 99,210 | \~974 |
| Uttar Pradesh | 2024 (Lok Sabha election) | 403 | 161,955 | \~971 |

#### Voter Records: SIR Rolls (2025–26)

| State | Roll | No. of Assembly Constituencies (AC) | No. of Polling Stations (PS) / Parts | Mean Voters in a PS |
|:------------|:------------|:--------------|:--------------|:--------------|
| Gujarat | SIR final roll (published in February 2026) | 182 | 56,620 | \~785 |
| Karnataka | SIR draft roll (published in August 2026) | 224 | 60,923 | \~733 |
| Karnataka | SIR final roll (published in October 2026) | 224 | 60,923 | \~749 |
| Uttar Pradesh | SIR final roll (published in April 2026) | 403 | 177,310 | \~759 |

An SIR final roll reprints the SIR draft roll and adds new voters at the end of each part. Voters deleted after the draft stay printed with a deletion mark, which is kept in `DelOrAdd_Code` (E, S, R, M or Q; # marks a modified entry). New voters carry the supplement number in `Addition_List`.

#### Deleted Voter Records: ASDD Lists at the SIR Draft Stage (2025–26)

| State | Year | No. of Polling Stations (PS) / Parts | Mean Deleted Voters in a PS |
|:------------|:------------|:--------------|:--------------|
| Bihar | 2025 (SIR draft published in August 2025) | 90,578 | \~72 |
| Uttar Pradesh | 2025/26 (SIR draft published in January 2026) | 177,422 | \~162 |
| Delhi | 2026 (SIR draft published in August 2026) | 14,947 | \~318 |
| Karnataka | 2026 (SIR draft published in August 2026) | 60,736 | \~177 |
| Gujarat | 2025/26 (SIR draft published in December 2025) | 56,586 | \~130 |

#### Folderisation (Voter Records)

1.  StateName_StateCode_RollYear_ACxxx-yyy.tar.gz (for example, Haryana_S07_AE2024_AC001-090.tar.gz; SIR rolls: Karnataka_S10_SIRDraft2026_AC001-224.tar.gz)
    -   StateName_StateCode
        -   AC_NO
            -   Part_NO.CSV

GE2024 in a file name refers to the roll prepared for the 2024 Lok Sabha election, while AE2024 and AE2025 refer to the rolls prepared for the Vidhan Sabha elections of 2024 and 2025. FR2025 is Gujarat's final roll of January 2025, and SIRDraft2026 and SIRFinal2026 are the draft and final rolls of the 2025–26 Special Intensive Revision. ACxxx-yyy gives the range of AC numbers inside a file. Maharashtra's and Uttar Pradesh's rolls (including Uttar Pradesh's SIR final roll) are split across multiple files (part01, part02, and so on). In Uttar Pradesh's case, the third file (part03) holds 23 ACs that I processed later; these ACs fall within the AC ranges of the first two files but are not included in them.

#### Folderisation (SIR Deleted Voter Records)

1.  StateName_SIR_DeletedVoters_CSVFiles.tar.zst (Uttar Pradesh) and StateName_SIRYear_DeletedVoters_CSVFiles.tar.zst (Gujarat)

    -   AC-level CSV files of deleted voter records

2.  StateName_SIRYear_DeletedVoters_CSVFiles.tar.zst (Bihar, Delhi, and Karnataka)

    -   StateName_SIRYear_DeletedVoters
        -   One state-level CSV file of deleted voter records

------------------------------------------------------------------------

#### Potential validation checks

You can validate data fields by applying some basic checks. I have not implemented these because they might exclude voter records that are problematic within the roll itself, rather than errors from my OCR pipeline (for example, missing names or house numbers, duplicate EPICs, or ages greater than 125). Here is a suggestive list for such checks:

1.  Voter/Parent/Spouse Names: Are there names with just one character? Or voter names that do not make sense (such as "." or "\_")? Are there missing entries?
2.  Roll No & Voter ID: Are there roll numbers that exceed the typical maximum length of a roll (1500 voters + 20% margin of safety)? Any missing roll numbers or EPIC ID? Any EPIC ID that do not make sense (under 5 characters or over 30 characters)?
3.  Part Number: Any characters in this field instead of numeric values?
4.  Age: Unusual age numbers such as under 18 or over 110 years?
5.  Gender: Any values other than male, female, or third gender (in English or Hindi, depending on the state)?

------------------------------------------------------------------------

#### Acknowledgements

This project is supported by the [Global Democracy Commons](https://demos.berkeley.edu/) Initiative at the University of California, Berkeley.

This work has been challenging but also rewarding in exploring the frontier of machine learning and high-performance computing. It would not have been possible without the high-performance computing resources made available via:

1.  University of California, Merced’s Pinnacles cluster

2.  NSF ACCESS-CI Allocations (Grant Nos. SOC250025 and SOC250082), which provided access to:

    -   San Diego Supercomputer Center’s Expanse cluster

    -   Texas A&M University’s ACES and FASTER clusters

    -   Purdue University’s Anvil cluster

    -   Pittsburgh Supercomputing Center’s Bridges-2 cluster

3.  OSG Consortium's Open Science Pool

My text extraction script uses the Surya-OCR engine developed by Datalab.

Existing work on India’s machine-readable electoral rolls by Raphael Susewind as well as Gaurav Sood and colleagues' work served as an inspiration and a prototype to follow.

While I wrote the core scripts, I received troubleshooting support from a vendor. I also used generative AI tools for coding assistance. All errors are mine, of course.

------------------------------------------------------------------------

#### Additional Resources

1.  Raphael Susewind’s [work](https://github.com/raphael-susewind/india-religion-politics) parsing India’s voter rolls over years

2.  Gaurav Sood and colleagues’ [work](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/MUEGDT) to parse India's voter rolls (2015-17, I think?)

3.  S1D Labs' [release](https://labs.s1d.me/up-eci) of Uttar Pradesh's voter rolls (2024 to 2027)

4.  Datalab's fantastic [Surya-OCR](https://github.com/datalab-to/surya) engine

5.  [Diagram Chasing](https://diagramchasing.fun/), a publication of data-driven works of various interests

6.  Some music that I recommend :)

    -   Naveen Bharathi's lovely YouTube [channel](https://www.youtube.com/@naveenbharathi)

    -   The Inimitiable Begum Akhtar singing my favourite [ghazal](https://youtu.be/eEPcbMvKA0w?si=recg2p9p1JmknmB0)

    -   Ustad Nusrat's music on [OSA](https://www.youtube.com/@OrientalStarAgencies)
