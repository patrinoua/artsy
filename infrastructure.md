# Infrastructure

Repository for Artsy's infrastructure scripts and documentation.

Point people @izakp @joeyAghion

## Setup

Example .zshrc file [link](https://github.com/patrinoua/artsy/blob/main/.zshrc)

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

## VPN [link](https://github.com/patrinoua/artsy/blob/main/vpn.md)


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
