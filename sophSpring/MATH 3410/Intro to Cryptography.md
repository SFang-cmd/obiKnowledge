**Homework:**
**Please read from the textbook:**
- 1.1, 1.1.1, 1.6, 1.7, 1.7.1,
- 5.2, 5.2.1
**Review:** 5.1, 5.1.1, 5.1.2, 5.1.3
**Exercises:** 1.1 a,b,c (p. 47-48) (Cut out cipher wheel)
______
Fun reading
David Kahn: The Codebreakers
Simon Singh: The Code Book

**A Brief History in Cryptography:**
- Cipher Wheels
- Rotor Machines
- Wadsworth (1817)
- Wheatstone (1867)
- **Typical of the era**
	- People used a secret key (Contents of a concentric disk and initial position)
- Later: Using gears, disks can rotate at different speeds
- Two inventions fueled interest in civilian cryptography:
	- 1844: Invention of Telegraph
	- 1890: Invention of Radio
- WWII:
	- Very complex rotor machines for codes
	- Needed ~30,000 women operators
- 1960s - 1970s
	- Using computers to encrypt, can design very robust ciphers
- 1975: Data Encryption Standard D.E.S.
- Not broken for 25 years, then 3 D.E.S.
- 2001: Advanced Encryption Standard (A.E.S.)
	- Result of international, public competition winner
	- Belgian Team
- Creation of Cryptography Regulatory Body:
	- U.S. National Institute of Standards and Technology (NIST)

**Key Transition:**
- Traditional Encryption is **Symmetric**
	- Same key used for encryption and decryption
	- Alice - Takes an input message, $m$ and key $k$ and feeds it into encryption algorithm $E$ to create $E_{k}(m) = c$
	- Bob - Reverses the process with decryption algorithm $D$ to get $D_{k}(c) = m$
	- If $k$ leaks, then message can be broken, but also vulnerable to attack
- Attack Models
	1. Ciphertext only attack:
		- Eve intercepts a ciphertext $c$
	2. Known plaintext attack (KPA):
		- Eve intercepts a **random** plaintext/ciphertext pair (m,c)
	3. Chosen Plaintext Attack (CPA):
		- Eve specifies plaintext $M$ and observes ciphertext $c$
		- Looks at the set encryption to try to figure out the encryption key
	1. Chosen ciphertext Attack (CCA):
		- Eve specifies ciphertext $c$ and observes the corresponding plaintext $m$
		- Basically, Eve can try to figure out the cipher given a decrypted message from an encryption
	2. Good ciphers should resist CPA and CCA
- **Important:**
	- A successful attack does **not** require Eve to recover a secret key!
	- It suffices that, if Even is given (or observes)
		- $(m_{1}, c_{1}), \dots, (m_{j}, c_{j})$,
	- Then Eve can decrypt
		- $m_{j+1}=D(c_{j+1})$

**Information-Theoretic (Unconditional) Security**
- Sections 5.3 and 5.6
- Making the substitution ciphers "secure"
- **Idea:** Change the key often (e.g. Vigenere's Cipher)

| Plaintext  |       |       | ... |      |
| ---------- | ----- | ----- | --- | ---- |
| Key        | $k_1$ | $k_2$ | ... | $k_7 |
| Ciphertext |       |       | ... |      |
- If you continued to extend the key length, eventually the key would be long enough to change the key for every bit!
	- Totally at random!!!

**Vernam 1917**
- One-tim pad (O.T.P)
- Secret Key: Random bit string as long as the plaintext
- Ex.
	- PT:   0 1 1 0 1 1 1 0 0 1 0 1 1
	- Key: 0 1 0 1 1 0 1 1 0 0 1 1 0 (XOR both ~ + mod 2)
- Cipher Text: 0 0 1 1 0 1 0 1 0 1 1 0 1
- **Decryption** is also by XOR
	- So very fast Encryption and Decryption
- Why is this secure?
	- **Shannon 1949**

