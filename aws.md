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

Please set up 2 Factor Authentication (2FA) using this [link](https://console.aws.amazon.com/iam/home?region=us-east-1#/security_credentials)

#### Select Assign MFA Device 

![Image](https://github.com/patrinoua/artsy/blob/main/Screenshot%202021-10-14%20at%2011.33.27.png)
