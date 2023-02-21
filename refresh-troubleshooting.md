# Refresh/Bunkum Troubleshooting

## Windows - Access denied on startup

***As of Refresh v1.1.0, this problem should no longer be relevant.
Please let us know if this is still required for Refresh to work on Windows.***

You may get the following exception on startup while hosting as a standard user on Windows:

```
Unhandled exception. System.Net.HttplistenerException (5): Access is denied.
```

This is due to lacking ACL permissions. There are two ways to obtain them.

1. Run Refresh as Administrator (not recommended)
1. Add them manually via a command: `netsh http add urlacl url="http://+:10061/" user=everyone`

The second method is recommended, as it allows Refresh to run with limited permissions. **Giving Refresh administrator privileges (or any software that does not need them) is a bad idea.**

## Windows - Refresh starts, but I don't get any requests in the console

If you dont get any requests in Refresh's console, try accessing Refresh's server from a browser on another device on the same network; your phone for example.

If you are unable to access it from another device, you are probably experiencing a firewall issue. You can resolve it by adding an inbound port rule in Windows Firewall:

1. Open "Windows Firewall with Advanced Security".
1. Select the "Inbound Rules" tab on the top-left side of the window.

    ![Inbound Rules Tab](https://littlebigrefresh.github.io/Docs/pics/add_firewall_rule_1.png)

1. Click "New rule..." on the top-right side of the window.

    ![New Rule... button](https://littlebigrefresh.github.io/Docs/pics/add_firewall_rule_2.png)

1. Select "Port" for the rule type and click Next.

    ![Port on wizard](https://littlebigrefresh.github.io/Docs/pics/add_firewall_rule_3.png)

1. Select TCP when asked what the rule should apply to, and choose a specific local port of `10061`, and click Next.

    ![Port information](https://littlebigrefresh.github.io/Docs/pics/add_firewall_rule_4.png)

1. For the remaining steps of this wizard, you can choose whatever works best for you. Generally the default options are okay.
1. Name the rule "Refresh" and click Finish.

The rule will apply immediately, and you should now be able to connect!