# Evaluating accessibility tools
**Context**: 

The goal of this assignment is to create a common toolkit for evaluating usability and accessibility of interfaces. In digital interfaces, consideration for sensory limitations is particularly important. 

**Initial Post**: 

[You have been assigned a tool](https://airtable.com/shrzqSjHWgAuZpzR1) that falls into one of 3 categories:

-   **Simulator** - helps understand how a person with disability experiences the world
-   **Assistive technology** - used by people with disabilities to access information (e.g. a screen reader)
-   **Accessibility Checker/Validator** - can be used to identify accessibility problems that users with disability experience.

Choose an established website, and use the tool to evaluate your chosen UI:

-   How did your chosen website perform? What kinds of problems did you identify?
-   What did you learn about improving accessibility from using the tool?
-   Did your mental model of how people with disabilities access information and the challenges they face change as a result of this experience?
-   Are you going to add this tool to your UX design toolkit going forward? Why or why not?
-   Include screenshots to help everyone understand how your tool works. 

Note: you may have to do some additional research to do a meaningful analysis - these are expert tools with some learning curve to utilize effectively.

**Replies**: In your replies, test 2 tools (from the categories you were NOT assigned) analyzed by your classmates  on _**your**_ chosen UI, and compare your experience to those of the original poster.    

**Criteria**: Students will produce one initial post (approx. 300 words) and post two replies (approx. 200 words). Students should draw from the learning materials through this week and ensure vocabulary and key terms are used where appropriate.

**Using chunking in your discussion posts**

Because chunking improves usability, going forward, I would like you to use chunking in your discussion posts, by using:

-   Subheadings
-   Bullet points, and 
-   Relatively short sentences

## Draft
My assigned tool was [accessibilitychecker.org](https://www.accessibilitychecker.org/). I was initially excited because I haven't seen this tool before, and it has some "in plain words" explanations of what each problem is and how to fix it. In Figure 1, the design of the interface uses plentiful white space to focus on the main action, which is to check a website URL for accessibility issues.

**Figure 1**
*Accessibilitychecker.org homepage*
![[Screen Shot 2022-02-05 at 11.13.47 AM.png]]
The accessibilitychecker.org homepage features minimal elements and plentiful whitespace, which draws the eye to the Check website feature (accessibilitychecker.org, 2020).

The report it generates is shown in Figure 2, and a few positives of this interface include the appropriate use of color to communicate urgency, the use of sans-serif fonts and appropriate space to group elements visually, and a clear summary of results. Ultimately, despite the good design, I do not recommend this tool for other reasons listed below.

**Figure 2**
*Accessibilitychecker.org report, National Grid Massachusetts website*
![[Screen Shot 2022-02-05 at 11.13.03 AM.png]]
An accessibility audit report prioritizes issues into urgent and secondary issues. The overall status of the report is easily identified with a red x signifier (accessibilitychecker.org, 2020).

**How did your chosen website perform? What kinds of problems did you identify?**

The report identified a major color contrast issue, which I was surprised by, and a number of "secondary" issues with aria labels and roles. The secondary issues with aria labels didn't have code or line numbers associated with them, so I couldn't understand where in the code the problem was and double check it. The contrast issue turned out to be a false positive, as confirmed in Firefox Dev Tools in Figure 3. I can't tell from this tool alone if the secondary issues are valid or not, but I should be able to do that using a screen reader and keyboard testing in my other forum posts. I'll link to those in a reply to this post.

**Figure 3**
*Annotated screenshot, Firefox Web Developer Tools on National Grid Massachusetts website*
![[Screen Shot 2022-02-05 at 11.35.31 AM.png]]
This screenshot verifies the contrast issue was a false positive due to the use of transparency in rgba color values. Both accessibilitychecker.org and Firefox Dev Tools initially labeled this element as having a contrast problem. When I changed the transparent rgba value to the equivalent non-transparent hex value in dev tools, the contrast value changed and the button's contrast was labeled AAA compliant. The element on screen and its final contrast value are circled in red (Mozilla et al., 2022).

**What did you learn about improving accessibility from using the tool?**
I learned there are different accessibility requirements for different countries, and that using transparency in rgba color values in CSS can lead to false positives in accessibility validators. This makes sense, because the validator is reading the code's value, which is transparent, in isolation. It isn't aware of the colors below the element.

**Did your mental model of how people with disabilities access information and the challenges they face change as a result of this experience?**
No. I use validation tools frequently since my university requires WCAG 2.0 AA compliance, and National Grid didn't have any advertising content. That said, Jacob's evaluation of Google Lighthouse, which is also a validation tool, totally changed my mental model of how advertising and normal content work together for a screen reader. I posted about that in [my reply to Jacob's evaluation of Google Lighthouse](https://moodle2.brandeis.edu/mod/forum/discuss.php?d=504407#p1393354).

**Are you going to add this tool to your UX design toolkit going forward? Why or why not?**
In short: no.

The main benefit of this tool is that it provides a way to paste in a URL and quickly check it for accessibility issues, and provides user-friendly explanations of each item that needs to be addressed. The way I would use this type of tool is to give it to someone without development experience to help guide them in improving their website. This isn't the right tool for me for my work, because by nature it is limited to web pages which are public facing. For example, in my National Grid audit, I couldn't validate anything behind a login page, such as My Account. It also didn't give me a code snippet or line numbers to help me identify where ARIA roles didn't match the validator's expectations.

I won't be using this as a resource to give to people I work with without development experience for a few reasons.

- There is an interstitial, shown in Figure 4, which uses the dark pattern of confirmshaming to induce a sense of fear that the website won't be "fixed" and attempts to sell a service (Brignull, 2022). This doesn't help me because I *am* part of the service that fixes this in my organization. 

**Figure 4**
*Interstitial, accessibilitychecker.org*
![[Screen Shot 2022-02-04 at 10.14.07 PM.png]]
An interstitial appears every time a user clicks "back to home". This makes in inconvinient to check multiple URLs in this tool. Additionally, a green color is used to drive users to purchase a service through an affiliate link, and the red color discourages checking another URL (accessibilitychecker.org, 2020).

- The typography is pretty, but I can't tell which set of accessibility guidelines the report checks against. For example, WCAG 2.1 standards have 3 levels: A, AA, and AAA (W3C Web Accessibility Initiative (WAI), 2020). Because I work at a university, we require AA compliance. I can't trust or recommend any tool which doesn't clearly label the level of accessibility compliance, and the lack of that information makes me question the expertise these results are built on.
- This website itself isn't very usable. As shown in Figure 5, the report is in a tiny area that takes up the bottom third of the screen, and you must have your mouse inside the area to scroll to read the report.

**Figure 5**
*Annotated screenshot of report demonstrating usability issues, accessibilitychecker.org*
![[Screen Shot 2022-02-04 at 10.37.13 PM.png]]
Limiting scroll area to the bottom half of the page makes readability of the long report difficult (accessibilitychecker.org & Kolodziej, 2022).
- Some errors, such as "[id] attributes on active, focusable elements are not unique" are incorrectly classified as "secondary" errors. This particular error also didn't come with a plain words explanation. The reason why this is a problem is because in valid HTML, the ID attribute value is required to be unique, and as a result some screen readers will skip all but the first element that uses the same ID in a page (Google Developers, 2019). That means there is content on the page a screen reader will not announce, which is not a secondary issue when it comes to accessibility. In fact, valid HTML markup is one of the minimum requirements for A level compliance in WCAG 2.0 (Caldwell et al., 2008).
- By repeating the same "Use automated solutions" option text on every error throughout the report, this website implies that an AI-based accessibility script can solve all the problems this report finds. However, JavaScript can't change the base markup on an HTML file on a server, so this tool would not be able to fix things like HTML validation problems. JavaScript can also be disabled in browsers, so it is a best practice to ensure basic functions of a website work without JavaScript where possible (MDN Contributors, 2022). I'd argue that basic markup falls into this category.

After reviewing other similar tools, I think https://web.dev/measure/ provides the best blend of clearly explaining how to improve the page in non-technical terms while making it clear what needs manual review. The design of the tool is clean and uncluttered, and does not have the dark patterns shown in this tool.

## Final
#### Summary  

My assigned tool was [accessibilitychecker.org](https://www.accessibilitychecker.org/). I was initially excited because I haven't seen this tool before, and it has some "in plain words" explanations of what each problem is and how to fix it. In Figure 1, the design of the interface uses plentiful white space to focus on the main action, which is to check a website URL for accessibility issues. I chose to evaluate the [National Grid Massachusetts website](https://www.nationalgridus.com/MA-Home/Default.aspx) since National Grid provides gas and electric service, which are basic utilities everyone needs to be able to access.  

  

---

**Figure 1**  
_Accessibilitychecker.org homepage_  
![accessibility checker homepage](https://moodle2.brandeis.edu/pluginfile.php/2675713/mod_forum/post/1393440/Screen%20Shot%202022-02-05%20at%2011.13.47%20AM.png)  
The accessibilitychecker.org homepage features minimal elements and plentiful whitespace, which draws the eye to the Check website feature (accessibilitychecker.org, 2020).

---

  

The report it generates is shown in Figure 2, and a few positives of this interface include the appropriate use of color to communicate urgency, the use of sans-serif fonts and appropriate space to group elements visually, and a clear summary of results. Ultimately, despite the good design, I do not recommend this tool for other reasons listed below.

  

---

**Figure 2**  
_Accessibilitychecker.org report, National Grid Massachusetts website_  
![accessibility checker report](https://moodle2.brandeis.edu/pluginfile.php/2675713/mod_forum/post/1393440/Screen%20Shot%202022-02-05%20at%2011.13.03%20AM.png)  
An accessibility audit report prioritizes issues into urgent and secondary issues. The overall status of the report is easily identified with a red x signifier (accessibilitychecker.org, 2020).

---

  

#### **How did your chosen website perform? What kinds of problems did you identify?**

The report identified a major color contrast issue, which I was surprised by, and a number of "secondary" issues with aria labels and roles. The secondary issues with aria labels didn't have code or line numbers associated with them, so I couldn't understand where in the code the problem was and double check it. The contrast issue turned out to be a false positive, as confirmed in Firefox Dev Tools in Figure 3. I can't tell from accessibilitychecker.org alone if the secondary issues are valid or not, but I should be able to do that using a screen reader and keyboard testing in my other forum posts.

---

**Figure 3**  
_Annotated screenshot, Firefox Web Developer Tools on National Grid Massachusetts website_  
![firefox dev tools](https://moodle2.brandeis.edu/pluginfile.php/2675713/mod_forum/post/1393440/Screen%20Shot%202022-02-05%20at%2011.35.31%20AM.png)  
This screenshot verifies the contrast issue was a false positive due to the use of transparency in rgba color values. Both accessibilitychecker.org and Firefox Dev Tools initially labeled this element as having a contrast problem. When I changed the transparent rgba value to the equivalent non-transparent hex value in dev tools, the contrast value changed and the button's contrast was labeled AAA compliant. The element on screen and its final contrast value are circled in red (Mozilla et al., 2022).

---

####   

#### **What did you learn about improving accessibility from using the tool?**

I learned there are different accessibility requirements for different countries, and that using transparency in rgba color values in CSS can lead to false positives in accessibility validators. This makes sense, because the validator is reading the code's value, which is transparent, in isolation. It isn't aware of the colors below the element.

####   

#### **Did your mental model of how people with disabilities access information and the challenges they face change as a result of this experience?**

No. I use validation tools frequently since my university requires WCAG 2.0 AA compliance, and National Grid didn't have any advertising content. That said, Jacob's evaluation of Google Lighthouse, which is also a validation tool, totally changed my mental model of how advertising and normal content work together for a screen reader. I posted about that in [my reply to Jacob's evaluation of Google Lighthouse](https://moodle2.brandeis.edu/mod/forum/discuss.php?d=504407#p1393354).

####   

#### **Are you going to add this tool to your UX design toolkit going forward? Why or why not?**

In short: no.

  

The main benefit of this tool is that it provides a way to paste in a URL and quickly check it for accessibility issues, and provides plain language explanations of each item that needs to be addressed. The way I would use this type of tool is to give it to someone without development experience to help guide them in improving their website. This isn't the right tool for me for my work, because by nature it is limited to web pages which are public facing. For example, in my National Grid audit, I couldn't validate anything behind a login page, such as My Account. It also didn't give me a code snippet or line numbers to help me identify where ARIA roles didn't match the validator's expectations.

  

I also won't be using this as a resource to give to people I work with without development experience for a few reasons. 

  

-   There is an interstitial, shown in Figure 4, which uses the dark pattern of confirmshaming to induce a sense of fear that the website won't be "fixed" and attempts to sell a service (Brignull, 2022). This doesn't help me because I _am_ part of the service that fixes this in my organization.

---

**Figure 4**  
_Interstitial, accessibilitychecker.org_  
![interstitial](https://moodle2.brandeis.edu/pluginfile.php/2675713/mod_forum/post/1393440/Screen%20Shot%202022-02-04%20at%2010.14.07%20PM.png)  
An interstitial appears every time a user clicks "back to home". This makes in inconvinient to check multiple URLs in this tool. Additionally, a green color is used to drive users to purchase a service through an affiliate link, and the red color discourages checking another URL (accessibilitychecker.org, 2020).

---

-   The typography is pretty, but I can't tell which set of accessibility guidelines the report checks against. For example, WCAG 2.1 standards have 3 levels: A, AA, and AAA (W3C Web Accessibility Initiative (WAI), 2020). Because I work at a university, we require AA compliance. I can't trust or recommend any tool which doesn't clearly label the level of accessibility compliance, and the lack of that information makes me question the expertise these results are built on.
-   This website itself isn't very usable. As shown in Figure 5, the report is in a tiny area that takes up the bottom third of the screen, and you must have your mouse inside the area to scroll to read the report.

---

**Figure 5**  
_Annotated screenshot of report demonstrating usability issues, accessibilitychecker.org_  
![Annotated report](https://moodle2.brandeis.edu/pluginfile.php/2675713/mod_forum/post/1393440/Screen%20Shot%202022-02-04%20at%2010.37.13%20PM.png)  
Limiting scroll area to the bottom half of the page makes readability of the long report difficult (accessibilitychecker.org & Kolodziej, 2022).

---

-   Some errors, such as "[id] attributes on active, focusable elements are not unique" are incorrectly classified as "secondary" errors. This particular error also didn't come with a plain words explanation. The reason why this is a problem is because in valid HTML, the ID attribute value is required to be unique, and as a result some screen readers will skip all but the first element that uses the same ID in a page (Google Developers, 2019). That means there is content on the page a screen reader will not announce, which is not a secondary issue when it comes to accessibility. In fact, valid HTML markup is one of the minimum requirements for A level compliance in WCAG 2.0 (Caldwell et al., 2008).
-   By repeating the same "Use automated solutions" option text on every error throughout the report, this website implies that an AI-based accessibility script can solve all the problems this report finds. However, JavaScript can't change the base markup on an HTML file on a server, so this tool would not be able to fix things like HTML validation problems. JavaScript can also be disabled in browsers, so it is a best practice to ensure basic functions of a website work without JavaScript where possible (MDN Contributors, 2022). I'd argue that basic markup falls into this category.

After reviewing other similar tools, I think [https://web.dev/measure/](https://web.dev/measure/) provides the best blend of clearly explaining how to improve the page in non-technical terms while making it clear what needs manual review. The design of the tool is clean and uncluttered, and does not have the dark patterns shown in this tool.

####   

#### References

accessibilitychecker.org. (2020). _Free Online Web Accessibility Checker (WCAG & ADA)_. [https://www.accessibilitychecker.org/](https://www.accessibilitychecker.org/)

  

accessibilitychecker.org, & Kolodziej, A. (2022). _Annotated screenshot of report_. [https://www.accessibilitychecker.org/](https://www.accessibilitychecker.org/)

  

Brignull, H. (2022, January 31). _Confirmshaming_. Dark Patterns. [https://www.darkpatterns.org/types-of-dark-pattern/confirmshaming](https://www.darkpatterns.org/types-of-dark-pattern/confirmshaming)

  

Caldwell, B., Cooper, M., Guarino Reid, L., Vanderheiden, G., Chisholm, W., Slatin, J., & White, J. (2008, December 11). _Web Content Accessibility Guidelines (WCAG) 2.0_. [https://www.w3.org/TR/2008/REC-WCAG20-20081211/#ensure-compat-parses](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#ensure-compat-parses)

  

Google Developers. (2019, October 17). _[id] attributes on active, focusable elements are not unique_. Web.Dev. [https://web.dev/duplicate-id-active/](https://web.dev/duplicate-id-active/)

  

MDN Contributors. (2022, January 31). _CSS and JavaScript accessibility best practices - Learn web development | MDN_. [https://developer.mozilla.org/en-US/docs/Learn/Accessibility/CSS_and_JavaScript](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/CSS_and_JavaScript)

  

Mozilla, National Grid Massachusetts, & Kolodziej, A. (2022). _Annotated screenshot of Firefox Web Developer Tools on the National Grid Massachusetts website_ [Screenshot].

  

W3C Web Accessibility Initiative (WAI). (2020, July 13). _Web Content Accessibility Guidelines (WCAG) 2 Level A Conformance_. Web Accessibility Initiative (WAI). [https://www.w3.org/WAI/WCAG2A-Conformance](https://www.w3.org/WAI/WCAG2A-Conformance)