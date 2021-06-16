---
layout: post
title: "Sprint Notes 2: From Discovery to Build (w/c 26th April - w/c 14th June)"
---

Blazing through early discovery on content modelling and architecture, we approached the end of discovery focusing on… content modelling and architecture, in more detail. As well as infrastructure, and overall project planning.

## Architecture update

Even with a monolithic architecture, there still are plenty of integration requirements to look into, such as accessing Tate’s collections data. We decided to go with a Django-friendly approach here, with collections data replicated directly within the application. This makes a lot of sense since the Tate API and website are combined as a single application, which would be the only place needing direct integration with collections databases. It will also make editors’ lives much simpler in the CMS, as they will be able to reference collections data with all of the idioms that are native to Wagtail.

Even though the integration itself is complicated (there’s no avoiding that), for developers it’ll also be much easier to combine collections data with CMS data. It’s as simple as using [Django QuerySets](https://docs.djangoproject.com/en/3.2/ref/models/querysets/)! See for yourself – querying all of Tate’s artwork accession numbers, in a Django-friendly one-liner:

```python
accession_numbers = ArtworkPage.objects.all().values_list("acno", flat=True)
```

## Infrastructure

The move from IaaS (Infrastructure-as-a-Service) to (PaaS) Platform-as-a-Service meant having to get more up to speed with Azure’s offering in this respect, as well as revisiting other parts of the stack – currently tate.org.uk uses a dedicated appliance for a Web Application Firewall, and has two layers of response caching, with Varnish and Memcached. We will want to simplify this by reducing the number of moving parts, and generally offloading the complexity to providers with more complete offerings (essentially [Cloudflare](https://www.cloudflare.com/) vs. [Azure Front Door](https://azure.microsoft.com/en-gb/services/frontdoor/)).

## Content modelling

This has been an ongoing area of focus for us – even though we could take an almost green-field approach to architecture, for content, there is no getting around the fact we do need to move across thousands of pages. This could be a blog post in its own right, but instead we will share some numbers. Coming from Drupal:

- 50 content types 😨
- 20 of those correspond to page types we will retain in Wagtail, with 6 non-page content types also relevant
- 5 more moving manually
- About 1300 fields in total, across the page types, as well as paragraph bundles

In Wagtail:

- 28 page types as equivalent to the ones in Drupal
- We’ll only expect about 400 different fields across page types, StreamField blocks, snippets, and custom models.

The number of fields going from well above 1000 down to 400 is a great representation of the effort we went through to review what content might be coming across, and simplify wherever possible. Re-platform projects like this are a great opportunity to prune old branches off a site, and we’re able to do so quite extensively. This is in large part helped with the project team at Tate, who liaise with internal stakeholders and organise regular reviews with editors to make sure we are on the right track.

## KPIs

We had pretty great KPI (Key Performance Indicator) definition sessions, retaining a good mixture of metrics that are paramount but need careful thinking to become measurable, and simple ones that can be assessed regularly at a glance. A few highlights form our early picks, to be confirmed:

- Editor happiness (the greatest gift that I possess) 😌
- CMS – Steps involved for page previews
- CMS – Time to create a page with complex content
- CMS – Accessibility checks directly in CMS
- DevOps – Reduce number of application codebases needed for production site
- Infrastructure – Running costs

There was also clear interest in a KPI on reducing the carbon intensity of the website, which is very exciting to us.

## What next

Did we mention we are now full-on building the site? Yes, yes we are! After a tricky merger of all of the existing projects into one, and following through a code freeze, we are now full speed ahead on building the site in Wagtail, hosted in Azure PaaS.
