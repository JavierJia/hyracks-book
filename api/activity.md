# Dataflow

## ActivityID
What is `ActivityID` ? 

## IActivity

`Activity` is the graph concept which is used to construct the dataflow graph.
It will create the `IOperatorNodePushable` for the computation.

```Java
public interface IActivity extends Serializable {
    public ActivityId getActivityId();

    public IOperatorNodePushable createPushRuntime(IHyracksTaskContext ctx,
            IRecordDescriptorProvider recordDescProvider, int partition, int nPartitions) throws HyracksDataException;
}
```

## `IOperatorNodePushable`
```Java
public interface IOperatorNodePushable {
    public void initialize() throws HyracksDataException;

    public void deinitialize() throws HyracksDataException;

    public int getInputArity();

    public void setOutputFrameWriter(int index, IFrameWriter writer, RecordDescriptor recordDesc)
            throws HyracksDataException;

    public IFrameWriter getInputFrameWriter(int index);

    public String getDisplayName();
}
```
What's the purpose of `getInputFrameWriter` ? Should it just need a reader than a writer ? 
