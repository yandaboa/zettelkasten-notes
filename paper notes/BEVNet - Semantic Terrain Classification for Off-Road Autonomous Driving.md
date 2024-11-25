https://sites.google.com/view/terrain-traversability/home#h.esrg71olrgxo

BEVNet = Birds Eye View Network
Uses a LIDAR sensor to create a cost map of the car's surroundings. The cost map includes both geometries and a discrete traversability rating

**Model architecture:**

![[Screenshot 2024-11-24 at 11.46.53 PM.png]]

**Method**
Supervised training approach - Given a dataset of semantically labeled lidar scans, the scans are mapped into the traversability/cost map. Model is then trained to be able to replicate this data.

**Novelties**
2. temporal aggregation
3. able to predict cost landscape in areas with limited LIDAR coverage
4. filtering out irrelevant obstacles, like branches or tree leaves that can be bypassed

New terms:
Sparse tensor - 
latent feature map - 
ConvGRU - 
Bayes filtering - 