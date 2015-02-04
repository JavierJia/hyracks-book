# ICCContext
It has the information about the Cluster which was maintained in CC.
```Java
public interface ICCContext {
    public ClusterControllerInfo getClusterControllerInfo();

    public void getIPAddressNodeMap(Map<InetAddress, Set<String>> map) throws Exception;

    public ClusterTopology getClusterTopology();
}
```
Anonymously implemented in `ClusterControllerService`.

# IHyracksRootContext
It has the information about the computation nodes which maintained in NC .

```Java
public interface IHyracksRootContext {
    public IIOManager getIOManager();

    public Map<String, NodeControllerInfo> getNodeControllerInfos() throws Exception;
}
```
Implemented in `NodeControllerService`

# IHyracksJobletContext
Everything about the Job that runs on NC.
```Java
public interface IHyracksJobletContext extends IWorkspaceFileFactory, IDeallocatableRegistry {
    public INCApplicationContext getApplicationContext();

    public JobId getJobId();

    public ICounterContext getCounterContext();

    public Object getGlobalJobData();

    public Class<?> loadClass(String className);

    public ClassLoader getClassLoader();
}
```

## Joblet
Joblet implements the `IHyracksJobletContext`. 

# IHyracksCommonContext
It mainly asks to implement the memory management related context. In other word, it is 
just the memory manager.

```Java
public interface IHyracksCommonContext {
    public int getFrameSize();

    public IIOManager getIOManager();

    public ByteBuffer allocateFrame() throws HyracksDataException;

    public ByteBuffer reallocateFrame(ByteBuffer bytes, int newSize) throws HyracksDataException;

    public void deallocateFrames(int frameCount);
}
```

## IHyracksTaskContext
It maintains the Task information.

```Java
public interface IHyracksTaskContext extends IHyracksCommonContext, IWorkspaceFileFactory, IDeallocatableRegistry,
        IOperatorEnvironment {
    public IHyracksJobletContext getJobletContext();

    public TaskAttemptId getTaskAttemptId();

    public ICounterContext getCounterContext();

    public IDatasetPartitionManager getDatasetPartitionManager();

    public void sendApplicationMessageToCC(byte[] message, DeploymentId deploymendId, String nodeId) throws Exception;
}
```

### Task
The implementation of the `IHyracksTaskContext`


### TestTaskContext
For tests supports

## DatasetClientContext
## DefaultHyracksCommonContext

# Application ? 
An Application has several Jobs, A Job has several Tasks. 
