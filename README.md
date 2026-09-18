# S3 Bucket Misconfiguration Demo

## Overview
This project demonstrates a common real-world cloud security 
misconfiguration: a publicly accessible S3 bucket. I intentionally 
created the vulnerability, verified it, then remediated it — 
mirroring how this issue is often found and fixed in production 
environments.

## Steps

### 1. Created an S3 bucket and uploaded a test object
Created a general-purpose S3 bucket and uploaded a sample file.

### 2. Made the bucket public (intentional misconfiguration)
Disabled "Block all public access" and attached a bucket policy 
granting `s3:GetObject` to `*` (everyone).

### 3. Verified public access
Accessed the object's direct URL with no authentication — the file 
loaded successfully, confirming the bucket was exposed.

**Before (public access working):**


![before](before.png)



### 4. Remediated the issue
- Removed the public bucket policy
- Re-enabled "Block all public access"

### 5. Verified the fix
Accessed the same URL again — received `AccessDenied`.

**After (access denied):**


![after](after.png)



## Why this matters
Misconfigured S3 buckets are one of the most common causes of real 
cloud data breaches, exposing everything from PII to credentials to 
source code. This exercise reflects the kind of misconfiguration 
detection and remediation a cloud security engineer performs 
regularly.

## Tools used
AWS S3, AWS Management Console# s3-misconfiguration-demo
