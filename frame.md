# What is inside a Frame
```
------------------------------------------------------
| Tuple1 | Tuple 2 ..............................    |
| XXXXX .............................................|
| ... | endOf_tn | ... | endOf_t2 | endOf_t1| #Tuples|
------------------------------------------------------
```
Each offset is 4bytes.

# What is inside a Tuple
```
------------------------------------------------------
EndOf_f0| EndOf_f1 | ... | EndOf_fn | TupleContents |
EndOf_f0| EndOf_f1 | ... | EndOf_fn | TupleContents |
.....
------------------------------------------------------
```
The `field offset` is the relative offset from TupleStart

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

