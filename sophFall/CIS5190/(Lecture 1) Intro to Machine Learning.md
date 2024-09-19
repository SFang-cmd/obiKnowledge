ML for Prediction:
- ML Automates the generation of "models" from data
- New input $x$ --> $f(.)$ --> $f(x)$

Example: Rediscovering Newton's 2nd Law
- How can we predict the acceleration $a$ of an object when we push it?
- ML Framing of this problem:
	1. Task (T) - Predict acceleration $a$ given pushing force $F$, mass $m$
	2. Performance Measure (P)
	3. Experience/Data (E)

Data In, Model Out:
- ML Design (hypothesis class, loss function, optimizer, hyperparameters, features,...)
- ML is essentially finding function values for a function
- **Hypothesis Class:** The class of functions from which the ML procedure must pick one to fit the data
- **Loss function:** *What* it means to "fit" the data: a function that has high values for bad fits, low for good fits
- **Optimizer:** How to search for the function that best fits the data
- Example hypothesis class (for varying values of $w_0,w_1,w_2,w_3,w_4,w_5$)
	- $a=w_0+w_1F+w_2m+w_3(F-m)+w_4(F*m)+w_5(\frac{F}{m})$
	- Learning = finding "good" values for the *weights* $w_{0,}w_{1,}..., w_5$
- (As early as Kepler and Newton used pseudo learning to find their laws of motion)

ML Workflow:
- Framing an ML problem (e.g. Mitchell's P, T, D)
- Class Project
	- Data curation (sourcing, scraping, collection, labeling)
	- Data analysis / visualization: Figuring out what are suitable structures/loss functions, etc to apply to the ML model
- Main focus of this class
	- ML Design (hypothesis class, loss function, optimizer, hyperparameters, features,...): What the model structure looks like
	- Train model: Apply parameters and find optimal values for the ML model
	- Validate / Evaluate: Verify effectiveness, etc.
- Deploy (and generate new data)
- Monitor performance on a new data

Learning is "Compression":
- Learning produces a function $f(.)$ that is a "digested" version of the data inputs
- Ex.
	- Dataset size = (N=7 data entries) * (D=2 features + 1 label) = 21 floats
	- "Model" / learned function size = 6 floats
	- Dataset is compressed to smaller amounts of data
- **Good learning should always lead to some form of compression**

What if we use more model parameters?
- More parameters may make it seem more well-fit to the data entries, but could be not effective to total dataset
- How do we know this is a bad result?
	- Collect more data!

Task specification in ML: programs --> examples
```python
def compute_force(m, a):
	'''
	returns force (in N) needed to move mass m (in kg) at 
	acceleration a (in m/s^2)
	'''
	F = m * a
	
	return F
```
- Very hard to find what aspects of an image can help you determine what a cow, etc.
- Instead, used Machine Learning

When should we use Machine Learning?
- Predict fashion in 20 years - No, probably (low data, low understanding)
- Adding two numbers - NO (too simple)
- Solving differential equations - YES Sometimes (faster predictions that don't involve step-wise solving)
- Flying rockets to other planets - NO (not interpretable)
- Checking large prime numbers - NO (we do not know whether the machine learning will produce a correct algorithm)
- Weather forecasting - Maybe? (some data and some forecasting, but not all)
- Recognizing animals from pictures - YES!
- Make art and music - YES!
- Get robots to make sandwiches - YES!

Summarizing
- Various conceptual views of machine learning:
	- Systems that improve with experience
	- Generating models from data
	- Programs --> examples to specify a task toa. computer
	- Compressing data
	- ...
- All of these are correct

