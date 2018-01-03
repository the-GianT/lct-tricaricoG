# lct-tricaricoG
last class today for 2018-01-02, to be added to the main one for pd. 5

## Tuesday, 2018-01-02 Socket to Me by Gian Tricarico

Today we began learning the basic concepts of networking. We will be moving on
to the coding part shortly and then we will go back to learn more about
conceptual networking stuff, as we young Padawans have much to learn.

### Socket

A socket is a connection between two programs over a network. Each socket corresponds to an IP* Address/Port pair (by that I mean a pair consisting of an IP
Address and a Port, not an IP Address or a Port pair, in case there is any
confusion with the slash I used in that sentence).

*IP stands for internet protocol.

To use a socket, you must

0. create the socket
1. bind it to an address and port
2. listen/initiate a connection (This is similar to how the clients and servers
behaved when we were working with pipes.)
3. send/receive data

### IP Addresses

All devices connected to the internet have an IP address. IP addresses come in
two flavors: IPv4 and IPv6. Addresses are allocated in blocks to make routing
easier.

IPv4 has 4-byte addresses of the form:

[0-255].[0-255].[0-255].[0-255]
(each group contains some integer from 0 to 255)

Each of these four groups is called an *octet*, because each group is 8 bits,
or one byte. At most there are 2<sup>32</sup>, or approximately 4.5 billion, IP
addresses. Teh problem is, that's not enough for the multitude of computers and
devices connected to the interwebs. We use network address translation to deal
with this, where there are multiple private addresses within a network that has
its own single public IP address. However, there is also IPv6, created to make
room for many more addresses (approximately 2<sup>128</sup>, which is a very
large number). IPv6 addresses use this format:

[0-ffff]:[0-ffff]:[0-ffff]:[0-ffff]:[0-ffff]:[0-ffff]:[0-ffff]:[0-ffff]
(using hexidecimal notation)

Each group in this system is known as a hextet (although this is not as standard
of a term as octet). In order to write it out more concisely, we ignore leading 0s and replace any number of consecutive all 0 hextets with the double colon (::). One can only use the double colon once in a single IP address, as otherwise the address would be ambiguous.

For example, we can write

0000:0000:0000:004f:13c2:0009:a2d2

as

::4f:13c2:9:a2d2

IPv4 Mapped addresses have the following format:

0000:0000:0000:0000:0000:ffff:[IPv4 portion of the address], 

for example,

0000:0000:0000:0000:0000:ffff:12.155.166.101,

or simply

::ffff:12.155.166.101 for short.

This allows us to convert every possible IPv4 address to a corresponding IPv6
address, but not the other way around, which creates compatibility issues that
help explain why IPv4 is still the standard for the internet and the transition
to IPv6 is proceeding quite slowly.

**Tech News** [Iran blocks messaging app Telegram used by protesters](https://www.usatoday.com/story/tech/2018/01/02/iran-blocks-messaging-app-used-protesters-share-info-demonstrations/998445001/)