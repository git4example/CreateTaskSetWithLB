# CreateTaskSet with Load balancers
Normal -- Represents TaskSets without Load balancer

LB -- Represents TaskSet with Load balancer

------------------------------------
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