# GCP Cloud Functions to propagate changes in a GCP cloud storage bucket into a Sesam.io node

**This function will not files stored in bucket before function was started**

### function-oncreated.go 

Contains cloud function code to execute with trigger type `Cloud storage` and event type `Finalise/Create`. This function uses GCP Secret Manager to retrieve JWT token to access Sesam node. Check environment variables section for details.  

#### Env vars
* SESAM_PIPE_NAME - name of receiver pipe (see example in example-pipe.json)
* SESAM_NODE_NAME - name of Sesam.io node
* SESAM_TOKEN_SECRET - name of secret where JWT token to access the node is stored (cloud function service account must have permission to read it)

#### Pipe setup

To push data into Sesam an http_endpoint source pipe is needed. An exapmple provided below.

```json
{
    "_id": "example-pipe",
    "type": "pipe",
    "source": {
      "type": "http_endpoint"
    },
    "transform": [{
      "type": "dtl",
      "rules": {
        "default": [
          ["add", "_id", "_S.selfLink"],
          ["copy", "*"]
        ]
      }
    }]
  }
```
