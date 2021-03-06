# nifi-ci-cd
This project is demonstrate CI/CD process in nifi <br>
References : 
* https://community.hortonworks.com/articles/210286/storing-apache-nifi-versioned-flows-in-a-git-repos.html
* https://pierrevillard.com/2018/04/09/automate-workflow-deployment-in-apache-nifi-with-the-nifi-registry/
* https://bryanbende.com/development/2018/06/20/apache-nifi-registry-0-2-0

# How to export and import Nifi workflow from nifi registry using nifi-toolkit 
* Get the list of bucket, you would like to export flow <br>
  ```javascript 
  registry list-buckets'
  ```
Output :- 
  
|      | Name                | Id                                   | Description |
| ---- |:-------------------:| :-----------------------------------:| -----------:|
| 1    | Local_Nifi_Bucket   | 7b4aedd4-d56d-474c-ba4b-d3828fa924ae |(empty)      | 
| 2    | Local_Nifi_Bucket_2 | e6f33205-199b-4240-90c1-86eea4622b89 |(empty)      | 

* Get the list of flow, you would like to export for given bucket<br>
  ```javascript 
  registry list-flows --bucketIdentifier 7b4aedd4-d56d-474c-ba4b-d3828fa924ae
  ```
Output :-

|     |Name           |Id                                    |Description|
|---- |:-------------:|:------------------------------------:| ---------:|   
|1    | Test Git Flow |  0ed6fbf0-605c-4305-85c3-f371a456f99c|           |

* Get the flow version you would like to export for given flow<br>
  ```javascript 
  registry list-flow-versions --flowIdentifier 0ed6fbf0-605c-4305-85c3-f371a456f99c
  ```
Output :-

|Ver  |Date                        |Author     |Message |  
|---  |:--------------------------:|:---------:|-------:| 
|1    |Mon, Jun 17 2019 07:56 IST  |anonymous  |        |

# How to start and stop NiFi Workflow using nifi-toolkit 
* Import Flow to NiFi UI from NiFi Registry
  ```javascript 
  'nifi pg-import --bucketIdentifier 7b4aedd4-d56d-474c-ba4b-d3828fa924ae --flowIdentifier 0ed6fbf0-605c-4305-85c3-f371a456f99c --flowVersion 1'
  ```
  Output :- Output will disply a uniqe processor group id.
  ```javascript 
  70493818-016b-1000-b64d-682ea1eb9c7c
  ```  
* Start Nifi Processor group
  ```javascript 
  nifi pg-start --processGroupId 70493818-016b-1000-b64d-682ea1eb9c7c
  ```
* Stop Nifi Processor group
  ```javascript 
  nifi pg-stop --processGroupId 70493818-016b-1000-b64d-682ea1eb9c7c
  ```
