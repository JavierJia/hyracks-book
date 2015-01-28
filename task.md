# Hyracks Task
Locate in `hyracks-control-nc` package

Who allocates Frame ? Task . Then it needs to take care of the Multiple buffer ? 

# hyracks.control.nc.Task.

Read from the `collectors`, and call the `operator` to process the frame by `nextFrame`.
the `
```Java
   public void setTaskRuntime(IPartitionCollector[] collectors, IOperatorNodePushable operator) {
        this.collectors = collectors;
        this.operator = operator;
    }
```

get IFrameReader from channel, the channel will read the available frames from the connectors. 
