## Written Solutions of CS 224n Assignment #2

All the identities tags come from *matrix calculus notes*.

**(a)** $- \sum_{w \in Vocab} y_w \log(\hat{y}_w) = -0\times\log(\hat{y_1})-0\times\log(\hat{y_2}) - \dots -1\times\log(\hat{y_o}) - \dots - 0\times \log(\hat{y_V})=-\log(\hat{y_o})​$ 

**(b)** Follow the convention of codes, $U \in \mathbb{R}^{V\times N}$, $V$ is the vocabulary size, $N$ is the length of embedding. $y,\hat{y},v_c,$ are row vectors. 

From identity $3(7)$ we get:
$$
\frac{\partial J}{\partial \theta} = \hat{y} - y \tag1
$$
From identity $3(2)$ we get:
$$
\frac{\partial \theta}{\partial v_c} = U \tag{2}
$$
Combine $(1)$ and $(2)​$ :
$$
\frac{\partial J}{\partial v_c} = (\hat{y} - y)U \in \mathbb{R}^{1 \times N},\text{same shape with } v_c
$$
**(c)**

From identity $3(5)$ we get:
$$
\frac{\partial J}{\partial U} = (\hat{y} - y)v_c \in \mathbb{R}^{V \times N} ,\text{same shape with } U \tag{3}
$$
then 
$$
\frac{\partial J}{\partial u_w} = \text{the } w \text{ row of } \frac{\partial J}{\partial U}
$$
The computing of $J$ involves all the rows of $U$,  so it doesn't matter whether $w = o$.



**(d)** 
$$
\frac{\partial \sigma(x)}{\partial x} = \sigma(x)\sigma(1-\sigma(x))
$$
**(e)**
$$
s1 = u_o^{\intercal}v_c, s2 = u_k^{\intercal}v_c
$$

$$
\frac{\partial J}{\partial v_c} = (\sigma(s1)-1))u_o + \sum_k (1-\sigma(-s2)) u_k
$$

$$
 \frac{\partial J}{\partial u_o} = (\sigma(s1)-1))v_c
$$

$$
\frac{\partial J}{\partial u_k} = (1-\sigma(-s2)) v_c
$$

**(f)**

(i)
$$
\frac{\partial J}{\partial U} = \sum_j\frac{\partial J(v_c,w_{t+j},U)}{\partial U}
$$
(ii)
$$
\frac{\partial J}{\partial v_c} = \sum_j\frac{\partial J(v_c,w_{t+j},U)}{\partial v_c}
$$
(iii)

$0$. For the vecotrs that are not the center word, they do not participate in the updata of parameters, they have no influence on the loss. So the answer is $0$.



