# ROSE notes

ROSE is a tool which can be used to identify super enhances from Chip Seq data. 

The workflow of the tool can be summarized as :-

- Create stitched enhancers bu joining those which are within a specified stitching distance
- Get sum of coverages for all positions from treatment and control bam files for these regions.
- Get a score by subtracting signal for control from the treatment.
- This score is then used to find a point where there is a dramatic increase in the score. This point is tangent to the plot of sorted scores vs rank.
  ![SE Calling Illustration](https://res.mdpi.com/genes/genes-06-01183/article_deploy/html/images/genes-06-01183-g001.png)
  [Source](http://www.mdpi.com/2073-4425/6/4/1183/htm)
- Once this point is obtained then all merged peaks which had a higher (treatment) - signal coverage are taken as super enhancers.
- The tool gives output in terms of bed files which can be visualised in UCSC/IGV, tables which can be viewed with excel, a hockey plot similar to the one in illustration above.
- The obtained enhancers/super enhancers can be annotate using the ROSE_geneMapper.py script in the tool.
