Welcome to the EFK stack sandbox.

EFK stands for Elasticsearch, Fluentd, and Kibana. EFK is a popular and the best open-source choice for the Kubernetes log aggregation and analysis.
Elasticsearch helps solve the problem of separating huge amounts of unstructured data and is in use by many organizations. Elasticsearch is commonly deployed alongside Kibana.

Here we have deployed the EFK stack with one sample application exporting its log to Elasticsearch. Explore the setup, tinker with it and learn various concepts while doing so.


Note: It might take few minutes for kibana UI to come up. To check the status , run the following commands:
```
# To check the status of pods in elastic-stack namespace:
 kubectl -n elastic-stack get pods -o=custom-columns='NAME:.metadata.name,READY:.status.conditions[?(@.type=="Ready")].status'

# To check if Kibana is UP:
until $(curl --output /dev/null --silent --head --fail http://0.0.0.0:30601); do
    echo 'Waiting for Kibana UI...'
    sleep 5
done
```
