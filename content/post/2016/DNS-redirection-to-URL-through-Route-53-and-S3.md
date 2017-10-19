---
title: DNS redirection to URL through Route 53 and S3
author: Sahil Ahuja
categories: [blog]
date: 2016-12-17 03:33:51
tags: [aws, s3]
---
I recently needed to redirect a DNS (like links.sportscafe.in) to a path (like http://trello.com/abc). Here is what finally helped me: http://stackoverflow.com/a/14289082/1233476
<!--more-->

The TTCBER (Thing That Cannot Be Easily Replicated) was the following redirection rule in S3:
```xml
<RoutingRules>
  <RoutingRule>
    <Redirect>
      <Protocol>https</Protocol>
      <HostName>myaccount.signin.aws.amazon.com</HostName>
      <ReplaceKeyPrefixWith>console/</ReplaceKeyPrefixWith>
      <HttpRedirectCode>301</HttpRedirectCode>
    </Redirect>
  </RoutingRule>
</RoutingRules>
```

Other TTCBERs:
---
To allow public access to S3 resources from any webpage (which you may would want in case hosting public assets for a website), we need to add the following bucket policy to the bucket:
```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "AddPerm",
			"Effect": "Allow",
			"Principal": "*",
			"Action": "s3:GetObject",
			"Resource": "arn:aws:s3:::cdn-static.mybucket.name/*"
		}
	]
}
```

To allow these resources to be embedded in all websites, add CORS configuration to the S3 bucket:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<CORSConfiguration xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
    <CORSRule>
        <AllowedOrigin>*</AllowedOrigin>
        <AllowedMethod>GET</AllowedMethod>
        <MaxAgeSeconds>3000</MaxAgeSeconds>
        <AllowedHeader>Authorization</AllowedHeader>
    </CORSRule>
</CORSConfiguration>

```
