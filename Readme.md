# Sample Python Deployment on GCP

This repository is a template for building a docker container with a python script on GCP. 

How to use:
1. Grab the Dockerfile and cloudbuild.yaml from this repo and move into your project
2. Update the repository URL in the two docker steps in cloudbuild.yaml
    - If it doesn't already exist, create the repository in Artifact Registry in the GCP Console
3. Update the entrypoint to your script in the Dockerfile. Required packages should be listed in requirements.txt
4. Define the build trigger in the GCP console
    - Cloud Build > Triggers > Create Trigger
    - Define your Repositry, Branch, and Event to suit your needs
    - Make sure the Service Account has the permissions required to push to Artifact Registry in IAM
5. Trigger your build as you defined in step 4. The image should show up in Artifact Registry shortly.
6. Create a Cloud Run Job and associated trigger to run the script automatically
    - Cloud Run > Jobs > Create Job
    - Once Created, open the Job again and choose 'Triggers'
    - 'Add Scheduler Trigger'