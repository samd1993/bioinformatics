# How to download and use Ilumina's BaseSpace Sequence Hub CLI
## This script is useful for anyone that wants to download sequence data from Basespace through the terminal instead of doing it on their browser

first make a directory called bin and then download bsc into that directory:

	mkdir $HOME/bin
 
	wget "https://api.bintray.com/content/basespace/BaseSpaceCLI-EarlyAccess-BIN/latest/\$latest/amd64-linux/bs?bt_package=latest" -O $HOME/bin/bs
 
while not necessary run this just in case your server requires it

	chmod u+x $HOME/bin/bs
  
Install bscp

	wget https://api.bintray.com/content/basespace/BaseSpace-Copy-BIN/\$latest/linux/bscp?bt_package=develop -O $HOME/bin/bs-cp

Now we must authenticate. This line will send you to a url to authenticate your server; copy paste the URL into your browser and follow the instructions

	bs auth

this lists all your projects on your basespace account (notice the IDs, you will need them in the next command

	bs list projects

You should get something like this:
_______________________
   Name         |    Id     | TotalSize
   -----------  | --------- | ----------
Project A    | 141432562 | 1360787841 
Project B    | 141378250 | 357584059  
Project C    | 139778624 | 5139415020 
Project D    | 122781570 | 3838271977   

This will download all fastq.gz files from your project. Note you have to copy paste the specific ID from your project into this

	bs download run -i <ID> --extension=fastq.gz -o ~/path/of/your/choice 

[Here](https://developer.basespace.illumina.com/docs/content/documentation/cli/cli-overview) is there official documentation on installing: 

And [here](https://developer.basespace.illumina.com/docs/content/documentation/cli/cli-examples) is more in depth documentation on how to navigate the program which I found super helpful
