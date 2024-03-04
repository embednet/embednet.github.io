+++
title = 'Embednet First UI'
date = 2024-03-04T14:41:20Z
draft = true
+++
## Current plans

The overall idea is:

1. fetch interesting content from the internet
1. organize everything into a large collaborative index
1. make the index searchable by any application, with good quality and performance

How is this different from Google? The main difference is I want to allow
developers to *embed the search results into their applications*, which I think
is pretty useful for LLM-based systems.

I'll explain more later, but for now I just wanted to write down what I have so far:

1. fetch datasets from hugging face, kaggle etc.
2. split the content using different chunk sizes
3. calculate document embedding vectors for every chunk using open-weight models
4. store each chunk along with a ton of metadata in our index

The biggest missing piece is the ability to search over a distributed index
spread over many different servers. I'll work on that next. For now, here's the
little UI I created:

## Flask

I experimented with different UIs. I tried [Gradio](https://www.gradio.app/)
but quickly had to move to a custom Flask app because I needed more control 
over how the content is displayed.

![embednet search results](results.png)

Right now this is just a wall of text, but we'll want to display images, result
scores, debugging information, etc so we'll just use good old HTML/CSS and
Javascript.
