[![Build Status](https://travis-ci.org/cghall/EasyCRM.svg?branch=master)](https://travis-ci.org/cghall/EasyCRM)
# EasyCRM
An open source Customer Relationship Management system powered by Flask and SQLAlchemy.

**Originally Created by [Chris Hall](www.chrishall.io)**

**Modified by Yu**


# Prerequisite

This app only works with python:3.6.4 so please setup your local python environment to use version 3.6.4

### How to verify your python version

`python --version` should print out "Python 3.6.4".

You can refer to [devops_initial_setup](https://github.com/JiangRenDevOps/DevOpsLectureNotesV5/blob/master/WK1-CDN-DNS/devops-initial-setup.md) on how to create a python virtual environment.

# Deploy EasyCRM locally

## Without Docker

1. Install all the dependencies
```
pip3 install -r requirements.txt
```
2. Create the db table
```
python manage.py create_db
```
3. Run the app
```
python run.py
```

## With Docker

1. Build Docker image `easycrm`
```
docker build -t easycrm .
```
2. Create a Docker container
```
docker run -p 8090:8090 easycrm
```
Now you can access http://0.0.0.0:8090/login/ with Username `test@gmail` and Password `shh`

# APIs
auth -> controller
```
/login/
```

core -> controller
```
/
/contact/create
/contact/<con_id>
/organisation/create
/organisation/<org_id>
```

# Folder Structure

```
- app
   |_ auth ...... controller, form helper and model for authentication
   |_ core ...... controller, form helper and model for core functions
   |_ database ...... admin data initialisation
   |_ templates ...... HTML templates for simple webpages
- tests ...... Unit Test files
- config.py ...... DB config for test
- manage.py ...... DB operation
- run.py ...... Run the App from here
```

# DevOps Ideas

1. Fork and separate the branch to master(dev), staging, prod
2. Improve the Travis(Github)/Pipeline(Bitbucket) for build, test and deploy to AWS EC2
3. Dockerise the app and build, test and deploy via Docker
4. Set up statsd, prometheus and grafana for monitoring
5. Add code to probe certain endpoints for monitoring the reliability, traffic and latency
6. Use a load tester to test the performance and monitor it. Point out the problems
7. Set up a CDN and Application Load Balancer
8. Use Terraform for monitor/infra set up

## Advanced

1. Separate the database, core logic and auth into multiple microservices
2. Generate 10000 DB entries
3. Add an external cache to load entries faster
4. Introduce autoscaling via EBS

## Other

1. Write a better frontend code in a different repo
2. Setup deployment for the frontend to S3
3. Point CloudFront to the S3
4. Use Terraform to do the deployment