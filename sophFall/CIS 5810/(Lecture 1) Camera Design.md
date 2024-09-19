- Use of having multiple cameras - can detect perspective/depth
- Using 12 cameras, can set up different exposures, to combine for better light levels

Depth & HDR:
- Simultaneously capture for Depth and HDR
- Resilient to sensor variations

Pinhole Camera Model
- Pinhole Model
	- Captures **pencil of rays** - all rays through a single point
	- The point is called **Center of Projection (COP)**
	- The image is formed on the **Image Plane**

Turns out, the **brain is also a pinhole camera**
- Receptive field mapping
- Brain maps up to down, left to right
- The brain will instantly flip the image

Camera with lens
- Way to avoid camera pinhole focus problem: Use lens to refract the light rays
- In order to focus on various different depths, need to create autofocus sensors

Camera Internals
- Lens
- CCD Sensor
	- When light hits the sensor, the voltage gets changed and read out into a digital signal
	- Charge up the sensor, when photon hits, it gets discharged
	- More consistent sensor values if fully charged

How to get colors?
- Filter RGB colors
	- Have blue filter that only lets blue in, green filter that lets green in, and red that lets red in
	- Have 3 CCD's
	- TOO EXPENSIVE
- Instead:
	- Use Bayer Grid Pattern in one CCD - 
	- [G  B]
	- [R  G]
	- Then, interpolate neighboring light intensities into each grid location
	- Each company (Sony, Canon, Nikon, etc.) have different methods of interpolation, which is why the colors are different

Computer Vision:
- An image is a 2-dimensional table of numbers, a 2D matrix (or 3D if RBG channels occur)
- I[i,j] is the sensor value at location $y = i, x = j$
- Brain is very good at adapting to color changes (surrounding colors doesn't change the way we perceive intensity such as shadows)

**There is an overall RBG value to determine the intensity, then a ratio between the values to determine the color**

Dimensionality Reduction Machine:
- Cameras reduce 3D world to 2D world
- Loss of Angles and Distances (length)
- Think if infinite points on an image as a direction on the horizon

Focal Length
- What: Roughly has to do with how big the lens is
- Paparazzi camera, we can see the lens really stick
- Larger focal length, shorter field of view
- Small focal length, larger field of view

*Note:* $(u_{ccd},v_{ccd})$ vectors are annotated on the projection plane, not the sensor

Homogeneous Coordinate:
- A point in Euclidean space
- Is is more customary for individuals to use polar homogeneous coordinates?
- Same ratio

Kappa matrix (Calibration Matrix)
- [f_x, , p_x]
- [ , f_y, p_y]
- [     ,      , 1]