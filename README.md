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

2016/11/2  
注意二阶的longlong  
二阶结果 UP:UR:UF = 92.4:91.8:92.1  

2016/11/11  
增加1阶feature  
Psubcat，Psubcat+Cword，Csubcat，Csubcat+Pword  
P-lca's FPOSPath+Cword ,lca-C's FPOSPath+Pword   
P_1word,P1word,C_1word,C1word  
whether P connect C in tree P-C : 1 C-P : -1  
P_1wPpCp,P_1pPwCp,P_1pPpCw , same as PP1C,PC_1C,PCC1  
UP:UR:UF = 92.57:91.22:91.89  

2016/11/12  
增加1阶feature  
define leftmost,rightmost word of C's subtree as lw,rw  
lwword,lwtag,lwword+lwtag , same as rw,lw-1,rw+1  
UP:UR:UF = 92.76：91.23:91.99  
2阶结果  
UP:UR:UF = 92.67:91.97:92.32

2016/11/17  
修改bug，之前数据都是错的，因为先把dev预decode了一遍，所以recall会虚假上升，precious几乎不变  
1ec 少特征的1阶： 92.17:90.59:91.37  
1ec 多特征的1阶： 92.72:90.96:91.83  
1ec 少特征的2阶： 92.39:91.68:92.04  
1ec 多特征的2阶： 92.69:92.01:92.35  
1阶原始还行，多特征的降得比较多，二阶基本还行，与原先持平，没有想象中降得那么多  

2016/11/25
增加了一阶特征的label，高阶还是只有方向  
1ec_1L more  U 93.08:90.87:91.96 L 91.96:89.77:90.85  
1ec_2L less  U 92.52:91.64:92.08 L 91.13:90.27:90.70  
1ec_2L more  U 92.95:91.84:92.39 L 91.71:90.62:91.16   
2016/12/12  
修改了更正感知机的部分，产生的高阶特征有图decodeArc过程的时候得到，而不是由生成的图本身得到  
1ec_2 92.72:92.13:92.42  
1ec_2gc 92.49:92.26:92.38  

2016/12/19  
1ec_2gc之前测试都是只有1ec的图，所以放到全图低了0.1-0.2%个点，宣告破产  
enccg的数据  
1ec_1enccg_tst 94.32 : 91.88 : 93.09  
1ec_1enccg_dev 94.28 : 91.79 : 93.02  
1ec_1Lenccg_tst U : 94.50 : 91.62 : 93.04 L 90.31 : 87.56 : 88.91
1ec_1Lenccg_dev U : 94.62 : 91.33 : 92.95 L 90.24 : 87.11 : 88.65
1ec_2enccg 94.07 : 92.23 : 93.14  

2016/12/23  
1ec_1在enccg上的结果  
tst_psdtr 94.23 : 91.13 : 92.66  
dev_psdtr 94.32 : 91.40 : 92.83  
dev_mate  93.96 : 91.52 : 92.73  

2016/12/27 阶段性成果  
| dog | bird | cat | 
| ----|------|---- |
| foo | foo  | foo | 
| bar | bar  | bar | 
| baz | baz  | baz |  
