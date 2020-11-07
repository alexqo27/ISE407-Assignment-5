<p> Assignment 5 <br>
Due: November 19, 2020 <br>

</p><ol class="enumerate" type=1><li class="li-enumerate">This problem is to compare dictionary implementations in
Julia, including Julia&#X2019;s own built-in implementation. First, get the Julia
dictionary implementation
<table class="display dcenter"><tr style="vertical-align:middle"><td class="dcell">
<span style="font-family:monospace">git clone https://github.com/JuliaLang/julia/blob/master/base/dict.jl</span>
</td></tr>
</table> 
In addition, you should choose one or two classic books that are out of
copyright and find a plain text copy on-line. Project Gutenberg is a good
place to browse. The book should have at least 10K words.<ol class="enumerate" type=a><li class="li-enumerate">Examine Julia&#X2019;s hash table implementation and describe it&#X2019;s approach in
terms of the elements we discussed in class.</li><li class="li-enumerate">Develop a Julia script that takes a book file as an input and counts the
number of occurrences of each word in the text by inserting them into a
dictionary. The value for each key should be the number of occurrences. Be
sure you strip punctuation and other characters away before insertion so
that you truly get just the words themselves. Also, make sure you ignore
case.</li><li class="li-enumerate">Measure the performance of Julia&#X2019;s dictionary implementation for this
task empirically. How best to do this is left up to you, but your analysis
should include an examination of the sensitivity to the load factor. This
may involve modifying the implementation so that table has a fixed size and
you can control the load factor manually. </li><li class="li-enumerate">Measure the performance when deletions also occur by deleting a word
that is already in the table when it is encountered a second time in the
text, then re-inserting it the third time, etc.</li><li class="li-enumerate">Modify Julia&#X2019;s implementation to change the approach in a substantive
way and do a comparison based on the same measures. Either try to improve
on Julia&#X2019;s implementation or discuss why it is difficult to do so. </li></ol></li><li class="li-enumerate">Consider an <span style="font-style:italic">m</span> &#XD7; <span style="font-style:italic">n</span> matrix such that the entries of each
row are in sorted order from left to right and the entries in each
column are in sorted order from top to bottom. We will call such a
matrix a <em>sorted matrix</em>. Note that some of the entries in the
matrix may be marked as empty, in which case we consider the value
to be infinite.<ol class="enumerate" type=a><li class="li-enumerate">Argue that all entries of a sorted matrix must be empty if the
entry (1, 1) is empty and that the matrix must be completely full
if the entry (<span style="font-style:italic">m</span>, <span style="font-style:italic">n</span>) is filled.</li><li class="li-enumerate">Give an algorithm to extract the minimum element of the matrix
in <span style="font-style:italic">O</span>(<span style="font-style:italic">m</span> + <span style="font-style:italic">n</span>) time (the main challenge is in restoring the
state of the matrix after deleting the minimum element). Your
algorithm should use a recursive subroutine that solves an <span style="font-style:italic">m</span> &#XD7;
<span style="font-style:italic">n</span> instance by solving either an <span style="font-style:italic">m</span> &#XD7; <span style="font-style:italic">n</span>&#X2212;1 instance or a <span style="font-style:italic">m</span>&#X2212;1
&#XD7; <span style="font-style:italic">n</span> instance. Give and solve a recurrence for the running time
in terms of <span style="font-style:italic">p</span> = <span style="font-style:italic">m</span> + <span style="font-style:italic">n</span> that yields the desired running time.</li><li class="li-enumerate">Give an <span style="font-style:italic">O</span>(<span style="font-style:italic">m</span> + <span style="font-style:italic">n</span>) algorithm for inserting a new element into a
non-full sorted matrix.</li><li class="li-enumerate">Explain how to sort <span style="font-style:italic">n</span><sup>2</sup> numbers in <span style="font-style:italic">O</span>(<span style="font-style:italic">n</span><sup>3</sup>) time using the
above methods without calling any other sorting algorithm as a
subroutine. </li></ol></li><li class="li-enumerate">Consider the following scheme for sorting a list of
<span style="font-style:italic">n</span> numbers. For simplicity, let&#X2019;s assume <span style="font-style:italic">n</span> = 2<sup><span style="font-style:italic">k</span></sup> for some <span style="font-style:italic">k</span>
(the numbers may have more than <span style="font-style:italic">k</span> bits). <ul class="itemize"><li class="li-itemize">
We first insert the items into a hash table with
chaining, with the hash function being the first <span style="font-style:italic">k</span> bits of the
number (this is not a good hash function in general, but serves a
purpose here). 
</li><li class="li-itemize">Next, we sort the individual lists of items in each slot in the
hash table with insertion sort.
</li><li class="li-itemize">Finally, we just concatenate all of these sorted lists together.
</li></ul><ol class="enumerate" type=a><li class="li-enumerate">
Why does this algorithm sort correctly?
</li><li class="li-enumerate">What is the worst case running time of this
algorithm and with what kinds of inputs is it realized?
</li><li class="li-enumerate">Assuming the numbers are completely random, what
running time would you expect in practice? Explain.
</li></ol></li><li class="li-enumerate">Consider the following sorting algorithm.
<pre class="verbatim">def fsort(A, beg = None, end = None):
    if beg == None:
        beg = 0
    if end == None:
        end = len(A) - 1
    if beg &gt;= end: 
        return
    if A[beg] &gt; A[end]: 
        A[beg], A[end] = A[end], A[beg]
    fsort(A, beg+1, end-1)
    if A[beg] &gt; A[beg+1]: 
        A[beg], A[beg+1] = A[beg+1], A[beg]
    fsort(A, beg+1, end)
</pre><ol class="enumerate" type=a><li class="li-enumerate">Formally show that this sorting algorithm is correct (hint: use
induction).</li><li class="li-enumerate">Write a recurrence for the running time of this algorithm.
Is this algorithm efficient? </li></ol></li></ol>
