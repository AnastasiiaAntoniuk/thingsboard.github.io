## Instructions for Contributing to the Docs/Website

* [Fork this repository](https://help.github.com/articles/fork-a-repo/)
* [Deploy the site locally](#deployment-of-the-site-locally)
* Add your changes
* [Generate image preview](#image-preview-generator)
* [Create Pull Request](https://help.github.com/articles/creating-a-pull-request/)

## Deployment of the site locally

The below commands set up your environment for running GitHub pages locally. 
Any edits you make will be viewable on a lightweight webserver that runs on your local machine.

Install Ruby **2.7.x**. If you're on Ubuntu 20.04.1 LTS, run these commands:

	sudo apt-get install software-properties-common
	sudo apt-add-repository ppa:brightbox/ruby-ng
	sudo apt-get update
	sudo apt-get install make ruby ruby-dev libffi-dev g++ zlib1g-dev
	sudo gem install github-pages
	sudo gem install jekyll bundler

* If you're on a Mac, follow [these instructions](https://gorails.com/setup/osx/) and choose Ruby 2.7.6.
* If you're on a Windows machine you can use the [Ruby Installer](http://rubyinstaller.org/downloads/). During the installation make sure to check the option for *Add Ruby executables to your PATH*.


Clone our site:

	git clone https://github.com/thingsboard/thingsboard.github.io.git

Make any changes you want. Then, to see your changes locally:

	cd thingsboard.github.io
	bundle install
	bundle exec jekyll serve --host 0.0.0.0
	
In case you change the layout or website structure you might need to execute following command:

    rm -rf _site .jekyll-metadata && bundle exec jekyll serve --host 0.0.0.0
        
or execute the below script from the project root directory:
        
    ./restart.sh


Your copy of the site will then be viewable at: [http://localhost:4000](http://localhost:4000)
(or wherever Jekyll tells you).

## Image preview generator

For new *.png images preview is required along with original images.

To create a previews use the script
````bash
#run once
#install mogrify utility to perform resize 
sudo apt install graphicsmagick-imagemagick-compat
````
Usage:
```bash
./generate-previews.sh path file_mask*.png
```
Example:
```bash
./generate-previews.sh images/solution-templates *.png
```

## Linkchecker

Use the following command to check the broken links.

```bash
docker run -it --rm --network=host ghcr.io/linkchecker/linkchecker --check-extern http://0.0.0.0:4000/
```
