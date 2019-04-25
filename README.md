
# usage 

## HelloWorld

```
 gcloud functions deploy HelloWorld --runtime go111 --trigger-http 
```

```
curl https://us-central1-k8s-demo-233507.cloudfunctions.net/HelloWorld
```

```
gcloud functions delete HelloWorld
```

## pstrigger

k8s-demo-233507

```
gcloud services enable cloudfunctions.googleapis.com
```

```
gcloud pubsub topics create randomNumbers
```

```
./gomod.sh
```


```
gcloud functions deploy api --entry-point Send --runtime go111 --trigger-http --SET-ENV-VARS PROJECT_ID=k8s-demo-233507
```

```
gcloud beta functions deploy api --entry-point Send --runtime go111 --trigger-http --set-env-vars PROJECT_ID=k8s-demo-233507
```

```
root@IA:~/gocode/src/github.com/myself659/gcp-serverless-demo/pstrigger/api# gcloud beta functions deploy api --entry-point Send --runtime go111 --trigger-http --set-env-vars PROJECT_ID=k8s-demo-233507
Deploying function (may take a while - up to 2 minutes)...done.                                                        
availableMemoryMb: 256
entryPoint: Send
environmentVariables:
  PROJECT_ID: k8s-demo-233507
httpsTrigger:
  url: https://us-central1-k8s-demo-233507.cloudfunctions.net/api
labels:
  deployment-tool: cli-gcloud
name: projects/k8s-demo-233507/locations/us-central1/functions/api
runtime: go111
serviceAccountEmail: k8s-demo-233507@appspot.gserviceaccount.com
sourceUploadUrl: https://storage.googleapis.com/gcf-upload-us-central1-5e391ea3-357c-47a9-beff-867e04377eb7/1a2d9d09-dbe3-44bd-8a95-d62409f8b69a.zip?GoogleAccessId=service-866513079190@gcf-admin-robot.iam.gserviceaccount.com&Expires=1552401451&Signature=Pf%2Fr%2FtjMDwcm3bdQm5xVED4eB%2B0%2Bw%2BvmyQ3G9JtVRY8R%2FQu60FMjN8yChftDXGdcoQn5bUwM7yBKDC0e2m%2BXHQ6Uez72KS6HiOYdwd6b6I4iUTGMQE4nRUWESiqbT0nXJWdEFBB9ZnpOhDMbcVlt7lJWnTzhe6W3BI30wUtxmfBr3WqbDTRea4I0lU9tMWAM9QsA%2FuSIyxn2YdzeNALm%2Ba6vYlG5jq5ipXAWUWuhVew3cuKxZTJQgReWCzZJcSgWR7C3XdD6qwjadUdVS70672vbOsmdqOKVY83HgaDNPwIA0gS4yn4NX78eyHDYYysnx2Du1QQ0%2FC217gmnUnh66A%3D%3D
status: ACTIVE
timeout: 60s
updateTime: '2019-03-12T14:12:44Z'
versionId: '1'
```

```
gcloud functions deploy consumer --entry-point Receive --runtime go111 --trigger-topic=randomNumbers
```

```
root@IA:~/gocode/src/github.com/myself659/gcp-serverless-demo/pstrigger/consumer# gcloud functions deploy consumer --entry-point Receive --runtime go111 --trigger-topic=randomNumbers
Deploying function (may take a while - up to 2 minutes)...done.                                                        
availableMemoryMb: 256
entryPoint: Receive
eventTrigger:
  eventType: google.pubsub.topic.publish
  failurePolicy: {}
  resource: projects/k8s-demo-233507/topics/randomNumbers
  service: pubsub.googleapis.com
labels:
  deployment-tool: cli-gcloud
name: projects/k8s-demo-233507/locations/us-central1/functions/consumer
runtime: go111
serviceAccountEmail: k8s-demo-233507@appspot.gserviceaccount.com
sourceUploadUrl: https://storage.googleapis.com/gcf-upload-us-central1-5e391ea3-357c-47a9-beff-867e04377eb7/38ee8892-4419-45d3-b159-7ba46ed7d7e8.zip?GoogleAccessId=service-866513079190@gcf-admin-robot.iam.gserviceaccount.com&Expires=1552401908&Signature=MQDxh19Uj8DkEUUuc5bqgD7mOgd37bjzChFxB7xa5l99rMT%2FvTLlNNh9diDqttB%2BeUtX7fULyQENYmlSbz9V%2FT07YS0SAqhQxWU6SZEQJJMqkwwFAMYNLNhPzCmyKQnMwpcAmwNLIfOHAEEJ%2B5A05uojw6taMt5rdEkMOEi9IR38JrFtqYq83BZh%2F3CcTmOKxzczUoH5L07RXyI22o%2FIgSruQPvi5HAAa1t%2FFeQJqgIyrEvLvrS%2F3o36dnEDi5HO4lx5qf1t2WTb%2BcQAdA9iA07eD5MKMOaJJzi3%2BdN4rJx3Y0ite8o7ZYgJl0mFta4UcotTwM9MwiR4bhOdJa28vg%3D%3D
status: ACTIVE
timeout: 60s
updateTime: '2019-03-12T14:16:01Z'
versionId: '1'
```

```
gcloud functions logs read consumer
```

```
root@IA:~/gocode/src/github.com/myself659/gcp-serverless-demo/pstrigger/consumer# gcloud functions logs read consumer
LEVEL  NAME      EXECUTION_ID     TIME_UTC                 LOG
D      consumer  431046056508290  2019-03-12 14:20:37.400  Function execution started
       consumer  431046056508290  2019-03-12 14:20:37.413  2019/03/12 14:20:37 694
D      consumer  431046056508290  2019-03-12 14:20:37.414  Function execution took 15 ms, finished with status: 'ok'
D      consumer  431035728233357  2019-03-12 14:20:42.364  Function execution started
       consumer  431035728233357  2019-03-12 14:20:42.365  2019/03/12 14:20:42 403
D      consumer  431035728233357  2019-03-12 14:20:42.367  Function execution took 3 ms, finished with status: 'ok'
```

