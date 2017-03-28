# tc-easy
Easy traffic control: bandwith, latency, and jitter

This script wraps the Linux 'tc' command to do a few easy things;
namely limit the bandwidth, latency, or jitter on an interface.

Enjoy!

## Usage

    tc-easy [options] BW LT JT [interface]

       BW = Bandwidth limit, 0 for unlimited
       LT = Latency, 0 for no latency
       JT = Jitter, 0 for none
       All ommited (all 0) means to remove any restrictions.

    If interface is omitted, the first global scope interface is used.

     Options:
       -h    --help          Usage summary
       -t    --test          Test mode; with -v shows the commands
       -v    --verbose       Verbose output

## Examples
       tc-easy                  # with nothing, clears traffic shaping
       tc-easy 550kbit          # Bandwidth limited to 550,000 bits-per-second
       tc-easy 0 350ms 10ms     # Latency set to 350msec with 10msec jitter
       tc-easy 1Mbit 0 0 eth3   # Bandwith to 1M bits-per-seconds on eth3

     Units:
       For Bandwidth
         kbps is really kilo "Bytes" per second
         kbit is really kilo "bits" per second
         mbps and mbit, gbps and gbit are similar.
       For latency and jitter, use 'ms' for milliseconds i.e. 13ms
