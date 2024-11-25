LIDAR data can be inaccurate in conditions with high climate interference (snow, rain, dust), and when used with fast moving vehicles. TerrainNet aims to solve these issues by building a semantic and geometric map using only RGBD camera data. Depth data is obtained through calculations that utilize 2+ cameras.

**Method**

Training data is collected using LIDAR scans. The 2-D geometric map is akin to an elevation map, with measures $h_{min}, h_{max},$ and $h_{ceiling}$ stored for each grid in the 2-D map. Simple numerical methods are used to compute the elevation. Next, a distribution of the grid's semantics is created by aggregating the labeled points in the LIDAR point cloud. 
- when doing semantic labeling, doesn't each different environment require a creation of a custom dataset? or is it that the labeled points are more generalizable labels, like traversability, slip, etc?

**Model Architecture**

![[Screenshot 2024-11-25 at 1.20.44 AM.png]]

**New Terms:**
- List-Splat-Shoot (LSS) - 
- backproject - 