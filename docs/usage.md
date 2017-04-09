# Usage

## Quick start

To enable you application to use the Skeleton Library, just register the Skeleton's module during the AutoFac setup:

```csharp
builder.RegisterModule(new SkeletonModule(connectionString);
```

From now on, you can subscribe to the queue `my_queue` and consume messages of type `MyPayload` with a stardard Adesso consumer, with the business logic `MyBusinessLogic` by using the helper `Skeleton`:

```csharp
// FIXME
var skeleton = scope.Resolve<Skeleton>();
skeleton.Register<MyPayload, MyBusinessLogic<MyPayload>, AdessoConsumer>
    ("my_queue", Func<MyBusinessLogic>)
```

Implement `MyBusinessLogic` extending `IBusinessLogic<MyPayload>`:
 
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


