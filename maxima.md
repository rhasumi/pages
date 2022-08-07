---
layout: default
title: Maximaについての備忘録
permalink: /maxima/
nav_order: 3
---

# Maximaについての備忘録

- 方程式
```
solve([2*x+4*y=30,x+y=12],[x,y]);
```

- 微分方程式
```
atvalue(x(t),t=0,A);
atvalue(diff(x(t),t),t=0,0); 
desolve(m*diff(x(t),t,2)=-k*x(t),x(t));
 
atvalue(x(t),t=0,1);
atvalue(y(t),t=0,1);
desolve([diff(x(t),t)=2*x(t)-y(t),diff(y(t),t)=x(t)+2*y(t)],[x(t),y(t)]);

ode2(diff(f(x),x)+x*f(x)=sin(x)/x,f(x),x);
```

- ラプラス変換
```
laplace(sin(t),t,s);
ilt(1/(s^2+1),s,t);
 
integrate(sin(t)*exp(-s*t),t,0,inf);
```

- 特性関数（正規分布）
```
integrate(1/sqrt(2*%pi)*exp(-x^2/2)*exp(%i*x*t),x,-inf,inf);
integrate(exp(-t^2/2)*exp(-%i*x*t),t,-inf,inf)/(2*%pi);
```

- 極限
```
limit(sin(x)/x,x,0);
limit((1+1/n)^n,n,inf);
limit(1/x,x,0,plus);
```

- tayler展開
```
taylor(sin(x),x,0,10);
```

- 行列
```
M1:matrix([1,-2],[2,1]);
M2:matrix([2,-1],[1,2]);
M1.M2;
 
transpose(M1); 
ident(4);
zeromatrix(4,4);
```

- フーリエ級数
```
load("fourie");
fourier(x^2, x, 1);
fourier(sin(x), x, %pi);

fourint(1/x,x);

fourintcos(1,x);
fourintsin(1,x);
```

- 関数の定義
```
f[0]:0;
f[1]:aa0;
f[2]:aa1;
 
val:(-((n^2-2*n+1)*f[n-1]+f[n-2]+f[n-3])/(n^2-n));
define(f[n],buildq([u:val],expand(u)));

buildq([u:x^2],expand(u));

eq1:x^2+2*x+1=y^2;
lhs(eq1);
rhs(eq1);
define(f(x), buildq([u:lhs(eq1)],expand(u)));

define(f[n](x),x^n);
```

- ラグランジュ乗数法
```
r:2-x+3*y;
obj:x^2+y^2;
L:obj+lam*r;
 
eq:[diff(L,x) = 0,diff(L,y) = 0,diff(L,lam) = 0];
 
ans1:solve(eq,[x,y,lam]);
 
ans:ans1[1];
ev(L,ans);
```

### 正規分布の導出
```
# lam is negative 

p(x) := exp(mu - 1 + lam*(x-m)^2 );
eq1 : integrate(p(x), x, minf, inf) = 1;

ans1 : solve(eq1, mu);
mu : rhs(ans1[1]);
eq2 : integrate((x-m)^2*p(x), x, minf, inf) =sig^2;
 
ans2 : solve(eq2, lam);
lam : rhs(ans2[1]);
mu : ev(mu);
ev(p(x));
```

### 指数分布の導出
```
 q(x) := exp(lam0 - 1 + lam1*x);
 eq1 : integrate(q(x), x, 0, inf) = 1;
 
 ans1 : solve(eq1, lam0);
 lam0 : rhs(ans1[1]);
 
 eq2 :integrate(x*q(x), x, 0, inf) = 1/lambda ;
 ans2 : solve(eq2, lam1);
 lam1:rhs(ans2[1]);
 
 lam0 : ev(lam0);
 ev(q(x));
 
 eq3 :integrate((x-1/lambda)^2*q(x), x, 0, inf)
```

## リンク
- [Professional Maxima](http://t-ikeda.akira.ne.jp/enter/science/math/maxima/doc/pro-maxima-20080303.pdf)
- [Maxima 入門ノート](http://fe.math.kobe-u.ac.jp/MathLibre-doc/maxima-note.pdf)
