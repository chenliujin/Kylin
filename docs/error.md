# Overwriting conflict /model_desc/price_distribute.json, expect old TS 0, but it is 1540380886475

```
# hbase shell
hbase > list
hbase > get "kylin_metadata", "/model_desc/price_distribute.json"
hbase > deleteall "kylin_metadata", "/model_desc/price_distribute.json"
```
