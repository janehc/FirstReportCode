READ ME
-------------------------------------------------------------------

#The images present are used in the python file 'Code for Report'

In 'Code for Report':

#1: Regular 3 phase SFDI Code
This code takes 6 sample open source data images from OpenSFDI [1] and processes them to extract their absorption and reduced 
scattering maps using regular 3 phase spatial frequency domain imaging. First, the six images are processed to obtain reflectance
maps. Then, using reference phantom data also available from [1], these reflectance images are calibrated to get diffuse reflectance
images. From these, using a look up table, the absorption and reduced scattering coefficient maps can be determined via cubic spline
interpolation. This cell will plor a map of AC and DC diffuse reflectance values and a map of the absorption and reduced scattering 
coefficients. 



#2: Filter and Shift Method SSOP Code
This code used single snapshot of optical properties method to obtain optical proeprty maps via a filter and shift technique. This
code uses just a single image from [1] instead of the six used before and processes in the spatial frequency domain. This method filters
high and low frequencies to obtain DC and AC images respectively via inverse Fourier transform after filtering, and in the AC image case 
the high frequency has to be shifted to the centre after the lower frequency and other high frequency are masked. Again, a 
reflectance map is first obtained and then reference phantom images are used to calibrate this image to obtain diffuse reflectance
maps. These maps are related to absorption and reduced scattering properties via a cubic spline interploation in a look up table.
The AC and DC diffuse reflectance maps are plotted as well as the optical propery maps for this technique. 



#3: Hilbert Transform Method SSOP Code
This code is the same as #2, except instead of filtering out the centre low frequency and left high frequency, and shifting the right high
frequency to the centre and applying an inverse Fourier transform to obtain the AC image, just the centre low frequency is masked and an
inverse Fourier transform is applied, followed by a Hilbert transform to obtain the AC image. This technique gives a better quality image.
The AC and DC diffuse reflectance maps are plotted as well as the absorption and reduced scattering maps for this technique.



#4: Hilbert Transform SSOP Method with my own images code
This code performs the same technique as #3, except instead of using open source sample data from [1] it uses my own images I captured 
in the lab bench-top system. Since these images were in the lab, I do not yet have reference phantom images so the diffuse reflectance
maps used are not calibrated. Therefore the optical property maps obtained are not accurate (they will be once I can calibrate the bench
top system with phantoms of known optical properties). The AC and DC diffuse reflectance maps are plotted as well as the absorption and 
reduced scattering maps for this technique.



#5: Fourier Transform Profilometry Code
This code takes images constructed in Blender and reconstructs their shape. Two images are inputted - one with just a sinusoidal pattern
and a second with this same sinusoidal pattern projected onto an object. Using the Hilbert transform SSOP method, the high frequency 
information is obtained for both input images. The phase is then obtained. The phase is unwrapped and then the height is calculated. Outliers
from the height data are removed and a 3D height plot of the object is produced. This piece of code can be altered to input images from the 
bench top system instead of from Blender.


[1]: M. B. Applegate, J. P. A. Jr, S. M. Tabassum, K. Tilbury, R. B. Saager, D. Roblyer, 
     M. B. Applegate, K. Karrobi, J. P. A. Jr, W. Austin, S. M. Tabassum, E. Aguénounon, 
     K. Tilbury, R. B. Saager, S. Gioux, and D. Roblyer, “OpenSFDI : an open-source guide 
     for constructing a spatial frequency domain imaging system,” vol. 25, no. 1, 2020. 