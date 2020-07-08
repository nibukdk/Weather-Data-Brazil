# Weather Data Analysis

## Data Source


https://www.kaggle.com/PROPPG-PPG/hourly-weather-surface-brazil-southeast-region

## Info On Some Columns


1. Instant Air Temperature (celsius degrees) = temp
2. Maximum Air Temperature (celsius degrees) = tmin
3. Minimum Air Temperature (celsius degrees) = tmax
4. Relative Humidity of Air (%) =hmdy
5. Maximum Relative Air Humidity (%) =hmax
6. Minimum Relative Air Humidity (%) = hmin
7. Instant Dew Point (celsius degrees) = dewp
8. Maximum Dew Point (celsius degrees)=dmax
9. Minimum Dew Point Temperature (celsius degrees) = dmin
10. Instant Air Atmospheric Pressure (millibars) =stp
11. Maximum Air Atmospheric Pressure (millibars) = smax
12. Minimum Air Atmospheric Pressure (millibars)= smin
13. Instant Wind Speed (metres per second) = wdsp
14. Wind Direction (radius degrees) = wdct
15. Wind Gust Intensity (metres per second) = gust
16. Solar radiation  =  gbrd
17. Precipitation (milimetres) = prcp
18. Elevation = elvt
19. Observation Datetime = mdct
20. Observation Date = date
21. Station number (INMET number) for the location = inme
22. The year (2000-2016) : yr
23. The month (0-12) : mo
24. The day (0-31): da
25. The hour : hr

*Not all the columns are mentioned in this list*


## Null Columns Correlations

![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Heatmap%20Null%20df.png)

The columns gust and wdsp have high correlation since they are both properties of wind. Moreover, both seem to be affected by properties of temperatures positively. 

Similary, Solar Radiation(GBRD) is also the affected by temperatures,gusts and windspeed respectively in order from higher to lower correlation. 

Dewpoint also has higher correlatin with temperature, while the highest with properties of humidity(hmin, hmax).

Lets plot the properties that have higher correlation with each other in heatmap to visualize null rows.

### Null value fill logic

After sorting the columns it seems, for all the missing values in gust there are missing values in windspeed(check notebook). But according to correlation heatmap, since gust and windspeed have higher realtion than with temperature.
Lets fill the rows  where windspeed has null values but gust does not with weighted mean of windspeed by gust column. i.e create a mask where wdsp is null and gust in not null. Then divide that range again into three interval just to be more precise.

After that apply  interval technique to fill remaining rows with wighted mean of temperature columns but five intervals this time. 


## Data share By Province

![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Provinces%20Proportions.png)

It seems abot 50% of the data is related to *Minas Gerlas* province of Brazil.


## Weathers By Provinces

![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Avg%20Weather%20Factors.png)

Province *Espirito Santo* is taking the top spot on average weather factors by province. While *Minas Gerias* and *Rio de Janerio* both share similar triats. 

## Temperatures

### Instant Temperatrue City Yealy

![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Avg%20Temp%20By%20City.png)


### Avereage Yealy

![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Avg%20Yearly%20Temp%20Box.png)

Year 2011 has least fluctuations, data in early 2000's are incomplete data so can't be compared properly. 

### Seasonal Temp

![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Seasonal%20Temp.png)

On average fluctation was noticeable during yr 2001 and 2006. Slightly however, there is constant sloppy decrease in temp from 2004 to 2006, lowest temperatures comparing to other years. 

From year 2010-2016 the temperatures are steady and warmer.

### Weekly Temp

![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Weekly%20Temp.png)

If the weekly timeline is provided on zooming in the max temp week is From Jan 18-25,2015


## Air pressure
### Seasonal Air pressure
![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Seasonal%20Airpressure.png)

Air pressure and temperature  seasonal dist show similar behaviour accoring to plot.

### Air pressure by city custom Timeline

![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Air%20Pressure%20by%20city.png)

City *Maneta* is the only one with air pressure in the upper range around the year, while *Vicosa's* in the middle range and other 3 are in lower range.

## Correlatons

### Whold Data Corr

![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Heatmap%20DF.png)

Above heatmap shows obvious high correlation between similar variables like (temp,tmax and tmin), (stp,smax and smin) and so on. However, it shows higher correaltion btween variables of dew points with humidity. It can implied that more due forms for humidity. The jointplot "Dew and Humidity" also proves the point. Moreover, the aspect of temperature(temp,tmax and tmin) and airpressure (stp,smax and smin) also have high correlation between them.  

It appears aspects wind-speeds have very low correlatoin with humidity. Windspeed and Humidity plot below will make this more clear.  

### Dew and Humidity

![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Humidity%20vs%20Dewpoint.png)

### Humidity and WindSpeed

![img](https://github.com/nibukdk/Weather-Data-Brazil/blob/master/Imgs/Windspped%20vs%20Humidty%20Density%20Plot.png)

The plot is denser on the left and botteom. So, it seems wind-speed and humidity are reversely proportional to each other. Increase in wind-speed causes decrease in humidity. Also the humidity is right skewed data.