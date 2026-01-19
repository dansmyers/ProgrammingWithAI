# Benford's Law

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Rozklad_benforda.svg/1920px-Rozklad_benforda.svg.png" width="40%" />

## Overview

Benford's Law is one of the all-time great "I can't believe this is a thing" results. It states that, in many real-world quantitative data sets, **1 is by  far the most common leading digit**. Specifically, slightly more than 30% of the numbers in the data set should start with a leading 1.  About 17% of data values should start with 2, and about 13% start with 3. Leading 9's occur less than 5% of the time.

This is surprising, because you might expect the distribution of leading digits to be uniform, with about 11% of entries starting with 1, another 11% with 2, and so forth.

The law is named after physicist Frank Benford, who called it *The Law of Anomalous Numbers* in a 1938 paper. Benford's Law has applications to fraud detection and accounting, because it can be used to identify fake data that has an unnatural distribution.

You're going to write a program to validate Benford's Law against a real-world data set: the county-level population estimates produced by the U.S. Census Bureau.
