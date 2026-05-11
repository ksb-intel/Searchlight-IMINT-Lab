# Searchlight — IMINT Lab

## Overview

<img width="2327" height="892" alt="image" src="https://github.com/user-attachments/assets/fa7ecdd1-6796-4fd3-82f3-3a11e9fd369b" />

<br>
A write-up of the TryHackMe room Searchlight - IMINT, involving Image Intelligence (IMINT) and Geospatial Intelligence (GEOINT). Each task presents an image to geolocate utilizing visual analysis, reverse image search, and other open-source tools.


## ⚠️ Disclaimer

All reconnaissance in this lab was conducted passively using publicly available information. This lab is for educational purposes and should not be used for unauthorized or malicious activity.

---

## What is IMINT / GEOINT?

**IMINT (Imagery Intelligence)** is the practice of extracting actionable intelligence from images and videos. **GEOINT (Geospatial Intelligence)** extends this to geographic context by identifying where something is, when it happened, and what the surroundings tell us.

According to GEOINT expert [Benjamin Strick](https://twitter.com/BenDoBrown), there are five core elements to consider when analyzing an image:

- **Context** — what is the broader setting or scenario?
- **Foreground** — what's immediately visible and identifiable?
- **Background** — what environmental or structural details exist behind the subject?
- **Map markings** — are there visible signs, text, or symbols with geographic significance?
- **Trial and error** — when the obvious fails, iterate

**Key questions to ask yourself:**
- Are there obvious data points in the image — street names, storefront signs, license plates?
- Can you determine the country or region from architecture, language, or which side of the road traffic uses?
- Do you recognize road sign styles, infrastructure quality, or vehicle types?
- Are there unique landmarks, bridges, statues, or mountains that anchor the location?

---

## Tools Used

| Tool | Purpose |
|------|---------|
| Google Reverse Image Search | Identify locations and subjects from images |
| [TinEye](https://tineye.com/) | Check image index history and find prior appearances |
| [RevEye Browser Extension](https://chrome.google.com/webstore/detail/reveye-reverse-image-sear/keaaclcjhehbbapnphnmpiklalfhelgf) | Multi-engine reverse image search (Google, Bing, Yandex, TinEye, Baidu) |
| Google Street View | Verify locations and compare with historical captures |
| Google Maps | Locate targets and confirm geographic context |
| [FFmpeg](https://ffmpeg.org/) | Extract key frames from video for analysis |
| [visitoslo.com](https://www.visitoslo.com/) | Interactive outdoor sculpture map — used in Task 7 |

---

## Metadata

| Field | Detail |
|-------|--------|
| Source Room | [TryHackMe — Searchlight IMINT](https://tryhackme.com/room/searchlightosint) |
| Disciplines | IMINT, GEOINT, OSINT |
| Methodology | Passive analysis — reverse image search, visual extraction, open-source verification |
| Classification | Training exercise |
| References | [Bellingcat Reverse Image Guide](https://www.bellingcat.com/resources/how-tos/2019/12/26/guide-to-using-reverse-image-search-for-investigations/) · [OSINT Curious](https://www.osintcurio.us/) |

---

## Executive Summary

This lab demonstrates the utilization of IMINT through a series of geolocation tasks. Using reverse image search, visual analysis of foreground and background elements, and open-source corroboration, each image was successfully geolocated. The most analytically demanding tasks required layered inference: using one identifiable text fragment to narrow geography, then cross-referencing architectural features with Street View to confirm.

---

## Geolocation Challenges

### Task 1 — The Street

<img width="630" height="420" alt="image" src="https://github.com/user-attachments/assets/5f2567a1-f5fd-45c3-9394-5de5e033890a" />

<br>

**Q: What is the name of the street where this image was taken?**

**Answer: Carnaby Street, London, United Kingdom**

Clearly we can see this is Carnaby Street from the arched signage. After searching the location on Google, the street is a well-known shopping strip located in London, United Kingdom. This image specifically is not recent however, as the businesses "Fornarina" on the left and "Make Up Store" on the right are no longer present, as seen below. 

<img width="1352" height="826" alt="image" src="https://github.com/user-attachments/assets/ac3934e5-4d11-4e2e-84e1-da3a77c54833" />


<br>

This is the best image found to demonstrate the two buisnesses are changed, additionally, on Google Maps they are no longer listed. dentifying the building on the left that connects to the "Carnaby Jubilee" sign closely resembles the second story business on the left side of the original image. The business to the right has the same greenery above the storefront, and the building architecture appears the same as well. 


<img width="1180" height="715" alt="image" src="https://github.com/user-attachments/assets/1790503b-5efb-4a9d-a699-38e3d4fde31c" />

<br>

Looking at the older dates on this street view, we can find a capture taken in Jul 2012 with the same two businesses "Fornarina" on the left and "Make Up Store," which confirms that this is the correct location. The next image is dated in Oct 2017, with these specific businesses gone indicating that the original image was taken at least before 2017. 

The Fornarina store itself was notable for it's interrior design, featuring a high-tech, experimental, modern, and feminine architecture, winning awards like the 2007 AIA LA Design Award. The store was designed by Giorgio Borruso and the picture below was photographed by Benny Chan.

<img width="432" height="552" alt="image" src="https://github.com/user-attachments/assets/a48ed474-2c66-442e-b993-c69eac184ad3" />

<br>

This challenge demonstrates IMINT involves making time-based observations as well as locational.

---

### Task 2 — The Tube

<img width="1800" height="1440" alt="image" src="https://github.com/user-attachments/assets/f2faf47d-38b9-4047-a46c-9ba2d21ec039" />

<br>

**Questions:**
- Which city is the tube station located in?
- Which tube station do these stairs lead to?
- Which year did this station open?
- How many platforms does this station have?

**Answers:**
- **City:** London, United Kingdom
- **Station:** Piccadilly Circus Underground Station
- **Year opened:** 1906
- **Platforms:** Four

<br>

After reverse image searching the image, results for **Piccadilly Circus Underground Station** located in London, United Kingdom populated immediately across multiple sources.

<img width="1193" height="870" alt="image" src="https://github.com/user-attachments/assets/106eaecf-e994-44d8-ab76-7a73541d6ac5" />

<br>

This task introduces **contextual questions**  by provding more information beyond the physical location of a target. 

---

### Task 3 — The Food Court

<img width="478" height="267" alt="image" src="https://github.com/user-attachments/assets/6b53bc01-9101-4941-a02e-420d06dccd90" />

<br>

**Questions:**
- What is the name of the airport the image was taken at?
- In which city and country is this airport located?

**Answers:**
- **Airport:** Vancouver International Airport (YVR)
- **Location:** Richmond, British Columbia, Canada

<br>

The image shows an overhead view of a food court. The key identifier is a banner in the back corner of the food court reading **"YVR CONNECTS"** and the domain `YVR.CA`. Running `site:YVR.CA` as a Google dork confirmed this as the Vancouver International Airport. Additionally we can see in the top left, a person dragging a suitcase, indicating this location as an airport terminal. However, that information without the banner would make it difficult to analyze which airport this is alone (without the use of reverse image searches). 

<img width="1112" height="863" alt="image" src="https://github.com/user-attachments/assets/3218bad6-af90-4324-a7b3-ba6cc9d356e8" />

<br>

Google searching "site:YVR.CA" which brought results from "Vancouver International Airport." From there, identifying the building as the airport and finding the city and country came simply. The Vancouver International Airport is in Richmond, Canada. 

<img width="1095" height="794" alt="image" src="https://github.com/user-attachments/assets/c050fb92-dc96-483a-b44d-54e3432237f3" />

<br>

This challenge shows how powerful signage and text can be in geolocation. 

---

### Task 4 — The Coffee Shop

**<img width="494" height="695" alt="image" src="https://github.com/user-attachments/assets/0ddc2af8-b2cd-4c2c-8350-9087a845ccba" />**

<br>

<img width="659" height="876" alt="image" src="https://github.com/user-attachments/assets/ceb933a6-4033-4118-bfe1-2ca9480b7248" />

<br>

**Questions:**
- What is the name of the coffee shop?
- What is the phone number?
- What is the email address?

**Answers:**
- **Coffee shop:** The Wee Coffee Shop, Blairgowrie, Scotland
- **Phone:** +44 7878 839128
- **Email:** theweecoffeeshop@aol.com

<br>

The first image (overhead food shot) has no obvious geographic identifiers. The second image contains the only identifyable text reading **"Edinburgh Wollen Mill"**  on the front of a white and red building across the street. Edinburgh Woolen Mill operates multiple locations across the United Kingdom, so the next step was searched all the stores located in Scotland, and cross referecning until one was found that matched the architecture in the image/ 

<img width="850" height="676" alt="image" src="https://github.com/user-attachments/assets/7f0bb2d9-9ff2-4e4e-ac82-5e8c8ffcd90a" />

<br>

The Blairgowrie [location](https://maps.app.goo.gl/67zQuYzqdMz6Z4EUA) matches the provided image with the distinct red architecture. The coffee shop across the street is "The Wee Coffee Shop," which is most definitely the one in the original image.

<img width="1101" height="884" alt="image" src="https://github.com/user-attachments/assets/515879b9-9516-4563-8864-4315fbb566ce" />

<br>

he coffee shop across the street is "The Wee Coffee Shop," which is most likely the one in the original image.

<img width="896" height="888" alt="image" src="https://github.com/user-attachments/assets/a1f763d2-e10a-4a64-bf7b-63f400687a53" />

<br>

The Wee Coffee Shop's Facebook page had identifiable information for the rest of the questions of this assignment such as phone number, email, and owner's name. 

**<img width="977" height="700" alt="image" src="https://github.com/user-attachments/assets/d1e72f30-7278-40d9-9b40-8e9dbb2ae34e" />
**

<br>

---

### Task 5 — Reverse Image Search (Katz's Deli)

<img width="337" height="450" alt="image" src="https://github.com/user-attachments/assets/9fb929c9-56f5-41c1-97f9-7bcd11741030" />

<br>

**Questions:**
- What is the name of this restaurant?
- What is the name of the Bon Appétit editor who worked 24 hours at this restaurant?

**Answers:**
- **Restaurant:** Katz's Delicatessen, New York City
- **Editor:** Andrew Knowlton

<br>

Running the image through [TinEye](https://tineye.com/) returned two results — both from other people's lab writeups doing the same exercise. By reverse image search via the **RevEye extension** on Google, results populated for "Katz's Delicatessen" which is a famous deli found in New York City, popularized for being in *When Harry Met Sally*.

<img width="1243" height="896" alt="image" src="https://github.com/user-attachments/assets/55edee90-9082-46f3-80c7-6303ffbdda39" />

<br>

Querying "katz's deli bon appetit" found search results for the editor who worked a 24 hour shift, Andrew Knowlton. 

<img width="953" height="742" alt="image" src="https://github.com/user-attachments/assets/cb219a4f-32d6-4995-9f62-f9f8109ca138" />

<br>

---

### Task 6 — Locate the Sculpture

<img width="2048" height="1536" alt="image" src="https://github.com/user-attachments/assets/5d72d631-8476-432e-b066-53ff4a366cf7" />

<br>

**Questions:**
- What is the name of the sculpture?
- Who created it?
- Who photographed it?
- Where exactly is it located?

**Answers:**
- **Sculpture:** Rudolph the Chrome Nosed Reindeer (2012)
- **Artist:** Magne Furuholmen (of the band Apparatjik)
- **Photographer:** Kjersti Stensrud
- **Location:** Tjuvholmen neighborhood, Oslo, Norway

<br>

Since there are no clear signage or text to indicate the geographical location, the only option is to utilize reverse image searches. Google search results show the sculpture is titled *Rudolph the Chrome Nosed Reindeer.* The sculpture was created by  Magne Furuholmen and is located in the Tjuvhilmen neighborhood of Oslo Norway. 


<img width="1163" height="774" alt="image" src="https://github.com/user-attachments/assets/3be672ed-82ef-4a12-be1c-6c4d28e08fb4" />

<br>

The photographer's name came from the [Visit Oslo](https://www.visitoslo.com/) interactive outdoor sculpture map, which lists the photographer credit as Kjersti Stensrud.

<img width="1573" height="741" alt="image" src="https://github.com/user-attachments/assets/4ad4965c-41a3-4837-99fe-0017056721dd" />

<br>

---

### Task 7 "And Justice for All?" — Lady Justice

<img width="915" height="612" alt="image" src="https://github.com/user-attachments/assets/e9424eb2-ff20-4e40-8127-a1314bc4f5e3" />

<br>

**Questions:**
- What is this statue?
- Where is it located?
- What is the building opposite?

**Answers:**
- **Statue:** Lady Justice (Iustitia)
- **Location:** Albert V. Bryan US Federal Courthouse, Alexandria, Virginia
- **Building opposite:** The Westin Alexandria Old Town

<br>

An initial text search for "Blind Justice Statue" surfaced the Wikipedia page for Lady Justice, however the exact statue in this image could not be identified. Reverse image search confirms that this figure is indeed Lady Justice. This statue specfiically is located outside  the Albert V. Bryan US Federal Courthouse in Alexandria, Virginia.

<img width="1014" height="728" alt="image" src="https://github.com/user-attachments/assets/fd4b684c-fce8-47d4-b8a1-5266f1392d5b" />

<br>

The building opposite of this statue is The Westin Alexandria Old Town.

<img width="1416" height="889" alt="image" src="https://github.com/user-attachments/assets/56530b89-3d36-4304-8468-1ff59633e059" />

<br>

Lady Justice (Latin: *Iustitia*) is an allegorical personification of the moral force in judicial systems. Her attributes are a scale, a sword, and sometimes a blindfold. The blindfold, originally a satirical addition to suggest justice was blind to the injustice before her, has been reinterpreted over time to represent impartiality — justice applied without regard to wealth, power, or status.

---

### Task 8 — The View From My Hotel Room

**Questions:**
- What hotel was this video taken from?
- In which city?

**Answers:**
- **Hotel:** METT Singapore
- **City:** Singapore

<br>

Videos hold a lot more images that can be analyzed. The lab suggests a [writeup](https://nixintel.info/osint-tools/using-ffmpeg-to-grab-stills-and-audio-for-osint/) by [Nixintel](https://twitter.com/nixintel) on a tool called [FFmpeg](https://ffmpeg.org/), which helps extract key images from videos. 

From the video we can see the words "Clarke Quay Central" and when searching that reveals a shopping center in Singapore. Across the way, following the video's recorded angle, is a hotel METT Singapore, the likely location of where the video was taken. 

<img width="1516" height="909" alt="image" src="https://github.com/user-attachments/assets/e51b760e-8514-410f-823e-5736b5be27a9" />

<br>

---

## Analytical Notes — "A Lesson on Looking"

The room recommended watching [*A Lesson on Looking*](https://www.ted.com/talks/amy_e_herman_a_lesson_on_looking), a TED Talk by Amy Herman on visual intelligence. Key takeaways:

- Looking closely can save a life — and a business
- **Looking is not seeing.** Visual intelligence means understanding how to look *slowly*, and remembering to step back before drawing conclusions
- Art trains you to think twice before coming to a judgment
- The **4 A's** framework for visual intelligence: **Assess → Analyze → Articulate → Act**
- Saying what *isn't* there is often as valuable as what is

The task image associated with this section was "The Castle" (2007) by Jorge Méndez Blake — a full brick wall with a single small book placed at the base, creating a ripple that disturbs the entire wall above it. The piece illustrates how a small, seemingly insignificant element can alter large, established structures. In the context of IMINT: a single data point can shift the analysis.

<img width="998" height="331" alt="image" src="https://github.com/user-attachments/assets/355c62cb-b5dd-4e4b-a782-87a114507b8d" />
<br>

---

## Skills Practiced

- Reverse image searching across multiple engines (Google, TinEye, Yandex via RevEye)
- Visual extraction of geographic indicators from foreground, background, and context
- Cross-referencing findings with Google Street View historical captures
- Temporal analysis, using business presence/absence to bracket image dates
- Video frame extraction for OSINT analysis
- Open-source corroboration of geolocation findings

---

## References

1. TryHackMe. [Searchlight - IMINT](https://tryhackme.com/room/searchlightosint). Accessed 05-08-2026.
2. Bellingcat. [Guide to Using Reverse Image Search for Investigations](https://www.bellingcat.com/resources/how-tos/2019/12/26/guide-to-using-reverse-image-search-for-investigations/).
3. [OSINT Curious](https://www.osintcurio.us/)
4. Nixintel. FFmpeg for OSINT video analysis.
5. Herman, Amy. [A Lesson on Looking](https://www.ted.com/talks/amy_e_herman_a_lesson_on_looking). TED.
6. [Visit Oslo — Outdoor Sculpture Map](https://www.visitoslo.com/)
