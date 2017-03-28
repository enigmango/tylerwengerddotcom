# tylerwengerddotcom

Source code for https://www.tylerwengerd.com. Built with Hugo.

## Overview
Hugo is a static site generator - it converts text files
([in markdown/TOML format](https://gohugo.io/content/example/)) into HTML pages.

This repo contains configuration files for the Hugo engine, along with all the
content Hugo needs to create the HTML files that make up www.tylerwengerd.com.

This repo is also configured to perform the following actions when a new
commit is added to the master branch:
* Spin up a virtual machine (actually a Docker container) with Hugo on it
* Create the HTML files with Hugo on the container
* Upload the HTML files to an AWS S3 bucket (which is configured to act as a static
web host)

With this flow, as soon as a new commit is pushed to the master branch, the new
content is converted to HTML and www.tylerwengerd.com is updated. All you have
to do is write some markdown. Nice.

## Layout
* `content/`: Post content stored in markdown/TOML format.
  * Content in this directory is under the 
  [Creative Commons BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)
  license.
* `static/`: Images, favicons, et cetera. Basically any non-text content needed
by the site.
* `themes/`: Hugo theme configuration.
  * `themes/unattended` is my custom theme; feel free to mash it up.
* `gitlab-ci.yml`: The configuration file that tells GitLab CI to run Hugo and
upload the content to S3.
* `config.toml`: The Hugo configuration file.