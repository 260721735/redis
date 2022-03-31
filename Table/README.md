# GetKeyByRedisClusterSlot
if you want use redLock with redis cluster,you can ues SlotTable to get key path.


```
for example,your redis cluster slot is
6816eefd5ecb094df2610127ba4ccdf536f8decf 127.0.0.1:10002@20002 master - 0 1648724135575 3 connected 10923-16383
2642e503c9c6b3027156ae63d7198689297c79e5 127.0.0.1:10000@20000 master - 0 1648724134000 1 connected 0-5460
d0d97a1c617c13f8e3dc2acd144389ceadfd3017 127.0.0.1:10001@20001 master - 0 1648724134768 2 connected 5461-10922
you can use key{SlotTable[10923]} key{SlotTable[0]} key{SlotTable[5461]} to Make your redlock keys truly distributed among the three masters
```
##how to use
```

import (
	"github.com/260721735/GetKeyByRedisClusterSlot/Table"
)

func main() {
	trueKey:="key{"+Table.SlotTable[10923]+"}"
	//for i:=range redisClients{
	//res,err:=redisClient[i].setNX(trueKey,radom)
	//if err!=nil{
	//do something
	//}
	//}
}
```