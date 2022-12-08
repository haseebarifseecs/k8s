# ConfigMaps allow us to store app configurational data.

#### With Config Maps we can store data in the form of key value pairs and then can reference it in Pod Def file or load it as environment variable.
#### To Create CM Imperatively run the following command

```
kubectl create cm "ConfigMapName" --Options
```

#### You can either load configuration from a file (Having Data in key value pairs) or Parse it as a literal string

```
kubectl create cm "ConfigMapName" --from-file=/path/to/file.properties

kubectl create cm "ConfigMapName" --from-literal=key1=value1 --from-literal=key2=value2
```


#### For Config Files we can import the configmap as a volume mount by specifying ConfigMap as volume type. These configs are not persistent though. (Ephemeral)

