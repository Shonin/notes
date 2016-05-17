Easy Deploy to AWS S3
=====================

We'll be using a ruby gem called `dandelion`

This is a from scratch install

You'll need:

* RVM (ruby version manager)
* Ruby >= 2.0.0
* Something to manage env variables (I use autoenv, a python package)

(set your default ruby -v w/  `rvm --default use 2.1.1` or whatever you have installed above 2.0.0)

A good resource for making an S3 bucket as a website: https://github.com/jamestalmage/s3-static-site-uploader
Instructions for danelion: https://github.com/scttnlsn/dandelion

an example `dandelion.yml`

    adapter: s3
    access_key_id: <%= ENV['AWS_ACCESS'] %>
    secret_access_key: <%= ENV['AWS_SECRET'] %>
    bucket_name: <%= ENV['AWS_BUCKET'] %>
    host: s3.amazonaws.com
    
    exclude:
        - .gitignore
        - dandelion.yml
        - .env
