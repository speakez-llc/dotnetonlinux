# .NET on Linux 🐧 ❤️

This is a Hugo-based site that is deployed to Cloudflare Pages automatically when a change is made on a branch. Contributions are welcome! You'll need to install [Hugo 'extended'](https://gohugo.io/installation/linux/) and then of course fork and then clone this repository. Check out the "stage" branch and write your post in Markdown format. Create a new post by typing the following into a prompt under that cloned repo's directory.

```bash
hugo new content/post/My_post.md
```
and you'll see from that a boilerplate generated all of the frontmatter that's required to complete am SEO-ready blog entry.

```frontmatter
---
title: "My_post" # Title of the blog post.
date: 2024-06-08T15:31:20-04:00 # Date of post creation.
description: "Article description." # Description used for search engine.
featured: true # Sets if post is a featured post, making it appear on the sidebar. A featured post won't be listed on the sidebar if it's the current page
draft: true # Sets whether to render this page. Draft of true will not be rendered.
toc: false # Controls if a table of contents should be generated for first-level links automatically.
usePageBundles: false # Set to true to group assets like images in the same folder as this post.
featureImage: "/images/path/file.jpg" # Sets featured image on blog post.
featureImageAlt: 'Description of image' # Alternative text for featured image.
featureImageCap: 'This is the featured image.' # Caption (optional).
thumbnail: "/images/path/thumbnail.png" # Sets thumbnail image appearing inside card on homepage.
shareImage: "/images/path/share.png" # Designate a separate image for social media sharing.
codeMaxLines: 10 # Override global value for how many lines within a code block before auto-collapsing.
codeLineNumbers: false # Override global value for showing of line numbers within code block.
figurePositionShow: true # Override global value for showing the figure label.
showRelatedInArticle: false # Override global value for showing related posts in this series at the end of the content.
categories:
  - Technology
tags:
  - Tag_name1
  - Tag_name2
---

**Insert Lead paragraph here.**
```
From there you'll need to create the body of the page, insert any image references (and include the images in the prescribed paths) and outlinks via markdown or use of shortcodes. With the REPL in hugo (running 'hugo server' from a prompt located at the cloned project folder) you'll see the site (running at localhost:1313) update each time you save the document. Review your changes locally and when you're done, create a pull request.


Beyond post generation it's possible to make other site mods if you're experienced. But I'm likely to cherry pick the content only *unless* there's a reasonably detailed explanation for the change to the site in the PR. And as per usual, submit a PR and it will get a quick review - once it's in stage and reviewed "live" on that site I'll merge the code into main and it'll go out to the main site.

## Roadmap 🗺️

While I've done some pretty significant Hugo modifications for a site I built with R markdown, those mods require a bit of adjustment to bring them into line with the latest version of Hugo (and to dovetail into the current template). Once those updates are made there will both be entries in the site itself and some additional notes here on how to use them (and in certain cases tooling I'll provide from the SpeakEZ lab) to help smooth out some of Hugo's rough edges.

I have opened up discussion in the repo to gather feedback and help the site to expand and grow. So if you want to bring up a topic without opening an issue or submitting a PR, feel free to use that as a place to make your ideas known! Thanks! 🙏

## The Future is Open 📖

The desire for this site is to be accepting of all good faith submissions. That said, the emphasis will be on multi-platform tools and applications and advice around the Linux platform. There are plenty of outlets for corporate marketing, so the bias here is to focus on being an *alternative* to the 📣 usual channels and provide fertile ground for independent voices outside of the Microsoft sphere of influence. This *doesn't* mean that this site is anti-anything - and certainly not anti-Azure or anti-Windows. The point is to provide a clear-eyed view of the large ecosystem that has grown up around .NET both because of and *in spite of* Microsoft's position in the technology marketplace.