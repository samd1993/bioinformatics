---


---

<h1 id="how-to-download-fastq.gz-files-from-iluminas-basespace-sequence-hub-cli">How to download fastq.gz files from Ilumina’s BaseSpace Sequence Hub CLI</h1>
<h3 id="this-script-is-useful-for-anyone-that-wants-to-download-sequence-data-from-basespace-through-the-terminal-instead-of-doing-it-on-their-browser">This script is useful for anyone that wants to download sequence data from Basespace through the terminal instead of doing it on their browser</h3>
<hr>
<p>First let’s make a directory called bin and then download bsc into that directory:</p>
<pre><code>mkdir $HOME/bin

wget "https://api.bintray.com/content/basespace/BaseSpaceCLI-EarlyAccess-BIN/latest/\$latest/amd64-linux/bs?bt_package=latest" -O $HOME/bin/bs
</code></pre>
<p>while not necessary let’s run this just in case your server requires it</p>
<pre><code>chmod u+x $HOME/bin/bs
</code></pre>
<p>Now you can install bscp</p>
<pre><code>wget https://api.bintray.com/content/basespace/BaseSpace-Copy-BIN/\$latest/linux/bscp?bt_package=develop -O $HOME/bin/bs-cp
</code></pre>
<p>Now we must authenticate with Basespace. This line will send you to a url to authenticate your server; copy paste the URL into your browser and follow the instructions</p>
<pre><code>bs auth
</code></pre>
<p>this lists all your projects on your basespace account (notice the IDs, you will need them in the next command)</p>
<pre><code>bs list projects
</code></pre>
<p>You should get something like this:</p>

<table>
<thead>
<tr>
<th>Name</th>
<th>Id</th>
<th>TotalSize</th>
</tr>
</thead>
<tbody>
<tr>
<td>Project A</td>
<td>141432562</td>
<td>1360787841</td>
</tr>
<tr>
<td>Project B</td>
<td>141378250</td>
<td>357584059</td>
</tr>
<tr>
<td>Project C</td>
<td>139778624</td>
<td>5139415020</td>
</tr>
<tr>
<td>Project D</td>
<td>122781570</td>
<td>3838271977</td>
</tr>
</tbody>
</table><p>Now the most important step. This will download all fastq.gz files from your project. Note you have to copy paste the specific ID from your project into this. See the second link below for how to download from multiple projects, subsets of projects, or how to sort by sample names</p>
<pre><code>bs download project -i &lt;ID&gt; --extension=fastq.gz -o ~/path/of/your/choice 
</code></pre>
<p><a href="https://developer.basespace.illumina.com/docs/content/documentation/cli/cli-overview">Here</a> is there official documentation on installing</p>
<p>And <a href="https://developer.basespace.illumina.com/docs/content/documentation/cli/cli-examples">here</a> is more in depth documentation on how to navigate the program which I 			   	found super helpful. You can search, sort, filter through different projects, runs, and search by sample names. This can be very helpful for people working with a large amount of datasets that want to download a subset of them or merge them with other datasets.</p>
<hr>

