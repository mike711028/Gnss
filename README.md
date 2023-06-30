# Gnss
## Geographic coordinate system
The **geographic coordinate system (GCS)** is a spherical or ellipsoidal coordinate system for measuring and communicating positions directly on the Earth as latitude, longitude.

<p align="center">
<img src=img/Geographic%20coordinate%20system.png>
</p>

Reference:

[[1]IBM Geographic coordinate system](https://www.ibm.com/docs/en/informix-servers/12.10?topic=data-geographic-coordinate-system)

[[2]wikipedia Geographic coordinate system](https://en.wikipedia.org/wiki/Geographic_coordinate_system)

## Geodetic Coordinates
**Geodetic coordinates** are a type of curvilinear orthogonal coordinate system used in geodesy based on a reference ellipsoid. They include **geodetic latitude** (north/south) ϕ, **longitude** (east/west) λ, and **ellipsoidal height** h (also known as geodetic height). The triad is also known as Earth ellipsoidal coordinates.

> Get one more parameter(height) than GCS

<p align="center">
<img src=img/Geodetic%20coordinates.png>
</p>

Reference:

[[1]wikipedia Geodetic coordinates](https://en.m.wikipedia.org/wiki/Geodetic_coordinates)

## ECEF Coordinate System
The **Earth-centered, Earth-fixed coordinate system** (acronym **ECEF**), also known as the **geocentric coordinate system**, is a cartesian spatial reference system that represents locations in the vicinity of the Earth (including its surface, interior, atmosphere, and surrounding outer space) as X, Y, and Z measurements from its center of mass.​

<p align="center">
<img src=img/ECEF%20coordinate%20system.png>
</p>

Reference:

[[1]wikipedia Earth-centered, Earth-fixed coordinate system](https://en.m.wikipedia.org/wiki/Earth-centered,_Earth-fixed_coordinate_system)

## Geodetic Coordinates to ECEF
Geodetic coordinates(latitude ${\phi}$, longitude ${\lambda}$, height ${h}$) can be converted into ECEF coordinates using the following equation:

$$
\begin{align*}
X &= (N(\phi)+h)\cos(\phi)\cos(\lambda)  \\
Y &= (N(\phi)+h)\cos(\phi)\sin(\lambda) \\
Z &= ({b^2 \over a^2} N(\phi)+h)\sin(\phi) \\
  &=((1-e^2)N(\phi)+h)\sin(\phi) \\
  &=((1-f)^2 N(\phi)+h)\sin(\phi)
\end{align*}
$$

$$
\begin{align*}
f   &= 1 - {b \over a} \\
e^2 &= 1 - {b^2 \over a^2} \\ 
N(\phi) &= {a^2 \over \sqrt{a^2 \cos^2(\phi) + b^2 \sin^2(\phi)}} 
         = {a \over \sqrt{1 - e^2 \sin^2(\phi)}} \\
f &\text{ : flattening of the ellipsoid} \\
a &\text{ : the equatorial radius(semi-major axis)} \\
b &\text{ : the polar radius(semi-minor axis)}
\end{align*}
$$

Reference: 

[[1]wikipedia Geographic coordinate conversion](https://en.m.wikipedia.org/wiki/Geographic_coordinate_conversion)

## ECEF to NED

NED coordinates is similar to ECEF in that they're Cartesian, however they can be more convenient due to the relatively small numbers involved, and also because of the intuitive axes. NED and ECEF coordinates can be related with the following formula:

$$
P_{NED} = R^{T}(P_{ECEF} - P_{Ref})
$$

where $P_{NED}$ is a 3D position in a NED system. $P_{ECEF}$ is the corresponding ECEF position. $P_{Ref}$ is the reference ECEF position (where the local tangent plane originates), and $R$ is a rotation matrix whose columns are the north, east and down axes. $R$ may be defined conventiently from the latitude $\phi$ and longtitude $\lambda$ corresponding to $P_{Ref}$:

$$
R = \begin{bmatrix} -\sin(\phi)\cos(\lambda) & -\sin(\phi)\sin(\lambda) & \cos(\phi)\\
-\sin(\lambda) & \cos(\lambda) & 0 \\
-\cos(\phi)\cos(\lambda) & -\cos(\phi)\sin(\lambda) & -\sin(\phi)
\end{bmatrix}
$$

<p align="center">
<img src=img/Local%20tangent%20plane%20coordinates.png>
</p>

Reference:

[[1]wikipedia Local tangent plane coordinates](https://en.m.wikipedia.org/wiki/Local_tangent_plane_coordinates)


