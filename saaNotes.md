# AWS Solution Architect Associate study notes

## [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)
- Regions
    - Are around the world
    - They have names (us-east-1, eu-west-3)
    - Regions are a cluster of data centers
    - Most services are region scoped
    - How to choose a region for a service?
        - Compliance
        - Proximity
        - Pricing
        - Available services [click to view services per region](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/?p=ngi&loc=4)
- Availability Zones (AZ)
    - Multiple AZs compose a region (Min 2 / Max 6 || usually 3), example Sydney region has:
        - ap-southeast-2a
        - ap-southeast-2b
        - ap-southeast-2c
    - Each AZ has one or more data centers with own power, networking and connectivity
    - Each data center is isolated form each other to isolate disasters
    - Each AZ are connected with ultra low latency and high bandwidth networking
- Data Centers
- Points of presence (Edge locations)
    - Deviler content to end users with lower latency

## IAM and AWS CLI