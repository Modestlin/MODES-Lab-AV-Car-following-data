# MODES-Lab-AV-Car-following-data
Car-following behavior data in autonomous driving scenarios

## Overview
This dataset contains processed longitudinal car-following behavior data derived from the ​**Waymo Open Dataset**, specifically focusing on autonomous vehicle (AV) operations in stable traffic scenarios. The data captures interactions between leading vehicles (LVs) and following AVs (FAVs) to analyze stochastic car-following distances and speed regulation patterns.

---

## Key Features
### 🚗 ​**Data Source**
- Primary dataset: [Waymo Open Dataset](https://waymo.com/open) (Ettinger et al., 2021)

### 🔍 ​**Scenario Filtering Criteria**
1. ​**Speed Stability**  
   - LV maintains an average speed of ​**20.2 m/s** (72.7 km/h or 45.2 mph)
   - Speed difference between LV and FAV ≤ ​**1 m/s** (3.6 km/h)
2. ​**Distance Consistency**  
   - FAV attempts to maintain a stable spatial gap
   - Excluded transient acceleration/deceleration phases

## 📊 Core Variables
| Variable             | Unit      | Description                                                                 |
|----------------------|-----------|-----------------------------------------------------------------------------|
| `Trajectory_ID`      | -         | Unique identifier for each car-following trajectory                        |
| `Time_Index`         | ms        | Timestamp from scenario start (0 = initial observation)                    |
| `ID_LV`              | -         | Unique ID of the leading vehicle in the scenario                           |
| `Type_LV`            | category  | Vehicle type classification (e.g., passenger, truck, motorcycle)           |
| `Pos_LV`             | [x,y,z] m | 3D position of leading vehicle (WGS84 projected coordinates)               |
| `Speed_LV`           | m/s       | Instantaneous speed of leading vehicle                                     |
| `Acc_LV`             | m/s²      | Longitudinal acceleration of leading vehicle (+ = acceleration)            |
| `ID_FAV`             | -         | Unique ID of the following autonomous vehicle                              |
| `Pos_FAV`            | [x,y,z] m | 3D position of following AV                                                 |
| `Speed_FAV`          | m/s       | Instantaneous speed of following AV                                        |
| `Acc_FAV`            | m/s²      | Longitudinal acceleration control input of AV (+ = acceleration)           |
| `Spatial_Gap`        | m         | ​**Bumper-to-bumper distance** between LV and FAV                            |
| `Spatial_Headway`    | m         | ​**Center-to-center distance** (includes vehicle length compensation)       |
| `Speed_Diff`         | m/s       | `Speed_LV - Speed_FAV` (positive when LV faster)  

## Reference
Ettinger, S., Cheng, S., Caine, B., Liu, C., Zhao, H., Pradhan, S., Chai, Y., Sapp, B., Qi, C.R., Zhou, Y., Yang, Z., Chouard, A., Sun, P., Ngiam, J.,
Vasudevan, V., McCauley, A., Shlens, J., Anguelov, D., 2021. Large scale interactive motion forecasting for autonomous driving: The waymo
open motion dataset, in: Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV), pp. 9710–9719.
