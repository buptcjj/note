# note
2016/3  
平面图结果  
1  : 92.3:89.32:90.78  
1L : 92.89:89.61:91.22   
2  : 93.25:90.78:92.00  

2016/10/18  
测试pas14+open中train的oneendingpoint的图的覆盖率  
project 19455/32389 = 0.6007  
oneendpoint 31507/32389 = 0.9728 , edge : 0.9607  
onecutendpoint 31507/32389 = 1 , edge : 0.9987

2016/10/27  
调试1ep在pas14+open中的decode结果
edge coverage 690072/691056 = 99.86%  
cut0 31507 / 32389 = 97.28%  
cut1 792 / 32389 = 2.45%  
cut2 80 / 32389 = 0.25%  
cut3+ 10 / 32389 = 0.03%  

2016/10/28  
1ep在pas14+open中一阶学习结果  
1order_UP：UR：UF = 92.21:90.06:91.40  

2016/11/1  
完成1ec的二阶形式，其他不变，在int_span_label中搜索zuodianheyoudiuan左点和右点
trick：和1plannar不同，有可能存在r-rsp的边但是是cross边因此造成无法完全decode  
solution：int_span_label搜索时增加考虑 int_span_label + int_span_nolabel,让右端点的cross边可被decode  

