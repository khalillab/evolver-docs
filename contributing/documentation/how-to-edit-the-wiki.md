# How to Edit the Wiki

## Overview

The wiki is hosted on GitBook. For more information, check out their [documentation](https://docs.gitbook.com/).

## Method 1: Open a Change Request on GitBook

### When to use

Making more than a few edits to the Wiki

### Information

Change requests are saved automatically

Your can access your change request draft at any time by clicking "Change Requests" in the upper left hand corner

For more information see the GitBook [documentation](https://docs.gitbook.com/collaboration/collaboration/change-requests)

### Guide

1. Sign up for [GitBook](https://app.gitbook.com/)
2. Get an invite to the organization (email your Khalil lab contact)
3. Navigate to the eVOLVER Wiki by switching organization to Khalil Lab

![](../../.gitbook/assets/image.png)

4. Click "Edit" in the top right corner to open a Change Request
5. Use the GitBook [editor](https://docs.gitbook.com/content-creation/editor) to make your changes
   1. Try to match existing formatting
   2. Follow our formatting [guidelines](how-to-edit-the-wiki.md#content-structure), especially for links
6. Once finished with changes, click "Submit for review"
7. Your request will be reviewed and possibly edited before being merged with the Wiki

## Method 2: Comment on GitBook

### When to use

Suggestions, opening a discussion, or questions

Making only a few edits to the Wiki

### Guide

1. Sign up for [GitBook](https://app.gitbook.com/)
2. Get an invite to the organization (email your Khalil lab contact)
3. Navigate to the eVOLVER Wiki by switching organization to Khalil Lab

![](../../.gitbook/assets/image.png)

4. &#x20;See the GitBook [documentation](https://docs.gitbook.com/collaboration/comments-discussion)

## Method 3: Edit on GitHub&#x20;

Less recommended because it does not translate Markdown

Does not require joining GitBook, only requires GitHub account

1. Click "Edit on GitHub" on the right hand side of the page you want to edit. (Or click on the three dots next to the title to show it)
2. [Edit the file directly on GitHub and open a Pull Request](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files).

## Resources

[Other ](https://www.gitbook.com/explore)[GitBook](https://docs.airbyte.com/contributing-to-airbyte/) [communities](https://docs.rocket.chat/)

Wikipedia's [list ](https://en.wikipedia.org/wiki/Wikipedia:List\_of\_guidelines#Content\_guide)of guidelines

## Content Structure

### Page Content

What content goes in a page?

What content doesn't go in a page?

* Long blocks of code
  * Reference to a forum post discussing the code
  * Exception: where code is walked through line-by-line as an illustration

Links to subpages in a table of contents

### Subpage Content

Content specific to subpages - anything not listed is the same as pages

## Formatting

### Links

Shortcuts (will not work in block edit mode):  `cmd + K` (Mac) or `ctrl + K` (Windows)

Usage:

1. Pointing towards pages, subpages, or paragraphs on this wiki

Formatting:

1. [Internal links should be relative](https://docs.gitbook.com/content-creation/editor/inline/link), otherwise they will not be updated when the title or location changes
2. Internal links should be formatted using the inline pane
   1. This looks like [this ](../../general/evolver-community/)(when text is highlighted before clicking on the inline text editing box above the cursor)
   2. Or this: [evolver-community](../../general/evolver-community/ "mention") (when no text is highlighted before clicking on the inline text editing box above the cursor)
3. Block-level internal links are very large and should not be used (such as the following):

{% content-ref url="../../general/evolver-community/" %}
[evolver-community](../../general/evolver-community/)
{% endcontent-ref %}

#### [Absolute Links](https://docs.gitbook.com/content-creation/editor/inline/link#absolute-links)

Usage:

1. Cite information as part of a page
2. Refer to a forum post on the topic - for questions, data, and detailed discussion
3. Refer to a specific place in a GitHub repository
4. NOT for referencing an eVOLVER Wiki page

Formatting:

1. Format like [this](https://docs.gitbook.com/content-creation/editor/inline/link#absolute-links), not: [https://docs.gitbook.com/content-creation/editor/inline/link#absolute-links](https://docs.gitbook.com/content-creation/editor/inline/link#absolute-links)
