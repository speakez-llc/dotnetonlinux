---
title: "Flexing Accessibility"
output:
  blogdown::html_page:
    toc: false
    toc_depth: 1
    fig_width: 8
    dev: "svg"
author: "Houston Haynes"
date: '2020-10-11T15:59:43+05:30'
featuredpath: img
featured: accessibility.png
ogfeatured: H3_og_wide_accessibility.png
emblem: sitemap.png
description: Creating an adaptive "dark mode" switch using CSS, JavaScript and Bootstrap
draft: false
tags:
- blogdown
- JavaScript
- Bootstrap
- Accessibility
- a11y
- dark
categories: 
- Sidebar
weight: 
editor_options: 
  chunk_output_type: inline
---
# A Devil's (in the details) Bargain
I told myself I'd keep this simple. And even though I failed in that goal, the compromises yielded important lessons along the way. As usual those lessons started as roadblocks. Hopefully this entry will help others save some time and frustration when considering a similar path. As with anything web and JavaScript related - beyond here be dragons.

## Re-using & extending code

I looked for a simple (there's that word again) dark mode switch for my site that didn't involve managing multiple themes. I had created SASS-based multi-theme frameworks for commercial sites, but for a personal site that felt like *a bridge too far*. I had been using a dark mode browser extension and after some research online <a href="https://radu-matei.com/blog/dark-mode/" target="_blank">found this article that borrowed CSS from a similar plugin</a>. As a bonus, the author also uses the same Hugo template that I had repurposed for my R/blogdown site. So I started with that as a boilerplate.

Aside from the clever use of CSS filtering for base elements, which I outline below with my own tweaks, I also shoe-horned some JavaScript together to cover a few extended scenarios. It not only manages the toggling for the button control on my site but also allows for a reset condition. While I was at it, I also included the ability for the site to pick up the OS or browser-level dark/light user defaults, where a "parent setting" could determine which mode is selected. 


### Spoiler Alert

And here is the final JavaScript which runs checks on page load and includes some event listeners. I'll spell out some details in this entry but there are some spoilers in the inline comments. And if you want to start with the simplest version of this JS you can refer to the article where I started, which simply responds to the user action on the on-screen control.

```js
const toggle = document.getElementById("dark-mode-toggle");
const clear = document.getElementById("clear-dark-mode");
const modal = document.getElementById("myModal");
let darkTheme = document.getElementById("dark-mode-theme");

// set mode on page load
document.addEventListener("DOMContentLoaded", setDefaultMode, false);

// Checks for value pushed from OS or browser settings
const darkMediaQuery = window.matchMedia('(prefers-color-scheme: dark)');

// this try/catch only exists because of Safari being weird
try {
    // Chrome & Firefox
    darkMediaQuery.addEventListener('change', (e) => {
        setDefaultMode();
    });
} catch (e1) {
    try {
        // Safari
        darkMediaQuery.addListener((e) => {
            setDefaultMode();
        });
    } catch (e2) {
        console.error(e2);
    }
}

// changes theme when sun/moon clicked on the menu
toggle.addEventListener("click", toggleSwitch, false);

// pop modal and clear localStorage when 'reset' clicked
clear.addEventListener("click", resetLocalStorage, false);

function resetLocalStorage() {
    $('#myModal').modal('show');
    localStorage.removeItem('dark-mode-storage');
    // rerun the default function to pick up browser/OS setting
    setDefaultMode();
}

// changes the menu logo and triggers the theme change
function toggleSwitch() {
    if (toggle.className === "fas fa-moon") {
        setTheme("dark");
    } else if (toggle.className === "fas fa-sun") {
        setTheme("light");
    }
}

function setTheme(mode) {
    localStorage.setItem("dark-mode-storage", mode);

    if (mode === "dark") {
        // set dark theme
        darkTheme.disabled = false;
        toggle.className = "fas fa-sun";
    } else if (mode === "light") {
        // set light theme
        darkTheme.disabled = true;
        toggle.className = "fas fa-moon";
    }
}

function setDefaultMode() {
    // check if localStorage value exists
    if (localStorage.getItem('dark-mode-storage')) {
        // get the value and set the theme
        console.log("localStorage value used to set light/dark")
        let savedTheme = localStorage.getItem("dark-mode-storage");
        setTheme(savedTheme);
    } else {
        //check user preferences for browser scheme
        if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
            // set dark theme
            darkTheme.disabled = false;
            toggle.className = "fas fa-sun";
            console.log('dark mode is enabled by browser/OS preference');
        } else {
            // set light theme            
            darkTheme.disabled = true;
            toggle.className = "fas fa-moon";
            console.log('light mode is enabled by browser/OS preference');
        }
    }
}
```

## Actions, overt and implied

On page load, the "setDefaultMode" function checks for an existing localStorage setting (ostensibility from a previous user action which set the value). If that's not found then it bases the "disabled" true/false setting in the header on whether the browser or OS preference is present. That's used by checking the darkMediaQuery constant. So where the user had set dark mode as the default for the browser or OS, then the page would simply follow suit without a direct action by the user. Unfortunately the code is a bit more convoluted than one might expect. There's a listener that checks for changes to that top-level setting, so that if the user switches between light and dark mode on their device that the page will continue to follow the default. But it's not quite that easy. As it turns out, Safari is behind the rest of the web world and continues to use a deprecated "addListener" method instead of the standard "addEventListener". That's the genesis of the *try-catch-catch* function, where when the first event "falls through" on Safari, the first catch enables the listener to function in that browser. 

I tested a version of this without the deprecated "addListener" against the latest version of Safari on iOS 14 and it worked. So I expect other versions of Safari to "catch up" eventually. In that case the "try" still applies and all will be well. Such as it is, this is an object lesson in how there's still some fragmentation out there for support of accessibility features. And well - while it will continue to get better - that's just the nature of the web.

## Late Additions

Because of wanting to allow for that "following the default setting" behavior I had to add a reset control. This clears any localStorage value and the listener takes whatever was set on the browser or OS level. As for how it's displayed, there was a bit of arm-wrestling with Bootstrap to get the contol to appear in a way that was integral with the dark/light mode switch. The end result displays as part of the dark mode control without crowding the menu with yet another "button".



## Modal Behavior

Originally I had set the behavior to simply "flip the switch" when the reset control was activated. When the "reset" toggle was clicked the site would "snap" to that setting as quickly as the CSS changes could be rendered on the canvas. However the behavior in certain browsers is not exactly as expected, since it's possible that the localStorage value and system-set value could match. Also, there are settings on the browser level that can sometimes conflict with the OS-level setting (which I found on mobile devices when testing) that meant the user could end up with a confusing end result. If the browser was still set to the same mode as the localStorage setting, and the OS was set to the opposite value, the user would see *no* change in the browser canvas. The prompt in the modal is there to add some context to this multi-tiered control.



While the standard "Close" and "times" buttons are on the modal, it's also set to clear on any click within the desktop space. It's not really dependent on the user confirming the modal for any behavior to change. I did that as a measure of convenience, but am also aware that it too might cause some confusion. Either way, once the top-level experience was in-hand I could deal with some unintended consequences with various elements inside the page. It can feel like a "game of whack-a-mole" but the end result was worth the effort.

## Masking dark mode in media embeds

I take advantage of Hugo's built-in templates for Vimeo and Twitter post embeds. But that has an unintended consequence of creating a "photo negative" effect for videos and image thumbnails in Twitter posts. I could have stayed with simply masking the changes for those embeds with a "not" clause in the CSS. But in this case I wanted to tweak things a bit by reducing the brightness and contrast for a truer "dark mode" experience.

```css
iframe[src^="https://player.vimeo.com/video"],
iframe[src^="https://platform.twitter.com"] {
    filter: invert(100%) hue-rotate(180deg) brightness(90%) contrast(95%);
    -webkit-filter: invert(100%) hue-rotate(180deg) brightness(90%) contrast(95%);
}
```

I was tempted to "surface" the internal Vimeo and Twitter embed templates in Hugo and modify them for my site. But again, I'm trying to split the difference between honoring the spirit of this browser feature set without overinvesting for what amounts to a personal tech vanity site. Considering usability issues like this have shifted "dark mode" from a convenience feature and more about how users who *need* this functionality can better interact with the site. This is still a burgeoning field within the web community, and I'll continue to refactor to make the site better suited to *"a11y"* standards as I learn work more with Hugo. (or when I transition to another framework which makes this more manageable)

## desktop versus mobile dark mode preferences

As mentioned above with the modal, I mistakenly believed that the OS-level listener was the only setting I had to account for. As it turns out there are also mobile settings in the browser and the device level settings. 



And here's the setting in Chrome for my Samsung Note10+. I noticed that this is only available in the mobile app. No equivalent setting exists in Chrome desktop. 



And beyond the device settings Samsung provides a control in their Bixby applet. I was able to put a widget that could flip the value manually without diving into device settings. And while this can be triggered based on a variety of conditions, here I'm simply using it for testing purposes.



So while the solution makes a good-faith-effort to provide a smooth user experience, there's still quite a bit of fragmentation in the marketplace. Different operating systems, browsers and devices approach accessibility their own way. And I expect that will continue to be the case as standards and practices are sorted out.

## Future Tweaks and Re-Engineering

This has been a good start, but more work remains to be done. The gray background for charts and code blocks (that I thought would be "easy on the eyes") actually creates a low contrast experience that's antagonistic to certain conditions and communities. Fortunately some of these things can be adjusted by simply selected a new "theme" that has a better default accessibility posture. In other cases I'll have to "get under the hood" and re-tool some of my R-based and Highcharts-rendered reports. That work is continuing now.

# Another Beginning

As usual, what started as "simple" will require more thought and work, and fortunately there are quite a few tools online to help with that process. I'm a huge fan of <a href="http://paletton.com/" target="_blank">paletton</a> not only for evaluating color schemes, but also for its vision simulator.



If you're looking at the low contrast between the menus and the text, the irony of that is not lost on me, either. Still it's an invaluable tool for checking color choices against the ability for people with different conditions to pick up the nuances in your color palette. There's also <a href="https://webaccessibility.com/" target="_blank">the webaccessibility site</a> also offers an initially free service which checks a wide variety of web settings. And a web search reveals a plethora of options, and I expect this only to become more common as standards and practices emerge.

This will continue to be a developing topic and I'm looking forward to moving past the "convenience feature" of dark mode and make the site more accessible to everyone.