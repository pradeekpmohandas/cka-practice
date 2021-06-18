resource section in pod to mention cpu/memory range
######
CPU | MEMORY-ram | Disk space
mini request : 
CPU: .5  MEMORY: 256Mi 
minimum : 1m
1 = 100m (milli cpu)

######
namespace resource quota KIND: LimitRange
namespace default container limit KIND: ResourceQuota
Kind: ResourceQuota ==> max allowed resource in that ns
Kind: LimitRange ==> default limit values per pod, unless specified in resource template