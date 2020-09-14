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

If you haven't installed hub, you need that first.

~~~
$ sudo apt-get install hub
~~~
{: .language-bash}

Create a directory Once the repository exists you can push changes to the repository online. Here are a series of commands that assume you have an ssh key set up with github.

~~~
$ mkdir [project]
$ cd [project]
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

You should now be able to push your changes to github.

~~~
$ git remote add origin git@github.com:[username]/[project].git
$ git push -u origin master
~~~
{: .language-bash}

For some Arduino programs, you may need to "add" other files, but avoid including the compiled files (.elf and .hex). Create a ".gitignore" file that includes these patterns to avoid adding them by mistake.

~~~
*.elf
*.hex
~~~
{: .source}

{% include links.md %}
