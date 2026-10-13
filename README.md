# 應用統計學與機率論 — 公式與知識點筆記

> **Applied Statistics & Probability — Formula and Knowledge-Point Notes**
> 繁體中文・中英術語對照・含例題詳解

本筆記依據五份講義（UFUG2104 課程）整理：

1. Introduction（緒論）
2. Descriptive Statistics（描述統計）
3. Probability（機率）
4. Discrete Random Variables（離散隨機變數）
5. Continuous Random Variables（連續隨機變數）

數學式以 LaTeX 撰寫，GitHub 原生支援 `$...$`（行內）與 `$$...$$`（獨立式）渲染。
若需要互動式 KaTeX 版本（可離線開啟、公式更美觀），請見同倉庫之 [`UFUG2104_公式筆記.html`](./UFUG2104_公式筆記.html)。

---

## 目錄

- [第一章 緒論 (Introduction)](#第一章-緒論-introduction)
- [第二章 描述統計 (Descriptive Statistics)](#第二章-描述統計-descriptive-statistics)
- [第三章 機率 (Probability)](#第三章-機率-probability)
- [第四章 離散隨機變數 (Discrete Random Variables)](#第四章-離散隨機變數-discrete-random-variables)
- [第五章 連續隨機變數 (Continuous Random Variables)](#第五章-連續隨機變數-continuous-random-variables)
- [附錄：分配速查表](#附錄分配速查表)

---

## 第一章 緒論 (Introduction)

### 1.1 何謂統計學 (What is Statistics)

- **統計學 (Statistics)**：從資料中蒐集、整理、分析、詮釋並做出推論的一門科學。
- **應用統計學 (Applied Statistics)**：把統計方法實際運用於解決真實問題（"statistics-in-action"），由 **描述統計** 與 **推論統計的應用** 組成。

### 1.2 描述統計 vs 推論統計

| 類型 | 英文 | 定義 | 關鍵動作 |
| --- | --- | --- | --- |
| 描述統計 | Descriptive Statistics | 對已觀察到的資料進行收集、整理、呈現與摘要 | 平均數、圖表、變異數 |
| 推論統計 | Inferential Statistics | 由樣本 (sample) 推論母體 (population) 的結論 | 估計、假說檢定、預測 |

### 1.3 母體與樣本

- **母體 (Population)**：研究對象的整體集合。
- **樣本 (Sample)**：從母體中選出、用來描述母體特徵的一部分。
- 目標：以較小的樣本資訊，推論整個母體的性質。

### 1.4 參數與統計量

- **參數 (Parameter)**：描述母體特徵的數值（通常以希臘字母表示，如 $\mu, \sigma^2$）。
- **統計量 (Statistic)**：由樣本計算出來、用來估計參數的數值（如 $\bar{x}, s^2$）。
- 關係：統計量是參數的**估計量 (estimator)**。

### 1.5 變數的類型 (Types of Variables)

| 分類軸 | 類別 | 說明 / 例子 |
| --- | --- | --- |
| 依測量尺度 | 類別變數 (Categorical) | 名義 (Nominal)：性別、顏色；有序 (Ordinal)：評等、學歷 |
| | 數值變數 (Quantitative) | 離散 (Discrete)：人數、次數；連續 (Continuous)：身高、時間 |
| 依因果角色 | 自變數 / 依變數 | independent / dependent variable |

### 1.6 研究設計

- **實驗性研究 (Experimental Study)**：研究者主動操控自變數、控制干擾因子。
- **觀察性研究 (Observational Study)**：僅觀察記錄，不介入操控。
- **統計素養 (Statistical Literacy)**：能解讀、批判並討論統計資訊的能力。

---

## 第二章 描述統計 (Descriptive Statistics)

### 2.1 資料類型回顧

- **類別資料 (Categorical)**：用圖表（長條圖 bar chart、圓餅圖 pie chart）呈現。
- **數值資料 (Quantitative)**：用次數表、直方圖 (histogram)、盒鬚圖 (boxplot)、散佈圖 (scatter plot) 等呈現。

### 2.2 位置量數 (Measures of Location)

| 量數 | 英文 | 定義 / 公式 |
| --- | --- | --- |
| 樣本平均數 | Sample Mean | $\bar{x}=\dfrac{1}{n}\sum_{i=1}^{n}x_i$ |
| 母體平均數 | Population Mean | $\mu=\dfrac{1}{N}\sum_{i=1}^{N}x_i$ |
| 中位數 | Median | 排序後位於正中者；若 $n$ 為偶數，取中間兩數平均 |
| 眾數 | Mode | 出現頻率最高的值 |
| 截尾平均 | Trimmed Mean | 去掉最高與最低各 $p\%$ 後再平均，可降低異常值影響 |
| 加權平均 | Weighted Mean | $\bar{x}_w=\dfrac{\sum w_i x_i}{\sum w_i}$ |

### 2.3 變異量數 (Measures of Variability)

| 量數 | 英文 | 公式 |
| --- | --- | --- |
| 全距 | Range | $\max-\min$ |
| 樣本變異數 | Sample Variance | $s^2=\dfrac{1}{n-1}\sum_{i=1}^{n}(x_i-\bar{x})^2$ |
| 母體變異數 | Population Variance | $\sigma^2=\dfrac{1}{N}\sum_{i=1}^{N}(x_i-\mu)^2$ |
| 樣本標準差 | Sample Std. Dev. | $s=\sqrt{s^2}$ |
| 母體標準差 | Population Std. Dev. | $\sigma=\sqrt{\sigma^2}$ |
| 變異係數 | Coefficient of Variation (CV) | $\mathrm{CV}=\dfrac{s}{\bar{x}}$（無量綱，便於比較不同尺度資料） |

> **重點**：樣本變異數的分母為 **$n-1$**（自由度 degrees of freedom），而非 $n$。
> 原因：先以樣本估計 $\bar{x}$ 會「消耗」一個自由度；使用 $n-1$ 可得到母體變異數的**不偏估計 (unbiased estimator)**。

### 2.4 四分位數、百分位數與 IQR

- **百分位數 (Percentile)** $P_k$：有 $k\%$ 的觀測值小於或等於該值。
- **四分位數 (Quartiles)**：$Q_1=P_{25},\; Q_2=\text{中位數},\; Q_3=P_{75}$。
- **四分位距 (Interquartile Range, IQR)**：

$$ \mathrm{IQR}=Q_3-Q_1 $$

### 2.5 盒鬚圖與異常值 (Boxplot & Outliers)

- 盒鬚圖以 $Q_1, Q_2, Q_3$ 與鬚 (whiskers) 呈現分佈與離群情形。
- **異常值判斷規則 (1.5×IQR rule)**：

$$
\text{正常值範圍：}\quad Q_1-1.5\,\mathrm{IQR}\;\le\; x \;\le\; Q_3+1.5\,\mathrm{IQR}
$$

超出此範圍者視為**潛在異常值 (outlier)**。

### 2.6 偏態與經驗法則

- **偏態 (Skewness)**：
  - 對稱 (symmetric)：$\bar{x}\approx \text{中位數}$
  - 右偏 / 正偏 (right-skewed)：平均數 > 中位數（長尾在右）
  - 左偏 / 負偏 (left-skewed)：平均數 < 中位數（長尾在左）
- **經驗法則 (Empirical Rule)**（僅適用於近似常態）：
  - 約 68% 資料落在 $\mu\pm\sigma$
  - 約 95% 落在 $\mu\pm2\sigma$
  - 約 99.7% 落在 $\mu\pm3\sigma$

### 2.7 例題詳解：pH 計偏差

**題目**：工程師檢測一台 pH 計的偏差，對中性物質（pH=7.0）取樣本數 $n=10$，量得：
`7.07, 7.00, 7.10, 6.97, 7.00, 7.03, 7.01, 7.01, 6.98, 7.08`。
求樣本變異數與樣本標準差。

**解**：
1. 樣本平均數

$$ \bar{x}=\frac{7.07+7.00+\cdots+7.08}{10}=7.025 $$

2. 樣本變異數（分母 $n-1=9$）

$$ s^2=\frac{(7.07-7.025)^2+(7.00-7.025)^2+\cdots+(7.08-7.025)^2}{9}=0.001939 $$

3. 樣本標準差

$$ s=\sqrt{0.001939}\approx 0.044 $$

自由度為 $n-1=9$。

---

## 第三章 機率 (Probability)

### 3.1 隨機試驗、樣本空間與事件

- **隨機試驗 (Random Experiment)**：結果不確定但可重複的實驗。
- **樣本空間 (Sample Space)** $S$：所有可能結果的集合。
- **事件 (Event)** $A$：樣本空間的子集合，$A\subseteq S$。

### 3.2 機率公理 (Kolmogorov Axioms)

1. 非負性 (Non-negativity)：$\displaystyle P(A)\ge 0$
2. 歸一性 (Normalization)：$\displaystyle P(S)=1$
3. 可數可加性 (Countable Additivity)：若 $A_1,A_2,\dots$ 兩兩互斥，則

$$ P\!\left(\bigcup_{i=1}^{\infty}A_i\right)=\sum_{i=1}^{\infty}P(A_i) $$

### 3.3 機率性質 (Properties)

- 補集 (Complement)：$\displaystyle P(A^c)=1-P(A)$
- 單調性：若 $A\subseteq B$，則 $P(A)\le P(B)$
- 空事件：$P(\varnothing)=0$

### 3.4 加法法則 (Addition Rule)

$$ P(A\cup B)=P(A)+P(B)-P(A\cap B) $$

- 若 $A,B$ **互斥 (mutually exclusive)**，即 $A\cap B=\varnothing$，則

$$ P(A\cup B)=P(A)+P(B) $$

### 3.5 計數原理 (Counting)

| 情境 | 公式 | 說明 |
| --- | --- | --- |
| 乘法原理 | $n_1\times n_2\times\cdots$ | 多階段、各階段選擇數相乘 |
| 可重複排列（有序、可放回） | $n^k$ | $k$ 次抽取，每次 $n$ 種 |
| 排列 (Permutation) | $P(n,k)=\dfrac{n!}{(n-k)!}$ | 從 $n$ 取 $k$ 個、考慮順序 |
| 組合 (Combination) | $\displaystyle \binom{n}{k}=\frac{n!}{k!(n-k)!}$ | 從 $n$ 取 $k$ 個、不考慮順序 |
| 階乘 | $n!=n(n-1)\cdots 1,\; 0!=1$ | — |
| Stirling 近似 | $\displaystyle n!\approx \sqrt{2\pi n}\left(\frac{n}{e}\right)^n$ | $n$ 很大時估算階乘 |

### 3.6 條件機率與乘法法則

- **條件機率 (Conditional Probability)**：

$$ P(A\mid B)=\frac{P(A\cap B)}{P(B)},\qquad P(B)>0 $$

- **乘法法則 (Multiplication Rule)**：

$$ P(A\cap B)=P(A)\,P(B\mid A)=P(B)\,P(A\mid B) $$

### 3.7 獨立性 (Independence)

- $A,B$ 獨立 $\iff P(A\cap B)=P(A)\,P(B)$
- 等價地：$P(A\mid B)=P(A)$（已知 $B$ 不改變 $A$ 的機率）
- 多事件獨立需滿足所有子集聯合機率皆等於邊際機率之乘積。

### 3.8 全機率定理 (Law of Total Probability)

若 $A_1,\dots,A_n$ 為 $S$ 的一個分割 (partition)（兩兩互斥且聯集為 $S$），則對任意事件 $B$：

$$ P(B)=\sum_{i=1}^{n}P(B\mid A_i)\,P(A_i) $$

### 3.9 貝氏定理 (Bayes' Theorem)

$$ P(A_i\mid B)=\frac{P(B\mid A_i)\,P(A_i)}{\sum_{j=1}^{n}P(B\mid A_j)\,P(A_j)} $$

醫學檢測常用術語：
- **敏感度 (Sensitivity)** $=P(\text{test+}\mid \text{有病})$
- **特異度 (Specificity)** $=P(\text{test-}\mid \text{無病})$

### 3.10 例題詳解

**例題 A — 號碼球（加法法則）**
甕中有編號 0–9 的 10 顆球，隨機取一球。令
$A=${號碼為奇數}$=\{1,3,5,7,9\}$，$P(A)=5/10$；
$B=${號碼為 3 的倍數}$=\{3,6,9\}$，$P(B)=3/10$；
$A\cap B=\{3,9\}$，$P(A\cap B)=2/10$。

$$ P(A\cup B)=P(A)+P(B)-P(A\cap B)=\frac{5}{10}+\frac{3}{10}-\frac{2}{10}=\frac{6}{10} $$

**例題 B — 貝氏定理（疾病篩檢）**
檢測準確率 99%（不論陽性或陰性皆 99%）。若**半數人口患病**，某人檢測陽性，求他真的患病的事後機率 $P(D\mid \text{test+})$。

$$
\begin{aligned}
P(D\mid \text{test+})
&=\frac{P(\text{test+}\mid D)\,P(D)}
        {P(\text{test+}\mid D)P(D)+P(\text{test+}\mid D^c)P(D^c)} \\[4pt]
&=\frac{0.99\times 0.5}{0.99\times 0.5+0.01\times 0.5}
 =\frac{0.495}{0.500}=0.99=99\%
\end{aligned}
$$

> 若**盛行率僅 1%**（敏感度、特異度仍 99%），則
> $P(\text{test+})=0.99\times0.01+0.01\times0.99=0.0198$，
> 事後機率 $P(D\mid\text{test+})=\dfrac{0.0099}{0.0198}=50\%$。
> 這說明：**基礎機率 (base rate) 極大影響事後機率**。

---

## 第四章 離散隨機變數 (Discrete Random Variables)

### 4.1 隨機變數、pmf 與 cdf

- **隨機變數 (Random Variable)** $X$：將樣本空間映射至實數的函數。
- **機率質量函數 (pmf, probability mass function)**：

$$ p_X(x)=P(X=x),\qquad \sum_x p_X(x)=1 $$

- **累積分佈函數 (cdf, cumulative distribution function)**：

$$ F_X(x)=P(X\le x) $$

離散型的 cdf 為**右連續的階梯函數 (right-continuous step function)**。

### 4.2 期望、變異數與動差

- **期望 / 平均 (Expectation / Mean)**：

$$ E[X]=\sum_x x\,p_X(x) $$

- 函數的期望：$E[g(X)]=\sum_x g(x)\,p_X(x)$

- **變異數 (Variance)**：

$$ \operatorname{Var}(X)=E\!\left[(X-\mu)^2\right]=E[X^2]-\mu^2,\qquad \mu=E[X] $$

- **標準差 (Standard Deviation)**：$SD(X)=\sqrt{\operatorname{Var}(X)}$
- **動差 (Moments)**：第 $k$ 階動差 $E[X^k]$；變異數是第二階**中心動差 (central moment)**。

### 4.3 期望與變異數的性質

$$
\begin{aligned}
E[aX+b] &= a\,E[X]+b \\
\operatorname{Var}(aX+b) &= a^2\,\operatorname{Var}(X) \\
E[X+Y] &= E[X]+E[Y] \quad\text{（恆成立）}\\
\operatorname{Var}(X+Y) &= \operatorname{Var}(X)+\operatorname{Var}(Y) \quad\text{（當 }X,Y\text{ 獨立時）}
\end{aligned}
$$

### 4.4 Bernoulli 分配 (Bernoulli Distribution)

單次試驗成功（1）或失敗（0），成功機率 $p$。

$$
p_X(k)=
\begin{cases}
p, & k=1\\
1-p, & k=0
\end{cases}
\qquad
E[X]=p,\quad \operatorname{Var}(X)=p(1-p)
$$

### 4.5 Binomial 分配 (Binomial Distribution)

$n$ 次**獨立** Bernoulli 試驗中成功次數，每次成功機率 $p$。

$$
P(X=k)=\binom{n}{k}p^k(1-p)^{n-k},\quad k=0,1,\dots,n
$$

$$
E[X]=np,\qquad \operatorname{Var}(X)=np(1-p)
$$

> 可視為 $n$ 個獨立 Bernoulli 變數之和：$X=\sum_{i=1}^{n}X_i$。

### 4.6 Geometric 分配 (Geometric Distribution)

反覆獨立試驗直到首次成功所需的試驗次數，成功機率 $p$。

$$
P(X=k)=(1-p)^{k-1}p,\quad k=1,2,\dots
$$

$$
E[X]=\frac{1}{p},\qquad \operatorname{Var}(X)=\frac{1-p}{p^2}
$$

- **無記憶性 (Memoryless)**：$\displaystyle P(X>m+n\mid X>m)=P(X>n)$

### 4.7 Poisson 分配 (Poisson Distribution)

描述單位時間/空間內事件發生的次數，平均發生率 $\lambda>0$。

$$
P(X=k)=\frac{e^{-\lambda}\lambda^k}{k!},\quad k=0,1,2,\dots
$$

$$
E[X]=\lambda,\qquad \operatorname{Var}(X)=\lambda
$$

- **二項近似 (Poisson approximation to Binomial)**：當 $n$ 很大、$p$ 很小時，令 $\lambda=np$，則

$$ \binom{n}{k}p^k(1-p)^{n-k}\approx \frac{e^{-\lambda}\lambda^k}{k!} $$

### 4.8 例題詳解

**例題 A — 擲硬幣三次（Binomial）**
擲一公平硬幣三次，令 $X=$ 正面次數，則 $X\sim\mathrm{Binomial}(n=3,p=0.5)$。

| $k$ | 0 | 1 | 2 | 3 |
| --- | --- | --- | --- | --- |
| $P(X=k)$ | $1/8$ | $3/8$ | $3/8$ | $1/8$ |

對應結果：TTT；{HTT,THT,TTH}；{HHT,HTH,THH}；HHH。

**例題 B — 位元錯誤（Binomial + Poisson 近似）**
一區塊 200 位元經二元通道傳送，每位元錯誤機率 $p=0.01$，且彼此獨立。令 $X=$ 錯誤位元數。

- (a) 恰有 3 個錯誤：

$$ P(X=3)=\binom{200}{3}(0.01)^3(0.99)^{197}\approx 0.1814 $$

- (b) 期望值與變異數：

$$ E[X]=np=200\times0.01=2,\qquad \operatorname{Var}(X)=np(1-p)=1.98 $$

此處 $\lambda=np=2$，必要時可用 Poisson(2) 近似。

---

## 第五章 連續隨機變數 (Continuous Random Variables)

### 5.1 cdf、pdf 與期望

- **累積分佈函數 (cdf)**：$F_X(x)=P(X\le x)$（連續、非遞減）。
- **機率密度函數 (pdf, probability density function)**：

$$ f_X(x)=\frac{d}{dx}F_X(x),\qquad \int_{-\infty}^{\infty}f_X(x)\,dx=1 $$

- 區間機率：

$$ P(a<X<b)=\int_a^b f_X(x)\,dx $$

- 單點機率為 0：$P(X=a)=0$（連續型與離散型最大差異）。
- 期望與變異數：

$$ E[X]=\int_{-\infty}^{\infty}x\,f_X(x)\,dx,\qquad
\operatorname{Var}(X)=\int_{-\infty}^{\infty}(x-\mu)^2 f_X(x)\,dx=E[X^2]-\mu^2 $$

### 5.2 Uniform 分配 (Continuous Uniform)

$X$ 在區間 $[a,b]$ 上等可能。

$$
f_X(x)=
\begin{cases}
\dfrac{1}{b-a}, & a\le x\le b\\[4pt]
0, & \text{otherwise}
\end{cases}
$$

$$
E[X]=\frac{a+b}{2},\qquad \operatorname{Var}(X)=\frac{(b-a)^2}{12}
$$

### 5.3 Exponential 分配 (Exponential Distribution)

常用於建模壽命、等候時間，參數 $\lambda>0$（速率 rate）。

$$
f_X(x)=
\begin{cases}
\lambda e^{-\lambda x}, & x\ge 0\\
0, & x<0
\end{cases}
\qquad
F_X(x)=1-e^{-\lambda x}\;(x\ge0)
$$

$$
E[X]=\frac{1}{\lambda},\qquad \operatorname{Var}(X)=\frac{1}{\lambda^2}
$$

- **無記憶性 (Memoryless)**：$\displaystyle P(X>s+t\mid X>s)=P(X>t)$
- 指數分配是 **Gamma 分配的特例**（形狀參數 $\alpha=1$）。

### 5.4 Gaussian / Normal 分配 (常態分配)

建模「集中於某均值附近」的變數，參數為均值 $m$（或 $\mu$）與變異數 $\sigma^2$。

$$
f_X(x)=\frac{1}{\sigma\sqrt{2\pi}}\exp\!\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)
$$

$$
E[X]=\mu,\qquad \operatorname{Var}(X)=\sigma^2
$$

- **標準化 (Standardization)**：若 $X\sim\mathcal{N}(\mu,\sigma^2)$，則

$$ Z=\frac{X-\mu}{\sigma}\sim\mathcal{N}(0,1) $$

- **標準常態 cdf** $\Phi(z)=P(Z\le z)$；**尾機率函數 (Q-function)** $Q(z)=1-\Phi(z)=P(Z>z)$。
- 一般常態機率計算：

$$
P(X\le x)=\Phi\!\left(\frac{x-\mu}{\sigma}\right),\qquad
P(a<X<b)=\Phi\!\left(\frac{b-\mu}{\sigma}\right)-\Phi\!\left(\frac{a-\mu}{\sigma}\right)
$$

- cdf / Q-function 無解析解，需查表或用 `scipy.stats.norm` 數值計算。

### 5.5 Gamma 分配 (Gamma Distribution)

參數：形狀 (shape) $\alpha>0$、速率 $\lambda>0$。

$$
f_X(x)=
\begin{cases}
\dfrac{\lambda^\alpha x^{\alpha-1}e^{-\lambda x}}{\Gamma(\alpha)}, & x\ge 0\\[6pt]
0, & x<0
\end{cases}
$$

$$
E[X]=\frac{\alpha}{\lambda},\qquad \operatorname{Var}(X)=\frac{\alpha}{\lambda^2}
$$

- **Gamma 函數**：

$$ \Gamma(z)=\int_0^\infty t^{z-1}e^{-t}\,dt,\qquad
\Gamma(n)=(n-1)!\;(n\in\mathbb{N}),\qquad \Gamma\!\left(\tfrac12\right)=\sqrt{\pi} $$

- Exponential 為 $\alpha=1$ 的特例；多個獨立 Exponential($\lambda$) 之和為 Gamma($\alpha=k,\lambda$)。

### 5.6 聯合高斯 (Pairs of Jointly Gaussian RVs)

若 $X_1,X_2$ 為聯合高斯，其聯合 pdf 為以 $(m_1,m_2)$ 為中心的鐘形山丘，$\rho$ 為相關係數：

$$
f(x_1,x_2)=\frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^2}}
\exp\!\left[
-\frac{1}{2(1-\rho^2)}
\left(
\frac{(x_1-m_1)^2}{\sigma_1^2}
-2\rho\frac{(x_1-m_1)(x_2-m_2)}{\sigma_1\sigma_2}
+\frac{(x_2-m_2)^2}{\sigma_2^2}
\right)
\right]
$$

### 5.7 Chebyshev 不等式與中央極限定理

- **Chebyshev 不等式 (Chebyshev's Inequality)**：

$$ P(|X-\mu|\ge k\sigma)\le \frac{1}{k^2}
\quad\text{或}\quad
P(|X-\mu|\ge \varepsilon)\le \frac{\sigma^2}{\varepsilon^2} $$

對**任意**分佈皆成立（不需常態假設）。

- **中央極限定理 (Central Limit Theorem, CLT)**：
  若 $X_1,\dots,X_n$ 為 i.i.d.，均值 $\mu$、變異數 $\sigma^2$，則樣本平均

$$ \bar{X}_n=\frac{1}{n}\sum_{i=1}^n X_i $$

在 $n$ 夠大時近似常態：

$$ \frac{\bar{X}_n-\mu}{\sigma/\sqrt{n}}\;\xrightarrow{d}\;\mathcal{N}(0,1) $$

### 5.8 例題詳解

**例題 A — 機器壽命（Exponential）**
機器壽命 $X$（年）服從指數分配，參數 $\lambda=0.5$。

- (a) 壽命超過 4 年的機率：

$$ P(X>4)=\int_4^\infty 0.5e^{-0.5x}\,dx=e^{-0.5\times4}=e^{-2}\approx 0.1353 $$

- (b) 已知已運轉 4 年，再續用至少 1 年的機率（無記憶性）：

$$ P(X>5\mid X>4)=P(X>1)=e^{-0.5\times1}=e^{-0.5}\approx 0.6065 $$

**例題 B — 通訊雜訊（Gaussian）**
通訊系統 $Y=av+N$，其中雜訊 $N\sim\mathcal{N}(m=0,\sigma=2)$。求最小 $v$ 使 $P(Y<0)\le 10^{-6}$。

$$
\begin{aligned}
P(Y<0)&=P(av+N<0)=P(N<-av)\\
&=\Phi\!\left(\frac{-av-0}{2}\right)=\Phi\!\left(-\frac{av}{2}\right)\le 10^{-6}
\end{aligned}
$$

由 $Q^{-1}(10^{-6})\approx 4.753$，得

$$ \frac{av}{2}\ge Q^{-1}(10^{-6})\approx 4.753
\;\Longrightarrow\;
v\ge \frac{2\times4.753}{a}\approx \frac{9.51}{a} $$

---

## 附錄：分配速查表

| 分配 | 參數 | pmf / pdf | 期望 $E[X]$ | 變異數 $\operatorname{Var}(X)$ | 關鍵性質 |
| --- | --- | --- | --- | --- | --- |
| Bernoulli | $p$ | $p^k(1-p)^{1-k},\;k\in\{0,1\}$ | $p$ | $p(1-p)$ | 單次試驗 |
| Binomial | $n,p$ | $\binom{n}{k}p^k(1-p)^{n-k}$ | $np$ | $np(1-p)$ | $n$ 次獨立 Bernoulli 和 |
| Geometric | $p$ | $(1-p)^{k-1}p,\;k\ge1$ | $1/p$ | $(1-p)/p^2$ | 無記憶 |
| Poisson | $\lambda$ | $e^{-\lambda}\lambda^k/k!$ | $\lambda$ | $\lambda$ | 二項近似 ($\lambda=np$) |
| Uniform | $a,b$ | $1/(b-a),\;a\le x\le b$ | $(a+b)/2$ | $(b-a)^2/12$ | 等可能 |
| Exponential | $\lambda$ | $\lambda e^{-\lambda x},\;x\ge0$ | $1/\lambda$ | $1/\lambda^2$ | 無記憶；Gamma($\alpha=1$) |
| Gaussian | $\mu,\sigma^2$ | $\frac{1}{\sigma\sqrt{2\pi}}e^{-(x-\mu)^2/2\sigma^2}$ | $\mu$ | $\sigma^2$ | 標準化 $Z=(X-\mu)/\sigma$ |
| Gamma | $\alpha,\lambda$ | $\lambda^\alpha x^{\alpha-1}e^{-\lambda x}/\Gamma(\alpha)$ | $\alpha/\lambda$ | $\alpha/\lambda^2$ | 多個 Exponential 和 |

---

> 本筆記所有例題數據與公式均對應原講義（UFUG2104），例題來源：pH 計偏差（Ch.2）、號碼球與疾病篩檢（Ch.3）、硬幣三次與位元錯誤（Ch.4）、機器壽命與通訊雜訊（Ch.5）。
