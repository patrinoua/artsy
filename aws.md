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

#### ❗️ Please Set up 2 Factor Authentication [link](https://github.com/patrinoua/artsy/blob/main/aws-2fa.md)
#### Install the AWS CLI

For this we need a later version of python than the one already installed so we will do that by installing asdf, a version manager for python, node, ruby and yarn.

```
# Install asdf, version manager for python, node, ruby, yarn

brew install asdf

# Not sure
echo -e "\n. $(brew --prefix asdf)/libexec/asdf.sh" >> ${ZDOTDIR:-~}/.zshrc

# Add python plugin
asdf plugin-add python

asdf install python 3.9.5

asdf global python 3.9.5

# See which python version is locally installed
asdf list python

# See all python versions installed
asdf list-all python

```
Now we have the 3.9.5 version of python and we can run

```$ sudo ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws```

which installs **awscli**
