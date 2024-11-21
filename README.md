<!-- PROJECT LOGO -->
<br />
<div align="center">
  </a>

<h3 align="center">Sentinel 4 Beginners</h3>

  <p align="center">
    This project was designed to help beginners or those new to setting up MS Sentinel with setting up your own little home lab (on the free trial version, can do this with the $200 credit provided by Microsoft)
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

The project was made to help upcoming individuals wanting to get hands on experience with setting up & using SIEM. This project includes how to enable & install data connectors, building out a detection rule using KQL, verifying logs are ingesting into Sentinel. 

<!-- GETTING STARTED -->

## Getting Started

To get started, feel free to go ahead and sign up for a free trial for Azure & set the account up. Don't worry, $200 will apply for 30 days & once per customer. 

### Installation

1. You will need to create a resource group & a log analytics workspace. You can simply search for these at the top on the search bar & type Resource Groups & Log Analytics Workspace
2. Once you've built both of them, you can make the analytics workspace which Sentinel will quote on quote link itself to. The page should look like this:
   ![Pasted image 20241121172837](https://github.com/user-attachments/assets/2256c0d5-5720-48aa-a4f1-b1ef71a75861)
3. Now you can search for Microsoft Sentinel & simply select the new workspace you've created & your page should look similar to this one:
   ![Pasted image 20241121173009](https://github.com/user-attachments/assets/c0df0fe0-8d56-4860-9ff9-0fcd2445ef21)
4. But.. Jack, I've loaded Sentinel & there's nothing here.. that is because we will need to set up data connectors to ingest data. Your page should look something like this.
![Pasted image 20241121173144](https://github.com/user-attachments/assets/29e4fda6-af8b-455c-86b7-153f77292d17)
5. Visit the content hub on the left side & you can see all the avaliable connectors. Note in this tutorial; we're only using the free ones. Simply pick the ones you are wanting & press install & go make a cup of tea, coffee or your favourite drink.
![Pasted image 20241121173250](https://github.com/user-attachments/assets/136c8f92-cdc0-450b-a5f3-c6b2ff40737f)
6. Whilst we're waiting on those to install, we want to ingest some logs from our very first device (woohoo!) so i've simply chosen to pick a Windows 10 machine & ingest this data into Sentinel. (yes, i've exposed the device to the public internet, but that's to get some failed RDP attempts..)
![Pasted image 20241121173749](https://github.com/user-attachments/assets/8d5450a7-4ea5-4dad-9917-04b43b03ff7a)
7. Once that is all set up, go back to Content Hub & install the Windows Security Events connector. In this tutorial, we'll be using the Events via AMA as the legacy one is being phased out by Microsoft. Once that is all installed, we will need to set up a data collection rule (DCR) to ingest this into our Sentinel workspace. Your page should look something like this:
![Pasted image 20241121174418](https://github.com/user-attachments/assets/9acb09a3-6f79-4d62-a920-98868ed3155f)
8. Select the VM you are wanting to ingest data into Sentinel, for us - we only have one so should look like this:
![Pasted image 20241121174452](https://github.com/user-attachments/assets/cfb79443-ac8d-4843-9b66-63bd94b70cca)
9. Give the collection rule a few moments to kick into gear & you should recieve data shortly. For example to check, go to logs & simply use the KQL syntax SecurityEvents to see if you are receiving Windows Security Event Logs. This is how mine looks:
![Pasted image 20241121180211](https://github.com/user-attachments/assets/746289aa-e0f4-48ad-9fe5-af3984dc66d6)
10. Let's say now you want to turn this query into a detection rule, simply follow the following steps. Simply press new Alert Rule & new scheduled rule. Your page should look like this:
![Pasted image 20241121180308](https://github.com/user-attachments/assets/5706cd86-0809-4007-8968-bd953a47a031)
Name the query whatever you'd like - for example, I named mine Successful Local Logins.
11. After a moment & you've configured the rule, give it a moment to kick in and it should appear in your analytics rule.
![Pasted image 20241121180405](https://github.com/user-attachments/assets/72bb3cdf-c308-4966-90e2-dcac80adc86f)
12. After a brief wait, your incident queue should have 1 alert for successful local logins to your VM you created earlier.
![Pasted image 20241121180439](https://github.com/user-attachments/assets/33cffb0d-1e91-4364-877e-aeb2a3193410)

And voila! You've set up your very first Sentinel instance! I hope you found this useful!
