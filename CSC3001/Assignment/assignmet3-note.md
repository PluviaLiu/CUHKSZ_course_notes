# Q1

No. Suppose a simple graph $G$ has $n$ vertices. The possible degrees are $\{0, 1, 2, \dots, n-1\}$. If all vertices have different degrees, each value in the set must be assigned to exactly one vertex. This implies $G$ contains:

1. A vertex with degree $0$ (isolated, connected to no one).
2. A vertex with degree $n-1$ (connected to all other $n-1$ vertices).
    These two conditions are mutually exclusive.
    Thus, at least two vertices must have the same degree.

# Q2

Suppose $G$ is a simple graph with $n$ vertices that is **not** connected. To maximize edges in a disconnected graph, $G$ should have two components that are complete graphs, $K_k$ and $K_{n-k}$, for some $1 \le k \le n-1$. The total number of edges $m$ is:

$$m \le \binom{k}{2} + \binom{n-k}{2} = \frac{k(k-1) + (n-k)(n-k-1)}{2}$$

The function $f(k) = k^2 - nk + \frac{n^2-n}{2}$ is maximized at the boundaries $k=1$ or $k=n-1$:

$$m \le \binom{1}{2} + \binom{n-1}{2} = 0 + \frac{(n-1)(n-2)}{2}$$

Therefore, if $m > \frac{(n-1)(n-2)}{2}$, $G$ must be connected.






# Q3

To prove $42 \mid (n^7 - n)$, we show divisibility by 2, 3, and 7.

1. **Mod 7**: By Fermat's Little Theorem, $n^7 \equiv n \pmod 7$, so $n^7 - n \equiv 0 \pmod 7$.
2. **Mod 3**: $n^7 - n = n(n^6 - 1) = n(n^2 - 1)(n^4 + n^2 + 1) = (n-1)n(n+1)(n^4 + n^2 + 1)$.
    Since $(n-1)n(n+1)$ is a product of three consecutive integers, it is divisible by $3! = 6$, so $n^7 - n \equiv 0 \pmod 3$.
3. **Mod 2**: $n^7$ and $n$ always have the same parity, so $n^7 - n \equiv 0 \pmod 2$. 
	Since $\text{gcd}(2, 3, 7) = 1$, $n^7 - n$ is divisible by $2 \cdot 3 \cdot 7 = 42$.


# Q4

We have $\frac{(kp)!}{k! [cite_start]\cdot p^k} \pmod p$ for prime $p > k$. Expand $(kp)!$ by grouping multiples of $p$:

$$(kp)! = \left( \prod_{j=1}^{k} jp \right) \cdot \left( \prod_{j=0}^{k-1} \prod_{i=1}^{p-1} (jp + i) \right) = p^k k! \cdot \prod_{j=0}^{k-1} \prod_{i=1}^{p-1} (jp + i)$$

Substitute into the expression:

$$\frac{p^k k! \prod_{j=0}^{k-1} \prod_{i=1}^{p-1} (jp + i)}{k! p^k} = \prod_{j=0}^{k-1} \prod_{i=1}^{p-1} (jp + i)$$

Modulo $p$, this simplifies to:

$$\prod_{j=0}^{k-1} (p-1)! \equiv ((p-1)!)^k \pmod p$$

By Wilson's Theorem, $(p-1)! \equiv -1 \pmod p$. Thus, the expression is $(-1)^k \pmod p$.

# Q5

System:

1. $x \equiv 5 \pmod 6$ 2. $x \equiv 7 \pmod{10}$ 3. $x \equiv 2 \pmod{15}$

Decompose the moduli:

- From (1): $x \equiv 1 \pmod 2$ and $x \equiv 2 \pmod 3$.
- From (2): $x \equiv 1 \pmod 2$ and $x \equiv 2 \pmod 5$.
- From (3): $x \equiv 2 \pmod 3$ and $x \equiv 2 \pmod 5$.

The conditions are consistent: $x \equiv 1 \pmod 2, x \equiv 2 \pmod 3, x \equiv 2 \pmod 5$.

Since $\text{gcd}(3, 5) = 1$, $x \equiv 2 \pmod 3$ and $x \equiv 2 \pmod 5 \implies x \equiv 2 \pmod{15}$.

Let $x = 15k + 2$.

Substitute into $x \equiv 1 \pmod 2$:

$15k + 2 \equiv 1 \pmod 2 \implies k \equiv 1 \pmod 2$.

Take $k=1$, then $x = 15(1) + 2 = 17$.

The general solution is $x \equiv 17 \pmod{30}$.



# Q6

**(a)** 
$K_{m,n}$ has an Eulerian cycle iff all vertex degrees are even. 
Degrees are $n$ (for $m$ vertices) and $m$ (for $n$ vertices). 
Thus, $m$ and $n$ must both be even.

**(b)** 
$K_{m,n}$ has an Eulerian path iff the number of odd-degree vertices is 0 or 2.

- **0 odd vertices**: $m, n$ are both even.
- **2 odd vertices
    - If $n$ is odd, then all $m$ vertices in the first set are odd. For there to be exactly 2 odd vertices, $m=2$.
    - If $m$ is odd, then all $n$ vertices in the second set are odd. For there to be exactly 2 odd vertices, $n=2$.
    - If both $m, n$ are odd, then $m+n$ vertices are odd. $m+n=2$ implies $m=1, n=1$.



# Q7

**( $\Rightarrow$ )** Suppose $G$ is $k$-extendable. 
If there  exists $X \subseteq A$ such that $|N(X)| < |X| + k$ and $N(X) \neq B$, one could choose a matching $M$ of size $k$ that "uses up" too many neighbors of $X$, leaving $X$ with fewer available neighbors than vertices in the remaining graph $G-M$. 
 This violates the existence of a perfect matching, contradicting $k$-extendability.

**( $\Leftarrow$ )** Assume $|N(X)| \ge |X| + k$ or $N(X) = B$ for all $X \subseteq A$. Let $M$ be any matching of size $k$. Let $G' = G - V(M)$. For any $X \subseteq A \cap V(G')$:

- If $N_G(X) = B$, then $|N_{G'}(X)| = |B| - k = (n - k) \ge |X|$.
- If $|N_G(X)| \ge |X| + k$, then since at most $k$ vertices of $N_G(X)$ are removed by $M$, we have $|N_{G'}(X)| \ge (|X| + k) - k = |X|$.
    By Hall's Theorem, $G'$ has a perfect matching, meaning $M$ is contained in a perfect matching of $G$. Thus $G$ is $k$-extendable.