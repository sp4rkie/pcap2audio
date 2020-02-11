pcap2audio
==========

what is it
----------

- a small tool to extract audio from pcap files suitable for playing it with your favorite audio editor (e.g. audacity)
- the programm tries to extract all audio data from RTP pakets
- it will look for associated audio tracks (forward and reversed direction) and mixes them to one single file
- works for PCMA only at the time of this writing

software installation
---------------------

- some prerequisites

        sudo apt install gawk tshark sox wget xxd

- download the tool

        wget https://raw.githubusercontent.com/sp4rkie/pcap2audio/master/pcap2audio.awklib
        wget https://raw.githubusercontent.com/sp4rkie/pcap2audio/master/pcap2audio
        chmod 755 pcap2audio

how to use it
-------------

- record some VoIP call with your favorite sniffer. E.g. 
        
        tcpdump -i eth4 port sip or portrange 14362-14462 -B 4096 -n -c 200000 -w trace.eth4

- to execute the program simply type

        pcap2audio -f trace.eth4

- this extracts audio in forward and reversed direction (if existent) and mixes both 
- all results currently end up in /tmp directory.

- command line options

        Usage: pcap2audio
          -h                    - print this help and exit
          -f (.+)               - pcap input file
          -v                    - increase logging verbosity

- diagnosis

The program logs all activity to file `pcap2audio.log`. This will be the first place to look at if something went wrong.

