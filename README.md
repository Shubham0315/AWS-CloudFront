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

----------------------------------------------------------------------------------------------------------------

How to host static website on S3 bucket?
-
- We can uplaod audio, video, binary objects and use it into our website.
- But if user has direct access to S3 bucket for using the content, it will be security prone. Other challenge will be latency if everyone is trying to access bucket. Everytime we upload, there will be cost associated
- So major challenges are
  - Security
  - Latency
  - Cost
- To overcome all we've CDN which helps us cache the content in the nearest edge locations. CDN service for AWS is CloudFront.
- Edge locations can be locations from where user is trying to access the data.
- So if users trying to access data of s3, content will be cached to edge locations. So if another user dont have need to access S3, he can directly go to edge locations and access it as it is cached.
- This helps enhance security as users are not accessing S3 directly. Also we dont have to pay for upload/download as content is cached. Also latency issue is resolved.
- So for user, it wont matter where website is hosted. They will be accessing from nearest locations. Thus data transfer cost will be less.


Practical Demo
-
- 
