## 🌐 Amazon CloudFront – Distribution Creation (Step-by-Step):

## 🎯 Objective:

Create an Amazon CloudFront distribution to deliver content (such as a web server) globally with low latency and high performance through caching at AWS edge locations.

## ✅ Prerequisites:

Before you begin, ensure the following:

✅ An S3 bucket or origin server (e.g., EC2, ALB, on-prem server, or any HTTP server) is already set up.

✅ The content (e.g., HTML files, images, videos) is uploaded to the origin.

✅ (Optional) A custom domain name is configured (via Route 53 or another DNS provider) if you want to use a branded CDN URL like cdn.example.com.

🛠️ Step-by-Step: Create a CloudFront Distribution
1️⃣ Open the CloudFront Console
🔗 URL: https://console.aws.amazon.com/cloudfront/

2️⃣ Click "Create Distribution"
Choose the Web distribution (HTTP/S delivery).
⚠️ RTMP is deprecated and should be avoided.

## 3️⃣ Configure Origin Settings
Setting	Description
Origin Domain Name	Choose your S3 bucket or enter the custom origin domain (e.g., example.com).
Origin Path	(Optional) Provide a subdirectory if you want to serve content from a specific folder.
Origin ID	Auto-filled or give a custom name for identification.
Restrict Bucket Access	Select Yes (recommended for private content).
Origin Access Control (OAC)	Create a new OAC or select an existing one to allow CloudFront access to your S3 bucket.

## 4️⃣ Configure Default Cache Behavior
Setting	Value
Viewer Protocol Policy	Redirect HTTP to HTTPS
Allowed HTTP Methods	GET, HEAD (add OPTIONS, PUT, POST if needed)
Cache and Origin Request Settings	Use recommended settings or customize headers/cookies if needed
Object Caching	Use origin cache headers or define TTL values
Minimum TTL	Example: 0 (for no caching)
Maximum TTL	Example: 31536000 (1 year)
Compress Objects Automatically	Yes (Gzip/Brotli enabled)
Lambda@Edge / Function associations	(Optional) Use for custom request/response logic

## 5️⃣ Configure Distribution Settings
Setting	Value
Price Class	Choose based on your region needs (e.g., "Use only North America and Europe" or "All Edge Locations")
Alternate Domain Names (CNAMEs)	(Optional) Use a custom domain like cdn.example.com
Custom SSL Certificate	Use an ACM certificate if you're using a custom domain
Default Root Object	e.g., index.html
Logging	Enable logging to an S3 bucket if needed
WAF Web ACL	Attach a Web ACL if you're using AWS WAF
IPv6	Enable (recommended)

## 6️⃣ Review and Create:

Click "Create Distribution".

Wait a few minutes for deployment.

Once completed, you'll receive a CloudFront URL such as:

```
https://dj2hji00vrmto.cloudfront.net/
```
You can now use this domain to serve your static/dynamic content globally.

## IMAGES:
