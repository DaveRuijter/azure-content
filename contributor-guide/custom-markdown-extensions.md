<properties title="required" pageTitle="Custom markdown extensions used in our technical articles" description="Lists the custom markdown extensions that enable embedded videos, notes and tips, reusable content, and other item in azure.microsoft.com technical articles." metaKeywords="" services="" solutions="" documentationCenter="" authors="tysonn" videoId="" scriptId="" manager="required" />

<tags ms.service="contributor-guide" ms.devlang="" ms.topic="article" ms.tgt_pltfrm="" ms.workload="" ms.date="12/16/2014" ms.author="tysonn" />

#Custom markdown extensions used in our technical articles

Our articles use standard markdown for most article formatting - paragraphs, links, lists, headings, etc. But we use custom markdown extensions where we need richer formatting in the rendered pages on azure.microsoft.com. Here's the extensions we are currently using:

- Notes and tips
- Includes (reusable content)


##Notes and tips
You can choose from 4 types of notes and tips:

- AZURE.NOTE
- AZURE.WARNING
- AZURE.TIP
- AZURE.IMPORTANT

###Usage 
In general, use notes and tips sparingly throughout your articles. When you do use them, choose the appropriate type of note or tip:

- Use AZURE.NOTE to highlight neutral or positive information that emphasizes or supplements key points of the main text. A note supplies information that applies only in special cases.

  ![](./media/custom-markdown-extensions/Notes-note.PNG)

- Use AZURE.WARNING to alert the user to a condition that might cause a problem in the future. For example, selecting a certain option or making a certain choice might permanently lock you into a particular scenario.

  ![](./media/custom-markdown-extensions/Notes-warning.PNG)

- Use AZURE.TIP to help your users apply the techniques and procedures described in the text to their specific needs. A tip might also suggest alternative methods that may not be obvious. Tips, however, are not essential to the basic understanding of the text.

  ![](./media/custom-markdown-extensions/Notes-tip.PNG)

- Use AZURE.IMPORTANT to provide information that is essential to the completion of a task.

  ![](./media/custom-markdown-extensions/Notes-important.PNG)

While these notes and tips support code blocks, images, lists, and links, try to keep your notes and tips simple and straightforward. If you find yourself creating complex notes with lots of formatting, that might be a sign you just need another section in the main text of the article. And, too many notes in an article can be distracting and hard to scan or read. 

###Sample markdown

The samples all show an AZURE.NOTE. To use a TIP, WARNING, or IMPORTANT, replace "NOTE" in the markdown:

    > [AZURE.TIP]

    > [AZURE.WARNING]

    > [AZURE.IMPORTANT] 

Single paragraph:

    > [AZURE.NOTE] To complete this tutorial, you must have an active Microsoft Azure account. If you don't have an account, you can create a free trial account in just a couple of minutes. 

Multiparagraph:

    > [AZURE.NOTE] To complete this tutorial, you must have an active Microsoft Azure account. 
    > 
    > If you don't have an account, you can [create a free trial account](http://www.windowsazure.com/en-us/pricing/free-trial/) in just a couple of minutes.

##Includes (reusable content)

Reusable text fragments in our GitHub repository are called "includes". When you have text that needs to be used in multiple articles, you include a reference to the text fragments in the markdown files. The text fragment (the include) itself is a simple markdown (.md) file. It can contain any valid markdown, including text, links, and images. All include markdown files must be in [the /includes directory](https://github.com/Azure/azure-content/tree/master/includes) in the root of the repository. When the article is published, the include text is seamlessly integrated into the published topic. 

- We use a specific syntax to reference an include.

- Media files you put in an include must be created in a media folder specific to the include. Media folders for includes belong in [the azure-content/includes/media folder](https://github.com/Azure/azure-content/tree/master/includes/media). The media directory should not contain any images in its root. If the include does not have images, then a corresponding media directory is not required. 

###Usage

- Use includes wherever you need the same text to appear in multiple articles.
- Includes are meant to be used for significant amounts of content - a paragraph or two, a shared procedure, or a shared section. Do not use them for anything smaller than a sentence; they are not for product names or incomplete sentences. 
- Don't embed includes within other includes. Bad things happen in the publishing system!
- Don't share media between files. Use a separate file with a unique name for each include and article. Store the media file in the media folder associated with the include. 
- Because all includes must be in the /includes directory, the path to an include from an article is always

    ../includes

- Do NOT repeat a link or image filename reference in both the article and the include. Add "-include" to the link reference or media filename to avoid repeating the reference:

 **Link reference**

 Change: odata.org
 To: odata.org-include

 **Image reference**

 Change: table.png
 To: table-include.png

###Sample markdown
The syntax for adding an include to a documentation article is:
 
    [AZURE.INCLUDE [include-short-name](../includes/include-file-name.md)] 

Example

    [AZURE.INCLUDE [howto-blob-storage](../includes/howto-blob-storage.md)] 
 
The first part of the include should be the include name without the path and without the .md extension. The second part should be the relative path to the include in the /includes directory.

###Rendering 

In the rendered GitHub page, the include will render as follows:

 [AZURE.INCLUDE howto-blob-storage]

In the rendered HTML on azure.microsoft.com, the HTML from the includes is merged into the rest of the document's HTML. However, the HTML will contain an HTML comment with the original include markdown filename and the GitHub commit hash. This comment is included for troubleshooting purposes so that the source content can easily be identified and found in GitHub:

  ![](./media/custom-markdown-extensions/include.png)

 