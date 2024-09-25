- Over the last century, Geometry and Linear Algebra have merged because we can think of geometrical operations as linear algebra transformations

**Homogeneous Coordinates:**
- $(x,y) \to (x,y,1)$: A point in Euclidean space ($R^{2}$) can be represented by a homogeneous representation in Projective space ($p^2$) (3 numbers)
- $= f(x,y,1)$
- $=\lambda(x,y,1)=(X,Y,Z)$
- Only care about the direction of the point, so all points in 3D space will radiate outwards
- $\lambda$ is the length to reach a point in space $(X,Y,Z)$

**3D Point Projection (Metric Space):**
- $(X,Y,Z)\to (u_{ccd},v_{ccd})=\left( f_{m} \frac{X}{Z}, \dots \right)$

**Camera Model (3rd Person Perspective):**
- As you move, while the image plane may move, the point in space does not
- (Test: when you move your head, if you move slow, the eyes can stabilize your movements, when it goes really fast, the stabilization doesn't work as well)
- 8 numbers is the maximum you need to record a transformation

**Image Warping (Coordinate Transform):**
- For an image $I_{1}(u)$, every pixel can be correlated to a different image pixel $I_{2}(v)$
- Thus, $I_{2}(v)=I_{1}(u)$
- $t_{x},t_{y}$ is NOT the center of rotation when transforming

**Perspective Transform (Homography):**
- The floor has been transformed to a different plane
- Set by clicking on 4 points
- **All camera transformations can be thought of as a homography**

