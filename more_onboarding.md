### A deeper dive into the Artsy world!

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
