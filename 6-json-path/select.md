json path is query language to parse json
accessing dictionary dot operator
$.car.ferrari

accessing list/array []
[1]

query
?()
@ for each
?( @>40)  
$[?(@>40 )]  --items greater than 40
@>, @==, @!=, @in[12,121,1], @nin[24,32,12]


List queries
$[0,10] #get 0th and 10th item
$[0:10] #get all items from 0 to 10
$[0:10:2] #get 0,2,4,6,8 skip by number 2
$[-1:0] #get last element
