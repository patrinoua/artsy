## AWS

For logging in

You should have received a note from your manager including 

**Account id** => Artsy 

**IAM username** => $yourUsserNameHere 

**Password** => $yourUserName

That you can use on this [link]() *MISSING*


```
> code .zshrc

# paste there

export AWS_ACCESS_KEY_ID=your_access_key_id #provided by your manager
export AWS_SECRET_ACCESS_KEY=your_secret_access_key #provided by your manager
export AWS_DEFAULT_REGION=us-east-1 

```

check also a set up for your .zshrc file [here](https://github.com/patrinoua/artsy/blob/main/.zshrc)

#### Set up 2FA 

Set up 2 Factor Authentication (2FA) using this [link](https://console.aws.amazon.com/iam/home?region=us-east-1#/security_credentials)

Select Assign MFA Device 

![Image](https://github.com/patrinoua/artsy/blob/main/Screenshot%202021-10-14%20at%2011.33.27.png)

Choose virtual MFA device 
![Image](https://github.com/patrinoua/artsy/blob/main/Screenshot%202021-10-13%20at%2014.09.13.png)

You can use step two and continue with either QR Code or Secret key. You can find those on this [link](https://team-artsy.1password.com/profile)

![Image](https://github.com/patrinoua/artsy/blob/main/Screenshot%202021-10-15%20at%2015.18.00.png)

Select 1 time password on 1password
![Image](https://github.com/patrinoua/artsy/blob/main/Screenshot%202021-10-14%20at%2011.40.39.png)
add it when prompted
![Image](https://github.com/patrinoua/artsy/blob/main/Screenshot%202021-10-15%20at%2015.23.40.png)

