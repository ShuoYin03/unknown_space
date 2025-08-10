---
title:       "Sweden Companies Contacts Scraping - CEO & Project Managers Emails"
subtitle:    "Efficient Data Extraction for Key Business Contacts"
description: "Google Search API & Email Extraction & Email Verification"
date:        2025-07-24
author: UNKNOWN_SPACE
URL:         "/2025/07/24/sweden-contact-scraping"
image:       ""
tags:        ["Scraping", "Case Study"]
categories:  ["post"]
---

### Project Overview

The client’s website hosts a comprehensive list of companies in Sweden. The goal is to scrape the website and gather essential company information, including name, location, and organisation number. Additionally, the project aims to extract CEO and Project Manager (PM) emails from each company’s official website and output this data into a structured CSV file. The website client provides doesn't include the official url, so google search API implementation is needed.

Usually the official website will have a page like this:

![Example Website](/img/projects/sweden/example-website.png "Example Site To Scrape")

### Challanges

The task involves scraping multiple pages under each company's domain to extract email addresses. However, there is a significant challenge in filtering out irrelevant emails (e.g., those starting with info@, which are generic contact emails). It's difficult to definitively categorize emails as belonging to the CEO or Project Manager without context.

Besides, the target companies are often listed on local yellow page websites, which can lead to irrelevant results when searching for the official company website via Google search API. These yellow page websites, along with other platforms like Reddit, LinkedIn, and Instagram, can clutter the search results, making it hard to locate the correct official websites for scraping.

### Solutions

To ensure the Google search API returns the correct website, I maintain a list of known yellow page website domains, along with domains for other irrelevant platforms like Reddit and LinkedIn. The bot filters out these domains to ensure it only scrapes company websites. For URLs that are not filtered out, the bot performs fuzzy match to confirm they lead to the correct official company website.

Besides, to identify whether an email belongs to the CEO or a Project Manager, I scrape 500 characters surrounding each email address found on the company’s website. This context is then analyzed for keywords such as “CEO” and “Project Manager” (in Swedish, “VD” and “Projektledare”). If multiple keywords are found in the context, I will choose the nearest keyword and assign the appropriate role (CEO or Project Manager) to the email. Additionally, if there are no CEO and PM emails, then the script fallback to the logic scraping info email, making sure client has someone to contact.

After email extraction, I developed a custom email verification script. This script checks all email addresses through SMTP-level validation, removing any invalid addresses or those that return a 550 error response. This process eliminates any incorrect or non-working emails from the dataset, leaving only the valid contacts for CEOs and Project Managers.

### Outcomes & Impact

Out of the 2,133 companies, 83.2% successfully had either the CEO or PM emails extracted. The remaining companies either had inaccessible websites, lacked a company website entirely, or did not list any email addresses. With the correct contact information neatly organized in a CSV file, the client was able to perform outreach more effectively, improving their marketing and sales efforts.