**Rationale:**
- Increased images and image sensors in the world
- However, it is difficult for algorithms to accurately determine what the image data means
- For every 3 seconds, there are 15 more hours of content on YouTube

**Interdisciplinary Field:**
- Physics: Optics, Image Formation
- Biology/Psychology: Cognitive Science
- Computer Science/Mathematic/Engineering: Implementation/Information Retrieval/Algorithms

**History of Computer Vision:**
- 53 Billion Years Ago - No eyes, if food swam by, they would eat, if not they would just chill
- Within a very short period of time (10 million years), number of species went from a few to a few thousand
- Theories on the Evolutionary Big Bang: Potentially because the animals developed eyes
- Onset of Vision started this explosive speciation phase
- Animals can suddenly see, life became much more proactice (animals become prey/predator to survive)
- Vision is the biggest sensory system of almost all animals
- Humans: 50% of neurons in cortex work on visual processing

**What about Mechanical Vision?**
- One of the earliest cameras: Camera Obscura
	- Based on optics and pinhole camera theories
![[Pasted image 20240516111848.png]]

**Where did we come from?**
- Hubel & Wiesel stuck electric nodes in the back of a cat's brain to determine what sections are responsible for vision
- Simple Cells: Response to specific rotation and orientation
- Complex Cells: Response to light orientation and movement, some translational invariance, becomes more complex

**Block World:**
- One of the first PhD theses on computer vision
- Focused on how to interpret the world using digital vision

**Summer Vision Project:**
- Goal: In one summer, work on the bulk of the visual system to study it
- Laid the groundwork for the current problems in vision (50+ years) stemming from this one project

**Influential figures:**
- David Marr
- Wrote a book in the 70s about what he thinks vision is, How can we develop algorithms, etc.
- Thought process:
	- In order to take an image and arrive at a 3D representation, given an input image:
	- First, Primal Sketch (identify simple structures such as edges, bars, lines, curves, boundaries)
	- Second, 2 and 1/2-D sketch (surfaces, discontinuities, in-depth surface orientation)
	- Third, 3-D Model Representation (Create real 3D models of all the surfaces)

**Another important seminal group of work:**
- 70s: How can we move beyond the simple block world and start representing real-world objects?
- Problem: in 70s, data was extremely scarce and computers were extremely slow
- 2 Schools of thoughts came out about how to identify moving individuals:
	- 1: Generalized Cylinders
	- 2: Pictoral Structures
	- ![[Pasted image 20240516112559.png]]
- Late 80s: David Lowe tried to identify razors using edges, straight lines, and their connections

**Big flaw with earlier attempts: These were all niche examples or specific ones, no real generalized algorithms**
- "AI Winter"
- Funding/Enthusiasm for AI research dwindled
- "Expert Systems" failed to deliver on their promises
- However, subfields of AI continues to grow
	- Computer vision, NLP, robotics, compbio, etc.

*Core idea: If generalized CV is too hard, first try to identify generalized groupings/image segmentation*

**Face Detection:**
- Viola and Jones, 2001
- One of the first successful applications of machine learning to vision

**Recognition via Matching (2000s):**
- Featured-based object recognition
- Idea: To match an entire object to another object, it's very difficult (example: two separate angles of stop signs look different)
- However, observe there are several features that tend to remain similar relative to other nearby features
- Easier than pattern-matching the entire object

**Spatial Pyramid Matching:**
- There are certain features that can give us clues about what types of scenes are present
- Work takes different features in different parts and puts them together in a feature descriptor
- Finally process with support vector/Machine Learning on top of this
- Other algorithms:
	- *Histogram of Gradients*
	- *Deformable Part Model*

*Note: As we come into the 21st century, the internet now provides lots of large and high-quality images now*

**PASCAL Visual Object Challenge:**
- A dataset of 20 categories of images
- Essentially allows researchers to develop algorithms to test against the dataset to understand the performance of detecting these objects

**IMAGENET:**
- Around a similar time, a group of Stanford and Princeton individuals began to ask the question:
	- Are we at the point where we can identify the world of all objects?
	- Can we overcome the machine learning bottleneck of overfitting?
- One of the largest datasets of all images on the internet - then allows individuals to train on these datasets
- Downloaded billions of images, then classify with 10s of thousands of image categories
- 22k categories, 14M images
- Used for the Large Scale Visual Recognition Challenge:
	- 1,000 object classes
	- 1.4 million images
- By 2012 or so, the algorithms have become so effective that they are now on-par with humans
- Only took a few years for the field to achieve this feat
- Note 2012: Error rate dropped 10% because of Krizhevsky's CNN Model
- Thus the goal of this course is to understand what CNNs are (Deep Learning)

**HISTORY COMPLETE**

**CS231n Overview:**
- Class focuses on the *image classification problem*
- Looks at images, then picks amongst the set of all categories to best categorize the image

**Other Tasks:**
- Semantic Segmentation
- Object Detection
- Instance Segmentation
- Object Captioning
- Video Classification
- Multimodal Video Understanding
- Visualization & Understanding

**Neural Network:**
- The future of image processing
- 2012 influential paper (LOOK AT) - AlexNet: Krizhevsky et al.
- In 2015, 152 layers of visual processing
- Main takeaway: CNNs are the breakthrough algorithm
- Now, looking to tune and tweak the general framework

**Convolutional Neural Networks:**
- 1998: influential paper that was able to recognize handwritten notes
- Lecun et al.
- Takes in the pixels of an image and classify what letter it was
- What changed for current popularity?
	- Increased computations
	- Moore's Law
	- General increase in how fast chips are
	- Data-hungry, we now live in a world filled with data

**Course Philosophy:**
- Thorough and Detailed
	- Understand how to write from scratch, debug, and train convolutional neural network
- Practical
	- Focus on practical techniques for training these networks at scale, and on GPUs (e.g. will touch on distributed optimization, differences between CPU vs. GPU, etc.) Also look at state of the art software tools such as Caffe, TensorFlow, and (Py)Torch
- State of the art
	- Most materials are new from research world in the past 1-3 years
- Fun
	- Some fun topics such as Image Captioning (using RNNs)

**Syllabus:**
- Deep Learning Basics
	- Data-driven approaches
	- Neural Networks
	- Optimization
	- Etc.
- Convolutional Neural Networks
	- Convolutions
	- PyTorch/TensorFlow
	- Batch Normalization
- Computer Vision Applications
	- RNNs/Attention/Transformers
	- Object Detection and Segmentation
	- Style Transfer
	- Robot Learning
	- Human-centered AI
	- Fairness & Ethics

