
# Introduction

## Concerns

Concerns about confidentiality in statistical products has increased in the past several years. While the new disclosure avoidance techniques in the Decennial Census garnered much attention (citations), the academic community also expressed concerns about plans to apply formal disclosure avoidance techniques to public-use microdata files (PUMFs), and after an initial announcement, the Census Bureau delayed implementation of such methods for the American Community Survey.[^acs]

[^acs]: See [Disclosure Avoidance Protections for the American Community Survey](https://www.census.gov/newsroom/blogs/random-samplings/2022/12/disclosure-avoidance-protections-acs.html)

## Validation and Verification

On the other hand, long-running pilot projects with (non-formal) synthetic microdata products (SynLBD, SIPP Synthetic Beta) came to an end in 2022.[^endsds]. These pilot projects made use of a publicly accessible analysis server housing synthetic data, authorized for release in this environment by the Census Bureau and the IRS, combined with a mechanism to re-run the analysis using confidential data, housed in the confidential computing environments of the U.S. Census Bureau. Requests to validate the results obtained from prepared code were sent via email to designated Census Bureau staff, who then ran the code (often times debugging it), and handled disclosure avoidance analysis at the Census Bureau on behalf of the researchers. The modeling and analysis code provided by the researchers served to improve subsequent versions of the synthetic data. The code was often not fully reproducible, and anecdotally, the process was time-consuming Census Bureau staff.

[^endsds]: See [End of life for the Cornell Synthetic Data Server September 30, 2022](https://web.archive.org/web/20230602202220/https://web.archive.org/web/20221130032540/https://www2.vrdc.cornell.edu/news/).

## Scaling up

These pilot projects were not set up to scale, and yet they demonstrated that there is a need for such a process. In general, based on conversation of the author with various researchers at conferences and by email, researchers were happy with the ability to access such data without having to request a full-blown project in an FSRDC, but were somewhat frustrated by the process. Statistical agencies and research institutes have explored various ways to scale up access to confidential data. Statistics Canada had RTRA process, Norway has the Microdata.no system, and Barrientos et al (2018) proposed a differentially private validation server. 

## Limitations

Many such processes have limitations that limit their utility for researchers. The aforementioned Statistics Canada and microdata.no systems strongly limit the type of analysis that is feasible by restricting the software keywords that can be used (RTRA), by creating a structured new statistical language (microdata.no), or by limiting the types of analysis that can be run and validated (Barrientos et al).

## Reproducibility

The issue is compounded by well-documented problems with the reproducibility of code in the social sciences. Heuristically, many of the problems with the SDS arose because the code failed to reproduce when run in a very similar environment (the SDS was specifically designed to mimic the environment of the FSRDCs). Researchers in the social sciences appear to rely heavily on interactive computing, failing basic reproducibility tests. In a sample of over 8,000 replication packages associated with high-profile economics articles, only 30% had some sort of master script. In part to cater to this need, remote-access or local secure access in the form of physical or virtual secure data enclaves is stil the dominant - but expensive - way to access confidential data. The dominant method of access thus forces researchers to choose between lower quality data in an environment that corresponds to their preferred computing method, and higher quality confidential data in environments that are expensive for researchers, data providers, or both.

## Possible solution

We demonstrate a simple scenario of using containers, which can be hosted on a cloud platform, but also run individually on researcher compute platforms, to facilitate synthetic and confidential data processing. The purpose of using containers is to provide users with access to synthetic data and coding resources such that their analysis is easily reproducible. Containers can easily be validated for reproducibility before they are then forwarded to the confidential computing environment. Once determined to be reproducible, extending the analysis to use confidential data, and enables a wide spectrum of plug-in disclosure avoidance measures as well. Crucially, all validation of reproducibility can be performed prior to validation using the confidential data, on open, possibly commercial platforms. Only once reproducibility is confirmed is the same analysis model ported to the confidential data. 

## Containers in the wild

The use of cloud providers removes the need for users of the synthetic to install anything locally. The use of containers enforces reproducibility out-of-box when using synthetic data, as well as streamlines validation against the confidential data (which is in essence a replication of the analysis on the synthetic data). Furthermore, it enables scalability. CodeOcean is a commercial service facilitating that process by making the resources available through a web browser, though the basic functionality can be achieved on any container system. Options include [Wholetale](https://wholetale.org),  and others.[^gigantum] Finally, users who wish to not use such services can also typically provide their own setup for the synthetic data component, at very little additional cost or effort. Many university computing system provide some support on their high-performance computing clusters. For data providers, the tools used (containers) are widely used by numerous cloud providers, are transparent in how they are built, and allow for in-depth security scanning while retaining much of the flexibility that researchers and IT providers seek.

[^gigantum]: An earlier version of this presentation mentioned  [Gigantum](https://gigantum.com). As is not unusual in this space, Gigantum no longer functions as a company.

## What's new

The use of containers in this way is novel as a systematic way to provide scalable, potentially high-throughput validation, and differs in usage from previous methods, such as the Cornell Synthetic Data Server. In the same 8,000 replication packages mentioned earlier, only 0.13% had used containers. However, it has been used in a small number of well-published instances in the economics literature for precisely this kind of purpose, and uses methods that are very widespread in the computer science and statistics community (Boettiger, 2015). We believe that it is promising as a modern way of implementing validation when data are confidential.