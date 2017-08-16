
1. Create a Google Cloud function with `Cloud Pub/Sub topic` as trigger
1. Select `eu.gcr.io%2F{YOUR_PROJECT_NAME}` from the topic dropdown
1. Write a simple cloud function
```
exports.pubsubTest = function pubsubTest (event, callback) {
  callback();
}
```
1. Set `pubsubTest` as function to execute
1. Save it
1. Clone this repository
1. Update the following placeholder in `Jenkins`
  - `SOME_JENKINS_NODE` The name of a Jenkins node
  - `YOUR_PROJECT_NAME` Your GCP name
1. Commit and push the changes
1. Update the git url in the `job.xml` file and import into Jenkins
1. Run the job

### Expected result
A Pub/Sub topic `eu.gcr.io%2F{YOUR_PROJECT_NAME}` which invokes the cloud function.

### Actual behaviour
Cloud function is not invoked
