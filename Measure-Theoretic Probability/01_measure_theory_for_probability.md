# 확률론을 위한 측도론 기초

> 기준 교재: Donald L. Cohn, *Measure Theory*, 2nd ed.
> 우선 학습 범위: §§1.1-1.2, 2.1-2.4, 2.6, 3.1, 5.1-5.2, 10.1

이 노트의 목적은 측도론 전체를 공부하는 것이 아니라, **확률론의 정의와 정리를 읽는 데 꼭 필요한 언어**를 먼저 익히는 것이다. 첫 회독에서는 증명의 세부 기교보다 다음 연결을 이해하는 데 집중하면 된다.

| 측도론 | 확률론 |
|---|---|
| 전체 공간 $X$ | 표본공간 $\Omega$ |
| 가측집합 $A$ | 사건 $A$ |
| 측도 $\mu(A)$ | 확률 $P(A)$ |
| 가측함수 $f$ | 확률변수 $X$ |
| 적분 $\int f\,d\mu$ | 기대값 $E[X]$ |
| 거의 모든 곳에서 성립 | 거의 확실하게 성립 |
| 곱측도 | 결합분포와 독립성 |

---

## 1. 출발점: 집합은 사건의 언어다

확률론에서 사건은 집합이다. 주사위를 한 번 던질 때

$$
\Omega=\{1,2,3,4,5,6\}
$$

라고 하면, "짝수가 나온다"는 사건은 $A=\{2,4,6\}$이다.

집합 연산은 사건에 자연스럽게 대응한다.

- $A^c$: $A$가 일어나지 않는다.
- $A\cup B$: $A$ 또는 $B$가 일어난다.
- $A\cap B$: $A$와 $B$가 모두 일어난다.
- $A-B$: $A$는 일어나지만 $B$는 일어나지 않는다.
- $A_n\uparrow A$: 사건들이 점점 커지고 그 합집합이 $A$이다.
- $A_n\downarrow A$: 사건들이 점점 작아지고 그 교집합이 $A$이다.

드모르간 법칙은 자주 사용된다.

$$
\left(\bigcup_{n=1}^{\infty}A_n\right)^c
=\bigcap_{n=1}^{\infty}A_n^c,
\qquad
\left(\bigcap_{n=1}^{\infty}A_n\right)^c
=\bigcup_{n=1}^{\infty}A_n^c.
$$

확률의 극한 문제에는 무한 합집합과 무한 교집합이 자연스럽게 등장한다. 그래서 유한 번의 연산만 허용하는 집합족으로는 충분하지 않다.

## 2. $\sigma$-대수: 확률을 물어볼 수 있는 사건들의 모음

집합 $\Omega$ 위의 집합족 $\mathcal F$가 다음 조건을 만족하면 $\sigma$-대수라고 한다.

1. $\Omega\in\mathcal F$.
2. $A\in\mathcal F$이면 $A^c\in\mathcal F$.
3. $A_1,A_2,\ldots\in\mathcal F$이면 $\bigcup_{n=1}^{\infty}A_n\in\mathcal F$.

이 조건들로부터 $\varnothing\in\mathcal F$이고, 가산 교집합도 $\mathcal F$에 속한다.

### 왜 모든 부분집합에 확률을 주지 않는가?

유한 또는 가산 표본공간에서는 보통 모든 부분집합을 사건으로 삼아도 문제가 없다. 하지만 $\mathbb R$처럼 비가산인 공간에서는 모든 부분집합에 길이와 양립하는 확률을 일관되게 부여할 수 없다. 따라서 확률을 정의할 수 있는 충분히 큰 집합족 $\mathcal F$를 따로 정한다.

### 생성된 $\sigma$-대수와 보렐집합

집합족 $\mathcal C$를 포함하는 가장 작은 $\sigma$-대수를 $\sigma(\mathcal C)$라고 쓴다. 실수선의 열린집합들이 생성하는 $\sigma$-대수

$$
\mathcal B(\mathbb R)
$$

를 **보렐 $\sigma$-대수**라고 한다. 다음 집합족들은 모두 같은 $\mathcal B(\mathbb R)$를 생성한다.

$$
\{\text{열린집합}\},\quad
\{(-\infty,x]:x\in\mathbb R\},\quad
\{(a,b]:a<b\}.
$$

따라서 실숫값 함수 $X$의 가측성을 확인할 때 모든 보렐집합을 직접 다룰 필요 없이 $\{X\le x\}$ 같은 사건만 확인해도 된다.

## 3. 측도와 확률측도

가측공간 $(X,\mathcal F)$ 위의 함수

$$
\mu:\mathcal F\to[0,\infty]
$$

가 다음을 만족하면 측도라고 한다.

1. $\mu(\varnothing)=0$.
2. 서로소인 $A_1,A_2,\ldots\in\mathcal F$에 대해

$$
\mu\left(\bigcup_{n=1}^{\infty}A_n\right)
=\sum_{n=1}^{\infty}\mu(A_n).
$$

둘째 조건을 **가산가법성**이라고 한다. 유한가법성만으로는 무한 시행과 극한을 안정적으로 다루기 어렵기 때문에 확률론에서는 가산가법성이 핵심이다.

측도공간 $(\Omega,\mathcal F,P)$에서 $P(\Omega)=1$이면 $P$를 확률측도라고 하고, $(\Omega,\mathcal F,P)$를 확률공간이라고 한다.

### 바로 써먹는 성질

$A,B,A_n\in\mathcal F$라 하자.

**단조성**

$$
A\subseteq B\quad\Longrightarrow\quad P(A)\le P(B).
$$

**여사건**

$$
P(A^c)=1-P(A).
$$

**두 사건의 합집합**

$$
P(A\cup B)=P(A)+P(B)-P(A\cap B).
$$

**가산 부분가법성(union bound)**

$$
P\left(\bigcup_{n=1}^{\infty}A_n\right)
\le\sum_{n=1}^{\infty}P(A_n).
$$

마지막 식은 사건들이 서로소가 아니어도 성립한다.

### 집합열에 대한 연속성

$A_n\uparrow A$이면

$$
P(A_n)\uparrow P(A).
$$

$A_n\downarrow A$이면 확률측도는 유한측도이므로

$$
P(A_n)\downarrow P(A).
$$

이 성질은 "사건의 극한"을 "확률의 극한"으로 옮기는 기본 도구다.

예를 들어 $A_n$을 "첫 $n$번의 시행 중 적어도 한 번 성공"이라는 사건이라 하자. $A_n\uparrow A$이고 $A$는 "언젠가는 성공"이라는 사건이므로

$$
P(A)=\lim_{n\to\infty}P(A_n).
$$

## 4. 영집합과 거의 확실한 성질

$P(N)=0$인 사건 $N$을 영집합이라고 한다. 어떤 명제가 $N^c$에서 성립하면 그 명제는 **거의 확실하게** 성립한다고 말하고 a.s.라고 쓴다.

"거의 확실하게"는 "모든 $\omega$에서"와 다르다. 확률 0인 사건도 빈집합일 필요는 없다. 예를 들어 $[0,1]$에서 균등하게 한 수를 뽑을 때 정확히 $1/2$가 나올 확률은 0이지만, $1/2$라는 결과가 논리적으로 불가능한 것은 아니다.

가산개의 영집합 $N_1,N_2,\ldots$에 대해서는

$$
P\left(\bigcup_{n=1}^{\infty}N_n\right)=0.
$$

그래서 가산개의 a.s. 명제를 동시에 성립시키는 것이 가능하다. 이 사실은 확률변수열과 확률과정에서 매우 중요하다.

## 5. 가측함수와 확률변수

가측공간 $(\Omega,\mathcal F)$에서 $(S,\mathcal S)$로 가는 함수 $X:\Omega\to S$가 모든 $B\in\mathcal S$에 대해

$$
X^{-1}(B)=\{\omega:X(\omega)\in B\}\in\mathcal F
$$

를 만족하면 가측함수라고 한다. 확률공간 위의 가측함수를 **확률변수**라고 한다.

가측성의 뜻은 간단하다. $X$의 값이 어떤 범위에 들어가는지 묻는 질문이 실제 사건이어야 그 확률을 계산할 수 있다는 뜻이다.

실숫값 함수 $X$의 경우 다음을 모든 $x\in\mathbb R$에 대해 확인하면 충분하다.

$$
\{X\le x\}\in\mathcal F.
$$

### 확률변수가 생성하는 정보

$X$를 가측하게 만드는 가장 작은 $\sigma$-대수를 $\sigma(X)$라고 한다. 이는 **$X$를 관측해서 알 수 있는 모든 사건**의 모음이다.

예를 들어 주사위 결과를 $\omega$라고 하고, $X(\omega)=1$ if $\omega$ is even, $0$ otherwise라고 하자. $X$는 홀짝만 알려 주므로 $\sigma(X)$만으로는 결과가 정확히 2인지 4인지 구별할 수 없다.

## 6. 분포: 표본공간을 잊고 값의 공간만 보기

확률변수 $X:(\Omega,\mathcal F,P)\to(S,\mathcal S)$의 분포 $P_X$는

$$
P_X(B)=P(X\in B)=P(X^{-1}(B)),\qquad B\in\mathcal S
$$

로 정의한다. 이를 상측도 또는 pushforward measure라고도 한다. 분포를 알면 원래 표본공간의 구조를 몰라도 $X$에 관한 확률과 기대값을 계산할 수 있다.

### 누적분포함수

실숫값 확률변수의 누적분포함수는

$$
F_X(x)=P(X\le x)
$$

이다. $F_X$는 단조증가하고 오른쪽 연속이며, $x\to-\infty$일 때 0으로, $x\to\infty$일 때 1로 간다. 확률측도 $P_X$와 누적분포함수 $F_X$는 같은 분포 정보를 표현한다.

### 이산분포와 연속분포를 하나로 보기

- 이산형: 점들에 확률질량 $P(X=x)$가 놓인다.
- 연속형: 밀도 $f_X$가 존재하여 $P(X\in A)=\int_A f_X(x)\,dx$로 쓸 수 있다.

둘은 서로 다른 이론이 아니라, 모두 확률측도 $P_X$의 특별한 형태다.

## 7. 르베그 적분과 기대값

확률변수 $X$의 기대값은 확률측도에 대한 적분이다.

$$
E[X]=\int_\Omega X\,dP.
$$

르베그 적분은 다음 순서로 이해하면 쉽다.

1. 지시함수부터 적분한다.
2. 음이 아닌 단순함수로 확장한다.
3. 음이 아닌 가측함수를 단순함수의 증가극한으로 적분한다.
4. 일반 함수는 양의 부분과 음의 부분으로 나눈다.

### 지시함수와 단순함수

사건 $A$의 지시함수는

$$
\mathbf 1_A(\omega)=
\begin{cases}
1,&\omega\in A,\\
0,&\omega\notin A
\end{cases}
$$

이며

$$
E[\mathbf 1_A]=P(A).
$$

즉, **확률은 지시함수의 기대값**이다.

음이 아닌 단순함수 $\phi=\sum_{i=1}^{m}a_i\mathbf 1_{A_i}$에 대해서는

$$
\int\phi\,dP=\sum_{i=1}^{m}a_iP(A_i).
$$

이것은 이산확률변수의 기대값 공식과 같은 구조다.

### 적분가능성

$X=X^+-X^-$로 두자. 여기서 $X^+=\max(X,0)$이고 $X^-=\max(-X,0)$이다. $X$가 적분가능하다는 것은

$$
E[|X|]<\infty
$$

라는 뜻이다. 이 조건이면 $E[X]$가 유한한 실수로 잘 정의된다.

### 분포를 이용한 기대값 계산

적절한 보렐함수 $g$에 대해

$$
E[g(X)]=\int_{\mathbb R}g(x)\,P_X(dx).
$$

이를 흔히 LOTUS(Law of the Unconscious Statistician)라고 부른다. 이산형이면

$$
E[g(X)]=\sum_x g(x)P(X=x),
$$

밀도 $f_X$가 있으면

$$
E[g(X)]=\int_{\mathbb R}g(x)f_X(x)\,dx.
$$

$g(X)$의 분포를 새로 구하지 않고도 계산할 수 있다는 것이 핵심이다.

## 8. 기대값의 성질과 기본 확률부등식

$X,Y$가 적분가능하고 $a,b\in\mathbb R$이면

$$
E[aX+bY]=aE[X]+bE[Y].
$$

$X\le Y$ a.s.이면 $E[X]\le E[Y]$이다.

### Markov 부등식

$X\ge0$이고 $a>0$이면

$$
P(X\ge a)\le\frac{E[X]}{a}.
$$

이는 $X\ge a\mathbf 1_{\{X\ge a\}}$의 양변에 기대값을 취하면 얻어진다.

### Chebyshev 부등식

$X$의 평균이 $\mu$, 분산이 $\sigma^2<\infty$이면

$$
P(|X-\mu|\ge\varepsilon)
\le\frac{\sigma^2}{\varepsilon^2}.
$$

Markov 부등식을 $(X-\mu)^2$에 적용한 결과이며, 약한 대수의 법칙을 증명하는 기본 도구다.

## 9. 적분과 극한을 바꾸는 세 정리

확률론에서는 확률변수열 $X_n$에 대해

$$
E\left[\lim_{n\to\infty}X_n\right]
\stackrel{?}{=}
\lim_{n\to\infty}E[X_n]
$$

을 자주 묻는다. 점별수렴만으로는 이 등식이 보장되지 않는다.

### 단조수렴정리(MCT)

$0\le X_n\uparrow X$이면

$$
E[X_n]\uparrow E[X].
$$

음이 아닌 함수들을 아래에서부터 점점 정확하게 근사하면 적분도 정확한 값으로 증가한다.

### Fatou 보조정리

$X_n\ge0$이면

$$
E[\liminf X_n]\le\liminf E[X_n].
$$

극한 과정에서 질량이 멀리 도망갈 수 있으므로 완전한 등식 대신 한쪽 부등식만 항상 보장된다.

### 지배수렴정리(DCT)

$X_n\to X$ a.s.이고, 어떤 적분가능한 $Y$가 있어 모든 $n$에 대해 $|X_n|\le Y$ a.s.이면

$$
E[X_n]\to E[X]
$$

이고 $E[|X_n-X|]\to0$도 성립한다. $Y$가 함수열의 큰 값을 통제하여 질량이 무한대로 도망가는 현상을 막는다고 이해하면 된다.

| 상황 | 먼저 떠올릴 정리 |
|---|---|
| $0\le X_n\uparrow X$ | 단조수렴정리 |
| 음이 아닌 함수열이고 하극한만 필요 | Fatou 보조정리 |
| $X_n\to X$이고 적분가능한 공통 지배함수가 있음 | 지배수렴정리 |

## 10. 확률변수열의 수렴

### 거의 확실한 수렴

$$
X_n\to X\text{ a.s.}
\quad\Longleftrightarrow\quad
P\bigl(\{\omega:X_n(\omega)\to X(\omega)\}\bigr)=1.
$$

표본점 $\omega$를 고정했을 때 수열이 실제로 수렴하는 강한 개념이다.

### 확률수렴

모든 $\varepsilon>0$에 대해

$$
P(|X_n-X|>\varepsilon)\to0.
$$

$n$이 커질수록 큰 오차가 날 확률이 0으로 간다는 뜻이다.

### $L^p$ 수렴

$p\ge1$에 대해

$$
E[|X_n-X|^p]\to0.
$$

$p=1$이면 평균 절대오차가, $p=2$이면 평균제곱오차가 0으로 간다.

### 분포수렴

$X_n\Rightarrow X$는 $X_n$의 분포가 $X$의 분포에 약하게 수렴한다는 뜻이며 중심극한정리에서 등장한다.

### 반드시 기억할 관계

$$
X_n\to X\text{ a.s.}
\Longrightarrow
X_n\to X\text{ in probability}
\Longrightarrow
X_n\Rightarrow X.
$$

또한 $p\ge1$일 때

$$
X_n\to X\text{ in }L^p
\Longrightarrow
X_n\to X\text{ in probability}.
$$

역방향은 추가 조건 없이는 일반적으로 성립하지 않는다. 수렴 종류를 생략하고 단순히 "$X_n\to X$"라고 쓰지 않는 습관이 중요하다.

## 11. 곱측도, 결합분포, 독립성

두 측도공간 $(X,\mathcal A,\mu)$와 $(Y,\mathcal B,\nu)$가 있을 때 곱공간에는 곱측도 $\mu\times\nu$를 정의할 수 있다. 직사각형 사건에 대해서는

$$
(\mu\times\nu)(A\times B)=\mu(A)\nu(B).
$$

확률변수 $X,Y$의 결합분포 $P_{(X,Y)}$는 $\mathbb R^2$ 위의 확률측도다. $X$와 $Y$가 독립이라는 것은

$$
P_{(X,Y)}=P_X\times P_Y
$$

라는 뜻이다. 즉, **독립성은 결합분포가 주변분포의 곱으로 분해되는 성질**이다.

적분가능한 독립 확률변수에 대해서는

$$
E[XY]=E[X]E[Y].
$$

그러나 이 등식 하나만으로 독립성이 보장되지는 않는다.

### Tonelli와 Fubini

음이 아닌 가측함수 $f$에는 Tonelli 정리를 사용하여

$$
\int f\,d(\mu\times\nu)
=\int\left(\int f(x,y)\,\nu(dy)\right)\mu(dx)
$$

처럼 적분 순서를 바꿀 수 있다. 값이 $+\infty$여도 등식은 성립한다.

$f$가 적분가능하여 $\int |f|\,d(\mu\times\nu)<\infty$이면 Fubini 정리에 의해 반복적분들이 유한하고 적분 순서를 바꿀 수 있다.

기억법:

- **음이 아니면 Tonelli**: 우선 계산해도 된다.
- **부호가 섞이면 Fubini**: 절대적분가능성을 먼저 확인한다.

## 12. 하나의 예제로 전체 구조 연결하기

공정한 동전을 두 번 던진다고 하자.

$$
\Omega=\{HH,HT,TH,TT\},\qquad \mathcal F=2^\Omega.
$$

각 표본점에 확률 $1/4$을 주면 $(\Omega,\mathcal F,P)$는 확률공간이다. 앞면의 개수를

$$
X(HH)=2,\quad X(HT)=X(TH)=1,\quad X(TT)=0
$$

로 정의하면 $X$는 확률변수다. 그 분포는

$$
P_X(\{0\})=\frac14,\qquad
P_X(\{1\})=\frac12,\qquad
P_X(\{2\})=\frac14.
$$

따라서

$$
E[X]=0\cdot\frac14+1\cdot\frac12+2\cdot\frac14=1.
$$

여기서 한 번에 연결되는 개념은 다음과 같다.

1. $\Omega$: 가능한 결과 전체
2. $\mathcal F$: 질문할 수 있는 사건들
3. $P$: 사건에 확률을 부여하는 측도
4. $X$: 결과를 숫자로 바꾸는 가측함수
5. $P_X$: 그 숫자가 가지는 분포
6. $E[X]$: $X$를 $P$에 대해 적분한 값

## 13. 자주 헷갈리는 점

### 확률변수는 "변하는 숫자"가 아니라 함수다

확률변수 $X$는 $\omega$를 입력받아 숫자를 출력하는 함수다. 무작위성은 함수 자체가 아니라 아직 어떤 $\omega$가 실현될지 모른다는 데서 온다.

### $P(X=x)=0$이 그 값이 불가능하다는 뜻은 아니다

연속분포에서는 각 한 점의 확률이 0이어도 전체 구간의 확률은 양수일 수 있다. 가산가법성은 비가산 합에 그대로 적용되지 않는다.

### 거의 확실한 등식과 모든 점에서의 등식은 다르다

$X=Y$ a.s.라도 영집합 위에서는 두 함수가 다를 수 있다. 기대값과 분포를 계산할 때는 보통 이 차이가 영향을 주지 않는다.

### 밀도와 확률은 다르다

$f_X(x)$는 점 $x$의 확률이 아니다. 연속분포에서는

$$
P(a<X\le b)=\int_a^b f_X(x)\,dx.
$$

밀도는 1보다 클 수도 있지만 전체 적분은 1이어야 한다.

### 기댓값의 극한과 극한의 기댓값을 함부로 바꾸면 안 된다

점별수렴이나 a.s. 수렴만으로는 충분하지 않다. MCT나 DCT의 조건을 확인해야 한다.

### 무상관은 독립보다 약하다

$\operatorname{Cov}(X,Y)=0$은 선형 관계가 없다는 뜻일 뿐이다. 독립은 결합분포 전체가 곱으로 분해된다는 더 강한 조건이다.

## 14. 첫 회독 학습 순서

1. 사건과 집합 연산
2. $\sigma$-대수와 보렐집합
3. 측도와 확률측도
4. 영집합과 a.s.
5. 가측함수와 확률변수
6. 분포와 누적분포함수
7. 르베그 적분과 기대값
8. MCT, Fatou, DCT
9. 여러 수렴 개념
10. 곱측도와 독립성

책에서는 다음 절을 우선 보면 된다.

- §1.1: Algebras and Sigma-Algebras
- §1.2: Measures
- §2.1: Measurable Functions
- §2.2: Properties That Hold Almost Everywhere
- §2.3: The Integral
- §2.4: Limit Theorems
- §2.6: Image Measures
- §3.1: Modes of Convergence
- §§5.1-5.2: Product Measures and Fubini's Theorem
- §10.1: Probability Basics

외측도 구성(§1.3), 르베그 측도의 세부 구성(§1.4), 정칙성(§1.5), 부호측도와 복소측도(Chapter 4), 일반 위상공간에서의 측도(Chapters 7-9)는 첫 회독에서 미뤄도 된다. 다만 조건부기대값을 엄밀하게 공부할 때는 절대연속성과 Radon-Nikodym 정리가 필요하므로 나중에 Chapter 4로 돌아오면 된다.

## 15. 스스로 확인할 문제

### 문제 1

$A_n=\{\omega:X(\omega)>n\}$이라 하자. 유한한 실숫값 확률변수 $X$에 대해 $P(X>n)\to0$인 이유를 설명하라.

<details>
<summary>답</summary>

$A_n\downarrow\varnothing$이다. 각 $\omega$에 대해 충분히 큰 $n$에서는 $X(\omega)\le n$이므로 어느 점도 모든 $A_n$에 속하지 않는다. 확률의 위에서의 연속성으로 $P(A_n)\downarrow0$이다.

</details>

### 문제 2

사건 $A$에 대해 $E[\mathbf 1_A]$와 $\operatorname{Var}(\mathbf 1_A)$를 구하라.

<details>
<summary>답</summary>

$E[\mathbf 1_A]=P(A)$. 또한 $\mathbf 1_A^2=\mathbf 1_A$이므로

$$
\operatorname{Var}(\mathbf 1_A)=P(A)-P(A)^2=P(A)(1-P(A)).
$$

</details>

### 문제 3

$X_n\to X$ a.s.이면 항상 $E[X_n]\to E[X]$인가?

<details>
<summary>답</summary>

아니다. 기대값과 극한을 바꾸려면 추가 조건이 필요하다. 음이 아닌 단조증가가 있으면 MCT를, 적분가능한 공통 지배함수가 있으면 DCT를 사용할 수 있다.

</details>

### 문제 4

독립인 적분가능 확률변수 $X,Y$에 대해 왜 $E[XY]=E[X]E[Y]$인가?

<details>
<summary>답</summary>

독립이면 결합분포가 $P_X\times P_Y$로 분해된다. Fubini 정리를 사용하면

$$
E[XY]
=\int xy\,(P_X\times P_Y)(dx,dy)
=\left(\int x\,P_X(dx)\right)
 \left(\int y\,P_Y(dy)\right).
$$

</details>

## 16. 이번 단계에서 기억할 핵심 문장

1. 확률공간은 전체 결과 $\Omega$, 사건의 모음 $\mathcal F$, 확률측도 $P$의 삼중항이다.
2. 확률변수는 가측함수다.
3. 분포는 확률변수가 원래 확률측도를 값의 공간으로 옮긴 것이다.
4. 기대값은 확률측도에 대한 르베그 적분이다.
5. 거의 확실하다는 것은 확률 0인 예외를 허용한다는 뜻이다.
6. 적분과 극한의 순서를 바꿀 때는 반드시 정리의 조건을 확인한다.
7. 독립성은 결합분포가 주변분포의 곱으로 분해되는 성질이다.
