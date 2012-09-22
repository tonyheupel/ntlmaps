README file for 'NTLM Authorization Proxy Server' v.0.9.9.0.1

Release Purpose:
----------------
This is a bugfix release of the 0.9.9 stable series. See changelog.txt for full description.

There is an issue with APS working as a standalone proxy. It serves requests from
an http-client one by one and allows persistent connections, then it may receive several
request in very sort time to one thread, and one of them may be to almost dead banner
site, then all the requests made after that one will be waiting till that "bad" connection
will be closed due to timeout. So I suggest switching off HTTP/1.1 presistent connections
in your browser when you are using APS for web (not proxy) authentication and surfing
banner rich evironment.

This is a beta version, so I expect it to have bugs. If something goes
wrong, please log a support request on the sourceforge.net project page.

Please read this file to the end, it contains useful installation
instructions and other information.


1. WHAT IS 'NTLM Authorization Proxy Server'?
---------------------------------------------

'NTLM Authorization Proxy Server' is a proxy-like software, that will authorize you
at MS proxy server and at web servers (ISS especially) using MS proprietary NTLM
authorization method and it can change some values in your client's request header
so that those requests will look like ones made by MS IE. It is written in Python
language. See www.python.org.

2. WHY MAY I WANT TO USE 'NTLM Authorization Proxy Server'?
-----------------------------------------------------------
When your web browser uses proxy server to surf the Web from within your local
network your may be required to authenticate youself to use proxy. There are
two methods to do this: using 'Basic' authorization method and 'Digest' method.

'Basic' is very basic;) and not secure, but considered often as sufficient to check
users inside your local network. The second - 'Digest' - is quite secure but, as I
could note, use of it considered as 'too much' in order to protect your own proxy
server from your own people. Well, 'Digest' is far more complicate method and I don't
know any software that can use it, I think it is becuse this method simply 'overkill' for
most cases. 'Basic' method is quite common and is standard method to authenticate
yourself at proxies.

But MicroSoft, being MS, has developed instead of standard methods two its own
authentication methods - 'NTLM' (NT LanManager) and 'Negotiate'. I don't know anything
about the second one, but I spend some time on 'NTLM'.

Because NTLM (NT LanManager) is a proprietary algorithm it is looks like that
only MS's products can use it (IE3+ as far as I know). And it gives you a bunch of
fun things: If proxy server that you have to use is set so it requres your to
authenticate yourself with 'NTLM' algorithm then you will be able to use ONLY MS's
products with this proxy server. No ReGet, no WGET, no Junkbuster, no Netscape
Navigator, no Lynx or your local squid and no lots of other good software.

Why admin of proxy server in your local network may want to ban standard 'Basic'
and require 'NTLM'? I don't know. May be because he likes MS too much;).


3. HISTORY BEHIND THE 'NTLM Authorization Proxy Server'.
--------------------------------------------------------

I got the idea for 'NTLM Authorization Proxy Server' when admin in our network
swiched MS Proxy so that we had to use 'NTLM'. It was simply disaster. Everything
stopped working but IE5.5.

So then I had realized that there was no solution to make my favorite programs work with
it I decided to do something. And here you are.


4. REQUIREMENTS
---------------

You will need a thread-safe Python installation, version 1.5.2 or later.
Python is available from http://www.python.org/ . Get it, install it, and you
are ready to try. Python also comes with all GNU/Linux distributions that
I am aware of, so if you are a GNU/Linux user you should have that in your
box already.

Please note that I have not test it with Python versions higher than 1.5.2.
Therefore you may have problems with later Pythons, but I hope you will not.

5. LICENSING & PRICING
----------------------

'NTLM Authorization Proxy Server' is distributed under the GNU Public License,
which is included in this archive (see file COPYING).

The above mean that 'NTLM Authorization Proxy Server' is pretty much free.
You have to pay nothing for it.

6. CREDITS
----------
Thanks to Nathan Lineback <lineback@pla-netx.com> for reporting about persistent
connection to MS server with multiple authorization requests. I had never heard of
such a behavior before that.

Janek Schwarz <j.schwarz@i-change.de> added command line option '-c' for config files
other than default server.cfg in working directory. Thanks for that to him.

Thanks to Stephen D. Cohen for very useful suggestions and cooperation.

Patch for Python >=1.6 by Markus Indenbirken (markus_i@gmx.de)

The most useful info has been got from "NTLM Authentication Scheme for HTTP"
page by Ronald Tschalar (ronald@innovation.ch). I included the page in the distribution
because it looks like that the server it contains is going down.
(http://www.innovation.ch/java/ntlm.html)

md4.py and des_c.py had been translated from md4.c and des.c from
"the Python Cryptography Toolkit, version 1.0.0 Copyright (C) 1995, A.M. Kuchling"

