# Recursive Web Crawling

Let's now turn to a different application of recursion: *Web page crawling*.

When we first introduced recursion, we discussed the problem of recursively searching through a filesystem. We said that recursion is a natural choice for this task, since you don't know ahead of time how many directories you may need to search through. Recursing through the levels of directories avoids the need for many levels of nested loops.

Crawling Web pages is a very similar task. On the Web, pages often contain *links*, which are connections to other pages. When you click on a link, your browser brings you to the page that is the target of the link. That page may itself also be filled with links to other pages. You can continue *crawling* through links in this manner.

## Web crawler algorithm

Let's think about how we would write a Web crawler. In order to fetch pages from the Web and follow links, we would need to use a Python library to help us with these tasks. Instead of using Python, though, for the moment let's just take a look at some pseudocode to describe how the Web crawler could work:

```txt
function crawl(url, visited_links):
    if url in visited_links:
        return
    response = send_request(url)
    links = extract_links(response.content)
    visited_links.append(url)
    for link in links:
        if is_valid_link(link):
            crawl(link, visited_links)
```

In this example, `crawl()` is the main function that recursively crawls websites. The function takes two parameters: `url` is the starting URL, and `visited_links` is a list of all the URLs that have already been visited.

The function first checks if the current URL has already been visited, and if so, it returns. Otherwise, it sends a request to the URL using a function `send_request()` and extracts all the links from the response content using a function `extract_links()`. The current URL is then added to the list of visited links.

Finally, the function recursively visits each link by calling itself with the new URL. The function `is_valid_link()` is a function that checks if the link is valid, such as checking if it starts with "http."

<aside>
<b>Check your understanding</b>
<p>Why is it necessary to keep track of the list of visited links?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> On the Web, many pages can link to the same page. For example, think of all of the pages on the Web that have a link to facebook.com.</p>
<p>However, there is no need for a Web crawler to repeatedly visit the same page. Visiting the same page would be wasteful, since not only would the crawler be revisiting that page, but it would also recursively re-visit <i>all</i> of the links on that page. This could lead to circular links and an infinite loop of Web crawling.</p>
<p>Keeping track of which pages have been visited solves this problem. If we have already visited a page, it will be in the list <code>visited_links</code>, and we don't need to revisit it.
</details>
</aside>

<aside>
<b>Check your understanding</b>
<p>What are the base cases of the Web crawling algorithm?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> Recall that the base case is when a recursive call is not made. For this algorithm, there are two base cases.</p>
<ol>
<li>When a URL has already been visited, no further recursive calls are needed.</li>
<li>If a page does not contain any links, then no further recursive calls are possible.</li>
</ol>
</details>
</aside>

### Limiting recursion depth

In a massive network of pages like the Web, there could be millions and millions of pages and links to visit. In fact, there are so many pages on the Web that if you create a new website, Google estimates that it could take *weeks* for its Web crawlers to reach your Web page and add it to Google's search index.

For a simple version of a Web crawler, it might make sense to stop the crawler at a certain *depth* of recursion. By depth of recursion, we mean the number of recursive calls currently on the runtime stack. Following a link causes the Web crawler to increase its depth of recursion, and returning from a recursive call decreases the depth.

For our Web crawler, we may wish to be able to say "crawl all Web pages starting from mywebsite.com, up to a recursion depth of 10." This would allow our Web crawler to perform its task within some limits, hopefully therefore completing in a reasonable amount of time.

How would this affect our algorithm? First of all, we would need another parameter to track the current level of depth of recursion. We will call it `depth`, and give it a default value of 0. We would also need to update this parameter -- each time we make a recursive call, we need to add one to `depth`:

<pre><code>function crawl(url, visited_links=[], <b>depth=0</b>):
    if url in visited_links:
        return
    response = send_request(url)
    links = extract_links(response.content)
    visited_links.append(url)
    for link in links:
        if is_valid_link(link):
            crawl(link, visited_links, <b>depth + 1</b>)
</code></pre>

> Note: `visited_links` and `depth` have default parameter values. If either one is not specified when `crawl()` is called, then they will be assigned a default value: `visited_links` will be the empty list, and `depth` will be 0.

<aside>
<b>Check your understanding</b>
<p>The algorithm above currently updates the <code>depth</code> parameter but does not actually use it. What needs to change for the algorithm to use it?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> The <code>depth</code> needs to be checked as a part of a new base case. The recursion should stop once the <code>depth</code> reaches a certain threshold:</p>
<pre><code class="language-python">function crawl(url, visited_links=[], depth=0):
    if url in visited_links:
        return
    <b>if depth > 10:
        return</b>
    response = send_request(url)
    ...</code></pre>
</details>
</aside>
