---
title: "AD4S - SDLC as Navel-gazing"
output:
  blogdown::html_page:
    toc: false
    toc_depth: 1
    fig_width: 8
    dev: "svg"
author: "Houston Haynes"
date: '2021-04-11T15:59:43+05:30'
featuredpath: img
featured: adaptivedesign.png
ogfeatured: H3_og_wide_adaptivedesign.png
emblem: penguin_server.jpg
description: Moving Beyond Agile SDLCs 
draft: false
tags:
- AD4S
- Observability
- Accessibility
- a11y
- o11y
- Domain Driven Design
- DDD
- ethics
- AI
- ML
- CNCF
- Distributed Systems
- Cloud
categories: 
- Perspective
weight: 104
editor_options: 
  chunk_output_type: inline
---

Adaptive Design for Software [AD4S] started as a thought experiment - a moment of clarity from my 20+ years in software and leading teams - from start-ups to multi-national conglomerates. AD4S is a rubric for decisions in complex software while maintaining a first-create-then-evaluate working pattern. It provides **de**scriptive and **pre**scriptive guidance for teams to evaluate for and avoid costly mistakes in user experience, performance, scale, accessibility, sustainability, security and proactively mitigates legal and regulatory risks. It also provides a declarative framework for anticipating potential *unintended harms* and related ethical considerations - particularly those ripple effects that constantly surface in "move fast and break things" culture.

The intent of AD4S is to establish the shared responsibilities among the various constituencies that build, maintain and use the software. Think of it as version management for higher-order product guidance. Through curation of an **AD4S ledger** a shared agreement is established between the company and its customers as well as other affected groups, and provides a guide rails to the engineering teams that support those systems they build and maintain. 

> Everyone in the working group has responsibilities __outside__ of the 'super power' that brought them to their role. In Adaptive Design for Software __this precept is as foundational as the law of gravity.__

AD4S aspires to make measurable the **true cost** and actual consequences of product decisions. In order to make it useful to as many organizations as possible it is conceived as a community-led project, which will pose many challenges and opportunities. For that purpose a handful of useful TLDs have been reserved. [adaptivedesign.software, ad4s.org, ad4s.net, etc.] The next step is to establish the proper location for contributions to be collected and receive comments from the broader community. The result will be a clearinghouse of information where concepts and course-corrections can be mapped out. The hope and expectation is that organizations and individual contributors of good faith will help cultivate AD4S precepts and help build an actionable, responsive and responsibility-minded compendium for crafting better software.

What follows is a series of notes, sketches and ideas that outline the problem space, along with a few ideas around how to shape a potential solution. This isn't an attempt to create the entire AD4S site on my blog - but more of my own "sketchbook" of examples that underscore the need for AD4S to exist - and hopefully inspire some constructive dialog along the way. Readers should expect to see additional entries and *more* than a few edits in the coming days and weeks.

# Everything Old Is New Again

There are natural innovation and implementation cycles in software architecture. It's been that way since the 1970s. With the proliferation of commoditized compute and storage, patterns once thought untenable are now seeing renewed interest. But there's a dark side to progress. Due to the "surface area" of digital technologies the threats to data security have grown exponentially. Many of the intentionally naive patterns from earlier eras existed in an inherently bounded context - of limited access and confined compute space (a system used and maintained at a specific location with limited or no internet access) As those early architectural ideas are re-imagined for the information age, so too must shielding and resiliency be re-imagined for those patterns to be useful in a forward-looking digital landscape.

`r blogdown::shortcode("ext-flink-card", "https://www.scmagazine.com/home/security-news/vulnerabilities/namewreck-is-the-latest-collision-between-tcp-ip-and-the-standards-process")` 

# On the toxicity of performative leadership

In large organizations it's common to hear software project meetings punctuated with the casual disclosure to the effect of "I'm here to represent the business". This is most often brandished in project management as a means to confer authority - but can surface within a variety of roles across the working group for any number of reasons. To be fair this *can* be a constructive comment, but decades of experience tells me it's more akin to explaining a joke - if you *have* to explain it, it's not funny. While it's more common for this type of troubling language to be passed around in corporate IT (where software is a cost center for the business, as opposed to being a driver of profit and loss) it has leaked into prima facae software shops as well. It implies that the business-to-software-engineering dynamic can be proxied by any generalist. And as with many systemic problems it's often a signal of a broader issue within the organization.

Any manager that believes they can "buffer" themselves from the responsibility of active systems management is likely missing key elements in their background and experience to realize that this approach works against business needs. This is what "performative leadership" refers to - and it has myriad forms in any size organization. It's both a process and institutional "smell" for this attitude to persist in whatever form it takes. At its worst it's a double abdication. On one hand, engineers may be "let off the hook" to disconnect from business input due to proxies that don't have actual domain knowledge. And similarly it can also be a means for the non-adept business leaders to parachute non-technical staff into the project. While it has any number of excuses, it too often is also used to shield the responsible business party from exposing for their inability or unwillingness to provide actionable domain knowledge. These kinds of institutional disconnects - whether by accident, cultural reflex or by design are the beginning of the end for any software project and is often an unseen strategic liability for the company. The common practice of "body-ing up" the room with a cadre of eager-but-inexperienced contributors only undermines the charter and dims prospects for a timely, successful project.

## Good design and proper engineering is everyone's business

Everyone in the working group represents the business. Everyone in engineering has responsibility to comprehend the broader aims of the system they're building. Similarly, it's the role of every business person *and* their proxies to carry enough comprehension of business domain to cultivate an ongoing constructive dialog with technical resources. This includes "meeting the engineers where they are" and having a working understanding of the technical solution such that they can engage in meaningful discussion and provide useful feedback. Engineers also must have a working mental model of the current state and future state of the businesses - a shared "tribal knowledge" construct that fosters rapid solution development and minimal course corrections. There are no exceptions to this. There are no "escape hatches" - such as excusing business-facing internal software solutions as separate from customer-facing end-user applications. Regardless of the software's origins or intended use, everyone in the working group has responsibilities outside of the 'super power' that brought them to their role. In Adaptive Design for Software this precept is as foundational as the law of gravity. Without it, things simply fly apart.

## What's in a name?




# Making Sound Decisions while Maintaining Momentum

## Limit the expense of revisiting complex decisions

## Every Company has its own Domain Specific Language

### Mapping business lexicon to design entities

## Reducing the Barriers to Entry

## Complexity: Essential vs Accidental vs Incidental

# CAP Theorem

## Choosing On a Gradient - the Brewer exception

"Choosing any two" between consistency, availability and partition tolerance is *not* an real choice, but it's a rhetorical device to remind software engineers that those choices lurk at every level in a solution. By extension, architectural patterns make those choices of how those factors are weighed and balanced against each other. And even where the architect is not *intentionally* looking at those factors, technology decisions reveal implied balancing of how they view the CAP theorem in the context of system under their purview. Recognizing the various shades/gradients and triangulating between them is key to a resilient architecture.

## Redistributing Risk

## Managing Modes of Failure

## Making the Instrumentation Easier to Change

## Fault and Resource Isolation

# Best Practices vs Good Practice - a GxP approach

### The Lessons Are Everywhere

### Artifacts: Work vs Design vs Status

### Natural Tensions in Systems Design

### Realize the Power of Outlining Known Unknowns

### Avoiding conflicting & loaded terms (buzzword bingo)

## Fragile Software - Inexperience is the Worst Teacher

### Beyond Agile Development

### Saying 'yes' to consistency, 'no' to dogma

<div id="reactiveisnotenough"/>

## Being Reactive is not enough

The `r blogdown::shortcode("url-link", "reactive manifesto", "https://www.reactivemanifesto.org/")` makes progress over agile patterns and practices but still suffers from a form navel-gazing. Its self-concern imbues an unhealthy projection onto a systems users which in-effect is an abdication of responsibility. It naively creates a tautological loop where it only responds to directed input - and fails to take any notice of larger contextual boundaries in which the system *should* (and in certain legal contexts, must) operate. This includes governance and compliance, privacy, ethics, accessibility, inclusion and sustainability. It rather naively assumes that there will be no contention between competing interests of users (and system managers) and therefore makes no attempt to be the arbiter of where and how certain compromises are to be made. It also assumes that there's no potential avenues for misuse or abuse, which as we're all well aware is a very dangerous assumption. What if the business managers or marketing team asks the engineers to change the system to behave in a way that's illegal? It has this tacit assumpton if constituencies don't specifically *ask* for these things to be considered - and therefore expresses no interest in addressing those broader systemic concerns.

A system has to be smarter than "there could be rakes is in the yard" only for the handle to smack the users/engineers/legal team in the face at every step.
`r blogdown::shortcode("youtube", "aRq1Ksh-32g")`
<br>
And the world of large systems software is full of examples of exactly that happening time and again.

## Case Studies in Unforced Errors

`r blogdown::shortcode("header-centered", "3", "Case Study: Discord")`

`r blogdown::shortcode("tweet", "1382018677026000897")`

`r blogdown::shortcode("header-centered", "3", "Case Study: WhatsApp")`

`r blogdown::shortcode("tweet", "1382452553233797120")`

`r blogdown::shortcode("header-centered", "3", "Case Study: Slack")`

`r blogdown::shortcode("tweet", "1375030200745000960")`

## DDD and higher-order software design

## Are Regulated Systems All That Different From Commercial systems?

# Regarding Software Design as a Practice

## Evaluate Software Design as a peer to Other Disciplines
Software is the digital infrastructure of our lives. When you're in a vehicle going over a bridge, you want the engineers who built it to be more qualified than "some socially mal-adapted guy who dropped out of Harvard".

#### legal, medical, construction & civil engineering

<p>&nbsp;</p>

### GDPR, CCPA and related standards and regulations

`r blogdown::shortcode("ext-flink-card", "https://fortune.com/2021/04/02/aclu-shares-data-facebook-third-parties-digital-privacy")` 

# The "So what" Factor

## Is this an internal or external-facing process - both?

## Similarities to SOC 2 & 3

## Cost/Benefits Analysis

# Avoiding the Slippery Slopes

## No Analysis Paralysis

## It's not a framework

## It's not a shortcut

## Checklists are for experts

## Privacy

## Security

`r blogdown::shortcode("ext-link-card", "https://traced.app/2021/04/13/whatsapp-status-loophole-is-aiding-cyberstalkers")`
<p>&nbsp;</p>

## Ethics and Algorithmic Accountability

`r blogdown::shortcode("tweet", "1382426863008681986")`
<p>&nbsp;</p>

# What Led Me To This Point

### Lessons from 'The Two Bobs'

### Further Lessons from regulated verticals

#### Finance

#### Automotive

#### Telecom

#### Global Manufacturing

#### Healthcare

`r blogdown::shortcode("ext-flink-card", "https://www.imt.ie/news/health-researchers-blocked-by-gdpr-12-04-2021")`
<p>&nbsp;</p>

## Risk Calculation - a CVE-inspired model

Not every problem requires a software engineering "fix". Aside from the up-front costs, those over-engineered solutions can sometimes open up side doors to other problems that quickly spin out into their own engineering quagmires. Sometimes it's more cost/time effective to put a remediation procedure in place and document it as part of the solution. That's why a 'risk' type in solution management is key to surfacing that shared responsibility across engineering, operations, legal and other business groups.

[Embed/integrate doc from 2009] https://int.h3tech.dev/pdf/HHaynes_2009_simpleCVE_model_for_issue_mgmt.pdf

## Earned & Inherent Limitations of Agile Software Development

# Meta-process: Designing AD4S

## Managing the conversation

## B2C versus B2B considerations

## Commercial versus Enterprise Systems

## Build vs Buy Considerations

## Managing Growth and Adaptation

## Slippery Slopes

## Cautionary Tales

# In closing

## Further Reading

`r blogdown::shortcode("ext-flink-card", "https://abbycovert.com/make-sense/")`
<p>&nbsp;</p>

`r blogdown::shortcode("ext-flink-card", "https://www.infoq.com/articles/C4-architecture-model/")`
<p>&nbsp;</p>

`r blogdown::shortcode("ext-flink-card", "https://structurizr.com/")`
<p>&nbsp;</p>




Geez - have you really read this far?