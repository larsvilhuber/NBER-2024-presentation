# Possible solution

## Containerized validation

We demonstrate a simple scenario of using containers, which can be hosted on a cloud platform, but also run individually on researcher compute platforms, to facilitate synthetic and confidential data processing. The purpose of using containers is to provide users with access to synthetic data and coding resources such that their analysis is easily reproducible. Containers can easily be validated for reproducibility before they are then forwarded to the confidential computing environment. Once determined to be reproducible, extending the analysis to use confidential data, and enables a wide spectrum of plug-in disclosure avoidance measures as well. Crucially, all validation of reproducibility can be performed prior to validation using the confidential data, on open, possibly commercial platforms. Only once reproducibility is confirmed is the same analysis model ported to the confidential data. 

- similar in spirit: IAB JoSuA system 

## Containers in the wild

The use of cloud providers removes the need for users of the synthetic to install anything locally. The use of containers enforces reproducibility out-of-box when using synthetic data, as well as streamlines validation against the confidential data (which is in essence a replication of the analysis on the synthetic data). Furthermore, it enables scalability. CodeOcean is a commercial service facilitating that process by making the resources available through a web browser, though the basic functionality can be achieved on any container system. Options include [Wholetale](https://wholetale.org),  and others.[^gigantum] Finally, users who wish to not use such services can also typically provide their own setup for the synthetic data component, at very little additional cost or effort. Many university computing system provide some support on their high-performance computing clusters. For data providers, the tools used (containers) are widely used by numerous cloud providers, are transparent in how they are built, and allow for in-depth security scanning while retaining much of the flexibility that researchers and IT providers seek.

[^gigantum]: An earlier version of this presentation mentioned  [Gigantum](https://gigantum.com). As is not unusual in this space, Gigantum no longer functions as a company.

## Containers in Social Sciences


In a sample of over **8,000 replication packages** associated with high-profile economics articles, **only 1% had a `Dockerfile`** (the key build script for containers). 

## What's new

The use of containers in this way is novel as a systematic way to provide scalable, potentially high-throughput validation, and differs in usage from previous methods, such as the Cornell Synthetic Data Server. In the same 8,000 replication packages mentioned earlier, only 0.13% had used containers. However, it has been used in a small number of well-published instances in the economics literature for precisely this kind of purpose, and uses methods that are very widespread in the computer science and statistics community (Boettiger, 2015). We believe that it is promising as a modern way of implementing validation when data are confidential.