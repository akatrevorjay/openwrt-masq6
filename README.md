Masquerading NAT6
=================

Easy to use `firewall.d` hook to allow you to specify `masq6` right as you'd expect.

Configuration is done per firewall zone, just like standard masquerading:

```
# in /etc/config/firewall:
config zone
        option name 'wan'
        option input 'DROP'
        option forward 'DROP'
        option output 'ACCEPT'
        option masq '1'
        option mtu_fix '1'
        list network wan
        list network wan6

        ##
        ## Above is just an example, below are the nat6 related options:
        ##

        option masq6 '1'            # Enable masquerading NAT6
        # option masq6_privacy '1'  # Enable IPv6 privacy extensions
```

Installation
------------

Simply put the included `90-nat6.fw` to `/etc/firewall.d/with_reload/`:

```sh
curl -sSLfo '/etc/firewall.d/with_reload/90-nat6.fw' 'https://raw.githubusercontent.com/akatrevorjay/openwrt-masq6/master/90-nat6.fw'
chmod +x '/etc/firewall.d/with_reload/90-nat6.fw'
```

Then configure as above and `/etc/init.d/firewall restart`.
