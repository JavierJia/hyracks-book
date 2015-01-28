# Frame is the basic memory components 

Pain in the ass

```Java
if (!appender.append(fta1, tStart, tEnd)) {
     FrameUtils.flushFrame(outFrame, writer);
     appender.reset(outFrame, true);
     if (!appender.append(fta1, tStart, tEnd)) {
         throw new HyracksDataException("Record size (" + (tEnd - tStart) + ") larger than frame size ("
                 + appender.getBuffer().capacity() + ")");
     }
 }
```
# IFrameWriter
In `IOperatorPushable` it has one function to return the `FrameWriter`. However,
basically every `Pushable` operator just return itself. The others just `sink`
operators which do not need writers.
