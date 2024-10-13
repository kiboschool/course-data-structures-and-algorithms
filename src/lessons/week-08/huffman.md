# Huffman Trees

One application of trees is *Huffman coding* -- building a tree (a *Huffman tree*) to encode and decode text. Often, Huffman coding also allows text to be *compressed* to take up less space for storage or transmission.

Watch the following video to see an overview of Huffman coding and the algorithm for building and using a Huffman tree:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/JsTptu56GM8"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

To summarize, text characters typically take 1 byte (8 bits) of space each. However, in many cases, documents can be compressed so that each character takes fewer than 8 bits. By building a Huffman tree based on the frequencies of characters in a document, high-frequency characters can get a short encoding (e.g., 3 bits) and low-frequency characters can get a relatively longer encoding (e.g., 6 bits). This will allow the document as a whole to be reduced in size, and then can be decoded using the Huffman tree.

## Building and using Huffman tree

Watch the video below for an explanation of (1) building a Huffman tree, (2) using a Huffman tree to compress some text, and (3) using a Huffman tree to decompress some text:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/BNRqihyzqWo"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

<aside>
<b>Check your understanding</b>
<p>Consider the following Huffman tree:</p><br>
<center>
<img src="/images/week-08/huffman-tree.png"
    class="center"
    alt="A Huffman tree showing how to code different characters. The root node has two children that are both interior nodes. The interior node on the left has a t node as the left child and an e node as the right child. The interior node on the right also has two children that are both interior nodes. Its left child has an o node as the left child and an i node as the right child. Its right child has an a node as the left child and an s node as the right child."
    style="width:325px;" />
</center>
<ol>
  <li>What is the encoding for the string <code>'satiate'</code>? What is the space savings?</li>
  <li>Use the tree to decode the string <code>1110111000111</code>.</li>
</ol>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b></p>
<ol>
  <li>The characters have the following encodings: t: <code>00</code>; e: <code>01</code; o: <code>100</code>; i: <code>101</code>; a: <code>110</code>; s: <code>111</code>. Therefore, after encoding the string <code>'satiate</code>, we get: <code>111110001011100001</code>. The original string is of length 7, so it takes up 7 * 8 = 56 bits. The encoded version of the string is 18 characters, which is 1/3 of the size!</li>
  <li>The first <code>111</code> is an s. The next <code>01</code> is an e. The next <code>110</code> is an a. The <code>00</code> is a t. And the <code>111</code> is an s. Therefore, the string is <code>'seats'</code>.</li>
</ol>
</details>
</aside>
