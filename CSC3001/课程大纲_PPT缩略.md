
### **命题逻辑 (Propositional Logic)**

---

#### **1. 数学证明 (Mathematical Proof)**

##### ① 定义与概念 (Definitions & Concepts)
1.  **数学证明 (Mathematical Proof):** 从一组公理 (Axioms) 出发，通过逻辑推导 (Logic Deduction) 得出定理 (Theorems) 的真实性的严谨过程。
2.  **公理 (Axiom):** 被认为是理所当然为真的陈述，是证明的起点。

##### ② 公式与方程 (Formulas & Equations)
1.  **勾股定理 (Pythagorean Theorem):** 对于直角三角形，两直角边$a, b$与斜边$c$满足: $a^2 + b^2 = c^2$.
2.  **欧几里得五大公理 (Euclid's Five Axioms):**
    1.  任意两点可作一直线。
    2.  直线可无限延长。
    3.  任意点为圆心，任意半径可作一圆。
    4.  所有直角都相等。
    5.  平行公设 (Parallel Postulate): 若两直线与第三条直线相交，同侧内角之和小于两直角，则此两直线无限延长后必相交于该侧。

##### ③ 常见错误与混淆 (Common Mistakes & Confusions)
1.  **坏证明 (Bad Proof):** 依赖于视觉错觉或不严谨的几何重排可能导致错误结论。例如，通过错误的图形拼接“证明”65=63，其根源在于小三角形的斜率不同 ($2:5 \neq 3:8$)，拼接后存在微小空隙。
2.  **直觉 vs 严谨 (Intuition vs Rigor):** 直观上“显而易见”的结论需要严格的逻辑证明来确保其正确性。

---

#### **2. 逻辑基础与基本算子 (Logic Basics & Operators)**

##### ① 定义与概念 (Definitions & Concepts)
1.  **命题 (Statement / Proposition):** 一个可以被判断为**真 (True, T)** 或**假 (False, F)** 的陈述句。
    -   **非命题:** 含有未定变量的表达式 (如 $x+y>0$) 不是命题，因其真值取决于变量。
2.  **逻辑算子 (Logic Operators):** 用于从已有命题构造新命题的符号。
3.  **真值表 (Truth Table):** 展示逻辑运算在所有可能的输入真值组合下输出结果的表格。
4.  **复合命题 (Compound Statement):** 由简单命题和逻辑算子构成的命题。

##### ② 公式与方程 (Formulas & Equations)
1.  **否定 (NOT / Negation):** $\neg p$ 或 $\bar{p}$

| $p$ | $\neg p$ |
| :-: | :------: |
|  T  |    F     |
|  F  |    T     |
2.  **合取 (AND / Conjunction):** $p \land q$

| $p$ | $q$ | $p \land q$ |
| :-: | :-: | :---------: |
|  T  |  T  |      T      |
|  T  |  F  |      F      |
|  F  |  T  |      F      |
|  F  |  F  |      F      |
2.  **析取 (OR / Disjunction):** $p \lor q$

| $p$ | $q$ | $p \lor q$ |
| :-: | :-: | :--------: |
|  T  |  T  |     T      |
|  T  |  F  |     T      |
|  F  |  T  |     T      |
|  F  |  F  |     F      |
3.  **异或 (XOR / Exclusive-OR):** $p \oplus q$ (当 $p$ 和 $q$ 真值不同时为真)

| $p$ | $q$ | $p \oplus q$ |
|:---:|:---:|:---:|
| T   | T   | F   |
| T   | F   | T   |
| F   | T   | T   |
| F   | F   | F   |
4.  **多数表决 (Majority):** $M(p, q, r)$ (当 $p, q, r$ 中至少有两个为真时为真)




#### **3. 从基本算子构造任意算子 (Constructing Any Operator)**

##### ① 定义与概念 (Definitions & Concepts)
1.  **功能完备性 (Functional Completeness):** 任何逻辑函数 (真值表) 都可以用 $\{\land, \lor, \neg\}$ 的组合来表示。

##### ② 公式与算法 (Formulas & Algorithms)
1.  **方法1: 析取范式 (Disjunctive Normal Form - DNF)**
    -   关注真值表中结果为 **T** 的行。
    -   为每个 T 行，写出一个**合取**式 (AND)，使得该式仅在这一行输入时为 T。 (变量为 T 则用原变量，为 F 则用其否定)。
    -   将所有 T 行对应的合取式用**析取** (OR) 连接起来。
    -   例: $p \oplus q \equiv (p \land \neg q) \lor (\neg p \land q)$
2.  **方法2: 合取范式 (Conjunctive Normal Form - CNF)**
    -   关注真值表中结果为 **F** 的行。
    -   为每个 F 行，写出一个**合取**式，并对其整体**否定**。
    -   将所有 F 行对应的否定式用**合取** (AND) 连接起来。
    -   例: $p \oplus q \equiv \neg(p \land q) \land \neg(\neg p \land \neg q)$

---

#### **4. 逻辑等价与德摩根定律 (Logical Equivalence & De Morgan's Law)**

##### ① 定义与概念 (Definitions & Concepts)
1.  **逻辑等价 (Logical Equivalence, $\equiv$):** 两个命题有完全相同的真值表。
2.  **重言式 (Tautology, $t$):** 永为真的命题 (如 $p \lor \neg p$)。
3.  **矛盾式 (Contradiction, $c$):** 永为假的命题 (如 $p \land \neg p$)。

##### ② 公式与方程 (Formulas & Equations)
1.  **德摩根定律 (De Morgan's Laws):**
    -   $\neg(p \land q) \equiv \neg p \lor \neg q$
    -   $\neg(p \lor q) \equiv \neg p \land \neg q$
2.  **其它重要逻辑定律:**
    -   **交换律 (Commutative):** $p \land q \equiv q \land p$; $p \lor q \equiv q \lor p$
    -   **结合律 (Associative):** $(p \land q) \land r \equiv p \land (q \land r)$
    -   **分配律 (Distributive):** $p \land (q \lor r) \equiv (p \land q) \lor (p \land r)$; $p \lor (q \land r) \equiv (p \lor q) \land (p \lor r)$
    -   **同一律 (Identity):** $p \land t \equiv p$; $p \lor c \equiv p$
    -   **否定律 (Negation):** $p \lor \neg p \equiv t$; $p \land \neg p \equiv c$
    -   **双重否定 (Double Negative):** $\neg(\neg p) \equiv p$
    -   **幂等律 (Idempotent):** $p \land p \equiv p$; $p \lor p \equiv p$
    -   **吸收律 (Absorption):** $p \lor (p \land q) \equiv p$; $p \land (p \lor q) \equiv p$

##### ③ 常见错误与混淆 (Common Mistakes & Confusions)
1.  **否定合取/析取:** $\neg(p \land q)$ 不等于 $\neg p \land \neg q$。否定时，内部算子 $\land$ 变为 $\lor$, $\lor$ 变为 $\land$。

##### ④ 关键点与附加说明 (Key Points & Additional Notes)
1.  **公式化简 (Simplifying Statement):** 应用逻辑定律可以化简复杂的逻辑表达式。
2.  **可满足性问题 (Satisfiability Problem - SAT):** 判断一个给定的命题公式是否是矛盾式是一个计算机科学中的核心难题。

---

#### **5. 条件语句 (Conditional Statement)**

##### ① 定义与概念 (Definitions & Concepts)
1.  **条件语句 (Conditional / Implication):** "if p then q"，记作 $p \rightarrow q$。
    -   $p$: 前提 (hypothesis / antecedent)
    -   $q$: 结论 (conclusion / consequent)
2.  **逆否命题 (Contrapositive):** "if $\neg q$ then $\neg p$" ($\neg q \rightarrow \neg p$)。一个条件语句与其逆否命题逻辑等价。
3.  **充分条件 (Sufficient Condition):** $S$ 是 $R$ 的充分条件 $\iff S \rightarrow R$。
4.  **必要条件 (Necessary Condition):** $S$ 是 $R$ 的必要条件 $\iff R \rightarrow S$。
5.  **充分必要条件 (Iff):** "p if and only if q"，记作 $p \leftrightarrow q$。

##### ② 公式与方程 (Formulas & Equations)
1.  **条件语句真值表:** $p \rightarrow q$ 仅在 $p$ 为 T 且 $q$ 为 F 时为 F。

| $p$ | $q$ | $p \rightarrow q$ |
| :-: | :-: | :---------------: |
|  T  |  T  |         T         |
|  T  |  F  |         F         |
|  F  |  T  |         T         |
|  F  |  F  |         T         |
2.  **等价形式 (Equivalences):**
    -   $p \rightarrow q \equiv \neg p \lor q$
    -   $p \rightarrow q \equiv \neg q \rightarrow \neg p$ (Contrapositive)
3.  **否定形式 (Negation):** $\neg(p \rightarrow q) \equiv p \land \neg q$
4.  **双条件 (Biconditional):** $p \leftrightarrow q \equiv (p \rightarrow q) \land (q \rightarrow p)$

##### ③ 常见错误与混淆 (Common Mistakes & Confusions)
1.  **"if" vs "only if":**
    -   "R **if** S" $\implies S \rightarrow R$
    -   "R **only if** S" $\implies R \rightarrow S$
2.  **日常语言 vs 逻辑语言:** 日常对话中的 "if...then..." 可能暗含双向关系，但在逻辑中是单向的。

---

#### **6. 论证 (Arguments)**

##### ① 定义与概念 (Definitions & Concepts)
1.  **论证 (Argument):** 一系列命题，其中最后一个为**结论 (Conclusion)**，其余为**前提 (Assumptions / Hypothesis)**。
2.  **有效论证 (Valid Argument):** 当所有前提都为真时，结论**必然**为真。有效性取决于其**形式**，而非内容。

##### ② 公式与方程 (有效论证形式 - Valid Argument Forms)
1.  **肯定前件式 (Modus Ponens):** $p \rightarrow q, p \therefore q$
2.  **否定后件式 (Modus Tollens):** $p \rightarrow q, \neg q \therefore \neg p$
3.  **假言三段论 (Transitivity):** $p \rightarrow q, q \rightarrow r \therefore p \rightarrow r$
4.  **析取三段论 (Elimination):** $p \lor q, \neg p \therefore q$
5.  **归纳 (Generalization):** $p \therefore p \lor q$
6.  **简化 (Specialization):** $p \land q \therefore p$
7.  **合取 (Conjunction):** $p, q \therefore p \land q$
8.  **分情况证明 (Proof by Cases):** $p \lor q, p \rightarrow r, q \rightarrow r \therefore r$
9.  **反证法 (Contradiction Rule):** $\neg p \rightarrow c \therefore p$

##### ③ 常见错误与混淆 (逻辑谬误 - Logical Fallacies)
1.  **肯定后件谬误 (Fallacy of Affirming the Consequent):** $p \rightarrow q, q \therefore p$ (无效)
    -   例: "如果你是鱼，你就要喝水。你喝水，所以你是鱼。" (错误)
2.  **否定前件谬误 (Fallacy of Denying the Antecedent):** $p \rightarrow q, \neg p \therefore \neg q$ (无效)
    -   例: "如果你是鱼，你就要喝水。你不是鱼，所以你不喝水。" (错误)

##### ④ 关键点与附加说明 (Key Points & Additional Notes)
1.  **有效性 vs 真值:**
    -   有效论证 + 真前提 $\implies$ 真结论。
    -   有效论证 + 假前提 $\implies$ 结论真假不定。
    -   无效论证 $\implies$ 结论真假不定 (即使前提和结论都为真)。
2.  **反例法 (Counterexample):** 证明一个论证无效，只需找到一个使所有前提为 T 但结论为 F 的情况。

=== 文档 3: LN2.1 - Sets.pdf ===

### **模块1: 集合基础 (Basic Sets)**

#### ① 定义与概念 (Definitions & Concepts)
1.  **集合 (Set)**: 无序 (unordered)、互异 (distinct) 的元素 (element/member) 构成的集合 (collection)。
    *   符号 (Notation):
        *   列举法 (Roster Method): `{a, b, c}`
        *   描述法 (Set-Builder): `{x ∈ A | P(x)}`
    *   `S = {2, 3, 5, 7}` 等价于 `S = {7, 5, 3, 2}` (无序性)。
    *   `{2, 3, 5, 3, 7}` 不是合法集合 (元素需互异)。
2.  **经典集合 (Classical Sets)**:
    *   $\mathbb{Z}$: 整数集 (Integers)
    *   $\mathbb{Z}^+ / \mathbb{Z}^-$: 正/负整数集
    *   $\mathbb{N}$: 非负整数集 (Natural numbers, 0, 1, 2, ...)
    *   $\mathbb{R}$: 实数集 (Real numbers)
    *   $\mathbb{Q}$: 有理数集 (Rational numbers)
    *   $\mathbb{C}$: 复数集 (Complex numbers)
3.  **基数 (Cardinality)**: 集合 `S` 的大小, 记作 `|S|`, 表示其中元素的数量。
4.  **隶属关系 (Membership)**:
    *   `x ∈ A`: x 是 A 的一个元素。
    *   `x ∉ A`: x 不是 A 的元素。
5.  **子集关系 (Subset Relations)**:
    *   **子集 (Subset)**: `A ⊆ B ⇔ ∀x(x ∈ A → x ∈ B)`。
    *   **真子集 (Proper Subset)**: `A ⊂ B ⇔ (A ⊆ B) ∧ (A ≠ B)`。
    *   **集合相等 (Set Equality)**: `A = B ⇔ (A ⊆ B) ∧ (B ⊆ A)`。
6.  **幂集 (Power Set)**: `pow(A)` 或 `P(A)`，是集合 `A` 的所有子集的集合。
    *   例: `pow({a,b}) = {∅, {a}, {b}, {a,b}}`。

#### ② 公式与方程 (Formulas & Equations)
1.  **幂集基数**: $|pow(A)| = 2^{|A|}$

#### ③ 常见错误与混淆 (Common Mistakes & Confusions)
1.  **`∈` vs `⊆`**: `a` 是 `{a, b}` 的元素 (`a ∈ {a, b}`), `{a}` 是 `{a, b}` 的子集 (`{a} ⊆ {a, b}`)。
2.  **元素可以是集合**: `S = {{a}, a}` 是一个合法集合，它有两个元素：集合 `{a}` 和元素 `a`。
3.  **`⊆` vs `⊂`**: 任何集合都是自身的子集 (`A ⊆ A`)，但不是自身的真子集。

#### ④ 关键点与补充 (Key Points & Additional Notes)
1.  **空集 (Empty Set)**: `∅` 或 `{}`.
    *   `∅` 是任何集合的子集。
    *   `|∅| = 0`。

### **模块2: 集合运算 (Operations on Sets)**

#### ① 定义与概念 (Definitions & Concepts)
1.  **全集 (Universal Set)**: `U`, 包含当前讨论范围内所有元素的集合。
2.  **交集 (Intersection)**: `A ∩ B = {x | x ∈ A ∧ x ∈ B}`。
3.  **并集 (Union)**: `A ∪ B = {x | x ∈ A ∨ x ∈ B}`。
4.  **补集 (Complement)**: `Ā = A^c = {x ∈ U | x ∉ A}`。
5.  **差集 (Difference)**: `A - B = {x | x ∈ A ∧ x ∉ B}`。
6.  **不相交 (Disjoint)**: 若 `A ∩ B = ∅`，则称 A 和 B 不相交。
7.  **划分 (Partition)**: 一组非空子集 `{A₁, A₂, ..., Aₙ}` 是集合 `A` 的一个划分，当且仅当:
    *   `A = A₁ ∪ A₂ ∪ ... ∪ Aₙ` (覆盖全集)
    *   `Aᵢ ∩ Aⱼ = ∅` (对所有 `i ≠ j`) (两两不交)
8.  **笛卡尔积 (Cartesian Product)**: `A × B = {(a,b) | a ∈ A, b ∈ B}`。元素是 **有序对 (Ordered Pairs)**。
9.  **索引集运算 (Indexed Collections)**:
    *   $\bigcup_{i=0}^{n} A_{i} = \{x \in U \mid \exists i \in \{0..n\}, x \in A_{i}\}$
    *   $\bigcap_{i=0}^{n} A_{i} = \{x \in U \mid \forall i \in \{0..n\}, x \in A_{i}\}$

#### ② 公式与方程 (Formulas & Equations)
1.  **容斥原理 (Inclusion-Exclusion Principle)**: `|A ∪ B| = |A| + |B| - |A ∩ B|`。
2.  **差集基数**: `|A - B| = |A| - |A ∩ B|`。
3.  **笛卡尔积基数**: $|A_1 \times A_2 \times \dots \times A_k| = |A_1| \cdot |A_2| \cdot \dots \cdot |A_k|$。
4.  **子集与补集关系**: `If A ⊆ B, then B̄ ⊆ Ā`。

#### ③ 常见错误与混淆 (Common Mistakes & Confusions)
1.  **划分的条件**: 必须同时满足“覆盖全集”和“两两不交”。
    *   例: `A₁={x∈Z|x>0}, A₂={x∈Z|x<0}` 不是 `Z` 的划分, 因 `0` 未被覆盖。
2.  **笛卡尔积的顺序**: `A × B ≠ B × A` (除非 `A=B` 或 `A=∅` 或 `B=∅`)，因为有序对 `(a,b) ≠ (b,a)`。

#### ④ 关键点与补充 (Key Points & Additional Notes)
1.  **差集与交集**: `A - B = A ∩ B^c`。
2.  **索引集运算示例**:
    *   令 $A_i = (-\frac{1}{i}, \frac{1}{i})$ for $i \in \mathbb{Z}^+$
    *   $\bigcup_{i=1}^{\infty} A_i = (-1, 1)$
    *   $\bigcap_{i=1}^{\infty} A_i = \{0\}$

### **模块3: 集合恒等式 (Set Identities)**

#### ① 定义与概念 (Definitions & Concepts)
(本模块主要为公式)

#### ② 公式与方程 (Formulas & Equations)
1.  **交换律 (Commutative Law)**: `A ∪ B = B ∪ A`; `A ∩ B = B ∩ A`。
2.  **结合律 (Associative Law)**: `(A ∪ B) ∪ C = A ∪ (B ∪ C)`; `(A ∩ B) ∩ C = A ∩ (B ∩ C)`。
3.  **分配律 (Distributive Law)**:
    *   `A ∪ (B ∩ C) = (A ∪ B) ∩ (A ∪ C)`
    *   `A ∩ (B ∪ C) = (A ∩ B) ∪ (A ∩ C)`
4.  **同一律 (Identity Law)**: `A ∪ ∅ = A`; `A ∩ U = A`。
5.  **补集律 (Complement Law)**: `A ∪ A^c = U`; `A ∩ A^c = ∅`。
6.  **德摩根定律 (De Morgan's Law)**:
    *   `(A ∪ B)^c = A^c ∩ B^c`
    *   `(A ∩ B)^c = A^c ∪ B^c`
    *   推广: $(\bigcup A_i)^c = \bigcap A_i^c$; $(\bigcap A_i)^c = \bigcup A_i^c$。

#### ③ 常见错误与混淆 (Common Mistakes & Confusions)
1.  **德摩根定律**: 易忘记将 `∪` 转换为 `∩` (反之亦然)。
2.  **证明 (Proof) vs 证伪 (Disproof)**:
    *   **证明**: 需严格推导。方法：代数证明法、定义证明法（证明双向包含 `LHS ⊆ RHS` 和 `RHS ⊆ LHS`）。
    *   **证伪**: 仅需一个反例 (counterexample)。
    *   例: `(A - B) ∪ (B - C) = A - C` 是错误的。

#### ④ 关键点与补充 (Key Points & Additional Notes)
1.  **文氏图 (Venn Diagram)**: 有助于理解和发现反例，但不能作为严格证明。
2.  **重要恒等式**: `(A ∩ B) × C = (A × C) ∩ (B × C)`。

### **模块4: 悖论与停机问题 (Paradoxes & Halting Problem)**

#### ① 定义与概念 (Definitions & Concepts)
1.  **罗素悖论 (Russell's Paradox)**: 定义集合 `W = {S | S 是一个集合且 S ∉ S}`。
    *   提问: `W ∈ W`?
    *   若 `W ∈ W`，则 W 满足 `S ∉ S` 的性质，即 `W ∉ W`，矛盾。
    *   若 `W ∉ W`，则 W 满足 `S ∉ S` 的性质，应被包含在 W 中，即 `W ∈ W`，矛盾。
2.  **理发师悖论 (Barber's Paradox)**: 罗素悖论的通俗版本。“一个理发师只给所有不自己刮胡子的人刮胡子”，他该不该给自己刮胡子？
3.  **停机问题 (Halting Problem)**: 是否存在一个通用程序 `H`，对于任意给定的程序 `P` 和输入 `I`，`H(P, I)` 总能（在有限时间内）判断 `P` 在输入 `I` 上是会最终停止（halt）还是会无限循环（loop forever）。
    *   结论: 这样的程序 `H` 不存在。

#### ② 公式与方程 (Formulas & Equations)
(本模块为概念性内容，无公式)

#### ③ 常见错误与混淆 (Common Mistakes & Confusions)
1.  **悖论的“解”**: 悖论的出现并非意味着逻辑本身有缺陷，而是源于不当的初始假设。
    *   **罗素悖论**: `W` 这种“集合”不允许存在。不是所有用性质描述的聚集都是集合。
    *   **理发师悖论**: 这样的理发师不存在。

#### ④ 关键点与补充 (Key Points & Additional Notes)
1.  **悖论的意义**: 揭示了朴素集合论 (Naive Set Theory) 的内在矛盾，推动了 **公理化集合论 (Axiomatic Set Theory, e.g., ZFC)** 的建立。
2.  **停机问题的不可解性 (Unsolvability)**:
    *   证明方法: **反证法 (Proof by Contradiction)**，其逻辑结构与罗素悖论相似。
    *   **证明思路**:
        1.  **假设** 存在解决停机问题的程序 `H(P, I)`。
        2.  **构造** 一个新程序 `Test(P)`:
            *   若 `H(P, P)` 返回 "halt"，则 `Test(P)` 进入无限循环。
            *   若 `H(P, P)` 返回 "loop forever"，则 `Test(P)` 立即停止。
        3.  **分析** `Test(Test)` 的行为：
            *   若 `Test(Test)` 停止，根据 `Test` 的定义，意味着 `H(Test, Test)` 返回 "loop forever"，但这又意味着 `Test(Test)` 应该无限循环。矛盾。
            *   若 `Test(Test)` 无限循环，根据 `Test` 的定义，意味着 `H(Test, Test)` 返回 "halt"，但这又意味着 `Test(Test)` 应该停止。矛盾。
        4.  **结论**: 矛盾源于初始假设，因此程序 `H` 不存在。停机问题是 **不可计算的 (uncomputable)**。

=== 文档 4: LN2.2 - First-order logic.pdf ===

### **一阶逻辑 (First-order Logic)**

#### **1. 基础概念与量词 (Basic Concepts & Quantifiers)**

##### **① 定义与概念 (Definitions & Concepts)**
1.  **谓词 (Predicate)**: 带变量的命题, 真值取决于变量的取值。
    *   例: $P(x,y): x+2=y$。当 $x=1, y=3$ 时 $P(1,3)$ 为真 (True)。
2.  **论域/定义域 (Domain)**: 变量可能取值的集合。量化语句的真值依赖于论域。
3.  **全称量词 (Universal Quantifier, $\forall$)**: 表示“对所有 (For ALL)”。
    *   $\forall x \in D, P(x)$ 意为论域 $D$ 中所有元素的 $P(x)$ 都为真。
    *   等价于一个大合取 (conjunction): $P(d_1) \land P(d_2) \land \dots$
4.  **存在量词 (Existential Quantifier, $\exists$)**: 表示“存在 (There EXISTS)”。
    *   $\exists x \in D, P(x)$ 意为论域 $D$ 中至少有一个元素的 $P(x)$ 为真。
    *   等价于一个大析取 (disjunction): $P(d_1) \lor P(d_2) \lor \dots$

##### **② 公式与应用 (Formulas & Applications)**
1.  **毕达哥拉斯定理 (Pythagorean Theorem)**:
    *   $\forall$ 直角三角形, $a^2+b^2=c^2$。
2.  **费马大定理 (Fermat's Last Theorem)**:
    *   $\forall n \in \mathbb{Z}, (n > 2) \to (\neg \exists a,b,c \in \mathbb{Z}^+ , a^n+b^n=c^n)$
3.  **哥德巴赫猜想 (Goldbach's Conjecture)**:
    *   $\forall n \in \mathbb{Z}, (\text{even}(n) \land n \ge 4) \to (\exists p,q, \text{prime}(p) \land \text{prime}(q) \land p+q=n)$
4.  **素数定义 (Prime Number Definition)**:
    *   $\text{prime}(p) \equiv (p \in \mathbb{Z} \land p > 1) \land (\forall a,b \in \mathbb{Z}^+, (p=ab) \to (a=1 \lor b=1))$
5.  **最小正整数存在**:
    *   $\exists s \in \mathbb{Z}^+ \forall x \in \mathbb{Z}^+, s \le x$
6.  **不存在最小正实数**:
    *   $\forall r \in \mathbb{R}^+ \exists x \in \mathbb{R}^+, x < r$

##### **③ 常见错误与混淆 (Common Mistakes & Confusions)**
1.  **命题逻辑 vs. 一阶逻辑 (Prop. Logic vs. FOL)**: 命题逻辑处理简单陈述句 (e.g., P, Q)，一阶逻辑处理带变量和量词的陈述句，表达能力更强。
2.  **论域的重要性**: 同一个量化语句在不同论域下真值可能不同。
    *   例: $\forall x, x^2 \ge x$。
        *   论域为整数 $\mathbb{Z}$ 时为真 (True)。
        *   论域为实数 $\mathbb{R}$ 时为假 (False)，如 $x=0.5$。

##### **④ 关键点与注释 (Key Points & Additional Notes)**
1.  将自然语言翻译为一阶逻辑的步骤:
    1.  识别条件 (Conditions)。
    2.  确定变量 (Variables)。
    3.  明确论域 (Domains)。
    4.  添加量词并调整顺序 (Add quantifiers & reconcile order)。

---

#### **2. 量词的否定与顺序 (Negation & Order of Quantifiers)**

##### **① 定义与概念 (Definitions & Concepts)**
1.  **量词否定规则**: 广义德摩根定律 (Generalized De Morgan's Law)。
    *   否定全称量词会得到存在量词。
    *   否定存在量词会得到全称量词。
2.  **量词顺序**: 混合使用 $\forall$ 和 $\exists$ 时，顺序至关重要。

##### **② 公式与方程 (Formulas & Equations)**
1.  **否定规则**:
    *   $\neg \forall x P(x) \equiv \exists x \neg P(x)$
        *   "不是所有人都..." $\equiv$ "存在有人不..."
    *   $\neg \exists x P(x) \equiv \forall x \neg P(x)$
        *   "不存在..." $\equiv$ "所有都不..."
2.  **多重量词否定**:
    *   $\neg (\exists P \forall V, \text{kill}(P, V)) \equiv \forall P \exists V, \neg \text{kill}(P, V)$
        *   "不存在一个能杀掉所有病毒的程序" $\equiv$ "对每个程序，都存在一个它杀不掉的病毒"
3.  **量词顺序**:
    *   **可交换 (Commutative)**:
        *   $\forall x \forall y P(x,y) \equiv \forall y \forall x P(x,y)$
        *   $\exists x \exists y P(x,y) \equiv \exists y \exists x P(x,y)$
    *   **不可交换 (Non-commutative)**:
        *   $\exists x \forall y P(x,y) \implies \forall y \exists x P(x,y)$ (蕴含关系，反之不成立)

##### **③ 常见错误与混淆 (Common Mistakes & Confusions)**
1.  **混淆 $\forall y \exists x$ 和 $\exists x \forall y$**:
    *   $\forall y \exists x, P(x,y)$: 对**每一个** $y$，都**存在一个** $x$ (这个 $x$ 可能依赖于 $y$)。
        *   例: 对每种病毒，都有一款杀毒软件能杀它 (可能需要多款软件)。
        *   $\forall \text{col } y, \exists \text{row } x: A[x,y]=1$ (每列至少有一个1)。
    *   $\exists x \forall y, P(x,y)$: **存在一个** $x$，它对**所有的** $y$ 都满足条件 (这个 $x$ 是通用的)。
        *   例: 有一款杀毒软件能杀掉所有病毒 (只需一款软件)。
        *   $\exists \text{row } x, \forall \text{col } y: A[x,y]=1$ (某一行全是1)。

##### **④ 关键点与注释 (Key Points & Additional Notes)**
1.  $\exists \forall$ 形式的陈述比 $\forall \exists$ 形式的陈述更强 (stronger)。
2.  对嵌套量词取非时，从外到内依次应用否定规则，改变每个量词并否定最内层的谓词。

---

#### **3. 量化论证 (Arguments with Quantified Statements)**

##### **① 定义与概念 (Definitions & Concepts)**
1.  **有效性 (Validity)**: 一个量化论证是有效的，当前提 (assumptions) 为真时，结论 (conclusion) 必为真。
2.  **重言式 (Tautology)**: 在任何论域和谓词解释下都为真的语句。

##### **② 推理规则 (Rules of Inference)**
1.  **全称实例化 (Universal Instantiation)**:
    *   $\forall x, P(x) \implies \therefore P(a)$ (其中 a 是论域中任意特定元素)
2.  **全称肯定前件式 (Universal Modus Ponens)**:
    *   $\forall x, (P(x) \to Q(x))$
    *   $P(a)$
    *   $\therefore Q(a)$
3.  **全称否定后件式 (Universal Modus Tollens)**:
    *   $\forall x, (P(x) \to Q(x))$
    *   $\neg Q(a)$
    *   $\therefore \neg P(a)$
4.  **全称推广 (Universal Generalization)**:
    *   $\frac{A \to R(c)}{A \to \forall x, R(x)}$
    *   条件: $c$ 是任意的 (arbitrary)，且独立于 $A$。

##### **③ 常见错误与混淆 (Common Mistakes & Confusions)**
1.  **分配律的误用 (Misusing Distributive Law)**:
    *   **无效 (Invalid)**: $\forall z [Q(z) \lor P(z)] \to [\forall x Q(x) \lor \forall y P(y)]$
        *   **反例 (Counterexample)**:
            *   论域 (Domain): 整数 $\mathbb{Z}$
            *   $Q(z): z$ 是偶数 (even)
            *   $P(z): z$ 是奇数 (odd)
            *   前提 $\forall z [Q(z) \lor P(z)]$ 为真 (所有整数非偶即奇)。
            *   结论 $[\forall x Q(x) \lor \forall y P(y)]$ 为假 (不是所有整数都是偶数，也不是所有整数都是奇数)。
    *   **有效 (Valid)**: $\forall z [Q(z) \land P(z)] \to [\forall x Q(x) \land \forall y P(y)]$

##### **④ 关键点与注释 (Key Points & Additional Notes)**
1.  证明一个论证无效，只需给出一个反例 (counterexample)，包括具体的论域 (domain) 和谓词 (predicate)。
2.  全称推广是数学归纳法等证明方法的基础。

=== 文档 5: LN3 - Methods of proofs.pdf ===

### **证明方法 (Methods of Proofs)**

#### **0. 基础定义 (Basic Definitions)**
1.  **偶数 (Even Number)**: 若整数 $n$ 存在整数 $k$ 使得 $n = 2k$.
2.  **奇数 (Odd Number)**: 若整数 $n$ 存在整数 $k$ 使得 $n = 2k+1$.
3.  **有理数 (Rational Number)**: 若实数 $r$ 存在整数 $a, b$ ($b \ne 0$) 使得 $r = \frac{a}{b}$.
4.  **无理数 (Irrational Number)**: 非有理数的实数.
5.  **完全平方数 (Perfect Square)**: 若整数 $m$ 存在整数 $a$ 使得 $m = a^2$.

---

### **1. 直接证明 (Direct Proof)**
#### ① 定义与概念
*   **目标 (Goal)**: 证明蕴含式 $P \to Q$.
*   **逻辑 (Logic)**: 假设 $P$ 为真, 通过一系列逻辑推导, 证明 $Q$ 也为真.

#### ② 方法与示例 (Method & Examples)
1.  **方法**: Assume $P \Rightarrow \text{Step 1} \Rightarrow \text{Step 2} \Rightarrow \dots \Rightarrow Q$.
2.  **示例1**: 两个偶数之和为偶数.
    *   **证明**: 设 $x=2m, y=2n$. 则 $x+y = 2m+2n = 2(m+n)$. 由于 $m+n$ 是整数, 故 $x+y$ 是偶数.
3.  **示例2**: 两个奇数之积为奇数.
    *   **证明**: 设 $x=2m+1, y=2n+1$. 则 $xy = (2m+1)(2n+1) = 4mn+2m+2n+1 = 2(2mn+m+n)+1$. 由于 $2mn+m+n$ 是整数, 故 $xy$ 是奇数.
4.  **示例3**: 若 $m, n$ 是完全平方数, 则 $m+n+2\sqrt{mn}$ 也是完全平方数.
    *   **证明**: 设 $m=a^2, n=b^2$. 则 $m+n+2\sqrt{mn} = a^2+b^2+2\sqrt{a^2b^2} = a^2+b^2+2ab = (a+b)^2$. 故是完全平方数.

---

### **2. 逆否命题证明 (Proof by Contrapositive)**
#### ① 定义与概念
*   **目标 (Goal)**: 证明蕴含式 $P \to Q$.
*   **逻辑 (Logic)**: 证明 $P \to Q$ 等价于证明其逆否命题 $\neg Q \to \neg P$.

#### ② 方法与示例
1.  **方法**: Assume $\neg Q \Rightarrow \text{Step 1} \Rightarrow \text{Step 2} \Rightarrow \dots \Rightarrow \neg P$.
2.  **示例1**: 若 $r$ 是无理数, 则 $\sqrt{r}$ 是无理数.
    *   **逆否命题**: 若 $\sqrt{r}$ 是有理数, 则 $r$ 是有理数.
    *   **证明**: 假设 $\sqrt{r}$ 是有理数, 则 $\sqrt{r} = \frac{a}{b}$ ($a,b$为整数, $b \ne 0$). 那么 $r = (\frac{a}{b})^2 = \frac{a^2}{b^2}$. 因为 $a^2, b^2$ 均为整数, 故 $r$ 是有理数. 逆否命题成立, 原命题得证.
3.  **示例2**: (用于证明 "当且仅当") 整数 $n$, $n^2$ 是偶数当且仅当 $n$ 是偶数.
    *   需证明两个方向: (1) $n$ 是偶数 $\to n^2$ 是偶数; (2) $n^2$ 是偶数 $\to n$ 是偶数.
    *   方向 (1) 可用直接证明: $n=2k \implies n^2=4k^2=2(2k^2)$, 故 $n^2$ 是偶数.
    *   方向 (2) 使用逆否命题证明: "若 $n$ 是奇数, 则 $n^2$ 是奇数".
    *   **证明**: 设 $n=2k+1$. 则 $n^2 = (2k+1)^2 = 4k^2+4k+1 = 2(2k^2+2k)+1$. 故 $n^2$ 是奇数.

#### ③ 常见错误与混淆
*   **逆否 (Contrapositive)**: $\neg Q \to \neg P$ (与原命题 $P \to Q$ 等价).
*   **逆命题 (Converse)**: $Q \to P$ (与原命题不等价).
*   **否命题 (Inverse)**: $\neg P \to \neg Q$ (与原命题不等价).

---

### **3. 反证法 / 归谬法 (Proof by Contradiction)**
#### ① 定义与概念
*   **目标 (Goal)**: 证明命题 $P$.
*   **逻辑 (Logic)**: 假设 $\neg P$ 为真, 并从此假设推导出一个矛盾 (Falsehood, $F$). 因为从真前提无法推出假结论, 所以最初的假设 $\neg P$ 必为假, 从而 $P$ 必为真.
*   **逻辑形式**: $\frac{\neg P \to F}{P}$.

#### ② 方法与示例
1.  **方法**: Assume $\neg P \Rightarrow \text{Step 1} \Rightarrow \dots \Rightarrow \text{Contradiction}$. Therefore, P must be true.
2.  **示例1**: $\sqrt{2}$ 是无理数.
    *   **证明**: 假设 $\sqrt{2}$ 是有理数 ($\neg P$). 则 $\sqrt{2} = \frac{m}{n}$, 其中 $m, n$ 是互质整数.
    *   $\implies 2 = \frac{m^2}{n^2} \implies m^2 = 2n^2$. 所以 $m^2$ 是偶数, 从而 $m$ 是偶数.
    *   设 $m=2k$. 则 $(2k)^2=2n^2 \implies 4k^2=2n^2 \implies n^2=2k^2$. 所以 $n^2$ 是偶数, 从而 $n$ 是偶数.
    *   **矛盾**: $m$ 和 $n$ 都是偶数, 它们有公因子2, 这与 $m, n$ 互质的假设矛盾. 故假设不成立, $\sqrt{2}$ 是无理数.
3.  **示例2**: 素数有无限多个.
    *   **证明**: 假设素数是有限的 ($\neg P$), 记为 $p_1, p_2, \dots, p_k$.
    *   构造一个数 $N = p_1 p_2 \dots p_k + 1$.
    *   $N$ 除以任何一个素数 $p_i$ 都会余1, 因此 $N$ 不能被任何已知的素数整除.
    *   **矛盾**: 根据算术基本定理, 任何大于1的整数都必须有一个素数因子. $N > 1$, 但它却不能被任何素数整除, 这与定理矛盾. 故假设不成立, 素数有无限多个.

#### ③ 关键点
*   **与逆否命题的区别**: 证明 $P \to Q$ 时, 反证法假设 $P \land \neg Q$ 然后导出矛盾; 逆否法则假设 $\neg Q$ 并推导出 $\neg P$. 反证法更普适, 可用于证明任何形式的命题.

---

### **4. 分类讨论证明 (Proof by Cases)**
#### ① 定义与概念
*   **目标 (Goal)**: 证明命题 $R$.
*   **逻辑 (Logic)**: 将问题的前提分解为有限个完备且互斥的案例 ($P_1 \lor P_2 \lor \dots \lor P_k$), 然后证明每个案例都能推出结论 $R$.
*   **逻辑形式**: $[(P_1 \lor P_2) \land (P_1 \to R) \land (P_2 \to R)] \to R$.

#### ② 方法与示例
1.  **方法**: Decompose problem into cases. Prove the conclusion for each case.
2.  **示例1**: 任意奇数 $n$, 存在整数 $m$ 使 $n^2 = 8m + 1$.
    *   **证明**: 奇数 $n$ 可表示为 $n = 2k+1$. $n^2 = (2k+1)^2 = 4k^2+4k+1 = 4k(k+1)+1$.
    *   **Case 1**: $k$ 是偶数. 设 $k=2j$. 则 $k(k+1)$ 是偶数. $n^2 = 4(2j)(2j+1)+1 = 8j(2j+1)+1$. 令 $m=j(2j+1)$, 满足条件.
    *   **Case 2**: $k$ 是奇数. 设 $k=2j+1$. 则 $k+1$ 是偶数. $k(k+1)$ 也是偶数. $n^2=4k(k+1)+1$. 既然 $k(k+1)$ 是偶数, 可设 $k(k+1)=2m'$. 则 $n^2 = 4(2m')+1 = 8m'+1$.
    *   两个案例均证明了结论.
3.  **示例2**: 存在无理数 $a, b$, 使得 $a^b$ 是有理数 (非构造性证明 Non-constructive proof).
    *   **证明**: 考虑数字 $x = \sqrt{2}^{\sqrt{2}}$. 我们知道 $\sqrt{2}$ 是无理数.
    *   **Case 1**: $x$ 是有理数. 则令 $a=\sqrt{2}$ (无理数), $b=\sqrt{2}$ (无理数), 此时 $a^b = x$ 是有理数. 命题得证.
    *   **Case 2**: $x$ 是无理数. 则令 $a=x=\sqrt{2}^{\sqrt{2}}$ (无理数), $b=\sqrt{2}$ (无理数). 此时 $a^b = (\sqrt{2}^{\sqrt{2}})^{\sqrt{2}} = \sqrt{2}^{(\sqrt{2} \cdot \sqrt{2})} = \sqrt{2}^2 = 2$, 2是有理数. 命题得证.
    *   **结论**: 无论 $\sqrt{2}^{\sqrt{2}}$ 是有理数还是无理数, 我们都能找到符合条件的 $a, b$.

=== 文档 6: LN4.1 - Mathematical induction.pdf ===

### **模块1: 数学归纳法 (Mathematical Induction) 基础**

#### ① 定义与概念 (Definitions & Concepts)
1.  **归纳法原理 (Principle of Induction):** 用于证明一个命题 `P(n)` 对所有 `n ≥ k` (k通常为0或1) 的整数成立。
2.  **多米诺骨牌类比 (Domino Analogy):**
    *   推倒第一张牌 (证明**基础情形 Base Case**)。
    *   证明每张牌倒下都会推倒下一张牌 (证明**归纳步骤 Inductive Step**)。
    *   结论：所有牌都会倒下。
3.  **证明目标 (Objective):** 证明形如 `∀n ≥ k, P(n)` 的全称量化命题。

#### ② 公式与法则 (Formulas & Rules)
1.  **归纳法公理 (Induction Rule):**
    $$ [P(k) \land (\forall n \ge k, P(n) \to P(n+1))] \to \forall m \ge k, P(m) $$
    *   **`P(k)`**: 基础情形 (Base Case)。
    *   **`P(n) \to P(n+1)`**: 归纳步骤 (Inductive Step)。
    *   **`P(n)`**: 归纳假设 (Inductive Hypothesis, 简称I.H.)。

#### ③ 常见错误与混淆 (Common Mistakes & Confusions)
1.  **与普遍推广规则 (Universal Generalization) 的区别:**
    *   **归纳法:** 步进式证明，利用 `P(n)` 为真来证明 `P(n+1)` 为真。
    *   **普遍推广:** 对任意一个体 `c` 证明 `R(c)` 为真，不依赖于其他个例的性质。

#### ④ 关键点与注意事项 (Key Points & Additional Notes)
1.  **归纳法三步 (Three Steps of Induction):**
    1.  **定义 P(n):** 清晰地写出归纳假设 `P(n)`。
    2.  **证明基础情形:** 证明起始值 `P(k)` 成立。
    3.  **证明归纳步骤:**
        *   **假设** `P(n)` 对某个 `n ≥ k` 成立 (此为I.H.)。
        *   **证明** `P(n+1)` 也成立。
        *   **必须**在证明过程中使用到归纳假设 `P(n)`。

---

### **模块2: 基本归纳证明应用 (Basic Induction Proofs)**

#### ① 定义与概念 (Definitions & Concepts)
1.  **应用领域:** 证明等式 (equalities), 不等式 (inequalities), 以及性质如整除性 (divisibility)。

#### ② 公式与案例 (Formulas & Examples)
1.  **等式证明 (Proving Equality):** `∀n ≥ 1, 1³ + 2³ + ... + n³ = (n(n+1)/2)²`
    *   **I.H. `P(n)`:** `∑_{i=1}^{n} i³ = (n(n+1)/2)²`
    *   **归纳步骤:**
        `∑_{i=1}^{n+1} i³ = (∑_{i=1}^{n} i³) + (n+1)³`
        `= (n(n+1)/2)² + (n+1)³`  (使用 I.H.)
        `= (n+1)² [n²/4 + n+1] = ((n+1)(n+2)/2)²` (证明 `P(n+1)` 成立)

2.  **性质证明 (Proving Property):** `∀n ≥ 1, 2^(2n) - 1` 可被3整除。
    *   **I.H. `P(n)`:** `2^(2n) - 1 = 3k`
    *   **归纳步骤:**
        `2^(2(n+1)) - 1 = 4 ⋅ 2^(2n) - 1`
        `= 3 ⋅ 2^(2n) + (2^(2n) - 1)`
        *   第一项 `3 ⋅ 2^(2n)` 可被3整除。
        *   第二项 `(2^(2n) - 1)` 根据I.H.可被3整除。

3.  **不等式证明 (Proving Inequality):** `∀n ≥ 2, ∑_{k=1}^{n} 1/√k > √n`
    *   **I.H. `P(n)`:** `∑_{k=1}^{n} 1/√k > √n`
    *   **归纳步骤:**
        `∑_{k=1}^{n+1} 1/√k = (∑_{k=1}^{n} 1/√k) + 1/√(n+1)`
        `> √n + 1/√(n+1)` (使用 I.H.)
        `= (√(n(n+1)) + 1)/√(n+1) > (√n² + 1)/√(n+1) = √(n+1)`

4.  **柯西-施瓦茨不等式 (Cauchy-Schwarz Inequality):**
    `∑ aᵢbᵢ ≤ √(∑ aᵢ²) √(∑ bᵢ²)`
    *   **证明技巧:** 归纳步骤 `P(n) → P(n+1)` 实际上利用了 `P(2)` 的结论。
    *   **`P(2)` 的证明:** `a₁b₁ + a₂b₂ ≤ √(a₁²+a₂²)√(b₁²+b₂²)` 等价于证明 `(a₁b₂ - a₂b₁)² ≥ 0`。

#### ④ 关键点与注意事项 (Key Points & Additional Notes)
1.  **多个基础情形:** 有时需要证明多个基础情形，如 `P(1)` 和 `P(2)`。

---

### **模块3: 归纳构造 (Inductive Constructions)**

#### ① 定义与概念 (Definitions & Concepts)
1.  **构造性证明:** 通过提供从 `n` 到 `n+1` 的递归构造方法，来证明某个对象存在。
2.  **算法:** 归纳构造本身常常定义了一个递归算法。

#### ② 案例 (Examples)
1.  **格雷码 (Gray Code):** n位二进制串的一种排列，相邻两串仅一位不同。
    *   **构造 `G_{n+1}`:**
        1.  将 `G_n` 列表复制，并在每个元素前加 `0`。
        2.  将 `G_n` 列表反转 (`G_n^R`)，并在每个元素前加 `1`。
        3.  拼接两个新列表。
    *   **示例:** `G₂`=(00,01,11,10) → `G₃`=(000,001,011,010, **1**10, **1**11, **1**01, **1**00)。

2.  **三格骨牌平铺 (Tromino Tiling):**
    *   **定理:** `2^n × 2^n` 棋盘移除任意一格后，总能被L形三格骨牌完全覆盖。
    *   **关键技巧: 加强归纳假设 (Strengthen the I.H.)**
        *   原命题：移除中间一格。
        *   **加强后 `P(n)`:** 移除**任意**一格。
    *   **构造 `2^{n+1} × 2^{n+1}`:**
        1.  分为4个 `2^n × 2^n` 子棋盘。
        2.  空缺格位于其中一个子棋盘。
        3.  在中心放置一个三格骨牌，使其覆盖另外三个子棋盘各一个角。
        4.  此时4个子棋盘都变为“`2^n × 2^n` 且移除一格”，可应用I.H.解决。

3.  **哈达玛矩阵 (Hadamard Matrix):** 元素为`±1`的 `n×n` 矩阵，任意两行正交（内积为0）。
    *   **构造:** `H₁ = [1]`, `H_{2n} = \begin{bmatrix} H_n & H_n \\ H_n & -H_n \end{bmatrix}`。
    *   **结论:** 对任意 `k ≥ 0`，存在 `2^k × 2^k` 的哈达玛矩阵。

#### ④ 关键点与注意事项 (Key Points & Additional Notes)
1.  **加强归纳假设:** 证明一个更强的命题，可能会使归纳步骤更容易，因为它提供了一个更强的归纳假设可供使用。

---

### **模块4: 归纳法悖论与常见错误**

#### ① 定义与概念 (Definitions & Concepts)
1.  **错误证明 (Flawed Proof):** 一个看似正确但包含逻辑漏洞的归纳法证明。

#### ② 案例 (Example)
1.  **“所有马同色”悖论 (All Horses Have the Same Color Paradox):**
    *   **I.H. `P(n)`:** 任意 `n` 匹马颜色相同。
    *   **Base Case `P(1)`:** 任意1匹马颜色相同。成立。
    *   **归纳步骤 (错误):**
        1.  取 `n+1` 匹马的集合 `{h₁, ..., hₙ, h_{n+1}}`。
        2.  前 `n` 匹马 `{h₁, ..., hₙ}` 颜色相同 (by I.H.)。
        3.  后 `n` 匹马 `{h₂, ..., h_{n+1}}` 颜色相同 (by I.H.)。
        4.  因为这两个集合有重叠，所以所有 `n+1` 匹马颜色相同。

#### ③ 错误分析 (Flaw Analysis)
1.  **逻辑漏洞:** 归纳步骤的论证在 `n=1` 时不成立。
2.  **`P(1) → P(2)` 失效:**
    *   当 `n=1` 时，要证明的 `n+1=2` 匹马集合为 `{h₁, h₂}`。
    *   “前 `n` 匹马”集合为 `{h₁}`。
    *   “后 `n` 匹马”集合为 `{h₂}`。
    *   这两个集合**没有重叠部分**，无法通过重叠来传递颜色相同这一性质。
3.  **结论:** 证明链在第一环 (`P(1) → P(2)`) 就断裂了。

#### ④ 关键点与注意事项 (Key Points & Additional Notes)
1.  **检查所有情况:** 归纳步骤 `P(n) → P(n+1)` 必须对**所有** `n ≥ k` 都成立。
2.  **警惕小值:** 特别注意 `n` 取小值时（如 `n=1, 2`），通用逻辑可能存在边界情况而不适用。

=== 文档 7: LN4.2 - Mathematical induction.pdf ===

### **数学归纳法 II (Mathematical Induction II)**

---

### **1. 强归纳法 (Strong Induction)**

#### ① 定义与概念 (Definitions & Concepts)
1.  **强归纳法 (Strong Induction):**
    *   **基础步骤 (Base Case):** 证明 `P(0)` 成立。
    *   **归纳步骤 (Inductive Step):** 假设 `P(0), P(1), ..., P(n)` 全部成立，然后证明 `P(n+1)` 也成立。
    *   **结论 (Conclusion):** `∀n, P(n)` 成立。
2.  **与普通归纳法对比 (vs. Ordinary Induction):**
    *   **普通归纳法:** 归纳步骤仅假设 `P(n)` 成立来证明 `P(n+1)`。
    *   **强归纳法:** 归纳步骤假设从基础情况到 `n` 的所有情况 `P(0), ..., P(n)` 都成立。
    *   **等价性 (Equivalence):** 二者在逻辑上是等价的，但强归纳法的假设更强，有时能让证明更简单。
3.  **重构归纳假设 (Rephrased Hypothesis):**
    *   为证明 `C(n+1)`，可定义新假设 `Q(n) ::= ∀m ≤ n. C(m)` (即所有小于等于n的命题都为真)。
    *   在归纳步骤中，使用 `Q(n)` 作为假设，可以理所当然地使用 `C(a)` 和 `C(b)`（其中 `a,b ≤ n`）。

#### ② 公式与方程 (Formulas & Equations)
1.  **分盒子游戏 (Unstacking Game) 总分公式:**
    *   从 `n` 个盒子开始，无论如何拆分，最终总分恒为:
        $$ S_n = \frac{n(n-1)}{2} $$
2.  **归纳步骤推导 (Inductive Step Derivation):**
    *   将 `n+1` 个盒子分成 `a` 和 `b` 两堆，其中 `a+b = n+1`。
    *   总分 = 本次得分 + `a`堆得分 + `b`堆得分。
    *   `Score(a+b) = ab + Score(a) + Score(b)`
    *   根据强归纳假设 `Score(a) = a(a-1)/2` 和 `Score(b) = b(b-1)/2`。
    *   $$ ab + \frac{a(a-1)}{2} + \frac{b(b-1)}{2} = \frac{2ab + a^2-a + b^2-b}{2} = \frac{(a+b)^2 - (a+b)}{2} = \frac{(n+1)n}{2} $$

#### ③ 常见错误与混淆 (Common Mistakes & Confusions)
1.  **忘记检验多个基础案例 (Forgetting Multiple Base Cases):** 当归纳步骤依赖于前 `k` 个状态时 (如 `P(n-k)` )，需要验证 `k` 个或更多的基础案例。例如邮票问题中，`P(n)` 依赖 `P(n-3)`，需要验证 `P(8), P(9), P(10)`。
2.  **混淆假设范围 (Confusing Hypothesis Scope):** 强归纳法假设 `P(0)` 到 `P(n)` 都成立，而不仅仅是 `P(n)`。

#### ④ 关键点与应用实例 (Key Points & Applications)
1.  **分盒子游戏 (Unstacking Game):**
    *   **问题:** 将一堆 `n` 个盒子，每次拆成两堆 `a, b` (a,b>0)，得分 `ab`，求证总分与拆分策略无关。
    *   **结论:** 总分恒为 `n(n-1)/2`。证明过程必须用强归纳法，因为拆分后的 `a` 和 `b` 小于 `n+1`，但不一定是 `n`。
2.  **质数乘积定理 (Prime Products Theorem):**
    *   **定理:** 每个大于1的整数都是质数的乘积。
    *   **证明思路 (强归纳):**
        *   **基础:** `n=2` 是质数，成立。
        *   **归纳:** 假设对所有 `2 ≤ i < n` 成立。考虑 `n`：
            *   若 `n` 是质数，则已证。
            *   若 `n` 是合数，则 `n = k * m`，其中 `2 ≤ k, m < n`。根据强归纳假设，`k` 和 `m` 都是质数的乘积，因此 `n` 也是。
3.  **邮票问题 (Postage Problem):**
    *   **问题1 (3¢ & 5¢):** 证明用3分和5分邮票可以组成任何不小于8分的面值。
        *   **基础案例:** `8¢=3+5`, `9¢=3*3`, `10¢=5*5`。
        *   **归纳步骤:** 对 `n ≥ 11`，目标是凑出 `n¢`。因为 `n-3 ≥ 8`，根据强归纳假设，可以凑出 `(n-3)¢`，再加一张3分邮票即可。
    *   **问题2 (5¢ & 7¢):** 可组成任何不小于24分的面值。

---

### **2. 良序原则 (Well Ordering Principle, WOP)**

#### ① 定义与概念 (Definitions & Concepts)
1.  **良序原则 (WOP):** 任何非空的**自然数**集合 (`\mathbb{N}=\{1, 2, 3, ...\}` 或 `\{0, 1, 2, ...\}`) 必有最小元素。
2.  **推广 (Variations):** 任何非空的**正整数** (`\mathbb{Z}^+`) 子集必有最小元素。
3.  **不适用情况 (Not Applicable):**
    *   整数集 (`\mathbb{Z}`): 没有最小元素。
    *   非负实数集 (`\mathbb{R}_{\ge 0}`): 没有最小元素 (如集合 `(0, 1]` 没有最小值)。

#### ② 应用实例 (Applications)
1.  **证明 `√2` 是无理数 (Proof that `√2` is irrational):**
    *   **思路:** 反证法 + WOP。
    *   假设 `√2 = m/n`。令 `S = { |m| ∈ Z⁺ | ∃n, √2 = m/n }`。
    *   `S` 非空，由WOP，存在最小元素 `|m₀|`，使得 `√2 = m₀/n₀`。
    *   可证 `m₀, n₀` 均为偶数，则 `√2 = (m₀/2) / (n₀/2)`。
    *   此时 `|m₀/2| < |m₀|` 且 `|m₀/2| ∈ S`，与 `|m₀|` 的最小性矛盾。
2.  **非费马定理 (Non-Fermat Theorem):**
    *   **定理:** `4a³ + 2b³ = c³` 没有正整数解。
    *   **思路:** 反证法 + WOP。
    *   设 `S = { a ∈ Z⁺ | ∃b,c ∈ Z⁺, 4a³+2b³=c³ }`。
    *   假设 `S` 非空，由WOP，存在最小元素 `a₀`。
    *   `4a₀³ + 2b₀³ = c₀³` ⟹ `c₀` 是偶数。令 `c₀=2c₁`。
    *   `2a₀³ + b₀³ = 4c₁³` ⟹ `b₀` 是偶数。令 `b₀=2b₁`。
    *   `a₀³ + 4b₁³ = 2c₁³` ⟹ `a₀` 是偶数。令 `a₀=2a₁`。
    *   因此 `(a₀/2, b₀/2, c₀/2)` 即 `(a₁, b₁, c₁)` 也是一组解。
    *   `a₁ = a₀/2 < a₀` 且 `a₁ ∈ S`，与 `a₀` 的最小性矛盾。

#### ④ WOP证明通用策略 (General Proof Strategy using WOP)
1.  **构造反例集 (Construct Counterexample Set):** 定义集合 `S = { n ∈ N | ¬P(n) }`。
2.  **假设非空 (Assume Non-empty):** 假设 `S` 非空，即存在反例。
3.  **找到最小元 (Find Least Element):** 根据WOP，`S` 必有最小元素 `n₀`。
4.  **导出矛盾 (Derive Contradiction):** 证明存在一个比 `n₀` 更小的元素 `n'` 也在 `S` 中 (`n' < n₀` 且 `¬P(n')`)，或者证明 `P(n₀)` 成立。这与 `n₀` 是 `S` 中最小的**反例**矛盾。
5.  **得出结论 (Conclude):** `S` 必须为空，即 `P(n)` 对所有 `n` 成立。

---

### **3. 不变量方法 (Invariant Method)**

#### ① 定义与概念 (Definitions & Concepts)
1.  **不变量 (Invariant):** 在一系列操作或变换过程中保持不变的性质或数量。
2.  **应用场景 (Use Case):** 通常用于证明某个状态无法通过一系列允许的操作达到。

#### ④ 关键点与应用实例 (Key Points & Applications)
1.  **不变量证明策略 (Invariant Proof Strategy):**
    *   **1. 识别不变量:** 找到一个在所有允许操作下都保持不变的性质 (e.g., 颜色、奇偶性、总和)。
    *   **2. 验证初始状态:** 确认初始状态满足该不变量性质。
    *   **3. 检查目标状态:** 证明目标状态**不满足**该不变量性质。
    *   **4. 得出结论:** 因为不变量在操作中保持不变，而初始与目标状态的不变量性质不同，所以目标状态不可达。
2.  **棋盘主教问题 (Chessboard Bishop Problem):**
    *   **问题:** 主教 (Bishop) 只能斜着走，能否从一个白格走到一个黑格？
    *   **不变量:** 主教所在格子的**颜色**。
    *   **分析:** 每次斜向移动，格子的颜色保持不变。
    *   **结论:** 不可能从白格走到黑格。
3.  **多米诺骨牌问题 (Domino Puzzle):**
    *   **问题:** 一个8x8棋盘，去掉对角的两个方格，能否用31个1x2的多米诺骨牌完全覆盖？
    *   **不变量:** 每个多米诺骨牌必须覆盖**一个白格和一个黑格**。因此，任何被骨牌覆盖的区域，白格和黑格数量必须相等。
    *   **分析:**
        *   完整8x8棋盘有32个白格和32个黑格。
        *   去掉对角的两个方格，由于对角方格颜色相同，所以剩下32个某色方格和30个另一色方格。
        *   白格和黑格数量不相等 (32 ≠ 30)。
    *   **结论:** 无法用31个骨牌覆盖。
4.  **15-puzzle 挑战 (15-Puzzle Challenge):**
    *   **问题:** 能否通过滑动将 `14` 和 `15` 的位置互换，而其他数字不动？
    *   **提示:** 这类问题通常也用不变量方法解决，不变量是**逆序数对 (inversion count) 的奇偶性**与**空格所在行的奇偶性**的关系。

=== 文档 8: LN5 - Recursion.pdf ===

### **模块1: 递归基础 (Recursion Basics)**

#### **① 定义与概念 (Definitions & Concepts)**
1.  **递归 (Recursion)**: 将问题分解为同一问题的更小实例来解决的技术。核心思想是捕捉重复行为中的不变量 (invariants)。
2.  **递归定义序列 (Recursively Defined Sequences)**: 通过当前项与前几项的关系来定义的序列。
    *   **等差数列 (Arithmetic Sequence)**: $(a, a+d, a+2d, \dots)$
    *   **等比数列 (Geometric Sequence)**: $(a, ra, r^2a, \dots)$
    *   **调和数列 (Harmonic Sequence)**: $(1, 1/2, 1/3, \dots)$

#### **② 公式与方程 (Formulas & Equations)**
1.  **等差数列**: $a_0 = a, \quad a_{i+1} = a_i + d$
2.  **等比数列**: $a_0 = a, \quad a_{i+1} = r \cdot a_i$
3.  **调和数列**: $a_0 = 1, \quad a_{i+1} = \frac{i \cdot a_i}{i+1}$

---

### **模块2: 建立递推关系 (Setting up Recurrence Relations)**

#### **2.1. 简单计数与分治 (Simple Counting & Divide and Conquer)**
*   **① 概念 (Concepts)**:
    *   **简单计数**: 将n个元素的集合问题，分解为(n-1)个元素的子问题。
    *   **分治法 (Divide and Conquer)**: 将问题分解为多个独立的子问题，递归解决子问题，然后合并结果。
*   **② 公式与示例 (Formulas & Examples)**:
    1.  **幂集大小 (Power Set Size)**: $n$元集合 $S_n$ 的幂集 $pow(S_n)$ 的大小 $r_n$。
        *   **思想**: $pow(S_n)$ = $pow(S_{n-1})$ $\cup$ {在$pow(S_{n-1})$每个子集中加入$a_n$}。
        *   **递推式**: $r_n = 2r_{n-1}$, 初始条件 $r_1=2$ 或 $r_0=1$。
        *   **解**: $r_n = 2^n$。
    2.  **汉诺塔 (Tower of Hanoi)**: 将n个盘子从柱1移动到柱3所需的最小步数 $r_n$。
        *   **思想**: 1. 将n-1个盘子从1→2 (借助3)； 2. 将第n个盘子从1→3； 3. 将n-1个盘子从2→3 (借助1)。
        *   **递推式**: $r_n = 2r_{n-1} + 1$, 初始条件 $r_1=1$。
        *   **解**: $r_n = 2^n - 1$。
    3.  **归并排序 (Merge Sort)**: 排序 $n$ 个数所需的时间复杂度 $T_n$。
        *   **思想**: 1. 将序列一分为二； 2. 递归排序两个子序列； 3. 合并两个已排序的子序列。
        *   **递推式**: $T_n = 2T_{n/2} + n$ (合并需要n步)。
        *   **解**: $T_n = O(n \log n)$。

#### **2.2. 斐波那契型递推 (Fibonacci-type Recurrences)**
*   **① 概念 (Concepts)**:
    *   问题的解 $r_n$ 可以由 $r_{n-1}$ 和 $r_{n-2}$ 的状态构造出来。通常通过对第一个或最后一个元素进行分类讨论得到。
*   **② 公式与示例 (Formulas & Examples)**: **通用递推式**: $r_n = r_{n-1} + r_{n-2}$
    1.  **斐波那契兔子 (Fibonacci Rabbits)**: 第n个月的兔子对数 $r_n$。
        *   **思想**: 第n个月兔子数 = (n-1)月已有的 + (n-1)月新生(来自n-2月的成熟兔子)。
        *   **递推式**: $r_n = r_{n-1} + r_{n-2}$。
    2.  **无"11"的比特串 (Bit Strings w/o "11")**: 长度为n且不含"11"的比特串数量 $r_n$。
        *   **思想**: 分类讨论第一位：
            *   Case 1: 以 '0' 开头 → 后面可以是任意长度为n-1的无"11"串 ($r_{n-1}$种)。
            *   Case 2: 以 '1' 开头 → 第二位必须是 '0'，后面可以是任意长度为n-2的无"11"串 ($r_{n-2}$种)。
        *   **递推式**: $r_n = r_{n-1} + r_{n-2}$。
    3.  **多米诺骨牌覆盖 (Domino Tiling)**: 用 2x1 骨牌覆盖 2xn 棋盘的方案数 $r_n$。
        *   **思想**: 分类讨论最右侧骨牌的放置方式：
            *   Case 1: 竖放1个 → 剩下 2x(n-1) 棋盘 ($r_{n-1}$种)。
            *   Case 2: 横放2个 → 剩下 2x(n-2) 棋盘 ($r_{n-2}$种)。
        *   **递推式**: $r_n = r_{n-1} + r_{n-2}$。
*   **④ 关键点 (Key Points)**
    *   多个不同问题可能共享相同的递推关系，但初始条件可能不同。
    *   练习: 无 "111" 的n-比特串数量: $r_n = r_{n-1} + r_{n-2} + r_{n-3}$。

#### **2.3. 卡特兰数型递推 (Catalan Recurrences)**
*   **① 概念 (Concepts)**:
    *   问题的解 $r_n$ 通过将问题分解为大小为 $k-1$ 和 $n-k$ 的两个独立子问题，并对所有可能的 $k$ 求和得到。
*   **② 公式与示例 (Formulas & Examples)**: **通用递推式**: $r_n = \sum_{k=1}^{n} r_{k-1}r_{n-k}$ (定义 $r_0=1$)
    1.  **有效括号 (Valid Parentheses)**: n对括号的有效组合方式数量 $r_n$。
        *   **思想**: 考虑第一个 `(` 匹配的 `)` 的位置。若它在第 $k$ 对，则形式为 `(A)B`。`A` 是 $k-1$ 对括号的有效组合，`B` 是 $n-k$ 对括号的有效组合。
        *   **递推式**: $r_n = \sum_{k=1}^{n} r_{k-1}r_{n-k}$。
    2.  **阶梯填充 (Stair Tiling)**: 用n个矩形填充n-阶梯的方案数 $r_n$。
        *   **思想**: 考虑覆盖右下角方格的矩形R。若R同时覆盖了对角线上的第 $i$ 个方格，它会将n-阶梯分解为一个 (i-1)-阶梯和一个 (n-i)-阶梯。
        *   **递推式**: $r_n = \sum_{i=1}^{n} r_{i-1}r_{n-i}$。
*   **④ 关键点 (Key Points)**
    *   **卡特兰数 (Catalan Number)** 的通项公式为 $C_n = \frac{1}{n+1} \binom{2n}{n}$。

---

### **模块3: 求解递推关系 (Solving Recurrence Relations)**

#### **3.1. 迭代法/猜测验证法 (Iteration / Guess & Verify)**
*   **① 概念 (Concepts)**:
    *   反复代入递推关系，展开式子，寻找规律，猜测通项公式，最后用数学归纳法证明。
*   **② 示例 (Examples)**:
    1.  $a_0 = 1, a_k = a_{k-1} + 2 \implies a_k = a_0 + 2k = 2k+1$。
    2.  $a_1 = 1, a_k = 2a_{k-1} + 1 \implies a_k = 2^k - 1$ (Hanoi)。

#### **3.2. 特征方程法 (Characteristic Equation Method)**
*   **① 概念 (Concepts)**:
    *   适用于求解**二阶线性齐次常系数递推关系 (second-order linear homogeneous recurrence relation with constant coefficients)**。
*   **② 公式与定理 (Formulas & Theorems)**:
    1.  **递推关系**: $a_k = A a_{k-1} + B a_{k-2}$ ($B \neq 0$)
    2.  **特征方程 (Characteristic Eq.)**: $t^2 - At - B = 0$
    3.  **不同根定理 (Distinct-Roots Theorem)**: 若特征方程有两个不同实根 $r, s$，则通解为 $a_n = C r^n + D s^n$。常数 $C, D$ 由初始条件 ($a_0, a_1$) 确定。
*   **③ 解题步骤 (Solving Steps)**:
    1.  写出特征方程 $t^2 - At - B = 0$。
    2.  求解得到根 $r, s$。
    3.  写出通解 $a_n = C r^n + D s^n$。
    4.  代入初始条件 $a_0, a_1$ 建立关于 $C, D$ 的方程组。
    5.  解出 $C, D$ 得到特解。
*   **④ 示例: 求解斐波那契数列 (Example: Solving Fibonacci)**
    *   $f_n = f_{n-1} + f_{n-2}$ with $f_0=0, f_1=1$.
    *   特征方程: $t^2 - t - 1 = 0$。
    *   根: $r = \frac{1+\sqrt{5}}{2}$ (黄金分割, $\phi$), $s = \frac{1-\sqrt{5}}{2}$。
    *   通解: $f_n = C(\frac{1+\sqrt{5}}{2})^n + D(\frac{1-\sqrt{5}}{2})^n$。
    *   代入初始值:
        *   $n=0: f_0=0 = C+D$
        *   $n=1: f_1=1 = C(\frac{1+\sqrt{5}}{2}) + D(\frac{1-\sqrt{5}}{2})$
    *   解得: $C = \frac{1}{\sqrt{5}}, D = -\frac{1}{\sqrt{5}}$。
    *   **比内公式 (Binet's Formula)**: $f_n = \frac{1}{\sqrt{5}} \left[ \left(\frac{1+\sqrt{5}}{2}\right)^n - \left(\frac{1-\sqrt{5}}{2}\right)^n \right]$。

#### **3.3. 生成函数法 (Generating Functions Method)**
*   **① 概念 (Concepts)**:
    *   **普通生成函数 (Ordinary Generating Function, OGF)**: 将一个无限序列 $\langle a_0, a_1, a_2, \dots \rangle$ 映射为一个形式幂级数 $F(x) = \sum_{n=0}^{\infty} a_n x^n$。
*   **② 常用函数与运算 (Common Functions & Operations)**:
    *   $\langle 1,1,1,\dots \rangle \leftrightarrow \frac{1}{1-x}$
    *   $\langle 1,-1,1,-1,\dots \rangle \leftrightarrow \frac{1}{1+x}$
    *   **数乘 (Scaling)**: $\langle ca_n \rangle \leftrightarrow c F(x)$
    *   **加法 (Addition)**: $\langle a_n+b_n \rangle \leftrightarrow A(x)+B(x)$
    *   **右移 (Right Shifting)**: $\langle \underbrace{0,..,0}_{k}, a_0, a_1,.. \rangle \leftrightarrow x^k F(x)$
    *   **微分 (Differentiation)**: $\langle (n+1)a_{n+1} \rangle \leftrightarrow F'(x)$
*   **③ 解题步骤 (Solving Steps)**:
    1.  将递推关系表示为序列间的运算。
    2.  利用运算性质将序列方程转换为生成函数的代数方程。
    3.  解出生成函数 $F(x)$ 的封闭形式。
    4.  将 $F(x)$ 分解 (如部分分式分解)。
    5.  将 $F(x)$ 展开为泰勒级数，找到 $x^n$ 的系数即为 $a_n$。
*   **④ 示例: 求解斐波那契数列 (Example: Solving Fibonacci)**
    *   $f_n = f_{n-1} + f_{n-2} \implies \langle f_n \rangle = \langle 0,1,0,.. \rangle + \langle 0,f_0,f_1,.. \rangle + \langle 0,0,f_0,.. \rangle$
    *   $F(x) = x + xF(x) + x^2F(x)$
    *   $F(x)(1-x-x^2) = x \implies F(x) = \frac{x}{1-x-x^2}$
    *   部分分式分解: $F(x) = \frac{1}{\sqrt{5}} \left( \frac{1}{1-\phi x} - \frac{1}{1-(1-\phi)x} \right)$
    *   展开: $f_n = \frac{1}{\sqrt{5}}(\phi^n - (1-\phi)^n)$, 结果同特征方程法。

=== 文档 9: LN6 - Greatest common divisors.pdf ===

### **1. 最大公约数 (Greatest Common Divisors)**

#### **1.1 ① 定义与概念 (Definitions & Concepts)**

1.  **整除 (Divisibility)**
    *   对于非零整数 $b$，若存在整数 $k$ 使得 $a=kb$，则称 $b$ 整除 $a$。
    *   记作 $b|a$。
    *   $b$ 是 $a$ 的**约数/因数 (divisor)**。
    *   $a$ 是 $b$ 的**倍数 (multiple)**。
    *   $b|a \iff a$ 是 $b$ 的倍数。

2.  **公约数 (Common Divisor)**
    *   若 $c|a$ 且 $c|b$，则 $c$ 是 $a$ 和 $b$ 的公约数。
    *   **最大公约数 (Greatest Common Divisor, gcd)**: $a, b$ 的公约数中最大的一个，记作 $\text{gcd}(a,b)$。
    *   **性质**: 若 $p$ 是素数且 $p \nmid a$，则 $\text{gcd}(p,a)=1$。

3.  **商-余数定理 (The Quotient-Remainder Theorem)**
    *   对于 $b>0$ 和任意整数 $a$，存在唯一的整数 $q$ (商, quotient) 和 $r$ (余数, remainder) 满足：
        $a = qb + r$，其中 $0 \le r < b$。
    *   $q = a \text{ div } b = \lfloor a/b \rfloor$
    *   $r = a \text{ mod } b$

4.  **线性组合 (Linear Combination)**
    *   **整型线性组合**: 若 $d=sa+tb$ (其中 $s,t$ 为整数)，则 $d$ 是 $a,b$ 的一个整型线性组合。
    *   **最小正线性组合 (Smallest Positive integer linear Combination, spc)**: $a,b$ 的所有正的线性组合中最小的一个，记作 $\text{spc}(a,b)$。

5.  **算术基本定理 (Fundamental Theorem of Arithmetic)**
    *   任何大于1的整数 $n$ 都可以唯一地分解为素数的乘积（不考虑顺序）。
    *   $n = p_1^{a_1} p_2^{a_2} \cdots p_k^{a_k}$

#### **1.2 ② 公式与算法 (Formulas & Equations)**

1.  **欧几里得算法 (Euclid's Algorithm)**
    *   **核心性质**: 若 $a=qb+r$，则 $\text{gcd}(a,b) = \text{gcd}(b,r)$。
    *   **算法描述** (假设 $a>b \ge 0$):
        ```
        gcd(a, b)
          if b == 0, return a
          else
            r = a mod b
            return gcd(b, r)
        ```
    *   **示例**: $\text{gcd}(102, 70)$
        *   $102 = 1 \cdot 70 + 32 \implies \text{gcd}(70, 32)$
        *   $70 = 2 \cdot 32 + 6 \implies \text{gcd}(32, 6)$
        *   $32 = 5 \cdot 6 + 2 \implies \text{gcd}(6, 2)$
        *   $6 = 3 \cdot 2 + 0 \implies \text{gcd}(2, 0) \implies \text{结果为 } 2$

2.  **GCD 与 SPC 的关系**
    *   **核心定理**: $\text{gcd}(a,b) = \text{spc}(a,b)$。
    *   **证明思路**:
        1.  **证 $\text{gcd} \le \text{spc}$**:
            *   令 $d=\text{gcd}(a,b)$。则 $d|a$ 且 $d|b$。
            *   对于任意线性组合 $sa+tb$，有 $d|(sa+tb)$。
            *   因此 $d | \text{spc}(a,b)$，由于 $\text{spc}>0$, $d>0$, 故 $d \le \text{spc}(a,b)$。
        2.  **证 $\text{spc} \le \text{gcd}$**:
            *   令 $f=\text{spc}(a,b)$。需证 $f$ 是 $a,b$ 的公约数。
            *   由商-余数定理，$a = qf+r$ ($0 \le r < f$)。
            *   $r = a - qf = a - q(sa+tb) = (1-qs)a + (-qt)b$，所以 $r$ 也是一个线性组合。
            *   因 $f$ 是最小正线性组合且 $r<f$，故 $r$ 必为0。
            *   所以 $f|a$。同理可证 $f|b$。
            *   因此 $f$ 是公约数，故 $f \le \text{gcd}(a,b)$。

3.  **扩展欧几里得算法 (Extended Euclidean Algorithm)**
    *   **目的**: 求解整数 $s,t$ 使得 $\text{gcd}(a,b) = sa+tb$。
    *   **方法**: 对欧几里得算法的每一步进行回代 (Back-substitution)。
    *   **示例**: 求 $\text{gcd}(259, 70)$ 的线性组合。
        *   $259 = 3 \cdot 70 + 49 \implies 49 = a - 3b$
        *   $70 = 1 \cdot 49 + 21 \implies 21 = b - 1 \cdot 49 = b - (a-3b) = -a+4b$
        *   $49 = 2 \cdot 21 + 7 \implies 7 = 49 - 2 \cdot 21 = (a-3b) - 2(-a+4b) = 3a - 11b$
        *   $\text{gcd}(259, 70)=7$，线性组合为 $7 = 3 \cdot 259 - 11 \cdot 70$。

#### **1.3 ③ 常见错误与混淆 (Common Mistakes & Confusions)**

1.  **GCD 计算方法对比**
    *   **朴素算法 (Naive)**: 遍历从1到 $\min(a,b)$ 的所有整数，找出公约数并取最大。
        *   **复杂度**: 线性时间 $O(\min(a,b))$，对于大数非常慢。
    *   **欧几里得算法 (Euclidean)**: 递归使用余数。
        *   **复杂度**: 对数时间 $O(\log(\min(a,b)))$，效率极高，呈指数级提升。
        *   **原理**: 每两轮迭代，数值至少减半。

2.  **GCD vs. SPC**
    *   $\text{gcd}(a,b)$ 是从**乘法**角度定义的（最大的公约数）。
    *   $\text{spc}(a,b)$ 是从**加法**角度定义的（$sa+tb$ 形式的最小正整数）。
    *   两者数值相等是一个重要的**定理**，而非定义。这个定理是数论中许多其他结论的基石。

#### **1.4 ④ 关键点与附加说明 (Key Points & Additional Notes)**

1.  **定理推论**
    *   **素数整除引理**: 若 $p$ 为素数且 $p|ab$，则 $p|a$ 或 $p|b$。
        *   **证明**: 若 $p \nmid a$，则 $\text{gcd}(p,a)=1$。由 $\text{gcd}=\text{spc}$ 定理，存在 $s,t$ 使 $sa+tp=1$。两边同乘 $b$ 得 $sab+tpb=b$。因 $p|ab$ 且 $p|tp$，故 $p|b$。
    *   **互质性质**: 若 $\text{gcd}(a,b)=1$ 且 $\text{gcd}(a,c)=1$，则 $\text{gcd}(a,bc)=1$。

2.  **应用: 量水问题 (Die Hard Problem)**
    *   **问题**: 给定容量为 $A$ 和 $B$ 的水壶，能否精确量出体积 $C$？
    *   **不变量 (Invariant)**: 任意时刻，壶中水量必为 $sA+tB$ 的形式（$s,t$为整数）。
    *   **可解性判据**: 体积 $C$ 能被量出 $\iff C$ 是 $\text{gcd}(A,B)$ 的倍数。
        *   **例**: 3加仑和9加仑的水壶无法量出4加仑，因为 $\text{gcd}(3,9)=3$，而 $3 \nmid 4$。
        *   **例**: 21和26加仑水壶可以量出3加仑，因为 $\text{gcd}(21,26)=1$，而 $1|3$。
    *   **通用解法**:
        1.  若 $\text{gcd}(A,B) \nmid C$，则无解。
        2.  否则，用扩展欧几里得算法找到 $s,t$ 使得 $\text{gcd}(A,B) = sA+tB$。
        3.  将等式两边同乘以 $C/\text{gcd}(A,B)$ 得到 $C = s'A+t'B$。
        4.  操作方案：重复 $s'$ 次“灌满A壶并倒入B壶（B满则倒空）”的操作，最终可在壶中得到 $C$ 体积的水。

=== 文档 10: LN7 - Modular arithmetic and Chinese remainder theorem.pdf ===

### **模块 1: 模运算 (Modular Arithmetic)**

#### **① 定义与概念 (Definitions & Concepts)**
1.  **同余 (Congruence):** $a \equiv b \pmod n \iff n | (a - b)$。
2.  **同余类 (Congruence Class):** $[a]_n = \{a+kn \mid k \in \mathbb{Z}\}$。表示所有与$a$模$n$同余的整数集合。
3.  **模n整数集 (Integers Modulo n):** $\mathbb{Z}_n = \{[0]_n, [1]_n, \dots, [n-1]_n\}$。由模$n$的同余类构成的集合。
4.  **乘法逆元 (Multiplicative Inverse):** 对$a \pmod n$，其逆元$a'$满足 $a \cdot a' \equiv 1 \pmod n$。
5.  **逆序对 (Disordered Pair):** 在序列 $(a_1, \dots, a_m)$ 中，若 $i < j$ 但 $a_i > a_j$，则序对 $(i,j)$ 为一个逆序对。

#### **② 公式与定理 (Formulas & Equations)**
1.  **模运算性质:**
    -   **加法:** 若 $a \equiv c \pmod n$ 且 $b \equiv d \pmod n$，则 $a+b \equiv c+d \pmod n$。
    -   **乘法:** 若 $a \equiv c \pmod n$ 且 $b \equiv d \pmod n$，则 $ab \equiv cd \pmod n$。
2.  **乘法逆元:**
    -   **存在性:** $a$ 模 $n$ 的乘法逆元存在 $\iff \gcd(a,n)=1$。
    -   **唯一性:** 若存在，逆元在模 $n$ 意义下是唯一的。
3.  **消去律 (Cancellation Law):** 若 $ac \equiv bc \pmod n$ 且 $\gcd(c,n)=1$，则 $a \equiv b \pmod n$。
4.  **费马小定理 (Fermat's Little Theorem):** 若 $p$ 为素数且 $p \nmid a$，则 $a^{p-1} \equiv 1 \pmod p$。
5.  **威尔逊定理 (Wilson's Theorem):** 整数 $p>1$ 是素数 $\iff (p-1)! \equiv -1 \pmod p$。
    -   **引理:** 对素数 $p$，$x^2 \equiv 1 \pmod p \iff x \equiv 1 \pmod p$ 或 $x \equiv -1 \pmod p$。

#### **③ 常见错误与混淆 (Common Mistakes & Confusions)**
1.  **错误消去:** $ac \equiv bc \pmod n$ 不能直接推出 $a \equiv b \pmod n$。
    -   **例:** $4 \cdot 2 \equiv 1 \cdot 2 \pmod 6$ (即 $8 \equiv 2 \pmod 6$)，但 $4 \not\equiv 1 \pmod 6$。
    -   **原因:** $\gcd(c, n) = \gcd(2, 6) = 2 \ne 1$。
2.  **逆元存在性:** 并非所有非零数都有乘法逆元。
    -   **例:** 在 $\mathbb{Z}_6$ 中，2, 3, 4 没有乘法逆元，因为它们与模数6不互质。

#### **④ 要点与补充 (Key Points & Additional Notes)**
1.  **应用: 整除性判定 (Divisibility Test):**
    -   一个数能被9整除 $\iff$ 其各位数字之和能被9整除。
    -   **证明:** $n = \sum d_i 10^i$。因 $10 \equiv 1 \pmod 9$，故 $n \equiv \sum d_i 1^i \equiv \sum d_i \pmod 9$。
2.  **应用: 十五数码问题 (Fifteen Puzzle):**
    -   **不变量方法 (Invariant Method):** 寻找在所有允许操作下保持不变的性质，若初始状态和目标状态该性质不同，则目标不可达。
    -   **游戏不变量:** 状态奇偶性 (Parity of State) = $(\text{逆序对数量} + \text{空格所在行号}) \pmod 2$。
    -   **结论:** 任何合法移动都保持状态奇偶性不变。
3.  **域结构 (Field Structure):** 模素数 $p$ 的算术构成一个有限域 $\mathbb{F}_p$，其中每个非零元素都有乘法逆元。

---

### **模块 2: 中国剩余定理 (Chinese Remainder Theorem - CRT)**

#### **① 定义与概念 (Definitions & Concepts)**
1.  **线性同余方程组 (System of Linear Congruences):** 形如 $x \equiv a_i \pmod{n_i}$ 的一组方程。
2.  **两两互质 (Mutually Coprime):** 一组整数 $\{n_1, \dots, n_k\}$ 中，任意两个数 $n_i, n_j$ ($i \ne j$) 的最大公约数均为1。

#### **② 公式与定理 (Formulas & Equations)**
1.  **解单个同余方程 $ax \equiv b \pmod n$:**
    -   **有解条件:** 当且仅当 $\gcd(a, n) | b$。
    -   **解的结构:** 若有解，解在模 $n/\gcd(a, n)$ 意义下唯一。
    -   **解法:**
        a. 设 $c = \gcd(a, n)$。若 $c \nmid b$，无解。
        b. 若 $c|b$，方程化为 $(a/c)x \equiv (b/c) \pmod{n/c}$。
        c. 在新方程中，$\gcd(a/c, n/c) = 1$，求 $(a/c)$ 的逆元即可解出 $x$。
2.  **中国剩余定理 (CRT):**
    -   **条件:** 方程组 $x \equiv a_i \pmod{n_i}$ ($i=1, \dots, k$)，其中模数 $n_1, \dots, n_k$ 两两互质。
    -   **结论:** 方程组在模 $N = n_1 n_2 \dots n_k$ 意义下有唯一解。
3.  **CRT 构造解法 (Constructive Solution):**
    a. 计算 $N = \prod_{i=1}^k n_i$。
    b. 对每个 $i$，计算 $N_i = N/n_i$。
    c. 对每个 $i$，计算 $N_i$ 模 $n_i$ 的乘法逆元 $y_i$，即 $N_i y_i \equiv 1 \pmod{n_i}$。
    d. 解为 $x \equiv \sum_{i=1}^k a_i N_i y_i \pmod N$。

#### **③ 常见错误与混淆 (Common Mistakes & Confusions)**
1.  **模数不互质:** 标准CRT公式不直接适用。需要先将每个模数分解为素数幂的乘积，将原方程组拆分为关于素数幂模的方程组，检查一致性后求解。
2.  **一致性检查 (Consistency Check):** 当模数不互质时，方程组可能无解。
    -   **例:** $\{x \equiv 3 \pmod{10}, x \equiv 8 \pmod{15}\}$。
        -   $x \equiv 3 \pmod{10} \implies x \equiv 3 \pmod 5$ 且 $x \equiv 1 \pmod 2$。
        -   $x \equiv 8 \pmod{15} \implies x \equiv 3 \pmod 5$ 且 $x \equiv 2 \pmod 3$。
        -   $x \equiv 3 \pmod 5$ 一致。将剩余方程组合并，可解。
    -   **例 (无解):** $\{x \equiv 1 \pmod 6, x \equiv 2 \pmod 4\}$。
        -   $x \equiv 1 \pmod 6 \implies x \equiv 1 \pmod 2$ (奇数)。
        -   $x \equiv 2 \pmod 4 \implies x \equiv 2 \pmod 2 \implies x \equiv 0 \pmod 2$ (偶数)。
        -   奇偶性矛盾，无解。

#### **④ 要点与补充 (Key Points & Additional Notes)**
1.  **应用: 韩信点兵 (Han Xin's Problem):**
    -   问题: $x \equiv 2 \pmod 3, x \equiv 4 \pmod 5, x \equiv 6 \pmod 7$。
    -   分析: 可写为 $x \equiv -1 \pmod 3, x \equiv -1 \pmod 5, x \equiv -1 \pmod 7$。
    -   解: $x \equiv -1 \pmod{\text{lcm}(3,5,7)} \implies x \equiv -1 \pmod{105}$。
2.  **迭代法/代入法 (Substitution Method):** 另一种求解方法，无需分解模数，普适性强。
    a. 从第一个方程 $x \equiv a_1 \pmod{n_1}$ 得 $x = a_1 + k_1 n_1$。
    b. 代入第二个方程: $a_1 + k_1 n_1 \equiv a_2 \pmod{n_2}$，解出 $k_1$。
    c. 设 $k_1 = b + k_2 (n_2/\gcd(n_1,n_2))$，代回 $x$ 的表达式，得到满足前两个方程的通解 $x \equiv A \pmod{\text{lcm}(n_1, n_2)}$。
    d. 重复此过程，直至所有方程用完。

=== 文档 11: softmax-notes.pdf ===

### **Softmax 实现 (Implementation)**

#### **① 定义与概念 (Definitions & Concepts)**
*   **1.1 Softmax 函数 (Softmax Function):** 将 n 维实数向量 $x \in \mathbb{R}^n$ 转换为 n 维概率分布 $p$ 的函数。
*   **1.2 数值稳定性 (Numerical Stability):** 标准 Softmax 实现中，当 $x_i$ 值较大时，计算 $e^{x_i}$ 易导致数值上溢 (Overflow)。
*   **1.3 稳定化技巧 (Stabilization Trick):** 为解决上溢问题，在计算指数前，从向量 $x$ 的每个元素中减去其最大值 $x_{\max} = \max_i x_i$。该操作不改变最终概率结果。
*   **1.4 在线实现 (Online Implementation):** 一种高效算法，通过单次遍历数据同时计算最大值和归一化分母，旨在减少内存访问和计算パス (pass)，对 GPU 等并行计算设备尤其重要。

#### **② 公式与方程 (Formulas & Equations)**
*   **2.1 标准 Softmax (Standard Softmax):**
    $$ p_i = \frac{e^{x_i}}{\sum_{j=1}^{n} e^{x_j}} $$
*   **2.2 数值稳定 Softmax (Numerically Stable Softmax):**
    $$ p_i = \frac{e^{x_i - x_{\max}}}{\sum_{j=1}^{n} e^{x_j - x_{\max}}}, \quad \text{其中} \; x_{\max} = \max_j x_j $$
*   **2.3 在线实现更新规则 (Online Implementation Update Rules):**
    *   **初始化 (Initialization):**
        $$ m_0 = -\infty, \quad d_0 = 0 $$
    *   **迭代步骤 (Iterative Step for $i=1, \dots, n$):**
        *   更新当前最大值 (Update current max):
          $$ m_i = \max(x_i, m_{i-1}) $$
        *   更新归一化分母 (Update normalizer):
          $$ d_i = d_{i-1} \cdot e^{m_{i-1}-m_i} + e^{x_i-m_i} $$
    *   **最终概率 (Final Probabilities):**
        $$ p_i = \frac{e^{x_i-m_n}}{d_n} $$

#### **③ 常见错误与混淆 (Common Mistakes & Confusions)**
*   **3.1 直接实现 vs. 稳定实现 (Direct vs. Stable Implementation):**
    *   **直接实现:** 使用标准公式 $p_i = \frac{e^{x_i}}{\sum e^{x_j}}$，当 $x_i$ 很大时（如 > 709），$e^{x_i}$ 会导致浮点数上溢 (Overflow)。
    *   **稳定实现:** 使用 $p_i = \frac{e^{x_i-x_{\max}}}{\sum e^{x_j-x_{\max}}}$，由于 $x_i - x_{\max} \le 0$，所以 $e^{x_i-x_{\max}} \le 1$，有效避免上溢。
*   **3.2 实现效率对比: 朴素 vs. 在线 (Implementation Efficiency: Naïve vs. Online):**
    *   **朴素实现 (Naïve, 3-Pass):**
        1.  **Pass 1:** 遍历数据找到 $x_{\max}$。
        2.  **Pass 2:** 遍历数据计算分母 $d = \sum e^{x_j-x_{\max}}$。
        3.  **Pass 3:** 遍历数据计算每个 $p_i$。
        *   缺点: 多次遍历数据，在 GPU 上导致多次内核启动 (kernel launches) 和内存带宽瓶颈 (memory bandwidth bottleneck)。
    *   **在线实现 (Online, 2-Pass):**
        1.  **Pass 1:** **单次**遍历同时计算最终最大值 $m_n$ 和归一化分母 $d_n$。
        2.  **Pass 2:** 遍历数据计算每个 $p_i$。
        *   优点: 减少了数据遍历次数，显著提升 GPU 性能。
*   **3.3 在线更新公式的理解 (Understanding the Online Update Formula):**
    *   $d_i = d_{i-1} \cdot e^{m_{i-1}-m_i} + e^{x_i-m_i}$
    *   **第一项 $d_{i-1} \cdot e^{m_{i-1}-m_i}$:** 这是核心技巧。当最大值从 $m_{i-1}$ 更新为 $m_i$ 时 ($m_i > m_{i-1}$), 此项将之前基于旧最大值 $m_{i-1}$ 计算的累加和 $d_{i-1} = \sum_{j=1}^{i-1} e^{x_j-m_{i-1}}$ 进行重新缩放 (rescale)，使其等价于基于新最大值 $m_i$ 的累加和 $\sum_{j=1}^{i-1} e^{x_j-m_i}$。
    *   **第二项 $e^{x_i-m_i}$:** 加上当前元素基于新最大值的指数项。

#### **④ 关键点与额外说明 (Key Points & Additional Notes)**
*   **4.1 平移不变性 (Shift Invariance):** Softmax 函数对输入向量的平移操作是不变的，即 $softmax(x) = softmax(x+c)$ 对任意常数 $c$ 成立。稳定化技巧正是利用此性质，令 $c = -x_{\max}$。
*   **4.2 在线算法正确性 (Online Algorithm Correctness):** 其正确性可通过数学归纳法 (Proof by Induction) 严格证明，确保在单次遍历结束后得到的 $m_n$ 和 $d_n$ 与朴素多遍算法的结果完全一致。
*   **4.3 适用场景 (Applicability):** "在线"或"单遍"计算思想广泛应用于流数据处理 (stream data processing) 和大规模数据集上的统计量计算（如均值、方差），以最小化内存和计算开销。