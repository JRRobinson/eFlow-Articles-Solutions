# **eFlow 5 - Collections from Recognition to Reject - Unicode surrogate characters** #

## **Question / Description** ##

I see that sometimes - randomly - collections go from Recognition to Reject. In the log I can see the error below. When dragging them back to Recognize everything is properly processed without error (and even without restarting the station). Does anyone saw this before / know the cause and solution? eFlow 5.0.3.6.

2014-06-03 16:30:44,992 [15] ERROR Source App: efProcessShell.exe, Message: System.AggregateException: One or more errors occurred. ---> System.ArgumentException: Unicode surrogate characters must be written out as pairs together in the same call, not individually. Consider passing in a character array instead.
   at System.IO.BinaryWriter.Write(Char ch)
   at System.Runtime.Serialization.Formatters.Binary.__BinaryWriter.WriteValue(InternalPrimitiveTypeE code, Object value)
   at System.Runtime.Serialization.Formatters.Binary.__BinaryWriter.WriteMember(NameInfo memberNameInfo, NameInfo typeNameInfo, Object value)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.WriteKnownValueClass(NameInfo memberNameInfo, NameInfo typeNameInfo, Object data)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.WriteMembers(NameInfo memberNameInfo, NameInfo memberTypeNameInfo, Object memberData, WriteObjectInfo objectInfo, NameInfo typeNameInfo, WriteObjectInfo memberObjectInfo)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.WriteMemberSetup(WriteObjectInfo objectInfo, NameInfo memberNameInfo, NameInfo typeNameInfo, String memberName, Type memberType, Object memberData, WriteObjectInfo memberObjectInfo)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.Write(WriteObjectInfo objectInfo, NameInfo memberNameInfo, NameInfo typeNameInfo, String[] memberNames, Type[] memberTypes, Object[] memberData, WriteObjectInfo[] memberObjectInfos)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.Write(WriteObjectInfo objectInfo, NameInfo memberNameInfo, NameInfo typeNameInfo)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.Serialize(Object graph, Header[] inHeaders, __BinaryWriter serWriter, Boolean fCheck)
   at System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize(Stream serializationStream, Object graph, Header[] headers, Boolean fCheck)
   at TiS.Recognition.RecognitionWorkflowStationProcessor.<>c__DisplayClassa.<Drd2CollectionInternal>b__8()
   at System.Threading.Tasks.Task.InnerInvoke()
   at System.Threading.Tasks.Task.Execute()
   --- End of inner exception stack trace ---
   at System.Threading.Tasks.Task.WaitAll(Task[] tasks, Int32 millisecondsTimeout, CancellationToken cancellationToken)
   at System.Threading.Tasks.Task.WaitAll(Task[] tasks, Int32 millisecondsTimeout)
   at System.Threading.Tasks.Task.WaitAll(Task[] tasks)
   at TiS.Recognition.RecognitionWorkflowStationProcessor.Drd2CollectionInternal(ITisCollectionData collectionData, IDocumentRecognition result)
   at TiS.Recognition.RecognitionWorkflowStationProcessor.Process(ITisCollectionData collectionData)
---> (Inner Exception #0) System.ArgumentException: Unicode surrogate characters must be written out as pairs together in the same call, not individually. Consider passing in a character array instead.
   at System.IO.BinaryWriter.Write(Char ch)
   at System.Runtime.Serialization.Formatters.Binary.__BinaryWriter.WriteValue(InternalPrimitiveTypeE code, Object value)
   at System.Runtime.Serialization.Formatters.Binary.__BinaryWriter.WriteMember(NameInfo memberNameInfo, NameInfo typeNameInfo, Object value)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.WriteKnownValueClass(NameInfo memberNameInfo, NameInfo typeNameInfo, Object data)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.WriteMembers(NameInfo memberNameInfo, NameInfo memberTypeNameInfo, Object memberData, WriteObjectInfo objectInfo, NameInfo typeNameInfo, WriteObjectInfo memberObjectInfo)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.WriteMemberSetup(WriteObjectInfo objectInfo, NameInfo memberNameInfo, NameInfo typeNameInfo, String memberName, Type memberType, Object memberData, WriteObjectInfo memberObjectInfo)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.Write(WriteObjectInfo objectInfo, NameInfo memberNameInfo, NameInfo typeNameInfo, String[] memberNames, Type[] memberTypes, Object[] memberData, WriteObjectInfo[] memberObjectInfos)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.Write(WriteObjectInfo objectInfo, NameInfo memberNameInfo, NameInfo typeNameInfo)
   at System.Runtime.Serialization.Formatters.Binary.ObjectWriter.Serialize(Object graph, Header[] inHeaders, __BinaryWriter serWriter, Boolean fCheck)
   at System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize(Stream serializationStream, Object graph, Header[] headers, Boolean fCheck)
   at TiS.Recognition.RecognitionWorkflowStationProcessor.<>c__DisplayClassa.<Drd2CollectionInternal>b__8()
   at System.Threading.Tasks.Task.InnerInvoke()
   at System.Threading.Tasks.Task.Execute()<---




## **Answer / Solution** ##

I dont have a solution, but I have seen this error before and even reported it to salesforce.  I got the answer that it has been spotted before but there is not solved yet

I had the same behaviour, if I remove the collections from reject back to Recognition everything gets processed correctly and there are no further errors.

