---
pcx_content_type: how-to
title: Zone-level
weight: 1
meta:
    title: Zone-level authenticated origin pulls
---

# Zone-level authenticated origin pulls

When you enable Authenticated Origin Pulls for a zone, all proxied traffic to your zone is authenticated at the origin web server.

## Before you begin

Make sure your zone is using an [SSL/TLS encryption mode](/ssl/origin-configuration/ssl-modes/) of **Full** or higher.

## 1. Upload certificate to origin

First, upload a certificate to your origin.

To use a Cloudflare certificate (which uses a specific CA), [download the .PEM file](/ssl/static/authenticated_origin_pull_ca.pem) and upload it to your origin. This certificate is **not** the same as the Cloudflare Origin CA certificate and will not appear on your Dashboard.

To use a custom certificate, follow the API instructions to [upload a custom certificate to Cloudflare](/ssl/edge-certificates/custom-certificates/uploading/#upload-a-custom-certificate), but use the [`origin_tls_client_auth` endpoint](/api/operations/zone-level-authenticated-origin-pulls-upload-certificate). Then, upload the certificate to your origin.

{{<Aside type="warning">}}

Although Cloudflare provides you a certificate to easily configure zone-level authenticated origin pulls, this certificate is not exclusive to your account and only guarantees that a request is coming from the Cloudflare network. If you want more strict security, you should upload your own certificate.

Using a custom certificate is required if you need your domain to be [FIPS](https://en.wikipedia.org/wiki/Federal_Information_Processing_Standards) compliant.

{{</Aside>}}

## 2. Configure origin to accept client certificates

{{<render file="_aop-configure-origin.md">}}

## 3. Configure Cloudflare to use client certificate

{{<render file="_aop-enable-feature.md">}}

##  4. Enable Authenticated Origin Pulls for all hostnames in a zone

Use the Cloudflare API to send a [`PUT`](/api/operations/zone-level-authenticated-origin-pulls-set-enablement-for-zone) request to enable zone-level authenticated origin pulls.

If you had set up logging on your origin during [step 2](#2-configure-origin-to-accept-client-certificates), test and confirm that Authenticated Origin Pulls is working.

##  5. Enforce validation check on your origin

{{<render file="_aop-enforce-validation.md">}}