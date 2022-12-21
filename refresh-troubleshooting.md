# Refresh Troubleshooting

## Access denied on startup on Windows

You may get the following exception on startup while hosting as a standard user on Windows:

```
Unhandled exception. System.Net.HttplistenerException (5): Access is denied.
```

This is due to lacking ACL permissions. There are two ways to obtain them.

1. Run Refresh as Administrator
1. Add them manually via a command: `netsh http add urlacl url="http://+:10061/" user=everyone`
