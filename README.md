# GCP Cloud Functions to synchronize changes in a GCP cloud storage bucket into a Sesam.io node

### function-oncreated.go 

Contains cloud function code to execute with trigger type `Cloud storage` and event type `Finalise/Create`. This function uses GCP Secret Manager to retrieve JWT token to access Sesam node. Check environment variables section for details.  

#### Env vars
* SESAM_PIPE_NAME - name of receiver pipe (see example in example-pipe.json)
* SESAM_NODE_NAME - name of Sesam.io node
* SESAM_TOKEN_SECRET - name of secret where JWT token to access the node is stored (cloud function service account must have permission to read it)
