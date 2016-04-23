As of 2015 Columbia UIT does not officially support Linux VPN. For Windows and
Mac OS instructions click [here](https://cuit.columbia.edu/vpn).

## What is VPN?

> Using VPNs, an organization can help secure private network traffic over an
unsecured network, such as the Internet. VPN helps provide a secure mechanism
for encrypting and encapsulating private network traffic and moving it through
an intermediate network. Data is encrypted for confidentiality, and packets
that might be intercepted on the shared or public network are indecipherable
without the correct encryption keys. Data is also encapsulated, or wrapped,
with an IP header containing routing information.<sup>†</sup> 

<sup>† http://web.archive.org/web/20150727173446/https://technet.microsoft.com/en-us/library/Cc779919(v=WS.10).aspx</sup>

## Why use it?

By routing traffic through the Columbia VPN you will have access to the
university and library resources. Your traffic will be secured from point
access to Columbia servers. This may be important when traveling or working
from home.

## Requirements

This tutorial assumes Ubuntu or Debian derivatives. Your mileage may vary. You
will need to have some proficiency with the terminal to follow.

## Instructions

1. Download the oldest **Mac** client from the official [CUIT
page](https://cuit.columbia.edu/vpn). You will need your ID and password.

2. The client comes as a `.dmg` file. Use the `7z` utility to unpack by running
`7z x vpnclient-XXXXXXXXXXXXXX-k9.dmg`.

3. `cd` into the resulting `CiscoVPNClient/Profiles` directory. Open `Columbia
VPN.pcf` in your text editor.

4. Note the encrypted `enc_GroupPwd` value which should be a long (100+ bytes)
string. You will also need values from the `Host` and `GroupName` fields.

5. Use the [Cisco Vpnclient Password
Decoder](https://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode).<sup>†</sup>
This should produce a short password that you should keep somewhere safe.

    <sup>†† Note that this step presents a minor security vulnerability, as you are
    potentially exposing the group password to third parties. Contact CUIT to
    request Linux VPN support today! Until they do, run the C script locally
    instead of using the web service.</sup>

6. Install `network-manager-vpnc` or `network-manager-vpnc-gnome` depending on
your distribution. In my case, I run "sudo apt-get install
network-manager-vpnc-gnome`.

7. Alternatively, `sudo apt-get install vpnc` for the command line version of
the tool. Skip to Step 11.

8. If you installed the network manager (nm) plugin, reboot. Left-click on the
nm status icon, select `vpn connections` and `configure vpn`.

9. Enter the value of `host` from Step 4 for `gateway` and your UNI
and password for `user name`. Copy the group name from Step 4, and the decoded
password for `group password`. Give the connection a reasonable name and save.

10. In `ipv4 settings` click `Routes` and select "Ignore automatically obtained
routes."

11. You are all set! To use, left click on nm status, select `vpn connections`
and click on name to connect. Look for a visual indication from nm to see if
you are connected.

12. Optionally, right click to edit connection and select "automatically
connect to VPN when using this connection." You are done!

13. If you went the command line route, edit `/etc/vpnc/default.conf` (create
if needed) to include the following (without the squre brackets):

    ```
    IPSec gateway host [Host from Step 4]
    IPSec id [groupname from Step 4]
    IPSec secret [decrypted pass from Step 4]
    Xauth username [your UNI]
    ```
    You can include your UNI password here, but it is not recommended to
    keep passwords in cleartext. For more information see
    [here](http://web.archive.org/web/20150725230515/http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-with-vpnc/).</sup>

14. Run `sudo vpnc-connect` and `sudo vpnc-disconnect` to operate. Look for
`tun` when running `sudo ifconfig` to check for the connection. You are done!
