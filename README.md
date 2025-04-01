# AWS-CloudFront
AWS CloudFront GitHub repository provides tools, samples, and configurations for deploying and managing Amazon CloudFront distributions efficiently.

- CloudFront is a managed AWS service offering solution for CDN - Content Delivery Network.
- We interact with CDN daily when we access apps like youtube, instagram, snapchat, amazon, flipkart or any other image or video sharing platform.

- Suppose for instagram, if anyone tries to upload image or video from anywhere in the world, it gets uplaoded. Instagram having Central storage system, image uploaded is copied here in central storage system. So anybody in the world can access the content from this central storage system.
  - If the central storage system in anywhere in the US and without CDN, the person in India to access the image, his request has to go through multiple routers and reach instagram servers. Simmilar process to get response back to person.
  - For anything we access on internet, request goes through multiple routers. Depending on no of routers, our latency keeps increasing to access the image.
  - So CSS being in US, US people wont find any latency. But rest of the world people will find latency.
  - Thats why people use CDN
  - Using CDN, initially while uploading image it goes to CSS. There will be a CDN and anyone trying to access image, we'll map CDN to instagram servers DNS. Using CDN, we'll make people access the CDN instead of servers. So anyone trying to access image, they will talk to CDN which will create local copies of image.
  - Instead of image getting stored at central location, it will get stored at edge location (all zones of AWS).
 
- CDN solves the problem by keeping multiple local copies.
