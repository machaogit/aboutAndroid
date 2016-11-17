##Android性能优化

+ 防止Overdraw,ListView的getView中判断是否获取到对应的Bitmap，获取到之后，把ImageView的Background设置为Transparent

+ 移除Window默认的Background和布局文件中非必须的Background，按需显示背景图片

+ 使用SparseArray或者ArrayMap代替HashMap存数据节省内存,SparseArray只能存储key为int的数据，数据量不大，最好在千级以内
，如果key类型为其它的类型，则使用ArrayMap。
( SparseArray：private int[] mKeys;
    		 private Object[] mValues;)

+ 可以通过下面的代码来获取手机的当前充电状态

		IntentFilter filter = new 			IntentFilter(Intent.ACTION_BATTERY_CHANGED);
		Intent batteryStatus = 	this.registerReceiver(null,filter);
		int chargePlug =batteryStatus.getIntExtra(BatteryManager.EXTRA_PLUGGED, -1);
		boolean acCharge = (chargePlug == 	BatteryManager.BATTERY_PLUGGED_AC);
		if (acCharge) {
    		Log.v(LOG_TAG,“The phone is charging!”);
		}
+ 加入JobScheduler,可以让后台任务在特定的时间满足特定的条件下执行

+ 网络请求的优化 <1 何时发起网络请求（通过JobScheduler，把网络请求的任务延迟到手机网络切换到WiFi，手机处于充电状态下再执行）.<2 
如何传递网络数据（预取和压缩）

+ 创建对象池防止短时间内创建过多对象，从而触发GC



