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
    colors: colors-f
    variant: variant-a
    title: Experiences through the technical assessment
    subtitle: ''
    text: "### Talk about how you made your site and why you chose the tools you did. Briefly explain one challenge you experienced in setting up this site and how you overcame it.\n\nThis site was created using the auto-annotated-portfolio template from Netlify. Locally, my tools are; Ubuntu 24.04, VS Code, and Git. These are tools I am extremely familiar and comfortable with that required the least amount of setup.\n\nOne challenge I experienced while building and updating this site is that the markdown formatting did not transfer from VS Code to the Visual Editor correctly. To resolve this, I opened the editor with the Markdown toggle enabled and verified the markdown formatting is correct and adjusted accordingly.\n\n### What did you think of our service during the time you used it? Provide some constructive criticism or some features that impressed you.\n\nThe service has been very intuitive and easy to navigate. The visual editor and auto-deployment on new commits in different branches without additional user intervention is a welcomed feature.\n\n### Rank your 5 favorite and 5 least favorite activities from this list: <https://gist.github.com/laurajodz/592402a6336410377dee1a744af846ab5>\n\n##### 5 Favorites Activities:\n\n```\n*   Work with the development team to help design a new feature based on feedback from customers\n*   Submit bug reports and potentially bug fixes\n*   Join a Zoom call with a VIP customer you have been helping via email, upon their request\n*   Write and maintain Support Guides for our product\n*   Dig through server logs to troubleshoot a customer's website behavior\n```\n\n##### 5 Least Favorite Activities:\n\n```\n*   Help manage communications during a service outage\n*   Respond to Netlify customers on Twitter\n*   Manage a Support team\n*   Create video tutorials to help teach users a specific feature or use case\n*   Respond to 20+ support requests via email every day\n```\n\n### Provide a link to documentation for a technical/developer-focused product, which you think are well done, and explain why you think they are well done.\n\nSpotify's Developer API Documentation: <https://developer.spotify.com/documentation/web-api/tutorials/getting-started>\n\nSpotify has put in effort to anticipate common questions a developer may ask when first using their API. The documentation is clean and direct answering those concerns. Additionally, documentation is linked in-line to clearly outline the linked article relates to the context of the topic being discussed. The embedded HTTP request tester in the Reference section helps reduce confusion on how to perform requests to the endpoint currently being reviewed and the expected output of that request.\n\n### Explain, in a couple of paragraphs, what you think are two major challenges around DNS configuration for less-technical customers hosting websites.\n\nTwo major challenges I have experienced with DNS configurations are determining where to update the DNS records and how CNAME aliases affect the hostname's value. We would have to check with the Domain's registrar to determine the Name Servers where the zone file resides and direct the customer to that portal to perform their DNS changes. As for CNAME aliases, we would have to review the output of tools like nslookup or dig to determine what is taking precedence in the record's value.\n\n### A customer writes in to Support saying simply that their “site won’t build”. You have access to their build logs, and there you see this error: Build failed due to a user error: Build script returned non-zero exit code: 2. You have no more information than this and the site’s source repository is private so you cannot test the build yourself. How would you troubleshoot this issue? What steps would you take? Also, please compose your best customer-facing first response.\n\nTroubleshooting method\n\n*   Update the customer that investigation into their issue has started and ask initial triage questions to get a better understanding of the site's build issue timeline.\n*   Review the build logs. Start with the most recent error message and backtrack the logs to find the first instance of a relevant error for this issue.\n*   If the error is unknown to me, use internal and external resources to find relevant information regarding the build failure.\n    *   3a. Search previous tickets for similar errors.\n    *   3b. Search internal docs for relevant build errors.\n    *   3c. If the error is not related to the internal build process, check Google for the error returned by the site's framework.\n*   Provide an update and suggest changes to the customer with the information I have found through my investigation.\n\nResponse to the customer:\n\n```\nHello,\nThank you for contacting Netlify. My name is Marco, and I will be reviewing your case today.\n\nI see the site is failing to deploy during the build and compile phase. Allow me some time to review the build logs further and help identify where the build is failing. In the meantime, could you provide us with some additional information regarding this issue?\n\n\n- Were you able to successfully deploy the site previously?\n- When was the last time the site was successfully deployed?\n- What changes (if any) were made to the site between the last successful deployment and now?\n\nI will update you shortly with the results of my investigation.\n\nWarm regards,\nMarco S.\n\n```\n\n### How would you set up an http 301 status redirect from “/netlify/anything” on your site, to <https://www.google.com/search?q=anything>. Please provide the redirect formatting here. Now, how about a proxy redirect? Please add that proxy redirect rule directly to your site.\n\nFor a basic 301 redirect, I would use the following configuration block in the netlify.toml file:\n\n```\n[[redirects]]\n  from = \"https://marco-technical-assessment.netlify.app/some-page\"\n  to = \"https://www.google.com/search?q=anything\"\n  status = 301\n  force = true\n```\n\nTo perform a dynamic proxy redirect where we use the URL path as the search query, I would use the following confiugration block:\n\n```\n[[redirects]]\n  from = \"/search/*\"\n  to = \"https://www.google.com/search?q=:splat\"\n  status = 200\n  force = true\n```\n\n### Please attempt to deploy a function on our service. This need not be complicated. It could be \"Hello World\". Note that failure to deploy is not failing the exercise! Whether you have trouble or not, please describe what you experienced and how you attempted to troubleshoot any issues you encountered.\n\nCreating a new function on my Netlify site was pretty straightforward thanks to the documentation. Unfortunately, I had combined the TS and Lambda functions together and created an invalid response type.\n\nInvalid function:\n```\nexport default async (req: Request, context: Context) => {\n    return {\n        statusCode: 200,\n        body: JSON.stringify({ message: \"Hello World\" }),\n    };\n};\n```\n\nThis resulted in the following error when executing the function via: https://marco-technical-assessment.netlify.app/.netlify/functions/hello\n```\nerror decoding lambda response: error decoding lambda response: unexpected end of JSON input\n```\n\nI access the function's logs from the Netlify portal for additional insight into the reason the function returned an invalid JSON object. The log entry I found was:\n\n```\nOct 27, 02:37:46 PM: ae85b89a ERROR  Invoke Error \t{\"errorType\":\"NetlifyUserError\",\"errorMessage\":\"Function returned an unsupported value. Accepted types are 'Response' or 'undefined'\",\"name\":\"NetlifyUserError\",\"stack\":[\"NetlifyUserError: Function returned an unsupported value. Accepted types are 'Response' or 'undefined'\",\"    at tr (file:///var/task/___netlify-bootstrap.mjs:2:29119)\",\"    at Runtime.handler (file:///var/task/___netlify-bootstrap.mjs:2:28339)\",\"    at async Runtime.handleOnceStreaming (file:///var/runtime/index.mjs:1206:26)\"]}\n```\n\nReviewing the documentation again, I found the source of my error and corrected the function's return object in the next commit. The updated function is:\n\n```\nexport default async (req: Request, context: Context) => {\n    return new Response(\"Hello, World!\")\n};\n```\n\n### We understand you don't know anything about our internal procedures at this stage, but we want you to explain at a high level how you'd react to this situation: You receive a report of a severe security issue on [www.netlify.com](http://www.netlify.com). You can't immediately confirm the report, so what steps might you take to investigate or substantiate the report? What might you say to the reporter, even though we haven't confirmed their assertion yet, that will instill confidence that our business is very concerned about security? You believe there is a reasonable chance the report is correct and the problem is very large and impactful. How might you escalate?\n\n#### Initial Process:\n\n```\n1. Update the reporter and let them know we have received their report and are actively investigating and reproducing the security issue. Suggest they submit their report to the bug bounty program.\n2. Reach out to the Support team via internal comms and confirm if this is something they've seen/heard of before.\n3. Contact the security team via internal comms and CC <security@netlify.com> (if needed on support ticket)\n4. Create internal bug/security ticket for Sec/Eng teams to track the resolution of the security issue.\n```\n\n```\nHello, \n\nThank you for reporting this security concern to Netlify. My name is Marco and I am a Support Engineer here at Netlify.\n\n(If the reporter provided reproduction steps)\nI have provided your report and reproduction steps to our Engineering and Security teams for further review.\n\n(If the reporter did not provide reproduction steps)\nTo help our teams further investigate this issue, please provide with an outline of the steps used to identify and reproduce this issue.\n\nAdditionally, if you haven't done so yet. I please submit your report to our Bug Bounty program (linked below) for our Security team to review, validate, and confirm the severity of this issue.\nReference: https://www.netlify.com/security/\nhttps://hackerone.com/netlify?type=team\n\nWe will update you via this ticket as we receive additonal update from our Engineering and Security teams regarding the next steps to address this issue. In the meantime, don't hesistate to reach out if you have any questions or concerns!\n\nWarm regards,\nMarco S.\n```\n"
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
