---
pcx_content_type: reference
title: How we do it
weight: 1
meta:
    title: Automation | How we do it
---

# How we do it

Cloudflare uses the following automations to streamline our documentation process. 

## Content maintenance

At Cloudflare, we use several automations to reduce the cost associated with content maintenance.

| Automation | Purpose | Implementation | Runs when |
| --- | --- | --- | --- |
| [Internal link checking](https://github.com/cloudflare/cloudflare-docs/blob/production/bin/crawl.ts) | Evaluates all internal links to make sure they are in the current build. Increases cross linking while reducing maintenance cost. | GitHub Actions | Every commit |
| External link checking | Evaluates external links for broken links or links that redirect to another location. | SEO crawler | Weekly |
| [Header link checking](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/anchor-link-audit.yml) | Evaluates anchor links within our docs to make sure they resolve correctly. | GitHub Actions | Every weekend |
| [API docs link checking](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/api-links-crawl.yml) | Evaluates links to our API docs. | GitHub Actions | Every weekend |
| [Unused images check](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/image-audit.yml) | Flags images that are in our resources, but not currently referenced in our documentation. | GitHub Actions | Every month |

## Reporting

| Automation | Purpose | Implementation | Runs when |
| --- | --- | --- | --- |
| [Label PRs](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/label-pr.yml) | Adds and updates labels related to the content subfolder and size of a pull request. Useful for rollup reporting and team self-assignment. | GitHub Actions | Every commit |

## Contributor resources

The following resources help contributors and stakeholders when they are making changes to our documentation.

| Automation | Purpose | Implementation | Runs when |
| --- | --- | --- | --- |
| [Build check](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/ci.yml) | Verifies that our docs site builds correctly. | GitHub Actions | Every commit |
| [Show before/after links](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/show-changed-files.yml) | Provides a comparison table that shows the current page in production and the changed page in a preview build. | GitHub Actions | Every Pages build |
| [Flag needed redirects](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/comment-changed-filenames.yml) | Comments with a list of changed or deleted files that might need a redirect. | GitHub Actions | Every commit |
| [Infinite redirect check](https://github.com/cloudflare/cloudflare-docs/blob/production/bin/find-infinite-redirects.ts) | Verifies whether the commit adds conflicting redirects.  | GitHub Actions | Every commit |
| [Spell check](https://github.com/cloudflare/cloudflare-docs/blob/production/.github/workflows/spell-check.yml) | Flags issues with spelling, casing, or insensitive language. | GitHub Actions | Every commit |