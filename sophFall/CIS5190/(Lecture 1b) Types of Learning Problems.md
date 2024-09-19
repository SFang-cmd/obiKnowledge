Types of Learning
- Supervised Learning
	- Input: Examples of inputs and desired outputs
	- Output: Model that predicts output given a new input
- Unsupervised Learning:
	- Input: Examples of some data (no "outputs")
	- Output: Representation of structure in the data
- Reinforcement Learning:
	- Input: Sequence of agent interactions with an environment
	- Output: Policy that maps agent's observations to actions
	- Ex. Robot operating in an environment, generate its own data/operations that can help generate better robots or better actions

Examples:
- Supervised Learning: Regression
	- Given $D = \{(x_1,y_1),(x_2,y_2),...,(x_n,y_n)\}$
	- Learn a function $f(x)$ to predict *y* given *x*
		- y is numeric == regression
	- Sea ice and carbon output for instance
- Supervised Learning: Classification
	- Given $\{(x_1,y_1),(x_2,y_2),...,(x_n,y_n)\}$
	- Learn a function $f(x)$ to predict $y$ given $x$
	- Determine whether a tumor is malignant or benign
		- $x$ can be multi-dimensional
		- Each dimension corresponds to an attribute:
			- Patient age
			- Clump thickness
			- Tumor color
			- Distance from optic nerve
			- Cell type
		- Cell type is the most telling feature, but it's risky to do a biopsy of the eye
- Unsupervised Learning
	- Given $x_1,x_2,...,x_n$ (without labels)
	- Output hidden structure behind the x's... connected to "learning as compression"
	- e.g. "clustering" - data that has multiple groups and identify those groups
- Reinforcement Learning
	- Given a sequence of states and actions with (delayed) rewards, output a policy
		- Policy is a mapping from states --> actions. It tells you what to do in a given state
	- Examples:
		- Game playing
		- Robot grasping an object
		- Balance a pole on your forehead
		- Medical treatment plans for patients

Example applications of ML:
- Everyday applications:
	- Spam emails
	- Self-driving cars
- Scientific Discovery:
	- Deepmind predicting a structure for CASP13 target protein.
	- Predict black holes and generate an image of what it looks like
	- Detect mouse feet through cameras

