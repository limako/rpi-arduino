---
title: "Using git for Arduino programs"
teaching: 20
exercises: 10
questions:
- "How can I maintain Arduino programs with git?"
- "How can I create a github reposistory from the command line?"
objectives:
- "Use git for version control with Arduino sketches."
keypoints:
- "Maintain all your programming in version control."
---

You should consider using version control for any serious programming you do. Here is a quick set up steps to help you create a repo and maintain a repository with an Arduino program.

You should have an account at github, an ssh key, and have git configured on your raspberry pi. If you've gone through the [Software Carpentry Version Control with Git](http://swcarpentry.github.io/git-novice/) you should have already set up most of these.

You can check your ssh keys by listing the contents of your .ssh directory

~~~
$ ls -al ~/.ssh
~~~
{: .language-bash}

If you don't have an id_rsa.pub file listed, you can create one:

~~~
$ ssh-keygen
~~~
{: .language-bash}

Follow along with the prompts and leave the password blank.

To configure github to use your public key, you can list out the key:

~~~
$ cat ~/.ssh/id_rsa.pub
~~~
{: .language-bash}

Then select and copy the contents of the key, visit your [GitHub settings page](https://github.com/settings/keys), click New SSH key, and past the key into the field. (You also have to give the key a title -- you can use the hostname of your pi.)

Finally, test the configuration:

~~~
$ ssh -T git@github.com
~~~
{: .language-bash}

You can check your git configuration with git config:

~~~
$ git config -l
~~~
{: .language-bash}

If your user.email and user.name are not set, you can set them:

~~~
$ git config --global user.email "you@example.com"
$ git config --global user.name "Your Name"
$ git config --global init.defaultBranch main
~~~
{: .language-bash}

If you haven't installed hub, you need that first.

~~~
$ sudo apt-get install hub
~~~
{: .language-bash}

Create a directory Once the repository exists you can push changes to the repository online. Here are a series of commands that assume you have an ssh key set up with github.

~~~
$ mkdir projectname
$ cd projectname
$ touch README.md
$ git init
$ git add *
$ git commit -m "First commit."
~~~
{: .language-bash}

With hub you can interact with github and easily create a new repository:

~~~
$ hub create
~~~
{: .language-bash}

Or you should be be able to. Unfortunately, you currently may need to create a
"personal access token" for hub via Settings -> Developer Settings -> Personal Access Tokens. Once you create
a token, you can copy it and then paste it in where you get asked for a password. 

You should now be able to push your changes to github.

~~~
$ git remote add origin git@github.com:USERNAME/projectname.git
$ git push -u origin main
~~~
{: .language-bash}

For some Arduino programs, you may need to "add" other files, but avoid including the compiled files (.elf and .hex). Create a ".gitignore" file (e.g. "nano .gitignore") an insert these patterns to avoid adding them by mistake. 

~~~
*.elf
*.hex
~~~
{: .source}

Then you can use the following commands to push changes to your github repository.
~~~
$ git add *
$ git commit -m "informative message"
$ git push
~~~
{: .language-bash}


{% include links.md %}
