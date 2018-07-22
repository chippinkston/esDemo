# 1. ElasticSearch env
This is just creating a basic ElasticSearch (called ES from now on) environment.  We'll be using Docker for this to make it easy.

From a terminal run:

    cd ../docker
    docker-compose up -d --build
    
This command will build an instance of ES and an instance of Kibana as well.

You can test that your ElasticSearch instance is running by running:

    curl htp://127.0.0.1:9200

This should return a message like:
```{
  "name" : "F_EZUbK",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "FPUuvogUQGmxYxpgDCAQDA",
  "version" : {
    "number" : "6.3.1",
    "build_flavor" : "default",
    "build_type" : "tar",
    "build_hash" : "eb782d0",
    "build_date" : "2018-06-29T21:59:26.107521Z",
    "build_snapshot" : false,
    "lucene_version" : "7.3.1",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
}
```

Look for that `"tagline" : "You Know, for Search"` to ensure that your ES instance is running.

You can also check that Kibana is running by visiting `http://127.0.0.1:5601` and confirming that the servvice is opperating.

### Postman setup.

If you are using Postman, please take this moment to set up an environment:

1. Go to the 'New' button in the upper left.
1. Select 'Environment' from the drop down.
1. In the modal, enter:
    1. `local` for environment name
    1. `esHost` for the key.
    1. `127.0.0.1:9200` for the value.
1. Press 'Add' to save this mapping.

Select the environment from the drop down in the left corner where it says 'No Environment'.

Test it by sending a:
'GET' to `http:{{esHost}}` to confirm that it is working.