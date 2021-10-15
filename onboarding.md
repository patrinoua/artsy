Mentor:

Manager:

## Your first day

_Goal: I've met my manager, mentor, and some members of the engineering team
(over lunch!). I've logged into slack, google (artsymail), Jira, 1Password, and
know how to use the coffee machine._

- [ ] ✅ Add a cool pic of yourself to Slack and Jira.
- [ ] ✅ Update your Slack profile with new personal information such as Github and your AWS username (which your manager should have given you).
- [ ] ✅ Say hi in [#dev](https://artsy.slack.com/messages/dev) with a :wave:.
- [ ] ✅ Join Slack Channels [Produce/Engineering](https://github.com/artsy/README/blob/main/culture/slack.md),  [Social](notion://www.notion.so/18b56c8d7eb744e08f2f5a4073095d04?v=58f38ea64f494b83817b94b802fb0230)


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
- [ ] 🔍 Review that team’s [onboarding docs](https://www.notion.so/artsy/Product-470238180cf94c87906ef1d3ee259e05)
- [ ] 🚀 … go!
