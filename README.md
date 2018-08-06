支持导出格式：txt和xlsx

导出大小：支持海量数据导出

导出分页：每10000条数据分为一页

导出结果：每条SQL对应一个导出文件，命名格式为：result_201808061408_0.xlsx.zip，自动压缩



导出命令例子：

python export_data.py -uincep_user -p123.com -H172.17.10.40 -P3306 -dtest -D./ -egbk -txlsx -f aaa.sql
python export_data.py -uincep_user -p123.com -H172.17.10.40 -P3306 -dtest -D./ -eutf-8 -ttxt -f aaa.sql


导出帮助命令：

python export_data.py -h



导出步骤：

1.将开发提供的select语句，写入到一个文件，文件名自定义即可，假如为：aaa.sql

vim -R aaa.sql

每条SQL必须以分号;结尾

```bash
SELECT id,mobile,TEXT,created_at FROM test_sms_log WHERE
created_at >= '2018-07-17 00:00:00' AND
created_at <= '2018-07-17 23:59:59' AND TEXT LIKE '%导出%';

SELECT id,mobile,TEXT,created_at FROM test_sms_log WHERE
created_at >= '2018-07-17 00:00:00' AND created_at <= '2018-07-18 23:59:59' AND TEXT LIKE '%企业%';


SELECT id,mobile,TEXT,created_at FROM test_sms_log WHERE created_at >= '2018-07-17 00:00:00' AND created_at <= '2018-07-25 23:59:59' AND TEXT LIKE '%你好%';
```



2.执行导出命令：

假如导出成：xlsx格式，编码：gbk，导出目录：/tmp/zhangsan

python export_data.py -uincep_user -p123.com -H172.17.10.40 -P3306 -dtest -D/tmp/zhangsan -egbk -txlsx -f aaa.sql
查看导出进度：
```bash
2018-08-06 14:08:56 - INFO - ### 提示 ###
2018-08-06 14:08:56 - INFO - 用户名：incep_user
2018-08-06 14:08:56 - INFO - 密码：123.com
2018-08-06 14:08:56 - INFO - 主机：172.17.10.40
2018-08-06 14:08:56 - INFO - 端口：3306
2018-08-06 14:08:56 - INFO - 库：test
2018-08-06 14:08:56 - INFO - 编码：gbk
2018-08-06 14:08:56 - INFO - 格式：xlsx
2018-08-06 14:08:56 - INFO - 读取SQL列表文件：aaa.sql
2018-08-06 14:08:56 - INFO -

2018-08-06 14:08:56 - INFO - 正在导出SQL：SELECT id,mobile,TEXT,created_at FROM sms_log WHERE
created_at >= '2018-07-17 00:00:00' AND
created_at <= '2018-07-17 23:59:59' AND TEXT LIKE '%客户%'
2018-08-06 14:08:56 - INFO - SQL导出记录总数：47147
2018-08-06 14:08:56 - INFO - SQL分页数量(page rows：10000)：5
2018-08-06 14:08:57 - INFO - 分页导出进度：1/5
2018-08-06 14:08:57 - INFO - 分页导出进度：2/5
2018-08-06 14:08:58 - INFO - 分页导出进度：3/5
2018-08-06 14:08:59 - INFO - 分页导出进度：4/5
2018-08-06 14:09:01 - INFO - 分页导出进度：5/5
2018-08-06 14:09:09 - INFO - 正在压缩文件：./result_201808061408_0.xlsx ---> ./result_201808061408_0.xlsx.zip
2018-08-06 14:09:09 - INFO - 删除源文件：./result_201808061408_0.xlsx
2018-08-06 14:09:09 - INFO - 耗时：12.55s
2018-08-06 14:09:09 - INFO -

2018-08-06 14:09:09 - INFO - 正在导出SQL：SELECT id,mobile,TEXT,created_at FROM sms_log WHERE
created_at >= '2018-07-17 00:00:00' AND created_at <= '2018-07-18 23:59:59' AND TEXT LIKE '%客户%'
2018-08-06 14:09:09 - INFO - SQL导出记录总数：47147
2018-08-06 14:09:09 - INFO - SQL分页数量(page rows：10000)：5
2018-08-06 14:09:10 - INFO - 分页导出进度：1/5
2018-08-06 14:09:10 - INFO - 分页导出进度：2/5
2018-08-06 14:09:11 - INFO - 分页导出进度：3/5
2018-08-06 14:09:12 - INFO - 分页导出进度：4/5
2018-08-06 14:09:14 - INFO - 分页导出进度：5/5
2018-08-06 14:09:22 - INFO - 正在压缩文件：./result_201808061408_1.xlsx ---> ./result_201808061408_1.xlsx.zip
2018-08-06 14:09:22 - INFO - 删除源文件：./result_201808061408_1.xlsx
2018-08-06 14:09:22 - INFO - 耗时：12.74s
2018-08-06 14:09:22 - INFO -

2018-08-06 14:09:22 - INFO - 正在导出SQL：SELECT id,mobile,TEXT,created_at FROM sms_log WHERE created_at >= '2018-07-17 00:00:00' AND created_at <= '2018-07-25 23:59:59' AND TEXT LIKE '%客户%'
2018-08-06 14:09:22 - INFO - SQL导出记录总数：47147
2018-08-06 14:09:22 - INFO - SQL分页数量(page rows：10000)：5
2018-08-06 14:09:23 - INFO - 分页导出进度：1/5
2018-08-06 14:09:23 - INFO - 分页导出进度：2/5
2018-08-06 14:09:24 - INFO - 分页导出进度：3/5
2018-08-06 14:09:26 - INFO - 分页导出进度：4/5
2018-08-06 14:09:27 - INFO - 分页导出进度：5/5
2018-08-06 14:09:35 - INFO - 正在压缩文件：./result_201808061408_2.xlsx ---> ./result_201808061408_2.xlsx.zip
2018-08-06 14:09:35 - INFO - 删除源文件：./result_201808061408_2.xlsx
2018-08-06 14:09:35 - INFO - 耗时：13.01s
```

