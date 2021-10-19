## VPN 

<details><summary>Technical details on cookbooks</summary>

OpenVPN is configured on 'bastion' instances in production and staging VPCs with the artsy_vpn cookbook.

</details>

**1. Install [Tunnelblick](https://tunnelblick.net/)**. This is our VPN client of choice, which you can [download here](https://tunnelblick.net/).

**2. Add a new VPN user**. Edit [`site-cookbooks/artsy_vpn/attributes/default.rb`](https://github.com/artsy/infrastructure/blob/master/site-cookbooks/artsy_vpn/attributes/default.rb) to include your **AWS username**. You can add your user to the `default[:artsy][:vpn][:users]` array, [here is an example](https://github.com/artsy/infrastructure/commit/5f0e18ef488c32a99aaf84ce558ea57dfa6baedd). Commit the change and push it to git for posterity.

**3. Generate the OpenVPN profiles**. Use `chef` to generate the VPN profiles and store them in the `artsy-citadel` S3 bucket. This needs to be done for staging _and_ production, in the _root_ of this repository (infrastructure):

```sh
bundle install
bundle exec knife solo cook ubuntu@vpn-production-2021.artsy.net --no-chef-check
bundle exec knife solo cook ubuntu@vpn-staging-2021.artsy.net --no-chef-check
```

If you are asked for a password, **stop**. This indicates that the `artsyow.pem` SSH keypair from earlier wasn't installed correctly. Return to [the Development Setup section](https://github.com/artsy/infrastructure/#development-setup) for instructions.

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
