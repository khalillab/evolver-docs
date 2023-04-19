---
description: The wiki is hosted on GitBook https://docs.gitbook.com/
---

# How to Edit the Wiki

## Making an Edit

1. Click "Edit on GitHub" on the right hand side of the page you want to edit. (Or click on the three dots next to the title to show it)
2. [Edit the file directly on GitHub and open a Pull Request](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files).



## Resources

[Other ](https://www.gitbook.com/explore)[GitBook](https://docs.airbyte.com/contributing-to-airbyte/) [communities](https://docs.rocket.chat/)

Wikipedia's [list ](https://en.wikipedia.org/wiki/Wikipedia:List\_of\_guidelines#Content\_guide)of guidelines

## Content Structure

[GitBook Link](https://docs.gitbook.com/editing-content/content-structure)

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

Shortcuts (will not work in block edit mode):  cmd + K (Mac) or ctrl + K (Windows)

#### [Internal Links](https://docs.gitbook.com/editing-content/rich-text#relative-links)

Usage:

1. Pointing towards pages, subpages, or paragraphs on this wiki

Formatting:

1. [Internal links should be relative](https://docs.gitbook.com/editing-content/content-structure), otherwise they will not be updated when the title or location changes
2. Internal links should be formatted using the inline pane
   1. This looks like [this ](../../general/evolver-community/)(when text is highlighted before clicking on the inline text editing box above the cursor)&#x20;
   2. Or this: [evolver-community](../../general/evolver-community/ "mention") (when no text is highlighted before clicking on the inline text editing box above the cursor)
3. [Block-level internal links](https://docs.gitbook.com/editing-content/content-structure) are very large and should not be used:

{% content-ref url="../../general/evolver-community/" %}
[evolver-community](../../general/evolver-community/)
{% endcontent-ref %}

#### [Absolute Links](https://docs.gitbook.com/editing-content/rich-text#absolute-links)

Usage:

1. Cite information as part of a page
2. Refer to a forum post on the topic - for questions, data, and detailed discussion
3. Refer to a specific place in a GitHub repository
4. NOT for referencing an internal page

Formatting:

1. Format like [this](https://docs.gitbook.com/editing-content/rich-text#absolute-links), not: [https://docs.gitbook.com/editing-content/rich-text#absolute-links](https://docs.gitbook.com/editing-content/rich-text#absolute-links)

