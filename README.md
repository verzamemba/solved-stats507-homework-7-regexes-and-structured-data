Download Link: https://assignmentchef.com/product/solved-stats507-homework-7-regexes-and-structured-data
<br>
<h1>1         Regular Expressions: Warmup</h1>

In this problem, you’ll get practice with basic regular expressions. Pay particular attention to edge cases such as the empty string and single-character strings when writing your regexes. At the URL <a href="http://www.greenteapress.com/thinkpython/code/words.txt">http://www.greenteapress.com/thinkpython/code/words.txt </a>is a list of about 100,000 English words.

<ol>

 <li>Use urllib to open the URL and read the file, and produce a list of ASCII strings so that each line of the file corresponds to an element of the list. You will likely need to convert the raw bytes read from the webpage to ASCII characters, for which you should see the documentation for the string methods encode and decode. How many words are in the file?</li>

 <li>It is a good habit to always look at your data to check that it makes sense. Havea look at the words in the list. Does anything jump out at you? <strong>Note: </strong>I am not requiring you to do anything specific, here. Just look at the data!</li>

 <li>Write a regular expression that matches any string containing exactly four consecutive consonants. Compile this regular expression, and assign it to a variable called four_consecutive_consonants. Use this regex to determine how many words from the list contain exactly four consecutive consonants. For the purposes of this <strong>specific </strong>problem, the vowels are a, e, i, o, u, y. All other letters are consonants. Produce a list of all such words.</li>

 <li>Write a regular expression that matches any string that contains no instances of theletter e. Compile this regular expression, and assign it to a variable called gadsby. (<em>Gadsby </em>is the title of an English novel written in the 1930s that contains <em>almost </em>no instances of the letter e). How many words in the list do not contain the letter e?</li>

 <li>Write a regular expression that matches any string that begins and ends with avowel and has no vowels in between. For the purposes of this <strong>specific </strong>problem, y is neither consonant nor vowel, so consonants are the 20 letters that are not one of a, e, i, o, u, y and vowels are a, e, i, o, u. The words need not begin and end with the <em>same </em>vowel, so angle is a valid match. Compile this regular expression, and assign it to a variable called vowel_vowel. How many words begin and end with a vowel with no vowels in between?</li>

 <li>Write a regular expression that matches any string whose last two characters arethe first two characters in reverse order. So, for example, your regex should match repeater and stats, but not neoprene. Compile this regular expression and assign it to a variable called bookends. How many words in the list have this property? <strong>Hint: </strong>be careful of the cases in which the word is length less or equal to 3. You may handle the case of a single character (e.g., a), as you like, but please give an explanation for your choice.</li>

</ol>

<h1>2         Exploring Internet Traffic with Regexes</h1>

In this problem, you’ll get a taste of a more realistic application of regular expressions. The file  contains data generated by web traffic associated with Skype and IRC, captured using the Wireshark program, a common tool for analyzing web traffic. The original data file can be found on the Wireshark wiki, <a href="https://wiki.wireshark.org/SampleCaptures">https://wiki.wireshark.org/SampleCaptures</a><a href="https://wiki.wireshark.org/SampleCaptures">,</a> but please use the file provided on my website for this assignment.

<ol>

 <li>Download the file from the URL above (or use urllib or requests to open it directly, being careful to convert the raw bytes back to UTF-8) and read its contents into a string. Each line of this file corresponds to a single packet sent over the internet. How many packets are in this file? Save the answer in a variable n_packets. <strong>Note: </strong>if you decide to download the file, don’t forget to include a copy of it in your submission so that we can run your code.</li>

 <li>Use regular expressions to extract all the IP addresses from the file and collect themin a Python list. An IP address consists of four numbers, which are displayed as B.C.D where A,B,C and D are each numbers between 0 and 255. How many unique IP addresses appear in the data set? Save the answer in a variable ip_addresses</li>

 <li>Write a function called get_packets_by_regex that takes a single raw string as its argument and returns all lines of the input file that match the input raw string as a regular expression. So, for example, get_packets_by_regex(r’comcast’) will return all lines from the file containing the string ’comcast’. Your function should perform appropriate error checking to ensure that the input is a string, but you do not need to check that it is a raw string.</li>

 <li>The second piece of text (i.e., non-whitespace) on each line is a time stamp, countingthe time (in seconds) since the beginning of the traffic recording. Using matplotlib, create a plot displaying how many packets appeared in each second of the recording. A histogram or line plot is the most obvious way to do this, but you should feel free to use a more creative way of displaying this information if you wish to do so. <strong>Note: </strong>in case it wasn’t obvious, there is no need to use a regular expression for this subproblem if you do not want to.</li>

</ol>

<h1>3         Retrieving Data from the Web</h1>

In this problem, we’ll scrape data from Wikipedia using BeautifulSoup. Documentation for BeauitfulSoup can be found at <a href="https://www.crummy.com/software/BeautifulSoup/bs4/doc/">https://www.crummy.com/software/BeautifulSoup/ </a><a href="https://www.crummy.com/software/BeautifulSoup/bs4/doc/">bs4/doc/</a><a href="https://www.crummy.com/software/BeautifulSoup/bs4/doc/">.</a> As mentioned in lecture, there is another package, called requests, which is becoming quite popular, which you are welcome to use for this problem instead, if you wish. Documentation for the requests package can be found at <a href="http://docs.python-requests.org/en/master/">http://docs. </a><a href="http://docs.python-requests.org/en/master/">python-requests.org/en/master/</a><a href="http://docs.python-requests.org/en/master/">.</a>

Suppose you are trying to choose a city to vacation in. A major factor in your decision is weather. Conveniently, lots of weather information is present in the Wikipedia articles for most world cities. Your job in this problem is to use BeautifulSoup to retrieve weather information from Wikipedia articles. We should note that in practice, such information is typically more easily obtained from, for example, the National Oceanic and Atmospheric Administration (NOAA), in the case of American cities, and from analogous organizations in other countries.

<ol>

 <li>Look at a few Wikipedia pages corresponding to cities. For example:

  <ul>

   <li><a href="https://en.wikipedia.org/wiki/Ann_Arbor,_Michigan">https://en.wikipedia.org/wiki/Ann_Arbor,_Michigan</a></li>

   <li><a href="https://en.wikipedia.org/wiki/Buenos_Aires">https://en.wikipedia.org/wiki/Buenos_Aires</a></li>

   <li><a href="https://en.wikipedia.org/wiki/Harbin">https://en.wikipedia.org/wiki/Harbin</a></li>

  </ul></li>

</ol>

Note that most city pages include a table titled something like “Climate data for [Cityname] (normals YYYY-YYYY, extremes YYYY-YYYY)” Find a Wikipedia page for a city that includes such a table (such as one of the three above). In your jupyter notebook, open the URL and read the HTML using either urllib or requests, and parse it with BeautifulSoup using the standard parser, html.parser. Have a look at the parsed HTML and find the climate data table, which will have the tag table and will contain a child tag th containing a string similar to

Climate data for [Cityname] (normals YYYY-YYYY, extremes YYYY-YYYY).

Find the node in the BeautifulSoup object corresponding to this table. What is the structure of this node of the tree (e.g., how many children does the table have, what are their tags, etc.)? You may want to learn a bit about the structure of HTML tables by looking at the resources available on these websites:

<ul>

 <li><a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table">https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table</a></li>

 <li><a href="https://www.w3schools.com/html/html_tables.asp">https://www.w3schools.com/html/html_tables.asp</a></li>

 <li><a href="https://www.w3.org/TR/html401/struct/tables.html">https://www.w3.org/TR/html401/struct/tables.html</a></li>

</ul>

<ol start="2">

 <li>Write a function retrieve climate table that takes as its only argument a Wikipedia URL, and returns the BeautifulSoup object corresponding to the climate data table (if it exists in the page) and returns None if no such table exists on the page. You should check that the URL is retrieved successfully, and raise an error if urllib2 fails to successfully read the website. You may notice that some city pages include more than one climate data table or several nested tables (see, for example, <a href="https://en.wikipedia.org/wiki/Los_Angeles">https://en.wikipedia.org/wiki/Los_Angeles</a><a href="https://en.wikipedia.org/wiki/Los_Angeles">)</a>. In this case, your function may arbitrarily choose one of the tables to return as a BeautifulSoup <strong>Note: </strong>a good way to check for edge cases is to test your script on the Wikipedia pages for a few of your favorite cities. The pages for Los Angeles, Hyderabad and Boston will give good examples of edge cases that you should be able to handle, but note that these are by no means exhaustive of all the possible edge cases. <strong>Hint: </strong>make use of the contents attribute of the BeautifulSoup objects and the ability to change the elements of the contents list to Unicode.</li>

 <li>As you look at some of the climate data tables, you may notice that different cities’tables contain different information. For example, not all cities include snowfall data. Write a function list_climate_table_row_names that takes as its only argument a Wikipedia URL and returns a list of the row names of the climate data table, or returns None if no such table exists. The list returned by your function should, ideally, consist solely of Python strings (either Unicode or ASCII), and should not include any BeautifulSoup objects or HTML (<strong>Hint: </strong>see the BeautifulSoup method get text()). The list returned by your script should <em>not </em>include an entry corresponding to the Climate data for… row in the table. <strong>Second hint: </strong>you are looking for HTML table header (th) objects. The HTML attribute scope is your friend here, because in the context of an HTML table it tells you when a th tag is the header of a row or a column.</li>

 <li>The next natural step would be to write a function that takes a URL and a rowname and retrieves the data from that row of the climate data table (if the table exists and has that row name). Doing this would require some complicated string wrangling to get right, so I’ll spare you the trouble. Instead, please <strong>briefly </strong>describe either in pseudo code or in plain English how you would accomplish this, using the two functions you wrote above and the tools available to you in the BeautifulSoup <strong>Note: </strong>just to be clear, you <strong>do not </strong>have to write any code for this last step.</li>

</ol>

<h1>4         Relational Databases and SQL</h1>

In this problem, you’ll interact with a toy SQL database using Python’s built-in sqlite3 package. Documentation can be found at <a href="https://docs.python.org/3/library/sqlite3.html">https://docs.python.org/3/library/sqlite3</a>. <a href="https://docs.python.org/3/library/sqlite3.html">html</a><a href="https://docs.python.org/3/library/sqlite3.html">.</a> For this problem, we’ll use a popular toy SQLite database, called Chinook, which represents a digital music collection. See the documentation at

<a href="https://github.com/lerocha/chinook-database/blob/master/ChinookDatabase/DataSources/Chinook_Sqlite.sqlite">https://github.com/lerocha/chinook-database/blob/master/ChinookDa</a>tabase/

<a href="https://github.com/lerocha/chinook-database/blob/master/ChinookDatabase/DataSources/Chinook_Sqlite.sqlite">DataSources/Chinook_Sqlite.sqlite </a>for a more detailed explanation. We’ll use the .sqlite file Chinook Sqlite.sqlite, which you should download from the GitHub page above. <strong>Note: </strong>Don’t forget to save the file in the directory that you’re going to compress and hand in, and make sure that you use a relative path when referring to the file, so that when we try to run your code on our machines the file path will still work!

<ol>

 <li>Load the database using the Python sqlite3 How many tables are in the database? Save the answer in the variable n_tables.</li>

 <li>What are the names of the tables in the database? Save the answer as a list ofstrings, table_names. <strong>Note: </strong>you should write Python sqlite3 code to answer this; don’t just look up the answer in the documentation!</li>

 <li>Write a function list_album_ids_by_letter that takes as an argument a single character and returns a list of the primary keys of all the albums whose titles start with that character. Your function should ignore case, so that the inputs “a” and “A” yield the same results. Include error checking that raises an error in the event that the input is not a single character.</li>

 <li>Write a function list_song_ids_by_album_letter that takes as an argument a single character and returns a list of the primary keys of all the songs whose album names begin with that letter. Again, your function should ignore case and perform error checking as in list_album_ids_by_letter. (again ignoring case). <strong>Hint: </strong>you’ll need a JOIN statement here. Don’t forget that you can use the description attribute to find out about tables and the names of their columns.</li>

 <li>Write a function total_cost_by_album_letter that takes as an argument a single character and returns the cost of buying every song whose album begins with that letter. This cost should be based on the tracks’ unit prices, so that the cost of buying a set of tracks is simply the sum of the unit prices of all the tracks in the set. Again your function should ignore case and perform appropriate error checking.</li>

</ol>