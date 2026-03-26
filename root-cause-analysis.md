# Root Cause Analysis

## Summary

The issue was caused by Windows Explorer (explorer.exe) hanging due to a problematic network share reference.

## Technical Breakdown

* A network path was created using an IP address (\192.168.x.x)
* Explorer attempts to resolve and maintain access to this path
* If the resource is slow/unreachable, Explorer can block UI threads

## Evidence

* Issue began after creating network shortcut
* Temporary fix achieved by resetting Explorer (lock/unlock or restart)
* System slowdown consistent with blocking network I/O

## Root Cause

Explorer.exe UI thread blocked by unresolved or slow SMB network reference

## Fix Applied

* Removed network shortcut
* Cleared SMB sessions using:
  net use * /delete
* Restarted Explorer process

## Result

System returned to stable operation

## Prevention

* Avoid persistent IP-based network shortcuts
* Use hostnames instead of raw IPs
* Always create a restore point before system changes
