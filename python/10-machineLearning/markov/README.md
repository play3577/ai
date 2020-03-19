# 馬可夫鏈 Markov Chain

## markov.js

計算某序列 [b,a,b,b] 的機率

```
$ node markov
P(["b","a","b","b"])=0.06
```

## gibbs.js


Gibbs Algorithm 的範例

問題：機率式有限狀態機，P(a=>b)=0.3, P(b=>a)=0.5 ; P(a=>b)=0.7, P(b=>b)=0.5

目標：尋找該「機率式有限狀態機」的穩態，也就是 P(a) = ?, P(b)=? 時系統會達到平衡。


```
$ node gibbs
P1 = {"a":0.54,"b":0.46}
P1 = {"a":0.608,"b":0.392}
P1 = {"a":0.6215999999999999,"b":0.37839999999999996}
P1 = {"a":0.62432,"b":0.37567999999999996}
P1 = {"a":0.624864,"b":0.37513599999999997}
標準答案:P(a)=5/8=0.625 P(b)=3/8=0.375
```

## metropolis.js

Metropolis Hasting 的範例

問題：機率式有限狀態機，P(a)=0.2, P(b)=0.3, P(c)=0.1

目標：尋找「轉移矩陣」的穩態，也就是 Q(x→y)=? 時系統會達到細緻平衡 (每條連線都平衡了)。

```
$ node metropolis
Q = {"a":0.2,"b":0.7,"c":0.1,"a=>a":0.5,"a=>b":0.3,"a=>c":0.2,"b=>a":0.1,"b=>b":0.2,"b=>c":0.7,"c=>a":0.3,"c=>b":0.3,"c=>c":0.4}
x=a y=a, A[x=>y]=1 P[y]*Q[y=>x]=0.1 P(x)*Q[x=>y]=0.1
x=a y=b, A[x=>y]=1.1666666666666665 P[y]*Q[y=>x]=0.06 P(x)*Q[x=>y]=0.06999999999999999
x=a y=c, A[x=>y]=0.7499999999999998 P[y]*Q[y=>x]=0.04000000000000001 P(x)*Q[x=>y]=0.03
x=b y=a, A[x=>y]=0.8571428571428572 P[y]*Q[y=>x]=0.06999999999999999 P(x)*Q[x=>y]=0.06
x=b y=b, A[x=>y]=1 P[y]*Q[y=>x]=0.13999999999999999 P(x)*Q[x=>y]=0.13999999999999999
x=b y=c, A[x=>y]=0.06122448979591837 P[y]*Q[y=>x]=0.48999999999999994 P(x)*Q[x=>y]=0.03
x=c y=a, A[x=>y]=1.3333333333333337 P[y]*Q[y=>x]=0.03 P(x)*Q[x=>y]=0.04000000000000001
x=c y=b, A[x=>y]=16.333333333333332 P[y]*Q[y=>x]=0.03 P(x)*Q[x=>y]=0.48999999999999994
x=c y=c, A[x=>y]=1 P[y]*Q[y=>x]=0.04000000000000001 P(x)*Q[x=>y]=0.04000000000000001
A = {"a=>a":1,"a=>b":1.1666666666666665,"a=>c":0.7499999999999998,"b=>a":0.8571428571428572,"b=>b":1,"b=>c":0.06122448979591837,"c=>a":1.3333333333333337,"c=>b":16.333333333333332,"c=>c":1}
diff = 0.7214285714285714
Q = {"a=>a":0.55,"a=>b":0.3,"a=>c":0.14999999999999997,"b=>a":0.08571428571428573,"b=>b":0.8714285714285714,"b=>c":0.04285714285714286,"c=>a":0.3,"c=>b":0.3,"c=>c":0.4}
x=a y=a, A[x=>y]=1 P[y]*Q[y=>x]=0.11000000000000001 P(x)*Q[x=>y]=0.11000000000000001
x=a y=b, A[x=>y]=1.0000000000000002 P[y]*Q[y=>x]=0.06 P(x)*Q[x=>y]=0.060000000000000005
x=a y=c, A[x=>y]=1.0000000000000002 P[y]*Q[y=>x]=0.029999999999999995 P(x)*Q[x=>y]=0.03
x=b y=a, A[x=>y]=0.9999999999999999 P[y]*Q[y=>x]=0.060000000000000005 P(x)*Q[x=>y]=0.06
x=b y=b, A[x=>y]=1 P[y]*Q[y=>x]=0.61 P(x)*Q[x=>y]=0.61
x=b y=c, A[x=>y]=1 P[y]*Q[y=>x]=0.03 P(x)*Q[x=>y]=0.03
x=c y=a, A[x=>y]=0.9999999999999999 P[y]*Q[y=>x]=0.03 P(x)*Q[x=>y]=0.029999999999999995
x=c y=b, A[x=>y]=1 P[y]*Q[y=>x]=0.03 P(x)*Q[x=>y]=0.03
x=c y=c, A[x=>y]=1 P[y]*Q[y=>x]=0.04000000000000001 P(x)*Q[x=>y]=0.04000000000000001
A = {"a=>a":1,"a=>b":1.0000000000000002,"a=>c":1.0000000000000002,"b=>a":0.9999999999999999,"b=>b":1,"b=>c":1,"c=>a":0.9999999999999999,"c=>b":1,"c=>c":1}
diff = 6.938893903907228e-17
```