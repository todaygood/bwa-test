
ot@fedora28 project]# cd cromwell/
[root@fedora28 cromwell]# ls
cromwell-34.jar
[root@fedora28 cromwell]# java -jar cromwell-34.jar run ../myWorkflow.wdl 
[2018-08-06 02:49:29,53] [info] Running with database db.url = jdbc:hsqldb:mem:f8707d42-af81-4939-8419-6121bc222e7d;shutdown=false;hsqldb.tx=mvcc
[2018-08-06 02:49:42,20] [info] Running migration RenameWorkflowOptionsInMetadata with a read batch size of 100000 and a write batch size of 100000
[2018-08-06 02:49:42,22] [info] [RenameWorkflowOptionsInMetadata] 100%
[2018-08-06 02:49:42,33] [info] Running with database db.url = jdbc:hsqldb:mem:790652a9-0e01-4c7f-9f24-522c9be37b6b;shutdown=false;hsqldb.tx=mvcc
[2018-08-06 02:49:42,96] [info] Slf4jLogger started
[2018-08-06 02:49:43,36] [info] Workflow heartbeat configuration:
{
  "cromwellId" : "cromid-10e8f79",
  "heartbeatInterval" : "2 minutes",
  "ttl" : "10 minutes",
  "writeBatchSize" : 10000,
  "writeThreshold" : 10000
}
[2018-08-06 02:49:43,42] [info] Metadata summary refreshing every 2 seconds.
[2018-08-06 02:49:43,50] [info] KvWriteActor configured to flush with batch size 200 and process rate 5 seconds.
[2018-08-06 02:49:43,50] [info] CallCacheWriteActor configured to flush with batch size 100 and process rate 3 seconds.
[2018-08-06 02:49:43,50] [info] WriteMetadataActor configured to flush with batch size 200 and process rate 5 seconds.
[2018-08-06 02:49:44,64] [info] JobExecutionTokenDispenser - Distribution rate: 50 per 1 seconds.
[2018-08-06 02:49:44,65] [info] SingleWorkflowRunnerActor: Version 34
[2018-08-06 02:49:44,66] [info] SingleWorkflowRunnerActor: Submitting workflow
[2018-08-06 02:49:44,75] [info] Unspecified type (Unspecified version) workflow 7954aa28-b717-48fb-8d91-58fc6a7c4547 submitted
[2018-08-06 02:49:44,82] [info] SingleWorkflowRunnerActor: Workflow submitted 7954aa28-b717-48fb-8d91-58fc6a7c4547
[2018-08-06 02:49:44,83] [info] 1 new workflows fetched
[2018-08-06 02:49:44,83] [info] WorkflowManagerActor Starting workflow 7954aa28-b717-48fb-8d91-58fc6a7c4547
[2018-08-06 02:49:44,84] [warn] SingleWorkflowRunnerActor: received unexpected message: Done in state RunningSwraData
[2018-08-06 02:49:44,85] [warn] Couldn't find a suitable DSN, defaulting to a Noop one.
[2018-08-06 02:49:44,86] [info] Using noop to send events.
[2018-08-06 02:49:44,88] [info] WorkflowManagerActor Successfully started WorkflowActor-7954aa28-b717-48fb-8d91-58fc6a7c4547
[2018-08-06 02:49:44,88] [info] Retrieved 1 workflows from the WorkflowStoreActor
[2018-08-06 02:49:44,88] [info] WorkflowStoreHeartbeatWriteActor configured to flush with batch size 10000 and process rate 2 minutes.
[2018-08-06 02:49:44,93] [info] MaterializeWorkflowDescriptorActor [7954aa28]: Parsing workflow as WDL draft-2
[2018-08-06 02:49:45,73] [info] MaterializeWorkflowDescriptorActor [7954aa28]: Call-to-Backend assignments: myWorkflow.myTask -> Local
[2018-08-06 02:49:47,22] [info] WorkflowExecutionActor-7954aa28-b717-48fb-8d91-58fc6a7c4547 [7954aa28]: Starting myWorkflow.myTask
[2018-08-06 02:49:48,78] [info] BackgroundConfigAsyncJobExecutionActor [7954aa28myWorkflow.myTask:NA:1]: echo "hello world"
[2018-08-06 02:49:48,87] [info] BackgroundConfigAsyncJobExecutionActor [7954aa28myWorkflow.myTask:NA:1]: executing: /bin/bash /opt/project/cromwell/cromwell-executions/myWorkflow/7954aa28-b717-48fb-8d91-58fc6a7c4547/call-myTask/execution/script
[2018-08-06 02:49:53,55] [info] BackgroundConfigAsyncJobExecutionActor [7954aa28myWorkflow.myTask:NA:1]: job id: 21769
[2018-08-06 02:49:53,56] [info] BackgroundConfigAsyncJobExecutionActor [7954aa28myWorkflow.myTask:NA:1]: Status change from - to Done
[2018-08-06 02:49:55,43] [info] WorkflowExecutionActor-7954aa28-b717-48fb-8d91-58fc6a7c4547 [7954aa28]: Workflow myWorkflow complete. Final Outputs:
{
  "myWorkflow.myTask.out": "hello world"
}
[2018-08-06 02:49:55,48] [info] WorkflowManagerActor WorkflowActor-7954aa28-b717-48fb-8d91-58fc6a7c4547 is in a terminal state: WorkflowSucceededState
[2018-08-06 02:49:58,77] [info] SingleWorkflowRunnerActor workflow finished with status 'Succeeded'.
{
  "outputs": {
    "myWorkflow.myTask.out": "hello world"
  },
  "id": "7954aa28-b717-48fb-8d91-58fc6a7c4547"
}
[2018-08-06 02:50:03,60] [info] Workflow polling stopped
[2018-08-06 02:50:03,61] [info] Shutting down WorkflowStoreActor - Timeout = 5 seconds
[2018-08-06 02:50:03,62] [info] Shutting down WorkflowLogCopyRouter - Timeout = 5 seconds
[2018-08-06 02:50:03,63] [info] Aborting all running workflows.
[2018-08-06 02:50:03,63] [info] Shutting down JobExecutionTokenDispenser - Timeout = 5 seconds
[2018-08-06 02:50:03,63] [info] JobExecutionTokenDispenser stopped
[2018-08-06 02:50:03,63] [info] WorkflowStoreActor stopped
[2018-08-06 02:50:03,64] [info] WorkflowLogCopyRouter stopped
[2018-08-06 02:50:03,64] [info] Shutting down WorkflowManagerActor - Timeout = 3600 seconds
[2018-08-06 02:50:03,64] [info] WorkflowManagerActor All workflows finished
[2018-08-06 02:50:03,64] [info] WorkflowManagerActor stopped
[2018-08-06 02:50:03,64] [info] Connection pools shut down
[2018-08-06 02:50:03,65] [info] Shutting down SubWorkflowStoreActor - Timeout = 1800 seconds
[2018-08-06 02:50:03,65] [info] Shutting down JobStoreActor - Timeout = 1800 seconds
[2018-08-06 02:50:03,65] [info] SubWorkflowStoreActor stopped
[2018-08-06 02:50:03,65] [info] Shutting down CallCacheWriteActor - Timeout = 1800 seconds
[2018-08-06 02:50:03,65] [info] Shutting down ServiceRegistryActor - Timeout = 1800 seconds
[2018-08-06 02:50:03,65] [info] Shutting down DockerHashActor - Timeout = 1800 seconds
[2018-08-06 02:50:03,65] [info] CallCacheWriteActor Shutting down: 0 queued messages to process
[2018-08-06 02:50:03,65] [info] Shutting down IoProxy - Timeout = 1800 seconds
[2018-08-06 02:50:03,65] [info] KvWriteActor Shutting down: 0 queued messages to process
[2018-08-06 02:50:03,65] [info] JobStoreActor stopped
[2018-08-06 02:50:03,65] [info] CallCacheWriteActor stopped
[2018-08-06 02:50:03,65] [info] WriteMetadataActor Shutting down: 0 queued messages to process
[2018-08-06 02:50:03,65] [info] DockerHashActor stopped
[2018-08-06 02:50:03,65] [info] IoProxy stopped
[2018-08-06 02:50:03,66] [info] ServiceRegistryActor stopped
[2018-08-06 02:50:03,68] [info] Database closed
[2018-08-06 02:50:03,68] [info] Stream materializer shut down
[2018-08-06 02:50:03,72] [info] Automatic shutdown of the async connection
[2018-08-06 02:50:03,72] [info] Gracefully shutdown sentry threads.
[2018-08-06 02:50:03,72] [info] Shutdown finished.

