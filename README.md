pcap2audio
==========

what is it
----------

- a CLI tool to extract conversation audio from VoIP calls by means of RTP packets residing in pcap files
- the retrieved audio is suitable for playing it with your favorite audio editor (e.g. audacity)
- the program tries to extract all available audio data based on encountered RTP packets
- it will look for associated streams (forward and reversed direction) and mixes them into one single file
- generated file names are composed of the starting date of the call for easier identification
- works for PCMA only at the time of this writing

software installation
---------------------

- some prerequisites

        sudo apt install gawk tshark sox xxd wget

- download the tool

        wget https://raw.githubusercontent.com/sp4rkie/pcap2audio/master/pcap2audio.awklib
        wget https://raw.githubusercontent.com/sp4rkie/pcap2audio/master/pcap2audio
        chmod 755 pcap2audio

how to use it
-------------

- record some VoIP call with your favorite packet sniffing tool. Example using tcpdump for this:
        
        tcpdump -i eth4 port sip or portrange 14362-14462 -B 4096 -n -c 200000 -w trace.eth4

- to execute the program simply type (for the example above):

        pcap2audio -f trace.eth4

- this extracts audio in forward and reversed direction (if existent) and mixes both 
- all results currently end up in `/tmp` directory.

- command line options

        Usage: pcap2audio
          -h                    - print this help and exit
          -f (.+)               - pcap input file
          -v                    - increase logging verbosity

- diagnosis

The program logs all activity to file `pcap2audio.log`. This will be the first place to look at if something went wrong.

