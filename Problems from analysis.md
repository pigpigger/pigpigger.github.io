## Problems from analysis

### 1 数学分析wsj习题5.41

$$
p_n(x)=\frac{1}{2^nn!}\frac{d^n}{dx^n}(x^2-1)^n\\
prove:\ p_n(1)=1 \\
proof\ 1:\\
\frac{d^n}{dx^n}(x^2-1)^n=n!\sum_{k=1}^n\binom{n}{k}\binom{2k}{n}x^{2k-n}(-1)^{n-k}\\
x=1\\
\sum_{k}\binom{n}{k}\binom{2k}{n}(-1)^{n-k}\\\
=\sum_{k}\binom{n}{k}\binom{2k}{n}(-1)^{n-k}\\
=\sum_{k,j}\binom{n}{k}\binom{k}{j}\binom{k}{n-j}(-1)^{n-k}\\
=\sum_{k,j}\binom{n}{j}\binom{n-j}{k-j}\binom{k}{n-j}(-1)^{n-k}\\
=\sum_{k,j,l}\binom{n}{j}\binom{n-j}{k-j}\binom{k-j}{l}\binom{j}{n-j-l}(-1)^{n-k}\\
=\sum_{k,j,l}\binom{n}{j}\binom{n-j}{l}\binom{n-j-l}{k-j-l}\binom{j}{n-j-l}(-1)^{n-k}\\
=\sum_{k,j,l}\binom{n}{j}\binom{n-j}{l}\binom{j}{n-j-l}(-1)^{n+j+l}(-1)^{k-j-l}\binom{n-j-l}{k-j-l}\\
=\sum_{k,j,l}\binom{n}{j}\binom{n-j}{l}\binom{j}{n-j-l}(-1)^{n+j+l}[j+l==n]\\
=\sum_{j}\binom{n}{j}\\
=2^n
$$

$$
prove \ 2:
\sum_{k}\binom{n}{k}\binom{2k}{n}(-1)^{n-k}\\
=\sum_{k}\binom{k}{n-k}\binom{2k}{k}(-1)^{n-k}\\
=[x^n]\sum_{k}\binom{2k}{k}(1+x)^kx^k(-1)^{n-k}
\ \ (ps:\sum_k\binom{2k}{k}x^k=\sqrt{\frac{1}{1-4x}})\\
=[x^n]\sqrt{\frac{1}{1+4x(1+x)}}(-1)^n\\
=[x^n]\frac{1}{1+2x}(-1)^n\\
=2^n
$$

but finally it occurred to me that ......
$$
\frac{1}{2^nn!}\frac{d^n}{dx^n}(x^2-1)^n\\
=\frac{1}{2^nn!}\frac{d^n}{dx^n}((x+1)^n(x-1)^n)\\
apply \ leibniz \ formula
$$

### 2 

$$
prove \\\sum_k{\binom{n}{k}\frac{(-1)^k}{m+k+1}}=\frac{m!n!}{(m+n+1)!}
$$

I found there was no suitable tool for it

so I had to look into Concrete Mathematics -- Gosper!

现学

#### proof 1:

$$
S(n)=t(n,k)=\binom{n}{k}\frac{(-1)^k}{m+k+1}\\
\hat{t}(n,k)=\beta_0(n)t(n,k)+\beta_1(n)t(n+1,k)=T(k+1)-T(k)\\
T(k) \ has \ the \ form \ T(k)=\frac{r(k)s(k)t(k)}{p(k)}  \\
\frac{t(n+1,k)}{t(n,k)}=\frac{n+1}{n+1-k}\\
so \ let \ p(n,k)=\beta_0(n)(n+1-k)+(n+1)\beta_1(n)\\
now\ \hat{t}(n,k)=p(n,k)\frac{t(n,k)}{n+1-k}\\
\bar{t}(n,k)=\frac{t(n,k)}{p(n,k)}\\
\bar{p}(n,k)=\frac{\hat{p}(n,k)}{p(n,k)}\\
\frac{\bar{t}(n,k+1)}{\bar{t}(n,k)}=\frac{\bar{p}(n,k+1)q(n,k)}{\bar{p}(n,k)r(n,k+1)}
=\frac{-(n+1-k)(m+k+1)}{(k+1)(m+k+2)}\\
\bar{p}(n,k)=1\\
q(n,k)=(n+1-k)(m+k+1)\\

r(n,k)=-k(m+k+1)\\
(n+1-k)\beta_0(n)+(n+1)\beta_1(n)=(m+k+1)((n+1-k)s(n,k+1)+ks(n,k))\\
consider \ \  the \ \ coefficient \ \ of \ \ k\\
the \ \ degree \ \ of \ \ s \ \  must \ \  be \ \ 0\\
hence \ s(n,k)=1 \ \  \beta_0(n)=-n-1 \ \  \beta_1(n)=m+n+2\\
S(n+1)/S(n)=(n+1)/(m+n+2)
$$
#### proof 2

$$
\Delta^n(\frac{1}{x})\\
=\Delta^n((1-x)^{\underline{-1}})=(-1)^n(x-1)^{\underline{-n-1}}=(-1)^n\frac{n!}{x(x+1)...(x+n)}
$$
on the other hand we can expand
$$
\Delta^n=(E-1)^n=.....
$$

#### proof 3

then I observe the form 

it is similar to a identity that haunted me for more than a year

it is about the connection between the recurrence and the inclusive-exclusive expression of stirling number of second kind
$$
\sum_{i=1}^m \frac{\binom{m}{i}(-1)^{m-i}}{1-ix}=\frac{x^m \ m!}{\prod_{i=1}^m(1-ix)}
$$
the left hand side is inclusive-exclusive

the right of obtained by the recurrence

 

it is easy(?) to see this is equivalent to the probem

thus we get a combinatorial demonstration

ps : whether x is an integer is not important since 考虑多项式在无限个点值为零则为零

#### proof 4

but in fact if we consider starting  from the right hand side

Partial Fraction Expansion
$$
F(x)=\frac{x!}{(x+n+1)!}=\frac{1}{(x+n+1)(x+n)...(x+1)}
$$


convert it into partial fraction
$$
F(x)=\sum_{k=1}^{n+1}\frac{b_k}{x+k}\\
b_k=\lim_{x\to-k}(x+k)F(x)=\frac{1}{(n+1-k)!(k-1)!(-1)^k}\\
F(x)=\frac{1}{n!}\sum_{k=1}^{n+1}\binom{n}{k-1}\frac{(-1)^{k-1}}{x+k}\\
$$
then set x=m.

#### proof 5

the real solution:

$$
\sum_k\binom{n}{k}\frac{(-1)^k}{m+k+1}\\
=\sum_k\binom{n}{k}\int_0^1{x^{m+k}}dx(-1)^k\\
=\int_0^1x^m(1-x)^n\\
$$
分部积分法+递推

ds![image-20221125120549510](/home/lbh/.config/Typora/typora-user-images/image-20221125120549510.png)
