+++
title = 'Embednet First UI'
date = 2024-03-04T14:41:20Z
draft = true
+++
## Embednet is a distributed search index of the internet

The overall idea is:

1. fetch as much content from the internet as we can find
1. organize everything into a large collaborative index
1. make the index openly searchable by apps, with good quality and performance

How is this different from Google? The main difference is we want to allow
developers to *embed the search results into their applications*, which I think
is pretty useful for LLM-based systems. To do that, we are proposing the
creation of an open protocol, the embednet protocol, to organize the world's
information and make it universally accessible and useful. More on that later.

## Re-organize the world's information

A lot of the world's information has been digitized but it is hard to find
using just standard internet protocols. We have to go through search engines.
Tthose search engines are biased towards serving revenue-maximization content,
including ads and ads-supported content.

Ads are not a problem by itself - the problem is that they are so dependent on
ads that search engines need users to go through their UI. They can't allow
developers to build alternative UIs or integrating the results of the search
queries directly into their products.

The intriguing thought was: what if we used open-weight embedding models and
other open technologies to index as much content as we can and make everything
searchable by developers in a way that enables the creation of new
applications?

## Current progress

Embednet works as such:

1. fetch datasets from hugging face, kaggle etc.
2. split the content using different chunk sizes
3. calculate document embedding vectors for every chunk using open-weight models
4. store each chunk along with a ton of metadata into a distributed index
5. allow searching over that index, optionally with re-ranking and filtering

The biggest missing piece is the ability to search over a distributed index
spread over many different servers. That is coming soon.

For now, here's the little UI we have:

![embednet search results](results.png)

## Flask

I experimented with different web UIs framerworks. I tried [Gradio](https://www.gradio.app/)
but quickly had to move to a custom Flask app because I needed more control 
over how the content is displayed.

Right now this is just a wall of text, but we'll want to display images, result
scores, debugging information, etc so we'll just use good old HTML/CSS and
Javascript.
