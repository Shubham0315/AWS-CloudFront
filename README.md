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
- Create bucket - Provide name (Same as our domain for website) - Block all public access (Only cloudfront to access it and not user) - Enable bucket versioning (to recover object if deleted) - Create bucket

<img width="959" alt="image" src="https://github.com/user-attachments/assets/19147ef6-d517-48d3-a3a8-54fbe2dc2e8e" />
![image](https://github.com/user-attachments/assets/98cc7272-a175-4da9-9f84-9d48f36910e7)
![image](https://github.com/user-attachments/assets/0bfd5cce-992f-4395-87ae-a2830d4835f9)

- Go inside bucket - Properties - Static website hosting - Edit - Enable - Add index and error pages - Save

![image](https://github.com/user-attachments/assets/5b0ff1c4-9b7f-4ae8-94cc-94df5ea9bf04)
![image](https://github.com/user-attachments/assets/2f24d963-35b5-4e2e-960b-5eabe22a8879)

- Now we've created bucket and enabled static website hosting with public access blocked.

- Now uplaod index.html and style.css

![image](https://github.com/user-attachments/assets/4b665a4d-1d64-4f5d-b091-307107dceba1)

- In bucket properties, we can see website URL. If we try to open it, we cannot access as we've disabled public access

<img width="959" alt="image" src="https://github.com/user-attachments/assets/9bcad5fd-8ff7-4046-8d68-7b8f46ee261f" />
![image](https://github.com/user-attachments/assets/df3bf264-1b51-408c-b788-f5366539d1b1)


- Now go to cloudfront - Create distribution - Provide origin domain (S3 and other objects get listed) - Name of origin will be auto generated when we select origin domain - Origin access should be "Legacy Access Identities" - Create new OAI (New identity will be created which will have access to bucket) - Update the bucket policy
- Disable Web App Firewall (WAF)

![image](https://github.com/user-attachments/assets/2eaba5b3-af88-407e-93d5-6072932898c8)
![image](https://github.com/user-attachments/assets/b47ced19-4f81-4ae5-9456-1ad05aa2febf)

  - In settings - Use all edge locations
    - We can define SSL, default root objects (if multiple files/sub directories are there)
    - Then create distribution
    
![image](https://github.com/user-attachments/assets/ef7d437e-1930-4f12-be86-2eff931da4c3)
![image](https://github.com/user-attachments/assets/36dde9cb-bca6-43e5-9974-c429541f8df3)

- We can see distribution got created with domain name

![image](https://github.com/user-attachments/assets/1dc5e03d-3375-4b28-afcb-04e6fea07cb5)

  - The URL in distribution domain name will point to S3 bucket. It is in deploying stage
  - We can check S3 bucket to check bucket policies. It shows ID for OAI created with CloudFront origin access identity with s3 bucket as resource.

![image](https://github.com/user-attachments/assets/cc8835e8-6726-45aa-b12c-000bef0ada66)



- When we use cloudfront when many users are trying to access our app, CDN will actually reduce the cost. So use S3 buckets with CloudFront.

- So if we try to access app from S3 bucket URL, access will be forbidden. But if we access from CDN cloudfront URL, we can access app with no latency.

![image](https://github.com/user-attachments/assets/9438e5b3-107d-4ee0-84f3-33819262d34a)


