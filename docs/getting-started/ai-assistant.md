---
description: Using the DataDistillr AI Assistant to Write Queries
---

# Crafting a Query With AI 
DataDistillr has a powerful AI assistant which can help you ask questions of your data without having to have any understanding of SQL or other coding.  It's like Google but with your data.

## Asking a Question:
To activate the AI assistant, simply click on the helper icon from the query page.

![ai_assistant1.png](..%2Fimg%2Fgetting-started%2Fai_assistant1.png)

!!! info "Open the Data Sources in the Nav Tree"
    The AI Assistant needs to know which data sources to consider when generating the query.  To do that, all you have to do is expand these data sources in the nav tree on the left.

After you've expanded the data sources in the nav tree, click on the helper icon and you'll see a window pop up. All you have to do is ask your question in this window and click the Generate button.

![ai_assistant2.png](..%2Fimg%2Fgetting-started%2Fai_assistant2.png)

At this point you should have a query in the query view and all you have to do is click on the `Run Query` button to execute the query! 

## Example Questions
The AI engine will work with basically any question in plain language.  Example questions include:

* How many customers do I have?
* Show me all the customers who live in Arizona
* How many orders has each customer placed?
* Which products are the most popular?

The AI Assistant works in multiple languages as well, and has been tested in French, Spanish, Portuguese, Swedish, Korean and German.

!!! tip
    The AI Assistant uses the field names present in your data to craft the query.  If your data uses unusual field names, you may have to experiment with your questions to get it to generate a query that works properly.

## Limitations
The AI Assistant is still in beta and there are some limitations:

* Queries involving time are not always correct.  We are working on this.
* If your data does not have field names that accurately describe the data, the AI engine will not be able to infer the meaning of your question.