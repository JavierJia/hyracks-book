# ExternalSortOperator

It calls ExternalSortRunGenerator to generate the runs.
Then the ExternalSortRunMerger to merge the runs into the frame ? 

```Java
    @Override
    public void contributeActivities(IActivityGraphBuilder builder) {
        SortActivity sa = new SortActivity(new ActivityId(odId, SORT_ACTIVITY_ID));
        MergeActivity ma = new MergeActivity(new ActivityId(odId, MERGE_ACTIVITY_ID));

        builder.addActivity(this, sa);
        builder.addSourceEdge(0, sa, 0);

        builder.addActivity(this, ma);
        builder.addTargetEdge(0, ma, 0);

        builder.addBlockingEdge(sa, ma);
    }
```

How to notify if there need more iterations? 

`ExternalSortRunGenerator` flush to `RunFileWriter`

Is it good to add the codecec for those `RunFileWriter`s ? 
Based on the Hadoop experience it is a good option to compress the files.

`Sort` function only sort the `Pointer`

Why not write a `Pointer` class ?
