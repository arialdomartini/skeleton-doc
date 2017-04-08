# Usage

## Quick start

To subscribe to the queue `my_queue` and consume messages of type `MyPayload` with a stardard Adesso consumer, with the business logic `MyBusinessLogic`, in an AutoFac powered application, just add the call:

```csharp
// FIXME
var skeleton = scope.Resolve<Skeleton>();
skeleton.Register<MyPayload, MyBusinessLogic<MyPayload>, AdessoConsumer>
    ("my_queue", Func<MyBusinessLogic>)
```
 Then, implement `MyBusinessLogic` extending `IBusinessLogic<MyPayload>`:
 
 ```csharp
 public class MyBusinessLogic : IBusinessLogic<MyPayload>
 {
   public IAcknowledgment(Payload paylod)
   {
     // Your business logic here
     return new Ack();
   }
 }
```


