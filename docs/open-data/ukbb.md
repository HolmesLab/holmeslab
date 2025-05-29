---
title: UK Biobank Data
parent: Open Source Data
nav_enabled: true
---

# Downloading Data from UK Biobank

## 1. **Register as a Researcher**

- Go to the UK Biobank Access Management System (AMS): [ams.ukbiobank.ac.uk](http://ams.ukbiobank.ac.uk)
- Create an account using your email - can be personal or Rutgers.
- Send Avram the email you used to sign up, and ask him to add you to as a collaborator to our lab project, “Structural genetic contributions brain function and behavior”, application ID 25163
- Once you’re added, check your account profile to see if you’ve been added to a project. Your account should look like this:
    
     [https://ams.ukbiobank.ac.uk/ams/resProjects](https://ams.ukbiobank.ac.uk/ams/resProjects)
    
    ![Screenshot 2025-05-22 at 3.52.10 PM.png](Downloading%20Data%20from%20UK%20Biobank%201fbcf00eb9368009b258e17c721c90ca/Screenshot_2025-05-22_at_3.52.10_PM.png)
    

---

## 2. Do the following courses:

The courses you need to do are listed in this section within your AMS profile: 

![Example of courses— this person has completed all but the MRC Research Course](Downloading%20Data%20from%20UK%20Biobank%201fbcf00eb9368009b258e17c721c90ca/Screenshot_2025-05-22_at_3.53.44_PM.png)

Example of courses— this person has completed all but the MRC Research Course

1. UKB course 1 - on UKB Profile
    1. Watch modules, take quiz 
2. UKB course 2 - on UKB Profile
    1. Watch modules, take quiz
- [**MRC course: “Research, GDPR & Confidentiality”**](https://bygsystems.net/mrcrsc-lms/enrol/index.php?id=71)
    1. The MRC course consists of 10 short video modules on various aspects of GDPR data security, including identifiable data, data sharing, and safeguards.
    2. To complete the course, you must pass a 10-question multiple-choice quiz with a score of 70% or higher. Your certificate should look like this:
    - Certificate image reference
        
        ![Screenshot 2025-05-22 at 3.54.34 PM.png](Downloading%20Data%20from%20UK%20Biobank%201fbcf00eb9368009b258e17c721c90ca/Screenshot_2025-05-22_at_3.54.34_PM.png)
        
    1. Steps to upload your certificate:
        - [Log in to your AMS](https://ams.ukbiobank.ac.uk/ams/) account
        - Select 'Profile'
        - Scroll down to 'Upload MRC certificate'
        - Select the blue 'Browse' button to the right
        - Upload your certificate in PDF format
        - Where to upload your certificate image reference
            
            ![Screenshot 2025-05-22 at 3.56.20 PM.png](Downloading%20Data%20from%20UK%20Biobank%201fbcf00eb9368009b258e17c721c90ca/Screenshot_2025-05-22_at_3.56.20_PM.png)
            

Listed on here: [https://community.ukbiobank.ac.uk/hc/en-gb/articles/22145292393757-Researcher-Training-Courses](https://community.ukbiobank.ac.uk/hc/en-gb/articles/22145292393757-Researcher-Training-Courses) 

## 3. **Get Approval and Dispense Data**

- Once approved, you'll get access to UKB-RAP via the **DNAnexus cloud platform**.
- You'll receive a RAP project with the approved data preloaded.

---

## 4. **Log In to UKB-RAP**

- Use your credentials to log in at: ukbiobank.dnanexus.com
- You'll be taken to your **project workspace** in the cloud.

---

## 5. **Set Up Your Environment**

- Choose between:
    - **JupyterLab**: Interactive Python/R environment
    - **Terminal (bash)**: For CLI tasks
- Install additional libraries (Python, R, bash) as needed
- Use the **Spark SQL database** for fast querying of tabular data

To learn how to use and manipulate data in the UKB-RAP, the documentation is here

## UKB-RAP Documentation

[Quickstart: Using the RAP](https://dnanexus.gitbook.io/uk-biobank-rap/getting-started/quickstart)

[Key concepts: Learn about the particularities of the Research Analysis Platform, and where to find detailed guidance on using its features.](https://dnanexus.gitbook.io/uk-biobank-rap/getting-started/key-concepts)

[Data structure: Learn how UK Biobank data is organized and named on the Research Analysis Platform. Learn how to find and access bulk files and tabular data](https://dnanexus.gitbook.io/uk-biobank-rap/getting-started/data-structure)

[Training Videos](https://dnanexus.gitbook.io/uk-biobank-rap/getting-started/training-videos)

### **Training resources**

The [**UKB-RAP training resources**](https://www.dnanexus.com/partnerships/ukb-rap-user-help-center/training) page allows you to specifically navigate to different video tutorials of the UKB-RAP. Some particular videos of note include the overview training  videos. [**Part 3](https://www.youtube.com/watch?v=foB7y2ZJHF4)** covers the cohort browser and how to explore and extract data, [**part 4**](https://www.youtube.com/watch?v=dm1xROYy1dA) talks about how to extract phenotype data using both table exporter and `dx extract_dataset`, whilst [**part 5**](https://www.youtube.com/watch?v=vJHzfqrDaFw) talks about the tools library with a focus on using Swiss Army Knife. 

Additionally, a particularly notable webinar video (found [**here**](https://www.youtube.com/watch?v=uT_jD1Ey3Fk)) guides you through data dispensal, project creation, data refreshing, dataset types and structures, basic file operations, apps in the UI and the considerations of cloud based analysis.

### **DNAnexus documentation**

[**The DNAnexus documentation page**](https://documentation.dnanexus.com/) provides detailed information on how to perform operations in the UKB-RAP using both the [**command line interface (CLI)**](https://documentation.dnanexus.com/getting-started/cli-quickstart) and the [**user interface (UI)**](https://documentation.dnanexus.com/getting-started/ui-quickstart), including how to [**run apps and workflows**](https://documentation.dnanexus.com/user/running-apps-and-workflows), as well as operate [**the cohort browser**.](https://documentation.dnanexus.com/user/cohort-browser) A particularly essential resource for users of the CLI is the [**index of dx commands page**,](https://documentation.dnanexus.com/user/helpstrings-of-sdk-command-line-utilities) which you can use to search for commands to perform operations like [**deleting](https://documentation.dnanexus.com/user/helpstrings-of-sdk-command-line-utilities#rm), [uploading](https://documentation.dnanexus.com/user/helpstrings-of-sdk-command-line-utilities#upload)** and [**downloading data**.](https://documentation.dnanexus.com/user/helpstrings-of-sdk-command-line-utilities#download) If you have questions about what data you can download, please see the following [**community forum post.**](https://community.ukbiobank.ac.uk/hc/en-gb/articles/19968494144157-Can-I-download-data-from-the-UKB-RAP)

### [UK Biobank Github notebooks](https://community.ukbiobank.ac.uk/hc/en-gb/articles/24597730355101-UK-Biobank-Github-notebooks)

To help researchers understand how to use the UKB-RAP, UK Biobank has created the **[UKB GitHub](https://github.com/UK-Biobank)** to offer code examples and insights for data analysis on the platform. 
This involves looking at how to access, extract and analyse data covering a range of data types, using Jupyter notebooks for both python and R, as well as Rstudio notebooks. More specifically, the [**A-series (Accessing Data) notebooks](https://github.com/UK-Biobank/UKB-RAP-Notebooks-Access)** focus on how to access and examine UKB phenotypic data, and the [**G-series (Genomics) notebooks**](https://github.com/UK-Biobank/UKB-RAP-Notebooks-Genomics) focus on performing genomics analytics workflows. Additionally, there are [**notebooks which allow individual SNPs to be filtered**](https://github.com/UK-Biobank/SNP-filtering) from the UKB genotyping data, as well as notebooks for researchers interested in [**executing complex, multi-stage workflows**](https://github.com/UK-Biobank/UKB-RAP-Workflows) on the UKB-RAP via [**apps, applets**](https://documentation.dnanexus.com/faqs/developing-apps-and-applets) and [**Workflow Description Language (WDL)**](https://github.com/openwdl/wdl). To learn more about these notebooks and how to access them, please see our [**UK Biobank GitHub notebooks**](https://community.ukbiobank.ac.uk/hc/en-gb/articles/24597730355101-UK-Biobank-Github-notebooks) article on the community forum which explains what there is on offer.

On a related note, DNAnexus also operates a a GitHub which offers some notebooks that you may find useful. For example, the [**basic data extraction notebook**](https://github.com/dnanexus/OpenBio/blob/master/UKB_notebooks/ukb-rap-pheno-basic.ipynb) guides you on how to extract phenotypic data, and the [**dx data notebook**](https://github.com/dnanexus/OpenBio/blob/master/dxdata/getting_started_with_dxdata.ipynb) can help you to load, access and retrieve metadata within datasets and cohorts.

Misc Documentation Pages:

[Setting up a project in the UKB-RAP](https://community.ukbiobank.ac.uk/hc/en-gb/articles/19982787052957-Setting-up-a-project-in-the-UKB-RAP)

[Finding data and how it is organised](https://community.ukbiobank.ac.uk/hc/en-gb/articles/26121043854365-Finding-data-and-how-it-is-organised)

[Working with RStudio](https://community.ukbiobank.ac.uk/hc/en-gb/articles/26206186769181-Working-with-RStudio)

[Working with Jupyter Notebooks](https://community.ukbiobank.ac.uk/hc/en-gb/articles/26224573928349-Working-with-Jupyter-Notebooks)

[How to access and use dispensed data](https://community.ukbiobank.ac.uk/hc/en-gb/articles/19982737660573-How-to-access-and-use-dispensed-data)

[Connect your UK Biobank AMS account to the UKB-RAP](https://community.ukbiobank.ac.uk/hc/en-gb/articles/19982750795165-Connect-your-UK-Biobank-AMS-account-to-the-UKB-RAP)

[Bulk data and using the tool library](https://community.ukbiobank.ac.uk/hc/en-gb/articles/26120097962397-Bulk-data-and-using-the-tool-library)

[Extracting phenotypic data](https://community.ukbiobank.ac.uk/hc/en-gb/articles/26205157055261-Extracting-phenotypic-data)

[How long does it take to be up and running with the data?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/19967877239069-How-long-does-it-take-to-be-up-and-running-with-the-data)

### **UKB-RAP costs**

For guidance on how much money you can expect to spend for computation and data storage on the UKB-RAP, please see the [**UKB-RAP Rate Card](https://20779781.fs1.hubspotusercontent-na1.net/hubfs/20779781/Product%20Team%20Folder/Rate%20Cards/BiobankResearchAnalysisPlatform_Rate%20Card_Current.pdf)** where you will find information on the cost per hour of using different instance types. You may also want to see our [**costs and billing page**](https://dnanexus.gitbook.io/uk-biobank-rap/administrator/billing-and-costs) and the [**costs & financial support webpage**](https://www.ukbiobank.ac.uk/enable-your-research/costs). To help reduce costs, remember to maintain good file management.

## **Find support**

The [**UKB-RAP help centre**](https://www.dnanexus.com/partnerships/ukb-rap-user-help-center) provides a page which links to various UKB-RAP support resources. 

If you have further questions about using the UKB-RAP, the [**UK Biobank community forum**](https://community.ukbiobank.ac.uk/hc/en-us/community/topics) is a great place to browse previously asked questions and to post your own inquiries to help out the wider research community. Alternatively, you can submit a ticket to get help from UK Biobank or contact DNAnexus support at [***ukbiobank-support@dnanexus.com***](mailto:ukbiobank-support@dnanexus.com) for assistance with any technical issues you may be facing.

If you are interested in looking through the metadata for fields in the UKB-RAP, you may also be interested in looking at the [**Showcase website**.](https://biobank.ctsu.ox.ac.uk/crystal/) Please see [**this article**](https://community.ukbiobank.ac.uk/hc/en-gb/articles/23472796568861-What-types-of-data-are-available-in-UK-Biobank) for more details.

## FAQs

Registering:

[What do I need to register for access?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15006592398493-What-do-I-need-to-register-for-access)

[Verifying an email address after submitting your AMS registration](https://community.ukbiobank.ac.uk/hc/en-gb/articles/24841260302877-Verifying-an-email-address-after-submitting-your-AMS-registration)

[How are my details checked?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15453660199197-How-are-my-details-checked)

[How long will it take for my registration to be reviewed?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15453266783773-How-long-will-it-take-for-my-registration-to-be-reviewed)

[How can I confirm my place of work?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15453253185309-How-can-I-confirm-my-place-of-work)

[How do I update the institute section of my registration?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15009554130589-How-do-I-update-the-institute-section-of-my-registration)

Applying for Access:

[Will UK Biobank complete a supplier set up form or supplier questionnaire issued by my institution?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/26649215176733-Will-UK-Biobank-complete-a-supplier-set-up-form-or-supplier-questionnaire-issued-by-my-institution)

[How to: Complete an access application](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15453619166749-How-to-Complete-an-access-application)

[Sign a Material Transfer Agreement (How to VIDEO)](https://community.ukbiobank.ac.uk/hc/en-gb/articles/14990876415645-Sign-a-Material-Transfer-Agreement-How-to-VIDEO)

[Who should I provide for an MTA contact?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/19982881759389-Who-should-I-provide-for-an-MTA-contact)

[How do I add an MTA contact to my application?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/19982830095005-How-do-I-add-an-MTA-contact-to-my-application)

[Lay summary guidance](https://community.ukbiobank.ac.uk/hc/en-gb/articles/17596044137501-Lay-summary-guidance)

Introductory Training:

[Researcher Training Courses](https://community.ukbiobank.ac.uk/hc/en-gb/articles/22145292393757-Researcher-Training-Courses)

[How do I upload my MRC certificate to my AMS profile?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/26348085571869-How-do-I-upload-my-MRC-certificate-to-my-AMS-profile)

[I’ve completed training, when will my profile be updated?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/22759559490333-I-ve-completed-training-when-will-my-profile-be-updated)

[I have completed my training, so why can’t I access the UKB-RAP?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/19968114375069-I-have-completed-my-training-so-why-can-t-I-access-the-UKB-RAP)

Managing Projects: 

[How can I remove a collaborator from my project?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/25614267880221-How-can-I-remove-a-collaborator-from-my-project)

[How do I extend the scope of my project?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/23358616000797-How-do-I-extend-the-scope-of-my-project)

[How do I change the tier of my project?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/23358302128413-How-do-I-change-the-tier-of-my-project)

[How do I extend the duration of my project?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/23357596850333-How-do-I-extend-the-duration-of-my-project)

[Who should I list as the DPO contact at my institute?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/19982770908445-Who-should-I-list-as-the-DPO-contact-at-my-institute)

[How to create a UKB-RAP account](https://community.ukbiobank.ac.uk/hc/en-gb/articles/19357348088733-How-to-create-a-UKB-RAP-account)

[What is the UKB-RAP?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/16593040085661-What-is-the-UKB-RAP)

[Make a change request for your project in AMS (How to VIDEO)](https://community.ukbiobank.ac.uk/hc/en-gb/articles/14990686460829-Make-a-change-request-for-your-project-in-AMS-How-to-VIDEO)

[Logging into the UKB-RAP](https://community.ukbiobank.ac.uk/hc/en-gb/articles/19357387312925-Logging-into-the-UKB-RAP)

[Submitting an annual report](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15013553517213-Submitting-an-annual-report)

[How do I add researchers to my project?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15010106167197-How-do-I-add-researchers-to-my-project)

[How do I access the restricted home location data?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15014023559837-How-do-I-access-the-restricted-home-location-data)

[Why are the tabs on my project inaccessible?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15013414705181-Why-are-the-tabs-on-my-project-inaccessible)

[How do I transfer PI status?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15007295597085-How-do-I-transfer-PI-status)

[What do I need to do to close my project?](https://community.ukbiobank.ac.uk/hc/en-gb/articles/15013815891741-What-do-I-need-to-do-to-close-my-project)