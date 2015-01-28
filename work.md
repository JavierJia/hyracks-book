# Relation between `Job`,`Work`,`Joblet`

All these are of NC class. User should see the `JobSpecification` only.

Work --> StartTasksWork create the Joblet,
Joblet has a Task,
Task has the Operator, which create by `IActivity.createPushRuntime`

IActivity creates the IOperatorNodePushable by `IActivity.createPushRuntime`

IOperatorDescriptor creates the IActivity via `IActivity.contributeActivities`

The `IActivity.contributeActivities` will be called in the `createActivityClusterGraphGenerator`
which is build the `IActivityClusterGraphGenerator`.

Work is the wrapper of the command between master and slave. 

The `StartTasksWork` will send the `JobGraph` to slaves. Slaves will create the `Joblet` based on the 
activity analysis of the graph. It will create one task for each of the operation. 

