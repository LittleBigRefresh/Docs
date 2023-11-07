# Refresh/Bunkum Troubleshooting

## Windows - Refresh starts, but I don't get any requests in the console

If you don't get any requests in Refresh's console, try accessing Refresh's server from a browser on another device on the same network; your phone for example.

If you are unable to access it from another device, you are probably experiencing a firewall issue. You can resolve it by adding an inbound port rule in Windows Firewall:

1. Open "Windows Firewall with Advanced Security".
2. Select the "Inbound Rules" tab on the top-left side of the window.

    ![Inbound Rules Tab](add_firewall_rule_1.png)

3. Click "New rule..." on the top-right side of the window.

    ![New Rule... button](add_firewall_rule_2.png)

4. Select "Port" for the rule type and click Next.

    ![Port on wizard](add_firewall_rule_3.png)

5. Select TCP when asked what the rule should apply to, and choose a specific local port of `10061`, and click Next.

    ![Port information](add_firewall_rule_4.png)

6. For the remaining steps of this wizard, you can choose whatever works best for you. Generally the default options are okay.
7. Name the rule "Refresh" and click Finish.

The rule will apply immediately, and you should now be able to connect!