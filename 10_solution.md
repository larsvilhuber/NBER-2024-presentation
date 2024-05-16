# Possible solution

## Containerized validation

- **Containers**, 
  - hosted on public cloud platform or run  on researcher laptop 
  - provide access to synthetic or "plausible" data, and coding resources
  - mechanism to ensure authors can validate reproducibility of analysis

. . . 

- Then submitted to the **confidential computing environment**. 
  - analysis modified to use confidential data
  - enables a wide spectrum of plug-in disclosure avoidance measures as well

. . . 

- similar in spirit: IAB JoSuA system, but without hosting costs 

## Containers in the wild

 One of the first mentions of containers for scientific research was @boettiger_introduction_2015.

- [CodeOcean](https://codeocean.com) is a commercial service facilitating that process by making the resources available through a web browser
- [Wholetale](https://wholetale.org) and [MyBinder](https://mybinder.org) are other (academically oriented) services that provide similar functionality[^gigantum] 
- Many universities HPC clusters provide some support (`Apptainer` more popular than `Docker`)

[^gigantum]: An earlier version of this presentation mentioned  [Gigantum](https://gigantum.com). As is not unusual in this space, Gigantum no longer functions as a company.

## Containers in Social Sciences are still a challenge!


In a sample of over **8,000 replication packages** associated with high-profile economics articles, **only 11 had a `Dockerfile`** (the key build script for containers). 

(That's n=11, not 11% - in fact, it's **0.13%** of replication packages.)

## What's new

The use of containers in this way is novel as a systematic way to provide **scalable, potentially high-throughput validation**, and differs in usage from previous methods, such as the Cornell Synthetic Data Server. 

> I believe that it is promising as a modern way of implementing validation when data are confidential.