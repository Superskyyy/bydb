
![696B332D-8FB0-4E73-A729-16B40578A642](https://github.com/Superskyyy/bydb/assets/26076517/5e85d08d-eb8a-4dda-91d1-379469de7504)
![CD950360-CBDF-40EA-89BF-8EC63B5FE1A9](https://github.com/Superskyyy/bydb/assets/26076517/f66ec43c-e5cf-4392-baa1-83424030558b)
```
Stream expectedStream = Stream.create(group, task_stream)
        .setEntityRelativeTags("taskId", "taskName")
        .addTagFamily(TagFamilySpec.create("searchable")
                .addTagSpec(TagFamilySpec.TagSpec.newStringTag("taskId"))
                .addTagSpec(TagFamilySpec.TagSpec.newStringTag("taskName"))
                .addTagSpec(TagFamilySpec.TagSpec.newStringTag("taskType"))
                .addTagSpec(TagFamilySpec.TagSpec.newStringTag("actorId"))
                .addTagSpec(TagFamilySpec.TagSpec.newStringTag("jobId"))
                .addTagSpec(TagFamilySpec.TagSpec.newStringTag("nodeId"))
                .addTagSpec(TagFamilySpec.TagSpec.newIntTag("numCPU"))
                .addTagSpec(TagFamilySpec.TagSpec.newIntTag("numGPU"))
                .addTagSpec(TagFamilySpec.TagSpec.newIntTag("numNPU"))
                .addTagSpec(TagFamilySpec.TagSpec.newIntTag("startTime"))
                .addTagSpec(TagFamilySpec.TagSpec.newIntTag("endTime"))
                .build())
        .build();
client.define(expectedStream);





String taskId ='0006a2509d0c53fbb4e8a14a8c1e9b8c82cf8d3203000000'; 
String taskName = 'Map(ActorB2)'; 
String taskType = 'ACTOR_TASK'; 
String actorId = 'b4e8a14a8c1e9b8c82cf8d3203000000'; 
String jobId = '03000000';
String nodeId = 'b8efa2ac47e492b258187d6e3be3a4fa45481e323d71a991a2cbf0bd'; 
int numCPU = 0; 
int numGPU = 0; 
int numNPU = 0; 
int startTime = 1714120325812; 
int endTime = 1714120325814;


StreamWrite streamWrite = client.createStreamWrite(group, task_stream, randomUUID().toString(), Instant.now().toEpochMilli());
streamWrite.tag("taskId", Value.stringTagValue(task.getTaskId()));
streamWrite.tag("taskName", Value.stringTagValue(task.getTaskName()));
streamWrite.tag("taskType", Value.stringTagValue(task.getTaskType()));
streamWrite.tag("actorId", Value.stringTagValue(task.getActorId()));
streamWrite.tag("jobId", Value.stringTagValue(task.getJobId()));
streamWrite.tag("nodeId", Value.stringTagValue(task.getNodeId()));
streamWrite.tag("numCPU", Value.longTagValue(task.getNumCPU()));
streamWrite.tag("numGPU", Value.longTagValue(task.getNumGPU()));
streamWrite.tag("numNPU", Value.longTagValue(task.getNumNPU()));
streamWrite.tag("startTime", Value.longTagValue(task.getStartTime()));
streamWrite.tag("endTime", Value.longTagValue(task.getEndTime()));
CompletableFuture<Void> future = processor.add(streamWrite);
			
```		
			
StreamQuery task_query = new StreamQuery(group, task_stream, ImmutableSet.of("taskId", "taskType", "jobId", "numCPU", "startTime", "endTime"));
task_query.and(PairQueryCondition.StringQueryCondition.eq("jobId", jobId));
task_query.and(PairQueryCondition.StringQueryCondition.eq("taskType", "NORMAL_TASK"));
task_query.setLimit(2000);
StreamQueryResponse task_resp = client.query(task_query);
