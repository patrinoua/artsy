Mentor:

Manager:

## Your first day

_Goal: I've met my manager, mentor, and some members of the engineering team
(over lunch!). I've logged into slack, google (artsymail), Jira, 1Password, and
know how to use the coffee machine._

- [ ] ✅ Add a cool pic of yourself to Slack and Jira.
- [ ] ✅ Update your Slack profile with new personal information such as Github and your AWS username (which your manager should have given you).
- [ ] ✅ Say hi in [#dev](https://artsy.slack.com/messages/dev) with a :wave:.

🎉😊🥳🍾🎉😊🥳🍾🎉😊🥳🍾🎉😊🥳🍾🎉😊🥳🍾

😊🥳🍾🎉😊🥳🍾🎉😊🥳🍾🎉😊🥳🍾🎉😊🥳🍾🎉

🥳🍾🎉😊🥳🍾🎉😊🥳🍾🎉😊🥳🍾🎉😊🥳🍾🎉😊


## Your first week

_Goal: I have my local development environment set up and have access to crucial
engineering resources like kubernetes, sentry, Datadog, and Papertrail. I've
made a change to a repo in Artsy's org and have deployed that change to
production. I have a sense for what the product teams are and I know my way
around the Artsy site._

### First week checklist

**Keep your eye out for ways to improve our documentation -- including in this
repo!** A code change is great, but improving documentation (in _whatever_
little way) with your fresh set of eyes helps us help the next person
onboarding. We emphatically do not underestimate it; this is _real_ work!

Also please keep a list of things that surprise you about Artsy! After your
first week be sure to discuss anything that comes up here with your manager. We
want to hear the WTFs that you encounter during your onboarding! See [this
fabulous talk](https://www.youtube.com/watch?v=8bxZuzDKoI0) if you're curious
about the motivation for this nudge.

The more you get through this checklist the better, but there is a lot here so
don't worry if you didn't finish all in one week. While you're onboarding,
you're learning. When you ask a colleague for help learning something, you are
doing your job, so don't be shy! As long as you're learning, you are
contributing to the team.

As a recommendation, before starting, scan through the entire checklist and plan
your week. For example, coordinating meetings with product team members can take
some time, so it's better to trigger those conversations sooner. Also, there is
a lot of written documentation to go through, so it can be better to start
reading it early while setting up your local environment.

#### Through the general Artsy onboarding:

- [ ] You have access to 1Password for any shared credentials (check your email for an invite), Gmail, [Bamboo](https://artsy.bamboohr.com/), [Slack](https://artsy.slack.com)
- [ ] You understand the Artsy organization at a high level
- [ ] You've learned [Artsy's values](https://www.notion.so/artsy/Artsy-Values-Behaviors-42a6905b3b4c44e097f860d3e847cc16)
- [ ] You've read the [most recent board memo](https://www.notion.so/artsy/Artsy-Strategy-OKRs-Homepage-0bdefa3cf1d243b28d047bf1353695b4#abfea49090524a7da6288584d5254390) detailing current plans and challenges
- [ ] Your calendar includes org-wide events (such as weekly all-hands and monthly demo days) and engineering-wide events (such as weekly stand-ups and incident-review).

#### Developer set-up:

_Remember to review *all* setup scripts before executing them :)_

- [ ] 📧 Check your email for 1password invite.
- [ ] ✅ [Enable two-factor authentication on your GitHub account](https://help.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/). _You'll need this enabled to join the Artsy GitHub org. You can use [1Password as an authenticator](https://support.1password.com/one-time-passwords/) for 2fa. You may also need to generate a [personal token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token#using-a-[…]and-line) to use GitHub from the command line. Note: Do not set up Git SSH instead of the personal token, since many scripts at Artsy don't use it._
- [ ] 👤 Update your GitHub account with your real name; that way teammates will be able to easily find and tag you in PRs and other communications.
- [ ] 👤 Update your [local git installation](https://docs.github.com/en/github/setting-up-and-managing-your-github-user-account/managing-email-preferences/setting-your-commit-email-address#setting-your-commit-email-address-in-git) with the same email address you use to login to GitHub.
- [ ] ✅ Set up MFA for your AWS account in your [account settings](https://console.aws.amazon.com/iam/home?region=us-east-1#/security_credentials). You can use 1Password to store unique passwords and it can also serve as a 2FA device.
- [ ] 💻 Download your favorite text editor and terminal application. A lot of us use VSCode and it will be installed for you as part of the initial developer setup script in the next step, along with the [Artsy VSCode extension](https://marketplace.visualstudio.com/items?itemName=Artsy.artsy-studio-extension-pack)
- [ ] 💻 Follow Artsy Engineering's [initial developer setup](https://github.com/artsy/potential/blob/main/scripts/setup)
      which provides a base for many artsy projects. Confirm how you want to configure it (ask questions if you're
      unsure about the options), and run it on your computer.
- [ ] 💻👯 If you haven't had your AWS IAM user set up or Artsy Github access, ping your manager.
- [ ] 💻👯 Work with your mentor to get set up with [Artsy's VPN](https://github.com/artsy/infrastructure/blob/master/README.md#vpn).
- [ ] 💻 Follow [these instructions](https://github.com/artsy/README/blob/main/playbooks/hokusai.md#setup) to get set up with hokusai, our internal CLI for managing applications deployed to our Kubernetes cluster. Verify your Hokusai setup by finding an artwork in Gravity's database:
  - Clone [Gravity](https://github.com/artsy/gravity)
  - In Gravity's folder try `hokusai staging run "rails c" --tty`
  - Once console is open try `Artwork.find('andy-warhol-skull')`
- [ ] 🔓Make sure you can access the following tools. Reach out to your mentor or manager if you need help getting access:
  - [Datadog](https://www.artsy.net/datadog) - Use your G Suite login
  - [Papertrail](https://papertrailapp.com/) - Use the shared account in 1Password
  - [Opsgenie](https://artsy.app.opsgenie.com/) - Use your G Suite login
  - [Sentry](https://sentry.io/organizations/artsynet) - Use your G Suite login

#### Product & teams:

- [ ] 🔍 Poke around the active sprints in [JIRA](https://artsyproduct.atlassian.net/secure/BrowseProjects.jspa)
  - [ ] [Collector Experience](https://artsyproduct.atlassian.net/secure/RapidBoard.jspa?rapidView=77&projectKey=CX)
  - [ ] [Find & Explore](https://artsyproduct.atlassian.net/secure/RapidBoard.jspa?rapidView=4)
  - [ ] [Grow](https://artsyproduct.atlassian.net/secure/RapidBoard.jspa?rapidView=96&projectKey=GRO)
  - [ ] [Partner Experience](https://artsyproduct.atlassian.net/secure/RapidBoard.jspa?rapidView=36&projectKey=GALL)
  - [ ] [Purchase](https://artsyproduct.atlassian.net/secure/RapidBoard.jspa?rapidView=41)
  - [ ] Check our latest [Staffing Page](https://www.notion.so/artsy/Staffing-c2d58c075e9b41a69e48f6d5fa474fbd) if you want to learn about the compositions of each team
  - [ ] Review [how we use Jira](https://www.notion.so/artsy/Team-Process-Handbook-3fbeb0ae934d48ca9074131331b46cff#ae081daa5b034dc2b6fb5ed4adc1a4bc) in the [Team Process Handbook](https://www.notion.so/artsy/Team-Process-Handbook-3fbeb0ae934d48ca9074131331b46cff) (a work in progress).
- [ ] 🔍 Check out the teams that support and serve the product teams
  - [ ] [Data](https://artsyproduct.atlassian.net/secure/RapidBoard.jspa?rapidView=59)
  - [ ] [Platform](https://artsyproduct.atlassian.net/secure/RapidBoard.jspa?rapidView=64)
- [ ] 🔍 Get a sense of our business and product strategy by looking at the [Product Team's onboarding resources](https://www.notion.so/artsy/Product-Onboarding-9bc3dc747ac44ed2866c8bf37c0c721b#ba384bf0f334435eab87f0e29e5a745b).
  - Specifically browse [Product Management Onboarding](https://www.notion.so/artsy/Product-Management-Onboarding-9bc3dc747ac44ed2866c8bf37c0c721b#4ad2c4707e3740549ee9dc5c62b80461)
- [ ] 🔍 Take a tour of Artsy by navigating around [staging.artsy.net](https://staging.artsy.net). Try following an artist, saving an artwork, inquiring, or making an offer.
  - [ ] Ask your mentor about Gravity's data reset on Saturdays.
- [ ] 🔍 Scan our [QA-able list of interactions](https://www.notion.so/artsy/20YY-MM-DD-Artsy-net-QA-689c76f0a5564e7c94b5908b12ec891b) to see how QA scripts and use-cases are written.
- [ ] 👯 Reach out to product teams and pair with team members on our most important flows on Artsy. Drawing diagrams for system interaction, investigating requests triggered, looking at data fetched/mutated, etc. can help dive deep into what happens behind the scene. Pick 3 from the example flows of each team:
  - [ ] 👯 Ask a member of the Find & Explore team to teach you about our authentication system and go through the process of creating a new user in staging.
  - [ ] 👯 Ask a member of the Purchase team to teach you about our auctions product and place a bid in an auction in staging.
  - [ ] 👯 Ask a member of the Partner Experience team to teach you about CMS (Volt) and upload a new artwork to a test partner in staging.
  - [ ] 👯 Ask a member of the Purchase team to teach you about our e-commerce flow and buy an artwork in staging.
  - [ ] 👯 Ask a member of the Collector Experience team to give you a tour of our app. If you have an iPhone or an Android device, get set up to be able to download the beta of our app and browse in staging.
  - [ ] 👯 Ask a member of the Grow team to walk you through the onboarding flow that collectors experience when they join Artsy by creating an account in staging.
  - [ ] 👯 Ask a member of the Platform team to do a walkthrough of our key systems:
    - [Gravity](https://github.com/artsy/gravity)
    - [Force](https://github.com/artsy/force)
    - [Metaphysics](https://github.com/artsy/metaphysics)

#### Platform learning:

We feel strongly about re-using patterns and infrastructure amongst our
engineering teams. This section is about getting to know some of this shared
infrastructure.

- [ ] 📖 Read about our [high-level Platform architecture](https://www.notion.so/artsy/Platform-Architecture-ad1363b26ea8422db0df08e7c8253677) to get a sense of our major systems.
- [ ] 📖 Read through the [project list](https://www.notion.so/artsy/17c4b550458a4cb8bcbf1b68060d63e6) to get a high-level view of the systems that the engineering team currently maintains.
- [ ] 📹 Watch [How Artsy Automates Team Culture](https://slideslive.com/38916507/how-artsy-automates-team-culture) talk by Ash about Peril and Danger and how we use them.
- [ ] 📹 Watch [this video on Hokusai/Kubernetes](https://drive.google.com/file/d/1VzkBnp0xHTM7vxO4TXmNywn9jh9LNFLx/view) to learn about our deployment system.
- [ ] 📖 To solidify that knowledge, read our [documentation on Kubernetes](https://github.com/artsy/README/blob/main/playbooks/kubernetes.md) and our [monitoring systems](https://www.notion.so/artsy/Monitoring-97d01d1bea214b3ebe3fbe081a888683).
- [ ] 💻 Check out our [Relay Workshop](https://github.com/artsy/relay-workshop) to learn about [Relay](https://relay.dev/), which we use both in our web app and mobile app.
- [ ] 🔍 Look at our top-level Datadog dashboards:
  - [ ] 🔍 [Artsy Systems Overview](https://app.datadoghq.com/dashboard/463-cin-cp4/artsy-systems-overview)
  - [ ] 🔍 [Artsy Operations Overview](https://app.datadoghq.com/dashboard/38q-9jf-bj2/artsy-operations-overview)
  - [ ] 🔍 [Service Map](https://app.datadoghq.com/apm/map?env=production)
- [ ] 🔍 We collect errors in Sentry. If you are not already, become familiar with Sentry's UI by looking at the issues for a few of our most critical projects: [Gravity](https://sentry.io/organizations/artsynet/issues/?project=157936), [Force](https://sentry.io/organizations/artsynet/issues/?project=28316), [Volt](https://sentry.io/organizations/artsynet/issues/?project=1281370), and [Metaphysics](https://sentry.io/organizations/artsynet/issues/?project=299996).
  - [ ] 🛠👯 With your mentor, pick an issue in one of the projects above and diagnose it. Submit a PR with the fix. Deploy that fix to production. Along the way, have your mentor explain our [staging environment](https://github.com/artsy/gravity/blob/master/doc/StagingEnvironment.md) and [how we deploy code](https://github.com/artsy/README/blob/main/playbooks/deployments.md). Examine the relevant workflows in CircleCI. You should leave this with a basic understanding of our deployment pipeline.
- [ ] 🔍 Scan through the issues in Jira labeled ["good-first-issue"](https://artsyproduct.atlassian.net/browse/CX-1689?filter=-4&jql=labels%20%3D%20good-first-issue%20and%20status%20not%20in%20(Done%2CClosed%2CMerged%2CBlocked%2C%22In%20Progress%22%2C%22In%20Review%22%2C%22QA%20Ready%22%2C%20%22Monitoring%2FQA%22)%20order%20by%20created%20DESC).
  - [ ] 🛠👯 With your mentor, pick an issue to work on. Understand the context, set up the project, and submit a PR for the fix. See that fix all the way to production. Along the way, make sure you are following our [PR best-practices](https://github.com/artsy/README/blob/main/playbooks/engineer-workflow.md#pull-requests).
- [ ] 📹 Watch some video overviews of our major systems for a refresher:
  - [ ] [Force](https://drive.google.com/drive/folders/1ZqyuXGriKgHC9xsF53vAaJEAWkgYmLMg?usp=sharing)
  - [ ] [Metaphysics](https://drive.google.com/drive/folders/1O1kRXyUA0jO3OM7gskljiL0IwRFFrwCi)
  - [ ] [Integrity](https://drive.google.com/file/d/1mEatjWJ37vmSsc4n7kbLXEu2evKHK3i-/view?usp=sharing)

#### Incident handling:

Learn about our on-call process.

- [ ] ✅ Join the [#incidents](https://artsy.slack.com/messages/incidents/) slack channel and scan through some recent threads.
- [ ] 📖 Read the [support doc](https://github.com/artsy/README/blob/main/playbooks/support#readme) about how support incidents are handled by our on-call rotation.
- [ ] 📹 Watch the [on-call onboarding video](https://drive.google.com/file/d/1nGtNLCwP9zOBxhocnAFI-Ua1xs7eJYyD/view).
- [ ] 🔍 Ask the [#on-call-working-group](https://artsy.slack.com/messages/on-call-working-group/) slack channel for access to [OpsGenie](https://artsy.app.opsgenie.com/incident/list) and browse some of the "Resolved" incidents. Click into the incidents' postmortems for more information.

#### Get to know our engineering team:

Scan the following list of resources. Ask questions if you'd like more context
or something is confusing.

- [ ] 📖 Read through the following (and anything else you find interesting) from
      [artsy/README](https://github.com/artsy/README):
  - [ ] 📖 Check out the
        [Engineer Workflow](https://github.com/artsy/README/blob/main/playbooks/engineer-workflow.md) for info on how we use project management software and GitHub, among other things
  - [ ] 📖 Besides
        [Artsy’s org-wide values](https://www.notion.so/artsy/Artsy-Values-Behaviors-42a6905b3b4c44e097f860d3e847cc16), the engineering team has its own additional
        [set of principles](https://github.com/artsy/README/blob/main/culture/engineering-principles.md). Check'em both out!
  - [ ] 📖 Read about the [history of our Engineering practices](https://github.com/artsy/README/blob/main/practices/history.md#readme) and dig into each one:
    - [ ] 📖 [Web](https://github.com/artsy/README/blob/main/practices/web.md)
    - [ ] 📖 [Mobile](https://github.com/artsy/README/blob/main/practices/mobile.md)
    - [ ] 📖 [Platform](https://github.com/artsy/README/blob/main/practices/platform.md)
  - [ ] 📖 [Best of Our Blog](https://github.com/artsy/README/blob/main/resources/blog.md)
  - [ ] 📖 Read about [Artsy's engineering career ladder](https://github.com/artsy/README/blob/main/careers/ladder.md)
  - [ ] 📖 [Internal and external tech learning resources](https://github.com/artsy/README/blob/main/resources/tech-learning.md)
  - [ ] 📹 Pick a video from our list of past [Lunch & Learns](https://github.com/artsy/README/blob/main/resources/lnl.md) and watch it. Ask your mentor if you want guidance on which to choose!
- [ ] Read about our [RFC](https://artsy.github.io/blog/2019/04/11/on-an-rfcs-process/) process and look at some of our [recent submitted RFCs](https://github.com/artsy/potential/issues?utf8=%E2%9C%93&q=is%3Aopen%2Cclosed+is%3Aissue+label%3ARFC+).

#### Personal:

Get to know your manager and mentor! If you will be working remotely, take extra
care this week to get to know the team.

- [ ] ✅ Get coffee/tea with your mentor.
- [ ] ✅ Get coffee/tea with your manager.
- [ ] ✅ Schedule coffee/tea with [Sam](mailto:samuel.rozenberg@artsymail.com) in the first few weeks.
- [ ] 📝 Keep track of questions/feedback you have as you go through this process
- [ ] 👯 Work with your mentor to get access to relevant calendars
  - [ ] 📅 [Open Engineering Calendar](https://calendar.google.com/calendar/embed?src=artsymail.com_g81io4a98ddvn1ih1a3lm2ocd4%40group.calendar.google.com&ctz=America%2FNew_York)
  - [ ] 📅 [Out of Office Calendar](https://calendar.google.com/calendar/embed?src=artsymail.com_4l9b71vlvtn9nanc465efqlp80%40group.calendar.google.com&ctz=America%2FNew_York)
  - [ ] 📅 [PDDE OOO Calendar](https://calendar.google.com/calendar/b/1/embed?src=artsymail.com_gl81jptn59gjfv1kg0fer1i4jo@group.calendar.google.com&ctz=America/New_York)
  - [ ] 📅 [Artsy Team Calendar](https://calendar.google.com/calendar/embed?src=admin%40artsymail.com&ctz=America%2FNew_York)
- [x] Add your [working hours](https://support.google.com/calendar/answer/7638168?co=GENIE.Platform%3DDesktop&hl=en&oco=0) to your calendar.

## End of first week

- [ ] ✅ Check-in with your manager. Be sure to chat about any WTFs you've hit
  along the way!
- [ ] 💆 Take a deep breath. You did it!

## Sprint Rotations

_Goal: I understand different product teams' current projects and processes.
I've paired with multiple members of the engineering team and have a sense for
how I might approach tasks._

You'll "rotate" through 3 or more teams for a sprint each. See the [doc on the
sprint
rotation](https://github.com/artsy/README/blob/main/onboarding/sprint-rotation.md)
to understand how this works.

## Join a Team

_Goal: I feel part of a team and understand how my work contributes to making
Artsy the best way to buy art. I'm
learning about Artsy’s stack and systems while also shipping code._

### Before you join:

- [ ] ✅ Make sure you are set up with all relevant meetings by joining the appropriate Google group. Use [this link](https://groups.google.com/all-groups) to search and add yourself to the team's Google group. Ping the Tech lead/PM of the product team if you don't get the meeting invites after joining the team's group.
- [ ] 🔍 If necessary, review that team’s [onboarding docs](https://www.notion.so/artsy/Product-470238180cf94c87906ef1d3ee259e05)
- [ ] 🚀 … go!
