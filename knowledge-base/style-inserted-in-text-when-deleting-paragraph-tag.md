---
title: Style inserted in text when deleting paragraph tag
description: Problem: Style inserted in text when deleting paragraph tag in Chrome
type: troubleshooting
page_title: Style inserted in text when deleting paragraph tag in Chrome
slug: style-inserted-in-text-when-deleting-paragraph-tag
position: 
tags: delete, editor, paragraph, style, chrome, safari
ticketid: 1432367
res_type: kb
---

## Environment
<table>
	<tbody>
		<tr>
			<td>Product Version</td>
			<td>2019.3.917</td>
		</tr>
		<tr>
			<td>Product</td>
			<td>RadEditor for ASP.NET AJAX</td>
		</tr>
	</tbody>
</table>


## Description
These inline styles are applied by the Chrome/Safari browser as the parent page has some default decoration regarding the page's text.

## Steps to Reproduce
Here are the steps to simulate:

1. I have existing text in the editor which does not have any style formatting, e.g. 
`<p>line 1</p><p>line 2</p>`
1. Now put the cursor in the beginning of the second paragraph and hit backspace
1. As you can see from the HTML view mode it now adds a <span> tag with formatting

## Solutions

### For ContentAreaMode="iframe":

The following solution will clear out any CSS files or styles derived from the parent page and may server as a possible workaround:

````<telerik:RadEditor runat="server" ID="RadEditor1" ContentAreaMode="iframe">
    <CssFiles>
        <telerik:EditorCssFile Value="~/Empty.css" />
    </CssFiles>
</telerik:RadEditor>
````

### For ContentAreaMode="div" or for the inline editor: Define a CSS class for the RadEditor div content area which applies a default font and color to the paragraphs:

````            .reContentArea p {
                font: 13px Arial !important;
                color: black;
            }
````


