pcap2audio
==========

what is it
----------

- a small tool to extract audio from pcap files suitable for playing with your favorite audio player (e.g. audacity)
- the programm tries to find associated audio tracks and mixes them to one single file

software installation
---------------------

        sudo apt install gawk tshark sox

- download the tool

        wget https://raw.githubusercontent.com/sp4rkie/pcap2audio/master/pcap2audio.awklib
        wget https://raw.githubusercontent.com/sp4rkie/pcap2audio/master/pcap2audio
        chmod 755 pcap2audio

how to use it
-------------

- to execute the program simply type

        pcap2audio

- command line options

        Usage: CableLoadMonitor
          -h                    - print this help and exit
          -f [0-9]+(:[0-9]+)*   - cap file to read 
          -v                    - increase logging verbosity
