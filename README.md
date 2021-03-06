# Wunion.DataAdapter.NetCore
巽翎君的开源代码库

轻量级的.NET跨平台数据库查询组件库.<br />
Lightweight .NET cross-platform database query component library.


<strong>兼容性(Compatibility) :</strong><br />
.NET Framework >= 4.6.1 <br />
.NET Core >= 2.0 <br />


<strong>数据库支持 (Supported databases)：</strong><br/>
Microsoft SQL Server <br />
PostgreSQL <br />
MySQL <br />
SQLite3


更多信息请阅读 Documents 目录下的开发人员文档 <br />
For more information, please read the developers documentation in the "Documents" directory.


右键点击项目打开“管理NuGet程序包”，并搜索关键字 “Wunion.DataAdapter.NetCore” 安装相应的包，您也可以自行编译nuget包发布到自己的Nuget服务器上。<br />
Right-click on your project open the NuGet Package Manager, Search keyword: "Wunion.DataAdapter.NetCore" for installation. And you can also compile and publish your own NuGet package to your own NuGet server



作者将会随时更新并改进组件库，同时欢迎各路开发人员加入该项目的开发及完善工作。
The author would update and improve the component library at any time, and welcome many developers to join the project development and improvement work.

<strong>BatchCommander类的使用 (Use of the BatchCommander class)：</strong><br />
命名空间 (Namespace) ：Wunion.DataAdapter.Kernel <br />
示例：<br />
int result = 0;<br />
using (BatchCommander commander = BatchCommander(dataEngine))<br />
{<br />
&nbsp;&nbsp;&nbsp;&nbsp;DbCommandBuilder cb = new DbCommandBuilder();<br />
&nbsp;&nbsp;&nbsp;&nbsp;cb.Insert(......).Values(......);<br />
&nbsp;&nbsp;&nbsp;&nbsp;result = commander.ExecuteNonQuery(cb);<br />
&nbsp;&nbsp;&nbsp;&nbsp;......   <br />
&nbsp;&nbsp;&nbsp;&nbsp;cb.Update(...).Set(......).Where(......);<br />
&nbsp;&nbsp;&nbsp;&nbsp;result = commander.ExecuteNonQuery(cb);<br />
&nbsp;&nbsp;&nbsp;&nbsp;......<br />
}


<strong>DataBatchProccesser类的使用(Use of the DataBatchProccesser class)：</strong><br />
命名空间 (Namespace) ：Wunion.DataAdapter.EntityUtils <br />
示例：<br />
using (DataBatchProcessor p = DbContext.BatchProcess())<br />
{<br />
&nbsp;&nbsp;&nbsp;&nbsp;int result = p.Table&lt;MyTestContext&gt;().Update(entity, p => new object[] { p.Id == 2 });<br />
&nbsp;&nbsp;&nbsp;&nbsp;if (result < 1)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;result = p.Table&lt;MyTestContext&gt;().Add(entity);<br />
&nbsp;&nbsp;&nbsp;&nbsp;...<br />
}
