Method that can match closely-related images (slight shifts in the way to image is moved/transformed)
- Fisheye distortion
- Transform
- Affine

General Overview:
1. Find "patches of similar color and shape"
2. Patches will generate an orientation to view
3. Use orientation and size of patch to match different patches
4. Filter for parallel line matches
5. Remove outliers where lines are intersecting and not closely related randomly for lin reg

