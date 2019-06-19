# nifi-ci-cd
This project is demonstrate CI/CD process in nifi
References : 
* https://community.hortonworks.com/articles/210286/storing-apache-nifi-versioned-flows-in-a-git-repos.html
* https://pierrevillard.com/2018/04/09/automate-workflow-deployment-in-apache-nifi-with-the-nifi-registry/

# How to export and import Nifi workflow from nifi registry using nifi-toolkit 
* Find Which bucket you would like to export flow <br>
  'registry list-buckets' <br>
  Output
  
|      | Name                | Id                                   | Description |
| ---- |:-------------------:| :-----------------------------------:| -----------:|
| 1    | Local_Nifi_Bucket   | <b>7b4aedd4-d56d-474c-ba4b-d3828fa924ae</b> |(empty)      | 
| 2    | Local_Nifi_Bucket_2 | e6f33205-199b-4240-90c1-86eea4622b89 |(empty)      | 

* Find Which flow you would like to export for given bucket<br>
registry list-flows --bucketIdentifier <b>7b4aedd4-d56d-474c-ba4b-d3828fa924ae</b>

|     |Name           |Id                                    |Description|
|---- |:-------------:|:------------------------------------:| ---------:|   
|1    | Test Git Flow |  0ed6fbf0-605c-4305-85c3-f371a456f99c|           |

* Find Which flow version you would like to export for given flow<br>
registry list-flow-versions --flowIdentifier <b>0ed6fbf0-605c-4305-85c3-f371a456f99c</b>

|Ver  |Date                        |Author     |Message |  
|---  |:--------------------------:|:---------:|-------:| 
|1    |Mon, Jun 17 2019 07:56 IST  |anonymous  |        |

# How to start and stop NiFi Workflow using nifi-toolkit 
'nifi pg-import --bucketIdentifier 7b4aedd4-d56d-474c-ba4b-d3828fa924ae --flowIdentifier 0ed6fbf0-605c-4305-85c3-f371a456f99c --flowVersion 1'

# 70493818-016b-1000-b64d-682ea1eb9c7c

#
# nifi pg-start --processGroupId 70493818-016b-1000-b64d-682ea1eb9c7c
#> nifi pg-stop --processGroupId 70493818-016b-1000-b64d-682ea1eb9c7c
