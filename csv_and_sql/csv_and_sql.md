# Introduction

CSVs are a convinient data dumping format in cases where all data
needs to be dumped at the same time. However, they only increase the
pain when the data needs to be modified, or sorted by a particular
column for presentation purposes. It is hence convinient to have a
native ability to convert csv files to sql. In this demo, I would be
using `sqlite3` and a comma seperated CSV taken from [wikipedia](https://en.wikipedia.org/wiki/Comma-separated_values#Example).

# CSV files

For a sample, I have the following CSV file:

    Year,Make,Model,Description,Price
    1997,Ford,E350,"ac, abs, moon",3000.00
    1999,Chevy,"Venture ""Extended Edition""","",4900.00
    1999,Chevy,"Venture ""Extended Edition, Very Large""",,5000.00
    1996,Jeep,Grand Cherokee,"MUST SELL! air, moon roof, loaded",4799.00

I have another sample similar to previous one, but with line breaks in
a records entry.

    Year,Make,Model,Description,Price
    1997,Ford,E350,"ac, abs, moon",3000.00
    1999,Chevy,"Venture ""Extended Edition""","",4900.00
    1999,Chevy,"Venture ""Extended Edition, Very Large""",,5000.00
    1996,Jeep,Grand Cherokee,"MUST SELL!
    air, moon roof, loaded",4799.00

# Playing with SQL

I got some help from [this](http://stackoverflow.com/questions/14947916/import-csv-to-sqlite) SO question. Proceeding accordingly, for a
first try, I managed to import csv without headers.

As per [this](https://www.sqlite.org/cli.html#csv) guide, `.mode csv` is important to help the interpreter,
though it is normally [just an output mode syntax](https://www.sqlite.org/cli.html).

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<tbody>
<tr>
<td class="org-right">Year</td>
<td class="org-left">Make</td>
<td class="org-left">Model</td>
<td class="org-left">Description</td>
<td class="org-right">Price</td>
</tr>


<tr>
<td class="org-right">1997</td>
<td class="org-left">Ford</td>
<td class="org-left">E350</td>
<td class="org-left">ac, abs, moon</td>
<td class="org-right">3000.0</td>
</tr>


<tr>
<td class="org-right">1999</td>
<td class="org-left">Chevy</td>
<td class="org-left">Extended Edition</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">4900.0</td>
</tr>


<tr>
<td class="org-right">1999</td>
<td class="org-left">Chevy</td>
<td class="org-left">Extended Edition, Very Large</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">5000.0</td>
</tr>


<tr>
<td class="org-right">1996</td>
<td class="org-left">Jeep</td>
<td class="org-left">Grand Cherokee</td>
<td class="org-left">MUST SELL! air, moon roof, loaded</td>
<td class="org-right">4799.0</td>
</tr>
</tbody>
</table>

# Limitations

-   **Importing without creating a table,:** that is, just using csv
    headers, does not seem to work all that well, at least as of
    now. I keep getting errors in that. Will explore sometime later -
    could be a version issue.
-   **CSV with line breaks in record entries:** breaks emacs tabular
    environment. That is a rare corner case, though, and can be
    worked around by adding `:results verbatim` to header args.

# Bonus: SQL to CSV conversion

This is possible via `sqlite3` inbuilt commands. Can explore this when
needed.
