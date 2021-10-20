

# Caching for Throughput Cash
* Exercise Assumptions
  * Latency issues are caused either by the network or the downstream Calendar services(Google, Microsoft, Apple, etc). i.e. the recommendation will not be focusing on performance issues caused internally by algorithms on the applications servers themselve
  * The data is a combination of dynamic and static data with various levels of non-functional performance requirements; e.g data can be:
    * Somewhat stale(e.g. Zillow property likes)
    * Updated immediated. (e.g. Meeting acceptance)

  * Architecturally, there are multiple instances of the same service, integrating with these APIs, that is fronted by a load balancer. Within the systems, the application is architected in a way that all interaction with the downstream systems flows through a particular module.
  

* Recommended approaches
    * Static data
        * Use a private cache. If initially populating the cache is really slow

* Also, you should take into considerations when the data will be populated. Do you want to wait until the data is initially requested 
* If the same piece of data could be written simultaneously across multiple instances of the server then the source of truth should have concurrency controls and the cache should make sure the data is persisted before saving it to the cache. 
* Need to make sure the data and cache stay in sync. How should failures be handled?
* Caching policies
    * Write through
    * Write back
    * Write around
* Cache eviction policies
    * Least Recently Used
    * Least Frequently Used
* Must take into consideration usage patterns.
    * Frequent read, frequent write
    * Infrequent read, frequent write
    * Frequent read, infrequent write
    * Infrequent read and write
* Whatever approach is chosen still should have performance monitoring and cache metric monitoring in place to verify the choices.

~[Cache Diagram](cache.jpg)


