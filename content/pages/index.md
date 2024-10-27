---
type: PageLayout
title: Home
colors: colors-a
backgroundImage:
  type: BackgroundImage
  url: /images/bg1.jpg
  backgroundSize: cover
  backgroundPosition: center
  backgroundRepeat: no-repeat
  opacity: 75
sections:
  - elementId: ''
    colors: colors-f
    backgroundSize: full
    title: Welcome to Marco's Netlify Technical Exercise
    subtitle: ''
    styles:
      self:
        height: auto
        width: wide
        margin:
          - mt-0
          - mb-0
          - ml-0
          - mr-0
        padding:
          - pt-36
          - pb-48
          - pl-4
          - pr-4
        alignItems: center
        justifyContent: center
        flexDirection: row-reverse
      title:
        textAlign: left
      subtitle:
        textAlign: left
      text:
        textAlign: left
      actions:
        justifyContent: flex-start
    type: HeroSection
    actions: []
  - type: TextSection
    colors: colors-d
    variant: variant-a
    title: Experiences through the technical assessment
    subtitle: ''
    text: >
      1.  Talk about how you made your site and why you chose the tools you did.
      Briefly explain one challenge you experienced in setting up this site and
      how you overcame it.

        Tools used:
        
        *   VS Code- Ubuntu Desktop 24.04
        *   Github and git
        
        About the site
        
        *   I made this site using the predefinied template auto-anotated-portfolio
        *   I used VS Code and Ubuntu as these required the least amount of setup and I am already familiar with these tools.

      2.  What did you think of our service during the time you used it? Provide
      some constructive criticism or some features that impressed you.

        *   The simplicity of deploying a site to the platform is a major plus.
        
        *   It was easier to deploy a new site than setting up a temporary github account with VS Code for this assignment
        
      3.  Rank your 5 favorite and 5 least favorite activities from this list:
      <https://gist.github.com/laurajodz/592402a6336410377dee1a744af846ab5>

        *   5 Favorites Activities:
          *   Work with the development team to help design a new feature based on feedback from customers  
          *   Submit bug reports and potentially bug fixes
          *   Join a Zoom call with a VIP customer you have been helping via email, upon their request
          *   Write and maintain Support Guides for our product
          *   Dig through server logs to troubleshoot a customer's website behavior
        
        *   5 Least Favorite Activities:
          *   Help manage communications during a service outage
          *   Respond to Netlify customers on Twitter
          *   Manage a Support team
          *   Create video tutorials to help teach users a specific feature or use case
          *   Respond to 20+ support requests via email every day

      4.  Provide a link to documentation for a technical/developer-focused
      product, which you think are well done, and explain why you think they are
      well done.
        Spotify's Developer API Documentation: <https://developer.spotify.com/documentation/web-api/tutorials/getting-started>

        Spotify has put in effort to anticipate common questions a developer may ask when first using their API. The documentation is clean and direct to the point answering those concerns. Additionally, additional documentation is linked in-line to clearly outline the linked article's context relates to the topic being discussed. The embedded HTTP request in the Reference section helps reduce confusion on how to perform requests to the endpoint currently being reviewed and the expected output of that request.

      5.  Explain, in a couple of paragraphs, what you think are two major
      challenges around DNS configuration for less-technical customers hosting
      websites.

        * Determining where to update DNS records
        * CNAME aliases

      6.  A customer writes in to Support saying simply that their “site won’t
      build”. You have access to their build logs, and there you see this error:
      Build failed due to a user error: Build script returned non-zero exit
      code: 2. You have no more information than this and the site’s source
      repository is private so you cannot test the build yourself. How would you
      troubleshoot this issue? What steps would you take? Also, please compose
      your best customer-facing first response.

        Troubleshooting method
        
        *   Update the customer that investigation into their issue has started and ask initial triage questions to get a better undestanding of the site's build issue timeline.
        *   Review the build logs. Start with the most recent error message and backtrack the logs to find the first instance of a relevant error for this issue.
        *   If the error is unknown to me, use internal and external resources to find relevant information regarding the build failure.
            *   3a. Search previous tickets for similar errors.
            *   3b. Search internal docs for relevant build errors.
            *   3c. If the error is not related to the internal build process, check Google for the error returned by the site's framework.
        *   Provide an update and suggest changes to the customer with the information I have found through my investigation.
        
        Response to the customer:
        
        ```
        Hello,
        Thank you for contacting Netlify. My name is Marco, and I will be reviewing your case today.
        
        I see the site is failing to deploy during the build and compile phase. Allow me some time to review the build logs further and help identify where the build is failing. In the meantime, could you provide us with some additional information regarding this issue?
        
        
        - Were you able to successfully deploy the site previously?
        - When was the last time the site was successfully deployed?
        - What changes (if any) were made to the site between the last successful deployment and now?
        
        I will update you shortly with the results of my investigation.
        
        Warm regards,
        Marco S.
        ```

      7.  How would you set up an http 301 status redirect from
      “/netlify/anything” on your site, to
      <https://www.google.com/search?q=anything>. Please provide the redirect
      formatting here. Now, how about a proxy redirect? Please add that proxy
      redirect rule directly to your site.
        For a basic 301 redirect, I would use the following configuration block in the netlify.toml file:
        
        ```
        [[redirects]]
          from = "https://marco-technical-assessment.netlify.app/some-page"
          to = "https://www.google.com/search?q=anything"
          status = 301
          force = true
        ```
        
        To perform a dynamic proxy redirect where we use the URL path as the search query, I would use the following confiugration block:  
        ```
        [[redirects]]
          from = "/search/*"
          to = "https://www.google.com/search?q=:splat"
          status = 200
          force = true
        ```

      8. Please attempt to deploy a function on our service. This need not be
      complicated. It could be "Hello World". Note that failure to deploy is not
      failing the exercise! Whether you have trouble or not, please describe
      what you experienced and how you attempted to troubleshoot any issues you
      encountered.


      9. We understand you don't know anything about our internal procedures at
      this stage, but we want you to explain at a high level how you'd react to
      this situation: You receive a report of a severe security issue on
      [www.netlify.com](http://www.netlify.com). You can't immediately confirm
      the report, so what steps might you take to investigate or substantiate
      the report? What might you say to the reporter, even though we haven't
      confirmed their assertion yet, that will instill confidence that our
      business is very concerned about security? You believe there is a
      reasonable chance the report is correct and the problem is very large and
      impactful. How might you escalate?
        Initial Process:
          1. Update the reporter and let them know we have received their report and are actively investigating and reproducting the security issue. Suggest they submit their report to the bug bounty program.
          2. Reach out to the Support team via internal comms and confirm if this is something they've seen/heard of before.
          3. Contact the security team via internal comms and CC <security@netlify.com> (if needed on support ticket)4. Create internal bug/security ticket for Sec/Eng teams to track the resolution of the secuity issue.

        ```
        Hello, 
        
        Thank you for reporting this security concern to Netlify. My name is Marco and I am a Support Engineer here at Netlify.

        (If the reporter provided reproduction steps)
        I have provided your report and reproduction steps to our Engineering and Security teams for further review.

        (If the reporter did not provide reproduction steps)
        To help our teams further investigate this issue, please provide with an outline of the steps used to identify and reproduce this issue.

        Additionally, if you haven't done so yet. I please submit your report to our Bug Bounty program for our Security team to review, validate, and confirm the severity of this issue.Reference: <https://www.netlify.com/security/https://hackerone.com/netlify?type=team>
        
        We will update you via this ticket as we receive additonal update from our Engineering and Security teams regarding the next steps to address this issue. In the meantime, don't hesistate to reach out if you have any questions or concerns!

        Warm regards,
        Marco S.
        ```
    elementId: ''
    styles:
      self:
        height: auto
        width: wide
        padding:
          - pt-28
          - pb-28
          - pl-4
          - pr-4
        justifyContent: center
      title:
        textAlign: left
      subtitle:
        textAlign: left
      text:
        textAlign: left
  - type: ContactSection
    colors: colors-f
    backgroundSize: full
    title: "Got an interesting project? Tell me more...\U0001F4AC"
    form:
      type: FormBlock
      elementId: sign-up-form
      fields:
        - name: firstName
          label: First Name
          hideLabel: true
          placeholder: First Name
          isRequired: true
          width: 1/2
          type: TextFormControl
        - name: lastName
          label: Last Name
          hideLabel: true
          placeholder: Last Name
          isRequired: false
          width: 1/2
          type: TextFormControl
        - name: email
          label: Email
          hideLabel: true
          placeholder: Email
          isRequired: true
          width: 1/2
          type: EmailFormControl
        - name: address
          label: Address
          hideLabel: true
          placeholder: Address
          isRequired: true
          width: 1/2
          type: TextFormControl
        - name: updatesConsent
          label: Sign me up to recieve updates
          isRequired: false
          width: full
          type: CheckboxFormControl
      submitLabel: "Submit \U0001F680"
      styles:
        submitLabel:
          textAlign: center
    styles:
      self:
        height: auto
        width: narrow
        margin:
          - mt-0
          - mb-0
          - ml-0
          - mr-0
        padding:
          - pt-24
          - pb-24
          - pr-4
          - pl-4
        alignItems: center
        justifyContent: center
        flexDirection: row
      title:
        textAlign: left
      text:
        textAlign: left
---
