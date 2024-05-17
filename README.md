```
panic: not invoked

goroutine 492 [running]:
github.com/apache/skywalking-banyandb/pkg/query/logical.bypassList.ToSlice(...)
	/root/skywalking-banyandb-0.6.0/pkg/query/logical/index_filter.go:721
github.com/apache/skywalking-banyandb/banyand/stream.(*elementIndex).Search(0x400000d0f8, {0x400d922f00?, 0x1?}, {0x4000d02c28, 0x1, 0x1?}, {0x15840e8, 0x4000d02bf0})
	/root/skywalking-banyandb-0.6.0/banyand/stream/index.go:82 +0x114
github.com/apache/skywalking-banyandb/banyand/stream.(*stream).Filter(0x40015af880, {0x158e830, 0x400d9230b0}, {{0x400d7253f8, 0x12}, 0x400d9163f8, {0x400d926420, 0x1, 0x1}, {0x15840e8, ...}, ...})
	/root/skywalking-banyandb-0.6.0/banyand/stream/query.go:390 +0x538
github.com/apache/skywalking-banyandb/pkg/query/logical/stream.(*localIndexScan).Execute(0x400d9163c0, {0x158e830, 0x400d9230b0})
	/root/skywalking-banyandb-0.6.0/pkg/query/logical/stream/stream_plan_indexscan_local.go:96 +0x38c
github.com/apache/skywalking-banyandb/pkg/query/logical/stream.(*tagFilterPlan).Execute(0x400d923020, {0x158e830?, 0x400d9230b0?})
	/root/skywalking-banyandb-0.6.0/pkg/query/logical/stream/stream_plan_tag_filter.go:151 +0xac
github.com/apache/skywalking-banyandb/pkg/query/logical/stream.(*offset).Execute(0x400d90f210, {0x158e830?, 0x400d9230b0?})
	/root/skywalking-banyandb-0.6.0/pkg/query/logical/stream/stream_analyzer.go:164 +0xac
github.com/apache/skywalking-banyandb/pkg/query/logical/stream.(*limit).Execute(0x400d90f220, {0x158e830?, 0x400d9230b0?})
	/root/skywalking-banyandb-0.6.0/pkg/query/logical/stream/stream_analyzer.go:111 +0xac
github.com/apache/skywalking-banyandb/banyand/query.(*streamQueryProcessor).Rev(0x400072dc08, {{0x10805e0, 0x400ca5e480}, {0x10f5cdd, 0x5}, 0x17d03df28a0c9bcc, 0x0})
	/root/skywalking-banyandb-0.6.0/banyand/query/processor.go:108 +0x844
github.com/apache/skywalking-banyandb/pkg/bus.(*Bus).Subscribe.func1({0x1579800, 0x400072dc08}, 0x4000c30cc0)
	/root/skywalking-banyandb-0.6.0/pkg/bus/bus.go:274 +0x9c
created by github.com/apache/skywalking-banyandb/pkg/bus.(*Bus).Subscribe in goroutine 1
	/root/skywalking-banyandb-0.6.0/pkg/bus/bus.go:270 +0x238
```

![image](https://github.com/Superskyyy/bydb/assets/26076517/1624f99e-f10c-4381-af26-48d1fabf7b90)
 
![image](https://github.com/Superskyyy/bydb/assets/26076517/f719749d-0fd0-4b30-8054-ec84bec26ae8)
