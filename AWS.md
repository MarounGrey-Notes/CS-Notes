# AWS
## How to choose an AWS Region?
* **Compliance** with data governance and legal requirements: data never leaves a region without your explicit permission
*  **Proximity** to customers: reduced latency
*  **Available services** within a Region: new services and new features aren't available in every Region
*  **Pricing** pricing varies region to region and is transparent in the service pricing page

## AWS Availability Zones
* Each region has many availability zones (usually 3, min is 3. max is 6). Example:
   * ap-southeast-2a
   * ap-southeast-2b
   * ap-southeast-2c

* Each availability zone (AZ) is one or more discrete data centers with redundant power; discrete data centers with redundant power, networking, and connectivity.
* They're separate from each other, so that they're isolated from disasters.
* They're connected with high bandwidth, ultra-low latency networking.

## AWS Points of Presence (Edge Locations)
* Amazon has 400+ Points of Presence (400+ Edge Locations & 10+ Regional Caches) in 90+ cities across 40+ countries
* Content is delivered to end users with lower latency
