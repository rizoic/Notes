# BWTool Notes

bwtool is a command line wiki for working with bigWig files. You can do a lot of data extraction, analysis and data modification operations on .bw files using bwtool. [More Info](https://github.com/CRG-Barcelona/bwtool/wiki)

### Summary

Provides summary stats like mean, median, max, min of bw coverage/signal in for each given interval.
So if an interval of 4 positions has coverage values of 1,2,3,4 it will calculate the mean of mean(1,2,3,4) and give values for that interval. Similary it will do the same for other operations.
You can optionally add the sum, quantiles,sum of squared deviations from mean(to see variablity of coverage in a region). 
You can also ask bwtool to consider or ignore positions with zero coverage in calculations with the argument fill=0/1. [Source](https://github.com/CRG-Barcelona/bwtool/wiki/summary)
