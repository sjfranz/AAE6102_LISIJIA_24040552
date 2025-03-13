# AAE6102 Assignment 1

**Name: Sijia Li**

**Student number: 24040552R**

### 1. Acquisition

#### 1.1 Acquisition for open-sky

The general acquisition showing which satellite is acquired is illustrated in Figure 1.1.1. This is obtained by setting the acquisition threshold to be 1.5. It can be observed that the satellite with PRN 16 has the strongest power. A further observation of the acquisition for PRN 16 is shown in Figure 1.1.2, where a time-frequency correlation is conducted to achieve a fine acquisition. 

**Figure 1.1.1** Acquisition results for all satellites

<img src="https://github.com/sjfranz/AAE6102_LISIJIA_24040552/blob/main/Figure/acquisition_open_sky.jpg" alt="Acquisition Result" style="zoom:80%;" />

**Figure 1.1.2** Acquisition result for PRN 16

<img src="https://github.com/sjfranz/AAE6102_LISIJIA_24040552/blob/main/Figure/acq_prn16_opensky.jpg" alt="Acquisition Results (PRN 16)" style="zoom:80%;" />



#### 1.2 Acquisition for urban

**Figure 1.2.1** Acquisition for all satellites

<img src="https://github.com/sjfranz/AAE6102_LISIJIA_24040552/blob/main/Figure/acquisition_urban.jpg" style="zoom:80%;" />

**Figure 1.2.2** Acquisition result for PRN 1

<img src="https://github.com/sjfranz/AAE6102_LISIJIA_24040552/blob/main/Figure/acq_prn1_urban.jpg" style="zoom:80%;" />

### 2. Tracking

In order to observe the correlation results for open-sky and urban, the multicorrelators are used with chip space being 0.1.  Figure 2.1 shows the correlation result for open-sky, and Figure 2.2 shows the correlation result for urban. It is noted that both the open-sky and the urban are plotted at the 10s epoch.

**Figure 2.1** Correlation result for open-sky

<img src="https://github.com/sjfranz/AAE6102_LISIJIA_24040552/blob/main/Figure/multicorr.jpg" style="zoom:80%;" />

**Figure 2.2** Correlation result for urban

<img src="https://github.com/sjfranz/AAE6102_LISIJIA_24040552/blob/main/Figure/multicorr_urban.jpg" style="zoom:80%;" />

It can be observed that the compared to urban scenario, correlation result for open-sky is more outstanding, especially in terms of the shape of the auto-correlation function (ACF). Specifically, the ACF shape for open-sky is more symmetric, while the ACF shape for urban is distorted mainly due to the severe multipath effect in urbanized settings.

### 3. Navigation Data Decoding

The navigation message is shown in Figure 3.1, and the detailed message of this satellite is listed in Table 3.1.

**Figure 3.1** Navigation message bit

![](https://github.com/sjfranz/AAE6102_LISIJIA_24040552/blob/main/Figure/navdata.jpg)

**Table 3.1** Navigation message

| Parameter  |         Value          |
| :--------: | :--------------------: |
|    C_ic    | -1.005828380584717e-07 |
|  omega_0   |   -1.674261428851700   |
|    C_is    | 1.359730958938599e-07  |
|    i_0     |   0.971603403113095    |
|    C_rc    | 2.376875000000000e+02  |
|   omega    |   0.679609496852005    |
|  omegaDot  | -8.012833766689160e-09 |
|  IODE_sf3  |           9            |
|    iDot    | -4.893060958486360e-10 |
|  idVaild   |        [2,0,3]         |
| weekNumber |          1155          |
|  accuracy  |           0            |
|   health   |           0            |
|    T_GD    | -1.024454832077026e-08 |
|    IODC    |          234           |
|    t_oc    |         396000         |
|    a_f2    |           0            |
|    a_f1    | -6.366462912410498e-12 |
|    a_f0    | -4.069251008331776e-04 |
|  IODE_sf2  |           9            |
|    C_rs    |   23.343750000000000   |
|   deltan   | 4.246605459591447e-09  |
|    M_0     |   0.718116855169473    |
|    C_uc    | 1.389533281326294e-06  |
|     e      |   0.012296279077418    |
|    C_us    | 7.687136530876160e-06  |
|   sqrtA    | 5.153771322250366e+03  |
|    t_oe    |         396000         |
|    TOW     |         390102         |

### 4. Position and Velocity Estimation

After tracking, both the pseudorange and the doppler for each satellite are calculated, and compensated based on the satellite clock error and the satellite clock drift. The corrected pseudorange and doppler are used for weighted least squares for further position and velocity estimation, where the weight matrix is constructed via the elevation angle of the satellites.

#### 4.1 Position and velocity estimation for open-sky

**Figure 4.1.1** Position estimation

<img src="https://github.com/sjfranz/AAE6102_LISIJIA_24040552/blob/main/Figure/opensky_pos.jpg" style="zoom:80%;" />

**Figure 4.1.2** Velocity estimation

<img src="https://github.com/sjfranz/AAE6102_LISIJIA_24040552/blob/main/Figure/opensky_vel.jpg" style="zoom:80%;" />

#### 4.2 Position and velocity estimation for urban

**Figure 4.2.1** Position estimation

<img src="https://github.com/sjfranz/AAE6102_LISIJIA_24040552/blob/main/Figure/urban_pos.jpg" style="zoom:80%;" />

**Figure 4.2.2** Velocity estimation

<img src="https://github.com/sjfranz/AAE6102_LISIJIA_24040552/blob/main/Figure/urban_vel.jpg" style="zoom:80%;" />

#### 4.3 Comparison with ground truth

For open-sky, it can be observed that the position estimation for open-sky is very close to the ground truth, with a mean deviation of 1.49m. However, for open-sky, the deviation of the mean of the estimation and the ground truth is as high as 151.2m.

#### 4.4 Impact of multipath on WLS

For position WLS solution, the multipath has a sever impact on the pseudorange measurement, due to its effect on the ACF shape. The tracking will end up with a wrong chip delay. For velocity WLS solution, the multipath deteriorate the doppler measurement in terms of the velocity direction, since the signal is reflected and the doppler can be measured with bias. 











