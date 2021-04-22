---
layout: post
title: Sprint Notes 1: Inception & Discovery (the first 6 weeks - w/c 1 March to w/c 19th April)
---

In early March 2021 we kicked off a really exciting project to replace the content management system (CMS) that powers the Tate Galleries signature website, [www.tate.org.uk](https://www.tate.org.uk/). The existing site has been running on the Drupal 7 platform since 2012 so it has had a good innings, but the technology is approaching end-of-life. Moreover the limitations present within the existing CMS add a significant amount of friction to the workflow used by Tate's content editors.

Over the coming months our task is to design and implement a new CMS for Tate in Wagtail, optimise and migrate some 10,000 pages of content, help simplify Tate’s technical architecture, improve editor workflows, and decommission the Drupal site.

The project team comprises Tate’s Digital and Content teams; a product team from Torchbox included two members of the Wagtail core team (who lead on the development of the open source CMS); and technical architects from Softwire who led the selection process for Tate, and will be working on hosting infrastructure.

Now that we’re settled in we’ll publish regular sprint notes on the project, but here’s an update on where things have got to so far - we’ve come a long way in the first 6 weeks!

- The core teams were introduced and we defined ways of working. As we headed into the Discovery phase, we agreed on rapid 1-week sprints initially, to keep momentum up and allow us to collaborate quickly and get up to speed on how the existing site is set up.
- From early inception, the tech teams hosted knowledge share sessions to allowed us to peek under the bonnet and understand the existing architecture of the site. Through an immersive exploration of the infrastructure set up we began to think out of the box:
  - the as-is architecture uses Drupal as a headless CMS, feeding content to a frontend built in Django, with an Elasticsearch instance in-between to help reduce direct demand on Drupal. For this reason Tate had planned the project based around a swap-in replacement of Drupal with Wagtail to keep the process simple and minimise disruption.
  - Tate were also clear that they had an ambition to simplify their architecture and we were struck that it was quite complex with many moving parts, and so developed a hypothesis that a more radical approach to the project could lead to a better outcome.
  - We put forward a number of different possible future state architectures, which included an option to consolidate various moving parts into a single 'monolithic' Wagtail instance - which would serve as CMS, front-end, and a content-API to support additional services.
  - We tested our hypotheses with a proof of concept which confirmed that the monolithic approach would yield time savings and have performance and removal of tech debt benefits, compared with re-engineering and updating the existing frontend application
- This approach will make it simpler for developers to maintain the project in one place, rather than multiple components of the architecture, and also allows editors to more easily preview content changes, and access A/B testing features.
- Our key priority right now is to continue our content audit of the site to inform Wagtail specification. We have recently introduced working sessions where we work closely with the Tate team to define what content types are required and what can be removed, edited or replaced. We’ve also been exploring where there are opportunities to streamline the ‘to be’ editorial process by making the most of Wagtail features and functionality - for example the ability to import structured content from Word or Google Docs. These sessions are crucial for us to define the requirements for the CMS, what can be improved from the existing Drupal system and how this can inform the Wagtail specification.
- We have consulted with Tate's analytics provider to and will be working closely together to ensure any impact to event tagging is planned ahead of the migration. We will also start thinking about the SEO migration plan alongside the content migration plan to ensure we are well prepared to maintain the amount of traffic the site receives.
- The Softwire team are looking at using this project as an opportunity to make an incremental move from Tate’s current hosting infrastructure (Azure-based Infrastructure-as-a-Service (IaaS)), to a lower maintenance Platform-as-a-Service (PaaS) setup. This will mean that the Tate team can largely forget about their infrastructure, and let Azure take care of things like scaling and load-balancing.

In the next sprint we’ll be:

- Drawing upon what we’ve learned from the Tate teams so far to establish some measurable objectives and KPIs for the project with a focus on site performance and productivity / efficiency around content creation
- Holding an architecture review session with Tate, TBX and Softwire to discuss the roadmap, agree roles and responsibilities and inform sprint planning, tasks, effort and timings for Azure set up
- Conducting a Data Protection Impact Assessment for Tate website (and specifically for Tate Kids) to help understand the use and extent of processing any personal data, and assessing any associated risks and mitigation
- Continuing with our content audit to further inform for the Wagtail content model and specifications at field level
- Running big picture refinement planning to review the MoSCoW list, prioritising the "Musts" for the MVP and starting to scope out the requirements to inform sprint planning and the overarching delivery plan.
