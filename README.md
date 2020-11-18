# CreateTaskSet with Load balancers

This is to test Mix type of TaskSets (Normal + LB) in the single service causes all the TaskSets are coming up later after the first one in the sequence shows tendency to fail and remain such in STABILIZING and never goes about deploying tasks. It does not matter if you make taskset as primary or not.

This is because this is currently not supported to have mix type of TaskSets are not supported under single ECS service. By combining the two types, ECS workflow does not behave correctly, as evidenced in these tests.

Here are my test results  : 

https://github.com/git4example/CreateTaskSetWithLB

------------------------------------

Legends Used below:
```
Normal --> Represents TaskSets without Load balancer
LB -- > Represents TaskSet with Load balancer
```

## CreateTaskSet with / without Load balancers
Following 10 test was created under their own respective services to check behavior of the single vs. multiple TaskSets running under same service.

Here are my test results from 10 different combination of the test I run around this :

https://github.com/git4example/CreateTaskSetWithLB

## Single TaskSets :
Normal -- > It works and reached STEADY_STATE

LB -- > It works and reached STEADY_STATE

## Dual TaskSets of same types:
LB + LB -- > Both works and reached STEADY_STATE

Normal + Normal -- > Both works and reached STEADY_STATE

## Dual TaskSets of different types:
Normal + LB -- > Normal works reached STEADY_STATE -- > LB remain stuck in STABILIZING

LB + Normal -- > LB works (however it remain in STABILIZING) -- > Normal remain stuck in STABILIZING

## Dual TaskSets of different types with marking one of it as Primary :
Normal (Primary) + LB -- > Normal works reached STEADY_STATE -- > LB remain stuck in STABILIZING

Normal + LB (Primary) -- > Normal works reached STEADY_STATE -- > LB remain stuck in STABILIZING

## Combination of three TaskSets :
Normal + LB + Normal -- > Normal works reached STEADY_STATE -- > LB remain stuck in STABILIZING -- > Normal remain stuck in STABILIZING

LB + Normal + LB -- > LB works (however it remain in STABILIZING) -- > Normal remain stuck in STABILIZING -- > LB remain stuck in STABILIZING