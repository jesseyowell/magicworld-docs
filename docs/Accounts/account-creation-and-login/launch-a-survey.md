---
title: launch-a-survey
excerpt: brief description of page contents that show up on previews
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
# Create & Launch a Microsurvey

Congratulations on making it this far! You are now ready to launch your very first microsurvey in UserLeap. Microsurvey creation starts from the [**Templates Page**](https://www.app.userleap.com/collections)**.**

## **Microsurvey Design Workflow**

Designing a microsurvey involves 4 quick steps:

1. Pick a template \(or create from scratch\)
2. Add/edit questions & skip logic 
3. Select an audience to target
4. Review and launch

### **Pick a Template**

The UserLeap template gallery contains 75+ templates for you to use, all made by our Head of User Research - Allison Dickin. 

Here are some of the areas that we cover: 

1. Finding Product/Market Fit
2. Customer Journey
3. Customer Acquisition
4. Feature Development
5. Onboarding Success

You also have the option to create new from scratch

![](https://p35.tr2.n0.cdn.getcloudapp.com/items/Jru4noRp/b1c9e563-853b-4b18-8bd1-69dd5cd22808.gif?v=4595aee1043082199d8eb5327bf95290)

### **Questions**

![](https://p35.tr2.n0.cdn.getcloudapp.com/items/6qu8vG2R/da1f0e95-3a16-496b-ae43-ce9d193212f0.jpg?v=a680dc9f6305ac5cb25627d262d73d44)

**Rename your Microsurvey** \(1\)**:** Click on the title bar to edit your microsurvey title

**Pick a Question Type** \(2\): 

UserLeap has a total of 5 question types: 

1. Open-ended text
2. Multiple choice single answer
3. Multiple choice multi answer
4. 1-5 rating scale
5. NPS

**Question Settings** \(3\)**:** Supports additional functionality, such as adding a duplicate question below, inserting a new question below, deleting the question, and moving the current question either up or down

**Survey Logic** \(4\)**:** All question types support survey skip logic. This is an easy way to segment questions based on audience responses. For example, if you ask “how easy to use is feature xyz,” you can show a different Q2 based on whether or not they had a positive experience \(answered 4 or 5, as compared to 1,2,3\). 

*Here's more information on* [***UserLeap skip logic***](../product-workflows/adding-and-removing-skip-logic.md)*\*\*\*\**

**Save Changes** \(5\): Please remember to save changes

### **Audience**

![](https://p35.tr2.n0.cdn.getcloudapp.com/items/eDujgnl5/02f90b98-b7cd-4410-b411-40c2a711fc52.jpg?v=fdea0fa34313d3ac62b1d364087c016a)

**Choose a Platform** \(1\):  A microsurvey is limited to a single platform; you have the option to pick from Web \(including mobile web browsers\), Mobile, Email \(available on Enterprise and Essentials\), or Shareable Link

*Here's how you* [***launch an email microsurvey***](../product-workflows/creating-an-email-survey.md)*\*\*\*\**

**Microsurvey Trigger** \(2\): Audience targeting requires that you add at least one event to UserLeap \(click \***\*\[**&#x68;ere\*\*]\(./)\). If you've already added an event, please select the event from the dropdown 

**Microsurvey Filters** \(3\): Like a trigger, a filter is used to further target audiences you have defined on the UserLeap platform. 

**UserLeap Terminology**:

**Events**: An event is an action that takes place in your web or mobile application. Events are used as both a trigger and a filter for a microsurvey.

Examples of events include: 

1. Visited a page \(i.e., visited the dashboard page\)
2. Clicked a button
3. Page scrolls

Your events can be found [**here**](http://app.userleap.com/events)\*\*\*\*

*Refresh your knowledge of events* [***here***](../product-definitions/events.md)*\*\*\*\**

**Trigger:** The event that must take place for a user to qualify for a microsurvey. Each microsurvey MUST have a trigger. Triggers are also known as [**events**](../product-definitions/events.md#what-is-a-userleap-event). 

* Advanced: if you click the “Advanced” dropdown, you can add a time delay to your microsurvey. UserLeap suggests adding a 3-5 second trigger delay. This means that UserLeap will wait the designated number of seconds before displaying a survey once the event takes place.

**Filter**: Filters are useful when you want to segment the audience that should qualify for a microsurvey. We’ll sometimes reference these as “survey filters.” Multiple microsurvey filters are treated as ANDs and not ORs.

* Advanced: in the “Advanced” dropdown for filters, you have the option to add minimum page views & session parameters. 
* Sessions in UserLeap are measured as 12-hour windows in which the user is active.
* Page views are only applicable to web microsurveys \(will not be displayed for email, mobile, link-based microsurveys\)

\_\_[***Here's a quick guide*** ](../product-workflows/interacting-with-survey-filters.md)*on how to use microsurvey filters* 

*Learn more about UserLeap attributes* [***here***](../product-definitions/attributes.md)*\*\*\*\**

**Total Responses**: In web and mobile microsurveys, you can choose to either deliver until a certain statistical confidence threshold has been met \(set number of responses\) or you can choose to deliver continuously \(no limit on responses\). With email surveys, you also have the option to deliver immediately to eligible recipients.

If choosing to run until a confidence threshold has been met, you can choose from one of several recommended trade-offs between statistical confidence and speed of obtaining results. Generally, requiring less confidence means you will get results faster. 

*You can also choose your own set number of responses using the* [***Custom option***](../product-workflows/custom-audience-sampling.md)*.*

**Resurvey Window**: To avoid sending the same user multiple microsurveys \(different surveys\), UserLeap designed a resurvey window that can be set in two places. 

The global resurvey window is under your [**settings page**](http://app.userleap.com/settings)\*\*\*\*

*Read more about* [***UserLeap resurvey windows***](../product-definitions/re-survey-windows.md)*\*\*\*\**

This is the number of days an individual MUST wait before qualifying to receive another microsurvey from UserLeap. 

![](https://p35.tr2.n0.cdn.getcloudapp.com/items/yAuD0Apq/1d8668e4-189d-4106-93fe-afe02e5e8df3.gif?v=53280c079e02613c686997389252cfdc)

Changing this number will allow this specific microsurvey \(and not any other microsurvey\) to appear outside of the global window. Please note that this WILL NOT change your [**global re-survey window**](../product-definitions/re-survey-windows.md#global-window). 

* It is recommended that you keep the “only show this survey once per user”. However, there are cases where you consider allowing users to retake a microsurvey - once such example is in a continuous microsurvey where you are trying to track historical trends of the same user\(s\)

### **Save and Launch your UserLeap Microsurvey**

![](https://p35.tr2.n0.cdn.getcloudapp.com/items/Jru4npLG/30ff6a66-9b62-49fc-83b8-6f8f57a1bf0c.gif?v=b7a8943e953fa2ce34820a2dbb27b1c2)

\{% hint style="info" %}\
If you have any questions please email us at **[success@userleap.com](mailto:success@userleap.com)** or use the in-product help chat\
\{% endhint %}
