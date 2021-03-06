Rhipe ARIMA
============================

This implementation of the ARIMA (AutoRegressive Integrated Moving Average) algorithm is based on R, Hadoop, and the RHIPE (Hree-pay) framework.

Rhipe webpage: <a href="http://www.datadr.org/getpack.html">Rhipe</a>


Analytic Requirements
---------------------
*  R packages forecast and chron

```
> installed.packages()
# make sure all packages are >= 3.0.0 
# if not run the below update and check again
> update.packages(checkBuilt = F, ask = F)

# for some reason codetools did not update the first
# time but did the second
> update.packages(checkBuilt = T, ask = F)

# install additional packages
> install.packages(c("forecast", "chron"))
```

Input
-----

The Rhipe ARIMA analytic assumes the data will be in the following format:

> IDENTIFIER\tTIMESTAMP(YYYY-MM-DD HH:mm:SS)


Output
------
It will also output the data in the following format:

> IDENTIFIER\tTIMESTAMP(YYYY-MM-DD HH:mm:SS)\tSTANDARDIZED_RESIDUALS(a floating point number)

Example
-------
</br>

A base example is provided, working on the Flight Data that can be found [here](http://stat-computing.org/dataexpo/2009/the-data.html) - [http://stat-computing.org/dataexpo/2009/the-data.html](http://stat-computing.org/dataexpo/2009/the-data.html).  

> Rscript rhipe_arima.R /tmp/airport_deps_sample /analytics/arima/airport days 4

The first argument after rhipe_arima.R is the input file.  
The second is the output directory.  
The third is how to aggregate the data.  Possible values for this third argument are __days,hours,minutes,secs__<br/>
The fourth is the threshold, in standard deviations, a residual must be above to be emitted

<img height="400" src="https://raw.github.com/wiki/Sotera/rhipe-arima/images/sample.png" />

This image shows a sample of how you could visualize the results of
this example.  It shows number of departures per day for each airport
and using the results of the analytic plots marks the days when the
standardized residual is greater than 4.


Other Information
-----------------

Please make sure you can read and write from the __/tmp__ directory as well as any other directory you specify. 
