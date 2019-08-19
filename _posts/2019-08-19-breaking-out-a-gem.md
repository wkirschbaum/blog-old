---
layout: post
title:  Breaking out a gem
date:   2019-08-19 08:51:20 +0200
categories: ruby programming
---

If you have some code to abstract in an application, you don't have to do a big bang change to rewrite the code. Use the following steps as a guideline.

1. Identify what you want to abstract
2. Roughly move the code you want to abstract into a separate file or folder.
3. Write some new tests against the new abstraction
4. Think about how the code can be used from different projects
5. Start removing any existing project specific code out of the new abstraction
6. Finish the refactor and submit your changes
7. Create a new gem and copy the code over
8. Do a local reference to your gem and test if it is working
9. Remove the new abstraction from your existing project
10. Test if the project works with the reference to the gem
11. Publish the gem
12. Replace the local reference with the real reference to the gem
13. Submit your changes to the project
