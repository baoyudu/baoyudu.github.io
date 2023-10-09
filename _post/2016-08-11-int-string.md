---
layout:     post
title:      " Android学习笔记－－将int数据以字符串形式输出"
subtitle:   " "
tags:
    - Programming
    - 
    - 
---


>最近一直在学习Android开发，还是比较基础的阶段，需要做一做笔记，除了代码中注释记录，就写在这里好了。

我想要在点击ListView列表项时弹出Toast item项的“id”（第几项）

```
public class MainActivity extends Activity implements OnItemClickListener//接口方式设置监听器
{

	@Override
	public void onItemClick(AdapterView<?> p1, View p2, int p3, long p4)
	{
		
		Toast.makeText(MainActivity.this,"this is " + p3,Toast.LENGTH_SHORT).show();
	}

	private ListView lv;
	private ArrayAdapter aa;
    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
     /*
     *ArrayAdapter适配ListView
     */
		lv = (ListView) findViewById(R.id.mainListView);
		String[] str = {"i111111111","i2222222222","i33333333","i4444444","i555555555"};
		aa = new ArrayAdapter(this,android.R.layout.simple_list_item_1,str);
		lv.setAdapter(aa);
		lv.setOnItemClickListener(this);//指定监听器
    }
}
```
这样运行后 程序发生了fc
我注意到 p3这个参数是int类型 而Toast要输出text
可是怎么办呢
误打误撞
将这行改成这样
`Toast.makeText(MainActivity.this,"" + p3,Toast.LENGTH_SHORT).show();`

也就是，在int数据前 加了一个空的字符串
成功的运行 达到了我想要的结果
我想 也许是  __""__  将p3转化为了字符串 （或者说 把它添加进了字符串中）
###### 希望能帮忙解释一下 Java相关部分基础学的实在一般
