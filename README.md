# CreateTaskSet with Load balancers

It looks like that Mix type of TaskSets (Normal + LB) in the single service causes all the TaskSets are coming up later after the first one in the sequence shows tendency to fail and remain such in STABILIZING and never goes about deploying tasks. It does not matter if you make taskset as primary or not.

Here are my test results  : 

https://github.com/git4example/CreateTaskSetWithLB

------------------------------------

Normal -- Represents TaskSets without Load balancer

LB -- Represents TaskSet with Load balancer


Normal -- > It works and reached STEADY_STATE

LB -- > It works and reached STEADY_STATE

LB - LB -- > Both works and reached STEADY_STATE

Normal - Normal -- > Both works and reached STEADY_STATE


Normal - LB -- > Normal works reached STEADY_STATE -- > LB remain stuck in STABILIZING

Normal (Primary) - LB -- > Normal works reached STEADY_STATE -- > LB remain stuck in STABILIZING
Normal - LB (Primary) -- > Normal works reached STEADY_STATE -- > LB remain stuck in STABILIZING

LB - Normal -- > LB works (however it remain in STABILIZING) -- > Normal remain stuck in STABILIZING



Normal - LB - Normal -- > Normal works reached STEADY_STATE -- > LB remain stuck in STABILIZING -- > Normal remain stuck in STABILIZING

LB - Normal - LB -- > LB works (however it remain in STABILIZING) -- > Normal remain stuck in STABILIZING -- > LB remain stuck in STABILIZING

------------------------------------