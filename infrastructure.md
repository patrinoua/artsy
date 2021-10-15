# Infrastructure

Repository for Artsy's infrastructure scripts and documentation.

Point people @izakp @joeyAghion

## Setup

Terraform and other dependencies are required for in-depth infrastructure work. Many Artsy engineers only need this repository to set up VPN access, which you can do by:

- [ ] Download and install [Terraform](https://www.terraform.io/downloads.html) **64-bit**
*Terraform is an open-source infrastructure as code software tool that provides a consistent CLI workflow to manage hundreds of cloud services *


- [ ] Install `jq`, `hokusai` and `aws-iam-authenticator`

```
brew install jq
brew tap artsy/formulas
brew install hokusai
brew install aws-iam-authenticator
```

- [ ] Install [Vagrant](https://www.vagrantup.com/downloads.html) (Version >= 1.8.1) _a tool for building and managing virtual machine environments in a single workflow._
- [ ] Install [Virtual Box](https://www.virtualbox.org/wiki/Downloads) (Version >= 5.0.16 r105871) _powerful x86 and AMD64/Intel64 virtualization product _

Install Vagrant plugins: `vagrant plugin install vagrant-bindfs vagrant-share vagrant-vbguest vagrant-berkshelf vagrant-cachier`

#### Configuration

Make sure IAM credentials are configured via `AWS_ACCESS_KEY_ID` / `AWS_SECRET_ACCESS_KEY` / `AWS_REGION`.

Run `hokusai configure --kubectl-version 1.10.7 --s3-bucket artsy-citadel --s3-key k8s/config-admin`

Only IAM users that are trusted entities of the [KubernetesAdmin IAM Role](https://console.aws.amazon.com/iam/home?region=us-east-1#/roles/KubernetesAdmin?section=trust) can perform Kubernetes Cluster-Admin operations with Terraform. Ask in #product-platform if you need to perform cluster-admin tasks.

#### Use

Terraform resources configure and provision cloud resources in the "configuration-as-code" paradigm. Documentation can be found at https://www.terraform.io/docs/index.html

All terraform commands must be run in subdirectories of the `terraform` directory in this repo. i.e.

- `./terraform/shared`
- `./terraform/staging`
- `./terraform/production`

* `cd` to one of these directories then run `terraform init` to initialize the S3 backend and plugin provider dependencies

* Make changes to `*.tf` files describing changes to resources rather than modifying them directly in EC2.

* To preview changes, run `terraform plan`

* Submit a PR for review and tracking changes, then once ready, merge and apply.

* To apply changes, run `terraform apply` - review changes and confirm with `yes`

## Development setup

This section is to install the bare minimum required to use this repo (useful for VPN setup). Make sure to **clone the repository locally** and run all commands from its directory. For example:

```sh
git clone https://github.com/artsy/infrastructure.git
cd infrastructure
```

**1. Install the ssh keypair**. Open the Engineering 1Password vault using the desktop client and locate the `artsyow.pem` file. Click the file once to decrypt it, then right-click and select "Show in Finder" to see the file. Next, open a terminal window and type `ssh-add` (with a space at the end), and then drag the file from Finder into the terminal.

Your command will look something like `ssh-add /private/var/folders/fl/89w91rz55k1bpl1n6p5y7ghh0000gp/T/com.agilebits.onepassword7/com.agilebits.Attachments.noindex/bc4rhkrtdjapzavupdsvfhesbm/artsyow.pem`

**2. Install the correct Ruby version**. Make sure you have the right ruby version installed, check the [.ruby-version file](https://github.com/artsy/infrastructure/blob/master/.ruby-version) for the project's latest version (currently 2.6.5). [rbenv setup instructions are here](https://github.com/rbenv/rbenv#installation). Then run:

```sh
rbenv install 2.6.5
```

**3. Setup AWS tools**. You need your AWS access key and secret pair, which you might have [set up already](https://github.com/artsy/potential/blob/master/platform/AWS.md). If you haven't yet, generate them in the AWS console and add them to `~/.bash_profile` (or equivalent). Specify the region, too:

```sh
export AWS_ACCESS_KEY_ID=YOUR_AWS_ACCESS_KEY
export AWS_SECRET_ACCESS_KEY=YOUR_AWS_SECRET_ACCESS_KEY
export AWS_DEFAULT_REGION=us-east-1
```

Then reload the environment variables:

```sh
source ~/.bash_profile # or equivalent
```

Next, [install the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html): `[sudo] pip install awscli`. Note that `sudo` is technical optional, but you'll probably need it unless you have a Python environment set up already. (If you have trouble on El Capitan with the installed Python six modules, add the `--ignore-installed six` flag.)

Finally, configure aws cli: `aws configure`. It _should_ read your keypair from environment variables, but you can enter them manually if asked for them. If you're having trouble configuring your AWS credentials, [check out these troubleshooting docs](https://aws.amazon.com/premiumsupport/knowledge-center/access-key-does-not-exist/).

**4. Install Knife and Chef**. They are included in this repository's `Gemfile`, so just run`bundle install`.

If you're just setting up VPN access, skip to the [VPN Section](#vpn).

## Cookbook development

Change directory to `site-cookbooks` and run `vagrant status`. Machines you see here can be provisioned with `vagrant up` / `vagrant provision` i.e. `vagrant up vpc`

Create a new cookbook:

- `knife cookbook create -o site-cookbooks/ artsy_foo`

- Add your new cookbook to Berksfile: `cookbook 'artsy_foo', path: './artsy_foo'`

- Add a block describing your new machine to Vagrantfile:

```rb
config.vm.define "artsy_foo" do |vb|
	...
end
```

- Run `vagrant up artsy_foo`, then on subsequent changes, `vagrant provision artsy_foo` to develop recipes on your Vagrant box

- When satisfied with the new recipes, bump cookbook versions if you are changing any existing cookbooks (make sure to also bump the version and change cookbook metadata of any cookbooks that depend on updated cookbooks!) and submit a PR

- When the pull request is merged, bring your local repo up to date with upstream/master (this repo) and tag the new versions of cookbooks. Follow the naming convention `{cookbook_name}-v{cookbook_version}`. For example, if my PR updated the cookbook `artsy_causality` to version `1.0.1`, I would tag master `artsy_causality-v1.0.1` at the PR merge.

- Push new tags with `git push --tags upstream`

- You can now reference the new versions of cookbooks with these tags in project-specific Berksfiles

## VPN

<details><summary>Technical details on cookbooks</summary>

OpenVPN is configured on 'bastion' instances in production and staging VPCs with the artsy_vpn cookbook.

</details>

**1. Install [Tunnelblick](https://tunnelblick.net/)**. This is our VPN client of choice, which you can [download here](https://tunnelblick.net/).

**2. Add a new VPN user**. Edit [`site-cookbooks/artsy_vpn/attributes/default.rb`](https://github.com/artsy/infrastructure/blob/master/site-cookbooks/artsy_vpn/attributes/default.rb) to include your **AWS username**. You can add your user to the `default[:artsy][:vpn][:users]` array, [here is an example](https://github.com/artsy/infrastructure/commit/5f0e18ef488c32a99aaf84ce558ea57dfa6baedd). Commit the change and push it to git for posterity.

**3. Generate the OpenVPN profiles**. Use `chef` to generate the VPN profiles and store them in the `artsy-citadel` S3 bucket. This needs to be done for staging _and_ production, in the _root_ of this repository:

```sh
bundle exec knife solo cook ubuntu@vpn-production-2021.artsy.net --no-chef-check
bundle exec knife solo cook ubuntu@vpn-staging-2021.artsy.net --no-chef-check
```

If you are asked for a password, **stop**. This indicates that the `artsyow.pem` SSH keypair from earlier wasn't installed correctly. Return to [the Development Setup section](#development-setup) for instructions.

**4. Download the OpenVPN Profiles from S3**. This can be done through the AWS console, but let's be cool and use the AWS tools we set up earlier:

```sh
aws s3 cp s3://artsy-citadel/vpn/profiles-2021/production/YOUR_AWS_USERNAME.ovpn ~/Documents/artsy-production.ovpn
aws s3 cp s3://artsy-citadel/vpn/profiles-2021/staging/YOUR_AWS_USERNAME.ovpn ~/Documents/artsy-staging.ovpn
```

**5. Install the VPN profiles in Tunnelblick**. You can double-click the profiles in Finder, or use the terminal:

```sh
open ~/Documents/artsy-production.ovpn
open ~/Documents/artsy-staging.ovpn
```

**6. Configure Tunnelblick**. Tunnelblick is running in your menubar, so click the icon and select "VPN Details..."

![Tunnelblick Menubar UI](readme_images/tunnelblick_menubar.png).

Next, select one of the profiles (staging or production, you'll need to do both) and then the Settings tab, then the Advanced button:

![Tunnelblick UI](readme_images/tunnelblick_ui.png).

In the "Connecting & disconnecting" tab: Ensure "Flush DNS cache after connecting or disconnecting" is checked:

![Tunnelblick Advanced UI](readme_images/tunnelblick_advanced.png)

**6. Test the VPN connection**. You should be able to resolve private DNS names, especially our Kubernetes dashboards. Try connecting to the staging VPN and going to `https://kubernetes.stg.artsy.systems` (or connecting to production and going to `http://kubernetes.prd.artsy.systems`). If you're asked for a password, it worked! (The password is in the Engineering 1Password vault).

**Note**: Only the connections to machines within the IP address range of `10.0._._` will use the VPN connection. The default behavior is that you can access machines in our VPC by DNS and private IP address over the VPN interface, while all other traffic remains over your primary network interface. To route _all_ internet traffic to _any_ host (including http traffic!) select "Route all IPv4 traffic through the VPN" in Tunnelblick settings:

![Tunnelblick Routing Setting](readme_images/tunnelblick_routing.png)

<details><summary>Technical details on modifying our shared VPN configuration</summary>

Add further DNS options in the `push_options` and further traffic routing in the `push_routes` attributes in the `artsy_vpn` cookbook.

</details>

And you're done!

## Knife-Solo

Knife solo manages certain standalone resources outside of AWS OpsWorks.

- Create a role and include the cookbook:

`echo '{ "run_list": [ "recipe[my_new_cookbook::default]" ] }' > roles/my-new-role.json`

- Update Berks:

`berks install`

- Upload the kitchen and run Chef-Zero:

`knife solo cook ubuntu@52.201.252.223 roles/my-new-role.json`

## Using knife solo with roles, nodes, and environments

Connect to the "staging" or "production" VPNs to access machines in the private subnets and resolve internal IPs.

When bootstrapping a new server, ALWAYS generate and commit a client config entry in ./nodes/ and install Chef 12

To prepare a new node (for example `cheeseshop.artsy.net`) in the production environment:

`knife solo prepare ubuntu@cheeseshop.artsy.net roles/cheeseshop.json -E production --bootstrap-version=14.15.6`

Ensure that `knife solo prepare` creates an instance catalog entry named `./nodes/cheeseshop.artsy.net.json`

WARNING! The existence of a client config entry means that further `knife solo` commands will look up this config based on FQDN, and use the run-list / environment defined therein... but unlike Chef server, this CAN BE OVERRIDDEN IF YOU ARE NOT CAREFUL.

IMPORTANT! Once the client config has been created ONLY use `knife solo cook ubuntu@cheeseshop.artsy.net` without ANY additional arguments and without referring to a different IP or FQDN of this machine or you WILL overwrite the role / environment of the server you are provisioning!
