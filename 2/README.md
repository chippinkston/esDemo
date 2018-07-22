# 2 New Index

ElasticSearch (ES) uses the same basic search process as SOLR.  The main difference in the interaction.  ES has a very well done REST API.  It also returns everything as JSON, so it is very easy to consume.  Indicies are pretty much equivalent to SOLR CORES.

### Check current indecies:

In Postman, make a `GET` request to: `http://{{esHost}}/_cat/indices?v&s=index` to see the current indecies

|METHOD|ARGUMENT|
|------|--------|
| GET | http://{{esHost}}/_cat/indices?v&s=index |

In a fresh copy, you should get back: a line like so:

`health status index uuid pri rep docs.count docs.deleted store.size pri.store.size`

Because there are no indices in your environment.

### Create an index

|METHOD|ARGUMENT|
|------|--------|
| PUT | http:{{esHost}}/foo |

Check this new index exists by using the commands from above to get the indexes.  You should now see a 'foo' index.

### Feed it some data

Part of what makes ES so nice is that it doesn't care what you give it (out of the box).

Try these two commands for some fun:

|METHOD|ARGUMENT|BODY|
|------|--------|----|
| PUT | http:{{esHost}}/foo |{"myID": "001","myBody":"bar"}|
| PUT | http:{{esHost}}/foo |{"myID": "001","myBody":true}|

