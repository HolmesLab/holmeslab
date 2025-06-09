---
title: Clinical Interview Session
parent: Psychiatric Connectomics
has_toc: true
nav_order: 5
---

# Script for Clinical Interview Session
---
**Table of Contents**
1. TOC
{:toc}
---

```bash
{: .new-title }
> Green Callout 
> **Payment Method**:
> - CCNP pays directly at the end of the session
> - Holmes Lab pays via Visa E-Gift Card which will be emailed to you, which you can use for purchases, but cannot add to your bank account 
> **Payment by Session**:
> $20/hr for SCID + Clinical Surveys Session (SCID = 1hr control, 1.5hr patient. Surveys session = 1hr control, 1.5hr patient)
> $60 for the MRI Scan session, ~3 hours (1.5hr MRI)
> $30 for an optional additional set of online surveys, wnich would take around 1hr
> An optional smartphone tracking component, where you would be paid based on the number of daily surveys you complete:
> $5 for 5-9 surveys completed 
> $10 for 10-14 surveys completed
> $15 for 15-19 surveys completed
> $30 for 20-24 surveys completed
> $35 for 25+ surveys completed
> -> For up to 6 months ($210 maximum total for the smartphone component)  
```


## Introduction
*Hi! Thank you for coming in today. I’m going to be reading from a script to make sure each participant has a similar experience.*

*You are being invited to participate in a research study on individual differences in how the brain functions. We hope that this data will allow us to better understand the bigger questions of how people vary in their behavior, and how those variations come about.*

*I'll give you a brief overview of our procedures, and then you can read more specifics in the consent form.* 

# 1. Consents
## 1.1 Clinical Interview (Holmes 01) Consent Form
[Holmes 01 Consent Form](https://rutgers.ca1.qualtrics.com/jfe/form/SV_byE8zSL9wiv3PLM) (Qualtrics)

*The first thing we’re going to do is go over the consent forms. This study is being led by Dr Avram Holmes, who is a faculty member in the department of Psychiatry. Their study consists of this session today and a second session with an MRI scan. The first consent form is a consent for the activities we’ll ask you to do today, which include a structured clinical interview, which will take 20min-2hours. This is exactly like the interview you did with us when you first came into CCNP, we’re just doing it again to make sure the diagnosis is up to date. After that, I may ask you some more questions about your symptoms specifically in the last two weeks. The third thing we’d do today is an online survey. I would send you the link and you would fill it out yourself. This is expected to take around 1 hour. 

*You'll be paid $20/hour to do this study, as well as reimbursed for your travel costs.*

*Signing this consent form confirms that you are willing to do these activities and willing to have your information shared with the study staff at Dr Avram Holmes’ lab, so they can schedule with you the MRI scanning session. I’ll let you read through the consent form now, let me know if you have any questions.* 



## 1.2 MRI & Smartphone Session (PCR) Consent Form
[PCR Consent Form](https://rutgers.ca1.qualtrics.com/jfe/form/SV_8vK8CJMuW2iNcmG) (Qualtrics)

*The second consent form is for the MRI scanning session. If you sign this form today, you’ll also be asked to sign the same form when you go in for the MRI scan. You can always decide not to participate, even if you sign it today. This consent form goes over the activities you would do in this session and the second session. These include some more surveys, a 90 minute MRI scan and some optional components. The optional components are adding your data to the data repository, and a smartphone-app tracking study.* 

*You'll be paid $60 for the 2.5 hours of MRI and surveys at the MRI session, and will receive a link to do an additional 1hr of surveys at home, for an additional $30*

*There is also an optional smartphone tracking component, where you would be paid based on the number of daily surveys you complete:*
        - $5 for 5-9 surveys completed 
        - $10 for 10-14 surveys completed
        - $15 for 15-19 surveys completed
        - $30 for 20-24 surveys completed
        - $35 for 25+ surveys completed
*This would last for up to 6 months ($210 total for the smartphone component). However, you can uninstall the app at any time if you would like to leave the study.*


**Signature Boxes:**
*The first signature box is allowing us to use your de-identified data in the datasets we upload to data sharing sites, so that other researchers can use it. This is an optional component.*

[Have them read the first page and sign]

*The second signature box is for the smartphone app portion of the study, where you could earn additional money to answer daily questions on your smartphone for up to 6 months. This is an optional component.*

[Have them read the second page and sign]

*Then the form discusses risks and benefits. Then the third signature is the main part of the study. It involves the surveys today, the supplemental survey, and the MRI scan. It also involves allowing us to share your private health information, including identifiable information such as your name, with only the groups listed.*

[Have them read the third page and sign]


**Note: Post-Consent Email**
An email gets automatically emailed to the participant through Qualtrics after they sign the consent forms, with a copy of their signed consent forms.

## 2. Enter Participant into ID-Linking Sheet
First, go the sheet in Box located at `/(Restricted)_PCR/PCR_Shared_with_CCNP/PCR_Linking_ID_CCNP.xlsx`.  
Enter this subject, assigning them a PCRID and a qualtrics ID.


## 3. Clinician Rating Survey + Self Report Scales

- Message to the subject (on chat if on zoom) the link to Psych Connectomics Clinical Visit Self Report Scales (https://rutgers.ca1.qualtrics.com/jfe/form/SV_78QRYTSOnegCSjQ) & their  (duration: ~50 minutes) 

*I've just messaged you a link in the chat. Can you open that link and share your screen with me?*

*Ok, great. Please enter this ID in the "qualtrics id" box*

- Message in the chat their qualtrics ID

*Now go ahead and start filling otu the survey. After every few surveys there will be a screen asking you to notify me. I may ask you some more questions during those times, or I may ask you to keep going. These surveys should take about 40 minutes.*


After they finish, Check [Self-Report Scales](https://rutgers.yul1.qualtrics.com/reporting-dashboard/web/6759f2274afe9f0008e00f36/pages/Page_7691eb9e-0279-4dea-b9f6-75c7541d5cfc/view?surveyId=SV_78QRYTSOnegCSjQ) (<- link to survey responses) for QIDS-SR scale question qids_12, deals with suicidal ideation
QIDS response is a 6, administer [Holmes Lab Suicide Risk Assessment](https://rutgers.ca1.qualtrics.com/jfe/form/SV_1Nb3mdge9pfjlnE) 
    - 2-4 questions, very fast
    - Logic displays what to do based on answers



### Notes for Interviewer 
> NOTE: These 4 surveys are in order of *content*, NOT separated by survey-- so a BPRS question may be in the middle of 2 PANSS questions, etc. 
> NOTE: 0=not assessed, 1=not present. Make sure to choose 1 if an item isn’t present. 
> NOTE: PANSS P questions- If people don’t have mania / schizoaffective disorders, **first ask if anything has changed in their symptoms in the last week.**
    - If they mention anything, you can ask further to see if any of the psychosis/mania (PANSS questions are relevant. 
    - If not, you can skip those questions (mark them as “not present" )
> NOTE: PANSS G+N, YMRS questions - Please still include+rate these scales, even if participants don’t have a history of mania/psychosis. We use these for factor analyses across symptom groups. 

- PANSS (guiding questions are optional if you have enough information from the SCID)
    - About the last week
    - Questions are similar to PANSS official guiding questions, and are consistent with our prior data collection of these scales
- MADRS  (guiding Q’s as needed) 
    - Questions are similar to MADRS official guiding questions, and are consistent with our prior data collection of these scales
- BPRS (overlaps with PANSS guiding Q’s; also as needed) 
- YMRS (guiding Q’s as needed)
- C-SSRS (only use when SI has been endorsed a.k.a as normal)
    - NOTE: CSSRS will only come up depending on the answer to MADRS Question 10, which is about suicidal ideation and intent. 



## 6. Payment
Once they've submitted, send them their payment.


---

# Protocol Overview
If the participant has questions or would like you to explain additional informaiton, here is a selection of study information: 

### Payment
- $20/hour for today's session, wihch is expected to last 2-3 hours. We will pay you via a gift card at the end of the session
- The rest of the sessions would be run by a collaborating group, who will pay you in Visa gift cards emailed to you at the end of each session
    - $60 for the MRI Scan session, which is expected to last around 3 hours
    - $30 for an optional additional set of online surveys, wnich would take around 1hr
    - An optional smartphone tracking component, where you would be paid based on the number of daily surveys you complete:
        - $5 for 5-9 surveys completed 
        - $10 for 10-14 surveys completed
        - $15 for 15-19 surveys completed
        - $30 for 20-24 surveys completed
        - $35 for 25+ surveys completed
    For up to 6 months ($210 total for the smartphone component)  


### **Scan Session Overview**
At the scanning session, this is what will happen: 

First, you're going to fill out a collection of surveys online, which will take about an hour, asking you about your mood, emotions and history.

After that, they'll take you through some of the tasks that we're going to be doing just on my computer here, so that you'll know what to expect when we get into the MRI room.

After that, you're going to walk down to the MRI room. You're going to have you change into a scrub top, but you can keep your pants - anything from the waist down. You'll also take off your shoes before going into the scanner. 

The large, donut-shaped machine in the room down the hall is the MRI scanner, which uses a magnetic field (***not*** ionizing radiation) to take pictures of your brain. The MRI scanner is like a really old camera, so you have to stay really still because it takes pictures of your brain over time. And so if you move, then the pictures will be blurry.

During the MRI study, they'll run a few different scans -- during these scans, you'll try to lie as still as possible. You will also play do some simple tasks that we’ll go over in just a second. You'll also watch some short films, and a planet earth episode. 

After the scan they're going to have a few more questionnaires which will take about 20 minutes.

We anticipate that the MRI session will take no more than 3 hours. You’ll be compensated with $60.


### Smartphone Tracking

You can opt into a smartphone tracking research that we're doing. Basically it will be on your phone - it's an app. It won't take any of your cellular data but it will occasionally (every 3 minutes or so) check your GPS location and it will also check things like how fast you're moving using the accelerometer. It will also check how many times your phone turns on and off.  

This will give us an idea of things like your activity during the day, how much you're sleeping, how much you're moving, how much exercise you're doing.
The other part of the app is daily surveys where it will ask you about 10 questions every day. It'll pop up at 6pm but we can change that specific time. Then you'll answer questions about your mood and what you've been doing during the day.

The reason that we are interested in this is because it can give us an insight into how people's behavior affects their mood and how different people with different brain profiles may have different activity patterns or mood relationships that we can investigate with this long-term data.

This will run for a maximum of **six months**, but if you would like to leave the study at any time during that period, you can always **uninstall the app and it will stop collecting data.**

### **Data Privacy**

All of the data we collect in this study will be de-identified and stored securely in our lab, to protect your privacy. So instead of your name, all your data will be associated with a numerical ID, and the link to your name is stored on a protected, HIPAA-compliant document. So even when sharing with collaborators or other researchers, we'll never disclose your personal information.  The only people who could see things like your name, your birthday, your email, would be people who are directly staffed in this lab. 

Your participation in this study is totally voluntary, so you’re free to stop participating at any point; just let us know.


## Suicidality Procedures
If a participant endorses suicidality, the study-staff (trained post-baccalaureate, postdoctoral researcher, and/or graduate student member(s) of the research team) will conduct a thorough suicide risk assessment. If the study-staff assesses imminent risk to the participant or to others, and the participant is unwilling to contact his/her current treatment provider to arrange for a prompt crisis session and to engage in suicide contracting, the study-staff will contact UBHC Psychiatric Emergency Services. The study staff escort the at-risk study participant to UBHC Psychiatric Emergency Services, one building over from the lab space (671 Hoes Lane Piscataway, NJ 08854). If a participant that the study-staff has assessed to be imminently at risk leaves the debriefing session without first contacting a provider and making arrangements that reduce risk, the study-staff will contact Rutgers Security and provide the name and contact information of the at-risk individual. The Director of Clinical Training and the IRB will also be contacted in such an incident. The study-staff will consult with the study PI, Dr. Avram Holmes immediately following each suicide assessment and before a participant has left the lab. Together, the study-staff and the consulting faculty member will determine the participant’s risk status and appropriate course of action.

If the participant is judged not to be an imminent risk to him/herself and/or others, the study-staff will debrief with the participant, in which s/he will discuss the participant’s extreme score, provide psycho-education about depression and/or anxiety, discuss any distress they may be experiencing, and suggest referrals to local treatment providers.

Regardless of risk status, each participant with extreme scores will be strongly encouraged to contact their mental health treatment provider, if they do not have one, or to make an appointment with a new provider. They will also be offered the option of being contacted by Dr. Avram Holmes, a Professor in the Rutgers Psychiatry Department. If participants desire, Dr. Avram Holmes will be contacted and provided with the participant’s name and email address, and will follow up the participant within 24 hours whenever possible with the following email message:

“I am a professor affiliated with Rutgers University - From your answers to one of the questionnaires in a psychology research study, you seemed to be feeling quite down and blue/anxious. You were provided with some information about counseling services at the end of your participation in the study, but I wanted to follow up and offer to provide any other referral information you might want. If you would prefer to discuss this over the phone, please send me your phone number and some preferred times and I will do my best to reach you at a time that is convenient for you."




