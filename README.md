# Spark K-Means

K-Means algorithm implementation using Spark. This algorithm does not perform
any calculation of the initial centroids, these must be given.

## Usage

*points centroids output max delta partitions*

```
spark-submit \
  --class "com.jgalilee.spark.kmeans.JobDriver" \
  --master local[4] \
  ./target/scala-2.10/spark-k-means_2.10-1.0.jar \
  input/points.txt \
  input/centroids.txt \
  output \
  10 \
  0.0 \
  3
```

* points - Path to the input points data.
* centroids - Path to the input centroid data.
* output - Path to write the output for iteration n - i.e. output/n
* max - Maximum number of iterations.
* delta - Delta definining the maximum difference between the last and current centroids.
* partitions - Number of partitions to use when calculating the new set of centroids.

## Assumptions

Input data is assumed to be string representations in double format. Each point
is assumed to be in the same dimensional space, as with each centroid. If two
points are not in the same dimensional space an exception is thrown.

Points should be in the form.

1.0 \s 2.0 \s ...

Centroids should be in the form.

1 \t 1.0 \s 2.0 \s ...

Where \t is a tab, and \s is a space. The number of duplicate items or order is
not important. This will be resolved during the map phase.

## Dependencies

* Spark 1.0.1
* Scala 2.10.4

## Licence

```
The MIT License (MIT)

Copyright (c) 2014 Jack Galilee

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
