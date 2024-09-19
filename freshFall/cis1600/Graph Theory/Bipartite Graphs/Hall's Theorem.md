
**Proof:**
$G=(x \cup y, E)$
G has a matching that saturates every vertex in X iff Hall's condition is true:
$\forall S \subseteq X, |N(S)| \geq |S|$
($\impliedby$) Hall's condition $\implies$ G has a matching that saturates every vertex in X.
Proof: Induction on m = |X| (cardinality of X)
**IH:** $|X| = k$
**BC:** $|X| = 1$
**IS:** Case 1: $\forall S \subset X, |N(S)| > |S|$
Case 2: $\exists W \subset X, |N(S)| = |S|$