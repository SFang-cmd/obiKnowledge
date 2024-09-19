Input: Alphabet $S$ text contains n letters from $S$. $\forall x \in S, fx:$ fraction of the ...

Proof of Correctness:
**Lemma:** $ABL(T)=ABL(T') + f_{w}$
(Average bits per length)
(here the $f_{w}$ needs to account/adjust for one side of the binary divide for $f_{w}$)

**Induction Hypothesis:**
Assume that Huffman works when $|S|=k$, for some int $k \geq 1$

**Base Case:**
$|S|=1, |S|=2$

**Induction Step:**
Assume for contradiction that Huffman fails to vive an optimal solution when $|S| = k+1$

That is, assume that T is not optimal. Let $Z$ be an optimal tree in which two lowest frequency letters are asserted to sibling leaves at the highest depth

$ABL(Z)=ABL(Z') + f_{w}$
$ABL(T)=ABL(T')+f_{w}$
(Contradiction, since the left side is negative, but the right side is greater than or equal to 0.)

(By IH, we know that $T'$ is an optimal Huffman tree, so at best, $Z'$ is comparable, if not having more bits per length compared to $T'$)

Runtime:
$|S| = s$
$T(s)=T(s-1) + s$
$=\theta(s^{2})$

Can't use presort, since we're not sure about the frequencies

*Use priority queue:*
BuildMinHeap - O(s)

Execute ExtractMin twice, returns a function, $InsertKey(\omega)$