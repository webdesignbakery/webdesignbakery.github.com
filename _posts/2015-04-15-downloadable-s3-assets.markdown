---
layout: post
title:  "Downloadable S3 Assets"
date:   2015-04-15 14:51:00
categories: s3
comments: true
---

Today I needed to make an ebook (PDF) downloadable from a landing page and I didn't want to have my web server do any special serving of assets. The problem with serving assets from S3 is that the browser will try to render pdfs and images. After some research and experimentation I found a way to have S3 serve the asset without the browser rendering it.

After you've uploaded your asset to S3 you need to add the following Key/Value metadata to your asset:

    Key: Content-Disposition
    Value: attachment; filename=

That's it. Some people suggest that you only need to add the `attachment` value, but that didn't work for me---YMMV. You can also include the filename of the asset, but I found it wasn't needed and saved me some typing.

You can see the S3 downloadable asset in action here: [Top 10 Tactics for Increasing Employee Referrals][top-ten].

[top-ten]: https://employeereferrals.com/top-ten-tactics
[s3-rest]: http://docs.aws.amazon.com/AmazonS3/latest/dev/RESTAuthentication.html
