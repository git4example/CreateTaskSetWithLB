# CreateTaskSet with Load balancers

Normal -- > It works and reached STEADY_STATE
LB -- > It works and reached STEADY_STATE
LB - LB -- > Both works and reached STEADY_STATE
Normal - Normal -- > Both works and reached STEADY_STATE


Normal - LB -- > Normal works reached STEADY_STATE -- > LB remain stuck in STABILIZING
LB - Normal -- > LB works (however it remain in STABILIZING) -- > Normal remain stuck in STABILIZING



Normal - LB - Normal -- > Normal works reached STEADY_STATE -- > LB remain stuck in STABILIZING
LB - Normal - LB -- > LB works (however it remain in STABILIZING) -- > Normal remain stuck in STABILIZING